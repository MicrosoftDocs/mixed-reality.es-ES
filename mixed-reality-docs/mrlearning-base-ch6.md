---
title: 'Módulo base de aprendizaje de Mixed Reality: Experiencia de ejemplo de ensamblado del objeto Lunar Module'
description: En esta lección, vamos a agrupar varios conceptos aprendidos de lecciones anteriores para crear una experiencia de ejemplo.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730849"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>Módulo base de aprendizaje de Mixed Reality: Experiencia de ejemplo de ensamblado del objeto Lunar Module

En esta lección, vamos a agrupar varios conceptos aprendidos de lecciones anteriores para crear una experiencia de ejemplo. Crearemos una aplicación de ensamblado del módulo lunar en la que el usuario tendrá que usar las manos con seguimiento para recoger las piezas del módulo lunar e intentar ensamblarlo. Para activar o desactivar las sugerencias de colocación, restablecer nuestra experiencia y para lanzar nuestro módulo lunar al espacio se usarán botones presionables. En futuros tutoriales, continuaremos creando sobre esta experiencia, incluidos casos de uso multiusuario que aprovechan Azure Spatial Anchors para la alineación espacial.

## <a name="objectives"></a>Objetivos

- Agrupar varios conceptos de lecciones anteriores para crear una experiencia única
- Obtener información sobre cómo activar o desactivar los objetos
- Desencadenar eventos complejos mediante los botones presionables
- Usar la física y la fuerza de los cuerpos rígidos
- Explorar el uso de la información sobre herramientas

## <a name="instructions"></a>Instrucciones

### <a name="configuring-the-lunar-module"></a>Configuración del módulo lunar

En este capítulo, se nos introducirá a los distintos componentes necesarios para crear nuestra experiencia de ejemplo.

1. Agrega el objeto prefabricado del ensamblado del módulo lunar a la escena base. Para ello, en la pestaña del proyecto, busca "Rocket Launcher_Tutorial". También puedes buscar el objeto prefabricado en Assets > BaseModuleAssets > Prefabs (Recursos>RecursosDeMóduloBase>Objetos prefabricados). Puedes ver dos objetos prefabricados de lanzacohetes: uno con el nombre "tutorial" y otro con el nombre "completo". Arrastra el objeto prefabricado "Rocket Launcher_Tutorial" a la escena base. No dudes en situar la colocación del objeto prefabricado en tu escena.
   Nota: El objeto prefabricado "Rocket Launcher_Complete" es la lanzadera completada, que se proporciona como referencia. 

![Imagen de la lección 6, capítulo 1, paso 1](images/Lesson6_Chapter1_step1im.PNG)

Si expandes el objeto de juego "Rocket Launcher_Tutorial" en tu jerarquía y expandes aún más el objeto "Lunar Module", verás varios objetos secundarios que tienen un material llamado "x-ray". El material "x-ray" permite un color ligeramente translúcido que se usará como sugerencia de colocación para el usuario. 

![Imagen de la lección 6, capítulo 1, nota a](images/Lesson6_Chapter1_noteaim.PNG) Hay cinco partes del módulo lunar con las que el usuario va a interactuar, como se muestra en la siguiente imagen:

1.  El alojamiento del vehículo lunar
2.  El depósito de combustible
3.  La célula de energía
4.  El portal de acoplamiento 
5.  El sensor externo

![Imagen de la lección 6, capítulo 1, nota b](images/Lesson6_Chapter1_notebim.PNG)

> Nota: Los nombres de los objetos del juego que se ven en la jerarquía de la escena base no se corresponden con los nombres de los objetos de la escena.

Paso 2: Agrega un origen de audio al módulo lunar. Asegúrate de que el módulo lunar esté seleccionado en la jerarquía de la escena base y haz clic en "Add Component" (Agregar componente). Busca "Audio Source" (Origen de audio) y agrégalo al objeto. Déjalo en blanco por ahora. Se usará para reproducir el sonido del lanzamiento más adelante.
 ![Imagen de la lección 6, capítulo 1, paso 2](images/Lesson6_Chapter1_step2im.PNG) Paso 3: Agrega el script "Toggle placement hints" (Activar o desactivar sugerencias de colocación). Haz clic en "Add Component" (Agregar componente) y busca "Toggle placement hints" (Activar o desactivar sugerencias de colocación). Se trata de un script personalizado que te permite activar y desactivar las sugerencias translúcidas (objetos con el material de rayos x) se han mencionado antes. 
