---
title: 'MR Learning Base mano de módulo: interfaz de usuario, realiza el seguimiento y mixto realidad configuración del Kit de herramientas'
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: 1530fd1a1ee06d01e8ab0cc009dfba03873c3427
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993643"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR Learning Base mano de módulo: interfaz de usuario, realiza el seguimiento y mixto realidad configuración del Kit de herramientas

En la lección anterior, aprendió a algunas de las capacidades que del MRTK tiene que ofrecer, iniciando su primera aplicación para el 2 de HoloLens. En esta siguiente lección obtendrá información sobre cómo crear y organizar botones junto con los paneles de texto de la interfaz de usuario y usar interacción predeterminada (toque) para interactuar con cada botón. También explorará la adición de acciones simples y efectos, como cambiar el tamaño, sonido y color de los objetos. Este módulo presentan los conceptos básicos sobre cómo modificar perfiles MRTK, empezando por si se desactiva la visualización de la malla espacial. 

## <a name="objectives"></a>Objetivos

* Personalice y configure los perfiles del Kit de herramientas de realidad mixta
* Interactuar con hologramas mediante los botones y elementos de interfaz de usuario
* Las interacciones y básico de entradas de seguimiento de la mano

## <a name="instructions"></a>Instrucciones

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Cómo configurar los perfiles del Kit de herramientas de realidad mixta (opción de visualización de cambio reconocimiento espaciales)
En esta sección obtendrá información sobre cómo personalizar y configurar los perfiles del Kit de herramientas de realidad mixta de forma predeterminada mediante el ajuste de la opción de visualización de la conciencia espacial malla. Puede seguir estos mismos principios para ajustar los valores o los valores en los perfiles de MRTK.

1. Seleccione Mixed Reality Kit de herramientas (MRTK) de la jerarquía "BaseScene". En el panel del inspector, busque la "Mixed Reality Kit de herramientas de secuencia de comandos" y seleccione el "perfil activo" como se muestra en la ilustración siguiente. Haga doble clic en él para abrirlo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>Nota: De forma predeterminada, los perfiles MRTK no son editables. Estos son desde el que puede copiar y personalizar las plantillas de perfil predeterminado. Hay varios niveles de personalización y perfiles, por lo que es una práctica estándar para copiar y personalizar varios perfiles al configurar una o más configuraciones.
>
>Para más información acerca de los perfiles MRTK y su arquitectura, visite la [documentación MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).

2. Crear una copia del perfil predeterminado para personalizarlo. Para copiar un perfil predeterminado, haga clic en la "copia & Personalizar" (consulte la imagen). Esto crea una copia del perfil MRTK. Con su propia copia del perfil MRTK, ahora tiene la capacidad de personalizar la configuración en este perfil. También necesitará Repita el paso de copia/personalizar para los perfiles adicionales anidados en este perfil, como se describe en los pasos siguientes.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. Deshabilitar la visibilidad de la malla de reconocimiento espacial. Para ello, busque "Configuración del sistema de reconocimiento espaciales" tal como se muestra en la imagen. Haga clic en el botón "clone" a la derecha de la la "espacial reconocimiento de perfil del sistema" para reemplazar el perfil predeterminado con una copia personalizable. Si aparece una ventana emergente, presione el botón "Clonación", como se muestra en la segunda imagen abajo.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Crear una copia personalizada del predeterminado mixto realidad espacial de la malla observador. Haga clic en la flecha abajo situada junto a "Windows mixto realidad espacial de la malla observador" para ver opciones adicionales. En estas opciones, verá el "predeterminado mixto realidad espacial de la malla observador" que aparece atenuada (no modificable). Debe reemplazar este perfil predeterminado con una copia personalizable para que pueda modificar. Haga clic en el botón a la derecha (marcado con una flecha verde) para clonar una copia.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. A continuación, se ajustará la configuración para la opción de visualización decir "oclusión." Esto hace invisible a la malla espacial, pero ocultar objetos del juego detrás de la malla espacial (Esto se conoce como oclusión.)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>Nota: Aunque la malla de asignación espacial no está visible, lo sigue estando presente y puede interactuar con él. Cualquier hologramas detrás de la malla de asignación espacial (por ejemplo, un holograma detrás de la pared visible) no serán visibles debido a la configuración de oclusión.

¡Enhorabuena! Acaba de aprender cómo modificar una configuración en el perfil MRTK. Como puede ver, con el fin de modificar la configuración de MRTK, deberá crear copias de los perfiles predeterminados para que se pueden editar. Siempre tendrá los perfiles predeterminados (que no son editables) para volver a si desea crear un perfil con la nueva configuración o hacer referencia a los perfiles predeterminados. Hay numerosas opciones que puede ajustar. Para obtener una referencia completa a la configuración de perfil MRTK, consulte la documentación de MRTK aquí: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botones Interactuable y gestos de mano de seguimiento
En esta sección, obtendrá información sobre cómo usar la mano de seguimiento para presionar un botón interactuable.

