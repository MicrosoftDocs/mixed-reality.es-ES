---
title: Referencia de la API del portal de dispositivos
description: Referencia de API para el Windows Device Portal en HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal, API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605372"
---
# <a name="device-portal-api-reference"></a>Referencia de la API del portal de dispositivos

Todo el contenido de la [Windows Device Portal](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para acceder a los datos y controlar el dispositivo mediante programación.

## <a name="app-deloyment"></a>Implementación de aplicación

**/API/App/PackageManager/Package (eliminar)**

Desinstala una aplicación

Parámetros
* paquete: Nombre de archivo del paquete que se puede desinstalar.

**/api/app/packagemanager/package (POST)**

Instala una aplicación

Parámetros
* paquete: Nombre de archivo del paquete de instalación.

carga
* cuerpo de http que cumplan varias partes

**/API/App/PackageManager/Packages (GET)**

Recupera la lista de las aplicaciones instaladas en el sistema, con detalles

Devolver datos
* Lista de paquetes instalados con detalles

**/api/app/packagemanager/state (GET)**

Obtiene el estado de en la instalación de la aplicación de progreso

## <a name="dump-collection"></a>Colección de volcados de memoria

**/api/debug/dump/usermode/crashcontrol (DELETE)**

Deshabilita el bloqueo recopilación del volcado de memoria para una aplicación de instalación de prueba

Parámetros
* packageFullname: nombre del paquete

**/api/debug/dump/usermode/crashcontrol (GET)**

Obtiene colección de volcados de configuración de aplicaciones con instalación de prueba

Parámetros
* packageFullname: nombre del paquete

**/api/debug/dump/usermode/crashcontrol (POST)**

Habilita y establece la configuración de control de volcado de memoria para una aplicación de instalación de prueba

Parámetros
* packageFullname: nombre del paquete

**/api/debug/dump/usermode/crashdump (DELETE)**

Elimina un volcado de memoria para una aplicación de instalación de prueba

Parámetros
* packageFullname: nombre del paquete
* nombre de archivo: nombre de archivo de volcado de memoria

**/api/debug/dump/usermode/crashdump (GET)**

Recupera un volcado de memoria para una aplicación de instalación de prueba

Parámetros
* packageFullname: nombre del paquete
* nombre de archivo: nombre de archivo de volcado de memoria

Devolver datos
* Archivo de volcado. Inspeccionar con WinDbg o en Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

Devuelve una lista de todos los volcados de memoria para las aplicaciones

Devolver datos
* Vuelca la lista de bloqueo por aplicación cargada de lado

## <a name="etw"></a>ETW

**/API/ETW/Providers (GET)**

Enumera los proveedores registrados

Devolver datos
* Lista de proveedores, el nombre descriptivo y el GUID

**/api/etw/session/realtime (GET/WebSocket)**

Crea una sesión ETW en tiempo real; se administran a través de un websocket.

Devolver datos
* Eventos ETW de los proveedores habilitados

## <a name="holographic-os"></a>SO Holographic

**/api/holographic/os/etw/customproviders (GET)**

Devuelve una lista de proveedores ETW específicos HoloLens que no están registrados con el sistema

**/api/holographic/os/services (GET)**

Devuelve los Estados de todos los servicios en ejecución.

**/api/holographic/os/settings/ipd (GET)**

Obtiene la IPD almacenada (distancia Interpupillary) en milímetros

**/api/holographic/os/settings/ipd (POST)**

Establece la IPD

Parámetros
* IPD: Nuevo valor IPD debe establecerse en milímetros

**/api/holographic/os/webmanagement/settings/https (GET)**

Obtener los requisitos de HTTPS para Device Portal

**/api/holographic/os/webmanagement/settings/https (POST)**

Establece los requisitos de HTTPS para el Portal de dispositivo

Parámetros
* requerido: Sí, no o el valor predeterminado

## <a name="holographic-perception"></a>Percepción holográfica

**/API/holographic/Perception/Client (GET/WebSocket)**

Acepta las actualizaciones de websocket y ejecuta a un cliente de la percepción que envía actualizaciones a 30 fps.

Parámetros
* clientmode: "activo" modo de seguimiento visual de fuerza cuando no se puede establecer de forma pasiva

## <a name="holographic-thermal"></a>Térmico holográfica

**/API/holographic/Thermal/Stage (GET)**

Obtener la fase térmica del dispositivo (normal 0, 1 en caliente, 2 crítico)

## <a name="perception-simulation-control"></a>Control de la simulación de percepción

**/API/holographic/Simulation/control/Mode (GET)**

Obtener el modo de simulación

**/API/holographic/Simulation/control/Mode (POST)**

Establecer el modo de simulación

Parámetros
* modo: modo de simulación: de forma predeterminada, simulación, remoto, heredado

**/API/holographic/Simulation/control/Stream (eliminar)**

Eliminar un flujo de control.

**/API/holographic/Simulation/control/Stream (GET/WebSocket)**

Abra una conexión de socket web para un flujo de control.

**/API/holographic/Simulation/control/Stream (POST)**

Crear un flujo de control (prioridad es necesaria) o publicar datos en un flujo creado (streamId necesario). Datos enviados debe ser de tipo "application/octet-stream".

## <a name="perception-simulation-playback"></a>Reproducción de simulación de percepción

**/API/holographic/Simulation/Playback/File (eliminar)**

Eliminar una grabación.

Parámetros
* grabación: Nombre de la grabación para eliminar.

**/API/holographic/Simulation/Playback/File (POST)**

Cargue una grabación.

**/API/holographic/Simulation/Playback/Files (GET)**

Obtener todas las grabaciones.

**/API/holographic/Simulation/Playback/Session (GET)**

Obtener el estado actual de la reproducción de una grabación.

Parámetros
* grabación: Nombre de la grabación.

**/API/holographic/Simulation/Playback/Session/File (eliminar)**

Descargar una grabación.

Parámetros
* grabación: Nombre de la grabación para descargar.

**/API/holographic/Simulation/Playback/Session/File (POST)**

Cargar una grabación.

Parámetros
* grabación: Nombre de la grabación para cargar.

**/API/holographic/Simulation/Playback/Session/Files (GET)**

Obtener grabaciones cargadas.

**/API/holographic/Simulation/Playback/Session/Pause (POST)**

Pausar una grabación.

Parámetros
* grabación: Nombre de la grabación.

**/API/holographic/Simulation/Playback/Session/Play (POST)**

Reproducir una grabación.

Parámetros
* grabación: Nombre de la grabación.

**/API/holographic/Simulation/Playback/Session/Stop (POST)**

Detener la grabación.

Parámetros
* grabación: Nombre de la grabación.

**/API/holographic/Simulation/Playback/Session/Types (GET)**

Obtiene los tipos de datos en una grabación de carga.

Parámetros
* grabación: Nombre de la grabación.

## <a name="perception-simulation-recording"></a>Grabación de simulación de percepción

**/API/holographic/Simulation/Recording/Start (POST)**

Iniciar una grabación. Solo puede estar activa una grabación única a la vez. Debe establecerse un encabezado, manos, spatialMapping o entorno.

Parámetros
* principal: Establezca en 1 para datos de registro principal.
* práctico: Se establece en 1 para registrar los datos disponibles.
* spatialMapping: Se establece en 1 para registrar la asignación espacial.
* entorno: Se establece en 1 para registrar datos de entorno.
* nombre: Nombre de la grabación.
* singleSpatialMappingFrame: Se establece en 1 para registrar solo un marco de asignación espacial único.

**/API/holographic/Simulation/Recording/Status (GET)**

Obtener estado de la grabación.

**/API/holographic/Simulation/Recording/Stop (GET)**

Detener la grabación actual. Grabación se devolverá como un archivo.

## <a name="mixed-reality-capture"></a>Captura de realidad mixta

**/API/holographic/MRC/File (eliminar)**

Elimina una grabación desde el dispositivo de realidad mixta.

Parámetros
* nombre de archivo: El nombre, hex64 codificada del archivo para eliminar

**/API/holographic/MRC/Settings (GET)**

Obtiene el valor predeterminado la realidad mixta configuración de capture

**/API/holographic/MRC/File (GET)**

Descarga un archivo de realidad mixta desde el dispositivo. Op uso = parámetro de consulta de stream para streaming.

Parámetros
* nombre de archivo: El nombre, hex64 codificada del archivo de vídeo para obtener
* op : stream

**/API/holographic/MRC/Thumbnail (GET)**

Obtiene la imagen en miniatura para el archivo especificado.

Parámetros
* filename: El nombre, hex64 codificada del archivo para el que se solicita la miniatura

**/API/holographic/MRC/Status (GET)**

Obtiene el estado de la realidad mixta registran (está ejecutando, detenido)

**/API/holographic/MRC/Files (GET)**

Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo

**/API/holographic/MRC/Settings (POST)**

Establece el valor predeterminado la realidad mixta configuración de capture

**/api/holographic/mrc/video/control/start (POST)**

Se inicia una grabación de realidad mixta

Parámetros
* Holo: capturar hologramas: true o false
* PV: cámara captura PV: true o false
* MIC: captura de micrófono: true o false
* bucle invertido: capturar audio de la aplicación: true o false

**/api/holographic/mrc/video/control/stop (POST)**

Se detiene la actual mixto grabación realidad

**/API/holographic/MRC/Photo (POST)**

Toma una fotografía de realidad mixta y crea un archivo en el dispositivo

Parámetros
* Holo: capturar hologramas: true o false
* PV: cámara captura PV: true o false

Realidad mixta de transmisión por secuencias

**/api/holographic/stream/live.mp4 (GET)**

Inicia una descarga fragmentada de un archivo mp4 fragmentado

Parámetros
* Holo: capturar hologramas: true o false
* PV: cámara captura PV: true o false
* MIC: captura de micrófono: true o false
* bucle invertido: capturar audio de la aplicación: true o false

**/api/holographic/stream/live_high.mp4 (GET)**

Inicia una descarga fragmentada de un archivo mp4 fragmentado

Parámetros
* Holo: capturar hologramas: true o false
* PV: cámara captura PV: true o false
* MIC: captura de micrófono: true o false
* bucle invertido: capturar audio de la aplicación: true o false

**/api/holographic/stream/live_low.mp4 (GET)**

Inicia una descarga fragmentada de un archivo mp4 fragmentado

Parámetros
* Holo: capturar hologramas: true o false
* PV: cámara captura PV: true o false
* MIC: captura de micrófono: true o false
* bucle invertido: capturar audio de la aplicación: true o false

**/API/holographic/Stream/live_med.mp4 (GET)**

Inicia una descarga fragmentada de un archivo mp4 fragmentado

Parámetros
* Holo: capturar hologramas: true o false
* PV: cámara captura PV: true o false
* MIC: captura de micrófono: true o false
* bucle invertido: capturar audio de la aplicación: true o false

## <a name="networking"></a>Funciones de red

**/api/networking/ipconfig (GET)**

Obtiene la configuración de ip actual

## <a name="os-information"></a>Información del sistema operativo

**/api/os/info (GET)**

Obtiene la información del sistema operativo

**/API/OS/MachineName (GET)**

Obtiene el nombre del equipo

**/api/os/machinename (POST)**

Establece el nombre del equipo

Parámetros
* nombre: Nuevo nombre de la máquina, hex64 codificado para establecer en

## <a name="performance-data"></a>Datos de rendimiento

**/api/resourcemanager/processes (GET)**

Devuelve la lista de procesos en ejecución con detalles

Devolver datos
* JSON con la lista de procesos y los detalles de cada proceso

**/api/resourcemanager/systemperf (GET)**

Devuelve estadísticas de rendimiento del sistema (lectura/escritura de E/S, estadísticas de memoria etcetera.

Devolver datos
* JSON con información del sistema: CPU, GPU, memoria, E/S y red

## <a name="power"></a>Alimentación

**/API/Power/Battery (GET)**

Obtiene el estado actual de la batería

**/api/power/state (GET)**

Comprueba si el sistema está en un estado de bajo consumo de energía

## <a name="remote-control"></a>Control remoto

**/api/control/restart (POST)**

Reinicia el dispositivo de destino

**/API/control/Shutdown (POST)**

Apaga el dispositivo de destino

## <a name="task-manager"></a>Administrador de tareas

**/api/taskmanager/app (DELETE)**

Detiene una aplicación moderna

Parámetros
* paquete: Nombre completo del paquete de aplicación, hex64 codificado
* forzar detención: Forzar que detener todos los procesos (= yes)

**/api/taskmanager/app (POST)**

Se inicia una aplicación moderna

Parámetros
* AppID: PRAID de aplicación para iniciar, hex64 codificado
* paquete: Nombre completo del paquete de aplicación, hex64 codificado

## <a name="wifi-management"></a>Administración de Wi-Fi

**/api/wifi/interfaces (GET)**

Enumera las interfaces de red inalámbrica

Devolver datos
* Lista de interfaces inalámbricas con detalles (GUID), descripción, etcetera.)

**/api/wifi/network (DELETE)**

Elimina un perfil asociado a una red en una interfaz especificada

Parámetros
* interfaz: guid de la interfaz de red
* perfil: nombre de perfil

**/api/wifi/networks (GET)**

Enumera las redes inalámbricas en la interfaz de red especificado

Parámetros
* interfaz: guid de la interfaz de red

Devolver datos
* Lista de redes inalámbricas que se encuentra en la interfaz de red con los detalles

**/api/wifi/network (POST)**

Se conecta o desconecta a una red en la interfaz especificada

Parámetros
* interfaz: guid de la interfaz de red
* SSID: ssid, hex64 codificado para conectarse a
* OP: conectar o desconectar
* CreateProfile: yes o no
* clave: hex64 clave, compartidos con codificación

## <a name="windows-performance-recorder"></a>Grabadora de rendimiento de Windows

**/api/wpr/customtrace (POST)**

Carga un perfil WPR e inicia el seguimiento con el perfil cargado.

carga
* cuerpo de http que cumplan varias partes

Devolver datos
* Devuelve el estado de sesión WPR.

**/api/wpr/status (GET)**

Recupera el estado de la sesión WPR

Devolver datos
* Estado de sesión WPR.

**/api/wpr/trace (GET)**

Detiene una sesión de seguimiento de WPR (rendimiento)

Devolver datos
* Devuelve el archivo ETL de seguimiento

**/api/wpr/trace (POST)**

Se inicia un WPR (rendimiento), las sesiones de seguimiento

Parámetros
* perfil: Nombre del perfil. Perfiles disponibles se almacenan en perfprofiles/profiles.json

Devolver datos
* Durante el inicio, se devuelve el estado de sesión WPR.

## <a name="see-also"></a>Vea también
* [Uso de la Windows Device Portal](using-the-windows-device-portal.md)
* [Núcleo de Portal de dispositivo (UWP) de referencia de API](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
