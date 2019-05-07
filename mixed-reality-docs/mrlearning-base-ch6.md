---
title: Módulo de la Base de aprendizaje de MR - experiencia de ejemplo de ensamblado de módulo Lunar
description: En esta lección, combinamos varios conceptos aprendidos lecciones anteriores para crear una experiencia única de ejemplo.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: 303ed17724ba8799490aa7bca7a60600f6e5349b
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929602"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>Módulo de la Base de aprendizaje de MR - experiencia de ejemplo de ensamblado de módulo Lunar

En esta lección, combinamos varios conceptos aprendidos lecciones anteriores para crear una experiencia única de ejemplo. Se creará una aplicación de ensamblado de módulo lunar mediante el cual un usuario deberá usar manos sometidas a seguimiento para recoger las partes del módulo lunar e intenta ensamblar un módulo lunar. Para activar o desactivar las sugerencias de colocación, restablecer nuestra experiencia y para iniciar nuestro módulo lunar en el espacio se usará botones pressable! En el futuro tutoriales, seguiremos se basan en esta experiencia, incluidos eficaz multiusuario casos de uso que aprovecha Azure espacial delimitadores para la alineación espacial.

## <a name="objectives"></a>Objetivos

- Combinar varios conceptos de las lecciones anteriores para crear una experiencia única
- Obtenga información sobre cómo activar o desactivar los objetos
- Desencadenar eventos complejos mediante los botones pressable
- Usar cuerpo rígido física y fuerza
- Explore el uso de información sobre herramientas

## <a name="instructions"></a>Instrucciones

### <a name="configuring-the-lunar-module"></a>Configuración del módulo Lunar

En este capítulo, se recibirá una introducción a los distintos componentes necesarios para crear nuestra experiencia de ejemplo.

1. Agregar el ensamblado de módulo lunar prefabricado verá a la escena de la Base. Para ello, en la ficha de proyecto, busque "Rocket Launcher_Tutorial." También puede encontrar el recurso prefabricado de activos > BaseModuleAssets > prefabricados. Es posible que vea dos prefabricados del iniciador de rocket; uno con el nombre "tutorial" y otro con el nombre "completan". Arrastre el recurso prefabricado "Rocket Launcher_Tutorial" a la escena de la Base. No dude en colocar la colocación del prefabricado verá en la escena.
   Nota: El recurso prefabricado "Rocket Launcher_Complete" es el iniciador completado, proporcionado como referencia. 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

Si se expanda el objeto de juego "Rocket Launcher_Tutorial" en la jerarquía y expandir el objeto "Módulo Lunar", verá varios objetos secundarios que tienen un material denominado "de rayos x." El material de "rayos x" permite que un color ligeramente translúcido que se usará como sugerencias de selección de ubicación para el usuario. 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) hay cinco partes al módulo lunar que el usuario que va a interactuar con, como se muestra en la imagen siguiente:

1.  El alojamiento de viajero
2.  El depósito de combustible
3.  La celda de energía
4.  El Portal de acoplamiento 
5.  El sensor externo

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> Nota: Los nombres de objeto de juego que ve en la jerarquía escena base no corresponden a los nombres de los objetos de la escena.

Paso 2: Agregar un origen de audio para el módulo lunar. Asegúrese de que el módulo lunar está seleccionado en la jerarquía escena base y haga clic en "Agregar el componente". Busque "Origen de Audio" y agregarlo al objeto. Déjelo en blanco por ahora. Se usará para reproducir el sonido de inicio más adelante.
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) paso 3: Agregue el script "activar o desactivar sugerencias de selección de ubicación". Haga clic en "Agregar componente" y busque "Activar o desactivar sugerencias de selección de ubicación". Se trata de un script personalizado que le permite activar y desactivar las sugerencias translúcidas (objetos con el material de rayos x) se ha mencionado anteriormente. 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) paso 4: Como tenemos 5 objetos, escriba "5" para el tamaño de la matriz de objeto de juego. Debería ver aparecer 5 nuevos elementos. 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

Arrastre cada uno de los objetos translúcidos en los cuadros que dicen "None (objeto de juego)." Arrastre los siguientes objetos del módulo lunar en su escena base: 

• Mochila

•   GasTank

• Topleftbody

• Nariz

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

Ahora está configurado el script "activar o desactivar las sugerencias de selección de ubicación". Esto nos permitirá activar y desactivar la las sugerencias.

Paso 5: Agregue el script "iniciar el módulo lunar". Haga clic en el botón "Agregar componente", busque "módulo lunar de lanzamiento" y selecciónelo. Esta secuencia de comandos será responsable de iniciar el módulo lunar. Cuando se presiona un botón configurado, se agregará una fuerza hacia arriba al componente de un cuerpo rígido del módulo lunar y hará que el módulo iniciar hacia arriba. Si está en el interior, el módulo lunar puede bloquearse en la malla de límite superior. Pero si está en el exterior, se vuele a espacio indefinidamente. 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

Paso 6: Ajustar el valor para que el módulo lunar se Volar seguridad correctamente. Pruebe con un valor de 0,01. Deje en blanco el campo "Rb". RB significa un cuerpo rígido, y este campo se rellenará automáticamente en tiempo de ejecución.

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>Información general sobre elementos de módulo lunar
El objeto de módulo Lunar partes primario es la colección de los objetos que interactúa con el usuario. Los nombres de objeto de juego (con escena con la etiqueta nombres en paretheses) se proporcionan en la lista siguiente:

- Mochila (depósito de combustible)
- GasTank (celda de energía)
- TopLeftBody (Rover revestimiento)
- Nariz (acoplamiento Portal)
- LeftTwirler (Sensor externo)

