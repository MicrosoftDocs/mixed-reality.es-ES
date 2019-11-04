---
title: MR espacial 230-asignación espacial
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de asignación espacial.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, asignación espacial, reconstrucción superficial, malla
ms.openlocfilehash: cf4a2dd3e5eb74c0aaf849442e5f5e404d7cb661
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434572"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR espacial 230: asignación espacial

La [asignación espacial](spatial-mapping.md) combina el mundo real y el mundo virtual juntos mediante la enseñanza de hologramas sobre el entorno. En MR Spatial 230 (Project Planetarium), veremos cómo:

* Examinar el entorno y transferir los datos desde HoloLens a su equipo de desarrollo.
* Explore los sombreadores y aprenda a usarlos para visualizar el espacio.
* Divida la malla de la habitación en planos simples mediante el procesamiento de malla.
* Vaya más allá de las técnicas de selección de ubicación que hemos aprendido en los [conceptos básicos de MR 101](holograms-101.md)y proporcione comentarios sobre dónde se puede colocar un holograma en el entorno.
* Explore los efectos de la oclusión, de modo que cuando el holograma esté detrás de un objeto del mundo real, todavía puede verlo con la visión x-Ray.

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>MR espacial 230: asignación espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).
* Funcionalidad básica C# de programación.
* Debe haber completado los [principios básicos 101](holograms-101.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) requeridos por el proyecto. Requiere Unity 2017,2 o posterior.
  * Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Notas

* "Habilitar Solo mi código" en Visual Studio debe estar deshabilitado *(desactivado*) en herramientas > opciones > depuración para poder alcanzar puntos de interrupción en el código.

## <a name="unity-setup"></a>Configuración de Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Inicie **Unity**.
* Seleccione **nuevo** para crear un nuevo proyecto.
* Asigne al proyecto el nombre **Planetarium**.
* Compruebe que está seleccionada la opción **3D** .
* Haz clic en **Create Project** (Crear proyecto).
* Una vez que se inicia Unity, vaya a **editar > configuración del proyecto > Player**.
* En el panel **Inspector** , busque y seleccione el icono verde de la **tienda Windows** .
* Expanda **otros valores**.
* En la sección **representación** , active la opción se **admite la realidad virtual** .
* Compruebe que **Windows Holographic** aparece en la lista de **SDK de realidad virtual**. Si no es así, seleccione el botón **+** situado en la parte inferior de la lista y elija **Windows Holographic**.
* Expanda **configuración de publicación**.
* En la sección **capacidades** , Compruebe la siguiente configuración:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Micrófono
    * SpatialPerception
* Vaya a **editar > configuración del proyecto > calidad**
* En el panel **Inspector** , bajo el icono de la tienda Windows, seleccione la flecha de lista desplegable negra situada debajo de la fila "predeterminada" y cambie la configuración predeterminada a **muy baja**.
* Vaya a **activos > importar paquete > paquete personalizado**.
* Vaya a la carpeta **. ..\holographicacademy-holograms-230-SpatialMapping\Starting** .
* Haga clic en **Planetarium. unitypackage Tools**.
* Haz clic en **Abrir**.
* Debe aparecer una ventana **importar paquete Unity** , haga clic en el botón **importar** .
* Espere a que Unity importe todos los recursos que se van a necesitar para completar este proyecto.
* En el panel **jerarquía** , elimine la **cámara principal**.
* En el panel **proyecto** , en la carpeta **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** , busque el objeto de **cámara principal** .
* Arrastre y coloque la **cámara principal** recurso prefabricado en el panel de **jerarquías** .
* En el panel **jerarquía** , elimine el objeto de **luz direccional** .
* En el panel **proyecto** , carpeta **hologramas** , busque el objeto **cursor** .
* Arrastre & Coloque el **cursor** recurso prefabricado en la **jerarquía**.
* En el panel **jerarquía** , seleccione el objeto **cursor** .
* En el panel **Inspector** , haga clic en la lista desplegable **capa** y seleccione **Editar capas.**
* Nombre de la **capa de usuario 31** como "**SpatialMapping**".
* Guarde la nueva escena: **archivo > guardar la escena como...**
* Haga clic en **nueva carpeta** y asigne un nombre a la carpeta **Scenes**.
* Asigne al archivo el nombre "**Planetarium**" y guárdelo en la carpeta **Scenes** .

