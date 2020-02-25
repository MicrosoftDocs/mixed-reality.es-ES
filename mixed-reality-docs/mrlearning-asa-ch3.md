---
title: 'Tutoriales de anclaje espacial de Azure: 3. Visualización de los comentarios del delimitador espacial de Azure'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553959"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Mostrar comentarios del delimitador espacial de Azure

En este tutorial, obtendrá información sobre cómo proporcionar a los usuarios comentarios sobre la detección de delimitadores, los eventos y el estado al usar delimitadores espaciales (ASA) de Azure.

## <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo configurar un panel de interfaz de usuario que muestre información importante sobre la sesión actual de ASA.
* Comprenda y explore los elementos de comentarios que el SDK de ASA pone a disposición de los usuarios

## <a name="set-up-asa-feedback-ui-panel"></a>Configuración del panel de interfaz de usuario de comentarios de ASA

En la ventana jerarquía, haga clic con el botón derecho en las **instrucciones** > objeto **TextContent** y seleccione **objeto 3D** > **Text-TextMeshPro** para crear un objeto de texto TextMeshPro como un elemento secundario de las instrucciones > objeto TextContent y asígnele un nombre adecuado, por ejemplo, **feedback**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Para que sea más fácil trabajar con la escena, haga clic en el icono de ojo situado a la izquierda del objeto para establecer la visibilidad de la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">escena</a> del objeto ParentAnchor en OFF. Esto oculta el objeto en la ventana de la escena sin cambiar su visibilidad en el juego.

Con el objeto de **comentarios** aún seleccionado, en la ventana del inspector cambie su posición y el tamaño para que se coloquen en un lugar inferior al texto de la instrucción, por ejemplo:

* Cambie la transformación de rectángulo **Y** a-0,24
* Cambiar el **ancho** de la transformación Rect a 0,555
* Cambiar el **alto** de la transformación Rect a 0,1

A continuación, elija Propiedades de fuente para que el texto se ajuste perfectamente dentro del área de texto, por ejemplo:

* Cambiar el **estilo de fuente** de la malla de texto Pro (Script) a negrita
* Cambiar el **tamaño de fuente** de la malla de texto Pro (Script) a 0,17
* Cambiar la **alineación** de la malla de texto Pro (Script) al centro y el medio

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Con el objeto de **comentarios** aún seleccionado, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente **script de comentarios de delimitador (Script)** al objeto de comentarios:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Asigne el objeto de **comentarios** en el campo de **texto de comentarios** del componente **script de comentarios delimitadores (Script)** :

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a crear un panel de interfaz de usuario para mostrar el estado actual de la experiencia del anclaje espacial de Azure para proporcionar a los usuarios comentarios en tiempo real.
