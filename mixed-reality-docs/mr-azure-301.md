---
title: 'MR y Azure 301: traducción de idiomas'
description: Complete este curso para aprender a implementar el Translator Text API de Azure en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, texto de traductor, hololens, envolventes, VR
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554334"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR y Azure 301: Traducción de idiomas

En este curso, aprenderá a agregar funcionalidades de traducción a una aplicación de realidad mixta con Azure Cognitive Services, con el Translator Text API.

![Producto final](images/AzureLabs-Lab1-00.png)

El Translator Text API es un servicio de traducción que funciona casi en tiempo real. El servicio se basa en la nube y, mediante una llamada de API de REST, una aplicación puede usar la tecnología de traducción automática de la máquina neuronal para traducir texto en otro idioma. Para obtener más información, visite la [Página de Translator Text API de Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Al finalizar este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:

1.  El usuario hablará con un micrófono conectado a un casco envolvente (VR) (o el micrófono integrado de HoloLens).
2.  La aplicación capturará el dictado y lo enviará a Azure Translator Text API.
3.  El resultado de la traducción se mostrará en un grupo de interfaz de usuario simple en la escena de Unity.

Este curso le enseñará a obtener los resultados del servicio de Traductor en una aplicación de ejemplo basada en Unity. Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 301: Traducción de idiomas</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Un conjunto de auriculares con micrófono integrado (si el casco no tiene micrófonos y altavoces integrados)
- Acceso a Internet para la instalación y la recuperación de traducciones de Azure

## <a name="before-you-start"></a>Antes de comenzar

- Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).
- El código de este tutorial le permitirá grabar desde el dispositivo de micrófono predeterminado conectado al equipo. Asegúrese de que el dispositivo de micrófono predeterminado está establecido en el dispositivo que va a usar para capturar la voz.
- Para permitir que su equipo habilite el dictado, vaya a **configuración > privacidad > voz, entrada manuscrita & escriba** y seleccione el botón **activar servicios de voz y sugerencias de escritura**.
- Si usa un micrófono y auriculares conectados (o incorporados a) el casco, asegúrese de que la opción "cuando he gastado el casco, cambiar a MIC micro" está activada en la **configuración > realidad mixta > audio y voz**.

   ![Configuración de realidad mixta](images/AzureLabs-Lab1-00-5.png)

   ![Configuración del micrófono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Tenga en cuenta que si está desarrollando para un casco envolvente para este laboratorio, puede experimentar problemas con el dispositivo de salida de audio. Esto se debe a un problema con Unity, que se corrige en versiones posteriores de Unity (Unity 2018,2). El problema impide que Unity cambie el dispositivo de salida de audio predeterminado en tiempo de ejecución. Como solución alternativa, asegúrese de que ha completado los pasos anteriores y cierre y vuelva a abrir el editor cuando este problema se presente.

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1: Azure portal

Para usar la API de traductor de Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.

1.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque "Translator Text API". Seleccione **entrar**.

    ![Nuevo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.

3.  La nueva página proporcionará una descripción del servicio *Translator Text API* . En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.

    ![Crear servicio de Translator Text API](images/AzureLabs-Lab1-03.png)

4.  Una vez que haya hecho clic en **crear**:

    1. Inserte el **nombre** que desee para esta instancia de servicio.
    2. Seleccione una **suscripción**adecuada.
    3. Seleccione el **plan de tarifa** adecuado para usted; si es la primera vez que crea un *servicio de Translator Text*, debe tener a su disposición un nivel gratis (denominado F0).
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    7. Seleccione **Crear**.

        ![Seleccione el botón crear.](images/AzureLabs-Lab1-04.png)

5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.
6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal. 

    ![Notificación de creación de servicio de Azure](images/AzureLabs-Lab1-05.png)

7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Vaya a menú emergente de recursos.](images/AzureLabs-Lab1-06.png)

8.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de servicio de Translator Text API. 

    ![Translator Text API página de servicio](images/AzureLabs-Lab1-07.png)

9.  En este tutorial, la aplicación necesitará realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio. 
10. En la página *Inicio rápido* del servicio de *Translator Text* , navegue hasta el primer paso, *grabe sus claves*y haga clic en **claves** (también puede conseguirlo haciendo clic en las teclas de hipervínculo azul, que se encuentran en el menú de navegación servicios, indicado por el icono de clave). Esto revelará las *claves*de servicio.
11. Realice una copia de una de las claves que se muestran, ya que la necesitará más adelante en el proyecto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2: configurar el proyecto de Unity

Configure y pruebe sus auriculares de la realidad mixta.

> [!NOTE]
> No necesitará controladores de movimiento para este curso. Si necesita admitir la configuración de un casco inmersivo, [siga estos pasos](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos:

1.  Abra *Unity* y haga clic en **nuevo**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab1-08.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity. Inserte **MR_Translation**. Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la *Ubicación* en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab1-09.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**. Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab1-10.png)

4.  A continuación, vaya a **archivo > configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab1-11.png)

