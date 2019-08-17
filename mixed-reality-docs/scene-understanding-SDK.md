---
title: SDK de introducción a la escena
description: Guía de programación para el SDK de descripción de la escena
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Comprensión de escenas, asignación espacial, Windows Mixed Reality, Unity
ms.openlocfilehash: 152ffdbd84798c164963717a8dc41beb2e1a0902
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559864"
---
## <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="2d503-104">Información general del SDK de introducción a la escena</span><span class="sxs-lookup"><span data-stu-id="2d503-104">Scene Understanding SDK Overview</span></span>

<span data-ttu-id="2d503-105">El objetivo de la comprensión de la escena es transformar los datos del sensor de entorno no estructurado que captura el dispositivo de realidad mixta y convertirlos en una representación eficaz pero abstracta que es intuitiva y fácil de desarrollar para.</span><span class="sxs-lookup"><span data-stu-id="2d503-105">The goal of Scene Understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="2d503-106">El SDK actúa como la capa de comunicación entre la aplicación y la escena que comprende el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2d503-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="2d503-107">Está diseñado para imitar construcciones estándar existentes como gráficos de escenas 3D para representaciones 3D y rectángulos y paneles 2D para aplicaciones 2D.</span><span class="sxs-lookup"><span data-stu-id="2d503-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span></span> <span data-ttu-id="2d503-108">Aunque las construcciones que comprenden los imitadores se asignarán a marcos concretos que se pueden usar, en general SceneUnderstanding es independiente del marco de trabajo, lo que permite la interoperabilidad entre marcos variados que interactúan con él.</span><span class="sxs-lookup"><span data-stu-id="2d503-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="2d503-109">A medida que la comprensión de la escena evolucione el rol del SDK, se asegurará de que las nuevas representaciones y capacidades sigan expuestas dentro de un marco unificado.</span><span class="sxs-lookup"><span data-stu-id="2d503-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="2d503-110">En este documento, en primer lugar, introduciremos conceptos de alto nivel que le ayudarán a familiarizarse con el uso o el entorno de desarrollo y, a continuación, proporcionar documentación más detallada sobre clases y construcciones específicas.</span><span class="sxs-lookup"><span data-stu-id="2d503-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="2d503-111">¿Dónde obtengo el SDK?</span><span class="sxs-lookup"><span data-stu-id="2d503-111">Where do I get the SDK?</span></span>

<span data-ttu-id="2d503-112">El SDK de SceneUnderstanding se descarga a través de NuGet.</span><span class="sxs-lookup"><span data-stu-id="2d503-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="2d503-113">SDK de SceneUnderstanding</span><span class="sxs-lookup"><span data-stu-id="2d503-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="2d503-114">Antes de empezar, tenga en cuenta que el SDK se ejecuta en la parte superior de UWP y requiere Windows SDK versión 18362 o posterior.</span><span class="sxs-lookup"><span data-stu-id="2d503-114">Before you begin please note that the SDK runs on top of the UWP, and requires Windows SDK version 18362 or higher.</span></span> 

### <a name="the-scene"></a><span data-ttu-id="2d503-115">La escena</span><span class="sxs-lookup"><span data-stu-id="2d503-115">The Scene</span></span>

<span data-ttu-id="2d503-116">El dispositivo de realidad mixta integra constantemente información sobre lo que ve en su entorno.</span><span class="sxs-lookup"><span data-stu-id="2d503-116">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="2d503-117">La comprensión de la escena canaliza todos estos orígenes de datos y genera una sola abstracción unida.</span><span class="sxs-lookup"><span data-stu-id="2d503-117">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="2d503-118">La comprensión de escenas genera escenas que son una composición de [SceneObjects](scene-understanding-SDK.md#sceneobjects) que representan una instancia de un solo elemento (por ejemplo, un muro/techo/piso). Los propios objetos de la escena son una composición de [SceneComponents](scene-understanding-SDK.md#scenecomponents) que representan partes más granulares que componen este SceneObject.</span><span class="sxs-lookup"><span data-stu-id="2d503-118">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="2d503-119">Algunos ejemplos de componentes son cuádruples y mallas, pero en el futuro podrían representar cuadros de límite, mehses de colisión, metadatos, etc.</span><span class="sxs-lookup"><span data-stu-id="2d503-119">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision mehses, metadata etc...</span></span>

<span data-ttu-id="2d503-120">El proceso de conversión de los datos del sensor sin formato en una escena es una operación potencialmente costosa que podría tardar unos segundos en espacios medios (~ 10x10m) hasta minutos para espacios muy grandes (~ 50x50m) y, por lo tanto, no es algo que el dispositivo está calculando sin solicitud de aplicación.</span><span class="sxs-lookup"><span data-stu-id="2d503-120">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="2d503-121">En su lugar, la generación de escenas la desencadena la aplicación a petición.</span><span class="sxs-lookup"><span data-stu-id="2d503-121">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="2d503-122">La clase SceneObserver tiene métodos estáticos que pueden calcular o deserializar una escena, que puede enumerar o interactuar con.</span><span class="sxs-lookup"><span data-stu-id="2d503-122">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="2d503-123">La acción de "proceso" se ejecuta a petición y se ejecuta en la CPU, pero en un proceso independiente (el controlador de realidad mixta).</span><span class="sxs-lookup"><span data-stu-id="2d503-123">The "Compute" action is executed on-demand and executes on the CPU but in a seperate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="2d503-124">Sin embargo, mientras se realiza el proceso en otro proceso, los datos de la escena resultantes se almacenan y mantienen en la aplicación en el objeto de la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-124">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="2d503-125">A continuación se muestra un diagrama que ilustra este flujo de proceso y muestra ejemplos de dos aplicaciones que interconectan con el entorno de tiempo de ejecución de la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-125">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagrama del proceso](images/SU-ProcessFlow.png)

