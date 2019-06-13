---
title: Introducción a la interacción multimodal
description: Introducción a la interacción multimodal
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hololens, MMR, multimodal
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516021"
---
# <a name="introducing-instinctual-interactions"></a>Introducción a las interacciones instintivas

La filosofía de interacciones simples e instintivas está integrada en la plataforma Microsoft Mixed Reality.  Hemos dado tres pasos para garantizar que los desarrolladores y diseñadores de aplicaciones puedan proporcionar interacciones sencillas e intuitivas para los clientes. 

En primer lugar, nos hemos asegurado de que nuestros increíbles sensores y nuestra tecnología de entrada, incluidos el seguimiento de la mano, el seguimiento de los ojos y el lenguaje natural, se combinen en modelos de interacción multimodal perfecta.  Según nuestras investigaciones, el diseño y el desarrollo multimodal (no basado en entradas únicas) es la clave para crear experiencias instintivas.

En segundo lugar, somos conscientes de que muchos desarrolladores tienen como destino varios dispositivos, es decir, HoloLens 2, HoloLens (1.ª generación) u HoloLens y VR.  Por lo tanto, hemos diseñado nuestros modelos de interacción para que funcionen en todos los dispositivos (aunque la tecnología de entrada sea diferente en cada dispositivo).  Por ejemplo, la interacción lejana en los cascos envolventes de Windows con un controlador 6DOF y la interacción lejana con HoloLens 2 usan prestaciones y patrones idénticos, lo que facilita el proceso para las aplicaciones multidispositivo. Esto no solo es práctico para desarrolladores y diseñadores, sino que los usuarios finales disfrutan de una experiencia más natural. 

Por último, aunque sabemos que existen miles de interacciones posibles eficaces, atractivas y mágicas en la realidad mixta, hemos descubierto que el empleo intencionado de un modelo de interacción único de principio a fin en una aplicación es la mejor manera de asegurarse de que los usuarios vivan una gran experiencia.  Para ello, hemos incluido tres elementos en esta guía de interacción:
* Hemos estructurado esta guía en torno a los tres modelos de interacción principales y los componentes y patrones necesarios para cada uno.
* Hemos incluido información complementaria acerca de las demás ventajas que ofrece nuestra plataforma.
* Hemos incluido información para ayudarte a seleccionar el modelo de interacción adecuado para tu escenario.

## <a name="multimodal-interaction-models"></a>Modelos de interacción multimodal

Según nuestras investigaciones y el trabajo con los clientes hasta la fecha, hemos descubierto que hay tres modelos de interacción principal que se adaptan a la mayoría de las experiencias de realidad mixta.

En muchos sentidos, el modelo de interacción es el modelo mental del usuario para completar los flujos.  Cada uno de estos modelos de interacción está optimizado para un conjunto de necesidades del cliente y cada uno es utilizable por derecho propio, es eficaz y es conveniente. 

El gráfico siguiente es una introducción simplificada.  En las páginas siguientes hay vínculos a información detallada sobre el uso de cada modelo de interacción con imágenes y ejemplos de código. 

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
        <td><strong>Apto para</strong></td>
        <td><strong>Hardware</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Controladores de movimiento y manos</a></td>
        <td>Experiencias espaciales en 3D, como el diseño espacial, la manipulación de contenido o la simulación.</td>
        <td>Ideal para usuarios nuevos, junto con la voz, el seguimiento de los ojos o la mirada con la cabeza. Curva de aprendizaje reducida. Experiencia de usuario coherente en el seguimiento de la mano y controladores 6DoF.</td>
        <td>HoloLens 2<br>Cascos envolventes</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Manos libres</a></td>
        <td>Experiencias contextuales en las que las manos de un usuario están ocupadas, por ejemplo, durante el aprendizaje de un trabajo o tareas de mantenimiento.</td>
        <td>Es necesario algún aprendizaje. Tener las manos no disponibles encaja bien con el lenguaje natural y la voz.</td>
        <td>HoloLens 2<br>HoloLens (1.ª generación)<br>Cascos envolventes</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></td>
        <td>Experiencias mediante clic; por ejemplo, presentaciones 3D, demostraciones.</td>
        <td>Requiere aprender HMD pero no en dispositivos móviles. Recomendado para controladores accesibles. Recomendado para HoloLens (1.ª generación).</td>
        <td>HoloLens 2<br>HoloLens (1.ª generación)<br>Cascos envolventes<br>Realidad aumentada en dispositivos móviles</td>
    </tr>
