---
title: Guardar y búsqueda de archivos
description: Cómo buscar, guardar y compartir archivos en HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: tema de procedimientos, selector de archivos, archivos, fotografías, vídeos, imágenes, OneDrive, el almacenamiento, el Explorador de archivos
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602687"
---
# <a name="saving-and-finding-your-files"></a>Guardar y búsqueda de archivos

Archivos se pueden guardar y administrar de forma similar a otros Windows 10 escritorio y dispositivos móviles:
* Mediante la aplicación de explorador de archivos para tener acceso a carpetas locales
* Dentro de un almacenamiento de la aplicación
* En una carpeta especial conocida (por ejemplo, la biblioteca de vídeos o música)
* Uso de un servicio de almacenamiento que incluye un selector de aplicación y archivo (por ejemplo, OneDrive)
* Usa un PC de escritorio conectado a su HoloLens a través de USB, a través de soporte técnico MTP (Protocolo de transferencia multimedia)

## <a name="file-explorer"></a>Explorador de archivos

Puede usar la aplicación de explorador de archivos para mover y eliminar archivos en HoloLens.

>[!NOTE]
>Si no ve los archivos en el Explorador de archivos, el filtro "Reciente" puede estar activo (el icono de reloj se resalta en el panel izquierdo). Para solucionar este problema, seleccione el **este dispositivo** documentar el icono en el panel izquierdo (debajo del icono de reloj), o abra el menú y seleccione **este dispositivo**.

## <a name="files-within-an-app"></a>Archivos dentro de una aplicación

Si una aplicación guarda los archivos en el dispositivo, puede usar esa aplicación para acceder a ellos.

### <a name="where-are-my-photosvideos"></a>¿Dónde están Mis fotos o vídeos?

[Mixto captura realidad](mixed-reality-capture.md) fotos y vídeos se guardan en la carpeta de álbum de cámara del dispositivo. Éstos son accesibles a través de la [aplicación fotos](see-your-photos.md#photos-app). Puede usar la aplicación fotos para sincronizar las fotos y vídeos en OneDrive. También puede acceder a tus fotos y vídeos a través de la página de realidad mixta de captura de la [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).

### <a name="requesting-files-from-another-app"></a>Solicitar archivos desde otra aplicación

Una aplicación puede solicitar para guardar un archivo o abrir un archivo desde otra aplicación a través de [selectores de archivos](app-model.md#file-pickers).

## <a name="known-folders"></a>Carpetas conocidas

HoloLens admite un número de [conocido carpetas](app-model.md#known-folders) que las aplicaciones pueden solicitar permiso de acceso.

## <a name="files-in-a-service"></a>Archivos en un servicio

Para guardar un archivo (o tener acceso a archivos de) un servicio, la aplicación asociada con el servicio debe estar instalado. Para guardar los archivos y tener acceso a archivos de OneDrive, deberá instalar el [aplicación OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).

## <a name="mtp-media-transfer-protocol"></a>MTP (Protocolo de transferencia multimedia)

Similar a otros dispositivos móviles, HoloLens de conectarse a su equipo de escritorio y abra el Explorador de archivos en el equipo para tener acceso a las bibliotecas de HoloLens (fotos, vídeos, documentos) para transferir fácilmente.

## <a name="clarifications"></a>Aclaraciones

* HoloLens no admiten la conexión a unidades de disco duro externas o tarjetas SD.
* Como de la [Windows 10 de abril de 2018 actualización (RS4) para HoloLens](release-notes-april-2018.md), HoloLens incluyen el Explorador de archivos para guardar y administrar archivos en el dispositivo. La adición del explorador de archivos también le ofrece la posibilidad de elegir el selector de archivos (por ejemplo, al guardar un archivo en el dispositivo o en OneDrive).
