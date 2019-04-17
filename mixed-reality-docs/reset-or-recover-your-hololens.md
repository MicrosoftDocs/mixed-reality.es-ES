---
title: Restablecer o recuperar su HoloLens
description: Instrucciones básicas y avanzadas para reiniciar o restablecer su HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: tema de procedimientos, reiniciar, restablecer, recuperar, reinicio, restablecimiento parcial, ciclo de energía, HoloLens, apagar
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599878"
---
# <a name="reset-or-recover-your-hololens"></a>Restablecer o recuperar su HoloLens

Si experimenta problemas con su HoloLens desea intentar un reinicio, restablecimiento, o incluso volver a flash con la recuperación del dispositivo. Este documento le guiará por los pasos recomendados en sucesión.

## <a name="perform-a-device-reboot"></a>Realizar un reinicio del dispositivo

Si su HoloLens está experimentando problemas o no responde, primero intente reiniciar el sistema a través de uno de los siguientes métodos.

### <a name="perform-a-safe-reboot-via-cortana"></a>Llevar a cabo un reinicio seguro a través de Cortana

La forma más segura para reiniciar el HoloLens es a través de Cortana. Por lo general es un primer paso excelente cuando experimenta un problema con HoloLens:
1. Colocar en el dispositivo
2. Asegúrese de que está encendido, un usuario ha iniciado sesión y el dispositivo no está esperando una contraseña desbloquearlo.
3. Por ejemplo "Hola Cortana, reinicie" o "Hola Cortana, reinicie."
4. Cuando confirma pedirá confirmación. Espere a un segundo para un sonido que se reproducirá después de que haya terminado su pregunta, que indica que está escuchando y, a continuación, diga "Sí".
5. El dispositivo se ahora reinicio o reiniciar.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Llevar a cabo un reinicio seguro a través de Windows Device Portal

Si lo anterior no funciona, puede intentar reiniciar el dispositivo a través de [Windows Device Portal](using-the-windows-device-portal.md). En la esquina superior derecha, hay una opción para reiniciar o apagar el dispositivo.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>Llevar a cabo un reinicio seguro mediante el botón de encendido

Si todavía no se puede reiniciar el dispositivo, puede intentar emitir un reinicio mediante el botón de encendido:
1. Presione y mantenga presionado el botón de encendido durante 5 segundos
   1. Después de 1 segundo, verá todas iluminan LED 5, a continuación, lentamente desactivar de derecha a izquierda
   2. Después de 5 segundos, todos los LED estará desactivada, que indica que el comando shutdown se emitió correctamente
   3. Tenga en cuenta es importante detener al presionar el botón inmediatamente después de que todos los LED han desactivado
2. Espere 1 minuto para el apagado correctamente se realice correctamente. Tenga en cuenta que el cierre puede ser aún en curso incluso si está desactivadas de la muestra
3. Encienda el dispositivo nuevo por presionando y manteniendo presionado el botón de encendido durante 1 segundo

### <a name="perform-an-unsafe-forced-reboot"></a>Llevar a cabo un reinicio forzado no seguro

Si ninguno de los métodos anteriores se pueden reiniciar correctamente el dispositivo, puede forzar un reinicio. Tenga en cuenta que este método es equivalente a extraer la batería de la HoloLens y, por lo tanto, es una operación peligrosa que puede dejar el dispositivo en un estado dañado. 

>[!WARNING]
>Esto es un método potencialmente perjudicial y solo debe usarse en caso de que ninguno de los métodos anteriores funciona.

1. Presione y mantenga presionado el botón de encendido durante al menos 10 segundos
   * Está bien mantenga presionado el botón durante más de 10 segundos
   * Es seguro pasar por alto cualquier actividad de LED
2. Suelte el botón y espere 2 y 3 segundos
3. Encienda el dispositivo nuevo por presionando y manteniendo presionado el botón de encendido durante 1 segundo

## <a name="reset-the-device-to-a-factory-clean-state"></a>Restablecer el dispositivo a un estado limpio de fábrica

Si su HoloLens todavía está experimentando problemas después de reiniciar, puede intentar restablecer a un estado limpio de fábrica. Si se restablece un dispositivo, se borrarán todos sus datos personales, aplicaciones y configuraciones. Restablecer solo se instalará la versión instalada más reciente de Windows Holographic y tendrá que repetir todos los pasos de inicialización (calibrar, conectarse a Wi-Fi, cree una cuenta de usuario, descargue las aplicaciones, etcetera...).
1. Iniciar el **configuración** -> aplicación **actualización** -> **restablecer**
2. Seleccione el **Restablecer dispositivo** opción y el cuadro de diálogo de confirmación de lectura
3. Si está de acuerdo restablecer el dispositivo, el dispositivo se reinicie y mostrar un conjunto de engranajes con una barra de progreso de giro
4. Espere unos 30 minutos para que se complete este proceso
5. El restablecimiento se completará y se reiniciará el dispositivo en el fuera de la experiencia estándar

## <a name="perform-a-full-device-recovery"></a>Realizar una recuperación de todos los dispositivos

Si, después de realizar las opciones anteriores, el dispositivo está **todavía** inmovilizadas, no responde, o está experimentando problemas de actualización o software puede recuperarla con el de Windows Device Recovery Tool. Recupera el dispositivo es similar a restablecerla en el sentido de que borrará todo el contenido de usuario en el dispositivo, incluidas aplicaciones, juegos, fotos, cuentas de usuario y mucho más. Si es posible, copia de seguridad de toda la información que desee conservar.

Para recuperar totalmente su HoloLens:
1. Desconecte todos los teléfonos y dispositivos de Windows de su PC
2. Instale e inicie la [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) en su PC
3. Conectar su HoloLens a su equipo mediante el cable micro USB que lo acompaña
   * Tenga en cuenta que no todos los cables USB son iguales. Incluso si ya se ha usado el otro cable correctamente, este flujo expondrá nuevos Estados donde el cable no puede realizar también. El acompañan su HoloLens es la opción mejor y más bien probada
4. Si la herramienta detecta automáticamente el dispositivo se mostrará un icono de HoloLens. Haga clic en ella y siga las instrucciones para completar el proceso

>[!NOTE]
>WDRT puede recuperar el dispositivo a una versión anterior de Windows Holographic; deberá instalar las actualizaciones tras el parpadeo

Si la herramienta no puede detectar automáticamente el dispositivo, intente lo siguiente:
1. Reinicie su equipo y vuelva a intentarlo (Esto soluciona la mayoría de los problemas)
2. Haga clic en el **no detectó mi dispositivo botón**, elija **Microsoft HoloLens**y siga el resto de las instrucciones que aparecen en la pantalla
