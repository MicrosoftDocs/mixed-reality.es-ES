---
title: Usar sonido espacial en aplicaciones de realidad mixta
description: El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, sonido espacial, diseño, estilo
ms.openlocfilehash: 34923e1ebfc8e46ea8e67a4444fe3c2691efd4db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182015"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Cómo usar sonido en aplicaciones de realidad mixta

Puede usar el sonido para informar y reforzar el modelo mental del usuario del estado de la aplicación. Use la espacialización, cuando corresponda, para colocar sonidos en el mundo de la realidad mixta. Cuando conecte el auditor y el visual de esta manera, podrá profundizar en la naturaleza intuitiva de las interacciones y aumentar la confianza de los usuarios.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>Cuándo agregar sonidos
Las aplicaciones de realidad mixta suelen tener una mayor necesidad de sonido que las aplicaciones 2D, debido a su falta de una interfaz táctil. Agregue sonidos cuando informan al usuario o refuerzan las interacciones.

### <a name="inform-and-reinforce"></a>Informar y reforzar
* En el caso de los eventos que no son iniciados por el usuario, como las notificaciones, use el sonido para informar al usuario de que se ha producido un cambio.
* Las interacciones pueden tener varias fases. Use el sonido para reforzar las transiciones de fase.

Vea los siguientes ejemplos de interacciones, eventos y características de sonido sugeridos.

### <a name="exercise-restraint"></a>Retención de ejercicio
Los usuarios no tienen una capacidad ilimitada para la información de audio.
* Cada sonido debe comunicarse información específica y valiosa.
* Cuando la aplicación reproduce un sonido para informar al usuario, reduzca temporalmente el volumen de otros sonidos.
* En el caso de los sonidos de desplazamiento del botón (consulte la siguiente información), agregue un retardo para evitar la activación excesiva de sonido.

### <a name="dont-rely-solely-on-sounds"></a>No confíe únicamente en sonidos
Los sonidos que se usan bien son valiosos para los usuarios. Pero asegúrese de que la aplicación se pueda usar incluso con el sonido desactivado.
* Los usuarios pueden tener dificultades auditivas.
* La aplicación se puede usar en un entorno de alta intensidad.
* Los usuarios pueden tener problemas de privacidad u otros motivos para deshabilitar el audio del dispositivo.

## <a name="how-to-sonify-interactions"></a>Cómo sonify interacciones
Los tipos de interacción en la realidad mixta incluyen gestos, manipulación directa y voz. Use las siguientes características sugeridas para seleccionar o diseñar sonidos para estas interacciones.

### <a name="gesture-interactions"></a>Interacciones de gestos
En realidad mixta, los usuarios pueden interactuar con los botones mediante un mouse. Normalmente, las acciones de botón se producen cuando el usuario suelta en lugar de presionar el botón para dar al usuario la oportunidad de cancelar la interacción. Use sonidos para reforzar estas fases. Para ayudar a los usuarios a centrarse en botones distantes, considere también el uso de un sonido de desplazamiento del puntero.
* Botón: los sonidos de la prensa deben ser cortos y táctiles.<br/>Ejemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Button: "unpress" los sonidos deben tener una sensación similar. Un tono más alto que el sonido de la prensa refuerza el sentido de la finalización.<br/>Ejemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* En el caso de los sonidos del mouse, considere la posibilidad de usar un sonido sutil y no amenazante, como un thud o golpe de baja frecuencia.

### <a name="direct-manipulation"></a>Manipulación directa
En HoloLens 2, el seguimiento de mano articulado admite la manipulación directa de los elementos de la interfaz de usuario. Los sonidos son importantes cuando no hay otros comentarios físicos.

Un sonido de *presionar un botón* es importante en la manipulación directa porque el usuario no obtiene ninguna otra indicación cuando llega a la parte inferior del trazo de tecla. Los indicadores sonoros de viajes clave pueden ser pequeños, sutiles y ocluidos. Al igual que con las interacciones de gestos, las pulsaciones de botón deberían obtener un sonido corto y táctil, como un clic. Las desimprentas deben tener un sonido de clic similar pero con un tono elevado.
* Ejemplo: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Ejemplo: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

Es difícil confirmar visualmente una acción de captura o de lanzamiento. La mano del usuario suele estar en la forma de cualquier efecto visual y los objetos de cuerpo rígidos no tienen un aspecto visual del mundo real "captando". Los sonidos pueden comunicar eficazmente las interacciones de captación y versión correctas.
* Las acciones de captación deben tener un sonido de tacto corto y ligeramente silenciado que confiere la idea de cerrar los dedos alrededor de un objeto. A veces también hay un sonido "whoosh" que conduce hasta el sonido de captación para comunicar el movimiento de la mano.<br/>Ejemplo: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Las acciones de lanzamiento deben obtener un sonido de igual corta y táctil. Normalmente, es más baja que el sonido de la toma y en orden inverso, con un impacto y, a continuación, un "whoosh" para comunicar que el objeto está en su lugar.<br/>Ejemplo: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Una interacción de *dibujo* debe obtener un sonido persistente y en bucle cuyo volumen esté determinado por el movimiento de la mano del usuario. Debe ser silenciosa cuando la mano del usuario sigue siendo la más alta cuando la mano se mueve rápidamente.

### <a name="voice-interactions"></a>Interacciones de voz
A menudo, las interacciones de voz tienen elementos visuales sutiles. Use sonidos para reforzar las fases de interacción. Puede que desee usar sonidos más tonales para distinguirlos de los sonidos de gestos y manipulación directa.

