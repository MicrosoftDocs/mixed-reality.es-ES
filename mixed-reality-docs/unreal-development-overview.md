---
title: Introducción al desarrollo con Unreal
description: Para empezar a crear aplicaciones de realidad mixta en Unreal.
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, comunicación remota, realidad mixta, desarrollo, introducción, nuevo proyecto, emulador, documentación
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491174"
---
# <a name="unreal-development-overview"></a>Introducción al desarrollo con Unreal

La compatibilidad de Unreal Engine 4 con la realidad mixta ahora se encuentra en versión beta. Si no estás familiarizado con el desarrollo con Unreal, la página <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Introducción a Unreal Engine 4</a> te resultará ideal para explorarlo. Si necesitas recursos, Unreal dispone de un <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a> completo. 

Una vez que hayas adquirido conocimientos básicos de Unreal Engine 4, puedes visitar la página <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Desarrollo de Microsoft HoloLens</a> en el sitio de documentación de Unreal Engine para obtener información sobre cómo crear y ejecutar tus aplicaciones en HoloLens. No olvides visitar los <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">foros de realidad mixta de Unreal</a> para interactuar con la comunidad que crea aplicaciones de realidad mixta en Unreal. Es un lugar idóneo en el que buscar soluciones a los problemas con los que puedes encontrarte.

## <a name="installing-the-prerequisites"></a>Instalación de los requisitos previos

Para empezar a crear una aplicación para HoloLens 2 en Unreal, necesitarás el [emulador de HoloLens 2](using-the-hololens-emulator.md) o un casco de HoloLens. También deberás instalar la versión más reciente de Visual Studio con las cargas de trabajo y los componentes que se indican en <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">Requisitos previos de HoloLens 2 para Unreal</a>.

## <a name="building-and-running-your-unreal-app"></a>Compilación y ejecución de tu aplicación de Unreal

En primer lugar, <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">empaqueta tu aplicación para HoloLens 2</a>. A continuación, elige dónde quieres implementar el paquete:
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Implementar en el emulador de HoloLens 2</a>
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Implementar en un casco de HoloLens 2</a>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>Streaming de tu aplicación a un casco mediante Holographic Remoting Player

Hacer streaming de tu aplicación desde el dispositivo de escritorio a la aplicación Holographic Remoting Player en un casco de HoloLens tienes dos ventajas principales: 
* Acelera el desarrollo, por lo que no es necesario volver a empaquetar y cargar la aplicación cada vez que se realiza un cambio.
* Aprovecha la eficacia de tu dispositivo de escritorio, de modo que puedas representar tantos polígonos como permita tu GPU de escritorio, sin estar limitado al ordenador disponible en el casco.

Para empezar a usar el streaming, consulta el <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">Inicio rápido de streaming de HoloLens 2</a>[]().

## <a name="see-also"></a>Consulta también
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Instrucciones de rendimiento de Unreal para dispositivos móviles</a>
