---
title: Representación
description: La representación holográfica permite a la aplicación dibujar un holograma en una ubicación precisa del mundo en torno al usuario, independientemente de si está colocado exactamente en el mundo físico o en un dominio virtual que haya creado.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: representación, holograma
ms.openlocfilehash: 9c32d8ddf5a1fb9e9d991211756ba1306f4d3fa9
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926861"
---
# <a name="rendering"></a>Representación

La representación holográfica permite a la aplicación dibujar un holograma en una ubicación precisa del mundo alrededor del usuario, independientemente de si está colocado exactamente en el mundo físico o en un dominio virtual que haya creado. Los [hologramas](hologram.md) son objetos que se componen de sonido y luz. La representación permite que la aplicación agregue la luz.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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

La clave para la representación holográfica es saber si está representando una pantalla de visualización a través como HoloLens que permite al usuario ver el mundo físico y los hologramas juntos, o una pantalla opaca como un casco de realidad de Windows mezclado que se bloquea. el mundo.

Los dispositivos con **visualizaciones de consulta**, como [HoloLens](hololens-hardware-details.md), agregan luz al mundo. Los píxeles negros son completamente transparentes, mientras que los píxeles más brillantes son cada vez más opacos. Dado que la luz de las pantallas se agrega a la luz del mundo real, los píxeles blancos son en cierto modo translúcidos.

Aunque la representación de Stereoscopic proporciona una indicación de profundidad para los hologramas, la adición de efectos de la [base](interaction-fundamentals.md) puede ayudar a los usuarios a ver con más facilidad qué superficie tiene un holograma. Una técnica de base consiste en agregar un resplandor alrededor de un holograma en la superficie cercana y, a continuación, representar una sombra en este resplandor. De este modo, parece que la sombra resta luz del entorno. El [sonido espacial](spatial-sound.md) es otra pista de profundidad extremadamente importante que permite a los usuarios conocer la distancia y la ubicación relativa de un holograma.

Los dispositivos con **pantallas opacas**, como las de [Windows Mixed Reality con auriculares](immersive-headset-hardware-details.md), bloquean el mundo. Los píxeles negros son negros sólidos y cualquier otro color aparece como ese color para el usuario. La aplicación es responsable de representar todo lo que ve el usuario. Esto hace que sea aún más importante mantener una frecuencia de actualización constante para que los usuarios tengan una experiencia cómoda.

## <a name="predicted-rendering-parameters"></a>Parámetros de representación de predicción

Los auriculares de realidad mixta (tanto HoloLens como con auriculares envolvente) realizan un seguimiento continuo de la posición y la orientación del cabezal del usuario con respecto a su entorno. A medida que la aplicación comienza a preparar el siguiente fotograma, el sistema predice dónde estará el encabezado del usuario en el momento exacto en que se muestra el fotograma en las pantallas. En función de esta predicción, el sistema calcula las transformaciones de vista y proyección que se van a usar para ese marco. La aplicación **debe usar estas transformaciones para generar resultados correctos**. Si no se utilizan transformaciones proporcionadas por el sistema, la imagen resultante no se alineará con el mundo real, lo que provocará la molestia del usuario.

Tenga en cuenta que para predecir con precisión cuándo un nuevo fotograma llegará a las pantallas, el sistema medirá constantemente la latencia de extremo a extremo efectiva de la canalización de representación de la aplicación. Mientras el sistema se ajusta a la longitud de la canalización de representación, puede mejorar la estabilidad del holograma manteniendo la canalización lo más corta posible.

Las aplicaciones que utilizan técnicas avanzadas para aumentar la predicción del sistema pueden invalidar la vista del sistema y las transformaciones de proyección. Estas aplicaciones deben seguir usando transformaciones proporcionadas por el sistema como base para sus transformaciones personalizadas con el fin de generar resultados significativos.

## <a name="other-rendering-parameters"></a>Otros parámetros de representación

Al representar un fotograma, el sistema especifica la ventanilla del búfer de reserva en la que se debe dibujar la aplicación. Esta ventanilla suele ser más pequeña que el tamaño completo del búfer de fotogramas. Independientemente del tamaño de la ventanilla, una vez que la aplicación represente el fotograma, el sistema escala la imagen para rellenar la totalidad de las pantallas.

En el caso de las aplicaciones que no se pueden representar con la frecuencia de actualización necesaria, [los parámetros de representación del sistema se pueden configurar](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) para reducir la presión de memoria y el costo de representación a costa del aumento de los alias de píxeles. También se puede cambiar el formato del búfer de reserva, que para algunas aplicaciones puede ayudar a mejorar el ancho de banda de memoria y el rendimiento de los píxeles.

El frustum de representación, la resolución y la velocidad de fotogramas en la que se solicita la representación de la aplicación también pueden cambiar de un marco a otro y pueden diferir en el ojo izquierdo y derecho. Por ejemplo, cuando la [captura de realidad mixta](mixed-reality-capture.md) (MRC) está activa y la configuración de la [vista de cámara de foto/vídeo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) no se ha incorporado, un ojo podría representarse con un gran tamaño o resolución.

