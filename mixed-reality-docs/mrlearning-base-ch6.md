---
title: 'Tutoriales de introducción: 7. Crear una aplicación de ejemplo de módulo lunar'
description: En esta lección, combinará varios conceptos aprendidos en lecciones anteriores para crear una experiencia de ejemplo única.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926517"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. crear una aplicación de ejemplo de módulo lunar

En este tutorial, se combinan varios conceptos de lecciones anteriores para crear una experiencia de ejemplo única. Aprenderá a crear una aplicación de ensamblado de módulo lunar en la que un usuario necesita usar manos con seguimiento para recoger los elementos del módulo lunar e intentar ensamblar un módulo lunar. Usamos botones que se utilizan para alternar las sugerencias de colocación, restablecer nuestra experiencia y lanzar el módulo lunar en el espacio. En los tutoriales futuros, se seguirá generando a partir de esta experiencia, que incluye eficaces casos de uso de varios usuarios que aprovechan los delimitadores espaciales de Azure para la alineación espacial.

## <a name="objectives"></a>Objetivos

- Agrupar varios conceptos de lecciones anteriores para crear una experiencia única
- Obtener información sobre cómo activar o desactivar los objetos
- Desencadenar eventos complejos mediante los botones presionables
- Usar la física y la fuerza de los cuerpos rígidos
- Explorar el uso de la información sobre herramientas

## <a name="instructions"></a>Instrucciones

### <a name="configuring-the-lunar-module"></a>Configuración del módulo lunar

En esta sección, se presentan los distintos componentes necesarios para crear nuestra experiencia de ejemplo.

