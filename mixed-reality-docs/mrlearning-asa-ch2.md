---
title: 'Tutoriales de anclaje espacial de Azure: 2. Guardar, recuperar y compartir anclajes espaciales de Azure'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4e60ed844e64d736c268dd3ec8453c6c2cb7ad75
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702046"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Guardar, recuperar y compartir anclajes espaciales de Azure

En este tutorial, veremos cómo guardar los anclajes espaciales de Azure en varias sesiones de la aplicación. para ello, guardamos la información de delimitador en el disco de HoloLens 2. También aprenderá a compartir esta información de delimitador en otros dispositivos para una alineación de delimitador de varios dispositivos.

## <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo guardar y recuperar información del delimitador espacial de Azure desde el disco local de HoloLens 2 para la persistencia entre sesiones de aplicación

* Aprenda a compartir información de delimitador espacial de Azure entre usuarios en un escenario de varios dispositivos

## <a name="instructions"></a>Instrucciones

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Persistencia de los delimitadores de Azure entre sesiones de aplicación: guardar el ID. de delimitador en el disco

1. Busque y agregue SaveAnchorToDisk recurso prefabricado a su escena. Estos incluyen dos botones, un botón para guardar cualquier identificador de delimitador de Azure disponible en el disco de HoloLens 2 y otro para recuperar los identificadores del disco.

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Configure cada botón según las instrucciones siguientes.

   - En el caso del botón denominado SaveToDisk, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método SaveAzureAnchorIDToDisk () desde el componente ASAmoduleScript del objeto ParentAnchor.
   
     > Nota: algunos de los botones pueden aparecer superpuestos con los demás botones de la escena. No dude en ajustar la posición del botón.

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - En el caso del botón denominado GetFromDisk, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método LoadAzureAnchorIDsFromDisk () desde el componente ASAmoduleScript del objeto ParentAnchor.

3. Siga las instrucciones de tutoiral 1 para compilar la aplicación actualizada en el dispositivo. Después de presionar el botón crear anclaje de Azure, como hizo en la lección anterior, puede guardar el identificador de delimitador de Azure en el disco presionando el botón Guardar en el disco.

4. Reinicie la aplicación, inicie la sesión de Azure, presione cargar identificador de delimitador y, a continuación, presione buscar delimitador de Azure para ubicar el delimitador asociado con el ID. que hemos guardado en el disco. La escena completa ahora debe ajustarse a la posición, en la ubicación en la que guardó el delimitador previamente.

### <a name="share-azure-anchors-between-multiple-devices"></a>Compartir anclajes de Azure entre varios dispositivos

En esta sección, aprenderá a compartir el identificador de delimitador de Azure entre varios dispositivos. Esto permitirá que varios dispositivos consulten Azure para el mismo identificador de delimitador, lo que permite alinear espacialmente los hologramas y las escenas anclados. La alineación espacial (ver los mismos hologramas en la misma ubicación física entre varios dispositivos) es fundamental para las experiencias compartidas locales en HoloLens 2. Hay muchas maneras de transferir información relacionada con los identificadores de Azure entre dispositivos, incluidos los métodos descritos en los tutoriales de experiencias compartidas de los delimitadores espaciales de Azure (TODO: Agregar vínculo). En este ejemplo se usa un servicio web simple para cargar y descargar los ID. de delimitador entre dispositivos.

1. Agregue el recurso prefabricado ShareAnchor en la jerarquía. Este recurso prefabricado agrega dos nuevos botones a la escena. uno para cargar información de identificador de delimitador y otro para descargar información de identificador de delimitador. 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Configure cada botón según las instrucciones siguientes.

   - En el caso del botón denominado, SendSharedAnchor, cree un nuevo evento bajo el desencadenador de eventos presionado de botón, así como el desencadenador de evento on click. Arrastre el objeto ParentAnchor al campo vacío y asigne el método ShareAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - En el caso del botón denominado, GetSharedAnchor, cree un nuevo evento bajo el desencadenador de eventos presionado de botón, así como el desencadenador de evento on click. Arrastre el objeto ParentAnchor al campo vacío y asigne el método GetSharedAzureAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.

3. Siga las instrucciones del [tutorial 1](mrlearning-base-ch1.md). para compilar la aplicación actualizada en el dispositivo. Después de presionar el botón crear anclaje de Azure, como hizo en la lección anterior, ahora puede compartir el identificador de delimitador de Azure con otros dispositivos si presiona el botón compartir en otro dispositivo.

   > Nota: Seleccione el delimitador primario y desplácese hacia abajo hasta el script de delimitador primario. Asegúrese de que el PIN de uso compartido público sea único, de modo que cuando lo comparta, sepa que es suyo que está compartiendo. Podría haber miles de usuarios compartiendo sus delimitadores de Azure, por lo que hacerlo le permitirá asegurarse de que comparte los delimitadores de Azure correctos.

4. Si tiene otro dispositivo HoloLens 2, inicie la aplicación y, a continuación, inicie la sesión de Azure. Presione el botón obtener identificador de delimitador compartido y, a continuación, presione el botón buscar delimitador de Azure para ubicar el delimitador asociado con el ID. que hemos guardado en el disco. La escena completa ahora debe ajustarse a la posición, en el lugar donde se colocó en el otro dispositivo HoloLens 2. Si solo tiene un HoloLens 2, puede probar la funcionalidad reiniciando la aplicación, iniciando la sesión de Azure y, a continuación, presione el botón de botón "obtener identificador de delimitador compartido" y, a continuación, presione el botón buscar delimitador de Azure para buscar el delimitador asociado al IDENTIFICADOR que hemos guardado en el disco. La escena completa ahora debe ajustarse a la posición, en la ubicación en la que guardó el delimitador previamente.

## <a name="congratulations"></a>Enhorabuena
En esta lección ha aprendido a conservar los anclajes espaciales de Azure entre las sesiones de aplicación y los reinicios de aplicación al guardar el identificador de delimitador espacial de Azure en el disco local en HoloLens 2. También aprendió a compartir anclajes espaciales de Azure entre varios dispositivos para una experiencia de uso compartido de hologramas estáticos y multiusuario.

Aprendemos a implementar anclajes espaciales de Azure como parte de una experiencia compartida local totalmente interactiva durante la lección final del módulo de uso compartido. Una experiencia de uso compartido local puede incluir funciones como la posición del objeto en 3D sincronizado, la rotación y la escala, los identificadores de cada usuario y los Estados de la aplicación compartida. Los delimitadores espaciales de Azure mejoran estos escenarios compartidos proporcionando a cada participante un delimitador común que permite a todos los usuarios ver los objetos virtuales en la misma ubicación física. Esto es cierto en una variedad de plataformas de dispositivos, incluidos los dispositivos HoloLens, Android e iOS. Para obtener información sobre cómo desarrollar una experiencia compartida, complete todas las lecciones del módulo de uso compartido.

En la lección siguiente, aprenderá a proporcionar a los usuarios comentarios en tiempo real. Estos comentarios incluirán información sobre la creación del delimitador, la calidad de la comprensión del entorno y el estado de la sesión de Azure. Sin comentarios, es posible que los usuarios no sepan si un delimitador se ha cargado correctamente en Azure, si la calidad del entorno es suficiente para la creación del delimitador o el estado actual.

[Siguiente lección: 3. Visualización de comentarios de Azure Spatial Anchors](mrlearning-asa-ch3.md)

