---
title: 6. Empaquetado e implementación en el dispositivo o emulador
description: Parte 6 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: c49e2a69cb97a996da4bf601a105c2176ccf267f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303546"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Empaquetado e implementación en el dispositivo o emulador

## <a name="overview"></a>Introducción

En el tutorial anterior, agregó un botón sencillo que restablece la pieza de ajedrez a su posición original. En esta última sección, preparará la aplicación para que se ejecute en HoloLens 2 o en un emulador. Si tiene HoloLens 2, puede transmitir en secuencias desde el equipo o el paquete la aplicación para ejecutarla directamente en el dispositivo. Si no tiene un dispositivo, deberá empaquetar la aplicación para que se ejecute en el emulador. Al final de esta sección, tendrá una aplicación de realidad mixta implementada que se puede reproducir, terminada con interacciones e interfaz de usuario.

## <a name="objectives"></a>Objetivos

* [Solo dispositivo] Transmisión en secuencias a HoloLens 2 con el control remoto de holografías de la aplicación
* Empaquetado e implementación de la aplicación en un dispositivo o emulador de HoloLens 2

## <a name="device-only-streaming"></a>[Solo dispositivo] Transmisión en secuencias
En este caso, el [control remoto de holografías](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) significa la transmisión en secuencias de datos desde un equipo o dispositivo UWP independiente a HoloLens 2, sin cambiar el canal. La manera en que funciona es que una aplicación host de control remoto recibe una transmisión en secuencias de datos de entrada de HoloLens, representa el contenido en una vista envolvente virtual y vuelve a transmitir en secuencia los fotogramas de contenido a HoloLens a través de Wi-Fi. La transmisión en secuencias permite agregar vistas envolventes remotas al software del equipo de escritorio existente y tener acceso a más recursos del sistema. 

Si va a realizar esta ruta con la aplicación de ajedrez, necesitará algunos elementos:

1.  Instale **Holographic Remoting Player** desde Microsoft Store en HoloLens 2 y ejecute la aplicación. Anote la dirección IP que se muestra en la aplicación.

2.  Cuando vuelva a estar en el editor de Unreal, vaya a **Edit > Project Settings** (Editar > Configuración del proyecto) y marque la opción **Habilitar la comunicación remota** en la sección **Holographic Remoting** (Comunicación remota de holografías).

3.  Reinicie el editor y, a continuación, escriba la dirección IP del dispositivo (como se muestra en la aplicación Holographic Remoting Player) y haga clic en **Conectar**.

Una vez conectado, haga clic en la flecha desplegable situada a la derecha del botón **Play** (Jugar) y seleccione **VR Preview** (Vista previa de VR). La aplicación se ejecutará en la ventana VR Preview (Vista previa de VR), de la que se hace streaming al casco de HoloLens. 

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>Empaquetado e implementación de la aplicación mediante el Portal de dispositivos

>[!NOTE]
>Si esta es la primera vez que empaquetas una aplicación de Unreal para HoloLens, deberás descargar los archivos auxiliares desde el iniciador de Epic. 
>- Vaya a la pestaña **Biblioteca** en Selector de juegos Epic, seleccione la flecha desplegable situada junto a **Lanzar** > y haga clic en **Opciones**. 
>- En **Target Platforms** (Plataformas de destino), selecciona **HoloLens 2** y haz clic en **Aplicar**. 
>![Configuración del proyecto: Descripción](images/unreal-uxt/6-installationoptions.PNG)

1.  Ve a **Edit > Project Settings** (Editar > Configuración del proyecto). 
    * Añada un nombre de proyecto en **Project > Description > About > Project Name** (Proyecto > Descripción > Acerca de > Nombre del proyecto). 
    * Añada **CN=NombreDeLaEmpresa** en **Project > Description > Publisher > Company Distinguished Name** (Proyecto > Descripción > Editor > Nombre distintivo de la empresa).

> [!IMPORTANT]
> Si deja alguno de estos campos en blanco, se producirá un error al intentar generar un nuevo certificado en el paso 3. 

> [!IMPORTANT]
> El nombre del editor debe tener el [formato de nombres distintivos de LADPv3](https://www.ietf.org/rfc/rfc2253.txt). Un nombre de editor con un formato incorrecto dará lugar al error "Signing key not found. The app could not be digitally signed." (Clave de firma no encontrada. No se pudo firmar digitalmente la aplicación.) al realizar el empaquetado.

![Configuración del proyecto: descripción](images/unreal-uxt/6-cn.PNG)

2.  Habilite **Build for HoloLens Emulation** (Compilar para emulación de HoloLens) y/o **Build for HoloLens Device** (Compilar para dispositivo HoloLens) en **Platforms > HoloLens** (Plataformas > HoloLens).

3.  Haga clic en **Generate new** (Generar nuevo) en la sección **Packaging** (Empaquetado) [junto a **Signing Certificate** (Certificado de firma)].

> [!IMPORTANT]
> Si utiliza un certificado ya generado, el nombre del editor del certificado debe ser el mismo que el nombre del editor de la aplicación. En caso contrario, se producirá el error "Signing key not found. The app could not be digitally signed." (Clave de firma no encontrada. No se pudo firmar digitalmente la aplicación.) error.

![Configuración del proyecto - Plataformas - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. Haga clic en **None** (Ninguno) con fines de prueba cuando se le pida que cree una contraseña de clave privada.

![Generación de un nuevo certificado](images/unreal-uxt/6-private-key-testing.png)

5. Ve a **File > Package Project** (Archivo > Proyecto de paquete) y selecciona **HoloLens**. 
    * Crea una nueva carpeta en la que guardar el paquete y haz clic en **Select Folder** (Seleccionar carpeta). 

6.  Abra el [Portal de dispositivos Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) después de empaquetar la aplicación, vaya a **Vistas > Aplicaciones** y busque la sección **Implementar aplicación**.

7.  Haga clic en **Examinar...** , vaya al archivo **ChessApp.appxbundle** y haga clic en **Abrir**. 

    * Active la casilla situada junto a **Allow me to select framework packages** (Permitirme seleccionar paquetes de marcos) si es la primera vez que instala la aplicación en el dispositivo. 
    * En el siguiente cuadro de diálogo, incluya los archivos **VCLibs** y **appx** adecuados (arm64 para el dispositivo, x64 para el emulador). Puede encontrarlos en **HoloLens** dentro de la carpeta donde ha guardado el paquete.

8.  Haz clic en **Instalar**
    * Ahora puede ir a **All apps** (Todas las aplicaciones) y pulsar en la aplicación recién instalada para ejecutarla, o puede iniciar la aplicación directamente desde el **Portal de dispositivos Windows**. 

Enhorabuena. La aplicación de realidad mixta de HoloLens está finalizada y lista para utilizarse. Sin embargo, este no es el final del camino. MRTK tiene muchas características independientes que puede agregar a los proyectos, como el mapeo espacial, la entrada de mirada y voz, e incluso los códigos QR. Puede encontrar más información sobre estas características en [Introducción al desarrollo con Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).
