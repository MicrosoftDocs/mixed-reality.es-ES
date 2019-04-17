---
title: Problemas conocidos de HoloLens
description: Esta es la lista de los problemas conocidos que pueden afectar a los desarrolladores de HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 04/1/2019
ms.topic: article
keywords: solución de problemas, problema conocido, ayuda
ms.openlocfilehash: a92ab52c899de44f9c5c8c86ebb6f9cd8433d395
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605754"
---
# <a name="hololens-known-issues"></a>Problemas conocidos de HoloLens

Esta es la lista actual de los problemas conocidos para desarrolladores que afectan a HoloLens. Busque aquí si observa un comportamiento extraño. Esta lista se mantendrán actualizada como se detectan nuevos problemas o se notifican o como problemas se solucionarán en futuras actualizaciones de software de HoloLens.

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Problemas de inicio de la Microsoft Store y aplicaciones en HoloLens

>[!IMPORTANT]
>Última actualización: 4/2, @ 10 A.M. - problema resuelto. 

Puede experimentar problemas al intentar iniciar la Microsoft Store y aplicaciones en HoloLens. Nos hemos determinado que el problema se produce cuando las actualizaciones de aplicaciones en segundo plano implementan una versión más reciente de los paquetes de framework en secuencias específicas, mientras que uno o varios de sus aplicaciones dependientes siguen en ejecución. En este caso, una actualización de aplicaciones automáticas entregada una nueva versión de .NET Native Framework (versión 10.0.25531 a 10.0.27413) provocó las aplicaciones que se ejecutan incorrectamente una actualización para todas las aplicaciones en ejecución el consumo de la versión anterior de framework.  El flujo de actualización de marco de trabajo es como sigue:-

1.  Se descarga desde la tienda e instala el nuevo paquete de marco de trabajo
2.  Todas las aplicaciones mediante el marco de trabajo anterior se 'actualizan' para usar la versión más reciente

Si se interrumpe el paso 2 antes de completarse, a continuación, las aplicaciones que no se ha registrado el marco de trabajo más reciente se producirá un error iniciar desde el menú Inicio.  Creemos que cualquier aplicación en HoloLens podría verse afectada por este problema.

Algunos usuarios tienen que notifican que cerrar las aplicaciones está bloqueadas e iniciar otras aplicaciones como centro de opiniones, 3D visor o fotos resuelve el problema para ellos, sin embargo, esto no funciona 100% del tiempo.

Tenemos raíz provocó que este problema no se produjo la actualización, pero un error en el sistema operativo que dieron lugar a la actualización de framework .NET Native se controlan correctamente. Nos complace anunciar que se ha identificado una corrección y ha lanzado una actualización (OS versión 17763.380) que contiene la corrección. 

Para ver si el dispositivo puede tardar la actualización:

1.  Vaya a la aplicación de "Configuración" y abra "Actualización y seguridad"
2.  Haga clic en "Buscar actualizaciones"
3.  Si está disponible la actualización 17763.380, actualice a esta compilación para recibir la corrección de errores de bloqueo de aplicación
4.  Tras la actualización a esta versión del sistema operativo, las aplicaciones deben funcionar según lo previsto.

Además, como ocurre con todas las versiones del sistema operativo de HoloLens, hemos publicado la imagen FFU a Microsoft Download Center en https://aka.ms/hololensdownload/10.0.17763.380. 

Si no desea realizar la actualización, hemos publicado una nueva versión de la aplicación para UWP de Microsoft Store a partir de 29/3. Una vez que tenga la versión actualizada de la Store:

1) Abra el Store y confirme que se carga.
2) Usar el gesto de Bloom para abrir el menú.
3) Intento de abrir aplicaciones interrumpidas previamente
3) Si todavía no se puede iniciar, pulse y mantenga pulsado el icono de la aplicación rota y seleccione Desinstalar.
4) Resinstall estas aplicaciones desde la tienda.

Si el dispositivo sigue sin poder cargar aplicaciones, puede transferir localmente una versión de .NET Framework nativo y en tiempo de ejecución a través del centro de descarga de manera práctica:

1)  Descargue [este archivo zip](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) desde Microsoft Download Center.  Al descomprimir generará dos archivos.  Microsoft.NET.Native.Runtime.1.7.appx y Microsoft.NET.Native.Framework.1.7.appx
2)  Compruebe que el dispositivo está desbloqueada de desarrollo.  Si aún no lo ha hecho antes de que las instrucciones para hacer que estén [aquí](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).
3)  A continuación, desea obtener en el Windows Device Portal.  Nuestra recomendación es hacerlo a través de USB y podría hacerlo escribiendo http://127.0.0.1:10080 en el explorador.  
4)  Una vez que tenga el Windows Device Portal seguridad se necesita "carga de lado" los dos archivos que descargó.  Para ello, deberá pasar hacia abajo de la barra lateral izquierda hasta que llegue a la sección "Aplicaciones" y haga clic en "Aplicaciones".
5)  A continuación, verá una pantalla similar a la siguiente.  Desea pasar a la sección que dice "Instalar aplicación" y vaya a donde descomprimió esos dos archivos APPX.  Puede realizar solo una vez, por lo que después de seleccionar la primera de ellas, a continuación, haga clic en "Go" en la sección de implementación.  A continuación, hacer esto para el segundo archivo APPX. 
  ![Windows Device Portal para instalar aplicaciones de transferencia local](images/20190322-DevicePortal.png)<br>
