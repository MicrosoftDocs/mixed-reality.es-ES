---
title: MR y Azure 302-Computer Vision
description: Complete este curso para aprender a reconocer contenido visual dentro de una imagen proporcionada, con Azure Computer Vision en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, Computer Vision, hololens, envolventes, VR
ms.openlocfilehash: d6f792a67adfd1038ca4cdbc44b2ef1bf12a1173
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437946"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR y Azure 302: Computer Vision

En este curso, aprenderá a reconocer el contenido visual dentro de una imagen proporcionada, con las funcionalidades de Azure Computer Vision en una aplicación de realidad mixta.

Los resultados del reconocimiento se mostrarán como etiquetas descriptivas. Puede usar este servicio sin necesidad de entrenar un modelo de aprendizaje automático. Si su implementación requiere entrenar un modelo de aprendizaje automático, consulte [Mr y Azure 302B](mr-azure-302b.md).

![resultado de laboratorio](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision es un conjunto de API diseñadas para ofrecer a los desarrolladores el procesamiento y el análisis de imágenes (con información de retorno), mediante algoritmos avanzados, todo desde la nube. Los desarrolladores cargan una imagen o una dirección URL de imagen, y los algoritmos de Microsoft Computer Vision API analizan el contenido visual, en función de las entradas elegidas para el usuario, que pueden devolver información, incluido, identificar el tipo y la calidad de una imagen, detectar caras humanas ( devolver sus coordenadas) y etiquetar o clasificar las imágenes. Para obtener más información, visite la [Página de Computer Vision API de Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Una vez completado este curso, tendrá una aplicación de realidad HoloLens mixta, que podrá hacer lo siguiente:

1.  Con el gesto de TAP, la cámara de HoloLens capturará una imagen.
2.  La imagen se enviará al servicio Azure Computer Vision API. 
3.  Los objetos reconocidos se enumerarán en un grupo de interfaz de usuario simple situado en la escena de Unity.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 302: Computer Vision</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR). Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo). Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Una cámara conectada al equipo (para el desarrollo de auriculares envolvente)
- Acceso a Internet para la configuración y recuperación de Computer Vision API de Azure

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
2.  Configure y pruebe su HoloLens. Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1: Azure portal

Para usar el servicio de *Computer Vision API* en Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.

1.  En primer lugar, inicie sesión en [Azure portal](https://portal.azure.com). 

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *Computer Vision API*y haga clic en **entrar**.

    ![Creación de un nuevo recurso en Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.
 
3.  La nueva página proporcionará una descripción del servicio *Computer Vision API* . En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.

    ![Acerca del servicio Computer Vision API](images/AzureLabs-Lab2-01.png)
 
4.  Una vez que haya hecho clic en **crear**:

    1. Inserte el **nombre** que desee para esta instancia de servicio.
    2. Seleccione una **suscripción**.
    3. Seleccione el **plan de tarifa** adecuado para usted; si es la primera vez que crea un servicio de *Computer Vision API* , debe tener a su disposición un nivel gratis (denominado F0).
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común). 

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determine la ubicación del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    7. Haga clic en crear.

        ![Información de creación del servicio](images/AzureLabs-Lab2-02.png)

5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.
6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![Vea la nueva notificación del nuevo servicio](images/AzureLabs-Lab2-03.png) 
 
7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Seleccione el botón ir a recurso.](images/AzureLabs-Lab2-04.png)
 
8. Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de servicio de Computer Vision API. 

    ![El nuevo servicio de Computer Vision API](images/AzureLabs-Lab2-05.png)
 
9.  En este tutorial, la aplicación necesitará realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio.
10. En la página *Inicio rápido* , del servicio de *Computer Vision API* , navegue hasta el primer paso, *grabe sus claves*y haga clic en **claves** (también puede conseguirlo haciendo clic en las teclas de hipervínculo azul, que se encuentran en el menú de navegación servicios. indicado por el icono de clave). Esto revelará las *claves*de servicio.
11. Realice una copia de una de las claves que se muestran, ya que la necesitará más adelante en el proyecto. 

