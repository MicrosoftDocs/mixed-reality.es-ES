---
title: Introducción a la interacción multimodal
description: Introducción a la interacción multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hololens, MMR, multimodal
ms.openlocfilehash: 7b04141c832597be4bb58447629e0ef6e248dc2b
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415254"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="d566e-104">Introducción a las interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="d566e-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="d566e-105">La filosofía de interacciones simples e instintivas está integrada en la plataforma Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="d566e-105">The philosophy of simple, instinctual interactions is interwoven throughout the Mixed Reality platform.</span></span>  <span data-ttu-id="d566e-106">Hemos dado tres pasos para garantizar que los desarrolladores y diseñadores de aplicaciones puedan proporcionar interacciones sencillas e intuitivas a sus clientes.</span><span class="sxs-lookup"><span data-stu-id="d566e-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="d566e-107">En primer lugar, nos hemos asegurado de que nuestros sensores y nuestra tecnología de entrada (que incluyen el seguimiento de la mano, el seguimiento de los ojos y la entrada de lenguaje natural), se combinen en modelos de interacción multimodal perfecta.</span><span class="sxs-lookup"><span data-stu-id="d566e-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  <span data-ttu-id="d566e-108">Según nuestras investigaciones, el diseño y el desarrollo en un marco multimodal, y no basado en entradas únicas, es la clave para crear experiencias instintivas.</span><span class="sxs-lookup"><span data-stu-id="d566e-108">Based on our research, designing and developing within a multimodal framework, and not based on single inputs, is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="d566e-109">En segundo lugar, somos conscientes de que muchos desarrolladores tienen como destino varios dispositivos HoloLens, como HoloLens 2, HoloLens (1.ª generación) u HoloLens y VR.</span><span class="sxs-lookup"><span data-stu-id="d566e-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="d566e-110">Por lo tanto, hemos diseñado nuestros modelos de interacción para que funcionen en todos los dispositivos, aunque la tecnología de entrada sea diferente en cada dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d566e-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  <span data-ttu-id="d566e-111">Por ejemplo, la interacción lejana en los cascos envolventes de Windows con un controlador 6DoF y la interacción lejana con HoloLens 2 usan prestaciones y patrones idénticos, lo que facilita el proceso para el desarrollo de aplicaciones multidispositivo que proporcione naturalidad a las interacciones del usuario final.</span><span class="sxs-lookup"><span data-stu-id="d566e-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use  identical affordances and patterns, making it easy for cross-device application development that provides a natural feel to end-user interactions.</span></span> 

<span data-ttu-id="d566e-112">Aunque sabemos que existen miles de interacciones posibles eficaces, atractivas y mágicas en la realidad mixta (MR), hemos descubierto que el empleo intencionado de un modelo de interacción único de principio a fin en una aplicación es la mejor manera de asegurarse de que los usuarios vivan una gran experiencia.</span><span class="sxs-lookup"><span data-stu-id="d566e-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in mixed reality (MR), we've found that intentionally employing a single interaction model, end-to-end, in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="d566e-113">Para ello, hemos incluido tres elementos en esta guía de interacción:</span><span class="sxs-lookup"><span data-stu-id="d566e-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="d566e-114">Estas instrucciones están estructuradas en torno a los tres modelos de interacción principales y los componentes y patrones necesarios para cada uno.</span><span class="sxs-lookup"><span data-stu-id="d566e-114">This guidance is structured around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="d566e-115">Se han incluido instrucciones complementarias acerca de las demás ventajas que ofrece nuestra plataforma.</span><span class="sxs-lookup"><span data-stu-id="d566e-115">Supplemental guidance has been included about other benefits that our platform provides.</span></span>
* <span data-ttu-id="d566e-116">También se han incluido instrucciones para ayudarte a seleccionar el modelo de interacción adecuado para tu escenario de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="d566e-116">Guidance has also been included to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="d566e-117">Modelos de interacción multimodal</span><span class="sxs-lookup"><span data-stu-id="d566e-117">Multimodal interaction models</span></span>

