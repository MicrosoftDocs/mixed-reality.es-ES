---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, IU, experiencia de usuario
ms.openlocfilehash: 4befaa6f55bff6a820c976db969fdad7b64a2214
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143246"
---
# <a name="progress-indicator"></a>Indicador de progreso

<br>

<img src="images/UX/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga. Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.

<br>

---

## <a name="types-of-progress"></a>Tipos de progreso

Es importante proporcionar información de usuario sobre lo que está ocurriendo. En realidad, los usuarios pueden distraerse fácilmente por el entorno físico u objetos si la aplicación no proporciona buenos comentarios visuales. En situaciones en las que se tardan unos segundos, como cuando se cargan datos o se actualiza una escena, es conveniente mostrar un indicador visual. Hay dos opciones para mostrar el usuario que está realizando una operación: una **barra de progreso** o un **anillo de progreso**.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra de progreso<br>
        Una barra de progreso muestra el porcentaje completado de una tarea. Se debe usar durante una operación cuya duración se conoce (determinan), pero su progreso no debe bloquear la interacción del usuario con la aplicación.<br>
        <br>
        *Imagen: ejemplo de barra de progreso en HoloLens*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Círculo de progreso<br>
        Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea cualquier interacción del usuario adicional hasta que se haya completado la operación.<br>
        <br>
        *Imagen: ejemplo de anillo de progreso en HoloLens*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![ejemplo de anillo de progreso en HoloLens](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Progreso con un objeto personalizado<br>
        Puede Agregar a la identidad de personalidad y marca de la aplicación personalizando el control de progreso con sus propios objetos 2D/3D personalizados.<br>
        <br>
        *Imagen: progreso con el ejemplo de malla personalizada en HoloLens*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![progreso con el ejemplo de malla personalizada en HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Procedimiento recomendado
* Encadenar estrechamente la [cartelera o etiqueta, junto](billboarding-and-tag-along.md) con la presentación de progreso, ya que el usuario puede trasladar fácilmente el encabezado a un espacio vacío y perder el contexto. La aplicación podría parecerse a que se ha bloqueado si el usuario no puede ver nada. La cartelera y el etiquetado están integrados en el recurso prefabricado de progreso.
* Siempre es conveniente proporcionar información de estado sobre lo que está ocurriendo al usuario. El recurso prefabricado de progreso proporciona varios estilos visuales, incluido el progreso de tipo anillo estándar de Windows para proporcionar el estado. También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.

<br>

---

## <a name="progress-indicator-in-mrtkmixed-reality-toolkit-for-unity"></a>Indicador de progreso en MRTK (kit de herramientas de realidad mixta) para Unity

* [MRTK: indicador de progreso Prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK: servicio de transición de escenas](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a>Consulta también

* [Cursores](cursors.md)
* [Rayo de mano](point-and-commit.md)
* [Button](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipula](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Near](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Herramienta](tooltip.md)
* [Tabletas](slate.md)
* [Control deslizante](slider.md)
* [Sombreador](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
