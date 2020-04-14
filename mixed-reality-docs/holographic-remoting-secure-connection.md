---
title: Establecimiento de una conexión segura con Holographic Remoting
description: En esta página se explica cómo establecer una conexión cifrada segura cuando se usa la comunicación remota holográfica.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278233"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Establecimiento de una conexión segura con Holographic Remoting

>[!IMPORTANT]
>Esta guía es específica de Holographic Remoting en HoloLens 2.

En esta página se explica cómo establecer una conexión cifrada segura cuando se usa la comunicación remota holográfica.

Al streaming de contenido a HoloLens 2 a través de una red no segura, como un WiFi abierto o Internet, se recomienda encarecidamente usar una conexión cifrada.

>[!IMPORTANT]
>Incluso cuando se usa una red Wi-Fi local de confianza mediante una conexión cifrada, debe tenerse en cuenta.

Para poder usar una conexión cifrada, debe implementar un [reproductor personalizado](holographic-remoting-create-player.md) y una [aplicación remota personalizada](holographic-remoting-create-host.md).

El cifrado se logra mediante el uso de la implementación de TLS de las plataformas subyacentes.

## <a name="basics-of-an-encrypted-connection"></a>Conceptos básicos de una conexión cifrada

Los objetos siguientes deben implementarse para permitir un intercambio de certificados.

>[!TIP]
>La implementación de interfaces de WinRT se puede C++realizar fácilmente mediante/WinRT. En el capítulo [API C++de autor con/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) se describe con más detalle.

>[!IMPORTANT]
>El ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` en el paquete NuGet contiene documentación detallada sobre la API relacionada con las conexiones seguras.

1) Objeto de certificado, que necesita implementar la interfaz de ```ICertificate```.

    * Devuelve el contenido binario del certificado pfx a través del método ```GetCertificatePfx```. Igual que el contenido binario de un archivo. pfx.
    * Devuelve el nombre del firmante del certificado a través de ```GetSubjectName```.
    * Devuelva la contraseña pfx a través de ```GetPfxPassword```. Devuelve una cadena vacía para un archivo PFX sin protección.

2) Un proveedor de certificados que implementa la interfaz de ```ICertificateProvider``` que proporciona un certificado cuando se le solicita a través del método ```GetCertificate```.

3) Un validador de certificado que implementa la interfaz ```ICertificateValidator```. Su tarea consiste en comprobar los certificados entrantes.
    * El método ```PerformSystemValidation``` debe devolver ```true``` cuando la plataforma subyacente debe validar la cadena de certificados entrante; de lo contrario ```false```.
    * el contexto del cliente llama a ```ValidateCertificate``` para solicitar la validación de un certificado. Este método acepta la cadena de certificados (con el primer certificado que es el certificado de sujeto), el nombre del servidor con el que se establece la conexión y si se debe forzar una comprobación de revocación. El resultado de la validación del sistema se proporcionará si se ha solicitado la validación por parte del sistema subyacente. Para continuar el procesamiento de ```CertificateValidated``` con el resultado adecuado o ```Cancel``` se debe llamar a para cancelar la validación en la ```ICertificateValidationCallback```pasada.

Además, para permitir el intercambio de un token seguro, es necesario implementar los objetos siguientes.

1) Proveedor de autenticación que implementa la interfaz ```IAuthenticationProvider```. El contexto del cliente llama a su método ```GetToken``` para solicitar un token para la autenticación del cliente. Para continuar ```TokenReceived``` para proporcionar el token de autenticación y continuar con el proceso de conexión o ```Cancel``` para cancelar el proceso debe llamarse en la ```IAuthenticationProviderCallback```pasada.
2) Receptor de autenticación que implementa la interfaz ```IAuthenticationReceiver```. Su tarea consiste en validar los tokens entrantes.
    * El método ```GetRealm``` debe devolver el nombre del dominio Kerberos de autenticación.
    * El contexto de red del servidor llama al método ```ValidateToken``` para solicitar la validación de un token de autenticación del cliente. Para continuar, llame a ```ValidationCompleted``` para indicar la finalización de la validación o ```Cancel``` para rechazar la conexión de cliente. La conexión de cliente se admitirá o rechazará según el resultado de la validación que se haya pasado a ```ValidationCompleted```. 

Una vez que se implementan estos objetos ```ListenSecure``` es necesario llamar a en lugar de ```Listen``` y ```ConnectSecure``` en lugar de ```Connect``` en el contexto remoto y en el contexto del reproductor, respectivamente. ```ListenSecure``` requiere un proveedor de certificados adicional y un receptor de autenticación a través de ```Listen```. ```ConnectSecure``` requiere un proveedor de autenticación adicional y un validador de certificados en ```Connect```.

## <a name="see-also"></a>Consulta también
* [Escritura de una aplicación remota holográfica Remoting](holographic-remoting-create-host.md)
* [Escritura de una aplicación de reproductor remoto holográfica personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
