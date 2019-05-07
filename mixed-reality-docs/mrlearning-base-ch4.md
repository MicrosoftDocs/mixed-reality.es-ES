---
title: 'Módulo MR Learning Base: interacción de objetos 3D'
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: 344b3bc892839bc22445e10af644771bc7008ac3
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929585"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>Módulo MR Learning Base: interacción de objetos 3D

En esta lección, se pasará a través de contenido 3D básica y la experiencia del usuario. Se obtendrá información sobre cómo organizar objetos 3D como parte de una colección, obtenga información sobre los cuadros de límite de manipulación básica, obtenga información sobre la interacción far y near y obtenga información sobre la pantalla táctil y captar gestos con seguimiento de mano. 

## <a name="objectives"></a>Objetivos

* Aprenda a organizar el contenido 3D mediante la colección de objetos de cuadrícula del MRTK
* Implementar cuadros de límite
* Configurar objetos 3D para la manipulación básica (mover, girar y escalar)
* Explore la interacción far y near
* Obtenga información acerca de la mano adicional seguimiento gestos como simplemente arrastrando y colocando táctil

## <a name="instructions"></a>Instrucciones

### <a name="organizing-3d-objects-in-a-collection"></a>Organizar los objetos 3D en una colección

1. Haga clic con el botón derecho en la jerarquía y seleccione, "Crear vacío". Esto crea un objeto de juego vacío. Cambie su nombre a "3DObjectCollection." Esto es donde se colocará todos nuestros objetos 3D. Asegúrese de que la posición de la colección se establece en x = 0, y = 0 y, z = 0.

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. Importar módulo activos con las mismas instrucciones para importar paquetes personalizados que se describen en [Lesson1](mrlearning-base-ch1.md). Los activos de módulo incluyen módulos 3D y otros scripts útiles que se usará en este tutorial. El paquete de unity de módulo puede encontrarse aquí: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Puede reconocer la taza de café prefabricado un cubo azul junto a él. No seleccione la taza de café con el cubo azul y notas pequeñas (que indica el modelo en 3D original y no el recurso prefabricado.) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. Arrastre el recurso prefabricado taza de café de su elección en el objeto de juego "3DObjectCollection" del paso 1. La taza de café ahora es un elemento secundario de la colección.

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. A continuación, vamos a agregar más objetos 3D en la escena. A continuación es una lista de objetos que vamos a agregar en este ejemplo. A medida que agrega los objetos, es posible que aparecen en la escena de varios tamaños. Ajustar la escala de cada modelo en 3D en la configuración de transformación en el panel del inspector. Ajustes recomendados en este ejemplo se muestran con los objetos siguientes. Estas palabras de búsqueda en el cuadro de búsqueda en el panel de proyecto y arrastre el recurso prefabricado objeto 3D en el objeto "3DObjectCollection" similar al paso anterior. Encontrará estos colección de prefabricados en activos > BaseModuleAssets > prefabricados del módulo de Base
- Busque "TheModule_BaseModuleIncomplete". Arrastre a la escena. Establezca la escala en x = 0,03, y = 0,03, z = 0.03. 
- Busque "Octa_BaseModuleIncomplete". Arrastre a la escena. Establezca la escala en x = 0.13. y = 0.13, z =0.13.
- Busque "EarthCore_BaseModuleIncomplete". Arrastre a la escena. Establezca la escala en x = 50,0 y = 50,0, z = 50,0.
- Busque "Cheese_BaseModuleIncomplete". Arrastre a la escena. Establezca la escala en x = 0,05, y = 0,05, z = 0,05.
- Busque "Model_Platonic_BaseModuleIncomplete". Arrastre a la escena. Establezca la escala en x = 0,13, y = 0,13, z = 0.13.
- Busque "CoffeeCup_BaseModuleIncomplete". Arrastre a la escena.

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. Agregar 3 cubos en la escena. A la derecha, haga clic en el objeto "3DObjectCollection", seleccione "objeto 3D" y luego seleccione "Cubo". Establezca la escala en x = 0.14, y = 0.14 y, z = 0.14. Repita este paso 2 veces más para crear un total de 3 cubos. Como alternativa, puede duplicar el cubo de dos veces para un total de 3 cubos. También puede usar los tres prefabricados cubo preparada desde activos > BaseModuleAssets > Base prefabricados de módulo y seleccione GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete y OrangeCube_BaseModuleIncomplete.

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. Organice su colección de objetos para formar una cuadrícula mediante el procedimiento descrito en [lección 2](mrlearning-base-ch2.md) utilizando la colección de objetos de cuadrícula del MRTK. Hacer referencia a la imagen siguiente para ver un ejemplo de configuración de los objetos en una cuadrícula de 3 x 3.

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>Nota: Es posible que tenga en cuenta que algunos de los objetos están fuera de centro, como los objetos en la imagen anterior. Esto es porque prefabricados u objetos pueden tener objetos secundarios que no estén alineados. No dude en realizar los ajustes necesarios para las posiciones de objeto o posiciones de objeto secundario para lograr una cuadrícula alineada correctamente.


