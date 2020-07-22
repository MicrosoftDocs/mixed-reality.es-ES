---
title: 'Tutoriales de introducción: 5. Creación de contenido dinámico mediante solucionadores'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbeaa8b65b7aecc0600294b3739fedfb903e568e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306654"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5. Creación de contenido dinámico mediante solucionadores

## <a name="overview"></a>Introducción

En este tutorial, explorará distintas formas de colocar hologramas de forma dinámica mediante las herramientas de selección de ubicación disponibles de MRTK, conocidas como "solucionadores", para resolver escenarios de selección de ubicación espacial complejos. En MRTK, los solucionadores son un sistema de scripts y comportamientos que se usaron para permitir que los objetos sigan al usuario o a otros objetos de juego en la escena. También pueden usarse para acoplarse en ciertas posiciones, de modo que la aplicación sea más intuitiva.

## <a name="objectives"></a>Objetivos

* Introducir los solucionadores de MRTK
* Aprender a usar los solucionadores para dirigir al usuario a objetos
* Aprender a usar los solucionadores para cambiar la posición de los objetos

## <a name="location-of-solvers-in-the-mrtk"></a>Ubicación de los solucionadores en MRTK

 Los solucionadores de MRTK se encuentran en la carpeta del SDK de MRTK. Para ver los solucionadores disponibles en el proyecto, en la ventana Project (Proyecto), navegue a **Assets** (Recursos)  > **MRTK** > **SDK** > **Features** (Características)  > **Utilities** (Utilidades)  > **Solvers** (Solucionadores):

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

