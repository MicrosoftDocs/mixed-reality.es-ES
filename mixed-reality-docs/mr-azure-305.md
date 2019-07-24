---
title: 'MR y Azure 305: funciones y almacenamiento'
description: Complete este curso para aprender a implementar Azure Storage y funciones en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, funciones, almacenamiento, hololens, envolventes, VR
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694556"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR y Azure 305: Funciones y almacenamiento

![Inicio del producto final](images/AzureLabs-Lab5-00.png)

En este curso, aprenderá a crear y usar Azure Functions y almacenar datos con un recurso Azure Storage, dentro de una aplicación de realidad mixta.

*Azure Functions* es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure. Esto proporciona una manera de delegar el trabajo en la nube, en lugar de la aplicación local, que puede tener muchas ventajas. *Azure Functions* admite varios lenguajes de desarrollo,\#como C\#, F, node. js, Java y php. Para obtener más información, visite el [artículo Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).

*Azure Storage* es un servicio en la nube de Microsoft, que permite a los desarrolladores almacenar datos, con el seguro de que estará altamente disponible, seguro, duradero, escalable y redundante. Esto significa que Microsoft administrará todo el mantenimiento y los problemas críticos. Para obtener más información, visite el [artículo Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Una vez finalizado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta que podrá hacer lo siguiente:

1.  Permite al usuario mirarse en una escena.
2.  Desencadenar la generación de objetos cuando el usuario mira en un "botón" 3D.
3.  Los objetos generados serán elegidos por una función de Azure.
4.  A medida que se genera cada objeto, la aplicación almacenará el tipo de objeto en un *archivo de Azure*, que se encuentra en *Azure Storage*.
5.  Tras la carga por segunda vez, los datos del *archivo de Azure* se recuperarán y se usarán para reproducir las acciones de generación de la instancia anterior de la aplicación.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>MR y Azure 305: Funciones y almacenamiento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens.

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
- Una suscripción a una cuenta de Azure para crear recursos de Azure
- Acceso a Internet para la configuración de Azure y la recuperación de datos

## <a name="before-you-start"></a>Antes de comenzar

Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: Azure portal

Para usar el **servicio Azure Storage**, debe crear y configurar una **cuenta de almacenamiento** en el Azure portal.

1.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda, busque la *cuenta de almacenamiento*y haga clic en **entrar**.

    ![búsqueda de Azure Storage](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.

3.  La nueva página proporcionará una descripción del servicio de *cuenta de Azure Storage* . En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.

    ![crear servicio](images/AzureLabs-Lab5-02.png)

4.  Una vez que haya hecho clic en **crear**:

    1.  Inserte un *nombre* para la cuenta. tenga en cuenta que este campo solo acepta números y letras minúsculas.

    2.  En *modelo de implementación*, seleccione **Resource Manager**.

    3.  En *tipo de cuenta*, seleccione **almacenamiento (uso general V1)** .

    4.  Determine la *Ubicación* del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    5.  En *replicación* , seleccione **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .

    6.  En *rendimiento*, seleccione **estándar**.

    7.  Deje la *transferencia segura requerida* como deshabilitada.

    8.  Seleccione una *suscripción*.

    9. Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común). 

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    11. Seleccione **Crear**.

        ![información del servicio de entrada](images/AzureLabs-Lab5-03.png)

5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación en Azure portal](images/AzureLabs-Lab5-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![Ir al recurso](images/AzureLabs-Lab5-05.png)

8.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de servicio de la *cuenta de almacenamiento* .

    ![teclas de acceso](images/AzureLabs-Lab5-06.png)

9.  Haga clic en *claves de acceso*para mostrar los puntos de conexión de este servicio en la nube. Use *el Bloc de notas* o similar para copiar una de las claves para usarla más adelante. Además, tenga en cuenta el valor de la *cadena de conexión* , ya que se usará en la clase *AzureServices* , que se creará más adelante.

    ![copiar cadena de conexión](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capítulo 2: configuración de una función de Azure

Ahora escribirá una **función** de **Azure** en el servicio de Azure.

Puede usar una **función de Azure** para hacer prácticamente todo lo que haría con una función clásica en el código, la diferencia es que cualquier aplicación que tenga credenciales para acceder a la cuenta de Azure puede tener acceso a esta función.

Para crear una función de Azure:

1.  En *Azure portal*, haga clic en **nuevo** en la esquina superior izquierda y busque *function App*y haga clic en **entrar**.

    ![creación de una aplicación de función](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.

2.  La nueva página proporcionará una descripción del servicio *Azure function App* . En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.

    ![información de la aplicación de función](images/AzureLabs-Lab5-09.png)

3.  Una vez que haya hecho clic en **crear**:

    1.  Proporcione un *nombre de aplicación*. Aquí solo se pueden usar letras y números (en mayúsculas o minúsculas).

    2.  Seleccione su *suscripción*preferida.

    3. Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común). 

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Para este ejercicio, seleccione *Windows* como el **sistema operativo**elegido.

    5.  Seleccione *plan de consumo* para el **plan de hospedaje**.

    6.  Determine la *Ubicación* del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones. Para obtener un rendimiento óptimo, seleccione la misma región que la cuenta de almacenamiento.

    7.  En *almacenamiento*, seleccione **usar existente**y, a continuación, use el menú desplegable para buscar el almacenamiento creado anteriormente.

    8.  Deje *Application Insights* desactivado para este ejercicio.

        ![detalles de la aplicación de función de entrada](images/AzureLabs-Lab5-10.png)

4.  Haga clic en el botón **Crear**.

5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación de Azure portal](images/AzureLabs-Lab5-11.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio. 

    ![vaya a la aplicación de función de recursos](images/AzureLabs-Lab5-12.png)

8.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de servicio de *function App* .

9.  En el panel de *function App* , mantenga el mouse sobre *las funciones*, que se encuentran dentro del panel de la izquierda y, a continuación, haga clic en el símbolo **+ (más)** .

    ![crear nueva función](images/AzureLabs-Lab5-13.png)

10. En la página siguiente, asegúrese de que se ha seleccionado **webhook + API** y, para *elegir un idioma,* seleccione **CSharp**, ya que este será el idioma usado para este tutorial. Por último, haga clic en el botón **crear esta función** .

    ![seleccionar CSharp de webhook](images/AzureLabs-Lab5-14.png)

11. Debe ir a la página de códigos (Run. CSX); si no es así, haga clic en la función recién creada en la lista de funciones dentro del panel de la izquierda.

    ![abrir nueva función](images/AzureLabs-Lab5-15.png)

12. Copie el código siguiente en la función. Esta función simplemente devolverá un entero aleatorio entre 0 y 2 cuando se llame a. No se preocupe por el código existente, no dude en pegarlo encima de la parte superior.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Seleccione **Guardar**.

14. El resultado debería ser similar a la imagen siguiente.

15. Haga clic en **obtener la dirección URL** de la función y tome nota del *punto de conexión* mostrado. Tendrá que insertarlo en la clase *AzureServices* que creará más adelante en este curso.

    ![obtener extremo de función](images/AzureLabs-Lab5-16.png)

    ![obtener extremo de función](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3: configuración del proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

Configure y pruebe sus auriculares de la realidad mixta.

> [!NOTE]
> **No** necesitará controladores de movimiento para este curso. Si necesita ayuda para configurar el casco inmersivo, [visite el artículo sobre la](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)configuración de la realidad mixta.

1.  Abra Unity y haga clic en **nuevo**.

    ![crear nuevo proyecto de Unity](images/AzureLabs-Lab5-17.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity. Inserte **MR_Azure_Functions**. Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la *Ubicación* en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![asignar un nombre al nuevo proyecto de Unity](images/AzureLabs-Lab5-18.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**. Vaya a **Editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![establecer Visual Studio como editor de scripts](images/AzureLabs-Lab5-19.png)

4.  A continuación, vaya a**configuración de compilación** de **archivos** > y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .

    ![cambiar la plataforma a UWP](images/AzureLabs-Lab5-20.png)

5.  Vaya a**configuración de compilación** de **archivos** > y asegúrese de que:

    1. El **dispositivo de destino** se establece en **cualquier dispositivo**.

        > Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.

    2. El **tipo de compilación** se establece en **D3D**

    3. **SDK** está establecido en la **versión más reciente instalada**

    4. La **versión de Visual Studio** está establecida en la **más reciente instalada**

    5. **Compilar y ejecutar** está establecido en **equipo local**

    6. Guarde la escena y agréguela a la compilación.

        1.  Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.

            ![agregar escenas abiertas](images/AzureLabs-Lab5-21.png)

        2.  Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre Scenes.

            ![crear carpeta de escenas](images/AzureLabs-Lab5-22.png)

        3.  Abra la carpeta Scenes recién creada y, a continuación, en el campo **nombre de archivo:** , escriba **FunctionsScene**y, a continuación, presione **Guardar**.

            ![escena de Save Functions](images/AzureLabs-Lab5-23.png)

6.  El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.

    ![escena de Save Functions](images/AzureLabs-Lab5-24.png)

7.  En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .

    ![configuración del reproductor en el inspector](images/AzureLabs-Lab5-25.png)

8.  En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  La **versión de scripting en tiempo de ejecución** debe ser **Experimental** (.net 4,6 equivalente), lo que desencadenará una necesidad de reiniciar el editor.
        2.  El **back-end** de scripting debe ser **.net**
        3.  El **nivel de compatibilidad de API** debe ser **.net 4,6**

    2.  En la pestaña **configuración de publicación** , en **capacidades**, seleccione:
        
        -  **InternetClient**

            ![establecer capacidades](images/AzureLabs-Lab5-26.png)

    3.  Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![establecer la configuración de XR](images/AzureLabs-Lab5-27.png)

9.  De nuevo en la *configuración de compilación* , los *proyectos de Unity C#*  ya no están atenuados; Marque la casilla situada junto a este.

    ![proyectos de c# de tick](images/AzureLabs-Lab5-28.png)

10.  Cierre la ventana Configuración de compilación.

11. Guarde la escena y el proyecto (**archivo** > **Guardar escena/archivo** > **Guardar proyecto**).

## <a name="chapter-4---setup-main-camera"></a>Capítulo 4: configuración de la cámara principal

> [!IMPORTANT]
> Si desea omitir los componentes de *configuración de Unity* de este curso y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html). También contendrá los archivos DLL del siguiente capítulo. Después de la importación, continúe en el [capítulo 7](#chapter-7---create-the-azureservices-class). 

1.  En el *Panel jerarquía*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista "principal" una vez que está "dentro" de la aplicación.

2.  Con el panel de Unity delante de usted, seleccione la **cámara principal GameObject**. Observará que el *panel Inspector* (generalmente situado a la derecha, dentro del panel) mostrará los distintos componentes de ese *GameObject*, con la *transformación* en la parte superior, la *cámara*y otros componentes. Tendrá que restablecer la transformación de la cámara principal, de modo que esté colocada correctamente.

3.  Para ello, seleccione el icono de **engranaje** situado junto al componente de *transformación* de la cámara y seleccione **restablecer**.

    ![restablecer transformación](images/AzureLabs-Lab5-29.png)

4.  A continuación, actualice el componente de **transformación** para que tenga el siguiente aspecto:

    |         |    TRANSFORMACIÓN: POSICIÓN   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **SÍ**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMACIÓN-GIRO |       |
    | :---: | :------------------: | :----:|
    | **X** | **SÍ**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMACIÓN DE ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **SÍ**             | **Z** |
    | 1     | 1                 | 1     |

    ![establecer transformación de cámara](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capítulo 5: configuración de la escena de Unity

1.  Haga clic con el botón secundario en un área vacía del *Panel*de jerarquías, en **objeto 3D**, agregar un **plano**.

    ![crear nuevo plano](images/AzureLabs-Lab5-31.png)

2.  Con el objeto de **plano** seleccionado, cambie los siguientes parámetros en el *panel del inspector*:

    |       | TRANSFORMACIÓN: POSICIÓN |       |
    | :---: | :------------------: | :---: |
    | **X** | **SÍ**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMACIÓN DE ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **SÍ**             | **Z** |
    | 10    | 1                 | 10    |

    ![establecer la posición y la escala del plano](images/AzureLabs-Lab5-32.png)

    ![vista de escena de plano](images/AzureLabs-Lab5-33.png)

3.  Haga clic con el botón secundario en un área vacía del *Panel jerarquía*, en **objeto 3D**, agregar un **cubo**.

    1.  Cambie el nombre del cubo a **GazeButton** (con el cubo seleccionado, presione ' F2 ').

    2.  Cambie los parámetros siguientes en el *panel Inspector*:

        |       | TRANSFORMACIÓN: POSICIÓN |       |
        | :---: | :------------------: |:-----:|
        | **X** | **SÍ**                | **Z** |
        | 0     | 3                    | 5     |


        ![establecer transformación de botón de mira](images/AzureLabs-Lab5-34.png)

        ![vista de escena de botón de mira](images/AzureLabs-Lab5-35.png)

    3.  Haga clic en el botón desplegable **etiqueta** y haga clic en **Agregar etiqueta** para abrir el *panel Etiquetas & capas*.

        ![Agregar nueva etiqueta](images/AzureLabs-Lab5-36.png)

        ![seleccionar más](images/AzureLabs-Lab5-37.png)

    4.  Seleccione el botón **+ (más)** y, en el campo *nuevo nombre de etiqueta* , escriba **GazeButton**y presione **Guardar**.

        ![nombre nueva etiqueta](images/AzureLabs-Lab5-38.png)

    5.  Haga clic en el objeto **GazeButton** en el *Panel jerarquía*y, en el *panel Inspector*, asigne la etiqueta **GazeButton** recién creada.

        ![asignar botón de mira la nueva etiqueta](images/AzureLabs-Lab5-39.png)

4.  Haga clic con el botón derecho en el objeto **GazeButton** , en el *Panel jerarquía*, y agregue un **GameObject vacío** (que se agregará como un objeto *secundario* ).

5.  Seleccione el nuevo objeto y cambie su nombre a **ShapeSpawnPoint**.

    1.  Cambie los parámetros siguientes en el *panel Inspector*:

        |       | TRANSFORMACIÓN: POSICIÓN |       |
        | :---: | :------------------: |:----: |
        | **X** |**SÍ**                 | **Z** |
        | 0     | -1                   | 0     |

        ![transformación actualizar punto de generación de forma](images/AzureLabs-Lab5-40.png)

        ![vista de escena de punto de generación de formas](images/AzureLabs-Lab5-41.png)

6.  A continuación, creará un objeto de **texto 3D** para proporcionar comentarios sobre el estado del servicio de Azure.

    Vuelva a hacer clic con el botón derecho en **GazeButton** en el panel jerarquía y agregue un objeto **3D** > de**texto 3D** de objeto como *elemento secundario*.

    ![crear nuevo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  Cambie el nombre del objeto de **texto 3D** a **AzureStatusText**.

8.  Cambie la transformación del objeto **AzureStatusText** de la siguiente manera:

    |       | TRANSFORMACIÓN: POSICIÓN |       |
    | :---: | :------------------: | :---: |
    | **X** | **SÍ**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRANSFORMACIÓN DE ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **SÍ**             | **Z** |
    | 0,1   | 0,1               | 0,1   |


    > [!NOTE]
    > No se preocupe si parece estar fuera del centro, ya que se solucionará cuando se actualice el componente de malla de texto siguiente.

9.  Cambie el componente de **malla de texto** para que coincida con el siguiente:

    ![establecer componente de malla de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > El color seleccionado aquí es color Hex: **000000FF**, sin embargo, no dude en elegir el suyo propio, solo tiene que asegurarse de que es legible.

10. La estructura del panel de jerarquías debería tener ahora el siguiente aspecto:

    ![malla de texto en la vista de escenas](images/AzureLabs-Lab5-43b.png)

10. La escena debe tener ahora el siguiente aspecto:

    ![malla de texto en la vista de escenas](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capítulo 6: importar Azure Storage para Unity

Usará Azure Storage para Unity (que a su vez usa el SDK de .net para Azure). Puede leer más sobre esto en el [artículo Azure Storage para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado el [". unitypackage Tools" más reciente de github](https://aka.ms/azstorage-unitysdk). A continuación, haga lo siguiente:

1.  Agregue el **archivo. unitypackage Tools** a Unity mediante la opción de menú de**paquete personalizado** de**importación** > de **recursos** > .

2.  En el cuadro **importar paquete Unity** que aparece, puede seleccionar todo en**almacenamiento**de **Complementos** > . Desactive todo lo demás, ya que no es necesario para este curso.

    ![importar a paquete](images/AzureLabs-Lab5-45.png)

3.  Haga clic en el botón **importar** para agregar los elementos al proyecto.

4.  Vaya a la carpeta *Storage* en *Complementos*, en la vista proyecto, y seleccione *solo*los siguientes complementos:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft.Json
    -   System. espacial

        ![desactive cualquier plataforma](images/AzureLabs-Lab5-46.png)

5.  Con *estos complementos específicos* seleccionados, **desactive** *cualquier plataforma* y **desactive** *WSAPlayer* y haga clic en **aplicar**.

    ![aplicar dll de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Estamos marcando estos complementos concretos para usarlos solo en el editor de Unity. Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.

6.  En la carpeta del complemento de *almacenamiento* , seleccione solo:

    -   Microsoft. Data. Services. Client

        ![establecer no procesar para archivos dll](images/AzureLabs-Lab5-48.png)

7.  Active la casilla **no procesar** en *configuración de plataforma* y haga clic en **aplicar**.

    ![no aplicar procesamiento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Estamos marcando este complemento como "no procesar" porque el parche de ensamblado de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se haya procesado.

## <a name="chapter-7---create-the-azureservices-class"></a>Capítulo 7: creación de la clase AzureServices

La primera clase que va a crear es la clase *AzureServices* .

La clase *AzureServices* se encargará de:

-   Almacenamiento de las credenciales de la cuenta de Azure.

-   Llamar a la función App de Azure.

-   La carga y descarga del archivo de datos en el almacenamiento en la nube de Azure.

Para crear esta clase:

1.  Haga clic con el botón derecho en la carpeta de *recursos* , que se encuentra en el panel Proyecto, **crear** > **carpeta**. Asigne a la carpeta el nombre scripts.

    ![crear nueva carpeta](images/AzureLabs-Lab5-50.png)

    ![carpeta de llamadas: scripts](images/AzureLabs-Lab5-51.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla.

3.  Haga clic con el botón derecho dentro de la carpeta, **crear**  >   **C# script**. Llame al script *AzureServices*.

4.  Haga doble clic en la nueva clase *AzureServices* para abrirla con *Visual Studio*.

5.  Agregue los siguientes espacios de nombres en la parte superior de *AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Agregue los siguientes campos de inspector dentro de la clase *AzureServices* :

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  A continuación, agregue las siguientes variables de miembro dentro de la clase *AzureServices* :

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Asegúrese de reemplazar los valores de *punto* de conexión y de *cadena de conexión* con los valores de Azure Storage, que se encuentran en Azure portal.

8.  Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* . Se llamará a estos métodos cuando se inicialice la clase:

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > En un [capítulo futuro](#chapter-10---completing-the-azureservices-class), rellenaremos el código para *CallAzureFunctionForNextShape ()* .

9.  Elimine el método *Update ()* , ya que esta clase no lo usará.

10. Guarde los cambios en Visual Studio y vuelva a Unity.

11. Haga clic y arrastre la clase *AzureServices* desde la carpeta scripts hasta el objeto cámara principal en el *Panel jerarquía*.

12. Seleccione la cámara principal, después arrastre el objeto secundario **AzureStatusText** de debajo del objeto **GazeButton** y colóquelo en el campo destino de referencia **AzureStatusText** , en el *Inspector*, para proporcionar la referencia al  *Script AzureServices* .

    ![asignar destino de referencia de texto de estado de Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capítulo 8: creación de la clase ShapeFactory

El siguiente script que se va a crear es la clase *ShapeFactory* . El rol de esta clase es crear una nueva forma, cuando se solicita, y mantener un historial de las formas creadas en una *lista de historial de formas*. Cada vez que se crea una forma, se actualiza la *lista de historial de formas* en la clase *AzureService* y, a continuación, se almacena en el *Azure Storage*. Cuando se inicia la aplicación, si se encuentra un archivo almacenado en el *Azure Storage*, se recupera y se vuelve a reproducir la *lista de historial de formas* , con el objeto de **texto 3D** que proporciona si la forma generada es de almacenamiento o nueva.

Para crear esta clase:

1.  Vaya a la  carpeta scripts que creó anteriormente.

2.  Haga clic con el botón derecho dentro de la carpeta, **crear**  >   **C# script**. Llame al script *ShapeFactory*.

3.  Haga doble clic en el nuevo script *ShapeFactory* para abrirlo con *Visual Studio*.

4.  Asegúrese de que la clase *ShapeFactory* incluye los siguientes espacios de nombres:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Agregue las variables que se muestran a continuación a la clase *ShapeFactory* y reemplace las funciones *Start ()* y Activate *()* con las siguientes:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  El método *CreateShape ()* genera las formas primitivas, basándose en el parámetro de *entero* proporcionado. El parámetro booleano se usa para especificar si la forma creada actualmente es de almacenamiento o nueva. Coloque el código siguiente en la clase *ShapeFactory* , debajo de los métodos anteriores:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.

8.  De nuevo en el editor de Unity, haga clic y arrastre la clase *ShapeFactory* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*.

9. Con la cámara principal seleccionada, observará que en el componente de script *ShapeFactory* falta la referencia de *punto de generación* . Para corregirlo, arrastre el objeto **ShapeSpawnPoint** desde el *Panel jerarquía* hasta el destino de referencia de **punto de generación** .

    ![establecer destino de referencia de generador de formas](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capítulo 9: creación de la clase fijamente

El último script que necesita crear es la clase *mira* .

Esta clase es responsable de crear un **Raycast** que se proyectará hacia delante desde la cámara principal, para detectar qué objeto está examinando el usuario. En este caso, Raycast deberá identificar si el usuario mira el objeto **GazeButton** en la escena y desencadena un comportamiento.

Para crear esta clase:

1.  Vaya a la  carpeta scripts que creó anteriormente.

2.  Haga clic con el botón derecho en el panel Proyecto, **crear**  >   **C# script**. Llame al script *fijamente*.

3.  Haga doble clic en el  nuevo script de miraciones para abrirlo con *Visual Studio.*

4.  Asegúrese de que el siguiente espacio de nombres se incluye en la parte superior del script:

    ```csharp
        using UnityEngine;
    ```

5.  Después, agregue las siguientes variables dentro  de la clase mirate:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Algunas de estas variables se podrán editar en el *Editor*.

6.  Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* .

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Agregue el código siguiente, que creará un objeto cursor en el inicio, junto con el método *Update ()* , que ejecutará el método Raycast, junto con el lugar donde se alterna el valor booleano GazeEnabled:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. A continuación, agregue el método *UpdateRaycast ()* , que proyectará un Raycast y detectará el destino de la visita.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Por último, agregue el método *ResetFocusedObject ()* , que cambiará el color actual de los objetos GazeButton, lo que indicará si está creando una nueva forma o no.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Guarde los cambios en Visual Studio antes de volver a Unity.

11.  Haga clic y arrastre la clase *mira* desde la carpeta scripts hasta el objeto **cámara principal** en el *Panel jerarquía*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capítulo 10: completar la clase AzureServices

Con los demás scripts en su lugar, ahora es posible *completar* la clase *AzureServices* . Esto se logra mediante:

1.  Agregar un nuevo método denominado *CreateCloudIdentityAsync ()* para configurar las variables de autenticación necesarias para comunicarse con Azure.

    > Este método también comprobará la existencia de un archivo previamente almacenado que contenga la lista de formas.
    >
    > **Si se encuentra el archivo**, se deshabilitará el *usuario y*se desencadenará la creación de la forma, según el patrón de formas, tal como se almacena en el **archivo de Azure Storage**. El usuario puede ver esto, ya que la **malla de texto** proporcionará la pantalla "almacenamiento" o "nuevo", según el origen de las formas.
    >
    > **Si no se encuentra ningún archivo**, se habilitará la *mirada*, lo que permite al usuario crear formas al mirar el objeto **GazeButton** de la escena.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  El siguiente fragmento de código se encuentra dentro del método *Start ()* ; donde se realizará una llamada al método *CreateCloudIdentityAsync ()* . No dude en copiar sobre el método *Start ()* actual, con lo siguiente:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Rellene el código para el método *CallAzureFunctionForNextShape ()* . Usará el *function App de Azure* creado anteriormente para solicitar un índice de forma. Una vez recibida la nueva forma, este método enviará la forma a la clase *ShapeFactory* para crear la nueva forma en la escena. Use el código siguiente para completar el cuerpo de *CallAzureFunctionForNextShape ()* .

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Agregue un método para crear una cadena mediante la concatenación de los enteros almacenados en la lista de historial de formas y guárdelo en el *archivo de Azure Storage*.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Agregue un método para recuperar el texto almacenado en el archivo que se encuentra en el *archivo de Azure Storage* y deserializarlo en una lista.

6.  Una vez completado este proceso, el método vuelve a habilitar la mirada para que el usuario pueda agregar más formas a la escena.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Guarde los cambios en Visual Studio antes de volver a Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Capítulo 11: compilar la solución UWP

Para comenzar el proceso de compilación:

1.  Vaya a **archivos** > **configuración de compilación**.

    ![compilar la aplicación](images/AzureLabs-Lab5-54.png)

2.  Haz clic en **Compilación**. Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y asígnele el nombre *App*. Después, con la carpeta de la *aplicación* seleccionada, presione **Seleccionar carpeta**.

3.  Unity comenzará a compilar el proyecto en la carpeta de la *aplicación* .

4.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del *Explorador de archivos* en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-12---deploying-your-application"></a>Capítulo 12: implementación de la aplicación

Para implementar la aplicación:

1.  Navegue hasta la carpeta de la *aplicación* que se creó en el [último capítulo](#chapter-11---build-the-uwp-solution). Verá un archivo con el nombre de la aplicación, con la extensión '. sln ', en la que debe hacer doble clic para abrirlo en *Visual Studio*.

2.  En la **plataforma**de la solución, seleccione **x86, equipo local**.

3.  En la **configuración de soluciones** , seleccione Depurar.

    > En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP** de HoloLens, que se encuentra en la red de **configuración** > &**Opciones avanzadas**de**Wi-Fi** > de**Internet** > ; la IPv4 es la dirección que debe usar. 
    > - Asegurarse de que el **modo de desarrollador** está **activado**; se encuentra en **configuración** > **Actualizar & seguridad** > **para los desarrolladores**.

    ![implementar solución](images/AzureLabs-Lab5-55.png)

4.  Vaya al menú  compilar y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.

5.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse y probarse.

## <a name="your-finished-azure-functions-and-storage-application"></a>La aplicación de almacenamiento y Azure Functions finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha los servicios Azure Functions y Azure Storage. La aplicación podrá dibujar en datos almacenados y proporcionar una acción basada en esos datos.

![final del producto final](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

Cree un segundo punto de generación y grabe el punto de generación a partir del que se creó un objeto. Al cargar el archivo de datos, reproduzca las formas que se van a generar desde la ubicación en la que se crearon originalmente.

### <a name="exercise-2"></a>Ejercicio 2

Cree una manera de reiniciar la aplicación, en lugar de tener que volver a abrirla cada vez. La **carga de escenas** es un buen punto de partida. Después de hacerlo, cree una manera de borrar la lista almacenada en *Azure Storage*, para que se pueda restablecer fácilmente desde la aplicación. 
