---
title: Uso de Portal de dispositivos Windows
description: Portal de dispositivos Windows para HoloLens te permite configurar y administrar de forma remota el dispositivo mediante Wi-Fi o USB. Device Portal es un servidor web en el dispositivo HoloLens al que puedes conectarte desde un navegador web del equipo. Portal de dispositivos incluye muchas herramientas que te ayudarán a administrar tu HoloLens, así como a depurar y optimizar tus aplicaciones.
author: hamalawi
ms.author: moelhama
ms.date: 02/24/2019
ms.topic: article
keywords: Portal de dispositivos Windows, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 4c84670e616d822bb8a9701a82f779a66ec19fe1
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451369"
---
# <a name="using-the-windows-device-portal"></a>Uso de Portal de dispositivos Windows

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Portal de dispositivos Windows</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Portal de dispositivos Windows para HoloLens te permite configurar y administrar de forma remota el dispositivo mediante Wi-Fi o USB. Device Portal es un servidor web en el dispositivo HoloLens al que puedes conectarte desde un navegador web del equipo. Portal de dispositivos incluye muchas herramientas que te ayudarán a administrar tu HoloLens, así como a depurar y optimizar tus aplicaciones.

Esta documentación trata específicamente sobre el Portal de dispositivos Windows para HoloLens. Para usar Portal de dispositivos Windows para escritorio (incluido para Windows Mixed Reality), consulta [Introducción a Portal de dispositivos Windows](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal).

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configuración de HoloLens para usar Portal de dispositivos Windows

