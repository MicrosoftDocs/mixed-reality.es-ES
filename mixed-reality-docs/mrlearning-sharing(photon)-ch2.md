---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327719"
---
# <a name="getting-unity-ready-for-development"></a>**Cómo prepararse para el desarrollo de Unity** 

En esta lección, se obtendrá información sobre cómo preparar y configurar Unity para el desarrollo de aplicaciones, como importar el Kit de herramientas de realidad mixta, configuración de generación y preparación de la escena.

Objetivos:

- Configuración de Unity para desarrollo de aplicaciones

- Importación de Mixed Reality Toolkit

- Preparación de la escena de proyecto

### <a name="instructions"></a>Instrucciones

1. Descargue y guarde el paquete de unity del Kit de herramientas de realidad mixta haciendo [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)
2. En Unity, haga clic en el menú de recursos y seleccione "Importar paquete" y luego haga clic en "Paquete personalizado".

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Seleccione el paquete de Unity que acaba de descargar desde el vínculo indicado en el paso 1. Una vez que aparece la ventana emergente de importación en Unity, haga clic en el botón Importar para comenzar a importar. Importar el MRTK puede tardar varios minutos.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Nota: El paquete descargado estará en la carpeta local donde ha guardado el archivo. La imagen anterior no describe donde encontrará el paquete.

4. Cree una nueva escena (Esto se puede realizar haciendo clic en "file" y seleccione "nueva escena"). Guarde la escena como "HLSharedProjectMain."

> Nota: puede recibir un mensaje emergente que tiene un aspecto similar a la siguiente imagen. Por ahora, simplemente haga clic en "no".
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. En "Mixed Reality Toolkit", haga clic en "Agregar a la escena y configurar".

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una vez completado, un nuevo archivo de configuración aparecerá, lo que le ofrece la opción de personalizar el perfil. Haga clic en "copiar y personalizar".

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. Desplácese hacia abajo y desactive la opción "Habilitar sistema de diagnóstico" Si desea ocultar la ventana de diagnóstico. Se recomienda mantener la ventana diagnóstico habilitado durante el desarrollo de aplicaciones para supervisar el rendimiento y, si lo deshabilitan en las demostraciones de producción o la aplicación.

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. Abra la configuración de compilación, presione control + MAYÚS + B o vaya a archivo > configuración de compilación. Tenga en cuenta que el programa está establecido actualmente en la plataforma "PC, Mac y Linux independiente". Para el desarrollo de HoloLens 2, establezca la plataforma como "Plataforma Universal de Windows". Selecciónelo y haga clic en "Cambiar plataforma".

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. Una vez que haya terminado, haga clic en el cuadro que dice "Agregar escenas abiertos". Ahora, vaya al panel de inspector y asegúrese de que la casilla situada a la derecha de "la realidad virtual admitida" (como se muestra en la imagen siguiente) está activada. También asegúrese de que también se activa la casilla de verificación situada junto a "escenas/HLSharedProjectMain", tal como se muestra en la imagen siguiente.

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. En la "configuración de publicación" sección en el panel inspector, desplácese a "Capacidades" y asegúrese de que se marcan las siguientes casillas:
    - cliente de Internet
       
       - servidor de cliente de Internet
       
       - servidor de cliente de red privada
   
       - camera/webcam

       - Micrófono
   
   11. Importe el paquete personalizado denominado "Lesson2", que puede descargarse aquí. TODO: Proporcione el vínculo al paquete de recursos.
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. Ahora, en el panel de proyecto, vaya a la carpeta "prefabricados", puesto que en los pasos siguientes, va a implementar unos prefabricados en la escena. En la carpeta "prefabricados", haga clic y arrastre el prefabricado verá, "DebugWindow" en la jerarquía. Una vez terminado, guarde el proyecto (haga clic en archivo, a continuación, guardar, o presione CTRL + S)
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > Nota: Puede que observe un elemento emergente aparece al hacer clic en el prefabricado verá, que le pide sobre Essentials TMP. Haga clic en "Importar TMP Essentials" como será necesaria. Si este elemento emergente aparece, es posible que deba eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Enhorabuena

Ahora está listo para Photon el proyecto de Unity. En las próximas lecciones, creamos esta escena y nuestro proyecto de Unity hacia una experiencia completa compartida.

[Siguiente lección: Sharing(Photon) lección 3](mrlearning-sharing(photon)-ch3.md)

