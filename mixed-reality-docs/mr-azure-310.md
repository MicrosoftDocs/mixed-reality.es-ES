---
title: El Sr. y 310 Azure - detección de objetos
description: Complete este curso para obtener información sobre cómo entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares y su posición en el mundo real desde dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: objeto de Azure, visión personalizada, detección, mixto en realidad, academy, unity, tutorial, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597648"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

# <a name="mr-and-azure-310-object-detection"></a>El Sr. y Azure 310: Detección de objetos

En este curso, aprenderá a reconocer contenido visual personalizado y su posición dentro de una imagen proporcionada, espacial con Azure Custom Vision capacidades "Detección de objetos" en una aplicación de realidad mixta.

Este servicio, podrá entrenar un modelo de aprendizaje automático mediante imágenes de objeto. A continuación, usará el modelo entrenado para reconocer objetos similares y aproximarse a su ubicación en el mundo real, tal como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara de conectarse a un PC para inmersivos (VR).

![resultado del curso](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision, detección de objetos** es un Service Microsoft que permite a los desarrolladores crear clasificadores de imagen personalizada. Estos clasificadores, a continuación, pueden utilizarse con las nuevas imágenes para detectar objetos dentro de esa imagen, proporcionando **los límites del cuadro** dentro de la imagen en Sí. El servicio proporciona un portal fácil de usar, sencillo y en línea para simplificar este proceso. Para obtener más información, visite los vínculos siguientes:

* [Página de Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Límites y cuotas](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:

1. El usuario podrá *que mirar* en un objeto que ha entrenado mediante Azure Custom Vision Service, detección de objetos. 
2. El usuario usará el *pulse* gesto para capturar una imagen de lo están mirando.
3. La aplicación enviará la imagen a Azure Custom Vision Service.
4. Habrá una respuesta desde el servicio que se mostrará el resultado del reconocimiento como texto de espacio global. Esto se logrará mediante la utilización espacial de seguimiento de la Microsoft HoloLens, como una manera de entender la posición global del objeto reconocido y, a continuación, usar el *etiqueta* asociados con lo que se detecta en la imagen, a Escriba el texto de etiqueta.

El curso también cubrirá manualmente cargar imágenes, crear etiquetas, y el servicio, para que reconozca diferentes entrenamiento objetos (en el ejemplo proporcionado, una taza), por establecer el *cuadro de límite* dentro de la imagen que envíe. 

> [!IMPORTANT]
> Después de la creación y uso de la aplicación, el desarrollador debe navegar hasta Azure Custom Vision Service, identificar las predicciones realizadas por el servicio y determinar si era correctas o no (a través del etiquetado nada del servicio perdió, y ajustar el *cuadros de límite*). El servicio, a continuación, se puede volver a entrenar, lo que aumentará la probabilidad de que el reconocimiento de objetos del mundo real.

Este curso le mostrará cómo obtener los resultados de Azure Custom Vision Service, detección de objetos, en una aplicación de ejemplo basada en Unity. Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 310: Detección de objetos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [El SDK más reciente de Windows 10](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Un [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con el modo de desarrollador habilitado
- Acceso a Internet para el programa de instalación de Azure y la recuperación de Custom Vision Service
-  Se requieren una serie de imágenes al menos quince (15)) para cada objeto que desea que la visión personalizada para que reconozca. Si lo desea, puede usar las imágenes que ya se proporciona con este curso, [una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
2.  Configurar y probar su HoloLens. Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Capítulo 1: el Portal de Custom Vision

Para usar el **Azure Custom Vision Service**, deberá configurar una instancia de ella esté disponible para su aplicación.

1.  Navegue [a la **Custom Vision Service** página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Haga clic en **Introducción**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Inicie sesión en el Portal de visión personalizada.

    ![](images/AzureLabs-Lab310-02.png)

4.  Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

5.  Una vez que haya iniciado sesión por primera vez, se le pedirá con el *condiciones del servicio* panel. Haga clic en la casilla de verificación *acepta los términos*. A continuación, haga clic en **acepto**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Tener aceptado los términos, ya está en el *Mis proyectos* sección. Haga clic en **nuevo proyecto**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Aparecerá una ficha en el lado derecho, que le solicitará que especifique algunos campos para el proyecto.

    1.  Insertar un nombre para el proyecto

    2.  Insertar una descripción para el proyecto (**opcional**)

    3.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos cursos) en un grupo de recursos comunes).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Si desea [Obtenga más información acerca de los grupos de recursos de Azure, vaya a los documentos asociados](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  Establecer el **tipos de proyecto** como **(versión preliminar) de detección de objetos**.

8.  Una vez haya terminado, haga clic en **crear un proyecto**, y se le redirigirá a la página de proyectos de Custom Vision Service.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2: el proyecto de Custom Vision de entrenamiento

Una vez en el Portal de visión personalizada, su principal objetivo es entrenar su proyecto para reconocer objetos específicos en las imágenes.

Necesita al menos quince (15) imágenes para cada objeto que desea que la aplicación reconozca. Puede usar las imágenes proporcionadas con este curso ([una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Para entrenar el proyecto de Custom Vision:

1.  Haga clic en el **+** situado junto a **etiquetas**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Agregar un **nombre** para la etiqueta que se usará para asociar las imágenes con. En este ejemplo para el reconocimiento, por lo que ha asignado un nombre de la etiqueta para esto, usamos las imágenes de tazas **Cup**. Haga clic en **guardar** una vez finalizado.

    ![](images/AzureLabs-Lab310-07.png)

3.  Observará el **etiqueta** se ha agregado (es posible que deba volver a cargar la página para que aparezca). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Haga clic en **agregar imágenes** en el centro de la página.

    ![](images/AzureLabs-Lab310-09.png)

5.  Haga clic en **examinar archivos locales**y vaya a las imágenes que desea cargar un objeto, siendo el mínimo quince (15).

    > [!TIP]
    >  Puede seleccionar varias imágenes a la vez, para cargar.

    ![](images/AzureLabs-Lab310-10.png)

6.  Presione **cargar archivos** una vez haya seleccionado todas las imágenes que desea entrenar el proyecto con. Los archivos cargarán. Una vez que la confirmación de la carga, haga clic en **realiza**.

    ![](images/AzureLabs-Lab310-11.png)

7.  En este momento las imágenes se cargan, pero no etiquetadas.

    ![](images/AzureLabs-Lab310-12.png)

8.  Para etiquetar las imágenes, use el mouse. Cuando se sitúa encima de la imagen, un área resaltada de selección le ayudará a dibujando automáticamente una selección alrededor de su objeto. Si no es preciso, puede dibujar sus propios. Esto se logra manteniendo primario del mouse, y arrastrando la región de selección para abarcar el objeto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Después de la selección del objeto dentro de la imagen, un pequeño se le preguntará si desea *Agregar etiqueta Region*. Seleccione la etiqueta creada anteriormente (en el ejemplo anterior, "Cup"), o si va a agregar más etiquetas, que, en Escriba y haga clic en el **+ (signo más)** botón.

    ![](images/AzureLabs-Lab310-14.png) 

10. Para etiquetar la imagen siguiente, puede haga clic en la flecha situada a la derecha de la hoja, o cierre la hoja de etiquetas (haciendo clic en el **X** en la esquina superior derecha de la hoja) y, a continuación, haga clic en la siguiente imagen. Una vez que la imagen siguiente lista, repita el mismo procedimiento. Hágalo para todas las imágenes que ha cargado, hasta que todos están etiquetados. 

    > [!NOTE]
    >  Puede seleccionar varios objetos en la misma imagen, al igual que la imagen siguiente: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Una vez que haya etiquetado todas ellas, haga clic en el **etiquetadas** botón a la izquierda de la pantalla para mostrar las imágenes etiquetadas. 

    ![](images/AzureLabs-Lab310-16.png)

12. Ahora está listo para entrenar el servicio. Haga clic en el **Train** botón y la primera iteración de entrenamiento se iniciará.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Una vez compilada, podrá ver dos botones denominados **Predeterminar** y **predicción URL**. Haga clic en **Predeterminar** en primer lugar, a continuación, haga clic en **predicción URL**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > El punto de conexión que se proporciona con esto, se establece en lo que ocurra *iteración* está marcada como predeterminada. Como tal, si posteriormente realiza una nueva *iteración* y actualizarlo como valor predeterminado, no necesitará cambiar el código.

14. Una vez que ha hecho clic **dirección URL de la predicción**, abra *el Bloc de notas*y copie y pegue el **URL** (también se denomina su **predicción extremo**) y el **clave de predicción de servicio**, de modo que puede recuperar cuando necesite más adelante en el código.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra **Unity** y haga clic en **New**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Insertar **CustomVisionObjDetection**. Asegúrese de que el tipo de proyecto se establece en **3D**y establezca el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **editar* > *preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **Visual Studio**. Cerrar la **preferencias** ventana.

    ![](images/AzureLabs-Lab310-23.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y cambie el **plataforma** a *Universal Windows Platform*y, a continuación, haga clic en el **Cambiar plataforma** botón.

    ![](images/AzureLabs-Lab310-24.png)

5.  En el mismo **configuración de compilación** ventana, asegúrese de que se establezca lo siguiente:

    1.  **Dispositivo de destino** está establecido en **HoloLens**        
    2.  **Tipo de compilación** está establecido en **D3D**
    3.  **SDK** está establecido en **instalada más reciente**
    4.  **Versión de Visual Studio** está establecido en **instalada más reciente**
    5.  **Compilar y ejecutar** está establecido en **máquina Local**            
    6.  El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.

        ![](images/AzureLabs-Lab310-25.png)

6.  En el mismo **configuración de compilación** ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental** (.NET 4.6 equivalente), que desencadenará una necesidad de reiniciar el Editor.

        2. **Scripting de back-end** debe ser **.NET**.

        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Más abajo el panel, en **XR configuración** (situado debajo de **configuración de publicación**), graduación **admite la realidad Virtual**, a continuación, asegúrese de que el **mixto de Windows Realidad SDK** se agrega.

        ![](images/AzureLabs-Lab310-29.png)

8.  En **configuración de compilación**, *Unity C\# proyectos* ya no está atenuado: Marque la casilla situada junto a esto.

9.  Cerrar la **configuración de compilación** ventana.

10. En el **Editor**, haga clic en **editar** > **configuración del proyecto** > **gráficos**.

    ![](images/AzureLabs-Lab310-30.png)

11. En el **Panel Inspector** el *configuración gráficos* estará abierto. Desplácese hacia abajo hasta que vea una matriz denominada **siempre incluyen los sombreadores**. Agregar una ranura aumentando la **tamaño** variable en uno (en este ejemplo, fuera 8 por lo que lo hicimos 9). Una nueva ranura aparecerá en la última posición de la matriz, como se muestra a continuación:

    ![](images/AzureLabs-Lab310-31.png)

12. En la ranura, haga clic en el círculo pequeño de destino junto a la ranura para abrir una lista de los sombreadores. Busque el **heredado sombreadores/Transparent/difuso** sombreador y haga doble clic en él. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capítulo 4: importar el paquete de CustomVisionObjDetection Unity

Para este curso se proporcionan con un paquete de activos de Unity, denominada **MR-Azure-310.unitypackage**. 

> [SUGERENCIA] Todos los objetos compatibles con Unity, incluidas las escenas completas, se pueden empaquetar en un **.unitypackage** archivo y exportar / importar en otros proyectos. Es la manera más segura y más eficaz para mover recursos entre los distintos **proyectos de Unity**.

Puede encontrar el [paquete Azure-MR-310 que deba descargar aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Con el panel de Unity delante de usted, haga clic en **activos** en el menú en la parte superior de la pantalla, a continuación, haga clic en **Importar paquete > paquete personalizado**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Utilice el selector de archivos para seleccionar la **MR-Azure-310.unitypackage** del paquete y haga clic en **abierto**. Se mostrará una lista de componentes para este recurso para usted. Confirmar la importación, haga clic en el **importar** botón.

    ![](images/AzureLabs-Lab310-34.png)

3.  Una vez que haya terminado de importarse, observará que ahora se han agregado las carpetas desde el paquete para su **activos** carpeta. Este tipo de estructura de carpetas es típico de un proyecto de Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  El **materiales** carpeta contiene el material utilizado por la **que mirar Cursor**. 

    2.  El **complementos** carpeta contiene la DLL de Newtonsoft utilizado por el código para deserializar la respuesta del servicio web. Las dos (2) diferentes versiones contenidas en la carpeta y la subcarpeta, son necesarias para permitir que la biblioteca para usarse y generados por el Editor de Unity y la compilación UWP. 

    3.  El **prefabricados** carpeta contiene el prefabricados contenidos en la escena. Esos son:

        1.  El **GazeCursor**, el cursor usado en la aplicación. Funciona junto con el recurso prefabricado de SpatialMapping que puedan colocarse en la escena encima de los objetos físicos.
        2.  El **etiqueta**, que es el objeto de interfaz de usuario utilizado para mostrar la etiqueta de objeto en la escena cuando sea necesario.
        3.  El **SpatialMapping**, que es el objeto que permite usar la aplicación cree un mapa virtual, con seguimiento espacial de la Microsoft HoloLens.

    4.  El **escenas** carpeta que contiene actualmente la escena creada previamente en este curso.

4.  Abra el **escenas** carpeta, en el **Panel proyecto**y haga doble clic en el **ObjDetectionScene**, cargar la escena que va a utilizar en este curso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Se incluye ningún código**, escribirá el código siguiendo este curso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capítulo 5: crear la clase CustomVisionAnalyser.

En este momento está listo para escribir código. Se iniciará con la **CustomVisionAnalyser** clase.

> [!NOTE]
> Las llamadas a la **Custom Vision Service**, realizados en el código se muestra a continuación, se realizan utilizando el **API de REST de Custom Vision**. A través del uso de esto, verá cómo implementar y hacer uso de esta API (útil para comprender cómo implementar algo similar en su propio). Tenga en cuenta que Microsoft ofrece un **Custom Vision SDK** que también se puede utilizar para realizar llamadas al servicio. Para obtener más información, visite la [artículo Custom Vision SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Esta clase es responsable de:

- Cargando la última imagen de captura como una matriz de bytes.

- Envío de la matriz de bytes en su Azure **Custom Vision Service** instancia para el análisis.

- Recibir la respuesta como una cadena JSON.

- Al deserializar la respuesta y el paso resultante **predicción** a la **SceneOrganiser** (clase), que se encargará de cómo se debe mostrar la respuesta.

Para crear esta clase:

1.  Haga clic en el **carpeta de activos**, que se encuentra en la **Panel proyecto**, a continuación, haga clic en **crear** > **carpeta**. Llame a la carpeta **Scripts**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Haga doble clic en la carpeta recién creada, para abrirlo.

3.  Haga clic en la carpeta, a continuación, haga clic en **crear** > **C\# Script**. Nombre de la secuencia de comandos **CustomVisionAnalyser.**

4.  Haga doble clic en el nuevo **CustomVisionAnalyser** script para abrirlo con **Visual Studio.**

5.  Asegúrese de que tiene los siguientes espacios de nombres al que hace referencia en la parte superior del archivo:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  En el **CustomVisionAnalyser** de clases, agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Asegúrese de insertar el **clave de predicción de servicio** en el **predictionKey** variable y su **predicción extremo** en el **predictionEndpoint**  variable. Ha copiado a [el Bloc de notas anteriormente, en el capítulo 2, el paso 14](#chapter-2---training-your-custom-vision-project).

7.  El código para **Awake()** ahora debe agregarse para inicializar la variable de instancia:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Agregar la corrutina (con el método estático **GetImageAsByteArray()** método debajo de él), que obtendrá los resultados del análisis de la imagen, capturado por el **ImageCapture** clase.

    > [!NOTE]
    > En el **AnalyseImageCapture** corrutina, hay una llamada a la **SceneOrganiser** clase que aún está a crear. Por lo tanto, **las deje líneas de comentarios por ahora**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. Eliminar el **Start()** y **Update()** métodos, ya que no se usará. 

10.  Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.

> [!IMPORTANT]
> Como se mencionó anteriormente, no se preocupe código que puede aparecer un error, ya que proporciona más clases pronto, lo que solucionará estas.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capítulo 6: crear la clase CustomVisionObjects

La clase que se va a crear es ahora el **CustomVisionObjects** clase.

Este script contiene un número de objetos usados por otras clases para serializar y deserializar las llamadas realizadas a Custom Vision Service.

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Llame al script **CustomVisionObjects.**

2.  Haga doble clic en el nuevo **CustomVisionObjects** script para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres al que hace referencia en la parte superior del archivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminar el **Start()** y **Update()** métodos dentro de la **CustomVisionObjects** (clase), esta clase ahora debe estar vacía.

    > [!WARNING]
    > Es importante que siga cuidadosamente la siguiente instrucción. Si coloca las declaraciones de clase nuevo dentro de la **CustomVisionObjects** (clase), obtendrá errores de compilación en [capítulo 10](#chapter-10---create-the-imagecapture-class), que indica que **AnalysisRootObject** y  **BoundingBox** no se encuentran.

5.  Agregue las siguientes clases *fuera* el **CustomVisionObjects** clase. Estos objetos se usan por el **Newtonsoft** library para serializar y deserializar los datos de respuesta:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capítulo 7: crear la clase SpatialMapping

Esta clase se establecerá la **Colisionador asignación espacial** en la escena, por lo que para poder detectar las colisiones entre objetos virtuales y los objetos reales.

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Llame al script **SpatialMapping.**

2.  Haga doble clic en el nuevo **SpatialMapping** script para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres mencionada anteriormente el **SpatialMapping** clase:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  A continuación, agregue las siguientes variables dentro de la **SpatialMapping** clase encima el **Start()** método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Agregar el **Awake()** y **Start()**:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Eliminar el **Update()** método.

7.  Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Capítulo 8: crear la clase GazeCursor

Esta clase es responsable de configurar el cursor en la ubicación correcta en el espacio real, al hacer uso de la **SpatialMappingCollider**, creado en el capítulo anterior.

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Llame al script **GazeCursor**

2.  Haga doble clic en el nuevo **GazeCursor** script para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene el siguiente espacio de nombres mencionada anteriormente el **GazeCursor** clase:

    ```csharp
    using UnityEngine;
    ```

4.  A continuación, agregue la siguiente variable dentro de la **GazeCursor** clase encima el **Start()** método. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Actualización de la **Start()** método con el código siguiente:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Actualización de la **Update()** método con el código siguiente:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > No se preocupe sobre el error para el **SceneOrganiser** clase no se encuentra, se creará en el próximo capítulo.

7. Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capítulo 9: crear la clase SceneOrganiser

Esta clase hará lo siguiente:

-   Configurar la *cámara principal* adjuntando los componentes adecuados a él.

-   Cuando se detecta un objeto, será responsable de su posición en el mundo real y el lugar de calcular una **etiqueta** cerca de él con los valores adecuados **nombre de la etiqueta**.    

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Nombre de la secuencia de comandos **SceneOrganiser**.

2.  Haga doble clic en el nuevo **SceneOrganiser** script para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres mencionada anteriormente el **SceneOrganiser** clase:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  A continuación, agregue las siguientes variables dentro de la **SceneOrganiser** clase encima el **Start()** método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Eliminar el **Start()** y **Update()** métodos.

6.  Debajo de las variables, agregue el **Awake()** método, que inicializará la clase y configuración de la escena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Agregar el **PlaceAnalysisLabel()** método, que se *Instantiate* la etiqueta de la escena (que en este momento es invisible para el usuario). También coloca el cuádruple (también invisible) donde se coloca la imagen y se superpone con el mundo real. Esto es importante porque las coordenadas del cuadro recuperados del servicio después de análisis se realizar un seguimiento en este cuádruple para determinar la ubicación aproximada del objeto en el mundo real. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Agregar el **FinaliseLabel()** método. Es responsable de:

    *   Establecer el *etiqueta* texto con el *etiqueta* de la predicción con la confianza más alta.
    *   Una llamada al cálculo de la *cuadro límite* en el objeto cuádruple, colocado anteriormente y sitúa la etiqueta de la escena.
    *   Cómo ajustar la profundidad de la etiqueta mediante un Raycast hacia el *cuadro límite*, que debe entrar en conflicto con el objeto en el mundo real.
    * Restableciendo el proceso de captura para permitir al usuario capturar la imagen de otro.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Agregar el **CalculateBoundingBoxPosition()** método, que hospeda una serie de cálculos necesarios para traducir el *cuadro límite* coordenadas recuperados del servicio y volver a crearlos proporcionalmente en lo cuatro.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.

    > [!IMPORTANT]
    > Antes de continuar, abra el **CustomVisionAnalyser** (clase) y dentro del **AnalyseLastImageCaptured()** método, *quite* las líneas siguientes:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> No se preocupe la **ImageCapture** class 'no se pudo encontrar' mensaje, se creará en el próximo capítulo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capítulo 10: crear la clase ImageCapture

La siguiente clase que se va a crear es la **ImageCapture** clase.

Esta clase es responsable de:

*   Capturar una imagen con la cámara de HoloLens y almacenarla en la *aplicación* carpeta.
*   Control *pulse* gestos del usuario.

Para crear esta clase:

1.  Vaya a la **Scripts** carpeta que creó anteriormente.

2.  Haga clic en la carpeta, a continuación, haga clic en **crear** > **C\# Script**. Nombre de la secuencia de comandos **ImageCapture**.

3.  Haga doble clic en el nuevo **ImageCapture** script para abrirlo con **Visual Studio.**

4.  Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro de la **ImageCapture** clase encima el **Start()** método:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  El código para **Awake()** y **Start()** métodos ahora debe agregar:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementar un controlador que se llamará cuando se produce un gesto de pulsar:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Cuando el cursor está **verde**, significa que la cámara está disponible para tomar la imagen. Cuando el cursor está **rojo**, lo que significa que la cámara está ocupada.

8.  Agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  Agregue los controladores que se llamará cuando se ha capturado la foto y para cuando esté listo para ser analizados. El resultado se pasa a la **CustomVisionAnalyser** para el análisis.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capítulo 11: configuración de las secuencias de comandos de la escena

Ahora que hemos escrito todo el código necesario para este proyecto, es momento de configurar las secuencias de comandos de la escena y en prefabricados, para que se comporten correctamente.

1.  Dentro de la **Editor de Unity**, en el **jerarquía Panel**, seleccione el **cámara principal**.
2.  En el **Panel Inspector**, con el **cámara principal** seleccionado, haga clic en **Agregar componente**, a continuación, busque **SceneOrganiser** secuencia de comandos y Haga doble clic para agregarlo.

    ![](images/AzureLabs-Lab310-38.png)

3.  En el **Panel proyecto**, abra el **carpeta prefabricados**, arrastre el **etiqueta** prefabricado en el *etiqueta* área, de entrada de destino de la referencia vacía en el **SceneOrganiser** secuencia de comandos que acaba de agregar a la *cámara principal*, tal y como se muestra en la imagen siguiente:

    ![](images/AzureLabs-Lab310-39.png)

4.  En el **jerarquía Panel**, seleccione el **GazeCursor** secundarios de la **cámara principal**.
5.  En el **Panel Inspector**, con el **GazeCursor** seleccionado, haga clic en **Agregar componente**, a continuación, busque **GazeCursor** secuencia de comandos y Haga doble clic para agregarlo.

    ![](images/AzureLabs-Lab310-40.png)

6.  De nuevo, en el **jerarquía Panel**, seleccione el **SpatialMapping** secundarios de la **cámara principal**.
7.  En el **Panel Inspector**, con el **SpatialMapping** seleccionado, haga clic en **Agregar componente**, a continuación, busque **SpatialMapping** secuencia de comandos y haga doble clic para agregarlo.

    ![](images/AzureLabs-Lab310-41.png)

Las secuencias de comandos restantes de la no tienen conjunto se agregará el código de la **SceneOrganiser** script en tiempo de ejecución.

## <a name="chapter-12---before-building"></a>Capítulo 12 - antes de compilar

Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su Microsoft HoloLens.

Antes de hacerlo, asegúrese de que:

-  Todas las configuraciones que se mencionan en la [capítulo 3](#chapter-3---set-up-the-unity-project) están establecidas correctamente.
- La secuencia de comandos **SceneOrganiser** está asociado a la **cámara principal** objeto.
- La secuencia de comandos **GazeCursor** está asociado a la **GazeCursor** objeto.
- La secuencia de comandos **SpatialMapping** está asociado a la **SpatialMapping** objeto.
- En [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), paso 6:

    - Asegúrese de insertar el **clave del servicio de predicción** en el **predictionKey** variable.
    - Ha insertado el **punto de conexión de predicción** en el **predictionEndpoint** clase.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capítulo 13 - compilar la solución UWP y transferir localmente la aplicación

Ahora está listo para compilar la aplicación como una solución de UWP que podrá implementar en el Microsoft HoloLens. Para comenzar el proceso de compilación:

1.  Vaya a **archivo > configuración de compilación**.

2.  Graduación **Unity C\# proyectos**.

3.  Haga clic en **agregar escenas abiertos**. Esto agregará la escena abierta actualmente a la compilación.

    ![](images/AzureLabs-Lab310-42.png)

4.  Haz clic en **Compilación**. Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta y asígnele el nombre **aplicación**. A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**.

5.  Unity empezará a compilar el proyecto para el **aplicación** carpeta.

6.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

7.  Para implementar la sesión en Microsoft HoloLens, necesitará la dirección IP del dispositivo (para la implementación remota), y para asegurarse de que también tiene **modo de programador** establecido. Para ello:

    1.  Mientras que el exceso de su HoloLens, abra el **configuración**.

    2.  Vaya a **red e Internet** > **Wi-Fi** > **opciones avanzadas**

    3.  Tenga en cuenta la **IPv4** dirección.

    4.  A continuación, vaya a **configuración**y, a continuación, en **actualización y seguridad** > **para desarrolladores**

    5.  Establecer **modo de programador** *en*.

8.  Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.

9.  En, seleccione la configuración de la solución **depurar**.

10. En la plataforma de soluciones, seleccione **x86, máquina remota**. Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (el Microsoft HoloLens, en este caso, lo cual observó).

    ![](images/AzureLabs-Lab310-43.png)

11. Vaya a la **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación a su HoloLens.

12. La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en el Microsoft HoloLens, lista para iniciarse.

### <a name="to-use-the-application"></a>Para usar la aplicación:

* Examine un objeto que se ha entrenado con su **Azure Custom Vision Service, detección de objetos**y usar el **gesto**.
* Si el objeto se detecte correctamente, un espacio global *texto de la etiqueta* aparecerá con el nombre de etiqueta.

> [!IMPORTANT]
> Cada vez que se captura una foto y enviarlo al servicio, puede volver a la página de servicio y reciclar el servicio con las imágenes de recién capturados. Al principio, probablemente también tenga que corregir la *cuadros de límite* para ser más preciso y reciclar el servicio.

> [!NOTE]
> Coloca el texto de la etiqueta podría no aparecer cerca del objeto cuando los sensores de Microsoft HoloLens o la SpatialTrackingComponent en Unity no se puede colocar el colisionadores adecuados, en relación con los objetos del mundo real. Pruebe a usar la aplicación en una superficie diferente si ese es el caso.

## <a name="your-custom-vision-object-detection-application"></a>Tu visión personalizada, aplicación de detección de objetos

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Custom Vision, API de detección de objeto, que puede reconocer un objeto desde una imagen y, a continuación, proporcione una ubicación aproximada para ese objeto en el espacio 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

Agregar a la etiqueta de texto, utilice un cubo semitransparente para encapsular el objeto real en 3D *cuadro límite*.

### <a name="exercise-2"></a>Ejercicio 2

Entrenar su Custom Vision Service para reconocer más objetos.

### <a name="exercise-3"></a>Ejercicio 3

Reproducir un sonido cuando se reconoce un objeto.

### <a name="exercise-4"></a>Ejercicio 4

Usar la API para volver a entrenar el servicio con las mismas imágenes que se está analizando la aplicación, por lo tanto, para que el servicio más precisos (realizar tareas de predicción y aprendizaje de forma simultánea).