## <a name="chapter-1---scanning"></a>Capítulo 1: exploración

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Objetivos**

* Obtenga información sobre SurfaceObserver y cómo su configuración afecta a la experiencia y el rendimiento.
* Cree una experiencia de detección de salones para recopilar las mallas de su habitación.

**Las**

* En la carpeta **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** del panel de **proyecto** , busque el **SpatialMapping** recurso prefabricado.
* Arrastre & Coloque el recurso prefabricado de **SpatialMapping** en el panel de **jerarquías** .

**Compilación e implementación (parte 1)**

* En Unity, seleccione **archivo > configuración de compilación**.
* Haga clic en **Agregar escenas abiertas** para agregar la escena **Planetarium** a la compilación.
* Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.
* Establezca el **tipo de compilación** **SDK** en **universal 10** y UWP en **D3D**.
* Compruebe **los C# proyectos de Unity**.
* Haz clic en **Compilación**.
* Cree una **nueva carpeta** denominada "app".
* Haga clic en la carpeta de la **aplicación** .
* Presione el botón **Seleccionar carpeta** .
* Cuando Unity termine de compilar, aparecerá una ventana del explorador de archivos.
* Haga doble clic en la carpeta de la **aplicación** para abrirla.
* Haga doble clic en **Planetarium. sln** para cargar el proyecto en Visual Studio.
* En Visual Studio, use la barra de herramientas superior para cambiar la configuración a **Release**.
* Cambie la plataforma a **x86**.
* Haga clic en la flecha desplegable situada a la derecha de "equipo local" y seleccione **equipo remoto**.
* Escriba la [dirección IP del dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) en el campo Dirección y cambie el modo de autenticación a **universal (protocolo sin cifrar)** .
* Haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.
* Vea el panel de **salida** en Visual Studio para ver el estado de compilación e implementación.
* Una vez que la aplicación se haya implementado, desplazarse por la habitación. Verá las superficies circundantes que se incluyen en mallas de alambres en blanco y negro.
* Digitalice su entorno. Asegúrese de mirar paredes, techos y suelos.

**Compilación e implementación (parte 2)**

Ahora vamos a explorar cómo la asignación espacial puede afectar al rendimiento.

* En Unity, seleccione **Window > Profiler**.
* Haga clic en **Agregar generador de perfiles > GPU**.
* Haga clic en **Active Profiler > <Enter IP>** .
* Escriba la **dirección IP** de su HoloLens.
* Haz clic en **Connect**.
* Observe el número de milisegundos que tarda la GPU en representar un fotograma.
* Detenga la ejecución de la aplicación en el dispositivo.
* Vuelva a Visual Studio y Abra **SpatialMappingObserver.CS**. Lo encontrará en la carpeta HoloToolkit\SpatialMapping del proyecto Assembly-CSharp (universal Windows).
* Busque la función Activate **()** y agregue la siguiente línea de código: **TrianglesPerCubicMeter = 1200;**
* Vuelva a implementar el proyecto en el dispositivo y, a continuación, vuelva a **conectar el generador de perfiles**. Observe el cambio en el número de milisegundos para representar un fotograma.
* Detenga la ejecución de la aplicación en el dispositivo.

**Guardar y cargar en Unity**

Por último, vamos a guardar la malla de sala y cargarla en Unity.

* Vuelva a Visual Studio y quite la línea **TrianglesPerCubicMeter** que agregó en la función Activate **()** en la sección anterior.
* Vuelva a implementar el proyecto en el dispositivo. Ahora deberíamos ejecutarse con triángulos **500** por metro cúbico.
* Abra un explorador y escriba en la dirección IP de HoloLens para ir al **portal de dispositivos de Windows**.
* Seleccione la opción **vista 3D** en el panel izquierdo.
* En **reconstrucción superficial** , seleccione el botón **Actualizar** .
* Observe que las áreas que ha examinado en HoloLens aparecen en la ventana de visualización.
* Presione el botón **Guardar** para guardar el análisis de la habitación.
* Abra la carpeta **downloads** para buscar el modelo Room **SRMesh. obj**guardado.
* Copie **SRMesh. obj** en la carpeta **assets** del proyecto de Unity.
* En Unity, seleccione el objeto **SpatialMapping** en el panel de **jerarquías** .
* Busque el componente de **observador de superficie de objeto (Script)** .
* Haga clic en el círculo situado a la derecha de la propiedad **modelo Room** .
* Busque y seleccione el objeto **SRMesh** y, a continuación, cierre la ventana.
* Compruebe que la propiedad **modelo de habitación** del panel **Inspector** está ahora establecida en **SRMesh**.
* Presione el botón **reproducir** para entrar en el modo de vista previa de Unity.
* El componente SpatialMapping cargará las mallas del modelo de habitación guardado para que pueda usarlas en Unity.
* Cambie a la vista **escena** para ver todo el modelo de habitación mostrado con el sombreador de tramas de alambres.
* Vuelva a presionar el botón **reproducir** para salir del modo de vista previa.