<span data-ttu-id="2d503-127">En el lado izquierdo hay un diagrama del tiempo de ejecución de realidad mixta que siempre está activado y en ejecución en su propio proceso.</span><span class="sxs-lookup"><span data-stu-id="2d503-127">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="2d503-128">Este tiempo de ejecución es responsable de realizar el seguimiento de los dispositivos, la reconstrucción superficial y otras operaciones que la comprensión de la escena usa para entender y explicar el mundo.</span><span class="sxs-lookup"><span data-stu-id="2d503-128">This runtime is responsible for performing device tracking, surface reconstruction, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="2d503-129">En el lado derecho del diagrama, se muestran dos aplicaciones teóricas que hacen uso de la comprensión de la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-129">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="2d503-130">La primera interfaz de la aplicación con MRTK, que usa el SDK de información de escenas internamente, la segunda aplicación calcula y usa dos instancias de sepereate Scene.</span><span class="sxs-lookup"><span data-stu-id="2d503-130">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two sepereate scene instances.</span></span> <span data-ttu-id="2d503-131">Las 3 escenas de este diagrama generan instancias distintas de las escenas, el controlador no realiza un seguimiento del estado global que se comparte entre las aplicaciones y los objetos de escena de una escena no se encuentran en otro.</span><span class="sxs-lookup"><span data-stu-id="2d503-131">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="2d503-132">La comprensión de la escena proporciona un mecanismo para realizar el seguimiento con el tiempo, pero esto se realiza mediante el SDK y codifica el código que realiza este seguimiento en el SDK del proceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2d503-132">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and code the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="2d503-133">Dado que cada escena almacena sus datos en el espacio de memoria de la aplicación, puede suponer que todas las funciones del objeto de escena o de sus datos internos siempre se ejecutan en el proceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2d503-133">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

#### <a name="layout"></a><span data-ttu-id="2d503-134">Diseño</span><span class="sxs-lookup"><span data-stu-id="2d503-134">Layout</span></span>

