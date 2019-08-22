---
title: Problemas conocidos de HoloLens
description: Esta es la lista de problemas conocidos que pueden afectar a los desarrolladores de HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: solución de problemas, problema conocido, ayuda
ms.openlocfilehash: f043164f21f20925a78b59057e14ac4607d0d3f1
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896544"
---
# <a name="hololens-known-issues"></a>Problemas conocidos de HoloLens

Esta es la lista actual de problemas conocidos de HoloLens que afectan a los desarrolladores. Active esta casilla primero si ve un comportamiento extraño. Esta lista se mantendrá actualizada a medida que se detecten o notifiquen nuevos problemas, o cuando se solucionen problemas en futuras actualizaciones de software de HoloLens.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>No se puede conectar e implementar en HoloLens a través de Visual Studio

>[!NOTE]
>Última actualización: 8/8 @ 5:11 P.M.-Visual Studio ha publicado VS 2019 versión 16,2 que incluye una corrección para este problema. Se recomienda actualizar a esta versión más reciente para evitar que se produzca este error.

Visual Studio ha publicado VS 2019 versión 16,2, que incluye una corrección para este problema. Se recomienda actualizar a esta versión más reciente para evitar que se produzca este error.

Causa raíz del problema: Los usuarios que usaron Visual Studio 2015 o versiones anteriores de Visual Studio 2017 para implementar y depurar aplicaciones en HoloLens y, posteriormente, usar las versiones más recientes de Visual Studio 2017 o Visual Studio 2019 con el mismo HoloLens se verán afectados. Las versiones más recientes de Visual Studio implementan una nueva versión de un componente, pero los archivos de la versión anterior se dejan en el dispositivo, lo que provoca un error en la versión más reciente.  Esto produce el siguiente mensaje de error: DEP0100: Asegúrese de que el dispositivo de destino tiene habilitado el modo de desarrollador. No se pudo obtener una licencia de <ip> Desarrollador en debido al error 80004005.
 
**Solución**: 

Nuestro equipo está trabajando actualmente en una solución. Mientras tanto, puede usar los pasos siguientes para solucionar el problema y ayudar a desbloquear la implementación y la depuración:  
1. Abra Visual Studio
2. Proyecto > Nuevo-> de archivo
3. Visual C# -> aplicación de consola de > de escritorio de Windows (.NET Framework)
4. Asigne un nombre al proyecto (por ejemplo, HoloLensDeploymentFix) y asegúrese de que el marco esté establecido en al menos .NET Framework 4,5 y, a continuación, haga clic en Aceptar.
5. Haga clic con el botón secundario en el nodo referencias en Explorador de soluciones y agregue las referencias siguientes (haga clic en la sección "examinar" y haga clic en "examinar..." botón):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >Si no tiene 10.0.18362.0 instalado, use la versión más reciente que tenga.
 
6. Haga clic con el botón derecho en el proyecto en Explorador de soluciones y elija Agregar > elemento existente.
 
7. Vaya a C:\Archivos de programa (x86) \Windows Kits\10\bin\10.0.18362.0\x86 y cambie el filtro a "todos los\*archivos\*(.)".
 
8. Seleccione SirepClient. dll y SshClient. dll y haga clic en "agregar".
 
9. Busque y seleccione ambos archivos en Explorador de soluciones (deben estar en la parte inferior de la lista de archivos) y cambie "copiar en el directorio de salida" en el ventana Propiedades a "copiar siempre".
 
10. En la parte superior del archivo, agregue lo siguiente a la lista existente de instrucciones ' Using ': 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. Dentro de "Static void main (...)", agregue el código siguiente:
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. Compilar: > la solución de compilación
 
13. Abra un símbolo del sistema para la carpeta que contiene el archivo. exe compilado (p. ej., C:\MyProjects\HoloLensDeploymentFix\bin\Debug)
 
14. Ejecute el archivo ejecutable y proporcione la dirección IP del dispositivo como argumento de la línea de comandos.  (Si se conecta a través de USB, puede usar 127.0.0.1; de lo contrario, use la dirección IP de Wi-Fi del dispositivo).  Por ejemplo, "HoloLensDeploymentFix 127.0.0.1"
 
15. Una vez que la herramienta haya salido sin ningún mensaje (esto solo debería tardar unos segundos), ahora podrá implementar y depurar desde Visual Studio 2017 o una versión más reciente.  El uso continuado de la herramienta no es necesario.

Le proporcionaremos más actualizaciones a medida que estén disponibles.

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Problemas al iniciar el Microsoft Store y las aplicaciones en HoloLens

