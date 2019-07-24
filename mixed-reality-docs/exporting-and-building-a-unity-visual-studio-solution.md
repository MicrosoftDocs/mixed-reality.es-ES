---
title: Exportar y compilar una solución de Visual Studio para Unity
description: En este artículo se describe la exportación de un proyecto de realidad mixta desde Unity para que pueda compilar e implementar en Visual Studio.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Visual Studio, exportar, compilar e implementar
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525836"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportar y compilar una solución de Visual Studio para Unity

Si no tiene previsto usar el teclado del sistema en su aplicación, nuestra recomendación es usar *D3D* , ya que la aplicación usará un poco menos de memoria y tendrá un tiempo de inicio ligeramente más rápido. Si usa la API de TouchScreenKeyboard en el proyecto para usar el teclado del sistema, debe exportarlo como *XAML*.

## <a name="how-to-export-from-unity"></a>Cómo exportar desde Unity

![Configuración de compilación de Unity](images/unitybuildsettings-300px.png)<br>
*Configuración de compilación de Unity*

1. Cuando esté listo para exportar el proyecto desde Unity, abra el menú **archivo** y seleccione **configuración de compilación..** .
2. Haga clic en **Agregar escenas abiertas** para agregar la escena a la compilación.
3. En el cuadro de diálogo **configuración de compilación** , elija las opciones siguientes para la exportación de HoloLens:
   * **Plataforma** *Plataforma universal de Windows* y asegúrese de seleccionar **cambiar plataforma** para que la selección surta efecto.
   * **SKD** *Universal 10*.
   * **Tipo de compilación de UWP:** *D3D*.
4. **Opcional**: **Proyectos C# de Unity:** Incorpora.

>[!NOTE]
>La activación de esta casilla le permite:
>* Depure la aplicación en el depurador remoto de Visual Studio.
>* Edite los scripts C# del proyecto de Unity mientras usa IntelliSense para las API de WinRT.

5. En la ventana **configuración de compilación...** , Abra **configuración del reproductor...**
6. Seleccione la **configuración de plataforma universal de Windows** pestaña.
7. Expanda el grupo de **configuración de XR** .
8. En la **sección configuración de XR** , active la casilla compatibilidad con **realidad virtual** para agregar una nueva lista de dispositivos de **realidad virtual** y confirme que **"Windows Mixed Reality"** aparece como un dispositivo compatible.
9. Vuelva al cuadro de diálogo **configuración de compilación** .
10. Seleccione compilar.
11. En el cuadro de diálogo del explorador de Windows que aparece, cree una nueva carpeta para almacenar la salida de la compilación de Unity. Por lo general, el nombre de la carpeta es "app".
12. Seleccione la carpeta que acaba de crear y haga clic en **Seleccionar carpeta**.
13. Una vez que Unity termine de crearse, se abrirá una ventana del explorador de Windows en el directorio raíz del proyecto. Navegue a la carpeta recién creada.
14. Abra el archivo de solución de Visual Studio generado que se encuentra dentro de esta carpeta.

## <a name="when-to-re-export-from-unity"></a>Cuándo volver a exportar desde Unity

Al activar laC# casilla "proyectos" al exportar la aplicación desde Unity, se crea una solución de Visual Studio que incluye todos los archivos de script de Unity. Esto le permite iterar en los scripts sin volver a exportar desde Unity. Sin embargo, si desea realizar cambios en el proyecto que no solo cambian el contenido de los scripts, deberá volver a exportar desde Unity. A continuación se indican algunos ejemplos de veces que es necesario volver a exportar desde Unity:
* Los recursos se agregan o quitan en la pestaña proyecto.
* Puede cambiar cualquier valor en la pestaña inspector.
* Los objetos se agregan o se quitan de la pestaña jerarquía.
* Puede cambiar cualquier configuración de proyecto de Unity.

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Compilar e implementar una solución de Visual Studio para Unity

El resto de compilar e implementar aplicaciones tiene lugar en [Visual Studio](using-visual-studio.md). Tendrá que especificar una configuración de compilación de Unity. Las convenciones de nomenclatura de Unity pueden diferir de lo que se suele usar en Visual Studio:

|  Configuración  |  Explicación | 
|----------|----------|
|  Depuración  |  Todas las optimizaciones están desactivadas y el generador de perfiles está habilitado. Se usa para depurar scripts. | 
|  Maestro  |  Todas las optimizaciones están activadas y el generador de perfiles está deshabilitado. Se usa para enviar aplicaciones a la tienda. | 
|  Release  |  Todas las optimizaciones están activadas y el generador de perfiles está habilitado. Se usa para evaluar el rendimiento de la aplicación. | 

Tenga en cuenta que la lista anterior es un subconjunto de los desencadenadores comunes que harán que se genere el proyecto de Visual Studio. En general, la edición de archivos. CS desde Visual Studio no requerirá que se vuelva a generar el proyecto desde Unity.

## <a name="troubleshooting"></a>Solución de problemas

Si observa que las modificaciones en los archivos. CS no se reconocen en el proyecto de Visual Studio, asegúrese de que la opción C# "proyectos de Unity" está activada cuando se genera el proyecto de vs desde el menú compilar de Unity.
