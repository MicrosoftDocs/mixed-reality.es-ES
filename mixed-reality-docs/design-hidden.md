---
layout: LandingPage
title: Empezar a diseñar y a crear prototipos
description: Estoy listo para crear algo. Conoce los conceptos básicos que necesitas para empezar a diseñar y a crear prototipos.
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidad mixta, detectar, distribuir, índice, página de inicio, diseño, desarrollo, tutoriales, aplicaciones de ejemplo, aspectos básicos, casos prácticos, recursos, procedimientos de HoloLens, proyectos de código abierto
ms.openlocfilehash: 3efb411425d18a8f50a209b69b00bfa038d594f1
ms.sourcegitcommit: 183b6248807f600fe7d83daa13a6fe0b0f0dc846
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "70148011"
---
# <a name="start-designing-and-prototyping"></a>Empezar a diseñar y a crear prototipos


![bloques de creación](images/text_in_unity_viewingangle.jpg)

## <a name="what-are-the-core-concepts-of-an-experience"></a>¿Cuáles son los conceptos básicos de una experiencia?

### <a name="keep-the-user-comfortable---comfortcomfortmd"></a>[Preservar la comodidad del usuario (confort)](comfort.md)
Para garantizar la máxima comodidad de los cascos de realidad virtual, es importante que los diseñadores y los desarrolladores puedan crear y presentar contenido imitando el funcionamiento de estas señales en el mundo real.

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frameholographic-framemd"></a>[Considerar cómo ve el mundo el usuario (trama holográfica)](holographic-frame.md)
Los usuarios ven el mundo de la realidad mixta a través de una ventanilla rectangular que funciona con el casco. En el dispositivo HoloLens, esta área rectangular se denomina trama holográfica y permite a los usuarios ver contenido digital superpuesto en el mundo real que les rodea.

<br>

### <a name="making-holographic-objects-feel-real---spatial-mappingspatial-mappingmd"></a>[Hacer que objetos holográficos parezcan reales (asignación espacial)](spatial-mapping.md)
La asignación espacial permite colocar objetos en superficies reales. Esto ayuda a anclar objetos en el mundo del usuario y aprovechar las indicaciones de profundidad del mundo real.

<br>

### <a name="suggesting-the-scale-of-an-object---scalescalemd"></a>[Sugerir la escala de un objeto (escala)](scale.md)
Una clave para mostrar contenido que parezca real en forma de holograma es imitar las estadísticas visuales del mundo real de la manera más semejante posible. Esto implica incorporar tantas indicaciones visuales como sea posible, que nos ayudarán (en el mundo real) a entender dónde se encuentran los objetos, cuál es su tamaño y de qué material están hechos.

<br>

### <a name="clear-and-readable-typographytypographymd"></a>[Tipografía clara y legible](typography.md)
Al igual que la tipografía en las pantallas 2D, el objetivo es que sea clara y legible. Con el aspecto tridimensional de la realidad mixta, existe la posibilidad de que el impacto sea aún mayor para el texto y la experiencia general del usuario.

<br>

### <a name="color-light-and-materialscolor-light-and-materialsmd"></a>[Color, luz y materiales](color,-light-and-materials.md)
El diseño de contenido para la realidad mixta requiere considerar con cautela el color, la iluminación y los materiales de cada uno de los recursos visuales que se usan en tu experiencia.


<br>

---



