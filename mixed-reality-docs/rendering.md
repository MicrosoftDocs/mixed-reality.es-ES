---
title: Representación
description: La representación holográfica permite a la aplicación dibujar un holograma en una ubicación precisa del mundo en torno al usuario, independientemente de si está colocado exactamente en el mundo físico o en un dominio virtual que haya creado.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: representación, holograma
ms.openlocfilehash: 544e43ced57309cfe2628cbea65d07e94563eb41
ms.sourcegitcommit: 317653cd8500563c514464f0337c1f230a6f3653
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/28/2019
ms.locfileid: "75503823"
---
# <a name="rendering"></a>Representación

La representación holográfica permite a la aplicación dibujar un holograma en una ubicación precisa del mundo alrededor del usuario, ya sea de forma precisa en el mundo físico o en un dominio virtual que haya creado. Los [hologramas](hologram.md) son objetos que se componen de sonido y luz. La representación permite que la aplicación agregue la luz.

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

La clave para la representación holográfica es saber si está representando una pantalla de visualización a través como HoloLens que permite al usuario ver el mundo físico y los hologramas juntos, o una pantalla opaca como un casco de realidad mixta de Windows que bloquea el WWPN.

Los dispositivos con **pantallas de consulta**, como [HoloLens](hololens-hardware-details.md), agregan Light al mundo. Los píxeles negros son completamente transparentes, mientras que los píxeles más brillantes son cada vez más opacos. Dado que la luz de las pantallas se agrega a la luz del mundo real, los píxeles blancos son en cierto modo translúcidos.

Aunque la representación de Stereoscopic proporciona una indicación de profundidad para los hologramas, la adición de efectos de la [base](interaction-fundamentals.md) puede ayudar a los usuarios a ver con más facilidad qué superficie tiene un holograma. Una técnica de base consiste en agregar un resplandor alrededor de un holograma en la superficie cercana y, a continuación, representar una sombra en este resplandor. De este modo, parece que la sombra resta luz del entorno. El [sonido espacial](spatial-sound.md) es otra pista de profundidad extremadamente importante que permite a los usuarios conocer la distancia y la ubicación relativa de un holograma.

Los dispositivos con **pantallas opacas**, como las de [Windows Mixed Reality con auriculares](immersive-headset-hardware-details.md), bloquean el mundo. Los píxeles negros son negros sólidos y cualquier otro color aparece como ese color para el usuario. La aplicación es responsable de representar todo lo que ve el usuario. Esto hace que sea aún más importante mantener una frecuencia de actualización constante para que los usuarios tengan una experiencia cómoda.

## <a name="predicted-rendering-parameters"></a>Parámetros de representación de predicción

Los auriculares de realidad mixta (tanto HoloLens como con auriculares envolvente) realizan un seguimiento continuo de la posición y la orientación del cabezal del usuario con respecto a su entorno. A medida que la aplicación comienza a preparar el siguiente fotograma, el sistema predice dónde estará el encabezado del usuario en el momento exacto en que se muestra el fotograma en las pantallas. En función de esta predicción, el sistema calcula la vista y las transformaciones de proyección que se van a usar para ese marco. La aplicación **debe usar estas transformaciones para generar resultados correctos**. Si no se utilizan transformaciones proporcionadas por el sistema, la imagen resultante no se alineará con el mundo real, lo que provocará la molestia del usuario.

Tenga en cuenta que para predecir con precisión cuándo un nuevo fotograma llegará a las pantallas, el sistema medirá constantemente la latencia de extremo a extremo efectiva de la canalización de representación de la aplicación. Mientras el sistema se ajusta a la longitud de la canalización de representación, puede mejorar la estabilidad del holograma manteniendo la canalización lo más corta posible.

Las aplicaciones que utilizan técnicas avanzadas para aumentar la predicción del sistema pueden invalidar la vista del sistema y las transformaciones de proyección. Estas aplicaciones todavía deben usar transformaciones proporcionadas por el sistema como base para sus transformaciones personalizadas con el fin de generar resultados significativos.

