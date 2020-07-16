---
title: Documentación del Empaquetador de datos espaciales de realidad mixta
description: Documentación para usar el Empaquetador de datos espaciales de realidad mixta
author: alfred-msft
ms.author: yuripek
ms.date: 05/16/2019
ms.topic: article
keywords: LBE, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 4a285cbd7423d7cacaf52370e6e19acf42672289
ms.sourcegitcommit: cfca6cb016d8683fa2c611a97d493a4947935dbb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2020
ms.locfileid: "86402744"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="5abe8-104">Documentación del Empaquetador de datos espaciales de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5abe8-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="5abe8-105">Esta herramienta y su operación se ofrecen tal cual.</span><span class="sxs-lookup"><span data-stu-id="5abe8-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="5abe8-106">Está sujeto a cambios sin previo aviso y es posible que no sea compatible con las futuras versiones de HMD de Windows o Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5abe8-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="5abe8-107">Descargar</span><span class="sxs-lookup"><span data-stu-id="5abe8-107">Download</span></span>
 <span data-ttu-id="5abe8-108">Descargar [MixedRealitySpatialDataPackager aquí](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="5abe8-108">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="5abe8-109">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="5abe8-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5abe8-110"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="5abe8-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5abe8-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5abe8-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5abe8-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="5abe8-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="5abe8-113"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="5abe8-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5abe8-114">Empaquetador de datos espaciales de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="5abe8-114">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="5abe8-115">✔️</span><span class="sxs-lookup"><span data-stu-id="5abe8-115">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="5abe8-116">Inicio rápido</span><span class="sxs-lookup"><span data-stu-id="5abe8-116">Quickstart</span></span>

<span data-ttu-id="5abe8-117">La herramienta de empaquetado de datos espaciales de realidad mixta copia los datos espaciales de una aplicación de destino de un equipo a otro a través de un proceso de exportación e importación de dos pasos.</span><span class="sxs-lookup"><span data-stu-id="5abe8-117">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="5abe8-118">La herramienta debe ejecutarse con privilegios de administrador y elimina los datos espaciales existentes al importar.</span><span class="sxs-lookup"><span data-stu-id="5abe8-118">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="5abe8-119">La exportación deja intactos los datos espaciales existentes.</span><span class="sxs-lookup"><span data-stu-id="5abe8-119">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="5abe8-120">Requisitos y limitaciones clave:</span><span class="sxs-lookup"><span data-stu-id="5abe8-120">Key requirements and limitations:</span></span>

1. <span data-ttu-id="5abe8-121">La herramienta debe ejecutarse con privilegios de administrador</span><span class="sxs-lookup"><span data-stu-id="5abe8-121">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="5abe8-122">Es posible que tenga que reiniciar el equipo si el portal de realidad mixta es inestable después de ejecutar la herramienta</span><span class="sxs-lookup"><span data-stu-id="5abe8-122">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="5abe8-123">La herramienta no se ejecutará al encontrar incompatibilidades o incompatibilidades de la versión de datos espaciales</span><span class="sxs-lookup"><span data-stu-id="5abe8-123">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="5abe8-124">La herramienta borrará los datos espaciales existentes al importar</span><span class="sxs-lookup"><span data-stu-id="5abe8-124">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="5abe8-125">Si se produce un error en el proceso de importación, los datos anteriores no se pueden restaurar a menos que se haya realizado la copia de seguridad mediante la exportación anterior</span><span class="sxs-lookup"><span data-stu-id="5abe8-125">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="5abe8-126">Calidad de la funcionalidad de importación condicionada en el modo de "solo lectura" para los datos de mapa espacial</span><span class="sxs-lookup"><span data-stu-id="5abe8-126">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="5abe8-127">Procedimientos recomendados de asignación</span><span class="sxs-lookup"><span data-stu-id="5abe8-127">Mapping Best Practices</span></span>

1. <span data-ttu-id="5abe8-128">Borrar asignaciones existentes en el panel de control (configuración-> entorno mixto de realidad >-> borrar datos de entorno)</span><span class="sxs-lookup"><span data-stu-id="5abe8-128">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="5abe8-129">Asegúrese de que haya suficiente iluminación para un buen seguimiento y si la ejecución del modo de mapa bloqueado intente mantener la misma iluminación</span><span class="sxs-lookup"><span data-stu-id="5abe8-129">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="5abe8-130">Cuando sea posible, mantenga el intervalo dinámico de iluminación bajo evitando áreas de iluminación alta junto a áreas oscuras y sombreadas.</span><span class="sxs-lookup"><span data-stu-id="5abe8-130">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="5abe8-131">Minimizar las superficies en blanco y sin texturas, por ejemplo, colocar un intervalo de pósters distintos en las paredes blancas</span><span class="sxs-lookup"><span data-stu-id="5abe8-131">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="5abe8-132">Asignar el espacio sin objetos dinámicos en la escena, como mover personas</span><span class="sxs-lookup"><span data-stu-id="5abe8-132">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="5abe8-133">Bloquear el mapa al importar (disponible a través de Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="5abe8-133">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="5abe8-134">Desbloquee el mapa y vuelva a examinar el entorno cuando el seguimiento de la calidad sea degradado o haya cambios en el entorno (iluminación o cambios en el diseño de objetos)</span><span class="sxs-lookup"><span data-stu-id="5abe8-134">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="5abe8-135">Ejecución de un empaquetador de datos espaciales de realidad mixta con un script complementario</span><span class="sxs-lookup"><span data-stu-id="5abe8-135">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="5abe8-136">Hemos proporcionado MRSpatialPackagerHelperScript.ps1 que ejecutan las herramientas del Empaquetador de mapas.</span><span class="sxs-lookup"><span data-stu-id="5abe8-136">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="5abe8-137">Los parámetros de script se definen a continuación:</span><span class="sxs-lookup"><span data-stu-id="5abe8-137">The script parameters are defined below:</span></span>

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="5abe8-138">Ejemplo de script de PowerShell uso y salida</span><span class="sxs-lookup"><span data-stu-id="5abe8-138">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="5abe8-139">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-nombredeusuario administrador-Mode Export-MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="5abe8-139">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="5abe8-140">Cómo exportar con MixedRealitySpatialDataPackager.exe</span><span class="sxs-lookup"><span data-stu-id="5abe8-140">How to Export using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="5abe8-141">La exportación de mapas fuera del dispositivo genera dos archivos MAPX, Het. MAPX y SA. MAPX.</span><span class="sxs-lookup"><span data-stu-id="5abe8-141">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="5abe8-142">Durante el proceso de exportación, se quitan todos los delimitadores espaciales, a excepción de la aplicación especificada y el límite creado por el usuario (si existe).</span><span class="sxs-lookup"><span data-stu-id="5abe8-142">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="5abe8-143">El nombre de familia del paquete de origen debe coincidir con una aplicación instalada existente o se producirá un error en el archivo exe.</span><span class="sxs-lookup"><span data-stu-id="5abe8-143">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="5abe8-144">Cómo importar mediante MixedRealitySpatialDataPackager.exe</span><span class="sxs-lookup"><span data-stu-id="5abe8-144">How to Import using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="5abe8-145">La importación elimina los datos espaciales existentes y los reemplaza con los datos del directorio especificado.</span><span class="sxs-lookup"><span data-stu-id="5abe8-145">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="5abe8-146">La entrada del nombre de la aplicación especifica el nombre del paquete de la aplicación de destino que se debe importar para y el SID del usuario de destino especifica el usuario que debe tener acceso a los delimitadores espaciales importados.</span><span class="sxs-lookup"><span data-stu-id="5abe8-146">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="5abe8-147">El nombre de familia y los SID de usuario del paquete de destino deben coincidir con los valores existentes en el equipo o se producirá un error en el archivo exe.</span><span class="sxs-lookup"><span data-stu-id="5abe8-147">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="5abe8-148">mensajes de error</span><span class="sxs-lookup"><span data-stu-id="5abe8-148">Error Messages</span></span>
<span data-ttu-id="5abe8-149">Además, los mensajes de error siguientes también irán acompañados de un valor HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5abe8-149">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="5abe8-150">Si se produjo un error argumentos no válidos</span><span class="sxs-lookup"><span data-stu-id="5abe8-150">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="5abe8-151">Si el ejecutable no se ejecutó en modo de administrador</span><span class="sxs-lookup"><span data-stu-id="5abe8-151">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="5abe8-152">Si se produjo un error al habilitar o deshabilitar el controlador</span><span class="sxs-lookup"><span data-stu-id="5abe8-152">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="5abe8-153">Si se produjo un error al validar la versión de la base de datos espacial</span><span class="sxs-lookup"><span data-stu-id="5abe8-153">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="5abe8-154">Si se produjo un error al validar el nombre de familia del paquete proporcionado para la aplicación de importación y exportación de destino</span><span class="sxs-lookup"><span data-stu-id="5abe8-154">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="5abe8-155">Si se produjo un error al validar el SID del usuario</span><span class="sxs-lookup"><span data-stu-id="5abe8-155">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="5abe8-156">Si se produjo un error relacionado con los archivos de datos espaciales de origen o de destino</span><span class="sxs-lookup"><span data-stu-id="5abe8-156">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="5abe8-157">Si se produjo un error relacionado con el inicio y la detención del espectro/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="5abe8-157">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
