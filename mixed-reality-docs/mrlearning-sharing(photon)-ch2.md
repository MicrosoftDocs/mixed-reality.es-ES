---
title: 'Tutoriales sobre las funcionalidades multiusuario: 3. Conexión de varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610931"
---
# <a name="2-connecting-multiple-users"></a>2. Conexión de varios usuarios

En este tutorial, aprenderás a conectar varios usuarios como parte de una experiencia compartida en directo. Al final del tutorial, podrás ejecutar la aplicación en varios dispositivos y hacer que todos los usuarios vean cómo se mueve el avatar de los demás en tiempo real.

## <a name="objectives"></a>Objetivos

* Aprender a conectar varios usuarios en una experiencia compartida

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Elementos prefabricados). Mientras mantienes presionado el botón CTRL, haz clic en **DebugWindow**, **NetworkLobby** y **SharedPlayground** para seleccionar los tres elementos prefabricados:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

Con los tres elementos prefabricados aún seleccionados, arrástralos a la ventana Jerarquía para agregarlos a la escena:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Creación del elemento prefabricado del usuario

En esta sección, crearás un elemento prefabricado que se usará para representar a los usuarios en la experiencia compartida.

### <a name="1-create-and-configure-the-user"></a>1. Creación y configuración del usuario

En la ventana Jerarquía, haz clic con el botón derecho en un área vacía y selecciona **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena. Asigna al objeto el nombre **PhotonUser** y configúralo de la siguiente manera:

* Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

Con el objeto **PhotonUser** aún seleccionado, en la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon User (Script)** (Usuario de Photon [script]) al objeto PhotonUser:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Generic Net Sync (Script)** (Sincronización neta genérica [script]) al objeto PhotonUser y configúralo de la siguiente manera:

* Selecciona la casilla **Is User** (Es el usuario).

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon View (Script)** (Vista de Photon [script]) al objeto PhotonUser y configúralo de la siguiente manera:

* En el campo **Observed Components** (Componentes observados), asigna el componente Generic Net Sync (Script) (Sincronización neta genérica [script]).

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Creación del avatar

En la ventana Jerarquía, haz clic con el botón derecho en el objeto **PhotonUser**, selecciona **Objeto 3D** > **Esfera** para crear un objeto con forma de esfera como elemento secundario del objeto PhotonUser, y configúralo de la manera siguiente:

* Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0.
* Cambia el valor **Escala** de Transformación a un tamaño adecuado; por ejemplo, X = 0,15, Y = 0,15 y Z = 0,15.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Creación del elemento prefabricado

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

Con la carpeta Recursos todavía seleccionada, **haz clic y arrastra** el objeto **PhotonUser** desde la ventana Jerarquía a la carpeta **Recursos** para convertir el objeto PhotonUser en un elemento prefabricado:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

En la ventana Jerarquía, haz clic con el botón derecho en el objeto **PhotonUser** y selecciona **Eliminar** para quitarlo de la escena:

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Configuración de PUN para crear una instancia del elemento prefabricado del usuario

En esta sección, configurarás el proyecto para usar el elemento prefabricado PhotonUser que creaste en la sección anterior.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Photon User Prefab** (Elemento prefabricado de usuario de Photon), asigna el elemento **PhotonUser** de la carpeta Recursos.

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Prueba de la experiencia con varios usuarios

Si ahora compilas e implementas el proyecto de Unity en tu dispositivo HoloLens y, después, vuelves a Unity, presiona el botón Reproducir para entrar en el Modo Juego. Mientras la aplicación se ejecuta en HoloLens, verás que el avatar de usuario de HoloLens se mueve cuando mueves la cabeza (HoloLens):

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puedes consultar las instrucciones de [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).

> [!CAUTION]
> La aplicación necesita conectarse a Photon, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.

## <a name="congratulations"></a>Enhorabuena

Has configurado correctamente el proyecto para permitir que varios usuarios se conecten a la misma experiencia y vean los movimientos de los demás. En el siguiente tutorial, implementarás la funcionalidad para que los movimientos de objetos también se compartan entre varios dispositivos.

[Tutorial siguiente: 2. Uso compartido de movimientos de objetos con varios usuarios](mrlearning-sharing(photon)-ch3.md)
