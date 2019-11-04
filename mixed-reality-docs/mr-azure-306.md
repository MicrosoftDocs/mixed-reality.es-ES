---
title: 'Sr. d y Azure 306: vídeo de streaming'
description: Complete este curso para aprender a implementar Azure Media Services en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, Media Services, streaming video, 360, envolventes, VR
ms.openlocfilehash: 6585aa731ff7ebb89beae67ab0b61ac5ef026e47
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438564"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR y Azure 306: streaming de vídeo

![última](images/AzureLabs-Lab6-00.png)
de inicio del producto ![última](images/AzureLabs-Lab6-01.png) de inicio del producto

En este curso aprenderá a conectar su Azure Media Services a una experiencia de Windows Mixed Reality VR para permitir la reproducción de vídeo a través de streaming de 360 Degree en auriculares de gran rendimiento. 

**Azure Media Services** son una colección de servicios que ofrece servicios de streaming de vídeo con calidad de difusión para llegar a audiencias de mayor tamaño en los dispositivos móviles más populares de hoy en día. Para obtener más información, visite la [página Azure Media Services](https://azure.microsoft.com/services/media-services).

Una vez finalizado este curso, tendrá una aplicación de auriculares envolvente de realidad mixta, que podrá hacer lo siguiente:

1. Recupere un vídeo de 360 grados de un **Azure Storage**a través de **Azure Media Services**.

2. Muestra el vídeo de 360 Degree recuperado dentro de una escena de Unity.

3. Desplazarse entre dos escenas, con dos vídeos diferentes.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 306: streaming de vídeo</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo). Puede usar el software más reciente, como se indica en el [artículo instalar las herramientas](install-the-tools.md), aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md)
- Acceso a Internet para la configuración de Azure y la recuperación de datos
- Vídeos de 2 360 grados en formato MP4 (puede encontrar algunos vídeos sin derechos de autor [en esta página de descarga](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
2.  Configure y pruebe sus auriculares de la realidad mixta.

    > [!NOTE]
    > **No** necesitará controladores de movimiento para este curso. Si necesita ayuda para configurar el casco envolvente, haga clic en [el vínculo para configurar Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capítulo 1: Azure Portal: creación de la cuenta de Azure Storage

Para usar el **servicio Azure Storage**, debe crear y configurar una **cuenta de almacenamiento** en el Azure portal.

1.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **cuentas de almacenamiento** en el menú de la izquierda.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-02.png)

3.  En la pestaña **cuentas de almacenamiento** , haga clic en **Agregar**.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-03.png)

4.  En la pestaña **crear cuenta de almacenamiento** :

    1.  Inserte un **nombre** para la cuenta. tenga en cuenta que este campo solo acepta números y letras minúsculas.

    2.  En **modelo de implementación,** seleccione **Resource Manager**.

    3.  En **tipo de cuenta**, seleccione **almacenamiento (uso general V1)** .

    4.  En **rendimiento**, seleccione **estándar *.**

    5.  En **replicación** **, seleccione almacenamiento con redundancia local (LRS)** .

    6.  Deje la **transferencia segura requerida** como **deshabilitada**.

    7.  Seleccione una **suscripción**.

    8.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.

    9.  Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

5.  Tendrá que confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-04.png)

6.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

7.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-05.png)

8.  En este momento no es necesario seguir el recurso, simplemente vaya al siguiente capítulo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capítulo 2: Azure Portal: creación del servicio multimedia

Para usar Azure Media Services, debe configurar una instancia del servicio para que esté disponible para la aplicación (donde el titular de la cuenta debe ser un administrador).

1.  En Azure portal, haga clic en **crear un recurso** en la esquina superior izquierda y busque **Media Service,** Presione **entrar**. El recurso que desea actualmente tiene un icono de color rosa; Haga clic en esta para mostrar una nueva página.

    ![Azure portal](images/AzureLabs-Lab6-06.png)

2.  La nueva página proporcionará una descripción del **servicio multimedia**. En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una asociación con este servicio.

    ![Azure portal](images/AzureLabs-Lab6-07.png)

