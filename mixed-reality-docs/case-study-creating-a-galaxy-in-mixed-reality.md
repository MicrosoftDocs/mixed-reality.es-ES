---
title: 'Caso práctico: creación de una galaxia en realidad mixta'
description: Antes de enviar Microsoft HoloLens, pedimos a nuestra comunidad de desarrolladores a qué tipo de aplicación les gustaría ver un equipo interno con experiencia de compilación para el nuevo dispositivo. Se compartieron más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea denominada "Explorador de Galaxy".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Explorador de Galaxy, HoloLens, Windows Mixed Reality, comparta sus ideas, caso práctico
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605730"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="454a5-105">Caso práctico: creación de una galaxia en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="454a5-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="454a5-106">Antes de enviar Microsoft HoloLens, pedimos a nuestra comunidad de desarrolladores a qué tipo de aplicación les gustaría ver un equipo interno con experiencia de compilación para el nuevo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="454a5-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="454a5-107">Se compartieron más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea llamada [Explorer Galaxy](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="454a5-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="454a5-108">Andy Zibits, el responsable de material gráfico en el proyecto y Karim Luccin, ingeniero de gráficos del equipo, hablar sobre el esfuerzo de colaboración entre imágenes y de ingeniería que dieron lugar a la creación de una representación precisa interactiva de galaxy vía láctea en el Explorador de Galaxy.</span><span class="sxs-lookup"><span data-stu-id="454a5-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="454a5-109">The Tech</span><span class="sxs-lookup"><span data-stu-id="454a5-109">The Tech</span></span>

