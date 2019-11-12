---
title: 'Tutoriales de introducción: 6. Explorar opciones de entrada avanzadas'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 5599fe48f62a35d1dc02ce30fb7858fd74e87685
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926534"
---
# <a name="6-exploring-advanced-input-options"></a>6. explorar opciones de entrada avanzadas

En este tutorial, se exploran varias opciones de entrada avanzadas para HoloLens 2, incluido el uso de comandos de voz, gestos de movimiento panorámico y seguimiento ocular. 

## <a name="objectives"></a>Objetivos

- Desencadenar eventos mediante comandos de voz y palabras clave
- Usar manos con seguimiento para panorámicas y objetos 3D con manos con seguimiento
- Aproveche las capacidades de seguimiento ocular de HoloLens 2 para seleccionar objetos

## <a name="instructions"></a>Instrucciones

### <a name="enabling-voice-commands"></a>Habilitar comandos de voz

En esta sección, se implementan dos comandos de voz. En primer lugar, la capacidad de alternar el panel de diagnósticos de velocidad de fotogramas se introduce indicando "alternar diagnósticos". En segundo lugar, se explora la capacidad de reproducir un sonido con un comando de voz. En primer lugar, se revisan los perfiles y configuraciones de MRTK responsables de la configuración de comandos de voz.

1. En la jerarquía BaseScene, seleccione MixedRealityToolkit. A continuación, en el panel Inspector, seleccione INPUT (entrada) y haga clic en el botón pequeño Clone situado a la izquierda de DefaultMixedRealityInputSystemProfile para abrir el menú emergente Clone Profile (clonar perfil). En el menú emergente, haga clic en clonar para crear un nuevo perfil MixedRealityInputSystemProfile.

    ![mrlearning-base-CH5-1-step1a. png](images/mrlearning-base-ch5-1-step1a.png)

    También se rellenará automáticamente el MixedRealityToolkitConfigurationProfile con la MixedRealityInputSystemProfile recién creada.

    ![mrlearning-base-CH5-1-step1b. png](images/mrlearning-base-ch5-1-step1b.png)

2. En el perfil del sistema de entrada, hay una variedad de opciones de configuración. En el caso de los comandos de voz, expanda la sección voz y siga el mismo proceso que en el paso anterior para clonar el DefaultMixedRealitySpeechCommandsProfile y reemplazarlo por su propia copia modificable.

    ![mrlearning-base-CH5-1-Step2. png](images/mrlearning-base-ch5-1-step2.png)

    En el perfil de comando de voz, observará una variedad de opciones de configuración. Para obtener una descripción completa de estas opciones, consulte la [documentación de MRTK Speech](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).

    de forma predeterminada, el comportamiento general es el inicio automático. Si lo desea, puede cambiar a manual-Start. Pero en este ejemplo, manténgalo en el inicio automático. MRTK incluye varios comandos de voz predeterminados, como menú, alternancia de diagnóstico y alternancia de Profiler. Usaremos la palabra clave "alternar diagnósticos" para activar y desactivar el contador de velocidad de fotogramas de diagnóstico. También vamos a agregar un nuevo comando de voz en los pasos siguientes.

