---
title: 'Módulo base de aprendizaje de Mixed Reality: Interacción con objetos 3D'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730906"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>Módulo base de aprendizaje de Mixed Reality: Interacción con objetos 3D

En esta lección revisaremos el contenido 3D básico y la experiencia del usuario. Aprenderemos a organizar objetos 3D como parte de una colección e información sobre los rectángulos de selección para la manipulación básica, la interacción próxima y lejana, y los gestos de tocar y agarrar con el seguimiento manual. 

## <a name="objectives"></a>Objetivos

* Aprender a organizar el contenido 3D mediante la colección de objetos de cuadrícula de MRTK
* Implementar rectángulos de selección
* Configurar objetos 3D para la manipulación básica (mover, girar y escalar)
* Explorar la interacción próxima y lejana
* Aprender información sobre otros gestos de seguimiento manuales, como agarrar y tocar

## <a name="instructions"></a>Instrucciones

### <a name="organizing-3d-objects-in-a-collection"></a>Organización de los objetos 3D en una colección

1. Haz clic con el botón derecho en la jerarquía y selecciona "Create Empty" (Crear vacío). Así se crea un objeto de juego vacío. Cámbiale el nombre a "3DObjectCollection". Aquí colocaremos todos nuestros objetos 3D. Asegúrate de que la posición de la colección se establece en x = 0, y = 0 y, z = 0.

![Imagen de la lección 4, capítulo 1, paso 1](images/Lesson4_Chapter1_step1im.PNG)

2. Importa los recursos BaseModule siguiendo las instrucciones para importar paquetes personalizados que se describen en la [lección 1](mrlearning-base-ch1.md). Los recursos BaseModule incluyen módulos 3D y otros script útiles que se usarán en este tutorial. El paquete BaseModule de Unity se encuentra aquí: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>.

3. El objeto prefabricado CoffeeCup se reconoce por el cubo azul que lo acompaña. No debes seleccionar el objeto CoffeeCup con el cubo azul y la nota blanca (que denota el modelo 3D original y no el prefabricado). 

![Imagen de la lección 4, capítulo 1, nota a](images/Lesson4_chapter1_noteaim.PNG)

4. Arrastra el objeto prefabricado CoffeeCup que prefieras al objeto de juego "3DObjectCollection" del paso 1. Ahora la taza de café será un elemento secundario de la colección.

![Imagen de la lección 4, capítulo 1, paso 4](images/Lesson4_chapter1_step4ima.PNG)

5. Ahora agregaremos más objetos 3D a la escena. A continuación se muestra la lista de objetos que vamos a agregar en este ejemplo. Al ir agregando objetos, pueden aparecer en la escena con distintos tamaños. Ajusta la escala de los modelos 3D en la configuración de transformación del panel del inspector. Los ajustes recomendados para este ejemplo se muestran con los objetos siguientes. Escribe estas palabras en el cuadro de búsqueda del panel del proyecto y arrastra el objeto 3D prefabricado al objeto "3DObjectCollection", como en el paso anterior. Esta colección de objetos prefabricados se encuentra en Assets>BaseModuleAssets>Base Module Prefabs (Recursos>RecursosDeMóduloBase>Objetos prefabricados del módulo base)
- Busca "TheModule_BaseModuleIncomplete" y arrástralo a la escena. Establece la escala en x = 0.03; y = 0.03; z = 0.03. 
- Busca "Octa_BaseModuleIncomplete" y arrástralo a la escena. Establece la escala en x = 0.13; y = 0.13; z =0.13.
- Busca "EarthCore_BaseModuleIncomplete" y arrástralo a la escena. Establece la escala en x = 50.0; y = 50.0; z = 50.0.
- Busca "Cheese_BaseModuleIncomplete" y arrástralo a la escena. Establece la escala en x = 0.05; y = 0.05; z = 0.05.
- Busca "Model_Platonic_BaseModuleIncomplete" y arrástralo a la escena. Establece la escala en x = 0.13; y = 0.13; z = 0.13.
- Busca "CoffeeCup_BaseModuleIncomplete" y arrástralo a la escena.

![Imagen de la lección 4, capítulo 1, paso 5](images/Lesson4_Chapter1_step5im.PNG)

