---
title: El Sr. y Azure 302b - visión personalizada
description: Complete este curso para obtener información sobre cómo entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, visión personalizada, hololens, envolventes, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599998"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>El Sr. y 302b Azure: Visión personalizada

En este curso, obtendrá información sobre cómo reconocer contenido visual personalizado dentro de una imagen proporcionada, con las funciones de visión personalizada de Azure en una aplicación de realidad mixta.

Este servicio, podrá entrenar un modelo de aprendizaje automático mediante imágenes de objeto. A continuación, usará el modelo entrenado para reconocer objetos similares, tal como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara conectada a su equipo para inmersivos (VR).

![resultado del curso](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision es un servicio de Microsoft Cognitive que permite a los desarrolladores crear clasificadores de imagen personalizada. A continuación, pueden utilizarse con las nuevas imágenes para reconocer estos clasificadores o clasificación objetos dentro de esa imagen. El servicio proporciona un portal fácil de usar, sencillo y en línea para agilizar el proceso. Para obtener más información, visite la [página Azure Custom Vision Service](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá trabajar en dos modos:

-   **Modo de análisis**: configuración de Custom Vision Service manualmente mediante la carga de imágenes, crear etiquetas y el servicio de entrenamiento para reconocer objetos diferentes (en este caso mouse y teclado). A continuación, creará una aplicación de HoloLens que se captura de imágenes con la cámara e intenta reconocer esos objetos en el mundo real.

-   **Modo de formación**: implementará código que le permitirán un "modo de aprendizaje" en la aplicación. El modo de formación, podrá capturar imágenes con la cámara de HoloLens, cargar las imágenes capturadas en el servicio y entrenar el modelo de visión personalizada.

Este curso le mostrará cómo obtener los resultados de Custom Vision Service en una aplicación de ejemplo basada en Unity. Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y 302b Azure: Visión personalizada</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality. Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC. Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK más reciente de Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Una cámara conectada a su equipo (para el desarrollo de amplias auriculares)
- Acceso a Internet para el programa de instalación de Azure y la recuperación de Custom Vision API
- Una serie de imágenes de al menos cinco (5) (¡diez (10) recomienda) para cada objeto que le gustaría Custom Vision Service para que reconozca. Si lo desea, puede usar [las imágenes que ya se proporciona con este curso (un mouse y teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
2.  Configurar y probar su HoloLens. Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar dichas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capítulo 1: Custom Vision Service Portal

Para usar el *Custom Vision Service* en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.

1.  Primero, [vaya a la *Custom Vision Service* página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Haga clic en el **comenzar** botón.

    ![](images/AzureLabs-Lab302b-01.png)

3.  Inicie sesión en el *Custom Vision Service* Portal.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

4.  Una vez que haya iniciado sesión por primera vez, se le pedirá con el *condiciones del servicio* panel. Haga clic en la casilla de verificación para aceptar los términos. A continuación, haga clic en **acepto**.

    ![](images/AzureLabs-Lab302b-03.png)

5.  Tener aceptado los términos, se abrirá el *proyectos* sección del Portal. Haga clic en **nuevo proyecto**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Aparecerá una ficha en el lado derecho, que le solicitará que especifique algunos campos para el proyecto.

    1.  Insertar un *nombre* para el proyecto.

    2.  Insertar un *descripción* para el proyecto (*opcional*).

    3.  Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).

    4. Establecer el *tipos de proyecto* a **clasificación**
    
    5. Establecer el *dominios* como **General**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Una vez haya terminado, haga clic en **crear un proyecto**, se le redirigirá a Custom Vision Service, página del proyecto.

## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2: el proyecto de Custom Vision de entrenamiento

Una vez en el portal de Custom Vision, su principal objetivo es entrenar su proyecto para reconocer objetos específicos en las imágenes. Necesita al menos cinco (5) las imágenes, aunque diez (10) se prefiere, para cada objeto que desea que la aplicación reconozca. [Puede usar las imágenes proporcionadas con este curso (un mouse y teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Para entrenar el proyecto de Custom Vision Service:

1.  Haga clic en el **+** situado junto a **etiquetas.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Agregar el **nombre** del objeto que desea reconocer. Haga clic en **guardar**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Observará el **etiqueta** se ha agregado (es posible que deba volver a cargar la página para que aparezca). Haga clic en la casilla de verificación junto a la nueva etiqueta, si ya no está seleccionada.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Haga clic en **agregar imágenes** en el centro de la página.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Haga clic en **examinar archivos locales**y de búsqueda, a continuación, seleccione las imágenes que desea cargar, siendo el mínimo cinco (5). Recuerde que todas estas imágenes deben contener el objeto que está enseñando.

    > [!NOTE]
    >  Puede seleccionar varias imágenes a la vez, para cargar.

6.  Una vez que se puede ver las imágenes en la ficha, seleccione la etiqueta correspondiente en el **Mis etiquetas** cuadro.

    ![](images/AzureLabs-Lab302b-10.png)

7.  Haga clic en **cargar archivos**. Los archivos cargarán. Una vez que la confirmación de la carga, haga clic en **realiza**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Repita el mismo proceso para crear un nuevo **etiqueta** denominado **teclado** y cargue las fotos adecuadas para él. No olvide **desactive** *Mouse* después de crear las nuevas etiquetas, por lo que para mostrar el *agregar imágenes* ventana.

9.  Una vez que tenga dos etiquetas configurar, haga clic en **Train**, y la primera iteración de entrenamiento se iniciará la creación.

    ![](images/AzureLabs-Lab302b-12.png)

10. Una vez compilada, podrá ver dos botones denominados **Predeterminar** y **predicción URL**. Haga clic en **Predeterminar** en primer lugar, a continuación, haga clic en **predicción URL**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > La dirección URL del extremo que se proporciona con esto, se establece en lo que ocurra *iteración* está marcada como predeterminada. Como tal, si posteriormente realiza una nueva *iteración* y actualizarlo como valor predeterminado, no necesitará cambiar el código.

11. Una vez que ha hecho clic *dirección URL de la predicción*, abra *el Bloc de notas*y copie y pegue el **URL** y el **predicción clave**, para que pueda recuperarlo cuando necesite más adelante en el código.

    ![](images/AzureLabs-Lab302b-14.png)

12. Haga clic en el **engranaje** en la parte superior derecha de la pantalla.

    ![](images/AzureLabs-Lab302b-15.png)

13. Copia el **clave entrenamiento** y péguelo en un *el Bloc de notas*, para su uso posterior.

    ![](images/AzureLabs-Lab302b-16.png)

14. Copie también el **Id. de proyecto**y péguela también en su *el Bloc de notas* archivo para su uso posterior.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **New**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Insertar **AzureCustomVision.** Asegúrese de que la plantilla de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **editar* > *preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![](images/AzureLabs-Lab302b-19.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.

    ![](images/AzureLabs-Lab302b-20.png)

5.  Mientras sigue en **archivo > configuración de compilación** y asegúrese de que:

    1.  **Dispositivo de destino** está establecido en **Hololens**

        > Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.
        
    2.  **Tipo de compilación** está establecido en **D3D**
    3.  **SDK** está establecido en **instalada más reciente**
    4.  **Versión de Visual Studio** está establecido en **instalada más reciente**
    5.  **Compilar y ejecutar** está establecido en **máquina Local**
    6.  Guarde la escena y agregarlo a la compilación. 

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo:* campo de texto, escriba **CustomVisionScene**, a continuación, haga clic en **guardar**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity. Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.
            
    7.  El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.

        ![](images/AzureLabs-Lab302b-24.png)

6.  En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental (.NET 4.6 equivalente)**, lo que desencadenará una necesidad de reiniciar el Editor.

        2. **Scripting de back-end** debe ser **.NET**

        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        1. **InternetClient**

        2.  **Webcam**

        3. **Micrófono**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.

    ![](images/AzureLabs-Lab302b-27.png)

8.  En *configuración de compilación* *Unity C\# proyectos* ya no está atenuada; Marque la casilla situada junto a esto.

9.  Cierre la ventana de configuración de compilación.

10.  Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capítulo 4: importar el archivo DLL de Newtonsoft en Unity

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [MR-Azure-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 6](#chapter-6---create-the-customvisionanalyser-class).

Este curso requiere el uso de la **Newtonsoft** biblioteca, que puede agregar como un archivo DLL a los recursos. El paquete que contiene [esta biblioteca se puede descargar desde este vínculo](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que acompaña a este curso.

1.  Agregar el *.unitypackage* a Unity mediante el uso de la **activos* > *importación* *paquete*  >  *Personalizado* *paquete** opción de menú.

2.  En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Haga clic en el **importación** para agregar los elementos al proyecto.

4.  Vaya a la **Newtonsoft** carpeta bajo **complementos** en la vista de proyecto y seleccione el *Newtonsoft.Json complemento*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Con el *Newtonsoft.Json complemento* seleccionado, asegúrese de que **cualquier plataforma** es **unchecked**, a continuación, asegúrese de que **WSAPlayer** también es **unchecked**, a continuación, haga clic en **aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Marcar estos complementos configura para su uso en el Editor de Unity. Hay un conjunto diferente de ellos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.

6.  A continuación, deberá abrir el **WSA** carpeta, en el **Newtonsoft** carpeta. Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector, asegúrese de que
    -   **Cualquier plataforma** es **desactivada** 
    -   **solo** **WSAPlayer** es **activada**
    -   **No procesar** es **activada**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capítulo 5: configuración de cámara

1.  En el Panel de la jerarquía, seleccione la *cámara principal*.

2.  Una vez seleccionado, podrá ver todos los componentes de la *cámara principal* en el *Panel Inspector*.

    1.  El *cámara* objeto debe denominarse **cámara principal** (tenga en cuenta la ortografía!)

    2.  La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)

    3.  Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**

    4.  Establecer **borrar las marcas** a **Color sólido** (omitir esto para envolventes auriculares).

    5.  Establecer el **en segundo plano** Color de la cámara al **negro, alfa de 0 (código hexadecimal: #00000000)** (omitir esto para envolventes auriculares).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capítulo 6: crear la clase CustomVisionAnalyser.

En este momento está listo para escribir código.

Se iniciará con la *CustomVisionAnalyser* clase.

> [!NOTE]
> Las llamadas a la **Custom Vision Service** realizados en el código se muestra a continuación se realizan utilizando el **API de REST de Custom Vision**. A través del uso de esto, verá cómo implementar y hacer uso de esta API (útil para comprender cómo implementar algo similar en su propio). Tenga en cuenta que Microsoft ofrece un **Custom Vision Service SDK** que también se puede utilizar para realizar llamadas al servicio. Para obtener más información, visite la [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) artículo.

Esta clase es responsable de:

-   Cargando la última imagen de captura como una matriz de bytes.

-   Envío de la matriz de bytes en su Azure *Custom Vision Service* instancia para el análisis.

-   Recibir la respuesta como una cadena JSON.

-   Al deserializar la respuesta y el paso resultante *predicción* a la *SceneOrganiser* (clase), que se encargará de cómo se debe mostrar la respuesta.

Para crear esta clase:

1.  Haga clic en el *carpeta de activos* ubicado en el *Panel proyecto*, a continuación, haga clic en **crear > carpeta**. Llame a la carpeta **Scripts**.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirlo.

3.  Haga clic en la carpeta, a continuación, haga clic en **crear** > **C\# Script**. Nombre de la secuencia de comandos *CustomVisionAnalyser*.

4.  Haga doble clic en el nuevo *CustomVisionAnalyser* script para abrirlo con **Visual Studio**.

5.  Actualice los espacios de nombres en la parte superior del archivo para que coincida con lo siguiente:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  En el *CustomVisionAnalyser* de clases, agregue las siguientes variables:

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
    > Asegúrese de insertar el **clave predicción** en el **predictionKey** variable y su **punto de conexión de predicción** en el **predictionEndpoint** variable. Ha copiado a *el Bloc de notas* anteriormente en el curso.

7.  El código para **Awake()** ahora debe agregarse para inicializar la variable de instancia:

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

8.  Elimine los métodos **Start()** y **Update()**.

9.  A continuación, agregue la corrutina (con el método estático **GetImageAsByteArray()** método debajo de él), que obtendrá los resultados del análisis de la imagen capturada por la *ImageCapture* clase.

    > [!NOTE]
    > En el **AnalyseImageCapture** corrutina, hay una llamada a la *SceneOrganiser* clase que aún está a crear. Por lo tanto, **las deje líneas de comentarios por ahora**.

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

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capítulo 7: crear la clase CustomVisionObjects

La clase que se va a crear es ahora el *CustomVisionObjects* clase.

Este script contiene un número de objetos usados por otras clases para serializar y deserializar las llamadas realizadas a la *Custom Vision Service*.

> [!WARNING]
> Es importante tomar nota del punto de conexión que Custom Vision Service proporciona, como el siguiente código JSON estructura se ha configurado para trabajar con [ *Custom Vision predicción v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Si tiene una versión diferente, es posible que deba actualizar la siguiente estructura.

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Llame al script *CustomVisionObjects*.

2.  Haga doble clic en el nuevo **CustomVisionObjects** script para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres en la parte superior del archivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminar el **Start()** y **Update()** métodos dentro de la *CustomVisionObjects* clase; esta clase debe estar vacía.

5.  Agregue las siguientes clases **fuera** el *CustomVisionObjects* clase. Estos objetos se usan por el *Newtonsoft* library para serializar y deserializar los datos de respuesta:

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capítulo 8: crear la clase VoiceRecognizer

Esta clase reconocerá la entrada de voz del usuario.

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Llame al script *VoiceRecognizer*.

2.  Haga doble clic en el nuevo **VoiceRecognizer** script para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres anterior el *VoiceRecognizer* clase:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  A continuación, agregue las siguientes variables dentro de la *VoiceRecognizer* clase encima el *Start()* método:

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

5.  Agregar el **Awake()** y **Start()** métodos, que establecerá el usuario *palabras clave* para ser reconocido cuando asocia una etiqueta a una imagen:

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

6.  Eliminar el **Update()** método.

7.  Agregue el siguiente controlador, que se llama cada vez que se reconoce la entrada de voz:

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
> No se preocupe código que puede aparecer un error, ya que proporciona clases más pronto, lo que solucionará estas.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capítulo 9: crear la clase CustomVisionTrainer

Esta clase encadenará una serie de llamadas de web para entrenar el *Custom Vision Service*. Cada llamada se explicarán detalladamente justo encima del código.

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Llame al script *CustomVisionTrainer*.

2.  Haga doble clic en el nuevo *CustomVisionTrainer* script para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres anterior el *CustomVisionTrainer* clase:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  A continuación, agregue las siguientes variables dentro de la *CustomVisionTrainer* clase encima el **Start()** método. 

    > [!NOTE]
    > La dirección URL de entrenamiento usada aquí se proporciona en el *Custom Vision Training 1.2* documentación, y tiene una estructura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Para obtener más información, visite la [ *referencia v1.2 de Custom Vision Training API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > Es importante tomar nota del punto de conexión que Custom Vision Service se proporciona para el modo de formación, como la estructura de JSON utilizada (dentro de la **CustomVisionObjects** clase) se ha configurado para trabajar con [  *Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). Si tiene una versión diferente, es posible que deba actualizar el *objetos* estructura.

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
    > Asegúrese de agregar su **clave de servicio** (entrenamiento clave-valor) y **Id. de proyecto** valor que anotó anterior; estos son los valores [recopilados desde el portal anteriormente en el curso () Capítulo 2, el paso 10 y versiones posteriores)](#chapter-2---training-your-custom-vision-oroject).

5.  Agregue el siguiente **Start()** y **Awake()** métodos. Esos métodos se llaman en la inicialización y contienen la llamada para configurar la interfaz de usuario:

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

6.  Eliminar el **Update()** método. Esta clase no necesitará.

7.  Agregar el **RequestTagSelection()** método. Este método es la primera que se llama cuando se captura una imagen y se almacena en el dispositivo y ahora está listo para enviarse a la *Custom Vision Service*, entrenarlo. Este método muestra, en el entrenamiento de la interfaz de usuario, un conjunto de palabras clave que el usuario puede utilizar para etiquetar la imagen que se ha capturado. También le avisa la *VoiceRecognizer* clase para empezar a escuchar al usuario para la entrada de voz.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Agregar el **VerifyTag()** método. Este método recibe la entrada de voz reconocida por el **VoiceRecognizer** clase y comprobar su validez y, a continuación, iniciar el proceso de entrenamiento.

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

9.  Agregar el **SubmitImageForTraining()** método. Este método comenzará el proceso de entrenamiento de Custom Vision Service. El primer paso es recuperar el **Id. de etiqueta** desde el servicio que está asociado con la entrada de voz validada del usuario. El **Id. de etiqueta** se cargará a continuación, junto con la imagen.

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

10. Agregar el **TrainCustomVisionProject()** método. Una vez que se han enviado y etiquetar la imagen, este método se llamará. Creará una nueva iteración que se van a entrenar con todas las imágenes anteriores y enviadas al servicio además de la imagen recién cargado. Una vez que se ha completado el entrenamiento, este método llamará a un método para establecer el recién creado **iteración** como **predeterminado**, de modo que el punto de conexión que usa para el análisis es la última iteración entrenada.

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

11. Agregar el **SetDefaultIteration()** método. Este método establece la iteración creada anteriormente y entrenada como *predeterminado*. Una vez completado, este método tendrá que eliminar la iteración anterior existente en el servicio. En el momento de redactar este curso, hay un límite de un máximo iteraciones de diez (10) permiten al mismo tiempo en el servicio.

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

12. Agregar el **DeletePreviousIteration()** método. Este método se busque y elimine la iteración no predeterminado anterior:

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

13. El último método para agregar de esta clase es el **GetImageAsByteArray()** método que se utiliza en llamadas a la web para convertir la imagen capturada en una matriz de bytes.

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

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capítulo 10: crear la clase SceneOrganiser

Esta clase hará lo siguiente:

-   Crear un **Cursor** objeto va a asociar a la cámara principal.

-   Crear un **etiqueta** objeto que va a aparecer cuando el servicio reconoce los objetos reales.

-   Configuración de la cámara principal adjuntando los componentes adecuados a él.

-   Cuando se encuentra en **modo de análisis**, generar las etiquetas en tiempo de ejecución, en el espacio adecuado mundo relativo a la posición de la cámara principal y mostrar los datos recibidos de Custom Vision Service.

-   Cuando se encuentra en **modo de formación**, generar la interfaz de usuario que se mostrará las distintas fases del proceso de entrenamiento.

Para crear esta clase:

1.  Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**. Nombre de la secuencia de comandos *SceneOrganiser*.

2.  Haga doble clic en el nuevo *SceneOrganiser* script para abrirlo con **Visual Studio**.

3.  Un espacio de nombres, solo tendrá que quitar las demás desde arriba la *SceneOrganiser* clase:

    ```csharp
    using UnityEngine;
    ```

4.  A continuación, agregue las siguientes variables dentro de la *SceneOrganiser* clase encima el **Start()** método:

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

5.  Eliminar el **Start()** y **Update()** métodos.

6.  Justo debajo de las variables, agregue el **Awake()** método, que inicializará la clase y configuración de la escena.

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

7.  Ahora, agregue el **CreateCameraCursor()** método que crea y coloca el cursor de la cámara principal, y el **CreateLabel()** método, que crea el **Analysis etiqueta** objeto .

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

8. Agregar el **SetCameraStatus()** método que controlará los mensajes destinados a la malla de texto que proporciona el estado de la cámara.

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

9. Agregar el **PlaceAnalysisLabel()** y **SetTagsToLastLabel()** métodos, generar y mostrar los datos de Custom Vision Service en la escena.

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

10. Por último, agregue el **CreateTrainingUI()** método, que generará la interfaz de usuario mostrar el varias fases del proceso de entrenamiento cuando la aplicación está en modo de formación. También se le sacado partido a este método para crear el objeto de estado de la cámara.

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
> Antes de continuar, abra el **CustomVisionAnalyser** (clase) y dentro del **AnalyseLastImageCaptured()** método, *quite* las líneas siguientes:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capítulo 11: crear la clase ImageCapture

La siguiente clase que se va a crear es la *ImageCapture* clase.

Esta clase es responsable de:

-   Capturar una imagen con la cámara de HoloLens y almacenarla en la *aplicación* carpeta.

-   Controlar los gestos de derivación del usuario.

-   Mantener la *Enum* valor que determina si la aplicación se ejecutará *Analysis* modo o *entrenamiento* modo.

Para crear esta clase:

1.  Vaya a la **Scripts** carpeta que creó anteriormente.

2.  Haga clic en la carpeta, a continuación, haga clic en **crear > C\# Script**. Nombre de la secuencia de comandos *ImageCapture*.

3.  Haga doble clic en el nuevo **ImageCapture** script para abrirlo con **Visual Studio**.

4.  Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *ImageCapture* clase encima el **Start()** método:

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

6.  El código para **Awake()** y **Start()** métodos ahora debe agregar:

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

7.  Implemente un controlador que se llamará cuando se produce un gesto de pulsar.

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
    > En *Analysis* modo, el **TapHandler** método actúa como un conmutador para iniciar o detener el bucle de captura de fotografías.
    >
    > En *entrenamiento* modo, capturará una imagen de la cámara.
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

9.  Agregue los controladores que se llamará cuando se ha capturado la foto y para cuando esté listo para ser analizados. El resultado se pasa a la *CustomVisionAnalyser* o *CustomVisionTrainer* dependiendo del modo que el código está establecido en.

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

11. Ahora que se han completado todas las secuencias de comandos, vuelva atrás en el Editor de Unity, a continuación, haga clic y arrastre el **SceneOrganiser** clase desde el **Scripts** carpeta a la **cámara principal** objeto en el *jerarquía Panel*.

## <a name="chapter-12---before-building"></a>Capítulo 12 - antes de compilar

Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.

Antes de hacerlo, asegúrese de que:

- Todas las configuraciones que se mencionan en la [capítulo 2](#chapter-2---training-your-custom-vision-project) están establecidas correctamente.

- Todos los campos de la **cámara principal**, Panel Inspector, se asignan correctamente.

- La secuencia de comandos **SceneOrganiser** está asociado a la **cámara principal** objeto.

- Asegúrese de insertar el **clave predicción** en el **predictionKey** variable.

- Ha insertado el **punto de conexión de predicción** en el **predictionEndpoint** variable.

- Ha insertado su **entrenamiento clave** en el **trainingKey** variable de la *CustomVisionTrainer* clase.

- Ha insertado el **Id. de proyecto** en el **projectId** variable de la *CustomVisionTrainer* clase.

## <a name="chapter-13---build-and-sideload-your-application"></a>Capítulo 13 - generar y transferir localmente la aplicación

Para comenzar la *compilar* proceso:

1.  Vaya a **archivo > configuración de compilación**.

2.  Graduación **Unity C\# proyectos**.

3.  Haz clic en **Compilación**. Unity se iniciará un **Explorador de archivos** ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta y asígnele el nombre **aplicación**. A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**.

4.  Unity empezará a compilar el proyecto para el **aplicación** carpeta.

5.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador**. Para ello:

    1.  Mientras que el exceso de su HoloLens, abra el **configuración**.

    2.  Vaya a **red e Internet** > **Wi-Fi** > **opciones avanzadas**

    3.  Tenga en cuenta la **IPv4** dirección.

    4.  A continuación, vaya a **configuración**y, a continuación, en **actualización y seguridad** > **para desarrolladores**

    5.  Establecer **modo de programador en**.

2.  Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.

3.  En el *configuración de la solución* seleccione **depurar**.

4.  En el *plataforma de solución*, seleccione **x86, máquina remota**. Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (el HoloLens, en este caso, lo cual observó).

    ![](images/AzureLabs-Lab302b-34.png)

5. Vaya a **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación a su HoloLens.

6. La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.

> [!NOTE]
> Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**. Implementar, a continuación, en el equipo local machine, utilizando el **compilar** elemento de menú, seleccionar *implementar solución*. 

## <a name="to-use-the-application"></a>Para usar la aplicación:

Para cambiar la funcionalidad de la aplicación entre *entrenamiento* modo y *predicción* modo deberá actualizar el **AppMode** variable, que se encuentra en la **Awake()** método ubicados dentro de la *ImageCapture* clase.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
o bien
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

En *entrenamiento* modo:

- Examine **Mouse** o **teclado** y usar el **gesto**.

- A continuación, el texto aparecerá que le pide que proporcione una etiqueta.

- Indicar **Mouse** o **teclado**.


En *predicción* modo:

- Consultar un objeto y utilizar el **gesto**.

- Aparecerá texto que proporciona el objeto detectado, con la probabilidad más alta (Esto se normaliza).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capítulo 14: evaluar y mejorar su modelo de visión personalizada

Para hacer que el servicio más precisos, deberá continuar entrenar el modelo utilizado para la predicción. Esto se logra a través del uso de la nueva aplicación, con ambos el *entrenamiento* y *predicción* modos, con el último tener que visitar el portal, que es lo que se trata en este capítulo. Esté preparado para volver a visitar su portal muchas veces, para mejorar continuamente el modelo.

1. Vaya a su Portal de Azure Custom Vision nuevo y una vez que esté en el proyecto, seleccione el *predicciones* ficha (desde la parte superior central de la página):

    ![](images/AzureLabs-Lab302b-35.png)

2. Verá todas las imágenes que se han enviado al servicio mientras se estaba ejecutando la aplicación. Si mantiene el puntero sobre las imágenes, le proporcionará las predicciones realizadas para la imagen:

    ![](images/AzureLabs-Lab302b-36.png)

3. Seleccione una de las imágenes para abrirlo. Una vez abierto, verá las predicciones realizadas para la imagen a la derecha. Si las predicciones fueran correctas, y que se va a agregar esta imagen al modelo de aprendizaje del servicio, haga clic en el *Mis etiquetas* cuadro de entrada y seleccione la etiqueta a la que desea asociar. Cuando haya terminado, haga clic en el *guardar y cerrar* situado en la esquina inferior derecha y continúe con la siguiente imagen.

    ![](images/AzureLabs-Lab302b-37.png)

4. Una vez que esté a la cuadrícula de imágenes, observará que las imágenes que ha agregado etiquetas a (y guardado), se quitará. Si encuentra cualquier imagen que piensa que es necesario el elemento etiquetado dentro de ellos, puede eliminarlos, haciendo clic en el "Tick" en esa imagen (puede hacerlo para varias imágenes) y, a continuación, haga clic en *eliminar* en la esquina superior derecha de la página de cuadrícula. En la ventana emergente a continuación, puede hacer clic en cualquiera *Sí, eliminar* o *No*para confirmar la eliminación o cancelarlo, respectivamente. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Cuando esté listo para continuar, haga clic en el verde *Train* botón en la esquina superior derecha. Se va a entrenar un modelo de servicio con todas las imágenes que ya haya proporcionado (que le resultará más precisas). Una vez completado el entrenamiento, asegúrese de hacer clic en el *Predeterminar* botón una vez más, para que su *dirección URL de la predicción* sigue usando la iteración más reciente del servicio.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>La aplicación finalizada de Custom Vision API

Enhorabuena, creó una aplicación de realidad mixta que aprovecha la API de Azure Custom Vision para reconocer objetos del mundo real, entrenar el modelo de servicio y mostrar la confianza de lo que hemos visto.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

Entrenar su **Custom Vision Service** a reconocer más objetos.

### <a name="exercise-2"></a>Ejercicio 2

Como una forma de ampliar lo que ha aprendido, completar los ejercicios siguientes:

Reproducir un sonido cuando se reconoce un objeto.

### <a name="exercise-3"></a>Ejercicio 3

Usar la API para volver a entrenar el servicio con las mismas imágenes que se está analizando la aplicación, por lo tanto, para que el servicio más precisos (realizar tareas de predicción y aprendizaje de forma simultánea).
