---
title: Crear modelos 3D para su uso en el hogar
description: Requisitos de recursos e instrucciones de creación para modelos 3D que se usarán en la Página principal de Windows Mixed Reality en auriculares de HoloLens y envolventes (VR).
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, modelado, guía de modelado, requisitos de recursos, directrices de creación, iniciador, selector 3D, textura, materiales, complejidad, triángulos, malla, polígonos, polinúmero, límites
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692286"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Crear modelos 3D para su uso en el hogar

La [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones. Puede diseñar la aplicación para que los auriculares de realidad mixta de Windows aprovechen un [modelo 3D como un iniciador de aplicaciones](implementing-3d-app-launchers.md) y permitir que [los vínculos profundos 3D se coloquen en la Página principal de Windows Mixed Reality](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) desde la aplicación. En este artículo se describen las instrucciones para crear modelos 3D compatibles con la Página principal de Windows Mixed Reality.

## <a name="asset-requirements-overview"></a>Información general sobre los requisitos de activos
Al crear modelos 3D para Windows Mixed Reality, hay algunos requisitos que deben cumplir todos los recursos: 
1. [Exportación](#exporting-models) : los recursos se deben entregar en el formato de archivo. glb (glTF binario)
2. [Modelado](#modeling-guidelines) : los recursos deben tener menos de 10 000 triángulos, no tener más de 64 nodos y submallas 32 por LOD
3. [Materiales](#material-guidelines) : las texturas no pueden ser mayores de 4096 x 4096 y el mapa MIP más pequeño no debe ser mayor que 4 en ninguna de las dimensiones.
4. [Animación](#animation-guidelines) : las animaciones no pueden tener más de 20 minutos a 30 fps (fotogramas clave de 36.000) y deben contener < = 8192 vértices de destino de transformación
5. [Optimización](#optimizations) : los recursos deben optimizarse mediante [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). Esto es **necesario en las versiones del sistema operativo windows < = 1709** y recomendado en las versiones del sistema operativo Windows > = 1803

En el resto de este artículo se incluye información general detallada de estos requisitos, así como directrices adicionales para asegurarse de que los modelos funcionan bien con la Página principal de Windows Mixed Reality. 

## <a name="detailed-guidance"></a>Instrucciones detalladas

### <a name="exporting-models"></a>Exportar modelos

La Página principal de Windows Mixed Reality espera que se entreguen recursos 3D con el formato de archivo. glb con imágenes incrustadas y datos binarios. Glb es la versión binaria del formato glTF, que es un estándar abierto sin regalías para la entrega de recursos 3D mantenido por el Grupo Khronos. A medida que glTF evolucione como un estándar del sector para el contenido en 3D interoperable, de este modo, la compatibilidad de Microsoft con el formato de las aplicaciones y experiencias de Windows. Si no ha creado un recurso de glTF antes de encontrar una [lista de los exportadores y convertidores admitidos](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) en la página de github grupo de trabajo de glTF.  

### <a name="modeling-guidelines"></a>Directrices de modelado

Windows espera que los recursos se generen con las siguientes directrices de modelado para garantizar la compatibilidad con la experiencia de inicio de realidad mixta. Al modelar el programa de su elección, tenga en cuenta las siguientes recomendaciones y limitaciones:
1. El eje hacia arriba debe establecerse en "Y".
2. El recurso debe estar en "adelante" hacia el eje Z positivo.
3. Todos los recursos deben crearse en el plano de la escena en el origen de la escena (0,0)
4. Las unidades de trabajo deben establecerse en medidores y recursos para que los recursos puedan crearse a escala mundial.
5. No es necesario combinar todas las mallas, pero se recomienda si tiene como destino dispositivos con restricción de recursos.
6. Todas las mallas deben compartir 1 material, con solo un conjunto de textura que se usa para todo el recurso.
7. UVs debe estar dispuesta en una disposición cuadrada en el espacio 0-1. Evite las texturas de mosaico, aunque se permitan.
8. No se admiten varios UVs
9. No se admiten materiales de doble cara

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Recuentos de triángulos y niveles de detalle (LODs)

La Página principal de Windows Mixed Reality no admite modelos con más de 10.000 triángulos. Se recomienda triangular las mallas antes de la exportación para asegurarse de que no superan este recuento. Windows MR también admite niveles de geometría opcionales (LODs) para garantizar una experiencia eficaz y de alta calidad. [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) le ayudará a combinar 3 versiones del modelo en un único modelo. glb. Windows determina qué LOD Mostrar en función de la cantidad de espacio real de la pantalla que está ocupando el modelo. Solo se admiten 3 niveles de LOD con los siguientes recuentos de triángulos recomendados:
<br>

|  Nivel LOD  |  Recuento de triángulos recomendado  |  Recuento de triángulo máximo | 
|------|------|------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

### <a name="node-counts-and-submesh-limits"></a>Recuentos de nodos y límites de submallas
La Página principal de Windows Mixed Reality no admite modelos con más de 64 nodos o submallas 32 por LOD. Los nodos son un concepto de la [especificación glTF](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) que define los objetos de la escena. Las submallas se definen en la matriz de [primitivas](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) de la malla en el objeto. 

|  Característica |  Descripción  |  Compatibilidad máxima | Documentación |
|------|------|------|------|
|  Nodos |  Objetos de la escena glTF |  64 por LOD | [Presenta](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submallas |  Suma de primitivas en todas las mallas |  32 por LOD | [Presenta](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Directrices de materiales

Las texturas se deben preparar mediante un flujo de trabajo de desbaste de metal. Empiece por crear un conjunto completo de texturas, como albedo, normal, oclusión, metálico y rugosidad. Windows Mixed Reality admite texturas con resoluciones de hasta 4096x4096, pero le recomendamos que cree en 512 x 512. Además, las texturas deben crearse en resoluciones en múltiplos de 4, ya que se trata de un requisito para el formato de compresión aplicado a las texturas en los pasos de exportación que se describen a continuación. Por último, cuando Gerating MIP Maps o una textura, el MIP más bajo debe ser un máximo de 4x4.
<br>

|  Tamaño de textura recomendado  |  Tamaño máximo de textura | MIP más bajo
|----|----|----|
|  512 x 512  |  4096x4096 | 4x4 máx.|

### <a name="albedo-base-color-map"></a>Mapa Albedo (color base)

Color sin procesar sin información de iluminación. Este mapa también contiene la reflexión y la información difusa de las superficies metal (blanco en las asignaciones metálicas) y aislante (negro en el mapa metálico) respectivamente.

### <a name="normal"></a>Normal

Mapa normal de espacio tangente

### <a name="roughness-map"></a>Mapa de desbaste

Describe la microsuperficie del objeto. El blanco 1,0 es el negro más suave 0,0. Este mapa proporciona al activo el carácter más alto, ya que describe realmente la superficie, por ejemplo, grietas, huellas digitales, manchas, grime, etc.

### <a name="ambient-occlusion-map"></a>Mapa de oclusión de ambiente

Mapa de escala de valor que describe áreas de ocluidos Light que bloquea las reflexiones

### <a name="metallic-map"></a>Mapa metálico

Indica al sombreador si algo es metal o no. Metal sin procesar = 1,0 blanco no metal = 0,0 negro. Puede haber valores grises transitorios que indiquen algo que cubra el metal sin procesar, como la suciedad, pero en general, este mapa debe ser solo en blanco y negro.

## <a name="optimizations"></a>Optimizaciones

Windows Mixed Reality Home ofrece una serie de optimizaciones sobre la especificación de glTF básica definida mediante extensiones personalizadas. Estas optimizaciones son necesarias en las versiones de Windows < = 1709 y se recomiendan en las versiones más recientes de Windows. Puede optimizar fácilmente cualquier modelo de glTF 2,0 con el [convertidor de activos de Windows Mixed Reality disponible en github](https://github.com/Microsoft/glTF-Toolkit/releases). Esta herramienta llevará a cabo las optimizaciones y el empaquetado correctos de las texturas, tal y como se especifica a continuación. Para el uso general, se recomienda usar WindowsMRAssetConverter, pero si necesita más control sobre la experiencia y desea crear su propia canalización de optimización, puede hacer referencia a la especificación detallada que aparece a continuación.  

### <a name="materials"></a>Prima

Para mejorar el tiempo de carga de los recursos en entornos de realidad mixta, Windows MR admite la representación de texturas DDS comprimidas en función del esquema de empaquetado de textura definido en esta sección. Se hace referencia a las texturas DDS con la [extensión MSFT_texture_dds](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). Es muy recomendable comprimir las texturas. 

#### <a name="hololens"></a>HoloLens

Las experiencias de realidad mixta basadas en HoloLens esperan que las texturas se empaquete con una configuración de 2 texturas mediante la siguiente especificación de empaquetado:
<br>

|  Propiedad glTF  |  Degrada  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rojo (R), verde (G), azul (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), rugosidad (B), metálico (A) | 


Al comprimir las texturas DDS, se espera la siguiente compresión en cada asignación:
<br>

|  Degrada  |  Compresión esperada | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Auriculares envolventes (VR)

Las experiencias de Windows Mixed Reality basadas en PC para auriculares envolvente (VR) esperan que las texturas se empaquete con una configuración de 3 texturas mediante la siguiente especificación de empaquetado:

##### <a name="windows-os--1803"></a>Windows OS > = 1803

<br>

|  Propiedad glTF  |  Degrada  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rojo (R), verde (G), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Oclusión (R), desbaste (G), metálico (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Al comprimir las texturas DDS, se espera la siguiente compresión en cada asignación:
<br>

|  Degrada  |  Compresión esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS < = 1709
<br>

|  Propiedad glTF  |  Degrada  |  Esquema de empaquetado | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rojo (R), verde (G), azul (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Desbaste (R), metálico (G), oclusión (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Al comprimir las texturas DDS, se espera la siguiente compresión en cada asignación:
<br>

|  Degrada  |  Compresión esperada | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Agregar LODs de malla

Windows MR usa el nodo de geometría LODs para representar modelos 3D en diferentes niveles de detalle en función de la cobertura de la pantalla. Aunque esta característica técnicamente no es necesaria, se recomienda encarecidamente para todos los recursos. Actualmente Windows admite tres niveles de detalle. El valor de LOD predeterminado es 0, que representa la mayor calidad. Otros LODs se numeran secuencialmente, por ejemplo, 1,2 y se reduce progresivamente la calidad. El [convertidor de activos de Windows Mixed Reality](https://github.com/Microsoft/glTF-Toolkit/releases) admite la generación de recursos que cumplen esta especificación LOD al aceptar varios modelos glTF y combinarlos en un único recurso con niveles de LOD válidos. En la tabla siguiente se describen los objetivos de ordenación LOD y triángulo esperados:
<br>

|  Nivel LOD  |  Recuento de triángulos recomendado  |  Recuento de triángulo máximo | 
|-------|-------|-------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

Al usar LODs, especifique siempre 3 niveles de LOD. Si falta LODs, el modelo no se representará de forma inesperada, ya que el sistema LOD cambia al nivel de LOD que falta. glTF 2,0 no admite actualmente LODs como parte de la especificación principal. Por lo tanto, LODs debe definirse mediante la [extensión MSFT_LOD](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Cobertura de pantalla

LODs se muestran en Windows Mixed Reality en función de un sistema controlado por el valor de la cobertura de pantalla establecido en cada LOD. Los objetos que están consumiendo una parte más grande del espacio de la pantalla se muestran en un nivel más alto de LOD. La cobertura de pantalla no forma parte de la especificación Core glTF 2,0 y debe especificarse mediante MSFT_ScreenCoverage en la sección "extras" de la [extensión MSFT_lod](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  Nivel LOD  |  Intervalo recomendado  |  Intervalo predeterminado | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  .5 | 
|  LOD 1 |  En 50%-20%  |  0,2 | 
|  LOD 2 |  En un 20%-1%  |  .01 | 
|  LOD 4  |  En un 1%  |  - | 

## <a name="animation-guidelines"></a>Instrucciones de animación

> [!NOTE]
> Esta característica se agregó como parte de la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md). En versiones anteriores de Windows, estas animaciones no se reproducirán, sin embargo, se cargarán si se crean según las instrucciones de este artículo.  

La Página principal de realidad mixta admite objetos glTF animados en cascos HoloLens y envolventes (VR). Si desea desencadenar animaciones en el modelo, deberá usar la extensión de la asignación de animación en el formato glTF. Esta extensión le permite desencadenar animaciones en el modelo glTF en función de la presencia de los usuarios en el mundo; por ejemplo, desencadenar una animación cuando el usuario está cerca del objeto o mientras lo examina. Si glTF objeto tiene animaciones, pero no define desencadenadores, las animaciones no se reproducirán. En la sección siguiente se describe un flujo de trabajo para agregar estos desencadenadores a cualquier objeto glTF animado.

### <a name="tools"></a>Herramientas
En primer lugar, descargue las herramientas siguientes si aún no las tiene. Estas herramientas facilitan el proceso de abrir cualquier modelo de glTF, obtener una vista previa del mismo, realizar cambios y volver a guardarlos como glTF o. glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Herramientas de glTF para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Abrir y obtener una vista previa del modelo
Comience abriendo el modelo glTF en VSCode arrastrando el archivo. glTF a la ventana del editor. Tenga en cuenta que si tiene un. glb en lugar de un archivo. glTF, puede importarlo en VSCode con el complemento de herramientas de glTF que descargó. Vaya a "vista-> paleta de comandos" y, a continuación, empiece a escribir "glTF" en la paleta de comandos y seleccione "glTF: Importar desde glb ", que mostrará un selector de archivos para importar un. glb con. 

Una vez que haya abierto el modelo glTF, debería ver el archivo JSON en la ventana del editor. Tenga en cuenta que también puede obtener una vista previa del modelo en un visor 3D en directo con haciendo clic con el botón secundario en el nombre del archivo y seleccionando "glTF: Vista previa del modelo 3D "acceso directo del comando en el menú contextual. 

### <a name="adding-the-triggers"></a>Agregar los desencadenadores
Los desencadenadores de animación se agregan al modelo JSON de glTF con la extensión de la asignación de animación. La extensión de la asignación de animación se documenta públicamente [aquí en github](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (Nota: SE TRATA DE UNA EXTENSIÓN DE BORRADOR). Para agregar la extensión al modelo, solo tiene que desplazarse hasta el final del archivo glTF en el editor y agregar el bloque "extensionsUsed" y "Extensions" al archivo si aún no existen. En la sección "extensionsUsed", agregará una referencia a la extensión "EXT_animation_map" y en el bloque "Extensions" agregará las asignaciones a las animaciones del modelo.

Como se indicó [en la especificación](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) , se define lo que desencadena la animación mediante la cadena "Semantic" en una lista de "animaciones", que es una matriz de índices de animación. En el ejemplo siguiente, hemos especificado la animación que se va a reproducir mientras el usuario está Gazing en el objeto:

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
La siguiente animación desencadena semántica es compatible con la Página principal de Windows Mixed Reality.  
* "SIEMPRE": Repetir una animación constantemente
* "MANTENIDO": Se repite durante todo el tiempo que se captura un objeto.
* "MIRA": En bucle mientras se examina un objeto
* "PROXIMIDAD": En bucle mientras un visor está cerca de un objeto
* "APUNTANDO": En bucle mientras un usuario señala a un objeto

### <a name="saving-and-exporting"></a>Guardar y exportar
Una vez realizados los cambios en el modelo glTF, puede guardarlos directamente como glTF o puede hacer clic con el botón derecho en el nombre del archivo en el editor y seleccionar "glTF: Exportar a GLB (archivo binario) "en su lugar, exporte a. glb. 

### <a name="restrictions"></a>Restricciones
Las animaciones no pueden tener más de 20 minutos y no pueden contener más de 36.000 fotogramas clave (20 minutos a 30 FPS). Además, cuando se usan animaciones basadas en destino de transformación, no se superan los 8192 vértices de destino de transformación o menos. Si se supera este número, se hacerrá el recurso animado para que no se admita en la Página principal de Windows Mixed Reality. 

|Característica|Máximo|
|-----|-----|
|Duration|20 minutos|
|Fotogramas clave|36,000| 
|Vértices de destino de transformación|8192|

## <a name="gltf-implementation-notes"></a>Notas sobre la implementación de glTF
El MR de Windows no admite la volteo de geometría mediante escalas negativas. La geometría con escalas negativas probablemente producirá artefactos visuales.

El recurso glTF debe apuntar a la escena predeterminada con el atributo Scene que va a representar Windows MR. Además, el cargador de glTF de Windows MR anterior a la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md) **requiere** descriptores de acceso:
* Debe tener valores min y Max.
* El tipo ESCALAr debe ser componentType UNSIGNED_SHORT (5123) o UNSIGNED_INT (5125).
* El tipo VEC2 y VEC3 deben ser componentType FLOAT (5126).

Las siguientes propiedades de material se utilizan desde la especificación Core glTF 2,0, pero no son necesarias:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: Debe apuntar a una textura almacenada en DDS.
* emissiveTexture: Debe apuntar a una textura almacenada en DDS.
* emissiveFactor
* alphaMode

Las siguientes propiedades de material se omiten de la especificación principal:
* Todos los UVs
* metalRoughnessTexture: En su lugar, debe usar el empaquetado de textura optimizado de Microsoft definido a continuación
* normalTexture: En su lugar, debe usar el empaquetado de textura optimizado de Microsoft definido a continuación
* normalScale
* occlusionTexture: En su lugar, debe usar el empaquetado de textura optimizado de Microsoft definido a continuación
* occlusionStrength

Windows MR no admite líneas y puntos de modo primitivo. 

Solo se admite un atributo de vértice UV.

## <a name="additional-resources"></a>Recursos adicionales
* [glTF exportadores y convertidores](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [Kit de herramientas de glTF](https://github.com/Microsoft/glTF-Toolkit)
* [Especificación de glTF 2,0](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Especificación de la extensión LOD de Microsoft glTF](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Especificación de extensiones de empaquetado de textura de realidad mixta de PC](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [Especificación de extensiones de empaquetado de textura de realidad mixta de HoloLens](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Especificación de extensiones de Microsoft DDS Textures glTF](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Vea también

* [Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)](implementing-3d-app-launchers.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