En este tutorial, revisaremos la implementación de los solucionadores Directional Indicator (Indicador direccional) y Tap To Place (Pulsar para colocar). Para obtener más información acerca de la gama completa de solucionadores disponibles en MRTK, puede consultar la guía [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

> [!NOTE]
> El solucionador de indicador direccional no se encuentra en las carpetas de solucionadores a las que se hace referencia anteriormente, sino en las carpetas Assets > MRTK > SDK > Experimental > Features > Utilities (Recursos > MRTK > SDK > Experimental > Características > Utilidades), ya que es una característica experimental.

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>Uso del solucionador Directional Indicator (Indicador direccional) para dirigir al usuario a objetos

En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK.Tutorials.GettingStarted** > carpeta **Prefabs** (Recursos prefabricados), haga clic y arrastre el elemento prefabricado **Chevron** (Botón de contenido adicional) a la ventana Jerarquía y establezca su **Posición** de transformación en X = 0, Y = 0, Z = 2 para colocarlo cerca del objeto RoverExplorer:

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> Si observa que la cámara u otros iconos de la escena ocultan otros objetos o son distracciones, puede ocultarlos al <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">desactivar el menú Gizmos</a>, tal como se muestra en la imagen anterior. Para obtener más información sobre el menú Gizmos y cómo puede usarlo para optimizar la vista de escenas, consulte la documentación sobre el <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menú de Gizmos </a> de Unity.

Cambie el nombre del objeto de botón de contenido adicional **Indicator** recién agregado y, a continuación, en la ventana Inspector, use el botón **Agregar componente** para agregar el componente **DirectionalIndicator** y **Directional Indicator Controller (Script)** (Controlador de indicador direccional [script]):

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> Al agregar un solucionador (en este caso, el componente DirectionalIndicator), se agrega automáticamente el componente SolverHandler porque los solucionadores lo requieren.

> [!NOTE]
> El componente Directional Indicator Controller (Script) (Controlador de indicador direccional [script]) no forma parte de MRTK, pero se incluyó con los recursos del tutorial.

Configure los componentes DirectionalIndicator y SolverHandler como se indica a continuación:

* Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Cabeza**.
* Asigne **RoverExplorer** al campo **Directional Target** (Objetivo direccional) del componente **DirectionalIndicator**; para ello, arrástrelo desde la ventana Jerarquía hasta el campo **None (Transform)** (Ninguno [transformación]).
* Cambie el valor de **View Offset** (Desplazamiento de vista) a 0,2.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

Presione el botón Play (Jugar) para entrar en el modo de juego y mantenga presionado el botón derecho del mouse mientras mueve el mouse hacia la izquierda o derecha para girar la dirección de la mirada y observe lo siguiente:

* Cuando aparte la mirada del objeto RoverExplorer, el objeto Indicator aparecerá y apuntará hacia el objeto RoverExplorer.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> Si no ve el rayo de la cámara en la ventana de la escena, asegúrese de que el menú Gizmos esté habilitado como se muestra en la imagen anterior.

> [!TIP]
> Para obtener información sobre cómo usar la simulación de entrada del editor, puedes consultar la guía [Uso de la simulación de entrada de mano en el editor para probar una escena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

> [!TIP]
> Si el equipo tiene un micrófono, puede alternar fácilmente el estado activo del panel Diagnóstico que aparece en la ventana del juego mediante el comando de voz "toggle diagnostics" (alternar diagnóstico). También puede deshabilitarlo en MRTK Configuration Profile > Diagnostics > Enable Diagnostics System (Perfil de configuración de MRTK > Diagnóstico > Habilitar sistema de diagnóstico). Sin embargo, por lo general, se recomienda mantener el sistema de diagnóstico activo durante el desarrollo.

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>Uso del solucionador Tap to Place (Pulsar para colocar) para cambiar la posición de los objetos

En la ventana Jerarquía, seleccione RoverExplorer > objeto **RoverAssembly** y, a continuación, en la ventana Inspector, use el botón **Agregar componente** para agregar el componente **Tap To Place (Script)** (Pulsar para colocar [script]) y configúrelo del modo siguiente:

* Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Cabeza**.
* Active la casilla **Keep Orientation Vertical** (Mantener la orientación vertical).
* En la lista desplegable **Magnetic Surfaces** (Superficies magnéticas)  > **Elemento 0**, desactive todas las opciones excepto **Spatial Awareness** (Reconocimiento espacial).

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> La configuración de superficies magnéticas determina qué objetos puede detectar el componente Tap to Place (Pulsar para colocar) al colocar un objeto. Al cambiar la configuración a solo Reconocimiento espacial, el componente Tap To Place (Script) (Pulsar para colocar [script]) solo podrá colocar el Rover en objetos de la capa de Unity denominada Spatial Awareness, que de forma predeterminada es la malla de reconocimiento espacial generada por HoloLens.
>
>Para obtener más información sobre las capas, puede consultas la documentación sobre <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">capas</a> de Unity.

> [!TIP]
> Si quiere ver la malla de reconocimiento espacial al probar la función Tap To Place (Pulsar para colocar) en HoloLens, puede establecer temporalmente la opción de visualización del observador de malla espacial en Visible. Para recibir un recordatorio sobre cómo cambiar la opción de visualización, puede consultar las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).

Con el objeto RoverAssembly aún seleccionado en la ventana Jerarquía, desde la ventana Inspector, busque el evento **On Placing Started ()** y haga clic en el icono **+** para agregar un nuevo evento:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

Configure el evento de la siguiente manera:

* Asigne el objeto **RoverAssembly** como cliente de escucha para el evento On Placing Started () arrastrándolo desde la ventana Jerarquía hasta el campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **Ninguna función**, seleccione **TapToPlace** > **float SurfaceNormalOffset** (SurfaceNormalOffset tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Compruebe que el argumento esté establecido en **0**

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

En la ventana Jerarquía, haga clic con el botón secundario en una zona vacía y seleccione **Objeto 3D** > **Cubo**, para crear un objeto temporal que represente el suelo y configure el componente **Transform** (Transformación) como se indica a continuación:

* **Posición**: X = 0, Y = -1,65, Z = 6
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 10, Y = 0,2, Z = 10

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

Con el cubo temporal seleccionado todavía en la ventana Jerarquía, desde la ventana Inspector, use la lista desplegable **Capas** para cambiar la configuración de la capa del cubo únicamente para incluir la capa **Spatial Awareness** (Reconocimiento espacial):

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionado el botón derecho del mouse mientras mueve el mouse hacia abajo hasta que la mirada entre en contacto con el objeto RoverAssembly:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

Haga clic en el botón izquierdo del mouse para iniciar el proceso para pulsar y colocar:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

Mantenga presionado el botón derecho del mouse mientras mueve el mouse hacia la izquierda o derecha para girar la dirección de la mirada; cuando esté satisfecho con su ubicación, haga clic con el botón izquierdo del mouse:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

Una vez que haya terminado de probar la característica en el modo de juego, haga clic con el botón derecho en el objeto de cubo y seleccione **Eliminar** para quitarlo de la escena:

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a usar el solucionador Directional Indicator (Indicador direccional) de MRTK para que un elemento de la interfaz de usuario dirige de forma intuitiva al usuario a los objetos. También aprendió a usar el solucionador Tap To Place (Pulsar para colocar) para cambiar la posición de los objetos fácilmente.

Para más información sobre estos y otros solucionadores incluidos con MRTK, consulte la guía de [solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Tutorial siguiente: 6. Creación de interfaces de usuario](mr-learning-base-06.md)
