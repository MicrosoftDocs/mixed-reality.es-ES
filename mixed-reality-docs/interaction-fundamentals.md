---
title: Información general de la interacción multimodal
description: Información general de la interacción multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Diseñar la realidad, mirada, mirada como destino, interacción, mixta
ms.openlocfilehash: f52a0cd8ec53bfe0f4c5da2c054c538eda1c93ca
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993599"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="e0f56-104">Introducción a las interacciones instinctual</span><span class="sxs-lookup"><span data-stu-id="e0f56-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="e0f56-105">La filosofía de interacciones simple, instinctual es integrando a través de la plataforma Microsoft Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="e0f56-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="e0f56-106">Hemos tomado tres pasos para asegurarse de que los desarrolladores y diseñadores de aplicaciones pueden proporcionar interacciones sencillas e intuitivas para sus clientes.</span><span class="sxs-lookup"><span data-stu-id="e0f56-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="e0f56-107">En primer lugar, nos hemos asegurado de que nuestras increíbles sensores y la tecnología de entrada, incluida la mano de seguimiento, seguimiento de los ojos y lenguaje natural, combinan en los modelos de interacción multimodal perfecta.</span><span class="sxs-lookup"><span data-stu-id="e0f56-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="e0f56-108">Según nuestras investigaciones, diseño y desarrollo multimodally--y no según unas entradas únicas; es la clave para crear experiencias instinctual.</span><span class="sxs-lookup"><span data-stu-id="e0f56-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="e0f56-109">En segundo lugar, somos conscientes de que muchos desarrolladores tener como destino varios dispositivos, si eso significa el 2 de HoloLens y HoloLens (gen 1) o HoloLens y VR.</span><span class="sxs-lookup"><span data-stu-id="e0f56-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="e0f56-110">Por lo que hemos diseñado nuestros modelos de interacción para que funcione en todos los dispositivos (incluso si la tecnología de entrada varía en cada dispositivo).</span><span class="sxs-lookup"><span data-stu-id="e0f56-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="e0f56-111">Por ejemplo, lejano interacción en auriculares envolventes de Windows con un controlador 6GDL e interacción lejos de un 2 HoloLens ambos usar las prestaciones idénticos y los patrones, facilitando el proceso para las aplicaciones entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e0f56-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="e0f56-112">No sólo es este práctico para los desarrolladores y diseñadores, pero se siente más cómodo a los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="e0f56-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="e0f56-113">Por último, aunque reconocemos que existen miles de efectivo, atractivas y mágicos interacciones posibles en MR, hemos descubierto que intencionadamente que emplean un modelo de interacción único extremo a extremo en una aplicación es la mejor manera de asegurarse de que los usuarios son correctas y tiene una gran experiencia.</span><span class="sxs-lookup"><span data-stu-id="e0f56-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="e0f56-114">Para ello, hemos incluido tres cosas en esta guía de interacción:</span><span class="sxs-lookup"><span data-stu-id="e0f56-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="e0f56-115">Nos hemos estructurado esta orientación acerca de los tres modelos de interacción principal y los componentes y patrones para cada uno</span><span class="sxs-lookup"><span data-stu-id="e0f56-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="e0f56-116">Hemos incluido orientación complementaria en otras ventajas que ofrece nuestra plataforma.</span><span class="sxs-lookup"><span data-stu-id="e0f56-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="e0f56-117">Hemos incluido orientación para ayudarle a seleccionar el modelo de interacción adecuado para su escenario</span><span class="sxs-lookup"><span data-stu-id="e0f56-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="e0f56-118">Tres modelos de interacción multimodal</span><span class="sxs-lookup"><span data-stu-id="e0f56-118">Three multimodal interaction models</span></span>
<span data-ttu-id="e0f56-119">Según nuestras investigaciones y trabajar con clientes hasta la fecha, hemos descubierto que tres modelos de interacción principal que se adapte a la mayoría de las experiencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="e0f56-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="e0f56-120">En muchos sentidos, el modelo de interacción es el modelo mental del usuario para completar sus flujos.</span><span class="sxs-lookup"><span data-stu-id="e0f56-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="e0f56-121">Cada uno de estos modelos de interacción se optimiza para un conjunto de necesidades del cliente y cada uno es utilizable por derecho propio, eficaz y conveniente.</span><span class="sxs-lookup"><span data-stu-id="e0f56-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="e0f56-122">El gráfico siguiente es una introducción simplificada.</span><span class="sxs-lookup"><span data-stu-id="e0f56-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="e0f56-123">Información detallada sobre el uso de cada modelo de interacción está vinculada a las páginas siguientes con imágenes y ejemplos de código.</span><span class="sxs-lookup"><span data-stu-id="e0f56-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e0f56-124"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="e0f56-125"><strong>Escenarios de ejemplo</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="e0f56-126"><strong>Fit</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="e0f56-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e0f56-128"><a href="hands-and-tools.md">Las manos y herramientas</a></span><span class="sxs-lookup"><span data-stu-id="e0f56-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="e0f56-129">Experiencias espaciales en 3D</span><span class="sxs-lookup"><span data-stu-id="e0f56-129">3D spatial experiences</span></span><br><span data-ttu-id="e0f56-130">Por ejemplo, diseño espacial y diseño, manipulación de contenido o simulación</span><span class="sxs-lookup"><span data-stu-id="e0f56-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="e0f56-131">Ideal para nuevos usuarios</span><span class="sxs-lookup"><span data-stu-id="e0f56-131">Great for new users</span></span><br><span data-ttu-id="e0f56-132">Curva de aprendizaje reducida</span><span class="sxs-lookup"><span data-stu-id="e0f56-132">Low learning curve</span></span><br><span data-ttu-id="e0f56-133">Conexión a tierra en factibilidad visual fácil</span><span class="sxs-lookup"><span data-stu-id="e0f56-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="e0f56-134">Experiencia de usuario coherente a través de la mano de seguimiento y controladores GDL 6</span><span class="sxs-lookup"><span data-stu-id="e0f56-134">Consistent UX across hand tracking and 6 DoF controllers</span></span><br><span data-ttu-id="e0f56-135">Excelente cuando se combina con la voz, seguimiento de los ojos o head que mirar</span><span class="sxs-lookup"><span data-stu-id="e0f56-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="e0f56-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e0f56-136">HoloLens 2</span></span><br><span data-ttu-id="e0f56-137">Envolventes con 6GDL controladores de Windows</span><span class="sxs-lookup"><span data-stu-id="e0f56-137">Windows Immersive w/ 6DOF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e0f56-138"><a href="hands-free.md">Hands-free</a></span><span class="sxs-lookup"><span data-stu-id="e0f56-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="e0f56-139">Experiencias contextuales donde están ocupadas, por ejemplo, las manos de un usuario en el trabajo de aprendizaje, mantenimiento</span><span class="sxs-lookup"><span data-stu-id="e0f56-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="e0f56-140">Algunos de aprendizaje necesarios</span><span class="sxs-lookup"><span data-stu-id="e0f56-140">Some learning required</span></span><br><span data-ttu-id="e0f56-141">Si no están disponibles las manos</span><span class="sxs-lookup"><span data-stu-id="e0f56-141">If hands are unavailable</span></span><br><span data-ttu-id="e0f56-142">pares de bien con lenguaje natural y voz</span><span class="sxs-lookup"><span data-stu-id="e0f56-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="e0f56-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e0f56-143">HoloLens 2</span></span><br><span data-ttu-id="e0f56-144">HoloLens (gen 1)</span><span class="sxs-lookup"><span data-stu-id="e0f56-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="e0f56-145">Envolventes de Windows</span><span class="sxs-lookup"><span data-stu-id="e0f56-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e0f56-146"><a href="gaze-and-commit.md">Mirada de encabezado y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="e0f56-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="e0f56-147">Por ejemplo, 3D presentaciones, demostraciones de experiencias de Click-through</span><span class="sxs-lookup"><span data-stu-id="e0f56-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="e0f56-148">Requiere recursos de aprendizaje en HMDs pero no en dispositivos móviles</span><span class="sxs-lookup"><span data-stu-id="e0f56-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="e0f56-149">Lo mejor para los controladores accesible</span><span class="sxs-lookup"><span data-stu-id="e0f56-149">Best for accessible controllers</span></span><br><span data-ttu-id="e0f56-150">Lo mejor para HoloLens (gen 1)</span><span class="sxs-lookup"><span data-stu-id="e0f56-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="e0f56-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e0f56-151">HoloLens 2</span></span><br><span data-ttu-id="e0f56-152">HoloLens (gen 1)</span><span class="sxs-lookup"><span data-stu-id="e0f56-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="e0f56-153">Envolventes de Windows</span><span class="sxs-lookup"><span data-stu-id="e0f56-153">Windows Immersive</span></span><br> <span data-ttu-id="e0f56-154">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="e0f56-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="e0f56-155">La mejor manera de asegurarse de que no hay espacios ni los huecos en la interacción de su experiencia es seguir las instrucciones para un único modelo de principio a fin.</span><span class="sxs-lookup"><span data-stu-id="e0f56-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="e0f56-156">Para acelerar el desarrollo y diseño, hemos incluido información detallada y vínculos a ejemplos de código y las imágenes dentro de nuestra cobertura de cada modelo.</span><span class="sxs-lookup"><span data-stu-id="e0f56-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="e0f56-157">Pero en primer lugar, siga los pasos de selección y de implementación de uno de estos modelos de interacción en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="e0f56-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="e0f56-158">Al final de esta página, comprenderá nuestras instrucciones en:</span><span class="sxs-lookup"><span data-stu-id="e0f56-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="e0f56-159">Elegir un modelo de interacción para sus clientes</span><span class="sxs-lookup"><span data-stu-id="e0f56-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="e0f56-160">Mediante las instrucciones del modelo de interacción</span><span class="sxs-lookup"><span data-stu-id="e0f56-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="e0f56-161">Realizar la transición entre los modelos de interacción</span><span class="sxs-lookup"><span data-stu-id="e0f56-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="e0f56-162">Pasos de diseño</span><span class="sxs-lookup"><span data-stu-id="e0f56-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="e0f56-163">Elegir un modelo de interacción para sus clientes</span><span class="sxs-lookup"><span data-stu-id="e0f56-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="e0f56-164">Probablemente, los desarrolladores y creadores ya tienen algunas ideas en mente de los tipos de la experiencia de interacción que deseen para sus usuarios.</span><span class="sxs-lookup"><span data-stu-id="e0f56-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="e0f56-165">Para fomentar un enfoque centrado en el cliente para diseñar, se recomienda seguir las instrucciones siguientes para seleccionar el modelo de interacción que está optimizado para su cliente.</span><span class="sxs-lookup"><span data-stu-id="e0f56-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="e0f56-166">¿Por qué seguir esta guía?</span><span class="sxs-lookup"><span data-stu-id="e0f56-166">Why follow this guidance?</span></span>

