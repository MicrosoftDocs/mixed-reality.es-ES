---
title: Obtenga aplicaciones para HoloLens
description: Describe la instalación de aplicaciones para HoloLens, tanto a través de la Microsoft Store y la instalación de prueba.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: transferir localmente, carga del lado, instalaciones de prueba, almacén, uwp, aplicación, instalar
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597557"
---
# <a name="get-apps-for-hololens"></a>Obtenga aplicaciones para HoloLens

Como un dispositivo Windows 10, HoloLens, es compatible con muchas aplicaciones de UWP existentes desde la tienda de aplicaciones, así como nuevas aplicaciones creadas específicamente para HoloLens. En la parte superior, incluso podría [desarrollar](development-overview.md) e instalar sus propias aplicaciones o aquellas de sus amigos!

## <a name="installing-apps"></a>Instalación de aplicaciones

Hay tres formas de instalar nuevas aplicaciones en su HoloLens. Será el método principal instalar nuevas aplicaciones desde el Store de Windows. Sin embargo, también puede instalar en sus propias aplicaciones mediante Device Portal o mediante su implementación desde Visual Studio.

### <a name="from-the-microsoft-store"></a>Desde la Microsoft Store
1. Realizar una [bloom](gestures.md#bloom) gesto para abrir el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione la aplicación Store y, a continuación, puntee para colocar este icono en el mundo.
3. Cuando se abra la aplicación Store, use la barra de búsqueda para buscar cualquier aplicación que desee.
4. Seleccione **obtener** o **instalar** en la página de aplicación (una compra puede ser necesaria).

### <a name="installing-an-application-package-with-the-device-portal"></a>Instalar un paquete de aplicación con el Portal de dispositivo
1. Establecer una conexión desde [Device Portal](using-the-windows-device-portal.md) al destino HoloLens.
2. Navegue hasta la **aplicaciones** página en el panel de navegación izquierdo.
3. En **paquete de aplicación** busque el archivo .appx relacionado con la aplicación.
  >[!IMPORTANT]
  >Asegúrese de hacer referencia a los archivos asociados de dependencia y el certificado.

4. Haga clic en **vaya**.

![Instalar el formulario de aplicación de Windows Device Portal en Microsoft HoloLens](images/deviceportal-appmanager.jpg)<br>
Uso de Windows Device Portal para instalar una aplicación en HoloLens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Implementar desde Microsoft Visual Studio 2015
1. Abra la solución de Visual Studio de la aplicación (archivo .sln).
2. Abra el proyecto **propiedades** .
3. Seleccione la configuración de compilación siguiente: Equipo maestro o x86/remoto.
4. Al seleccionar un equipo remoto:
   * Asegúrese de que la dirección señala a la dirección de IP WiFi de HoloLens.
   * Establecer la autenticación Universal (protocolo sin cifrar).
5. Compile la solución.
6. Haga clic en el **máquina remota** botón para implementar la aplicación desde el equipo de desarrollo en su HoloLens. Si ya tiene una compilación existente en el HoloLens, seleccione Sí para volver a instalar esta versión más reciente.<br>
  ![Implementación de la máquina remota para las aplicaciones de Microsoft HoloLens en Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. Instalará la aplicación y auto lanzamiento en su HoloLens.
