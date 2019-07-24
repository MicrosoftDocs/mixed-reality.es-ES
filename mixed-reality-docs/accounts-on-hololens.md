---
title: Cuentas en HoloLens
description: Cómo configurar y administrar cuentas de usuario en HoloLens.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, usuario, cuenta, AAD, ADFS, cuenta Microsoft, MSA, credenciales
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516815"
---
# <a name="accounts-on-hololens"></a>Cuentas en HoloLens

Durante la configuración inicial de HoloLens, los usuarios deben iniciar sesión con la cuenta que quieran usar en el dispositivo. Esta cuenta puede ser una cuenta de Microsoft de consumidor o una cuenta de empresa configurada en Azure Active Directory (AAD) o Servicios de federación de Active Directory (AD FS) (ADFS).

Al iniciar sesión en esta cuenta durante la instalación, se crea un perfil de usuario en el dispositivo que el usuario puede usar para iniciar sesión y en el que todas las aplicaciones almacenarán sus datos. Esta misma cuenta también proporciona un inicio de sesión único para aplicaciones como Edge o Skype a través de las API del administrador de cuentas de Windows.

Además, al iniciar sesión en una cuenta de empresa o de organización en el dispositivo, también puede aplicar la Directiva de administración de dispositivos móviles (MDM), si la configura el administrador de ti.

Siempre que el dispositivo se reinicie o se reanude de modo de espera, se usarán las credenciales de esta cuenta para iniciar sesión de nuevo. Si la opción que aplica un inicio de sesión explícito está habilitada en la configuración, el usuario deberá volver a escribir sus credenciales. Cada vez que se reinicia el dispositivo después de recibir y aplicar una actualización del sistema operativo, se requiere un inicio de sesión explícito.

## <a name="multi-user-support"></a>Compatibilidad con varios usuarios

>[!NOTE]
>La compatibilidad con varios usuarios requiere Commercial Suite, ya que se trata de una característica [de Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) .

A partir de la [actualización del 2018 de abril de Windows 10](release-notes-april-2018.md), HoloLens admite varios usuarios en el mismo inquilino de AAD. Para usarlo, debe configurar el dispositivo inicialmente con una cuenta que pertenezca a su organización. Posteriormente, otros usuarios del mismo inquilino podrán iniciar sesión en el dispositivo desde la pantalla de inicio de sesión o pulsar el icono de usuario en el panel Inicio para cerrar la sesión del usuario existente. 

Las aplicaciones instaladas en el dispositivo estarán disponibles para todos los demás usuarios, pero cada una de ellas tendrá sus propios datos de aplicación y preferencias. Sin embargo, al quitar una aplicación también se quitará de todos los demás usuarios. 

Puede quitar usuarios de dispositivos del dispositivo para recuperar espacio; para ello, vaya a Configuración > cuentas > otras personas. Esto también quitará todos los datos de la aplicación de otros usuarios del dispositivo. 

## <a name="linked-accounts"></a>Cuentas vinculadas

Dentro de una sola cuenta de dispositivo, los usuarios pueden vincular credenciales de cuenta web adicionales con el fin de facilitar el acceso dentro de las aplicaciones (por ejemplo, la tienda) o para combinar el acceso a recursos personales y de trabajo, de forma similar a la versión de escritorio de Windows. Iniciar sesión en una cuenta adicional de este modo no separa los datos de usuario creados en el dispositivo, como imágenes o descargas. Una vez que una cuenta se ha conectado a un dispositivo, las aplicaciones pueden hacer uso de ella con su permiso para reducir la necesidad de iniciar sesión en cada aplicación de forma individual.

## <a name="using-single-sign-on-within-an-app"></a>Uso del inicio de sesión único en una aplicación

Como desarrollador de aplicaciones, puede aprovechar la posibilidad de tener una identidad conectada en HoloLens con las [API del administrador de cuentas de Windows](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx), igual que haría en otros dispositivos Windows. Algunos ejemplos de código de estas API están disponibles [aquí](http://go.microsoft.com/fwlink/p/?LinkId=620621).

Las interrupciones de cuenta que pueden producirse, como solicitar el consentimiento del usuario para la información de la cuenta, la autenticación en dos fases, etc., deben administrarse cuando la aplicación solicita un token de autenticación.

Si la aplicación requiere un tipo de cuenta específico que no se ha vinculado anteriormente, la aplicación puede pedir al sistema que solicite al usuario que agregue uno. Esto desencadenará el panel Configuración de la cuenta para que se inicie como un elemento secundario modal de la aplicación. En el caso de las aplicaciones 2D, esta ventana se representará directamente en el centro de la aplicación y en las aplicaciones de Unity, lo que hará que el usuario salga de la aplicación holográfica para que se pueda representar esta ventana secundaria. La personalización de los comandos y las acciones de este panel se describe [aquí](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx).

## <a name="enterprise-and-other-authentication"></a>Empresa y otra autenticación

Si la aplicación hace uso de otros tipos de autenticación, como NTLM, básico o Kerberos, puede usar la interfaz de usuario de credenciales de [Windows](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) para recopilar, procesar y almacenar las credenciales del usuario. La experiencia del usuario para recopilar estas credenciales es muy similar a otras interrupciones de cuentas controladas por la nube y se mostrarán como una aplicación secundaria en la parte superior de la aplicación 2D, o bien suspenderán brevemente una aplicación de Unity para mostrar la interfaz de usuario.

## <a name="deprecated-apis"></a>API en desuso

Una diferencia en el desarrollo en HoloLens desde el escritorio es que [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API no es totalmente compatible. Aunque devolverá un token si la cuenta principal está en buen estado, las interrupciones como las descritas anteriormente no mostrarán ninguna interfaz de usuario para el usuario y no podrán autenticarse correctamente la cuenta.

