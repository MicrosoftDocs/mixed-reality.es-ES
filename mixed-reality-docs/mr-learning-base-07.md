---
title: 'Tutoriales de introducción: 7. Interacción con objetos 3D'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8920b35d1583777b86bc82868bb90338e25298e2
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305994"
---
# <a name="7-interacting-with-3d-objects"></a>7. Interacción con objetos 3D

En este tutorial, aprenderá a habilitar la manipulación cercana y lejana de objetos 3D y a limitar los tipos de manipulación permitidos. También aprenderá a agregar cuadros de límite alrededor de objetos 3D para facilitar el control de la manipulación de objetos.

## <a name="objectives"></a>Objetivos

* Aprender a configurar objetos 3D para poder interactuar con ellos
* Aprender a agregar cuadros de límite a objetos 3D

## <a name="manipulating-3d-objects"></a>Manipulación de objetos 3D

En esta sección, agregará la capacidad de manipular todas las partes del róver que organizó en la tabla durante el tutorial [Posicionamiento de los objetos en la escena](mr-learning-base-04.md).

Los principales pasos que debes seguir para lograrlo son:

1. Agregar el componente Object Manipulator (Script) (Manipulador de objetos [script]) a todos los objetos de las partes
2. Agregar el componente NearInteractionGrabbable a todos los objetos de las partes
3. Configurar el componente Object Manipulator (Script) (Manipulador de objetos [script])

> [!NOTE]
> Para poder **manipular un objeto**, el objeto debe tener los siguientes componentes:
>
> * Componente **Collider**; por ejemplo, un colisionador de cuadro
> * Componente **Object Manipulator (Script)** (Manipulador de objetos [script])
>
> Para poder **manipular** y **agarrar un objeto con seguimiento de manos**, el objeto debe tener los componentes siguientes:
>
> * Componente **Collider**; por ejemplo, un colisionador de cuadro
> * Componente **Object Manipulator (Script)** (Manipulador de objetos [script])
> * Componente **NearInteractionGrabbable**

Además, configurará el explorador del róver a fin de poder colocarle las partes y crear un ensamblado completo.

En la ventana Hierarchy (Jerarquía), expanda el objeto RoverExplorer > **RoverParts** y seleccione todos los objetos secundarios de la parte, así como el objeto **RoverAssembly**, y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar los siguientes componentes a todos los objetos seleccionados:

* Componente **Object Manipulator (Script)** (Manipulador de objetos [script])
* Componente **NearInteractionGrabbable**
* Componente **Part Assembly Controller (Script)** (Controlador de ensamblado de partes [script])

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> Para seleccionar varios objetos que no estén juntos entre sí, mantenga presionada la tecla Control mientras usa el mouse para seleccionar cualquier objeto.

> [!NOTE]
> Para los fines de este tutorial, los colisionadores ya se han agregado a las partes del róver. Para obtener más información sobre los colisionadores, visita la documentación sobre <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">colisionadores</a> de Unity.

> [!NOTE]
> El controlador Part Assembly Controller (Script) (Controlador de ensamblado de partes [script]) no forma parte de MRTK, pero se incluyó con los recursos del tutorial.

Con todos los objetos de las partes de róver y el objeto RoverAssembly todavía seleccionados, en la ventana Inspector, configure el componente **Object Manipulator (Script)** (Manipulador de objetos [script]) como se indica a continuación:

* En la lista desplegable **Two Handed Manipulation Type** (Tipo de manipulación con dos manos), desactive la escala, de modo que solo queden habilitadas las opciones **Mover** y **Girar**.

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> En este punto, ha habilitado la manipulación de objetos para todos los objetos de las piezas de Rover y el objeto RoverAssembly.

En la ventana Proyecto, navegue hasta la carpeta **Recursos** > **MRTK** > **SDK** > **StandardAssets** > **Audio** para buscar los clips de audio:

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

En la ventana Hierarchy (Jerarquía), seleccione todos los **objetos de las partes del róver** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **Audio sources** (Orígenes de audio) y configurarlo del modo siguiente:

* Asigne el clip de audio **MRTK_Scale_Start** al campo **AudioClip**.
* Desactive la casilla **Play On Awake** (Reproducir al reactivar).
* Cambie **Spatial Blend** a 1.

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

En la ventana Hierarchy (Jerarquía), expanda el objeto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** para mostrar todos los objetos de sugerencia de selección de ubicación y, a continuación, seleccione la primera parte de róver, RoverParts > **Camera_Part** y configure el componente **Part Assembly Controller (Script)** (Controlador de ensamblado de partes [script]) de la siguiente manera:

* Asigne el objeto **Camera_PlacementHint** al campo **Location To Place** (Ubicación de colocación).

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