* <span data-ttu-id="e0f56-167">Los modelos de interacción se prueban para objetiva y subjetivos criterios como el esfuerzo físico y cognitiva, intuitiveness y learnability.</span><span class="sxs-lookup"><span data-stu-id="e0f56-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="e0f56-168">Dado que es diferente de interacción, visual y prestaciones de audio y el comportamiento de los objetos también pueden diferir entre los modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="e0f56-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="e0f56-169">Combinar elementos de varios modelos de interacción, crea el riesgo de factibilidad competencia, como los rayos mano simultáneos y un cursor mirada, que sobrecargar y confundir a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="e0f56-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="e0f56-170">Estos son algunos ejemplos de cómo se optimizan factibilidad y comportamientos para cada modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="e0f56-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="e0f56-171">Con frecuencia vemos nuevos usuarios como preguntas similares, como "¿cómo se puede saber el sistema funciona, ¿cómo puedo saber lo que puedo hacer, y cómo saber si entiende lo que hice?"</span><span class="sxs-lookup"><span data-stu-id="e0f56-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e0f56-172"><strong>Modelo</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="e0f56-173"><strong>¿Cómo puede saber funciona?</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="e0f56-174"><strong>¿Cómo puedo saber qué puedo hacer?</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-174"><strong>How do I know what can I do?</strong></span></span></td>
        <td><span data-ttu-id="e0f56-175"><strong>¿Cómo se puede saber lo que hice?</strong></span><span class="sxs-lookup"><span data-stu-id="e0f56-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e0f56-176"><a href="hands-and-tools.md">Las manos y herramientas</a></span><span class="sxs-lookup"><span data-stu-id="e0f56-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="e0f56-177">Veo una mano de malla, se ve una prestación de la yema del dedo o mano / rayos de controlador.</span><span class="sxs-lookup"><span data-stu-id="e0f56-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="e0f56-178">Veo un rectángulo de selección aparecen cuando mi mano está cerca o identificadores grabbable.</span><span class="sxs-lookup"><span data-stu-id="e0f56-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="e0f56-179">Puedo oír tonos audibles y ver animaciones en la captura y liberación.</span><span class="sxs-lookup"><span data-stu-id="e0f56-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e0f56-180"><a href="gaze-and-commit.md">Mirada de encabezado y confirmación</a></span><span class="sxs-lookup"><span data-stu-id="e0f56-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="e0f56-181">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="e0f56-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="e0f56-182">El cursor mirada cambia el estado cuando se encuentre sobre determinados objetos.</span><span class="sxs-lookup"><span data-stu-id="e0f56-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="e0f56-183">Puedo ver o escuchar visuales y audibles confirmaciones al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="e0f56-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="e0f56-184"><a href="hands-free.md">Manos libres (mirada y permanencia)</a></span><span class="sxs-lookup"><span data-stu-id="e0f56-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="e0f56-185">Veo un cursor en el centro de mi campo de visión.</span><span class="sxs-lookup"><span data-stu-id="e0f56-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="e0f56-186">Veo un indicador de progreso cuando hincapié en un objeto interactuable.</span><span class="sxs-lookup"><span data-stu-id="e0f56-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="e0f56-187">Puedo ver o escuchar visuales y audibles confirmaciones al realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="e0f56-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e0f56-188"><a href="hands-free.md">Manos libres (comandos de voz)</a></span><span class="sxs-lookup"><span data-stu-id="e0f56-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="e0f56-189">Veo un indicador de escuchando y las leyendas que muestran lo que escucha el sistema.</span><span class="sxs-lookup"><span data-stu-id="e0f56-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="e0f56-190">Recibo mensajes de voz y sugerencias.</span><span class="sxs-lookup"><span data-stu-id="e0f56-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="e0f56-191">Cuando digo "¿Qué puedo decir?"</span><span class="sxs-lookup"><span data-stu-id="e0f56-191">When I say "what can I say?"</span></span> <span data-ttu-id="e0f56-192">Puedo ver comentarios.</span><span class="sxs-lookup"><span data-stu-id="e0f56-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="e0f56-193">Puedo ver o escuchar visuales y audibles confirmaciones cuando asigne a un comando u obtener desambiguación UX cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="e0f56-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="e0f56-194">A continuación se muestran las preguntas que hemos encontrado ayuda equipos seleccione un modelo de interacción:</span><span class="sxs-lookup"><span data-stu-id="e0f56-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="e0f56-195">Q:  ¿Mis usuarios quieren tocar hologramas y realizar manipulaciones holográfica precisión?</span><span class="sxs-lookup"><span data-stu-id="e0f56-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="e0f56-196">R:  Si es así, consulte el modelo de interacción de las manos y herramientas para la manipulación con manos o los controladores de movimiento y destinatarios de la precisión.</span><span class="sxs-lookup"><span data-stu-id="e0f56-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="e0f56-197">Q:  ¿Es necesario mantener sus manos libres para las tareas reales Mis usuarios?</span><span class="sxs-lookup"><span data-stu-id="e0f56-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="e0f56-198">R:  Si es así, eche un vistazo en el modelo de interacción de manos libres, que proporciona una gran experiencia a través de las interacciones basadas en voz y mirada manos libres.</span><span class="sxs-lookup"><span data-stu-id="e0f56-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="e0f56-199">Q:  ¿Mis usuarios tienen tiempo para obtener información sobre las interacciones para mi aplicación de realidad mixta, o necesitan las interacciones con la curva de aprendizaje más bajo posible?</span><span class="sxs-lookup"><span data-stu-id="e0f56-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="e0f56-200">R:  Se recomienda el modelo de manos y las herramientas de la curva de aprendizaje más bajo e interacciones más intuitivas, siempre y cuando los usuarios pueden usar sus manos para la interacción.</span><span class="sxs-lookup"><span data-stu-id="e0f56-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="e0f56-201">Q:  ¿Mis usuarios utilizan los controladores de movimiento para señalar y manipulación?</span><span class="sxs-lookup"><span data-stu-id="e0f56-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="e0f56-202">R:  El modelo de las manos e incluye todas las instrucciones para una gran experiencia con los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="e0f56-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="e0f56-203">Q:  ¿Mis usuarios usar un controlador de accesibilidad o un controlador de Bluetooth comunes, como un clicker?</span><span class="sxs-lookup"><span data-stu-id="e0f56-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="e0f56-204">R:  Se recomienda el modelo mirada de encabezado y confirmación para todos los controladores no realiza un seguimiento.</span><span class="sxs-lookup"><span data-stu-id="e0f56-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="e0f56-205">Se ha diseñado para permitir que un usuario recorrer una experiencia completa con un simple mecánico "de destino y de confirmación".</span><span class="sxs-lookup"><span data-stu-id="e0f56-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="e0f56-206">Q: ¿Mis usuarios solo de progreso a través de una experiencia haciendo clic en"a través de" (por ejemplo, en un entorno como presentación de diapositivas 3d), en lugar de navegar por los diseños densos de los controles de interfaz de usuario?</span><span class="sxs-lookup"><span data-stu-id="e0f56-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="e0f56-207">R:  Si los usuarios no necesitan controlar una gran cantidad de interfaz de usuario, Head mirada y confirmación ofrece una opción fácil de aprender, donde los usuarios no tienen que preocuparse sobre cómo destinar.</span><span class="sxs-lookup"><span data-stu-id="e0f56-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="e0f56-208">Q:  ¿Mis usuarios usa ambos HoloLens (gen 1) y HoloLens 2 / r: envolventes de Windows (auriculares de realidad virtual)  Puesto que la mirada de encabezado y confirmación es el modelo de interacción para HoloLens (gen 1), se recomienda que creadores de admiten HoloLens (gen 1) use Head mirada y la confirmación de características o modos que pueden experimentar los usuarios en un HoloLens (gen 1) auriculares.</span><span class="sxs-lookup"><span data-stu-id="e0f56-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="e0f56-209">Consulte la sección siguiente a continuación en *transición de modelos de interacción* para obtener más información acerca de cómo realizar una gran experiencia para varias generaciones de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e0f56-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="e0f56-210">Q: ¿Qué sucede a los usuarios que son generalmente móviles (que abarcan un amplio espacio o mover entre espacios), frente a los usuarios que tienden a funcionar en un único espacio?</span><span class="sxs-lookup"><span data-stu-id="e0f56-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="e0f56-211">R:  Cualquiera de los modelos de interacción funcionará para estos usuarios.</span><span class="sxs-lookup"><span data-stu-id="e0f56-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="e0f56-212">Obtener información más específica de diseño de aplicaciones [próximamente](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="e0f56-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="e0f56-213">Modelos de interacción de transición</span><span class="sxs-lookup"><span data-stu-id="e0f56-213">Transition interaction models</span></span>
<span data-ttu-id="e0f56-214">También hay casos donde los casos de uso pueden requerir que el uso de más de un modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="e0f56-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="e0f56-215">Por ejemplo, "flujo de creación" de la aplicación utiliza el modelo de interacción de las manos y las herramientas, pero desea emplear un modo manos libres para los técnicos de campo.</span><span class="sxs-lookup"><span data-stu-id="e0f56-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="e0f56-216">Si su experiencia requieren varios modelos de interacción, hemos visto que muchos usuarios finales pueden encontrar dificultades para realizar la transición de un modelo a otro, especialmente los usuarios finales que está familiarizados con el Sr.</span><span class="sxs-lookup"><span data-stu-id="e0f56-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="e0f56-217">Para ayudar a los diseñadores de guía y los desarrolladores a través de las opciones que pueden ser difíciles en MR, estamos trabajando en obtener más instrucciones para usar varios modelos de interacción.</span><span class="sxs-lookup"><span data-stu-id="e0f56-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="e0f56-218">Vea también</span><span class="sxs-lookup"><span data-stu-id="e0f56-218">See also</span></span>
* [<span data-ttu-id="e0f56-219">Mirada de encabezado y confirmación</span><span class="sxs-lookup"><span data-stu-id="e0f56-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e0f56-220">Manipulación directa</span><span class="sxs-lookup"><span data-stu-id="e0f56-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e0f56-221">Punto y confirmación</span><span class="sxs-lookup"><span data-stu-id="e0f56-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e0f56-222">Selección de destinos de la mirada</span><span class="sxs-lookup"><span data-stu-id="e0f56-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="e0f56-223">Gestos</span><span class="sxs-lookup"><span data-stu-id="e0f56-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="e0f56-224">Diseño de la voz</span><span class="sxs-lookup"><span data-stu-id="e0f56-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="e0f56-225">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="e0f56-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="e0f56-226">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="e0f56-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="e0f56-227">Diseño de asignaciones espaciales</span><span class="sxs-lookup"><span data-stu-id="e0f56-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="e0f56-228">Comodidad</span><span class="sxs-lookup"><span data-stu-id="e0f56-228">Comfort</span></span>](comfort.md)
