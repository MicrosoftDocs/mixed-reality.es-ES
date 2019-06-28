---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416126"
---
# <a name="setting-up-photon"></a>Configurar Photon

En esta lección, aprenderemos cómo prepararse para la creación de una experiencia compartida importando Photon Unity a redes (juego de palabras) en el proyecto de Unity. Photon es una de varias opciones de red disponibles para los desarrolladores de realidad mixta para crear experiencias compartidas. Se obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.

Objetivos:

* Aprenda a crear la cuenta de Photon

* Obtenga información sobre cómo buscar e importar Unity Photon a redes

* Configurar un servidor local de Photon

  

### <a name="setting-up-photon"></a>Configurar Photon

1. Configurar un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) cuenta. Vaya a la página de registro Photon haciendo clic en [este vínculo](https://dashboard.photonengine.com/en-US/Account/SignUp). Siga las instrucciones de la página de registro para crear la cuenta. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crear un identificador de aplicación, haga clic en el botón "crear una nueva aplicación".

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Seleccione "Juego de palabras Photon" en el menú desplegable bajo "tipo photon". A continuación, asígnele un nombre, en este ejemplo, se lo denominó "HoloLensPhotonProject." Una vez finalizado, haga clic en el botón "Crear".

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen. Haga clic en el identificador de aplicación y cópielo. Pegar es en algún lugar que puede acceder fácilmente.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Cree un nuevo proyecto de unity y asígnele el nombre "HLSharingProject." Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [sección "Crear proyecto de Unity" de la Base del módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Cuando se cargue el proyecto, haga clic en la pestaña "almacén de activos", tal como se muestra en la imagen siguiente. A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba en "Juego de palabras" y seleccione el recurso "Juego de palabras 2 - Photon libre" de los resultados de búsqueda. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Descargue e importe este activo al presionar los botones "Descargar" y "Import".

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Cuando Photon se haya completado el proceso de importación, aparecerá el Asistente de juego de palabras. Tome el identificador de aplicación (que debe estar en el Portapapeles) del paso 4 y péguelo en el cuadro de AppID y presione el botón "Setup Project". 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Después de agregar correctamente el AppID, vaya a "Photon"->"PhotonUnityNetworking" -> "Recursos" -> "PhotonServerSettings" en los activos. Seleccione la opción "Servidor de nombres de uso" y establezca la región fija a "nosotros" o la región del servicio photon.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Enhorabuena

Correctamente ha creado una cuenta de Photon, configurar un servidor local de Photon e importan el juego de palabras en Unity. El siguiente paso es configurar el proyecto y, a continuación, permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo. 

[Siguiente lección: Sharing(Photon) lección 2](mrlearning-sharing(photon)-ch2.md)

