---
title: 'Tutoriales de Azure Speech Services: 3. Adición del componente de traducción de voz de Azure Cognitive Services'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913200"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. agregar el componente de traducción de voz de Azure Cognitive Services

En este tutorial, aprendemos sobre el componente de traducción de voz de Azure Cognitive Services en nuestro proyecto, además de traducirse en tres lenguajes diferentes.

## <a name="instructions"></a>Instrucciones

1. Seleccione el objeto de Lunarcom_Base de la jerarquía y haga clic en Agregar componente en el panel Inspector. Busque y seleccione reconocedor de traducción de Lunarcom.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Deshabilite el simulador en modo sin conexión.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Antes de continuar, asegúrese de que el simulador en modo sin conexión está deshabilitado, tal como se muestra en la imagen anterior, antes de probar el traductor de Speech-SDK. Para traducir, debe estar conectado a Internet.

2. Haga clic en la lista desplegable del reconocedor de traducción de Lunarcom y seleccione el idioma al que le gustaría traducir.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Ahora, ejecute la aplicación y pruebe el traductor; para ello, haga clic en el botón satélite y empiece a hablar. Vuelva a presionar el botón satélite para detener el reconocimiento. A continuación se muestra un ejemplo de la apariencia de la escena. No dude en cambiar el idioma en la lista desplegable "idioma de destino" (consulte la imagen anterior) para explorar la traducción en otros idiomas.

    A continuación se muestra un ejemplo de la apariencia de la escena:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Enhorabuena

Ahora el proyecto puede traducir las palabras que habla en varios idiomas diferentes. No dude en experimentar con los lenguajes y probar la precisión de la traducción.

[Siguiente tutorial: 4. configuración del propósito y comprensión del lenguaje natural](mrlearning-speechSDK-ch4.md)
