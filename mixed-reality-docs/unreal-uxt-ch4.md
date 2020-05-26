---
title: 4. Creación de escenas interactivas
description: Parte 4 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 2e4d26ed4e0b8199bfc629016aea688bd1c41ef8
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/18/2020
ms.locfileid: "83520030"
---
# <a name="4-making-your-scene-interactive"></a>4. Creación de escenas interactivas

En esta sección se presenta el complemento de código abierto UX Tools de Mixed Reality Toolkit, que proporciona un conjunto de herramientas para hacer que la escena sea interactiva fácilmente. Al final de esta sección, las piezas de ajedrez responderán a la entrada del usuario. 

## <a name="objectives"></a>Objetivos

* Incluir el complemento UX Tools de Mixed Reality Toolkit en el proyecto
* Agregar los actores de interacción con la mano a su alcance
* Crear y adjuntar manipuladores al tablero y las piezas de ajedrez 
* Usar la simulación de entrada para validar el proyecto

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>Descarga del complemento UX Tools de Mixed Reality Toolkit

1.  Clona o descarga y descomprime la versión más reciente del complemento UX Tools de MRTK del [repositorio de GitHub de UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases).

2.  En la carpeta raíz del proyecto de ajedrez, crea una nueva carpeta denominada "Plugins" (Complementos). Copia el complemento UXTools descomprimido en esta carpeta. Reinicia el editor de Unreal. 

![Crear una carpeta de complementos del proyecto](images/unreal-uxt/4-plugins.PNG)

3.  Después de reiniciar, si no ves el contenido del complemento UX Tools en el panel de orígenes, puede que tengas que hacer clic en **View Options > Show Plugin Content** (Opciones de vista > Mostrar contenido de complementos). Verás que el complemento UXTools proporciona una carpeta de contenido con punteros, simulación de entrada y un botón sencillo, así como una carpeta de clases de C++ con subcarpetas separadas por función.  

![Mostrar el contenido del complemento](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>Generar actores de interacción con la mano

1.  Para empezar, generemos actores de interacción con la mano de nuestro MRPawn para que 1) podamos visualizar MRPawn con un cursor en las puntas de los dedos índices del peón, 2) podamos proporcionar eventos de entrada manual articulados (y, por tanto, manipular directamente los actores) mediante el peón y 3) proporcionar eventos de entrada de interacción lejanos mediante un haz de mano al extender las palmas. Abre el plano técnico **MRPawn** y desplázate hasta **Event Graph** (Gráfico de eventos). 

2.  Arrastra la marca de ejecución del elemento BeginPlay del evento y suéltala para colocar un nuevo nodo. Selecciona el nodo **Spawn Actor from Class** (Generar actor a partir de clase). Haz clic en la lista desplegable situada junto a la marca **Class** (Clase) y busca **Uxt Hand Interaction Actor** (Actor de interacción con la mano de UXT). Arrastra la marca de ejecución del nodo de interacción con la mano de UXT SpawnActor, suéltala y busca la función **Set Hand** (Establecer mano) de la clase Uxt Hand Interaction Actor (Actor de interacción con la mano de UXT). Conecta el valor devuelto del nodo SpawnActor con la marca de destino del nodo Set Hand (Establecer mano) del actor de interacción con la mano en **Izquierda**. Genera un segundo **Uxt Hand Interaction Actor** (Actor de interacción con la mano de UXT), esta vez estableciendo la mano en **Right** (Derecha), de modo que cuando empiece el evento, se genere este actor en cada mano. 

![Generar actores de interacción con la mano de UXT](images/unreal-uxt/4-spawnactor.PNG)

3.  A continuación, debemos proporcionar a nuestros actores de interacción con la mano una transformación inicial a partir de la que generarse, así como un propietario. Arrastra la marca de las marcas de **Spawn Transform** (Generar transformación) y suéltala para colocar un nuevo nodo. Busca el nodo **Make Transform** (Crear transformación). Realmente, la transformación inicial no importa, ya que los actores de interacción con la mano saltarán a nuestras manos en cuanto estén visibles (código que ya está escrito para nosotros en el complemento UX Tools). De lo contrario, desaparecerán. Sin embargo, la función SpawnActor requiere una transformación como entrada para evitar un error del compilador, por lo que dejaremos los valores predeterminados de Make Transform (Crear transformación) como están. Arrastra **Return Value** (Valor devuelto) de Make Transform (Crear transformación) a la transformación de generación del actor de interacción de la otra mano. 

