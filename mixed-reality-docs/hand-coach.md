---
title: Autocar manual
description: manos 3D que se desencadenan cuando el sistema no detecta las manos del usuario para ayudarles.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, autocar de mano, auriculares envolvente, MRTK, manos, ayudando a manos
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345674"
---
# <a name="hand-coach"></a>Autocar manual
![Ejemplo: autocar manual](images/HandCoach/MRTK_handCoach.jpg)<br>

El autocar de mano es una práctica con modelo 3D que se desencadena cuando el sistema no detecta las manos del usuario. Esto se implementa como un componente de "enseñanza" que ayuda a guiar al usuario cuando no se ha impartido el gesto. Si los usuarios no han realizado el gesto especificado durante un período, las manos se repetirán con un retraso. El autocar manual se puede usar para representar presionar un botón o recoger un holograma.  

## <a name="hand-coach-provided"></a>Autocar proporcionado

El modelo de interacción actual representa una gran variedad de controles de gestos, como el desplazamiento, la selección desplazada y la derivación cercana. A continuación se muestra una lista completa de los gestos de mano existentes que se proporcionan en<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:

:::row:::
    :::column:::
       ![Ejemplo de Near Select](images/HandCoach/NearSelect.gif)<br>
       **Ejemplo de Near Selected muestra cómo seleccionar botones o cerrar objetos interactivos**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de TAP de Air](images/HandCoach/AirTap.gif)<br>
        **Ejemplo de TAP de Air: se usa para mostrar cómo seleccionar objetos que están lejos**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de movimiento](images/HandCoach/Move.gif)<br>
       **Ejemplo de movimiento de un objeto en el espacio: se usa para mostrar cómo mover un holograma en el espacio**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de giro](images/HandCoach/Rotate.gif)<br>
       **Ejemplo de Rotate: se usa para mostrar cómo se giran los hologramas u objetos**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Ejemplo de escala](images/HandCoach/Scale.gif)<br>
       **Ejemplo de escalado: se usa para mostrar cómo manipular los hologramas para ser más grandes o más pequeños**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de Palm up](images/HandCoach/PalmUp.gif)<br>
        **Ejemplo de Palm up: uso sugerido, para abrir menús**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de HandFlip](images/HandCoach/HandFlip.gif)<br>
       **La forma de voltear la mano: otra manera de abrir los menús de la mano**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de desplazamiento](images/HandCoach/Scoll.gif)<br>
       **Ejemplo de scroll: se usa para desplazarse por una lista o un documento largo**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Conceptos de diseño

En el caso de Hololens2, diseñamos interacciones de mano basadas en instinctual y gestos de mano naturales. Creemos que son intuitivos para la mayoría de los usuarios y, por lo tanto, no crean momentos de aprendizaje de gestos dedicados. En su lugar, creamos el autocar de mano para ayudar a los usuarios que se bloquean o que no están familiarizados con la interacción con los hologramas. Obtenga información sobre estos gestos. Sin un momento de aprendizaje, pensamos que mostrar a los usuarios cómo realizar una acción mediante la demostración sería la mejor opción. En nuestros estudios, encontramos que los usuarios podían averiguar el gesto pero necesitaba un poco de orientación. Si se detecta que un usuario no interactúa con un objeto durante un período, se desencadenaría un autocar de mano que demuestra la colocación correcta de la mano y el dedo. 

### <a name="intuitive"></a>Intuitivo

Al animar las manos, debe ser obvio y shoudn't causar cualquier confusión. La animación de las manos es una representación del gesto que está intentando llevar al usuario a entender su finalidad. 

Por ejemplo, si desea que un usuario presione un botón, se desencadenaría una mano al presionar un botón.

![Ejemplo: autocar de mano cerca de TAP](images/HandCoach/NearSelect_unity.gif)<br>
*Manos del coche que muestra cómo pulsar cerca de una gema*  

### <a name="hand-scale"></a>Escala de mano

Se han probado varios tamaños de mano con los menús de la interfaz de usuario y se ha dado la sensación de que, si las manos eran verdaderas para el tamaño, se dio una menacing pero, si fueran demasiado pequeños, era difícil ver y entender el gesto. 

**Voz sobre y manos**

No se espera que los usuarios puedan escuchar un conjunto de instrucciones a través de la voz y ver instrucciones diferentes a través del autocar manual. Ordene las instrucciones para ayudar a los usuarios a centrarse en la atención en su atención para reducir la sobrecarga organoléptica.


## <a name="can-i-create-my-own"></a>¿Puedo crear mis propios?

Sí. Le recomendamos que cree su propio gesto único para su juego y contribuya de nuevo a la comunidad.
Hemos proporcionado un archivo Maya de una mano RIGGED que se puede usar para la aplicación que se puede descargar aquí: <a href="files/HandCoach_MRTK.zip">descargar HandCoach_MRTK.zip</a>

