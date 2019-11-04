---
title: 'Caso práctico: creación de HoloSketch, un diseño espacial y una aplicación de boceto de experiencia de usuario para HoloLens'
description: HoloSketch es un diseño espacial en el dispositivo y una herramienta de boceto de la experiencia del usuario para HoloLens que ayuda a crear experiencias holográficas.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, boceto, aplicación
ms.openlocfilehash: d6d22aae7709bcc1a33b142a100d1a0f9645d3cc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436944"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Caso práctico: creación de HoloSketch, un diseño espacial y una aplicación de boceto de experiencia de usuario para HoloLens

HoloSketch es un diseño espacial en el dispositivo y una herramienta de boceto de la experiencia del usuario para HoloLens que ayuda a crear experiencias holográficas. HoloSketch funciona con un teclado y un mouse Bluetooth emparejados, así como con comandos de gestos y voz. El objetivo de HoloSketch es proporcionar una sencilla herramienta de diseño de la experiencia de usuario para la visualización y la iteración rápidas.

![HoloSketch: una aplicación de diseño espacial y de boceto de la experiencia de usuario para HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: aplicación de diseño espacial y de boceto de la experiencia de usuario para HoloLens*

![una sencilla herramienta de diseño de la experiencia del usuario para una visualización rápida e iteración.](images/holosketch-image-02.png)<br>
*Una herramienta de diseño de experiencia de usuario sencilla para una visualización rápida e iteración*

## <a name="features"></a>Características

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitivas para estudios rápidos y creación de prototipos de escalado

![Usar formas primitivas](images/holosketch-primitives-giphy.gif)

Use formas primitivas para los estudios y la creación de prototipos de escalado rápido.

### <a name="import-objects-through-onedrive"></a>Importar objetos a través de OneDrive

![importar objetos](images/holosketch-importobjects-giphy.gif)

Importe imágenes PNG/JPG o objetos FBX 3D (requiere empaquetado en Unity) en el espacio de realidad mixta a través de OneDrive.

### <a name="manipulate-objects"></a>Manipular objetos

![manipular objetos](images/manipulate-objects-640px.jpg)

Manipular objetos (Move/Rotate/Scale) con una interfaz de objeto 3D conocida.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, Mouse/teclado, gestos y comandos de voz

![admite Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch admite comandos de mouse/teclado, gestos y comandos de voz de Bluetooth.

## <a name="background"></a>Background

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importancia de experimentar el diseño en el dispositivo

Al diseñar algo para HoloLens, es importante experimentar el diseño en el dispositivo. Uno de los mayores desafíos en el diseño de aplicaciones de realidad mixta es que es difícil obtener el sentido de la escala, la posición y la profundidad, especialmente a través de los bocetos 2D tradicionales.

### <a name="cost-of-2d-based-communication"></a>Costo de la comunicación basada en 2D

Para comunicar de forma eficaz los flujos y escenarios de la experiencia de usuario a otros, un diseñador puede acabar invirtiendo mucho tiempo en crear recursos mediante herramientas tradicionales de 2D como Illustrator, Photoshop y PowerPoint. Estos diseños 2D suelen requerir un esfuerzo adicional para convertirlos en 3D. En esta traducción se pierden algunas ideas de 2D a 3D.

### <a name="complex-deployment-process"></a>Proceso de implementación complejo

Dado que la realidad mixta es un nuevo lienzo para nosotros, implica una gran cantidad de iteración de diseño y de prueba y error por su naturaleza. En el caso de los diseñadores que no están familiarizados con herramientas como Unity y Visual Studio, no es fácil poner nada en HoloLens. Normalmente tiene que seguir el proceso siguiente para ver la ilustración 2D/3D en el dispositivo. Esta era una gran barrera para diseñadores que recorren ideas y escenarios rápidamente.

![proceso de implementación complejo](images/holosketch-image-03-1000px.png)<br>
*Proceso de implementación*

### <a name="simplified-process-with-holosketch"></a>Proceso simplificado con HoloSketch

Con HoloSketch, queríamos simplificar este proceso sin involucrar las herramientas de desarrollo y el emparejamiento del portal de dispositivos. Con OneDrive, los usuarios pueden colocar fácilmente activos 2D/3D en HoloLens.

![proceso simplificado con HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Proceso simplificado con HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Fomento de soluciones y pensamiento de diseño de tres dimensiones

Pensamos que esta herramienta proporciona a los diseñadores una oportunidad para explorar soluciones en un espacio realmente tridimensional y no estar atascadas en 2D. No tienen que preocuparse por crear un fondo 3D para su interfaz de usuario, ya que el fondo es el mundo real en el caso de HoloLens. HoloSketch abre una forma para que los diseñadores exploren fácilmente el diseño 3D en HoloLens.

## <a name="get-started"></a>Comenzar

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Cómo importar imágenes 2D (JPG/PNG) en HoloSketch

* Cargue imágenes JPG/PNG en la carpeta de OneDrive "Documents/HoloSketch".
* En el menú de OneDrive de HoloSketch, podrá seleccionar y colocar la imagen en el entorno.

![importar imágenes 2D](images/import-2d-images-1000px.jpg)<br>
*Importación de imágenes y objetos 3D a través de OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Cómo importar objetos 3D en HoloSketch

Antes de cargar en su carpeta de OneDrive, siga los pasos que se indican a continuación para empaquetar los objetos 3D en un paquete de recursos de Unity. Con este proceso puede importar los archivos FBX/OBJ del software 3D, como Maya, Cinema 4D y Microsoft Paint 3D.

>[!IMPORTANT]
>Actualmente, la creación de paquetes de activos es compatible con la versión de Unity 5.4.5 F1.

1. Descargue y abra el proyecto de Unity ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Este proyecto de Unity incluye el script para la generación de recursos de agrupación.
2. Cree un nuevo GameObject.
3. Asigne el nombre GameObject a la base de contenido.
4. En el panel Inspector, haga clic en ' Agregar componente ' y en Agregar ' Box Colisionador '. 

   ![En el panel Inspector, haga clic en ' Agregar componente ' y en Agregar ' Box Colisionador '](images/holosketch-10a-assetbundles-1000px.png)
   
   ![En el panel Inspector, haga clic en ' Agregar componente ' y en Agregar ' Box Colisionador ' #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importe el archivo FBX 3D arrastrándolo al panel Proyecto.
6. Arrastre el objeto al panel jerarquía **bajo el nuevo GameObject**.

   ![Arrastre el objeto al panel jerarquía bajo el nuevo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Ajuste la dimensión del Colisionador si no coincide con el objeto. Gire el objeto al **eje Z de**la esfera.

   ![Ajuste la dimensión del Colisionador si no coincide con el objeto.](images/holosketch-13-assetbundles-1000px.png)

8. Arrastre el objeto desde el panel jerarquía hasta el panel Proyecto para **convertirlo en recurso prefabricado**.
9. En la parte inferior del panel Inspector, haga clic en la lista desplegable, crear y asignar un nuevo nombre único. En el ejemplo siguiente se muestra cómo agregar y asignar ' brownchair ' para el nombre de AssetBundle. 

   ![En la parte inferior del panel Inspector, haga clic en la lista desplegable y asigne un nuevo nombre único.](images/holosketch-14-assetbundles-1000px.png)

10. Preparar una imagen en miniatura para el objeto de modelo. 
   ![arrastre una imagen al panel Proyecto y asigne el nombre usado para el objeto.](images/holosketch-15-assetbundles-1000px.png)

11. Cree una carpeta denominada ' Assetbundles ' en la carpeta ' Asset ' del proyecto de Unity.

12. En el menú activos, seleccione ' compilar AssetBundles ' para generar el archivo. 
   ![en el menú activos, seleccione ' compilar AssetBundles ' para generar el archivo.](images/holosketch-15a-assetbundles.png)


13. **Cargue el archivo generado en la carpeta/Files/Documents/HoloSketch en OneDrive.** Cargue solo el archivo asset_unique_name. No es necesario cargar los archivos de manifiesto o el archivo AssetBundles. <br>
![agregar archivos a archivos/documentos/HoloSketch/carpeta](images/holosketch-onedriveupload-1000px.png)
![verá el objeto 3D agregado en el menú de OneDrive de HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Cómo manipular los objetos

HoloSketch admite la interfaz tradicional que se usa ampliamente en el software 3D. Puede usar la acción de desplazar, girar y escalar los objetos con gestos y un mouse. Puede cambiar rápidamente entre diferentes modos con voz o teclado.

### <a name="object-manipulation-modes"></a>Modos de manipulación de objetos

![cómo manipular los objetos](images/holosketch-image-06-1000px.png)<br>
*Cómo manipular los objetos*

### <a name="contextual-and-tool-belt-menus"></a>Menús contextuales y cinturón de herramientas

**Usar el menú contextual**

Doble aire Puntee para abrir el menú contextual. 

Elementos de menú:
* **Superficie de diseño:** Se trata de un sistema de cuadrícula 3D en el que puede diseñar varios objetos y administrarlos como un grupo. Haga doble punteo en la superficie de diseño para agregarle objetos.
* **Primitivas:** Use cubos, esferas, cilindros y conos para estudios en masa.
* **OneDrive:** Abra el menú de OneDrive para importar objetos.
* **Ayuda:** Muestra la pantalla de ayuda.

![menú contextual](images/holosketch-image-07.png)<br>
*Menú contextual*

**Usar el menú de la herramienta cinturón**

La escena de movimiento, giro, escala, guardado y carga está disponible en el menú de cinturón de herramientas. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Usar comandos de teclado, gestos y voz

![comandos de teclado, gestos y voz](images/holosketch-image-08-1000px.png)<br>
*Teclado, gestos y comandos de voz*

## <a name="download-the-app"></a>Descarga de la aplicación

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Descargue e instale la aplicación HoloSketch de forma gratuita desde el Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemas conocidos
* Actualmente se admite la creación de paquetes de activos con la **versión de Unity 5.4.5 F1.**
* En función de la cantidad de datos en OneDrive, la aplicación podría aparecer como si se hubiera detenido mientras se cargaba el contenido de OneDrive
* Actualmente, la característica de guardar y cargar solo admite objetos primitivos
* Los menús texto, sonido, vídeo y foto están deshabilitados en el menú contextual
* El botón reproducir del menú del cinturón de herramientas borra la Gizmos de manipulación.

## <a name="sharing-your-sketches"></a>Compartir bocetos

Puede usar la característica de grabación de vídeo de HoloLens diciendo "Hola Cortana, iniciar/detener grabación". Presione la tecla subir/bajar volumen para tomar una foto del boceto.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>@Microsoft del diseñador de la experiencia del usuario</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>@Microsoft para desarrolladores</td>
</tr>
</table> 
