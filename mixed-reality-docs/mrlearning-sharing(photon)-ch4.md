---
title: 'Tutoriales de funcionalidades para varios usuarios: 4. Compartir movimientos de objetos con varios usuarios'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 56f7c767323285453cbeea9034f97a7c14e92359
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885628"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. compartir movimientos de objetos con varios usuarios

En este tutorial, aprenderá a compartir los movimientos de objetos para que todos los participantes de una sesión compartida puedan colaborar y ver las interacciones de los demás. Esta lección se basa en el selector lunar que se compiló como parte de los [Tutoriales del módulo base](mrlearning-base.md).

## <a name="objectives"></a>Objetivos

- Traer el selector lunar como el modelo 3D que se va a compartir
- Configurar el proyecto para compartir los movimientos del modelo 3D
- Obtenga información sobre cómo crear una aplicación de colaboración de varios usuarios básica

## <a name="instructions"></a>Instrucciones

1. Guarde la escena de la lección anterior (control + S). Puede asignarle el nombre HLSharedProjectMainPart4. Unity para que sea más fácil encontrarlo cuando lo necesite.

2. En la ventana proyecto, en la carpeta assets-> scripts, haga doble clic en GenericNetSync para abrirlo en Visual Studio o en el editor de código que esté usando.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. En las líneas 34 y 38, quite "//" para activar el código para la tabla que utilizará en esta lección. A continuación, guarde el archivo.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. En la ventana proyecto, haga doble clic en el archivo PhotonRoom.cs en la carpeta assets-> scripts para abrirlo en Visual Studio.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Al igual que en el paso 3, es necesario quitar "//" para activar el código en las líneas 25, 26 y 106.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. En la vista de jerarquía, seleccione el objeto NetworkRoom.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. En la vista de proyecto, vaya a activos-> recursos-> Prefabs. En primer lugar, arrastre y coloque la tabla recurso prefabricado en la ranura Tableprefab en la clase PhotonRoom. A continuación, arrastre y coloque RocketLauncherCompleteVariantprefab en la ranura recurso prefabricado del módulo en la clase PhotonRoom.

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Si hace clic en uno de los objetos y la versión de recurso prefabricado, el inspector cambiará a ese objeto. Haga clic, arrastre, suelte y suelte cada objeto en su ranura adecuada.

8. Haga clic en la flecha situada a la izquierda de MixedRealityPlayspace y mueva el objeto de juego secundario MainCamera hacia abajo en SharedPlayground recurso prefabricado. A continuación, elimine el recurso prefabricado, MixedRealityPlayspace seleccionando recurso prefabricado y puntee en "eliminar" en el teclado).

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Asegúrese de que las posiciones de cámara y SharedPlayground principales están establecidas en 0, 0 y 0.

9. Seleccione el objeto "SharedPlayground" y haga clic con el botón secundario del mouse para seleccionar la opción "crear vacío" para crear un objeto de juego vacío como elemento secundario del objeto de juego "SharedPlayground".

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto a TableAnchor en el panel Inspector. Además, haga clic en Agregar componente y busque el componente TableAnchor. Selecciónelo y agréguelo al objeto.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. En el panel Proyecto de la carpeta Prefabs, arrastre la tabla recurso prefabricado hasta el objeto secundario "TableAnchor" que acaba de crear.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)
   
12. Abra "Rocket Launcher_Complete Variant" recurso prefabricado from assets-> Resources-> Prefabs.

13. Seleccione el GameObject "LunarModule" y agregue los dos componentes siguientes: "Photon Transform View" y "Photon View".

14. Con el GameObject "LunarModule" todavía seleccionado, arrastre el componente "vista de transformación de Photon" a la ranura "componentes observados" del componente "vista Photon".

## <a name="congratulations"></a>Enhorabuena

Una vez completado, busque el módulo lunar. Después de esto, todos los usuarios que se unen al proyecto de Unity pueden mover el selector lunar.  Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás. Estos conceptos sirven como bloques de creación fundamentales para experiencias de colaboración compartidas completas.

Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos relativos de los objetos, la aplicación todavía no puede alinear con precisión los avatares y objetos para que los usuarios locales no se puedan ver entre sí y objetos en el mismo lugar dentro de la mundo físico. Para delimitar una experiencia compartida local, todos los dispositivos requieren un conocimiento común del entorno físico. En este módulo, lograremos esto mediante el uso de [delimitadores espaciales](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) de Azure que se implementarán en la lección siguiente.

Antes de continuar con la siguiente lección, deberá completar el módulo de aprendizaje de ASA que trata los conceptos básicos de ASA, la creación de cuentas y recursos de Azure, así como otros bloques de edificios fundamentales necesarios antes de que podamos integrarlo en nuestra experiencia compartida.

[Lección siguiente: 5. integración de los anclajes espaciales de Azure en una experiencia compartida](mrlearning-sharing(photon)-ch5.md)
