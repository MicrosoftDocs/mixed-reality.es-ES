---
title: El Sr. y Azure 305 - funciones y almacenamiento
description: Realice este curso para obtener información sobre cómo implementar el almacenamiento de Azure y las funciones dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, funciones, almacenamiento, hololens, vr envolvente,
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694556"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>El Sr. y Azure 305: Funciones y almacenamiento

![final producto-inicio](images/AzureLabs-Lab5-00.png)

En este curso, obtendrá información sobre cómo crear y usar Azure Functions y almacenar los datos con un recurso de almacenamiento de Azure, dentro de una aplicación de realidad mixta.

*Las funciones de Azure* es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure. Esto proporciona una manera para delegar el trabajo a la nube, en lugar de la aplicación local, lo que puede tener muchas ventajas. *Las funciones de Azure* admite varios lenguajes de desarrollo, incluidos C\#, F\#, Node.js, Java y PHP. Para obtener más información, visite la [artículo de Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).

*Almacenamiento de Azure* es un servicio de nube de Microsoft, lo que permite a los desarrolladores almacenar datos, con el seguro que será altamente disponible, seguro, duradero, escalable y redundante. Esto significa que Microsoft controlará todas mantenimiento y los problemas críticos por usted. Para obtener más información, visite la [artículo de Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Una vez completado este curso, tendrá una aplicación de envolventes auriculares de realidad mixta que podrá hacer lo siguiente:

1.  Permitir que el usuario que mirar en torno a una escena.
2.  Desencadenar la creación de objetos cuando el usuario gazes en 3D "button".
3.  Elegirá los objetos generados por una función de Azure.
4.  Como cada objeto se genera, la aplicación almacenará el tipo de objeto en un *Azure File*, que se encuentra en *Azure Storage*.
5.  Al cargar una segunda vez, el *Azure File* datos se recuperan y se usa para reproducir las acciones de generación de la instancia anterior de la aplicación.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar su aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>El Sr. y Azure 305: Funciones y almacenamiento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens. Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens.

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
- Una suscripción a una cuenta de Azure para crear recursos de Azure
- Acceso a Internet para la recuperación de datos e instalación de Azure

## <a name="before-you-start"></a>Antes de empezar

Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: el Portal de Azure

Para usar el **servicio Azure Storage**, deberá crear y configurar un **cuenta de almacenamiento** en Azure portal.

1.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *cuenta de almacenamiento*y haga clic en **ENTRAR**.

    ![búsqueda de almacenamiento de Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.

3.  La nueva página proporcionará una descripción de la *cuenta de Azure Storage* service. En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.

    ![Crear servicio](images/AzureLabs-Lab5-02.png)

4.  Una vez que ha hecho clic **crear**:

    1.  Insertar un *nombre* para su cuenta, tenga en cuenta este campo sólo acepta números y letras minúsculas.

    2.  Para *modelo de implementación*, seleccione **Administrador de recursos**.

    3.  Para *tipo de cuenta*, seleccione **almacenamiento (uso general v1)** .

    4.  Determinar la *ubicación* para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    5.  Para *replicación* seleccione **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)** .

    6.  Para *rendimiento*, seleccione **estándar**.

    7.  Deje *se requiere transferencia segura* como **deshabilitado**.

    8.  Seleccione un *suscripción*.

    9. Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes). 

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    11. Selecciona **Crear**.

        ![información de entrada de servicio](images/AzureLabs-Lab5-03.png)

