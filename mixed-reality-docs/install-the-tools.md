---
title: Instalación de las herramientas
description: Empieza aquí a prepararte para el desarrollo de realidad mixta. En este artículo deberían aparecer siempre las versiones más actuales de Unity, Visual Studio y las demás herramientas recomendadas para el desarrollo con HoloLens y con los cascos envolventes de Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 3/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: actualizadas, herramientas, introducción, conceptos básicos, unity, visual studio, toolkit
ms.openlocfilehash: 131d2a91c882fbcd31c4deb76a5ab5c3f97d7d42
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82137880"
---
# <a name="install-the-tools"></a>Instalación de las herramientas

Consigue las herramientas necesarias para compilar aplicaciones para Microsoft HoloLens y los cascos envolventes de Windows Mixed Reality (VR). No hay ningún SDK independiente para el desarrollo con Windows Mixed Reality. Tendrás que usar Visual Studio con el SDK de Windows 10.

¿No tienes un dispositivo de realidad mixta? Puedes instalar el [emulador de HoloLens](using-the-hololens-emulator.md) para probar algunas funciones de las aplicaciones de realidad mixta sin necesidad de un dispositivo HoloLens. También puedes utilizar el [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) para probar las aplicaciones de realidad mixta con unos cascos envolventes.

Se recomienda instalar el motor de juego de Unity como la manera más sencilla de empezar a crear aplicaciones de realidad mixta. Sin embargo, también puedes compilar en DirectX si quieres utilizar un motor personalizado.

>[!TIP]
>Marca esta página como favorita y compruébala con regularidad para estar al día de la versión más reciente de cada herramienta recomendada para el desarrollo de realidad mixta.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Lista de comprobación de la instalación


