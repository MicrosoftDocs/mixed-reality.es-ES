---
title: 'Módulo base de aprendizaje de MR: Configuración de la interfaz de usuario, el seguimiento de la mano y Mixed Reality Toolkit'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730951"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>Módulo base de aprendizaje de MR: Configuración de la interfaz de usuario, el seguimiento de la mano y Mixed Reality Toolkit

En la lección anterior, aprendiste algunas de las funcionalidades que ofrece MRTK e iniciaste tu primera aplicación para HoloLens 2. En esta lección, aprenderás a crear y organizar los botones junto con los paneles de texto de la interfaz de usuario, y a usar la interacción predeterminada (entrada táctil) para interactuar con cada botón. También explorarás la incorporación de acciones y efectos sencillos, como cambiar el tamaño, el sonido y color de los objetos. En este módulo se presentan los conceptos básicos sobre cómo modificar los perfiles de MRTK; para empezar, se desactiva la visualización de la malla espacial. 

## <a name="objectives"></a>Objetivos

* Personalizar y configurar los perfiles de Mixed Reality Toolkit
* Interactuar con hologramas mediante botones y elementos de la interfaz de usuario
* Entrada e interacciones básicas del seguimiento de la mano

## <a name="instructions"></a>Instrucciones

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Configuración de los perfiles de Mixed Reality Toolkit (opción para cambiar la visualización de orientación espacial)
En esta sección, aprenderás a personalizar y configurar los perfiles predeterminados de Mixed Reality Toolkit mediante el ajuste de la opción de visualización de la malla de orientación espacial. Puedes seguir estos mismos principios para ajustar cualquier parámetro o valor de los perfiles de MRTK.

