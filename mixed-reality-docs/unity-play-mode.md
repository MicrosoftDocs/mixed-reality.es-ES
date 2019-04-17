---
title: Modo de juego de Unity
description: Uso del modo de reproducir en el editor de Unity para obtener una vista previa de los cambios en un dispositivo sin necesidad de implementar una aplicación.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicación remota, remoting holográfica, Reproductor de remoting holográfica
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597827"
---
# <a name="unity-play-mode"></a>Modo de juego de Unity

Una forma rápida de trabajar en el proyecto de Unity es usar el "Modo de reproducir". Esto ejecuta la aplicación localmente en el editor de Unity en su PC. Unity usa holográfica Remoting para proporcionar una forma rápida de obtener una vista previa de su contenido en un dispositivo real de HoloLens.

## <a name="unity-play-mode-with-holographic-remoting"></a>Modo de juego Unity con comunicación remota holográfica

Con la comunicación remota de holográfica, pueden experimentar la aplicación en el HoloLens, mientras se ejecuta en el editor de Unity en su PC. Mirada, gestos, voz y entrada de asignación espacial se envía desde su HoloLens a su equipo. Fotogramas representados, a continuación, se envían a su HoloLens. Esto es una excelente manera de depurar la aplicación rápidamente sin compilar e implementar un proyecto completo.
1. En su HoloLens, vaya a la **Microsoft Store** e instale el **[holográfica Reproductor Remoting](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.
2. En su HoloLens, inicie el **holográfica Reproductor Remoting** app.
3. En Unity, vaya a la **ventana** menú y seleccione **emulación holográfica**.
4. Establecer **en modo de emulación** a **remota al dispositivo**.
5. Para **máquina remota**, escriba la dirección IP de su HoloLens.
6. Haga clic en **Conectar**. Debería ver **estado de la conexión** cambie a **conectado** y marche la pantalla en blanco en el HoloLens.
7. Haga clic en el **reproducir** botón para iniciar el modo de reproducción y la experiencia de la aplicación en su HoloLens.

Remoting holográfica requiere una conexión rápida de PC y Wi-Fi. Consulte [holográfica Reproductor Remoting](holographic-remoting-player.md) para obtener detalles completos.

Para obtener mejores resultados, asegúrese de que la aplicación establece adecuadamente el [centrarse punto](focus-point-in-unity.md). Esto ayuda a holográfica Remoting para adaptar mejor la escena a la latencia de la conexión inalámbrica.

## <a name="see-also"></a>Vea también
* [Reproductor de Remoting holográfica](holographic-remoting-player.md)
