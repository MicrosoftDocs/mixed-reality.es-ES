---
title: 1. Introducción
description: Parte 1 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 39e4e7218341dcc69eacf01f43b5e0721e76031b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720381"
---
# <a name="1-getting-started"></a>1. Introducción

Independientemente de que no esté familiarizado con la realidad virtual o que sea un profesional experimentado, aquí empieza su camino con [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) y [Unreal Engine](https://www.unrealengine.com/en-US/). En esta serie de tutoriales se ofrece una guía paso a paso sobre cómo compilar una aplicación de ajedrez interactiva con el [complemento UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte de [Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal). El complemento le ayudará a agregar características comunes de UX a sus proyectos con código, planos técnicos y ejemplos. 

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

Al final de la serie tendrá experiencia práctica en las siguientes tareas:
* Inicio de un nuevo proyecto
* Configuración para la realidad mixta
* Trabajo con la entrada de usuario
* Adición de botones
* Reproducción en un emulador o un dispositivo

Si tiene alguna pregunta, consulte nuestra [Introducción al desarrollo con Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).

## <a name="prerequisites"></a>Requisitos previos
Asegúrese de que cumple los siguientes requisitos antes de empezar:
* Windows 10 1809 o posterior
* SDK de Windows 10 10.0.18362.0 o posterior
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 o posterior
* Un dispositivo Microsoft HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode) o un emulador
* Visual Studio 2019 con las cargas de trabajo siguientes

### <a name="installing-visual-studio-2019"></a>Instalación de Visual Studio 2019
El último paso es configurar Visual Studio de la manera siguiente:
1. Instale la versión más reciente de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).
2. Instale las [cargas de trabajo](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads) siguientes:
    * Desarrollo de escritorio con C++
    * Desarrollo de escritorio de .NET
    * Desarrollo con la Plataforma universal de Windows

3. Instale los [componentes](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components) siguientes:
    * Compiladores, herramientas de compilación y entornos en tiempo de ejecución > herramientas de desarrollo para ARM64 en C++ de MSVC v142 - VS 2019 (versión más reciente)

Eso es todo. Está listo para pasar a iniciar el proyecto de aplicación de ajedrez.

[Sección siguiente: 2. Inicialización del proyecto y primera aplicación](unreal-uxt-ch2.md)