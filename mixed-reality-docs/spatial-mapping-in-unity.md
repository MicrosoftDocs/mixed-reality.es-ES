---
title: Asignación espacial en Unity
description: Representación y chocar con la geometría del mundo real que le rodea en Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, asignación espacial, representador, colisionador, malla, el análisis, componente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148649"
---
# <a name="spatial-mapping-in-unity"></a>Asignación espacial en Unity

Este tema describe cómo usar [asignación espacial](spatial-mapping.md) en el proyecto de Unity, recuperar las mallas de triangulares que representan las superficies del mundo en torno a un dispositivo HoloLens, para la colocación, oclusión, análisis de la sala y mucho más.

Unity es totalmente compatible con la asignación espacial, que se expone a los desarrolladores de las maneras siguientes:
1. Asignación de componentes disponibles en el MixedRealityToolkit espaciales, que proporcionan una ruta cómoda y rápida para comenzar con la asignación espacial
2. Asignación espacial de nivel inferior API, que proporcionan un completo control y permiten la personalización específica de aplicación más sofisticada

Para usar asignación espacial en la aplicación, la capacidad de spatialPerception debe establecerse en su AppxManifest.

## <a name="setting-the-spatialperception-capability"></a>Establecer la capacidad de SpatialPerception

En el orden de una aplicación consumir datos de asignación espacial, debe habilitarse la capacidad de SpatialPerception.

Cómo habilitar la funcionalidad de SpatialPerception:
1. En el Editor de Unity, abra el **"Configuración del Reproductor"** panel (Editar > configuración del proyecto > Reproductor)
2. Haga clic en el **"Windows Store"** ficha
3. Expanda **"Configuración de publicación"** y compruebe el **"SpatialPerception"** capacidad en el **"Capacidades"** lista

