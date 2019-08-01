---
title: 'Tutoriales de introducción: 7. Crear una aplicación de ejemplo de módulo lunar'
description: En esta lección, vamos a agrupar varios conceptos aprendidos de lecciones anteriores para crear una experiencia de ejemplo.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 97dd8fce1ebe53efc37cb48cde7dc9e207be9a42
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701992"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Crear una aplicación de ejemplo de módulo lunar

En este tutorial, se combinan varios conceptos presentados en las lecciones anteriores para crear una experiencia de ejemplo única. Crearemos una aplicación de ensamblado de módulo lunar en la que un usuario necesita usar manos con seguimiento para recoger los elementos del módulo lunar e intentar ensamblar un módulo lunar. Usamos botones que se utilizan para alternar las sugerencias de colocación, restablecer nuestra experiencia y lanzar el módulo lunar en el espacio. En los tutoriales futuros, se seguirá generando a partir de esta experiencia, que incluye eficaces casos de uso de varios usuarios que aprovechan los delimitadores espaciales de Azure para la alineación espacial.

## <a name="objectives"></a>Objetivos

- Agrupar varios conceptos de lecciones anteriores para crear una experiencia única
- Obtener información sobre cómo activar o desactivar los objetos
- Desencadenar eventos complejos mediante los botones presionables
- Usar la física y la fuerza de los cuerpos rígidos
- Explorar el uso de la información sobre herramientas

## <a name="instructions"></a>Instrucciones

### <a name="configuring-the-lunar-module"></a>Configuración del módulo lunar

En esta sección, se presentan los distintos componentes necesarios para crear nuestra experiencia de ejemplo.

1. Agregue el ensamblado del módulo lunar recurso prefabricado a la escena base. Para ello, en la pestaña proyecto, busque Rocket Launcher_Tutorial. 
Busque recurso prefabricado en assets-> BaseModuleAssets-> Prefabs. También verá dos Prefabs del selector de Rocket; uno con el nombre "Tutorial" y el otro con el nombre "completo". Arrastre el recurso prefabricado de Rocket Launcher_Tutorial a la escena base y colóquelo como desee.
   Nota: Rocket Launcher_Complete recurso prefabricado es el selector completado, proporcionado como referencia. 

![Imagen de la lección 6, capítulo 1, paso 1](images/Lesson6_Chapter1_step1im.PNG)

Si expande el objeto de juego Rocket Launcher_Tutorial en la jerarquía y expande aún más el objeto de módulo lunar, encontrará varios objetos secundarios que tienen un material denominado "x-Ray". El material "x-Ray" permite un color ligeramente translúcido que se va a usar como sugerencia de selección de ubicación para el usuario. 

![Lesson6 archivo chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) hay cinco partes en el módulo lunar con las que interactuará el usuario, tal y como se muestra en la imagen siguiente:

1.  El alojamiento del vehículo lunar
2.  El depósito de combustible
3.  La célula de energía
4.  El portal de acoplamiento 
5.  El sensor externo

![Imagen de la lección 6, capítulo 1, nota b](images/Lesson6_Chapter1_notebim.PNG)

> Nota: Los nombres de objetos de juego que se ven en la jerarquía de escenas base no se corresponden con los nombres de los objetos de la escena.

Paso 2: Agrega un origen de audio al módulo lunar. Asegúrese de que el módulo lunar está seleccionado en la jerarquía de escenas base y haga clic en Agregar componente. Busque el origen de audio y agréguelo al objeto. Déjalo en blanco por ahora. Se usará para reproducir el sonido del lanzamiento más adelante.

 ![Lesson6 archivo chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)  
Paso 3: Agregue el script, alterne las sugerencias de colocación. Haga clic en Agregar componente y busque sugerencias de alternancia de ubicación. Se trata de un script personalizado que le permite activar y desactivar las sugerencias translúcidas (objetos con material x-ray) mencionadas anteriormente.  
![Lesson6 archivo chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)  
Paso 4: Dado que tenemos cinco objetos, escriba "5" para el tamaño de la matriz de objetos de juego. Verá que aparecen cinco nuevos elementos.  