![Factores de diseño de la interacción](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>Factores de diseño de la interacción a tener en cuenta


### <a name="expanding-the-design-process-for-mixed-realitycase-study-expanding-the-design-process-for-mixed-realitymd"></a>[Expansión del proceso de diseño para la realidad mixta](case-study-expanding-the-design-process-for-mixed-reality.md)
Cuando Microsoft lanzó el dispositivo HoloLens para un público de desarrolladores ansiosos en 2016, el equipo ya se había asociado con estudios dentro y fuera de Microsoft para crear las experiencias de lanzamiento del dispositivo. Estos equipos aprendieron con la práctica y la búsqueda de oportunidades y retos en el nuevo campo del diseño de realidad mixta.

<br>

### <a name="types-of-mixed-reality-appstypes-of-mixed-reality-appsmd"></a>[Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md)
Una de las ventajas de desarrollar aplicaciones para Windows Mixed Reality es el amplio espectro de experiencias que la plataforma puede admitir. Desde entornos virtuales totalmente envolventes hasta la disposición en capas de información de iluminación en el entorno actual de un usuario, Windows Mixed Reality proporciona un sólido conjunto de herramientas para convertir cualquier experiencia en realidad.

<br>

### <a name="choose-an-interaction-model-for-your-customerinteraction-fundamentalsmd"></a>[Elección de un modelo de interacción para los clientes](interaction-fundamentals.md)
La filosofía de interacciones simples e instintivas está integrada en la plataforma Microsoft Mixed Reality. Hemos dado tres pasos para garantizar que los desarrolladores y diseñadores de aplicaciones puedan proporcionar interacciones sencillas e intuitivas a sus clientes.

<br>

### <a name="hands-and-motion-controllershands-and-toolsmd"></a>[Controladores de movimiento y manos](hands-and-tools.md)
Al igual que la tipografía en las pantallas 2D, el objetivo es que sea clara y legible. Con el aspecto tridimensional de la realidad mixta, existe la posibilidad de que el impacto sea aún mayor para el texto y la experiencia general del usuario.

<br>

### <a name="voice-commandingvoice-designmd"></a>[Comandos de voz](voice-design.md)
Al utilizar los comandos de voz, la mirada se utiliza normalmente como un mecanismo selector de destino, ya sea como un puntero ("seleccionar") o para dirigir un comando a una aplicación ("verlo, decirlo").

<br>

### <a name="leveraging-the-users-eye-gazeeye-trackingmd"></a>[Uso de la mirada del usuario](eye-tracking.md)
HoloLens 2 ofrece un nuevo nivel de conocimiento del contexto y del comportamiento humano dentro de la experiencia holográfica al proporcionar a los desarrolladores la capacidad de usar información sobre lo que están mirando los usuarios.


<br>


---

## <a name="choose-a-prototyping-option"></a>Elección de una opción de creación de prototipos  





:::row:::
    :::column:::
        <img alt="Unity Logo" width="70" height="70" src="images/unity_logo.png">
         <a href="https://learn.unity.com/" target="">Learn Unity</a>
        Learn how to create interactive experiences with Unity
    :::column-end:::
        :::column:::
       <img alt="MRTK Logo" width="70" height="70" src="images/MRTK_Logo_Sq_Text.png">
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="">Kit de herramientas de Mixed Reality</a> Gracias a la interacción espacial del kit de herramientas de Mixed Reality con los bloques de creación de la interfaz de usuario, puede empezar a diseñar y desarrollar realidad mixta con Unity.
    :::column-end:::
    :::column:::
        <img alt="MRDL Logo" width="70" height="70" src="images/MRDL_Logo_Sq_Text.png">
         <a href="https://github.com/Microsoft/MRDL_Unity_PeriodicTable" target="">Mixed Reality Design Labs</a>
        Mixed Reality Design Lab's sample apps shows how to use MRTK's building blocks to create beautiful mixed reality experiences.
    :::column-end:::
    :::column:::
        <img alt="Maquette Logo" width="70" height="70" src="images/MicrosoftMaquette_logo_glow.png">
         <a href="https://www.maquette.ms/" target="">Microsoft Maquette</a>
        Design for VR. Microsoft Maquette makes spatial prototyping easy, quick, and immersive.
    :::column-end:::
:::row-end:::


<br>

---



## <a name="what-would-you-like-to-do-next"></a>¿Qué quieres hacer ahora?


:::row:::
    :::column:::
       ![Comprender los conceptos básicos](images/icon-lightbulb.jpg)
        ### [Understand the basics](index-hidden.md)
        Get a better understanding of what defines mixed reality and how it’s being used.
    :::column-end:::
    :::column:::
        ![Install the tools](images/icon-design.jpg)
         ### [Install the tools](install-the-tools.md)
        Use the installation checklist to get the tools you need to build applications for Microsoft HoloLens and Windows Mixed Reality.
    :::column-end:::
    :::column:::
        ![Come to an event](images/icon-calendar.jpg)
         ### [Come to an event](sf-academy-events.md)
        See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.
    :::column-end:::
    :::column:::
        ![Start developing](images/icon-developer.jpg)
         ### [Start developing](development-hidden.md)
        Choose a development path based on your skill level, work style. or platform interest.
    :::column-end:::
:::row-end:::



