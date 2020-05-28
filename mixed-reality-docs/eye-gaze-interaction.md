---
title: Interacción basada en el control con los ojos
description: HoloLens 2 ofrece un nuevo nivel de conocimiento del contexto y del comportamiento humano dentro de la experiencia holográfica al proporcionar a los desarrolladores la capacidad de usar información sobre lo que están mirando los usuarios. En esta página se tratan las recomendaciones de diseño para los desarrolladores que quieren usar miradamente como entrada.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Seguimiento ocular, realidad mixta, entrada, ojo
ms.openlocfilehash: 2ae7723f116771986edc757f1c9d4f454b0a256f
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2020
ms.locfileid: "84111038"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interacción mirada en la vista en HoloLens 2

![Demostración de seguimiento ocular en MRTK](images/mrtk_et_scenemenu.jpg)

Una de nuestras nuevas funcionalidades interesantes en HoloLens 2 es el seguimiento ocular.
En la página [seguimiento de la vista de HoloLens 2](eye-tracking.md) , hemos mencionado la necesidad de que cada usuario pase por una [calibración](https://docs.microsoft.com/hololens/hololens-calibration), proporcionó algunas instrucciones para desarrolladores y casos de uso resaltados para el seguimiento ocular.
La entrada de mirada sigue siendo un nuevo tipo de entrada de usuario y hay mucho que aprender. Aunque la entrada de ojo mirada solo se usa muy sutilmente en nuestra experiencia de Shell holográfica (la interfaz de usuario que ve al iniciar su HoloLens 2), varias aplicaciones, como la ["animación de HoloLens"](https://www.microsoft.com/p/mr-playground/9nb31lh723s2), muestran excelentes ejemplos de cómo puede agregarse la entrada ocular a la magia de su experiencia holográfica.
En esta página, se describen las consideraciones de diseño para la integración de la entrada ocular para interactuar con las aplicaciones holográficas.
Aprenderá sobre las principales ventajas y también los desafíos únicos que acompañan a la entrada de mirada.  
En función de estas, se proporcionan varias recomendaciones de diseño para ayudarle a crear interfaces de usuario compatibles con la vista de ojo. 

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
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Control con los ojos</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>


## <a name="eye-gaze-input-design-guidelines"></a>Guías de diseño de entrada de mirada
Crear una interacción que aproveche los objetivos de vista rápida en movimiento puede ser un reto. En esta sección, se resumen las principales ventajas y los desafíos que se deben tener en cuenta al diseñar la aplicación. 

### <a name="benefits-of-eye-gaze-input"></a>Ventajas de la entrada ocular
- **Señalización a alta velocidad.** El músculo ocular es el músculo de reacción más rápido en el cuerpo humano. 

- **Poco esfuerzo.** Prácticamente no se necesita ningún movimiento físico. 

- **Implícito.** A menudo lo describen los usuarios como "atención", la información acerca de los movimientos oculares de un usuario permite que el sistema sepa cuál es el objetivo que el usuario tiene previsto interactuar. 

- **Canal de entrada alternativo.** La mirada a la mano puede proporcionar una gran cantidad de datos de soporte técnico para la entrada de voz y entrega en años de experiencia de los usuarios en función de su coordinación ocular a mano.

- **Atención visual.** Otra ventaja importante es la posibilidad de deducir lo que un usuario está pagando con atención. Esto puede ayudar en diversas áreas de la aplicación que abarcan de una evaluación más eficaz de los distintos diseños para ayudar a las interfaces de usuario más inteligentes y a las guías sociales mejoradas para la comunicación remota.

En pocas palabras, el uso de la mirada a la entrada ofrece una señal de entrada contextual rápida y sin esfuerzo. Esto es especialmente eficaz cuando se combina con otras entradas como la *voz* y la entrada *manual* para confirmar la intención del usuario.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafíos de la mirada: la entrada
Con una gran cantidad de energía, supone una gran responsabilidad.
A pesar de que la mirada se puede usar para crear experiencias de usuario satisfactorias, lo que hace que se sienta como un Superhero, también es importante saber lo que no es adecuado para la consideración adecuada. A continuación se explican algunos de los *desafíos* que se deben tener en cuenta y cómo solucionarlos al trabajar con la entrada de mirada: 

- **La mirada está "Always On"** En el momento en que se abre el Lids, los ojos comienzan fixating sobre las cosas en el entorno. Al reaccionar a cada una de las búsquedas que realiza y emite acciones accidentalmente, porque ha examinado algo durante demasiado tiempo, se producirá una experiencia incumplida.
Por lo tanto, se recomienda combinar el ojo con un *comando de voz*, un gesto de *mano*, un *clic de botón* o una permanencia extendida para desencadenar la selección de un destino (para obtener más información, consulte [miras y confirmaciones](gaze-and-commit-eyes.md)).
Esta solución también permite un modo en el que el usuario puede mirar libremente sin saturarse mediante la activación involuntaria de algo. Este problema también se debe tener en cuenta a la hora de diseñar comentarios visuales y acústicos al mirar un objetivo.
Intente no sobrecargar al usuario con efectos emergentes inmediatos o desplazarse por los sonidos. El detalle es clave. Hablaremos de algunas prácticas recomendadas para esta información más adelante al hablar acerca de las [recomendaciones de diseño](eye-gaze-interaction.md#design-recommendations).

- **Observación frente a control** Imagine que desea enderezar con precisión una fotografía en la pared. Miras los bordes y la zona circundante para ver si está bien alineada. Ahora Imagine cómo lo haría si quiere usar el ojo de la mirada como entrada para trasladar la imagen. Difícil, ¿verdad? Esto describe el doble rol de ojo y mira si es necesario para la entrada y el control. 

- **Dejar antes de hacer clic:** En el caso de las selecciones de destino rápido, la investigación ha demostrado que el ojo de un usuario puede continuar antes de concluir un clic manual (por ejemplo, una pulsación aérea). Por lo tanto, se debe prestar especial atención a la sincronización de la señal de mirada rápida con una entrada de control más lenta (por ejemplo, voz, manos, controlador).

- **Destinos pequeños:** ¿Sabe que se siente al intentar leer texto que es simplemente un poco pequeño para leerlo de forma cómoda? Esta limitación de los ojos puede hacer que se sienta cansado y se haya gastado, ya que intenta reajustar los ojos para centrarse mejor.
Se trata de una sensación que podría invocar a los usuarios al obligarles a seleccionar destinos que son demasiado pequeños en la aplicación mediante el establecimiento de destinos de la vista.
Al diseñar la aplicación, para crear una experiencia agradable y cómoda para los usuarios, se recomienda que los objetivos sean al menos de 2° en ángulo visual, o preferiblemente mayores.

- **Movimientos oculares desiguales** Nuestros ojos realizan movimientos rápidos desde la fijación hasta la fijación. Si observas las trayectorias de movimientos registrados de ojos, podrás ver que son irregulares. Los ojos se mueven rápidamente y en saltos espontáneos en comparación con los *movimientos*de *miras* o de mano.  

- **Seguimiento de la confiabilidad:** La precisión del seguimiento ocular puede degradar un poco en la luz cambiante a medida que los ojos se ajustan a las nuevas condiciones.
Aunque esto no debería afectar necesariamente al diseño de la aplicación, dado que la precisión debe estar dentro de la limitación de 2 °, puede que sea necesario que el usuario se calibre de nuevo. 


## <a name="design-recommendations"></a>Recomendaciones de diseño
A continuación se muestra una lista de recomendaciones de diseño específicas basadas en las ventajas y los desafíos descritos para la entrada ocular:

1. **La mirada no es lo mismo que la mirada:**
    - **Considere si los movimientos de ojo rápidos pero desiguales se ajustan a la tarea de entrada:** Aunque nuestros movimientos de ojo rápidos y desiguales son excelentes para seleccionar rápidamente los destinos en nuestro campo de vista, es menos aplicable a las tareas que requieren trayectorias de entrada fluidas (por ejemplo, dibujar o enmarcar anotaciones). En este caso, es preferible apuntar con la mano o con la cabeza.
  
    - **Evite adjuntar algo directamente a la mirada del usuario (por ejemplo, un control deslizante o un cursor).**
En el caso de un cursor, esto puede dar lugar a un efecto de "cursor fleeing" debido a ligeras desplazamientos en la señal de ojo mirada. En el caso de un control deslizante, puede entrar en conflicto con el doble rol de controlar el control deslizante con los ojos mientras también se desea comprobar si el objeto está en la ubicación correcta. En el ejemplo del control deslizante, tiene más sentido usar la mirada en combinación con gestos de mano. Esto significa que el usuario podría cambiar de forma rápida y sencilla entre un número de controles deslizantes, levantando su mano y moviendo su Thumb y el dedo del índice para captarlo y moverlo. Cuando se suelta el contacto, el control deslizante deja de moverse. En pocas palabras, los usuarios pueden saturarse y distraerse, especialmente si la señal es imprecisa para ese usuario. 
  
2. **Combine la mirada con otras entradas:** La integración del seguimiento ocular con otras entradas, como gestos de mano, comandos de voz o pulsaciones de botones, ofrece varias ventajas:
    - **Permitir observación gratuita:** Dado que el rol principal de nuestros ojos es observar nuestro entorno, es importante que los usuarios tengan la posibilidad de desplazarse sin activar ningún comentario o acción (visual, Auditor, etc.). 
    La combinación del seguimiento ocular con otro control de entrada permite una transición suave entre los modos de observación de seguimiento ocular y de control de entrada.
  
    - **Proveedor de contexto eficaz:** El uso de información sobre dónde y qué mira el usuario mientras se indica un comando de voz o que realiza un gesto de mano permite canalizar sin problemas la entrada a través del campo de vista. Por ejemplo, supongamos _que "colocamos allí"_ para seleccionar y colocar de forma rápida y sencilla un holograma en la escena con solo mirar un destino y su destino previsto. 

    - **Necesidad de sincronizar las entradas multimodal:** La combinación de movimientos oculares rápidos con entradas adicionales más complejas, como comandos de voz largos o gestos de mano, asume el riesgo de que el usuario ya tenga que buscar antes de que el comando de entrada adicional finalice y se reconozca. Por lo tanto, si crea sus propios controles de entrada (por ejemplo, gestos de mano personalizados), asegúrese de registrar la aparición de esta entrada o de una duración aproximada para correlacionarla con lo que un usuario había examinado en el pasado.
    
3. **Comentarios sutiles para la entrada de seguimiento ocular:** Resulta útil proporcionar comentarios cuando se examina un destino para indicar que el sistema funciona según lo previsto, pero debe mantenerse sutil. Esto puede incluir la mezcla lenta, de arriba y de salida, los elementos visuales y otros comportamientos de destino sutiles, como los movimientos lentos, como un aumento ligeramente del tamaño de destino, para indicar que el sistema ha detectado correctamente que el usuario está viendo un destino sin interrumpir innecesariamente el flujo de trabajo actual del usuario. 

4. **Evite aplicar movimientos oculares no naturales como entrada:** No obligue a los usuarios a realizar movimientos oculares específicos (gestos de mirados) para desencadenar acciones en la aplicación.

5. Tenga **en cuenta las imprecisiones:** Se distinguen dos tipos de imprecisiones que son evidentes para los usuarios: desplazamiento y vibración. La manera más fácil de resolver un desplazamiento es proporcionar destinos suficientemente grandes para interactuar con. Se recomienda usar un ángulo visual superior a 2 ° como referencia. Por ejemplo, la miniatura es aproximadamente de 2 ° en el ángulo visual al expandir el brazo. Esto conduce a la siguiente pauta:
    - No obligue a los usuarios a seleccionar pequeños destinos. La investigación ha demostrado que si los destinos son suficientemente grandes y que el sistema está diseñado correctamente, los usuarios describen sus interacciones como sin esfuerzo y mágicas. Si los objetivos son demasiado pequeños, los usuarios describen la experiencia como agotadora y frustrante.
  
<br>

Esta página le proporcionó una buena introducción para empezar a entender la mirada como una entrada en realidad mixta. Para empezar a desarrollar, eche un vistazo a nuestra información sobre [la vista de la mirada en Unity](https://aka.ms/mrtk-eyes) y [la mirada en DirectX](gaze-in-directx.md).


## <a name="see-also"></a>Consulte también
* [Comodidad](comfort.md)
* [Miras a la vista en DirectX](gaze-in-directx.md)
* [Mirada a la vista de Unity (kit de herramientas de realidad mixta)](https://aka.ms/mrtk-eyes)
* [Seguimiento de los ojos en HoloLens 2](eye-tracking.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Entrada de voz](voice-design.md)
