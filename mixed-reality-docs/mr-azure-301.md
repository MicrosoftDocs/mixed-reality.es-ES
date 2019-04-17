---
title: El Sr. y Azure 301 - traducción de idiomas
description: Realice este curso para obtener información sobre cómo implementar Azure Translator Text API dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, texto de traductor, hololens, envolventes, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605455"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-and-azure-301-language-translation"></a>El Sr. y Azure 301: Traducción de idiomas

En este curso, obtendrá información sobre cómo agregar capacidades de traducción a una aplicación de realidad mixta con Azure Cognitive Services, con Translator Text API.

![Final producto](images/AzureLabs-Lab1-00.png)

Translator Text API es una servicio que funciona en casi en tiempo real de traducción. El servicio está en la nube y, mediante una llamada de API de REST, una aplicación puede hacer uso de la tecnología de traducción automática neuronal para traducir texto en otro lenguaje. Para obtener más información, visite la [página Azure Translator Text API](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:

1.  El usuario se hable un micrófono conectado a un auricular (VR) envolvente (o el micrófono integrado de HoloLens).
2.  La aplicación capturará el dictado y enviarla a Translator Text API de Azure.
3.  El resultado de la traducción se mostrará en un grupo de interfaz de usuario simple en la escena de Unity.

Este curso le mostrará cómo obtener los resultados desde el servicio del traductor en una aplicación de ejemplo basada en Unity. Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 301: Traducción de idiomas</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Un conjunto de auriculares con micrófono integrado (si no tienen los auriculares altavoces y un micrófono integrado)
- Acceso a Internet para el programa de instalación y traducción de la recuperación de Azure

## <a name="before-you-start"></a>Antes de empezar

- Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
- El código de este tutorial, podrá grabar desde el dispositivo de micrófono predeterminado conectado a su PC. Asegúrese de que el dispositivo de micrófono predeterminado se establece en el dispositivo que se va a usar para capturar la voz.
- Para permitir que su equipo habilitar el dictado, vaya a **configuración > privacidad > voz de tinta & escribir** y seleccione el botón **activar servicios de voz y escritura sugerencias**.
- Si usas un micrófono y auriculares conectados a (o está integrada en) los auriculares, asegúrese de que la opción "Cuando wear mi auriculares, vaya a auriculares con micrófono" está activada en **configuración > la realidad mixta > Audio y voz**.

   ![Configuración de la realidad mixta](images/AzureLabs-Lab1-00-5.png)

   ![Configuración del micrófono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Tenga en cuenta que si está desarrollando para un auricular envolvente para este laboratorio, puede experimentar problemas de dispositivo de salida de audio. Esto es debido a un problema con Unity, que se ha corregido en versiones posteriores de Unity (Unity 2018.2). El problema impide que Unity cambie el dispositivo de salida de audio predeterminado en tiempo de ejecución. Como solución alternativa, asegúrese de que haber completado los pasos anteriores y cierre y vuelva a abrir el Editor, cuando se presenta este problema.

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1: el Portal de Azure

Para usar la API del traductor de Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.

1.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **New** en la parte superior izquierda esquina y busque "Translator Text API". Seleccione **escriba**.

    ![Nuevo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.

3.  La nueva página proporcionará una descripción de la *Translator Text API* Service. En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.

    ![Crear servicio de API de texto de traductor](images/AzureLabs-Lab1-03.png)

4.  Una vez que ha hecho clic **crear**:

    1. Insertar el elemento **nombre** para esta instancia de servicio.
    2. Seleccione un **suscripción**.
    3. Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *Translator Text Service*, un nivel gratuito (denominado F0) debe estar disponible para usted.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un solo proyecto (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    7. Selecciona **Crear**.

        ![Seleccione el botón Crear.](images/AzureLabs-Lab1-04.png)

5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.
6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal. 

    ![Notificación de creación de servicio de Azure](images/AzureLabs-Lab1-05.png)

7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Vaya al menú emergente de recursos.](images/AzureLabs-Lab1-06.png)

8.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia de servicio de API de texto de traductor. 

    ![Página de servicio de API de texto de traductor](images/AzureLabs-Lab1-07.png)

9.  En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través del uso clave del servicio en la de suscripción. 
10. Desde el *inicio rápido* página de su *Translator Text* Service, navegue hasta el primer paso, *obtener las claves*y haga clic en **claves** (puede También lograr esto, haga clic en el hipervínculo azul claves, ubicado en el menú de navegación de servicios, indicado por el icono de llave). Esto revelará su servicio *claves*.
11. Realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2: configurar el proyecto de Unity

Configurar y probar los auriculares de realidad mixta envolventes.

> [!NOTE]
> En este curso, no necesitará controladores de movimiento. Si necesita admite la configuración de un auricular envolvente, [siga estos pasos](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y, por lo tanto, es una buena plantilla para otros proyectos:

1.  Abra *Unity* y haga clic en **New**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab1-08.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Insertar **MR_Translation**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establecer el *ubicación* a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab1-09.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab1-10.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab1-11.png)

5.  Vaya a **archivo > configuración de compilación** y asegúrese de que:

    1. **Dispositivo de destino** está establecido en **cualquier dispositivo**.

        > Para Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.

    2. **Tipo de compilación** está establecido en **D3D**
    3. **SDK** está establecido en **instalada más reciente**
    4. **Versión de Visual Studio** está establecido en **instalada más reciente**
    5. **Compilar y ejecutar** está establecido en **máquina Local**
    6. Guarde la escena y agregarlo a la compilación.

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab1-12.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab1-13.png)

        3. Abra el recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_TranslationScene**, a continuación, presione **guardar**.

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab1-14.png)

            > Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity. Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.

    7. El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra. 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab1-15.png)

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1. En el **otra configuración** pestaña:

        1. **Versión en tiempo de ejecución de secuencias de comandos** debe ser **estable** (.NET 3.5 equivalente).
        2. **Scripting de back-end** debe ser **.NET**
        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab1-16.png)
      
    2. Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        1. **InternetClient**
        2. **Micrófono**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab1-17.png)

    3. Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab1-18.png)

