---
title: El Sr. y 312 Azure - integración de Bot
description: Complete este curso para obtener información sobre cómo crear e implementar un bot mediante Microsoft Bot Framework v4 y comunicarse con él en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, computer vision o hololens, vr envolventes, microsoft bot framework v4, bot de web Apps, framework bot, bot de microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605760"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

# <a name="mr-and-azure-312-bot-integration"></a>El Sr. y Azure 312: Integración de bot

En este curso, obtendrá información sobre cómo crear e implementar un bot mediante el V4 de Microsoft Bot Framework y comunicarse con él a través de una aplicación de Windows Mixed Reality. 

![](images/AzureLabs-Lab312-00.png)

El **Microsoft Bot Framework V4** es un conjunto de API diseñadas para ofrecer a los desarrolladores las herramientas necesarias para crear un bot escalable y extensible application. Para obtener más información, visite la [página Microsoft Bot Framework](https://dev.botframework.com/) o [V4 repositorio](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Después de completar este curso, habrá creado una aplicación Windows Mixed Reality, que podrá hacer lo siguiente:

1. Use un **gesto de pulsar** para iniciar el bot a la escucha de la voz de los usuarios.
2. Cuando el usuario indicaba un mensaje, el bot intentará proporcionar una respuesta.
3. Muestra la respuesta de los bots como texto, situado cerca de bot, en la escena de Unity.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 312: Integración de bot</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality. Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC. Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK más reciente de Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Acceso a Internet para Azure y para la recuperación de Azure Bot. Para obtener más información, [, siga este vínculo](https://dev.botframework.com/).

### <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
2.  Configurar y probar su HoloLens. Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar dichas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Capítulo 1: crear la aplicación Bot

El primer paso es crear un bot como aplicación Web de ASP.Net Core local. Una vez que haya finalizado y probado, se publicará en el Portal de Azure.

1.  Abra Visual Studio. Crear un nuevo proyecto, seleccione **aplicación Web de ASP NET Core** como el tipo de proyecto (lo encontrará en la subsección .NET Core) y llámelo **MyBot**. Haga clic en **Aceptar**.

2.  En la ventana que va a aparecer seleccione **vacía**. También asegúrese de que el destino se establece en **ASP NET Core 2.0** y la autenticación se establece en **sin autenticación**. Haga clic en **Aceptar**.  

    ![Crear la aplicación bot](images/AzureLabs-Lab312-01.png)

3.  Ahora se abrirá la solución. Haga doble clic en la solución **Mybot** en el **el Explorador de soluciones** y haga clic en **administrar paquetes de NuGet para la solución**. 

    ![Crear la aplicación Bot](images/AzureLabs-Lab312-02.png)

4.  En el **examinar** pestaña, busque **Microsoft.Bot.Builder.Integration.AspNet.Core** (asegúrese de tener **incluir versión preliminar** activada). Seleccione la versión del paquete **4.0.1-Preview**y marque las casillas de proyecto. A continuación, haga clic en **instalar**. Ahora ha instalado las bibliotecas necesarias para la **Bot Framework v4**. Cierre la página de NuGet.

    ![Crear la aplicación bot](images/AzureLabs-Lab312-03.png)

5.  Haga doble clic en su *proyecto*, **MyBot**, en el **el Explorador de soluciones** y haga clic en **agregar** **|** **Clase**.

    ![Crear la aplicación Bot](images/AzureLabs-Lab312-04.png)

6.  Nombre de la clase **MyBot** y haga clic en **agregar**.

    ![Crear la aplicación bot](images/AzureLabs-Lab312-05.png)

7.  Repita el punto anterior, para crear otra clase denominada **ConversationContext**. 

8.  Haga doble clic en **wwwroot** en el **el Explorador de soluciones** y haga clic en **agregar** **|** **denuevoelemento**. Seleccione **página HTML** (lo encontrará en la subsección Web). Nombre del archivo **default.html**. Haz clic en **Agregar**.

    ![Crear la aplicación bot](images/AzureLabs-Lab312-06.png)

9.  La lista de clases y objetos en el **el Explorador de soluciones** debería ser similar a la imagen siguiente.

    ![Crear la aplicación bot](images/AzureLabs-Lab312-07.png)

10. Haga doble clic en el **ConversationContext** clase. Esta clase es responsable de almacenar las variables utilizadas por el bot para mantener el contexto de la conversación. Estos valores de contexto de la conversación se mantienen en una instancia de esta clase, porque cualquier instancia de la **MyBot** clase actualizará cada vez que se recibe una actividad. Agregue el código siguiente a la clase:

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

11. Haga doble clic en el **MyBot** clase. Esta clase va a hospedar los controladores que se llama a cualquier actividad entrante del cliente. En esta clase se agregará el código usado para crear la conversación entre el bot y el cliente. Como se mencionó anteriormente, una instancia de esta clase se inicializa cada vez que se recibe una actividad. Agregue el código siguiente a esta clase:

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

12. Haga doble clic en el **inicio** clase. Esta clase inicializará el bot. Agregue el código siguiente a la clase:

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

13. Abra el **programa** archivo de clase y compruebe el código en él es igual a lo siguiente:

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

14. No olvide guardar los cambios, para ello, vaya a **archivo** > **guardar todo**, desde la barra de herramientas en la parte superior de Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capítulo 2: crear el servicio de Azure Bot

Ahora que ha creado el código para el bot, tiene que publicarla en una instancia de la *Bot de Web Apps* servicio, en el Portal de Azure. Este capítulo le mostrará cómo crear y configurar el servicio Bot en Azure y, a continuación, publicar el código en él.

1.  En primer lugar, inicie sesión en el Portal de Azure (https://portal.azure.com). 

    1. Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda esquina y busque *bot de aplicación Web*y haga clic en **ENTRAR**.

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  La nueva página proporcionará una descripción de la *Bot de Web Apps* Service. En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  Una vez que ha hecho clic **crear**:

    1. Insertar el elemento **nombre** para esta instancia de servicio.
    2. Seleccione un **suscripción**.
    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, [, siga este vínculo](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. Determinar la ubicación del grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    5. Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *Bot de Web Apps* servicio, un nivel gratuito (denominado F0) debe estar disponible para usted
    6. **Nombre de la aplicación** sólo se puede dejar el mismo que el *nombre Bot*. 
    7. Deje el *plantilla Bot* como **básica (C#)**.
    8. *Plan de App service/ubicación* debería haber sido rellenados automáticamente para su cuenta.
    9. Establecer el **Azure Storage** que desea usar para hospedar su Bot. Si no tiene uno ya, puede crear aquí.
    10. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    11. Haga clic en crear.
 
        ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-10.png)

5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el Portal.

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia del servicio de Azure. 

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  En este momento debe configurar una característica denominada **línea directa** para permitir que la aplicación cliente para comunicarse con este servicio de bots. Haga clic en **canales**, a continuación, en el **agregar un canal destacado** sección, haga clic en **canal de línea directa configurar**.

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-14.png)

10. En esta página encontrará el **claves secretas** que permitirá que la aplicación cliente se autentique con el bot. Haga clic en el **mostrar** botón y realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto. 

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capítulo 3: publicar el Bot en el servicio Bot de aplicación Web de Azure

Ahora que el servicio está listo, deberá publicar el código de Bot, que creó anteriormente, a su servicio de Bot de aplicación Web recién creada.

> [!NOTE] 
> Tendrá que publicar su Bot en el servicio de Azure cada vez que realice cambios en la solución de Bot / código.

1.  Vuelva a la solución de Visual Studio que creó anteriormente. 
2.  Haga doble clic en su **MyBot** del proyecto, en el **el Explorador de soluciones**, a continuación, haga clic en **publicar**.

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-16.png)

3.  En el *elegir un destino de publicación* página, haga clic en **App Service**, a continuación, **seleccionar existente**, por último, haga clic en **Crear perfil** (es posible que deba Haga clic en la flecha desplegable junto a la *publicar* button, si esto no está visible).

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-17.png)

4. Si están aún no iniciaron sesión en su Account de Microsoft, deberá hacerlo aquí.
5. En el **publicar** página encontrará tendrá que establecer el mismo **suscripción** que usó para la *Bot de Web Apps* la creación del servicio. A continuación, establezca el **vista** como **grupo de recursos** y, en la lista desplegable de la estructura de carpetas, seleccione el **grupo de recursos** creado anteriormente. Haga clic en **Aceptar**. 

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-18.png)

