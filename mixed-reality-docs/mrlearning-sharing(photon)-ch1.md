---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327640"
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

2. Una vez que se registre, haga clic en el SDK. Una vez que esté en esa página, haga clic en "servidor" y asegurarse de que dice, "alojado en sí mismo." A continuación, desplácese hacia abajo y haga clic en "servidor" tal como se muestra en la segunda imagen abajo.

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. Esto hará que aparezca con la etiqueta, un cuadro de texto "me lees." Continúe y leerlo. Una vez finalizado, haga clic en el vínculo situado junto a "downloadSDK" para descargarla.


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. Haga doble clic en la carpeta una vez que termine la descarga.  Una vez que el Explorador de archivos abre revelar la carpeta del SDK, copie la carpeta del SDK.
   
   - El siguiente paso sería entrar en la unidad C: de windows y crear una nueva carpeta denominada "server".
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - Ahora abra la carpeta y pegue la carpeta del SDK que copió anteriormente.
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. Una vez que se ha completado, abra la carpeta del SDK y vaya a "implementar", a continuación, "bin_Win64", a continuación, haga doble clic en "control photon".


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> Nota: Si tiene alguna pregunta sobre la dirección IP o alguna otra pregunta similar, puede encontrar la mayor parte de su información en la barra de herramientas (como se muestra en la imagen siguiente).
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. Ahora que el servidor está configurado y se inicia, vuelva al sitio Web de Photon y asegúrese de que se inició todavía (o iniciarla, si no). Haga clic en el icono del perfil (aplicar la conversión boxing en la esquina superior derecha de la imagen siguiente) y seleccione "las aplicaciones".
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. Crear un identificador de aplicación, haga clic en el botón "crear una nueva aplicación".

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - Seleccione "Juego de palabras Photon" en el menú desplegable bajo "tipo photon". A continuación, asígnele un nombre, en este ejemplo, se lo denominó "HoloLensPhotonProject." Una vez finalizado, haga clic en el botón "Crear".

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen. Haga clic en el identificador de aplicación y cópielo. Pegar es en algún lugar que puede acceder fácilmente.  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. Cree un nuevo proyecto de unity y asígnele el nombre "HLSharingProject." Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [sección "Crear proyecto de Unity" de la Base del módulo](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 


10. Cuando se cargue el proyecto, haga clic en la pestaña "almacén de activos", tal como se muestra en la imagen siguiente. A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba en "Juego de palabras" y seleccione el recurso "Photon 2 del juego de palabras gratuita" desde los resultados de búsqueda. 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. Descargue e importe este activo al presionar los botones "Descargar" y "Import".
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>Enhorabuena

Correctamente ha creado una cuenta de Photon, configurar un servidor local de Photon e importan el juego de palabras en Unity. El siguiente paso es configurar el proyecto y, a continuación, permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo. 

[Siguiente lección: Sharing(Photon) lección 2](mrlearning-sharing(photon)-ch2.md)

