---
title: Experiencias compartidas en realidad mixta
description: Las aplicaciones holográficas pueden compartir anclajes espaciales de un HoloLens a otro, lo que permite a los usuarios representar un holograma en el mismo lugar en el mundo real, en varios dispositivos.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: experiencia compartida, realidad mixta, holograma, delimitador espacial, multiusuario, múltiple
ms.openlocfilehash: c846bcd8c9c52f1f169d306df3afd4f982656078
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926928"
---
# <a name="shared-experiences-in-mixed-reality"></a>Experiencias compartidas en realidad mixta

Los hologramas no necesitan permanecer privados para un solo usuario. Las aplicaciones holográficas pueden compartir [anclajes espaciales](spatial-anchors.md) de un dispositivo HoloLens, iOS o Android en otro, lo que permite a los usuarios representar un holograma en el mismo lugar del mundo real en varios dispositivos.

## <a name="six-questions-to-define-shared-scenarios"></a>Seis preguntas para definir escenarios compartidos

Antes de empezar a diseñar para experiencias compartidas, es importante definir los escenarios de destino. Estos escenarios ayudan a aclarar lo que está diseñando y establecen un vocabulario común para ayudar a comparar y contrastar las características necesarias en su experiencia. Entender el problema principal y las diferentes vías para las soluciones es clave para detectar las oportunidades inherentes a este nuevo medio.

A través de los prototipos internos y las exploraciones de nuestras agencias de asociados de HoloLens, creamos seis preguntas que le ayudarán a definir escenarios compartidos. Estas preguntas forman un marco de trabajo, no pretende ser exhaustiva, para ayudar a descartar los atributos importantes de sus escenarios.

### <a name="1-how-are-they-sharing"></a>1. ¿cómo se comparten?

Una presentación podría ser dirigida por un único usuario virtual, mientras que varios usuarios pueden colaborar, o bien un profesor podría proporcionar orientación a los estudiantes virtuales que trabajan con materiales virtuales, lo que aumenta la complejidad de las experiencias en función del nivel de agencia que tiene un usuario o puede tener en un escenario.

![Hombre y mujer con holograph en la tabla](images/man-and-women-with-holograph-on-table-500px.png)

Hay muchas maneras de compartir, pero encontramos que la mayoría de ellas se dividen en tres categorías:

* **Presentación**: cuando el mismo contenido se muestra a varios usuarios. Por ejemplo: un profesor está ofreciendo una conferencia a varios estudiantes con el mismo material holográfica que se presenta a todos. Sin embargo, el profesor podría tener sus propias sugerencias y notas que es posible que no sean visibles para otras personas.
* **Colaboración**: cuando los usuarios trabajan juntos para lograr algunos objetivos comunes. Por ejemplo: el profesor dio un proyecto para obtener información sobre cómo realizar una cirugía cardíaca. Los estudiantes se emparejan y crean una experiencia de laboratorio de habilidades compartidas que permite a los estudiantes médicos colaborar en el modelo de corazón y aprender.
* **Guía**: cuando una persona está ayudando a alguien a resolver un problema en una interacción de estilo uno a uno más. Por ejemplo: el profesor le ofrece orientación a un estudiante cuando está llevando a cabo el laboratorio de aptitudes del corazón en la experiencia compartida.

### <a name="2-what-is-the-group-size"></a>2. ¿Cuál es el tamaño del grupo?