![Imagen de la lección 6, capítulo 1, paso 3](images/Lesson6_Chapter1_step3im.PNG) Paso 4: Como tenemos cinco objetos, escribe "5" para el tamaño de la matriz de los objetos del juego. Deberías ver aparecer cinco nuevos elementos. 

![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4bim.PNG)

Arrastra cada uno de los objetos translúcidos a los cuadros que dicen "None (Game Object)" (Ninguno [Objeto del juego]). Arrastra los siguientes objetos del módulo lunar a tu escena base: 

• Backpack

• GasTank

• Topleftbody

• Nose

• LeftTwirler

 ![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4aim.PNG)

Ahora ya está configurado el script "Toggle placement hints" (Activar o desactivar sugerencias de colocación). Esto nos permitirá activar y desactivar las sugerencias.

Paso 5: Agrega el script "Launch lunar module" (Lanzar el módulo lunar). Haz clic en el botón "Add Component" (Agregar componente), busca "Launch lunar module" (Lanzar módulo lunar) y selecciónalo. Este script será responsable de lanzar el módulo lunar. Cuando presionamos un botón configurado, se agregará una fuerza ascendente al componente de un cuerpo rígido del módulo lunar y hará que el módulo se impulse hacia arriba. Si estás en el interior, el módulo lunar puede chocar con la malla del techo. Pero si estás en el exterior, volará al espacio indefinidamente. 

![Imagen de la lección 6, capítulo 1, paso 5](images/Lesson6_Chapter1_step5im.PNG)

Paso 6: Ajusta el impulso de modo que el módulo lunar vuele hacia arriba con elegancia. Prueba con un valor de 0,01. Deja en blanco el campo "Rb". RB significa "cuerpo rígido" y este campo se rellenará automáticamente durante el tiempo de ejecución.