6. Agrega 3 cubos a la escena. Haz clic con el botón derecho en el objeto "3DObjectCollection" y selecciona "3D Object" (Objeto 3D) y "Cube" (Cubo). Establece la escala en x = 0.14; y = 0.14; z = 0.14. Repite este paso dos veces más para crear tres cubos en total. Para conseguir los tres, puedes duplicar el cubo dos veces. También puedes usar los tres cubos prefabricados preparados de Assets>BaseModuleAssets>Base Module Prefabs (Recursos>RecursosDeMóduloBase>Objetos prefabricados del módulo base) y seleccionar GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete y OrangeCube_BaseModuleIncomplete.

![Imagen de la lección 4, capítulo 1, paso 6](images/Lesson4_Chapter1_step6im.PNG)

7. Organiza la colección de objetos para formar una cuadrícula mediante el procedimiento descrito en la [lección 2](mrlearning-base-ch2.md) con la colección de objetos de cuadrícula de MRTK. Consulta la imagen siguiente para ver un ejemplo de configuración de los objetos en una cuadrícula de 3 x 3.

![Imagen de la lección 4, capítulo 1, nota b](images/Lesson4_chapter1_notebim.PNG)

>Nota: Puedes notar que algunos de los objetos están descentrados, como los de la imagen anterior. Esto se debe a que los recursos prefabricados o los objetos pueden tener objetos secundarios sin alinear. Puedes realizar los ajustes de posición necesarios en los objetos o los objetos secundarios para alinear la cuadrícula correctamente.


### <a name="manipulating-3d-objects"></a>Manipulación de objetos 3D
1. Agrega la capacidad de manipular un cubo. Para agregar la capacidad de manipular objetos 3D, debes hacer lo siguiente:
-   Selecciona el objeto 3D que desees manipular en la jerarquía (en este ejemplo, uno de los cubos).
-   Haz clic en "Add component" (Agregar componente). 
-   Busca "Manipulation" (Manipulación).
-   Selecciona "Manipulation Handler" (Controlador de manipulación).
-   Repite el proceso para todos los objetos 3D del objeto "3DObjectCollection", pero no para "3DObjectCollection".
-   Asegúrate de que todos los objetos 3D tienen un colisionador o un colisionador de cuadro (Add Component > Box Collider [Agregar componente > Colisionador de cuadro]).

![Imagen de la lección 4, capítulo 2, paso 1](images/Lesson4_chapter2_step1im.PNG)

>El controlador de manipulación es un componente que permite ajustar la configuración de cómo se comportan los objetos al manipularlos. Esto incluye el giro, el escalado, el movimiento y la limitación de movimiento en determinados ejes. 

2. Restringe un cubo para que solo se pueda escalar. Selecciona un cubo del objeto "3DObjectCollection". En el panel del inspector, junto a "Two Handed Manipulation Type" (Manipulación con dos manos), haz clic en el menú desplegable y selecciona "Scale" (Escalar). Esto hace que el usuario solo pueda cambiar del cubo el tamaño.

![Imagen de la lección 4, capítulo 2, paso 2](images/Lesson4_Chapter2_step2im.PNG)

3. Cambia el color de cada cubo para que los podemos diferenciar. 
-   Ve al panel del proyecto y desplázate hacia abajo hasta que veas "MixedRealityToolkit.SDK" y puedas seleccionarlo.
-   Selecciona la carpeta "Standard Assets" (Recursos estándar).
-   Haz clic en la carpeta "Materials" (Materiales).
-   Arrastra un material distinto a cada cubo. 

>Nota: Para los cubos, puedes elegir cualquier color. En nuestro ejemplo, vamos a usar "glowingcyan", "glowingorange," y "green". Puedes también experimentar con otros colores. Para agregar el color al cubo, haz clic en el cubo correspondiente y arrastra el material al campo de material de la representación de la malla en el panel del inspector del cubo. 

![Imagen de la lección 4, capítulo 2, paso 3](images/Lesson4_Chapter2_step3im.PNG)

