---
title: Recomendaciones de rendimiento para Unity
description: Sugerencias específicas de Unity para mejorar el rendimiento con aplicaciones de realidad mixta.
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: gráficos, CPU, GPU, representación, recolección de elementos no utilizados, hololens
ms.localizationpriority: high
ms.openlocfilehash: c6c68a6dd6e8ba59bee983e158e210aed27d2b17
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216246"
---
# <a name="performance-recommendations-for-unity"></a>Recomendaciones de rendimiento para Unity

Este artículo se basa en la explicación que se indica en las [recomendaciones de rendimiento para la realidad mixta](understanding-performance-for-mixed-reality.md), pero se centra en los conocimientos específicos del entorno del motor Unity.

## <a name="use-recommended-unity-project-settings"></a>Uso de la configuración del proyecto de Unity

El primer paso más importante al optimizar el rendimiento de las aplicaciones de realidad mixta en Unity es asegurarse de que estás usando la [configuración de entorno recomendada para Unity](recommended-settings-for-unity.md). En este artículo se incluye contenido con algunas de las configuraciones de escenas más importantes para la creación de aplicaciones de realidad mixta de gran rendimiento. Algunas de estas configuraciones recomendadas también se indican a continuación.

## <a name="how-to-profile-with-unity"></a>Cómo generar perfiles con Unity

Unity proporciona una instancia integrada de **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** , que es un excelente recurso para recopilar información valiosa sobre el rendimiento de tu aplicación en particular. Aunque se puede ejecutar Profiler en el editor, estas métricas no representan el entorno real en tiempo de ejecución y, por tanto, los resultados se deben usar con precaución. Se recomienda generar perfiles de la aplicación de forma remota, mientras se ejecuta en el dispositivo, para obtener una información más precisa y útil. Además, [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) de Unity también es una herramienta muy eficaz y de información que se puede utilizar.

