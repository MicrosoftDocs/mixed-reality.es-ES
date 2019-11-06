---
title: Usar sonido en aplicaciones de realidad mixta
description: El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, sonido espacial, diseño, estilo
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641064"
---
# <a name="using-sound-in-mixed-reality-applications"></a>Usar sonido en aplicaciones de realidad mixta

Use el sonido para informar y reforzar el modelo mental del usuario del estado de la aplicación. Use la espacialización, cuando corresponda, para colocar sonidos en el mundo mixto. La conexión del Auditor y el visual de esta manera profundiza en la naturaleza intuitiva de muchas interacciones y da lugar a una mayor confianza del usuario.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>¿Cuándo debo agregar sonidos?
Las aplicaciones de realidad mixta suelen tener una mayor necesidad de sonidos que las aplicaciones en una pantalla 2D, debido a la falta de una interfaz física. Los sonidos deben agregarse cuando informan al usuario o refuerzan las interacciones.

### <a name="inform-and-reinforce"></a>Informar y reforzar
* En el caso de los eventos no iniciados por el usuario, como las notificaciones, considere la posibilidad de agregar sonidos para informar al usuario de que se ha producido un cambio.
* Las interacciones pueden tener varias fases. Considere la posibilidad de usar sonidos para reforzar las transiciones de fase.

A continuación se muestran ejemplos de interacciones, eventos y características de sonido sugeridos.

### <a name="exercise-restraint"></a>Retención de ejercicio
Los usuarios no tienen una capacidad ilimitada para la información de audio:
* Cada sonido debe comunicarse con datos valiosos específicos
* Al reproducir sonidos diseñados para informar al usuario, reducir temporalmente el volumen de otros sonidos
* En el caso de los sonidos de desplazamiento del botón (ver más abajo), agregue un retardo para evitar la activación excesiva de los sonidos

### <a name="dont-rely-solely-on-sounds"></a>No confíe únicamente en sonidos
Los sonidos que se usan bien serán valiosos cuando los usuarios puedan escucharlos, pero asegúrese de que la aplicación se pueda usar incluso con el sonido desactivado.
* Los usuarios pueden tener dificultades auditivas
* La aplicación se puede usar en un entorno de alta intensidad
* Los usuarios pueden tener privacidad u otros motivos para deshabilitar el audio del dispositivo

## <a name="how-should-i-sonify-interactions"></a>¿Cómo debo sonify interacciones?
Los tipos de interacción en la realidad mixta incluyen gestos, manipulación directa y voz. Use las siguientes características sugeridas para seleccionar o diseñar sonidos para estas interacciones.

### <a name="gesture-interactions"></a>Interacciones de gestos
En realidad mixta, los usuarios pueden interactuar con los botones mediante un cursor. Normalmente, las acciones de botón se realizan cuando el usuario ha soltado el botón, en lugar de cuando se ha presionado, para permitir que el usuario cancele la interacción. Use sonidos para reforzar estas fases. Además, para ayudar a los usuarios a centrarse en botones distantes, considere la posibilidad de usar un sonido de desplazamiento del cursor.
* Los sonidos de la pulsación de botones deben tener un clic corto y táctil. Ejemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* El botón despresionar sonidos debe tener una sensación similar. El hecho de tener un tono elevado frente al sonido de la prensa refuerza el sentido de la finalización. Ejemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* En el caso de los sonidos, considere la posibilidad de usar un sonido sutil y no amenazante, como un thud o golpe de baja frecuencia.


### <a name="direct-manipulation"></a>Manipulación directa
En HoloLens 2, el seguimiento de mano articulado admite la manipulación directa de los elementos de la interfaz de usuario. Los sonidos son reemplazos importantes para la falta de comentarios físicos.

Un sonido de **presionar un botón** es importante en la manipulación directa porque el usuario no tiene la indicación física de cuándo ha alcanzado la parte inferior del viaje de la clave. Los indicadores visuales de viajes clave pueden ser pequeños, sutiles y ocluidos. Al igual que con las interacciones de gestos, las pulsaciones de botón deben tener un sonido corto y táctil, como un clic, y las desimprentas deben tener un clic similar con un tono elevado.
* Ejemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Ejemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

La confirmación de una **captura** o **lanzamiento** en la manipulación directa es difícil de comunicarse visualmente. A menudo, la mano del usuario estará en la forma de cualquier efecto visual y los objetos de cuerpo rígido no tienen un aspecto visual del mundo real de "captación". En cambio, los sonidos pueden comunicar eficazmente las interacciones de captación y versión correctas.
* Las acciones de captación deben tener un sonido de tacto corto y de un solo silenciado que confiere la idea de cerrar los dedos alrededor de un objeto. A veces, esto va acompañado de un sonido "whoosh" que conduce al impacto del sonido para comunicar el movimiento de la mano al captarla. Ejemplo: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Las acciones de lanzamiento deben tener un sonido similar y de corta duración, que normalmente se han interrumpido del sonido de la toma y en un orden inverso en el tiempo, con un impacto y, a continuación, un "whoosh" para comunicar el objeto que se está deteniendo en su lugar. Ejemplo: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Una interacción de **dibujo** debe tener un sonido persistente en bucle que tenga su volumen controlado por el movimiento de la mano del usuario, de modo que sea completamente silencioso cuando el usuario todavía esté disponible y en su volumen máximo cuando la mano del usuario se mueva rápidamente.



### <a name="voice-interactions"></a>Interacciones de voz
A menudo, las interacciones de voz tienen elementos visuales sutiles. Refuerce las fases de interacción con sonidos. Considere la posibilidad de elegir más sonidos tonales para distinguirlos de los sonidos de manipulación y de gestos directos.

