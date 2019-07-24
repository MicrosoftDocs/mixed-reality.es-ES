---
title: 'MR y Azure 302B: visión personalizada'
description: Complete este curso para aprender a entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, visión personalizada, hololens, envolventes, VR
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63553563"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR y Azure 302B: Visión personalizada

En este curso, aprenderá a reconocer el contenido visual personalizado dentro de una imagen proporcionada, con las funcionalidades de Azure Custom Vision en una aplicación de realidad mixta.

Este servicio le permitirá entrenar un modelo de aprendizaje automático mediante imágenes de objeto. A continuación, usará el modelo entrenado para reconocer objetos similares, tal y como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara conectada a su equipo para auriculares envolvente (VR).

![resultado del curso](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision es un servicio cognitivo de Microsoft que permite a los desarrolladores crear clasificadores de imágenes personalizados. Estos clasificadores se pueden usar con nuevas imágenes para reconocer o clasificar objetos dentro de la nueva imagen. El servicio proporciona un portal en línea sencillo y fácil de usar para simplificar el proceso. Para obtener más información, visite la [Página de Custom Vision Service de Azure](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

Al finalizar este curso, tendrá una aplicación de realidad mixta que podrá trabajar en dos modos:

-   **Modo de análisis**: configurar el Custom Vision Service manualmente mediante la carga de imágenes, la creación de etiquetas y el entrenamiento del servicio para reconocer objetos diferentes (en este caso, el mouse y el teclado). Después creará una aplicación de HoloLens que capturará imágenes mediante la cámara e intentará reconocer esos objetos en el mundo real.

-   **Modo de entrenamiento**: implementará código que habilitará un "modo de entrenamiento" en la aplicación. El modo de entrenamiento le permitirá capturar imágenes mediante la cámara de HoloLens, cargar las imágenes capturadas en el servicio y entrenar el modelo de visión personalizada.

Este curso le enseñará cómo obtener los resultados de la Custom Vision Service en una aplicación de ejemplo basada en Unity. Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 302B: Visión personalizada</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR). Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio). Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se enumera a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Una cámara conectada al equipo (para el desarrollo de auriculares envolvente)
- Acceso a Internet para la instalación de Azure y Custom Vision la recuperación de API
- Una serie de al menos cinco (5) imágenes (diez (10) recomendado) para cada objeto que desea que reconozca el Custom Vision Service. Si lo desea, puede usar [las imágenes que ya se proporcionan con este curso (un mouse de equipo y un teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
2.  Configure y pruebe su HoloLens. Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capítulo 1: portal de Custom Vision Service

Para usar el *Custom Vision Service* en Azure, debe configurar una instancia del servicio para que esté disponible para la aplicación.

1.  En primer lugar, [vaya a la Página principal de *Custom Vision Service* ](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Haga clic en **el botón** introducción.

    ![](images/AzureLabs-Lab302b-01.png)

3.  Inicie sesión en el portal de *Custom Vision Service* .

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

4.  Una vez iniciada la sesión por primera vez, se le solicitará el panel *de condiciones de servicio* . Haga clic en la casilla para aceptar los términos. A continuación, haga clic en **acepto.**

    ![](images/AzureLabs-Lab302b-03.png)

5.  Una vez aceptados los términos, se le dirigirá a la sección *proyectos* del portal. Haga clic en **nuevo proyecto**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Aparecerá una pestaña en el lado derecho, que le pedirá que especifique algunos campos para el proyecto.

    1.  Inserte un *nombre* para el proyecto.

    2.  Inserte una *Descripción* para el proyecto (*opcional*).

    3.  Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

    4. Establecer los *tipos de proyecto* en **clasificación**
    
    5. Establezca los *dominios* como **generales**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Cuando haya terminado, haga clic en **Create Project (crear proyecto**), se le redirigirá a la página Custom Vision Service, Project (proyecto).

## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2: entrenar el proyecto de Custom Vision

Una vez en el portal de Custom Vision, el objetivo principal es entrenar el proyecto para que reconozca objetos específicos en las imágenes. Necesita al menos cinco (5) imágenes, aunque se prefiere diez (10) para cada objeto que desea que reconozca la aplicación. [Puede usar las imágenes proporcionadas con este curso (un mouse de equipo y un teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Para entrenar su proyecto de Custom Vision Service:

1.  Haga clic en **+** el botón situado junto a **etiquetas.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Agregue el **nombre** del objeto que desea reconocer. Haga clic en **Guardar**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Observará que se ha agregado la **etiqueta** (es posible que tenga que volver a cargar la página para que aparezca). Haga clic en la casilla junto a la nueva etiqueta, si aún no está activada.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Haga clic en **Agregar imágenes** en el centro de la página.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Haga clic en **examinar archivos locales**y busque y, a continuación, seleccione las imágenes que desea cargar y, como mínimo, cinco (5). Recuerde que todas estas imágenes deben contener el objeto al que va a entrenar.

    > [!NOTE]
    >  Puede seleccionar varias imágenes a la vez para cargarlas.

6.  Una vez que pueda ver las imágenes en la pestaña, seleccione la etiqueta adecuada en el cuadro **mis etiquetas** .

    ![](images/AzureLabs-Lab302b-10.png)

7.  Haga clic en **cargar archivos**. Los archivos comenzarán a cargarse. Una vez que haya confirmado la carga, haga clic en **listo**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Repita el mismo proceso para crear una nueva **etiqueta** denominada **teclado** y cargar las fotos adecuadas para ella. Asegúrese de **desactivar** el *mouse* una vez que haya creado las nuevas etiquetas para que se muestre la ventana *Agregar imágenes* .

9.  Una vez que tenga ambas etiquetas configuradas, haga clic en **entrenar**y la primera iteración de entrenamiento comenzará a compilarse.

    ![](images/AzureLabs-Lab302b-12.png)

10. Una vez compilada, podrá ver dos botones denominados establecer **dirección URL** **predeterminada** y de predicción. Haga clic en **establecer como predeterminado** primero y luego haga clic en **dirección URL**de predicción.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > La dirección URL del punto de conexión que se proporciona a partir de  este, se establece en la iteración que se haya marcado como predeterminada. Por lo tanto, si posteriormente realiza una nueva *iteración* y la actualiza como predeterminada, no necesitará cambiar el código.

11. Una vez que haya hecho clic en *dirección URL*de predicción, Abra *el Bloc de notas*y copie y pegue la **dirección URL** y la **clave de predicción**para que pueda recuperarla cuando la necesite más adelante en el código.

    ![](images/AzureLabs-Lab302b-14.png)

12. Haga clic en el **engranaje** de la parte superior derecha de la pantalla.

    ![](images/AzureLabs-Lab302b-15.png)

13. Copie la **clave de entrenamiento** y péguela en un *Bloc de notas*para su uso posterior.

    ![](images/AzureLabs-Lab302b-16.png)

14. Copie también el **identificador del proyecto**y péguelo en el archivo del *Bloc de notas* para su uso posterior.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: configuración del proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **nuevo**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity. Inserte **AzureCustomVision.** Asegúrese de que la plantilla de proyecto está establecida en **3D**. Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**. Vaya a **Editar* > *preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![](images/AzureLabs-Lab302b-19.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y seleccione **plataforma universal de Windows**y, después, haga clic en el botón **cambiar plataforma** para aplicar la selección.

    ![](images/AzureLabs-Lab302b-20.png)

5.  Mientras sigue en el **archivo > la configuración de compilación** y asegúrese de que:

    1.  El **dispositivo de destino** está establecido en **Hololens**

        > Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.
        
    2.  El **tipo de compilación** se establece en **D3D**
    3.  **SDK** está establecido en la **versión más reciente instalada**
    4.  La **versión de Visual Studio** está establecida en la **más reciente instalada**
    5.  **Compilar y ejecutar** está establecido en **equipo local**
    6.  Guarde la escena y agréguela a la compilación. 

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre Scenes.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo:* , escriba **CustomVisionScene**y, a continuación, haga clic en **Guardar**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Tenga en cuenta que debe guardar las escenas de Unity dentro de la carpeta *assets* , ya que deben estar asociadas con el proyecto Unity. La creación de la carpeta Scenes (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.
            
    7.  El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.

        ![](images/AzureLabs-Lab302b-24.png)

6.  En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .

7. En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  La **versión de scripting en tiempo de ejecución** debe ser **Experimental (.net 4,6 equivalente)** , lo que desencadenará una necesidad de reiniciar el editor.

        2. El **back-end** de scripting debe ser **.net**

        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        1. **InternetClient**

        2.  **Web**

        3. **Micrófono**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

    ![](images/AzureLabs-Lab302b-27.png)

8.  De nuevo en la *configuración de compilación* , los *proyectos de Unity C\#*  ya no están atenuados; Marque la casilla situada junto a este.

9.  Cierre la ventana Configuración de compilación.

10.  Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capítulo 4: importar el archivo DLL de Newtonsoft en Unity

> [!IMPORTANT]
> Si desea omitir el componente de *configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [Azure-Mr-302B. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo 6. ](#chapter-6---create-the-customvisionanalyser-class).

Este curso requiere el uso de la biblioteca **Newtonsoft** , que se puede agregar como un archivo DLL a los recursos. El paquete que contiene [esta biblioteca se puede descargar desde este vínculo](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que se incluía con este curso.

1.  Agregue el *. unitypackage Tools* a Unity mediante la opción de menú de * >  *paquetes* *importar* *paquete* > *personalizado** de paquetes.

2.  En el cuadro **importar paquete Unity** que aparece, asegúrese de que todo lo que hay en **Complementos** (y incluido) está seleccionado.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Haga clic en el botón **importar** para agregar los elementos al proyecto.

4.  Vaya a la carpeta **Newtonsoft** en **Complementos** en la vista de proyecto y seleccione el *complemento Newtonsoft. JSON*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Con el *complemento Newtonsoft. JSON* seleccionado, asegúrese de que **cualquier plataforma** esté desactivada, asegúrese de que **WSAPlayer** también está desactivado y haga clic en **aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Al marcar estos complementos, se configuran para que solo se usen en el editor de Unity. Hay un conjunto diferente de ellos en la carpeta WSA que se usará después de exportar el proyecto desde Unity.

6.  A continuación, debe abrir la carpeta **WSA** , dentro de la carpeta **Newtonsoft** Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector, asegúrese de que
    -   **Cualquier plataforma** está  desactivada 
    -   **solo** **WSAPlayer** está **activado**
    -   No **procesar** está **activado**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capítulo 5: configuración de la cámara

1.  En el panel jerarquía, seleccione la *cámara principal*.

2.  Una vez seleccionado, podrá ver todos los componentes de la *cámara principal* en el *panel del inspector*.

    1.  El objeto de *cámara* debe tener el nombre de la **cámara principal** (tenga en cuenta la ortografía).

    2.  La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía).

    3.  Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**

    4.  Establezca **marcas** de borrado en **color sólido** (Ignore esto para los auriculares inmersivo).

    5.  Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)** (no se tiene en cuenta para el casco inmersivo).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capítulo 6: crear la clase CustomVisionAnalyser.

En este momento está listo para escribir código.

Comenzará con la clase *CustomVisionAnalyser* .

> [!NOTE]
> Las llamadas a la **Custom Vision Service** realizada en el código que se muestra a continuación se realizan mediante la **API de REST de Custom Vision**. Mediante este procedimiento, verá cómo implementar y usar esta API (útil para entender cómo implementar algo similar por su cuenta). Tenga en cuenta que Microsoft ofrece un **SDK de Custom Vision Service** que también se puede usar para realizar llamadas al servicio. Para obtener más información, visite el artículo [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) .

Esta clase es responsable de:

-   Cargar la imagen más reciente capturada como una matriz de bytes.

-   Envío de la matriz de bytes a la instancia de Azure *Custom Vision Service* para su análisis.

-   Recibir la respuesta como una cadena JSON.

-   Deserializar la respuesta y pasar la *predicción* resultante a la clase *SceneOrganiser* , que se encargará de cómo se debe mostrar la respuesta.

Para crear esta clase:

1.  Haga clic con el botón secundario en la *carpeta de recursos* que se encuentra en el *panel Proyecto*y, a continuación, haga clic en **crear > carpeta**. Llame a los **scripts**de la carpeta.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla.

3.  Haga clic con el botón derecho en la carpeta y luego haga clic en **crear** > **script de C\#** . Asigne al script el nombre *CustomVisionAnalyser*.

4.  Haga doble clic en el nuevo script *CustomVisionAnalyser* para abrirlo con **Visual Studio**.

5.  Actualice los espacios de nombres en la parte superior del archivo para que coincidan con lo siguiente:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  En la clase *CustomVisionAnalyser* , agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Asegúrese de insertar la **clave** de predicción en la variable **PredictionKey** y el **punto de conexión** de predicción en la variable **predictionEndpoint** . Los copió en el *Bloc de notas* anteriormente en el curso.

7.  Ahora es necesario agregar el código para **activo ()** para inicializar la variable de instancia:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Elimine los métodos **Start ()** y **Update ()** .

9.  A continuación, agregue la corutina (con el método estático **GetImageAsByteArray ()** debajo de ella), que obtendrá los resultados del análisis de la imagen capturada por la clase *ImageCapture* .

    > [!NOTE]
    > En la corutina **AnalyseImageCapture** , hay una llamada a la clase *SceneOrganiser* que se va a crear todavía. Por lo tanto, **deje las líneas comentadas por ahora**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capítulo 7: creación de la clase CustomVisionObjects

La clase que creará ahora es la clase *CustomVisionObjects* .

Este script contiene una serie de objetos utilizados por otras clases para serializar y deserializar las llamadas realizadas a la *Custom Vision Service*.

> [!WARNING]
> Es importante tomar nota del punto de conexión que le proporciona el Custom Vision Service, ya que se ha configurado la siguiente estructura JSON para que funcione con [*Custom Vision predicción v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Si tiene una versión diferente, puede que tenga que actualizar la siguiente estructura.

Para crear esta clase:

1.  Haga clic con el botón  derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Llame al script *CustomVisionObjects*.

2.  Haga doble clic en el nuevo script **CustomVisionObjects** para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres al principio del archivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Elimine los métodos **Start ()** y **Update ()** dentro de la clase *CustomVisionObjects* ; Esta clase debe estar ahora vacía.

5.  Agregue las siguientes clases **fuera** de la clase *CustomVisionObjects* . La biblioteca *Newtonsoft* usa estos objetos para serializar y deserializar los datos de respuesta:

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capítulo 8: creación de la clase VoiceRecognizer

Esta clase reconocerá la entrada de voz del usuario.

Para crear esta clase:

1.  Haga clic con el botón  derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Llame al script *VoiceRecognizer*.

2.  Haga doble clic en el nuevo script **VoiceRecognizer** para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres encima de la clase *VoiceRecognizer* :

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  A continuación, agregue las siguientes variables dentro de la clase *VoiceRecognizer* , sobre el método *Start ()* :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Agregue los métodos **activo ()** e **Inicio ()** , que configurarán las *palabras clave* del usuario para que se reconozcan al asociar una etiqueta a una imagen:

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Elimine el método **Update ()** .

7.  Agregue el siguiente controlador, al que se llama cada vez que se reconoce la entrada de voz:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.

> [!NOTE]
> No se preocupe por el código que podría parecer que presenta un error, ya que proporcionaremos más clases pronto, lo que solucionará estos errores.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capítulo 9: creación de la clase CustomVisionTrainer

Esta clase encadenará una serie de llamadas web para entrenar el *Custom Vision Service*. Cada llamada se explicará en detalle justo encima del código.

Para crear esta clase:

1.  Haga clic con el botón  derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Llame al script *CustomVisionTrainer*.

2.  Haga doble clic en el nuevo script *CustomVisionTrainer* para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres encima de la clase *CustomVisionTrainer* :

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  A continuación, agregue las siguientes variables dentro de la clase *CustomVisionTrainer* , sobre el método **Start ()** . 

    > [!NOTE]
    > La dirección URL de entrenamiento que se usa aquí se proporciona en la documentación de *Custom Vision training 1,2* y tiene una estructura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Para obtener más información, visite la [*API de referencia de Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > Es importante tener en cuenta el punto de conexión que el Custom Vision Service proporciona para el modo de entrenamiento, ya que la estructura JSON usada (dentro de la clase **CustomVisionObjects** ) se ha configurado para funcionar con [*Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). Si tiene una versión diferente, puede que tenga que actualizar la estructura de *objetos* .

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Asegúrese de agregar el valor de **clave de servicio** (clave de entrenamiento) y el valor de identificador de **proyecto** , que anotó anteriormente; Estos son los valores que [recopiló en el portal anteriormente en el curso (capítulo 2, paso 10 y posteriores)](#chapter-2---training-your-custom-vision-oroject).

5.  Agregue los siguientes métodos **Start ()** y Activate **()** . Estos métodos se llaman en la inicialización y contienen la llamada para configurar la interfaz de usuario:

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Elimine el método **Update ()** . Esta clase no la necesitará.

7.  Agregue el método **RequestTagSelection ()** . Este método es el primero que se llama cuando se ha capturado una imagen y se ha almacenado en el dispositivo y ahora está lista para enviarse al *Custom Vision Service*, para entrenarla. Este método muestra, en la interfaz de usuario de entrenamiento, un conjunto de palabras clave que el usuario puede usar para etiquetar la imagen que se ha capturado. También alerta a la clase *VoiceRecognizer* para empezar a escuchar al usuario de la entrada de voz.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Agregue el método **VerifyTag ()** . Este método recibirá la entrada de voz reconocida por la clase **VoiceRecognizer** y comprobará su validez y, a continuación, iniciará el proceso de entrenamiento.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Agregue el método **SubmitImageForTraining ()** . Este método iniciará el proceso de aprendizaje de Custom Vision Service. El primer paso consiste en recuperar el **ID** . de etiqueta del servicio que está asociado a la entrada de voz validada del usuario. El **ID** . de etiqueta se cargará junto con la imagen.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Agregue el método **TrainCustomVisionProject ()** . Una vez que la imagen se haya enviado y etiquetado, se llamará a este método. Se creará una nueva iteración que se entrenará con todas las imágenes anteriores enviadas al servicio más la imagen que se acaba de cargar. Una vez que se haya completado el entrenamiento, este método llamará a un método para establecer  la iteración recién creada como **predeterminada**, de modo que el punto de conexión que se usa para el análisis sea la iteración entrenada más reciente.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Agregue el método **SetDefaultIteration ()** . Este método establecerá la iteración previamente creada y entrenada como *predeterminada*. Una vez completado, este método tendrá que eliminar la iteración anterior existente en el servicio. En el momento de redactar este curso, existe un límite de diez (10) iteraciones máximas que pueden existir al mismo tiempo en el servicio.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Agregue el método **DeletePreviousIteration ()** . Este método buscará y eliminará la iteración no predeterminada anterior:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. El último método que se va a agregar en esta clase es el método **GetImageAsByteArray ()** , que se utiliza en las llamadas web para convertir la imagen capturada en una matriz de bytes.

    ```csharp
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

14. Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capítulo 10: creación de la clase SceneOrganiser

Esta clase hará lo siguiente:

-   Cree un objeto **cursor** para adjuntar a la cámara principal.

-   Cree un objeto de **etiqueta** que aparecerá cuando el servicio reconozca los objetos del mundo real.

-   Configure la cámara principal adjuntando los componentes adecuados.

-   En el **modo de análisis**, genere las etiquetas en tiempo de ejecución, en el espacio universal adecuado con respecto a la posición de la cámara principal, y muestre los datos recibidos de la Custom Vision Service.

-   En el **modo de entrenamiento**, cree la interfaz de usuario que mostrará las distintas fases del proceso de entrenamiento.

Para crear esta clase:

1.  Haga clic con el botón  derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** . Asigne al script el nombre *SceneOrganiser*.

2.  Haga doble clic en el nuevo script *SceneOrganiser* para abrirlo con **Visual Studio**.

3.  Solo necesitará un espacio de nombres, quite los otros de encima de la clase *SceneOrganiser* :

    ```csharp
    using UnityEngine;
    ```

4.  A continuación, agregue las siguientes variables dentro de la clase *SceneOrganiser* , sobre el método **Start ()** :

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Elimine los métodos **Start ()** y **Update ()** .

6.  Justo debajo de las variables, agregue el método **activo ()** , que inicializará la clase y configurará la escena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Ahora, agregue el método **CreateCameraCursor ()** que crea y coloca el cursor de cámara principal y el método **CreateLabel ()** , que crea el objeto de **etiqueta de análisis** .

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Agregue el método **SetCameraStatus ()** , que controlará los mensajes destinados a la malla de texto que proporciona el estado de la cámara.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Agregue los métodos **PlaceAnalysisLabel ()** y **SetTagsToLastLabel ()** , que generarán y mostrarán los datos del Custom Vision Service en la escena.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Por último, agregue el método **CreateTrainingUI ()** , que generará la interfaz de usuario que muestra las distintas fases del proceso de entrenamiento cuando la aplicación está en modo de entrenamiento. Este método también se utilizará para crear el objeto de estado de la cámara.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.

> [!IMPORTANT]
> Antes de continuar, abra la clase **CustomVisionAnalyser** y, en el método **AnalyseLastImageCaptured ()** , *Quite las marcas de comentario* de las líneas siguientes:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capítulo 11: creación de la clase ImageCapture

La clase siguiente que va a crear es la clase *ImageCapture* .

Esta clase es responsable de:

-   Captura de una imagen con la cámara de HoloLens y su almacenamiento en la carpeta de la *aplicación* .

-   Controlar los gestos de TAP del usuario.

-   Mantener el  valor de enumeración que determina si la aplicación se ejecutará en modo de *análisis* o en modo de *entrenamiento* .

Para crear esta clase:

1.  Vaya a la  carpeta scripts que creó anteriormente.

2.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic en **crear > script de\# C**. Asigne al script el nombre *ImageCapture*.

3.  Haga doble clic en el nuevo script **ImageCapture** para abrirlo con **Visual Studio**.

4.  Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro de la clase *ImageCapture* , sobre el método **Start ()** :

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implemente un controlador que se llamará cuando se produzca un gesto de TAP.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > En el modo de *análisis* , el método **TapHandler** actúa como un modificador para iniciar o detener el bucle de captura de fotografías.
    >
    > En el modo de *entrenamiento* , capturará una imagen de la cámara.
    >
    > Cuando el cursor está en verde, significa que la cámara está disponible para tomar la imagen.
    >
    > Cuando el cursor está en rojo, significa que la cámara está ocupada.

8.  Agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  Agregue los controladores a los que se llamará cuando se haya capturado la foto y cuando esté listo para su análisis. A continuación, el resultado se pasa a *CustomVisionAnalyser* o *CustomVisionTrainer* , en función del modo en el que se establece el código.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.

11. Ahora que todos los scripts se han completado, vuelva al editor de Unity, haga clic y arrastre la clase **SceneOrganiser** desde la carpeta **scripts** hasta el objeto de **cámara principal** en el *Panel de jerarquías*.

## <a name="chapter-12---before-building"></a>Capítulo 12: antes de la compilación

Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.

Antes de hacerlo, asegúrese de que:

- Toda la configuración mencionada en el [capítulo 2](#chapter-2---training-your-custom-vision-project) se establece correctamente.

- Todos los campos de la **cámara principal**, el panel Inspector, se asignan correctamente.

- El script **SceneOrganiser** se adjunta al objeto de **cámara principal** .

- Asegúrese de insertar la **clave** de predicción en la variable **predictionKey** .

- Ha insertado el **punto de conexión** de predicción en la variable **predictionEndpoint** .

- Ha insertado la **clave de entrenamiento** en la variable **trainingKey** de la clase *CustomVisionTrainer* .

- Ha insertado el **identificador del proyecto** en la variable **Projectid** de la clase *CustomVisionTrainer* .

## <a name="chapter-13---build-and-sideload-your-application"></a>Capítulo 13: compilar y transferir localmente la aplicación

Para comenzar el proceso de *compilación* :

1.  Vaya a **archivo > configuración de compilación**.

2.  Marque **proyectos de\# Unity C**.

3.  Haz clic en **Compilación**. Unity iniciará una ventana del **Explorador de archivos** , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y asígnele el nombre **App**. Después, con la carpeta de la **aplicación** seleccionada, haga clic en **Seleccionar carpeta**.

4.  Unity comenzará a compilar el proyecto en la carpeta de la **aplicación** .

5.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).

Para implementar en HoloLens:

1.  Necesitará la dirección IP de HoloLens (para la implementación remota) y para asegurarse de que HoloLens está en **modo de desarrollador**. Para ello:

    1.  Mientras se contenga HoloLens, abra la **configuración**.

    2.  Vaya a **red &**  > **Opciones avanzadas** **de Wi-Fi** > de Internet

    3.  Anote la dirección **IPv4** .

    4.  A continuación, vuelva a **configuración**y, a continuación, **actualice & Security** > **para desarrolladores**

    5.  Establezca el **modo de Desarrollador en**.

2.  Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.

3.  En la *configuración de soluciones* , seleccione Depurar.

4.  En la *plataforma*de la solución, seleccione **x86, equipo remoto**. Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (HoloLens, en este caso, que anotó).

    ![](images/AzureLabs-Lab302b-34.png)

5. Vaya al  menú compilar y haga clic en **implementar solución** para transferir localmente la aplicación a HoloLens.

6. La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.

> [!NOTE]
> Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local*y establezca la **configuración** en depurar, con  *x86* como **plataforma**. A continuación, implemente en el equipo local  mediante el elemento de menú compilar y seleccione *implementar solución*. 

## <a name="to-use-the-application"></a>Para usar la aplicación:

Para cambiar la funcionalidad de la aplicación entre el modo de *entrenamiento* y el modo de predicción, debe actualizar la variable **AppMode** , ubicada en el método  **activo ()** ubicado dentro de la clase *ImageCapture* .

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
o bien
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

En modo de *entrenamiento* :

- Fíjese en **mouse** o **teclado** y use el **gesto**de puntear.

- A continuación, aparecerá texto en el que se le pedirá que proporcione una etiqueta.

- Por ejemplo, el **mouse** o el **teclado**.


En  modo de predicción:

- Mire un objeto y use el **gesto**de puntear.

- Aparecerá el texto proporcionando el objeto detectado, con la probabilidad más alta (se normaliza).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capítulo 14: evaluación y mejora del modelo de Custom Vision

Para que el servicio sea más preciso, debe seguir entrenar el modelo usado para la predicción. Esto se logra mediante el uso de la nueva aplicación, con los modos de *entrenamiento* y predicción, con los que se necesitan para visitar el portal, que es lo que se trata en este capítulo. Esté preparado para volver a visitar su portal muchas veces, para mejorar continuamente el modelo.

1. Vuelva al portal de Azure Custom Vision y, una vez que esté en el proyecto, seleccione la  pestaña predicciones (en el centro superior de la página):

    ![](images/AzureLabs-Lab302b-35.png)

2. Verá todas las imágenes que se enviaron al servicio mientras se ejecutaba la aplicación. Si mantiene el mouse sobre las imágenes, le proporcionará las predicciones que se realizaron para esa imagen:

    ![](images/AzureLabs-Lab302b-36.png)

3. Seleccione una de las imágenes para abrirla. Una vez abierta, verá las predicciones realizadas para esa imagen a la derecha. Si las predicciones son correctas y desea agregar esta imagen al modelo de entrenamiento del servicio, haga clic en el cuadro de entrada *mis etiquetas* y seleccione la etiqueta que desea asociar. Cuando haya terminado, haga clic en el botón *Guardar y cerrar* situado en la parte inferior derecha y continúe con la imagen siguiente.

    ![](images/AzureLabs-Lab302b-37.png)

4. Una vez que vuelva a la cuadrícula de imágenes, observará que se quitarán las imágenes que haya agregado etiquetas (y guardado). Si encuentra alguna imagen que cree que no tiene el elemento etiquetado, puede eliminarlas haciendo clic en la marca de la imagen (puede hacer esto para varias imágenes) y, a continuación, hacer clic en *eliminar* en la esquina superior derecha de la página de cuadrícula. En el menú emergente que aparece a continuación, puede hacer clic en *sí, eliminar* o *no*, para confirmar la eliminación o cancelarla, respectivamente. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Cuando esté listo para continuar, haga clic en el botón verde *entrenar* situado en la parte superior derecha. El modelo de servicio se entrenará con todas las imágenes que ya ha proporcionado (lo que hará que sea más preciso). Una vez completado el entrenamiento, asegúrese de hacer clic en el botón *establecer como predeterminado* una vez más para que la *dirección URL* de predicción siga usando la iteración más actualizada del servicio.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Su aplicación de API de Custom Vision finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Custom Vision API para reconocer objetos reales, entrenar el modelo de servicio y mostrar la confianza de lo que se ha detectado.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

Entrenar el **Custom Vision Service** para reconocer más objetos.

### <a name="exercise-2"></a>Ejercicio 2

Para ampliar la información que ha aprendido, complete los siguientes ejercicios:

Reproducir un sonido cuando se reconoce un objeto.

### <a name="exercise-3"></a>Ejercicio 3

Use la API para volver a entrenar su servicio con las mismas imágenes que está analizando la aplicación, para que el servicio sea más preciso (realice la predicción y el entrenamiento simultáneamente).
