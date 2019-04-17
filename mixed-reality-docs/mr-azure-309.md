---
title: El Sr. y Azure 309 - Application insights
description: Realice este curso para obtener información sobre cómo recopilar análisis relacionadas con el comportamiento de los usuarios dentro de una aplicación de realidad mixta, mediante el servicio de Azure Application Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, información de la aplicación, hololens, envolventes, vr
ms.openlocfilehash: 838dbe38724d29f4c5987e2f6ac7a07231015c82
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605718"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>El Sr. y Azure 309: Información de la aplicación

![final producto-inicio](images/AzureLabs-Lab309-00.png)

En este curso, obtendrá información sobre cómo agregar funcionalidades de Application Insights a una aplicación de realidad mixta, mediante la API de Azure Application Insights para recopilar análisis de comportamiento del usuario.

Application Insights es un servicio de Microsoft, lo que permite a los desarrolladores recopilar análisis de sus aplicaciones y administrarla desde un portal fácil de usar. El análisis pueden ser cualquier cosa, desde rendimiento a la información personalizada que desea recopilar. Para obtener más información, visite la [página Application Insights](https://azure.microsoft.com/services/application-insights/).

Una vez completado este curso, tendrá una aplicación de envolventes auriculares de realidad mixta que podrá hacer lo siguiente:

1.  Permitir que el usuario que mirar y para desplazarse por una escena.
2.  Desencadenar el envío de análisis para el *servicio Application Insights*, mediante el uso de mirada y proximidad a los objetos en la escena.
3.  También llamará la aplicación en el servicio, la obtención de información acerca del objeto que ha sido abordó la mayor parte por el usuario, dentro de las últimas 24 horas. Ese objeto cambiará su color en verde.

Este curso le mostrará cómo obtener los resultados desde el servicio de Application Insights, en una aplicación de ejemplo basada en Unity. Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 309: Información de la aplicación</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens. Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.

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
- Un conjunto de auriculares con micrófono integrado (si no tiene los auriculares altavoces y un micrófono integrado)
- Acceso a Internet para el programa de instalación de Azure y la recuperación de datos de Application Insights

## <a name="before-you-start"></a>Antes de empezar

Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).

> [!WARNING] 
> Tenga en cuenta, los datos que van a *Application Insights* lleva tiempo, así que los paciente. Si desea comprobar si el servicio ha recibido los datos, consulte [capítulo 14](#chapter-14---the-application-insights-service-portal), que le mostrará cómo navegar por el portal.

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: el Portal de Azure

Para usar *Application Insights*, deberá crear y configurar un *servicio Application Insights* en Azure portal.

1.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Application Insights*y haga clic en **ENTRAR**.

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  La nueva página a la derecha proporcionará una descripción de la *Azure Application Insights* Service. En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  Una vez que ha hecho clic **crear**:

    1.  Insertar el elemento **nombre** para esta instancia de servicio.

    2.  Como **tipo de aplicación**, seleccione **General**.

    3.  Seleccione un **suscripción**.

    4.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Seleccione un **ubicación**.

    6.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7.  Selecciona **Crear**.

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva *servicio Application Insights* instancia.

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Mantenga abierta esta página web y de fácil acceso, procederá a este punto a menudo para ver los datos recopilados.

    > [!IMPORTANT]
    > Para implementar Application Insights, deberá usar los valores específicos de tres (3): **Clave de instrumentación**, **Id. de aplicación**, y **clave de API**. A continuación verá cómo recuperar estos valores desde el servicio. Asegúrese de que tener en cuenta estos valores en un espacio en blanco *el Bloc de notas* página, ya que lo usará pronto en el código.

9.  Para buscar el **clave de instrumentación**, deberá desplazarse hacia abajo en la lista de funciones de servicio y haga clic en **propiedades**, se mostrará la pestaña muestra la **clave de servicio**.

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. Un poco a continuación **propiedades**, encontrará **acceso a la API**, que tiene que hacer clic. El panel a la derecha le proporcionará la **Id. de aplicación** de la aplicación.

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. Con el **Id. de aplicación** panel sigue abierto, haga clic en **Create API Key**, que abrirá el *crear clave de API* panel.

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. Dentro de la apertura ahora *crear clave de API* del panel, escriba una descripción, y **los tres cuadros de graduación**.

13. Haga clic en **generar clave**. Su **clave de API** se crean y se mostrará. 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Esta es la única vez su **clave de servicio** se mostrará, así que asegúrese de realizar ahora una copia del mismo.

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **New**.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-11.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity, insertar **MR\_Azure\_aplicación\_Insights**. Asegúrese de que el *plantilla* está establecido en **3D**. Establecer el *ubicación* a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-12.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a **editar \> preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-13.png)

