---
title: 'Caso práctico: escalado de Datascape entre dispositivos con un rendimiento diferente'
description: En este caso práctico se ofrece información sobre cómo los desarrolladores de Microsoft optimizaron la aplicación Datascape para ofrecer una experiencia atractiva en todos los dispositivos con una variedad de capacidades de rendimiento.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: auriculares inmersivo, optimización del rendimiento, VR, caso práctico
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523401"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Caso práctico: escalado de Datascape entre dispositivos con un rendimiento diferente

Datascape es una aplicación de Windows Mixed Reality desarrollada internamente en Microsoft donde nos centramos en mostrar los datos meteorológicos sobre los datos de terreno. La aplicación explora la información única que los usuarios obtienen de la detección de datos en realidad mixta rodeando al usuario con la visualización de datos holográfica.

En el caso de Datascape, queríamos tener como destino una gran variedad de plataformas con distintas capacidades de hardware que abarcan desde Microsoft HoloLens hasta auriculares mixtos de Windows Mixed Reality y desde equipos con una versión más reciente a los equipos más recientes con GPU de alto nivel. El principal desafío era representar nuestra escena en una cuestión visualmente atractiva en los dispositivos con funcionalidades de gráficos extremadamente diferentes mientras se ejecutaba en una velocidad de fotogramas.

Este caso práctico le guiará a través del proceso y las técnicas que se usan para crear algunos de nuestros sistemas más intensivos de GPU, donde se describen los problemas que se han encontrado y cómo se superaron.

## <a name="transparency-and-overdraw"></a>Transparencia y desdibujando

Nuestra representación principal se enfrenta a la transparencia, ya que la transparencia puede ser costosa en una GPU.

La geometría sólida se puede representar de delante a vuelta mientras se escribe en el búfer de profundidad, lo que detiene los píxeles futuros situados detrás de ese píxel para que no se descarten. Esto evita que los píxeles ocultos ejecuten el sombreador de píxeles, lo que acelera considerablemente el proceso. Si Geometry se ordena de forma óptima, cada píxel de la pantalla se dibujará una sola vez.

La geometría transparente debe estar ordenada de nuevo al frente y se basa en la mezcla de la salida del sombreador de píxeles con el píxel actual de la pantalla. Esto puede hacer que cada píxel de la pantalla se dibuje varias veces por fotograma, lo que se conoce como sobredibujo.

En el caso de los equipos de HoloLens y estándar, la pantalla solo se puede rellenar unas cuantas veces, lo que hace problemáticas la representación transparente.

## <a name="introduction-to-datascape-scene-components"></a>Introducción a los componentes de Datascape Scene

Tenemos tres componentes principales en nuestra escena; **la interfaz de usuario, la asignación**y **el tiempo**. Sabíamos pronto que nuestros efectos meteorológicos requerirían todo el tiempo de la GPU que podía obtener, por lo que hemos diseñado específicamente la interfaz de usuario y el terreno de una manera que reduciría cualquier posible desdibujo.

La interfaz de usuario se reutiliza varias veces para minimizar la cantidad de sobredibujo que produciría. Nos sentimos en el lateral de geometría más compleja en lugar de superponer un arte transparente encima de otro para componentes como los botones de resplandor y la información general sobre mapas.

En el mapa, usamos un sombreador personalizado que descartaría las características estándar de Unity, como sombras e iluminación compleja, y las reemplaza por un modelo simple de iluminación de sol sencillo y un cálculo de niebla personalizado. Esto produjo un sombreador de píxeles simple y libera ciclos de GPU.

Nos hemos administrado para obtener tanto la interfaz de usuario como el mapa que se va a representar en el presupuesto en el que no necesitábamos realizar ningún cambio en función del hardware. sin embargo, la visualización meteorológica, en particular la representación en la nube, demostró ser más difícil.

## <a name="background-on-cloud-data"></a>Información general sobre los datos en la nube

