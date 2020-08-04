---
title: 'Tutoriales de la nube de Azure: 2. Integración de Azure Storage'
description: Complete este curso para aprender a implementar Azure Table Storage y Azure Blob Storage en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, azure storage
ms.localizationpriority: high
ms.openlocfilehash: a8d91bc55b3ce73d6e1fb46e5d696d853adcf871
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376477"
---
# <a name="2-integrating-azure-storage"></a>2. Integración de Azure Storage

En este tutorial, obtendrá información sobre cómo guardar datos de entidad en Azure Table Storage e imágenes en miniatura en Azure Blob Storage. Esta característica nos permitirá almacenar y recuperar *objetos de los que se realiza un seguimiento* con datos como el identificador, el nombre, la imagen en miniatura, etc. entre las sesiones y los dispositivos en la nube.

## <a name="objectives"></a>Objetivos

* Aprender los aspectos básicos de Azure Storage
* Aprenda a almacenar, modificar y recuperar datos de Table Storage
* Aprender a almacenar y eliminar imágenes de Blob Storage

## <a name="understanding-azure-storage"></a>Descripción de Azure Storage

**Azure Storage** es una solución de almacenamiento de Microsoft en la nube que puede abarcar muchos escenarios y requisitos. Se puede escalar de forma masiva y los desarrolladores pueden acceder a ella fácilmente. Todos los servicios se pueden consumir en el paraguas de una **cuenta de Azure Storage**. En nuestro caso de uso, usaremos *Table Storage* y *Blob Storage*.

Obtenga más información sobre los [servicios de Azure Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview).

### <a name="azure-table-storage"></a>Azure Table Storage

Estos servicios nos permiten almacenar los datos mediante un mecanismo NoSQL. En este proyecto, lo usaremos para almacenar información sobre el *objeto del que se realiza un seguimiento*, p. ej., el nombre, la descripción, el identificador del delimitador espacial, etc.

En el contexto de la aplicación de demostración, necesita dos tablas, una para almacenar información sobre el proyecto con información sobre el estado de los modelos entrenados (puede obtener más información al respecto en el tutorial [Integración de Azure Custom Vision](mr-learning-azure-03.md)) y una segunda tabla para almacenar información sobre los *objetos de los que se realiza un seguimiento*.

