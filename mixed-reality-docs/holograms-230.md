---
title: El Sr. espacial 230 - asignación espacial
description: Siga este tutorial con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de asignación espacial de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, asignación espacial, reconstrucción expuesta, malla
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600927"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR 230 espacial: Asignación espacial

[Asignación espacial](spatial-mapping.md) combina el mundo real y el mundo virtual juntos enseñanza hologramas sobre el entorno. En el Sr. espacial 230 (apartado planetario del proyecto y disfrutará), obtendrá información sobre cómo:

* Analizar los datos de entorno y la transferencia de la HoloLens a la máquina de desarrollo.
* Explore los sombreadores y obtenga información sobre cómo usarlas para visualizar el espacio.
* Desglosar la malla del salón en planos simple mediante el procesamiento de la malla.
* Vaya más allá de las técnicas de selección de ubicación que hemos aprendido en [MR Fundamentos 101](holograms-101.md)y proporcionar comentarios sobre dónde se puede colocar un holograma en el entorno.
* Explore los efectos de oclusión, por lo que cuando su holograma está detrás de un objeto del mundo real, todavía puede ver con la visión de rayos x!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>MR 230 espacial: Asignación espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).
* Básica C# capacidad de programación.
* Debe haber completado [MR Fundamentos 101](holograms-101.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Notas

* "Habilitar Solo mi código" en Visual Studio debe estar deshabilitada (*unchecked*) en Herramientas > Opciones > depuración con el fin de alcanzar los puntos de interrupción en el código.

## <a name="unity-setup"></a>Programa de instalación de Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Iniciar **Unity**.
* Seleccione **New** para crear un nuevo proyecto.
* Denomine el proyecto **planetario y disfrutará**.
* Compruebe que la **3D** está seleccionada.
* Haga clic en **crear proyecto**.
* Una vez que se inicia en Unity, vaya a **Editar > configuración del proyecto > Reproductor**.
* En el **Inspector** panel, busque y seleccione el color verde **Windows Store** icono.
* Expanda **otras configuraciones**.
* En el **representación** sección, compruebe el **admite la realidad Virtual** opción.
* Compruebe que **Windows Holographic** aparece en la lista de **SDK de realidad Virtual**. Si no, seleccione el **+** situado en la parte inferior de la lista y elija **Windows Holographic**.
* Expanda **configuración de publicación**.
* En el **capacidades** sección, compruebe la configuración siguiente:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Micrófono
    * SpatialPerception
* Vaya a **Editar > configuración del proyecto > calidad**
* En el **Inspector** panel, bajo el icono de Windows Store, seleccione la flecha de lista desplegable negra en la fila "Default" y cambie la configuración predeterminada para **Fastest**.
* Vaya a **activos > Importar paquete > paquete personalizado**.
* Navegue hasta la **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** carpeta.
* Haga clic en **Planetarium.unitypackage**.
* Haga clic en **Abrir**.
* Un **Importar paquete de Unity** debe aparecer la ventana, haga clic en el **importación** botón.
* Espere a que Unity importar todos los recursos que necesitamos para completar este proyecto.
* En el **jerarquía** panel, elimine el **cámara principal**.
* En el **proyecto** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** carpeta, busque la **cámara principal** objeto.
* Arrastre y coloque el **cámara principal** prefabricado en el **jerarquía** panel.
* En el **jerarquía** panel, elimine el **luz direccional** objeto.
* En el **proyecto** panel, **hologramas** carpeta, busque la **Cursor** objeto.
* Arrastrar y colocar la **Cursor** prefabricado en el **jerarquía**.
* En el **jerarquía** panel, seleccione el **Cursor** objeto.
* En el **Inspector** del panel, haga clic en el **capa** hacia abajo y seleccione **capas editar...** .
* Nombre **usuario capa 31** como "**SpatialMapping**".
* Guarde la nueva escena: **Archivo > Guardar escena como...**
* Haga clic en **nueva carpeta** y el nombre de la carpeta **escenas**.
* Nombre del archivo "**planetario y disfrutará**" y guárdela en el **escenas** carpeta.

## <a name="chapter-1---scanning"></a>Capítulo 1: examen

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Objetivos**
* Obtenga información sobre la SurfaceObserver y cómo su impacto de la configuración de la experiencia y el rendimiento.
* Crear un salón de experiencia para recopilar las mallas de su sala de análisis.

**Instrucciones**
* En el **proyecto** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** carpeta, busque la **SpatialMapping** prefabricado.
* Arrastrar y colocar la **SpatialMapping** prefabricado en el **jerarquía** panel.

**Compilar e implementar (parte 1)**
* En Unity, seleccione **archivo > configuración de compilación**.
* Haga clic en **agregar escenas abierto** para agregar la **planetario y disfrutará** escena a la compilación.
* Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.
* Establecer **SDK** a **10 Universal** y **tipo de compilación UWP** a **D3D**.
* Comprobar **Unity C# proyectos**.
* Haz clic en **Compilación**.
* Crear un **nueva carpeta** denominada "Aplicación".
* Solo haga clic en el **aplicación** carpeta.
* Presione el **Seleccionar carpeta** botón.
* Cuando se hace Unity compilar, aparecerá una ventana del explorador de archivos.
* Haga doble clic en el **aplicación** carpeta para abrirla.
* Haga doble clic en **Planetarium.sln** para cargar el proyecto en Visual Studio.
* En Visual Studio, utilice la barra de herramientas superior para cambiar la configuración a **versión**.
* Cambiar la plataforma a **x86**.
* Haga clic en la flecha desplegable a la derecha de la «Máquina Local» y seleccione **máquina remota**.
* Escriba [dirección IP de su dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) en la dirección de campo y cambiar el modo de autenticación a **Universal (protocolo sin cifrar)**.
* Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
* Inspección del **salida** panel en Visual Studio para la compilación y el estado de la implementación.
* Una vez que se ha implementado la aplicación, caminar alrededor de la sala. Verá las superficies que lo rodea cubiertas por las mallas de tramas de alambres en blanco y negro.
* Analizar respecto a su entorno. No olvide mirar paredes, los límites máximos y los pisos.

**Compilar e implementar (parte 2)**

Ahora veamos cómo puede afectar la asignación espacial al rendimiento.
* En Unity, seleccione **Ventana > Profiler**.
* Haga clic en **agregar Profiler > GPU**.
* Haga clic en **Profiler Active > <Enter IP>** .
* Escriba el **dirección IP** de su HoloLens.
* Haga clic en **Conectar**.
* Observe el número de milisegundos que tarda la GPU representar un fotograma.
* Detener la aplicación se ejecute en el dispositivo.
* Vuelva a Visual Studio y abra **SpatialMappingObserver.cs**. La encontrará en la carpeta HoloToolkit\SpatialMapping del proyecto de ensamblado-CSharp (Windows Universal).
* Buscar el **Awake()** funcione y agregue la siguiente línea de código: **TrianglesPerCubicMeter = 1200;**
* Volver a implementar el proyecto en el dispositivo y, a continuación, **volver a conectar el generador de perfiles**. Observe el cambio en el número de milisegundos para representar un fotograma.
* Detener la aplicación se ejecute en el dispositivo.

**Guardar y cargar en Unity**

Por último, vamos a guardar la malla de la sala y cargarlos en Unity.
* Vuelva a Visual Studio y quitar el **TrianglesPerCubicMeter** línea que agregó en el **Awake()** función durante la sección anterior.
* Volver a implementar el proyecto en el dispositivo. Nos debemos estar ejecutando con **500** triángulos por medidor cúbica.
* Abra un explorador y escriba en su HoloLens IPAddress para navegar hasta el **Windows Device Portal**.
* Seleccione el **vista 3D** opción en el panel izquierdo.
* En **reconstrucción de superficie** seleccione la **actualización** botón.
* Vea en las áreas que se han analizado en su HoloLens aparecen en la ventana de presentación.
* Para guardar el examen de la sala, presione el **guardar** botón.
* Abra su **descargas** carpeta para encontrar el modelo guardado sala **SRMesh.obj**.
* Copia **SRMesh.obj** a la **activos** carpeta del proyecto de Unity.
* En Unity, seleccione el **SpatialMapping** objeto en el **jerarquía** panel.
* Busque el **objeto observador de superficie (Script)** componente.
* Haga clic en el círculo situado a la derecha de la **sala modelo** propiedad.
* Busque y seleccione el **SRMesh** objeto y, a continuación, cierre la ventana.
* Compruebe que la **sala modelo** propiedad en el **Inspector** panel ahora está configurado para **SRMesh**.
* Presione el **reproducir** botón Entrar en modo de vista previa de Unity.
* El componente SpatialMapping cargará las mallas del modelo guardado espacio para que pueda usar en Unity.
* Cambie a **escena** vista para ver todo el modelo de sala muestra con el sombreador de tramas de alambres.
* Presione el **reproducir** botón nuevo para salir del modo de vista previa.

**NOTA:** La próxima vez que especifique el modo de vista previa en Unity, cargará la malla de la sala guardado de forma predeterminada.

## <a name="chapter-2---visualization"></a>Capítulo 2: visualización

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Objetivos**
* Obtenga información sobre los conceptos básicos de los sombreadores.
* Visualizar respecto a su entorno.

**Instrucciones**
* En Unity **jerarquía** panel, seleccione el **SpatialMapping** objeto.
* En el **Inspector** panel, busque el **espacial Administrador de asignación (Script)** componente.
* Haga clic en el círculo situado a la derecha de la **superficie Material** propiedad.
* Busque y seleccione el **BlueLinesOnWalls** material y cerrar la ventana.
* En el **proyecto** panel **sombreadores** carpeta, haga doble clic en **BlueLinesOnWalls** para abrir el sombreador en Visual Studio.
* Se trata de un píxel simple (vértice fragmentar) sombreador, que lleva a cabo las siguientes tareas:
    1. Convierte la ubicación de un vértice en espacio global.
    2. Comprueba que el vértice 's normal para determinar si un píxel es vertical.
    3. Establece el color del píxel para la representación.

**Compilación e implementación**
* Volver a Unity y presione **reproducir** entrar en modo de vista previa.
* Las líneas azules se representará en todas las superficies verticales de la malla de espacio (que se cargan automáticamente desde nuestros datos guardados de análisis).
* Cambie a la **escena** tab para ajustar la vista de la sala de reuniones y vea cómo aparece la malla en toda la sala de Unity.
* En el **proyecto** panel, busque el **materiales** carpeta y seleccione el **BlueLinesOnWalls** material.
* Modificar algunas propiedades y ver cómo aparecen los cambios en el editor de Unity.
    * En el **Inspector** del panel, ajustar el **LineScale** valor para que las líneas aparezcan más gruesa o más estrecha.
    * En el **Inspector** del panel, ajustar el **LinesPerMeter** valor para cambiar el número de líneas que aparecen en cada muro.
* Haga clic en **reproducir** nuevo para salir del modo de vista previa.
* Compilar e implementar a la HoloLens y observe cómo aparece el sombreador de representación en superficies real.

Unity hace un gran trabajo de vista previa de materiales, pero siempre es una buena idea a la representación de desprotección en el dispositivo.

## <a name="chapter-3---processing"></a>Capítulo 3: procesar

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Objetivos**
* Aprenda técnicas para procesar los datos de asignación espacial para su uso en la aplicación.
* Analizar los datos de asignación espacial para buscar planes y quitar triángulos.
* Utilice planos para selección de ubicación holograma.

**Instrucciones**
* En Unity **proyecto** panel, **hologramas** carpeta, busque la **SpatialProcessing** objeto.
* Arrastrar y colocar la **SpatialProcessing** objeto en el **jerarquía** panel.

El recurso prefabricado SpatialProcessing incluye componentes para procesar los datos de asignación espacial. **SurfaceMeshesToPlanes.cs** encontrará y generar planes según los datos de asignación espacial. Usaremos planos en nuestra aplicación para representar las paredes, pisos y los límites máximos. También incluye este recurso prefabricado **RemoveSurfaceVertices.cs** que puede quitar los vértices de la malla de asignación espacial. Esto puede usarse para crear agujeros en la malla, o para quitar un exceso triángulos que ya no son necesarios (porque los planos pueden usarse en su lugar).
* En Unity **proyecto** panel, **hologramas** carpeta, busque la **SpaceCollection** objeto.
* Arrastre y coloque el **SpaceCollection** objeto en el **jerarquía** panel.
* En el **jerarquía** panel, seleccione el **SpatialProcessing** objeto.
* En el **Inspector** panel, busque el **reproducir el Administrador de espacio (Script)** componente.
* Haga doble clic en **PlaySpaceManager.cs** para abrirlo en Visual Studio.

PlaySpaceManager.cs contiene código específico de la aplicación. Se agregará funcionalidad a esta secuencia de comandos para habilitar el comportamiento siguiente:
1. Detener la recopilación de datos de asignación espacial después de que se supere el límite de tiempo de análisis (10 segundos).
2. Procesar los datos de asignación espacial:
    1. Use SurfaceMeshesToPlanes para crear una representación más sencilla del mundo como planos (paredes, pisos, los límites máximos, etcetera).
    2. Use RemoveSurfaceVertices para quitar los triángulos superficies que se encuentran dentro de los límites del plano.
3. Generar una colección de hologramas en el mundo y colocarlos en planos de piso y la pared cerca del usuario.

Completar los ejercicios de codificación marcados en PlaySpaceManager.cs o reemplazar la secuencia de comandos con la solución completa de los siguientes:

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
* Antes de implementar en el HoloLens, presione el **reproducir** botón en Unity para entrar en modo de reproducción.
* Después de la malla de la sala se carga desde el archivo, espere 10 segundos antes de que comience el procesamiento en la malla de asignación espacial.
* Cuando se completa el procesamiento, planos aparecerá representar el suelo, paredes, ceiling, etcetera.
* Después de todo de los aviones se han encontrado, debería ver un sistema solar aparecen en una tabla de piso cerca de la cámara.
* Dos pósteres demasiado deben aparecer en las paredes cerca de la cámara. Cambie a la **escena** pestaña si no puede verlas en **juego** modo.
* Presione el **reproducir** botón nuevo para salir del modo de juego.
* Compilar e implementar en el HoloLens, como de costumbre.
* Espere a análisis y procesamiento de los datos de asignación espacial en completarse.
* Una vez que vea aviones, intenta encontrar el sistema solar y pósters en el mundo.

## <a name="chapter-4---placement"></a>Capítulo 4: selección de ubicación

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Objetivos**
* Determinar si un holograma caben en una superficie.
* Proporcionar comentarios al usuario cuando un holograma puede o no cabe en una superficie.

**Instrucciones**
* En Unity **jerarquía** panel, seleccione el **SpatialProcessing** objeto.
* En el **Inspector** panel, busque el **mallas de superficie para aviones (Script)** componente.
* Cambiar el **dibujar planos** propiedad **nada** para borrar la selección.
* Cambiar el **dibujar planos** propiedad **pared**, de modo que solo los planos de pared se representará.
* En el **proyecto** panel, **Scripts** carpeta, haga doble clic en **Placeable.cs** para abrirlo en Visual Studio.

El **Placeable** script ya está conectado con el cuadro de proyección y pósteres de los que se crean una vez finalizada la búsqueda de plano. Todo lo que necesitamos hacer es eliminar los comentarios algo de código, y esta secuencia de comandos, logrará lo siguiente:
1. Determinar si un holograma caben en una superficie de detalles de las cuatro esquinas del cubo delimitador y el centro.
2. Comprobar para determinar si es lo suficientemente suave para el holograma vaciado estuvieron en normal de la superficie.
3. Representar el holograma para mostrar su tamaño real mientras se coloca un cubo de delimitador.
4. Convertir una sombra el holograma para mostrar dónde se colocarán en el muro de piso en/subyacente.
5. Representar la sombra en rojo si el holograma no se puede colocar en la superficie o verde, si es posible.
6. Vuelva a orientar el holograma para alinearse con el tipo de superficie (horizontal o vertical) que tiene afinidad con.
7. Coloca sin problemas el holograma en la superficie seleccionada para evitar saltar o comportamiento de ajuste.

Quite todo el código en el ejercicio de codificación a continuación o usar esta solución completa en **Placeable.cs**:

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
    /// The aligntoVerticalSurface parameter is ignored if the object
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
* Como antes, compile el proyecto e implemente en el HoloLens.
* Espere a análisis y procesamiento de los datos de asignación espacial en completarse.
* Cuando ve el sistema solar, mire debajo de la casilla de proyección y realizar un gesto de select para moverse por. Mientras está seleccionado el cuadro de proyección, un cubo delimitador estará visible alrededor del cuadro de proyección.
* Mover head para que mirar en una ubicación diferente en la sala. El cuadro de proyección debe seguir a su mirada. Cuando la sombra debajo del cuadro de proyección en color roja, no se puede colocar el holograma en que se muestran. Cuando se vuelve verde la sombra debajo del cuadro de proyección, puede colocar el holograma realizando gesto seleccione otro.
* Busque y seleccione uno de los pósteres holográficas en una pared para moverlo a una nueva ubicación. Tenga en cuenta que no se puede colocar el póster en el suelo, ceiling, y que se mantiene correctamente orientado hacia cada pared al desplazarse por.

## <a name="chapter-5---occlusion"></a>Capítulo 5: oclusión

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Objetivos**
* Determinar si un holograma se ocluyeron en la malla de asignación espacial.
* Aplicar técnicas de oclusión diferentes para lograr un divertido efecto.

**Instrucciones**

En primer lugar, vamos a permitir la malla de asignación espacial a occlude otros hologramas sin occluding del mundo real:
* En el **jerarquía** panel, seleccione el **SpatialProcessing** objeto.
* En el **Inspector** panel, busque el **reproducir el Administrador de espacio (Script)** componente.
* Haga clic en el círculo situado a la derecha de la **Material secundario** propiedad.
* Busque y seleccione el **oclusión** material y cerrar la ventana.

A continuación, vamos a agregar un comportamiento especial a la tierra, para que tenga un resaltado azul cada vez que se pasa a ser ocluido holograma otro (por ejemplo, el sol), o bien la malla de asignación espacial:
* En el **proyecto** panel el **hologramas** carpeta, expanda la **SolarSystem** objeto.
* Haga clic en **tierra**.
* En el **Inspector** del panel, encontrará abundante material de la tierra (componente de la parte inferior).
* En el **sombreador desplegable**, cambie el sombreador **personalizado > OcclusionRim**. Esto representará un resaltado azul alrededor de la tierra cada vez que se ocluyeron en otro objeto.

Por último, vamos a habilitar un efecto de la visión de rayos x para planetas en nuestro sistema solar. Tendremos que editar **PlanetOcclusion.cs** (que se encuentra en la carpeta Scripts\SolarSystem) con el fin de lograr lo siguiente:
1. Determinar si un planeta se ocluyeron en la capa SpatialMapping (sala mallas y planos).
2. Mostrar la representación de tramas de alambres de un mundo cada vez que se ocluyeron en la capa SpatialMapping.
3. Ocultar la representación de tramas de alambres de un planeta cuando no está bloqueado por la capa de SpatialMapping.

Siga el ejercicio de codificación de PlanetOcclusion.cs, o utilice la siguiente solución:

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
* Compile e implemente la aplicación a HoloLens, como de costumbre.
* Espere de análisis y procesamiento de los datos de asignación espacial que se complete (debería ver las líneas azules aparecen en las paredes).
* Buscar y seleccione el cuadro de proyección solar del sistema y, a continuación, establezca el cuadro situado junto a una pared o detrás de un contador.
* Puede ver la oclusión básica ocultándose tras las superficies del mismo nivel en el cuadro de póster o proyección.
* Busque la tierra, debe haber un efecto de resaltado en azul cada vez que va detrás de otro holograma o la superficie.
* Ver cómo mover los planetas detrás de la pared o en otras superficies en la sala. ¡Ahora tiene la visión de rayos x y puede ver sus esqueletos de tramas de alambres!

## <a name="the-end"></a>Fin

¡Enhorabuena! Ahora ha completado **MR espacial 230: Asignación espacial**.
* Saber cómo analizar los datos de carga y el entorno de asignación espacial a Unity.
* Comprender los conceptos básicos de los sombreadores y cómo se pueden usar los materiales para volver a visualizar el mundo.
* Ha aprendido de nuevas técnicas de procesamiento para buscar los planos y quitarlo una malla de triángulos.
* Podía mover y colocar hologramas en superficies que tenía sentido.
* ¡Ha experimentado técnicas diferentes oclusión y aprovecha la potencia de la visión de rayos x!
