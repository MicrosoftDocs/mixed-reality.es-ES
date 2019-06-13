---
title: 'Módulo de base de aprendizaje de MR: Entrada avanzada'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719894"
---
# <a name="mr-learning-base-module---advanced-input"></a>Módulo de base de aprendizaje de MR: Entrada avanzada

En esta lección, se analizarán varias opciones de entrada avanzadas para HoloLens 2, entre las que se incluyen comandos de voz, gestos panorámicos y seguimiento de los ojos. 

## <a name="objectives"></a>Objetivos

- Aprender a desencadenar eventos mediante comandos de voz y palabras clave
- Usar las manos objeto de seguimiento para realizar un gesto de desplazamiento panorámico de texturas y objetos 3D
- Aprovechar las funcionalidades de seguimiento de los ojos de HoloLens 2 para seleccionar objetos

## <a name="instructions"></a>Instrucciones

### <a name="enabling-voice-commands"></a>Habilitar comandos de voz

En esta sección se van a implementar dos comandos de voz. El primero permitirá la posibilidad de activar o desactivar el panel de diagnóstico de velocidad de fotogramas diciendo "toggle diagnostics" (alternar diagnóstico). El segundo permitirá reproducir un sonido con un comando de voz. En primer lugar, se analizarán los perfiles y valores de MRTK responsables de la configuración de los comandos de voz. 

1. En la jerarquía del escenario básico, selecciona "MixedRealityToolkit". En el panel del inspector, desplázate hacia abajo hasta el valor del sistema de entrada. Haz doble clic para abrir el perfil del sistema de entrada. Clona el perfil del sistema de entrada para que se pueda modificar, como hemos visto en la [lección 1](mrlearning-base-ch1.md). 

En el perfil del sistema de entrada verás diversos valores. Para los comandos de voz, ve hasta donde dice "Configuración de los comandos de voz". 

![Imagen de la lección 5, capítulo 1, paso 2](images/Lesson5_Chapter1_step2im.PNG)

2. Clona el perfil de comandos de voz para que se pueda modificar, como hemos visto en la [lección 1](mrlearning-base-ch1.md). Haz doble clic en el perfil de comandos de voz, donde podrás observar diversos valores. Para obtener una descripción completa sobre estos valores, consulta la [documentación de voz de MRTK](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>). 

>Nota: de forma predeterminada, el comportamiento general es el inicio automático. Esto se puede cambiar a inicio manual si se desea, pero para este ejemplo lo vamos a mantener en automático. MRTK viene con varios comandos de voz predeterminados como, por ejemplo, menu (menú), toggle diagnostics (alternar diagnóstico) y toggle profiler (alternar generador de perfiles). Vamos a usar la palabra clave "toggle diagnostics" (alternar diagnóstico) para activar y desactivar el contador de velocidad de fotogramas de diagnóstico. También vamos a agregar un nuevo comando de voz en los pasos siguientes.
>
> ![Imagen de la lección 5, capítulo 1, nota](images/Lesson5_chapter1_noteim.PNG)

3. Agrega un nuevo comando de voz. Para agregar un nuevo comando de voz, haz clic en el botón "+ add a new speech command" (Agregar un nuevo comando de voz) y verás una nueva línea que aparece debajo de la lista de los comandos de voz existentes. Escribe el comando de voz que deseas utilizar. En este ejemplo musical, se va a utilizar el comando "play music" (reproducir música).

>Sugerencia: también puedes establecer un código de teclas para los comandos de voz. Esto permite que los comandos de voz se desencadenen al pulsar una tecla del teclado.   

4. Agrega la posibilidad de responder a comandos de voz. Selecciona cualquier objeto de la jerarquía del escenario básico que no tenga ningún script de entrada asociado (por ejemplo, ningún controlador de manipulación). En el panel del inspector, haz clic en "add component" (agregar componente). Escribe "speech input handler" (controlador de entrada de voz). Selecciónalo.
   ![Imagen de la lección 5, capítulo 1, paso 4](images/Lesson5_chapter1_step4im.PNG)

   

De forma predeterminada, verás 2 casillas de verificación, una de ellas es la casilla "is focus required" (¿se requiere enfoque?). Esto significa que siempre que apuntes al objeto con algún tipo de control (control con la mirada, con la cabeza, con controlador o con la mano) el comando de voz se desencadenará. Desactiva esta casilla para hacer que el usuario no tenga que mirar al objeto para usar el comando de voz.

