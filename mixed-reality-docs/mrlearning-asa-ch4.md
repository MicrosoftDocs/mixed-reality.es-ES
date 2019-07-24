---
title: MR Learning ASA Module Azure Spatial delimitador de HoloLens 2
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
# <a name="photon-correct-me-if-im-wrong"></a>Photon (corregir si soy mal)

En esta lección, 

Objetivos

* Obtener información sobre cómo _____________________________________________

* Obtener información sobre cómo _________________________________________________

  

## <a name="instructions"></a>Instrucciones

### <a name="setting-up-photon"></a>Configuración de Photon

1. Configure una cuenta de [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) . Esto consistirá en imputar el correo electrónico y seguir algunos pasos de comprobación.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Una vez que se haya registrado, haga clic en SDK. Una vez que esté en esa página, haga clic en "servidor" y asegúrese de que dice "autohospedado". A continuación, desplácese hacia abajo y haga clic en "servidor" como se muestra en la segunda imagen siguiente.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Esto hará que un cuadro de texto aparezca etiquetado como "Léame". Siga leyendo. Una vez finalizado, haga clic en el vínculo situado junto a "downloadSDK" para descargarlo.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Haga doble clic en la carpeta una vez finalizada la descarga.  Cuando el explorador de archivos se abra y revele la carpeta del SDK, copie la carpeta del SDK.
   
   - El siguiente paso consiste en ir a la unidad C: de Windows y crear una nueva carpeta denominada "Server".
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Ahora, abra la carpeta y pegue la carpeta del SDK que copió anteriormente.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Una vez que se haya completado, abra la carpeta SDK, vaya a "deploy", "bin_Win64" y haga doble clic en "Photon control".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Nota: Si tiene alguna pregunta sobre la dirección IP o cualquier otra pregunta similar, puede encontrar la mayor parte de la información en la barra de herramientas (como se muestra en la imagen siguiente).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Ahora que el servidor está configurado e iniciado, vuelva al sitio web de Photon y haga clic en el icono de perfil (con la conversión boxing de la imagen siguiente) y seleccione "Your Applications".
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Cree un identificador de aplicación haciendo clic en el botón "crear una nueva aplicación".

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Seleccione "Photon ejecutar" en el menú desplegable en "tipo de Photon". A continuación, asígnele un nombre (algo que recordaría). En este ejemplo, se denomina "HoloLensPhotonProject". Una vez finalizado, haga clic en "crear".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la imagen siguiente. Haga clic en el identificador de la aplicación y cópielo. Pegar es un lugar en el que se puede acceder fácilmente.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Cree un nuevo proyecto de Unity. Abra Unity Hub y haga clic en "nuevo". Asígnele el nombre "HLSharingProject". A continuación, haga clic en crear. 

   > Tenga en cuenta Esto puede tardar hasta 2 minutos en cargarse, en función de la velocidad del equipo.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Nota: elija un lugar para guardar el proyecto en el equipo; para ello, cambie la opción "ubicación". Guárdelo en un lugar que recuerde y que tenga fácil acceso a.

10. Una vez que se cargue el proyecto, haga clic en el "almacén de activos". A continuación, en el cuadro de búsqueda que aparece en la imagen siguiente, escriba "BURDO" y seleccione el recurso "Photon BURDO-2 FREE". 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Descargar e importar
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Configuración del proyecto de Unity** 

11. Descargue un nuevo recurso necesario para configurar Photon en Unity. para ello, haga clic [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. En Unity, haga clic en el menú activos y seleccione "importar recursos" y, a continuación, haga clic en "activos personalizados".

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Seleccione el paquete de Unity que acaba de descargar del vínculo proporcionado en el paso 1. Cuando aparezca el botón importar en Unity, haga clic en él.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Nota: dondequiera que haya descargado el paquete, será donde lo encuentre. La imagen anterior no indica dónde encontrará el paquete.

14. Cree una nueva escena (esto puede hacerse mediante control/comando + N o haciendo clic en "archivo" y seleccionando "nueva escena"). Guarde la escena como "HLSharedProjectMain".

> Nota: es posible que reciba un elemento emergente que tenga un aspecto similar a la imagen siguiente. Por ahora, solo tiene que hacer clic en "no".
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. En "kit de herramientas de realidad mixta", haga clic en "Agregar a la escena y configurar".

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Una vez que haya finalizado, aparecerá un nuevo archivo de configuración que le proporcionará la opción de personalizar el perfil. Haga clic en "copiar y personalizar".

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Desplácese hacia abajo y desactive "habilitar el sistema de diagnóstico". Esto facilitará la configuración de este proyecto.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Abra la configuración de compilación (Control + Mayús + B). Tenga en cuenta que el programa está establecido actualmente en la plataforma "PC, Mac y Linux standalone". Para este proyecto, establezca la plataforma en "plataforma universal de Windows". Selecciónelo y haga clic en "cambiar plataforma".

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Una vez que haya finalizado, haga clic en el cuadro que indica "agregar escenas abiertas". Ahora, vaya al panel Inspector y asegúrese de que esté activada la casilla situada a la derecha de "realidad virtual compatible" (como se muestra en la imagen siguiente). 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Tenga en cuenta Asegúrese también de que la casilla situada junto a "Scenes/HLSharedProjectMain" también está activada.

20. En "configuración de publicación" en el panel de inspectores, desplácese hacia abajo hasta "capacidades" y asegúrese de que solo están marcadas las siguientes casillas:

- cliente de Internet
- servidor de cliente de Internet
- servidor cliente de red privada
- cámara o cámara web
- Micrófono

21. Al igual que el paso 12, el paso siguiente sería importar otro paquete personalizado llamado "Lesson2", que se puede descargar [aquí.] [lesson2. unitypackage Tools vínculo va aquí] Importe ese paquete.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. Ahora, en el panel Proyecto, vaya a la carpeta "Prefabs", ya que en los próximos pasos va a implementar algunos Prefabs en la escena. En la carpeta "Prefabs", haga clic y arrastre recurso prefabricado "DebugWindow" a la jerarquía. Cuando haya terminado, guarde el proyecto (haga clic en archivo, después en guardar o en control + S).

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Tenga en cuenta Es posible que observe que aparece una ventana emergente al hacer clic en el recurso prefabricado, donde se le pregunta sobre TMP Essentials. Haga clic en "importar TMP Essentials", ya que se necesitarán.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Conexión de varios usuarios**

23. Al igual que en el paso 22, en la carpeta "Prefabs" del panel Proyecto, el paso siguiente consiste en arrastrar y colocar el NetworkLobby "recurso prefabricado" en la jerarquía. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Al abrir el recurso prefabricado primario, "NetworkLobby", debería ver un recurso prefabricado secundario, "NetworkRoom". Con esta opción seleccionada, vaya al panel Inspector y haga clic en "Agregar componente". Busque "PhotonView" y agregue el componente.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Cree un nuevo objeto de juego vacío en la jerarquía (haga clic con el botón derecho en la jerarquía y seleccione "vacío"). Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y asigne al objeto el nombre "PhotonUser".

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Enhorabuena