1. Seleccione "Activos" en la carpeta de proyectos.

2. Escriba en la barra de búsqueda, "pressablebutton".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. Arrastre el recurso prefabricado (representado por un cuadro azul) denominado "PressableButton" en la jerarquía. 

   > Nota: Si recibe un mensaje acerca de "importación TMP Essentials" impórtelo en este momento. Si TMP Essentials ya no formaba parte del proyecto, deberá repetir este paso después de importar Essentials TMP, en caso contrario, no puede aparecer el texto del botón.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. Haga doble clic en el objeto de juego "PressableButton" (que debe estar en la jerarquía BaseScene) para verlo en la escena, como se muestra en la imagen siguiente (los gráficos de botón pueden aparecer diferentes de la imagen siguiente). 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. En el panel del inspector, haga clic en "Agregar evento" para proporcionar al botón un evento para responder a cuando se insertan. En la opción que aparece, seleccione el menú desplegable. Seleccione "InteractableOnPressReciever." Esto permite que el botón responder a un evento presionado cuando una mano sometidas a seguimiento presiona el botón.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. Agregue un cubo a la escena. Haga clic con el botón derecho en el área de la jerarquía, seleccione un objeto 3D y luego haga clic en "cubo". Ahora, un cubo debe estar en la pantalla. Le son muy grande, por lo que ajustar las coordenadas (mientras "cubo" está seleccionado en el área de la jerarquía) para reducir el tamaño. Establezca los valores de escala en x = 0.1, y = 0,1 y z = 0.1. Ser seguro colocar el cubo en la escena para colocarlo junto al botón pressable, pero que no se superponen con el botón. En la imagen siguiente, es la posición del cubo x = 0, y = 0,2 y, z = 1. 

   > Nota: En general, 1 unidad en Unity equivale aproximadamente a 1 metro en el mundo físico. Existen excepciones a esto, por ejemplo, cuando los objetos son elementos secundarios de objetos con escala.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. En este paso configurará el cubo para cambiar el color cuando se presiona el botón. Seleccione el PressableButton en el menú "BaseScene". En el panel del inspector, en el cuadro "Seleccionar tipo de evento", haga clic en el botón "+". Arrastre el "cubo" en el menú "BaseScene" en el cuadro "Solo en tiempo de ejecución", tal como se muestra en la imagen siguiente

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

Haga clic en la lista desplegable que no dice "Ninguna función". Seleccione "MeshRenderer", a continuación, seleccione "material Material". Esto le permitirá cambiar el material de cuando se presiona el botón. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

Vaya al panel proyecto y busque el material que desee cambiarla a. Va a usar el material "MRTK_Standard_Cyan" en este ejemplo, se encuentra escribiendo "cian" en la barra de búsqueda de la pestaña proyecto (The MRTK incluye muchos de los materiales y colores para elegir). Arrastre el material en el cuadro situado debajo de "MeshRenderer.material". Encontrará los materiales MRTK en activos > MixedRealityToolkit.SDK > StandardAssets > materiales.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

El evento ahora está establecido para que cuando se presiona el botón, el cubo cambiará de color según el material especificado. En este ejemplo, el cubo cambiará al color aguamarina.

8. A continuación va a configurar la acción de versión para que después de su lanzamiento, el botón volverá al color predeterminado. Repita el paso 7 (el paso anterior), pero esta vez con el evento "OnRelease" en lugar del evento "OnPress", tal como se muestra en la imagen siguiente.

9.  En el panel proyecto, busque un material para el cubo de forma predeterminada en el botón de versión (en nuestro caso, elegimos MRTK_Standard_LightGray.) Arrastre el material en el cuadro situado debajo del campo "MeshRenderer.material".

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

Ahora cuando se presiona el botón, debería cambiar a un nuevo color (por ejemplo, cian) y cuando se suelta el botón debe cambiar al color predeterminado especificado (por ejemplo, gris claro.) ¡Presione el botón "reproducir" en la parte superior de la pantalla para probarlo en el editor o implementar en el 2 de HoloLens para probar! Para obtener más información acerca de la simulación en el editor, incluida la simulación de mano leer el [página de documentación de simulación del MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>). 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creación de un panel de botones con la colección de objetos de cuadrícula del MRTK

En esta sección, obtendrá información sobre cómo se alinean automáticamente varios botones en una interfaz de usuario nueva mediante la herramienta de GridObjectCollection del MRTK.

1. Duplicar el botón de la sección anterior hasta que haya 5 botones. Hay varias maneras de hacerlo:
- Haga clic con el botón derecho en el botón "Copiar", a continuación, vaya hasta debajo del botón y haga clic de nuevo y haga clic en "Pegar". 
- Haga clic con el botón secundario y haga clic en "duplicado". 
- Use el comando de teclado, haga clic en el cubo y pulse "ctrl D" en el teclado.

Repita este paso hasta que haya 5 botones total (consulte 5 flechas rojas en la imagen siguiente).

