---
title: Uso de Visual Studio para implementar y depurar
description: Cómo compilar, depurar e implementar aplicaciones para HoloLens y realidad mixta de Windows con Visual Studio.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio, HoloLens, Mixed Reality, depurar, implementar
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601368"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Uso de Visual Studio para implementar y depurar

Si desea utilizar DirectX o Unity para desarrollar su aplicación de realidad mixta, usará Visual Studio para depurar e implementar. En esta sección, obtendrá información sobre:
* Cómo implementar aplicaciones en los auriculares envolventes HoloLens o Windows Mixed Reality a través de Visual Studio.
* Cómo usar el emulador de HoloLens integrado en Visual Studio.
* Cómo depurar aplicaciones de realidad mixta.

## <a name="prerequisites"></a>Requisitos previos
1. Consulte [instalar las herramientas de](install-the-tools.md) para obtener instrucciones de instalación.
2. Cree un nuevo proyecto de aplicación Windows Universal en Visual Studio 2015 Update 1 o Visual Studio 2017. C#, C++, y los proyectos de JavaScript son compatibles. (O siga las instrucciones para [crear una aplicación de una compilación en Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Habilitar el modo de desarrollador

Comience por habilitar **modo de programador** en el dispositivo, por lo que Visual Studio puede conectarse a él.

### <a name="hololens"></a>HoloLens
1. Encienda su HoloLens y colocar en el dispositivo.
2. Realiza el gesto [nástico](gestures.md#bloom) para iniciar el menú principal.
3. Mire el **configuración** icono y llevar a cabo la [pulsar en el aire](gestures.md#air-tap) gesto. Realiza un segundo toque en el aire para colocar la aplicación en tu entorno. La aplicación Configuración se iniciará una vez la hayas colocado.
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilita el **Modo de desarrollador**. Esto le permitirá [implementar aplicaciones desde Visual Studio](using-visual-studio.md) a su HoloLens.
7. Opcional: Desplácese hacia abajo y también permiten **Device Portal**. Esto también le permitirá conectarse a la [Windows Device Portal](using-the-windows-device-portal.md) en su HoloLens desde un explorador web.

### <a name="windows-pc"></a>PC Windows

Si está trabajando con Windows Mixed Reality auriculares con micrófono conectado a su equipo, debe habilitar **modo de programador** en el equipo.
1. Vaya a **configuración**
2. Seleccione **actualización y seguridad**
3. Seleccione **para desarrolladores**
4. Habilitar **modo de programador**, lea la declinación de responsabilidades para la configuración elegida, a continuación, haga clic en Sí para aceptar el cambio.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Implementar una aplicación a través de Wi-Fi - HoloLens (gen 1)
1. Seleccione un **x86** crear configuración de la aplicación ![x86 crear configuración en Visual Studio](images/x86setting.png)
2. Seleccione **máquina remota** en el menú desplegable de destino de implementación ![destino de implementación de la máquina remota en Visual Studio](images/remotemachinesetting.png)
3. Para C++ y proyectos de JavaScript, vaya a **proyecto > Propiedades > Propiedades de configuración > depuración**. Para C# proyecta un testamento de cuadro de diálogo emergente automáticamente para configurar la conexión.
  a. Escriba la dirección IP del dispositivo en el **dirección** o **nombre de la máquina** campo. Buscar la dirección IP en su HoloLens en **configuración > red e Internet > Opciones avanzadas**, o puede solicitar a Cortana "¿Qué es mi dirección IP?"
  b. Establecer el modo de autenticación **Universal (protocolo sin cifrar)**![cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)
4. Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploynodebugging.png)
5. La primera vez que implemente una aplicación en su HoloLens desde su PC, se pedirá un PIN. Siga el **emparejar su dispositivo** las instrucciones siguientes.

Si cambia la dirección IP de HoloLens, puede cambiar la dirección IP del equipo de destino, vaya a **proyecto > Propiedades > Propiedades de configuración > depuración**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Implementar una aplicación a través de USB - HoloLens (gen 1)
1. Seleccione un **x86** crear configuración de la aplicación ![x86 crear configuración en Visual Studio](images/x86setting.png)
2. Seleccione **dispositivo** en el menú desplegable de destino de implementación![implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy.png)
3. Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploynodebugging.png)
4. La primera vez que implemente una aplicación en su HoloLens desde su PC, se pedirá un PIN. Siga el **emparejar su dispositivo** las instrucciones siguientes.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Implementar una aplicación en su PC Local - auriculares envolventes

