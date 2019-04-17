---
title: El Sr. y Azure 304 - reconocimiento de caras
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, se enfrentan a mixed reality, academy, unity, tutorial, api, reconocimiento, vr envolventes, hololens,
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605505"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>El Sr. y Azure 304: Reconocimiento de caras

![resultado de realizar este curso](images/AzureLabs-Lab4-00.png)

En este curso obtendrá información sobre cómo agregar funcionalidades de reconocimiento de cara a una aplicación de realidad mixta, con Azure Cognitive Services, Microsoft Face API.

*Azure Face API* es un servicio de Microsoft, que proporciona a los desarrolladores con los algoritmos más avanzados de cara, todo ello en la nube. El *Face API* tiene dos funciones principales: la detección con atributos de caras y reconocimiento se enfrentan. Esto permite a los desarrolladores simplemente un conjunto de grupos de caras y, a continuación, enviar las imágenes de la consulta al servicio más adelante, para determinar a quién pertenece una cara. Para obtener más información, visite la [página Azure Face Recognition](https://azure.microsoft.com/services/cognitive-services/face/).

Una vez completado este curso, tendrá una realidad mixta HoloLens aplicación, que podrá hacer lo siguiente:

1. Use un **gesto de pulsar** para iniciar la captura de una imagen con la cámara integrada de HoloLens. 
2. Enviar la imagen capturada a la *Azure Face API* service.
3. Recibir los resultados de la *Face API* algoritmo.
4. Use una interfaz de usuario simple para mostrar el nombre de las personas coincidentes.

Esto le mostrará cómo obtener los resultados desde el servicio de API de cara a la aplicación de realidad mixta basada en Unity.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 304: Reconocimiento de caras</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality. Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC. Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md)
- [El SDK más reciente de Windows 10](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Una cámara conectada a su equipo (para el desarrollo de amplias auriculares)
- Acceso a Internet para el programa de instalación de Azure y la recuperación de Face API

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
2.  Configurar y probar su HoloLens. Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: el Portal de Azure

Para usar el *Face API* service en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.

1.  En primer lugar, inicie sesión en el [Portal de Azure](https://portal.azure.com). 

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Face API*, presione **ENTRAR**.

    ![Busque se enfrentan a api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.

3.  La nueva página proporcionará una descripción de la *Face API* service. En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.

    ![información de la api se enfrentan](images/AzureLabs-Lab4-02.png)

4.  Una vez que ha hecho clic **crear**:

    1. Inserte el nombre deseado para esta instancia de servicio.

    2. Seleccione una suscripción.

    3. Seleccione el plan de tarifa adecuado para usted, si ésta es la primera hora de creación de un *Face API de servicio*, un nivel gratuito (denominado F0) debe estar disponible para usted.

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes). 

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. La aplicación para UWP, **persona Maker**, que usará más adelante, requiere el uso de "West US" para la ubicación.

    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7. Seleccione **crear *.**

        ![Crear servicio de api se enfrentan](images/AzureLabs-Lab4-03.png)

5.  Una vez que ha hecho clic **crear *** tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![notificación de creación de servicio](images/AzureLabs-Lab4-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![Vaya a la notificación de recursos](images/AzureLabs-Lab4-05.png)

8.  Cuando esté listo, haga clic en **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.

    ![claves de api se enfrentan a Access](images/AzureLabs-Lab4-06.png)

9.  En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través de la suscripción del servicio en la "clave". Desde el *inicio rápido* página, de su *Face API* , el primer punto de servicio es el número a 1, *obtener las claves.*

10. En el *servicio* página Seleccionar cualquier azul **claves** hipervínculo (si está en la página de inicio rápido), o la **claves** vínculo en el menú de navegación de servicios (a la izquierda, indicado por la ' clave ' icono), para revelar las claves.

    > [!NOTE] 
    > Tome nota de cualquiera de las claves y protegerla, ya que lo necesitará más adelante.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capítulo 2: mediante la aplicación de UWP 'Persona Maker'

Asegúrese de descargar la aplicación de UWP creado previamente denominado [persona Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Esta aplicación no es el producto final de este curso, sólo una herramienta que le ayudarán a crear las entradas de Azure, que utilizan el proyecto más adelante.

**Persona Maker** le permite crear entradas de Azure, que están asociadas con las personas y grupos de personas. La aplicación colocará toda la información necesaria en un formato que, a continuación, más adelante se puede usar por el FaceAPI, para reconocer las caras de personas a las que han agregado. 

> [IMPORTANTE] **Persona Maker** ciertas limitaciones básica, se utiliza para ayudar a garantizar que no superen el número de llamadas de servicio por minuto para el **nivel de suscripción gratuita**. El texto de color verde en la parte superior se cambia a rojo y actualizar como "Activo" cuando se produce la limitación; Si este es el caso, simplemente espera la aplicación (esperará hasta que siguiente puede continuar teniendo acceso al servicio de cara, como activo / en la actualización cuando se puede volver a usarlo).

Esta aplicación usa el *Microsoft.ProjectOxford.Face* bibliotecas, que le permitirán sacar el máximo usan de Face API. Esta biblioteca está disponible gratuitamente como un paquete de NuGet. Para obtener más información acerca de esto y otros similares, las API [Asegúrese de visitar el artículo de referencia de API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Estas son solo los pasos necesarios, instrucciones sobre cómo realizar estas operaciones es más abajo en el documento. El **persona Maker** aplicación le permitirá:
>
> - Crear un *persona grupo*, que es un grupo compuesto por varias personas que desea asociar con ella. Con su cuenta de Azure puede hospedar varios grupos de personas.
>
> - Crear un *persona*, que es un miembro de un grupo de persona. Cada persona tiene un número de *cara* imágenes asociadas con él.
>
> -  Asignar *se enfrentan a imágenes* a un *persona*, para permitir que el servicio de Azure Face API reconocer una *persona* por la correspondiente *cara*.
>
> -  *Entrenar* su *servicio de API se enfrentan a Azure*.

Tenga en cuenta, por lo que para formar a esta aplicación para que reconozca las personas, deberán fotos de primer planos diez (10) de cada persona que le gustaría agregar a la persona del grupo. La aplicación para Windows 10 Cam puede ayudarle a tenerla. Debe asegurarse de que cada foto está desactivada (evitar desenfoque, ocultar o estén demasiado lejos, desde el asunto), tiene la foto en formato de archivo jpg o png, con el tamaño del archivo de imagen que se va a no más **4 MB**y no menos de **1 KB**.

> [!NOTE]
> Si está siguiendo este tutorial, no use su propia imagen para el entrenamiento, como cuando se coloca el HoloLens, no se observa usted mismo. Utilice la cara de un alumno colega o empleado.

Ejecutando **Maker persona**:

1.  Abra el **PersonMaker** carpeta y haga doble clic en el *PersonMaker solución* para abrirlo con *Visual Studio*.

2.  Una vez el *PersonMaker solución* está abierto, asegúrese de que:

    1. El *configuración de la solución* está establecido en **depurar**.

    2. El *plataforma de solución* está establecido en **x86**

    3. El *plataforma de destino* es **máquina Local**.

    4.  También es posible que deba *restaurar paquetes NuGet* (haga clic en el *solución* y seleccione **restaurar paquetes NuGet**).

3.  Haga clic en *máquina Local* y se iniciará la aplicación. Tenga en cuenta en pantallas más pequeñas, todo el contenido puede no estar visible, aunque puede desplazarse más abajo para verlo.

    ![interfaz de usuario del creador de persona](images/AzureLabs-Lab4-07.png)

4.  Inserte su **clave de autenticación de Azure**, que debe tener, desde su *Face API* servicio dentro de Azure.

5.  insertar:

    1. El *ID* que desea asignar a la *persona grupo*. El identificador debe estar en minúscula, sin espacios en blanco. Tome nota de este identificador, tal como se requerirá más adelante en el proyecto de Unity.
    2. El *nombre* que desea asignar a la *persona grupo* (puede tener espacios).


6.  Presione **crear grupo de persona** botón. Debajo del botón, debería aparecer un mensaje de confirmación.

> [!NOTE]
> Si tiene un error "Acceso denegado", compruebe la ubicación que haya configurado para su servicio de Azure. Como se indicó anteriormente, esta aplicación está diseñada para "West US".

> [!IMPORTANT]
> Observará que también puede hacer clic en el **capturar un grupo conocido** botón: se trata de si ya ha creado una persona grupo y deseos para usarlo en lugar de crear uno nuevo. Tenga en cuenta, si hace clic en *crear un grupo de persona* con un grupo conocido, esto también capturará un grupo.

7.  Insertar el *nombre* de la *persona* que desea crear.

    1. Haga clic en el **crear persona** botón.

    2. Debajo del botón, debería aparecer un mensaje de confirmación.

    3. Si desea eliminar una persona ha creado anteriormente, puede escribir el nombre en el cuadro de texto y presione **persona eliminar**

8.  Asegúrese de que conoce la ubicación de fotos de diez (10) de la persona que le gustaría agregar a su grupo.

9.  Presione **crear y Abrir carpeta** para abrir el Explorador de Windows en la carpeta asociada a la persona. Agregar las imágenes de diez (10) en la carpeta. Debe tratarse de *JPG* o *PNG* formato de archivo.

10. Haga clic en **enviar a Azure**. Un contador le mostrará el estado del envío, seguido de un mensaje cuando se ha completado.

11. Una vez que ha finalizado el contador y se ha mostrado un mensaje de confirmación, haga clic en **entrenar** para entrenar el servicio.

Una vez que haya completado el proceso, está listo para mover a Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **New**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab4-08.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Insertar **MR_FaceRecognition**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab4-09.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab4-10.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab4-11.png)

5.  Vaya a **archivo > configuración de compilación** y asegúrese de que:

    1. **Dispositivo de destino** está establecido en **HoloLens**

        > Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.

    2. **Tipo de compilación** está establecido en **D3D**
    3. **SDK** está establecido en **instalada más reciente**
    4. **Versión de Visual Studio** está establecido en **instalada más reciente**
    5. **Compilar y ejecutar** está establecido en **máquina Local**
    6. Guarde la escena y agregarlo a la compilación. 

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab4-12.png)

        2. Seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab4-13.png)

        3. Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo**: campo de texto, escriba **FaceRecScene**, a continuación, presione **guardar**.

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab4-14.png)

    7. El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra. 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab4-15.png)

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1. En el **otra configuración** pestaña:

        1. **Scripting** **en tiempo de ejecución versión** debe ser **Experimental** (.NET 4.6 equivalente). Cambiar esto desencadenará una necesidad de reiniciar el Editor.
        2. **Scripting de back-end** debe ser **.NET**
        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab4-16.png)
      
    2. Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        - **InternetClient**
        - **Webcam**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab4-17.png)

    3. Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab4-18.png)

