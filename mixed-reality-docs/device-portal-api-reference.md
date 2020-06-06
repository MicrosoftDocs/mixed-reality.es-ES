---
title: Referencia de la API del Portal de dispositivos
description: Referencia de API para Windows Device portal en HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portal de dispositivos de Windows, API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451330"
---
# <a name="device-portal-api-reference"></a>Referencia de la API del Portal de dispositivos

Todo lo que se encuentra en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para tener acceso a los datos y controlar el dispositivo mediante programación.

## <a name="app-deloyment"></a>Implementación de aplicación

**/API/App/packagemanager/Package (eliminar)**

Desinstala una aplicación

Parámetros
* paquete: nombre de archivo del paquete que se va a desinstalar.

**/API/App/packagemanager/Package (POST)**

Instala una aplicación

Parámetros
* paquete: nombre de archivo del paquete que se va a instalar.

Carga
* cuerpo http compatible con varias partes

**/API/App/packagemanager/packages (GET)**

Recupera la lista de aplicaciones instaladas en el sistema con detalles

Devolver datos
* Lista de paquetes instalados con detalles

**/API/App/packagemanager/State (GET)**

Obtiene el estado de la instalación de la aplicación en curso

## <a name="dump-collection"></a>Colección de volcados de memoria

**/API/Debug/dump/usermode/CrashControl (eliminar)**

Deshabilita la recopilación de volcados de memoria para una aplicación transferida localmente

Parámetros
* packageFullname: nombre del paquete

**/API/Debug/dump/usermode/CrashControl (GET)**

Obtiene la configuración de la colección de volcados de memoria de aplicaciones transferidas

Parámetros
* packageFullname: nombre del paquete

**/API/Debug/dump/usermode/CrashControl (POST)**

Habilita y establece la configuración de control de volcado para una aplicación transferida localmente

Parámetros
* packageFullname: nombre del paquete

**/API/Debug/dump/usermode/crashdump (eliminar)**

Elimina un volcado de memoria para una aplicación transferida localmente

Parámetros
* packageFullname: nombre del paquete
* fileName: nombre de archivo de volcado

**/API/Debug/dump/usermode/crashdump (GET)**

Recupera un volcado de memoria para una aplicación transferida localmente

Parámetros
* packageFullname: nombre del paquete
* fileName: nombre de archivo de volcado

Devolver datos
* Archivo de volcado de memoria. Inspeccionar con WinDbg o Visual Studio

**/API/Debug/dump/usermode/dumps (GET)**

Devuelve la lista de todos los volcados de memoria de las aplicaciones transferidas localmente

Devolver datos
* Lista de volcados de memoria por aplicación cargada

## <a name="etw"></a>ETW

**/API/ETW/Providers (GET)**

Enumera los proveedores registrados

Devolver datos
* Lista de proveedores, nombre descriptivo y GUID

**/API/ETW/Session/Realtime (GET/WebSocket)**

Crea una sesión ETW en tiempo real; se administra a través de un WebSocket.

Devolver datos
* Eventos ETW de los proveedores habilitados

## <a name="holographic-os"></a>SO Holographic

**/API/Holographic/os/ETW/customproviders (GET)**

Devuelve una lista de proveedores ETW específicos de HoloLens que no están registrados en el sistema.

**/API/Holographic/os/Services (GET)**

Devuelve los Estados de todos los servicios que se están ejecutando.

**/API/Holographic/os/Settings/IPD (GET)**

Obtiene el IPD almacenado (distancia interpupillary) en milímetros.

**/API/Holographic/os/Settings/IPD (POST)**

Establece la configuración de IPD

Parámetros
* IPD: nuevo valor de IPD que se establecerá en milímetros

**/API/Holographic/os/webmanagement/Settings/https (GET)**

Obtener los requisitos de HTTPS para Device Portal

**/API/Holographic/os/webmanagement/Settings/https (POST)**

Establece los requisitos de HTTPS para el portal de dispositivos

Parámetros
* requerido: sí, no o predeterminado

## <a name="holographic-perception"></a>Percepción holográfica

**/API/Holographic/Perception/Client (GET/WebSocket)**

