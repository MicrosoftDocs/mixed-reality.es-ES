---
title: Representación
description: Representación holográfica permite a la aplicación dibujar un holograma en una ubicación exacta en el mundo que rodea el usuario, si se coloca exactamente en el mundo físico o dentro de un dominio virtual que ha creado.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: representación, holograma
ms.openlocfilehash: 45713fd7a30fc55a799da7e89ef52aff8f7eec46
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415415"
---
# <a name="rendering"></a>Representación

Representación holográfica permite que la aplicación se va a dibujar un holograma en una ubicación exacta en el mundo que rodea el usuario, si se coloca exactamente en el mundo físico o dentro de un dominio virtual que ha creado. [Hologramas](hologram.md) son objetos de luz y sonido. Representación permite su Application agregar la luz.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Representación</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Representación holográfica

Clave a la representación holográfica es saber si está representando en una pantalla, como HoloLens que permite al usuario ver el mundo físico y sus hologramas juntos--transparente o una pantalla similar a Windows Mixed Reality auriculares envolventes que bloquea opaca el mundo.

Dispositivos con **muestra transparente**, como [HoloLens](hololens-hardware-details.md), agregar luz a todo el mundo. Los píxeles negros son totalmente transparentes, mientras que los píxeles más brillantes son cada vez más opacos. Dado que la luz de la muestra se agrega a la luz procedentes del mundo real, píxeles blancos son un poco translúcidos.

Mientras estereoscópica representación proporciona una indicación de profundidad para sus hologramas, agregar [efectos de toma de tierra](interaction-fundamentals.md) puede ayudar a los usuarios a ver más fácilmente qué superficie un holograma es cerca. Es una técnica de toma de tierra agregar un efecto de iluminado en torno a un holograma en la superficie cercana y, a continuación, representar una sombra con este efecto de iluminado. De este modo, la sombra paralela restar la luz desde el entorno. [Sonido espacial](spatial-sound.md) es otra indicación de profundidad muy importante, lo que permite el motivo de los usuarios acerca de la distancia y la ubicación relativa de un holograma.

Dispositivos con **muestra opaco**, como [inmersivos Windows Mixed Reality](immersive-headset-hardware-details.md), bloquear el mundo. Los píxeles negros son negro sólido, y cualquier otro color aparecen como ese color al usuario. La aplicación es responsable de representar todo lo que el usuario ve. Esto hace que sea aún más importante para mantener una frecuencia de actualización constante para que los usuarios tengan una experiencia cómoda.

## <a name="predicted-rendering-parameters"></a>Parámetros de representación de predicción

Mixto auriculares de realidad (HoloLens e inmersivos) continuamente realizar un seguimiento de la posición y orientación de head del usuario en relación con su entorno. Como la aplicación empieza a preparar su siguiente fotograma, el sistema predice donde principal del usuario será en el futuro en el momento exacto que se muestra el marco en las pantallas. Según esta predicción, el sistema calcula las transformaciones de proyección y de vista que se usará para ese marco. La aplicación **debe utilizar estas transformaciones para generar resultados correctos**; si no se utilizan las transformaciones proporcionado por el sistema, la imagen resultante no se alineará con el mundo real, dando lugar a malestar de usuario.

Tenga en cuenta que para predecir con precisión cuando un nuevo marco alcanzará la muestra, el sistema constantemente es medir la latencia de extremo a otro efectiva de canalización de representación de la aplicación. Mientras el sistema se ajusta a la longitud de la canalización de representación, puede mejorar la estabilidad holograma manteniendo esa canalización lo más corta posible.

Las aplicaciones que usan técnicas avanzadas para intensificar la predicción del sistema pueden invalidar las transformaciones de proyección y de vista del sistema. Estas aplicaciones deben todavía utilizar transformaciones proporcionado por el sistema como punto de partida para sus transformaciones personalizadas para generar resultados significativos.

## <a name="other-rendering-parameters"></a>Otros parámetros de representación

Cuando se presentaba un fotograma, el sistema especifica la ventanilla del búfer de reserva en el que se debe dibujar de la aplicación. Esta ventanilla a menudo es menor que el tamaño del búfer de fotograma completo. Independientemente del tamaño de la ventanilla, una vez que el marco se representa por la aplicación, el sistema upscales la imagen para rellenar la totalidad de la muestra.

Para las aplicaciones que se encuentran no se pueden representar en la frecuencia de actualización necesarios, [se pueden configurar los parámetros de representación del sistema](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) para reducir la presión de memoria y el costo de representación a costa de alias de píxel mayor. El formato de búfer de reserva también puede cambiarse, lo que, para algunas aplicaciones puede ayudar a mejorar el rendimiento de píxeles y el ancho de banda de memoria.

El frustum de representación, la resolución y velocidad de fotogramas en el que se le pide para representar la aplicación también podrían cambiar de fotograma a fotograma y pueden diferir entre el ojo izquierdo y derecho. Por ejemplo, cuando [mixto captura realidad](mixed-reality-capture.md) (MRC) está activo y el [ver configuración de la cámara de fotografías y vídeo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) no es participar en, en un ojo podría representarse con una mayor FOV o resolución.