</table>
<br>

La mejor manera de asegurarse de que no haya espacios ni huecos en la interacción de la experiencia es seguir la guía de un único modelo de principio a fin. 

Para acelerar el diseño y el desarrollo, hemos incluido información detallada y vínculos a ejemplos de código e imágenes dentro de la explicación de cada modelo.

Pero, en primer lugar, en las secciones siguientes se describen los pasos para seleccionar e implementar uno de estos modelos de interacción.  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a>Al final de esta página, encontrarás información para:
 
* Elegir un modelo de interacción para los clientes.
* Utilizar la guía del modelo de interacción.
* Realizar la transición entre distintos modelos de interacción.
* Diseñar los pasos siguientes.


## <a name="choose-an-interaction-model-for-your-customer"></a>Elección de un modelo de interacción para los clientes


Probablemente, los desarrolladores y creadores ya tienen algunas ideas en mente sobre los tipos de experiencia de interacción que quieren para sus usuarios.
Para fomentar un enfoque centrado en el cliente durante el diseño, se recomienda seguir estas instrucciones para seleccionar un modelo de interacción optimizado para el cliente.

### <a name="why-follow-this-guidance"></a>¿Por qué seguir esta guía?

* Los modelos de interacción han sido probados con criterios objetivos y subjetivos como el esfuerzo físico y cognitivo, su intuitividad y la facilidad de aprendizaje. 
* Dado que las interacciones son diferentes, las prestaciones visuales y auditivas, y el comportamiento de los objetos también pueden diferir entre los modelos de interacción.  
* Combinar elementos de varios modelos de interacción crea el riesgo de competencia entre las prestaciones, por ejemplo, rayos de las manos y un cursor de la mirada con la cabeza simultáneos, que pueden sobrecargar y confundir a los usuarios.

Estos son algunos ejemplos de cómo se optimizan las prestaciones y los comportamientos para cada modelo de interacción.  Con frecuencia vemos que los nuevos usuarios tienen preguntas similares, tales como "¿cómo sé que el sistema funciona?, ¿cómo sé lo que puedo hacer? y ¿cómo sé si se entiende lo que acabo de hacer?".

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
        <td><strong>¿Cómo sé que funciona?</strong></td>
        <td><strong>¿Cómo sé qué puedo hacer?</strong></td>
        <td><strong>¿Cómo sé qué acabo de hacer?</strong></td>
    </tr>
    <tr>
        <td><a href="hands-and-tools.md">Controladores de movimiento y manos</a></td>
        <td>Veo una malla de mano, una prestación de dedo o rayos de mano o controlador.</td>
        <td>Veo manipuladores que se pueden agarrar o aparece un rectángulo de selección cuando mi mano está cerca.</td>
        <td>Puedo oír tonos audibles y ver animaciones al agarrar y soltar.</td>
    </tr>
    <tr>
        <td><a href="gaze-and-commit.md">Mirada-cabeza y confirmación</a></td>
        <td>Veo un cursor en el centro de mi campo de visión.</td>
        <td>El cursor de la mirada con la cabeza cambia de estado cuando se encuentra sobre determinados objetos.</td>
        <td>Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</td>
    </tr>   
    <tr>
        <td><a href="hands-free.md">Manos libres (mirada con la cabeza y permanencia)</a></td>
        <td>Veo un cursor en el centro de mi campo de visión.</td>
        <td>Veo un indicador de progreso al detenerme en un objeto con el que se puede interactuar.</td>
        <td>Veo u oigo confirmaciones visuales y auditivas al realizar una acción.</td>
    </tr>
    <tr>
        <td><a href="hands-free.md">Manos libres (comandos de voz)</a></td>
        <td>Veo un indicador de escucha y leyendas que muestran lo que ha oído el sistema.</td>
        <td>Recibo mensajes de voz y sugerencias.  Cuando digo "¿Qué puedo decir?" Veo comentarios.</td>
        <td>Veo u oigo confirmaciones visuales y auditivas cuando emito un comando u obtengo una experiencia de usuario de desambiguación cuando es necesario.</a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a>A continuación se muestran las preguntas que pueden ayudar a los equipos a seleccionar un modelo de interacción:
 
