---
title: Notas de la versión - abril de 2018
description: HoloLens y notas de la versión de Windows Mixed Reality para Windows 10 de abril de 2018 actualización (también conocido como RS4).
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: release notes, versión, windows 10, compilación, rs4, sistema operativo
ms.openlocfilehash: 1fc1b43b0581234e835379fd553b78121108086e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600907"
---
# <a name="release-notes---april-2018"></a>Notas de la versión - abril de 2018

El **[Windows 10 de abril de 2018 Update](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (también conocido como RS4) incluye nuevas características para HoloLens y Windows Mixed Reality inmersivos conectados a PC. 

Para actualizar a la versión más reciente de cualquier tipo de dispositivo, abra el **configuración** aplicación, vaya a **actualización y seguridad**, a continuación, seleccione el **buscar actualizaciones** botón. En un equipo con Windows 10, puede instalar manualmente Windows 10 de abril de 2018 actualizar mediante el [herramienta de creación de Windows media](https://www.microsoft.com/software-download/windows10).

**Última versión de escritorio:** Actualización de Windows 10 de abril de 2018 (**10.0.17134.1**)<br>
**Versión más reciente para HoloLens:** Actualización de Windows 10 de abril de 2018 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Actualización de un mensaje de información general de nuevas características de realidad mixta en las ventanas y Alex Kipman 10 de abril de 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuevas características para inmersivos Windows Mixed Reality

Windows 10 de abril de 2018 Update incluye muchas mejoras para usar auriculares de Windows Mixed Reality envolventes (VR) con su PC de escritorio, como: 

* **Nuevos entornos para el inicio de realidad mixta** : ahora puede elegir entre el Cliff House y el nuevo entorno Skyloft seleccionando **lugares** en el menú Inicio. También hemos agregado [una característica experimental](add-custom-home-environments.md) que le permitirá usar entornos personalizados que ha creado.
* **Acceso rápido a la captura de realidad mixta** -ahora pueden aprovechar las fotos de realidad mixta mediante un controlador de movimiento. Mantenga presionado el botón de Windows y, a continuación, puntee en el desencadenador. Esto funciona en entornos y las aplicaciones, pero no capturará el contenido protegido con DRM.
* **Nuevas opciones para iniciar y cambiar el tamaño de contenido** -aplicaciones ahora se colocan automáticamente delante de usted al iniciar desde el menú Inicio. Ahora también puede cambiar el tamaño de las aplicaciones 2D arrastrando los bordes y esquinas de la ventana.
* **Saltar fácilmente al contenido con el comando de voz "teleport"** : ahora puede rápidamente teleport para estar delante de contenido en el inicio de Windows Mixed Reality gazing en contenido y que dice "teleport."
* **[Animar los iniciadores de aplicaciones 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#animation-guidelines) y [decorativos objetos 3D](enable-placement-of-3d-models-in-the-home.md) para el inicio de realidad mixta** : ahora puede agregar animación a los iniciadores de aplicaciones 3D y permitir a los usuarios que coloquen decorativos modelos 3D desde una aplicación de página Web o 2D en el Windows Mixed Reality principal.
* **[Mejoras en Windows Mixed Reality for SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md)**  -Windows Mixed Reality para SteamVR está fuera de "acceso prioritario" con las actualizaciones nuevas, incluida: comentarios hápticos al usar controladores de movimiento, mejorar el rendimiento y confiabilidad, y mejoras en la apariencia de los controladores de movimiento en SteamVR.
* **Otras mejoras** -configuración de rendimiento automáticas se han actualizado para proporcionar una experiencia más optimizada (puede [invalidar manualmente](#visual-quality) esta configuración). Programa de instalación ahora proporciona más información sobre problemas comunes de compatibilidad con tarjetas USB 3.0 de los controladores y los gráficos.

## <a name="new-features-for-hololens"></a>Nuevas características para HoloLens

Windows 10 de abril de 2018 Update ha llegado para todos los clientes de HoloLens! Esta actualización incluye numerosas mejoras que se han introducido desde la última versión del software de HoloLens en [agosto de 2016](release-notes-august-2016.md).

### <a name="for-everyone"></a>Para todos los usuarios

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Colocación automática de contenido 2D y 3D en el inicio</td><td>Una aplicación UWP app 2D del iniciador o 2D auto-lugares del mundo con una distancia cuando se inicia en lugar de requerir al usuario que lo coloca y un tamaño óptimo. Si un <a href="app-views.md">aplicaciones envolventes</a> usa un iniciador de aplicaciones 2D en lugar de un <a href="3d-app-launcher-design-guidance.md">iniciador de aplicaciones 3D</a>, la aplicación envolventes iniciar automáticamente desde el iniciador de aplicaciones 2D igual que en RS1.<br><br>Un iniciador de aplicaciones 3D en el menú Inicio también auto-lugares del mundo. En lugar de iniciar automáticamente la aplicación, los usuarios, a continuación, hacer clic en el selector para iniciar la aplicación envolvente. Contenido 3D que se puede abrir desde la aplicación hologramas y Edge también auto-lugares del mundo.</td><td>Al abrir una aplicación desde el menú Inicio, ya no se le pedirá que lo coloca en el mundo.<br><br>Si la aplicación 2D /<a href="3d-app-launcher-design-guidance.md">iniciador de aplicaciones 3D</a> la ubicación no es óptimo, se puede mover fácilmente mediante la nuevo manipulaciones fluido de aplicación se describe a continuación. También puede volver a colocar el contenido de aplicación 2D/3D del iniciador "mover esto" y, a continuación, usando a mirada para volver a colocar el contenido.</td>
  </tr>
  <tr>
    <td>Manipulación de la aplicación fluido</td><td>Mover, cambiar el tamaño y girar contenido 2D y 3D sin tener que entrar en modo de "Ajustar".</td><td>Para mover una aplicación para UWP 2D o iniciador de aplicaciones 2D, simplemente mire su barra de la aplicación y, a continuación, usar la derivación de + mantenga + gesto de arrastre. Puede mover contenido 3D por gazing en cualquier lugar en el objeto y, a continuación, usar pulse + mantenga + arrastrar.<br><br>Para cambiar el tamaño de contenido 2D, mire su esquina. El cursor mirada se convertirá en un cursor de cambio de tamaño y, a continuación, puede pulse + mantenga + arrastrar para cambiar el tamaño. También puede hacer contenido 2D sea más alto o más ancho examinando sus bordes y arrastrando.<br><br>Para cambiar el tamaño del contenido 3D, levante copia las manos libres en el marco de gestos, los dedos en la posición de la lista. Verá el cursor convertir en un estado con 2 manos poco. Realice la derivación de mantener presionado el lápiz con ambos las manos. Mover las manos de más de cerca o más alejadas cambiará el tamaño del objeto. Mover las manos hacia delante y hacia atrás entre sí girará el objeto. También puede cambiar el tamaño o girar contenido 2D de este modo.</td>
  </tr>
  <tr>
    <td>Cambio de tamaño horizontal de aplicación 2D con reflujo</td><td>Crear una aplicación UWP 2D más amplia en la relación de aspecto para ver más contenido de la aplicación. Por ejemplo, hace que la aplicación de correo electrónico lo suficientemente ancha para mostrar el panel de vista previa.</td><td>Solo tiene que mirar en el borde izquierdo o derecho de la aplicación UWP 2D para ver el cursor de cambio de tamaño, a continuación, utilice la derivación de mantenga + arrastre gesto para cambiar el tamaño.</td>
  </tr>
  <tr>
    <td>Compatibilidad con comandos de voz expandido</td><td>Puede hacer más simplemente con la voz.</td><td>Pruebe estos comandos de voz:<ul><li>"Vaya a Inicio": abre el menú Inicio o se cierra un <a href="app-views.md">aplicaciones envolventes</a>.</li><li>"Mover esto -" le permite mover un objeto.</li></ul></td>
  </tr>
  <tr>
    <td>Aplicaciones que se actualizan hologramas y fotos</td><td>Aplicación hologramas actualizada con nuevo hologramas. Aplicación de fotos actualizada.</td><td>Observará un aspecto actualizado a las aplicaciones hologramas y fotos. La aplicación hologramas incluye varios hologramas nueva y un creador de etiquetas para facilitar la creación de texto.</td>
  </tr>
  <tr>
    <td>Mejora de la captura de realidad mixta</td><td>Inicio de método abreviado de hardware y MRC vídeo de final.</td><td>Mantenga la tecla Subir volumen + abajo durante 3 segundos iniciar la grabación de vídeo MRC. Ambos pulse de nuevo o usar el gesto de bloom para finalizar.</td>
  </tr>
  <tr>
    <td>Espacios consolidados</td><td>Simplificar la administración de espacio para hologramas en un único espacio.</td><td>HoloLens busca automáticamente el espacio y ya no requiere que administre o seleccione espacios. Si tiene problemas con hologramas rodean, puede ir a <b>configuración > sistema > hologramas > Quitar cercanas hologramas</b>. Si es necesario, también puede seleccionar <b>quitar todos los hologramas</b>.</td>
  </tr>
  <tr>
    <td>Inmersión de audio mejorada</td><td>Ahora puede oír HoloLens mejor en entornos con mucho ruido y experiencia de sonido más realista de aplicaciones como su sonido quedarán ocultos por paredes real detectadas por el dispositivo.</td><td>No tiene que hacer nada para disfrutar del sonido espacial mejorado.</td>
  </tr>
  <tr>
    <td>Explorador de archivos</td><td>Mover y eliminar archivos en HoloLens.</td><td>Puede usar el <b>Explorador de archivos</b> aplicación para mover y eliminar archivos en HoloLens.<br><br><b>Sugerencia:</b> Si no ve los archivos, el filtro "Reciente" puede estar activo (el icono de reloj se resalta en el panel izquierdo). Para solucionar el problema, seleccione el <b>este dispositivo</b> documentar el icono en el panel izquierdo (debajo del icono de reloj), o abra el menú y seleccione <b>este dispositivo</b>.
</td>
  </tr>
  <tr>
    <td>Compatibilidad con MTP (Protocolo de transferencia multimedia)</td><td>Permite que su PC de escritorio para tener acceso a las bibliotecas (fotos, vídeos, documentos) en HoloLens para transferir fácilmente.</td><td>Similar a otros dispositivos móviles, conecte su HoloLens a su PC para que aparezca <b>Explorador de archivos</b> para tener acceso a las bibliotecas de HoloLens (fotos, vídeos, documentos) para transferir fácilmente.<br><br><b>Sugerencias:</b><ul><li>Si no ve los archivos, asegúrese de que iniciar sesión en su HoloLens para habilitar el acceso a los datos.</li><li>Desde <b>Explorador de archivos</b> en su PC, puede seleccionar <b>las propiedades del dispositivo</b> para ver el número de versión del sistema operativo de Windows Holographic (versión de firmware) y el número de serie del dispositivo.</li></ul><b>Problema conocido:</b> Cambiar el nombre de HoloLens a través de <b>Explorador de archivos</b> no está habilitado en su PC.</td>
  </tr>
  <tr>
    <td>Soporte técnico de red del portal cautivo durante la instalación</td><td>Ahora puede configurar su HoloLens en una red de invitado en hoteles, centros de conferencias, tiendas minoristas o a las empresas que usan captive portal.</td><td>Durante la instalación, seleccione la red, consulte conectarse automáticamente si lo desea y escriba la información de red que se le pida.</td>
  </tr>
  <tr>
    <td>Sincronización de fotos y vídeos a través de la aplicación OneDrive</td><td>Las fotos y vídeos de HoloLens ahora se sincronizarán a través de la aplicación de OneDrive desde la Microsoft Store en lugar de directamente a través de la aplicación fotos.</td><td>Para configurar esta opción, descargue e inicie la aplicación OneDrive desde el Store. En la primera ejecución se solicitará al cargar automáticamente las fotografías en OneDrive, o puede encontrar la opción en la configuración de la aplicación.</td>
  </tr>
</table>

### <a name="for-developers"></a>Para desarrolladores

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Mejoras de asignación espacial</td><td>Mejoras de calidad, la simplificación y el rendimiento.</td><td>Malla asignación espacial aparecerá más limpio, menos triángulos necesarios para representar el mismo nivel de detalle. Es posible que observe los cambios en la densidad de triángulo de la escena.</td>
  </tr>
  <tr>
    <td>Selección automática del punto de enfoque basado en el búfer de profundidad</td><td>El envío de un búfer de profundidad para Windows permite HoloLens seleccionar un punto de enfoque automáticamente para optimizar la estabilidad holograma.</td><td>En Unity, vaya a <b>Editar > configuración del proyecto > Reproductor > pestaña de la plataforma Universal de Windows > configuración XR</b>, expanda el <b>Windows Mixed Reality SDK</b> de elemento y asegúrese de <b>Habilitar búfer de profundidad Uso compartido</b> está activada. Esto se comprobará automáticamente para los nuevos proyectos.<br><br>Para aplicaciones de DirectX, asegúrese de llamar a la <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer </a> método <b>HolographicRenderingParameters</b> cada fotograma para proporcionar el búfer de profundidad para Windows.
</td>
  </tr>
  <tr>
    <td>Modos de reprojection holográfica</td><td>Ahora puede deshabilitar reprojection posicional en HoloLens para mejorar la estabilidad holograma de rígidamente bloqueado contra el cuerpo de contenido como un vídeo de 360 grados.</td><td>En Unity, establezca <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a> a <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a> cuando todo el contenido está en la vista rígidamente bloqueado de cuerpo.<br><br>Para aplicaciones de DirectX, establezca <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a> a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a> cuando todo el contenido está en la vista rígidamente bloqueado de cuerpo.</td>
  </tr>
  <tr>
    <td>API de personalización de aplicaciones</td><td>Las API de Windows obtener más información acerca de dónde se ejecuta la aplicación, por ejemplo, si la pantalla del dispositivo es transparente (HoloLens) u opaco (envolventes auriculares) y si la vista 2D de una aplicación para UWP se muestre en el shell holográfico.</td><td>Unity manualmente tenía expuestos anteriormente <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a> de manera que funcionaban incluso antes de que esta compilación.<br><br>Para las aplicaciones de DirectX, ahora puede acceder a las API existentes como <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault(). IsOpaque</a> y <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> en HoloLens también.
</td>
  </tr>
  <tr>
      <td>Modo de investigación</td><td>Permite a los desarrolladores tener acceso a los sensores de HoloLens claves al compilar aplicaciones industriales y académicas para probar nuevas ideas en los campos de computer vision y robótica, incluidos:<ul><li>Los cuatro cámaras de seguimiento del entorno</li><li>Dos versiones de los datos de cámara de asignación de profundidad</li><li>Dos versiones de un flujo de reflexión de infrarrojos</li></ul></td><td><a href="research-mode.md">Documentación de modo de investigación</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Aplicaciones de ejemplo del modo de investigación</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Para los clientes comerciales

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Usar varias cuentas de usuario de Azure Active Directory en un único dispositivo</td><td>Compartir un HoloLens con varios usuarios de Azure AD, cada uno con su propia configuración de usuario y datos de usuario en el dispositivo.</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT Pro Center: Recurso compartido HoloLens con varias personas</a></td>
  </tr>
  <tr>
    <td>Cambiar la red Wi-Fi en el inicio de sesión</td><td>Cambiar la red Wi-Fi antes de iniciar sesión en habilitar a otro usuario inicie sesión con su cuenta de usuario de Azure AD por primera vez, lo que permite a los usuarios compartir dispositivos en varias ubicaciones y sitios de trabajo.</td><td>En la pantalla Inicio de sesión, puede usar el icono de red debajo del campo de contraseña para conectarse a una red. Esto resulta útil cuando se trata de la primera vez que inicie sesión en un dispositivo.</td>
  </tr>
  <tr>
    <td>Inscripción unificada</td><td>Ahora es fácil para un usuario de HoloLens que configurar el dispositivo con una cuenta Microsoft personal para agregar una cuenta profesional (Azure AD) y unir el dispositivo a su servidor MDM.</td><td>Simplemente inicie sesión con una cuenta de Azure AD y la inscripción se realiza automáticamente.</td>
  </tr>
  <tr>
    <td>Sincronización de correo electrónico sin inscripción de MDM</td><td>Compatibilidad con la sincronización de correo electrónico de Exchange Active Sync (EAS) sin necesidad de inscripción de MDM.</td><td>Ahora se puede sincronizar correo electrónico sin la inscripción en MDM. Se puede configurar el dispositivo con una Account de Microsoft, descargar e instalar la aplicación de correo y agregar una cuenta de correo electrónico de trabajo directamente.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>para profesionales de TI

<table>
  <tr>
    <th>Característica</th><th>Detalles</th><th>Instrucciones</th>
  </tr>
  <tr>
    <td>Nuevo nombre de "Windows Holographic for Business" sistema operativo</td><td>Desactive la edición de nomenclatura para reducir la confusión en la aplicación de la licencia de actualización de edición cuando están habilitadas las características de Commercial Suite en HoloLens.</td><td>Puede ver qué edición de Windows Holographic es en su dispositivo en <b>configuración > sistema > acerca de</b>. "Windows Holographic for Business" aparecerá si se ha aplicado una actualización de edición para habilitar las características de Commercial Suite. Obtenga información sobre cómo <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">desbloquear Windows Holographic for Business características</a>.</td>
  </tr>
  <tr>
  <td>Diseñador de configuración de Windows (WCD)</td><td>Crear y editar los paquetes de aprovisionamiento para configurar HoloLens a través de la aplicación WCD actualizada. Asistente de HoloLens simple para la actualización de edición, OOBE configurable, zona horaria/región, token de Azure AD de forma masiva, red y para desarrolladores CSP. Editor avanzado filtrado a HoloLens admite opciones, incluido el acceso asignado y cuenta de administración de CSP.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar mediante un paquete de aprovisionamiento de HoloLens</a></td>
  </tr>
  <tr>
    <td>(Configuración rápida OOBE) del programa de instalación configurable</td><td>Ocultar la calibración, aprendizaje de gestos/mirada y pantallas de configuración de Wi-Fi durante la instalación.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro Center: Configurar mediante un paquete de aprovisionamiento de HoloLens</a></td>
  </tr>
  <tr>
    <td>Compatibilidad con token de Azure AD de forma masiva</td><td>Regístrese con antelación dispositivos al inquilino de directorio de Azure AD para el flujo de programa de instalación más rápido de usuario.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar mediante un paquete de aprovisionamiento de HoloLens</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>Implementar perfil de configuración de HoloLens en modo de programador. Es útil para los dispositivos de desarrollo y demostración.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar mediante un paquete de aprovisionamiento de HoloLens</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>Compartir un dispositivo HoloLens y quitar los datos de usuario después de cierre de sesión o los umbrales de inactividad y almacenamiento para uso temporal. Es compatible con cuentas de Azure AD.</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro Center: Configurar mediante un paquete de aprovisionamiento de HoloLens</a></td>
  </tr>
  <tr>
  <td>Acceso asignado</td><td>Windows asignan acceso para los trabajadores de la primera línea o demostraciones. Bloqueo de solo o con varias aplicaciones. No desbloquear necesidad de desarrollador.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT Pro Center: Configuración de HoloLens en modo de pantalla completa</a></td>
  </tr>
  <tr>
  <td>Acceso de invitado para dispositivos de pantalla completa</td><td>Windows asignan acceso con la cuenta de invitado sin contraseña para las demostraciones. Bloqueo de solo o con varias aplicaciones. No desbloquear necesidad de desarrollador.</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT Pro Center: Configuración de HoloLens en modo de pantalla completa</a></td>
  </tr>
  <tr>
    <td>Configuración de diagnósticos de (configuración rápida OOBE)</td><td>Obtener registros de diagnóstico de HoloLens para que pueda solucionar errores de inicio de sesión de Azure AD (antes de que está disponible para el usuario cuyo inicio de sesión no se pudo centro comentarios).</td><td>Cuando se produce un error en el programa de instalación o inicio de sesión, elija el nuevo <b>recopile información</b> opción para obtener los registros de diagnóstico para solucionar problemas.</td>
  </tr>
  <tr>
    <td>Expiración de contraseña indefinido de cuenta local</td><td>Quitar una interrupción del dispositivo que se restablece cuando expira la contraseña de cuenta local.</td><td>Al aprovisionar una cuenta local, ya no necesita cambiar la contraseña cada 42 días en <b>configuración</b>, como la contraseña de cuenta ya no expira.</td>
  </tr>
  <tr>
    <td>Detalles y el estado de sincronización MDM</td><td>Funcionalidad de Windows estándar para comprender el estado de sincronización MDM y obtener información detallada de HoloLens.</td><td>Puede comprobar el estado de sincronización MDM para un dispositivo en <b>configuración > cuentas > obtener acceso a trabajo o escuela > información</b>. En el <b>estado de sincronización del dispositivo<b> sección, puede iniciar una sincronización, vea áreas administradas por MDM y crear y exportar un informe de diagnóstico avanzado.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado duro para ofrecer una excelente experiencia de Windows Mixed Reality, pero todavía estamos realizando un seguimiento algunos problemas conocidos. Si encuentra otros, [enviarnos comentarios](give-us-feedback.md).

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Después de la actualización

Es posible que observe los siguientes problemas después de actualizar desde RS1 a RS4 en su HoloLens:
* **Restablecer PIN** -el 3 x 3 aplicaciones Anclar al menú Inicio se restablecerá a los valores predeterminados después de la actualización. 
* **Las aplicaciones y restablecer hologramas colocado** -aplicaciones colocadas en el mundo se eliminará después de la actualización y deberá volver a colocarse en todo el espacio. 
* **Centro de comentarios no puede iniciar inmediatamente** -inmediatamente después de la actualización, se tardará unos minutos antes de poder iniciar algunas aplicaciones de la Bandeja de entrada como centro de opiniones, mientras que se actualizan. 
* **Certificados de Wi-Fi corporativos tienen que volver a sincronizados** -estamos investigando un problema que requiere el HoloLens que estar conectado a una red diferente en orden para los certificados corporativos se vuelve a sincronizado con el dispositivo antes de que se pueda volver a conectar a redes corporativas mediante certificados. 
* **No funciona la reproducción de vídeo H.265 HEVC** -las aplicaciones que intentan reproducir vídeos H.265 recibirá un mensaje de error. La solución consiste en [tener acceso a la de Windows Device Portal](using-the-windows-device-portal.md), seleccione **aplicaciones** en la barra de navegación izquierdo, y **quitar** la aplicación de HEVC. A continuación, instale la versión más reciente [extensión de vídeo HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) desde la Microsoft Store. Estamos investigando el problema. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Para los desarrolladores: HoloLens aplicaciones para dispositivos que ejecutan Windows 10 de abril de 2018 se actualiza

Junto con una amplia lista de [nuevas características](#new-features-for-hololens), Windows 10 de abril 2018 Update (RS4) para HoloLens exige algunos comportamientos de código que no lo hizo de las versiones anteriores:
* **Solicitudes de permiso para usar los recursos confidenciales (cámara, micrófono, etcetera.)**  -RS4 en HoloLens hará cumplir las solicitudes de permiso para las aplicaciones que se va a obtener acceso a recursos confidenciales, como la cámara o el micrófono. RS1 en HoloLens no forzó estos mensajes, por lo tanto, si la aplicación supone que el acceso inmediato a estos recursos, se puede bloquear en RS4 (incluso si el usuario concede el permiso para el recurso solicitado). Lea la correspondiente [artículo de declaraciones de capacidad de aplicación UWP](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) para obtener más información.
* **Las llamadas a las aplicaciones fuera de su propio** -RS4 en HoloLens exigirá el uso correcto de la [ *Windows.System.Launcher* clase](https://docs.microsoft.com/uwp/api/Windows.System.Launcher) para iniciar otra aplicación de su propia. Por ejemplo, hemos visto problemas con aplicaciones que llaman a *Windows.System.Launcher.LaunchUriForResultsAsync* desde un subproceso no ASTA UI. Esto se realizaría correctamente en RS1 en HoloLens, pero RS4 requiere la llamada que se ejecuta en el subproceso de interfaz de usuario.

### <a name="windows-mixed-reality-on-desktop"></a>Realidad mixta en el escritorio de Windows

#### <a name="visual-quality"></a>Calidad Visual

* Si observa después de 10 de abril de 2018 de Windows Update que los gráficos son más borrosos que antes, o que el campo de visión, tenga un aspecto más pequeño en los auriculares, la configuración de rendimiento automática puede haber cambiado con el fin de mantener una velocidad de fotogramas suficiente en menos eficaces tarjeta de gráficos (como Nvidia 1050). Para invalidar manualmente esta (si elige), vaya a **configuración > la realidad mixta > Mostrar auriculares > Opciones de experiencias > cambio** y cambiar "Automático" a "Hz 90". También puede intentar cambiar **calidad Visual** (en la misma página de configuración) en "Alto".

#### <a name="windows-mixed-reality-setup"></a>Programa de instalación de Windows Mixed Reality

* Al configurar Windows con un auricular conectado, el monitor del equipo puede entrar en blanco. Desconecte los auriculares para habilitar la salida en el monitor de equipo para completar la instalación de Windows.
* Si no tiene los auriculares conectados, se pueden perder sugerencias adicionales cuando visite por primera vez el inicio de Windows Mixed Reality.
* Otros dispositivos Bluetooth pueden causar interferencias con controladores de movimiento. Si los controladores de movimiento tienen problemas de conexión y de emparejamiento/seguimiento, asegúrese de que la radio Bluetooth (si un dispositivo externo) está conectados a una ubicación despejada y no inmediatamente al lado de otro dispositivo Bluetooth. También intente apagar otros periféricos Bluetooth durante las sesiones de Windows Mixed Reality para ver si sirve de ayuda.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Juegos y aplicaciones desde la Microsoft Store

* Algunos juegos con muchos gráficos, como Forza Motorsport 7, pueden causar problemas de rendimiento en equipos con menor capacidad cuando reproduce dentro de Windows Mixed Reality.

#### <a name="audio"></a>Audio

* Si tiene Cortana habilitado en el equipo host antes de usar los auriculares de Windows Mixed Reality, puede perder espacial simulación sonido aplicada a las aplicaciones que coloque en torno a Windows Mixed Reality principal. 
   * La solución alternativa es permitirle "Windows Sonic para auriculares" en todos los dispositivos de audio conectados a su equipo, incluso los auriculares audio dispositivo conectado:
      1. Haga clic en el icono Altavoz de la barra de tareas de escritorio y seleccione en la lista de dispositivos de audio.
      2. Haga clic en el icono Altavoz de la barra de tareas de escritorio y seleccione "Windows Sonic para auriculares" en el menú "Configuración de altavoces".
      3. Repita estos pasos para todos los dispositivos de audio (extremos).
   * Otra opción es si se desactiva "Cortana permiten responder a Hola Cortana" **configuración** > **Cortana** en el escritorio antes de iniciar Windows Mixed Reality.
* Cuando otro dispositivo USB multimedia (por ejemplo, una cámara web) comparte el mismo concentrador USB (externo o dentro de su equipo) con los auriculares de realidad mixta de Windows, en raras ocasiones audio jack/auriculares de los auriculares puede tener un sonido zunbido o sin audio en absoluto. Puede corregir esto por los auriculares en un puerto USB que no comparten el mismo concentrador que el otro dispositivo o desconectar o deshabilitar su otro dispositivo multimedia USB.
* En muy raras ocasiones, concentrador USB del equipo de host no puede proporcionar suficiente capacidad para los auriculares de realidad mixta de Windows y es posible que observe una ráfaga de ruido de los auriculares conectados a los auriculares.

#### <a name="holograms"></a>Hologramas

* Si ha colocado un gran número de hologramas en el inicio de Windows Mixed Reality, algunos pueden desaparecer y volverán a aparecer como echa un vistazo alrededor. Para evitar este problema, quite algunas de las hologramas en esa área de Windows Mixed Reality principal.

#### <a name="motion-controllers"></a>Controladores de movimiento

* Si la entrada no se está enrutando a los auriculares, el controlador de movimiento brevemente desaparecerá cuando se mantiene al lado de límite de la sala. Al presionar Win + S para asegurarse de que hay un banner azul situado entre el monitor de escritorio resolver esto. 
* En ocasiones, al hacer clic en una página web en Microsoft Edge, irá el contenido en lugar de hacer clic.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicación de escritorio en el inicio de Windows Mixed Reality

* Herramienta recortes no funciona en una aplicación de escritorio.
* Aplicación de escritorio no conserva la configuración al volver a iniciar.
* Si usas un vista previa del Portal de realidad mixta en el escritorio, al abrir la aplicación de escritorio en el inicio de Windows Mixed Reality, puede observar el efecto de espejo infinito. 
* Ejecuta la aplicación de escritorio puede provocar problemas de rendimiento en no - Ultra Mixed Reality equipos con Windows; no se recomienda.  
* Aplicación de escritorio puede iniciar automáticamente porque una ventana invisible en escritorio tiene el foco. 
* Control de cuentas de usuario de escritorio símbolo del sistema hará auriculares mostrar negro hasta que se complete el símbolo del sistema.

#### <a name="windows-mixed-reality-for-steamvr"></a>Realidad mixta de Windows para SteamVR

* Es posible que deba iniciar el Portal de realidad mixta después de actualizar para asegurarse de las actualizaciones de software necesarios para Windows 10 de abril de 2018 Update ha completado antes de iniciar SteamVR. 
* Debe estar en una versión reciente de Windows Mixed Reality para SteamVR siga siendo compatible con Windows Update 10 de abril de 2018. Asegúrese de que las actualizaciones automáticas están activadas para Windows Mixed Reality para SteamVR, que se encuentra en la sección "Software" de la biblioteca en la secuencia.  

#### <a name="other-issues"></a>Otros problemas

>[!IMPORTANT]
>Una versión anterior de Windows 10 de abril de 2018 actualización insertada para Insiders (versión 17134.5) faltaba un componente de software necesario para ejecutar Windows Mixed Reality. Se recomienda evitar esta versión, si usa Windows Mixed Reality. 

Hemos detectado una regresión del rendimiento al usar Surface Book 2 en la versión inicial de esta actualización (10.0.17134.1) que estamos trabajando para solucionar el problema en una revisión de la próxima actualización. Se recomienda esperar a que esto se ha solucionado antes de actualizar manualmente o esperar a la actualización para la implementación con normalidad.

## <a name="provide-feedback-and-report-issues"></a>Proporcionar comentarios e informe de problemas

Use la [aplicación Centro de opiniones en su equipo con Windows 10 o en HoloLens](give-us-feedback.md) para proporcionar comentarios e informe de problemas. Mediante el centro de comentarios asegura que toda la información de diagnóstico necesarios se incluyen para ayudar a nuestros ingenieros de depurar y resolver el problema rápidamente.

>[!NOTE]
>No olvide acepte el mensaje que pregunta si desea que el centro de opiniones para tener acceso a la carpeta documentos (seleccione **Sí** cuando se le solicite).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión - octubre de 2017](release-notes-october-2017.md)
* [Notas de la versión - agosto de 2016](release-notes-august-2016.md)
* [Notas de la versión - mayo de 2016](release-notes-may-2016.md)
* [Notas de la versión: marzo de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Soporte técnico de auriculares envolventes (vínculo externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Soporte técnico de HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalar las herramientas](install-the-tools.md)
* [Envíenos sus comentarios](give-us-feedback.md)

