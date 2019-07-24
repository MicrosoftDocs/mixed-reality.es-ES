---
title: 'Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens'
description: Al crear las primeras aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto se podían introducir los límites de la asignación espacial en el dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, asignación espacial
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522710"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens

Al crear las primeras aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto se podían introducir los límites de la asignación espacial en el dispositivo. Jeff Evertt, Ingeniero de software en Microsoft Studios, explica cómo se desarrolló una nueva tecnología fuera de la necesidad de tener más control sobre cómo se colocan los hologramas en el entorno real de un usuario.

## <a name="watch-the-video"></a>Ver el vídeo

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Más allá de la asignación espacial

Mientras estábamos trabajando en [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8) y [conkers jóvenes](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dos de los primeros juegos de HoloLens, encontramos que cuando estábamos realizando la selección de ubicación de los hologramas en el mundo físico, necesitábamos un nivel más alto de comprensión sobre el entorno. Cada juego tenía sus propias necesidades específicas de selección de Ubicación: Por ejemplo, en los fragmentos queríamos poder distinguir entre diferentes superficies (como el piso o una tabla) para colocar pistas en las ubicaciones correspondientes. También queríamos poder identificar las superficies en las que podrían sentarse los caracteres holográficas de tamaño real, como un sofá o una silla. En jóvenes Conker, queríamos que Conker y sus oponentes pudieran usar superficies levantadas en el salón de un jugador como plataformas.

[Asobo Studios](http://www.asobostudio.com/index.html), nuestro asociado de desarrollo para estos juegos, se enfrentó a este problema y creaba una tecnología que amplía las capacidades de asignación espacial de HoloLens. Con esto, podríamos analizar la habitación de un jugador e identificar superficies como paredes, mesas, sillas y suelos. También nos permitió optimizar con respecto a un conjunto de restricciones para determinar la mejor ubicación de los objetos holográficas.

## <a name="the-spatial-understanding-code"></a>Código espacial de comprensión

Hemos tomado el código original de Asobo y hemos creado una biblioteca que encapsula esta tecnología. Microsoft y Asobo ahora tienen código abierto y lo ponen a disposición de [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para que pueda usarlos en sus propios proyectos. Se incluye todo el código fuente, lo que le permite personalizarlo según sus necesidades y compartir sus mejoras con la comunidad. El código de C++ Solver se ha encapsulado en un archivo dll de UWP y expuesto a Unity con un [recurso prefabricado de colocación incluido en MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

En el ejemplo de Unity se incluyen muchas consultas útiles que le permitirán buscar espacios vacíos en las paredes, colocar objetos en el límite superior o en espacios grandes en el suelo, identificar los lugares en los que se colocan los caracteres y una gran cantidad de consultas espaciales.

Aunque la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genérica como para satisfacer las necesidades de la gama completa de espacios problemáticos, el módulo de comprensión espacial se creó para admitir las necesidades de dos juegos específicos. Como tal, su solución está estructurada en torno a un proceso específico y un conjunto de suposiciones:
* **Playspace de tamaño fijo**: El usuario especifica el tamaño máximo de Playspace en la llamada init.
* **Proceso de examen único**: El proceso requiere una fase de detección discreta en la que el usuario se desplazará, definiendo el Playspace. Las funciones de consulta no funcionarán hasta que se haya finalizado el examen.
* **Playspace controlado por el usuario "Painting"** : Durante la fase de examen, el usuario se mueve y busca en torno a Playspace, con lo que se pintan de forma eficaz las áreas que se deben incluir. La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.
* **Instalación en casa o en Office**: Las funciones de consulta están diseñadas en torno a superficies planas y paredes en los ángulos rectos. Se trata de una limitación flexible. Sin embargo, durante la fase de examen, se completa un análisis de eje principal para optimizar la teselación de malla junto con el eje principal y el secundario.

### <a name="room-scanning-process"></a>Proceso de detección de salas

Al cargar el módulo de comprensión espacial, lo primero que hará es examinar el espacio, de modo que todas las superficies que se pueden usar (por ejemplo, el piso, el techo y las paredes) se identifican y se etiquetan. Durante el proceso de digitalización, mire el salón y "pinte" las áreas que deben incluirse en el análisis.

La malla que se ha detectado durante esta fase es una parte importante de los comentarios visuales que permite a los usuarios saber qué partes del salón se están analizando. El archivo DLL del módulo espacial Understanding almacena internamente Playspace como una cuadrícula de cubos voxel de 8cm de tamaño. Durante la parte inicial del análisis, se completa un análisis de componentes principales para determinar los ejes de la habitación. Internamente, almacena su espacio voxel alineado con estos ejes. Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie del volumen voxel.

![Malla espacial de asignación en blanco y descripción de la malla Playspace en verde](images/spatial-mapping-500px.png)

Malla espacial de asignación en blanco y descripción de la malla Playspace en verde



El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis. Llama a las siguientes funciones:
* **SpatialUnderstanding_Init**: Se llama una vez al inicio.
* **GeneratePlayspace_InitScan**: Indica que debe comenzar la fase de análisis.
* **GeneratePlayspace_UpdateScan_DynamicScan**: Se llama cada fotograma para actualizar el proceso de examen. La posición y orientación de la cámara se pasa y se usa para el proceso de dibujo de Playspace, descrito anteriormente.
* **GeneratePlayspace_RequestFinish**: Se llama para finalizar Playspace. Se usarán las áreas "pintadas" durante la fase de análisis para definir y bloquear el Playspace. La aplicación puede consultar las estadísticas durante la fase de análisis, así como consultar la malla personalizada para proporcionar los comentarios de los usuarios.
* **Import_UnderstandingMesh**: Durante el examen, el comportamiento de **SpatialUnderstandingCustomMesh** proporcionado por el módulo y colocado en la descripción de recurso prefabricado periódicamente consultará la malla personalizada generada por el proceso. Además, esto se realiza una vez más después de haber finalizado el examen.

El flujo de análisis, controlado por el comportamiento de **SpatialUnderstanding** llama a **InitScan**y **UpdateScan** cada fotograma. Cuando la consulta de estadísticas notifica una cobertura razonable, el usuario puede airtap para llamar a **RequestFinish** para indicar el final de la fase de análisis. **UpdateScan** sigue siendo llamado hasta que su valor devuelto indica que el archivo DLL ha finalizado el procesamiento.

## <a name="the-queries"></a>Las consultas

Una vez completado el análisis, podrá tener acceso a tres tipos diferentes de consultas en la interfaz:
* **Consultas de topología**: Se trata de consultas rápidas basadas en la topología de la sala digitalizada.
* **Consultas de forma**: Estos usan los resultados de las consultas de topología para buscar superficies horizontales que sean una buena coincidencia con las formas personalizadas que defina.
* **Consultas de selección de ubicación de objetos**: Se trata de consultas más complejas que buscan la ubicación con ajuste perfecto en función de un conjunto de reglas y restricciones para el objeto.

Además de las tres consultas principales, hay una interfaz raycasting que se puede usar para recuperar tipos de superficie etiquetada y se puede copiar una malla de sala de estancos personalizada.

### <a name="topology-queries"></a>Consultas de topología

En el archivo DLL, el administrador de topología controla el etiquetado del entorno. Como se mencionó anteriormente, gran parte de los datos se almacenan en surfels, que están incluidos en un volumen de voxel. Además, la estructura **PlaySpaceInfos** se usa para almacenar información sobre Playspace, incluida la alineación del mundo (más detalles a continuación), Floor y height.

La heurística se usa para determinar el piso, el techo y las paredes. Por ejemplo, la superficie horizontal más grande y más baja con un área de superficie superior a 1 m2 se considera el piso. Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de digitalización también se usa en este proceso.

Un subconjunto de las consultas expuestas por el administrador de topología se expone a través de la DLL. Las consultas de topologías expuestas son las siguientes:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Cada una de las consultas tiene un conjunto de parámetros, específico del tipo de consulta. En el ejemplo siguiente, el usuario especifica el alto mínimo & ancho del volumen deseado, el alto mínimo de la ubicación por encima del piso y la cantidad mínima de holgura delante del volumen. Todas las medidas están en metros.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada una de estas consultas toma una matriz preasignada de estructuras **TopologyResult** . El parámetro **locationCount** especifica la longitud de la matriz pasada. El valor devuelto informa del número de ubicaciones devueltas. Este número nunca es mayor que el parámetro **locationCount** pasado.

**TopologyResult** contiene la posición central del volumen devuelto, la dirección orientada (es decir, normal) y las dimensiones del espacio encontrado.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculada a un botón en el panel de interfaz de usuario virtual. En el ejemplo se codifican los parámetros de cada una de estas consultas en valores razonables. Vea *SpaceVisualizer.CS* en el código de ejemplo para obtener más ejemplos.

### <a name="shape-queries"></a>Consultas de forma

Dentro de la DLL, el analizador de formas (**ShapeAnalyzer_W**) utiliza el analizador de topología para buscar coincidencias con las formas personalizadas definidas por el usuario. El ejemplo de Unity tiene un conjunto predefinido de formas que se muestran en el menú consulta, en la pestaña forma.

Tenga en cuenta que el análisis de formas solo funciona en superficies horizontales. Por ejemplo, un sofá se define mediante la superficie de asiento plana y la parte superior plana del sofá. La consulta de forma busca dos superficies de un tamaño, alto y intervalo de aspecto específicos, con las dos superficies alineadas y conectadas. Con la terminología de las API, el asiento del sofá y la parte superior del sofá son componentes de forma y los requisitos de alineación son restricciones de componentes de forma.

A continuación se muestra una consulta de ejemplo definida en el ejemplo de Unity (**ShapeDefinition.CS**) para objetos "sittable":




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Cada consulta de forma se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componentes y un conjunto de restricciones de forma que enumera las dependencias entre los componentes. En este ejemplo se incluyen tres restricciones en una definición de componente único y no hay restricciones de forma entre los componentes (como solo hay un componente).

En cambio, la forma sofá tiene dos componentes de forma y cuatro restricciones de forma. Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Las funciones de contenedor se proporcionan en el módulo Unity para facilitar la creación de definiciones de formas personalizadas. La lista completa de restricciones de componente y forma se puede encontrar en **SpatialUnderstandingDll.CS** dentro de las estructuras **ShapeComponentConstraint** y **ShapeConstraint** .

![El rectángulo azul resalta los resultados de la consulta de forma de silla.](images/chair-shape-query-500px.png)

El rectángulo azul resalta los resultados de la consulta de forma de silla.



### <a name="object-placement-solver"></a>Selección de ubicación de objetos

Las consultas de selección de ubicación de objetos se pueden usar para identificar las ubicaciones ideales en la habitación física para colocar los objetos. El Solver encontrará la ubicación con ajuste perfecto en función de las reglas y restricciones del objeto. Además, las consultas de objeto se conservan hasta que el objeto se quita con llamadas a **Solver_RemoveObject** o **Solver_RemoveAllObjects** , lo que permite la selección de ubicación de varios objetos restringidos.

Las consultas de selección de ubicación de objetos constan de tres partes: tipo de selección de ubicación con parámetros, una lista de reglas y una lista de restricciones. Para ejecutar una consulta, use la siguiente API:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Esta función toma un nombre de objeto, una definición de ubicación y una lista de reglas y restricciones. Los C# contenedores proporcionan funciones auxiliares de construcción para facilitar la creación de reglas y restricciones. La definición de ubicación contiene el tipo de consulta, es decir, uno de los siguientes:




```
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

Cada uno de los tipos de ubicación tiene un conjunto de parámetros únicos para el tipo. La estructura **ObjectPlacementDefinition** contiene un conjunto de funciones auxiliares estáticas para crear estas definiciones. Por ejemplo, para encontrar un lugar donde colocar un objeto en el piso, puede usar la función siguiente: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Además del tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones. No se pueden infringir las reglas. Las ubicaciones de ubicación posibles que satisfacen el tipo y las reglas se optimizan con el conjunto de restricciones para seleccionar la ubicación de colocación óptima. Cada una de las reglas y restricciones se pueden crear mediante las funciones de creación estáticas proporcionadas. A continuación se proporciona una función de ejemplo y una función de construcción de restricciones.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

En la consulta de selección de ubicación de objetos siguiente se busca un lugar donde colocar un cubo de media metro en el borde de una superficie, lejos de otros objetos colocados anteriormente y cerca del centro de la habitación.




```
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

Si se realiza correctamente, se devuelve una estructura **ObjectPlacementResult** que contiene la posición de colocación, las dimensiones y la orientación. Además, la selección de ubicación se agrega a la lista interna de objetos colocados del archivo DLL. Las consultas de selección de ubicación posteriores tendrán en cuenta este objeto. El archivo **LevelSolver.CS** en el ejemplo de Unity contiene más consultas de ejemplo.

![Los cuadros azules muestran el resultado de las consultas de tres lugares en el suelo con las reglas "fuera de la posición de la cámara".](images/away-from-camera-position-500px.png)

Los cuadros azules muestran el resultado de las consultas de tres lugares en el suelo con las reglas "fuera de la posición de la cámara".


**Útiles**
* En la resolución de ubicación de varios objetos necesarios para un escenario de nivel o aplicación, primero se resuelven los objetos disposibles y grandes para maximizar la probabilidad de que se pueda encontrar un espacio.
* El orden de la ubicación es importante. Si no se encuentran colocaciones de objeto, pruebe con menos configuraciones restringidas. Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de salón.

### <a name="ray-casting"></a>Conversión de rayos

Además de las tres consultas principales, se puede usar una interfaz de conversión de rayos para recuperar tipos de superficie etiquetada y se puede copiar una malla de Playspace estanco personalizada después de que se haya analizado y finalizado el salón; las etiquetas se generan internamente para superficies como la piso, techo y paredes. La función **PlayspaceRaycast** toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y, en caso afirmativo, información sobre esa superficie en forma de **RaycastResult**. 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Internamente, el Raycast se calcula con la representación calculada de 8cm con cubo voxel de Playspace. Cada voxel contiene un conjunto de elementos Surface con datos de topología procesados (también conocidos como surfels). Se comparan los surfels contenidos en la celda voxel intersectada y la mejor coincidencia utilizada para buscar la información de la topología. Estos datos de topología contienen la etiqueta devuelta en el formulario de la enumeración **SurfaceTypes** , así como el área expuesta de la superficie intersectada.

En el ejemplo de Unity, el cursor convierte un rayo en cada fotograma. En primer lugar, con los colisionadores de Unity; en segundo lugar, en la representación mundial del módulo de comprensión; y, por último, con los elementos de la interfaz de usuario. En esta aplicación, la interfaz de usuario obtiene prioridad, después el resultado de comprensión y, por último, los colisionadores de Unity. El **SurfaceType** se muestra como texto junto al cursor.

![Raycast resultado de la intersección de informes con el piso.](images/raycast-result-500px.jpg)

Raycast resultado de la intersección de informes con el piso.


## <a name="get-the-code"></a>Obtener el código

El código de código abierto está disponible en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity). Háganoslo saber en los [foros para desarrolladores de HoloLens](https://forums.hololens.com/) si usa el código en un proyecto. No podemos esperar para ver lo que hace con él.

## <a name="about-the-author"></a>Acerca del autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> es un responsable de ingeniería de software que ha trabajado en HoloLens desde los primeros días, desde la incubación hasta la experiencia de desarrollo. Antes de HoloLens, trabajó en el Kinect de Xbox y en el sector de juegos en una amplia variedad de plataformas y juegos. Juan es apasionante de robóticas, gráficos y cosas con luces Flash que emiten sonido. Disfruta aprendiendo nuevas cosas y trabajando en software, hardware y, en especial, en el espacio en el que se intersecan dos.</td>
</tr>
</table>



## <a name="see-also"></a>Vea también
* [Asignación espacial](spatial-mapping.md)
* [Diseño de asignaciones espaciales](spatial-mapping-design.md)
* [Visualización de la exploración de la sala](room-scan-visualization.md)
* [MixedRealityToolkit: Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lecciones de la vanguardia del desarrollo de HoloLens](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
