---
title: El Sr. y 311 - Microsoft Graph de Azure
description: Realice este curso para obtener información sobre cómo aprovechar Microsoft Graph y conectarse a los datos que impulsan la productividad, dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, graph de microsoft, hololens, envolventes, vr
ms.openlocfilehash: 98fe2c872f332a21fff3af6751ae555968073a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597658"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

# <a name="mr-and-azure-311---microsoft-graph"></a>El Sr. y 311 - Microsoft Graph de Azure

En este curso, obtendrá información sobre cómo usar *Microsoft Graph* para iniciar sesión en tu cuenta Microsoft con autenticación segura dentro de una aplicación de realidad mixta. A continuación, recuperará y mostrar sus reuniones programadas en la interfaz de la aplicación.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* es un conjunto de API que se ha diseñado para permitir el acceso a muchos de los servicios de Microsoft. Microsoft describe Microsoft Graph como una matriz de los recursos conectados mediante relaciones, lo que significa que permite que una aplicación tener acceso a todo tipo de datos de usuario conectado. Para obtener más información, visite la [página de Microsoft Graph](https://developer.microsoft.com/graph).

Desarrollo incluirá la creación de una aplicación donde el usuario le indicará que mire y, a continuación, puntee en una esfera, que se le pedirá al usuario que inicie sesión con seguridad en una cuenta de Microsoft. Una vez que inicia sesión en su cuenta, el usuario podrá ver una lista de las reuniones programadas para el día.

Una vez completado este curso, tendrá una realidad mixta HoloLens aplicación, que podrá hacer lo siguiente:

1.  Con el gesto de pulsar, puntee en un objeto que se le pedirá al usuario iniciar sesión en un Account de Microsoft (sale de la aplicación para iniciar sesión y, a continuación, volver a la aplicación).
2.  Ver una lista de las reuniones programadas para el día. 

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y 311 de Azure: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK más reciente de Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Acceso a Internet para el programa de instalación de Azure y la recuperación de datos de Microsoft Graph
- Válido **Account Microsoft** (personal o profesional o educativa)
- Algunas reuniones programadas para el día actual, con la misma Account de Microsoft

### <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
2.  Configurar y probar su HoloLens. Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Capítulo 1: crear la aplicación en el Portal de registro de aplicación

Para empezar, deberá crear y registrar la aplicación en el **Portal de registro de aplicación**.

En este capítulo también encontrará la clave de servicio que le permitirá realizar llamadas a *Microsoft Graph* para tener acceso a su contenido de la cuenta.

1.  Navegue hasta la [Portal de registro de aplicaciones de Microsoft](https://apps.dev.microsoft.com) e inicie sesión con su Account de Microsoft. Una vez que haya iniciado sesión, se le redirigirá a la **Portal de registro de aplicación**.

2.  En el **mis aplicaciones** sección, haga clic en el botón **agregar una aplicación**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > El **Portal de registro de aplicación** puede parecer diferente, dependiendo de si ha trabajado previamente con *Microsoft Graph*. Las siguientes capturas de pantalla muestra las distintas versiones.

3.  Agregue un nombre para la aplicación y haga clic en **crear**.

    ![](images/AzureLabs-Lab311-03.png)

4.  Una vez creada la aplicación, se le redirigirá a la página principal de la aplicación. Copia el **Id. de aplicación** y asegúrese de que tener en cuenta este valor en un lugar seguro, se usará pronto en el código.

    ![](images/AzureLabs-Lab311-04.png)

5.  En el **plataformas** sección, asegúrese de que **aplicación nativa** se muestra. Si *no* haga clic en **Agregar plataforma** y seleccione **aplicación nativa**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Desplácese hacia abajo en la misma página y en la sección denominada **permisos de Microsoft Graph** deberá agregar permisos adicionales para la aplicación. Haga clic en **agregar** junto a **permisos delegados**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Puesto que desea que su aplicación tenga acceso al calendario del usuario, active la casilla denominada **Calendars.Read** y haga clic en **Aceptar**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Desplácese hacia abajo y haga clic en el **guardar** botón.

    ![](images/AzureLabs-Lab311-08.png)

9.  Se confirmará la de guardar y cerrar desde la **Portal de registro de aplicación**.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **New**.

    ![](images/AzureLabs-Lab311-09.png)

2.  Deberá proporcionar un nombre de proyecto de Unity. Insertar **MSGraphMR**. Asegúrese de que la plantilla de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![](images/AzureLabs-Lab311-11.png)

4.  Vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.

    ![](images/AzureLabs-Lab311-12.png)

5.  Mientras sigue en **archivo > configuración de compilación**, asegúrese de que:

    1. **Dispositivo de destino** está establecido en **HoloLens**
    2. **Tipo de compilación** está establecido en **D3D**
    3. **SDK** está establecido en **instalada más reciente**
    4. **Versión de Visual Studio** está establecido en **instalada más reciente**
    5. **Compilar y ejecutar** está establecido en **máquina Local**
    6. Guarde la escena y agregarlo a la compilación.

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![](images/AzureLabs-Lab311-13.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena. Seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_ComputerVisionScene**, a continuación, haga clic en **guardar** .

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity. Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.

    7.  El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.

6.  En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra. 

    ![](images/AzureLabs-Lab311-16.png)

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1. En el **otra configuración** pestaña:

        1.  **Scripting** **en tiempo de ejecución versión** debe ser **Experimental** (.NET 4.6 equivalente), que desencadenará una necesidad de reiniciar el Editor.

        2. **Scripting de back-end** debe ser **.NET**

        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), compruebe **admite la realidad Virtual**, asegúrese de que el **Windows Mixed Reality SDK** se agrega.

        ![](images/AzureLabs-Lab311-19.png)

8.  En *configuración de compilación*, *Unity C# proyectos* ya no está atenuada; Active la casilla situada junto a esto.

9.  Cerrar la *configuración de compilación* ventana.

10.  Guarde la escena y el proyecto (**archivo > Guardar ESCENAS / archivo > Guardar proyecto**).

## <a name="chapter-3---import-libraries-in-unity"></a>Capítulo 3: las bibliotecas de importación en Unity

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [MR-Azure-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5---create-meetingsui-class).

Para usar *Microsoft Graph* Unity es preciso que el uso de la **Microsoft.Identity.Client** DLL. Es posible usar el SDK de Microsoft Graph, sin embargo, requerirá la adición de un paquete NuGet después de compilar el proyecto de Unity (es decir, la posterior a la compilación del proyecto de edición). Se considera más sencillo importar los archivos DLL necesarios directamente en Unity.

> [!NOTE]
> Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación. Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.

Para importar *Microsoft Graph* en su propio proyecto, [descargar el archivo MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Este paquete se creó con las versiones de las bibliotecas que se han probado.

Si desea obtener más información acerca de cómo agregar archivos DLL personalizado a su proyecto de Unity, [siga este vínculo](https://docs.unity3d.com/Manual/UsingDLL.html).

Para importar el paquete:

1.  Agregar el paquete de Unity para Unity mediante el **activos* > *Importar paquete* > *paquete personalizado** opción de menú. Seleccione el paquete que acaba de descargar.

2.  En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.

    ![](images/AzureLabs-Lab311-20.png)

3.  Haga clic en el **importación** para agregar los elementos al proyecto.

4.  Vaya a la **MSGraph** carpeta bajo **complementos** en el *Panel proyecto* y seleccione el complemento llamado **Microsoft.Identity.Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  Con el *complemento* seleccionado, asegúrese de que **cualquier plataforma** está desactivada y, después, asegúrese de que **WSAPlayer** también está desactivada y, después, haga clic en **aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Marcar estos complementos configura para su uso en el Editor de Unity. Hay un conjunto diferente de DLL en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity como una aplicación Universal de Windows.

6.  A continuación, deberá abrir el **WSA** carpeta, en el **MSGraph** carpeta. Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector:

    -   Asegúrese de que **cualquier plataforma** es **unchecked**y que **sólo** **WSAPlayer** es **comprueban**.

    -   Asegúrese de **SDK** está establecido en **UWP**, y **back-end de Scripting** está establecido en **Dot Net**

    -   Asegúrese de que **no procesar** es **comprueban**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Haga clic en **Aplicar**.

## <a name="chapter-4---camera-setup"></a>Capítulo 4: configuración de cámara

Durante este capítulo se configurará la cámara principal de la escena:

1.  En el *jerarquía Panel*, seleccione el **cámara principal**.

2.  Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *Inspector* panel.

    1.  El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía!)

    2.  La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)

    3.  Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**

    4.  Establecer **borrar las marcas de** a **Color sólido**

    5.  Establecer el **Color de fondo** del componente de cámara para **negro, alfa 0** **(Hex código: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  La estructura del objeto final en el *jerarquía Panel* debe ser como se muestra en la imagen siguiente:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Capítulo 5: crear la clase MeetingsUI

Es el primer script, deberá crear **MeetingsUI**, que es responsable del hospedaje y rellenar la interfaz de usuario de la aplicación (mensaje de bienvenida, instrucciones y los detalles de las reuniones).

Para crear esta clase:

1.  Haga doble clic en el **activos** carpeta en el *Panel proyecto*, a continuación, seleccione **crear* > * carpeta **. Nombre de la carpeta **Scripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Abra el **Scripts** carpeta, dentro de esa carpeta, haga clic en, **crear* > * C\# Script **. Nombre de la secuencia de comandos **MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Haga doble clic en el nuevo **MeetingsUI** script para abrirlo con *Visual Studio*.

4.  Inserte los espacios de nombres siguientes:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  Dentro de la clase inserte las siguientes variables:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  A continuación, reemplace el **Start()** método y agregue un **Awake()** método. Estos se llamará cuando se inicializa la clase:

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Agregue los métodos responsables de crear el *reuniones UI* y rellenarla con las reuniones actuales cuando se solicite:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Eliminar** el **Update()** método, y **guardar los cambios** en Visual Studio antes de volver a Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Capítulo 6: crear la clase de gráfico

Es el script siguiente para crear el **Graph** secuencia de comandos. Este script es responsable de realizar las llamadas a autenticar al usuario y recuperar las reuniones programadas para el día actual desde el calendario del usuario.

Para crear esta clase:

1.  Haga doble clic en el **Scripts** carpeta para abrirla.

2.  Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**. Nombre de la secuencia de comandos **gráfico**.

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Inserte los espacios de nombres siguientes:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Observará que las partes del código en esta secuencia de comandos se ajustan en torno a [precompilar directivas](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), esto es para evitar problemas con las bibliotecas al compilar la solución de Visual Studio.

5.  Eliminar el **Start()** y **Update()** métodos, ya que no se usará.

6.  Fuera del **Graph** class, insertar los objetos siguientes, que son necesarios para deserializar el objeto JSON que representa las reuniones programadas diarias:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  Dentro de la **gráfico** de clases, agregue las siguientes variables:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Cambiar el **appId** valor sea el **Id. de aplicación** que haya anotado en  **[capítulo 1](#chapter-1---create-your-app-in-the-application-registration-portal), paso 4**. Este valor debe ser el mismo que se muestra en el **Portal de registro de aplicación,** en la página de registro de aplicación.

8.  Dentro de la **Graph** de clases, agregue los métodos **SignInAsync()** y **AquireTokenAsync()**, que le solicitará al usuario que inserte las credenciales de inicio de sesión.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Agregue los dos métodos siguientes:

    1.  **BuildTodayCalendarEndpoint()**, que basa el URI que especifica el día y el intervalo de tiempo, en el que se recuperan las reuniones programadas.

    2.  **ListMeetingsAsync()**, que solicita las reuniones programadas de *Microsoft Graph*.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. Ahora ha completado la **Graph** secuencia de comandos. **Guarde los cambios** en Visual Studio antes de volver a Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Capítulo 7: crear la secuencia de comandos GazeInput

Ahora creará el **GazeInput**. Esta clase controla y realiza un seguimiento de mirada del usuario, mediante un **Raycast** procedentes de la **cámara principal**, proyectar hacia delante.

Para crear la secuencia de comandos:

1.  Haga doble clic en el **Scripts** carpeta para abrirla.

2.  Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**. Nombre de la secuencia de comandos **GazeInput**.

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Cambiar el código de espacios de nombres para que coincida con lo siguiente, además de agregar el '**\[System.Serializable\]**' etiqueta anterior su **GazeInput** clase, para que pueda serializarse:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  Dentro de la **GazeInput** de clases, agregue las siguientes variables:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

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

6.  Agregar el **CreateCursor()** método para crear el cursor de HoloLens en la escena y llamar al método desde el **Start()** método:

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  Los métodos siguientes permiten a la mirada Raycast y realizar un seguimiento de los objetos con foco.

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
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
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
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Guarde los cambios** en Visual Studio antes de volver a Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Capítulo 8: crear la clase interacciones

Ahora deberá crear el **interacciones** script, que es responsable de:

-   Controlar la **pulse** interacción y la **cámara que mirar**, lo que permite al usuario interactuar con el inicio de sesión "button" en la escena.

-   Crear el registro en el objeto de "button" en la escena para el usuario interactuar con.

Para crear la secuencia de comandos:

1.  Haga doble clic en el **Scripts** carpeta para abrirla.

2.  Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**. Nombre de la secuencia de comandos **interacciones**.

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Inserte los espacios de nombres siguientes:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Cambiar la herencia de la **interacción** clase *MonoBehaviour* a **GazeInput**.

    ~~Interacciones de clase pública: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Dentro de la **interacción** clase inserte la siguiente variable:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Reemplace el **iniciar** método; tenga en cuenta es un método de invalidación, que llama al método de clase 'base' mirada. **Start()** se llamará cuando se inicializa la clase, registrar para el reconocimiento de entrada y crear el inicio de sesión *botón* en la escena:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Agregar el **CreateSignInButton()** método, que creará una instancia el inicio de sesión *botón* en la escena y establezca sus propiedades:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Agregar el **GestureRecognizer_Tapped()** responder método, que ser el *pulse* evento de usuario.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Eliminar** el **Update()** método y, a continuación, **guardar los cambios** en Visual Studio antes de volver a Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Capítulo 9: configurar las referencias de script

En este capítulo tiene que colocar el **interacciones** de script en el **cámara principal**. Ese script controlará la colocación de los demás scripts donde deben estar.

-  Desde el **Scripts** carpeta en el *Panel proyecto*, arrastre la secuencia de comandos **interacciones** a la **cámara principal** de objeto, como se muestra a continuación.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Capítulo 10: configuración de la etiqueta

El código que controla la mirada hará uso de la etiqueta **SignInButton** para identificar el objeto que el usuario interactuará con para iniciar sesión *Microsoft Graph*.

Para crear la etiqueta:

1.  Haga clic en el Editor de Unity en el **cámara principal** en el *jerarquía Panel*.

2.  En el *Panel Inspector* haga clic en el **MainCamera** *etiqueta* para abrir una lista desplegable. Haga clic en **Agregar etiqueta...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Haga clic en el **+** botón.

    ![](images/AzureLabs-Lab311-31.png)

4.  Escribir el nombre de etiqueta como **SignInButton** y haga clic en Guardar.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Capítulo 11: Compile el proyecto de Unity a UWP

Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.

1.  Vaya a *configuración de compilación* (**archivo* > * compilar configuración **).

    ![](images/AzureLabs-Lab311-33.png)

2.  Si aún no marque **Unity C\# proyectos**.

3.  Haz clic en **Compilación**. Unity se iniciará un **Explorador de archivos** ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta y asígnele el nombre **aplicación**. A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**.

4.  Unity empezará a compilar el proyecto para el **aplicación** carpeta.

5.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

## <a name="chapter-12---deploy-to-hololens"></a>Capítulo 12 - implementación en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador.** Para ello:

    1.  Mientras que el exceso de su HoloLens, abra el **configuración**.

    2.  Vaya a **red e Internet** > **Wi-Fi** > **opciones avanzadas**

    3.  Tenga en cuenta la **IPv4** dirección.

    4.  A continuación, vaya a **configuración**y, a continuación, en **actualización y seguridad** > **para desarrolladores**

    5.  Establecer **modo de programador en**.

2.  Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.

3.  En el **configuración de la solución** seleccione **depurar**.

4.  En el **plataforma de solución**, seleccione **x86, máquina remota**. Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (el HoloLens, en este caso, lo cual observó).

    ![](images/AzureLabs-Lab311-34.png)

5.  Vaya a **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación a su HoloLens.

6.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.

## <a name="your-microsoft-graph-hololens-application"></a>La aplicación de Microsoft Graph HoloLens

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Microsoft Graph, para leer y mostrar datos de calendario del usuario.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

Usar Microsoft Graph para mostrar otra información sobre el usuario

-   Correo electrónico del usuario / número de teléfono / imagen del perfil

### <a name="exercise-1"></a>Ejercicio 1

Implementar el control de voz para navegar por la interfaz de usuario de Microsoft Graph.
