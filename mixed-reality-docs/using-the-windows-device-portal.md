---
title: Uso del portal de dispositivos de Windows
description: Windows Device portal para HoloLens le permite configurar y administrar el dispositivo de forma remota a través de Wi-Fi o USB. Device Portal es un servidor web en el dispositivo HoloLens al que puedes conectarte desde un navegador web del equipo. El portal de dispositivos incluye muchas herramientas que le ayudarán a administrar su HoloLens y a depurar y optimizar sus aplicaciones.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Portal de dispositivos de Windows, HoloLens
ms.openlocfilehash: 9bb8116330d88c532b955ef497d29fe98c86fddb
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182025"
---
# <a name="using-the-windows-device-portal"></a>Uso del portal de dispositivos de Windows

<table>
<tr>
<th>Función</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1ª generación)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Windows Device portal para HoloLens le permite configurar y administrar el dispositivo de forma remota a través de Wi-Fi o USB. Device Portal es un servidor web en el dispositivo HoloLens al que puedes conectarte desde un navegador web del equipo. El portal de dispositivos incluye muchas herramientas que le ayudarán a administrar su HoloLens y a depurar y optimizar sus aplicaciones.

Esta documentación trata específicamente sobre el portal de dispositivos de Windows para HoloLens. Para usar el portal de dispositivos de Windows para escritorio (incluido para Windows Mixed Reality), consulte [Introducción a Windows Device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal) .

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configuración de HoloLens para usar el portal de dispositivos de Windows

