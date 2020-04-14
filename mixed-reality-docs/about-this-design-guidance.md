---
title: Acerca de esta guía de diseño
description: Microsoft ha creado esta guía para diseñadores, desarrolladores, administradores de programas e investigadores, cuyo trabajo abarca dispositivos holográficos (por ejemplo, HoloLens) y envolventes (por ejemplo, los cascos Windows Mixed Reality de Acer y HP).
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, introducción, guía
ms.openlocfilehash: 114a3808d57b2bd78044ce743d568bd5effe25bb
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277523"
---
# <a name="about-this-design-guidance"></a>Acerca de esta guía de diseño

## <a name="introduction"></a>Introducción

**Hola y le agradecemos su guía de diseño para la realidad mixta.**

Esta guía la crean los diseñadores de Microsoft, desarrolladores, administradores de programas e investigadores, cuyo trabajo abarca dispositivos holográficas, como HoloLens y dispositivos envolventes, como Acer y HP Windows con auriculares de realidad mixta. Tenga en cuenta este trabajo como un conjunto de temas sobre cómo diseñar pantallas montadas por el cabezal de Windows.

Con usted, estamos introduciendo una nueva era enormemente emocionante de informática. Los avances en las pantallas montadas por el cabezal, el sonido espacial, los sensores, el reconocimiento medioambiental, la entrada y los gráficos 3D nos conducen y desafiamos para definir nuevos tipos de experiencias: una nueva frontera es mucho más personal, intuitiva, envolvente y contextual.

Siempre que sea posible, ofreceremos orientación de diseño accionable con código relacionado en GitHub. Dicho esto, como estamos aprendiendo directamente con usted, no siempre podremos ofrecer instrucciones específicas y accionables aquí. Algunos de los elementos que compartimos estarán en el espíritu de las ' lecciones que hemos aprendido ' y ' no vamos a bajar ese camino '.

Y sabemos que muchas innovaciones se generarán en la comunidad de diseño de mayor tamaño. Por lo tanto, esperamos tener noticias suyas, aprender de usted y trabajar en estrecha colaboración con usted. En nuestro caso, haremos todo lo posible para compartir la información, incluso si son exploratorios y pronto con el objetivo de permitir a los desarrolladores y diseñadores el diseño del diseño, los procedimientos recomendados y los controles de código abierto, patrones y aplicaciones de ejemplo relacionados que puede usar directamente en su propio trabajo.

## <a name="overview"></a>Información general

