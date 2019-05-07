---
title: Conectarse a Wi-Fi en HoloLens
description: Instrucciones sobre cómo conectarse a internet inalámbrica con HoloLens y cómo identificar la dirección IP del dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, Wi-Fi, conexiones inalámbricas, internet, ip, dirección ip
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670111"
---
# <a name="connecting-to-wi-fi-on-hololens"></a>Conectarse a Wi-Fi en HoloLens

HoloLens contiene un 802. 11ac-capaz, 2 x 2 radio de Wi-Fi. La conexión de HoloLens a una red Wi-Fi es parecido a conectar un dispositivo Windows 10 escritorio o móvil a una red Wi-Fi.

![Configuración de Wi-Fi de HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a>Conectarse a una red Wi-Fi en HoloLens

1. [Bloom](gestures.md#bloom) a la **iniciar** menú.
2. Seleccione el **configuración** aplicación desde el principio o desde el **todas las aplicaciones** lista a la derecha del menú Inicio.
3. El **configuración** aplicación será coloca automáticamente delante de usted.
4. Seleccione **red e Internet**.
5. Asegúrate de que la conexión Wi-Fi está activada.
6. Seleccione una red Wi-Fi de la lista.
7. Escriba la contraseña de la red Wi-Fi (si es necesario).

## <a name="disabling-wi-fi-on-hololens"></a>Deshabilitación de Wi-Fi en HoloLens

### <a name="using-the-settings-app-on-hololens"></a>Uso de la aplicación de configuración en HoloLens

1. [Bloom](gestures.md#bloom) a la **iniciar** menú.
2. Seleccione el **configuración** aplicación desde el principio o desde el **todas las aplicaciones** lista a la derecha del menú Inicio.
3. El **configuración** aplicación será coloca automáticamente delante de usted.
4. Seleccione **red e Internet**.
5. Seleccione el control deslizante Wi-Fi para moverla a la posición "Off". Esto se desactivará los componentes de RF de la radio de Wi-Fi y deshabilitar toda la funcionalidad de Wi-Fi en HoloLens. 

    >[!WARNING]
    >HoloLens no podrá cargar automáticamente su [espacios](environment-considerations-for-hololens.md#WiFi fingerprint considerations) cuando está deshabilitado el radio de Wi-Fi.
    
6. Mueva el control deslizante a la posición "On" para activar el radio de Wi-Fi y restaurar la funcionalidad de Wi-Fi en Microsoft HoloLens. El estado seleccionado de radio de Wi-Fi ("On" de "Off") se conservan entre reinicios.

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a>Cómo confirmar que está conectados a una red Wi-Fi

1. [Bloom](gestures.md#bloom) para que aparezca el **iniciar** menú.
2. En la parte superior izquierda del menú Inicio para el estado de Wi-Fi. Se mostrará el estado de Wi-Fi y el SSID de la red conectada.

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a>Que identifica la dirección IP de su HoloLens en la red Wi-Fi

### <a name="using-the-settings-app"></a>Uso de la aplicación de configuración

1. [Bloom](gestures.md#bloom) a la **iniciar** menú.
2. Seleccione el **configuración** aplicación desde el principio o desde el **todas las aplicaciones** lista a la derecha del menú Inicio.
3. El **configuración** aplicación será coloca automáticamente delante de usted.
4. Seleccione **red e Internet**.
5. Desplácese hacia abajo hasta debajo de la lista de redes Wi-Fi disponibles y seleccione **propiedades de Hardware**.

    ![Propiedades de hardware en las opciones de Wi-Fi](images/wifi-hololens-hwdetails.jpg)

Se mostrará junto a la dirección IP **dirección IPv4**.

### <a name="using-cortana"></a>Uso de Cortana

Por ejemplo "*Hola Cortana, ¿cuál es mi dirección IP?*" y Cortana mostrará y leer la dirección IP.

### <a name="using-windows-device-portal"></a>Uso de Windows Device Portal

1. Abra el [portal dispositivos](using-the-windows-device-portal.md#networking) en un explorador web en su PC.
2. Navegue hasta la **redes** sección.

Allí se mostrará la dirección IP y otra información de red. Este método permite fácil copiar y pegar de la dirección IP en el equipo de desarrollo.
