---
title: Mixto captura realidad para desarrolladores
description: Procedimientos recomendados para la realidad mixta de captura para desarrolladores.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: MRC, fotos, vídeo, captura, cámara
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599457"
---
# <a name="mixed-reality-capture-for-developers"></a>Mixto captura realidad para desarrolladores

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes). 

Consulte [MRC habilitar en su aplicación](#enabling-mrc-in-your-app) a continuación para obtener orientación sobre una nueva funcionalidad MRC de HoloLens 2.

Puesto que un usuario podría llevar a cabo una [mixto captura realidad](mixed-reality-capture.md) foto (MRC) o de vídeo en cualquier momento, hay algunas cosas que debe tener en cuenta al desarrollar la aplicación. Esto incluye procedimientos recomendados para la calidad visual MRC y poder reaccionar a los cambios del sistema mientras se están capturando MRCs.

Los desarrolladores pueden integrar perfectamente también captura la realidad mixta y la inserción en sus aplicaciones.

MRC en HoloLens (primera generación) es compatible con vídeos y fotos hasta 720p, mientras que MRC en HoloLens 2 admite vídeos hasta 1.080 p y fotos hasta resolución de 4 K.

## <a name="the-importance-of-quality-mrc"></a>La importancia de calidad MRC

Realidad mixta captura fotos y vídeos son probablemente la primera exposición que tendrá un usuario de la aplicación. Si, como capturas de pantalla de realidad mixta en la página de Microsoft Store o a otros usuarios compartidos MRCs en redes sociales. Puede usar MRC para su aplicación de demostración, educar a los usuarios, animamos a los usuarios compartir sus interacciones mixto del mundo y de investigación de usuario y la resolución de problemas.

## <a name="how-mrc-impacts-your-app"></a>Cómo MRC afecta a la aplicación

### <a name="enabling-mrc-in-your-app"></a>Habilitar MRC en la aplicación

De forma predeterminada, una aplicación no tiene que hacer nada para permitir que los usuarios a tomar capturas de realidad mixta. Sin embargo, dado que el diseño de HoloLens 2 aumenta la distancia entre la cámara de vídeo/fotos (PV) y la presentación, presentaremos una nueva opción para generar una representación de cámara 3rd alineada a la cámara PV de **HoloLens 2**. 

Participar en la cámara 3rd se representan en HoloLens 2 ofrece las siguientes mejoras a través de la experiencia MRC predeterminada:
* Alineación holograma a su entorno físico y el alcance (para las interacciones de casi) debe ser precisa en absoluto las distancias, en lugar de tener un desplazamiento a una distancia distinto el [centrarse punto](focus-point-in-unity.md) como puede ver en el valor predeterminado MRC.
* El efecto de ojos derecha en los auriculares no se pongan en peligro, ya que no se utiliza para representar el hologramas para la salida MRC.

### <a name="disabling-mrc-in-your-app"></a>Deshabilitar MRC en la aplicación

Cuando se usa una aplicación 2D [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) o [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) para mostrar el contenido protegido con una cadena de intercambio configurado correctamente, será contenido visual de la aplicación se oculta automáticamente mientras se está ejecutando la captura de realidad mixta.

### <a name="knowing-when-mrc-is-active"></a>Saber cuándo MRC está activo

El [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) clase puede utilizarse por una aplicación para saber cuando se ejecuta el sistema mixto captura realidad (para audio o vídeo).

>[!NOTE]
>Del AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API puede devolver null si se combina con captura de la realidad no está disponible en el dispositivo. También es importante eliminar del registro el evento CapturingChanged cuando se suspende la aplicación, en caso contrario, puede obtener MRC en un estado bloqueado.

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

Otras aplicaciones pueden hacerlo mediante la [las API de captura de Windows Media](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) para controlar la cámara y agregar un efecto de Audio y vídeo MRC para incluir hologramas virtuales y el audio de la aplicación en imágenes fijas y vídeos.

Las aplicaciones tienen dos opciones para agregar el efecto:
* La API anterior: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* El nuevo Microsoft recomienda API (devuelve un objeto, lo que permite manipular las propiedades dinámicas): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) que requieren la aplicación cree su propia implementación de [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) y [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx). Consulte el ejemplo de efecto MRC para ejemplo de uso.

(Tenga en cuenta que Visual Studio no reconocerá estos espacios de nombres, pero las cadenas siguen siendo válidas)

Efecto de vídeo MRC (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  Nombre de la propiedad  |  Tipo  |  Valor predeterminado  |  Descripción | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  Describir qué secuencia de captura este efecto se utiliza para. Audio no está disponible. | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  Marca para habilitar o deshabilitar hologramas en la captura de vídeo. | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  Marca para habilitar o deshabilitar el indicador de grabación de pantalla durante holograma de captura. | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la estabilización de vídeo con la tecnología de la herramienta de seguimiento de HoloLens. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  Establecer el número de marcos histórico se usa para la estabilización de vídeo. 0 es la latencia de 0 y casi "gratuita" desde una perspectiva de capacidad y rendimiento. se recomienda 15 para calidad más alta (a costa de 15 fotogramas de latencia y memoria). | 
|  GlobalOpacityCoefficient  |  flotante  |  0,9 (HoloLens) 1.0 (envolventes auriculares)  |  Establecer coeficiente de opacidad global de holograma en el intervalo comprendido entre 0,0 (completamente transparente) a 1.0 (totalmente opaco). | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar la devolución de un marco vacío si no hay un contenido protegido que muestra de aplicación UWP 2d. Si esta marca es false y una 2d aplicación para UWP es mostrando protegido contenido, que la aplicación para UWP 2d se reemplazará por una textura de contenido protegida en los auriculares con micrófono y en la captura de realidad mixta. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  Marca para habilitar o deshabilitar que muestra la malla de la cámara holográfica área oculta y los vecinos de contenido. |

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

Con Windows 10 de abril de 2018 actualización, esta restricción no se aplica si la cámara integrada MRC la interfaz de usuario se usa para tomar una foto o grabar un vídeo después de que ha iniciado una aplicación con la cámara de vídeo y fotos. Cuando esto sucede, pueden reducirse la velocidad de fotogramas de la cámara integrada de MRC la interfaz de usuario y la resolución de sus valores normales.

Con Windows 10 de octubre de 2018 actualización, esta restricción no es aplicable a MRC de transmisión por secuencias a través de Miracast.

#### <a name="mrc-access"></a>Acceso MRC

Con Windows 10 de abril de 2018 actualización, ya no hay una limitación en torno a varias aplicaciones de acceso a la secuencia MRC (sin embargo, el acceso a la cámara de vídeo y fotos todavía tiene limitaciones).

Anterior a Windows 10 de abril de 2018 actualización, la grabadora de una aplicación personalizada MRC era es mutuamente excluyente con sistema MRC (captura de fotografías, capturar vídeos o transmisión por secuencias desde la de Windows Device Portal).

## <a name="see-also"></a>Vea también
* [Captura de realidad mixta](mixed-reality-capture.md)
* [Vista del espectador](spectator-view.md)