4.  A continuación, vaya a **archivo \> configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-14.png)

5.  Vaya a **archivo \> configuración de compilación** y asegúrese de que:

    1.  **Dispositivo de destino** está establecido en **cualquier dispositivo**

        > Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.

    2.  **Tipo de compilación** está establecido en **D3D**

    3.  **SDK** está establecido en **instalada más reciente**

    4.  **Compilar y ejecutar** está establecido en **máquina Local**

    5.  Guarde la escena y agregarlo a la compilación.

        1.  Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-15.png)

        2. Cree una nueva carpeta para este y cualquier futura escena, a continuación, haga clic en el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-16.png)

        3. Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo:* campo de texto, escriba **ApplicationInsightsScene**, a continuación, haga clic en **guardar**.

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-17.png)

6.  El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.

7.  En el **configuración de compilación** ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-18.png)

8. En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Scripting** **en tiempo de ejecución versión** debe ser **Experimental (.NET 4.6 equivalente)**, que desencadenará una necesidad de reiniciar el Editor.

        2.  **Scripting de back-end** debe ser **.NET**

        3.  **Nivel de compatibilidad de API** debe ser **.NET 4.6**

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-19.png)

    2.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        - **InternetClient**     

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-20.png)

    3.  Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **Windows Mixed Reality SDK** se agrega.

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-21.png)

9.  En **configuración de compilación**, **Unity C\# proyectos** ya no está atenuada; Marque la casilla situada junto a esto.

10.  Cierre la ventana de configuración de compilación.

11.  Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).


## <a name="chapter-3---import-the-unity-package"></a>Capítulo 3: importar el paquete de Unity

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componentes de este curso y continuar directamente en código, no dude en descargar este [MR-Azure-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html). Esto también contendrá los archivos DLL en el capítulo siguiente. Después de la importación, continuar desde [ **capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Para usar Application Insights en Unity, deberá importar el archivo DLL, junto con la DLL de Newtonsoft. Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación. Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.

Para importar Application Insights en su propio proyecto, asegúrese de que haya [descargado '.unitypackage', que contiene los complementos](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). A continuación, haga lo siguiente:

1.  Agregar el **.unitypackage** a Unity mediante el uso de la **activos \> Importar paquete \> paquete personalizado** opción de menú.

2.  En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-22.png)

3.  Haga clic en el **importación** botón para agregar los elementos al proyecto.

4.  Vaya a la **Insights** carpeta bajo **complementos** en el proyecto, ver y seleccione los siguientes complementos *sólo*:

    -   Microsoft.ApplicationInsights

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-23.png)

5.  Con esto *complemento* seleccionado, asegúrese de que **cualquier plataforma** es **desactivada**, a continuación, asegúrese de que **WSAPlayer** también es  **unchecked**, a continuación, haga clic en **aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Marcar los complementos como esta, configura que solo se utilicen en el Editor de Unity. Hay un conjunto diferente de DLL en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.

6.  A continuación, deberá abrir el **WSA** carpeta, en el **Insights** carpeta. Verá una copia del mismo archivo que acaba de configurar. Seleccione este archivo y, a continuación, en el inspector, asegúrese de que **cualquier plataforma** es **unchecked**, a continuación, asegúrese de que **sólo** **WSAPlayer** es **comprueban**. Haga clic en **Aplicar**.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25.png)

