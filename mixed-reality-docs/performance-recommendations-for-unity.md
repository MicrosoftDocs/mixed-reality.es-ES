---
title: Recomendaciones de rendimiento para Unity
description: Sugerencias específicas de Unity para mejorar el rendimiento con aplicaciones de realidad mixta.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: gráficos, CPU, GPU, representación, recolección de elementos no utilizados, hololens
ms.openlocfilehash: 6507667904cfa26dfad1ccf1402cc75f14386609
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003204"
---
# <a name="performance-recommendations-for-unity"></a>Recomendaciones de rendimiento para Unity

Este artículo se basa en la explicación que se describe en [recomendaciones de rendimiento para la realidad mixta](understanding-performance-for-mixed-reality.md) pero se centra en los aprendizajes específicos del entorno del motor de Unity.

También es muy recomendable que los desarrolladores revisen el [artículo de configuración de entorno recomendado para Unity](Recommended-settings-for-unity.md). En este artículo se incluye contenido con algunas de las configuraciones de escenas más importantes para la creación de aplicaciones de realidad mixta de gran rendimiento. Algunos de estos valores recomendados se resaltan a continuación.

## <a name="how-to-profile-with-unity"></a>Cómo generar perfiles con Unity

Unity proporciona el **[generador de perfiles de Unity](https://docs.unity3d.com/Manual/Profiler.html)** integrado, que es un excelente recurso para recopilar información valiosa sobre el rendimiento de la aplicación en particular. Aunque se puede ejecutar el generador de perfiles en el editor, estas métricas no representan el entorno en tiempo de ejecución real y, por tanto, se deben usar con precaución. Se recomienda generar perfiles de forma remota de la aplicación mientras se ejecuta en el dispositivo para obtener información más precisa y útil. Además, el [depurador de fotogramas](https://docs.unity3d.com/Manual/FrameDebugger.html) de Unity también es una herramienta muy eficaz y de información para su uso.

Unity proporciona una excelente documentación para:
1) Cómo conectar el [generador de perfiles de Unity a aplicaciones de UWP de forma remota](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Cómo diagnosticar de forma eficaz [los problemas de rendimiento con el generador de perfiles de Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Con el generador de perfiles de Unity conectado y después de agregar el generador de perfiles de GPU (consulte *Agregar Profiler* en la esquina superior derecha), puede ver cuánto tiempo se dedica a la CPU & GPU, respectivamente, en medio del generador de perfiles. Esto permite al desarrollador obtener una aproximación rápida si su aplicación está limitada por CPU o GPU.
>
> ![CPU de Unity frente a GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU

El contenido que aparece a continuación abarca prácticas más detalladas de rendimiento, especialmente destinadas a desarrollo de Unity & C# .

#### <a name="cache-references"></a>Referencias de caché

Se recomienda almacenar en caché las referencias a todos los componentes relevantes y GameObjects en la inicialización. Esto se debe a que la repetición de llamadas de función como *[GetComponent\<t > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* son significativamente más caras en relación con el costo de memoria para almacenar un puntero. Esto también se aplica a la [cámara. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html)de uso frecuente. En realidad, *Camera. Main* solo usa *[FindGameObjectsWithTag ()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* , que busca de un modo costoso un objeto de cámara con la etiqueta *"MainCamera"* .

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> Evite GetComponent (cadena) <br/>
> Al usar *[GetComponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , hay una serie de sobrecargas diferentes. Es importante usar siempre las implementaciones basadas en tipos y nunca la sobrecarga de búsqueda basada en cadenas. La búsqueda por cadena en la escena es significativamente más costosa que la búsqueda por tipo. <br/>
> Apropiado Componente GetComponent (tipo Type) <br/>
> Apropiado > T GetComponent\<T () <br/>
> N Componente GetComponent (cadena) > <br/>

#### <a name="avoid-expensive-operations"></a>Evite operaciones costosas

1) **Evitar el uso de [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Aunque LINQ puede ser muy limpio y fácil de leer y escribir, generalmente requiere mucho más cálculo y más asignación de memoria que escribir el algoritmo de forma manual.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **API de Unity comunes**

    Ciertas API de Unity, aunque resultan útiles, pueden ser muy costosas de ejecutar. La mayoría de ellas implican buscar en todo el gráfico de escenas una lista coincidente de GameObjects. Por lo general, estas operaciones se pueden evitar mediante el almacenamiento en caché de las referencias o la implementación de un componente de administrador para el GameObjects en cuestión para realizar el seguimiento de las referencias en tiempo de ejecución.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* y *[BroadcastMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* deben eliminarse a todos los costos. Estas funciones pueden estar en el orden de 1000 veces más lento que las llamadas de función directas.

3) **Tenga cuidado con la conversión boxing**

    La C# [conversión boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) es un concepto básico del lenguaje y del tiempo de ejecución. Es el proceso de ajustar variables con tipo de valor como Char, int, bool, etc. en variables de tipo de referencia. Cuando una variable con tipo de valor se "aplica a la conversión boxing", se ajusta dentro de un objeto System. Object que se almacena en el montón administrado. Por lo tanto, se asigna la memoria y, en el momento en el que se elimina, debe ser procesada por el recolector de elementos no utilizados. Estas asignaciones y desasignaciones incurren en un costo de rendimiento y en muchos escenarios no son necesarios o se pueden reemplazar fácilmente por una alternativa menos costosa.

    Una de las formas más comunes de conversión boxing en el desarrollo es el uso de [tipos de valor que aceptan valores NULL](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/). Es habitual tener la posibilidad de devolver null para un tipo de valor en una función, sobre todo cuando la operación puede producir un error al intentar obtener el valor. El posible problema con este enfoque es que la asignación se produce ahora en el montón y, por consiguiente, debe ser recolectada como elemento no utilizado más adelante.

    **Ejemplo de conversión boxing enC#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Ejemplo de conversión boxing problemática a través de tipos de valor que aceptan valores NULL**

    Este código muestra una clase de partícula ficticia que se puede crear en un proyecto de Unity. Una llamada a `TryGetSpeed()` producirá la asignación de objetos en el montón que necesitará recolectar elementos no utilizados en un momento posterior. Este ejemplo es especialmente problemático, ya que puede haber 1000 o más partículas en una escena, cada una de las cuales solicita su velocidad actual. Por lo tanto, se asignarán 1000 objetos y, por tanto, se anulará la asignación de cada fotograma, lo que reduciría considerablemente el rendimiento. Volver a escribir la función para devolver un valor negativo como-1 para indicar un error evitaría este problema y mantener la memoria en la pila.

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a>Repetir rutas de código

Cualquier función de devolución de llamada de Unity repetida (es decir, Update) que se ejecutan muchas veces por segundo o el marco debe escribirse con sumo cuidado. Cualquier operación costosa aquí tendrá un impacto enorme y coherente en el rendimiento.

1) **Funciones de devolución de llamada vacías**

    Aunque el código siguiente puede parecer inocentes de dejar en la aplicación, sobre todo porque cada script de Unity se inicializa automáticamente con este bloque de código, estas devoluciones de llamada vacías pueden llegar a ser muy costosas. Unity opera hacia atrás y hacia delante a través de un límite de código administrado o no administrado, entre el código UnityEngine y el código de aplicación. El cambio de contexto sobre este puente es bastante caro, incluso si no hay nada que ejecutar. Esto resulta especialmente problemático si la aplicación tiene 100 de GameObjects con componentes que tienen devoluciones de llamada de Unity repetidas.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () es la manifestación más común de este problema de rendimiento, pero otras devoluciones de llamada de Unity repetidas, como las siguientes pueden ser igualmente incorrectas, si no peor: FixedUpdate (), LateUpdate (), OnPostRender ", OnPreRender (), OnRenderImage (), etc. 

2) **Operaciones para favorecer la ejecución una vez por fotograma**

    Las siguientes API de Unity son operaciones comunes para muchas aplicaciones holográficas. Aunque no siempre es posible, los resultados de estas funciones se suelen calcular una vez y los resultados se reutilizan en la aplicación para un fotograma determinado.

    a) por lo general, es recomendable tener una clase o un servicio singleton dedicado para controlar el Raycast de fijamente en la escena y, a continuación, volver a usar este resultado en todos los demás componentes de la escena, en lugar de realizar operaciones Raycast repetidas y esencialmente idénticas en cada pone. Por supuesto, algunas aplicaciones pueden requerir raycasts de diferentes orígenes o de [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html)diferentes.

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Evite las operaciones GetComponent () en las devoluciones de llamada de Unity repetidas como Update () mediante el [almacenamiento en caché de las referencias](#cache-references) en Start () o activo ()

        UnityEngine.Object.GetComponent()

    c) es recomendable crear una instancia de todos los objetos, si es posible, en la inicialización y usar la [agrupación de objetos](#object-pooling) para reciclar y volver a usar GameObjects en tiempo de ejecución de la aplicación.

        UnityEngine.Object.Instantiate()

3) **Evitar interfaces y construcciones virtuales**

    La invocación de llamadas a funciones a través de interfaces frente a objetos directos o llamadas a funciones virtuales a menudo puede ser mucho más costosa que usar construcciones directas o llamadas a funciones directas. Si la función virtual o la interfaz no son necesarias, se debe quitar. Sin embargo, el impacto en el rendimiento de estos enfoques por lo general merece la pena el equilibrio si su uso simplifica la colaboración en el desarrollo, la legibilidad del código y el mantenimiento del código.

    Por lo general, la recomendación es no marcar los campos y las funciones como virtuales a menos que haya una expectativa clara de que sea necesario sobrescribir este miembro. Debe ser especialmente cauto en torno a las rutas de acceso de código de alta frecuencia a las que se llama muchas veces por fotograma, o incluso una vez por fotograma, como un método `UpdateUI()`.

4) **Evite pasar Structs por valor**

    A diferencia de las clases, las estructuras son tipos de valor y, cuando se pasan directamente a una función, su contenido se copia en una instancia recién creada. Esta copia agrega costo de CPU, así como memoria adicional en la pila. En el caso de las estructuras pequeñas, el efecto es normalmente muy mínimo y, por tanto, aceptable. Sin embargo, para las funciones invocadas repetidamente cada fotograma y las funciones que toman estructuras grandes, si es posible, modifique la definición de función para que pase por referencia. [Más información aquí](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Varios

1) **Efectos**

    a) por lo general, la manera más fácil de mejorar la física es limitar la cantidad de tiempo empleado en la física o el número de iteraciones por segundo. Por supuesto, esto reducirá la precisión de la simulación. Consulte [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) en Unity

    b) el tipo de colisionadores en Unity tiene características de rendimiento muy diferentes. En el orden siguiente se enumeran los colisiones de mayor rendimiento de los colisionadores con menos rendimiento de izquierda a derecha. Es más importante evitar los colisionadores de malla, que son mucho más caros que los colisionadores primitivos.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Consulte [prácticas recomendadas](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) de la física de Unity para obtener más información