5.  Vaya a **archivo > configuración de compilación** y asegúrese de que:

    1. El **dispositivo de destino** se establece en **cualquier dispositivo**.

        > Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.

    2. El **tipo de compilación** se establece en **D3D**
    3. **SDK** está establecido en la **versión más reciente instalada**
    4. La **versión de Visual Studio** está establecida en la **más reciente instalada**
    5. **Compilar y ejecutar** está establecido en **equipo local**
    6. Guarde la escena y agréguela a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.

            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab1-12.png)

        2. Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre Scenes.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab1-13.png)

        3. Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **MR_TranslationScene**y, a continuación, presione **Guardar**.

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab1-14.png)

            > Tenga en cuenta que debe guardar las escenas de Unity dentro de la carpeta *assets* , ya que deben estar asociadas con el proyecto Unity. La creación de la carpeta Scenes (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.

    7. El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* . 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab1-15.png)

7. En este panel, deben comprobarse algunas opciones de configuración:

    1. En la pestaña **otros valores** :

        1. La **versión de scripting en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).
        2. El **back-end** de scripting debe ser **.net**
        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab1-16.png)
      
    2. En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        1. **InternetClient**
        2. **Micrófono**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab1-17.png)

    3. Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![Actualice la configuración de X R.](images/AzureLabs-Lab1-18.png)

8.  De nuevo en la **configuración de compilación**, los *proyectos de Unity C#*  ya no están atenuados; Marque la casilla situada junto a este. 
9.  Cierre la ventana Configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3: configuración de la cámara principal

