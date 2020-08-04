---
title: 'Tutoriales sobre las funcionalidades multiusuario: 3. Conexión de varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376397"
---
# <a name="3-connecting-multiple-users"></a>3. Conexión de varios usuarios

En este tutorial, aprenderás a conectar varios usuarios como parte de una experiencia compartida en directo. Al final del tutorial, podrá ejecutar la aplicación en varios dispositivos y hacer que todos los usuarios vean cómo se mueve el avatar de los demás en tiempo real.

## <a name="objectives"></a>Objetivos

* Aprender a conectar varios usuarios en una experiencia compartida

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK.Tutorials.MultiUserCapabilities** > carpeta **Prefabs** (Recursos prefabricados) y, a continuación, haga clic y arrastre el siguiente objeto prefabricado a la ventana Jerarquía para agregarlos a la escena:

* Objeto prefabricado **NetworkLobby**
* Objeto prefabricado **SharedPlayground**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

En la ventana Proyecto, desplácese hasta **Assets** (Recursos)  > **MRTK.Tutorials.AzureSpatialAnchors** > carpeta **Prefabs** (Recursos prefabricados) y haga clic y arrastre el siguiente objeto prefabricado a la ventana Jerarquía para agregarlo a la escena:

* Objeto prefabricado **DebugWindow**

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Creación del elemento prefabricado del usuario

En esta sección, crearás un elemento prefabricado que se usará para representar a los usuarios en la experiencia compartida.

### <a name="1-create-and-configure-the-user"></a>1. Creación y configuración del usuario

En la ventana Jerarquía, haz clic con el botón derecho en un área vacía y selecciona **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena. Asigna al objeto el nombre **PhotonUser** y configúralo de la siguiente manera:

* Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

En la ventana Jerarquía, seleccione el objeto **PhotonUser**; después, en la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon User (Script)** (Usuario de Photon [script]) al objeto PhotonUser:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Generic Net Sync (Script)** (Sincronización neta genérica [script]) al objeto PhotonUser y configúralo de la siguiente manera:

* Selecciona la casilla **Is User** (Es el usuario).

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon View (Script)** (Vista de Photon [script]) al objeto PhotonUser y configúralo de la siguiente manera:

* En el campo **Observed Components** (Componentes observados), asigne el componente **Generic Net Sync (Script)** (Sincronización neta genérica [script]).

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Creación del avatar

En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK** > **SDK** > **StandardAssets** > carpeta **Materials** (Materiales) para buscar los materiales de MRTK.

Después, en la ventana Jerarquía, haga clic con el botón derecho en el objeto **PhotonUser** y seleccione **Objeto 3D** > **Esfera** para crear un objeto con forma de esfera como elemento secundario del objeto PhotonUser, y configúrelo de la manera siguiente:

* Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0.
* Cambia el valor **Escala** de Transformación a un tamaño adecuado; por ejemplo, X = 0,15, Y = 0,15 y Z = 0,15.
* En el campo MeshRenderer > Materials (Materiales) > **Elemento 0**, asigne el material **MRTK_Standard_White**.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Creación del elemento prefabricado

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

Con la carpeta Recursos todavía seleccionada, **haz clic y arrastra** el objeto **PhotonUser** desde la ventana Jerarquía a la carpeta **Recursos** para convertir el objeto PhotonUser en un elemento prefabricado:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

En la ventana Jerarquía, haz clic con el botón derecho en el objeto **PhotonUser** y selecciona **Eliminar** para quitarlo de la escena:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Configuración de PUN para crear una instancia del elemento prefabricado del usuario

En esta sección, configurarás el proyecto para usar el elemento prefabricado PhotonUser que creaste en la sección anterior.

En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:

* En el campo **Photon User Prefab** (Elemento prefabricado de usuario de Photon), asigna el elemento **PhotonUser** de la carpeta Recursos.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Prueba de la experiencia con varios usuarios

Si ahora compila e implementa el proyecto de Unity en su dispositivo HoloLens, vuelva a Unity y entre en el Modo Juego. Mientras la aplicación se ejecuta en HoloLens, verá que el avatar de usuario de HoloLens se mueve cuando mueve la cabeza (HoloLens):

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> La aplicación necesita conectarse a Photon, por lo que debe asegurarse de que el equipo o dispositivo esté conectado a Internet.

## <a name="congratulations"></a>Enhorabuena

Has configurado correctamente el proyecto para permitir que varios usuarios se conecten a la misma experiencia y vean los movimientos de los demás. En el siguiente tutorial, implementarás la funcionalidad para que los movimientos de objetos también se compartan entre varios dispositivos.

[Tutorial siguiente: 4. Uso compartido de movimientos de objetos con varios usuarios](mr-learning-sharing-04.md)