8.  En **configuración de compilación**, *Unity C# proyectos* ya no está atenuada; Marque la casilla situada junto a esto. 
9.  Cierre la ventana de configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3: configuración de cámara principal

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importarlo en el proyecto como un [ *Paquete personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5--create-the-results-class). Deberá crear un proyecto de Unity.

1.  En el *jerarquía Panel*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista de "head" una vez que esté "dentro" de la aplicación.
2.  Con el panel de Unity delante de usted, seleccione el **Main cámara GameObject**. Observará que el *Panel Inspector* (generalmente se encuentra a la derecha, en el panel) mostrará los distintos componentes de la que *GameObject*, con *transformar* en la parte superior, seguido por *cámara*y algunos otros componentes. Deberá restablecer la transformación de la cámara principal, por lo que está colocado correctamente.
3.  Para ello, seleccione el **engranaje** icono situado junto a la cámara *transformar* componente y seleccione **restablecer**. 

    ![Restablecer la transformación de la cámara principal.](images/AzureLabs-Lab1-19.png)
 
4.  El *transformar* componente debería entonces el aspecto siguiente:

    1. El *posición* está establecido en **0, 0, 0**
    2. *Rotación* está establecido en **0, 0, 0**
    3. Y *escala* está establecido en **1, 1, 1**

        ![Transformar la información de la cámara](images/AzureLabs-Lab1-20.png)

