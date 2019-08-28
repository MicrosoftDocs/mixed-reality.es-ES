---
title: 'MR y Azure 310: detección de objetos'
description: Complete este curso para aprender a entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares y su posición en el mundo real desde una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visión personalizada, detección de objetos, realidad mixta, Academia, Unity, tutorial, API, hololens
ms.openlocfilehash: 71370db84a9b90b017e8d5fac0799a862883d046
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047226"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

# <a name="mr-and-azure-310-object-detection"></a>Mr y Azure 310: Detección de objetos

En este curso, aprenderá a reconocer el contenido visual personalizado y su posición espacial dentro de una imagen proporcionada, mediante las funcionalidades de Azure Custom Vision "detección de objetos" en una aplicación de realidad mixta.

Este servicio le permitirá entrenar un modelo de aprendizaje automático mediante imágenes de objeto. A continuación, usará el modelo entrenado para reconocer objetos similares y aproximar su ubicación en el mundo real, tal como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara conectarse a un equipo para recibir auriculares envolventes (VR).

![resultado del curso](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision, la detección de objetos** es un servicio de Microsoft que permite a los desarrolladores crear clasificadores de imágenes personalizados. Estos clasificadores se pueden usar con nuevas imágenes para detectar objetos dentro de esa nueva imagen, proporcionando **límites de cuadro** dentro de la propia imagen. El servicio proporciona un portal en línea sencillo y fácil de usar para simplificar este proceso. Para obtener más información, visite los vínculos siguientes:

* [Página de Custom Vision de Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Límites y cuotas](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Al finalizar este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:

1. El usuario podrá hacer una *mirada* a un objeto, que ha entrenado con la Custom Vision Service de Azure, la detección de objetos. 
2. El usuario usará el gesto de puntear para capturar una imagen de lo que están examinando.
3. La aplicación enviará la imagen a Azure Custom Vision Service.
4. Habrá una respuesta del servicio que mostrará el resultado del reconocimiento como texto de espacio universal. Esto se consigue mediante el seguimiento espacial de Microsoft HoloLens, como una forma de entender la posición mundial del objeto reconocido y, a continuación, usando la *etiqueta* asociada a lo que se detecta en la imagen para proporcionar el texto de la etiqueta.

El curso también cubrirá la carga manual de imágenes, la creación de etiquetas y el entrenamiento del servicio, para reconocer objetos diferentes (en el ejemplo proporcionado, una copa), estableciendo el *cuadro de límite* dentro de la imagen que envía. 

> [!IMPORTANT]
> Después de la creación y el uso de la aplicación, el desarrollador debe volver a la Custom Vision Service de Azure e identificar las predicciones realizadas por el servicio y determinar si son correctas o no (mediante el etiquetado de todo el servicio que faltaba y ajustar los *rectángulos*de selección). Después, se puede volver a entrenar el servicio, lo que aumentará la probabilidad de que reconozca objetos del mundo real.

Este curso le enseñará cómo obtener los resultados de la Custom Vision Service de Azure, la detección de objetos, en una aplicación de ejemplo basada en Unity. Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 310: Detección de objetos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio). Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se enumera a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [El SDK de Windows 10 más reciente](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017,4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Un [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con el modo de desarrollador habilitado
- Acceso a Internet para la configuración y recuperación de Custom Vision Service de Azure
-  Se requiere una serie de al menos quince (15) imágenes) para cada objeto que desea que reconozca el Custom Vision. Si lo desea, puede usar las imágenes que ya se proporcionan con este curso, [una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
2.  Configure y pruebe su HoloLens. Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Capítulo 1: portal de Custom Vision

Para usar la **Custom Vision Service de Azure**, debe configurar una instancia de para que esté disponible para la aplicación.

1.  Navegue [hasta el **Custom Vision Service** Página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Haga clic en **Introducción**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Inicie sesión en el portal de Custom Vision.

    ![](images/AzureLabs-Lab310-02.png)

4.  Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

5.  Una vez iniciada la sesión por primera vez, se le solicitará el panel *de condiciones de servicio* . Haga clic en la casilla para *aceptar los términos*. A continuación, haga clic en Acepto.

    ![](images/AzureLabs-Lab310-03.png)

6.  Una vez aceptados los términos, ahora está en la sección *mis proyectos* . Haga clic en **nuevo proyecto**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Aparecerá una pestaña en el lado derecho, que le pedirá que especifique algunos campos para el proyecto.

    1.  Insertar un nombre para el proyecto

    2.  Insertar una descripción para el proyecto (**opcional**)

    3.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Si desea [leer más información sobre los grupos de recursos de Azure, vaya a los documentos asociados](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) .

    4.  Establezca los **tipos de proyecto** como **detección de objetos (vista previa)** .

8.  Cuando haya terminado, haga clic en **crear proyecto**y se le redirigirá a la página Custom Vision Service proyecto.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2: entrenar el proyecto de Custom Vision

Una vez en el portal de Custom Vision, el objetivo principal es entrenar el proyecto para que reconozca objetos específicos en las imágenes.

Necesita al menos quince (15) imágenes para cada objeto que desea que reconozca la aplicación. Puede usar las imágenes que se proporcionan con este curso ([una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Para entrenar su proyecto de Custom Vision:

1.  Haga clic en **+** el botón situado junto a **etiquetas**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Agregue un **nombre** para la etiqueta que se utilizará para asociar las imágenes con. En este ejemplo se usan imágenes de copas para el reconocimiento, por lo que hemos llamado a la etiqueta de esta, **Cup**. Haga clic en **Guardar** cuando haya terminado.

    ![](images/AzureLabs-Lab310-07.png)

3.  Observará que se ha agregado la **etiqueta** (es posible que tenga que volver a cargar la página para que aparezca). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Haga clic en **Agregar imágenes** en el centro de la página.

    ![](images/AzureLabs-Lab310-09.png)

5.  Haga clic en **examinar archivos locales**y busque las imágenes que desea cargar para un objeto, con el mínimo de quince (15).

    > [!TIP]
    >  Puede seleccionar varias imágenes a la vez para cargarlas.

    ![](images/AzureLabs-Lab310-10.png)

6.  Presione **cargar archivos** una vez que haya seleccionado todas las imágenes con las que desea entrenar el proyecto. Los archivos comenzarán a cargarse. Una vez que haya confirmado la carga, haga clic en **listo**.

    ![](images/AzureLabs-Lab310-11.png)

7.  En este momento, las imágenes se cargan, pero no se etiquetan.

    ![](images/AzureLabs-Lab310-12.png)

8.  Para etiquetar las imágenes, use el mouse. Al mantener el mouse sobre la imagen, un resaltado de selección le ayudará a dibujar automáticamente una selección alrededor del objeto. Si no es preciso, puede dibujar el suyo propio. Para ello, mantenga pulsado el botón primario del mouse y arrastre la región de selección para abarcar el objeto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Tras la selección del objeto dentro de la imagen, una pequeña solicitud le pedirá que *agregue la etiqueta de región*. Seleccione la etiqueta creada anteriormente (' Cup ', en el ejemplo anterior) o, si va a agregar más etiquetas, escríbala y haga clic en el botón **+ (Plus)** .

    ![](images/AzureLabs-Lab310-14.png) 

10. Para etiquetar la imagen siguiente, puede hacer clic en la flecha situada a la derecha de la hoja o cerrar la hoja de etiquetas (haciendo clic en la **X** en la esquina superior derecha de la hoja) y, a continuación, haga clic en la imagen siguiente. Una vez que tenga la siguiente imagen lista, repita el mismo procedimiento. Haga esto para todas las imágenes que ha cargado hasta que se etiqueten todas. 

    > [!NOTE]
    >  Puede seleccionar varios objetos en la misma imagen, como en la imagen siguiente: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Una vez que las etiquete todas, haga clic en el botón **etiquetado** , situado a la izquierda de la pantalla, para mostrar las imágenes etiquetadas. 

    ![](images/AzureLabs-Lab310-16.png)

12. Ya está listo para entrenar su servicio. Haga clic en el botón **entrenar** y comenzará la primera iteración de entrenamiento.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Una vez compilada, podrá ver dos botones denominados establecer **dirección URL** **predeterminada** y de predicción. Haga clic en **establecer como predeterminado** primero y luego haga clic en **dirección URL**de predicción.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > El extremo que se proporciona a partir de este, se establece en la iteración que se haya marcado como predeterminada. Por lo tanto, si posteriormente realiza una nueva *iteración* y la actualiza como predeterminada, no necesitará cambiar el código.

14. Una vez que haya hecho clic **en URL**de predicción, abra el *Bloc de notas*y copie y pegue la **dirección URL** (también denominada predicción **-punto de conexión**) y la **clave de predicción del servicio**para que pueda recuperarla cuando la necesite más adelante en el código.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: configuración del proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra **Unity** y haga clic en **nuevo**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity. Inserte **CustomVisionObjDetection**. Asegúrese de que el tipo de proyecto está establecido en **3D**y establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**. Vaya a **Editar* > *preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio**. Cierre la ventana **preferencias** .

    ![](images/AzureLabs-Lab310-23.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y cambie la **plataforma** a *plataforma universal de Windows*y, a continuación, haga clic en el botón **cambiar plataforma** .

    ![](images/AzureLabs-Lab310-24.png)

5.  En la misma ventana de **configuración de compilación** , asegúrese de que se establece lo siguiente:

    1.  El **dispositivo de destino** está establecido en **HoloLens**        
    2.  El **tipo de compilación** se establece en **D3D**
    3.  **SDK** está establecido en la **versión más reciente instalada**
    4.  La **versión de Visual Studio** está establecida en la **más reciente instalada**
    5.  **Compilar y ejecutar** está establecido en **equipo local**            
    6.  El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.

        ![](images/AzureLabs-Lab310-25.png)

6.  En la misma ventana de configuración de la **compilación** , haga clic en el botón **configuración del reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .

7. En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  La **versión de scripting en tiempo de ejecución** debe ser **Experimental** (.net 4,6 equivalente), lo que desencadenará una necesidad de reiniciar el editor.

        2. El **back-end** de scripting debe ser **.net**.

        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        1. **InternetClient**

        2.  **Web**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), marque la **realidad virtual compatible**y asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![](images/AzureLabs-Lab310-29.png)

8.  De nuevo en la **configuración de compilación**, los *proyectos de Unity C\#*  ya no están atenuados: Marque la casilla situada junto a este.

9.  Cierre la ventana **configuración de compilación** .

10. En el **Editor**, haga clic en **Editar** > **configuración** > del proyecto**gráficos**.

    ![](images/AzureLabs-Lab310-30.png)

11. En el **panel Inspector** , se abrirá la *configuración de gráficos* . Desplácese hacia abajo hasta que vea una matriz denominada **incluir siempre sombreadores**. Agregue una ranura aumentando la variable de **tamaño** en uno (en este ejemplo, era 8, por lo que lo hicimos 9). Aparecerá una nueva ranura en la última posición de la matriz, como se muestra a continuación:

    ![](images/AzureLabs-Lab310-31.png)

12. En la ranura, haga clic en el círculo de destino pequeño junto a la ranura para abrir una lista de sombreadores. Busque los sombreadores **heredados/transparente/difusor** y haga doble clic en él. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capítulo 4: importación del paquete Unity de CustomVisionObjDetection

En este curso, se proporciona un paquete de recursos de Unity llamado **Azure-Mr-310. unitypackage Tools**. 

> Tip Cualquier objeto admitido por Unity, incluidas todas las escenas, se puede empaquetar en un archivo **. unitypackage Tools** y exportarse o importarse en otros proyectos. Es la forma más segura y eficaz de trasladar recursos entre distintos proyectos de **Unity**.

Puede encontrar el [paquete Azure-Mr-310 que necesita descargar aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Con el panel de Unity delante de usted, haga clic en **recursos** en el menú de la parte superior de la pantalla y, a continuación, haga clic en **importar paquete > paquete personalizado**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Use el selector de archivos para seleccionar el paquete **Azure-Mr-310. unitypackage Tools** y haga clic en **abrir**. Se le mostrará una lista de los componentes de este recurso. Para confirmar la importación, haga clic en el botón **importar** .

    ![](images/AzureLabs-Lab310-34.png)

3.  Una vez que haya finalizado la importación, observará que ahora se han agregado carpetas del paquete a la carpeta **assets** . Este tipo de estructura de carpetas es típico para un proyecto de Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  La carpeta **materiales** contiene el material usado por el **cursor de mira fijamente**. 

    2.  La carpeta plugins contiene el archivo dll de Newtonsoft que usa el código para deserializar la respuesta web del servicio. Las dos (2) versiones diferentes contenidas en la carpeta y subcarpeta, son necesarias para permitir que la biblioteca sea utilizada y compilada por el editor de Unity y la compilación de UWP. 

    3.  La carpeta **Prefabs** contiene el Prefabs contenido en la escena. Estos son:

        1.  **GazeCursor**, el cursor que se usa en la aplicación. Funcionará junto con el recurso prefabricado de SpatialMapping para poder colocarse en la escena sobre objetos físicos.
        2.  La **etiqueta**, que es el objeto de interfaz de usuario que se usa para mostrar la etiqueta de objeto en la escena cuando sea necesario.
        3.  **SpatialMapping**, que es el objeto que permite a la aplicación usar crear un mapa virtual, mediante el seguimiento espacial de Microsoft HoloLens.

    4.  La carpeta Scenes que contiene actualmente la escena pregenerada para este curso.

4.  Abra la carpeta Scenes, en el **panel Proyecto**, y haga doble clic en **ObjDetectionScene**para cargar la escena que usará para este curso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **No se incluye ningún código**, se escribirá el código siguiendo este curso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capítulo 5: creación de la clase CustomVisionAnalyser.

En este momento está listo para escribir código. Comenzará con la clase **CustomVisionAnalyser** .

> [!NOTE]
> Las llamadas al **Custom Vision Service**, realizadas en el código que se muestra a continuación, se realizan mediante la **API de REST de Custom Vision**. Mediante este procedimiento, verá cómo implementar y usar esta API (útil para entender cómo implementar algo similar por su cuenta). Tenga en cuenta que Microsoft ofrece un **SDK de Custom Vision** que también se puede usar para realizar llamadas al servicio. Para obtener más información, visite el [artículo Custom Vision SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Esta clase es responsable de:

- Cargar la imagen más reciente capturada como una matriz de bytes.

- Envío de la matriz de bytes a la instancia de Azure **Custom Vision Service** para su análisis.

- Recibir la respuesta como una cadena JSON.

- Deserializar la respuesta y pasar la **predicción** resultante a la clase **SceneOrganiser** , que se encargará de cómo se debe mostrar la respuesta.

Para crear esta clase:

1.  Haga clic con el botón derecho en la **carpeta de recursos**, que se encuentra en el **panel Proyecto**y, a continuación, haga clic en **crear** > **carpeta**. Llame a los **scripts**de la carpeta.

    ![](images/AzureLabs-Lab310-37.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla.

3.  Haga clic con el botón derecho en la carpeta y luego haga clic en **crear** > **script de C\#** . Asigne al script el nombre **CustomVisionAnalyser.**

4.  Haga doble clic en el nuevo script **CustomVisionAnalyser** para abrirlo con **Visual Studio.**

5.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia en la parte superior del archivo:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  En la clase **CustomVisionAnalyser** , agregue las siguientes variables:

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
    > Asegúrese de insertar la **clave de predicción de servicio** en la **variable PredictionKey** y el **punto de conexión de predicción** en la variable **predictionEndpoint** . Los copió en [el Bloc de notas anterior, en el capítulo 2, paso 14](#chapter-2---training-your-custom-vision-project).

7.  Ahora es necesario agregar el código para **activo ()** para inicializar la variable de instancia:

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

8.  Agregue la corutina (con el método estático **GetImageAsByteArray ()** debajo de ella), que obtendrá los resultados del análisis de la imagen, capturado por la clase **ImageCapture** .

    > [!NOTE]
    > En la corutina **AnalyseImageCapture** , hay una llamada a la clase **SceneOrganiser** que se va a crear todavía. Por lo tanto, **deje las líneas comentadas por ahora**.

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

9. Elimine los métodos **Start ()** y **Update ()** , ya que no se usarán. 

10.  Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.

> [!IMPORTANT]
> Como se mencionó anteriormente, no se preocupe por el código que podría parecer que tiene un error, ya que proporcionaremos más clases pronto, lo que solucionará estos errores.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capítulo 6: crear la clase CustomVisionObjects

La clase que creará ahora es la clase **CustomVisionObjects** .

Este script contiene una serie de objetos utilizados por otras clases para serializar y deserializar las llamadas realizadas a la Custom Vision Service.

Para crear esta clase:

1.  Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Llame al script **CustomVisionObjects.**

2.  Haga doble clic en el nuevo script **CustomVisionObjects** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia en la parte superior del archivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Elimine los métodos **Start ()** y **Update ()** dentro de la clase **CustomVisionObjects** , esta clase debe estar ahora vacía.

    > [!WARNING]
    > Es importante que siga detenidamente la siguiente instrucción. Si coloca las nuevas declaraciones de clase dentro de la clase **CustomVisionObjects** , obtendrá errores de compilación en el [capítulo 10](#chapter-10---create-the-imagecapture-class), lo que indica que no se encuentran **AnalysisRootObject** y **BoundingBox** .

5.  Agregue las siguientes clases *fuera* de la clase **CustomVisionObjects** . La biblioteca **Newtonsoft** usa estos objetos para serializar y deserializar los datos de respuesta:

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

6.  Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capítulo 7: creación de la clase SpatialMapping

Esta clase establecerá el **Colisionador de asignación espacial** en la escena para poder detectar colisiones entre objetos virtuales y objetos reales.

Para crear esta clase:

1.  Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Llame al script **SpatialMapping.**

2.  Haga doble clic en el nuevo script **SpatialMapping** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia sobre la clase **SpatialMapping** :

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  A continuación, agregue las siguientes variables dentro de la clase **SpatialMapping** , sobre el método **Start ()** :

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

5.  Agregue el **activo ()** y el **Inicio ()** :

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

6.  Elimine el método **Update ()** .

7.  Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Capítulo 8: creación de la clase GazeCursor

Esta clase es responsable de configurar el cursor en la ubicación correcta en el espacio real, mediante el uso de **SpatialMappingCollider**, que se creó en el capítulo anterior.

Para crear esta clase:

1.  Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Llame al script **GazeCursor**

2.  Haga doble clic en el nuevo script **GazeCursor** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene el siguiente espacio de nombres al que se hace referencia sobre la clase **GazeCursor** :

    ```csharp
    using UnityEngine;
    ```

4.  A continuación, agregue la variable siguiente dentro de la clase **GazeCursor** , sobre el método **Start ()** . 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Actualice el método **Start ()** con el siguiente código:

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

6.  Actualice el método **Update ()** con el siguiente código:

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
    > No se preocupe por el error de la clase **SceneOrganiser** que no se encuentra, la creará en el siguiente capítulo.

7. Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capítulo 9: creación de la clase SceneOrganiser

Esta clase hará lo siguiente:

-   Configure la *cámara principal* adjuntando los componentes adecuados.

-   Cuando se detecta un objeto, será responsable de calcular su posición en el mundo real y de colocar una etiqueta de **etiqueta** cerca del **nombre de etiqueta**adecuado.    

Para crear esta clase:

1.  Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Asigne al script el nombre **SceneOrganiser**.

2.  Haga doble clic en el nuevo script **SceneOrganiser** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia sobre la clase **SceneOrganiser** :

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  A continuación, agregue las siguientes variables dentro de la clase **SceneOrganiser** , sobre el método **Start ()** :

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

5.  Elimine los métodos **Start ()** y **Update ()** .

6.  Debajo de las variables, agregue el método **activo ()** , que inicializará la clase y configurará la escena.

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

7.  Agregue el método **PlaceAnalysisLabel ()** , que creará *una instancia* de la etiqueta en la escena (que en este punto es invisible para el usuario). También coloca el cuádruple (también invisible) en el que se coloca la imagen y se superpone con el mundo real. Esto es importante porque las coordenadas del cuadro recuperadas del servicio después del análisis se devuelven a este cuádruple para determinar la ubicación aproximada del objeto en el mundo real. 

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

8.  Agregue el método **FinaliseLabel ()** . Es responsable de:

    *   Establecer el texto de la *etiqueta* con la *etiqueta* de la predicción con la mayor confianza.
    *   Llamar al cálculo del *cuadro de límite* en el objeto cuádruple, colocado previamente y colocar la etiqueta en la escena.
    *   Ajustar la profundidad de la etiqueta mediante una Raycast hacia el *cuadro de límite*, que debe entrar en conflicto con el objeto en el mundo real.
    * Restablecer el proceso de captura para permitir que el usuario Capture otra imagen.

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

9.  Agregue el método **CalculateBoundingBoxPosition ()** , que hospeda varios cálculos necesarios para traducir las coordenadas del *cuadro de límite* recuperadas del servicio y volver a crearlas proporcionalmente en el cuádruple.

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

10. Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.

    > [!IMPORTANT]
    > Antes de continuar, abra la clase **CustomVisionAnalyser** y, en el método **AnalyseLastImageCaptured ()** , *Quite las marcas de comentario* de las líneas siguientes:
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
> No se preocupe por el mensaje "no se encontró la clase **ImageCapture** ", se creará en el siguiente capítulo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capítulo 10: creación de la clase ImageCapture

La clase siguiente que va a crear es la clase **ImageCapture** .

Esta clase es responsable de:

*   Captura de una imagen con la cámara de HoloLens y su almacenamiento en la carpeta de la *aplicación* .
*   Controlar los gestos de *TAP* del usuario.

Para crear esta clase:

1.  Vaya a la carpeta scripts que creó anteriormente.

2.  Haga clic con el botón derecho en la carpeta y luego haga clic en **crear** > **script de C\#** . Asigne al script el nombre **ImageCapture**.

3.  Haga doble clic en el nuevo script **ImageCapture** para abrirlo con **Visual Studio.**

4.  Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro de la clase **ImageCapture** , sobre el método **Start ()** :

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

6.  Ahora es necesario agregar el código para los métodos **activo ()** e **Inicio ()** :

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

7.  Implemente un controlador que se llamará cuando se produzca un gesto de punteo:

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
    > Cuando el cursor está en **verde**, significa que la cámara está disponible para tomar la imagen. Cuando el cursor está en **rojo**, significa que la cámara está ocupada.

8.  Agregue el método que usa la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen:

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

9.  Agregue los controladores a los que se llamará cuando se haya capturado la foto y cuando esté listo para su análisis. A continuación, el resultado se pasa a **CustomVisionAnalyser** para su análisis.

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

10. Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capítulo 11: configuración de los scripts de la escena

Ahora que ha escrito todo el código necesario para este proyecto, es el momento de configurar los scripts en la escena y en Prefabs para que se comporten correctamente.

1.  Dentro del **Editor de Unity**, en el **Panel jerarquía**, seleccione la **cámara principal**.
2.  En el **panel Inspector**, con la **cámara principal** seleccionada, haga clic en **Agregar componente**, busque el script **SceneOrganiser** y haga doble clic en, para agregarlo.

    ![](images/AzureLabs-Lab310-38.png)

3.  En el **panel Proyecto**, abra la **carpeta Prefabs**, arrastre la **etiqueta** recurso prefabricado al área de entrada de destino de referencia vacía de *etiqueta* , en el script **SceneOrganiser** que acaba de agregar a la *cámara principal*, como se muestra en la imagen siguiente:

    ![](images/AzureLabs-Lab310-39.png)

4.  En el **Panel jerarquía**, seleccione el elemento secundario **GazeCursor** de la **cámara principal**.
5.  En el **panel Inspector**, con la **GazeCursor** seleccionada, haga clic en **Agregar componente**, busque el script **GazeCursor** y haga doble clic en para agregarlo.

    ![](images/AzureLabs-Lab310-40.png)

6.  De nuevo, en el **Panel jerarquía**, seleccione el elemento secundario **SpatialMapping** de la **cámara principal**.
7.  En el **panel Inspector**, con la **SpatialMapping** seleccionada, haga clic en **Agregar componente**, busque el script **SpatialMapping** y haga doble clic en para agregarlo.

    ![](images/AzureLabs-Lab310-41.png)

Los scripts restantes que no haya establecido se agregarán mediante el código del script **SceneOrganiser** , durante el tiempo de ejecución.

## <a name="chapter-12---before-building"></a>Capítulo 12: antes de la compilación

Para realizar una prueba exhaustiva de la aplicación, debe transferirla a Microsoft HoloLens.

Antes de hacerlo, asegúrese de que:

-  Toda la configuración mencionada en el [capítulo 3](#chapter-3---set-up-the-unity-project) se establece correctamente.
- El script **SceneOrganiser** se adjunta al objeto de **cámara principal** .
- El script **GazeCursor** se adjunta al objeto **GazeCursor** .
- El script **SpatialMapping** se adjunta al objeto **SpatialMapping** .
- En el [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), paso 6:

    - Asegúrese de insertar la clave de predicción de **servicio** en la variable **predictionKey** .
    - Ha insertado el **punto de conexión** de predicción en la clase **predictionEndpoint** .

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capítulo 13: compilar la solución UWP y transferir localmente la aplicación

Ya está listo para compilar la aplicación como una solución de UWP en la que podrá realizar la implementación en Microsoft HoloLens. Para comenzar el proceso de compilación:

1.  Vaya a **archivo > configuración de compilación**.

2.  Marque **proyectos de\# Unity C**.

3.  Haga clic en **Agregar escenas abiertas**. Esto agregará la escena abierta actualmente a la compilación.

    ![](images/AzureLabs-Lab310-42.png)

4.  Haz clic en **Compilación**. Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y asígnele el nombre **App**. Después, con la carpeta de la **aplicación** seleccionada, haga clic en **Seleccionar carpeta**.

5.  Unity comenzará a compilar el proyecto en la carpeta de la **aplicación** .

6.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).

7.  Para realizar la implementación en Microsoft HoloLens, necesitará la dirección IP de ese dispositivo (para la implementación remota) y para asegurarse de que también tiene establecido el **modo de desarrollador** . Para ello:

    1.  Mientras se contenga HoloLens, abra la **configuración**.

    2.  Vaya a **red &**  > **Opciones avanzadas** **de Wi-Fi** > de Internet

    3.  Anote la dirección **IPv4** .

    4.  A continuación, vuelva a **configuración**y, a continuación, **actualice & Security** > **para desarrolladores**

    5.  Establezca el **modo de desarrollador** *en*.

8.  Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.

9.  En la configuración de soluciones, seleccione Depurar.

10. En la plataforma de la solución, seleccione **x86, equipo remoto**. Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (Microsoft HoloLens, en este caso, que anotó).

    ![](images/AzureLabs-Lab310-43.png)

11. Vaya al menú compilar y haga clic en **implementar solución** para transferir localmente la aplicación a HoloLens.

12. La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en Microsoft HoloLens, lista para su lanzamiento.

### <a name="to-use-the-application"></a>Para usar la aplicación:

* Examine un objeto, que ha entrenado con la Custom Vision Service de **Azure, la detección de objetos**y use el **gesto de TAP**.
* Si el objeto se detecta correctamente, aparecerá un texto de *etiqueta* de espacio mundial con el nombre de la etiqueta.

> [!IMPORTANT]
> Cada vez que capture una foto y la envíe al servicio, puede volver a la página de servicio y volver a entrenar el servicio con las imágenes recién capturadas. Al principio, probablemente también tendrá que corregir los *cuadros de límite* para ser más precisos y volver a entrenar el servicio.

> [!NOTE]
> El texto de la etiqueta que se coloca podría no aparecer cerca del objeto cuando los sensores de Microsoft HoloLens y/o SpatialTrackingComponent en Unity no pueden colocar los colisionadores adecuados, en relación con los objetos reales. Si es así, intente usar la aplicación en una superficie diferente.

## <a name="your-custom-vision-object-detection-application"></a>La aplicación de detección de objetos de Custom Vision

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el Custom Vision de Azure, la API de detección de objetos, que puede reconocer un objeto de una imagen y, a continuación, proporcionar una posición aproximada para ese objeto en el espacio 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

Agregando a la etiqueta de texto, use un cubo semitransparente para ajustar el objeto real en un *cuadro de límite*3D.

### <a name="exercise-2"></a>Ejercicio 2

Entrenar el Custom Vision Service para reconocer más objetos.

### <a name="exercise-3"></a>Ejercicio 3

Reproducir un sonido cuando se reconoce un objeto.

### <a name="exercise-4"></a>Ejercicio 4

Use la API para volver a entrenar su servicio con las mismas imágenes que está analizando la aplicación, para que el servicio sea más preciso (realice la predicción y el entrenamiento simultáneamente).
