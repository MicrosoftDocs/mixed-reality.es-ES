---
title: 'Caso práctico: expandir las capacidades de asignación espacial de HoloLens'
description: Al crear nuestra primera aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto simplemente podríamos sobrepasamos los límites de asignación espacial en el dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Asignación espacial Windows Mixed Reality, HoloLens,
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602837"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Caso práctico: expandir las capacidades de asignación espacial de HoloLens

Al crear nuestra primera aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto simplemente podríamos sobrepasamos los límites de asignación espacial en el dispositivo. Jeff Evertt, un ingeniero de software de Microsoft Studios, se explica cómo se desarrolló una nueva tecnología de fuera de la necesidad de tener más control sobre cómo hologramas se colocan en el entorno de un usuario real.

## <a name="watch-the-video"></a>Vea el vídeo

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Más allá de la asignación espacial

Mientras que estábamos trabajando [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8) y [Conker Young](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dos de los juegos de la primera para HoloLens, descubrimos que cuando se estaba realizando la colocación de procedimientos de hologramas en el mundo físico, es necesario un nivel más alto de conocimiento sobre el entorno del usuario. Cada juego tenía sus propias necesidades específicas de la selección de ubicación: En fragmentos, por ejemplo, deseamos poder distinguir entre diferentes tipos de superficies, como el límite inferior o una tabla, colocar pistas en ubicaciones importantes. También deseamos ser capaz de identificar las superficies que podrían se colocan caracteres holográficas tamaño real, por ejemplo, un sofá o una silla. Conker Young, quisimos Conker y sus oponentes para que pueda usar superficies se genera en la sala de un jugador que las plataformas.

[Estudios Asobo](http://www.asobostudio.com/index.html), nuestro socio de desarrollo de estos juegos, que se enfrentan este problema toro por las astas y creó una tecnología que amplía las capacidades de asignación espacial de HoloLens. Con esto, podríamos analizar sala de un jugador y superficies como paredes, tablas, sillas y plantas de identificar. También nos da la capacidad de optimizar con un conjunto de restricciones para determinar la mejor ubicación para los objetos holográficas.

## <a name="the-spatial-understanding-code"></a>El código de comprensión espacial

Se tardó el código original de Asobo y había creado una biblioteca que encapsula esta tecnología. Microsoft y Asobo tiene ahora este código abierto y disponible en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para su uso en sus propios proyectos. Todo el código fuente se incluye, por lo que permite personalizar según sus necesidades y compartir sus mejoras con la Comunidad. El código para el C++ solver se ha ajustado en una DLL de UWP y expuestos a Unity con una [prefabricado de orden dentro de MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

Hay muchas consultas útiles incluidas en el ejemplo de Unity que le permitirá encontrar espacios vacíos en las paredes, colocar objetos en el límite superior o en espacios de gran tamaño en el suelo, identificar los lugares de caracteres que se encuentran y un sinnúmero de otras consultas espaciales descripción.

Mientras la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genéricos como para satisfacer las necesidades de toda la gama de espacios del problema, el módulo de comprensión espaciales se generó para admitir las necesidades de dos juegos específicos. Por lo tanto, su solución está estructurada en torno a un proceso específico y un conjunto de supuestos:
* **Se ha corregido tamaño playspace**: El usuario especifica el tamaño máximo playspace en la llamada de init.
* **Proceso de examen único**: El proceso requiere un discretos fase donde el usuario le guía en torno al análisis, definir el playspace. Funciones de consulta no funcionará hasta que una vez se ha finalizado el examen.
* **Usuario controlado por playspace "pintar"**: Durante la fase de análisis, el usuario se mueve y mira alrededor del playspace, pintar las áreas que deben incluirse de forma eficaz. La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.
* **En el interior el programa de instalación de casa u oficina**: Las funciones de consulta están diseñadas en torno a las superficies planas y paredes ángulos rectos. Esta es una limitación temporal. Sin embargo, durante la fase de análisis, se completa un análisis del eje principal para optimizar la teselación de malla a lo largo del eje principal y secundaria.

### <a name="room-scanning-process"></a>Proceso de exploración de sala

Al cargar el módulo de comprensión espacial, lo primero que haré es examinar el espacio, por lo que todas las superficies utilizables, como paredes, ceiling y floor, se identifican y con la etiqueta. Durante el proceso de digitalización, echa un vistazo alrededor de la sala y "paint" las áreas que deben incluirse en el examen.

La malla vista durante esta fase es una parte importante de los comentarios visuales que permiten a los usuarios saber qué partes de la sala se están analizando. El archivo DLL para el módulo espacial descripción almacena internamente el playspace como una cuadrícula de 8cm tamaño voxel cubos. Durante la parte inicial del análisis, se completa un análisis del componente principal para determinar los ejes de la sala. Internamente, almacena su espacio voxel alineado para estos ejes. Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie desde el volumen voxel.

![Espacial de asignación de malla en blanco y entender playspace de malla en verde](images/spatial-mapping-500px.png)

Espacial de asignación de malla en blanco y entender playspace de malla en verde



El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis. Llama a las funciones siguientes:
* **SpatialUnderstanding_Init**: Se llama una vez al principio.
* **GeneratePlayspace_InitScan**: Indica que debería comenzar la fase de análisis.
* **GeneratePlayspace_UpdateScan_DynamicScan**: Llama a cada fotograma para actualizar el proceso de detección. La posición de la cámara y la orientación se pasa y se usa para el proceso de dibujo playspace, se ha descrito anteriormente.
* **GeneratePlayspace_RequestFinish**: Se llama para finalizar la playspace. Se usarán las áreas que "pintadas" durante la fase de análisis para definir y bloquear el playspace. La aplicación puede consultar las estadísticas durante el análisis fase, así como consultar la malla personalizada para proporcionar comentarios del usuario.
* **Import_UnderstandingMesh**: Durante la detección, la **SpatialUnderstandingCustomMesh** comportamiento proporcionado por el módulo y se coloca en el prefabricado verá descripción consultará periódicamente la malla personalizada generada por el proceso. Además, esto se hace una vez más después de que se ha finalizado el análisis.

El flujo de análisis, controlado por la **SpatialUnderstanding** comportamiento llamadas **InitScan**, a continuación, **UpdateScan** cada fotograma. Cuando informa de la consulta de estadísticas de cobertura razonable, el usuario puede airtap para llamar a **RequestFinish** para indicar el final de la fase de análisis. **UpdateScan** continúa llamada hasta que devueltos es el valor indica que el archivo DLL ha completado el procesamiento.

## <a name="the-queries"></a>Las consultas

Una vez completado el análisis, podrá tener acceso a tres tipos diferentes de las consultas en la interfaz:
* **Las consultas de topología**: Estas son las consultas que se basan en la topología de la sala digitalizada.
* **Las consultas de forma**: Estos usan los resultados de las consultas de topología para buscar las superficies horizontales que son una coincidencia acertada a formas personalizadas que defina.
* **Consultas de selección de ubicación de objeto**: Estas son las consultas más complejas que buscar la ubicación de ajuste perfecto basándose en un conjunto de reglas y restricciones para el objeto.

Además de las tres consultas principales, hay una interfaz de detalles que se puede utilizar para recuperar tipos de superficie etiquetados y se puede copiar una malla de sala estanca personalizado.

### <a name="topology-queries"></a>Consultas de topología

En el archivo DLL, el Administrador de la topología controla etiquetado del entorno. Como se mencionó anteriormente, gran parte de los datos se almacena en surfels, que están dentro de un volumen voxel. Además, el **PlaySpaceInfos** estructura se usa para almacenar información sobre la playspace, incluida la alineación del mundo (más detalles en este tema), floor y ceiling de alto.

Se utiliza la heurística para determinar las paredes, ceiling y floor. Por ejemplo, la superficie más grande y más baja horizontal con más de 1 área expuesta de m2 se considera el suelo. Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de análisis también se usa en este proceso.

Un subconjunto de consultas expuestas por el Administrador de topología se exponen fuera a través de la DLL. Las consultas de topología expuestas son las siguientes:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Cada una de las consultas tiene un conjunto de parámetros, el tipo de consulta específicos. En el ejemplo siguiente, el usuario especifica el alto mínimo anc & ho del volumen deseado, el alto mínimo de la selección de ubicación por encima el suelo y la cantidad mínima de limpieza delante el volumen. Todas las medidas son en metros.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Cada una de estas consultas toma una matriz asignada previamente de **TopologyResult** estructuras. El **locationCount** parámetro especifica la longitud de la matriz pasada. El valor devuelto indica el número de ubicaciones devueltas. Este número nunca es mayor que en el pasado **locationCount** parámetro.

El **TopologyResult** contiene la posición central de las dimensiones del espacio se encuentra, la dirección opuesta (es decir, normal) y el volumen devuelto.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculado a un botón en el panel de interfaz de usuario virtual. El disco duro de ejemplo códigos de los parámetros para cada una de estas consultas para valores razonables. Consulte *SpaceVisualizer.cs* en el código de ejemplo para obtener más ejemplos.

### <a name="shape-queries"></a>Consultas de forma

Dentro de la DLL, el analizador de forma (**ShapeAnalyzer_W**) usa el analizador de topología para coincidir con las formas personalizadas definidas por el usuario. El ejemplo de Unity tiene un conjunto predefinido de formas que se muestran en el menú de la consulta, en la pestaña de la forma.

Tenga en cuenta que el análisis de forma funciona en las superficies horizontales. Por ejemplo, un sofá, se define por la superficie del asiento sin formato y la parte superior plana de vuelta el sofá. La consulta shape busca dos superficies de un intervalo de tamaño, el alto y el aspecto específico, con las dos superficies alineado y conectado. Con la terminología de API, el asiento del sofá y la parte superior de la parte posterior del sofá son dar forma a los componentes y la alineación de los requisitos son las restricciones de componentes de forma.

Una consulta de ejemplo que se define en el ejemplo de Unity (**ShapeDefinition.cs**), para objetos "sittable" es el siguiente:




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

Cada consulta shape se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componente y un conjunto de restricciones de forma que se enumera las dependencias entre los componentes. En este ejemplo incluye tres restricciones en una definición de componente único y sin restricciones de forma entre los componentes (como hay solo un componente).

En cambio, la forma del sofá tiene dos componentes de la forma y cuatro de las restricciones de forma. Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Se proporcionan funciones de contenedor en el módulo de Unity para la creación fácil de definiciones de forma personalizada. Encontrará la lista completa de las restricciones de componente y la forma en **SpatialUnderstandingDll.cs** dentro de la **ShapeComponentConstraint** y **ShapeConstraint** estructuras.

![El rectángulo azul resalta los resultados de la consulta shape silla.](images/chair-shape-query-500px.png)

El rectángulo azul resalta los resultados de la consulta shape silla.



### <a name="object-placement-solver"></a>Solucionador de selección de ubicación del objeto

Las consultas de selección de ubicación del objeto pueden utilizarse para identificar las ubicaciones ideales en la sala física para colocar los objetos. El solucionador encontrará la ubicación de ajuste perfecto dada las restricciones y reglas de objetos. Además, las consultas de objeto conservan hasta que se quita el objeto con **Solver_RemoveObject** o **Solver_RemoveAllObjects** llamadas, lo que permite restringida la colocación de varios objetos.

Las consultas de selección de ubicación del objeto constan de tres partes: un tipo de colocación con parámetros, una lista de reglas y una lista de restricciones. Para ejecutar una consulta, use la siguiente API:




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
Esta función toma un nombre de objeto, definición de la selección de ubicación y una lista de reglas y restricciones. El C# contenedores proporciona funciones auxiliares para facilitar la construcción de la regla y la restricción de construcción. La definición de la selección de ubicación contiene el tipo de consulta, es decir, uno de los siguientes:




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

Cada uno de los tipos de posición tiene un conjunto de parámetros únicos para el tipo. El **ObjectPlacementDefinition** estructura contiene un conjunto de funciones auxiliares estáticos para crear estas definiciones. Por ejemplo, para encontrar un lugar para colocar un objeto en el suelo, puede usar la función siguiente: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Además del tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones. No se puede infringir las reglas. Ubicaciones de posible selección de ubicación que cumplen el tipo y las reglas están optimizadas, a continuación, en el conjunto de restricciones para seleccionar la ubicación de la ubicación óptima. Cada una de las reglas y restricciones se puede crear las funciones de creación estático proporcionado. A continuación, se proporciona una función de construcción de restricción y regla de ejemplo.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La siguiente consulta de selección de ubicación de objeto está buscando un lugar para colocar un cubo de la mitad del medidor en el borde de una superficie, fuera otro previamente colocar objetos y cerca del centro de la sala.




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

Si es correcto, un **ObjectPlacementResult** se devuelve la estructura que contiene la posición de colocación, dimensiones y la orientación. Además, la selección de ubicación se agrega a la lista interna de la DLL de objetos colocados. Las consultas posteriores de la selección de ubicación tendrá este objeto en la cuenta. El **LevelSolver.cs** archivo en el ejemplo de Unity contiene más de las consultas de ejemplo.

![Los cuadros azules muestran el resultado de tres consultas del lugar en el piso con reglas de "fuera de la posición de la cámara".](images/away-from-camera-position-500px.png)

Los cuadros azules muestran el resultado de tres consultas del lugar en el piso con reglas de "fuera de la posición de la cámara".


**Sugerencias:**
* Al resolver para la ubicación de colocación de varios objetos necesarios para un escenario de aplicación o nivel, solucione primero objetos grandes e indispensables para maximizar la probabilidad de que se puede encontrar un espacio.
* Es importante el orden de selección de ubicación. Si no se puede encontrar las selecciones de ubicación del objeto, intente configuraciones menos restringidas. Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de espacio.

### <a name="ray-casting"></a>Ray conversión

Además de las tres consultas principales, una interfaz de la conversión de ray puede usarse para recuperar tipos de superficie etiquetados y se puede copiar una malla playspace estanca personalizado espera después de haber analizado y finaliza, la sala de etiquetas se hayan generado internamente para superficies como el Floor, ceiling y paredes. El **PlayspaceRaycast** función toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y si es así, obtener información acerca de la que se muestran en forma de un **RaycastResult**. 


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

Internamente, el raycast es calculado con respecto a la representación de voxel calculada 8cm al cubo de la playspace. Cada voxel contiene un conjunto de elementos de superficie con datos de la topología procesados (también conocido como surfels). Se comparan los surfels dentro de la celda voxel intersectado y la mejor coincidencia utilizada para buscar la información de topología. Estos datos de la topología contienen el etiquetado que se devuelve en forma de la **SurfaceTypes** enum, así como el área expuesta de la superficie de intersección.

En el ejemplo de Unity, el cursor convierte un rayo cada fotograma. En primer lugar, con colisionadores de Unity; en segundo lugar, con representación de mundo del módulo descripción; y por último, frente a los elementos de interfaz de usuario. En esta aplicación, la interfaz de usuario obtiene la prioridad, a continuación, el resultado de la descripción y por último, colisionadores de Unity. El **SurfaceType** se notifica como texto situado junto al cursor.

![Resultado de Raycast reporting intersección con el límite inferior.](images/raycast-result-500px.jpg)

Resultado de Raycast reporting intersección con el límite inferior.


## <a name="get-the-code"></a>Obtener el código

El código abierto y está disponible en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity). Háganoslo saber en el [foros para desarrolladores de HoloLens](https://forums.hololens.com/) si usa el código en un proyecto. Estamos ansiosos por ver qué hace con él.

## <a name="about-the-author"></a>Acerca del autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> es director de ingeniería de software que ha trabajado en HoloLens desde los primeros días de incubación a la experiencia de desarrollo. Antes de HoloLens, trabajó en el Xbox Kinect y en el sector de juegos en una amplia variedad de plataformas y juegos. Juan es un apasionado de las cosas con luces parpadeantes que vaya Bip, gráficos y robótica. Le encanta aprender cosas nuevas y trabajar en software, hardware y especialmente en el espacio de intersección de los dos.</td>
</tr>
</table>



## <a name="see-also"></a>Vea también
* [Asignación espacial](spatial-mapping.md)
* [Diseño de la asignación espacial](spatial-mapping-design.md)
* [Visualización de análisis de sala](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lecciones desde la primera línea de desarrollo de HoloLens](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
