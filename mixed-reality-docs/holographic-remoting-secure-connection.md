---
title: Establecimiento de una conexión segura con Holographic Remoting
description: En esta página se explica cómo establecer una conexión cifrada segura cuando se usa la comunicación remota holográfica.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 5bc039d7a1e500f577c4a30d2d082b718a45a8b4
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718079"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Establecimiento de una conexión segura con Holographic Remoting

>[!IMPORTANT]
>Esta guía es específica de Holographic Remoting en HoloLens 2.

En esta página se explica cómo establecer una conexión cifrada segura cuando se usa la comunicación remota holográfica.

Al streaming de contenido a HoloLens 2 a través de una red no segura, como un WiFi abierto o Internet, se recomienda encarecidamente usar una conexión cifrada.

>[!IMPORTANT]
>Incluso cuando se usa una red Wi-Fi local de confianza mediante una conexión cifrada, debe tenerse en cuenta.

Para poder usar una conexión cifrada, debe implementar un [reproductor personalizado](holographic-remoting-create-player.md) y una [aplicación host personalizada](holographic-remoting-create-host.md).

El cifrado se logra mediante el uso de la implementación de TLS de las plataformas subyacentes.

## <a name="basics-of-an-encrypted-connection"></a>Conceptos básicos de una conexión cifrada

Los objetos siguientes deben implementarse para permitir un intercambio de certificados.

>[!TIP]
>La implementación de interfaces de WinRT se puede C++realizar fácilmente mediante/WinRT. En el capítulo [API C++de autor con/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/author-apis) se describe con más detalle.

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` En el paquete de NuGet se incluye documentación detallada sobre la API relacionada con las conexiones seguras.

1) Objeto de certificado, que necesita implementar la ```ICertificate``` interfaz.

    * Devuelve el contenido binario del certificado pfx a través ```GetCertificatePfx``` del método. Igual que el contenido binario de un archivo. pfx.
    * Devuelva el nombre del firmante ```GetSubjectName```del certificado a través de.
    * Devuelva la contraseña pfx ```GetPfxPassword```a través de. Devuelve una cadena vacía para un archivo PFX sin protección.

2) Un proveedor de certificados que ```ICertificateProvider``` implementa la interfaz, que proporciona un certificado cuando ```GetCertificate``` se le solicita a través del método.

3) Un validador de certificado ```ICertificateValidator``` que implementa la interfaz. Su tarea consiste en comprobar los certificados entrantes.
    * El ```PerformSystemValidation``` método debe devolver ```true``` cuando la plataforma subyacente debe validar la cadena de certificados entrante ```false``` ; de lo contrario,.
    * ```ValidateCertificate```el contexto del cliente llama a para solicitar la validación de un certificado. Este método acepta la cadena de certificados (con el primer certificado que es el certificado de sujeto), el nombre del servidor con el que se establece la conexión y si se debe forzar una comprobación de revocación. El resultado de la validación del sistema se proporcionará si se ha solicitado la validación por parte del sistema subyacente. Para continuar el procesamiento ```CertificateValidated``` con el resultado adecuado o ```Cancel``` para cancelar la validación, es necesario llamar a en ```ICertificateValidationCallback```el pasado.

Además, para permitir el intercambio de un token seguro, es necesario implementar los objetos siguientes.

1) Un proveedor de autenticación que ```IAuthenticationProvider``` implementa la interfaz. El ```GetToken``` contexto del cliente llama a su método para solicitar un token para la autenticación del cliente. Para continuar con ```TokenReceived``` el fin de proporcionar el token de autenticación y continuar el ```Cancel``` proceso de conexión o para cancelar el proceso, es necesario ```IAuthenticationProviderCallback```llamar a en el pasado.
2) Receptor de autenticación que implementa ```IAuthenticationReceiver``` la interfaz. Su tarea consiste en validar los tokens entrantes.
    * El ```GetRealm``` método debe devolver el nombre del dominio Kerberos de autenticación.
    * El ```ValidateToken``` contexto de red del servidor llama al método para solicitar la validación de un token de autenticación del cliente. Para continuar con la ```ValidationCompleted``` llamada a la finalización de la ```Cancel``` validación o para rechazar la conexión de cliente. La conexión de cliente se admitirá o rechazará según el resultado de la ```ValidationCompleted```validación que se haya pasado a. 

Una vez implementados ```ListenSecure``` estos objetos, es necesario llamar a en lugar ```ConnectSecure``` de ```Listen``` y en ```Connect``` lugar de hacerlo en el contexto remoto y en el contexto del reproductor, respectivamente. ```ListenSecure```requiere un proveedor de certificados adicional y un receptor ```Listen```de autenticación a través de. ```ConnectSecure```requiere un proveedor de autenticación adicional y un validador ```Connect```de certificado.

## <a name="see-also"></a>Vea también
* [Escritura de una aplicación de host de Holographic Remoting](holographic-remoting-create-host.md)
* [Escritura de una aplicación de reproductor remoto holográfica personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de Holographic Remoting](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)