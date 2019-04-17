---
title: Recomendaciones de rendimiento para Unity
description: Sugerencias específicas de Unity para mejorar el rendimiento con las aplicaciones de realidad mixta.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: gráficos, cpu, gpu, representación, recolección de elementos, hololens
ms.openlocfilehash: 37eac566a0315009330ac7fee96edd82348d6ba3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605746"
---
# <a name="performance-recommendations-for-unity"></a>Recomendaciones de rendimiento para Unity

Este artículo se basa en la explicación que se describen en [recomendaciones de rendimiento para realidad mixta](understanding-performance-for-mixed-reality.md) pero se centra en aprendizajes específicas del entorno de motor de Unity.

También es aconsejable que los desarrolladores revisen el [recomienda la configuración del entorno para el artículo de Unity](Recommended-settings-for-unity.md). En este artículo tiene contenido con algunas de las configuraciones de escena más importante en lo que respecta a la creación de alto rendimiento de aplicaciones de realidad mixta. También algunos de estos valores recomendados se resaltan a continuación.

## <a name="how-to-profile-with-unity"></a>Cómo generar perfiles con Unity

Unity proporciona el **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** integrado que es un excelente recurso para recopilar información de rendimiento valiosas para la aplicación concreta. Aunque puede ejecutar el generador de perfiles en el editor, estas métricas no representan el entorno en tiempo de ejecución es true y por lo tanto, los resultados de esta deben usarse con precaución. Se recomienda para el perfil de forma remota su aplicación mientras se ejecuta en el dispositivo para obtener información más precisa y útil. Además, Unity [depurador marco](https://docs.unity3d.com/Manual/FrameDebugger.html) también es muy eficaz y herramienta de información para usar.

Unity proporciona documentación excelente para:
1) Cómo conectar el [generador de perfiles de Unity para aplicaciones UWP remotamente](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Cómo eficazmente [diagnosticar problemas de rendimiento con el Profiler de Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Con el Profiler Unity conectado y después de agregar el generador de perfiles GPU (consulte *agregar Profiler* en la esquina superior derecha), puede ver cuánto tiempo se invierte en la CPU y GPU respectivamente en medio del generador de perfiles. Esto permite al desarrollador obtener una aproximación rápida si su aplicación es la CPU o GPU limitado.
>
> ![Vs para Unity CPU GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU

El siguiente contenido trata más prácticas detalladas de rendimiento, especialmente destinadas a Unity & C# desarrollo.

#### <a name="cache-references"></a>Memoria caché las referencias

Es una práctica recomendada para las referencias a todos los componentes pertinentes y GameObjects en la inicialización. Esto es porque las llamadas a funciones de repetición, como *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* es mucho más costoso en relación con el costo para almacenar un puntero de memoria. Esto también se aplica a la muy, con frecuencia utilizan [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). *Camera.Main* realmente solo usa *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* debajo que busca costosa en el gráfico de escena para un objeto de cámara con la *"MainCamera"*  etiqueta.

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

>[!NOTE] Evitar GetComponent(string) <br/>
> Cuando se usa  *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)*, hay una serie de sobrecargas diferentes. Es importante usar siempre las implementaciones en función del tipo y nunca la sobrecarga de búsqueda basada en cadena. Búsqueda por la cadena de la escena es significativamente más costosa que la búsqueda por tipo. <br/>
> (Bueno) Componente GetComponent (tipo) <br/>
> (Bueno) T GetComponent\<T >) <br/>
> (Incorrecto) Componente GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>Evite operaciones caras

1) **Evite el uso de [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Aunque LINQ puede ser muy limpia y fácil de leer y escribir, por lo general requiere cálculo mucho más y más especialmente la asignación de memoria que escribir manualmente el algoritmo de.

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

    Ciertas API de Unity, aunque es útil, puede ser muy costoso de ejecutar. La mayoría de ellos implica buscar en el gráfico de escena completa para alguna lista de búsqueda de coincidencias de GameObjects. Estas operaciones por lo general pueden evitarse mediante el almacenamiento en caché las referencias o implementar un componente de administrador para que los GameObjects en cuestión realizar el seguimiento de las referencias en tiempo de ejecución.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)*  y *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* debe eliminarse a toda costa. Estas funciones pueden ser del orden de 1000 veces más lento que las llamadas de función directa.

