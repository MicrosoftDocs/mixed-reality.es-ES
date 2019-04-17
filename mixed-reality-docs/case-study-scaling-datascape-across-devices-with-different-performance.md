---
title: 'Caso práctico: escalado Datascape en todos los dispositivos con distintos del rendimiento'
description: En este caso práctico se ofrece información sobre cómo los desarrolladores de Microsoft optimiza la aplicación Datascape para ofrecer una experiencia convincente en dispositivos con una variedad de capacidades de rendimiento.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: auriculares envolventes, optimización, VR, caso práctico de rendimiento
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605738"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Caso práctico: escalado Datascape en todos los dispositivos con distintos del rendimiento

Datascape es una aplicación de Windows Mixed Reality desarrollada internamente en Microsoft que nos hemos centrado en mostrar los datos meteorológicos encima de los datos de terreno. La aplicación explora la información única que los usuarios obtienen de detección de datos en mixed reality rodeando el usuario con la visualización de datos holográfica.

Datascape queríamos una variedad de plataformas de destino con capacidades de hardware diferentes que abarcan desde Microsoft HoloLens a inmersivos Windows Mixed Reality y desde los equipos con tecnología de inferior para los equipos más recientes con GPU de gama alta. El desafío principal fue la representación de la escena en cuestión visualmente atractiva en dispositivos con capacidades de gráficos totalmente diferente mientras se ejecuta en una alta velocidad de fotogramas.

En este caso práctico le guiará a través del proceso y las técnicas utilizadas para crear algunos de nuestros sistemas GPU que consumen muchos más, donde se describen los problemas que se producen y cómo los hemos superado.

## <a name="transparency-and-overdraw"></a>Transparencia y sobredibujan

Nuestro dificultades de procesamiento principal tratan con transparencia, ya que la transparencia puede ser costosa en una GPU.

Se pueden representar geometría sólida delante hacia atrás al escribir en el búfer de profundidad, deteniendo los píxeles futuras detrás de ese píxel desde que se descarte. Esto evita que oculta píxeles ejecutando al sombreador de píxeles, acelerar significativamente el proceso. Si la geometría se ordena de forma óptima, se dibujará una sola vez cada píxel en la pantalla.

Geometría transparente debe ordenarse atrás adelante y se basa en la salida del sombreador de píxeles y el píxel actual en la pantalla de fusión. Esto puede dar lugar a que cada píxel en la pantalla se dibuja en varias veces por fotograma, conocido como el sobredibujo.

Para equipos estándar y HoloLens, la pantalla solo se puede rellenar una serie de veces, haciendo que sea transparente representación problemático.

## <a name="introduction-to-datascape-scene-components"></a>Introducción a los componentes de escena Datascape

Tuvimos tres componentes principales que nuestra escena; **la interfaz de usuario, el mapa**, y **la información meteorológica**. Desde el principio sabíamos que nuestros efectos meteorológicos requeriría todo el tiempo GPU podría obtener, por lo que hemos diseñado la interfaz de usuario y el terreno de manera que podría reducir cualquier sobredibujo.

Nos rehacerse la interfaz de usuario varias veces para minimizar la cantidad de sobredibujo se generará. Nos equivocamos en el lado de geometría más complejo en lugar de superposición de arte transparente encima de otros para componentes como descripciones de los botones y asignación resplandecientes.

Para la asignación, se usa a un sombreador personalizado que desea quitar las características estándar de Unity como sombras e iluminación compleja, reemplazarlos con un modelo de iluminación simple sun único y un cálculo personalizado niebla. Esto genera un sombreador de píxeles simples y liberar ciclos GPU.

Se administra obtener la interfaz de usuario y la asignación a la representación en el presupuesto que no necesitábamos los cambios en ellos dependiendo del hardware; Sin embargo, la visualización del tiempo, en particular, la representación en la nube, resultó para ser más complicado!

## <a name="background-on-cloud-data"></a>En segundo plano de datos en la nube

