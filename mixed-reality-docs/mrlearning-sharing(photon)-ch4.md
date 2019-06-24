---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327715"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>Sincronizar los movimientos de objetos compartidos

En esta lección, aprenderemos a compartir los movimientos de objetos para que puedan colaborar juntos y ver los demás interacciones todos los participantes de una sesión compartida. En esta lección se basa en el Lunar iniciador que se compiló como parte de la [Base módulo tutoriales](mrlearning-base.md).

Objetivos:

- Importar el iniciador Lunar completado como el modelo 3D para compartirse
- Configurar el proyecto para compartir los movimientos del modelo 3D.
- Obtenga información sobre cómo compilar una aplicación de colaboración multiusuario básica

### <a name="instructions"></a>Instrucciones

1. Guarde la escena de la lección anterior (CTRL + S). Es posible que denominó "HLSharedProjectMainPart4.unity" para que resulte más fácil encontrar cuando necesite de nuevo.

2. Elimine el objeto "NetworkLobby" (, selecciónela y presione SUPR). Además, vaya a la carpeta "prefabricados" de la lección 2 y elimine el recurso prefabricado "NetworkLobby" desde allí también.

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. Importar un nuevo paquete personalizado (por ejemplo, paso 2 de la lección 2) e importar el [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) y [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. Ahora, en la carpeta "prefabricados", arrastre el nuevo recurso prefabricado de "NetworkLobby" en la jerarquía. 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> Nota: los dos paquetes que se ha importado en los pasos anteriores actualizan el recurso prefabricado "NetworkLobby". ¡Le evita tener que escribir mucho!

5. Ahora, haga clic en la flecha situada a la izquierda de "MixedRealityPlayspace" y mover el objeto de juego secundarios, "MainCamera" hacia abajo en el prefabricado "SharedPlayground". A continuación, elimine el prefabricado "MixedRealityPlayspace" (para eliminar, seleccione el recurso prefabricado y pulse "eliminar" en el teclado).

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. Cree un nuevo objeto de juego establecer como objeto secundario al objeto primario "SharedPlayground" (para crear un nuevo objeto, haga clic con el botón derecho en el objeto primario y seleccione "Crear vacío").
7. Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto para "TableAnchor" en el panel del inspector. Además, haga clic en "agregar el componente" y busque el componente "TableAnchor". Selecciónelo y agregarlo al objeto.

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Nota: establezca el posicionamiento a x = 1, y =-0,55 y, z = 2. Además, establezca la rotación en y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. Ahora en el panel de proyecto, en la carpeta "prefabricados", arrastre el recurso prefabricado "table" en el objeto secundario de "TableAnchor" que acaba de crear.

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. Seleccione "NetworkRoom", un objeto secundario en "NetworkLobby" en la jerarquía y haga clic en "agregar el componente" en el panel de inspector y busque "PhotonView" y agregue el script para el "*NetworkRoom*" objeto.

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. Por último, en el objeto "DebugWindow", cambie el ancho en 80 y el alto a 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Enhorabuena

Una vez completado, todos los usuarios que se unen a su proyecto Unity pueden moverse el iniciador Lunar. Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás. Estos conceptos sirven como los bloques de creación fundamentales para las experiencias de colaboración compartido completa. 

Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos de objetos relativos, la aplicación es todavía no se puede alinear con precisión los avatares y objetos para que los usuarios locales ven entre sí y objetos en el mismo lugar dentro de la física mundo. Para fijar un experiencias compartidas locales, cada dispositivo requiere una comprensión común del entorno físico. En este módulo, conseguiremos esto mediante [Azure espacial delimitadores](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), que se implementará en la lección siguiente.

Antes de continuar con la siguiente lección, necesitaremos completar el módulo de aprendizaje de ASA, que tratará aspectos básicos ASA, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales necesitan antes de que podemos integrar esto en nuestra experiencia compartido.

[Siguiente lección: Sharing(Photon) lección 5](mrlearning-sharing(photon)-ch5.md)

