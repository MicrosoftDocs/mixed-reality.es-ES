---
title: Entradas mediante teclado en Unity
description: Unity proporciona la clase TouchScreenKeyboard para aceptar la entrada de teclado cuando no hay disponible ningún teclado físico.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: unity de entrada, teclado, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605741"
---
# <a name="keyboard-input-in-unity"></a>Entradas mediante teclado en Unity

**Namespace:** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Mientras HoloLens admite muchos formatos de entrada, incluidos los teclados Bluetooth, la mayoría de las aplicaciones no puede suponer que todos los usuarios tendrán un teclado físico disponible. Si la aplicación requiere una entrada de texto, se debe proporcionar algún tipo de teclado en pantalla.

Unity proporciona el *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* clase para aceptar la entrada de teclado cuando no hay disponible ningún teclado físico.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamiento de teclado del sistema de HoloLens en Unity

En HoloLens, el *TouchScreenKeyboard* aprovecha el teclado en pantalla del sistema. Teclado en pantalla del sistema no puede superponer sobre una vista volumétrica, por lo que Unity tiene que crear una vista XAML 2D secundaria para mostrar el teclado, a continuación, devolver a la vista volumétrica una vez que se ha enviado la entrada. El flujo de usuario es el siguiente:
1. El usuario realiza una acción haciendo que el código de aplicación llamar a *TouchScreenKeyboard*
    * La aplicación es responsable de estado de la aplicación Pausando antes de llamar a *TouchScreenKeyboard*
    * La aplicación puede finalizar antes de cambiar alguna vez a la vista volumétrica
2. Unity cambia a la vista XAML 2D que se encuentra ubicados automáticamente en el mundo
3. El usuario escribe texto mediante el teclado del sistema y envía o se cancela
4. Unity vuelve a cambiar a la vista volumétrica
    * La aplicación es responsable de reanudar la aplicación de estado cuando el *TouchScreenKeyboard* se realiza
5. Está disponible en el texto presentado el *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Vistas de teclado disponibles

Hay seis vistas diferentes de teclado disponibles:
* Cuadro de texto multilínea
* Cuadro de texto multilínea con título
* Cuadro de texto multilínea
* Cuadro de texto de varias líneas con título
* Cuadro de contraseña de la línea
* Cuadro de contraseña de la línea con título

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Cómo habilitar el teclado del sistema en Unity

El teclado del sistema HoloLens solo está disponible para las aplicaciones de Unity que se exportan con el "UWP compilar tipo" establecido en "XAML". Hay equilibrios que realizar cuando se elige "XAML" como el "tipo de generación de UWP" sobre "D3D". Si no está familiarizado con estos inconvenientes, puede desear explorar un [solución de entrada alternativos](#alternative-keyboard-options) para el teclado del sistema.
1. Abra el **archivo** menú y seleccione **configuración de compilación...**
2. Asegúrese del **plataforma** está establecido en **Windows Store**, el **SDK** está establecido en **10 Universal**y establezca el **el tipo de compilación para UWP**  a **XAML**.
3. En el **configuración de compilación** cuadro de diálogo, haga clic en el **configuración del Reproductor...**  botón
4. Seleccione el **configuración para Windows Store** ficha
5. Expanda el **otra configuración** grupo
6. En el **representación** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar un nuevo **dispositivos de realidad Virtual** lista
7. Asegúrese de **Windows Holographic** aparece en la lista de SDK de realidad Virtual

>[!NOTE]
>Si no marca la compilación como admite la realidad Virtual con el dispositivo HoloLens, exportará el proyecto como una aplicación XAML 2D.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Usar el teclado del sistema en la aplicación de Unity

### <a name="declare-the-keyboard"></a>Declare el teclado

En la clase, declare una variable para almacenar el *TouchScreenKeyboard* y devuelve una variable que contenga la cadena en el teclado.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Invocar el teclado

Cuando la solicitud de entrada de teclado produce un evento, llame a una de estas funciones según el tipo de entrada deseado. Tenga en cuenta que el título se especifica en el parámetro textPlaceholder.

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a>Recuperar contenido con tipo

En el bucle de actualización, compruebe si el teclado recibió una entrada nueva y almacenarla para su uso en otro lugar.

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a>Opciones de teclado alternativo

Somos conscientes de que desactivando una vista en una vista 2D volumétrica no ideales para obtener la entrada de texto del usuario.

Las alternativas actuales a aprovechar el teclado del sistema a través de Unity incluyen:
* Utilizando el dictado de voz de entrada (<b>Nota:</b> esto a menudo es propenso a errores no se encuentra en el diccionario de palabras y no es adecuado como entrada de contraseña)
* Creación de un teclado que funciona en la vista exclusiva de las aplicaciones
