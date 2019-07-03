---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 44cc41b10ed79d3085ec601ec9cf21af47b0fea5
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523304"
---
# <a name="connecting-multiple-users"></a>Conectar varios usuarios

En esta lección, se obtenga información sobre cómo conectar varios usuarios como parte de una experiencia compartida en vivo. Al final de esta lección, podrá abrir la aplicación en varios dispositivos y vea avatar, representado por una esfera, representaciones de cada persona que se une. 

Objetivos:

- Configurar el juego de palabras dentro de la aplicación
- Configurar los jugadores
- Obtenga información sobre cómo conectar varios usuarios en una experiencia compartido

### <a name="instructions"></a>Instrucciones

1. En los recursos -> recursos -> carpeta prefabricados en el panel proyecto, arrastre y coloque el prefabricado NetworkLobby en a la jerarquía, tal como se muestra en la imagen siguiente.


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Al expandir NetworkLobby, verá un objeto secundario llamado NetworkRoom. Con NetworkRoom seleccionado, vaya al panel de Inspector y haga clic en Agregar componente. Buscar PhotonView y agregue el componente.

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Crear un nuevo objeto de juego vacío en la jerarquía. Haga clic con el botón derecho en la jerarquía y seleccione vacía en el menú contextual. Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y el nombre del objeto, PhotonUser.

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Haga clic en Agregar componente y escriba sincronización neto genérico. Seleccione la clase genérica sincronización Net. Cuando aparezca la clase, haga clic en la casilla de verificación de usuario para activarlo. 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Haga clic en Agregar componente nuevo y escriba Photon View. Seleccione la clase de vista Photon que aparece en la lista desplegable.

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Haga clic en el icono del archivo para la clase genérica sincronización Net. Arrastre y colóquelo en el campo de la vista Photon componentes observado. ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. A continuación, creamos esferas para representar a cada persona que une una experiencia compartida. Haga clic en el objeto PhotonUser que acaba de crear y scrolldown a "esfera objeto 3D y haga clic en. Esto creará un objeto de juego esfera como elemento secundario del objeto PhotonUser.

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Escalar la esfera hasta x = 0,06, y = 0,06, ad z = 0,06.

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arrastre el objeto de juego PhotonUser en la carpeta prefabricados en el panel de proyecto y, a continuación, eliminarlo de la escena. Ahora hemos creado un prefabricado que se puede usar al generar o crear una instancia de nuevos jugadores en una experiencia compartida.

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Nota: asegúrese de que el objeto de juego ha copiado correctamente en la carpeta prefabricados antes de eliminarlos de la jerarquía.

10. Crear un nuevo objeto en la jerarquía, siga las instrucciones en el paso 3 y asígnele el nombre SharedPlayground. A continuación, haga clic en Agregar componente, busque el Administrador de red genéricos y haga clic en él para agregar el componente del Administrador de red genéricos. Cambiar la posición del objeto a x = 0, y = 0 y, z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Enhorabuena

Una vez que finalizan todos los pasos anteriores, y el proceso de compilación también está completando, presione el botón Reproducir y conectar el 2 de HoloLens. Debería ver una esfera mover mover la cabeza. Se mostrará para cualquier usuario que se une a su proyecto de Unity.

[Siguiente lección: Sharing(Photon) lección 4](mrlearning-sharing(photon)-ch4.md)

