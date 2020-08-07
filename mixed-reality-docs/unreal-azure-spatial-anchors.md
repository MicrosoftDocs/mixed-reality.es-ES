---
title: Azure Spatial Anchors en Unreal
description: Información general sobre la creación de Azure Spatial Anchors en Unreal Engine.
author: hferrone
services: azure-spatial-anchors
ms.author: v-haferr
ms.date: 07/01/2020
ms.topic: tutorial
ms.service: azure-spatial-anchors
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, desarrollo de azure, anclajes espaciales, realidad mixta, desarrollo, características, nuevo proyecto, emulador, documentación, guías, hologramas, desarrollo de juegos
ms.openlocfilehash: c7189407bea4b38e7305f0dda7637b82d3325704
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377350"
---
# <a name="azure-spatial-anchors-in-unreal"></a>Azure Spatial Anchors en Unreal

## <a name="overview"></a>Introducción

Azure Spatial Anchors es un servicio de Microsoft Mixed Reality, que permite que los dispositivos de realidad aumentada detecten, compartan y conserven puntos de anclaje en el mundo físico. En la documentación siguiente se proporcionan instrucciones para integrar el servicio de Azure Spatial Anchors en un proyecto de Unreal. Si busca más información, consulte el [servicio de Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).

> [!IMPORTANT]
> Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube. Si tiene pensado almacenar los anclajes localmente en un dispositivo, hay un documento de [Anclajes espaciales locales](unreal-spatial-anchors.md) que puede guiarle por el proceso. Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.

## <a name="prerequisites"></a>Requisitos previos

Para completar esta guía, asegúrese de tener:

- Instalado [Unreal versión 4.25](https://www.unrealengine.com/get-now) o posterior
- Un [proyecto de HoloLens 2](unreal-uxt-ch1.md) configurado en Unreal 
- Leída la [información general de Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview)
- Conocimientos básicos de C++ y Unreal

## <a name="getting-azure-spatial-anchors-account-info"></a>Obtención de información de cuenta de Azure Spatial Anchors

Antes de usar Azure Spatial Anchors en un proyecto, debe:
* [Crear un recurso de anclajes espaciales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) y copiar los campos de la cuenta que se enumeran a continuación. Estos valores se usan para autenticar a los usuarios con la cuenta de la aplicación:
    * **Id. de cuenta**
    * **Clave de cuenta**

Para obtener más información, consulte los documentos de [autenticación de Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp).

> [!NOTE]
> Azure Spatial Anchors en Unreal 4.25 no admite tokens de autenticación de Azure AD, pero la compatibilidad con esta funcionalidad estará disponible en una versión posterior.

## <a name="adding-azure-spatial-anchors-plugins"></a>Adición de complementos de Azure Spatial Anchors

Para habilitar los complementos de Azure Spatial Anchors en el editor de Unreal:
1. Haga clic en **Edit > Plugins** (Editar > Complementos) y busque **AzureSpatialAnchors** y **AzureSpatialAnchorsForWMR**.
2. Active la casilla **Enabled** (Habilitado) en ambos complementos para permitir el acceso a las bibliotecas de planos técnicos de Azure Spatial Anchors en la aplicación.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-01.png)

Una vez hecho esto, reinicie Unreal Editor para que los cambios de los complementos surtan efecto. El proyecto ahora está listo para usar Azure Spatial Anchors.

## <a name="starting-a-spatial-anchors-session"></a>Inicio de una sesión en Spatial Anchors
Una sesión de Azure Spatial Anchors permite que las aplicaciones cliente se comuniquen con el servicio de Azure Spatial Anchors. Deberá crear e iniciar una sesión de Azure Spatial Anchors para crear, conservar y compartir Azure Spatial Anchors:

1. Abra el plano técnico del Pawn (Peón) que está usando en la aplicación.
2. Agregue dos variables de cadena para **Account ID** (ID. de cuenta) y **Account Key** (Clave de cuenta) y, a continuación, asigne los valores correspondientes de la cuenta de Azure Spatial Anchors para autenticar la sesión.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-02.png)

Para iniciar una sesión de Azure Spatial Anchors:
1. Compruebe que se está ejecutando una **AR Session** (Sesión de AR) en la aplicación de HoloLens, ya que la sesión de Azure Spatial Anchors no puede iniciarse mientras no se esté ejecutando una sesión de AR. Si no tiene una configurada, [cree un recurso de AR Session](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).
2. Agregue el evento personalizado **Start Azure Spatial Anchors Session** (Iniciar sesión de Azure Spatial Anchors) y configúrelo como se muestra en la captura de pantalla siguiente.
    * Al crear una sesión no se inicia la sesión de forma predeterminada, lo que permite que el desarrollador configure la sesión para la autenticación en el servicio de Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. Configure la sesión de Azure Spatial Anchors para que proporcione **Account ID** (Id. de cuenta) y **Account Key** (Clave de cuenta).

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. Inicie la sesión de Azure Spatial Anchors, lo que permite a la aplicación crear y ubicar los Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-05.png)

