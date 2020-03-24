---
title: 'Tutoriales sobre las funcionalidades multiusuario: 1. Configuración de Photon Unity Networking'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031332"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Configuración de Photon Unity Networking

## <a name="overview"></a>Introducción

En este tutorial, aprenderás a preparar la creación de una experiencia compartida. Para hacerlo, importarás Photon Unity Networking (PUN) en el proyecto de Unity. Photon es una de las diversas opciones de redes disponibles para que los desarrolladores de Mixed Reality creen experiencias compartidas. Aprenderás a crear una cuenta de Photon, a importar Photon y a crear un servidor local opcional.

## <a name="objectives"></a>Objetivos

* Aprender a crear una cuenta de Photon
* Aprender a buscar e importar Photon Unity Networking
* Configurar un servidor local de Photon

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no has completado los [tutoriales de introducción](mrlearning-base.md) y los [tutoriales de introducción a Azure Spatial Anchors](mrlearning-asa-ch1.md), es recomendable que lo hagas en primer lugar.

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)

>[!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X. Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="setting-up-photon"></a>Configuración de Photon

1. Configura una cuenta de [Photon](https://dashboard.photonengine.com//Account/SignUp). Ve a la página de registro de Photon. Para ello, haz clic en [este vínculo](https://dashboard.photonengine.com//Account/SignUp). Sigue las instrucciones de la página de registro para crear la cuenta.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Crea un identificador de aplicación haciendo clic en el botón Create a New App (Crear una nueva aplicación).

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Selecciona Photon PUN en el menú desplegable, bajo Photon Type (Tipo de Photon). A continuación, asígnale un nombre. En este ejemplo, se denomina HoloLensPhotonProject. Al finalizar, haz clic en el botón Crear.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Vuelve a la página de aplicaciones. Deberías ver algo parecido a la imagen siguiente. Haz clic en el id. de aplicación y cópialo. Ponlo en algún lugar al que puedas acceder fácilmente.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Crea un nuevo proyecto de Unity llamado HLSharingProject. Para obtener instrucciones sobre cómo crear un nuevo proyecto de Unity, consulta [la sección "Crear proyecto de Unity" del módulo base](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Una vez cargado el proyecto, haz clic en la pestaña Assets Store (Almacén de recursos), como se muestra en la imagen siguiente. A continuación, en el cuadro de búsqueda resaltado en la imagen siguiente, escribe PUN y selecciona el recurso Photon PUN 2 - FREE (Photon PUN 2 - GRATUITO) en los resultados de la búsqueda.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Descarga e importa este recurso presionando los botones Download (Descargar) e Import (Importar).

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Cuando Photon complete el proceso de importación, aparecerá el asistente de PUN. Usa el identificador de la aplicación (debe estar en el portapapeles) del paso 4, pégalo en el cuadro AppID y presiona el botón Setup Project (Configurar proyecto).

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Después de agregar correctamente AppID, desplázate a Photon -> PhotonUnityNetworking -> Resources (Recursos) -> PhotonServerSettings en Assets (Recursos). Selecciona la opción de Use Name Server (Usar servidor de nombres) y establece la región fija en US (EE. UU.) o en tu región de servicio de Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Enhorabuena

Has creado correctamente una cuenta de Photon, has configurado un servidor de Photon local y has importado PUN a Unity. El siguiente paso consiste en configurar el proyecto y permitir las conexiones con otros usuarios para que varios usuarios puedan ver tu trabajo.

[Tutorial siguiente: 2. Preparación de Unity para desarrollo](mrlearning-sharing(photon)-ch2.md)
