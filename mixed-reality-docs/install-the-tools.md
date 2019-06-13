---
title: Instalación de las herramientas
description: Empieza aquí a prepararte para el desarrollo de realidad mixta. En este artículo deberían aparecer siempre las versiones más actuales de Unity, Visual Studio y las demás herramientas recomendadas para el desarrollo con HoloLens y con los cascos envolventes de Windows Mixed Reality.
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: actualizadas, herramientas, introducción, conceptos básicos, unity, visual studio, toolkit
ms.openlocfilehash: 32dcda0eceb8d3717de7b2502d86f03cda975b8f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66453727"
---
# <a name="install-the-tools"></a>Instalación de las herramientas

Consigue las herramientas necesarias para compilar aplicaciones para Microsoft HoloLens y los cascos envolventes de Windows Mixed Reality. No hay ningún SDK independiente para el desarrollo con Windows Mixed Reality. Tendrás que usar Visual Studio con el SDK de Windows 10.

¿No tienes un dispositivo de realidad mixta? Puedes instalar el [emulador de HoloLens](using-the-hololens-emulator.md) para probar algunas funciones de las aplicaciones de realidad mixta sin necesidad de un dispositivo HoloLens. También puedes utilizar el [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) para probar las aplicaciones de realidad mixta con unos cascos envolventes.

Se recomienda instalar el motor de juegos de Unity como la manera más fácil de empezar a crear aplicaciones de realidad mixta. No obstante, también puedes compilar en DirectX si prefieres emplear un motor personalizado.

>[!TIP]
>Marca esta página como favorita y compruébala con regularidad para estar al día de la versión más reciente de cada herramienta recomendada para el desarrollo de realidad mixta.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Lista de comprobación de la instalación


