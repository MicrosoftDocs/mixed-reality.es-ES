---
title: Interacciones instintivas
description: Aprende la filosofía de interacciones simples e instintivas, integrada en la plataforma de realidad mixta.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hololens, MMR, multimodal
ms.openlocfilehash: 6b54d6e844c1b501a0835fc3a48deb4932ba551d
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539735"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="b1ce5-104">Introducción a las interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="b1ce5-104">Introducing instinctual interactions</span></span>

![Manipulación lejana con las manos](images/04_InteractionFundamentals.png)

<span data-ttu-id="b1ce5-106">La filosofía de interacciones simples e instintivas está integrada en toda la plataforma de realidad integrada (MR).</span><span class="sxs-lookup"><span data-stu-id="b1ce5-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="b1ce5-107">Hemos dado tres pasos para garantizar que los desarrolladores y diseñadores de aplicaciones puedan proporcionar interacciones sencillas e intuitivas a sus clientes.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="b1ce5-108">En primer lugar, nos hemos asegurado de que nuestros sensores y nuestra tecnología de entrada (que incluyen el seguimiento de la mano, el seguimiento de los ojos y la entrada de lenguaje natural), se combinen en modelos de interacción multimodal perfecta.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-108">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  
<span data-ttu-id="b1ce5-109">Según nuestras investigaciones, el diseño y el desarrollo en un marco multimodal (y no basado en entradas individuales) es la clave para crear experiencias instintivas.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-109">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="b1ce5-110">En segundo lugar, somos conscientes de que muchos desarrolladores tienen como destino varios dispositivos HoloLens, como HoloLens 2, HoloLens (1.ª generación) u HoloLens y VR.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-110">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  
<span data-ttu-id="b1ce5-111">Por lo tanto, hemos diseñado nuestros modelos de interacción para que funcionen en todos los dispositivos, aunque la tecnología de entrada sea diferente en cada dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-111">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  
<span data-ttu-id="b1ce5-112">Por ejemplo, la interacción lejana con los cascos envolventes de Windows con un controlador 6DoF y la interacción lejana con HoloLens 2 usan prestaciones y patrones idénticos, lo que facilita el proceso para el desarrollo de aplicaciones multidispositivo y proporciona naturalidad a las interacciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-112">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use identical affordances and patterns, making it easy for cross-device application development and providing a natural feel to user interactions.</span></span> 

<span data-ttu-id="b1ce5-113">Aunque sabemos que existen miles de interacciones posibles eficaces, atractivas y mágicas en la realidad mixta, hemos descubierto que el empleo intencionado de un modelo de interacción único de principio a fin en una aplicación es la mejor manera de asegurarse de que los usuarios vivan una gran experiencia.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-113">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model end-to-end in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="b1ce5-114">Para ello, hemos incluido tres elementos en esta guía de interacción:</span><span class="sxs-lookup"><span data-stu-id="b1ce5-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="b1ce5-115">Instrucciones específicas en torno a los tres modelos de interacción principales y los componentes y patrones necesarios para cada uno.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-115">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="b1ce5-116">Instrucciones complementarias acerca de las demás ventajas que ofrece nuestra plataforma.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-116">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="b1ce5-117">Instrucciones generales para ayudarte a seleccionar el modelo de interacción adecuado para tu escenario de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-117">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="b1ce5-118">Modelos de interacción multimodal</span><span class="sxs-lookup"><span data-stu-id="b1ce5-118">Multimodal interaction models</span></span>

