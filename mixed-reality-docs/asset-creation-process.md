---
title: Proceso de creación de recursos
description: Instrucciones para crear recursos para experiencias de realidad mixta.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: activo, creación, proceso, presupuesto, polígonos, texturas, sombreadores, rendimiento
ms.openlocfilehash: f7bee55249764af37453ea0fab01730b43907569
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896508"
---
# <a name="asset-creation-process"></a>Proceso de creación de recursos

Windows Mixed Reality se basa en las décadas de inversión que Microsoft ha realizado en DirectX. Esto significa que toda la experiencia y los conocimientos que tienen los desarrolladores con la creación de gráficos 3D continúan siendo valiosos con HoloLens.

Los recursos que se crean para un proyecto de tienen muchas formas y formularios. Pueden estar formados por una serie de texturas e imágenes, audio, vídeo, modelos 3D y animaciones. No podemos empezar a cubrir todas las herramientas que están disponibles para crear los diferentes tipos de recursos que se usan en un proyecto. En este artículo, nos centraremos en los métodos de creación de recursos 3D.

![Concepto, creación, integración e flujo de iteración](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Concepto, creación, integración e flujo de iteración*

## <a name="things-to-consider"></a>Cosas a tener en cuenta

Al examinar la experiencia que está intentando crear, piense en ella como un **presupuesto** que puede gastar para intentar crear la mejor experiencia. No hay necesariamente límites estrictos en cuanto al número de polígonos o **tipos de materiales** que se usan en los recursos, sino más un conjunto presupuestado de contrapartidas.

A continuación se muestra un presupuesto de ejemplo para su experiencia. Por lo general, el rendimiento no es un punto único de error, sino una muerte de mil cortes por cada se.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Circula</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memoria</th>
</tr><tr>
<td> Polígonos</td><td> 0,1</td><td> 5 %</td><td> 10 %</td>
</tr><tr>
<td> Texturas</td><td> 5 %</td><td> 4,5</td><td>25%</td>
</tr><tr>
<td> Sombreadores</td><td> 4,5</td><td> 35 %</td><td> 0,1</td>
</tr><tr>
<td> <b>Dinámica</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Efectos</td><td> 5 %</td><td> 4,5</td><td> 0,1</td>
</tr><tr>
<td> Iluminación en tiempo real</td><td> 10 %</td><td> 0,1</td><td> 0,1</td>
</tr><tr>
<td> Medios (audio y vídeo)</td><td> -</td><td> 4,5</td><td> 25%</td>
</tr><tr>
<td> Script o lógica</td><td> 25%</td><td> 0,1</td><td> 5 %</td>
</tr><tr>
<td> Sobrecarga general</td><td> 5 %</td><td> 5 %</td><td> 5 %</td>
</tr><tr>
<td> <b>Total</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Número total de activos**
* ¿Cuántos activos están activos en la escena?

**Complejidad de los recursos**
* ¿Cuántos triángulos/polígonos?
* ¿Qué complejidad tiene el sombreador? Cuando se usa el kit de herramientas de la realidad mixta, se recomienda usar el sombreador de la opción de [conjunto de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) para reducir la complejidad del sombreador.

Tanto los desarrolladores como los artistas tienen que tener en cuenta las capacidades del dispositivo y el motor de gráficos. Microsoft HoloLens tiene todo el cálculo y los gráficos integrados en el dispositivo. Comparte las funcionalidades que los desarrolladores encontrarán en una plataforma móvil.

El proceso de creación de activos es el mismo, independientemente de si el destino es una experiencia para un [dispositivo Holographic o un dispositivo envolvente](mixed-reality.md#the-mixed-reality-spectrum). Lo principal que hay que tener en cuenta es la capacidad del dispositivo, tal y como se mencionó anteriormente, ya que puede ver el mundo real en una realidad mixta, por lo que querrá mantener la escala correcta en función de la experiencia. 

## <a name="authoring-assets"></a>Creación de recursos

Comenzaremos con las formas de obtener recursos para el proyecto:
1. Crear recursos (herramientas de creación y captura de objetos)
2. Compra de recursos (compra de activos en línea)
3. Traslado de recursos (tomando activos existentes)
4. Recursos de Outsourcing (importación de recursos de terceros)

### <a name="creating-assets"></a>Crear recursos

**Herramientas de creación**<br>
En primer lugar, puede crear sus propios recursos de varias maneras diferentes. los artistas 3D usan varias aplicaciones y herramientas para crear modelos que se componen de **mallas**, **texturas**y **materiales**. A continuación, se guarda en un formato de archivo que se puede importar o usar mediante el motor de gráficos que usa la aplicación, como **. FBX** o **. OBJ**. Cualquier herramienta que genere un modelo compatible con el motor de gráficos elegido funcionará en **HoloLens**. Entre los artistas 3D, muchos optan por usar [Maya de Autodesk, que es capaz de usar HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar el modo en que se crean los recursos. Si desea obtener algo rápidamente, también puede usar el [generador 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) incluido en Windows para exportar. OBJ para su uso en la aplicación.

**Captura de objeto**<br>
También hay la opción de capturar objetos en 3D. La captura de objetos inanimados en 3D y su edición con el software de creación de contenido digital es cada vez más popular con el aumento de la impresión en 3D. Con el sensor de **Kinect 2** y el [generador 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) , puede usar la característica de captura para crear recursos a partir de objetos del mundo real. Esto también es un [conjunto de herramientas](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) para hacer lo mismo con **Photogrammetry** mediante el procesamiento de una serie de imágenes que se unen y la malla y las texturas.

### <a name="purchasing-assets"></a>Recursos de compra

Otra opción excelente es adquirir recursos para su experiencia. Hay una gran cantidad de recursos disponibles a través de servicios como el [almacén de recursos de Unity](https://www.assetstore.unity3d.com/) o [TurboSquid](http://www.turbosquid.com/) entre otros.

Cuando compre recursos de un tercero, siempre querrá comprobar lo siguiente:
* **¿Cuál es el número de poli?**
  * ¿Encaja en el presupuesto?
* **¿Hay niveles de detalle (LODs) para el modelo?**
  * El nivel de detalle de un modelo le permite escalar los detalles de un modelo para el rendimiento.
* **¿Está disponible el archivo de origen?**
  * Normalmente no se incluye con el [almacén de recursos de Unity](https://www.assetstore.unity3d.com/) , pero siempre se incluye con servicios como [TurboSquid](http://www.turbosquid.com/).
  * Sin el archivo de origen no podrá modificar el recurso.
  * Asegúrese de que las herramientas 3D pueden importar el archivo de código fuente proporcionado.
* **Sepa lo que está obteniendo**
  * ¿Se proporcionan animaciones?
  * Asegúrese de comprobar la lista de contenido del recurso que está comprando.

### <a name="porting-assets"></a>Trasladar recursos

En algunos casos, se le entregarán recursos existentes que se compilaron originalmente para otros dispositivos y aplicaciones diferentes. En la mayoría de los casos, estos recursos se pueden convertir a formatos compatibles con el motor de gráficos que usa su aplicación.

Al migrar los recursos que se usarán en la aplicación de HoloLens, deberá hacer lo siguiente:
* **¿Se puede importar directamente o tiene que convertirse a otro formato?** Compruebe el formato que está importando con el motor de gráficos que está usando.
* **Si la conversión a un formato compatible es algo que se pierde?** A veces, los detalles se pueden perder o importar puede producir artefactos que se deben limpiar en una herramienta de creación de 3D.
* **¿Cuál es el recuento de triángulos/polígonos del recurso?** Según el presupuesto de la aplicación, puede usar [Simplygon](https://www.simplygon.com/) o herramientas similares para diezmar (de forma manual o manual) el activo original para ajustarse al presupuesto de las aplicaciones.

### <a name="outsourcing-assets"></a>Recursos de outsourcing

Otra opción para los proyectos más grandes que requieren más recursos de los que el equipo está equipada para crear es externalizar la creación de recursos. El proceso de outsourcing implica encontrar la agencia o el estudio correcto que se especializa en los recursos de outsourcing. Puede ser la opción más costosa, pero también es la más flexible en lo que se obtiene.
* **Defina claramente lo que está solicitando**
  * Proporcione tantos detalles como sea posible
  * Imágenes de concepto de Front, Side y back
  * Material gráfico de referencia que muestra recursos en contexto
  * Escala del objeto (normalmente se especifica en centímetros)
* **Proporcionar un presupuesto**
  * Intervalo de recuento de poli
  * Número de texturas
  * Tipo de sombreador (para Unity y HoloLens siempre debe tener primero como valor predeterminado los sombreadores móviles)
* **Comprender los costos**
  * ¿Cuál es la Directiva de outsourcing para las solicitudes de cambio?

El outsourcing puede funcionar muy bien en función de la escala de tiempo de los proyectos, pero requiere una mayor supervisión para garantizar que obtiene los recursos adecuados que necesita la primera vez.
