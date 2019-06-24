---
title: Módulo de ASA de aprendizaje MR Azure delimitador espacial en HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327292"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (corregirme si estoy equivocado)

En esta lección, 

Objetivos:

* Obtenga información sobre cómo ___

* Obtenga información sobre cómo ___

  

## <a name="instructions"></a>Instrucciones

### <a name="setting-up-photon"></a>Configurar Photon

1. Configurar un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) cuenta. Esto constará de imputar su correo electrónico y realizar algunos pasos de comprobación.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Una vez que se registre, haga clic en el SDK. Una vez que esté en esa página, haga clic en "servidor" y asegurarse de que dice, "alojado en sí mismo." A continuación, desplácese hacia abajo y haga clic en "servidor" tal como se muestra en la segunda imagen abajo.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Esto hará que aparezca con la etiqueta, un cuadro de texto "me lees." Continúe y leerlo. Una vez finalizado, haga clic en el vínculo situado junto a "downloadSDK" para descargarla.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Haga doble clic en la carpeta una vez que termine la descarga.  Una vez que el Explorador de archivos abre revelar la carpeta del SDK, copie la carpeta del SDK.
   
   - El siguiente paso sería entrar en la unidad C: de windows y crear una nueva carpeta denominada "server".
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Ahora abra la carpeta y pegue la carpeta del SDK que copió anteriormente.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Una vez que se ha completado, abra la carpeta del SDK y vaya a "implementar", a continuación, "bin_Win64", a continuación, haga doble clic en "control photon".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Nota: Si tiene alguna pregunta sobre la dirección IP o alguna otra pregunta similar, puede encontrar la mayor parte de su información en la barra de herramientas (como se muestra en la imagen siguiente).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Ahora que el servidor está configurado y se inicia, vuelva al sitio Web de Photon y haga clic en el icono del perfil (aplicar la conversión boxing en la imagen siguiente) y seleccione "las aplicaciones".
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Crear un identificador de aplicación, haga clic en el botón "crear una nueva aplicación".

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Seleccione "Ejecutar Photon" en el menú desplegable bajo "tipo photon". A continuación, asígnele un nombre, (algo que recordaría). En este ejemplo, se lo denominó "HoloLensPhotonProject." Una vez finalizado, haga clic en "crear".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen. Haga clic en el identificador de aplicación y cópielo. Pegar es en algún lugar que puede acceder fácilmente.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Cree un nuevo proyecto de unity. Abra el centro de Unity y haga clic en "nuevo". Asígnele el nombre "HLSharingProject." A continuación, haga clic en crear. 

   > Nota: Esto puede tardar hasta 2 minutos en cargarse, según la velocidad del equipo.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Nota: elegir una ubicación para guardar el proyecto en el equipo cambiando la opción de "ubicación". Guárdelo en un lugar recordará y acceder fácilmente a.

10. Cuando se cargue el proyecto, haga clic en el "almacén de activos". A continuación, en el cuadro de búsqueda que se muestra en la imagen siguiente, escriba en "Juego de palabras" y seleccione el recurso "Photon 2 del juego de palabras libre". 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. ¡Descargue e importe!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Configurar el proyecto de Unity** 

11. Descargue un nuevo recurso necesario para configurar Photon en Unity haciendo [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. En Unity, haga clic en el menú de recursos y seleccione "importar recursos" y luego haga clic en "recursos personalizados".

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Seleccione el paquete de Unity que acaba de descargar desde el vínculo indicado en el paso 1. Una vez que aparece el botón Importar en Unity, haga clic en él.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Nota: donde descargó el paquete a será donde se encuentra. La imagen anterior no describe donde encontrará el paquete.

14. Crear una nueva escena (Esto puede ser lleva a cabo mediante el control o comando + N o haciendo clic en "file" y seleccione "nueva escena."). Guarde la escena como "HLSharedProjectMain."

> Nota: puede recibir un mensaje emergente que tiene un aspecto similar a la siguiente imagen. Por ahora, simplemente haga clic en "no".
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. En "Mixed Reality Toolkit", haga clic en "Agregar a la escena y configurar".

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Una vez completado, un nuevo archivo de configuración aparecerá, lo que le ofrece la opción de personalizar el perfil. Haga clic en "copiar y personalizar".

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Desplácese hacia abajo y desactive la opción "Habilitar sistema de diagnóstico". Así resultará más fácil de configurar este proyecto.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Abra la configuración de compilación (control + MAYÚS + B). Tenga en cuenta que el programa está establecido actualmente en la plataforma "PC, Mac y Linux independiente". Para este proyecto, establezca la plataforma como "plataforma universal de windows". Selecciónelo y haga clic en "Cambiar plataforma".

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Una vez que haya terminado, haga clic en el cuadro que dice "Agregar escenas abiertos". Ahora, vaya al panel de inspector y asegúrese de que la casilla situada a la derecha de "la realidad virtual admitida" (como se muestra en la imagen siguiente) está activada. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Nota: Asegúrese también de que la casilla de verificación situada junto a "escenas/HLSharedProjectMain" también se comprueba.

20. En la "configuración de publicación" en el panel del inspector desplácese hacia abajo hasta "capacidades" y asegúrese de que se marcan solo las siguientes casillas:

- cliente de Internet
- servidor de cliente de Internet
- servidor de cliente de red privada
- camera/webcam
- Micrófono

21. Al igual que el paso 12, el siguiente paso sería importar otro paquete personalizado denominado "Lesson2" que se puede descargar [aquí]. [lesson2.unitypackage vínculo va aquí] Importar ese paquete.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. Ahora, en el panel de proyecto, vaya a la carpeta "prefabricados", puesto que en los pasos siguientes, va a implementar unos prefabricados en la escena. En la carpeta "prefabricados", haga clic y arrastre el prefabricado verá, "DebugWindow" en la jerarquía. Una vez terminado, guarde el proyecto (haga clic en archivo, a continuación, guarde o control + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Nota: Puede que observe un elemento emergente aparece al hacer clic en el prefabricado verá, que le pide sobre Essentials TMP. Haga clic en "Importar TMP Essentials" como será necesaria.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Conectar varios usuarios**

23. Como paso 22, en la carpeta "prefabricados" en el panel de proyecto, el siguiente paso es arrastrar y colocar el recurso prefabricado "NetworkLobby" a la jerarquía. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Cuando abra el recurso prefabricado primario, "NetworkLobby", debería ver a un elemento secundario prefabricado, "NetworkRoom". Con él seleccionado, vaya al panel de inspector y haga clic en "Agregar el componente". Busque "PhotonView" y agregue el componente.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Crear un nuevo objeto de juego vacío en la jerarquía (clic derecho en la jerarquía y seleccione 'empty'). Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y el nombre del objeto, "PhotonUser".

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Enhorabuena