3.  Una vez que haya hecho clic en **crear** un panel, aparecerá donde debe proporcionar algunos detalles sobre el nuevo servicio multimedia:

    1.  Inserte el **nombre de cuenta** que desee para esta instancia de servicio.

    2.  Seleccione una **suscripción**.

    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común). 
    
    > Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar grupos de recursos de Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    5.  En la sección **cuenta de almacenamiento** , haga clic en la sección **Seleccione..** . y luego haga clic en la **cuenta de almacenamiento** que creó en el último capítulo.

    6.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7.  Haz clic en **Crear**.

        ![Azure portal](images/AzureLabs-Lab6-08.png)

4.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

5.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure portal](images/AzureLabs-Lab6-09.png)

6.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![Azure portal](images/AzureLabs-Lab6-10.png)

7.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.

8.  Dentro de la página nuevo servicio multimedia, dentro del panel de la izquierda, haga clic en el vínculo **activos** , que se encuentra cerca de la mitad.

9.  En la página siguiente, en la esquina superior izquierda de la página, haga clic en **cargar**.

    ![Azure portal](images/AzureLabs-Lab6-11.png)

10. Haga clic en el icono de la **carpeta** para examinar los archivos y seleccione el primer vídeo 360 que le gustaría transmitir. 
    
    > Puede seguir este [vínculo para descargar un vídeo de ejemplo](https://vimeo.com/214401712).

    ![Azure portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Los nombres de archivo largos pueden producir un problema con el codificador: para asegurarse de que los vídeos no tienen problemas, considere la posibilidad de acortar la longitud de los nombres de archivo de vídeo.

11. La barra de progreso se volverá verde cuando el vídeo termine de cargarse.

    ![Azure portal](images/AzureLabs-Lab6-13.png)

12. Haga clic en el texto anterior (**yourservicename-assets**) para volver a la página **activos** .

13. Observará que el vídeo se ha cargado correctamente. Haga clic en él.

    ![Azure portal](images/AzureLabs-Lab6-14.png)

14. La página a la que se redirige le mostrará información detallada acerca del vídeo. Para poder usar el vídeo debe codificarlo, haga clic en el botón **codificar** situado en la parte superior izquierda de la página.

    ![Azure portal](images/AzureLabs-Lab6-15.png)

15. Aparecerá un nuevo panel a la derecha, donde podrá establecer las opciones de codificación para el archivo. Establezca las siguientes propiedades (algunas ya estarán establecidas de forma predeterminada):

    1.  **Nombre del codificador multimedia *Media Encoder Standard***

    2.  **Contenido preestablecido de codificación de *varias velocidades de bits adaptables MP4***

    3.  **Nombre *del trabajo Media Encoder Standard procesamiento de VIDEO1. mp4***

    4.  **Nombre de recurso multimedia *de salida VIDEO1. MP4: Media Encoder Standard codificado***

        ![Azure portal](images/AzureLabs-Lab6-16.png)

16. Haga clic en el botón **Crear**.

17. Observará que se **ha agregado**una barra con el trabajo de codificación, haga clic en esa barra y aparecerá un panel con el progreso de la codificación que se muestra en ella.

    ![Azure portal](images/AzureLabs-Lab6-17.png)

    ![Azure portal](images/AzureLabs-Lab6-18.png)

18. Espere a que se complete el trabajo. Una vez hecho esto, no dude en cerrar el panel con la "X" en la parte superior derecha de ese panel.

    ![Azure portal](images/AzureLabs-Lab6-19.png)

    ![Azure portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > El tiempo que tarda, depende del tamaño de archivo del vídeo. Este proceso puede tardar bastante tiempo.

19. Ahora que se ha creado la versión codificada del vídeo, puede publicarla para que sea accesible. Para ello, haga clic en los **recursos** de vínculo azul para volver a la página activos.

    ![Azure portal](images/AzureLabs-Lab6-21.png)

20. Verá el vídeo junto con otro, que es el tipo de **recurso _MP4 de velocidad de bits múltiple_** .

    ![Azure portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Es posible que observe que el nuevo recurso, junto con el vídeo inicial, es *desconocido*y tiene ' 0 ' bytes para su **tamaño**, solo tiene que actualizar la ventana para que se actualice.

21. Haga clic en este nuevo recurso.

    ![Azure portal](images/AzureLabs-Lab6-23.png)

22. Verá un panel similar al que usó antes, solo que se trata de un recurso diferente. Haga clic en el botón **publicar** situado en el centro superior de la página.

    ![Azure portal](images/AzureLabs-Lab6-24.png)

23. Se le pedirá que establezca un **localizador**, que es el punto de entrada, en archivo/s en los recursos. En el escenario, establezca las siguientes propiedades:

    1.  **Tipo de localizador** > **progresiva**.

    2.  La **fecha** y la **hora** se establecerán automáticamente, desde la fecha actual, hasta una hora futura (100 años en este caso). Deje tal cual o cámbielo para adaptarse.

    > [!NOTE]
    > Para obtener más información acerca de los localizadores y lo que puede elegir, visite la [documentación de Azure Media Services](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. En la parte inferior de ese panel, haga clic en el botón **Agregar** .

    ![Azure portal](images/AzureLabs-Lab6-25.png)

25. El vídeo ya está publicado y se puede transmitir mediante su punto de conexión. Más abajo, la página es una sección de **archivos** . Aquí es donde serán las distintas versiones codificadas del vídeo. Seleccione la resolución más alta posible (en la imagen siguiente es el archivo 1920x960) y, a continuación, aparecerá un panel a la derecha. Allí encontrará una **dirección URL de descarga**. Copie este **punto de conexión** , ya que lo usará más adelante en el código.

    ![Azure portal](images/AzureLabs-Lab6-26.png)    

    ![Azure portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > También puede hacer clic en el botón **reproducir** para reproducir el vídeo y probarlo.

26. Ahora debe cargar el segundo vídeo que usará en este laboratorio. Siga los pasos anteriores y repita el mismo proceso para el segundo vídeo. Asegúrese de copiar también el segundo **punto de conexión** . Use el siguiente [vínculo para descargar un segundo vídeo](https://vimeo.com/214402865).

27. Una vez publicados ambos vídeos, está listo para pasar al siguiente capítulo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3: configuración del proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra **Unity** y haga clic en **nuevo**. 

    ![Azure portal](images/AzureLabs-Lab6-28.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity, insertar **MR\_360VideoStreaming.** . Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la ubicación en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![Azure portal](images/AzureLabs-Lab6-29.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio.** Vaya a ***Editar* *preferencias*** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![Azure portal](images/AzureLabs-Lab6-30.png)

4.  A continuación, vaya a configuración de compilación de ***archivos*** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .

5.  Asegúrese también de que:

    1. El **dispositivo de destino** se establece en **cualquier dispositivo.**
    
    2.  El **tipo de compilación** se establece en **D3D.**

    3.  **SDK** está establecido en **instalado más recientemente.**

    4.  La **versión de Visual Studio** está establecida en **instalación más reciente.**

    5.  **Compilar y ejecutar** está establecido en **equipo local.**

    6.  No se preocupe por la configuración de **escenas** en este momento, ya que las configurará más adelante.

    7.  El resto de la configuración debe dejarse como predeterminada por ahora.

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-31.png)

6.  En la ventana **configuración de compilación** , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** . 

7. En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  La versión de **scripting** **en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).

        2. El **back-end de scripting** debe ser **.net.**

        3. El **nivel de compatibilidad de API** debe ser **.net 4,6.**

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-32.png)

    2.  Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-33.png)

    3.  En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        - **InternetClient**

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-34.png)

8.  Una vez realizados los cambios, cierre la ventana **configuración de compilación** .

9.  Guarde el proyecto **archivo* * guardar proyecto * *.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capítulo 4: importación del paquete Unity de InsideOutSphere

> [!IMPORTANT]
> Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el **capítulo 5**. Todavía tendrá que crear un proyecto de Unity.

En este curso, deberá descargar un paquete de recursos de Unity llamado [**InsideOutSphere. unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Cómo importar **unitypackage Tools**:

1.  Con el panel de Unity delante de usted, haga clic en **recursos** en el menú de la parte superior de la pantalla y, a continuación, haga clic en **importar paquete > paquete personalizado**.

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-35.png)

2.  Use el selector de archivos para seleccionar el paquete **InsideOutSphere. unitypackage Tools** y haga clic en **abrir**. Se le mostrará una lista de los componentes de este recurso. Confirme la importación haciendo clic en **importar**.

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-36.png)

3.  Una vez que haya finalizado la importación, observará que se han agregado tres nuevas carpetas, **materiales**, **modelos**y **Prefabs**a la carpeta **assets** . Este tipo de estructura de carpetas es típico para un proyecto de Unity.

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-37.png)

    1.  Abra la carpeta **modelos** y verá que se ha importado el modelo **InsideOutSphere** .

    2.  En la carpeta **materiales** encontrará el **InsideOutSpheres** material *lambert1*, junto con un material denominado *ButtonMaterial*, que se usa en el GazeButton, que verá en breve.

    3.  La carpeta **Prefabs** contiene recurso prefabricado **InsideOutSphere** , que contiene el modelo **InsideOutSphere** y el *GazeButton*.

    4.  **No se incluye ningún código**, se escribirá el código siguiendo este curso.


4.  Dentro de la **jerarquía**, seleccione el objeto de **cámara principal** y actualice los siguientes componentes:

    1.  **Transformación**

        1.  Position = **X**: 0, **y**: 0, **Z**: 0.

        2. Rotation = **X**: 0, **y**: 0, **Z**: 0.

        3. Escala **X**: 1, **y**: 1, **Z**: 1.

    2.  **Cámara**

        1. **Borrar marcas**: color sólido.

        2.  **Planos de recorte**: Near: 0,1, Far: 6.

            ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-38.png)

5.  Navegue hasta la carpeta **recurso prefabricado** y, a continuación, arrastre **InsideOutSphere** recurso prefabricado al panel **jerarquía** .

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-39.png)

