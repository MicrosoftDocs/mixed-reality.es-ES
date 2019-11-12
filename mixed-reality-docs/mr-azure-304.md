---
title: 'MR y Azure 304: reconocimiento facial'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, reconocimiento facial, hololens, envolventes, VR
ms.openlocfilehash: 23676684c2ec325f9d6f1924e7a0bad14d41f13e
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926790"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR y Azure 304: reconocimiento facial

![resultado de la finalización de este curso](images/AzureLabs-Lab4-00.png)

En este curso aprenderá a agregar funcionalidades de reconocimiento facial a una aplicación de realidad mixta, con Azure Cognitive Services, con el Face API de Microsoft.

*Azure Face API* es un servicio de Microsoft, que proporciona a los desarrolladores los algoritmos de caras más avanzados, todo en la nube. El *face API* tiene dos funciones principales: detección de caras con atributos y reconocimiento facial. Esto permite a los desarrolladores simplemente establecer un conjunto de grupos para caras y, a continuación, enviar imágenes de consulta al servicio más adelante para determinar a quién pertenece una cara. Para obtener más información, visite la [Página de reconocimiento facial de Azure](https://azure.microsoft.com/services/cognitive-services/face/).

Una vez completado este curso, tendrá una aplicación de realidad HoloLens mixta, que podrá hacer lo siguiente:

1. Use un **gesto de TAP** para iniciar la captura de una imagen mediante la cámara HoloLens incorporada. 
2. Envíe la imagen capturada al servicio *Azure Face API* .
3. Recibir los resultados del algoritmo de *face API* .
4. Use una interfaz de usuario simple para mostrar el nombre de las personas coincidentes.

Esto le enseñará a obtener los resultados del servicio de Face API en la aplicación de realidad mixta basada en Unity.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 304: reconocimiento facial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR). Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo). Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md)
- [El SDK de Windows 10 más reciente](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Una cámara conectada al equipo (para el desarrollo de auriculares envolvente)
- Acceso a Internet para la configuración y recuperación de Face API de Azure

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
2.  Configure y pruebe su HoloLens. Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: Azure portal

Para usar el servicio de *face API* en Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.

1.  En primer lugar, inicie sesión en [Azure portal](https://portal.azure.com). 

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *face API*, presione **entrar**.

    ![búsqueda de facial API](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.

3.  La nueva página proporcionará una descripción del servicio *face API* . En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.

    ![información de la API facial](images/AzureLabs-Lab4-02.png)

4.  Una vez que haya hecho clic en **crear**:

    1. Inserte el nombre que desee para esta instancia de servicio.

    2. Seleccione una suscripción.

    3. Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea un *servicio de Face API*, debe tener a su disposición un nivel gratis (denominado F0).

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común). 

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. La aplicación para UWP, **Person Maker**, que se usa más adelante, requiere el uso de ' oeste de EE. UU. ' en la ubicación.

    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7. Seleccione **crear *.**

        ![creación de un servicio facial API](images/AzureLabs-Lab4-03.png)

5.  Una vez que haya hecho clic en **crear *,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![notificación de creación de servicio](images/AzureLabs-Lab4-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![ir a la notificación de recursos](images/AzureLabs-Lab4-05.png)

8.  Cuando esté listo, haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.

    ![acceso a las claves de la API facial](images/AzureLabs-Lab4-06.png)

9.  En este tutorial, la aplicación tendrá que realizar llamadas al servicio, lo que se realiza mediante el uso de la suscripción de su servicio. En la página de *Inicio rápido* , del servicio *face API* , el primer punto es el número 1, para *tomar las claves.*

10. En la página de *servicio* , seleccione el hipervínculo de **teclas** azules (si se trata de la página inicio rápido) o el vínculo **claves** en el menú de navegación servicios (a la izquierda, indicado por el icono "clave"), para mostrar las claves.

    > [!NOTE] 
    > Tome nota de cualquiera de las claves y protéjalo, ya que la necesitará más adelante.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capítulo 2: uso de la aplicación de UWP ' Person Maker '

Asegúrese de descargar la aplicación de UWP precompilada denominada [persona Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Esta aplicación no es el producto final de este curso, solo una herramienta que le ayudará a crear sus entradas de Azure, en las que se basará el proyecto posterior.

**Person Maker** le permite crear entradas de Azure, que están asociadas a personas y grupos de personas. La aplicación colocará toda la información necesaria en un formato que posteriormente pueda usar el FaceAPI para reconocer las caras de las personas que ha agregado. 

> AÚN **Person Maker** usa algunas limitaciones básicas para asegurarse de que no supere el número de llamadas de servicio por minuto para el nivel de **suscripción gratuita**. El texto verde de la parte superior cambiará a rojo y se actualizará como ' activo ' cuando se esté produciendo la limitación; Si este es el caso, simplemente espere a que la aplicación (esperará hasta que pueda seguir accediendo al servicio de caras, actualizando como "en activo" cuando pueda volver a usarla).

Esta aplicación usa las bibliotecas *Microsoft. ProjectOxford. facial* , que le permitirán hacer uso completo de los Face API. Esta biblioteca está disponible de forma gratuita como paquete NuGet. Para obtener más información sobre esta y las API similares, asegúrese [de visitar el artículo de referencia de la API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Estos son solo los pasos necesarios, las instrucciones sobre cómo realizar estas acciones se encuentran en el documento. La aplicación **creador de personas** le permitirá:
>
> - Cree un *grupo de personas*, que es un grupo compuesto por varias personas a las que desea asociarla. Con su cuenta de Azure, puede hospedar varios grupos de personas.
>
> - Cree una *persona*, que sea miembro de un grupo de personas. Cada persona tiene varias imágenes de *caras* asociadas.
>
> -  Asigne *imágenes faciales* a una *persona*, para permitir que el servicio Azure Face API reconozca a una *persona* por la *esfera*correspondiente.
>
> -  *Entrenar* su *servicio Azure Face API*.

Tenga en cuenta que, para entrenar a esta aplicación para que reconozca a los usuarios, necesitará diez (10) fotos próximas de cada persona que le gustaría agregar a su grupo de personas. La aplicación CAM de Windows 10 puede ayudarle a tomarlos. Debe asegurarse de que cada foto esté clara (Evite Desenfocar, ocultar o estar demasiado lejos, del asunto), tener la foto en formato de archivo jpg o PNG, con un tamaño de archivo de imagen no mayor de **4 MB**y no inferior a **1 KB**.

> [!NOTE]
> Si sigue este tutorial, no use su propio aspecto para el entrenamiento, al igual que cuando se coloca HoloLens en, no se puede ver. Usar el aspecto de un colega o de un estudiante.

Encargado de la ejecución de la **persona**:

1.  Abra la carpeta **PersonMaker** y haga doble clic en la *solución PersonMaker* para abrirla con *Visual Studio*.

2.  Una vez abierta la *solución PersonMaker* , asegúrese de que:

    1. La *configuración* de la solución está establecida en **depurar**.

    2. La *plataforma* de la solución está establecida en **x86**

    3. La *plataforma de destino* es la **máquina local**.

    4.  También es posible que necesite *restaurar paquetes Nuget* (haga clic con el botón derecho en la *solución* y seleccione **restaurar paquetes Nuget**).

3.  Haga clic en *equipo local* y se iniciará la aplicación. Tenga en cuenta que, en pantallas más pequeñas, todo el contenido puede no estar visible, aunque puede desplazarse hacia abajo para verlo.

    ![interfaz de usuario de creador de personas](images/AzureLabs-Lab4-07.png)

4.  Inserte su **clave de autenticación de Azure**, que debe tener, desde el servicio de *face API* dentro de Azure.

5.  Introducir

    1. El *identificador* que desea asignar al *Grupo Person*. El identificador debe estar en minúsculas, sin espacios en blanco. Tome nota de este identificador, ya que será necesario más adelante en el proyecto de Unity.
    2. El *nombre* que desea asignar al *Grupo Person* (puede tener espacios).


6.  Presione el botón **Crear grupo de personas** . Debe aparecer un mensaje de confirmación debajo del botón.

> [!NOTE]
> Si tiene un error de "acceso denegado", Compruebe la ubicación que estableció para el servicio de Azure. Como se indicó anteriormente, esta aplicación está diseñada para ' oeste de EE. UU. '.

> [!IMPORTANT]
> Observará que también puede hacer clic en el botón **capturar un grupo conocido** : es para si ya ha creado un grupo de personas y desea usarlo, en lugar de crear uno nuevo. Tenga en cuenta que, si hace clic en *crear un grupo de personas* con un grupo conocido, también se recuperará un grupo.

7.  Inserte el *nombre* de la *persona* que desea crear.

    1. Haga clic en el botón **crear persona** .

    2. Debe aparecer un mensaje de confirmación debajo del botón.

    3. Si desea eliminar una persona que ha creado anteriormente, puede escribir el nombre en el cuadro de texto y presionar **eliminar persona**

8.  Asegúrese de que conoce la ubicación de diez (10) fotos de la persona que desea agregar al grupo.

9.  Presione **crear y abrir carpeta** para abrir el explorador de Windows en la carpeta asociada a la persona. Agregue las diez (10) imágenes en la carpeta. Deben ser del formato de archivo *jpg* o *PNG* .

10. Haga clic en **Enviar a Azure**. Un contador mostrará el estado del envío, seguido de un mensaje cuando se haya completado.

11. Una vez que el contador ha finalizado y se ha mostrado un mensaje de confirmación, haga clic en **entrenar** para entrenar su servicio.

Una vez completado el proceso, está listo para pasar a Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: configuración del proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **nuevo**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab4-08.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity. Inserte **MR_FaceRecognition**. Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab4-09.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab4-10.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab4-11.png)

5.  Vaya a **archivo > configuración de compilación** y asegúrese de que:

    1. El **dispositivo de destino** está establecido en **HoloLens**

        > Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.

    2. El **tipo de compilación** se establece en **D3D**
    3. **SDK** está establecido en la **versión más reciente instalada**
    4. La **versión de Visual Studio** está establecida en la **más reciente instalada**
    5. **Compilar y ejecutar** está establecido en **equipo local**
    6. Guarde la escena y agréguela a la compilación. 

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.

            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab4-12.png)

        2. Seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab4-13.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo **nombre de archivo**:, escriba **FaceRecScene**y, a continuación, presione **Guardar**.

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab4-14.png)

    7. El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* . 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab4-15.png)

7. En este panel, deben comprobarse algunas opciones de configuración:

    1. En la pestaña **otros valores** :

        1. La versión de **scripting** **en tiempo de ejecución** debe ser **experimental** (.net 4,6 equivalente). Al cambiar esto se desencadenará la necesidad de reiniciar el editor.
        2. El **back-end de scripting** debe ser **.net**
        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab4-16.png)
      
    2. En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        - **InternetClient**
        - **Web**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab4-17.png)

    3. Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![Actualice la configuración de X R.](images/AzureLabs-Lab4-18.png)

