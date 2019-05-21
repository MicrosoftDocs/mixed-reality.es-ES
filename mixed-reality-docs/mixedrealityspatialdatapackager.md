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
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Documentación de Empaquetador de datos espaciales de realidad mixta

>[!NOTE]
> Esta herramienta y su funcionamiento se ofrecen como-es. Se está sujeta a cambios sin aviso y pueden no ser compatible con futuras Windows o Windows Mixed Reality HMD libera.

## <a name="download"></a>Descargar
 Descargar [MixedRealitySpatialDataPackager aquí](http://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="quickstart"></a>Guía de inicio rápido

La herramienta Mixed Reality Empaquetador de datos espaciales copia los datos espaciales de una aplicación de destino de un PC a otro a través de un paso dos exportación e importación de proceso. La herramienta debe ejecutarse con privilegios de administrador y elimina los datos espaciales existentes en la importación. Exportación no altera los datos espaciales existentes.

Limitaciones y requisitos clave:

1. Se debe ejecutar la herramienta con privilegios de administrador 
2. Es posible que deba reiniciar PC si el Portal de realidad mixta es inestable después de ejecutar la herramienta
3. No se ejecutará la herramienta al encontrar errores de coincidencia de versión de los datos espaciales o incompatibilidades
4. Herramienta, borrará los datos espaciales existentes en la importación
5. Si el proceso de importación se produce un error anterior no se puede restaurar datos a menos que se ha hecho backup exportando previamente
6. Calidad de la funcionalidad de importación contingente en modo "Solo lectura" para los datos espaciales del mapa
***

## <a name="mapping-best-practices"></a>Asignación de procedimientos recomendados

1. Borrar asignaciones existentes desde el Panel de Control (configuración -> Mixed Reality -> entorno -> entorno borrar datos)
2. Asegúrese de iluminación suficiente para seguimiento buena y si ejecuta el modo Mapa bloqueado intenta mantener la misma iluminación
3. Cuando sea posible mantener el intervalo dinámico de iluminación baja, ya que evita las áreas de iluminación alta junto a áreas con sombra oscuras
4. Minimizar en blanco, superficies textureless, por ejemplo, colocan una gama de diferentes Pósteres paredes blancas
5. Asignar el espacio sin objetos dinámicos en la escena, como mover usuarios
6. Bloquear el mapa en la importación (disponible a través de Insider Preview)
7. Desbloquear la asignación y volver a examinar el entorno cuando se degrada el seguimiento de la calidad y hay cambios en el entorno (iluminación o cambios en el diseño de objeto)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Empaquetador de datos espaciales de realidad mixta ejecución con el Script complementario

Hemos proporcionado MRSpatialPackagerHelperScript.ps1 que se ejecuta al Empaquetador de mapa de las herramientas. 


Los parámetros del script se definen a continuación:

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

### <a name="powershell-script-example-usage-and-output"></a>Salida y el uso de ejemplo de Script de Powershell

.\MRSpatialPackagerHelperScript.ps1 - AppName holoshell - nombre de usuario administrador-modo de exportación - MapxPath D:\temp\ LockMap - 0
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

### <a name="how-to-export-using-mixedrealitypackagerexe"></a>Cómo exportar mediante MixedRealityPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

Exportar mapas de dispositivo genera dos archivos: mapx het.mapx y sa.mapx. Durante el proceso de exportación se quitan todos los delimitadores espaciales excepto para la aplicación especificada y los límites creados por el usuario (si existe). El nombre de familia del paquete de origen debe coincidir con una aplicación existente instalada o se producirá un error en el archivo exe.

### <a name="how-to-import-using-mixedrealitypackagerexe"></a>Cómo importar mediante MixedRealityPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Importación elimina los datos espaciales existentes y lo reemplaza con los datos del directorio especificado. La entrada de nombre de la aplicación especifica el nombre del paquete de la aplicación de destino que al igual que los anclajes espaciales se debe importar para y el SID del usuario de destino Especifica el usuario que debe tener acceso a los delimitadores espaciales importados. El nombre de familia de paquete de destino y el SID de usuario deben coincidir con los valores existentes en el equipo o se producirá un error en el archivo exe.


***
## <a name="error-messages"></a>Mensajes de error
Además los mensajes de error por debajo de los errores también irá acompañados de un valor HRESULT

### <a name="if-there-was-an-error-invalid-arguments"></a>Si se produjo un error de argumentos no válidos
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Si el archivo ejecutable no se ejecutó en modo de administrador
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Si se produjo un error al habilitar o deshabilitar el controlador
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Si se ha producido un error al validar la versión de la base de datos espaciales
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Si se ha producido un error al validar el nombre de familia de paquete proporcionado para la aplicación de importación y exportación de destino
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Si se ha producido un error al validar el SID del usuario
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Si se ha producido un error en el destino o el origen de datos espaciales archivos relacionados
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stoping-spectrumsharedrealitysvc"></a>Si se produjo un error relacionado con iniciar y detener el espectro/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