### <a name="manipulating-3d-objects"></a>Manipular objetos 3D
1. Agregar la capacidad de manipular un cubo. Para agregar la capacidad de manipular objetos 3D, debe hacer lo siguiente:
-   Seleccione el objeto 3D que desea manipular en la jerarquía (en este ejemplo, uno de los cubos).
-   Haga clic en "agregar el componente". 
-   Busque "manipulación".
-   Seleccione "controlador de manipulación".
-   Repita el proceso para todos los objetos 3D en el objeto "3DObjectCollection", pero no el "3DObjectCollection" propio.
-   Asegúrese de que todos los objetos 3D tienen un colisionador o colisionador de cuadro (Agregar componente > cuadro colisionador).

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>El controlador de manipulación es un componente que le permitirá ajustar la configuración de cómo se comportan los objetos al que se ha manipulado. Esto incluye la rotación, escala, mover y el movimiento de restricción en algunos ejes. 

2. Restringir un cubo para que solo se puede escalar. Seleccione un cubo en el objeto "3DObjectCollection". En el panel del inspector, junto a "tipo de manipulación pasar dos", haga clic en el menú desplegable y seleccione "escalar". Esto hace que el usuario sólo puede cambiar el tamaño del cubo.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. Cambiar el color de cada cubo para que nos podemos diferenciar entre ellos. 
-   Vaya al panel de proyecto y desplácese hacia abajo hasta que vea "MixedRealityToolkit.SDK", a continuación, selecciónelo.
-   Seleccione la carpeta "Recursos estándar".
-   Haga clic en la carpeta "materiales".
-   Arrastre un material diferente a cada uno de los cubos. 

>Nota: Puede elegir cualquier color para los cubos. En nuestro ejemplo, vamos a usar "glowingcyan", "glowingorange," y "verde". No dude en experimentar con diferentes colores. Para agregar el color para el cubo, haga clic en el cubo que desee cambiar el color de, a continuación, arrastre el material al campo de material del representador de malla en el panel del inspector del cubo. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. Seleccione otro cubo en el objeto "3DObjectCollection" y hacer que su movimiento está limitado a la distancia de corrección del encabezado. Para ello, a la derecha de "restricción en movimiento", haga clic en el menú desplegable y seleccione "corregir la distancia desde el encabezado". Esto hace que el usuario sólo puede mover el cubo dentro de su campo de visión. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

Objetivo de los pasos siguientes: Se habilitará la captación y la interacción con nuestros objetos 3D. Se aplicará la configuración de manipulación diferentes 

5. Seleccione el objeto de queso y en el panel del inspector, haga clic en "agregar el componente". 

6. Busque en el cuadro de búsqueda "Cerca de la interacción Grabbable" y seleccione la secuencia de comandos. Este componente permite a los usuarios llegar y tomar los objetos con manos sometidas a seguimiento. Los objetos también se puede manipular a distancia, a menos que esté desactivada la casilla "Permitir la manipulación en el momento" (se indica con un círculo verde en la imagen siguiente).

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. Agregue "Cerca de la interacción Grabbable" para el objeto octal, objeto Platonic, core tierra, módulo lunar y taza de café, repita el paso 5 y 6 en dichos objetos.

8. Quite la capacidad de manipulación lejos del objeto octal. Para ello, seleccione el octal en la jerarquía y desactive la casilla "permitir una manipulación lejano" (marcada con un círculo verde). Esto hace que los usuarios sólo pueden interactuar con el octal directamente mediante manos sometidas a seguimiento.