4. Selecciona otro cubo del objeto "3DObjectCollection" y haz que solo se pueda mover una distancia fija desde la cabeza. Para ello, a la derecha de "Constraint on Movement" (Limitación del movimiento), haz clic en el menú desplegable y selecciona "Fix Distance From Head" (Distancia fija desde la cabeza). De esta manera, el usuario solo podrá mover el cubo dentro de su campo de visión. 

![Imagen de la lección 4, capítulo 2, paso 4](images/Lesson4_chapter2_step4im.PNG)

Objetivo de los siguientes pasos: podremos agarrar nuestros objetos 3D e interactuar con ellos. Aplicaremos distintas configuraciones de manipulación. 

5. Selecciona el objeto Cheese y, en el panel del inspector, haz clic en "Add Component" (Agregar componente). 

6. En el cuadro de búsqueda, busca "Near Interaction Grabbable" (Interacción próxima: atrapar) y selecciona el script. Este componente permite a los usuarios alcanzar y agarrar los objetos con las manos con seguimiento. Los objetos también se pueden manipular a distancia, a menos que esté desactivada la casilla "Allow Far Manipulation" (Permitir la manipulación lejana), la que tiene un círculo verde en la imagen siguiente.

![Imagen de la lección 4, capítulo 2, paso 6](images/Lesson4_Chapter2_step6im.PNG)

7. Repite los pasos 5 y 6 en los objetos Octa, Platonic, Earth Core, Lunar Module y CoffeeCup para agregar el evento "Near Interaction Grabbable" (Interacción próxima: atrapar).

8. Deshabilita la manipulación lejana para el objeto Octa. Para ello, selecciónalo en la jerarquía y desactiva la casilla "Allow Far Manipulation" (Permitir manipulación lejana), marcada con un círculo verde en la imagen anterior. Esto hace que los usuarios solo pueden interactuar con el objeto Octa directamente con las manos con seguimiento.