6.  Expanda el objeto **InsideOutSphere** dentro de la **jerarquía** haciendo clic en la pequeña flecha situada junto a él. Verá un objeto **secundario** debajo de él denominado **GazeButton**. Se usará para cambiar escenas y, por lo tanto, vídeos.

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-40.png)

7.  En la ventana del inspector, haga clic en el componente de transformación de **InsideOutSphere**, asegúrese de que se establecen las siguientes propiedades:

    |            |    TRANSFORMACIÓN: POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORMACIÓN-GIRO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORMACIÓN DE ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **S** 1          |  **Z** 1  |

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-41.png)

8.  Haga clic en el objeto secundario **GazeButton** y establezca su **transformación** como se indica a continuación:

    |            |    TRANSFORMACIÓN: POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3,6|          **Y** 1,3        |  **Z** 0  |

    |            |    TRANSFORMACIÓN-GIRO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMACIÓN DE ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **S** 1          |  **Z** 1  |

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capítulo 5: creación de la clase videocontroller

La clase **videocontroller** hospeda los dos puntos de conexión de vídeo que se usarán para transmitir el contenido de Azure Media Services.

Para crear esta clase:

1.  Haga clic con el botón derecho en la **carpeta de recursos**, que se encuentra en el panel **proyecto** , y haga clic en **crear > carpeta**. Asigne a la carpeta el nombre **scripts**.

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-43.png)

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-44.png)

