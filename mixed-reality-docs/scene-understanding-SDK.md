---
title: SDK de introducción a la escena
description: Guía de programación para el SDK de descripción de la escena
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensión de escenas, asignación espacial, Windows Mixed Reality, Unity
ms.openlocfilehash: f293e779b041cdf4aa636cf317b7eaca70e16410
ms.sourcegitcommit: 37816514b8fe20669c487774b86e80ec08edcadf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "81003331"
---
# <a name="scene-understanding-sdk-overview"></a>Información general del SDK de introducción a la escena

El objetivo de la comprensión de la escena es transformar los datos del sensor de entorno no estructurado que captura el dispositivo de realidad mixta y convertirlos en una representación eficaz pero abstracta que es intuitiva y fácil de desarrollar para. El SDK actúa como la capa de comunicación entre la aplicación y la escena que comprende el tiempo de ejecución. Está diseñado para imitar construcciones estándar existentes como gráficos de escenas 3D para representaciones 3D y rectángulos 2D y paneles para aplicaciones 2D. Aunque las construcciones que comprenden los imitadores se asignarán a marcos concretos que se pueden usar, en general SceneUnderstanding es independiente del marco de trabajo, lo que permite la interoperabilidad entre marcos variados que interactúan con él. A medida que la comprensión de la escena evolucione el rol del SDK, se asegurará de que las nuevas representaciones y capacidades sigan expuestas dentro de un marco unificado. En este documento, en primer lugar, introduciremos conceptos de alto nivel que le ayudarán a familiarizarse con el uso o el entorno de desarrollo y, a continuación, proporcionar documentación más detallada sobre clases y construcciones específicas.

## <a name="where-do-i-get-the-sdk"></a>¿Dónde obtengo el SDK?

El SDK de SceneUnderstanding se descarga a través de NuGet.

[SDK de SceneUnderstanding](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

**Nota:** la versión más reciente depende de los paquetes de versión preliminar y tendrá que habilitar los paquetes de versión preliminar para verlos.

A partir de la versión 0.5.2022-RC, la descripción de la escena C# admite C++ proyecciones de idioma para y permite a las aplicaciones desarrollar aplicaciones para las plataformas Win32 o UWP. A partir de esta versión, SceneUnderstanding es compatible con la compatibilidad del editor de Unity con el SceneObserver, que se usa únicamente para comunicarse con HoloLens2. 

SceneUnderstanding requiere Windows SDK versión 18362 o posterior. 

Si usa el SDK en un proyecto de Unity, use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity) para instalar el paquete en el proyecto.

## <a name="conceptual-overview"></a>Información conceptual

### <a name="the-scene"></a>La escena

