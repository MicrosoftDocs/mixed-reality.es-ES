---
title: Entrada de teclado en Unity
description: Unity proporciona la clase TouchScreenKeyboard para aceptar la entrada de teclado cuando no hay ningún teclado físico disponible.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: teclado, entrada, Unity, touchscreenkeyboard
ms.openlocfilehash: f506415f9658d9723bf31b339d63fe4569100ace
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438553"
---
# <a name="keyboard-input-in-unity"></a>Entrada de teclado en Unity

**Espacio de nombres:** *UnityEngine*<br>
 **Tipo**:  *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Aunque HoloLens admite muchas formas de entrada, incluidos los teclados Bluetooth, la mayoría de las aplicaciones no puede suponer que todos los usuarios tendrán un teclado físico disponible. Si la aplicación requiere una entrada de texto, se debe proporcionar alguna forma de teclado en pantalla.

Unity proporciona la clase *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceptar la entrada de teclado cuando no hay ningún teclado físico disponible.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamiento del teclado del sistema HoloLens en Unity

En HoloLens, el *TouchScreenKeyboard* aprovecha el teclado en pantalla del sistema. El teclado en pantalla del sistema no se puede superponer sobre una vista volumétrica, por lo que Unity tiene que crear una vista XAML 2D secundaria para mostrar el teclado y volver a la vista volumétrica una vez que se ha enviado la entrada. El flujo de usuario es similar al siguiente:
1. El usuario realiza una acción que hace que el código de la aplicación llame a *TouchScreenKeyboard*
    * La aplicación es responsable de pausar el estado de la aplicación antes de llamar a *TouchScreenKeyboard*
    * La aplicación puede finalizar antes de volver a cambiar a la vista volumétrica.
2. Unity cambia a una vista XAML 2D que se coloca automáticamente en el mundo.
3. El usuario escribe texto mediante el teclado del sistema y lo envía o cancela.
4. Unity vuelve a cambiar a la vista volumétrica
    * La aplicación es responsable de reanudar el estado de la aplicación cuando se realiza la *TouchScreenKeyboard*
5. El texto enviado está disponible en *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Vistas del teclado disponibles

Hay seis vistas de teclado diferentes disponibles:
* Cuadro de texto de una sola línea
* Cuadro de texto de una sola línea con título
* Cuadro de texto de varias líneas
* Cuadro de texto de varias líneas con título
* Cuadro de contraseña de una sola línea
* Cuadro de contraseña de una sola línea con título

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Cómo habilitar el teclado del sistema en Unity

El teclado del sistema HoloLens solo está disponible para las aplicaciones de Unity que se exportan con el "tipo de compilación de UWP" establecido en "XAML". Hay inconvenientes que debe realizar al elegir "XAML" como "tipo de compilación de UWP" sobre "D3D". Si no está familiarizado con esos inconvenientes, puede que desee explorar una [solución de entrada alternativa](#alternative-keyboard-options) al teclado del sistema.
1. Abra el menú **archivo** y seleccione **configuración de compilación..** .
2. Asegúrese de que la **plataforma** esté establecida en **tienda Windows**, que el **SDK** esté establecido en **universal 10**y establezca el **tipo de compilación de UWP** en **XAML**.
3. En el cuadro de diálogo **configuración de compilación** , haga clic en el botón **configuración del reproductor...**
4. Seleccionar la **configuración de la pestaña de la tienda Windows**
5. Expandir el grupo **otras configuraciones**
6. En la sección **representación** , active la casilla **compatibilidad con realidad virtual** para agregar una nueva lista de **dispositivos de realidad virtual**
7. Asegúrese de que **Windows Holographic** aparece en la lista de SDK de realidad virtual

>[!NOTE]
>Si no marca la compilación como realidad virtual compatible con el dispositivo HoloLens, el proyecto se exportará como una aplicación XAML 2D.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Uso del teclado del sistema en la aplicación de Unity

### <a name="declare-the-keyboard"></a>Declarar el teclado

En la clase, declare una variable para almacenar el *TouchScreenKeyboard* y una variable que contenga la cadena que devuelve el teclado.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Invocar el teclado

Cuando se produce un evento que solicita una entrada de teclado, llame a una de estas funciones según el tipo de entrada que desee. Tenga en cuenta que el título se especifica en el parámetro textPlaceholder.

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

En el bucle de actualización, compruebe si el teclado ha recibido una nueva entrada y almacénela para su uso en otra parte.

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

## <a name="alternative-keyboard-options"></a>Opciones de teclado alternativas

Sabemos que el desactivador de una vista volumétrica en una vista 2D no es la manera ideal de obtener entradas de texto del usuario.

Las alternativas actuales para aprovechar el teclado del sistema mediante Unity incluyen:
* Usar el dictado de voz para la entrada (<b>Nota:</b> a menudo esto es propenso a errores para las palabras que no se encuentran en el Diccionario y no es adecuada para la entrada de contraseña)
* Crear un teclado que funcione en la vista exclusiva de aplicaciones