2.  Haga doble clic en la carpeta **scripts** para abrirla.

3.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic en **crear > C\# script**. Asigne un nombre al **videocontrolador**del script.

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-45.png)

4.  Haga doble clic en el nuevo script **videocontroller** para abrirlo con **Visual Studio 2017.**

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-46.png)

5.  Actualice los espacios de nombres en la parte superior del archivo de código como se indica a continuación:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Escriba las siguientes variables en la clase **videocontroller** , junto con el método **activo ()** :

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  Ahora es el momento de escribir los puntos de conexión de los vídeos de Azure Media Services:

    1.  El primero en la variable *video1endpoint* .
    
    2.  El segundo en la variable *video2endpoint* .

    > [!WARNING]
    > Existe un problema conocido con el uso de *https* en Unity, con la versión 2017.4.1 F1. Si los vídeos proporcionan un error en la reproducción, pruebe a usar ' http ' en su lugar.

8.  A continuación, es necesario editar el método **Start ()** . Este método se desencadenará cada vez que el usuario cambie la escena (por lo tanto, cambiando el vídeo) examinando el botón de mira.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Después del método **Start ()** , inserte el método *IEnumerator* **PlayVideo ()** , que se usará para iniciar vídeos sin problemas (por lo que no se verá ningún salto).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. El último método que necesita para esta clase es el método **ChangeScene ()** , que se usará para intercambiar entre las escenas.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > El método **ChangeScene ()** utiliza una sencilla característica de C\# denominada *operador condicional*. Esto permite comprobar las condiciones y, después, los valores devueltos en función del resultado de la comprobación, todo dentro de una única instrucción. Siga este [vínculo para obtener más información acerca del operador condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