<span data-ttu-id="b1ce5-119">Según nuestras investigaciones y los comentarios de los clientes, hemos descubierto que hay tres modelos de interacción principales que se adaptan a la mayoría de las experiencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-119">Based on our research and feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span> <span data-ttu-id="b1ce5-120">En muchos sentidos, el modelo de interacción es el modelo mental del usuario de cómo completar un flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-120">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="b1ce5-121">Cada uno de estos modelos de interacción está optimizado para un conjunto de necesidades del cliente y es conveniente, eficaz y utilizable cuando se usa correctamente.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-121">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="b1ce5-122">El gráfico siguiente es una introducción simplificada.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="b1ce5-123">En las páginas siguientes hay vínculos a información detallada sobre el uso de cada modelo de interacción con imágenes y ejemplos de código.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b1ce5-124"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="b1ce5-125"><strong>Escenarios de ejemplo</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="b1ce5-126"><strong>Apto para</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="b1ce5-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b1ce5-128"><a href="hands-and-tools.md">Controladores de movimiento y manos</a></span><span class="sxs-lookup"><span data-stu-id="b1ce5-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="b1ce5-129">Experiencias espaciales en 3D, como el diseño espacial, la manipulación de contenido o la simulación.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="b1ce5-130">Ideal para usuarios nuevos, junto con la voz, el seguimiento de los ojos o la mirada con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="b1ce5-131">Curva de aprendizaje reducida.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-131">Low learning curve.</span></span> <span data-ttu-id="b1ce5-132">Experiencia de usuario coherente en el seguimiento de la mano y los controladores 6DoF.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="b1ce5-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b1ce5-133">HoloLens 2</span></span><br><span data-ttu-id="b1ce5-134">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="b1ce5-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b1ce5-135"><a href="hands-free.md">Manos libres</a></span><span class="sxs-lookup"><span data-stu-id="b1ce5-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="b1ce5-136">Experiencias contextuales en las que las manos de un usuario están ocupadas, como, por ejemplo, durante el aprendizaje de un trabajo y las tareas de mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="b1ce5-137">Es necesario algún aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-137">Some learning required.</span></span> <span data-ttu-id="b1ce5-138">Si las manos no están disponibles, el dispositivo encaja bien con el lenguaje natural y la voz.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="b1ce5-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b1ce5-139">HoloLens 2</span></span><br><span data-ttu-id="b1ce5-140">HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="b1ce5-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="b1ce5-141">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="b1ce5-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b1ce5-142"><a href="gaze-and-commit.md">Mirada y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="b1ce5-142"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="b1ce5-143">Experiencias mediante clic; por ejemplo, presentaciones 3D, demostraciones.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="b1ce5-144">Requiere aprender HMD pero no en dispositivos móviles.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="b1ce5-145">Recomendado para controladores accesibles.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-145">Best for accessible controllers.</span></span> <span data-ttu-id="b1ce5-146">Recomendado para HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="b1ce5-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="b1ce5-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b1ce5-147">HoloLens 2</span></span><br><span data-ttu-id="b1ce5-148">HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="b1ce5-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="b1ce5-149">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="b1ce5-149">Immersive headsets</span></span><br><span data-ttu-id="b1ce5-150">Realidad aumentada en dispositivos móviles</span><span class="sxs-lookup"><span data-stu-id="b1ce5-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="b1ce5-151">Para asegurarse de que no haya lagunas en la experiencia de interacción del usuario, lo mejor es seguir las instrucciones de un único modelo de principio a fin.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-151">To ensure that there are no gaps in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="b1ce5-152">En las secciones siguientes se describen los pasos para seleccionar e implementar uno de estos modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-152">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="b1ce5-153">Al final de esta página, encontrarás información para:</span><span class="sxs-lookup"><span data-stu-id="b1ce5-153">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="b1ce5-154">Elegir un modelo de interacción para los clientes.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-154">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="b1ce5-155">Implementación del modelo de interacción</span><span class="sxs-lookup"><span data-stu-id="b1ce5-155">Implementing the interaction model</span></span>
* <span data-ttu-id="b1ce5-156">Realizar la transición entre distintos modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-156">Transitioning between interaction models</span></span>
* <span data-ttu-id="b1ce5-157">Diseñar los pasos siguientes.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-157">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="b1ce5-158">Elección de un modelo de interacción para los clientes</span><span class="sxs-lookup"><span data-stu-id="b1ce5-158">Choose an interaction model for your customer</span></span>

<span data-ttu-id="b1ce5-159">Normalmente, los desarrolladores y creadores han considerado los tipos de interacciones que pueden tener sus clientes.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-159">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="b1ce5-160">Para fomentar un enfoque centrado en el cliente durante el diseño, se recomienda seguir estas instrucciones para seleccionar el modelo de interacción optimizado para el cliente.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-160">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="b1ce5-161">¿Por qué seguir esta guía?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-161">Why follow this guidance?</span></span>