![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4bim.PNG)

Arrastre cada uno de los objetos translúcidos a todos los cuadros nombre (juego).
Arrastra los siguientes objetos del módulo lunar a tu escena base: 

• Backpack

• GasTank

• Topleftbody

• Nose

• LeftTwirler

 ![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4aim.PNG)

Ahora se configura el script para alternar sugerencias de colocación. Esto nos permite activar y desactivar las sugerencias.

Paso 5: Agregue el script Launch lunar del módulo. Haga clic en el botón Agregar componente, busque "iniciar módulo lunar" y selecciónelo. Este script inicia el módulo lunar. Cuando se presiona un botón configurado, agrega una fuerza ascendente al componente del cuerpo rígido del módulo lunar y hace que el módulo se inicie hacia arriba. Si estás en el interior, el módulo lunar puede chocar con la malla del techo. Pero si estás en el exterior, volará al espacio indefinidamente. 

![Imagen de la lección 6, capítulo 1, paso 5](images/Lesson6_Chapter1_step5im.PNG)

Paso 6: Ajusta el impulso de modo que el módulo lunar vuele hacia arriba con elegancia. Prueba con un valor de 0,01. Deja en blanco el campo "Rb". RB significa "cuerpo rígido" y este campo se rellenará automáticamente durante el tiempo de ejecución.

