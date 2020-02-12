---
title: 'Tutoriales de introducción: 4. Colocar contenido dinámico y usar solucionadores'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129351"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. colocar contenido dinámico y usar solucionadores
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Los hologramas llegan a la vida en HoloLens 2 cuando siguen de forma intuitiva al usuario y se colocan en el entorno físico de una manera que hace que la interacción sea fluida y elegante. En este tutorial, se exploran las formas de colocar dinámicamente los hologramas con las herramientas de selección de ubicación disponibles de MRTK, conocidas como solucionadores, para solucionar escenarios complejos de colocación espacial. En MRTK, los solucionadores son un sistema de scripts y comportamientos que se usan para permitir que los elementos de la interfaz de usuario sigan el usuario, el usuario u otros objetos de juego de la escena. También pueden usarse para acoplarse rápidamente en ciertas posiciones, haciendo que la aplicación sea más intuitiva.

## <a name="objectives"></a>Objetivos

* Introducción a los solucionadores de MRTK
* Usar solucionadores para que una colección de botones siga al usuario
* Usar solucionadores para que un objeto de juego siga las manos controladas por el usuario

## <a name="location-of-solvers-in-the-mrtk"></a>Ubicación de los solucionadores en el MRTK

 Los solucionadores de MRTK se encuentran en la carpeta MRTK SDK. Para ver las resoluciones disponibles en el proyecto, en la ventana proyecto, vaya a **activos** > **MixedRealityToolkit. SDK** > **features** > **Utilities** > **resolvetions**:

![mrlearning: base](images/mrlearning-base/tutorial3-section1-step1-1.png)

En este tutorial, revisaremos la implementación del Solver orbital y el Solver de la vista radial. Para obtener más información acerca de la gama completa de solucionadores disponibles en MRTK, puede visitar la guía de [soluciones](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="use-a-solver-to-follow-the-user"></a>Usar un Solver para seguir al usuario
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

En esta sección, mejorará la colección de botones que creó en el tutorial anterior para que siga la dirección del usuario. Además, también configurará el Solver para que la colección de botones sea siempre:

* Girado en paralelo a la dirección de lectura del usuario, para la lectura natural de izquierda a derecha
* Se coloca ligeramente por debajo de la dirección de miración horizontal del usuario, por lo que no obstaculiza los otros objetos que se agregarán más adelante en este tutorial.
* Se coloca aproximadamente a la longitud de un brazo del usuario, por lo que los botones se pueden presionar fácilmente

Para ello, usará el **Solver orbital** , que bloquea el objeto en una posición y desplazamiento especificados desde el objeto al que se hace referencia.

### <a name="1-add-the-orbital-solver"></a>1. agregar el Solver orbital

En la ventana jerarquía, seleccione el objeto **ButtonCollection** y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente **orbital (Script)** al objeto ButtonCollection.

> [!NOTE]
> Al agregar un Solver, en este caso, el componente orbital (Script), se agrega automáticamente el componente de controlador de Solver (Script) porque lo requiere el solucionador.

### <a name="2-configure-the-orbital-solver"></a>2. configurar el Solver orbital

Configurar el componente de **controlador de Solver (Script)** :

* Compruebe que el tipo de destino del que se ha **realizado el seguimiento** está establecido en **principal**

Configure el componente **orbital (Script)** :

* Cambiar el **tipo de orientación** a seguimiento del **objeto controlado**
* Restablecer **desplazamiento local** a X = 0, y = 0, Z = 0
* Cambiar el **desplazamiento de mundo** a X = 0, y =-0,4, Z = 0,3

![mrlearning: base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. probar el Solver orbital mediante la simulación en el editor

Presione el botón reproducir para entrar en el modo de juego y mantenga presionado el botón secundario del mouse para girar la dirección de miración y observe lo siguiente:

* La posición de transformación de ButtonCollection ahora está controlada por la configuración de Solver
* El cubo, que no se ve afectado por el Solver, permanece en la misma posición

![mrlearning: base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> Si no ve el rayo de la cámara en la ventana de la escena, asegúrese de que el menú de Gizmos está habilitado. Para más información sobre el menú Gizmos y cómo puede usarlo para optimizar la vista de escenas, puede visitar la documentación del <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menú Gizmos</a> de Unity.
>
> Para mostrar la escena y la ventana de juego en paralelo, tal y como se muestra en la imagen anterior, basta con arrastrar la ventana de juego hasta el lado derecho de la ventana de la escena. Para obtener más información sobre cómo personalizar el área de trabajo, puede visitar la documentación personalización de Unity en <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">el área de trabajo</a> .

## <a name="enabling-objects-to-follow-tracked-hands"></a>Habilitar objetos para seguir manos de seguimiento

En esta sección, configurará el objeto de cubo que ha creado en el tutorial anterior para que siga las manos controladas por el usuario, en concreto la muñeca de la mano derecha. Además, también configurará el Solver para que el cubo:

* Cambia su orientación con la rotación del usuario.
* Colocado en la muñeca del usuario

Para ello, usará la **vista radial Solver** , que mantiene el objeto dentro de un cono de vista convertido por el objeto al que se hace referencia.

### <a name="1-add-the-radial-view-solver"></a>1. agregar la vista radial Solver

En la ventana jerarquía, seleccione el objeto de **cubo** y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el objeto de cubo componente de **vista radial (Script)** .

### <a name="2-configure-the-radial-view-solver"></a>2. configurar el Solver de la vista radial

Configurar el componente de **controlador de Solver (Script)** :

* Cambiar el tipo de destino del que se **realiza el seguimiento** a la **Unión manual**
* Cambiar la **mano sometida a seguimiento** a la **derecha**
* Cambio de **conjunto de mano** controlado a **muñeca**

Configure el componente de **vista radial (Script)** :

* Cambiar la **dirección de referencia** a **orientada a objetos**y activar la casilla **orientar a la dirección de referencia**
* Cambiar la **distancia mínima** y la **distancia máxima** a 0

![mrlearning: base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. probar la vista radial Solver mediante la simulación en el editor

Presione el botón reproducir para entrar en el modo de juego y, a continuación, mantenga presionada la barra espaciadora para abrirla. Mueva el cursor del mouse para mover la mano y haga clic y mantenga presionado el botón primario del mouse para girar la mano:

![mrlearning: base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a usar los solucionadores de MRTK para que una interfaz de usuario pueda seguir de forma intuitiva al usuario. También ha aprendido cómo adjuntar un Solver a un objeto (es decir, un cubo) para seguir las manos controladas por el usuario. Para obtener más información sobre estos y otros solucionadores que se incluyen en MRTK, puede visitar la guía de [soluciones](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

[Siguiente tutorial: 5. interactuar con objetos 3D](mrlearning-base-ch4.md)
