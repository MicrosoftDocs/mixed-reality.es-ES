---
title: 'Caso práctico: equipo de diseño de mi primer año en el HoloLens'
description: Mi trayectoria de un flatland 2D a todo el mundo 3D que se inicia cuando me uní al equipo de diseño de HoloLens en enero de 2016.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Personal de Windows Mixed Reality, HoloLens, diseño, editorial,
ms.openlocfilehash: e16be57d42bdc003fd601b94e054c7c25ebd290e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605770"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Caso práctico: equipo de diseño de mi primer año en el HoloLens

Mi trayectoria de un flatland 2D a todo el mundo 3D que se inicia cuando me uní al equipo de diseño de HoloLens en enero de 2016. Antes de unirse al equipo, tuve muy poca experiencia en el diseño 3D. Era como el chino proverbio acerca de una trayectoria de millas de mil empezando por un solo paso, excepto en mi caso, ese primer paso fue un año bisiesto.

![Teniendo el salto de 2D en 3D](images/2D_to_3D-800px.gif)<br>
*Teniendo el salto de 2D en 3D*

> *"Sentía como si he saltado en el asiento del conductor sin necesidad de saber cómo dirigir el coche. Se ha desbordado y lo asusta, pero muy centrada. "*<br>
> — Hae Jin Lee

Durante el año pasado, recogen conocimientos teóricos y prácticos tan rápido como podría, pero aún tengo mucho que aprender. En este caso, he escrito de 4 observaciones con un vídeo tutorial documentar la transición desde un 2D a Diseñador interacción 3D. Espero que mi experiencia le inspiren otros diseñadores para realizar el salto a 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Marco de Adiós. Hola espacial / diegetic la interfaz de usuario

Cada vez que diseñé Pósteres, revistas, sitios Web o pantallas de la aplicación, un período determinado (normalmente un rectángulo) era una constante para todos los problemas. A menos que se está leyendo este artículo en un HoloLens u otro dispositivo de realidad virtual, es *mirando esto desde el exterior* a través de la pantalla 2D protegido de forma segura dentro de un marco. Contenido es externo a usted. Sin embargo, auriculares de realidad mixta *elimina el marco*, por lo que está dentro del espacio de contenido, buscar y recorrer el contenido de dentro afuera.

