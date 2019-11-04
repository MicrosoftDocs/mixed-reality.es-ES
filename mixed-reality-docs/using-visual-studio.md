---
title: Usar Visual Studio para implementar y depurar
description: Cómo compilar, depurar e implementar aplicaciones para HoloLens y Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
keywords: Visual Studio, HoloLens, realidad mixta, depurar, implementar
ms.openlocfilehash: 2b84183417a1bd4eaa90eef58bebe2b65966b933
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437296"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Usar Visual Studio para implementar y depurar

Si quiere usar DirectX o Unity para desarrollar la aplicación de realidad mixta, usará Visual Studio para la depuración e implementación. En esta sección, aprenderá lo siguiente:
* Cómo implementar aplicaciones en un casco con HoloLens o Windows Mixed Reality a través de Visual Studio.
* Cómo usar el emulador de HoloLens integrado en Visual Studio.
* Cómo depurar aplicaciones de realidad mixta.

## <a name="prerequisites"></a>Requisitos previos
1. Vea [instalar las herramientas](install-the-tools.md) para obtener instrucciones de instalación.
2. Cree un nuevo proyecto de aplicación universal de Windows en Visual Studio.  Para HoloLens (1ª generación), use Visual Studio 2017 o una versión más reciente.  Para Hololens 2, use Visual Studio 2019 16,2 o una versión más reciente. C#y C++ se admiten. (O siga las instrucciones para [crear una aplicación en Unity](holograms-100.md)).

## <a name="enabling-developer-mode"></a>Habilitar el modo de desarrollador

Comience habilitando el **modo de desarrollador** en el dispositivo para que Visual Studio pueda conectarse a él.

### <a name="hololens"></a>HoloLens
1. Encienda HoloLens y colóquelo en el dispositivo.
2. Realiza el gesto [nástico](system-gesture.md#bloom) para iniciar el menú principal.
3. Mira el icono de **configuración** y realiza el gesto [de puntear](gaze-and-commit.md#composite-gestures) en el aire. Realiza un segundo toque en el aire para colocar la aplicación en tu entorno. La aplicación Configuración se iniciará una vez la hayas colocado.
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilita el **Modo de desarrollador**. Esto le permitirá [implementar aplicaciones desde Visual Studio](using-visual-studio.md) en HoloLens.
7. Opcional: Desplácese hacia abajo y habilite también el **portal de dispositivos**. Esto también le permitirá conectarse a [Windows Device portal](using-the-windows-device-portal.md) en su HoloLens desde un explorador Web.

### <a name="windows-pc"></a>PC Windows

Si está trabajando con un casco de realidad mixta de Windows conectado a su PC, debe habilitar el **modo de desarrollador** en el equipo.
1. Ir a **configuración**
2. Seleccionar **actualización y seguridad**
3. Seleccionar **para desarrolladores**
4. Habilite el **modo de desarrollador**, lea la declinación de responsabilidades de la configuración elegida y haga clic en sí para aceptar el cambio.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Implementación de una aplicación a través de Wi-Fi-HoloLens (1ª generación)
1. Seleccione una configuración de compilación **x86** para la aplicación ![configuración de compilación x86 en Visual Studio](images/x86setting.png)
2. Seleccione **equipo remoto** en el menú desplegable destino de implementación ![destino de implementación de equipo remoto en Visual Studio](images/remotemachinesetting.png)
3. Para C++ los proyectos de y JavaScript, vaya a **Project > propiedades > propiedades de configuración > depuración**. En C# el caso de los proyectos, aparecerá un cuadro de diálogo automáticamente para configurar la conexión.
  a. Escriba la dirección IP del dispositivo en el campo **Dirección** o **nombre del equipo** . Busque la dirección IP en su HoloLens en **configuración > red & opciones avanzadas de Internet >** , o bien, puede solicitar a Cortana "¿Cuál es mi dirección IP?".
  b. Establezca el modo de autenticación en **universal (protocolo sin cifrar)** ![cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)
4. Seleccione depurar **> iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploywithdebugging.png)
5. La primera vez que implemente una aplicación en su HoloLens desde su PC, se le pedirá un PIN. Siga las instrucciones de **emparejamiento de su dispositivo** a continuación.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Implementación de una aplicación a través de Wi-Fi-HoloLens 2
1. Seleccione una configuración de compilación **ARM** o **ARM64** para la aplicación ![configuración de compilación de ARM64 en Visual Studio](images/arm64setting.png)
2. Seleccione **equipo remoto** en el menú desplegable destino de implementación ![destino de implementación de equipo remoto en Visual Studio](images/remotemachinesetting_arm64.png)
3. Para C++ los proyectos de y JavaScript, vaya a **Project > propiedades > propiedades de configuración > depuración**. En C# el caso de los proyectos, aparecerá un cuadro de diálogo automáticamente para configurar la conexión.
  a. Escriba la dirección IP del dispositivo en el campo **Dirección** o **nombre del equipo** . Busque la dirección IP en su HoloLens en **configuración > red & opciones avanzadas de Internet >** , o bien, puede solicitar a Cortana "¿Cuál es mi dirección IP?".
  b. Establezca el modo de autenticación en **universal (protocolo sin cifrar)** ![cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)
4. Seleccione depurar **> iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploywithdebugging.png)
5. La primera vez que implemente una aplicación en su HoloLens desde su PC, se le pedirá un PIN. Siga las instrucciones de **emparejamiento de su dispositivo** a continuación.