| Herramienta | Descripción | Notas |
|---------|---------|---------|
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (vínculo de instalación manual)</a> | Instala la versión más reciente de Windows 10 para que el sistema operativo del equipo coincida con la plataforma para la que vas a compilar las aplicaciones de realidad mixta. | **Instalación de Windows 10** <br> <ul><li>Puedes instalar la versión más reciente de Windows 10 mediante Windows Update en Configuración o mediante la creación de soportes de instalación a través del vínculo de la columna izquierda.<li>Consulta las [notas de la versión actual](release-notes-october-2018.md) para más información acerca de las características de realidad mixta más recientes disponibles en cada versión de Windows 10.</ul> **Habilita el modo para desarrolladores en el equipo** en Configuración > Actualización y seguridad > Para programadores. <br><br> **Nota para equipos empresariales o de administración corporativa:** si el equipo lo administra un departamento de TI de la organización, es posible que debas ponerte en contacto con ellos para la actualización. <br><br> **Versiones "N" de Windows:** Los cascos envolventes de Windows Mixed Reality no son compatibles con las versiones "N" de Windows. |
| ![Logotipo de Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.2 o superior)** (vínculo de instalación)</a> | Entorno de desarrollo integrado (IDE) completo para Windows, etc. Vas a utilizar Visual Studio para escribir código, depurar, realizar pruebas e implementar. | Asegúrate de instalar las siguientes cargas de trabajo: <ul><li>**Desarrollo de escritorio con C++**</li><li>**Desarrollo para la Plataforma universal de Windows (UWP)**</li></ul>En la carga de trabajo de UWP, asegúrate de comprobar el siguiente componente opcional si vas a desarrollar para HoloLens:<ul><li>**Conectividad del dispositivo USB**</li></ul>**Nota acerca de Unity:** A menos que intencionadamente estés intentando instalar una versión más reciente (no LTS) de Unity para un propósito específico, se recomienda *no* instalar la carga de trabajo de Unity como parte de la instalación de Visual Studio y, en su lugar, instalar la secuencia **Unity 2018.4 LTS** como se indica a continuación.<br> <br>**Nota:** Hay algunos problemas conocidos con la depuración de aplicaciones de realidad mixta en Visual Studio 2019, versión 16.0.  Asegúrate de actualizar a **Visual Studio 2019, versión 16.2 o superior**. |
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK de Windows 10 (10.0.18362.0)** (vínculo de instalación manual)</a> | Proporciona los encabezados, bibliotecas, metadatos y herramientas más recientes para compilar aplicaciones de Windows 10 en HoloLens 2. | Para compilar aplicaciones de HoloLens 2, debes instalar el SDK de Windows, compilación 18362 o posterior.<br> <br> Si solo vas a desarrollar aplicaciones para cascos de Windows Mixed Reality o HoloLens (1.ª generación), puedes usar el SDK de Windows que instala Visual Studio 2017. |
| ![Logotipo de Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2126826" target="_blank">**Emulador de HoloLens 2 (actualización de abril de 2020)** (vínculo de instalación: 10.0.18362.1059)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador de HoloLens (Gen 1)** (vínculo de instalación: 10.0.17763.134)</a> | El emulador te permite ejecutar aplicaciones en una imagen de máquina virtual de HoloLens sin necesidad de un dispositivo HoloLens físico.<br> <br> | Consulta [Uso del emulador de HoloLens](using-the-hololens-emulator.md) para más información sobre cómo empezar a trabajar con el emulador.<br> <br> **El sistema debe admitir Hyper-V** para que la instalación del emulador se realice correctamente. Consulta la sección Requisitos del sistema que aparece a continuación para obtener los detalles. <br>|

## <a name="choose-your-engine"></a>Elige el motor

:::row:::
    :::column:::
        <a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">![Unity](images/unity_logo.png)<br>**Unity**</a><br>
        Normalmente, se recomienda la versión Unity LTS (soporte técnico a largo plazo) como la mejor versión con la que empezar nuevos proyectos, actualizándola a la revisión más reciente para aprovechar las actualizaciones más estables.<br>
        <br>
        La recomendación actual es usar **Unity 2018.4.x**, que es la compilación LTS necesaria para MRTK, versión 2 o inferior.<br>
        <br>
        Puede que a algunos desarrolladores les guste usar una versión diferente de Unity por motivos concretos. En esos casos, Unity admite instalaciones paralelas de distintas versiones.<br>
        <br>
        Consulta [Introducción al desarrollo de Unity](unity-development-overview.md) para empezar a desarrollar con Unity para los cascos envolventes HoloLens 2 o Windows Mixed Reality.<br>
        <br>
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">![MRTK](images/final_mrtk-small_logo.png)<br>**Mixed Reality Toolkit (MRTK)** </a><br>
        Mixed Reality Toolkit (MRTK) v2 para Unity es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.<br>
        <br>
        MRTK v2 está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.
    :::column-end:::
    :::column:::
        <a href="https://docs.unrealengine.com//GettingStarted/Installation/index.html" target="_blank">![Unreal](images/Unreal_logo.png)<br>**Unreal**</a><br>
        Unreal Engine 4 es un potente motor de creación de código abierto con compatibilidad total con la realidad mixta en C++ y Blueprints.<br>
        <br>
        La compatibilidad de HoloLens con Unreal Engine 4.24 se encuentra actualmente en versión beta.<br>
        <br>
        Consulta [Introducción al desarrollo con Unreal](unreal-development-overview.md) para empezar a desarrollar con Unreal para HoloLens 2.
    :::column-end:::
    :::column:::
        ![Desarrollo de aplicaciones nativas](images/visualstudio-small_logo.png)<br>
        [**Nativo (OpenXR)** ](openxr-getting-started.md)<br>
        OpenXR es un estándar de API abierto libre de regalías de Khronos que proporciona a los motores acceso nativo a una amplia gama de dispositivos de muchos proveedores que abarcan todo el espectro de la realidad mixta.  En el proyecto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> se muestra un ejemplo de OpenXR simple con dos archivos de proyecto de Visual Studio, uno para una aplicación de escritorio de Win32 y otro para una aplicación para UWP de HoloLens 2.<br>
        <br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">**Nativo (WinRT)** </a><br>
        Las <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">plantillas de aplicaciones nativas de Windows Mixed Reality</a> proporcionan todos los aspectos esenciales que necesitas para empezar a escribir una aplicación de realidad mixta mediante DirectX con las API nativas. Incluye un bucle de representación (o "bucle de juego"), una clase auxiliar DeviceResources para administrar el dispositivo y el contexto de Direct3D, y un representador de hologramas de ejemplo sencillo. Disponible para Direct3D 11 y Direct3D 12.<br>
        <br>
        Consulta [Introducción al desarrollo nativo](directx-development-overview.md) para empezar a desarrollar aplicaciones nativas con WinRT u OpenXR para los cascos envolventes HoloLens 2 o Windows Mixed Reality.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>Mixed Reality Toolkit (MRTK)

Mixed Reality Toolkit proporciona componentes y características que están pensadas para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit</a>: una colección de scripts y componentes diseñados para acelerar el desarrollo de aplicaciones de realidad mixta.
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit-Unity</a>: usa código del kit de herramientas básico y facilita su uso en Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit</a>: bits y componentes de código que no se pueden ejecutar directamente en HoloLens o en cascos envolventes (VR), sino que se emparejan para generar experiencias destinadas a Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Configuración del equipo para el desarrollo de realidad mixta

El SDK de Windows 10 funciona mejor en el sistema operativo Windows 10. Este SDK también es compatible con: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 y Windows Server 2008 R2. Ten en cuenta que no todas las herramientas son compatibles con sistemas operativos anteriores. 

### <a name="for-hololens-development"></a>Para el desarrollo de HoloLens

Cuando configures el equipo para el desarrollo de HoloLens, asegúrate de que cumple con los requisitos del sistema de <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> y de <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si tienes previsto usar el emulador de HoloLens, deberás asegurarte de que el equipo también cumple con los [requisitos del sistema del emulador de HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Para empezar a trabajar con el emulador de HoloLens, consulta [Uso del emulador de HoloLens](using-the-hololens-emulator.md).

Si tienes previsto desarrollar aplicaciones para HoloLens y para los cascos envolventes (VR) de Windows Mixed Reality, usa los requisitos y las recomendaciones del sistema que aparecen en la siguiente sección.

### <a name="for-immersive-vr-headset-development"></a>Para el desarrollo para cascos envolventes

>[!NOTE]
>Las instrucciones siguientes son las especificaciones actuales mínimas y recomendadas para el *equipo de desarrollo* para cascos envolventes (VR) y puede que se actualicen con regularidad.

>[!WARNING]
>No confundas esto con las [instrucciones de compatibilidad con el hardware del equipo](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que describe las *especificaciones del equipo del usuario* de las que debes disponer para desarrollar aplicaciones o juegos con destino a cascos envolventes.

Si el equipo de desarrollo para cascos envolventes no dispone de una HDMI completa o de puertos USB 3.0, necesitarás [adaptadores](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar los cascos.

Existen en la actualidad [problemas conocidos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con algunas configuraciones de hardware, especialmente en portátiles que tienen gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Procesador</td><td> <b>Portátil:</b> Intel Mobile Core i5 de con CPU de séptima generación, de doble núcleo con Hyper Threading <b>Dispositivo de escritorio:</b> Intel Desktop i5 con CPU de sexta generación, de doble núcleo con Hyper Threading <b>O</b> AMD FX4350 4.2Ghz Quad-Core equivalente</td><td> <b>Dispositivo de escritorio:</b> Intel Desktop i7 de sexta generación (6 núcleos) <b>O</b> AMD Ryzen 5 1600 (6 núcleos, 12 subprocesos)</td>
</tr><tr>
<td> GPU</td><td> <b>Portátil:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) con GPU compatible con DX12 equivalente o superior <b>Dispositivo de escritorio:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) con GPU compatible con DX12 equivalente o superior</td><td><b>Dispositivo de escritorio:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) con GPU compatible con DX12 equivalente o superior</td>
</tr><tr>
<td> Versión de WDDM del controlador de GPU</td><td colspan="2"> Controlador WDDM 2.2</td>
</tr><tr>
<td> Potencia de diseño térmico</td><td colspan="2"> 15 W o más</td>
</tr><tr>
<td> Puertos de pantalla gráfica</td><td colspan="2"> 1 puerto de pantalla gráfica disponible para casco de realidad mixta (HDMI 1.4 o DisplayPort 1.2 para cascos de 60 Hz, HDMI 2.0 o DisplayPort 1.2 para cascos de 90 Hz)</td>
</tr><tr>
<td> Resolución de pantalla</td><td colspan="2"> Solución: SVGA (800 x 600) o con mayor profundidad de bits: 32 bits de color por píxel</td>
</tr><tr>
<td> Memory</td><td> 8 GB de RAM o más</td><td> 16 GB de RAM o más</td>
</tr><tr>
<td> Almacenamiento</td><td colspan="2"> &gt;Espacio libre adicional de 10 GB</td>
</tr><tr>
<td> Puertos USB</td><td colspan="2"> 1 puerto USB disponible para casco de realidad mixta (USB 3.0 Type-A) <b>Nota: el USB debe proporcionar un mínimo de 900 mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para la conectividad de los accesorios)</td>
</tr>
</table>

## <a name="see-also"></a>Consulta también

* [Introducción al desarrollo](development.md)
* [Uso del emulador de HoloLens](using-the-hololens-emulator.md)
* [Uso del simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Introducción al desarrollo de Unreal](unreal-development-overview.md)
* [Introducción al desarrollo de DirectX](directx-development-overview.md)
* [Archivo del emulador de HoloLens](hololens-emulator-archive.md)