* <span data-ttu-id="b1ce5-162">Los modelos de interacción se han probado con criterios objetivos y subjetivos, como el esfuerzo físico y cognitivo, la capacidad intuitiva y la facilidad de aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-162">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="b1ce5-163">Dado que las interacciones son diferentes, las prestaciones visuales y auditivas, y el comportamiento de los objetos también pueden diferir entre los modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-163">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="b1ce5-164">La combinación de elementos de varios modelos de interacción crea el riesgo de competencia entre las prestaciones, por ejemplo, haces de mano y un cursor de la mirada con la cabeza simultáneos.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-164">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="b1ce5-165">Esto puede saturar y confundir a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-165">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="b1ce5-166">Estos son algunos ejemplos de cómo se optimizan las prestaciones y los comportamientos para cada modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="b1ce5-167">Con frecuencia vemos que los nuevos usuarios tienen preguntas similares, tales como _"¿cómo sé que el sistema funciona?_ , _¿cómo sé lo que puedo hacer?_ y _¿cómo sé si se entiende lo que acabo de hacer?"_ .</span><span class="sxs-lookup"><span data-stu-id="b1ce5-167">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b1ce5-168"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="b1ce5-169"><strong>¿Cómo sé que funciona?</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="b1ce5-170"><strong>¿Cómo sé qué puedo hacer?</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="b1ce5-171"><strong>¿Cómo sé qué acabo de hacer?</strong></span><span class="sxs-lookup"><span data-stu-id="b1ce5-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b1ce5-172"><a href="hands-and-tools.md">Controladores de movimiento y manos</a></span><span class="sxs-lookup"><span data-stu-id="b1ce5-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="b1ce5-173">Veo una malla de mano, una prestación de dedo o haces de mano o controlador.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-173">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="b1ce5-174">Veo controladores que se pueden agarrar o aparece un rectángulo de selección cuando mi mano está cerca de un objeto.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-174">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="b1ce5-175">Puedo oír tonos audibles y ver animaciones al agarrar y soltar.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b1ce5-176"><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="b1ce5-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="b1ce5-177">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="b1ce5-178">El cursor cambia de estado cuando se encuentra sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-178">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="b1ce5-179">Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-179">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="b1ce5-180"><a href="hands-free.md">Manos libres (mirada con la cabeza y permanencia)</a></span><span class="sxs-lookup"><span data-stu-id="b1ce5-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="b1ce5-181">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="b1ce5-182">Veo un indicador de progreso al detenerme en un objeto con el que se puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="b1ce5-183">Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b1ce5-184"><a href="hands-free.md">Manos libres (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="b1ce5-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="b1ce5-185">Veo un indicador de escucha y leyendas que muestran lo que ha oído el sistema.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="b1ce5-186">Recibo mensajes de voz y sugerencias.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-186">I get voice prompts and hints.</span></span> <span data-ttu-id="b1ce5-187">Cuando digo: "¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="b1ce5-187">When I say: "What can I say?"</span></span> <span data-ttu-id="b1ce5-188">Veo comentarios.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="b1ce5-189">Veo u oigo confirmaciones visuales y auditivas cuando emito un comando u obtengo una experiencia de usuario de desambiguación cuando es necesario.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-189">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="b1ce5-190">A continuación, se muestran las preguntas que pueden ayudar a los equipos a seleccionar un modelo de interacción:</span><span class="sxs-lookup"><span data-stu-id="b1ce5-190">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="b1ce5-191">Q:  ¿Los usuarios quieren tocar hologramas y realizar manipulaciones holográficas de precisión?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="b1ce5-192">R:  Si es así, consulta el modelo de interacción de manos y controladores de movimiento para la precisión en el establecimiento del destino y la manipulación.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="b1ce5-193">Q:  ¿Los usuarios necesitan tener las manos libres para sus tareas en el mundo real?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="b1ce5-194">R:  Si es así, consulta el modelo de interacción de manos libres, que proporciona una gran experiencia mediante interacciones basadas en la mirada y la voz.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="b1ce5-195">Q:  ¿Los usuarios tienen tiempo para aprender las interacciones de la aplicación de MR o necesitan interacciones con la curva de aprendizaje más corta posible?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="b1ce5-196">R:  Para una curva de aprendizaje más baja e interacciones más intuitivas, se recomienda el modelo de manos y controladores de movimiento, siempre y cuando los usuarios puedan usar sus manos para la interacción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-196">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="b1ce5-197">Q:  ¿Los usuarios utilizan controladores de movimiento para apuntar y manipular?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="b1ce5-198">R:  El modelo de manos y controladores de movimiento incluye instrucciones completas para crear una gran experiencia con controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="b1ce5-199">Q:  ¿Los usuarios utilizan un controlador de accesibilidad o un controlador Bluetooth común, como un dispositivo de clic?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="b1ce5-200">R:  Se recomienda el modelo de mirada con la cabeza y confirmación para todos los controladores sin seguimiento.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="b1ce5-201">Se ha diseñado para que los usuarios puedan recorrer una experiencia completa con un sencillo mecanismo de "establecer destino y confirmar".</span><span class="sxs-lookup"><span data-stu-id="b1ce5-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="b1ce5-202">Q: ¿Los usuarios recorren una experiencia simplemente haciendo clic (por ejemplo, en un entorno similar a una presentación de diapositivas en 3D) en lugar de navegar por diseños densos de controles de interfaz de usuario?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="b1ce5-203">R:  Si los usuarios no necesitan controlar una gran cantidad de elementos de interfaz de usuario, el modelo de mirada con la cabeza y confirmación es una opción fácil de aprender, en la que los usuarios no tienen que preocuparse sobre cómo establecer un destino.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="b1ce5-204">Q:  ¿Los usuarios usan cascos envolventes tanto HoloLens (1.ª generación) como HoloLens 2 o Windows Mixed Reality (VR)?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="b1ce5-205">R:  Mirada con la cabeza y confirmación es el modelo de interacción para HoloLens (1.ª generación), por lo que se recomienda que los creadores que admiten HoloLens (1.ª generación) usen la mirada con la cabeza y confirmación para todas las características o modos que los usuarios pueden experimentar con los cascos HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="b1ce5-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="b1ce5-206">Consulta la sección siguiente sobre la *transición de los modelos de interacción* para más información acerca de cómo crear una gran experiencia para varias generaciones de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="b1ce5-207">Q: ¿Qué sucede con los usuarios que son generalmente móviles abarcan un amplio espacio o se mueven entre espacios, frente a los usuarios que tienden a funcionar en un único espacio?</span><span class="sxs-lookup"><span data-stu-id="b1ce5-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="b1ce5-208">R:  Cualquiera de los modelos de interacción funcionará para estos usuarios.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="b1ce5-209">[Próximamente](news.md) habrá disponible más información específica para el diseño de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-209">More guidance specific to app design [coming soon](news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="b1ce5-210">Transición de los modelos de interacción</span><span class="sxs-lookup"><span data-stu-id="b1ce5-210">Transitioning interaction models</span></span>
<span data-ttu-id="b1ce5-211">También hay casos de uso en los que puede ser necesario usar más de un modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="b1ce5-212">Por ejemplo, el flujo de creación de la aplicación utiliza el modelo de interacción de _"manos y controladores de movimiento"_ , pero quieres utilizar un modo de manos libres para los técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-212">For example, your application's creation flow utilizes the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span>
<span data-ttu-id="b1ce5-213">Si la experiencia requiere varios modelos de interacción, ten en cuenta que muchos usuarios pueden encontrar dificultades para realizar la transición de un modelo a otro, especialmente los usuarios que no están familiarizados con la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-213">If your experience does require multiple interaction models, please keep in mind that many users might encounter difficulty when transitioning from one model to another, especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="b1ce5-214">Trabajamos constantemente en nuevas instrucciones que estarán disponibles para los desarrolladores y diseñadores, para informarles sobre cómo, cuándo y por qué usar varios modelos de interacción de MR.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="b1ce5-215">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b1ce5-215">See also</span></span>
* [<span data-ttu-id="b1ce5-216">Comodidad</span><span class="sxs-lookup"><span data-stu-id="b1ce5-216">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="b1ce5-217">Interacción basada en los ojos</span><span class="sxs-lookup"><span data-stu-id="b1ce5-217">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="b1ce5-218">Seguimiento de los ojos en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b1ce5-218">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="b1ce5-219">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="b1ce5-219">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b1ce5-220">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="b1ce5-220">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b1ce5-221">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="b1ce5-221">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b1ce5-222">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="b1ce5-222">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="b1ce5-223">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="b1ce5-223">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="b1ce5-224">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="b1ce5-224">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b1ce5-225">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="b1ce5-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="b1ce5-226">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="b1ce5-226">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="b1ce5-227">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="b1ce5-227">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="b1ce5-228">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="b1ce5-228">Voice input</span></span>](voice-input.md)


