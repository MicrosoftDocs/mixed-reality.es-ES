---
title: Introducción a la interacción multimodal
description: Introducción a la interacción multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hololens, MMR, multimodal
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516021"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="dcc63-104">Introducción a las interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="dcc63-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="dcc63-105">La filosofía de interacciones simples e instintivas está integrada en la plataforma Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="dcc63-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="dcc63-106">Hemos dado tres pasos para garantizar que los desarrolladores y diseñadores de aplicaciones puedan proporcionar interacciones sencillas e intuitivas para los clientes.</span><span class="sxs-lookup"><span data-stu-id="dcc63-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="dcc63-107">En primer lugar, nos hemos asegurado de que nuestros increíbles sensores y nuestra tecnología de entrada, incluidos el seguimiento de la mano, el seguimiento de los ojos y el lenguaje natural, se combinen en modelos de interacción multimodal perfecta.</span><span class="sxs-lookup"><span data-stu-id="dcc63-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="dcc63-108">Según nuestras investigaciones, el diseño y el desarrollo multimodal (no basado en entradas únicas) es la clave para crear experiencias instintivas.</span><span class="sxs-lookup"><span data-stu-id="dcc63-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="dcc63-109">En segundo lugar, somos conscientes de que muchos desarrolladores tienen como destino varios dispositivos, es decir, HoloLens 2, HoloLens (1.ª generación) u HoloLens y VR.</span><span class="sxs-lookup"><span data-stu-id="dcc63-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="dcc63-110">Por lo tanto, hemos diseñado nuestros modelos de interacción para que funcionen en todos los dispositivos (aunque la tecnología de entrada sea diferente en cada dispositivo).</span><span class="sxs-lookup"><span data-stu-id="dcc63-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="dcc63-111">Por ejemplo, la interacción lejana en los cascos envolventes de Windows con un controlador 6DOF y la interacción lejana con HoloLens 2 usan prestaciones y patrones idénticos, lo que facilita el proceso para las aplicaciones multidispositivo.</span><span class="sxs-lookup"><span data-stu-id="dcc63-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="dcc63-112">Esto no solo es práctico para desarrolladores y diseñadores, sino que los usuarios finales disfrutan de una experiencia más natural.</span><span class="sxs-lookup"><span data-stu-id="dcc63-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="dcc63-113">Por último, aunque sabemos que existen miles de interacciones posibles eficaces, atractivas y mágicas en la realidad mixta, hemos descubierto que el empleo intencionado de un modelo de interacción único de principio a fin en una aplicación es la mejor manera de asegurarse de que los usuarios vivan una gran experiencia.</span><span class="sxs-lookup"><span data-stu-id="dcc63-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="dcc63-114">Para ello, hemos incluido tres elementos en esta guía de interacción:</span><span class="sxs-lookup"><span data-stu-id="dcc63-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="dcc63-115">Hemos estructurado esta guía en torno a los tres modelos de interacción principales y los componentes y patrones necesarios para cada uno.</span><span class="sxs-lookup"><span data-stu-id="dcc63-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="dcc63-116">Hemos incluido información complementaria acerca de las demás ventajas que ofrece nuestra plataforma.</span><span class="sxs-lookup"><span data-stu-id="dcc63-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="dcc63-117">Hemos incluido información para ayudarte a seleccionar el modelo de interacción adecuado para tu escenario.</span><span class="sxs-lookup"><span data-stu-id="dcc63-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="dcc63-118">Modelos de interacción multimodal</span><span class="sxs-lookup"><span data-stu-id="dcc63-118">Multimodal interaction models</span></span>