Unity proporciona una documentación excelente sobre:
1) Cómo conectar [Unity Profiler a aplicaciones para UWP de forma remota](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Cómo [diagnosticar los problemas de rendimiento con Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window) de forma eficaz

>[!NOTE]
> Con Unity Profiler conectado y después de agregar el generador de perfiles de GPU (consulta *Agregar generador de perfiles* en la esquina superior derecha), puedes ver cuánto tiempo se dedica a CPU y a GPU, respectivamente, en medio del generador de perfiles. Esto permite al desarrollador obtener una aproximación rápida de si su aplicación está vinculada a la CPU o la GPU.
>
> ![CPU de Unity frente a GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU

El siguiente contenido abarca prácticas de rendimiento más detalladas, especialmente destinadas al desarrollo en Unity y C#.

#### <a name="cache-references"></a>Almacenamiento en caché de referencias

Es una buena práctica almacenar en caché las referencias para todos los componentes pertinentes y GameObjects en la inicialización. Esto se debe a que las llamadas a funciones repetitivas, como *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* son considerablemente más costosas en relación con el costo de memoria para almacenar un puntero. Esto también se aplica a [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html) que se usa con frecuencia. *Camera.main* en realidad solo usa *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* debajo, que busca de un modo costoso en el gráfico de la escena un objeto de cámara con la etiqueta *"MainCamera"* .

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
> Evita GetComponent(string) <br/>
> Al usar *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , se producen unas cuantas sobrecargas diferentes. Es importante usar siempre las implementaciones basadas en tipo y nunca la sobrecarga de búsqueda basada en cadena. La búsqueda por cadena en la escena es significativamente más costosa que la búsqueda por tipo. <br/>
> (Correcto) Component GetComponent(Type tipo) <br/>
> (Correcto) T GetComponent\<T>() <br/>
> (Incorrecto) Component GetComponent(string)> <br/>

#### <a name="avoid-expensive-operations"></a>Evita operaciones costosas

1) **Evita el uso de [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Aunque LINQ puede ser muy limpio y fácil de leer y escribir, generalmente requiere mucho más cálculo y, en particular, más asignación de memoria que escribir el algoritmo de forma manual.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **API comunes de Unity**

    Ciertas API de Unity, aunque resultan útiles, pueden ser muy costosas de ejecutar. La mayoría de ellas implican buscar, en todo el gráfico de escena, una lista de GameObjects coincidentes. Por lo general, estas operaciones se pueden evitar mediante el almacenamiento en caché de las referencias o la implementación de un componente administrador para los GameObjects en cuestión, a fin de realizar el seguimiento de las referencias en tiempo de ejecución.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* y *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* deben eliminarse a toda costa. Estas funciones pueden ser del orden de 1000 veces más lentas que las llamadas a funciones directas.

3) **Ten cuidado con la conversión boxing**

    [La conversión boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) es un concepto básico del lenguaje C# y del tiempo de ejecución. Es el proceso de encapsular variables con tipo de valor como char, int, bool, etc. en variables con tipo de referencia. Cuando a una variable con tipo de valor se le aplica la "conversión boxing", se encapsula dentro de un objeto System.Object que se almacena en el montón administrado. Por lo tanto, se asigna memoria y, en el momento en el que se elimina, el recolector de elementos no utilizados la debe procesar. Estas asignaciones y anulaciones de asignación incurren en un costo de rendimiento y en muchos escenarios no son necesarias o se pueden reemplazar fácilmente por una alternativa menos costosa.

    Una de las formas más comunes de conversión boxing en el desarrollo es el uso de [tipos de valor que aceptan valores NULL](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/). Es habitual querer tener la posibilidad de devolver null para un tipo de valor en una función, sobre todo cuando la operación puede producir un error al intentar obtener el valor. El posible problema con este enfoque es que la asignación se produce ahora en el montón y, por consiguiente, debe recolectarse como elemento no utilizado más adelante.

    **Ejemplo de conversión boxing en C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Ejemplo de conversión boxing problemática mediante tipos de valor que aceptan valores NULL**

    Este código muestra una clase de partícula ficticia que se puede crear en un proyecto de Unity. Una llamada a `TryGetSpeed()` producirá la asignación de objetos en el montón que se deberán recolectar como elementos no utilizados en un momento posterior. Este ejemplo es especialmente problemático, ya que puede haber 1000 o más partículas en una escena, a cada una de las cuales se solicita su velocidad actual. Por lo tanto, se asignarán miles de objetos y, por consiguiente, se anulará su asignación en cada fotograma, lo que reducirá considerablemente el rendimiento. Volver a escribir la función para devolver un valor negativo como -1 para indicar un error evitará este problema y conservará la memoria en la pila.

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

#### <a name="repeating-code-paths"></a>Rutas de acceso al código repetitivas

Cualquier función de devolución de llamada de Unity repetitiva (por ejemplo, Update) que se ejecuta muchas veces por segundo o fotograma debe escribirse con sumo cuidado. Cualquier operación costosa tendrá un impacto enorme y consistente en el rendimiento.

1) **Funciones de devolución de llamada vacías**

    Aunque pueda parecer inofensivo dejar el código siguiente en la aplicación, sobre todo porque cada script de Unity se inicializa automáticamente con este bloque de código, estas devoluciones de llamada vacías pueden llegar a ser muy costosas. Unity opera de un lado para otro de un límite de código administrado o no administrado, entre el código UnityEngine y el código de la aplicación. El cambio de contexto sobre este puente es bastante caro, incluso si no hay nada que ejecutar. Resulta especialmente problemático si la aplicación tiene cientos de objetos GameObject con componentes que tienen devoluciones de llamada vacías de Unity repetitivas.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () es la manifestación más común de este problema de rendimiento, pero otras devoluciones de llamada de Unity repetitivas, como las siguientes, pueden ser igual de perjudiciales, si no peores: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **Operaciones para favorecer una ejecución por fotograma**

    Las siguientes API de Unity son operaciones comunes para muchas aplicaciones holográficas. Aunque no siempre es posible, los resultados de estas funciones se suelen calcular una vez y los resultados se reutilizan en la aplicación para un fotograma determinado.

    a) Por lo general, es una buena práctica tener una clase o un servicio Singleton dedicado para controlar la mirada Raycast de la escena y, a continuación, volver a usar este resultado en todos los demás componentes de la escena, en lugar de realizar repetidas operaciones Raycast y esencialmente idénticas para cada componente. Por supuesto, es posible que algunas aplicaciones requieran Raycast de distintos orígenes o con diferentes[LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Evita las operaciones GetComponent() en las devoluciones de llamada de Unity repetitivas, como Update(), mediante el [almacenamiento en caché de referencias](#cache-references) en Start() o Awake()

        UnityEngine.Object.GetComponent()

    c) Es una buena práctica crear instancias de todos los objetos, si es posible, en la inicialización y usar la [agrupación de objetos](#object-pooling) para reciclar y volver a usar GameObjects durante todo el tiempo de ejecución de la aplicación.

        UnityEngine.Object.Instantiate()

3) **Evita interfaces y construcciones virtuales**

    La invocación de llamadas a funciones a través de interfaces frente a objetos directos o la llamada a funciones virtuales pueden ser a menudo mucho más costosas que usar construcciones directas o llamadas a funciones directas. Si la interfaz o función virtual no es necesaria, se debe quitar. Sin embargo, por lo general, el impacto en el rendimiento de estos enfoques merece la pena si su uso simplifica la colaboración en el desarrollo, la legibilidad del código y el mantenimiento del código.

    Por lo general, la recomendación es no marcar los campos y las funciones como virtuales a menos que haya una expectativa clara de que sea necesario sobrescribir este miembro. Se debe ser especialmente cauto en torno a las rutas de acceso del código de alta frecuencia a las que se llama muchas veces por fotograma, o incluso una vez por fotograma, como un método `UpdateUI()`.

4) **Evita pasar estructuras por valor**

    A diferencia de las clases, las estructuras son tipos de valor y, cuando se pasan directamente a una función, su contenido se copia en una instancia recién creada. Esta copia agrega costo de CPU, así como memoria adicional a la pila. En el caso de las estructuras pequeñas, el efecto es normalmente mínimo y, por tanto, aceptable. Sin embargo, para las funciones invocadas repetidamente en cada fotograma y las funciones que toman estructuras grandes, si es posible, modifica la definición de función para que pase por referencia. [Obtén más información aquí](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Varios

1) **Física**

    a) En general, la manera más fácil de mejorar la física es limitar la cantidad de tiempo empleado en la física o el número de iteraciones por segundo. Por supuesto, disminuirá la precisión de la simulación. Consulta [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) en Unity.

    b) El tipo de colisionadores en Unity tiene características de rendimiento muy diferentes. En el orden siguiente se indican los colisionadores de mayor rendimiento a los colisionadores con menor rendimiento, de izquierda a derecha. Es de suma importancia evitar los colisionadores de malla, que son mucho más caros que los colisionadores primitivos.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Consulta [Buenas prácticas de la física de Unity](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) para obtener más información.

