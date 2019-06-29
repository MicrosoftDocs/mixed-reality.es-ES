---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465200"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure delimitadores espacial y experiencias compartidas

En esta lección, se obtenga información sobre cómo integrar Azure espacial delimitadores (ASA) en nuestra experiencia compartida. ASA permite varios dispositivos colocados para tener una referencia común si su entorno físico es experiencias virtual delimitador forma que todos los participantes ven objetos en el mismo lugar físico.

Antes de continuar con esta lección, necesitaremos completar el módulo de aprendizaje de ASA que cubrirá sus aspectos básicos, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales que son necesarios antes de que podemos integrar ASA en nuestra experiencia compartido ASA.

Objetivos:

- Integrar ASA en una experiencia compartida para la alineación de varios dispositivo
- Conozca los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia local compartido

### <a name="instructions"></a>Instrucciones

1. Guarde el proyecto de la lección anterior (CTRL + S) y asígnele el nombre "HLSharedProjectMainPart5.unity" para que resulte más fácil encontrar cuando necesite de nuevo.

2. Seleccione el recurso prefabricado de TableAnchor debajo del objeto primario de MixedRealityPlayspace y elimínelo.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  En la vista del proyecto vaya a recursos -> recursos -> prefabricados y arrastre el prefabricado TableAnchor encima del objeto SharedPlayground convertirlo en un elemento secundario.
4.  Expanda el objeto primario de MixedRealityPlayspace, el objeto TableAnchor y así el objeto de botones. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Ahora en la jerarquía, seleccione ShareAzureAnchorButton y mover su atención en el panel de Inaspector. Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente y seleccione AnchorModuleScript y haga clic en ShareAnchorNetework().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Seleccione GetAzureAnchorButton (consulte el paso 4), y mover la atención de nuevo en el panel del Inspector. Desplácese hacia abajo hasta el menú desplegable que se muestra en la imagen siguiente, AnchorModuleScript y haga clic en GetSharedAnchorNetwork() y seleccione Guardar.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Enhorabuena

En esta lección ha aprendido a integrar eficaz nuevos espacial delimitadores de Azure para alinear dispositivos colocados en una experiencia compartido! En esta lección también se concluye el módulo de uso compartido. Hemos aprendido cómo configurar una nueva cuenta Photon, integrar Photon y juego de palabras en una nueva aplicación de Unity, configurar los avatares y objetos compartidos y, por último, Alinear a varios participantes con ASA. 