Si cambia la dirección IP de HoloLens, puede cambiar la dirección IP del equipo de destino yendo a **Project > propiedades > propiedades de configuración > depuración**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Implementación de una aplicación a través de USB-HoloLens (1ª generación)
1. Seleccione una configuración de compilación **x86** para la aplicación ![configuración de compilación x86 en Visual Studio](images/x86setting.png)
2. Seleccione **dispositivo** en el menú desplegable destino de implementación![implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy.png)
3. Seleccione depurar **> iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploywithdebugging.png)
4. La primera vez que implemente una aplicación en su HoloLens desde su PC, se le pedirá un PIN. Siga las instrucciones de **emparejamiento de su dispositivo** a continuación.

## <a name="deploying-an-app-over-usb---hololens-2"></a>Implementación de una aplicación a través de USB-HoloLens 2
1. Seleccione una configuración de compilación **ARM** o **ARM64** para la aplicación ![configuración de compilación de ARM64 en Visual Studio](images/arm64setting.png)
2. Seleccione **dispositivo** en el menú desplegable destino de implementación![implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy_arm64.png)
3. Seleccione depurar **> iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploywithdebugging.png)
4. La primera vez que implemente una aplicación en su HoloLens desde su PC, se le pedirá un PIN. Siga las instrucciones de **emparejamiento de su dispositivo** a continuación.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Implementación de una aplicación en un equipo local con auriculares

Siga estas instrucciones al usar un casco de realidad mixta de Windows que se conecte a su equipo o al [simulador de realidad mixta](using-the-windows-mixed-reality-simulator.md). En estos casos, solo tiene que implementar y ejecutar la aplicación en el equipo local.
1. Seleccionar una configuración de compilación **x86** o **x64** para la aplicación
2. Seleccionar **equipo local** en el menú desplegable destino de implementación
3. Seleccione **Depurar > iniciar depuración** para implementar la aplicación e iniciar la depuración

## <a name="pairing-your-device"></a>Emparejamiento del dispositivo

La primera vez que implemente una aplicación desde Visual Studio a HoloLens, se le pedirá un PIN. En HoloLens, genere un PIN iniciando la aplicación de configuración, vaya a **Update > para desarrolladores** y pulse en **Pair**. Se mostrará un PIN en HoloLens; Escriba este PIN en Visual Studio. Una vez completado el emparejamiento, pulse en **listo** en su HoloLens para descartar el cuadro de diálogo. Este equipo ya está emparejado con HoloLens y podrá implementar aplicaciones automáticamente. Repita estos pasos para todos los equipos posteriores que se usan para implementar aplicaciones en HoloLens.