2) **Animaciones**

    Deshabilitar animaciones inactivas deshabilitando el componente de animación (la deshabilitación del objeto de juego no tendrá el mismo efecto). Evite patrones de diseño en los que un animador se encuentre en un bucle estableciendo un valor en lo mismo. Esta técnica conlleva una sobrecarga considerable, sin ningún efecto en la aplicación. [Obtenga más información aquí.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmos complejos**

    Si su aplicación usa algoritmos complejos, como cinemáticas inversas, búsqueda de rutas de acceso, etc., busque un enfoque más sencillo o ajuste los valores de configuración relevantes para su rendimiento.

## <a name="cpu-to-gpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU a GPU

Por lo general, el rendimiento de la CPU a la GPU se reduce a las **llamadas de dibujo** enviadas a la tarjeta gráfica. Para mejorar el rendimiento, las llamadas a Draw deben ser estratégicamente **a) reducidas** o **b) reestructuradas** para obtener resultados óptimos. Dado que las llamadas de dibujo a sí mismas son de uso intensivo de recursos, reducirlos reducirá todo el trabajo necesario. Además, los cambios de estado entre llamadas de dibujo requieren pasos de traducción y validación costosos en el controlador de gráficos y, por lo tanto, la reestructuración de las llamadas a Draw de la aplicación para limitar los cambios de estado (es decir, distintos materiales, etc.) pueden mejorar el rendimiento.

