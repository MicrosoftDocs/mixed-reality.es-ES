---
title: Modo de reproducción de Unity
description: Usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios en un dispositivo sin necesidad de implementar una aplicación.
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor remoto Holographic
ms.openlocfilehash: dca7ffba1270802fcabed8a88fe7428ef2981553
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277563"
---
# <a name="unity-play-mode"></a>Modo de reproducción de Unity

Una forma rápida de trabajar en el proyecto de Unity es usar el modo de reproducción. Se ejecuta la aplicación localmente en el editor de Unity en el equipo. Unity usa la comunicación remota holográfica para proporcionar una manera rápida de obtener una vista previa del contenido en un dispositivo HoloLens real. El modo de reproducción también puede usarse con un casco de realidad mixta de Windows conectado al equipo de desarrollo.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de reproducción de Unity con la comunicación remota holográfica

Con Holographic Remoting, puedes experimentar tu aplicación en HoloLens mientras se ejecuta en el editor de Unity en tu PC. La entrada de la asignación de miras, gestos, voz y espaciales se envía desde HoloLens al equipo. Los fotogramas representados se envían a su HoloLens. Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.
1. En HoloLens, vaya al **Microsoft Store** e instale la aplicación **[holográfica Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .
2. En HoloLens, inicie la aplicación de **reproductor de comunicación remota holográfica** .
3. En Unity, vaya al menú **ventana** y seleccione **emulación holográfica**.
4. Establezca el **modo de emulación** en **remoto en dispositivo**.
5. En **equipo remoto**, escriba la dirección IP de su HoloLens.
6. Haga clic en **Conectar**. Debería ver el cambio de estado de la **conexión** a **conectado** y ver que la pantalla aparece en blanco en HoloLens.
7. Haga clic en el botón **reproducir** para iniciar el modo de reproducción y experimentar la aplicación en su HoloLens.

Holographic Remoting requiere una conexión Wi-Fi y rápida de PC. Vea [Holographic Remoting Player](holographic-remoting-player.md) para obtener detalles completos.

Para obtener los mejores resultados, asegúrese de que la aplicación establece correctamente el [punto de enfoque](focus-point-in-unity.md). Esto ayuda a Holographic Remoting a adaptar mejor su escena a la latencia de la conexión inalámbrica.

## <a name="see-also"></a>Consulta también
* [Holographic Remoting Player](holographic-remoting-player.md)