Para desemparejar HoloLens de todos los equipos con los que se emparejó, inicie la aplicación de **configuración** , vaya a **Update > para desarrolladores** y pulse en **Clear (borrar**).

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Implementación de una aplicación en el emulador de HoloLens (1ª generación)
1. Asegúrese de que ha **[instalado el emulador de HoloLens](install-the-tools.md)** .
2. Seleccione una configuración de compilación **x86** para la aplicación.
configuración de compilación de ![x86 en Visual Studio](images/x86setting.png)
3. Seleccione **emulador de HoloLens** en el menú desplegable destino de implementación![el destino del emulador en Visual Studio](images/deployemulator.png)
4. Seleccione depurar **> iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Implementación de una aplicación en el emulador de HoloLens 2
1. Asegúrese de que ha **[instalado el emulador de HoloLens](install-the-tools.md)** .
2. Seleccione una configuración de compilación **x86** o **x64** para la aplicación.
configuración de compilación de ![x86 en Visual Studio](images/x86setting.png)
3. Seleccione **emulador de HoloLens 2** en el menú desplegable destino de implementación![el destino del emulador en Visual Studio](images/deployemulator2.png)
4. Seleccione depurar **> iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Depurador de gráficos para HoloLens (1ª generación)

Las herramientas de Diagnóstico de gráficos de Visual Studio son muy útiles a la hora de escribir y optimizar una aplicación holográfica. Vea [diagnóstico de gráficos de Visual Studio en MSDN](https://msdn.microsoft.com/library/hh315751.aspx) para obtener todos los detalles.

**Para iniciar el depurador de gráficos**
1. Siga las instrucciones anteriores para dirigirse a un dispositivo o emulador
2. Vaya a **Depurar > gráficos > iniciar diagnósticos**
3. La primera vez que lo haga con HoloLens, es posible que obtenga un error de "acceso denegado". Reinicie HoloLens para permitir que los permisos actualizados surtan efecto e inténtelo de nuevo.

## <a name="profiling"></a>Generación

Las herramientas de generación de perfiles de Visual Studio le permiten analizar el rendimiento y el uso de recursos de la aplicación. Esto incluye herramientas para optimizar la CPU, la memoria, los gráficos y el uso de la red. Consulte [ejecutar herramientas de diagnóstico sin depurar en MSDN](https://msdn.microsoft.com/library/dn957936.aspx) para obtener todos los detalles.

**Para iniciar el Herramientas de generación de perfiles con HoloLens**
1. Siga las instrucciones anteriores para dirigirse a un dispositivo o emulador
2. Vaya a **Depurar > iniciar herramientas de diagnóstico sin depurar...**
3. Seleccione las herramientas que desea usar
4. Haga clic en **Inicio**
5. La primera vez que lo haga con HoloLens, es posible que obtenga un error de "acceso denegado". Reinicie HoloLens para permitir que los permisos actualizados surtan efecto e inténtelo de nuevo.

## <a name="debugging-an-installed-or-running-app"></a>Depurar una aplicación instalada o en ejecución

Puede usar Visual Studio para depurar una aplicación universal de Windows que se instala sin implementar desde un proyecto de Visual Studio. Esto resulta útil si desea depurar un paquete de aplicaciones instalado o si desea depurar una aplicación que ya se está ejecutando.
1. Vaya a **depurar-> otros destinos de depuración-> depurar paquete de aplicaciones instalado**
2. Seleccione el destino de la **máquina remota** para HoloLens o el **equipo local** para los auriculares más envolventes.
3. Escriba la **dirección IP** del dispositivo
4. Elegir el modo de autenticación **universal**
5. La ventana muestra las aplicaciones en ejecución e inactivas. Elija el que desea depurar.
6. Elegir el tipo de código que se va a depurar (administrado, nativo, mixto)
7. Haga clic en **asociar** o **iniciar**

## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](install-the-tools.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Implementación y depuración de aplicaciones Plataforma universal de Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Habilitar el dispositivo para el desarrollo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