>Nota: Para la documentación completa sobre el componente de controlador de manipulación y tiene asociados configuración, consulte el [MRTK documentación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Asegúrese de que el componente "Cerca de la interacción Grabbable" se ha agregado el núcleo de la tierra, el módulo lunar y la taza de café (vea el paso 7).

10. Para el módulo lunar, cambie la configuración de controlador de manipulación para que gira sobre el objeto center para ambos cerca y lejano interacción, tal como se muestra en la imagen siguiente.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: Para el núcleo de la tierra, cambiar el comportamiento de la versión a "nothing". Esto hace que una vez que se libera el núcleo de la tierra de comprensión de los usuarios, no continúe mover. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> Nota: Esta configuración es útil para escenarios como la creación de una bola que puede iniciar. Mantener la velocidad y la velocidad angular hace que una vez que la bola se lanza continuará mover a la velocidad era publicadas en, de forma similar a cómo se comportaría una bola física.

### <a name="adding-bounding-boxes"></a>Agregar cuadros de límite
Cuadros de límite que sea más sencillo e intuitivo para manipular objetos con una mano para la manipulación directa (cerca de interacción) y en función de ray manipulación (interacción lejano). Cuadros de límite de la oferta "handles" que se pueden arrastrar para escalar y girar objetos a lo largo de ejes específicos.
>Nota: Antes de poder agregar un rectángulo a un objeto primero deberá tener un colisionador en el objeto (por ejemplo, un colisionador de cuadro.) Como hicimos anteriormente en esta lección. Se pueden agregar colisionadores, seleccione el objeto y, en el panel del inspector del objeto al seleccionar Agregar componente > Colisionador de cuadro.
>

1. Agregar un colisionador de cuadro para el objeto básico de tierra, si aún no existe (colisionador de cuadro y el programa de instalación no es necesario si usa el recurso prefabricado proporcionado en la carpeta activos del módulo de Base, por las instrucciones que aparecen). En el caso del principal de la tierra, se deberá agregar el colisionador de cuadro para el objeto "node_id30" bajo el núcleo de la tierra, tal como se muestra en la imagen siguiente. Seleccione node_id30 y en la ficha del objeto inspector, haga clic en "agregar el componente" y busque "colisionador de cuadro". 

![Lesson4 capítulo 3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 capítulo 3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> Nota: Asegúrese de que visualice el colisionador de cuadro para que no sea demasiado grande o demasiado pequeño. Debe ser aproximadamente el mismo tamaño que el objeto es que rodean a (en este ejemplo, el núcleo de la tierra). Ajuste el colisionador de cuadro según sea necesario mediante la opción Editar colisionador en el colisionador de cuadro. Puede cambiar la x, y y los valores z o arrastre los controladores de cuadro de límite en la ventana del editor de escena. 

![Lesson4 capítulo 3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. Agregue un rectángulo al objeto de la tierra core "node_id30". Para ello, seleccione el objeto "node_id30" desde "3DObjectCollection". En la pestaña inspector, haga clic en "agregar el componente" y busque "rectángulo". Asegúrese de que el cuadro de límite, colisionador de cuadro y scripts de manipulación (controlador de manipulación, cerca de la interacción grabbable) están todos en el mismo objeto de juego.

3.  En la sección de "Comportamiento" del cuadro de límite, seleccione "Activar inicio" en la lista desplegable de activación. Para revisar los detalles adicionales sobre las distintas opciones de activación y otras opciones del cuadro de límite, consulte el [MRTK documentación del cuadro de límite](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *En los pasos siguientes, se cambiará también cómo se ve el cuadro de límite ajustando el material de cuadro de forma predeterminada, el material mientras se está obteniendo un elemento, así como la visualización de identificadores (manipuladores de esquina y en paralelo). El MRTK contiene varias opciones para personalizar el cuadro de límite.*

4. En el panel de proyecto, busque "boundingbox" y verá una lista de materiales que se indica mediante una esfera azul en los resultados de búsqueda, como se muestra en la imagen siguiente. 

5. Arrastre el material "boundingbox" en la ranura de material de casilla en el componente del cuadro de límite. También tome el material "boundingboxgrabbed" y colocar en la ranura de material grabbed cuadro en el componente del cuadro de límite.

6. Arrastre el material "MRTK_BoundingBox_ScaleWidget" en la ranura prefabricado de controlador de escala en el componente del cuadro de límite. 

7. Arrastre el material "MRTK_BoundingBox_RotateWidget" en la ranura de identificador de la rotación en el componente del cuadro de unión.

![Capítulo 3 Lesson4 paso4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. Asegúrese de que el rectángulo de selección tiene como destino el objeto correcto. En el componente de cuadro de límite, es el "objeto de destino" y "delimita invalidación" secuencias de comandos. Asegúrese de que al arrastrar el objeto que tiene el cuadro de límite alrededor de ella a ambas de estas ranuras. En este ejemplo, arrastre el objeto "node_id30" a ambos de estos espacios, tal como se muestra en la imagen siguiente.

> Al iniciar o al reproducir la aplicación, el objeto aparecerá ahora rodeado por un marco de azul. Se agradece arrastre las esquinas de ese marco para cambiar el tamaño del objeto. Si queremos que los identificadores de escalado y los controladores de giro a ser más grande y más visible, se recomienda usar el valor predeterminado (evitando los pasos 4-7). configuración del cuadro de límite 

![Lesson4 capítulo 3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. Para volver a la visualización del cuadro, en el panel del inspector de objeto del cuadro de límite de delimitador predeterminado Seleccione el recurso prefabricado de identificador de rotación y presione la tecla SUPR, ahora verá una visualización de cuadro delimitador similar a la siguiente imagen. Nota: las visualizaciones del cuadro delimitador solo aparece cuando está en modo de juego.

![Lesson4 capítulo 3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Adición de efectos de interacción
En este ejemplo, vamos a reproducir un sonido efecto al tocar un objeto con la mano.

1. Agregue un componente de origen de audio para el objeto de juego. Seleccione el objeto "octal" en la jerarquía de la escena. En el panel del inspector, haga clic en el botón "agregar el componente", busque y seleccione "origen de audio". Vamos a usar este origen de audio se reproduzca un efecto de sonido en un paso posterior. 

>Nota: Asegúrese de que el objeto "Octal" tiene un colisionador de cuadro en ella.

2. Agregue el componente "cerca de la interacción touchable". Haga clic en el botón "Agregar componente" en el panel de inspector y busque "cerca de interacción touchable". Selecciónelo para agregar el componente. Nota: corregir la captura de pantalla para resaltar que estamos agregando el componente y no solo resaltado colisionador de cuadro.

>Nota: Se agregó anteriormente "casi interacción grabbable." La diferencia entre esto y "cerca de la interacción touchable" es que la interacción de "grabbable" está pensada para que un objeto se capturó e interactúe con él. El componente "touchable" está diseñado para que el objeto que se han tocado. Ambos componentes se pueden usar conjuntamente para una combinación de las interacciones.

![Lesson4 Capítulo4 2Im del paso 1](images/Lesson4_chapter4_step1-2im.PNG)

3. Agregar en la secuencia de comandos "entregar táctil interacción". Tenga en cuenta que esta secuencia de comandos se incluye con la escena de unity que importa como parte de este paquete de demostración y no se incluye en el MRTK original. Simplemente, como el paso anterior, haga clic en "agregar el componente" y busque "touch de interacción de mano" para agregarlo. 
   Tenga en cuenta que tiene 3 opciones con la secuencia de comandos: 

   - "En touch completado". Esto desencadenará cuando toque y liberar el objeto. 
   - "En touch iniciado". Esto desencadenará cuando se toca el objeto. 
   - "En la tecnología táctil actualizado." Esto desencadenará periódicamente mientras toca el objeto de la mano. 

   En este ejemplo, se trabajará con la configuración "en la tecnología táctil iniciado".

4. Haga clic en el botón "+" en la opción "en la tecnología táctil iniciado", tal como se muestra en la imagen siguiente. Arrastre el objeto de ocho en el campo vacío. 

5. En la lista desplegable que no dice "ninguna función" (por encima de un rectángulo verde en la imagen siguiente), seleccione AudioSource > PlayOneShot. Agregaremos un clip de audio a este campo con los conceptos siguientes:

   - El MRTK proporcionan una breve lista de clips de audio. No dude en explorar estas opciones en el panel de proyecto. Los encontrará en la carpeta "MixedRealityToolkit.SDK" y, a continuación, en la carpeta "recursos estándar". Allí verá una carpeta de "audio" ¿dónde están los clips de audio.
   - En este ejemplo, vamos a usar el clip de audio "MRTK_Gem". 
   - Para agregar un clip de audio, simplemente arrastre el clip que desee desde el panel de proyecto en el AudioSource.PlayOneShot (marcados con un cuadro verde en el ejemplo anterior) en el panel del inspector.

   Ahora cuando el usuario llega y afecta al objeto de ocho, se reproducirá la pista de audio "MRTK_Gem". La secuencia de comandos "Mano interacción táctil" también ajustará el color del objeto al tocarla. 

![Paso 3 de Capítulo4 Lesson4 Noteim 5](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>Enhorabuena 
En esta lección, ha aprendido cómo organizar los objetos 3D en una colección de la cuadrícula y cómo manipular objetos 3D (ajuste de escala, rotación y mover) con cerca de interacción (acaparando directamente con manos sometidas a seguimiento) y la interacción lejano (con rayos mirada o los rayos de mano). También aprendió a colocar cuadros de límite alrededor de los objetos 3D y aprendió a usar y personalizar el gizmos en los cuadros de límites. Por último, ha aprendido cómo desencadenar eventos al tocar un objeto.

[Próxima lección: Entrada avanzados](mrlearning-base-ch5.md)

