---
title: Acerca de esta guía de diseño
description: Microsoft ha creado esta guía para diseñadores, desarrolladores, administradores de programas e investigadores, cuyo trabajo abarca dispositivos holográficos (por ejemplo, HoloLens) y envolventes (por ejemplo, los cascos Windows Mixed Reality de Acer y HP).
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, introducción, instrucciones
ms.openlocfilehash: 6173f7cd2bcc4280f86f8f5ecaae1e90e01b62a0
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326124"
---
# <a name="about-this-design-guidance"></a>Acerca de esta guía de diseño

## <a name="introduction"></a>Introducción

**Hola y bienvenida a la Guía de diseño de realidad mixta.**

Esta guía es creada por Microsoft diseñadores, desarrolladores, administradores de programas y los investigadores, cuyo trabajo abarca holográficas dispositivos, como HoloLens y envolventes dispositivos, como los auriculares Acer y HP Windows Mixed Reality. Considere la posibilidad de este trabajo como un conjunto de temas sobre cómo diseñar para las pantallas de Windows montada head.

Con usted, estamos entrando en una nueva era muy emocionante de la informática. Avances en muestra montada head, espacial sonido, sensores, concienciación medioambiental, entrados y gráficos en 3D guiarnos y lo desafiamos a nosotros, para definir nuevos tipos de experiencias--frontera nuevo considerablemente más personal, intuitiva, envolvente y contextual.

Siempre que sea posible, le ofreceremos instrucciones de diseño que requieren acción con el código relacionado en GitHub. Dicho esto, ya que nos estamos aprendizaje derecha con usted, no siempre podremos ofrecer específico, que requieren acción aquí. Algunos de lo que compartimos estará siguiendo el espíritu de 'lecciones que aprendimos' y 'evitar bajando esa ruta de acceso'.

Y lo sabemos, se generarán muchas innovaciones en la comunidad general de diseño. Por lo tanto, esperamos trabajar estrechamente con usted, aprendizaje del usuario y comunicarse con nosotros. Por nuestra parte, haremos todo lo posible para compartir la información, incluso si son exploratorias y anticipada con la intención de permitiendo a los desarrolladores y diseñadores con ideas de diseño, los procedimientos recomendados y los controles relacionados de código abierto, patrones y aplicaciones de ejemplo que puede usar directamente en su propio trabajo.

## <a name="overview"></a>Información general

