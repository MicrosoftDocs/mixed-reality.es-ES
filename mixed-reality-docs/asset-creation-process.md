---
title: Proceso de creación de activos
description: Instrucciones sobre cómo crear recursos para la experiencia de realidad mixta.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: activo, creación, proceso, presupuesto, polígonos, texturas, sombreadores, rendimiento
ms.openlocfilehash: 513a9856ac35e4229cfb7bc8bcb92d9d6a152980
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692297"
---
# <a name="asset-creation-process"></a>Proceso de creación de activos

Windows Mixed Reality se basa en las décadas de inversión, que Microsoft ha realizado en DirectX. Esto significa que todos los desarrolladores con experiencia y conocimientos tienen con la creación de 3D gráficos instrumento valioso con HoloLens.

Los recursos que cree para un proyecto vienen en muchas formas y tamaños. Puede estar formados por una serie de texturas e imágenes, audio, vídeo, animaciones y modelos 3D. No podemos comenzar a cubrir todas las herramientas que están disponibles para crear los diferentes tipos de activos que se usan en un proyecto. En este artículo nos centraremos en los métodos de creación de activos 3D.

![Flujo de concepto, la creación, la integración y la iteración](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Flujo de concepto, la creación, la integración y la iteración*

## <a name="things-to-consider"></a>Cosas a tener en cuenta

Al mirar la experiencia que está intentando crear piense en ella como una **presupuesto** que puede emplear para intentar crear la mejor experiencia. No hay límites estrictos necesariamente en el número de **polígonos** o **tipos de materiales** usar en sus activos, pero más de un conjunto presupuestado de equilibrios.

A continuación es un presupuesto de ejemplo para su experiencia. Rendimiento no suele ser un único punto de error pero muerte por mil cortes por-se.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Activos</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memoria</th>
</tr><tr>
<td> Polígonos</td><td> 0%</td><td> 5 %</td><td> 10 %</td>
</tr><tr>
<td> Texturas</td><td> 5 %</td><td> 15%</td><td>25%</td>
</tr><tr>
<td> Sombreadores</td><td> 15%</td><td> 35 %</td><td> 0%</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Física</td><td> 5 %</td><td> 15%</td><td> 0%</td>
</tr><tr>
<td> Iluminación en tiempo real</td><td> 10 %</td><td> 0%</td><td> 0%</td>
</tr><tr>
<td> Multimedia (audio/vídeo)</td><td> -</td><td> 15%</td><td> 25%</td>
</tr><tr>
<td> Lógica del script</td><td> 25%</td><td> 0%</td><td> 5 %</td>
</tr><tr>
<td> Gasto general</td><td> 5 %</td><td> 5 %</td><td> 5 %</td>
</tr><tr>
<td> <b>Total</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Número total de activos**
* ¿Cuántos recursos están activos en la escena?

**Complejidad de activos**
* ¿Cuántos triángulos o polígonos?
* ¿Quiénes es el sombreador?

Tanto los desarrolladores y artistas tienen en cuenta las capacidades del dispositivo y el motor de gráficos. Microsoft HoloLens tiene todo el cálculo y gráficos integran en el dispositivo. Comparte las capacidades de los desarrolladores se encontraría en una plataforma móvil.

El proceso de creación de recursos es el mismo independientemente de si tiene como destino una experiencia para un [holographic dispositivo o un dispositivo envolvente](mixed-reality.md#the-mixed-reality-spectrum). Lo principal que tenga en cuenta es la funcionalidad del dispositivo como se mencionó anteriormente, así como la escala, ya que puede ver el mundo real en mixed reality que desea mantener la escala correcta según la experiencia. 

## <a name="authoring-assets"></a>Creación de activos

Comenzaremos con las formas de obtener los recursos para el proyecto:
1. Creación de activos (objeto de captura y herramientas de creación)
2. Compra de activos (activos de comprar en línea)
3. Trasladar recursos (teniendo los activos existentes)
4. Subcontratación activos (importar activos de 3 partes)

### <a name="creating-assets"></a>Creación de activos

**Herramientas de creación**<br>
Primero puede crear sus propios recursos de varias maneras diferentes. 3D artistas usar un número de aplicaciones y herramientas para crear modelos que constan de **mallas**, **texturas**, y **materiales**. A continuación, se guarda en un formato de archivo que se puede importar o utilizado por el motor de gráficos que usa la aplicación, como **. FBX** o **. OBJ**. Funcionará cualquier herramienta que genera un modelo que admite el motor de gráficos seleccionado en **HoloLens**. Entre los artistas 3D, muchos optar por usar [Maya de Autodesk que a su vez es capaz de usar HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) para transformar los activos de forma se crean. Si desea obtener algo en rápida también puede usar [generador 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) que se incluye con Windows para exportar. OBJ para su uso en la aplicación.

**Captura de objeto**<br>
También es la opción para capturar objetos en 3D. Captura objetos inanimados en 3D y editarlos con software de creación de contenido digital son cada vez más popular con el aumento de impresión en 3D. Mediante el **Kinect 2** sensor y [generador 3D](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) puede usar la característica de captura para crear activos de los objetos del mundo real. Esto es también un [conjunto de herramientas de](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) hacer lo mismo con **photogrammetry** mediante el procesamiento de un número de imágenes de cuadernillo junto y malla y texturas.

### <a name="purchasing-assets"></a>Compra de activos

Otra excelente opción consiste en adquirir recursos para su experiencia. Hay una gran cantidad de recursos disponibles a través de servicios como el [Unity Asset Store](https://www.assetstore.unity3d.com/) o [TurboSquid](http://www.turbosquid.com/) entre otros.

Al adquirir los activos de una parte 3ª siempre desea comprobar lo siguiente:
* **¿Qué es el recuento de poli?**
  * ¿Ésta cabe dentro del presupuesto?
* **¿Existen niveles de detalle para el modelo?**
  * Nivel de detalle de un modelo le permiten escalar el detalle de un modelo para el rendimiento.
* **¿Está disponible el archivo de origen?**
  * Normalmente, no se incluye con [Unity Asset Store](https://www.assetstore.unity3d.com/) pero siempre se incluye con servicios como [TurboSquid](http://www.turbosquid.com/).
  * Sin el archivo de origen no podrá modificar el recurso.
  * Asegúrese de que se puede importar el archivo de origen proporcionado por las herramientas de 3D.
* **Saber lo que le esté sacando**
  * ¿Se proporcionan las animaciones?
  * Asegúrese de que se comprueba la lista de contenido del recurso que desea adquirir.

### <a name="porting-assets"></a>Activos de migración

En algunos casos deberá entregar activos existentes que se crearon originalmente para otros dispositivos y aplicaciones diferentes. En la mayoría de los casos estos activos se pueden convertir a formatos compatibles con su aplicación usa el motor de gráficos.

Al migrar activos a usar en la aplicación de HoloLens desea preguntar lo siguiente:
* **¿Puede importar directamente o deben convertirse a otro formato?** Compruebe el formato que se va a importar con el motor de gráficos que está usando.
* **¿Se pierde nada si la conversión a un formato compatible?** A veces, los detalles pueden perderse o la importación puede provocar los artefactos que deben limpiarse en una herramienta de creación de 3D.
* **¿Qué es los triángulos / polígonos recuento para el recurso?** Según el presupuesto para la aplicación puede usar [Simplygon](https://www.simplygon.com/) o herramientas similares para Aventaje (manual o mediante procedimientos reducir el número de poli) el recurso original para ajustarse a su presupuesto de aplicaciones.

### <a name="outsourcing-assets"></a>Activos de subcontratación internacional

Otra opción para los proyectos más grandes que requieren más recursos que el equipo está equipado para crear es externalizar la creación de recursos. El proceso de subcontratación implica buscar el derecho studio o la Agencia que se especializa en activos de subcontratación. Esto puede ser la opción más cara pero también ser más flexible en lo que se obtiene.
* **Definir claramente lo que se solicita**
  * Proporcione tantos detalles como sea posible
  * Frontales, laterales y back-concepto imágenes
  * Recurso de referencia material gráfico que muestra en contexto
  * Escala de objeto (normalmente se especifica en centímetros)
* **Proporcione un presupuesto**
  * Intervalo de recuento poli
  * Número de texturas
  * Tipo de sombreador (para Unity y HoloLens que siempre, de forma predeterminada los sombreadores de móviles primero)
* **Comprender los costos**
  * ¿Qué es la directiva de subcontratación internacional para las solicitudes de cambio?

Subcontratación puede funcionar muy bien en función de la escala de tiempo de proyectos, pero requiere más capacidades de supervisión para garantizar que se obtienen los activos derechos que necesita la primera vez.
