---
title: Módulo de ASA de aprendizaje de MR Azure delimitador espaciales en HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327567"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Visualización de comentarios de Azure delimitador espacial

En esta lección, aprenderá acerca de cómo proporcionar a los usuarios con sus comentarios sobre la detección de anclaje, eventos y el estado cuando se usa Azure espacial delimitadores.

Objetivos:

* Obtenga información sobre cómo configurar un panel de interfaz de usuario que se muestra información importante acerca de la sesión actual de ASA

* Conocer y explorar elementos de comentarios que el SDK de ASA pone a disposición de los usuarios

  

## <a name="instructions"></a>Instrucciones

### <a name="set-up-asa-feedback-ui-panel"></a>Configurar el Panel de interfaz de usuario de comentarios ASA

1. En esta lección, no vamos a usar el "SaveAnchorToDisk" y "ShareAnchor" botones así que seleccione ambos botones y desactive la casilla de verificación en el panel del inspector (como se muestra a continuación) para ocultar estos botones.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. A continuación, cree el panel de la instrucción. Iniciar haciendo clic en el botón "instructions", mantenga el mouse sobre el "objeto 3D" y seleccione "textmeshpro-text".

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. Ajustar la escala y la posición del texto para que haga coincidir con las instrucciones de la escena. Asegúrese también de que la alineación de todo el texto está centrada. A continuación, elimine el texto de ejemplo del editor de texto, como se muestra en la imagen siguiente.


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Cambie el nombre del objeto TextMeshPro a "FeedbackPanel."
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. En el panel proyecto, seleccione "activos" y haga clic en, seleccione "mostrar en el explorador."
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Ahora, haga clic en [aquí](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) descargar los archivos necesarios en los próximos pasos.

6. Una vez que se abre el explorador, seleccione la carpeta assets y, después, en la carpeta "ASAmodulesAssets" y copie el script de comentarios de delimitador y los archivos de script del módulo de anclaje en la carpeta. 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Nota: Si recibe un mensaje emergente que pregunta si desea sobrescribir la antigua o mantener la antigua, asegúrese de seleccionar sobrescritura.

7. Ahora, vuelva a la carpeta Assets. A continuación, vaya a la carpeta "AzureSpatialAnchorsPlugin", a continuación, la carpeta de ejemplos y, finalmente, en la carpeta de scripts y copie el contenedor de demostración de Azure espacial anclajes en dicha carpeta. 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Ahora que se cargan los archivos, asegúrese de que el texto "feedbackpanel" está seleccionado, en la jerarquía ASA_feedback y haga clic en "agregar el componente" y agregue el script de comentarios de anclaje, búsquelo y selecciónelo cuando aparezca. 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Arrastre el objeto de texto "feedbackPanel" de la jerarquía de ASA_Feedback a la ranura vacía debajo de la secuencia de comandos tal como se muestra en la figura siguiente. 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>Enhorabuena

En esta lección hemos aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia de anclaje espacial de Azure para proporcionar el usuario con comentarios en tiempo real.