11. Guarde los cambios en Visual Studio antes de volver a Unity.

12. De nuevo en el editor de Unity, haga clic y arrastre la clase **videocontroller** [desde] {. Underline} la carpeta **scripts** al objeto de **cámara principal** en el panel **jerarquía** .

13. Haga clic en la **cámara principal** y mire en el **panel del inspector**. Observará que, dentro del componente de script recién agregado, hay un campo con un valor vacío. Se trata de un campo de referencia, que tiene como destino las variables públicas del código.

14. Arrastre el objeto **InsideOutSphere** desde el **Panel jerarquía** hasta la ranura de la **esfera** , tal como se muestra en la imagen siguiente.

    ![crear la clase videocontroller](images/AzureLabs-Lab6-47.png)
    ![crear la clase videocontroller](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capítulo 6: crear la clase fijamente

Esta clase es responsable de crear un **Raycast** que se proyectará hacia delante desde la **cámara principal**, para detectar qué objeto está examinando el usuario. En este caso, **Raycast** deberá identificar si el usuario mira el objeto **GazeButton** en la escena y desencadena un comportamiento.

Para crear esta clase:

1.  Vaya a la carpeta **scripts** que creó anteriormente.

2.  Haga clic con el botón derecho en el panel **proyecto** , **crear* * C\# script * *. Asigne un nombre **al script.**

3.  Haga doble clic en el nuevo script de ***miraciones*** para abrirlo con **Visual Studio 2017.**

4.  Asegúrese de que el siguiente espacio de nombres se encuentra en la parte superior del script y quite los demás:

    ```csharp
    using UnityEngine;
    ```

5.  Después, agregue las siguientes variables dentro de la clase **mirate** :

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  Ahora es necesario agregar el código para los métodos **activo ()** e **Inicio ()** .

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Agregue el código siguiente en el método **Update ()** para proyectar un Raycast y detectar el acierto de destino:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Guarde los cambios en Visual Studio antes de volver a Unity.

9.  Haga clic y arrastre la clase **mira** desde la carpeta scripts hasta el objeto cámara principal en el panel **jerarquía** .

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capítulo 7: configuración de las dos escenas de Unity

El propósito de este capítulo es configurar las dos escenas, cada una de las cuales hospeda un vídeo para la transmisión. Duplicará la escena que ya ha creado, de modo que no necesite configurarla de nuevo, aunque después modificará la nueva escena, de modo que el objeto *GazeButton* esté en una ubicación diferente y tenga un aspecto diferente. Esto es para mostrar cómo cambiar entre escenas.

1.  Para ello, vaya a **archivo > guardar la escena como...** . Aparecerá una ventana de guardar. Haga clic en el botón **nueva carpeta** .

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-49.png)