4.  Haz clic en la **flecha hacia abajo** en la parte inferior de los nodos SpawnActor para revelar la marca **Owner** (Propietario). Arrastra la marca de las marcas de **Owner** (Propietario) y suéltala para colocar un nuevo nodo. Busca “self” (propio) y selecciona la variable **Get a reference to self** (Obtener una referencia a un elemento propio). Crea un vínculo entre el nodo de referencia de objetos propios y la marca del propietario del actor de interacción con la mano, también. No dudes en arrastrar los nodos para que el plano técnico resulte más fácil de leer. **Compila**, **guarda** y vuelve a la ventana principal. 

![Completar la configuración del actor de interacción con la mano de UXT](images/unreal-uxt/4-fingerptrs.PNG)

Para obtener más información sobre el actor de interacción manual proporcionado en el complemento UX Tools de MRTK, consulta la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html) oficial.

## <a name="attach-manipulators"></a>Adjuntar manipuladores

1.  A continuación, adjuntaremos manipuladores a nuestros actores del rey y el tablero de ajedrez. Un manipulador es un componente que responde a la entrada manual articulada y se puede capturar, girar e interpretar. Al aplicar la transformación del manipulador a la de un actor, los actores se pueden manipular directamente. 

2.  Abre el plano técnico Board. En el panel **Components** (Componentes), haz clic en **Add Component** (Agregar componente) y busca **Uxt Generic Manipulator** (Manipulador genérico de UXT). En el panel Details (Detalles), encontrarás una sección titulada **Generic Manipulator** (Manipulador genérico), donde puedes establecer si quieres habilitar la manipulación con una mano o con dos, el modo de rotación y el suavizado. No dudes en seleccionar los modos que quieras y, a continuación, **compila** y **guarda** el tablero. 

![Agregar un manipulador genérico](images/unreal-uxt/4-addmanip.PNG)

![Establecer el modo](images/unreal-uxt/4-setrotmode.PNG)

3.  Repite los pasos anteriores para el actor WhiteKing.

Para obtener más información sobre los componentes del manipulador del complemento UX Tools de MRTK, visita la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html) oficial.

## <a name="test-out-your-scene-with-simulated-hands"></a>Prueba de la escena con manos simuladas

1.  En la ventana principal, presiona **Play** (Jugar). Deberías ver las dos manos de la malla que proporciona el complemento UX Tools de MRTK, con haces de mano que se extienden desde la palma de cada mano. 

![Manos simuladas en la ventanilla](images/unreal-uxt/4-handsim.PNG)

2.  Para controlar la **mano derecha**, mantén presionado el botón **Alt izquierdo**. Mueve el ratón para mover la mano. Desplázate con la **rueda del ratón** para mover la mano **hacia adelante** o **hacia atrás**. Haz clic con el botón principal del ratón para **reducir** o clic en el botón central del ratón para **tocar**.

3.  Para controlar la **mano izquierda**, mantén presionado el botón **tecla Mayús**. Los controles para mover la mano izquierda son los mismos que para la mano derecha. 

4.  Ahora, prueba a usar las manos simuladas para seleccionar, mover y colocar el rey blanco del ajedrez. También puedes manipular el tablero. Experimenta con la interacción de cerca y de lejos: observa que, cuando las manos se acercan lo suficiente como para agarrar el tablero y el rey directamente, el haz de mano desaparece y se reemplaza con un cursor en forma de dedo en la punta del índice. 

Para obtener más información sobre la característica de manos simuladas que ofrece el complemento UX Tools de MRTK, visita la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html) oficial.

[Sección siguiente: 5. Adición de un botón y restablecimiento de las ubicaciones de las piezas](unreal-uxt-ch5.md)
