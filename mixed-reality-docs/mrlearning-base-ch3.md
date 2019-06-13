---
title: 'Módulo base de aprendizaje MR: Colocación de contenido dinámico y solucionadores'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270400"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>Módulo base de aprendizaje MR: Colocación de contenido dinámico y solucionadores

Los hologramas cobran vida en HoloLens 2 cuando intuitivamente siguen al usuario y se colocan en el entorno físico, de forma que la interacción resulta fluida y elegante. En la lección 3, exploraremos las distintas formas para colocar de forma dinámica hologramas mediante las herramientas de selección de ubicación disponibles de MRTK, conocidas como "solucionadores". Se las conocen como "solucionadores" por la forma en la que solucionan los algoritmos de ubicación espacial complejos. En MRTK, los solucionadores son un sistema de scripts y comportamientos que utilizamos para permitir que los elementos de interfaz de usuario te sigan a ti, al usuario o a otros objetos de juego en la escena. También pueden usarse para acoplarse rápidamente en ciertas posiciones, haciendo que la aplicación sea más intuitiva. 

## <a name="objectives"></a>Objetivos

* Introducir los solucionadores de MRTK
* Usa solucionadores para tener una colección de botones que sigan al usuario
* Usa solucionadores para tener un objeto de juego que siga las manos con seguimiento del usuario

## <a name="instructions"></a>Instrucciones

### <a name="location-of-solvers-in-the-mrtk"></a>Ubicación de los solucionadores en MRTK
 Para encontrar los solucionadores disponibles en el proyecto, busca en la carpeta MRTK SDK (carpeta MixedRealityToolkit.SDK), en la carpeta de utilidades verás la carpeta de solucionadores, como se muestra en la imagen siguiente.

![Solucionadores](images/lesson3_chapter1_step1im.PNG)

>Nota: En esta lección solo veremos la implementación de los solucionadores "Orbital" y "RadialView". Para más información sobre la gama completa de solucionadores disponibles en MRTK, visita: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Uso de un solucionador para seguir al usuario
El objetivo de este capítulo es mejorar la colección de botones que creamos anteriormente, de forma que sigua la dirección de la mirada del usuario. En la versión anterior de MRTK y HoloToolkit, esto se conocía como una funcionalidad de "taglong".

1. Selecciona el objeto primario de colección de botones de la lección anterior.

![Imagen de la lección 3, capítulo 2, paso 1](images/Lesson3_chapter2_step1im.PNG)

2. En el panel del inspector, haz clic en el botón "Add Component" (Agregar componente), y busca "Orbital". El componente orbital debería aparecer. Selecciónalo para agregar el componente orbital al objeto de juego Button Collection (Colección de botones).

![Imagen de la lección 3, capítulo 2, paso 2](images/Lesson3_Chapter2_step2im.PNG)

>Nota: Al agregar el componente observarás que el sistema agrega el script de orbital y el script controlador del solucionador en la pestaña del inspector, que es un componente necesario. 

3. Para configurar la colección de botones para seguir al usuario, tenemos que implementar los siguientes ajustes (consulta también la imagen siguiente):
- En el script Orbital, establece la lista desplegable "Orientation type" (Tipo de orientación) en "Yaw Only" (Solo rotación alrededor del eje). Con esto solo un eje del objeto gira mientras sigue al usuario.
- Establece Local Offset (Desplazamiento local) en 0 en todos los ejes. Establece World Offset (Desplazamiento del mundo) en x = 0, y = -0,1 y z = 0,6. Esto bloquea el movimiento del objeto de tal forma que cuando el usuario cambia la altura, el objeto permanecerá en una altura fija en el entorno físico, a la vez que se le sigue permitiendo que siga al usuario mientras este se mueve en el entorno. Estos valores se pueden ajustar para lograr una amplia variedad de comportamientos.
- Para un comportamiento de seguimiento mediante el cual los botones siguen únicamente la vista del usuario después de que el usuario vuelve la cabeza suficientemente, puedes seleccionar la casilla "Use Angle Stepping for world offset" (Usar el ángulo de ejecución paso a paso para el desplazamiento del mundo) (Nota: Este título puede aparecer truncado en algunas pantallas, como en la imagen a continuación). Por ejemplo, para que el objeto siga al usuario solo cada 90 grados, establece el número de pasos igual a 4 (marcados con una flecha verde en el ejemplo a la izquierda). 

![Imagen de la lección 3, capítulo 2, paso 3](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Habilitación de los objetos para que sigan a las manos con seguimiento

En esta sección, configuraremos el objeto de juego de cubo creado anteriormente para seguir a las manos con seguimiento del usuario mediante el solucionador RadialView.

1. Selecciona el objeto "Cube" (Cubo) en la jerarquía BaseScene. En el panel del inspector, haz clic en "Add Component" (Agregar componente). 

![Imagen de la lección 3, capítulo 3, paso 1](images/Lesson3_Chapter3_step1im.PNG)

2. Escribe "RadialView" en el cuadro de búsqueda y selecciona el componente RadialView para agregarlo al cubo. El componente de controlador del solucionador también se agregará automáticamente al cubo.

3. Cambia la vista radial para no seguir la cabeza y seguir a la mano izquierda. Selecciona el menú desplegable junto a la opción "Tracked Object To Reference" (Seguimiento de objeto para referencia). A continuación, selecciona "Hand Joint Left" (Articulación de la mano izquierda) en el menú.

![Imagen de la lección 3, capítulo 3, paso 3](images/Lesson3_chapter3_step3im.PNG)

4. Una vez que hayas selecciona la articulación de la mano, puedes elegir a qué parte de la mano quieres que siga el cubo. Para este ejemplo usaremos la muñeca. Junto a la opción "Tracked Hand Joint" (Articulación de la mano con seguimiento) selecciona el menú desplegable y en él la opción "Wrist" (Muñeca). 

![Imagen de la lección 3, capítulo 3, paso 4](images/Lesson3_chapter3_step4im.PNG)

5. Establece la distancia máxima y mínima en 0 para que no haya ningún distancia entre el cubo y la muñeca del usuario. Una vez establecido, el cubo se alinea perfectamente con la muñeca. También puedes ajustar el campo "Reference Direction" (Dirección de referencia) para ajustar el comportamiento de cómo se orienta el cubo. Por ejemplo, si quieres permitir que el objeto gire con la muñeca del usuario, establece la dirección de la referencia con el valor "Orient with Tracked Object" (Orientar con objeto de seguimiento)

![Imagen de la lección 3, capítulo 3, paso 5](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>Enhorabuena
Enhorabuena. En esta lección, has aprendido a usar los solucionadores de MRTK para tener una interfaz de usuario intuitiva que siga al usuario. También has aprendido cómo adjuntar un solucionador a un objeto de juego (es decir, el cubo) para seguir a las manos con seguimiento del usuario. Para más información sobre estos y otros solucionadores incluidos con MRTK, no dudes en visitar la [página de documentación de los solucionadores de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Próxima lección: Interacción de objetos 3D](mrlearning-base-ch4.md)