3) **Tenga cuidado con conversión boxing**

    [Conversión boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) es un concepto básico de la C# lenguaje y tiempo de ejecución. Es el proceso de ajuste de las variables de tipo de valor como char, int, bool, etc. en las variables con tipo de referencia. Una variable de tipo de valor es "boxing", se encapsula dentro de una clase System.Object que se almacena en el montón administrado. Por lo tanto, se asigna memoria y, finalmente, cuando se elimina debe ser procesada por el recolector de elementos no utilizados. Estas asignaciones y desasignaciones incurrir en costos de rendimiento y en muchos escenarios no son necesarias o se pueden reemplazar fácilmente por una alternativa menos costosa.

#### <a name="repeating-code-paths"></a>Repetición de las rutas de código

Las funciones de devolución de llamada Unity repetición (como) Actualización) que se ejecutan muchas veces por segundo o marco debe escribirse con mucho cuidado. Operaciones costosas aquí tendrá impacto enorme y coherente en el rendimiento.

1) **Funciones de devolución de llamada vacío**

    Aunque el código siguiente puede parecer inofensivo para dejar en su aplicación, especialmente porque cada script Unity auto-inicializa con este bloque de código, estas devoluciones de llamada vacíos pueden pasar a ser muy costosas. Unity y viceversa funciona a través de un límite de código no administrado o administrado, entre el código de UnityEngine y el código de aplicación. Cambio a través de este puente de contexto es bastante costoso, incluso si no hay nada que ejecutar. Esto es especialmente problemático si la aplicación tiene cientos de GameObjects con los componentes que tienen las devoluciones de llamada de Unity repetición vacíos.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update() es la manifestación más común de este problema de rendimiento, pero otras devoluciones de llamada de repetición Unity como la siguiente pueden ser igualmente tan malo si no peor: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **Operaciones para favorecer la ejecución de una vez por fotograma**

    Las siguientes API de Unity son operaciones comunes para muchas aplicaciones holográfica. Aunque no siempre es posible, los resultados de estas funciones con mucha frecuencia se pueden calcular una vez y volver a utilizan los resultados a través de la aplicación de un período determinado.

    (a) por lo general es recomendable tener una clase Singleton dedicado o un servicio para controlar a su mirada Raycast en la escena y, a continuación, volver a usar este resultado en todos los demás componentes de la escena, en lugar de realizar operaciones de Raycast repetidas y prácticamente idénticas por cada uno componente. Por supuesto, algunas aplicaciones pueden requerir raycasts desde diferentes orígenes o en diferentes [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    (b) evitar GetComponent() operaciones repetidas devoluciones de llamada de Unity como Update() por [almacenamiento en caché las referencias](#cache-references) en Start() o Awake()

        UnityEngine.Object.GetComponent()

    (c) es recomendable crear instancias de todos los objetos, si es posible, y use la inicialización [agrupación de objetos](#object-pooling) reciclar y volver a utilizar GameObjects a lo largo del tiempo de ejecución de la aplicación

        UnityEngine.Object.Instantiate()

3) **Evitar interfaces y construcciones virtuales**

    Invocar llamadas a funciones a través de interfaces frente a direct objetos o llamar a funciones virtuales a veces puede consumir mucho más caros que utilizando construcciones directas o llamadas de función directa. Si la función virtual o la interfaz no es necesario, se debe quitar. Sin embargo, el rendimiento de aciertos de estos enfoques son generalmente vale la pena el equilibrio si aprovechando simplifica la colaboración de desarrollo, la legibilidad del código y mantenimiento del código. 

4) **Evitar las estructuras de pasar por valor**

    A diferencia de las clases, structs son tipos de valor y cuando se pasa directamente a una función, su contenido se copia en una instancia recién creada. Esta copia agrega, así como memoria adicional en la pila el costo de CPU. Para los structs pequeño, el efecto es generalmente muy mínima y, por tanto, aceptable. Sin embargo, para funciones invocan repetidamente cada fotograma, así como funciones que tardan las estructuras de gran tamaño, si es posible modificar la definición de función para pasar por referencia. [Obtenga más información aquí](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Varios

1) **Física**

    (a) por lo general, la manera más fácil para mejorar la física es limitar la cantidad de tiempo invertido en física o el número de iteraciones por segundo. Por supuesto, esto reducirá la precisión de la simulación. Consulte [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) en Unity

    (b) el tipo de colisionadores en Unity tiene características de rendimiento muy diferentes. El orden siguiente enumera la mayoría colisionadores de alto rendimiento a menor colisionadores de alto rendimiento de izquierda a derecha. Es más importante evitar Colisionadores de malla que son considerablemente más costoso que el primitivos colisionadores.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Consulte [prácticas recomendadas de Unity física](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) para obtener más información

2) **Animaciones**

    Deshabilitar las animaciones inactivas al deshabilitar el componente de Animador (deshabilitar el objeto de juego tendrá el mismo efecto). Evite los patrones de diseño donde se ubica una animación en un bucle que establecer un valor a la misma cosa. Hay una sobrecarga considerable para que esta técnica no tiene ningún efecto en la aplicación. [Obtenga más información aquí.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Algoritmos complejos**

    Si la aplicación utiliza algoritmos complejos como cinemática inversa, búsqueda de ruta de acceso, etcetera, buscar para buscar un enfoque más sencillo o ajustar la configuración pertinente de su rendimiento

## <a name="cpu-to-gpu-performance-recommendations"></a>Recomendaciones de rendimiento de la CPU al GPU

Por lo general, el rendimiento de CPU al GPU viene abajo hasta la **llamadas a draw** enviadas a la tarjeta gráfica. Para mejorar el rendimiento, las llamadas a draw deben ser estratégicamente **) reduce** o **b) reestructurado** para obtener resultados óptimos. Puesto que las llamadas de dibujo a sí mismos son intensivo de recursos, lo que reduce su reducirá trabajo general necesario. Además, los cambios entre las llamadas a draw requiere validación costoso y los pasos de traducción en el controlador de gráficos de estado y por lo tanto, se reestructurarán las llamadas a draw de la aplicación para limitar los cambios de estado (como) materiales diferentes, etcetera) puede mejorar el rendimiento.

