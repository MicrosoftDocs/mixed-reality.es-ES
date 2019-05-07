---
title: Módulo MR Learning Base - avanzada de entrada
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: c28b607e3532a7c964ab74fdb7a7d514c9293579
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929577"
---
# <a name="mr-learning-base-module---advanced-input"></a>Módulo MR Learning Base - avanzada de entrada

En esta lección, exploramos varias opciones avanzadas de entrada para el 2 de HoloLens, incluido el uso de comandos de voz, el gesto de panorámica y el seguimiento de los ojos. 

## <a name="objectives"></a>Objetivos

- Vea cómo desencadenar eventos mediante las palabras clave y los comandos de voz
- Usar manos sometidas a seguimiento para realizar una panorámica de texturas y objetos 3D
- Aprovechar las capacidades para seleccionar objetos de seguimiento de los ojos del 2 de HoloLens

## <a name="instructions"></a>Instrucciones

### <a name="enabling-voice-commands"></a>Habilitar los comandos de voz

En esta sección, se va a implementar dos comandos de voz. En primer lugar, la capacidad para activar o desactivar el panel de diagnóstico de velocidad de fotograma diciendo "Alternar diagnostics". En segundo lugar, la capacidad de reproducir un sonido con un comando de voz. En primer lugar, exploraremos los perfiles MRTK y configuración responsable de configurar los comandos de voz. 

1. En la jerarquía de la escena de Base, seleccione "MixedRealityToolkit." En el panel del inspector, desplácese hacia abajo hasta la configuración del sistema de entrada. Haga doble clic para abrir el perfil de sistema de entrada. Clonar el perfil de sistema de entrada para que se pueda modificar, como hemos visto en [lección 1](mrlearning-base-ch1.md) 