<span data-ttu-id="2d503-135">Para trabajar con la comprensión de la escena, puede ser útil conocer y entender cómo representa los componentes el tiempo de ejecución de forma lógica y física.</span><span class="sxs-lookup"><span data-stu-id="2d503-135">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="2d503-136">La escena representa los datos con un diseño específico que se eligió para ser sencillo al tiempo que se mantiene una estructura subyacente que se pliable para satisfacer los requisitos futuros sin necesidad de revisiones importantes.</span><span class="sxs-lookup"><span data-stu-id="2d503-136">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="2d503-137">Para ello, la escena almacena todos los componentes (bloques de creación de todos los objetos de escena) en una lista plana y define la jerarquía y la composición a través de referencias en las que determinados componentes hacen referencia a otros.</span><span class="sxs-lookup"><span data-stu-id="2d503-137">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="2d503-138">A continuación se presenta un ejemplo de una estructura en su forma plana y lógica.</span><span class="sxs-lookup"><span data-stu-id="2d503-138">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="2d503-139">Diseño lógico</span><span class="sxs-lookup"><span data-stu-id="2d503-139">Logical Layout</span></span></th><th><span data-ttu-id="2d503-140">Diseño físico</span><span class="sxs-lookup"><span data-stu-id="2d503-140">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="2d503-141">Escenas</span><span class="sxs-lookup"><span data-stu-id="2d503-141">Scene</span></span>
  <ul>
  <li><span data-ttu-id="2d503-142">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="2d503-142">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="2d503-143">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="2d503-143">Mesh_1</span></span></li>
      <li><span data-ttu-id="2d503-144">Quad_1</span><span class="sxs-lookup"><span data-stu-id="2d503-144">Quad_1</span></span></li>
      <li><span data-ttu-id="2d503-145">Quad_2</span><span class="sxs-lookup"><span data-stu-id="2d503-145">Quad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="2d503-146">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="2d503-146">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="2d503-147">Quad_1</span><span class="sxs-lookup"><span data-stu-id="2d503-147">Quad_1</span></span></li>
      <li><span data-ttu-id="2d503-148">Quad_3</span><span class="sxs-lookup"><span data-stu-id="2d503-148">Quad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="2d503-149">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="2d503-149">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="2d503-150">Mesh_3</span><span class="sxs-lookup"><span data-stu-id="2d503-150">Mesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="2d503-151">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="2d503-151">SceneObject_1</span></span></li>
  <li><span data-ttu-id="2d503-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="2d503-152">SceneObject_2</span></span></li>
  <li><span data-ttu-id="2d503-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="2d503-153">SceneObject_3</span></span></li>
  <li><span data-ttu-id="2d503-154">Quad_1</span><span class="sxs-lookup"><span data-stu-id="2d503-154">Quad_1</span></span></li>
  <li><span data-ttu-id="2d503-155">Quad_2</span><span class="sxs-lookup"><span data-stu-id="2d503-155">Quad_2</span></span></li>
  <li><span data-ttu-id="2d503-156">Quad_3</span><span class="sxs-lookup"><span data-stu-id="2d503-156">Quad_3</span></span></li>
  <li><span data-ttu-id="2d503-157">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="2d503-157">Mesh_1</span></span></li>
  <li><span data-ttu-id="2d503-158">Mesh_2</span><span class="sxs-lookup"><span data-stu-id="2d503-158">Mesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="2d503-159">En esta ilustración se resalta la diferencia entre el diseño físico y lógico de la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-159">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="2d503-160">A la derecha, vemos el diseño jerárquico de los datos que la aplicación ve al enumerar la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-160">On the right we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="2d503-161">A la izquierda, vemos que la escena se compone en realidad de 12 componentes distintos a los que se puede tener acceso individualmente si es necesario.</span><span class="sxs-lookup"><span data-stu-id="2d503-161">On the left we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="2d503-162">Al procesar una nueva escena, esperamos que las aplicaciones recorran esta jerarquía de manera lógica; sin embargo, al realizar un seguimiento entre las actualizaciones de la escena, algunas aplicaciones solo pueden estar interesadas en determinados componentes que se comparten entre dos escenas.</span><span class="sxs-lookup"><span data-stu-id="2d503-162">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

### <a name="high-level-overview"></a><span data-ttu-id="2d503-163">Información general de alto nivel</span><span class="sxs-lookup"><span data-stu-id="2d503-163">High-level Overview</span></span>

<span data-ttu-id="2d503-164">En la sección siguiente se proporciona información general de alto nivel sobre las construcciones de comprensión de la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-164">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="2d503-165">Al leer esta sección se proporciona una descripción de cómo se representan las escenas y para qué se usan los distintos componentes.</span><span class="sxs-lookup"><span data-stu-id="2d503-165">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="2d503-166">En la siguiente sección se proporcionan ejemplos de código concretos e información adicional con el glosario en esta información general.</span><span class="sxs-lookup"><span data-stu-id="2d503-166">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

#### <a name="scenecomponents"></a><span data-ttu-id="2d503-167">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="2d503-167">SceneComponents</span></span>

<span data-ttu-id="2d503-168">Ahora que comprende el diseño lógico de escenas, ahora podemos presentar el concepto de SceneComponents y cómo se usan para crear la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="2d503-168">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="2d503-169">SceneComponents son las descomposiciones más pormenorizadas de SceneUnderstanding que representan una sola cosa principal, por ejemplo, una malla o un cuadro de límite cuádruple o de rectángulo.</span><span class="sxs-lookup"><span data-stu-id="2d503-169">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="2d503-170">SceneComponents son elementos que se pueden actualizar de forma independiente y a los que puede hacer referencia otro SceneComponents, por lo que tienen una única propiedad global como un identificador único, lo que permite este tipo de mecanismo de seguimiento o referencia.</span><span class="sxs-lookup"><span data-stu-id="2d503-170">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="2d503-171">Los identificadores se usan para la composición lógica de la jerarquía de escenas, así como para la persistencia de objetos (la acción de actualizar una escena en relación con otra).</span><span class="sxs-lookup"><span data-stu-id="2d503-171">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="2d503-172">Si trata cada escena recién calculada como DISTINCT y simplemente enumera todos los datos que contiene, los identificadores son en gran medida transparentes para usted.</span><span class="sxs-lookup"><span data-stu-id="2d503-172">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="2d503-173">Sin embargo, si planea realizar un seguimiento de los componentes de varias actualizaciones, usará los identificadores para indexar y buscar SceneComponents entre los objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-173">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

#### <a name="sceneobjects"></a><span data-ttu-id="2d503-174">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="2d503-174">SceneObjects</span></span>

