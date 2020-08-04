---
title: 'Tutoriales de la nube de Azure: 5. Integración de Azure Bot Service con LUIS'
description: Complete este curso para aprender a implementar Azure Bot Service y el reconocimiento del lenguaje natural en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens, hololens 2, azure bot service, luis, lenguaje natural, bot de conversación
ms.localizationpriority: high
ms.openlocfilehash: daf97cde1477a84c1776a069ec5b8d1a185b63cc
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376457"
---
# <a name="5-integrating-azure-bot-service"></a>5. Integración de Azure Bot Service

En este tutorial, aprenderá a usar **Azure Bot Service** en la aplicación de demostración de **HoloLens 2** para agregar el reconocimiento del lenguaje (LUIS) y dejar que el bot ayude al usuario al buscar **objetos con seguimiento**. Este es un tutorial de dos partes en el que, en la primera parte, crea el bot con [Bot Composer](https://docs.microsoft.com/composer/introduction) como una solución sin código y echa un vistazo rápido a la función de Azure que alimenta el bot con los datos necesarios. En la segunda parte se usa **BotManager (script)** en el proyecto de Unity para consumir el servicio de bot hospedado.

## <a name="objectives"></a>Objetivos

## <a name="part-1"></a>1ª parte

* Aprender los aspectos básicos de Azure Bot Service
* Aprender a usar Bot Composer para crear un bot
* Aprender a usar una función de Azure para proporcionar datos de Azure Storage

## <a name="part-2"></a>2ª parte

* Aprender a configurar la escena para usar Azure Bot Service en este proyecto
* Aprender a establecer y encontrar objetos conversando con el bot

## <a name="understanding-azure-bot-service"></a>Descripción de Azure Bot Service

**Azure Bot Service** permite a los desarrolladores crear bots inteligentes que pueden mantener conversaciones naturales con los usuarios gracias a **LUIS**. Un bot de conversación es una excelente manera de ampliar las formas de las que un usuario puede interactuar con la aplicación. Un bot puede actuar como una base de conocimiento con [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) para mantener una conversación sofisticada con la potencia del [reconocimiento del lenguaje (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp).

Obtenga más información sobre [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).

## <a name="part-1---creating-the-bot"></a>1ª parte: creación del bot

Antes de poder usar el bot en la aplicación de Unity, debe desarrollarlo, proporcionarle datos y hospedarlo en **Azure**.
El objetivo del bot es tener las capacidades para indicar cuántos *objetos con seguimiento* se almacenan en la base de datos, buscar un *objeto con seguimiento* por su nombre y indicar al usuario información básica sobre el mismo.

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>Vista rápida de la función de Azure de objetos con seguimiento

Está a punto de empezar a crear el bot, pero para que resulte útil, debe proporcionarle un recurso del que pueda extraer datos. Dado que el *bot* podrá contar la cantidad de **objetos con seguimiento**, buscar objetos específicos por nombre e indicar detalles, usará una función de Azure sencilla que tenga acceso al **almacenamiento de tablas de Azure**.

Descargue el proyecto de la función de Azure: [Función de Azure de objetos con seguimiento](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)

Esta función de Azure tiene dos acciones, **Count** y **Find**, que se pueden invocar a través de llamadas *HTTP* *GET* básicas. Puede inspeccionar el código en **Visual Studio**.

Obtenga más información sobre [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).

La función **Count** consulta en el **almacenamiento de tablas** todos los elementos **TrackedObjects** de la tabla, es muy sencillo. Por otra parte, la función **Find** toma un parámetro de consulta *name* de la solicitud *GET* y consulta en el **almacenamiento de tablas** un elemento **TrackedObject** coincidente y devuelve un DTO como JSON.

Puede implementar esta **función de Azure** directamente desde **Visual Studio**.
Aquí encontrará toda la información relacionada con la [implementación de la función de Azure](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).

Una vez que haya completado la implementación, en el **portal de Azure**, abra el recurso correspondiente y haga clic en **Configuración**, que se encuentra en la sección *Configuración*. En **Configuración de la aplicación** debe proporcionar la *cadena de conexión* a **Azure Storage** donde se almacenan los **objetos con seguimiento**. Haga clic en **Nueva configuración de la aplicación** y use para el nombre: **AzureStorageConnectionString** y para el valor proporcione la *cadena de conexión* correcta. Después de ello, haga clic en **Guardar** y la **función de Azure** está lista para hacer funcionar el *bot* que creará a continuación.

### <a name="creating-a-conversation-bot"></a>Creación de un bot de conversación

Hay varias maneras de desarrollar un bot de conversación basado en Bot Framework. En esta lección usará la aplicación de escritorio [Bot Framework Composer](https://docs.microsoft.com/composer/), que es un diseñador visual perfecto para el desarrollo rápido.

Puede descargar las últimas versiones desde el [repositorio de GitHub](https://github.com/microsoft/BotFramework-Composer/releases). Está disponible para Windows, Mac y Linux.

Una vez que se haya instalado **Bot Framework Composer**, inicie la aplicación y debería ver esta interfaz:

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

Ha preparado un proyecto de Bot Composer que proporciona los diálogos y desencadenadores necesarios para este tutorial.
Descargue el proyecto: [Proyecto de Bot Framework Composer](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)

En la barra superior, haga clic en **Abrir** y seleccione el proyecto de Bot Framework que ha descargado, denominado **TrackedObjectsBot**. Una vez que el proyecto esté totalmente cargado, debería ver el proyecto listo.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

Vamos a centrarnos en el lado izquierdo, en el que puede ver el **panel Diálogos**. Allí hay un diálogo denominado **TrackedObjectsBot** en el que puede ver varios **desencadenadores**.

Obtenga más información acerca de los [conceptos de Bot Framework](https://docs.microsoft.com/composer/concept-dialog).

Estos desencadenadores hacen lo siguiente:

#### <a name="greeting"></a>Saludo

Este es el punto de entrada del *bot* de chat cuando un *usuario* inicia una conversación.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

Este diálogo se desencadena cuando el *usuario* pide el recuento de todos los **objetos con seguimiento**.
Estas son las frases que lo desencadenan:

>* contar todo
>* cuántos se almacenan

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

Gracias a [LUIS](https://docs.microsoft.com/composer/how-to-use-luis), el *usuario* no tiene que formular las frases de la manera exacta, lo que permite una conversación natural para el *usuario*.

En este diálogo, el *bot* también se comunicará con la función de Azure **Count**, lo que de detallará más adelante.

#### <a name="unknown-intent"></a>Intención desconocida

Este diálogo se desencadena si la entrada del *usuario* no se ajusta a ninguna otra condición desencadenadora y responde al usuario que intente de nuevo su pregunta.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

El último diálogo es más complejo, ya que contiene bifurcaciones y almacena datos en la memoria de *bots*.
Solicita al usuario el *nombre* del **objeto con seguimiento** del que quiere saber más información, realiza una consulta a la función de Azure **Find** y usa la respuesta para continuar con la conversación.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

Si no se encuentra el **objeto con seguimiento**, se informa al usuario y finaliza la conversación. Cuando se encuentra el **objeto con seguimiento** en cuestión, el bot comprobará qué propiedades están disponibles e informará sobre ellas.

### <a name="adapting-the-bot"></a>Adaptación del bot

Los desencadenadores **AskingForCount** y **FindEntity** deben comunicarse con el back-end, lo que significa que tiene que agregar la dirección URL correcta de la **función de Azure** que implementó anteriormente.

En el panel de diálogos, haga clic en **AskingForCount** y busque la acción *Enviar una solicitud HTTP*; aquí puede ver el campo **URL** que necesita para cambiar la URL correcta para el punto de conexión de la función **Count**.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

Por último, busque el desencadenador **FindEntity** y busque la acción *Enviar una solicitud HTTP*; en el campo **URL**, cambie la dirección URL por el punto de conexión de la función **Find**.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

Con todo definido, ya está listo para implementar el bot. Puesto que tiene Bot Framework Composer instalado, puede publicarlo directamente desde allí.

Obtenga más información sobre cómo [publicar un bot desde Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).

> [!TIP]
> No dude en experimentar con el bot agregando más frases desencadenadoras, nuevas respuestas o bifurcaciones de conversación.

## <a name="part-2---putting-everything-together-in-unity"></a>Parte 2: configuración de todo en Unity

### <a name="preparing-the-scene"></a>Preparación de la escena

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

Desde ahí, mueva el elemento prefabricado **ChatBotManager** a la jerarquía de la escena.

Una vez que agregue ChatBotManager a la escena, haga clic en el componente **Chat Bot Manager** (Administrador de bot de chat).
En el inspector verá que hay un campo **Direct Line Secret Key** (Clave secreta de línea directa) que debe rellenar.

> [!TIP]
> Puede recuperar la *clave secreta* del portal de Azure; para ello, busque el recurso del tipo **Registro de canales de bots** que ha creado en la primera parte de este tutorial.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

Ahora, conectará el objeto **ChatBotManager** con el componente **ChatBotController** adjunto al objeto **ChatBotPanel**. En la jerarquía, seleccione **ChatBotPanel** y verá un campo vacío **Chat Bot Manager** (Administrador de bots de chat); arrastre desde la jerarquía el objeto **ChatBotManager** al campo **Chat Bot Manager** (Administrador de bots de chat).

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

A continuación, necesita una manera de abrir **ChatBotPanel** para que el usuario pueda interactuar con él. En la ventana Scene (Escena) es posible que haya observado que hay un botón secundario *Chat bot* (Bot de chat) en el objeto **MainMenu**, que usará para resolver este problema.

En la jerarquía, busque **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** y busque en el Inspector el script *ButtonConfigHelper*. Allí verá una ranura vacía en la devolución de llamada del evento **OnClick()** . Arrastre y coloque **ChatBotPanel** en la ranura del evento, en la lista desplegable vaya a *GameObject*, seleccione en el submenú *SetActive (bool)* y active la casilla.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

Ahora el bot de chat puede iniciarse desde el menú principal, por lo que la escena está lista para su uso.

### <a name="putting-the-bot-to-a-test"></a>Puesta a prueba del bot

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>Pregunta sobre la cantidad de objetos con seguimiento

En primer lugar, realice una prueba en la que pida al bot cuántos **objetos con seguimiento** se almacenan en la base de datos.

> [!NOTE]
> Esta vez debe ejecutar la aplicación desde HoloLens 2 porque es posible que servicios como *texto a voz* no estén disponibles en el sistema.

Ejecute la aplicación en HoloLens 2 y haga clic en el botón *Bot de chat* situado junto al menú principal.
El bot le saludará. Pregunte **¿cuántos objetos tenemos?**
Debe indicarle la cantidad y finalizar la conversación.

#### <a name="asking-about-a-tracked-object"></a>Pregunta sobre un objeto con seguimiento

Vuelva a ejecutar la aplicación y, esta vez, pregunte **busca un objeto con seguimiento**; el bot le pedirá el nombre, al que debe responder con "coche" o el nombre de otro *objeto con seguimiento* que sepa que existe en la base de datos. El bot le indicará detalles como la descripción y si tiene un anclaje espacial asignado.

> [!TIP]
> Pruebe de preguntar por un **objeto con seguimiento** que no exista y escuche cómo responde el bot.

## <a name="congratulations"></a>Enhorabuena

En este tutorial ha aprendido cómo se puede usar Azure Bot Framework para interactuar con la aplicación mediante la conversación con lenguaje natural. Ha aprendido a desarrollar su propio bot y cuáles son las piezas necesarias para que funcione.

## <a name="conclusion"></a>Conclusión

A lo largo de esta serie de tutoriales, ha experimentado cómo **Azure Cloud Services** ha incorporado características nuevas y emocionantes a la aplicación.
Ahora puede almacenar datos e imágenes en la nube con **Azure Storage**, usar **Azure Custom Vision** para asociar imágenes y entrenar un modelo, incorporar objetos a un contexto local con **anclajes espaciales de Azure** e implementar **Azure Bot Framework con tecnología de LUIS** para agregar un bot de conversación para un patrón de interacción nuevo y natural.