>[!NOTE]
>Última actualización: 4/2 @ 10 AM-problema resuelto. 

Puede experimentar problemas al intentar iniciar el Microsoft Store y las aplicaciones en HoloLens. Hemos determinado que el problema se produce cuando las actualizaciones de la aplicación en segundo plano implementan una versión más reciente de los paquetes de Framework en secuencias específicas mientras que una o varias de sus aplicaciones dependientes todavía se están ejecutando. En este caso, una actualización de aplicación automática proporcionó una nueva versión de .NET Native Framework (versión 10.0.25531 a 10.0.27413), las aplicaciones que se están ejecutando no se actualizan correctamente para todas las aplicaciones en ejecución que consumen la versión anterior del marco.  El flujo para la actualización del marco es el siguiente:

1.  El nuevo paquete de Framework se descarga del almacén y se instala.
2.  Todas las aplicaciones que usan el marco anterior se ' actualizan ' para usar la versión más reciente

Si se interrumpe el paso 2 antes de la finalización, las aplicaciones para las que no se registró el marco de trabajo más reciente no se podrán iniciar desde el menú Inicio.  Creemos que cualquier aplicación en HoloLens podría verse afectada por este problema.

Algunos usuarios han comunicado que el cierre de aplicaciones bloqueadas y el inicio de otras aplicaciones como el centro de opiniones, el visor 3D o las fotos resuelven el problema. sin embargo, esto no funcionará el 100% del tiempo.

Tenemos la raíz debido a que este problema no causó la actualización en sí, sino un error en el sistema operativo que dio lugar a que la actualización del marco de .NET Native se controlara de forma incorrecta. Nos complace anunciar que hemos identificado una corrección y que hemos lanzado una actualización (versión 17763,380 del SO) que contiene la corrección. 

Para ver si el dispositivo puede realizar la actualización, haga lo siguiente:

1.  Vaya a la aplicación "configuración" y abra "actualizar & seguridad".
2.  Haga clic en "buscar actualizaciones".
3.  Si está disponible la actualización a 17763,380, actualice a esta compilación para recibir la corrección del error de bloqueo de la aplicación.
4.  Al actualizar a esta versión del sistema operativo, las aplicaciones deben funcionar según lo previsto.

Además, como hacemos con cada versión del sistema operativo HoloLens, hemos publicado la imagen de FFU en el centro de descarga https://aka.ms/hololensdownload/10.0.17763.380 de Microsoft en. 

Si no desea realizar la actualización, hemos publicado una nueva versión de la aplicación Microsoft Store UWP a partir de 3/29. Una vez que tenga la versión actualizada del almacén:

1) Abra el almacén y confirme que se carga.
2) Use el gesto de floración para abrir el menú.
3) Intento de abrir aplicaciones interrumpidas previamente
3) Si todavía no se puede iniciar, mantenga pulsado el icono de la aplicación interrumpida y seleccione Desinstalar.
4) Resinstall estas aplicaciones de la tienda.

Si el dispositivo sigue sin poder cargar aplicaciones, puede transferir localmente una versión del marco de trabajo de .NET Native y el tiempo de ejecución a través del centro de descarga haciendo lo siguiente:

1)  Descargue [este archivo zip](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) del centro de descarga de Microsoft.  La descompresión producirá dos archivos.  Microsoft. NET. Native. Runtime. 1.7. appx y Microsoft. NET. Native. Framework. 1.7. appx
2)  Compruebe que el dispositivo está desbloqueado.  Si no lo ha hecho antes de las instrucciones que debe hacer [aquí](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).
3)  A continuación, desea entrar en el portal de dispositivos de Windows.  Nuestra recomendación es hacer esto a través de USB y lo haría escribiendo http://127.0.0.1:10080 en el explorador.  
4)  Una vez que tenga el portal de dispositivos de Windows, necesitará "cargar" los dos archivos que descargó.  Para ello, debe ir a la barra lateral izquierda hasta llegar a la sección "aplicaciones" y hacer clic en "aplicaciones".
5)  Verá una pantalla similar a la siguiente.  Quiere ir a la sección en la que se indica "instalar aplicación" y buscar dónde descomprimió esos dos archivos APPX.  Solo puede realizar una sola vez, por lo que después de seleccionar la primera, haga clic en "ir" en la sección implementar.  A continuación, haga esto para el segundo archivo APPX. 
  ![Windows Device portal para instalar la aplicación de instalación de prueba](images/20190322-DevicePortal.png)<br>