Entender esto conceptualmente, pero al principio había cometido a simplemente transfiriendo 2D pensar en un espacio 3D. Que obviamente no funcionó bien porque el espacio 3D tiene sus propias propiedades únicas, como un cambio de la vista (según el movimiento del usuario) y [requisito distinto para su comodidad del usuario](https://www.youtube.com/watch?v=-606oZKLa_s/) (según las propiedades de los dispositivos y los seres humanos mediante ellos). Por ejemplo, en un espacio 2D de diseño de interfaz de usuario, el bloqueo de elementos de interfaz de usuario en la esquina de una pantalla es un patrón muy común, pero no se sienta natural en experiencias MR/VR; este estilo de HUD (Head mostrar) la interfaz de usuario dificulta una inmersión en el espacio del usuario y hace que las molestias de usuario. Es como tener una partícula de polvo molesto en sus gafas que están deseando deshacerse de. Con el tiempo, he aprendido que se siente más natural para colocar contenido en un espacio 3D y agregar comportamiento bloqueado por el cuerpo de la que hace que el contenido siga al usuario a una distancia fija relativa.

![Body-locked](images/bodylockedtagalong.gif)<br>
*Body-locked*

<br>

![World-locked](images/worldlocked.gif)<br>
*World-locked*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmentos: Un ejemplo de excelente de Diegetic de UI

[Fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8), un intriga en primera persona crime desarrollado por [Asobo Studio](http://www.asobostudio.com/) para HoloLens muestra una UI Diegetic excelente. En este juego, el usuario se convierte en un carácter principal, una detección que intenta resolver un misterio. Las pistas de pivotal para solucionar este gran misterio obtengan esparcidas espacio físico del usuario y son a menudo incrustado dentro de un objeto ficticio en lugar de existente por sí solos. Esta interfaz de usuario tiende a ser menos reconocibles que bloqueado por el cuerpo de la interfaz de usuario, por lo que el equipo Asobo inteligentemente usa muchas indicaciones como dirección de caracteres virtual mirada, sonido, claro y guías (por ejemplo, la flecha que señala la ubicación de la pista) de diegetic para captar la atención del usuario.

![Fragmentos - ejemplos Diegetic UI](images/fragments-game-example-1.jpg)<br>
*Fragmentos - ejemplos Diegetic UI*

### <a name="observations-about-diegetic-ui"></a>Observaciones sobre diegetic la interfaz de usuario

Espacial de la interfaz de usuario (ambos bloqueado por el cuerpo y bloqueado por el mundo) y diegetic la interfaz de usuario tienen sus propios puntos fuertes y débiles. Lo animo a los diseñadores para probar tantas aplicaciones MR/VR como sea posible y para desarrollar su propia descripción y la sensibilidad de la interfaz de usuario distintos métodos de colocación.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>La devolución de esqueuomorfismo e interacción mágica

Esqueuomorfismo, ha sido una interfaz digital que se asemeja a la forma de objetos del mundo real "uncool" durante los últimos años de 5 a 7 en el sector de diseño. Cuando Apple, por último, dio forma al diseño de plano en iOS 7, parecía que Esqueuomorfismo estaba inactivo, por último, como una metodología de diseño de interfaz. Pero, a continuación, un nuevo medio, auriculares MR/VR llegaron la comercialización y parece Esqueuomorfismo devolvió de nuevo. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulador de trabajo: Un ejemplo de diseño VR skeuomorphic

[Trabajo de simulador](http://jobsimulatorgame.com/), un juego divertido desarrollado por [Owlchemy Labs](https://owlchemylabs.com/) es uno del ejemplo para el diseño VR skeuomorphic más popular. Dentro de este juego, se transportan los jugadores en el futuro, donde los robots de reemplazar a los seres humanos y los seres humanos visite un museo para experimentar lo que se siente para realizar tareas mundanas en uno de cuatro trabajos diferentes: Auto mecánico, Gourmet Chef, distribuidor Store o trabajador de oficina.

La ventaja de Esqueuomorfismo está clara. Entorno familiar y objetos dentro de este juego ayudan a los nuevos usuarios VR sentirse más cómodos y presente en el espacio virtual. También les hace sentir como en el control mediante la asociación de conocimientos familiar y comportamientos con los objetos y sus reacciones físicas correspondientes. Por ejemplo, para Beba una taza de café, las personas simplemente deben guiarán a la máquina de café, presione un botón, agarre el identificador de cup y planos inclinados hacia su boca como lo harían en el mundo real.

![Simulador de trabajo](images/job-simulator.gif)<br>
*Simulador de trabajo*

Porque MR/VR sigue siendo un medio de desarrollo, utilizando un cierto grado de esqueuomorfismo es necesario para desmitificar la tecnología MR/VR e introducirlo a audiencias de mayor tamaño en todo el mundo. Además, utilizando esqueuomorfismo o representación real puede ser beneficioso para tipos específicos de aplicaciones como simulación de cirugía o vuelo. Puesto que es el objetivo de estas aplicaciones desarrollar y perfeccionar los conocimientos específicos que se pueden aplicar directamente en el mundo real, cuanto más se acerque la simulación es el mundo real, el conocimiento más transferible es.

Recuerde que esqueuomorfismo es sólo uno de ellos. Es mucho mayor que el potencial del mundo MR/VR y deben esforzarse por diseñadores crear interacciones de hyper-natural mágicos, nuevas prestaciones que son posibles en forma exclusiva en el mundo MR/VR. Para comenzar, considere la posibilidad de agregar mágicos poderes a los objetos normales para permitir que los usuarios cumplir sus deseos fundamentales, incluidos teleportation y omniscience.

![Puerta mágica del Doraemon (izquierda) y slippers(right) Ruby](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Puerta mágica del Doraemon (izquierda) y slippers(right) ruby*

### <a name="observations-about-skeuomorphism-in-vr"></a>Observaciones sobre esqueuomorfismo de VR

Desde "En cualquier lugar de puerta" en Doraemon, "Zapatos de rubí" en el mago de Oz a "Asignación de Maurader" de Harry Potter, ejemplos de objetos ordinarios con eficacia mágica abundan en ficción popular. Estos objetos mágicos nos ayudan a visualizar una conexión entre el mundo real y lo fantástico, entre las novedades y lo que podría ser. Tenga en cuenta que cuando se diseña el mágica o surrealistas objeto uno debe lograr un equilibrio entre funcionalidad y entretenimiento. Tenga cuidado con la tentación de crear algo mágico puramente solo para fines de novedad.

## <a name="understanding-different-input-methods"></a>Descripción de los métodos de entrada diferentes

Cuando ha diseñado para el medio de 2D, tuve que centrarse en táctil, mouse y las interacciones de teclado para las entradas. En el espacio de diseño MR/VR, nuestro organismo se convierte en la interfaz y los usuarios pueden usar una selección más amplia de los métodos de entrada: como voz, mirada, gestos, [6 GDL controladores](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)y guantes que permitirse conexiones más intuitivo y directo con objetos virtuales.

![Entradas disponibles en HoloLens](images/inputs.jpg)<br>
*Entradas disponibles en HoloLens*

> *"Todo lo que es algo mejor y peor para otra cosa".*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

Por ejemplo, gestos de entrada con la mano reconstrucción y sensores de cámara en un dispositivo HMD libera la mano de los usuarios de que contiene los controladores o utilizar sudoroso guantes, pero uso frecuente puede provocar fatiga físico (conocidas también como gorila). Además, los usuarios deben mantener sus manos dentro de la línea de visión; Si la cámara no puede ver las manos, no se puede usar las manos.

Entrada de voz es buena para atravesar las tareas complejas porque permite que los usuarios corten a través de los menús anidados con un comando (por ejemplo, "Muéstrame las películas realizadas por Laika studio.") y también muy económica cuando se combina con otro modalidad (p. ej., "Se enfrentan a mí" comando ofrece orientación sobre la holograma de un usuario está mirando hacia el usuario). Sin embargo, la entrada de voz no puede funcionar bien en un entorno con ruido o es posible que no adecuados en un espacio muy silencioso.

Además de gestos y voz, portátiles realiza un seguimiento de los controladores (p. ej., Oculus touch, Vive, etc.) son métodos de entrada muy populares porque son Aproveche fácil de usar, con precisión, República [proprioception](https://en.wikipedia.org/wiki/Proprioception)y proporcionar indicaciones hápticos pasivas. Sin embargo, estas ventajas se derivan a costa de no poder ser manos operativo y utilizar el seguimiento del dedo completa.

![Senso (izquierda) y Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (izquierda) y Manus VR (derecha)*

Aunque no es tan popular como controladores, guantes están tomando impulso nuevo gracias a la ola de MR/VR. Más recientemente, ha iniciado el cerebro/cuenta entrada ganar terreno como una interfaz para los entornos virtuales mediante la integración de sensor EEG o EMG para auriculares (p. ej., [MindMaze VR](http://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Observaciones sobre los métodos de entrada

Estos son solo un ejemplo de dispositivos de entrada disponibles en el mercado para MR/VR. Continúan proliferan hasta que la industria a crecer y está de acuerdo en los procedimientos recomendados. Hasta entonces, los diseñadores deben estar al tanto de nuevos dispositivos de entrada y ser muy versado en los métodos de entrada específicos para su proyecto en particular. Los diseñadores deben buscar soluciones creativas dentro de las limitaciones, mientras se reproduce también a los puntos fuertes de un dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>La escena de boceto y probar en los auriculares

Cuando trabajé en 2D, había esbozada principalmente solo el contenido. Sin embargo, en el espacio de realidad mixta que no era suficiente. Tuve que boceto de toda la escena imaginar mejor las relaciones entre los objetos virtuales y el usuario. Para ayudar a mi pensamiento espacial, empecé a bosquejar escenas en [cine 4D](https://www.maxon.net/en/products/cinema-4d/overview/) y a veces, crear activos simple para crear prototipos en [Maya](http://www.autodesk.com/products/maya/overview/). Nunca lo he utilizado cualquier programa antes de unirse al equipo de HoloLens y soy un principiante, pero trabajar con estos programas 3D definitivamente me ayudó a comenzar a familiarizarse con la nueva terminología, como [sombreador](https://en.wikipedia.org/wiki/Shader) y [IK (inverso cinemática)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Aproximación esbozado la escena en 3D, independientemente de la experiencia real en auriculares era casi nunca el mismo que el boceto. Por eso es importante probar la escena en el destino auriculares. "— Hae Jin Lee**

Para crear prototipos de HoloLens, he intentado todos los tutoriales en [Mixed Reality Academy](academy.md) para iniciar. Luego comencé a jugar con [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) que Microsoft proporciona a los desarrolladores para acelerar el desarrollo de aplicaciones holográficas. Cuando fui bloqueado con algo, registrar mi pregunta a [foro de respuesta y la pregunta de HoloLens](https://forums.hololens.com/categories/questions-and-answers/).

Después de adquirir conocimientos básicos de creación de prototipos de HoloLens, deseaba permitir que a otros no codificadores prototipos por sí solos. Por lo que hice un tutorial de vídeo que enseña a desarrollar un proyectil simple con HoloLens. Explican brevemente los conceptos básicos, incluso que si tiene cero experiencia en desarrollo de HoloLens, podrá seguir el tutorial.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*He realizado este sencillo tutorial para programadores, como yo mismo.*

Para crear prototipos de realidad virtual, tomé los cursos en [VR Dev School](http://learn.vrdev.school/) y también tardó [la creación de contenido 3D de realidad Virtual](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) en Lynda.com. Desarrollo VR school proporciona que más conocimientos detallados en la codificación y el curso de Lynda me ofrece una breve introducción interesante a crear activos de realidad virtual.

## <a name="take-the-leap"></a>Realizar el salto

Hace un año, sentía como todo esto era un poco abrumador. Ahora que puedo afirmar que fue 100%, vale la pena. MR/VR sigue siendo un medio muy joven y hay muchas posibilidades muy interesantes a la espera de llevarse a cabo. Me siento lleno de inspiración y afortunada ser capaz de reproducir una pequeña parte de diseñar el futuro. Espero que se unirá me en su viaje en un espacio 3D.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>Diseñador UX @Microsoft</td>
</tr>
</table>

 