Tenga en cuenta que cada uno de estos objetos tiene el controlador de manipulación, como se describe en la lección 4. Con el controlador de manipulación, los usuarios pueden tomar y manipular el objeto. Tenga en cuenta también que la configuración de "tipo de manipulación pasar dos" se establece en "mover y girar". Esto solo permite al usuario mover el objeto y no cambiar su tamaño, que es la funcionalidad deseada para una aplicación de ensamblado.
Además, manipulación de lejos está desactivada para permitir solo la interacción directa de partes del módulo.

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

El script de demostración de ensamblado parte (mostrado arriba) es el script que administra los objetos que se va a colocar en el módulo lunar por el usuario. 

El campo "Contexto de objeto" es la transformación que está seleccionado (n el caso de la imagen anterior, el depósito de combustible/mochila) con el objeto que se pueda conectar a. 

La configuración "Cerca de la distancia" y "Ahora distancia" es responsable de determinar la proximidad a la que se ajustarán en su lugar partes o liberarse. Por ejemplo, necesitaría 0,1 unidades fuera del módulo lunar para colocarla en el depósito de combustible/mochila. La "ahora"distancia establece la ubicación donde el objeto debe ser desasocie el módulo lunar. En este caso, la mano del usuario debe tomar el depósito de combustible/mochila y tire de él 0,2 unidades fuera del módulo lunar para quitarlo de ajuste de vuelta en su lugar.

El "objeto de sugerencia de herramienta" es la etiqueta de sugerencia de la herramienta de la escena. Cuando los objetos están ajustados en su lugar, se deshabilitará la etiqueta. 

El origen de Audio se muestrear automáticamente. 

### <a name="placement-hints-buttons"></a>Selección de ubicación de las sugerencias de botones
En [lección 2](mrlearning-base-ch2.md), ha aprendido a realizar y configurar botones para realizar acciones como cambiar el color de un elemento o que se reproduzca un sonido cuando se inserta. Seguimos usar esos principios ya configuramos nuestro botones de alternar las sugerencias de ubicación. 

El objetivo es nuestro botón configurar para que cada vez que el usuario presiona el botón de la sugerencia de colocación, cambiará la visibilidad de las sugerencias de colocación translúcido. 

Paso 1: Mueva el módulo Lunar a la ranura vacía "" tiempo de ejecución solo en el panel del inspector mientras está seleccionado el objeto de sugerencias de selección de ubicación de la jerarquía escena base. 
 ![Lesson6 capítulo 3 Step1im](images/Lesson6_Chapter3_step1im.PNG) paso 2: Ahora haga clic en la lista desplegable, donde no dice, "ninguna función". Vaya a "TogglePlacementHints" y, en ese menú Seleccionar "ToggleGameObjects ()." ToggleGameObjects() alternará las sugerencias de colocación, activar y desactivar para que estén visible o invisible cada vez que se presiona el botón.
 ![Lesson6 capítulo 3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>Configurar el botón Restablecer

Habrá situaciones en las que el usuario realiza un error, o inicia accidentalmente que el objeto inmediatamente, o simplemente desea la experiencia de rest. El botón Restablecer agregará la capacidad de reiniciar la experiencia. 

Paso 1: Seleccione el botón Restablecer. En la escena base, se llama "ResetRoundButton." 

Paso 2: Arrastre el módulo de lunar desde la jerarquía escena base en la ranura vacía en el "botón presionado" del panel del inspector.
 ![Lesson6 Capítulo4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

Paso 3: Seleccione el menú desplegable que no dice, "ninguna función" y mantenga el mouse sobre "LaunchLunarModule." Ahora, seleccione "resetModule ()."

![Lesson6 Capítulo4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> Nota: Observará que, de forma predeterminada, el "GameObject.BroadcastMessage" está configurado para "ResetPlacement". Esto difunde un mensaje denominado "ResetPlacement" para cada objeto secundario de RocketLauncher_Tutorial. Cualquier objeto que tiene un método para "ResetPlacement()" responderá a ese mensaje mediante el restablecimiento de su posición. 

### <a name="launching-the-lunar-module"></a>Iniciar el módulo Lunar
Este capítulo se va a configurar el botón de inicio. Esto permitirá al usuario que presione el botón e iniciar el módulo Lunar en espacio.

Paso 1: Seleccione el botón de inicio (en la escena base se denomina "LaunchRoundButton"). Arrastre el módulo de Lunar a la ranura vacía en "End tocar" en el panel del inspector.
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) paso 2: Seleccione el menú desplegable que no dice, "ninguna función". Mantenga el mouse sobre "LaunchLunarModule" y seleccione "StopThruster ()." Esto controlará cuánto empuje el usuario desea dar al módulo Lunar. 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) paso 3: En "ButtonPressed()", agregue el módulo Lunar (hacer clic, suspensión y arrastrar) a la ranura vacía. 

Paso 4: Haga clic en el menú desplegable que no dice, "ninguna función" y mantenga el mouse sobre "LaunchLunarModule" y seleccione "StartThruster ()." 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) paso 5: Agregar música al módulo Lunar para que cuando el cohete despega, se reproducirá la música. Para ello, arrastre el módulo de Lunar a la siguiente ranura vacía en el "Botón Pressed()".

Paso 6: Seleccione el menú desplegable que no dice, "ninguna función" y mantenga el mouse sobre "AudioSource" y seleccione "PlayOneShot (AudioClip)". No dude en explorar la variedad de sonidos que se incluye con el MRTK. En este ejemplo, vamos a ceñirnos a "MRTK_Gem."
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>Enhorabuena 
¡Esta aplicación se ha configurado totalmente! Ahora cuando presiona play, puede totalmente ensamblar el módulo Lunar, activar o desactivar las sugerencias, inicie el módulo Lunar y restablecerla para hacerlo nuevamente.
