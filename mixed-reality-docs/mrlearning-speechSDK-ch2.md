---
title: 'Tutoriales de Azure Speech Services: 2. Agregar un modo sin conexión para la traducción de voz a texto local'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 962d7d4750cf59fe56de4af9088c90e8ecd0aa16
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913210"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. agregar un modo sin conexión para la traducción de voz a texto local

En este tutorial, vamos a agregar un modo sin conexión que le permite realizar la traducción de voz a texto local cuando no se puede conectar al servicio de Azure. También se *simulará* un estado desconectado.

## <a name="instructions"></a>Instrucciones

1. Seleccione el objeto de Lunarcom_Base de la jerarquía.

2. Haga clic en Agregar componente en el panel Inspector. Busque y seleccione el reconocimiento sin conexión de Lunarcom.

    ![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. Haga clic en la lista desplegable de LunarcomOfflineRecognizer y seleccione habilitado. Este programa el proyecto para que actúe como el usuario no tiene conexión.

    ![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. Presione reproducir en el editor de Unity y pruébelo. Presione el micrófono en la esquina inferior izquierda de la escena y empiece a hablar.

    >[!NOTE]
    >Como estamos sin conexión, se ha deshabilitado la funcionalidad de reactivación de Word. Deberá hacer clic físicamente en el micrófono cada vez que quiera que la voz se reconozca cuando esté sin conexión.

    A continuación se muestra un ejemplo de la apariencia que podría tener la escena.

    ![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Enhorabuena

Se ha habilitado el modo sin conexión. Ahora, cuando esté sin conexión, puede seguir trabajando en el proyecto con el SDK de Speech.

[Siguiente tutorial: 3. agregar el componente de traducción de voz de Azure Cognitive Services](mrlearning-speechSDK-ch3.md)