A continuación se muestra una introducción rápida de cómo se organiza esta guía de diseño. 
* **[Información general](design.md)** : Obtenga información sobre el proceso de diseño, los conceptos básicos y los factores de interacción que se deben tener en cuenta.
* **[Conceptos básicos](core-concepts-landingpage.md)** : Obtenga información sobre la comodidad, el marco holográfica, la asignación espacial y otros conceptos básicos a tener en cuenta.
* **[Modelos de interacción](interaction-fundamentals.md)** : esta guía está estructurada en torno a tres modelos de interacción principales.
* **[Elementos](app-patterns-landingpage.md)** de la experiencia de usuario: Use controles y comportamientos como bloques de creación para crear su propia experiencia de la aplicación.
* **[Recursos](design.md#choose-a-prototyping-option)** : inicie el proyecto con las herramientas de diseño y las opciones de prototipo.

Para todo lo anterior, nos esforzamos por ofrecer la combinación correcta de texto, ilustraciones y diagramas, y vídeos, por lo que nos vemos experimentando con distintos formatos y técnicas, todo ello con la intención de ofrecer lo que necesita. Y, en los próximos meses, ampliaremos esta taxonomía para incluir un conjunto más amplio de temas de diseño. Siempre que sea posible, le daremos un aviso sobre lo que va a continuación, por lo que debe volver a realizar la comprobación.

## <a name="objectives"></a>Objetivos

A continuación se muestra una visión rápida de algunos objetivos de alto nivel que son la guía de este trabajo para que pueda comprender desde dónde proviene

### <a name="help-solve-customer-challenges"></a>Ayudar a resolver los desafíos del cliente

![Ayudar a resolver los desafíos del cliente](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Nos Wrestle con muchos de los mismos problemas que usted hace, y sabemos cómo es desafiante su trabajo. Es emocionante explorar y definir una nueva frontera... también puede ser desalentadora. Es necesario volver a pensar en los paradigmas y prácticas anteriores; los clientes necesitan nuevas experiencias; y hay muchas posibilidades de innovación. Dado que deseamos que este trabajo sea lo más completo posible, puede ir más allá de una guía de estilo. Nos esforzamos por ofrecer un conjunto completo de instrucciones de diseño que cubra la interacción con la realidad mixta, los comandos, la navegación, la entrada y el estilo, todo ello en escenarios y comportamientos humanos. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Apuntar a una forma nueva y más humana de calcular

![Apuntar a una forma nueva y más humana de calcular](images/500px-man-and-women-with-holograph-on-table.png)<br>

Aunque es importante centrarse en problemas específicos del cliente, también queremos inserciones para pensar más allá y ofrecer más. Creemos que un diseño excelente no es "simplemente" resolver problemas, sino también una manera de activar de forma significativa la evolución humana. Nuevas formas de comportamiento humano; nuevas formas de personas relacionadas con ellos mismos, sus actividades y sus entornos; nuevas formas de ver nuestro mundo... queremos que nuestras instrucciones reflejen también todas estas formas de pensar. 

### <a name="meet-creators-where-they-are"></a>Conozca a los creadores donde están

![Conozca a los creadores donde están](images/500px-creators.jpg) <br>

Esperamos que muchas audiencias encuentren esta guía para ser útiles. Tiene diferentes conjuntos de aptitudes (principiantes, intermedios, avanzados), usan diferentes herramientas (Unity C++, C#DirectX,, etc.), están familiarizados con las distintas plataformas (Windows, iOS y Android), proceden de distintos niveles (móviles, empresariales, juegos) y están trabajando en equipos de tamaño diferente (solo, pequeño, mediano y grande). Por lo tanto, esta guía se puede ver con diferentes perspectivas y necesidades. Siempre que sea posible, intentaremos tener en cuenta esta diversidad y haremos lo que sea más importante como sea posible a tantas personas como sea posible. Además, sabemos que muchos de los ya están en GitHub. Por lo tanto, se vincularán directamente a los foros y repositorioss de GitHub para que se le satisfagan donde ya está. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Comparta todo lo posible, desde experimental hasta explícito

![Comparta todo lo posible, desde experimental hasta explícito](images/500px-man-playinggame.jpg) <br>

Uno de los desafíos de ofrecer instrucciones de diseño en este nuevo medio 3D es que no siempre tenemos instrucciones definitivas para ofrecer. Del mismo modo, estamos aprendiendo, experimentando, prototipo, resolviendo problemas y ajustando a medida que se alcanzan los obstáculos. En lugar de esperar a un momento futuro en el que se haya descubierto todo, nos esforzaremos por compartir nuestro pensamiento en tiempo real, incluso si no es concluyente. Por supuesto, nuestro objetivo final es ser definitivo siempre que podamos, proporcionar una guía de diseño flexible y clara relacionada con el código de código abierto y accionable en herramientas de desarrollo y diseño de Microsoft. Pero llegar a ese punto conlleva muchos ciclos de iteración y aprendizaje. Queremos colaborar con usted y aprender con usted a lo largo del proceso. Teniendo todo esto en mente, haremos todo lo posible para compartir a medida que avanzamos, incluso con nuestro material experimental. 

### <a name="the-right-balance-of-global-and-local-design"></a>El equilibrio derecho del diseño global y local

![El equilibrio derecho del diseño global y local](images/500px-fluentdesign.jpg) <br>

Ofreceremos dos niveles de orientación de diseño: global y local. Nuestra guía de diseño "global" se incorpora en el [sistema de diseño fluida](https://fluent.microsoft.com). Información fluida sobre aspectos básicos como la luz, la profundidad, el movimiento, el material y la escala en todo el diseño de Microsoft, nuestros dispositivos, productos, herramientas y servicios. Dicho esto, existen importantes diferencias específicas del dispositivo en este sistema más grande. Por lo tanto, nuestra guía de diseño "local" para las pantallas montadas por el cabezal describe el diseño de dispositivos holográficas y envolventes que suelen tener distintos métodos de entrada y salida, así como diferentes necesidades y escenarios de usuario. La guía de diseño local trata los temas exclusivos de HMDs. Por ejemplo: entornos y objetos 3D; entornos compartidos; el uso de sensores, seguimiento ocular y asignación espacial; y las oportunidades de audio espacial. A lo largo de nuestras instrucciones, probablemente nos referiremos a ambos aspectos globales y locales. Espero que esto le ayude a realizar su trabajo en una base más grande del diseño mientras aprovecha las diferencias de diseño entre dispositivos específicos.

### <a name="have-a-discussion"></a>Tener una discusión

![Tener una discusión](images/500px-share.jpg) <br>

Quizás lo más importante es que quieramos colaborar con usted, la comunidad de diseñadores y desarrolladores de Holographic y envolventes, para definir esta nueva era emocionante de diseño. Como se mencionó anteriormente, sabemos que no tenemos todas las respuestas. Esta es la razón por la que creemos que muchas interesantes soluciones e innovaciones provienen de usted. Nos esforzamos por estar abierto y disponible para recibir información sobre ellos, y hablaremos con usted en línea y en eventos, y agregaremos valor dondequiera que podamos. Nos complace formar parte de esta impresionante comunidad de diseño y embarcarnos en una aventura. 

## <a name="please-dive-in"></a>Profundice

Esperamos que este artículo introductorio proporcione un contexto significativo a medida que Explore nuestra guía de diseño. Profundice y díganos sus pensamientos en los foros de GitHub que encontrará vinculados en nuestros artículos o en Microsoft Design en [Twitter](https://twitter.com/MicrosoftDesign) y [Facebook](https://www.facebook.com/microsoftdesign/). Vamos a diseñar el futuro juntos.
