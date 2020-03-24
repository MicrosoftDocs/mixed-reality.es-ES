---
title: 'Tutoriales sobre las funcionalidades multiusuario: 4. Uso compartido de movimientos de objetos con varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031248"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Uso compartido de movimientos de objetos con varios usuarios

En este tutorial, aprenderás a compartir los movimientos de objetos para que todos los participantes de una sesión compartida puedan colaborar y ver las interacciones de los demás. Esta lección se basa en el lanzacohetes lunar que se creó como parte de los [tutoriales del módulo básico](mrlearning-base.md).

## <a name="objectives"></a>Objetivos

- Seleccionar el lanzacohetes lunar como modelo 3D que se compartirá
- Configurar el proyecto para compartir los movimientos del modelo 3D
- Aprender a crear una aplicación de colaboración de varios usuarios básica

## <a name="instructions"></a>Instrucciones

1. Guarda la escena de la lección anterior (Control + S). Puedes asignarle el nombre HLSharedProjectMainPart4.unity para que sea más fácil de encontrar cuando la necesites.

2. Desde la ventana Project (Proyecto), en la carpeta Assets -> Scripts (Recursos -> Scripts), haz doble clic en GenericNetSync para abrirlo en Visual Studio o en el editor de código que estés usando.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. En las líneas 34 y 38, quita "//" para activar el código para la tabla que usarás en esta lección. A continuación, guarda el archivo.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. En la ventana Project (Proyecto), haz doble clic en el archivo PhotonRoom.cs en la carpeta Assets -> Scripts (Recursos -> Scripts) para abrirlo en Visual Studio.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Al igual que en el paso 3, es necesario quitar "//" para activar el código en las líneas 25, 26 y 106.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5b.png)

6. En la vista Hierarchy (Jerarquía), selecciona el objeto NetworkRoom.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. En la vista Project (Proyecto), desplázate a Assets->Resources->Prefabs (Recursos -> Recursos -> Objetos prefabricados). En primer lugar, arrastra y suelta el objeto prefabricado Table (Tabla) en el espacio Tableprefab de la clase PhotonRoom. A continuación, arrastra y suelta RocketLauncherCompleteVariantprefab en el espacio Module de la clase PhotonRoom.

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Si haces clic en uno de los objetos prefabricados y sueltas, el inspector cambiará a ese objeto. Haz clic en cada objeto y arrástralo y suéltalo en su espacio correspondiente.

8. Haz clic en la flecha situada a la izquierda de MixedRealityPlayspace y desplaza el objeto de juego secundario MainCamera hacia abajo en el objeto prefabricado SharedPlayground. A continuación, elimina el objeto prefabricado MixedRealityPlayspace seleccionando el objeto prefabricado y pulsa "Suprimir" en el teclado).

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Asegúrate de que tanto las posiciones de la cámara principal como de SharedPlayground están establecidas en 0,0,0.

9. Selecciona el objeto "SharedPlayground" y haz clic con el botón derecho del mouse para seleccionar la opción "Create empty" (Crear vacío) " para crear un objeto de juego vacío como elemento secundario del objeto de juego "SharedPlayground".

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. Con el nuevo objeto seleccionado en la jerarquía, cambia el nombre del objeto a TableAnchor en el panel Inspector. Además, haz clic en Agregar componente y busca el componente TableAnchor. Selecciónalo y agrégalo al objeto.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. En el panel Project (Proyecto) de la carpeta Prefabs, arrastra el objeto prefabricado Table (Tabla) hasta el objeto secundario "TableAnchor" que acabas de crear.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>Enhorabuena

Una vez completados estos pasos, busca el módulo lunar. Después de esto, todos los usuarios que se unan al proyecto de Unity podrán mover el lanzacohetes lunar.  Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás. Estos conceptos sirven como bloques de creación fundamentales para conseguir experiencias de colaboración compartidas completas.

Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos relativos de los objetos, la aplicación todavía no puede alinear con precisión los avatares y objetos, de modo que los usuarios locales no se pueden ver entre sí ni los objetos en el mismo lugar dentro del mundo físico. Para delimitar una experiencia compartida local, todos los dispositivos requieren un conocimiento común del entorno físico. En este módulo, lo conseguirás con [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>), que se implementará en la siguiente lección.

Antes de continuar con la siguiente lección, deberás completar el módulo de aprendizaje de ASA que abarca los conceptos básicos de ASA, la creación de cuentas y recursos de Azure, así como otros bloques de creación fundamentales para poder integrar esto en nuestra experiencia compartida.

[Siguiente lección: 5. Integración de Azure Spatial Anchors en una experiencia compartida](mrlearning-sharing(photon)-ch5.md)
