---
title: Manipulación directa con manos
description: Información general sobre el modelo de entrada de la manipulación directa
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixto en realidad, mirada, mirada como destino, interacción, diseñar, manos cerca, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402393"
---
# <a name="direct-manipulation-with-hands"></a>Manipulación directa con manos
La manipulación directa es un modelo de entrada que implica tocar hologramas directamente con las manos. La manipulación directa, el objetivo es que los objetos se comportan igual que en el mundo real. Botones que se pueden activar simplemente presionándolos, los objetos se pueden seleccionarlos contratiempos y contenido 2D se comporta como una pantalla táctil virtual.  Por este motivo, dirigir es fácil para los usuarios obtener información sobre la manipulación, así como de la diversión demasiado.  Se considera un "cerca de" modelo de entrada, lo que significa que está concebida para interactuar con el contenido que está dentro de brazos llegar.

Manipulación directa es la prestación de la base, lo que significa que es fácil de usar. No hay ningún gestos simbólicos a enseñar a los usuarios. Todas las interacciones se basan en un elemento visual que puede tocar ni tomar.

## <a name="device-support"></a>Compatibilidad con dispositivos


| Modelo de entrada | [HoloLens (gen 1)](hololens-hardware-details.md) | HoloLens 2 |[Inmersivos](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| Manipulación directa con manos | ❌ No compatible | ✔️ Recomendado | ➕ Una alternativa, [elija y confirme con manos](point-and-commit.md) se recomienda.

Manipulación directa es un modelo de entrada principal en HoloLens 2 y usa el nuevo sistema de seguimiento de la mano articulado. El modelo de entrada también está disponible en inmersivos mediante el uso de los controladores de movimiento, pero no se recomienda como medio principal de interacción fuera de la manipulación del objeto.  Dirigir manipluation no está disponible en HoloLens (gen 1).


## <a name="collidable-fingertip"></a>Yema collidable

En HoloLens 2, se reconoce manos real del usuario y se interpretan como modelos de esqueleto mano izquierda y derecha. Para implementar la idea de tocar hologramas directamente con las manos, idealmente, 5 colisionadores se podrían conectar a 5 alcance de cada modelo de esqueleto de la mano. Sin embargo, en la práctica, debido a la falta de comentarios al tacto, 10 alcance collidable provocó colisiones inesperadas e impredecibles con hologramas. 

Por lo tanto, se recomienda para poner solo un colisionador en cada dedo índice. El alcance del índice collidable todavía puede actuar como puntos de toque activa para los gestos de toque diverso que implican otro dedo, por ejemplo, presione un dedo 1, 1-dedo tap, presione un dedo 2 y 5 dedo press, tal como se muestra en la imagen siguiente.

![Imagen de la yema del dedo collidable](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a>Colisionador esfera

En lugar de una forma genérica aleatoria, se recomienda usar un colisionador esfera y para representar visualmente para proporcionar indicaciones mejores para dirigirse a casi. Diámetro de la esfera debe coincidir con el grosor del dedo índice para aumentar la precisión de toque. Será fácil recuperar la variable de grosor dedo mediante una llamada a la API de mano.

### <a name="fingertip-cursor"></a>Cursor de la yema del dedo

Además de representar una esfera de la yema del dedo índice collidable, hemos creado una solución avanzada, cursor yema, para lograr una mejor experiencia orientado a cerca de interactivamente. Es un cursor en forma de anillo asociado en la yema del dedo índice. Según la proximidad, dinámicamente reacciona a un destino en términos de orientación y el tamaño como se detalla a continuación:

* Cuando se mueve un dedo índice hacia un holograma, el cursor siempre es parecido a la superficie del holograma y gradualmente reduce su tamaño.
* Tan pronto como el dedo toque la superficie, el cursor se reduce en un punto y emite un evento de toque.

Con la información interactiva, los usuarios puedan lograr alta precisión cerca de destinatarios de tareas, como desencadenar un hipervínculo en el contenido web o al presionar un botón, como se muestra a continuación. 

![Imagen del cursor yema del dedo](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a>Cuadro de límite con el sombreador de proximidad

Holograma de sí mismo también requiere la capacidad de proporcionar comentarios visuales y de audio para compensar la falta de comentarios al tacto. Para eso, generamos el concepto de un rectángulo con el sombreador de proximidad. Un cuadro de límite es una superficie mínima volumétrica que rodea a un objeto 3D. El rectángulo tiene un mecanismo de representación interactiva denominado a sombreador de proximidad. Se comporta el sombreador de proximidad:

* Cuando el dedo índice está dentro del intervalo, se convierte un foco yema del dedo en la superficie del cuadro de límite.
* Cuando se aproxime la yema del dedo a la superficie, destacados condensa según corresponda.
* Tan pronto como la yema del dedo toque la superficie, todo el rectángulo de selección cambia el color o generar un efecto visual para reflejar el estado de toque.
* Mientras tanto, se puede activar un efecto de sonido para mejorar los comentarios de visual táctil.

![Cuadro de límite con la imagen del sombreador de proximidad](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a>Botón pressable

Con el dedo collidable, los usuarios ahora están listos para interactuar con el componente holográfico muy fundamental de la interfaz de usuario, botón pressable. Un botón pressable es un holográfica adaptada de presionar el dedo directa. Nuevamente, debido a la falta de comentarios al tacto, un botón pressable proporciona dos mecanismos para abordar problemas relacionados con comentarios al tacto.

* El primer mecanismo es un rectángulo con el sombreador de proximidad, detallado en la sección anterior. Sirve para proporcionar un mejor sentido de proximidad a los usuarios enfocar y asegúrese de contacto con un botón.
* La segunda es la depresión. Crea sensación de prensa, después de un dedo pone en contacto con el botón. El mecanismo es que el botón se mueve estrechamente con el dedo en el eje de profundidad. El botón puede activarse cuando alcanza una profundidad designada (al presionar) o se sale de la profundidad (en lanzamiento) después de pasar a través de él.
* El efecto de sonido se debe agregar para mejorar los comentarios, cuando se activa el botón.

![Imagen del botón pressable](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a>Interacción de pizarra 2D

Una pizarra 2D es un contenedor holográfico hospedar contenido de la aplicación 2D, como explorador web. El concepto de diseño para interactuar con una pizarra 2D a través de la manipulación directa es aprovechar el modelo mental de interactuar con una pantalla táctil físico.

Para interactuar con el contacto Pizarra:

* Utilice un dedo índice presionar un botón o un hipervínculo.
* Utilice un dedo índice desplazar una pizarra contenido hacia arriba y abajo.
* Los usuarios usar dos dedos de índice para aumentar y reducir el contenido de pizarra según movimiento relativo de los dedos.

![Imagen de pizarra 2D](images/2D-Slate-Interaction-720px.jpg)

Para manipular la 2D Pizarra propio:

* Aborde las manos hacia las esquinas y bordes para revelar la factibilidad de manipulación más cercano.
* Agarre la factibilidad de manipulación y realizar un escalado uniforme a través de las prestaciones de la esquina y reflujo a través de las prestaciones de edge.
* Arrastre el holobar en la parte superior de la Pizarra 2D, lo que le permite mover la Pizarra toda.

![Imagen de pizarra manipulación](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a>Manipulación del objeto 3D

HoloLens 2 permite que permite a los usuarios habilitan sus manos dirigir manipular objetos 3D hologramphic aplicando un cuadro de límite para cada objeto 3D. El cuadro de límite proporciona una mejor percepción de profundidad a través de su sombras de proximidad. Con el cuadro de límite, hay dos enfoques de diseño para la manipulación del objeto 3D.

### <a name="affordance-based-manipulation"></a>Manipulación de prestación

Esto le permite manipular el objeto 3D a través de un cuadro de límite y la factibilidad de manipulación alrededor de ella. Tan pronto como parte de un usuario está a punto de un objeto 3D, se revelan el cuadro de límite y la prestación más cercano. Los usuarios pueden tomar el cuadro de límite para mover todo el objeto, la factibilidad de borde se va a girar y las prestaciones de la esquina para escalar de manera uniforme.

![Imagen de manipulación del objeto 3D](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a>No prestación en función de manipulación

En este mecanismo, no se asocia ninguna prestación en el cuadro de límite. Los usuarios pueden revelar sólo el rectángulo de selección y luego interactuar directamente con él. Si el cuadro de límite se obtiene con una mano, la traslación y rotación del objeto se asocian a movimiento y la orientación de la mano. Cuando el objeto se obtiene con dos manos, los usuarios pueden trasladar, escalar y girarlo según los movimientos relativos de dos manos.

Manipulación concreta requiere la precisión, se recomienda que use **manipulación de prestación**, ya que proporciona un alto nivel de granularidad. Para la manipulación flexible, le recomendamos que usa **manipulación no prestación** es porque permite que las experiencias de instantáneas y divertidas.

## <a name="instinctual-gestures"></a>Gestos instinctual

Con HoloLens (gen 1), se enseñan los usuarios un par gestos predefinidos, como Bloom y puntee en el aire. Para HoloLens 2, no pedimos a los usuarios que memorizar los gestos simbólicos. Todos los gestos de usuario necesarios, los usuarios deben interactuar con hologramas y el contenido, son instinctual. Es la forma de lograr gesto instinctual guiar a los usuarios para llevar a cabo movimientos con el diseño de prestaciones de la interfaz de usuario.

Por ejemplo, si le animamos a que arrastre un objeto o un punto de control con pinch dos dedos, el objeto o el punto de control debe ser pequeño. Si queremos realizar cinco grab del dedo, el objeto o el punto de control debería ser relativamente grande. Al igual que los botones, un botón pequeño limitaría usuarios, haga clic con un solo dedo, mientras que un botón enorme insto a los usuarios presionen con sus palmas.

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>Diseño simétrica entre manos y controladores GDL 6

Es posible que haya observado que ahora hay parallels interacción que podemos dibujar entre manos en los controladores VR AR y movimiento. Las dos entradas pueden usarse para desencadenar manipulaciones en sus respectivos entornos. En el 2 de HoloLens, hacerlo y arrastre las manos de un works corta distancia mucho en la misma manera que el botón de agarre hace en los controladores de movimiento en WMR. Esto proporciona a los usuarios con la familiaridad de la interacción entre las dos plataformas y puede resultar útil si alguna vez decide portar tu aplicación de uno a otro.

## <a name="optimize-with-eye-tracking"></a>Optimizar el seguimiento de los ojos

Si funciona según lo previsto, pero puede volverse rápidamente también frustrante si no se puede mover la mano en cualquier parte ya sin desencadenar involuntariamente un holograma, puede sentirse mágica manipulación directa.
Seguimiento de los ojos potencialmente pueden ayudar a identificar mejor lo que es la intención del usuario.

* **When**: Reducir falsamente desencadenar una respuesta de manipulación. Permite entender mejor lo que un usuario esté implicado actualmente con seguimiento de los ojos.
Por ejemplo, imagine que está leyendo a través de un texto (informativo) holográfica al alcanzar otra vez para obtener la herramienta de trabajo reales.

Al hacerlo, accidentalmente mover la mano a través de algunos botones holográfica interactivos que incluso no vio antes (por ejemplo, era incluso fuera campo de visión del usuario en el (FOV)).

  Para hacer el cuento corto: Si el usuario no ha visto un holograma durante un tiempo, pero se ha detectado un evento táctil o entender para él, es probable que el usuario realmente indebida interactuar con ese holograma.

* **Cuál**:  Aparte de direccionamiento activaciones positivas falsas, otro ejemplo incluye la identificación de mejor qué hologramas para captar o echar un vistazo que no puede ser el punto de intersección precisa claro desde su perspectiva sobre todo si se colocan varias hologramas cerca de cada uno Otro.

  Mientras que realizar un seguimiento de ojos en HoloLens 2 tiene una limitación determinada acerca de cómo con precisión puede determinar ocular a mirada, esto todavía puede ser muy útil para casi interacciones debido a la disparidad de profundidad al interactuar con la mano de entrada.  Esto significa que a veces es difícil determinar si la mano es detrás o delante un holograma precisamente por ejemplo a tomar un widget de manipulación.

* **Dónde**: Información de uso sobre lo que un usuario está viendo con quick - produce los gestos. Tome un holograma y aproximadamente lo meter hacia su destino previsto.  

    Aunque esto es posible que a veces funciona perfectamente, rápidamente realizar gestos de mano puede dar lugar destinos muy imprecisos. Esto es donde rastreo ocular podría ayudar a al inclinar la mano producir vector de vuelta a la posición deseada.

## <a name="see-also"></a>Vea también

* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)

