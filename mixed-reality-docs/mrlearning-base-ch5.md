---
title: 'Tutoriales de introducción: 6. Explorar opciones de entrada avanzadas'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 0f01b789cfc358500ec94a10f82315bca55dd622
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702007"
---
# <a name="6-exploring-advanced-input-options"></a>6. Explorar opciones de entrada avanzadas

En este tutorial, se exploran varias opciones de entrada avanzadas para HoloLens 2, incluido el uso de comandos de voz, gestos de movimiento panorámico y seguimiento ocular. 

## <a name="objectives"></a>Objetivos

- Desencadenar eventos mediante comandos de voz y palabras clave
- Usar manos con seguimiento para panorámicas y objetos 3D con manos con seguimiento
- Aproveche las capacidades de seguimiento ocular de HoloLens 2 para seleccionar objetos

## <a name="instructions"></a>Instrucciones

### <a name="enabling-voice-commands"></a>Habilitar comandos de voz

En esta sección, se implementarán dos comandos de voz. En primer lugar, introduciremos la capacidad de alternar el panel de diagnósticos de velocidad de fotogramas diciendo "alternar diagnósticos". En segundo lugar, veremos la posibilidad de reproducir un sonido con un comando de voz. Para empezar, exploraremos los perfiles y configuraciones de MRTK responsables de configurar comandos de voz. 

1. En la jerarquía base de la escena, seleccione MixedRealityToolkit. En el panel Inspector, desplácese hacia abajo hasta configuración del sistema de entrada. Haz doble clic para abrir el perfil del sistema de entrada. Clonar el perfil del sistema de entrada para que sea editable como hemos aprendido en la [Lección 1](mrlearning-base-ch1.md) 

En el perfil del sistema de entrada, hay una variedad de opciones de configuración. Para comandos de voz, seleccione Configuración de comandos de voz. 

![Imagen de la lección 5, capítulo 1, paso 2](images/Lesson5_Chapter1_step2im.PNG)

