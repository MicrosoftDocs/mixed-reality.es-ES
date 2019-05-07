---
title: Comenzar
description: Esta guía describe la manera más rápida de empezar a trabajar con el desarrollo de realidad mixta.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: empezar a trabajar, conceptos básicos, HoloLens, auriculares envolventes, ar, vr, unity, visual studio, inicio rápido, cómo
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873960"
---
# <a name="get-started"></a>Comenzar

Bienvenido al mundo del desarrollo de realidad mixta. Si está familiarizado con el Sr., esta guía será el concentrador para poner en marcha y ejecutar tan pronto como sea posible. Le ayudaremos a marcha el conjunto de equipos para el desarrollo, preparar los dispositivos e instalar herramientas que permitirán acelerar el proceso de desarrollo MR. 

## <a name="intro-to-mixed-reality"></a>Introducción a la realidad mixta

Puede tener algunas preguntas sobre lo que queremos decir con "mixed reality" y cómo se relaciona con la realidad aumentada (AR) y realidad virtual (VR). En resumen, la realidad mixta es la combinación del mundo físico con el mundo digital, por lo que es un espectro que abarca todo, desde la realidad aumentada, donde se coloca el contenido digital en el mundo real, en realidad virtual, donde es casi por completo el mundo real reemplazado por el digital. 

![Ejemplo de una aplicación de realidad mixta que admita HoloLens e inmersivos (VR)](images/mr-island.png)<br>
*Pueden admitir aplicaciones de realidad mixta HoloLens e inmersivos (VR)*

Hemos creado Windows Mixed Reality como una sola plataforma de desarrollo y el conjunto de herramientas que puede cubrir el espectro de MR y actualmente se admiten dos tipos de dispositivo que cubre el espectro de la mismo: [Microsoft HoloLens](https://www.microsoft.com/hololens), primera autocontenida holográfica auriculares de todo el mundo, y [inmersivos Windows Mixed Reality y controladores de movimiento](https://www.microsoft.com/windows/windows-mixed-reality), que se conectarán a un equipo para experiencias eficaces de realidad virtual. Puede consultar nuestra ¿qué es [mixed reality?] (artículo de una respuesta más completa si le interesa.

## <a name="choose-your-development-path"></a>Elija la ruta de acceso de desarrollo

Está usando la manera más fácil de desarrollar una aplicación de realidad mixta [Unity](https://unity3d.com), una herramienta eficaz y popular middleware suelen utilizada para el desarrollo de juegos. Si desea usar un motor personalizado, también puede [compilar con DirectX](directx-development-overview.md), pero la mayoría de los desarrolladores MR usa Unity para sus aplicaciones y juegos. Con Unity podrá crear una aplicación de realidad mixta destinada a HoloLens, inmersivos (VR) o ambos.

## <a name="prepare-your-pc-and-devices-for-development"></a>Prepare su PC y dispositivos para el desarrollo

Si está creando una aplicación de realidad mixta destinada a HoloLens, inmersivos (VR) o ambos, se usará un conjunto común de herramientas y API. También conviene asegurarse de que es lo suficientemente eficaz para el desarrollo que realizará su PC. 

>[!NOTE]
>Puede encontrar especificaciones de nuestras recomendaciones en el equipo de desarrollo, las versiones compatibles de cada herramienta de software, y notas de la configuración o valores de configuración relevantes para cada uno de los [instalar las herramientas de](install-the-tools.md) artículo. Consulte ese artículo antes de instalar las herramientas siguientes.

Herramientas para instalar:
* [Unity](https://store.unity.com/download)
* [Visual Studio (con Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Kit de herramientas de realidad mixta para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

También deseará [poner el dispositivo de destino en modo de programador y configurar Visual Studio para implementar aplicaciones en el dispositivo de destino](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Una nota sobre el Kit de herramientas de realidad mixta para Unity

![MRTK para Unity](images/mrtkandunity.png)<br>

***YOYO ESTE COMANDO MATERIALIZAR Y TODOS LOS USUARIOS SABER POR QUÉ ES TAN ASOMBROSA MRTK UNITY Y TODAS LAS COSAS INTERESANTES TIENE DENTRO DE :)***

El Kit de herramientas de realidad mixta es una colección de secuencias de comandos y los componentes diseñados para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens y Windows Mixed Reality auriculares. El proyecto está destinado a reducir las barreras de entrada para crear aplicaciones de realidad mixta y contribuir a la Comunidad que todos a medida que crecen.

## <a name="start-your-first-mr-project"></a>Iniciar su primer proyecto MR

Ahora que su PC y dispositivos están configuradas, está listo para crear su primer proyecto de realidad mixta en Unity. Gracias a nuestro primer curso de la Academia MR, [MR 100 de conceptos básicos: Introducción a Unity](holograms-100.md), y al final, tendrá un cubo y funcionando en auriculares de realidad mixta.

![Captura de pantalla de un cubo en un proyecto de Unity de realidad mixta](images/mr-cube.PNG)<br>
*¡Su primer proyecto de realidad mixta en Unity: Hola a todos!*

## <a name="learn-more-and-get-help"></a>Obtenga más información y obtener ayuda

Ahora que ha creado correctamente su primer proyecto MR, probablemente ya tenga ganas para obtener más información. Estos son algunos recursos que le ayudarán:
* [Mixto documentación para desarrolladores de realidad](mixed-reality.md) : ya está aquí, pero hay mucho más que desproteja, incluidos casos prácticos, instrucciones de diseño, proyectos de ejemplo y documentación técnica.
* [Mixto tutoriales realidad](tutorials.md) -seguir tutoriales que abarcan todo, desde configurar proyectos para implementar los bloques de creación fundamentales MR, a la integración de Azure servicios en la nube en su aplicación MR.
* [Obtenga información sobre Unity](https://unity3d.com/learn) -sitio Web de Unity ofrece tutoriales, proyectos y las sesiones de formación en línea para los creadores de en cada fase de aprendizaje.

También puede obtener ayuda de estos recursos de comunidad excelente:
* [Foros para desarrolladores de realidad mixta](https://forums.hololens.com/) -el foro oficial para desarrolladores de realidad mixta formular y responder preguntas, así como leer noticias de desarrollo MR directamente de Microsoft.
* [Canal de Slack HoloDevelopers](https://holodevelopersslack.azurewebsites.net/) -externo más sólida y con recursos mixto de canal de desarrollador específica de la realidad; aquí los desarrolladores son expertos y útil.
* [Foros de Unity](https://forum.unity3d.com/) -foros oficiales de Unity.
