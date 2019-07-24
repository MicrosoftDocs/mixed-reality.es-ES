---
title: Asignación espacial en Unity
description: Representación y colisión con la geometría del mundo real en su lugar en Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, asignación espacial, representador, Colisionador, malla, exploración, componente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148649"
---
# <a name="spatial-mapping-in-unity"></a>Asignación espacial en Unity

En este tema se describe cómo usar la [asignación espacial](spatial-mapping.md) en el proyecto de Unity, con lo que se recuperan mallas triangulares que representan las superficies del mundo en torno a un dispositivo HoloLens, para la selección de ubicación, la oclusión, el análisis de habitación y mucho más.

Unity incluye compatibilidad total con la asignación espacial, que se expone a los desarrolladores de las siguientes maneras:
1. Componentes de asignación espacial disponibles en MixedRealityToolkit, que proporcionan una ruta de acceso cómoda y rápida para empezar a trabajar con la asignación espacial
2. API de asignación espacial de nivel inferior, que proporcionan control total y permiten una personalización específica de la aplicación más sofisticada.

Para usar la asignación espacial en la aplicación, debe establecerse la funcionalidad spatialPerception en el AppxManifest.

## <a name="setting-the-spatialperception-capability"></a>Establecimiento de la funcionalidad SpatialPerception

Para que una aplicación consuma datos de asignación espacial, la funcionalidad SpatialPerception debe estar habilitada.

Cómo habilitar la funcionalidad SpatialPerception:
1. En el editor de Unity, abra el panel de **configuración del reproductor** (Editar > configuración del proyecto > Player).
2. Haga clic en la pestaña **"tienda Windows"**
3. Expanda **"configuración de publicación"** y seleccione la funcionalidad **"SpatialPerception"** en la lista **"funcionalidades"** .

