---
title: Agregar entornos de inicio personalizados
description: Además de los entornos de inicio de Windows Mixed Reality que proporcionamos, puede experimentar con la creación y uso de sus propios.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, en realidad Virtual, VR, MR, Home, entornos personalizados, lugares, casa cliff, skyloft, usuario, crear
ms.openlocfilehash: ef140efd88aa0d3329ae2aa7e5b202c3bfe77c0a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597518"
---
# <a name="add-custom-home-environments"></a>Agregar entornos de inicio personalizados

>[!NOTE]
>Se trata de una característica experimental. Pruébelo y Diviértase con él, pero no se sorprenda si todo lo que no suele funciona según lo previsto. Se evalúan la viabilidad de esta característica y el interés usarlo, por lo tanto, Díganos sobre su experiencia (y los errores que encuentre) en el [foros para desarrolladores](https://forums.hololens.com/categories/custom-home-environments).

A partir de la [actualización de Windows 10 de abril de 2018](#release-notes-april-2018.md), hemos habilitado una característica experimental que le permite agregar entornos personalizados para el selector de lugares (en el menú Inicio) para usar como el [Windows Mixed Reality doméstica](#navigating-the-windows-mixed-reality-home.md). Windows Mixed Reality tiene dos entornos de forma predeterminada, Cliff House y Skyloft, que puede elegir como su casa. Para expandir esa lista con sus propias creaciones permite crear entornos personalizados. Hemos realizado esto disponibles en un estado temprana para evaluar el interés de los creadores y desarrolladores, consulte ¿Qué tipos de espacios de crear y comprender cómo trabajar con distintas herramientas de creación.

Cuando se usa un entorno personalizado, observará que teleporting, interactuar con las aplicaciones y colocando hologramas funciona al igual que ocurre en el Cliff House y Skyloft. Puede explorar el web en un entorno de fantasía o rellenar una ciudad futurista con hologramas: las posibilidades son infinitas.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Entornos de inicio personalizados</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="trying-a-sample-environment"></a>Probar un entorno de ejemplo

Hemos creado un entorno de ejemplo que muestra algunas de las posibilidades creativas de entornos de inicio personalizados. Siga estos pasos para probar esta característica:
1. [Descargar nuestro entorno de ejemplo isla de fantasía](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (apunta el vínculo al archivo ejecutable autoextraíble).

    ![Entorno de ejemplo de fantasía isla](images/FantasyLand.jpg)<br>
    *Entorno de ejemplo de fantasía isla*<br>

2. Ejecute el **Fantasy_Island.exe** que acaba de descargar el archivo.

    > [!NOTE]
    > Al intentar ejecutar un archivo .exe descargado de Internet (como ésta), puede encontrar un elemento emergente "Windows había protegido su PC". Para ejecutar Fantasy_Island.exe desde esta ventana emergente, seleccione **obtener más información** y, a continuación, **ejecutar de todas formas**. Esta configuración de seguridad está pensada para impedir la descarga de archivos, es posible que no desea confiar, lo elija esta opción sólo si confía en el origen del archivo.

3. Abra **Explorador de archivos** y navegue hasta la carpeta entornos pegando lo siguiente en la barra de direcciones: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.
4. Copie el entorno de ejemplo que descargó en esta carpeta.
5. Reiniciar **mixto realidad Portal**. Esto actualizará la lista de entornos en el selector de lugares.
6. Colocar en los auriculares. Una vez que esté en la página principal, abra el **menú Inicio** usando el Windows botón el controlador.
7. Seleccione el **lugares** icono situado encima de la lista de aplicaciones ancladas para elegir un entorno doméstico.
8. Encontrará el entorno de la isla de fantasía que descargó en la lista de lugares. Seleccione **isla de fantasía** para escribir el nuevo entorno doméstico personalizado!

## <a name="creating-your-own-custom-environment"></a>Crear su propio entorno personalizado

Además de usar nuestros entornos de ejemplo, puede exportar sus propios entornos personalizados mediante el software de edición de 3D favorito. 

### <a name="modeling-guidelines"></a>Directrices de modelado

Al modelar su entorno, tenga en cuenta las siguientes recomendaciones. Esto ayudará a garantizar el usuario genera en la orientación correcta en un mundo believably tamaño:

1. Los usuarios generará 0,0,0 centro es así, la ubicación deseada spawn en torno al origen.
2. Unidades de trabajo deben establecerse en metros, por lo que se pueden crear los activos a escala mundial.
3. El eje vertical debe establecerse en "S".
4. El recurso debe enfrentar "forward" hacia el eje Z positivo.
5. No es necesario combinar todas las mallas, pero se recomienda si tiene como destino dispositivos con recursos limitados.

### <a name="exporting-your-environment"></a>Exportación de su entorno

Windows Mixed Reality se basa en glTF binario (.glb) como el formato de entrega de activos para los entornos. glTF es una con derechos de licencia gratuita estándar abierto para la entrega de activos 3D mantenida por el grupo Khronos. A medida que evoluciona glTF como un estándar del sector para contenidos 3D interoperable, también la tendrán soporte técnico de Microsoft para el formato en las experiencias y aplicaciones de Windows.

El primer paso para exportar activos que se usará como entornos de inicio personalizados es generar un modelo glTF 2.0. El grupo de trabajo glTF mantiene un [lista de exportadores admitidos y los convertidores de tipos](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) para crear un modelo glTF 2.0. Para empezar, use uno de los programas que aparecen en esta página para crear y exportar un modelo glTF 2.0 o convertir un modelo existente mediante uno de los convertidores de tipos compatibles.

Además, visite [en este artículo útil](https://www.khronos.org/blog/art-pipeline-for-gltf) que proporciona información general de un flujo de trabajo de arte para exportar modelos glTF desde Blender y 3DS Max directamente. 

### <a name="environment-limits"></a>Límites del entorno

Todos los entornos deben ser < 256 MB. Se producirá un error en entornos de mayores que 256 MB cargar y revertir a un mundo vacío con simplemente skybox predeterminada que rodean el usuario. Mantenga este límite de tamaño de archivo en cuenta al crear los modelos. Además, si va a optimizar su entorno mediante el WindowsMRAssetConverter tal como se describe a continuación, ser consciente de que aumentará el tamaño de textura como el optimizador crea las texturas que tienen un tamaño de archivo más grande, pero se cargan con mayor rapidez. 

### <a name="optimizing-your-environment"></a>Optimizar el entorno

Windows Mixed Reality admite un número de optimizaciones opcionales que reducirá significativamente el tiempo de carga de los entornos. Esto puede ser especialmente importante para los entornos con muchas texturas, que lo harán en ocasiones, tiempo de espera mientras se carga. En general, se recomienda este paso para todos los activos, sin embargo, en entornos más pequeños con pocos o de baja resolución texturas no siempre requieren. 

Para facilitar este proceso, hemos creado la [Mixed Reality activos Convertidor Windows (disponible en GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) para realizar las optimizaciones. Esta herramienta utiliza un conjunto de utilidades disponibles en el Kit de herramientas de Microsoft glTF para optimizar .glb ni glTF 2.0 estándar mediante la realización de una mejora del empaquetado texturas adicionales, compresión y resolución reducción vertical. 

Actualmente, el convertidor admite un número de marcas para ajustar el comportamiento exacto de las optimizaciones. Se recomienda ejecutar con las marcas siguientes para obtener mejores resultados:

Bandera|Valores recomendados|Descripción
---|---|---
-max-texture-size|1024 o 2048| Ajustar para mejorar la calidad de las texturas, el valor predeterminado es 512 x 512. Por lo tanto, tenga en cuenta que un valor mayor afectarán significativamente el tamaño del archivo del entorno tenga el límite de 256 mb en mente
-min-version|1803|Entornos personalizados solo se admiten en las versiones de windows > = 1803. Esta marca quitará las texturas para versiones anteriores y reducir el tamaño de archivo del recurso final

Por ejemplo:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>El entorno de pruebas

Una vez que su entorno .glb final está listo para comenzar a probarlo en los auriculares. Comenzar en el paso 2 en el ["Tratando de un entorno de ejemplo"](#trying-a-sample-environment) sección para utilizar el entorno personalizado como el inicio de realidad mixta. 

## <a name="feedback"></a>Comentarios

Aunque se evalúan esta característica experimental, estamos interesados en aprender cómo va a utilizar entornos personalizados, los errores que surjan, y cómo desea que la característica. Comparta sus comentarios todo para crear y usar entornos de inicio personalizados en el [foros para desarrolladores](https://forums.hololens.com/categories/custom-home-environments).

## <a name="troubleshooting-and-tips"></a>Sugerencias y solución de problemas

### <a name="how-do-i-change-the-name-of-the-environment"></a>¿Cómo se puede cambiar el nombre del entorno?

El nombre de archivo en la carpeta entornos se usará en el selector de lugares. Para cambiar el nombre de su entorno simplemente cambie el nombre del entorno de nombre de archivo y, a continuación, reinicie Portal de realidad mixta.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>¿Cómo quito entornos personalizados de mi selector lugares?

Para quitar un entorno personalizado, abra la carpeta entornos en su PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) y eliminar el entorno. Una vez que reinicie Portal de realidad mixta, este entorno ya no aparecerá en el selector de lugares. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>¿Cómo predeterminado a mi favorito entorno personalizado?

Actualmente no se puede cambiar el entorno predeterminado. Cada vez que reinicie Portal de realidad mixta, se le devolverá al entorno Cliff House. 

### <a name="i-spawn-into-a-blank-space"></a>Generar en un espacio en blanco

Windows Mixed Reality [no es compatible con entornos que superan los 256 mb](#environment-limits). Cuando un entorno supera este límite, se colocará en el cuadro vacío cielo con ningún modelo.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Tarda mucho tiempo en cargar mi entorno

Puede agregar las optimizaciones de opcionales a su entorno para que sea más rápido cargar. Consulte ["Optimizar el entorno"](#optimizing-your-environment) para obtener más información.

### <a name="the-scale-of-my-environment-is-incorrect"></a>La escala de mi entorno es incorrecta

Windows Mixed Reality traduce glTF unidades a 1 metro al cargar los entornos. Si su entorno de carga de una escala inesperada, compruebe lo siguiente para asegurarse de que el exportador de la que está modelando a una escala de 1 metro. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>La ubicación spawn en mi entorno es incorrecta

La ubicación de generación predeterminada se encuentra en 0,0,0 en el entorno. Sus no actualmente es posible personalizar esta ubicación, por lo que debe modificar el punto de reproducción mediante la exportación de su entorno con el origen situado en el punto deseado spawn.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>El audio no parece correcto en el entorno

Cuando se crea el entorno personalizado, va a utilizar una simulación de representación acústica que no coincide con el espacio físico que ha creado. Sonido pueden proceder de las instrucciones incorrectas y puede parecer atenuarse. 

## <a name="see-also"></a>Vea también
* [Navegar por las ventanas mixto realidad principal](#navigating-the-windows-mixed-reality-home.md)
* [Windows mixto realidad conversor de recurso (en GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)

