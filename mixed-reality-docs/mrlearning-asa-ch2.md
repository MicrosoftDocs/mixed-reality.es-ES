---
title: Módulo de ASA de aprendizaje de MR Azure delimitador espaciales en HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4dc36aec4d885fa75ea490446c2d682264049725
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327808"
---
# <a name="persistence-and-sharing-of-azure-spatial-anchors"></a>Persistencia y el uso compartido de Azure delimitadores espaciales

En esta lección, aprenderemos cómo conservar nuestro delimitadores espacial de Azure en varias sesiones de aplicación guardando nuestra información de anclaje en el disco del 2 de HoloLens. También aprenderá cómo compartir esta información de anclaje para otros dispositivos para la alineación de un delimitador de varios dispositivos.

## <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo guardar y recuperar información espacial delimitador de Azure desde el disco local de HoloLens 2, para la persistencia entre sesiones de aplicación

* Obtenga información sobre cómo compartir información de Azure espacial delimitador entre los usuarios en un escenario de varios dispositivo

  

## <a name="instructions"></a>Instrucciones

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Conservar delimitadores de Azure entre sesiones de aplicación: identificador de delimitador en el disco de almacenamiento

1. Buscar y agregar el recurso prefabricado "SaveAnchorToDisk" a la escena. Estos incluyen dos botones, un botón para guardar los identificadores de delimitador de Azure disponibles en el disco 2 de HoloLens y otro para recuperar los identificadores desde el disco.

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Configure cada botón según las instrucciones siguientes
   - Para el botón denominado "SaveToDisk", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método SaveAzureAnchorIDToDisk() del componente de ASAmoduleScript ParentAnchor del objeto.
   
     > Nota: algunos de los botones pueden aparecer la superposición de los otros botones de la escena. No dude en ajustar la posición del botón.
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - Para el botón denominado "GetFromDisk", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método LoadAzureAnchorIDsFromDisk() del componente de ASAmoduleScript ParentAnchor del objeto.

3. Siga las instrucciones de la lección 1 para compilar la aplicación actualizada en el dispositivo. Después de presionar el botón "Crear Azure delimitador", como hizo en la lección anterior, ahora puede guardar el identificador de delimitador de Azure en el disco presionando el botón Guardar en disco.

4. Reiniciar la aplicación, inicie la sesión de Azure, presione el botón "Identificador de delimitador de carga" y, a continuación, presione el botón "Buscar el delimitador de Azure" para buscar el delimitador asociado con el identificador se guardan en el disco. Toda la escena ahora debe ajustarse a su posición, en la ubicación que ha guardado el delimitador anteriormente!

### <a name="share-azure-anchors-between-multiple-devices"></a>Compartir los anclajes de Azure entre varios dispositivos

En esta sección, se obtendrá información sobre cómo compartir el identificador de delimitador de Azure entre varios dispositivos. Esto permitirá que varios dispositivos consultar Azure para el mismo identificador de delimitador, que permite que nuestra hologramas anclados y escenas espacialmente estén alineados. Alineación espacial (ver la mismas hologramas en la misma ubicación física entre varios dispositivos) es clave para local experiencias compartidas en el 2 de HoloLens. Hay muchas maneras para transferir información relativa a los identificadores de azure entre dispositivos, incluidos los métodos describen en las experiencias compartidas Azure espacial delimitadores tutoriales (TODO: Agregar vínculo.) Este ejemplo utiliza un servicio web simple para cargar y descargar los identificadores de delimitador entre dispositivos.

1. Agregue el recurso prefabricado de "ShareAnchor" en la jerarquía. Este recurso prefabricado agrega dos nuevos botones a la escena; uno para cargar información de Id. de anclaje y otro para descargar información de Id. de anclaje. 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Configure cada botón según las instrucciones siguientes

   - Para el botón denominado "SendSharedAnchor", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método ShareAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - Para el botón denominado "GetSharedAnchor", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método GetSharedAzureAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

3. Siga las instrucciones de [lección 1](mrlearning-base-ch1.md). Para compilar la aplicación actualizada en el dispositivo. Después de presionar el botón "Crear Azure delimitador", como hizo en la lección anterior, es posible que ahora compartir el identificador de delimitador de Azure a otros dispositivos presionando el botón compartir a otro dispositivo.

   > Nota: Seleccione el delimitador de elemento primario y desplácese hacia abajo hasta la secuencia de comandos de delimitador de elemento primario. Asegúrese de que el "pin público para compartir" es exclusivo, por lo que cuando lo comparte, sabrá que es suyo que va a compartir. Puede haber miles de usuarios que comparten sus delimitadores de Azure, por lo que esto le permitirá asegurarse de que comparta los delimitadores de Azure correcto.

4. Si tiene otro dispositivo HoloLens 2, inicie la aplicación y, a continuación, iniciar la sesión de Azure. Presione el botón "Obtener el identificador de delimitador compartido" y, a continuación, presione el botón "Buscar el delimitador de Azure" para buscar el delimitador asociado con el identificador se guardan en el disco. Toda la escena ahora debe ajustarse a su posición, en donde se colocó en el otro dispositivo HoloLens 2. Si tiene sólo un 2 HoloLens, puede aún probar la funcionalidad mediante el reinicio de la aplicación, iniciar la sesión de Azure y, a continuación, presione el botón "Obtener el identificador de delimitador compartido" y, a continuación, presione el botón "Buscar el delimitador de Azure" para buscar el delimitador asociado con el identificador se guardan en el disco. Toda la escena ahora debe ajustarse a su posición, en la ubicación que ha guardado el delimitador anteriormente!

## <a name="congratulations"></a>Enhorabuena
En esta lección ha aprendido cómo conservar los delimitadores espacial de Azure entre sesiones de aplicación y los reinicios de aplicación al guardar el identificador de delimitador espacial de Azure en el disco local de HoloLens 2. También ha aprendido cómo compartir Azure espacial delimitadores entre varios dispositivos para una experiencia básica holograma multiusuario, estáticos compartido!

Se obtendrá información sobre cómo implementar Azure espacial delimitadores como parte de una experiencia totalmente interactiva de compartido local durante la última lección del módulo de uso compartido. Una experiencia de uso compartido local puede incluir funcionalidad como identificadores de objeto 3D sincronizado posición, rotación y escala, para cada usuario y compartir los Estados de la aplicación. Delimitadores espacial Azure mejora estos escenarios compartidos proporcionando cada participante con un delimitador común que permite a los usuarios ver los objetos virtuales en la misma ubicación física. Esto es cierto en una variedad de plataformas de dispositivos, incluidos los dispositivos HoloLens, iOS y Android. Para obtener información sobre cómo desarrollar una experiencia compartida, complete todas las lecciones del módulo de recursos compartidos.

En la lección siguiente, se obtendrá información sobre cómo proporcionar comentarios en tiempo real a los usuarios. Esta información incluirá información sobre la creación de anclaje, la calidad de comprensión del entorno y el estado de la sesión de Azure. Sin comentarios, los usuarios que no sepa si un delimitador ha sido correctamente la carga en Azure, si la calidad del entorno es suficiente para la creación de delimitador o el estado actual.

[Siguiente lección: Lección 3 de ASA](mrlearning-asa-ch3.md)