6)  En este punto creemos que las aplicaciones deben empezar a funcionar de nuevo y que también puede acceder a la tienda.
7)  En algunos casos, es necesario ejecutar el paso adicional de iniciar la aplicación de visor 3D antes de que se inicien las aplicaciones afectadas. 

Agradecemos su paciencia a medida que hemos pasado por el proceso para resolver este problema y esperamos seguir trabajando con nuestra comunidad para crear experiencias de realidad mixta.

## <a name="connecting-to-wifi"></a>Conexión a Wi-Fi

Durante la configuración de OOBE &, hay un tiempo de espera de credencial de 2 minutos. El nombre de usuario/contraseña debe especificarse en 2 minutos; de lo contrario, el campo de nombre de usuario se desactivará automáticamente.

Se recomienda usar un teclado Bluetooth para escribir contraseñas largas.

>[!NOTE]
> Si se selecciona la red incorrecta durante la OOBE, el dispositivo deberá restablecerse por completo. Las instrucciones se pueden encontrar [aquí.](https://docs.microsoft.com/en-us/windows/mixed-reality/reset-or-recover-your-hololens#perform-a-full-device-recovery) 

## <a name="device-update"></a>Actualización del dispositivo
* 30 segundos después de una nueva actualización, el shell puede desaparecer una vez. Realice el gesto de **floración** para reanudar la sesión.

## <a name="visual-studio"></a>Programa para la mejora
* Vea [instalar las herramientas](install-the-tools.md) para la versión más actualizada de Visual Studio recomendada para el desarrollo de HoloLens.
* Al implementar una aplicación desde Visual Studio a HoloLens, es posible que vea el error: **La operación solicitada no se puede realizar en un archivo con una sección asignada por el usuario abierta. (Excepción de HRESULT: 0x800704C8)** . Si esto ocurre, inténtelo de nuevo y la implementación se realizará normalmente.

## <a name="emulator"></a>Emulador
* No todas las aplicaciones del Microsoft Store son compatibles con el emulador. Por ejemplo, los conkers y los fragmentos jóvenes no se pueden reproducir en el emulador.
* No se puede usar la cámara web de PC en el emulador.
* La característica de vista previa dinámica del portal de dispositivos de Windows no funciona con el emulador. Todavía puede capturar imágenes y vídeos de realidad mixta.

## <a name="unity"></a>Unity
* Vea [instalar las herramientas](install-the-tools.md) para la versión más actualizada de Unity recomendada para el desarrollo de HoloLens.
* Los problemas conocidos de la versión preliminar técnica de Unity HoloLens se documentan en los [foros de Unity de hololens](http://forum.unity3d.com/threads/known-issues.394627/).

## <a name="windows-device-portal"></a>Windows Device Portal
* La característica de vista previa dinámica de la captura de realidad mixta puede presentar varios segundos de latencia.
* En la página de entrada virtual, los controles de gesto y desplazamiento en la sección de gestos virtuales no son funcionales. Su uso no tendrá ningún efecto. El teclado virtual de la misma página funciona correctamente.
* Después de habilitar el modo de Desarrollador en la configuración, puede tardar unos segundos antes de que se habilite el conmutador para activar el portal de dispositivos.

## <a name="api"></a>API
* Si la aplicación establece el [punto de enfoque](focus-point-in-unity.md) detrás del usuario o el normal a la cámara. avance, los hologramas no aparecerán en las fotos o vídeos de la realidad mixta. Hasta que se solucione este error en Windows, si las aplicaciones establecen activamente el [punto de enfoque](focus-point-in-unity.md) , deben asegurarse de que el plano normal está establecido en la cámara hacia delante (por ejemplo, normal =-Camera. forward).

## <a name="xbox-wireless-controller"></a>Controlador inalámbrico Xbox
* La controladora inalámbrica Xbox debe actualizarse antes de poder usarla con HoloLens. Asegúrese de que está [actualizado](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de intentar emparejar el controlador con un HoloLens.
* Si reinicia HoloLens mientras el controlador inalámbrico de Xbox está conectado, el controlador no se volverá a conectar automáticamente a HoloLens. La luz del botón de la guía parpadeará lentamente hasta que el controlador se apague después de 3 minutos. Para volver a conectar el controlador inmediatamente, apague el controlador manteniendo el botón guía hasta que se apague la luz. Cuando vuelva a encender el controlador, se volverá a conectar a HoloLens.
* Si HoloLens entra en modo de espera mientras el controlador inalámbrico Xbox está conectado, cualquier entrada en el controlador reactivará HoloLens. Para evitarlo, apague el controlador cuando termine de usarlo.
