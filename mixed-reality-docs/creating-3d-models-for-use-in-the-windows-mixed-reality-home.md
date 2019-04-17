---
title: Crear modelos 3D para su uso en el hogar
description: Creación de una guía para los modelos 3D que se usará en el inicio en HoloLens e inmersivos (VR) de Windows Mixed Reality y requisitos activos.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Límites de modelado 3D, orientación, los requisitos activos, directrices, iniciador, iniciador 3D, textura, materiales, complejidad, triángulos, malla, polígonos, polycount, de creación de modelado
ms.openlocfilehash: 209a92a8e7070ca23bcb9402d8716f3f91747a96
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598877"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Crear modelos 3D para su uso en el hogar

El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) es el punto de partida que lleguen a los usuarios antes de iniciar las aplicaciones. Puede diseñar la aplicación para aprovechar los auriculares de Windows Mixed Reality un [modelo 3D como un iniciador de aplicaciones](implementing-3d-app-launchers.md) y permitir [3D vínculos profundos a colocarse en el inicio de Windows Mixed Reality](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) desde dentro de la aplicación. En este artículo se describe las directrices para crear modelos 3D compatible con Windows Mixed Reality principal.

## <a name="asset-requirements-overview"></a>Información general sobre los requisitos de activos
Al crear modelos 3D de Windows Mixed Reality, hay algunos requisitos que deben cumplir todos los activos: 
1. [Exportar](#exporting-models) -activos se deben entregar en el formato de archivo .glb (binario glTF)
2. [Modelado](#modeling-guidelines) -activos deben ser triángulos de menos de 10 k, tener no más de 64 nodos y 32 submeshes por LOD
3. [Materiales](#material-guidelines) : las texturas que no pueden ser mayores que 4096 × 4096 y la asignación de mip más pequeña debe ser mayor que 4 en ambas dimensiones
4. [Animación](#animation-guidelines) -las animaciones no se pueden tener más de 20 minutos a 30 FPS (36.000 fotogramas clave) y debe contener < = 8192 vértices de destino morph
5. [Optimizar](#optimizations) -activos deben optimizarse mediante el [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). Se trata de **necesario en las versiones de sistema operativo de Windows < = 1709** y recomienda en las versiones de sistema operativo de Windows > = 1803

El resto de este artículo incluye una descripción detallada de estos requisitos así como directrices adicionales para asegurarse de que los modelos funcionan bien con Windows Mixed Reality principal. 

## <a name="detailed-guidance"></a>Instrucciones detalladas

## <a name="exporting-models"></a>Exportar modelos

El inicio de Windows Mixed Reality espera activos 3D para entregarse con el formato de archivo .glb con imágenes incrustadas y datos binarios. GLB es la versión binaria del formato glTF que una regalía gratuita estándar abierto para la entrega de activos 3D mantenida por el grupo Khronos. A medida que evoluciona glTF como un estándar del sector para contenidos 3D interoperable también la tendrán soporte técnico de Microsoft para el formato en las experiencias y aplicaciones de Windows. Si no ha creado un recurso glTF para poder buscar un [lista de exportadores admitidos y los convertidores de tipos](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) en la página de github glTF grupo de trabajo.  

## <a name="modeling-guidelines"></a>Directrices de modelado

Windows espera activos que se pueden generar mediante las siguientes directrices de modelado para garantizar la compatibilidad con la experiencia de inicio de realidad mixta. Al modelar en el programa de su elección tenga en cuenta las recomendaciones y las limitaciones siguientes:
1. El eje vertical debe establecerse en "S".
2. El recurso debe enfrentar "forward" hacia el eje Z positivo.
3. Se deben compilar todos los activos en el plano de cero en el origen de la escena (0,0,0)
4. Unidades de trabajo deben establecerse en metros y activos para que se pueden crear los activos a escala mundial
5. No es necesario combinar todas las mallas, pero se recomienda si tiene como destino dispositivos de restricción de recursos
6. Todas las mallas deben compartir 1 material, con solo 1 textura establecido que se usa para el activo completo
7. UVs deben disponerse en una organización cuadrada en el 0-1 espacio. Evite las texturas de disposición en mosaico aunque tienen permiso.
8. No se admiten múltiples UVs
9. No se admiten los materiales de una cara y doble

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Recuentos de triángulo y niveles de detalle

Windows Mixed Reality home no admite modelos con más de 10.000 triángulos. Se recomienda que triangular las mallas antes de exportarlos para asegurarse de que no superen este recuento. Windows MR también admite niveles de geometría opcional de detalle para garantizar un alto rendimiento y la experiencia de alta calidad. [El WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) le ayudará a combinar 3 versiones del modelo en un modelo único .glb. Windows determina qué LOD para mostrar en función de la cantidad de espacio en pantalla que está ocupando el modelo. Solo 3 niveles LOD son compatibles con el siguiente recomienda recuentos de triángulo:
<br>

|  Nivel LOD  |  Recuento de triángulo recomendada  |  Número máximo de triángulo | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>Límites de recuentos de nodo y Submalla
Windows Mixed Reality home no admite modelos con más de 64 nodos o 32 submeshes por LOD. Los nodos son un concepto en el [glTF especificación](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) que definen los objetos de la escena. Submeshes se definen en la matriz de [primitivas](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) en la malla en el objeto. 

|  Característica |  Descripción  |  Max compatibles | Documentación |
|------|------|------|------|
|  Nodos |  Objetos de la escena glTF |  64 por LOD | [Here](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  Suma de los elementos primitivos en todas las mallas |  32 por LOD | [Here](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Directrices de material

Las texturas deben estar preparadas mediante un flujo de trabajo de rugosidad metal PBR. Empiece por crear un conjunto completo de las texturas como Albedo, Normal, oclusión, metálicos y rugosidad. Windows Mixed Reality admite texturas con resoluciones de hasta 4096 × 4096, pero se recomienda que se crea en 512 x 512. Además deben crearse las texturas con resoluciones en múltiplos de 4 puesto que éste es un requisito para el formato de compresión aplicado a las texturas en los pasos de exportación que se describen a continuación. Por último, cuando los mapas mip gerating o una textura el mip más baja debe ser un máximo de 4 x 4.
<br>

|  Tamaño de textura recomendado  |  Tamaño de la textura máxima | Mip más bajo
|----|----|----|
|  512x512  |  4096x4096 | número máximo de 4 x 4|

### <a name="albedo-base-color-map"></a>Mapa albedo (color base)

Color sin formato sin información de iluminación. Esta asignación también contiene la reflectancia difuso información y metal (blanco en el mapa metálico) y superficies aislante (negro en el mapa metálico) respectivamente.

### <a name="normal"></a>Normal

Mapa de Normal de espacio tangente

### <a name="roughness-map"></a>Mapa de rugosidad

Describe la microsurface del objeto. Es una aproximación del blanco 1.0 negro 0,0 es suave. Este mapa proporciona el activo que más caracteres ya que realmente describe la superficie, por ejemplo, es muy general, las huellas digitales, manchas, suciedad etcetera.

### <a name="ambient-occlusion-map"></a>Mapa de oclusión de ambiente

Mapa de escala del valor que representan áreas de luz ocluido que bloquea las reflexiones

### <a name="metallic-map"></a>Mapa metálico

Indica que el sombreador si algo es de sistema operativo o no. Sistema operativo sin procesar = 1,0 metal no blanco = 0,0 negro. Puede haber valores gris transitorios que indican de alguna que abarca el sistema operativo sin procesar como suciedad, pero en general, esta asignación debe ser blanco y negro.

## <a name="optimizations"></a>optimizaciones

Windows Mixed Reality principal ofrece una serie de optimizaciones encima de la especificación de glTF core definido mediante las extensiones personalizadas. Estas optimizaciones son necesarios en las versiones de Windows < = 1709 y recomienda en las versiones más recientes de Windows. Puede optimizar fácilmente cualquier modelo glTF 2.0 mediante la [Mixed Reality activos Convertidor Windows disponible en GitHub](https://github.com/Microsoft/glTF-Toolkit/releases). Esta herramienta llevará a cabo la textura correcta de empaquetado y optimizaciones como se indica a continuación. Para uso general se recomienda usar el WindowsMRAssetConverter, pero si necesita más control sobre la experiencia y le gustaría crear su propia canalización de optimización, a continuación, puede hacer referencia a las especificaciones detalladas a continuación.  

### <a name="materials"></a>Materiales

Para mejorar el tiempo en entornos Windows MR de realidad mixta de carga de activos permite presentar las texturas comprimidas de DDS empaquetadas según la textura empaquetar el esquema definido en esta sección. Las texturas de dominios de detección se hace referencia mediante el [MSFT_texture_dds extensión](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). Se recomienda comprimir las texturas. 

#### <a name="hololens"></a>HoloLens

Experiencias de realidad mixta basada en HoloLens esperan las texturas se empaquetan con un programa de instalación de textura de 2 mediante la siguiente especificación de empaquetado:
<br>

|  Propiedad glTF  |  Textura  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Red (R), Green (G), Blue (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), (B), de rugosidad metálicos (A) | 


Al comprimir las texturas DDS en cada asignación se espera que la compresión siguiente:
<br>

|  Textura  |  Compresión esperada | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Inmersivos (VR)

Basados en PC Windows Mixed Reality experiencias para inmersivos (VR) esperan las texturas se empaquetan con un programa de instalación de la textura de 3 mediante la siguiente especificación de empaquetado:

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  Propiedad glTF  |  Textura  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Red (R), Green (G), Blue (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R), dureza (G), metálicos (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Al comprimir las texturas DDS en cada asignación se espera que la compresión siguiente:
<br>

|  Textura  |  Compresión esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  Propiedad glTF  |  Textura  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Red (R), Green (G), Blue (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R), metálicos (G), (B) de oclusión | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Al comprimir las texturas DDS en cada asignación se espera que la compresión siguiente:
<br>

|  Textura  |  Compresión esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Adición de malla LODs

El Sr. Windows utiliza el nodo de geometría LODs para representar modelos 3D en diferentes niveles de detalle, dependiendo de la cobertura de la pantalla. Aunque técnicamente, esta característica no es necesaria, se recomienda para todos los activos. Windows admite actualmente 3 niveles de detalle. El valor predeterminado LOD es 0, que representa la mejor calidad. Otros LODs están numeradas secuencialmente, por ejemplo, 1, 2 y get progresivamente más abajo en la calidad. El [Windows mixto realidad activos convertidor](https://github.com/Microsoft/glTF-Toolkit/releases) admite la generación de recursos que cumplen esta especificación LOD al aceptar varios modelos glTF y combinarlos en un solo recurso con los niveles LOD válidos. En la tabla siguiente se describe los objetivos de ordenación y triángulo LOD esperados:
<br>

|  Nivel LOD  |  Recuento de triángulo recomendada  |  Número máximo de triángulo | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

Cuando se usa siempre LODs especifique 3 niveles LOD. Falta LODs hará que el modelo no se represente inesperadamente como los conmutadores de sistema LOD al nivel LOD que faltan. glTF 2.0 no admite actualmente LODs como parte de la especificación de core. LODs, por tanto, debe definirse mediante el [extensión MSFT_LOD](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Cobertura de pantalla

LODs se muestran en Windows Mixed Reality se basa en un sistema controlado por el valor de la cobertura de pantalla establecido en cada LOD. Los objetos que están consumiendo actualmente una mayor parte del espacio de pantalla se muestran en un nivel superior de LOD. Cobertura de pantalla no es una parte de la especificación de glTF 2.0 core y debe especificarse utilizando MSFT_ScreenCoverage en la sección "adicionales" de la [MSFT_lod extensión](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Nivel LOD  |  Intervalo recomendado  |  Intervalo predeterminado | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  En un 50% 20%  |  .2 | 
|  LOD 2 |  En un 20% 1%  |  .01 | 
|  LOD 4  |  En un 1%  |  - | 

## <a name="animation-guidelines"></a>Directrices de animación

> [!NOTE]
> Esta característica se agregó como parte de [Windows 10 de abril de 2018 Update](release-notes-april-2018.md). En versiones anteriores de Windows, estas animaciones no se reproducen, sin embargo, cargará si se crean según las instrucciones de este artículo.  

La página principal de realidad mixta admite objetos animados glTF en HoloLens e inmersivos (VR). Si desea activar las animaciones en el modelo, deberá usar la extensión de asignación de animación en el formato glTF. Esta extensión le permite activar las animaciones en el modelo glTF según la presencia de los usuarios en el mundo, por ejemplo activar una animación cuando el usuario está cerca del objeto o mientras está examinando. Si se glTF objeto tiene animaciones, pero no define desencadenadores las animaciones no se reproducirá. La siguiente sección describe un flujo de trabajo para agregar estos desencadenadores para cualquier objeto glTF animado.

### <a name="tools"></a>Herramientas
En primer lugar, descargue las herramientas siguientes si no tiene ya. Estas herramientas le resultará fácil de abrir cualquier modelo glTF, obtener la vista previa, realizar cambios y guardar la salida como glTF o .glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [glTF Tools para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Abrir y obtener una vista previa del modelo
Comience abriendo el modelo glTF en VSCode, arrastre el archivo .glTF en la ventana del editor. Tenga en cuenta que si tiene un .glb en lugar de un archivo .glTF puede importar en VSCode mediante el complemento de herramientas glTF que ha descargado. Vaya a "Ver -> Paleta de comandos" y, a continuación, comience a escribir "glTF" en la paleta de comandos y seleccione "glTF: Importar desde glb"que se abrirá un selector de archivos para importar un .glb con. 

Después de abrir el modelo glTF debería ver el código JSON en la ventana del editor. Tenga en cuenta que también una vista previa en un visor 3D en vivo mediante el modelo de la derecha haciendo clic en el nombre de archivo y seleccionar el "glTF: Obtener una vista previa de un modelo 3D"acceso directo de comando en el menú contextual. 

### <a name="adding-the-triggers"></a>Agregar los desencadenadores
Desencadenadores de animación se agregan al modelo de glTF JSON mediante la extensión de asignación de animación. La extensión de asignación de la animación está documentada públicamente [aquí en GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (tenga en cuenta: ESTO ES UNA EXTENSIÓN DE BORRADOR). Para agregar la extensión a su desplazamiento simplemente modelo hasta el final del archivo glTF en el editor y agregue el bloque "extensionsUsed" y "extensions" al archivo si aún no existen. En la sección "extensionsUsed" se agregará una referencia a la extensión "EXT_animation_map" y en el bloque "extensions" agregará las asignaciones a las animaciones en el modelo.

Como se indicó [en las especificaciones de](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) definir lo que desencadena la animación mediante la cadena "semántica" en una lista de "animaciones" que es una matriz de índices de la animación. Hemos especificado la animación se reproduzca mientras el usuario se gazing en el objeto en el ejemplo siguiente:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
La semántica de los desencadenadores de animación siguiente es compatibles con Windows Mixed Reality principal.  
* "SIEMPRE": Constantemente repetir una animación
* "RETENCIÓN": Un bucle durante toda la duración que se obtiene un objeto.
* "MIRADA": Un bucle mientras se está examinando un objeto
* "PROXIMIDAD": Un bucle mientras un visor está cerca de un objeto
* "APUNTA": Un bucle mientras un usuario que señala a un objeto

### <a name="saving-and-exporting"></a>Guardar y exportar
Una vez realizados los cambios al modelo glTF puede guardar directamente como glTF o clic el nombre del archivo en el editor y seleccione "glTF: Exportar a GLB (archivo binario) "para exportar en su lugar un .glb. 

### <a name="restrictions"></a>Restricciones
Las animaciones no se pueden tener más de 20 minutos y no pueden contener más de 36.000 fotogramas clave (minutos de 20 a 30 FPS). Además cuando se usa en función de destino de morph las animaciones no superar los 8192 vértices de destino morph o menos. Si se supera estos tarden voluntad de recuento activo animado a no ser compatibles en la página principal de Windows Mixed Reality. 

|Característica|Máximo|
|-----|-----|
|Duración|20 minutos|
|Fotogramas clave|36,000| 
|Morph vértices de destino|8192|

## <a name="gltf-implementation-notes"></a>notas de implementación glTF
El Sr. Windows no admite volteo geometría mediante escalas negativo. Geometría con escalas negativo probablemente tendrá como resultado de artefactos visuales.

El recurso glTF debe apuntar a la escena predeterminada con el atributo de la escena para representarse MR por Windows. Además, el cargador de Windows MR glTF anteriores a la [actualización de Windows 10 de abril de 2018](release-notes-april-2018.md) **requiere** descriptores de acceso:
* Debe tener valores mínimo y máximo.
* Valor escalar de tipo debe ser componentType UNSIGNED_SHORT (5123) o UNSIGNED_INT (5125).
* Tipo VEC2 y VEC3 deben ser componentType FLOAT (5126).

Las siguientes propiedades de material se utilizan de la especificación de glTF 2.0 core pero no es necesario:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: Debe apuntar a una textura que se almacenan en dominios de detección.
* emissiveTexture: Debe apuntar a una textura que se almacenan en dominios de detección.
* emissiveFactor
* alphaMode

Se omiten las siguientes propiedades de material de la especificación de core:
* Todos los Multi-UVs
* metalRoughnessTexture: En su lugar se debe usar el empaquetado de textura optimizado de Microsoft definido a continuación
* normalTexture: En su lugar se debe usar el empaquetado de textura optimizado de Microsoft definido a continuación
* normalScale
* occlusionTexture: En su lugar se debe usar el empaquetado de textura optimizado de Microsoft definido a continuación
* occlusionStrength

MR de Windows no admite puntos y líneas de modo primitivo. 

Se admite solo un único atributo de vértices de UV.

## <a name="additional-resources"></a>Recursos adicionales
* [glTF exportadores y los convertidores de tipos](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [glTF Kit de herramientas](https://github.com/Microsoft/glTF-Toolkit)
* [glTF 2.0 especificación](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft glTF LOD especificación de extensión](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC mixto especificación de extensiones de empaquetado de textura de realidad](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens mixto especificación de extensiones de empaquetado de textura de realidad](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Especificación de extensiones de Microsoft DDS texturas glTF](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Vea también

* [Implementar los iniciadores de aplicaciones 3D (aplicaciones UWP)](implementing-3d-app-launchers.md)
* [Implementar los iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
* [Navegar por el inicio de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
