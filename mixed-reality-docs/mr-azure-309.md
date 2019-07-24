---
title: MR y Azure 309-Application Insights
description: Complete este curso para aprender a recopilar análisis sobre el comportamiento del usuario en una aplicación de realidad mixta, mediante el servicio de Aplicación de Azure Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, Application Insights, hololens, envolventes, VR
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694569"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR y Azure 309: Application Insights

![Inicio del producto final](images/AzureLabs-Lab309-00.png)

En este curso, aprenderá a agregar funcionalidades de Application Insights a una aplicación de realidad mixta, mediante la API de Aplicación de Azure Insights para recopilar análisis sobre el comportamiento de los usuarios.

Application Insights es un servicio de Microsoft, lo que permite a los desarrolladores recopilar análisis de sus aplicaciones y administrarlo desde un portal fácil de usar. El análisis puede ser cualquier cosa desde el rendimiento hasta la información personalizada que desea recopilar. Para obtener más información, visite la [página Application Insights](https://azure.microsoft.com/services/application-insights/).

Una vez finalizado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta que podrá hacer lo siguiente:

1.  Permite al usuario avanzar y desplazarse por una escena.
2.  Desencadene el envío de análisis al servicio de *Application Insights*, mediante el uso de miras y proximidad a objetos en la escena.
3.  La aplicación también llamará a en el servicio, obteniendo información sobre el objeto que el usuario ha abordado más en las últimas 24 horas. Ese objeto cambiará su color a verde.

Este curso le enseñará a obtener los resultados del servicio de Application Insights, en una aplicación de ejemplo basada en Unity. Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 309: Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens. Al usar HoloLens, puede observar algún Eco durante la captura de voz.

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
- Un conjunto de auriculares con un micrófono integrado (si el casco no tiene micrófonos y altavoces integrados)
- Acceso a Internet para la instalación de Azure y Application Insights la recuperación de datos

## <a name="before-you-start"></a>Antes de comenzar

Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).

> [!WARNING] 
> Tenga en cuenta que los datos que van a *Application Insights* lleva tiempo, por lo que debe ser paciente. Si desea comprobar si el servicio ha recibido los datos, consulte el [capítulo 14](#chapter-14---the-application-insights-service-portal), que le mostrará cómo navegar por el portal.

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: Azure portal

Para usar *Application Insights*, debe crear y configurar un *servicio de Application Insights* en la Azure portal.

1.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *Application Insights*y haga clic en **entrar**.

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  La nueva página a la derecha proporcionará una descripción del servicio *aplicación de Azure Insights* . En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  Una vez que haya hecho clic en **crear**:

    1.  Inserte el **nombre** que desee para esta instancia de servicio.

    2.  Como **tipo de aplicación**, seleccione **General**.

    3.  Seleccione una **suscripción**adecuada.

    4.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Seleccione una **Ubicación**.

    6.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7.  Seleccione **Crear**.

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de *servicio de Application Insights* .

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Mantenga esta página web abierta y fácil de acceder; volverá a menudo para ver los datos recopilados.

    > [!IMPORTANT]
    > Para implementar Application Insights, debe usar tres (3) valores específicos: **Clave de instrumentación**, **ID**. de aplicación y **clave de API**. A continuación, verá cómo recuperar estos valores desde el servicio. Asegúrese de anotar estos valores en una página en blanco del *Bloc* de notas, ya que los usará pronto en el código.

9.  Para buscar la **clave de instrumentación**, deberá desplazarse hacia abajo en la lista de funciones de servicio y hacer clic en **propiedades**; la pestaña que se muestra revelará la **clave de servicio**.

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. A continuación **, encontrará un**poco más bajo propiedades, en **las**que tendrá que hacer clic. En el panel de la derecha se proporcionará el identificador de la **aplicación** .

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. Con el panel **ID. de aplicación** todavía abierto, haga clic en **crear clave de API**, que abrirá el panel *crear clave de API* .

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. En el panel abrir ahora *crear clave de API* , escriba una descripción y **marque los tres cuadros**.

13. Haga clic en **generar clave**. Se creará y mostrará la **clave de API** . 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Esta es la única vez que se mostrará la **clave de servicio** , por lo que debe asegurarse de hacer una copia de ella ahora.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2: configurar el proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **nuevo**.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-11.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity e insertar **Mr\_Azure\_Application\_Insights**. Asegúrese de que la *plantilla* está establecida en **3D**. Establezca la *Ubicación* en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-12.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**. Vaya a **Editar \> preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-13.png)