<span data-ttu-id="dcc63-119">Según nuestras investigaciones y el trabajo con los clientes hasta la fecha, hemos descubierto que hay tres modelos de interacción principal que se adaptan a la mayoría de las experiencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="dcc63-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="dcc63-120">En muchos sentidos, el modelo de interacción es el modelo mental del usuario para completar los flujos.</span><span class="sxs-lookup"><span data-stu-id="dcc63-120">In many ways, the interaction model is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="dcc63-121">Cada uno de estos modelos de interacción está optimizado para un conjunto de necesidades del cliente y cada uno es utilizable por derecho propio, es eficaz y es conveniente.</span><span class="sxs-lookup"><span data-stu-id="dcc63-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="dcc63-122">El gráfico siguiente es una introducción simplificada.</span><span class="sxs-lookup"><span data-stu-id="dcc63-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="dcc63-123">En las páginas siguientes hay vínculos a información detallada sobre el uso de cada modelo de interacción con imágenes y ejemplos de código.</span><span class="sxs-lookup"><span data-stu-id="dcc63-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dcc63-124"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="dcc63-125"><strong>Escenarios de ejemplo</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="dcc63-126"><strong>Apto para</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="dcc63-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dcc63-128"><a href="hands-and-tools.md">Controladores de movimiento y manos</a></span><span class="sxs-lookup"><span data-stu-id="dcc63-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="dcc63-129">Experiencias espaciales en 3D, como el diseño espacial, la manipulación de contenido o la simulación.</span><span class="sxs-lookup"><span data-stu-id="dcc63-129">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="dcc63-130">Ideal para usuarios nuevos, junto con la voz, el seguimiento de los ojos o la mirada con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="dcc63-130">Great for new users, coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="dcc63-131">Curva de aprendizaje reducida.</span><span class="sxs-lookup"><span data-stu-id="dcc63-131">Low learning curve.</span></span> <span data-ttu-id="dcc63-132">Experiencia de usuario coherente en el seguimiento de la mano y controladores 6DoF.</span><span class="sxs-lookup"><span data-stu-id="dcc63-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span></td>
        <td><span data-ttu-id="dcc63-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dcc63-133">HoloLens 2</span></span><br><span data-ttu-id="dcc63-134">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="dcc63-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dcc63-135"><a href="hands-free.md">Manos libres</a></span><span class="sxs-lookup"><span data-stu-id="dcc63-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="dcc63-136">Experiencias contextuales en las que las manos de un usuario están ocupadas, por ejemplo, durante el aprendizaje de un trabajo o tareas de mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="dcc63-136">Contextual experiences where a user's hands are occupied, e.g. on-the-job learning, maintenance.</span></span></td>
        <td><span data-ttu-id="dcc63-137">Es necesario algún aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="dcc63-137">Some learning required.</span></span> <span data-ttu-id="dcc63-138">Tener las manos no disponibles encaja bien con el lenguaje natural y la voz.</span><span class="sxs-lookup"><span data-stu-id="dcc63-138">If hands are unavailable pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="dcc63-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dcc63-139">HoloLens 2</span></span><br><span data-ttu-id="dcc63-140">HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="dcc63-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="dcc63-141">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="dcc63-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dcc63-142"><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="dcc63-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="dcc63-143">Experiencias mediante clic; por ejemplo, presentaciones 3D, demostraciones.</span><span class="sxs-lookup"><span data-stu-id="dcc63-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="dcc63-144">Requiere aprender HMD pero no en dispositivos móviles.</span><span class="sxs-lookup"><span data-stu-id="dcc63-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="dcc63-145">Recomendado para controladores accesibles.</span><span class="sxs-lookup"><span data-stu-id="dcc63-145">Best for accessible controllers.</span></span> <span data-ttu-id="dcc63-146">Recomendado para HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="dcc63-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="dcc63-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="dcc63-147">HoloLens 2</span></span><br><span data-ttu-id="dcc63-148">HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="dcc63-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="dcc63-149">Cascos envolventes</span><span class="sxs-lookup"><span data-stu-id="dcc63-149">Immersive headsets</span></span><br><span data-ttu-id="dcc63-150">Realidad aumentada en dispositivos móviles</span><span class="sxs-lookup"><span data-stu-id="dcc63-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="dcc63-151">La mejor manera de asegurarse de que no haya espacios ni huecos en la interacción de la experiencia es seguir la guía de un único modelo de principio a fin.</span><span class="sxs-lookup"><span data-stu-id="dcc63-151">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="dcc63-152">Para acelerar el diseño y el desarrollo, hemos incluido información detallada y vínculos a ejemplos de código e imágenes dentro de la explicación de cada modelo.</span><span class="sxs-lookup"><span data-stu-id="dcc63-152">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="dcc63-153">Pero, en primer lugar, en las secciones siguientes se describen los pasos para seleccionar e implementar uno de estos modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-153">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="dcc63-154">Al final de esta página, encontrarás información para:</span><span class="sxs-lookup"><span data-stu-id="dcc63-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="dcc63-155">Elegir un modelo de interacción para los clientes.</span><span class="sxs-lookup"><span data-stu-id="dcc63-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="dcc63-156">Utilizar la guía del modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="dcc63-157">Realizar la transición entre distintos modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="dcc63-158">Diseñar los pasos siguientes.</span><span class="sxs-lookup"><span data-stu-id="dcc63-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="dcc63-159">Elección de un modelo de interacción para los clientes</span><span class="sxs-lookup"><span data-stu-id="dcc63-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="dcc63-160">Probablemente, los desarrolladores y creadores ya tienen algunas ideas en mente sobre los tipos de experiencia de interacción que quieren para sus usuarios.</span><span class="sxs-lookup"><span data-stu-id="dcc63-160">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="dcc63-161">Para fomentar un enfoque centrado en el cliente durante el diseño, se recomienda seguir estas instrucciones para seleccionar un modelo de interacción optimizado para el cliente.</span><span class="sxs-lookup"><span data-stu-id="dcc63-161">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="dcc63-162">¿Por qué seguir esta guía?</span><span class="sxs-lookup"><span data-stu-id="dcc63-162">Why follow this guidance?</span></span>