Tenga en cuenta que si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o [establecer manualmente esta funcionalidad en el AppxManifest de Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

La asignación espacial también requiere un MaxVersionTested de al menos 10.0.10586.0:
1. En Visual Studio, haga clic con el botón derecho en **Package. appxmanifest** en el explorador de soluciones y seleccione **Ver código** .
2. Busque la línea que especifica **TargetDeviceFamily** y cambie **MaxVersionTested = "10.0.10240.0"** por **MaxVersionTested = "10.0.10586.0"**
3. **Guarde** el paquete. appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introducción a los componentes de asignación espacial integrados de Unity

Unity ofrece 2 componentes para agregar fácilmente la asignación espacial a la aplicación, el representador de **asignación espacial** y el Colisionador de **asignación espacial**.

### <a name="spatial-mapping-renderer"></a>Representador de asignación espacial

El representador de asignación espacial permite la visualización de la malla de asignación espacial.

![Representador de asignación espacial en Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Colisionador de asignación espacial

El Colisionador de asignación espacial permite la interacción de contenido holográfica (o de caracteres), como la física, con la malla de asignación espacial.

![Colisionador de asignación espacial en Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Usar los componentes de asignación espacial integrados

Puede Agregar ambos componentes a la aplicación si desea visualizar y interactuar con las superficies físicas.

Para usar estos dos componentes en la aplicación de Unity:
1. Seleccione un GameObject en el centro del área en la que desea detectar mallas de superficie espacial.
2. En la ventana del inspector, **agregue el elemento** > Colisionador de**asignación espacial** del componente**XR** > o el representador de **asignación espacial**.

Puede encontrar más detalles sobre cómo usar estos componentes en el sitio de <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">documentación de Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Ir más allá de los componentes de asignación espacial integrados

Estos componentes facilitan la tarea de arrastrar y colocar para empezar a trabajar con la asignación espacial.  Si desea continuar, hay dos rutas principales para explorar:
* Para realizar su propio procesamiento de malla de nivel inferior, consulte la sección siguiente sobre la API de script de asignación espacial de bajo nivel.
* Para realizar análisis de malla de nivel superior, consulte la sección siguiente sobre la biblioteca SpatialUnderstanding en <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Uso de la API de asignación espacial de Unity de bajo nivel

Si necesita más control de los que obtiene del representador de asignación espacial y los componentes de Colisionador de asignación espacial, puede usar las API de script de asignación espacial de bajo nivel.

**System.IO** *UnityEngine. XR. WSA*<br>
**Tipos**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

A continuación se describe el flujo sugerido para una aplicación que usa las API de asignación espacial.

### <a name="set-up-the-surfaceobservers"></a>Configuración de los SurfaceObserver

Cree una instancia de un objeto SurfaceObserver para cada región de espacio definida por la aplicación para la que necesite datos de asignación espacial.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Especifique la región de espacio para la que cada objeto SurfaceObserver proporcionará los datos mediante una llamada a SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. Para volver a definir la región de espacio en el futuro, simplemente vuelva a llamar a uno de estos métodos.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Cuando se llama a SurfaceObserver. Update (), debe proporcionar un controlador para cada superficie espacial en la región de espacio de SurfaceObserver para la que el sistema de asignación espacial tiene información nueva. El controlador recibe, para una superficie espacial:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Control de cambios de superficie

Hay varios casos principales que se deben controlar. Se ha agregado & actualizado que puede usar la misma ruta de código y se ha quitado.
* En los casos agregados & actualizados en el ejemplo, se agrega u obtiene el GameObject que representa esta malla del diccionario, se crea un struct SurfaceData con los componentes necesarios y, después, se llama a RequestMeshDataAsync para rellenar el GameObject con los datos de la malla y posición en la escena.
* En el caso de que se quite, se quita el GameObject que representa esta malla del diccionario y se destruye.

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

### <a name="handling-data-ready"></a>Controlar los datos preparados

El controlador OnDataReady recibe un objeto SurfaceData. Los objetos WorldAnchor, MeshFilter y (opcionalmente) MeshCollider que contiene reflejan el estado más reciente de la superficie espacial asociada. Opcionalmente, realice el análisis y/o el [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla mediante el acceso al miembro de la malla del objeto MeshFilter. Represente la superficie espacial con la malla más reciente y, opcionalmente, Úsela para las colisiones físicas y raycasts. Es importante confirmar que el contenido de SurfaceData no es NULL.

### <a name="start-processing-on-updates"></a>Iniciar el procesamiento en las actualizaciones

Se debe llamar a SurfaceObserver. Update () en un retraso, no en todos los fotogramas.

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Análisis de malla de nivel superior: SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> es una colección de código de utilidad útil para el desarrollo holográfica basado en las API de Unity de Holographic.

### <a name="spatial-understanding"></a>Descripción espacial

Al colocar hologramas en el mundo físico, a menudo es conveniente ir más allá de los planos de malla y de superficie de la asignación espacial. Cuando la selección de ubicación se realiza con procedimientos, es deseable un nivel más alto de comprensión del entorno. Normalmente, esto requiere tomar decisiones sobre qué es el suelo, el techo y las paredes. Además, la capacidad de optimizar con respecto a un conjunto de restricciones de selección de ubicación para determinar las ubicaciones físicas más deseables de los objetos holográficas.

Durante el desarrollo de conkers y fragmentos jóvenes, Asobo Studios se enfrentó a este problema en el desarrollo de una sala de Solver para este fin. Cada uno de estos juegos tenía necesidades específicas del juego, pero compartimos la tecnología de comprensión espacial básica. La biblioteca HoloToolkit. SpatialUnderstanding encapsula esta tecnología, lo que permite encontrar rápidamente espacios vacíos en las paredes, colocar objetos en el límite superior, identificar colocadas para que el carácter quede sentado y una gran cantidad de consultas espaciales.

Se incluye todo el código fuente, lo que le permite personalizarlo según sus necesidades y compartir sus mejoras con la comunidad. El código de C++ Solver se ha encapsulado en un archivo dll de UWP y expuesto a Unity con una colocación en recurso prefabricado incluida en el MixedRealityToolkit.

### <a name="understanding-modules"></a>Descripción de los módulos

Hay tres interfaces principales que expone el módulo: la topología para las consultas simples de superficie y espacial, la forma de detección de objetos y la colocación de objetos de Solver para la colocación basada en restricciones de los conjuntos de objetos. Cada una de ellas se describe a continuación. Además de las tres interfaces de módulos principales, se puede usar una interfaz de conversión de rayos para recuperar tipos de superficie etiquetada y se puede copiar una malla Playspace estanco personalizada.

### <a name="ray-casting"></a>Conversión de rayos

Una vez que se ha analizado y finalizado el salón, las etiquetas se generan internamente para las superficies como el piso, el techo y las paredes. La función "PlayspaceRaycast" toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y, en caso afirmativo, información sobre esa superficie en forma de "RaycastResult".

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

Internamente, el Raycast se calcula con la representación calculada de 8cm con cubo voxel de Playspace. Cada voxel contiene un conjunto de elementos Surface con datos de topología procesados (también conocido como surfels). Se comparan los surfels contenidos en la celda voxel intersectada y la mejor coincidencia utilizada para buscar la información de la topología. Estos datos de topología contienen la etiqueta devuelta en forma de enumeración "SurfaceTypes", así como el área expuesta de la superficie intersectada.

En el ejemplo de Unity, el cursor convierte un rayo en cada fotograma. En primer lugar, con los colisionadores de Unity. En segundo lugar, en la representación mundial del módulo de comprensión. Y, por último, los elementos de la interfaz de usuario. En esta aplicación, la interfaz de usuario obtiene prioridad, después del resultado de comprensión y, por último, los colisionadores de Unity. El SurfaceType se muestra como texto junto al cursor.

![El tipo de superficie se etiqueta junto al cursor](images/su-raycastresults-300px.jpg)<br>
*El tipo de superficie se etiqueta junto al cursor*

### <a name="topology-queries"></a>Consultas de topología

En el archivo DLL, el administrador de topología controla el etiquetado del entorno. Como se mencionó anteriormente, gran parte de los datos se almacenan en surfels, contenidos en un volumen de voxel. Además, la estructura "PlaySpaceInfos" se usa para almacenar información sobre Playspace, incluida la alineación del mundo (más detalles a continuación), piso y alto del techo. La heurística se usa para determinar el piso, el techo y las paredes. Por ejemplo, la superficie horizontal más grande y más baja con un área de superficie superior a 1 m2 se considera el piso. Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de digitalización también se usa en este proceso.

Un subconjunto de las consultas expuestas por el administrador de topología se expone a través de la dll. Las consultas de topologías expuestas son las siguientes.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Cada una de las consultas tiene un conjunto de parámetros, específico del tipo de consulta. En el ejemplo siguiente, el usuario especifica el alto mínimo & ancho del volumen deseado, el alto mínimo de la ubicación por encima del piso y la cantidad mínima de holgura delante del volumen. Todas las medidas están en metros.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada una de estas consultas toma una matriz preasignada de estructuras "TopologyResult". El parámetro "locationCount" especifica la longitud de la matriz pasada. El valor devuelto informa del número de ubicaciones devueltas. Este número nunca es mayor que el pasado en el parámetro "locationCount".

"TopologyResult" contiene la posición central del volumen devuelto, la dirección orientada (es decir, normal) y las dimensiones del espacio encontrado.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculada a un botón en el panel de interfaz de usuario virtual. En el ejemplo se codifican los parámetros de cada una de estas consultas en valores razonables. Vea SpaceVisualizer.cs en el código de ejemplo para obtener más ejemplos.

### <a name="shape-queries"></a>Consultas de forma

Dentro del archivo dll, el analizador de formas ("ShapeAnalyzer_W") utiliza el analizador de topología para buscar coincidencias con las formas personalizadas definidas por el usuario. En el ejemplo de Unity se define un conjunto de formas y se exponen los resultados a través del menú de consulta en la aplicación, dentro de la pestaña forma. La intención es que el usuario pueda definir sus propias consultas de forma de objeto y hacer uso de ellas, según las necesidades de su aplicación.

Tenga en cuenta que el análisis de formas solo funciona en superficies horizontales. Por ejemplo, un sofá se define mediante la superficie de asiento plana y la parte superior plana del sofá. La consulta de forma busca dos superficies de un tamaño, alto y intervalo de aspecto específicos, con las dos superficies alineadas y conectadas. Con la terminología de las API, el asiento del sofá y la parte superior son componentes de forma y los requisitos de alineación son restricciones de componentes de forma.

A continuación se muestra una consulta de ejemplo definida en el ejemplo de Unity (ShapeDefinition.cs) para objetos "sittable".

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

Cada consulta de forma se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componentes y un conjunto de restricciones de forma que enumeran las dependencias entre los componentes. En este ejemplo se incluyen tres restricciones en una definición de componente único y no hay restricciones de forma entre los componentes (como solo hay un componente).

En cambio, la forma sofá tiene dos componentes de forma y cuatro restricciones de forma. Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Las funciones de contenedor se proporcionan en el módulo Unity para facilitar la creación de definiciones de formas personalizadas. La lista completa de restricciones de componente y forma se puede encontrar en "SpatialUnderstandingDll.cs" dentro de las estructuras "ShapeComponentConstraint" y "ShapeConstraint".

![La forma de rectángulo se encuentra en esta superficie](images/su-shapequery-300px.jpg)<br>
*La forma de rectángulo se encuentra en esta superficie*

### <a name="object-placement-solver"></a>Selección de ubicación de objetos

La selección de ubicación de objetos se puede usar para identificar las ubicaciones ideales en la habitación física para colocar los objetos. El Solver encontrará la ubicación más adecuada en función de las reglas y restricciones del objeto. Además, las consultas de objeto se conservan hasta que el objeto se quita con llamadas "Solver_RemoveObject" o "Solver_RemoveAllObjects", lo que permite la selección de ubicación de varios objetos restringidos. Las consultas de selección de ubicación de objetos constan de tres partes: tipo de ubicación con parámetros, una lista de reglas y una lista de restricciones. Para ejecutar una consulta, use la siguiente API.

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

Esta función toma un nombre de objeto, una definición de ubicación y una lista de reglas y restricciones. Los C# contenedores proporcionan funciones auxiliares de construcción para facilitar la creación de reglas y restricciones. La definición de ubicación contiene el tipo de consulta, es decir, uno de los siguientes.

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

Cada uno de los tipos de ubicación tiene un conjunto de parámetros únicos para el tipo. La estructura "ObjectPlacementDefinition" contiene un conjunto de funciones auxiliares estáticas para crear estas definiciones. Por ejemplo, para encontrar un lugar donde colocar un objeto en el piso, puede usar la función siguiente. public static ObjectPlacementDefinition Create_OnFloor (Vector3 halfDims) además del tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones. No se pueden infringir las reglas. Las ubicaciones de ubicación posibles que satisfacen el tipo y las reglas se optimizan con el conjunto de restricciones para seleccionar la ubicación de colocación óptima. Cada una de las reglas y restricciones se pueden crear mediante las funciones de creación estáticas proporcionadas. A continuación se proporciona una función de ejemplo y una función de construcción de restricciones.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La siguiente consulta de selección de ubicación de objetos busca un lugar donde colocar un cubo de media metro en el borde de una superficie, lejos de otros objetos colocados anteriormente y cerca del centro de la habitación.

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

Si se realiza correctamente, se devuelve una estructura "ObjectPlacementResult" que contiene la posición de colocación, las dimensiones y la orientación. Además, la selección de ubicación se agrega a la lista interna de objetos colocados del archivo dll. Las consultas de selección de ubicación posteriores tendrán en cuenta este objeto. El archivo "LevelSolver.cs" del ejemplo de Unity contiene más consultas de ejemplo.

![Resultados de la colocación del objeto](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: Los cuadros azules de cómo se realiza el resultado de tres consultas en planta con respecto a las reglas de posición de la cámara*

En la resolución de ubicación de varios objetos necesarios para un escenario de nivel o aplicación, primero se resuelven objetos grandes e indispensables con el fin de maximizar la probabilidad de que se pueda encontrar un espacio. El orden de la ubicación es importante. Si no se encuentran colocaciones de objeto, pruebe con menos configuraciones restringidas. Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de salón.

### <a name="room-scanning-process"></a>Proceso de detección de salas

Aunque la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genérica como para satisfacer las necesidades de la gama completa de espacios problemáticos, el módulo de comprensión espacial se creó para admitir las necesidades de dos juegos específicos. Su solución está estructurada en torno a un proceso específico y un conjunto de supuestos, que se resumen a continuación.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Playspace controlada por el usuario "Painting": durante la fase de análisis, el usuario se mueve y se desplaza por el ritmo de las jugadas, con lo que se pintan las áreas que se deben incluir. La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase. Instalación en casa o en el programa de instalación de Office: las funciones de consulta están diseñadas en torno a superficies planas y paredes en los ángulos correctos. Se trata de una limitación flexible. Sin embargo, durante la fase de examen, se completa un análisis de eje principal para optimizar la teselación de malla junto con el eje principal y el secundario. El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis. Llama a las siguientes funciones.

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

El flujo de análisis, controlado por el comportamiento "SpatialUnderstanding" llama a InitScan y, a continuación, UpdateScan cada fotograma. Cuando la consulta de estadísticas notifica una cobertura razonable, se permite al usuario airtap llamar a RequestFinish para indicar el final de la fase de análisis. UpdateScan sigue siendo llamado hasta que su valor devuelto indica que el archivo DLL ha finalizado el procesamiento.

### <a name="understanding-mesh"></a>Descripción de la malla

La dll de comprensión almacena internamente el Playspace como una cuadrícula de cubos voxel de 8cm de tamaño. Durante la parte inicial del análisis, se completa un análisis de componentes principales para determinar los ejes de la habitación. Internamente, almacena su espacio voxel alineado con estos ejes. Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie del volumen voxel. 

![Malla generada generada a partir del volumen voxel](images/su-custommesh.jpg)<br>
*Malla generada generada a partir del volumen voxel*

## <a name="troubleshooting"></a>Solución de problemas
* Asegúrese de que ha establecido la funcionalidad [SpatialPerception](#setting-the-spatialperception-capability)
* Cuando se pierde el seguimiento, el siguiente evento OnSurfaceChanged quitará todas las mallas.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Asignación espacial en el kit de herramientas de realidad mixta
Para obtener más información sobre el uso de la asignación espacial con el kit de herramientas de realidad mixta V2, consulte la <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sección de reconocimiento espacial</a> de los documentos de MRTK.

## <a name="see-also"></a>Vea también
* [MR Spatial 230: asignación espacial](holograms-230.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Sistemas de coordenadas de Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a>
