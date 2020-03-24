---
title: 'Tutoriales de introducción: 4. Colocación del contenido dinámico y uso de solucionadores'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2825f99f49eca6fd7277d02828bfe1bc3c23291a
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031220"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. Colocación del contenido dinámico y uso de solucionadores
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Los hologramas cobran vida en HoloLens 2 cuando, intuitivamente, siguen al usuario y se colocan en el entorno físico, de forma que la interacción resulta fluida y elegante. En este tutorial, exploramos distintas formas de colocar hologramas de forma dinámica mediante las herramientas de selección de ubicación disponibles de MRTK, conocidas como "solucionadores", para resolver escenarios de selección de ubicación espacial complejos. En MRTK, los solucionadores son un sistema de scripts y comportamientos que se usan para permitir que los elementos de la interfaz de usuario te sigan, sigan al usuario o sigan a otros objetos de juego en la escena. También pueden usarse para acoplarse rápidamente en ciertas posiciones, haciendo que la aplicación sea más intuitiva.

## <a name="objectives"></a>Objetivos

* Introducir los solucionadores de MRTK
* Usa solucionadores para tener una colección de botones que sigan al usuario
* Usa solucionadores para tener un objeto de juego que siga las manos con seguimiento del usuario

## <a name="location-of-solvers-in-the-mrtk"></a>Ubicación de los solucionadores en MRTK

 Los solucionadores de MRTK se encuentran en la carpeta del SDK de MRTK. Para ver los solucionadores disponibles en el proyecto, en la ventana Project (Proyecto), navega a **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers** (Recursos > MixedRealityToolkit.SDK > Características > Utilidades > Solucionadores):

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

En este tutorial, revisaremos la implementación de los solucionadores Orbital y Radial View (Vista radial). Para obtener más información acerca de la gama completa de solucionadores disponibles en MRTK, puedes visitar la guía [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Uso de un solucionador para seguir al usuario
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

En esta sección, mejorarás la colección de botones que creaste en el tutorial anterior para que siga la dirección de la mirada del usuario. Además, también configurarás el solucionador para que la colección de botones siempre:

* se gire en paralelo a la dirección de lectura del usuario, para proporcionar una lectura natural de izquierda a derecha;
* se coloque ligeramente por debajo de la dirección de mirada horizontal del usuario para no obstaculizar otros objetos que se agregarán más adelante en este tutorial.
* se coloque, aproximadamente, a la distancia de la longitud de un brazo del usuario para que los botones se puedan presionar fácilmente.

Para ello, usarás el **solucionador Orbital**, que bloquea el objeto en una posición y desplazamiento especificados respecto al objeto al que se hace referencia.

### <a name="1-add-the-orbital-solver"></a>1. Agregar el solucionador Orbital

En la ventaja Hierarchy (Jerarquía), selecciona el objeto **ButtonCollection** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Orbital (Script)** (Orbital [script]) al objeto ButtonCollection:

> [!NOTE]
> Al agregar un solucionador, en este caso, el componente Orbital (Script), se agrega automáticamente el componente Solver Handler (Script) porque lo requiere el solucionador.

### <a name="2-configure-the-orbital-solver"></a>2. Configurar el solucionador Orbital

Configura el componente **Solver Handler (Script)** (Controlador de solucionador [script]):

* Comprueba que **Tracked Target Type** (Tipo de destino de seguimiento) esté definido como **Head** (Cabeza).

Configura el componente **Orbital (Script)** :

* Comprueba que **Orientation Type** (Tipo de orientación) se haya definido como **Follow Tracked Object** (Hacer seguimiento del objeto que se sigue).
* Restaura **Local Offset** (Desplazamiento local) a X = 0, Y = 0, Z = 0.
* Cambia **World Offset** (Desplazamiento del mundo) a X = 0, Y = -0,4, Z = 0,3.

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. Probar el solucionador orbital mediante la simulación en el editor

Presiona el botón Play (Jugar) para entrar en el modo de juego y mantén presionado el botón derecho del mouse para girar la dirección de la mirada y observa lo siguiente:

* La posición de transformación de ButtonCollection está controlada por la configuración del solucionador.
* El cubo, que no se ve afectado por el solucionador, sigue en la misma posición.

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Si no ves el rayo de la cámara en la ventana de la escena, asegúrate de que el menú Gizmos esté habilitado. Para obtener más información sobre el menú Gizmos y cómo puedes usarlo para optimizar la vista de escenas, visita la documentación sobre el <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menú de Gizmos </a> de Unity.
>
> Para mostrar las ventanas Scene (Escena) y Game (Juego) una al lado de otra como se muestra en la imagen anterior, arrastra la ventana Game (Juego) al lado derecho de la ventana Scene (Escena). Para obtener más información sobre cómo personalizar el área de trabajo, puedes visitar la documentación sobre la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalización del área de trabajo</a> de Unity.

## <a name="enabling-objects-to-follow-tracked-hands"></a>Habilitación de los objetos para que sigan a las manos con seguimiento

En esta sección, configurarás el objeto de cubo que creaste en el tutorial anterior para que siga las manos con seguimiento del usuario, en concreto, la muñeca de la mano derecha. Además, también configurarás el solucionador para que el cubo:

* cambie su orientación con la rotación de la mano del usuario;
* esté situado sobre la muñeca del usuario.

Para ello, usarás el **solucionador de vista radial**, que mantiene el objeto dentro de un cono de vista convertido por el objeto al que se hace referencia.

### <a name="1-add-the-radial-view-solver"></a>1. Agregar el solucionador de vista radial

En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cube** (Cubo) y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Radial View (Script)** (Vista radial [script]) al objeto Cube (Cubo).

### <a name="2-configure-the-radial-view-solver"></a>2. Configurar el solucionador de vista radial

Configura el componente **Solver Handler (Script)** (Controlador de solucionador [script]):

* Cambia **Tracked Target Type** (Tipo de destino de seguimiento) a **Hand Joint** (Articulación de la mano).
* Cambia **Tracked Handness** (Mano de seguimiento) a **Right** (Derecha)
* Cambia **Tracked Hand Joint** (Articulación de mano de seguimiento) a **Wrist** (Muñeca)

Configura el componente **Radial View (Script)** (Vista radial [script]):

* Cambia **Reference Direction** (Dirección de referencia) a **Object Oriented** (Orientada a objetos) y activa la casilla **Orient To Reference Direction** (Orientar a dirección de referencia)
* Cambia **Min Distance** (Distancia mínima) y **Max Distance** (Distancia máxima) a 0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. Probar el solucionador de vista radial mediante la simulación en el editor

Presiona el botón Play (Jugar) para entrar en el modo de juego y, a continuación, mantén presionada la barra espaciadora para mostrar la mano. Mueve el cursor del mouse para mover la mano y haz clic y mantén presionado el botón del ratón para girar la mano:

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido a usar los solucionadores de MRTK para tener una interfaz de usuario intuitiva que siga al usuario. También has aprendido cómo adjuntar un solucionador a un objeto (es decir, el cubo) para seguir a las manos con seguimiento del usuario. Para más información sobre estos y otros solucionadores incluidos con MRTK, visita la guía de [solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Tutorial siguiente: 5. Interacción con objetos 3D](mrlearning-base-ch4.md)