El dispositivo de realidad mixta integra constantemente información sobre lo que ve en su entorno. La comprensión de la escena canaliza todos estos orígenes de datos y genera una sola abstracción unida. La comprensión de escenas genera escenas que son una composición de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representan una instancia de un solo elemento (por ejemplo, un muro/techo/piso). Los propios objetos de la escena son una composición de [SceneComponents](scene-understanding-SDK.md#scenecomponents) que representan partes más granulares que componen este SceneObject. Algunos ejemplos de componentes son cuatro y mallas, pero en el futuro podrían representar cuadros de límite, mallas de colisión, metadatos, etc.

El proceso de conversión de los datos del sensor sin procesar en una escena es una operación potencialmente costosa que podría tardar unos segundos en espacios medios (~ 10x10m) hasta minutos para espacios muy grandes (~ 50x50m) y, por lo tanto, no es algo que el dispositivo está calculando sin solicitud de aplicación. En su lugar, la generación de escenas la desencadena la aplicación a petición. La clase SceneObserver tiene métodos estáticos que pueden calcular o deserializar una escena, que puede enumerar o interactuar con. La acción de "proceso" se ejecuta a petición y se ejecuta en la CPU, pero en un proceso independiente (el controlador de realidad mixta). Sin embargo, mientras se realiza el proceso en otro proceso, los datos de la escena resultantes se almacenan y mantienen en la aplicación en el objeto de la escena. 

A continuación se muestra un diagrama que ilustra este flujo de proceso y muestra ejemplos de dos aplicaciones que interconectan con el entorno de tiempo de ejecución de la escena. 

![Diagrama del proceso](images/SU-ProcessFlow.png)

En el lado izquierdo hay un diagrama del tiempo de ejecución de realidad mixta que siempre está activado y en ejecución en su propio proceso. Este tiempo de ejecución es responsable de realizar el seguimiento de los dispositivos, la asignación espacial y otras operaciones que la comprensión de la escena usa para entender y explicar el mundo. En el lado derecho del diagrama, se muestran dos aplicaciones teóricas que hacen uso de la comprensión de la escena. La primera interfaz de la aplicación con MRTK, que usa el SDK de información de escenas internamente, la segunda aplicación calcula y usa dos instancias de escena independientes. Las 3 escenas de este diagrama generan instancias distintas de las escenas, el controlador no realiza un seguimiento del estado global que se comparte entre las aplicaciones y los objetos de escena de una escena no se encuentran en otro. La comprensión de la escena proporciona un mecanismo para realizar el seguimiento con el tiempo, pero esto se hace con el SDK y el código que realiza este seguimiento se ejecuta en el SDK del proceso de la aplicación.

Dado que cada escena almacena sus datos en el espacio de memoria de la aplicación, puede suponer que todas las funciones del objeto de escena o de sus datos internos siempre se ejecutan en el proceso de la aplicación.

### <a name="layout"></a>Diseño

Para trabajar con la comprensión de la escena, puede ser útil conocer y entender cómo representa los componentes el tiempo de ejecución de forma lógica y física. La escena representa los datos con un diseño específico que se eligió para ser sencillo al tiempo que se mantiene una estructura subyacente que se pliable para satisfacer los requisitos futuros sin necesidad de revisiones importantes. Para ello, la escena almacena todos los componentes (bloques de creación de todos los objetos de escena) en una lista plana y define la jerarquía y la composición a través de referencias en las que determinados componentes hacen referencia a otros.

A continuación se presenta un ejemplo de una estructura en su forma plana y lógica.

<table>
<tr><th>Diseño lógico</th><th>Diseño físico</th></tr>
<tr>
<td>
<ul>
  Escena
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

En esta ilustración se resalta la diferencia entre el diseño físico y lógico de la escena. A la izquierda, vemos el diseño jerárquico de los datos que la aplicación ve al enumerar la escena. A la derecha, vemos que la escena se compone de 12 componentes distintos a los que se puede tener acceso individualmente si es necesario. Al procesar una nueva escena, esperamos que las aplicaciones recorran esta jerarquía de manera lógica; sin embargo, al realizar un seguimiento entre las actualizaciones de la escena, algunas aplicaciones solo pueden estar interesadas en determinados componentes que se comparten entre dos escenas.

## <a name="api-overview"></a>Introducción a API

En la sección siguiente se proporciona información general de alto nivel sobre las construcciones de comprensión de la escena. Al leer esta sección se proporciona una descripción de cómo se representan las escenas y para qué se usan los distintos componentes. En la siguiente sección se proporcionan ejemplos de código concretos e información adicional con el glosario en esta información general.

Todos los tipos que se describen a continuación residen en el espacio de nombres `Microsoft.MixedReality.SceneUnderstanding`.

### <a name="scenecomponents"></a>SceneComponents

Ahora que comprende el diseño lógico de escenas, ahora podemos presentar el concepto de SceneComponents y cómo se usan para crear la jerarquía. SceneComponents son las descomposiciones más pormenorizadas de SceneUnderstanding que representan una sola cosa principal, por ejemplo, una malla o un cuadro de límite cuádruple o de rectángulo. SceneComponents son elementos que se pueden actualizar de forma independiente y a los que puede hacer referencia otro SceneComponents, por lo que tienen una única propiedad global como un identificador único, lo que permite este tipo de mecanismo de seguimiento o referencia. Los identificadores se usan para la composición lógica de la jerarquía de escenas, así como para la persistencia de objetos (la acción de actualizar una escena en relación con otra). 

Si trata cada escena recién calculada como DISTINCT y simplemente enumera todos los datos que contiene, los identificadores son en gran medida transparentes para usted. Sin embargo, si planea realizar un seguimiento de los componentes de varias actualizaciones, usará los identificadores para indexar y buscar SceneComponents entre los objetos de la escena.

### <a name="sceneobjects"></a>SceneObjects

Un SceneObject es un SceneComponent que representa una instancia de una "cosa", por ejemplo, una pared, una planta, un límite superior, etc. expresado por su propiedad Kind. Los SceneObjects son geométricos y, por tanto, tienen funciones y propiedades que representan su ubicación en el espacio, pero no contienen ninguna estructura geométrica o lógica. En su lugar, SceneObjects hace referencia a otros SceneComponents, en concreto SceneQuads y SceneMeshes, que proporcionan las representaciones variadas que son compatibles con el sistema. Cuando se calcula una nueva escena, es probable que la aplicación Enumere los SceneObjects de la escena para procesar lo que le interesa.

SceneObjects puede tener cualquiera de las siguientes opciones:

<table>
<tr>
<th>SceneObjectKind</th> <th>Descripción</th>
</tr>
<tr><td>Fondo</td><td>Se sabe que el SceneObject <b>no</b> es uno de los otros tipos reconocidos de objeto de escena. Esta clase no se debe confundir con Unknown, donde se sabe que el fondo no es mural, piso, techo, etc. Aunque Unknown no se ha categorizado todavía.</b></td></tr>
<tr><td>Reloj</td><td>Una pared física. Se supone que las paredes son estructuras de entorno inmóviles.</td></tr>
<tr><td>Palabra</td><td>Las plantas son superficies en las que se puede recorrer. Nota: las escaleras no están en el suelo. Tenga en cuenta también que las plantas suponen cualquier superficie que se puede examinar y, por lo tanto, no hay ninguna suposición explícita de un piso singular. Estructuras de varios niveles, rampas, etc... debe clasificarse como Floor.</td></tr>
<tr><td>Ceiling</td><td>La superficie superior de una habitación.</td></tr>
<tr><td>Platform</td><td>Una superficie plana grande en la que se pueden colocar hologramas. Tienden a representar las tablas, los extremos y otras superficies horizontales grandes.</td></tr>
<tr><td>Mundo</td><td>Etiqueta reservada para los datos geométricos que es independiente de la etiqueta. La malla generada al establecer la marca de actualización EnableWorldMesh se clasificaría como World.</td></tr>
<tr><td>Desconocida</td><td>Este objeto de escena todavía se puede clasificar y asignar a un tipo. Esto no se debe confundir con el fondo, ya que este objeto podría ser cualquier cosa, el sistema no ha incorporado todavía una clasificación suficientemente fuerte para él.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Un SceneMesh es un SceneComponent que se aproxima a la geometría de objetos geométricos arbitrarios mediante una lista de triángulos. SceneMeshes se usan en varios contextos diferentes, pueden representar componentes de la estructura de celda estanca o como WorldMesh que representa la malla de asignación espacial sin enlazar asociada a la escena. Los datos de índice y vértices que se proporcionan con cada malla usan el mismo diseño conocido que los [búferes de vértices y de índices](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) que se usan para representar mallas de triángulo en todas las API de representación modernas. Tenga en cuenta que, en la descripción de la escena, las mallas usan índices de 32 bits y es posible que necesiten dividirse en fragmentos para determinados motores de representación.

#### <a name="winding-order-and-coordinate-systems"></a>Orden de bobinado y sistemas de coordenadas

Se espera que todas las mallas generadas por el conocimiento de escenas devuelvan mallas en un sistema de coordenadas de la mano a la derecha con el orden de bobinado. 

Nota: las compilaciones del sistema operativo anteriores a. 191105 pueden tener un error conocido en el que las mallas "mundiales" devolvían en el orden de bobinado en sentido contrario, que se ha corregido posteriormente.

### <a name="scenequad"></a>SceneQuad

Un SceneQuad es un SceneComponent que representa superficies 2D que ocupan el mundo 3D. SceneQuads se puede usar de forma similar a los planos ARKit ARPlaneAnchor o ARCore, pero ofrecen más funcionalidad de alto nivel que los lienzos 2D que usarán las aplicaciones planas o la experiencia de usuario aumentada. se proporcionan API específicas de 2D para cuádruples que facilitan el uso de la ubicación y el diseño, y el desarrollo (con la excepción de la representación) con cuatros se siente más parecido al trabajo con lienzos 2D que las mallas 3D.

#### <a name="scenequad-shape"></a>Forma SceneQuad

SceneQuads define una superficie rectangular limitada en 2D. Sin embargo, los SceneQuads representan superficies con formas arbitrarias y potencialmente complejas (por ejemplo, una tabla con forma de anillo). Para representar la forma compleja de la superficie de una cuádruple, puede usar la API GetSurfaceMask para representar la forma de la superficie en un búfer de imagen que proporcione. Si el SceneObject que tiene el cuádruple también tiene una malla, los triángulos de la malla deben ser equivalentes a esta imagen representada, ambos representan la geometría real de la superficie, simplemente en coordenadas 2D o 3D.

## <a name="scene-understanding-sdk-details-and-reference"></a>Detalles y referencia del SDK de la escena

La siguiente sección le ayudará a familiarizarse con los conceptos básicos de SceneUnderstanding. En esta sección se proporcionan los conceptos básicos, momento en el que debe tener suficiente contexto para examinar las aplicaciones de ejemplo para ver cómo se usa SceneUnderstanding de forma holística.

### <a name="initialization"></a>Inicialización

El primer paso para trabajar con SceneUnderstanding es que la aplicación pueda obtener referencias a un objeto de escena. Esto puede realizarse de una de estas dos formas: el controlador puede calcular una escena, o bien se puede deserializar una escena existente calculada en el pasado. Esto último es especialmente útil para trabajar con SceneUnderstanding durante el desarrollo, donde las aplicaciones y experiencias se pueden crear rápidamente con un dispositivo de realidad mixta.

Las escenas se calculan mediante una SceneObserver. Antes de crear una escena, la aplicación debe consultar el dispositivo para asegurarse de que admite SceneUnderstanding, así como para solicitar acceso de usuario para obtener información que necesita SceneUnderstanding.

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Si no se llama a RequestAccessAsync (), se producirá un error al calcular una nueva escena. A continuación, calcularemos una nueva escena que se basa en torno al casco de realidad mixta y que tiene un radio de 10 medidor.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a>Inicialización de datos (también conocido como la ruta de acceso del equipo)

Aunque se pueden calcular escenas para su consumo directo, también se pueden calcular en forma serializada para su uso posterior. Esto ha demostrado ser muy útil para el desarrollo, ya que permite a los desarrolladores trabajar y probar la comprensión de la escena sin necesidad de un dispositivo. El acto de serializar una escena es casi idéntico al cálculo, los datos se devuelven a la aplicación en lugar de deserializarse localmente mediante el SDK. Después, puede deserializarlo usted mismo o guardarlo para su uso futuro.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a>Enumeración SceneObject

Ahora que la aplicación tiene una escena, la aplicación examinará e interactuará con SceneObjects. Esto se hace mediante el acceso a la propiedad **SceneObjects** :

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a>Actualización de componentes y volver a buscar componentes

Hay otra función que recupera los componentes de la escena denominada ***FindComponent***. Esta función es útil cuando se actualizan objetos de seguimiento y se encuentran en escenas posteriores. El siguiente código calculará una nueva escena en relación con una escena anterior y, a continuación, buscará el piso en la nueva escena.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Acceso a mallas y cuádruples de objetos de escena

Una vez que se ha detectado SceneObjects, es más probable que la aplicación tenga acceso a los datos contenidos en las cuádruples o mallas de las que se compone. Se tiene acceso a estos datos con las propiedades de ***cuádruples*** y ***mallas*** . En el código siguiente se enumeran todos los cuádruples y mallas de nuestro objeto Floor.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Observe que es el SceneObject que tiene la transformación relativa al origen de la escena. Esto se debe a que SceneObject representa una instancia de una "Thing" y es localizable en el espacio, las cuádruples y las mallas representan geometría que se transforma con respecto a su elemento primario. Es posible que SceneObjects independientes haga referencia al mismo SceneMesh/SceneQuad SceneComponents, y también es posible que una SceneObject tenga más de una SceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Trabajar con transformaciones

La comprensión de la escena ha realizado un intento deliberado de alinearse con representaciones de escenas 3D tradicionales al tratar con transformaciones. Por lo tanto, cada escena se limita a un sistema de coordenadas único, de forma muy similar a la mayoría de las representaciones comunes del entorno 3D. Cada SceneObjects proporciona su ubicación como posición y orientación dentro de ese sistema de coordenadas. Si la aplicación está tratando con escenas que amplían el límite de lo que proporciona un único origen, puede delimitar SceneObjects a SpatialAnchors, o generar varias escenas y combinarlas juntas, pero para simplificar, se supone que las escenas estancas existen en su propio origen localizado por un NodeId definido por Scene. OriginSpatialGraphNodeId.

El siguiente código de Unity, por ejemplo, muestra cómo usar las API de Windows y la percepción de Windows para alinear los sistemas de coordenadas. Vea [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) y [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) para obtener más información sobre las API de percepción de Windows y los [objetos nativos de realidad mixta en Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) para obtener más información sobre cómo obtener una SpatialCoordinateSystem que se corresponda con el origen mundial de Unity, así como el método de extensión `.ToUnity()` para la conversión entre `System.Numerics.Matrix4x4` y `UnityEngine.Matrix4x4`.

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

Cada `SceneObject` tiene una propiedad `Position` y `Orientation` que se puede utilizar para colocar el contenido correspondiente en relación con el origen del `Scene`contenedor. Por ejemplo, en el ejemplo siguiente se da por supuesto que el juego es un elemento secundario de la raíz de la escena y asigna su posición y giro local para alinear con una `SceneObject`determinada:

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a>Cuádruple

Las Quad se diseñaron para facilitar escenarios de selección de ubicación 2D y deben considerarse como extensiones para los elementos de la experiencia de usuario de lienzo 2D. Aunque cuádruples son componentes de SceneObjects y se pueden representar en 3D, las propias API en sí suponen que los cuatro son estructuras 2D. Ofrecen información como extensión, forma y proporcionan API para la selección de ubicación.

Las Quad tienen extensiones rectangulares, pero representan superficies 2D con forma arbitraria. Para habilitar la selección de ubicación en estas superficies 2D que interactúan con las utilidades de los cuatro entornos en 3D para que esta interacción sea posible. Actualmente, la comprensión de la escena proporciona dos funciones, **FindCentermostPlacement** y **GetOcclusionMask**. FindCentermostPlacement es una API de alto nivel que busca una posición en la cuádruple donde se puede colocar un objeto e intenta encontrar la mejor ubicación para el objeto, lo que garantiza que el cuadro de límite que proporcione residirá en la superficie subyacente.

En el ejemplo siguiente se muestra cómo buscar la ubicación centermost colocar y delimitar un holograma a la cuádruple.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

Los pasos 1-4 son muy dependientes de la implementación o el marco de trabajo en particular, pero los temas deben ser similares. Es importante tener en cuenta que la cuádruple simplemente representa un plano 2D enlazado que está localizado en el espacio. Teniendo el motor o el marco de trabajo de saber dónde está el cuádruple y la raíz de los objetos en relación con la cuádruple, los hologramas se ubicarán correctamente con respecto al mundo real. Para obtener información más detallada, consulte nuestros ejemplos en cuatro que muestran implementaciones específicas.

### <a name="mesh"></a>Tamiz

Las mallas representan representaciones geométricas de objetos o entornos. De forma similar a la [asignación espacial](spatial-mapping.md), los datos del índice de malla y del vértice que se proporcionan con cada malla de superficie espacial usan el mismo diseño conocido que los búferes de vértices y de índices que se usan para representar mallas de triángulo en todas las API de representación modernas. Las posiciones de los vértices se proporcionan en el sistema de coordenadas de la `Scene`. Las API específicas que se usan para hacer referencia a estos datos son las siguientes:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

El código siguiente proporciona un ejemplo de generación de una lista de triángulos a partir de la estructura de malla:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Los búferes de índice/vértices se deben > = los recuentos de índice o vértices, pero de lo contrario se puede cambiar el tamaño de forma arbitraria, lo que permite reutilizar la memoria de forma eficaz.

## <a name="developing-with-scene-understandings"></a>Desarrollo con conocimientos de escenas

En este momento, debe comprender los principales bloques de creación de la escena que comprende el tiempo de ejecución y el SDK. La mayor parte de la eficacia y la complejidad radica en los patrones de acceso, la interacción con Marcos 3D y las herramientas que se pueden escribir sobre estas API para realizar tareas más avanzadas, como la planeación espacial, el análisis de salas, la navegación, la física, etc. Esperamos que se capturen en ejemplos que deberían ser de esperar en la dirección adecuada para que los escenarios se muestren. Si hay ejemplos/escenarios que no abordamos, háganoslo saber e intentaremos documentar o crear prototipos de lo que necesita.

### <a name="where-can-i-get-sample-code"></a>¿Dónde puedo obtener código de ejemplo?

En la página de la [Página de ejemplo de Unity](https://github.com/sceneunderstanding-microsoft/unitysample) puede encontrar el código de ejemplo de la escena para Unity. Esta aplicación le permitirá comunicarse con el dispositivo y representar los distintos objetos de la escena, o bien le permitirá cargar una escena serializada en su equipo y le permitirá experimentar la comprensión de la escena sin un dispositivo.

### <a name="where-can-i-get-sample-scenes"></a>¿Dónde puedo obtener escenas de ejemplo?

Si tiene un HoloLens2, puede guardar cualquier escena que haya capturado guardando el resultado de ComputeSerializedAsync en un archivo y deserializarlo por su comodidad. 

Si no tiene un dispositivo HoloLens2 pero desea jugar con la comprensión de la escena, tendrá que descargar una escena capturada previamente. El ejemplo de comprensión de la escena se incluye actualmente con escenas serializadas que se pueden descargar y usar por su comodidad. Puede encontrarlos aquí:

[Escenas de ejemplo de la escena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a>Vea también

* [Asignación espacial](spatial-mapping.md)
* [Descripción de escenas](scene-understanding.md)
* [Ejemplo de Unity](https://github.com/sceneunderstanding-microsoft/unitysample)
