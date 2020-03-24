---
title: 'Tutoriales sobre las funcionalidades multiusuario: 5. Integración de Azure Spatial Anchors en una experiencia compartida'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031688"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integración de Azure Spatial Anchors en una experiencia compartida

En esta lección, aprenderás a integrar Azure Spatial Anchors (ASA) en nuestra experiencia compartida. ASA permite que varios dispositivos colocados tengan una referencia común si su entorno físico va a delimitar experiencias virtuales de forma que todos los participantes vean objetos en la misma ubicación física.

## <a name="objectives"></a>Objetivos

* Integrar ASA en una experiencia compartida para la alineación de varios dispositivos
* Aprender los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia compartida local.

## <a name="instructions"></a>Instrucciones

1. Selecciona el objeto prefabricado TableAnchor, bajo el objeto principal MixedRealityPlayspace, y elimínalo.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. En la vista Project (Proyecto), ve a Assets -> Resources -> Prefabs (Recursos -> Recursos -> Objetos prefabricados) y arrastra el objeto prefabricado TableAnchor sobre el objeto SharedPlayground para convertirlo en un elemento secundario.

3. Expande el objeto principal MixedRealityPlayspace, el objeto TableAnchor y también el objeto Buttons (Botones).

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Ahora, en la jerarquía, selecciona ShareAzureAnchorButton y desplaza tu atención al panel Inspector. Desplázate hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, selecciona AnchorModuleScript y haz clic en ShareAnchorNetwork().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Selecciona GetAzureAnchorButton (consulta el paso 4) y vuelve a desplazar tu atención al panel Inspector. Desplázate hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, selecciona AnchorModuleScript, haz clic en GetSharedAnchorNetwork() y guarda los cambios.

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Repite el paso 4 para enlazar la función StartAzureSession() a StartAzureSessionButton.

7. Repite el paso 4 para enlazar la función CreateAzureAnchor() a CreateAzureAnchorButton y comprueba que el objeto TableAnchor está asignado al campo "Game Object" (Objeto de juego) del parámetro de la función.

8. Sigue las instrucciones de [Conexión de la escena al recurso de Azure](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) para agregar las credenciales de servicio de Azure Spatial Anchors.

9. Para probar el módulo de uso compartido, haz clic en el botón "Start Azure ASA Session" (Iniciar sesión de Azure ASA), lo que iniciará la sesión de Azure Spatial Anchors y creará un anclaje de Azure al hacer clic en el botón "Create Azure Anchor" (Crear anclaje de Azure). Espera a que se cree el anclaje de Azure. Una vez creado el anclaje de Azure, haz clic en el botón "Share Azure Anchor" (Compartir anclaje de Azure) para compartir el anclaje de Azure creado desde HoloLens.

10. Para recibir el anclaje compartido de Azure compartido en otra instancia de HoloLens, haz clic en "Start Azure ASA Session" (Iniciar sesión de Azure ASA) para empezar a trabajar en la sesión de ASA actual.

11. Haz clic en el botón "Get Azure Anchor" (Obtener anclaje de Azure)" para obtener el anclaje de Azure desde la otra instancia de HoloLens.

## <a name="congratulations"></a>Enhorabuena

En esta lección, has aprendido a integrar los nuevos anclajes espaciales de Azure para alinear dispositivos colocados en una experiencia compartida. Esto también concluye el módulo de uso compartido. Hemos aprendido a configurar una nueva cuenta de Photon, a integrar Photon y PUN en una nueva aplicación de Unity, a configurar avatares y objetos compartidos y, por último, a alinear varios participantes con ASA.
