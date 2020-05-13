---
title: Introducción a OpenXR
description: Comience a usar el estándar portable OpenXR API en Windows Mixed Reality y los auriculares de HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality OpenXR Herramientas de desarrollo, DirectX, nativo, aplicación nativa, motor personalizado, middleware, introducción, 101, extensiones de vista previa, versión de tiempo de ejecución de OpenXR, estado del sistema
ms.openlocfilehash: b4cf91c7a7b5bd203a4fef43c7a988d3ff1e9b16
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228068"
---
# <a name="getting-started-with-openxr"></a>Introducción a OpenXR

Puede desarrollar con OpenXR en un casco con HoloLens 2 o Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introducción a OpenXR para HoloLens 2

Para empezar a desarrollar aplicaciones de OpenXR para HoloLens 2:

1. Configure un HoloLens 2 o siga las instrucciones para [instalar una versión reciente del emulador de hololens 2](using-the-hololens-emulator.md).  Si el dispositivo ha actualizado recientemente su sistema operativo o si usa una imagen de emulador reciente, ya debe tener OpenXR 1,0 listo para usar.
1. Para asegurarse de que tiene el tiempo de ejecución de OpenXR más reciente con todas [las extensiones](openxr.md#roadmap) presentes, inicie la aplicación de la **tienda** desde el dispositivo o el emulador, abra el menú de la parte superior derecha, haga clic en **descargas y actualizaciones** y haga clic en **obtener actualizaciones**.  Esto garantiza que el tiempo de ejecución de OpenXR en HoloLens esté actualizado.  Tenga en cuenta que si usa el emulador, la imagen del emulador se restablecerá cada vez que la inicie y, por lo tanto, la mejor opción es asegurarse de que tiene [la versión más reciente de la imagen del emulador de HoloLens 2](using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introducción a OpenXR para auriculares con Windows Mixed Reality

Para empezar a desarrollar aplicaciones de OpenXR para auriculares con Windows de realidad mixta:

1. Asegúrese de que está ejecutando al menos la actualización 2019 de Windows 10 (1903), que es el requisito mínimo para que los usuarios finales de Windows Mixed Reality ejecuten aplicaciones OpenXR.  Si se encuentra en una versión anterior de Windows 10, puede actualizar mediante el Asistente de <a href="https://www.microsoft.com/software-download/windows10" target="_blank">actualización de Windows 10</a>.
2. Configure un casco de realidad mixta de Windows o siga las instrucciones para [Habilitar el simulador de realidad mixta de Windows](using-the-windows-mixed-reality-simulator.md).  Al configurar Windows Mixed Reality, el portal de realidad mixta instalará automáticamente el tiempo de ejecución de Windows Mixed Reality OpenXR.  El Microsoft Store mantendrá el tiempo de ejecución actualizado.
3. Active el tiempo de ejecución de Windows Mixed Reality OpenXR ejecutando el portal de realidad mixta en el menú Inicio y haga clic en... en la parte inferior izquierda y seleccione "configurar OpenXR".<br>
![Configuración de OpenXR en el portal de realidad mixta](images/mixed-reality-portal-set-up-openxr.png)

Si alguna vez necesita volver a activar el tiempo de ejecución de OpenXR de Windows Mixed Reality, repita el paso 3.

> [!NOTE]
> El tiempo de ejecución de OpenXR de Windows Mixed Reality pronto se activará automáticamente para todos los usuarios finales de Windows Mixed Reality.

## <a name="getting-the-windows-mixed-reality-openxr-developer-tools"></a>Obtener OpenXR de Windows Mixed Reality Herramientas de desarrollo

Para probar el tiempo de ejecución de Windows Mixed Reality OpenXR, puede instalar la <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicación Mixed Reality OpenXR herramientas de desarrollo</a>.  Esta aplicación proporciona una escena de demostración que ejercita varias características de OpenXR, junto con una página de estado del sistema que proporciona información clave sobre el tiempo de ejecución activo y el casco actual.

Si usa el emulador, la manera más fácil de instalar el Herramientas de desarrollo Mixed Reality OpenXR es usar el [portal de dispositivos de Windows](using-the-windows-device-portal.md). para ello, vaya a la página "OpenXR" y, a continuación, haga clic en el botón "instalar" en "características para desarrolladores". (esto también funciona en un dispositivo de HoloLens 2 físico)

![Aplicación OpenXR de realidad mixta Herramientas de desarrollo](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Compilación de una aplicación de OpenXR de ejemplo

Asegúrese de [instalar las herramientas](install-the-tools.md) que necesita para el desarrollo de OpenXR si todavía no lo ha hecho.

El proyecto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> muestra un sencillo ejemplo de OpenXR con dos archivos de proyecto de Visual Studio, uno para una aplicación de escritorio de Win32 y otro para una aplicación de UWP de HoloLens 2.  Dado que la solución contiene un proyecto de UWP de HoloLens, necesitará la [carga de trabajo de desarrollo de plataforma universal de Windows](install-the-tools.md#installation-checklist) instalada en Visual Studio para abrirla por completo.

Tenga en cuenta que aunque los archivos de proyecto de UWP y Win32 son independientes debido a las diferencias de empaquetado e implementación, el código de la aplicación dentro de cada proyecto es 100% del mismo.

Después de crear un escritorio de Win32 de OpenXR. EXE, puede usarlo con un casco de VR en cualquier plataforma de escritorio VR que admita OpenXR, ya sea un casco de realidad mixta de Windows o cualquier otro casco.

Después de compilar un paquete de aplicación de UWP para OpenXR, puede [implementarlo](using-visual-studio.md) en un dispositivo hololens 2 o en el emulador de hololens 2.

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrar el cargador de OpenXR en un proyecto

Para empezar a trabajar con OpenXR en un proyecto existente, incluirá el cargador de OpenXR.  El cargador detecta el tiempo de ejecución de OpenXR activo en el dispositivo y proporciona acceso a las funciones básicas y a las funciones de extensión que implementa.

Puede [hacer referencia al paquete de NuGet OpenXR oficial](#reference-official-openxr-nuget-package) desde el proyecto de Visual Studio o [incluir el origen oficial del cargador de OpenXR](#include-official-openxr-loader-source) desde el repositorio de github de Khronos.  Cualquier enfoque le proporcionará acceso a las características principales de OpenXR 1,0, además de las publicadas `KHR` `EXT` y `MSFT` las extensiones.

Si le interesa experimentar `MSFT_preview` también con las extensiones, puede [Copiar en la vista previa](#using-preview-extensions) de los encabezados de OpenXR desde el repositorio de github de realidad mixta.

### <a name="reference-official-openxr-nuget-package"></a>Referencia a un paquete de NuGet de OpenXR oficial

El <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">paquete NuGet **OpenXR. Loader** </a> es la forma más fácil de hacer referencia a un cargador de OpenXR creado previamente. DLL en la solución de Visual Studio C++.  Esto le proporcionará acceso a las características principales de OpenXR 1,0, además de las publicadas `KHR` `EXT` y `MSFT` las extensiones.

Para agregar una referencia de paquete NuGet OpenXR. Loader a su solución de Visual Studio C++:
1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto que usará OpenXR y seleccione **administrar paquetes NuGet..**..
1. Cambie a la pestaña **examinar** y busque **OpenXR. Loader**.
1. Seleccione el paquete **OpenXR. Loader** y haga clic en instalar en el panel de detalles de la derecha.
1. Haga clic en Aceptar para aceptar los cambios en el proyecto.
1. Agregue `#include <openxr/openxr.h>` a un archivo de código fuente para empezar a usar la API de OpenXR.

Para ver un ejemplo de la API de OpenXR en acción, consulte la aplicación de ejemplo <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Incluir origen oficial de cargador de OpenXR

Si desea compilar el cargador por su cuenta, por ejemplo, para evitar el cargador adicional. DLL, puede extraer los orígenes oficiales del cargador de Khronos OpenXR en el proyecto.  Esto le proporcionará acceso a las características principales de OpenXR 1,0, además de las publicadas `KHR` `EXT` y `MSFT` las extensiones.

Para empezar aquí, siga las instrucciones del <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repositorio Khronos OpenXR-SDK en github</a>.  El proyecto está configurado para compilar con CMake. Si usa MSBuild, deberá copiar el código en su propio proyecto.

## <a name="using-preview-extensions"></a>Uso de extensiones de vista previa

Las `MSFT_preview` extensiones enumeradas en el [mapa de ruta](openxr.md#roadmap) de la extensión son extensiones de proveedor experimentales en las que se obtiene una vista previa para recopilar comentarios.  Estas extensiones son solo para dispositivos de desarrollador y se quitarán cuando se distribuya la extensión real.

Si está interesado en probar las `MSFT_preview` extensiones disponibles, siga los pasos que se indican a continuación para actualizar el proyecto:
1. Siga uno de los métodos anteriores para integrar un cargador de OpenXR en el proyecto.
1. Reemplace los encabezados OpenXR estándar del proyecto por los <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">encabezados de vista previa del repositorio Mixed Reality OpenXR en github</a>.

Para activar la compatibilidad con la extensión de vista previa en el equipo de escritorio o HoloLens 2 de destino:
  1. Para asegurarse de que tiene el tiempo de ejecución de OpenXR más reciente con todas [las extensiones](openxr.md#roadmap) presentes, inicie la aplicación de la **tienda** desde el emulador o el dispositivo de destino, abra el menú de la parte superior derecha, haga clic en **descargas y actualizaciones** y, a continuación, haga clic en **obtener actualizaciones**.
  1. Habilite Windows Device portal en el dispositivo de destino:
     * Si el dispositivo de destino es un dispositivo HoloLens 2, [siga estas instrucciones](using-the-windows-device-portal.md) en el dispositivo de destino.  Tenga en cuenta que esto requiere un casco físico, ya que un problema conocido en el emulador de HoloLens 2 impedirá que la interfaz de usuario del paso siguiente aparezca en el emulador.
     * Si el dispositivo de destino es un equipo de escritorio con un periférico con auriculares envolvente conectado, <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">siga estas instrucciones</a> en el equipo de escritorio de destino.
  1. Vaya a la pestaña **OpenXR** en el panel izquierdo y habilite **usar la última versión preliminar de OpenXR Runtime**.  Esto habilita el tiempo de ejecución de vista previa en el dispositivo, que tiene activadas las extensiones de versión preliminar.
  1. Confirme que la **versión en tiempo de ejecución** que se muestra en la pestaña **Estado del sistema** de [Windows Mixed Reality OpenXR herramientas de desarrollo](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) ahora coincide con la versión necesaria de las extensiones de vista previa que planea probar.  En ese caso, debería ver la extensión en la lista de **extensiones** .  Tenga en cuenta que una vez que haya disponible una extensión estable, se quitará su extensión de vista previa.<br />
     ![Pestaña Estado del sistema de OpenXR de realidad mixta Herramientas de desarrollo](images/mixed-reality-openxr-developer-tools-status.png)

Consulte el <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repositorio de OpenXR de realidad mixta</a> para obtener documentación de estas extensiones de vista previa y ejemplos de cómo usarlas.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas para empezar a trabajar con el desarrollo de OpenXR, consulte nuestras [sugerencias sobre solución de problemas](openxr-troubleshooting.md).