<span data-ttu-id="2d503-175">Un SceneObject es un SceneComponent que representa una instancia de una "cosa", por ejemplo, una pared, una planta, un límite superior, etc. expresado por su propiedad Kind.</span><span class="sxs-lookup"><span data-stu-id="2d503-175">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="2d503-176">Los SceneObjects son geométricos y, por tanto, tienen funciones y propiedades que representan su ubicación en el espacio, pero no contienen ninguna estructura geométrica o lógica.</span><span class="sxs-lookup"><span data-stu-id="2d503-176">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="2d503-177">En su lugar, SceneObjects hace referencia a otros SceneComponents, en concreto SceneQuads y SceneMeshes, que proporcionan las representaciones variadas que son compatibles con el sistema.</span><span class="sxs-lookup"><span data-stu-id="2d503-177">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="2d503-178">Cuando se calcula una nueva escena, es probable que la aplicación Enumere los SceneObjects de la escena para procesar lo que le interesa.</span><span class="sxs-lookup"><span data-stu-id="2d503-178">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="2d503-179">SceneObjects puede tener cualquiera de las siguientes opciones:</span><span class="sxs-lookup"><span data-stu-id="2d503-179">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="2d503-180">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="2d503-180">SceneObjectKind</span></span></th> <th><span data-ttu-id="2d503-181">Descripción</span><span class="sxs-lookup"><span data-stu-id="2d503-181">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="2d503-182">Background</span><span class="sxs-lookup"><span data-stu-id="2d503-182">Background</span></span></td><td><span data-ttu-id="2d503-183">Se sabe que el SceneObject <b>no</b> es uno de los otros tipos reconocidos de objeto de escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-183">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="2d503-184">Esta clase no se debe confundir con Unknown, donde se sabe que el fondo no es mural, piso, techo, etc. Aunque Unknown no se ha categorizado todavía.</span><span class="sxs-lookup"><span data-stu-id="2d503-184">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="2d503-185">Reloj</span><span class="sxs-lookup"><span data-stu-id="2d503-185">Wall</span></span></td><td><span data-ttu-id="2d503-186">Una pared física.</span><span class="sxs-lookup"><span data-stu-id="2d503-186">A physical wall.</span></span> <span data-ttu-id="2d503-187">Se supone que las paredes son estructuras de entorno inmóviles.</span><span class="sxs-lookup"><span data-stu-id="2d503-187">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="2d503-188">Palabra</span><span class="sxs-lookup"><span data-stu-id="2d503-188">Floor</span></span></td><td><span data-ttu-id="2d503-189">Las plantas son superficies en las que se puede recorrer.</span><span class="sxs-lookup"><span data-stu-id="2d503-189">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="2d503-190">Nota: las escaleras no están en el suelo.</span><span class="sxs-lookup"><span data-stu-id="2d503-190">Note: stairs are not floors.</span></span> <span data-ttu-id="2d503-191">Tenga en cuenta también que las plantas suponen cualquier superficie que se puede examinar y, por lo tanto, no hay ninguna suposición explícita de un piso singular.</span><span class="sxs-lookup"><span data-stu-id="2d503-191">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="2d503-192">Estructuras de varios niveles, rampas, etc... debe clasificarse como Floor.</span><span class="sxs-lookup"><span data-stu-id="2d503-192">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="2d503-193">Umbral</span><span class="sxs-lookup"><span data-stu-id="2d503-193">Ceiling</span></span></td><td><span data-ttu-id="2d503-194">La superficie superior de una habitación.</span><span class="sxs-lookup"><span data-stu-id="2d503-194">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="2d503-195">Plataforma</span><span class="sxs-lookup"><span data-stu-id="2d503-195">Platform</span></span></td><td><span data-ttu-id="2d503-196">Una superficie plana grande en la que se pueden colocar hologramas.</span><span class="sxs-lookup"><span data-stu-id="2d503-196">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="2d503-197">Tienden a representar las tablas, los extremos y otras superficies horizontales grandes.</span><span class="sxs-lookup"><span data-stu-id="2d503-197">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="2d503-198">Mundo</span><span class="sxs-lookup"><span data-stu-id="2d503-198">World</span></span></td><td><span data-ttu-id="2d503-199">Etiqueta reservada para los datos geométricos que es independiente de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="2d503-199">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="2d503-200">La malla generada al establecer la marca de actualización EnableWorldMesh se clasificaría como World.</span><span class="sxs-lookup"><span data-stu-id="2d503-200">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="2d503-201">Unknown</span><span class="sxs-lookup"><span data-stu-id="2d503-201">Unknown</span></span></td><td><span data-ttu-id="2d503-202">Este objeto de escena todavía se puede clasificar y asignar a un tipo.</span><span class="sxs-lookup"><span data-stu-id="2d503-202">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="2d503-203">Esto no se debe confundir con el fondo, ya que este objeto podría ser cualquier cosa, el sistema no ha incorporado todavía una clasificación suficientemente fuerte para él.</span><span class="sxs-lookup"><span data-stu-id="2d503-203">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