6.  Ahora haga clic en el **publicar** botón y espere a que el Bot a publicarse (podría tardar unos minutos).

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capítulo 4: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **New**. 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-20.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Insertar **Hololens Bot**. Asegúrese de que la plantilla de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-21.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-22.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-23.png)

5.  Mientras sigue en **archivo > configuración de compilación** y asegúrese de que:

    1.  **Dispositivo de destino** está establecido en **Hololens**

        > Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.

    2.  **Tipo de compilación** está establecido en **D3D**

    3.  **SDK** está establecido en **instalada más reciente**

    4.  **Versión de Visual Studio** está establecido en **instalada más reciente**

    5.  **Compilar y ejecutar** está establecido en **máquina Local**

    6.  Guarde la escena y agregarlo a la compilación. 

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.
        
            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-24.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

             ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-25.png)

        3. Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **BotScene**, a continuación, haga clic en **guardar**.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-26.png)

    7. El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.

6. En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra. 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-27.png)

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1. En el **otra configuración** pestaña:

        1. **Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental (NET 4.6 equivalente)**; cambiar esto requerirá un reinicio del Editor.
        2. **Scripting de back-end** debe ser **.NET**
        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-28.png)
      
    2. Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        - **InternetClient**
        - **Micrófono**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-29.png)

    3. Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-30.png)

