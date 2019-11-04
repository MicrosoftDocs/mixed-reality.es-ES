---
title: 'Notas de la versión: agosto 2016'
description: Notas de la versión de HoloLens para la versión de aniversario de Windows 10 (2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de la versión, sistema operativo, plataforma, características, Commercial Suite
ms.openlocfilehash: dcac64524cd8d1b1f2b0a496c4dcd2ad2fc7b690
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438098"
---
# <a name="release-notes---august-2016"></a>Notas de la versión: agosto 2016

El equipo de HoloLens está escuchando comentarios de los desarrolladores del programa Windows Insider para priorizar el trabajo. Envíenos [sus comentarios](give-us-feedback.md) a través del centro de comentarios, los [foros para desarrolladores](https://forums.hololens.com) y [Twitter a través de @HoloLens](https://twitter.com/hololens). A medida que Windows 10 adopta la actualización de aniversario, el equipo de HoloLens está satisfecho con la mejora de la experiencia holográfica. En esta actualización, nos centramos en las principales correcciones, mejoras e introduciendo características solicitadas por las empresas y disponibles en Microsoft HoloLens Commercial Suite.

**Versión más reciente:** Actualización de Windows Holographic de agosto de 2016 (**10.0.14393.0**, versión de aniversario de Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Para [actualizar a la versión actual](updating-hololens.md), abra la aplicación de *configuración* , vaya a *Actualizar & seguridad*y, a continuación, seleccione el botón *Buscar actualizaciones* .

## <a name="new-features"></a>Nuevas características

**Asociar a la depuración del proceso** HoloLens ahora admite la depuración de conexión a proceso. Puede usar Visual Studio 2015 Update 3 para conectarse a una aplicación en ejecución en HoloLens y [comenzar a depurarla](using-visual-studio.md#debugging-an-installed-or-running-app). Esto funciona sin necesidad de implementar desde un proyecto de Visual Studio.

**Emulador de HoloLens actualizado** También hemos publicado una versión actualizada del emulador de HoloLens.

**Compatibilidad con el controlador para juegos** Ahora puede emparejar y usar los controladores de juegos Bluetooth con HoloLens. La nueva versión de la controladora inalámbrica Xbox tiene características de Bluetooth y se puede usar para reproducir sus aplicaciones y juegos favoritos habilitados para el controlador de interfaz de red. Debe aplicarse una [actualización de controlador](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de poder conectar la controladora inalámbrica Xbox S con HoloLens. La controladora inalámbrica Xbox S es compatible con las API de [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) y [Windows. Gaming. Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) . Se puede acceder a los modelos adicionales de controladores Bluetooth a través de la API [Windows. Gaming. Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) .

## <a name="improvements-and-fixes"></a>Mejoras y correcciones

Estamos sincronizados con el resto de la actualización de aniversario de Windows 10, así que, además de las correcciones específicas de HoloLens, también recibe todo lo mejor de Windows Update para aumentar la confiabilidad y el rendimiento de la plataforma. Sus comentarios son muy importantes y tienen una prioridad para las correcciones de la versión.

Hemos mejorado las siguientes experiencias:
* experiencias de inicio de sesión.
* Unión al área de trabajo.
* eficiencia de energía de las transiciones de estado de energía de dispositivo.
* estabilidad con capturas de realidad mixta.
* confiabilidad de la conectividad Bluetooth
* persistencia de holograma en el escenario de varias aplicaciones.

Hemos corregido los siguientes problemas:
* los perfiles de Visual Studio y el depurador de gráficos no se pueden conectar.
* las fotos & documentos no aparecen en el explorador de archivos en el portal de dispositivos.
* la barra de la aplicación puede parpadear cuando el cursor se coloca sobre él mientras está en el modo ajustar.
* En el modo de ajuste, el cursor de punto mira fijamente cambiará al cursor de 4 flechas más lentamente.
* "Hola Cortana reproducir música" no inicia Groove.
* después de la actualización anterior, indicando "ir a Inicio" no muestra el panel de PIN correctamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Presentación de Microsoft HoloLens Commercial Suite

Microsoft HoloLens Commercial Suite está listo para la implementación empresarial. Hemos agregado varias [características comerciales](commercial-features.md) altamente solicitadas de nuestros primeros socios comerciales.

Póngase en contacto con su administrador de cuenta de Microsoft local para comprar Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Características comerciales clave 

* **Pantalla completa.** Con el modo de quiosco de HoloLens, puede limitar las aplicaciones que se ejecutarán para habilitar las experiencias de demostración o de presentación.<br>
  ![con el modo de quiosco, HoloLens se inicia directamente en la aplicación de su elección.](images/201608-kioskmode-400px.png)
* **Administración de dispositivos móviles (MDM) para HoloLens.** El Departamento de ti puede administrar varios dispositivos de HoloLens simultáneamente mediante soluciones como Microsoft Intune. Podrás administrar la configuración, seleccionar qué aplicaciones se instalarán y establecer las opciones de configuración de seguridad adaptadas a las necesidades de tu organización.<br>
  ![la administración de dispositivos móviles en HoloLens proporciona administración de dispositivos de nivel empresarial en varios dispositivos.](images/201608-enterprisemanagement-400px.png)
* **Windows Update para la empresa.** Actualizaciones del sistema operativo controlado a los dispositivos y compatibilidad con la rama de mantenimiento a largo plazo.
* **Seguridad de los datos.** El cifrado de datos de BitLocker está habilitado en HoloLens para proporcionar el mismo nivel de protección de seguridad que cualquier otro dispositivo de Windows.
* **Acceso al trabajo.** Cualquier persona de su organización puede conectarse de forma remota a la red corporativa a través de una red privada virtual en un HoloLens. HoloLens también puede acceder a redes Wi-Fi que requieran credenciales.
* **Microsoft Store para la empresa.** El Departamento de ti también puede configurar un almacén privado de la empresa que contenga solo las aplicaciones de su empresa para su uso específico de HoloLens. Distribuir de forma segura el software empresarial al grupo seleccionado de usuarios empresariales.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition frente a Commercial Suite

<table>
<tr>
<th>Características</th><th>Edición de desarrollo</th><th>Conjunto comercial</th>
</tr><tr>
<td>Cifrado de dispositivos (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Red privada virtual (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modo de quiosco</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Administración e implementación</th>
</tr><tr>
<td>Administración de dispositivos móviles (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Capacidad de bloquear la anulación de la inscripción</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Acceso Wi-Fi corporativo basado en certificados</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumidor)</td><td style="text-align: center;">Independiente</td><td style="text-align: center;">Filtrado a través de MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portal de la tienda de empresas</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Identidad y seguridad</th>
</tr><tr>
<td>Inicio de sesión con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Inicio de sesión con la cuenta de Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenciales de próxima generación con desbloqueo PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Arranque seguro</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Mantenimiento y soporte técnico</th>
</tr><tr>
<td>Actualizaciones automáticas del sistema a medida que llegan</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update para la empresa</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rama de mantenimiento a largo plazo</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulta también
* [Problemas conocidos de HoloLens](hololens-known-issues.md)
* [Características comerciales](commercial-features.md)
* [Instalación de las herramientas](install-the-tools.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
