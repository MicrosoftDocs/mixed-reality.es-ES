---
title: 'Caso práctico: HoloStudio 3 interfaz de usuario y la interacción de diseño aprendizajes'
description: HoloStudio UI y conocimientos de diseño de interacción
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloLens, HoloStudio, la realidad mixta
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605355"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Caso práctico: HoloStudio 3 interfaz de usuario y la interacción de diseño aprendizajes

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) era una de las primeras aplicaciones de Microsoft para HoloLens. Por este motivo, tuvimos que crear nuevas y mejores prácticas para 3D de la interfaz de usuario y el diseño de interacción. Esto es lo hicimos a través de una gran cantidad de pruebas de usuario, creación de prototipos y pruebas y errores.

Sabemos que no todo el mundo tiene los recursos a su disposición para realizar este tipo de investigación, por lo que teníamos nuestra diseñador holográfica senior, Marcus Ghaly, compartir tres cosas aprendimos durante el desarrollo de HoloStudio sobre el diseño de interfaz de usuario y la interacción para aplicaciones de HoloLens.

## <a name="watch-the-video"></a>Vea el vídeo

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problema #1: Las personas no deseaba mover sus creaciones

Se diseñó originalmente en HoloStudio workbench como un rectángulo, mucho que encontrará en el mundo real. El problema es que las personas tienen una duración de la experiencia que les indica que permanezca aún cuando están sentados en una mesa o trabajar frente a un equipo, por lo que no estaban moverse por el área de trabajo y explorar su creación en 3D desde todos los lados.

![El diseño rectangular de workbench en HoloStudio dissuaded a los usuarios mover y ver sus creaciones de todos los lados.](images/rectangular-workbench-500px.jpg)

Teníamos los conocimientos para hacer que workbench redondear, por lo que se ha producido ninguna "delante" o borrar el lugar al que se suponía que debía independiente. Cuando lo probamos, repentinamente personas a mover y explorar sus creaciones en sus propios.

![El diseño de workbench circular aconseja a los usuarios recorrer todo sentido sus creaciones.](images/circular-workbench-500px.jpg)

**¿Qué hemos aprendido**

Siempre se puede pensar en lo que es cómodo para el usuario. Sacar provecho de su espacio físico es una interesante característica de HoloLens y algo que no se puede hacer con otros dispositivos.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problema #2: Los cuadros de diálogo modales a veces están fuera del marco holográfico

A veces, el usuario puede buscar en una dirección diferente de lo que necesita su atención en la aplicación. En un equipo, que puede simplemente la ventana emergente de seguridad de un cuadro de diálogo, pero si lo hace en la cara de una persona en un entorno 3D, puede sentir como si el cuadro de diálogo se está metiendo su manera. Debe leer el mensaje, pero su instinto es intentar obtener fuera de él. Esta reacción es fantástica si juega un juego, pero en una herramienta diseñada para el trabajo, es ideal.

Después de probar algunas cosas diferentes, finalmente se liquidan sobre el uso de un sistema de "pensé burbuja" para nuestro cuadros de diálogo y agregan tendrils que los usuarios pueden seguir para que sea necesaria su atención en nuestra aplicación. También hemos realizado el pulso tendrils, lo que suponía una sensación de direccionalidad para que los usuarios supieran dónde debe ir.

![El sistema "Pensé burbuja" incluye parpadeante tendrils que proporciona una idea de dirección, dando lugar a los usuarios a que se necesita su atención en la aplicación.](images/thought-bubble-500px.jpg)

**¿Qué hemos aprendido**

Es mucho más difícil en 3D alertar a los usuarios lo que necesitan prestar atención a. Con los directores de atención como [sonido espacial](spatial-sound.md), rayos con poca o burbujas de pensamiento, puede dar lugar a los usuarios a donde deben estar.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problema #3: A veces, la interfaz de usuario puede bloquearse por otros hologramas

Hay veces cuando un usuario desea interactuar con un holograma y sus controles de interfaz de usuario asociadas, pero están bloqueados en la vista porque otro holograma está delante de ellas. Mientras estábamos desarrollando HoloStudio, hemos usado la prueba y error para llegar a una solución para esto.

![Un control de interfaz de usuario asociado con un holograma puede quedarse bloqueado si hay otro holograma entre ella y el usuario gastando de HoloLens.](images/ui-blocked-500px.jpg)

Se ha intentado mover el control de interfaz de usuario más cercano al usuario, por lo que no se pudo obtener bloqueada, pero se encontró que no le bastaba con el usuario examina un control que se ha producido cerca al mirar simultáneamente un holograma que era muy lejos. Si, sin embargo, se mueve el control delante el holograma más cercano al usuario, sentía como se separó del holograma debe estar afectando a.

Por último terminé fantasma el control de interfaz de usuario y colocarlo en la misma distancia desde el usuario como el holograma que está asociado, por lo que ambos se sienten conectados. Esto permite al usuario interactuar con el control, aunque se ha está oculto.

![La solución: se reflejó el control de interfaz de usuario, que permite la interacción con el control y llegó a sentirse está conectado a la holograma lo estaba afectando a.](images/ghosting-ui-500px.jpg)

**¿Qué hemos aprendido**

Los usuarios necesitan poder tener acceso fácilmente a los controles de interfaz de usuario incluso si ha bloqueados, así que descubra métodos para asegurarse de que los usuarios pueden completar sus tareas con independencia de dónde están sus hologramas en el mundo real.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Diseñador holográfico senior @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Aspectos básicos de interacción](interaction-fundamentals.md)

 
