---
title: Conocimiento de escenas
description: Introducción a las funcionalidades de comprensión de escenas para HoloLens
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensión de escenas, asignación espacial, Windows Mixed Reality, Unity
ms.openlocfilehash: 3d56f375c38b1dee6ab9eb97219a5e37fe698c63
ms.sourcegitcommit: 37816514b8fe20669c487774b86e80ec08edcadf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2020
ms.locfileid: "81003341"
---
# <a name="scene-understanding"></a>Conocimiento de escenas

La comprensión de la escena proporciona a los desarrolladores de realidad mixta una representación de entorno estructurada de alto nivel diseñada para facilitar el desarrollo de aplicaciones con conciencia del entorno. La comprensión de la escena realiza esto combinando la eficacia de los tiempos de ejecución de la realidad mixta existentes, como la [asignación espacial](spatial-mapping.md) menos precisa y los nuevos tiempos de ejecución controlados por AI. Mediante la combinación de estas tecnologías, la comprensión de escenas genera representaciones de entornos 3D que son similares a los que se han usado en marcos como Unity o ARKit/ARCore. El punto de entrada que comprende la escena comienza con un observador de escenas, al que llama su aplicación para calcular una nueva escena. En la actualidad, la tecnología es capaz de generar 3 categorías de objetos distintas pero relacionadas: mallas de entornos estancos simplificados que infieren la estructura de habitación plana sin desorden, regiones de plano para la selección de ubicación a las que llamamos cuádruples y una instantánea de la malla de [asignación espacial](spatial-mapping.md) que se alinea con los datos de cuádruples y estancos que se muestran.

![Malla de asignación espacial, superficie plana etiquetada, malla estanca](images/SUScenarios.png)

Este documento está pensado para proporcionar información general sobre el escenario y para aclarar la relación que la comprensión de escenas y la asignación espacial comparten.

## <a name="developing-with-scene-understanding"></a>Desarrollo con conocimiento de escenas

Este artículo solo sirve para introducir la escena que comprende el tiempo de ejecución y los conceptos. Si busca documentación sobre cómo desarrollar con la comprensión de escenas, puede que le interese lo siguiente:

[Información general del SDK de introducción a la escena](scene-understanding-SDK.md)

Puede descargar la aplicación de ejemplo de descripción de la escena en el sitio de GitHub de ejemplo:

