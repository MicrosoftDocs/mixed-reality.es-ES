---
title: El Sr. y Azure 306 - Streaming de vídeo
description: Realice este curso para obtener información sobre cómo implementar Azure Media Services dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, streaming de media services, vídeo, 360, envolventes, vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599487"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>El Sr. y Azure 306: Transmisión de vídeo

![final producto-iniciar](images/AzureLabs-Lab6-00.png)
![producto final-inicio](images/AzureLabs-Lab6-01.png)

En este curso, aprenderá cómo conectar Azure Media Services con una experiencia de Windows Mixed Reality VR para permitir la reproducción de vídeo de 360 grados en inmersivos de transmisión por secuencias. 

**Azure Media Services** son una colección de servicios que proporciona servicios de transmisión por secuencias vídeo con calidad de difusión para llegar a audiencias de mayor en los dispositivos móviles más populares de hoy en día. Para obtener más información, visite la [página de Azure Media Services](https://azure.microsoft.com/services/media-services).

Una vez completado este curso, tendrá una aplicación de envolventes auriculares de realidad mixta, que podrá hacer lo siguiente:

1. Recuperar un vídeo de 360 grados de un **Azure Storage**, mediante el **servicios multimedia de Azure**.

2. Mostrar el vídeo de 360 grados recuperados en una escena de Unity.

3. Navegar entre las dos escenas, con dos vídeos diferentes.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 306: Transmisión de vídeo</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar el artículo herramientas](install-the-tools.md), aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK más reciente de Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md)
- Acceso a Internet para la recuperación de datos e instalación de Azure
- Dos vídeos de 360 grados en formato mp4 (puede encontrar algunos vídeos libre de regalías [en esta página de descarga](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).
2.  Configurar y probar los auriculares envolventes de realidad mixta.

    > [!NOTE]
    > Podrá **no** requieren controladores de movimiento de este curso. Si necesita admite la configuración de los auriculares envolventes, por favor, haga clic en [vínculo sobre cómo configurar Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Capítulo 1: el Portal de Azure: creación de la cuenta de almacenamiento de Azure

Para usar el **servicio Azure Storage**, deberá crear y configurar un **cuenta de almacenamiento** en Azure portal.

1.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **cuentas de almacenamiento** en el menú izquierdo.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab6-02.png)

3.  En el **cuentas de almacenamiento** pestaña, haga clic en **agregar**.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab6-03.png)

4.  En el **crear cuenta de almacenamiento** pestaña:

    1.  Insertar un **nombre** para su cuenta, tenga en cuenta este campo sólo acepta números y letras minúsculas.

    2.  Para **modelo de implementación,** seleccione **Administrador de recursos**.

    3.  Para **tipo de cuenta**, seleccione **almacenamiento (uso general v1)**.

    4.  Para **rendimiento**, seleccione **estándar*.**

    5.  Para **replicación** seleccione **almacenamiento con redundancia local (LRS)**.

    6.  Deje **se requiere transferencia segura** como **deshabilitado**.

    7.  Seleccione un **suscripción**.

    8.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.

    9.  Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

5.  Deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab6-04.png)

6.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

7.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab6-05.png)

8.  En este momento no es necesario seguir el recurso, simplemente mueva al siguiente capítulo.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Capítulo 2: el Portal de Azure: creación del servicio multimedia

Para usar los servicios de multimedia de Azure, deberá configurar una instancia del servicio esté disponible para la aplicación (en la que el titular de la cuenta debe ser un administrador).

1.  En el Portal de Azure, haga clic en **crear un recurso** en la esquina superior izquierda esquina y busque **servicio multimedia,** presione **ENTRAR**. El recurso que desee actualmente tiene un icono de color rosado; Haga clic aquí para mostrar una página nueva.

    ![El Portal de Azure](images/AzureLabs-Lab6-06.png)

2.  La nueva página proporcionará una descripción de la **servicio multimedia**. En la parte inferior izquierda de este símbolo del sistema, haga clic en el **crear** botón para crear una asociación con este servicio.

    ![El Portal de Azure](images/AzureLabs-Lab6-07.png)