1. Enciende HoloLens y colócalo en el dispositivo.
2. Realice el [gesto de inicio](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) de HoloLens2 o [floración](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) en HoloLens (1ª generación) para abrir el menú principal. 
3. Mira el icono de **configuración** y realiza el gesto de [puntear](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) en hololens (1ª generación) o seleccionarlo en hololens 2. para ello, debe [tocarlo o usar un rayo](https://docs.microsoft.com/hololens/hololens2-basic-usage). 
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilita el **Modo de desarrollador**.
7. [Desplácese hacia abajo](gaze-and-commit.md#composite-gestures) y habilite el **portal de dispositivos**.
8. Si está configurando Windows Device portal para que pueda implementar aplicaciones en este HoloLens a través de USB o Wi-Fi, haga clic en **emparejar** para [generar un PIN de emparejamiento](using-visual-studio.md). Deje la aplicación de configuración en el menú emergente del PIN hasta que escriba el PIN en Visual Studio durante la primera implementación.

   ![Habilitación del modo de Desarrollador en la aplicación de configuración para Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Conexión a través de Wi-Fi

1. [Conecte su HoloLens a Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Buscar la dirección IP del dispositivo.
   * Busque la dirección IP en el dispositivo en **configuración > red & Internet > Wi-Fi > opciones avanzadas**.
3. Desde un explorador Web en su equipo, vaya a https://< YOUR_HOLOLENS_IP_ADDRESS >
   * El explorador mostrará el siguiente mensaje: "hay un problema con el certificado de seguridad de este sitio web". Esto ocurre porque el certificado emitido en Device Portal es un certificado de prueba. Puedes ignorar este error de certificado por ahora y continuar.

## <a name="connecting-over-usb"></a>Conexión a través de USB

1. [Instale las herramientas](install-the-tools.md) para asegurarse de que tiene Visual Studio Update 1 con las herramientas de desarrollo de Windows 10 instaladas en su equipo. Esto permite la conectividad USB.
2. Conecta HoloLens en el equipo con un cable micro-USB.
3. Desde un explorador Web en su equipo, vaya a [https://127.0.0.1:10080](https://127.0.0.1:10080).

## <a name="connecting-to-an-emulator"></a>Conectarse a un emulador

También puedes usar Device Portal con el emulador. Para conectarse al portal de dispositivos, use la [barra de herramientas](using-the-hololens-emulator.md). Haga clic en este icono: ![abrir el icono del portal de dispositivos](images/emulator-deviceportal.png) **abrir el portal**de dispositivos: Abra el portal de dispositivos de Windows para el sistema operativo HoloLens en el emulador.

## <a name="creating-a-username-and-password"></a>Crear un nombre de usuario y una contraseña

![configurar el acceso al portal de dispositivos de Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurar el acceso al portal de dispositivos de Windows*

La primera vez que te conectes a Device Portal en HoloLens, debes crear un nombre de usuario y una contraseña.
1. En un explorador web de tu equipo, escribe la dirección IP de HoloLens. Se abrirá la página de acceso Configuración.
2. Pulse o haga clic en **solicitar PIN** y mire la pantalla de HoloLens para obtener el PIN generado.
3. Escriba el PIN en el **código PIN mostrado en** el cuadro de texto del dispositivo.
4. Escribe el nombre de usuario que usarás para conectarte a Device Portal. No es necesario que sea un nombre de cuenta de Microsoft (MSA) ni un nombre de dominio.
5. Escribe una contraseña y confírmala. La contraseña debe tener al menos siete caracteres de longitud. No es necesario que sea una MSA ni una contraseña de dominio.
6. Haga clic en **emparejar** para conectarse al portal de dispositivos de Windows en HoloLens.

Si desea cambiar este nombre de usuario o contraseña en cualquier momento, puede repetir este proceso visitando la página de seguridad del dispositivo; para ello, vaya a: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.

## <a name="security-certificate"></a>Certificado de seguridad

Si ves un "error de certificado" en el explorador, puedes corregirlo mediante la creación de una relación de confianza con el dispositivo.

Cada HoloLens genera un certificado autofirmado único para su conexión de SSL. De manera predeterminada, este certificado no es de confianza por parte del explorador web de tu equipo y puede que recibas un "error de certificado". Al descargar este certificado desde HoloLens (a través de USB o una red Wi-Fi en la que confíes) y confiar en el equipo, puedes conectarte a tu dispositivo de forma segura.
1. **Asegúrese de que se encuentre en una red segura (USB o una red Wi-Fi en la que confíe).**
2. Descargue el certificado de este dispositivo en la página "seguridad" en el portal de dispositivos.
   * Vaya a: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
3. Instale el certificado en el almacén "entidades de certificación raíz de confianza" en su equipo.
   * En el menú Windows, escriba: Manage Computer Certificates e inicie el applet.
   * Expanda la carpeta **entidad de certificación raíz de confianza** .
   * Haga clic en la carpeta **certificados** .
   * En el menú Acción, selecciona: Todas las tareas > Importar...
   * Completa el Asistente para importación de certificados con el archivo de certificado descargado desde Device Portal.
4. Reinicia el explorador.

## <a name="device-portal-pages"></a>Páginas de Device Portal

### <a name="home"></a>Inicio

![Página principal de Windows Device portal en Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Página principal de Windows Device portal en Microsoft HoloLens*

La sesión de Device Portal se inicia en la página principal. Accede a otras páginas desde la barra de navegación en el lado izquierdo de la página principal.

La barra de herramientas de la parte superior de la página proporciona acceso al estado usado frecuentemente y a las características.
* **En línea**: indica si el dispositivo está conectado a Wi-Fi.
* **Apagar**: apaga el dispositivo.
* **Reiniciar**: vuelve a iniciar el dispositivo.
* **Seguridad**: abre la página Seguridad del dispositivo.
* **Frío**: indica la temperatura del dispositivo.
* **CA**: indica si el dispositivo está enchufado y cargándose.
* **Ayuda**: abre la página de documentación de la interfaz REST.

En la página principal se muestra la siguiente información:
* **Estado del dispositivo:** supervisa el estado del dispositivo e informa de los errores críticos.
* **Información de Windows:** muestra el nombre de HoloLens y la versión de Windows instalada actualmente.
* La sección **Preferencias** contiene las siguientes opciones:
   * **IPD**: establece la distancia interpupilar (IPD), que es la distancia, en milímetros, entre el centro de las pupilas del usuario cuando mira al frente. La configuración surte efecto inmediatamente. El valor predeterminado se calculó automáticamente al configurar el dispositivo.
   * **Nombre del dispositivo**: asigna un nombre a HoloLens. Debes reiniciar el dispositivo después de cambiar este valor para que surta efecto. Después de hacer clic en **Guardar**, se le preguntará si desea reiniciar el dispositivo inmediatamente o reiniciarlo más tarde.
   * **Configuración de suspensión**: establece el período de tiempo de espera antes de que el dispositivo entre en el modo de suspensión cuando está conectado y cuando funciona con batería.

### <a name="3d-view"></a>Vista 3D

![página de vista 3D en Windows Device portal en Microsoft HoloLens](images/3dview-1000px.png)<br>
*Página de vista 3D en Windows Device portal en Microsoft HoloLens*

Usa la página Vista 3D para ver cómo HoloLens interpreta el entorno. Navega por la vista con el mouse:
* Rotate: clic con el botón izquierdo + mouse;
* Pan: clic con el botón derecho + mouse;
* Zoom: desplazamiento del mouse.
* **Opciones de seguimiento**
   * Active el seguimiento visual continuo mediante la comprobación del seguimiento visual de **fuerza**. 
   * **Pausar** detiene el seguimiento visual.
* **Opciones de vista**: establezca las opciones en la vista 3D:
  * **Tracking**: indica si el seguimiento visual está activo.
  * **Show floor**: muestra un plano de la planta a cuadros.
  * **Show frustum**: muestra el tronco de vista.
  * **Show stabilization plane**: muestra el plano que usa HoloLens para estabilizar el movimiento.
  * **Mostrar malla**: muestra la malla de asignación espacial que representa el entorno.
  * **Mostrar anclajes espaciales**: muestra los anclajes espaciales de la aplicación activa. Debe hacer clic en el botón actualizar para obtener y actualizar los delimitadores.
  * **Mostrar detalles**: muestra las posiciones de la mano, las cuaternas de rotación del encabezado y el vector de origen del dispositivo cuando cambian en tiempo real.
  * **Botón Pantalla completa**: muestra la vista 3D en modo de pantalla completa. Presiona ESC para salir de la vista de pantalla completa.
* **Reconstrucción de superficie**: haga clic o pulse en **Actualizar** para mostrar la malla de asignación espacial más reciente desde el dispositivo. Un recorrido completo puede tardar unos segundos en completarse. La malla no se actualiza automáticamente en la vista 3D y debe hacer clic manualmente en **Actualizar** para obtener la malla más reciente del dispositivo. Haga clic en **Guardar** para guardar la malla de asignación espacial actual como un archivo OBJ en su PC.
* **Delimitadores espaciales**: haga clic en actualizar para mostrar o actualizar los delimitadores espaciales de la aplicación activa.

### <a name="mixed-reality-capture"></a>Captura de realidad mixta

![página de captura de realidad mixta en Windows Device portal en Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Página de captura de realidad mixta en Windows Device portal en Microsoft HoloLens*

Usa la página Mixed Reality Capture (Captura de realidad mixta) para guardar flujos multimedia desde HoloLens.
* **Configuración**: controle los flujos multimedia que se capturan comprobando la siguiente configuración:
  * **Hologramas**: captura el contenido holográfica en el flujo de vídeo. Los hologramas se representan en mono y no estéreo.
  * **PV camera**: captura la secuencia de vídeo de la cámara de vídeo o fotos.
  * **Mic Audio**: captura el audio de la matriz del micrófono.
  * **App Audio**: captura el audio de la aplicación que está en ejecución actualmente.
  * **Representación de la cámara**: alinea la captura para que proviene de la perspectiva de la cámara de fotos o vídeos, si es [compatible con la aplicación en ejecución](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (solo HoloLens 2).
  * **Live preview quality**: selecciona la resolución de pantalla, la velocidad de fotogramas y la velocidad de streaming de la Vista previa dinámica.
* Pulse o haga clic en el botón **vista previa dinámica** para mostrar el flujo de captura. **Detener vista previa dinámica** detiene la secuencia de captura.
* Pulse o haga clic en **registrar** para iniciar la grabación de la secuencia de realidad mixta con la configuración especificada. **Detener grabación** finaliza la grabación y la guarda.
* Pulse o haga clic en **tomar foto** para tomar una imagen de la secuencia de captura.
* **Vídeos y fotos**: muestra una lista de las capturas de vídeos y fotos tomadas en el dispositivo.

> [!NOTE]
> Hay [limitaciones en el MRC simultáneo](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Si una aplicación intenta tener acceso a la cámara de fotos o vídeo mientras Windows Device portal está grabando un vídeo, la grabación de vídeo se detendrá.
>   * HoloLens 2 no dejará de grabar vídeo si la aplicación tiene acceso a la cámara de fotos o vídeos con el modo SharedReadOnly.
> * Si una aplicación usa activamente la cámara de fotos o vídeos, el portal de dispositivos de Windows puede tomar una foto o grabar un vídeo.
> * Streaming en vivo:
>   * HoloLens (1ª generación) impide que una aplicación tenga acceso a la cámara de fotos o vídeos mientras se transmite por streaming en vivo desde el portal de dispositivos de Windows.
>   * HoloLens (1ª generación) no podrá hacer streaming en vivo si una aplicación está usando activamente la cámara de fotos o vídeos.
>   * HoloLens 2 detiene automáticamente el streaming en vivo cuando una aplicación intenta acceder a la cámara de fotos o vídeos en modo ExclusiveControl.
>   * HoloLens 2 es capaz de iniciar una secuencia en directo mientras una aplicación usa activamente la cámara PV.

### <a name="performance-tracing"></a>Seguimiento de rendimiento

![página de seguimiento del rendimiento en Windows Device portal en Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Página de seguimiento del rendimiento en Windows Device portal en Microsoft HoloLens*

Capture los seguimientos de la [grabadora de rendimiento de Windows](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) desde HoloLens.
* **Available profiles**: selecciona el perfil de WPR en la lista desplegable y pulsa o haz clic en **Inicio** para iniciar el seguimiento.
* **Custom profiles**: haz clic o pulsa en **Examinar** para elegir un perfil de WPR desde tu equipo. Haz clic o pulsa en **Cargar e iniciar** para iniciar el seguimiento.

Para detener el seguimiento, haz clic en el vínculo de detención. Permanezca en esta página hasta que se complete la descarga del archivo de seguimiento.

Los archivos ETL se pueden abrir para realizar análisis en [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Processes

Página de ![procesos de Windows Device portal en Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Página procesos en Windows Device portal en Microsoft HoloLens*

Muestra detalles acerca de los procesos que se ejecutan actualmente. Esto incluye aplicaciones y procesos del sistema.

### <a name="system-performance"></a>Rendimiento del sistema

![página de rendimiento del sistema de Windows Device portal en Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Página rendimiento del sistema de Windows Device portal en Microsoft HoloLens*

Muestra gráficos en tiempo real de la información de diagnóstico del sistema, como el uso de energía, la velocidad de fotogramas y la carga de la CPU.

Estas son las métricas disponibles:
* **SoC power**: uso de energía instantánea de sistema en un chip (SoC), con una media superior a un minuto
* **Energía del sistema**: uso de energía instantánea del sistema, con una media superior a un minuto
* **Velocidad de fotogramas**: fotogramas por segundo, intervalos en blanco verticales perdidos por segundo y perdidos consecutivos
* **GPU**: uso del motor de la GPU, porcentaje del total disponible
* **CPU**: porcentaje del total disponible
* **E/S**: lecturas y escrituras
* **Red**: envíos y recepciones
* **Memoria**: total, en uso, confirmada, paginada y no paginada

### <a name="apps"></a>Aplicaciones

![página de aplicaciones de Windows Device portal en Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Página de aplicaciones de Windows Device portal en Microsoft HoloLens*

Administra las aplicaciones que están instaladas en HoloLens.
* **Aplicaciones instaladas**: quita e inicia aplicaciones.
* **Aplicaciones en ejecución**: enumera las aplicaciones que se ejecutan actualmente.
* **Instalar aplicación**: seleccione paquetes de aplicaciones para la instalación desde una carpeta de su equipo o red.
* **Dependencia**: agrega las dependencias de la aplicación que se va a instalar.
* **Implementar**: implemente la aplicación y las dependencias seleccionadas en HoloLens.

### <a name="app-crash-dumps"></a>Volcados de memoria de la aplicación

![página de volcados de memoria de la aplicación en Windows Device portal en Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Página de volcados de memoria de la aplicación en Windows Device portal en Microsoft HoloLens*

En esta página puedes recopilar los volcados de memoria de las aplicaciones transferidas localmente. Active la casilla **volcados de memoria habilitados** para cada aplicación para la que desea recopilar volcados de memoria. Vuelve a esta página para recopilar los volcados de memoria. Los archivos de volcado de memoria se pueden [abrir en Visual Studio para la depuración](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Explorador de archivos

![página del explorador de archivos de Windows Device portal en Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Página del explorador de archivos en Windows Device portal en Microsoft HoloLens*

Use el explorador de archivos para examinar, cargar y descargar archivos. Puede trabajar con archivos en la carpeta documentos, en la carpeta imágenes y en las carpetas de almacenamiento local para las aplicaciones que implementó desde Visual Studio o desde el portal de dispositivos.

### <a name="kiosk-mode"></a>Pantalla completa

>[!NOTE]
>El modo de quiosco solo está disponible con [Microsoft HoloLens Commercial Suite](commercial-features.md).

Consulte el artículo [configuración de HoloLens en modo de pantalla completa](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) en el centro de profesionales de TI de Windows para obtener instrucciones actualizadas sobre cómo habilitar el modo de quiosco a través del portal de dispositivos de Windows.

### <a name="logging"></a>Registro

![página de registro en Windows Device portal en Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Página registro en Windows Device portal en Microsoft HoloLens*

Administra el seguimiento de eventos en tiempo real para Windows (ETW) en HoloLens.

Active **ocultar proveedores** para mostrar solo la lista de **eventos** .
* **Registered providers**: selecciona el proveedor ETW y el nivel de seguimiento. El nivel de seguimiento es uno de estos valores:
   1. Terminación o salida anómala
   2. Errores graves
   3. Warnings
   4. Advertencias sin errores

Haz clic o pulsa en **Activar** para iniciar el seguimiento. El proveedor se agrega a la lista desplegable de **Proveedores habilitados**.
* **Proveedores personalizados**: selecciona un proveedor ETW personalizado y el nivel de seguimiento. Identifica el proveedor por su GUID. No incluyas corchetes en el GUID.
* **Proveedores habilitados**: enumera los proveedores habilitados. Selecciona un proveedor de la lista desplegable y haz clic o pulsa en **Desactivar** para detener el seguimiento. Haz clic o pulsa en **Detener todo** para suspender todos los seguimientos.
* **Providers history**: muestra los proveedores ETW que estaban habilitados durante la sesión actual. Haz clic o pulsa en **Activar** para activar un proveedor deshabilitado. Haz clic o pulsa en **Borrar** para borrar el historial.
* **Eventos**: enumera los eventos ETW de los proveedores seleccionados en formato de tabla. Esta tabla se actualiza en tiempo real. Debajo de la tabla, haga clic en el botón **Borrar** para eliminar todos los eventos ETW de la tabla. Esta acción no deshabilita ningún proveedor. Puedes hacer clic en **Guardar en archivo** para exportar los eventos ETW recopilados actualmente en un archivo CSV de forma local.
* **Filtros**: le permite filtrar los eventos ETW recopilados por el identificador, la palabra clave, el nivel, el nombre del proveedor, el nombre de la tarea o el texto. Puede combinar varios criterios juntos:
   1. En el caso de los criterios que se aplican a la misma propiedad, los eventos pueden cumplir uno de estos criterios.
   2. Para los criterios que se aplican a diferentes eventos de propiedad, debe cumplir todos los criterios.

Por ejemplo, puede especificar los criterios *(el nombre de tarea contiene ' foo ' o ' bar ') y (el texto contiene ' error ' o ' Warning ')*

### <a name="simulation"></a>Simulation

![página de simulación en Windows Device portal en Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Página de simulación en Windows Device portal en Microsoft HoloLens*

Te permite grabar y reproducir datos de entrada para las pruebas.
* **Capture room**: se usa para descargar un archivo de espacio simulado que contiene la malla espacial de asignación del entorno del usuario. Asigne un nombre a la sala y haga clic en **capturar** para guardar los datos como un archivo. XEF en su PC. Puedes cargar este archivo de espacio en el emulador HoloLens.
* **Grabación**: Compruebe las secuencias para grabar, asigne un nombre a la grabación y pulse o haga clic en **registrar** para iniciar la recodificación. Realice acciones con HoloLens y, a continuación, haga clic en **detener** para guardar los datos como un archivo. XEF en su PC. Este archivo se puede cargar en el dispositivo o emulador HoloLens.
* **Reproducción**: haga clic o pulse en **cargar grabación** para seleccionar un archivo de XEF desde su equipo y enviar los datos a HoloLens.
* **Modo de control**: seleccione el **valor predeterminado** o **simulación** en la lista desplegable y haga clic o pulse en el botón **establecer** para seleccionar el modo en HoloLens. Si eliges "Simulación", se deshabilitan los sensores reales de HoloLens y se usan los datos simulados cargados en su lugar. Si cambias a "Simulación", HoloLens no responderá al usuario real hasta que vuelva al "Valor predeterminado".

### <a name="networking"></a>Funciones de red de

![página redes de Windows Device portal en Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Página de redes en Windows Device portal en Microsoft HoloLens*

Administra conexiones Wi-Fi en HoloLens.
* **Adaptadores de WiFi**: Seleccione un adaptador y un perfil de Wi-Fi mediante los controles desplegables. Pulse o haga clic en **conectar** para usar el adaptador seleccionado.
* **Redes disponibles**: enumera las redes Wi-Fi a las que se puede conectar HoloLens. Pulse o haga clic en **Actualizar** para actualizar la lista.
* **Configuración de IP**: muestra la dirección IP y otros detalles de la conexión de red.

### <a name="virtual-input"></a>Entrada virtual

![página de entrada virtual en Windows Device portal en Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Página de entrada virtual en Windows Device portal en Microsoft HoloLens*

Envía la entrada de teclado desde la máquina remota a HoloLens.

Pulse o haga clic en la región en **teclado virtual** para habilitar el envío de pulsaciones de teclas a HoloLens. Escriba en el cuadro de **texto de texto de entrada** y haga clic o pulse en **Enviar** para enviar las pulsaciones de tecla a la aplicación activa.

## <a name="device-portal-rest-apis"></a>API de REST del portal de dispositivos

Todo lo que se encuentra en el portal de dispositivos se basa en las [API de REST](device-portal-api-reference.md) que puede usar opcionalmente para tener acceso a los datos y controlar el dispositivo mediante programación.