* Use un tono de sonido positivo para las *confirmaciones*de comandos de voz. Los tonos ascendentes e intervalos musicales principales son eficaces.
* Use un tono de sonido menos corto y positivo para *errores*de comandos de voz. Evite sonidos negativos. En su lugar, use un sonido más percussive, que sea neutro para comunicar que la aplicación está pasando de la interacción.
* Si la aplicación tiene una palabra de reactivación, use un tono corto y suave cuando el dispositivo *empiece a escuchar*. Use un sonido de bucle sutil mientras la aplicación *está* escuchando.

### <a name="notifications"></a>Notificaciones
Las notificaciones comunican los cambios de estado de aplicación y otros eventos que no inicia el usuario, como finalizaciones de procesos, mensajes y llamadas telefónicas.

En realidad mixta, los objetos a veces salen del campo de vista del usuario. Acompañar *objetos animados* en movimiento con un sonido espacial que depende del tipo de objeto y la velocidad de movimiento.
* Ayuda a reproducir un sonido espacial al final de una animación para informar al usuario de la nueva posición del objeto.
* En el caso de movimientos graduales, un sonido "whoosh" durante el movimiento ayuda al usuario a realizar el seguimiento del objeto.

Los sonidos de la *notificación de mensajes* pueden escucharse repetidamente, a veces en una sucesión rápida. Es importante que no destaquen ni suenen muy intensos. Los sonidos tonales positivos de rango medio son eficaces.

* Los sonidos de llamada entrante deben tener cualidades similares a un tono de teléfono móvil. Normalmente, suelen repetir frases musicales que se reproducen hasta que el usuario responde a la llamada.
* La conexión y desconexión de comunicación de voz deben tener un sonido corto y tonal. El sonido de conexión debe ser un tono positivo para indicar que la conexión se ha realizado correctamente. El sonido de desconexión debe ser un sonido neutro para indicar la finalización de la llamada.

## <a name="handle-spatialization"></a>Controlar la espacialización
La espacialización utiliza auriculares o altavoces estéreo para colocar sonidos en el mundo de la realidad mixta.

### <a name="which-sounds-to-spatialize"></a>Qué sonidos se deben espacialar
Un sonido debe ser espacial cuando está asociado a un evento que tiene una ubicación espacial. Esto incluye la interfaz de usuario, las voces de Ia incorporadas y los indicadores visuales.

Spatial los elementos de la *interfaz de usuario* para ayudar a despejar el "espacio" de Sonic del usuario limitando el número de sonidos estéreo que escuchan. Las interacciones de manipulación como el toque, la captación y la liberación se sienten más naturales cuando se espaciales los comentarios de audio. Tenga en cuenta la siguiente información sobre la atenuación de distancia de estos elementos.

Enpole los *indicadores visuales* y *expresar las voces de AI* para informar a los usuarios de forma intuitiva cuando estas cosas están fuera del campo de la vista.
    
Por el contrario, evite la espacialización de *voces de Ia sin caras* y otros elementos que carecen de una ubicación espacial bien definida. La espacialización sin un elemento visual relacionado puede distraer a los usuarios pensando que hay un elemento visual que no pueden encontrar.

La espacialización incluye algún costo de la CPU. Muchas aplicaciones tienen como máximo dos sonidos que se reproducen simultáneamente. Lo más probable es que el costo de la espacialización en ese caso sea insignificante. Puede usar el monitor de velocidad de fotogramas de MRTK para juzgar el impacto de agregar la espacialización.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>Cuándo y cómo aplicar la atenuación basada en la distancia
En el mundo físico, los sonidos que están más lejos son más silenciosos. El motor de audio puede modelar esta atenuación en función de la distancia de origen. Use la atenuación basada en la distancia cuando comunique la información pertinente.

Las distancias a los *indicadores visuales*, los *hologramas animados*y otros sonidos informativos suelen ser relevantes para el usuario. Use la atenuación basada en la distancia para proporcionar indicaciones de manera intuitiva.

Ajuste la curva de atenuación de cada origen para ajustarse al tamaño de los espacios del mundo de la realidad mixta. La curva predeterminada del motor de audio suele estar pensada para espacios muy grandes (hasta el medio kilómetro).

Los sonidos que refuerzan las *fases progresivas de las acciones de botón* y otras interacciones no deben aplicar la atenuación. Los efectos de reforzamiento de estos sonidos suelen ser más importantes que la comunicación de la distancia con el botón. Las variaciones pueden distraerse, sobre todo con los teclados, cuando muchos clics de botón pueden escucharse en sucesión.

### <a name="which-spatialization-technology-to-use"></a>Qué tecnología de espacialidad usar
Con auriculares o altavoces HoloLens, use tecnologías de espacialización basadas en la función de transferencia relacionada con el encabezado (HRTF). Estas tecnologías modelan la propagación de sonido en torno al cabezal del mundo físico. Incluso cuando un origen de sonido está en el extremo de una cabeza, el sonido se propaga a la lengüeta distante con cierta atenuación y retraso. En cambio, el movimiento panorámico de los oradores solo se basa en la atenuación y aplica la atenuación total en el oído izquierdo cuando los sonidos están en el lado derecho (y viceversa). Esta técnica puede ser incómodo para los agentes de escucha de "audición normal" y ser inaccesible para los agentes de escucha que tienen dificultades auditivas en una lengüeta.

## <a name="next-steps"></a>Pasos siguientes
* [Uso de sonido espacial en Unity](spatial-sound-in-unity.md)
* [Caso práctico de Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Caso práctico de HoloTour](case-study-spatial-sound-design-for-holotour.md)
