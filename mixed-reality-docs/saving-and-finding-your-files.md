---
title: Guardar y buscar archivos
description: Cómo buscar, guardar y compartir archivos en HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: Cómo, selector de archivos, archivos, fotos, vídeos, imágenes, OneDrive, almacenamiento, explorador de archivos
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524604"
---
# <a name="saving-and-finding-your-files"></a>Guardar y buscar archivos

Los archivos se pueden guardar y administrar de forma similar a otros dispositivos móviles y de escritorio de Windows 10:
* Uso de la aplicación explorador de archivos para acceder a las carpetas locales
* Dentro de un almacenamiento propio de la aplicación
* En una carpeta especial conocida (como la biblioteca de vídeos o música)
* Usar un servicio de almacenamiento que incluya una aplicación y un selector de archivos (por ejemplo, OneDrive)
* Uso de un equipo de escritorio conectado a HoloLens a través de USB a través de la compatibilidad con MTP (Protocolo de transferencia multimedia)

## <a name="file-explorer"></a>Explorador de archivos

Puede usar la aplicación explorador de archivos para trasladar y eliminar archivos desde HoloLens.

>[!NOTE]
>Si no ve ningún archivo en el explorador de archivos, el filtro "reciente" puede estar activo (el icono de reloj está resaltado en el panel izquierdo). Para corregir esto, seleccione el icono de este documento de **dispositivo** en el panel izquierdo (debajo del icono de reloj) o abra el menú y seleccione **este dispositivo**.

## <a name="files-within-an-app"></a>Archivos dentro de una aplicación

Si una aplicación guarda archivos en el dispositivo, puede usar esa aplicación para tener acceso a ellos.

### <a name="where-are-my-photosvideos"></a>¿Dónde están mis fotos o vídeos?

Las fotografías y los vídeos de [captura de realidad mixta](mixed-reality-capture.md) se guardan en la carpeta de rollo de cámara del dispositivo. Se puede acceder a ellos a través de la [aplicación fotos](see-your-photos.md#photos-app). Puede usar la aplicación fotos para sincronizar sus fotos y vídeos en OneDrive. También puede acceder a sus fotos y vídeos a través de la página de captura de realidad mixta del [portal de dispositivos de Windows](using-the-windows-device-portal.md#mixed-reality-capture).

### <a name="requesting-files-from-another-app"></a>Solicitar archivos de otra aplicación

Una aplicación puede solicitar guardar un archivo o abrir un archivo desde otra aplicación a través de los selectores de [archivos](app-model.md#file-pickers).

## <a name="known-folders"></a>Carpetas conocidas

HoloLens es compatible con una serie de [carpetas conocidas a las que las](app-model.md#known-folders) aplicaciones pueden solicitar permiso de acceso.

## <a name="files-in-a-service"></a>Archivos en un servicio

Para guardar un archivo en un servicio (o acceder a los archivos desde él), se debe instalar la aplicación asociada con el servicio. Para guardar archivos y obtener acceso a los archivos desde OneDrive, deberá instalar la [aplicación onedrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).

## <a name="mtp-media-transfer-protocol"></a>MTP (Protocolo de transferencia multimedia)

Similar a otros dispositivos móviles, conecte HoloLens al equipo de escritorio y abra el explorador de archivos en el equipo para acceder a las bibliotecas de HoloLens (fotos, vídeos, documentos) para facilitar la transferencia.

## <a name="clarifications"></a>Aclaraciones

* HoloLens no admite la conexión a unidades de disco duro externas o tarjetas SD.
* A partir de la [actualización 2018 de abril de Windows 10 (RS4) para HoloLens](release-notes-april-2018.md), hololens incluye el explorador de archivos para guardar y administrar archivos en el dispositivo. La adición del explorador de archivos también le permite elegir el selector de archivos (por ejemplo, guardar un archivo en el dispositivo o en OneDrive).