> [!IMPORTANT]
> Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), impórtelo en el proyecto como un [*paquete personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo 5](#chapter-5--create-the-results-class). Todavía tendrá que crear un proyecto de Unity.

1.  En el *Panel jerarquía*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista "principal" una vez que está "dentro" de la aplicación.
2.  Con el panel de Unity delante de usted, seleccione la **cámara principal GameObject**. Observará que el *panel Inspector* (generalmente situado a la derecha, dentro del panel) mostrará los distintos componentes de ese *GameObject*, con la *transformación* en la parte superior, la *cámara*y otros componentes. Tendrá que restablecer la transformación de la cámara principal, de modo que esté colocada correctamente.
3.  Para ello, seleccione el icono de **engranaje** situado junto al componente de *transformación* de la cámara y seleccione **restablecer**. 

    ![Restablezca la transformación de cámara principal.](images/AzureLabs-Lab1-19.png)
 
4.  El componente de *transformación* debería tener el siguiente aspecto:

    1. La *posición* se establece en **0, 0,0**
    2. La *rotación* se establece en **0,** 0,0
    3. Y *escala* se establece en **1, 1, 1**

        ![Transformación de la información de la cámara](images/AzureLabs-Lab1-20.png)

5.  A continuación, con el objeto de **cámara principal** seleccionado, vea el botón **Agregar componente** situado en la parte inferior del *panel Inspector*. 
6.  Seleccione ese botón y busque (escriba el origen de *audio* en el campo de búsqueda o navegue por las secciones) del componente denominado **origen de audio** como se muestra a continuación y selecciónelo (presione Entrar en él también funciona).
7.  Se agregará un componente de *origen de audio* a la **cámara principal**, como se muestra a continuación.

    ![Agregue un componente de origen de audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > En el caso de Microsoft HoloLens, también tendrá que cambiar lo siguiente, que forman parte del componente de **cámara** de la **cámara principal**:
    > - **Borrar marcas:** Color sólido.
    > - **Información general** ' Black, Alpha 0 ' – color Hex: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Capítulo 4: configurar el lienzo de depuración

Para mostrar la entrada y la salida de la traducción, es necesario crear una interfaz de usuario básica. En este curso, creará un objeto de interfaz de usuario de lienzo, con varios objetos de texto para mostrar los datos.

1.  Haga clic con el botón secundario en un área vacía del *Panel jerarquía*, en **UI**, agregar un **lienzo**.

    ![Agregue un nuevo objeto de interfaz de usuario de lienzo.](images/AzureLabs-Lab1-22.png)

2.  Con el objeto Canvas seleccionado, en el *panel Inspector* (dentro del componente ' Canvas '), cambie el **modo de representación** a **espacio universal**. 
3.  A continuación, cambie los siguientes parámetros en la *transformación Rect del panel Inspector*:

    1. *POS*    X 0 Y 0 Z 40 -  
    2. *Ancho* : 500
    3. *Alto* : 300
    4. *Escala*    X 0,13 Y 0,13 Z 0,13 - 

        ![Actualice la transformación Rect para el lienzo.](images/AzureLabs-Lab1-23.png)
 
4.  Haga clic con el botón derecho en el **lienzo** en el *Panel jerarquía*, en **UI**, y agregue un **Panel**. Este **Panel** proporcionará un fondo para el texto que se mostrará en la escena.
5.  Haga clic con el botón derecho en el **Panel de** jerarquías, en **UI**, y agregue un **objeto de texto**. Repita el mismo proceso hasta que haya creado cuatro objetos de texto de interfaz de usuario en total (sugerencia: Si tiene seleccionado el primer objeto ' text ', simplemente presione **' Ctrl ' + ' d '** para duplicarlo, hasta que tenga cuatro en total). 
6.  Para cada **objeto de texto**, selecciónelo y use las tablas siguientes para establecer los parámetros en el *panel Inspector*.

    1. Para el componente de *transformación Rect* :

        | NOMBRE                   | Transformación: *posición*             | Ancho      | Alto    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Para el componente de **texto (Script)** :


        | Name                   | Text               | Tamaño de fuente    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Estado del micrófono: | 20           |
        | AzureResponseLabel     | Respuesta web de Azure | 20           |
        | DictationLabel         |   Acaba de decir:   | 20           |
        | TranslationResultLabel |    Automática    | 20           |

        ![Escriba los valores correspondientes para las etiquetas de la interfaz de usuario.](images/AzureLabs-Lab1-24.png)

    3. Además, haga que el estilo de fuente esté en **negrita**. Esto hará que el texto sea más fácil de leer.

        ![Fuente Negrita.](images/AzureLabs-Lab1-25.png)

7.  Para cada *objeto de texto de interfaz de usuario* creado en el [capítulo 5](#chapter-5--create-the-results-class), cree un nuevo **objeto de texto de interfaz de usuario** *secundaria* . Estos elementos secundarios mostrarán la salida de la aplicación. Cree objetos *secundarios* haciendo clic con el botón derecho en el elemento primario previsto (por ejemplo, *MicrophoneStatusLabel*) y, a continuación, seleccione **interfaz de usuario** y, después, seleccione **texto**.
8.  Para cada uno de estos elementos secundarios, selecciónelo y use las tablas siguientes para establecer los parámetros en el panel del inspector.

    1. Para el componente de **transformación Rect** :

        | NOMBRE                  | Transformación: *posición* | Ancho      | Alto    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y-30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y-30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y-30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y-30 Z 0          | 300        | 30        |

    2. Para el componente de **texto (Script)** :

        | NOMBRE                  | Text          | Tamaño de fuente    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. A continuación, seleccione la opción de alineación ' centro ' para cada componente de texto:

    ![alinear texto.](images/AzureLabs-Lab1-26.png)

10. Para asegurarse de que los objetos de texto de la interfaz de usuario **secundarios** se pueden leer fácilmente, cambie su *color*. Para ello, haga clic en la barra (actualmente ' negra ') junto a *color*. 

    ![Escriba los valores correspondientes para las salidas de texto de la interfaz de usuario.](images/AzureLabs-Lab1-27.png)
 
11. A continuación, en la ventana nuevo, pequeño, *color* , cambie el *color Hex* a: **0032EAFF**

    ![Actualice el color a azul.](images/AzureLabs-Lab1-28.png)
 
12. A continuación se muestra el aspecto de la **interfaz de usuario** .
    1.  En el *Panel jerarquía*:

        ![Tienen una jerarquía en la estructura proporcionada.](images/AzureLabs-Lab1-29.png)

    2.  En las vistas de *escena* y *juego*:

        ![Tenga las vistas escena y juego en la misma estructura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capítulo 5: crear la clase de resultados

El primer script que debe crear es la clase *Results* , que es responsable de proporcionar una manera de ver los resultados de la traducción. La clase almacena y muestra lo siguiente: 

- Resultado de la respuesta de Azure.
- El estado del micrófono. 
- Resultado del dictado (voz a texto).
- Resultado de la conversión.

Para crear esta clase: 

1.  Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, **cree > carpeta**. Asigne a la carpeta el nombre scripts. 
 
    ![Crear carpeta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra la carpeta scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Con la  carpeta scripts creada, haga doble clic en ella para abrirla. Después, dentro de esa carpeta, haga clic con el botón derecho y seleccione **crear >** después  **C# script**. Asigne un nombre a los *resultados*del script. 

    ![Cree el primer script.](images/AzureLabs-Lab1-33.png)
 
3.  Haga doble clic en el nuevo script de *resultados* para abrirlo con **Visual Studio**.
4.  Inserte los espacios de nombres siguientes:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Dentro de la clase, inserte las siguientes variables:

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

6.  A continuación, agregue el método *activo ()* , al que se llamará cuando se inicialice la clase. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Por último, agregue los métodos que son responsables de generar la información de los diversos resultados en la interfaz de usuario. 

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

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capítulo 6: crear la clase *MicrophoneManager*

La segunda clase que va a crear es *MicrophoneManager*.

Esta clase es responsable de:

- Detección del dispositivo de grabación conectado a los auriculares o al equipo (el valor predeterminado).
- Capture el audio (voz) y use el dictado para almacenarlo como una cadena.
- Una vez que se haya pausado la voz, envíe el dictado a la clase Translator.
- Hospede un método que pueda detener la captura de voz si lo desea.

Para crear esta clase: 
1.  Haga doble clic en  la carpeta scripts para abrirla. 
2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**. Asigne al script el nombre *MicrophoneManager*. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres para que sean los mismos que los que se indican a continuación, en la parte superior de la clase *MicrophoneManager* :

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  A continuación, agregue las siguientes variables dentro de la clase *MicrophoneManager* :

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

6.  Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* . Se llamará cuando se inicialice la clase:

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

7.  Puede *eliminar* el método *Update ()* , ya que esta clase no lo usará.
8.  Ahora necesita los métodos que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la clase *Translator* , que creará pronto. Copie el código siguiente y péguelo debajo del método *Start ()* .

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
    > Aunque esta aplicación no hará uso de ella, el método *StopCapturingAudio ()* también se ha proporcionado aquí, si desea implementar la capacidad de detener la captura de audio en la aplicación.

9.  Ahora debe agregar un controlador de dictado que se invocará cuando se detenga la voz. A continuación, este método pasará el texto dictado a la clase *Translator* .

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
> En este punto, observará que aparece un error en el panel de la *consola del editor de Unity* ("el nombre ' Translator ' no existe..."). Esto se debe a que el código hace referencia a la clase *Translator* , que creará en el siguiente capítulo.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capítulo 7: llamada a Azure y a servicio de traductor

El último script que debe crear es la clase *Translator* . 

Esta clase es responsable de:

-   Autenticación de la aplicación con *Azure*, en Exchange para un **token de autenticación**.
-   Use el **token de autenticación** para enviar el texto (recibido de la clase *MicrophoneManager* ) para su traducción.
-   Reciba el resultado traducido y páselo a la clase de *resultados* que se visualizará en la interfaz de usuario.

Para crear esta clase: 
1.  Vaya a la  carpeta scripts que creó anteriormente. 
2.  Haga clic con el botón derecho en el **panel Proyecto**, **cree > C# script**. Llame al *traductor*de scripts.
3.  Haga doble clic en el nuevo script de *traductor* para abrirlo **con Visual Studio**.
4.  Agregue los siguientes espacios de nombres al principio del archivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  A continuación, agregue las siguientes variables dentro de la clase *Translator* :

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
    > - Los lenguajes insertados en  la enumeración de lenguajes son solo ejemplos. No dude en agregar más si lo desea; la [API admite más de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluido Klingon).
    > - Hay una [página más interactiva que cubre los idiomas disponibles](https://www.microsoft.com/translator/business/languages/), aunque tenga en cuenta que la página solo parece funcionar cuando el idioma del sitio se establece en "en-US" (y el sitio de Microsoft probablemente redirigirá a su idioma nativo). Puede cambiar el idioma del sitio en la parte inferior de la página o mediante la modificación de la dirección URL.
    > - El valor **authorizationKey** , en el fragmento de código anterior, debe ser la **clave** que recibió al suscribirse a *Azure Translator Text API*. Esto se trató en el [capítulo 1](#chapter-1--the-azure-portal).

6.  Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* . 
7.  En este caso, el código realizará una llamada a *Azure* mediante la clave de autorización para obtener un *token*.

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
    > El token expirará después de 10 minutos. En función del escenario de la aplicación, es posible que tenga que realizar la misma llamada de corutina varias veces.

8.  La corutina para obtener el token es la siguiente:

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
    > Si edita el nombre del método IEnumerator **GetTokenCoroutine ()** , debe actualizar los valores de cadena de llamada *StartCoroutine* y *StopCoroutine* en el código anterior. [Según la documentación de Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), para detener una *corutina*concreta, debe usar el método de valor de cadena.

9.  A continuación, agregue la corutina (con un método de secuencia "support" justo debajo de ella) para obtener la traducción del texto que recibe la clase *MicrophoneManager* . Este código crea una cadena de consulta para enviar a *Azure Translator Text API*y, a continuación, usa la clase UnityWebRequest de Unity interna para realizar una llamada "Get" al punto de conexión con la cadena de consulta. A continuación, el resultado se usa para establecer la traducción en el objeto de resultados. En el código siguiente se muestra la implementación:

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

## <a name="chapter-8--configure-the-unity-scene"></a>Capítulo 8: configuración de la escena de Unity

1.  De nuevo en el editor de Unity, haga clic y arrastre la clase de *resultados* *desde* la carpeta **scripts** hasta el objeto de **cámara principal** en el *Panel jerarquía*.
2.  Haga clic en la **cámara principal** y mire en el *panel del inspector*. Observará que, dentro del componente de *script* recién agregado, hay cuatro campos con valores vacíos. Estas son las referencias de salida a las propiedades del código. 
3.  Arrastre los objetos de **texto** correspondientes desde el *Panel jerarquía* hasta las cuatro ranuras, tal como se muestra en la imagen siguiente.

    ![Actualice las referencias de destino con los valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  A continuación, haga clic y arrastre la clase *Translator* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*. 
5.  A continuación, haga clic y arrastre la clase *MicrophoneManager* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*. 
6.  Por último, haga clic en la **cámara principal** y mire en el *panel del inspector*. Observará que en el script que ha arrastrado, hay dos cuadros desplegables que le permitirán establecer los idiomas.
 
    ![Asegúrese de que se introducen los idiomas de traducción previstos.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capítulo 9: probar en realidad mixta

Llegados a este punto, debe probar que la escena se ha implementado correctamente.

Asegúrate de lo siguiente:

- Toda la configuración mencionada en el [capítulo 1](#chapter-1--the-azure-portal) se establece correctamente. 
- Los scripts Results, *Translator*y *MicrophoneManager*se adjuntan al objeto de **cámara principal** . 
- Ha colocado la **clave** de servicio de *Azure Translator Text API* dentro de la variable **AuthorizationKey** dentro del script de *traductor* .  
- Todos los campos del *panel Inspector de cámara principal* están asignados correctamente.
- El micrófono funciona al ejecutar la escena (si no es así, compruebe que el micrófono conectado es el dispositivo *predeterminado* y que lo ha [configurado correctamente en Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Puede probar el casco envolvente presionando el botón **reproducir** en el editor de *Unity*.
La aplicación debe estar funcionando a través de los auriculares que se agregan.

> [!WARNING]  
> Si ve un error en la consola de Unity sobre el cambio del dispositivo de audio predeterminado, es posible que la escena no funcione según lo previsto. Esto se debe a la forma en que el portal de realidad mixta trata los micrófonos integrados para los auriculares que los tienen. Si ve este error, simplemente detenga la escena e iníciela de nuevo y las cosas deberían funcionar según lo previsto.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capítulo 10: compilar la solución de UWP y transferir localmente en el equipo local

Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.

1.  Vaya a **configuración de compilación**: **Configuración de compilación de > de archivos...**
2.  En la ventana **configuración de compilación** , haga clic en compilar.

    ![Compile la escena de Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Si aún no lo está, marque los **proyectos de Unity C#** .
4.  Haz clic en **Compilación**. Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y asígnele el nombre *App*. Después, con la carpeta de la *aplicación* seleccionada, presione **Seleccionar carpeta**. 
5.  Unity comenzará a compilar el proyecto en la carpeta de la *aplicación* . 
6.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del *Explorador de archivos* en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-11--deploy-your-application"></a>Capítulo 11: implementación de la aplicación

Para implementar la aplicación:

1.  Vaya a la nueva compilación de Unity (la carpeta de la *aplicación* ) y abra el archivo de solución con *Visual Studio*.
2.  En la configuración de soluciones , seleccione Depurar.
3.  En la plataforma de la solución, seleccione **x86**, **equipo local**. 

    > En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP** de HoloLens, que puede encontrarse en la *configuración > red & Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar. 
    > - Asegurarse de que el *modo de desarrollador* está **activado**; se encuentra en *configuración > actualizar & > de seguridad para desarrolladores*.

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Vaya al **menú** compilar y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.
5.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.
6.  Una vez iniciado, la aplicación le pedirá que autorice el acceso al micrófono. Asegúrese de hacer clic en el botón **sí** .
7.  Ya está listo para empezar a traducir.

## <a name="your-finished-translation-text-api-application"></a>Su aplicación de API de texto de traducción finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha la API de texto de traducción de Azure para convertir voz en texto traducido.

![Producto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

¿Se puede Agregar funcionalidad de texto a voz a la aplicación para que se diga el texto devuelto?

### <a name="exercise-2"></a>Ejercicio 2

Permite que el usuario cambie los idiomas de origen y de salida ("de" y "a") dentro de la propia aplicación, por lo que no es necesario recompilar la aplicación cada vez que desee cambiar los idiomas.