| Herramienta | Descripción | Notas |
|---------|---------|---------|
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(Vínculo de instalación manual)</a> | Instala la versión más reciente de Windows 10 para que el sistema operativo del PC coincida con la plataforma para la que va a compilar las aplicaciones de realidad mixta. | **Instalación de Windows 10** <br> <ul><li>Puedes instalar la versión más reciente de Windows 10 mediante Windows Update en Configuración o mediante la creación de soportes de instalación (en el vínculo de la columna izquierda).<li>Consulta las [notas de la versión actual](release-notes-october-2018.md) para más información acerca de las características de realidad mixta más recientes disponibles en cada versión de Windows 10.</ul> **Habilita el modo para desarrolladores en el equipo** en Configuración > Actualización y seguridad > Para programadores. <br><br> **Nota para equipos empresariales o de administración corporativa:** si el equipo lo administra un departamento de TI de la organización, tendrás que ponerte en contacto con ellos para la actualización. <br><br> **Versiones "N" de Windows:** Los cascos envolventes de Windows Mixed Reality no son compatibles con las versiones "N" de Windows. |
| ![Logotipo de Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(vínculo de instalación)</a> | Entorno de desarrollo integrado (IDE) completo para Windows, etc. Vas a utilizar Visual Studio para escribir código, depurar, realizar pruebas e implementar. | **Cargas de trabajo para instalar:** <ul><li>Desarrollo de escritorio con C++</li><li>Desarrollo con la Plataforma universal de Windows</li></ul>**Nota acerca de Unity:** A menos que intencionadamente estés intentando instalar una versión más reciente (no LTS) de Unity para un propósito específico, se recomienda *no* instalar la carga de trabajo de Unity como parte de la instalación de Visual Studio y, en su lugar, instalar la secuencia 2018.4 LTS de Unity como se indica a continuación.<br> <br>**Nota:** Hay algunos problemas conocidos con el desarrollo de realidad mixta en Visual Studio 2019 en este momento.  Por ahora, se recomienda que sigas usando Visual Studio 2017. |
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**SDK de Windows 10 (10.0.18362.0)**<br>(Vínculo de instalación manual)</a> | Proporciona los encabezados, bibliotecas, metadatos y herramientas más recientes para compilar aplicaciones de Windows 10 en HoloLens 2. | Para compilar aplicaciones de HoloLens 2, deberás instalar el SDK de Windows, compilación 18362 o posterior.<br> <br> Si solo vas a desarrollar aplicaciones para cascos de Windows Mixed Reality o HoloLens (primera generación), puedes usar el SDK de Windows que instala Visual Studio 2017. |
| ![Logotipo de Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**Emulador de HoloLens 2**<br>(vínculo de instalación: 10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador de HoloLens (1ª generación)**<br>(vínculo de instalación: 10.0.17763.253)</a> | El emulador te permite ejecutar aplicaciones en una imagen de máquina virtual de HoloLens sin necesidad de un dispositivo HoloLens físico.<br> <br> Esta paquete también incluye plantillas de proyecto de DirectX holográficas para Visual Studio. | Consulta [Uso del emulador de HoloLens](using-the-hololens-emulator.md) para más información sobre cómo empezar a trabajar con el emulador.<br> <br> **El sistema debe admitir Hyper-V** para que la instalación del emulador se realice correctamente. Consulte la sección Requisitos del sistema que aparece a continuación para obtener los detalles. Si lo prefieres, puedes seleccionar instalar sólo las plantillas sin el emulador.<br>|
| ![Logotipo de Unity](images/unity_logo.png)<br><br><a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">**Unity 2018.4**<br>(vínculo de instalación)</a> | El motor de juego de Unity es la manera más fácil de crear experiencias de realidad mixta, con compatibilidad integrada con las características de Windows Mixed Reality. | Normalmente, se recomienda la versión Unity LTS (soporte técnico a largo plazo) como la mejor versión con la que empezar nuevos proyectos, actualizándola a la revisión más reciente para aprovechar las actualizaciones más estables.<br> <br>La recomendación actual es usar **Unity 2018.4.x**, que es la compilación LTS necesaria para MRTK v2 o versiones inferiores.<br> <br>Puede que a algunos desarrolladores les guste usar una versión diferente de Unity por motivos concretos. En esos casos, Unity admite instalaciones paralelas de distintas versiones. |
| ![Logotipo de MRTK](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Mixed Reality Toolkit (MRTK v2) for Unity**</a> | MRTK v2 for Unity es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.<br><br> MRTK v2 está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad. | Puedes encontrar más información acerca de MRTK v2 visitando el sitio <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">wiki de GitHub</a> del proyecto. |


## <a name="mixed-reality-toolkit"></a>Mixed Reality Toolkit

Mixed Reality Toolkit proporciona componentes y características que están pensadas para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit-Unity</a>: usa código del kit de herramientas básico y facilita su uso en Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a>: bits y componentes del código que no se pueden ejecutar directamente en HoloLens o en cascos envolventes sino que se emparejan para generar experiencias destinadas a Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Configuración del equipo para el desarrollo de realidad mixta

El SDK de Windows 10 funciona mejor en el sistema operativo Windows 10. Este SDK también es compatible con: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 y Windows Server 2008 R2. Ten en cuenta que no todas las herramientas son compatibles con sistemas operativos anteriores. 

### <a name="for-hololens-development"></a>Para el desarrollo de HoloLens

Cuando configures el equipo para el desarrollo de HoloLens, asegúrate de que cumple con los requisitos del sistema de <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> y de <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>. Si tienes previsto usar el emulador de HoloLens (primera generación), deberás asegurarte de que el PC también cumple con los [requisitos del sistema del emulador de HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Para empezar a trabajar con el emulador de HoloLens, consulta [Uso del emulador de HoloLens](using-the-hololens-emulator.md).

Si tienes previsto desarrollar aplicaciones para HoloLens y para los cascos envolventes de Windows Mixed Reality, usa los requisitos y recomendaciones del sistema que aparecen en la siguiente sección.

### <a name="for-immersive-vr-headset-development"></a>Para el desarrollo para cascos envolventes

>[!NOTE]
>Las instrucciones siguientes son las especificaciones actuales mínimas y recomendadas para el *equipo de desarrollo* para cascos envolventes y puede que se actualicen con regularidad.

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
<td> Memoria</td><td> 8 GB de RAM o más</td><td> 16 GB de RAM o más</td>
</tr><tr>
<td> Almacenamiento</td><td colspan="2"> &gt;Espacio libre adicional de 10 GB</td>
</tr><tr>
<td> Puertos USB</td><td colspan="2"> 1 puerto USB disponible para casco de realidad mixta (USB 3.0 Type-A) <b>Nota: el USB debe proporcionar un mínimo de 900 mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para la conectividad de los accesorios)</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también

* [Introducción al desarrollo](development-overview.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Uso del simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Introducción al desarrollo de DirectX](directx-development-overview.md)
* [Archivo del emulador de HoloLens](hololens-emulator-archive.md)
