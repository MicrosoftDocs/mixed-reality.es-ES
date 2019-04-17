---
title: Exportar y creación de una solución de Visual Studio de Unity
description: Este artículo describe la exportación de su proyecto de realidad mixta de Unity para que pueda compilar e implementar en Visual Studio.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, visual studio, exportar, compilar, implementar
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605477"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportar y creación de una solución de Visual Studio de Unity

Si no tiene la intención de utilizar el teclado del sistema en la aplicación, nuestra recomendación es usar *D3D* como la aplicación usará un poco menos memoria y tienen un tiempo de inicio de un poco más rápido. Si utiliza la API TouchScreenKeyboard en el proyecto para usar el teclado del sistema, debe exportar como *XAML*.

## <a name="how-to-export-from-unity"></a>Cómo exportar desde Unity

![Configuración de compilación de Unity](images/unitybuildsettings-300px.png)<br>
*Configuración de compilación de Unity*

1. Cuando esté listo para exportar el proyecto de Unity, abra el **archivo** menú y seleccione **configuración de compilación...**
2. Haga clic en **agregar escenas abierto** para agregar la escena a la compilación.
3. En el **configuración de compilación** cuadro de diálogo, elija las opciones siguientes para exportar de HoloLens:
   * **Plataforma:** *Plataforma universal de Windows* y no olvide seleccionar **Cambiar plataforma** para su selección surta efecto.
   * **SDK:** *10 universal*.
   * **Tipo de compilación para UWP:** *D3D*.
4. **Opcional**: **Unity C# proyectos:** Activada.

>[!NOTE]
>Al activar esta casilla permite:
>* Depurar la aplicación en el depurador remoto de Visual Studio.
>* Edición de scripts en el Unity C# proyecto al usar IntelliSense para WinRT APIs.

5. Desde el **configuración de compilación...**  ventana abierta **configuración del Reproductor...**
6. Seleccione el **configuración de plataforma Universal de Windows** ficha.
7. Expanda el **configuración XR** grupo.
8. En el **XR configuración** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar un nuevo **dispositivos de realidad Virtual** lista y confirme **"de Windows mixto Realidad"** aparece como un dispositivo compatible.
9. Vuelva a la **configuración de compilación** cuadro de diálogo.
10. Seleccione **compilar**.
11. En el cuadro de diálogo de explorador de Windows que aparece, cree una nueva carpeta para incluir los resultados de compilación de Unity. Por lo general, usamos la carpeta "App".
12. Seleccione la carpeta recién creada y haga clic en **seleccionar la carpeta**.
13. Cuando Unity haya finalizado la compilación, se abrirá una ventana del explorador de Windows para el directorio raíz del proyecto. Vaya a la carpeta recién creada.
14. Abra el archivo de solución de Visual Studio generado ubicado dentro de esta carpeta.

## <a name="when-to-re-export-from-unity"></a>Cuándo se debe volver a exportar desde Unity

Comprobación de la "C# proyectos" casilla de verificación cuando al exportar la aplicación de Unity crea una solución de Visual Studio que incluye todos los archivos de script de Unity. Esto le permite realizar una iteración en las secuencias de comandos sin necesidad de volver a exportar desde Unity. Sin embargo, si desea realizar cambios en el proyecto que no están cambiando simplemente el contenido de secuencias de comandos, deberá volver a exportar desde Unity. Algunos ejemplos de veces que deberá volver a exportar desde Unity son:
* Agregar o quitar recursos en la pestaña proyecto.
* Cambiar cualquier valor en la pestaña del Inspector.
* Agregar o quitar objetos de la pestaña de la jerarquía.
* Cambiar las configuraciones de proyecto de Unity

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Crear e implementar una solución de Visual Studio de Unity

Se produce en el resto de compilar e implementar aplicaciones [Visual Studio](using-visual-studio.md). Deberá especificar una configuración de compilación de Unity. Convenciones de nomenclatura de Unity pueden diferir de lo ya está familiarizado normalmente en Visual Studio:

|  Configuración  |  Explicación | 
|----------|----------|
|  Depuración  |  Todas las optimizaciones desactivado y el generador de perfiles están habilitados. Se usa para depurar scripts. | 
|  Maestro  |  Todas las optimizaciones están activadas y el generador de perfiles está deshabilitada. Se usa para enviar aplicaciones a la Store. | 
|  Publicación  |  Todas las optimizaciones están activadas y se habilita el generador de perfiles. Se utiliza para evaluar el rendimiento de la aplicación. | 

Tenga en cuenta que la lista anterior es un subconjunto de los desencadenadores comunes que hará que el proyecto de Visual Studio que se generan. En general, la edición de archivos .cs desde dentro de Visual Studio no requerirá el proyecto a regenerarse a partir de Unity.

## <a name="troubleshooting"></a>Solución de problemas

Si encuentra que las modificaciones de los archivos .cs no no se reconocen en el proyecto de Visual Studio, asegúrese de que "Unity C# proyectos" está activada al generar el proyecto de VS desde el menú de compilación de Unity.