5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación en azure portal](images/AzureLabs-Lab5-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![Ir al recurso](images/AzureLabs-Lab5-05.png)

8.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva *cuenta de almacenamiento* instancia de servicio.

    ![teclas de acceso](images/AzureLabs-Lab5-06.png)

9.  Haga clic en *claves de acceso*para revelar los puntos de conexión para este servicio en la nube. Usar *el Bloc de notas* o similar, para copiar una de las claves para su uso posterior. Además, tenga en cuenta la *cadena de conexión* valor, tal como se usará en el *AzureServices* (clase), que creará más adelante.

    ![Copie la cadena de conexión](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capítulo 2: configurar una función de Azure

Ahora escribirá un **Azure** **función** en el servicio de Azure.

Puede usar un **Azure Function** para casi todo lo que haría con una función clásica en el código, la diferencia es que cualquier aplicación que disponga de credenciales para tener acceso a su cuenta de Azure puede tener acceso a esta función hacer.

Para crear una función de Azure:

1.  Desde su *Portal de Azure*, haga clic en **New** en la esquina superior izquierda esquina y busque *Function App*y haga clic en **ENTRAR**.

    ![Crear aplicación de función](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.

2.  La nueva página proporcionará una descripción de la *Azure Function App* service. En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.

    ![información de la aplicación de función](images/AzureLabs-Lab5-09.png)

3.  Una vez que ha hecho clic **crear**:

    1.  Proporcione un *nombre de la aplicación*. Solo letras y números se pueden emplear (ya sea en mayúsculas o minúsculas se permite).

    2.  Seleccione la *suscripción*.

    3. Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes). 

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Para este ejercicio, seleccione *Windows* como los elegidos **OS**.

    5.  Seleccione *Plan de consumo* para el **Plan de hospedaje**.

    6.  Determinar la *ubicación* para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones. Para obtener un rendimiento óptimo, seleccione la misma región que la cuenta de almacenamiento.

    7.  Para *almacenamiento*, seleccione **usar existente**, y, a continuación, mediante el menú desplegable, encontrar el almacenamiento creado anteriormente.

    8.  Deje *Application Insights* desactivado para este ejercicio.

        ![detalles de la aplicación de función de entrada](images/AzureLabs-Lab5-10.png)

4.  Haga clic en el botón **Crear**.

5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación en azure portal](images/AzureLabs-Lab5-11.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio. 

    ![Vaya a la aplicación de función de recursos](images/AzureLabs-Lab5-12.png)

8.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva *Function App* instancia de servicio.

9.  En el *Function App* panel, mantenga el mouse sobre *funciones*, se encuentra en el panel de la izquierda y, a continuación, haga clic en el **+ (signo más)** símbolos.

    ![Crear una nueva función](images/AzureLabs-Lab5-13.png)

10. En la página siguiente, asegúrese de **Webhook y API** está seleccionada y para *elegir un idioma,* seleccione **CSharp**, ya que será el idioma utilizado para este tutorial. Por último, haga clic en el **crear esta función** botón.

    ![Seleccione web gancho csharp](images/AzureLabs-Lab5-14.png)

11. Debería ir al código de página (run.csx), si no, haga clic en la función recién creada en la lista de funciones dentro del panel de la izquierda.

    ![Abra la nueva función](images/AzureLabs-Lab5-15.png)

12. Copie el código siguiente en la función. Esta función simplemente devolverá un entero aleatorio entre 0 y 2, cuando se llama. No preocuparse por el código existente, no dude en pegue encima de él.

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

13. Selecciona **Guardar**.

14. El resultado debería parecerse a la imagen siguiente.

15. Haga clic en **obtener la dirección URL de función** y tome nota de la *extremo* muestra. Debe insertar en el *AzureServices* clase que creará más adelante en este curso.

    ![obtener punto de conexión de función](images/AzureLabs-Lab5-16.png)

    ![obtener punto de conexión de función](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

Configurar y probar los auriculares de realidad mixta envolventes.

> [!NOTE]
> Podrá **no** requieren controladores de movimiento de este curso. Si necesita admite la configuración de los auriculares envolventes, [visite la realidad mixta configurar artículo](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra Unity y haga clic en **New**.

    ![Crear nuevo proyecto de unity](images/AzureLabs-Lab5-17.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Insertar **MR_Azure_Functions**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establecer el *ubicación* a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Asigne un nombre nuevo proyecto de unity](images/AzureLabs-Lab5-18.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **editar** > **preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![conjunto de visual studio como editor de script](images/AzureLabs-Lab5-19.png)

4.  A continuación, vaya a **archivo** > **configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma**  botón.

    ![cambiar la plataforma a uwp](images/AzureLabs-Lab5-20.png)

5.  Vaya a **archivo** > **configuración de compilación** y asegúrese de que:

    1. **Dispositivo de destino** está establecido en **cualquier dispositivo**.

        > Para Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.

    2. **Tipo de compilación** está establecido en **D3D**

    3. **SDK** está establecido en **instalada más reciente**

    4. **Versión de Visual Studio** está establecido en **instalada más reciente**

    5. **Compilar y ejecutar** está establecido en **máquina Local**

    6. Guarde la escena y agregarlo a la compilación.

        1.  Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![Agregar escenas abiertos](images/AzureLabs-Lab5-21.png)

        2.  Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![Crear carpeta de segundo plano](images/AzureLabs-Lab5-22.png)

        3.  Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo:** campo de texto, escriba **FunctionsScene**, a continuación, presione **guardar**.

            ![Guardar escena de funciones](images/AzureLabs-Lab5-23.png)

6.  El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.

    ![Guardar escena de funciones](images/AzureLabs-Lab5-24.png)

7.  En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.

    ![configuración del Reproductor en inspector](images/AzureLabs-Lab5-25.png)

8.  En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental** (.NET 4.6 equivalente), que desencadenará una necesidad de reiniciar el Editor.
        2.  **Scripting de back-end** debe ser **.NET**
        3.  **Nivel de compatibilidad de API** debe ser **.NET 4.6**

    2.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:
        
        -  **InternetClient**

            ![conjunto de capacidades](images/AzureLabs-Lab5-26.png)

    3.  Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **Windows Mixed Reality SDK** se agrega.

        ![configuración del conjunto de XR](images/AzureLabs-Lab5-27.png)

9.  En *configuración de compilación* *Unity C# proyectos* ya no está atenuada; Marque la casilla situada junto a esto.

    ![proyectos de c# graduación](images/AzureLabs-Lab5-28.png)

10.  Cierre la ventana de configuración de compilación.

11. Guarde la escena y el proyecto (**archivo** > **guardar ESCENA / archivo** > **Guardar proyecto**).

## <a name="chapter-4---setup-main-camera"></a>Capítulo 4: configuración de cámara principal

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componentes de este curso y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo en el proyecto como un [personalizado Paquete](https://docs.unity3d.com/Manual/AssetPackages.html). Esto también contendrá los archivos DLL en el capítulo siguiente. Después de la importación, continuar desde [capítulo 7](#chapter-7---create-the-azureservices-class). 

1.  En el *jerarquía Panel*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista de "head" una vez que esté "dentro" de la aplicación.

2.  Con el panel de Unity delante de usted, seleccione el **Main cámara GameObject**. Observará que el *Panel Inspector* (generalmente se encuentra a la derecha, en el panel) mostrará los distintos componentes de la que *GameObject*, con *transformar* en la parte superior, seguido por *cámara*y algunos otros componentes. Deberá restablecer la transformación de la cámara principal, por lo que está colocado correctamente.

3.  Para ello, seleccione el **engranaje** icono situado junto a la cámara *transformar* componente y, a continuación, seleccione **restablecer**.

    ![Restablecer transformación](images/AzureLabs-Lab5-29.png)

4.  A continuación, actualice el **transformar** componente tenga el siguiente aspecto:

    |         |    TRANSFORMACIÓN - POSICIÓN   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | -TRANSFORMACIÓN DE GIRO |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMACIÓN - ESCALADO |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![conjunto de transformación de cámara](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capítulo 5: configuración de la escena de Unity

1.  Haga clic en un área vacía de la *jerarquía Panel*, en **objeto 3D**, agregue un **plano**.

    ![Crear nuevo plano](images/AzureLabs-Lab5-31.png)

2.  Con el **plano** objeto seleccionado, cambie los parámetros siguientes en el *Panel Inspector*:

    |       | TRANSFORMACIÓN - POSICIÓN |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMACIÓN - ESCALADO |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![posición del conjunto plano y la escala](images/AzureLabs-Lab5-32.png)

    ![vista de la escena del plano](images/AzureLabs-Lab5-33.png)

3.  Haga clic en un área vacía de la *jerarquía Panel*, en **objeto 3D**, agregue un **cubo**.

    1.  Cambiar el nombre del cubo a **GazeButton** (con el cubo seleccionado, pulse 'F2').

    2.  Cambiar los parámetros siguientes en el *Panel Inspector*:

        |       | TRANSFORMACIÓN - POSICIÓN |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![conjunto mirada botón transformación](images/AzureLabs-Lab5-34.png)

        ![vista de escena de botón que mirar](images/AzureLabs-Lab5-35.png)

    3.  Haga clic en el **etiqueta** botón desplegable y haga clic en **Agregar etiqueta** para abrir el *etiquetas & panel Capas*.

        ![Agregar nueva etiqueta](images/AzureLabs-Lab5-36.png)

        ![Seleccione más](images/AzureLabs-Lab5-37.png)

    4.  Seleccione el **+ (signo más)** botón y en el *nuevo nombre de la etiqueta* , introduzca **GazeButton**y presione **guardar**.

        ![nueva etiqueta de nombre](images/AzureLabs-Lab5-38.png)

    5.  Haga clic en el **GazeButton** objeto en el *jerarquía Panel*y en el *Panel Inspector*, asignar recién creado **GazeButton** etiqueta.

        ![mirada botón asignar la nueva etiqueta](images/AzureLabs-Lab5-39.png)

4.  Haga doble clic en el **GazeButton** objeto, en el *jerarquía Panel*y agregue un **GameObject vacío** (que se agregará como un *secundarios* objeto).

5.  Seleccione el nuevo objeto y cámbielo por **ShapeSpawnPoint**.

    1.  Cambiar los parámetros siguientes en el *Panel Inspector*:

        |       | TRANSFORMACIÓN - POSICIÓN |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![transformación de punto de actualización de forma spawn](images/AzureLabs-Lab5-40.png)

        ![vista de escena de forma spawn punto](images/AzureLabs-Lab5-41.png)

6.  A continuación creará un **texto 3D** objeto para proporcionar comentarios sobre el estado del servicio de Azure.

    Haga clic con el botón derecho en el **GazeButton** en la jerarquía del nuevo Panel y agregar un **objeto 3D** > **texto 3D** objeto como un *secundarios*.

    ![Crear nuevo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  Cambiar el nombre de la **texto 3D** objeto **AzureStatusText**.

8.  Cambiar el **AzureStatusText** objeto transformación como sigue:

    |       | TRANSFORMACIÓN - POSICIÓN |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | TRANSFORMACIÓN - ESCALADO |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > No se preocupe si parece estar fuera del centro, como esto se corregirá cuando el debajo del texto de la malla se actualiza el componente.

9.  Cambiar el **texto de la malla** componente para que coincida con el a continuación:

    ![componente de malla de conjunto de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > Aquí, el color seleccionado es de color hexadecimal: **000000FF**, aunque no dude en Elija su propio, solo tiene que comprobar es legible.

10. La estructura del Panel de la jerarquía debe ser ahora similar al siguiente:

    ![texto de la malla en la vista de escena](images/AzureLabs-Lab5-43b.png)

10. La escena ahora un aspecto similar al siguiente:

    ![texto de la malla en la vista de escena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capítulo 6: importar el almacenamiento de Azure para Unity

Va a usar Azure Storage para Unity (que a su vez aprovecha el .net SDK de Azure). Puede leer más sobre esto en el [el almacenamiento de Azure para el artículo de Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación. Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente ['.unitypackage' desde GitHub](https://aka.ms/azstorage-unitysdk). A continuación, haga lo siguiente:

1.  Agregar el **.unitypackage** a Unity de un archivo utilizando el **activos** > **Importar paquete** > **paquete personalizado**opción de menú.

2.  En el **Importar paquete de Unity** cuadro que aparece, puede seleccionar todo el contenido **complemento** > **almacenamiento**. Desactive todo lo demás, ya no es necesaria para este curso.

    ![Importar paquete](images/AzureLabs-Lab5-45.png)

3.  Haga clic en el **importación** para agregar los elementos al proyecto.

4.  Vaya a la *almacenamiento* carpeta bajo *complementos*, en la vista del proyecto y seleccione los siguientes complementos *sólo*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![Desactive cualquier plataforma](images/AzureLabs-Lab5-46.png)

5.  Con *estos complementos específicos* seleccionado, **desactive** *cualquier plataforma* y **desactive** *WSAPlayer* a continuación, haga clic en **aplicar**.

    ![se aplican a archivos DLL de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Vamos a marcar estos complementos determinados para su uso en el Editor de Unity. Esto es porque hay diferentes versiones de los complementos mismos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.

6.  En el *almacenamiento* carpeta de complemento, solo seleccione:

    -   Microsoft.Data.Services.Client

        ![No procesar conjunto para archivos DLL](images/AzureLabs-Lab5-48.png)

7.  Compruebe el **proceso no** cuadro bajo *configuración de plataforma* y haga clic en **aplicar**.

    ![no aplicar ningún procesamiento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Vamos a marcar este complemento "No procesar" porque la revisión del ensamblado de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se ha procesado.

## <a name="chapter-7---create-the-azureservices-class"></a>Capítulo 7: crear la clase AzureServices

Es la primera clase que se va a crear el *AzureServices* clase.

El *AzureServices* clase será responsable de:

-   Almacenar las credenciales de cuenta de Azure.

-   Una llamada a la función de la aplicación de Azure.

-   La carga y descarga del archivo de datos en la nube de Azure Storage.

Para crear esta clase:

1.  Haga clic en el *activos* carpeta, que se encuentra en el Panel de proyecto **crear** > **carpeta**. Nombre de la carpeta **Scripts**.

    ![Crear nueva carpeta](images/AzureLabs-Lab5-50.png)

    ![Llame a la carpeta - secuencias de comandos](images/AzureLabs-Lab5-51.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirlo.

3.  Haga clic en la carpeta, **crear**  >   **C# Script**. Llame al script *AzureServices*.

4.  Haga doble clic en el nuevo *AzureServices* clase para abrirlo con *Visual Studio*.

5.  Agregue los siguientes espacios de nombres al principio de la *AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Agregue los siguientes campos de Inspector dentro de la *AzureServices* clase:

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

7.  A continuación, agregue las siguientes variables de miembro dentro de la *AzureServices* clase:

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
    > Asegúrese de reemplazar el *extremo* y *cadena de conexión* valores con los valores de almacenamiento de Azure, se encuentran en el Portal de Azure

8.  El código para *Awake()* y *Start()* métodos ahora debe agregarse. Estos métodos se llamará cuando se inicializa la clase:

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
    > Se rellenará en el código de *CallAzureFunctionForNextShape()* en un [capítulo futuras](#chapter-10---completing-the-azureservices-class).

9.  Eliminar el *Update()* método puesto que esta clase no lo usará.

10. Guarde los cambios en Visual Studio y, a continuación, volver a Unity.

11. Haga clic y arrastre el *AzureServices* clase a partir de la carpeta Scripts en el objeto de cámara principal en el *jerarquía Panel*.

12. Seleccione la cámara principal, a continuación, tomar el **AzureStatusText** objeto secundario debajo de la **GazeButton** objeto y colóquelo dentro de la **AzureStatusText** un destino de referencia campo en el *Inspector*, para proporcionar la referencia a la *AzureServices* secuencia de comandos.

    ![Asigne el destino de referencia de texto de estado de azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capítulo 8: crear la clase ShapeFactory

El script siguiente para crear, es el *ShapeFactory* clase. El rol de esta clase es crear una nueva forma, cuando se solicita y mantener un historial de las formas que creó en un *lista del historial de forma*. Cada vez que se crea una forma, el *lista del historial de forma* se actualiza en el *AzureService* clase y, a continuación, se almacenan en su *Azure Storage*. Cuando se inicia la aplicación, si se encuentra un archivo almacenado en su *Azure Storage*, *lista del historial de forma* se recupera y reproduce, con el **texto 3D** que proporciona el objeto Si la forma generada es de almacenamiento o nuevo.

Para crear esta clase:

1.  Vaya a la **Scripts** carpeta que creó anteriormente.

2.  Haga clic en la carpeta, **crear**  >   **C# Script**. Llame al script *ShapeFactory*.

3.  Haga doble clic en el nuevo *ShapeFactory* script para abrirlo con *Visual Studio*.

4.  Asegúrese del *ShapeFactory* clase incluye los espacios de nombres siguientes:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Agregue las variables que se muestra a continuación para el *ShapeFactory* clase y reemplazar el *Start()* y *Awake()* funciones con los siguientes:

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

6.  El *CreateShape()* método genera las formas de primitivas, según el proporcionado *entero* parámetro. El parámetro booleano se utiliza para especificar si es la forma actualmente creada desde el almacenamiento nuevo. Coloque el código siguiente en su *ShapeFactory* (clase), a continuación de los métodos anteriores:

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

8.  Atrás en el Editor de Unity, haga clic y arrastre el *ShapeFactory* clase desde el **Scripts** carpeta a la **cámara principal** objeto en el *jerarquía Panel*.

9. Con la cámara principal seleccionado, observará el *ShapeFactory* falta un componente de script el *punto Spawn* referencia. Para corregirlo, arrastre el **ShapeSpawnPoint** objeto desde el *jerarquía Panel* a la **Spawn punto** un destino de referencia.

    ![destino de la referencia de conjunto de forma factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capítulo 9: crear la clase de mirada

Es el último script, deberá crear el *que mirar* clase.

Esta clase es responsable de crear un **Raycast** que se proyectará hacia delante de la cámara principal, para detectar el objeto que está mirando el usuario. En este caso, necesitará el Raycast identificar si el usuario está viendo la **GazeButton** de objetos de la escena y desencadenar un comportamiento.

Para crear esta clase:

1.  Vaya a la **Scripts** carpeta que creó anteriormente.

2.  Haga clic en el Panel proyecto, **crear**  >   **C# Script**. Llame al script *que mirar*.

3.  Haga doble clic en el nuevo *que mirar* script para abrirlo con *Visual Studio.*

4.  Asegúrese de que el espacio de nombres siguiente se incluye en la parte superior de la secuencia de comandos:

    ```csharp
        using UnityEngine;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *que mirar* clase:

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
> Algunas de estas variables podrán modificarse en el *Editor*.

6.  El código para el *Awake()* y *Start()* métodos ahora debe agregarse.

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

7.  Agregue el código siguiente, que se creará un objeto de cursor al iniciarse, junto con el *Update()* método, que se ejecutará el método Raycast, junto con que se va a donde se alterna el valor booleano GazeEnabled:

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

8. A continuación agregue el *UpdateRaycast()* método, lo que un Raycast del proyecto y detectar el posicionamiento de destino.

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

9. Por último, agregue el *ResetFocusedObject()* método, que cambiará el GazeButton objetos color actual, que indica si se está creando una nueva forma o no.

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

11.  Haga clic y arrastre el *que mirar* clase a partir de la carpeta Scripts para la **cámara principal** objeto en el *jerarquía Panel*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capítulo 10: finalización de la clase AzureServices

Con los demás scripts en su lugar, es posible *completa* el *AzureServices* clase. Esto se conseguirá mediante:

1.  Agregar un nuevo método denominado *CreateCloudIdentityAsync()* , para establecer las variables de autenticación necesarias para la comunicación con Azure.

    > Este método también comprobará la existencia de un archivo almacenado anteriormente que contiene la lista de la forma.
    >
    > **Si se encuentra el archivo**, deshabilitará el usuario *que mirar*y desencadenar la creación de formas, según el patrón de formas, tal como está almacenado en el **archivos de Azure Storage**. El usuario puede ver esto, como el **texto de la malla** proporcionará mostrar 'Storage' o 'New', dependiendo del origen de las formas.
    >
    > **Si se encuentra ningún archivo**, se habilitará la *que mirar*, permitir que el usuario crear formas al observar la **GazeButton** objeto en la escena.

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

2.  Es el siguiente fragmento de código desde el *Start()* método; en la que se realizará una llamada a la *CreateCloudIdentityAsync()* método. No dude en Copiar a través de su actual *Start()* método, con la siguiente:

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

3.  Rellene el código para el método *CallAzureFunctionForNextShape()* . Va a usar creado previamente *Azure Function App* para solicitar un índice de la forma. Una vez que se recibe la nueva forma, este método enviará la forma para el *ShapeFactory* clase para crear la nueva forma de la escena. Utilice el código siguiente para completar el cuerpo de *CallAzureFunctionForNextShape()* .

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

4.  Agregue un método para crear una cadena, mediante la concatenación de los enteros almacenados en la lista de historial de la forma y guardarlos en su *archivos de almacenamiento de Azure*.

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

5.  Agregue un método para recuperar el texto almacenado en el archivo se encuentra en su *archivos de almacenamiento de Azure* y *deserializar* en una lista.

6.  Una vez completado este proceso, el método vuelve a habilita a la mirada para que el usuario puede agregar más formas a la escena.

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

## <a name="chapter-11---build-the-uwp-solution"></a>Capítulo 11: Compile la solución UWP

Para comenzar el proceso de compilación:

1.  Vaya a **archivo** > **configuración de compilación**.

    ![Compilar la aplicación](images/AzureLabs-Lab5-54.png)

2.  Haz clic en **Compilación**. Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta y asígnele el nombre *aplicación*. A continuación, con el *aplicación* carpeta seleccionada, presione **seleccionar la carpeta**.

3.  Unity empezará a compilar el proyecto para el *aplicación* carpeta.

4.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un *Explorador de archivos* ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

## <a name="chapter-12---deploying-your-application"></a>Capítulo 12 - implementación de la aplicación

Para implementar la aplicación:

1.  Navegue hasta la *aplicación* carpeta que creó en el [último capítulo](#chapter-11---build-the-uwp-solution). Verá un archivo con el nombre de las aplicaciones, con la extensión '.sln', que debería haga doble clic en, por lo que para abrirlo en *Visual Studio*.

2.  En el **plataforma de solución**, seleccione **x86, equipo Local**.

3.  En el **configuración de la solución** seleccione **depurar**.

    > Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo. Sin embargo, necesitará también hacer lo siguiente:
    > - Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la **configuración** > **red e Internet**  >   **Wi-Fi** > **opciones avanzadas**; IPv4 es la dirección que debe usar. 
    > - Asegúrese de **modo de programador** es **en**; se encuentra en **configuración** > **actualización y seguridad**  >  **Para los desarrolladores**.

    ![Implementar solución](images/AzureLabs-Lab5-55.png)

4.  Vaya a la **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listas para iniciar y probado.

## <a name="your-finished-azure-functions-and-storage-application"></a>El Azure Functions y la aplicación de almacenamiento finalizado

Enhorabuena, compila una aplicación de realidad mixta que aprovecha los servicios de la funciones de Azure y el almacenamiento de Azure. La aplicación podrá dibujar en los datos almacenados y proporcionar una acción basada en esos datos.

![final producto-end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

Cree una segunda spawn punto y registro que se creó un objeto desde el punto de generar. Al cargar el archivo de datos, reproducir las formas que se generan a partir de la ubicación que se crearon originalmente.

### <a name="exercise-2"></a>Ejercicio 2

Crear un método para reiniciar la aplicación, en lugar de tener que volver a abrirlo cada vez. **Cargar escenas** es un buen lugar para comenzar. Después de hacer eso, cree una forma de borrar la lista almacenada en *Azure Storage*, de modo que pueden restablecerse fácilmente desde su aplicación. 
