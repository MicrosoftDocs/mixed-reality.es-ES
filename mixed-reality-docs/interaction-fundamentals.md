---
title: Información general de la interacción multimodal
description: Información general de la interacción multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixto en realidad, mirada, mirada como destino, interacción, diseñar, hololens, MMR, multimodal
ms.openlocfilehash: d018179e20d26ee8b7b24bc74d7c1711bc788282
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270383"
---
# <a name="introducing-instinctual-interactions"></a>Introducción a las interacciones instinctual

La filosofía de interacciones simple, instinctual es tejida a lo largo de la plataforma Microsoft Mixed Reality (MMR), de hardware al software.

Estas interacciones instinctual utilizan todas las tecnologías de entrada disponibles, incluido el seguimiento por completo, disponible de seguimiento, seguimiento de los ojos y lenguaje natural, en los modelos de interacción multimodal perfecta. Según nuestras investigaciones, diseñar y desarrollar multimodals y no en función de unas entradas únicas, es fundamental al crear experiencias instintiva.

Los modelos de interacción Instinctual también naturalmente alinearán por tipo de dispositivo.  Por ejemplo, interacción lejano en un auricular envolvente con un 6 grados de controlador de libertad (DoF) e interacción lejos de un 2 HoloLens usar los mismos prestaciones, patrones y comportamientos.  No sólo es este práctico para los desarrolladores y diseñadores, pero se siente más cómodo a los usuarios finales.


Por último, aunque reconocemos que existen miles de efectivo, atractivas y mágicos interacciones posibles en MR, hemos descubierto que intencionadamente que emplean un modelo de interacción único extremo a extremo en una aplicación es la mejor manera de asegurarse de que los usuarios son correctas y tiene una gran experiencia.  Para ello, hemos incluido tres cosas en esta guía de interacción:
* Nos hemos estructurado esta orientación acerca de los tres modelos de interacción principal y los componentes y patrones para cada uno
* Hemos incluido orientación complementaria en otras ventajas que ofrece nuestra plataforma.
* Hemos incluido orientación para ayudarle a seleccionar el modelo de interacción adecuado para su escenario

## <a name="multimodal-interaction-models"></a>Modelos de interacción multimodal

Según nuestras investigaciones y trabajar con clientes hasta la fecha, hemos descubierto tres modelos de interacción principal que se adapten a la mayoría de las experiencias de realidad mixta.  

Piense en estos modelos de interacción como modelo mental del usuario para completar sus flujos.

Cada uno de estos modelos de interacción es utilizable por derecho propio, eficaz y conveniente, y todos están optimizados para un conjunto de necesidades del cliente. Ver el gráfico a continuación, para escenarios, ejemplos y las ventajas de cada modelo de interacción.  

**Modelo** | **[Las manos y los controladores de movimiento](hands-and-tools.md)** | **[Manos libres](hands-free.md)** | **[Mirada de encabezado y confirmación](gaze-and-commit.md)**
|--------- | --------------| ------------| ---------|
**Escenarios de ejemplo** | 3D experiencias espaciales, por ejemplo, espacial y un diseño, manipulación o simulación de contenido | Experiencias contextuales donde están ocupadas manos de un usuario, por ejemplo, en el trabajo de aprendizaje, mantenimiento| Click-through experiencias, por ejemplo, 3D presentaciones, demostraciones
**Fit** | Muy bien para usuarios nuevos, voz wit acopladas, ocular a mirada principal o de seguimiento. Curva de aprendizaje reducida. Experiencia de usuario coherente a través de la mano de seguimiento y 6 controladores GDL. | Algunos de aprendizaje necesarios. Si las manos son pares disponible también con lenguaje natural y voz | Requiere recursos de aprendizaje en HMDs pero no en dispositivos móviles. Recomendado para controladores accesible. Lo mejor para HoloLens (gen 1). |
**Hardware** | HoloLens 2 <br>Cascos envolventes | HoloLens 2 <br>HoloLens (gen 1) <br>Cascos envolventes | HoloLens 2 <br>Cascos envolventes | HoloLens 2 <br>HoloLens (gen 1) <br>Cascos envolventes <br>Mobile AR |

Información detallada para usar todas las entradas disponibles juntos sin problemas en cada modelo de interacción es en las páginas siguientes, así como las ilustraciones y vínculos a contenido de ejemplo de nuestra MRTK de Unity.


## <a name="choose-an-interaction-model-for-your-customer"></a>Elija un modelo de interacción de cara al cliente


Probablemente, los desarrolladores y creadores de también ya tienen algunas ideas en mente de los tipos de la experiencia de interacción que quieren que sus usuarios a tener.
Para fomentar un enfoque centrado en el cliente para diseñar, se recomienda seguir las instrucciones siguientes para seleccionar el modelo de interacción que está optimizado para su cliente.

### <a name="why-follow-this-guidance"></a>¿Por qué seguir esta guía?

* Los modelos de interacción se prueban para objetiva y subjetivos criterios como el esfuerzo físico y cognitiva, intuitiveness y learnability. 
* Dado que es diferente de interacción, visual y prestaciones de audio y el comportamiento de los objetos también pueden diferir entre los modelos de interacción.  
* Combinar elementos de varios modelos de interacción, crea el riesgo de factibilidad competencia, como los rayos mano simultáneos y un cursor head mirada, que sobrecargar y confundir a los usuarios.