## <a name="other-rendering-parameters"></a>Otros parámetros de representación

Al representar un fotograma, el sistema especifica la ventanilla del búfer de reserva en la que se debe dibujar la aplicación. Esta ventanilla suele ser más pequeña que el tamaño completo del búfer de fotogramas. Independientemente del tamaño de la ventanilla, una vez que la aplicación represente el fotograma, el sistema escala la imagen para rellenar la totalidad de las pantallas.

En el caso de las aplicaciones que no se pueden representar con la frecuencia de actualización necesaria, [los parámetros de representación del sistema se pueden configurar](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) para reducir la presión de memoria y el costo de representación a costa del aumento de los alias de píxeles. También se puede cambiar el formato del búfer de reserva, que para algunas aplicaciones puede ayudar a mejorar el ancho de banda de memoria y el rendimiento de los píxeles.

El frustum de representación, la resolución y la velocidad de fotogramas en la que se solicita la representación de la aplicación también pueden cambiar de un marco a otro y pueden diferir en el ojo izquierdo y derecho. Por ejemplo, cuando la [captura de realidad mixta](mixed-reality-capture.md) (MRC) está activa y la configuración de la [vista de cámara de foto/vídeo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) no se ha incorporado, un ojo podría representarse con un gran tamaño o resolución.

Para cualquier fotograma determinado, la aplicación *debe* representarse mediante la transformación de la vista, la transformación de la proyección y la resolución de la ventanilla proporcionada por el sistema. Además, la aplicación nunca debe asumir que cualquier parámetro de representación o vista permanece fijo de fotograma a fotograma. Los motores como Unity controlan todas estas transformaciones en sus propios objetos de cámara, de modo que siempre se respeta el movimiento físico de los usuarios y el estado del sistema. Si la aplicación permite el movimiento virtual del usuario a través del mundo (por ejemplo, con el stick analógico en un controlador de juegos), puede Agregar un objeto de plataforma de control principal encima de la cámara que lo mueve. Esto hace que la cámara refleje el movimiento virtual y físico del usuario. Si la aplicación modifica la transformación de la vista, la transformación de proyección o la dimensión de ventanilla proporcionada por el sistema, debe informar al sistema mediante una llamada a la [API de invalidación](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)adecuada.

Para mejorar la estabilidad de la representación holográfica, la aplicación debe proporcionar a Windows cada fotograma el búfer de profundidad que se usa para la representación. Si la aplicación proporciona un búfer de profundidad, debe tener valores de profundidad coherentes, con una profundidad expresada en metros de la cámara. Esto permite que el sistema use los datos de profundidad por píxel para estabilizar mejor el contenido si el encabezado del usuario termina ligeramente desplazado desde la ubicación de predicción. Si no puede proporcionar el búfer de profundidad, puede proporcionar un punto de enfoque y normal, y definir un plano que recorte la mayor parte del contenido. Si se proporcionan el búfer de profundidad y un plano de foco, el sistema podría usar ambos. En concreto, es útil proporcionar el búfer de profundidad y un punto de enfoque que incluye un vector de velocidad cuando la aplicación muestra hologramas que están en movimiento.

Consulte el artículo sobre [representación en DirectX](rendering-in-directx.md) para obtener detalles de bajo nivel sobre su tema.

## <a name="holographic-cameras"></a>Cámaras holográficas

Windows Mixed Reality presenta el concepto de una **cámara holográfica**. Las cámaras holográficas son similares a la cámara tradicional que se encuentra en los textos de gráficos 3D; definen las propiedades extrínsecos (posición y orientación) y de cámara intrínseca. (Por ejemplo:, el campo de vista se usa para ver una escena 3D virtual). A diferencia de las cámaras 3D tradicionales, la aplicación no tiene el control de la posición, la orientación y las propiedades intrínsecas de la cámara. En su lugar, el movimiento del usuario controla implícitamente la posición y la orientación de la cámara holográfica. El movimiento del usuario se retransmite a la aplicación de forma fotograma a fotograma a través de una transformación de vista. Del mismo modo, las propiedades intrínsecas de la cámara se definen mediante los dispositivos ópticos calibrados del dispositivo y el marco por fotograma retransmitido a través de la transformación de proyección.

