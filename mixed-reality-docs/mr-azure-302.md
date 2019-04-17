---
title: El Sr. y Azure 302 - Computer vision
description: Realice este curso para aprender a reconocer contenido visual dentro de una imagen proporcionada, con Azure Computer Vision en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, visión de equipo, hololens, envolventes, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597888"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>El Sr. y 302 de Azure: Visión de equipo

En este curso, obtendrá información sobre cómo reconocer contenido visual dentro de una imagen proporcionada, con funcionalidades de Azure Computer Vision en una aplicación de realidad mixta.

Resultados de reconocimiento se mostrará como etiquetas descriptivas. Puede usar este servicio sin necesidad de para entrenar un modelo de aprendizaje automático. Si su implementación requiere entrenar un modelo de aprendizaje automático, vea [MR y Azure 302b](mr-azure-302b.md).

![Resultado de laboratorio](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision es un conjunto de API diseñadas para ofrecer a los desarrolladores con procesamiento de imágenes y análisis (con la información de devolución), mediante algoritmos avanzados, todo ello desde la nube. Los desarrolladores cargar una imagen o una dirección URL de imagen y los algoritmos de Microsoft Computer Vision API analizan el contenido visual, en función de entradas que elige el usuario, que, a continuación, puede devolver información, incluidos, que identifica el tipo y la calidad de una imagen, detectar caras humanas () devolver sus coordenadas) y etiquetado, o categorizar las imágenes. Para obtener más información, visite la [página Azure Computer Vision API](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Una vez completado este curso, tendrá una realidad mixta HoloLens aplicación, que podrá hacer lo siguiente:

1.  La cámara de la HoloLens con el gesto de pulsar, capturará una imagen.
2.  La imagen se enviará con el servicio de API de visión de equipos de Azure. 
3.  Los objetos reconocidos se mostrarán en un grupo de interfaz de usuario simple que está situado en la escena de Unity.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y 302 de Azure: Visión de equipo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality. Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC. Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK más reciente de Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Una cámara conectada a su equipo (para el desarrollo de amplias auriculares)
- Acceso a Internet para el programa de instalación de Azure y la recuperación de Computer Vision API

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
2.  Configurar y probar su HoloLens. Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1: el Portal de Azure

Para usar el *Computer Vision API* service en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.

1.  En primer lugar, inicie sesión en el [Portal de Azure](https://portal.azure.com). 

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Computer Vision API*y haga clic en **ENTRAR**.

    ![Crear un nuevo recurso en Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.
 
3.  La nueva página proporcionará una descripción de la *Computer Vision API* service. En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.

    ![Acerca del servicio de api de visión de equipo](images/AzureLabs-Lab2-01.png)
 
4.  Una vez que ha hecho clic **crear**:

    1. Insertar el elemento **nombre** para esta instancia de servicio.
    2. Seleccione un **suscripción**.
    3. Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *Computer Vision API* servicio, un nivel gratuito (denominado F0) debe estar disponible para usted.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes). 

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinar la ubicación del grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    7. Haga clic en crear.

        ![Información sobre la creación de servicio](images/AzureLabs-Lab2-02.png)

5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.
6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Vea la notificación de nuevo para su nuevo servicio](images/AzureLabs-Lab2-03.png) 
 
7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Seleccione el botón Ir a recursos.](images/AzureLabs-Lab2-04.png)
 
8. Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia del servicio Computer Vision API. 

    ![El nuevo servicio Computer Vision API](images/AzureLabs-Lab2-05.png)
 
9.  En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través del uso clave del servicio en la de suscripción.
10. Desde el *inicio rápido* página, de su *Computer Vision API* de servicio, navegue hasta el primer paso, *obtener las claves*y haga clic en **claves** () También puede lograr esto, haga clic en el hipervínculo azul claves, ubicado en el menú de navegación de servicios, indicado por el icono de llave). Esto revelará su servicio *claves*.
11. Realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto. 