Para cualquier marco, la aplicación *debe* representar mediante la transformación de vista, la transformación de proyección y la resolución de ventanilla proporcionados por el sistema. Además, la aplicación nunca debe suponer que cualquier parámetro de representación o la vista permanece fija de fotograma a fotograma. Los motores, como Unity controlan todas estas transformaciones por usted en sus propios objetos de la cámara para que siempre se respeta el traslado físico de los usuarios y el estado del sistema. Si la aplicación permite moverlas virtual del usuario a través del mundo (por ejemplo, mediante la tecla de navegación en un controlador para juegos), puede agregar un objeto de la plataforma de pruebas primario por encima de la cámara que se mueve por. Esto hace que la cámara para que refleje tanto el movimiento física y virtual del usuario. Si la aplicación modifica la transformación de vista, transformación de proyección o dimensión de ventanilla proporcionada por el sistema, debe informar al sistema mediante una llamada a la correspondiente [invalidar API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose).

Para mejorar la estabilidad de su representación holográfica, la aplicación debe proporcionar a Windows cada fotograma usa para representar el búfer de profundidad. Si la aplicación proporciona un búfer de profundidad, debe tener valores de profundidad coherente, con profundidad expresa en metros de la cámara. Esto permite al sistema a usar los datos de profundidad por píxel para estabilizar mejor contenido si principal del usuario termina desplacen ligeramente a la ubicación de la predicción. Si no es capaz de proporcionar el búfer de profundidad, puede proporcionar un punto de enfoque y normal, define un plano que corta durante la mayor parte de su contenido. Si se proporcionan el búfer de profundidad y un plano de foco, el sistema podría usar ambos. En concreto, es útil proporcionar el búfer de profundidad y un punto de enfoque que incluye un vector de velocidad cuando la aplicación muestra hologramas que están en movimiento.

Consulte [de representación en DirectX](rendering-in-directx.md) artículo para obtener detalles de bajo nivel sobre su tema.

## <a name="holographic-cameras"></a>Cámaras holográficas

Windows Mixed Reality introduce el concepto de un **cámara holográfica**. Cámaras holográficas son similares a la cámara tradicional que se encuentra en los textos de gráficos 3D: definen tanto la extrínsecos (posición y orientación) y las propiedades intrínsecas de cámara. (Por ejemplo:, se usa el campo de vista para ver una escena 3D virtual.) A diferencia de las cámaras 3D tradicionales, la aplicación no está en el control de posición, orientación y las propiedades intrínsecas de la cámara. En su lugar, la posición y la orientación de la cámara holográfica implícitamente se controla mediante el desplazamiento del usuario. El desplazamiento del usuario se retransmite a la aplicación según el fotograma a fotograma a través de una transformación de vista. Del mismo modo, las propiedades intrínsecas de la cámara se definen mediante la óptica calibrada del dispositivo y retransmiten fotograma a fotograma a través de la transformación de proyección.

En general se representará la aplicación para una sola cámara estéreo. Sin embargo, un bucle de representación sólida admitirá varias cámaras y será compatible con las cámaras de mono y estéreo. Por ejemplo, el sistema podría solicitar la aplicación para representar desde una perspectiva alternativa cuando el usuario activa una característica como [mixto captura realidad](mixed-reality-capture.md) (MRC), dependiendo de la forma de los auriculares en cuestión. Las aplicaciones que pueden admitir varias cámaras obtención [participar en](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) a la [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) de cámaras que pueden admitir.

## <a name="volume-rendering"></a>Representación de volumen

Cuando representación Resonance médica o volúmenes en 3D, de ingeniería [representación volumen](volume-rendering.md) técnicas se usan a menudo. Estas técnicas pueden ser especialmente interesantes en mixed reality, donde los usuarios pueden ver naturalmente estos volúmenes de ángulos de claves, basta con mover su cabeza.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Admite resoluciones en HoloLens (gen 1)
> [!NOTE]
> Más actualizaciones estarán disponibles próximamente. [Ver la lista de actualizaciones](release-notes-april-2018.md)

* Las resoluciones actuales y máxima admitidas son propiedades de la [ver configuración](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens se establece en la resolución máxima, que es 720p (1268 x 720), de forma predeterminada.
* El tamaño mínimo admitido ventanilla es 50% de 720p, que es 360p (634 x 360). En HoloLens, se trata de un ViewportScaleFactor de 0,5.
* Algo inferior a la p 540 es **no recomienda** debido a una degradación visual, pero se puede usar para identificar el cuello de botella en la tasa de relleno de píxeles.

## <a name="supported-resolutions-on-hololens-2"></a>Soluciones compatibles en HoloLens 2

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).


## <a name="see-also"></a>Vea también
* [Estabilidad de hologramas](hologram-stability.md)
* [Representación en DirectX](rendering-in-directx.md)
