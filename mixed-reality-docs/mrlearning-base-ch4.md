---
title: 'Tutoriales de introducción: 5. Interactuar con objetos 3D'
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 07bcce2ab9ab3bda035f7f2b39a90753cf45358d
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913858"
---
# <a name="5-interacting-with-3d-objects"></a>5. interactuar con objetos 3D

En este tutorial, obtendrá información sobre el contenido 3D básico y la experiencia del usuario, por ejemplo:

* Organizar objetos 3D como parte de una colección
* Cuadros de límite para la manipulación básica
* Interacción cercana y lejana
* Gestos táctiles y de agarre con seguimiento manual

## <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo organizar el contenido 3D con la colección de objetos Grid de MRTK
* Implementar rectángulos de selección
* Configurar objetos 3D para la manipulación básica: movimiento, rotación y escala
* Explorar la interacción próxima y lejana
* Más información acerca de los gestos de seguimiento de la mano, como captar y tocar

## <a name="instructions"></a>Instrucciones

### <a name="organizing-3d-objects-in-a-collection"></a>Organización de los objetos 3D en una colección

1. Haga clic con el botón derecho en la jerarquía y seleccione crear vacío para crear un objeto de juego vacío, cambie su nombre a 3DObjectCollection y asegúrese de que está colocado en x = 0, y = 0 y z = 0.

    ![mrlearning-base-CH4-1-STEP1. png](images/mrlearning-base-ch4-1-step1.png)

2. Descargue el paquete de Unity [BaseModuleAssets versión 1.2.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage) e impórtelo con las mismas instrucciones para importar los paquetes personalizados descritos en [Lesson1](mrlearning-base-ch1.md). Este paquete incluye modelos 3D y otros recursos útiles que se usan en este tutorial.

3. En el panel Proyecto, vaya a activos > BaseModuleAssets > módulo base Prefabs y busque "incompleto", se usarán algunos de estos Prefabs.

    ![mrlearning-base-CH4-1-Step3. png](images/mrlearning-base-ch4-1-step3.png)

4. Arrastre la taza de café al objeto de juego 3DObjectCollection del paso 1. Ahora la taza de café será un elemento secundario de la colección.

    ![mrlearning-base-CH4-1-Step4. png](images/mrlearning-base-ch4-1-step4.png)

5. A continuación, agregará más objetos 3D a la escena siguiendo el mismo proceso que en el paso anterior. A continuación se muestra una lista de los objetos que se van a agregar en este ejemplo. A medida que agrega los objetos, es posible que aparezcan en la escena en varios tamaños. Ajuste la escala de cada modelo 3D en configuración de transformación en el panel Inspector. Los ajustes recomendados para este ejemplo se muestran con los objetos siguientes.

    * Cheese_BaseModuleIncomplete. Escala: x = 0,05, y = 0,05, z = 0,05.
    * CoffeeCup_BaseModuleIncomplete. Escala: x = 0,1, y = 0,1, z = 0,1.
    * EarthCore_BaseModuleIncomplete. Escala: x = 50,0 y = 50,0, z = 50,0.
    * Model_Platonic_BaseModuleIncomplete. Escala: x = 0,13, y = 0,13, z = 0,13.
    * Octa_BaseModuleIncomplete. Escala: x = 0,13. y = 0.13; z =0.13.
    * TheModule_BaseModuleIncomplete. Escala: x = 0,03, y = 0,03, z = 0,03.

    ![mrlearning-base-CH4-1-Step5. png](images/mrlearning-base-ch4-1-step5.png)

6. Agregue tres cubos a la escena. Haga clic con el botón secundario en el objeto 3DObjectCollection, seleccione objeto 3D y, a continuación, seleccione cubo. Establece la escala en x = 0.14; y = 0.14; z = 0.14. Repita este paso dos veces más para crear un total de tres cubos. Como alternativa, puede duplicar el cubo dos veces para un total de tres cubos. También puedes usar los tres cubos prefabricados preparados de Assets>BaseModuleAssets>Base Module Prefabs (Recursos>RecursosDeMóduloBase>Objetos prefabricados del módulo base) y seleccionar GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete y OrangeCube_BaseModuleIncomplete.

    ![mrlearning-base-CH4-1-Step6. png](images/mrlearning-base-ch4-1-step6.png)

