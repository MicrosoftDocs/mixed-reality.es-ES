---
title: 'Tutoriales de Azure Speech Services: 3. Adición del componente de traducción de voz de Azure Cognitive Services'
description: En este curso, aprenderá a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143227"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. agregar el componente de traducción de voz de Azure Cognitive Services

En este tutorial, obtendrá información sobre el componente de traducción de voz de Azure Cognitive Services del proyecto, así como sobre cómo traducir en tres idiomas diferentes.

## <a name="instructions"></a>Instrucciones

1. Seleccione el objeto de Lunarcom_Base de la jerarquía y haga clic en Agregar componente en el panel Inspector. Busque y seleccione reconocedor de traducción de Lunarcom.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Deshabilite el simulador en modo sin conexión.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Antes de continuar, asegúrese de que el simulador en modo sin conexión está deshabilitado (como se muestra en la imagen anterior) antes de probar el traductor de Speech-SDK. Para traducir, debe estar conectado a Internet.

2. Haga clic en la lista desplegable del reconocedor de traducción de Lunarcom y seleccione el idioma al que le gustaría traducir.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Ejecute la aplicación y pruebe el traductor; para ello, haga clic en el botón satélite y empiece a hablar. Vuelva a presionar el botón satélite para detener el reconocimiento. A continuación se muestra un ejemplo de la apariencia de la escena. No dude en cambiar el idioma en la lista desplegable "idioma de destino" (consulte la imagen anterior) para explorar la traducción en otros idiomas.

    A continuación se muestra un ejemplo de la apariencia de la escena:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Enhorabuena

El proyecto ahora puede traducir correctamente las palabras que habla en varios idiomas diferentes. No dude en experimentar con los lenguajes y probar la precisión de la traducción.

[Siguiente tutorial: 4. configuración del propósito y comprensión del lenguaje natural](mrlearning-speechSDK-ch4.md)
