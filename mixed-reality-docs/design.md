---
layout: LandingPage
title: Empezar a diseñar y a crear prototipos
description: Si estás listo para crear, aprende los conceptos básicos que necesitas para empezar a diseñar y a crear prototipos.
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realidad mixta, detectar, distribuir, índice, página de aterrizaje, diseño, desarrollo, tutoriales, aplicaciones de ejemplo, aspectos básicos, casos prácticos, recursos, procedimientos de HoloLens, proyectos de código abierto, conceptos principales, interacción
ms.openlocfilehash: 708a6f83c2de149be9c221130b83f5d787f8f56a
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447921"
---
# <a name="start-designing-and-prototyping"></a>Empezar a diseñar y a crear prototipos


![resumen de diseño de realidad mixta](images/03_Design.png)

## <a name="expand-your-design-process"></a>[Ampliar el proceso de diseño](case-study-expanding-the-design-process-for-mixed-reality.md)

Cuando Microsoft lanzó el dispositivo HoloLens para un público de desarrolladores ansiosos en 2016, el equipo ya se había asociado con estudios dentro y fuera de Microsoft para crear las experiencias de lanzamiento del dispositivo. Estos equipos aprendieron con la práctica y la búsqueda de oportunidades y retos en el nuevo campo del diseño de realidad mixta. [Leer más](case-study-expanding-the-design-process-for-mixed-reality.md)

<br>

---

## <a name="what-are-the-core-concepts-of-an-experience"></a>¿Cuáles son los conceptos básicos de una experiencia?

### <a name="keep-the-user-comfortable---comfort"></a>[Preservar la comodidad del usuario (confort)](comfort.md)
Para garantizar la máxima comodidad de los cascos de realidad virtual, es importante que los diseñadores y los desarrolladores puedan crear y presentar contenido imitando el funcionamiento de estas señales en el mundo real.

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frame"></a>[Considerar cómo ve el mundo el usuario (trama holográfica)](holographic-frame.md)
Los usuarios ven el mundo de la realidad mixta a través de una ventanilla rectangular que funciona con el casco. En el dispositivo HoloLens, esta área rectangular se denomina trama holográfica y permite a los usuarios ver contenido digital superpuesto en el mundo real que les rodea.

<br>

### <a name="types-of-mixed-reality-apps"></a>[Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md)
Una de las ventajas de desarrollar aplicaciones para realidad mixta es el amplio espectro de experiencias que la plataforma puede admitir. Desde entornos virtuales totalmente envolventes hasta la disposición en capas de información de iluminación en el entorno actual de un usuario, la realidad mixta proporciona un sólido conjunto de herramientas para convertir cualquier experiencia en realidad.

<br>

### <a name="keeping-holograms-in-place---coordinate-systems"></a>[Mantener los hologramas en su lugar (sistemas de coordenadas)](coordinate-systems.md)
En esencia, las aplicaciones de realidad mixta colocan hologramas en tu mundo para que parezcan y suenen como objetos reales. Esto implica el posicionamiento preciso de los hologramas en lugares del mundo que son significativos para el usuario, ya sea su espacio físico o un dominio virtual que hayas creado.

<br>

### <a name="making-holographic-objects-feel-real---spatial-mapping"></a>[Hacer que objetos holográficos parezcan reales (asignación espacial)](spatial-mapping.md)
La asignación espacial permite colocar objetos en superficies reales. Esto ayuda a anclar objetos en el mundo del usuario y aprovechar las indicaciones de profundidad del mundo real.

<br>


---

<br>

![Factores de diseño de la interacción](images/UX/UX_Hero_Manipulation.jpg)

## <a name="interaction-design-factors-to-consider"></a>Factores de diseño de la interacción a tener en cuenta


### <a name="choose-an-interaction-model-for-your-customer"></a>[Elección de un modelo de interacción para los clientes](interaction-fundamentals.md)
La filosofía de interacciones simples e instintivas está integrada en la plataforma Microsoft Mixed Reality. Hemos dado tres pasos para garantizar que los desarrolladores y diseñadores de aplicaciones puedan proporcionar interacciones sencillas e intuitivas a sus clientes.

<br>

### <a name="hands-and-motion-controllers"></a>[Controladores de movimiento y manos](hands-and-tools.md)
Los usuarios pueden tocar y manipular los hologramas directamente con una o ambas manos, de forma muy similar que con los objetos del mundo real. O bien, con controladores de movimiento, puedes ampliar las capacidades físicas del usuario proporcionando interacciones precisas en una gran variedad de distancias.

<br>