Unity ofrece un excelente artículo que ofrece información general y profundiza en llamadas a draw para su plataforma de procesamiento por lotes.
- [Unity dibujar llamada procesamiento por lotes](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Representación con instancias de paso único

Representación de un solo paso Instanced en Unity permite llamadas a draw para todos los ojos a reducirse hasta la llamada a draw con instancias uno. Debido a la coherencia entre las dos llamadas de dibujo de la caché, también hay ciertas mejoras de rendimiento en la GPU también.

Para habilitar esta característica en el proyecto de Unity
1)  Abra **configuración del Reproductor XR** (vaya a **editar** > **configuración del proyecto** > **Reproductor**  >  **Configuración XR**)
2) Seleccione **pasar una instancia única** desde el **el método de representación estéreo** menú desplegable (**admite la realidad Virtual** casilla debe estar seleccionada)

Lea los artículos siguientes de Unity para obtener más información con este enfoque de representación.
- [Cómo maximizar el rendimiento de AR y VR con representación estéreo avanzada](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creación de instancias de un solo paso](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Se produce un problema común con solo pasar una instancia de representación si los desarrolladores ya tienen sombreadores personalizados existentes no escritos para creación de instancias. Después de habilitar esta característica, los desarrolladores que observe algún procesamiento solo GameObjects en un ojo. Esto es porque los sombreadores personalizados asociados no tienen las propiedades adecuadas para la creación de instancias.
>
> Consulte [solo pasar estéreo de representación de HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) desde Unity para abordar este problema

#### <a name="static-batching"></a>El procesamiento por lotes estático

Unity es capaz de procesar por lotes demasiados objetos static para reducir las llamadas de dibujo a la GPU. El procesamiento por lotes estática funciona para la mayoría [representador](https://docs.unity3d.com/ScriptReference/Renderer.html) objetos de Unity que **(1) comparten el mismo material de** y **2) son todas marcadas como *estático***  () Seleccione un objeto en Unity y haga clic en la casilla de verificación en la parte superior derecha del inspector de). GameObjects marcado como *estático* no se puede mover a lo largo del tiempo de ejecución de la aplicación. Por lo tanto, puede ser difícil aprovechar en HoloLens donde debe colocarse, mover, escala, etcetera prácticamente todos los objetos estáticos de procesamiento por lotes. Para inmersivos, los estáticos de procesamiento por lotes puede reducir drásticamente las llamadas a draw y, por tanto, mejorar el rendimiento.

Lectura *estático de procesamiento por lotes* en [dibujar llame al procesamiento por lotes en Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para obtener más detalles.

#### <a name="dynamic-batching"></a>El procesamiento por lotes dinámico

Puesto que es problemático para marcar objetos como *estático* para el desarrollo de HoloLens, el procesamiento por lotes dinámico puede ser una excelente herramienta para compensarlo que carecen de característica. Por supuesto, es puede también resultar útil en inmersivos también. Dinámica de procesamiento por lotes en Unity puede ser difícil Aunque habilitar porque debe GameObjects **) compartir el mismo Material** y **b) cumplir con una larga lista de otros criterios**.

Lectura *dinámica de procesamiento por lotes* en [dibujar llame al procesamiento por lotes en Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) para ver la lista completa. Normalmente, GameObjects dejan de ser válidos para procesar por lotes dinámicamente porque los datos de la malla asociado pueden ser no más de 300 vértices.

#### <a name="other-techniques"></a>otras técnicas

Procesamiento por lotes sólo puede ocurrir si se pueden compartir el mismo material de varias GameObjects. Normalmente esto bloqueará la necesidad de GameObjects disponer de una textura única para su respectivo Material. Es habitual combinar las texturas en una textura grande, un método conocido como [Atlasing textura](https://en.wikipedia.org/wiki/Texture_atlas).

Además, es preferible generalmente para combinar las mallas en un GameObject donde sea posible y razonable. Cada representador en Unity hará que se ha asociado las llamadas de dibujo frente al envío de una malla combinada en un representador. 

>[!NOTE]
> Modificar las propiedades de Renderer.material en tiempo de ejecución creará una copia del Material y, por tanto, afectar el procesamiento por lotes. Utilice Renderer.sharedMaterial para modificar las propiedades de material compartidas entre GameObjects.

## <a name="gpu-performance-recommendations"></a>Recomendaciones de rendimiento de GPU

Obtenga más información sobre [optimización de la representación de gráficos en Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

#### <a name="reduce-poly-count"></a>Reducir el número de poli

Normalmente se reduce el número de polígonos, ya sea por
1) Quitar objetos de una escena
2) Diezmado activos lo que reduce el número de polígonos de una malla determinada
3) Implementar un [System de nivel de detalle (LOD)](https://docs.unity3d.com/Manual/LevelOfDetail.html) en la aplicación que procesa lejos estén los objetos con la versión de polígono de inferior de la misma geometría

#### <a name="limit-overdraw"></a>Límite de sobredibujo

En Unity, uno puede mostrar el sobredibujo para su escena, alternando el [ **dibujar menú modo de** ](https://docs.unity3d.com/Manual/ViewModes.html) en la esquina superior izquierda de la **vista de escena** y seleccionando **Sobredibujo** .

Por lo general, el sobredibujo se puede mitigar mediante el sacrificio de objetos antes de tiempo antes de enviarlos a la GPU. Unity proporciona detalles sobre cómo implementar [oclusión de caras traseras](https://docs.unity3d.com/Manual/OcclusionCulling.html) para su motor.

#### <a name="understanding-shaders-in-unity"></a>Sombreadores de descripción en Unity

Una sencilla aproximación para comparar a los sombreadores en el rendimiento es identificar el número promedio de operaciones cada que se ejecuta en tiempo de ejecución. Esto puede hacerse fácilmente en Unity.

1) Seleccione el recurso de sombreador o seleccione un material, en la esquina superior derecha de la ventana del inspector, seleccione el icono de engranaje y, a continuación, **"Seleccione sombreador"**

    ![Seleccione el sombreador de Unity](images/Select-shader-unity.png)
2) Con el recurso de sombreador seleccionado, haga clic en el **"Compilar y mostrar el código"** botón en la ventana del inspector

    ![Compilar el código del sombreador de Unity](images/compile-shader-code-unity.PNG)

3) Después de compilar, busque la sección de estadísticas en los resultados con el número de operaciones diferentes para el sombreador de píxeles y vértices (Nota: los sombreadores de píxeles se denominan a menudo también los sombreadores de fragmento)

    ![Operaciones estándar de sombreador de Unity](images/unity-standard-shader-compilation.png)