Nuestros datos en la nube se descargan desde los servidores de la NOAA (http://nomads.ncep.noaa.gov/) y llegó a nosotros en tres capas 2D distintas, cada uno con el alto de la parte superior e inferior de la nube, así como la densidad de la nube para cada celda de la cuadrícula. Se obtuvo procesan los datos en una textura de información en la nube donde cada componente se almacenó en el componente rojo, verde y azul de la textura para facilitar el acceso en la GPU.

## <a name="geometry-clouds"></a>Nubes de geometría

Para asegurarse de que nuestros equipos con tecnología inferior se podía mostrar nuestro nubes hemos decidido empezar con un enfoque que utilizaría la geometría sólida para minimizar el sobredibujo.

En primer lugar, hemos intentado generar nubes generando una malla de mapa de elevación sólido para cada capa con el radio de la textura de información en la nube por cada vértice para generar la forma. Se utiliza a un sombreador de geometría para producir los vértices en la parte superior y en la parte inferior de la nube genera formas sólida en la nube. Se usará el valor de densidad de la textura a la nube de color con los colores más oscuros para obtener más nubes densas.

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

Se introdujo un modelo pequeño ruido para obtener más detalles sobre los datos reales. Para generar los bordes de redondeo en la nube, se recortan los píxeles en el sombreador de píxeles cuando el valor de radio interpolada alcanza un umbral para descartar los valores de casi cero.

![Nubes de geometría](images/datascape-geometry-clouds-700px.jpg)

Puesto que las nubes son geometría sólida, que se puede procesar antes del terreno para ocultar los píxeles del mapa costoso debajo para mejorar la velocidad de fotogramas. Esta solución se ejecutó correctamente en todas las tarjetas gráficas de min-spec las tarjetas de gráficos avanzados, así como en HoloLens, debido al enfoque de representación de geometría sólida.

## <a name="solid-particle-clouds"></a>Nubes de partícula sólida

Ahora tenemos una solución de copia de seguridad que genera una representación decente de nuestros datos en la nube, pero fue un poco mediocres en el factor "wow" y no transmitir la idea volumétrico que deseábamos para nuestros equipos de nivel superior.

El siguiente paso era crear las nubes que se representan con aproximadamente 100.000 objetos para producir una apariencia más orgánica y volumétrica.

Si partículas permanecen sólidas y ordenación delante hacia atrás, nos podemos aún aprovechar sacrificio de búfer de profundidad de los píxeles detrás de objetos procesados anteriormente, lo que reduce el sobredibujo. Además, con una solución basada en partículas, podemos alterar la cantidad de partículas usa en otro hardware de destino. Sin embargo, todos los píxeles todavía deben ser probado en profundidad, lo que produce una sobrecarga adicional.

En primer lugar, creamos las posiciones de partículas alrededor del punto central de la experiencia en el inicio. Se distribuyen las partículas más densidad en torno al centro y menos por lo tanto, en la distancia. Se ordenan previamente todas las partículas desde el centro hacia atrás por lo que implicaría que primero las partículas más cercano.

Un sombreador de cálculo sería la textura de información en la nube para colocar cada partícula en un alto correcto y el color que basa en la densidad de ejemplo.

Hemos usado *DrawProcedural* representar un cuatro por partículas permitir que los datos de la partícula para mantenerse en la GPU en todo momento.

Cada partícula contenía un alto y un radio. El alto se basaba en los datos en la nube muestreados de la textura de información en la nube y el radio se basaba en la distribución inicial donde se calcularán para almacenar la distancia horizontal a su vecino más cercano. Los cuadrantes utilizaría estos datos para orientar a sí mismo en el ángulo entre el alto para que cuando los usuarios lo mires horizontalmente, se mostraría el alto y cuando los usuarios consultó arriba a abajo, el área entre sus vecinos sería cubierto.

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

Como ordenamos el partículas de delante hacia atrás y todavía se usa a un sombreador de estilo continuo a los píxeles transparentes de clip (blend no), esta técnica controla una cantidad sorprendente de partículas, evitar costosa draw excesiva incluso en las máquinas basadas en la inferior.

## <a name="transparent-particle-clouds"></a>Nubes de partículas transparente

Las partículas sólidas proporcionan una buena idea orgánica a la forma de las nubes, pero todavía necesita algo que vender el fluffiness de nubes. Hemos decidido intentar una solución personalizada para las tarjetas de gráficos avanzados donde podemos introducir la transparencia.

Para hacer esto simplemente se cambia el criterio de ordenación inicial de las partículas y cambia el sombreador para usar la versión alfa de texturas.

![Fluffy nubes](images/fluffy-clouds-700px.jpg)

Un aspecto excelente, pero ha demostrado para ser demasiado pesada para incluso las máquinas más complicadas, ya que daría como resultado del procesamiento de cada píxel en la pantalla de cientos de veces en!

## <a name="render-off-screen-with-lower-resolution"></a>Representar fuera de la pantalla con una resolución inferior

Para reducir el número de píxeles representados por las nubes, comenzamos a procesarlas en el búfer de resolución de un trimestre (en comparación con la pantalla) y ajuste el resultado final copia de seguridad en la pantalla después de que todas las partículas tenían ha dibujado. Esto nos dio aproximadamente una velocidad 4 x, pero suministrada con un par de advertencias.

**Código para representar fuera de la pantalla:**

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

En primer lugar, al representar en un búfer fuera de la pantalla, hemos perdido toda la información de profundidad de nuestra escena principal, lo que resulta en partículas detrás montañas representación encima de la montaña.

En segundo lugar, ajuste el búfer también introdujo los artefactos de los bordes de nuestro nubes donde el cambio de la resolución fue evidente. Las dos secciones siguientes se hablan acerca de cómo se resuelven estos problemas.

## <a name="particle-depth-buffer"></a>Búfer de profundidad de partículas

Para hacer que los objetos coexistir con la geometría del mundo donde una montaña o un objeto podría abarcar partículas detrás de él, se rellena el búfer fuera de la pantalla con un búfer de profundidad con la geometría de la escena principal. Para generar este tipo búfer de profundidad, creamos una segunda cámara, sólo la geometría sólida y la profundidad de la escena de representación.

A continuación, usamos la textura nuevo en el sombreador de píxeles de las nubes para occlude píxeles. Se usa la misma textura para calcular la distancia a la geometría detrás de un píxel en la nube. Mediante esa distancia y aplicarlo a la versión alfa del píxel, ahora se tenía el efecto de nubes de difuminación que obtienen cerca de terreno, quitando los cortes de disco duros donde se encuentran las partículas y el terreno.

![Nubes combinadas en terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Enfocar los bordes

Las nubes arriba ajusta tenía casi idénticas a las nubes de tamaño normal en el centro de las partículas o donde superponen, pero se ha mostrado algunos artefactos en los bordes de la nube. En caso contrario, bordes nítidos podría aparecer borrosos y efectos de alias se introdujeron cuando mueve la cámara.

Resolvimos este problema mediante la ejecución de un sombreador sencillo en el búfer fuera de la pantalla para determinar donde grandes cambios produjeron por el contrario (1). Colocamos los píxeles con grandes cambios en un búfer nuevo de la Galería de símbolos (2). A continuación, utilizamos el búfer de galería de símbolos para la máscara de estas áreas de alto contraste al aplicar el búfer fuera de la pantalla en la pantalla, lo que resulta en agujeros dentro y alrededor de las nubes (3).

Se luego se representan todas las partículas nuevo en el modo de pantalla completa, pero esta vez había utilizado el búfer de galería de símbolos para ocultar todo, pero los bordes, lo que resulta en un conjunto mínimo de píxeles tocado (4). Dado que el búfer de comandos ya se ha creado las partículas, teníamos simplemente procésela de nuevo a la cámara nuevo.

![Progresión de representar los bordes de la nube](images/cloud-steps-1-4-700px.jpg)

El resultado final fue bordes nítidos secciones center económico de las nubes.

Aunque esto era mucho más rápido que la representación de todas las partículas en pantalla completa, no hay todavía un costo asociado con las pruebas de un píxel en el búfer de galería de símbolos, por lo que una enorme cantidad de sobredibujo todavía se suministra con un costo.

## <a name="culling-particles"></a>Selección de objetos

Para nuestro efecto del viento, generamos bandas de triángulo larga en un sombreador de cálculo, crear muchas espirales de viento en el mundo. Aunque el efecto del viento no era un gran velocidad de relleno debido a las tiras delgadas generado, genera muchos cientos de miles de vértices, lo que resulta en una carga elevada para el sombreador de vértices.

Hemos introducido anexar los búferes en el sombreador de cálculo para introducir un subconjunto de las bandas de viento va a dibujar. Con alguna vista simple frustum selección lógica en el sombreador de cálculo, podríamos determinar si fue una banda fuera de la vista de la cámara y evitar que se agreguen al búfer de inserción. Esto reduce la cantidad de bandas considerablemente, liberando algunos ciclos necesarios en la GPU.

**Código que muestra un búfer de datos anexados:**

*Sombreador de cálculo:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#código:*

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

Intentamos usando la misma técnica en las partículas en la nube, donde podría eliminar directamente a ellos en el sombreador de cálculo y solo insertar las partículas visibles va a representar. Esta técnica realmente no ha guardado nos mucho en la GPU ya que el cuello de botella más importante era los píxeles de cantidad representados en la pantalla y no el costo de calcular los vértices.

El otro problema con esta técnica era que rellena el búfer de datos anexados en orden aleatorio debido a su naturaleza de las partículas, causando las partículas ordenadas sea no ordenada, lo que resulta en que parpadean partículas en la nube de informática en paralelo.

Existen técnicas para ordenar el búfer de inserción, pero la cantidad limitada de ganancia de rendimiento que obtuvimos fuera de partículas de caras traseras probablemente haría desplazamiento con una ordenación adicional, por lo que decidimos no iniciará esta optimización.

## <a name="adaptive-rendering"></a>Procesamiento adaptable

Para garantizar una velocidad de fotogramas constante en una aplicación con distintas condiciones, como un vs nublado de representación de una vista clara, procesamiento adaptable se introdujo a nuestra aplicación.

Es el primer paso de procesamiento adaptable medir la GPU. Esto es lo hicimos insertando código personalizado en el búfer de comandos GPU al principio y final de un fotograma representado, capturar tanto la izquierda y derecha ocular. hora de la pantalla.

Midiendo el tiempo dedicado a procesamiento y compararlo con nuestro frecuencia de actualización deseada que obtuvimos una idea de cómo cerrar fuéramos a fotogramas descartados.

Cuando cerca de fotogramas descartados, adaptamos nuestra presentación para que sea más rápido. Una manera sencilla de adaptar está cambiando el tamaño de la ventanilla de la pantalla, que requieren menos píxeles que se procesan.

Mediante el uso de *UnityEngine.XR.XRSettings.renderViewportScale* el sistema se reduce la ventanilla de destino y se expande automáticamente el resultado de la copia de seguridad en la pantalla de ajuste. Un pequeño cambio en la escala es apenas perceptible en la geometría del mundo, y un factor de escala de 0,7 requiere la mitad de la cantidad de píxeles que se va a representar.

![escala de un 70%, la mitad de los píxeles](images/datascape-scaling-700px.jpg)

Cuando se detecten que se van a elimina fotogramas, reducir el escalado por un número fijo y aumentar nuevo cuando ejecutamos de nuevo con la suficiente rapidez.

Aunque hemos decidido qué técnica en la nube para utilizarla según gráficos capacidades del hardware en el inicio, es posible basarlo en los datos de la medición de GPU para impedir que el sistema permanece en baja resolución durante mucho tiempo, pero esto es algo que no tuvimos tiempo  para explorar en Datascape.

## <a name="final-thoughts"></a>Observaciones finales

Destinatarios de una variedad de hardware es difícil y requiere cierta planeación.

Le recomendamos que inicie máquinas con tecnología de inferior para familiarizarse con el espacio del problema y desarrollar una solución de copia de seguridad que se ejecutará en todos los equipos de destino. Diseñar la solución con la tasa de relleno en mente, como píxeles estará el recurso más valioso. Geometría sólida de destino a través de transparencia.

Con una solución de copia de seguridad, puede iniciar, a continuación, en capas en la complejidad de las máquinas de gama alta o quizás simplemente mejorar la resolución de la solución de copia de seguridad.

Diseñar para escenarios más desfavorables y quizás considere el uso de procesamiento adaptable para situaciones pesadas.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>Ingeniero de software @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Ingeniero de software @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Vea también
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)

 