12. Vuelva a la *inicio rápido* página y, a partir de ahí, capturar el punto de conexión. Tenga en cuenta suya puede ser diferente, dependiendo de su región (lo que si es así, deberá realizar un cambio en el código más adelante). Realice una copia de este punto de conexión para su uso posterior:

    ![El nuevo servicio Computer Vision API](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Puede comprobar cuáles son los diferentes extremos [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **New**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab2-06.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Insertar **MR_ComputerVision**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab2-07.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab2-08.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab2-10.png)

5.  Mientras sigue en **archivo > configuración de compilación** y asegúrese de que:

    1. **Dispositivo de destino** está establecido en **HoloLens**

        > Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.

    2. **Tipo de compilación** está establecido en **D3D**
    3. **SDK** está establecido en **instalada más reciente**
    4. **Versión de Visual Studio** está establecido en **instalada más reciente**
    5. **Compilar y ejecutar** está establecido en **máquina Local**
    6. Guarde la escena y agregarlo a la compilación.

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.
        
            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab2-11.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab2-12.png)

        3. Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_ComputerVisionScene**, a continuación, haga clic en **guardar** .

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab2-13.png)

            > Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity. Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.

    7. El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra. 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab2-14.png)

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1. En el **otra configuración** pestaña:

        1. **Versión en tiempo de ejecución de secuencias de comandos** debe ser **estable** (.NET 3.5 equivalente).
        2. **Scripting de back-end** debe ser **.NET**
        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab2-15.png)
      
    2. Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        1. **InternetClient**
        2. **Webcam**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab2-16.png)

    3. Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab2-17.png)

8.  En *configuración de compilación* _Unity C#_  proyectos ya no está atenuada; Marque la casilla situada junto a esto. 
9.  Cierre la ventana de configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3: configuración de cámara principal

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importarlo en el proyecto como un [paquete personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5--create-the-resultslabel-class).

