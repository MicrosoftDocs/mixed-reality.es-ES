---
title: 'Tutoriales de introducción: 3. Crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e961238b8fc7f2ef15bea5f25eba8a8e9eb2ef3e
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334396"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta

En la lección anterior, aprendió sobre algunas de las funcionalidades que el kit de herramientas de realidad mixta (MRTK) tiene que ofrecer al iniciar su primera aplicación para HoloLens 2. En la siguiente lección aprenderá a crear y organizar botones junto con los paneles de texto de la interfaz de usuario y a usar interacción predeterminada (Touch) para interactuar con cada botón. También explorarás la incorporación de acciones y efectos sencillos, como cambiar el tamaño, el sonido y color de los objetos. Este módulo presentará conceptos básicos sobre la modificación de perfiles de MRTK, empezando por desactivar la visualización de la malla de [asignación espacial](spatial-mapping.md) .

## <a name="objectives"></a>Objetivos

* Personalizar y configurar los perfiles de Mixed Reality Toolkit
* Interacción con hologramas mediante elementos y botones de la interfaz de usuario
* Entrada e interacciones básicas del seguimiento de la mano

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Configuración de los perfiles de kit de herramientas de realidad mixta (cambiar la opción de visualización de reconocimiento espacial)

En esta sección, aprenderá a personalizar y configurar los perfiles predeterminados de MRTK ajustando la opción de visualización de la malla de reconocimiento espacial. Puedes seguir estos mismos principios para ajustar cualquier parámetro o valor de los perfiles de MRTK.

1. Seleccione el kit de herramientas de realidad mixta (MRTK) de la jerarquía de BaseScene. En el panel Inspector, busque el script Mixed Reality Toolkit y seleccione el perfil activo como se muestra en la ilustración siguiente. Haga doble clic para abrirlo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    >De forma predeterminada, los perfiles de MRTK no son editables. Estas son plantillas de perfil predeterminadas que puede copiar y personalizar. Existen varios niveles de personalización y perfiles. Por lo tanto, es una práctica estándar copiar y personalizar varios perfiles al configurar una o más opciones.
    >
    >Para obtener más información sobre los perfiles de MRTK y su arquitectura, visite la [documentación de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).

2. Crea una copia del perfil predeterminado para personalizarlo. Para empezar, haga clic en **copiar & personalizar**.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    Se abrirá la ventana emergente del *Perfil de clonación* .

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    Haga clic en **clonar** para crear una copia del perfil de MRTK. Con su propia copia del perfil de MRTK, ahora tiene la capacidad de personalizar cualquier configuración en este perfil. También deberá repetir el paso copiar y personalizar para cualquier perfil adicional anidado bajo este perfil, tal como se describe en los pasos siguientes.

3. Deshabilita la visibilidad de la malla de orientación espacial. Para ello, busque la configuración del sistema de reconocimiento espacial tal como se muestra en la imagen siguiente. Asegúrese de que la opción **Habilitar sistema de reconocimiento espacial** está activada. Haga clic en el botón **clonar** a la derecha del perfil del sistema de reconocimiento espacial para reemplazar el perfil predeterminado por una copia personalizable. En la ventana emergente que aparece, presione el botón **clonar** , tal como se muestra en la segunda imagen siguiente.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. Crea una copia personalizada del observador predeterminado de la malla espacial de Mixed Reality. Haga clic en la flecha hacia abajo junto al observador de malla espacial de realidad mixta de Windows para ver opciones adicionales.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    En estas opciones, verá el observador de malla espacial de la realidad mixta predeterminada que está atenuado (no editable). Debes reemplazar este perfil predeterminado por una copia personalizable para poder editarlo. Como hizo antes, haga clic en el botón **clonar** y, a continuación, en la ventana emergente que aparece, presione el botón **clonar** , tal como se muestra en la segunda imagen siguiente.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. A continuación, vas a ajustar la configuración de la opción de visualización a "Occlusión" (Oclusión). Esto hace que la malla de asignación espacial sea invisible, pero todavía oculta objetos de juego detrás de la malla de asignación espacial, también conocida como oclusión.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    >Nota: aunque la malla de asignación espacial no está visible, sigue estando presente y puede interactuar con ella. Los hologramas detrás de la malla de asignación espacial, como un holograma detrás de la pared visible, no estarán visibles debido a la configuración de la oclusión.

Enhorabuena. Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puedes ver, para modificar la configuración de MRTK debes crear copias de los perfiles predeterminados para poder editarlos. Siempre tendrá los perfiles predeterminados, que no son editables, para volver a si desea crear un perfil con una nueva configuración o puede volver a consultar los perfiles predeterminados. Hay numerosas opciones que puedes ajustar. Para obtener una referencia completa a la configuración del perfil de MRTK, consulte la documentación de MRTK aquí: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botones de interacción y gestos de seguimiento de la mano

