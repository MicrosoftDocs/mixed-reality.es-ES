---
title: 'Tutoriales de funcionalidades para varios usuarios: 1. Configuración de redes Photon Unity'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: d879144c7097d8b3873618f986b9f169e8553fa8
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553823"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. configuración de redes Photon Unity

## <a name="overview"></a>Información general

En este tutorial, obtendrá información sobre cómo prepararse para crear una experiencia compartida mediante la importación de Photon Unity Networking (BURDO) en el proyecto de Unity. Photon es una de las diversas opciones de red disponibles para que los desarrolladores de realidad mixta creen experiencias compartidas. Obtendrá información sobre cómo crear una cuenta de Photon, importar Photon y crear un servidor local opcional.

## <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo crear una cuenta de Photon
* Obtenga información sobre cómo buscar e importar Photon Unity Networking
* Configuración de un servidor local de Photon

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no ha completado los [tutoriales de introducción](mrlearning-base.md) y la serie de tutoriales de los [delimitadores espaciales de Azure](mrlearning-asa-ch1.md) , se recomienda que complete los tutoriales en primer lugar.

* Un equipo Windows 10 configurado con las [herramientas instaladas](install-the-tools.md) correctas
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)

>[!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X. Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="setting-up-photon"></a>Configuración de Photon

1. Configure una cuenta de [Photon](https://dashboard.photonengine.com//Account/SignUp) . Para ir a la página de registro de Photon, haga clic en [este vínculo](https://dashboard.photonengine.com//Account/SignUp). Siga las instrucciones que aparecen en la página de registro para crear la cuenta.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Cree un identificador de aplicación haciendo clic en el botón crear una nueva aplicación.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Seleccione Photon BURDO en el menú desplegable en Photon tipo. A continuación, asígnele un nombre. En este ejemplo, se denomina HoloLensPhotonProject. Una vez finalizado, haga clic en el botón crear.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Vuelva a la página de aplicaciones y debería ver algo parecido a la imagen siguiente. Haga clic en el identificador de la aplicación y cópielo. Péguelo en un lugar en el que pueda acceder fácilmente.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Cree un nuevo proyecto de Unity y asígnele el nombre HLSharingProject. Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulte [la sección "creación de un proyecto de Unity" del módulo base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Una vez que se cargue el proyecto, haga clic en la pestaña almacén de activos, tal como se muestra en la imagen siguiente. A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escriba BURDO y seleccione el recurso Photon BURDO 2-FREE "en los resultados de la búsqueda.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Descargue e importe este recurso presionando los botones descargar e importar.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Una vez que Photon haya completado el proceso de importación, aparecerá el Asistente para burdo. Tome el identificador de la aplicación (que debe estar en el portapapeles) del paso 4, péguelo en el cuadro AppID y presione el botón instalar proyecto.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Después de agregar correctamente el AppID, vaya a Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings in assets. Seleccione la opción usar servidor de nombres y establezca la región fija en US o en su región de servicio de Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Enhorabuena

Ha creado correctamente una cuenta de Photon, ha configurado un servidor de Photon local y ha importado BURDO en Unity. El siguiente paso consiste en configurar el proyecto y permitir las conexiones con otros usuarios para que varios usuarios puedan ver su trabajo.

[Siguiente tutorial: 2. obtener Unity listo para el desarrollo](mrlearning-sharing(photon)-ch2.md)
