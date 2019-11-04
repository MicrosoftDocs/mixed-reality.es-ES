---
title: 'Tutoriales de anclaje espacial de Azure: 3. Visualización de los comentarios del delimitador espacial de Azure'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438417"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Mostrar comentarios del delimitador espacial de Azure

En esta lección, aprenderá a proporcionar a los usuarios comentarios sobre la detección de delimitadores, los eventos y el estado al usar los anclajes espaciales de Azure.

## <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA.

* Comprenda y explore los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios

## <a name="instructions"></a>Instrucciones

### <a name="set-up-asa-feedback-ui-panel"></a>Configuración del panel de interfaz de usuario de comentarios de ASA

1. En esta lección, no vamos a usar los botones "SaveAnchorToDisk" y "ShareAnchor", así que seleccione ambos botones y desactive la casilla en el panel del Inspector (como se muestra a continuación) para ocultar estos botones.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Cree el panel de instrucciones. Para empezar, haga clic con el botón derecho en el botón "instrucciones", mantenga el mouse sobre "objeto 3D" y seleccione "textmeshpro-Text".

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. Ajuste la escala y la posición del texto para que coincida con las instrucciones de la escena. Además, asegúrese de que la alineación para todo el texto está centrada. A continuación, elimine el texto de ejemplo del editor de texto, tal como se muestra en la imagen siguiente.

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Cambie el nombre del objeto TextMeshPro a "FeedbackPanel".
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. En el panel Proyecto, seleccione "recursos" y haga clic con el botón secundario y, a continuación, seleccione "Mostrar en el explorador".
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Haga clic [aquí](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) para descargar los archivos necesarios en los pasos siguientes.

6. Una vez que se abra el explorador, seleccione la carpeta assets y, a continuación, la carpeta "ASAmodulesAssets" y copie los archivos de script del módulo de delimitador y los de la carpeta. 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Nota: Si recibe un mensaje emergente que le pregunta si desea sobrescribir el antiguo o conservar el antiguo, seleccione sobrescribir.

7. Vuelva a la carpeta assets. A continuación, vaya a la carpeta "AzureSpatialAnchorsPlugin", seguida de la carpeta Examples y, por último, la carpeta scripts. A continuación, copie el contenedor de demostración de anclajes espaciales de Azure en esa carpeta. 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Ahora que los archivos se han cargado, asegúrese de que el texto "feedbackpanel" está seleccionado en la jerarquía de ASA_feedback, haga clic en "Agregar componente" y agregue el script de comentarios de delimitador buscándolo y seleccionándolo cuando aparezca. 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Arrastre el objeto de texto "feedbackPanel" desde la jerarquía de ASA_Feedback hasta la ranura vacía situada debajo del script, tal como se muestra en la figura siguiente. 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>Enhorabuena

En esta lección, hemos aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia del anclaje espacial de Azure para proporcionar a los usuarios comentarios en tiempo real.