5.  A continuación, con el **cámara principal** seleccionado de objetos, consulte el **Agregar componente** situado en la parte inferior de la *Panel Inspector*. 
6.  Seleccionar ese botón y buscar (escribiendo *origen Audio* en el campo de búsqueda o desplazarse por las secciones) para el componente denominado **origen Audio** tal como se muestra a continuación y selecciónelo (presione ENTRAR en ella También funciona).
7.  Un *origen Audio* componente se agregará a la **cámara principal**, tal y como se muestra a continuación.

    ![Agregar un componente de origen de Audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Para Microsoft HoloLens, deberá cambiar también los siguientes valores, que forman parte de la **cámara** componente en su **cámara principal**:
    > - **Borrar las marcas de:** Color sólido.
    > - **En segundo plano** ' negro, alfa 0': código de color hexadecimal: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Capítulo 4: lienzo de depuración del programa de instalación

Para mostrar la entrada y salida de la traducción, se debe crear una interfaz de usuario básica. En este curso, creará un objeto de interfaz de usuario de Canvas, con varios objetos 'Texto' para mostrar los datos.

1.  Haga clic en un área vacía de la *jerarquía Panel*, en **UI**, agregar un **lienzo**.

    ![Agregue el nuevo objeto de interfaz de usuario de Canvas.](images/AzureLabs-Lab1-22.png)

2.  Con el objeto de lienzo seleccionado, en el *Panel Inspector* (en el componente "Lienzo"), cambiar **modo de representar** a **espacio universal**. 
3.  A continuación, cambie los parámetros siguientes en el *Rect transformación del Panel del Inspector*:

    1. *PDV* -  **X** 0 **Y** 0 **Z** 40
    2. *Width* -    500
    3. *Alto* : 300
    4. *Escala* - **X** 0.13 **Y** 0.13 **Z** 0.13

        ![Actualizar la transformación rect del lienzo.](images/AzureLabs-Lab1-23.png)
 
4.  Haga clic con el botón derecho en el **lienzo** en el *jerarquía Panel*, en **UI**y agregue un **Panel**. Esto **Panel** proporcionará un fondo para el texto que se va a mostrar en la escena.
5.  Haga clic con el botón derecho en el **Panel** en el *jerarquía Panel*, en **UI**y agregue un **objeto de texto**. Repita el mismo proceso hasta que haya creado cuatro objetos de texto de la interfaz de usuario en total (Sugerencia: si tiene el primer objeto de 'Text' seleccionado, puede simplemente presionar **'Ctrl' + tenía '**, duplicarla, hasta que haya cuatro en total). 
6.  Para cada **objeto texto**, selecciónelo y utilice el debajo de las tablas para definir los parámetros el *Panel Inspector*.

    1. Para el *Rect transformación* componente:

        | Nombre                   | Transformar - *posición*             | Ancho      | Alto    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Para el **texto (Script)** componente:


        | Nombre                   | Text               | Tamaño de fuente    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Estado de micrófono: | 20           |
        | AzureResponseLabel     | Respuesta Web de Azure | 20           |
        | DictationLabel         |   Acabamos de decir:   | 20           |
        | TranslationResultLabel |    Traducción:    | 20           |

        ![Escriba los valores correspondientes para las etiquetas de interfaz de usuario.](images/AzureLabs-Lab1-24.png)

    3. Además, asegúrese del estilo de fuente **negrita**. Esto hará que el texto más fácil de leer.

        ![Fuente negrita.](images/AzureLabs-Lab1-25.png)

7.  Para cada *objeto de texto de la interfaz de usuario* creado en [capítulo 5](#chapter-5--create-the-results-class), cree un nuevo *secundarios* **objeto de texto de la interfaz de usuario**. Estos controles secundarios mostrarán el resultado de la aplicación. Crear *secundarios* objetos a través con el botón secundario de su padre deseado (por ejemplo, *MicrophoneStatusLabel*) y, a continuación, seleccione **UI** y, a continuación, seleccione **texto**.
8.  Para cada uno de estos controles secundarios, selecciónelo y utilice el debajo de las tablas para definir los parámetros en el Panel del Inspector.

    1. Para el **Rect transformación** componente:

        | Nombre                  | Transformar - *posición* | Ancho      | Alto    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. Para el **texto (Script)** componente:

        | Name                  | Text          | Tamaño de fuente    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. A continuación, seleccione la opción de alineación de "centre" para cada componente de texto:

    ![Alinear el texto.](images/AzureLabs-Lab1-26.png)

10. Para garantizar la **texto de la interfaz de usuario secundario** objetos sean fácilmente legibles, cambie sus *Color*. Esto se realiza al hacer clic en la barra (actualmente ' negro") junto a *Color*. 

    ![Entrada correspondiente a los valores de las salidas de texto de la interfaz de usuario.](images/AzureLabs-Lab1-27.png)
 
11. A continuación, en el nuevo, pequeño, *Color* ventana, cambie el *de Color hexadecimal* para: **0032EAFF**

    ![Actualice el color a azul.](images/AzureLabs-Lab1-28.png)
 
12. A continuación se presenta cómo la **UI** debe tener un aspecto.
    1.  En el *jerarquía Panel*:

        ![Tiene la jerarquía de la estructura proporcionada.](images/AzureLabs-Lab1-29.png)

    2.  En el *escena* y *juegos vistas*:

        ![Tiene las vistas de la escena y juego en la misma estructura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capítulo 5: crear la clase de resultados

Es el primer script, deberá crear el *resultados* (clase), que es responsable de proporcionar una manera de ver los resultados de la traducción. La clase almacena y muestra lo siguiente: 

- El resultado de la respuesta de Azure.
- El estado de micrófono. 
- El resultado de la dictado (voz a texto).
- El resultado de la traducción.

Para crear esta clase: 

1.  Haga clic en el *Panel del proyecto*, a continuación, **crear > carpeta**. Nombre de la carpeta **Scripts**. 
 
    ![Crear carpeta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra la carpeta de scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Con el **Scripts** carpeta crear, haga doble clic en él para abrirlo. A continuación, dentro de esa carpeta, contextual y seleccione **crear >** , a continuación,  **C# Script**. Nombre de la secuencia de comandos *resultados*. 

    ![Cree la primera secuencia de comandos.](images/AzureLabs-Lab1-33.png)
 
3.  Haga doble clic en el nuevo *resultados* script para abrirlo con **Visual Studio**.
4.  Inserte los espacios de nombres siguientes:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Dentro de la clase inserte las siguientes variables:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  A continuación, agregue el *Awake()* método, que se llamará cuando se inicializa la clase. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Por último, agregue los métodos que son responsables de generar la diversa información de los resultados a la interfaz de usuario. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capítulo 6: crear el *MicrophoneManager* clase

La segunda clase va a crear es la *MicrophoneManager*.

Esta clase es responsable de:

- Detectar el dispositivo de grabación conectado al equipo (lo que sea el valor predeterminado) o auriculares.
- Captura de audio (voces) y use el dictado para almacenarla como una cadena.
- Una vez que se ha pausado la voz, enviar el dictado a la clase de traductor.
- Hospedar un método que se puede detener la captura de voz si lo desea.

Para crear esta clase: 
1.  Haga doble clic en el **Scripts** carpeta para abrirla. 
2.  Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos *MicrophoneManager*. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres para que sea igual a lo siguiente en la parte superior de la *MicrophoneManager* clase:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *MicrophoneManager* clase:

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  El código para el *Awake()* y *Start()* métodos ahora debe agregarse. Estos se llamará cuando se inicializa la clase:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  También puede *eliminar* el *Update()* método puesto que esta clase no lo usará.
8.  Ahora tiene los métodos que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la *traductor* (clase), que se compila en breve. Copie el código siguiente y péguelo debajo de la *Start()* método.

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Aunque no hará que esta aplicación use, el *StopCapturingAudio()* método también se ha proporcionado en este caso, si desea implementar la capacidad para detener la captura de audio en la aplicación.

9.  Ahora debe agregar un controlador de dictado que se invocará cuando se detiene la voz. Este método, a continuación, pasará el texto dictado a la *traductor* clase.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.

> [!WARNING]  
> En este momento aparece un error que aparecen en la *consola del Editor de Unity* Panel ("el nombre 'Traductor' no existe …"). Esto es porque el código hace referencia a la *traductor* (clase), que creará en el próximo capítulo.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capítulo 7: llamada al servicio de Azure y el traductor

Es el último script, deberá crear el *traductor* clase. 

Esta clase es responsable de:

-   Autenticar la aplicación con *Azure*, exchange para un **Auth Token**.
-   Use la **Token de autenticación** para enviar texto (recibidos desde el *MicrophoneManager* clase) que se deben traducir.
-   Recibir el resultado traducido y páselo a la *resultados* clase que se visualizará en la interfaz de usuario.

Para crear esta clase: 
1.  Vaya a la **Scripts** carpeta que creó anteriormente. 
2.  Haga clic en el **Panel del proyecto**, **crear > C# Script**. Llame al script *traductor*.
3.  Haga doble clic en el nuevo *traductor* script para abrirlo **con Visual Studio**.
4.  Agregue los siguientes espacios de nombres en la parte superior del archivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *traductor* clase:

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Los idiomas que se insertan en los idiomas **enum** son solo ejemplos. Puede agregar más si lo desea; el [API admite más de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluido Klingon)!
    > - Hay un [página más interactiva que cubre lenguajes disponibles](https://www.microsoft.com/translator/business/languages/), aunque tenga en la página solo aparece para que funcione cuando se establece el idioma del sitio en "en-us' (y el sitio de Microsoft le redireccionamiento probable para su idioma nativo). Puede cambiar el idioma del sitio en la parte inferior de la página o modificando la dirección URL.
    > - El **authorizationKey** valor, en el fragmento de código anterior, debe ser el **clave** recibe al suscribirse a la *Azure Translator Text API*. Esto se trata en [capítulo 1](#chapter-1--the-azure-portal).

6.  El código para el *Awake()* y *Start()* métodos ahora debe agregarse. 
7.  En este caso, el código hará que una llamada a *Azure* con la clave de autorización para obtener un *Token*.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > El token expirará transcurridos 10 minutos. Según el escenario de la aplicación, es posible que deba realizar la misma corrutina llamada varias veces.

8.  La corrutina para obtener el Token es la siguiente:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Si edita el nombre del método IEnumerator **GetTokenCoroutine()**, deberá actualizar el *StartCoroutine* y *StopCoroutine* llamar a los valores de cadena en el código anterior. [Según la documentación de Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), para detener un determinado *Corrutina*, deberá usar el método de valor de cadena.

9.  A continuación, agregue la corrutina (con un método de secuencia "soporte técnico" situado debajo de ella) para obtener la traducción de texto recibida el *MicrophoneManager* clase. Este código crea una cadena de consulta para enviar a la *Azure Translator Text API*y, a continuación, utiliza la clase de Unity UnityWebRequest interna para realizar una llamada de 'Get' al punto de conexión con la cadena de consulta. El resultado, a continuación, se usa para establecer la traducción en el objeto de resultados. El código siguiente muestra la implementación:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-8--configure-the-unity-scene"></a>Capítulo 8: configurar la escena de Unity

1.  En el Editor de Unity, haga clic en Atrás y arrastre el *resultados* clase *desde* el **Scripts** carpeta para el **cámara principal** objeto en el  *Panel de la jerarquía*.
2.  Haga clic en el **cámara principal** y examine el *Panel Inspector*. Observará que en la recién agregada *Script* , componente, hay cuatro campos con valores vacíos. Estas son las referencias de salida a las propiedades en el código. 
3.  Arrastre adecuado **texto** objetos desde el *jerarquía Panel* para esas cuatro ranuras, tal como se muestra en la imagen siguiente.

    ![Actualice las referencias de destino con los valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  A continuación, haga clic y arrastre el *traductor* clase desde el **Scripts** carpeta a la **cámara principal** objeto en el *jerarquía Panel*. 
5.  A continuación, haga clic y arrastre el *MicrophoneManager* clase desde el **secuencias de comandos** carpeta para el **cámara principal** objeto en el *jerarquía Panel*. 
6.  Por último, haga clic en el **cámara principal** y examine el *Panel Inspector*. Observará que en la secuencia de comandos que se arrastró en, hay dos cuadros desplegables de que le permitirá establecer los idiomas.
 
    ![Asegúrese de que se introducen los idiomas de traducción previsto.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capítulo 9: prueba de realidad mixta

En este momento deberá comprobar que se ha implementado correctamente la escena.

Asegúrate de lo siguiente:

- Todas las configuraciones que se mencionan en [capítulo 1](#chapter-1--the-azure-portal) están establecidas correctamente. 
- El *resultados*, *traductor*, y *MicrophoneManager*, secuencias de comandos están conectados a la **cámara principal** objeto. 
- Ha colocado su *Azure Translator Text API* servicio **clave** dentro de la **authorizationKey** variable dentro de la *traductor* Guión.  
- Todos los campos de la *Panel de Inspector de cámara principal* se asignan correctamente.
- El micrófono está funcionando cuando se ejecuta la escena (si no, compruebe que el micrófono conectado es el *predeterminada* dispositivo y que tiene [configurarlo correctamente dentro de Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Puede probar los auriculares envolventes presionando el **reproducir** situado en la *Editor de Unity*.
La aplicación debe funcionar a través de los auriculares envolventes adjunto.

> [!WARNING]  
> Si ve un error en la consola de Unity sobre el dispositivo de audio predeterminado cambia, la escena podría no funcionar según lo previsto. Esto es debido al modo en que el portal de realidad mixta se ocupa de los micrófonos integrados para auriculares que disponen de ella. Si ve este error, basta con detener la escena y vuelva a iniciarlo y todo debería funcionar como se esperaba.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capítulo 10: crear la solución UWP y transferir localmente en el equipo local

Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.

1.  Vaya a **configuración de compilación**: **Archivo > configuración de compilación...**
2.  Desde el **configuración de compilación** ventana, haga clic en **compilar**.

    ![Compile la escena de Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Si aún no marque **Unity C# proyectos**.
4.  Haz clic en **Compilación**. Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en. Crear la carpeta y asígnele el nombre *aplicación*. A continuación, con el *aplicación* carpeta seleccionada, presione **seleccionar la carpeta**. 
5.  Unity empezará a compilar el proyecto para el *aplicación* carpeta. 
6.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un *Explorador de archivos* ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

## <a name="chapter-11--deploy-your-application"></a>Capítulo 11: implementar la aplicación

Para implementar la aplicación:

1.  Vaya a la nueva compilación de Unity (la *aplicación* carpeta) y abra el archivo de solución con *Visual Studio*.
2.  En, seleccione la configuración de la solución **depurar**.
3.  En la plataforma de soluciones, seleccione **x86**, **máquina Local**. 

    > Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo. Sin embargo, necesitará también hacer lo siguiente:
    > - Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la *configuración > red e Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar. 
    > - Asegúrese de *modo de programador* es **en**; se encuentra en *configuración > actualización y seguridad > para los desarrolladores*.

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.
5.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.
6.  Una vez iniciado, la aplicación le pedirá que autorice el acceso al micrófono. Asegúrese de hacer clic en el **Sí** botón.
7.  Ahora está listo para comenzar a traducir.

## <a name="your-finished-translation-text-api-application"></a>La aplicación finalizada de Text Translation API

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha la API de texto de traducción de Azure para convertir voz en texto traducido.

![Producto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

¿Puede agregar texto a voz funcionalidad a la aplicación, por lo que se diga el texto devuelto?

### <a name="exercise-2"></a>Ejercicio 2

Permiten al usuario cambiar los idiomas de origen y de salida ('from' y 'to') dentro de la propia aplicación, por lo que la aplicación no necesitan volver a crearse cada vez desee cambiar los idiomas.