2) **Animaciones**

    Deshabilita las animaciones inactivas deshabilitando el componente animador (la deshabilitación del objeto de juego no tendrá el mismo efecto). Evita patrones de diseño en los que un animador se encuentre en un bucle estableciendo un valor en lo mismo. Esta técnica conlleva una sobrecarga considerable, sin ningún efecto en la aplicación. [Obtén más información aquí.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmos complejos**

    Si tu aplicación usa algoritmos complejos, como la cinemática inversa, la búsqueda de rutas de acceso, etc., busca un enfoque más sencillo o ajusta los valores de configuración pertinentes para su rendimiento.

## <a name="cpu-to-gpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU a GPU

En general, el rendimiento de CPU a GPU baja hasta las **llamadas a draw** enviadas a la tarjeta gráfica. Para mejorar el rendimiento, las llamadas a draw se deben **a)** reducir o **b) reestructurar** estratégicamente para obtener resultados óptimos. Dado que las llamadas a draw en sí mismas usan una gran cantidad de recursos, reducirlas también reducirá el trabajo general necesario. Además, los cambios de estado entre llamadas a draw requieren pasos de validación y traducción costosos en el controlador de gráficos y, por lo tanto, la reestructuración de las llamadas a draw de la aplicación para limitar los cambios de estado (es decir, distintos materiales, etc.) puede mejorar el rendimiento.

