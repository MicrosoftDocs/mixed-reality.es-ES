---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, IU, experiencia de usuario
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523254"
---
# <a name="displaying-progress"></a>Mostrar progreso

Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga. Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.

![Ejemplo de anillo de progreso en HoloLens](images/HoloLens2_Loader.gif)<br>
*Ejemplo de anillo de progreso en HoloLens*

## <a name="types-of-progress"></a>Tipos de progreso

Es importante proporcionar información de usuario sobre lo que está ocurriendo. En realidad, los usuarios pueden distraerse fácilmente por el entorno físico u objetos si la aplicación no proporciona buenos comentarios visuales. En situaciones en las que se tardan unos segundos, como cuando se cargan datos o se actualiza una escena, es conveniente mostrar un indicador visual. Hay dos opciones para mostrar el usuario que está realizando una operación: una **barra de progreso** o un **anillo de progreso**.

### <a name="progress-bar"></a>Barra de progreso

![Ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)

Una barra de progreso muestra el porcentaje completado de una tarea. Se debe usar durante una operación cuya duración se conoce (determinan), pero su progreso no debe bloquear la interacción del usuario con la aplicación.

### <a name="progress-ring"></a>Círculo de progreso

![Ejemplo de anillo de progreso en HoloLens](images/640px-progressring.jpg)

Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea cualquier interacción del usuario adicional hasta que se haya completado la operación.

### <a name="progress-with-a-custom-object"></a>Progreso con un objeto personalizado

![Progreso con el ejemplo de malla personalizada en HoloLens](images/640px-progresscustom.jpg)

Puede Agregar a la identidad de personalidad y marca de la aplicación personalizando el control de progreso con sus propios objetos 2D/3D personalizados.

## <a name="best-practices"></a>Procedimientos recomendados
* Encadenar estrechamente la [cartelera o etiqueta, junto](billboarding-and-tag-along.md) con la presentación de progreso, ya que el usuario puede trasladar fácilmente el encabezado a un espacio vacío y perder el contexto. La aplicación podría parecerse a que se ha bloqueado si el usuario no puede ver nada. La cartelera y el etiquetado están integrados en el recurso prefabricado de progreso.
* Siempre es conveniente proporcionar información de estado sobre lo que está ocurriendo al usuario. El recurso prefabricado de progreso proporciona varios estilos visuales, incluido el progreso de tipo anillo estándar de Windows para proporcionar el estado. También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.

## <a name="see-also"></a>Vea también
* [Scripts de progreso y Prefabs en el kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Cuadro de límite](app-bar-and-bounding-box.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Colección de objetos](object-collection.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
