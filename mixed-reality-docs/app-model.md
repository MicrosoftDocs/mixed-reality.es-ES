---
title: Modelo de aplicación
description: Windows Mixed Reality usa el modelo de aplicación proporcionado por la plataforma Universal de Windows, un modelo y el entorno para aplicaciones modernas de Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, modelo de aplicación, el ciclo de vida, suspender, reanudar, icono, vistas, los contratos
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605302"
---
# <a name="app-model"></a>Modelo de aplicación

Windows Mixed Reality usa el modelo de aplicación proporcionado por el [Universal Windows Platform](https://docs.microsoft.com/windows/uwp/get-started/) (UWP), un entorno para aplicaciones Windows modernas y modelo. El modelo de aplicación para UWP define cómo las aplicaciones están instaladas, actualizada con control de versiones y quita de forma segura y completamente. Lo controla el ciclo de vida de aplicación - cómo las aplicaciones ejecutarán, suspendieron y finalización - y cómo puede conservar el estado. También cubre la integración y la interacción con el sistema operativo, archivos y otras aplicaciones.

![Aplicaciones 2D organizadas en el Windows Mixed Reality principal en un área desayuno](images/20160112-055908-hololens-500px.jpg)<br>
*Aplicaciones con una vista 2D organizados en el inicio de Windows Mixed Reality*

## <a name="app-lifecycle"></a>Ciclo de vida de la aplicación

El ciclo de vida de una aplicación de realidad mixta implica los conceptos de aplicación estándar, como la selección de ubicación de inicio, finalización y eliminación.

### <a name="placement-is-launch"></a>La ubicación es el inicio

Cada aplicación se inicia en realidad mixta mediante la colocación de un icono de la aplicación (simplemente un [mosaico secundario Windows](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) en el [Windows Mixed Reality principal](navigating-the-windows-mixed-reality-home.md). Estos iconos de aplicación, en la selección de ubicación, volverá a ejecutarse la aplicación. Estos iconos de aplicación conservar y permanecer en la ubicación donde se colocan, que actúan como iniciadores para siempre que desean volver a la aplicación.

![Selección de ubicación coloca un icono secundario en el mundo](images/slide1-600px.png)<br>
*Selección de ubicación coloca un icono secundario en el mundo*

Tan pronto como finaliza la selección de ubicación (a menos que se inició la selección de ubicación con un [una aplicación a](app-model.md#protocols) iniciar), la aplicación empieza a iniciar. Windows Mixed Reality puede ejecutar un número limitado de aplicaciones al mismo tiempo. Tan pronto como se coloca y se inicie una aplicación, pueden suspender otras aplicaciones activas, dejando una captura de pantalla de último estado de la aplicación en su icono de aplicación siempre que lo ha colocado. Consulte [ciclo de vida de aplicación de Windows 10 UWP](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) para obtener más información sobre cómo administrar la reanudación y otros eventos de ciclo de vida de la aplicación.

![Después de colocar un icono, la aplicación comienza a ejecutarse](images/slide2-500px.png) ![diagrama de estado para la aplicación en ejecución, suspendidas o no se está ejecutando](images/ic576232-500px.png)<br>
*Izquierda: después de colocar un icono, la aplicación comienza a ejecutarse. Derecha: diagrama de estado de para la aplicación en ejecución, suspendidas o no se está ejecutando.*

### <a name="remove-is-closeterminate-process"></a>Quitar es cerrar o Finalizar proceso

Cuando se quita un icono de la aplicación coloca el mundo, esto cierra los procesos subyacentes. Esto puede ser útil para garantizar que se termina la aplicación o reiniciar una aplicación problemática.

### <a name="app-suspensiontermination"></a>Suspensión o finalización de la aplicación

En el [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md), el usuario es capaz de crear varios puntos de entrada para una aplicación. Para ello, inicie la aplicación desde el menú Inicio y colocar el icono de la aplicación en el mundo. Cada icono de la aplicación se comporta como un punto de entrada diferente y tiene una instancia independiente de mosaico en el sistema. Una consulta para [SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) dará como resultado un **SecondaryTile** para cada instancia de la aplicación.

Cuando una aplicación para UWP se suspende, se toma una captura de pantalla del estado actual.

![Capturas de pantalla se muestran para las aplicaciones suspendidas](images/slide9-800px.png)<br>
*Capturas de pantalla se muestran para las aplicaciones suspendidas*

Una diferencia clave de otros shells de Windows 10 es cómo se informa a la aplicación de una activación de instancias de aplicación a través de la [CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) y [CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) eventos.

|  Escenario |  Reanudar  |  Activado | 
|----------|----------|----------|
|  Inicie una nueva instancia de la aplicación desde el menú Inicio  |   |  **Activar** con un nuevo [TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Iniciar la segunda instancia de la aplicación desde el menú Inicio  |   |  **Activar** con un nuevo **TileId** | 
|  Seleccione la instancia de la aplicación que no está activa actualmente  |   |  **Activar** con el **TileId** asociado a la instancia | 
|  Seleccione una aplicación diferente y luego seleccione la instancia activa anteriormente  |  **Reanudar** provoca  |  | 
|  Seleccione una aplicación diferente y luego seleccione la instancia que era anteriormente inactiva  |  **Reanudar** provoca  |  A continuación, **Activated** con el **TileId** asociado a la instancia | 

### <a name="extended-execution"></a>Ejecución extendida

A veces, la aplicación debe continuar trabajando en segundo plano o la reproducción de audio. [Tareas en segundo plano](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) están disponibles en HoloLens.

![Las aplicaciones pueden ejecutar en segundo plano](images/slide10-800px.png)<br>
*Las aplicaciones pueden ejecutar en segundo plano*

## <a name="app-views"></a>Vistas de aplicación

Cuando se activa la aplicación, puede elegir qué tipo de vista que le gustaría mostrar. Para una aplicación **CoreApplication**, siempre hay un elemento principal [vista aplicación](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) y cualquier número de vistas de aplicación adicional que le gustaría crear. En escritorio, se puede considerar una vista de la aplicación como una ventana. Nuestras plantillas de aplicación de realidad mixta crean un proyecto de Unity que la vista de la aplicación principal es [envolventes](app-views.md). 

La aplicación puede crear una vista de aplicación 2D adicionales con tecnología como XAML, para usar las características de Windows 10, como la compra en la aplicación. Si la aplicación se inicia como una aplicación para UWP para otros dispositivos Windows 10, la vista principal es 2D, pero podría "encenderse" en realidad mixta mediante la adición de una vista de aplicación adicionales envolvente para mostrar una experiencia volumetrically. Imagine la creación de una aplicación de Visor de fotos en XAML en el botón presentación con diapositivas cambia a una vista de aplicaciones envolventes que voló fotos desde la aplicación en el mundo y superficies.

![La aplicación en ejecución puede tener una vista 2D o una vista envolvente](images/slide3-800px.png)<br>
*La aplicación en ejecución puede tener una vista 2D o una vista envolvente*

### <a name="creating-an-immersive-view"></a>Creación de una vista envolvente

Las aplicaciones de realidad mixta son aquellos que crean una vista envolvente, lo cual se consigue con la [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) tipo.

Una aplicación que es puramente envolvente siempre debe crear una vista envolvente en el inicio, incluso si inicia desde el escritorio. Vistas envolventes siempre aparecen en los auriculares, independientemente de donde se crearon. Activación de una vista envolvente mostrará el Portal de realidad mixta y guiar al usuario para poner en sus auriculares.

Una aplicación que se inicia con una vista 2D en el monitor de escritorio puede crear una vista secundaria envolvente para mostrar el contenido en los auriculares. Un ejemplo de esto es una ventana de Edge 2D en el monitor muestra un vídeo de 360 grados en los auriculares.

![Aplicaciones que se ejecutan en la vista envolvente son el único visible](images/slide4-800px.png)<br>
*Una aplicación que se ejecuta en una vista envolvente sólo está visible*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Vista 2D en el inicio de Windows Mixed Reality

Algo distinto de una vista envolvente se representa como una vista 2D en el mundo.

Una aplicación puede tener vistas 2D en ambos el monitor de escritorio y en los auriculares. Tenga en cuenta que se colocará una nueva vista 2D en el shell de la mismo que la vista que lo creó, en el monitor o en los auriculares. No es actualmente posible para una aplicación o un usuario para mover una vista 2D entre el inicio de la realidad mixta y el monitor.

![Aplicaciones que se ejecutan en la vista 2D comparten el espacio en el mundo mixto con otras aplicaciones](images/slide5-800px.png)<br>
*Aplicaciones que se ejecutan en una vista 2D compartan el espacio con otras aplicaciones*

### <a name="placement-of-additional-app-tiles"></a>Selección de ubicación de los iconos de aplicación adicionales

Puede colocar como muchas aplicaciones con un 2D ver en el mundo como desee con la [API de mosaico secundario](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Estos iconos "anclados" aparecerá como pantallas de presentación que los usuarios, deben colocar y, a continuación, pueden usar más adelante para iniciar la aplicación. Windows Mixed Reality no admite actualmente el contenido del icono 2D de representación como iconos dinámicos.

![Las aplicaciones pueden tener varias ubicaciones con los iconos secundarios](images/slide6-800px.png)<br>
*Las aplicaciones pueden tener varias ubicaciones con los iconos secundarios*

### <a name="switching-views"></a>Al cambiar de vista

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Cambio de la vista XAML 2D a la vista envolvente

Si la aplicación usa XAML y, a continuación, el XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) controlará la primera vista de la aplicación. La aplicación debe pasar a la vista envolvente antes de activar la **CoreWindow**para asegurarse de que la aplicación se inicia directamente en la experiencia envolvente.

Use [CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) y [ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) para facilitar la vista activa.

> [!NOTE]
>* No se especifica la [ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) marca **SwitchAsync** cuando se quitará el cambio de la vista XAML a la vista envolvente, o la pizarra que inició la aplicación en el mundo.
>* **SwitchAsync** se debería llamar mediante el [distribuidor](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) asociado a la vista cambia a.
>* Deberá **SwitchAsync** volver a la vista XAML, si tiene que iniciar un teclado virtual o activar otra aplicación.

![Las aplicaciones pueden cambiar entre vistas 2D y envolventes](images/slide7-600px.png) ![cuando una aplicación entra en una vista envolvente, desaparecen el mundo mixto y otras aplicaciones](images/slide8-600px.png)<br>
*Izquierda: aplicaciones pueden cambiar entre vistas 2D y envolventes. Right: cuando una aplicación entra en una vista envolvente, desaparecen las aplicaciones de Windows Mixed Reality domésticas y de otras.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Cambiar desde la vista envolvente a un teclado vista XAML

Un motivo habitual para cambiar atrás y hacia las vistas muestra un teclado en una aplicación de realidad mixta. El shell sólo es capaz de mostrar el teclado del sistema si la aplicación muestra una vista 2D. Si la aplicación necesita obtener entrada de texto, puede proporcionar una vista personalizada de XAML con un campo de entrada de texto, cambie a él y, a continuación, cambie después de completada la entrada.

Al igual que en la sección anterior, puede usar **ApplicationViewSwitcher.SwitchAsync** realizar la transición a una vista XAML de la vista envolvente.

## <a name="app-size"></a>Tamaño de la aplicación

Vistas de aplicación 2D siempre aparecen en una pizarra virtual fija. Esto hace que todas las vistas 2D muestran la misma cantidad exacta de contenido. Estos son algunos detalles adicionales sobre el tamaño de vista 2D de la aplicación:
* Al cambiar el tamaño, se conserva la relación de aspecto de la aplicación.
* Aplicación [factor de escala y de resolución](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) no cambian al cambiar el tamaño.
* Las aplicaciones no pueden consultar su tamaño en el mundo real.

![Aplicaciones 2D aparecen con tamaños de ventana fijo](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Las aplicaciones con una vista 2D aparecen con tamaños de ventana fijo*

## <a name="app-tiles"></a>Iconos de aplicación

El menú Inicio utiliza el icono pequeño estándar y el icono mediano para PIN y la **todas las aplicaciones** lista en realidad mixta. 

![El menú de inicio de Windows Mixed Reality](images/start-500px.png)<br>
*El menú de inicio de Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Aplicación para las interacciones de aplicación

Al crear aplicaciones, tener acceso a los mecanismos de aplicación a una comunicación sofisticada disponibles en Windows 10. Muchas de las nuevas API de protocolo y los registros de archivo funcionan perfectamente en HoloLens para habilitar el inicio de aplicación y la comunicación. 

Tenga en cuenta que para auriculares de escritorio, la aplicación asociada con una extensión de archivo determinada o protocolo puede ser una aplicación de Win32 que solo puede aparecer en el monitor de escritorio o en la Pizarra de escritorio.

### <a name="protocols"></a>Protocolos

HoloLens permite una aplicación a iniciar a través de la [Windows.System.Launcher APIs](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

Hay algunas cosas a tener en cuenta al iniciar otra aplicación:

* Al realizar un inicio de no modal de como [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), el usuario debe colocar la aplicación antes de interactuar con él.

* Al realizar un inicio modal, como a través de [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), la aplicación modal se coloca por encima de la ventana.

* Windows Mixed Reality no se puede superponer las aplicaciones sobre las vistas exclusivas. Para mostrar la aplicación iniciada, Windows lleva al usuario volver a todo el mundo para mostrar la aplicación.

### <a name="file-pickers"></a>Selectores de archivos

HoloLens admite tanto [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) y [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) contratos. Sin embargo, no hay ninguna aplicación viene preinstalada que cumple los contratos del selector de archivos. Estas aplicaciones: por ejemplo, OneDrive - pueden instalarse desde la Microsoft Store.

Si tiene instalada más de una aplicación de selector de archivos, no verá ninguna interfaz de usuario de desambiguación para elegir qué aplicación para iniciar; en su lugar, se elegirá el primer selector de archivos instalado. Al guardar un archivo, se genera el nombre de archivo que incluye la marca de tiempo. No se puede cambiar por el usuario.

De forma predeterminada, se admiten las siguientes extensiones localmente:

|  Aplicación  |  Extensions | 
|----------|----------|
|  Fotos  |  bmp, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Contratos de aplicación y las extensiones de Windows Mixed Reality

Contratos de aplicación y los puntos de extensión permiten registrar la aplicación para aprovechar las características más profundas del sistema operativo como una extensión de archivo de control o con tareas en segundo plano. Se trata de una lista de los puntos de extensión en HoloLens y contratos admitidos y no admitidos.

|  Contrato o la extensión  |  ¿Admite? | 
|----------|----------|
| [Proveedor de imágenes de cuenta (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | No compatible | 
| [Alarma](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | No compatible | 
| [Servicio de aplicación](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Se admiten pero no es totalmente funcional | 
| [Proveedor de citas](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | No compatible | 
| [Reproducción automática (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | No compatible | 
| [Tareas en segundo plano (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Se admiten parcialmente (no todos los desencadenadores de trabajo) | 
| [Tarea de actualización (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Se admite | 
| [Contrato del actualizador de archivos en caché](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Se admite | 
| [Configuración de la cámara (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | No compatible | 
| [Protocolo de acceso telefónico](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | No compatible | 
| [Activación de archivo (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Se admite | 
| [Contrato del selector para abrir archivos](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Se admite | 
| [Contrato del selector para guardar archivos](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Se admite | 
| [Llamada de la pantalla de bloqueo](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | No compatible | 
| [Reproducción de multimedia](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | No compatible | 
| [Contrato de reproducir en](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | No compatible | 
| [Tarea de configuración preinstalada](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | No compatible | 
| [Imprimir el flujo de trabajo 3D](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Se admite | 
| [Configuración de la tarea de impresión (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | No compatible | 
| [Activación de URI (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Se admite | 
| [Inicio restringido](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | No compatible | 
| [Contrato de búsqueda](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | No compatible | 
| [Contrato de configuración](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | No compatible | 
| [Contrato de compartir](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | No compatible | 
| [/ Certificados SSL (extensión)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Se admite | 
| [Proveedor de cuentas Web](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Se admite | 

## <a name="app-file-storage"></a>Almacenamiento de archivos de aplicación

Todo el almacenamiento es a través de la [espacio de nombres Windows.Storage](https://docs.microsoft.com/uwp/api/Windows.Storage). Consulte la documentación siguiente para obtener más detalles. HoloLens no es compatible con la sincronización de almacenamiento/movilidad de aplicación.

* [Archivos, carpetas y bibliotecas](https://docs.microsoft.com/windows/uwp/files/index)
* [Almacenar y recuperar la configuración y otros datos de aplicación](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Carpetas conocidas

Consulte [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) para los detalles completos de las aplicaciones para UWP.

<table>
<tr>
<th> Property</th><th> Se admite en HoloLens</th><th> Compatible con inmersivos</th><th> Descripción</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de captura de la aplicación.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta álbum de cámara.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de documentos. La biblioteca de documentos no está pensada para uso general.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de música.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de objetos 3D.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de imágenes.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Listas de reproducción</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de listas de reproducción.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta Saved Pictures.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Obtiene la biblioteca de vídeos.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">HomeGroup</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta grupo hogar.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta del medio de los dispositivos de servidor (Digital Living Network Alliance (DLNA)).</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta de llamadas grabadas.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Obtiene la carpeta dispositivos extraíbles.</td>
</tr>
</table>

## <a name="app-package"></a>Paquete de la aplicación

Con Windows 10 destino ya no es un sistema operativo, pero en su lugar [dirigir su aplicación a uno o más familias de dispositivos](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Una familia de dispositivos identifica las API, las características del sistema y los comportamientos que puedes esperar en todos los dispositivos de la familia. También determina el conjunto de dispositivos en el que se puede instalar la aplicación desde el [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Para tener como destino auriculares de escritorio y HoloLens, dirigir su aplicación a la **Windows.Universal** familia de dispositivos.
* Para establecer el destino de escritorios simplemente auriculares, dirigir su aplicación a la **Windows.Desktop** familia de dispositivos.
* Para tener como destino solo HoloLens, dirigir su aplicación a la **Windows.Holographic** familia de dispositivos.

## <a name="see-also"></a>Vea también

* [Vistas de aplicación](app-views.md)
* [Actualización de aplicaciones UWP 2D de realidad mixta](building-2d-apps.md)
* [Guía de diseño de la aplicación 3D del iniciador](3d-app-launcher-design-guidance.md)
* [Implementación de los iniciadores de aplicaciones 3D](implementing-3d-app-launchers.md)