Acepta actualizaciones de WebSocket y ejecuta un cliente de percepción que envía actualizaciones a 30 fps.

Parámetros
* clientmode: "Active" fuerza el modo de seguimiento visual cuando no se puede establecer de forma pasiva

## <a name="holographic-thermal"></a>Temperatura térmica holográfica

**/API/Holographic/Thermal/Stage (GET)**

Obtener la fase térmica del dispositivo (0 normal, 1 cálido, 2 crítico)

## <a name="perception-simulation-control"></a>Control de simulación de percepción

**/API/Holographic/Simulation/control/MODE (GET)**

Obtención del modo de simulación

**/API/Holographic/Simulation/control/MODE (POST)**

Establecer el modo de simulación

Parámetros
* modo de simulación: predeterminado, simulación, remoto, heredado

**/API/Holographic/Simulation/control/Stream (eliminar)**

Elimine un flujo de control.

**/API/Holographic/Simulation/control/Stream (GET/WebSocket)**

Abra una conexión de socket web para un flujo de control.

**/API/Holographic/Simulation/control/Stream (POST)**

Cree un flujo de control (se requiere prioridad) o publique los datos en un flujo creado (streamId obligatorio). Se espera que los datos expuestos sean del tipo "application/octet-stream".

**/API/Holographic/Simulation/display/Stream (GET/WebSocket)**

Solicitar una secuencia de vídeo de simulación que contenga el contenido representado en la pantalla del sistema cuando esté en modo de ' simulación '.  Inicialmente, se enviará un encabezado de descriptor de formato simple, seguido de las texturas codificadas en H. 264, cada una precedida por un encabezado que indica el índice ocular y el tamaño de la textura.

## <a name="perception-simulation-playback"></a>Reproducción de la simulación de percepción

**/API/Holographic/Simulation/Playback/File (eliminar)**

Elimina una grabación.

Parámetros
* grabación: nombre de la grabación que se va a eliminar.

**/API/Holographic/Simulation/Playback/File (POST)**

Carga de una grabación.

**/API/Holographic/Simulation/Playback/files (GET)**

Obtener todas las grabaciones.

**/API/Holographic/Simulation/Playback/Session (GET)**

Obtiene el estado de reproducción actual de una grabación.

Parámetros
* grabación: nombre de la grabación.

**/API/Holographic/Simulation/Playback/Session/File (eliminar)**

Descargar una grabación.

Parámetros
* grabación: nombre de la grabación que se va a descargar.

**/API/Holographic/Simulation/Playback/Session/File (POST)**

Carga de una grabación.

Parámetros
* grabación: nombre de la grabación que se va a cargar.

**/API/Holographic/Simulation/Playback/Session/files (GET)**

Obtiene todas las grabaciones cargadas.

**/API/Holographic/Simulation/Playback/Session/PAUSE (POST)**

Pausar una grabación.

Parámetros
* grabación: nombre de la grabación.

**/API/Holographic/Simulation/Playback/Session/Play (POST)**

Reproducir una grabación.

Parámetros
* grabación: nombre de la grabación.

**/API/Holographic/Simulation/Playback/Session/STOP (POST)**

Detener una grabación.

Parámetros
* grabación: nombre de la grabación.

**/API/Holographic/Simulation/Playback/Session/Types (GET)**

Obtiene los tipos de datos en una grabación cargada.

Parámetros
* grabación: nombre de la grabación.

## <a name="perception-simulation-recording"></a>Grabación de simulación de percepción

**/API/Holographic/Simulation/Recording/Start (POST)**

Iniciar una grabación. Solo puede haber una grabación activa al mismo tiempo. Debe establecerse una de las clases Head, Hand, spatialMapping o Environment.

Parámetros
* Head: establézcalo en 1 para registrar los datos principales.
* manos: establézcalo en 1 para registrar los datos de la mano.
* spatialMapping: establézcalo en 1 para registrar la asignación espacial.
* entorno: establézcalo en 1 para registrar los datos del entorno.
* Nombre: nombre de la grabación.
* singleSpatialMappingFrame: establézcalo en 1 para registrar solo un marco de asignación espacial.

