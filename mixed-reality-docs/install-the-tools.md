---
title: Instalar las herramientas
description: Comience aquí para prepararse para el desarrollo de realidad mixta. En este artículo siempre debe reflejar las versiones más actuales de Unity, Visual Studio y otras herramientas que se recomienda para el desarrollo de auriculares envolventes de HoloLens y Windows Mixed Reality.
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: actualizados, herramientas, introducción, conceptos básicos, unity, visual studio, Kit de herramientas
ms.openlocfilehash: 03a310457bf5ef498a6369a158b697c7fa59d6d9
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730877"
---
# <a name="install-the-tools"></a>Instalar las herramientas

Obtenga las herramientas que necesita para compilar aplicaciones para Microsoft HoloLens e inmersivos (VR) Windows Mixed Reality. No hay ninguna separación de desarrollo SDK para Windows Mixed Reality; usará Visual Studio con el SDK de Windows 10.

¿No tiene un dispositivo de realidad mixta? Puede instalar el [emulador de HoloLens](using-the-hololens-emulator.md) para probar algunas funciones de aplicaciones de realidad mixta sin un HoloLens. También puede usar el [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) para probar sus aplicaciones de realidad mixta para inmersivos.

Se recomienda instalar el motor de juegos de Unity como mixto de la manera más fácil empezar a crear aplicaciones de realidad, sin embargo, también puede compilar con DirectX si desea usar un motor personalizado.

>[!TIP]
>Marque esta página y la comprobará periódicamente para mantenerse en la versión más reciente de cada herramienta recomendada para el desarrollo de realidad mixta.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Lista de comprobación de instalación