7. Ahora deberá seguir **los pasos 4 a 6**, pero para el *Newtonsoft* complementos en su lugar. Consulte la siguiente captura de pantalla de aspecto que debería tener el resultado.

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Capítulo 4: configuración de la cámara y el usuario controles

En este capítulo configurará la cámara y los controles para permitir al usuario ver y mover de la escena.

1.  Haga doble clic en un área vacía en el Panel de la jerarquía, a continuación, en **crear > vacío**.

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-26.png)

2.  Cambiar el nombre del nuevo GameObject vacío a **cámara primaria**.

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-27.png)

3.  Haga doble clic en un área vacía en el Panel de la jerarquía, a continuación, en **objeto 3D**, a continuación, en **esfera**.

4.  Cambiar el nombre de la esfera **derecho**.

5.  Establecer el **transformar escala** de la mano derecha para **0,1, 0,1, 0,1**

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-28.png)

6.  Quitar el **esfera Colisionador** componente desde el lado derecho, haga clic en el **engranaje** en el *esfera Colisionador* componente y, a continuación, **quitar componente** .

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-29.png)

7.  En la operación de arrastrar al Panel de la jerarquía la **cámara principal** y **mano derecha** objetos la **cámara primaria** objeto.

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-30.png)

8.  Establecer el **posición transformar** de ambos el **cámara principal** y el **mano derecha** objeto **0, 0, 0**.

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-31.png)

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Capítulo 5: configurar los objetos de la escena de Unity

Ahora creará algunas formas básicas para la escena, con el que el usuario puede interactuar.

1.  Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D**, a continuación, seleccione **plano**.

2.  Definir el plano **transformar posición** a **0, -1, 0**.

3.  Definir el plano **transformar escala** a **5, 1, 5**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-33.png)

4.  Crear un material básico para usar con su **plano** objeto, para que sean fáciles de ver las demás formas. Vaya a su *Panel proyecto*, con el botón secundario, a continuación, **crear**, seguido de **carpeta**, para crear una nueva carpeta. Asígnele el nombre **materiales**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-34.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-35.png)

5.  Abrir el **materiales** carpeta y, a continuación, haga clic **crear**, a continuación, **Material**, para crear un nuevo material. Asígnele el nombre **azul**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-36.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-37.png)

6.  Con el nuevo **azul** material seleccionado, busque en el *Inspector*y haga clic en la ventana rectangular junto con **Albedo**. Seleccione un color azul (es la siguiente uno imagen **de Color hexadecimal: \#3592FFFF**). Haga clic en el botón Cerrar cuando haya elegido.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-38.png)

7.  Arrastre el nuevo material de la **materiales** carpeta, en la recién creado **plano**, dentro de su escena (o colóquela en la **plano** objeto dentro de la  *Jerarquía*).

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-39.png)

8.  Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D, Capsule**.

    -  Con el **Capsule** seleccionado, cambie su **transformar** *posición* a: **-10, 1, 0**.

9.  Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D, cubo**.

    -  Con el **cubo** seleccionado, cambie su **transformar** *posición* para: **0, 0, 10**.

10. Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D, esfera**.

    -  Con el **esfera** seleccionado, cambie su **transformar** *posición* para: **10, 0, 0**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Estos *posición* los valores son *sugerencias*. Es libre para establecer las posiciones de los objetos que desee, aunque es más fácil para el usuario de la aplicación si las distancias de objetos no son demasiado lejos de la cámara.

11. Cuando se ejecuta la aplicación, debe ser capaz de identificar los objetos dentro de la escena, para lograr esto, se deben etiquetar. Seleccione uno de los objetos y, en el *Inspector* del panel, haga clic en **Agregar etiqueta...** , que intercambiará el *Inspector* con el **etiquetas & capas** panel.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. Haga clic en el **+ (signo más)** de símbolos, a continuación, escriba el nombre de etiqueta como **ObjectInScene**.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Si usa un nombre diferente para la etiqueta, deberá asegurarse de que este cambio también se realiza el *DataFromAnalytics*, *ObjectTrigger*, y *que mirar*, scripts más adelante, para que su objetos se encuentra y detecta, dentro de la escena.

