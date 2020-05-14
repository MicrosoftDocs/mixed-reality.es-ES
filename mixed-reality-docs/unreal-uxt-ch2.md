---
title: 2. Inicialización de tu proyecto y primera aplicación
description: Parte 2 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851579"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicialización de tu proyecto y primera aplicación

En esta sección, se proporciona orientación con la creación de una nueva aplicación de Unreal para HoloLens 2. 

## <a name="objectives"></a>Objetivos

* Configurar el desarrollo con Unreal para HoloLens
* Importar recursos y configurar la escena

## <a name="create-a-new-unreal-project"></a>Crear un nuevo proyecto de Unreal

1. Iniciar Unreal Engine

2. En **New Project Categories** (Nuevas categorías de proyecto), selecciona **Games** (Juegos) y haz clic en Next (Siguiente). Selecciona una plantilla **Blank** (En blanco) y haz clic en Next (Siguiente). 

![Seleccionar la plantilla en blanco](images/unreal-uxt/2-template.PNG)

3. En Project Settings (Configuración del proyecto), elige **C++, Scalable 3D or 2D, Mobile / Tablet** (C++, 3D o 2D escalable, móvil/tablet) y **No Starter Content** (Sin contenido inicial). Selecciona una ubicación para guardar el proyecto y haz clic en **Create Project** (Crear proyecto). Esto abrirá los archivos C++ en un proyecto de Visual Studio y en el editor de Unreal. 

![Configuración del proyecto inicial](images/unreal-uxt/2-project-settings.PNG)

4. En la esquina superior izquierda, selecciona **Edit > Plugins** (Editar > Complementos). En Augmented Reality (Realidad aumentada), activa la casilla para habilitar el complemento de **HoloLens**. Desplázate hacia abajo hasta la sección Virtual Reality (Realidad virtual) y activa la casilla para habilitar el complemento de **Microsoft Windows Mixed Reality**. Ambos complementos son necesarios para el desarrollo para HoloLens 2. Reinicia el editor. 

![Complementos](images/unreal-uxt/2-plugins.PNG)

5. En la esquina superior izquierda, ve a **File > New Level** (Archivo > Nuevo nivel). Selecciona **Empty Level** (Nivel vacío). Ahora, la escena predeterminada en la ventanilla debe estar vacía.

6. Arrastra PlayerStart y suéltalo desde el panel Modes (Modos) de la izquierda, en la pestaña Basic (Básico). En el panel de detalles de la derecha, establezca la ubicación en X = 0, Y = 0, Z = 0 para que el usuario empiece en el origen cuando la aplicación se inicie.

