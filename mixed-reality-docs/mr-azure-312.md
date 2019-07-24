---
title: 'MR y Azure 312: integración con bot'
description: Complete este curso para obtener información sobre cómo crear e implementar un bot, usar Microsoft bot Framework V4 y comunicarse con él en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, Computer Vision, hololens, inmersivo, VR, Microsoft bot Framework V4, Web App bot, Bot Framework, Microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63542474"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

# <a name="mr-and-azure-312-bot-integration"></a>MR y Azure 312: Integración de bot

En este curso, aprenderá a crear e implementar un bot mediante Microsoft bot Framework V4 y a comunicarse con él a través de una aplicación de Windows Mixed Reality. 

![](images/AzureLabs-Lab312-00.png)

**Microsoft bot Framework V4** es un conjunto de API diseñadas para proporcionar a los desarrolladores las herramientas para crear una aplicación de bot extensible y escalable. Para obtener más información, visite la [Página Microsoft bot Framework](https://dev.botframework.com/) o el [repositorio git de V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Después de completar este curso, habrá creado una aplicación de Windows Mixed Reality, que podrá hacer lo siguiente:

1. Use un **gesto de TAP** para iniciar el bot que escucha la voz de los usuarios.
2. Cuando el usuario ha mencionado algo, el bot intentará proporcionar una respuesta.
3. Muestre la respuesta de bots como texto, situado cerca del bot, en la escena de Unity.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 312: Integración de bot</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR). Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio). Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se enumera a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Acceso a Internet para Azure y para la recuperación de Azure bot. Para obtener más información, [siga este vínculo](https://dev.botframework.com/).

### <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
2.  Configure y pruebe su HoloLens. Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Capítulo 1: creación de la aplicación bot

El primer paso es crear el bot como una aplicación Web de ASP.Net Core local. Una vez que haya terminado y probado, lo publicará en Azure portal.

1.  Abra Visual Studio. Cree un nuevo proyecto, seleccione **asp net Core aplicación web** como el tipo de proyecto (lo encontrará en la subsección .net Core) y llámelo **MyBot**. Haga clic en **Aceptar**.

2.  En la ventana que aparecerá, seleccione **vacío**. Asegúrese también de que el destino esté establecido en **asp net Core 2,0** y que la autenticación esté establecida en **sin autenticación**. Haga clic en **Aceptar**.  

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-01.png)

3.  La solución se abrirá ahora. Haga clic con el botón derecho en la solución **Mybot** en el **Explorador de soluciones** y haga clic en **administrar paquetes NuGet para la solución**. 

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-02.png)

4.  En la pestaña **examinar** , busque **Microsoft. bot. Builder. Integration. Aspnet. Core** (Asegúrese de que tiene activada **la versión preliminar** ). Seleccione la versión **de paquete 4.0.1-Preview**y marque las casillas de proyecto. A continuación, haga clic en **instalar**. Ya ha instalado las bibliotecas necesarias para **Bot Framework V4**. Cierre la página NuGet.

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-03.png)

5.  Haga clic con el botón derecho en el *proyecto*, **MyBot**, en el **Explorador de soluciones** y haga clic en **Agregar** **|** **clase**.

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-04.png)

6.  Asigne a la clase el nombre **MyBot** y haga clic en **Agregar**.

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-05.png)

7.  Repita el punto anterior para crear otra clase denominada **ConversationContext**. 

8.  Haga clic con el botón derecho en **wwwroot** en el **Explorador de soluciones** y haga clic en **Agregar** **|** **nuevo elemento**. Seleccione **página HTML** (la encontrará en la subsección Web). Asigne al archivo el nombre **default. html**. Haga clic en **Agregar**.

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-06.png)

9.  La lista de clases y objetos en el **Explorador de soluciones** debe ser similar a la imagen siguiente.

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-07.png)