Nuestros datos en la nube se han descargado de los servidores de NOAA (http://nomads.ncep.noaa.gov/) y nos venían en tres capas 2D distintas, cada una con la altura superior e inferior de la nube, así como la densidad de la nube para cada celda de la cuadrícula. Los datos se procesaron en una textura de información de la nube donde cada componente estaba almacenado en el componente rojo, verde y azul de la textura para facilitar el acceso a la GPU.

## <a name="geometry-clouds"></a>Nubes de geometría

Para asegurarse de que nuestros equipos con las versiones más bajas podrían representar las nubes que decidimos empezar con un enfoque que usaría geometría sólida para minimizar el desdibujado.

En primer lugar, hemos intentado generar nubes mediante la generación de una malla de mapa de elevación sólida para cada capa mediante el radio de la textura de información de la nube por vértice para generar la forma. Usamos un sombreador de geometría para generar los vértices en la parte superior y en la parte inferior de la nube que genera las formas de nube sólida. Usamos el valor de densidad de la textura para colorear la nube con colores más oscuros para nubes más densas.

**Sombreador para crear los vértices:**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

Hemos introducido un pequeño patrón de ruido para obtener más detalles sobre los datos reales. Para producir bordes redondos de la nube, se recortan los píxeles del sombreador de píxeles cuando el valor de radio interpolado alcanza un umbral para descartar los valores cercanos a cero.

![Nubes de geometría](images/datascape-geometry-clouds-700px.jpg)

Dado que las nubes son geometría sólida, se pueden representar antes del terreno para ocultar los píxeles de mapa caros de debajo para mejorar la velocidad de fotogramas. Esta solución se ejecutó correctamente en todas las tarjetas gráficas de las tarjetas de gráficos de alta especificación a las tarjetas gráficas de alto nivel, así como en HoloLens, debido al enfoque de representación de geometría sólida.

## <a name="solid-particle-clouds"></a>Nubes de partículas sólidas

Ahora tenemos una solución de copia de seguridad que generaba una representación decente de nuestros datos en la nube, pero era un poco Lackluster en el factor "wow" y no transmitió la sensación volumétrica que queríamos para nuestros equipos de alta gama.

El siguiente paso fue crear las nubes al representarlas con aproximadamente 100.000 partículas para producir una apariencia más orgánica y volumétrica.

Si los objetos siguen siendo sólidos y se ordenan de antemano, se puede beneficiar de la selección del búfer de profundidad de los píxeles que se encuentran en las partículas representadas anteriormente, lo que reduce el desdibujo. Además, con una solución basada en partículas, podemos modificar la cantidad de partículas que se usan para tener como destino un hardware diferente. Sin embargo, todavía es necesario probar en profundidad todos los píxeles, lo que da lugar a una sobrecarga adicional.

En primer lugar, creamos posiciones de partículas alrededor del punto central de la experiencia en el inicio. Distribuimos las partículas más densamente en torno al centro y menos en la distancia. Se han ordenado previamente todas las partículas del centro al fondo para que los objetos más cercanos se representen primero.

Un sombreador de cálculo muestrearía la textura de información de la nube para colocar cada partícula con un alto y color correctos en función de la densidad.

Usamos *DrawProcedural* para representar una cuádruple por partícula, lo que permite que los datos de partículas permanezcan en la GPU en todo momento.

Cada partícula contenía un alto y un radio. El alto se basó en los datos en la nube muestreados desde la textura de información de la nube y el radio se basó en la distribución inicial, donde se calcularía para almacenar la distancia horizontal a su vecino más cercano. Los cuádruples usarían estos datos para orientarse horizontalmente con el alto, de modo que cuando los usuarios lo examinen horizontalmente, se muestre el alto y, cuando los usuarios lo examinaran de arriba abajo, se cubrirá el área entre sus vecinos.

![Forma de partícula](images/particle-shape-700px.png)

**Código del sombreador que muestra la distribución:**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

Puesto que las partículas se ordenan de antemano y todavía usamos un sombreador de estilo sólido para recortar (no Blend) píxeles transparentes, esta técnica controla una cantidad sorprendente de partículas, evitando el costoso exceso de espacio, incluso en los equipos con menos potencia.

## <a name="transparent-particle-clouds"></a>Nubes de partículas transparentes

Las partículas sólidas proporcionaban una buena sensación orgánica a la forma de las nubes, pero todavía necesitaba algo para vender el fluffiness de las nubes. Hemos decidido probar una solución personalizada para las tarjetas de gráficos de gama alta en las que se puede introducir transparencia.

Para ello, simplemente hemos cambiado el criterio de ordenación inicial de las partículas y hemos cambiado el sombreador para usar las texturas alfa.

![Nubes Fluffy](images/fluffy-clouds-700px.jpg)

Parecía estupendo pero resultó que era demasiado pesado para incluso las máquinas más complicadas, ya que daría lugar a la representación de cada píxel en la pantalla cientos de veces.

## <a name="render-off-screen-with-lower-resolution"></a>Representación fuera de la pantalla con una resolución más baja

Para reducir el número de píxeles representados por las nubes, empezamos a representarlos en un búfer de resolución de trimestre (en comparación con la pantalla) y ajustar el resultado final en la pantalla después de dibujar todos los objetos. Esto nos brindó aproximadamente una velocidad 4x, pero se incluía con un par de advertencias.

**Código para la representación fuera de la pantalla:**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

En primer lugar, al representar en un búfer fuera de pantalla, se pierde toda la información de profundidad de la escena principal, lo que da lugar a partículas detrás de las montañas que se representan en la montaña.

En segundo lugar, al ajustar el búfer también se presentaron artefactos en los bordes de nuestras nubes donde el cambio de resolución era perceptible. En las dos secciones siguientes se habla sobre cómo se resuelven estos problemas.

## <a name="particle-depth-buffer"></a>Búfer de profundidad de partículas

Para que las partículas coexistan con la geometría del mundo, donde una montaña o un objeto podrían cubrir partículas detrás de ella, rellenó el búfer fuera de pantalla con un búfer de profundidad que contiene la geometría de la escena principal. Para generar este búfer de profundidad, creamos una segunda cámara y solo representamos la geometría sólida y la profundidad de la escena.

Después usamos la nueva textura en el sombreador de píxeles de las nubes para tapaba píxeles. Usamos la misma textura para calcular la distancia a la geometría detrás de un píxel en la nube. Al usar esa distancia y aplicarla al alfa del píxel, ahora se tenía el efecto de que las nubes se atenuaron a medida que se alejan del terreno, lo que elimina cualquier corte duro en el que se cumplan las partículas y el terreno.

![Nubes mixtas en terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Enfoque de los bordes

Las nubes extendidas parecían prácticamente idénticas a las nubes de tamaño normal en el centro de las partículas o donde se superponen, pero mostraban algunos artefactos en los bordes de la nube. De lo contrario, los bordes nítidos aparecerán borrosos y los efectos de alias se presentaron cuando se movía la cámara.

Resolvemos este problema mediante la ejecución de un sombreador simple en el búfer fuera de pantalla para determinar dónde se produjeron los grandes cambios en el contraste (1). Se colocan los píxeles con cambios importantes en un nuevo búfer de estarcido (2). Después usamos el búfer de estarcido para enmascarar estas áreas de contraste alto al aplicar el búfer fuera de pantalla a la pantalla, lo que da lugar a huecos en las nubes (3).

A continuación, representamos todas las partículas de nuevo en el modo de pantalla completa, pero esta vez usaba el búfer de estarcido para enmascarar todo excepto los bordes, lo que da lugar a un conjunto mínimo de píxeles tocados (4). Puesto que el búfer de comandos ya se creó para las partículas, simplemente tenía que representarlo en la nueva cámara.

![Progresión de los bordes de la nube de representación](images/cloud-steps-1-4-700px.jpg)

El resultado final era bordes nítidos con secciones del centro baratas de las nubes.

Aunque esto era mucho más rápido que la representación de todos los objetos en la pantalla completa, sigue habiendo un costo asociado a la prueba de un píxel en el búfer de estarcido, por lo que una cantidad masiva de sobredibujo sigue teniendo un costo.

## <a name="culling-particles"></a>Selección de partículas

En nuestro efecto de viento, se generaron bandas triangulares largas en un sombreador de cálculo, con lo que se crean muchos WISPs de viento en el mundo. Aunque el efecto de viento no era pesado en la velocidad de relleno debido a que las tiras de la piel se generaron, producía muchos cientos de miles de vértices, lo que produce una carga pesada para el sombreador de vértices.

Hemos introducido búferes de anexión en el sombreador de cálculo para alimentar un subconjunto de las franjas de viento que se van a dibujar. Con alguna lógica de selección de frustum de vista simple en el sombreador de cálculo, podríamos determinar si una franja estaba fuera de la vista de cámara e impedir que se agregara al búfer de inserciones. Esto redujo significativamente la cantidad de bandas, liberando algunos ciclos necesarios en la GPU.

**Código que muestra un búfer de anexión:**

*Sombreador de cálculo:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#codifica*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

Se intentó usar la misma técnica en las partículas de la nube, donde se seleccionarían en el sombreador de cálculo y solo se enviarían los objetos visibles que se van a representar. En realidad, esta técnica no nos ha ahorrado mucho en la GPU, ya que el cuello de botella más importante era la cantidad de píxeles representada en la pantalla y no el costo de calcular los vértices.

El otro problema con esta técnica fue que el búfer de anexión se rellenó en orden aleatorio debido a su naturaleza en paralelo de la informática de las partículas, lo que hace que las partículas ordenadas no se ordenen, lo que provoca el parpadeo de los objetos en la nube.

Hay técnicas para ordenar el búfer de inserciones, pero la cantidad limitada de ganancia de rendimiento que se obtiene de los objetos de selección probablemente se desplazaría con una ordenación adicional, por lo que hemos decidido no seguir esta optimización.

## <a name="adaptive-rendering"></a>Representación adaptable

Para garantizar una velocidad de fotogramas constante en una aplicación con condiciones de representación variables como una vista en la nube y una vista clara, se presentó la representación adaptable a nuestra aplicación.

El primer paso de la representación adaptable es medir GPU. Para ello, se inserta código personalizado en el búfer de comandos de GPU al principio y al final de un fotograma representado, lo que captura el tiempo de la pantalla de ojo izquierdo y derecho.

Al medir el tiempo empleado en la representación y compararlo con la tasa de actualización deseada, tenemos una idea de lo cerca que tuvimos que quitar fotogramas.

Cuando se acerque a quitar fotogramas, se adapta la representación para que sea más rápida. Una manera sencilla de adaptar es cambiar el tamaño de la ventanilla de la pantalla, lo que requiere menos píxeles para representarlos.

Mediante el uso de *UnityEngine. XR. XRSettings. renderViewportScale* , el sistema reduce la ventanilla de destino y ajusta automáticamente el resultado de la copia de seguridad para que se ajuste a la pantalla. Un pequeño cambio en la escala es apenas perceptible en la geometría universal, y un factor de escala de 0,7 requiere la mitad de la cantidad de píxeles que se va a representar.

![70% de la escala, la mitad de los píxeles](images/datascape-scaling-700px.jpg)

Cuando se detecta que estamos a punto de quitar fotogramas, la escala se reduce en un número fijo y se vuelve a aumentar cuando se ejecuta de nuevo lo suficientemente rápido.

Aunque decidimos qué técnica de nube usar en función de las capacidades de gráficos del hardware en el inicio, es posible basarla en los datos de la medición de la GPU para evitar que el sistema se quede con poca resolución durante mucho tiempo, pero esto es algo que no teníamos tiempo.  para explorar en Datascape.

## <a name="final-thoughts"></a>Opiniones finales

El objetivo de una variedad de hardware es desafiante y requiere cierta planeación.

Le recomendamos que empiece a trabajar con máquinas de bajo consumo para familiarizarse con el espacio del problema y desarrollar una solución de copia de seguridad que se ejecutará en todas las máquinas. Diseñe la solución con la velocidad de relleno en mente, ya que los píxeles serán el recurso más valioso. Geometría sólida de destino sobre la transparencia.

Con una solución de copia de seguridad, puede empezar a crear niveles en mayor complejidad para máquinas de gama alta o quizás simplemente mejorar la resolución de la solución de copia de seguridad.

Diseño para los peores escenarios de casos y quizás considere el uso de la representación adaptable para situaciones pesadas.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>Ingeniero de software@Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Ingeniero de software@Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Vea también
* [Descripción del rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)

 