1. Agregue el ensamblado del módulo lunar recurso prefabricado a la escena base. Para ello, en la pestaña proyecto, vaya a activos > BaseModuleAssets > Prefabs. Verá dos Prefabs del selector de Rocket, arrastre el Rocket Launcher_Tutorial recurso prefabricado a la escena y colóquelo como desee.

    >[!NOTE]
    >El Rocket Launcher_Complete recurso prefabricado es el selector completado, proporcionado como referencia.

    ![Imagen de la lección 6, capítulo 1, paso 1](images/Lesson6_Chapter1_step1im.PNG)

    Si expande el objeto Rocket Launcher_Tutorial Game en la jerarquía y expande aún más el objeto de módulo lunar, encontrará varios objetos secundarios que tienen un material denominado "x-Ray". El material "x-Ray" permite un color ligeramente translúcido que se usará como sugerencias de selección de ubicación para el usuario. 

    ![Lesson6 archivo chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    Hay cinco partes en el módulo lunar con las que interactuará el usuario, tal como se muestra en la imagen siguiente:

    1. El alojamiento del vehículo lunar
    2. El depósito de combustible
    3. La célula de energía
    4. El portal de acoplamiento
    5. El sensor externo

    ![Imagen de la lección 6, capítulo 1, nota b](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    >Los nombres de los objetos del juego que se ven en la jerarquía de la escena base no se corresponden con los nombres de los objetos de la escena.

2. Agregue un origen de audio al objeto de juego LunarModule. Asegúrese de que LunarModule está seleccionado en la jerarquía de la escena y haga clic en Agregar componente. Busque el origen de audio y agréguelo al objeto Game. Deje el campo AudioClip en blanco por ahora, pero cambie la configuración de Blend especial de 0 a 1 para habilitar el audio espacial. Usará este origen de audio para reproducir el sonido de inicio más adelante.

    ![Lesson6 archivo chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. Agregue las sugerencias de alternancia de colocación del script. Haga clic en Agregar componente y busque sugerencias de alternancia de ubicación. Se trata de un script personalizado que le permite activar y desactivar las sugerencias translúcidas (objetos con el material de rayos x), como se mencionó anteriormente.

    ![Lesson6 archivo chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. Dado que tenemos cinco objetos, escriba "5" para el tamaño de la matriz de objetos de juego. Verá que aparecen cinco nuevos elementos.

    ![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4bim.PNG)

    Arrastre cada uno de los objetos translúcidos a todos los cuadros nombre (objeto de juego). Arrastre los siguientes objetos desde el módulo lunar de la escena hasta los campos de la matriz de objetos, tal como se muestra en la imagen anterior:

    ![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4aim.PNG)

    El script Toggle Placement hints se ha configurado ahora, lo que nos permite activar y desactivar las sugerencias.

5. Agregue el script Launch lunar del módulo. Haga clic en el botón Agregar componente, busque "iniciar módulo lunar" y selecciónelo. Este script inicia el módulo lunar. Cuando se presiona un botón configurado, agrega una fuerza ascendente al componente del cuerpo rígido del módulo lunar y hace que el módulo se inicie hacia arriba. Si estás en el interior, el módulo lunar puede chocar con la malla del techo. Si se encuentran en un área con límites máximos o sin límites, el módulo lunar entrará en el espacio indefinidamente.

    ![Imagen de la lección 6, capítulo 1, paso 5](images/Lesson6_Chapter1_step5im.PNG)

6. Ajusta el impulso de modo que el módulo lunar vuele hacia arriba con elegancia. Prueba con un valor de 0,01. Deja en blanco el campo "Rb". RB significa cuerpo rígido y este campo se rellenará automáticamente durante el tiempo de ejecución.

    ![Imagen de la lección 6, capítulo 1, paso 6](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Información general sobre los elementos del módulo lunar

El objeto primario de los elementos de módulo lunar es la colección de los objetos con los que el usuario interactúa. Los nombres de los objetos de juego con la escena con la etiqueta nombres entre paréntesis se muestran en la lista siguiente:

- Mochila (célula de energía)
- GasTank (depósito de combustible)
- TopLeftBody (Alojamiento del vehículo lunar)
- Nose (Portal de acoplamiento)
- LeftTwirler (Sensor externo)

Observe que cada uno de estos objetos tiene un controlador de manipulación, como se explica en la lección 4. Esta característica permite a los usuarios tomar y manipular el objeto. Tenga en cuenta también que el valor, el tipo de manipulación de dos manos, se establece en Move y rotate. Esta opción solo permite al usuario desplace el objeto y no cambie su tamaño, que es la funcionalidad deseada para una aplicación de ensamblado.
Además, la manipulación lejana está desactivada para permitir solo la interacción directa de las partes del módulo.

![Imagen de la lección 6, capítulo 2](images/Lesson6_Chapter2im.PNG)

El script de demostración del ensamblado de elementos (mostrado anteriormente) es el script que administra los objetos que el usuario coloca en el módulo lunar.

El campo objeto que se va a colocar es la transformación seleccionada, tal como se muestra en la imagen anterior, el tanque de la mochila/combustible asociado al objeto al que se conecta.

La configuración de la distancia cercana y de la distancia determina la proximidad a la que se ajustan o se pueden liberar los elementos. Por ejemplo, el tanque de la mochila o el depósito de combustible debe ser de 0,1 unidades del módulo lunar antes de que se ajuste. La configuración de distancia de distancia establece la ubicación donde puede estar el objeto antes de que se pueda desasociar del módulo lunar. En este caso, la mano del usuario debe sujetar la mochila o depósito de combustible y alejarla 0,2 unidades del módulo lunar para evitar que vuelva a acoplarse en su lugar.

El objeto de información sobre herramientas es la etiqueta de información sobre herramientas de la escena. Cuando se ajustan los objetos en su lugar, la etiqueta está deshabilitada.

El origen de audio se captura automáticamente.

### <a name="configuring-the-placement-hints-button"></a>Configuración del botón sugerencias de selección de ubicación

En la [Lección 2](mrlearning-base-ch2.md), ha aprendido a colocar y configurar botones para realizar acciones como cambiar el color de un elemento o hacer que se reproduzca un sonido al insertarlo. Seguiremos utilizando estos principios a medida que configuramos nuestros botones para alternar las sugerencias de colocación.

El objetivo es configurar nuestro botón para que cada vez que el usuario presione el botón de la sugerencia de selección de ubicación, alterne la visibilidad de las sugerencias de colocación translúcidas.

1. Mueva el módulo lunar a la ranura vacío en tiempo de ejecución en el panel Inspector mientras el objeto sugerencias de colocación está seleccionado en la jerarquía de escenas base.

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. Haga clic en la lista desplegable ninguna función. Vaya a TogglePlacementHints y seleccione ToggleGameObjects () en ese menú. ToggleGameObjects () activa y desactiva las sugerencias de selección de ubicación para que sean visibles o invisibles cada vez que se presiona el botón.

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configuración del botón restablecer

Habrá situaciones en las que el usuario comete un error, produce accidentalmente el objeto o simplemente desea restablecer la experiencia. El botón Restablecer agrega la posibilidad de reiniciar la experiencia.

1. Seleccione el botón Restablecer. En la escena base, se denomina ResetRoundButton.

2. Arrastre el módulo lunar desde la jerarquía de escenas base hasta la ranura vacía en el botón presionado en el panel del inspector.

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. Seleccione el menú desplegable ninguna función y mantenga el mouse sobre LaunchLunarModule y, a continuación, seleccione resetModule ().

    ![Imagen de la lección 6, capítulo 4, paso 3](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    >Tenga en cuenta que, de forma predeterminada, GameObject. BroadcastMessage se configura como ResetPlacement. Esto difunde un mensaje denominado ResetPlacement para cada objeto secundario del RocketLauncher_Tutorial. Cualquier objeto que tenga un método para ResetPlacement () responde a ese mensaje restableciendo su posición.

### <a name="configuring-the-launch-button"></a>Configuración del botón Launch

En esta sección se explica cómo configurar el botón Launch, que permite al usuario presionar el botón e iniciar el módulo lunar en el espacio.

1. Seleccione el botón Launch (iniciar). En la escena base, se denomina LaunchRoundButton. Arrastre el módulo lunar a la ranura vacía de Touch end en el panel Inspector.

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. Seleccione el menú desplegable ninguna función y mantenga el mouse sobre LaunchLunarModule y seleccione StopThruster (). Controla la cantidad de empuje que el usuario desea dar al módulo lunar.

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. Arrastre el módulo lunar desde la jerarquía de escenas base hasta la ranura vacía en el botón presionado en el panel del inspector.

4. Haga clic en el menú desplegable ninguna función y, a continuación, en LaunchLunarModule y seleccione StartThruster ().

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. Agregue música al módulo lunar para que se reproduzca cuando se desactive el cohete. Para ello, arrastre el módulo lunar a la siguiente ranura vacía en el botón presionado ().

6. Seleccione el menú desplegable ninguna función, mantenga el mouse sobre AudioSource y seleccione PlayOneShot (AudioClip). No dudes en explorar la variedad de sonidos que se incluyen con MRTK. En este ejemplo, usaremos "MRTK_Gem".

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a>Enhorabuena

Ha configurado completamente esta aplicación. Ahora, cuando presione reproducir, puede ensamblar completamente el módulo lunar, alternar sugerencias, iniciar el módulo lunar y restablecerlo para que se inicie de nuevo.