13. Con la etiqueta que se creó, debe aplicarlo a las tres de los objetos. Desde el *jerarquía*, mantenga el **MAYÚS** clave, a continuación, haga clic en el **Capsule**, **cubo**, y **esfera**, objetos, a continuación, en el *Inspector*, haga clic en el menú desplegable junto a **etiqueta**, a continuación, haga clic en el *ObjectInScene* de etiquetas que ha creado.

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Capítulo 6: crear la clase ApplicationInsightsTracker

Es el primer script, deberá crear **ApplicationInsightsTracker**, que es responsable de:

1.  Creación de eventos en función de las interacciones del usuario para enviar a Azure Application Insights.

2. Creación de nombres de evento adecuados, según la interacción del usuario.

3. Envío de eventos a la instancia del servicio Application Insights.

Para crear esta clase:

1.  Haga clic en el *Panel del proyecto*, a continuación, **crear > carpeta**. Nombre de la carpeta **Scripts**.

    ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  Con el **Scripts** carpeta creada, haga doble clic en él para abrirlo. A continuación, dentro de esa carpeta, con el botón secundario, **crear > C\# Script**. Nombre de la secuencia de comandos **ApplicationInsightsTracker**.

3.  Haga doble clic en el nuevo **ApplicationInsightsTracker** script para abrirlo con **Visual Studio**.

