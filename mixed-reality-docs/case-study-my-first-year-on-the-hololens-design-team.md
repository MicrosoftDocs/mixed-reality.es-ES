---
title: 'Caso práctico: mi primer año en el equipo de diseño de HoloLens'
description: Mi viaje desde un Flatland de 2D al mundo en 3D comenzó cuando se unió al equipo de diseño de HoloLens en enero de 2016.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, diseño, editorial, personal
ms.openlocfilehash: 47ed5edd58846687daa4242f7bdbc85dae0f5255
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436604"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>Caso práctico: mi primer año en el equipo de diseño de HoloLens

Mi viaje desde un Flatland de 2D al mundo en 3D comenzó cuando se unió al equipo de diseño de HoloLens en enero de 2016. Antes de unirse al equipo, tenía muy poca experiencia en el diseño 3D. Era como el proverbor chino sobre un recorrido de mil millas que comienza con un solo paso, excepto en el caso de que el primer paso fuera un salto.

![realizar el salto de 2D a 3D](images/2D_to_3D-800px.gif)<br>
*Realizar el salto de 2D a 3D*

> *"Me sentía como si hubiera saltado el puesto del conductor sin saber cómo impulsar el coche. Me abrumaron y mezclarlas, pero muy centrados ".*<br>
> — Hae Jin Lee

En el año pasado, reconozco las habilidades y los conocimientos tan rápido como podía, pero todavía tengo mucho que aprender. Aquí, he escrito 4 observaciones con un tutorial en vídeo que documenta la transición de un diseñador de interacciones de 2D a 3D. Espero que mi experiencia inspire a otros diseñadores para que tomen el salto en 3D.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Fotograma bueno: adiós. Interfaz de usuario de Hola espacial/diegetic

Cada vez que se diseñan pósteres, revistas, sitios web o pantallas de aplicación, un fotograma definido (normalmente un rectángulo) era una constante para cada problema. A menos que lea esta entrada en un dispositivo HoloLens u otro dispositivo VR, lo *examinará de la pantalla exterior a la* 2D protegida de forma segura dentro de un marco. El contenido es externo. Sin embargo, el casco de realidad mixta *elimina el fotograma*, por lo que se encuentra dentro del espacio de contenido, mirando y recorriendo el contenido desde dentro.

