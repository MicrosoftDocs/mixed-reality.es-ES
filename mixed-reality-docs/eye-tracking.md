---
title: Miras hacia abajo
description: HoloLens 2 permite un nuevo nivel de contexto y comprensión humana dentro de la experiencia holográfica, ya que proporciona a los desarrolladores la capacidad de usar información sobre lo que los usuarios ven.
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
keywords: Seguimiento ocular, realidad mixta, entrada, ojo
ms.openlocfilehash: c847f7de2cf4492c89225a88aeaf189f51cfbc40
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387594"
---
# <a name="eye-gaze-on-hololens-2"></a>Miras a la vista de HoloLens 2
HoloLens 2 permite un nuevo nivel de contexto y comprensión humana dentro de la experiencia holográfica, ya que proporciona a los desarrolladores la capacidad de usar información sobre lo que los usuarios ven. En esta página se indica a los desarrolladores cómo pueden beneficiarse del seguimiento ocular de varios casos de uso, así como qué buscar al diseñar interfaces de usuario basadas en el ojo. 


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Característica</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Miras hacia abajo</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="use-cases"></a>Casos de uso
El seguimiento de los ojos permite a las aplicaciones realizar un seguimiento de dónde mira el usuario en tiempo real. En los siguientes casos de uso se describen algunas interacciones que son posibles con el seguimiento ocular en la realidad mixta.
Tenga en cuenta que el [Kit de herramientas de la realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) es útil para proporcionar varios ejemplos interesantes y eficaces para usar el seguimiento ocular, como selecciones de destino compatibles con la vista rápida y sin esfuerzo, así como desplazarse automáticamente por el texto basado en el aspecto del usuario. 

