---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, la interfaz de usuario, experiencia de usuario
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813730"
---
# <a name="displaying-progress"></a>Mostrar progreso

Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga. Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.

![Ejemplo de anillo de progreso en HoloLens](images/HoloLens2_Loader.gif)<br>
*Ejemplo de anillo de progreso en HoloLens*

## <a name="types-of-progress"></a>Tipos de progreso

Es importante proporcionar al usuario información sobre lo que sucede. En realidad mixta los usuarios pueden fácilmente distraerse por entorno físico u objetos si la aplicación no da buenos comentarios visuales. Para situaciones que tardan unos segundos, por ejemplo, cuando se está cargando datos o una escena se está actualizando, es buena idea para mostrar un indicador visual. Hay dos opciones para mostrar al usuario que una operación está en curso: un **barra de progreso** o un **anillo de progreso**.

### <a name="progress-bar"></a>Barra de progreso

![Ejemplo de la barra de progreso en HoloLens](images/640px-progressbar.jpg)

Una barra de progreso muestra el porcentaje completado de una tarea. Se debe usar durante una operación cuya duración se conoce (determinada), pero su progreso no debe bloquear la interacción del usuario con la aplicación.

### <a name="progress-ring"></a>Círculo de progreso

![Ejemplo de anillo de progreso en HoloLens](images/640px-progressring.jpg)

Un anillo de progreso debe usarse cuando ninguna intervención del usuario se bloquea hasta que se ha completado la operación y solo tiene un estado indeterminado.

### <a name="progress-with-a-custom-object"></a>Progreso con un objeto personalizado

![Progreso de la malla personalizada de ejemplo en HoloLens](images/640px-progresscustom.jpg)

Puede agregar a la personalidad de la aplicación y la identidad de marca personalizando el control de progreso con sus propios objetos 2D o 3D personalizados.

## <a name="best-practices"></a>Procedimiento recomendado
* Acoplando [vallas publicitarias o tag-along](billboarding-and-tag-along.md) a la pantalla de progreso, ya que el usuario puede mover su cabeza a un espacio vacío fácilmente y perder contexto de. La aplicación puede parecer que se ha bloqueado si el usuario no puede ver nada. Billboarding y tag-along está integrado en el recurso prefabricado de progreso.
* Siempre es bueno proporcionar información de estado sobre lo que sucede al usuario. El recurso prefabricado de progreso proporciona varios estilos visuales, incluidos el progreso de tipo de anillo estándar de Windows para proporcionar el estado. También puede usar una malla personalizada con una animación si desea que el estilo de su progreso para alinearse con la marca de la aplicación.

## <a name="see-also"></a>Vea también
* [Scripts de progreso y prefabricados en el Kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [Cuadro de límite](app-bar-and-bounding-box.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Colección de objetos](object-collection.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