4.  A continuación, vaya **a \> configuración de compilación de archivos** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-14.png)

5.  Vaya a **configuración \> de compilación de archivos** y asegúrese de que:

    1.  El **dispositivo de destino** se establece en **cualquier dispositivo**

        > Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.

    2.  El **tipo de compilación** se establece en **D3D**

    3.  **SDK** está establecido en la **versión más reciente instalada**

    4.  **Compilar y ejecutar** está establecido en **equipo local**

    5.  Guarde la escena y agréguela a la compilación.

        1.  Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-15.png)

        2. Cree una nueva carpeta para esta y cualquier escena futura, haga clic en el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-16.png)

        3. Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo:* , escriba **ApplicationInsightsScene**y haga clic en **Guardar**.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-17.png)

6.  El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.

7.  En la ventana **configuración de compilación** , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-18.png)

8. En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  **Scripting** La **versión del tiempo de ejecución** debe ser **Experimental (.net 4,6 equivalente)** , lo que desencadenará una necesidad de reiniciar el editor.

        2.  El **back-end** de scripting debe ser **.net**

        3.  El **nivel de compatibilidad de API** debe ser **.net 4,6**

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-19.png)

    2.  En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        - **InternetClient**     

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-20.png)

    3.  Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-21.png)

9.  De nuevo en la **configuración de compilación**, los **proyectos de Unity C#**  ya no están atenuados; Marque la casilla situada junto a este.

10.  Cierre la ventana Configuración de compilación.

11.  Guarde la escena y el proyecto (**archivo** > **Guardar escena/archivo** > **Guardar proyecto**).


## <a name="chapter-3---import-the-unity-package"></a>Capítulo 3: importación del paquete Unity

> [!IMPORTANT]
> Si desea omitir los componentes de *configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [Azure-Mr-309. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html). También contendrá los archivos DLL del siguiente capítulo. Después de la importación, continúe en el [**capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Para usar Application Insights en Unity, debe importar el archivo DLL para él, junto con el archivo DLL de Newtonsoft. Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.

Para importar Application Insights en su propio proyecto, asegúrese de que ha [descargado el ". unitypackage Tools", que contiene los complementos](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). A continuación, haga lo siguiente:

1.  Agregue el **. unitypackage Tools** a Unity mediante la opción de menú de  **\> paquetes \> importar paquete personalizado** de paquetes.

2.  En el cuadro **importar paquete Unity** que aparece, asegúrese de que todo lo que hay en **Complementos** (y incluido) está seleccionado.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-22.png)

3.  Haga clic en el botón **importar** para agregar los elementos al proyecto.

4.  Vaya a la  carpeta Insights en **Complementos** en la vista de proyecto y seleccione *solo*los siguientes complementos:

    -   Microsoft. ApplicationInsights

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-23.png)

5.  Con este *complemento* seleccionado, asegúrese de que **cualquier plataforma** esté desactivada, Asegúrese de que **WSAPlayer** también está desactivado y haga clic en **aplicar**. Para ello, solo hay que confirmar que los archivos están configurados correctamente.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Al marcar los complementos de este modo, se configuran para que solo se usen en el editor de Unity. Hay un conjunto diferente de archivos dll en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.