<span data-ttu-id="d566e-118">Según nuestras investigaciones y los comentarios de los clientes, hemos descubierto que hay tres modelos de interacción principales que se adaptan a la mayoría de las experiencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d566e-118">Based on our research as well as feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="d566e-119">En muchos sentidos, el modelo de interacción es el modelo mental del usuario para completar los flujos.</span><span class="sxs-lookup"><span data-stu-id="d566e-119">In many ways, the interaction model is the user's mental model for completing their flows.</span></span> <span data-ttu-id="d566e-120">Cada uno de estos modelos de interacción está optimizado para un conjunto de necesidades del cliente.</span><span class="sxs-lookup"><span data-stu-id="d566e-120">Each of these interaction models is optimized for a set of customer needs.</span></span> <span data-ttu-id="d566e-121">Cada uno de ellos resulta práctico, eficaz y útil por sí mismo.</span><span class="sxs-lookup"><span data-stu-id="d566e-121">Each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="d566e-122">El gráfico siguiente es una introducción simplificada.</span><span class="sxs-lookup"><span data-stu-id="d566e-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="d566e-123">En las páginas siguientes hay vínculos a información detallada sobre el uso de cada modelo de interacción con imágenes y ejemplos de código.</span><span class="sxs-lookup"><span data-stu-id="d566e-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d566e-124"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="d566e-125"><strong>Escenarios de ejemplo</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="d566e-126"><strong>Apto para</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="d566e-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d566e-128"><a href="hands-and-tools.md">Controladores de movimiento y manos</a></span><span class="sxs-lookup"><span data-stu-id="d566e-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="d566e-129">Experiencias espaciales en 3D, como el diseño espacial, la manipulación de contenido o la simulación.</span><span class="sxs-lookup"><span data-stu-id="d566e-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="d566e-130">Ideal para usuarios nuevos, junto con la voz, el seguimiento de los ojos o la mirada con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="d566e-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="d566e-131">Curva de aprendizaje reducida.</span><span class="sxs-lookup"><span data-stu-id="d566e-131">Low learning curve.</span></span> <span data-ttu-id="d566e-132">Experiencia de usuario coherente en el seguimiento de la mano y los controladores 6DoF.</span><span class="sxs-lookup"><span data-stu-id="d566e-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="d566e-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d566e-133">HoloLens 2</span></span><br><span data-ttu-id="d566e-134">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="d566e-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d566e-135"><a href="hands-free.md">Manos libres</a></span><span class="sxs-lookup"><span data-stu-id="d566e-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="d566e-136">Experiencias contextuales en las que las manos de un usuario están ocupadas, como, por ejemplo, durante el aprendizaje de un trabajo o las tareas de mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="d566e-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning, and maintenance.</span></span></td>
        <td><span data-ttu-id="d566e-137">Es necesario algún aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="d566e-137">Some learning required.</span></span> <span data-ttu-id="d566e-138">Si las manos no están disponibles, el dispositivo encaja bien con el lenguaje natural y la voz.</span><span class="sxs-lookup"><span data-stu-id="d566e-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="d566e-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d566e-139">HoloLens 2</span></span><br><span data-ttu-id="d566e-140">HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="d566e-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="d566e-141">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="d566e-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d566e-142"><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="d566e-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="d566e-143">Experiencias mediante clic; por ejemplo, presentaciones 3D, demostraciones.</span><span class="sxs-lookup"><span data-stu-id="d566e-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="d566e-144">Requiere aprender HMD pero no en dispositivos móviles.</span><span class="sxs-lookup"><span data-stu-id="d566e-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="d566e-145">Recomendado para controladores accesibles.</span><span class="sxs-lookup"><span data-stu-id="d566e-145">Best for accessible controllers.</span></span> <span data-ttu-id="d566e-146">Recomendado para HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="d566e-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="d566e-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d566e-147">HoloLens 2</span></span><br><span data-ttu-id="d566e-148">HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="d566e-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="d566e-149">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="d566e-149">Immersive headsets</span></span><br><span data-ttu-id="d566e-150">Realidad aumentada en dispositivos móviles</span><span class="sxs-lookup"><span data-stu-id="d566e-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="d566e-151">Para asegurarse de que no haya espacios ni huecos en la experiencia de interacción del usuario, lo mejor es seguir las instrucciones de un único modelo de principio a fin.</span><span class="sxs-lookup"><span data-stu-id="d566e-151">To ensure that there are no gaps or holes in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="d566e-152">Para acelerar el diseño y el desarrollo, hemos incluido información detallada y vínculos a ejemplos de código e imágenes dentro de la explicación de cada modelo.</span><span class="sxs-lookup"><span data-stu-id="d566e-152">To speed up design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="d566e-153">En las secciones siguientes se describen los pasos para seleccionar e implementar uno de estos modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="d566e-153">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="d566e-154">Al final de esta página, encontrarás información para:</span><span class="sxs-lookup"><span data-stu-id="d566e-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="d566e-155">Elegir un modelo de interacción para los clientes.</span><span class="sxs-lookup"><span data-stu-id="d566e-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="d566e-156">Utilizar la guía del modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="d566e-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="d566e-157">Realizar la transición entre distintos modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="d566e-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="d566e-158">Diseñar los pasos siguientes.</span><span class="sxs-lookup"><span data-stu-id="d566e-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="d566e-159">Elección de un modelo de interacción para los clientes</span><span class="sxs-lookup"><span data-stu-id="d566e-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="d566e-160">Normalmente, los desarrolladores y creadores han considerado los tipos de interacciones que pueden tener sus clientes.</span><span class="sxs-lookup"><span data-stu-id="d566e-160">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="d566e-161">Para fomentar un enfoque centrado en el cliente durante el diseño, se recomienda seguir estas instrucciones para seleccionar el modelo de interacción optimizado para el cliente.</span><span class="sxs-lookup"><span data-stu-id="d566e-161">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="d566e-162">¿Por qué seguir esta guía?</span><span class="sxs-lookup"><span data-stu-id="d566e-162">Why follow this guidance?</span></span>

