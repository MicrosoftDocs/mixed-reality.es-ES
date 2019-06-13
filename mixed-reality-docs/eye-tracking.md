---
title: Seguimiento de los ojos
description: Seguimiento de los ojos
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Eye Tracking, Mixed Reality, Input, Eye Gaze
ms.openlocfilehash: 7298a34a946f86aaf789cfe44ad971169fc8ece3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66453704"
---
# <a name="eye-tracking-on-hololens-2"></a>Seguimiento de los ojos en HoloLens 2
HoloLens 2 ofrece un nivel completamente nuevo de conocimiento del contexto y del comportamiento humano dentro de la experiencia holográfica al proporcionar a los desarrolladores la increíble capacidad de usar información sobre lo que están mirando los usuarios. Esta página proporciona información general sobre cómo pueden aprovechar los desarrolladores el seguimiento de los ojos para varios casos de uso y qué debe tenerse en cuenta al diseñar interfaces de usuario basadas en la mirada con los ojos. 

## <a name="use-cases"></a>Casos de uso
El seguimiento de los ojos permite a las aplicaciones realizar un seguimiento de dónde mira el usuario en tiempo real. En esta sección se describen algunos de los posibles casos de uso y las interacciones novedosas que son posibles mediante el seguimiento de los ojos en la realidad mixta.
Antes de comenzar, a continuación se mencionará [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) varias veces, ya que proporciona varios ejemplos interesantes y eficaces para usar el seguimiento de los ojos, como la selección rápida y sin esfuerzo de objetivos mediante los ojos y el desplazamiento automático por texto en función de dónde mira el usuario. 