6.  A continuación, debe abrir la carpeta **WSA** , dentro de la  carpeta Insights. Verá una copia del mismo archivo que acaba de configurar. Seleccione este archivo y, a continuación, en el inspector, asegúrese de que  **cualquier plataforma** esté desactivada y, a continuación, asegúrese de que **solo** **WSAPlayer** está **activada**. Haga clic en **Aplicar**.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25.png)

7. Ahora tendrá que seguir **los pasos 4-6**, pero para los complementos de *Newtonsoft* en su lugar. Vea la captura de pantalla siguiente para saber cuál debe ser el resultado.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capítulo 4: configurar la cámara y los controles de usuario

En este capítulo, configurará la cámara y los controles para que el usuario pueda ver y desplace en la escena.

1.  Haga clic con el botón secundario en un área vacía del panel jerarquía y, después, en **crear** > **vacío**.

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-26.png)

2.  Cambie el nombre de la nueva GameObject vacía a **cámara primaria**.

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-27.png)

3.  Haga clic con el botón secundario en un área vacía del panel de jerarquías y, después, en el **objeto 3D**, en **esfera**.

4.  Cambie el nombre de la esfera a **derecha**.

5.  Establezca la **escala de transformación** de la mano derecha en **0,1, 0,1, 0,1**

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-28.png)

6.  Quite el componente Colisionador de **esfera** de la mano derecha; para ello, haga clic en el **engranaje** del componente Colisionador de *esfera* y, a continuación, **Quite el componente**.

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-29.png)

7.  En el panel jerarquía, arrastre la **cámara principal** y los objetos de la **mano derecha** al objeto primario de la **cámara** .

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-30.png)

8.  Establezca la **posición de transformación** de la **cámara principal** y del objeto de la **derecha** en **0, 0,** 0.

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-31.png)

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capítulo 5: configuración de los objetos de la escena de Unity

Ahora creará algunas formas básicas para la escena, con las que el usuario puede interactuar.

1.  Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D**y seleccione **plano**.

2.  Establezca la posición de la **transformación** del plano en **0,-1, 0**.

3.  Establezca la escala de la **transformación** del plano en **5, 1, 5**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-33.png)

4.  Cree un material básico para usarlo con el objeto de **plano** , de modo que las demás formas sean más fáciles de ver. Vaya al *panel del proyecto*, haga clic con el botón secundario y, a continuación, **cree**, seguido de la **carpeta**, para crear una nueva carpeta. Asígnele el nombre **materiales**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-34.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-35.png)

5.  Abra la carpeta **materiales** y, a continuación, haga clic con el botón secundario en, haga clic en **crear**y luego en **material**para crear un nuevo material. Asígnele el nombre **Blue**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-36.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-37.png)

6.  Con el nuevo material **azul** seleccionado, examine el *Inspector*y haga clic en la ventana rectangular junto a **Albedo**. Seleccione un color azul (la imagen siguiente es **el color hexadecimal: \#3592FFFF**). Haga clic en el botón cerrar cuando haya elegido.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-38.png)

7.  Arrastre el nuevo material desde la carpeta **materiales** hasta el **plano**que acaba de crear, dentro de la escena (o colóquelo en el objeto de **plano** dentro de la *jerarquía*).

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-39.png)

8.  Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D, cápsula**.

    -  Con la **cápsula** seleccionada, cambie su  *posición* de transformación a: **-10, 1, 0**.

9.  Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D, cubo**.

    -  Con el **cubo** seleccionado, cambie su  *posición* de transformación a: **0, 0, 10**.

10. Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D, esfera**.

    -  Con la **esfera** seleccionada, cambie su  *posición* de transformación a: **10, 0,0**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Estos valores de *posición* son *sugerencias*. Puede establecer las posiciones de los objetos en el que desee, aunque es más fácil para el usuario de la aplicación si las distancias de los objetos no están demasiado lejos de la cámara.