Siga estas instrucciones cuando se usa un auricular Windows Mixed Reality envolvente que se conecta a su equipo o la [simulador Mixed Reality](using-the-windows-mixed-reality-simulator.md). En estos casos, implementar y ejecutar la aplicación en el equipo local.
1. Seleccione un **x86** o **x64** crear configuración de la aplicación
2. Seleccione **máquina Local** en el menú desplegable de destino de implementación
3. Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración

## <a name="pairing-your-device---hololens-1st-gen"></a>El dispositivo - HoloLens de emparejamiento (gen 1)

La primera vez que implemente una aplicación desde Visual Studio en su HoloLens, solicitará un PIN. En el HoloLens, generar un PIN, inicie la aplicación de configuración, vaya a **actualización > para desarrolladores** y mantener pulsado **par**. Se mostrará un PIN en su HoloLens; Escriba este PIN en Visual Studio. Una vez finalizado la emparejamiento, pulse **realiza** en su HoloLens para descartar el cuadro de diálogo. Este equipo ya está emparejado con el HoloLens y podrá implementar aplicaciones automáticamente. Repita estos pasos para cada PC posteriores que se usa para implementar aplicaciones en su HoloLens.

Para anular par iniciar sus HoloLens de todos los equipos se empareja con, la **configuración** aplicación, vaya a **Update > para desarrolladores** y mantener pulsado **clara**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Implementar una aplicación en el HoloLens (gen 1) emulador
1. Asegúrese de tener  **[instalado el emulador de HoloLens](install-the-tools.md)**.
2. Seleccione un **x86** crear configuración de la aplicación.
![x86 crear configuración en Visual Studio](images/x86setting.png)
3. Seleccione **emulador de HoloLens** en el menú desplegable de destino de implementación![destino del emulador de Visual Studio](images/deployemulator.png)
4. Seleccione **Depurar > Iniciar depuración** para implementar la aplicación e iniciar la depuración![iniciar sin depurar en Visual Studio](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>Depurador de gráficos

Las herramientas de diagnóstico de gráficos de Visual Studio son muy útiles cuando se escribe y optimizar una aplicación holográfica. Consulte [diagnóstico de gráficos de Visual Studio en MSDN](https://msdn.microsoft.com/library/hh315751.aspx) para obtener detalles completos.

**Para iniciar al depurador de gráficos**
1. Siga las instrucciones anteriores para un dispositivo o emulador de destino
2. Vaya a **Depurar > gráficos > Iniciar diagnóstico**
3. La primera vez que se hace esto con un HoloLens, es posible que obtenga un error "acceso denegado". Reinicie su HoloLens para permitir que los permisos actualizados surtan efecto y vuelva a intentarlo.

## <a name="profiling"></a>Generación de perfiles

Las herramientas de generación de perfiles de Visual Studio permiten analizar el uso de recursos y el rendimiento de la aplicación. Esto incluye herramientas para optimizar la CPU, memoria, gráficos y uso de red. Consulte [ejecutar herramientas de diagnóstico sin depuración en MSDN](https://msdn.microsoft.com/library/dn957936.aspx) para obtener detalles completos.

**Para iniciar las herramientas de generación de perfiles con HoloLens**
1. Siga las instrucciones anteriores para un dispositivo o emulador de destino
2. Vaya a **Depurar > Iniciar herramientas de diagnóstico sin depuración...**
3. Seleccione las herramientas que desee usar
4. Haga clic en **iniciar**
5. La primera vez que se hace esto con un HoloLens, es posible que obtenga un error "acceso denegado". Reinicie su HoloLens para permitir que los permisos actualizados surtan efecto y vuelva a intentarlo.

## <a name="debugging-an-installed-or-running-app"></a>Depurar una aplicación instalada o se está ejecutando

Puede usar Visual Studio para depurar una aplicación Universal Windows que se instala sin necesidad de implementar desde un proyecto de Visual Studio. Esto es útil si desea depurar un paquete de aplicación instalada, o si desea depurar una aplicación que ya se está ejecutando.
1. Vaya a **Depurar -> otro depuración destinos -> Depurar paquete de aplicaciones instalado**
2. Seleccione el **máquina remota** destinados a HoloLens o **máquina Local** para inmersivos.
3. Especifique el dispositivo **dirección IP**
4. Elija la **Universal** modo de autenticación
5. La ventana muestra las aplicaciones de ejecución e inactivas. Elija la que desea depurar.
6. Elija el tipo de código para depurar (administrado, nativo y mixto)
7. Haga clic en **adjuntar** o **iniciar**

## <a name="see-also"></a>Vea también
* [Instalar las herramientas](install-the-tools.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Implementar y depurar aplicaciones de la plataforma Universal de Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Habilitar el dispositivo para el desarrollo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
