---
title: 2. Inicialización de tu proyecto y primera aplicación
description: Parte 2 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 150fee721bb9cd72d287737aca4262bd87dccba8
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345735"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicialización de tu proyecto y primera aplicación

## <a name="overview"></a>Introducción

En este primer tutorial, comenzará con una nueva aplicación de Unreal para HoloLens 2. Incluirá agregar el complemento de HoloLens, crear e iluminar un nivel y rellenarlo con un tablero de juegos y una pieza de ajedrez. Usará recursos predefinidos para los materiales de los objetos y la pieza de ajedrez 3D, por lo que no deberá preocuparse por un modelado desde cero. Al final de este tutorial tendrá un lienzo en blanco listo para la realidad mixta.

Antes de continuar, asegúrese de que tiene todos los requisitos previos de la página [Introducción](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).

## <a name="objectives"></a>Objetivos
* Configuración de un proyecto de Unreal para el desarrollo de HoloLens
* Importación de recursos y configuración de una escena
* Creación de actores y eventos de nivel de script con planos técnicos

## <a name="creating-a-new-unreal-project"></a>Creación de un nuevo proyecto de Unreal
Lo primero que necesita es un proyecto con el que trabajar. Si esta es la primera vez que crea una aplicación de Unreal para HoloLens, deberá [descargar los archivos auxiliares](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) desde el iniciador de Epic.

1. Iniciar Unreal Engine

2. En **Games** (Juegos), seleccione **New Project Categories** (Nuevas categorías de proyecto) y haga clic en **Next** (Siguiente). 

![Selección de la plantilla del proyecto Games](images/unreal-uxt/2-gamestemplate.png)

3. Seleccione una plantilla **Blank** (En blanco) y haga clic en **Next** (Siguiente). 

![Seleccionar la plantilla en blanco](images/unreal-uxt/2-template.PNG)

4. Defina **C++** , **Scalable 3D or 2D, Mobile/Tablet** (Móvil o tableta escalable 3D o 2D) y **No Starter Content** (Sin contenido de inicio) como **Configuración del proyecto**. 
    * Elija una ubicación para guardarlo y haga clic en **Crear un proyecto**. 

> [!NOTE]
> Debe seleccionar un proyecto de C++ en lugar de un proyecto de plano técnico para compilar el complemento de herramientas de la experiencia del usuario, que configurará más adelante en la sección 4.

![Configuración del proyecto inicial](images/unreal-uxt/2-project-settings.PNG)

El proyecto deberá abrirse automáticamente en el editor de Unreal, lo que significa que está listo para la sección siguiente.

## <a name="enabling-required-plugins"></a>Habilitación de los complementos necesarios
Antes de empezar a agregar objetos a la escena, deberá habilitar dos complementos.

1. Abra **Edit > Plugins** (Editar > Complementos) y seleccione **Augmented Reality** (Realidad aumentada) en la lista opciones integradas. 
    * Desplácese hacia abajo hasta **HoloLens** y marque **Enabled** (Habilitado). 

![Habilitación de complementos de HoloLens](images/unreal-uxt/2-plugins.PNG)

2. Seleccione **Realidad virtual** en la lista opciones integradas. 
    * Desplácese hacia abajo hasta **Microsoft Windows Mixed Reality**, marque **Habilitado** y reinicie el editor. 

