---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, la interfaz de usuario, experiencia de usuario
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605356"
---
# <a name="displaying-progress"></a>Mostrar progreso

Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga. Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.

![Ejemplo de anillo de progreso en HoloLens](images/640px-progress-hero.jpg)<br>
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
* [Secuencias de comandos y prefabricados para el progreso en el Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [Objeto interactuable](interactable-object.md)
* [Colección de objetos](object-collection.md)
* [Vallas publicitarias y tag-along](billboarding-and-tag-along.md)