**/API/Holographic/Simulation/Recording/status (GET)**

Obtiene el estado de grabación.

**/API/Holographic/Simulation/Recording/STOP (GET)**

Detener la grabación actual. La grabación se devolverá como un archivo.

## <a name="mixed-reality-capture"></a>Captura de realidad mixta

**/API/Holographic/MRC/File (GET)**

Descarga un archivo de realidad mixta desde el dispositivo. Use OP = parámetro de consulta de transmisión por secuencias.

Parámetros
* Filename: nombre, hex64 codificado, del archivo de vídeo que se va a obtener
* OP: Stream

**/API/Holographic/MRC/File (eliminar)**

Elimina una grabación de realidad mixta del dispositivo.

Parámetros
* Filename: nombre, hex64 codificado, del archivo que se va a eliminar.

**/API/Holographic/MRC/files (GET)**

Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo

**/API/Holographic/MRC/Photo (POST)**

Toma una fotografía de realidad mixta y crea un archivo en el dispositivo.

Parámetros
* hololens: Capture hologramas: true o false (el valor predeterminado es false)
* PV: capturar la cámara PV: true o false (el valor predeterminado es false)
* RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).

**/API/Holographic/MRC/Settings (GET)**

Obtiene la configuración de captura de realidad mixta predeterminada

**/API/Holographic/MRC/Settings (POST)**

Establece la configuración de captura de realidad mixta predeterminada.  Algunos de estos valores se aplican a la captura de vídeo y fotos de MRC del sistema.

**/API/Holographic/MRC/status (GET)**

Obtiene el estado de la captura de realidad mixta en el portal de dispositivos de Windows.

***Respuesta***

La respuesta contiene una propiedad JSON que indica si el portal de dispositivos de Windows está grabando vídeo o no.

``` javascript
{"IsRecording" : boolean}
```

**/API/Holographic/MRC/Thumbnail (GET)**

Obtiene la imagen en miniatura del archivo especificado.

Parámetros
* Filename: nombre, hex64 codificado, del archivo para el que se solicita la miniatura

**/API/Holographic/MRC/video/control/Start (POST)**

Inicia una grabación de realidad mixta

Parámetros
* hololens: Capture hologramas: true o false (el valor predeterminado es false)
* PV: capturar la cámara PV: true o false (el valor predeterminado es false)
* MIC: Capture Microphone: true o false (el valor predeterminado es false)
* bucle invertido: captura de audio de la aplicación: true o false (el valor predeterminado es false)
* RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).
* Vstab: (solo HoloLens 2) habilitar estabilización de vídeo: true o false (el valor predeterminado es true)
* vstabbuffer: (solo HoloLens 2) latencia de búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)

**/API/Holographic/MRC/video/control/STOP (POST)**

Detiene la grabación de realidad mixta actual

## <a name="mixed-reality-streaming"></a>Streaming de realidad mixta

HoloLens admite la vista previa dinámica de la realidad mixta a través de la descarga fragmentada de un MP4 fragmentado.

Los flujos de realidad mixta comparten el mismo conjunto de parámetros para controlar lo que se captura:
* hololens: capturar hologramas: true o false
* PV: capturar la cámara PV: true o false
* MIC: capturar micrófono: true o false
* bucle invertido: captura de audio de la aplicación: true o false

Si no se especifica ninguno de estos: los hologramas, la cámara de foto/vídeo y el audio de la aplicación se capturarán<br>
Si se especifica any: los parámetros no especificados tendrán como valor predeterminado False.

Parámetros opcionales (solo HoloLens 2)
* RenderFromCamera: representación de la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).
* Vstab: habilitar estabilización de vídeo: true o false (el valor predeterminado es false)
* vstabbuffer: latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)

**/API/Holographic/Stream/Live.MP4 (GET)**

1280x720p 30 fps 5Mbit.

**/API/Holographic/Stream/live_high. MP4 (GET)**

1280x720p 30 fps 5Mbit.

**/API/Holographic/Stream/live_med. MP4 (GET)**

Una secuencia de 854x480p 30 fps 2.5 Mbit.

**/API/Holographic/Stream/live_low. MP4 (GET)**