En general, la aplicación se representará para una sola cámara estéreo. Sin embargo, un bucle de representación sólido será compatible con varias cámaras y admitirá cámaras mono y estéreo. Por ejemplo, el sistema puede pedir a la aplicación que se represente desde una perspectiva alternativa cuando el usuario activa una característica como [captura de realidad mixta](mixed-reality-capture.md) (MRC), dependiendo de la forma de los auriculares en cuestión. Las aplicaciones que pueden admitir varias cámaras las obtienen al [participar](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) en el [tipo](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) de cámaras que pueden admitir.

## <a name="volume-rendering"></a>Representación de volumen

Al representar volúmenes médicos MRIs o de ingeniería en 3D, a menudo se utilizan técnicas de [representación por volumen](volume-rendering.md) . Estas técnicas pueden ser especialmente interesantes en la realidad mixta, donde los usuarios pueden ver de forma natural dicho volumen desde ángulos clave, simplemente moviendo su principal.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>Resoluciones admitidas en HoloLens (1ª generación)

* El tamaño máximo de la ventanilla es una propiedad de [HolographicDisplay](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay). HoloLens se establece en el tamaño máximo de la ventanilla, que es 720p (1268x720), de forma predeterminada.
* El tamaño de la ventanilla se puede cambiar estableciendo ViewportScaleFactor en HolographicCamera. Este factor de escala está en el intervalo de 0 a 1.
* El tamaño de ventanilla compatible más bajo de HoloLens (1ª generación) es el 50% de 720p, que es 360p (634x360). Se trata de un ViewportScaleFactor de 0,5.
* No se recomienda nada inferior a 540P debido a la degradación visual, pero se puede usar para identificar cuellos de botella en la velocidad de relleno de píxeles.

## <a name="supported-resolutions-on-hololens-2"></a>Resoluciones admitidas en HoloLens 2

* Los tamaños de destino de representación actuales y máximos admitidos son propiedades de la configuración de la [vista](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration). HoloLens 2 se establece en el tamaño máximo de destino de representación, que es 1440x936, de forma predeterminada.
* Las aplicaciones pueden cambiar el tamaño de los búferes de destino de representación llamando al método RequestRenderTargetSize para solicitar un nuevo tamaño de destino de representación. Se elegirá un nuevo tamaño de destino de representación, que cumple o supera el tamaño de destino de presentación solicitado. Esta API cambia el tamaño del búfer de destino de representación, que requiere la reasignación de memoria en la GPU. Las implicaciones de esto incluyen: el tamaño del destino de representación se puede reducir verticalmente para reducir la presión de memoria en la GPU y este método no se debe llamar a alta frecuencia.
* Las aplicaciones todavía pueden cambiar el tamaño de la ventanilla de la misma forma que lo hacían para HoloLens 1. Esto no produce una reasignación de memoria en la GPU, por lo que se puede cambiar con una frecuencia alta, pero no se puede usar para reducir la presión de memoria en la GPU.
* El tamaño de ventanilla compatible más bajo de HoloLens 2 es 634x412. Se trata de un ViewportScaleFactor de aproximadamente 0,44 cuando el tamaño de destino de representación predeterminado está en uso.
* Si se proporciona un tamaño de destino de representación que es menor que el tamaño de ventanilla compatible más bajo, se omitirá el factor de escala de la ventanilla.
* No se recomienda nada inferior a 540P debido a la degradación visual, pero se puede usar para identificar cuellos de botella en la velocidad de relleno de píxeles.



## <a name="see-also"></a>Consulta también
* [Estabilidad de hologramas](hologram-stability.md)
* [Representación en DirectX](rendering-in-directx.md)