11. Cuando la aplicación se está ejecutando, debe ser capaz de identificar los objetos dentro de la escena para lograrlo, es necesario etiquetarlos. Seleccione uno de los objetos y, en el panel *Inspector* , haga clic en **Agregar etiqueta...** , que intercambiará el *Inspector* con las **etiquetas & panel capas** .

    ![Configurar los objetos de la escena](images/AzureLabs-Lab309-41.png) de Unity![](images/AzureLabs-Lab309-42.png)

12. Haga clic en el signo **+ (más)** y, a continuación, escriba el nombre de la etiqueta como **ObjectInScene**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Si usa un nombre diferente para la etiqueta, deberá asegurarse de que este cambio también se convierte en los scripts de *DataFromAnalytics*, *ObjectTrigger*y *fijamente*más adelante, de modo que los objetos se encuentren y detecten dentro de la escena.

13. Con la etiqueta creada, ahora debe aplicarla a los tres objetos. En la *jerarquía*, mantenga presionada la tecla **MAYÚS** , haga clic en la **cápsula**, el **cubo**y la **esfera**, objetos y, después, en el *Inspector*, haga clic en el menú desplegable junto a **etiqueta**y, a continuación, haga clic en *ObjectInScene* etiqueta que creó.

    ![Configurar los objetos de la escena](images/AzureLabs-Lab309-44.png) de Unity![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capítulo 6: crear la clase ApplicationInsightsTracker

El primer script que debe crear es **ApplicationInsightsTracker**, que es responsable de:

1.  Creación de eventos basados en interacciones de usuario para enviar a Aplicación de Azure Insights.

2. Crear los nombres de evento adecuados, en función de la interacción del usuario.

3. Enviar eventos a la instancia de servicio de Application Insights.

Para crear esta clase:

1.  Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, en **crear** > **carpeta**. Asigne a la carpeta el nombre scripts.

    ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Con la  carpeta scripts creada, haga doble clic en ella para abrirla. A continuación, en esa carpeta, haga clic con el botón secundario en **crear**  >   **C# script**. Asigne al script el nombre **ApplicationInsightsTracker**.

3.  Haga doble clic en el nuevo script **ApplicationInsightsTracker** para abrirlo con **Visual Studio**.

4.  Actualice los espacios de nombres en la parte superior del script para que sea como se indica a continuación:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Dentro de la clase, inserte las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Establezca los valores **instrumentationKey, ApplicationID y API_Key** de forma adecuada, con las *claves de servicio* de Azure portal, como se mencionó en el [capítulo 1](#chapter-1---the-azure-portal), en el paso 9, en adelante.

6.  A continuación, agregue los métodos **Start ()** y Activate **()** , a los que se llamará cuando se inicialice la clase:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Agregue los métodos responsables de enviar los eventos y las métricas registrados por la aplicación:

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-7---create-the-gaze-script"></a>Capítulo 7: creación del script de mira

El siguiente script que se va a  crear es el script de miras. Este script es responsable de crear un *Raycast* que se proyectará hacia delante desde la *cámara principal*, para detectar qué objeto está examinando el usuario. En este caso, *Raycast* deberá identificar si el usuario está viendo un objeto con la etiqueta **ObjectInScene** y, a continuación, contar cuánto tiempo el usuario *mira* el objeto.

1.  Haga doble clic en la  carpeta scripts para abrirla.

2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**. Asigne un nombre **al script.**

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Reemplace el código existente por lo siguiente:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  Ahora es necesario agregar el código para los métodos **activo ()** e **Inicio ()** .

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  Dentro de la clase **fijamente** , agregue el siguiente código en el método **Update ()** para proyectar un *Raycast* y detectar el acierto de destino:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Agregue el método **ResetFocusedObject ()** para enviar datos a **Application Insights** cuando el usuario haya examinado un objeto.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  Ya ha completado el script  de miras. Guarde los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capítulo 8: creación de la clase ObjectTrigger

El siguiente script que debe crear es **ObjectTrigger**, que es responsable de:

- Agregando componentes necesarios para la colisión a la cámara principal.
- Detectar si la cámara está cerca de un objeto etiquetado como **ObjectInScene**.

Para crear el script:

1.  Haga doble clic en la  carpeta scripts para abrirla.

2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**. Asigne al script el nombre **ObjectTrigger**.

3.  Haga doble clic en el script para abrirlo con Visual Studio. Reemplace el código existente por lo siguiente:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capítulo 9: creación de la clase DataFromAnalytics

Ahora tendrá que crear el script **DataFromAnalytics** , que es responsable de:

- Recuperación de datos de análisis sobre qué objeto se ha aproximado a la cámara.
- Con las *claves de servicio*, que permiten la comunicación con la instancia de servicio de aplicación de Azure Insights.
- Ordenar los objetos en la escena, según el número de eventos más alto.
- Cambiar el color del material, del objeto más enfocado, a *verde*.

Para crear el script:

1.  Haga doble clic en la  carpeta scripts para abrirla.

2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**. Asigne al script el nombre **DataFromAnalytics**.

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Inserte los espacios de nombres siguientes:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  En el script, inserte lo siguiente:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  Dentro de la clase **DataFromAnalytics** , justo después del método **Start ()** , agregue el siguiente método denominado **FetchAnalytics ()** . Este método es responsable de rellenar la lista de pares clave-valor, con un *GameObject* y un número de recuento de eventos de marcador de posición. A continuación, inicializa la corutina **GetWebRequest ()** . La estructura de la consulta de la llamada a *Application Insights* se puede encontrar también en este método, como punto de conexión de la *dirección URL* de la consulta.

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Justo debajo del método **FetchAnalytics ()** , agregue un método denominado **GetWebRequest ()** , que devuelve una *IEnumerator*. Este método es responsable de solicitar el número de veces que se ha llamado a un evento, que corresponde a un *GameObject*específico, dentro de *Application Insights*. Cuando se devuelven todas las consultas enviadas, se llama al método **DetermineWinner ()** .

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  El siguiente método es **DetermineWinner ()** , que ordena la lista de pares *GameObject* e *int* , según el recuento de eventos más alto. A continuación, cambia el color del material de ese *GameObject* a *verde* (como comentarios sobre el recuento más alto). Se muestra un mensaje con los resultados del análisis.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Agregue la estructura de clase que se usará para deserializar el objeto JSON, recibida de *Application Insights*. Agregue estas clases en la parte inferior del archivo de la clase **DataFromAnalytics** , **fuera** de la definición de clase.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-10---create-the-movement-class"></a>Capítulo 10: creación de la clase movimiento

El script de **movimiento** es el siguiente script que tendrá que crear. Es responsable de:

- Mover la cámara principal según la dirección que está buscando la cámara.
- Agregar todos los demás scripts a los objetos de la escena.

Para crear el script:

1.  Haga doble clic en la  carpeta scripts para abrirla.

2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**. Asigne un nombre al **movimiento**del script.

3.  Haga doble clic en el script para abrirlo con *Visual Studio*.

4.  Reemplace el código existente por lo siguiente:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  Dentro de la clase de **movimiento** , *debajo* del método **Update ()** vacío, inserte los siguientes métodos que permiten al usuario usar el controlador de mano para desplazarse por el espacio virtual:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Por último, agregue la llamada al método en el método **Update ()** .

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capítulo 11: configuración de las referencias de scripts

En este capítulo, debe colocar el script de **movimiento** en el **elemento primario** de la cámara y establecer sus objetivos de referencia. Después, ese script controlará la colocación de los demás scripts en los que sea necesario.

1.  En la  carpeta scripts del *panel Proyecto*, arrastre el script de **movimiento** hasta el objeto primario de la **cámara** , situado en el *Panel jerarquía*.

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-48.png)

2.  Haga clic en el **elemento primario**de la cámara. En el *Panel jerarquía*, arrastre el objeto **situado** a la derecha desde el *Panel jerarquía* hasta el destino de referencia, **controlador**, en el *panel Inspector*. Establezca la **velocidad del usuario** en **5**, tal como se muestra en la imagen siguiente.

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capítulo 12: compilar el proyecto de Unity

Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.

1.  Vaya a **configuración de compilación**(**configuración de compilación**de**archivos** > ).

2.  En la ventana **configuración de compilación** , haga clic en compilar.

    ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-50.png)