* Use un tono de sonido positivo para las **confirmaciones**de comandos de voz. En este momento, los tonos que aumentan y los principales intervalos musicales son eficaces.
* Use un tono de sonido más corto y menos positivo para el **error**de comando de voz. Evite sonidos negativos; en su lugar, use un sonido neutro más percussive para comunicar que la aplicación está pasando de la interacción.
* Si la aplicación usa una palabra de reactivación, use un tono corto y suave cuando el dispositivo haya **empezado a escuchar**y un sonido de bucle sutil mientras la aplicación realiza escuchas. 

### <a name="notifications"></a>Notificaciones
Las notificaciones comunican los cambios de estado de la aplicación y otros eventos no iniciados por el usuario, como finalizaciones de procesos, mensajes y llamadas.

En realidad mixta, los objetos que se mueven pueden salir del campo de vista del usuario. Acompañar **objetos animados** con un sonido espacial que dependa del objeto y la velocidad de movimiento.
* También ayuda a reproducir un sonido espacial al final de una animación para informar al usuario de la nueva posición.
* En el caso de movimientos graduales, un sonido "whoosh" durante el movimiento ayudará al usuario a realizar el seguimiento del objeto.

Las **notificaciones de mensajes** probablemente se escucharán varias veces y, a veces, en una sucesión rápida. Es importante que no resalte ni suene demasiado intenso. Los sonidos tonales positivos de rango medio son efectivos aquí.

* Las llamadas deben tener calidades similares a las de un tono de teléfono móvil. Normalmente, suelen repetir frases musicales que se reproducen hasta que el usuario ha respondido a la llamada.
* La conexión y desconexión de comunicación de voz deben tener un sonido corto y tonal. El sonido de conexión debe tener un tono positivo, que indica que la conexión se ha realizado correctamente, mientras que el sonido de desconexión debe ser un sonido neutro que indica la finalización de la llamada.

## <a name="spatialization"></a>Espacialización
La espacialización utiliza auriculares o altavoces estéreo para colocar sonidos en el mundo mixto.

### <a name="which-sounds-should-i-spatialize"></a>¿Qué sonidos debo espacialar?
Un sonido debe ser espacial cuando está asociado a un evento que tiene una ubicación espacial. Esto incluye la interfaz de usuario, las voces de Ia incorporadas y los indicadores visuales.

La espacialización de los elementos de la **interfaz de usuario** ayuda a despejar el "espacio" de Sonic del usuario limitando el número de sonidos estéreo bloqueados a sus cabezas. Especialmente en las interacciones de manipulación directa, tocar, captar y soltar es más natural cuando se espacialen los comentarios de audio. Sin embargo, vea a continuación la atenuación de distancia de estos elementos.

La espacialización de **indicadores visuales** y la información sobre las voces de AI informa de forma intuitiva a los usuarios cuando están fuera del campo de la vista.
    
Por el contrario, evite la espacialización de voces de Ia sin **_caras_** y otros elementos sin una ubicación espacial bien definida. La espacialización sin un elemento visual relacionado puede distraer a los usuarios pensando que hay un elemento visual que no puede encontrar.

La adición de la espacialidad conlleva cierto costo de la CPU. Muchas aplicaciones tendrán, como máximo, dos sonidos que se reproducen simultáneamente. El costo de la espacialización en ese caso puede ser insignificante. Puede usar el monitor de velocidad de fotogramas de MRTK para juzgar el impacto de agregar la espacialización. 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>¿Cuándo y cómo se debe aplicar la atenuación basada en la distancia?
En el mundo físico, los sonidos que están más lejos son más silenciosos. El motor de audio puede modelar esta atenuación en función de la distancia de origen. Use la atenuación basada en la distancia cuando comunique la información pertinente.

Las distancias a los **indicadores visuales**, los **hologramas animados**y otros sonidos informativos suelen ser relevantes para el usuario. Use la atenuación basada en la distancia para proporcionar esta indicación de manera intuitiva.
* Ajuste la curva de atenuación de cada origen para ajustarse al tamaño de los espacios universales mixtos. La curva predeterminada del motor de audio suele estar pensada para espacios muy grandes (hasta el medio kilómetro).

Los sonidos que refuerzan las **fases progresivas de los botones** y otras interacciones no deben aplicar la atenuación. Los efectos de reforzamiento de estos sonidos suelen ser más importantes que la comunicación de la distancia con el botón. Las variaciones pueden distraerse, especialmente con los teclados, en los que muchos clics de botones se escucharán sucesivamente.

### <a name="which-spatialization-technology-should-i-use"></a>¿Qué tecnología de espacialidad debo usar?
Al usar auriculares o altavoces HoloLens, use tecnologías de espacialización basadas en HRTF (función de transferencia relacionada con el cabezal). Modelan la propagación de sonido en torno al cabezal del mundo físico. Incluso cuando un origen de sonido está lejos de un lado del cabezal, el sonido se propaga a la lengüeta distante con cierta atenuación y retraso. En cambio, el movimiento panorámico de los oradores solo se basa en la atenuación y aplica la atenuación total en el lengüeta izquierdo cuando los sonidos están en el lado derecho (y viceversa). Esto puede resultar incómodo para los agentes de escucha de audición normal y no accesible para los agentes de escucha con deficiencias auditivas en una lengüeta.

## <a name="next-steps"></a>Pasos siguientes
* [Uso de sonido espacial en Unity](spatial-sound-in-unity.md)
* [Caso práctico de Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Caso práctico de HoloTour](case-study-spatial-sound-design-for-holotour.md)

