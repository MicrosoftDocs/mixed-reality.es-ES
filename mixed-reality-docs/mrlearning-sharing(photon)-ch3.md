---
title: 'Tutoriales sobre las funcionalidades multiusuario: 3. Conexión de varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031227"
---
# <a name="3-connecting-multiple-users"></a>3. Conexión de varios usuarios

En esta lección, aprenderemos cómo conectar varios usuarios como parte de una experiencia compartida en directo. Al final de esta lección, podrás abrir la aplicación en varios dispositivos y ver el avatar, representado por una esfera para cada persona que se una.

## <a name="objectives"></a>Objetivos

* Configurar PUN en la aplicación
* Configurar los jugadores
* Aprender a conectar varios usuarios en una experiencia compartida

## <a name="instructions"></a>Instrucciones

1. En la carpeta Assets->Resources->Prefabs (Recursos -> Recursos-> Objetos prefabricados) del panel Proyecto, arrastra y coloca el objeto prefabricado NetworkLobby en la jerarquía, tal y como se muestra en la imagen siguiente.

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. Al expandir NetworkLobby, verás un objeto secundario denominado NetworkRoom. Con el objeto NetworkRoom seleccionado, ve al panel Inspector y haz clic en Add Component (Agregar componente). Busca PhotonView y agrega el componente.

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. Crea un nuevo objeto de juego vacío en la jerarquía. Haz clic con el botón derecho en la jerarquía y selecciona Vacío en el menú contextual. Asegúrate de que la posición está establecida en x = 0, y = 0, z = 0 y asigna al objeto el nombre PhotonUser.

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. Haz clic en Agregar componente y escribe Generic Net Sync (Sincronización de red genérica). Selecciona la clase Generic Net Sync (Sincronización de red genérica). Cuando aparezca la clase, haz clic en la casilla Usuario para activarla.

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. Haz clic de nuevo en Add Component (Agregar componente) y escribe Photon View (Vista de Photon). Selecciona la clase Photon View (Vista de Photon) que aparece en la lista desplegable.

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Haz clic en el icono Archivo de la clase Generic Net Sync (Sincronización de red genérica). Arrástralo y colócalo en el campo Observed Components (Componentes observados) de Photon View (Vista Photon).

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. A continuación, creamos esferas para representar a cada persona que se une a una experiencia compartida. Haz clic con el botón secundario en el objeto PhotonUser que acabas de crear, desplázate hacia abajo hasta 3D Object (Objeto 3D) y haz clic en Sphere (Esfera). Se creará un objeto de juego de esfera como elemento secundario del objeto PhotonUser.

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. Reduce verticalmente la esfera a x = 0,06, y = 0,06 y z = 0,06.

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. Arrastra el objeto de juego PhotonUser a la carpeta Prefabs del panel Project (Proyecto) y, a continuación, elimínalo de la escena. Ya has creado un objeto prefabricado que se puede usar al generar nuevos jugadores o crear instancias a partir de estos en una experiencia compartida.

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >Comprueba que el objeto de juego se haya copiado correctamente en la carpeta Prefabs antes de eliminarlo de la jerarquía.

10. Crea un objeto nuevo en la jerarquía siguiendo las instrucciones del paso 3 y asígnale el nombre SharedPlayground. A continuación, haz clic en Add Component (Agregar componente) y busca un administrador de red genérico.  Vuelve a hacer clic en el componente Generic Network Manager (Administrador de red genérico). Cambia la posición del objeto a x = 0, y = 0 y z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>Enhorabuena

Una vez completados todos los pasos anteriores y finalizado el proceso de compilación, presiona el botón Play (Jugar) y conecta el dispositivo HoloLens 2. Deberías ver una esfera a tu alrededor a medida que mueves la cabeza. Se mostrará para cualquier usuario que se una a tu proyecto de Unity.

[Siguiente lección: 4. Uso compartido de movimientos de objetos con varios usuarios](mrlearning-sharing(photon)-ch4.md)