![Imagen de la lección 6, capítulo 1, paso 6](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Información general sobre los elementos del módulo lunar
El objeto primario de los elementos de módulo lunar es la colección de los objetos con los que el usuario interactúa. En la lista siguiente se proporcionan los nombres de objeto de juego, con los nombres con etiqueta de escena en paretheses:

- Backpack (Depósito de combustible)
- GasTank (Célula de energía)
- TopLeftBody (Alojamiento del vehículo lunar)
- Nose (Portal de acoplamiento)
- LeftTwirler (Sensor externo)

Observe que cada uno de estos objetos tiene un controlador de manipulación como se describe en la lección 4. Con el controlador de manipulación, los usuarios pueden tomar y manipular el objeto. Tenga en cuenta también que la configuración de, el tipo de manipulación de dos manos está establecida en movimiento y giro. Esto solo permite al usuario mover el objeto y no cambiar su tamaño, que es la funcionalidad deseada para una aplicación de ensamblado.
Además, la manipulación lejana está desactivada para permitir solo la interacción directa de las partes del módulo.

![Imagen de la lección 6, capítulo 2](images/Lesson6_Chapter2im.PNG)

El script de demostración del ensamblado de elementos (mostrado anteriormente) es el script que administra los objetos que el usuario coloca en el módulo lunar. 

El campo objeto que se va a colocar es la transformación seleccionada, tal como se muestra en la imagen anterior, el tanque de la mochila/combustible asociado al objeto al que se conecta. 

La configuración de la distancia cercana y de la distancia determina la proximidad a la que se ajustan o se pueden liberar los elementos. Por ejemplo, el tanque de la mochila o el depósito de combustible debe ser de 0,1 unidades del módulo lunar antes de que se ajuste. La configuración de distancia de distancia establece la ubicación donde puede estar el objeto antes de que se pueda desasociar del módulo lunar. En este caso, la mano del usuario debe sujetar la mochila o depósito de combustible y alejarla 0,2 unidades del módulo lunar para evitar que vuelva a acoplarse en su lugar.

El objeto de información sobre herramientas es la etiqueta de información sobre herramientas de la escena. Cuando se ajustan los objetos en su lugar, la etiqueta está deshabilitada. 

El origen de audio se captura automáticamente. 

### <a name="placement-hints-buttons"></a>Botones de sugerencias de colocación
En la [lección 2](mrlearning-base-ch2.md), has aprendido a colocar y configurar botones para hacer cosas como cambiar el color de un elemento o hacer que se reproduzca un sonido cuando se pulsa. Seguiremos utilizando estos principios a medida que configuramos nuestros botones para alternar las sugerencias de colocación. 

El objetivo es configurar nuestro botón para que cada vez que el usuario presione el botón de la sugerencia de selección de ubicación, alterne la visibilidad de las sugerencias de colocación translúcidas. 

Paso 1: Mueva el módulo lunar a la ranura vacío en tiempo de ejecución en el panel Inspector mientras el objeto sugerencias de colocación está seleccionado en la jerarquía de escenas base. 
 ![Imagen de la lección 6, capítulo 3, paso 1](images/Lesson6_Chapter3_step1im.PNG) Paso 2: Ahora haga clic en la lista desplegable sin funciones. Vaya a TogglePlacementHints y, en ese menú, seleccione ToggleGameObjects (). ToggleGameObjects () activa y desactiva las sugerencias de selección de ubicación para que sean visibles o invisibles cada vez que se presiona el botón.  
 ![Imagen de la lección 6, capítulo 3, paso 2](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configuración del botón restablecer

Habrá situaciones en las que el usuario comete un error, o bien produce accidentalmente el objeto o simplemente quiere restablecer la experiencia. El botón Restablecer agrega la posibilidad de reiniciar la experiencia. 

Paso 1: Seleccione el botón Restablecer. En la escena base, se denomina ResetRoundButton. 

Paso 2: Arrastre el módulo lunar desde la jerarquía de escenas base hasta la ranura vacía en el botón, que se ha presionado en el panel Inspector.
 ![Imagen de la lección 6, capítulo 4, paso 2](images/Lesson6_Chapter4_step2im.PNG)

Paso 3: Seleccione el menú desplegable ninguna función y mantenga el mouse sobre LaunchLunarModule, seleccione resetModule ().

![Imagen de la lección 6, capítulo 4, paso 3](images/Lesson6_Chapter4_step3im.PNG)

> Nota: Tenga en cuenta que, de forma predeterminada, GameObject. BroadcastMessage se configura como ResetPlacement. De este método se emite un mensaje denominado ResetPlacement para cada objeto secundario de RocketLauncher_Tutorial. Cualquier objeto que tenga un método para ResetPlacement () responde a ese mensaje restableciendo su posición. 

### <a name="launching-the-lunar-module"></a>Inicio del módulo lunar
En esta sección se explaings cómo configurar el botón Launch (iniciar). Esto permite al usuario presionar el botón e iniciar el módulo lunar en el espacio.

Paso 1: Seleccione el botón Launch (iniciar). En la escena base, se llama a LaunchRoundButton. Arrastre el módulo lunar a la ranura vacía de Touch end en el panel Inspector.
 ![Imagen de la lección 6, capítulo 5, paso 1](images/Lesson6_Chapter5_step1im.PNG) Paso 2: Seleccione el menú desplegable ninguna función y mantenga el mouse sobre LaunchLunarModule y seleccione StopThruster (). Controla la cantidad de empuje que el usuario desea dar al módulo lunar. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
Paso 3: En ButtonPressed (), agregue el módulo lunar (haga clic, mantenga presionado y arrastre) a la ranura vacía. 

Paso 4: Haga clic en el menú desplegable sin funciones y mantenga el mouse sobre LaunchLunarModule y seleccione StartThruster (). 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
Paso 5: Agregue música al módulo lunar para que se reproduzca cuando se desactive el cohete. Para ello, arrastre el módulo lunar a la siguiente ranura vacía en el botón presionado ().

Paso 6: Seleccione el menú desplegable ninguna función, mantenga el mouse sobre AudioSource y seleccione PlayOneShot (AudioClip). No dudes en explorar la variedad de sonidos que se incluyen con MRTK. En este ejemplo, usaremos "MRTK_Gem".
 ![Imagen de la lección 6, capítulo 5, paso 6](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Enhorabuena 
Ha configurado completamente esta aplicación. Ahora, cuando presione reproducir, puede ensamblar completamente el módulo lunar, alternar sugerencias, iniciar el módulo lunar y restablecerlo para que se vuelva a iniciar.
