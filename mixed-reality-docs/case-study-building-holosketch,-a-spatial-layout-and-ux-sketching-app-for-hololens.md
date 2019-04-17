---
title: 'Caso práctico: creación HoloSketch, un diseño espacial y UX esbozo app para HoloLens'
description: HoloSketch es un diseño espacial en el dispositivo y UX esbozo herramienta para HoloLens ayudar a crear experiencias holográficas.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, esbozar, aplicación
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600137"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Caso práctico: creación HoloSketch, un diseño espacial y UX esbozo app para HoloLens

HoloSketch es un diseño espacial en el dispositivo y UX esbozo herramienta para HoloLens ayudar a crear experiencias holográficas. HoloSketch funciona con un comandos de teclado y mouse, así como los gestos y voz de Bluetooth emparejados. El propósito de HoloSketch es proporcionar una herramienta de diseño de experiencia de usuario sencilla para la iteración y visualización rápida.

![HoloSketch: Un diseño espacial y UX esbozo app para HoloLens.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: espacial diseño y UX esbozo app para HoloLens*

![Una herramienta de diseño de experiencia de usuario sencilla visualización rápida e iteración.](images/holosketch-image-02.png)<br>
*Una herramienta de diseño de experiencia de usuario sencilla visualización rápida e iteración*

## <a name="features"></a>Características

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitivas de estudios de rápido y creación de prototipos de escala

![Uso de primitivas formas](images/holosketch-primitives-giphy.gif)

Usar formas de primitivas de estudios massing rápidos y creación de prototipos de escala.

### <a name="import-objects-through-onedrive"></a>Importar objetos a través de OneDrive

![importar objetos](images/holosketch-importobjects-giphy.gif)

Importar objetos 3D de FBX o de imágenes PNG o JPG (requiere empaquetado en Unity) en el espacio de realidad mixta mediante OneDrive.

### <a name="manipulate-objects"></a>Manipular objetos

![manipulación de objetos](images/manipulate-objects-640px.jpg)

Manipular objetos (mover o girar/escala) con una interfaz familiar objeto 3D.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse y teclado, gestos y comandos de voz

![es compatible con Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch es compatible con Bluetooth mouse/teclado, gestos y comandos de voz.

## <a name="background"></a>Background

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importancia de experimentar el diseño en el dispositivo

Al diseñar algo para HoloLens, es importante experimentar el diseño en el dispositivo. Uno de los mayores desafíos de diseño de aplicaciones de realidad mixta es que resulta difícil de obtener el sentido de escala, la posición y la profundidad, especialmente a través de dibujos 2D tradicionales.

### <a name="cost-of-2d-based-communication"></a>Comunicación basada en el costo de 2D

Para comunicar de forma eficaz los flujos de experiencia de usuario y escenarios a otros usuarios, un diseñador puede acabar dedicar mucho tiempo en crear activos mediante las herramientas tradicionales de 2D como Illustrator, Photoshop y PowerPoint. Estos diseños 2D a menudo requieren un esfuerzo adicional para convertirlos en 3D. En esta traducción se pierden algunas ideas, de 2D a 3D.

### <a name="complex-deployment-process"></a>Proceso de implementación complejos

Puesto que la realidad mixta es un nuevo lienzo para nosotros, implica una gran cantidad de iteración de diseño y de prueba y error por su naturaleza. Diseñador que no están familiarizados con herramientas como Unity y Visual Studio, no es fácil poner algo en HoloLens. Normalmente, tendrá que pasar por el proceso siguiente para ver ilustraciones 2D o 3D en el dispositivo. Esto era una barrera grande para los diseñadores de iterar rápidamente en las ideas y escenarios.

![Proceso de implementación complejos](images/holosketch-image-03-1000px.png)<br>
*Proceso de implementación*

### <a name="simplified-process-with-holosketch"></a>Proceso simplificado con HoloSketch

Con HoloSketch, queríamos simplificar este proceso sin necesidad de herramientas de desarrollo y el dispositivo de emparejamiento portal. Uso de OneDrive, los usuarios pueden poner fácilmente activos 2D o 3D en HoloLens.

![Proceso simplificado con HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Proceso simplificado con HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Fomento de soluciones y pensar en diseño tridimensional

Pensamos que esta herramienta le proporcionaría los diseñadores una oportunidad para explorar soluciones en un espacio tridimensional realmente y no esté bloqueado en 2D. No tienen que pensar en crear un plano 3D para su interfaz de usuario, ya que el fondo es el mundo real en el caso de Hololens. Abre una manera para que los diseñadores explorar fácilmente el diseño 3D en Hololens HoloSketch.

## <a name="get-started"></a>Comenzar

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Cómo importar imágenes en 2D (JPG/PNG) en HoloSketch

* Cargar imágenes JPG/PNG en su carpeta de OneDrive ' Documentos/HoloSketch'.
* En el menú de OneDrive en HoloSketch, podrá seleccionar y coloque la imagen en el entorno.

![Importación de imágenes en 2D](images/import-2d-images-1000px.jpg)<br>
*Importación de imágenes y objetos 3D a través de OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Cómo importar objetos 3D en HoloSketch

Antes de cargarlo en la carpeta de OneDrive, siga los pasos siguientes para empaquetar los objetos 3D en un conjunto de activos de Unity. Mediante este proceso puede importar los archivos OBJ y FBX de software 3D, como Maya, cine 4D y Microsoft Paint 3D.

>[!IMPORTANT]
>Actualmente, la creación de la agrupación de recursos es compatible con Unity versión 5.4.5f1.

1. Descargue y abra el proyecto de Unity ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Este proyecto de Unity incluye la secuencia de comandos para la generación de activos de agrupación.
2. Cree un nuevo GameObject.
3. Nombre el GameObject según el contenido.
4. En el panel del Inspector, haga clic en 'Agregar componente' y agregue 'Colisionador de cuadro'. 

   ![En el panel del Inspector, haga clic en 'Agregar componente' y agregue 'Colisionador de cuadro'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![En el panel del Inspector, haga clic en 'Agregar componente' y agregue 'Colisionador de cuadro' #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importar el archivo FBX 3D arrastrándolo al panel de proyecto.
6. Arrastre el objeto en el panel de la jerarquía **en su nuevo GameObject**.

   ![Arrastre el objeto en el panel de jerarquía en su nuevo GameObject](images/holosketch-12-assetbundles-1000px.png)

7. Ajuste la dimensión colisionador si no coincide con el objeto. Girar el objeto al que se enfrentan a **z**.

   ![Ajustar la dimensión colisionador si no coincide con el objeto.](images/holosketch-13-assetbundles-1000px.png)

8. Arrastre el objeto desde el panel de la jerarquía al panel de proyecto para **hacerla prefabricado**.
9. En la parte inferior del panel del inspector, haga clic en la lista desplegable, cree y asigne un nuevo nombre único. Ejemplo siguiente muestra cómo agregar y asignar 'brownchair' para el nombre AssetBundle. 

   ![En la parte inferior del panel del inspector, haga clic en la lista desplegable y asigne un nuevo nombre único.](images/holosketch-14-assetbundles-1000px.png)

10. Preparar una imagen en miniatura para el objeto de modelo. 
   ![Arrastre una imagen en el panel de proyecto y asigne el nombre usado para el objeto.](images/holosketch-15-assetbundles-1000px.png)

11. Cree una carpeta denominada 'Assetbundles' en carpeta de 'Activo' del proyecto de Unity.

12. En el menú de recursos, seleccione compilar AssetBundles para generar el archivo. 
   ![En el menú de recursos, seleccione compilar AssetBundles para generar el archivo.](images/holosketch-15a-assetbundles.png)


13. **Cargue el archivo generado en la carpeta /Files/Documents/HoloSketch en OneDrive.** Cargue el archivo asset_unique_name solo. No es necesario cargar los archivos de manifiesto o archivo AssetBundles. <br>
![Agregar archivos a los archivos/documentos/HoloSketch/carpeta](images/holosketch-onedriveupload-1000px.png)
![, verá que se ha agregado el objeto 3D en el menú de OneDrive del HoloSketch](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Cómo manipular los objetos

HoloSketch es compatible con la interfaz tradicional que se usa ampliamente en software 3D. Puede mover, girar, escalar los objetos con los gestos y un mouse. Puede cambiar rápidamente entre los distintos modos con voz o el teclado.

### <a name="object-manipulation-modes"></a>Modos de manipulación de objetos

![Cómo manipular los objetos](images/holosketch-image-06-1000px.png)<br>
*Cómo manipular los objetos*

### <a name="contextual-and-tool-belt-menus"></a>Menús contextuales y cinturón de herramientas

**Mediante el menú Contextual**

Pulsar en el aire dobles para abrir el menú Contextual. 

Elementos de menú:
* **Superficie de diseño:** Esto es un sistema 3D de cuadrícula donde puede distribuir varios objetos y administrarlos como un grupo. Derivación de aire doble en la superficie de diseño para agregar objetos a él.
* **Elementos primitivos:** Utilice los cubos, esferas, cilindros y conos para massing prácticos.
* **OneDrive:** Abra el menú de OneDrive para importar objetos.
* **Ayuda:** Muestra la pantalla de ayuda.

![Menú contextual](images/holosketch-image-07.png)<br>
*Menú contextual*

**Mediante el menú de cinturón de herramienta**

Mover, girar, escalar, guardar y cargar escena están disponibles en el menú de cinturón de herramienta. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Uso del teclado, gestos y comandos de voz

![Teclado, gestos y comandos de voz](images/holosketch-image-08-1000px.png)<br>
*Teclado, gestos y comandos de voz*

## <a name="download-the-app"></a>Descargar la aplicación

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Descargue e instale la aplicación HoloSketch de forma gratuita desde la Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemas conocidos
* Actualmente se admite la creación de la agrupación de recursos con **5.4.5f1 de versión de Unity.**
* Según la cantidad de datos en OneDrive, la aplicación podría aparecer como si se ha detenido al cargar el contenido de OneDrive
* Actualmente, guardar y cargar la característica solo admite objetos primitivos
* Los menús de texto, sonido, vídeo y fotografías están deshabilitados en el menú contextual
* El botón Reproducir en el menú herramienta cinturón borra el gizmos manipulación

## <a name="sharing-your-sketches"></a>Uso compartido de los dibujos

Puede usar la característica de grabación de vídeo en HoloLens diciendo: "Hola Cortana, iniciar o Detener grabación '. Presione la tecla conjuntamente para tomar una foto del boceto de arriba/abajo del volumen.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Diseñador UX @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Para desarrolladores @Microsoft</td>
</tr>
</table> 