3.  Una vez que ha hecho clic **crear** se mostrará un panel donde debe proporcionar algunos detalles sobre los nuevos servicios de multimedia:

    1.  Insertar el elemento **nombreCuenta** para esta instancia de servicio.

    2.  Seleccione un **suscripción**.

    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes). 
    
    > Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar grupos de recursos de Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    5.  Para el **cuenta de almacenamiento** sección, haga clic en el **seleccione...**  sección y, después, haga clic en el **cuenta de almacenamiento** que creó en el último capítulo.

    6.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    7.  Haga clic en **Crear**.

        ![El Portal de Azure](images/AzureLabs-Lab6-08.png)

4.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

5.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![El Portal de Azure](images/AzureLabs-Lab6-09.png)

6.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![El Portal de Azure](images/AzureLabs-Lab6-10.png)

7.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.

8.  En la página de servicio de medios nuevo, dentro del panel de la izquierda, haga clic en el **activos** vínculo, que es aproximadamente la mitad inferior.

9.  En la página siguiente, en la esquina superior izquierda de la página, haga clic en **cargar**.

    ![El Portal de Azure](images/AzureLabs-Lab6-11.png)

10. Haga clic en el **carpeta** icono para examinar los archivos y seleccione el vídeo en primer lugar 360 que le gustaría hacer streaming. 
    
    > Puede seguir este [vínculo para descargar un vídeo de ejemplo](https://vimeo.com/214401712).

    ![El Portal de Azure](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Los nombres de archivo largo pueden producir un error con el codificador: por lo que para asegurarse de vídeos no tienen problemas, considere la posibilidad de acortar la longitud de los nombres de archivo de vídeo.

11. La barra de progreso se pondrá verde cuando el vídeo ha terminado de cargarse.

    ![El Portal de Azure](images/AzureLabs-Lab6-13.png)

12. Haga clic en el texto anterior (**yourservicename - activos**) para volver a la **activos** página.

13. Observará que el vídeo se ha cargado correctamente. Haga clic en él.

    ![El Portal de Azure](images/AzureLabs-Lab6-14.png)

14. La página a que se le redirigirá mostrará que información detallada sobre el vídeo. Para poder usar el vídeo tiene que codificar, haciendo clic en el **Encode** situado en la parte superior izquierda de la página.

    ![El Portal de Azure](images/AzureLabs-Lab6-15.png)

15. Un nuevo panel aparecerán a la derecha, donde podrá establecer opciones de codificación para el archivo. Establezca las propiedades siguientes (algunos ya establecerá de forma predeterminada):

    1.  **Nombre del Codificador multimedia *Media Encoder Standard***

    2.  **Valor preestablecido de codificación *Content Adaptive Multiple Bitrate MP4***

    3.  **Nombre del trabajo *el procesamiento de Video1.mp4 Media Encoder Standard***

    4.  **Nombre del recurso multimedia salida *Video1.mp4--Media Encoder Standard con codificación***

        ![El Portal de Azure](images/AzureLabs-Lab6-16.png)

16. Haga clic en el botón **Crear**.

17. Aparece una barra con **trabajo de codificación que se va a agregar**, haga clic en esa barra y aparecerá un panel con el progreso de codificación se muestran en él.

    ![El Portal de Azure](images/AzureLabs-Lab6-17.png)

    ![El Portal de Azure](images/AzureLabs-Lab6-18.png)

18. Espere a que el trabajo se complete. Una vez hecho, puede cerrar el panel con la 'X' en la esquina superior derecha de dicho panel.

    ![El Portal de Azure](images/AzureLabs-Lab6-19.png)

    ![El Portal de Azure](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > El tiempo que tarde, depende del tamaño de archivo del vídeo. Este proceso puede tardar bastante tiempo.

19. Ahora que se ha creado la versión codificada del vídeo, puede publicarla para que sea accesible. Para ello, haga clic en el vínculo azul **activos** para volver a la página de recursos.

    ![El Portal de Azure](images/AzureLabs-Lab6-21.png)

20. Podrá ver el vídeo junto con otro, que es de **tipo de activo*MP4 de velocidad de bits múltiple***.

    ![El Portal de Azure](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Es posible que observe que el nuevo recurso, junto con el vídeo inicial, se *desconocido*, y tiene "0" bytes para es **tamaño**, simplemente actualice la ventana para actualizar.

21. Haga clic en este nuevo recurso.

    ![El Portal de Azure](images/AzureLabs-Lab6-23.png)

22. Verá un panel similar al usado antes, simplemente se trata de un recurso diferente. Haga clic en el **publicar** situado en la parte superior central de la página.

    ![El Portal de Azure](images/AzureLabs-Lab6-24.png)

23. Se le pedirá que establezca un **localizador**, que es el punto de entrada al archivo/s en sus activos. Para su escenario, establezca las propiedades siguientes:

    1.  **Tipo de localizador** > **progresiva**.

    2.  El **fecha** y **tiempo** se establecerá automáticamente, de la fecha actual, en un momento en el futuro (cien años en este caso). Dejar tal cual o cambiarla para que se adapte a.

    > [!NOTE]
    > Para obtener más información sobre los localizadores, y puede elegir, visite la [documentación de Azure Media Services](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. En la parte inferior de ese panel, haga clic en el **agregar** botón.

    ![El Portal de Azure](images/AzureLabs-Lab6-25.png)

25. El vídeo se ha publicado y se puede transmitir mediante el uso de su punto de conexión. Más abajo la página es una **archivos** sección. Esto es donde las distintas versiones codificadas del vídeo. Seleccione la resolución más alta posible uno (en la imagen siguiente es el archivo de 1920 x 960), y, a continuación, aparecerá un panel a la derecha. Allí encontrará un **descarga URL**. Copie esta **extremo** ya que usará más adelante en el código.

    ![El Portal de Azure](images/AzureLabs-Lab6-26.png)    

    ![El Portal de Azure](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > También puede presionar el **reproducir** botón reproducir el vídeo y probarlo.

26. Deberá cargar el segundo vídeo que va a utilizar en este laboratorio. Siga los pasos anteriores, repetir el mismo proceso para el segundo vídeo. Asegúrese de copiar el segundo **extremo** también. Use el siguiente [vínculo para descargar un segundo vídeo](https://vimeo.com/214402865).

27. Una vez que se han publicado los vídeos, está listo para pasar al siguiente capítulo.

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra **Unity** y haga clic en **New**. 

    ![El Portal de Azure](images/AzureLabs-Lab6-28.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity, insertar **MR\_360VideoStreaming.**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establezca la ubicación en algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![El Portal de Azure](images/AzureLabs-Lab6-29.png)

3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio.** Vaya a ***editar* *preferencias*** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![El Portal de Azure](images/AzureLabs-Lab6-30.png)

4.  A continuación, vaya a ***archivo* *configuración de compilación*** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.

5.  También asegúrese de que:

    1. **Dispositivo de destino** está establecido en **cualquier dispositivo.**
    
    2.  **Tipo de compilación** está establecido en **D3D.**

    3.  **SDK** está establecido en **instalada más reciente.**

    4.  **Versión de Visual Studio** está establecido en **instalada más reciente.**

    5.  **Compilar y ejecutar** está establecido en **máquina Local.**

    6.  No se preocupe sobre cómo configurar **escenas** ahora mismo, tal y como se va a configurar estas más adelante.

    7.  Por ahora, se debe dejar el resto de la configuración como valor predeterminado.

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab6-31.png)

6.  En el **configuración de compilación** ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra. 

7. En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Scripting** **en tiempo de ejecución versión** debe ser **estable** (.NET 3.5 equivalente).

        2. **Scripting de back-end** debe ser **. NET.**

        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6.**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab6-32.png)

    2.  Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab6-33.png)

    3.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        - **InternetClient**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab6-34.png)

8.  Una vez realizados estos cambios, cierre el **configuración de compilación** ventana.

9.  Guarde el proyecto **archivo* *Guardar proyecto**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Capítulo 4: importar el paquete de InsideOutSphere Unity

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde **capítulo 5**. Deberá crear un proyecto de Unity.

Para este curso deberá descargar un paquete de activos de Unity, denominada [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Importación de procedimientos del **unitypackage**:

1.  Con el panel de Unity delante de usted, haga clic en **activos** en el menú en la parte superior de la pantalla, a continuación, haga clic en **Importar paquete > paquete personalizado**.

    ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-35.png)

2.  Utilice el selector de archivos para seleccionar la **InsideOutSphere.unitypackage** del paquete y haga clic en **abierto**. Se mostrará una lista de componentes para este recurso para usted. Haga clic en confirmar la importación **importar**.

    ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-36.png)

3.  Una vez que haya terminado de importarse, observará tres nuevas carpetas **materiales**, **modelos**, y **prefabricados**, se han agregado a su **activos**carpeta. Este tipo de estructura de carpetas es típico de un proyecto de Unity.

    ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-37.png)

    1.  Abra el **modelos** carpeta y verá que el **InsideOutSphere** modelo se ha importado.

    2.  Dentro de la **materiales** carpeta, encontrará el **InsideOutSpheres** material *lambert1*, junto con un material llamado *ButtonMaterial*, que se usa en el GazeButton, que verá en breve.

    3.  El **prefabricados** carpeta contiene el **InsideOutSphere** prefabricado que contiene tanto el **InsideOutSphere** *modelo* y el  *GazeButton*.

    4.  **Se incluye ningún código**, escribirá el código siguiendo este curso.


4.  Dentro de la **jerarquía**, seleccione el **cámara principal** de objetos y actualizar los componentes siguientes:

    1.  **Transformación**

        1.  Posición = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotación = **X**: 0, **Y**: 0, **Z**: 0.

        3. Escala **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Cámara**

        1. **Borrar las marcas de**: Color sólido.

        2.  **Planos de recorte**: Cerca de: 0,1, ahora: 6.

            ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-38.png)

5.  Navegue hasta la **prefabricado** carpeta y, a continuación, arrastre el **InsideOutSphere** prefabricado en el **jerarquía** Panel.

    ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-39.png)

