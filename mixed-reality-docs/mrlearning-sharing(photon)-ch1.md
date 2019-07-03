---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523292"
---
#  <a name="setting-up-photon-unity-networking"></a>Configurar redes de Unity Photon

En este tutorial, se obtenga información sobre cómo prepararse para la creación de una experiencia compartida importando Photon Unity a redes (juego de palabras) en el proyecto de Unity. Photon es una de varias opciones de red disponibles para los desarrolladores de realidad mixta para crear experiencias compartidas. Se obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.

Objetivos:

* Obtenga información sobre cómo crear una cuenta de Photon

* Obtenga información sobre cómo buscar e importar Unity Photon a redes

* Configurar un servidor local de Photon

  

### <a name="setting-up-photon"></a>Configurar Photon

1. Configurar un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) cuenta. Vaya a la página de registro Photon haciendo clic en [este vínculo](https://dashboard.photonengine.com/en-US/Account/SignUp). Siga las instrucciones de la página de registro para crear la cuenta. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crear un identificador de aplicación, haga clic en crear un botón de nueva aplicación.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Seleccione el juego de palabras Photon en el menú desplegable bajo tipo Photon. A continuación, asígnele un nombre. En este ejemplo, se lo denominó HoloLensPhotonProject. Una vez finalizado, haga clic en el botón Crear.

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen. Haga clic en el identificador de aplicación y cópielo. Pegar es en algún lugar que puede acceder fácilmente.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Cree un nuevo proyecto de unity y asígnele el nombre HLSharingProject. Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [sección "Crear proyecto de Unity" de la Base del módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Cuando se cargue el proyecto, haga clic en la pestaña activos Store, como se muestra en la imagen siguiente. A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba en el juego de palabras y seleccione el 2 de juego de palabras Photon - FRE"recurso de los resultados de búsqueda. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Descargue e importe este activo al presionar los botones de la descarga e importación.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Cuando Photon se haya completado el proceso de importación, aparece el Asistente de juego de palabras. Tome el identificador de aplicación (que debe estar en el Portapapeles) del paso 4 y péguelo en el cuadro de AppID y presione el botón del proyecto de instalación. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Después de agregar correctamente el AppID, vaya a Photon -> PhotonUnityNetworking -> recursos -> PhotonServerSettings en activos. Seleccione la opción de servidor de nombres de uso y establezca la zona fija para nosotros o yourPphoton servicio de región.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Enhorabuena

Correctamente ha creado una cuenta de Photon, configurar un servidor local de Photon e importan el juego de palabras en Unity. El siguiente paso es configurar el proyecto y, a continuación, permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo. 

[Tutorial siguiente: Cómo prepararse para el desarrollo de Unity](mrlearning-sharing(photon)-ch2.md)