1. Selecciona Mixed-Reality Toolkit (MRTK) en la jerarquía "BaseScene". En el panel del inspector, busca "Mixed Reality Toolkit Script" (Script de Mixed Reality Toolkit) y selecciona el "perfil activo" como se muestra en la ilustración siguiente. Haz doble clic en él para abrirlo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Nota: De forma predeterminada, los perfiles de MRTK no son editables. Son plantillas de perfil predeterminadas con las que puedes copiar y personalizar perfiles. Hay varias capas de personalización y perfiles, por lo que es habitual copiar y personalizar varios perfiles al realizar una o varias configuraciones.
>
>Para más información sobre los perfiles de MRTK y su arquitectura, consulta la [documentación de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Crea una copia del perfil predeterminado para personalizarlo. Para copiar un perfil predeterminado, haz clic en el botón "Copy & Customize" (Copiar y personalizar) (consulta la imagen). Se crea una copia del perfil de MRTK. Con tu propia copia del perfil de MRTK, ahora tienes la posibilidad de personalizar cualquier configuración de este perfil. También deberás repetir el paso de copiar y personalizar con los perfiles adicionales anidados en este perfil, como se describe en los pasos siguientes.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Deshabilita la visibilidad de la malla de orientación espacial. Para ello, busca "Spatial Awareness System Settings" (Configuración del sistema de orientación espacial) como se muestra en la imagen. Haz clic en el botón "Clone" (Clonar) a la derecha de "Spatial Awareness System Profile" (Perfil del sistema de orientación espacial) para reemplazar el perfil predeterminado por una copia personalizable. Si aparece una ventana emergente, presiona el botón "Clone" (Clonar), como se muestra en la segunda imagen a continuación.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Crea una copia personalizada del observador predeterminado de la malla espacial de Mixed Reality. Haz clic en la flecha abajo junto a "Windows Mixed Reality Spatial Mesh Observer" (Observador de la malla espacial de Windows Mixed Reality) para ver opciones adicionales. En estas opciones, verás que el observador predeterminado de la malla espacial de Mixed Reality aparece atenuado (no editable). Debes reemplazar este perfil predeterminado por una copia personalizable para poder editarlo. Haz clic en el botón de la derecha (marcado con una flecha verde) para clonar una copia.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. A continuación, vas a ajustar la configuración de la opción de visualización a "Occlusión" (Oclusión). De esta forma la malla espacial se hace invisible, pero siguen estando ocultos los objetos del juego que hay detrás de ella (esto se conoce como oclusión).

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Nota: Aunque la malla de asignación espacial no está visible, sigue existiendo y puedes interactuar con ella. Cualquier holograma que haya detrás de la malla de asignación espacial (por ejemplo, un holograma detrás de la pared visible) no será visible debido a la configuración de oclusión.

Enhorabuena. Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puedes ver, para modificar la configuración de MRTK debes crear copias de los perfiles predeterminados para poder editarlos. Siempre podrás volver a los perfiles predeterminados (que no son editables) cuando quieras crear un perfil con una nueva configuración o hacer referencia a estos perfiles. Hay numerosas opciones que puedes ajustar. Para obtener una referencia completa a la configuración de perfiles de MRTK, consulta la documentación de MRTK aquí: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html.

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botones de interacción y gestos de seguimiento de la mano
En esta sección, aprenderás a usar el seguimiento de la mano para presionar un botón de interacción.

1. Selecciona "Assets" (Recursos) en la carpeta de proyectos.

2. En la barra de búsqueda, escribe "pressablebutton".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Arrastra el objeto prefabricado (representado por un cuadro azul) denominado "PressableButton" a la jerarquía. 

   > Nota: Si recibes un mensaje sobre la importación de TMP Essentials, impórtalo en este momento. Si TMP Essentials ya no formaba parte del proyecto, puede que debas repetir este paso después de importarlo o puede que el texto del botón no aparezca.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Haz doble clic en el objeto de juego "PressableButton" (que debe estar en la jerarquía BaseScene) para verlo en tu escena, como se muestra en la imagen siguiente (los gráficos de botón pueden ser diferentes a los de la imagen siguiente). 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. En el panel del inspector, haz clic en "Add Event" (Agregar evento) para proporcionar al botón un evento al que responder cuando se presiona. En la opción que aparece, selecciona el menú desplegable. Selecciona "InteractableOnPressReciever". Esto permite que el botón responda a un evento presionado cuando una mano con seguimiento presiona el botón.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Agrega un cubo a la escena. Haz clic con el botón derecho en el área de la jerarquía, selecciona un objeto 3D y luego haz clic en "Cube" (Cubo). Ahora, debe aparecer un cubo en la pantalla. Será muy grande así que ajusta las coordenadas (mientras aún sigue seleccionado cubo en el área de la jerarquía) para reducir el tamaño. Establece los valores de escala en x = 0,1, y = 0,1 y z = 0,1. Asegúrate de colocar el cubo en la escena cerca del botón que se puede presionar, pero sin que se solape con él. En la imagen siguiente, la posición del cubo es x = 0, y = 0,2 y z = 1. 

   > Nota: En general, 1 unidad en Unity equivale aproximadamente a 1 metro en el mundo físico. Existen excepciones a esto, por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. En este paso configurarás el cubo para que cambie de color cuando se presiona el botón. Selecciona PressableButton en el menú "BaseScene". En el panel del inspector, en el cuadro "Select Event Type" (Seleccionar tipo de evento), haz clic en el botón "+". Arrastra el cubo desde el menú "BaseScene" hasta el cuadro "Runtime Only" (Solo en tiempo de ejecución), tal como se muestra en la imagen siguiente:

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Haz clic en la lista desplegable que pone "No Function" (Ninguna función). Selecciona "MeshRenderer" y, luego, "Material material". Esto permite cambiar el material cuando se presiona el botón. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Dirígete al panel de proyectos y busca el material por el que quieres cambiarlo. En este ejemplo, vas a usar el material "MRTK_Standard_Cyan", que puedes encontrar si escribes "cyan" en la barra de búsqueda de la pestaña del proyecto (MRTK incluye muchos materiales y colores para elegir). Arrastra el material al cuadro situado debajo de "MeshRenderer.material". Encontrarás los materiales de MRTK en Assets>MixedRealityToolkit.SDK>StandardAssets>Materials (Recursos > MixedRealityToolkit.SDK > RecursosEstándar > Materiales).

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

El evento ahora está establecido para que cuando se presiona el botón, el cubo cambie de color según el material especificado. En este ejemplo, el cubo cambiará al color aguamarina.

8. A continuación, vas a configurar la acción de liberación para que tras esta, el botón vuelva a su color predeterminado. Repite el paso 7 (el paso anterior), pero esta vez con el evento "OnRelease" en lugar del evento "OnPress", tal como se muestra en la imagen siguiente.

9.  En el panel del proyecto, busca el material que adopte el cubo como predeterminado tras soltar el botón (en nuestro caso, elegimos MRTK_Standard_LightGray.) Arrastra el material al cuadro que aparece debajo del campo "MeshRenderer.material".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Ahora, cuando se presiona el botón, debería cambiar a un nuevo color (por ejemplo, cian) y, cuando se suelta, volver al color predeterminado especificado (por ejemplo, gris claro.) Presiona el botón "Play" (Reproducir) en la parte superior de la pantalla para probarlo en el editor o impleméntalo en HoloLens 2 para probarlo. Para más información sobre la simulación en el editor, incluida la simulación de la mano, lee la [página de documentación de simulación del MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creación de un panel de botones con la colección de objetos de cuadrícula de MRTK

En esta sección, aprenderás a alinear automáticamente varios botones en una interfaz de usuario nueva mediante la herramienta GridObjectCollection de MRTK.

1. Duplica el botón de la sección anterior hasta que tengas cinco botones. Hay varias maneras de hacerlo:
- Haz clic con el botón derecho en el botón y haz clic en "Copy" (Copiar), luego, baja hasta situarte debajo del botón y vuelve a hacer clic con el botón derecho y haz clic en "Paste" (Pegar). 
- Haz clic con el botón derecho en el botón y haz clic en "Duplicate" (Duplicar). 
- Para usar el comando del teclado, haz clic en el cubo y presiona "Ctrl+D" en el teclado.

Repite este paso hasta que haya cinco botones en total (consulta las 5 flechas rojas de la imagen siguiente).

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupa los botones debajo de un objeto de juego primario. Para tener los botones en la colección de la cuadrícula, debes agruparlos en un objeto primario común. Haz clic con el botón derecho en el jerarquía y haz clic en "Create empty" (Crear vacío). Se crea un objeto de juego vacío en el que colocar todos los botones. Se mostrará como "gameObject". Haz clic con el botón derecho y cambia su nombre por "ButtonCollection".

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mueve todos los botones a la nueva colección. Para ello, selecciona los cinco botones de objeto de la jerarquía y arrástralos al objeto de juego "ButtonCollection", tal como se muestra en la imagen siguiente. Sugerencia: Para seleccionar varios elementos, mantén presionada la tecla Ctrl al tiempo que seleccionas los elementos.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Agrega el componente "Grid Object Collection" (Colección de objetos de cuadrícula) de MRTK a la colección de botones.  Para ello, selecciona el objeto primario "ButtonCollection" y, en el panel del inspector, haz clic en el botón "Add Component" (Agregar componente). A continuación, busca "Grid Object Collection" (Colección de objetos de cuadrícula) en la barra de búsqueda y selecciónalo cuando aparezca en la lista.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

El componente Grid Object Collection (Colección de objetos de cuadrícula) permite organizar botones o cualquier conjunto de objetos en una nueva fila, columna o cuadrícula. Este es uno de los bloques de creación proporcionados por MRTK que ofrece una manera rápida y sencilla de crear atractivas interfaces de usuario.

5. Configura la colección de objetos de cuadrícula. Para garantizar que todos los botones miran al usuario, selecciona "Orient type" (Tipo de orientación) y, luego, selecciona "Face parent forward" (Orientar primario hacia adelante) (como se muestra en la imagen). A continuación, cambia el tamaño de celda para establecer el espacio entre los botones. Comienza con 0,12 unidades por 0,12 unidades para el ancho y el alto de celda, como se muestra en la imagen siguiente. Es posible que debas ajustar estos valores, según los recursos de objeto o botón elegidos. Asegúrate de que "Rows" (Filas) está establecido en 1. A continuación, haz clic en "Update Collection" (Actualizar colección); la escena se parecerá a la siguiente imagen. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Nota: Según la orientación de los objetos secundarios o del objeto primario, es probable que debas ajustar la orientación de manera diferente en futuros proyectos. También, puede que los campos de ancho y alto de celda se deban definir de forma diferente, según el tamaño de los objetos de la colección.

### <a name="adding-text-into-your-scene"></a>Adición de texto a la escena

En esta sección, aprenderás a agregar texto a tus experiencias de realidad mixta y a editarlo. Si no lo has hecho ya, asegúrate de tener habilitado TextMeshPro en Unity mediante las instrucciones [aquí](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation) descritas.

1. Selecciona el objeto primario "ButtonCollection" y haz clic con el botón derecho en la colección. Expande "3D object" (Objeto 3D) en el menú desplegable y, luego, selecciona "TextMeshPro - Text" (TextMeshPro: Texto). Verás un objeto TextMeshPro en la colección de botones, tal como se muestra en la imagen siguiente.

![Lección 2, capítulo 4, paso 1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lección 2, capítulo 4, paso 1b](images/Lesson2_Chapter4_Step1b.JPG)

2. En el campo de texto del componente TextMeshPro (que se encuentra en el panel del inspector, tal como se muestra a continuación), escriba "texto de colección de botones". El texto aparecerá en la escena, pero quedará oculto detrás de los botones o porque el tamaño no es correcto.

![Lección 2, capítulo 4, paso 2](images/Lesson2_Chapter4_Step2.JPG)

3. Para mejorar el tamaño y la ubicación del texto para facilitar la legibilidad, ajusta el campo "Font size" (Tamaño de fuente) en el componente TextMeshPro para cambiar el tamaño de la fuente. También deberás ajustar la posición "Rect Transform" (Transformación recta) y la escala, tal como se muestra en la imagen siguiente. Consulta las imágenes siguientes para ver los valores usados en la configuración del texto, y usa libremente estos valores como punto de partida para mejorar el tamaño y la ubicación del campo de texto.

![Lección 2, capítulo 4, paso 3](images/Lesson2_Chapter4_Step3.JPG)
![Lección 2, capítulo 4, paso 4](images/Lesson2_Chapter4_Step4.JPG)

5. Para modificar los valores de texto en los objetos de botón, haz clic en la flecha situada junto a cualquier botón para expandirlo y dirígete al objeto "SeeItSayItLabel" y, luego, a "TextMeshPro", donde puedes editar el texto de los botones, tal como se ha descrito en los pasos anteriores.

![Lección 2, capítulo 4, paso 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Enhorabuena
En esta lección, has aprendido a copiar, personalizar y configurar un perfil de MRTK (es decir, la visibilidad de la malla de orientación espacial). También has aprendido a interactuar con un botón para desencadenar eventos mediante manos con seguimiento en HoloLens 2. Por último, has aprendido a crear una sencilla interfaz de usuario mediante el componente de colección de objetos de cuadrícula de MRTK de Text Mesh Pro de Unity.

[Próxima lección: Colocación de contenido dinámico y solucionadores](mrlearning-base-ch3.md)