3.  Aparecerá una ventana del **Explorador de archivos** que le pedirá una ubicación para la compilación. Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre compilaciones.

    ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-51.png)

    1.  Abra la nueva  carpeta Compilaciones y cree otra carpeta (con la **nueva carpeta** una vez más) y asígnele el nombre **Mr\_\_Azure Application\_Insights**.

        ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-52.png)

    2.  Con la **carpeta\_Mr\_de\_Azure Application Insights** seleccionada, haga clic en **Seleccionar carpeta**. El proyecto tardará un minuto o más en compilarse.

4.  Después de la *compilación*, aparecerá el **Explorador de archivos** que muestra la ubicación del nuevo proyecto.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Capítulo 13: implementación de la aplicación MR_Azure_Application_Insights en el equipo

Para implementar la aplicación de **\_Azure\_\_Application Insights Mr** en el equipo local:

1.  Abra el archivo de solución de **la\_aplicación\_Mr\_de Azure Application Insights** en **Visual Studio**.

2.  En la **plataforma**de la solución, seleccione **x86, equipo local**.

3.  En la **configuración de soluciones** , seleccione Depurar.

    ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-53.png)

4.  Vaya al **menú** compilar y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.

5.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

6. Inicie la aplicación de realidad mixta.

7. Desplazarse por la escena, cerca de los objetos y observando ellos, cuando el *servicio Azure Insights* haya recopilado suficientes datos de eventos, establecerá el objeto que se ha centrado más en verde.