Para cualquier fotograma determinado, la aplicación *debe* representarse mediante la transformación de la vista, la transformación de la proyección y la resolución de la ventanilla proporcionada por el sistema. Además, la aplicación nunca debe asumir que cualquier parámetro de representación o vista permanece fijo de fotograma a fotograma. Los motores como Unity controlan todas estas transformaciones en sus propios objetos de cámara, de modo que siempre se respeta el movimiento físico de los usuarios y el estado del sistema. Si la aplicación permite el movimiento virtual del usuario a través del mundo (por ejemplo, con el stick analógico en un controlador de juegos), puede Agregar un objeto de plataforma de control principal encima de la cámara que lo mueve. Esto hace que la cámara refleje el movimiento virtual y físico del usuario. Si la aplicación modifica la transformación de la vista, la transformación de proyección o la dimensión de ventanilla proporcionada por el sistema, debe informar al sistema mediante una llamada a la [API de invalidación](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)adecuada.

Para mejorar la estabilidad de la representación holográfica, la aplicación debe proporcionar a Windows cada fotograma el búfer de profundidad que se usa para la representación. Si la aplicación proporciona un búfer de profundidad, debe tener valores de profundidad coherentes, con una profundidad expresada en metros de la cámara. Esto permite que el sistema use los datos de profundidad por píxel para estabilizar mejor el contenido si el encabezado del usuario termina ligeramente desplazado desde la ubicación de predicción. Si no puede proporcionar el búfer de profundidad, puede proporcionar un punto de enfoque y normal, y definir un plano que recorte la mayor parte del contenido. Si se proporcionan el búfer de profundidad y un plano de foco, el sistema podría usar ambos. En concreto, es útil proporcionar el búfer de profundidad y un punto de enfoque que incluye un vector de velocidad cuando la aplicación muestra hologramas que están en movimiento.

Consulte el artículo sobre [representación en DirectX](rendering-in-directx.md) para obtener detalles de bajo nivel sobre su tema.

## <a name="holographic-cameras"></a>Cámaras holográficas

Windows Mixed Reality presenta el concepto de una **cámara holográfica**. Las cámaras holográficas son similares a la cámara tradicional que se encuentra en los textos de gráficos 3D: definen las propiedades extrínsecos (posición y orientación) y de cámara intrínseca. (Por ejemplo:, el campo de vista se usa para ver una escena 3D virtual). A diferencia de las cámaras 3D tradicionales, la aplicación no tiene el control de la posición, la orientación y las propiedades intrínsecas de la cámara. En su lugar, el movimiento del usuario controla implícitamente la posición y la orientación de la cámara holográfica. El movimiento del usuario se retransmite a la aplicación de forma fotograma a fotograma a través de una transformación de vista. Del mismo modo, las propiedades intrínsecas de la cámara se definen mediante los dispositivos ópticos calibrados del dispositivo y el marco por fotograma retransmitido a través de la transformación de proyección.

En general, la aplicación se representará para una sola cámara estéreo. Sin embargo, un bucle de representación sólido será compatible con varias cámaras y admitirá cámaras mono y estéreo. Por ejemplo, el sistema puede pedir a la aplicación que se represente desde una perspectiva alternativa cuando el usuario activa una característica como [captura de realidad mixta](mixed-reality-capture.md) (MRC), dependiendo de la forma de los auriculares en cuestión. Las aplicaciones que pueden admitir varias cámaras las obtienen al [participar en el](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) de cámaras que pueden admitir.

## <a name="volume-rendering"></a>Representación de volumen

Al representar volúmenes médicos MRIs o de ingeniería en 3D, a menudo se utilizan técnicas de [representación por volumen](volume-rendering.md) . Estas técnicas pueden ser especialmente interesantes en la realidad mixta, donde los usuarios pueden ver de forma natural dicho volumen desde ángulos clave, simplemente moviendo su principal.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Resoluciones admitidas en HoloLens (1ª generación)
> [!NOTE]
> Próximamente habrá más actualizaciones. [Ver la lista de actualizaciones](release-notes-april-2018.md)

* Las resoluciones actuales y máximas admitidas son las propiedades de la configuración de la [vista](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens se establece en la resolución máxima, que es 720p (1268x720), de forma predeterminada.
* El tamaño de ventanilla compatible más bajo es el 50% de 720p, que es 360p (634x360). En HoloLens, se trata de un ViewportScaleFactor de 0,5.
* **No se recomienda** nada inferior a 540P debido a la degradación visual, pero se puede usar para identificar cuellos de botella en la velocidad de relleno de píxeles.

## <a name="supported-resolutions-on-hololens-2"></a>Resoluciones admitidas en HoloLens 2

> [!NOTE]
> [Próximamente](news.md)se ofrecerá orientación específica para HoloLens 2.


## <a name="see-also"></a>Consulta también
* [Estabilidad de hologramas](hologram-stability.md)
* [Representación en DirectX](rendering-in-directx.md)
