---
title: Características comerciales
description: Microsoft HoloLens Commercial Suite incluye características que facilitan a las empresas a administrar los dispositivos HoloLens.
author: xerxesb85
ms.author: xerxesb
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, comerciales, características, mdm, administración de dispositivos móviles, de modo de pantalla completa
ms.openlocfilehash: 5fd5c56983fb3e94376fac08c6e96510bccc0002
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605762"
---
# <a name="commercial-features"></a>Características comerciales

Microsoft HoloLens Commercial Suite incluye características que facilitan a las empresas a administrar los dispositivos HoloLens. Las características comerciales se incluyen en el sistema operativo de Windows, pero están habilitadas por una licencia. En casi todos los casos, la licencia está habilitada por la administración de dispositivos de Microsoft cuando HoloLens se inscripción en una organización. Póngase en contacto con su administrador de cuenta local de Microsoft para adquirir Commercial Suite de Microsoft HoloLens.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

## <a name="key-commercial-features"></a>Características comerciales clave

* **Modo de pantalla completa.** Con el modo de quiosco de HoloLens, puede limitar las aplicaciones que desea ejecutar para habilitar experiencias completas de demostración o presentación.

  ![Con el modo de quiosco, HoloLens inicia directamente desde la aplicación de su elección.](images/201608-kioskmode-400px.png)

* **Administración de dispositivos móviles (MDM) para HoloLens.** El departamento de TI puede administrar varios dispositivos HoloLens simultáneamente con soluciones como Microsoft Intune. Podrás administrar la configuración, seleccionar qué aplicaciones instalar y establecer las opciones de configuración de seguridad adaptadas a las necesidades de su organización.

  ![Administración de dispositivos móviles en HoloLens proporciona administración de dispositivos de nivel de empresa en varios dispositivos.](images/201608-enterprisemanagement-400px.png)
  
* **Windows Update para empresas.** Controla las actualizaciones del sistema operativo en dispositivos y soporte técnico para la rama de mantenimiento a largo plazo.
* **Seguridad de los datos.** El cifrado de BitLocker está habilitado en HoloLens para proporcionar el mismo nivel de protección de seguridad como cualquier otro dispositivo de Windows.
* **Acceso al trabajo.** Cualquier persona de su organización puede conectarse de forma remota a la red corporativa a través de una red privada virtual en un HoloLens. HoloLens también pueden tener acceso a redes Wi-Fi que requieran credenciales.
* **Microsoft Store para empresas.** El departamento de TI también puede configurar un almacén privado enterprise, que contiene solo las aplicaciones de su empresa para su uso HoloLens específicos. Distribuir el software enterprise al grupo seleccionado de usuarios de empresas de manera segura.

## <a name="development-edition-vs-commercial-suite"></a>Development Edition frente a Conjunto de aplicaciones comercial

<table>
<tr>
<th>Características</th><th>HoloLens Development Edition</th><th>HoloLens Commercial Suite</th><th>HoloLens 2</th>
</tr><tr>
<td>Cifrado del dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Red privada virtual (VPN)</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">Modo de pantalla completa</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Implementación y administración</th>
</tr><tr>
<td>Administración de dispositivos móviles (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Capacidad de bloquear la anulación de la inscripción</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Acceso Wi-Fi corporativa basada en certificado</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumidor)</td><td style="text-align: center;">Consumidor</td><td style="text-align: center;">Filtrado a través de MDM</td><td style="text-align: center;">Filtrado a través de MDM</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">Portal de empresa Store</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Identidad y seguridad</th>
</tr><tr>
<td>Inicio de sesión con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Inicio de sesión con la cuenta de Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenciales próxima generación con PIN desbloquear</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">Arranque seguro</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Mantenimiento y soporte técnico</th>
</tr><tr>
<td>Las actualizaciones automáticas sistema cuando llegan</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">Windows Update para empresas</a></td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rama de mantenimiento a largo plazo</td><td></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>



## <a name="enabling-commercial-features"></a>Habilitar las características comerciales

Las características comerciales, como Microsoft Store para empresas, modo de pantalla completa, y acceso Wi-Fi de empresa están configuradas por una organización Administrador de TI. El [centro de TI de Windows para HoloLens](https://technet.microsoft.com/itpro/hololens/index) proporciona instrucciones paso a paso para instalar aplicaciones desde Microsoft Store para empresas e inscripción de dispositivos.

## <a name="see-also"></a>Vea también
* [IT Pro guía para HoloLens](https://technet.microsoft.com/itpro/hololens/index)
* [Modo de pantalla completa](using-the-windows-device-portal.md#kiosk-mode)
* [CSP admitidos en Windows Holographic para enterprise](https://msdn.microsoft.com/library/windows/hardware/dn920025(v=vs.85).aspx#HoloLens)
* [Microsoft Store para empresas y aplicaciones empresariales](https://blogs.technet.microsoft.com/sbucci/2016/04/13/windows-store-for-business-and-line-of-business-applications/)
* [Trabajar con aplicaciones de línea de negocio](https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps)