7. Organice la colección de objetos para formar una cuadrícula, a través del procedimiento descrito en la [Lección 2](mrlearning-base-ch2.md), mediante la colección de objetos Grid de MRTK. Consulte la imagen siguiente para obtener un ejemplo de la configuración de los objetos en una cuadrícula de 3x3.

    ![mrlearning-base-CH4-1-STEP7. png](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    >Es posible que observe que algunos de los objetos están fuera del centro, como los objetos de la imagen anterior. Esto se debe a que los recursos prefabricados o los objetos pueden tener objetos secundarios sin alinear. Puedes realizar los ajustes de posición necesarios en los objetos o los objetos secundarios para alinear la cuadrícula correctamente.

### <a name="manipulating-3d-objects"></a>Manipulación de objetos 3D

1. Agrega la capacidad de manipular un cubo. Para agregar la capacidad de manipular objetos 3D, haga lo siguiente:
    * Seleccione el objeto 3D que desea manipular en la jerarquía (es decir, uno de los cubos).
    * Haga clic en Agregar componente.
    * Buscar "manipulación"
    * Seleccionar controlador de manipulación
    * Repita el procedimiento con todos los objetos 3D del objeto 3DObjectCollection, pero no con el propio 3DObjectCollection.
    * Asegúrese de que todos los objetos 3D tengan un Colisionador de cuadro o Colisionador (agregar Colisionador de cuadro de > de componentes).

    ![Imagen de la lección 4, capítulo 2, paso 1](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    >El controlador de manipulación es un componente que le permite ajustar la configuración de cómo se comportan los objetos cuando se manipulan. Esto incluye la rotación, el escalado, el movimiento y la restricción de movimiento en un eje específico.

2. Restringe un cubo para que solo se pueda escalar. Seleccione un cubo en el objeto 3DObjectCollection. En el panel Inspector, junto a tipo de manipulación dos manos, haga clic en el menú desplegable y seleccione escalar. Esto hace que el usuario solo pueda cambiar del cubo el tamaño.

    ![Imagen de la lección 4, capítulo 2, paso 2](images/Lesson4_Chapter2_step2im.PNG)

3. Cambia el color de cada cubo para que los podemos diferenciar.
    * Vaya al panel Proyecto y desplácese hacia abajo hasta que vea MixedRealityToolkit. SDK y, a continuación, selecciónelo.
    * Seleccione la carpeta activos estándar.
    * Haga clic en la carpeta materiales.
    * Arrastra un material distinto a cada cubo.

    >[!NOTE]
    >Para los cubos, puedes elegir cualquier color. En este ejemplo, se usan glowingcyan, glowingorange y Green. Puedes también experimentar con otros colores. Para agregar el color al cubo, haga clic en el cubo que desea cambiar y, a continuación, arrastre el material al campo material del representador de malla en el panel Inspector del cubo.

    ![Imagen de la lección 4, capítulo 2, paso 3](images/Lesson4_Chapter2_step3im.PNG)

4. Seleccione otro cubo en el objeto 3DObjectCollection y conviértalo de modo que su movimiento esté restringido a una distancia fija desde el encabezado. Para ello, a la derecha de la etiqueta en movimiento de restricción, haga clic en el menú desplegable y seleccione corregir distancia en el encabezado. Esto ajusta el cubo para que se encuentre dentro de su campo de visión.

    ![Imagen de la lección 4, capítulo 2, paso 4](images/Lesson4_chapter2_step4im.PNG)

    El objetivo de los siguientes pasos es habilitar la captación e interacción con nuestros objetos 3D y la aplicación de diferentes configuraciones de manipulación.

5. Seleccione el objeto queso y, a continuación, haga clic en Agregar componente en el panel Inspector.

6. Busque en el cuadro de búsqueda para que se capte la interacción cercana y seleccione el script. Este componente permite a los usuarios ponerse en contacto con los objetos con manos con seguimiento. Los objetos también se pueden manipular desde una distancia, a menos que la casilla permitir manipulación lejana esté desactivada, tal como se indica en un círculo verde en la imagen siguiente.

    ![Imagen de la lección 4, capítulo 2, paso 6](images/Lesson4_Chapter2_step6im.PNG)

7. Agregue Near Interaction captable al objeto OCTA, el objeto Platonic, Earth Core, el módulo lunar y la taza de café repitiendo los pasos 5 y 6 en esos objetos.

8. Deshabilita la manipulación lejana para el objeto Octa. Para ello, seleccione el OCTA en la jerarquía y desactive la casilla permitir la manipulación lejana (marcada con un círculo verde). Esto hace que los usuarios solo puedan interactuar con el OCTA directamente mediante las manos con seguimiento.

    >[!NOTE]
    >Para obtener la documentación completa del componente de controlador de manipulación y su configuración asociada, consulte la [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).

9. Asegúrese de que se ha agregado a la tierra Core, el módulo lunar y la taza de café (consulte el paso 7).

10. Para el módulo lunar, cambie la configuración del controlador de manipulación de modo que gire alrededor del centro del objeto para la interacción cercana y lejana, tal como se muestra en la imagen siguiente.

    ![Imagen de la lección 4, capítulo 2, paso 10](images/Lesson4_chapter2_step10im.PNG)

11. En el núcleo de la tierra, cambie el comportamiento de la versión a nada. Esto lo convierte en una vez que el núcleo de la tierra se suelta del agarre del usuario, no se sigue moviendo.

    ![Imagen de la lección 4, capítulo 2, paso 11](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    >Esta configuración es útil en escenarios como, por ejemplo, la creación de una bola que puede iniciar. Manteniendo la velocidad adecuada y la velocidad angular para asegurarse de que una vez que se suelta la bola, continuará avanzando a la velocidad en la que se lanzó; similar al comportamiento de una bola física.

### <a name="adding-bounding-boxes"></a>Agregar rectángulos de selección

Los cuadros de límite facilitan y simplifican la manipulación de objetos con una mano para la manipulación directa (cerca de la interacción) y la manipulación basada en rayos (interacción lejana). Los cuadros de límite proporcionan controladores que se pueden capturar para escalar y girar objetos a lo largo de un eje específico.

>[!NOTE]
>Antes de poder agregar un cuadro de límite a un objeto, primero debe tener un Colisionador en el objeto (por ejemplo, un Colisionador de cuadro), como se explicó anteriormente en esta lección. Se pueden agregar colisiones seleccionando el objeto y, en el panel Inspector del objeto, seleccionando Agregar componente > Box Colisionador.

1. Agregue un Colisionador de cuadro al objeto de la tierra, si aún no existe uno. El Colisionador de Box y el programa de instalación no son necesarios, si se usa el recurso prefabricado proporcionado en la carpeta de recursos del módulo base según las instrucciones proporcionadas. En el caso de la tierra Core, agregamos el Colisionador de cajas al objeto, node_id30, que se encuentra debajo del núcleo de la tierra, tal como se muestra en la imagen siguiente. Seleccione node_id30 en la pestaña inspector del objeto, haga clic en Agregar componente y busque Box Colisionador.

    ![Imagen de la lección 4, capítulo 3, paso 1](images/Lesson4_Chapter3_step1im.PNG)

    ![Imagen de la lección 4, capítulo 3, paso 2](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    >Asegúrese de ajustar el tamaño del Colisionador de caja para que no sea demasiado grande o demasiado pequeño. Debe ser aproximadamente del mismo tamaño que el objeto que rodea (en este ejemplo, el Earth Core). Ajuste el Colisionador de Box según sea necesario; para ello, seleccione la opción Editar Colisionador en el Colisionador de Box. Puede cambiar los valores x, y y z o arrastrar los controladores de rectángulo de selección en la ventana de escena del editor.

    ![Imagen de la lección 4, capítulo 3, nota](images/Lesson4_Chapter3_noteim.PNG)

2. Agregue un cuadro de límite al objeto de node_id30 de la base de la tierra. Para ello, seleccione el objeto de node_id30 de 3DObjectCollection. En la pestaña inspector, haga clic en Agregar componente y busque cuadro de límite. Asegúrate de que el rectángulo de selección, el colisionador de cuadro y los scripts de manipulación (Manipulation Handler [Controlador de manipulación] y Near Interaction Grabbable [Interacción próxima: agarrar]) se encuentran en el mismo objeto del juego.

3. En la sección comportamiento del cuadro de límite, seleccione Activar al iniciar en la lista desplegable activación. Para revisar detalles adicionales relacionados con las distintas opciones de activación y otras opciones del cuadro de límite, consulte la [documentación del cuadro de límite de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

    *En los siguientes pasos, también cambiaremos el aspecto del cuadro de límite ajustando el material del cuadro predeterminado, el material mientras se está captando, así como la visualización de los manipuladores de la esquina y del lado. MRTK contiene varias opciones para personalizar el cuadro de límite.*

4. En el panel Proyecto, busque "BoundingBox" y verá una lista de materiales indicados por una esfera azul en los resultados de la búsqueda como se muestra en la imagen siguiente.

5. Arrastre el material BoundingBox a la ranura de material del cuadro en el componente del cuadro de límite. También puede captar el material boundingboxgrabbed y colocarlo en la ranura de material captada por Box del componente de cuadro de límite.

    ![mrlearning-base-CH4-3-Step5. png](images/mrlearning-base-ch4-3-step5.png)

6. Arrastre el MRTK_BoundingBox_ScaleHandle recurso prefabricado a la ranura de recurso prefabricado de control de escala y el recurso prefabricado de la MRTK_BoundingBox_RotateHandle a la ranura del controlador de rotación en el componente del cuadro de enlace.

    ![mrlearning-base-CH4-3-Step6. png](images/mrlearning-base-ch4-3-step6.png)

7. Asegúrate de que el rectángulo de selección apunta al objeto correcto. En el componente de cuadro de límite, hay el objeto de destino y los límites invalidan los scripts. Arrastre el objeto que tiene el cuadro de límite alrededor a ambas ranuras. En este ejemplo, arrastre el objeto node_id30 a ambas ranuras, tal como se muestra en la imagen siguiente.

    ![mrlearning-base-CH4-3-STEP7. png](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    >Al iniciar o reproducir la aplicación, el objeto estará rodeado por un marco azul. Puedes arrastrar las esquinas de este para cambiar el tamaño del objeto. Si desea que los manipuladores de escalado y los controladores de giro sean más grandes y más visibles, se recomienda usar la configuración predeterminada del cuadro de límite (evitando los pasos del 4 al 6).

8. Para volver a la visualización predeterminada del cuadro de límite, en el panel Inspector del objeto del cuadro de límite, seleccione el controlador de giro recurso prefabricado y presione SUPR para quitarlo. Al entrar en el modo de reproducción, Wou verá una visualización de cuadro de límite similar a la imagen siguiente.

    ![mrlearning-base-CH4-3-step8. png](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    >Las visualizaciones de cuadro de límite solo aparecen en el modo de reproducción.

### <a name="adding-touch-effects"></a>Agregar efectos de toque

En este ejemplo vamos a reproducir un efecto de sonido al tocar un objeto con la mano.

1. Agrega un componente de origen de audio al objeto de juego. Seleccione el objeto OCTA en la jerarquía de la escena. En el panel Inspector, haga clic en el botón Agregar componente, busque y seleccione origen de audio. Usaremos este origen de audio para reproducir un efecto de sonido más adelante.

    >[!NOTE]
    >Asegúrese de que el objeto OCTA tiene un Colisionador de cuadro en él.

2. Agregue el componente que se toque en la interacción cercana. Haga clic en el botón Agregar componente en el panel Inspector y busque Near Interaction Touchable. Selecciónalo para agregar el componente.

    >[!NOTE]
    >Anteriormente, agregamos Near Interaction acpuesto. La diferencia entre este y el toque de interacción cercano es que la interacción capturable está pensada para que un objeto se capte y se interactúe con él. El componente táctil está pensado para el objeto que se va a tocar. Ambos componentes se pueden usar conjuntamente para una combinación de interacciones.

    ![Imagen de la lección 4, capítulo 4, pasos 1-2](images/Lesson4_chapter4_step1-2im.PNG)

3. Agregue el script Touch de interacción táctil. Al igual que en el paso anterior, haga clic en Agregar componente y busque el toque de interacción manual para agregarlo.

    Tenga en cuenta que tiene tres opciones con el script:
    * En Touch Completed: se desencadena cuando se toca y libera el objeto
    * En Touch Started: se desencadena cuando se toca el objeto
    * En Touch Updated: se desencadena periódicamente mientras su mano toca el objeto

    En este ejemplo, vamos a trabajar con la opción on Touch Started.

    >[!NOTE]
    >Este script se incluye con el paquete BaseModuleAssets Unity que importó al principio de este tutorial y no se incluye en el MRTK original.

4. Haga clic en el botón + en la opción on Touch Started y arrastre el objeto OCTA al campo vacío.

    ![mrlearning-base-CH4-4-Step4. png](images/mrlearning-base-ch4-4-step4.png)

5. En la lista desplegable que indica que no hay función, seleccione AudioSource > PlayOneShot. Agregaremos un clip de audio a este campo con los siguientes conceptos:

    * MRTK proporcionan una pequeña lista de clips de audio. No dude en explorarlas en el panel del proyecto. Los encontrará en los activos > MixedRealityToolkit. SDK > recursos estándar > carpeta de audio.
    * En este ejemplo, vamos a usar el clip de audio MRTK_Gem.
    * Para agregar un clip de audio, simplemente arrastre el clip que desee desde el panel Proyecto hasta el campo AudioSource. PlayOneShot.

    ![mrlearning-base-CH4-4-Step5. png](images/mrlearning-base-ch4-4-step5.png)

   Ahora, cuando el usuario llegue y toque el objeto OCTA, se reproducirá la pista de audio MRTK_Gem. El script Touch de interacción táctil también ajustará el color del objeto cuando se toca.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a organizar objetos 3D en una colección de cuadrículas y cómo manipular estos objetos (escalado, rotación y movimiento) mediante la interacción aproximada (captando directamente con manos sometidas a seguimiento) e interacción lejana (mediante rayos de miración o rayos de mano). También ha aprendido a colocar rectángulos de selección alrededor de objetos 3D y ha aprendido a usar y personalizar Gizmos en los cuadros de límite. Por último, has aprendido a desencadenar eventos al tocar objetos.

[Lección siguiente: 6. explorar opciones de entrada avanzadas](mrlearning-base-ch5.md)
