---
title: 'Caso práctico: creación de una galaxia en una realidad mixta'
description: Antes de que se enviara a Microsoft HoloLens, hemos preguntado a nuestra comunidad de desarrolladores qué tipo de aplicación les gustaría ver una compilación de equipo interna con experiencia para el nuevo dispositivo. Se comparten más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea denominada "explorador de Galaxy".
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, compartir ideas, caso práctico
ms.openlocfilehash: f13395250c8a73718408c051ab95d2ec4bf62014
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278183"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="6dd5e-105">Caso práctico: creación de una galaxia en una realidad mixta</span><span class="sxs-lookup"><span data-stu-id="6dd5e-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="6dd5e-106">Antes de que se enviara a Microsoft HoloLens, hemos preguntado a nuestra comunidad de desarrolladores qué tipo de aplicación les gustaría ver una compilación de equipo interna con experiencia para el nuevo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="6dd5e-107">Se comparten más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea denominada [Galaxy Explorer](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="6dd5e-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="6dd5e-108">Andy Zibits, el director de arte del proyecto y Karim Luccin, el ingeniero de gráficos del equipo, habla sobre el esfuerzo colaborativo entre arte e ingeniería que llevó a la creación de una representación precisa e interactiva de la forma láctea de Galaxy en el explorador de Galaxy.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="6dd5e-109">La tecnología</span><span class="sxs-lookup"><span data-stu-id="6dd5e-109">The Tech</span></span>

<span data-ttu-id="6dd5e-110">[Nuestro equipo](galaxy-explorer.md#meet-the-team) , compuesto por dos diseñadores, tres desarrolladores, cuatro artistas, un productor y un evaluador, tenía seis semanas para compilar una aplicación totalmente funcional que permitiría a los usuarios obtener información sobre la inmensaidad y la belleza de nuestra forma de ordeño.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="6dd5e-111">Queríamos sacar el máximo partido de la capacidad de HoloLens para representar objetos 3D directamente en tu espacio de vida, por lo que decidimos que queríamos crear una galaxia de aspecto realista en la que los usuarios podrían hacer zoom para ampliar y ver los estrellas individuales, cada uno con sus propias trayectorias.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="6dd5e-112">En la primera semana de desarrollo, surgimos con unos pocos objetivos para nuestra representación de la forma láctea de Galaxy: era necesario tener una profundidad, un movimiento y un volumétrico (lleno de estrellas) que le ayuden a crear la forma de la galaxia.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="6dd5e-113">El problema con la creación de una galaxia animada que tenía miles de millones de estrellas era que el número de elementos únicos que es necesario actualizar sería demasiado grande por fotograma para que HoloLens se animase con la CPU.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="6dd5e-114">Nuestra solución ha participado en una combinación compleja de arte y ciencia.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="6dd5e-115">En segundo plano</span><span class="sxs-lookup"><span data-stu-id="6dd5e-115">Behind the scenes</span></span>

<span data-ttu-id="6dd5e-116">Para que los usuarios puedan explorar estrellas individuales, el primer paso era averiguar cuántas partículas se podían representar a la vez.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="6dd5e-117">Representar objetos</span><span class="sxs-lookup"><span data-stu-id="6dd5e-117">Rendering particles</span></span>

<span data-ttu-id="6dd5e-118">Las CPU actuales son ideales para procesar tareas en serie y hasta algunas tareas paralelas a la vez (en función de la cantidad de núcleos que tengan), pero las GPU son mucho más eficaces en el procesamiento de miles de operaciones en paralelo.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="6dd5e-119">Sin embargo, dado que normalmente no comparten la misma memoria que la CPU, el intercambio de datos entre < de CPU > GPU puede convertirse rápidamente en un cuello de botella.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="6dd5e-120">Nuestra solución era crear una galaxia en la GPU y debía vivir completamente en la GPU.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="6dd5e-121">Iniciamos pruebas de esfuerzo con miles de objetos de punto en distintos patrones.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="6dd5e-122">Esto nos permitió obtener la galaxia en HoloLens para ver lo que funcionó y lo que no.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="6dd5e-123">Crear la posición de las estrellas</span><span class="sxs-lookup"><span data-stu-id="6dd5e-123">Creating the position of the stars</span></span>

<span data-ttu-id="6dd5e-124">Uno de nuestros miembros del equipo ya ha escrito C# el código que generaría estrellas en su posición inicial.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="6dd5e-125">Las estrellas se encuentran en una elipse y su posición puede describirse mediante (**curveOffset**, **ellipseSize**, **elevation**), donde **curveOffset** es el ángulo de la estrella a lo largo de la elipse, **ellipseSize** es la dimensión de la elipse a lo largo de X y Z, y eleva la elevación adecuada de la estrella dentro de la galaxia.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="6dd5e-126">Por lo tanto, podemos crear un búfer ([ComputeBuffer de Unity](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que se inicializaría con cada atributo de estrella y lo enviaría en la GPU donde residiría para el resto de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="6dd5e-127">Para dibujar este búfer, usamos [DrawProcedural de Unity](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , que permite ejecutar un sombreador (código en una GPU) en un conjunto arbitrario de puntos sin tener una malla real que represente la galaxia:</span><span class="sxs-lookup"><span data-stu-id="6dd5e-127">To draw this buffer, we use [Unity’s DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="6dd5e-128">**CPU**</span><span class="sxs-lookup"><span data-stu-id="6dd5e-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="6dd5e-129">**GPU**</span><span class="sxs-lookup"><span data-stu-id="6dd5e-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="6dd5e-130">Comenzamos con patrones circulares sin procesar con miles de partículas.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="6dd5e-131">Esto nos dio la prueba de que necesitábamos que podamos administrar muchas partículas y ejecutarla a velocidades de rendimiento, pero no estamos satisfecho con la forma general de Galaxy.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="6dd5e-132">Para mejorar la forma, se intentaron varios patrones y sistemas de partículas con rotación.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="6dd5e-133">Estarían en primer lugar, ya que el número de partículas y el rendimiento se han mantenido coherentes, pero la forma se ha interrumpido cerca del centro y las estrellas no eran realistas.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="6dd5e-134">Necesitábamos una emisión que nos permitiera manipular el tiempo y hacer que las partículas se muevan de forma realista, lo que se repite cada vez más cerca del centro de la galaxia.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Se han intentado varios patrones y sistemas de partículas que se han girado, como estos.](images/galaxy-patterns-500px.png)

<span data-ttu-id="6dd5e-136">Se han intentado varios patrones y sistemas de partículas que se han girado, como estos.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="6dd5e-137">Nuestro equipo realizó una investigación sobre la manera en que galaxiesó la función y creamos un sistema de partículas personalizado específicamente para la galaxia, de modo que podríamos trasladar las partículas a las elipses en función de "[teoría de ola de densidad](https://en.wikipedia.org/wiki/Density_wave_theory)", que theorizes que los brazos de una galaxia son áreas de mayor densidad pero en flujo constante, como un atasco de tráfico.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="6dd5e-138">Parece estable y sólido, pero en realidad las estrellas están pasando y salen de los brazos a medida que se mueven a lo largo de sus puntos suspensivos respectivos.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="6dd5e-139">En nuestro sistema, los objetos nunca existen en la CPU, por lo que se generan las tarjetas y se orientan todas en la GPU, por lo que todo el sistema es simplemente el estado inicial + hora.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="6dd5e-140">Progresaría de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6dd5e-140">It progressed like this:</span></span>

![Progresión del sistema de partículas con representación de GPU](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="6dd5e-142">Progresión del sistema de partículas con representación de GPU</span><span class="sxs-lookup"><span data-stu-id="6dd5e-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="6dd5e-143">Una vez que se agregan las elipses suficientes y se establecen para rotar, el Galaxies comenzó a formar "armas" donde converge el movimiento de estrellas.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="6dd5e-144">El espaciado de las estrellas a lo largo de cada trazado elíptico se proporcionó cierta aleatoriedad y cada estrella tenía un bit de aleatoriedad posicional agregado.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="6dd5e-145">Esto creó una distribución mucho más natural del movimiento de estrella y la forma de ARM.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="6dd5e-146">Por último, se ha agregado la capacidad de controlar el color en función de la distancia desde el centro.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="6dd5e-147">Crear el movimiento de las estrellas</span><span class="sxs-lookup"><span data-stu-id="6dd5e-147">Creating the motion of the stars</span></span>

<span data-ttu-id="6dd5e-148">Para animar el movimiento de estrella general, era necesario agregar un ángulo constante para cada fotograma y hacer que las estrellas se muevan a lo largo de sus puntos suspensivos en una velocidad radial constante.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="6dd5e-149">Esta es la razón principal para usar **curveOffset**.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="6dd5e-150">Esto no es técnicamente correcto, ya que las estrellas se moverán más rápido a lo largo de los extremos largos de las elipses, pero el movimiento general se considera adecuado.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Las estrellas se mueven más rápido en el arco largo, más lentamente en los bordes.](images/ellipse-movement.jpg)

<span data-ttu-id="6dd5e-152">Las estrellas se mueven más rápido en el arco largo, más lentamente en los bordes.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="6dd5e-153">Con eso, cada estrella se describe por completo (**curveOffset**, **ellipseSize**, **elevación**, **Age**), donde **Age** es una acumulación del tiempo total transcurrido desde que se cargó la escena.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="6dd5e-154">Esto nos permitió generar decenas de miles de estrellas una vez al principio de la aplicación y, a continuación, animamos un conjunto único de estrellas a lo largo de las curvas establecidas.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="6dd5e-155">Dado que todo está en la GPU, el sistema puede animar todas las estrellas en paralelo sin costo alguno en la CPU.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Este es su aspecto cuando se dibujan cuatros blancos.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="6dd5e-157">Este es su aspecto cuando se dibujan cuatros blancos.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="6dd5e-158">Para que cada cuatro se enfrente a la cámara, usamos un sombreador de geometría para transformar cada posición en estrella en un rectángulo 2D de la pantalla que contendrá la textura en estrella.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Diamantes en lugar de cuádruples.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="6dd5e-160">Diamantes en lugar de cuádruples.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="6dd5e-161">Como queríamos limitar el exceso (el número de veces que se procesará un píxel) en la medida de lo posible, giramos nuestras cuádruples para que tuvieran menos superposición.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="6dd5e-162">Agregar nubes</span><span class="sxs-lookup"><span data-stu-id="6dd5e-162">Adding clouds</span></span>

<span data-ttu-id="6dd5e-163">Hay muchas maneras de obtener una sensación volumétrica con partículas: desde Ray, desde el interior de un volumen hasta el dibujo de tantas partículas como sea posible para simular una nube.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="6dd5e-164">El radio en tiempo real de marzo iba a ser demasiado caro y difícil de crear, por lo que primero hemos intentado crear un sistema impostor con un método para representar bosques en juegos, con una gran cantidad de imágenes 2D de árboles orientados a la cámara.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="6dd5e-165">Cuando hacemos esto en un juego, podemos hacer que las texturas de los árboles se representen a partir de una cámara que gira, guardar todas esas imágenes y en tiempo de ejecución para cada tarjeta de la cartelera, seleccionar la imagen que coincida con la dirección de la vista.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="6dd5e-166">Esto no funciona tan bien cuando las imágenes son hologramas.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="6dd5e-167">La diferencia entre el ojo izquierdo y el ojo derecho lo hace para que se necesite una resolución mucho más alta, o bien que se parezca plana, con alias o repetitivo.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="6dd5e-168">En el segundo intento, intentamos tener tantas partículas como sea posible.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="6dd5e-169">Los mejores objetos visuales se logran cuando se dibujan partículas y se desenfocaron antes de agregarlas a la escena.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="6dd5e-170">Los problemas típicos de ese enfoque estaban relacionados con el número de objetos que se podían dibujar en un momento dado y el área de la pantalla que se encontraban mientras se sigue manteniendo 60fps.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="6dd5e-171">Desenfocar la imagen resultante para obtener esta nube suele ser una operación muy costosa.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Sin textura, este es el aspecto de las nubes con una opacidad del 2%.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="6dd5e-173">Sin textura, este es el aspecto de las nubes con una opacidad del 2%.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="6dd5e-174">Ser aditivos y tener una gran cantidad de ellos significa que tendremos varias cuádruples en la parte superior entre sí, con un sombreado repetido del mismo píxel.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="6dd5e-175">En el centro de la galaxia, el mismo píxel tiene cientos de cuádruples unos de otros, y esto tenía un costo enorme cuando se realizaba una pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="6dd5e-176">Realizar nubes de pantalla completa e intentar desenfocarlos habría sido una mala idea, por lo que, en su lugar, decidimos dejar que el hardware hiciera el trabajo.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="6dd5e-177">Un bit de contexto primero</span><span class="sxs-lookup"><span data-stu-id="6dd5e-177">A bit of context first</span></span>

<span data-ttu-id="6dd5e-178">Cuando se usan texturas en un juego, el tamaño de la textura rara vez coincidirá con el área en la que se desea utilizar, pero se puede usar un tipo diferente de filtrado de textura para que la tarjeta gráfica se interpole el color que se desea de los píxeles de la textura ([filtrado de textura](https://msdn.microsoft.com/library/dn642451.aspx)).</span><span class="sxs-lookup"><span data-stu-id="6dd5e-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="6dd5e-179">El filtrado que nos interesa es [bilineal Filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) , que calculará el valor de cualquier píxel usando los 4 vecinos más cercanos.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Original antes del filtrado](images/texture-1.png)

![Resultado después del filtrado](images/texture-2.png)

<span data-ttu-id="6dd5e-182">Con esta propiedad, vemos que cada vez que se intenta dibujar una textura en un área dos veces como grande, se desenfoca el resultado.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="6dd5e-183">En lugar de representarla en una pantalla completa y perder esos precioso milisegundos que podríamos gastar en algo más, representamos en una versión pequeña de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="6dd5e-184">Después, copiando esta textura y ajustándola en un factor de 2 varias veces, volveremos a la pantalla completa al desenfocar el contenido del proceso.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![X3 vuelve a escalar a la resolución completa.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="6dd5e-186">X3 vuelve a escalar a la resolución completa.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="6dd5e-187">Esto nos permitió obtener la parte de la nube con solo una fracción del costo original.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="6dd5e-188">En lugar de agregar nubes en la resolución completa, solo dibujamos 1/64TH de los píxeles y simplemente ajustamos la textura a la resolución completa.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Izquierda, con una escala de 1/8 a resolución completa; y a la derecha, con una capacidad de 3 escalado con potencia de 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="6dd5e-190">Izquierda, con una escala de 1/8 a resolución completa; y a la derecha, con una capacidad de 3 escalado con potencia de 2.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="6dd5e-191">Tenga en cuenta que el intento de pasar de 1/64TH del tamaño al tamaño completo en un solo aspecto sería completamente diferente, ya que la tarjeta gráfica seguiría usando 4 píxeles en nuestra configuración para sombrear un área más grande y los artefactos comenzarán a aparecer.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="6dd5e-192">A continuación, si agregamos estrellas de resolución completa con tarjetas más pequeñas, obtenemos el completo Galaxy:</span><span class="sxs-lookup"><span data-stu-id="6dd5e-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Resultado casi final de la representación de Galaxy con estrellas de resolución completa](images/full-galaxy-500px.png)

<span data-ttu-id="6dd5e-194">Una vez que se encontraba el buen seguimiento con la forma, agregamos una capa de nubes, cambiaban los puntos temporales por los que dibujamos en Photoshop y agregamos un color adicional.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="6dd5e-195">El resultado era una forma láctea de Galaxy que nuestros equipos de arte e ingeniería nos sentían bien y cumplían nuestros objetivos de tener profundidad, volumen y movimiento, todo ello sin agotar la CPU.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![La forma láctea final de Galaxy en 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="6dd5e-197">La forma láctea final de Galaxy en 3D.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="6dd5e-198">Más información para explorar</span><span class="sxs-lookup"><span data-stu-id="6dd5e-198">More to explore</span></span>

<span data-ttu-id="6dd5e-199">Hemos abierto el código para la aplicación Galaxy Explorer y lo hemos puesto a disposición de los desarrolladores en [GitHub](https://github.com/Microsoft/GalaxyExplorer) .</span><span class="sxs-lookup"><span data-stu-id="6dd5e-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="6dd5e-200">¿Está interesado en encontrar más información sobre el proceso de desarrollo de Galaxy Explorer?</span><span class="sxs-lookup"><span data-stu-id="6dd5e-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="6dd5e-201">Eche un vistazo a las últimas actualizaciones del proyecto en el [canal de YouTube de Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="6dd5e-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="6dd5e-202">Acerca de los autores</span><span class="sxs-lookup"><span data-stu-id="6dd5e-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="6dd5e-203"><b>Karim Luccin</b> es un ingeniero de software y entusiasta de los objetos visuales.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="6dd5e-204">Fue el ingeniero de gráficos de Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="6dd5e-205"><b>Andy Zibits</b> es un líder de vanguardia y un entusiasta de espacio que administraba el equipo de modelado 3D para Galaxy Explorer y fought para incluso más partículas.</span><span class="sxs-lookup"><span data-stu-id="6dd5e-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="6dd5e-206">Vea también</span><span class="sxs-lookup"><span data-stu-id="6dd5e-206">See also</span></span>
* [<span data-ttu-id="6dd5e-207">Explorador de Galaxy en GitHub</span><span class="sxs-lookup"><span data-stu-id="6dd5e-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="6dd5e-208">Actualizaciones de proyectos del explorador de Galaxy en YouTube</span><span class="sxs-lookup"><span data-stu-id="6dd5e-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
