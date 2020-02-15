---
title: 'Tutoriales de anclaje espacial de Azure: 2. Guardar, recuperar y compartir anclajes espaciales de Azure'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250757"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. guardar, recuperar y compartir anclajes espaciales de Azure

En este tutorial, obtendrá información sobre cómo guardar los anclajes espaciales de Azure en varias sesiones de la aplicación si guarda el identificador de delimitador en el almacenamiento de HoloLens 2. También aprenderá a compartir este identificador de delimitador con otros dispositivos para una alineación de delimitador de varios dispositivos.

## <a name="objectives"></a>Objetivos

* Obtenga información acerca de cómo guardar y recuperar los identificadores de delimitador espacial de Azure en el disco local de HoloLens 2 para la persistencia entre sesiones de aplicación
* Obtenga información sobre cómo compartir los identificadores de delimitador espacial de Azure entre los usuarios en un escenario de varios dispositivos

## <a name="preparing-the-scene"></a>Preparación de la escena

En la ventana del proyecto, vaya a **activos** > **MRTK. Tutoriales. AzureSpatialAnchors** > carpeta **Prefabs** Mientras mantiene presionado el botón CTRL, haga clic en **ButtonParent_SaveAnchorId** y **ButtonParent_ShareAnchorId** para seleccionar los dos Prefabs y, a continuación, arrástrelos a la ventana de la jerarquía para agregarlos a la escena:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Persistencia de los delimitadores de Azure entre sesiones de aplicación: guardar el ID. de delimitador en el disco
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

En esta sección, aprenderá a guardar y recuperar el identificador de delimitador de Azure en el disco local de HoloLens 2. Esto le permitirá consultar Azure para el mismo identificador de delimitador entre distintas sesiones de aplicación, lo que permite colocar los hologramas anclados en la misma ubicación que en la sesión de aplicación anterior.

En la ventana jerarquía, expanda el objeto **ButtonParent_SaveAnchorId** que contiene dos botones, un botón para guardar el identificador de delimitador de Azure en el almacenamiento de HoloLens 2 y otro para recuperar el identificador guardado del disco:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Siga los mismos pasos que en la [configuración de los botones para que funcionen las](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instrucciones de la escena del tutorial anterior para configurar el componente del botón que se ha **presionado hololens Lens 2 (Script)** y el componente **interactuable (Script)** en cada uno de los dos botones:

* Para el objeto **SaveAzureAnchorIdToDisk** , asigne la función AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Para el objeto **GetAzureAnchorIdFromDisk** , asigne la función AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Si compila la aplicación actualizada en HoloLens, ahora puede conservar los anclajes espaciales de Azure entre las sesiones de la aplicación si guarda el identificador de delimitador de Azure. Para probarlo, puede seguir estos pasos:

1. Mueva la experiencia del selector de Rocket a la ubicación deseada.
2. Inicie sesión de Azure.
3. Cree un delimitador de Azure (crea delimitadores en la ubicación de la experiencia del selector de Rocket).
4. Guarde el identificador de delimitador de Azure en el disco.
5. Reinicie la aplicación.
6. Obtenga el delimitador de Azure del disco (carga el ID. de delimitador que acaba de guardar).
7. Inicie sesión de Azure.
8. Busque el anclaje de Azure (coloca la experiencia del selector de Rocket en la ubicación del paso 3).

## <a name="share-azure-anchors-between-multiple-devices"></a>Compartir anclajes de Azure entre varios dispositivos

En esta sección, obtendrá información sobre cómo compartir el identificador de delimitador de Azure entre varios dispositivos. Esto permitirá que varios dispositivos consulten a Azure para el mismo identificador de delimitador, lo que permite alinear los hologramas delimitados espacialmente. La alineación espacial, es decir, ver los mismos hologramas en la misma ubicación física entre varios dispositivos, es fundamental para las experiencias compartidas locales en HoloLens 2.

Hay muchas maneras de transferir los identificadores de delimitador de Azure entre dispositivos, incluidos los métodos descritos en la serie de [tutoriales de funcionalidades para varios usuarios](mrlearning-sharing(photon)-ch1.md) . En este ejemplo, usará un servicio web simple para cargar y descargar los ID. de delimitador entre dispositivos.

En la ventana jerarquía, expanda el objeto **ButtonParent_ShareAnchorId** que contiene dos botones; un botón para cargar el identificador de delimitador de Azure en el servidor Web y otro para descargar el identificador del servidor Web:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Siga los mismos pasos que en la [configuración de los botones para que funcionen las](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instrucciones de la escena del tutorial anterior para configurar el componente del botón que se ha **presionado hololens Lens 2 (Script)** y el componente **interactuable (Script)** en cada uno de los dos botones:

* Para el objeto **ShareAzureAnchorIdToNetwork** , asigne la función AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Para el objeto **GetAzureAnchorIdFromNetwork** , asigne la función AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Si compila la aplicación actualizada en dos dispositivos HoloLens, ahora puede lograr la alineación espacial entre ellos compartiendo el identificador de delimitador de Azure. Para probarlo, puede seguir estos pasos:

1. En el dispositivo de HoloLens 1: mueva la experiencia del selector de Rocket a la ubicación deseada.
2. En el dispositivo de HoloLens 1: inicie sesión de Azure.
3. En el dispositivo de HoloLens 1: creación de un delimitador de Azure (crea delimitadores en la ubicación de la experiencia del selector de Rocket).
4. En el dispositivo de HoloLens 1: compartir el ID. de delimitador de Azure con la red.
5. En el dispositivo de HoloLens 2: reinicie la aplicación.
6. En el dispositivo de HoloLens 2: obtener el identificador de delimitador compartido de la red (captura el identificador de delimitador que se acaba de compartir desde el dispositivo de HoloLens 1).
7. En el dispositivo de HoloLens 2: iniciar sesión de Azure.
8. En el dispositivo de HoloLens 2: Busque el anclaje de Azure (coloca la experiencia del selector de Rocket en la ubicación del paso 3).

> [!TIP]
> Si solo tiene un HoloLens, todavía puede probar la funcionalidad reiniciando la aplicación en lugar de usar un segundo dispositivo HoloLens.

## <a name="congratulations"></a>Enhorabuena

En este tutorial ha aprendido a conservar los delimitadores espaciales de Azure entre las sesiones de aplicación y los reinicios de aplicación al guardar el identificador de delimitador espacial de Azure en el disco local en HoloLens. También aprendió a compartir anclajes espaciales de Azure entre varios dispositivos para una experiencia de uso compartido de hologramas estáticos y multiusuario.

En el siguiente tutorial, aprenderá a proporcionar a los usuarios comentarios en tiempo real. Estos comentarios incluirán información sobre la creación del delimitador, la calidad de la comprensión del entorno y el estado de la sesión de Azure. Sin comentarios, es posible que los usuarios no sepan si un delimitador se ha cargado correctamente en Azure, si la calidad del entorno es suficiente para la creación del delimitador o el estado actual.

[Lección siguiente: 3. Mostrar comentarios del delimitador espacial de Azure](mrlearning-asa-ch3.md)
