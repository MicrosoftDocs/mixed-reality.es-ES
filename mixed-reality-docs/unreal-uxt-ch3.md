---
title: 3. Configuración del proyecto para la realidad mixta
description: Parte 3 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840624"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Configuración del proyecto para la realidad mixta

En esta sección se te orienta a lo largo del proceso de configuración de la aplicación para el desarrollo para realidad mixta. 

## <a name="objectives"></a>Objetivos

* Entender cómo configurar un proyecto de realidad mixta con ARSessionConfig, Pawn y GameMode

## <a name="configure-the-session"></a>Configuración de la sesión

1. En el explorador de contenido, vuelve a la carpeta **Content** (Contenido). Haz clic en **Add New > Miscellaneous > Data Asset** (Agregar nuevo > Varios > Recursos de datos). 

2. Elige **ARSessionConfig** como clase y haz clic en **Select** (Seleccionar). Asigna al recurso el nombre "ARSessionConfig".

![Crear un recurso de datos](images/unreal-uxt/3-createasset.PNG)

3. Haz doble clic en ARSessionConfig para abrirlo. El recurso de datos ARSessionConfig contiene una serie de valores de AR útiles, como el mapeo espacial y la oclusión. Para obtener más información sobre ARSessionConfig, echa un vistazo a la documentación de Unreal Engine sobre [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html). Para nuestra aplicación de ajedrez, no es necesario modificar la configuración, así que solo tienes que seleccionar **Save** (Guardar) y volver a la ventana principal. 

![Configuración de sesión de AR](images/unreal-uxt/3-arsessionconfig.PNG)

4. En la barra de herramientas situada encima de la ventanilla, haz clic en **Blueprints > Open Level Blueprint** (Planos técnicos > Abrir plano técnico de nivel). El plano técnico de nivel es un plano especial que actúa como un gráfico de eventos global de nivel superior. Vamos a iniciar una sesión de AR aquí, de modo que la configuración de la sesión de AR se aplique al principio del nivel.  

5. Saca el modo de ejecución **Event BeginPlay** (Event BeginPlay) y suéltalo. Busca el nodo **Start AR Session** (Iniciar sesión de AR). Haz clic en **Session Config** (Configuración de sesión) y selecciona el recurso **ARSessionConfig** que acabas de crear. Selecciona **Compile** (Compilar) y, a continuación, **Save** (Guardar). Vuelve a la ventana principal.

![Iniciar sesión de AR](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>Creación de un peón

1.  En la carpeta Content (Contenido), crea un nuevo plano técnico que herede de **DefaultPawn**. En Unreal, un peón representa al usuario en el juego o, en este caso, la experiencia de HoloLens 2. Cambia el nombre del nuevo peón a "MRPawn" y haz doble clic en él para abrirlo. 

![Crear un nuevo peón que herede de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

2.  De forma predeterminada, el peón tiene un componente de malla y uno de colisión, ya que, en la mayoría de los proyectos de Unreal, los peones controlados por el usuario son objetos sólidos que colisionan con otros componentes. En esta situación, dado que el usuario es el peón, queremos poder realizar el paso a través de hologramas sin generar colisiones. En el panel Components (Componentes), selecciona **CollisionComponent**. En el panel Details (Detalles), desplázate hacia abajo hasta la sección Collision (Colisión) y haz clic en la lista desplegable junto a Collision Presets (Valores preestablecidos de colisión). Cámbialo de Pawn (Peón) a **NoCollision**. Haz lo mismo para **MeshComponent**. **Compila** y, a continuación, **guarda** el plano técnico. Vuelve a la ventana principal. 

![Ajustar los valores preestablecidos de colisión del peón](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>Creación de un modo de juego

1.  En la carpeta Content (Contenido) del explorador de contenido, crea un nuevo plano técnico con la **Game Mode Base** (Base del modo de juego) principal. Asígnale el nombre MRGameMode y haz doble clic en él para abrirlo. En Unreal, el modo de juego determina una serie de opciones de configuración para el juego o la experiencia, incluido el peón predeterminado que se usará. 

![MRGameMode en el explorador de contenido](images/unreal-uxt/3-gamemode.PNG)

2.  En el panel de detalles, busca la sección Classes (Clases). Cambia la clase de peón predeterminada de DefaultPawn a la **MRPawn** que acaba de crear. Selecciona **Compile** (Compilar) y, a continuación, **Save** (Guardar). Vuelve a la ventana principal. 

![Establecer la clase de peón predeterminada](images/unreal-uxt/3-setpawn.PNG)

3.  El último paso en la configuración del proyecto consiste en indicar a Unreal que debe usar de forma predeterminada MRGameMode. Ve a la sección **Edit > Projects Settings > Maps & Modes** (Editar > Configuración de proyectos > Mapas y modos), en Projects (Proyectos). En la sección Default Modes (Modos predeterminados), haz clic en la lista desplegable y elige **MRGameMode**. En la sección Default Maps (Mapas predeterminados) que hay justo a continuación, cambia **EditorStartupMap** y **GameDefaultMap** a **Main** (Principal). De este modo, cuando cierres el editor y vuelvas a abrirlo, se seleccionará el mapa principal de forma predeterminada. Del mismo modo, al reproducir el juego, el mapa principal será el nivel que se inicie. 

![Configuración del proyecto: mapas y modos](images/unreal-uxt/3-mapsandmodes.PNG)

[Sección siguiente: 4. Creación de escenas interactivas](unreal-uxt-ch4.md)