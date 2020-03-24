---
title: 'Tutoriales sobre las funcionalidades multiusuario: 2. Preparación de Unity para desarrollo'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031239"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Preparación de Unity para el desarrollo

En este tutorial, aprenderás a preparar y configurar Unity para el desarrollo de aplicaciones, incluida la importación de Mixed Reality Toolkit, la configuración de las opciones de compilación y la preparación de la escena.

## <a name="objectives"></a>Objetivos

* Configurar Unity para el desarrollo de aplicaciones
* Importación de Mixed Reality Toolkit
* Preparar la escena del proyecto

## <a name="instructions"></a>Instrucciones

1. Haz clic [aquí](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) para descargar el paquete básico de Unity de Mixed Reality Toolkit.

2. En Unity, haz clic en el menú Assets (Recursos) y selecciona Import Package (Importar paquete). A continuación, haz clic en Custom Package (Paquete personalizado).

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Selecciona el paquete de Unity que acabas de descargar del vínculo proporcionado en el paso 1. Cuando aparezca la ventana emergente de importación en Unity, haz clic en el botón Importar para empezar a importar el MRTK. Esto puede tardar varios minutos.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >El paquete descargado está en la carpeta local, donde has guardado el archivo. La imagen anterior no indica dónde encontrarás el paquete.

    Una vez importado el paquete, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK). Si no aparece, se puede abrir seleccionando la opción Mixed Reality Toolkit > Utilities > Configure Unity Project (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) en el menú de Unity.

    En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), expande la sección Modify Configurations (Modificar configuraciones), desactiva la casilla Enable MSBuild for Unity (Habilitar MSBuild para Unity), asegúrate de que todas las demás opciones están seleccionadas y haz clic en el botón Apply (Aplicar) para aplicar la configuración.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > Es posible que MSBuild para Unity no admita todos los SDK que vas a usar y puede ser difícil de deshabilitar una vez que se haya habilitado. Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.
    
4. Crea una escena nueva. Para hacerlo, haz clic en File (Archivo) y selecciona New Scene (Nueva escena). Guárdala como HLSharedProjectMain.

5. En Mixed Reality Toolkit, haz clic en Add to Scene (Agregar a escena) y Configure (Configurar).

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Al acabar, selecciona Mixed-Reality Toolkit (MRTK) en la jerarquía. En el panel del inspector, cambia el perfil de configuración de MRTK a DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Selecciona Mixed-Reality Toolkit (MRTK) en la jerarquía. En el panel del inspector, busca Mixed Reality Toolkit Script (Script de Mixed Reality Toolkit) y selecciona el botón "Copy & Customize" (Copiar y personalizar) como se muestra en la ilustración siguiente.  Después de esto, aparecerá un elemento emergente. Selecciona la opción Clone (Clonar) en el menú emergente.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Desplázate hacia abajo y desactiva Enable Diagnostics system (Habilitar el sistema de diagnóstico) si quieres ocultar la ventana de diagnóstico. Es recomendable mantener la ventana de diagnóstico habilitada durante el desarrollo de la aplicación para supervisar el rendimiento y, a continuación, deshabilitarla durante las demostraciones de producción o de la aplicación. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Para abrir la configuración de compilación, presiona Control + Mayús + B o ve a File -> Build Settings (Archivo -> Configuración de compilación). Ten en cuenta, actualmente, que el programa está definido en la plataforma independiente para PC, Mac y Linux. Para el desarrollo de HoloLens 2, define la Plataforma universal de Windows como plataforma. Selecciónala y haz clic en Switch Platform (Cambiar plataforma).

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Al finalizar, haz clic en el cuadro denominado Add Open Scenes (Agregar escenas abiertas). Ahora, ve al panel Inspector y asegúrate de que esté activada la casilla situada a la derecha de Virtual Reality Supported (Realidad virtual compatible), como se muestra en la imagen siguiente. Asegúrate también de que la casilla situada junto a Scenes (Escenas)/HLSharedProjectMain también esté activada, como se muestra en la imagen siguiente.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. En la sección Publishing Settings (Configuración de publicación) del panel Inspector, desplázate hacia abajo hasta Capabilities (Funcionalidades) y asegúrate de que las siguientes casillas estén marcadas:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importa los paquetes personalizados que se muestran:

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Para obtener un recordatorio sobre cómo configurar un proyecto de Unity para Azure Spatial Anchors, puedes consultar el tutorial [Introducción a Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1), que forma parte de la serie de tutoriales de [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).


13. En el panel Proyecto, ve a la carpeta Prefabs. En los pasos siguientes, se implementarán algunos objetos prefabricados a la escena. En la carpeta Prefabs, haz clic y arrastra el objeto prefabricado DebugWindow a la jerarquía. Al acabar, guarda el proyecto. Para hacerlo, haz clic en File (Archivo) y Save (Guardar) o presiona Control+S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Puede que observes que aparece una ventana emergente al hacer clic en el objeto prefabricado, que te preguntará acerca de TMP Essentials. Haz clic en Import TMP Essentials (Importar TMP Essentials), ya que se necesita. Si aparece esta ventana emergente, es posible que tengas que eliminar el objeto prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Enhorabuena

El proyecto de Unity ya está listo para Photon. En los próximos tutoriales, nos basaremos en esta escena y nuestro proyecto de Unity para lograr una experiencia completa compartida.

[Tutorial siguiente: 3. Conexión de varios usuarios](mrlearning-sharing(photon)-ch3.md)
