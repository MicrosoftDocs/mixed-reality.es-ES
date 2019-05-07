---
title: Información general de la interacción multimodal
description: Información general de la interacción multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Diseñar la realidad, mirada, mirada como destino, interacción, mixta
ms.openlocfilehash: f52a0cd8ec53bfe0f4c5da2c054c538eda1c93ca
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993599"
---
# <a name="introducing-instinctual-interactions"></a>Introducción a las interacciones instinctual
La filosofía de interacciones simple, instinctual es integrando a través de la plataforma Microsoft Mixed Reality.  Hemos tomado tres pasos para asegurarse de que los desarrolladores y diseñadores de aplicaciones pueden proporcionar interacciones sencillas e intuitivas para sus clientes. 

En primer lugar, nos hemos asegurado de que nuestras increíbles sensores y la tecnología de entrada, incluida la mano de seguimiento, seguimiento de los ojos y lenguaje natural, combinan en los modelos de interacción multimodal perfecta.  Según nuestras investigaciones, diseño y desarrollo multimodally--y no según unas entradas únicas; es la clave para crear experiencias instinctual.

En segundo lugar, somos conscientes de que muchos desarrolladores tener como destino varios dispositivos, si eso significa el 2 de HoloLens y HoloLens (gen 1) o HoloLens y VR.  Por lo que hemos diseñado nuestros modelos de interacción para que funcione en todos los dispositivos (incluso si la tecnología de entrada varía en cada dispositivo).  Por ejemplo, lejano interacción en auriculares envolventes de Windows con un controlador 6GDL e interacción lejos de un 2 HoloLens ambos usar las prestaciones idénticos y los patrones, facilitando el proceso para las aplicaciones entre dispositivos. No sólo es este práctico para los desarrolladores y diseñadores, pero se siente más cómodo a los usuarios finales. 

Por último, aunque reconocemos que existen miles de efectivo, atractivas y mágicos interacciones posibles en MR, hemos descubierto que intencionadamente que emplean un modelo de interacción único extremo a extremo en una aplicación es la mejor manera de asegurarse de que los usuarios son correctas y tiene una gran experiencia.  Para ello, hemos incluido tres cosas en esta guía de interacción:
* Nos hemos estructurado esta orientación acerca de los tres modelos de interacción principal y los componentes y patrones para cada uno
* Hemos incluido orientación complementaria en otras ventajas que ofrece nuestra plataforma.
* Hemos incluido orientación para ayudarle a seleccionar el modelo de interacción adecuado para su escenario


## <a name="three-multimodal-interaction-models"></a>Tres modelos de interacción multimodal
Según nuestras investigaciones y trabajar con clientes hasta la fecha, hemos descubierto que tres modelos de interacción principal que se adapte a la mayoría de las experiencias de realidad mixta.

En muchos sentidos, el modelo de interacción es el modelo mental del usuario para completar sus flujos.  Cada uno de estos modelos de interacción se optimiza para un conjunto de necesidades del cliente y cada uno es utilizable por derecho propio, eficaz y conveniente. 

