---
title: 'Módulo base de aprendizaje de MR: Configuración de la interfaz de usuario, el seguimiento de la mano y Mixed Reality Toolkit'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 5275e862d2dec78c98510f754162961c80e9e4b8
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387714"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta 

En la lección anterior, aprendió sobre algunas de las funcionalidades que el kit de herramientas de realidad mixta (MRTK) tiene que ofrecer al iniciar su primera aplicación para HoloLens 2. En la siguiente lección aprenderá a crear y organizar botones junto con los paneles de texto de la interfaz de usuario y a usar interacción predeterminada (Touch) para interactuar con cada botón. También explorarás la incorporación de acciones y efectos sencillos, como cambiar el tamaño, el sonido y color de los objetos. Este módulo presentará conceptos básicos sobre la modificación de perfiles de MRTK, empezando por desactivar la visualización de malla espacial. 

## <a name="objectives"></a>Objetivos

* Personalizar y configurar los perfiles de Mixed Reality Toolkit
* Interacción con hologramas mediante elementos y botones de la interfaz de usuario
* Entrada e interacciones básicas del seguimiento de la mano

## <a name="instructions"></a>Instrucciones

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Configuración de los perfiles de Mixed Reality Toolkit (opción para cambiar la visualización de orientación espacial)
En esta sección, aprenderá a personalizar y configurar los perfiles predeterminados de MRTK ajustando la opción de visualización de la malla de reconocimiento espacial. Puedes seguir estos mismos principios para ajustar cualquier parámetro o valor de los perfiles de MRTK.