[Ejemplo de información de escena](https://github.com/sceneunderstanding-microsoft/unitysample)

Si no tiene un dispositivo y desea tener acceso a escenas de ejemplo para probar la introducción de escenas, hay escenas en la carpeta de recursos de ejemplo:

[Escenas de ejemplo de la escena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Si busca detalles específicos sobre cómo desarrollar para la comprensión de escenas o detalles sobre cómo funciona la comprensión de escenas y cómo desarrollar para ello, consulte la documentación de [información general sobre el SDK de introducción](scene-understanding-SDK.md) a la escena.


### <a name="sample"></a>Ejemplo


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Conocimiento de escenas</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Escenarios de uso comunes

![ilustraciones de escenarios de uso de la asignación espacial común: selección de ubicación, oclusión, física y navegación](images/sm-concepts-1000px.png)<br>
*Escenarios comunes de uso de la asignación espacial: selección de ubicación, oclusión, física y navegación.*

<br>

Muchos de los escenarios principales para las aplicaciones compatibles con el entorno (selección de ubicación, oclusión, física, etc.) son direccionables por la asignación espacial y la comprensión de escenas, y en esta sección se resaltan estas diferencias. Una diferencia principal entre la comprensión de escenas y la asignación espacial es un equilibrio entre la precisión máxima y la latencia y la estructura y simplicidad. Si su aplicación requiere los triángulos de malla posible y de menor latencia a los que solo desea acceder, utilice la asignación espacial directamente. Si va a realizar un procesamiento de nivel superior, puede considerar la posibilidad de cambiar al modelo de comprensión de la escena, ya que debe proporcionarle un superconjunto de funcionalidad. Tenga en cuenta también que, dado que el conocimiento de escenas proporciona una instantánea de la malla de asignación espacial como parte de su representación, siempre tendrá acceso a los datos de asignación espacial más completos y precisos posibles.

En las secciones siguientes se vuelven a visitar los escenarios principales de asignación espacial en el contexto de la nueva escena que comprende el SDK.

### <a name="placement"></a>Ubicación

La comprensión de la escena proporciona nuevas construcciones diseñadas específicamente para simplificar los escenarios de colocación. Una escena puede calcular primitivas denominadas SceneQuads que describen las superficies planas en las que se pueden colocar hologramas. SceneQuads se han diseñado específicamente en torno a la selección de ubicación y describen una superficie 2D y proporcionan una API para la selección de ubicación en esa superficie. Anteriormente, al usar la malla del triángulo para realizar la selección de ubicación, se tenía que examinar todas las áreas de la cuádruple y realizar el rellenado y el procesamiento posterior de huecos para identificar buenas ubicaciones para la colocación de objetos. Esto no siempre es necesario con cuatro, ya que la escena que comprende el tiempo de ejecución es capaz de deducir las áreas de la cuádruple que no se han analizado e invalidar las áreas de la cuádruple que no forman parte de la superficie.

:::row:::
    :::column:::
       ![SceneQuads con inferencia deshabilitada, capturando áreas de colocación para regiones examinadas.](images/SUQuads.png)<br>
       **Image #1** -SceneQuads con inferencia deshabilitada, capturando áreas de colocación para regiones examinadas.
    :::column-end:::
        :::column:::
       ![cuádruples con la inferencia habilitada, la selección de ubicación ya no se limita a las áreas examinadas.](images/SUWatertight.png)<br>
        **Imagen #2** -cuádruples con inferencia habilitada, la selección de ubicación ya no se limita a las áreas examinadas.
    :::column-end:::
:::row-end:::

<br>


Si la aplicación intenta colocar hologramas 2D o 3D en estructuras rígidas de su entorno, la simplicidad y la comodidad de SceneQuads para la selección de ubicación son preferibles para calcular esta información desde la malla de [asignación espacial](spatial-mapping.md) . Para obtener más información sobre este tema, consulte la [Referencia del SDK](scene-understanding-SDK.md) de la escena.

**Nota:** Para el código de colocación heredado que depende de la malla de asignación espacial, la malla de asignación espacial se puede calcular junto con SceneQuads estableciendo el valor de EnableWorldMesh. Si la API de comprensión de escenas no satisface los requisitos de latencia de la aplicación, se recomienda seguir usando la [API de asignación espacial](spatial-mapping.md#placement).

### <a name="occlusion"></a>Oclusión

La [oclusión de asignación espacial](spatial-mapping.md#occlusion) sigue siendo la manera menos latente de capturar el estado en tiempo real del entorno. Aunque esto puede ser útil para proporcionar la oclusión en escenas muy dinámicas, es posible que desee considerar la posibilidad de realizar una comprensión de la escena por varias razones. Si usa la malla de asignación espacial generada por la comprensión de la escena, puede solicitar datos de la asignación espacial que no se almacenarán en la memoria caché local y, por lo tanto, no estarán disponibles en las API de percepción. El uso de la asignación espacial para la oclusión junto con las mallas estancas proporcionará un valor adicional, la finalización específica de la estructura de sala sin explorar.

Si sus requisitos pueden tolerar el aumento de la latencia de la comprensión de la escena, los desarrolladores de aplicaciones deben considerar la posibilidad de usar la escena para comprender la malla estanca y, presumiblemente, la malla de asignación espacial al unísono con representaciones planas. Esto proporcionaría un escenario "lo mejor de ambos mundos" en el que la oclusión estanca simplificada se casado con geometría no plana más precisa que proporciona los mapas de oclusión más realistas posibles.

### <a name="physics"></a>Efectos

La comprensión de escenas genera mallas estancos que descomponen el espacio con semántica, específicamente para abordar muchas limitaciones de la física que imponen las mallas de asignación espacial. Las estructuras estancas garantizan que siempre se alcanzan las conversiones de rayos físicos y la descomposición semántica permite una generación más sencilla de mallas de navegación para la navegación en interiores. Como se describe en la sección sobre la [oclusión](#occlusion), la creación de una escena con EnableSceneObjectMeshes y EnableWorldMesh producirá la malla más completa posible. La propiedad estanca de la malla del entorno impedirá que las pruebas de posicionamiento no se realicen en las superficies de posicionamiento y los datos de la malla garantizarán que la física interactúe con todos los objetos de la escena, y no solo con la estructura de la habitación.

### <a name="navigation"></a>Navegación

Las mallas planas descompuestas por la clase semántica son construcciones ideales para la navegación y la planificación de rutas, lo que facilita muchos de los problemas descritos en la introducción a la navegación por la [asignación espacial](spatial-mapping.md#navigation) . Los objetos SceneMesh calculados en la escena ya están descompuestos por tipo de superficie, lo que garantiza que la generación de NAV-Mesh está limitada a las superficies que se pueden recorrer. Debido a la simplicidad de la estructura del piso, la generación de la malla de navegación dinámica en motores 3D, como Unity, se pueden lograr en función de los requisitos en tiempo real.

La generación de las mallas de navegación precisas aún requiere un procesamiento posterior, es decir, las aplicaciones deben seguir proyectando occluders en el piso para asegurarse de que la navegación no pase por desorden/tablas, etc. La forma más precisa de lograrlo es proyectar los datos de malla mundial que se proporcionan si la escena se calcula con la marca EnableWorldMesh.

### <a name="visualization"></a>Visualización

Aunque se puede usar la visualización de la [asignación espacial](spatial-mapping.md#visualization) para los comentarios en tiempo real del entorno, hay muchos escenarios en los que la simplicidad de los objetos planos y estancos proporciona más rendimiento o calidad visual. Las técnicas de proyección de instantáneas y de uso de las bases que se describen mediante la asignación espacial pueden ser más agradables si se proyectan en las superficies planas que proporcionan cuádruples o la malla estanca plana. Esto es especialmente cierto en entornos o escenarios en los que el análisis previo exhaustivo no es óptimo debido al hecho de que la escena se inferirá, y los entornos completos y las suposiciones planas minimizarán los artefactos.

Además, el número total de superficies devueltas por la asignación espacial está limitado por la memoria caché espacial interna, mientras que la versión de la malla de la asignación espacial puede tener acceso a datos de asignación espacial que no están almacenados en caché. Por este motivo, la comprensión de la escena es más adecuada para capturar representaciones de malla para espacios más grandes (por ejemplo, más de una habitación) para la visualización o el procesamiento de malla adicional. La malla mundial devuelta con EnableWorldMesh tendrá un nivel de detalle coherente en todo el mundo, lo que puede dar lugar a una visualización más agradable si se representa como trama de alambres.

### <a name="see-also"></a>Consulta también

* [SDK de introducción a la escena](scene-understanding-SDK.md)
* [Asignación espacial](spatial-mapping.md)
