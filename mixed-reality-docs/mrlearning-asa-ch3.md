---
title: MR Learning ASA Module Azure Spatial delimitador de HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c6e902710eebe205b9e944b1bf95a9ddd3bd9044
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293804"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Visualización de los comentarios del delimitador espacial de Azure

En esta lección, aprenderá a proporcionar a los usuarios comentarios sobre la detección de delimitadores, los eventos y el estado al usar delimitadores espaciales de Azure.

Objetivos

* Obtenga información sobre cómo configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA.

* Comprenda y explore los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios

## <a name="instructions"></a>Instrucciones

### <a name="set-up-asa-feedback-ui-panel"></a>Configuración del panel de interfaz de usuario de comentarios de ASA

1. En esta lección, no vamos a usar los botones "SaveAnchorToDisk" y "ShareAnchor", por lo que debe seleccionar ambos botones y desactivar la casilla en el panel Inspector (como se muestra a continuación) para ocultar estos botones.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. A continuación, cree el panel de instrucciones. Para empezar, haga clic con el botón derecho en el botón "instrucciones", mantenga el mouse sobre "objeto 3D" y seleccione "textmeshpro-Text".

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. Ajuste la escala y la posición del texto para que coincida con las instrucciones de la escena. Además, asegúrese de que la alineación para todo el texto está centrada. A continuación, elimine el texto de ejemplo del editor de texto, tal como se muestra en la imagen siguiente.

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Cambie el nombre del objeto TextMeshPro a "FeedbackPanel".
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. En el panel Proyecto, seleccione "recursos" y haga clic con el botón secundario y, a continuación, seleccione "Mostrar en el explorador".
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Ahora, haga clic [aquí](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) para descargar los archivos necesarios en los pasos siguientes.

6. Una vez que se abra el explorador, seleccione la carpeta Assets, la carpeta "ASAmodulesAssets" y copie los archivos de script del módulo de delimitador y los de la carpeta. 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Nota: Si aparece un mensaje emergente que le pregunta si desea sobrescribir el antiguo o conservar el antiguo, asegúrese de que selecciona sobrescribir.

7. Ahora vuelva a la carpeta assets. A continuación, vaya a la carpeta "AzureSpatialAnchorsPlugin", a continuación, a la carpeta Examples y, por último, a la carpeta scripts, y copie el contenedor de demostración de delimitadores espaciales de Azure en esa carpeta. 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Ahora que los archivos se han cargado, asegúrese de que el texto "feedbackpanel" está seleccionado, en la jerarquía de ASA_feedback y haga clic en "Agregar componente" y agregue el script de comentarios de delimitador. para ello, búsquelo y selecciónelo cuando aparezca. 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Arrastre el objeto de texto "feedbackPanel" desde la jerarquía de ASA_Feedback hasta la ranura vacía situada debajo del script, tal como se muestra en la figura siguiente. 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>Enhorabuena

En esta lección se ha aprendido cómo crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia de anclaje espacial de Azure para proporcionar a los usuarios comentarios en tiempo real.


