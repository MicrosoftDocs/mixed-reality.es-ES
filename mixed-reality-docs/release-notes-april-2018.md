---
title: 'Notas de la versión: abril 2018'
description: Las notas de la versión de HoloLens y Windows Mixed Reality para la actualización 2018 de abril de Windows 10 (también conocida como RS4).
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: Notas de la versión, versión, Windows 10, compilación, RS4, so
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524174"
---
# <a name="release-notes---april-2018"></a>Notas de la versión: abril 2018

La **[actualización 2018 de abril de Windows 10](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (también conocida como RS4) incluye nuevas características para los auriculares de la realidad de HoloLens y Windows Mixed Reality conectados a equipos. 

Para actualizar a la versión más reciente de cualquier tipo de dispositivo, abra la aplicación de **configuración** , vaya a **Actualizar & seguridad**y, a continuación, seleccione el botón **Buscar actualizaciones** . En un equipo con Windows 10, también puede instalar manualmente la actualización 2018 de abril de Windows 10 mediante la [herramienta de creación de Windows Media](https://www.microsoft.com/software-download/windows10).

**Versión más reciente del escritorio:** Actualización 2018 de abril de Windows 10 (**10.0.17134.1**)<br>
**Versión más reciente de HoloLens:** Actualización 2018 de abril de Windows 10 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Un mensaje de Alex Kipman e información general sobre las nuevas características de realidad mixta en la actualización 2018 de abril de Windows 10*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuevas características para auriculares con Windows Mixed Reality

La actualización 2018 de abril de Windows 10 incluye muchas mejoras en el uso de auriculares con Windows Mixed Reality envolventes (VR) con el equipo de escritorio, como: 

* **Nuevos entornos para la Página principal de la realidad mixta** : ahora puede elegir entre la casa de acantilado y el nuevo entorno de Skyloft seleccionando **lugares** en el menú Inicio. También hemos agregado [una característica experimental](add-custom-home-environments.md) que le permitirá usar los entornos personalizados que ha creado.
* **Acceso rápido a la captura de realidad mixta** : ahora puede tomar fotografías de realidad mixta con un controlador de movimiento. Mantenga presionado el botón de Windows y, a continuación, puntee en el desencadenador. Esto funciona en entornos y aplicaciones, pero no capturará contenido protegido con DRM.
* **Nuevas opciones para iniciar y cambiar el tamaño de contenido** : ahora, las aplicaciones se colocan automáticamente al iniciarlos desde el menú Inicio. También puede cambiar el tamaño de las aplicaciones 2D arrastrando los bordes y las esquinas de la ventana.
* Desplazarse fácilmente por el **contenido con el comando de voz "teletranspórtate"** : ahora puede transportar rápidamente el contenido de la Página principal de Windows Mixed Reality Gazing en el contenido y decir "teletranspórtate".
* Iniciadores **de [aplicaciones 3D animados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) y [objetos 3D decorativos](enable-placement-of-3d-models-in-the-home.md) para la Página principal de realidad mixta** : ahora puede Agregar animación a los iniciadores de aplicaciones 3D y permitir que los usuarios coloquen modelos 3D decorativos de una página web o una aplicación 2D en la Página principal de Windows Mixed Reality.
* **[Mejoras en Windows Mixed Reality para SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md)** : Windows Mixed Reality for SteamVR está fuera del "acceso temprano" con nuevas actualizaciones, entre las que se incluyen comentarios hápticos al usar controladores de movimiento, rendimiento y confiabilidad mejorados y mejoras en el apariencia de los controladores de movimiento en SteamVR.
* **Otras mejoras** : la configuración de rendimiento automática se ha actualizado para proporcionar una experiencia más optimizada (puede invalidar esta configuración [manualmente](#visual-quality) ). Ahora, el programa de instalación proporciona información más detallada acerca de los problemas de compatibilidad comunes con tarjetas gráficas y controladores USB 3,0.

## <a name="new-features-for-hololens"></a>Nuevas características de HoloLens

La actualización 2018 de abril de Windows 10 llegó para todos los clientes de HoloLens. Esta actualización incluye mejoras que se han introducido desde la última versión principal del software HoloLens en agosto de [2016](release-notes-august-2016.md).

### <a name="for-everyone"></a>Para todos

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Colocación automática del contenido 2D y 3D en el inicio</td><td>Un iniciador de aplicaciones 2D o una aplicación UWP de 2D se coloca automáticamente en el mundo con un tamaño y una distancia óptimos cuando se inicia en lugar de solicitar al usuario que lo coloque. Si una <a href="app-views.md">aplicación envolvente</a> usa un iniciador de aplicaciones 2D en lugar de un iniciador de <a href="3d-app-launcher-design-guidance.md">aplicaciones 3D</a>, la aplicación envolvente se iniciará automáticamente desde el iniciador de aplicaciones 2D igual que en RS1.<br><br>Un iniciador de aplicaciones 3D del menú Inicio también coloca automáticamente en el mundo. En lugar de iniciar automáticamente la aplicación, los usuarios pueden hacer clic en el iniciador para iniciar la aplicación envolvente. el contenido 3D que se abre desde la aplicación de hologramas y desde el borde también se coloca automáticamente en el mundo.</td><td>Al abrir una aplicación desde el menú Inicio, ya no se le pedirá que la coloque en el mundo.<br><br>Si la selección de ubicación de la aplicación 2D o del iniciador de<a href="3d-app-launcher-design-guidance.md">aplicaciones 3D</a> no es óptima, puede moverlas fácilmente mediante las nuevas manipulaciones de aplicaciones fluidas que se describen a continuación. También puede volver a colocar el selector de aplicación 2D o el contenido 3D indicando "mover esto" y, a continuación, usando fijamente para volver a colocar el contenido.</td>
  </tr>
  <tr>
    <td>Manipulación de aplicaciones fluidas</td><td>Mueva, cambie de tamaño y gire contenido 2D y 3D sin tener que escribir el modo "ajustar".</td><td>Para trasladar una aplicación para UWP 2D o un iniciador de aplicaciones en 2D, simplemente mira en la barra de la aplicación y, después, usa el gesto pulsar + mantener + arrastrar. Puede trasladar contenido 3D Gazing en cualquier lugar del objeto y, a continuación, usar TAP + Hold + arrastrar.<br><br>Para cambiar el tamaño del contenido 2D, mira en su esquina. El cursor de mira hacia abajo se convertirá en un cursor de cambio de tamaño y, a continuación, puede pulsar + mantener + arrastrar para cambiar el tamaño. También puede hacer que el contenido 2D sea más alto o más amplio mirando los bordes y arrastrando.<br><br>Para cambiar el tamaño del contenido 3D, suba el marco de gestos hacia arriba en la posición listo. Verá que el cursor se convierte en un estado con dos manos. Realice el gesto de pulsar y sostener con las manos. Si mueve las manos más o menos lejos, cambiará el tamaño del objeto. Si mueve las manos hacia delante y hacia atrás con respecto a otras, girará el objeto. También puede cambiar el tamaño del contenido 2D y girarlo de esta manera.</td>
  </tr>
  <tr>
    <td>tamaño horizontal de la aplicación 2D con reflujo</td><td>Haga que una aplicación de UWP 2D sea más ancha en relación de aspecto para ver más contenido de la aplicación. Por ejemplo, hacer que la aplicación de correo sea lo suficientemente ancha para mostrar el panel de vista previa.</td><td>Simplemente miramos en el borde izquierdo o derecho de la aplicación de UWP 2D para ver el cursor de cambiar el tamaño y, a continuación, usar el gesto de soltar y mantener presionado + arrastrar para cambiar el tamaño.</td>
  </tr>
  <tr>
    <td>Compatibilidad ampliada con los comandos de voz</td><td>Puede usar la voz con más facilidad.</td><td>Pruebe estos comandos de voz:<ul><li>"Ir a Inicio": abre el menú Inicio o sale de una <a href="app-views.md">aplicación envolvente</a>.</li><li>"Move this": permite desplace un objeto.</li></ul></td>
  </tr>
  <tr>
    <td>Aplicaciones de hologramas y fotos actualizadas</td><td>Aplicación de hologramas actualizada con nuevos hologramas. Aplicación fotos actualizada.</td><td>Observará que se ha actualizado la apariencia de las aplicaciones de hologramas y fotos. La aplicación de hologramas incluye varios hologramas nuevos y un creador de etiquetas para facilitar la creación de texto.</td>
  </tr>
  <tr>
    <td>Captura de realidad mixta mejorada</td><td>Vídeo de inicio y fin de acceso directo de hardware.</td><td>Mantenga el volumen activo + abajo durante 3 segundos para empezar a grabar vídeo de MRC. Pulse de nuevo o use el gesto de floración para finalizar.</td>
  </tr>
  <tr>
    <td>Espacios consolidados</td><td>Simplifique la administración del espacio para los hologramas en un solo espacio.</td><td>HoloLens encuentra el espacio automáticamente y ya no requiere que administre o seleccione espacios. Si tiene problemas con los hologramas, puede ir a <b>configuración > del sistema > hologramas > quitar los hologramas cercanos</b>. Si es necesario, también puede seleccionar <b>quitar todos los hologramas</b>.</td>
  </tr>
  <tr>
    <td>Inmersión de audio mejorada</td><td>Ahora puede oír de HoloLens mejor en entornos ruidosos y experimentar un sonido más realista de las aplicaciones, ya que su sonido quedará oculto en las paredes reales detectadas por el dispositivo.</td><td>No tiene que hacer nada para disfrutar del sonido espacial mejorado.</td>
  </tr>
  <tr>
    <td>Explorador de archivos</td><td>Mueva y elimine archivos desde HoloLens.</td><td>Puede usar la aplicación <b>Explorador de archivos</b> para trasladar y eliminar archivos desde HoloLens.<br><br><b>Sugerencia:</b> Si no ve ningún archivo, el filtro "reciente" puede estar activo (el icono de reloj está resaltado en el panel izquierdo). Para corregirlo, seleccione el icono de este documento de <b>dispositivo</b> en el panel izquierdo (debajo del icono de reloj) o abra el menú y seleccione <b>este dispositivo</b>.
</td>
  </tr>
  <tr>
    <td>Compatibilidad con MTP (Protocolo de transferencia multimedia)</td><td>Permite que el equipo de escritorio acceda a las bibliotecas (fotos, vídeos, documentos) en HoloLens para facilitar la transferencia.</td><td>De forma similar a otros dispositivos móviles, conecte su HoloLens a su equipo para abrir el <b>Explorador de archivos</b> para acceder a las bibliotecas de hololens (fotos, vídeos, documentos) para facilitar la transferencia.<br><br><b>Útiles</b><ul><li>Si no ve ningún archivo, asegúrese de que inicia sesión en HoloLens para permitir el acceso a los datos.</li><li>En el <b>Explorador de archivos</b> del equipo, puede seleccionar <b>propiedades del dispositivo</b> para ver el número de versión del sistema operativo Windows Holographic (versión de firmware) y el número de serie del dispositivo.</li></ul><b>Problema conocido:</b> El cambio de nombre de HoloLens a través del <b>Explorador de archivos</b> en el equipo no está habilitado.</td>
  </tr>
  <tr>
    <td>Compatibilidad con la red del portal cautivo durante la instalación</td><td>Ahora puede configurar HoloLens en una red invitada en hoteles, centros de conferencias, tiendas minoristas o empresas que usan el portal cautivo.</td><td>Durante la instalación, seleccione la red, Active conectar automáticamente si lo desea y escriba la información de la red cuando se le solicite.</td>
  </tr>
  <tr>
    <td>Sincronización de fotos y vídeos a través de la aplicación OneDrive</td><td>Las fotos y los vídeos de HoloLens se sincronizarán ahora a través de la aplicación de OneDrive desde el Microsoft Store en lugar de hacerlo directamente a través de la aplicación fotos.</td><td>Para configurarlo, descargue e inicie la aplicación OneDrive desde la tienda. En la primera ejecución, se le pedirá que cargue automáticamente las fotos en OneDrive, o bien que encuentre la opción en la configuración de la aplicación.</td>
  </tr>
</table>

### <a name="for-developers"></a>Para desarrolladores

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Mejoras en la asignación espacial</td><td>Mejoras en la calidad, la simplificación y el rendimiento.</td><td>La malla de asignación espacial aparecerá en el limpiador; se requieren menos triángulos para representar el mismo nivel de detalle. Es posible que observe cambios en la densidad de los triángulos de la escena.</td>
  </tr>
  <tr>
    <td>Selección automática del punto de enfoque basado en el búfer de profundidad</td><td>El envío de un búfer de profundidad a Windows permite a HoloLens seleccionar automáticamente un punto de enfoque para optimizar la estabilidad del holograma.</td><td>En Unity, vaya a <b>editar > configuración del proyecto > Player > plataforma universal de Windows pestaña > XR configuración</b>, expanda el elemento <b>SDK de Windows Mixed Reality</b> y asegúrese de que esté activada la opción <b>Habilitar uso compartido de búfer de profundidad</b> . Se comprobará automáticamente si hay nuevos proyectos.<br><br>En el caso de las aplicaciones de DirectX, asegúrese de llamar al método <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a> en <b>HolographicRenderingParameters</b> cada fotograma para proporcionar el búfer de profundidad a Windows.
</td>
  </tr>
  <tr>
    <td>Modos de reproyecto Holographic</td><td>Ahora puede deshabilitar la Reproyección posicional en HoloLens para mejorar la estabilidad del holograma del contenido rígidomente bloqueado por cuerpo, como el vídeo de 360 grados.</td><td>En Unity, establezca <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings. ReprojectionMode</a> en <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode. OrientationOnly</a> cuando todo el contenido de la vista esté rígidomente bloqueado por el cuerpo.<br><br>En el caso de las aplicaciones de DirectX, establezca <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">HolographicCameraRenderingParameters. ReprojectionMode</a> en <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode. OrientationOnly</a> cuando todo el contenido de la vista esté bloqueado rígidamente por el cuerpo.</td>
  </tr>
  <tr>
    <td>API de personalización de aplicaciones</td><td>Las API de Windows saben más sobre dónde se ejecuta la aplicación, por ejemplo, si la pantalla del dispositivo es transparente (HoloLens) o opaca (casco envolvente) y si la vista 2D de una aplicación para UWP aparece en el shell de Holographic.</td><td>Unity había expuesto previamente <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings. IsDisplayOpaque</a> de forma que funcionase incluso antes de esta compilación.<br><br>En el caso de las aplicaciones de DirectX, ahora puede acceder a las API existentes como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay. GetDefault (). IsOpaque</a> y <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview. IsCurrentViewPresentedOnHolographicDisplay</a> también en HoloLens.
</td>
  </tr>
  <tr>
      <td>Modo de investigación</td><td>Permite a los desarrolladores tener acceso a los sensores clave de HoloLens al compilar aplicaciones académicas e industriales para probar nuevas ideas en los campos de la visión informática y robótica, incluidos:<ul><li>Las cuatro cámaras de seguimiento del entorno</li><li>Dos versiones de los datos de la cámara de asignación de profundidad</li><li>Dos versiones de una secuencia IR-reflectividad</li></ul></td><td><a href="research-mode.md">Documentación del modo de investigación</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Aplicaciones de ejemplo de modo de investigación</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Para clientes comerciales

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Usar varias cuentas de usuario de Azure Active Directory en un solo dispositivo</td><td>Comparta un HoloLens con varios Azure AD usuarios, cada uno con su propia configuración de usuario y datos de usuario en el dispositivo.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">Centro de profesionales de TI: Compartir HoloLens con varias personas</a></td>
  </tr>
  <tr>
    <td>Cambiar la red Wi-Fi en el inicio de sesión</td><td>Cambiar la red Wi-Fi antes del inicio de sesión para permitir que otro usuario inicie sesión con su cuenta de usuario de Azure AD por primera vez, lo que permite a los usuarios compartir dispositivos en diversas ubicaciones y sitios de trabajo.</td><td>En la pantalla de inicio de sesión, puede usar el icono red situado debajo del campo contraseña para conectarse a una red. Esto resulta útil cuando se trata de la primera vez que inicia sesión en un dispositivo.</td>
  </tr>
  <tr>
    <td>Inscripción unificada</td><td>Ahora es fácil para un usuario de HoloLens que configure el dispositivo con un cuenta de Microsoft personal agregar una cuenta profesional (Azure AD) y unir el dispositivo a su servidor MDM.</td><td>Simplemente inicie sesión con una cuenta de Azure AD y la inscripción se realiza automáticamente.</td>
  </tr>
  <tr>
    <td>Sincronización de correo sin inscripción de MDM</td><td>Compatibilidad con la sincronización de correo de Exchange Active Sync (EAS) sin requerir la inscripción de MDM.</td><td>Ahora puede sincronizar el correo electrónico sin inscribirse en MDM. Puede configurar el dispositivo con una cuenta Microsoft, descargar e instalar la aplicación mail y agregar una cuenta de correo electrónico profesional directamente.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>para profesionales de TI

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Nuevo nombre del sistema operativo de Windows Holographic for Business</td><td>Borre el nombre de la edición para reducir la confusión en la aplicación de licencias de actualización de edición cuando se habilitan las características del conjunto comercial en HoloLens.</td><td>Puede ver qué edición de Windows Holographic está en el dispositivo en <b>configuración > sistema > acerca</b>de. "Windows Holographic for Business" aparecerá si se ha aplicado una actualización de edición para habilitar las características de Commercial Suite. Obtenga información acerca <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">de cómo desbloquear características de Windows Holographic for Business</a>.</td>
  </tr>
  <tr>
  <td>Diseñador de configuración de Windows (WCD)</td><td>Cree y edite paquetes de aprovisionamiento para configurar HoloLens a través de la aplicación WCD actualizada. Asistente simple de HoloLens para la actualización de edición, OOBE configurable, zona horaria, región, token de Azure AD masivo, red y CSP del desarrollador. Editor avanzado filtrado para las opciones admitidas por HoloLens, incluidos los CSP asignados de administración de cuentas y acceso.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profesionales de TI: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
    <td>Instalación configurable (OOBE)</td><td>Oculte la calibración, el entrenamiento de gestos y miramientos y las pantallas de configuración de Wi-Fi durante la instalación.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">Centro de profesionales de TI: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
    <td>Compatibilidad con tokens de Azure AD masiva</td><td>Registre previamente el dispositivo en Azure AD inquilino de directorio para un flujo de configuración de usuario más rápido.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profesionales de TI: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>Implemente el perfil para configurar HoloLens en modo de desarrollador. Útil para dispositivos de desarrollo y demostración.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profesionales de TI: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>Compartir un dispositivo HoloLens y quitar los datos de usuario después del cierre de sesión o los umbrales de inactividad/almacenamiento para uso temporal. Admite cuentas Azure AD.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">Centro de profesionales de TI: Configuración de HoloLens mediante un paquete de aprovisionamiento</a></td>
  </tr>
  <tr>
  <td>Acceso asignado</td><td>Windows ha asignado acceso a los trabajadores de primera línea o demostraciones. Bloqueo de una o varias aplicaciones. No es necesario desbloquear el desarrollador.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">Centro de profesionales de TI: Configuración de HoloLens en el modo de pantalla completa</a></td>
  </tr>
  <tr>
  <td>Acceso de invitado para dispositivos de quiosco</td><td>Windows ha asignado acceso con una cuenta de invitado sin contraseña para demostraciones. Bloqueo de una o varias aplicaciones. No es necesario desbloquear el desarrollador.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">Centro de profesionales de TI: Configuración de HoloLens en el modo de pantalla completa</a></td>
  </tr>
  <tr>
    <td>Configuración de diagnósticos (OOBE)</td><td>Obtenga registros de diagnóstico de HoloLens para que pueda solucionar problemas de Azure AD errores de inicio de sesión (antes de que el centro de comentarios esté disponible para el usuario cuyo inicio de sesión ha producido un error).</td><td>Cuando se produce un error en la instalación o el inicio de sesión, elija la opción nueva <b>recopilación de información</b> para obtener registros de diagnóstico para la solución de problemas.</td>
  </tr>
  <tr>
    <td>Expiración de contraseña indefinida de cuenta local</td><td>Quitar la interrupción del restablecimiento del dispositivo cuando expira la contraseña de la cuenta local.</td><td>Al aprovisionar una cuenta local, ya no es necesario cambiar la contraseña cada 42 días en la <b>configuración</b>, ya que la contraseña de la cuenta ya no expira.</td>
  </tr>
  <tr>
    <td>Estado y detalles de sincronización de MDM</td><td>Funcionalidad estándar de Windows para comprender el estado y los detalles de sincronización de MDM desde HoloLens.</td><td>Puede comprobar el estado de sincronización de MDM para un dispositivo en <b>configuración > cuentas > acceder al trabajo o la escuela > información</b>. En la <b>sección estado<b> de sincronización de dispositivos, puede iniciar una sincronización, ver las áreas administradas por MDM y crear y exportar un informe de diagnóstico avanzado.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado mucho para ofrecer una excelente experiencia de realidad mixta de Windows, pero todavía estamos realizando un seguimiento de algunos problemas conocidos. Si encuentra otras personas, envíenos [sus comentarios](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Después de la actualización

Es posible que observe los siguientes problemas después de actualizar de RS1 a RS4 en HoloLens:
* **Restablecimiento de PIN** : las aplicaciones de 3x3 ancladas al menú Inicio se restablecerán a los valores predeterminados después de la actualización. 
* Las **aplicaciones y** los hologramas colocados se restablecen: las aplicaciones colocadas en su mundo se quitarán después de la actualización y habrá que volver a colocarlas en todo el espacio. 
* **Es posible que el centro de comentarios no se inicie inmediatamente** : inmediatamente después de la actualización, tardará unos minutos antes de poder iniciar algunas aplicaciones de bandeja de entrada, como el centro de comentarios, mientras se actualizan. 
* **Es necesario volver a sincronizar los certificados de Wi-Fi corporativos** : estamos investigando un problema que requiere que HoloLens esté conectado a una red diferente para que los certificados corporativos se vuelvan a sincronizar con el dispositivo antes de poder volver a conectarse a la empresa. redes que usan certificados. 
* La **reproducción de vídeo h. 265 HEVC no funciona** : las aplicaciones que intentan reproducir H. 265 vídeos recibirán un mensaje de error. La solución alternativa es [acceder al portal de dispositivos de Windows](using-the-windows-device-portal.md), seleccionar **aplicaciones** en la barra de navegación izquierda y **quitar** la aplicación HEVC. A continuación, instale la [extensión de vídeo HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) más reciente desde el Microsoft Store. Estamos investigando el problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Para desarrolladores: actualización de aplicaciones de HoloLens para dispositivos que ejecutan la actualización 2018 de abril de Windows 10

Junto con una excelente lista de [características nuevas](#new-features-for-hololens), la actualización 2018 de abril de Windows 10 (RS4) para HoloLens exige algunos comportamientos de código que las versiones anteriores no:
* **Solicitudes de permiso para usar recursos confidenciales (cámara, micrófono, etc.)** -RS4 en HoloLens aplicará solicitudes de permisos para las aplicaciones que tengan acceso a recursos confidenciales, como la cámara o el micrófono. RS1 en HoloLens no aplicó estos mensajes, por lo que si la aplicación asume el acceso inmediato a estos recursos, puede bloquearse en RS4 (aunque el usuario conceda permiso al recurso solicitado). Para obtener más información, consulte el artículo de declaraciones de funcionalidades de la [aplicación UWP](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) pertinente.
* Las **llamadas a aplicaciones fuera de su propio** RS4 en HoloLens aplicarán el uso correcto de la [clase *Windows. System. Launcher* ](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) para iniciar otra aplicación a partir de la suya propia. Por ejemplo, se han detectado problemas con aplicaciones que llaman a *Windows. System. Launcher. LaunchUriForResultsAsync* desde un subproceso que no es asta (UI). Esto se realizará correctamente en RS1 en HoloLens, pero RS4 requiere que la llamada se ejecute en el subproceso de la interfaz de usuario.

### <a name="windows-mixed-reality-on-desktop"></a>Windows Mixed Reality en escritorio

#### <a name="visual-quality"></a>Calidad visual

* Si observa que una vez que la actualización de Windows 10 de abril de 2018 los gráficos son más borrosos que antes, o que el campo de la vista es más pequeño en el casco, puede que se haya cambiado la configuración de rendimiento automática para mantener una velocidad de fotogramas suficiente en una operación menos eficaz. tarjeta gráfica (como NVIDIA 1050). Puede invalidar esta opción manualmente (si lo desea). para ello, vaya a **configuración > realidad mixta > > Opciones de experiencia > cambiar** y cambie "automático" a "90 Hz". También puede intentar cambiar la **calidad visual** (en la misma página de configuración) a "alta".

#### <a name="windows-mixed-reality-setup"></a>Configuración de Windows Mixed Reality

* Al configurar Windows con un auricular conectado, el monitor de PC puede dejar de estar en blanco. Desenchufe los auriculares para habilitar la salida en el monitor de PC para completar la instalación de Windows.
* Si no tiene auriculares conectados, es posible que se pierdan sugerencias adicionales cuando visite por primera vez la Página principal de Windows Mixed Reality.
* Otros dispositivos Bluetooth pueden producir interferencias con los controladores de movimiento. Si los controladores de movimiento tienen problemas de conexión/emparejamiento/seguimiento, asegúrese de que la radio Bluetooth (si se trata de una llave externa) esté conectada a una ubicación no obstaculizada y no inmediatamente después de otra llave Bluetooth. Intente también apagar otros periféricos Bluetooth durante las sesiones de realidad mixta de Windows para ver si ayuda.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Juegos y aplicaciones del Microsoft Store

* Algunos juegos con un uso intensivo de gráficos, como Forza Motorsport 7, pueden provocar problemas de rendimiento en equipos menos compatibles cuando se reproducen dentro de Windows Mixed Reality.

#### <a name="audio"></a>Audio

* Si tiene Cortana habilitada en el equipo host antes de usar el casco de realidad mixta de Windows, puede perder la simulación de sonido espacial que se aplica a las aplicaciones que se colocan en la Página principal de Windows Mixed Reality. 
   * La solución consiste en habilitar "Sonic de Windows para auriculares" en todos los dispositivos de audio conectados al equipo, incluso en el dispositivo de audio conectado con auriculares:
      1. Haga clic con el botón izquierdo en el icono de altavoz de la barra de tareas del escritorio y seleccione de la lista de dispositivos de audio.
      2. Haga clic con el botón secundario en el icono de altavoz de la barra de tareas del escritorio y seleccione "Windows Sonic para auriculares" en el menú "configuración del altavoz".
      3. Repita estos pasos para todos los dispositivos de audio (puntos de conexión).
   * Otra opción es desactivar "permitir que Cortana responda a Hola Cortana" en **configuración** > **Cortana** en el escritorio antes de iniciar Windows Mixed Reality.
* Cuando otro dispositivo USB multimedia (como una cámara web) comparte el mismo concentrador USB (ya sea externo o dentro de su PC) con el casco de realidad mixta de Windows, en raras ocasiones, es posible que el Jack o los auriculares de audio del casco tengan un sonido sonoro o que no haya audio. Puede corregirlo mediante los auriculares en un puerto USB que no comparta el mismo concentrador que el otro dispositivo o desconectar o deshabilitar el otro dispositivo multimedia USB.
* En raras ocasiones, el concentrador USB del equipo host no puede proporcionar suficiente energía para los auriculares de la realidad mixta de Windows y es posible que observe una ráfaga de ruido de los auriculares conectados al casco.

#### <a name="holograms"></a>Hologramas

* Si ha colocado un gran número de hologramas en su página principal de Windows Mixed Reality, algunos pueden desaparecer y volver a aparecer mientras busca. Para evitar esto, quite algunos de los hologramas en esa área de la Página principal de Windows Mixed Reality.

#### <a name="motion-controllers"></a>Controladores de movimiento

* Si la entrada no se enruta al casco, el controlador de movimiento desaparecerá brevemente al mantenerse junto al límite de la habitación. Si presiona Win + Y para asegurarse de que hay un banner azul en el monitor de escritorio, resolverá este error. 
* En ocasiones, al hacer clic en una página web en Microsoft Edge, el contenido se acercará en lugar de hacer clic en él.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicación de escritorio en la Página principal de Windows Mixed Reality

* Recortes no funciona en la aplicación de escritorio.
* La configuración de la aplicación de escritorio no se mantiene al volver a iniciarla.
* Si usa la versión preliminar del portal de realidad mixta en el escritorio, al abrir la aplicación de escritorio en la Página principal de Windows Mixed Reality, es posible que observe el efecto de reflejo infinito. 
* La ejecución de la aplicación de escritorio puede producir problemas de rendimiento en equipos que no son de alta calidad de Windows. no se recomienda.  
* La aplicación de escritorio puede iniciarse automáticamente porque una ventana invisible en el escritorio tiene el foco. 
* El aviso de control de cuentas de usuario de escritorio hará que el casco se muestre en negro hasta que se complete el aviso.

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed Reality para SteamVR

* Es posible que tenga que iniciar el portal de realidad mixta después de la actualización para asegurarse de que las actualizaciones de software necesarias para la actualización de abril 2018 de Windows 10 se han completado antes de iniciar SteamVR. 
* Debe estar en una versión reciente de Windows Mixed Reality para que SteamVR siga siendo compatible con la actualización 2018 de abril de Windows 10. Asegúrese de que las actualizaciones automáticas están activadas para Windows Mixed Reality para SteamVR, que se encuentra en la sección "software" de la biblioteca en vapor.  

#### <a name="other-issues"></a>Otros problemas

>[!IMPORTANT]
>A una versión anterior de la actualización de abril 2018 de Windows 10 que se insertó en Insiders (versión 17134,5) le faltaba parte del software necesario para ejecutar Windows Mixed Reality. Se recomienda evitar esta versión si se usa Windows Mixed Reality. 

Hemos identificado una regresión de rendimiento al usar Surface Book 2 en la versión inicial de esta actualización (10.0.17134.1) que estamos trabajando para corregir en una próxima revisión de actualización. Se recomienda esperar hasta que se haya corregido antes de actualizar manualmente o esperar a que la actualización se implemente con normalidad.

## <a name="provide-feedback-and-report-issues"></a>Proporcionar comentarios e informar de problemas

Use la [aplicación de centro de comentarios en su equipo HoloLens o Windows 10](give-us-feedback.md) para proporcionar comentarios e informar de problemas. El uso del centro de comentarios garantiza que se incluye toda la información de diagnóstico necesaria para ayudar a nuestros ingenieros a depurar y resolver el problema rápidamente.

>[!NOTE]
>Asegúrese de aceptar el mensaje que le pregunta si desea que el centro de comentarios tenga acceso a la carpeta de documentos (seleccione **sí** cuando se le solicite).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Compatibilidad con auriculares envolvente (vínculo externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Compatibilidad con HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalación de las herramientas](install-the-tools.md)
* [Comentarios](give-us-feedback.md)

