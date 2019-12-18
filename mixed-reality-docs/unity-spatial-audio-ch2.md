---
title: 'Tutoriales de audio espacial: 2. Sonidos de interacción del botón de espacialización'
description: Agregue un botón al proyecto y Spatial los sonidos de interacción del botón.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182782"
---
# <a name="spatializing-button-interaction-sounds"></a>Sonidos de interacción del botón de espacialización

## <a name="objectives"></a>Objetivos
En este segundo capítulo del módulo de audio espacial de los tutoriales de HoloLens 2, hará lo siguiente:
* Adición de un botón
* Spatial los sonidos del clic del botón

## <a name="add-a-button"></a>Adición de un botón
En el panel **proyecto** , seleccione **recursos** y escriba "PressableButtonHoloLens2" en la barra de búsqueda:

![Botón recurso prefabricado en activos](images/spatial-audio/button-prefab-in-assets.png)

El botón recurso prefabricado es la entrada representada por un icono azul, en lugar de un icono blanco. Arrastre recurso prefabricado con el nombre **PressableButtonHoloLens2** al panel **jerarquía** . En el panel **Inspector** del nuevo botón, establezca la propiedad **Position** en (0,-0,4, 2) para que aparezca delante del usuario cuando se inicie la aplicación. El componente de **transformación** del botón tendrá el siguiente aspecto:

![Transformación de botón](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Comentario del botón de Spatial
En este paso, creará un espacial de los comentarios de audio para el botón. Para obtener sugerencias de diseño relacionadas, consulte [diseño de sonido espacial](spatial-sound-design.md). 

El panel **mezclador de audio** permite definir destinos, denominados grupos de **mezclador**, para la reproducción de audio de componentes de origen de **audio** . 
* Abra el panel del **mezclador de audio** en la barra de menús con el **mezclador de audio > Audio-> de Windows**
* Para crear un **mezclador** , haga clic en el "+" junto a **mixers**. El nuevo mezclador incluirá un **Grupo** predeterminado denominado **maestro**.

El panel del **mezclador** tendrá ahora el siguiente aspecto:

![Panel de mezclador con el primer mezclador](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> Hasta que se habilita la reverberación en el [capítulo 5](unity-spatial-audio-ch5.md), el medidor de volumen del mezclador no muestra la actividad de los sonidos que se reproducen a través de Microsoft Spatializer

Haga clic en **PressableButtonHoloLens2** en el panel **jerarquía** . En el panel **Inspector** :
1. Buscar el componente de **origen de audio**
2. En la propiedad **salida** , haga clic en el selector y elija el mezclador.
3. Active la casilla **Spatial**
4. Mueva el control deslizante de **mezcla espacial** a 3D (1).

> [!NOTE]
> En las versiones de Unity anteriores a 2019, la casilla ' Spatial ' está en la parte inferior del panel del **Inspector** para el **origen de audio**.

Después de estos cambios, el componente de **origen de audio** de su **PressableButtonHoloLens2** tendrá el siguiente aspecto:

![Origen de audio de botón](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> Si mueve la **mezcla espacial** a 1 (3D) sin activar la casilla **Spatial** , Unity usará su spatializer de movimiento panorámico, en lugar de **spatializer de Microsoft** con HRTFs.

## <a name="adjust-the-volume-curve"></a>Ajustar la curva del volumen
De forma predeterminada, Unity atenúa los sonidos espaciales a medida que se alejan del agente de escucha. Cuando se aplica esta atenuación a los sonidos de interacción, la interfaz puede resultar más difícil de usar.

Para deshabilitar esta atenuación, ajuste la curva del **volumen** . En el componente **origen de audio** del panel **Inspector** de **PressableButtonHoloLens2**, hay una sección denominada configuración de **sonido 3D**. En esa sección:
1. Establezca la propiedad **Volume rolloff** en lineal.
2. Arrastre el punto de conexión en la curva de **volumen** (la curva roja) desde ' 0 ' en el eje y hasta ' 1 '
3. Para ajustar la forma de la curva de **volumen** para que sea plana, arrastre el control de forma de curva blanca para que sea paralelo al eje X.

Después de estos cambios, la sección **configuración de sonido 3D** de las propiedades de **origen de audio** del **PressableButtonHoloLens2** tendrá el siguiente aspecto:

![Configuración de sonido 3D del botón](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a>Pasos siguientes

Pruebe la aplicación en HoloLens 2 o en el editor de Unity. En la aplicación, puede tocar el botón y oír los sonidos de interacción del botón espacial.

Al realizar pruebas en el editor de Unity, presione la barra espaciadora y desplácese con la rueda de desplazamiento para activar la simulación de mano. Para obtener más información, consulte la [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).

Continúe con el [capítulo 3](unity-spatial-audio-ch3.md) para agregar un vídeo a la aplicación y Spatial el audio del vídeo.

