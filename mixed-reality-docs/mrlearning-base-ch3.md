---
title: Módulo de la Base de aprendizaje de MR - selección de ubicación de contenido dinámico y los algoritmos de resolución
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: b212812beeff54bb1f92ccbcc923ab9c301945b7
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929557"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>Módulo de la Base de aprendizaje de MR - selección de ubicación de contenido dinámico y los algoritmos de resolución

Hologramas cobran vida en HoloLens 2 cuando intuitivamente seguir al usuario y se colocan en el entorno físico de una forma que resulte interacción fluida y elegante. En la lección 3, Investigaremos distintas formas para colocar de forma dinámica hologramas mediante herramientas de selección de ubicación disponibles del MRTK, conocidas como "algoritmos de resolución". Se conocen como algoritmos de "Resolución" para la forma en que solucionan los algoritmos de selección de ubicación espacial complejas. En el MRTK, los algoritmos de resolución son un sistema de secuencias de comandos y comportamientos que utilizamos para poder permitir que los elementos de interfaz de usuario siga usted, el usuario u otros objetos del juego en la escena. Puede también usarse para ajustar rápidamente, en ciertas posiciones pone la aplicación sea más intuitiva. 

## <a name="objectives"></a>Objetivos

* Introducir los algoritmos de resolución de MRTK
* Use algoritmos de resolución para tener una colección de botones seguir al usuario
* Use algoritmos de resolución para tener un objeto de juego siguen manos sometidas a seguimiento del usuario

## <a name="instructions"></a>Instrucciones

### <a name="location-of-solvers-in-the-mrtk"></a>Ubicación de los algoritmos de resolución en el MRTK
 Para encontrar los algoritmos de resolución disponibles en el proyecto, busque en la carpeta MRTK SDK (MixedRealityToolkit.SDK carpeta), a continuación, en la carpeta Utilidades verá la carpeta de herramientas de resolución, como se muestra en la imagen siguiente.

![Algoritmos de resolución](images/lesson3_chapter1_step1im.PNG)

>Nota: En esta lección solo se pasará a través de la implementación de solver "Orbital" y "RadialView" solver. Para obtener más información sobre la gama completa de los algoritmos de resolución disponibles en el MRTK, visite: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Utilizar un solucionador de seguir al usuario
El objetivo de este capítulo es mejorar la colección de botones que creamos anteriormente, que sigue la dirección de mirada del usuario. En la versión anterior del MRTK y HoloToolkit, esto se conoce como una funcionalidad de "taglong".

1. Seleccione el objeto primario de colección de botones de la lección anterior.

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. En el panel del inspector, haga clic en el botón "agregar el componente" y busque "orbitales." El componente orbital debería aparecer. Selecciónelo para agregar el componente orbital para el objeto de juego de la colección de botones.

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>Nota: Al agregar el componente observará que el sistema agrega el script orbital y el controlador solver en la pestaña inspector, que es un componente necesario. 

3. Para configurar la colección de botones para seguir el usuario, es necesario implementar los siguientes ajustes (consulte también la imagen siguiente):
- En el script Orbital, establezca la lista desplegable "tipo de orientación" a "Sólo guiñada." Esto hace que, por lo que solo un eje del objeto gira manera el usuario.
- Establece el desplazamiento local en 0 en todos los ejes. Establece el desplazamiento del mundo a x = 0, y = -0.1 y z = 0,6. Esto bloquea el movimiento del objeto tal que cuando el usuario cambia el alto, el objeto permanecerá en un alto fijo en el entorno físico, mientras sigue permitiendo que siguen al usuario cuando el usuario se mueve sobre el entorno. Estos valores se pueden ajustar para lograr una gama wade de comportamientos.
- Para un comportamiento de seguimiento mediante el cual los botones siguen únicamente la vista del usuario después de que el usuario activa su cabeza suficientemente, puede seleccionar la casilla "Use ángulo ejecución paso a paso para desplazamiento world" (tenga en cuenta: Este título puede aparecer truncado en algunas pantallas, como en la imagen siguiente.) Por ejemplo, para que el objeto siga el usuario sólo cada 90 grados, establecer igual a 4 (marcados con una flecha verde en el ejemplo a la izquierda) el número de pasos. 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Permitir a los objetos siguen las manos sometidas a seguimiento

En esta sección, configuramos el objeto de juego de cubo creado anteriormente para seguir manos sometidas a seguimiento del usuario mediante el solucionador RadialView.

1. Seleccione el objeto de cubo en la jerarquía BaseScene. Haga clic en "agregar el componente" en el panel del inspector. 

![Lesson3 capítulo 3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. Escriba "RadialView" en el cuadro de búsqueda y seleccione el componente RadialView para agregarlo al cubo. El componente de controlador solver también se agregará automáticamente al cubo.

3. Cambiar la vista radial para no seguir el encabezado, pero siga la mano izquierda. Seleccione el menú desplegable junto a la opción "realiza un seguimiento de objeto para hacer referencia a". A continuación, seleccione "pasar conjunta izquierda" en el menú.

![Lesson3 capítulo 3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. Una vez que selecciona la junta de la mano, puede elegir qué parte de la mano que desea que siga el cubo. En este ejemplo, vamos a usar la muñeca. Junto a la opción "mano sometidas a seguimiento junta" Seleccione el menú desplegable y seleccione la muñeca. 

![Lesson3 capítulo 3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. Establece la distancia máxima y mínima en 0 para que el cubo no tendrá ningún distancia entre ella y muñeca del usuario. Una vez establecido, el cubo se perfectamente alinea con la muñeca. También puede ajustar el campo "Dirección de referencia" para ajustar el comportamiento de cómo se orienta el cubo (por ejemplo, si desea permitir que el objeto gira con muñeca del usuario, establezca la dirección de la referencia a "Orientar con objeto de seguimiento")

![Lesson3 capítulo 3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>Enhorabuena
¡Enhorabuena! En esta lección, ha aprendido a usar los algoritmos de resolución del MRTK para tener una interfaz de usuario intuitiva seguir al usuario. También ha aprendido cómo conectar un solucionador de a un objeto de juego (es decir, el cubo) seguir manos sometidas a seguimiento del usuario. Para obtener más información sobre estas y otras herramientas de resolución de incluidos con el MRTK, no dude en visitar el [página de documentación de los algoritmos de resolución MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Próxima lección: Interacción de objetos 3D](mrlearning-base-ch4.md)