![Ventanilla con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

7. Arrastra un elemento **Cube** (Cubo) desde la pestaña Basic (Básico) del panel Modes (modos) a la ventanilla. En el panel de detalles, establece la ubicación en X = 50, Y = 0, Z = 0 para poner el cubo a 50 cm del jugador en el momento del inicio. Puesto que el cubo predeterminado es bastante grande, cambia su escala a (0,2, 0,2, 0,2). 

8. No podrás ver el cubo a menos que agregues una luz a la escena. Cambia a la pestaña **Lights** (Luces) del panel Modes (Modos) y arrastra una **Directional Light** (Luz direccional) a la escena, sobre PlayerStart.

![Ventanilla con luz agregada](images/unreal-uxt/2-light.PNG)

9.  Presiona el botón **Play** (Jugar) de la barra de herramientas para ver el cubo en la ventanilla. Presiona **Esc** para detener el nivel. 

![Cubo en la ventanilla](images/unreal-uxt/2-cube.PNG)

10. Vamos a guardar el nivel. En la esquina superior izquierda, haz clic en **File > Save Current** (Archivo > Guardar actual). Asigna a tu nivel el nombre "Main" y haz clic en **Save** (Guardar). 

## <a name="set-up-a-chess-scene"></a>Configurar una escena de ajedrez

1. En el explorador de contenido, haz clic en el icono situado bajo Agregar nuevo para mostrar el panel de orígenes. A continuación, haz clic en **Add New > New Folder** (Agregar nuevo > Nueva carpeta) y asigna a la carpeta el nombre "ChessAssets". Haz doble clic en esta carpeta para examinarla. Aquí es donde importaremos los recursos 3D para nuestro juego de ajedrez.

![Mostrar u ocultar el panel de orígenes](images/unreal-uxt/2-showhidesources.PNG)

2. Descarga el archivo ZIP de recursos de [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z). Este archivo contiene los modelos 3D para un tablero y unas piezas de ajedrez. Descomprime este archivo.

3. En la parte superior del explorador de contenido, haz clic en **Importar**. Navega hasta la carpeta que acabas de descomprimir y selecciona todos los elementos que contiene. Esta carpeta contiene archivos FBX, que son las mallas de objetos 3D para el tablero y las piezas de ajedrez, así como archivos TGA, que son los mapas de texturas que se van a usar para crear materiales para el tablero y las piezas. Haga clic en **Abrir**. 

4. Aparecerá la ventana FBX Import Options (Opciones de importación de FBX). En la sección **Material** (Material), cambie **Material Import Method** (Método de importación de material) a **Do Not Create Material** (No crear material). A continuación, haz clic en **Import All** (Importar todo).

![Opciones de importación de FBX](images/unreal-uxt/2-nocreatemat.PNG)

5. De nuevo en la carpeta Content (Contenido), crea una nueva carpeta denominada **Blueprints** (Planos técnicos). Aquí es donde se almacenarán todos nuestros planos técnicos, que son recursos especiales que proporcionan una interfaz basada en nodos para crear nuevos tipos de actores y eventos de nivel de script. 

6. Haz doble clic en la carpeta **Blueprints** (Planos técnicos) para examinarla. A continuación, haz clic con el botón derecho en el explorador de contenido y selecciona **Blueprint Class** (Clase de plano técnico). Haz clic en **Actor** y asigna el nombre "Board" (Tablero) al nuevo plano técnico. Haz doble clic en Board (Tablero) para abrirlo. 

![Selecciona una clase principal para el plano técnico](images/unreal-uxt/2-bpparent.PNG)

![Nuevo plano técnico Board](images/unreal-uxt/2-bpboard.PNG)

7. En el editor de planos técnicos, navega hasta el panel Components (Componentes) y haz clic en **Add Component > Scene** (Agregar componente > Escena). Asigna un nombre a la escena "Root" que acabas de crear y, después, haz clic en ella y arrástrala a DefaultSceneRoot. Esto reemplazará la raíz de la escena predeterminada y se deshará de la esfera de la ventanilla. 

![Reemplazar la raíz](images/unreal-uxt/2-root.PNG)

8. Haz clic en **Add Component** (Agregar componente) y, esta vez, elige **Static Mesh** (Malla estática). Asigna a la nueva malla el nombre "SM_Board". 

![Adición de una malla estática](images/unreal-uxt/2-sm-board.PNG)

9. En el panel **Details** (Detalles), localiza la sección **Static Mesh** (Malla estática) y haz clic en la lista desplegable. Selecciona **ChessBoard**. 

![Malla del tablero en la ventanilla](images/unreal-uxt/2-sm-board-view.PNG)

10. En el panel **Details** (Detalles), localiza la sección **Materiales** y haz clic en la lista desplegable. En **Create New Asset** (Crear nuevo recurso), selecciona **Material**. Asigna a este recurso el nombre **M_ChessBoard** y guárdalo en la carpeta **ChessAssets**. 

![Crear un material nuevo](images/unreal-uxt/2-newmat.PNG)

11. Haz doble clic en el cuadrado junto a la lista desplegable M_ChessBoard para abrir el material M_ChessBoard que acabas de crear. En el editor de materiales, haz clic con el botón derecho y busca el nodo **Texture Sample**. En el panel **Details** (Detalles), en la sección **Material Expression Texture Base** (Base de textura de expresión de material), haz clic en la lista desplegable y selecciona **ChessBoard_Albedo**. Por último, arrastra la marca de salida de **RGB** a la marca Base Color (Color de base) de **M_ChessBoard**. 

![Establecer el color de base](images/unreal-uxt/2-boardalbedomat.PNG)

12. Haz lo mismo cuatro veces para vincular la muestra de textura **ChessBoard_AO** con la marca **Ambient Occlusion**, **ChessBoard_Metal** con **Metallic**, **ChessBoard_Normal** con **Normal** y **ChessBoard_Rough** con **Roughness**. Haga clic en **Guardar**. 

![Enlazar las texturas restantes](images/unreal-uxt/2-boardmat.PNG)

13. Vuelve al plano técnico **Board**. Deberías ver que el material que acabas de crear se ha aplicado al plano técnico. Para asegurarte de que el tablero tiene un tamaño y una posición razonables cuando lo colocamos en nuestra escena, cambia el valor de **Scale** (Escala) del tablero a (0,05, 0,05, 0,05) y el de **Rotation** (Rotación) a Z = 90. En la barra de herramientas de la parte superior, haz clic en **Compile** (Compilar) y **Save** (Guardar). Vuelve a la ventana principal. 

![Tablero de ajedrez con el material aplicado](images/unreal-uxt/2-chessboard.PNG)

14. Ahora vamos a eliminar el cubo y reemplazarlo por el actor Board (Tablero) recién creado. En **World Outliner** (Esquematizador del mundo), haz clic con el botón derecho en **Cube > Edit > Delete** (Cubo > Editar > Eliminar). Arrastra el panel desde el explorador de contenido hasta la ventanilla. Establece la ubicación del tablero en X = 80, Y = 0, Z =-20. 

15. Haz clic en el botón **Play** (Jugar) para ver el nuevo tablero en el nivel. Presiona **Esc** para volver al editor. 

16. Ahora seguiremos los mismos pasos para crear una pieza de ajedrez como hicimos con el tablero, pero esta vez seleccionaremos la malla y el material para la pieza de ajedrez:

    a) Ve a la carpeta Blueprints desde el explorador de contenido y crea una nueva clase Blueprint de tipo Actor. Asigna al actor el nombre "WhiteKing".

    b) Haz doble clic en WhiteKing para abrirlo. Agrega un nuevo componente de escena denominado "Root" y úsalo para reemplazar DefaultSceneRoot. 

    c) Agrega un nuevo componente de malla estática denominado "SM_King". En el panel de detalles, establece **Static Mesh** en **Chess_King** y **Material** en un nuevo material denominado **M_ChessWhite**. 

    d) Abre el nuevo material **M_ChessWhite** y enlaza las texturas pertinentes con sus entradas de material correspondientes. 

    ![Crear el material para el rey del ajedrez](images/unreal-uxt/2-chesskingmat.PNG)

    e) De nuevo en el plano técnico **WhiteKing**, cambia el valor de **Scale** a (0,05, 0,05, 0,05) y el de **Rotation** (Rotación) a Z = 90.

    f) Compila y guarda el plano y, a continuación, vuelve a la ventana principal. 

17. Arrastra WhiteKing a la ventanilla. En **World Outliner** (Esquematizador del mundo), arrastra WhiteKing a Board para que se convierta en un elemento secundario de este. 

![World Outliner (Esquematizador del mundo)](images/unreal-uxt/2-child.PNG)

18. En el panel **Details** (Detalles), en **Transform** (Transformar), define el valor de **Location** (Ubicación) de WhiteKing en X = -26, Y = 4, Z = 0.

19. Haz clic en **Play** (Jugar) para ver tu nivel. Presiona **Esc** para salir. 

[Sección siguiente: 3. Configuración del proyecto para la realidad mixta](unreal-uxt-ch3.md)