* <span data-ttu-id="dcc63-163">Los modelos de interacción han sido probados con criterios objetivos y subjetivos como el esfuerzo físico y cognitivo, su intuitividad y la facilidad de aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="dcc63-163">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="dcc63-164">Dado que las interacciones son diferentes, las prestaciones visuales y auditivas, y el comportamiento de los objetos también pueden diferir entre los modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-164">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="dcc63-165">Combinar elementos de varios modelos de interacción crea el riesgo de competencia entre las prestaciones, por ejemplo, rayos de las manos y un cursor de la mirada con la cabeza simultáneos, que pueden sobrecargar y confundir a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="dcc63-165">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which can overwhelm and confuse users.</span></span>

<span data-ttu-id="dcc63-166">Estos son algunos ejemplos de cómo se optimizan las prestaciones y los comportamientos para cada modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="dcc63-167">Con frecuencia vemos que los nuevos usuarios tienen preguntas similares, tales como "¿cómo sé que el sistema funciona?, ¿cómo sé lo que puedo hacer? y ¿cómo sé si se entiende lo que acabo de hacer?".</span><span class="sxs-lookup"><span data-stu-id="dcc63-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dcc63-168"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="dcc63-169"><strong>¿Cómo sé que funciona?</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="dcc63-170"><strong>¿Cómo sé qué puedo hacer?</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="dcc63-171"><strong>¿Cómo sé qué acabo de hacer?</strong></span><span class="sxs-lookup"><span data-stu-id="dcc63-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dcc63-172"><a href="hands-and-tools.md">Controladores de movimiento y manos</a></span><span class="sxs-lookup"><span data-stu-id="dcc63-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="dcc63-173">Veo una malla de mano, una prestación de dedo o rayos de mano o controlador.</span><span class="sxs-lookup"><span data-stu-id="dcc63-173">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="dcc63-174">Veo manipuladores que se pueden agarrar o aparece un rectángulo de selección cuando mi mano está cerca.</span><span class="sxs-lookup"><span data-stu-id="dcc63-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="dcc63-175">Puedo oír tonos audibles y ver animaciones al agarrar y soltar.</span><span class="sxs-lookup"><span data-stu-id="dcc63-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dcc63-176"><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="dcc63-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="dcc63-177">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="dcc63-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="dcc63-178">El cursor de la mirada con la cabeza cambia de estado cuando se encuentra sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="dcc63-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="dcc63-179">Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="dcc63-180"><a href="hands-free.md">Manos libres (mirada con la cabeza y permanencia)</a></span><span class="sxs-lookup"><span data-stu-id="dcc63-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="dcc63-181">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="dcc63-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="dcc63-182">Veo un indicador de progreso al detenerme en un objeto con el que se puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="dcc63-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="dcc63-183">Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="dcc63-184"><a href="hands-free.md">Manos libres (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="dcc63-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="dcc63-185">Veo un indicador de escucha y leyendas que muestran lo que ha oído el sistema.</span><span class="sxs-lookup"><span data-stu-id="dcc63-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="dcc63-186">Recibo mensajes de voz y sugerencias.</span><span class="sxs-lookup"><span data-stu-id="dcc63-186">I get voice prompts and hints.</span></span>  <span data-ttu-id="dcc63-187">Cuando digo "¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="dcc63-187">When I say "what can I say?"</span></span> <span data-ttu-id="dcc63-188">Veo comentarios.</span><span class="sxs-lookup"><span data-stu-id="dcc63-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="dcc63-189">Veo u oigo confirmaciones visuales y auditivas cuando emito un comando u obtengo una experiencia de usuario de desambiguación cuando es necesario.</span><span class="sxs-lookup"><span data-stu-id="dcc63-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="dcc63-190">A continuación se muestran las preguntas que pueden ayudar a los equipos a seleccionar un modelo de interacción:</span><span class="sxs-lookup"><span data-stu-id="dcc63-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="dcc63-191">Q:  ¿Los usuarios quieren tocar hologramas y realizar manipulaciones holográficas de precisión?</span><span class="sxs-lookup"><span data-stu-id="dcc63-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="dcc63-192">R:  Si es así, consulta el modelo de interacción de manos y herramientas para establecer los objetivos y manipular con precisión usando las manos o controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="dcc63-192">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="dcc63-193">Q:  ¿Los usuarios necesitan tener las manos libres para sus tareas en el mundo real?</span><span class="sxs-lookup"><span data-stu-id="dcc63-193">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="dcc63-194">R:  Si es así, consulta el modelo de interacción de manos libres, que proporciona una gran experiencia mediante interacciones basadas en la mirada y la voz.</span><span class="sxs-lookup"><span data-stu-id="dcc63-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="dcc63-195">Q:  ¿Los usuarios tienen tiempo para aprender las interacciones de la aplicación de realidad mixta o necesitan interacciones con la curva de aprendizaje más corta posible?</span><span class="sxs-lookup"><span data-stu-id="dcc63-195">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="dcc63-196">R:  Se recomienda el modelo de manos y herramientas, con una curva de aprendizaje más corta e interacciones más intuitivas, siempre y cuando los usuarios puedan usar sus manos para la interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-196">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="dcc63-197">Q:  ¿Los usuarios utilizan controladores de movimiento para apuntar y manipular?</span><span class="sxs-lookup"><span data-stu-id="dcc63-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="dcc63-198">R:  El modelo de manos y herramientas incluye instrucciones completas para crear una gran experiencia con controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="dcc63-198">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="dcc63-199">Q:  ¿Los usuarios utilizan un controlador de accesibilidad o un controlador Bluetooth común, como un dispositivo de clic?</span><span class="sxs-lookup"><span data-stu-id="dcc63-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="dcc63-200">R:  Se recomienda el modelo de mirada con la cabeza y confirmación para todos los controladores sin seguimiento.</span><span class="sxs-lookup"><span data-stu-id="dcc63-200">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="dcc63-201">Se ha diseñado para que los usuarios puedan recorrer una experiencia completa con una sencilla mecánica de "establecer destino y confirmar".</span><span class="sxs-lookup"><span data-stu-id="dcc63-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="dcc63-202">Q: ¿Los usuarios recorren una experiencia simplemente haciendo clic (por ejemplo, en un entorno similar a una presentación de diapositivas en 3D) en lugar de navegar por diseños densos de controles de interfaz de usuario?</span><span class="sxs-lookup"><span data-stu-id="dcc63-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="dcc63-203">R:  Si los usuarios no necesitan controlar una gran cantidad de elementos de interfaz de usuario, el modelo de mirada con la cabeza y confirmación es una opción fácil de aprender, en la que los usuarios no tienen que preocuparse sobre cómo establecer un destino.</span><span class="sxs-lookup"><span data-stu-id="dcc63-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="dcc63-204">Q:  ¿Los usuarios usan tanto HoloLens (1.ª generación) como HoloLens 2 o Windows Immersive (cascos de realidad virtual)?</span><span class="sxs-lookup"><span data-stu-id="dcc63-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="dcc63-205">R:  Mirada con la cabeza y confirmación es el modelo de interacción para HoloLens (1.ª generación), por lo que se recomienda que los creadores que admiten HoloLens (1.ª generación) usen la mirada con la cabeza y confirmación para todas las características o modos que los usuarios pueden experimentar con los cascos HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="dcc63-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="dcc63-206">Consulta la sección siguiente sobre la *transición de los modelos de interacción* para más información acerca de cómo crear una gran experiencia para varias generaciones de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dcc63-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="dcc63-207">Q: ¿Qué sucede con los usuarios que son generalmente móviles (abarcan un amplio espacio o se mueven entre espacios) frente a los usuarios que tienden a funcionar en un único espacio?</span><span class="sxs-lookup"><span data-stu-id="dcc63-207">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="dcc63-208">R:  Cualquiera de los modelos de interacción funcionará para estos usuarios.</span><span class="sxs-lookup"><span data-stu-id="dcc63-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="dcc63-209">[Próximamente](index.md#news-and-notes) habrá disponible más información específica para el diseño de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="dcc63-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="dcc63-210">Transición de los modelos de interacción</span><span class="sxs-lookup"><span data-stu-id="dcc63-210">Transition interaction models</span></span>
<span data-ttu-id="dcc63-211">También hay casos en los que puede ser necesario usar más de un modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-211">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="dcc63-212">Por ejemplo, el "flujo de creación" de la aplicación utiliza el modelo de interacción de manos y controladores de movimiento, pero quieres utilizar un modo de manos libres para los técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="dcc63-212">For example, your app's "creation flow" utilizes the Hands and motion controllers interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="dcc63-213">Si la experiencia requiere varios modelos de interacción, hemos visto que muchos usuarios finales pueden encontrar dificultades para realizar la transición de un modelo a otro, especialmente en usuarios no familiarizados con la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="dcc63-213">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="dcc63-214">Para ayudar a diseñadores y desarrolladores con las opciones que pueden ser difíciles en la realidad mixta, estamos elaborando más instrucciones para usar varios modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="dcc63-214">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="dcc63-215">Consulte también</span><span class="sxs-lookup"><span data-stu-id="dcc63-215">See also</span></span>
* [<span data-ttu-id="dcc63-216">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="dcc63-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="dcc63-217">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="dcc63-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="dcc63-218">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="dcc63-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dcc63-219">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="dcc63-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="dcc63-220">Gestos</span><span class="sxs-lookup"><span data-stu-id="dcc63-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="dcc63-221">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="dcc63-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="dcc63-222">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="dcc63-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="dcc63-223">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="dcc63-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="dcc63-224">Diseño de asignaciones espaciales</span><span class="sxs-lookup"><span data-stu-id="dcc63-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="dcc63-225">Comodidad</span><span class="sxs-lookup"><span data-stu-id="dcc63-225">Comfort</span></span>](comfort.md)