Entiendo esto conceptualmente, pero al principio he cometido el error de simplemente transferir el pensamiento 2D en el espacio 3D. Obviamente, eso no funcionaba bien porque el espacio 3D tiene sus propias propiedades únicas, como un cambio de vista (basado en el movimiento del usuario) y un [requisito diferente para la comodidad del usuario](https://www.youtube.com/watch?v=-606oZKLa_s/) (en función de las propiedades de los dispositivos y los usuarios que las usan). Por ejemplo, en un espacio de diseño de la interfaz de usuario 2D, el bloqueo de los elementos de la interfaz de usuario en la esquina de una pantalla es un patrón muy común, pero esta interfaz de usuario de estilo HUD (presentación de encabezado) no se siente natural en las experiencias MR/VR; dificulta la inmersión del usuario en el espacio y hace que el usuario se haga más cómodo. Es como tener una partícula de polvo molesta en sus anteojos de los que Dying deshacerse. Con el tiempo, aprendí que es más natural colocar el contenido en el espacio 3D y agregar un comportamiento con bloqueo de cuerpo que hace que el contenido siga el usuario a una distancia fija relativa.

![](images/bodylockedtagalong.gif) bloqueada por el cuerpo<br>
*Con bloqueo del cuerpo*

<br>

![](images/worldlocked.gif) con bloqueo mundial<br>
*Con bloqueo mundial*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>Fragmentos: un ejemplo de excelente interfaz de usuario de Diegetic

En el caso de los [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8), un mayor emocionado de delitos desarrollado por [Asobo Studio](https://www.asobostudio.com/) para HoloLens demuestra una excelente interfaz de usuario de Diegetic. En este juego, el usuario se convierte en un carácter principal, un detective que intenta resolver un misterio. Las pistas dinámicas para solucionar este misterio se separan en el salón físico del usuario y, a menudo, se insertan en un objeto ficticio en lugar de hacerlo por su cuenta. Esta interfaz de usuario de diegetic tiende a ser menos reconocible que la interfaz de usuario bloqueada por el cuerpo, por lo que el equipo de Asobo ha usado de forma inteligente muchas guías, como la dirección de miración de los caracteres virtuales, el sonido, la luz y las guías (por ejemplo, la flecha que apunta a la posición de la pista) para atraer la atención del usuario.

![fragmentos-ejemplos de la interfaz de usuario de Diegetic](images/fragments-game-example-1.jpg)<br>
*Fragmentos: ejemplos de la interfaz de usuario de Diegetic*

### <a name="observations-about-diegetic-ui"></a>Observaciones sobre la interfaz de usuario de diegetic

La interfaz de usuario espacial (tanto con bloqueo de cuerpo como con bloqueo mundial) y la interfaz de usuario de diegetic tienen sus propios puntos fuertes y débiles. Animamos a los diseñadores a probar tantas aplicaciones de MR/VR como sea posible y desarrollar sus propios conocimientos y Sensibility para varios métodos de posicionamiento de la interfaz de usuario.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>La devolución de skeuomorphism e interacción mágica

Skeuomorphism, una interfaz digital que imita la forma de objetos del mundo real ha sido "inestable" durante los últimos 5 y 7 años en el sector del diseño. Por último, cuando Apple dio forma a un diseño plano en iOS 7, parecía que Skeuomorphism estuvo inactivo como una metodología de diseño de interfaz. Pero, a continuación, se ha llegado a un nuevo casco de MR/VR en el mercado y parece que Skeuomorphism vuelve a devolverse. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>Simulador de trabajo: ejemplo de diseño de skeuomorphic VR

El [simulador de trabajo](https://jobsimulatorgame.com/), un juego de divertidos desarrollado por [Owlchemy Labs](https://owlchemylabs.com/) , es uno de los ejemplos más populares del diseño de skeuomorphic VR. Dentro de este juego, los jugadores se transportan en el futuro, donde los robots reemplazan a los seres humanos y los seres humanos visitan un museo para experimentar lo que le gustaría realizar tareas rutinarias en uno de cuatro trabajos diferentes: mecánico automático, chef de gourmet, encargado de la tienda u trabajador de oficina.

La ventaja de Skeuomorphism es clara. Los entornos y objetos conocidos de este juego ayudan a los nuevos usuarios de VR a sentirse más cómodos y presentan espacio virtual. También hace que se sientan como están en el control mediante la Asociación de conocimientos y comportamientos conocidos con objetos y sus reacciones físicas correspondientes. Por ejemplo, para beber una taza de café, las personas simplemente tienen que dirigirse al equipo de café, presionar un botón, captar el asa y inclinarlo hacia su boca como lo harían en el mundo real.

![el simulador de trabajo](images/job-simulator.gif)<br>
*Simulador de trabajo*

Dado que MR/VR sigue siendo un medio en desarrollo, es necesario usar un cierto grado de skeuomorphism para desrelacionar la tecnología MR/VR y para presentarla a audiencias de mayor tamaño en todo el mundo. Además, el uso de skeuomorphism o la representación realista puede ser beneficioso para tipos específicos de aplicaciones como cirugía o simulación de vuelo. Dado que el objetivo de estas aplicaciones es desarrollar y perfeccionar habilidades específicas que se pueden aplicar directamente en el mundo real, cuanto más se acerque la simulación al mundo real, mayor será la posibilidad de transferir la información.

Recuerde que skeuomorphism es solo un enfoque. El potencial del mundo MR/VR es mucho mayor que eso, y los diseñadores deben procurar crear interacciones mágicas hipernaturales, nuevas prestaciones que son exclusivas en el mundo MR/VR. Como inicio, considere la posibilidad de agregar las facultades mágicas a los objetos ordinarios para permitir que los usuarios cumplan sus deseos fundamentales, como teleportabilidad y Omniscience.

![de la puerta mágica (izquierda) y los zapatas de Ruby (derecha) de Doraemon](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*La puerta mágica (izquierda) y las zapatas de Ruby (derecha) de Doraemon*

### <a name="observations-about-skeuomorphism-in-vr"></a>Observaciones sobre skeuomorphism en VR

Desde "puerta de cualquier lugar" en Doraemon, "zapatas de Ruby" en el Asistente de oz a "mapa de Maurader" en Harry Potter, ejemplos de objetos ordinarios con una potencia mágica en la conocida ficción. Estos objetos mágicos nos ayudan a visualizar una conexión entre el mundo real y el fantástico, entre lo que y lo que podría ser. Tenga en cuenta que al diseñar el objeto mágico o surreal, es necesario conseguir un equilibrio entre funcionalidad y entretenimiento. Tenga cuidado con la tentación de crear algo tan mágico como para la novedad.

## <a name="understanding-different-input-methods"></a>Descripción de los distintos métodos de entrada

Cuando se diseñó para el medio 2D, tuve que centrarme en las interacciones táctiles, del mouse y del teclado para las entradas. En el espacio de diseño MR/VR, nuestro cuerpo se convierte en la interfaz y los usuarios pueden usar una selección más amplia de métodos de entrada: como voz, mira, gesto, [6-DOF controladores](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)y guantes que permiten una conexión directa e intuitiva con objetos virtuales.

![entradas disponibles en HoloLens](images/inputs.jpg)<br>
*Entradas disponibles en HoloLens*

> *"Todo lo mejor para algo y peor para algo".*<br>
> : [Bill Buxton comparte](https://www.billbuxton.com/)

Por ejemplo, la entrada de gestos con sensores de cámara y de mano en un dispositivo HMD libera a los usuarios de la posesión de controladores o la utilización de Sweaty guantes, pero el uso frecuente puede provocar fatiga física (a. k. a Gorilla ARM). Además, los usuarios deben mantener sus manos dentro de la línea de visión; Si la cámara no puede ver las manos, no se pueden usar las manos.

La entrada de voz es buena en el recorrido de tareas complejas porque permite a los usuarios desplazarse por los menús anidados con un comando (por ejemplo, "mostrarme las películas realizadas por Laika Studio") y también muy económico cuando se acoplan con otro tipo de moda (por ejemplo, el comando "facial me" orienta el holograma que un usuario mira hacia el usuario). Sin embargo, es posible que la entrada de voz no funcione bien en un entorno ruidoso o que no sea adecuada en un espacio muy silencioso.

Además de los gestos y la voz, los controladores de seguimiento de mano (por ejemplo, Oculus Touch, Naopak, etc.) son métodos de entrada muy populares porque son fáciles de usar, precisos, aprovechan los [proprioception](https://en.wikipedia.org/wiki/Proprioception)de los usuarios y proporcionan indicaciones de hápticos pasivas. Sin embargo, estas ventajas suponen el costo de no ser capaces de ser manos libres y usar el seguimiento completo de los dedos.

![Sensa (left) y Manus VR (right)](images/senso-and-manus-vr.jpg)<br>
*Sens (left) y Manus VR (right)*

Aunque no es tan popular como los controladores, los guantes están ganando tiempo de nuevo gracias a la ola de MR/VR. Más recientemente, la entrada de cerebro/mente comenzó a obtener la tracción como una interfaz para entornos virtuales mediante la integración del sensor de EEG o EMG en los auriculares (por ejemplo, [MINDMAZE VR](https://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>Observaciones sobre los métodos de entrada

Se trata de un solo ejemplo de dispositivos de entrada disponibles en el mercado para MR/VR. Continuarán proliferando hasta que el sector madura y acepte los procedimientos recomendados. Hasta entonces, los diseñadores deben seguir teniendo en cuenta los nuevos dispositivos de entrada y estar bien en los métodos de entrada específicos de su proyecto en particular. Los diseñadores deben buscar soluciones creativa dentro de las limitaciones y, al mismo tiempo, reproducirse en las fortalezas de un dispositivo.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>Esboce la escena y la prueba en el casco

Cuando trabajaba en 2D, principalmente esbozamos solo el contenido. Sin embargo, en el espacio de realidad mixta que no era suficiente. Tuve que esbozar toda la escena para imaginar mejor las relaciones entre el usuario y los objetos virtuales. Para ayudar a mi pensamiento espacial, comencé a esbozar escenas en [cine 4D](https://www.maxon.net/en/products/cinema-4d/overview/) y a veces crear recursos simples para la creación de prototipos en [Maya](https://www.autodesk.com/products/maya/overview/). Nunca he usado ninguno de los programas antes de unirse al equipo de HoloLens y sigo siendo un novato, pero trabajar con estos programas en 3D nos ayudó a familiarizarse con la nueva terminología, como el [sombreador](https://en.wikipedia.org/wiki/Shader) y la [IK (cinemática inversa)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/).

**"Independientemente de la profundidad de la escena en 3D, la experiencia real en el casco es casi nunca la misma que la del boceto. Por eso es importante probar la escena en los auriculares de destino. "— Hae Jin Lee**

En el caso de los prototipos de HoloLens, probé todos los tutoriales en [tutoriales de realidad mixta](tutorials.md) para comenzar. Empezaron a jugar con [HoloToolkit. Unity](https://github.com/Microsoft/HoloToolkit-Unity/) que Microsoft proporciona a los desarrolladores para acelerar el desarrollo de aplicaciones holográficas. Cuando me he quedado atascado, he publicado mi pregunta en la [pregunta de HoloLens & el foro de respuestas](https://forums.hololens.com/categories/questions-and-answers/).

Después de adquirir el conocimiento básico de la plataforma de prototipos de HoloLens, quería habilitar otros no codificadores en prototipo por su cuenta. He realizado un tutorial en vídeo que enseña cómo desarrollar un proyectil sencillo mediante HoloLens. Explicaremos brevemente los conceptos básicos, por lo que, aunque no tenga experiencia en el desarrollo de HoloLens, debería poder continuar.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*He realizado este sencillo tutorial para los programadores que no son de este tipo.*

En el caso de la creación de prototipos de VR, se tomaron cursos en la [escuela de desarrollo de VR](https://learn.vrdev.school/) y también se llevó a cabo la [creación de contenido 3D para la realidad virtual](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) en Lynda.com La escuela de desarrollo de VR proporcionó más información en profundidad en la codificación y el curso de Lynda me ofrecía una buena introducción a la creación de recursos para VR.

## <a name="take-the-leap"></a>Avance

Hace un año, me parecía que todo esto fue un poco abrumador. Ahora puedo indicarle que el esfuerzo de 100% merece la pena. MR/VR todavía es un medio muy joven y hay muchas posibilidades interesantes a la espera de ser realizadas. Me siento inspirado y la suerte de poder jugar a una pequeña parte del diseño del futuro. Espero que se una al camino en el espacio 3D.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>@Microsoft del diseñador de la experiencia del usuario</td>
</tr>
</table>

 
