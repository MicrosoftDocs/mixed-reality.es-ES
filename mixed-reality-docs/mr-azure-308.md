---
title: El Sr. y Azure 308 - notificaciones entre dispositivos
description: Realice este curso para obtener información sobre cómo implementar Azure Notification Hubs, Azure Functions y el almacenamiento de Azure y las tablas dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, notificaciones, funciones, tablas, centros de notificaciones, vr envolventes, hololens,
ms.openlocfilehash: ed56c936a0498b6e0ac804da15a2c6ec98239d0c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605720"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>El Sr. y Azure 308: Notificaciones entre dispositivos

![final producto-inicio](images/AzureLabs-Lab8-00.png)

En este curso, obtendrá información sobre cómo agregar funcionalidades de Notification Hubs a una aplicación de realidad mixta mediante Azure Notification Hubs, las tablas de Azure y Azure Functions.

**Azure Notification Hubs** es un servicio de Microsoft, que permite a los desarrolladores enviar notificaciones push personalizadas y dirigidas a cualquier plataforma, todo ello gracias dentro de la nube. Esto puede eficazmente permiten a los desarrolladores para comunicarse con los usuarios finales, o incluso comunicarse entre varias aplicaciones, según el escenario. Para obtener más información, visite la **Azure Notification Hubs** [página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).

**Las funciones de Azure** es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure. Esto proporciona una manera para delegar el trabajo a la nube, en lugar de la aplicación local, lo que puede tener muchas ventajas. **Las funciones de Azure** admite varios lenguajes de desarrollo, incluidos C\#, F\#, Node.js, Java y PHP. Para obtener más información, visite la **Azure Functions** [página](https://docs.microsoft.com/azure/azure-functions/functions-overview).

