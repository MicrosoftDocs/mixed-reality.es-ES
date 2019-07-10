---
title: Mixto captura realidad para desarrolladores
description: Procedimientos recomendados para la realidad mixta de captura para desarrolladores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, fotos, vídeo, captura, cámara
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694364"
---
# <a name="mixed-reality-capture-for-developers"></a>Mixto captura realidad para desarrolladores

> [NOTA] Consulte [procesar desde la cámara PV](#render-from-the-pv-camera-opt-in) a continuación para obtener orientación sobre una nueva funcionalidad MRC de HoloLens 2.

Puesto que un usuario podría llevar a cabo una [mixto captura realidad](mixed-reality-capture.md) foto (MRC) o de vídeo en cualquier momento, hay algunas cosas que debe tener en cuenta al desarrollar la aplicación. Esto incluye procedimientos recomendados para la calidad visual MRC y poder reaccionar a los cambios del sistema mientras se están capturando MRCs.

Los desarrolladores pueden integrar perfectamente también captura la realidad mixta y la inserción en sus aplicaciones.

MRC en HoloLens (primera generación) es compatible con vídeos y fotos hasta 720p, mientras que MRC en HoloLens 2 admite vídeos hasta 1.080 p y fotos hasta resolución de 4 K.

## <a name="the-importance-of-quality-mrc"></a>La importancia de calidad MRC

Realidad mixta captura fotos y vídeos son probablemente la primera exposición que tendrá un usuario de la aplicación. Si, como capturas de pantalla de realidad mixta en la página de Microsoft Store o a otros usuarios compartidos MRCs en redes sociales. Puede usar MRC para su aplicación de demostración, educar a los usuarios, animamos a los usuarios compartir sus interacciones mixto del mundo y de investigación de usuario y la resolución de problemas.

## <a name="how-mrc-impacts-your-app"></a>Cómo MRC afecta a la aplicación

### <a name="enabling-mrc-in-your-app"></a>Habilitar MRC en la aplicación

De forma predeterminada, una aplicación no tiene que hacer nada para permitir que los usuarios a tomar capturas de realidad mixta.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Habilitación de alineación mejorada para MRC en la aplicación

De forma predeterminada, la realidad mixta captura combina salida holográfica derecha del ojo con la cámara de vídeo/fotos (PV). Estos dos orígenes se combinan mediante el punto de enfoque establecido por la aplicación actualmente en ejecución envolvente.

Esto significa que no se alinean hologramas fuera del plano de foco también (debido a la distancia física entre la cámara PV y la presentación de la derecha).

#### <a name="set-the-focus-point"></a>Establecer el punto de enfoque

Aplicaciones envolventes (en HoloLens) se deben establecer el [centrarse punto](focus-point-in-unity.md) de donde quieran su plano estabilización sea. Esto garantiza la mejor alineación en los auriculares con micrófono y en la captura de realidad mixta.

Si no se establece un punto de enfoque, el plano de estabilización predeterminada será dos medidores.

#### <a name="render-from-the-pv-camera-opt-in"></a>Representación de la cámara PV (opt-in)

HoloLens 2 agrega la capacidad de una aplicación envolvente para **procesar desde la cámara PV** mientras se está ejecutando la captura de realidad mixta. Para asegurarse de que la aplicación admite el procesamiento adicional correctamente, la aplicación debe participar en esta funcionalidad.

Representar entre las ofertas de cámara PV las siguientes mejoras sobre la experiencia MRC predeterminada:
* Alineación holograma a su entorno físico y el alcance (para las interacciones de casi) debe ser precisa en absoluto las distancias, en lugar de tener un desplazamiento a una distancia que no sea el punto de enfoque, como puede ver en el valor predeterminado MRC.
* El efecto de ojos derecha en los auriculares no se pongan en peligro, ya que no se utiliza para representar el hologramas para la salida MRC.

Hay tres pasos para habilitar la representación de la cámara PV:
1. Habilitar la PhotoVideoCamera HolographicViewConfiguration
2. Controlar la representación HolographicCamera adicional
3. Compruebe el código y los sombreadores se representan correctamente desde este HolographicCamera adicional

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>Habilitar la PhotoVideoCamera HolographicViewConfiguration

Para participar en, una aplicación permite simplemente la PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Controlar la representación de HolographicCamera adicional de DirectX

Cuando la aplicación tiene participar en procesamiento de la cámara PV y se inicia la captura de realidad mixta:
1. Evento de CameraAdded del HolographicSpace se desencadenará. Este evento puede ser diferido si la aplicación no puede controlar la cámara en este momento.
2. Una vez que se ha completado el evento (y no hay ningún aplazamientos pendientes) el HolographicCamera aparecerá en la lista de AddedCameras de la HolographicFrame siguiente.

Cuando se detiene captura la realidad mixta (o si la aplicación deshabilita la configuración de la vista mientras se está ejecutando la captura de realidad mixta): el HolographicCamera aparecerá en la lista de RemovedCameras de la HolographicFrame siguiente y eventos de CameraRemoved del HolographicSpace le se activan.

Un [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) propiedad se ha agregado a HolographicCamera para ayudar a identificar la configuración de una cámara que pertenece.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Controlar la representación HolographicCamera adicional en Unity

>[!NOTE]
> Compatibilidad con Unity para procesar a partir de la cámara PV está en desarrollo y no se puede utilizar todavía. Esta documentación se actualizará cuando una compilación de Unity con el soporte técnico para la representación de la cámara PV está disponible.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Compruebe a los sombreadores y cámaras adicionales de soporte técnico de código

Ejecutar una captura de realidad mixta y compruebe si hay alineación inusual, el contenido que falta o problemas de rendimiento. Actualizar los sombreadores y el código según corresponda.

Si hay determinados escenas que no es compatible con la representación de una cámara adicional, puede deshabilitar HolographicViewConfiguration del PhotoVideoCamera durante éstas.

### <a name="disabling-mrc-in-your-app"></a>Deshabilitar MRC en la aplicación

#### <a name="2d-app"></a>Aplicación 2D

Pueden elegir aplicaciones 2D que su contenido visual tapado cuando se captura la realidad mixta se está ejecutando:
* Presente con el [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) marca
* Crear cadena de intercambio de la aplicación con el [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) marca
* Con Windows 10 puede 2019 actualizar, configuración del ApplicationView [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>Aplicación envolvente

Pueden elegir aplicaciones envolventes que su contenido visual excluir de la captura de realidad mixta por:
* Configuración del HolographicCameraRenderingParameter [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) para deshabilitar la captura de realidad mixta para su marco asociado
* Configuración del HolographicCamera [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) para deshabilitar la captura de realidad mixta para su cámara holográfica asociado

#### <a name="password-keyboard"></a>Teclado de contraseña

Con Windows 10, es posible que la actualización de 2019, contenido visual se excluye automáticamente de la captura de realidad mixta cuando un teclado de contraseña o pin está visible.

### <a name="knowing-when-mrc-is-active"></a>Saber cuándo MRC está activo

El [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) clase puede utilizarse por una aplicación para saber cuando se ejecuta el sistema mixto captura realidad (para audio o vídeo).

>[!NOTE]
>Del AppCapture [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API puede devolver null si se combina con captura de la realidad no está disponible en el dispositivo. También es importante eliminar del registro el evento CapturingChanged cuando se suspende la aplicación, en caso contrario, puede obtener MRC en un estado bloqueado.

### <a name="best-practices-hololens-specific"></a>Procedimientos recomendados (específico de HoloLens)

MRC se espera que funcione sin trabajo adicional de los desarrolladores, pero hay algunos aspectos que debe tener en cuenta para ofrecer una experiencia mejor la realidad mixta captura de la aplicación.

**MRC usa el canal alfa del holograma para combinar con el [cámara](locatable-camera.md) imágenes**

El paso más importante es asegurarse de que la aplicación se desactiva en negro transparente, en lugar de borrar en negro opaco. En Unity, esto se realiza de forma predeterminada con la MixedRealityToolkit pero si está desarrollando en que no sean de Unity, puede que necesite realizar cambios en una línea.

Estos son algunos de los artefactos que puede aparecer en MRC si la aplicación no se desactiva en negro transparente:

**Errores de ejemplo**: Bordes negros alrededor del contenido (conmutación por error borrar en negro transparente)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**Errores de ejemplo**: La escena completa en segundo plano de la holograma aparece en negra. Establecer un valor alfa de fondo de resultados 1 en un fondo negro

![Establecer un valor alfa de fondo de resultados 1 en un fondo negro](images/clearopaqueblack-300px.png)

**Resultado esperado**: Hologramas aparecen correctamente combinadas con el mundo real (resultado esperado si se borra en negro transparente)

![Resultado esperado si se borra en negro transparente](images/cleartransparentblack-300px.png)

**Solución**:
* Cambie cualquier contenido que se muestre como negro opaco para tener un valor alfa de 0.
* Asegúrese de que la aplicación se desactiva en negro transparente.
* Valores predeterminados de Unity para borrar para borrar automáticamente con MixedRealityToolkit, pero si es una aplicación que no sea Unity que debe modificar el color utilizado con ID3D11DeiceContext::ClearRenderTargetView(). Desea asegurarse de que desactive en negro transparente (0,0,0,0) en lugar de color negro opaco (0,0,0,1).

Ahora puede ajustar los valores alfabéticos de los recursos si desea que, pero normalmente no es necesario. La mayoría de los casos, será buenas de fábrica MRCs. MRC supone alfa premultiplicado. Los valores alfa solo afectará a la captura MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Qué esperar cuando se habilita MRC en HoloLens

Los siguientes se aplican a HoloLens (primera generación) y 2 de HoloLens, a menos que se indique lo contrario:

* El sistema limita la aplicación a la representación de 30Hz. Esto crea algún espacio disponible para MRC para ejecutarse por lo que la aplicación no necesita mantener una reserva de presupuesto constante y también coincide con la velocidad de fotogramas de vídeo registro MRC de 30fps
* Holograma contenido en la vista correcto del dispositivo puede aparecer "chispeante" cuando la grabación/streaming MRC: texto puede resultar más difícil de leer y bordes holograma pueden aparecer más irregular (participar en la cámara 3rd se representan en **HoloLens 2** evita Este compromiso)
* MRC fotos y vídeos respetará la aplicación [centrarse punto](focus-point-in-unity.md) si la aplicación ha habilitado, que le ayudarán a garantizar hologramas con precisión se colocan. Para ver vídeos, el punto de enfoque se suaviza por lo que pueden aparecer hologramas a desviarse lentamente en su lugar, si la profundidad de punto de enfoque cambia de forma significativa. Hologramas que se encuentran en distintas profundidades desde el punto de enfoque pueden aparecer desplazamiento procedentes del mundo real (consulte el ejemplo siguiente donde el punto de enfoque está establecido en 2 metros pero holograma se coloca en el medidor de 1).

![Hologramas en 2 metros aparecerán perfectamente está registradas en el mundo. Hologramas a close o lejano distancias es posible que se desplacen ligeramente.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integrar la funcionalidad de MRC desde dentro de la aplicación

Puede iniciar la aplicación de realidad mixta foto MRC o captura de vídeo desde dentro de la aplicación y el contenido capturado está disponible para su aplicación sin que se almacena en el de dispositivo "álbum de cámara." Puede crear una grabación MRC personalizado o aprovechar las ventajas de la interfaz de usuario de captura de cámara integrada. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC con cámara integrada de interfaz de usuario

Los desarrolladores pueden usar el *[API de interfaz de usuario de captura de cámara](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* para obtener una foto de realidad mixta capturados por el usuario o un vídeo con unas pocas líneas de código.

Esta API inicia la cámara integrada MRC interfaz de usuario, desde el que el usuario puede hacer una foto o vídeo y devuelve la captura resultante a la aplicación.  Si desea crear su propia interfaz de usuario de la cámara o necesita inferiores acceso a la secuencia de captura, puede crear una grabadora personalizada Capture de realidad mixta.

### <a name="creating-a-custom-mrc-recorder"></a>Creación de una grabadora MRC personalizado

Mientras el usuario siempre puede desencadenar una foto o vídeo con el sistema MRC el servicio de captura, una aplicación que desee crear una aplicación de cámara personalizada pero incluir hologramas en la secuencia de la cámara al igual que MRC. Esto permite que la aplicación iniciar las capturas en nombre del usuario, generar grabación personalizada de la interfaz de usuario o personalizar la configuración de MRC para nombrar algunos ejemplos.

**HoloStudio agrega una cámara MRC personalizada mediante efectos MRC**

![HoloStudio agrega una cámara MRC personalizada mediante efectos MRC](images/cameraiconholostudio-300px.jpg)

Deberían ver las aplicaciones de Unity [Locatable_camera_in_Unity](locatable-camera-in-unity.md) para la propiedad para habilitar hologramas.

Otras aplicaciones pueden hacerlo mediante la [las API de captura de Windows Media](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) para controlar la cámara y agregar un efecto de Audio y vídeo MRC para incluir hologramas virtuales y el audio de la aplicación en imágenes fijas y vídeos.

Las aplicaciones tienen dos opciones para agregar el efecto:
* La API anterior: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* El nuevo Microsoft recomienda API (devuelve un objeto, lo que permite manipular las propiedades dinámicas): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) que requieren la aplicación cree su propia implementación de [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) y [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition). Consulte el ejemplo de efecto MRC para ejemplo de uso.

>[!NOTE]
> No se reconocerá el espacio de nombres Windows.Media.MixedRealityCapture por Visual Studio, pero las cadenas siguen siendo válidas.

Efecto de vídeo MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nombre de la propiedad  |  Tipo  |  Valor predeterminado  |  Descripción | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  Describir qué secuencia de captura este efecto se utiliza para. Audio no está disponible. | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Marca para habilitar o deshabilitar hologramas en la captura de vídeo. | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Marca para habilitar o deshabilitar el indicador de grabación de pantalla durante holograma de captura. | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la estabilización de vídeo con la tecnología de la herramienta de seguimiento de HoloLens. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Establecer el número de marcos histórico se usa para la estabilización de vídeo. 0 es la latencia de 0 y casi "gratuita" desde una perspectiva de capacidad y rendimiento. se recomienda 15 para calidad más alta (a costa de 15 fotogramas de latencia y memoria). | 
|  GlobalOpacityCoefficient  |  flotante  |  0,9 (HoloLens) 1.0 (envolventes auriculares)  |  Establecer coeficiente de opacidad global de holograma en el intervalo comprendido entre 0,0 (completamente transparente) a 1.0 (totalmente opaco). | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la devolución de un marco vacío si no hay un contenido protegido que muestra de aplicación UWP 2d. Si esta marca es false y una 2d aplicación para UWP es mostrando protegido contenido, que la aplicación para UWP 2d se reemplazará por una textura de contenido protegida en los auriculares con micrófono y en la captura de realidad mixta. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar que muestra la malla de la cámara holográfica área oculta y los vecinos de contenido. |
| OutputSize | Tamaño | 0, 0 | Establezca el tamaño del resultado deseado después de recortarse para la estabilización de vídeo. Si se especifica 0 o un tamaño de salida no válido, se elige un tamaño de recorte predeterminado. |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | Enumeración que se usa para indicar qué configuración de la vista holográfica cámara debe capturarse. Configuración de 0 significa (mostrar) que la aplicación no se le pedirá para procesar a partir de la cámara de vídeo y fotografías |

Efecto de Audio MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>Nombre de la propiedad</th>
<th>Tipo</th>
<th>Valor predeterminado</th>
<th>Descripción</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 : Solo el audio del micrófono</li>
<li>1 : Solo el audio del sistema</li>
<li>2 : MIC y audio del sistema</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>Limitaciones de MRC simultáneas

Existen ciertas limitaciones en torno a varias aplicaciones que acceden al MRC al mismo tiempo.

#### <a name="photovideo-camera-access"></a>Acceso a la cámara de vídeo y fotos

La cámara de vídeo y fotos se limita al número de procesos que pueden tener acceso al mismo tiempo. Mientras se graba un proceso de vídeo o hacer una fotografía de cualquier otro proceso se producirá un error al adquirir la cámara de vídeo y fotos. (Esto se aplica a la captura de realidad mixta y de captura de fotografías y vídeo estándar)

Con el 2 de HoloLens, una aplicación puede usar de MediaCaptureInitializationSettings [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) propiedad para indicar que desea ejecutar SharedReadOnly si no necesitan control exclusivo sobre la cámara de vídeo y fotos. De este modo, la resolución y velocidad de fotogramas de la captura se limitará a lo que otras aplicaciones han configurado la cámara para proporcionar.

##### <a name="built-in-mrc-photovideo-camera-access"></a>Acceso a la cámara a integrados MRC fotografías y vídeo

Característica MRC integrada en Windows 10 (a través de Cortana, menú Inicio, accesos directos de hardware, Miracast, Windows Device Portal):
* Se ejecutará con ExclusiveControl de forma predeterminada

Sin embargo, se agregó compatibilidad para cada subsistema para operar en modo compartido:
* Si una aplicación solicita acceso ExclusiveControl a la cámara de vídeo y fotos, MRC integrado detendrá automáticamente con la cámara de vídeo y fotografías de modo que se realizará correctamente la solicitud de la aplicación
* Si se ha iniciado MRC integrada mientras que una aplicación tiene ExclusiveControl, MRC integrado se ejecutará en modo de SharedReadOnly

Esta funcionalidad en modo compartido tiene algunas restricciones:
* Foto a través de Cortana, los métodos abreviados de hardware o menú Inicio: Requiere Windows 10 de abril de 2018 actualización (o posterior)
* Vídeo a través de Cortana, los métodos abreviados de hardware o menú Inicio: Requiere Windows 10 de abril de 2018 actualización (o posterior)
* MRC transmisión por secuencias a través de Miracast: Requiere Windows 10 de octubre de 2018 actualización (o posterior)
* MRC de transmisión por secuencias a través de Windows Device Portal o a través de la aplicación complementaria de HoloLens: Requiere HoloLens 2

>[!NOTE]
> Pueden reducirse la velocidad de fotogramas de la cámara integrada de MRC la interfaz de usuario y la resolución de sus valores normales cuando otra aplicación está utilizando la cámara de vídeo y fotos.

#### <a name="mrc-access"></a>Acceso MRC

Con Windows 10 de abril de 2018 actualización, ya no hay una limitación en torno a varias aplicaciones de acceso a la secuencia MRC (sin embargo, el acceso a la cámara de vídeo y fotos todavía tiene limitaciones).

Anterior a Windows 10 de abril de 2018 actualización, la grabadora de una aplicación personalizada MRC era es mutuamente excluyente con sistema MRC (captura de fotografías, capturar vídeos o transmisión por secuencias desde la de Windows Device Portal).

## <a name="see-also"></a>Vea también
* [Captura de realidad mixta](mixed-reality-capture.md)
* [Vista del espectador](spectator-view.md)
