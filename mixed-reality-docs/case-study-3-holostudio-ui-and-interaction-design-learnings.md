---
title: 'Caso práctico: 3 aprendizajes del diseño de la interfaz de usuario e interacción de HoloStudio'
description: Aprendizaje de la interfaz de usuario y diseño de interacción de HoloStudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974829"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Caso práctico: 3 aprendizajes del diseño de la interfaz de usuario e interacción de HoloStudio

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) era una de las primeras aplicaciones de Microsoft para HoloLens. Por este motivo, teníamos que crear nuevas prácticas recomendadas para la interfaz de usuario y el diseño de interacción 3D. Hicimos esto a través de una gran cantidad de pruebas de usuario, prototipos y errores.

Sabemos que no todos los usuarios tienen los recursos a su disposición para realizar este tipo de investigación, por lo que teníamos nuestro diseñador Sr. Holographic, Marcus Ghaly, compartimos tres cosas que hemos aprendido durante el desarrollo de HoloStudio sobre la interfaz de usuario y el diseño de interacción para aplicaciones de HoloLens.

## <a name="watch-the-video"></a>Ver el vídeo

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problema #1: Las personas no quieren desplazarse por sus creaciones

Originalmente diseñamos el Workbench en HoloStudio como un rectángulo, de forma muy similar a lo que encontraría en el mundo real. El problema es que las personas tienen una duración de experiencia que les indica que permanezcan cuando se encuentren en un escritorio o trabajen frente a un equipo, por lo que no se mueven por Workbench y exploran su creación en 3D desde todos los lados.

![El diseño rectangular de Workbench en HoloStudio dissuaded que los usuarios desplazan y vean sus creaciones desde todos los lados.](images/rectangular-workbench-500px.jpg)

Teníamos la información para que el área de trabajo se redondee, de modo que no haya ningún "anverso" o claro que se supone que se debe. Cuando lo probamos, las personas empezaron a desplazarse y explorar sus creaciones por su cuenta.

![El diseño circular de Workbench anima a los usuarios a recorrer todo el proceso en torno a su creación.](images/circular-workbench-500px.jpg)

**Lo que hemos aprendido**

Siempre debe pensar en lo que se siente cómodo para el usuario. Sacar partido de su espacio físico es una característica interesante de HoloLens y algo que no se puede hacer con otros dispositivos.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problema #2: A veces, los cuadros de diálogo modales están fuera del marco holográfica

En ocasiones, es posible que el usuario esté buscando en una dirección diferente de algo que necesite su atención en la aplicación. En un equipo, puede simplemente mostrar un cuadro de diálogo, pero si lo hace en la superficie de alguien en un entorno 3D, puede parecer que el cuadro de diálogo se está obteniendo. Los necesita para leer el mensaje, pero su instinto es intentar salir de él. Esta reacción es excelente si juega un juego, pero en una herramienta diseñada para el trabajo, es menos que lo ideal.

Una vez que se han intentado algunas cosas diferentes, finalmente se ha liquidado el uso de un sistema de "burbuja de pensamiento" para nuestros cuadros de diálogo y se ha agregado tendrils que los usuarios pueden seguir a donde se requiere su atención en nuestra aplicación. También hemos realizado el pulso de tendrils, que implícitamente es una sensación de direccionalidad para que los usuarios supieran adónde ir.

![El sistema de "pensamiento de pensamiento" incluía tendrils que ofrecían una sensación de dirección, los usuarios a los que se necesitaba su atención en la aplicación.](images/thought-bubble-500px.jpg)

**Lo que hemos aprendido**

Es mucho más difícil en 3D avisar a los usuarios de las cosas que necesitan prestar atención. El uso de directores de atención, como [sonido espacial](spatial-sound.md), rayos claros o burbujas de pensamiento, puede conducir a los usuarios a dónde deben ser.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problema #3: A veces, otros hologramas pueden bloquear la interfaz de usuario

Hay veces en las que un usuario desea interactuar con un holograma y sus controles de interfaz de usuario asociados, pero se bloquea en la vista porque otro holograma está delante de ellos. Durante el desarrollo de HoloStudio, hemos usado la prueba y el error para obtener una solución.

![Un control de interfaz de usuario asociado a un holograma puede quedar bloqueado si hay otro holograma entre él y el usuario que contenga HoloLens.](images/ui-blocked-500px.jpg)

Se intentó desplazar el control de la interfaz de usuario para que no se pudiera bloquear, pero se encontró que no estaba familiarizado con el usuario de ver un control que estaba cerca de usted mientras examinaba simultáneamente un holograma que estaba lejos. Sin embargo, si se mueve el control delante del holograma más cercano al usuario, parecía que se separó del holograma que debería estar afectando.

Finalmente, terminamos con fantasma el control de IU y lo colocamos a la misma distancia del usuario que el holograma al que está asociado, por lo que ambos se sienten conectados. Esto permite al usuario interactuar con el control aunque esté oculto.

![La solución: hemos convertido en fantasma el control de interfaz de usuario, que permitía la interacción con el control y lo hicieron conectados al holograma al que estaba afectando.](images/ghosting-ui-500px.jpg)

**Lo que hemos aprendido**

Los usuarios deben poder acceder fácilmente a los controles de interfaz de usuario incluso si se han bloqueado, por lo que debe averiguar los métodos para asegurarse de que los usuarios puedan completar sus tareas independientemente de dónde se encuentren sus hologramas en el mundo real.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Diseñador de Sr. Holographic@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Interacciones instintivas](interaction-fundamentals.md)

 