12. Vuelva a la página *Inicio rápido* y, desde ahí, recupere el punto de conexión. Tenga en cuenta que el suyo puede ser diferente, en función de su región (que, si es así, deberá realizar un cambio en el código más adelante). Realice una copia de este punto de conexión para usarlo más adelante:

    ![El nuevo servicio de Computer Vision API](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Puede comprobar los distintos puntos de conexión [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2: configurar el proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **nuevo**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab2-06.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity. Inserte **MR_ComputerVision**. Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab2-07.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab2-08.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y seleccione **plataforma universal de Windows**y, después, haga clic en el botón **cambiar plataforma** para aplicar la selección.

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab2-10.png)

5.  Mientras sigue en el **archivo > la configuración de compilación** y asegúrese de que:

    1. El **dispositivo de destino** está establecido en **HoloLens**

        > Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.

    2. El **tipo de compilación** se establece en **D3D**
    3. **SDK** está establecido en la **versión más reciente instalada**
    4. La **versión de Visual Studio** está establecida en la **más reciente instalada**
    5. **Compilar y ejecutar** está establecido en **equipo local**
    6. Guarde la escena y agréguela a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.
        
            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab2-11.png)

        2. Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab2-12.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **MR_ComputerVisionScene**y haga clic en **Guardar**.

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab2-13.png)

            > Tenga en cuenta que debe guardar las escenas de Unity dentro de la carpeta *assets* , ya que deben estar asociadas con el proyecto Unity. La creación de la carpeta Scenes (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.

    7. El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* . 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab2-14.png)

7. En este panel, deben comprobarse algunas opciones de configuración:

    1. En la pestaña **otros valores** :

        1. La **versión de scripting en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).
        2. El **back-end de scripting** debe ser **.net**
        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab2-15.png)
      
    2. En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        1. **InternetClient**
        2. **Web**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab2-16.png)

    3. Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![Actualice la configuración de X R.](images/AzureLabs-Lab2-17.png)

8.  De nuevo en la *configuración de compilación* , los proyectos de _Unity C#_  ya no están atenuados; Marque la casilla situada junto a este. 
9.  Cierre la ventana Configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3: configuración de la cámara principal

> [!IMPORTANT]
> Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), impórtelo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo 5](#chapter-5--create-the-resultslabel-class).

1.  En el *Panel jerarquía*, seleccione la **cámara principal**. 
2.  Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel del inspector*.

    1. El **objeto de cámara** debe tener el nombre de la **cámara principal** (tenga en cuenta la ortografía).
    2. La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía).
    3. Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**
    4. Establezca **marcas de borrado** en **color sólido** (Ignore esto para los auriculares inmersivo).
    5. Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)** (no se tiene en cuenta para el casco inmersivo).

        ![Actualice los componentes de la cámara.](images/AzureLabs-Lab2-18.png)
 
3.  A continuación, tendrá que crear un objeto de "cursor" simple adjunto a la **cámara principal**, lo que le ayudará a colocar la salida del análisis de la imagen cuando la aplicación se esté ejecutando. Este cursor determinará el punto central del foco de la cámara.

Para crear el cursor:

1.  En el *Panel jerarquía*, haga clic con el botón secundario en la **cámara principal**. En **objeto 3D**, haga clic en **Sphere**.

    ![Seleccione el objeto Cursor.](images/AzureLabs-Lab2-19.png)
 
2.  Cambie el nombre de la **esfera** a **cursor** (haga doble clic en el objeto cursor o presione el botón de teclado ' F2 ' con el objeto seleccionado) y asegúrese de que se encuentra como elemento secundario de la **cámara principal**.

