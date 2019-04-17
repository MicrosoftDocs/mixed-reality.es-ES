---
title: Notas de la versión - agosto de 2016
description: Notas de la versión de HoloLens para el Windows 10 Anniversary Release (otoño de 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Versión de HoloLens, notas, sistema operativo, plataforma, características, suite comercial
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605469"
---
# <a name="release-notes---august-2016"></a>Notas de la versión - agosto de 2016

El equipo de HoloLens está escuchando a los comentarios de desarrolladores en el programa de Windows Insider para dar prioridad a nuestro trabajo. Continúe para [enviarnos comentarios](give-us-feedback.md) a través del centro de comentarios, la [foros para desarrolladores de](https://forums.hololens.com) y [a través de Twitter @HoloLens ](https://twitter.com/hololens). Como Windows 10 adopta que la actualización de aniversario, el equipo de HoloLens está feliz de entregar mejora aún más la experiencia holográfica. Esta actualización, se centra en las características de presentación solicitadas por las empresas y está disponible en el conjunto de aplicaciones comerciales de Microsoft HoloLens, mejoras y correcciones importantes.

**Versión más reciente:** Actualización de Windows Holographic de agosto de 2016 (**10.0.14393.0**, versión de aniversario de Windows 10)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Para [actualización a la versión actual](updating-hololens.md), abra el *configuración* aplicación, vaya a *actualización y seguridad*, a continuación, seleccione el *buscar actualizaciones* botón.

## <a name="new-features"></a>Nuevas características

**Adjuntar al proceso de depuración** HoloLens ahora admite la depuración de asociar al proceso. Puede usar Visual Studio 2015 Update 3 para conectarse a una aplicación en ejecución en un HoloLens y [comenzar a depurarlo](using-visual-studio.md#debugging-an-installed-or-running-app). Esto funciona sin necesidad de implementar desde un proyecto de Visual Studio.

**Actualiza el emulador de HoloLens** también hemos lanzado una versión actualizada del emulador de HoloLens.

**Soporte técnico de gamepad** puede emparejar y usar controladores de Bluetooth con HoloLens ahora! El controlador S más recientes de Xbox Wireless funcionalidades de Bluetooth y puede usarse para reproducir sus aplicaciones y juegos favoritos habilitados gamepad. Un [actualización del controlador](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) deben aplicarse antes de poder conectar la S de controlador Xbox inalámbrico con HoloLens. La S de controlador Xbox inalámbrica es compatible con [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) y [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API. Pueden tener acceso a los modelos adicionales de controladores de Bluetooth a través de la [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.

## <a name="improvements-and-fixes"></a>Mejoras y correcciones

Se están sincronizadas con el resto de la actualización de aniversario de Windows 10, por lo que además de las correcciones específicas de Hololens, están recibiendo también todas las ventajas de la actualización de Windows para aumentar el rendimiento y confiabilidad de la plataforma. Sus comentarios son con valores de alta y se tenga prioridad para las correcciones de la versión.

Se han mejorado las experiencias siguientes:
* Inicie sesión en las experiencias.
* unión al área.
* eficiencia de energía para las transiciones de estado de energía de dispositivos.
* estabilidad con captura de realidad mixta.
* confiabilidad para la conectividad de Bluetooth
* persistencia holograma en escenario de aplicación de varios.

Hemos corregido los problemas siguientes:
* los generadores de perfiles de Visual Studio y el depurador de gráficos no puede conectarse.
* fotos y documentos no se muestran en el Explorador de archivos en el portal de dispositivo.
* la barra de aplicaciones puede flash cuando se coloca el cursor por encima de él en el modo de ajuste.
* Cuando está en modo de ajuste, el cursor de punto de ojo mirada cambiará al cursor de flecha de 4 unos minutos más lentamente.
* "Hola Cortana reproducir música" no iniciar Groove.
* Tras la actualización anterior, que dice "Go Home" no muestra el panel de PIN correctamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introducción a Microsoft HoloLens comercial Suite

Microsoft HoloLens Commercial Suite está lista para la implementación empresarial. Hemos agregado algunas muy solicitados [las características comerciales](commercial-features.md) de nuestros primeros socios comerciales.

Póngase en contacto con su administrador de cuenta local de Microsoft para adquirir Commercial Suite de Microsoft HoloLens.

### <a name="key-commercial-features"></a>Características comerciales clave 

* **Modo de pantalla completa.** Con el modo de quiosco de HoloLens, puede limitar las aplicaciones que desea ejecutar para habilitar experiencias completas de demostración o presentación.<br>
  ![Con el modo de quiosco, HoloLens inicia directamente desde la aplicación de su elección.](images/201608-kioskmode-400px.png)
* **Administración de dispositivos móviles (MDM) para HoloLens.** El departamento de TI puede administrar varios dispositivos HoloLens simultáneamente con soluciones como Microsoft Intune. Podrás administrar la configuración, seleccionar qué aplicaciones instalar y establecer las opciones de configuración de seguridad adaptadas a las necesidades de su organización.<br>
  ![Administración de dispositivos móviles en HoloLens proporciona administración de dispositivos de nivel de empresa en varios dispositivos.](images/201608-enterprisemanagement-400px.png)
* **Windows Update para empresas.** Controla las actualizaciones del sistema operativo en dispositivos y soporte técnico para la rama de mantenimiento a largo plazo.
* **Seguridad de los datos.** El cifrado de BitLocker está habilitado en HoloLens para proporcionar el mismo nivel de protección de seguridad como cualquier otro dispositivo de Windows.
* **Acceso al trabajo.** Cualquier persona de su organización puede conectarse de forma remota a la red corporativa a través de una red privada virtual en un HoloLens. HoloLens también pueden tener acceso a redes Wi-Fi que requieran credenciales.
* **Microsoft Store para empresas.** El departamento de TI también puede configurar un almacén privado enterprise, que contiene solo las aplicaciones de su empresa para su uso HoloLens específicos. Distribuir el software enterprise al grupo seleccionado de usuarios de empresas de manera segura.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition frente a Conjunto de aplicaciones comercial

<table>
<tr>
<th>Características</th><th>Development Edition</th><th>Conjunto de aplicaciones comercial</th>
</tr><tr>
<td>Cifrado del dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Red privada virtual (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modo de pantalla completa</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Implementación y administración</th>
</tr><tr>
<td>Administración de dispositivos móviles (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Capacidad de bloquear la anulación de la inscripción</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Acceso Wi-Fi corporativa basada en certificado</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumidor)</td><td style="text-align: center;">Consumidor</td><td style="text-align: center;">Filtrado a través de MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portal de empresa Store</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Identidad y seguridad</th>
</tr><tr>
<td>Inicio de sesión con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Inicio de sesión con la cuenta de Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenciales próxima generación con PIN desbloquear</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Arranque seguro</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Mantenimiento y soporte técnico</th>
</tr><tr>
<td>Las actualizaciones automáticas sistema cuando llegan</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update para empresas</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rama de mantenimiento a largo plazo</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión - mayo de 2016](release-notes-may-2016.md)
* [Notas de la versión: marzo de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Problemas conocidos de HoloLens](hololens-known-issues.md)
* [Características comerciales](commercial-features.md)
* [Instalar las herramientas](install-the-tools.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
