---
title: Uso de Visual Studio para implementaciones y depuraciones
description: Obtén información sobre cómo crear, depurar e implementar aplicaciones para HoloLens y Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realidad mixta, depurar, implementar
ms.openlocfilehash: 718635922196b9c044c6904ebab994e9e2a2ff1a
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278003"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Uso de Visual Studio para implementaciones y depuraciones

Tanto si quieres usar DirectX como Unity para desarrollar tu aplicación de realidad mixta, usarás Visual Studio para la depuración y la implementación. En esta sección, aprenderás a:
* Implementar aplicaciones en tu casco envolvente de HoloLens o Windows Mixed Reality a través de Visual Studio.
* Usar el emulador de HoloLens integrado en Visual Studio.
* Depurar aplicaciones de realidad mixta.

## <a name="prerequisites"></a>Requisitos previos
1. Consulta [Instalar las herramientas](install-the-tools.md) para obtener instrucciones de instalación.
2. Crea un proyecto de aplicación universal de Windows en Visual Studio.  Para HoloLens (1.ª generación), usa Visual Studio 2017 o una versión más reciente.  Para Hololens 2, usa Visual Studio 2019 16.2 o una versión más reciente. Se admiten los lenguajes C# y C++. (También puedes seguir las instrucciones para [crear una aplicación en Unity](holograms-100.md)).

## <a name="enabling-developer-mode"></a>Habilitar el modo de desarrollador

Para empezar, habilita el **Modo de desarrollador** en tu dispositivo, para que Visual Studio pueda conectarse a él.