6.  Expanda el **InsideOutSphere** objeto dentro de la **jerarquía** haciendo clic en la flecha pequeña situada junto a ella. Verá un **secundarios** objeto situado debajo de él llamado **GazeButton**. Esto se usará para cambiar a segundo plano y, por tanto, los vídeos.

    ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-40.png)

7.  En la ventana del Inspector, haga clic en el **InsideOutSphere**del componente de transformación, asegúrese de que se establecen las propiedades siguientes:

    |            |    TRANSFORMACIÓN - POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    -TRANSFORMACIÓN DE GIRO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORMACIÓN - ESCALADO     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-41.png)

8.  Haga clic en el **GazeButton** objeto secundario y establezca su **transformar** como sigue:

    |            |    TRANSFORMACIÓN - POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    -TRANSFORMACIÓN DE GIRO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMACIÓN - ESCALADO     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importar el paquete de Unity InsideOutSphere](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Capítulo 5: crear la clase VideoController

El **VideoController** clase hospeda los dos extremos de vídeo que se usará para transmitir el contenido de los servicios de multimedia de Azure.

Para crear esta clase:

1.  Haga clic en el **carpeta de activos**, que se encuentra en la **proyecto** Panel y haga clic en **crear > carpeta**. Nombre de la carpeta **Scripts**.

    ![Crear la clase VideoController](images/AzureLabs-Lab6-43.png)

    ![Crear la clase VideoController](images/AzureLabs-Lab6-44.png)

2.  Haga doble clic en el **Scripts** carpeta para abrirla.

3.  Haga clic en la carpeta, a continuación, haga clic en **crear > C\# Script**. Nombre de la secuencia de comandos **VideoController**.

    ![Crear la clase VideoController](images/AzureLabs-Lab6-45.png)

4.  Haga doble clic en el nuevo **VideoController** script para abrirlo con **Visual Studio 2017.**

    ![Crear la clase VideoController](images/AzureLabs-Lab6-46.png)

5.  Actualice los espacios de nombres en la parte superior del archivo de código de la manera siguiente:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Escriba las siguientes variables en el **VideoController** clase, junto con el **Awake()** método:

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  Ahora es el momento de escribir los puntos de conexión de los vídeos de Azure Media Services:

    1.  El primero en el *video1endpoint* variable.
    
    2.  El segundo en el *video2endpoint* variable.

    > [!WARNING]
    > Hay un problema conocido con el uso de *https* dentro de Unity con versión 2017.4.1f1. Si los vídeos proporcionan un error en play, intente usar 'http' en su lugar.

8.  A continuación, el **Start()** método debe modificarse. Este método se desencadenará cada vez que el usuario cambia la escena (conmutación en consecuencia el vídeo) examinando el botón que mirar.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Siguiendo el **Start()** método, inserte el **PlayVideo()** *IEnumerator* método, que se usará para iniciar vídeos sin problemas (por lo que no se ve ningún entrecortarse).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. El último método necesario para esta clase es el **ChangeScene()** método, que se usará para intercambiar entre bastidores.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > El **ChangeScene()** método usa una práctica C\# característica denominada el *operador condicional*. Esto permite que las condiciones que se va a comprobar y, a continuación, los valores devuelven según el resultado de la comprobación, todo ello en una sola instrucción. Siga este [vínculo para obtener más información sobre el operador condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

11. Guarde los cambios en Visual Studio antes de volver a Unity.

12. En el Editor de Unity, haga clic en Atrás y arrastre el **VideoController** clase [from] {.underline} el **Scripts** carpeta para el **cámara principal** objeto en el  **Jerarquía** Panel.

13. Haga clic en el **cámara principal** y examine el **Panel Inspector**. Observará que en el componente de Script recién agregado, es un campo con un valor vacío. Se trata de un campo de referencia, que tiene como destino las variables públicas dentro del código.

14. Arrastre el **InsideOutSphere** objeto desde el **jerarquía Panel** a la **esfera** ranura, tal como se muestra en la imagen siguiente.

    ![Crear la clase VideoController](images/AzureLabs-Lab6-47.png)
    ![crear la clase VideoController](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Capítulo 6: crear la clase de mirada

Esta clase es responsable de crear un **Raycast** que beprojected reenviará desde el **cámara principal**, para detectar el objeto que está mirando el usuario. En este caso, el **Raycast** tendrá que identificar si el usuario está viendo la **GazeButton** de objetos de la escena y desencadenar un comportamiento.

Para crear esta clase:

1.  Vaya a la **Scripts** carpeta que creó anteriormente.

2.  Haga clic en el **proyecto** Panel, **crear* *C\# Script**. Nombre de la secuencia de comandos **que mirar**.

3.  Haga doble clic en el nuevo ***que mirar*** script para abrirlo con **Visual Studio 2017.**

4.  Asegúrese de que es el espacio de nombres siguiente en la parte superior de la secuencia de comandos y quite cualquier otro:

    ```csharp
    using UnityEngine;
    ```

5.  A continuación, agregue las siguientes variables dentro de la **que mirar** clase:

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  El código para el **Awake()** y **Start()** métodos ahora debe agregarse.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Agregue el código siguiente en el **Update()** método proyectar una Raycast y detectar el posicionamiento de destino:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Guarde los cambios en Visual Studio antes de volver a Unity.

9.  Haga clic y arrastre el **que mirar** clase a partir de la carpeta Scripts en el objeto de cámara principal en el **jerarquía** Panel.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Capítulo 7: configuración de las dos escenas de Unity

El propósito de este capítulo es configurar las dos escenas, cada hospedar un vídeo en secuencia. Duplicará la escena que ya ha creado, por lo que no es necesario configurar de nuevo, aunque, a continuación, modificará la nueva escena, para que la *GazeButton* objeto está en una ubicación diferente y tiene una apariencia diferente. Esto es mostrar cómo cambiar entre bastidores.

1.  Para ello, vaya a **archivo > Guardar escena como...** . Aparecerá el guardado de la ventana. Haga clic en el **nueva carpeta** botón.

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-49.png)

2.  Nombre de la carpeta **escenas**.

3.  El **Guardar escena** ventana todavía estará abierto. Abra el recién creado **escenas** carpeta.

4.  En el **nombre de archivo:** campo de texto, escriba **VideoScene1**, a continuación, presione **guardar**.

5.  En Unity, abra su **escenas** carpeta y haga clic en su **VideoScene1** archivo. Usar el teclado y presione **Ctrl + D** duplicará dicha escena

    > [!TIP]
    > El **duplicar** comando también pueden realizarse yendo a **Editar > Duplicar**.

6.  Unity automáticamente incrementar el número de nombres de la escena, pero compruébelo en cualquier caso, para asegurarse de coincide con el código insertado previamente.

    >  Debe tener **VideoScene1** y **VideoScene2**.

7.  Con sus dos escenas, vaya a **archivo > configuración de compilación**. Con el **configuración de compilación** ventana abierta, arrastre el segundo plano para el **escenas en compilación** sección.

    ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Puede seleccionar ambos sus escenas de su **escenas** carpeta a través de explotación el **Ctrl** button y, a continuación, hace clic cada escena y, por último, arrastre ambos a través.

8.  Cerrar la **configuración de compilación** ventana y haga doble clic en **VideoScene2**.

9.  Con la segunda escena abierta, haga clic en el **GazeButton** objeto secundario de la **InsideOutSphere**y establezca su transformación como sigue:

    |            |    TRANSFORMACIÓN - POSICIÓN   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    -TRANSFORMACIÓN DE GIRO   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMACIÓN - ESCALADO     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Con el **GazeButton** secundarios aún seleccionado, busque en el **Inspector** y en el **Mesh filtro**. Haga clic en el destino poco junto a la **malla** campo de referencia:

    ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-51.png)

