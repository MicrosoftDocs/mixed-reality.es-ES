---
title: Documentación de Empaquetador de datos espaciales de realidad mixta
description: Documentación para usar Mixed Reality Empaquetador de datos espaciales
author: alfred-msft
ms.author: alreynol
ms.date: 05/16/2019
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 7ad1159af9eecd3ca3622dd25cc1f49fb0b1700a
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942111"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="d22fb-104">Documentación de Empaquetador de datos espaciales de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="d22fb-104">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="d22fb-105">Esta herramienta y su funcionamiento se ofrecen como-es.</span><span class="sxs-lookup"><span data-stu-id="d22fb-105">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="d22fb-106">Se está sujeta a cambios sin aviso y pueden no ser compatible con futuras Windows o Windows Mixed Reality HMD libera.</span><span class="sxs-lookup"><span data-stu-id="d22fb-106">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span>

## <a name="download"></a><span data-ttu-id="d22fb-107">Descargar</span><span class="sxs-lookup"><span data-stu-id="d22fb-107">Download</span></span>
 <span data-ttu-id="d22fb-108">Descargar [MixedRealitySpatialDataPackager aquí](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="d22fb-108">Download [MixedRealitySpatialDataPackager here](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="quickstart"></a><span data-ttu-id="d22fb-109">Guía de inicio rápido</span><span class="sxs-lookup"><span data-stu-id="d22fb-109">Quickstart</span></span>

<span data-ttu-id="d22fb-110">La herramienta Mixed Reality Empaquetador de datos espaciales copia los datos espaciales de una aplicación de destino de un PC a otro a través de un paso dos exportación e importación de proceso.</span><span class="sxs-lookup"><span data-stu-id="d22fb-110">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="d22fb-111">La herramienta debe ejecutarse con privilegios de administrador y elimina los datos espaciales existentes en la importación.</span><span class="sxs-lookup"><span data-stu-id="d22fb-111">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="d22fb-112">Exportación no altera los datos espaciales existentes.</span><span class="sxs-lookup"><span data-stu-id="d22fb-112">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="d22fb-113">Limitaciones y requisitos clave:</span><span class="sxs-lookup"><span data-stu-id="d22fb-113">Key requirements and limitations:</span></span>

1. <span data-ttu-id="d22fb-114">Se debe ejecutar la herramienta con privilegios de administrador</span><span class="sxs-lookup"><span data-stu-id="d22fb-114">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="d22fb-115">Es posible que deba reiniciar PC si el Portal de realidad mixta es inestable después de ejecutar la herramienta</span><span class="sxs-lookup"><span data-stu-id="d22fb-115">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="d22fb-116">No se ejecutará la herramienta al encontrar errores de coincidencia de versión de los datos espaciales o incompatibilidades</span><span class="sxs-lookup"><span data-stu-id="d22fb-116">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="d22fb-117">Herramienta, borrará los datos espaciales existentes en la importación</span><span class="sxs-lookup"><span data-stu-id="d22fb-117">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="d22fb-118">Si el proceso de importación se produce un error anterior no se puede restaurar datos a menos que se ha hecho backup exportando previamente</span><span class="sxs-lookup"><span data-stu-id="d22fb-118">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="d22fb-119">Calidad de la funcionalidad de importación contingente en modo "Solo lectura" para los datos espaciales del mapa</span><span class="sxs-lookup"><span data-stu-id="d22fb-119">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="d22fb-120">Asignación de procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="d22fb-120">Mapping Best Practices</span></span>

1. <span data-ttu-id="d22fb-121">Borrar asignaciones existentes desde el Panel de Control (configuración -> Mixed Reality -> entorno -> entorno borrar datos)</span><span class="sxs-lookup"><span data-stu-id="d22fb-121">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="d22fb-122">Asegúrese de iluminación suficiente para seguimiento buena y si ejecuta el modo Mapa bloqueado intenta mantener la misma iluminación</span><span class="sxs-lookup"><span data-stu-id="d22fb-122">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="d22fb-123">Cuando sea posible mantener el intervalo dinámico de iluminación baja, ya que evita las áreas de iluminación alta junto a áreas con sombra oscuras</span><span class="sxs-lookup"><span data-stu-id="d22fb-123">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="d22fb-124">Minimizar en blanco, superficies textureless, por ejemplo, colocan una gama de diferentes Pósteres paredes blancas</span><span class="sxs-lookup"><span data-stu-id="d22fb-124">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="d22fb-125">Asignar el espacio sin objetos dinámicos en la escena, como mover usuarios</span><span class="sxs-lookup"><span data-stu-id="d22fb-125">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="d22fb-126">Bloquear el mapa en la importación (disponible a través de Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="d22fb-126">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="d22fb-127">Desbloquear la asignación y volver a examinar el entorno cuando se degrada el seguimiento de la calidad y hay cambios en el entorno (iluminación o cambios en el diseño de objeto)</span><span class="sxs-lookup"><span data-stu-id="d22fb-127">Unlock the map and rescan the enviornment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="d22fb-128">Empaquetador de datos espaciales de realidad mixta ejecución con el Script complementario</span><span class="sxs-lookup"><span data-stu-id="d22fb-128">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="d22fb-129">Hemos proporcionado MRSpatialPackagerHelperScript.ps1 que se ejecuta al Empaquetador de mapa de las herramientas.</span><span class="sxs-lookup"><span data-stu-id="d22fb-129">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="d22fb-130">Los parámetros del script se definen a continuación:</span><span class="sxs-lookup"><span data-stu-id="d22fb-130">The script parameters are defined below:</span></span>

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
    This functionality requires an updated driver from Insider Preview Builds with the Map Locking feature

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="d22fb-131">Salida y el uso de ejemplo de Script de Powershell</span><span class="sxs-lookup"><span data-stu-id="d22fb-131">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="d22fb-132">.\MRSpatialPackagerHelperScript.ps1 - AppName holoshell - nombre de usuario administrador-modo de exportación - MapxPath D:\temp\ LockMap - 0</span><span class="sxs-lookup"><span data-stu-id="d22fb-132">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value succesfully set to 0

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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a><span data-ttu-id="d22fb-133">Cómo exportar mediante MixedRealityPackager.exe</span><span class="sxs-lookup"><span data-stu-id="d22fb-133">How to Export using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="d22fb-134">Exportar mapas de dispositivo genera dos archivos: mapx het.mapx y sa.mapx.</span><span class="sxs-lookup"><span data-stu-id="d22fb-134">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="d22fb-135">Durante el proceso de exportación se quitan todos los delimitadores espaciales excepto para la aplicación especificada y los límites creados por el usuario (si existe).</span><span class="sxs-lookup"><span data-stu-id="d22fb-135">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="d22fb-136">El nombre de familia del paquete de origen debe coincidir con una aplicación existente instalada o se producirá un error en el archivo exe.</span><span class="sxs-lookup"><span data-stu-id="d22fb-136">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealitypackagerexe"></a><span data-ttu-id="d22fb-137">Cómo importar mediante MixedRealityPackager.exe</span><span class="sxs-lookup"><span data-stu-id="d22fb-137">How to Import using MixedRealityPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="d22fb-138">Importación elimina los datos espaciales existentes y lo reemplaza con los datos del directorio especificado.</span><span class="sxs-lookup"><span data-stu-id="d22fb-138">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="d22fb-139">La entrada de nombre de la aplicación especifica el nombre del paquete de la aplicación de destino que al igual que los anclajes espaciales se debe importar para y el SID del usuario de destino Especifica el usuario que debe tener acceso a los delimitadores espaciales importados.</span><span class="sxs-lookup"><span data-stu-id="d22fb-139">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="d22fb-140">El nombre de familia de paquete de destino y el SID de usuario deben coincidir con los valores existentes en el equipo o se producirá un error en el archivo exe.</span><span class="sxs-lookup"><span data-stu-id="d22fb-140">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="d22fb-141">Mensajes de error</span><span class="sxs-lookup"><span data-stu-id="d22fb-141">Error Messages</span></span>
<span data-ttu-id="d22fb-142">Además los mensajes de error por debajo de los errores también irá acompañados de un valor HRESULT</span><span class="sxs-lookup"><span data-stu-id="d22fb-142">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="d22fb-143">Si se produjo un error de argumentos no válidos</span><span class="sxs-lookup"><span data-stu-id="d22fb-143">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="d22fb-144">Si el archivo ejecutable no se ejecutó en modo de administrador</span><span class="sxs-lookup"><span data-stu-id="d22fb-144">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="d22fb-145">Si se produjo un error al habilitar o deshabilitar el controlador</span><span class="sxs-lookup"><span data-stu-id="d22fb-145">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="d22fb-146">Si se ha producido un error al validar la versión de la base de datos espaciales</span><span class="sxs-lookup"><span data-stu-id="d22fb-146">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="d22fb-147">Si se ha producido un error al validar el nombre de familia de paquete proporcionado para la aplicación de importación y exportación de destino</span><span class="sxs-lookup"><span data-stu-id="d22fb-147">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="d22fb-148">Si se ha producido un error al validar el SID del usuario</span><span class="sxs-lookup"><span data-stu-id="d22fb-148">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="d22fb-149">Si se ha producido un error en el destino o el origen de datos espaciales archivos relacionados</span><span class="sxs-lookup"><span data-stu-id="d22fb-149">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a><span data-ttu-id="d22fb-150">Si se produjo un error relacionado con iniciar y detener el espectro/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="d22fb-150">If there was an error related to starting and stoping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
