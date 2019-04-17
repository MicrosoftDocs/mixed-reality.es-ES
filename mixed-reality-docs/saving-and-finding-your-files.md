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
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="d2984-104">Guardar y búsqueda de archivos</span><span class="sxs-lookup"><span data-stu-id="d2984-104">Saving and finding your files</span></span>

<span data-ttu-id="d2984-105">Archivos se pueden guardar y administrar de forma similar a otros Windows 10 escritorio y dispositivos móviles:</span><span class="sxs-lookup"><span data-stu-id="d2984-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="d2984-106">Mediante la aplicación de explorador de archivos para tener acceso a carpetas locales</span><span class="sxs-lookup"><span data-stu-id="d2984-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="d2984-107">Dentro de un almacenamiento de la aplicación</span><span class="sxs-lookup"><span data-stu-id="d2984-107">Within an app's own storage</span></span>
* <span data-ttu-id="d2984-108">En una carpeta especial conocida (por ejemplo, la biblioteca de vídeos o música)</span><span class="sxs-lookup"><span data-stu-id="d2984-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="d2984-109">Uso de un servicio de almacenamiento que incluye un selector de aplicación y archivo (por ejemplo, OneDrive)</span><span class="sxs-lookup"><span data-stu-id="d2984-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="d2984-110">Usa un PC de escritorio conectado a su HoloLens a través de USB, a través de soporte técnico MTP (Protocolo de transferencia multimedia)</span><span class="sxs-lookup"><span data-stu-id="d2984-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="d2984-111">Explorador de archivos</span><span class="sxs-lookup"><span data-stu-id="d2984-111">File Explorer</span></span>

<span data-ttu-id="d2984-112">Puede usar la aplicación de explorador de archivos para mover y eliminar archivos en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d2984-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="d2984-113">Si no ve los archivos en el Explorador de archivos, el filtro "Reciente" puede estar activo (el icono de reloj se resalta en el panel izquierdo).</span><span class="sxs-lookup"><span data-stu-id="d2984-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="d2984-114">Para solucionar este problema, seleccione el **este dispositivo** documentar el icono en el panel izquierdo (debajo del icono de reloj), o abra el menú y seleccione **este dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="d2984-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="d2984-115">Archivos dentro de una aplicación</span><span class="sxs-lookup"><span data-stu-id="d2984-115">Files within an app</span></span>

<span data-ttu-id="d2984-116">Si una aplicación guarda los archivos en el dispositivo, puede usar esa aplicación para acceder a ellos.</span><span class="sxs-lookup"><span data-stu-id="d2984-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="d2984-117">¿Dónde están Mis fotos o vídeos?</span><span class="sxs-lookup"><span data-stu-id="d2984-117">Where are my photos/videos?</span></span>

<span data-ttu-id="d2984-118">[Mixto captura realidad](mixed-reality-capture.md) fotos y vídeos se guardan en la carpeta de álbum de cámara del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d2984-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="d2984-119">Éstos son accesibles a través de la [aplicación fotos](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="d2984-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="d2984-120">Puede usar la aplicación fotos para sincronizar las fotos y vídeos en OneDrive.</span><span class="sxs-lookup"><span data-stu-id="d2984-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="d2984-121">También puede acceder a tus fotos y vídeos a través de la página de realidad mixta de captura de la [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="d2984-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="d2984-122">Solicitar archivos desde otra aplicación</span><span class="sxs-lookup"><span data-stu-id="d2984-122">Requesting files from another app</span></span>

<span data-ttu-id="d2984-123">Una aplicación puede solicitar para guardar un archivo o abrir un archivo desde otra aplicación a través de [selectores de archivos](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="d2984-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="d2984-124">Carpetas conocidas</span><span class="sxs-lookup"><span data-stu-id="d2984-124">Known folders</span></span>

<span data-ttu-id="d2984-125">HoloLens admite un número de [conocido carpetas](app-model.md#known-folders) que las aplicaciones pueden solicitar permiso de acceso.</span><span class="sxs-lookup"><span data-stu-id="d2984-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="d2984-126">Archivos en un servicio</span><span class="sxs-lookup"><span data-stu-id="d2984-126">Files in a service</span></span>

<span data-ttu-id="d2984-127">Para guardar un archivo (o tener acceso a archivos de) un servicio, la aplicación asociada con el servicio debe estar instalado.</span><span class="sxs-lookup"><span data-stu-id="d2984-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="d2984-128">Para guardar los archivos y tener acceso a archivos de OneDrive, deberá instalar el [aplicación OneDrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="d2984-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="d2984-129">MTP (Protocolo de transferencia multimedia)</span><span class="sxs-lookup"><span data-stu-id="d2984-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="d2984-130">Similar a otros dispositivos móviles, HoloLens de conectarse a su equipo de escritorio y abra el Explorador de archivos en el equipo para tener acceso a las bibliotecas de HoloLens (fotos, vídeos, documentos) para transferir fácilmente.</span><span class="sxs-lookup"><span data-stu-id="d2984-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="d2984-131">Aclaraciones</span><span class="sxs-lookup"><span data-stu-id="d2984-131">Clarifications</span></span>

* <span data-ttu-id="d2984-132">HoloLens no admiten la conexión a unidades de disco duro externas o tarjetas SD.</span><span class="sxs-lookup"><span data-stu-id="d2984-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="d2984-133">Como de la [Windows 10 de abril de 2018 actualización (RS4) para HoloLens](release-notes-april-2018.md), HoloLens incluyen el Explorador de archivos para guardar y administrar archivos en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d2984-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="d2984-134">La adición del explorador de archivos también le ofrece la posibilidad de elegir el selector de archivos (por ejemplo, al guardar un archivo en el dispositivo o en OneDrive).</span><span class="sxs-lookup"><span data-stu-id="d2984-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