4.  Actualice los espacios de nombres en la parte superior de la secuencia de comandos como sigue:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Dentro de la clase inserte las siguientes variables:

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
    > Establecer el **instrumentationKey, applicationId y API_Key** valores como corresponda, utilizando el *las claves del servicio* desde el Portal de Azure como se mencionó en [capítulo 1](#chapter-1---the-azure-portal), paso 9 y versiones posteriores.

6.  A continuación, agregue el **Start()** y **Awake()** métodos, que se llamará cuando se inicializa la clase:

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

7.  Agregue los métodos que se encarga de enviar los eventos y las métricas registradas por la aplicación:

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

## <a name="chapter-7---create-the-gaze-script"></a>Capítulo 7: crear la secuencia de comandos de mirada

Es el script siguiente para crear el **que mirar** secuencia de comandos. Este script es responsable de crear un *Raycast* que se proyectará hacia delante desde el *cámara principal*, para detectar el objeto que está mirando el usuario. En este caso, el *Raycast* tendrá que identificar si el usuario está viendo un objeto con el **ObjectInScene** etiqueta y, a continuación, contabilizar el tiempo que el usuario *gazes* en ese objeto.

1.  Haga doble clic en el **Scripts** carpeta para abrirla.

2.  Haga clic en el **Scripts** carpeta, haga clic en **crear** > **C\# Script**. Nombre de la secuencia de comandos **que mirar**.

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Reemplace el código existente con lo siguiente:

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

5.  El código para el **Awake()** y **Start()** métodos ahora debe agregarse.

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

6.  Dentro de la **que mirar** de clases, agregue el código siguiente en el **Update()** método al proyecto un *Raycast* y detectar el posicionamiento de destino:

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

7.  Agregar el **ResetFocusedObject()** método envíe datos a **Application Insights** cuando el usuario ha examinado de un objeto.

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

8.  Ahora ha completado la **que mirar** secuencia de comandos. Guarde los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Capítulo 8: crear la clase ObjectTrigger

Es el siguiente script, deberá crear **ObjectTrigger**, que es responsable de:

- Agregar los componentes necesarios de colisión de la cámara principal.
- Detectar si la cámara está cerca de un objeto etiquetado como **ObjectInScene**.

Para crear la secuencia de comandos:

1.  Haga doble clic en el **Scripts** carpeta para abrirla.

2.  Haga clic en el **Scripts** carpeta, haga clic en **crear** **C\# > Script**. Nombre de la secuencia de comandos **ObjectTrigger**.

3.  Haga doble clic en el script para abrirlo con Visual Studio. Reemplace el código existente con lo siguiente:

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

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Capítulo 9: crear la clase DataFromAnalytics

Ahora deberá crear el **DataFromAnalytics** script, que es responsable de:

- Captura de datos de análisis sobre qué objeto se ha se aproxime a la cámara más.
- Mediante el *las claves del servicio*, que permiten la comunicación con la instancia de servicio de Azure Application Insights.
- Ordenar los objetos de escena, según los cuales tiene el mayor número de eventos.
- Cambiar el color del material, del objeto acerca más al *verde*.

Para crear la secuencia de comandos:

1.  Haga doble clic en el **Scripts** carpeta para abrirla.

2.  Haga clic en el **Scripts** carpeta, haga clic en **crear** **C\# > Script**. Nombre de la secuencia de comandos **DataFromAnalytics**.

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

5.  Dentro de la secuencia de comandos, inserte el siguiente:

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

6.  Dentro de la **DataFromAnalytics** class, justo después de la **Start()** método, agregue el siguiente método denominado **FetchAnalytics()**. Este método es responsable de rellenar la lista de pares clave / valor, con un *GameObject* y un número de recuento de eventos de marcador de posición. A continuación, se inicializa el **GetWebRequest()** corrutina. La estructura de consulta de la llamada a *Application Insights* puede encontrarse dentro de este método también, como el *dirección URL de consulta* punto de conexión.

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

7.  Justo debajo de la **FetchAnalytics()** método, agregue un método llamado **GetWebRequest()**, que devuelve un *IEnumerator*. Este método es responsable de que solicita el número de veces que un evento, que se corresponde con un valor concreto *GameObject*, se ha llamado dentro de *Application Insights*. Cuando se hayan devuelto todas las consultas enviadas, el **DetermineWinner()** se llama al método.

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

8.  El siguiente método es **DetermineWinner()**, que ordena la lista de *GameObject* y *Int* pares, según el mayor número de eventos. A continuación, cambia el color de dicho material *GameObject* a *verde* (como comentarios para que tenga el número más alto). Esto muestra un mensaje con los resultados del análisis.

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

9.  Agregue la estructura de clases que se usará para deserializar el objeto JSON procedente de *Application Insights*. Agregue estas clases en la parte inferior de la **DataFromAnalytics** archivo de clase, **fuera** de la definición de clase.

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

## <a name="chapter-10---create-the-movement-class"></a>Capítulo 10: crear la clase de movimiento

El **movimiento** script es el siguiente script deberá crear. Es responsable de:

- Mover la cámara principal según la dirección de la cámara mira hacia.
- Agregar todos los demás scripts a objetos de la escena.

Para crear la secuencia de comandos:

1.  Haga doble clic en el **Scripts** carpeta para abrirla.

2.  Haga clic en el **Scripts** carpeta, haga clic en **crear** > **C\# Script**. Nombre de la secuencia de comandos **movimiento**.

3.  Haga doble clic en el script para abrirlo con *Visual Studio*.

4.  Reemplace el código existente con lo siguiente:

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

5.  Dentro de la **movimiento** (clase), *debajo* vacío **Update()** método, inserte los siguientes métodos que permiten al usuario usar el controlador de mano para mover en el espacio virtual:

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

6.  Por último, agregar la llamada al método dentro de la **Update()** método.

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Capítulo 11: configuración de las referencias de scripts

En este capítulo tiene que colocar el **movimiento** de script en el **cámara primaria** y establezca sus destinos de referencia. Ese script controlará la colocación de los demás scripts donde deben estar.

1.  Desde el **Scripts** carpeta en el *Panel proyecto*, arrastre el **movimiento** scripts para la **cámara primaria** objeto, que se encuentra en la  *Panel de la jerarquía*.

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-48.png)

