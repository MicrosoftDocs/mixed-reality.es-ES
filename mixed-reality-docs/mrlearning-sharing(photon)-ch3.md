---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415916"
---
# <a name="connecting-multiple-users"></a>**Conectar varios usuarios** 

En esta lección, se obtendrá información sobre cómo conectar varios usuarios como parte de una experiencia compartida en vivo. Al final de esta lección, podrá abrir la aplicación en varios dispositivos y ver representaciones "avatar" de cada persona que une (avatares representados por una esfera). 

Objetivos:

- Configurar el juego de palabras dentro de la aplicación
- Configurar los jugadores
- Obtenga información sobre cómo conectar varios usuarios en una experiencia compartido

### <a name="instructions"></a>Instrucciones

1. En los recursos > recursos > prefabricados carpeta del panel proyecto, arrastrar y colocar la "NetworkLobby" prefabricado en a la jerarquía, tal como se muestra en la imagen siguiente.


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Al expandir el prefabricado "NetworkLobby", debería ver un objeto secundario denominado "NetworkRoom." Con él seleccionado, vaya al panel de inspector y haga clic en "Agregar el componente". Busque "PhotonView" y agregue el componente.

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Crear un nuevo objeto de juego vacío en la jerarquía (haga clic con el botón derecho en la jerarquía y seleccione "Empty" en el menú contextual). Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y el nombre del objeto, "PhotonUser".

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Haga clic en el botón "Agregar componente" y escriba "Sync neto genérico" y seleccione la clase genérica sincronización Net. Una vez que la clase aparece, haga clic en la casilla de verificación "Usuario" para activarlo. 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Vuelva a haga clic en "Agregar componente" y, a continuación, escriba "Photon vista" y seleccione la clase de vista Photon que aparece en la lista desplegable.

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Ahora haga clic en el icono del archivo para la clase genérica sincronización neto, en, a continuación, arrastre y colóquelo en el campo de la vista Photon "Observado componentes". ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. A continuación, deseamos crear ámbitos para representar a cada persona que une una experiencia compartida. A la derecha, haga clic en el objeto "PhotonUser" que acaba de crear, ir a "objeto 3D" y haga clic en "Esfera". Esto creará un objeto de juego esfera como elemento secundario del objeto PhotonUser.

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Escalar la esfera hasta x = 0,06, y = 0,06, ad z = 0,06.

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arrastre el objeto de juego "PhotonUser" en la carpeta "prefabricados" en el panel de proyecto. A continuación, eliminarlo de la escena. Ahora hemos creado un prefabricado que se usará al generar o crear una instancia de nuevos jugadores en una experiencia compartida.

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Nota: asegúrese de que el objeto de juego ha copiado correctamente en la carpeta "prefabs" antes de eliminarlos de la jerarquía.

10. Cree un nuevo objeto en la jerarquía (con instrucciones similares a la de paso 3) y asígnele el nombre "SharedPlayground." A continuación, haga clic en "Agregar componente" y busque "Administrador de red genéricos" y haga clic en él para agregar el componente del Administrador de red genéricos. Cambiar la posición del objeto a x = 0, y = 0 y, z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Enhorabuena

Una vez que finalizan todos los pasos anteriores, y el proceso de compilación ha finalizado, cuando presione el botón play y se conecta el 2 de HoloLens, debería ver una esfera mover mover la cabeza! Se mostrará para cualquier usuario que se une a su proyecto de Unity.

[Siguiente lección: Sharing(Photon) lección 4](mrlearning-sharing(photon)-ch4.md)