Unity dispone de un excelente artículo que proporciona información general y profundiza en el procesamiento por lotes de las llamadas a draw para su plataforma.
- [Procesamiento por lotes de llamadas a draw de Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Representación con instancia de un solo paso

La representación con instancia de un solo paso en Unity permite que las llamadas a draw de cada ojo se reduzcan a una llamada a draw con instancia. Debido a la coherencia de la memoria caché entre dos llamadas a draw, también hay una mejora del rendimiento de la GPU.

Para habilitar esta característica en el proyecto de Unity
1)  Abre **Player XR Settings** (Configuración del reproductor XR) (ve a **Editar** > **Configuración del proyecto** > **Reproductor** > **XR Settings** [Configuración de XR]).
2) Selecciona **Single Pass Instanced** (Con instancia de un solo paso) en el menú desplegable **Stereo Rendering Method** (Método de representación en estéreo) (la casilla **Virtual Reality Supported** [Compatibilidad con realidad virtual] debe estar marcada)

Lee los siguientes artículos de Unity para obtener más información sobre este enfoque de representación.
- [Cómo maximizar el rendimiento de AR y VR con la representación en estéreo avanzada](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creación de instancias de un solo paso](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Un problema común con la representación con instancia de un solo paso se produce si los desarrolladores ya tienen sombreadores personalizados no escritos para la creación de instancias. Después de habilitar esta característica, los desarrolladores pueden observar que algunos objetos GameObjects solo se representan en un ojo. Esto se debe a que los sombreadores personalizados asociados no tienen las propiedades adecuadas para la creación de instancias.
>
> Consulta [Representación en estéreo de un solo paso para HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) de Unity para solucionar este problema.

#### <a name="static-batching"></a>Procesamiento por lotes estático

Unity puede procesar por lotes muchos objetos estáticos para reducir las llamadas draw a la GPU. El procesamiento por lotes estático funciona en la mayoría de los objetos [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) en Unity que **1) comparten el mismo material** y **2) todos están marcados como *estáticos*** (selecciona un objeto en Unity y haz clic en la casilla de la parte superior derecha del inspector). Los objetos GameObject marcados como *estáticos* no se pueden mover en tiempo de ejecución de la aplicación. Por lo tanto, el procesamiento por lotes estático puede ser difícil de utilizar en HoloLens, donde prácticamente todos los objetos deben colocarse, moverse, escalarse, etc. En el caso de los cascos envolventes, el procesamiento por lotes estático puede reducir drásticamente las llamadas a draw y mejorar el rendimiento.

Lee *Procesamiento por lotes estático* en [Procesamiento por lotes de llamadas a draw en Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obtener más detalles.

#### <a name="dynamic-batching"></a>Procesamiento por lotes dinámico

Dado que es problemático marcar objetos como *estáticos* para el desarrollo de HoloLens, el procesamiento por lotes dinámico puede ser una herramienta excelente para compensar esta característica que falta. Por supuesto, también puede ser útil en los cascos envolventes. Sin embargo, el procesamiento por lotes dinámico en Unity puede ser difícil de habilitar porque los objetos GameObject deben **a) compartir el mismo material** y **b) cumplir una larga lista de otros criterios**.