11. Un **seleccione malla** aparecerá la ventana emergente. Haga doble clic en el **cubo** de malla en la lista de **activos**.

    ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-52.png)

12. El **Mesh filtro** actualizará y estar ahora un **cubo**. Ahora, haga clic en el **engranaje** icono situado junto al **esfera Colisionador** y haga clic en **quitar componente**, para eliminar el colisionador de este objeto.

    ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-53.png)

13. Con el **GazeButton** aún seleccionado, haga clic en el **Agregar componente** situado en la parte inferior de la **Inspector**. En el campo de búsqueda, escriba **cuadro**, y **Colisionador de cuadro** se sea una opción, haga clic en el que, para agregar un **Colisionador de cuadro** a su **GazeButton** objeto .

    ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-54.png)

14. El **GazeButton** es ahora se actualizó parcialmente, para tener un aspecto diferente, sin embargo, ahora creará un nuevo **Material**, de modo que tiene un aspecto completamente diferente lo que es más fácil de reconocer como un objeto diferente, que el objeto en la primera escena.

15. Vaya a su **materiales** carpeta, en el **Panel proyecto**. Duplicar la **ButtonMaterial** Material (presione **Ctrl** + **d.** en el teclado o haga clic en el **Material**, a continuación, desde el **editar** archivo la opción de menú, seleccione **duplicar**).

    ![Capítulo 7: Configurar las dos escenas Unity](images/AzureLabs-Lab6-55.png)
    ![capítulo 7: configurar las dos escenas de Unity](images/AzureLabs-Lab6-56.png)

