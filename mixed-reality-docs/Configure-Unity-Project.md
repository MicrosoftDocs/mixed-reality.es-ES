---
title: Configurar un nuevo proyecto de Unity para Windows Mixed Reality
description: configurar el proyecto de Unity sin MRTK
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixto en realidad, desarrollo, introducción, nuevo proyecto
ms.openlocfilehash: 4ee81eca25109da428d7b3addf59e102ddc5c5cf
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993539"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configurar un nuevo proyecto de Unity para Windows Mixed Reality 

(omita si ya ha importado MRTK v2 en el proyecto de Unity)

Si desea crear un nuevo proyecto de Unity sin importar el Kit de herramientas de realidad mixta, hay un pequeño conjunto de configuración de Unity, deberá cambiar manualmente para Windows Mixed Reality, dividida en dos categorías: por proyecto y por la escena.

## <a name="per-project-settings"></a>Configuración por proyecto

Para tener como destino Windows Mixed Reality, primero debe configurar su proyecto de Unity para exportar como una aplicación plataforma Universal de Windows:
1. Seleccione **archivo > configuración de compilación...**
2. Seleccione **Universal Windows Platform** en la plataforma de lista y haga clic en **Cambiar plataforma**
3. Establecer **SDK** a **10 Universal**
4. Establecer **dispositivo de destino** a **cualquier dispositivo** para admitir inmersivos o cambie a **HoloLens**
5. Establecer **tipo de compilación** a **D3D**
6. Establecer **UWP SDK** a **instalada más reciente**

A continuación, es necesario informar a Unity que se debe crear la aplicación que estamos intentando exportar una [vista envolvente](app-views.md) en lugar de una vista 2D. Para hacerlo habilitando "Realidad Virtual admite":
1. Desde el **configuración de compilación...**  ventana abierta **configuración del Reproductor...**
2. Seleccione el **configuración de plataforma Universal de Windows** ficha
3. Expanda el **configuración XR** grupo
4. En el **XR configuración** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar el **dispositivos de realidad Virtual** lista.
5. En el **XR configuración** grupo, confirme que **"Windows Mixed Reality"** aparece como un dispositivo compatible. (Esto puede aparecer como "Windows Holographic" en versiones anteriores de Unity)

Ahora puede hacer la aplicación básica representación holográfica y entrada espacial. Para ir más allá y aprovechar las ventajas de cierta funcionalidad, la aplicación debe declarar las capacidades adecuadas en su manifiesto. Las declaraciones del manifiesto se pueden realizar en Unity, por lo que se incluyen en cada exportación proyecto posterior. La configuración se encuentran en **configuración del Reproductor > configuración de plataforma Universal de Windows > configuración de publicación > capacidades**. Las capacidades para habilitar las API de Unity usados para Mixed Reality aplicables son:

|  Capacidad  |  API que requieren la capacidad | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acceso a [asignación espacial](spatial-mapping.md) mallas en HoloLens)&mdash;*ninguna funcionalidad necesaria para seguimiento espacial general de los auriculares* | 
|  WebCam  |  PhotoCapture y VideoCapture | 
|  PicturesLibrary o VideosLibrary  |  PhotoCapture o VideoCapture, respectivamente (al almacenar el contenido capturado) | 
|  Micrófono  |  VideoCapture (cuando la captura de audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (y utilizar el Profiler de Unity) | 

**Configuración de calidad de Unity**

![Configuración de calidad de Unity](images/unityqualitysettings-350px.png)<br>
*Configuración de calidad de Unity*

HoloLens tiene una GPU de la clase mobile. Si la aplicación está destinada a HoloLens, querrá la configuración de calidad optimizada para rendimiento más rápido para asegurarse de que mantenemos la velocidad de fotogramas completa:
1. Seleccione **Editar > configuración del proyecto > calidad**
2. Seleccione el **desplegable** bajo el **Windows Store** logotipo y seleccione **Very Low**. Sabrá que la configuración se aplique correctamente cuando la casilla de la columna de Windows Store y **Very Low** fila es verde.

## <a name="per-scene-settings"></a>Configuración por la escena

**Configuración de la cámara de Unity**

![Configuración de la cámara de Unity](images/Unitycamerasettings.png)<br>
*Configuración de la cámara de Unity*

Una vez que habilite la casilla "Compatible de realidad Virtual", la [Unity cámara](camera-in-unity.md) identificadores de componente [head seguimiento y la representación estereoscópica](rendering.md). No hay ninguna necesidad reemplazarla con una cámara personalizada para hacerlo.

Si la aplicación está destinada específicamente a HoloLens, hay algunas opciones de configuración que deben cambiarse para optimizar la muestra de transparente del dispositivo, por lo que se mostrará la aplicación a través en el mundo físico:
1. En el **jerarquía**, seleccione el **cámara principal**
2. En el **Inspector** del panel, establezca la transformación **posición** a **0, 0, 0** para que la ubicación de la cabeza a los usuarios que se inicie en el origen del mundo de Unity.
3. Cambio **borrar las marcas de** a **Color sólido**.
4. Cambiar el **en segundo plano** al color **RGBA 0,0,0,0**. Negro se representa como transparente en HoloLens.
5. Cambio **cerca de recorte planos -** a la [HoloLens recomendadas](camera-in-unity.md#clip-planes) 0,85 (metros).

Si elimina y creación de una cámara nueva, asegúrese de que la cámara es **etiquetada** como **MainCamera**.


## <a name="see-also"></a>Vea también
* [La realidad mixta Toolkit v2](mrtk-getting-started.md)
* [Introducción al desarrollo de Unity](unity-development-overview.md)