Lee *Procesamiento por lotes dinámico* en [Procesamiento por lotes de llamadas a draw en Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obtener la lista completa. Normalmente, los objetos GameObject dejan de ser válidos para el procesamiento por lotes dinámico, porque los datos de malla asociados no pueden ser más de 300 vértices.

#### <a name="other-techniques"></a>Otras técnicas

El procesamiento por lotes solo puede producirse si varios objetos GameObject pueden compartir el mismo material. Normalmente, se bloqueará por la necesidad de que los objetos GameObject tengan una textura única para su material respectivo. Es habitual combinar texturas en una sola gran textura, un método conocido como [Creación de atlas de texturas](https://en.wikipedia.org/wiki/Texture_atlas).

Además, suele ser preferible combinar las mallas en un objeto GameObject siempre que sea posible y razonable. Cada Renderer de Unity tendrá sus llamadas a draw asociadas y enviará una malla combinada bajo un Renderer.

>[!NOTE]
> La modificación de las propiedades de Renderer.material en tiempo de ejecución creará una copia del material y, por tanto, puede interrumpir el procesamiento por lotes. Usa Renderer.sharedMaterial para modificar las propiedades de material compartido en los objetos GameObject.

## <a name="gpu-performance-recommendations"></a>Recomendaciones de rendimiento de GPU

Más información acerca de la [optimización de la representación de gráficos en Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>Optimización del uso compartido del búfer de profundidad

Por lo general, se recomienda habilitar **Depth buffer sharing** (Uso compartido del búfer de profundidad) en **Player XR Settings** (Configuración del reproductor XR) para optimizar la [estabilidad del holograma](Hologram-stability.md). Sin embargo, al habilitar la reproyección en etapa posterior basada en la profundidad con esta configuración, se recomienda seleccionar el **formato de profundidad de 16 bits** en lugar del **formato de profundidad de 24 bits**. Los búferes de profundidad de 16 bits reducirán drásticamente el ancho de banda (y, por lo tanto, la energía) asociado con el tráfico del búfer de profundidad. Puede ser una gran victoria tanto en la reducción de energía como en la mejora del rendimiento. Sin embargo, hay dos posibles resultados negativos al usar el *formato de profundidad de 16 bits*.

**Z-Fighting**

La fidelidad del intervalo de profundidad reducida hace que sea más probable que se produzca [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) con 16 bits que con 24 bits. Para evitar estos artefactos, modifica los planos de recortes cercanos o lejanos de la [cámara de Unity](https://docs.unity3d.com/Manual/class-Camera.html) para tener en cuenta la precisión inferior. En el caso de las aplicaciones basadas en HoloLens, un plano de recorte lejano de 50 m, en lugar del valor predeterminado de Unity de 1000 m, puede eliminar cualquier z-fighting.

**Búfer de galería de símbolos deshabilitado**

Cuando Unity crea una [representación de textura con profundidad de 16 bits](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html), no se crea ningún búfer de galería de símbolos. Al seleccionar el formato de profundidad de 24 bits, según la documentación de Unity, se creará un búfer Z de 24 bits, así como un [búfer de galería de símbolos de 8 bits] (https://docs.unity3d.com/Manual/SL-Stencil.html) (si se puede aplicar 32 bits en un dispositivo, que suele ser el caso, como HoloLens).

### <a name="avoid-full-screen-effects"></a>Evita efectos de pantalla completa

Las técnicas que operan en la pantalla completa pueden resultar bastante costosas, ya que su orden de magnitud es millones de operaciones en cada fotograma. Por lo tanto, se recomienda evitar [efectos posteriores al procesamiento](https://docs.unity3d.com/Manual/PostProcessingOverview.html) como el suavizado de contorno, la eclosión, etc.

### <a name="optimal-lighting-settings"></a>Configuración de iluminación óptima

La [iluminación global en tiempo real](https://docs.unity3d.com/Manual/GIIntro.html) de Unity puede proporcionar resultados visuales excelentes, pero implica cálculos de iluminación bastante costosos. Se recomienda deshabilitar la iluminación global en tiempo real para cada archivo de escena de Unity a través de **Ventana** > **Representación** > **Lighting Settings** (Configuración de iluminación) > desmarca **Real-time Global Illumination** (Iluminación global en tiempo real).

Además, se recomienda deshabilitar todas las proyecciones de sombras, ya que también agregan pasadas de GPU costosas a una escena de Unity. Las sombras se pueden deshabilitar por iluminación, pero también se pueden controlar holísticamente a través de la configuración de la calidad.

**Editar** > **Configuración del proyecto**, luego selecciona la categoría **Calidad** > selecciona **Calidad baja** para la Plataforma UWP. También puedes establecer solo la propiedad **Sombras** en **Disable Shadows** (Deshabilitar sombras).

Se recomienda usar la iluminación posterior con los modelos en Unity.

### <a name="reduce-poly-count"></a>Reducción del recuento de polígonos

Normalmente, se reduce el número de polígonos mediante alguna de las acciones siguientes
1) Eliminación de objetos de una escena
2) Supresión de recursos, lo que reduce el número de polígonos de una malla determinada
3) Implementación de un [sistema de nivel de detalle (LOD)](https://docs.unity3d.com/Manual/LevelOfDetail.html) en la aplicación, que represente los objetos alejados con una versión de polígono inferior de la misma geometría

### <a name="understanding-shaders-in-unity"></a>Descripción de los sombreadores en Unity

Una aproximación sencilla para comparar los sombreadores en el rendimiento es identificar el número promedio de operaciones que cada uno ejecuta en tiempo de ejecución. Esto se puede hacer fácilmente en Unity.

1) Selecciona el recurso de sombreador o selecciona un material y, a continuación, en la esquina superior derecha de la ventana del inspector, selecciona el icono de engranaje seguido de **"Select Shader"** (Seleccionar sombreador).

    ![Selección del sombreador en Unity](images/Select-shader-unity.png)
2) Con el recurso de sombreador seleccionado, haz clic en el botón **"Compile and show code"** (Compilar y mostrar código) en la ventana del inspector.

    ![Compilación del código de sombreador en Unity](images/compile-shader-code-unity.PNG)

3) Después de la compilación, busca la sección de estadísticas en los resultados con el número de las diferentes operaciones para el sombreador de vértices y píxeles. (Nota: Los sombreadores de píxeles se suelen denominar sombreadores de fragmentos).

    ![Operaciones del sombreador estándar de Unity](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>Optimización de los sombreadores de píxeles

Si se examinan los resultados de las estadísticas compiladas con el método anterior, el [sombreador de fragmentos](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) ejecutará normalmente más operaciones que el [sombreador de vértices](https://en.wikipedia.org/wiki/Shader#Vertex_shaders), como promedio. El sombreador de fragmentos, también conocido como sombreador de píxeles, se ejecuta por píxel en la salida de la pantalla, mientras que el sombreador de vértices solo se ejecuta por vértice de todas las mallas que se dibujan en la pantalla. 

Por lo tanto, no solo los sombreadores de fragmentos tienen más instrucciones que los sombreadores de vértices debido a todos los cálculos de iluminación, los sombreadores de fragmentos casi siempre se ejecutan en un conjunto de datos mayor. Por ejemplo, si la salida de la pantalla es una imagen de 2 K por 2 K, el sombreador de fragmentos puede ejecutarse 2000 * 2000 = 4 000 000 veces. Si se representan dos ojos, este número se duplica ya que hay dos pantallas. Si una aplicación de realidad mixta tiene varios pasos, efectos de procesamiento posterior de pantalla completa o representación de varias mallas para el mismo píxel, este número aumentará drásticamente. 

Por lo tanto, reducir el número de operaciones en el sombreador de fragmentos normalmente puede proporcionar mejoras de rendimiento mucho mayores que las optimizaciones del sombreador de vértices.

#### <a name="unity-standard-shader-alternatives"></a>Alternativas del sombreador estándar de Unity

En lugar de usar una representación basada físicamente (PBR) u otro sombreador de alta calidad, consulta el uso de un sombreador más eficaz y económico. [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona el [sombreador estándar de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) que se ha optimizado para proyectos de realidad mixta.

Unity también proporciona opciones sin iluminación, iluminación de vértice, difuso y otras opciones simplificadas de sombreador que son mucho más rápidas en comparación con el sombreador estándar de Unity. Consulta [Uso y rendimiento de los sombreadores integrados](https://docs.unity3d.com/Manual/shader-Performance.html) para obtener información más detallada.

#### <a name="shader-preloading"></a>Precarga de sombreador

Usa la *precarga del sombreador* y otros trucos para optimizar el [tiempo de carga del sombreador](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html). En concreto, la precarga del sombreador significa que no verás ningún problema debido a la compilación del sombreador en tiempo de ejecución.

### <a name="limit-overdraw"></a>Sobredibujo del límite

En Unity, se puede mostrar el sobredibujo de la escena, alternando el [**menú de modo de dibujo**](https://docs.unity3d.com/Manual/ViewModes.html) en la esquina superior izquierda de **Scene view** (Vista de escena) y seleccionando **Overdraw** (Sobredibujar).

Por lo general, el sobredibujo se puede mitigar eliminando los objetos antes de enviarlos a la GPU. Unity proporciona información detallada sobre la implementación de la [Eliminación de oclusión](https://docs.unity3d.com/Manual/OcclusionCulling.html) para su motor.

## <a name="memory-recommendations"></a>Recomendaciones de memoria

Un número excesivo de operaciones de asignación y anulación de asignación de memoria puede tener efectos negativos en la aplicación holográfica, lo que produce un rendimiento incoherente, fotogramas inmovilizados y otro comportamiento perjudicial. Es especialmente importante comprender las consideraciones de memoria al desarrollar en Unity, ya que la administración de la memoria se controla mediante el recolector de elementos no utilizados.

#### <a name="garbage-collection"></a>Recolección de elementos no utilizados

Las aplicaciones holográficas perderán tiempo de cálculo de procesamiento en el recolector de elementos no utilizados (GC) cuando se active el GC para analizar los objetos que ya no están en el ámbito durante la ejecución y se deba liberar su memoria, a fin de que pueda estar disponible para su reutilización. Normalmente, las constantes asignaciones y anulaciones de asignación requerirán que el recolector de elementos no utilizados se ejecute con más frecuencia, con lo que se perjudica el rendimiento y la experiencia del usuario.

Unity ha proporcionado una página excelente que explica con detalle cómo funciona el recolector de elementos no utilizados y las sugerencias para escribir código más eficaz en lo que respecta a la administración de memoria.
- [Optimización de la recolección de elementos no utilizados en juegos de Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Una de las prácticas más comunes que conduce a una recolección excesiva de elementos no utilizados es no almacenar en caché las referencias para componentes y clases del desarrollo de Unity. Las referencias deben capturarse durante las funciones Start() o Awake() y se pueden volver a usar en funciones posteriores como Update() o LateUpdate().

Otras sugerencias rápidas:
- Usa la clase [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) de C# para generar dinámicamente cadenas complejas en tiempo de ejecución.
- Quita las llamadas a Debug.log() cuando ya no sean necesarias, ya que se ejecutan en todas las versiones de compilación de una aplicación.
- Si la aplicación holográfica normalmente requiere una gran cantidad de memoria, considera la posibilidad de llamar a [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante las fases de carga, como cuando se presenta una pantalla de carga o transición.

#### <a name="object-pooling"></a>Agrupación de objetos

La agrupación de objetos es una técnica popular para reducir el costo de asignaciones y anulaciones de asignación continuas de objetos. Para ello, se asigna un grupo grande de objetos idénticos y se reutilizan instancias disponibles inactivas de este grupo en lugar de generar y destruir objetos constantemente a lo largo del tiempo. Los grupos de objetos son excelentes para los componentes reutilizables que tienen una duración variable en una aplicación.

- [Tutorial de agrupación de objetos en Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Rendimiento del inicio

Considera la posibilidad de iniciar la aplicación con una escena más pequeña y, a continuación, usar *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* para cargar el resto de la escena. Esto permite a la aplicación acceder a un estado interactivo lo más rápido posible. Ten en cuenta que puede haber un gran pico de CPU mientras se activa la nueva escena y que cualquier contenido representado se puede trabar o enganchar. Una manera de solucionar este problema es establecer la propiedad AsyncOperation.allowSceneActivation en "false" en la escena que se está cargando, esperar a que se cargue, fundir a negro la pantalla y volver a establecerla en "true" para completar la activación de la escena.

Recuerda que mientras se carga la escena de inicio, se mostrará la pantalla de presentación holográfica al usuario.

## <a name="see-also"></a>Consulta también
- [Optimización de la representación de gráficos en juegos de Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Optimización de la recolección de elementos no utilizados en juegos de Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Procedimientos recomendados para la física [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Optimización de scripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
