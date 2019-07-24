---
title: Obtener aplicaciones para HoloLens
description: Describe la instalación de aplicaciones para HoloLens, tanto mediante el Microsoft Store como la carga de prueba.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: instalación de prueba, carga lateral, carga lateral, almacén, UWP, aplicación, instalar
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522563"
---
# <a name="get-apps-for-hololens"></a>Obtener aplicaciones para HoloLens

Como dispositivo Windows 10, HoloLens es compatible con muchas aplicaciones UWP existentes desde la tienda de aplicaciones, así como con nuevas aplicaciones compiladas específicamente para HoloLens. Además, es posible que incluso desee [desarrollar](development-overview.md) e instalar sus propias aplicaciones o sus amigos.

## <a name="installing-apps"></a>Instalación de aplicaciones

Hay tres maneras de instalar aplicaciones nuevas en HoloLens. El método principal será instalar nuevas aplicaciones desde la tienda Windows. Sin embargo, también puede instalar sus propias aplicaciones con el portal de dispositivos o mediante su implementación desde Visual Studio.

### <a name="from-the-microsoft-store"></a>Desde el Microsoft Store
1. Realice un gesto de [floración](gestures.md#bloom) para abrir el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione la aplicación de la tienda y, después, pulse para colocar este icono en su mundo.
3. Una vez que se abra la aplicación de la tienda, use la barra de búsqueda para buscar cualquier aplicación deseada.
4. Seleccione **obtener** o **instalar** en la página de la aplicación (es posible que se requiera una compra).

### <a name="installing-an-application-package-with-the-device-portal"></a>Instalación de un paquete de aplicación con el portal de dispositivos
1. Establezca una conexión desde el [portal de dispositivos](using-the-windows-device-portal.md) a la HoloLens de destino.
2. Vaya a la página **aplicaciones** en el panel de navegación izquierdo.
3. En **paquete** de la aplicación, busque el archivo. appx asociado a la aplicación.
  >[!IMPORTANT]
  >Asegúrese de hacer referencia a los archivos de certificado y de dependencia asociados.

4. Haga clic en **ir**.

![Instalación del formulario de aplicación en Windows Device portal en Microsoft HoloLens](images/deviceportal-appmanager.jpg)<br>
Uso del portal de dispositivos de Windows para instalar una aplicación en HoloLens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Implementación desde Microsoft Visual Studio 2015
1. Abra la solución de Visual Studio de la aplicación (archivo. sln).
2. Abra las **propiedades** del proyecto.
3. Seleccione la siguiente configuración de compilación: Máquina maestra/x86/equipo remoto.
4. Al seleccionar equipo remoto:
   * Asegúrese de que la dirección señala a la dirección IP de Wi-Fi de HoloLens.
   * Establezca la autenticación en universal (protocolo sin cifrar).
5. Compile la solución.
6. Haga clic en el botón **equipo remoto** para implementar la aplicación desde el equipo de desarrollo en su HoloLens. Si ya tiene una compilación existente en HoloLens, seleccione Sí para volver a instalar esta versión más reciente.<br>
  ![Implementación de equipos remotos para aplicaciones en Microsoft HoloLens en Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. La aplicación se instalará y se iniciará automáticamente en HoloLens.
