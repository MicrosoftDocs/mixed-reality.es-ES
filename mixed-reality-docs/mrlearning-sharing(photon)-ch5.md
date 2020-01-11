---
title: 'Tutoriales de funcionalidades para varios usuarios: 5. Integración de los anclajes espaciales de Azure en una experiencia compartida'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a3b136023b0beea7cf6eecd52a9a21447576d482
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901466"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. integrar los anclajes espaciales de Azure en una experiencia compartida

En esta lección, aprenderá a integrar anclajes espaciales de Azure (ASA) en nuestra experiencia compartida. ASA permite que varios dispositivos colocalizados tengan una referencia común si su entorno físico va a delimitar experiencias virtuales de forma que todos los participantes vean objetos en la misma ubicación física.

## <a name="objectives"></a>Objetivos

* Integre ASA en una experiencia compartida para la alineación de varios dispositivos.
* Conozca los aspectos básicos de cómo funciona ASA en el contexto de una experiencia compartida local.

## <a name="instructions"></a>Instrucciones

1. Seleccione TableAnchor recurso prefabricado bajo el objeto primario MixedRealityPlayspace y elimínelo.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. En la vista de proyecto, vaya a activos-> Resources-> Prefabs y arrastre el recurso prefabricado TableAnchor sobre el objeto SharedPlayground para convertirlo en un elemento secundario.

3. Expanda el objeto primario MixedRealityPlayspace, el objeto TableAnchor y expanda también el objeto botones.

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Ahora, en la jerarquía, seleccione ShareAzureAnchorButton y desplace su atención al panel del inspector. Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, seleccione AnchorModuleScript y haga clic en ShareAnchorNetwork ().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Seleccione GetAzureAnchorButton (consulte el paso 4) y vuelva a llamar al panel Inspector. Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, seleccione AnchorModuleScript, haga clic en GetSharedAnchorNetwork () y en guardar.

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Para probar el módulo de uso compartido, haga clic en el botón "iniciar sesión de Azure ASA", que iniciará la sesión de anclajes espaciales de Azure y luego cree el anclaje de Azure haciendo clic en el botón "crear anclaje de Azure". Espere a que se cree el delimitador de Azure. Una vez creado el delimitador de Azure, haga clic en el botón "compartir el anclaje de Azure" para compartir el anclaje de Azure creado desde HoloLens.

7. Para recibir el delimitador de Azure compartido en otro HoloLens, haga clic en "iniciar sesión de Azure ASA" para empezar a trabajar en la sesión de ASA actual.

8. Haga clic en el botón "obtener anclaje de Azure" para obtener el anclaje compartido de Azure desde el otro HoloLens.

## <a name="congratulations"></a>Enhorabuena

En esta lección, ha aprendido a integrar los nuevos delimitadores espaciales de Azure para alinear dispositivos colocalizados en una experiencia compartida. Esto también concluye el módulo de uso compartido. Hemos aprendido a configurar una nueva cuenta de Photon, a integrar Photon y BURDO en una nueva aplicación de Unity, a configurar avatares y a objetos compartidos y, por último, a alinear varios participantes con ASA.