#### <a name="scenemesh"></a><span data-ttu-id="2d503-204">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="2d503-204">SceneMesh</span></span>

<span data-ttu-id="2d503-205">Un SceneMesh es un SceneComponent que se aproxima a la geometría de objetos geométricos arbitrarios mediante una lista de triángulos.</span><span class="sxs-lookup"><span data-stu-id="2d503-205">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="2d503-206">SceneMeshes se usan en varios contextos diferentes, pueden representar componentes de la estructura de la celda estanca o como WorldMesh que representa la reconstrucción de la superficie sin enlazar asociada a la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-206">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded Surface Reconstruction associated with the Scene.</span></span> <span data-ttu-id="2d503-207">Los datos de índice y vértices que se proporcionan con cada malla usan el mismo diseño conocido que los búferes de [vértices y de índices](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) que se usan para representar mallas de triángulo en todas las API de representación modernas.</span><span class="sxs-lookup"><span data-stu-id="2d503-207">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="2d503-208">Tenga en cuenta que, en la descripción de la escena, las mallas usan índices de 32 bits y es posible que necesiten dividirse en fragmentos para determinados motores de representación.</span><span class="sxs-lookup"><span data-stu-id="2d503-208">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="scenequad"></a><span data-ttu-id="2d503-209">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="2d503-209">SceneQuad</span></span>

<span data-ttu-id="2d503-210">Un SceneQuad es un SceneComponent que representa superficies 2D que ocupan el mundo 3D.</span><span class="sxs-lookup"><span data-stu-id="2d503-210">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="2d503-211">SceneQuads se puede usar de forma similar a los planos ARKit ARPlaneAnchor o ARCore, pero ofrecen más funcionalidad de alto nivel que los lienzos 2D que usarán las aplicaciones planas o la experiencia de usuario aumentada.</span><span class="sxs-lookup"><span data-stu-id="2d503-211">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="2d503-212">se proporcionan API específicas de 2D para cuádruples que facilitan el uso de la ubicación y el diseño, y el desarrollo (con la excepción de la representación) con cuatros se siente más parecido al trabajo con lienzos 2D que las mallas 3D.</span><span class="sxs-lookup"><span data-stu-id="2d503-212">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

### <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="2d503-213">Detalles y referencia del SDK de la escena</span><span class="sxs-lookup"><span data-stu-id="2d503-213">Scene Understanding SDK Details and Reference</span></span>

#### <a name="sdk"></a><span data-ttu-id="2d503-214">SDK</span><span class="sxs-lookup"><span data-stu-id="2d503-214">SDK</span></span>

<span data-ttu-id="2d503-215">La siguiente sección le ayudará a familiarizarse con los conceptos básicos de SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="2d503-215">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="2d503-216">En esta sección se proporcionan los conceptos básicos, momento en el que debe tener suficiente contexto para examinar las aplicaciones de ejemplo para ver cómo se usa SceneUnderstanding de forma holística.</span><span class="sxs-lookup"><span data-stu-id="2d503-216">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

#### <a name="initialization"></a><span data-ttu-id="2d503-217">Inicialización</span><span class="sxs-lookup"><span data-stu-id="2d503-217">Initialization</span></span>

<span data-ttu-id="2d503-218">El primer paso para trabajar con SceneUnderstanding es que la aplicación pueda obtener referencias a un objeto de escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-218">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="2d503-219">Esto puede realizarse de una de estas dos formas: el controlador puede calcular una escena, o bien se puede deserializar una escena existente calculada en el pasado.</span><span class="sxs-lookup"><span data-stu-id="2d503-219">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="2d503-220">Esto último es especialmente útil para trabajar con SceneUnderstanding durante el desarrollo, donde las aplicaciones y experiencias se pueden crear rápidamente con un dispositivo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2d503-220">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="2d503-221">Las escenas se calculan mediante una SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="2d503-221">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="2d503-222">Antes de crear una escena, la aplicación debe consultar el dispositivo para asegurarse de que admite SceneUnderstanding, así como para solicitar acceso de usuario para obtener información que necesita SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="2d503-222">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="2d503-223">Si no se llama a RequestAccessAsync (), se producirá un error al calcular una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-223">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="2d503-224">A continuación, calcularemos una nueva escena que se basa en torno al casco de realidad mixta y que tiene un radio de 10 medidor.</span><span class="sxs-lookup"><span data-stu-id="2d503-224">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.Compute(querySettings, 10.0f);
```

#### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="2d503-225">Inicialización de datos (también conocido como</span><span class="sxs-lookup"><span data-stu-id="2d503-225">Initialization from Data (aka.</span></span> <span data-ttu-id="2d503-226">la ruta de acceso del equipo)</span><span class="sxs-lookup"><span data-stu-id="2d503-226">the PC Path)</span></span>

<span data-ttu-id="2d503-227">Aunque se pueden calcular escenas para su consumo directo, también se pueden calcular en forma serializada para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="2d503-227">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="2d503-228">Esto ha demostrado ser muy útil para el desarrollo, ya que permite a los desarrolladores trabajar y probar la comprensión de la escena sin necesidad de un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2d503-228">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="2d503-229">El acto de serializar una escena es casi idéntico al cálculo, los datos se devuelven a la aplicación en lugar de deserializarse localmente mediante el SDK.</span><span class="sxs-lookup"><span data-stu-id="2d503-229">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="2d503-230">Después, puede deserializarlo usted mismo o guardarlo para su uso futuro.</span><span class="sxs-lookup"><span data-stu-id="2d503-230">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneUnderstanding.QuerySettings querySettings;

// Compute a scene but serialized as a byte array
byte[] newSceneBlob = SceneObserver.ComputeSerialized(querySettings, 10.0f);

// If we want to use it immediatley we can de-serialize the scene ourselves
Scene mySceneDeSerialized = Scene.Deserialize(newSceneBlob);

// Save newSceneBlob for later
```