Se recomienda limpiar los recursos de Azure Spatial Anchors en el plano técnico Event Graph (Gráfico de eventos) cuando ya no use el servicio:

1. Detenga la sesión de Azure Spatial Anchors. La sesión ya no estará en ejecución, pero sus recursos asociados seguirán existiendo en el complemento de Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. Destruya la sesión de Azure Spatial Anchors para limpiar los recursos de la sesión de Azure Spatial Anchors aún conocidos por el complemento de Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-07.png)

El plano técnico Event Graph (Gráfico de eventos) debe ser similar a la siguiente captura de pantalla:

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a>Creación de un anclaje
Un Azure Spatial Anchor representa un lugar del mundo físico en el espacio de la aplicación de realidad aumentada, que fija el contenido de la realidad aumentada a ubicaciones del mundo físico. Los Azure Spatial Anchors también se pueden compartir entre distintos usuarios. Este uso compartido permite que el contenido de la realidad aumentada dibujado en diferentes dispositivos se coloque en la misma ubicación del mundo físico. 

Para crear un nuevo Azure Spatial Anchor:
1. Compruebe que haya una sesión de Azure Spatial Anchors en ejecución. La aplicación no puede crear o conservar un Azure Spatial Anchor cuando no se está ejecutando ninguna sesión de Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. Cree u obtenga un **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** (Componente de escena) de Unreal cuya ubicación deba conservarse. 
    * En la imagen siguiente, el componente **Scene Component Needing Anchor** se usa como variable. Se necesita un componente de escena de Unreal para establecer una transformación del mundo de la aplicación para un [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) (Marca de AR) y Azure Spatial Anchor.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-10.png)

Para construir y guardar un Azure Spatial Anchor para un componente de escena de Unreal:
1. Llame al [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) (Componente de marca) para el componente de escena de Unreal y especifique la **World Transform** (Transformación de mundos) del componente de escena como la transformación de mundos que se usa para AR Pin (Marca de AR).
    * Unreal realiza un seguimiento de los puntos de AR en el espacio de la aplicación mediante AR Pins (Marcas de AR), que se usan para crear un Azure Spatial Anchor. En Unreal, una AR Pin (Marca de AR) es análoga a SpatialAnchor en HoloLens.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. Llame a **Create Cloud Anchor** (Crear anclaje de nube) con la AR Pin (Marca de AR) recién creada.
    * Create Cloud Anchor crea un Azure Spatial Anchor de forma local, pero no en el servicio de Azure Spatial Anchors. Los parámetros del Azure Spatial Anchor, como una fecha de expiración, se pueden establecer antes de crear el Azure Spatial Anchor con el servicio.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. Establezca la expiración del Azure Spatial Anchor. El parámetro Lifetime (Duración) de la función permite al desarrollador especificar en segundos cuánto tiempo debe el servicio mantener el anclaje.
    * Por ejemplo, una expiración de una semana tomaría un valor de 60 segundos x 60 minutos x 24 horas x 7 días = 604 800 segundos.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-13.png)

Después de establecer los parámetros de los anclajes, declare el anclaje como listo para guardarse. En el ejemplo siguiente, el Azure Spatial Anchor recién creado se agrega a un conjunto de Azure Spatial Anchors que debe guardarse. Este conjunto se declara como variable para el plano técnico del Pawn (Peón).

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a>Guardado de un anclaje

Después de configurar el Azure Spatial Anchor con sus parámetros, llame a **Save Cloud Anchor** (Guardar anclaje de nube). Save Cloud Anchor declara el anclaje en el servicio de Azure Spatial Anchors. Cuando la llamada a Save Cloud Anchor se realiza correctamente, el Azure Spatial Anchor está disponible para otros usuarios del servicio de Azure Spatial Anchors.  

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> Save Cloud Anchor es una función asincrónica y solo se puede llamar desde un evento de subproceso de juego, como **EventTick**. Es posible que Save Cloud Anchor no aparezca como una función de plano técnico en el plano técnico personalizado Functions (Funciones). Sin embargo, debe estar disponible en el editor de planos técnicos Event Graph (Gráfico de eventos) del Pawn (Peón).

En el ejemplo siguiente, el Azure Spatial Anchor se almacena en un conjunto durante una devolución de llamada del evento de entrada. Después, el elemento se guarda en EventTick. Se pueden necesitar varios intentos para guardar un Azure Spatial Anchor, en función de la cantidad de datos espaciales que se hayan creado en la sesión de Azure Spatial Anchors. Por eso es conveniente comprobar si la llamada de guardado se realizó correctamente.