16. Seleccione la nueva **ButtonMaterial** Material (denominada aquí **ButtonMaterial 1**) y dentro del **Inspector**, haga clic en el **Albedo** color ventana. Aparecerá una ventana emergente, donde puede seleccionar otro color (elija el que desee), a continuación, cierre la ventana emergente. El Material será su propia instancia y es diferente al original.

    ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-57.png)

17. Arrastre el nuevo **Material** hasta la **GazeButton** secundario ahora actualizar completamente su apariencia, para que resulte diferenciar fácilmente desde el primer botón de escenas.

    ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-58.png)

18. En este momento puede probar el proyecto en el Editor antes de compilar el proyecto para UWP.

    -  Presione el **reproducir** situado en la **Editor** y use los auriculares.

        ![Capítulo 7: Configurar las dos escenas de Unity](images/AzureLabs-Lab6-59.png)

19. Examine los dos **GazeButton** objetos para cambiar entre el primer y segundo vídeo.

## <a name="chapter-8---build-the-uwp-solution"></a>Capítulo 8: Compile la solución UWP

Una vez que se ha asegurado de que el editor no tiene errores, está listo para la compilación.

Para compilar:

1.  Guarde la escena actual haciendo clic en **archivo > Guardar**.

2.  Active la casilla denominada **Unity C\# proyectos** (Esto es importante porque permite editar las clases, una vez completada la compilación).