El gráfico siguiente es una introducción simplificada.  Información detallada sobre el uso de cada modelo de interacción está vinculada a las páginas siguientes con imágenes y ejemplos de código.  

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
        <td><strong>Escenarios de ejemplo</strong></td>
        <td><strong>Fit</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Las manos y herramientas</a></td>
        <td>Experiencias espaciales en 3D<br>Por ejemplo, diseño espacial y diseño, manipulación de contenido o simulación</td>
        <td>Ideal para nuevos usuarios<br>Curva de aprendizaje reducida<br>Conexión a tierra en factibilidad visual fácil<br>Experiencia de usuario coherente a través de la mano de seguimiento y controladores GDL 6<br>Excelente cuando se combina con la voz, seguimiento de los ojos o head que mirar</td>
        <td>HoloLens 2<br>Envolventes con 6GDL controladores de Windows</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Hands-free</a></td>
        <td>Experiencias contextuales donde están ocupadas, por ejemplo, las manos de un usuario en el trabajo de aprendizaje, mantenimiento</td>
        <td>Algunos de aprendizaje necesarios<br>Si no están disponibles las manos<br>pares de bien con lenguaje natural y voz</td>
        <td>HoloLens 2<br>HoloLens (gen 1)<br> Envolventes de Windows</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Mirada de encabezado y confirmación</a></td>
        <td>Por ejemplo, 3D presentaciones, demostraciones de experiencias de Click-through</td>
        <td>Requiere recursos de aprendizaje en HMDs pero no en dispositivos móviles<br>Lo mejor para los controladores accesible<br>Lo mejor para HoloLens (gen 1)</td>
        <td>HoloLens 2<br>HoloLens (gen 1)<br> Envolventes de Windows<br> Mobile AR</td>
    </tr>
</table>
<br>

La mejor manera de asegurarse de que no hay espacios ni los huecos en la interacción de su experiencia es seguir las instrucciones para un único modelo de principio a fin. 

Para acelerar el desarrollo y diseño, hemos incluido información detallada y vínculos a ejemplos de código y las imágenes dentro de nuestra cobertura de cada modelo.

Pero en primer lugar, siga los pasos de selección y de implementación de uno de estos modelos de interacción en las secciones siguientes.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>Al final de esta página, comprenderá nuestras instrucciones en:
 
* Elegir un modelo de interacción para sus clientes
* Mediante las instrucciones del modelo de interacción
* Realizar la transición entre los modelos de interacción
* Pasos de diseño

## <a name="choosing-an-interaction-model-for-your-customer"></a>Elegir un modelo de interacción para sus clientes

Probablemente, los desarrolladores y creadores ya tienen algunas ideas en mente de los tipos de la experiencia de interacción que deseen para sus usuarios.
Para fomentar un enfoque centrado en el cliente para diseñar, se recomienda seguir las instrucciones siguientes para seleccionar el modelo de interacción que está optimizado para su cliente.

### <a name="why-follow-this-guidance"></a>¿Por qué seguir esta guía?

* Los modelos de interacción se prueban para objetiva y subjetivos criterios como el esfuerzo físico y cognitiva, intuitiveness y learnability. 
* Dado que es diferente de interacción, visual y prestaciones de audio y el comportamiento de los objetos también pueden diferir entre los modelos de interacción.  
* Combinar elementos de varios modelos de interacción, crea el riesgo de factibilidad competencia, como los rayos mano simultáneos y un cursor mirada, que sobrecargar y confundir a los usuarios.

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
        <td><strong>¿Cómo puedo saber qué puedo hacer?</strong></td>
        <td><strong>¿Cómo se puede saber lo que hice?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Las manos y herramientas</a></td>
        <td>Veo una mano de malla, se ve una prestación de la yema del dedo o mano / rayos de controlador.</td>
        <td>Veo un rectángulo de selección aparecen cuando mi mano está cerca o identificadores grabbable.</td>
        <td>Puedo oír tonos audibles y ver animaciones en la captura y liberación.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Mirada de encabezado y confirmación</a></td>
        <td>Veo un cursor en el centro de mi campo de visión.</td>
        <td>El cursor mirada cambia el estado cuando se encuentre sobre determinados objetos.</td>
        <td>Puedo ver o escuchar visuales y audibles confirmaciones al realizar una acción.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Manos libres (mirada y permanencia)</a></td>
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
 
1.  Q:  ¿Mis usuarios quieren tocar hologramas y realizar manipulaciones holográfica precisión?
R:  Si es así, consulte el modelo de interacción de las manos y herramientas para la manipulación con manos o los controladores de movimiento y destinatarios de la precisión.
 
