---
title: 'Tutoriales de la comunicación remota holográfica del equipo: 2. Creación de una aplicación para equipos de comunicación remota holográfica'
description: Complete este curso para aprender cómo crear una experiencia de realidad mixta remota del PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 32fccbaf6bae8031572ff716f3c9fc26a43849e5
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306437"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Creación de una aplicación para PC de comunicación remota holográfica

En este tutorial, aprenderá cómo crear una aplicación de PC para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta.

## <a name="objectives"></a>Objetivos

* Configurar Unity para la comunicación remota holográfica
* Aprender a compilar e implementar la aplicación con Visual Studio
* Desarrollar una aplicación de comunicación remota holográfica y conectarla a HoloLens

## <a name="configuring-your-scene-for-holographic-remoting"></a>Configurar la escena para la comunicación remota holográfica

En esta sección, configurará el proyecto para que transmita la experiencia de realidad mixta a su dispositivo HoloLens 2 desde su PC en tiempo real a través de una conexión Wi-Fi.

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** y haga clic y arrastre el elemento prefabricado **HolographicRemoting** a la escena.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a>Compilación de la aplicación para PC

La aplicación de comunicación remota holográfica ya está lista para compilarse en su PC. Siga los pasos que se indican a continuación y realice estos cambios para compilar esta aplicación en su PC.

### <a name="1-set-the-player-settings"></a>1. Configuración del reproductor

En el menú de Unity, seleccione Edit > Project Settings (Editar > Configuración del proyecto) para abrir la ventana Player Settings (Configuración del reproductor):

En la sección **XR Settings** (Configuración de XR), seleccione la casilla **WSA Holographic Remoting Supported** (Admitir la comunicación remota holográfica de WSA) y habilite la comunicación remota holográfica.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Compilación del proyecto de Unity

En el menú de Unity, seleccione File > Build Settings (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), haga clic en el botón ***Add Open Scenes*** (Agregar escenas abiertas) para agregar la escena actual a las escenas. En la lista Build (Compilación), haga clic en el ***botón Build*** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows):

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

En la ventana Build Universal Windows Platform (Compilar Plataforma universal de Windows), elija una ubicación adecuada para almacenar la compilación, como por ejemplo, Mis Documentos\AprendizajeRealidadMixta. Cree una nueva carpeta y asígnele un nombre adecuado, por ejemplo, ComunicaciónRemotaHolográficaPC. A continuación, haga clic en el botón ***Select Folder*** (Seleccionar carpeta) para iniciar el proceso de compilación:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Espere a que Unity finalice el proceso de compilación.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. Compilar e implementar la aplicación

Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación. Navegue dentro de la carpeta y haga doble clic en el archivo .sln para abrirlo en Visual Studio:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que todos los componentes de los requisitos previos estén instalados, tal como se especifica en la documentación Instalación de herramientas.

Configure Visual Studio para PC. Para ello, selecciona la configuración Publicación, la arquitectura x64 y la opción Equipo local como destino:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

Haga clic en el botón que indica ***Equipo local***. Comienza la compilación e implementación de la aplicación en el PC. La aplicación se instalará de forma predeterminada en su PC.

## <a name="testing-holographic-remoting-remote-application"></a>Prueba de la aplicación remota de comunicación remota holográfica

Para conectar la aplicación de PC a HoloLens 2, siga el proceso siguiente:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Instalación de la aplicación Remoting Player en el dispositivo HoloLens 2

* En HoloLens 2, visite la aplicación Store y busque "**Remoting Player**".
* Seleccione la aplicación **Remoting Player**.
* Pulse **Instalar** una vez para descargar e instalar la aplicación.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Conexión de la aplicación de comunicación remota holográfica para PC a Remoting Player

* Inicie **Remoting Player** en HoloLens.
* Tome nota de la **dirección IP** de HoloLens. **Remoting Player** la mostrará como un holograma en cuanto se inicie.
* Abra la aplicación de comunicación remota holográfica para PC en su PC.
* Una vez iniciada la aplicación, escriba la **dirección IP** y haga clic en el botón **Conectar** para conectarse.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió cómo crear una aplicación para la comunicación remota holográfica y a conectarse a HoloLens 2 en cualquier momento, lo que proporciona una manera de visualizar contenido 3D en realidad mixta. Una vez que HoloLens esté conectado a la aplicación de comunicación remota holográfica para PC, debería ver la experiencia de realidad mixta transmitida en el dispositivo HoloLens 2.
