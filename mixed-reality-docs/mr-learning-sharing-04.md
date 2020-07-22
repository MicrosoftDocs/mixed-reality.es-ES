---
title: 'Tutoriales sobre las funcionalidades multiusuario: 4. Uso compartido de movimientos de objetos con varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cd8f0cb8888e7225566acc8c4b26aced3e4d977e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306252"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Uso compartido de movimientos de objetos con varios usuarios

En este tutorial, aprenderá a compartir los movimientos de objetos para que todos los participantes de una experiencia compartida puedan colaborar y ver las interacciones de los demás.

## <a name="objectives"></a>Objetivos

* Configurar el proyecto para compartir los movimientos de los objetos
* Aprender a crear una aplicación de colaboración de varios usuarios básica

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregaras elementos prefabricados del tutorial para preparar la escena.

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** y arrastre el elemento prefabricado **TableAnchor** para colocarlo encima del objeto **SharedPlayground** de la ventana Hierarchy (Jerarquía) y agregarlo a la escena como elemento secundario del objeto SharedPlayground:

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Configuración de PUN para crear instancias de los objetos

En esta sección, configurará el proyecto para usar la experiencia Rover Explorer creada durante los [tutoriales de introducción](mr-learning-base-01.md) y definirá dónde se crearán las instancias.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Rover Explorer Prefab** (Elemento prefabricado de explorador rover), asigne el elemento prefabricado **RoverExplorer_Complete_Variant** desde la carpeta de recursos.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Con el objeto secundario **NetworkLobby** seleccionado, en la ventana Jerarquía, expande el objeto **TableAnchor**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Rover Explorer Location** (Ubicación del explorador rover), asigne el objeto secundario TableAnchor > **Table** (Tabla) desde la ventana Hierarchy (Jerarquía).

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Prueba de la experiencia con el movimiento de objetos compartidos

Si ahora compila e implementa el proyecto de Unity en su dispositivo HoloLens y, después, vuelve a Unity, presione el botón Reproducir para entrar en el modo de juego. Mientras la aplicación se ejecuta en HoloLens, verá que el objeto se mueve en Unity cuando lo mueve en HoloLens:

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Enhorabuena

Ha configurado correctamente el proyecto para que los movimientos de los objetos se sincronicen y los usuarios puedan ver que los objetos se mueven cuando otros usuarios los mueven. En el siguiente tutorial, implementará la funcionalidad para alinear la experiencia en el mundo físico. Esto garantizará que los usuarios se vean entre sí en su ubicación física real y, por tanto, los objetos aparezcan en la misma posición y rotación física para todos los usuarios.

[Tutorial siguiente: 5. Integración de Azure Spatial Anchors en una experiencia compartida](mr-learning-sharing-05.md)
