---
title: 'Tutoriales sobre Azure Spatial Anchors: 2. Guardar, recuperar y compartir Azure Spatial Anchors'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4de40bb0b66ed299fa4a571490b33a0454f25817
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031703"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Guardar, recuperar y compartir Azure Spatial Anchors

En este tutorial, aprenderás cómo guardar Azure Spatial Anchors en varias sesiones de la aplicación guardando el identificador de anclaje en el almacenamiento de HoloLens 2. También aprenderás a compartir este identificador de anclaje con otros dispositivos para una alineación de anclaje de varios dispositivos.

## <a name="objectives"></a>Objetivos

* Aprender a guardar y recuperar los identificadores de Azure Spatial Anchors en el disco local de HoloLens 2 para la persistencia entre sesiones de aplicación
* Aprender a compartir identificadores de Azure Spatial Anchor entre usuarios en un escenario de varios dispositivos

## <a name="preparing-the-scene"></a>Preparación de la escena

Desde la ventana Project (Proyecto), desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpatialAnchors** > carpeta **Prefabs**. Mientras mantienes presionado el botón CTRL, haz clic en **ButtonParent_SaveAnchorId** y **ButtonParent_ShareAnchorId** para seleccionar los dos objetos prefabricados y, a continuación, arrástralos a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Persistencia de anclajes de Azure entre sesiones de aplicación: guardar el identificador de anclaje en el disco
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

En esta sección, aprenderás a guardar y recuperar el identificador de anclaje de Azure desde y hasta el disco local de HoloLens 2. Esto te permitirá consultar Azure con el mismo identificador de anclaje en distintas sesiones de aplicación, lo que permite colocar los hologramas anclados en la misma ubicación que en la sesión de aplicación anterior.

En la ventana Hierarchy (Jerarquía), expande el objeto **ButtonParent_SaveAnchorId**, que contiene dos botones: uno para guardar el identificador del anclaje de Azure en el almacenamiento de HoloLens 2 y otro para recuperar el identificador guardado del disco:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Sigue los mismos pasos de las instrucciones de [Configuración de los botones para el funcionamiento de la escena](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) del tutorial anterior para configurar el componente **Pressable Button Holo Lens 2 (Script)** (Botón presionable de HoloLens 2 [script]) y el componente **Interactable (Script)** (Interactuable [script]) en cada uno de los dos botones:

* Para el objeto **SaveAzureAnchorIdToDisk**, asigna la función AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Para el objeto **GetAzureAnchorIdFromDisk**, asigna la función AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Si compilas la aplicación actualizada en HoloLens, puedes conservar Azure Spatial Anchors entre sesiones de aplicación si guardas el identificador del anclaje de Azure. Para probarlo, puedes seguir estos pasos:

1. Mueve la experiencia del lanzacohetes a la ubicación deseada.
2. Inicia una sesión de Azure.
3. Crea un anclaje de (crea anclajes en la ubicación de la experiencia del lanzacohetes).
4. Guarda el identificador del anclaje de Azure en el disco.
5. Reinicia la aplicación.
6. Obtén el anclaje de Azure del disco (carga el id. de anclaje que acabas de guardar).
7. Inicia una sesión de Azure.
8. Busca el anclaje de Azure (coloca la experiencia del lanzacohetes en la ubicación del paso 3).

## <a name="share-azure-anchors-between-multiple-devices"></a>Compartir anclajes de Azure entre varios dispositivos

En esta sección, obtendrás información sobre cómo compartir el identificador del anclaje de Azure entre varios dispositivos. Esto permitirá que varios dispositivos consulten Azure para el mismo identificador de anclaje, lo que permite alinear espacialmente los hologramas delimitados. La alineación espacial, que permite ver los mismos hologramas en la misma ubicación física entre varios dispositivos, es fundamental para las experiencias compartidas locales en HoloLens 2.

Hay muchas formas de transferir identificadores de anclaje de Azure entre dispositivos, incluidos los métodos descritos en la serie [Tutoriales de funcionalidades de varios usuarios](mrlearning-sharing(photon)-ch1.md). En este ejemplo, usarás un servicio web simple para cargar y descargar los id. de anclaje entre dispositivos.

En la ventana Hierarchy (Jerarquía), expande el objeto **ButtonParent_ShareAnchorId**, que contiene dos botones: uno para cargar el identificador del anclaje de Azure en el servidor web y otro para descargar el identificador del servidor web:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Sigue los mismos pasos de las instrucciones de [Configuración de los botones para el funcionamiento de la escena](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) del tutorial anterior para configurar el componente **Pressable Button Holo Lens 2 (Script)** (Botón presionable de HoloLens 2 [script]) y el componente **Interactable (Script)** (Interactuable [script]) en cada uno de los dos botones:

* Para el objeto **ShareAzureAnchorIdToNetwork**, asigna la función AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Para el objeto **GetAzureAnchorIdFromNetwork**, asigna la función AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Si compilas la aplicación actualizada en dos dispositivos HoloLens, ahora puedes lograr la alineación espacial entre ellos al compartir el identificador de anclaje de Azure. Para probarlo, puedes seguir estos pasos:

1. En el dispositivo HoloLens 1: mueve la experiencia del lanzacohetes a la ubicación deseada.
2. En el dispositivo HoloLens 1: inicia una sesión de Azure.
3. En el dispositivo HoloLens 1: crea un anclaje de Azure (crea anclajes en la ubicación de la experiencia del lanzacohetes).
4. En el dispositivo HoloLens 1: comparte el id. de anclaje de Azure con la red
5. En el dispositivo HoloLens 2: reinicia la aplicación.
6. En el dispositivo HoloLens 2: obtén el identificador de anclaje compartido de la red (captura el identificador de anclaje que se acaba de compartir desde el dispositivo HoloLens 1).
7. En el dispositivo HoloLens 2: inicia una sesión de Azure.
8. En el dispositivo HoloLens 2: busca el anclaje de Azure (coloca la experiencia del lanzacohetes en la ubicación del paso 3).

> [!TIP]
> Si solo tienes un dispositivo HoloLens, puedes probar la funcionalidad igualmente reiniciando la aplicación, en lugar de usar un segundo dispositivo HoloLens.

## <a name="congratulations"></a>Enhorabuena

En este tutorial has aprendido a conservar Azure Spatial Anchors entre las sesiones y reinicios de aplicación al guardar el identificador de anclaje espacial de Azure en el disco local en HoloLens. También has aprendido a compartir Azure Spatial Anchors entre varios dispositivos para una experiencia de uso compartido con hologramas estáticos y varios usuarios.

En el siguiente tutorial, aprenderás a proporcionar a los usuarios comentarios en tiempo real. Estos comentarios incluirán información sobre la creación de los anclajes, la calidad de la comprensión del entorno y el estado de la sesión de Azure. Sin comentarios, es posible que los usuarios no sepan si un anclaje se ha cargado correctamente en Azure, si la calidad del entorno es suficiente para la creación del anclaje o el estado actual.

[Siguiente lección: 3. Visualización de comentarios de Azure Spatial Anchors](mrlearning-asa-ch3.md)