10. Haga doble clic en la clase **ConversationContext** . Esta clase es responsable de conservar las variables que usa el bot para mantener el contexto de la conversación. Estos valores de contexto de conversación se mantienen en una instancia de esta clase, porque cualquier instancia de la clase **MyBot** se actualizará cada vez que se reciba una actividad. Agregue el código siguiente a la clase:

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Haga doble clic en la clase **MyBot** . Esta clase hospedará los controladores a los que llama cualquier actividad entrante del cliente. En esta clase agregará el código que se usa para crear la conversación entre el bot y el cliente. Como se mencionó anteriormente, una instancia de esta clase se inicializa cada vez que se recibe una actividad. Agregue el código siguiente a esta clase:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Haga doble clic en la clase **Startup** . Esta clase inicializará el bot. Agregue el código siguiente a la clase:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Abra el archivo de clase de **programa** y compruebe que el código es el mismo que el siguiente:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Recuerde guardar los cambios; para ello, vaya a **archivo** > **guardar todo**en la barra de herramientas de la parte superior de Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capítulo 2: creación del Azure Bot Service

Ahora que ha compilado el código para el bot, debe publicarlo en una instancia de *Web App bot* Service en Azure portal. En este capítulo se muestra cómo crear y configurar el servicio bot en Azure y, después, publicar el código en él.

1.  En primer lugar, inicie sesión en Azure portal https://portal.azure.com) (. 

    1. Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda, busque *Bot App bot*y haga clic en **entrar**.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-08.png)
 
3.  La nueva página proporcionará una descripción de *Web App bot* Service. En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-09.png)
 
4.  Una vez que haya hecho clic en **crear**:

    1. Inserte el **nombre** que desee para esta instancia de servicio.
    2. Seleccione una **suscripción**.
    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

        > Si desea leer más información sobre los grupos de recursos de Azure, [siga este vínculo.](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. Determine la ubicación del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    5. Seleccione el **plan de tarifa** que sea adecuado para usted; si es la primera vez que crea un servicio *Web App bot* , debe estar disponible un nivel gratis (denominado F0)
    6. El nombre de la **aplicación** puede dejarse igual que el *nombre del bot*. 
    7. Deje la *plantilla de bot* como **básicaC#()** .
    8. El *plan de App Service/ubicación* debe haberse rellenado automáticamente para su cuenta.
    9. Establezca la **Azure Storage** que desea usar para hospedar el bot. Si aún no tiene una, puede crearla aquí.
    10. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    11. Haga clic en crear.
 
        ![Cree el Azure Bot Service](images/AzureLabs-Lab312-10.png)

5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-12.png)
 
8. Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de servicio de Azure. 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-13.png)
 
9.  En este momento, debe configurar una característica denominada **Direct line** para permitir que la aplicación cliente se comunique con este servicio de bot. Haga clic en **canales**y, a continuación, en la sección **Agregar un canal destacado** , haga clic en **configurar canal de línea directa**.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-14.png)

10. En esta página encontrará las **claves secretas** que permitirán que la aplicación cliente se autentique con el bot. Haga clic en el botón **Mostrar** y realice una copia de una de las claves mostradas, ya que lo necesitará más adelante en el proyecto. 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capítulo 3: publicación del bot en Azure Web App bot Service

Ahora que el servicio está listo, debe publicar el código de bot que creó previamente en el servicio bot de aplicación web recién creado.

> [!NOTE] 
> Tendrá que publicar su bot en el servicio de Azure cada vez que realice cambios en la solución o el código de bot.

1.  Vuelva a la solución de Visual Studio que creó anteriormente. 
2.  Haga clic con el botón derecho en el proyecto **MyBot** , en el **Explorador de soluciones**y, a continuación, haga clic en **publicar**.

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-16.png)

3.  En la página *seleccionar un destino de publicación* , haga clic en **App Service**y, a continuación, **Seleccione existente**; por último, haga clic en **crear perfil** (puede que tenga que hacer clic en la flecha desplegable junto al botón *publicar* , si no está visible).

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-17.png)

