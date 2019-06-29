---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465222"
---
# <a name="synchronizing-shared-object-movements"></a>Sincronizar los movimientos de objeto compartidas

En esta lección, se obtenga información sobre cómo compartir los movimientos de objetos para que puedan colaborar juntos y ver los demás interacciones todos los participantes de una sesión compartida. En esta lección se basa en el Lunar iniciador que se compiló como parte de la [Base módulo tutoriales](mrlearning-base.md).

Objetivos:

- Vuelva a poner en el lunar iniciador como el modelo 3D para compartirse
- Configurar el proyecto para compartir los movimientos del modelo 3D.
- Obtenga información sobre cómo compilar una aplicación de colaboración multiusuario básica

### <a name="instructions"></a>Instrucciones


1. Guarde la escena de la lección anterior (Control + S). Puede asignarle el nombre HLSharedProjectMainPart4.unity para que resulte más fácil encontrar cuando lo necesite.

2. En la ventana de proyecto, en los recursos -> carpeta de Scripts, haga doble clic en GenericNetSync para abrirlo en Visual Studio o que alguna vez code editor que está utilizando.  ![](images/module3chapter4updatestep2.png)

3. En líneas 34 y 38, quite la / / para activar el código de la tabla que se utilizará en esta lección. a continuación, guarde el archivo. ![](images/module3chapter4updatestep3.png)

4. En la ventana de proyecto, haga doble clic en el archivo PhotonRoom.cs en los recursos -> carpeta de Scripts para abrirlo en Visual Studio. ![](images/module3chapter4updatestep4.png)

5. Al igual que en el paso 3, se deberá quitar la / / para activar el código en líneas 106, 25 y 26.![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. En la vista de jerarquía, seleccione el objeto NetworkRoom.![](images/module3chapter4updatestep6.png)

7. En la vista del proyecto, vaya a recursos -> recursos -> prefabricados. En primer lugar, arrastre y coloque el recurso prefabricado de tabla a la ranura Tableprefab en la clase PhotonRoom. A continuación arrastre y coloque el recurso prefabricado LunarModule a la ranura en la clase PhotonRoom prefabricado de módulo. ![](images/module3chapter4updatestep7.png)

   Nota: Si hace clic en uno de los objetos prefabricados y versión, el inspector se cambiará a ese objeto. Haga clic en, arrastrar, colocar y liberar cada objeto en su espacio adecuado.



8. Haga clic en la flecha situada a la izquierda del MixedRealityPlayspace y mover el objeto de juego secundarios, MainCamera hacia abajo en el prefabricado SharedPlayground. A continuación, elimine el recurso prefabricado, MixedRealityPlayspace para eliminar, seleccione el recurso prefabricado y pulse "delete" en el teclado).
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

Nota:  Asegúrese de que se establecen las posiciones de la cámara principal y SharedPlayground en 0,0,0.

9. Cree un nuevo objeto de juego que se establece como un objeto secundario al objeto primario SharedPlayground para crear un nuevo objeto. Haga clic con el botón derecho en el objeto primario y seleccione Crear vacío. 

10. Con el nuevo objeto seleccionado en la jerarquía, cambie el nombre del objeto a TableAnchor en el panel del Inspector. Además, haga clic en Agregar componente y busque el componente TableAnchor. Selecciónelo y agregarlo al objeto. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> Nota: Establecer la posición a x = 1, y =-0,55 y, z = 2. Además, establezca la rotación en y = 90. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. Ahora, desde el panel de proyecto en la carpeta prefabricados, arrastre el recurso prefabricado de tabla en el objeto secundario de "TableAnchor" que acaba de crear.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. Por último, en el objeto DebugWindow, cambie el ancho en 80 y el alto a 10.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>Enhorabuena


Una vez completado, todos los usuarios que se unen a su proyecto Unity pueden moverse el iniciador lunar. Todos los movimientos se sincronizan para que cada usuario pueda ver las interacciones de los demás. Estos conceptos sirven como los bloques de creación fundamentales para las experiencias de colaboración completas y compartido. 

Aunque todos los usuarios están conectados como parte de una experiencia compartida y pueden ver los movimientos de objetos relativos, la aplicación es todavía no se puede alinear con precisión los avatares y objetos para que los usuarios locales ven entre sí y objetos en el mismo lugar dentro de la física mundo. Para fijar un experiencias compartidas locales, cada dispositivo requiere una comprensión común del entorno físico. En este módulo, se conseguirá esto usando [Azure espacial delimitadores](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) que se implementará en la lección siguiente.

Antes de continuar con la siguiente lección, necesitaremos completar el módulo de aprendizaje de ASA que abarca conceptos básicos ASA, cuenta de Azure y creación de recursos y otros bloques de edificios fundamentales necesitan antes de que podemos integrar esto en nuestra experiencia compartida.

[Siguiente lección: Sharing(Photon) lección 5](mrlearning-sharing(photon)-ch5.md)