##### <a name="unity-standard-shader-alternatives"></a>Alternativas de estándar de sombreador de Unity

En lugar de una representación basada en físicamente (PBR) u otro sombreador de alta calidad, examine el uso de un mayor rendimiento y el sombreador más barato. [Mixto realidad Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona un [sombreador estándar](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader) que se ha optimizado para los proyectos de realidad mixta.

Unity también proporciona un apagado, vértice iluminado, sombras simplificada difuso y otras opciones que son significativamente más rápido si se compara con el sombreador de Unity estándar. Consulte [uso y rendimiento de sombreadores integrados](https://docs.unity3d.com/Manual/shader-Performance.html) para obtener más información.

## <a name="memory-recommendations"></a>Recomendaciones de memoria

Las operaciones de asignación y desasignación de memoria excesivo pueden tener efectos adversos sobre su aplicación holográfica, dando como resultado un rendimiento incoherente, marcos inmovilizados y otro comportamiento perjudicial. Es especialmente importante entender las consideraciones de memoria al desarrollar en Unity, puesto que la administración de memoria se controla mediante el recolector de elementos no utilizados.

#### <a name="garbage-collection"></a>Recolección de elementos

Aplicaciones holográficas perderá el tiempo de proceso de procesamiento para el recolector de elementos no utilizados (GC) cuando se activa el GC para analizar los objetos que ya no están en ámbito durante la ejecución y su memoria debe liberarse por lo que puede hacer disponible para su reutilización. Desasignación y asignaciones de constantes por lo general requerirá el recolector de elementos ejecutar con más frecuencia negativa, por tanto, rendimiento y experiencia del usuario.

Unity ha proporcionado una página excelente que se explica en detalle cómo funciona el recolector de elementos no utilizados y sugerencias para escribir código más eficaz en lo que respecta a la administración de memoria.
- [Optimizar la recolección de elementos no utilizados en los juegos de Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Una de las prácticas más comunes que conduce a una excesiva recolección no almacena en caché las referencias a componentes y las clases en el desarrollo de Unity. Deben ser capturadas durante Start() o Awake() y volver a usar en funciones más adelante como Update() o LateUpdate() todas las referencias.

Otras sugerencias rápidas:
- Use la [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# clase para generar dinámicamente cadenas complejas en tiempo de ejecución
- Quite las llamadas a Debug.Log() cuando ya no necesite mientras se ejecutan todavía en todas las versiones de compilación de una aplicación
- Si su aplicación holográfica generalmente requiere una gran cantidad de memoria, considere la posibilidad de llamar a [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) durante las fases de carga, como cuando se presenta una carga o pantalla de transición

#### <a name="object-pooling"></a>Agrupación de objetos

Agrupación de objetos es una técnica popular para reducir el costo de las asignaciones continua y las cancelaciones de asignación de objetos. Esto se hace mediante la asignación de un grupo grande de objetos idénticos y volver a usar las instancias inactivas, disponibles desde este grupo en lugar de generar constantemente y destruir objetos con el tiempo. Los grupos de objetos son excelentes para los componentes puedan volver a utilizar con duración de la variable durante una aplicación.

- [Tutorial de Unity de agrupación de objetos](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Rendimiento de inicio

Puede iniciar la aplicación con una escena más pequeña, a continuación, usar *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* para cargar el resto de la escena. Esto permite que la aplicación llegar a un estado interactivo tan rápido como sea posible. Se puede tener en cuenta que puede haber un gran aumento de CPU mientras se está activando la nueva escena y que cualquier contenido representado es posible que sufra interrupciones o problemas. Una manera de solucionar este problema consiste en establecer la propiedad AsyncOperation.allowSceneActivation en false en la escena que se está cargando, espere a que la escena para cargar, desactive la pantalla en negro y, a continuación, vuelve a establecer en true para completar la activación de la escena.

Recuerde que, mientras se está cargando la escena de inicio se mostrará la pantalla de presentación holográfica al usuario.

## <a name="see-also"></a>Vea también
- [Optimización de la representación de gráficos de juegos Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Optimizar la recolección de elementos no utilizados en los juegos de Unity](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Prácticas recomendadas de leyes físicas [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Optimización de las secuencias de comandos [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
