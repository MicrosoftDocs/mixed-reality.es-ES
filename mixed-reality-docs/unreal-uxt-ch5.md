---
title: 5. Adición de un botón y restablecimiento de la ubicación de las piezas
description: Parte 5 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840404"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Adición de un botón y restablecimiento de la ubicación de las piezas

En esta sección se siguen mostrando las funcionalidades del complemento UX Tools de Mixed Reality Toolkit y se siguen compilando las características de la aplicación de ajedrez. Crearás una nueva función y aprenderás a obtener referencias a actores de tu nivel en un plano técnico.

## <a name="objectives"></a>Objetivos

* Agregar un botón al proyecto
* Crear una nueva función “Reset Location” (Restablecer ubicación) que envíe un elemento de vuelta a su ubicación original
* Configurar el botón para que desencadene la función recién creada cuando se presione

## <a name="create-a-function-to-reset-location"></a>Crear una función para restablecer la ubicación

1.  Abre **WhiteKing**. En el panel **My Blueprint** (Mi plano técnico), haz clic en el botón "+" situado junto a la sección **Functions** (Funciones) para crear una nueva función. Asigna a esta función el nombre "Reset Location" (Restablecer ubicación). 

2.  En el plano técnico **Reset Location** (Restablecer ubicación) que acabas de crear, arrastra la marca de ejecución y suéltala en cualquier punto de la cuadrícula de Blueprint para llamar a un nodo **SetActorRelativeTransform**. Esta función define la transformación (ubicación, rotación y escala) de un actor en relación con su elemento principal. Usaremos esta función para restablecer la posición del rey en el tablero, incluso si la posición original del tablero ha cambiado. Crea un nodo **Make Transform** (Crear transformación) con la ubicación X = -26, Y = 4, Z = 0 y conéctalo a la entrada New Relative Transform (Nueva transformación relativa). 

![Función Reset Location (Restablecer ubicación)](images/unreal-uxt/5-function.PNG)

3.  Compila y guarda **WhiteKing**. Vuelve a la ventana principal. 

## <a name="add-a-button"></a>Adición de un botón

1.  En la carpeta **Blueprints**, crea un nuevo plano técnico como subclase de SimpleButton. SimpleButton es un actor de plano técnico de botón 3D que se proporciona como parte del complemento UX Tools. Asigna a este botón el nombre "ResetButton" y haz doble clic para abrir el plano técnico. 

![Subclase del nuevo plano técnico de SimpleButton](images/unreal-uxt/5-subclass.PNG)

2.  En el panel **Components** (Componentes), haz clic en **PressableButton (Inherited)** . En el panel de detalles, desplázate hasta la sección **Eventos**. Haz clic en el botón verde con el signo más junto a **On Button Pressed** (Al presionar un botón). Esto agregará un nuevo evento **On Button Pressed** (Al presionar un botón) al gráfico de eventos, que se invocará cuando se presione el botón. Desde aquí, llamaremos a la función Reset Location (Restablecer ubicación) de WhiteKing. Para ello, primero necesitamos obtener una referencia al actor de WhiteKing de nuestro nivel. 

3.  En el panel **My Blueprint**, busca la sección **Variables** y haz clic en el botón **+** para agregar una nueva variable. Asigna a esta variable el nombre "WhiteKing". En el panel de detalles, selecciona la lista desplegable situada junto a **Variable Type** (Tipo de variable), busca "WhiteKing" y selecciona **Object Reference** (Referencia de objetos). Por último, activa la casilla situada junto a **Instance Editable** (Instance editable). Esto permitirá que la variable se defina desde el nivel principal. 

![Crear una variable](images/unreal-uxt/5-var.PNG)

4.  Arrastra la variable de WhiteKing desde **My Blueprint > Variables** (Mi plano técnico > Variables) hasta el gráfico de eventos de botón sencillo. Elige **Get WhiteKing** (Obtener WhiteKing). 

5.  Arrastra la marca de salida de WhiteKing y suéltala para colocar un nodo nuevo. Selecciona la función**Reset Location** (Restaurar ubicación). Por último, arrastra la marca de ejecución de salida de **On Button Pressed** (Al presionar un botón) a la marca de ejecución de entrada de **Reset Location** (Restablecer ubicación). **Compila** y **guarda** el plano técnico ResetButton y, a continuación, vuelve a la ventana principal. 

![Llamar a la función Reset Location (Restablecer ubicación) desde On Button Pressed (Al presionar un botón)](images/unreal-uxt/5-callresetloc.PNG)

6.  Arrastra **SimpleButton** a la ventanilla y establece su ubicación en X = 50, Y =-25, Z = 10. En **Default** (Predeterminada), establece el valor de la variable WhiteKing en **WhiteKing**.

![Definir la variable](images/unreal-uxt/5-buttonlevel.PNG)

Ahora tienes una aplicación de realidad mixta con un tablero y una pieza de ajedrez manipulables, así como un botón totalmente funcional que restablecerá la ubicación de la pieza cuando se presione. La aplicación completada hasta este momento se puede encontrar en [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). No dudes en profundizar más allá de este tutorial y configurar el resto de las piezas de ajedrez de modo que se restablezca todo el tablero cuando el usuario presione el botón.

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

[Sección siguiente: 6. Empaquetado y implementación en el dispositivo o emulador](unreal-uxt-ch6.md)