1. Seleccione el kit de herramientas de realidad mixta (MRTK) de la jerarquía de BaseScene. En el panel Inspector, busque el script Mixed Reality Toolkit y seleccione el perfil activo como se muestra en la ilustración siguiente. Haz doble clic en él para abrirlo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Nota: De forma predeterminada, los perfiles de MRTK no son editables. Estas son plantillas de perfil predeterminadas que puede copiar y personalizar. Existen varios niveles de personalización y perfiles. Por lo tanto, es una práctica estándar copiar y personalizar varios perfiles al configurar una o más opciones.
>
>Para obtener más información sobre los perfiles de MRTK y su arquitectura, visite la [documentación de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Crea una copia del perfil predeterminado para personalizarlo. Para copiar un perfil predeterminado, haga clic en copiar & personalizar (vea la imagen). Se crea una copia del perfil de MRTK. Con tu propia copia del perfil de MRTK, ahora tienes la posibilidad de personalizar cualquier configuración de este perfil. También deberá repetir el paso copiar y personalizar para cualquier perfil adicional anidado bajo este perfil, tal como se describe en los pasos siguientes.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Deshabilita la visibilidad de la malla de orientación espacial. Para ello, busque la configuración del sistema de reconocimiento espacial tal como se muestra en la imagen. Haga clic en el botón clonar a la derecha del perfil del sistema de reconocimiento espacial para reemplazar el perfil predeterminado por una copia personalizable. Si aparece una ventana emergente, presione el botón clonar, tal como se muestra en la segunda imagen siguiente.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Crea una copia personalizada del observador predeterminado de la malla espacial de Mixed Reality. Haga clic en la flecha hacia abajo junto al observador de malla espacial de realidad mixta de Windows para ver opciones adicionales. En estas opciones, verá el observador de malla espacial de la realidad mixta predeterminada que está atenuado (no editable). Debes reemplazar este perfil predeterminado por una copia personalizable para poder editarlo. Haga clic en el botón situado a la derecha (marcado con una flecha verde) para clonar una copia.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. A continuación, vas a ajustar la configuración de la opción de visualización a "Occlusión" (Oclusión). Esto hace que la malla espacial sea invisible, pero todavía oculta objetos de juego detrás de la malla espacial, también conocido como oclusión.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Nota: Aunque la malla de asignación espacial no está visible, sigue existiendo y puedes interactuar con ella. Los hologramas detrás de la malla de asignación espacial, como un holograma detrás de la pared visible, no estarán visibles debido a la configuración de la oclusión.

¡Enhorabuena! Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puedes ver, para modificar la configuración de MRTK debes crear copias de los perfiles predeterminados para poder editarlos. Siempre tendrá los perfiles predeterminados, que no son editables, para volver a si desea crear un perfil con una nueva configuración o puede volver a consultar los perfiles predeterminados. Hay numerosas opciones que puedes ajustar. Para obtener una referencia completa a la configuración de perfiles de MRTK, consulta la documentación de MRTK aquí: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html.

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botones de interacción y gestos de seguimiento de la mano
En esta sección, aprenderá a usar el seguimiento de manos para presionar un botón que se puede presionar.

1. Seleccione recursos en la carpeta proyectos.

2. En la barra de búsqueda, escribe "pressablebutton".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Arrastra el objeto prefabricado (representado por un cuadro azul) denominado "PressableButton" a la jerarquía. 

   > Nota: Si recibe un mensaje acerca de la importación de TMP Essentials, impórtelo en este momento. Si TMP Essentials no formaba parte del proyecto, es posible que deba repetir este paso después de importar TMP Essentials; de lo contrario, es posible que no aparezca el texto del botón.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Haga doble clic en el objeto de juego PressableButton, que ahora debe estar en la jerarquía de BaseScene, para verlo en la escena, tal como se muestra en la imagen siguiente. Los gráficos de botones pueden aparecer distintos de los de la imagen siguiente. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. En el panel Inspector, haga clic en agregar evento para dar al botón que un evento debe responder cuando se inserte. En la opción que aparece, seleccione el menú desplegable y seleccione InteractableOnPressReciever. Esto permite que el botón responda a un evento presionado cuando una mano con seguimiento presiona el botón.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Agrega un cubo a la escena. Haga clic con el botón derecho en el área jerarquía, seleccione un objeto 3D y, a continuación, haga clic en cubo. Ahora, debe aparecer un cubo en la pantalla. Aparecerá muy grande. Puede ajustar las coordenadas (mientras el cubo todavía está seleccionado en el área de jerarquía) para reducir el tamaño. Establece los valores de escala en x = 0,1, y = 0,1 y z = 0,1. Asegúrate de colocar el cubo en la escena cerca del botón que se puede presionar, pero sin que se solape con él. En la imagen siguiente, la posición del cubo es x = 0, y = 0,2 y z = 1. 

   > Nota: En general, 1 unidad en Unity equivale aproximadamente a 1 metro en el mundo físico. Existen excepciones a esto, por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. En este paso configurarás el cubo para que cambie de color cuando se presiona el botón. Seleccione PressableButton en el menú BaseScene. En el panel Inspector, en el cuadro Seleccionar tipo de evento, haga clic en el botón +. Arrastre el cubo desde el menú BaseScene al cuadro solo tiempo de ejecución como se muestra en la imagen siguiente.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Haga clic en la lista desplegable que indica que no hay ninguna función. Seleccione MeshRenderer y, a continuación, material material. Esto le permite cambiar el material cuando se presiona el botón. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Vaya al panel Proyecto y busque el material al que desea cambiarlo. En este ejemplo, va a usar el material MRTK_Standard_Cyan, que se encuentra escribiendo "aguamarina" en la barra de búsqueda de la pestaña proyecto. (MRTK incluye muchos materiales y colores entre los que elegir). Arrastre el material al cuadro debajo de MeshRenderer. material. Encontrarás los materiales de MRTK en Assets>MixedRealityToolkit.SDK>StandardAssets>Materials (Recursos > MixedRealityToolkit.SDK > RecursosEstándar > Materiales).

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

El evento ahora está establecido para que cuando se presiona el botón, el cubo cambie de color según el material especificado. En este ejemplo, el cubo cambiará al color aguamarina.

8. A continuación, vas a configurar la acción de liberación para que tras esta, el botón vuelva a su color predeterminado. Repita el paso 7 anterior. Pero esta vez con el evento unrelease en lugar del evento alpress, tal y como se muestra en la imagen siguiente.

9.  En el panel Proyecto, busque un material para que el cubo tenga como valor predeterminado al soltar el botón. En este caso, elegimos MRTK_Standard_LightGray. Arrastre el material al cuadro situado debajo del campo MeshRenderer. material.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Ahora, cuando se presiona el botón, cambia a un nuevo color, aguamarina. Al soltar el botón, se volverá a cambiar al color predeterminado especificado (por ejemplo, gris claro). Presione el botón reproducir en la parte superior de la pantalla para probarlo en el editor o realice la implementación en HoloLens 2 para probarlo. Para obtener más información sobre la simulación en el editor, incluida la simulación manual, lea la [Página de documentación de la simulación de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creación de un panel de botones con la colección de objetos de cuadrícula de MRTK

En esta sección, aprenderá a alinear automáticamente varios botones en una interfaz de usuario ordenada mediante la herramienta GridObjectCollection de MRTK.

1. Duplique el botón de la sección anterior hasta que tenga cinco botones. Hay varias maneras de hacerlo:
- Haga clic con el botón derecho en el botón y haga clic en copiar. Después, vaya a debajo del botón y haga clic con el botón derecho de nuevo y haga clic en pegar. 
- Haga clic con el botón derecho en el botón y haga clic en duplicar. 
- Use el comando de teclado haciendo clic en el cubo y presionando Ctrl D en el teclado.

Repita este paso hasta que tenga cinco botones; Vea las cinco flechas rojas de la imagen siguiente.

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupa los botones debajo de un objeto de juego primario. Para tener los botones en la colección de cuadrículas, debe agrupar los botones en un objeto primario común. Haga clic con el botón derecho en hiearachy y haga clic en crear vacío. Se crea un objeto de juego vacío en el que colocar todos los botones. Se muestra como gameObject. Haga clic con el botón derecho y cambie el nombre por ButtonCollection.

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mueve todos los botones a la nueva colección. Para ello, seleccione los cinco objetos de botón en la jerarquía y arrástrelos todos en el objeto de juego ButtonCollection como se muestra en la imagen siguiente. Sugerencia: Seleccione varios elementos manteniendo presionada la tecla Ctrl mientras selecciona los elementos.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Agregue el componente de colección de objetos de cuadrícula de MRTK a la colección de botones. Para ello, seleccione el objeto primario ButtonCollection. En el panel Inspector, haga clic en el botón Agregar componente. Busque la colección de objetos de cuadrícula en la barra de búsqueda y selecciónela cuando aparezca en la lista.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

El componente de colección de objetos de cuadrícula permite organizar botones o cualquier conjunto de objetos en una fila, columna o cuadrícula ordenada. Se trata de uno de los bloques de creación que proporciona el MRTK, que ofrece una manera rápida y sencilla de crear interfaces de usuario atractivas.

5. Configura la colección de objetos de cuadrícula. Para asegurarse de que todos los botones se encuentran en el usuario, seleccione orientar tipo. A continuación, seleccione la esfera principal hacia delante, tal como se muestra en la imagen siguiente. A continuación, cambia el tamaño de celda para establecer el espacio entre los botones. Empiece con 0,12 unidades por 0,12 unidades para el ancho de celda y el alto de celda, tal y como se muestra en la imagen siguiente. Es posible que deba ajustar estos valores, en función de los recursos de objeto y botón elegidos. Asegúrese de que filas está establecido en 1. Haga clic en actualizar colección. La escena tendrá un aspecto similar al de la siguiente imagen. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Nota: Según la orientación de los objetos secundarios o del objeto primario, es probable que debas ajustar la orientación de manera diferente en futuros proyectos. También, puede que los campos de ancho y alto de celda se deban definir de forma diferente, según el tamaño de los objetos de la colección.

### <a name="adding-text-into-your-scene"></a>Adición de texto a la escena

En esta sección, aprenderás a agregar texto a tus experiencias de realidad mixta y a editarlo. Si no lo has hecho ya, asegúrate de tener habilitado TextMeshPro en Unity mediante las instrucciones [aquí](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation) descritas.

1. Seleccione el objeto primario ButtonCollection y haga clic con el botón secundario en la colección. Expanda objeto 3D en el menú desplegable. A continuación, seleccione TextMeshPro-Text. Debería ver un objeto TextMeshPro en la colección de botones, tal como se muestra en la imagen siguiente.

![Lección 2, capítulo 4, paso 1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lección 2, capítulo 4, paso 1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Para mejorar el tamaño del texto y la ubicación para facilitar la lectura, ajuste el campo tamaño de fuente del componente TextMeshPro para cambiar el tamaño de la fuente. También tendrá que ajustar la posición y la escala de la transformación Rect, tal y como se muestra en la imagen siguiente. Consulte las imágenes siguientes para ver los valores usados para la configuración de texto. No dude en usar estos valores como punto de partida para mejorar aún más el tamaño y la posición del campo de texto.

![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)

3. En el campo de texto del componente TextMeshPro del panel Inspector, tal como se muestra a continuación. Escriba en el texto de la colección de botones. El texto aparece en la escena, pero se oculta detrás de los botones o el tamaño incorrecto.

![Lesson2 Chapter4 paso 2](images/Lesson2_Chapter4_Step2.JPG)
![Lesson2 Chapter4 Paso4](images/Lesson2_Chapter4_Step4.JPG)

4. Para modificar los valores de texto de los objetos de botón, haga clic en la flecha situada junto a cualquier botón para expandirlo y navegue hasta el objeto SeeItSayItLabel. Vaya a TextMeshPro, donde puede editar el texto en los botones tal y como se describe en los pasos anteriores.

![Lección 2, capítulo 4, paso 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Enhorabuena
En esta lección, has aprendido a copiar, personalizar y configurar un perfil de MRTK (es decir, la visibilidad de la malla de orientación espacial). También has aprendido a interactuar con un botón para desencadenar eventos mediante manos con seguimiento en HoloLens 2. Por último, has aprendido a crear una sencilla interfaz de usuario mediante el componente de colección de objetos de cuadrícula de MRTK de Text Mesh Pro de Unity.

[Próxima lección: Colocación de contenido dinámico y solucionadores](mrlearning-base-ch3.md)