#### <a name="sceneobject-enumeration"></a><span data-ttu-id="2d503-231">Enumeración SceneObject</span><span class="sxs-lookup"><span data-stu-id="2d503-231">SceneObject Enumeration</span></span>

<span data-ttu-id="2d503-232">Ahora que la aplicación tiene una escena, la aplicación examinará e interactuará con SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="2d503-232">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="2d503-233">Esto se hace mediante el acceso a la propiedad **SceneObjects** :</span><span class="sxs-lookup"><span data-stu-id="2d503-233">This is done by accessing the **SceneObjects** property:</span></span>

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

#### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="2d503-234">Actualización de componentes y volver a buscar componentes</span><span class="sxs-lookup"><span data-stu-id="2d503-234">Component update and re-finding components</span></span>

<span data-ttu-id="2d503-235">Hay otra función que recupera los componentes de la escena denominada ***FindComponent***.</span><span class="sxs-lookup"><span data-stu-id="2d503-235">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="2d503-236">Esta función es útil cuando se actualizan objetos de seguimiento y se encuentran en escenas posteriores.</span><span class="sxs-lookup"><span data-stu-id="2d503-236">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="2d503-237">El siguiente código calculará una nueva escena en relación con una escena anterior y, a continuación, buscará el piso en la nueva escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-237">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, but tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.Compute(querySettings, 10.0f, myScene);

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attatched to this floor transform
}
```

### <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="2d503-238">Acceso a mallas y cuádruples de objetos de escena</span><span class="sxs-lookup"><span data-stu-id="2d503-238">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="2d503-239">Una vez que se ha detectado SceneObjects, es más probable que la aplicación tenga acceso a los datos contenidos en las cuatro o las mallas de las que se compone.</span><span class="sxs-lookup"><span data-stu-id="2d503-239">Once SceneObjects have been found your application will most likely want to access the data that is contained n the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="2d503-240">Se tiene acceso a estos datos con las propiedades de cuádruples y ***mallas*** .</span><span class="sxs-lookup"><span data-stu-id="2d503-240">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="2d503-241">En el código siguiente se enumeran todos los cuádruples y mallas de nuestro objeto Floor.</span><span class="sxs-lookup"><span data-stu-id="2d503-241">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the matrix for the SceneObject
System.Numerics.Matrix4x4 floorTransform = firstFloor.LocationAsMatrix();

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

<span data-ttu-id="2d503-242">Observe que es el SceneObject que tiene la transformación relativa al origen de la escena.</span><span class="sxs-lookup"><span data-stu-id="2d503-242">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="2d503-243">Esto se debe a que SceneObject representa una instancia de una "Thing" y es localizable en el espacio, las cuádruples y las mallas representan geometría que se transforma con respecto a su elemento primario.</span><span class="sxs-lookup"><span data-stu-id="2d503-243">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="2d503-244">Es posible que SceneObjects independientes haga referencia al mismo SceneMesh/SceneQuad SceneComponewnts, y también es posible que una SceneObject tenga más de una SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="2d503-244">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponewnts, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="2d503-245">Trabajar con transformaciones</span><span class="sxs-lookup"><span data-stu-id="2d503-245">Dealing with Transforms</span></span>

<span data-ttu-id="2d503-246">La comprensión de la escena ha realizado un intento deliberado de alinearse con representaciones de escenas 3D tradicionales al tratar con transformaciones.</span><span class="sxs-lookup"><span data-stu-id="2d503-246">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="2d503-247">Por lo tanto, cada escena se limita a un sistema de coordenadas único, de forma muy similar a la mayoría de las representaciones comunes del entorno 3D.</span><span class="sxs-lookup"><span data-stu-id="2d503-247">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="2d503-248">Si la aplicación trata de escenas que amplían el límite de lo que proporciona un único origen, puede delimitar SceneObjects a SpatialAnchors, o generar varias escenas y combinarlas juntas, pero para simplificar, se supone que las escenas estancas existen en su propio origen localizado por un NodeId definido por Scene:: OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="2d503-248">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene::OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="2d503-249">El siguiente código de Unity, por ejemplo, muestra cómo usar las API de Windows y la percepción de Windows para alinear los sistemas de coordenadas juntos:</span><span class="sxs-lookup"><span data-stu-id="2d503-249">The following unity code, for example, shows how to use windows perception and Unity APIs to align coordinate systems together:</span></span>


```cs
    public static System.Numerics.Matrix4x4? GetSceneToUnityTransform(Guid nodeId)
    {
        System.Numerics.Matrix4x4? sceneToUnityTransform; 
       
        SpatialCoordinateSystem sceneSpatialCoordinateSystem = Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(nodeId);
        SpatialCoordinateSystem unitySpatialCoordinateSystem = (SpatialCoordinateSystem)System.Runtime.InteropServices.Marshal.GetObjectForIUnknown(UnityEngine.XR.WSA.WorldManager.GetNativeISpatialCoordinateSystemPtr());

        sceneToUnityTransform = sceneSpatialCoordinateSystem.TryGetTransformTo(unitySpatialCoordinateSystem);

        if (sceneToUnityTransform != null)
        {
            sceneToUnityTransform = TransformUtils.ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
        }
        
        return sceneToUnityTransform;
    }

    /// <summary>
    /// Converts a transformation matrix from right handed (+x is right, +y is up, +z is back) to left handed (+x is right, +y is up, +z is front).
    /// </summary>
    /// <param name="transformationMatrix">Right-handed transformation matrix to convert.</param>
    /// <returns>Converted left-handed matrix.</returns>
    public System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 transformationMatrix)
    {
        transformationMatrix.M13 = -transformationMatrix.M13;
        transformationMatrix.M23 = -transformationMatrix.M23;
        transformationMatrix.M43 = -transformationMatrix.M43;

        transformationMatrix.M31 = -transformationMatrix.M31;
        transformationMatrix.M32 = -transformationMatrix.M32;
        transformationMatrix.M34 = -transformationMatrix.M34;

        return transformationMatrix;
    }