### <a name="hololens"></a>HoloLens
1. Enciende tu HoloLens y colócate el dispositivo.
2. Realiza el gesto [nástico](system-gesture.md#bloom) para iniciar el menú principal.
3. Mira el icono **Configuración** y realiza el gesto de [pulsación en el aire](gaze-and-commit.md#composite-gestures). Realiza un segundo toque en el aire para colocar la aplicación en tu entorno. La aplicación Configuración se iniciará una vez la hayas colocado.
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilita el **Modo de desarrollador**. Esto te permitirá [implementar aplicaciones desde Visual Studio](using-visual-studio.md) a tu HoloLens.
7. Opcional: Desplázate hacia abajo y habilita el **Portal de dispositivos**. Esto también te permitirá conectarte al [Portal de dispositivos Windows](using-the-windows-device-portal.md) en tu HoloLens desde un explorador web.

### <a name="windows-pc"></a>Equipo Windows

Si trabajas con un casco de Windows Mixed Reality conectado a tu PC, debes habilitar el **Modo de desarrollador** en el equipo.
1. Ve a **Configuración**.
2. Selecciona **Actualización y seguridad**.
3. Selecciona **Para desarrolladores**.
4. Habilita el **Modo de desarrollador**, lee el aviso de declinación de responsabilidades para la configuración elegida y, luego, haz clic en Sí para aceptar el cambio.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Implementación de una aplicación a través de Wi-Fi: HoloLens (1.ª generación)
1. Selecciona una configuración de compilación **x86** para tu aplicación.</br>
![Configuración de compilación x86 en Visual Studio](images/x86setting.png)</br>
2. Selecciona **Máquina remota** en el menú desplegable de destino de la implementación.</br>
![Destino de implementación de la máquina remota en Visual Studio](images/remotemachinesetting.png)</br>
3. Para proyectos de C++ y JavaScript, ve a **Proyecto > Propiedades > Propiedades de configuración > Depuración**. Para proyectos de C#, aparecerá automáticamente un cuadro de diálogo para configurar tu conexión.
  a. Escribe la dirección IP del dispositivo en el campo **Dirección** o **Nombre de la máquina**. Busca la dirección IP de tu HoloLens en **Configuración > Red e Internet > Opciones avanzadas**, o puedes pedirle a Cortana "¿Cuál es mi dirección IP?"
  b. Establece el modo de autenticación en **Universal (protocolo sin cifrar)** .</br>
  ![Cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)</br>
4. Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</br>
![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>
5. La primera vez que implementes una aplicación en tu HoloLens desde tu equipo, se te pedirá un PIN. Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Implementación de una aplicación a través de Wi-Fi: HoloLens 2
1. Selecciona una configuración de compilación **ARM** o **ARM64** para tu aplicación.</br>
![Configuración de compilación ARM64 en Visual Studio](images/arm64setting.png)</br>
2. Selecciona **Máquina remota** en el menú desplegable de destino de la implementación.</br>
![Destino de implementación de la máquina remota en Visual Studio](images/remotemachinesetting_arm64.png)</br>
3. Para proyectos de C++ y JavaScript, ve a **Proyecto > Propiedades > Propiedades de configuración > Depuración**. Para proyectos de C#, aparecerá automáticamente un cuadro de diálogo para configurar tu conexión.
  a. Escribe la dirección IP del dispositivo en el campo **Dirección** o **Nombre de la máquina**. Busca la dirección IP de tu HoloLens en **Configuración > Red e Internet > Opciones avanzadas**, o puedes pedirle a Cortana "¿Cuál es mi dirección IP?"
  b. Establece el modo de autenticación en **Universal (protocolo sin cifrar)** .</br>
  ![Cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)</br>
4. Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</br>
![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>
5. La primera vez que implementes una aplicación en tu HoloLens desde tu equipo, se te pedirá un PIN. Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.

Si cambia la dirección IP de tu HoloLens, puedes cambiar la dirección IP de la máquina de destino. Para ello, ve a **Proyecto > Propiedades > Propiedades de configuración > Depuración**.

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Implementar una aplicación a través de USB: HoloLens (1.ª generación)
1. Selecciona una configuración de compilación **x86** para tu aplicación.</br>
![Configuración de compilación x86 en Visual Studio](images/x86setting.png)</br>
2. Selecciona **Dispositivo** en el menú desplegable de destino de la implementación.</br>
![Implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy.png)</br>
3. Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</br>
![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>
4. La primera vez que implementes una aplicación en tu HoloLens desde tu equipo, se te pedirá un PIN. Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.

## <a name="deploying-an-app-over-usb---hololens-2"></a>Implementación de una aplicación a través de USB: HoloLens 2
1. Selecciona una configuración de compilación **ARM** o **ARM64** para tu aplicación.</br>
![Configuración de compilación ARM64 en Visual Studio](images/arm64setting.png)</br>
2. Selecciona **Dispositivo** en el menú desplegable de destino de la implementación.</br>
![Implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy_arm64.png)</br>
3. Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</br>
![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>
4. La primera vez que implementes una aplicación en tu HoloLens desde tu equipo, se te pedirá un PIN. Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Implementación de una aplicación en tu equipo local: casco envolvente

Sigue estas instrucciones a la hora de usar un casco envolvente de Windows Mixed Reality que se conecte a tu equipo o al [simulador de realidad mixta](using-the-windows-mixed-reality-simulator.md). En estos casos, simplemente implementa y ejecuta la aplicación en el equipo local.
1. Selecciona una configuración de compilación **x86** o **x64** para tu aplicación.
2. Selecciona **Máquina local** en el menú desplegable de destino de la implementación.
3. Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.

## <a name="pairing-your-device"></a>Emparejamiento del dispositivo

La primera vez que implementes una aplicación desde Visual Studio en tu HoloLens, se te pedirá un PIN. En HoloLens, para generar un PIN, inicia la aplicación Configuración, ve a **Actualizar > Para desarrolladores** y pulsa **Emparejar**. Se mostrará un PIN en tu HoloLens. Escríbelo en Visual Studio. Una vez completado el emparejamiento, pulsa **Listo** en HoloLens para descartar el cuadro de diálogo. En este momento, este equipo estará emparejado con HoloLens y podrás implementar aplicaciones automáticamente. Repite estos pasos para todos los equipos sucesivos que se usen para implementar aplicaciones en tu HoloLens.

Para desemparejar tu HoloLens de todos los ordenadores con los que se emparejó, inicia la aplicación **Configuración**, ve a  **Actualizar > Para desarrolladores** y pulsa **Borrar**.

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Implementación de una aplicación en el emulador de HoloLens (1.ª generación)
1. Asegúrate de que tienes **[instalado el emulador de HoloLens](install-the-tools.md)** .
2. Selecciona una configuración de compilación **x86** para tu aplicación.</br>
![Configuración de compilación x86 en Visual Studio](images/x86setting.png)</br>
3. Selecciona **Emulador de HoloLens** en el menú desplegable de destino de la implementación.</br>
![Destino del emulador en Visual Studio](images/deployemulator.png)</br>
4. Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</br>
![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Implementación de una aplicación en el emulador de HoloLens 2
1. Asegúrate de que tienes **[instalado el emulador de HoloLens](install-the-tools.md)** .
2. Selecciona una configuración de compilación **x86** o **x64** para tu aplicación.</br>
![Configuración de compilación x86 en Visual Studio](images/x86setting.png)</br>
3. Selecciona **Emulador de HoloLens 2** en el menú desplegable de destino de la implementación.</br>
![Destino del emulador en Visual Studio](images/deployemulator2.png)</br>
4. Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.</br>
![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Depurador de gráficos para HoloLens (1.ª generación)

Las herramientas de Diagnóstico de gráficos de Visual Studio son muy útiles a la hora de escribir y optimizar una aplicación holográfica. Consulta [Diagnóstico de gráficos de Visual Studio en MSDN](https://msdn.microsoft.com/library/hh315751.aspx) para obtener todos los detalles.

**Para iniciar el depurador de gráficos**
1. Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.
2. Ve a **Depurar > Gráficos > Iniciar diagnóstico**.
3. Es posible que la primera vez que hagas esto con HoloLens obtengas un error de "acceso denegado". Reinicia tu HoloLens para permitir que los permisos actualizados tengan efecto y vuelve a intentarlo.

## <a name="profiling"></a>Generación de perfiles

Las herramientas de generación de perfiles de Visual Studio te permiten analizar el rendimiento y el uso de recursos de tu aplicación. Esto incluye herramientas para optimizar el uso de la CPU, la memoria, los gráficos y la red. Consulta [Ejecutar las herramientas de diagnóstico sin depuración en MSDN](https://msdn.microsoft.com/library/dn957936.aspx) para obtener todos los detalles.

**Para iniciar las herramientas de generación de perfiles con HoloLens**
1. Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.
2. Ve a **Depurar > Iniciar herramientas de diagnóstico sin depuración...** .
3. Selecciona las herramientas que quieres utilizar.
4. Haz clic en **Iniciar**.
5. Es posible que la primera vez que hagas esto con HoloLens obtengas un error de "acceso denegado". Reinicia tu HoloLens para permitir que se apliquen los permisos actualizados y vuelve a intentarlo.

## <a name="debugging-an-installed-or-running-app"></a>Depuración de una aplicación instalada o en ejecución

Puedes usar Visual Studio para depurar una aplicación universal de Windows instalada sin implementarla desde un proyecto de Visual Studio. Esto resulta útil si quieres depurar un paquete de la aplicación instalado o si quieres depurar una aplicación que ya se está ejecutando.
1. Ve a **Depurar > Otros destinos de depuración > Depurar paquete de aplicaciones instalado**.
2. Selecciona el destino **Máquina remota** para HoloLens o **Máquina local** para los cascos envolventes.
3. Escribe la **dirección IP** de tu dispositivo.
4. Selecciona el modo de autenticación **Universal**.
5. En la ventana se muestran las aplicaciones en ejecución e inactivas. Elige la que quieras depurar.
6. Elige el tipo de código que quieras depurar (administrado, nativo, mixto).
7. Haz clic en **Adjuntar** o **Iniciar**.

## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](install-the-tools.md)
* [Uso del emulador de HoloLens](using-the-hololens-emulator.md)
* [Implementación y depuración de aplicaciones para la Plataforma universal de Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Habilitar el dispositivo para el desarrollo](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
