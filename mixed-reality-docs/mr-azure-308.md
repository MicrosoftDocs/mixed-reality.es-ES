---
title: 'MR y Azure 308: notificaciones entre dispositivos'
description: Complete este curso para aprender a implementar Azure Notification Hubs, Azure Functions, Azure Storage y tablas en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, notificación, funciones, tablas, Notification hubs, hololens, envolventes, VR
ms.openlocfilehash: d65750f37815efecae85e7bff85318a234079af8
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438761"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR y Azure 308: notificaciones entre dispositivos

![Inicio del producto final](images/AzureLabs-Lab8-00.png)

En este curso, aprenderá a agregar funcionalidades de Notification Hubs a una aplicación de realidad mixta con Azure Notification Hubs, tablas de Azure y Azure Functions.

**Azure Notification hubs** es un servicio de Microsoft que permite a los desarrolladores enviar notificaciones de envío personalizadas y personalizadas a cualquier plataforma, todo ello en la nube. Esto puede permitir que los desarrolladores se comuniquen con los usuarios finales o incluso comunicarse entre varias aplicaciones, dependiendo del escenario. Para obtener más información, visite la [Página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)de **Notification hubs de Azure** .

**Azure Functions** es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure. Esto proporciona una manera de delegar el trabajo en la nube, en lugar de la aplicación local, que puede tener muchas ventajas. **Azure Functions** admite varios lenguajes de desarrollo, como C\#, F\#, node. js, Java y php. Para obtener más información, visite la [página](https://docs.microsoft.com/azure/azure-functions/functions-overview) **Azure Functions** .

**Azure tables** es un servicio en la nube de Microsoft, que permite a los desarrolladores almacenar datos estructurados que no son de SQL en la nube, lo que facilita el acceso desde cualquier lugar. El servicio ofrece un diseño sin esquemas, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible. Para obtener más información, visite la [Página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) **tablas de Azure** .

Una vez completado este curso, tendrá una aplicación de auriculares envolvente de realidad mixta y una aplicación de equipo de escritorio, que podrá hacer lo siguiente:

1. La aplicación de equipo de escritorio permitirá al usuario desplace un objeto en el espacio 2D (X e y) con el mouse.

2. El movimiento de objetos dentro de la aplicación de PC se enviará a la nube mediante JSON, que tendrá el formato de una cadena que contiene un identificador de objeto, un tipo y una información de transformación (coordenadas X e y). 

3. La aplicación de realidad mixta, que tiene una escena idéntica a la aplicación de escritorio, recibirá notificaciones sobre el movimiento de objetos, desde el servicio de Notification Hubs (que acaba de actualizar la aplicación de equipo de escritorio). 

4. Tras recibir una notificación, que contendrá el identificador de objeto, el tipo y la información de transformación, la aplicación de realidad mixta aplicará la información recibida a su propia escena.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta. Este curso es un tutorial independiente, que no implica directamente ningún otro laboratorio de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 308: notificaciones entre dispositivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens. Al usar HoloLens, puede observar algún Eco durante la captura de voz.

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
- Acceso a Internet para la instalación de Azure y acceso a Notification Hubs

## <a name="before-you-start"></a>Antes de empezar

- Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
- Debe ser el propietario del portal para desarrolladores de Microsoft y el portal de registro de aplicaciones; de lo contrario, no tendrá permiso para acceder a la aplicación en el [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capítulo 1: creación de una aplicación en el portal para desarrolladores de Microsoft

Para usar el servicio **Azure Notification hubs** , tendrá que crear una aplicación en el portal para desarrolladores de Microsoft, ya que será necesario registrar la aplicación para que pueda enviar y recibir notificaciones.

1.  Inicie sesión en el [portal para desarrolladores de Microsoft](https://developer.microsoft.com/dashboard).

    > Tendrá que iniciar sesión en su cuenta de Microsoft.

2.  En el panel, haga clic en **crear una nueva aplicación**.

    ![Creación de una aplicación](images/AzureLabs-Lab8-01.png)

3.  Aparecerá un elemento emergente en el que debe reservar un nombre para la nueva aplicación. En el cuadro de texto, inserte un nombre apropiado; Si el nombre elegido está disponible, aparecerá un paso a la derecha del cuadro de texto. Una vez que haya insertado un nombre disponible, haga clic en el botón **reservar nombre del producto** situado en la parte inferior izquierda de la ventana emergente.

    ![invertir un nombre](images/AzureLabs-Lab8-02.png)

4.  Una vez creada la aplicación, estará listo para pasar al siguiente capítulo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capítulo 2: recuperar las nuevas credenciales de las aplicaciones

Inicie sesión en el portal de registro de aplicaciones, donde se mostrará la nueva aplicación y recupere las credenciales que se usarán para configurar el **servicio de Notification hubs** en **Azure portal**.

1.  Vaya al [portal de registro de aplicaciones](https://apps.dev.microsoft.com).

    ![Portal de registro de aplicaciones](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Tendrá que usar su cuenta de Microsoft para iniciar sesión.  
    > **Debe** ser la cuenta de Microsoft que usó en el [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal)anterior, con el portal para desarrolladores de la tienda Windows.

2.  La aplicación se encuentra en la sección **mis aplicaciones** . Una vez que lo encuentre, haga clic en él y se le dirigirá a una nueva página que tiene el nombre de la aplicación más el **registro**.

    ![la aplicación recién registrada](images/AzureLabs-Lab8-04.png)

3.  Desplácese hacia abajo en la página de registro para buscar la sección de secretos de la **aplicación** y el **SID del paquete** de la aplicación. Copie ambos para usarlos con la configuración del **servicio Azure Notification hubs** en el siguiente capítulo.

    ![secretos de la aplicación](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capítulo 3: instalación de Azure Portal: creación de un servicio de Notification Hubs

Una vez que se recuperen las credenciales de las aplicaciones, tendrá que ir a Azure portal, donde creará un servicio de Azure Notification Hubs.

1.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

    > [!NOTE] 
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque **centro de notificaciones**y haga clic en ***entrar***.

    ![búsqueda del centro de notificaciones](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > Es posible que la palabra ***nuevo*** se haya reemplazado por **crear un recurso**, en portales más recientes.

3.  La nueva página proporcionará una descripción del servicio *Notification hubs* . En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.

    ![Crear instancia de Notification hubs](images/AzureLabs-Lab8-07.png)

4.  Una vez que haya hecho clic en ***crear***:

    1.  Inserte el nombre que desee para esta instancia de servicio.

    2.  Proporcione un **espacio de nombres** que podrá asociar a esta aplicación.

    3.  Seleccione una **ubicación.**

    4.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).

        > Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Seleccione una **suscripción**adecuada.

    6.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7. Selecciona **Crear**.

        ![detalles del servicio de rellenado](images/AzureLabs-Lab8-08.png)

5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![notificación](images/AzureLabs-Lab8-09.png)

7.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de servicio del **centro de notificaciones** .

    ![ir al recurso](images/AzureLabs-Lab8-10.png)
    
8.  En la página información general, en el medio de la página, haga clic en **Windows (WNS).** El panel de la derecha cambiará para mostrar dos campos de texto, que requieren el **SID del paquete** y la clave de **seguridad**, de la aplicación que configuró anteriormente.

    ![servicio de hubs recién creado](images/AzureLabs-Lab8-11.png)

9. Una vez que haya copiado los detalles en los campos correctos, haga clic en **Guardar**y recibirá una notificación cuando se haya actualizado correctamente el centro de notificaciones.

    ![copiar detalles de seguridad](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capítulo 4: configurar el servicio tabla de Azure portal

Después de crear la instancia de servicio de Notification Hubs, vuelva a Azure portal, donde creará un servicio de tablas de Azure mediante la creación de un recurso de almacenamiento.

1.  Si aún no ha iniciado sesión, inicie sesión en [Azure portal](https://portal.azure.com).

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda, busque la **cuenta de almacenamiento**y haga clic en **entrar**.

    > [!NOTE] 
    > Es posible que la palabra ***nuevo*** se haya reemplazado por **crear un recurso**, en portales más recientes.

3.  Seleccione **cuenta de almacenamiento: BLOB, archivo, tabla, cola** en la lista.

    ![búsqueda de la cuenta de almacenamiento](images/AzureLabs-Lab8-13.png)

4.  La nueva página proporcionará una descripción del servicio de la **cuenta de almacenamiento** . En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una instancia de este servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab8-14.png)

5.  Una vez que haya hecho clic en **crear**, aparecerá un panel:

    1. Inserte el **nombre** que desee para esta instancia de servicio (debe estar todo en minúsculas).

    2. En **modelo de implementación**, haga clic en **Administrador de recursos**.

    3.  En **tipo de cuenta**, en el menú desplegable, seleccione **almacenamiento (uso general V1)** .

    4. Seleccione una **Ubicación**adecuada.
    
    5.  En el menú desplegable **replicación** , seleccione **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .

    6.  En **rendimiento**, haga clic en **estándar**.

    7.  En la sección **transferencia segura requerida** , seleccione **deshabilitado**.

    8.  En el menú desplegable **suscripción** , seleccione una suscripción adecuada.

    9.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).

        > Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Deje las **redes virtuales** como **deshabilitadas** si se trata de una opción.

    11. Haz clic en **Crear**.

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab8-15.png)

6.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

7.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal. Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab8-16.png)

8.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la página de información general de la nueva instancia del servicio de almacenamiento.

    ![ir al recurso](images/AzureLabs-Lab8-17.PNG)

9. En la página información general, en la parte derecha, haga clic en **tablas**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. El panel de la derecha cambiará para mostrar la información de **Table Service** , en la que es necesario agregar una nueva tabla. Para ello, haga clic en el botón **+** **tabla** en la esquina superior izquierda.

    ![abrir tablas](images/AzureLabs-Lab8-19.png)

11. Se mostrará una nueva página, en la que es necesario escribir un **nombre de tabla**. Este es el nombre que usará para hacer referencia a los datos de la aplicación en capítulos posteriores. Inserte un nombre apropiado y haga clic en **Aceptar**.

    ![crear nueva tabla](images/AzureLabs-Lab8-20.png)    

12. Una vez creada la nueva tabla, podrá verla dentro de la página **Table Service** (en la parte inferior).

    ![nueva tabla creada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capítulo 5: completar la tabla de Azure en Visual Studio

Ahora que ha configurado la cuenta de almacenamiento de **Table Service** , es el momento de agregar datos a ella, que se usará para almacenar y recuperar información. La edición de las tablas se puede realizar a través de **Visual Studio**.

1.  Abra **Visual Studio**.

2.  En el menú, haga clic en **ver** > **Cloud Explorer**.

    ![Abra Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  El **Cloud Explorer** se abrirá como un elemento acoplado (sea paciente, ya que la carga puede tardar tiempo).

    > [!NOTE] 
    > Si la suscripción que usó para crear las *cuentas de almacenamiento* no es visible, asegúrese de que tiene: 
    > - Ha iniciado sesión en la misma cuenta que la que usó para Azure portal.
    > - Seleccionó su suscripción desde la página de administración de cuentas (puede que tenga que aplicar un filtro de la configuración de la cuenta):  
    >
    >   ![buscar suscripción](images/AzureLabs-Lab8-22-5.png)

4.  Se mostrarán los servicios en la nube de Azure. Busque **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de ella para expandir sus cuentas.

    ![abrir cuentas de almacenamiento](images/AzureLabs-Lab8-23.png)

5.  Una vez expandida, la **cuenta de almacenamiento** recién creada debe estar disponible. Haga clic en la flecha situada a la izquierda de su almacenamiento y, después, una vez expandida, busque **tablas** y haga clic en la flecha situada junto a ella para mostrar la **tabla** que ha creado en el último capítulo. Haga doble clic en la **tabla**.

    ![abrir tabla de objetos de escenas](images/AzureLabs-Lab8-24.png)

6.  La tabla se abrirá en el centro de la ventana de Visual Studio. Haga clic en el icono de la tabla con la **+** (más).

    ![Agregar nueva tabla](images/AzureLabs-Lab8-25.png)

7.  Aparecerá una ventana que le solicitará que *agregue la entidad*. Creará tres entidades en total, cada una con varias propiedades. Observará que *PartitionKey* y *RowKey* ya se han proporcionado, ya que se usan en la tabla para buscar los datos. 

    ![partición y clave de fila](images/AzureLabs-Lab8-26.png)

8. Actualice el *valor* de **PartitionKey** y **RowKey** como se indica a continuación (Recuerde hacer esto para cada propiedad de fila que agregue, aunque incremente el RowKey cada vez):

    ![agregar valores correctos](images/AzureLabs-Lab8-26-5.png)

9.  Haga clic en **Agregar propiedad** para agregar filas de datos adicionales. Haga que la primera tabla vacía coincida con la tabla siguiente.

10. Cuando haya terminado, haga clic en **Aceptar** .

    ![Haga clic en Aceptar cuando haya terminado](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Asegúrese de que ha cambiado el **tipo** de las entradas **X**, **y**y **Z**, a **doble**. 

11. Observará que la tabla tiene ahora una fila de datos. Haga clic de nuevo en el icono de **+** (Plus) para agregar otra entidad.

    ![primera fila](images/AzureLabs-Lab8-27-5.png)

12. Cree una propiedad adicional y, a continuación, establezca los valores de la nueva entidad para que coincidan con los que se muestran a continuación.

    ![Agregar cubo](images/AzureLabs-Lab8-28.png)

13. Repita el último paso para agregar otra entidad. Establezca los valores de esta entidad en los que se muestran a continuación.

    ![Agregar cilindro](images/AzureLabs-Lab8-29.png)

14. La tabla debería tener ahora el siguiente aspecto.

    ![tabla completa](images/AzureLabs-Lab8-30.png)

15. Ha completado este capítulo. Asegúrese de guardar.

## <a name="chapter-6---create-an-azure-function-app"></a>Capítulo 6: creación de una Function App de Azure

Cree una Function App de Azure, a la que llamará la aplicación de escritorio para actualizar **TABLE** Service y enviar una notificación a través del **centro de notificaciones**.

En primer lugar, debe crear un archivo que permita que la función de Azure cargue las bibliotecas que necesita.

1.  Abra **el Bloc de notas** (Presione la tecla Windows y escriba Bloc de notas).

    ![abrir el Bloc de notas](images/AzureLabs-Lab8-31.png)

2.  Con el Bloc de notas abierto, inserte la siguiente estructura JSON en él. Una vez hecho esto, guárdelo en el escritorio como **Project. JSON**. Es importante que la nomenclatura sea correcta: Asegúrese de que **no tiene una extensión de archivo. txt** . Este archivo define las bibliotecas que utilizará la función. Si ha usado NuGet, le resultará familiar.

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

3.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

4.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque **function App**, presione **entrar**.

    ![búsqueda de function App](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.

5.  La nueva página proporcionará una descripción del servicio **function App** . En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.

    ![instancia de la aplicación de función](images/AzureLabs-Lab8-33.png)

6.  Una vez que haya hecho clic en **crear**, rellene lo siguiente:

    1. En **nombre**de la aplicación, inserte el nombre que desee para esta instancia de servicio.

    2. Seleccione una **suscripción**.

    3. Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea un **servicio de function App**, debe estar disponible un nivel gratis.

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).

        > Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. En el caso de **sistemas operativos**, haga clic en Windows, ya que es la plataforma prevista.

    6. Seleccione un **plan de hospedaje** (este tutorial usa un **plan de consumo**.

    7. Seleccione una **Ubicación** **(elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)**

    8. En la sección **almacenamiento** , **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.

    9. No necesitará *Application Insights* en esta aplicación, así que no dude en dejarlo **fuera**de servicio.

    10. Haz clic en **Crear**.

        ![crear nueva instancia](images/AzureLabs-Lab8-34.png)

7.  Una vez que haya hecho clic en **crear** , tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

8.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación](images/AzureLabs-Lab8-35.png)

9.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

10. Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. 

    ![ir al recurso](images/AzureLabs-Lab8-36.png)

11. Haga clic en el icono de **+** (más) situado junto a *funciones*para *crear un nuevo*.

    ![Agregar nueva función](images/AzureLabs-Lab8-37.png)

12. En el panel central, aparecerá la ventana de creación de la **función** . Omita la información de la mitad superior del panel y haga clic en **función personalizada**, que se encuentra cerca de la parte inferior (en el área azul, como se muestra a continuación).

    ![función personalizada](images/AzureLabs-Lab8-38.png)

13. La nueva página dentro de la ventana mostrará varios tipos de función. Desplácese hacia abajo para ver los tipos púrpura y haga clic en el elemento **http Put** .

    ![http put (vínculo)](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Es posible que tenga que desplazarse más hacia abajo en la página (y es posible que esta imagen no tenga exactamente el mismo aspecto, si se han realizado actualizaciones de Azure portal), pero busca un elemento denominado *http Put*.

14. Aparecerá la ventana **put de http** , donde tendrá que configurar la función (vea la imagen siguiente).

    1.  En **idioma,** en el menú desplegable, seleccione C\#.

    2.  En **nombre,** escriba un nombre adecuado.

    3.  En el menú desplegable **nivel de autenticación** , seleccione **función**.

    4.  En la sección **nombre de tabla** , debe usar el nombre exacto que usó para crear el servicio **tabla** previamente (incluido el mismo caso de letra).

    5.  En la sección conexión de la **cuenta de almacenamiento** , use el menú desplegable y seleccione la cuenta de almacenamiento desde allí. Si no está allí, haga clic en el **nuevo** hipervínculo que aparece junto al título de la sección para mostrar otro panel, donde debe aparecer la cuenta de almacenamiento.

        ![nuevo almacenamiento](images/AzureLabs-Lab8-40.png)

15. Haga clic en **crear** y recibirá una notificación que le notificará que la configuración se ha actualizado correctamente.

    ![Create (función)](images/AzureLabs-Lab8-41.png)

16. Después de hacer clic en **crear**, se le redirigirá al editor de funciones.

    ![actualizar código de función](images/AzureLabs-Lab8-42.png)

17. Inserte el código siguiente en el editor de funciones (reemplazando el código de la función):

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
    > Con las bibliotecas incluidas, la función recibe el nombre y la ubicación del objeto que se ha colocado en la escena de Unity ( C# como un objeto, denominado **UnityGameObject**). A continuación, este objeto se utiliza para actualizar los parámetros de objeto de la tabla creada. Después, la función realiza una llamada al servicio de centro de notificaciones creado, que notifica a todas las aplicaciones suscritas.

18. Con el código en su lugar, haga clic en **Guardar**.

19. A continuación, haga clic en el icono de **\<** (flecha) situado en el lado derecho de la página.

    ![abrir el panel de carga](images/AzureLabs-Lab8-43.png)

20. Un panel se deslizará hacia la derecha. En ese panel, haga clic en **cargar**y aparecerá un explorador de archivos.

21. Vaya a y haga clic en el archivo **Project. JSON** , que ha creado anteriormente en el **Bloc de notas** y, a continuación, haga clic en el botón **abrir** . Este archivo define las bibliotecas que utilizará la función.

    ![cargar JSON](images/AzureLabs-Lab8-44.png)

22. Cuando se haya cargado el archivo, aparecerá en el panel de la derecha. Al hacer clic en él se abrirá en el editor de **funciones** . Debe tener **exactamente** el mismo aspecto que la siguiente imagen (debajo del paso 23).

23. A continuación, en el panel de la izquierda, debajo de **funciones**, haga clic en el vínculo **integrar** .

    ![función Integrate](images/AzureLabs-Lab8-45.png)

24. En la siguiente página, en la esquina superior derecha, haga clic en **editor avanzado** (como se muestra a continuación).

    ![abrir el editor avanzado](images/AzureLabs-Lab8-46.png)

25. Se abrirá un archivo **function. JSON** en el panel central, que debe reemplazarse por el siguiente fragmento de código. Esto define la función que se va a compilar y los parámetros que se pasan a la función.

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

26. El editor debe ser ahora similar a la imagen siguiente:

    ![volver al editor estándar](images/AzureLabs-Lab8-47.png)

27. Es posible que observe que los parámetros de entrada que acaba de insertar podrían no coincidir con los detalles de almacenamiento y tabla y, por tanto, deben actualizarse con la información. No **lo haga aquí**, como se explica a continuación. Simplemente haga clic en el vínculo **Editor estándar** , en la esquina superior derecha de la página, para volver atrás.

28. De nuevo en el **Editor estándar**, haga clic en **Azure Table Storage (tabla)** , en **entradas**. 
    
    ![Entradas de tabla](images/AzureLabs-Lab8-47-5.png)

29. Asegúrese de que la siguiente coincidencia con **su** información es diferente (hay una imagen por debajo de los pasos siguientes):

    1.  **Nombre de tabla**: el nombre de la tabla que ha creado en el Azure Storage, Table Service.

    2.  **Conexión de la cuenta de almacenamiento:** haga clic en **nuevo**, que aparece junto al menú desplegable, y aparecerá un panel a la derecha de la ventana.

        ![nuevo almacenamiento](images/AzureLabs-Lab8-48.png)

        1.  Seleccione la **cuenta de almacenamiento**que creó anteriormente para hospedar las **aplicaciones de función.**

        2. Observará que se ha creado el valor de conexión de la **cuenta de almacenamiento** .

        3. Asegúrese de presionar **Guardar** cuando haya terminado.

    3.  La página **entradas** debe coincidir con la que se muestra a continuación, mostrando **su** información.

        ![entradas completadas](images/AzureLabs-Lab8-49.png)

30. A continuación, haga clic en **centro de notificaciones de Azure (notificación)** en **salidas**. Asegúrese de que los siguientes elementos coinciden con **su** información, ya que pueden ser diferentes (hay una imagen por debajo de los pasos siguientes):

    1.  **Nombre del centro de notificaciones**: este es el nombre de la instancia de servicio del **centro de notificaciones** que creó anteriormente.

    2.  **Notification hubs conexión de espacio de nombres**: haga clic en **nuevo**, que aparece junto al menú desplegable.

        ![comprobar salidas](images/AzureLabs-Lab8-50.png)

    3. Aparecerá el cuadro emergente de **conexión** (consulte la imagen siguiente), donde debe seleccionar el **espacio de nombres** del **centro de notificaciones**, que configuró anteriormente.

    4. Seleccione el nombre del **centro de notificaciones** en el menú desplegable central.

    5.  Establezca el menú desplegable **Directiva** en **DefaultFullSharedAccessSignature**.

    6. Haga clic en el botón **seleccionar** para volver atrás.

        ![actualización de salida](images/AzureLabs-Lab8-51.png)

31.  La página de **resultados** debe coincidir ahora con la siguiente, pero con **su** información en su lugar. Asegúrese de presionar **Guardar**.

> [!WARNING]
> *No edite el nombre del centro de notificaciones directamente* (esto debe realizarse mediante el **editor avanzado**, siempre y cuando haya seguido los pasos anteriores correctamente.

![salidas completadas](images/AzureLabs-Lab8-50.png)

32. En este punto, debe probar la función para asegurarse de que funciona. Para ello: 

    1. Vaya a la página de la función una vez más:

        ![salidas completadas](images/AzureLabs-Lab8-50-1.png)

    2. De nuevo en la página de la función, haga clic en la pestaña **probar** en el extremo derecho de la página para abrir la hoja *prueba* :

        ![salidas completadas](images/AzureLabs-Lab8-50-2.png)

    3. En el cuadro de texto cuerpo de la **solicitud** de la hoja, pegue el código siguiente:

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

    4. Con el código de prueba en su lugar, haga clic en el botón **Ejecutar** situado en la parte inferior derecha y se ejecutará la prueba. Los registros de salida de la prueba aparecerán en el área de la consola, debajo del código de la función.

        ![salidas completadas](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Si se produce un error en la prueba anterior, tendrá que comprobar que ha seguido los pasos anteriores exactamente, en particular, en el **Panel de integración**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capítulo 7: configurar un proyecto de Unity de escritorio

> [!IMPORTANT]
> La aplicación de escritorio que está creando ahora **no** funcionará en el editor de Unity. Debe ejecutarse fuera del editor, después de la compilación de la aplicación, mediante Visual Studio (o la aplicación implementada). 

Lo siguiente es una configuración típica para desarrollar con Unity y la realidad mixta, y como tal, es una buena plantilla para otros proyectos.

Configure y pruebe sus auriculares de la realidad mixta.

> [!NOTE] 
> **No** necesitará controladores de movimiento para este curso. Si necesita ayuda para configurar el casco inmersivo, siga este [vínculo sobre cómo configurar Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **Unity** y haga clic en **nuevo**.

    ![nuevo proyecto de Unity](images/AzureLabs-Lab8-52.png)

2.  Debe proporcionar un nombre de proyecto de Unity, insertar **UnityDesktopNotifHub**. Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![crear proyecto](images/AzureLabs-Lab8-53.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![establecer herramientas externas de VS](images/AzureLabs-Lab8-54.png)

4.  A continuación, vaya a **archivo** > **configuración de compilación** y seleccione **plataforma universal de Windows**y, después, haga clic en el botón **cambiar plataforma** para aplicar la selección.

    ![cambiar plataformas](images/AzureLabs-Lab8-55.png)

5.  Mientras sigue en el **archivo** > la **configuración de compilación**, asegúrese de que:

    1.  El **dispositivo de destino** se establece en **cualquier dispositivo**

        > Esta aplicación será para el escritorio, por lo que debe ser **cualquier dispositivo** .

    2.  El **tipo de compilación** se establece en **D3D**

    3.  **SDK** está establecido en la **versión más reciente instalada**

    4.  La **versión de Visual Studio** está establecida en la **más reciente instalada**

    5.  **Compilar y ejecutar** está establecido en **equipo local**

    6.  Mientras tanto, merece la pena guardar la escena y agregarla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.

            ![agregar escenas abiertas](images/AzureLabs-Lab8-56.png)

        2. Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.

            ![nueva carpeta Scenes](images/AzureLabs-Lab8-57.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo **nombre de archivo:** , escriba **NH\_Desktop\_Scene**y, a continuación, presione **Guardar**.

            ![nuevo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.

6.  En la misma ventana, haga clic en el botón **configuración del reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .

7.  En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  La **versión de scripting en tiempo de ejecución** debe ser **Experimental (.net 4,6 equivalente)**

        2. El **back-end de scripting** debe ser **.net**

        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![versión de 4,6 net](images/AzureLabs-Lab8-59.png)

    2.  En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        - **InternetClient**

            ![marcar el cliente de Internet](images/AzureLabs-Lab8-60.png)

8.  De nuevo en la **configuración de compilación** , los *proyectos de Unity C\#* ya no están atenuados; Marque la casilla situada junto a este.

9.  Cierre la ventana **configuración de compilación** .

10. Guarde la escena y el **archivo** de proyecto > **guardar la escena o el archivo** > **guardar el proyecto**.

    > [!IMPORTANT]
    > Si desea omitir el componente de *configuración de Unity* para este proyecto (aplicación de escritorio) y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo. 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Todavía tendrá que agregar los componentes de script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capítulo 8: importación de los archivos dll en Unity

Usará Azure Storage para Unity (que a su vez usa el SDK de .net para Azure). Para obtener más información, siga este [vínculo sobre Azure Storage para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado el [ **. unitypackage Tools**](https://aka.ms/azstorage-unitysdk) más reciente de github. A continuación, haga lo siguiente:

1.  Agregue el **. unitypackage Tools** a Unity mediante la opción de menú **recursos \> importar paquete \> paquete personalizado** .

2.  En el cuadro **importar paquete Unity** que aparece, puede seleccionar todo en * **plugin* \> * Storage * * *.  Desactive todo lo demás, ya que no es necesario para este curso.

    ![importar a paquete](images/AzureLabs-Lab8-61.png)

3.  Haga clic en el botón ***importar*** para agregar los elementos al proyecto.

4.  Vaya a la carpeta **Storage** en **Complementos** en la vista proyecto y seleccione *solo*los siguientes complementos:

    -   Microsoft. Data. Edm
    -   Microsoft. Data. OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft. JSON
    -   System. espacial

![desactive cualquier plataforma](images/AzureLabs-Lab8-62.png)

5.  Con *estos complementos específicos* seleccionados, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** y haga clic en **aplicar**.

    ![aplicar dll de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Estamos marcando estos complementos concretos para usarlos solo en el editor de Unity. Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.

6.  En la carpeta del complemento de **almacenamiento** , seleccione solo:

    -   Microsoft. Data. Services. Client

        ![establecer no procesar para archivos dll](images/AzureLabs-Lab8-64.png)

7.  Active la casilla **no procesar** en **configuración de plataforma** y haga clic en ***aplicar***.

    ![no aplicar procesamiento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Estamos marcando este complemento como "no procesar", ya que el parche de ensamblado de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se haya procesado.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capítulo 9: creación de la clase TableToScene en el proyecto de Unity de escritorio

Ahora debe crear los scripts que contienen el código para ejecutar esta aplicación.

El primer script que debe crear es **TableToScene**, que es responsable de:

-   Lectura de entidades en la tabla de Azure.
-   Con los datos de la tabla, determine qué objetos generar y en qué posición.

El segundo script que debe crear es **CloudScene**, que es responsable de:

-   Registrar el evento de clic izquierdo para permitir que el usuario arrastre objetos alrededor de la escena.
-   Serializar los datos de objeto de esta escena de Unity y enviarlos a Azure Function App.

Para crear esta clase:

1.  Haga clic con el botón derecho en la carpeta de **recursos** que se encuentra en el panel Proyecto y **cree** > **carpeta**. Asigne a la carpeta el nombre **scripts**.

    ![crear carpeta de scripts](images/AzureLabs-Lab8-66.png)

    ![crear scripts (carpeta 2)](images/AzureLabs-Lab8-67.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla.

3.  Haga clic con el botón derecho en la carpeta **scripts** y haga clic en **crear** >  **C# script**. Asigne al script el nombre **TableToScene**.

    ![nuevo script de c#](images/AzureLabs-Lab8-68.png)
    ![cambiar el nombre de TableToScene](images/AzureLabs-Lab8-69.png)

4.  Haga doble clic en el script para abrirlo en Visual Studio 2017.

5.  Agregue los siguientes espacios de nombres:

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
    > Sustituya el valor **accountName** por el nombre del servicio de Azure Storage y el valor **accountKey** por el valor de clave que se encuentra en el servicio Azure Storage, en Azure portal (consulte la imagen siguiente). 
    >
    > ![capturar clave de cuenta](images/AzureLabs-Lab8-70.png)

7.  Ahora, agregue los métodos **Start ()** y Activate **()** para inicializar la clase.

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

8.  Dentro de la clase **TableToScene** , agregue el método que recuperará los valores de la tabla de Azure y los usará para generar los primitivos adecuados en la escena.

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

9.  Fuera de la clase **TableToScene** , debe definir la clase utilizada por la aplicación para serializar y deserializar las **entidades de tabla**.

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

10. Asegúrese de **Guardar** antes de volver al editor de Unity.

11. En el panel **jerarquía** , haga clic en la **cámara principal** para que sus propiedades aparezcan en el **Inspector**.

12. Con la carpeta **scripts** abierta, seleccione el **archivo** de script TableToScene y arrástrelo a la **cámara principal**. El resultado debe ser el siguiente:

    ![Agregar script a la cámara principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capítulo 10: creación de la clase CloudScene en el proyecto de Unity de escritorio

El segundo script que debe crear es **CloudScene**, que es responsable de:

-   Registrar el evento de clic izquierdo para permitir que el usuario arrastre objetos alrededor de la escena.

-   Serializar los datos de objeto de esta escena de Unity y enviarlos a Azure Function App.

Para crear el segundo script:

1.  Haga clic con el botón derecho en la carpeta **scripts** , haga clic en **crear**, **C\# script**. Asigne un nombre al script **CloudScene**
    
    ![nuevo script de c#](images/AzureLabs-Lab8-72.png)
    ![cambiar el nombre de CloudScene](images/AzureLabs-Lab8-73.png)

2.  Agregue los siguientes espacios de nombres:

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

4.  Sustituya el valor de **azureFunctionEndpoint** por la dirección URL de Azure function App que se encuentra en el servicio Azure function App, en Azure portal, tal como se muestra en la imagen siguiente:

    ![obtener dirección URL de la función](images/AzureLabs-Lab8-74.png)

5.  Ahora, agregue los métodos **Start ()** y Activate **()** para inicializar la clase.

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

6.  En el método **Update ()** , agregue el siguiente código que detectará la entrada del mouse y arrastre, que a su vez moverá GameObjects en la escena. Si el usuario ha arrastrado y colocado un objeto, pasará el nombre y las coordenadas del objeto al método **UpdateCloudScene ()** , que llamará al servicio Azure function App, que actualizará la tabla de Azure y desencadenará la notificación.

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

7.  Ahora, agregue el método **UpdateCloudScene ()** , como se indica a continuación:

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

8.  Guardar el código y volver a Unity

9.  Arrastre el script **CloudScene** a la **cámara principal**. 

    1. En el panel **jerarquía** , haga clic en la **cámara principal** para que sus propiedades aparezcan en el **Inspector**. 

    2. Con la carpeta **scripts** abierta, seleccione el script **CloudScene** y arrástrelo a la **cámara principal**. El resultado debe ser el siguiente:

        > ![Arrastre el script de nube a la cámara principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capítulo 11: compilar el proyecto de escritorio en UWP

Ya se ha completado todo lo necesario para la sección Unity de este proyecto.

1.  Vaya a **configuración de compilación** ( **configuración de compilación**de > de**archivos** ).

2.  En la ventana **configuración de compilación** , haga clic en **compilar**.

    ![compilar proyecto](images/AzureLabs-Lab8-76.png)

3.  Se abrirá una ventana del **Explorador de archivos** en la que se le solicitará una ubicación para compilar. Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.

    ![nueva carpeta para compilación](images/AzureLabs-Lab8-77.png)

    1.  Abra la nueva carpeta **compilaciones** y cree otra carpeta (con la **nueva carpeta** una vez más) y asígnele el nombre **NH\_Desktop\_aplicación**.

        ![nombre de carpeta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Con la **aplicación NH\_Desktop\_** seleccionada. Haga clic en **Seleccionar carpeta**. El proyecto tardará un minuto o más en compilarse.

4.  Después de la compilación, aparecerá el **Explorador de archivos** que muestra la ubicación del nuevo proyecto. Sin embargo, no es necesario abrirlo, ya que primero debe crear el otro proyecto de Unity, en los próximos capítulos.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capítulo 12: configuración de un proyecto de Unity de realidad mixta

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra **Unity** y haga clic en **nuevo**.

    ![nuevo proyecto de Unity](images/AzureLabs-Lab8-79.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity, insertar **UnityMRNotifHub**. Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![nombre UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![establecer el editor externo en VS](images/AzureLabs-Lab8-81.png)

4.  A continuación, vaya a **archivo** > **configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .

    ![cambiar de plataforma a UWP](images/AzureLabs-Lab8-82.png)

5.  Vaya a **archivo** > **configuración de compilación** y asegúrese de que:

    1.  El **dispositivo de destino** se establece en **cualquier dispositivo**

        > Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.

    2.  El **tipo de compilación** se establece en **D3D**

    3.  **SDK** está establecido en la **versión más reciente instalada**

    4.  La **versión de Visual Studio** está establecida en la **más reciente instalada**

    5.  **Compilar y ejecutar** está establecido en **equipo local**

    6.  Mientras tanto, merece la pena guardar la escena y agregarla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.

            ![agregar escenas abiertas](images/AzureLabs-Lab8-83.png)

        2. Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.

            ![nueva carpeta Scenes](images/AzureLabs-Lab8-84.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo **nombre de archivo:** , escriba **NH\_Mr\_Scene**y presione **Guardar**.

            ![nueva escena: NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.

6.  En la misma ventana, haga clic en el botón **configuración del reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .    

    ![abrir configuración del reproductor](images/AzureLabs-Lab8-86.png)

7.  En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  La **versión de scripting en tiempo de ejecución** debe ser **Experimental** (.net 4,6 equivalente)
        2.  El **back-end de scripting** debe ser ***.net***
        3.  El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![compatibilidad de API](images/AzureLabs-Lab8-87.png)

    2.  Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se ha agregado el **SDK de Windows Mixed Reality** .

        ![actualizar la configuración de XR](images/AzureLabs-Lab8-88.png)        

    3.  En la pestaña **configuración de publicación** , en **capacidades**, tenga en cuentan lo siguiente:

        - **InternetClient**           

            ![marcar el cliente de Internet](images/AzureLabs-Lab8-89.png)

8.  De nuevo en la **configuración de compilación**, los **proyectos de Unity C#**  ya no están atenuados: Marque la casilla situada junto a este.

9.  Una vez realizados estos cambios, cierre la ventana Configuración de compilación.

10. Guarde la escena y el **archivo** de proyecto > **guardar la escena o el archivo** > **guardar el proyecto**.

    > [!IMPORTANT]
    > Si desea omitir el componente de *configuración de Unity* para este proyecto (aplicación de realidad mixta) y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe desde [ Capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Todavía tendrá que agregar los componentes de script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capítulo 13: importación de los archivos dll en el proyecto de Unity de realidad mixta

Usará Azure Storage para la biblioteca de Unity (que usa el SDK de .net para Azure). Siga este [vínculo sobre cómo usar Azure Storage con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente de [. unitypackage Tools](https://aka.ms/azstorage-unitysdk). A continuación, haga lo siguiente:

1.  Agregue el. unitypackage Tools que descargó desde el anterior a Unity mediante la opción de menú **recursos** > **importar paquete** > **paquete personalizado** .

2.  En el cuadro **importar paquete Unity** que aparece, puede seleccionar todo en **complemento** > **Storage**.

    ![importar paquete](images/AzureLabs-Lab8-90.png)

3.  Haga clic en el botón **importar** para agregar los elementos al proyecto.

4.  Vaya a la carpeta **Storage** en **Complementos** en la vista proyecto y seleccione *solo*los siguientes complementos:

    -   Microsoft. Data. Edm
    -   Microsoft. Data. OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft. JSON
    -   System. espacial

    ![seleccionar complementos](images/AzureLabs-Lab8-91.png)

5.  Con *estos complementos específicos* seleccionados, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** y haga clic en **aplicar**.

    ![aplicar cambios de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Está marcando estos complementos concretos para usarlos solo en el editor de Unity. Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.

6.  En la carpeta del complemento de **almacenamiento** , seleccione solo:

    -   Microsoft. Data. Services. Client

        ![seleccionar cliente de servicios de datos](images/AzureLabs-Lab8-93.png)

7.  Active la casilla **no procesar** en **configuración de plataforma** y haga clic en **aplicar**.

    ![no procesar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Está marcando este complemento "no procesar" porque el parche de ensamblado de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se haya procesado.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capítulo 14: creación de la clase TableToScene en el proyecto de Unity de realidad mixta

La clase **TableToScene** es idéntica a la que se explica en el [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). Cree la misma clase en el proyecto de Unity de realidad mixta siguiendo el mismo procedimiento descrito en el [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Una vez que haya completado este capítulo, los dos **proyectos de Unity** tendrán esta clase configurada en la cámara principal.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capítulo 15: creación de la clase NotificationReceiver en el proyecto de Unity de realidad mixta

El segundo script que debe crear es **NotificationReceiver**, que es responsable de:

-   Registrando la aplicación con el centro de notificaciones en la inicialización.
-   Escucha de notificaciones procedentes del centro de notificaciones.
-   Deserializar los datos de objeto de las notificaciones recibidas.
-   Mueva GameObjects en la escena, en función de los datos deserializados.

Para crear el script **NotificationReceiver** :

1.  Haga clic con el botón derecho en la carpeta **scripts** , haga clic en **crear**, **C\# script**. Asigne al script el nombre **NotificationReceiver**.

    ![crear un nuevo script de c#](images/AzureLabs-Lab8-95.png)
    ![asígnele el nombre NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Haga doble clic en el script para abrirlo.

3.  Agregue los siguientes espacios de nombres:

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

5.  Sustituya el valor de **hubName** por el nombre del servicio de centro de notificaciones y el valor de **hubListenEndpoint** por el valor de punto de conexión que se encuentra en la pestaña directivas de acceso, servicio Azure Notification Hub, en Azure portal (consulte la imagen siguiente).

    ![Insertar punto de conexión de directiva de Notification hubs](images/AzureLabs-Lab8-97.png)

6.  Ahora, agregue los métodos **Start ()** y Activate **()** para inicializar la clase.

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

7.  Agregue el método **WaitForNotification** para permitir que la aplicación reciba notificaciones de la biblioteca del centro de notificaciones sin entrar en conflicto con el subproceso principal:

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

8.  El método siguiente, **InitNotificationAsync ()** , registrará la aplicación con el servicio del centro de notificaciones en la inicialización. El código se marca como comentario, ya que Unity no podrá compilar el proyecto. Se quitarán los comentarios al importar el paquete Nuget de mensajería de Azure en Visual Studio.

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

9.  El siguiente controlador, **Channel\_PushNotificationReceived ()** , se desencadenará cada vez que se reciba una notificación. Deserializará la notificación, que será la entidad de la tabla de Azure que se ha movido a la aplicación de escritorio y, a continuación, moverá el GameObject correspondiente de la escena MR a la misma posición. 
    
    > [!IMPORTANT]
    > El código está comentado porque el código hace referencia a la biblioteca de mensajería de Azure, que agregará después de compilar el proyecto de Unity mediante el administrador de paquetes Nuget, dentro de Visual Studio. Como tal, el proyecto de Unity no podrá compilar, a menos que esté comentado. Tenga en cuenta que, para compilar el proyecto y, a continuación, desea volver a Unity, deberá **cambiar el comentario** del código.

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

10. Recuerde guardar los cambios antes de volver al editor de Unity.

11. En el panel **jerarquía** , haga clic en la **cámara principal** para que sus propiedades aparezcan en el **Inspector**.

12. Con la carpeta **scripts** abierta, seleccione el script **NotificationReceiver** y arrástrelo a la **cámara principal**. El resultado debe ser el siguiente:

    ![Arrastre el script del receptor de notificaciones a la cámara](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Si va a desarrollar esto para Microsoft HoloLens, tendrá que actualizar el componente de *cámara* de la **cámara principal**para que:
    > - Borrar marcas: color sólido
    > - Fondo: negro

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capítulo 16: compilar el proyecto de realidad mixta en UWP

Este capítulo es idéntico al proceso de compilación del proyecto anterior. Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.

1.  Vaya a **configuración de compilación** ( **configuración de compilación** de > de **archivos** ).

2.  En el menú **configuración de compilación** , asegúrese de que los proyectos de **Unity C#** * se marcan (lo que le permitirá editar los scripts en este proyecto después de la compilación).

3.  Una vez hecho esto, haga clic en **compilar**.

    ![compilar proyecto](images/AzureLabs-Lab8-99.png)

4.  Se abrirá una ventana del **Explorador de archivos** en la que se le solicitará una ubicación para compilar. Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.

    ![crear carpeta de compilaciones](images/AzureLabs-Lab8-100.png)

    1.  Abra la nueva carpeta **compilaciones** y cree otra carpeta (con la **nueva carpeta** una vez más) y asígnele el nombre **NH\_Mr\_aplicación**.

        ![crear carpeta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  Con la **aplicación NH\_MR\_** seleccionada. Haga clic en **Seleccionar carpeta**. El proyecto tardará un minuto o más en compilarse.

5.  Después de la compilación, se abrirá una ventana del **Explorador de archivos** en la ubicación del nuevo proyecto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capítulo 17: adición de paquetes NuGet a la solución UnityMRNotifHub

> [!WARNING] 
> Recuerde que, una vez que agregue los siguientes paquetes NuGet (y quite los comentarios del código en el siguiente [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), el código, cuando se vuelve a abrir en el proyecto Unity, presentará errores. Si desea volver y seguir editando en el editor de Unity, necesitará comentar que errosome código y, a continuación, quitar el comentario de nuevo más tarde, una vez que vuelva a usar Visual Studio. 

Una vez completada la compilación de realidad mixta, navegue hasta el proyecto de realidad mixta, que creó, y haga doble clic en el archivo de solución (. sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.
Ahora deberá agregar el paquete de NuGet **WindowsAzure. Messaging. Managed** . se trata de una biblioteca que se usa para recibir notificaciones del centro de notificaciones.

Para importar el paquete NuGet:

1.  En el **Explorador de soluciones**, haga clic con el botón derecho en la solución.

2.  Haga clic en **administrar paquetes NuGet**.

    ![abrir el administrador de Nuget](images/AzureLabs-Lab8-102.png)

3.  Seleccione la pestaña ***examinar*** y busque **WindowsAzure. Messaging. Managed**.

    ![buscar paquete de mensajería de Windows Azure](images/AzureLabs-Lab8-103.png)

4.  Seleccione el resultado (como se muestra a continuación) y, en la ventana de la derecha, active la casilla junto a **proyecto**. Esto colocará un paso en la casilla junto a **proyecto**, junto con la casilla junto al proyecto **Assembly-CSharp** y **UnityMRNotifHub** .

    ![marcar todos los proyectos](images/AzureLabs-Lab8-104.png)

5.  **Es posible que** la versión proporcionada inicialmente no sea compatible con este proyecto. Por lo tanto, haga clic en el menú desplegable junto a **versión**y haga clic en **versión 0.1.7.9**y, a continuación, haga clic en **instalar**.

6.  Ya ha terminado de instalar el paquete NuGet. Busque el código comentado que escribió en la clase **NotificationReceiver** y quite los comentarios.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capítulo 18: edición de la aplicación UnityMRNotifHub, clase NotificationReceiver

Después de haber agregado los **paquetes de NuGet**, deberá quitar la marca de *Comentario* de parte del código dentro de la clase **NotificationReceiver** .

Esto incluye:

1. Espacio de nombres en la parte superior:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Todo el código dentro del método **InitNotificationsAsync ()** :

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
> El código anterior tiene un Comentario en él: Asegúrese de que no ha eliminado accidentalmente *ese comentario (ya que el* código no se compilará si lo tiene!).

3. Y, por último, el evento **Channel_PushNotificationReceived** :

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

Con estos sin comentarios, asegúrese de guardar y, a continuación, continúe con el siguiente capítulo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capítulo 19: asociar el proyecto de realidad mixta a la aplicación de la tienda

Ahora debe asociar el proyecto de **realidad mixta** a la aplicación de la tienda que creó en al principio del laboratorio.

1.  Abra la solución.

2.  Haga clic con el botón derecho en el proyecto de aplicación de UWP en el panel de Explorador de soluciones, vaya a **tienda**y **asocie la aplicación con la tienda..** ..

    ![Asociación de la tienda abierta](images/AzureLabs-Lab8-105.png)

3.  Aparecerá una nueva ventana denominada **asociar la aplicación a la tienda Windows**. Haz clic en **Siguiente**.

    ![ir a la pantalla siguiente](images/AzureLabs-Lab8-106.png)

4.  Se cargarán todas las aplicaciones asociadas a la cuenta con la que ha iniciado sesión. Si no ha iniciado sesión en su cuenta, puede **iniciar sesión** en esta página.

5.  Busque el **nombre** de la aplicación de la tienda que creó al principio de este tutorial y selecciónelo. Después haz clic en **Next**.

    ![buscar y seleccionar el nombre del almacén](images/AzureLabs-Lab8-107.png)

6.  Haga clic en **asociar**.

    ![asociar la aplicación](images/AzureLabs-Lab8-108.png)

7.  La aplicación está ahora **asociada** a la aplicación de la tienda. Esto es necesario para habilitar las notificaciones.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capítulo 20: implementación de aplicaciones UnityMRNotifHub y UnityDesktopNotifHub

Este capítulo puede ser más fácil con dos personas, ya que el resultado incluirá las aplicaciones que se ejecutan, una que se ejecuta en el escritorio del equipo y la otra dentro de los auriculares que se incluyen.

La aplicación de casco envolvente está esperando recibir los cambios en la escena (los cambios de posición del GameObjects local) y la aplicación de escritorio realizará cambios en su escena local (cambios de posición), que se compartirán en la aplicación MR. Tiene sentido implementar la aplicación MR primero, seguida de la aplicación de escritorio, de modo que el receptor pueda empezar a escuchar.

Para implementar la aplicación **UnityMRNotifHub** en el equipo local:

1.  Abra el archivo de solución de la aplicación **UnityMRNotifHub** en **Visual Studio 2017**.

2.  En la **plataforma**de la solución, seleccione **x86, equipo local**.

3.  En la **configuración de soluciones** , seleccione **depurar**.

    ![establecer la configuración del proyecto](images/AzureLabs-Lab8-109.png)

4.  Vaya al **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.

5.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

Para implementar la aplicación **UnityDesktopNotifHub** en la máquina local:

1.  Abra el archivo de solución de la aplicación **UnityDesktopNotifHub** en **Visual Studio 2017**.

2.  En la **plataforma**de la solución, seleccione **x86, equipo local**.

3.  En la **configuración de soluciones** , seleccione **depurar**.

    ![establecer la configuración del proyecto](images/AzureLabs-Lab8-110.png)

4.  Vaya al **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.

5.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

6.  Inicie la aplicación de realidad mixta, seguida de la aplicación de escritorio.

Con ambas aplicaciones en ejecución, mueva un objeto en la escena del escritorio (con el botón primario del mouse). Estos cambios posicionales se realizarán de forma local, se serializarán y se enviarán al servicio Function App. El servicio de Function App actualizará la tabla junto con el centro de notificaciones. Tras recibir una actualización, el centro de notificaciones enviará los datos actualizados directamente a todas las aplicaciones registradas (en este caso, la aplicación de auriculares envolvente), que luego deserializará los datos entrantes y aplicará los nuevos datos posicionales a los objetos locales. moviéndolos en la escena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Su aplicación de Azure Notification Hubs finalizada
 
Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio Azure Notification Hubs y permite la comunicación entre las aplicaciones.
 
![final del producto final](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

¿Puede averiguar cómo cambiar el color del GameObjects y enviar la notificación a otras aplicaciones que vean la escena?

### <a name="exercise-2"></a>Ejercicio 2

¿Puede Agregar movimiento de GameObjects a la aplicación MR y ver la escena actualizada en la aplicación de escritorio?