Le presentamos una introducción rápida de cómo se organiza esta guía de diseño. Encontrará las secciones para cada una de estas áreas con vínculos a varios artículos.
* **[Empezar a trabajar con diseño](mixed-reality.md)**  : lea nuestras ideas de alto nivel y comprender los principios se siguen.
* **[Interacciones instinctual](interaction-fundamentals.md)**  -Obtenga información sobre la entrada, los comandos, navegación y otros conceptos básicos de interacción para diseñar sus aplicaciones.
* **[Estilo](typography.md)**  -hacer que la aplicación agradable con color, movimiento y tipografía.
* **[Patrones de aplicaciones](types-of-mixed-reality-apps.md)**  -Obtenga información sobre cómo app; ications pueden abarcar escenarios en entornos reales y envolventes.
* **[Controles](interactable-object.md)**  -usar controles y patrones como bloques de creación para crear su propia experiencia de aplicación.
* **[Aplicaciones de ejemplo](design.md#sample-apps)**  -crear experiencias inmejorables en ejemplos diseñado y creado por nuestro equipo.
* **[Herramientas y recursos de diseño](design.md#design-tools)**  -ponga en marcha su proyecto con las herramientas y plantillas de diseño.

Para todos los mencionados anteriormente, nuestro objetivo es entregar la combinación correcta de texto, ilustraciones y los diagramas y vídeos, por lo que verá nos experimentar con distintos formatos y técnicas, todo ello con la intención de proporcionar lo que necesitan. Y en los próximos meses, ampliaremos esta taxonomía para incluir un conjunto más amplio de temas de diseño. Siempre que sea posible, que le ofreceremos un aviso sobre las próximas novedades, por tanto, tenga que comprobar de nuevo.

## <a name="objectives"></a>Objetivos

Este es un vistazo a algunos objetivos de alto nivel que se indicará este trabajo para que pueda comprender dónde que regresamos de

### <a name="help-solve-customer-challenges"></a>Ayudar a resolver los desafíos del cliente

![Ayudar a resolver los desafíos del cliente](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Se aprendieron con muchos de los mismos problemas que hacer, y somos conscientes es cómo un desafío de su trabajo. Es emocionante explorar y definir una frontera nuevo... y también puede resultar desalentadora. Procedimientos recomendados y paradigmas antiguos que se vuelva a considerar; los clientes necesitan nuevas experiencias; y hay muchas posibles para la innovación. Dado que queremos que este trabajo sea tan completa como bien posibles, moverse más allá de una guía de estilo. Nuestro objetivo es entregar un conjunto completo de la Guía de diseño que cubre mixto de interacción de la realidad, los comandos, navegación, entrada y el estilo: todos se basa en los escenarios y comportamiento humano. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Señalar el camino hacia una forma novedosa y más humano de la informática

![Señalar el camino hacia una forma novedosa y más humano de la informática](images/500px-man-and-women-with-holograph-on-table.png)<br>

Si bien es importante centrarse en los problemas del cliente específico, también queremos insertar nosotros mismos pensar más allá de eso y para ofrecer más. Creemos un diseño excelente no es "solo" solución de problemas, sino una manera de activar significativamente evolución humana. Nuevas formas de comportamiento humano; nuevas formas de personas relacionadas con, sus actividades y sus entornos; nuevas formas de ver nuestro mundo... Queremos que nuestra orientación para reflejar todas estas formas más ambiciosos de pensamiento demasiado. 

### <a name="meet-creators-where-they-are"></a>Cumplir con los creadores de dónde estén

![Cumplir con los creadores de dónde estén](images/500px-creators.jpg) <br>

Esperamos más audiencias esta guía sea útil. Tiene diferentes habilidades (a partir de, intermedio, avanzado), use herramientas diferentes (Unity, DirectX, C++, C#, otros), están familiarizados con diversas plataformas (Windows, iOS, Android), proceden de distintos fondos (mobile, enterprise, juegos ) y estamos trabajando en los equipos de diferente tamaño (solo, pequeño, mediano, grande). Por lo tanto, esta guía puede verse con necesidades y perspectivas diferentes. Siempre que sea posible, intentamos mantener esta diversidad en mente, y hacer que nuestra orientación relevantes tanto como sea posible a tantas personas como sea posible. Además, sabemos que muchos de ustedes ya están en GitHub. Por lo tanto, directamente se vinculará a repositorios de GitHub y foros de conocerte donde ya están. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Compartir tanto como sea posible, de experimental a explícita

![Compartir tanto como sea posible, de experimental a explícita](images/500px-man-playinggame.jpg) <br>

Uno de los desafíos de la oferta de instrucciones de diseño de este medio nuevo 3D es que no siempre tenemos una guía definitiva para ofrecer. Como usted, nos estamos de aprendizaje, experimentación, creación de prototipos, solución de problemas y el ajuste y ya que alcanzamos obstáculos. En lugar de esperar a que algunos momento futuro mítico cuando tengamos que imaginado, queremos compartir nuestro Pensamiento con usted en tiempo real, incluso si no es concluyente. Por supuesto, nuestro objetivo final es ser definitivos, dondequiera que se puede, clear, proporcionar un diseño flexible orientación asociada al código abierto y que requieren acción en las herramientas de diseño y desarrollo de Microsoft. Pero llegar a ese punto de toma de muchas rondas de iteración y el aprendizaje. Queremos ponerse en contacto con usted y Aprenda con usted, en el camino. Con todo esto en mente, haremos todo lo posible para compartir a medida que avancemos, incluso con nuestro material que es experimental. 

### <a name="the-right-balance-of-global-and-local-design"></a>El equilibrio adecuado entre diseño global y local

![El equilibrio adecuado entre diseño global y local](images/500px-fluentdesign.jpg) <br>

Ofrecemos dos niveles de la Guía de diseño: globales y locales. Nuestra guía de diseño 'global' se expresa en el [sistema de diseño Fluent](http://fluent.microsoft.com). Detalles de Fluent lo que pensamos sobre conceptos básicos, como la luz, profundidad, movimiento, material y escala a través de todo el diseño de Microsoft, nuestros dispositivos, productos, herramientas y servicios. Es decir, existen diferencias significativas de específico del dispositivo a través de este sistema de mayor tamaño. Por lo tanto, nuestra guía de diseño 'local' para las pantallas montada head describen el diseño para dispositivos holográficas y envolventes que a menudo tener otra entrada y salida de métodos, así como las necesidades de usuario diferente y escenarios. Guía de diseño local abarca temas HMDs exclusivos. Por ejemplo: Entornos 3D y los objetos; entornos compartidos; el uso de sensores, seguimiento de ojo y asignación espacial; y las oportunidades de audio espacial. En nuestra guía probablemente verá nos hacen referencia a estas globales y los aspectos locales. Espero que esto le ayudará en una base más grande del diseño de fondo de su trabajo mientras se aprovecha de las diferencias de diseño entre dispositivos específicos.

### <a name="have-a-discussion"></a>Tiene una discusión

![Tiene una discusión](images/500px-share.jpg) <br>

Lo más importante, quizás desee ponerse en contacto con usted, la Comunidad de programadores y diseñadores holográficas y envolventes para definir esta fascinante era de diseño. Como se mencionó anteriormente, sabemos que no tenemos todas las respuestas. Que por ¿por qué creemos muchas soluciones interesantes e innovaciones procederán de usted. Nuestro objetivo es estar abierta y disponible para escuchar sobre ellos y analizar con usted en línea y en los eventos y agregar valor siempre que sea posible. Nos complace formar parte de este sorprendentes Comunidad de diseño, embarcarse en una aventura juntos. 

## <a name="please-dive-in"></a>Sumérjase.

Esperamos que este artículo introductorio proporciona algún contexto significativo como explorar nuestra guía de diseño. Por favor, profundizar y háganos saber sus opiniones en los foros de GitHub, encontrará vinculados en nuestros artículos, o en Microsoft Design en [Twitter](https://twitter.com/MicrosoftDesign) y [Facebook](https://www.facebook.com/microsoftdesign/). Vamos a compartir diseña el futuro juntos.