![Imagen de la lección 6, capítulo 1, paso 6](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Introducción a la piezas del módulo lunar
El objeto primario de las piezas del módulo lunar es la colección de objetos con los que interactuará el usuario. Los nombres de los objetos del juego (con los nombres de las escenas etiquetados entre paréntesis) se indican en la siguiente lista:

- Backpack (Depósito de combustible)
- GasTank (Célula de energía)
- TopLeftBody (Alojamiento del vehículo lunar)
- Nose (Portal de acoplamiento)
- LeftTwirler (Sensor externo)

Ten en cuenta que cada uno de estos objetos tiene un controlador de manipulación, tal como se vio en la lección 4. Con el controlador de manipulación, los usuarios pueden agarrar y manipular el objeto. Ten en cuenta también que la configuración de "Two handed manipulation type" (Manipulación con dos manos) se establece en "Move and rotate" (Mover y girar). Esto solo permite al usuario mover el objeto y no cambiar su tamaño, que es la funcionalidad deseada para una aplicación de ensamblado.
Además, la manipulación remota no se controla para permitir solo la interacción directa de las piezas del módulo.

![Imagen de la lección 6, capítulo 2](images/Lesson6_Chapter2im.PNG)

El script de demostración del ensamblado de piezas (que se muestra arriba) es el script que administra los objetos que el usuario debe colocar en el módulo lunar. 

El campo "Object To Place" (Objeto para colocar) es la transformación que se selecciona (en el caso de la imagen de arriba, la mochila o depósito de combustible) con el objeto al que se puede conectar. 

Los valores "Near Distance" (Distancia cercana) y "Far Distance" (Distancia lejana) son responsables de determinar la proximidad a las piezas que se van a acoplar o soltar. Por ejemplo, la mochila o depósito de combustible tendría que estar a 0,1 unidades del módulo lunar para que se acople en su sitio. El valor de "Far Distance" (Distancia lejana) establece la ubicación donde el objeto debe estar para separarse del módulo lunar. En este caso, la mano del usuario debe sujetar la mochila o depósito de combustible y alejarla 0,2 unidades del módulo lunar para evitar que vuelva a acoplarse en su lugar.

La opción "Tool Tip Object" (Objeto de información sobre herramientas) es la etiqueta de información sobre las herramientas de la escena. Cuando los objetos están acoplados en su lugar, se deshabilitará la etiqueta. 

La opción "Audio Source" (Origen de audio) se selecciona automáticamente. 

### <a name="placement-hints-buttons"></a>Botones de sugerencias de colocación
En la [lección 2](mrlearning-base-ch2.md), has aprendido a colocar y configurar botones para hacer cosas como cambiar el color de un elemento o hacer que se reproduzca un sonido cuando se pulsa. Seguiremos utilizando estos principios a medida que configuramos nuestros botones para alternar las sugerencias de colocación. 

El objetivo es configurar nuestro botón para que cada vez que el usuario pulse el botón de sugerencia de colocación, cambie la visibilidad de las sugerencias de colocación translúcidas. 

Paso 1: Mueve el módulo lunar al recuadro vacío "Runtime only" (Solo en tiempo de ejecución) en el panel de inspección mientras el objeto Placement Hints (Sugerencias de colocación) está seleccionado en la jerarquía de la escena base. 
 ![Imagen de la lección 6, capítulo 3, paso 1](images/Lesson6_Chapter3_step1im.PNG) Paso 2: Ahora haz clic en la lista desplegable, donde dice "No function" (Ninguna función). Desplázate hacia abajo a "TogglePlacementHints" y, debajo de ese menú, selecciona "ToggleGameObjects ()". ToggleGameObjects() activará y desactivará las sugerencias de colocación para que estén visibles o no cada vez que se presiona el botón.
 ![Imagen de la lección 6, capítulo 3, paso 2](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configuración del botón Reset (Restablecer)

Habrá situaciones en las que el usuario comete un error o expulsa accidentalmente un objeto, o simplemente quiere restablecer la experiencia. El botón Reset (Restablecer) agregará la capacidad de reiniciar la experiencia. 

Paso 1: Selecciona el botón Reset (Restablecer). En la escena base, se llama "ResetRoundButton". 

Paso 2: Arrastra el módulo lunar desde la jerarquía de la escena base hasta el recuadro vacío debajo de "Button pressed" (Botón presionado) en el panel del inspector.
 ![Imagen de la lección 6, capítulo 4, paso 2](images/Lesson6_Chapter4_step2im.PNG)

Paso 3: Selecciona el menú desplegable que indica "No function" (Ninguna función) y mantén el puntero en "LaunchLunarModule". Ahora, selecciona "resetModule ()".

![Imagen de la lección 6, capítulo 4, paso 3](images/Lesson6_Chapter4_step3im.PNG)

> Nota: Observarás que, de manera predeterminada, el objeto "GameObject.BroadcastMessage" está configurado en "ResetPlacement". Esto difundirá un mensaje llamado "ResetPlacement" para cada objeto secundario de RocketLauncher_Tutorial. Cualquier objeto que tenga un método para "ResetPlacement()" responderá a ese mensaje restableciendo su posición. 

### <a name="launching-the-lunar-module"></a>Lanzamiento del módulo lunar
En este capítulo vamos a configurar el botón de lanzamiento. Esto permitirá al usuario pulsar el botón y lanzar el módulo lunar al espacio.

Paso 1: Selecciona el botón de lanzamiento (en la escena base se denomina "LaunchRoundButton"). Arrastra el módulo lunar al recuadro vacío en "Touch End" (Tocar terminar) en el panel del inspector.
 ![Imagen de la lección 6, capítulo 5, paso 1](images/Lesson6_Chapter5_step1im.PNG) Paso 2: Selecciona el menú desplegable que indica "No Function" (Ninguna función). Mantén el puntero en "LaunchLunarModule" y selecciona "StopThruster ()". Esto controlará cuánto impulso quiere dar el usuario al módulo lunar. 
 ![Imagen de la lección 6, capítulo 5, paso 2](images/Lesson6_Chapter5_step2im.PNG) Paso 3: En "ButtonPressed()", agrega el módulo lunar (haz clic, mantén y arrastra) al recuadro vacío. 

Paso 4: Haz clic en el menú desplegable que indica "No function" (Ninguna función) y mantén el puntero en "LaunchLunarModule" y selecciona "StartThruster ()". 
 ![Imagen de la lección 6, capítulo 5, paso 4](images/Lesson6_Chapter5_step4im.PNG) Paso 5: Agrega música al módulo lunar para que cuando el cohete despegue, se reproducirá la música. Para ello, arrastra el módulo lunar al siguiente recuadro vacío en "ButtonPressed()".

Paso 6: Selecciona el menú desplegable que dice "No function" (Ninguna función), mantén el puntero en "AudioSource" y, a continuación, selecciona "PlayOneShot (AudioClip)". No dudes en explorar la variedad de sonidos que se incluyen con MRTK. En este ejemplo, vamos a ceñirnos a "MRTK_Gem".
 ![Imagen de la lección 6, capítulo 5, paso 6](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Enhorabuena 
¡Ya has configurado totalmente esta aplicación! Ahora, al presionar el botón de reproducir, puedes ensamblar completamente el módulo lunar, activar o desactivar las sugerencias, lanzar el módulo lunar y restablecerlo para hacerlo todo de nuevo.
