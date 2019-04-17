---
title: Uso de la Windows Device Portal
description: El Windows Device Portal para HoloLens le permite configurar y administrar el dispositivo de forma remota a través de Wi-Fi o USB. Device Portal es un servidor web en el dispositivo HoloLens al que puedes conectarte desde un navegador web del equipo. El Portal de dispositivos incluye muchas herramientas que le ayudarán a administrar el HoloLens y la depuración y optimice sus aplicaciones.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal, HoloLens
ms.openlocfilehash: 8b9935d6b64abfd22e2e856e0142c953a6366008
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600967"
---
# <a name="using-the-windows-device-portal"></a>Uso de la Windows Device Portal

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

El Windows Device Portal para HoloLens le permite configurar y administrar el dispositivo de forma remota a través de Wi-Fi o USB. Device Portal es un servidor web en el dispositivo HoloLens al que puedes conectarte desde un navegador web del equipo. El Portal de dispositivos incluye muchas herramientas que le ayudarán a administrar el HoloLens y la depuración y optimice sus aplicaciones.

Esta documentación trata específicamente el Windows Device Portal para HoloLens. Para usar el portal de dispositivos de Windows para escritorio (incluidos para Windows Mixed Reality), consulte [información general de Windows Device Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configuración de HoloLens para utilizar Windows Device Portal

1. Enciende HoloLens y colócalo en el dispositivo.
2. Realiza el gesto [nástico](gestures.md#bloom) para iniciar el menú principal.
3. Mire el **configuración** icono y llevar a cabo la [pulsar en el aire](gestures.md#air-tap) gesto. Realizar una derivación de aire segundo para colocar la aplicación en su entorno. La aplicación Configuración se iniciará una vez la hayas colocado.
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilita el **Modo de desarrollador**.
7. [Desplácese hacia abajo](gestures.md#composite-gestures) y habilitar **Device Portal**.
8. Si está configurando Windows Device Portal para poder implementar las aplicaciones a través de USB o Wi-Fi para este HoloLens, haga clic en **par** a [generar un PIN emparejamiento](using-visual-studio.md#pairing-your-device-hololens). Deje la configuración de aplicación en el menú emergente PIN hasta que escriba el PIN en Visual Studio durante la primera implementación.

   ![Habilite el modo de desarrollador en la aplicación de configuración para Windows Holographic](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Conectarse a través de Wi-Fi

1. [Conectar su HoloLens con Wi-Fi](connecting-to-wi-fi-on-hololens.md).
2. Buscar la dirección IP de su dispositivo.
   * Buscar la dirección IP del dispositivo en **configuración > red e Internet > Wi-Fi > Opciones avanzadas**.
3. Desde un explorador web en su equipo, vaya a https://<YOUR_HOLOLENS_IP_ADDRESS>
   * El explorador mostrará el mensaje siguiente: "Hay un problema con el certificado de seguridad del sitio Web". Esto ocurre porque el certificado emitido en Device Portal es un certificado de prueba. Puedes ignorar este error de certificado por ahora y continuar.

## <a name="connecting-over-usb"></a>Conectarse a través de USB

1. [Instalar las herramientas de](install-the-tools.md) para asegurarse de que tiene Visual Studio Update 1 con las herramientas de desarrollo de Windows 10 instaladas en su equipo. Esto permite la conectividad USB.
2. Conecta HoloLens en el equipo con un cable micro-USB.
3. Desde un explorador web de tu equipo, ve a http://127.0.0.1:10080.

## <a name="connecting-to-an-emulator"></a>Conectarse a un emulador

También puedes usar Device Portal con el emulador. Para conectarse al Portal de dispositivo, use el [barra de herramientas](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator). Haz clic en este icono: ![Icono de dispositivo Portal abierta](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra el Windows Device Portal para el sistema operativo de HoloLens en el emulador.

## <a name="creating-a-username-and-password"></a>Creación de un nombre de usuario y contraseña

![Configurar el acceso a Windows Device Portal](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurar el acceso a Windows Device Portal*

La primera vez que te conectes a Device Portal en HoloLens, debes crear un nombre de usuario y una contraseña.
1. En un explorador web de tu equipo, escribe la dirección IP de HoloLens. Se abrirá la página de acceso Configuración.
2. Haga clic o pulse **solicitud de pin** y examine la presentación de HoloLens para obtener el código PIN generado.
3. Escriba el PIN en el **PIN mostrado en el dispositivo** cuadro de texto.
4. Escribe el nombre de usuario que usarás para conectarte a Device Portal. No es necesario que sea un nombre de cuenta de Microsoft (MSA) ni un nombre de dominio.
5. Escribe una contraseña y confírmala. La contraseña debe tener al menos siete caracteres de longitud. No es necesario que sea una MSA ni una contraseña de dominio.
6. Haga clic en **par** para conectarse a Windows Device Portal en el HoloLens.

Si desea cambiar este nombre de usuario o la contraseña en cualquier momento, puede repetir este proceso, visite la página seguridad del dispositivo haciendo clic en el **seguridad** vínculo a lo largo de la parte superior derecha, o al ir a: https://<YOUR_HOLOLENS_IP_ DIRECCIÓN > / devicesecurity.htm.

## <a name="security-certificate"></a>Certificado de seguridad

Si ves un "error de certificado" en el explorador, puedes corregirlo mediante la creación de una relación de confianza con el dispositivo.

Cada HoloLens genera un certificado autofirmado único para su conexión de SSL. De manera predeterminada, este certificado no es de confianza por parte del explorador web de tu equipo y puede que recibas un "error de certificado". Al descargar este certificado desde HoloLens (a través de USB o una red Wi-Fi en la que confíes) y confiar en el equipo, puedes conectarte a tu dispositivo de forma segura.
1. **Asegúrese de que se encuentra en una red segura (USB o una red Wi-Fi que confía).**
2. Descargar certificado del dispositivo desde la página de "Seguridad" en el Portal del dispositivo.
   * Haga clic en el **seguridad** un vínculo desde la lista superior derecha de los iconos o desplácese a: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicesecurity.htm
3. Instale el certificado en el "confianza entidades de certificación raíz" se almacena en su PC.
   * En el menú de Windows, escriba: Administrar certificados de equipo e inicie el applet.
   * Expanda el **entidad de certificación raíz de confianza** carpeta.
   * Haga clic en el **certificados** carpeta.
   * En el menú Acción, seleccione: Todas las tareas > Importar...
   * Completa el Asistente para importación de certificados con el archivo de certificado descargado desde Device Portal.
4. Reinicia el explorador.

## <a name="device-portal-pages"></a>Páginas de Device Portal

### <a name="home"></a>Inicio

![Página principal de Windows Device Portal Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Página principal de Windows Device Portal Microsoft HoloLens*

La sesión de Device Portal se inicia en la página principal. Accede a otras páginas desde la barra de navegación en el lado izquierdo de la página principal.

La barra de herramientas de la parte superior de la página proporciona acceso al estado usado frecuentemente y a las características.
* **En línea**: Indica si el dispositivo está conectado a Wi-Fi.
* **Shutdown**: Desactiva el dispositivo.
* **Restart**: Los ciclos de energía en el dispositivo.
* **Seguridad**: Abre la página seguridad del dispositivo.
* **Genial**: Indica la temperatura del dispositivo.
* **A/C**: Indica si el dispositivo está conectado y de carga.
* **Ayudar a**: Se abre la página de documentación de la interfaz REST.

En la página principal se muestra la siguiente información:
* **Estado del dispositivo:** supervisa el estado del dispositivo e informa de errores críticos.
* **Información de Windows:** muestra el nombre de la HoloLens y la versión actualmente instalada de Windows.
* La sección **Preferencias** contiene las siguientes configuraciones:
   * **IPD**: Establece la distancia interpupillary (IPD), que es la distancia, en milímetros, entre el centro de los alumnos del usuario al buscar recta. La configuración surte efecto inmediatamente. El valor predeterminado se calculó automáticamente al configurar el dispositivo.
   * **Nombre de dispositivo**: Asigne un nombre a la HoloLens. Debes reiniciar el dispositivo después de cambiar este valor para que surta efecto. Después de hacer clic **guardar**, un cuadro de diálogo le preguntará si desea reiniciar el dispositivo inmediatamente o reiniciar más tarde.
   * **Configuración de suspensión**: Establece la longitud de tiempo de espera antes de que el dispositivo entra en suspensión cuando está conectado y si se encuentra en la batería.

### <a name="3d-view"></a>Vista 3D

![Página de vista 3D en Windows Device Portal en Microsoft HoloLens](images/3dview-1000px.png)<br>
*Página de vista 3D en Windows Device Portal en Microsoft HoloLens*

Usa la página Vista 3D para ver cómo HoloLens interpreta el entorno. Navega por la vista con el mouse:
* Girar: haga clic y mueva el mouse;
* Movimiento panorámico: derecha haga clic en + mouse;
* Zoom: el desplazamiento del mouse.
* **Opciones de seguimiento**
   * Activar el seguimiento visual continua mediante la comprobación de **seguimiento visual de Force**. 
   * **Pausar** detiene el seguimiento visual.
* **Ver las opciones de**: Establecer las opciones de la vista 3D:
  * **Seguimiento**: Indica si el seguimiento visual está activa.
  * **Mostrar floor**: Muestra un plano a cuadros de límite inferior.
  * **Mostrar frustum**: Muestra el frustum de vista.
  * **Mostrar el plano de estabilización**: Muestra el plano de HoloLens se usa para la estabilización del movimiento.
  * **Mostrar malla**: Muestra la malla de asignación espacial que representa su entorno.
  * **Muestre los delimitadores espaciales**: Muestra los anclajes espaciales para la aplicación activa. Debe hacer clic en el botón Actualizar para obtener y actualizar los delimitadores.
  * **Mostrar detalles**: Muestra entrega posiciones, cuaterniones rotación principal y el vector de origen del dispositivo según cambian en tiempo real.
  * **Botón de pantalla completa**: Muestra la vista 3D en modo de pantalla completa. Presiona ESC para salir de la vista de pantalla completa.
* **Reconstrucción de superficie**: Haga clic o pulse **actualización** para mostrar la malla de última asignación espacial desde el dispositivo. Un recorrido completo puede tardar unos segundos en completarse. La malla no se actualiza automáticamente en la vista 3D, y debe hacer clic manualmente **actualizar** para obtener la malla más reciente desde el dispositivo. Haga clic en **guardar** para guardar la malla de asignación espacial actual como un archivo obj en su PC.
* **Delimitadores espaciales**: Haga clic en Actualizar para mostrar o actualizar los delimitadores espaciales para la aplicación activa.

### <a name="mixed-reality-capture"></a>Captura de realidad mixta

![Página capturar de realidad mixta en Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Página capturar de realidad mixta en Windows Device Portal en Microsoft HoloLens*

Use la [capturar de realidad mixta](mixed-reality-capture.md) página para guardar secuencias multimedia desde el HoloLens.
* **Configuración de**: Controlar las secuencias de multimedia que se capturan mediante la comprobación de las siguientes opciones:
  * **Hologramas**: Captura el contenido en la secuencia de vídeo holográfico. Los hologramas se representan en mono y no estéreo.
  * **Cámara PV**: Captura de la secuencia de vídeo desde la cámara de vídeo y fotos.
  * **MIC Audio**: Captura de audio de la matriz de micrófono.
  * **Aplicación Audio**: Captura de audio desde la aplicación que se está ejecutando.
  * **Calidad de vista previa de Live**: Seleccione la resolución de pantalla, la velocidad de fotogramas y la velocidad de transmisión por secuencias para la vista previa activa.
* Haga clic o pulse el **la vista previa activa** botón para mostrar el flujo de captura. **La vista previa activa Stop** detiene la secuencia de captura.
* Haga clic o pulse **registro** para iniciar la grabación de acciones de la secuencia de realidad mixta, mediante los valores especificados. **Detener la grabación** finaliza la grabación y lo guarda.
* Haga clic o pulse **toman fotografías** para tomar una imagen fija de la secuencia de captura.
* **Fotos y vídeos**: Muestra una lista de capturas de vídeo y fotos tomadas en el dispositivo.

Ten en cuenta que las aplicaciones de HoloLens no podrán capturar una foto o un vídeo MRC mientras grabas o haces streaming de una Vista previa dinámica des de Device Portal.

### <a name="performance-tracing"></a>Seguimiento del rendimiento

![Rendimiento de seguimiento de la página de Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Rendimiento de seguimiento de la página de Windows Device Portal en Microsoft HoloLens*

Capturar [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) seguimientos (WPR) desde su HoloLens.
* **Perfiles disponibles**: Seleccione el perfil WPR en la lista desplegable y haga clic o pulse **iniciar** para comenzar el seguimiento.
* **Perfiles personalizados**: Haga clic o pulse **examinar** para elegir un perfil WPR desde su PC. Haz clic o pulsa en **Cargar e iniciar** para iniciar el seguimiento.

Para detener el seguimiento, haz clic en el vínculo de detención. Permanezca en esta página hasta que el archivo de seguimiento completó la descarga.

Los archivos ETL se pueden abrir para realizar análisis en [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Procesos

![Página de procesos de Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Página de procesos de Windows Device Portal en Microsoft HoloLens*

Muestra detalles acerca de los procesos que se ejecutan actualmente. Esto incluye aplicaciones y procesos del sistema.

### <a name="system-performance"></a>Rendimiento del sistema

![Página de rendimiento del sistema en Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Página de rendimiento del sistema en Windows Device Portal en Microsoft HoloLens*

Muestra gráficos en tiempo real de la información de diagnóstico del sistema, como el uso de energía, la velocidad de fotogramas y la carga de la CPU.

Estas son las métricas disponibles:
* **SoC power**: Instantánea del sistema en chip energético, promediado por minuto
* **Alimentación del sistema**: Utilización de energía del sistema instantáneo, promediado por minuto
* **Velocidad de fotogramas**: Fotogramas por segundo, perdió VBlanks por segundo y consecutivos VBlanks perdidas
* **GPU**: Uso del motor de GPU, porcentaje del total disponible
* **CPU**: porcentaje del total disponible
* **I/O**: Lecturas y escrituras
* **Red**: Recibidos y enviados
* **Memoria**: Total, en uso, confirmado, paginada y no paginada

### <a name="apps"></a>Aplicaciones

![Página de aplicaciones de Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-apps-page-1000px.png)<br>
*Página de aplicaciones de Windows Device Portal en Microsoft HoloLens*

Administra las aplicaciones que están instaladas en el HoloLens.
* **Las aplicaciones instaladas**: Quitar e iniciar las aplicaciones.
* **Ejecutar aplicaciones**: Enumera las aplicaciones que se están ejecutando actualmente.
* **Instalar aplicación**: Seleccione los paquetes de aplicaciones para la instalación desde una carpeta en la red de equipos.
* **Dependencia**: Agregue las dependencias de la aplicación que se va a instalar.
* **Implementar**: Implemente la aplicación seleccionada y dependencias en el HoloLens.

### <a name="app-crash-dumps"></a>Volcados de sucesos de aplicación

![Página de volcados de aplicación de Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Página de volcados de aplicación de Windows Device Portal en Microsoft HoloLens*

En esta página puedes recopilar los volcados de memoria de las aplicaciones transferidas localmente. Compruebe el **volcados habilitados bloqueos** casilla de verificación para cada aplicación para el que van a recopilar volcados de memoria. Vuelve a esta página para recopilar los volcados de memoria. Archivos de volcado de memoria pueden ser [abierta en Visual Studio para depurar](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Explorador de archivos

![Página del explorador de archivos en Windows Device Portal en Microsoft HoloLens](images/fileexplorer-1000px.png)<br>
*Página del explorador de archivos en Windows Device Portal en Microsoft HoloLens*

Utilice el Explorador de archivos para examinar, cargar y descargar archivos. Puede trabajar con archivos en la carpeta de documentos, la carpeta imágenes y en las carpetas de almacenamiento local para las aplicaciones que ha implementado desde Visual Studio o el Portal de dispositivo.

### <a name="kiosk-mode"></a>Pantalla completa

>[!NOTE]
>Modo de pantalla completa solo está disponible con la [Microsoft HoloLens Commercial Suite](commercial-features.md).

Compruebe el [configurar HoloLens en modo de quiosco](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) artículo de Windows IT Pro Center para obtener instrucciones sobre cómo habilitar el modo de pantalla completa a través de Windows Device Portal actualizadas.

### <a name="logging"></a>Registro

![Página de registro en Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-logging-page-1000px.png)<br>
*Página de registro en Windows Device Portal en Microsoft HoloLens*

Administra el seguimiento de eventos para Windows (ETW) en el HoloLens en tiempo real.

Comprobar **ocultar proveedores** para mostrar el **eventos** sólo la lista.
* **Proveedores registrados**: Seleccione el proveedor ETW y el nivel de seguimiento. El nivel de seguimiento es uno de estos valores:
   1. Terminación o salida anómala
   2. Errores graves
   3. Warnings
   4. Advertencias sin errores

Haz clic o pulsa en **Activar** para iniciar el seguimiento. El proveedor se agrega a la lista desplegable de **Proveedores habilitados**.
* **Proveedores personalizados**: Seleccione un proveedor ETW personalizado y el nivel de seguimiento. Identifica el proveedor por su GUID. No incluyas corchetes en el GUID.
* **Los proveedores habilitados**: Enumera los proveedores habilitados. Selecciona un proveedor de la lista desplegable y haz clic o pulsa en **Desactivar** para detener el seguimiento. Haz clic o pulsa en **Detener todo** para suspender todos los seguimientos.
* **Historial de los proveedores**: Muestra los proveedores de ETW que estaban habilitados durante la sesión actual. Haz clic o pulsa en **Activar** para activar un proveedor deshabilitado. Haz clic o pulsa en **Borrar** para borrar el historial.
* **Eventos**: Muestra los eventos ETW de los proveedores seleccionados en formato de tabla. Esta tabla se actualiza en tiempo real. Debajo de la tabla, haga clic en el **clara** botón para eliminar todos los eventos ETW de la tabla. Esta acción no deshabilita ningún proveedor. Puedes hacer clic en **Guardar en archivo** para exportar los eventos ETW recopilados actualmente en un archivo CSV de forma local.
* **Filtros**: Le permiten filtrar los eventos ETW recopilados por identificador, palabra clave, nivel, nombre del proveedor, nombre de la tarea o texto. Puede combinar varios criterios juntos:
   1. Para los criterios que se aplica a la misma propiedad - pueden satisfacer los eventos se muestran uno de estos criterios.
   2. Para los criterios de aplicación a otra propiedad - eventos deben cumplir todos los criterios

Por ejemplo, puede especificar los criterios *(nombre de tarea contiene 'Foo' o 'Bar') y (texto contiene 'error' o 'advertencia')*

### <a name="simulation"></a>Simulation

![Página de la simulación en Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-simulation-page-1000px.png)<br>
*Página de la simulación en Windows Device Portal en Microsoft HoloLens*

Te permite grabar y reproducir datos de entrada para las pruebas.
* **Capturar sala**: Se utiliza para descargar un archivo de sala simulado que contenga la malla de asignación espacial para el entorno del usuario. Nombre de la sala de reuniones y, a continuación, haga clic en **capturar** para guardar los datos como un archivo .xef en su PC. Puedes cargar este archivo de espacio en el emulador HoloLens.
* **Grabación**: Compruebe las secuencias para registrar, asigne el nombre de la grabación y haga clic o pulse **registro** para iniciar la grabación. Realizar acciones con su HoloLens y, a continuación, haga clic en **detener** para guardar los datos como un archivo .xef en su PC. Este archivo se puede cargar en el dispositivo o emulador HoloLens.
* **Reproducción**: Haga clic o pulse **carga grabación** para seleccionar un archivo xef de su PC y enviar los datos a la HoloLens.
* **Modo de control**: Seleccione **predeterminado** o **simulación** desde la lista desplegable y haga clic o pulse el **establecer** botón para seleccionar el modo en el HoloLens. Si eliges "Simulación", se deshabilitan los sensores reales de HoloLens y se usan los datos simulados cargados en su lugar. Si cambias a "Simulación", HoloLens no responderá al usuario real hasta que vuelva al "Valor predeterminado".

### <a name="networking"></a>Funciones de red

![Página de redes en Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-networking-page-1000px.png)<br>
*Página de redes en Windows Device Portal en Microsoft HoloLens*

Administra las conexiones Wi-Fi en el HoloLens.
* **Adaptadores de red Wi-Fi**: Seleccione un adaptador Wi-Fi y el perfil mediante el uso de los controles de lista desplegable. Haga clic o pulse **Connect** para usar el adaptador seleccionado.
* **Las redes disponibles**: Muestra las redes Wi-Fi que pueden conectarse el HoloLens. Haga clic o pulse **actualizar** para actualizar la lista.
* **Configuración de IP**: Muestra la dirección IP y otros detalles de la conexión de red.

### <a name="virtual-input"></a>Entrada virtual

![Página de entrada virtual en Windows Device Portal en Microsoft HoloLens](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Página de entrada virtual en Windows Device Portal en Microsoft HoloLens*

Envía la entrada de teclado desde la máquina remota a HoloLens.

Haga clic o pulse en la región en **teclado Virtual** para habilitar el envío pulsaciones de tecla a la HoloLens. Escriba el **texto de entrada** cuadro de texto y haga clic o pulse **enviar** para enviar las pulsaciones de tecla a la aplicación activa.

## <a name="device-portal-rest-apis"></a>La API de REST de Portal de dispositivo

Todo en el portal de dispositivo se crea en la parte superior de [API de REST](device-portal-api-reference.md) que también puede usar para acceder a los datos y controlar el dispositivo mediante programación.