**Nota:** La próxima vez que escriba el modo de vista previa en Unity, se cargará la malla de habitación guardada de forma predeterminada.

## <a name="chapter-2---visualization"></a>Capítulo 2: visualización

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Objetivos**

* Conozca los aspectos básicos de los sombreadores.
* Visualice su entorno.

**Las**

* En el panel de **jerarquías** de Unity, seleccione el objeto **SpatialMapping** .
* En el panel **Inspector** , busque el componente **Administrador de asignación espacial (Script)** .
* Haga clic en el círculo situado a la derecha de la propiedad material de la **superficie** .
* Busque y seleccione el material **BlueLinesOnWalls** y cierre la ventana.
* En la carpeta **sombreadores** del panel de **proyecto** , haga doble clic en **BlueLinesOnWalls** para abrir el sombreador en Visual Studio.
* Se trata de un sombreador de píxeles sencillo (vértice a fragmento), que realiza las tareas siguientes:
    1. Convierte la ubicación de un vértice en el espacio universal.
    2. Comprueba la normal del vértice para determinar si un píxel es vertical.
    3. Establece el color del píxel que se va a representar.

**Compilación e implementación**

* Vuelva a Unity y presione **reproducir** para entrar en el modo de vista previa.
* Las líneas azules se representarán en todas las superficies verticales de la malla de habitación (que se cargan automáticamente a partir de los datos de exámenes guardados).
* Cambie a la pestaña **escena** para ajustar la vista de la habitación y ver cómo aparece toda la malla de habitación en Unity.
* En el panel **proyecto** , busque la carpeta **materiales** y seleccione el material **BlueLinesOnWalls** .
* Modifique algunas propiedades y vea cómo aparecen los cambios en el editor de Unity.
    * En el panel **Inspector** , ajuste el valor **LineScale** para que las líneas aparezcan más gruesas o más delgadas.
    * En el panel **Inspector** , ajuste el valor **LinesPerMeter** para cambiar el número de líneas que aparecen en cada muro.
* Haga clic en **reproducir** de nuevo para salir del modo de vista previa.
* Compile e implemente en HoloLens y observe cómo aparece la representación del sombreador en superficies reales.

Unity hace un gran trabajo de obtener una vista previa de los materiales, pero siempre es una buena idea desproteger la representación en el dispositivo.

## <a name="chapter-3---processing"></a>Capítulo 3: procesamiento

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Objetivos**

* Aprenda técnicas para procesar datos de asignación espacial para su uso en la aplicación.
* Analizar datos de asignación espacial para buscar planos y Quitar triángulos.
* Usar planos para la colocación de hologramas.

**Las**

* En el panel de **proyectos** de Unity, carpeta **hologramas** , busque el objeto **SpatialProcessing** .
* Arrastre & Coloque el objeto **SpatialProcessing** en el panel de **jerarquías** .

SpatialProcessing recurso prefabricado incluye componentes para procesar los datos de asignación espacial. **SurfaceMeshesToPlanes.CS** buscará y generará planos basados en los datos de asignación espacial. Usaremos planos en nuestra aplicación para representar paredes, suelos y techos. Este recurso prefabricado también incluye **RemoveSurfaceVertices.CS** , que puede quitar vértices de la malla de asignación espacial. Se puede usar para crear huecos en la malla o para quitar los triángulos sobrantes que ya no son necesarios (porque en su lugar se pueden usar planos).