3.  Vaya a **archivo > configuración de compilación**, haga clic en **compilar**.

4.  Se le pedirá que seleccione la carpeta donde desea buildthe solución.

5.  Crear un **compilaciones** carpeta y dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.

6.  Haga clic en la nueva carpeta y, a continuación, haga clic en **seleccionar la carpeta**, por lo tanto, para elegir esa carpeta, para iniciar la compilación en esa ubicación.

    ![Capítulo 8: Compile la solución UWP](images/AzureLabs-Lab6-60.png)
    ![capítulo 8: Compile la solución UWP](images/AzureLabs-Lab6-61.png)

7.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación.

## <a name="chapter-9---deploy-on-local-machine"></a>Capítulo 9: implementar en el equipo Local

Una vez completada la compilación, un **Explorador de archivos** ventana aparecerá en la ubicación de la compilación. Abra la carpeta denominada e integrado, a continuación, haga doble clic en el archivo de solución (.sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.

La única cosa por hacer es implementar la aplicación en el equipo (o *máquina Local*).

Para implementar una máquina Local:

1.  En **Visual Studio 2017**, abra el archivo de solución que se acaba de crear.

2.  En el **plataforma de solución**, seleccione **x86, equipo Local**.

3.  En el **configuración de la solución** seleccione **depurar**.

    ![Capítulo 9: Implementar en el equipo Local](images/AzureLabs-Lab6-62.png)

4.  Ahora deberá restaurar todos los paquetes a la solución. Haga doble clic en su **solución**y haga clic en **restaurar paquetes de NuGet para la solución...**

    > [!NOTE] 
    > Esto se hace porque los paquetes que generaron Unity deben tener como destino para trabajar con las referencias de las máquinas locales.

5.  Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo. Visual Studio cree primero y, a continuación, implementar la aplicación.

6.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.

    ![Capítulo 9: Implementar en el equipo Local](images/AzureLabs-Lab6-63.png)

Cuando se ejecuta la aplicación de realidad mixta, tendrá estar dentro del **InsideOutSphere** modelo que usa dentro de la aplicación. Esta esfera será donde se transmitirá el vídeo, proporcionando una vista de 360 grados, de vídeo entrante (que se graban para este tipo de perspectiva). No se sorprenda que si el vídeo tarda unos segundos en cargarse, la aplicación está sujeta a la velocidad de Internet disponible, como el vídeo necesita se capturan y, a continuación, descargar, por lo tanto, para transmitir a la aplicación.
Cuando esté listo, cambie el segundo plano y abra el segundo vídeo, por gazing en la esfera roja! A continuación, no dude en volver atrás, con el cubo azul en la segunda escena!

## <a name="your-finished-azure-media-service-application"></a>La aplicación de servicios multimedia de Azure finalizada
 
Enhorabuena, compila una aplicación de realidad mixta que aprovecha los servicios de multimedia de Azure para transmitir 360 vídeos.

![Resultado de laboratorio](images/AzureLabs-Lab6-00.png)

![Resultado de laboratorio](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

**Ejercicio 1**

Es totalmente posible usar solo una sola escena cambiar vídeos dentro de este tutorial. Experimente con la aplicación y convertirlo en una sola escena. Quizás incluso agregar otro vídeo a la combinación.

**Ejercicio 2**

Experimentar con Azure y Unity e intente implementar la capacidad de la aplicación seleccionar automáticamente un vídeo con un tamaño de archivo diferente, dependiendo de la fortaleza de una conexión a Internet.