![Base Mrlearning Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupar los botones en un objeto de juego vacío primario. Para disponer de los botones en la colección de la cuadrícula, debe agrupar los botones en un objeto de elemento primario común. Haga clic con el botón derecho en el hiearachy y haga clic en "Crear vacío". Esto crea un nuevo objeto de juego vacío para incluir todos los botones. Se mostrará como "gameObject." Haga clic y cambie su nombre a "ButtonCollection."

![Base Mrlearning Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mueva todos los botones en la nueva colección. Hacer esto seleccionando los cinco de los objetos de botón en su heirarch y arrástrelos todas en el objeto de juego "ButtonCollection", tal como se muestra en la imagen siguiente. Sugerencia: seleccionar varios elementos, mantenga presionada la tecla ctrl mientras selecciona elementos.

![Base Mrlearning Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Agregar componente de "Colección de objetos de cuadrícula" del MRTK a la colección de botones.  Para ello, seleccione el objeto primario "ButtonCollection" y en el panel del inspector, haga clic en el botón "Agregar componente". A continuación, busque "Colección de objetos de cuadrícula" en la barra de búsqueda y selecciónelo cuando aparezca en la lista.

![Base Mrlearning Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

El componente de la colección de objetos de cuadrícula permite organizar botones o cualquier conjunto de objetos en una nueva fila, columna o una cuadrícula. Éste es uno de los bloques de creación proporcionados por el MRTK que le proporciona una manera rápida y sencilla para crear interfaces de usuario atractivas.

5. Configurar la colección de objetos de cuadrícula. Para garantizar que todos los botones se enfrentan el usuario, seleccione "orientar de tipo" y, a continuación, seleccione "primario al día se enfrentan" (como se muestra en la imagen.) A continuación, cambie el tamaño de celda para establecer el espacio entre los botones. Empieza con 0,12 unidades 0,12 unidades para el ancho de celda y el alto de celda, como se muestra en la imagen siguiente. Es posible que deba ajustar estos valores, dependiendo de los activos de botón del objeto elegidos. Asegúrese de que "Rows" está establecidos en 1. A continuación, haga clic en "Actualizar colección" y la escena debería ser similar a la siguiente imagen. 


![Base Mrlearning Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>Nota: Según la orientación de los objetos secundarios o el objeto primario, es probable que deba ajustar la orientación de la configuración de manera diferente en proyectos futuros. El ancho de celda y los campos de alto de celda también deberá definirse de forma diferente, dependiendo del tamaño de los objetos de la colección.

### <a name="adding-text-into-your-scene"></a>Agregar texto en la escena

En esta sección, obtendrá información sobre cómo agregar y editar texto en sus experiencias de realidad mixta. Si no lo ha hecho ya, asegúrese de tener habilitado en Unity, siga las instrucciones de TextMeshPro [aquí](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).

1. Seleccione el objeto primario "ButtonCollection" y a la derecha, haga clic en la colección. Expanda "objeto 3D" en el menú desplegable y luego seleccione "TextMeshPro – Text". Debería ver un objeto TextMeshPro en la colección de botones, tal como se muestra en la imagen siguiente.

![Lección 2 Capítulo4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Capítulo4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. En el campo de texto del componente TextMeshPro (que se encuentra en el panel del inspector, tal como se muestra a continuación), escriba "Botón colección Text". El texto aparecerá en la escena, pero se oculta detrás de los botones o un tamaño erróneo.

![Lección 2 Capítulo4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. Para mejorar el tamaño del texto y la ubicación para mejorar la legibilidad, ajustar el campo de "tamaño de fuente" en el componente TextMeshPro para cambiar el tamaño de la fuente. También deberá ajustar la posición de "Transformación Rect" y la escala tal como se muestra en la imagen siguiente. Ver las imágenes por debajo de los valores que se usan para esta configuración de texto y no dude en usar estos valores como punto de partida desde el que se va a mejorar aún más el tamaño y la colocación del campo de texto.

![Lección 2 Capítulo4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Capítulo4 paso4](images/Lesson2_Chapter4_Step4.JPG)

5. Para modificar los valores de texto en los objetos de botón, haga clic en la flecha situada junto a cualquier botón para expandirla y desplácese hasta el objeto "SeeItSayItLabel" y luego vaya a "TextMeshPro", donde puede editar el texto en los botones tal como se describe en los pasos anteriores.

![Lección 2 Capítulo4 paso5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>Enhorabuena
En esta lección, ha aprendido a copiar, personalizar y configurar una configuración de perfil MRTK (es decir, reconocimiento espacial malla visibilidad.) También ha aprendido cómo interactuar con el botón para desencadenar eventos mediante manos sometidas a seguimiento en el 2 de HoloLens. Por último, ha aprendido a crear una sencilla interfaz de la interfaz de usuario mediante texto de la malla Pro del Unity componente de colección de objetos de cuadrícula del MRTK.

[Próxima lección: Los algoritmos de resolución y la ubicación de contenido dinámico](mrlearning-base-ch3.md)