Unity tiene un excelente artículo que proporciona información general y profundiza en el procesamiento por lotes de las llamadas de dibujo para su plataforma.
- [Procesamiento por lotes de llamadas de Unity Draw](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Representación con instancia de un solo paso

La representación con instancia de un solo paso en Unity permite que las llamadas de dibujo de cada ojo se reduzcan a una llamada a Draw con instancias. Debido a la coherencia de la memoria caché entre dos llamadas a Draw, también hay una mejora del rendimiento en la GPU.

Para habilitar esta característica en el proyecto de Unity
1)  Abra la configuración de el **reproductor XR** (vaya a **Editar** > **configuración del proyecto** > **Player** > **configuración de XR**)
2) Seleccione **una instancia de paso único** en el menú desplegable **método de representación de estéreo** (se debe activar la casilla se admite la**realidad virtual** )

Lea los siguientes artículos de Unity para obtener más información sobre este enfoque de representación.
- [Cómo maximizar el rendimiento de AR y VR con la representación avanzada de estéreo](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creación de instancias de un solo paso](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Un problema común con la representación con instancias de paso único se produce si los desarrolladores ya tienen sombreadores personalizados no escritos para la creación de instancias. Después de habilitar esta característica, los desarrolladores pueden observar que algunos GameObjects solo se representan en un ojo. Esto se debe a que los sombreadores personalizados asociados no tienen las propiedades adecuadas para la creación de instancias.
>
> Consulte [representación de un solo paso estéreo para HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) desde Unity para saber cómo solucionar este problema.

#### <a name="static-batching"></a>Procesamiento por lotes estático

Unity puede procesar por lotes muchos objetos estáticos para reducir las llamadas de dibujo a la GPU. El procesamiento por lotes estático funciona para la mayoría de los objetos de [representador](https://docs.unity3d.com/ScriptReference/Renderer.html) en Unity que **1) comparten el mismo material** y **2) se marcan como *estáticos***  (seleccione un objeto en Unity y haga clic en la casilla situada en la parte superior derecha del inspector). Los GameObjects marcados como *static* no se pueden transferir a lo largo del tiempo de ejecución de la aplicación. Por lo tanto, el procesamiento por lotes estático puede ser difícil de aprovechar en HoloLens, donde prácticamente todos los objetos deben colocarse, moverse, escalarse, etc. En el caso de los auriculares más envolventes, el procesamiento por lotes estático puede reducir drásticamente las llamadas a Draw y mejorar el rendimiento.

Lea *procesamiento por lotes estático* en [procesamiento por lotes de llamadas en Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obtener más detalles.

#### <a name="dynamic-batching"></a>Procesamiento por lotes dinámico

Dado que es problemático marcar objetos como *estáticos* para el desarrollo de HoloLens, el procesamiento por lotes dinámico puede ser una herramienta excelente para compensar esta característica que falta. Por supuesto, también puede ser útil en los auriculares más envolventes. Sin embargo, el procesamiento por lotes dinámico en Unity puede ser difícil de habilitar porque GameObjects debe tener **un recurso compartido con el mismo material** y **b) cumplir una larga lista de otros criterios**.

Lea *procesamiento por lotes dinámico* en el [procesamiento por lotes de llamadas en Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obtener la lista completa. Normalmente, GameObjects dejan de ser válidos para procesarse por lotes dinámicamente, porque los datos de malla asociados no pueden ser más de 300 vértices.

#### <a name="other-techniques"></a>Otras técnicas

El procesamiento por lotes solo puede producirse si varios GameObjects pueden compartir el mismo material. Normalmente, se bloqueará la necesidad de que GameObjects tenga una textura única para su material respectivo. Es habitual combinar texturas en una sola textura grande, un método conocido como [Atlas de textura](https://en.wikipedia.org/wiki/Texture_atlas).

Además, suele ser preferible combinar las mallas en una GameObject siempre que sea posible y razonable. Cada representador en Unity tendrá sus llamadas a Draw asociadas y enviará una malla combinada bajo un representador.

>[!NOTE]
> La modificación de las propiedades del representador. el material en tiempo de ejecución creará una copia del material y, por tanto, puede romper el procesamiento por lotes. Use renderer. sharedMaterial para modificar las propiedades de material compartido en GameObjects.

## <a name="gpu-performance-recommendations"></a>Recomendaciones de rendimiento de GPU

Más información sobre la [optimización de la representación de gráficos en Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>Optimizar el uso compartido de búfer de profundidad

Por lo general, se recomienda habilitar el **uso compartido de búfer de profundidad** en **Player XR Settings** para optimizar la estabilidad de los [hologramas](Hologram-stability.md). Sin embargo, al habilitar la Reproyección en fases posteriores basada en la profundidad con esta configuración, se recomienda seleccionar el **formato de profundidad de 16 bits** en lugar del **formato de profundidad de 24 bits**. Los búferes de profundidad de 16 bits reducirán drásticamente el ancho de banda (y, por lo tanto, la potencia) asociado con el tráfico de búfer de profundidad. Esto puede ser una gran victoria tanto en la reducción de energía como en la mejora del rendimiento. Sin embargo, hay dos posibles resultados negativos con *el formato de profundidad de 16 bits*.

**Lucha Z**

La fidelidad de rango de profundidad reducida hace que las supuestos de [z](https://en.wikipedia.org/wiki/Z-fighting) sean más probables que se produzcan con 16 bits de 24 bits. Para evitar estos artefactos, modifique los planos de clips cercanos o lejos de la [cámara de Unity](https://docs.unity3d.com/Manual/class-Camera.html) para tener en cuenta la precisión más baja. En el caso de las aplicaciones basadas en HoloLens, un plano de recorte lejano de 50 millones, en lugar del valor predeterminado de Unity, puede eliminar cualquier combate z.

**Búfer de estarcido deshabilitado**

Cuando Unity crea una [textura de representación con una profundidad de 16 bits](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), no se crea ningún búfer de estarcido. Al seleccionar el formato de profundidad de 24 bits, por documentación de Unity, se creará un búfer z de 24 bits, así como un [búfer de estarcido de 8 bits] (https://docs.unity3d.com/Manual/SL-Stencil.html) (si 32 bits es aplicable en un dispositivo, que suele ser el caso como HoloLens).

### <a name="avoid-full-screen-effects"></a>Evitar efectos de pantalla completa

Las técnicas que operan en la pantalla completa pueden resultar bastante costosas, ya que su orden de magnitud es millones de operaciones en cada fotograma. Por lo tanto, se recomienda evitar los [efectos posteriores al procesamiento](https://docs.unity3d.com/Manual/PostProcessingOverview.html) , como el suavizado de contorno, la floración, etc.

### <a name="optimal-lighting-settings"></a>Configuración de iluminación óptima

[La iluminación global en tiempo real](https://docs.unity3d.com/Manual/GIIntro.html) en Unity puede proporcionar resultados visuales pendientes, pero implica cálculos de iluminación bastante costosos. Se recomienda deshabilitar la iluminación global en tiempo real para cada archivo de escena de Unity a través de **Window** > la **representación** de > **configuración de iluminación** > desactivar **la iluminación global en tiempo real**.

Además, se recomienda deshabilitar todas las conversiones de instantáneas, ya que también se pueden agregar pasadas de GPU costosas a una escena de Unity. Las sombras se pueden deshabilitar por luz, pero también se pueden controlar holísticamente a través de la configuración de calidad.

**Edite** > **configuración del proyecto**y, a continuación, seleccione la categoría **calidad** > seleccione **calidad baja** para la plataforma UWP. También puede establecer la propiedad **Shadows** para **deshabilitar Shadows**.

### <a name="reduce-poly-count"></a>Reducir el número de poli

Normalmente, se reduce el número de polígonos.
1) Quitar objetos de una escena
2) La diezmación de recursos, lo que reduce el número de polígonos de una malla determinada
3) Implementar un [sistema de nivel de detalle (LOD)](https://docs.unity3d.com/Manual/LevelOfDetail.html) en la aplicación que representa objetos alejados con una versión de polígono inferior de la misma geometría

### <a name="understanding-shaders-in-unity"></a>Descripción de los sombreadores en Unity

Una aproximación sencilla para comparar los sombreadores en el rendimiento es identificar el promedio de operaciones que cada una se ejecuta en tiempo de ejecución. Esto se puede hacer fácilmente en Unity.

1) Seleccione el recurso de sombreador o seleccione un material y, a continuación, en la esquina superior derecha de la ventana del inspector, seleccione el icono de engranaje seguido de **"seleccionar sombreador"** .

    ![Selección del sombreador en Unity](images/Select-shader-unity.png)
2) Con el recurso de sombreador seleccionado, haga clic en el botón **"compilar y Mostrar código"** en la ventana del inspector.

    ![Compilar código de sombreador en Unity](images/compile-shader-code-unity.PNG)

3) Después de compilar, busque la sección de estadísticas en los resultados con el número de operaciones diferentes para el sombreador de vértices y píxeles (Nota: los sombreadores de píxeles se suelen denominar sombreadores de fragmentos)

    ![Operaciones del sombreador estándar de Unity](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>Optimizar los sombreadores de píxeles

Si se examinan los resultados de la estadística compilada con el método anterior, el [sombreador de fragmentos](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) normalmente ejecutará más operaciones que el [sombreador de vértices](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), en promedio. El sombreador de fragmentos, también conocido como sombreador de píxeles, se ejecuta por píxel en la salida de la pantalla, mientras que el sombreador de vértices solo se ejecuta por vértice de todas las mallas que se dibujan en la pantalla. 

Por lo tanto, no solo los sombreadores de fragmentos tienen más instrucciones que los sombreadores de vértices debido a todos los cálculos de iluminación, los sombreadores de fragmentos casi siempre se ejecutan en un conjunto de DataSet más grande. Por ejemplo, si la salida de pantalla es una imagen de 2K por 2K, el sombreador de fragmentos puede ejecutarse 2000 * 2000 = 4 millones veces. Si se representan dos ojos, este número se duplica ya que hay dos pantallas. Si una aplicación de realidad mixta tiene varios pasos, efectos de procesamiento posterior de pantalla completa o representación de varias mallas en el mismo píxel, este número aumentará drásticamente. 

Por lo tanto, reducir el número de operaciones en el sombreador de fragmentos normalmente puede proporcionar mejoras de rendimiento mucho mayores en las optimizaciones del sombreador de vértices.

#### <a name="unity-standard-shader-alternatives"></a>Alternativas del sombreador estándar de Unity

En lugar de usar una representación basada físicamente (PBR) u otro sombreador de alta calidad, consulte uso de un sombreador más eficaz y más económico. El [Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona el [sombreador estándar de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) que se ha optimizado para proyectos de realidad mixta.

Unity también proporciona un sin iluminación, un vértice iluminado, difuso y otras opciones de sombreador simplificado que son mucho más rápidas en comparación con el sombreador estándar de Unity. Vea [uso y rendimiento de los sombreadores integrados](https://docs.unity3d.com/Manual/shader-Performance.html) para obtener información más detallada.

#### <a name="shader-preloading"></a>Carga previa del sombreador

Use la *carga previa del sombreador* y otros trucos para optimizar [el tiempo de carga del sombreador](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html). En concreto, la precarga del sombreador significa que no verá ningún desequilibrio debido a la compilación del sombreador en tiempo de ejecución.

### <a name="limit-overdraw"></a>Sobredibujar límite

En Unity, se puede mostrar el sobredibujo de la escena, alternando el [**menú modo de dibujo**](https://docs.unity3d.com/Manual/ViewModes.html) en la esquina superior izquierda de la **vista de escena** y seleccionando **desdibujando**.

Por lo general, el sobredibujo se puede mitigar Reseleccionando los objetos antes de enviarlos a la GPU. Unity proporciona detalles sobre la implementación de la selección de la [oclusión](https://docs.unity3d.com/Manual/OcclusionCulling.html) para su motor.

## <a name="memory-recommendations"></a>Recomendaciones de memoria

Una asignación de memoria excesiva & las operaciones de desasignación pueden tener efectos negativos en la aplicación holográfica, lo que produce un rendimiento incoherente, fotogramas inmovilizados y otro comportamiento perjudicial. Es especialmente importante comprender las consideraciones de memoria al desarrollar en Unity, ya que la administración de la memoria se controla mediante el recolector de elementos no utilizados.

#### <a name="garbage-collection"></a>Colección de elementos no utilizados

Las aplicaciones holográficas perderán el procesamiento del tiempo de proceso en el recolector de elementos no utilizados (GC) cuando se active el GC para analizar los objetos que ya no están en el ámbito durante la ejecución y se debe liberar su memoria, por lo que puede estar disponible para su reutilización. Normalmente, las asignaciones y desasignaciones constantes requerirán que el recolector de elementos no utilizados se ejecute con más frecuencia, con lo que se perjudica el rendimiento y la experiencia del usuario.

Unity ha proporcionado una página excelente que explica en detalle cómo funciona el recolector de elementos no utilizados y sugerencias para escribir código más eficaz en lo que respecta a la administración de memoria.
- [Optimizar la recolección de elementos no utilizados en juegos de Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Una de las prácticas más comunes que conduce a una recolección de elementos no utilizados excesiva no almacena en caché las referencias a componentes y clases en el desarrollo de Unity. Las referencias deben capturarse durante el inicio () o activo () y se pueden volver a usar en funciones posteriores como Update () o LateUpdate ().

Otras sugerencias rápidas:
- Usar la clase [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# para compilar dinámicamente cadenas complejas en tiempo de ejecución
- Quite las llamadas a Debug. log () cuando ya no sean necesarias, ya que se ejecutan en todas las versiones de compilación de una aplicación.
- Si la aplicación holográfica normalmente requiere una gran cantidad de memoria, considere la posibilidad de llamar a [ _**System. GC. Collect ()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante las fases de carga, como cuando se presenta una pantalla de carga o transición.

#### <a name="object-pooling"></a>Agrupación de objetos

La agrupación de objetos es una técnica popular para reducir el costo de las asignaciones continuas & desasignaciones de objetos. Para ello, se asigna un grupo grande de objetos idénticos y se reutilizan instancias disponibles inactivas de este grupo en lugar de generar y destruir objetos constantemente a lo largo del tiempo. Los grupos de objetos son excelentes para los componentes reutilizables que tienen una duración variable durante una aplicación.

- [Tutorial de agrupación de objetos en Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Rendimiento de inicio

Considere la posibilidad de iniciar la aplicación con una escena más pequeña y luego use *[SceneManager. LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* para cargar el resto de la escena. Esto permite a la aplicación acceder a un estado interactivo lo más rápido posible. Tenga en cuenta que puede haber un gran aumento de la CPU mientras se activa la nueva escena y que cualquier contenido representado puede producir un error o una dificultad. Una manera de solucionar este aspecto es establecer la propiedad AsyncOperation. allowSceneActivation en "false" en la escena que se está cargando, esperar a que se cargue la escena, borrar la pantalla a negro y volver a establecerla en "true" para completar la activación de la escena.

Recuerde que mientras se carga la escena de inicio, se mostrará la pantalla de presentación holográfica al usuario.

## <a name="see-also"></a>Vea también
- [Optimización de la representación de gráficos en juegos de Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Optimizar la recolección de elementos no utilizados en juegos de Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Prácticas recomendadas de la física [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Optimizar scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