2.  Q:  ¿Es necesario mantener sus manos libres para las tareas reales Mis usuarios?
R:  Si es así, eche un vistazo en el modelo de interacción de manos libres, que proporciona una gran experiencia a través de las interacciones basadas en voz y mirada manos libres.
 
3.  Q:  ¿Mis usuarios tienen tiempo para obtener información sobre las interacciones para mi aplicación de realidad mixta, o necesitan las interacciones con la curva de aprendizaje más bajo posible?
R:  Se recomienda el modelo de manos y las herramientas de la curva de aprendizaje más bajo e interacciones más intuitivas, siempre y cuando los usuarios pueden usar sus manos para la interacción.
 
4.  Q:  ¿Mis usuarios utilizan los controladores de movimiento para señalar y manipulación?
R:  El modelo de las manos e incluye todas las instrucciones para una gran experiencia con los controladores de movimiento.
 
5.  Q:  ¿Mis usuarios usar un controlador de accesibilidad o un controlador de Bluetooth comunes, como un clicker?
R:  Se recomienda el modelo mirada de encabezado y confirmación para todos los controladores no realiza un seguimiento.  Se ha diseñado para permitir que un usuario recorrer una experiencia completa con un simple mecánico "de destino y de confirmación". 
 
6.  Q: ¿Mis usuarios solo de progreso a través de una experiencia haciendo clic en"a través de" (por ejemplo, en un entorno como presentación de diapositivas 3d), en lugar de navegar por los diseños densos de los controles de interfaz de usuario?
R:  Si los usuarios no necesitan controlar una gran cantidad de interfaz de usuario, Head mirada y confirmación ofrece una opción fácil de aprender, donde los usuarios no tienen que preocuparse sobre cómo destinar. 
 
7.  Q:  ¿Mis usuarios usa ambos HoloLens (gen 1) y HoloLens 2 / r: envolventes de Windows (auriculares de realidad virtual)  Puesto que la mirada de encabezado y confirmación es el modelo de interacción para HoloLens (gen 1), se recomienda que creadores de admiten HoloLens (gen 1) use Head mirada y la confirmación de características o modos que pueden experimentar los usuarios en un HoloLens (gen 1) auriculares.  Consulte la sección siguiente a continuación en *transición de modelos de interacción* para obtener más información acerca de cómo realizar una gran experiencia para varias generaciones de HoloLens.
 
8.  Q: ¿Qué sucede a los usuarios que son generalmente móviles (que abarcan un amplio espacio o mover entre espacios), frente a los usuarios que tienden a funcionar en un único espacio?  
R:  Cualquiera de los modelos de interacción funcionará para estos usuarios.  

> [!NOTE]
> Obtener información más específica de diseño de aplicaciones [próximamente](index.md#news-and-notes).


## <a name="transition-interaction-models"></a>Modelos de interacción de transición
También hay casos donde los casos de uso pueden requerir que el uso de más de un modelo de interacción.  Por ejemplo, "flujo de creación" de la aplicación utiliza el modelo de interacción de las manos y las herramientas, pero desea emplear un modo manos libres para los técnicos de campo.  

Si su experiencia requieren varios modelos de interacción, hemos visto que muchos usuarios finales pueden encontrar dificultades para realizar la transición de un modelo a otro, especialmente los usuarios finales que está familiarizados con el Sr.

> [!Note]
> Para ayudar a los diseñadores de guía y los desarrolladores a través de las opciones que pueden ser difíciles en MR, estamos trabajando en obtener más instrucciones para usar varios modelos de interacción.
 

## <a name="see-also"></a>Vea también
* [Mirada de encabezado y confirmación](gaze-and-commit.md)
* [Manipulación directa](direct-manipulation.md)
* [Punto y confirmación](point-and-commit.md)
* [Selección de destinos de la mirada](gaze-targeting.md)
* [Gestos](gestures.md)
* [Diseño de la voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Diseño de asignaciones espaciales](spatial-mapping-design.md)
* [Comodidad](comfort.md)