Tenga en cuenta que si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o manualmente [establecer esta funcionalidad en el AppxManifest en Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Asignación espacial también requiere un MaxVersionTested de al menos 10.0.10586.0:
1. En Visual Studio, haga clic en **Package.appxmanifest** en el Explorador de soluciones y seleccione **ver código**
2. Busque la línea especifica **TargetDeviceFamily** y cambiar **MaxVersionTested = "10.0.10240.0"** a **MaxVersionTested = "10.0.10586.0"**
3. **Guardar** Package.appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introducción a los componentes de asignación espacial integradas de Unity

Unity ofrece 2 componentes para agregar fácilmente la asignación espacial a su aplicación, **representador de asignación espacial** y **espacial Colisionador asignación**.

### <a name="spatial-mapping-renderer"></a>Representador de asignación espacial

El representador de asignación espacial permite la visualización de la malla de asignación espacial.

![Asignación espacial representador en Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Asignación espacial Colisionador

Permite el Colisionador asignación espacial holográfica contenido (o carácter) interacción, como física, con la malla de asignación espacial.

![Asignación espacial Colisionador en Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Con los componentes integrados asignación espacial

Puede agregar ambos componentes a la aplicación si desea que tanto visualizar e interactuar con las superficies físico.

Para usar estos dos componentes en la aplicación de Unity:
1. Seleccione un GameObject en el centro del área en la que le gustaría detectar las mallas de superficie espaciales.
2. En la ventana del Inspector, **Agregar componente** > **XR** > **Colisionador asignación espacial** o **espacial Representador de asignación**.

Puede encontrar más detalles sobre cómo usar estos componentes en el <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">sitio de documentación de Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Ir más allá de los componentes integrados asignación espacial

Estos componentes facilitan arrastrar y colocar fácil empezar a trabajar con la asignación espacial.  Cuando desea ir más allá, hay dos formas de explorar:
* Para realizar el procesamiento de la malla de nivel inferior, vea la sección siguiente sobre el script de bajo nivel de asignación espacial API.
* Para realizar análisis de malla de nivel superior, consulte la sección acerca de la biblioteca SpatialUnderstanding en <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Utilizando el Unity espacial asignación de API de bajo nivel

Si necesita más control que obtendrá de los componentes de representador asignación espacial y Colisionador asignación espacial, puede usar el script de asignación espacial bajo nivel API.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipos**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

El siguiente es un esquema del flujo sugerido para una aplicación que utiliza la API de asignación espacial.

### <a name="set-up-the-surfaceobservers"></a>Configurar la SurfaceObserver(s)

Crear una instancia de un objeto SurfaceObserver para cada región definida por la aplicación de espacio que necesita datos de asignación espacial para.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Especificar la región del espacio que cada objeto SurfaceObserver proporcionará datos para llamar al método SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. Basta con volver a llamar a uno de estos métodos puede volver a definir la región de espacio en el futuro.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Cuando se llama a SurfaceObserver.Update(), debe proporcionar un controlador para cada superficie espacial en región del SurfaceObserver de espacio que el sistema de asignación espacial tiene nueva información de. El controlador recibe de una superficie espacial:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Control de cambios superficiales

Hay varios casos principales para controlar. Agregar & actualizado que puede usar la misma ruta de acceso y se eliminan de código.
* En los casos Added & actualizado en el ejemplo, se agrega u obtener el GameObject que representa esto de malla del diccionario, creación de un struct SurfaceData con los componentes necesarios y luego llamar a RequestMeshDataAsync para rellenar el GameObject con los datos de la malla y posición en la escena.
* En el caso de quitado, se quita el GameObject que representa esta malla del diccionario y destruirlo.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a>Listas de control de datos

El controlador de OnDataReady recibe un objeto SurfaceData. El WorldAnchor, MeshFilter y (opcionalmente) MeshCollider objetos que contiene reflejan el estado más reciente de la superficie espacial asociado. Opcionalmente, realizar análisis o [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla mediante el acceso a los miembros de malla del objeto MeshFilter. Representar la superficie espacial con la malla más reciente y (opcionalmente) se utiliza para conflictos de leyes físicas y raycasts. Es importante confirmar que el contenido de la SurfaceData no es null.

### <a name="start-processing-on-updates"></a>Iniciar el procesamiento de las actualizaciones

SurfaceObserver.Update() debe llamarse en un retraso, no en cada fotograma.

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Análisis de la malla de nivel superior: SpatialUnderstanding

El <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> es una colección de código de la utilidad de ayuda para el desarrollo holográfico basado las API de Unity holográfica.

### <a name="spatial-understanding"></a>Understanding espacial

Al colocar hologramas en el mundo físico suele ser deseable para ir más allá de la asignación espacial de la malla y planos de la superficie. Cuando la selección de ubicación se realiza mediante procedimientos, es deseable un mayor nivel de comprensión del entorno. Esto requiere generalmente tomar decisiones sobre las novedades de las paredes, ceiling y floor. Además, la capacidad de optimizar con un conjunto de restricciones de colocación para determinar las ubicaciones físicas más conveniente para los objetos holográficas.

Durante el desarrollo de fragmentos y Conker Young, Asobo Studios que afrontar este problema sin rodeos, desarrollo de un solucionador de espacio para este propósito. Cada uno de estos juegos tenía juego necesidades específicas, pero comparten core espacial descripción de la tecnología. Coloca el HoloToolkit.SpatialUnderstanding biblioteca encapsula esta tecnología, lo que permite que a rápidamente buscar espacios en blanco en las paredes, los objetos de contexto en el techo, identificar para carácter estar sentado y un sinnúmero de otras consultas espaciales descripción.

Todo el código fuente se incluye, lo que permite personalizar según sus necesidades y compartir sus mejoras con la Comunidad. El código para el C++ solver se ha ajustado en un archivo dll UWP y expuestos a Unity con una disminución en el prefabricado verá dentro de la MixedRealityToolkit.

### <a name="understanding-modules"></a>Módulos de descripción

Hay tres interfaces principales expuestas por el módulo: topología de superficie simple y consultas espaciales, forma para la detección de objeto y el Solucionador de selección de ubicación del objeto para la colocación de restricción en función de los conjuntos de objetos. Cada una de ellas se describe a continuación. Además de las tres interfaces de módulo principal, una interfaz de la conversión de ray puede usarse para recuperar tipos de superficie con etiquetas y una malla playspace estanca personalizados se puede copiar.

### <a name="ray-casting"></a>Ray conversión

Después de haber analizado y finaliza la sala, las etiquetas se hayan generado internamente para superficies como paredes, ceiling y floor. El "PlayspaceRaycast" función toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y si es así, la información sobre la que se muestran en forma de un "RaycastResult".

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

Internamente, el raycast es calculado con respecto a la representación de voxel calculada 8cm al cubo de la playspace. Cada voxel contiene un conjunto de elementos de superficie con datos de la topología procesados (también conocido como surfels). Se comparan los surfels dentro de la celda voxel intersectado y la mejor coincidencia utilizada para buscar la información de topología. Estos datos de la topología contienen el etiquetado devuelto en el formulario de la enumeración "SurfaceTypes", así como el área expuesta de la superficie de intersección.

En el ejemplo de Unity, el cursor convierte un rayo cada fotograma. En primer lugar, con colisionadores de Unity. En segundo lugar, con representación de mundo del módulo de la descripción. Y por último, vuelva a elementos de IU. En esta aplicación, la interfaz de usuario obtiene la prioridad, a continuación el resultado de la descripción y, por último, colisionadores de Unity. El SurfaceType se notifica como texto situado junto al cursor.

![Tipo de superficie tiene la etiqueta situado junto al cursor](images/su-raycastresults-300px.jpg)<br>
*Tipo de superficie tiene la etiqueta situado junto al cursor*

### <a name="topology-queries"></a>Consultas de topología

En el archivo DLL, el Administrador de la topología controla etiquetado del entorno. Como se mencionó anteriormente, gran parte de los datos se almacena en surfels, dentro de un volumen voxel. Además, la estructura "PlaySpaceInfos" se usa para almacenar información sobre la playspace, incluida la alineación del mundo (más detalles en este tema), floor y ceiling de alto. Se utiliza la heurística para determinar las paredes, ceiling y floor. Por ejemplo, la superficie más grande y más baja horizontal con más de 1 área expuesta de m2 se considera el suelo. Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de análisis también se usa en este proceso.

Un subconjunto de consultas expuestas por el Administrador de topología se exponen fuera a través de la dll. Las consultas de topología expuestas son los siguientes.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Cada una de las consultas tiene un conjunto de parámetros, el tipo de consulta específicos. En el ejemplo siguiente, el usuario especifica el alto mínimo anc & ho del volumen deseado, el alto mínimo de la selección de ubicación por encima el suelo y la cantidad mínima de limpieza delante el volumen. Todas las medidas son en metros.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada una de estas consultas toma una matriz de estructuras "TopologyResult" preasignada. El parámetro "locationCount" especifica la longitud de la matriz pasada. El valor devuelto indica el número de ubicaciones devueltas. Este número nunca es mayor que ha pasado en el parámetro "locationCount".

El "TopologyResult" contiene la posición central de las dimensiones del espacio se encuentra, la dirección opuesta (es decir, normal) y el volumen devuelto.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculado a un botón en el panel de interfaz de usuario virtual. El disco duro de ejemplo códigos de los parámetros para cada una de estas consultas para valores razonables. En el código de ejemplo para obtener más ejemplos, consulte SpaceVisualizer.cs.

### <a name="shape-queries"></a>Consultas de forma

Dentro de la dll, el analizador de forma ("ShapeAnalyzer_W") usa el analizador de topología para coincidir con las formas personalizadas definidas por el usuario. El ejemplo de Unity define un conjunto de formas y muestra los resultados de salida a través del menú de la consulta en la aplicación, dentro de la pestaña de la forma. La intención es que el usuario puede definir sus propias consultas de forma de objeto y asegúrese de usar de ellas, según sea necesario para su aplicación.

Tenga en cuenta que el análisis de forma funciona en las superficies horizontales. Por ejemplo, un sofá, se define por la superficie del asiento sin formato y la parte superior plana de vuelta el sofá. La consulta shape busca dos superficies de un intervalo de tamaño, el alto y el aspecto específico, con las dos superficies alineado y conectado. Con la terminología de API, el sofá puesto y el back-superior son componentes de la forma y los requisitos de alineación son las restricciones de componentes de forma.

Una consulta de ejemplo que se define en el ejemplo de Unity (ShapeDefinition.cs), para los objetos "sittable" es el siguiente.

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

Cada consulta shape se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componente y un conjunto de restricciones de forma que enumerar las dependencias entre los componentes. En este ejemplo incluye tres restricciones en una definición de componente único y sin restricciones de forma entre los componentes (como hay solo un componente).

En cambio, la forma del sofá tiene dos componentes de la forma y cuatro de las restricciones de forma. Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Se proporcionan funciones de contenedor en el módulo de Unity para la creación fácil de definiciones de forma personalizada. Encontrará la lista completa de las restricciones de componente y la forma de "SpatialUnderstandingDll.cs" dentro de la "ShapeComponentConstraint" y las estructuras de "ShapeConstraint".

![Forma de rectángulo se encuentra en esta superficie](images/su-shapequery-300px.jpg)<br>
*Forma de rectángulo se encuentra en esta superficie*

### <a name="object-placement-solver"></a>Solucionador de selección de ubicación del objeto

El Solucionador de selección de ubicación del objeto puede utilizarse para identificar las ubicaciones ideales en la sala física para colocar los objetos. El solucionador encontrará que el que mejor ajusta según las reglas de objeto y las restricciones de ubicación. Además, las consultas de objeto se mantienen hasta que se quita el objeto con "Solver_RemoveObject" o "Solver_RemoveAllObjects", lo que permite las llamadas restringido de colocación de varios objetos. Las consultas de selección de ubicación de los objetos se componen de tres partes: un tipo de colocación con parámetros, una lista de reglas y una lista de restricciones. Para ejecutar una consulta, use la siguiente API.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

Esta función toma un nombre de objeto, definición de la selección de ubicación y una lista de reglas y restricciones. El C# contenedores proporciona construcción funciones auxiliares para facilitar la construcción de la regla y la restricción. La definición de la selección de ubicación contiene el tipo de consulta: es decir, uno de los siguientes.

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

Cada uno de los tipos de posición tiene un conjunto de parámetros únicos para el tipo. La estructura de "ObjectPlacementDefinition" contiene un conjunto de funciones auxiliares estáticos para crear estas definiciones. Por ejemplo, para encontrar un lugar para colocar un objeto en el suelo, puede usar la función siguiente. público estático ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) además de para el tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones. No se puede infringir las reglas. Ubicaciones posibles de la selección de ubicación que cumplen el tipo y las reglas están optimizadas, a continuación, en el conjunto de restricciones con el fin de seleccionar la ubicación de la ubicación óptima. Cada una de las reglas y restricciones se puede crear las funciones de creación estático proporcionado. A continuación, se proporciona una función de construcción de restricción y regla de ejemplo.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

El siguiente objeto de consulta de selección de ubicación está buscando un lugar para colocar un cubo de la mitad del medidor en el borde de una superficie, fuera de sí previamente colocar objetos y cerca del centro de la sala de.

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

Si se realiza correctamente, una estructura de "ObjectPlacementResult" que contiene la posición de colocación, dimensiones y la orientación se devuelve. Además, la selección de ubicación se agrega a la lista interna de la dll de objetos colocados. Las consultas posteriores de la selección de ubicación tendrá este objeto en la cuenta. El archivo "LevelSolver.cs" en el ejemplo de Unity contiene más de las consultas de ejemplo.

![Resultados de la posición de los objetos](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: Cuadros de selección azul cómo el resultado de lugar tres participar en las consultas con fuera de las reglas de posición de cámara*

Al resolver para la ubicación de colocación de varios objetos necesarios para un escenario de aplicación o nivel, resolver primero objetos indispensables y de gran tamaño con el fin de maximizar la probabilidad de que se puede encontrar un espacio. Es importante el orden de selección de ubicación. Si no se puede encontrar las selecciones de ubicación del objeto, intente configuraciones menos restringidas. Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de espacio.

### <a name="room-scanning-process"></a>Proceso de exploración de sala

Mientras la solución de asignación espacial proporcionada por el HoloLens está diseñada para ser lo suficientemente genéricos como para satisfacer las necesidades de toda la gama de espacios del problema, el módulo de comprensión espaciales se generó para admitir las necesidades de dos juegos específicos. Su solución está estructurada en torno a un proceso específico y un conjunto de supuestos, resumida a continuación.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Controlada por playspace "pintar" – durante la fase de análisis, el usuario, el usuario se mueve y mira alrededor reproduce el ritmo, pintar eficazmente las áreas que deben incluirse. La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase. En el interior de inicio o de instalación de office: la consulta de funciones están diseñadas en torno a las superficies planas y paredes ángulos rectos. Esta es una limitación temporal. Sin embargo, durante la fase de análisis, se completa un análisis del eje principal para optimizar la teselación de malla a lo largo del eje principal y secundaria. El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis. Llama a las funciones siguientes.

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

El flujo de análisis controlado por el comportamiento de "SpatialUnderstanding" llama InitScan, a continuación, UpdateScan cada fotograma. Cuando informa de la consulta de estadísticas de cobertura razonable, se permite al usuario airtap para llamar a RequestFinish para indicar el final de la fase de análisis. UpdateScan continúa llamada hasta que devueltos es el valor indica que el archivo dll ha completado el procesamiento.

### <a name="understanding-mesh"></a>Malla de descripción

El archivo dll de la descripción almacena internamente el playspace como una cuadrícula de 8cm tamaño voxel cubos. Durante la parte inicial del análisis, se completa un análisis del componente principal para determinar los ejes de la sala. Internamente, almacena su espacio voxel alineado para estos ejes. Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie desde el volumen voxel. 

![Malla generado producidos desde el volumen voxel](images/su-custommesh.jpg)<br>
*Malla generado producidos desde el volumen voxel*

## <a name="troubleshooting"></a>Solución de problemas
* Asegúrese de que ha establecido la [SpatialPerception](#setting-the-spatialperception-capability) capacidad
* Cuando se pierde el seguimiento, el siguiente evento OnSurfaceChanged quitará todas las mallas.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Asignación espacial en el Kit de herramientas de realidad mixta
Para obtener más información sobre el uso de la asignación espacial con el Kit de herramientas de realidad mixta v2, consulte el <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sección reconocimiento espacial</a> de los documentos MRTK.

## <a name="see-also"></a>Vea también
* [MR Spatial 230: asignación espacial](holograms-230.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Sistemas de coordenadas de Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
