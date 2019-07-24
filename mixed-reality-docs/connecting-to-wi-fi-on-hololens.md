---
title: Conexión a Wi-Fi en HoloLens
description: Instrucciones sobre cómo conectarse a Internet inalámbrica con HoloLens y cómo identificar la dirección IP del dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, Wi-Fi, inalámbrica, Internet, IP, dirección IP
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670111"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>Conexión a Wi-Fi en HoloLens

HoloLens contiene una radio Wi-Fi compatible con AC 802.11 y 2x2. Conectar HoloLens a una red Wi-Fi es similar a conectar un dispositivo móvil o de escritorio de Windows 10 a una red Wi-Fi.

![Configuración de Wi-Fi de HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>Conexión a una red Wi-Fi en HoloLens

1. [Floración](gestures.md#bloom) al menú **Inicio** .
2. Seleccione la aplicación de **configuración** en Inicio o en la lista **todas las aplicaciones** a la derecha del menú Inicio.
3. La aplicación de **configuración** se colocará automáticamente delante de usted.
4. Seleccione **red & Internet**.
5. Asegúrate de que la conexión Wi-Fi está activada.
6. Seleccione una red Wi-Fi en la lista.
7. Escriba la contraseña de red Wi-Fi (si es necesario).

## <a name="disabling-wi-fi-on-hololens"></a>Deshabilitación de Wi-Fi en HoloLens

### <a name="using-the-settings-app-on-hololens"></a>Uso de la aplicación de configuración en HoloLens

1. [Floración](gestures.md#bloom) al menú **Inicio** .
2. Seleccione la aplicación de **configuración** en Inicio o en la lista **todas las aplicaciones** a la derecha del menú Inicio.
3. La aplicación de **configuración** se colocará automáticamente delante de usted.
4. Seleccione **red & Internet**.
5. Seleccione el conmutador de control deslizante de Wi-Fi para moverlo a la posición "desactivado". Se desactivarán los componentes de RF del radio Wi-Fi y se deshabilitará toda la funcionalidad de Wi-Fi en HoloLens. 

    >[!WARNING]
    >HoloLens no podrá cargar automáticamente los [espacios](environment-considerations-for-hololens.md#WiFi fingerprint considerations) cuando la radio Wi-Fi esté deshabilitada.
    
6. Mueva el control deslizante a la posición "activado" para activar la radio Wi-Fi y restaurar la funcionalidad de Wi-Fi en Microsoft HoloLens. El estado de radio Wi-Fi seleccionado ("activado" de "desactivado") se conservará en los reinicios.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Cómo confirmar que está conectado a una red Wi-Fi

1. [Floración](gestures.md#bloom) para abrir el menú **Inicio** .
2. Fíjese en la parte superior izquierda del menú Inicio para ver el estado de Wi-Fi. Se mostrará el estado de Wi-Fi y el SSID de la red conectada.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Identificación de la dirección IP de HoloLens en la red Wi-Fi

### <a name="using-the-settings-app"></a>Uso de la aplicación de configuración

1. [Floración](gestures.md#bloom) al menú **Inicio** .
2. Seleccione la aplicación de **configuración** en Inicio o en la lista **todas las aplicaciones** a la derecha del menú Inicio.
3. La aplicación de **configuración** se colocará automáticamente delante de usted.
4. Seleccione **red & Internet**.
5. Desplácese hacia abajo hasta la lista de redes Wi-Fi disponibles y seleccione **propiedades de hardware**.

    ![Propiedades de hardware en configuración de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

La dirección IP se mostrará junto a **dirección IPv4**.

### <a name="using-cortana"></a>Uso de Cortana

Supongamos*que "Hola Cortana, ¿cuál es mi dirección IP?* " y Cortana mostrará y leerá su dirección IP.

### <a name="using-windows-device-portal"></a>Uso del portal de dispositivos de Windows

1. Abra el [portal de dispositivos](using-the-windows-device-portal.md#networking) en un explorador Web en su PC.
2. Vaya a la sección **redes** .

La dirección IP y otra información de red se mostrarán allí. Este método permite copiar y pegar fácilmente la dirección IP en el equipo de desarrollo.
