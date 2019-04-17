---
title: Aspectos básicos de interacción
description: Como hemos creado las experiencias en HoloLens (gen 1), 2 de HoloLens e inmersivos, hemos iniciado anotar algunas cosas que se han encontrado útiles para compartir.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Diseño de interacción, la realidad mixta
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597548"
---
# <a name="interaction-fundamentals"></a>Aspectos básicos de interacción

Como hemos creado las experiencias en HoloLens e inmersivos, comenzamos anotar algunas cosas que se han encontrado útiles para compartir. Piense en estos elementos como los bloques constitutivos fundamentales para el diseño de interacción de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

Aquí tiene un resumen de los artículos de diseño de interacción disponibles y qué tipo de dispositivo o tipos que se aplican a.
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>entrada</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">Manos articuladas</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">Destinatarios de ojo</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">Mirada destinadas a</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">Gestos</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">Diseño de voz</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> Controlador para juegos</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">Controladores de movimiento</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>Percepción y las características espaciales</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">Diseño espacial de sonido</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">Diseño de la asignación espacial</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">Hologramas</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>El usuario es la cámara

![Usuario es la cámara](images/useriscamera-640px.jpg)

Piense sobre el diseño para el punto de vista de los usuarios siempre cuando pasen sobre sus ámbitos reales y virtuales.

**Algunas preguntas que debe hacer**
* ¿Es el usuario la oportunidad de sentarse, reclinables, permanente o caminar al usar su experiencia?
* ¿Cómo se ajustar su contenido en diferentes posiciones?
* ¿El usuario puede ajustarlo?
* ¿El usuario estará familiarizado con el uso de la aplicación?

**Procedimientos recomendados**
* El usuario es la cámara y controlan el movimiento. Deje que su unidad.
* Si tiene que transportar prácticamente el usuario, ser sensibles a los problemas en torno a vestibular molestias.
* Usar animaciones más cortas
* Animar desde abajo, izquierda y derecha o Fundido de entrada en lugar de Z
* Ralentizar el tiempo
* Permitir al usuario ver el mundo en segundo plano

**Lo que debe evitar**
* No agite la cámara o deliberadamente bloquearla en 3DOF (sólo orientación, ninguna traducción), puede hacer que los usuarios sienten incómodos.
* Ningún movimiento abrupta. Si tiene que poner el contenido a o desde el usuario, muévalo lentamente y sin problemas hacia ellos para obtener la máxima comodidad. Los usuarios reaccionará a menús grandes estará disponible en ellos.
* No acelerar o activar la cámara del usuario. Los usuarios son sensibles a la aceleración (angular y traslación).

## <a name="leverage-the-users-perspective"></a>Aproveche la perspectiva del usuario

Los usuarios ver el mundo de la realidad mixta a través de la muestra en los dispositivos envolventes y holográficas. En el HoloLens, se llama a esta pantalla el [marco holográfica](holographic-frame.md).

En el desarrollo 2D, se puede colocar contenido a los que accede con frecuencia y la configuración en las esquinas de una pantalla para hacerlos fácilmente accesibles. Sin embargo, en aplicaciones holográficas, puede ser incómodo para tener acceso a contenido en las esquinas de la vista del usuario. En este caso, el centro del marco holográfico es la ubicación principal para el contenido.

El usuario deba ser guiada por perfiles para ayudar a localizar los eventos importantes u objetos más allá de su vista inmediata. Puede usar flechas, seguimientos de luz, movimiento carácter, bocadillos, punteros, sonido espacial y los mensajes de voz para ayudar a guiar al usuario al contenido importante en la aplicación.

Se recomienda no bloquear contenido en la pantalla para mayor comodidad del usuario. Si tiene que conservar el contenido de la vista, colóquelo en el mundo y hacer que el contenido "tag-along" como el menú Inicio. Se sentirá más natural en el entorno de contenido que se extrae junto con la perspectiva del usuario.

![El menú inicio sigue a la vista del usuario cuando se alcanza el borde del marco](images/tagalong-1000px.jpg)<br>
*El menú inicio sigue a la vista del usuario cuando se alcanza el borde del marco*

En HoloLens, hologramas sentirse real cuando ya que no se recorten caben dentro del marco holográfico. Los usuarios se moverán para ver los límites de un holograma dentro del marco. En HoloLens, es importante simplificar la interfaz de usuario para ajustarse a la vista del usuario y mantiene el foco en la acción principal. Para inmersivos, es importante mantener la ilusión de un mundo virtual persistente dentro campo de la vista del dispositivo en el.

## <a name="user-comfort"></a>Comodidad del usuario

Para garantizar el máximo [confort](comfort.md) en pantallas montada head, es importante para los diseñadores y desarrolladores a crear y presentar el contenido de forma que se asemeje a cómo los seres humanos interpretan las formas 3D y la posición relativa de los objetos en natural mundo. Desde una perspectiva física, también es importante diseñar el contenido que no requiera la fatiga de los movimientos del cuello o armas.

Si el desarrollo para HoloLens o inmersivos, es importante representar objetos visuales para ambos ojos. Representación de una pantalla informativa en un ojo solo puede realizar una interfaz difíciles de entender, así como causando uneasiness al ojo y el cerebro del usuario.

## <a name="share-your-experience"></a>Comparta su experiencia

Uso de [mixto captura realidad](mixed-reality-capture.md), los usuarios pueden capturar fotos o vídeos de su experiencia en cualquier momento. Considere la posibilidad de experiencias en la aplicación donde que desea animar a las instantáneas o los vídeos.

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>Aproveche los elementos básicos de la interfaz de usuario de Windows Mixed Reality principal

Al igual que la experiencia de PC de Windows se inicia con el escritorio, Windows Mixed Reality comienza con la página principal. El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) aprovecha nuestra capacidad para comprender y navegar por los lugares 3D innata. Con HoloLens, su casa es el espacio físico. Con inmersivos, su casa es un espacio virtual.

Su casa es también donde usará el menú Inicio para abrir y colocar las aplicaciones y el contenido. Puede rellenar su hogar con contenido de realidad mixta y realizar varias tareas mediante el uso de varias aplicaciones al mismo tiempo. Las cosas que se coloca en su hogar permanecen allí, incluso si reinicia el dispositivo.

## <a name="see-also"></a>Vea también
* [Mirada destinadas a](gaze-targeting.md)
* [Gestos](gestures.md)
* [Diseño de voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
* [Diseño espacial de sonido](spatial-sound-design.md)
* [Diseño de la asignación espacial](spatial-mapping-design.md)
* [Comodidad](comfort.md)
* [Navegar por el inicio de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