![Ejemplo de manos animadas en Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Ejemplo de Poking de mano animada un cuadro en Maya*


**Herramienta de creación recomendada**

Entre los artistas 3D, muchos optan por usar [Maya de Autodesk, que es capaz de usar HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar el modo en que se crean los recursos. El archivo de manos proporcionado es un archivo binario Maya, por lo que se recomienda usar Maya para animar y exportar las manos. Si prefiere usar otro programa 3D, aquí se muestra un <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Descargue HandCoachMRTK_FBX.zip</a> para crear su propia configuración del controlador. 

Si se usa el archivo de la mano que se va a descargar, se recomienda reducir el tamaño de las manos en Unity a 0,6.

![Ejemplo: plataforma de autocar manual en Maya](images/HandCoach/MayaExample.png)<br>
*Manos de RIGGED*

### <a name="technical-specs"></a>Especificaciones técnicas

*   El archivo de dos manos está disponible en formato de formato ASCII Maya
*    La mano derecha e izquierda está disponible en formato binario de Maya
*   Establezca el archivo Maya en 24 FPS
*   Dentro del archivo, hay una mano izquierda y derecha que se puede usar para los gestos de dos manos o de una sola mano. La mano derecha solo será visible de forma predeterminada.
*   Se recomienda dejar un búfer de aproximadamente 10 fotogramas al principio y al final de los fundidos
*   Si se anima un objeto con un destino especificado, su procedimiento recomendado es animar a un cuadro predeterminado o a un valor null.
*   Si la mano está animando un objeto físico como un cuadro, el procedimiento recomendado es no animar la traducción en Maya pero esperar a animarla en Unity o en el código.
*   La animación visible debe ser de 1,5 segundos para que se transmita información significativa
*   Cuando se sienta satisfecho con la animación:
    *   Seleccionar todas las uniones y los fotogramas clave de la hornea
    *   Elimine los controladores, seleccione Unions and Mesh y Export como FBX
    *  Si hay varias animaciones, puede usar el exportador de juegos integrado de Maya:https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Exportar desde Maya

Una vez que esté satisfecho con la animación
* Seleccionar todas las uniones: seleccionar > jerarquía

     ![Ejemplo: Ubicación del menú](images/HandCoach/Hierarchy.png)<br>
* Integrar la animación: cambiar a la animación > clave > animación de hornear

     ![Ejemplo: Ubicación del menú](images/HandCoach/BakeAnimation.png)<br>
* Elimine la plataforma de pruebas de controlador: > MainR_Grp o MainL_Grp

     ![Ejemplo: Ubicación del menú](images/HandCoach/ControllerRig.png)<br>

* Exportar como FBX: seleccione JNT + Mesh: file > exportar selección (cuadro de opción) > selección de exportación

     ![Ejemplo: Ubicación del menú](images/HandCoach/OptionBox.png)<br>

     ![Ejemplo: Ubicación del menú](images/HandCoach/SelectionExport.png)<br>

     ![Ejemplo: Ubicación del menú](images/HandCoach/FBXSelection.png)<br>


 Al exportar como FBX y incorporarse a Unity, escale las manos hacia abajo hasta 0,6. Encontramos que este era el equilibrio perfecto para mostrar las manos. 

![Ejemplo: configuración de Unity](images/HandCoach/HandHintScale.png)<br>
*Se encontró la configuración de Unity para HandCoach_R recurso prefabricado en MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementación de manos en el proyecto de Unity

### <a name="best-practices"></a>Procedimientos recomendados
*    Se recomienda reducir verticalmente las manos en Unity en 0,6
*   Las manos se deben reproducir dos veces y, si no se completan, se repiten continuamente hasta que se completa el gesto. Las manos deben repetirse dos veces para asegurarse de que el usuario tiene tiempo para registrarse y ver el gesto. Las manos deben intensificar y desplazarse entre bucles. 
 *  Si las manos de los usuarios son visibles para las cámaras HL2, pero los usuarios no realizan la interacción necesaria, las manos aparecerán después de 10 segundos.
*   Si las manos del usuario no son visibles para las cámaras de HL2, las manos aparecerán después de 5 segundos.  
*   Si se realiza un seguimiento de las manos del usuario mediante las cámaras HL2 en el medio de la animación, la animación se completará y desaparecerá.
*   Si incluye la voz sobre, se recomienda que se corresponda con el gesto de la mano.
*   Si ha aprendido las manos al menos una vez, repita solo el gesto si detecta que el usuario está atascado.
*   Si las posiciones de dedo/mano específicas son críticas, asegúrese de que los usuarios puedan ver claramente estos matices en la animación. Pruebe angulación las manos para que las partes más importantes estén claramente visibles. 
* Si observa distorsión en las manos, debe ir a la configuración de calidad de Unity para aumentar la cantidad de huesos. 
 Vaya a la > Editar configuración del proyecto de Unity > calidad > otros pesos > Blend. Asegúrese de que se seleccionan "4 huesos" para ver uniones suaves. 

   ![Ejemplo: Ubicación del menú](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a>Qué evitar
* Escalar las manos demasiado grandes
* colocar las manos demasiado cerca del usuario
* Las manos solo deben impartirse una vez. La enseñanza en exceso puede causar confusión y desenredado
*   En Unity, descargue la versión más reciente de MRTK aquí:https://github.com/microsoft/MixedRealityToolkit-Unity
    *   Material: Teaching_Hand2
    *   Scripts: Consulte las instrucciones de MRTK para el <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">autocar de MRTK</a>
    *   Configuración por proyecto
        *   Escena establecida en UWP: puede encontrar instrucciones en el [proyecto de configuración de Unity](Configure-Unity-Project.md) para Windows Mixed Reality.

## <a name="see-also"></a>Vea también
* [Interacción: aspectos fundamentales del](interaction-fundamentals.md)
* [Proceso de creación de recursos](asset-creation-process.md)
* [Gestos](gestures.md)
* [Instalar las herramientas](install-the-tools.md)
* [Configuración del proyecto de Unity](Configure-Unity-Project.md)
* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [MRTK 101](mrtk-101.md)