En el perfil de sistema de entrada, verá una diversas opciones de configuración. Para los comandos de voz, ir a, donde dice, "Configuración de comando de voz". 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. Clonar el perfil de los comandos de voz para que se pueda modificar, como hemos visto en [lección 1](mrlearning-base-ch1.md). Haga doble clic en el perfil de comandos de voz, donde podrá observar una variedad de opciones. Para obtener una descripción completa sobre estas opciones, consulte el [documentación de voz MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Nota: De forma predeterminada, el comportamiento general es el inicio automático. Que se puede cambiar para el inicio manual si lo desea, pero en este ejemplo, vamos a mantenerlo en el inicio automático. El MRTK viene con varios comandos de voz predeterminado (por ejemplo, menú, alternar diagnósticos y el generador de perfiles de alternancia). Vamos a usar la palabra clave "Alternar diagnostics" con el fin de activar y desactivar el contador de velocidad de fotogramas de diagnóstico. Además, agregaremos un nuevo comando de voz en los pasos siguientes.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. Agregar un nuevo comando de voz. Para agregar un nuevo comando de voz, haga clic en el botón "+ Agregar un nuevo comando de voz" y verá una nueva línea que aparece abajo debajo de la lista de comandos de voz existente. Escriba el comando de voz que desea utilizar. En este ex musicample vamos a usar el comando "reproducir música".

>Sugerencia: También puede establecer un código de tecla para los comandos de voz. Esto permite que los comandos de voz desencadenar la pulsación de una tecla de teclado.   

4. Agregar la capacidad para responder a comandos de voz. Seleccione cualquier objeto en la jerarquía escena base que no tiene otros scripts de entrada asociadas a él (p. ej., ningún controlador de manipulación.) En el panel del inspector, haga clic en "agregar el componente". Escriba "controlador de entrada de voz". Selecciónela.
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

De forma predeterminada, verá las casillas de 2 verificación, uno es la casilla "no es necesario el enfoque". Esto significa que apuntan al objeto con una mirada ray, (mirada, head mirada, controlador mirada o mano mirada) siempre que se desencadenará el comando de voz. Desactive esta casilla para hacer que el usuario no tiene que mirar el objeto que se va a usar el comando de voz.

5. Agregar la capacidad para responder a un comando de voz. Para ello, haga clic en el botón "+" que se encuentra en el controlador de entrada de voz y seleccione la palabra clave que le gustaría responder a.

   > Nota: Estas palabras clave se rellenan según el perfil que puede editar en el paso anterior.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. Junto a "Palabra clave" verá un menú desplegable. Seleccione "Activar diagnóstico". Esto hará que para que cada vez que el usuario dice la frase, "Alternar diagnósticos" desencadenará una acción. Tenga en cuenta que es posible que deba expandir "elemento 0" al presionar la flecha situada junto a ella.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. Agregue el "script de control de diagnóstico demo" para activar y desactivar la el diagnóstico de contador de velocidad de fotogramas. Para ello, presione el botón "agregar el componente" y busque "script de control de diagnóstico demo", a continuación, agregarlo en el menú. Esta secuencia de comandos se puede agregar a cualquier objeto, pero por motivos de simplicidad, se agregará al mismo objeto, como el controlador de entrada de voz. 

   > Nota: este script solo está incluida con estos módulos y no se incluye con el MRTK original.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. Agregue una nueva respuesta en el controlador de entrada de voz. Para hacer esto, haga clic en el botón "+" debajo, donde dice "respuesta ()" (marcados con una flecha verde en la imagen anterior).

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Arrastre el objeto que contiene el script de los controles de demostración de diagnóstico a la nueva respuesta que acaba de crear en el paso 8.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. Ahora seleccione la lista desplegable de "ninguna función", los controles de demostración de diagnóstico, y luego "en Alternar () de diagnóstico". Esta función activa el diagnóstico y se desactiva.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> Tenga en cuenta que antes de compilar para el dispositivo deberá habilitar la configuración de mic. Para ello haga clic en el archivo, vaya a configuración a partir de ahí, configuración del Reproductor, de compilación y asegúrese de que se establece la funcionalidad micrófono.

A continuación, agregamos la capacidad de reproducir un archivo de audio de comando de voz con el objeto "ocho". Recuerde que en [lección 4](mrlearning-base-ch4.md), hemos agregado la capacidad de reproducir un clip de audio de tocar el objeto octal. Se aprovechará este mismo origen de audio para el comando de voz de música.

11. Seleccione el objeto de ocho en la jerarquía escena base.

12. Agregar otro controlador de entrada de voz (Repita los pasos 4 y 5), pero con el objeto octal. 

13. En lugar de agregar el comando de voz "Alternar Diagnostics" en el paso 6, agregue el comando de voz "reproducir música", tal como se muestra en la imagen siguiente.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Al igual que con los pasos 8 y 9, agregar una nueva respuesta y arrastrar el octal a la ranura vacía en la respuesta.

15. Seleccione el menú desplegable que no dice "ninguna función," select "origen de Audio" y, a continuación, seleccione "PlayOneShot (AudioClip)."

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. El clip de audio, en este ejemplo vamos a usar el mismo clip de audio desde [lección 4](mrlearning-base-ch4.md). ENTRAR en el panel de proyecto, busque "MRTK_Gem" clip de audio y arrástrelo a la ranura de origen de audio, como se muestra en la imagen siguiente. Ahora la aplicación debe poder responder a los comandos de voz "Alternar diagnostics" para activar o desactivar el panel de contadores de velocidad de marco y "reproducir música" para reproducir la canción MRTK_Gem.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>El movimiento panorámico 

En este capítulo, se obtendrá información sobre cómo usar el movimiento panorámico. Es útil para el desplazamiento (con la mano o el dedo para desplazarse por contenido). También puede usar el movimiento panorámico girar objetos para recorrer en iteración una colección de objetos 3D, o incluso el desplazamiento de la interfaz de usuario de 2D. Se se puede aprender a usar el movimiento panorámico a warp una textura. También examinamos cómo mover una colección de objetos 3D.

1. Crear un cuadrado. En la jerarquía escena base, haga clic en, seleccione "objeto 3D" y luego seleccione "Cuatro".

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. Cambiar la posición de lo cuatro según corresponda. En nuestro ejemplo, establecemos la x = 0, la y = 0 y la z = 1.5 fuera de la cámara para una posición cómoda de HoloLens 2.

   > Nota: Si los cuatro bloques (es infront de) cualquier contenido de las lecciones anteriores, asegúrese de moverla, que no bloquea cualquiera de los demás objetos.

3. Aplicar un material a lo cuatro. Este material será el material que se desplazarse a través con el movimiento panorámico. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. En el panel proyectos, escriba en el cuadro de búsqueda "contenido de pan". Arrastre ese material de la sesión en el cuatro de la escena. 

> Nota: No se incluye el material "Desplazar el contenido" en el MRTK, pero es un recurso en el paquete de recurso de este módulo, como importar en lecciones anteriores. 

> Nota: Cuando se agrega el contenido de panorámica, puede parecer estirada. Para solucionar este problema mediante el ajuste de los valores x, y y z de los valores del tamaño de lo cuatro hasta que esté satisfecho con su aspecto.

Para usar el movimiento panorámico, necesitará un colisionador en el objeto. Puede ver que la cuatro ya tiene un colisionador de malla. Sin embargo, el colisionador malla no es ideal, porque resulta muy difícil seleccionar y fino. Se recomienda reemplazar el colisionador malla con un colisionador de cuadro.

5. Haga clic con el botón secundario del mouse en el colisionador malla que se encuentra en la cuatro (en el panel del inspector), a continuación, quítelo haciendo clic en "quitar el componente". 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. Ahora agregue el colisionador de cuadro haciendo clic en "agregar el componente" y buscar "colisionador de cuadro". El valor predeterminado se agrega colisionador de cuadro sigue siendo demasiado delgado, así que haga clic en el botón "Editar colisionador" para editarlo. Cuando se presiona en, puede ajustar el tamaño mediante la x, y y z de los valores o los elementos en el editor de la escena. En nuestro ejemplo, desea extender el colisionador de cuadro un poco detrás de lo cuatro. En el editor de la escena, arrastre el colisionador de cuadro de la parte posterior, hacia el exterior (vea la imagen siguiente). Esto lo que sucede es permitir que el usuario use no sólo sus dedos, pero su mano toda para desplazarse. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. Que lo sea interactivo. Puesto que deseamos interactuar directamente con el cuádruple, queremos usar el componente "cerca de la interacción touchable" (que también usa esto en la lección 4 para reproducir música desde el octal). Haga clic en "agregar el componente" y busque "cerca de interacción touchable" y seleccionarlo, como se muestra en las imágenes siguientes. 

8. Agregar la capacidad para reconocer el movimiento panorámico. Haga clic en "agregar el componente" y escriba "mano panorámica de interacción". Tendrá la posibilidad de elegir entre ray mano (lo que permite desplazar a distancia) y el índice. En este ejemplo, déjelo en dedo índice. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. En la secuencia de comandos de panorámica de interacción de mano, las casillas de verificación de "bloqueo vertical" y "bloqueo horizontal" se bloquearán los movimientos, respectivamente. La configuración de la textura encapsulado hará que la textura (asignación de textura) siga movimientos de panorámica del usuario. En este ejemplo, vamos a esa casilla. También hay "velocidad active" que, si se desactiva, el movimiento panorámico no funcionará. Active esta casilla también. Ahora debe tener un cuádruple pan habilitado.

   

   A continuación, se obtendrá información sobre cómo aplicar panorámica objetos 3D. 

10. A la derecha, haga clic en el objeto de cuatro, seleccione el objeto 3D, a continuación, haga clic en "cubo". Escalar el cubo para que sea más o menos x = 0.1, y = 0,1 y z = 0.1. Copiar ese cubo 3 veces (a la derecha, haga clic en el cubo y presionando duplicados, o bien presione control comando/D). Separarlas uniformemente. La escena debe ser similar a la siguiente imagen.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. Vuelva a seleccionar el cuádruple, y en la secuencia de comandos de panorámica de interacción de mano, queremos establecer las acciones de pan a cada uno de los cubos. En "receptores de eventos de pan" queremos especificar el número de objetos que reciben el evento. Puesto que hay 4 cubos, escriba "4" y presione ENTRAR. deberían aparecer 4 campos vacíos.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. Arrastre cada uno de los cubos de a cada una de las ranuras de elemento vacío.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. Agregue el script "mover con pan" para todos los cubos. Para ello, presione y mantenga/comando de control y seleccione cada objeto. A continuación, en el panel del inspector, haga clic en "agregar el componente" y busque "mover con pan". Haga clic en la secuencia de comandos y se agregará a cada cubo. ¡Ahora se moverán los objetos 3D con el gesto de pan! Si quita la malla se representan en su cuádruple, ahora debería tener un cuádruple invisible donde puede desplazarse a través de una lista de objetos 3D.

### <a name="eye-tracking"></a>Seguimiento de los ojos

En este capítulo, exploramos cómo habilitar el seguimiento de los ojos en nuestra demostración. Se girará lentamente nuestros elementos de menú 3D cuando se está gazed tras con mirada ojos. También se desencadenará un divertido efecto cuando se selecciona el elemento gazed tras.

1. Asegúrese de que se han configurado correctamente los perfiles del Kit de herramientas de realidad mixta. Cuando se redactó este documento, la configuración de perfiles del Kit de herramientas de realidad mixta no incluye capacidades de seguimiento de forma predeterminada el efecto de ojos. Para agregar capacidades de seguimiento de los ojos, siga las instrucciones que aparecen en la sección "Configurar los perfiles MRTK necesarios para realizar un seguimiento de ojos" tal como se describe en el [documentación del Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Asegúrese de que rastreo ocular está configurado correctamente, siga los pasos restantes en el vínculo de documentación sobre, incluida la habilitación de seguimiento de los ojos en GazeProvider (componente conectado a la cámara) y habilitar la simulación de ojo de seguimiento en el editor de Unity. Tenga en cuenta esa versión futura de la MRTK puede incluir el seguimiento de ojo de forma predeterminada.

    El vínculo anterior proporciona instrucciones breves para:

    - Crear el efecto de ojos que mirar de proveedor de datos para su uso en el perfil MRTK
    - Habilitación del seguimiento de los ojos en el proveedor de observación
    - Configurar para simular el efecto de ojos de seguimiento en el editor de
    - Funciones de la solución de Visual Studio para realizar el seguimiento de la aplicación compilada ojo de edición

2. Agregar el componente de destino de ojo de seguimiento a los objetos de destino. Para permitir que un objeto responder a eventos de ojo mirada, necesitamos agregar el componente EyeTrackingTarget en cada objeto que se desee interactuar con el uso de mirada ojos. Agregar este componente a cada uno de los nueve objetos 3D que forman parte de la colección de la cuadrícula. Sugerencia: seleccionar varios elementos en la jerarquía para agregar el componente EyeTrackingTarget en masa.
    ![Paso 2 del capítulo 3 de Lesson5](images/Lesson5Chapter3Step2.JPG)

3. A continuación, agregaremos la secuencia de comandos EyeTrackingTutorialDemo para algunos interesantes interacciones. La secuencia de comandos EyeTrackingTutorialDemo se incluye como parte del repositorio de esta serie y no se incluye de forma predeterminada con el Kit de herramientas de realidad mixta. Para cada objeto 3D en la colección de la cuadrícula, agregue el script de EyeTrackingTutorialDemo buscando el componente en el menú "Agregar componente".
   ![Paso 3 del capítulo 3 de Lesson5](images/Lesson5Chapter3Step3.JPG)

   4. Gire el objeto al examinar el destino. Nos gustaría configurar nuestro objeto 3D para sincronizar mientras estamos examinando lo. Para ello, inserte un nuevo campo en la sección "Mientras busca en Target" del componente EyeTrackingTarget, tal como se muestra en la imagen siguiente. 

![Lesson5 capítulo 3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 capítulo 3 Step4b](images/Lesson5Chapter3Step4b.JPG)



En el campo recién creado, agregue el objeto de juego actual en el campo vacío y seleccione EyeTrackingTutorialDemo > RotateTarget() tal como se muestra en la imagen siguiente. Ahora el objeto 3D está configurado para poner cuando se está gazed tras con seguimiento de ojos. 

5. Agregar capacidad a "interrupción momentánea target" que se está gazed en tras seleccionar (pulsar en el aire, o que dice "select"). Al igual que el paso 4, queremos desencadenar EyeTrackingTutorialDemo > BlipTarget() asignándola a campo de "Select()" del objeto de juego del componente EyeTrackingTarget, tal como se muestra en la ilustración siguiente. Con esto ya configurada, observará una pequeña interrupción momentánea de en el objeto de juego cada vez que desencadene una acción de selección, como pulsar en el aire o el comando de voz "seleccionar". 
    ![Lesson5 capítulo 3 paso5](images/Lesson5Chapter3Step5.JPG)
6. Asegurarse de que las capacidades de seguimiento de ojo están configuradas correctamente antes de compilar a HoloLens 2. Cuando se redactó este documento, Unity no tiene todavía la capacidad de establecer la capacidad de entrada (para el seguimiento de ojo) mirada. Configuración de esta funcionalidad es necesaria para el seguimiento de ojo trabajar en el 2 de HoloLens. Siga estas instrucciones en la documentación del Kit de herramientas de realidad mixta para habilitar la capacidad de entrada de mirada: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>¡Enhorabuena! 
Se han agregado correctamente los ojos básico capacidades de seguimiento a la aplicación. Estas acciones son solo el comienzo de un mundo de posibilidades con seguimiento de los ojos. Este capítulo también concluye la lección 5, donde hemos aprendido sobre la funcionalidad avanzada de entrada como los comandos de voz, gestos y el seguimiento de ojo de movimiento panorámico. 

[Próxima lección: Experiencia de ejemplo de ensamblado de módulo lunar](mrlearning-base-ch6.md)

