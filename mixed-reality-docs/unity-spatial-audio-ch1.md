---
title: 'Tutoriales de audio espacial: 1. Agregar audio espacial al proyecto'
description: Agregue el complemento de Microsoft Spatializer a su proyecto de Unity para acceder a la descarga de hardware de HoloLens 2 HRTF.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182802"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Incorporación de audio espacial al proyecto de Unity

Este es el tutioral de audio espacial para Unity en HoloLens2. Esta secuencia de tutorial muestra:
* Cómo usar la descarga de HRTF en HoloLens 2 en Unity
* Cómo habilitar la reverberación al usar la descarga de HRTF

El [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tiene un proyecto de Unity completado de esta secuencia de tutoriales. 

Para ver las recomendaciones sobre cuándo puede ser útil espaciales, consulte diseño de [sonido espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="objectives"></a>Objetivos
En este primer capítulo, hará lo siguiente:
* Creación de un proyecto de Unity e importación de MRTK
* Importar el complemento de Microsoft spatializer
* Habilitación del complemento Microsoft spatializer
* Habilitación del audio espacial en la estación de trabajo de desarrollador

## <a name="create-a-project-and-add-nuget-for-unity"></a>Creación de un proyecto y adición de NuGet para Unity
Comience con un proyecto de Unity vacío y, después, agregue y configure NuGet para Unity:
1. Descargue la versión más reciente de [NuGetForUnity. unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. En la barra de menús de Unity, haga clic en **activos > importar paquete > paquete personalizado...** e instalar el paquete NuGetForUnity:

![Importar paquete personalizado](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Agregar el paquete de Windows Mixed Reality
La compatibilidad con Windows Mixed Reality en Unity 2019 y versiones posteriores se incluye en un paquete opcional. Para agregarlo al proyecto, abra el **Administrador de paquetes de > de ventana** desde la barra de menús de Unity:

![Menú del administrador de paquetes](images/spatial-audio/package-manager-menu.png)

A continuación, busque e instale el paquete de **Windows Mixed Reality** :

![Ventana del administrador de paquetes](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>Instalación de MRTK y Microsoft Spatializer
Con NuGet para Unity, instale los complementos de MRTK y Microsoft Spatializer:
1. En la barra de menús de Unity, haga clic en **Nuget-> administrar paquetes NuGet**.

![Administrar paquetes NuGet](images/spatial-audio/manage-nuget-packages.png)

2. En el cuadro de **búsqueda** , escriba "Microsoft. MixedReality. Toolkit" e instale el paquete de MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation** .

![Paquete NuGet de MRTK](images/spatial-audio/mrtk-nuget-package.png)

El [paquete NuGet de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) tiene contexto y detalles adicionales.

4. En el cuadro de **búsqueda** , escriba "Microsoft. SpatialAudio" e instale el paquete de Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity** .

![Complemento NuGet de Spatializer](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>Configuración de MRTK en el proyecto

1. Para abrir la ventana Configuración de compilación, vaya a **archivo-> configuración de compilación**.

2. Seleccione la _plataforma universal de Windows_ y haga clic en **cambiar plataforma**.

3. Haga clic en **configuración del reproductor** en la **ventana compilar** para abrir las propiedades de **configuración del reproductor** en el panel **Inspector** .
    * En **configuración de XR**, active la casilla **compatible con realidad virtual**
    * En **configuración de XR**, cambie el **modo de representación de estéreo** a instancia de **paso único**.
    * En **configuración de publicación**, active la casilla **percepción espacial** en la sección **capacidades** .

4. En la barra de menús, haga clic en **Kit de herramientas de realidad mixta: > agregar a la escena y configurar.** para agregar MRTK a la escena.

Para obtener instrucciones adicionales, incluida la forma de compilar la aplicación e implementarla en HoloLens 2, consulte [el capítulo 1 del módulo de base de aprendizaje Mr](mrlearning-base-ch1.md).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Habilitación del complemento Microsoft Spatializer
Habilite el complemento de **Microsoft Spatializer** . Abra **editar > configuración del proyecto-> audio**y cambie el **complemento Spatializer** a "Microsoft Spatializer". La sección **audio** de la **configuración del proyecto** tendrá ahora el siguiente aspecto:

![Configuración del proyecto que muestra el complemento spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Habilitación del audio espacial en la estación de trabajo
En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada. Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas. Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **sonido espacial > Windows Sonic para auriculares**.

![Configuración de audio espacial de escritorio](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> Esta configuración solo es necesaria si tiene previsto probar el proyecto en el editor de Unity.

## <a name="next-steps"></a>Pasos siguientes
Continúe con el [capítulo 2 del audio espacial de Unity](unity-spatial-audio-ch2.md) para enspatial los sonidos de interacción del botón.