5. Agrega la posibilidad de responder a un comando de voz. Para ello, haz clic en el botón "+" en el controlador de entrada de voz y selecciona la palabra clave a la que te gustaría responder.

   > Nota: estas palabras clave se rellenan según el perfil que editó en el paso anterior.

![Imagen de la lección 5, capítulo 1, paso 5](images/Lesson5_chapter1_step5im.PNG)

6. Junto a "Keyword" (Palabra clave) aparece un menú desplegable. Selecciona "Toggle Diagnostics" (Alternar diagnóstico). Esto hará que siempre que el usuario diga la frase "toggle diagnostics" se desencadenará una acción. Ten en cuenta que es posible que tengas que expandir el "elemento 0" presionando la flecha que está junto a él.

![Imagen de la lección 5, capítulo 1, paso 6](images/Lesson5_chapter1_step6im.PNG)

7. Agrega el "script de control de la demostración de diagnóstico" para activar y desactivar el diagnóstico del contador de velocidad de fotogramas. Para ello, presiona el botón "add component" (agregar componente) y busca "diagnostics demo control script" (script de control de demostración de diagnóstico) y, a continuación, agrégalo del menú. Este script se puede agregar a cualquier objeto, pero por motivos de simplicidad, se agregará al mismo objeto que el controlador de entrada de voz. 

   > Nota: este script solo se incluye con estos módulos y no se incluye con MRTK original.

![Imagen de la lección 5, capítulo 1, paso 7](images/Lesson5_chapter1_step7im.PNG)

8. Agrega una nueva respuesta en el controlador de entrada de voz. Para ello, haz clic en el botón "+" que aparece más abajo, donde dice "response ()" (aparece marcado con una flecha verde en la siguiente imagen).

![Imagen de la lección 5, capítulo 1, paso 7](images/Lesson5_chapter1_step8.PNG)

9. Arrastra el objeto que contiene el script de los controles de demostración de diagnóstico a la nueva respuesta que acabas de crear en el paso 8.
    ![Imagen de la lección 5, capítulo 1, paso 9](images/Lesson5_chapter1_step9im.PNG)

10. Ahora, selecciona la lista desplegable "no function" (ninguna función), selecciona los controles de la demostración de diagnóstico y, a continuación, "on toggle diagnostics ()" (activar alternar diagnóstico). Esta función activa y desactiva el diagnóstico.  ![Imagen de la lección 5, capítulo 1, paso 10](images/Lesson5_chapter1_step10im.PNG)
    
> Ten en cuenta que antes de compilar en el dispositivo tendrás que habilitar la configuración del micrófono. Para ello, haz clic en el archivo, ve a los valores de compilación y, desde allí, a los valores del reproductor, y asegúrate de que está configurada la funcionalidad de micrófono.

A continuación, vamos a agregar la posibilidad de reproducir un archivo de audio a partir de un comando de voz mediante el objeto "octa". Recuerda que en la [lección 4](mrlearning-base-ch4.md) hemos agregado la posibilidad de reproducir un clip de audio simplemente tocando el objeto "octa". Vamos a aprovechar este mismo origen de audio para nuestro comando de voz de música.

11. Selecciona el objeto "octa" en la jerarquía del escenario básico.

12. Agrega otro controlador de entrada de voz (repite los pasos 4 y 5), pero con el objeto "octa". 

