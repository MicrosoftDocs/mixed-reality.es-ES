---
title: 'Tutoriales de Azure Speech Services: 3. Adición del componente de traducción de voz de Azure Cognitive Services'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 27742702f7a274b3212cdf12c77d8acfa0a29834
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701824"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Adición del componente de traducción de voz de Azure Cognitive Services

En este tutorial, aprendemos Aabout el componente de traducción de voz de Azure Cognitive Services en nuestro proyecto, además de traducirse en tres lenguajes diferentes. 

## <a name="instructions"></a>Instrucciones

1. Seleccione el objeto Lunarcom_Base en la jerarquía y haga clic en Agregar componente en el panel Inspector. Busque y seleccione LunarcomTranslationRecognizer.

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> Nota: Asegúrese de que el simulador en modo sin conexión está deshabilitado antes de probar el traductor de Speech-SDK. Para traducir, debe estar conectado a Internet. Vea la imagen siguiente sobre dónde encontrar esta configuración. 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. Haga clic en la lista desplegable de LunarcomTranslationRecognizer y seleccione el idioma al que le gustaría traducir.

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Ahora, ejecute la aplicación y pruebe el traductor; para ello, haga clic en el botón satélite y empiece a hablar. Vuelva a presionar el botón satélite para detener el reconocimiento. A continuación se muestra un ejemplo de la apariencia de la escena. No dude en cambiar el idioma en la lista desplegable "idioma de destino" (consulte la imagen anterior) para explorar la traducción en otros idiomas.

> Nota: Antes de realizar las pruebas, asegúrese de que el simulador sin conexión está deshabilitado, tal como se muestra en la imagen siguiente.
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

A continuación se muestra un ejemplo de la apariencia de la escena:

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Enhorabuena

Ahora el proyecto puede traducir las palabras que habla en varios idiomas diferentes. No dude en experimentar con los lenguajes y probar la precisión de la traducción. 

[Siguiente tutorial: 4.  Configuración de reconocimiento de intenciones y comprensión del lenguaje natural](mrlearning-speechSDK-ch4.md)