| Herramienta | Descripción | Notas |
|---------|---------|---------|
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(Vínculo de instalación manual)</a> | Instale la versión más reciente de Windows 10 para la plataforma para el que va a crear aplicaciones de realidad mixta coincida con el sistema operativo de su PC. | **Instalación de Windows 10** <br> <ul><li>Puede instalar la versión más reciente de Windows 10 a través de Windows Update en la configuración o mediante la creación de medios de instalación (mediante el vínculo de la columna izquierda).<li>Consulte [notas de la versión actual](release-notes-october-2018.md) para obtener información acerca de la más reciente mixto características realidad disponibles con cada versión de Windows 10.</ul> **Habilitar el modo de desarrollador en su PC** en Configuración > actualización y seguridad > para los desarrolladores. <br><br> **Nota para la empresa y equipos corporativos administrados:** si su equipo está administrado por una de su organización el departamento de TI, es posible que deba ponerse en contacto con ellos con el fin de actualizar. <br><br> **Versiones de "n" de Windows:** Auriculares de Windows Mixed Reality envolventes (VR) no se admiten en las versiones de "n" de Windows. |
| ![Logotipo de Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(Vínculo de instalación)</a> | Completo entorno de desarrollo integrado (IDE de) Windows y mucho más. Usará Visual Studio para escribir código, depurar, probar e implementar. | **Cargas de trabajo para instalar:** <ul><li>Desarrollo de escritorio con C++</li><li>Desarrollo de plataforma de Windows universal</li></ul>**Tenga en cuenta acerca de Unity:** A menos que intencionadamente está intentando instalar una versión (no-LTS) más reciente de Unity para un propósito específico, se recomienda *no* instalar la carga de trabajo de Unity como parte de la instalación de Visual Studio e instalar en su lugar el 2018.3 LTS flujo de Unity que se indican a continuación.<br> <br>**Nota:** Hay algunos problemas conocidos con el desarrollo de realidad mixta en Visual Studio de 2019 en este momento.  Por ahora, se recomienda que siga usando Visual Studio 2017. |
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(Vínculo de instalación manual)</a> | Proporciona las últimas encabezados, metadatos, bibliotecas y herramientas para crear aplicaciones de Windows 10 en HoloLens 2. | Para compilar aplicaciones de HoloLens 2, deberá instalar el Windows SDK, compilación 18362 o posterior.<br> <br> Si solo va a desarrollar aplicaciones para escritorio auriculares de realidad mixta de Windows o HoloLens (gen 1), puede usar el SDK de Windows instalados por Visual Studio 2017. |
| ![Logotipo de Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**Emulador de HoloLens 2**<br>(Vínculo de instalación: 10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (gen 1) emulador**<br>(Vínculo de instalación: 10.0.17763.253)</a> | El emulador le permite ejecutar aplicaciones en una imagen de máquina virtual de HoloLens sin un HoloLens físico.<br> <br> Este paquete también incluye plantillas de proyecto de DirectX holographic para Visual Studio. | Consulte [mediante el emulador de HoloLens](using-the-hololens-emulator.md) para obtener más información sobre cómo comenzar con el emulador.<br> <br> **El sistema debe admitir Hyper-V** para la instalación del emulador se realice correctamente. Consulte la sección Requisitos del sistema, a continuación para obtener los detalles. Si lo desea, puede seleccionar para instalar sólo las plantillas sin el emulador.<br>|
| ![Logotipo de Unity](images/unity_logo.png)<br><br><a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 2018.3**<br>(Vínculo de instalación)</a> | El motor de juego Unity es la manera más fácil de crear experiencias de realidad mixta, con compatibilidad integrada para las características de Windows Mixed Reality. | Normalmente, se recomienda la secuencia de LTS de Unity (Long Term Support) como la mejor versión con la que se va a iniciar nuevos proyectos, la actualización para su revisión más reciente para recoger las correcciones estables más recientes.<br> <br> Recomendación actual es usar **Unity 2018.3.x**, lo cual es necesario para MRTK v2 a continuación y que pronto se harán 2018 LTS de Unity de compilación. <br> <br> Algunos desarrolladores que desee usar una versión diferente de Unity por razones específicas. Para esos casos, Unity es compatible con instalaciones en paralelo de distintas versiones. |
| ![Logotipo MRTK](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Kit de herramientas de realidad mixta (MRTK v2) para Unity**</a> | MRTK v2 para Unity es un kit de desarrollo multiplataforma de código abierto para las aplicaciones de realidad mixta.<br><br> MRTK v2 está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, inmersivos (VR) Windows Mixed Reality y la plataforma OpenVR. El proyecto está destinado a reducir las barreras de entrada para crear aplicaciones de realidad mixta y que contribuyen a la Comunidad como somos crecer. | Más información sobre MRTK v2 visitando el proyecto <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">wiki de GitHub</a>. |


## <a name="mixed-reality-toolkit"></a>Kit de herramientas de realidad mixta

El Kit de herramientas de realidad mixta proporciona componentes y características que están diseñadas para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, auriculares de realidad mixta de Windows y plataforma OpenVR. El proyecto está destinado a reducir las barreras de entrada para crear aplicaciones de realidad mixta y contribuir a la Comunidad que todos a medida que crecen.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> - usa código desde el Kit de herramientas base y hace que sea más fácil de consumir en Unity.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> : código de bits y componentes que no se pueden ejecutar directamente en HoloLens o inmersivos (VR), pero en su lugar par con ellos para crear experiencias de destino es Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Configuración de su PC para el desarrollo de realidad mixta

El SDK de Windows 10 funciona mejor en el sistema operativo Windows 10. Este SDK también se admite en Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2. Tenga en cuenta que no todas las herramientas se admiten en sistemas operativos anteriores. 

### <a name="for-hololens-development"></a>Para el desarrollo de HoloLens

Al configurar el equipo de desarrollo para el desarrollo de HoloLens, asegúrese de que cumple los requisitos del sistema para ambos <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> y <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>. Si tiene previsto usar el HoloLens (gen 1) emulador, querrá asegurarse de que su PC de cumple el [requisitos de sistema del emulador de HoloLens](using-the-hololens-emulator.md#hololens-emulator-system-requirements) también.

Para empezar a trabajar con el emulador de HoloLens, vea [mediante el emulador de HoloLens](using-the-hololens-emulator.md).

Si tiene previsto para el desarrollo para HoloLens y Windows Mixed Reality inmersivos de (VR), use los requisitos y recomendaciones del sistema en la sección siguiente.

### <a name="for-immersive-vr-headset-development"></a>Para desarrollo de auriculares envolvente (VR)

>[!NOTE]
>Las instrucciones siguientes son las especificaciones actuales mínimas y recomendadas para los auriculares (VR) envolventes *equipo de desarrollo*y puede actualizarse con regularidad.

>[!WARNING]
>No lo confunda con el [instrucciones de compatibilidad de hardware de PC mínimos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que se detallan los *especificaciones de consumidor PC* a la que debe dirigirse la aplicación de auriculares de envolventes (VR) o el juego.

Si el equipo de desarrollo envolvente auriculares no tiene puertos HDMI o USB 3.0 de tamaño completo, necesitará [adaptadores](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar los auriculares.

Actualmente no hay [problemas conocidos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con algunas configuraciones de hardware, especialmente con blocs de notas que tienen gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Procesador</td><td> <b>cuaderno:</b> Mobile de Intel Core i5 generación comienzan el 7 de CPU, núcleos con Hyper Threading <b>escritorio:</b> I5 6ª generación de CPU, núcleos con Hyper Threading de Intel Desktop <b>o</b> FX4350 AMD equivalente de núcleo cuádruple de 4,2 Ghz</td><td> <b>Escritorio:</b> Escritorio Intel i7 6ª generación (6 núcleos) <b>o</b> AMD Ryzen 1600 5 (6 núcleos, 12 subprocesos)</td>
</tr><tr>
<td> GPU</td><td> <b>cuaderno:</b> NVIDIA GTX 965M, RX 460M (2GB) de AMD equivalente o mayor DX12 GPU compatible con <b>escritorio:</b> RX 460 (2GB) de AMD Radeon equivalente o mayor DX12 compatibles con GPU de NVIDIA GTX 960/1050,</td><td><b>Escritorio:</b> RX 480 (2GB) de AMD Radeon equivalente o mayor DX12 compatibles con GPU de NVIDIA GTX 980/1060,</td>
</tr><tr>
<td> Versión del controlador WDDM de GPU</td><td colspan="2"> Controlador WDDM 2.2</td>
</tr><tr>
<td> Potencia del diseño térmico</td><td colspan="2"> 15 o superior</td>
</tr><tr>
<td> Los puertos muestren gráficos</td><td colspan="2"> 1 x gráficos disponibles mostrar puerto para&#160;auriculares (1.4 HDMI o DisplayPort 1.2 para auriculares de 60 Hz, HDMI 2.0 o DisplayPort 1.2 para auriculares de 90 Hz)</td>
</tr><tr>
<td> Resolución de pantalla</td><td colspan="2"> Solución: SVGA (800 x 600) o mayor profundidad de bits: 32 bits de color por píxel</td>
</tr><tr>
<td> Memoria</td><td> 8&#160;GB de RAM o superior</td><td> 16 GB de RAM o superior</td>
</tr><tr>
<td> Almacenamiento</td><td colspan="2"> &gt;10 GB de espacio libre adicional</td>
</tr><tr>
<td> Puertos USB</td><td colspan="2"> 1 x USB disponible el puerto para auriculares (USB 3.0 Type-A) <b>Nota: USB debe proporcionar un mínimo de 900mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para la conectividad de accesorio)</td>
</tr>
</table>

## <a name="see-also"></a>Vea también

* [Información general sobre desarrollo](development-overview.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Uso del simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Introducción al desarrollo de DirectX](directx-development-overview.md)
* [Archivo del emulador de HoloLens](hololens-emulator-archive.md)
