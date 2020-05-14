---
title: 6. Empaquetado e implementación en el dispositivo o emulador
description: Parte 6 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840384"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Empaquetado e implementación en el dispositivo o emulador

En esta sección se te orientará a lo largo de los pasos necesarios para preparar la aplicación para que se ejecute en un emulador o dispositivo de HoloLens 2. Si tienes un dispositivo, puedes transmitir en secuencias desde el equipo al dispositivo o empaquetar la aplicación para ejecutarla directamente en el dispositivo. Si no tienes ningún dispositivo, tendrás que empaquetar la aplicación para que se ejecute en el emulador. 

## <a name="objectives"></a>Objetivos

* [Solo dispositivo] Transmitir en secuencias la aplicación a HoloLens 2 mediante la comunicación remota con la aplicación holográfica
* Empaquetar e implementar la aplicación en un dispositivo o emulador de HoloLens 2

## <a name="device-only-stream"></a>[Solo dispositivo] Transmitir en secuencias

1.  Instala **Holographic Remoting Player** desde Microsoft Store en HoloLens 2 y ejecuta la aplicación.

2.  Ve a **Edit > Project Settings** (Editar > Configuración del proyecto). En la sección Holographic Remoting, activa la casilla para habilitar la comunicación remota y reinicia el editor.

3.  Escribe la dirección IP del dispositivo y haz clic en Connect (Conectar).

4.  Una vez conectado, en el editor de UE4, haz clic en la flecha desplegable situada a la derecha del botón Play (Jugar) y selecciona VR Preview (Vista previa de VR).

## <a name="package-and-deploy-your-app"></a>Empaquetar e implementar la aplicación 

1.  Ve a **Edit > Project Settings** (Editar > Configuración del proyecto). En **Project > Description > About > Project Name** (Proyecto > Descripción > Acerca de > Nombre del proyecto), asigna un nombre al proyecto. En **Project > Description > Publisher > Company Distinguished Name** (Proyecto > Descripción > Editor > Empresa > Nombre distintivo), escribe “CN={NOMBRE DE EMPRESA}”. Si dejas alguno de estos campos en blanco, se producirá un error. 

![Configuración del proyecto: descripción](images/unreal-uxt/6-cn.PNG)

2.  En **Platforms > HoloLens** (Plataformas > HoloLens), elige Emulation (Emulación) o Device (Dispositivo), en función del destino al que quieras orientarte.

3.  En la sección **Packaging** (Empaquetado), haz clic junto a **Signing Certificate** (Certificado de firma), haz clic en el botón **Generate new** (Generar nuevo) para generar un nuevo certificado de firma. Vuelve a la ventana principal.

![Configuración del proyecto - Plataformas - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  Ve a **File > Package Project** (Archivo > Proyecto de paquete) y selecciona **HoloLens**. Crea una nueva carpeta en la que guardar el paquete y haz clic en **Select Folder** (Seleccionar carpeta). 

5.  Una vez empaquetada la aplicación, abre el **Portal de dispositivos de Windows**, ve a **Vistas > Aplicaciones** y busca la sección **Implementar aplicaciones**.

6.  Haz clic en **Examinar...** y desplázate hasta el archivo **ChessApp.appxbundle**. Haga clic en **Abrir**. 

    * Si es la primera vez que instalas la aplicación en el dispositivo, activa la casilla situada junto a **Allow me to select framework packages** (Permitirme seleccionar paquetes de marcos). En el siguiente cuadro de diálogo, incluye el archivo appx VCLibs adecuado (arm64 para el dispositivo, x64 para el emulador). 

7.  Haz clic en **Instalar**

Enhorabuena por haber finalizado este tutorial.  