### <a name="user-intent"></a>Intención del usuario    
Información sobre dónde y qué mira un usuario proporciona un contexto eficaz **para otras entradas**, como voz, manos y controladores.
Esta información puede utilizarse para varias tareas.
Por ejemplo, esto puede variar de forma rápida y sin esfuerzo **a través de** la escena, simplemente mirando un holograma y diciendo "Select" (consulte también la [cabecera y la confirmación](gaze-and-commit.md)) o diciendo "Put this..." y, a continuación, buscando dónde desea colocar el usuario el holograma y el "... allí ". Puedes consultar varios ejemplos en [Mixed Reality Toolkit: Selección de objetivos con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) y [Mixed Reality Toolkit: Posicionamiento de objetivos con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Además, un ejemplo de intención del usuario podría incluir el uso de información sobre lo que los usuarios ven para mejorar la interacción con agentes virtuales incorporados y hologramas interactivos. Por ejemplo, los agentes virtuales pueden adaptar las opciones disponibles y su comportamiento en función del contenido que se vea actualmente. 

### <a name="implicit-actions"></a>Acciones implícitas
La categoría de acciones implícitas está estrechamente relacionada con la intención del usuario.
La idea es que los hologramas o los elementos de la interfaz de usuario reaccionan de una manera algo instinctual que puede que no parezca incluso que el usuario está interactuando con el sistema, sino que el sistema y el usuario están sincronizados. Un ejemplo es el **desplazamiento automático basado en la mirada** en el que el usuario lee el texto a medida que el texto continúa desplazando o fluyen en sincronización con con la vista del usuario. Un aspecto clave de esto es que la velocidad de desplazamiento se adapta a la velocidad de lectura del usuario.
Otro ejemplo es el **zoom y la panorámica** que se admiten, donde el usuario puede sentir como sumergir exactamente hacia lo que está enfocado o. El zoom y el control de la velocidad de zoom se pueden controlar mediante la entrada de voz o a mano, lo que es importante para proporcionar al usuario la sensación de control mientras evita estar abrumado. Hablaremos sobre estas instrucciones de diseño con más detalle a continuación. Una vez que se ha ampliado, el usuario puede seguir sin problemas, por ejemplo, en el transcurso de una calle para explorar su entorno con solo ver la mirada.
Puedes consultar ejemplos de demostración de estos tipos de interacciones en el ejemplo [Mixed Reality Toolkit - Navegación con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Los casos de uso adicionales para _acciones implícitas_ pueden incluir:
- **Notificaciones inteligentes:** ¿Te molesta que aparezcan notificaciones justo donde estabas mirando? Teniendo en cuenta la atención de un usuario, puede mejorar esta experiencia mediante el desplazamiento de notificaciones desde donde el usuario está Gazing actualmente. Esto limita las distracciones y las descarta automáticamente una vez que el usuario haya terminado de leer. 
- **Hologramas atentos:** Hologramas que reaccionan sutilmente cuando se miran. Esto puede abarcar desde elementos de interfaz de usuario ligeramente iluminados hasta una flor de floración lenta hasta una mascota virtual que empieza a volver al usuario o intenta evitar la mirada al usuario después de una estrella prolongada. Esta interacción podría proporcionar una sensación interesante de conectividad y satisfacción en la aplicación.

### <a name="attention-tracking"></a>Seguimiento de la atención   
Información sobre dónde o qué ven los usuarios es una herramienta enormemente eficaz para evaluar la facilidad de uso de los diseños y para identificar problemas en flujos de trabajo eficientes. La visualización y el análisis de seguimiento ocular son una práctica común en diversas áreas de la aplicación. Con HoloLens 2, se proporciona una nueva dimensión para esta comprensión, ya que los hologramas 3D se pueden colocar en contextos reales y evaluarse como corresponda. El [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) proporciona ejemplos básicos para registrar y cargar datos de seguimiento ocular y cómo visualizarlos.

Otras aplicaciones de esta área pueden incluir: 
-   **Visualización de ojo remoto:** Visualice los colaboradores remotos que buscan para asegurarse de que las instrucciones se comprenden y se siguen correctamente.
-   **Estudios de investigación con usuarios:** El seguimiento de atención se puede usar para explorar la forma en que los usuarios principiantes frente a expertos analizan visualmente el contenido o cómo su coordinación ocular para tareas complejas, como el análisis de datos médicos o la maquinaria operativa.
-   **Entrenamiento de simulaciones y supervisión del rendimiento:** Practica y optimiza la ejecución de tareas mediante una identificación de cuellos de botella más eficaz en el flujo de ejecución.
-   **Evaluaciones de diseño, publicidad y estudios de mercado:** El seguimiento ocular es una herramienta común para la investigación de mercado al evaluar los diseños de productos y sitios Web.

### <a name="additional-use-cases"></a>Casos de uso adicionales
- **Videojuegos:** ¿Alguna vez has deseado tener superpoderes? Esta es tu oportunidad. Puede levitater los hologramas mediante la estrella. Dispara rayos láser con los ojos. Convierta los enemigos en piedra o inmovilice. Usa tu visión de rayos X para explorar edificios. El límite es tu imaginación.  

- **Avatares expresivos:** El seguimiento ocular ayuda en avatares 3D más expresivos mediante el uso de la fecha de seguimiento de ojos vivos para animar los ojos del Avatar que indican lo que el usuario está mirando. Además, aporta más expresividad mediante guiños y parpadeos. 

- **Entrada de texto:** El seguimiento ocular se puede usar como alternativa a la entrada de texto de bajo esfuerzo, especialmente cuando la voz o las manos no son prácticas de usar. 


## <a name="eye-tracking-api"></a>API de seguimiento de los ojos
Antes de entrar en detalles sobre las directrices de diseño específicas para la interacción ocular, queremos señalar brevemente las funcionalidades que proporciona la API de seguimiento de la vista HoloLens 2 para los desarrolladores. Proporciona un único origen y una dirección con miras a la vista, lo que proporciona datos a aproximadamente _30 fps_. 

La vista de predicción mira en la CA. 1,0-1,5 grados en el ángulo visual alrededor del destino real. Caben esperar pequeñas imprecisiones, por lo que debe dejarse algo de margen para este valor límite inferior. Más adelante se tratará este aspecto en detalle. Para que el seguimiento de los ojos funcione con precisión, cada usuario debe realizar una calibración de seguimiento de los ojos. 

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño óptimo de destino a una distancia de 2 metros*
<br>
<br>
La [API de seguimiento ocular](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) es accesible a través de: ' Windows. Perception. people. EyesPose '. 

## <a name="eye-gaze-design-guidelines"></a>Guías de diseño ocular
La creación de una interacción que aproveche el enfoque de los ojos en rápido movimiento puede ser complicada. En esta sección, se resumen las principales ventajas y los desafíos que se deben tener en cuenta al diseñar la aplicación. 

### <a name="benefits-of-eye-gaze-input"></a>Ventajas de la entrada ocular
- **Señalización a alta velocidad.** El músculo ocular es el que más rápido reacciona en el cuerpo humano. 

- **Poco esfuerzo.** Prácticamente no se necesita ningún movimiento físico. 

- **Implícito.** A menudo lo describen los usuarios como "atención", la información acerca de los movimientos oculares de un usuario permite que el sistema sepa cuál es el objetivo que el usuario tiene previsto interactuar. 

- **Canal de entrada alternativo.** La mirada a la mano puede proporcionar una gran cantidad de datos de soporte técnico para la entrada de voz y entrega en años de experiencia de los usuarios en función de su coordinación ocular a mano.

- **Atención visual.** Otra ventaja importante es la posibilidad de deducir lo que un usuario está pagando con atención. Esto puede ayudar en diversas áreas de la aplicación que abarcan de una evaluación más eficaz de los distintos diseños para ayudar a las interfaces de usuario más inteligentes y a las guías sociales mejoradas para la comunicación remota.

En pocas palabras, el uso de la mirada a la entrada ofrece una señal contextual rápida y sin esfuerzo. Esto es especialmente eficaz cuando se combina con otras entradas como la *voz* y la entrada *manual* para confirmar la intención del usuario.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafíos de la mirada: la entrada
Con una gran cantidad de energía, supone una gran responsabilidad.
A pesar de que la mirada se puede usar para crear experiencias de usuario satisfactorias, se siente como un Superhero, también es importante saber lo que no es adecuado para la consideración adecuada. A continuación se describen algunos de los *desafíos* que se deben tener en cuenta y cómo solucionarlos al trabajar con la entrada de mirada: 

- **La mirada está "Always On"** En el momento en que se abre el Lids, los ojos comienzan fixating sobre las cosas en el entorno. Al reaccionar a cada una de las búsquedas que se realizan y se emiten acciones accidentalmente porque se ha buscado algo demasiado tiempo, se producirá una experiencia incumplida.
Este es el motivo por el que se recomienda combinar el ojo con un *comando de voz*, un *gesto de mano*, un clic de *botón* o una permanencia extendida para desencadenar la selección de un destino.
Esta solución también permite un modo en el que el usuario puede mirar libremente sin saturarse mediante la activación involuntaria de algo. Esta cuestión también debe tenerse en cuenta al diseñar la información visual y auditiva que se recibe con solo mirar a un objetivo.
No debe sobrecargarse al usuario con efectos emergentes inmediatos o sonidos al pasar sobre los elementos. El detalle es clave. Más adelante, en las recomendaciones de diseño, se describen algunos de los procedimientos recomendados para esto.

- **Observación frente a control** Imagine que desea enderezar con precisión una fotografía en la pared. Miras los bordes y la zona circundante para ver si está bien alineada. Ahora Imagine cómo lo haría si quiere usar el ojo de la mirada como entrada para trasladar la imagen. Difícil, ¿verdad? Esto describe el doble rol de ojo y mira si es necesario para la entrada y el control. 

- **Salir antes de hacer clic:** En el caso de las selecciones de destino rápido, la investigación ha demostrado que el ojo de un usuario puede continuar antes de concluir un clic manual (por ejemplo, un airtap). Por lo tanto, se debe prestar especial atención a la sincronización de la señal de mirada rápida con una entrada de control más lenta (por ejemplo, voz, manos, controlador).

- **Objetivos pequeños:** ¿Sabe lo que se siente al intentar leer texto que es simplemente un poco más fácil de leer? Esta limitación de los ojos puede hacer que se sienta cansado y se haya gastado porque intenta reajustar los ojos para centrarse mejor.
Se trata de una sensación que podría invocar a los usuarios al obligarles a seleccionar destinos que son demasiado pequeños en la aplicación mediante el establecimiento de destinos de la vista.
Al diseñar la aplicación, para crear una experiencia agradable y cómoda para los usuarios, se recomienda que los objetivos sean al menos de 2° en ángulo visual, o preferiblemente mayores.

- **Movimientos oculares** desiguales Nuestros ojos realizan movimientos rápidos desde la fijación hasta la fijación. Si observas las trayectorias de movimientos registrados de ojos, podrás ver que son irregulares. Los ojos se mueven rápidamente y a saltos espontáneos en comparación con la *mirada con la cabeza* o los *movimientos manuales*.  

- **Confiabilidad del seguimiento:** La precisión del seguimiento de los ojos puede verse mermada con los cambios de luz, al ajustarse los ojos a las nuevas condiciones.
Aunque esto no debería afectar necesariamente al diseño de la aplicación, dado que la precisión debe estar dentro de la limitación de 2 °, podría ser necesario que el usuario ejecutara otra calibración. 


## <a name="design-recommendations"></a>Recomendaciones de diseño
A continuación se muestra una lista de recomendaciones de diseño específicas basadas en las ventajas y los desafíos descritos para la entrada ocular:

1. **Mira fijamente. = encabezado:**
    - **Ten en cuenta si los movimientos rápidos e irregulares de los ojos funcionan bien para la tarea de entrada:** Aunque nuestros movimientos de ojo rápidos y desiguales son excelentes a la vez que se seleccionan rápidamente los destinos en nuestro campo de vista (hipercampo), es menos aplicable a las tareas que requieren trayectorias de entrada suaves (por ejemplo, dibujar o enmarcar anotaciones). En este caso, es preferible apuntar con la mano o con la cabeza.
  
    - **Evite adjuntar algo directamente a la mirada del usuario (por ejemplo, un control deslizante o un cursor).**
En el caso de un cursor, esto puede dar lugar al efecto "cursor fleeing" debido a ligeras desplazamientos en la señal de ojo mirada. En el caso de un control deslizante, puede entrar en conflicto con el doble rol de controlar el control deslizante con los ojos mientras también se desea comprobar si el objeto está en la ubicación correcta. En pocas palabras, los usuarios pueden saturarse y distraerse, especialmente si la señal es imprecisa para ese usuario. 
  
2. **Combine la mirada con otras entradas:** La integración del seguimiento ocular con otras entradas, como gestos de mano, comandos de voz o pulsaciones de botones, ofrece varias ventajas:
    - **Permitir la observación libre:** Dado que el rol principal de nuestros ojos es observar nuestro entorno, es importante que los usuarios tengan la posibilidad de buscar sin desencadenar comentarios ni acciones (visual, Auditor, etc.). 
    La combinación del seguimiento ocular con otro control de entrada permite una transición suave entre los modos de observación de seguimiento ocular y de control de entrada.
  
    - **Proveedor de contexto eficaz:** El uso de información sobre dónde y qué mira el usuario mientras se ejecuta un comando de voz o realiza un gesto de mano permite canalizar sin problemas la entrada a través del campo de vista. Por ejemplo: “Coloca eso ahí” para seleccionar y situar de manera rápida y fluida un holograma en la escena con solo mirar un objetivo y un destino. 

    - **Necesidad de sincronizar entradas multimodales (problema de “salir antes de hacer clic”):** La combinación de movimientos oculares rápidos con entradas adicionales más complejas, como comandos de voz largos o gestos de mano, asume el riesgo de continuar la mirada antes de finalizar el comando de entrada adicional. Por lo tanto, si creas tus propios controles de entrada (por ejemplo, gestos con la mano personalizados), asegúrate de registrar el comienzo de esta entrada o la duración aproximada para relacionarla con el elemento en el que se había fijado el usuario en el pasado.
    
3. **Información sutil para la entrada de seguimiento de los ojos:** Resulta útil proporcionar comentarios cuando se examina un destino para indicar que el sistema funciona según lo previsto, pero debe mantenerse sutil. Esto puede incluir una mezcla lenta, de arriba y de salida, que se resalta visualmente o se realizan otros comportamientos de destino sutiles, como los movimientos lentos, como un aumento ligeramente del destino, para indicar que el sistema ha detectado correctamente que el usuario está viendo un objetivo sin interrumpir innecesariamente el flujo de trabajo actual del usuario. 

4. **Evita entradas que obliguen a realizar movimientos forzados con los ojos:** No obligue a los usuarios a realizar movimientos oculares específicos (gestos de mirados) para desencadenar acciones en la aplicación.

5. **Ten en cuenta las imprecisiones:** Se distinguen dos tipos de imprecisiones que son evidentes para los usuarios: desplazamiento y vibración. La manera más fácil de resolver un desplazamiento es proporcionar destinos suficientemente grandes para interactuar con. Se recomienda usar un ángulo visual superior a 2 ° como referencia. Por ejemplo, la miniatura es aproximadamente de 2 ° en el ángulo visual al expandir el brazo. Esto conduce a la siguiente pauta:
    - No obligue a los usuarios a seleccionar pequeños destinos. La investigación ha demostrado que si los destinos son suficientemente grandes y que el sistema está diseñado correctamente, los usuarios describen sus interacciones como sin esfuerzo y mágicas. Si los objetivos son demasiado pequeños, los usuarios describen la experiencia como agotadora y frustrante.
   

## <a name="see-also"></a>Vea también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Encabezado y ojo en DirectX](gaze-in-directx.md)
* [Mirada a la vista de Unity (kit de herramientas de realidad mixta)](https://aka.ms/mrtk-eyes)
* [Gestos con la mano](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
* [Comodidad](comfort.md)