>Nota: Para la documentación completa sobre el componente del controlador de manipulación y las configuraciones asociadas, consulta la [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Asegúrate de que el componente "Near Interaction Grabbable" (Interacción próxima: atrapar) se ha agregado el objeto Earth Core, al objeto Lunar Module y al objeto Coffee Cup (consulta el paso 7).

10. Para el objeto Lunar Module, cambia la configuración del controlador de manipulación para que gire alrededor del centro del objeto para la interacción tanto próxima como lejana, tal y como se muestra en la siguiente imagen.

![Imagen de la lección 4, capítulo 2, paso 10](images/Lesson4_chapter2_step10im.PNG)

11: Para el objeto Earth Core, cambia el comportamiento de liberación a "Nothing" (Ninguno). Esto hace el objeto Earth Core deje de moverse al liberarse del alcance de los usuarios. 

![Imagen de la lección 4, capítulo 2, paso 11](images/Lesson4_Chapter2_step11im.PNG)

> Nota: Esta configuración es útil para escenarios como la creación de una pelota para tirar. Mantener la velocidad linear y la angular hace que una vez lanzada la pelota, esta continúe moviéndose a la velocidad inicial, tal y como lo haría una bola física.

### <a name="adding-bounding-boxes"></a>Agregar rectángulos de selección
Los rectángulos de selección facilitan la manipulación de objetos con una mano y la hacen más intuitiva tanto en la manipulación directa (interacción próxima) como por rayos (interacción lejana). Los rectángulos de selección ofrecen "asas" que se pueden agarrar para el escalado y el giro de objetos en ejes concretos.
>Nota: Para agregar un rectángulo de selección a un objeto, este debe tener un colisionador (por ejemplo, un colisionador de cuadro). Como hicimos anteriormente en esta lección, para agregar un colisionador, selecciona el objeto y en su panel del inspector, selecciona Add Component>Box Collider (Agregar componente > Colisionador de cuadro).
>

1. Si no lo tiene, agrega un colisionador de cuadro al objeto Earth Core (según las instrucciones, el colisionador de cuadro y la configuración no son necesarios si se usa el objeto prefabricado de la carpeta Base Module Assets [Recursos de Módulo Base]). En el caso del objeto Earth Core, tendremos que agregar el colisionador de cuadro al objeto "node_id30" de debajo, como se muestra en la siguiente imagen. Selecciona node_id30 y, en la pestaña del inspector del objeto, haz clic en "Add Component" (Agregar componente) y busca "Box Collider" (Colisionador de cuadro). 

![Imagen de la lección 4, capítulo 3, paso 1](images/Lesson4_Chapter3_step1im.PNG)

![Imagen de la lección 4, capítulo 3, paso 2](images/Lesson4_chapter3_step2im.PNG)

> Nota: Asegúrate de que visualizas el colisionador de cuadro, de manera que no sea demasiado grande ni demasiado pequeño. Debe ser aproximadamente del mismo tamaño que el objeto que rodea (en este ejemplo, el Earth Core). Ajusta el colisionador de cuadro como proceda al seleccionar la opción de edición del colisionador de cuadro. Puedes cambiar los valores de x, y o z, o arrastrar los controladores del rectángulo de selección en la ventana de edición de la escena. 

![Imagen de la lección 4, capítulo 3, nota](images/Lesson4_Chapter3_noteim.PNG)

2. Agrega un rectángulo de selección al objeto "node_id30" de Earth Core. Para ello, selecciona el objeto "node_id30" desde "3DObjectCollection". En la pestaña del inspector, haz clic en "Add Component" (Agregar componente) y busca "Bounding Box" (Rectángulo de selección). Asegúrate de que el rectángulo de selección, el colisionador de cuadro y los scripts de manipulación (Manipulation Handler [Controlador de manipulación] y Near Interaction Grabbable [Interacción próxima: agarrar]) se encuentran en el mismo objeto del juego.

3.  En la sección "Behaviour" (Comportamiento) del rectángulo de selección, selecciona "Activate on start" (Activar al inicio) en la lista desplegable Activation (Activación). Para revisar los detalles adicionales sobre las distintas opciones de activación y otras del rectángulo de selección, consulta la [documentación del recuadro de selección de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>).

   

   *En los siguientes pasos también cambiaremos el aspecto del rectángulo de selección. Para ello, ajustaremos el material predeterminado de la caja, el material que se agarra y la visualización de las asas (en la esquina y los laterales). MRTK contiene varias opciones para personalizar el rectángulo de selección.*

4. En el panel del proyecto, busca "boundingbox" y verás una lista de materiales, que se indican con una esfera azul en los resultados de búsqueda, como en la siguiente imagen. 

5. Arrastra el material "boundingbox" al recuadro del material de la caja del componente del rectángulo de selección. Arrastra también el material "boundingboxgrabbed" y colócalo en el recuadro del material de la caja agarrada del componente del rectángulo de selección.

6. Arrastra el material "MRTK_BoundingBox_ScaleWidget" al recuadro del asa para escalado prefabricada del componente del rectángulo de selección. 

7. Arrastra el material "MRTK_BoundingBox_RotateWidget" al recuadro del asa para giro del componente del rectángulo de selección.

![Imagen de la lección 4, capítulo 3, pasos 4-7](images/Lesson4_chapter3_step4-7im.PNG)

8. Asegúrate de que el rectángulo de selección apunta al objeto correcto. En el componente del rectángulo de selección se encuentran los scripts "Target Object" (Objeto de destino) y "Bounds Override" (Superponer selección). Asegúrate de arrastrar el objeto con el rectángulo de selección a su alrededor a ambos recuadros. En este ejemplo, arrastra "node_id30" a estos recuadros como se muestra en la siguiente imagen.

> Al iniciar la aplicación o al reproducirla, el objeto estará rodeado de un cuadro azul. Puedes arrastrar las esquinas de este para cambiar el tamaño del objeto. Si quieres que las asas de escalado y de giro sean mayores y más visibles, te recomendamos que uses la configuración del rectángulo de selección predeterminada (y se evitan los pasos 4-7). 

![Imagen de la lección 4, capítulo 3, paso 8](images/Lesson4_Chapter3_step8im.PNG)

9. Para volver a la visualización predeterminada del rectángulo de selección, en el panel del inspector del objeto de este, selecciona el asa de giro prefabricada y presiona la tecla Delete (Eliminar). Verás un rectángulo de selección similar al de esta imagen. Nota: La visualización del rectángulo de selección solo aparece en el modo de reproducción.

![Imagen de la lección 4, capítulo 3, paso 9](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>Agregar de efectos al tocar
En este ejemplo vamos a reproducir un efecto de sonido al tocar un objeto con la mano.

1. Agrega un componente de origen de audio al objeto de juego. Selecciona el objeto Octa en la jerarquía del escenario. En el panel del inspector, haz clic en el botón "Add Component" (Agregar componente), y busca y selecciona "Audio Source" (Origen de audio). Usaremos este origen de audio para reproducir un efecto de sonido más adelante. 

>Nota: Asegúrate de que el objeto Octa tiene un colisionador de cuadro.

2. Agrega el componente "Near Interaction Touchable" (Interacción próxima: tocar). Haz clic en el botón "Add Component" (Agregar componente) en el panel de inspector y busca "Near Interaction Touchable" (Interacción próxima: tocar). Selecciónalo para agregar el componente. NOTA: Corregir la captura de pantalla para destacar que estamos agregando el componente y no solo resaltando el colisionador de cuadro.

>Nota: Antes agregamos "Near Interaction Grabbable" (Interacción próxima: agarrar). La diferencia entre esta y "Near Interaction Touchable" (Interacción próxima: tocar) es que la primera sirve para que un objeto se pueda agarrar y para que se pueda interactuar con él. La segunda, para poder tocar el objeto. Ambos componentes se pueden usar conjuntamente para una combinación de interacciones.

![Imagen de la lección 4, capítulo 4, pasos 1-2](images/Lesson4_chapter4_step1-2im.PNG)

3. Agrega el script "Hand Interaction Touch" (Interacción con las manos: tocar). Ten en cuenta que este script se incluye en la escena de Unity que importaste como parte de este paquete de demostración y no en la instancia de MRTK original. Como en el paso anterior, haz clic en "Add Component" (Agregar componente) y busca "Hand Interaction Touch" (Interacción con las manos: tocar) para agregarla. 
   Observa que el script ofrece tres opciones: 

   - "On Touch Completed" (Al terminar de tocar). Esta opción se activará al tocar y soltar el objeto. 
   - "On Touch Started" (Al empezar a tocar). Esta, al tocar el objeto. 
   - "On Touch Updated" (Al actualizarse el tocar). Esta se activará periódicamente mientras la mano toque el objeto. 

   En este ejemplo trabajaremos con la configuración "On Touch Started" (Al empezar a tocar).

4. Haz clic en el botón "+" de "On Touch Started" (Al empezar a tocar), como se muestra en la siguiente imagen. Arrastra el objeto Octa al campo vacío. 

5. En la lista desplegable que reza "No Function" (Ninguna función) (encima del rectángulo verde de la siguiente imagen), selecciona AudioSource>PlayOneShot (OrigenDeAudio>ReproducirUnaPista). Agregaremos un clip de audio a este campo con los siguientes conceptos:

   - MRTK proporcionan una pequeña lista de clips de audio. Puedes explorarlas en el panel del proyecto. Se encuentran en carpeta "MixedRealityToolkit.SDK" y la subcarpeta "Standard Assets" (Recursos estándar). En ella se encuentra una carpeta "audio" con todos los clips.
   - En este ejemplo usaremos "MRTK_Gem". 
   - Para agregar un clip de audio solo tienes que arrastrar el que quieras del panel del proyecto a AudioSource.PlayOneShot (que aparece con un recuadro verde en el siguiente ejemplo) en el panel del inspector.

   Ahora, cuando el usuario alcance y toque el objeto Octa, se reproducirá la pista de audio "MRTK_Gem". El script "Hand Interaction Touch" (Interacción con las manos: tocar) también ajustará el color del objeto al tocarlo. 

![Imagen de la lección 4, capítulo 4, pasos 3-5 y nota](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>Enhorabuena 
En esta lección has aprendido a organizar objetos 3D en una colección de cuadrícula y a manipular objetos 3D (escalado, giro y movimiento) con interacción próxima (agarrándolos directamente con manos con seguimiento) y lejana (con la mirada o rayos de las manos). También has aprendido a colocar rectángulos de selección alrededor de objetos 3D, y a usar y personalizar los artilugios de estos rectángulos. Por último, has aprendido a desencadenar eventos al tocar objetos.

[Próxima lección: Entrada avanzada](mrlearning-base-ch5.md)