8.  En *configuración de compilación* _Unity C#_  proyectos ya no está atenuada; Marque la casilla situada junto a esto. 
9.  Cierre la ventana de configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).


## <a name="chapter-5--camera-setup"></a>Capítulo 5: configuración de cámara

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [Package.unitypackage-Azure-MR-312](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 7](#chapter-7-–-create-the-botobjects-class).

1.  En el *panel jerarquía*, seleccione el **cámara principal**. 
2.  Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel Inspector*.

    1. El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía)
    2. La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía)
    3. Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**
    4. Establecer **borrar las marcas de** a **Color sólido**.
    5. Establecer el **en segundo plano** Color del componente de cámara para **negro, alfa de 0 (código hexadecimal: #00000000)**

    ![Configuración de cámara](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capítulo 6: importar la biblioteca de Newtonsoft

Para ayudarle a deserializan y serializan objetos recibidos y enviados al servicio Bot debe descargar el **Newtonsoft** biblioteca. Encontrará un [versión compatible ya organizado con la correcta Unity estructura de carpetas aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que acompaña a este curso.

1.  Agregar el *.unitypackage* a Unity mediante el uso de la **activos** > **Importar paquete** > **paquete personalizado** opción de menú.

    ![Importación de la biblioteca de Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.

    ![Importación de la biblioteca de Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Haga clic en el **importación** para agregar los elementos al proyecto.

4.  Vaya a la **Newtonsoft** carpeta bajo **complementos** en la vista de proyecto y seleccione el complemento de Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Con el complemento de Newtonsoft seleccionado, asegúrese de que **cualquier plataforma** es **unchecked**, a continuación, asegúrese de que **WSAPlayer** también es **unchecked**, a continuación, haga clic en **aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Marcar estos complementos configura para su uso en el Editor de Unity. Hay un conjunto diferente de ellos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.

6.  A continuación, deberá abrir el **WSA** carpeta, en el **Newtonsoft** carpeta. Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector, asegúrese de que
    -   **Cualquier plataforma** es **desactivada** 
    -   **solo** **WSAPlayer** es **activada**
    -   **No procesar** es **activada**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capítulo 7: crear el BotTag

1.  Cree un nuevo **etiqueta** objeto llamado **BotTag**. Seleccione la cámara principal de la escena. Haga clic en el menú en el panel del Inspector desplegable etiqueta. Haga clic en **Agregar etiqueta**.

    ![Configuración de cámara](images/AzureLabs-Lab312-32.png)
 
2.  Haga clic en el **+** símbolos. El nombre del nuevo **etiqueta** como **BotTag**, *guardar*.

    ![Configuración de cámara](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **No** aplicar el **BotTag** a la cámara principal. Si accidentalmente lo ha hecho, no olvide cambiar la cámara principal al etiqueta *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Capítulo 8: crear la clase BotObjects

Es el primer script, deberá crear el **BotObjects** (clase), que es una clase vacía que se crean de modo que se puede almacenar una serie de otros objetos de clase dentro de la misma secuencia de comandos y el acceso a otros scripts de la escena.

La creación de esta clase es puramente una opción de arquitectura, estos objetos podrían hospedarse en su lugar en el script de Bot que creará más adelante en este curso.

Para crear esta clase: 

1.  Haga clic en el *panel proyecto*, a continuación, **crear > carpeta**. Nombre de la carpeta **Scripts**. 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab312-36.png)

2.  Haga doble clic en el **Scripts** carpeta para abrirla. A continuación, dentro de esa carpeta, contextual y seleccione **crear > C# Script**. Nombre de la secuencia de comandos **BotObjects**. 

3.  Haga doble clic en el nuevo **BotObjects** script para abrirlo con **Visual Studio**.

4.  Elimine el contenido de la secuencia de comandos y reemplazarlo por el código siguiente:

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

## <a name="chapter-9--create-the-gazeinput-class"></a>Capítulo 9: crear la clase GazeInput

La siguiente clase que se va a crear es la **GazeInput** clase. Esta clase es responsable de:

- Creación de un cursor que representará el *que mirar* del Reproductor.
- Detección de objetos que se vea afectados por la mirada del Reproductor y que contiene una referencia a objetos detectados.

Para crear esta clase: 

1.  Vaya a la **Scripts** carpeta que creó anteriormente. 
2.  Haga clic en la carpeta, **crear > C# Script**. Llame al script **GazeInput**. 
3.  Haga doble clic en el nuevo **GazeInput** script para abrirlo con **Visual Studio**.
4.  Inserte la siguiente línea justo encima del nombre de clase:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  A continuación, agregue las siguientes variables dentro de la **GazeInput** clase encima el **Start()** método:

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

6.  El código para **Start()** se debe agregar el método. Se llamará cuando se inicializa la clase:

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

7.  Implementar un método que va a crear una instancia y el cursor mirada de instalación: 

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

8.  Implemente los métodos que le permitirán configurar el Raycast desde la cámara principal y realizará el seguimiento del objeto foco actual.

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

## <a name="chapter-10--create-the-bot-class"></a>Capítulo 10: crear la clase de Bot

El script que se va a crear ahora se llama **Bot**. Esta es la clase principal de la aplicación, almacena: 

- Las credenciales de Bot de Web Apps
- El método que se recopilan en los comandos de voz del usuario
- El método necesario iniciar conversaciones con el Bot de aplicación Web 
- El método necesario enviar mensajes a su Bot de aplicación Web 

Para enviar mensajes a Bot Service, el **SendMessageToBot()** corrutina creará una actividad, que es un objeto de Bot Framework reconocido como datos enviados por el usuario. 
 
Para crear esta clase: 

1. Haga doble clic en el **Scripts** carpeta para abrirla. 
2. Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos **Bot**. 
3. Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4. Actualice los espacios de nombres para que sea igual a lo siguiente en la parte superior de la **Bot** clase:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Dentro de la **Bot** clase agregue las siguientes variables:

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
    > Asegúrese de insertar el **clave secreta de Bot** en el **botSecret** variable. Habrá anotó la **clave secreta de Bot** al principio de este curso, en  **[capítulo 2](#chapter-2---create-the-azure-bot-service), paso 10**.

7. El código para **Awake()** y **Start()** ahora debe agregarse. 

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

8. Agregue los dos controladores que se llama a las bibliotecas de voz cuando la captura de voz comienza y termina. El *DictationRecognizer* automáticamente dejará de capturar la voz del usuario cuando el usuario deja de habla.

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

1. El siguiente controlador recopila el resultado de la entrada de voz del usuario y llama a la corrutina responsable de enviar el mensaje al servicio de Bot de aplicación Web.

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

10. Se llama a la corrutina siguiente para iniciar una conversación con el Bot. Observará que una vez completada la llamada de la conversación, llamará el **SendMessageToCoroutine()** pasando una serie de parámetros que se establecerá la actividad para enviarse al servicio Bot como un mensaje vacío. Esto sirve para solicitar el servicio de bots para iniciar el cuadro de diálogo.

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

11. Se llama a la corrutina siguiente para crear la actividad para enviarse al servicio de bots. 

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

12. La corrutina siguiente se llama para solicitar una respuesta después de enviar una actividad para el servicio Bot. 

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

13. El último método que se agregarán a esta clase, es necesario para mostrar el mensaje de la escena:

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
    > Verá un error en la consola Editor de Unity, falta la **SceneOrganiser** clase. Pasar por alto este mensaje, ya que creará esta clase más adelante en el tutorial.

14.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Capítulo 11: crear la clase interacciones

La clase que se va a crear ahora se denomina **interacciones**. Esta clase se utiliza para detectar la HoloLens pulse entrada del usuario. 

Si el usuario puntea al examinar el *Bot* objeto en la escena y el Bot está listo para realizar escuchas para las entradas de voz, el objeto de Bot cambiará de color a **rojo** y empezar a escuchar las entradas de voz. 

Esta clase hereda de la **GazeInput** clase por lo que es capaz de hacer referencia a la **Start()** método y variables de esa clase, que se indica mediante el uso de **base**. 
 
Para crear esta clase:

1.  Haga doble clic en el **Scripts** carpeta para abrirla. 
2.  Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos **interacciones**. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres y la herencia de clases para ser el mismo que el siguiente, en la parte superior de la **interacciones** clase:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Dentro de la **interacciones** clase agregue la siguiente variable:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  A continuación, agregue el **Start()** método:

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

7.  Agregue el controlador que se desencadena cuando el usuario realiza el gesto de pulsar delante de la cámara de HoloLens

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

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capítulo 12: crear la clase SceneOrganiser

Se llama a la última clase necesaria en este laboratorio **SceneOrganiser**. Esta clase configurará la escena mediante programación, agregando componentes y las secuencias de comandos a la cámara principal, y crear los objetos adecuados en la escena.
 
Para crear esta clase:

1.  Haga doble clic en el **Scripts** carpeta para abrirla. 
2.  Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos **SceneOrganiser**. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Dentro de la **SceneOrganiser** clase agregue las siguientes variables:

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

6.  A continuación, agregue el **Awake()** y **Start()** métodos:

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

7.  Agregue el siguiente método, responsable de crear el objeto de Bot en la escena y la configuración de los parámetros y los componentes:

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

7.  Agregue el siguiente método, responsable de crear el objeto de interfaz de usuario de la escena, que representa las respuestas del Bot:

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
9.  En el Editor de Unity, arrastre el **SceneOrganiser** script desde la carpeta de Scripts a la cámara principal. El componente de la escena organizador debería aparecer ahora en el objeto de cámara principal, como se muestra en la imagen siguiente.

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capítulo 13: antes de compilar

Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.
Antes de hacerlo, asegúrese de que:

-   Todas las configuraciones que se mencionan en la [ **Chapter 4** ](#Chapter-4-–-Set-up-the-unity-project) están establecidas correctamente. 
-   La secuencia de comandos **SceneOrganiser** está asociado a la **cámara principal** objeto. 
-   En el **Bot** class, asegúrese de que haya insertado el **clave secreta de Bot** en el **botSecret** variable.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capítulo 14: compilación y transfiérala localmente para el HoloLens

Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.

1.  Vaya a **configuración de compilación**, **archivo > configuración de compilación...** .
2.  Desde el **configuración de compilación** ventana, haga clic en **compilar**.

    ![Creación de la aplicación de Unity](images/AzureLabs-Lab312-38.png)

3.  Si aún no marque **Unity C# proyectos**.
4.  Haz clic en **Compilación**. Unity se iniciará un **Explorador de archivos** ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta y asígnele el nombre **aplicación**. A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**. 
5.  Unity empezará a compilar el proyecto para el **aplicación** carpeta. 
6.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

## <a name="chapter-15--deploy-to-hololens"></a>Capítulo 15: implementar en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador**. Para ello:

    1. Mientras que el exceso de su HoloLens, abra el **configuración**.
    2. Vaya a **red e Internet > Wi-Fi > Opciones avanzadas**
    3. Tenga en cuenta la **IPv4** dirección.
    4. A continuación, vaya a **configuración**y, a continuación, para **actualización y seguridad > para desarrolladores** 
    5. Activar el modo de programador.

2.  Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.
3.  En el **configuración de la solución** seleccione **depurar**.
4.  En el **plataforma de solución**, seleccione **x86**, **máquina remota**. 

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Vaya a la **menú compilar** y haga clic en **implementar solución**, para transferir localmente la aplicación a su HoloLens.
6.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.

    > [!NOTE]
    > Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**. Implementar, a continuación, en el equipo local machine, utilizando el **menú compilar**, seleccionar *implementar solución*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capítulo 16: uso de la aplicación en el HoloLens

- Una vez que haya iniciado la aplicación, verá el Bot como una esfera azul delante de usted.

- Use la **gesto de pulsar** mientras se gazing en la esfera para iniciar una conversación. 
 
- Espere a que la conversación iniciar (la interfaz de usuario se mostrará un mensaje cuando ocurre). Una vez que reciba un mensaje de la introducción del Bot, pulse de nuevo en el Bot para que se vuelven de color rojo y empezar a escuchar su voz. 

- Una vez detenido hablando, la aplicación enviará el mensaje al Bot y con prontitud recibirán una respuesta que se mostrará en la interfaz de usuario. 

- Repita el proceso para enviar más mensajes a su Bot (que tiene que puntear en cada vez que desee enviar un mensaje).

Esta conversación, muestra cómo el Bot pueda conservar la información (su nombre), mientras que también proporciona la información conocida (por ejemplo, los elementos que se almacenó).

#### <a name="some-questions-to-ask-the-bot"></a>Algunas preguntas para formular el Bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>La aplicación finalizada de Bot de Web Apps (v4)

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el Bot de aplicación Web de Azure, Microsoft Bot Framework v4.

![Final producto](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

La estructura de la conversación en este laboratorio es muy básica. Uso de LUIS de Microsoft para proporcionar capacidades de comprensión de lenguaje natural a su bot.

### <a name="exercise-2"></a>Ejercicio 2

En este ejemplo no incluyen finalizar una conversación y el reinicio de una nueva. Para hacer que el Bot que todas las características, intente implementar el cierre para la conversación.
