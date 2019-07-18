---
title: Módulo de uso compartido de aprendizaje MR para HoloLens 2
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293666"
---
# <a name="connecting-multiple-users"></a>Conexión de varios usuarios

En esta lección, aprenderá a conectar varios usuarios como parte de una experiencia compartida en directo. Al final de esta lección, podrá abrir la aplicación en varios dispositivos y ver el Avatar, representado por una esfera, representaciones de cada persona que se une. 

Objetivos

- Configuración de BURDO dentro de la aplicación
- Configuración de reproductores
- Obtenga información acerca de cómo conectar varios usuarios en una experiencia compartida

### <a name="instructions"></a>Instrucciones

1. En la carpeta assets-> Resources-> Prefabs en el panel Proyecto, arrastre y coloque el NetworkLobby recurso prefabricado en la jerarquía, tal como se muestra en la imagen siguiente.

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Al expandir NetworkLobby, verá un objeto secundario denominado NetworkRoom. Con NetworkRoom seleccionado, vaya al panel de inspectores y haga clic en Agregar componente. Busque PhotonView y agregue el componente.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Cree un nuevo objeto de juego vacío en la jerarquía. Haga clic con el botón derecho en la jerarquía y seleccione vacío en el menú contextual. Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y asigne al objeto el nombre PhotonUser.

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Haga clic en Agregar componente y escriba Generic net Sync. Seleccione la clase de sincronización de red genérica. Cuando aparezca la clase, haga clic en la casilla usuario para activarla. 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Vuelva a hacer clic en Agregar componente y escriba vista de Photon. Seleccione la clase de vista Photon que aparece en la lista desplegable.

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Haga clic en el icono de archivo de la clase net Sync genérica. Arrástrelo y colóquelo en el campo componentes observados de la vista Photon. 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. A continuación, creamos esferas para representar a cada persona que se une a una experiencia compartida. Haga clic con el botón derecho en el objeto PhotonUser que acaba de crear y scrollDown en "objeto 3D" y haga clic en sphere. Se creará un objeto de juego de esfera como elemento secundario del objeto PhotonUser.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Escale la esfera hacia abajo hasta x = 0.06, y = 0.06, ad z = 0.06.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arrastre el objeto de juego PhotonUser a la carpeta Prefabs del panel Proyecto y, a continuación, elimínelo de la escena. Ahora hemos creado un recurso prefabricado que se puede usar al generar o crear instancias de nuevos jugadores en una experiencia compartida.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> Nota: Asegúrese de que el objeto de juego se ha copiado correctamente en la carpeta Prefabs antes de eliminarlo de la jerarquía.

10. Cree un nuevo objeto en la jerarquía siguiendo las instrucciones del paso 3 y asígnele el nombre SharedPlayground. A continuación, haga clic en Agregar componente y busque administrador de red genérico y haga clic en él para agregar el componente de administrador de red genérico. Cambie la posición del objeto a x = 0, y = 0 y z = 0.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>Enhorabuena

Una vez completados todos los pasos anteriores, también se completa el proceso de compilación, presione el botón reproducir y conecte su HoloLens 2. Debería ver una esfera desplazada a medida que mueve el cabezal. Esto se mostrará para cualquier usuario que se una a su proyecto de Unity.

[Siguiente lección: Lección 4 de uso compartido (Photon)](mrlearning-sharing(photon)-ch4.md)