* En el panel de **proyectos** de Unity, carpeta **hologramas** , busque el objeto **SpaceCollection** .
* Arrastre y coloque el objeto **SpaceCollection** en el panel de **jerarquías** .
* En el panel **jerarquía** , seleccione el objeto **SpatialProcessing** .
* En el panel **Inspector** , busque el componente de **Administrador de espacio de reproducción (Script)** .
* Haga doble clic en **PlaySpaceManager.CS** para abrirlo en Visual Studio.

PlaySpaceManager.cs contiene código específico de la aplicación. Agregaremos funcionalidad a este script para habilitar el comportamiento siguiente:

1. Detener la recopilación de datos de asignación espacial después de superar el límite de tiempo de examen (10 segundos).
2. Procesar los datos de asignación espacial:
    1. Use SurfaceMeshesToPlanes para crear una representación más sencilla del mundo como planos (paredes, suelos, techos, etc.).
    2. Use RemoveSurfaceVertices para quitar los triángulos de superficie que se encuentran dentro de los límites del plano.
3. Generar una colección de hologramas en el mundo y colocarlos en planos murales y en planta cercanos al usuario.

Complete los ejercicios de codificación marcados en PlaySpaceManager.cs o reemplace el script por la solución terminada que aparece a continuación:

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**Compilación e implementación**

* Antes de implementar en HoloLens, presione el botón **reproducir** en Unity para entrar en el modo de reproducción.
* Después de cargar la malla de sala desde el archivo, espere 10 segundos antes de que se inicie el procesamiento en la malla de asignación espacial.
* Una vez completado el procesamiento, aparecerán los planos para representar el suelo, las paredes, el límite superior, etc.
* Una vez que se hayan encontrado todos los planos, debería ver que aparece un sistema solar en una tabla de piso cerca de la cámara.
* También deberían aparecer dos pósteres en las paredes cerca de la cámara. Cambie a la pestaña **escena** si no puede verla en el modo de **juego** .
* Vuelva a presionar el botón **reproducir** para salir del modo de reproducción.
* Compilar e implementar en HoloLens, como de costumbre.
* Espere a que se complete el análisis y el procesamiento de los datos de la asignación espacial.
* Una vez que vea los planos, intente encontrar el sistema solar y los pósteres de su mundo.

## <a name="chapter-4---placement"></a>Capítulo 4: selección de ubicación

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Objetivos**

* Determine si un holograma se ajustará en una superficie.
* Proporcione comentarios al usuario cuando un holograma pueda o no quepa en una superficie.

**Las**

* En el panel de **jerarquías** de Unity, seleccione el objeto **SpatialProcessing** .
* En el panel **Inspector** , busque el componente de **mallas de superficie en los planos (Script)** .
* Cambie la propiedad **Draw aviones** a **Nothing** para borrar la selección.
* Cambie la propiedad **Draw aviones** a **Wall**para que solo se representen los planos de pared.
* En el panel **proyecto** , en la carpeta **scripts** , haga doble clic en **placeable.CS** para abrirlo en Visual Studio.

El script que se pueda **colocar** ya está adjunto a los pósters y al cuadro de proyección que se crearon una vez completada la búsqueda de planos. Lo único que debemos hacer es quitar la marca de comentario de código y este script logrará lo siguiente:

1. Determine si un holograma se ajustará en una superficie raycasting desde el centro y cuatro esquinas del cubo de límite.
2. Compruebe la superficie normal para determinar si es lo suficientemente suave para que el holograma permanezca en el vaciado.
3. Representa un cubo de límite alrededor del holograma para mostrar su tamaño real mientras se coloca.
4. Convierta una sombra debajo/detrás del holograma para mostrar dónde se colocará en el piso o la pared.
5. Representa la sombra en rojo si el holograma no se puede colocar en la superficie, o en verde, si es posible.
6. Vuelva a orientar el holograma para alinearlo con el tipo de superficie (vertical u horizontal) al que tiene afinidad.
7. Coloque suavemente el holograma en la superficie seleccionada para evitar saltar o ajustar el comportamiento.

Quite la marca de comentario de todo el código del ejercicio de codificación siguiente o use esta solución completada en **placeable.CS**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**Compilación e implementación**