**Las tablas de Azure** es un servicio de nube de Microsoft, que permite a los desarrolladores almacenar datos estructurados que no sean de SQL en la nube, lo que sea fácilmente accesible en cualquier lugar. El servicio cuenta con un diseño sin esquema, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible. Para obtener más información, visite la **Azure Tables** [página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Una vez completado este curso, tendrá una aplicación envolventes auriculares de realidad mixta y una aplicación de PC de escritorio, que podrá hacer lo siguiente:

1. La aplicación de PC de escritorio permite al usuario mover un objeto en el espacio 2D (X y), con el mouse.

2. El movimiento de objetos dentro de la aplicación de PC se enviarán a la nube mediante JSON, que estará en la forma de cadena, que contiene un identificador de objeto, tipo y transformar la información (coordenadas X e Y). 

3. La aplicación de realidad mixta, que tiene una escena idéntica a la aplicación de escritorio, recibirá notificaciones sobre el movimiento de objetos desde el servicio Notification Hubs (que simplemente se ha actualizado la aplicación de PC de escritorio). 

4. Al recibir una notificación, que contiene el Id. de objeto, el tipo y la información de transformación, la aplicación de realidad mixta aplicará la información recibida a su escena.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta. Este curso es un tutorial independiente, que no implican directamente otros laboratorios realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 308: Notificaciones entre dispositivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens. Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.

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
- Acceso a Internet para la instalación de Azure y tener acceso a Notification Hubs

## <a name="before-you-start"></a>Antes de empezar

- Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
- Debe ser el propietario de su Portal para desarrolladores de Microsoft y el Portal de registro de aplicación, en caso contrario, no tendrá permiso para tener acceso a la aplicación en [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capítulo 1: crear una aplicación en el Portal para desarrolladores de Microsoft

Para usar el **Azure Notification Hubs** servicio, deberá crear una aplicación en el Portal para desarrolladores de Microsoft, como la aplicación deberá registrarse, para que pueda enviar y recibir notificaciones.

1.  Inicie sesión en el [Portal para desarrolladores de Microsoft](https://developer.microsoft.com/dashboard).

    > Deberá iniciar sesión en su Account de Microsoft.

2.  En el panel, haga clic en **crear una nueva aplicación**.

    ![Creación de una aplicación](images/AzureLabs-Lab8-01.png)

3.  Aparecerá un menú emergente en la que necesita reservar un nombre para la nueva aplicación. En el cuadro de texto, inserte un nombre adecuado; Si el nombre elegido está disponible, aparecerá una marca de verificación a la derecha del cuadro de texto. Una vez que tenga un nombre disponible insertado, haga clic en el **reservar nombre de producto** botón a la parte inferior izquierda de la ventana emergente.

    ![un nombre inverso](images/AzureLabs-Lab8-02.png)

4.  Con la aplicación creada ahora, está listo para pasar al siguiente capítulo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capítulo 2: recuperar las credenciales de las aplicaciones nuevas

Inicie sesión en el Portal de registro de aplicación, donde se mostrará la nueva aplicación y recuperar las credenciales que se usará para el programa de instalación la **Notification Hubs Service** dentro de la **Portal de Azure**.

1.  Navegue hasta la [Portal de registro de aplicación](http://apps.dev.microsoft.com).

    ![portal de registro de aplicación](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Deberá usar su Account de Microsoft para inicio de sesión.  
    > Esto **debe** ser la Account de Microsoft que ha usado en el anterior [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal), con el portal para desarrolladores de Windows Store.

2.  Encontrará la aplicación en el **mis aplicaciones** sección. Una vez encontrado, haga clic en él y se le llevará a una página nueva que tenga la aplicación más nombre **registro**.

    ![la aplicación recién registrada](images/AzureLabs-Lab8-04.png)

3.  Desplácese hacia abajo en la página de registro para encontrar su **secretos de aplicación** sección y la **SID del paquete** para la aplicación. Copie las dos para su uso con la configuración de la **servicio de Azure Notification Hubs** en el capítulo siguiente.

    ![Secretos de aplicación](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capítulo 3: configurar el Portal de Azure: creación de servicio de Notification Hubs

Con las credenciales de las aplicaciones recuperar, se tendrán que ir al Portal de Azure, donde creará un servicio de Azure Notification Hubs.

1.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

    > [!NOTE] 
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque **centro de notificaciones**y haga clic en ***ENTRAR***.

    ![Buscar centro de notificaciones](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > La palabra ***New*** se han reemplazado con **crear un recurso**, en los portales más reciente.

3.  La nueva página proporcionará una descripción de la *Notification Hubs* service. En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.

    ![Crear instancia de notification hubs](images/AzureLabs-Lab8-07.png)

4.  Una vez que ha hecho clic ***crear***:

    1.  Inserte el nombre deseado para esta instancia de servicio.

    2.  Proporcione un **espacio de nombres** que podrá asociar a esta aplicación.

    3.  Seleccione un **ubicación.**

    4.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Seleccione un **suscripción**.

    6.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7. Selecciona **Crear**.

        ![Rellene los detalles del servicio](images/AzureLabs-Lab8-08.png)

5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![notificación](images/AzureLabs-Lab8-09.png)

7.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva **centro de notificaciones** instancia de servicio.

    ![Ir al recurso](images/AzureLabs-Lab8-10.png)
    
8.  En la página de introducción a medio camino hacia abajo en la página, haga clic en **Windows (WNS).** El panel de la derecha cambiará a mostrar dos campos de texto que requieren su **SID del paquete** y **clave de seguridad**, desde la aplicación configurada anteriormente.

    ![recién creado el servicio de concentradores](images/AzureLabs-Lab8-11.png)

9. Una vez que haya copiado los detalles en los campos correctos, haga clic en **guardar**, y recibirá una notificación cuando se ha actualizado correctamente el centro de notificaciones.

    ![Copiar detalles de seguridad](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capítulo 4: configurar el Portal de Azure: creación de Table Service

Después de crear la instancia del servicio de Notification Hubs, navegar hasta el Portal de Azure, donde creará un servicio de tablas de Azure mediante la creación de un recurso de almacenamiento.

1.  Si no ha iniciado sesión, inicie sesión en el [Portal de Azure](https://portal.azure.com).

2.  Una vez iniciada la sesión, haga clic en **New** en la esquina superior izquierda esquina y busque **cuenta de almacenamiento**y haga clic en **ENTRAR**.

    > [!NOTE] 
    > La palabra ***New*** se han reemplazado con **crear un recurso**, en los portales más reciente.

3.  Seleccione **cuenta de almacenamiento: blob, archivo, tabla, cola** en la lista.

    ![Busque la cuenta de almacenamiento](images/AzureLabs-Lab8-13.png)

4.  La nueva página proporcionará una descripción de la **cuenta de almacenamiento** service. En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una instancia de este servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab8-14.png)

5.  Una vez que ha hecho clic **crear**, aparecerá un panel:

    1. Insertar el elemento **nombre** para esta instancia de servicio (debe estar en minúsculas).

    2. Para **modelo de implementación**, haga clic en **Administrador de recursos**.

    3.  Para **tipo de cuenta**, mediante el menú desplegable, seleccione **almacenamiento (uso general v1)**.

    4. Seleccione un **ubicación**.
    
    5.  Para el **replicación** menú desplegable, seleccione **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)**.

    6.  Para **rendimiento**, haga clic en **estándar**.

    7.  Dentro de la **se requiere transferencia segura** sección, seleccione **deshabilitado**.

    8.  Desde el **suscripción** menú desplegable, seleccione una suscripción adecuada.

    9.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Deje **redes virtuales** como **deshabilitado** si se trata de una opción para usted.

    11. Haga clic en **Crear**.

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab8-15.png)

6.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

7.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal. Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab8-16.png)

8.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva página de información general de instancia de servicio de almacenamiento.

    ![Ir al recurso](images/AzureLabs-Lab8-17.PNG)

9. En la página de información general, en el lado derecho, haga clic en **tablas**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. El panel de la derecha cambiará para mostrar el **de Table service** información, en la que deberá agregar una nueva tabla. Haga clic en el **+** **tabla** botón a la esquina superior izquierda.

    ![abrir tablas](images/AzureLabs-Lab8-19.png)

11. Se mostrará una página nueva, en la que tiene que introducir un **nombre de la tabla**. Este es el nombre que usará para hacer referencia a los datos en la aplicación en los capítulos posteriores. Inserte un nombre adecuado y haga clic en **Aceptar**.

    ![Crear nueva tabla](images/AzureLabs-Lab8-20.png)    

12. Una vez creada la nueva tabla, podrá verlo en el **de Table service** página (en la parte inferior).

    ![nueva tabla creada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capítulo 5: completar la tabla de Azure en Visual Studio

Ahora que su **de Table service** cuenta de almacenamiento ha sido el programa de instalación, es momento de agregar datos a él, que se usará para almacenar y recuperar información. La edición de las tablas puede realizarse a través de **Visual Studio**.

1.  Abra **Visual Studio**.

2.  En el menú, haga clic en **Ver > Cloud Explorer**.

    ![Abra cloud explorer](images/AzureLabs-Lab8-22.png)

3.  El **Cloud Explorer** se abrirá como un elemento acoplado (tenga paciencia, como la carga puede tardar tiempo).

    > [!NOTE] 
    > Si la suscripción que usó para crear su *cuentas de almacenamiento* no está visible, asegúrese de que tiene: 
    > - Iniciar sesión en la misma cuenta que usan para el Portal de Azure.
    > - Selecciona la suscripción desde la página de administración de cuenta (es posible que deba aplicar un filtro de la configuración de su cuenta):  
    >
    >   ![encuentra la suscripción](images/AzureLabs-Lab8-22-5.png)

4.  Se mostrarán los servicios de nube de Azure. Buscar **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de la que se va a expandir sus cuentas.

    ![Abra cuentas de almacenamiento](images/AzureLabs-Lab8-23.png)

5.  Una vez que se expande el recién creado **cuenta de almacenamiento** debe estar disponible. Haga clic en la flecha situada a la izquierda de su almacenamiento y, a continuación, una vez que se expande, encontrar **tablas** y haga clic en la flecha situada junto a la que, para que se muestre el **tabla** que creó en el último capítulo. Haga doble clic en su **tabla**.

    ![Abra la tabla de objetos de la escena](images/AzureLabs-Lab8-24.png)

6.  La tabla se abrirá en el centro de la ventana de Visual Studio. Haga clic en el icono de tabla con el **+** (más) en él.

    ![Agregar nueva tabla](images/AzureLabs-Lab8-25.png)

7.  Se mostrará una ventana, se le pide para permitirle *Agregar entidad*. Creará tres entidades en total, cada una con varias propiedades. Observará que *PartitionKey* y *RowKey* ya se proporcionan, ya que se usan para buscar los datos en la tabla. 

    ![clave de partición y fila](images/AzureLabs-Lab8-26.png)

8. Actualización el *valor* de la **PartitionKey** y **RowKey** como sigue (no olvide hacer esto para cada propiedad de la fila agregar, aunque incremente la clave de fila cada vez):

    ![Agregue los valores correctos](images/AzureLabs-Lab8-26-5.png)

9.  Haga clic en **Agregar propiedad** para agregar filas de datos adicionales. Hacer la primera tabla vacía que coincida con la tabla siguiente.

10. Haga clic en **Aceptar** cuando haya terminado.

    ![Cuando haya terminado, haga clic en Aceptar](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Asegúrese de que ha cambiado el **tipo** de la **X**, **Y**, y **Z**, entradas de **doble**. 

11. Observará que la tabla tiene ahora una fila de datos. Haga clic en el **+** (icono nuevo para agregar otra entidad más).

    ![primera fila](images/AzureLabs-Lab8-27-5.png)

12. Cree una propiedad adicional y, a continuación, establezca los valores de la nueva entidad que coincidan con las que se muestra a continuación.

    ![Agregar cubo](images/AzureLabs-Lab8-28.png)

13. Repita el último paso para agregar otra entidad. Establezca los valores para esta entidad en los que se muestran a continuación.

    ![Agregar cilindro](images/AzureLabs-Lab8-29.png)

14. Ahora, la tabla debería parecerse a lo siguiente.

    ![tabla completa](images/AzureLabs-Lab8-30.png)

15. Ha completado este capítulo. Asegúrese de guardar.

## <a name="chapter-6---create-an-azure-function-app"></a>Capítulo 6: crear una aplicación de función de Azure

Crear una aplicación de función de Azure, que será llamado por la aplicación de escritorio para actualizar el **tabla** de servicio y enviar una notificación a través de la **centro de notificaciones**.

En primer lugar, deberá crear un archivo que permitirá que la función de Azure cargar las bibliotecas que necesarias.

1.  Abra **el Bloc de notas** (presione la tecla de Windows y escriba notepad).

    ![Abra el Bloc de notas](images/AzureLabs-Lab8-31.png)

2.  Con el Bloc de notas abierto, inserte la siguiente estructura JSON en ella. Una vez que lo haya hecho, guárdelo en el escritorio como **project.json**. Es importante que la nomenclatura sea correcta: asegúrese de que lo hace **no tienen un .txt** la extensión de archivo. Este archivo define las bibliotecas que se va a utilizar la función, si ha usado NuGet le resultarán familiares.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

4.  Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque **Function App**, presione **ENTRAR**.

    ![Busque la aplicación de función](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.

5.  La nueva página proporcionará una descripción de la **Function App** service. En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.

    ![instancia de la aplicación de función](images/AzureLabs-Lab8-33.png)

6.  Una vez que ha hecho clic **crear**, rellene lo siguiente:

    1. Para **nombre de la aplicación**, inserte el nombre deseado para esta instancia de servicio.

    2. Seleccione un **suscripción**.

    3. Seleccione el plan de tarifa adecuado para usted, si ésta es la primera hora de creación de un **Function App Service**, un nivel gratuito debe estar disponible para usted.

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Para **OS**, haga clic en Windows, ya que es la plataforma prevista.

    6. Seleccione un **Plan de hospedaje** (este tutorial se usará un **Plan de consumo**.

    7. Seleccione un **ubicación** **(elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)**

    8. Para el **almacenamiento** sección **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.

    9. No necesitará *Application Insights* en esta aplicación, por lo que no dude en dejarlo **desactivar**.

    10. Haga clic en **Crear**.

        ![Crear nueva instancia](images/AzureLabs-Lab8-34.png)

7.  Una vez que ha hecho clic **crear** tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

8.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación](images/AzureLabs-Lab8-35.png)

9.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

10. Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. 

    ![Ir al recurso](images/AzureLabs-Lab8-36.png)

11. Haga clic en el **+** (más) situado junto a *funciones*a *crear nuevo*.

    ![Agregar nueva función](images/AzureLabs-Lab8-37.png)

12. En el panel central, el **función** aparecerá la ventana de creación. Omitir la información de la mitad superior del panel y haga clic en **función personalizada**, que se encuentra en la parte inferior (en el área azul más abajo).

    ![función personalizada](images/AzureLabs-Lab8-38.png)

13. La nueva página dentro de la ventana mostrará los distintos tipos de función. Desplácese hacia abajo para ver los tipos de color púrpuras y haga clic en **HTTP PUT** elemento.

    ![vínculo de put de http](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Es posible que tenga que desplazarse aún más la profundidad la página (y esta imagen puede no ser exactamente el mismo, si han realizado actualizaciones del Portal de Azure), sin embargo, que busca un elemento denominado *HTTP PUT*.

14. El **HTTP PUT** ventana aparecerá, donde deberá configurar la función (vea a continuación para la imagen).

    1.  Para **lenguaje,** mediante el menú desplegable, seleccione C\#.

    2.  Para **nombre,** un nombre adecuado de entrada.

    3.  En el **nivel de autenticación** menú desplegable, seleccione **función**.

    4.  Para el **nombre de la tabla** sección, deberá usar el nombre exacto que usó para crear su **tabla** servicio anteriormente (incluido letras mayúsculas y minúsculas).

    5.  Dentro de la **conexión de la cuenta de almacenamiento** sección, use el menú desplegable y seleccione la cuenta de almacenamiento a partir de ahí. Si no está allí, clic la **New** hipervínculo junto con el título de sección para mostrar otro panel, donde debería aparecer su cuenta de almacenamiento.

        ![nuevo almacenamiento](images/AzureLabs-Lab8-40.png)

15. Haga clic en **crear** y recibirá una notificación que se ha actualizado correctamente la configuración.

    ![Crear función](images/AzureLabs-Lab8-41.png)

16. Después de hacer clic **crear**, se le redirigirá al editor de función.

    ![Actualizar código de función](images/AzureLabs-Lab8-42.png)

17. Inserte el código siguiente en el editor de funciones (el código de la función que reemplaza):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Mediante las bibliotecas incluyen, la función recibe el nombre y la ubicación del objeto que se ha movido de la escena de Unity (como un C# objeto, denominado **UnityGameObject**). Este objeto, a continuación, se usa para actualizar los parámetros de objeto dentro de la tabla creada. De este modo, la función realiza una llamada al servicio creado centro de notificaciones, que notifica a todos los de las aplicaciones.

18. Con el código en su lugar, haga clic en **guardar**.

19. A continuación, haga clic en el **\<** icono (flecha), en el lado derecho de la página.

    ![panel de carga abierta](images/AzureLabs-Lab8-43.png)

20. Un panel se desliza en desde la derecha. En el panel de control, haga clic en **cargar**, y se mostrará un explorador de archivos.

21. Vaya a y haga clic en, el **project.json** archivo que creó en **el Bloc de notas** anteriormente y, a continuación, haga clic en el **abierto** botón. Este archivo define las bibliotecas que se va a usar la función.

    ![upload json](images/AzureLabs-Lab8-44.png)

22. Cuando se ha cargado el archivo, aparecerá en el panel de la derecha. Haga clic en él se abrirá dentro la **función** editor. Debe examinar **exactamente** igual que la imagen siguiente (siguiente paso 23).

23. A continuación, en el panel de la izquierda, bajo **funciones**, haga clic en el **integrar** vínculo.

    ![integrar (función)](images/AzureLabs-Lab8-45.png)

24. En la página siguiente, en la esquina superior derecha, haga clic en **editor avanzado** (continuación).

    ![Abrir el editor avanzado](images/AzureLabs-Lab8-46.png)

25. Un **function.json** archivo se abrirá en el panel central, que debe reemplazarse por el siguiente fragmento de código. Esto define la función que se va a compilar y los parámetros pasados a la función.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. El editor ahora debería parecerse a la imagen siguiente:

    ![volver al editor estándar](images/AzureLabs-Lab8-47.png)

27. Es posible que observe los parámetros de entrada que acaba de insertar podrían no coincidir con los detalles de la tabla y el almacenamiento y, por tanto, deberá actualizarse con la información. **Esta operación no aquí**, tal y como se trata a continuación. Simplemente haga clic en el **editor estándar** vínculo, en la esquina superior derecha de la página para volver atrás.

28. En el **editor estándar**, haga clic en **(tabla) de Azure Table Storage**, en **entradas**. 
    
    ![Entradas de tabla](images/AzureLabs-Lab8-47-5.png)

29. Asegúrese de que la siguiente coincidencia **su** información, como pueden ser diferentes (no hay una imagen hasta por debajo de los pasos siguientes):

    1.  **Nombre de la tabla**: el nombre de la tabla que creó en el almacenamiento de Azure, servicio de tablas.

    2.  **Conexión de la cuenta de almacenamiento:** haga clic en **nuevo**, que aparece junto con el menú desplegable, y aparecerá un panel a la derecha de la ventana.

        ![nuevo almacenamiento](images/AzureLabs-Lab8-48.png)

        1.  Seleccione su **cuenta de almacenamiento**, que creó anteriormente para hospedar el **aplicaciones de función.**

        2. Observará que el **cuenta de almacenamiento** se ha creado el valor de la conexión.

        3. Asegúrese de que presionar **guardar** cuando haya terminado.

    3.  El **entradas** página ahora debe coincidir con la muestra a continuación, **su** información.

        ![complete las entradas](images/AzureLabs-Lab8-49.png)

30. A continuación, haga clic en **(notificación) de Azure Notification Hub** : en **salidas**. Asegúrese de que coincidan con los siguientes **su** información, como pueden ser diferentes (no hay una imagen hasta por debajo de los pasos siguientes):

    1.  **Nombre del centro de notificaciones**: éste es el nombre de su **centro de notificaciones** instancia de servicio que creó anteriormente.

    2.  **Conexión de espacio de nombres de Notification Hubs**: haga clic en **nuevo**, que aparece junto con el menú desplegable.

        ![Comprobar resultados](images/AzureLabs-Lab8-50.png)

    3. El **conexión** emergente aparecerá (consulte la imagen siguiente), donde se debe seleccionar la **Namespace** de la **centro de notificaciones**, que configuró anteriormente.

    4. Seleccione su **centro de notificaciones** nombre en el menú desplegable central.

    5.  Establecer el **directiva** del menú desplegable para **DefaultFullSharedAccessSignature**.

    6. Haga clic en el **seleccione** botón para volver atrás.

        ![actualización de salida](images/AzureLabs-Lab8-51.png)

31.  El **salidas** página ahora debe coincidir con el más abajo, pero con **su** información en su lugar. Asegúrese de que presionar **guardar**.

> [!WARNING]
> *No modifique directamente el nombre del centro de notificaciones* (debería todo esto se realiza mediante el **Editor avanzado**, siempre que ha seguido los pasos anteriores correctamente.

![salidas completa](images/AzureLabs-Lab8-50.png)

32. En este momento, debe probar la función, para asegurarse de que funciona. Para ello: 

    1. Vaya a la página de la función una vez más:

        ![salidas completa](images/AzureLabs-Lab8-50-1.png)

    2. En la página de la función, haga clic en el **prueba** ficha en el extremo derecho de la página para abrir el *prueba* hoja:

        ![salidas completa](images/AzureLabs-Lab8-50-2.png)

    3. Dentro de la **cuerpo de la solicitud** cuadro de texto de la hoja, pegue el siguiente código:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Con el código de prueba en su lugar, haga clic en el **ejecutar** situado en la esquina inferior derecha y la prueba se ejecutará. Los registros de salida de la prueba aparecerá en el área de la consola, bajo el código de función.

        ![salidas completa](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Si se produce un error en la prueba anterior, deberá comprobar que ha seguido los pasos anteriores exactamente, especialmente la configuración de la **integrar panel**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capítulo 7: configurar el proyecto de Unity de escritorio

> [!IMPORTANT]
> La aplicación de escritorio que se va a crear, **no** profesional en el Editor de Unity. Necesita para ejecutarse fuera del Editor, siguiendo la compilación de la aplicación con Visual Studio (o la aplicación implementada). 

El siguiente es un conjunto típico de para desarrollar con Unity y realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

Configurar y probar los auriculares de realidad mixta envolventes.

> [!NOTE] 
> Podrá **no** requieren controladores de movimiento de este curso. Si necesita admite la configuración de los auriculares envolventes, siga esta [vínculo sobre cómo configurar Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **Unity** y haga clic en **New**.

    ![nuevo proyecto de unity](images/AzureLabs-Lab8-52.png)

2.  Deberá proporcionar un nombre de proyecto de Unity, inserte **UnityDesktopNotifHub**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Crear proyecto](images/AzureLabs-Lab8-53.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![conjunto de herramientas de VS externas](images/AzureLabs-Lab8-54.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.

    ![cambiar la plataforma](images/AzureLabs-Lab8-55.png)

5.  Mientras sigue en **archivo > configuración de compilación**, asegúrese de que:

    1.  **Dispositivo de destino** está establecido en **cualquier dispositivo**

        > Esta aplicación será para el escritorio, por lo que debe ser **cualquier dispositivo**

    2.  **Tipo de compilación** está establecido en **D3D**

    3.  **SDK** está establecido en **instalada más reciente**

    4.  **Versión de Visual Studio** está establecido en **instalada más reciente**

    5.  **Compilar y ejecutar** está establecido en **máquina Local**

    6.  Aquí, merece la pena guardar la escena y agregarlo a la compilación.

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![Agregar escenas abiertos](images/AzureLabs-Lab8-56.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![nueva carpeta de segundo plano](images/AzureLabs-Lab8-57.png)

        3. Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo:** campo de texto, escriba **NH\_Desktop\_escena**, a continuación, presione **Guardar**.

            ![nuevo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.

6.  En la misma ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.

7.  En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental (.NET 4.6 equivalente)**

        2. **Scripting de back-end** debe ser **.NET**

        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![versión de .NET 4.6](images/AzureLabs-Lab8-59.png)

    2.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        - **InternetClient**

            ![cliente de internet de graduación](images/AzureLabs-Lab8-60.png)

8.  En **configuración de compilación** *Unity C\# proyectos* ya no está atenuada; Marque la casilla situada junto a esto.

9.  Cerrar la **configuración de compilación** ventana.

10. Guarde la escena y el proyecto **archivo > Guardar escena* / * archivo > Guardar proyecto **.

    > [!IMPORTANT]
    > Si desea omitir la *configurar Unity* componente para este proyecto (aplicación de escritorio) y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Deberá agregar los componentes de script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capítulo 8: importar los archivos DLL en Unity

Va a usar Azure Storage para Unity (que a su vez aprovecha el .net SDK de Azure). Para obtener más información, siga este [vínculo acerca del almacenamiento de Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación. Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) desde GitHub. A continuación, haga lo siguiente:

1.  Agregar el **.unitypackage** a Unity mediante el uso de la **activos \> Importar paquete \> paquete personalizado** opción de menú.

2.  En el **Importar paquete de Unity** cuadro que aparece, puede seleccionar todo el contenido ***complemento* \> * *** de almacenamiento.  Desactive todo lo demás, ya no es necesaria para este curso.

    ![Importar paquete](images/AzureLabs-Lab8-61.png)

3.  Haga clic en el ***importación*** para agregar los elementos al proyecto.

4.  Vaya a la **almacenamiento** carpeta bajo **complementos** en el proyecto, ver y seleccione los siguientes complementos *sólo*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![Desactive cualquier plataforma](images/AzureLabs-Lab8-62.png)

5.  Con *estos complementos específicos* seleccionado, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** a continuación, haga clic en **aplicar**.

    ![se aplican a archivos DLL de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Vamos a marcar estos complementos determinados para su uso en el Editor de Unity. Esto es porque hay diferentes versiones de los complementos mismos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.

6.  En el **almacenamiento** carpeta de complemento, solo seleccione:

    -   Microsoft.Data.Services.Client

        ![No procesar conjunto para archivos DLL](images/AzureLabs-Lab8-64.png)

7.  Compruebe el **proceso no** cuadro bajo **configuración de plataforma** y haga clic en ***aplicar***.

    ![no aplicar ningún procesamiento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Vamos a marcar este complemento "No procesar", porque la revisión del ensamblado de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se ha procesado.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capítulo 9: crear la clase TableToScene en el proyecto de Unity de escritorio

Deberá crear las secuencias de comandos que contiene el código para ejecutar esta aplicación.

Es el primer script, deberá crear **TableToScene**, que es responsable de:

-   Leer entidades dentro de la tabla de Azure.
-   Con los datos de tabla, determinar qué objetos desea generar y en qué posición.

Es el segundo script, deberá crear **CloudScene**, que es responsable de:

-   Registrando el evento primario, para permitir al usuario arrastrar objetos en torno a la escena.
-   Serializar los datos del objeto de esta escena de Unity y enviarlo a la aplicación de función de Azure.

Para crear esta clase:

1.  Haga clic en el **activos** carpeta se encuentra en el Panel de proyecto **crear > carpeta**. Nombre de la carpeta **Scripts**.

    ![Crear carpeta de scripts](images/AzureLabs-Lab8-66.png)

    ![Crear carpeta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirlo.

3.  Haga clic en el **Scripts** carpeta, haga clic en **crear** **C\# Script**. Nombre de la secuencia de comandos **TableToScene**.

    ![script de c#](images/AzureLabs-Lab8-68.png)
    ![TableToScene rename](images/AzureLabs-Lab8-69.png)

4.  Haga doble clic en el script para abrirlo en Visual Studio 2017.

5.  Agregue los espacios de nombres siguientes:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Dentro de la clase, inserte las siguientes variables:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Sustituya el **accountName** valor con el nombre del servicio de almacenamiento de Azure y **accountKey** valor con el valor de clave que se encuentra en el servicio de almacenamiento de Azure, en el Portal de Azure (consulte la imagen siguiente). 
    >
    > ![clave de cuenta de captura](images/AzureLabs-Lab8-70.png)

7.  Ahora, agregue el **Start()** y **Awake()** métodos para inicializar la clase.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  Dentro de la **TableToScene** clase, agregue el método que recupere los valores de la tabla de Azure y usarlas para generar los tipos primitivos adecuados en la escena.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Fuera del **TableToScene** (clase), deberá definir la clase usada por la aplicación de serializar y deserializar la **las entidades de tabla**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Asegúrese de que **guardar** antes de volver al Editor de Unity.

11. Haga clic en el **cámara principal** desde el **jerarquía** panel, para que sus propiedades aparecen en la **Inspector**.

12. Con el **Scripts** carpeta abierta, seleccione la secuencia de comandos **TableToScene archivo** y arrástrelo hasta el **cámara principal**. El resultado debería ser como sigue:

    ![Agregar script a la cámara principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capítulo 10: crear la clase CloudScene en el proyecto de Unity de escritorio

Es el segundo script, deberá crear **CloudScene**, que es responsable de:

-   Registrando el evento primario, para permitir al usuario arrastrar objetos en torno a la escena.

-   Serializar los datos del objeto de esta escena de Unity y enviarlo a la aplicación de función de Azure.

Para crear el segundo script:

1.  Haga clic en el **Scripts** carpeta, haga clic en **crear**, **C\# Script**. Nombre de la secuencia de comandos **CloudScene**
    
    ![script de c#](images/AzureLabs-Lab8-72.png)
    ![cambiar el nombre de CloudScene](images/AzureLabs-Lab8-73.png)

2.  Agregue los espacios de nombres siguientes:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Inserte las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Sustituya el **azureFunctionEndpoint** valor por su URL de aplicación de función de Azure se encuentra en el servicio de aplicación de función de Azure, en el Portal de Azure, como se muestra en la imagen siguiente:

    ![obtener la dirección URL de función](images/AzureLabs-Lab8-74.png)

5.  Ahora, agregue el **Start()** y **Awake()** métodos para inicializar la clase.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  Dentro de la **Update()** método, agregue el código siguiente que detectará la entrada del mouse y arrastre, lo que a su vez se moverá GameObjects en la escena. Si el usuario ha arrastrar y colocar un objeto, se pasará el nombre y las coordenadas del objeto al método **UpdateCloudScene()**, que llamará el servicio de Azure Function App, que actualizará la tabla de Azure y desencadenar el notificación.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Ahora, agregue el **UpdateCloudScene()** método, como sigue:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Guarde el código y volver a Unity

9.  Arrastre el **CloudScene** de script en el **cámara principal**. 

    1. Haga clic en el **cámara principal** desde el **jerarquía** panel, para que sus propiedades aparecen en la **Inspector**. 

    2. Con el **Scripts** abierto, seleccione de la carpeta la **CloudScene** de secuencias de comandos y arrástrelo hasta el **cámara principal**. El resultado debería ser como sigue:

        > ![Arrastre el script en la nube a cámara principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capítulo 11: Compile el proyecto de escritorio para UWP

Ahora todo lo necesario para la sección de Unity de este proyecto se ha completado.

1.  Vaya a **configuración de compilación** (**archivo > configuración de compilación**).

2.  Desde el **configuración de compilación** ventana, haga clic en **compilar**.

    ![Compilar proyecto](images/AzureLabs-Lab8-76.png)

3.  Un **Explorador de archivos** menú emergente de voluntad de ventana, que le solicitará una ubicación para la compilación. Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.

    ![nueva carpeta de compilación](images/AzureLabs-Lab8-77.png)

    1.  Abra el nuevo **compilaciones** carpeta y cree otra carpeta (mediante **nueva carpeta** una vez más) y asígnele el nombre **NH\_Desktop\_aplicación**.

        ![nombre de la carpeta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Con el **NH\_Desktop\_aplicación** seleccionado. Haga clic en **seleccionar la carpeta**. El proyecto tardará un minuto o más en crear.

4.  Después de la compilación, **Explorador de archivos** aparecerá con la ubicación del nuevo proyecto. No hay necesidad de abrirlo, aunque, como necesite para crear otro Unity del proyecto en primer lugar, en los siguientes capítulos.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capítulo 12: configurar el proyecto de Unity de realidad mixta

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra **Unity** y haga clic en **New**.

    ![nuevo proyecto de unity](images/AzureLabs-Lab8-79.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity, insertar **UnityMRNotifHub**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![nombre UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![editor de conjuntos de externas a VS](images/AzureLabs-Lab8-81.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.

    ![cambiar la plataforma a UWP](images/AzureLabs-Lab8-82.png)

5.  Vaya a **archivo > configuración de compilación** y asegúrese de que:

    1.  **Dispositivo de destino** está establecido en **cualquier dispositivo**

        > Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.

    2.  **Tipo de compilación** está establecido en **D3D**

    3.  **SDK** está establecido en **instalada más reciente**

    4.  **Versión de Visual Studio** está establecido en **instalada más reciente**

    5.  **Compilar y ejecutar** está establecido en **máquina Local**

    6.  Aquí, merece la pena guardar la escena y agregarlo a la compilación.

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![Agregar escenas abiertos](images/AzureLabs-Lab8-83.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![nueva carpeta de segundo plano](images/AzureLabs-Lab8-84.png)

        3. Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo:** campo de texto, escriba **NH\_MR\_escena**, a continuación, presione  **Guardar**.

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.

6.  En la misma ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.    

    ![Abrir configuración del Reproductor](images/AzureLabs-Lab8-86.png)

7.  En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental** (.NET 4.6 equivalente)
        2.  **Scripting de back-end** debe ser ***.NET***
        3.  **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![compatibilidad con la API](images/AzureLabs-Lab8-87.png)

    2.  Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega

        ![actualizar la configuración de xr](images/AzureLabs-Lab8-88.png)        

    3.  Dentro de la **configuración de publicación** ficha **capacidades**, documentales:

        - **InternetClient**           

            ![cliente de internet de graduación](images/AzureLabs-Lab8-89.png)

8.  En **configuración de compilación** *Unity C\# proyectos* ya no está atenuado: Marque la casilla situada junto a esto.

9.  Con estos cambios realizados, cierre la ventana de configuración de compilación.

10. Guarde la escena y el proyecto **archivo* *Guardar escena*/ *archivo* * Guardar proyecto **.

    > [!IMPORTANT]
    > Si desea omitir la *configurar Unity* componente para este proyecto (aplicación de la realidad mixta) y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Deberá agregar los componentes de script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capítulo 13: importar los archivos DLL en el proyecto de Unity de realidad mixta

Va a usar el almacenamiento de Azure para la biblioteca de Unity (que usa el SDK de .net para Azure). Siga esta [vínculo sobre cómo usar el almacenamiento de Azure con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación. Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente [.unitypackage](https://aka.ms/azstorage-unitysdk). A continuación, haga lo siguiente:

1.  Agregar el .unitypackage que descargó desde el anterior a Unity mediante el uso de la **activos > Importar paquete > paquete personalizado** opción de menú.

2.  En el **Importar paquete de Unity** cuadro que aparece, puede seleccionar todo el contenido **Plugin > almacenamiento**.

    ![Importar paquete](images/AzureLabs-Lab8-90.png)

3.  Haga clic en el **importación** para agregar los elementos al proyecto.

4.  Vaya a la **almacenamiento** carpeta bajo **complementos** en el proyecto, ver y seleccione los siguientes complementos *sólo*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![Seleccione los complementos](images/AzureLabs-Lab8-91.png)

5.  Con *estos complementos específicos* seleccionado, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** a continuación, haga clic en **aplicar**.

    ![Aplicar cambios de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Marca estos complementos determinados para su uso en el Editor de Unity. Esto es porque hay diferentes versiones de los complementos mismos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.

6.  En el **almacenamiento** carpeta de complemento, solo seleccione:

    -   Microsoft.Data.Services.Client

        ![Seleccione el cliente de servicios de datos](images/AzureLabs-Lab8-93.png)

7.  Compruebe el **proceso no** cuadro bajo **configuración de plataforma** y haga clic en **aplicar**.

    ![No procesar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Marca este complemento "No procesar" porque la revisión del ensamblado de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se procesa.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capítulo 14: creación de la clase TableToScene en el proyecto de Unity de realidad mixta

El **TableToScene** clase es idéntica a la que se explica en [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). Crear la misma clase en el proyecto de Unity siguiendo el mismo procedimiento se explica en la realidad mixta [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Cuando haya completado este capítulo, tanto de su **proyectos de Unity** tendrá esta clase en la cámara principal.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capítulo 15: creación de la clase NotificationReceiver en el proyecto de Unity de realidad mixta

Es el segundo script, deberá crear **NotificationReceiver**, que es responsable de:

-   Registrar la aplicación con el centro de notificaciones en la inicialización.
-   Escuchar notificaciones procedentes del centro de notificaciones.
-   Al deserializar los datos del objeto desde las notificaciones recibidas.
-   Mueva los GameObjects en la escena, en función de los datos deserializados.

Para crear el **NotificationReceiver** secuencia de comandos:

1.  Haga clic en el **Scripts** carpeta, haga clic en **crear**, **C\# Script**. Nombre de la secuencia de comandos **NotificationReceiver**.

    ![Crear script de c#](images/AzureLabs-Lab8-95.png)
    ![denomínelo NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Haga doble clic en el script para abrirlo.

3.  Agregue los espacios de nombres siguientes:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Inserte las siguientes variables:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Sustituya el **hubName** valor por el nombre de servicio de Notification hubs y **hubListenEndpoint** con el valor de punto de conexión se encuentra en la pestaña de directivas de acceso, el servicio de Azure Notification hubs, en el Portal de Azure (consulte la imagen siguiente).

    ![Insertar punto de conexión de directiva de notification hubs](images/AzureLabs-Lab8-97.png)

6.  Ahora, agregue el **Start()** y **Awake()** métodos para inicializar la clase.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Agregar el **WaitForNotification** método para permitir que la aplicación recibir notificaciones de la biblioteca de centro de notificaciones sin conflictos con el subproceso principal:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  El método siguiente, **InitNotificationAsync()**, registrará la aplicación con la notificación del servicio de concentrador en la inicialización. El código está comentado como Unity, no podrá compilar el proyecto. Se quitará los comentarios al importar el paquete Nuget de mensajería de Azure en Visual Studio.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  El siguiente controlador, **canal\_PushNotificationReceived()**, se desencadenará cada vez que se recibe una notificación. Deserializará la notificación, que es la entidad de tabla de Azure que se ha movido de la aplicación de escritorio y, a continuación, mueva el GameObject correspondiente en la escena MR a la misma posición. 
    
    > [!IMPORTANT]
    > El código está comentado porque el código hace referencia a la biblioteca de mensajería de Azure, que se va a agregar después de compilar el proyecto de Unity mediante el Administrador de paquetes de Nuget en Visual Studio. Por lo tanto, el proyecto de Unity no podrá compilar, a menos que se está comentada. Tenga en cuenta que debe compilar el proyecto y, a continuación, se va a devolver a Unity, deberá **volver a comentar** ese código.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. No olvide guardar los cambios antes de volver al Editor de Unity.

11. Haga clic en el **cámara principal** desde el **jerarquía** panel, para que sus propiedades aparecen en la **Inspector**.

12. Con el **Scripts** abierto, seleccione de la carpeta la **NotificationReceiver** de secuencias de comandos y arrástrelo hasta el **cámara principal**. El resultado debería ser como sigue:

    ![Arrastre el script del receptor de notificaciones a la cámara](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Si va a desarrollar para el Microsoft HoloLens, deberá actualizar el **cámara principal**del *cámara* componente, por lo que:
    > - Borrar las marcas de: Color sólido
    > - En segundo plano: Negro

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capítulo 16: compilar el proyecto de realidad mixta a UWP

Este capítulo es idéntico al proceso para el proyecto anterior de compilación. Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.

1.  Vaya a **configuración de compilación** ( **archivo > configuración de compilación...**  ).

2.  Desde el **configuración de compilación** menú, asegúrese de **Unity C# proyectos*** está activada (lo que le permitirá modificar los scripts de este proyecto, después de la compilación).

3.  Una vez hecho esto, haga clic en **compilar**.

    ![Compilar proyecto](images/AzureLabs-Lab8-99.png)

4.  Un **Explorador de archivos** menú emergente de voluntad de ventana, que le solicitará una ubicación para la compilación. Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.

    ![Crear carpeta compilaciones](images/AzureLabs-Lab8-100.png)

    1.  Abra el nuevo **compilaciones** carpeta y cree otra carpeta (mediante **nueva carpeta** una vez más) y asígnele el nombre **NH\_MR\_aplicación**.

        ![Crear carpeta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  Con el **NH\_MR\_aplicación** seleccionado. Haga clic en **seleccionar la carpeta**. El proyecto tardará un minuto o más en crear.

5.  Después de la compilación, un **Explorador de archivos** se abrirá una ventana en la ubicación del nuevo proyecto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capítulo 17: agregar paquetes de NuGet para la solución UnityMRNotifHub

> [!WARNING] 
> Recuerde que, una vez que agregue los siguientes paquetes NuGet (y quite los comentarios del código en los próximos [capítulo](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), el código, cuando vuelva a abrir dentro del proyecto de Unity, presentará errores. Si desea volver atrás y continuar con la edición en el Editor de Unity, deberá comentar ese código errosome y, a continuación, quite a intentarlo más tarde, una vez que esté de nuevo en Visual Studio. 

Una vez completada la compilación de realidad mixta, navegue hasta el proyecto de realidad mixta, que ha creado, y haga doble clic en el archivo de solución (.sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.
Ahora deberá agregar el **WindowsAzure.Messaging.managed** paquete de NuGet; se trata de una biblioteca que se usa para recibir notificaciones desde el centro de notificaciones.

Para importar el paquete de NuGet:

1.  En el **el Explorador de soluciones**, haga clic con el botón derecho en la solución

2.  Haga clic en **administrar paquetes de NuGet**.

    ![Abra el Administrador de nuget](images/AzureLabs-Lab8-102.png)

3.  Seleccione el ***examinar*** pestaña y busque **WindowsAzure.Messaging.managed**.

    ![Busque el paquete de mensajería de windows azure](images/AzureLabs-Lab8-103.png)

4.  Seleccione el resultado (como se muestra a continuación) y, en la ventana a la derecha, seleccione la casilla de verificación junto a **proyecto**. Esto colocará una marca de verificación en la casilla de verificación junto a **proyecto**, junto con la casilla junto a la **ensamblado CSharp** y **UnityMRNotifHub** proyecto.

    ![Marque todos los proyectos](images/AzureLabs-Lab8-104.png)

5.  La versión proporcionada inicialmente **no** que sean compatibles con este proyecto. Por lo tanto, haga clic en el menú desplegable junto a **versión**y haga clic en **versión 0.1.7.9**, a continuación, haga clic en **instalar**.

6.  Ahora ha terminado de instalar el paquete NuGet. Busque el código comentado que escribió en el **NotificationReceiver** clase y quite los comentarios...



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capítulo 18: aplicación de edición UnityMRNotifHub, clase NotificationReceiver

Siguiendo una vez agregada la **paquetes de NuGet**, deberá *quite* parte del código dentro de la **NotificationReceiver** clase.

Esto incluye:

1. El espacio de nombres en la parte superior:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Todo el código dentro de la **InitNotificationsAsync()** método:

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> El código anterior tiene un comentario en él: asegúrese de que tiene no accidentalmente *marca de comentario* que comentar (como el código no se compilará si tienes!).

3. Y, por último, el **Channel_PushNotificationReceived** eventos:

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Con estos marca de comentario, asegúrese de guardar y, a continuación, continúe con el siguiente capítulo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capítulo 19: asociar el proyecto de realidad mixta en el app Store

Ahora debe asociar el **la realidad mixta** proyecto a la aplicación Store que creó en el principio del laboratorio.

1.  Abra la solución.

2.  Haga clic con el botón derecho en la aplicación para UWP proyecto en el panel Explorador de soluciones, el ir a **Store**, y **asociar aplicación con el Store...** .

    ![Abrir almacén de asociación](images/AzureLabs-Lab8-105.png)

3.  Se mostrará una nueva ventana llamada **asociar la aplicación con el Store Windows**. Haz clic en **Siguiente**.

    ![Vaya a la pantalla siguiente](images/AzureLabs-Lab8-106.png)

4.  La carga de seguridad de todas las aplicaciones asociadas con la cuenta que ha iniciado sesión. Si no ha iniciado sesión en su cuenta, puede **sesión** en esta página.

5.  Buscar el **nombre de la aplicación Store** que creó al principio de este tutorial y selecciónelo. Haga clic en **Siguiente**.

    ![Busque y seleccione el nombre del almacén](images/AzureLabs-Lab8-107.png)

6.  Haga clic en **asociar**.

    ![asociar la aplicación](images/AzureLabs-Lab8-108.png)

7.  La aplicación está ahora **asociado** con la aplicación Store. Esto es necesario para habilitar las notificaciones.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capítulo 20: implementar aplicaciones UnityMRNotifHub y UnityDesktopNotifHub

Este capítulo puede ser más fácil con las dos personas, como el resultado incluirá tanto aplicaciones que se ejecutan, uno que ejecute en el equipo, escritorio y la otra en los auriculares envolventes.

La aplicación de auriculares envolventes está esperando a recibir los cambios a la escena (cambia de posición de los GameObjects local) y la aplicación de escritorio se realicen cambios en su escena local (cambia de posición), que se van a compartir a la aplicación MR. Tiene sentido implementar la aplicación MR en primer lugar, seguida de la aplicación de escritorio, para que el receptor puede empezar a escuchar.

Para implementar el **UnityMRNotifHub** aplicación en el equipo Local:

1.  Abra el archivo de solución de su **UnityMRNotifHub** app en **Visual Studio 2017**.

2.  En el **plataforma de solución**, seleccione **x86, equipo Local**.

3.  En el **configuración de la solución** seleccione **depurar**.

    ![conjunto de configuración del proyecto](images/AzureLabs-Lab8-109.png)

4.  Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.

Para implementar el **UnityDesktopNotifHub** aplicación en el equipo Local:

1.  Abra el archivo de solución de su **UnityDesktopNotifHub** app en **Visual Studio 2017**.

2.  En el **plataforma de solución**, seleccione **x86, equipo Local**.

3.  En el **configuración de la solución** seleccione **depurar**.

    ![conjunto de configuración del proyecto](images/AzureLabs-Lab8-110.png)

4.  Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.

6.  Inicie la aplicación de realidad mixta, seguida de la aplicación de escritorio.

Con ambas aplicaciones se ejecutan, mover un objeto de la escena de escritorio (con el botón de Mouse de la izquierda). Estos cambios de posición se se realizan localmente, serializados y enviados al servicio de aplicación de función. El servicio de aplicación de función, a continuación, actualizará la tabla junto con el centro de notificaciones. Que ha recibido una actualización, el centro de notificaciones se enviarán los datos actualizados directamente a todas las aplicaciones registradas (en este caso, la aplicación envolventes auriculares), que, a continuación, deserializar los datos entrantes y los nuevos datos posicionales se aplican a los objetos locales, moverlos en escena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Su terminado la aplicación de Azure Notification Hubs
 
Enhorabuena, compila una aplicación de realidad mixta que aprovecha el servicio de Azure Notification Hubs y permite la comunicación entre aplicaciones.
 
![final producto-end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

¿Puede averiguar cómo cambiar el color de los GameObjects y enviar notificación a otras aplicaciones de visualización de la escena?

### <a name="exercise-2"></a>Ejercicio 2

¿Puede agregar el movimiento de los GameObjects a la aplicación MR y ver la escena actualizada en su aplicación de escritorio?