**Repita** este paso para cada uno de los objetos de las partes de róver restantes y el objeto RoverAssembly con tal de configurar el componente **Part Assembly Controller (Script)** (Controlador de ensamblado de partes [script]) de la manera siguiente:

* Para la parte **Generator_Part**, asigne el objeto **Generator_PlacementHint** al campo **Location To Place** (Ubicación de colocación).
* Para la parte **Lights_Partt**, asigne el objeto **Lights_PlacementHint** al campo **Location To Place** (Ubicación de colocación).
* Para la parte **UHFAntenna_Part**, asigne el objeto **UHFAntenna_PlacementHint** al campo **Location To Place** (Ubicación de colocación).
* Para la parte **Spectrometer_Part**, asigne el objeto **Spectrometer_PlacementHint** al campo **Location To Place** (Ubicación de colocación).
* Para el elemento **RoverAssembly**, asigne el propio objeto, es decir, el mismo objeto **RoverAssembly**, en el campo **Location To Place** (Ubicación de colocación).

En la ventana Hierarchy (Jerarquía), seleccione el objeto del botón RoverExplorer > Buttons > **Reset** (RoverExplorer > Botones > Restablecer) y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de interacción de la siguiente manera:

* Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **PartAssemblyController** > **ResetPlacement ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

Si ahora entra en el Modo Juego, podrá usar la interacción cercana o lejana para colocar las partes en el róver. Una vez que la parte esté cerca de la sugerencia de ubicación correspondiente, se ajustará en su lugar y pasará a ser una parte del róver. Para restablecer las ubicaciones, puede presionar el botón Restablecer:

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

Para obtener más información sobre el componente Object Manipulator (Manipulador de objetos) y sus propiedades asociadas, consulte la guía [Manipulador de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Adición de cuadros de límite

Los cuadros de límite hacen que manipular objetos con una mano sea más sencillo e intuitivo tanto para la interacción próxima como remota, ya que proporcionan controladores que se pueden usar para el escalado y la rotación.

En este ejemplo, agregará un cuadro de límite al objeto RoverExplorer para que toda la experiencia se pueda desplazar, girar y escalar fácilmente. Además, configurará el menú para poder activar y desactivar el cuadro de límite.

En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverExplorer** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar los componentes siguientes:

* Componente **BoundingBox**
* Componente **Object Manipulator (Script)** (Manipulador de objetos [script])

A continuación, **desactive** la casilla situada junto a ambos componentes para que **estén deshabilitados** de forma predeterminada:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> La visualización del cuadro de límite se crea en tiempo de ejecución y, por tanto, no es visible antes de entrar en el Modo Juego.

> [!NOTE]
> El componente BoundingBox agregará automáticamente el componente NearInteractionGrabbable en tiempo de ejecución. Por lo tanto, no es necesario agregar este componente para agarrar los objetos delimitados con las manos con seguimiento.

En la ventana Hierarchy (Jerarquía), expanda el objeto Menu (Menú) > **ButtonCollection** para mostrar los cuatro botones. Cambie el nombre del tercer botón a **BoundingBox_Enable** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) como se indica a continuación:

* Cambie el valor **Main Label Text** (Texto de la etiqueta principal) a **Habilitar**.
* Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **BoundingBox** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Verifique que la casilla del argumento esté **activada**.
* Haga clic en el icono **+** pequeño para agregar otro evento.
* Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Verifique que la casilla del argumento esté **activada**.
* Deje el **icono** como el icono "cubo con cuadro de límite".

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

Cambie el nombre del cuarto y el último botón por **BoundingBox_Disable** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:

* Cambie el valor **Main Label Text** (Texto de la etiqueta principal) a **Deshabilitar**.
* Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **BoundingBox** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Verifique que la casilla del argumento esté **desactivada**.
* Haga clic en el icono **+** pequeño para agregar otro evento.
* Asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool Enabled** (Booleano habilitado) para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Verifique que la casilla del argumento esté **desactivada**.
* Deje el **icono** como el icono "cubo con cuadro de límite".

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

Si ahora entra en el Modo Juego y habilita el cuadro de límite haciendo clic en el botón Habilitar, podrá usar la interacción cercana o lejana para desplazar, girar y escalar el cuadro de límite, así como usar el botón Deshabilitar para deshabilitar de nuevo el cuadro de límite:

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

Para obtener más información sobre el componente de cuadro de límite y sus propiedades asociadas, puedes visitar la guía sobre el [cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a habilitar la manipulación cercana y lejana de objetos 3D y a limitar los tipos de manipulación permitidos. También aprendió a agregar cuadros de límite alrededor de objetos 3D para facilitar el control de la manipulación de objetos.

[Tutorial siguiente: 8. Uso del seguimiento ocular](mr-learning-base-08.md)