2.  Asigne a la carpeta el nombre **Scenes**.

3.  La ventana **Guardar escena** permanecerá abierta. Abra la carpeta de **escenas** recién creada.

4.  En el campo **nombre de archivo:** , escriba **VideoScene1**y, a continuación, presione **Guardar**.

5.  De nuevo en Unity, abra la carpeta **Scenes** y haga clic con el botón primario en el archivo **VideoScene1** . Usar el teclado y presionar **Ctrl + D** se duplicará la escena

    > [!TIP]
    > El comando **duplicado** también puede realizarse desplazándose a **Editar > duplicar**.

6.  Unity incrementará automáticamente el número de nombres de escena, pero Compruébelo de todos modos para asegurarse de que coincide con el código insertado anteriormente.

    >  Debe tener **VideoScene1** y **VideoScene2**.

7.  Con las dos escenas, vaya a **archivo > configuración de compilación**. Con la ventana **configuración de compilación** abierta, arrastre las escenas hasta la sección **escenas en la compilación** .

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Puede seleccionar las dos escenas de la carpeta **Scenes** mientras mantiene presionado el botón **Ctrl** y, a continuación, hacer clic con el botón izquierdo en cada escena y, por último, arrastrar ambas cosas.

8.  Cierre la ventana **configuración de compilación** y haga doble clic en **VideoScene2**.

9.  Con la segunda escena abierta, haga clic en el objeto secundario **GazeButton** de **InsideOutSphere**y establezca su transformación como se indica a continuación:

    |            |    TRANSFORMACIÓN: POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1,3         | **Z** 3,6 |

    |            |    TRANSFORMACIÓN-GIRO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMACIÓN DE ESCALA     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **S** 1          |  **Z** 1  |

10. Con el elemento secundario **GazeButton** todavía seleccionado, fíjese en el **Inspector** y en el **filtro de malla**. Haga clic en el destino pequeño junto al campo de referencia de la **malla** :

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-51.png)

11. Aparecerá una ventana emergente de **la malla seleccionada** . Haga doble clic en la malla del **cubo** de la lista de **activos**.

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-52.png)

12. El **filtro de malla** se actualizará y ahora será un **cubo**. Ahora, haga clic en el icono de **engranaje** junto a **Sphere Colisionador** y haga clic en **quitar componente**para eliminar el Colisionador de este objeto.

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-53.png)

13. Con el **GazeButton** aún seleccionado, haga clic en el botón **Agregar componente** situado en la parte inferior del **Inspector**. En el campo de búsqueda, escriba **Box**y **Box Colisionador** será una opción; haga clic en él para agregar un **Colisionador de cuadro** al objeto **GazeButton** .

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-54.png)

14. El **GazeButton** se ha actualizado de forma parcial para que tenga un aspecto diferente. sin embargo, ahora creará un nuevo **material**, de modo que tenga un aspecto completamente diferente y sea más fácil de reconocer como un objeto diferente, que el objeto de la primera escena.

15. Vaya a la carpeta **materiales** , dentro del **panel Proyecto**. Duplique el material de **ButtonMaterial** (presione **Ctrl** + **D** en el teclado o haga clic con el botón primario en el **material**y, a continuación, en la opción de menú **Editar** archivo, seleccione **duplicar**).

    ![capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-55.png)
    ![capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-56.png)

16. Seleccione el nuevo material de **ButtonMaterial** (aquí llamado **ButtonMaterial 1**) y, dentro del **Inspector**, haga clic en la ventana color **Albedo** . Aparecerá un menú emergente en el que podrá seleccionar otro color (elija el que desee) y, a continuación, cerrar el elemento emergente. El material será su propia instancia y diferente al original.

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-57.png)

17. Arrastre el nuevo **material** hasta el elemento secundario **GazeButton** y, a continuación, actualice su apariencia para que se pueda distinguir fácilmente del primer botón de escenas.

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-58.png)