Obtenga más información sobre [Azure Table Storage](https://docs.microsoft.com/azure/storage/tables/table-storage-overview).

### <a name="azure-blob-storage"></a>Azure Blob Storage

Este servicio permite almacenar archivos binarios de gran tamaño. Lo usará para almacenar las fotografías tomadas para los *objetos de los que se realiza un seguimiento* como miniatura.
En el caso de la aplicación de demostración, necesita un contenedor de blobs para almacenar las imágenes.

Obtenga más información sobre [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction).

## <a name="preparing-azure-storage"></a>Preparación de Azure Storage

Para consumir los servicios de Azure Storage, necesitará una cuenta de Azure Storage. Para crear una cuenta de almacenamiento, consulte [Creación de una cuenta de almacenamiento](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal). Para obtener más información sobre las cuentas de almacenamiento, consulte [Información general de la cuenta de Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-account-overview).

Una vez que tenga una cuenta de almacenamiento, puede recuperar la cadena de conexión desde **Azure Portal** que se necesitará en la siguiente sección de esta lección.

### <a name="optional-azure-storage-explorer"></a>Explorador de Azure Storage opcional

Aunque puede ver y comprobar todos los cambios de datos de la interfaz de usuario dentro de la aplicación, le recomendamos que instale el [Explorador de Azure Storage](https://azure.microsoft.com/features/storage-explorer/). Esta herramienta le permite ver los datos en Azure Storage y resulta muy útil para la depuración y el aprendizaje.

> [!TIP]
> Para realizar pruebas desde el editor de Unity, puede usar un emulador local:

> * En Windows 10, puede usar el [emulador de Azure Storage.](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)
> * En MacOS/Linux, puede usar la [imagen de Docker de Azurite](https://hub.docker.com/_/microsoft-azure-storage-azurite) para Docker.

## <a name="preparing-the-scene"></a>Preparación de la escena

En la ventana Hierarchy (Jerarquía), busque el objeto **DataManager** y selecciónelo.

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

En la ventana Inspector verá que el componente**DataManager (script)** es el sitio donde se conservan todos los valores de configuración relacionados con **Azure Storage**. Ya se han establecido todos los valores de configuración pertinentes. Ahora, solo tiene que reemplazar el campo *Connection String* (Cadena de conexión) por el que puede recuperar en Azure Portal. Si usa una solución de emulador de Azure Storage local, puede mantener la *cadena de conexión* que ya proporcionó.

El componente **DataManager (script)** es responsable de comunicarse con **Table Storage** y **Blob Storage**, que consumen otros scripts del controlador en los componentes de la interfaz de usuario.

## <a name="writing-and-reading-data-from-azure-table-storage"></a>Escritura y lectura de datos de Azure Table Storage

Una vez esté todo preparado, es el momento de crear un *objeto del que se realizará un seguimiento*.

Abra la aplicación en HoloLens, haga clic en **Set Object** (Establecer objeto) y verá cómo el objeto *EnterObjectName* se activará en la jerarquía. En este menú, haga clic en la *barra de búsqueda* y escriba el nombre que quiera asignar al *objeto del que se realizará un seguimiento*. Después de proporcionar un nombre, haga clic en el botón **Set Object** (Establecer objeto). Se creará el *objeto del que se realizará un seguimiento* en Azure Table Storage y verá la **tarjeta del objeto**.

La **tarjeta del objeto** es una representación de la interfaz de usuario del *objeto del que se realiza el seguimiento* y tendrá un rol importante varias veces en esta serie de tutoriales.

Ahora, haga clic en el *cuadro de texto* de la descripción y escriba "Coche", después de hacer clic en el botón **Save** (Guardar) para guardar los cambios. Detenga la aplicación y vuelva a ejecutarla.

Ahora, haga clic en **Search Object** (Buscar objeto) y escriba en la *barra de búsqueda* el nombre que ha utilizado antes al crear el *objeto del que se realiza un seguimiento*. Verá que se recupera la **tarjeta del objeto** con todos los datos de **Azure Table Storage**.

No dude en cerrar la **tarjeta del objeto** y crear nuevos *objetos de los que se realice un seguimiento*, así como editar sus datos.

> [!TIP]
> Si instaló el [Explorador de Azure Storage](https://azure.microsoft.com/features/storage-explorer/), a continuación, examine la tabla de *objetos* y verá el *objeto del que se realiza un seguimiento*.

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>Carga y descarga de una imagen desde Azure Blob Storage

En esta sección, usará Azure Blob Storage para cargar y descargar imágenes que se usarán como miniaturas para los *objetos de los que se realiza un seguimiento*.

> [!NOTE]
> En este tutorial, la aplicación tomará fotos para cargar imágenes en Blob Storage. Si lo ejecuta de forma local desde el editor de Unity, asegúrese de que tiene una cámara web conectada al equipo.

Abra la aplicación en HoloLens, haga clic en **Set Object** (Establecer objeto) y escriba en la *barra de búsqueda* el nombre "Coche". Ahora debería ver la **tarjeta del objeto**. Haga clic en el botón **Camera** (Cámara) y se le indicará que realice un gesto de pulsación en el aire para tomar una foto. Después de tomar una foto, verá un mensaje en el que se le informará sobre la carga activa y, al cabo de un rato, la imagen deberá aparecer en el lugar en el que se encontraba el marcador de posición.

Ahora vuelva a ejecutar la aplicación, busque el *objeto del que se realiza un seguimiento* y la imagen cargada previamente debería aparecer como miniatura.

## <a name="deleting-image-from-azure-blob-storage"></a>Eliminación de una imagen de Azure Blob Storage.

En la sección anterior, cargó imágenes nuevas en Azure Blob Storage y, en esta, eliminará una miniatura de imagen de los *objetos de los que realiza un seguimiento*.

Abra la aplicación en HoloLens, haga clic en **Set Object** (Establecer objeto) y escriba en la *barra de búsqueda* el nombre "Coche". Ahora debería ver la **tarjeta del objeto** con la imagen en miniatura. Si es así, haga clic en el botón **Delete** (Eliminar). Observará que la imagen en miniatura se ha reemplazado por la imagen del marcador de posición.

Ahora vuelva a ejecutar la aplicación y busque el *objeto del que se realiza un seguimiento* de la miniatura previamente eliminada. Solo debería ver la imagen del marcador de posición.

## <a name="congratulations"></a>Enhorabuena

En este tutorial ha aprendido a usar los servicios de Azure Storage para conservar datos no estructurados, como los **objetos de los que realiza un seguimiento** y los archivos binarios en formato de imágenes en miniatura para la aplicación de demostración de **HoloLens 2** en la nube.

En el siguiente tutorial, aprenderá a usar Azure Custom Vision para detectar imágenes asociadas a un *objeto del que se realiza un seguimiento*.

[Tutorial siguiente: 3. Integración de Azure Custom Vision](mr-learning-azure-03.md)