2.  Haga clic en el **cámara primaria**. En el *jerarquía Panel*, arrastre el **mano derecha** objeto desde el *jerarquía Panel* al destino de referencia, **controlador**, en el *Panel inspector*. Establecer el **usuario velocidad** a **5**, tal y como se muestra en la imagen siguiente.

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Capítulo 12: compilar el proyecto de Unity

Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.

1.  Vaya a **configuración de compilación**, **(archivo > configuración de compilación...)** .

2.  Desde el **configuración de compilación** ventana, haga clic en **compilar**.

    ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-50.png)

3.  Un **Explorador de archivos** will ventana emergente, que le solicitará una ubicación para la compilación. Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.

    ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-51.png)

    1.  Abra el nuevo **compilaciones** carpeta y cree otra carpeta (mediante **nueva carpeta** una vez más) y asígnele el nombre **MR\_Azure\_aplicación\_ Insights**.

        ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-52.png)

    2.  Con el **MR\_Azure\_aplicación\_Insights** carpeta seleccionada, haga clic en **seleccionar la carpeta**. El proyecto tardará un minuto o más en crear.

4.  Siga *compilar*, **Explorador de archivos** aparecerá con la ubicación del nuevo proyecto.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Capítulo 13 - implementar la aplicación MR_Azure_Application_Insights en la máquina

Para implementar el **MR\_Azure\_aplicación\_Insights** aplicación en el equipo Local:

1.  Abra el archivo de solución de su **MR\_Azure\_aplicación\_Insights** app en **Visual Studio**.

2.  En el **plataforma de solución**, seleccione **x86, equipo Local**.

3.  En el **configuración de la solución** seleccione **depurar**.

    ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-53.png)

4.  Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.

6. Inicie la aplicación de realidad mixta.

7. Mueva la escena, como elementos no utilizados los objetos y mirando, cuando el *Azure Insight Service* ha recopilado datos suficientes eventos, establecerá el objeto que se han analizado el máximo partido a verde.

> [!IMPORTANT] 
> Mientras que el tiempo de espera promedio para la *eventos y métricas* sea recopilado por el servicio tarda aproximadamente 15 minutos, en algunas ocasiones puede tardar hasta una hora.

## <a name="chapter-14---the-application-insights-service-portal"></a>Capítulo 14: el portal de Application Insights

Una vez que han movido en torno a la escena y gazed en varios objetos puede ver los datos recopilados en el *servicio Application Insights* portal.

1.  Vuelva al portal de servicio Application Insights.

2.  Haga clic en *Explorador de métricas*.

    ![Examina los datos recopilados](images/AzureLabs-Lab309-54.png)

3.  Se abrirá en una pestaña que contiene el gráfico que representan el *eventos y métricas* relacionados con la aplicación. Como se mencionó anteriormente, puede tardar algún tiempo (hasta 1 hora) para que los datos que se mostrará en el gráfico

    ![Examina los datos recopilados](images/AzureLabs-Lab309-55.png)

4.  Haga clic en el *barra eventos* en el *Total de eventos* por versión de la aplicación para ver un desglose detallado de los eventos con sus nombres.

    ![Examina los datos recopilados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Su terminado la aplicación de servicio Application Insights

Enhorabuena, creó una aplicación de realidad mixta que aprovecha el servicio Application Insights para supervisar la actividad del usuario dentro de la aplicación.

![resultado del curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

**Ejercicio 1**

Vuelva a generar, en lugar de crear manualmente los objetos ObjectInScene y establezca sus coordenadas en el plano dentro de sus scripts. De esta manera, podría pedir que Azure era qué objeto más popular (ya sea desde resultados mirada o proximidad) y generar un *adicional* uno de esos objetos.

**Ejercicio 2**

Ordenar los resultados de Application Insights por hora, para que obtenga los datos más relevantes e implementar esos datos confidenciales de tiempo en su aplicación.