<span data-ttu-id="454a5-110">[Nuestro equipo](galaxy-explorer.md#meet-the-team) : realizar copia de dos diseñadores, tres desarrolladores, cuatro artistas, un productor y un evaluador, tenía seis semanas para compilar una aplicación totalmente funcional que le permite que la gente conozca y explore la gran amplitud y la belleza de nuestro Galaxy vía láctea.</span><span class="sxs-lookup"><span data-stu-id="454a5-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="454a5-111">Queríamos aprovechar al máximo la capacidad de representar objetos 3D directamente en su espacio vital, por lo que decidimos que queríamos crear un realista galaxy atractivo donde las personas sería capaz de acercar close y ver estrellas individuales, cada uno en sus propia trayectorias de HoloLens .</span><span class="sxs-lookup"><span data-stu-id="454a5-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="454a5-112">En la primera semana del desarrollo, dimos con unos pocos objetivos para la representación de Galaxy vía láctea: Necesita para tener profundidad, el movimiento y el funcionamiento volumétrico: completo de estrellas que ayudaría a crear la forma de galaxy.</span><span class="sxs-lookup"><span data-stu-id="454a5-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="454a5-113">El problema con la creación de un galaxy animado que tuviera miles de millones de estrellas fue que la mera cantidad de elementos únicos que requieren actualización sería demasiado grande por fotograma para HoloLens se va a animar el uso de la CPU.</span><span class="sxs-lookup"><span data-stu-id="454a5-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="454a5-114">Nuestra solución implicaba una mezcla compleja de arte y conocimientos teóricos.</span><span class="sxs-lookup"><span data-stu-id="454a5-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="454a5-115">En segundo plano</span><span class="sxs-lookup"><span data-stu-id="454a5-115">Behind the scenes</span></span>

<span data-ttu-id="454a5-116">Para permitir a los usuarios explorar estrellas individuales, nuestro primer paso fue averiguar cuántos objetos representamos podríamos a la vez.</span><span class="sxs-lookup"><span data-stu-id="454a5-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="454a5-117">Objetos de representación</span><span class="sxs-lookup"><span data-stu-id="454a5-117">Rendering particles</span></span>

<span data-ttu-id="454a5-118">CPU actuales son excelentes para procesar tareas en serie y un máximo de algunas tareas en paralelo a la vez (dependiendo de cuántos núcleos tengan), pero las GPU son mucho más eficaces para procesar miles de operaciones en paralelo.</span><span class="sxs-lookup"><span data-stu-id="454a5-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="454a5-119">Sin embargo, porque normalmente no comparten la misma memoria que la CPU, el intercambio de datos entre CPU <> GPU puede volverse rápidamente un cuello de botella.</span><span class="sxs-lookup"><span data-stu-id="454a5-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="454a5-120">Nuestra solución fue hacer que un galaxy en la GPU y tenía que residen completamente en la GPU.</span><span class="sxs-lookup"><span data-stu-id="454a5-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="454a5-121">Comenzamos a las pruebas de esfuerzo con miles de partículas de punto en varios modelos.</span><span class="sxs-lookup"><span data-stu-id="454a5-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="454a5-122">Esto nos permitió obtener galaxy en HoloLens para ver lo que funcionó y lo que no.</span><span class="sxs-lookup"><span data-stu-id="454a5-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="454a5-123">Creación de la posición de las estrellas</span><span class="sxs-lookup"><span data-stu-id="454a5-123">Creating the position of the stars</span></span>

<span data-ttu-id="454a5-124">Uno de nuestros miembros del equipo ya había desarrollado el C# código que generaría estrellas en su posición inicial.</span><span class="sxs-lookup"><span data-stu-id="454a5-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="454a5-125">Las estrellas se encuentran en una elipse y se puede describir su posición (**curveOffset**, **ellipseSize**, **elevación**) donde **curveOffset**es el ángulo de la estrella a lo largo de la elipse, **ellipseSize** es la dimensión de la elipse a lo largo de X y Z y la elevación la elevación de la estrella dentro de galaxy adecuada.</span><span class="sxs-lookup"><span data-stu-id="454a5-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="454a5-126">Por lo tanto, podemos crear un búfer ([ComputeBuffer de Unity](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que se inicializaría a cada atributo de estrella y enviarlo en la GPU donde sería definitivamente durante el resto de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="454a5-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="454a5-127">Para dibujar este búfer, usamos [DrawProcedural de Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) que permite ejecutar un sombreador (código de una GPU) en un conjunto arbitrario de puntos sin necesidad de una malla real que representa el galaxy:</span><span class="sxs-lookup"><span data-stu-id="454a5-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="454a5-128">**CPU:**</span><span class="sxs-lookup"><span data-stu-id="454a5-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="454a5-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="454a5-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="454a5-130">Comenzamos con patrones circulares sin procesar con miles de partículas.</span><span class="sxs-lookup"><span data-stu-id="454a5-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="454a5-131">Esto nos dio la prueba que necesitábamos que podríamos administrar muchos objetos y ejecutarla a velocidades de alto rendimiento, pero no se ha satisfechos con la forma general de galaxy.</span><span class="sxs-lookup"><span data-stu-id="454a5-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="454a5-132">Para mejorar la forma, hemos intentado distintos patrones y sistemas de partículas con una rotación.</span><span class="sxs-lookup"><span data-stu-id="454a5-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="454a5-133">Se trataba inicialmente prometedor porque permanecido coherente, el número de objetos y el rendimiento, pero la forma infringió cerca del centro y estaban emitiendo las estrellas aparentemente sea lo que no era realista.</span><span class="sxs-lookup"><span data-stu-id="454a5-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="454a5-134">Necesitábamos una emisión que nos permitiría manipular tiempo y que las partículas mover de manera realista, bucle cada vez más estrecha al centro de galaxy.</span><span class="sxs-lookup"><span data-stu-id="454a5-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Hemos intentado distintos patrones y sistemas de partículas que girar, como estos.](images/galaxy-patterns-500px.png)

<span data-ttu-id="454a5-136">Hemos intentado distintos patrones y sistemas de partículas que girar, como estos.</span><span class="sxs-lookup"><span data-stu-id="454a5-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="454a5-137">Nuestro equipo hizo investigar un poco acerca de la función de manera galaxias y hemos realizado un sistema de partículas personalizado específicamente para galaxy, por lo que podríamos pasar las partículas en función de un botón de puntos suspensivos "[teoría de onda de densidad](https://en.wikipedia.org/wiki/Density_wave_theory)," que theorizes que las ramas de un Galaxy son áreas de una mayor densidad pero inestable constante, como un atasco de tráfico.</span><span class="sxs-lookup"><span data-stu-id="454a5-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="454a5-138">Parece sólido y estable, pero las estrellas se mueven realmente dentro y fuera de las ramas como mueva a lo largo de sus respectivos elipses.</span><span class="sxs-lookup"><span data-stu-id="454a5-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="454a5-139">En nuestro sistema, las partículas nunca existen en la CPU, generamos las tarjetas y orientar a ellos en la GPU, por lo que todo el sistema es el estado inicial simplemente + tiempo.</span><span class="sxs-lookup"><span data-stu-id="454a5-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="454a5-140">Lo progresado similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="454a5-140">It progressed like this:</span></span>

![Progresión de sistema de partículas con la representación de GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="454a5-142">Progresión de sistema de partículas con la representación de GPU</span><span class="sxs-lookup"><span data-stu-id="454a5-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="454a5-143">Una vez suficientes puntos suspensivos se agregan y se establecen para girar, las galaxias comenzaron a formulario donde el movimiento de estrellas converger "segmentos".</span><span class="sxs-lookup"><span data-stu-id="454a5-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="454a5-144">El espaciado de las estrellas a lo largo de cada trazado elíptico recibió algo de aleatoriedad, y cada estrella tiene algo de aleatoriedad posicional agregado.</span><span class="sxs-lookup"><span data-stu-id="454a5-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="454a5-145">Esto crea una distribución de aspecto mucho más natural de la forma de estrella, movimiento y arm.</span><span class="sxs-lookup"><span data-stu-id="454a5-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="454a5-146">Por último, agregamos la capacidad al color de la unidad en función de la distancia desde el centro.</span><span class="sxs-lookup"><span data-stu-id="454a5-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="454a5-147">Crear el movimiento de las estrellas</span><span class="sxs-lookup"><span data-stu-id="454a5-147">Creating the motion of the stars</span></span>

<span data-ttu-id="454a5-148">Para animar el movimiento de estrella general, se necesita para agregar un ángulo constante para cada fotograma y obtener estrellas moverse a lo largo de los puntos suspensivos a una velocidad constante radial.</span><span class="sxs-lookup"><span data-stu-id="454a5-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="454a5-149">Esta es la razón principal para usar **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="454a5-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="454a5-150">Esto no es técnicamente correcta tal y como estrellas se moverá con mayor rapidez a los lados largo de los puntos suspensivos, pero el movimiento general consideramos buena.</span><span class="sxs-lookup"><span data-stu-id="454a5-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Estrellas más rápido pasar del arco largo, más lento en los bordes.](images/ellipse-movement.jpg)

<span data-ttu-id="454a5-152">Estrellas más rápido pasar del arco largo, más lento en los bordes.</span><span class="sxs-lookup"><span data-stu-id="454a5-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="454a5-153">Con esto, se describe detalladamente cada estrella por (**curveOffset**, **ellipseSize**, **elevación**, **Age**) donde **edad** es una acumulación del tiempo total que ha transcurrido desde que se cargó la escena.</span><span class="sxs-lookup"><span data-stu-id="454a5-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="454a5-154">Esto nos ha permitido generar decenas de miles de estrellas una vez al principio de la aplicación y, a continuación, se anima un conjunto de estrellas a lo largo de las curvas establecidas un.</span><span class="sxs-lookup"><span data-stu-id="454a5-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="454a5-155">Puesto que todo está en la GPU, el sistema puede animar todas las estrellas en paralelo sin costo a la CPU.</span><span class="sxs-lookup"><span data-stu-id="454a5-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Este es su aspecto cuando cuadrantes blancos de dibujo.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="454a5-157">Este es su aspecto cuando cuadrantes blancos de dibujo.</span><span class="sxs-lookup"><span data-stu-id="454a5-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="454a5-158">Para hacer que la cámara cada cara cuádruple, hemos usado a un sombreador de geometría para transformar cada posición estrella a un rectángulo en la pantalla que contendrá la estrella textura 2D.</span><span class="sxs-lookup"><span data-stu-id="454a5-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Diamantes en lugar de cuadrantes.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="454a5-160">Diamantes en lugar de cuadrantes.</span><span class="sxs-lookup"><span data-stu-id="454a5-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="454a5-161">Dado que quisiéramos limitar el sobredibujo (número de veces que se procesará un píxel) tanto como sea posible, se giran nuestro cuadrantes para que se tengan menos superposiciones.</span><span class="sxs-lookup"><span data-stu-id="454a5-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="454a5-162">Adición de nubes</span><span class="sxs-lookup"><span data-stu-id="454a5-162">Adding clouds</span></span>

<span data-ttu-id="454a5-163">Hay muchas maneras para hacerse una idea volumétrica con partículas — de ray marching dentro de un volumen para dibujar las partículas tantos como sea posible para simular una nube.</span><span class="sxs-lookup"><span data-stu-id="454a5-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="454a5-164">Ray en tiempo real marching iba a ser demasiado costoso y difícil de autor, así que intentamos primero la creación de un sistema impostor mediante un método de bosques de representación en juegos, con una gran cantidad de imágenes en 2D de árboles orientado a la cámara.</span><span class="sxs-lookup"><span data-stu-id="454a5-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="454a5-165">Al hacer esto en un juego, podemos tener las texturas de árboles que se procesan a partir de una cámara que gira en torno a y guarde todas esas imágenes en tiempo de ejecución para cada tarjeta cartelera, seleccione la imagen que coincide con la dirección de la vista.</span><span class="sxs-lookup"><span data-stu-id="454a5-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="454a5-166">Esto no funciona tan bien cuando las imágenes son hologramas.</span><span class="sxs-lookup"><span data-stu-id="454a5-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="454a5-167">La diferencia entre el ojo izquierdo y derecho ojo permiten que se necesita una resolución mucho mayor, o bien se ve plana, alias, o repetitivas.</span><span class="sxs-lookup"><span data-stu-id="454a5-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="454a5-168">En nuestro segundo intento, intentamos tener tantos objetos como sea posible.</span><span class="sxs-lookup"><span data-stu-id="454a5-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="454a5-169">Se obtuvieron los objetos visuales mejor cuando nos aditivamente dibujó partículas y borrosa ellos antes de agregarlos a la escena.</span><span class="sxs-lookup"><span data-stu-id="454a5-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="454a5-170">Los problemas típicos con ese enfoque eran objetos relacionados a cuántos nos podemos dibujar en una sola vez y cuánto pantalla área que cubierta manteniendo los 60fps.</span><span class="sxs-lookup"><span data-stu-id="454a5-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="454a5-171">Desenfoque de la imagen resultante para obtener esta nube se siente normalmente era una operación muy costosa.</span><span class="sxs-lookup"><span data-stu-id="454a5-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Sin la textura, esto es lo que sería las nubes con 2% de opacidad.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="454a5-173">Sin la textura, esto es lo que sería las nubes con 2% de opacidad.</span><span class="sxs-lookup"><span data-stu-id="454a5-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="454a5-174">Que se va a aditivas y tener una gran cantidad de ellos significa que se tendría varios cuadrantes encima de otro, sombreado repetidamente el mismo píxel.</span><span class="sxs-lookup"><span data-stu-id="454a5-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="454a5-175">En el centro de galaxy, el mismo píxel tiene cientos de cuadrantes uno sobre otro y esto tuvo un costo enorme cuando se realiza a pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="454a5-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="454a5-176">Realizando las nubes de pantalla completa y tratando de les desenfoque habría sido una mala idea, por lo tanto, que hemos decidido permitir que el hardware de hacer el trabajo por nosotros.</span><span class="sxs-lookup"><span data-stu-id="454a5-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="454a5-177">Un bit del contexto en primer lugar</span><span class="sxs-lookup"><span data-stu-id="454a5-177">A bit of context first</span></span>

<span data-ttu-id="454a5-178">Al usar las texturas en un juego el tamaño de la textura rara vez coincidirá con el área que deseamos utilizar en, pero podemos usar otro tipo de filtrado para obtener la tarjeta gráfica para interpolar el color que desee de los píxeles de la textura de textura ([Texture Filtering<C3/>).](https://msdn.microsoft.com/library/dn642451.aspx)</span><span class="sxs-lookup"><span data-stu-id="454a5-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="454a5-179">El filtrado que nos interesa es [filtrado bilineal](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) que va a calcular el valor de cualquier píxel con el 4 de vecinos más cercanos.</span><span class="sxs-lookup"><span data-stu-id="454a5-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Original antes de filtrado](images/texture-1.png)

![Como resultado tras el filtrado](images/texture-2.png)

<span data-ttu-id="454a5-182">Con esta propiedad, vemos que cada vez que se intente dibujar una textura a un área dos veces más grandes, se desenfoca el resultado.</span><span class="sxs-lookup"><span data-stu-id="454a5-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="454a5-183">En lugar de representación a pantalla completa y perder los milisegundos preciosos que nos podríamos emplear en algo más, representamos a una versión pequeña de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="454a5-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="454a5-184">A continuación, copiando esta textura y ajuste en un factor de 2 varias veces, obtenemos a pantalla completa mientras el contenido en el proceso de desenfoque.</span><span class="sxs-lookup"><span data-stu-id="454a5-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 exclusiva a resolución completa.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="454a5-186">x3 exclusiva a resolución completa.</span><span class="sxs-lookup"><span data-stu-id="454a5-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="454a5-187">Esto nos permitió obtener la parte de la nube con sólo una fracción del costo original.</span><span class="sxs-lookup"><span data-stu-id="454a5-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="454a5-188">En lugar de agregar nubes en la resolución por completa, solo se paint 1/64 de los píxeles y tan solo ajustar la textura a resolución completa.</span><span class="sxs-lookup"><span data-stu-id="454a5-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Izquierda, con un lujoso de 1/8 a resolución completa; y, con 3 exclusiva con la potencia de 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="454a5-190">Izquierda, con un lujoso de 1/8 a resolución completa; y, con 3 exclusiva con la potencia de 2.</span><span class="sxs-lookup"><span data-stu-id="454a5-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="454a5-191">Tenga en cuenta que intenta ir de 1/64 del tamaño al máximo tamaño en una sola operación tendría el aspecto completamente diferente, como la tarjeta gráfica seguiría usando 4 píxeles en nuestro programa de instalación para sombrear un área más grande y artefactos empiecen a aparecer.</span><span class="sxs-lookup"><span data-stu-id="454a5-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="454a5-192">A continuación, si se agregan las estrellas de resolución completa con tarjetas más pequeñas, obtenemos el galaxy completa:</span><span class="sxs-lookup"><span data-stu-id="454a5-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Cerca del resultado final de la representación de galaxy con estrellas de resolución completa](images/full-galaxy-500px.png)

<span data-ttu-id="454a5-194">Una vez que se estaban en el camino correcto con la forma, se agrega una capa de nubes, intercambiadas los puntos temporales con los se pinta en Photoshop y agregan algunos colores adicionales.</span><span class="sxs-lookup"><span data-stu-id="454a5-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="454a5-195">El resultado fue una galaxia vía láctea nuestro material gráfico y tanto los equipos de ingeniería sentían estupendo y cumple nuestros objetivos de disponer de profundidad, el volumen y movimiento, todo sin recargar la CPU.</span><span class="sxs-lookup"><span data-stu-id="454a5-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Nuestro Galaxy vía láctea final en 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="454a5-197">Nuestro Galaxy vía láctea final en 3D.</span><span class="sxs-lookup"><span data-stu-id="454a5-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="454a5-198">Más para explorar</span><span class="sxs-lookup"><span data-stu-id="454a5-198">More to explore</span></span>

<span data-ttu-id="454a5-199">Hemos conseguido que esté disponible en y abierto el código de la aplicación de explorador Galaxy [GitHub](https://github.com/Microsoft/GalaxyExplorer) a los desarrolladores compilar.</span><span class="sxs-lookup"><span data-stu-id="454a5-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="454a5-200">¿Está interesado en obtener más información sobre el proceso de desarrollo para Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="454a5-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="454a5-201">Consulte todas nuestras actualizaciones de proyecto anteriores en el [canal de YouTube de Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="454a5-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="454a5-202">Acerca de los autores</span><span class="sxs-lookup"><span data-stu-id="454a5-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="454a5-203"><b>Karim Luccin</b> es un ingeniero de Software y un entusiasta de los objetos visuales decorativo.</span><span class="sxs-lookup"><span data-stu-id="454a5-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="454a5-204">Fue el ingeniero de gráficos para Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="454a5-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="454a5-205"><b>Andy Zibits</b> es un entusiasta de arte Lead y el espacio que administra el equipo de modelado 3D para Galaxy Explorer y luchó de partículas aún más.</span><span class="sxs-lookup"><span data-stu-id="454a5-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="454a5-206">Vea también</span><span class="sxs-lookup"><span data-stu-id="454a5-206">See also</span></span>
* [<span data-ttu-id="454a5-207">Explorador de Galaxy en GitHub</span><span class="sxs-lookup"><span data-stu-id="454a5-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="454a5-208">Actualizaciones del explorador de Galaxy de project en YouTube</span><span class="sxs-lookup"><span data-stu-id="454a5-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