```

<span data-ttu-id="2d503-250">Y el código siguiente llama a esta función:</span><span class="sxs-lookup"><span data-stu-id="2d503-250">And the following code calls this function:</span></span>

```cs
System.Numerics.Matrix4x4? sceneToUnityTransform = TransformUtils.GetSceneToUnityTransform(scene.OriginSpatialGraphNodeId);

// Set the root transform
Vector3 t;
Quaternion r;
Vector3 s;

System.Numerics.Matrix4x4.Decompose(sceneToUnityTransform, out s, out r, out t);
SceneRoot.Transform.SetPositionAndRotation(t, r);
```

### <a name="quad"></a><span data-ttu-id="2d503-251">Cuádruple</span><span class="sxs-lookup"><span data-stu-id="2d503-251">Quad</span></span>

<span data-ttu-id="2d503-252">Las Quad se diseñaron para facilitar escenarios de selección de ubicación 2D y deben considerarse como extensiones para los elementos de la experiencia de usuario de lienzo 2D.</span><span class="sxs-lookup"><span data-stu-id="2d503-252">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="2d503-253">Aunque cuádruples son componentes de SceneObjects y se pueden representar en 3D, las propias API en sí suponen que los cuatro son estructuras 2D.</span><span class="sxs-lookup"><span data-stu-id="2d503-253">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="2d503-254">Ofrecen información como extensión, forma y proporcionan API para la selección de ubicación.</span><span class="sxs-lookup"><span data-stu-id="2d503-254">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="2d503-255">Las Quad tienen extensiones rectangulares, pero representan superficies 2D con forma arbitraria.</span><span class="sxs-lookup"><span data-stu-id="2d503-255">Quads have rectangular extents, but they represent arbitrarily shaped 2d surfaces.</span></span> <span data-ttu-id="2d503-256">Para habilitar la selección de ubicación en estas superficies 2D que interactúan con las utilidades de los cuatro entornos en 3D para que esta interacción sea posible.</span><span class="sxs-lookup"><span data-stu-id="2d503-256">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="2d503-257">Actualmente, la comprensión de la escena proporciona dos funciones, **FindCentermostPlacement** y **GetOcclusionMask**.</span><span class="sxs-lookup"><span data-stu-id="2d503-257">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="2d503-258">FindCentermostPlacement es una API de alto nivel que busca una posición en la cuádruple donde se puede colocar un objeto e intenta encontrar la mejor ubicación para el objeto, lo que garantiza que el cuadro de límite que proporcione residirá en la superficie subyacente.</span><span class="sxs-lookup"><span data-stu-id="2d503-258">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="2d503-259">En el ejemplo siguiente se muestra cómo buscar la ubicación centermost colocar y delimitar un holograma a la cuádruple.</span><span class="sxs-lookup"><span data-stu-id="2d503-259">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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
                // Step 1: Create a new node QuadTransformNode as a child of Root, and set the transform from quad[0].Transform
                // Step 2: Create your hologram and set it as a child of QuadTransformNode
                // Step 3: Set the QuadTransformNode tranform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="2d503-260">Los pasos 1-3 son muy dependientes de la implementación o el marco de trabajo en particular, pero los temas deben ser similares.</span><span class="sxs-lookup"><span data-stu-id="2d503-260">Steps 1-3 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="2d503-261">Es importante tener en cuenta que la cuádruple no está pensada normalmente como, simplemente representa un plano 2D enlazado que está localizado en el espacio.</span><span class="sxs-lookup"><span data-stu-id="2d503-261">It is important to note that the Quad is not usually intended to be, is just represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="2d503-262">Si el motor o el marco de trabajo saben dónde está la cuádruple y la raíz de los objetos en relación con la cuádruple, los hologramas se encontrarán correctamente.</span><span class="sxs-lookup"><span data-stu-id="2d503-262">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly.</span></span> <span data-ttu-id="2d503-263">Para obtener información más detallada, consulte nuestros ejemplos en cuatro que muestran implementaciones específicas.</span><span class="sxs-lookup"><span data-stu-id="2d503-263">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="2d503-264">Tamiz</span><span class="sxs-lookup"><span data-stu-id="2d503-264">Mesh</span></span>

<span data-ttu-id="2d503-265">Las mallas representan representaciones geométricas de objetos o entornos.</span><span class="sxs-lookup"><span data-stu-id="2d503-265">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="2d503-266">De forma similar a la [asignación espacial](spatial-mapping.md), los datos del índice de malla y del vértice que se proporcionan con cada malla de superficie espacial usan el mismo diseño conocido que los búferes de vértices y de índices que se usan para representar mallas de triángulo en todas las API de representación modernas.</span><span class="sxs-lookup"><span data-stu-id="2d503-266">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="2d503-267">Las API específicas que se usan para hacer referencia a estos datos son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="2d503-267">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(float[] vertices);
```