1.  En el *jerarquía Panel*, seleccione el **cámara principal**. 
2.  Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *Panel Inspector*.

    1. El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía!)
    2. La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)
    3. Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**
    4. Establecer **borrar las marcas** a **Color sólido** (omitir esto para envolventes auriculares).
    5. Establecer el **en segundo plano** Color del componente de cámara para **negro, alfa de 0 (código hexadecimal: #00000000)** (omitir esto para envolventes auriculares).

        ![Actualizar componentes de la cámara.](images/AzureLabs-Lab2-18.png)
 
3.  A continuación, tendrá que crear un objeto simple "Cursor" conectado a la **cámara principal**, que ayudan a colocar el análisis de imagen generará cuando se ejecuta la aplicación. Este Cursor determinará el punto central del foco de la cámara.

Para crear el Cursor:

1.  En el *jerarquía Panel*, haga doble clic en el **cámara principal**. En **objeto 3D**, haga clic en **esfera**.

    ![Seleccione el objeto del Cursor.](images/AzureLabs-Lab2-19.png)
 
2.  Cambiar el nombre de la **esfera** a **Cursor** (haga doble clic en el objeto del Cursor o presione el botón de teclado 'F2' con el objeto seleccionado) y asegúrese de que se encuentra como elemento secundario de la **cámara principal**.

3.  En el *jerarquía Panel*, haga clic en el **Cursor**. Con el Cursor seleccionado, ajustar las siguientes variables en el *Panel Inspector*:

    1. Establecer el *transformar posición* a **0, 0, 5**
    2. Establecer el *escala* a **0,02, 0,02, 0,02**

        ![Actualizar la posición de la transformación y la escala.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capítulo 4: instalación del sistema de etiqueta

Una vez que ha capturado una imagen con la cámara de HoloLens, esa imagen se enviará a su *Azure Computer Vision API* instancia de servicio para el análisis. 

Los resultados del análisis será una lista de objetos reconocidos denominados **etiquetas**. 

Debe utilizar las etiquetas (como texto 3D en el espacio global) para mostrar estas etiquetas en la ubicación que se tomó la fotografía.

Los pasos siguientes muestran cómo configurar el **etiqueta** objeto.

1.  Haga doble clic en cualquier lugar en la jerarquía de Panel (la ubicación no importa en este momento), en **objeto 3D**, agregue un **texto 3D**. Asígnele el nombre **LabelText**.

    ![Crear objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  En el *jerarquía Panel*, haga clic en el **LabelText**. Con el **LabelText** seleccionado, ajustar las siguientes variables en el *Panel Inspector*:

    1. Establecer el **posición** a **0,0,0**
    2. Establecer el **escala** a **0,01, 0,01, 0,01**
    3. En el componente **texto de la malla**:
    4. Reemplace todo el texto dentro de **texto**, con "..."        
    5. Establecer el **delimitador** a **intermedio central**
    6. Establecer el **alineación** a **Center**
    7. Establecer el **tamaño de tabulación** a **4**
    8. Establecer el **tamaño de fuente** a **50**
    9. Establecer el **Color** a **#FFFFFFFF**

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  Arrastre el **LabelText** desde el *Panel de la jerarquía*, en el *carpeta de activos*, en el *Panel del proyecto*. Esto hará que el **LabelText** un prefabricado, por lo que TI se puede crear instancias en el código.

    ![Creación de un prefabricado del objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  Debe eliminar el **LabelText** desde el *jerarquía Panel*, de modo que no se mostrará en la escena de apertura. Ya que es ahora un prefabricado, que llamará en para las instancias individuales de la carpeta de activos, no hay ninguna necesidad para mantenerlo dentro de la escena. 
5.  La estructura del objeto final en el *jerarquía Panel* debe ser como se muestra en la imagen siguiente:

    ![Estructura final del panel de la jerarquía.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capítulo 5: crear la clase de etiqueta resultados

Es el primer script, deberá crear el *etiqueta resultados* (clase), que es responsable de lo siguiente: 

- Creación de las etiquetas en el espacio adecuado del mundo, con respecto a la posición de la cámara.
- Mostrar las etiquetas de la ardua de imagen.

Para crear esta clase: 

1.  Haga clic en el *Panel del proyecto*, a continuación, **crear > carpeta**. Nombre de la carpeta **Scripts**. 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab2-24.png)

2.  Con el **Scripts** carpeta crear, haga doble clic en él para abrirlo. A continuación, dentro de esa carpeta, contextual y seleccione **crear >** , a continuación,  **C# Script**. Nombre de la secuencia de comandos *etiqueta resultados*. 

3.  Haga doble clic en el nuevo *etiqueta resultados* script para abrirlo con **Visual Studio**.

4.  Dentro de la clase, inserte el código siguiente en el *etiqueta resultados* clase:

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
7.  En el *Editor de Unity*, haga clic y arrastre el *etiqueta resultados* clase desde el **Scripts** carpeta a la **cámara principal** objeto en el  *Panel de la jerarquía*.
8.  Haga clic en el **cámara principal** y examine el *Panel Inspector*.

Observará que, desde la secuencia de comandos que acaba de arrastrar a la cámara, hay dos campos: **Cursor** y **etiquetar prefabricado**.

9.  Arrastre el objeto llamado **Cursor** desde el *jerarquía Panel* a la ranura denominada **Cursor**, tal y como se muestra en la imagen siguiente.
10. Arrastre el objeto llamado **LabelText** desde el *carpeta Assets* en el *Panel proyecto* a la ranura denominada **etiqueta prefabricado**, tal y como se muestra en el imagen siguiente. 

    ![Establecer los destinos de referencia dentro de Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capítulo 6: crear la clase ImageCapture

La siguiente clase que se va a crear es la *ImageCapture* clase. Esta clase es responsable de:

-   Capturar una imagen con la cámara de HoloLens y almacenarla en la carpeta de la aplicación.
-   Captura de derivación de gestos del usuario.

Para crear esta clase: 

1.  Vaya a la **Scripts** carpeta que creó anteriormente. 
2.  Haga clic en la carpeta, **crear > C# Script**. Llame al script *ImageCapture*. 
3.  Haga doble clic en el nuevo *ImageCapture* script para abrirlo con **Visual Studio**.
4.  Agregue los siguientes espacios de nombres en la parte superior del archivo:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *ImageCapture* clase encima el *Start()* método:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
El **tapsCount** variable almacenará el número de movimientos de tap capturados desde el usuario. Este número se usa en la denominación de las imágenes de captura.

6.  El código para *Awake()* y *Start()* métodos ahora debe agregarse. Estos se llamará cuando se inicializa la clase:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente un controlador que se llamará cuando se produce un gesto de pulsar. 

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
 
El *TapHandler()* método incrementa el número de pesos capturados desde el usuario y la posición actual del Cursor se utiliza para determinar dónde colocar una etiqueta nueva.

A continuación, llama a este método la *ExecuteImageCaptureAndAnalysis()* método para comenzar la funcionalidad básica de esta aplicación.

8.  Una vez capturada y almacena una imagen, se llamará los siguientes controladores. Si el proceso se realiza correctamente, el resultado se pasa a la *VisionManager* (que aún están crear) para el análisis.

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
> En este momento aparece un error que aparecen en la *Panel de consola del Editor de Unity*. Esto es porque el código hace referencia a la *VisionManager* clase que se creará en el próximo capítulo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capítulo 7: llamada a Azure y análisis de imágenes

Es el último script, deberá crear el *VisionManager* clase. 

Esta clase es responsable de:

-   Cargando la última imagen de captura como una matriz de bytes.
-   Envío de la matriz de bytes para su *Azure Computer Vision API* instancia de servicio para el análisis.
-   Recibir la respuesta como una cadena JSON.
-   Al deserializar la respuesta y pasar las etiquetas resultantes a la *etiqueta resultados* clase.
 
Para crear esta clase:

1.  Haga doble clic en el **Scripts** carpeta para abrirla. 
2.  Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos *VisionManager*. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres para que sea igual a lo siguiente en la parte superior de la *VisionManager* clase:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  En la parte superior de la secuencia de comandos, *dentro de* el *VisionManager* clase (anteriormente el *Start()* método), ahora debe crear dos *clases* que representa la respuesta JSON deserializada de Azure:

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
    > El *TagData* y *AnalysedObject* clases deben tener la *[System.Serializable]* atributo agregado antes de la declaración se pueda deserializar con la de Unity bibliotecas.

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
    > Asegúrese de insertar el **Auth Key** en el **authorizationKey** variable. Habrá anotó la **Auth Key** al principio de este curso, [capítulo 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > El **visionAnalysisEndpoint** variable puede diferir de lo especificado en este ejemplo. El **oeste-EE** estrictamente hace referencia a instancias de servicio creadas para la región Oeste de Estados Unidos. Actualícelo con su [dirección URL del extremo](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); aquí son algunos ejemplos de lo que podrían ser similar a:
    > - Europa occidental: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Sudeste de Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Este de Australia: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Código para Awake ahora debe agregarse. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  A continuación, agregue la corrutina (con el método estático secuencia debajo de él), que se va a obtener los resultados del análisis de la imagen capturada por la *ImageCapture* clase. 

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
10. En el Editor de Unity, haga clic en Atrás y arrastre el *VisionManager* y *ImageCapture* clases a partir de la **Scripts** carpeta a la **cámara principal**objeto en el *jerarquía Panel*. 

## <a name="chapter-8--before-building"></a>Capítulo 8 antes de compilar

Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.
Antes de hacerlo, asegúrese de que:

-   Todas las configuraciones que se mencionan en [capítulo 2](#chapter-2--set-up-the-unity-project) están establecidas correctamente. 
-   Todos los scripts están conectados a la **cámara principal** objeto. 
-   Todos los campos de la *Panel de Inspector de cámara principal* se asignan correctamente.
-   Asegúrese de insertar el **Auth Key** en el **authorizationKey** variable.
-   Asegúrese de que también ha comprobado el punto de conexión su *VisionManager* script y que se alinea con *su* región (este documento usa *west-nos* de forma predeterminada).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capítulo 9: compilar la solución de UWP y transferir localmente la aplicación
Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.

1.  Vaya a *configuración de compilación* - **archivo > configuración de compilación...**
2.  Desde el *configuración de compilación* ventana, haga clic en **compilar**.

    ![Creación de la aplicación de Unity](images/AzureLabs-Lab2-26.png)

3.  Si aún no marque **Unity C# proyectos**.
4.  Haz clic en **Compilación**. Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta y asígnele el nombre *aplicación*. A continuación, con el *aplicación* carpeta seleccionada, presione **seleccionar la carpeta**. 
5.  Unity empezará a compilar el proyecto para el *aplicación* carpeta. 
6.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un *Explorador de archivos* ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

## <a name="chapter-10--deploy-to-hololens"></a>Capítulo 10: implementar en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador**. Para ello:

    1. Mientras que el exceso de su HoloLens, abra el **configuración**.
    2. Vaya a **red e Internet > Wi-Fi > Opciones avanzadas**
    3. Tenga en cuenta la **IPv4** dirección.
    4. A continuación, vaya a **configuración**y, a continuación, para **actualización y seguridad > para desarrolladores** 
    5. Activar el modo de programador.

2.  Vaya a la nueva compilación de Unity (la *aplicación* carpeta) y abra el archivo de solución con *Visual Studio*.
3.  En, seleccione la configuración de la solución **depurar**.
4.  En la plataforma de soluciones, seleccione **x86**, **máquina remota**. 

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Vaya a la **menú compilar** y haga clic en **implementar solución**, para transferir localmente la aplicación a su HoloLens.
6.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.

> [!NOTE]
> Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**. Implementar, a continuación, en el equipo local machine, utilizando el **menú compilar**, seleccionar *implementar solución*. 

## <a name="your-finished-computer-vision-api-application"></a>La aplicación finalizada de Computer Vision API

Enhorabuena, creó una aplicación de realidad mixta que aprovecha Azure Computer Vision API para reconocer objetos del mundo real y mostrar la confianza de lo que se ha visto.

![Resultado de laboratorio](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

Tal como ha usado el *etiquetas* parámetro (tal como se evidencia dentro de la *extremo* utilizado dentro de la *VisionManager*), amplíe la aplicación para detectar la información de otro; Eche un vistazo a ¿Qué otros parámetros que tienen acceso a [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Ejercicio 2

Mostrar los datos devueltos de Azure, de forma más conversacional y legible, quizás ocultando los números. Como si es posible que se habla un bot al usuario.