En esta sección, aprenderá a usar el seguimiento de manos para presionar un botón que se puede presionar.

1. Seleccione recursos en la carpeta proyectos.

2. Escriba "PressableButtonHoloLens2" en la barra de búsqueda.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. Arrastre recurso prefabricado (representado por un cuadro azul) denominado "PressableButtonHoloLens2" en la jerarquía y establezca establezca los valores de posición en x = 0, y = 0 y z = 0,2, de modo que el botón esté delante de la cámara. (La cámara se coloca en el origen).

    >[!NOTE]
    >Si recibe un mensaje acerca de la importación de TMP Essentials, impórtelo en este momento. Si TMP Essentials no formaba parte del proyecto, es posible que deba repetir este paso después de importar TMP Essentials; de lo contrario, es posible que no aparezca el texto del botón.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. Agrega un cubo a la escena. Haga clic con el botón secundario en el área jerarquía, seleccione un objeto 3D y, a continuación, haga clic en cubo.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    Ahora, debe aparecer un cubo en la pantalla. Aparecerá muy grande. Puede ajustar las coordenadas (mientras el cubo todavía está seleccionado en el área de jerarquía) para reducir el tamaño. Establezca los valores de escala en x = 0,02, y = 0,02 y z = 0,02. Asegúrese de colocar el cubo en la escena cerca del botón, pero no superpuesto. En la imagen siguiente, la posición del cubo es x = 0, y = 0,04 y z = 0,2.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    >En general, 1 unidad en Unity equivale aproximadamente a 1 metro en el mundo físico. Hay excepciones a esto; por ejemplo, cuando los objetos son elementos secundarios de objetos escalados.

5. Con el objeto de juego PressableButtonHoloLens2 seleccionado, desplácese hacia la parte inferior del inspector para buscar la sección de eventos del componente interactuable (Script).

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. Modificaremos el evento existente para dar al botón un evento al que responder cuando se inserte. Como puede ver, el tipo de receptor de eventos se establece en InteractableOnPressReceiver. Esto permite que el botón responda a un evento presionado cuando una mano con seguimiento presiona el botón. En este punto, también debe cambiar el filtro de interacción a Near y Far.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. En este paso configurarás el cubo para que cambie de color cuando se presiona el botón. Seleccione el PressableButtonHoloLens2 en la jerarquía de BaseScene y arrastre el objeto de juego del cubo desde la jerarquía de BaseScene al campo solo en tiempo de ejecución como se muestra en la imagen siguiente.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    Haga clic en la lista desplegable que indica que no hay ninguna función. Seleccione MeshRenderer y, a continuación, material material. Esto le permite cambiar el material cuando se presiona el botón.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    Haga clic en el círculo situado junto al campo material vacío para abrir el menú emergente seleccionar material. MRTK incluye muchos materiales y colores entre los que elegir. En este ejemplo, va a usar el material, MRTK_Standard_Cyan, que se encuentra escribiendo "MRTK_Standard" en la barra de búsqueda emergente. Seleccione el material de MRTK_Standard_Cyan para rellenar el campo material.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    El evento ahora está establecido para que cuando se presiona el botón, el cubo cambie de color según el material especificado. En este ejemplo, el cubo cambiará al color aguamarina.