13. En lugar de agregar el comando de voz "Toggle Diagnostics" (Alternar diagnóstico) en el paso 6, agrega el comando de voz "play music" (reproducir música), tal como se muestra en la imagen siguiente.
    
     ![Imagen de la lección 5, capítulo 1, paso 13](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. Al igual que en los pasos 8 y 9, agrega una nueva respuesta y arrastra el objeto "octa" al recuadro vacío de la respuesta.

15. Selecciona el menú desplegable que dice "no function" (ninguna función), selecciona "Audio source" (Origen de audio) y, a continuación, selecciona "PlayOneShot (AudioClip)".

![Imagen de la lección 5, capítulo 1, paso 15](images/Lesson5_chapter1_step15im.PNG)

16. Para el clip de audio de este ejemplo vamos a usar el mismo de la [Lección 4](mrlearning-base-ch4.md). Entra en el panel de proyecto, busca el clip de audio "MRTK_Gem" y arrástralo al recuadro del origen de audio, como se muestra en la imagen siguiente. Ahora la aplicación debe poder responder a los comandos de voz "toggle diagnostics" (alternar diagnóstico) para activar o desactivar el panel de contadores de velocidad de fotogramas y "play music" (reproducir música) para reproducir la canción MRTK_Gem.
     ![Imagen de la lección 5, capítulo 1, paso 16](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>Gesto de desplazamiento panorámico 

En este capítulo, aprenderemos a usar los gestos de desplazamiento panorámico. Es útil para desplazarse (empleando un dedo o la mano para desplazarse por contenido). También puedes usar un gesto de desplazamiento panorámico para girar objetos, para recorrer una colección de objetos 3D, o incluso para desplazarte por una interfaz de usuario en 2D. Aprenderemos a usar los gestos de desplazamiento panorámico para deformar una textura. También examinaremos cómo mover una colección de objetos 3D.

1. Creación de un cuadrángulo. En la jerarquía del escenario básico, haz clic con el botón derecho y selecciona "3D Object" (Objeto 3D). A continuación, selecciona "Quad" (Cuadrángulo).

![Imagen de la lección 5, capítulo 2, paso 2](images/Lesson5_chapter2_step2im.PNG)

2. Cambia la posición del cuadrángulo según corresponda. En nuestro ejemplo, vamos a establecer x = 0, y = 0 y z = 1,5 fuera de la cámara para una posición cómoda con respecto a HoloLens 2.

   > Nota: Si el cuadrángulo bloquea (está enfrente de) algún contenido de las lecciones anteriores, asegúrate de moverlo de tal manera que deje de hacerlo.

3. Aplica un material al cuadrángulo. Este material será el material que vamos a desplazar con un gesto de desplazamiento panorámico. 

![Imagen de la lección 5, capítulo 2, paso 3](images/Lesson5_chapter2_step3im.PNG)

4. En el panel proyectos, escribe en el cuadro de búsqueda "pan content" (contenido panorámico). Arrastra ese material al cuadrángulo de su ejemplo. 

> Nota: El material "Pan content" (Contenido panorámico) no está incluido en MRTK, pero es uno de los recursos de este paquete de recursos del módulo que se importó en lecciones anteriores. 

> Nota: Cuando se agrega el contenido panorámico, este puede parecer alargado. Puedes solucionar este problema mediante el ajuste de los valores x, y y z del tamaño del cuadrángulo hasta que esté satisfecho con su aspecto.

Para usar los gestos de desplazamiento panorámico, necesitarás un colisionador en el objeto. Puede ver que el cuadrángulo ya tiene un colisionador de malla. Sin embargo, este no es el ideal ya que es extremadamente fino y difícil de seleccionar. Se recomienda reemplazar el colisionador de malla por un colisionador de cuadro.

5. Haz clic con el botón derecho en el colisionador de malla que está en el cuadrángulo (en el panel del inspector) y elimínalo haciendo clic en "remove component" (eliminar componente). 
   ![Imagen de la lección 5, capítulo 2, paso 5](images/Lesson5_chapter2_step5im.PNG)

6. Ahora, agrega el colisionador de cuadro haciendo clic en "add component" (agregar componente) y buscando "box collider" (colisionador de cuadro). El colisionador de cuadro agregado predeterminado es todavía muy delgado, así que haz clic en el botón "edit collider" (editar colisionador) para editarlo. Al presionarlo, puedes ajustar el tamaño con los valores x, y, y z o con los elementos del editor de escenas. En nuestro ejemplo, queremos ampliar el colisionador de cuadro un poco por detrás del cuadrángulo. En el editor de escenas, arrastra el colisionador de cuadro desde la parte posterior hacia el exterior (mira la imagen siguiente). Esto permitirá al usuario no solo usar sus dedos sino toda la mano para realizar desplazamientos. 
    ![Imagen de la lección 5, capítulo 2, paso 6](images/Lesson5_chapter2_step6im.PNG)
7. Hazlo interactivo. Como queremos interactuar con el cuadrángulo directamente, usaremos el componente "Near Interaction Touchable" (Interacción próxima: tocar) (también lo usamos en la Lección 4 para reproducir música del objeto "octa". Haz clic en "add component" (agregar componente) y busca "Near Interaction Touchable" (Interacción próxima: tocar) y selecciónalo como se muestra en las imágenes siguientes. 

8. Agrega la posibilidad de reconocer el gesto de desplazamiento panorámico. Haz clic en "add component" (agregar componente) y escriba "hand interaction pan" (desplazamiento panorámico con interacción de manos). Tendrás la posibilidad de elegir entre rayo de la mano (que te permitirá realizar un desplazamiento panorámico desde una cierta distancia) y el dedo índice. En este ejemplo, déjalo en dedo índice. 
    ![Imagen de la lección 5, capítulo 2, paso 7-8](images/Lesson5_chapter2_step7-8im.PNG)

![Imagen de la lección 5, capítulo 2, paso 8](images/Lesson5_chapter2_step8im.PNG)

9. En el script de desplazamiento panorámico con interacción de manos, las casillas "lock horizontal" (bloqueo horizontal) y "lock vertical" (bloqueo vertical) bloquearán esos movimientos respectivamente. La configuración de las texturas Wrap hará que la textura (asignación de textura) siga los movimientos panorámicos del usuario. En este ejemplo vamos a seleccionar esa casilla. También hay otra casilla, “velocity active” (velocidad activa) que, si no se selecciona, no funcionará el gesto de desplazamiento panorámico. Selecciona también esta casilla. Ahora ya deberías tener un cuadrángulo habilitado para los movimientos panorámicos.

   

   A continuación, vamos a aprender cómo realizar movimientos panorámicos de objetos 3D. 

10. Haz clic con el botón derecho en el cuadrángulo, selecciona 3D Object (Objeto 3D) y haz clic en "cube" (cubo). Escala el cubo para que los valores sean aproximadamente x = 0,1, y = 0,1 y z = 0,1. Copia ese cubo 3 veces (haciendo clic con el botón derecho en el cubo y presionando Duplicate (Duplicar), o bien pulsando Control o Command + D). Deje un espacio similar entre ellos. La escena debería tener el siguiente aspecto.

![Imagen de la lección 5, capítulo 2, paso 10](images/Lesson5_chapter2_step10im.PNG)







11. Selecciona de nuevo el cuadrángulo y en el script de desplazamiento panorámico con interacción de manos vamos a establecer las acciones del movimiento panorámico de cada uno de los cubos. En "pan event receivers" (Receptores de eventos de movimientos panorámicos) vamos a especificar el número de objetos que van a recibir el evento. Puesto que hay 4 cubos, escribe "4" y presiona ENTRAR. Deben aparecer 4 campos vacíos.


![Imagen de la lección 5, capítulo 2, paso 11](images/Lesson5_chapter2_step11im.PNG)



12. Arrastra cada uno de los cubos a cada uno de los recuadros de elementos vacíos.
     ![Imagen de la lección 5, capítulo 2, paso 12](images/Lesson5_chapter2_step12im.PNG)
    
13. Agrega el script "move with pan" (Desplazar con movimiento panorámico) a todos los cubos. Para ello, mantén presionado Control o Command y selecciona cada objeto. A continuación, en el panel del inspector, haz clic en "add component" (Agregar componente) y busca "move with pan" (Desplazar con movimiento panorámico). Haz clic en el script y este se agregará a cada cubo. Ahora ya se moverán los objetos 3D con gestos de desplazamiento panorámico. Si quitas la representación de la malla del cuadrángulo, ahora tienes un cuadrángulo invisible en el que puedes realizar movimientos panorámicos para recorrer una lista de objetos 3D.

### <a name="eye-tracking"></a>Seguimiento de los ojos

En este capítulo, vamos a explorar cómo habilitar el seguimiento de los ojos en nuestra demostración. Vamos a girar lentamente los elementos del menú 3D mediante mirada con los ojos. También vamos a desencadenar un divertido efecto cuando se seleccione el elemento con la mirada.

1. Asegúrate de que los perfiles de Mixed Reality Toolkit están configurados correctamente. Cuando se redactó este documento, la configuración del perfil de Mixed Reality Toolkit no incluía de forma predeterminada las funcionalidades de seguimiento de los ojos. Para agregarlas, sigue las instrucciones de la sección "Setting up the MRTK profiles required for Eye Tracking" (Configuración de los perfiles de MRTK para el seguimiento de los ojos) tal como se explica en la [documentación sobre Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ). Asegúrate de que el seguimiento de los ojos está configurado correctamente siguiendo los pasos restantes del vínculo anterior de documentación, incluido el habilitamiento del seguimiento de los ojos en GazeProvider (componente conectado a una cámara) y el habilitamiento del seguimiento de los ojos en el editor de Unity. Ten en cuenta que las próximas versiones de MRTK puede que incluyan ya esta funcionalidad de manera predeterminada.

    El vínculo anterior proporciona instrucciones breves para:

    - Crear el proveedor de datos para mirada con los ojos para su uso en el perfil de MRTK
    - Habilitar el seguimiento de los ojos en GazeProvider
    - Configurar una simulación del seguimiento de los ojos en el editor
    - Editar las funcionalidades de la solución Visual Studio para permitir el seguimiento de los ojos en la aplicación integrada

2. Agrega el componente Eye Tracking Target (Destino del seguimiento de los ojos) a los objetos de destino. Para permitir que un objeto responda a eventos de mirada con los ojos, necesitamos agregar el componente EyeTrackingTarget a cada objeto con el que queremos interactuar mediante esta funcionalidad. Agrega este componente a cada uno de los nueve objetos 3D que forman parte de la colección de la cuadrícula. Sugerencia: selecciona varios elementos de la jerarquía para agregar el componente EyeTrackingTarget en masa.
    ![Lección 5 Capítulo 3 Paso 2](images/Lesson5Chapter3Step2.JPG)

3. A continuación, vamos a agregar el script EyeTrackingTutorialDemo para conseguir varias interacciones muy interesantes. Este script se incluye como parte del repositorio de esa serie de tutoriales y no viene incluido de forma predeterminada con Mixed Reality Toolkit. Para cada objeto 3D de la colección de la cuadrícula, agrega el script EyeTrackingTutorialDemo buscando el componente en el menú "Add Component" (Agregar componente).
   ![Lección 5 Capítulo 3 Paso 3](images/Lesson5Chapter3Step3.JPG)

   4. Gira el objeto al examinar el destino. Nos gustaría configurar el objeto 3D para que girara mientras lo observamos. Para ello, inserta un nuevo campo en la sección "While Looking At Target" (Mientras se observa el destino) del componente EyeTrackingTarget, tal como se muestra en la imagen siguiente. 

![Lección 5 Capítulo 3 Paso 4a](images/Lesson5Chapter3Step4a.JPG)
![Lección 5 Capítulo 3 Paso 4b](images/Lesson5Chapter3Step4b.JPG)



En el campo recién creado, agrega el objeto GameObject actual al campo vacío y selecciona EyeTrackingTutorialDemo > RotateTarget() tal como se muestra en la imagen siguiente. Ahora el objeto 3D está configurado para girar cuando se le observa con seguimiento de los ojos. 

5. Capacidad adicional para enviar un sonido de ecolocalización al objeto de destino que se está mirando al seleccionarlo (pulsación en el aire o diciendo "Seleccionar") Al igual que en el paso 4, queremos desencadenar EyeTrackingTutorialDemo > BlipTarget() asignándolo al campo "Select()" de GameObject del componente EyeTrackingTarget, tal como se muestra en la ilustración siguiente. Con esto ya configurado, podrás notar un ligero sonido en GameObject cada vez que desencadenes una acción de selección como, por ejemplo, una pulsación en el aire o el comando de voz "seleccionar". 
    ![Lección 5 Capítulo 3 Paso 5](images/Lesson5Chapter3Step5.JPG)
6. Asegúrate de que las funcionalidades de seguimiento de los ojos están configuradas correctamente antes de empezar a crear en HoloLens 2. En el momento de redactar este documento, Unity no incluía todavía la posibilidad de configurar la funcionalidad de entrada mediante mirada (para el seguimiento de los ojos) La configuración de esta funcionalidad es necesaria para que el seguimiento de los ojos funcione en HoloLens 2. Sigue estas instrucciones de la documentación de Mixed Reality Toolkit para habilitar la funcionalidad de entrada con la mirada: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2. 


### <a name="congratulations"></a>Enhorabuena. 
Has conseguido agregar las funcionalidades básicas de seguimiento de los ojos a la aplicación. Estas acciones son solo el comienzo de un mundo lleno de posibilidades relacionadas con el seguimiento de los ojos. Este capítulo completa la Lección 5 en la que hemos aprendido sobre la funcionalidad de entrada de datos avanzada mediante comandos de voz, gestos de desplazamiento panorámico y seguimiento de los ojos. 

[Siguiente lección: Experiencia de ejemplo de montaje de módulo lunar](mrlearning-base-ch6.md)