### <a name="user-intent"></a>Intención del usuario    
La información acerca de dónde mira un usuario proporciona un potente **contexto para otras entradas**, como las de voz, manos y controlador.
Esta información puede utilizarse para varias tareas.
Por ejemplo, puede servir para **enfocar** rápidamente y sin esfuerzo objetivos por la escena solo con mirar un holograma y decir "Seleccionar" (consulta también [Mirada con la cabeza y confirmación](gaze-and-commit.md)) o para decir "Coloca esto..." y, a continuación, mirar al lugar donde deseas colocar el holograma y decir "...ahí". Puedes consultar varios ejemplos en [Mixed Reality Toolkit: Selección de objetivos con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) y [Mixed Reality Toolkit: Posicionamiento de objetivos con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Otro ejemplo relacionado con la intención del usuario es usar la información sobre lo que mira el usuario para mejorar la interacción con agentes virtuales integrados y hologramas interactivos. Por ejemplo, los agentes virtuales pueden adaptar las opciones disponibles y su comportamiento según el contenido visualizado en cada momento. 

### <a name="implicit-actions"></a>Acciones implícitas
La categoría de acciones implícitas está estrechamente relacionada con la intención del usuario.
La idea es que los hologramas o los elementos de la interfaz de usuario reaccionen de manera prácticamente instintiva, de modo que casi no parezca que el usuario interactúa con el sistema, sino que el sistema y el usuario están sincronizados. Un ejemplo muy eficaz es el del **desplazamiento automático basado en la mirada con los ojos**. La idea es muy sencilla: El usuario lee un texto y puede seguir leyendo. El texto se mueve hacia arriba gradualmente para que el usuario pueda seguir leyendo. Un aspecto clave es que la velocidad de desplazamiento se adapta a la velocidad de lectura del usuario.
Otro ejemplo es el **zoom y el desplazamiento lateral con los ojos** que hace que el usuario sienta que se dirige exactamente hacia donde enfoca. La activación del zoom y el control de su velocidad pueden realizarse con la voz o manualmente, lo que resulta importante para transmitir una sensación de control y evitar abrumar al usuario (más adelante se describen con más detalle estas directrices de diseño). Tras acercar la imagen con el zoom, el usuario puede seguir de manera fluida, por ejemplo, el curso de una calle para explorar su vecindario simplemente mirando con los ojos.
Puedes consultar ejemplos de demostración de estos tipos de interacciones en el ejemplo [Mixed Reality Toolkit - Navegación con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

A continuación, se indican algunos otros casos de uso para _acciones implícitas_:
- **Notificaciones inteligentes:** ¿Te molesta que aparezcan notificaciones justo donde estabas mirando? La experiencia puede mejorar si se tiene en cuenta dónde está centrando el usuario su atención en cada momento. Muestra notificaciones desplazadas de donde está mirando actualmente el usuario para limitar las distracciones y ciérralas automáticamente una vez leídas. 
- **Hologramas atentos:** Hologramas que reaccionan sutilmente cuando se les mira. Pueden ser elementos de la interfaz de usuario que brillan ligeramente, una flor que se abre lentamente o una mascota virtual que te devuelve la mirada o evita el contacto visual tras mirarla durante un tiempo. Esto puede proporcionar una interesante sensación de conectividad y satisfacción en la aplicación.

### <a name="attention-tracking"></a>Seguimiento de la atención   
La información acerca de dónde miran los usuarios es una herramienta increíblemente eficaz para evaluar la utilidad de diseños e identificar problemas en flujos de trabajo eficientes. Actualmente, los análisis y la visualización con seguimiento de los ojos ya son una práctica habitual en varias áreas de aplicación. Con HoloLens 2, proporcionamos una nueva dimensión de este conocimiento, ya que es posible situar hologramas 3D en contextos reales y evaluarlos en esas situaciones. [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) proporciona ejemplos básicos para el registro y la carga de datos de seguimiento de los ojos y cómo visualizarlos.

Algunas aplicaciones en esta área son las siguientes: 
-   **Visualización de mirada con los ojos remota:** Visualiza lo que están mirando colaboradores remotos para, por ejemplo, asegurarte de que las instrucciones se entienden y siguen correctamente.
-   **Estudios de investigación con usuarios:** El seguimiento de la atención puede usarse para comparar la manera en que los usuarios inexpertos y los expertos analizan visualmente contenido o su coordinación ojo-mano en tareas complejas (por ejemplo, al analizar datos médicos o al manejar maquinaria).
-   **Entrenamiento de simulaciones y supervisión del rendimiento:** Practica y optimiza la ejecución de tareas mediante una identificación de cuellos de botella más eficaz en el flujo de ejecución.
-   **Evaluaciones de diseño, publicidad y estudios de mercado:** El seguimiento de los ojos es una herramienta común en estudios de mercado para evaluar los diseños de productos y sitios web.

### <a name="additional-use-cases"></a>Casos de uso adicionales
- **Videojuegos:** ¿Alguna vez has deseado tener superpoderes? Esta es tu oportunidad. Haz que los hologramas leviten con solo mirarlos. Dispara rayos láser con los ojos. Congela a tus enemigos o conviértelos en piedra. Usa tu visión de rayos X para explorar edificios. El límite es tu imaginación.  

- **Avatares expresivos:** El seguimiento de los ojos ayuda a conseguir avatares 3D más expresivos mediante el uso de datos de seguimiento de ojos en vivo para animar los ojos del avatar de forma que indiquen lo que el usuario está mirando actualmente. Además, aporta más expresividad mediante guiños y parpadeos. 

- **Entrada de texto:** El seguimiento de los ojos puede ser una alternativa interesante para introducir texto sin esfuerzo, especialmente cuando no es práctico usar la voz o las manos. 


## <a name="eye-tracking-api"></a>API de seguimiento de los ojos
Antes de entrar en detalles sobre las directrices de diseño específicas para la interacción de mirada con los ojos, expondremos brevemente las funcionalidades que ofrece el seguidor de ojos de HoloLens 2. La [API de seguimiento de los ojos](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) es accesible mediante: `Windows.Perception.People.EyesPose`. Proporciona un único haz de mirada con los ojos (origen y dirección de la mirada) a los desarrolladores.
El seguidor de ojos proporciona datos a _30 FPS_ aproximadamente.
La mirada con los ojos prevista se encuentra a entre 1 y 1,5 grados aproximadamente en ángulo visual en torno al objetivo enfocado. Caben esperar pequeñas imprecisiones, por lo que debe dejarse algo de margen para este valor límite inferior. Más adelante se tratará este aspecto en detalle. Para que el seguimiento de los ojos funcione con precisión, cada usuario debe realizar una calibración de seguimiento de los ojos. 

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de objetivo óptimo a una distancia de 2 metros*


## <a name="eye-gaze-design-guidelines"></a>Directrices para el diseño de mirada con los ojos
La creación de una interacción que aproveche el enfoque de los ojos en rápido movimiento puede ser complicada. En esta sección, se resumen las principales ventajas y desafíos que tener en cuenta al diseñar la aplicación. 

### <a name="benefits-of-eye-gaze-input"></a>Ventajas de la entrada mediante mirada con los ojos
- **Señalización a alta velocidad.** El músculo ocular es el que más rápido reacciona en el cuerpo humano. 

- **Poco esfuerzo.** Prácticamente no se necesita ningún movimiento físico. 

- **Implícito.** La información sobre los movimientos oculares de un usuario permite al sistema saber con qué objetivo planea interactuar el usuario, lo que suele describirse como "leer la mente". 

- **Canal de entrada alternativo.** La mirada con los ojos puede ofrecer una entrada eficaz alternativa a las entradas con la mano y con la voz, respaldada por años de experiencia de usuarios basada en su coordinación ojo-mano.

- **Atención visual.** Otra ventaja importante es la posibilidad de deducir a qué presta atención un usuario. Esto puede resultar útil en varias áreas de aplicación, como para evaluar más eficazmente diseños diferentes o para crear interfaces de usuario más inteligentes y mejorar indicaciones sociales para comunicación remota.

En pocas palabras, el uso de la mirada con los ojos como entrada ofrece potencialmente una señal contextual rápida y sin esfuerzo. Esto es especialmente eficaz en combinación con otras entradas, como la de *voz* y la *manual*, para confirmar la intención del usuario.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafíos de la mirada con los ojos como entrada
Un gran poder conlleva una gran responsabilidad: Aunque la mirada con los ojos puede usarse para crear experiencias mágicas en las que el usuario puede sentirse como un superhéroe, también es importante saber en qué casos no resulta tan eficaz para tener esto en cuenta cuando corresponda. A continuación, se describen algunos *desafíos* que tener en cuenta y cómo abordarlos al trabajar con la entrada mediante mirada con los ojos: 

- **La mirada con los ojos "siempre está activada".** En el momento en el que abres los párpados, los ojos comienzan a fijar cosas por el entorno. Si se reacciona a cada cosa que miras, con la posibilidad de que se desencadenen acciones por error porque has mantenido la mirada sobre algo demasiado tiempo, la experiencia resultaría terrible.
Por esta razón, se recomienda combinar la mirada con los ojos con un *comando de voz*, un *gesto con la mano*, un *clic de botón* o con permanencia prolongada para desencadenar la selección de un objetivo.
Esta solución también admite un modo en que el usuario puede mirar libremente sin la abrumadora sensación de desencadenar involuntariamente algo. Esta cuestión también debe tenerse en cuenta al diseñar la información visual y auditiva que se recibe con solo mirar a un objetivo.
No debe sobrecargarse al usuario con efectos emergentes inmediatos o sonidos al pasar sobre los elementos. La clave es la sutileza. Más adelante, en las recomendaciones de diseño, se describen algunos de los procedimientos recomendados para esto.

- **Observación frente a control.** Supón que deseas alinear una fotografía con la pared de forma precisa. Miras los bordes y la zona circundante para ver si está bien alineada. Ahora imagina cómo podrías hacerlo si al mismo tiempo quieres utilizar la mirada con los ojos como entrada para mover la imagen. Difícil, ¿verdad? Esto describe la doble función de la mirada con los ojos cuando se necesita como entrada y como control. 

- **Salir antes de hacer clic:** Los estudios han demostrado que, para selecciones de objetivos rápidas, la mirada con los ojos del usuario puede desplazarse antes de concluir un clic manual (por ejemplo, al pulsar en el aire). Por lo tanto, se debe prestar especial atención a la sincronización de la señal de la mirada con los ojos rápida con la entrada de un control más lento (por ejemplo, una entrada de voz, manos o controlador).

- **Objetivos pequeños:** Piensa en la sensación al intentar leer texto que es demasiado pequeño para leerse cómodamente. Es una sensación estresante para los ojos, que provoca agotamiento al intentar reajustar los ojos para enfocar mejor.
Esta misma sensación es la que puedes hacer sentir a los usuarios si los obligas a seleccionar objetivos demasiado pequeños en la aplicación mediante la mirada con los ojos.
Al diseñar la aplicación, para crear una experiencia agradable y cómoda para los usuarios, se recomienda que los objetivos sean al menos de 2° en ángulo visual, o preferiblemente mayores.

- **Movimientos de mirada con los ojos irregulares.** Los ojos realizan movimientos rápidos al pasar de fijarse en un elemento a fijarse en otro. Si observas las trayectorias de movimientos registrados de ojos, podrás ver que son irregulares. Los ojos se mueven rápidamente y a saltos espontáneos en comparación con la *mirada con la cabeza* o los *movimientos manuales*.  

- **Confiabilidad del seguimiento:** La precisión del seguimiento de los ojos puede verse mermada con los cambios de luz, al ajustarse los ojos a las nuevas condiciones.
Aunque esto no debe necesariamente afectar al diseño de tu aplicación, ya que la precisión debe oscilar dentro de la limitación de 2° mencionada anteriormente, sí puede significar que el usuario tenga que realizar otra calibración. 


### <a name="design-recommendations"></a>Recomendaciones de diseño
A continuación, se enumeran las recomendaciones de diseño específicas en función de las ventajas y desafíos descritos para la entrada mediante mirada con los ojos:

1. **La mirada con los ojos no es lo mismo que la mirada con la cabeza:**
    - **Ten en cuenta si los movimientos rápidos e irregulares de los ojos funcionan bien para la tarea de entrada:** Aunque los movimientos rápidos e irregulares de los ojos son excelentes para seleccionar rápidamente objetivos en nuestro campo de visión, son menos eficaces para tareas que requieren trayectorias de entrada suaves (por ejemplo, para dibujar o rodear anotaciones con un círculo). En este caso, es preferible apuntar con la mano o con la cabeza.
  
    - **Evita asociar elementos directamente a la mirada con los ojos del usuario (por ejemplo, un control deslizante o un cursor).**
En el caso de un cursor, esto podría provocar un efecto de fuga del cursor, debido a ligeros desplazamientos en la señal de la mirada con los ojos proyectada. En el caso de un control deslizante, surge un conflicto con la doble función de controlar el control deslizante con los ojos mientras también se desea comprobar que el objeto se encuentra en la ubicación correcta. En pocas palabras, un usuario puede rápidamente sentirse abrumado y distraerse, especialmente si la señal es imprecisa para ese usuario. 
  
2. **Combina la mirada con los ojos con otras entradas:** La integración del seguimiento de los ojos con otras entradas, como gestos manuales, comandos de voz o la pulsación de un botón, tiene varias ventajas:
    - **Permitir la observación libre:** Dado que la función principal de los ojos es observar nuestro entorno, es importante permitir mirar a los usuarios sin activar acciones o información (visual, auditiva, etc.). 
    La combinación del seguimiento de ojos con otro control de entrada permite una transición fluida entre los modos de control de entrada y de observación con seguimiento de ojos.
  
    - **Proveedor de contexto eficaz:** Al usar información acerca de dónde mira el usuario mientras se pronuncia un comando de voz o se realiza un gesto con la mano, es posible canalizar sin esfuerzo la entrada por el campo de visión. Algunos ejemplos son: “Coloca eso ahí” para seleccionar y situar de manera rápida y fluida un holograma en la escena con solo mirar un objetivo y un destino. 

    - **Necesidad de sincronizar entradas multimodales (problema de “salir antes de hacer clic”):** La combinación de rápidos movimientos oculares con entradas adicionales más complejas (por ejemplo, comandos de voz prolongados o gestos con la mano) conlleva el riesgo de desviar la mirada con los ojos antes de finalizar el comando de entrada adicional. Por lo tanto, si creas tus propios controles de entrada (por ejemplo, gestos con la mano personalizados), asegúrate de registrar el comienzo de esta entrada o la duración aproximada para relacionarla con el elemento en el que se había fijado el usuario en el pasado.
    
3. **Información sutil para la entrada de seguimiento de los ojos:** Es útil proporcionar información al mirar un objetivo (para indicar que el sistema funciona según lo previsto) pero debe ser sutil. Esta puede ser información visual destacada que aparece o desaparece lentamente u otros comportamientos sutiles según el objetivo, como movimientos lentos (por ejemplo, aumentar ligeramente el tamaño del objetivo) para indicar que el sistema ha detectado correctamente que el usuario está mirando a un objetivo, sin interrumpir innecesariamente el flujo de trabajo actual del usuario. 

4. **Evita entradas que obliguen a realizar movimientos forzados con los ojos:** No obligues a los usuarios a realizar movimientos con los ojos específicos (gestos de mirada) para desencadenar acciones en la aplicación.

5. **Ten en cuenta las imprecisiones:** Podemos distinguir dos tipos de imprecisiones que son visibles para los usuarios: El desplazamiento y las sacudidas. La manera más sencilla de solucionar los desplazamientos es proporcionar objetivos suficientemente grandes para interactuar con ellos (más de 2° en ángulo visual; como referencia: la miniatura es de aproximadamente 2° en ángulo visual al estirar el brazo (1)). Esto conduce a la siguiente pauta:
    - No obligues a los usuarios a seleccionar objetivos demasiado pequeños: Hay estudios que han demostrado que si los objetivos son lo suficientemente grandes (y el sistema está correctamente diseñado), los usuarios afirman que la interacción resulta mágica y no requiere esfuerzo. Si los objetivos son demasiado pequeños, los usuarios describen la experiencia como agotadora y frustrante.
   

## <a name="see-also"></a>Consulte también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Mirada con los ojos en Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Gestos con la mano](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
* [Comodidad](comfort.md)