3. Agrega un nuevo comando de voz. Para ello, haga clic en el botón + Agregar un nuevo comando de voz. Verá una nueva línea que aparece debajo de la lista de comandos de voz existentes. Escriba el comando de voz que desea usar. En este ejemplo, use el comando "reproducir música".

    ![mrlearning-base-CH5-1-Step3. png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >también puedes establecer un código de teclas para los comandos de voz. Esto permite que los comandos de voz desencadenen eventos al presionar una tecla del teclado.

4. Agrega la posibilidad de responder a comandos de voz. Seleccione cualquier objeto de la jerarquía de BaseScene que no tenga ningún otro script de entrada asociado, por ejemplo, el objeto de juego MixedRealityPlayspace. En el panel Inspector, haga clic en Agregar componente, busque "voz" y seleccione el script controlador de entrada de voz.

    ![mrlearning-base-CH5-1-Step4. png](images/mrlearning-base-ch5-1-step4.png)

    De forma predeterminada, verá dos casillas. Una es la casilla es necesario el foco. Por lo tanto, siempre que apunte al objeto con un rayo mirada, una mirada hacia abajo, un controlador o una mirada a mano, se desencadenará el comando de voz. Desactive esta casilla para que el usuario no tenga que mirar el objeto para usar el comando de voz.

5. Agrega la posibilidad de responder a un comando de voz. Para ello, haga clic en el botón + que se encuentra en el controlador de entrada de voz.

    ![mrlearning-base-CH5-1-Step5. png](images/mrlearning-base-ch5-1-step5.png)

6. Junto a palabra clave, verá un menú desplegable. Seleccione alternar diagnósticos para que cada vez que el usuario diga la frase "alternar diagnósticos", desencadene una acción. Tenga en cuenta que es posible que tenga que expandir el elemento 0 presionando la flecha situada junto a él.

    ![mrlearning-base-CH5-1-Step6. png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >Estas palabras clave se rellenan según el perfil que editó en el paso 3.

7. Agregue el script Diagnostics System Voice Controls para activar y desactivar el diagnóstico del contador de velocidad de fotogramas. Para ello, presione Agregar componente, busque el script Diagnostics System Voice Controls y agréguelo desde el menú. Este script se puede agregar a cualquier objeto, pero por motivos de simplicidad, se agregará al mismo objeto que el controlador de entrada de voz.

    ![mrlearning-base-CH5-1-STEP7. png](images/mrlearning-base-ch5-1-step7.png)

8. Agregue una nueva respuesta en el controlador de entrada de voz. Para ello, haga clic en el icono "+" para agregar una nueva respuesta a la lista de respuestas.

    ![mrlearning-base-CH5-1-step8. png](images/mrlearning-base-ch5-1-step8.png)

9. Arrastre el objeto que tiene el script Diagnostics System Voice Controls a la nueva respuesta que acaba de crear en el paso anterior.

    ![mrlearning-base-CH5-1-step9. png](images/mrlearning-base-ch5-1-step9.png)

10. Haga clic en la lista desplegable función (donde indica que no hay función), luego en controles de voz del sistema de diagnóstico y seleccione la función ToggleDiagnostics () que activa y desactiva los diagnósticos.

    ![mrlearning-base-CH5-1-step10. png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > Antes de compilar en el dispositivo, debe habilitar la configuración de MIC. Para ello, haga clic en archivo y vaya a configuración de compilación, configuración del reproductor y asegúrese de que esté establecida la capacidad del micrófono.

    A continuación, agregue la capacidad de reproducir un archivo de audio desde el comando Voice mediante el objeto OCTA. Recuerde de la [Lección 4](mrlearning-base-ch4.md) que se ha agregado la capacidad de reproducir un clip de audio al tocar el objeto OCTA. Vamos a aprovechar este mismo origen de audio para nuestro comando de voz de música.

11. Seleccione el objeto OCTA en la jerarquía de BaseScene.

12. Agregue otro controlador de entrada de voz (Repita los pasos 4 y 5), pero con el objeto OCTA.

13. En lugar de agregar el comando alternar diagnóstico de voz desde el paso 6, agregue el comando reproducir música Voice como se muestra en la imagen siguiente.

    ![mrlearning-base-CH5-1-step13. png](images/mrlearning-base-ch5-1-step13.png)

14. Al igual que con los pasos 8 y 9, agregue una nueva respuesta y arrastre el objeto OCTA, el objeto que tiene el script Diagnostics System Voice Controls, a la ranura de respuesta vacía.

15. Seleccione el menú desplegable que indica que no hay ninguna función. A continuación, seleccione origen de audio, seguido de PlayOneShot (AudioClip).

    ![Imagen de la lección 5, capítulo 1, paso 15](images/Lesson5_chapter1_step15im.PNG)

16. En este ejemplo, vamos a usar el mismo clip de audio de la [Lección 4](mrlearning-base-ch4.md). Vaya al panel del proyecto, busque el clip de audio "MRTK_Gem" y arrástrelo a la ranura de origen de audio, tal como se muestra en la imagen siguiente. Ahora la aplicación responderá a los comandos de voz "alternar diagnósticos" para alternar el panel de contadores de velocidad de fotogramas y reproducir música para reproducir la MRTK_Gem canción.

    ![Lesson5 archivo chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a>Gesto de desplazamiento panorámico

En esta sección, aprenderá a usar el gesto de panorámica. Esto resulta útil para desplazarse con el dedo o la mano para desplazarse por el contenido. También puede usar el gesto de panorámica para girar objetos, recorrer una colección de objetos 3D o incluso desplazarse por una interfaz de usuario 2D. <!--TMP You will also learn how to use the pan gesture to warp a texture, and how to move a collection of 3D objects.-->

1. Creación de un cuadrángulo. En la jerarquía de BaseScene, haga clic con el botón derecho en, seleccione "objeto 3D" seguido de cuatro.

    ![Imagen de la lección 5, capítulo 2, paso 2](images/Lesson5_chapter2_step2im.PNG)

2. Cambie la posición de la cuádruple, según corresponda. En nuestro ejemplo, se establece x = 0, y = 0 y z = 1,5 fuera de la cámara para una posición cómoda de HoloLens 2.

    >[!NOTE]
    >Si los bloques cuádruples o están delante de cualquier contenido de las lecciones anteriores, asegúrese de moverlo para que no bloquee ninguno de los demás objetos.

3. Aplica un material al cuadrángulo. Este material será de lo que se desplazará con el gesto de panorámica.

    ![Imagen de la lección 5, capítulo 2, paso 3](images/Lesson5_chapter2_step3im.PNG)

4. En el panel proyectos, escriba "panorama del contenido" en el cuadro de búsqueda. Arrastre ese material a la cuádruple de la escena.

    >[!NOTE]
    >El material de contenido de pan no se incluye en MRTK, sino un recurso en el paquete de activos de este módulo como importado en lecciones anteriores.

    >[!NOTE]
    >Cuando se agrega el contenido panorámico, este puede parecer alargado. Puedes solucionar este problema mediante el ajuste de los valores x, y y z del tamaño del cuadrángulo hasta que esté satisfecho con su aspecto.

    Para usar los gestos de desplazamiento panorámico, necesitarás un colisionador en el objeto. Puede ver que el cuadrángulo ya tiene un colisionador de malla. Sin embargo, este no es el ideal ya que es extremadamente fino y difícil de seleccionar. Se recomienda reemplazar el colisionador de malla por un colisionador de cuadro.

5. Haga clic con el botón derecho en el Colisionador de malla que se encuentra en la cuádruple del panel Inspector. A continuación, quítelo haciendo clic en quitar componente.

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Ahora, agregue el Colisionador de Box; para ello, haga clic en Agregar componente y busque "Colisionador de cuadro". El Colisionador de cuadro agregado predeterminado todavía es demasiado fino, así que haga clic en el botón Editar Colisionador para editarlo. Al presionarlo, puedes ajustar el tamaño con los valores x, y, y z o con los elementos del editor de escenas. En nuestro ejemplo, queremos ampliar el colisionador de cuadro un poco por detrás del cuadrángulo. En el editor de escenas, arrastra el colisionador de cuadro desde la parte posterior hacia el exterior (mira la imagen siguiente). Esto permite que el usuario no solo use el dedo, sino todo su mano para desplazarse.

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. Hazlo interactivo. Puesto que queremos interactuar directamente con el cuádruple, queremos usar el componente táctil de la interacción cercana que usamos en la lección 4 para reproducir música desde el objeto OCTA. Haga clic en Agregar componente, busque "near Interaction Touchable" y selecciónelo tal como se muestra en las imágenes siguientes.

    ![mrlearning-base-CH5-2-step7a. png](images/mrlearning-base-ch5-2-step7a.png)

    Si ve una advertencia amarilla sobre los límites y/o el centro que no coinciden con el tamaño y/o centro de BoxCollider, haga clic en los botones corregir límites y/o centro de corrección para actualizar los valores del centro y los límites.

    ![mrlearning-base-CH5-2-step7b. png](images/mrlearning-base-ch5-2-step7b.png)

8. Agrega la posibilidad de reconocer el gesto de desplazamiento panorámico. Haga clic en Agregar componente, escriba "interacción con la mano" en el campo de búsqueda y agregue el componente de script zoom de panorámica de interacción con la mano.

    ![mrlearning-base-CH5-2-step8a. png](images/mrlearning-base-ch5-2-step8a.png)

    Y con eso, tiene una cuádruple habilitada para pan.

    Como puede ver, el componente zoom de pan de interacción a mano tiene varias opciones de configuración, como un ejercicio opcional, no dude en experimentar con ellas.

    ![mrlearning-base-CH5-2-step8b. png](images/mrlearning-base-ch5-2-step8b.png)

<!--TMP
   Next, we will learn how to pan 3D objects. 

10. Right-click the quad object, select 3D object and click Cube. Scale the cube so that it’s roughly x = 0.1, y = 0.1 and z = 0.1. Copy that cube three times by right-clicking the cube and pressing duplicate, or by pressing control/command D. Space them out evenly. Your scene should look similar to the image below.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)

11. Select the quad again and under the hand interaction pan script, set the pan actions to each of the cubes. Under Pan Event Receivers, we want to specify the number of objects receiving the event. Since there are four cubes, type “4” and press Enter. Four empty fields should appear.

![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)

12. Drag each of the cubes into each of the empty element slots.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Add the Move with Pan script to all of the cubes by pressing and holding control/command and select each object. From the Inspector panel, click Add Component and search for “move with pan.” Click the script and it is added to each cube. Now the 3D objects will move with your pan gesture. If you remove the mesh render on your quad, you should now have an invisible quad where you can pan through a list of 3D objects.
-->

### <a name="eye-tracking"></a>Seguimiento de los ojos

En esta sección, veremos cómo habilitar el seguimiento ocular en nuestra demostración. Giraremos lentamente los elementos de menú 3D cuando se encuentren al mirarnos con la mirada. También vamos a desencadenar un divertido efecto cuando se seleccione el elemento con la mirada.

1. Asegúrese de que los perfiles de MRTK estén configurados correctamente para el seguimiento ocular. Para ello, vaya a la [Introducción a seguimiento de ojo en las instrucciones de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) y compruebe que el seguimiento ocular está configurado correctamente revisando los pasos de la sección configuración de [seguimiento de ojos paso a paso](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) . Complete los pasos restantes de la documentación.

    >[!NOTE]
    >Si usó DefaultHoloLens2InputSystemProfile, tal y como se indicó en la lección [configurar el kit de herramientas de realidad mixta](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) , para clonar el perfil de configuración de MRTK personalizado, el seguimiento ocular está habilitado de forma predeterminada en el proyecto de Unity, pero todavía tendrá que configurar la simulación de seguimiento para el editor de Unity y configurar Visual Studio para permitir el seguimiento ocular de la compilación.

    El vínculo anterior proporciona instrucciones breves para:

    - Crear el proveedor de datos de mirada a la realidad mixta de Windows para su uso en el perfil de MRTK
    - Habilitación del seguimiento ocular en el proveedor de miras adjuntado a la cámara
    - Configuración de una simulación de seguimiento de ojo en el editor de Unity
    - Editar las funcionalidades de la solución Visual Studio para permitir el seguimiento de los ojos en la aplicación integrada

2. Agrega el componente Eye Tracking Target (Destino del seguimiento de los ojos) a los objetos de destino. Para permitir que un objeto responda a los eventos de ojo, debemos agregar el componente EyeTrackingTarget en cada objeto con el que queremos interactuar mediante la vista de ojo. Agrega este componente a cada uno de los nueve objetos 3D que forman parte de la colección de la cuadrícula.

    >[!TIP]
    >Puede utilizar las teclas Mayús y/o Ctrl para seleccionar varios elementos de la jerarquía de la escena y, a continuación, agregar de forma masiva el componente EyeTrackingTarget.

    ![Lesson5 Chapter3 paso 2](images/Lesson5Chapter3Step2.JPG)

3. A continuación, agregaremos el script EyeTrackingTutorialDemo para algunas interacciones emocionantes. El script EyeTrackingTutorialDemo se incluye como parte de este repositorio de la serie de tutoriales. No se incluye de forma predeterminada con el kit de herramientas de realidad mixta. Para cada objeto 3D de la colección de cuadrículas, agregue el script EyeTrackingTutorialDemo buscando el componente en el menú Agregar componente.

   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

4. Gira el objeto al examinar el destino. Queremos configurar nuestros objetos 3D para que giren mientras se examinan. Para ello, inserte un nuevo campo en la sección al mirar el destino () del componente EyeTrackingTarget, tal y como se muestra en la imagen siguiente.

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    En el campo recién creado, agregue el objeto de juego actual al campo vacío y seleccione EyeTrackingTutorialDemo > RotateTarget (), tal como se muestra en la imagen siguiente. Ahora el objeto 3D está configurado para girar cuando se le observa con seguimiento de los ojos.

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. Agregue la capacidad de "destino de señalización", que se mira al seleccionarse por vía aérea o a "seleccionar". Al igual que en el paso 4, queremos desencadenar EyeTrackingTutorialDemo > BlipTarget () asignándole el campo Select () del objeto Game del componente EyeTrackingTarget, como se muestra en la ilustración siguiente. Ahora que ya está configurado, observará una ligera señalización en el objeto de juego siempre que desencadene una acción de selección, como la pulsación aérea o el comando de voz "seleccionar".

    ![Lesson5 Chapter3 Paso5](images/Lesson5Chapter3Step5.JPG)

6. Asegúrate de que las funcionalidades de seguimiento de los ojos están configuradas correctamente antes de empezar a crear en HoloLens 2. En el momento de redactar este documento, Unity todavía no tiene la capacidad de establecer la entrada mirada para las funcionalidades de seguimiento ocular. La configuración de esta funcionalidad es necesaria para que el seguimiento ocular funcione en HoloLens 2. Siga las instrucciones para [probar la aplicación de Unity en una instrucción de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) para habilitar la capacidad de entrada de fijamente.

## <a name="congratulations"></a>Enhorabuena

Ha agregado correctamente las funciones básicas de seguimiento de los ojos a la aplicación. Estas acciones son solo el comienzo de un mundo lleno de posibilidades relacionadas con el seguimiento de los ojos. En este capítulo también concluye la lección 5, donde se ha aprendido sobre la funcionalidad de entrada avanzada, como comandos de voz, gestos de movimiento panorámico y seguimiento ocular.

[Lección siguiente: 7. crear una aplicación de ejemplo de módulo lunar](mrlearning-base-ch6.md)
