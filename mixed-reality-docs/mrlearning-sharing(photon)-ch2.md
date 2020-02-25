---
title: 'Tutoriales de funcionalidades para varios usuarios: 2. Preparar Unity para el desarrollo'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2bcec7e70949186c6e711120c36ee8649c006ec7
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553851"
---
# <a name="2-getting-unity-ready-for-development"></a>2. obtener Unity listo para el desarrollo

En este tutorial, obtendrá información sobre cómo preparar y configurar Unity para el desarrollo de aplicaciones, incluida la importación del kit de herramientas de realidad mixta, la configuración de las opciones de compilación y la preparación de la escena.

## <a name="objectives"></a>Objetivos

* Configuración de Unity para el desarrollo de aplicaciones
* Importación de Mixed Reality Toolkit
* Preparación de la escena del proyecto

## <a name="instructions"></a>Instrucciones

1. Para descargar y guardar el paquete Mixed Reality Toolkit Foundation Unity, haga clic [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

2. En Unity, haga clic en el menú activos y seleccione Importar paquete y, a continuación, haga clic en paquete personalizado.

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Seleccione el paquete de Unity que acaba de descargar del vínculo proporcionado en el paso 1. Una vez que aparezca la ventana emergente importar en Unity, haga clic en el botón importar para empezar a importar el MRTK. Esto puede tardar varios minutos.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >El paquete descargado se encuentra en la carpeta local, donde se guardó el archivo. La imagen anterior no indica dónde encontrará el paquete.

    Una vez importado el paquete, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK). Si no es así, ábralo seleccionando el kit de herramientas de realidad mixta > Utilidades > configurar el proyecto de Unity en el menú de Unity.

    En la ventana Configurator del proyecto de MRTK, expanda la sección modificar configuraciones, desactive la casilla habilitar MSBuild para Unity, asegúrese de que todas las demás opciones están seleccionadas y haga clic en el botón aplicar para aplicar la configuración.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > Es posible que MSBuild para Unity no admita todos los SDK que vas a usar y puede ser difícil de deshabilitar una vez que se haya habilitado. Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.
    
4. Cree una nueva escena. Para ello, haga clic en archivo y seleccione nueva escena ". Guárdelo como HLSharedProjectMain.

5. En el kit de herramientas de realidad mixta, haga clic en Agregar a escena y configurar.

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una vez que haya finalizado, seleccione el kit de herramientas de realidad mixta (MRTK) de la jerarquía. En el panel Inspector, cambie el perfil de configuración de MRTK a DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Seleccione el kit de herramientas de realidad mixta (MRTK) de la jerarquía. En el panel Inspector, busque el script Mixed Reality Toolkit y presione el botón "copiar & personalizar" como se muestra en la ilustración siguiente.  Después de esto, aparecerá un pop en el menú emergente.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Desplácese hacia abajo y desactive habilitar el sistema de diagnósticos si desea ocultar la ventana de diagnóstico. Se recomienda mantener la ventana de diagnósticos habilitada durante el desarrollo de la aplicación para supervisar el rendimiento y, a continuación, deshabilitarla durante las demostraciones de producción o de aplicación. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Para abrir la configuración de compilación, presione Control + Mayús + B o vaya a archivo-> configuración de compilación. Tenga en cuenta que el programa está establecido actualmente en la plataforma independiente PC, Mac y Linux. Para el desarrollo de HoloLens 2, establezca la plataforma que se va a Plataforma universal de Windows. Selecciónelo y haga clic en switch Platform (cambiar plataforma).

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Una vez que haya finalizado, haga clic en el cuadro denominado agregar escenas abiertas. Ahora, vaya al panel Inspector y asegúrese de que esté activada la casilla situada a la derecha de realidad virtual (como se muestra en la imagen siguiente). Asegúrese también de que la casilla situada junto a Scenes/HLSharedProjectMain también está activada, como se muestra en la imagen siguiente.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. En la sección configuración de publicación del panel Inspector, desplácese hacia abajo hasta capacidades y asegúrese de que las siguientes casillas están marcadas como:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importe los paquetes personalizados enumerados:

    * [AzureSpatialAnchors. unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)
    * [MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.3.0.2. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriales. assets. AzureSpatialAnchors. 2.3.0.0. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK. HoloLens2. Unity. tutoriales. assets. MultiUserCapabilities. 2.1.0.1. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Para obtener un recordatorio sobre cómo configurar un proyecto de Unity para los anclajes espaciales de Azure, puede consultar el tutorial Introducción a los [anclajes espaciales de Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) , que forma parte de la serie de tutoriales de los [delimitadores espaciales de Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .


13. En el panel Proyecto, vaya a la carpeta Prefabs. En los pasos siguientes, se implementarán algunas Prefabs en la escena. En la carpeta Prefabs, haga clic y arrastre la ventana de depuración recurso prefabricado a la jerarquía. Una vez finalizado, guarde el proyecto haciendo clic en archivo, luego en guardar o presione Control + S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Es posible que observe que aparece una ventana emergente al hacer clic en el recurso prefabricado, donde se le pregunta sobre TMP Essentials. Haga clic en importar TMP Essentials según sea necesario. Si aparece esta ventana emergente, es posible que tenga que eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Enhorabuena

El proyecto de Unity ya está listo para Photon. En los tutoriales venideros, se basará en esta escena y nuestro proyecto de Unity en una experiencia completa compartida.

[Siguiente tutorial: 3. conectar varios usuarios](mrlearning-sharing(photon)-ch3.md)