<span data-ttu-id="2d503-268">\* \* Nota: GetVertices devuelve una lista de vértices donde cada tres tuplas de valores de punto flotante representa una única coordenada en el espacio de x, y y z cartesiano.</span><span class="sxs-lookup"><span data-stu-id="2d503-268">\*\*Note: GetVertices returns a list of vertices where every 3-tuple of floating point values represents a single coordinate in cartesian x,y and z space.</span></span>

<span data-ttu-id="2d503-269">El código siguiente proporciona un ejemplo de generación de una lista de triángulos a partir de la estructura de malla:</span><span class="sxs-lookup"><span data-stu-id="2d503-269">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
float[] positions = new float[mesh.VertexCount * 3];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="2d503-270">Los búferes de índice/vértices se deben > = los recuentos de índice o vértices, pero de lo contrario se puede cambiar el tamaño de forma arbitraria, lo que permite reutilizar la memoria de forma eficaz.</span><span class="sxs-lookup"><span data-stu-id="2d503-270">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

### <a name="developing-with-scene-understandings"></a><span data-ttu-id="2d503-271">Desarrollo con conocimientos de escenas</span><span class="sxs-lookup"><span data-stu-id="2d503-271">Developing with Scene Understandings</span></span>

<span data-ttu-id="2d503-272">En este momento, debe comprender los principales bloques de creación de la escena que comprende el tiempo de ejecución y el SDK.</span><span class="sxs-lookup"><span data-stu-id="2d503-272">At this point you should understand the core building blocks of the Scene Understanding runtime and SDK.</span></span> <span data-ttu-id="2d503-273">La mayor parte de la eficacia y la complejidad radica en los patrones de acceso, la interacción con los marcos 3D y las herramientas que se pueden escribir sobre estas API para realizar tareas más avanzadas, como la planeación espacial, el análisis de salas, la navegación, la física, etc. Esperamos que se capturen en ejemplos que deberían ser de esperar en la dirección adecuada para que los escenarios se muestren.</span><span class="sxs-lookup"><span data-stu-id="2d503-273">The bulk of the power and complexity lies in access patterns, interaction with 3d frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc... We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="2d503-274">Si hay ejemplos/escenarios que no abordamos, háganoslo saber e intentaremos documentar o crear prototipos de lo que necesita.</span><span class="sxs-lookup"><span data-stu-id="2d503-274">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d503-275">Vea también</span><span class="sxs-lookup"><span data-stu-id="2d503-275">See also</span></span>

* [<span data-ttu-id="2d503-276">asignación espacial</span><span class="sxs-lookup"><span data-stu-id="2d503-276">spatial mapping</span></span>](spatial-mapping.md)