1.  Q:  ¿Los usuarios quieren tocar hologramas y realizar manipulaciones holográficas de precisión?<br><br>
R:  Si es así, consulta el modelo de interacción de manos y herramientas para establecer los objetivos y manipular con precisión usando las manos o controladores de movimiento.
 
2.  Q:  ¿Los usuarios necesitan tener las manos libres para sus tareas en el mundo real?<br><br>
R:  Si es así, consulta el modelo de interacción de manos libres, que proporciona una gran experiencia mediante interacciones basadas en la mirada y la voz.
 
3.  Q:  ¿Los usuarios tienen tiempo para aprender las interacciones de la aplicación de realidad mixta o necesitan interacciones con la curva de aprendizaje más corta posible?<br><br>
R:  Se recomienda el modelo de manos y herramientas, con una curva de aprendizaje más corta e interacciones más intuitivas, siempre y cuando los usuarios puedan usar sus manos para la interacción.
 
4.  Q:  ¿Los usuarios utilizan controladores de movimiento para apuntar y manipular?<br><br>
R:  El modelo de manos y herramientas incluye instrucciones completas para crear una gran experiencia con controladores de movimiento.
 
5.  Q:  ¿Los usuarios utilizan un controlador de accesibilidad o un controlador Bluetooth común, como un dispositivo de clic?<br><br>
R:  Se recomienda el modelo de mirada con la cabeza y confirmación para todos los controladores sin seguimiento.  Se ha diseñado para que los usuarios puedan recorrer una experiencia completa con una sencilla mecánica de "establecer destino y confirmar". 
 
6.  Q: ¿Los usuarios recorren una experiencia simplemente haciendo clic (por ejemplo, en un entorno similar a una presentación de diapositivas en 3D) en lugar de navegar por diseños densos de controles de interfaz de usuario?<br><br>
R:  Si los usuarios no necesitan controlar una gran cantidad de elementos de interfaz de usuario, el modelo de mirada con la cabeza y confirmación es una opción fácil de aprender, en la que los usuarios no tienen que preocuparse sobre cómo establecer un destino. 
 
7.  Q:  ¿Los usuarios usan tanto HoloLens (1.ª generación) como HoloLens 2 o Windows Immersive (cascos de realidad virtual)?<br><br>
R:  Mirada con la cabeza y confirmación es el modelo de interacción para HoloLens (1.ª generación), por lo que se recomienda que los creadores que admiten HoloLens (1.ª generación) usen la mirada con la cabeza y confirmación para todas las características o modos que los usuarios pueden experimentar con los cascos HoloLens (1.ª generación).  Consulta la sección siguiente sobre la *transición de los modelos de interacción* para más información acerca de cómo crear una gran experiencia para varias generaciones de HoloLens.
 
8.  Q: ¿Qué sucede con los usuarios que son generalmente móviles (abarcan un amplio espacio o se mueven entre espacios) frente a los usuarios que tienden a funcionar en un único espacio?<br><br>
R:  Cualquiera de los modelos de interacción funcionará para estos usuarios.  

> [!NOTE]
> [Próximamente](index.md#news-and-notes) habrá disponible más información específica para el diseño de aplicaciones.


## <a name="transition-interaction-models"></a>Transición de los modelos de interacción
También hay casos en los que puede ser necesario usar más de un modelo de interacción.  Por ejemplo, el "flujo de creación" de la aplicación utiliza el modelo de interacción de manos y controladores de movimiento, pero quieres utilizar un modo de manos libres para los técnicos de campo.  

Si la experiencia requiere varios modelos de interacción, hemos visto que muchos usuarios finales pueden encontrar dificultades para realizar la transición de un modelo a otro, especialmente en usuarios no familiarizados con la realidad mixta.

> [!Note]
> Para ayudar a diseñadores y desarrolladores con las opciones que pueden ser difíciles en la realidad mixta, estamos elaborando más instrucciones para usar varios modelos de interacción.
 

## <a name="see-also"></a>Consulte también
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

