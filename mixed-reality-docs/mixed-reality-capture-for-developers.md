---
title: Captura de realidad mixta para desarrolladores
description: Prácticas recomendadas para la captura de realidad mixta para desarrolladores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, Foto, vídeo, captura, cámara
ms.openlocfilehash: 740b02dd1714679028541a888d721ae74e8e1f32
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937070"
---
# <a name="mixed-reality-capture-for-developers"></a>Captura de realidad mixta para desarrolladores

> [!NOTE]
> Consulte [representación de la cámara PV](#render-from-the-pv-camera-opt-in) a continuación para obtener instrucciones sobre una nueva funcionalidad de MRC para HoloLens 2.

Dado que un usuario podría tomar una foto o un vídeo de [captura de realidad mixta](mixed-reality-capture.md) (MRC) en cualquier momento, hay algunas cosas que debe tener en cuenta al desarrollar la aplicación. Esto incluye procedimientos recomendados para la calidad visual de MRC y para responder a los cambios del sistema mientras se capturan MRCs.

Los desarrolladores también pueden integrar sin problemas la captura y la inserción de la realidad mixta en sus aplicaciones.

MRC en HoloLens (primera generación) es compatible con vídeos y fotos de hasta 720p, mientras que MRC en HoloLens 2 es compatible con vídeos de hasta 1080p y fotos de hasta 4K.

## <a name="the-importance-of-quality-mrc"></a>La importancia de la MRC de calidad

Las fotos y los vídeos capturados de realidad mixta son probablemente la primera exposición que tendrá un usuario de la aplicación. Ya sea como capturas de pantallas de realidad mixta en la página de Microsoft Store o desde otros usuarios que comparten MRCs en redes sociales. Puede usar MRC para demostrar su aplicación, educar a los usuarios, animar a los usuarios a compartir sus interacciones de mundo mixtas y para la investigación de los usuarios y la solución de problemas.

## <a name="how-mrc-impacts-your-app"></a>Cómo afecta la MRC a la aplicación

### <a name="enabling-mrc-in-your-app"></a>Habilitación de MRC en la aplicación

De forma predeterminada, una aplicación no tiene que hacer nada para permitir que los usuarios tomen capturas de realidad mixta.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>Habilitación de la alineación mejorada de MRC en la aplicación

De forma predeterminada, la captura de realidad mixta combina la salida holográfica del ojo derecho con la cámara de foto/vídeo (PV). Estos dos orígenes se combinan mediante el punto de enfoque establecido por la aplicación envolvente que se está ejecutando actualmente.

Esto significa que los hologramas fuera del plano de foco no se alinearán también (debido a la distancia física entre la cámara PV y la pantalla derecha).

#### <a name="set-the-focus-point"></a>Establecer el punto de enfoque

Las aplicaciones envolventes (en HoloLens) deben establecer el [punto de enfoque](focus-point-in-unity.md) en el que quieren que el plano de estabilización sea. Esto garantiza la mejor alineación en el casco y en la captura de realidad mixta.

Si no se establece un punto de enfoque, el plano de estabilización tendrá como valor predeterminado dos metros.

#### <a name="render-from-the-pv-camera-opt-in"></a>Representación de la cámara PV (participación)

HoloLens 2 agrega la posibilidad de que una aplicación envolvente se **represente desde la cámara PV** mientras se ejecuta la captura de realidad mixta. Para asegurarse de que la aplicación admite la representación adicional correctamente, la aplicación tiene que participar en esta funcionalidad.

La representación de la cámara PV ofrece las siguientes mejoras con respecto a la experiencia predeterminada de MRC:
* La alineación de hologramas en el entorno físico y las manos (para interacciones cercanas) deben ser precisas en todas las distancias, en lugar de tener un desplazamiento en distancias distintas del punto de enfoque tal como se puede ver en el MRC predeterminado.
* El ojo adecuado en el casco no se verá comprometido, ya que no se usará para representar los hologramas para la salida de MRC.

Hay tres pasos para habilitar la representación desde la cámara PV:
1. Habilitación de PhotoVideoCamera HolographicViewConfiguration
2. Controlar la representación HolographicCamera adicional
3. Compruebe que los sombreadores y el código se representan correctamente desde este HolographicCamera adicional

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>Habilitación de PhotoVideoCamera HolographicViewConfiguration

Para participar, una aplicación simplemente habilita el [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)de PhotoVideoCamera:
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>Control del procesamiento de HolographicCamera adicional en DirectX

Cuando la aplicación tiene participación en la representación de la cámara PV y se inicia la captura de realidad mixta:
1. Se activará el evento CameraAdded de HolographicSpace. Este evento se puede diferir si la aplicación no puede controlar la cámara en este momento.
2. Una vez que se haya completado el evento (y no haya referencias pendientes), el HolographicCamera aparecerá en la lista AddedCameras de HolographicFrame siguiente.

Cuando se detiene la captura de realidad mixta (o si la aplicación deshabilita la configuración de vista mientras se está ejecutando la captura de realidad mixta): HolographicCamera aparecerá en la lista RemovedCameras de HolographicFrame siguiente y el evento CameraRemoved de HolographicSpace. inflama.

Se ha agregado una propiedad [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) a HolographicCamera para ayudar a identificar la configuración a la que pertenece una cámara.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Control del procesamiento de HolographicCamera adicional en Unity

>[!NOTE]
> La compatibilidad de Unity con la presentación de la cámara PV está en desarrollo y aún no se puede usar. Esta documentación se actualizará cuando esté disponible una compilación de Unity que admita la representación desde la cámara PV.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>Comprobar que los sombreadores y el código admiten cámaras adicionales

Ejecutar una captura de realidad mixta y comprobar la alineación inusual, el contenido que falta o los problemas de rendimiento. Actualice los sombreadores y el código según corresponda.

Si hay ciertas escenas que no admiten la representación en una cámara adicional, puede deshabilitar el HolographicViewConfiguration de PhotoVideoCamera durante ellos.

### <a name="disabling-mrc-in-your-app"></a>Deshabilitación de MRC en la aplicación

#### <a name="2d-app"></a>aplicación 2D

las aplicaciones 2D pueden elegir que el contenido visual esté oculto cuando se ejecute la captura de realidad mixta:
* Presente con la marca [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)
* Crear la cadena de intercambio de la aplicación con la marca [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)
* Con la actualización de Windows 10 de mayo de 2019, estableciendo [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) de ApplicationView

#### <a name="immersive-app"></a>Aplicación envolvente

Las aplicaciones envolventes pueden optar por tener el contenido visual excluido de la captura de realidad mixta:
* Configuración de [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) de HolographicCameraRenderingParameter para deshabilitar la captura de realidad mixta para su fotograma asociado
* Configuración de [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) de HolographicCamera para deshabilitar la captura de realidad mixta para su cámara holográfica asociada

#### <a name="password-keyboard"></a>Teclado de contraseña

Con la actualización de Windows 10 de mayo de 2019, el contenido visual se excluye automáticamente de la captura de realidad mixta cuando se ve una contraseña o un teclado de PIN.

### <a name="knowing-when-mrc-is-active"></a>Saber cuándo está activa la MRC

Una aplicación puede usar la clase [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) para saber cuándo se está ejecutando la captura de realidad mixta del sistema (para audio o vídeo).

>[!NOTE]
>La API de [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) de AppCapture puede devolver null si la captura de realidad mixta no está disponible en el dispositivo. También es importante anular el registro del evento CapturingChanged cuando la aplicación está suspendida; de lo contrario, MRC puede entrar en un estado bloqueado.

### <a name="best-practices-hololens-specific"></a>Procedimientos recomendados (específicos de HoloLens)

Se espera que el MRC funcione sin trabajo adicional por parte de los desarrolladores, pero hay algunos aspectos que deben tenerse en cuenta para proporcionar la mejor experiencia de captura de la realidad mixta de la aplicación.

**MRC usa el canal alfa del holograma para combinar con la imagen de la [cámara](locatable-camera.md)**

El paso más importante es asegurarse de que la aplicación se está borrando a negro transparente en lugar de desplazarse al negro opaco. En Unity, esto se realiza de forma predeterminada con el MixedRealityToolkit pero, si está desarrollando en otro lugar, puede que necesite realizar un cambio de una línea.

Estos son algunos de los artefactos que puede ver en MRC si la aplicación no está desactivando el negro transparente:

**Errores de ejemplo**: Bordes negros alrededor del contenido (no se puede borrar a negro transparente)

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

**Errores de ejemplo**: La escena de fondo completa del holograma aparece en negro. Si se establece un valor alfa de fondo de 1, se produce un fondo negro.

![Si se establece un valor alfa de fondo de 1, se produce un fondo negro.](images/clearopaqueblack-300px.png)

**Resultado esperado**: Los hologramas aparecen correctamente combinados con el mundo real (resultado esperado si se borra a negro transparente)

![Resultado esperado si se borra a negro transparente](images/cleartransparentblack-300px.png)

**Solución**:
* Cambie cualquier contenido que se muestre como negro opaco para que tenga un valor alfa de 0.
* Asegúrese de que la aplicación se está borrando a negro transparente.
* De forma predeterminada, Unity se borra para borrar automáticamente con el MixedRealityToolkit, pero si se trata de una aplicación que no es Unity, debe modificar el color usado con ID3D11DeiceContext:: ClearRenderTargetView (). Desea asegurarse de que está claro a negro transparente (0, 0, 0, 0) en lugar de negro opaco (0, 0, 0, 1).

Ahora puede ajustar los valores alfa de sus recursos si lo desea, pero normalmente no es necesario. La mayoría de las veces, MRCs tendrá un aspecto correcto. MRC supone que el alfa se multiplica previamente. Los valores alfa solo afectan a la captura de MRC.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>Qué esperar cuando se habilita MRC en HoloLens

Lo siguiente se aplica tanto a HoloLens (primera generación) como a HoloLens 2, a menos que se indique lo contrario:

* El sistema limitará la aplicación a la representación de 30Hz. Esto crea un espacio para la ejecución de MRC, por lo que la aplicación no necesita mantener una reserva de presupuesto constante y también coincide con el registro de vídeo de MRC fotogramas de 30 fps
* El contenido de hologramas en el ojo adecuado del dispositivo puede parecer "brillar" al grabar y transmitir por secuencias el MRC: el texto puede ser más difícil de leer y los bordes de hologramas pueden parecer más Jaggy (al participar en la tercera cámara en **HoloLens 2** se evita este riesgo).
* Las fotos y los vídeos de MRC respetarán el [punto de enfoque](focus-point-in-unity.md) de la aplicación si la aplicación lo ha habilitado, lo que le ayudará a garantizar que los hologramas se colocan con precisión. En el caso de los vídeos, el punto de enfoque se suaviza para que los hologramas parezcan desplazarse lentamente en su lugar si la profundidad del punto de enfoque cambia significativamente. Los hologramas que se encuentran en diferentes profundidades del punto de enfoque pueden aparecer como desplazamiento desde el mundo real (vea el ejemplo siguiente, donde el punto de enfoque se establece en 2 metros, pero el holograma se coloca en un medidor).

![Los hologramas de 2 metros aparecerán perfectamente registrados en el mundo. Los hologramas en distancias cercanas o Far pueden ser ligeramente desplazamientos.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>Integración de la funcionalidad de MRC desde dentro de la aplicación

La aplicación de realidad mixta puede iniciar la captura de fotos o vídeos de MRC desde dentro de la aplicación y el contenido capturado se pone a disposición de la aplicación sin que se almacene en el "rollo de cámara" del dispositivo. Puede crear una grabadora de MRC personalizada o aprovechar la interfaz de usuario de captura de cámara integrada. 

### <a name="mrc-with-built-in-camera-ui"></a>MRC con interfaz de usuario de cámara integrada

Los desarrolladores pueden usar la *[API de captura de imágenes](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* de la cámara para obtener una foto o vídeo de realidad mixta capturada por el usuario con solo unas pocas líneas de código.

Esta API inicia la interfaz de usuario de la cámara MRC integrada, desde la que el usuario puede tomar una foto o un vídeo, y devuelve la captura resultante a la aplicación.  Si desea crear su propia interfaz de usuario de la cámara, o necesita un acceso de nivel inferior a la secuencia de captura, puede crear una grabadora de captura de realidad mixta.

### <a name="creating-a-custom-mrc-recorder"></a>Creación de una grabadora de MRC personalizada

Aunque el usuario siempre puede desencadenar una foto o un vídeo mediante el servicio de captura de MRC del sistema, es posible que una aplicación quiera compilar una aplicación de cámara personalizada, pero incluir hologramas en el flujo de la cámara como MRC. Esto permite a la aplicación iniciar las capturas en nombre del usuario, compilar una interfaz de usuario de grabación personalizada o personalizar la configuración de MRC para nombrar algunos ejemplos.

**HoloStudio agrega una cámara de MRC personalizada con efectos de MRC**

![HoloStudio agrega una cámara de MRC personalizada con efectos de MRC](images/cameraiconholostudio-300px.jpg)

Las aplicaciones de Unity deben ver [Locatable_camera_in_Unity](locatable-camera-in-unity.md) para que la propiedad habilite los hologramas.

Otras aplicaciones pueden hacerlo mediante el uso de las [API de captura de multimedia de Windows](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) para controlar la cámara y agregar un efecto de vídeo y audio de MRC para incluir los hologramas virtuales y el audio de las aplicaciones en las imágenes y los vídeos.

Las aplicaciones tienen dos opciones para agregar el efecto:
* La API anterior: [Windows. Media. Capture. MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* La nueva API recomendada de Microsoft (devuelve un objeto, lo que permite manipular propiedades dinámicas): [Windows. Media. Capture. mediacapture. AddVideoEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows. Media. Capture. mediacapture. AddAudioEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) que requiere que la aplicación cree su propia implementación de [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) y [ IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition). Vea el ejemplo de efecto de MRC para ver el uso de ejemplo.

>[!NOTE]
> Visual Studio no reconocerá el espacio de nombres Windows. Media. MixedRealityCapture, pero las cadenas seguirán siendo válidas.

Efecto de vídeo de MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  Nombre de la propiedad  |  Type  |  Valor predeterminado  |  Descripción | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (videograbación)  |  Describir en qué secuencia de captura se utiliza este efecto. Audio no disponible. | 
|  HologramCompositionEnabled  |  booleano  |  TRUE  |  Marca para habilitar o deshabilitar los hologramas en la captura de vídeo. | 
|  RecordingIndicatorEnabled  |  booleano  |  TRUE  |  Marca para habilitar o deshabilitar el indicador de grabación en pantalla durante la captura de hologramas. | 
|  VideoStabilizationEnabled  |  booleano  |  FALSE  |  Marca para habilitar o deshabilitar la estabilización de vídeo con el seguimiento de HoloLens. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Establezca el número de fotogramas históricos que se usan para la estabilización de vídeo. 0 es 0-latencia y casi "gratis" desde una perspectiva de eficacia y rendimiento. 15 se recomienda para obtener una mayor calidad (a costa de 15 fotogramas de latencia y memoria). | 
|  GlobalOpacityCoefficient  |  float  |  0,9 (HoloLens) 1,0 (auricular envolvente)  |  Establezca el coeficiente de opacidad global del holograma en el intervalo de 0,0 (totalmente transparente) a 1,0 (totalmente opaco). | 
|  BlankOnProtectedContent  |  booleano  |  FALSE  |  Marca para habilitar o deshabilitar la devolución de un marco vacío si hay una aplicación de UWP 2D que muestra contenido protegido. Si esta marca es falsa y una aplicación de UWP en 2D muestra contenido protegido, la aplicación de UWP de 2D se reemplazará por una textura de contenido protegido tanto en el casco como en la captura de realidad mixta. |
|  ShowHiddenMesh  |  booleano  |  FALSE  |  Marca para habilitar o deshabilitar que muestra la malla de área oculta y el contenido adyacente de la cámara holográfica. |
| Outlocate | Tamaño | 0, 0 | Establezca el tamaño de salida deseado después de recortar para la estabilización de vídeo. Se elige un tamaño de recorte predeterminado si es 0 o se especifica un tamaño de salida no válido. |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | Enumeración que se usa para indicar qué configuración de la vista de cámara holográfica debe capturarse. Establecer 0 (Mostrar) significa que no se pedirá a la aplicación que se represente desde la cámara de fotos o vídeos |

Efecto de audio de MRC (**Windows. Media. MixedRealityCapture. MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>Nombre de la propiedad</th>
<th>Type</th>
<th>Valor predeterminado</th>
<th>Descripción</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0,1 Solo audio MIC</li>
<li>dimensional Solo audio del sistema</li>
<li>dos MIC y audio del sistema</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>Limitaciones de MRC simultáneas

Existen ciertas limitaciones en cuanto a las aplicaciones que acceden a MRC al mismo tiempo.

#### <a name="photovideo-camera-access"></a>Acceso a cámaras de fotos o vídeos

La cámara de foto/vídeo se limita al número de procesos que pueden tener acceso al mismo tiempo. Mientras que un proceso está grabando vídeo o realizando una foto, cualquier otro proceso no podrá adquirir la cámara de fotos o vídeos. (esto se aplica tanto a la captura de realidad mixta como a la captura de foto/vídeo estándar)

Con HoloLens 2, una aplicación puede usar la propiedad [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) de MediaCaptureInitializationSettings para indicar que desea ejecutar SharedReadOnly si no necesitan un control exclusivo sobre la cámara de fotos o vídeos. Si lo hace, la resolución y la velocidad de fotogramas de la captura se limitarán a lo que otras aplicaciones hayan configurado para proporcionar la cámara.

##### <a name="built-in-mrc-photovideo-camera-access"></a>Acceso integrado a cámaras de foto/vídeo de MRC

Funcionalidad de MRC integrada en Windows 10 (a través de Cortana, menú Inicio, métodos abreviados de hardware, Miracast, Windows Device portal):
* Se ejecutará con ExclusiveControl de forma predeterminada

Sin embargo, se ha agregado compatibilidad a cada subsistema para que funcione en modo compartido:
* Si una aplicación solicita acceso de ExclusiveControl a la cámara de fotos o vídeos, el MRC integrado se detendrá automáticamente con la cámara de fotos o vídeos, de modo que la solicitud de la aplicación se realizará correctamente.
* Si el MRC integrado se inicia mientras una aplicación tiene ExclusiveControl, el MRC integrado se ejecutará en modo SharedReadOnly

Esta funcionalidad de modo compartido tiene algunas restricciones:
* Foto a través de Cortana, accesos directos de hardware o menú Inicio: Requiere la actualización 2018 de abril de Windows 10 (o posterior)
* Vídeo a través de Cortana, accesos directos de hardware o menú Inicio: Requiere la actualización 2018 de abril de Windows 10 (o posterior)
* Transmisión por secuencias de MRC en Miracast: Requiere la actualización 2018 de octubre de Windows 10 (o posterior)
* Streaming de MRC en el portal de dispositivos de Windows o a través de la aplicación complementaria de HoloLens: Requiere HoloLens 2

>[!NOTE]
> La resolución y la velocidad de fotogramas de la interfaz de usuario de la cámara MRC integrada pueden reducirse de sus valores normales cuando otra aplicación usa la cámara foto/vídeo.

#### <a name="mrc-access"></a>Acceso a MRC

Con la actualización 2018 de abril de Windows 10, ya no hay una limitación en torno a la existencia de varias aplicaciones que acceden a la secuencia de MRC (sin embargo, el acceso a la cámara de fotos o vídeos todavía tiene limitaciones).

Antes de la actualización del 2018 de abril de Windows 10, la grabadora personalizada de MRC de una aplicación se excluyeba mutuamente con el sistema de MRC (captura de fotografías, captura de vídeos o streaming desde el portal de dispositivos de Windows).

## <a name="see-also"></a>Vea también
* [Captura de realidad mixta](mixed-reality-capture.md)
* [Vista del espectador](spectator-view.md)