* <span data-ttu-id="d566e-163">Los modelos de interacción se han probado con criterios objetivos y subjetivos, como el esfuerzo físico y cognitivo, la capacidad intuitiva y la facilidad de aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="d566e-163">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="d566e-164">Dado que las interacciones son diferentes, las prestaciones visuales y auditivas, y el comportamiento de los objetos también pueden diferir entre los modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="d566e-164">Because interactions differ, visual and audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="d566e-165">La combinación de elementos de varios modelos de interacción crea el riesgo de competencia entre las prestaciones, por ejemplo, haces de mano y un cursor de la mirada con la cabeza simultáneos, que pueden sobrecargar y confundir a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="d566e-165">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor that can overwhelm and confuse users.</span></span>

<span data-ttu-id="d566e-166">Estos son algunos ejemplos de cómo se optimizan las prestaciones y los comportamientos para cada modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="d566e-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="d566e-167">Con frecuencia vemos que los nuevos usuarios tienen preguntas similares, tales como "¿cómo sé que el sistema funciona?, ¿cómo sé lo que puedo hacer? y ¿cómo sé si se entiende lo que acabo de hacer?".</span><span class="sxs-lookup"><span data-stu-id="d566e-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d566e-168"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="d566e-169"><strong>¿Cómo sé que funciona?</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="d566e-170"><strong>¿Cómo sé qué puedo hacer?</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="d566e-171"><strong>¿Cómo sé qué acabo de hacer?</strong></span><span class="sxs-lookup"><span data-stu-id="d566e-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d566e-172"><a href="hands-and-tools.md">Controladores de movimiento y manos</a></span><span class="sxs-lookup"><span data-stu-id="d566e-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="d566e-173">Veo una malla de mano, una prestación de dedo o haces de mano o controlador.</span><span class="sxs-lookup"><span data-stu-id="d566e-173">I see a hand mesh, I see a fingertip affordance or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="d566e-174">Veo manipuladores que se pueden agarrar o aparece un rectángulo de selección cuando mi mano está cerca.</span><span class="sxs-lookup"><span data-stu-id="d566e-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="d566e-175">Puedo oír tonos audibles y ver animaciones al agarrar y soltar.</span><span class="sxs-lookup"><span data-stu-id="d566e-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d566e-176"><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="d566e-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="d566e-177">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="d566e-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="d566e-178">El cursor de la mirada con la cabeza cambia de estado cuando se encuentra sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="d566e-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="d566e-179">Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="d566e-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="d566e-180"><a href="hands-free.md">Manos libres (mirada con la cabeza y permanencia)</a></span><span class="sxs-lookup"><span data-stu-id="d566e-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="d566e-181">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="d566e-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="d566e-182">Veo un indicador de progreso al detenerme en un objeto con el que se puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="d566e-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="d566e-183">Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="d566e-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d566e-184"><a href="hands-free.md">Manos libres (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="d566e-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="d566e-185">Veo un indicador de escucha y leyendas que muestran lo que ha oído el sistema.</span><span class="sxs-lookup"><span data-stu-id="d566e-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="d566e-186">Recibo mensajes de voz y sugerencias.</span><span class="sxs-lookup"><span data-stu-id="d566e-186">I get voice prompts and hints.</span></span> <span data-ttu-id="d566e-187">Cuando digo: "¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="d566e-187">When I say: "what can I say?"</span></span> <span data-ttu-id="d566e-188">Veo comentarios.</span><span class="sxs-lookup"><span data-stu-id="d566e-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="d566e-189">Veo u oigo confirmaciones visuales y auditivas cuando emito un comando u obtengo una experiencia de usuario de desambiguación cuando es necesario.</span><span class="sxs-lookup"><span data-stu-id="d566e-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="d566e-190">A continuación se muestran las preguntas que pueden ayudar a los equipos a seleccionar un modelo de interacción:</span><span class="sxs-lookup"><span data-stu-id="d566e-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="d566e-191">Q:  ¿Los usuarios quieren tocar hologramas y realizar manipulaciones holográficas de precisión?</span><span class="sxs-lookup"><span data-stu-id="d566e-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="d566e-192">R:  Si es así, consulta el modelo de interacción de manos y controladores de movimiento para establecer los objetivos y manipular con precisión usando las manos o los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="d566e-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="d566e-193">Q:  ¿Los usuarios necesitan tener las manos libres para sus tareas en el mundo real?</span><span class="sxs-lookup"><span data-stu-id="d566e-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="d566e-194">R:  Si es así, consulta el modelo de interacción de manos libres, que proporciona una gran experiencia mediante interacciones basadas en la mirada y la voz.</span><span class="sxs-lookup"><span data-stu-id="d566e-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="d566e-195">Q:  ¿Los usuarios tienen tiempo para aprender las interacciones de la aplicación de MR o necesitan interacciones con la curva de aprendizaje más corta posible?</span><span class="sxs-lookup"><span data-stu-id="d566e-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="d566e-196">R:  Se recomienda el modelo de manos y controladores de movimiento, con una curva de aprendizaje más corta e interacciones más intuitivas, siempre y cuando los usuarios puedan usar sus manos para la interacción.</span><span class="sxs-lookup"><span data-stu-id="d566e-196">A:  We recommend the Hands and motion controllers model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="d566e-197">Q:  ¿Los usuarios utilizan controladores de movimiento para apuntar y manipular?</span><span class="sxs-lookup"><span data-stu-id="d566e-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="d566e-198">R:  El modelo de manos y controladores de movimiento incluye instrucciones completas para crear una gran experiencia con controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="d566e-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="d566e-199">Q:  ¿Los usuarios utilizan un controlador de accesibilidad o un controlador Bluetooth común, como un dispositivo de clic?</span><span class="sxs-lookup"><span data-stu-id="d566e-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="d566e-200">R:  Se recomienda el modelo de mirada con la cabeza y confirmación para todos los controladores sin seguimiento.</span><span class="sxs-lookup"><span data-stu-id="d566e-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="d566e-201">Se ha diseñado para que los usuarios puedan recorrer una experiencia completa con un sencillo mecanismo de "establecer destino y confirmar".</span><span class="sxs-lookup"><span data-stu-id="d566e-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="d566e-202">Q: ¿Los usuarios recorren una experiencia simplemente haciendo clic (por ejemplo, en un entorno similar a una presentación de diapositivas en 3D) en lugar de navegar por diseños densos de controles de interfaz de usuario?</span><span class="sxs-lookup"><span data-stu-id="d566e-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="d566e-203">R:  Si los usuarios no necesitan controlar una gran cantidad de elementos de interfaz de usuario, el modelo de mirada con la cabeza y confirmación es una opción fácil de aprender, en la que los usuarios no tienen que preocuparse sobre cómo establecer un destino.</span><span class="sxs-lookup"><span data-stu-id="d566e-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="d566e-204">Q:  ¿Los usuarios usan cascos envolventes tanto HoloLens (1.ª generación) como HoloLens 2 o Windows Mixed Reality (VR)?</span><span class="sxs-lookup"><span data-stu-id="d566e-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="d566e-205">R:  Mirada con la cabeza y confirmación es el modelo de interacción para HoloLens (1.ª generación), por lo que se recomienda que los creadores que admiten HoloLens (1.ª generación) usen la mirada con la cabeza y confirmación para todas las características o modos que los usuarios pueden experimentar con los cascos HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="d566e-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="d566e-206">Consulta la sección siguiente sobre la *transición de los modelos de interacción* para más información acerca de cómo crear una gran experiencia para varias generaciones de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d566e-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="d566e-207">Q: ¿Qué sucede con los usuarios que son generalmente móviles abarcan un amplio espacio o se mueven entre espacios, frente a los usuarios que tienden a funcionar en un único espacio?</span><span class="sxs-lookup"><span data-stu-id="d566e-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="d566e-208">R:  Cualquiera de los modelos de interacción funcionará para estos usuarios.</span><span class="sxs-lookup"><span data-stu-id="d566e-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="d566e-209">[Próximamente](index.md#news-and-notes) habrá disponible más información específica para el diseño de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d566e-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="d566e-210">Transición de los modelos de interacción</span><span class="sxs-lookup"><span data-stu-id="d566e-210">Transitioning interaction models</span></span>
<span data-ttu-id="d566e-211">También hay casos de uso en los que puede ser necesario usar más de un modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="d566e-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="d566e-212">Por ejemplo, el flujo de creación de la aplicación utiliza el modelo de interacción de manos y controladores de movimiento, pero quieres utilizar un modo de manos libres para los técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="d566e-212">For example, your application's creation flow utilizes the Hands and motion controllers interaction model, but you want to employ a hands-free mode for field technicians.</span></span>  

<span data-ttu-id="d566e-213">Si la experiencia requiere varios modelos de interacción, ten en cuenta que muchos usuarios finales pueden encontrar dificultades para realizar la transición de un modelo a otro, especialmente los usuarios que no están familiarizados con la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d566e-213">If your experience does require multiple interaction models, keep in mind that many end users might encounter difficulty when transitioning from one model to another--especially for users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="d566e-214">Trabajamos constantemente en nuevas instrucciones que estarán disponibles para los desarrolladores y diseñadores, para informarles sobre cómo, cuándo y por qué usar varios modelos de interacción de MR.</span><span class="sxs-lookup"><span data-stu-id="d566e-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="d566e-215">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d566e-215">See also</span></span>
* [<span data-ttu-id="d566e-216">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="d566e-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d566e-217">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="d566e-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="d566e-218">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="d566e-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d566e-219">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="d566e-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="d566e-220">Gestos</span><span class="sxs-lookup"><span data-stu-id="d566e-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d566e-221">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="d566e-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="d566e-222">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="d566e-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="d566e-223">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="d566e-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="d566e-224">Diseño de asignaciones espaciales</span><span class="sxs-lookup"><span data-stu-id="d566e-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="d566e-225">Comodidad</span><span class="sxs-lookup"><span data-stu-id="d566e-225">Comfort</span></span>](comfort.md)