2. Clone el perfil de comandos de voz para que sea editable como hemos aprendido en la [Lección 1](mrlearning-base-ch1.md). Haga doble clic en el perfil de comando de voz en el que observará una variedad de opciones de configuración. Para obtener una descripción completa de estas opciones, consulte la [documentación de MRTK Speech](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Nota: de forma predeterminada, el comportamiento general es el inicio automático. Si lo desea, puede cambiar a manual-Start. Pero en este ejemplo vamos a mantenerlo en el inicio automático. MRTK incluye varios comandos de voz predeterminados, como MENU, Toggle Diagnostics y Toggle Profiler. Usaremos la palabra clave "alternar diagnósticos" para activar y desactivar el contador de velocidad de fotogramas de diagnóstico. También vamos a agregar un nuevo comando de voz en los pasos siguientes.
>
> ![Imagen de la lección 5, capítulo 1, nota](images/Lesson5_chapter1_noteim.PNG)

3. Agrega un nuevo comando de voz. Para agregar un nuevo comando de voz, haga clic en el botón + Agregar un nuevo comando de voz. Verá una nueva línea que aparece debajo de la lista de comandos de voz existentes. Escribe el comando de voz que deseas utilizar. En este ejemplo, vamos a usar el comando "reproducir música".

>Sugerencia: también puedes establecer un código de teclas para los comandos de voz. Esto permite que los comandos de voz desencadenen eventos al presionar una tecla del teclado.    

4. Agrega la posibilidad de responder a comandos de voz. Seleccione cualquier objeto de la jerarquía de escenas base que no tenga ningún otro script de entrada asociado (por ejemplo, sin controlador de manipulación). En el panel Inspector, haga clic en Agregar componente. Escriba "controlador de entrada de voz" y selecciónelo.

   ![Lesson5 archivo chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

De forma predeterminada, verá dos casillas. Una es la casilla es necesario el foco. Esto significa que, siempre y cuando esté señalando el objeto con un rayo de mira fijamente, mirando hacia abajo, a la izquierda, al controlador o a la mano, se desencadenará el comando de voz. Desactive esta casilla para que el usuario no tenga que mirar el objeto para usar el comando de voz.

5. Agrega la posibilidad de responder a un comando de voz. Para ello, haga clic en el botón + que se encuentra en el controlador de entrada de voz y seleccione la palabra clave a la que desea responder.

   > Nota: estas palabras clave se rellenan según el perfil que editó en el paso anterior.

![Imagen de la lección 5, capítulo 1, paso 5](images/Lesson5_chapter1_step5im.PNG)

6. Junto a palabra clave, verá un menú desplegable. Seleccione alternar diagnósticos para que cada vez que el usuario diga la frase "alternar diagnósticos", desencadene una acción. Tenga en cuenta que es posible que tenga que expandir el elemento 0 presionando la flecha situada junto a él.

![Imagen de la lección 5, capítulo 1, paso 6](images/Lesson5_chapter1_step6im.PNG)

7. Agregue el script de control demo de diagnósticos para activar y desactivar el diagnóstico del contador de velocidad de fotogramas. Para ello, presione Agregar componente y busque scripts de controles demo de diagnósticos y agréguelo desde el menú. Este script se puede Agregar a cualquier objeto. Pero, por simplicidad, lo agregaremos al mismo objeto que el controlador de entrada de voz. 

   > Nota: Este script solo se incluye con estos módulos y no se incluye con el MRTK original.

![Imagen de la lección 5, capítulo 1, paso 7](images/Lesson5_chapter1_step7im.PNG)

8. Agregue una nueva respuesta en el controlador de entrada de voz. Para ello, haga clic en el botón + debajo de donde dice respuesta () (marcado con la flecha verde en la imagen anterior).

![Imagen de la lección 5, capítulo 1, paso 7](images/Lesson5_chapter1_step8.PNG)

9. Arrastre el objeto que tiene el script de controles demo de diagnósticos a la nueva respuesta que acaba de crear en el paso 8.
    ![Imagen de la lección 5, capítulo 1, paso 9](images/Lesson5_chapter1_step9im.PNG)

10. Ahora seleccione la lista desplegable "no Function" y seleccione Control demo de diagnóstico. A continuación, seleccione la función "activar o desactivar diagnósticos ()" que activa y desactiva los diagnósticos.  ![Imagen de la lección 5, capítulo 1, paso 10](images/Lesson5_chapter1_step10im.PNG)
    
> Ten en cuenta que antes de compilar en el dispositivo tendrás que habilitar la configuración del micrófono. Para ello, haga clic en archivo, vaya a configuración de compilación, configuración del reproductor y asegúrese de que esté establecida la capacidad del micrófono.

A continuación, agregaremos la capacidad de reproducir un archivo de audio desde el comando Voice mediante el objeto OCTA. Recuerde de la [Lección 4](mrlearning-base-ch4.md) que hemos agregado la capacidad de reproducir un clip de audio al tocar el objeto OCTA. Vamos a aprovechar este mismo origen de audio para nuestro comando de voz de música.

11. Seleccione el objeto OCTA en la jerarquía de escenas base.

12. Agregue otro controlador de entrada de voz (Repita los pasos 4 y 5), pero con el objeto OCTA. 

13. En lugar de agregar el comando alternar diagnóstico de voz desde el paso 6, agregue el comando reproducir música Voice como se muestra en la imagen siguiente.
    
     ![Imagen de la lección 5, capítulo 1, paso 13](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Como con los pasos 8 y 9, agregue una nueva respuesta y arrastre el objeto OCTA a la ranura de respuesta vacía.

15. Seleccione el menú desplegable que indica que no hay ninguna función. Después, seleccione origen de audio y seleccione PlayOneShot (AudioClip).

![Imagen de la lección 5, capítulo 1, paso 15](images/Lesson5_chapter1_step15im.PNG)

16. En este ejemplo, vamos a usar el mismo clip de audio de la [Lección 4](mrlearning-base-ch4.md). Vaya al panel del proyecto, busque el clip de audio "MRTK_Gem" y arrástrelo a la ranura de origen de audio, tal y como se muestra en la imagen siguiente. Ahora la aplicación responderá a los comandos de voz "alternar diagnósticos" para alternar el panel de contadores de velocidad de fotogramas y reproducir música para reproducir la canción MRTK_Gem.
     ![Imagen de la lección 5, capítulo 1, paso 16](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Gesto de desplazamiento panorámico 

En esta sección, aprenderá a usar el gesto de panorámica. Esto resulta útil para desplazarse con el dedo o la mano para desplazarse por el contenido. También puede usar el gesto de panorámica para girar objetos, recorrer una colección de objetos 3D o incluso desplazarse por una interfaz de usuario 2D. También aprenderá a usar el movimiento de panorámica para deformar una textura y cómo mover una colección de objetos 3D.

1. Creación de un cuadrángulo. En la jerarquía de escenas base, haga clic con el botón derecho, seleccione "objeto 3D" y seleccione cuádruple.

![Imagen de la lección 5, capítulo 2, paso 2](images/Lesson5_chapter2_step2im.PNG)

2. Cambia la posición del cuadrángulo según corresponda. En nuestro ejemplo, se establece x = 0, y = 0 y z = 1,5 fuera de la cámara para una posición cómoda de HoloLens 2.

   > Nota: Si los bloques cuádruples o están delante de cualquier contenido de las lecciones anteriores, asegúrese de moverlo para que no bloquee ninguno de los demás objetos.

3. Aplica un material al cuadrángulo. Este material será el material que vamos a desplazar con un gesto de desplazamiento panorámico. 

![Imagen de la lección 5, capítulo 2, paso 3](images/Lesson5_chapter2_step3im.PNG)

4. En el panel proyectos, escriba en el cuadro de búsqueda "panorama de contenido". Arrastra ese material al cuadrángulo de su ejemplo. 

> Nota: El material de contenido de pan no se incluye en MRTK, sino un recurso en el paquete de activos de este módulo como importado en lecciones anteriores. 

> Nota: Cuando se agrega el contenido panorámico, este puede parecer alargado. Puedes solucionar este problema mediante el ajuste de los valores x, y y z del tamaño del cuadrángulo hasta que esté satisfecho con su aspecto.

Para usar los gestos de desplazamiento panorámico, necesitarás un colisionador en el objeto. Puede ver que el cuadrángulo ya tiene un colisionador de malla. Sin embargo, este no es el ideal ya que es extremadamente fino y difícil de seleccionar. Se recomienda reemplazar el colisionador de malla por un colisionador de cuadro.

5. Haga clic con el botón derecho en el Colisionador de malla que se encuentra en la cuádruple del panel Inspector. A continuación, quítelo haciendo clic en quitar componente.
    ![Imagen de la lección 5, capítulo 2, paso 5](images/Lesson5_chapter2_step5im.PNG)
6. Ahora, para agregar el Colisionador de Box, haga clic en Add Component (Agregar componente) y busque "Box Colisionador", el Colisionador de cuadro que se ha agregado de forma predeterminada todavía es demasiado fino, así que haga clic en el botón Editar Colisionador para editarlo. Al presionarlo, puedes ajustar el tamaño con los valores x, y, y z o con los elementos del editor de escenas. En nuestro ejemplo, queremos ampliar el colisionador de cuadro un poco por detrás del cuadrángulo. En el editor de escenas, arrastra el colisionador de cuadro desde la parte posterior hacia el exterior (mira la imagen siguiente). Esto permite que el usuario no solo use el dedo, sino todo su mano para desplazarse. 
    ![Imagen de la lección 5, capítulo 2, paso 6](images/Lesson5_chapter2_step6im.PNG)
7. Hazlo interactivo. Puesto que queremos interactuar directamente con el cuádruple, queremos usar el componente táctil de la interacción cercana que usamos en la lección 4 para reproducir música desde el objeto OCTA. Haga clic en Agregar componente y busque "near Interaction Touching" y selecciónelo tal como se muestra en las imágenes siguientes. 

8. Agrega la posibilidad de reconocer el gesto de desplazamiento panorámico. Haga clic en Agregar componente y escriba "mano de interacción con la mano". tendrá una opción entre el rayo (que le permite desplazarse de una distancia) y un dedo del índice. En este ejemplo, déjalo en dedo índice. 
    ![Imagen de la lección 5, capítulo 2, paso 7-8](images/Lesson5_chapter2_step7-8im.PNG)

![Imagen de la lección 5, capítulo 2, paso 8](images/Lesson5_chapter2_step8im.PNG)

9. En el script de movimiento de la interacción de mano, las casillas de verificación bloquear horizontal y bloquear verticalmente bloquean los movimientos, respectivamente. La configuración ajustar textura hace que la textura (asignación de textura) siga los movimientos de la panorámica del usuario. En este ejemplo, activará esta casilla. También hay una velocidad activa que, si no está activada, el movimiento de la panorámica no funcionará. Selecciona también esta casilla. Ahora tendrá una cuádruple habilitada para pan.

   

   A continuación, vamos a aprender cómo realizar movimientos panorámicos de objetos 3D. 

10. Haga clic con el botón derecho en el objeto cuádruple, seleccione objeto 3D y haga clic en cubo. Escala el cubo para que los valores sean aproximadamente x = 0,1, y = 0,1 y z = 0,1. Copie ese cubo tres veces; para ello, haga clic con el botón secundario en el cubo y presione duplicado, o bien presione Control/Command D. separarlos uniformemente. La escena debe ser similar a la imagen siguiente.

![Imagen de la lección 5, capítulo 2, paso 10](images/Lesson5_chapter2_step10im.PNG)







11. Vuelva a seleccionar el cuádruple y, en el script de pan de interacción, establezca las acciones de pan en cada uno de los cubos. En los receptores de eventos de pan, queremos especificar el número de objetos que reciben el evento. Dado que hay cuatro cubos, escriba "4" y presione Entrar. Deben aparecer cuatro campos vacíos.


![Imagen de la lección 5, capítulo 2, paso 11](images/Lesson5_chapter2_step11im.PNG)



12. Arrastre cada uno de los cubos a cada una de las ranuras de elemento vacías.
     ![Imagen de la lección 5, capítulo 2, paso 12](images/Lesson5_chapter2_step12im.PNG)
    
13. Agregue el script Move with pan a todos los cubos presionando y manteniendo control/Command y seleccione cada objeto. En el panel Inspector, haga clic en Agregar componente y busque "mover con pan". Haga clic en el script y se agrega a cada cubo. Ahora los objetos 3D se moverán con el gesto de pan. Si quitas la representación de la malla del cuadrángulo, ahora tienes un cuadrángulo invisible en el que puedes realizar movimientos panorámicos para recorrer una lista de objetos 3D.

### <a name="eye-tracking"></a>Seguimiento de los ojos

En esta sección, veremos cómo habilitar el seguimiento ocular en nuestra demostración. Giraremos lentamente los elementos de menú 3D cuando se encuentren al mirarnos con la mirada. También vamos a desencadenar un divertido efecto cuando se seleccione el elemento con la mirada.

1. Asegúrese de que los perfiles de MRTK estén configurados correctamente. Cuando se redactó este documento, la configuración del perfil de Mixed Reality Toolkit no incluía de forma predeterminada las funcionalidades de seguimiento de los ojos. Para agregar capacidades de seguimiento ocular, siga las instrucciones de la sección "configuración de los perfiles de MRTK necesarios para el seguimiento ocular", tal como se describe en la [documentación del kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Asegúrese de que el seguimiento ocular esté configurado correctamente siguiendo los pasos restantes del vínculo de documentación anterior, lo que incluye la habilitación del seguimiento ocular en GazeProvider (el componente conectado a la cámara) y la habilitación de la simulación del seguimiento ocular en el editor de Unity. Tenga en cuenta que las futuras versiones de MRTK podrían incluir el seguimiento ocular de forma predeterminada.

    El vínculo anterior proporciona instrucciones breves para:

    - Crear el proveedor de datos de mirada a ojo para su uso en el perfil de MRTK
    - Habilitar el seguimiento de los ojos en GazeProvider
    - Configuración de una simulación de seguimiento ocular en el editor
    - Editar las funcionalidades de la solución Visual Studio para permitir el seguimiento de los ojos en la aplicación integrada

2. Agrega el componente Eye Tracking Target (Destino del seguimiento de los ojos) a los objetos de destino. Para permitir que un objeto responda a los eventos de ojo, debemos agregar el componente EyeTrackingTarget en cada objeto con el que queremos interactuar mediante la vista de ojo. Agrega este componente a cada uno de los nueve objetos 3D que forman parte de la colección de la cuadrícula. Sugerencia: Seleccione varios elementos de la jerarquía para agregar de forma masiva el componente EyeTrackingTarget.
    ![Lección 5 Capítulo 3 Paso 2](images/Lesson5Chapter3Step2.JPG)

3. A continuación, vamos a agregar el script EyeTrackingTutorialDemo para conseguir varias interacciones muy interesantes. El script EyeTrackingTutorialDemo se incluye como parte de este repositorio de la serie de tutoriales. No se incluye de forma predeterminada con el kit de herramientas de realidad mixta. Para cada objeto 3D de la colección de cuadrículas, agregue el script EyeTrackingTutorialDemo buscando el componente en el menú Agregar componente.
   ![Lección 5 Capítulo 3 Paso 3](images/Lesson5Chapter3Step3.JPG)

4. Gira el objeto al examinar el destino. Queremos configurar nuestro objeto 3D para que gire mientras se examina. Para ello, inserte un nuevo campo en la sección al mirar el destino () del componente EyeTrackingTarget, tal y como se muestra en la imagen siguiente. 

![Lección 5 Capítulo 3 Paso 4a](images/Lesson5Chapter3Step4a.JPG)
![Lección 5 Capítulo 3 Paso 4b](images/Lesson5Chapter3Step4b.JPG)



En el campo recién creado, agregue el objeto de juego actual al campo vacío y seleccione EyeTrackingTutorialDemo > RotateTarget () como se muestra en la imagen siguiente. Ahora el objeto 3D está configurado para girar cuando se le observa con seguimiento de los ojos. 

5. Agregue la capacidad de "destino de señalización", que se mira al seleccionarse por vía aérea o a "seleccionar". Al igual que en el paso 4, queremos desencadenar EyeTrackingTutorialDemo > BlipTarget () asignándole el campo Select () del objeto Game del componente EyeTrackingTarget como se muestra en la ilustración siguiente. Ahora que ya está configurado, observará una ligera señalización en el objeto de juego siempre que desencadene una acción de selección, como la pulsación aérea o el comando de voz "seleccionar". 
    ![Lección 5 Capítulo 3 Paso 5](images/Lesson5Chapter3Step5.JPG)
6. Asegúrate de que las funcionalidades de seguimiento de los ojos están configuradas correctamente antes de empezar a crear en HoloLens 2. En el momento de redactar este documento, Unity todavía no tiene la capacidad de establecer la entrada mirada para las funcionalidades de seguimiento ocular. La configuración de esta funcionalidad es necesaria para que el seguimiento ocular funcione en HoloLens 2. Sigue estas instrucciones de la documentación de Mixed Reality Toolkit para habilitar la funcionalidad de entrada con la mirada: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2. 


## <a name="congratulations"></a>Enhorabuena

Ha agregado correctamente las funciones básicas de seguimiento de los ojos a la aplicación. Estas acciones son solo el comienzo de un mundo lleno de posibilidades relacionadas con el seguimiento de los ojos. En este capítulo también concluye la lección 5, donde se ha aprendido sobre la funcionalidad de entrada avanzada, como comandos de voz, gestos de movimiento panorámico y seguimiento ocular. 

[Siguiente lección: 7. Creación de una aplicación de ejemplo de módulo lunar](mrlearning-base-ch6.md)

