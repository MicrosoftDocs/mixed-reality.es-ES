---
title: 'Tutoriales de introducción: 4. Colocar contenido dinámico y usar solucionadores'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 93fcdcdfb7941f377b2f3f7786368783415b1ef2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438406"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. colocar contenido dinámico y usar solucionadores

Los hologramas llegan a la vida en HoloLens 2 cuando siguen de forma intuitiva al usuario y se colocan en el entorno físico de una manera que hace que la interacción sea fluida y elegante. En este tutorial, se exploran las formas de colocar dinámicamente los hologramas mediante las herramientas de selección de ubicación disponibles de MRTK (conocidas como solucionadores) para resolver escenarios complejos de colocación espacial. En MRTK, los solucionadores son un sistema de scripts y comportamientos que se usan para permitir que los elementos de la interfaz de usuario sigan el usuario, el usuario u otros objetos de juego de la escena. También pueden usarse para acoplarse rápidamente en ciertas posiciones, haciendo que la aplicación sea más intuitiva. 

## <a name="objectives"></a>Objetivos

* Introducir los solucionadores de MRTK
* Usa solucionadores para tener una colección de botones que sigan al usuario
* Usa solucionadores para tener un objeto de juego que siga las manos con seguimiento del usuario

## <a name="instructions"></a>Instrucciones

### <a name="location-of-solvers-in-the-mrtk"></a>Ubicación de los solucionadores en MRTK
 Para encontrar los solucionadores disponibles en el proyecto, busque en la carpeta del SDK de MRTK (carpeta MixedRealityToolkit. SDK). En la carpeta Utilities, verá la carpeta Solves, tal como se muestra en la imagen siguiente.

![Solucionadores](images/lesson3_chapter1_step1im.PNG)

>Nota: en esta lección, solo revisaremos la implementación del Solver orbital y el RadialView Solver. Para obtener más información acerca de la gama completa de solucionadores disponibles en MRTK, visite: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>Uso de un solucionador para seguir al usuario
El objetivo de este capítulo es mejorar la colección de botones que se creó anteriormente para que siga la dirección del usuario. En la versión anterior de MRTK y HoloToolkit, esto se denominaba funcionalidad de tagalong.

1. Selecciona el objeto primario de colección de botones de la lección anterior.

![Imagen de la lección 3, capítulo 2, paso 1](images/Lesson3_chapter2_step1im.PNG)

2. En el panel Inspector, haga clic en el botón Agregar componente y busque orbital. Debe aparecer el componente orbital. Selecciónelo para agregar el componente orbital al objeto de juego de la colección de botones.

![Imagen de la lección 3, capítulo 2, paso 2](images/Lesson3_Chapter2_step2im.PNG)

>Nota: al agregar el componente orbital, observará que el sistema también agrega el componente SolverHandler, que es un componente necesario. 

3. Para configurar la colección de botones para que siga el usuario, es necesario implementar los siguientes ajustes (consulte la imagen siguiente):
- En el script orbital, establezca la lista desplegable tipo de orientación en guiñada solamente. Con esto solo un eje del objeto gira mientras sigue al usuario.
- Establece Local Offset (Desplazamiento local) en 0 en todos los ejes. Establezca el desplazamiento de mundo en x = 0, y =-0,1 y z = 0,6. Esto bloquea el movimiento del objeto para que cuando el usuario cambie el alto, el objeto permanezca en un alto fijo en el entorno físico, a la vez que sigue permitiendo que siga el usuario a medida que el usuario mueve el entorno. Estos valores se pueden ajustar para lograr una amplia variedad de comportamientos.
- Para un seguimiento del comportamiento mediante el cual los botones solo siguen la vista del usuario después de que el usuario haya desplazado el cabezal lo suficiente, puede activar la casilla usar la ejecución paso a paso para el desplazamiento del mundo (Nota: este título puede truncarse en algunas pantallas, como se muestra en la imagen siguiente). Por ejemplo, para que el objeto siga el usuario solo cada 90 grados, establezca el número de pasos igual a 4 (marcado con una flecha verde en el ejemplo siguiente). 

![Imagen de la lección 3, capítulo 2, paso 3](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>Habilitar objetos para seguir manos de seguimiento

En esta sección, configuraremos el objeto de juego de cubos que se creó anteriormente para seguir las manos de seguimiento del usuario mediante RadialView Solver.

1. Seleccione el objeto de cubo en la jerarquía de BaseScene. Haga clic en Agregar componente en el panel Inspector. 

![Imagen de la lección 3, capítulo 3, paso 1](images/Lesson3_Chapter3_step1im.PNG)

2. Escriba RadialView en el cuadro de búsqueda y seleccione el componente RadialView para agregarlo al cubo. El componente SolverHandler también se agregará automáticamente al cubo.

3. Para cambiar RadialView a fin de que siga la mano izquierda en lugar del encabezado, seleccione el menú desplegable situado junto a la opción objeto sometido a seguimiento en referencia y, a continuación, seleccione Unión a mano izquierda en el menú.

![Imagen de la lección 3, capítulo 3, paso 3](images/Lesson3_chapter3_step3im.PNG)

4. Una vez que hayas selecciona la articulación de la mano, puedes elegir a qué parte de la mano quieres que siga el cubo. Para este ejemplo usaremos la muñeca. Junto a la opción Unión a mano con seguimiento, seleccione el menú desplegable y seleccione muñeca. 

![Imagen de la lección 3, capítulo 3, paso 4](images/Lesson3_chapter3_step4im.PNG)

5. Establece la distancia máxima y mínima en 0 para que no haya ningún distancia entre el cubo y la muñeca del usuario. Una vez establecido, el cubo se alinea perfectamente con la muñeca. También puede ajustar el campo Dirección de referencia para ajustar el comportamiento de la orientación del cubo, como, por ejemplo, si desea permitir que el objeto rote con la muñeca del usuario estableciendo la dirección de referencia para orientarse con el objeto al que se realiza el seguimiento.

![Imagen de la lección 3, capítulo 3, paso 5](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>Enhorabuena
En este tutorial, aprendió a usar los solucionadores de MRTK para que una interfaz de usuario pueda seguir de forma intuitiva al usuario. También has aprendido cómo adjuntar un solucionador a un objeto de juego (es decir, el cubo) para seguir a las manos con seguimiento del usuario. Para más información sobre estos y otros solucionadores incluidos con MRTK, no dudes en visitar la [página de documentación de los solucionadores de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).

[Lección siguiente: 5. interactuar con objetos 3D](mrlearning-base-ch4.md)