4. Si aún no ha iniciado sesión en su cuenta de Microsoft, tendrá que hacerlo aquí.
5. En la página **publicar** , verá que tiene que establecer la misma **suscripción** que usó para la creación del servicio *Web App bot* . A continuación, establezca la **vista** como **grupo de recursos** y, en la lista desplegable de la estructura de carpetas, seleccione el **grupo de recursos** que creó anteriormente. Haga clic en **Aceptar**. 

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-18.png)

6.  Ahora, haga clic en el botón **publicar** y espere a que se publique el bot (puede tardar unos minutos).

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capítulo 4: configurar el proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **nuevo**. 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-20.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity. Inserte el **Bot de Hololens**. Asegúrese de que la plantilla de proyecto está establecida en **3D**. Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-21.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**. Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-22.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y seleccione **plataforma universal de Windows**y, después, haga clic en el botón **cambiar plataforma** para aplicar la selección.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-23.png)

5.  Mientras sigue en el **archivo > la configuración de compilación** y asegúrese de que:

    1.  El **dispositivo de destino** está establecido en **Hololens**

        > Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.

    2.  El **tipo de compilación** se establece en **D3D**

    3.  **SDK** está establecido en la **versión más reciente instalada**

    4.  La **versión de Visual Studio** está establecida en la **más reciente instalada**

    5.  **Compilar y ejecutar** está establecido en **equipo local**

    6.  Guarde la escena y agréguela a la compilación. 

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.
        
            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-24.png)

        2. Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre Scenes.

             ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-25.png)

        3. Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **BotScene**y, a continuación, haga clic en **Guardar**.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-26.png)

    7. El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.

6. En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* . 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-27.png)

7. En este panel, deben comprobarse algunas opciones de configuración:

    1. En la pestaña **otros valores** :

        1. La **versión de scripting en tiempo de ejecución** debe ser **experimental (equivalente en net 4,6)** ; cambiar esto requerirá un reinicio del editor.
        2. El **back-end** de scripting debe ser **.net**
        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-28.png)
      
    2. En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        - **InternetClient**
        - **Micrófono**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-29.png)

    3. Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-30.png)

8.  De nuevo en la *configuración de compilación* , los proyectos de _Unity C#_  ya no están atenuados; Marque la casilla situada junto a este. 
9.  Cierre la ventana Configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).


## <a name="chapter-5--camera-setup"></a>Capítulo 5: configuración de cámara