8.  En *configuración de compilación*, **Unity C# proyectos** ya no está atenuada; Marque la casilla situada junto a esto. 
9.  Cierre la ventana de configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).

## <a name="chapter-4---main-camera-setup"></a>Capítulo 4: configuración de cámara principal

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo en el proyecto como un [personalizado Paquete](https://docs.unity3d.com/Manual/AssetPackages.html). Tenga en cuenta que este paquete también incluye la importación de la *Newtonsoft DLL*, descrito en [capítulo 5](#chapter-5--import-the-newtonsoft.json-library). Con esto se importa, puede continuar desde [capítulo 6](#chapter-6-create-the-faceanalysis-class).

1.  En el *jerarquía* Panel, seleccione el **cámara principal**.

2.  Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *Panel Inspector*.

    1. El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía!)

    2. La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)

    3. Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**

    4. Establecer **borrar las marcas de** a **Color sólido**

    5. Establecer el **en segundo plano** Color del componente de cámara para **negro, alfa de 0 (Hex código: #00000000)**

        ![configurar componentes de la cámara](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capítulo 5: importación de la biblioteca de Newtonsoft.Json

> [!IMPORTANT]
> Si ha importado el '.unitypackage' en el [último capítulo](#chapter-4--main-camera-setup), puede omitir este capítulo.

Para ayudarle a deserializan y serializan objetos recibidos y enviados al servicio Bot debe descargar el *Newtonsoft.Json* biblioteca. Encontrará una versión compatible ya organizada con la estructura de carpetas de Unity correcta en esta [archivo de paquete de Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

Para importar la biblioteca:

1.  Descargue el paquete de Unity.
2.  Haga clic en **activos**, **Importar paquete**, **paquete personalizado**.

    ![Importación de la biblioteca de Newtonsoft.Json](images/AzureLabs-Lab4-20.png)

3.  Busque el paquete de Unity que ha descargado y haga clic en Abrir.
4.  Asegúrese de que todos los componentes del paquete están activados y haga clic en **importación**.

    ![Importación de la biblioteca de Newtonsoft.Json](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capítulo 6: crear la clase FaceAnalysis

El propósito de la clase FaceAnalysis va a hospedar los métodos necesarios para comunicarse con el servicio de reconocimiento de caras de Azure. 

- Después de enviar el servicio de una imagen de captura, su análisis e identificará las caras dentro y determinar si cualquiera pertenecen a una persona conocida. 
- Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario de la escena.

Para crear el *FaceAnalysis* clase:

 1. Haga clic en el *carpeta Assets* ubicado en el Panel proyecto, haga clic en **crear** > **carpeta**. Llame a la carpeta **Scripts**. 

    ![Cree la clase FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirlo. 
3.  Haga clic en la carpeta, a continuación, haga clic en **crear**  >   **C# Script**. Llame al script *FaceAnalysis*. 
4.  Haga doble clic en el nuevo *FaceAnalysis* script para abrirlo con Visual Studio 2017.
5.  Escriba los siguientes espacios de nombres anterior el *FaceAnalysis* clase:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Deberá agregar todos los objetos que se usan para deserialising. Estos objetos deben agregarse **fuera** de la *FaceAnalysis* script (debajo de la llave inferior). 

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
7. El *Start()* y *Update()* métodos no se usará, por lo que eliminarlos ahora. 

8.  Dentro de la *FaceAnalysis* de clases, agregue las siguientes variables:

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
    > Reemplace el **clave** y **personGroupId** con su clave de servicio y el identificador del grupo que creó anteriormente.

9.  Agregar el *Awake()* método, que initialises la clase, agregando el *ImageCapture* clase a la cámara principal y llama al método de creación de etiqueta:

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

10. Agregar el *CreateLabel()* método, que crea el *etiqueta* objeto para mostrar el resultado del análisis:

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

11. Agregar el *DetectFacesFromImage()* y *GetImageAsByteArray()* método. La primera solicitud que el servicio de reconocimiento de caras para detectar cualquier posible cara en la imagen enviada, mientras que el último es necesario para convertir la imagen capturada en una matriz de bytes:

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

12. Agregar el *IdentifyFaces()* método, que solicita la *servicio de reconocimiento de caras* para identificar cualquier cara conocido detectado anteriormente en la imagen enviada. La solicitud devolverá un identificador de la persona identificada pero no el nombre:

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

            // Serialise to Json format
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

13. Agregar el *GetPerson()* método. Al proporcionar dicho Id., este método, a continuación, las solicitudes para el *servicio de reconocimiento de caras* para devolver el nombre de la persona identificado:

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

14.  No olvide **guardar** los cambios antes de volver al Editor de Unity.
15.  En el Editor de Unity, arrastre la secuencia de comandos FaceAnalysis desde la carpeta de Scripts en el panel de proyecto para el objeto de cámara principal en el *panel jerarquía*. El nuevo componente de script se agregará a la cámara principal así. 

![Colocar FaceAnalysis hasta la cámara principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capítulo 7: crear la clase ImageCapture

El propósito de la *ImageCapture* clase va a hospedar los métodos necesarios para comunicarse con su *servicio de reconocimiento de caras Azure* para analizar la imagen que capturará, identificación de caras en él y determinar si pertenece a una persona conocida. Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario de la escena.

Para crear el *ImageCapture* clase:
 
1.  Haga clic en el **Scripts** carpeta que ha creado anteriormente y, después, haga clic en **crear**,  **C# Script**. Llame al script *ImageCapture*. 
2.  Haga doble clic en el nuevo *ImageCapture* script para abrirlo con Visual Studio 2017.
3.  Escriba los siguientes espacios de nombres encima de la clase ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Dentro de la *ImageCapture* de clases, agregue las siguientes variables:

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

5.  Agregar el *Awake()* y *Start()* métodos necesarios para inicializar la clase y permitir la HoloLens capturar los gestos del usuario:

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

6.  Agregar el *TapHandler()* que se llama cuando el usuario realiza una *pulse* gestos:

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

7.  Agregar el *ExecuteImageCaptureAndAnalysis()* método, que se iniciará el proceso de captura de imagen:

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

8.  Agregue los controladores que se llaman cuando se ha completado el proceso de captura de fotos:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. No olvide **guardar** los cambios antes de volver al Editor de Unity.

## <a name="chapter-8---building-the-solution"></a>Capítulo 8: creación de la solución

Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.

Antes de hacerlo, asegúrese de que:

-   Todas las configuraciones que se mencionan en el capítulo 3 se establecen correctamente. 
-   La secuencia de comandos *FaceAnalysis* se adjunta al objeto de cámara principal. 
-   Tanto el **Auth Key** y **Id. de grupo** se han establecido dentro de la *FaceAnalysis* secuencia de comandos.

Este punto, está listo para compilar la solución. Una vez que se ha compilado la solución, estará listo para implementar la aplicación.

Para comenzar el proceso de compilación:

1.  Guarde la escena actual haciendo clic en archivo, guardar.
2.  Vaya al archivo de configuración de compilación, haga clic en Agregar escenas abierto.
3.  Asegúrese de graduación Unity C# proyectos.

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  Presione la compilación. Al hacerlo, Unity iniciará una ventana del explorador de archivos, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta ahora, dentro del proyecto de Unity y llámelo App. A continuación, con la carpeta de la aplicación seleccionada, presione seleccionar la carpeta. 
5.  Unity empezará a crear el proyecto, en la carpeta de la aplicación. 
6.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá una ventana del explorador de archivos en la ubicación de la compilación.

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  Abra la carpeta de aplicación y, a continuación, abra la nueva solución de proyecto (tal y como se muestra anteriormente, MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Capítulo 9: implementación de la aplicación

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

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  Vaya a la **menú compilar** y haga clic en **implementar solución**, para transferir localmente la aplicación a su HoloLens.
6.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.

> [!NOTE]
> Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**. Implementar, a continuación, en el equipo local machine, utilizando el **menú compilar**, seleccionar *implementar solución*. 


## <a name="chapter-10---using-the-application"></a>Capítulo 10: uso de la aplicación

1.  El exceso de la HoloLens, inicie la aplicación.
2.  Examine la persona que haya registrado con el *Face API*. Asegúrese de que:

    -  Su cara no está claramente visibles y demasiado distantes
    -  La iluminación de entorno no es demasiado oscura

3.  Usar el gesto de pulsar para capturar la imagen de la persona.
4.  Espere a que la aplicación enviar la solicitud de análisis y recibir una respuesta.
5.  Si la persona que ha sido reconocida correctamente, el nombre de persona aparecerá como texto de la interfaz de usuario.
6.  Puede repetir el proceso de captura con el gesto de pulsar cada pocos segundos.

## <a name="your-finished-azure-face-api-application"></a>La aplicación de API de cara Azure finalizada

Enhorabuena, compila una aplicación de realidad mixta que aprovecha el servicio de reconocimiento de caras de Azure para detectar caras dentro de una imagen e identificar cualquier caras conocidas.

![resultado de realizar este curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

El **Azure Face API** es lo suficientemente eficaz para detectar hasta 64 caras en una sola imagen. Ampliar la aplicación, por lo que pudieran reconocer caras de dos o tres, entre muchas otras personas.

### <a name="exercise-2"></a>Ejercicio 2

El **Azure Face API** también es capaz de proporcionar todos los tipos de información de atributos de vuelta. Integrar esto en la aplicación. Esto podría ser aún más interesante, cuando se combina con la [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).