8.  De nuevo en la *configuración de compilación*, los **proyectos de Unity C#**  ya no están atenuados; Marque la casilla situada junto a este. 
9.  Cierre la ventana Configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).

## <a name="chapter-4---main-camera-setup"></a>Capítulo 4: configuración de la cámara principal

> [!IMPORTANT]
> Si desea omitir el componente de *configuración de Unity* de este curso y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html). Tenga en cuenta que este paquete también incluye la importación del *archivo dll de Newtonsoft*, que se describe en el [capítulo 5](#chapter-5--import-the-newtonsoftjson-library). Con esta importación, puede continuar en el [capítulo 6](#chapter-6---create-the-faceanalysis-class).

1.  En el panel *jerarquía* , seleccione la **cámara principal**.

2.  Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel del inspector*.

    1. El **objeto de cámara** debe tener el nombre de la **cámara principal** (tenga en cuenta la ortografía).

    2. La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía).

    3. Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**

    4. Establecer **marcas de borrado** en **color sólido**

    5. Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)**

        ![configuración de componentes de cámara](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capítulo 5: importar la biblioteca Newtonsoft. JSON

> [!IMPORTANT]
> Si importó el ". unitypackage Tools" en el [último capítulo](#chapter-4---main-camera-setup), puede omitir este capítulo.

Para ayudarle a deserializar y serializar los objetos recibidos y enviados al servicio de bot, debe descargar la biblioteca *Newtonsoft. JSON* . Encontrará una versión compatible ya organizada con la estructura de carpetas de Unity correcta en este [archivo de paquete de Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Para importar la biblioteca:

1.  Descargue el paquete de Unity.
2.  Haga clic en **activos**, **importar paquete**, **paquete personalizado**.

    ![Importación de la biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  Busque el paquete de Unity que ha descargado y haga clic en abrir.
4.  Asegúrese de que todos los componentes del paquete estén marcados y haga clic en **importar**.

    ![Importación de la biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capítulo 6: crear la clase FaceAnalysis

El propósito de la clase FaceAnalysis es hospedar los métodos necesarios para comunicarse con el servicio de reconocimiento facial de Azure. 

- Después de enviar el servicio a una imagen de captura, se lo analizará e identificará las caras dentro de y determinará si alguna pertenece a una persona conocida. 
- Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario en la escena.

Para crear la clase *FaceAnalysis* :

 1. Haga clic con el botón derecho en la *carpeta activos* que se encuentra en el panel Proyecto y, a continuación, haga clic en **crear** > **carpeta**. Llame a los **scripts**de la carpeta. 

    ![Cree la clase FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla. 
3.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic en **crear** >  **C# script**. Llame al script *FaceAnalysis*. 
4.  Haga doble clic en el nuevo script *FaceAnalysis* para abrirlo con Visual Studio 2017.
5.  Escriba los siguientes espacios de nombres encima de la clase *FaceAnalysis* :

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Ahora debe agregar todos los objetos que se usan para deserialising. Estos objetos deben agregarse **fuera** del script *FaceAnalysis* (debajo del corchete de cierre). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. No se usarán los métodos *Start ()* y *Update ()* , así que elimínelos ahora. 

8.  Dentro de la clase *FaceAnalysis* , agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Reemplace la **clave** y el **PersonGroupId** por la clave de servicio y el identificador del grupo que creó anteriormente.

9.  Agregue el método *activo ()* , que inicializa la clase, agregando la clase *ImageCapture* a la cámara principal y llama al método de creación de la etiqueta:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Agregue el método *CreateLabel ()* , que crea el objeto de *etiqueta* para mostrar el resultado del análisis:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Agregue el método *DetectFacesFromImage ()* y *GetImageAsByteArray ()* . La primera solicitud solicitará al servicio de reconocimiento facial que detecte cualquier posible aspecto en la imagen enviada, mientras que la última es necesaria para convertir la imagen capturada en una matriz de bytes:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Agregue el método *IdentifyFaces ()* , que solicita al *servicio de reconocimiento facial* que identifique cualquier aspecto conocido detectado anteriormente en la imagen enviada. La solicitud devolverá un identificador de la persona identificada, pero no el nombre:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Agregue el método *GetPerson ()* . Al proporcionar el identificador de persona, este método solicita al *servicio de reconocimiento facial* que devuelva el nombre de la persona identificada:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Recuerde **Guardar** los cambios antes de volver al editor de Unity.
15.  En el editor de Unity, arrastre el script FaceAnalysis desde la carpeta scripts del panel Proyecto hasta el objeto cámara principal en el *Panel jerarquía*. El nuevo componente de script se agregará a la cámara principal. 

![Colocar FaceAnalysis en la cámara principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capítulo 7: creación de la clase ImageCapture

El propósito de la clase *ImageCapture* es hospedar los métodos necesarios para comunicarse con el *servicio de reconocimiento facial de Azure* para analizar la imagen que se va a capturar, identificar caras y determinar si pertenece a una persona conocida. Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario en la escena.

Para crear la clase *ImageCapture* :
 
1.  Haga clic con el botón derecho dentro de la carpeta **scripts** que ha creado anteriormente y, a continuación, haga clic en **crear**,  **C# script**. Llame al script *ImageCapture*. 
2.  Haga doble clic en el nuevo script *ImageCapture* para abrirlo con Visual Studio 2017.
3.  Escriba los siguientes espacios de nombres encima de la clase ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Dentro de la clase *ImageCapture* , agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Agregue los métodos *activo ()* e *Inicio ()* necesarios para inicializar la clase y permitir que HoloLens Capture los gestos del usuario:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Agregue *TapHandler (),* al que se llama cuando el usuario realiza un gesto de *TAP* :

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Agregue el método *ExecuteImageCaptureAndAnalysis ()* , que iniciará el proceso de captura de imágenes:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Agregue los controladores a los que se llama cuando se ha completado el proceso de captura de fotografías:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Recuerde **Guardar** los cambios antes de volver al editor de Unity.

## <a name="chapter-8---building-the-solution"></a>Capítulo 8: compilar la solución

Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.

Antes de hacerlo, asegúrese de que:

-   Toda la configuración mencionada en el capítulo 3 se establece correctamente. 
-   El script *FaceAnalysis* se adjunta al objeto de cámara principal. 
-   La **clave de autenticación** y el ID. de **Grupo** se han establecido en el script *FaceAnalysis* .

En este momento está listo para compilar la solución. Una vez creada la solución, estará listo para implementar la aplicación.

Para comenzar el proceso de compilación:

1.  Guarde la escena actual haciendo clic en archivo, guardar.
2.  Vaya a archivo, configuración de compilación y haga clic en agregar escenas abiertas.
3.  Asegúrese de marcar los proyectos C# de Unity.

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Presione compilar. Al hacerlo, Unity iniciará una ventana del explorador de archivos, donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora, dentro del proyecto de Unity y llámela. Después, con la carpeta de la aplicación seleccionada, Presione Seleccionar carpeta. 
5.  Unity comenzará a compilar el proyecto, en la carpeta de la aplicación. 
6.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del explorador de archivos en la ubicación de la compilación.

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Abra la carpeta de la aplicación y, a continuación, abra la solución nuevo proyecto (como se ha indicado anteriormente, MR_FaceRecognition. sln).


## <a name="chapter-9---deploying-your-application"></a>Capítulo 9: implementación de la aplicación

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

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Vaya al **menú compilar** y haga clic en **implementar solución**para transferir localmente la aplicación a HoloLens.
6.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.

> [!NOTE]
> Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local*y establezca la **configuración** en *depurar*, con *x86* como **plataforma**. A continuación, implemente en el equipo local, mediante el **menú compilar**, seleccionando *implementar solución*. 


## <a name="chapter-10---using-the-application"></a>Capítulo 10: uso de la aplicación

1.  Con HoloLens, inicie la aplicación.
2.  Fíjese en la persona que ha registrado con el *face API*. Asegúrese de que:

    -  La superficie de la persona no está demasiado lejana y es claramente visible
    -  La iluminación del entorno no es demasiado oscura

3.  Use el gesto de puntear para capturar la imagen de la persona.
4.  Espere a que la aplicación envíe la solicitud de análisis y reciba una respuesta.
5.  Si la persona se reconoció correctamente, el nombre de la persona aparecerá como texto de la interfaz de usuario.
6.  Puede repetir el proceso de captura con el gesto de punteo cada pocos segundos.

## <a name="your-finished-azure-face-api-application"></a>Su aplicación de Azure Face API finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio de reconocimiento facial de Azure para detectar rostros dentro de una imagen e identificar cualquier rostro conocido.

![resultado de la finalización de este curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

**Azure Face API** es lo suficientemente eficaz como para detectar hasta 64 caras en una sola imagen. Amplíe la aplicación para que pueda reconocer dos o tres caras, entre muchas otras personas.

### <a name="exercise-2"></a>Ejercicio 2

**Azure Face API** también puede proporcionar todos los tipos de información de atributos. Integre esto en la aplicación. Esto podría ser aún más interesante, cuando se combina con el [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/).
