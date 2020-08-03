---
title: Configuración de un nuevo proyecto de Unity para Windows Mixed Reality
description: Instrucciones para configurar un proyecto de Unity para Windows Mixed Reality
author: thetuvix
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto
ms.openlocfilehash: 877bdb803dc69e519a274eedabb8e51fe0197689
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476777"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Configuración de un nuevo proyecto de Unity para Windows Mixed Reality 

## <a name="overview"></a>Información general

Windows Mixed Reality (WMR) es una plataforma de Microsoft introducida como parte del sistema operativo Windows 10. La plataforma WMR permite crear aplicaciones que representan contenido digital en dispositivos de visualización holográfica y VR.

Al configurar para WMR, hay dos rutas que puede tomar. La primera opción es instalar el [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) (MRTK) V2, que configurará automáticamente el entorno de WMR. La segunda opción es cambiar manualmente algunos valores de Unity para empezar a trabajar con WMR. 

> [!NOTE]
> Siempre puede importar MRTK más adelante, por lo que no hay ninguna penalización en primer lugar en la ruta manual.

Si elige la configuración manual de WMR, la configuración que debe cambiar se divide en dos categorías: por proyecto y por escena.

## <a name="per-project-settings"></a>Configuración por proyecto

La primera configuración que debe cambiar para WMR es la plataforma del proyecto: 
1. Seleccionar **archivo > configuración de compilación...**
2. Seleccione **plataforma universal de Windows** en la lista plataforma y haga clic en **cambiar plataforma** .
3. Establecer **SDK** en **universal 10**
4. Establecer el **dispositivo de destino** en **cualquier dispositivo** para admitir auriculares envolventes o cambiar a **HoloLens**
5. Establecer el **tipo de compilación** en **D3D**
6. Establecimiento del **SDK de UWP** en la **versión más reciente instalada**

![Configuración de Unity XR](images/unity-uwp-settings.png)<br>
*Configuración de Unity XR*

Una vez configurada correctamente la plataforma, debe dejar que Unity sepa que la aplicación debe crear una [vista envolvente](app-views.md) en lugar de una vista 2D cuando se exportó:
1. En la ventana **configuración de compilación...** , Abra **configuración del reproductor...**
2. Seleccione la **configuración de plataforma universal de Windows** pestaña y expanda el grupo de **configuración de XR**
3. En la sección **configuración de XR** , active la casilla **compatibilidad con realidad virtual** para agregar la lista de **dispositivos de realidad virtual** .
4. En el grupo de **configuración de XR** , confirme que **"Windows Mixed Reality"** aparece como un dispositivo compatible. (esta opción puede aparecer como **Windows Holographic** en versiones anteriores de Unity)

![Configuración de UWP de Unity](images/xrsettings.png)<br>
*Configuración de Unity XR*

### <a name="updating-the-manifest"></a>Actualización del manifiesto

La aplicación ahora puede controlar la representación holográfica y la entrada espacial. Sin embargo, la aplicación debe declarar las capacidades adecuadas en el manifiesto para aprovechar ciertas funciones. Para encontrar las capacidades de los proyectos, vaya a **configuración del reproductor > configuración de Plataforma universal de Windows > configuración de publicación > funcionalidades**. 

Se recomienda que realice las declaraciones de manifiesto en Unity para incluirlas en todos los proyectos futuros que exporte. Las capacidades aplicables para habilitar las API de Unity usadas con frecuencia para la realidad mixta son:

|  Capacidad  |  API que requieren funcionalidad | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (acceso a mallas de [asignación espacial](spatial-mapping.md) en HoloLens) &mdash; *no se necesita ninguna funcionalidad para el seguimiento espacial general de los auriculares* | 
|  Web  |  Fotocaptura y videocaptura | 
|  PicturesLibrary/VideosLibrary  |  Fotocaptura o videocaptura, respectivamente (al almacenar el contenido capturado) | 
|  Micrófono  |  VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (y para usar el generador de perfiles de Unity) | 

### <a name="quality-settings"></a>Configuración de calidad

HoloLens tiene una GPU de clase móvil. Si su aplicación tiene como destino HoloLens, querrá que la configuración de calidad de la aplicación se ajuste para obtener un rendimiento más rápido para asegurarse de que mantiene la velocidad de fotogramas completa:
1. Seleccione **editar > configuración del proyecto > calidad**
2. Seleccione la **lista desplegable** en el logotipo de la **tienda Windows** y seleccione **muy baja**. Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna Windows Store (Tienda Windows) y la fila **Very Low** (Muy baja) estén en verde.

![Configuración de calidad de Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Configuración de calidad de Unity*

## <a name="per-scene-settings"></a>Configuración por escena

### <a name="unity-camera-settings"></a>Configuración de la cámara de Unity

Con la **realidad virtual compatible** activada, el componente de [cámara Unity](camera-in-unity.md) controla el [seguimiento de los cabezales y la representación Stereoscopic](rendering.md). Esto significa que no es necesario reemplazar el objeto de cámara principal por una cámara personalizada.

Si su aplicación tiene como destino HoloLens específicamente, debe cambiar algunas opciones de configuración para optimizar las pantallas transparentes del dispositivo. Esta configuración permite que el contenido holográfica se muestre a través del mundo físico:
1. En la **jerarquía**, seleccione la **cámara principal** .
2. En el panel **Inspector** , establezca la **posición** de la transformación en **0, 0, 0** para que la ubicación del encabezado del usuario se inicie en el origen del mundo Unity.
3. Cambie las **marcas de borrado** a **color sólido**.
4. Cambie el color de **fondo** a **RGBA 0, 0, 0 y 0**. Los negros se representan como transparentes en HoloLens.
5. Cambiar los **planos de recorte, cerca** de [HoloLens recomendado](camera-in-unity.md#clip-planes) 0,85 (metros).

![Configuración de la cámara de Unity](images/Unitycamerasettings.png)<br>
*Configuración de la cámara de Unity*

> [!IMPORTANT]
> Si elimina y crea una nueva cámara, asegúrese de que la nueva cámara esté etiquetada como **MainCamera**.

## <a name="see-also"></a>Consulta también
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Introducción al desarrollo de Unity](unity-development-overview.md)
