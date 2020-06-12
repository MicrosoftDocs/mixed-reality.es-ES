---
title: 3. Configuración del proyecto para la realidad mixta
description: Parte 3 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330309"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Configuración del proyecto para la realidad mixta

## <a name="overview"></a>Introducción

En el tutorial anterior, ha dedicado tiempo a configurar el proyecto de aplicación de ajedrez. En esta sección se le guiará en la configuración de la aplicación para el desarrollo de realidad mixta, lo que significa la adición de una sesión de AR. Usará un recurso de datos ARSessionConfig para esta tarea, que dispone una gran cantidad de opciones útiles de AR, como el mapeo espacial y la oclusión. Si desea profundizar más, en la documentación de Unreal Engine se incluyen más detalles sobre el recurso [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) y la clase [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).

## <a name="objectives"></a>Objetivos
* Trabajo con la configuración de AR de Unreal Engine 
* Uso de un recurso de datos ARSessionConfig
* Configuración de un peón y el modo de juego

## <a name="adding-the-session-asset"></a>Adición del recurso de sesión
Las sesiones de AR en Unreal no aparecen por sí mismas. Para usar una sesión, necesita un recurso de datos ARSessionConfig con el que trabajar, que será la tarea siguiente:

1. Haga clic en **Add New > Miscellaneous > Data Asset** (Agregar nuevo > Varios > Recursos de datos) en **Content Browser** (Explorador de contenido). Asegúrese de que se encuentra en el nivel raíz de la carpeta **Content** (Contenido). 
    * Seleccione **ARSessionConfig**, haga clic en **Select** (Seleccionar) y asigne al recurso el nombre **ARSessionConfig**.

![Crear un recurso de datos](images/unreal-uxt/3-createasset.PNG)

3. Haga doble clic en **ARSessionConfig** para abrirlo, deje la configuración predeterminada y haga clic en **Save** (Guardar). Vuelve a la ventana principal. 

![Configuración de sesión de AR](images/unreal-uxt/3-arsessionconfig.PNG)

Después de hacer esto, el paso siguiente consiste en asegurarse de que la sesión de AR se inicia cuando se carga el nivel. Por suerte, Unreal tiene un tipo especial de plano técnico denominado **Level Blueprint** (Plano técnico de nivel) que actúa como un gráfico de eventos global de nivel superior. La conexión del recurso ARSessionConfig en **Level Blueprint** (Plano técnico de nivel) garantiza que la sesión de AR se activará cuando se inicie la reproducción del juego.

1. Haga clic en **Blueprints > Open Level Blueprint** (Planos técnicos > Abrir plano técnico de nivel) en la barra de herramientas del editor: 

![Abrir plano técnico de nivel](images/unreal-uxt/3-level-blueprint.PNG)

5. Arrastre el nodo de ejecución (icono de flecha hacia la izquierda) fuera de **Event BeginPlay** (Evento BeginPlay) y suéltelo. Busque **Start AR Session** (Iniciar sesión de AR).  
    * Haga clic en la lista desplegable **Select Asset** (Seleccionar recurso) en **Session Config** (Configuración de sesión) y elija el recurso **ARSessionConfig**. 
    * Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.

![Iniciar sesión de AR](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a>Creación de un peón
En este punto, el proyecto todavía necesita un objeto que sea el jugador. En Unreal, **Pawn** (Peón) representa al usuario del juego; pero, en este caso, será la experiencia de HoloLens 2.

1. Haga clic en **Add New > Blueprint Class** (Agregar nuevo > Clase de plano técnico) en la carpeta **Content** (Contenido) y expanda la sección **All Classes** (Todas las clases) en la parte inferior. 
    * Busque **DefaultPawn**, haga clic en **Select** (Seleccionar) y haga doble clic en el recurso para abrirlo. 

![Crear un nuevo peón que herede de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> De forma predeterminada, los peones tienen componentes de malla y colisión. En la mayoría de los proyectos de Unreal, los peones son objetos sólidos que pueden colisionar con otros componentes. Dado que el peón y el usuario son los mismos en la realidad mixta, querrá poder pasar a través de hologramas sin colisiones. 

2. Seleccione **CollisionComponent** en el panel **Components** (Componentes) y desplácese hacia abajo hasta la sección **Collision** (Colisión) del panel **Details** (Detalles). 
    * Haga clic en la lista desplegable **Collision Presets** (Valores preestablecidos de colisión) y cambie el valor a **NoCollision**. 
    * Haga lo mismo para **MeshComponent**, después **compile** y **guarde** el plano técnico. 

![Ajustar los valores preestablecidos de colisión del peón](images/unreal-uxt/3-nocollision.PNG)

Con el trabajo que ha realizado aquí, vuelva a la ventana principal.

## <a name="create-a-game-mode"></a>Creación de un modo de juego
La última pieza del rompecabezas de la configuración de la realidad mixta es el modo de juego. El modo de juego determina una serie de opciones de configuración para el juego o la experiencia, incluido el peón predeterminado que se usará.

1.  Haga clic en **Add New > Blueprint Class** (Agregar nuevo > Clase de plano técnico) en la carpeta **Content** (Contenido) y expanda la sección **All Classes** (Todas las clases) en la parte inferior. 
    * Busque **Game Mode Base** (Base de modo de juego), asígnele el nombre **MRGameMode** y haga doble clic en él para abrirlo. 

![MRGameMode en el explorador de contenido](images/unreal-uxt/3-gamemode.PNG)

2.  Vaya a la sección **Classes** (Clases) en el panel **Details** (Detalles) y cambie **Default Pawn Class** (Clase de peón predeterminado) a **MRPawn**. 
    * Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal. 

![Establecer la clase de peón predeterminada](images/unreal-uxt/3-setpawn.PNG)

3.  Seleccione **Edit > Projects Settings** (Editar > Configuración de proyectos) y haga clic en **Maps & Modes** (Mapas y modos) en la lista de la izquierda. 
    * Expanda **Default Modes** (Modos predeterminados) y cambie **Default Game Mode** (Modo de juego predeterminado) a **MRGameMode**. 
    * Expanda **Default Maps** (Mapas predeterminados) y cambie **EditorStartupMap** y **GameDefaultMap** a **Main** (Principal). De este modo, cuando cierre el editor y vuelva a abrirlo o cuando juegue una partida, se seleccionará el mapa principal de forma predeterminada.

![Configuración del proyecto: mapas y modos](images/unreal-uxt/3-mapsandmodes.PNG)

Una vez que el proyecto se haya configurado completamente para la realidad mixta, está listo para pasar al siguiente tutorial y empezar a agregar datos proporcionados por el usuario a la escena. 

[Sección siguiente: 4. Creación de escenas interactivas](unreal-uxt-ch4.md)