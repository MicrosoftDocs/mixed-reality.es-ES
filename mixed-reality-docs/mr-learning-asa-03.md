---
title: 'Tutoriales sobre Azure Spatial Anchors: 3. Guardar, recuperar y compartir Azure Spatial Anchors'
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 25676404a71daf41b6a5c7587fa9bed95ab813f6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305970"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a>3. Guardar, recuperar y compartir Azure Spatial Anchors

En este tutorial, aprenderás cómo guardar Azure Spatial Anchors en varias sesiones de la aplicación guardando el identificador de anclaje en el almacenamiento de HoloLens 2. También aprenderás a compartir este identificador de anclaje con otros dispositivos para una alineación de anclaje de varios dispositivos.

## <a name="objectives"></a>Objetivos

* Aprender a lograr la alineación espacial entre varias sesiones de una aplicación.
* Aprender a lograr la alineación espacial entre varios dispositivos.

## <a name="preparing-the-scene"></a>Preparación de la escena

En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent**. Seleccione los **cuatro últimos objetos de botones secundarios**. En la ventana Inspector, **active** la casilla situada junto al campo de nombre para activar todos los objetos activos.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

En la ventana Hierarchy (Jerarquía), expanda los objetos **ButtonParent**. A continuación, en la ventana Inspector, busque el componente **GridObjectCollection** y haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de todos los objetos secundarios del objeto **ButtonParent**.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a>Persistencia de Azure Spatial Anchors entre sesiones de la aplicación

En esta sección, aprenderá a guardar y recuperar el identificador de anclaje de Azure desde y hasta el disco local de HoloLens. De este modo, podrá consultar Azure para el mismo identificador de anclaje entre distintas sesiones de la aplicación. Se habilitarán los hologramas anclados para que se puedan colocar en la misma ubicación que en la sesión de aplicación anterior.

En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent** y busque los dos botones denominados **SaveAzureAnchorIdToDisk** y **GetAzureAnchorIdFromDisk**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

Siga los mismos pasos de las instrucciones proporcionadas en [Configuración de los botones para el funcionamiento de la escena](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) del tutorial anterior para configurar el componente **Interactable (Script)** (Interactuable [script]) en cada uno de los dos botones:

* Para el objeto del botón **SaveAzureAnchorIdToDisk**, asigne la función AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** .
* Para el objeto del botón **GetAzureAnchorIdFromDisk**, asigne la función AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** .

Si compila la aplicación actualizada en HoloLens, puede conservar Azure Spatial Anchors entre sesiones de aplicación si guarda el identificador del anclaje de Azure. Para probarlo, puedes seguir estos pasos:

1. Mueva el explorador del róver a la ubicación deseada.
2. Inicie una sesión de Azure.
3. Crea un anclaje de Azure (se crean anclajes en la ubicación del explorador de róver).
4. Guarde el identificador del anclaje de Azure en el disco.
5. Reinicie el equipo.
6. Obtenga el anclaje de Azure del disco (se carga el identificador de anclaje que acaba de guardar).
7. Inicia una sesión de Azure.
8. Busque el anclaje de Azure (coloca el explorador del róver en la ubicación del paso 3).

> [!NOTE]
> Para reiniciar completamente la aplicación, después de salir de la vista de aplicación inmersiva, la ventana de la aplicación en el ambiente principal debe cerrarse antes de volver a iniciar la aplicación desde el menú Inicio. Para obtener más información, puedes consultar la documentación de [Usar aplicaciones en HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens).

## <a name="sharing-azure-spatial-anchors-between-devices"></a>Uso compartido de Azure Spatial Anchors entre sesiones de la aplicación

En esta sección, obtendrás información sobre cómo compartir el identificador del anclaje de Azure entre varios dispositivos. Esto permitirá que varios dispositivos consulten Azure para el mismo identificador de anclaje, lo que permite alinear espacialmente los hologramas delimitados. La alineación espacial, que permite ver los mismos hologramas en la misma ubicación física entre varios dispositivos, es fundamental para las experiencias compartidas locales en HoloLens 2.

Hay muchas formas de transferir identificadores de anclaje de Azure entre dispositivos, incluidos los métodos descritos en la serie [Tutoriales de funcionalidades de varios usuarios](mr-learning-sharing-02.md). En este ejemplo, usarás un servicio web simple para cargar y descargar los id. de anclaje entre dispositivos.

En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent**.   Busque los dos botones denominados **ShareAzureAnchorIdToNetwork** y **GetAzureAnchorIdFromNetwork**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

Siga los mismos pasos de las instrucciones proporcionadas en [Configuración de los botones para el funcionamiento de la escena](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) del tutorial anterior para configurar el componente **Interactable (Script)** (Interactuable [script]) en cada uno de los dos botones:

* Para el objeto **ShareAzureAnchorIdToNetwork**, asigna la función AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** .
* Para el objeto **GetAzureAnchorIdFromNetwork**, asigna la función AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** .

Si compilas la aplicación actualizada en dos dispositivos HoloLens, ahora puede lograr la alineación espacial al compartir el identificador de anclaje de Azure. Para probarlo, puedes seguir estos pasos:

1. En el dispositivo HoloLens 1: Mueva el explorador del róver a la ubicación deseada.
2. En el dispositivo HoloLens 1: inicia una sesión de Azure.
3. En el dispositivo HoloLens 1: Cree un anclaje de Azure (se crean anclajes en la ubicación del explorador de róver).
4. En el dispositivo HoloLens 1: comparte el id. de anclaje de Azure con la red
5. En el dispositivo HoloLens 2: Inicie la aplicación.
6. En el dispositivo HoloLens 2: obtén el identificador de anclaje compartido de la red (captura el identificador de anclaje que se acaba de compartir desde el dispositivo HoloLens 1).
7. En el dispositivo HoloLens 2: inicia una sesión de Azure.
8. En el dispositivo HoloLens 2: Busque el anclaje de Azure (se coloca el explorador del róver en la ubicación del paso 3).

> [!TIP]
> Si solo tiene un dispositivo HoloLens, puede probar la funcionalidad igualmente reiniciando la aplicación, en lugar de usar un segundo dispositivo HoloLens.

## <a name="congratulations"></a>Enhorabuena

En este tutorial ha aprendido a conservar Azure Spatial Anchors entre las sesiones y reinicios de aplicación al guardar el identificador de anclaje espacial de Azure en el disco local de HoloLens. También has aprendido a compartir Azure Spatial Anchors entre varios dispositivos para una experiencia de uso compartido con hologramas estáticos y varios usuarios.

En el siguiente tutorial, aprenderá a proporcionar a los usuarios comentarios en tiempo real. Estos comentarios incluirán información sobre la creación de los anclajes, la calidad de la comprensión del entorno y el estado de la sesión de Azure. Sin comentarios, es posible que los usuarios no sepan si un anclaje se ha cargado correctamente en Azure, si la calidad del entorno es suficiente para la creación del anclaje o el estado actual.

[Tutorial siguiente: 4. Visualización de comentarios de Azure Spatial Anchors](mr-learning-asa-04.md)