![Habilitación del complemento Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> Ambos complementos son necesarios para el desarrollo para HoloLens 2.

Después de esto, el nivel vacío está listo para llenarlo.

## <a name="creating-a-level"></a>Creación de un nivel
La siguiente tarea consiste en crear una configuración sencilla de un jugador con un punto inicial y un cubo para referencia y escala.

1. Seleccione **File > New Level** (Archivo > Nuevo nivel) y elija **Empty Level** (Nivel vacío). Ahora, la escena predeterminada en la ventanilla debe estar vacía.

2. Seleccione **Basic** (Básico) en la pestaña **Modes** (Modos) y arrastre **PlayerStart** a la escena. 
    * Establezca **Location** (Ubicación) en **X = 0**, **Y = 0** y **Z = 0** en la pestaña **Details** (Detalles). De este modo se establece al usuario en el centro de la escena cuando se inicia la aplicación.

![Ventanilla con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. Arrastre un **Cube** (Cubo) desde la pestaña **Basic** (Básico) a la escena. 
    * Establezca **Location** (Ubicación) en **X = 50**, **Y = 0** y **Z = 0**. Así, se coloca el cubo a 50 cm del jugador en el momento del inicio. 
    * Cambie **Scale** (Escala) a **X = 0,2**, **Y = 0,2** y **Z = 0,2** para reducir el cubo. 

No podrá ver el cubo a menos que agregue una luz a la escena, que es la última tarea antes de probar la escena.

4. Cambie a la pestaña **Ligths** (Luces) del panel **Modes** (Modos) y arrastre **Directional Light** (Luz direccional) a la escena. Coloque la luz sobre **PlayerStart** para que pueda verlo.

![Ventanilla con luz agregada](images/unreal-uxt/2-light.PNG)

5. Vaya a **File > Save Current** (Archivo > Guardar actual), asigne un nombre al nivel **Main** (Principal) y haga clic en **Save** (Guardar). 

Con la escena definida, presione **Play** (Jugar) en la barra de herramientas para ver el cubo en acción. Cuando haya terminado de admirar su trabajo, presione **Esc** para detener la aplicación.

![Cubo en la ventanilla](images/unreal-uxt/2-cube.PNG)

Ahora que la escena está configurada, puede empezar a agregar el panel de ajedrez y la pieza para completar el entorno de la aplicación.

## <a name="importing-assets"></a>Importación de recursos
La escena está un poco vacía en este momento, pero se solucionará al importar los recursos ya preparados al proyecto.

1. Descargue y descomprima la carpeta de recursos de [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).

2. Haga clic en **Add New > New Folder** (Agregar nuevo > Nueva carpeta) en **Content Browser** (Explorador de contenido) y asígnele el nombre **ChessAssets**. 
    * Haga doble clic en la nueva carpeta; ahí es donde importará los recursos 3D.

![Mostrar u ocultar el panel de orígenes](images/unreal-uxt/2-showhidesources.PNG)

3. Haga clic en **Import** (Importar) en **Content Browser** (Explorador de contenido), seleccione todos los elementos de la carpeta de recursos descomprimidos y haga clic en **Open** (Abrir). 
    * Esta carpeta contiene las mallas de objetos 3D para el tablero de ajedrez, las piezas en formato FBX y los mapas de textura en formato TGA que usará para los materiales.  

4. Cuando aparezca la ventana de opciones de importación de FBX, expanda la sección **Material** y cambie **Material Import Method** (Método de importación de material) a **Do Not Create Material** (No crear material).
    * Haga clic en **Import All** (Importar todo).

![Opciones de importación de FBX](images/unreal-uxt/2-nocreatemat.PNG)

Es todo lo que debe hacer para los recursos. El siguiente conjunto de tareas consiste en crear los bloques de creación de la aplicación con planos técnicos.

## <a name="adding-blueprints"></a>Adición de planos técnicos

1. Haga clic en **Add New > New Folder** (Agregar nuevo > Nueva carpeta) en **Content Browser** (Explorador de contenido) y asígnele el nombre **Explorador de contenido**. 

> [!NOTE]
> Los [planos técnicos](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) son recursos especiales que proporcionan una interfaz basada en nodos para crear nuevos tipos de actores y eventos de nivel de script. 

2. Haga doble clic en la carpeta **Blueprints** (Planos técnicos), haga clic con el botón derecho y seleccione **Blueprint Class** (Clase de plano técnico).         
    * Seleccione **Actor** y asigne el nombre **Board** al nuevo plano técnico. 

![Selecciona una clase principal para el plano técnico](images/unreal-uxt/2-bpparent.PNG)

El nuevo plano técnico **Board** ahora aparece en la carpeta **Blueprints** (Planos técnicos) como se muestra en la captura de pantalla siguiente. 

![Nuevo plano técnico Board](images/unreal-uxt/2-bpboard.PNG)

Está listo para empezar a agregar materiales a los objetos creados.

## <a name="working-with-materials"></a>Utilización de materiales
Los objetos que ha creado son de color gris de forma predeterminada, lo que no es muy alegre. La adición de materiales y mallas a los objetos es el último conjunto de tareas de este tutorial.

1. Haga doble clic en **Board** para abrir el editor de planos técnicos. 

2. Haga clic en **Add Component > Scene**  (Agregar componente > Escena) en el panel **Components** (Componentes) y asígnele el nombre **Root**. Observe que **Root** se muestra como un elemento secundario de **DefaultSceneRoot** en la siguiente captura de pantalla:

![Reemplazar la raíz](images/unreal-uxt/2-root-blueprint.PNG)


3. Haga clic y arrastre **Root** a **DefaultSceneRoot** para reemplazarlo y eliminar la esfera en la ventanilla. 

![Reemplazar la raíz](images/unreal-uxt/2-root.PNG)


4. Haga clic en **Add Component > Static Mesh** (Agregar componente > Malla estática) en el panel **Components** (Componentes) y asígnele el nombre **SM_Board**. Aparecerá como un objeto secundario en **Root**.

![Adición de una malla estática](images/unreal-uxt/2-sm-board.PNG)

4. Haga clic en **SM_Board**, desplácese hacia abajo hasta la sección **Static Mesh** (Malla estática) del panel **Details** (Detalles) y seleccione **ChessBoard** en la lista desplegable. 

![Malla del tablero en la ventanilla](images/unreal-uxt/2-sm-board-view.PNG)

5.  En el panel **Details** (Detalles), expanda la sección **Materials** (Materiales) y haga clic en **Create New Asset > Material** (Crear nuevo recurso > Material) en la lista desplegable. 
    * Asigne al material el nombre **M_ChessBoard** y guárdelo en la carpeta **ChessAssets**. 

![Crear un material nuevo](images/unreal-uxt/2-newmat.PNG)

6.  Haga doble clic en la imagen del material **M_ChessBoard** para abrir el editor de materiales. 

![Apertura del editor de materiales](images/unreal-uxt/2-material-editor.PNG)

7. En el editor de materiales, haga clic con el botón derecho y busque **Texture Sample** (Muestra de textura). 
    * Expanda la sección **Material Expression Texture Base** (Base de textura de expresión de material) del panel **Details** (Detalles) y defina **Texture** (Textura) en **ChessBoard_Albedo**. 
    * Arrastre la marca de salida de **RGB** a la marca de color base de **M_ChessBoard**. 

![Establecer el color de base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  Repita el paso anterior cuatro veces más para crear cuatro nodos de **Texture Sample** (Muestra de textura) con la siguiente configuración:
    * Establezca **Texture** (Textura) en **ChessBoard_AO** y vincule **RGB** a la marca de **Ambient Occlusion** (Oclusión ambiental).
    * Establezca **Texture** (Textura) en **ChessBoard_Metal** y vincule **RGB** a la marca de **Metallic** (Metálico). 
    * Establezca **Texture** (Textura) en **ChessBoard_Normal** y vincule **RGB** a la marca de **Normal**.
    * Establezca **Texture** (Textura) en **ChessBoard_Rough** y vincule **RGB** a la marca de **Roughness** (Rugosidad). 
    * Haga clic en **Guardar**. 

![Enlazar las texturas restantes](images/unreal-uxt/2-boardmat.PNG)

Asegúrese de que la configuración del material sea similar a la captura de pantalla anterior antes de continuar.

## <a name="populating-the-scene"></a>Rellenado de la escena
Si vuelve al plano técnico **Board**, verá que se ha aplicado el material que acaba de crear. Lo único que queda es configurar la escena. En primer lugar, cambie las siguientes propiedades para asegurarse de que el tablero tiene un tamaño razonable y que tiene el ángulo correcto cuando se coloca en la escena:
1.  Establezca **Scale** (Escala) en **(0,05, 0,05, 0,05)** y **Z Rotation** (Rotación Z) en **90**. 
    * Haga clic en **Compile** (Compilar) en la barra de herramientas superior, luego en **Save** (Guardar) y vuelva a la ventana principal. 

![Tablero de ajedrez con el material aplicado](images/unreal-uxt/2-chessboard.PNG)

2.  Haga clic con el botón derecho en **Cube > Edit > Delete** (Cubo > Editar > Eliminar) y arrastre **Board** desde **Content Browser** (Explorador de contenido) a la ventanilla. 
    * Establezca **Location** (Ubicación) en **X = 80**, **Y = 0** y **Z = 20**. 

3.  Haga clic en el botón **Play** (Jugar) para ver el nuevo tablero en el nivel. Presiona **Esc** para volver al editor. 

Ahora seguirá los mismos pasos para crear una pieza de ajedrez como hizo con el tablero:

1. Vaya a la carpeta **Blueprints** (Planos técnicos), haga clic con el botón derecho, seleccione **Blueprint Class** (Clase de plano técnico) y elija **Actor**. Asigne al actor el nombre **WhiteKing**.

2. Haga doble clic en **WhiteKing** para abrirlo en el editor de planos técnicos, haga clic en **Add Component > Scene** (Agregar componente > Escena) y asígnele el nombre **Root**. 
    * Arrastre y coloque **Root** en **DefaultSceneRoot** para reemplazarlo. 

3. Haga clic en **Add Component > Static Mesh** (Agregar componente > Malla estática) y asígnele el nombre **SM_King**. 
    * Establezca **Static Mesh** (Malla estática) en **Chess_King** y **Material** en un nuevo material denominado **M_ChessWhite** en el panel de detalles. 

4. Abra **M_ChessWhite** en el editor de materiales y enlace los siguientes nodos de **Texture Sample** (Muestra de textura) a lo siguiente:
    * Establezca **Texture** (Textura) en **ChessWhite_AO** y vincule **RGB** a la marca de **Ambient Occlusion** (Oclusión ambiental).
    * Establezca **Texture** (Textura) en **ChessWhite_Metal** y vincule **RGB** a la marca de **Metallic** (Metálico). 
    * Establezca **Texture** (Textura) en **ChessWhite_Metal** y vincule **RGB** a la marca de **Normal**.
    * Establezca **Texture** (Textura) en **ChessWhite_Rough** y vincule **RGB** a la marca de **Roughness** (Rugosidad). 
    * Haga clic en **Guardar**. 

El material de **M_ChessKing** debe parecerse a la siguiente imagen antes de continuar.

![Crear el material para el rey del ajedrez](images/unreal-uxt/2-chesskingmat.PNG)

Casi está, solo tiene que agregar la nueva pieza de ajedrez a la escena: 

1. Abra el plano técnico **WhiteKing**, cambie el valor de **Scale** (Escala) a **(0,05, 0,05, 0,05)** y de **Z Rotation** (Rotación Z) a **90**.
    * Compile y guarde el plano técnico y, a continuación, vuelva a la ventana principal. 

2.  Arrastre **WhiteKing** a la ventanilla, cambie al panel **World Outliner** (Esquematizador del mundo), arrastre **WhiteKing** a **Board** para convertirlo en un objeto secundario.

![World Outliner (Esquematizador del mundo)](images/unreal-uxt/2-child.PNG)

3.  En el panel **Details** (Detalles) en **Transform** (Transformar), establezca el valor de **Location** (Ubicación) de **WhiteKing** en **X = -26**, **Y = 4** y **Z = 0**.

Ya está. Haga clic en **Play** (Jugar) para ver el nivel rellenado en acción y presione **Esc** cuando esté listo para salir. En este tutorial se ha tratado una gran cantidad de información sobre la creación de un proyecto sencillo, pero el proyecto está listo para pasar a la siguiente parte de la serie: configuración de la realidad mixta. 

[Sección siguiente: 3. Configuración del proyecto para la realidad mixta](unreal-uxt-ch3.md)