3.  En el *Panel jerarquía*, haga clic con el botón izquierdo en el **cursor**. Con el cursor seleccionado, ajuste las siguientes variables en el *panel del inspector*:

    1. Establecer la *posición* de la transformación en **0,** 0,5
    2. Establezca la *escala* en **0,02, 0,02, 0,02**

        ![Actualice la posición y la escala de transformación.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capítulo 4: configurar el sistema de etiquetas

Una vez que haya capturado una imagen con la cámara de HoloLens, esa imagen se enviará a la instancia de servicio de *Azure Computer Vision API* para su análisis. 

Los resultados de ese análisis serán una lista de objetos reconocidos denominados **etiquetas**. 

Usará etiquetas (como texto en 3D en el espacio universal) para mostrar estas etiquetas en la ubicación en la que se tomó la foto.

En los pasos siguientes se muestra cómo configurar el objeto de **etiqueta** .

1.  Haga clic con el botón secundario en cualquier lugar del panel jerarquía (la ubicación no importa en este momento), en **objeto 3D**, agregue un **texto 3D**. Asígnele el nombre **LabelText**.

    ![Cree un objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  En el *Panel jerarquía*, haga clic con el botón izquierdo en el **LabelText**. Con el **LabelText** seleccionado, ajuste las siguientes variables en el *panel del inspector*:

    1. Establezca la **posición** en **0, 0,0**
    2. Establezca la **escala** en **0,01, 0,01, 0,01**
    3. En la **malla de texto**del componente:
    4. Reemplace todo el texto dentro del **texto**, con "..."        
    5. Establecer el **anclaje** en el **Centro central**
    6. Establecer la **alineación** en **Center**
    7. Establecer el **tamaño de tabulación** en **4**
    8. Establezca el **tamaño de fuente** en **50**
    9. Establezca el **color** en **#FFFFFFFF**

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  Arrastre **LabelText** desde el *Panel jerarquía*, a la *carpeta Asset*, dentro del *panel Proyecto*. Esto hará que el **LabelText** sea recurso prefabricado, de modo que se puedan crear instancias en el código.

    ![Cree un recurso prefabricado del objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  Debe eliminar el **LabelText** del panel de *jerarquías*, de modo que no se muestre en la escena de apertura. Como es ahora un recurso prefabricado, al que se llamará para las instancias individuales de la carpeta Assets, no hay necesidad de mantenerla dentro de la escena. 
5.  La estructura final del objeto en el *Panel jerarquía* debe ser como la que se muestra en la imagen siguiente:

    ![Estructura final del panel de jerarquía.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capítulo 5: crear la clase ResultsLabel

El primer script que necesita crear es la clase *ResultsLabel* , que es responsable de lo siguiente: 

- Crear las etiquetas en el espacio del mundo adecuado, con respecto a la posición de la cámara.
- Mostrar las etiquetas de la imagen ardua.

Para crear esta clase: 

1.  Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, **cree > carpeta**. Asigne a la carpeta el nombre **scripts**. 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab2-24.png)

2.  Con la carpeta **scripts** creada, haga doble clic en ella para abrirla. Después, dentro de esa carpeta, haga clic con el botón derecho y seleccione **crear >** después  **C# script**. Asigne al script el nombre *ResultsLabel*. 

3.  Haga doble clic en el nuevo script *ResultsLabel* para abrirlo con **Visual Studio**.

4.  Dentro de la clase, inserte el siguiente código en la clase *ResultsLabel* :

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.
7.  De nuevo en el *Editor de Unity*, haga clic y arrastre la clase *ResultsLabel* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*.
8.  Haga clic en la **cámara principal** y mire en el *panel del inspector*.

Observará que, desde el script que acaba de arrastrar a la cámara, hay dos campos: **cursor** y **etiqueta recurso prefabricado**.

9.  Arrastre el objeto denominado **cursor** desde el *Panel jerarquía* hasta la ranura denominada **cursor**, tal como se muestra en la imagen siguiente.
10. Arrastre el objeto llamado **LabelText** desde la *carpeta assets* del *panel Proyecto* hasta la ranura denominada **etiqueta recurso prefabricado**, tal como se muestra en la imagen siguiente. 

    ![Establezca los destinos de referencia en Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capítulo 6: crear la clase ImageCapture

La clase siguiente que va a crear es la clase *ImageCapture* . Esta clase es responsable de:

-   Captura de una imagen con la cámara de HoloLens y su almacenamiento en la carpeta de la aplicación.
-   Captura de gestos de TAP del usuario.

Para crear esta clase: 

1.  Vaya a la carpeta **scripts** que creó anteriormente. 
2.  Haga clic con el botón derecho dentro de la carpeta, **cree > C# script**. Llame al script *ImageCapture*. 
3.  Haga doble clic en el nuevo script *ImageCapture* para abrirlo con **Visual Studio**.
4.  Agregue los siguientes espacios de nombres al principio del archivo:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro de la clase *ImageCapture* , sobre el método *Start ()* :

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
La variable **tapsCount** almacenará el número de gestos de TAP capturados por el usuario. Este número se usa en el nombre de las imágenes capturadas.

6.  Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* . Se llamará cuando se inicialice la clase:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente un controlador que se llamará cuando se produzca un gesto de TAP. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
El método *TapHandler ()* incrementa el número de pulsaciones capturadas por el usuario y usa la posición del cursor actual para determinar dónde se debe colocar una nueva etiqueta.

A continuación, este método llama al método *ExecuteImageCaptureAndAnalysis ()* para comenzar la funcionalidad básica de esta aplicación.

8.  Una vez capturada y almacenada una imagen, se llamará a los siguientes controladores. Si el proceso se realiza correctamente, el resultado se pasa a *VisionManager* (que aún no se ha creado) para el análisis.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  A continuación, agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> En este punto, observará que aparece un error en el *Panel*de la consola del editor de Unity. Esto se debe a que el código hace referencia a la clase *VisionManager* que creará en el siguiente capítulo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capítulo 7: llamada a Azure y análisis de imágenes

El último script que debe crear es la clase *VisionManager* . 

Esta clase es responsable de:

-   Cargar la imagen más reciente capturada como una matriz de bytes.
-   Envío de la matriz de bytes a la instancia de servicio de *Azure Computer Vision API* para su análisis.
-   Recibir la respuesta como una cadena JSON.
-   Deserializar la respuesta y pasar las etiquetas resultantes a la clase *ResultsLabel* .
 
Para crear esta clase:

1.  Haga doble clic en la carpeta **scripts** para abrirla. 
2.  Haga clic con el botón derecho en la carpeta **scripts** y haga clic en **crear > C# script**. Asigne al script el nombre *VisionManager*. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres para que sean los mismos que los que se indican a continuación, en la parte superior de la clase *VisionManager* :

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  En la parte superior del script, *dentro* de la clase *VisionManager* (encima del método *Start ()* ), ahora debe crear dos *clases* que representen la respuesta JSON deserializada de Azure:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > Las clases *TagData* y *AnalysedObject* deben tener el atributo *[System. Serializable]* agregado antes de que se pueda deserializar con las bibliotecas de Unity.

6.  En la clase VisionManager, debe agregar las siguientes variables:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Asegúrese de insertar la **clave de autenticación** en la variable **authorizationKey** . Habrá anotado la **clave de autenticación** al principio de este curso, [capítulo 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > La variable **visionAnalysisEndpoint** podría diferir de la especificada en este ejemplo. **West-US** hace referencia estrictamente a las instancias de servicio creadas para la región oeste de EE. UU. Actualícelo con la [dirección URL del punto de conexión](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); Estos son algunos ejemplos de lo que podría ser similar a:
    > - Europa Occidental: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Sudeste Asiático: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Este de Australia: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Ahora es necesario agregar el código para activo. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  A continuación, agregue la corutina (con el método de secuencia estático debajo), que obtendrá los resultados del análisis de la imagen capturada por la clase *ImageCapture* . 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.
10. De nuevo en el editor de Unity, haga clic y arrastre las clases *VisionManager* y *ImageCapture* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*. 

## <a name="chapter-8--before-building"></a>Capítulo 8: antes de compilar

Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.
Antes de hacerlo, asegúrese de que:

-   Toda la configuración mencionada en el [capítulo 2](#chapter-2--set-up-the-unity-project) se establece correctamente. 
-   Todos los scripts se adjuntan al objeto de **cámara principal** . 
-   Todos los campos del *panel Inspector de cámara principal* están asignados correctamente.
-   Asegúrese de insertar la **clave de autenticación** en la variable **authorizationKey** .
-   Asegúrese de que también ha comprobado el punto de conexión en el script de *VisionManager* y que está alineado con *su* región (este documento usa *West-US* de forma predeterminada).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capítulo 9: compilar la solución UWP y transferir localmente la aplicación
Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.

1.  Vaya a *configuración de compilación* - **archivo > configuración de compilación...**
2.  En la ventana *configuración de compilación* , haga clic en **compilar**.

    ![Compilar la aplicación desde Unity](images/AzureLabs-Lab2-26.png)

3.  Si aún no lo está, marque los **proyectos de Unity C#** .
4.  Haz clic en **Compilación**. Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y asígnele el nombre *App*. Después, con la carpeta de la *aplicación* seleccionada, presione **Seleccionar carpeta**. 
5.  Unity comenzará a compilar el proyecto en la carpeta de la *aplicación* . 
6.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del *Explorador de archivos* en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-10--deploy-to-hololens"></a>Capítulo 10: implementación en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de HoloLens (para la implementación remota) y para asegurarse de que HoloLens está en **modo de desarrollador**. Para ello:

    1. Mientras se contenga HoloLens, abra la **configuración**.
    2. Vaya a **Network & Internet > Wi-Fi > opciones avanzadas** .
    3. Anote la dirección **IPv4** .
    4. A continuación, vuelva a **configuración**y, a continuación, **actualice & seguridad > para desarrolladores** 
    5. Establezca el modo de Desarrollador en.

2.  Vaya a la nueva compilación de Unity (la carpeta de la *aplicación* ) y abra el archivo de solución con *Visual Studio*.
3.  En la configuración de soluciones, seleccione **depurar**.
4.  En la plataforma de la solución, seleccione **x86**, **equipo remoto**. 

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Vaya al **menú compilar** y haga clic en **implementar solución**para transferir localmente la aplicación a HoloLens.
6.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.

> [!NOTE]
> Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local*y establezca la **configuración** en *depurar*, con *x86* como **plataforma**. A continuación, implemente en el equipo local, mediante el **menú compilar**, seleccionando *implementar solución*. 

## <a name="your-finished-computer-vision-api-application"></a>La aplicación Computer Vision API finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el Computer Vision API de Azure para reconocer objetos reales y mostrar la confianza de lo que se ha detectado.

![resultado de laboratorio](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

Del mismo modo que ha usado el parámetro *Tags* (como se evidencia en el *punto de conexión* usado dentro del *VisionManager*), extienda la aplicación para detectar otra información; Observe a qué otros parámetros tiene acceso [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Ejercicio 2

Muestre los datos de Azure devueltos, de forma más conversación y legibles, y quizás oculte los números. Como si un bot pudiera estar hablando al usuario.
