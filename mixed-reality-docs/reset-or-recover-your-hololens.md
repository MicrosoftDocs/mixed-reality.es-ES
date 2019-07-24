---
title: Restablecimiento o recuperación de HoloLens
description: Instrucciones básicas y avanzadas para reiniciar o restablecer la HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: procedimientos, reinicio, restablecimiento, recuperación, restablecimiento de hardware, restablecimiento parcial, ciclo de energía, HoloLens, apagado
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524036"
---
# <a name="reset-or-recover-your-hololens"></a>Restablecimiento o recuperación de HoloLens

Si tiene problemas con su HoloLens, es posible que quiera intentar reiniciar, restablecer o incluso volver a Flash con recuperación del dispositivo. Este documento le guiará a través de los pasos recomendados en sucesión.

## <a name="perform-a-device-reboot"></a>Realización de un reinicio del dispositivo

Si HoloLens está experimentando problemas o no responde, primero intente reiniciarlo a través de uno de los métodos siguientes.

### <a name="perform-a-safe-reboot-via-cortana"></a>Realización de un reinicio seguro a través de Cortana

La forma más segura de reiniciar HoloLens es a través de Cortana. Suele ser un excelente primer paso cuando se produce un problema con HoloLens:
1. Colocar en el dispositivo
2. Asegúrese de que está encendido, de que un usuario ha iniciado sesión y de que el dispositivo no está esperando una contraseña para desbloquearlo.
3. Supalabras "Hola Cortana, reinicio" o "Hola Cortana, reinicio".
4. Cuando confirma que le pide confirmación. Espere un segundo para que se reproduzca un sonido después de que haya finalizado su pregunta, lo que indica que está escuchando a usted y, a continuación, diga "sí".
5. El dispositivo se reiniciará y reiniciará ahora.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Realización de un reinicio seguro a través del portal de dispositivos de Windows

Si lo anterior no funciona, puede intentar reiniciar el dispositivo a través del [portal de dispositivos de Windows](using-the-windows-device-portal.md). En la esquina superior derecha, hay una opción para reiniciar o apagar el dispositivo.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Realización de un reinicio seguro a través del botón de encendido

Si sigue sin poder reiniciar el dispositivo, puede intentar realizar un reinicio mediante el botón de encendido:
1. Mantenga presionado el botón de encendido durante 5 segundos
   1. Después de un segundo, verá que se iluminan los 5 LED y, después, se desactivan lentamente de derecha a izquierda.
   2. Después de 5 segundos, todos los LED estarán desactivados, lo que indica que el comando SHUTDOWN se emitió correctamente
   3. Tenga en cuenta que es importante dejar de presionar el botón inmediatamente después de que todos los LED se hayan desactivado
2. Espere un minuto para que el cierre sea correcto. Tenga en cuenta que el cierre todavía puede estar en curso incluso si las pantallas están desactivadas
3. Volver a encender el dispositivo presionando y manteniendo presionado el botón de encendido durante un segundo

### <a name="perform-an-unsafe-forced-reboot"></a>Realizar un reinicio forzado no seguro

Si ninguno de los métodos anteriores es capaz de reiniciar el dispositivo correctamente, puede forzar un reinicio. Tenga en cuenta que este método es equivalente a extraer la batería de HoloLens y, como tal, es una operación peligrosa que puede dejar el dispositivo en un estado dañado. 

>[!WARNING]
>Se trata de un método potencialmente perjudicial y solo debe usarse en el caso de que no funcione ninguno de los métodos anteriores.

1. Mantenga presionado el botón de encendido durante 10 segundos como mínimo
   * Es correcto mantener el botón durante más de 10 segundos
   * Es seguro ignorar cualquier actividad LED
2. Suelte el botón y espere 2-3 segundos
3. Volver a encender el dispositivo presionando y manteniendo presionado el botón de encendido durante un segundo

## <a name="reset-the-device-to-a-factory-clean-state"></a>Restablecer el dispositivo a un estado limpio de fábrica

Si HoloLens sigue experimentando problemas después del reinicio, puede intentar restablecerlo a un estado limpio de fábrica. Si restablece el dispositivo, se borrarán todos los datos personales, las aplicaciones y la configuración. Al restablecer solo se instalará la última versión instalada de Windows Holographic y tendrá que rehacer todos los pasos de inicialización (calibrar, conectarse a WiFi, crear una cuenta de usuario, descargar aplicaciones, etc.).
1. Iniciar la **configuración** de App-> **Update** -> **RESET**
2. Seleccione la opción **restablecer dispositivo** y lea el cuadro de diálogo de confirmación.
3. Si acepta restablecer el dispositivo, el dispositivo se reiniciará y mostrará un conjunto de engranajes de giro con una barra de progreso.
4. Espere unos 30 minutos hasta que se complete este proceso
5. El restablecimiento se completará y el dispositivo se reiniciará en la experiencia rápida.

## <a name="perform-a-full-device-recovery"></a>Realizar una recuperación completa del dispositivo

Si después de realizar las opciones anteriores, el dispositivo **todavía** está inmovilizado, no responde o experimenta problemas de actualización o software, puede recuperarlo mediante la herramienta de recuperación de dispositivos de Windows. La recuperación del dispositivo es similar a restablecerlo en el sentido de que borrará todo el contenido del usuario en el dispositivo, incluidas las aplicaciones, juegos, fotos, cuentas de usuario y mucho más. Si es posible, realice una copia de seguridad de toda la información que desee conservar.

Para recuperar completamente su HoloLens:
1. Desconectar todos los teléfonos y dispositivos Windows del equipo
2. Instalación e inicio de la [herramienta de recuperación de dispositivos de Windows](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) en el equipo
3. Conecte su HoloLens a su equipo con el cable micro USB que incluye
   * Tenga en cuenta que no todos los cables USB se crean igual. Incluso si ha estado usando otro cable correctamente, este flujo expondrá nuevos Estados en los que el cable podría no funcionar también. Lo que incluye HoloLens es la opción mejor y más bien probada
4. Si la herramienta detecta automáticamente el dispositivo, mostrará un icono de HoloLens. Haga clic en él y siga las instrucciones para completar el proceso.

>[!NOTE]
>WDRT puede recuperar el dispositivo a una versión anterior de Windows Holographic; es posible que tenga que instalar las actualizaciones después de la intermitencia

Si la herramienta no puede detectar el dispositivo automáticamente, intente lo siguiente:
1. Reinicie el equipo y vuelva a intentarlo (Esto corrige la mayoría de los problemas)
2. Haga clic en el **botón mi dispositivo no se detectó**, elija **Microsoft HoloLens**y siga el resto de las instrucciones de la pantalla.