1. Enciende HoloLens y colócalo en el dispositivo.
2. Realiza el [gesto Inicio](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) para HoloLens2 o el de [eclosión](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) en HoloLens (1.ª generación) para iniciar el menú principal. 
3. Mira el icono **Configuración** y realiza el gesto de [pulsación en el aire](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) en HoloLens (1.ª generación) o selecciónalo en HoloLens 2 [tocándolo o usando un haz de mano](https://docs.microsoft.com/hololens/hololens2-basic-usage). 
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilita el **Modo de desarrollador**.
7. [Desplázate hacia abajo](gaze-and-commit.md#composite-gestures) y habilita **Portal de dispositivos**.
8. Si estás configurando Portal de dispositivos Windows para que puedas implementar aplicaciones en este HoloLens a través de USB o Wi-Fi, haz clic en **Emparejar** para [generar un PIN de emparejamiento](using-visual-studio.md). Deja la aplicación Configuración en el menú emergente del PIN hasta que escribas el PIN en Visual Studio durante la primera implementación.

   ![Habilitación del modo de desarrollador en la aplicación Configuración para Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Conexión mediante Wi-Fi

1. [Conecta HoloLens a una red Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Busca la dirección IP de tu dispositivo.
   * Busca la dirección IP del dispositivo en **Configuración > Red e Internet > Wi-Fi > Opciones avanzadas**.
3. Desde un explorador web de tu equipo, ve a https://<TU_DIRECCIÓN_IP_HOLOLENS>
   * Se mostrará el siguiente mensaje en el explorador: "Hay un problema con el certificado de seguridad de este sitio web". Esto ocurre porque el certificado emitido en Device Portal es un certificado de prueba. Puedes ignorar este error de certificado por ahora y continuar.

## <a name="connecting-over-usb"></a>Conexión mediante USB

1. [Instala las herramientas](install-the-tools.md) para asegurarte de que tienes Visual Studio Update 1 con las herramientas del desarrollador de Windows 10 instaladas en el equipo. Esto permite la conectividad USB.
2. Conecta tu HoloLens a tu equipo con un cable micro USB para HoloLens (1.ª generación) o USB-C para HoloLens 2.
3. Desde un explorador web de tu equipo, ve a [https://127.0.0.1:10080](https://127.0.0.1:10080).

## <a name="connecting-to-an-emulator"></a>Conexión a un emulador

También puedes usar Device Portal con el emulador. Para conectarte al Portal de dispositivos, usa la [barra de herramientas](using-the-hololens-emulator.md). Haz clic en este icono: ![Icono de Open Device Portal](images/emulator-deviceportal.png) **Open Device Portal** (Abrir portal de dispositivos): abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.

## <a name="creating-a-username-and-password"></a>Creación de un nombre de usuario y una contraseña

![Configuración del acceso a Portal de dispositivos Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configuración del acceso a Portal de dispositivos Windows*

La primera vez que te conectes a Device Portal en HoloLens, debes crear un nombre de usuario y una contraseña.
1. En un explorador web de tu equipo, escribe la dirección IP de HoloLens. Se abrirá la página de acceso Configuración.
2. Haz clic o pulsa en **Solicitar PIN** y mira la pantalla de HoloLens para obtener el PIN generado.
3. Escribe el PIN en el cuadro de texto **PIN displayed on your device** (PIN mostrado en el dispositivo).
4. Escribe el nombre de usuario que usarás para conectarte a Device Portal. No es necesario que sea un nombre de cuenta de Microsoft (MSA) ni un nombre de dominio.
5. Escribe una contraseña y confírmala. La contraseña debe tener al menos siete caracteres de longitud. No es necesario que sea una MSA ni una contraseña de dominio.
6. Haz clic en **Emparejar** para conectarte al Portal de dispositivos Windows en HoloLens.

Si quieres cambiar este nombre de usuario o contraseña en cualquier momento, puedes repetir este proceso. Para ello, visita la página de seguridad del dispositivo navegando hasta: https://<TU_DIRECCIÓN_IP_HOLOLENS>/devicepair.htm.

## <a name="security-certificate"></a>Certificado de seguridad

Si ves un "error de certificado" en el explorador, puedes corregirlo mediante la creación de una relación de confianza con el dispositivo.

Cada HoloLens genera un certificado autofirmado único para su conexión de SSL. De manera predeterminada, este certificado no es de confianza por parte del explorador web de tu equipo y puede que recibas un "error de certificado". Al descargar este certificado desde HoloLens (a través de USB o una red Wi-Fi en la que confíes) y confiar en el equipo, puedes conectarte a tu dispositivo de forma segura.
1. **Asegúrate de que estás en una red segura (USB o una red Wi-Fi de confianza).**
2. Descarga el certificado de este dispositivo desde la página "Seguridad" de Portal de dispositivos.
   * Ve a: https://<TU_DIRECCIÓN_IP_HOLOLENS>/devicepair.htm
   * Abre el nodo Sistema > Preferencias. 
   * Desplázate hacia abajo hasta Seguridad del dispositivo y haz clic en el botón "Download this device's certificate" (Descargar el certificado de este dispositivo).
3. Instala el certificado en el almacén "Entidades de certificación raíz de confianza" en tu equipo.
   * En el menú Windows, escribe: Administrar certificados de equipo e inicia el applet.
   * Expande la carpeta **Entidad de certificación de raíz de confianza**.
   * Haga clic en la carpeta **Certificados**.
   * En el menú Acción, selecciona: Todas las tareas > Importar...
   * Completa el Asistente para importación de certificados con el archivo de certificado descargado desde Device Portal.
4. Reinicia el explorador.

>[!NOTE]
> Este certificado solo será de confianza para el dispositivo y el usuario tendrá que volver a realizar el proceso si se instala una imagen en el dispositivo.


## <a name="device-portal-pages"></a>Páginas de Device Portal

### <a name="home"></a>Inicio

![Página principal de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Página principal de Portal de dispositivos Windows en Microsoft HoloLens*

La sesión de Device Portal se inicia en la página principal. Accede a otras páginas desde la barra de navegación en el lado izquierdo de la página principal.

La barra de herramientas de la parte superior de la página proporciona acceso al estado usado frecuentemente y a las características.
* **En línea**: indica si el dispositivo está conectado a Wi-Fi.
* **Apagar**: apaga el dispositivo.
* **Reiniciar**: apaga y vuelve a encender el dispositivo.
* **Seguridad**: abre la página Seguridad del dispositivo.
* **Frío**: indica la temperatura del dispositivo.
* **CA**: indica si el dispositivo está enchufado y cargándose.
* **Ayuda**: abre la página de documentación de la interfaz REST.

En la página principal se muestra la siguiente información:
* **Estado del dispositivo**: supervisa el estado del dispositivo y notifica los errores graves.
* **Información de Windows**: muestra el nombre de HoloLens y la versión de Windows instalada actualmente.
* La sección **Preferencias** contiene las siguientes configuraciones:
   * **IPD**: establece la distancia interpupilar (IPD), que es la distancia, en milímetros, entre el centro de las pupilas del usuario cuando mira al frente. La configuración surte efecto inmediatamente. El valor predeterminado se calculó automáticamente al configurar el dispositivo.
   * **Nombre del dispositivo**: asigna un nombre a HoloLens. Debes reiniciar el dispositivo después de cambiar este valor para que surta efecto. Después de hacer clic en **Guardar**, se te preguntará en un cuadro de diálogo si quieres reiniciar el dispositivo inmediatamente o más tarde.
   * **Configuración de suspensión**: establece el período de tiempo de espera antes de que el dispositivo entre en el modo de suspensión cuando está conectado y cuando funciona con batería.

### <a name="3d-view"></a>Vista 3D

![Página Vista 3D de Portal de dispositivos en Microsoft HoloLens](images/3dview-1000px.png)<br>
*Página Vista 3D de Portal de dispositivos en Microsoft HoloLens*

Usa la página Vista 3D para ver cómo HoloLens interpreta el entorno. Navega por la vista con el mouse:
* Girar: haz clic con el botón izquierdo + mouse;
* Panorámica: haz clic con el botón derecho + mouse;
* Zoom: desplazamiento del mouse.
* **Opciones de seguimiento**
   * activa el seguimiento visual continuo marcando la opción **Force visual tracking** (Forzar seguimiento visual). 
   * **Pausa** detiene el seguimiento visual.
* **Opciones de vista**: establece las opciones en la vista 3D:
  * **Seguimiento**: indica si el seguimiento visual está activo.
  * **Show floor** (Mostrar suelo): muestra un plano de la planta a cuadros.
  * **Show frustum** (Mostrar tronco): muestra el tronco de la vista.
  * **Show stabilization plane** (Mostrar plano de estabilización): muestra el plano que HoloLens usa para estabilizar el movimiento.
  * **Show mesh** (Mostrar malla): muestra la malla de asignación espacial que representa el entorno.
  * **Show spatial anchors** (Mostrar delimitadores espaciales): muestra los delimitadores espaciales para la aplicación activa. Debes hacer clic en el botón Actualizar para obtener y actualizar los delimitadores.
  * **Mostrar detalles**: muestra las posiciones de la mano, los cuaterniones de rotación de la cabeza y el vector de origen del dispositivo cuando cambian en tiempo real.
  * **Botón Pantalla completa**: muestra la vista 3D en modo de pantalla completa. Presiona ESC para salir de la vista de pantalla completa.
* **Reconstrucción de superficie**: haz clic o pulsa en **Actualizar** para mostrar la última malla de asignación espacial del dispositivo. Un recorrido completo puede tardar un tiempo en completarse, unos segundos. La malla no se actualiza automáticamente en la vista 3D y debes hacer clic manualmente en **Actualizar** para obtener la malla más reciente desde el dispositivo. Haz clic en **Guardar** para guardar la malla de asignación espacial actual como un archivo obj en tu equipo.
* **Spatial Anchors**: haz clic en Actualizar para mostrar o actualizar los delimitadores espaciales de la aplicación activa.

### <a name="mixed-reality-capture"></a>Captura de realidad mixta

![Página Captura de realidad mixta de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Página Captura de realidad mixta de Portal de dispositivos Windows en Microsoft HoloLens*

Usa la página Mixed Reality Capture (Captura de realidad mixta) para guardar flujos multimedia desde HoloLens.
* **Configuración de captura**: controla las secuencias multimedia que se capturan comprobando la siguiente configuración:
  * **Hologramas**: captura el contenido holográfico en la secuencia de vídeo. Los hologramas se representan en mono y no estéreo.
  * **PV camera** (Cámara de vídeo o fotos): captura la secuencia de vídeo de la cámara de vídeo o fotos.
  * **Mic Audio** (Audio de micrófono): captura el audio de la matriz del micrófono.
  * **App Audio** (Audio de la aplicación): captura el audio de la aplicación que está en ejecución actualmente.
  * **Render from Camera** (Representar desde la cámara): alinea la captura para que provenga de la perspectiva de la cámara de vídeo o fotos, en caso de que [la aplicación en ejecución la admita](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (solo HoloLens 2).
  * **Live preview quality** (Calidad de vista previa dinámica): selecciona la resolución de pantalla, la velocidad de fotogramas y la velocidad de streaming de la vista previa dinámica.
* **Configuración de audio** (solo HoloLens 2):
  * **Audio Media Category** (Categoría de medio de audio): seleccione la categoría que se usa al procesar el micrófono. **Predeterminada**: incluye parte del entorno, mientras que **Comunicaciones** aplica la cancelación del ruido de fondo.
  * **App Audio Gain** (Ganancia de audio de aplicación): la ganancia aplicada al volumen de audio de la aplicación.
  * **Mic Audio Gain** (Ganancia de audio de micrófono): la ganancia aplicada al volumen de audio del micrófono.
* **Photo and Video Settings** (Configuración de foto y vídeo) (HoloLens 2, versión 2004 o posterior):
  * **Capture Profile** (Perfil de captura): seleccione el perfil usado al tomar fotos y grabar vídeos. El perfil determina qué resoluciones y velocidades de fotogramas están disponibles.
  * **Resolución de foto**: la resolución con la que se tomará la foto.
  * **Video Resolution and Frame-rate** (Resolución de vídeo y velocidad de fotogramas): la resolución y la velocidad de fotogramas con las que se grabará el vídeo.
  * **Video Stabilization Buffer** (Búfer de estabilización de vídeo): tamaño de búfer usado al grabar un vídeo. Cuanto mayor sea el valor, mejor puede compensar los movimientos rápidos.
* Haz clic o pulsa en el botón **Vista previa dinámica** para mostrar el flujo de captura. **Stop live preview** (Detener la vista previa dinámica) detiene la secuencia de captura.
* Haz clic o pulsa en **Grabar** para comenzar a grabar la secuencia de realidad mixta, con la configuración especificada. **Detener grabación** finaliza la grabación y la guarda.
* Haz clic o pulsa en **Hacer una foto** para tomar una imagen estática de la secuencia de captura.
* Haga clic o pulse en **Restaurar configuración predeterminada** para restaurar la configuración predeterminada para las opciones de audio, foto y vídeo.
* **Vídeos y fotos**: muestra una lista de las capturas de vídeo y fotos tomadas en el dispositivo.

Todas las opciones de esta página se aplican a las capturas tomadas mediante el Portal de dispositivos Windows, pero algunas se aplican también a MRC del sistema (menú Inicio, botones de hardware, comandos de voz globales, Miracast) y a las grabadoras de MRC personalizadas.
|  Valor  |  Se aplica a MRC del sistema  |  Se aplica a grabadoras de MRC personalizadas |
|----------|----------|----------|
|  Hologramas  |  No  |  No |
|  Cámara de foto y vídeo  |  No  |  No |
|  Mic Audio (Audio de micrófono)  |  No  |  No |
|  App Audio (Audio de la aplicación)  |  No  |  No |
|  Render from Camera (Representar desde la cámara)  |  Sí    |  Sí (se puede invalidar) |
|  Live preview quality (Calidad de vista previa dinámica)  |  No  |  No |
|  Audio Media Category (Categoría de medio de audio)  |  Sí  |  No |
|  App Audio Gain (Ganancia de audio de aplicación)  |  Sí  |  Sí (se puede invalidar) |
|  Mic Audio Gain (Ganancia de audio de micrófono)  |  Sí  |  Sí (se puede invalidar) |
|  Capture Profile (Perfil de captura)  |  Sí  |  No |
|  Resolución de foto  |  Sí  |  No |
|  Video Resolution and Frame-rate (Resolución de vídeo y velocidad de fotogramas)  |  Sí  |  No |
|  Video Stabilization Buffer (Búfer de estabilización de vídeo)  |  Sí  |  Sí (se puede invalidar) |

> [!NOTE]
> Hay [limitaciones de MRC simultáneas](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Si una aplicación intenta acceder a la cámara de vídeo o fotos mientras Portal de dispositivos Windows graba un vídeo, la grabación de vídeo se detendrá.
>   * HoloLens 2 no dejará de grabar vídeo si la aplicación accede a la cámara de vídeo o fotos con el modo SharedReadOnly.
> * Si una aplicación usa activamente la cámara de vídeo o fotos, Portal de dispositivos de Windows puede tomar una foto o grabar un vídeo.
> * Streaming en directo:
>   * HoloLens (1.ª generación) impide que una aplicación acceda a la cámara de vídeo o fotos durante el streaming en vivo desde Portal de dispositivos Windows.
>   * HoloLens (1.ª generación) no podrá hacer streaming en vivo si una aplicación está usando activamente la cámara de vídeo o fotos.
>   * HoloLens 2 detiene automáticamente el streaming en vivo cuando una aplicación intenta acceder a la cámara de vídeo o fotos en modo ExclusiveControl.
>   * HoloLens 2 es capaz de iniciar el streaming en vivo mientras una aplicación usa activamente la cámara de vídeo o fotos.

### <a name="performance-tracing"></a>Seguimiento de rendimiento

![Página Seguimiento de rendimiento de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Página Seguimiento de rendimiento de Portal de dispositivos Windows en Microsoft HoloLens*

Captura los seguimientos de [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) de HoloLens.
* **Perfiles disponibles**: selecciona el perfil de WPR en la lista desplegable y pulsa o haz clic en **Inicio** para iniciar el seguimiento.
* **Perfiles personalizados**: haz clic o pulsa en **Examinar** para elegir un perfil de WPR de tu equipo. Haz clic o pulsa en **Cargar e iniciar** para iniciar el seguimiento.

Para detener el seguimiento, haz clic en el vínculo de detención. Permanece en esta página hasta que el archivo de seguimiento se haya terminado de descargar.

Los archivos ETL se pueden abrir para realizar análisis en [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Procesos

![Página Procesos de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Página Procesos de Portal de dispositivos Windows en Microsoft HoloLens*

Muestra detalles acerca de los procesos que se ejecutan actualmente. Esto incluye aplicaciones y procesos del sistema.

### <a name="system-performance"></a>Rendimiento del sistema

![Página Rendimiento del sistema de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Página Rendimiento del sistema de Portal de dispositivos Windows en Microsoft HoloLens*

Muestra gráficos en tiempo real de la información de diagnóstico del sistema, como el uso de energía, la velocidad de fotogramas y la carga de la CPU.

Estas son las métricas disponibles:
* **SoC power** (Energía SoC): uso de energía instantánea system-on-chip, con una media superior a un minuto
* **Energía del sistema**: uso de energía instantánea del sistema, con una media superior a un minuto
* **Velocidad de fotogramas**: fotogramas por segundo, VBlank (intervalos verticales) perdidos por segundo y VBlank perdidos consecutivos
* **GPU**: uso del motor de la GPU, porcentaje del total disponible
* **CPU**: porcentaje del total disponible
* **E/S**: lecturas y escrituras
* **Red**: envíos y recepciones
* **Memoria:** total, en uso, confirmada, paginada y no paginada

### <a name="apps"></a>Aplicaciones

![Página Aplicaciones de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Página Aplicaciones de Portal de dispositivos Windows en Microsoft HoloLens*

Administra las aplicaciones que están instaladas en HoloLens.
* **Aplicaciones instaladas**: quita e inicia aplicaciones.
* **Aplicaciones en ejecución**: enumera las aplicaciones que se ejecutan actualmente.
* **Instalar aplicación**: selecciona paquetes de la aplicación para la instalación desde una carpeta en el equipo o red.
* **Dependencia**: agrega las dependencias de la aplicación que vas a instalar.
* **Implementar**: implementa la aplicación seleccionada y las dependencias en HoloLens.

### <a name="app-crash-dumps"></a>Página de volcados de memoria de la aplicación

![Página de volcados de memoria de aplicación de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Página de volcados de memoria de aplicación de Portal de dispositivos Windows en Microsoft HoloLens*

En esta página puedes recopilar los volcados de memoria de las aplicaciones transferidas localmente. Marca la casilla **Crash Dumps Enabled** (Volcados de memoria habilitados) de cada aplicación de la que quieras recopilar volcados de memoria. Vuelve a esta página para recopilar los volcados de memoria. Los archivos de volcado se pueden [abrir en Visual Studio para su depuración](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Explorador de archivos

![Página Explorador de archivos de Portal de dispositivos Windows en Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Página Explorador de archivos de Portal de dispositivos Windows en Microsoft HoloLens*

Usa el explorador de archivos para examinar, cargar y descargar archivos. Puedes trabajar con archivos en la carpeta Documentos, en la carpeta Imágenes y en las carpetas de almacenamiento local para las aplicaciones que implementaste desde Visual Studio o desde Portal de dispositivos.

### <a name="kiosk-mode"></a>Pantalla completa

>[!NOTE]
>La opción de pantalla completa solo está disponible con [Microsoft HoloLens Commercial Suite](commercial-features.md).

Consulta el artículo [Configurar HoloLens en pantalla completa](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) en Windows IT Pro Center para obtener instrucciones actualizadas sobre cómo habilitar la pantalla completa a través de Portal de dispositivos Windows.

### <a name="logging"></a>Registro

![Página Registro de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Página Registro de Portal de dispositivos Windows en Microsoft HoloLens*

Administra el seguimiento de eventos para Windows (ETW) en tiempo real en HoloLens.

Marca **Hide providers** (Ocultar proveedores) para mostrar solamente la lista **Eventos**.
* **Registered providers** (Proveedores registrados): selecciona el proveedor ETW y el nivel de seguimiento. El nivel de seguimiento es uno de estos valores:
   1. Terminación o salida anómala
   2. Errores graves
   3. Warnings
   4. Advertencias sin errores

Haz clic o pulsa en **Activar** para iniciar el seguimiento. El proveedor se agrega a la lista desplegable de **Proveedores habilitados**.
* **Proveedores personalizados**: selecciona el proveedor ETW personalizado y el nivel de seguimiento. Identifica el proveedor por su GUID. No incluyas corchetes en el GUID.
* **Proveedores habilitados**: enumera los proveedores habilitados. Selecciona un proveedor de la lista desplegable y haz clic o pulsa en **Desactivar** para detener el seguimiento. Haz clic o pulsa en **Detener todo** para suspender todos los seguimientos.
* **Providers history** (Historial de proveedores): muestra los proveedores ETW habilitados durante la sesión actual. Haz clic o pulsa en **Activar** para activar un proveedor deshabilitado. Haz clic o pulsa en **Borrar** para borrar el historial.
* **Eventos**: enumera los eventos ETW de los proveedores seleccionados en formato de tabla. Esta tabla se actualiza en tiempo real. Debajo de la tabla, haz clic en el botón **Borrar** para eliminar todos los eventos ETW de la tabla. Esta acción no deshabilita ningún proveedor. Puedes hacer clic en **Guardar en archivo** para exportar los eventos ETW recopilados actualmente en un archivo CSV de forma local.
* **Filtros**: permite filtrar los eventos ETW recopilados por id., palabra clave, nivel, nombre de proveedor, nombre de la tarea o texto. Puedes combinar varios criterios:
   1. En el caso de los criterios que se aplican a la misma propiedad, se muestran los eventos que pueden cumplir cualquiera de ellos.
   2. En el caso de los criterios que se aplican a una propiedad diferente, los eventos deben cumplir todos los criterios.

Por ejemplo, puedes especificar los criterios *(el nombre de tarea contiene "Foo" o "Bar") y (el texto contiene "error" o "advertencia")*

### <a name="simulation"></a>Simulation

![Página Simulación de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Página Simulación de Portal de dispositivos Windows en Microsoft HoloLens*

Te permite grabar y reproducir datos de entrada para las pruebas.
* **Capture room** (Espacio de captura): se usa para descargar un archivo de espacio simulado que contiene la malla espacial de asignación del entorno del usuario. Asigna un nombre al espacio y, a continuación, haz clic en **Capturar** para guardar los datos como un archivo .xef en tu equipo. Puedes cargar este archivo de espacio en el emulador HoloLens.
* **Grabación**: marca los flujos que quieres grabar, asigna un nombre a la grabación y haz clic o pulsa en **Grabar** para iniciar la grabación. Realiza acciones con HoloLens y, a continuación, haz clic en **Detener** para guardar los datos como un archivo .xef en tu equipo. Este archivo se puede cargar en el dispositivo o emulador HoloLens.
* **Reproducción**: haz clic o pulsa en **Cargar grabación** para seleccionar un archivo .xef desde tu equipo y enviar los datos a HoloLens.
* **Modo de control**: selecciona **Valor predeterminado** o **Simulación** en la lista desplegable y pulsa o haz clic en el botón **Establecer** para seleccionar el modo en HoloLens. Si eliges "Simulación", se deshabilitan los sensores reales de HoloLens y se usan los datos simulados cargados en su lugar. Si cambias a "Simulación", HoloLens no responderá al usuario real hasta que vuelva al "Valor predeterminado".

### <a name="networking"></a>Funciones de red

![Página Redes de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Página Redes de Portal de dispositivos Windows en Microsoft HoloLens*

Administra conexiones Wi-Fi en HoloLens.
* **WiFi adapters** (Adaptadores WiFi): Selecciona un adaptador Wi-Fi y un perfil mediante los controles desplegables. Pulsa o haz clic en **Conectar** para usar el adaptador seleccionado.
* **Redes disponibles**: enumera las redes Wi-Fi a las que se puede conectar HoloLens. Haz clic en o pulsa en **Actualizar** para actualizar la lista.
* **Configuración IP**: muestra la dirección IP y otros detalles de la conexión de red.

### <a name="virtual-input"></a>Entrada virtual

![Página Entrada virtual de Portal de dispositivos Windows en Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Página Entrada virtual de Portal de dispositivos Windows en Microsoft HoloLens*

Envía la entrada de teclado desde la máquina remota a HoloLens.

Haz clic o pulsa en la región de debajo de **Teclado virtual** para habilitar el envío de pulsaciones de teclas a HoloLens. Escribe en el cuadro de texto **Texto de entrada** y haz clic o pulsa en **Enviar** para enviar las pulsaciones de teclas a la aplicación activa.

## <a name="device-portal-rest-apis"></a>API de REST del Portal de dispositivos

Todo lo que contiene Portal de dispositivos Windows se basa en las [API de REST](device-portal-api-reference.md) que puedes usar para acceder a los datos y controlar el dispositivo mediante programación.