6)  En este momento, consideramos que las aplicaciones deben empezar a trabajar de nuevo y que también se puede abrir el Store.
7)  En algunos casos, es necesario ejecutar el paso adicional de iniciar la aplicación de visor 3D antes de que las aplicaciones afectadas se iniciarán. 

Agradecemos su paciencia tal como hemos realizado a través del proceso para resolver este problema, y Estamos ansiosos continuar trabajando con nuestra comunidad para crear correctamente la realidad mixta experiencias.

## <a name="connecting-to-wifi"></a>Conectarse a Wi-Fi

Durante la bienvenida de Windows y configuración, hay un tiempo de espera de la credencial de 2 minutos. El nombre de usuario y la contraseña debe escribirse dentro de 2 minutos en caso contrario, que se borrará automáticamente el campo de nombre de usuario.

Se recomienda usar un teclado Bluetooth para escribir las contraseñas largas.

## <a name="device-update"></a>Actualización del dispositivo
* 30 segundos después de una nueva actualización, el shell puede desaparecer una vez. Lleve a cabo la **bloom** gesto reanude la sesión.

## <a name="visual-studio"></a>Programa para la mejora
* Consulte [instalar las herramientas de](install-the-tools.md) para la versión más actualizada de Visual Studio que se recomienda para el desarrollo de HoloLens.
* Al implementar una aplicación desde Visual Studio en su HoloLens, verá el error: **No se puede realizar la operación solicitada en un archivo con una sección asignada por el usuario abierta. (Excepción de HRESULT: 0x800704C8)**. Si esto ocurre, vuelva a intentarlo y generalmente se realizará correctamente la implementación.

## <a name="emulator"></a>Emulador
* No todas las aplicaciones en la Microsoft Store son compatibles con el emulador. Por ejemplo, no son puede jugar en el emulador Conker Young y fragmentos.
* No se puede usar la cámara Web de PC en el emulador.
* La característica de vista previa activa de la Windows Device Portal no funciona con el emulador. También puede capturar imágenes y vídeos de realidad mixta.

## <a name="unity"></a>Unity
* Consulte [instalar las herramientas de](install-the-tools.md) para la versión más actualizada de Unity que se recomienda para el desarrollo de HoloLens.
* Problemas conocidos con la versión preliminar técnica de Unity HoloLens se documentan en el [foros HoloLens Unity](http://forum.unity3d.com/threads/known-issues.394627/).

## <a name="windows-device-portal"></a>Windows Device Portal
* La característica de vista previa activa en la captura de realidad mixta puede presentar varios segundos de latencia.
* En la página de entrada Virtual, los controles de gesto y desplazamiento en la sección Virtual gestos no son funcionales. Su uso no tendrá ningún efecto. El teclado virtual en la misma página funciona correctamente.
* Después de habilitar el modo de programador en la configuración, puede tardar unos segundos antes de que el conmutador para activar el Portal de dispositivos está habilitado.

## <a name="api"></a>API
* Si la aplicación establece el [centrarse punto](focus-point-in-unity.md) detrás del usuario o el valor normal a camera.forward, hologramas no aparecerán en Mixed Reality capturar fotos o vídeos. Hasta que se solucione este error en Windows, si las aplicaciones establecer activamente el [centrarse punto](focus-point-in-unity.md) debe asegurarse de la normal del plano se establece opuesto cámara hacia delante (normal, por ejemplo, = - camera.forward).

## <a name="xbox-wireless-controller"></a>Controlador inalámbrico Xbox
* Xbox Wireless controlador S debe actualizarse antes de que se puede usar con HoloLens. Asegúrese de que esté [actualizado](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de intentar emparejar el controlador con un HoloLens.
* Si reinicia el HoloLens mientras está conectado el controlador de Xbox inalámbrica, el controlador no se conectar automáticamente a HoloLens. La luz del botón guía parpadeará lentamente hasta las competencias de controlador desactivado después de 3 minutos. Para volver a conectar el controlador de inmediato, apagar el controlador manteniendo el botón guía hasta que la luz se apaga. Cuando enciende el controlador nuevo, se volverá a conectar a HoloLens.
* Si su HoloLens entra en suspensión mientras está conectado el controlador de Xbox inalámbrico, cualquier entrada en el controlador activará la HoloLens. Puede evitarlo por apagar el controlador cuando haya terminado con él.