8. A continuación, va a configurar la acción de lanzamiento para que, en el momento de la versión, el botón vuelva a su color predeterminado. Repita el paso 7 anterior. Sin embargo, esta vez con el evento de lanzamiento en lugar de en el material de MRTK_Standard_LightGray Press, tal y como se muestra en la imagen siguiente.

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    Ahora, cuando se presiona el botón, cambia a un nuevo color. color. Al soltar el botón, se volverá a cambiar al color predeterminado especificado (por ejemplo, gris claro). Haga clic en el botón reproducir en la parte superior de la pantalla para probarlo en el editor o en la implementación en HoloLens 2 para realizar la prueba. Para obtener más información sobre la simulación en el editor, incluida la simulación manual, lea la [Página de documentación de la simulación de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creación de un panel de botones con la colección de objetos de cuadrícula de MRTK

En esta sección, aprenderá a alinear automáticamente varios botones en una interfaz de usuario ordenada mediante la herramienta GridObjectCollection de MRTK.

1. Duplique el botón de la sección anterior hasta que tenga cinco botones. Hay varias maneras de hacerlo: haga clic con el botón derecho en el botón y haga clic en copiar. Después, vaya a debajo del botón y haga clic con el botón derecho de nuevo y, después, haga clic en pegar.
    -Haga clic con el botón derecho en el botón y haga clic en duplicar.
    -Use el comando de teclado haciendo clic en el cubo y presionando Ctrl D en el teclado.

    Repita este paso hasta que tenga cinco botones; Vea las cinco flechas rojas de la imagen siguiente.

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. Agrupa los botones debajo de un objeto de juego primario. Para tener los botones en la colección de cuadrículas, debe agrupar los botones en un objeto primario común. Haga clic con el botón secundario en hiearachy y haga clic en crear vacío. Se crea un objeto de juego vacío en el que colocar todos los botones. Se muestra como gameObject. Haga clic con el botón secundario y cambie su nombre, ButtonCollection.

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. Mueve todos los botones a la nueva colección. Para ello, seleccione los cinco objetos de botón en la jerarquía y arrástrelos todos en el objeto de juego ButtonCollection como se muestra en la imagen siguiente. Sugerencia: Seleccione varios elementos manteniendo presionada la tecla Ctrl mientras selecciona los elementos.

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. Agregue el componente de colección de objetos de cuadrícula de MRTK a la colección de botones. Para ello, seleccione el objeto primario ButtonCollection. En el panel Inspector, haga clic en el botón Agregar componente. Busque la colección de objetos de cuadrícula en la barra de búsqueda y selecciónela cuando aparezca en la lista.

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    El componente de colección de objetos de cuadrícula permite organizar botones o cualquier conjunto de objetos en una fila, columna o cuadrícula ordenada. Se trata de uno de los bloques de creación que proporciona el MRTK, que ofrece una manera rápida y sencilla de crear interfaces de usuario atractivas.

5. Configura la colección de objetos de cuadrícula. Para asegurarse de que todos los botones se encuentran en el usuario, seleccione orientar tipo. A continuación, seleccione la esfera principal hacia delante, tal como se muestra en la imagen siguiente. A continuación, cambia el tamaño de celda para establecer el espacio entre los botones. Empiece con 0,05 unidades por 0,05 unidades para el ancho de celda y el alto de celda, tal y como se muestra en la imagen siguiente. Asegúrese de que Distance está establecido en 0 y Rows está establecido en 1. Haga clic en actualizar colección. La escena tendrá un aspecto similar al de la siguiente imagen.

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    >Según la orientación de los objetos secundarios o del objeto primario, es probable que debas ajustar la orientación de manera diferente en futuros proyectos. También, puede que los campos de ancho y alto de celda se deban definir de forma diferente, según el tamaño de los objetos de la colección.

## <a name="adding-text-into-your-scene"></a>Adición de texto a la escena

En esta sección, aprenderás a agregar texto a tus experiencias de realidad mixta y a editarlo. Si aún no lo ha hecho, asegúrese de que ha habilitado TextMeshPro en Unity siguiendo [estas instrucciones.](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)

1. Seleccione el objeto primario ButtonCollection y haga clic con el botón secundario en la colección. Expanda objeto 3D en el menú desplegable. A continuación, seleccione TextMeshPro-Text. Debería ver un objeto TextMeshPro en la colección de botones, tal como se muestra en la imagen siguiente.

    ![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. Para mejorar el tamaño del texto y la ubicación para facilitar la lectura, ajuste el campo tamaño de fuente del componente TextMeshPro para cambiar el tamaño de la fuente. También tendrá que ajustar la posición y la escala de la transformación Rect, tal y como se muestra en la imagen siguiente. Consulte las imágenes siguientes para ver los valores usados para la configuración de texto. No dude en usar estos valores como punto de partida para mejorar aún más el tamaño y la posición del campo de texto.

    ![Lesson2 Chapter4 Step3](images/mrlearning-base-ch2-4-step3.png)

3. En el campo de texto del componente TextMeshPro del panel Inspector, escriba "texto de la colección de botones" y ajuste las propiedades de alineación en Center y Top, tal como se muestra en la imagen siguiente.

    ![Lesson2 Chapter4 Paso4](images/mrlearning-base-ch2-4-step4.png)

4. Para modificar los valores de texto de los objetos de botón, haga clic en la flecha situada junto a cualquier botón para expandirlo y navegue hasta el objeto SeeItSayItLabel. Vaya a TextMeshPro, donde puede editar el texto en los botones tal y como se describe en los pasos anteriores.

    ![Lección 2, capítulo 4, paso 5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>Enhorabuena

En esta lección, aprendió a copiar, personalizar y configurar una configuración de Perfil de MRTK (es decir, visibilidad espacial de la malla). También ha aprendido a interactuar con un botón para desencadenar eventos mediante las manos con seguimiento en HoloLens 2. Por último, aprendió a crear una interfaz de usuario simple mediante la malla de texto de Unity Pro y el componente de colección de objetos de cuadrícula de MRTK.

[Lección siguiente: 4. colocar contenido dinámico y usar solucionadores](mrlearning-base-ch3.md)
