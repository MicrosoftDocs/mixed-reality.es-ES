---
title: Introducción
description: En esta guía se describe la manera más rápida de empezar a trabajar con el desarrollo de realidad mixta.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: Introducción, conceptos básicos, HoloLens, auriculares envolvente, ar, VR, Unity, Visual Studio, Inicio rápido, procedimientos
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873960"
---
# <a name="get-started"></a>Introducción

Le agradecemos el mundo del desarrollo de realidad mixta. Si no está familiarizado con MR, esta guía será su centro para ponerse en marcha lo más rápido posible. Le ayudaremos a preparar su equipo para el desarrollo, a preparar los dispositivos y a instalar herramientas que acelerarán el proceso de desarrollo MR. 

## <a name="intro-to-mixed-reality"></a>Introducción a la realidad mixta

Es posible que tenga algunas preguntas sobre lo que significa "realidad mixta" y cómo se relaciona con la realidad aumentada (AR) y la realidad virtual (VR). En Resumen, la realidad mixta es la mezcla del mundo físico con el mundo digital, por lo que es un espectro que abarca todo, desde la realidad aumentada, donde el contenido digital se coloca en el mundo real, hasta la realidad virtual, donde el mundo real es casi totalmente reemplazado por el digital. 

![Ejemplo de una aplicación de realidad mixta que admite los auriculares HoloLens y envolventes (VR)](images/mr-island.png)<br>
*Las aplicaciones de realidad mixta pueden admitir los auriculares HoloLens y envolventes (VR)*

Hemos creado Windows Mixed Reality como una plataforma de desarrollo única y un conjunto de herramientas que pueden cubrir el espectro MR y actualmente se admiten dos tipos de dispositivos que cubren el mismo espectro: [Microsoft HoloLens](https://www.microsoft.com/hololens), el primero de los auriculares holográfica propio del mundo y [los auriculares y controladores de movimiento de realidad mixta de Windows](https://www.microsoft.com/windows/windows-mixed-reality), que se conectan a un equipo para obtener experiencias eficaces de realidad virtual. Puede consultar nuestro contenido de [Mixed Reality?] (artículo para obtener una respuesta más exhaustiva si está interesado.

## <a name="choose-your-development-path"></a>Elegir la ruta de acceso de desarrollo

La forma más fácil de desarrollar una aplicación de realidad mixta es usar [Unity](https://unity3d.com), una herramienta de middleware eficaz y popular que se suele usar para el desarrollo de juegos. Si desea usar un motor personalizado, también puede compilar [en DirectX](directx-development-overview.md), pero la mayoría de los desarrolladores de Mr usan Unity para sus juegos y aplicaciones. Con Unity podrá crear una aplicación de realidad mixta destinada a HoloLens, auriculares envolvente (VR) o ambos.

## <a name="prepare-your-pc-and-devices-for-development"></a>Preparación del equipo y los dispositivos para el desarrollo

Tanto si va a compilar una aplicación de realidad mixta destinada a HoloLens como a auriculares envolventes (VR), o ambas, usará un conjunto común de herramientas y API. También querrá asegurarse de que su equipo es lo suficientemente eficaz para el desarrollo que va a realizar. 

>[!NOTE]
>Puede encontrar nuestras recomendaciones sobre las especificaciones de los equipos de desarrollo, las versiones compatibles de cada herramienta de software y las opciones de configuración o las notas de configuración relevantes para cada una de ellas en el artículo [instalar las herramientas](install-the-tools.md) . Revise este artículo antes de instalar las herramientas siguientes.

Herramientas para instalar:
* [Unity](https://store.unity.com/download)
* [Visual Studio (con el SDK de Windows 10)](https://developer.microsoft.com/windows/downloads)
* [Kit de herramientas de realidad mixta para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

También querrá [poner el dispositivo de destino en modo de desarrollador y configurar Visual Studio para implementar aplicaciones en el dispositivo de destino](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Una nota sobre el kit de herramientas de realidad mixta para Unity

![MRTK para Unity](images/mrtkandunity.png)<br>

***YOYO Y DÍGALE A TODOS LOS MOTIVOS POR QUÉ MRTK-UNITY ES TAN ASOMBROSO Y TODO LO INTERESANTE QUE TIENE EN:)***

El kit de herramientas de realidad mixta es una colección de scripts y componentes diseñados para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens y a auriculares de Windows Mixed Reality. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.

## <a name="start-your-first-mr-project"></a>Inicie su primer proyecto MR

Ahora que el equipo y los dispositivos están configurados, está listo para crear su primer proyecto de realidad mixta en Unity. Siga los pasos que se indican en el primer [curso de la Academia Mr 100: Introducción a Unity](holograms-100.md)y, al final, tendrá un cubo activo y en ejecución en un casco de realidad mixta.

![Captura de pantalla de un cubo en un proyecto de Unity de realidad mixta](images/mr-cube.PNG)<br>
*Su primer proyecto de realidad mixta en Unity-Hello World!*

## <a name="learn-more-and-get-help"></a>Más información y obtener ayuda

Ahora que ha creado correctamente su primer proyecto MR, es probable que le resulte más seguro. Estos son algunos recursos que deben ayudar:
* [Documentación para desarrolladores de realidad mixta](mixed-reality.md) : ya está aquí, pero hay mucho más para desprotegerlo, incluida la documentación técnica, la guía de diseño, los proyectos de ejemplo y los casos prácticos.
* [Tutoriales de realidad mixta](tutorials.md) : siga los tutoriales que abarcan todo, desde la configuración de proyectos hasta la implementación de los principales bloques de creación, hasta la integración de Azure Cloud Services en la aplicación Mr.
* [Aprenda](https://unity3d.com/learn) el sitio web de Unity-Unity ofrece tutoriales, proyectos y sesiones de aprendizaje en vivo para los creadores en cada etapa del aprendizaje.

También puede obtener ayuda de estos excelentes recursos de la comunidad:
* [Foros de desarrolladores de realidad mixta](https://forums.hololens.com/) : el foro oficial para desarrolladores de realidad mixta para preguntar y responder a preguntas, así como para leer noticias de desarrollo de Mr directamente de Microsoft.
* [Canal de margen de demora de HoloDevelopers](https://holodevelopersslack.azurewebsites.net/) : el canal de desarrollador específico de la realidad mixta más robusta y ingenioso externo; los desarrolladores aquí son útiles y útiles.
* [Foros de Unity](https://forum.unity3d.com/) : foros oficiales de Unity.