> [!IMPORTANT] 
> Aunque el tiempo de espera promedio de los *eventos y* las métricas que va a recopilar el servicio tarda aproximadamente 15 minutos, en algunas ocasiones, puede tardar hasta 1 hora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capítulo 14: portal de servicios de Application Insights

Una vez que haya movido en torno a la escena y haya mirado en varios objetos, puede ver los datos recopilados en el portal de *servicios de Application Insights* .

1.  Vuelva al portal de servicios de Application Insights.

2.  Haga clic en *Explorador de métricas*.

    ![Examinar los datos recopilados](images/AzureLabs-Lab309-54.png)

3.  Se abrirá en una pestaña que contiene el gráfico que representa los *eventos y* las métricas relacionados con la aplicación. Como se mencionó anteriormente, es posible que se tarde un tiempo (hasta 1 hora) en mostrar los datos en el gráfico.

    ![Examinar los datos recopilados](images/AzureLabs-Lab309-55.png)

4.  Haga clic en la *barra eventos* en el *total de eventos* por versión de la aplicación para ver un desglose detallado de los eventos con sus nombres.

    ![Examinar los datos recopilados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Su aplicación de servicio de Application Insights finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio de Application Insights para supervisar la actividad del usuario dentro de la aplicación.

![resultado del curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

**Ejercicio 1**

Pruebe a generar, en lugar de crear manualmente, los objetos ObjectInScene y establecer sus coordenadas en el plano dentro de los scripts. De esta manera, podría solicitar a Azure lo que era el objeto más popular (ya sea desde los resultados de mirarnos o de proximidad) y generar uno *extra* de esos objetos.

**Ejercicio 2**

Ordene los resultados de la Application Insights por hora, para obtener los datos más relevantes e implementar esos datos confidenciales en la aplicación.