Las experiencias de uso compartido **uno a uno** pueden proporcionar una línea base sólida y, idealmente, se pueden crear pruebas de concepto en este nivel. Pero tenga en cuenta que el uso compartido con grupos de gran tamaño (más allá de 6 personas) puede provocar dificultades tanto técnicas (de datos como de red) y sociales (el impacto de estar en un salón con [varios avatares](https://vimeo.com/160704056)). La complejidad aumenta exponencialmente a medida que avanza de **grupos** **pequeños** a grandes.

Hemos descubierto que las necesidades de los grupos pueden dividirse en tres categorías de tamaño:
* 1:1
* Small < 7
* > Grande = 7

El tamaño de grupo hace una pregunta importante porque influye en lo siguiente:

* Representaciones de personas en el espacio holográfica
* Escala de objetos
* Escala del entorno

### <a name="3-where-is-everyone"></a>3. ¿Dónde está todos?

La fuerza de la realidad mixta entra en juego cuando una experiencia compartida puede tener lugar en la misma ubicación. Llamamos a esa **Ubicación**. Por el contrario, cuando se distribuye el grupo y al menos un participante no está en el mismo espacio físico (lo que suele ser el caso con VR), se llama una **experiencia remota**. A menudo, es el caso de que el grupo **tenga participantes colocalizados** y remotos (por ejemplo, dos grupos en salas de conferencias).

![Tres personas con holograph en la tabla](images/three-people-with-holograph-on-table-500px.png)

Las categorías siguientes ayudan a transmitir dónde se encuentran los usuarios:

* **Ubicación compartida**: todos los usuarios estarán en el mismo espacio físico.
* **Remoto**: todos los usuarios estarán en espacios físicos independientes.
* **Ambos**: los usuarios serán una combinación de espacios colocalizados y remotos.

Esta pregunta es fundamental porque influye en lo siguiente:

* ¿Cómo se comunican las personas?
    * Por ejemplo: ¿si deben tener avatars?
* Qué objetos ven. ¿Están todos los objetos compartidos?
* ¿Si necesitamos adaptarse a su entorno?

### <a name="4-when-are-they-sharing"></a>4. ¿Cuándo están compartiendo?

Normalmente pensamos en experiencias **sincrónicas** cuando las experiencias compartidas van a tener en cuenta: estamos haciendo todo juntos. Pero si se incluye un único elemento virtual que agregó otro usuario, tenemos un escenario **asincrónico** . Imagine una nota, o memorando de voz, que se deja en un entorno virtual. ¿Cómo se controlan 100 memorandos virtuales que quedan en el diseño? ¿Qué ocurre si proceden de docenas de personas con distintos niveles de privacidad?

Tenga en cuenta sus experiencias como una de estas categorías de tiempo:

* **Sincrónicamente**: compartir la experiencia holográfica al mismo tiempo. Por ejemplo: dos estudiantes que realizan el laboratorio de aptitudes al mismo tiempo.
* **Asincrónicamente**: compartir la experiencia holográfica en momentos diferentes. Por ejemplo: dos estudiantes que realizan el laboratorio de aptitudes, pero trabajan en secciones independientes en distintos momentos.
* **Ambos**: a veces, los usuarios compartirán sincrónicamente pero otras veces de forma asincrónica. Por ejemplo: un profesor está evaluando la asignación que realizan los estudiantes en un momento posterior y saliendo de las notas para los estudiantes el día siguiente.

Esta pregunta es importante porque influye en lo siguiente:

* Persistencia de objetos y entornos. Por ejemplo: almacenar los Estados para poder recuperarlos.
* Perspectiva del usuario. Por ejemplo: quizás recuerda lo que estaba buscando el usuario al pasar notas.

### <a name="5-how-similar-are-their-physical-environments"></a>5. ¿son similares los entornos físicos?

La probabilidad de dos entornos de vida real idénticos, fuera de las experiencias colocalizadas, es ligera a menos que dichos entornos se hayan diseñado para ser idénticos. Es más probable que tenga entornos **similares** . Por ejemplo, las salas de conferencias son similares, por lo general tienen una tabla ubicada centralmente entre sillas. Por otro lado, los salones de vida suelen ser **diferentes** y pueden incluir cualquier número de piezas de mobiliario en una matriz infinita de diseños.

![Holograph en la tabla](images/holograph-on-table-500px.png)

Tenga en cuenta que las experiencias de uso compartido se encajan en una de estas dos categorías:

* **Similar**: entornos que tienden a tener mobiliario similar, luz de ambiente y sonido, tamaño físico de la sala. Por ejemplo: el profesor está en la Conferencia de la sala A y los estudiantes están en la sala Hall B. el salón de la Conferencia a puede tener menos sillas que B, pero ambos pueden tener un escritorio físico en el que colocar los hologramas.
* **Diferente**: entornos que son bastante diferentes en la configuración de mobiliario, tamaños de sala, consideraciones claras y de sonido. Por ejemplo: un profesor está en una sala de enfoque, mientras que los estudiantes se encuentran en un salón de conferencia grande, con estudiantes y profesores.

Es importante pensar en [el entorno](environment-considerations-for-hololens.md), ya que influirá en:

* Cómo los usuarios experimentarán estos objetos. Por ejemplo: Si la experiencia funciona mejor en una tabla y el usuario no tiene ninguna tabla, O en una superficie plana, pero el usuario tiene un espacio abarrotado.
* Escala de los objetos. Por ejemplo, la colocación de un modelo humano de 6 metros en una tabla puede ser desafiante, pero un modelo de corazón funcionará bien.

### <a name="6-what-devices-are-they-using"></a>6. ¿Qué dispositivos usan?

En la actualidad, es probable que vea experiencias compartidas entre dos [**dispositivos envolventes**](immersive-headset-hardware-details.md) (estos dispositivos pueden diferir ligeramente en cuanto a botones y funcionalidad relativa, pero no en gran medida) o dos **dispositivos holográficas** según las soluciones de destino. en estos dispositivos. Pero tenga en cuenta si los **dispositivos 2D** (un observador o un participante móvil o de escritorio) serán una consideración necesaria, especialmente en situaciones de **dispositivos 2D y 3D mixtos**. La comprensión de los tipos de dispositivos que van a utilizar los participantes es importante, no solo porque tienen distintas posibilidades y restricciones de datos y fidelidad, pero dado que los usuarios tienen expectativas únicas para cada plataforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Exploración del potencial de experiencias compartidas

Las respuestas a las preguntas anteriores se pueden combinar para comprender mejor el escenario compartido, Crystallizing los desafíos a medida que amplía la experiencia. Para el equipo de Microsoft, esto ayudó a establecer un mapa de carreteras para mejorar las experiencias que usamos hoy en día, entendiendo el Matic de estos problemas complejos y cómo aprovechar las experiencias compartidas en la realidad mixta.

Por ejemplo, considere uno de los escenarios de Skype desde el lanzamiento de HoloLens: un usuario ha trabajado en [Cómo corregir un conmutador de luz rota](https://www.youtube.com/watch?v=iBfzs3G8BEA) con ayuda de un experto ubicado de forma remota.

![Corrección de un interruptor ligero con asistencia a través de Skype para HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Un experto proporciona una guía de **1:1** de su equipo de escritorio **2D**a un usuario de un dispositivo **3D de realidad mixta** . Las **instrucciones** son **sincrónicas** y los entornos físicos son **distintos**.*

Una experiencia como esta es un cambio de paso de nuestra experiencia actual: aplicar el paradigma de vídeo y voz a un nuevo medio. Pero en el futuro, debemos definir mejor la oportunidad de nuestros escenarios y crear experiencias que reflejen la seguridad de la realidad mixta.

Considere la [herramienta de colaboración](https://www.youtube.com/watch?v=XtUyUJAVQ6w)en la vista, desarrollada por el laboratorio de propulsión de jet de la NASA. Los científicos que trabajan en los datos de las misiones de Marte Rover pueden colaborar con sus colegas en tiempo real con los datos del entorno Martian.

![Colaborar entre colegas separados de forma remota para planear el trabajo de Marte Rover](images/onsight-nasa-jpl.gif)

*Un científico explora un entorno mediante un dispositivo **3D de realidad mixta** con un **pequeño** grupo de compañeros **remotos** que usan dispositivos **3D y 2D** . La **colaboración** es **sincrónica** (pero se puede revisar de forma asincrónica) y los entornos físicos son (prácticamente) **similares**.*

Experiencias como la vista actual presentan nuevas oportunidades de colaboración. Desde señalar físicamente los elementos del entorno virtual hasta el lado de un colega y compartir su perspectiva a medida que explican sus hallazgos. En la vista se usa la lente de inmersión y presencia para replantear experiencias de uso compartido en la realidad mixta.

La colaboración intuitiva es el cimientos de conversación, trabajando conjuntamente y comprender cómo podemos aplicar este Intuition a la complejidad de la realidad mixta es fundamental. Si no solo se pueden volver a crear experiencias de uso compartido en la realidad mixta pero se sobrecargan, será un cambio de paradigma para el futuro del trabajo. El diseño de experiencias compartidas en la realidad mixta es un espacio nuevo y emocionante, y solo estamos al principio.

## <a name="get-started-building-shared-experiences"></a>Introducción a la creación de experiencias compartidas

En función de la aplicación y el escenario, habrá varios requisitos para lograr la experiencia deseada. Algunos de ellos incluyen:

* **Coincidencia**: capacidad de crear sesiones, anunciar sesiones, detectar e invitar a personas específicas, tanto de forma local como remota para unirse a la sesión.
* **Uso compartido de delimitadores**: capacidad de alinear las coordenadas entre varios dispositivos en un espacio local común, por lo que los hologramas aparecen en el mismo lugar para todas las personas.
* **Redes**: capacidad de tener puestos, interacciones y movimientos de personas y hologramas sincronizados en tiempo real en todos los participantes.
* **Almacenamiento de estado**: capacidad de almacenar características y ubicaciones de hologramas en el espacio para la Unión a la sesión intermedia, recuperar en un momento posterior y solidez frente a problemas de red.

La clave de las experiencias compartidas tiene varios usuarios que ven los mismos hologramas en el mundo en su propio dispositivo, que se suelen realizar mediante el uso compartido de los anclajes para alinear las coordenadas entre los dispositivos.

Para compartir los delimitadores, use los [anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors):

* En primer lugar, el usuario coloca el holograma.
* La aplicación crea un [delimitador espacial](spatial-anchors.md)para anclar ese holograma exactamente en el mundo.
* Los delimitadores se pueden compartir en dispositivos de HoloLens, iOS y Android a través de los [anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/).

Con un delimitador espacial compartido, la aplicación en cada dispositivo tiene ahora un [sistema de coordenadas común](coordinate-systems.md) en el que puede colocar el contenido. Ahora la aplicación puede asegurarse de colocar y orientar el holograma en la misma ubicación.

En los dispositivos HoloLens, también puede compartir los delimitadores sin conexión de un dispositivo a otro.  Use los vínculos siguientes para decidir qué es lo mejor para su aplicación.

## <a name="evaluating-tech-options"></a>Evaluación de las opciones técnicas

Hay varias opciones de servicio y tecnología disponibles para ayudar a crear experiencias de realidad mixta de varios usuarios.  Puede ser complicado elegir una ruta de acceso, por lo que tomar una perspectiva centrada en el escenario, algunas opciones se detallan a continuación.

## <a name="shared-static-holograms-no-interactions"></a>Hologramas estáticos compartidos (sin interacciones)

Aproveche los [anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/) en la aplicación.  Habilitar y compartir anclajes espaciales entre dispositivos permite crear una aplicación en la que los usuarios ven los hologramas en el mismo lugar al mismo tiempo.  Se necesita sincronización adicional entre dispositivos para permitir que los usuarios puedan interactuar con los hologramas y ver los movimientos o las actualizaciones de estado de los hologramas.

## <a name="share-1st-person-perspective"></a>Compartir perspectiva de 1ª persona

Aproveche la compatibilidad integrada de Miracast para usuarios locales cuando tenga un receptor de Miracast compatible, como un equipo o TV, no se necesita código de aplicación adicional.

Aproveche [MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) en la aplicación, para los usuarios remotos o si tiene dispositivos no Miracast en los que desea compartir.  Al habilitar una conexión WebRTC, se habilitan las secuencias de audio/vídeo de 1:1 entre los usuarios, con un canal de datos para mensajería en todos los dispositivos.  La implementación de realidad mixta optimiza para HoloLens, ya que proporciona una secuencia de vídeo de captura de realidad mixta de la vista del usuario de HoloLens a otros usuarios.  Si desea escalar verticalmente el streaming de vídeo a varios clientes remotos, normalmente se usa un [proveedor de servicios MCU](https://webrtcglossary.com/mcu/) (unidad de conferencia Multipoint), como [SignalWire](https://signalwire.com/).  Hay disponible una implementación de SignalWire de un solo clic en Azure a través de [FreeSwitch](https://github.com/andywolk/azure-freeswitch-gpu-windows).

> [!NOTE]
> Tenga en cuenta que SignalWire es un servicio de pago y no pertenece a Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Presenter: aplicaciones y demostraciones de Spectator

Aproveche [MixedReality-SpectatorView](https://github.com/microsoft/MixedReality-SpectatorView) para incorporar la [funcionalidad de visualización de Spectator](spectator-view.md) a la aplicación.  Habilite otros dispositivos (cámaras HL, Android, iOS y vídeo) para ver qué ve HoloLens desde una perspectiva diferente en la misma ubicación y recibir actualizaciones de las interacciones del usuario de HoloLens del host que interactúa con los hologramas.  Vea, tome fotografías y grabe vídeo sobre lo que hace el host con los hologramas en la aplicación desde su propia perspectiva espacial con el complemento Spectator de la misma aplicación.

**Nota:** Las imágenes se realizan a través de la captura de pantalla en dispositivos iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Experiencia de colaboración de varios usuarios

Comience con nuestro [tutorial de aprendizaje multiusuario](mrlearning-sharing(photon)-ch1.md), que aprovecha los [anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/) para los usuarios locales y el [SDK de Photon](https://www.photonengine.com/PUN) para sincronizar el contenido o el estado de la escena. Cree aplicaciones de colaboración local en las que cada usuario tenga su propia perspectiva en los hologramas de la escena y pueda interactuar completamente con los hologramas.  Las actualizaciones se proporcionan en todos los dispositivos y la administración de conflictos de interacción se controla mediante Photon.

> [!NOTE]
> Tenga en cuenta que [Photon](https://www.photonengine.com/) es un producto que no es de Microsoft, por lo que es posible que se necesite una relación de facturación con Photon para la producción y el escalado para un uso más alto.

## <a name="future-work"></a>Trabajo futuro

Las funciones e interfaces de los componentes le ayudarán a proporcionar una sólida compatibilidad y coherencia comunes en los distintos escenarios y tecnologías subyacentes.  Hasta entonces, elija la mejor ruta de acceso que se alinee con el escenario que está intentando lograr en la aplicación.

¿Hay otro escenario o desea usar un técnico o un servicio diferente? Proporcione comentarios como problemas de GitHub en el repositorio correspondiente, en la parte inferior de esta página, o bien, puede ponerse en contacto con el [margen de HoloDevelopers](https://holodevelopers.slack.com/).

## <a name="see-also"></a>Consulta también

* [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors)
* [Delimitadores espaciales compartidos en DirectX](shared-spatial-anchors-in-directx.md)
* [Experiencias compartidas en Unity](shared-experiences-in-unity.md)
* [Vista del espectador](spectator-view.md)