* Como antes, compile el proyecto e impleméntelo en HoloLens.
* Espere a que se complete el análisis y el procesamiento de los datos de la asignación espacial.
* Cuando vea el sistema solar, mira en el cuadro proyección siguiente y realiza un gesto de selección para moverlo. Mientras se selecciona el cuadro proyección, un cubo de límite estará visible alrededor del cuadro de proyección.
* Desplácese hacia mira en una ubicación diferente de la habitación. El cuadro proyección debe seguir su mirada. Cuando la sombra situada debajo del cuadro proyección se vuelve roja, no se puede colocar el holograma en esa superficie. Cuando la sombra situada debajo del cuadro proyección se vuelve verde, puede colocar el holograma realizando otro gesto seleccionar.
* Busque y seleccione uno de los pósteres holográficas en una pared para moverlo a una nueva ubicación. Tenga en cuenta que no puede colocar el póster en el piso o el límite superior, y que permanece correctamente orientado a cada pared mientras se desplaza.

## <a name="chapter-5---occlusion"></a>Capítulo 5: oclusión

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Objetivos**

* Determine si la malla de asignación espacial ocluidos un holograma.
* Aplique distintas técnicas de oclusión para lograr un efecto divertido.

**Las**

En primer lugar, vamos a permitir que la malla de asignación espacial tapaba otros hologramas sin occluding el mundo real:

* En el panel **jerarquía** , seleccione el objeto **SpatialProcessing** .
* En el panel **Inspector** , busque el componente de **Administrador de espacio de reproducción (Script)** .
* Haga clic en el círculo situado a la derecha de la propiedad **material secundario** .
* Busque y seleccione el material de **oclusión** y cierre la ventana.

A continuación, vamos a agregar un comportamiento especial a la tierra, de modo que tenga un resaltado azul cada vez que se ocluidos por otro holograma (por ejemplo, el sol) o por la malla de asignación espacial:

* En el panel **proyecto** , en la carpeta **hologramas** , expanda el objeto **SolarSystem** .
* Haga clic en **tierra**.
* En el panel **Inspector** , busque el material de la tierra (componente inferior).
* En el **menú desplegable del sombreador**, cambie el sombreador a **personalizado > OcclusionRim**. Esto representará un resaltado azul alrededor de tierra siempre que se ocluidos por otro objeto.

Por último, vamos a habilitar un efecto x-Ray Vision para los planetas de nuestro sistema solar. Tendremos que editar **PlanetOcclusion.CS** (que se encuentra en la carpeta Scripts\SolarSystem) para lograr lo siguiente:

1. Determinar si el nivel de SpatialMapping (mallas y planos de la habitación) ocluidos un planeta.
2. Muestra la representación en alambre de un planeta siempre que se ocluidos por el nivel de SpatialMapping.
3. Oculte la representación en alambre de un planeta cuando no esté bloqueada por el nivel SpatialMapping.

Siga el ejercicio de codificación de PlanetOcclusion.cs o use la siguiente solución:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**Compilación e implementación**

* Compile e implemente la aplicación en HoloLens, como de costumbre.
* Espere a que se completen el análisis y el procesamiento de los datos de la asignación espacial (debe ver que aparecen líneas azules en las paredes).
* Busque y seleccione el cuadro proyección del sistema solar y, a continuación, establezca el cuadro junto a una pared o detrás de un contador.
* Para ver la oclusión básica, oculte las superficies detrás del mismo nivel en el póster o en el cuadro de proyección.
* Busque la tierra; debe haber un efecto de resaltado azul cada vez que se encuentre detrás de otro holograma o superficie.
* Observe que los planetas se mueven detrás de la pared u otras superficies de la habitación. Ahora tiene una visión de rayos x y puede ver sus esqueletos de alambres.

## <a name="the-end"></a>Fin

Enhorabuena. Ha completado **MR 230: asignación espacial**.

* Sabe cómo analizar el entorno y cargar datos de asignación espacial en Unity.
* Comprende los aspectos básicos de los sombreadores y cómo se pueden usar los materiales para volver a visualizar el mundo.
* Ha aprendido las nuevas técnicas de procesamiento para buscar planos y Quitar triángulos de una malla.
* Puede trasladar y colocar hologramas en superficies que tengan sentido.
* Ha experimentado diferentes técnicas de oclusión y ha aprovechado la potencia de la visión de rayos x.