18. Llegados a este punto, puede probar el proyecto en el editor antes de compilar el proyecto de UWP.

    -  Presione el botón de **reproducción** en el **Editor** y desgaste el casco.

        ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-59.png)

19. Examine los dos objetos **GazeButton** para cambiar entre el primer y el segundo vídeo.

## <a name="chapter-8---build-the-uwp-solution"></a>Capítulo 8: compilar la solución de UWP

Una vez que se ha asegurado de que el editor no tiene errores, está listo para compilar.

Para compilar:

1.  Guarde la escena actual haciendo clic en **archivo > guardar**.

2.  Active la casilla llamada **Unity C\# proyectos** (esto es importante porque le permitirá editar las clases una vez completada la compilación).

3.  Vaya a **archivo > configuración de compilación**y haga clic en **compilar**.

4.  Se le pedirá que seleccione la carpeta en la que desea buildthe solución.

5.  Cree una carpeta **compilaciones** y, dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.

6.  Haga clic en la nueva carpeta y, a continuación, haga clic en **Seleccionar carpeta**para que se inicie la compilación en esa ubicación.

    ![el capítulo 8: compilar la solución UWP](images/AzureLabs-Lab6-60.png)
    ![capítulo 8: compilar la solución UWP](images/AzureLabs-Lab6-61.png)

7.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación.

## <a name="chapter-9---deploy-on-local-machine"></a>Capítulo 9: implementación en el equipo local

Una vez completada la compilación, aparecerá una ventana del **Explorador de archivos** en la ubicación de la compilación. Abra la carpeta con el nombre y la compilación en y, a continuación, haga doble clic en el archivo de solución (. sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.

Lo único que queda por hacer es implementar la aplicación en el equipo (o *equipo local*).

Para implementar en la máquina local:

1.  En **Visual Studio 2017**, abra el archivo de solución que acaba de crear.

2.  En la **plataforma**de la solución, seleccione **x86, equipo local**.

3.  En la **configuración de soluciones** , seleccione **depurar**.

    ![Capítulo 9: implementación en el equipo local](images/AzureLabs-Lab6-62.png)

4.  Ahora tendrá que restaurar los paquetes en la solución. Haga clic con el botón derecho en la **solución**y haga clic en **restaurar paquetes NuGet para la solución...**

    > [!NOTE] 
    > Esto se hace porque los paquetes compilados por Unity deben estar destinados a funcionar con las referencias de los equipos locales.

5.  Vaya al **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina. Visual Studio compilará primero y, a continuación, implementará la aplicación.

6.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

    ![Capítulo 9: implementación en el equipo local](images/AzureLabs-Lab6-63.png)

Al ejecutar la aplicación de realidad mixta, se encontrará dentro del modelo **InsideOutSphere** que usó en la aplicación. Esta esfera será el lugar al que se transmitirá el vídeo, lo que proporciona una vista de 360 grados del vídeo entrante (que se filmó para este tipo de perspectiva). No se sorprenda si el vídeo tarda un par de segundos en cargarse, la aplicación está sujeta a la velocidad de Internet disponible, ya que el vídeo debe capturarse y descargarse, por lo que debe transmitirse a la aplicación.
Cuando esté listo, cambie las escenas y abra el segundo vídeo, Gazing en la esfera roja. Después, no dude en volver, usando el cubo azul en la segunda escena.

## <a name="your-finished-azure-media-service-application"></a>Su aplicación finalizada de Azure Media Services
 
Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Media Services para transmitir vídeos de 360.

![resultado de laboratorio](images/AzureLabs-Lab6-00.png)

![resultado de laboratorio](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

**Ejercicio 1**

Es totalmente posible usar una sola escena para cambiar vídeos en este tutorial. Experimente con la aplicación y conviértalo en una sola escena. Quizás incluso agregue otro vídeo a la combinación.

**Ejercicio 2**

Experimente con Azure y Unity e intente implementar la capacidad de la aplicación para seleccionar automáticamente un vídeo con un tamaño de archivo diferente, en función de la seguridad de una conexión a Internet.