Si el anclaje no se guarda, vuelva a agregarlo al conjunto de anclajes que todavía deben guardarse. Los EventTicks futuros intentarán guardar el anclaje hasta que se almacene correctamente en el servicio de Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-16.png)

Una vez que se guarde el anclaje, puede usar la transformación de AR Pins (Marcas de AR) como transformación de referencia para colocar contenido en la aplicación. Otros usuarios pueden detectar este anclaje y alinear el contenido de AR para diferentes dispositivos del mundo físico.

## <a name="deleting-an-anchor"></a>Eliminación de un anclaje

Puede eliminar los anclajes del servicio Azure Spatial Anchors llamando a **Delete Cloud Anchor** (Eliminar anclaje de nube).

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> Delete Cloud Anchor es una función latente y solo se puede llamar desde un evento de subproceso de juego, como EventTick. Es posible que Delete Cloud Anchor no aparezca como una función de plano técnico en el plano técnico personalizado Functions (Funciones). Sin embargo, debe estar disponible en el editor de planos técnicos Event Graph (Gráfico de eventos) del Pawn (Peón).

En el ejemplo siguiente, el anclaje está marcado para su eliminación en un evento de entrada personalizado. A continuación, se intenta la eliminación en EventTick. Si se produce un error en la eliminación del anclaje, agregue el Azure Spatial Anchor al conjunto de anclajes marcados para su eliminación y vuelva a intentarlo en EventTicks posteriores.

El plano técnico Event Graph (Gráfico de eventos) ahora debe ser similar a la siguiente captura de pantalla:

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a>Detección de anclajes preexistentes

Además de crear Azure Spatial Anchors, puede detectar anclajes creados por pares con el servicio de Azure Spatial Anchors:

1. Obtenga un identificador de Azure Spatial Anchor para el anclaje que desea detectar.
    * Se puede obtener un identificador de anclaje para un anclaje creado por el mismo dispositivo en una sesión anterior de Azure Spatial Anchors. También se puede crear y compartir mediante dispositivos del mismo nivel que interactúen con el servicio de Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. Agregue un componente **AzureSpatialAnchorsEvent** al plano técnico del Pawn (Peón).
    * Este componente le permite suscribirse a varios eventos de Azure Spatial Anchors, como los eventos a los que se llama cuando se detectan Azure Spatial Anchors.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. Suscríbase a **ASAAnchor Located Delegate** (Delegado detectado de ASAAnchor) para el componente **AzureSpatialAnchorsEvent**.
    * El delegado permite que la aplicación sepa cuándo se han encontrado nuevos anclajes asociados con la cuenta de Azure Spatial Anchors.
    * Con la devolución de llamada del evento, no se crearán de forma predeterminada AR Pins (Marcas de AR) para los Azure Spatial Anchors creados por pares mediante la sesión de Azure Spatial Anchors. Para crear una AR Pin (Marca de AR) para el Spatial Anchor de Azure detectado, los desarrolladores pueden llamar a **Create ARPin Around Azure Cloud Spatial Anchor** (Crear ARPin en función del anclaje espacial en la nube de Azure).

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-20.png)

Para buscar los Azure Spatial Anchors creados por los pares mediante el servicio de Azure Spatial Anchors, la aplicación tendrá que crear un **Azure Spatial Anchors Watcher** (Monitor de Azure Spatial Anchors):
1. Compruebe que haya una sesión de Azure Spatial Anchors en ejecución.
2. Cree un **AzureSpatialAnchorsLocateCriteria**.
    * Puede especificar varios parámetros de ubicación, como la distancia desde el usuario o la distancia desde otro anclaje.
3. Declare el identificador del Azure Spatial Anchor que desee en **AzureSpatialAnchorsLocateCritieria**.
4. Llame a **Create Watcher** (Crear monitor).

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-21.png)

Ahora, la aplicación comienza a buscar los Azure Spatial Anchors que conoce el servicio de Azure Spatial Anchors, lo que significa que los usuarios pueden localizar los Azure Spatial Anchors creados por sus pares.

Después de localizar el Azure Spatial Anchor, llame a **Stop Watcher** (Detener monitor) para detener Azure Spatial Anchors Watcher (Monitor de Azure Spatial Anchors) y limpie los recursos del monitor.

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-22.png)

El plano técnico Event Graph (Gráfico de eventos) final ahora debe ser similar a la siguiente captura de pantalla:

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-23.png)


## <a name="next-steps"></a>Pasos siguientes
* [Anclajes espaciales locales](unreal-spatial-anchors.md)
* [Documentación sobre anclajes espaciales](https://docs.microsoft.com/azure/spatial-anchors/)
* [Características de Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/#features)
* [Instrucciones sobre una experiencia de anclaje efectiva](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)