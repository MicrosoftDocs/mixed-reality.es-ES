---
title: Audio espacial en Unreal
description: Información general del complemento de audio espacial para Unreal Engine.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446816"
---
# <a name="spatial-audio-in-unreal"></a>Audio espacial en Unreal

## <a name="overview"></a>Introducción

A diferencia de la visión, los seres humanos escuchan el sonido envolvente en 360 grados. El sonido espacial emula el funcionamiento de la audición humana y proporciona las indicaciones necesarias para identificar las ubicaciones del sonido en el espacio real. Al agregar sonido espacial en las aplicaciones de realidad mixta, mejora el nivel de inmersión de la experiencia de los usuarios.  

El procesamiento de sonido espacial de alta calidad es complejo, por lo que HoloLens 2 incluye hardware dedicado para procesar esos objetos de sonido.  Para poder acceder a este soporte de procesamiento de hardware, debe instalar el complemento **MicrosoftSpatialSound** en su proyecto de Unreal. Este artículo le guiará a través de la instalación y configuración de ese complemento y le indicará recursos más detallados para usar el sonido espacial en Unreal Engine. 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>Instalación del complemento de sonido espacial de Microsoft 

El primer paso para agregar sonido espacial a su proyecto es instalar el complemento de sonido espacial de Microsoft, que puede buscar de la siguiente manera: 

1. Haga clic en **Editar > Complementos** y busque **MicrosoftSpatialSound** en el cuadro de búsqueda. 
2. Active la casilla **Habilitado** en el complemento **MicrosoftSpatialSound**. 
3. Reinicie el editor de Unreal mediante la opción **Reiniciar ahora** desde la página de complementos. 

> [!NOTE]
> Si todavía no lo ha hecho, deberá instalar los complementos de **Microsoft Windows Mixed Reality** y **HoloLens** siguiendo las instrucciones de la sección **[Inicialización del proyecto](unreal-uxt-ch2.md)** de nuestra serie de tutoriales de Unreal.

![Complemento de audio espacial de Unreal](images/unreal-spatial-audio-img-01.png)

Cuando se reinicia el editor, el proyecto ya está preparado.


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>Configuración del complemento de espacialización para la plataforma HoloLens 2
La configuración del complemento de espacialización se realiza por plataforma.  Puede habilitar el complemento de sonido espacial de Microsoft para HoloLens 2 de la siguiente manera:
1. Seleccione **Edit > Projects Settings** (Editar > Configuración del proyecto), desplácese a **Platforms** (Plataformas) y haga clic en **HoloLens**.
2. Expanda las propiedades **Audio** y establezca el campo **Spatialization Plugin** (Complemento de la espacialización) en **Microsoft Spatial Sound** (Sonido espacial de Microsoft).

![Complemento de espacialización para la plataforma HoloLens](images/unreal-spatial-audio-img-02.png)

Si va a obtener una vista previa de la aplicación en el editor de Unreal en un equipo de escritorio, deberá repetir los pasos anteriores para la plataforma **Windows**:

![Complemento de espacialización para la plataforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>Habilitación del audio espacial en la estación de trabajo
El audio espacial está deshabilitado de forma predeterminada en las versiones de escritorio de Windows. Puede habilitarlo de la siguiente manera:
* Haga clic con el botón derecho en el icono de **volumen** de la barra de tareas. 
    + Elija **Sonido espacial > Windows Sonic para auriculares** para obtener la mejor representación de lo que escuchará en HoloLens 2.

![Complemento de espacialización](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>Esta opción solo es necesaria si tiene previsto probar el proyecto en el editor de Unreal.

## <a name="creating-attenuation-objects"></a>Creación de objetos de atenuación
Después de instalar y configurar los complementos necesarios:
1. Busque un actor de **Ambient Sound** (Sonido ambiental) actor en la ventana **Place Actors** (Colocar actores) y arrástrelo a la ventana **Scene** (Escena).

![Adición de un actor de sonido ambiental](images/unreal-spatial-audio-img-07.png)

2. Convierta el actor de **Ambient Sound** (Sonido ambiental) en un elemento secundario de un elemento visual de la escena. 
    * Un actor de sonido ambiental no tiene ninguna representación visual de forma predeterminada, por lo que solo oirá un sonido de su posición en la escena. Al adjuntarlo a un elemento visual, el actor se muestra y se mueve como cualquier otro recurso.

3.  Haga clic con el botón derecho en **Content Browser** (Explorador de contenido) y seleccione **Create Advanced Asset -> Sounds -> Sound Attenuation** (Crear recurso avanzado -> Sonidos -> Atenuación de sonido):

![Creación de un recurso de atenuación de sonido](images/unreal-spatial-audio-img-06.png)

4. Haga clic con el botón derecho en el recurso **Sound Attenuation** (Atenuación de sonido) en la ventana **Content Browser** (Explorador de contenido) y seleccione la opción **Edit** (Editar) para abrir la ventana de propiedades.
    * Cambie el valor de **Spatialization Method** (Método de espacialización) a **Binaural**.

![Establecimiento del método de espacialización](images/unreal-spatial-audio-img-03.png)

5. Seleccione el actor de **Ambient Sound** (Sonido ambiental) y desplácese hacia abajo hasta la sección **Attenuation** (Atenuación) del panel **Details** (Detalles). 
    * Establezca la propiedad **Attenuation Settings** (Configuración de atenuación) en el recurso de **Sound Attenuation** (Atenuación de sonido) que creó.

![Establecimiento de la configuración de atenuación](images/unreal-spatial-audio-img-08.png)

6. Establezca la opción de **Sound Asset** (Recurso de sonido) que desea asociar al actor de sonido ambiental mediante la actualización de la propiedad **Sound** (Sonido) de dicho actor para especificar el archivo SoundAsset que se va a usar.

![Establecimiento del recurso de sonido](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> El archivo SoundAsset debe ser monoaural para que se pueda espacializar con el complemento de sonido espacial de Microsoft. Para buscar las propiedades del archivo de sonido, puede mantener el puntero sobre el recurso en la ventana Content Browser (Explorador de contenido), tal como se muestra en la captura de pantalla siguiente.

![Nuevo recurso de atenuación de sonido](images/unreal-spatial-audio-img-10.png)

Una vez configurado todo esto, el sonido ambiental se puede espacializar con el soporte de descarga de hardware dedicado en HoloLens 2.

## <a name="configuring-objects-for-spatialization"></a>Configuración de objetos para la espacialización
Trabajar con audio espacial significa responsabilizarse de administrar el comportamiento del sonido en un entorno virtual. El enfoque principal es crear objetos de sonido que parezcan más altos cuando el usuario esté cerca y más silenciosos cuando el usuario esté lejos. Esto se conoce como atenuación de sonido y hace que los sonidos se oigan como si estuvieran en una posición fija.

Todos los objetos de atenuación tienen valores modificables de:
* Distancia
* Espacialización
* Absorción de aire
* Foco del agente de escucha
* Envío de reverberación
* Oclusión

La [atenuación de sonido en Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) tiene detalles e información específica de la implementación en cada uno de estos temas.


## <a name="see-also"></a>Consulta también
* [Sonido espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [Diseño de sonido espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [MR Spatial 220: sonido espacial](https://docs.microsoft.com/windows/mixed-reality/holograms-220)