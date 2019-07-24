---
title: Configuración de un nuevo proyecto de Unity para Windows Mixed Reality
description: configuración de un proyecto de Unity sin MRTK
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto
ms.openlocfilehash: 68dded9d0fc9e861bdda56c4954d72ddafafa686
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326092"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configuración de un nuevo proyecto de Unity para Windows Mixed Reality 

(omitir si ya ha importado MRTK V2 en el proyecto de Unity)

Si desea crear un nuevo proyecto de Unity sin importar el kit de herramientas de realidad mixta, hay un pequeño conjunto de opciones de Unity que debe cambiar manualmente para Windows Mixed Reality, dividido en dos categorías: por proyecto y por escena.

## <a name="per-project-settings"></a>Configuración por proyecto

Para tener como destino Windows Mixed Reality, primero debe configurar el proyecto de Unity para que lo exporte como una aplicación Plataforma universal de Windows: 
1. Seleccionar **archivo > configuración de compilación...**
2. Seleccione **plataforma universal de Windows** en la lista plataforma y haga clic en **cambiar plataforma** .
3. Establecer **SDK** en **universal 10**
4. Establecer el **dispositivo de destino** en **cualquier dispositivo** para admitir auriculares envolventes o cambiar a **HoloLens**
5. Establecer el **tipo de compilación** en **D3D**
6. Establecimiento del **SDK de UWP** en la **versión más reciente instalada**

A continuación, necesitamos que Unity sepa que la aplicación que se está intentando exportar debe crear una [vista envolvente](app-views.md) en lugar de una vista 2D. Lo hacemos habilitando "realidad virtual admitida":
1. En la ventana **configuración de compilación...** , Abra **configuración del reproductor...**
2. Seleccione la **configuración de plataforma universal de Windows** pestaña
3. Expandir el grupo de **configuración de XR**
4. En la sección **configuración de XR** , active la casilla **compatibilidad con realidad virtual** para agregar la lista de **dispositivos de realidad virtual** .
5. En el grupo de **configuración de XR** , confirme que **"Windows Mixed Reality"** aparece como un dispositivo compatible. (esto puede aparecer como "Windows Holographic" en versiones anteriores de Unity)

![Configuración de calidad de Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configuración de Unity XR*

La aplicación ahora puede realizar la representación básica holográfica y la entrada espacial. Para seguir sacando provecho de ciertas funciones, la aplicación debe declarar las capacidades adecuadas en su manifiesto. Las declaraciones de manifiesto se pueden realizar en Unity para que se incluyan en cada exportación de proyecto subsiguiente. La configuración se encuentra en **configuración del reproductor > configuración de Plataforma universal de Windows > configuración de publicación > funcionalidades**. Las funcionalidades aplicables para habilitar las API de Unity usadas con frecuencia para la realidad mixta son:

|  Capacidad  |  API que requieren funcionalidad | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acceso a mallas de [asignación espacial](spatial-mapping.md) en HoloLens&mdash;)*no se necesita ninguna funcionalidad para el seguimiento espacial general de los auriculares* | 
|  Web  |  Fotocaptura y videocaptura | 
|  PicturesLibrary/VideosLibrary  |  Fotocaptura o videocaptura, respectivamente (al almacenar el contenido capturado) | 
|  Micrófono  |  VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (y para usar el generador de perfiles de Unity) | 

**Configuración de calidad de Unity**

![Configuración de calidad de Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configuración de calidad de Unity*

HoloLens tiene una GPU de clase móvil. Si la aplicación está destinada a HoloLens, querrá que la configuración de calidad esté optimizada para obtener un rendimiento más rápido para asegurarse de que se mantiene la velocidad de fotogramas completa:
1. Seleccione **editar > configuración del proyecto > calidad**
2. Seleccione la **lista desplegable** en el logotipo de la **tienda Windows** y seleccione **muy baja**. Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna tienda Windows y la fila **muy baja** es verde.

## <a name="per-scene-settings"></a>Configuración por escena

**Configuración de la cámara de Unity**

![Configuración de la cámara de Unity](images/Unitycamerasettings.png)<br>
*Configuración de la cámara de Unity*

Una vez habilitada la casilla "se admite Virtual Reality", el componente de [cámara Unity](camera-in-unity.md) controla el [seguimiento de los cabezales y la representación Stereoscopic](rendering.md). No es necesario reemplazarlo por una cámara personalizada para hacerlo.

Si su aplicación tiene como destino HoloLens específicamente, hay algunas opciones de configuración que deben cambiarse para optimizar las pantallas transparentes del dispositivo, por lo que la aplicación se mostrará a través del mundo físico:
1. En la **jerarquía**, seleccione la **cámara principal** .
2. En el panel **Inspector** , establezca la **posición** de la transformación en **0, 0, 0** para que la ubicación del encabezado de los usuarios se inicie en el origen del mundo de Unity.
3. Cambie las **marcas** de borrado a **color sólido**.
4. Cambie el color de **fondo** a **RGBA 0, 0, 0 y 0**. Los negros se representan como transparentes en HoloLens.
5. Cambiar los **planos de recorte, cerca** de [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

Si elimina y crea una nueva cámara, asegúrese de que la cámara esté **etiquetada** como **MainCamera**.


## <a name="see-also"></a>Vea también
* [Kit de herramientas de realidad mixta V2](mrtk-getting-started.md)
* [Introducción al desarrollo de Unity](unity-development-overview.md)