### <a name="directly-commanding-objects-with-voice-input"></a>[Emisión directa de comandos a los objetos con entrada de voz](voice-input.md)
La voz es una de las formas clave de entrada en HoloLens. Te permite emitir directamente comandos a un holograma sin tener que usar gestos. La entrada de voz es una manera natural de comunicar tus intenciones.

<br>

### <a name="leveraging-the-users-eye-gaze"></a>[Uso de la mirada del usuario](eye-tracking.md)
HoloLens 2 ofrece un nuevo nivel de conocimiento del contexto y del comportamiento humano dentro de la experiencia holográfica al proporcionar a los desarrolladores la capacidad de usar información sobre lo que están mirando los usuarios.

<br>


---

<br>


![Elementos de la experiencia del usuario](images/UX/UX_Hero_BoundingBox.jpg)

## <a name="user-experience-elements-for-mixed-reality"></a>Elementos de la experiencia del usuario para realidad mixta


### <a name="color-light-and-materials"></a>[Color, luz y materiales](color,-light-and-materials.md)
El diseño de contenido para la realidad mixta requiere considerar con cautela el color, la iluminación y los materiales de cada uno de los recursos visuales que se usan en tu experiencia.

<br>

### <a name="suggesting-the-scale-of-an-object"></a>[Sugerir la escala de un objeto](scale.md)
Una clave para que el contenido visualizado parezca real en forma de holograma es imitar las características visuales del mundo real de la manera más parecida posible. Esto implica incorporar tantas indicaciones visuales como sea posible, que nos ayudarán (en el mundo real) a entender dónde se encuentran los objetos, cuál es su tamaño y de qué material están hechos.

<br>

### <a name="clear-and-readable-typography"></a>[Tipografía clara y legible](typography.md)
Al igual que la tipografía en las pantallas 2D, el objetivo es que sea clara y legible. Con el aspecto tridimensional de la realidad mixta, existe la posibilidad de que el impacto sea aún mayor para el texto y la experiencia general del usuario.

<br>

### <a name="common-controls-and-behaviors"></a>[Controles y comportamientos comunes](app-patterns-landingpage.md)
Obtenga información sobre las interacciones espaciales y los bloques de compilación de la interfaz de usuario comunes que se usan con frecuencia para las experiencias de realidad mixta.



<br>


---

## <a name="choose-a-prototyping-option"></a>Elección de una opción de creación de prototipos  

:::row:::   
    :::column:::    
       [![Información sobre Unity](images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[Información sobre Unity](https://learn.unity.com/)**<br>
        Aprende a crear experiencias interactivas con Unity. Aprende con la práctica, de principio a fin.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality Toolkit (MRTK)](images/Final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        Con la interacción espacial y los bloques de creación de la interfaz de usuario, pon en marcha el diseño y desarrollo de la realidad mixta con Unity.   
    :::column-end:::
    :::column:::    
        [![Laboratorios de diseño de realidad mixta](images/Final_mrdl_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        Obtén aplicaciones de ejemplo que te muestren cómo usar los bloques de creación de MRTK para crear experiencias de realidad mixta.
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/Final_maquette_logo.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        Diseño para VR. Microsoft Maquette hace que la creación de prototipos espaciales sea fácil, rápida y envolvente. 
    :::column-end:::    
:::row-end:::

<br>

---



## <a name="what-would-you-like-to-do-next"></a>¿Qué quieres hacer ahora?

:::row:::
    :::column:::
       [![Comprender los conceptos básicos](images/icon-lightbulb.png)](get-started-with-mr.md#understand-the-basics)<br>
        **[Comprender los conceptos básicos](get-started-with-mr.md#understand-the-basics)**<br>
        Obtén una mejor comprensión de lo que define la realidad mixta y cómo se usa.
    :::column-end:::
    :::column:::
        [![Asistir a un evento](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[Asistir a un evento](sf-academy-events.md)**<br>
        Observa el hardware y obtén un tutorial práctico para crear tu primera aplicación de HoloLens 2.
    :::column-end:::
    :::column:::
        [![Instalar las herramientas](images/icon-design.jpg)](install-the-tools.md)<br>
         **[Instalar las herramientas](install-the-tools.md)**<br>
        Usa la lista de comprobación de instalación para obtener las herramientas que necesitas para crear aplicaciones para HoloLens y realidad mixta.
    :::column-end:::
    :::column:::
        [![Empezar a desarrollar](images/icon-developer.jpg)](development.md)<br>
        **[Empezar a desarrollar](development.md)**<br>
        Elige un método de desarrollo en función de tu nivel de aptitud, estilo de trabajo o preferencia de plataforma.
    :::column-end:::
:::row-end:::


<br>

<br>