Estos son algunos ejemplos de cómo se optimizan factibilidad y comportamientos para cada modelo de interacción.  Con frecuencia vemos nuevos usuarios como preguntas similares, como "¿cómo se puede saber el sistema funciona, ¿cómo puedo saber lo que puedo hacer, y cómo saber si entiende lo que hice?"

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo</strong></td>
        <td><strong>¿Cómo puede saber funciona?</strong></td>
        <td><strong>¿Cómo se puede saber qué puedo hacer?</strong></td>
        <td><strong>¿Cómo se puede saber lo que hice?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Controladores de movimiento y manos</a></td>
        <td>Veo una mano de malla, se ve una prestación de la yema del dedo o mano / rayos de controlador.</td>
        <td>Veo un rectángulo de selección aparecen cuando mi mano está cerca o identificadores grabbable.</td>
        <td>Puedo oír tonos audibles y ver animaciones en la captura y liberación.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></td>
        <td>Veo un cursor en el centro de mi campo de visión.</td>
        <td>El cursor head mirada cambia el estado cuando se encuentre sobre determinados objetos.</td>
        <td>Puedo ver o escuchar visuales y audibles confirmaciones al realizar una acción.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Manos libres (Head mirada y permanencia)</a></td>
        <td>Veo un cursor en el centro de mi campo de visión.</td>
        <td>Veo un indicador de progreso cuando hincapié en un objeto interactuable.</td>
        <td>Puedo ver o escuchar visuales y audibles confirmaciones al realizar una acción.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Manos libres (comandos de voz)</a></td>
        <td>Veo un indicador de escuchando y las leyendas que muestran lo que escucha el sistema.</td>
        <td>Recibo mensajes de voz y sugerencias.  Cuando digo "¿Qué puedo decir?" Puedo ver comentarios.</td>
        <td>Puedo ver o escuchar visuales y audibles confirmaciones cuando asigne a un comando u obtener desambiguación UX cuando sea necesario.</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>A continuación se muestran las preguntas que hemos encontrado ayuda equipos seleccione un modelo de interacción:
 
1.  Q:  ¿Mis usuarios quieren tocar hologramas y realizar manipulaciones holográfica precisión?<br><br>
R:  Si es así, consulte el modelo de interacción de las manos y herramientas para la manipulación con manos o los controladores de movimiento y destinatarios de la precisión.
 
2.  Q:  ¿Es necesario mantener sus manos libres para las tareas reales Mis usuarios?<br><br>
R:  Si es así, eche un vistazo en el modelo de interacción de manos libres, que proporciona una gran experiencia a través de las interacciones basadas en voz y mirada manos libres.
 
3.  Q:  ¿Mis usuarios tienen tiempo para obtener información sobre las interacciones para mi aplicación de realidad mixta, o necesitan las interacciones con la curva de aprendizaje más bajo posible?<br><br>
R:  Se recomienda el modelo de manos y las herramientas de la curva de aprendizaje más bajo e interacciones más intuitivas, siempre y cuando los usuarios pueden usar sus manos para la interacción.
 
4.  Q:  ¿Mis usuarios utilizan los controladores de movimiento para señalar y manipulación?<br><br>
R:  El modelo de las manos e incluye todas las instrucciones para una gran experiencia con los controladores de movimiento.
 
5.  Q:  ¿Mis usuarios usar un controlador de accesibilidad o un controlador de Bluetooth comunes, como un clicker?<br><br>
R:  Se recomienda el modelo mirada de encabezado y confirmación para todos los controladores no realiza un seguimiento.  Se ha diseñado para permitir que un usuario recorrer una experiencia completa con un simple mecánico "de destino y de confirmación". 
 
6.  Q: ¿Mis usuarios solo de progreso a través de una experiencia haciendo clic en"a través de" (por ejemplo, en un entorno como presentación de diapositivas 3d), en lugar de navegar por los diseños densos de los controles de interfaz de usuario?<br><br>
R:  Si los usuarios no necesitan controlar una gran cantidad de interfaz de usuario, Head mirada y confirmación ofrece una opción fácil de aprender, donde los usuarios no tienen que preocuparse sobre cómo destinar. 
 
7.  Q:  ¿Mis usuarios usa ambos HoloLens (gen 1) y HoloLens 2 / envolventes de Windows (auriculares de realidad virtual)<br><br>
R:  Puesto que la mirada de encabezado y confirmación es el modelo de interacción para HoloLens (gen 1), se recomienda que creadores de admiten HoloLens (gen 1) use Head mirada y la confirmación de características o modos que pueden experimentar los usuarios en un HoloLens (gen 1) auriculares.  Consulte la sección siguiente a continuación en *transición de modelos de interacción* para obtener más información acerca de cómo realizar una gran experiencia para varias generaciones de HoloLens.
 
8.  Q: ¿Qué sucede a los usuarios que son generalmente móviles (que abarcan un amplio espacio o mover entre espacios), frente a los usuarios que tienden a funcionar en un único espacio?<br><br>
R:  Cualquiera de los modelos de interacción funcionará para estos usuarios.  

> [!NOTE]
> Obtener información más específica de diseño de aplicaciones [próximamente](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Modelos de interacción de transición
También hay casos donde los casos de uso pueden requerir que el uso de más de un modelo de interacción.  Por ejemplo, "flujo de creación" de la aplicación utiliza el modelo de interacción de las manos y las herramientas, pero desea emplear un modo manos libres para los técnicos de campo.  

Si su experiencia requieren varios modelos de interacción, hemos visto que muchos usuarios finales pueden encontrar dificultades para realizar la transición de un modelo a otro, especialmente los usuarios finales que está familiarizados con el Sr.

> [!Note]
> Para ayudar a los diseñadores de guía y los desarrolladores a través de las opciones que pueden ser difíciles en MR, estamos trabajando en obtener más instrucciones para usar varios modelos de interacción.
 

## <a name="see-also"></a>Vea también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Gestos](gestures.md)
* [Comandos de voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Diseño de asignaciones espaciales](spatial-mapping-design.md)
* [Comodidad](comfort.md)