> [!IMPORTANT]
> Si desea omitir el componente de *configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [paquete Azure-Mr-312-package. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe desde [ Capítulo 7](#chapter-7-–-create-the-botobjects-class).

1.  En el *Panel jerarquía*, seleccione la **cámara principal**. 
2.  Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel del inspector*.

    1. El **objeto de cámara** se debe llamar **cámara principal** (tenga en cuenta la ortografía)
    2. La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía)
    3. Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**
    4. Establezca **marcas** de borrado en **color sólido**.
    5. Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)**

    ![Configuración de la cámara](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capítulo 6: importar la biblioteca Newtonsoft

Para ayudarle a deserializar y serializar los objetos recibidos y enviados al servicio bot, debe descargar la biblioteca **Newtonsoft** . Aquí encontrará una [versión compatible que ya está organizada con la estructura de carpetas de Unity correcta](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que se incluía con este curso.

1.  Agregue el *. unitypackage Tools* a Unity **mediante la opción** > de menú de paquetes**importar paquete** > **personalizado** de paquetes.

    ![Importar la biblioteca Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  En el cuadro **importar paquete Unity** que aparece, asegúrese de que todo lo que hay en **Complementos** (y incluido) está seleccionado.

    ![Importar la biblioteca Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Haga clic en el botón **importar** para agregar los elementos al proyecto.

4.  Vaya a la carpeta **Newtonsoft** en **Complementos** en la vista de proyecto y seleccione el complemento Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Con el complemento Newtonsoft seleccionado, asegúrese de que **cualquier plataforma** esté desactivada, asegúrese de que **WSAPlayer** también está desactivado y haga clic en **aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Al marcar estos complementos, se configuran para que solo se usen en el editor de Unity. Hay un conjunto diferente de ellos en la carpeta WSA que se usará después de exportar el proyecto desde Unity.

6.  A continuación, debe abrir la carpeta **WSA** , dentro de la carpeta **Newtonsoft** Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector, asegúrese de que
    -   **Cualquier plataforma** está  desactivada 
    -   **solo** **WSAPlayer** está **activado**
    -   No **procesar** está **activado**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capítulo 7: creación de BotTag

1.  Cree un nuevo objeto de **etiqueta** denominado **BotTag**. Seleccione la cámara principal en la escena. Haga clic en el menú desplegable etiqueta en el panel Inspector. Haga clic en **Agregar etiqueta**.

    ![Configuración de la cámara](images/AzureLabs-Lab312-32.png)
 
2.  Haga clic en **+** el símbolo. Asigne a la nueva **etiqueta** el nombre **BotTag**, *Guardar*.

    ![Configuración de la cámara](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **No** aplique el **BotTag** a la cámara principal. Si ha hecho esto accidentalmente, asegúrese de volver a cambiar la etiqueta de cámara principal a *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Capítulo 8: creación de la clase BotObjects

El primer script que necesita crear es la clase **BotObjects** , que es una clase vacía creada para que se pueda almacenar una serie de otros objetos de clase en el mismo script y que otros scripts de la escena tengan acceso a ellos.

La creación de esta clase es puramente una opción arquitectónica, en su lugar, estos objetos se pueden hospedar en el script de bot que creará más adelante en este curso.

Para crear esta clase: 

1.  Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, **cree > carpeta**. Asigne a la carpeta el nombre scripts. 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab312-36.png)

2.  Haga doble clic en la  carpeta scripts para abrirla. Después, en esa carpeta, haga clic con el botón derecho y seleccione **crear > C# script**. Asigne al script el nombre **BotObjects**. 

3.  Haga doble clic en el nuevo script **BotObjects** para abrirlo con **Visual Studio**.

4.  Elimine el contenido del script y reemplácelo por el código siguiente:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-9--create-the-gazeinput-class"></a>Capítulo 9: creación de la clase GazeInput

La clase siguiente que va a crear es la clase **GazeInput** . Esta clase es responsable de:

- Crear un cursor que represente la *mirada* al jugador.
- Detección de objetos detectados por la mirada del reproductor y que contiene una referencia a los objetos detectados.

Para crear esta clase: 

1.  Vaya a la  carpeta scripts que creó anteriormente. 
2.  Haga clic con el botón derecho dentro de la carpeta, **cree > C# script**. Llame al script **GazeInput**. 
3.  Haga doble clic en el nuevo script **GazeInput** para abrirlo con **Visual Studio**.
4.  Inserte la siguiente línea justo encima del nombre de clase:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  A continuación, agregue las siguientes variables dentro de la clase **GazeInput** , sobre el método **Start ()** :

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Debe agregarse el código para el método **Start ()** . Se llamará cuando se inicialice la clase:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implemente un método que creará instancias y configurará el cursor de miración: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implemente los métodos que configurarán el Raycast desde la cámara principal y realizarán un seguimiento del objeto con el foco actual.

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-10--create-the-bot-class"></a>Capítulo 10: crear la clase bot

El script que va a crear ahora se llama **Bot**. Esta es la clase principal de la aplicación, que almacena: 

- Sus credenciales de bot de aplicación Web
- El método que recopila los comandos de voz de usuario.
- El método necesario para iniciar conversaciones con el bot de la aplicación Web 
- El método necesario para enviar mensajes al bot de la aplicación Web 

Para enviar mensajes al servicio bot, la corutina **SendMessageToBot ()** creará una actividad, que es un objeto reconocido por el marco bot como datos enviados por el usuario. 
 
Para crear esta clase: 

1. Haga doble clic en la  carpeta scripts para abrirla. 
2. Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**. Asigne al **Bot**el nombre de la secuencia de comandos. 
3. Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4. Actualice los espacios de nombres para que sean los mismos que los que se indican a continuación, en la parte superior de la clase **Bot** :

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Dentro de la clase **Bot** , agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Asegúrese de insertar la **clave de bot secreta** en la variable **botSecret** . Habrá anotado la **clave secreta de bot** al principio de este curso, en el  **[capítulo 2](#chapter-2---create-the-azure-bot-service), paso 10**.

7. Ahora es necesario agregar el código para el **activo ()** y el **Inicio ()** . 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Agregue los dos controladores a los que llaman las bibliotecas de voz cuando comienza y finaliza la captura de voz. *DictationRecognizer* dejará de capturar automáticamente la voz de usuario cuando el usuario deje de hablar.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. El siguiente controlador recopila el resultado de la entrada de voz de usuario y llama a la corutina responsable de enviar el mensaje a Web App bot Service.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. Se llama a la siguiente corutina para iniciar una conversación con el bot. Observará que una vez completada la llamada de conversación, llamará a **SendMessageToCoroutine ()** pasando una serie de parámetros que establecerán la actividad que se va a enviar al servicio bot como un mensaje vacío. Esto se hace para pedir al servicio de bot que inicie el cuadro de diálogo.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. Se llama a la siguiente corutina para compilar la actividad que se va a enviar al servicio bot. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. Se llama a la siguiente corutina para solicitar una respuesta después de enviar una actividad al servicio bot. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. El último método que se va a agregar a esta clase es necesario para mostrar el mensaje en la escena:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > Es posible que vea un error en la consola del editor de Unity, sobre la falta de la clase **SceneOrganiser** . Pase por alto este mensaje, ya que creará esta clase más adelante en el tutorial.

14.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Capítulo 11: crear la clase Interactions

La clase que va a crear ahora se denomina **interacciones**. Esta clase se usa para detectar la entrada de la pulsación de HoloLens del usuario. 

Si el usuario pulsa mientras mira el objeto *Bot* en la escena y el bot está listo para escuchar las entradas de voz, el objeto bot cambiará el color a **rojo** y comenzará a escuchar las entradas de voz. 

Esta clase hereda de la clase **GazeInput** y, por lo tanto, puede hacer referencia al método **Start ()** y a las variables de esa clase, que se indican mediante el uso de **base**. 
 
Para crear esta clase:

1.  Haga doble clic en la  carpeta scripts para abrirla. 
2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**. Asigne un nombre a las interacciones del script. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres y la herencia de clases para que sea igual que la siguiente, en la parte  superior de la clase Interactions:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Dentro de  la clase Interactions, agregue la siguiente variable:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  A continuación, agregue el método **Start ()** :

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Agregar el controlador que se desencadenará cuando el usuario realice el gesto de TAP delante de la cámara HoloLens

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capítulo 12: creación de la clase SceneOrganiser

La última clase requerida en este laboratorio se denomina **SceneOrganiser**. Esta clase configurará la escena mediante programación, agregando componentes y scripts a la cámara principal y creando los objetos adecuados en la escena.
 
Para crear esta clase:

1.  Haga doble clic en la  carpeta scripts para abrirla. 
2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**. Asigne al script el nombre **SceneOrganiser**. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Dentro de la clase **SceneOrganiser** , agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  A continuación, agregue los métodos **activo ()** e **Inicio ()** :

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Agregue el método siguiente, responsable de crear el objeto bot en la escena y configurar los parámetros y componentes:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Agregue el método siguiente, responsable de crear el objeto de interfaz de usuario en la escena, que representa las respuestas del bot:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.
9.  En el editor de Unity, arrastre el script **SceneOrganiser** desde la carpeta scripts a la cámara principal. El componente de organizador de escenas debe aparecer ahora en el objeto de cámara principal, como se muestra en la imagen siguiente.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capítulo 13: antes de compilar

Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.
Antes de hacerlo, asegúrese de que:

-   Toda la configuración mencionada en el [**capítulo 4**](#Chapter-4-–-Set-up-the-unity-project) se establece correctamente. 
-   El script **SceneOrganiser** se adjunta al objeto de **cámara principal** . 
-   En la clase **Bot** , asegúrese de que ha insertado la **clave de bot secreta** en la variable **botSecret** .

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capítulo 14: compilar y transferir localmente a HoloLens

Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.

1.  Vaya a **configuración de compilación**, **archivo > configuración de compilación.** .
2.  En la ventana **configuración de compilación** , haga clic en compilar.

    ![Compilar la aplicación desde Unity](images/AzureLabs-Lab312-38.png)

3.  Si aún no lo está, marque los **proyectos de Unity C#** .
4.  Haz clic en **Compilación**. Unity iniciará una ventana del **Explorador de archivos** , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y asígnele el nombre **App**. Después, con la carpeta de la **aplicación** seleccionada, haga clic en **Seleccionar carpeta**. 
5.  Unity comenzará a compilar el proyecto en la carpeta de la **aplicación** . 
6.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-15--deploy-to-hololens"></a>Capítulo 15: implementación en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de HoloLens (para la implementación remota) y para asegurarse de que HoloLens está en **modo de desarrollador**. Para ello:

    1. Mientras se contenga HoloLens, abra la **configuración**.
    2. Vaya a **Network & Internet > Wi-Fi > opciones avanzadas** .
    3. Anote la dirección **IPv4** .
    4. A continuación, vuelva a **configuración**y, a continuación, **actualice & seguridad > para desarrolladores** 
    5. Establezca el modo de Desarrollador en.

2.  Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.
3.  En la **configuración de soluciones** , seleccione Depurar.
4.  En la **plataforma**de la solución, seleccione **x86**, **equipo remoto**. 

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Vaya al **menú** compilar y haga clic en **implementar solución**para transferir localmente la aplicación a HoloLens.
6.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.

    > [!NOTE]
    > Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local*y establezca la **configuración** en depurar, con  *x86* como **plataforma**. A continuación, implemente en el equipo local, mediante el **menú**compilar, seleccionando *implementar solución*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capítulo 16: uso de la aplicación en HoloLens

- Una vez que haya iniciado la aplicación, verá el bot como una esfera azul delante de usted.

- Use el **gesto de TAP** mientras está Gazing en la esfera para iniciar una conversación. 
 
- Espere a que se inicie la conversación (la interfaz de usuario mostrará un mensaje cuando se produzca). Una vez que reciba el mensaje introductorio del bot, pulse de nuevo en el bot para que se vuelva rojo y empiece a escuchar la voz. 

- Una vez que haya dejado de hablar, la aplicación enviará el mensaje al bot y recibirá una respuesta que se mostrará en la interfaz de usuario. 

- Repita el proceso para enviar más mensajes a su Bot (debe puntear cada vez que desee enviar un mensaje).

Esta conversación muestra cómo el bot puede conservar la información (su nombre), a la vez que proporciona información conocida (como los elementos que están almacenados en existencias).

#### <a name="some-questions-to-ask-the-bot"></a>Algunas preguntas para preguntar al bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Su aplicación Web App Bot (v4) finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el bot de aplicaciones Web de Azure, Microsoft bot Framework V4.

![Producto final](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

La estructura de conversación de este laboratorio es muy básica. Utilice Microsoft LUIS para ofrecer capacidades de comprensión del lenguaje natural de bot.

### <a name="exercise-2"></a>Ejercicio 2

En este ejemplo no se incluye la finalización de una conversación y el reinicio de una nueva. Para que la característica de bot se complete, intente implementar el cierre de la conversación.
