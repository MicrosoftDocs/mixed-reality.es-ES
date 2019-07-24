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
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="ed9eb-104">Guardar y buscar archivos</span><span class="sxs-lookup"><span data-stu-id="ed9eb-104">Saving and finding your files</span></span>

<span data-ttu-id="ed9eb-105">Los archivos se pueden guardar y administrar de forma similar a otros dispositivos móviles y de escritorio de Windows 10:</span><span class="sxs-lookup"><span data-stu-id="ed9eb-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="ed9eb-106">Uso de la aplicación explorador de archivos para acceder a las carpetas locales</span><span class="sxs-lookup"><span data-stu-id="ed9eb-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="ed9eb-107">Dentro de un almacenamiento propio de la aplicación</span><span class="sxs-lookup"><span data-stu-id="ed9eb-107">Within an app's own storage</span></span>
* <span data-ttu-id="ed9eb-108">En una carpeta especial conocida (como la biblioteca de vídeos o música)</span><span class="sxs-lookup"><span data-stu-id="ed9eb-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="ed9eb-109">Usar un servicio de almacenamiento que incluya una aplicación y un selector de archivos (por ejemplo, OneDrive)</span><span class="sxs-lookup"><span data-stu-id="ed9eb-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="ed9eb-110">Uso de un equipo de escritorio conectado a HoloLens a través de USB a través de la compatibilidad con MTP (Protocolo de transferencia multimedia)</span><span class="sxs-lookup"><span data-stu-id="ed9eb-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="ed9eb-111">Explorador de archivos</span><span class="sxs-lookup"><span data-stu-id="ed9eb-111">File Explorer</span></span>

<span data-ttu-id="ed9eb-112">Puede usar la aplicación explorador de archivos para trasladar y eliminar archivos desde HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="ed9eb-113">Si no ve ningún archivo en el explorador de archivos, el filtro "reciente" puede estar activo (el icono de reloj está resaltado en el panel izquierdo).</span><span class="sxs-lookup"><span data-stu-id="ed9eb-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="ed9eb-114">Para corregir esto, seleccione el icono de este documento de **dispositivo** en el panel izquierdo (debajo del icono de reloj) o abra el menú y seleccione **este dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="ed9eb-115">Archivos dentro de una aplicación</span><span class="sxs-lookup"><span data-stu-id="ed9eb-115">Files within an app</span></span>

<span data-ttu-id="ed9eb-116">Si una aplicación guarda archivos en el dispositivo, puede usar esa aplicación para tener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="ed9eb-117">¿Dónde están mis fotos o vídeos?</span><span class="sxs-lookup"><span data-stu-id="ed9eb-117">Where are my photos/videos?</span></span>

<span data-ttu-id="ed9eb-118">Las fotografías y los vídeos de [captura de realidad mixta](mixed-reality-capture.md) se guardan en la carpeta de rollo de cámara del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="ed9eb-119">Se puede acceder a ellos a través de la [aplicación fotos](see-your-photos.md#photos-app).</span><span class="sxs-lookup"><span data-stu-id="ed9eb-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="ed9eb-120">Puede usar la aplicación fotos para sincronizar sus fotos y vídeos en OneDrive.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="ed9eb-121">También puede acceder a sus fotos y vídeos a través de la página de captura de realidad mixta del [portal de dispositivos de Windows](using-the-windows-device-portal.md#mixed-reality-capture).</span><span class="sxs-lookup"><span data-stu-id="ed9eb-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="ed9eb-122">Solicitar archivos de otra aplicación</span><span class="sxs-lookup"><span data-stu-id="ed9eb-122">Requesting files from another app</span></span>

<span data-ttu-id="ed9eb-123">Una aplicación puede solicitar guardar un archivo o abrir un archivo desde otra aplicación a través de los selectores de [archivos](app-model.md#file-pickers).</span><span class="sxs-lookup"><span data-stu-id="ed9eb-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="ed9eb-124">Carpetas conocidas</span><span class="sxs-lookup"><span data-stu-id="ed9eb-124">Known folders</span></span>

<span data-ttu-id="ed9eb-125">HoloLens es compatible con una serie de [carpetas conocidas a las que las](app-model.md#known-folders) aplicaciones pueden solicitar permiso de acceso.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="ed9eb-126">Archivos en un servicio</span><span class="sxs-lookup"><span data-stu-id="ed9eb-126">Files in a service</span></span>

<span data-ttu-id="ed9eb-127">Para guardar un archivo en un servicio (o acceder a los archivos desde él), se debe instalar la aplicación asociada con el servicio.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="ed9eb-128">Para guardar archivos y obtener acceso a los archivos desde OneDrive, deberá instalar la [aplicación onedrive](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span><span class="sxs-lookup"><span data-stu-id="ed9eb-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="ed9eb-129">MTP (Protocolo de transferencia multimedia)</span><span class="sxs-lookup"><span data-stu-id="ed9eb-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="ed9eb-130">Similar a otros dispositivos móviles, conecte HoloLens al equipo de escritorio y abra el explorador de archivos en el equipo para acceder a las bibliotecas de HoloLens (fotos, vídeos, documentos) para facilitar la transferencia.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="ed9eb-131">Aclaraciones</span><span class="sxs-lookup"><span data-stu-id="ed9eb-131">Clarifications</span></span>

* <span data-ttu-id="ed9eb-132">HoloLens no admite la conexión a unidades de disco duro externas o tarjetas SD.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="ed9eb-133">A partir de la [actualización 2018 de abril de Windows 10 (RS4) para HoloLens](release-notes-april-2018.md), hololens incluye el explorador de archivos para guardar y administrar archivos en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="ed9eb-134">La adición del explorador de archivos también le permite elegir el selector de archivos (por ejemplo, guardar un archivo en el dispositivo o en OneDrive).</span><span class="sxs-lookup"><span data-stu-id="ed9eb-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
