---
title: Cuentas en HoloLens
description: Cómo configurar y administrar cuentas de usuario en HoloLens.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, usuario, cuenta, aad, adfs, cuenta microsoft, msa, credenciales
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599828"
---
# <a name="accounts-on-hololens"></a>Cuentas en HoloLens

Durante la instalación inicial de HoloLens, los usuarios deben iniciar sesión con la cuenta que desean usar en el dispositivo. Esta cuenta puede ser una cuenta de Microsoft de consumidor o una cuenta de empresa que se ha configurado en Azure Active Directory (AAD) o servicios de federación de Active Directory (ADFS).

Iniciar sesión en esta cuenta durante la instalación, crea un perfil de usuario en el dispositivo que el usuario puede utilizar para iniciar sesión, y con qué todas las aplicaciones almacenarán los datos. También proporciona esta misma cuenta de inicio de sesión único para aplicaciones como borde o Skype a través de las API del Administrador de cuenta de Windows.

Además, al iniciar sesión en una empresa o una cuenta profesional en el dispositivo, lo también puede aplicar directivas de administración de dispositivos móviles (MDM), si configura el Administrador de TI.

Cada vez que el dispositivo se reinicia o se reanuda desde el modo de espera, se usan las credenciales para esta cuenta para el inicio de sesión de nuevo. Si está habilitada la opción de exigir un inicio de sesión explícito en la configuración, el usuario se le pedirá que vuelva a escribir sus credenciales. Cada vez que el dispositivo se reinicia después de recibir y aplicar una actualización del SO, en un sesión explícito se requiere.

## <a name="multi-user-support"></a>Compatibilidad con varios usuario

>[!NOTE]
>Compatibilidad con varios usuario requiere Commercial Suite, como se trata de un [Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) característica.

A partir de la [Windows 10 de abril de 2018 Update](release-notes-april-2018.md), HoloLens admite varios usuarios desde dentro del mismo inquilino AAD. Para utilizar esta debe configurar el dispositivo inicialmente con una cuenta que pertenezca a su organización. Posteriormente, otros usuarios desde el mismo inquilino podrán iniciar sesión en el dispositivo desde la pantalla de inicio de sesión o al pulsar el icono del usuario en el panel de inicio para cerrar la sesión el usuario existente. 

Las aplicaciones instaladas en el dispositivo estará disponibles para todos los demás usuarios, pero cada uno tendrá sus propios datos de la aplicación y las preferencias. Quitar una aplicación también quitará los demás usuarios aunque. 

Puede quitar los usuarios de dispositivos desde el dispositivo para recuperar espacio para ello, vaya a Configuración > cuentas > otras personas. Esto también quitará todos datos de aplicación los demás usuarios desde el dispositivo. 

## <a name="linked-accounts"></a>Cuentas vinculadas

Dentro de una cuenta de dispositivo único, los usuarios pueden vincular las credenciales de cuenta web adicional con el fin de facilitar el acceso dentro de las aplicaciones (por ejemplo, el Store) o para combinar el acceso a recursos personales y profesionales, similares a la versión de escritorio de Windows. Iniciar sesión en una cuenta adicional de este modo no separa los datos de usuario creados en el dispositivo, como imágenes o descarga. Una vez que una cuenta se ha conectado a un dispositivo, pueden hacer que las aplicaciones de uso de ella con su permiso para reducir la necesidad de iniciar sesión en cada aplicación de forma individual.

## <a name="using-single-sign-on-within-an-app"></a>Uso de inicio de sesión único dentro de una aplicación

Como desarrollador de aplicaciones, puede aprovechar las ventajas de contar con una identidad conectada en HoloLens con el [API del Administrador de cuenta de Windows](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx), tal como lo haría en otros dispositivos de Windows. Algunos ejemplos de código para estas API están disponibles [aquí](http://go.microsoft.com/fwlink/p/?LinkId=620621).

Consentimiento de interrupciones de cualquier cuenta que se pueden producir como usuario solicitante para obtener información de cuenta, debe controlarse la autenticación en dos fases etc. cuando la aplicación solicita un token de autenticación.

Si la aplicación requiere un tipo de cuenta específico que no se ha vinculado anteriormente, la aplicación puede solicitar al sistema que pedir al usuario que agregue uno. Esto desencadenará el panel de configuración de la cuenta que se iniciará como un elemento secundario modal de la aplicación. Para aplicaciones 2D, esta ventana se representará directamente sobre el centro de la aplicación y para las aplicaciones de Unity, este proceso tardará brevemente del usuario de la aplicación holographic para que se puede representar esta ventana secundaria. Personalización de los comandos y las acciones en este panel se describe [aquí](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx).

## <a name="enterprise-and-other-authentication"></a>Enterprise y otro tipo de autenticación

Si la aplicación hace uso de otros tipos de autenticación, como NTLM, Basic o Kerberos, puede usar [la interfaz de usuario de credenciales de Windows](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) para recopilar, procesar y almacenar las credenciales del usuario. La experiencia del usuario para recopilar las credenciales de estas es muy similar a otra nube controlado por interrupciones de la cuenta y aparecen como una aplicación secundaria encima de la aplicación 2D o al suspender brevemente una aplicación de Unity para mostrar la interfaz de usuario.

## <a name="deprecated-apis"></a>API en desuso

Una diferencia para el desarrollo de HoloLens de escritorio es que [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API no es totalmente compatible. Aunque devolverá que un token si la cuenta principal está en buena independientes, se interrumpe, como los descritos anteriormente no mostrará ninguna interfaz de usuario para el usuario y se producirá un error al autenticar correctamente la cuenta.

