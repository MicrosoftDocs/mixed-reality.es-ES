---
title: 'Tutoriales sobre las funcionalidades multiusuario: 4. Uso compartido de movimientos de objetos con varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610618"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3. Uso compartido de movimientos de objetos con varios usuarios

En este tutorial, aprenderás a compartir los movimientos de objetos para que todos los participantes de una experiencia compartida puedan colaborar y ver las interacciones de los demás.

## <a name="objectives"></a>Objetivos

* Configurar el proyecto para compartir los movimientos de los objetos
* Aprender a crear una aplicación de colaboración de varios usuarios básica

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregaras elementos prefabricados del tutorial para preparar la escena.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Elementos prefabricados) y arrastra el elemento prefabricado **TableAnchor** para colocarlo encima del objeto **SharedPlayground** de la ventana Jerarquía y agregarlo a la escena como elemento secundario del objeto SharedPlayground:

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Configuración de PUN para crear instancias de los objetos

En esta sección, configurarás el proyecto para usar el elemento prefabricado RocketLauncher_Complete_Variant creado en la sección anterior y definir el lugar en el que se creará una instancia de este.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Photon User Prefab** (Elemento prefabricado de usuario de Photon), asigna el elemento **PhotonUser** de la carpeta Recursos.

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

Con el objeto secundario **NetworkLobby** seleccionado, en la ventana Jerarquía, expande el objeto **TableAnchor**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Rocket Launcher Location** (Ubicación del iniciador de Rocket), asigna el objeto secundario **Table** desde la ventana Jerarquía.

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Prueba de la experiencia con el movimiento de objetos compartidos

Si ahora compilas e implementas el proyecto de Unity en tu dispositivo HoloLens y, después, vuelves a Unity, presiona el botón Reproducir para entrar en el Modo Juego. Mientras la aplicación se ejecuta en HoloLens, verás que el objeto se mueve en Unity cuando lo mueves en HoloLens:

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>Enhorabuena

Has configurado correctamente el proyecto para que los movimientos de los objetos se sincronicen y los usuarios puedan ver cuándo otros usuarios mueven los objetos. En el siguiente tutorial, implementarás la funcionalidad para que la experiencia compartida se alinee con el mundo físico y los usuarios se vean entre sí en su ubicación física real, y para que los objetos se muestren en la misma posición física y rotación para todos los usuarios.

[Tutorial siguiente: 4. Integración de Azure Spatial Anchors en una experiencia compartida](mrlearning-sharing(photon)-ch4.md)
