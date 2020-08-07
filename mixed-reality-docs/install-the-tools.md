---
title: Instalación de las herramientas
description: Empieza aquí a prepararte para el desarrollo de realidad mixta. En este artículo deberían aparecer siempre las versiones más actuales de Unity, Visual Studio y las demás herramientas recomendadas para el desarrollo con HoloLens y con los cascos envolventes de Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 07/31/2020
ms.topic: article
ms.localizationpriority: high
keywords: actualizadas, herramientas, introducción, conceptos básicos, unity, visual studio, toolkit
ms.openlocfilehash: f5c779aa0bb89fe66b53419b03ec1b4d3e6b562b
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476914"
---
# <a name="install-the-tools"></a>Instalación de las herramientas

Consigue las herramientas necesarias para compilar aplicaciones para Microsoft HoloLens y los cascos envolventes de Windows Mixed Reality (VR). No hay ningún SDK independiente para el desarrollo con Windows Mixed Reality. Tendrás que usar Visual Studio con el SDK de Windows 10.

¿No tienes un dispositivo de realidad mixta? Puedes instalar el [emulador de HoloLens](using-the-hololens-emulator.md) para probar algunas funciones de las aplicaciones de realidad mixta sin necesidad de un dispositivo HoloLens. También puedes utilizar el [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) para probar las aplicaciones de realidad mixta con unos cascos envolventes. Si usa Unity, puede usar la simulación de entrada de [Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) para probar varios tipos de interacciones de entrada, como el seguimiento de la mano y el ocular.

Se recomienda instalar el motor de juego de Unity como la manera más sencilla de empezar a crear aplicaciones de realidad mixta. Sin embargo, también puedes compilar en DirectX si quieres utilizar un motor personalizado.

>[!TIP]
>Marca esta página como favorita y compruébala con regularidad para estar al día de la versión más reciente de cada herramienta recomendada para el desarrollo de realidad mixta.

<br>

## <a name="installation-checklist"></a>Lista de comprobación de la instalación


| Herramienta | Notas |
|---------|---------|
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (vínculo de instalación manual)</a><br><br>Instala la versión más reciente de Windows 10 para que el sistema operativo del equipo coincida con la plataforma para la que vas a compilar las aplicaciones de realidad mixta.  | **Instalación de Windows 10** <br> Puedes instalar la versión más reciente de Windows 10 mediante Windows Update en Configuración o mediante la creación de soportes de instalación a través del vínculo de la columna izquierda. <br><br>Consulta las [notas de la versión actual](release-notes-october-2018.md) para más información acerca de las características de realidad mixta más recientes disponibles en cada versión de Windows 10. **Habilita el modo para desarrolladores en el equipo** en Configuración > Actualización y seguridad > Para programadores. <br><br> **Nota para equipos empresariales y de administración corporativa**<br>Si administra el equipo un departamento de TI de la organización, es posible que deba ponerse en contacto con ellos para la actualización. <br><br> **Versiones "N" de Windows**<br> Los cascos envolventes de Windows Mixed Reality no son compatibles con las versiones "N" de Windows. |
| ![Logotipo de Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.2 o superior)** (vínculo de instalación)</a> <br><br>Entorno de desarrollo integrado (IDE) completo para Windows, etc. Vas a utilizar Visual Studio para escribir código, depurar, realizar pruebas e implementar. | Asegúrate de instalar las siguientes cargas de trabajo: <br><br>**● Desarrollo de escritorio con C++**<br>**● Desarrollo para la Plataforma universal de Windows (UWP)**<br><br>En la carga de trabajo de UWP, asegúrate de comprobar el siguiente componente opcional si vas a desarrollar para HoloLens:<br><br>**● Conectividad con dispositivo USB**<br><br>**Nota acerca de Unity**<br>A menos que esté intentando instalar de manera intencionada una versión más reciente (no LTS) de Unity para un propósito específico, le recomendamos que *no* instale la carga de trabajo de Unity como parte de la instalación de Visual Studio y que, en su lugar, instale el flujo **Unity 2019 LTS** como se indica a continuación.<br><br>**Note**<br>Hay algunos problemas conocidos con la depuración de aplicaciones de realidad mixta en Visual Studio 2019, versión 16.0.  Asegúrate de actualizar a **Visual Studio 2019, versión 16.2 o superior**. |
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK de Windows 10 (10.0.18362.0)** (vínculo de instalación manual)</a> <br><br>Proporciona los encabezados, bibliotecas, metadatos y herramientas más recientes para compilar aplicaciones de Windows 10 en HoloLens 2. | **Para compilar aplicaciones de HoloLens 2, debe instalar Windows SDK, compilación 18362 o posterior.**<br> <br> Si solo vas a desarrollar aplicaciones para cascos de Windows Mixed Reality o HoloLens (1.ª generación), puedes usar el SDK de Windows que instala Visual Studio 2017. |
| ![Logotipo de Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2132415" target="_blank">**Emulador de HoloLens 2 (Windows Holographic, versión 2004, actualización de junio de 2020)** (vínculo de instalación: 10.0.19041.1106)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador de HoloLens (Gen 1)** (vínculo de instalación: 10.0.17763.134)</a> <br><br>El emulador te permite ejecutar aplicaciones en una imagen de máquina virtual de HoloLens sin necesidad de un dispositivo HoloLens físico.<br> <br> | Consulta [Uso del emulador de HoloLens](using-the-hololens-emulator.md) para más información sobre cómo empezar a trabajar con el emulador.<br> <br> **El sistema debe admitir Hyper-V** para que la instalación del emulador se realice correctamente. Consulta la sección Requisitos del sistema que aparece a continuación para obtener los detalles. <br>|

## <a name="choose-your-engine"></a>Elige el motor

Ahora que tiene Windows 10, Visual Studio y el SDK de Windows 10 listos para usar, vamos a elegir un motor con el cual crear. 

[!INCLUDE[](~/includes/tools-overview.md)]