Una secuencia de 428x240p 15fps 0,6 Mbit.

## <a name="networking"></a>Redes

**/API/Networking/ipconfig (GET)**

Obtiene la configuración de IP actual.

## <a name="os-information"></a>Información del sistema operativo

**/API/os/info (GET)**

Obtiene información del sistema operativo

**/API/os/MachineName (GET)**

Obtiene el nombre de la máquina.

**/API/os/MachineName (POST)**

Establece el nombre de la máquina

Parámetros
* Nombre: nuevo nombre del equipo, hex64 codificado, para establecer en

## <a name="performance-data"></a>Datos de rendimiento

**/API/ResourceManager/processes (GET)**

Devuelve la lista de procesos en ejecución con detalles

Devolver datos
* JSON con la lista de procesos y detalles de cada proceso

**/API/ResourceManager/systemperf (GET)**

Devuelve las estadísticas de rendimiento del sistema (e/s de lectura/escritura, estadísticas de memoria, etc.).

Devolver datos
* JSON con información del sistema: CPU, GPU, memoria, red, e/s

## <a name="power"></a>Potencia

**/API/Power/Battery (GET)**

Obtiene el estado actual de la batería

**/API/Power/State (GET)**

Comprueba si el sistema está en un estado de baja energía.

## <a name="remote-control"></a>Control remoto

**/API/control/Restart (POST)**

Reinicia el dispositivo de destino

**/API/control/Shutdown (POST)**

Apaga el dispositivo de destino

## <a name="task-manager"></a>Administrador de tareas

**/API/TaskManager/App (eliminar)**

Detiene una aplicación moderna

Parámetros
* paquete: nombre completo del paquete de la aplicación, hex64 codificado
* forcestop: forzar la detención de todos los procesos (= sí)

**/API/TaskManager/App (POST)**

Inicia una aplicación moderna

Parámetros
* AppID: PRAID de la aplicación que se va a iniciar, hex64 codificada
* paquete: nombre completo del paquete de la aplicación, hex64 codificado

## <a name="wifi-management"></a>Administración de WiFi

**/API/WiFi/interfaces (GET)**

Enumera las interfaces de red inalámbrica

Devolver datos
* Lista de interfaces inalámbricas con detalles (GUID, descripción, etc.)

**/API/WiFi/Network (eliminar)**

Elimina un perfil asociado a una red en una interfaz especificada.

Parámetros
* interfaz: GUID de la interfaz de red
* Perfil: nombre del perfil

**/API/WiFi/Networks (GET)**

Enumera las redes inalámbricas de la interfaz de red especificada

Parámetros
* interfaz: GUID de la interfaz de red

Devolver datos
* Lista de redes inalámbricas encontradas en la interfaz de red con detalles

**/API/WiFi/Network (POST)**

Conecta o desconecta una red de la interfaz especificada

Parámetros
* interfaz: GUID de la interfaz de red
* SSID: SSID, hex64 codificado, para conectarse
* OP: conectar o desconectar
* createprofile: sí o no
* clave: clave compartida, hex64 codificado

## <a name="windows-performance-recorder"></a>Grabadora de rendimiento de Windows

**/API/WPR/customtrace (POST)**

Carga un perfil de WPR e inicia el seguimiento con el perfil cargado.

Carga
* cuerpo http compatible con varias partes

Devolver datos
* Devuelve el estado de sesión WPR.

**/API/WPR/status (GET)**

Recupera el estado de la sesión de WPR

Devolver datos
* Estado de la sesión de WPR.

**/API/WPR/trace (GET)**

Detiene una sesión de seguimiento de WPR (rendimiento)

Devolver datos
* Devuelve el archivo ETL de seguimiento.

**/API/WPR/trace (POST)**

Inicia una sesión de seguimiento de WPR (rendimiento)

Parámetros
* Perfil: nombre del perfil. Los perfiles disponibles se almacenan en perfprofiles/profiles. JSON.

Devolver datos
* Al iniciar, devuelve el estado de la sesión de WPR.

## <a name="see-also"></a>Consulte también
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)
* [Referencia de API principal del portal de dispositivos (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
