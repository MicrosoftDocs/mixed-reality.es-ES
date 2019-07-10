---
title: El Sr. y 313 - servicio IoT Hub de Azure
description: Complete este curso para obtener información sobre cómo implementar el servicio Azure IoT Hub en una máquina virtual con Ubuntu 16.4 y, a continuación, visualizar los datos del mensaje utilizando Microsoft HoloLens o auriculares para envolventes (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, edge, iot edge, tutorial, api, notificaciones, funciones, tablas, envolventes, hololens, vr, iot, máquina virtual, ubuntu, python
ms.openlocfilehash: 93f7dc64426360d2e02b0ee0a9b1796fc8f2b469
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694598"
---
>[!NOTE]
><span data-ttu-id="39c37-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="39c37-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="39c37-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="39c37-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="39c37-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="39c37-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="39c37-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="39c37-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="39c37-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="39c37-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="39c37-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="39c37-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="39c37-110">El Sr. y Azure 313: Servicio IoT Hub</span><span class="sxs-lookup"><span data-stu-id="39c37-110">MR and Azure 313: IoT Hub Service</span></span>

![resultado del curso](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="39c37-112">En este curso, obtendrá información sobre cómo implementar un **servicio Azure IoT Hub** en una máquina virtual ejecuta el sistema operativo Ubuntu 16.4.</span><span class="sxs-lookup"><span data-stu-id="39c37-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="39c37-113">Un **Azure Function App** , a continuación, se utilizará para recibir mensajes de la VM de Ubuntu y almacenar el resultado dentro de un **Azure Table Service**.</span><span class="sxs-lookup"><span data-stu-id="39c37-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="39c37-114">A continuación, podrá ver estos datos mediante **Power BI** en Microsoft HoloLens o envolventes auriculares (VR).</span><span class="sxs-lookup"><span data-stu-id="39c37-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="39c37-115">El contenido de este curso *es aplicable* en dispositivos de IoT Edge, aunque con el propósito de este curso, el foco estará en un entorno de máquina virtual, por lo que no es necesario el acceso a un dispositivo físico de Edge.</span><span class="sxs-lookup"><span data-stu-id="39c37-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="39c37-116">Al terminar este curso, obtendrá información sobre cómo:</span><span class="sxs-lookup"><span data-stu-id="39c37-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="39c37-117">Implementar un **módulo IoT Edge** a una máquina Virtual (Ubuntu 16 SO), que representa el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="39c37-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="39c37-118">Agregar un **modelo de Tensorflow Azure Custom Vision** para el módulo de Edge con código que analizará las imágenes almacenadas en el contenedor.</span><span class="sxs-lookup"><span data-stu-id="39c37-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="39c37-119">Configurar el módulo para enviar el mensaje de resultado del análisis a su **servicio IoT Hub**.</span><span class="sxs-lookup"><span data-stu-id="39c37-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="39c37-120">Use un **Azure Function App** para almacenar el mensaje dentro de un **Azure Table**.</span><span class="sxs-lookup"><span data-stu-id="39c37-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="39c37-121">Configurar **Power BI** para recopilar el mensaje almacenado y crear un informe.</span><span class="sxs-lookup"><span data-stu-id="39c37-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="39c37-122">Visualizar los datos de mensajes de IoT en **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="39c37-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="39c37-123">Los servicios que se va a utilizar incluyen:</span><span class="sxs-lookup"><span data-stu-id="39c37-123">The Services you will use include:</span></span>

- <span data-ttu-id="39c37-124">**Azure IoT Hub** es un servicio de Azure de Microsoft que permite a los desarrolladores a conectar, supervisar y administrar recursos de IoT.</span><span class="sxs-lookup"><span data-stu-id="39c37-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="39c37-125">Para obtener más información, visite la [ **servicio Azure IoT Hub** página](https://azure.microsoft.com/en-au/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="39c37-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="39c37-126">**Azure Container Registry** es un servicio de Azure de Microsoft que permite a los desarrolladores almacenar imágenes de contenedor, para varios tipos de contenedores.</span><span class="sxs-lookup"><span data-stu-id="39c37-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="39c37-127">Para obtener más información, visite la [ **del registro de Azure Container Service** página](https://azure.microsoft.com/en-au/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="39c37-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="39c37-128">**Azure Function App** es un servicio de Microsoft Azure, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure.</span><span class="sxs-lookup"><span data-stu-id="39c37-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="39c37-129">Esto proporciona una manera para delegar el trabajo a la nube, en lugar de la aplicación local, lo que puede tener muchas ventajas.</span><span class="sxs-lookup"><span data-stu-id="39c37-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="39c37-130">**Las funciones de Azure** admite varios lenguajes de desarrollo, incluidos C\#, F\#, Node.js, Java y PHP.</span><span class="sxs-lookup"><span data-stu-id="39c37-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="39c37-131">Para obtener más información, visite la [ **Azure Functions** página](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="39c37-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="39c37-132">**Almacenamiento de Azure: Las tablas** es una Microsoft Azure Service que permite a los desarrolladores almacenar estructurado, que no sea de SQL, los datos en la nube, lo que sea fácilmente accesible en cualquier lugar.</span><span class="sxs-lookup"><span data-stu-id="39c37-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="39c37-133">El servicio cuenta con un diseño sin esquema, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible.</span><span class="sxs-lookup"><span data-stu-id="39c37-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="39c37-134">Para obtener más información, visite la [ **Azure Tables** página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="39c37-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="39c37-135">Este curso le mostrará cómo configurar y usar el servicio IoT Hub y, a continuación, visualizar una respuesta de un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39c37-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="39c37-136">Será quien decide estos conceptos se aplican a una configuración personalizada del servicio IoT Hub, que puede que esté creando.</span><span class="sxs-lookup"><span data-stu-id="39c37-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="39c37-137">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="39c37-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="39c37-138">Curso</span><span class="sxs-lookup"><span data-stu-id="39c37-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="39c37-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="39c37-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="39c37-140"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="39c37-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="39c37-141">El Sr. y Azure 313: Servicio IoT Hub</span><span class="sxs-lookup"><span data-stu-id="39c37-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="39c37-142">✔️</span><span class="sxs-lookup"><span data-stu-id="39c37-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="39c37-143">✔️</span><span class="sxs-lookup"><span data-stu-id="39c37-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="39c37-144">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="39c37-144">Prerequisites</span></span>

<span data-ttu-id="39c37-145">Para los requisitos previos más recientes para el desarrollo con la realidad mixta, incluidos con el Microsoft HoloLens, visite la [instalar las herramientas de](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) artículo.</span><span class="sxs-lookup"><span data-stu-id="39c37-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="39c37-146">Este tutorial está diseñado para los desarrolladores con experiencia básica en Python.</span><span class="sxs-lookup"><span data-stu-id="39c37-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="39c37-147">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018).</span><span class="sxs-lookup"><span data-stu-id="39c37-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="39c37-148">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente de la que figura a continuación.</span><span class="sxs-lookup"><span data-stu-id="39c37-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="39c37-149">Se requiere el siguiente hardware y software:</span><span class="sxs-lookup"><span data-stu-id="39c37-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="39c37-150">Windows 10 Fall Creators Update (o posterior), **habilitado el modo de programador**</span><span class="sxs-lookup"><span data-stu-id="39c37-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="39c37-151">No se puede ejecutar una máquina Virtual mediante Hyper-V en Windows 10 Home Edition.</span><span class="sxs-lookup"><span data-stu-id="39c37-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="39c37-152">Windows 10 SDK (última versión)</span><span class="sxs-lookup"><span data-stu-id="39c37-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="39c37-153">A HoloLens, **habilitado el modo de programador**</span><span class="sxs-lookup"><span data-stu-id="39c37-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="39c37-154">Visual Studio 2017.15.4 (sólo se utiliza para tener acceso al explorador en la nube de Azure)</span><span class="sxs-lookup"><span data-stu-id="39c37-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="39c37-155">Acceso a Internet para Azure y para el servicio IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="39c37-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="39c37-156">Para obtener más información, siga este [vínculo a la página de servicio IoT Hub](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="39c37-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="39c37-157">Un modelo de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="39c37-157">A machine learning model.</span></span> <span data-ttu-id="39c37-158">Si no tiene sus propias listas para usar el modelo, [puede usar el modelo proporcionado con este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="39c37-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="39c37-159">**Hyper-V** software habilitado en el equipo de desarrollo de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="39c37-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="39c37-160">Una máquina Virtual con Ubuntu (16.4 o 18.4), en ejecución en el equipo de desarrollo o de forma alternativa puede usar un equipo independiente que ejecuta Linux (Ubuntu 16.4 o 18.4).</span><span class="sxs-lookup"><span data-stu-id="39c37-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="39c37-161">Puede encontrar más información sobre cómo crear una máquina virtual en Windows con Hyper-V en el ["Antes de empezar" capítulo](#before-you-start). () https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="39c37-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="39c37-162">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="39c37-162">Before you start</span></span>

1. <span data-ttu-id="39c37-163">Configurar y probar su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="39c37-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="39c37-164">Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="39c37-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="39c37-165">Es una buena idea realizar **calibración** y **optimización Sensor** cuando comienza a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar dichas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="39c37-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="39c37-166">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="39c37-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="39c37-167">Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="39c37-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="39c37-168">Configurar su **Máquina Virtual Ubuntu** mediante **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="39c37-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="39c37-169">Los siguientes recursos le ayudará con el proceso.</span><span class="sxs-lookup"><span data-stu-id="39c37-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="39c37-170">En primer lugar, siga este vínculo para [Descargue el archivo ISO (Xenial Xerus) LTS de Ubuntu 16.04.4](http://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="39c37-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="39c37-171">Seleccione el **imagen de escritorio de PC (AMD64) de 64 bits**.</span><span class="sxs-lookup"><span data-stu-id="39c37-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="39c37-172">Asegúrese de que **Hyper-V** está habilitada en el equipo de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="39c37-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="39c37-173">Puede seguir este vínculo para obtener instrucciones sobre [instalar y habilitar Hyper-V en Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="39c37-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="39c37-174">Inicie Hyper-V y crear una nueva VM de Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="39c37-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="39c37-175">Puede seguir este vínculo para ver un [guía paso a paso sobre cómo crear una máquina virtual con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="39c37-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="39c37-176">Cuando se solicita a **"Instalar un sistema operativo desde un archivo de imagen de arranque"** , seleccione el **ISO de Ubuntu** tiene descarga anterior.</span><span class="sxs-lookup"><span data-stu-id="39c37-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="39c37-177">Uso de **creación rápida de Hyper-V** no se recomienda.</span><span class="sxs-lookup"><span data-stu-id="39c37-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="39c37-178">Capítulo 1: recuperar el modelo de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="39c37-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="39c37-179">Con este curso tendrá acceso a un [pregenerado modelo Custom Vision](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) que detecta teclados y mouse a partir de imágenes.</span><span class="sxs-lookup"><span data-stu-id="39c37-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="39c37-180">Si utiliza esto, continúe con [capítulo 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="39c37-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="39c37-181">Sin embargo, puede seguir estos pasos si desea utilizar su propio modelo de visión personalizada:</span><span class="sxs-lookup"><span data-stu-id="39c37-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="39c37-182">En su **Custom Vision proyecto** vaya a la **rendimiento** ficha.</span><span class="sxs-lookup"><span data-stu-id="39c37-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="39c37-183">Debe usar el modelo un *compact* dominio, para exportar el modelo.</span><span class="sxs-lookup"><span data-stu-id="39c37-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="39c37-184">Puede cambiar el dominio de los modelos en la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="39c37-184">You can change your models domain in the settings for your project.</span></span>

    ![pestaña rendimiento](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="39c37-186">Seleccione el **iteración** que desea exportar y haga clic en **exportar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="39c37-187">Aparecerá una hoja.</span><span class="sxs-lookup"><span data-stu-id="39c37-187">A blade will appear.</span></span>

    ![hoja de exportación](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="39c37-189">En la hoja, haga clic en **Docker archivo**.</span><span class="sxs-lookup"><span data-stu-id="39c37-189">In the blade click **Docker File**.</span></span>

    ![Seleccione docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="39c37-191">Haga clic en **Linux** en el menú desplegable y, a continuación, haga clic en **descargar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Haga clic en descargar](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="39c37-193">Descomprima el contenido.</span><span class="sxs-lookup"><span data-stu-id="39c37-193">Unzip the content.</span></span> <span data-ttu-id="39c37-194">La usará más adelante en este curso.</span><span class="sxs-lookup"><span data-stu-id="39c37-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="39c37-195">Capítulo 2: el servicio de registro de contenedor</span><span class="sxs-lookup"><span data-stu-id="39c37-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="39c37-196">El **servicio de registro de contenedor** es el repositorio que se utiliza para hospedar los contenedores.</span><span class="sxs-lookup"><span data-stu-id="39c37-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="39c37-197">El **servicio IoT Hub** que va a crear y usar en este curso, se refiere a **servicio de registro de contenedor** para obtener los contenedores para implementar en el dispositivo de Edge.</span><span class="sxs-lookup"><span data-stu-id="39c37-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="39c37-198">En primer lugar, siga este [vínculo al Portal de Azure](https://portal.azure.com/)e inicie sesión con sus credenciales.</span><span class="sxs-lookup"><span data-stu-id="39c37-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="39c37-199">Vaya a **crear un recurso** y busque **Container Registry**.</span><span class="sxs-lookup"><span data-stu-id="39c37-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![registro de contenedor](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="39c37-201">Haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="39c37-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="39c37-202">Establecer el servicio de los parámetros de instalación:</span><span class="sxs-lookup"><span data-stu-id="39c37-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="39c37-203">Insertar un nombre para el proyecto, en este ejemplo se llama **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="39c37-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="39c37-204">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="39c37-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="39c37-205">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionamiento y administrar, de facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="39c37-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="39c37-206">Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="39c37-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="39c37-207">Establezca la ubicación del servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="39c37-208">Establecer **usuario Admin** a **habilitar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="39c37-209">Establecer **SKU** a **básica**.</span><span class="sxs-lookup"><span data-stu-id="39c37-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="39c37-210">Haga clic en **crear** y espere a que los servicios que se va a crearse.</span><span class="sxs-lookup"><span data-stu-id="39c37-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="39c37-211">Una vez que la notificación emergente que le informa de la creación correcta de la *Container Registry*, haga clic en **ir al recurso** se redirijan a la página del servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="39c37-212">En el *Container Registry* página de servicios, haga clic en **claves de acceso**.</span><span class="sxs-lookup"><span data-stu-id="39c37-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="39c37-213">Tenga en cuenta (podría usar el Bloc de notas) de los parámetros siguientes:</span><span class="sxs-lookup"><span data-stu-id="39c37-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="39c37-214">**Servidor de inicio de sesión**</span><span class="sxs-lookup"><span data-stu-id="39c37-214">**Login Server**</span></span>
    2. <span data-ttu-id="39c37-215">**Nombre de usuario**</span><span class="sxs-lookup"><span data-stu-id="39c37-215">**Username**</span></span>
    3. <span data-ttu-id="39c37-216">**Contraseña**</span><span class="sxs-lookup"><span data-stu-id="39c37-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="39c37-217">Capítulo 3: el servicio IoT Hub</span><span class="sxs-lookup"><span data-stu-id="39c37-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="39c37-218">Ahora se iniciará la creación y configuración de su **servicio IoT Hub**.</span><span class="sxs-lookup"><span data-stu-id="39c37-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="39c37-219">Si no ha iniciado sesión, inicie sesión en el [Portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="39c37-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="39c37-220">Una vez iniciada la sesión, haga clic en **crear un recurso** en la esquina superior izquierda esquina y busque **IoT Hub**y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="39c37-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Busque la cuenta de almacenamiento](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="39c37-222">La nueva página proporcionará una descripción de la **cuenta de almacenamiento** Service.</span><span class="sxs-lookup"><span data-stu-id="39c37-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="39c37-223">En la parte inferior izquierda de este símbolo del sistema, haga clic en el **crear** botón para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="39c37-225">Una vez que ha hecho clic **crear**, aparecerá un panel:</span><span class="sxs-lookup"><span data-stu-id="39c37-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="39c37-226">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="39c37-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="39c37-227">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="39c37-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="39c37-228">Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="39c37-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="39c37-229">Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="39c37-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="39c37-230">Seleccione un **ubicación** (usar la misma ubicación para todos los servicios que cree en este curso).</span><span class="sxs-lookup"><span data-stu-id="39c37-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="39c37-231">Insertar el elemento **nombre** para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="39c37-232">En la parte inferior de la página, haga clic en **siguiente: Tamaño y escala**.</span><span class="sxs-lookup"><span data-stu-id="39c37-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="39c37-234">En esta página, seleccione su **nivel de precios y escala** (si se trata de la primera instancia de servicio IoT Hub, un nivel gratuito debe estar disponible para usted).</span><span class="sxs-lookup"><span data-stu-id="39c37-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="39c37-235">Haga clic en **revisar y crear**.</span><span class="sxs-lookup"><span data-stu-id="39c37-235">Click on **Review + Create**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="39c37-237">Revise la configuración y haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="39c37-237">Review your settings and click on **Create**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="39c37-239">Una vez que la notificación emergente que le informa de la creación correcta de la *IoT Hub* servicio, haga clic en **ir al recurso** se redirijan a la página del servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="39c37-241">Desplácese al panel lateral de la izquierda hasta que vea *administración automática de dispositivos*, haga clic en **IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="39c37-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="39c37-243">En la ventana que aparece a la derecha, haga clic en **Agregar dispositivo de IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="39c37-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="39c37-244">Aparecerá una hoja a la derecha.</span><span class="sxs-lookup"><span data-stu-id="39c37-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="39c37-245">En la hoja, proporcione el nuevo dispositivo un **Id. de dispositivo** (un nombre de su elección).</span><span class="sxs-lookup"><span data-stu-id="39c37-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="39c37-246">A continuación, haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-246">Then, click **Save**.</span></span> <span data-ttu-id="39c37-247">El *principal* y *claves secundarias* automática generará, si tiene **Autogenerar** activada.</span><span class="sxs-lookup"><span data-stu-id="39c37-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="39c37-249">Se desplazará hasta el *dispositivos de IoT Edge* sección, donde se mostrará el nuevo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39c37-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="39c37-250">Haga clic en el nuevo dispositivo (destacados en rojo en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="39c37-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="39c37-252">En el *detalles del dispositivo* página que aparece, realice una copia de la **cadena de conexión** (clave principal).</span><span class="sxs-lookup"><span data-stu-id="39c37-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="39c37-254">Vuelva al panel de la izquierda y haga clic en *directivas de acceso compartido*, para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="39c37-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="39c37-255">En la página que aparece, haga clic en **iothubowner**, y aparecerá una hoja a la derecha de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="39c37-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="39c37-256">Tome nota (en el Bloc de notas) de la **cadena de conexión** (clave principal), para su uso posterior cuando se establece la *cadena de conexión* al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39c37-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="39c37-258">Capítulo 4: configurar el entorno de desarrollo</span><span class="sxs-lookup"><span data-stu-id="39c37-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="39c37-259">Para crear e implementar los módulos para *centro de IoT Edge*, necesita los siguientes componentes instalados en el equipo de desarrollo que ejecutan Windows 10:</span><span class="sxs-lookup"><span data-stu-id="39c37-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="39c37-260">[Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), le pedirá que cree una cuenta para poder descargar.</span><span class="sxs-lookup"><span data-stu-id="39c37-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="39c37-261">[![descarga de docker para windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="39c37-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="39c37-262">Requiere docker *Windows 10 PRO*, *Enterprise 14393*, o *Windows Server 2016 RTM*, para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="39c37-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="39c37-263">Si está ejecutando otras versiones de Windows 10, puede intentar instalar Docker mediante el [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="39c37-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="39c37-264">[Python 3.6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="39c37-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="39c37-265">[![Descargar python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="39c37-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="39c37-266">[Código de Visual Studio (también conocido como VS Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="39c37-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="39c37-267">[![Descargar VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="39c37-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="39c37-268">Después de instalar el software que se mencionó anteriormente, deberá reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="39c37-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="39c37-269">Capítulo 5: configurar el entorno de Ubuntu</span><span class="sxs-lookup"><span data-stu-id="39c37-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="39c37-270">Ahora puede pasar a la configuración del dispositivo **con el sistema operativo Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="39c37-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="39c37-271">Siga los pasos siguientes para instalar el software necesario para implementar los contenedores en el panel:</span><span class="sxs-lookup"><span data-stu-id="39c37-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39c37-272">Siempre debe preceder a los comandos de terminales por **sudo** para ejecutarse como usuario administrador.</span><span class="sxs-lookup"><span data-stu-id="39c37-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="39c37-273">i.e:</span><span class="sxs-lookup"><span data-stu-id="39c37-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="39c37-274">Abra el **Ubuntu Terminal**y use el siguiente comando para instalar **pip**:</span><span class="sxs-lookup"><span data-stu-id="39c37-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [!Sugerencia]<span data-ttu-id="39c37-275"> puede abrir *Terminal* muy fácilmente a través del uso el método abreviado de teclado: **Ctrl + Alt + T**.</span><span class="sxs-lookup"><span data-stu-id="39c37-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="39c37-276">A lo largo de este capítulo, se le pedirá, por *Terminal*, permiso usar el almacenamiento del dispositivo y para que escriba **y/n** (Sí o no), tipo **'y'** y, a continuación, presione el **ENTRAR** clave, para Aceptar.</span><span class="sxs-lookup"><span data-stu-id="39c37-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="39c37-277">Una vez que se haya completado ese comando, use el siguiente comando para instalar **curl**:</span><span class="sxs-lookup"><span data-stu-id="39c37-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="39c37-278">Una vez **pip** y **curl** están instaladas, use el siguiente comando para instalar el **en tiempo de ejecución de IoT Edge**, esto es necesario para implementar y los módulos en el panel de control:</span><span class="sxs-lookup"><span data-stu-id="39c37-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="39c37-279">En este momento se le indicará que abrirán la *archivo de configuración en tiempo de ejecución*, para insertar el **Device Connection String**, que ha anotado (en el Bloc de notas), al crear el **servicio IoT Hub**  ([en el paso 14, del capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="39c37-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="39c37-280">Ejecute la siguiente línea en el terminal para abrir el archivo:</span><span class="sxs-lookup"><span data-stu-id="39c37-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="39c37-281">El **config.yaml** archivo será mostrado, listo para editar:</span><span class="sxs-lookup"><span data-stu-id="39c37-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="39c37-282">Cuando se abre este archivo, puede ser un poco confusa.</span><span class="sxs-lookup"><span data-stu-id="39c37-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="39c37-283">Puede editar este archivo, dentro del texto del *Terminal* propio.</span><span class="sxs-lookup"><span data-stu-id="39c37-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="39c37-284">Use las teclas de flecha del teclado para desplazarse hacia abajo (deberá desplazarse un poco hacia abajo), para llegar a la línea que contiene ":</span><span class="sxs-lookup"><span data-stu-id="39c37-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="39c37-285">" **\<AGREGUE AQUÍ LA CADENA DE CONEXIÓN DE DISPOSITIVO >** ".</span><span class="sxs-lookup"><span data-stu-id="39c37-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="39c37-286">Sustituya la línea, **incluidos los corchetes**, con el **Device Connection String** haya anotado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="39c37-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="39c37-287">Con la cadena de conexión en su lugar, en el teclado, presione el **Ctrl-X** claves para guardar el archivo.</span><span class="sxs-lookup"><span data-stu-id="39c37-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="39c37-288">Se le pedirá que confirme escribiendo **Y**. A continuación, presione el **ENTRAR** clave, para confirmar.</span><span class="sxs-lookup"><span data-stu-id="39c37-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="39c37-289">Volverá a la normal *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="39c37-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="39c37-290">Una vez que estos comandos todos ejecutaron correctamente, habrá instalado el **en tiempo de ejecución de IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="39c37-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="39c37-291">Una vez inicializado, el tiempo de ejecución se iniciará en su propio cada vez que el dispositivo está encendido y se asienta en segundo plano, esperando módulos implementarse desde el **servicio IoT Hub**.</span><span class="sxs-lookup"><span data-stu-id="39c37-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="39c37-292">Ejecute la siguiente línea de comandos para inicializar el *en tiempo de ejecución de IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="39c37-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="39c37-293">Si realiza cambios en el archivo .yaml o la configuración anterior, necesitará volver a ejecutar la línea anterior de reinicio, dentro de *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="39c37-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="39c37-294">Compruebe el *en tiempo de ejecución de IoT Edge* estado ejecutando la siguiente línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="39c37-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="39c37-295">El tiempo de ejecución debe aparecer con el estado **activas (en ejecución)** en texto verde.</span><span class="sxs-lookup"><span data-stu-id="39c37-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="39c37-296">Presione el **Ctrl-C** claves, para salir de la página de estado.</span><span class="sxs-lookup"><span data-stu-id="39c37-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="39c37-297">Puede comprobar que la *en tiempo de ejecución de IoT Edge* está extrayendo los contenedores correctamente escribiendo el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="39c37-298">Debe aparecer una lista con los contenedores de dos (2).</span><span class="sxs-lookup"><span data-stu-id="39c37-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="39c37-299">Estos son los módulos predeterminados que se crean automáticamente por el servicio IoT Hub (edgeAgent y edgeHub).</span><span class="sxs-lookup"><span data-stu-id="39c37-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="39c37-300">Una vez que cree e implemente sus propios módulos, aparecen en esta lista, debajo de los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="39c37-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="39c37-301">Capítulo 6: instalar las extensiones</span><span class="sxs-lookup"><span data-stu-id="39c37-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39c37-302">Los capítulos siguientes (6-9) que se van a realizar en el equipo de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="39c37-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="39c37-303">Abra **Vscode**.</span><span class="sxs-lookup"><span data-stu-id="39c37-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="39c37-304">Haga clic en el **extensiones** botón (cuadrado) en el izquierdo barra de VS Code, para abrir el **panel extensiones**.</span><span class="sxs-lookup"><span data-stu-id="39c37-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="39c37-305">Busque e instale, las siguientes extensiones (como se muestra en la imagen siguiente):</span><span class="sxs-lookup"><span data-stu-id="39c37-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="39c37-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="39c37-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="39c37-307">El Kit de herramientas de Azure IoT</span><span class="sxs-lookup"><span data-stu-id="39c37-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="39c37-308">Docker</span><span class="sxs-lookup"><span data-stu-id="39c37-308">Docker</span></span>   

    ![Creación del contenedor](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="39c37-310">Una vez que se instalan las extensiones, cierre y vuelva a abrir VS Code.</span><span class="sxs-lookup"><span data-stu-id="39c37-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="39c37-311">Con VS Code, abra una vez más, vaya a **vista** > **terminal integrado**.</span><span class="sxs-lookup"><span data-stu-id="39c37-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="39c37-312">Ahora instalará **Cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="39c37-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="39c37-313">En el terminal, ejecute el siguiente comando de bash:</span><span class="sxs-lookup"><span data-stu-id="39c37-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Sugerencia]<span data-ttu-id="39c37-314"> Si tienes algún problema con este comando:</span><span class="sxs-lookup"><span data-stu-id="39c37-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="39c37-315">Reinicie VS Code, o el equipo.</span><span class="sxs-lookup"><span data-stu-id="39c37-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="39c37-316">Podría ser necesario cambiar el **Terminal de VS Code** a la que se ha usado para instalar Python, es decir, **Powershell** (especialmente si el entorno de Python instalado en el equipo).</span><span class="sxs-lookup"><span data-stu-id="39c37-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="39c37-317">Con el Terminal abierto, encontrará el menú desplegable en el lado derecho de la Terminal.</span><span class="sxs-lookup"><span data-stu-id="39c37-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="39c37-318">![Creación del contenedor](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="39c37-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="39c37-319">Asegúrese de que el **Python** ruta de instalación se agrega como **Variable de entorno** en su equipo.</span><span class="sxs-lookup"><span data-stu-id="39c37-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="39c37-320">Cookiecutter debe formar parte de la misma ruta de acceso de ubicación.</span><span class="sxs-lookup"><span data-stu-id="39c37-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="39c37-321">Siga esta [vínculo para obtener más información sobre las Variables de entorno](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span><span class="sxs-lookup"><span data-stu-id="39c37-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="39c37-322">Una vez **Cookiecutter** ha finalizado la instalación, debe reiniciar el equipo, por lo que **Cookiecutter** se reconoce como un comando dentro del entorno del sistema.</span><span class="sxs-lookup"><span data-stu-id="39c37-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="39c37-323">Capítulo 7: crear la solución de contenedor</span><span class="sxs-lookup"><span data-stu-id="39c37-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="39c37-324">En este momento, deberá crear el contenedor, con el módulo, se inserte en el *Container Registry*.</span><span class="sxs-lookup"><span data-stu-id="39c37-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="39c37-325">Una vez que haya insertado el contenedor, usará el *centro de IoT Edge* servicio implementarlo en el dispositivo, que se está ejecutando el *en tiempo de ejecución de IoT Edge*.</span><span class="sxs-lookup"><span data-stu-id="39c37-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="39c37-326">En VS Code, haga clic en **vista** > **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="39c37-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="39c37-327">En la paleta, buscar y ejecutar **Azure IoT Edge: Nueva solución de Iot Edge**.</span><span class="sxs-lookup"><span data-stu-id="39c37-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="39c37-328">Examinar en una ubicación donde desea crear la solución.</span><span class="sxs-lookup"><span data-stu-id="39c37-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="39c37-329">Presione el **ENTRAR** clave, para aceptar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="39c37-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="39c37-330">Asigne un nombre a la solución.</span><span class="sxs-lookup"><span data-stu-id="39c37-330">Give a name to your solution.</span></span> <span data-ttu-id="39c37-331">Presione el **ENTRAR** clave, para confirmar el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="39c37-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="39c37-332">Ahora se le pedirá elegir el marco de trabajo de la plantilla para su solución.</span><span class="sxs-lookup"><span data-stu-id="39c37-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="39c37-333">Haga clic en **módulo de Python**.</span><span class="sxs-lookup"><span data-stu-id="39c37-333">Click **Python Module**.</span></span> <span data-ttu-id="39c37-334">Presione el **ENTRAR** clave, para confirmar esta opción.</span><span class="sxs-lookup"><span data-stu-id="39c37-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="39c37-335">Asigne un nombre al módulo.</span><span class="sxs-lookup"><span data-stu-id="39c37-335">Give a name to your module.</span></span> <span data-ttu-id="39c37-336">Presione el **ENTRAR** clave, para confirmar el nombre de su módulo.</span><span class="sxs-lookup"><span data-stu-id="39c37-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="39c37-337">Asegúrese de anotar (con el Bloc de notas) el nombre del módulo, ya que se usará más adelante.</span><span class="sxs-lookup"><span data-stu-id="39c37-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="39c37-338">Observará un pregenerados *repositorio de imágenes de Docker* dirección aparecerá en la paleta.</span><span class="sxs-lookup"><span data-stu-id="39c37-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="39c37-339">Tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="39c37-339">It will look like:</span></span>

    <span data-ttu-id="39c37-340">**localhost: 5000 /, el nombre del módulo -** .</span><span class="sxs-lookup"><span data-stu-id="39c37-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="39c37-341">Eliminar **localhost: 5000**y en su lugar de insertar el *Container Registry* **servidor de inicio de sesión** dirección, que anotó al crear el **contenedor Servicio de registro** ([en el paso 8 de capítulo 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="39c37-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="39c37-342">Presione el **ENTRAR** clave, para confirmar la dirección.</span><span class="sxs-lookup"><span data-stu-id="39c37-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="39c37-343">En este momento, se creará la solución que contiene la plantilla para el módulo de Python y su estructura se mostrará en el **ficha explorar**, de VS Code, en el lado izquierdo de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="39c37-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="39c37-344">Si el **ficha explorar** es no está abierto, puede abrirlo haciendo clic en el botón de más arriba, en la barra de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="39c37-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Creación del contenedor](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="39c37-346">Es el último paso de este capítulo, haga clic en y abra el **archivo .env**, desde el **ficha explorar**y agregue su *Container Registry* **denombredeusuario** y **contraseña**.</span><span class="sxs-lookup"><span data-stu-id="39c37-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="39c37-347">Este archivo se pasa por alto por git, pero en la creación del contenedor, establecerá las credenciales para tener acceso a la **servicio de registro de contenedor**.</span><span class="sxs-lookup"><span data-stu-id="39c37-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Creación del contenedor](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="39c37-349">Capítulo 8: edición de la solución de contenedor</span><span class="sxs-lookup"><span data-stu-id="39c37-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="39c37-350">Ahora se completará la solución de contenedor, mediante la actualización de los siguientes archivos:</span><span class="sxs-lookup"><span data-stu-id="39c37-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="39c37-351">*principales<span></span>.py* script de python.</span><span class="sxs-lookup"><span data-stu-id="39c37-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="39c37-352">*requirements.txt*.</span><span class="sxs-lookup"><span data-stu-id="39c37-352">*requirements.txt*.</span></span>
- <span data-ttu-id="39c37-353">*deployment.template.json*.</span><span class="sxs-lookup"><span data-stu-id="39c37-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="39c37-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="39c37-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="39c37-355">A continuación, creará el *imágenes* carpeta, utilizada por el script de python para comprobar si las imágenes que debe coincidir con su *modelo Custom Vision*.</span><span class="sxs-lookup"><span data-stu-id="39c37-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="39c37-356">Por último, agregará el *labels.txt* archivo, para ayudar a leer el modelo y el *model.pb* archivo, que es el modelo.</span><span class="sxs-lookup"><span data-stu-id="39c37-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="39c37-357">Con VS Code abra, navegue a la carpeta de módulo y busque la secuencia de comandos denominada **principal<span></span>.py**.</span><span class="sxs-lookup"><span data-stu-id="39c37-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="39c37-358">Haga doble clic en él para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="39c37-358">Double-click to open it.</span></span>

2. <span data-ttu-id="39c37-359">Eliminar el contenido del archivo e inserte el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="39c37-360">Abra el archivo denominado **requirements.txt**y sustituya su contenido por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="39c37-361">Abra el archivo denominado **deployment.template.json**y sustituya su contenido siguiente la siguiente directriz:</span><span class="sxs-lookup"><span data-stu-id="39c37-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="39c37-362">Ya que tendrá su propia, único, estructura JSON, deberá editarlo manualmente (en lugar de copiar un ejemplo).</span><span class="sxs-lookup"><span data-stu-id="39c37-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="39c37-363">Para facilitar este proceso, utilice el debajo de la imagen como guía.</span><span class="sxs-lookup"><span data-stu-id="39c37-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="39c37-364">Las áreas que tendrá un aspecto diferentes a la suya, pero que **no debería cambiar está resaltado en amarillo**.</span><span class="sxs-lookup"><span data-stu-id="39c37-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="39c37-365">**Las secciones que deba eliminar, están resaltadas en rojo.**</span><span class="sxs-lookup"><span data-stu-id="39c37-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="39c37-366">Tenga cuidado al eliminar los corchetes correctos y también quitar las comas.</span><span class="sxs-lookup"><span data-stu-id="39c37-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Creación del contenedor](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="39c37-368">El JSON completado debería ser similar a la siguiente imagen (sin embargo, con sus diferencias únicas: *referencias de nombre de usuario/contraseña/nombre/módulo*):</span><span class="sxs-lookup"><span data-stu-id="39c37-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Creación del contenedor](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="39c37-370">Abra el archivo denominado **Dockerfile.amd64**y sustituya su contenido por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="39c37-371">Haga doble clic en la carpeta en **módulos** (tendrá el nombre que proporcionó anteriormente; en el ejemplo más abajo, lo que se denomina *pythonmodule*) y haga clic en **nueva carpeta**.</span><span class="sxs-lookup"><span data-stu-id="39c37-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="39c37-372">Nombre de la carpeta **imágenes**.</span><span class="sxs-lookup"><span data-stu-id="39c37-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="39c37-373">Dentro de la carpeta, agregue algunas imágenes con el mouse o teclado.</span><span class="sxs-lookup"><span data-stu-id="39c37-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="39c37-374">Serán las imágenes que se va a analizar el modelo de Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="39c37-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="39c37-375">Si usa su propio modelo, deberá cambiar este comportamiento para reflejar sus propios datos de modelos.</span><span class="sxs-lookup"><span data-stu-id="39c37-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="39c37-376">Ahora deberá recuperar el **labels.txt** y **model.pb** desde la carpeta de modelos anteriores descargó los archivos (o creado a partir de su propio **Custom Vision Service** ), en [capítulo 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="39c37-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="39c37-377">Una vez que los archivos, colocarlos dentro de la solución, junto con los demás archivos.</span><span class="sxs-lookup"><span data-stu-id="39c37-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="39c37-378">El resultado final debe parecerse a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-378">The final result should look like the image below:</span></span>

    ![Creación del contenedor](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="39c37-380">Capítulo 9 - paquete de la solución como un contenedor</span><span class="sxs-lookup"><span data-stu-id="39c37-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="39c37-381">Ahora está listo para "paquete" los archivos como un contenedor y los insertará en sus **Azure Container Registry**.</span><span class="sxs-lookup"><span data-stu-id="39c37-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="39c37-382">Dentro de VS Code, abra el *Terminal integrado* (**vista** > **Terminal integrado** o **Ctrl** + **\`** ) y utilice la siguiente línea para iniciar sesión en **Docker** (sustituya los valores del comando con las credenciales de su **Azure Container Registry (ACR)** ):</span><span class="sxs-lookup"><span data-stu-id="39c37-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="39c37-383">Haga doble clic en el archivo **deployment.template.json**y haga clic en **compilar solución de IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="39c37-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="39c37-384">Este proceso de compilación tarda bastante tiempo (según el dispositivo), así que Prepárese esperar.</span><span class="sxs-lookup"><span data-stu-id="39c37-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="39c37-385">Al finalizar el proceso de compilación, un **deployment.json** archivo se habrá creado dentro de una nueva carpeta denominada **config**.</span><span class="sxs-lookup"><span data-stu-id="39c37-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![Crear implementación](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="39c37-387">Abra el **paleta de comandos** nuevo y busque **Azure: Inicie sesión en**.</span><span class="sxs-lookup"><span data-stu-id="39c37-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="39c37-388">Siga las indicaciones con sus credenciales de cuenta de Azure; VS Code le proporcionará una opción para *copiar y abrir*, que se copiará el código del dispositivo en breve necesitará y abra el explorador web predeterminado.</span><span class="sxs-lookup"><span data-stu-id="39c37-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="39c37-389">Cuando se le solicite, pegue el código de dispositivo, para autenticar el equipo.</span><span class="sxs-lookup"><span data-stu-id="39c37-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![copiar y abrir](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="39c37-391">Una vez firmados en observará, en el lado inferior de la *explorar* panel una nueva sección denominada **dispositivos de Azure IoT Hub**.</span><span class="sxs-lookup"><span data-stu-id="39c37-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="39c37-392">Haga clic en esta sección para expandirlo.</span><span class="sxs-lookup"><span data-stu-id="39c37-392">Click this section to expand it.</span></span>

    ![dispositivo de Edge](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="39c37-394">Si el dispositivo no está aquí, deberá haga *dispositivos de Azure IoT Hub*y, a continuación, haga clic en **establece IoT Hub Connection String**.</span><span class="sxs-lookup"><span data-stu-id="39c37-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="39c37-395">A continuación, verá que el **paleta de comandos** (en la parte superior de VS Code), le pedirá que escriba su *cadena de conexión*.</span><span class="sxs-lookup"><span data-stu-id="39c37-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="39c37-396">Se trata de la *cadena de conexión* que anotó al final de [capítulo 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="39c37-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="39c37-397">Presione el **ENTRAR** clave, una vez que ha copiado la cadena.</span><span class="sxs-lookup"><span data-stu-id="39c37-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="39c37-398">El dispositivo debe cargar y aparecen.</span><span class="sxs-lookup"><span data-stu-id="39c37-398">Your device should load, and appear.</span></span> <span data-ttu-id="39c37-399">Haga doble clic en el nombre del dispositivo y, a continuación, haga clic en **Crear implementación para dispositivo único**.</span><span class="sxs-lookup"><span data-stu-id="39c37-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![Crear implementación](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="39c37-401">Obtendrá un *Explorador de archivos* símbolo del sistema, donde puede navegar a la **config** carpeta y, a continuación, seleccione el **deployment.json** archivo.</span><span class="sxs-lookup"><span data-stu-id="39c37-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="39c37-402">Con ese archivo seleccionado, haga clic en el **Seleccionar manifiesto de implementación de Edge** botón.</span><span class="sxs-lookup"><span data-stu-id="39c37-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![Crear implementación](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="39c37-404">En este momento ha proporcionado su **servicio IoT Hub** con el manifiesto para que pueda implementar el contenedor, como un módulo, desde su **Azure Container Registry**, eficaz implementarla en su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39c37-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="39c37-405">Para ver los mensajes enviados desde el dispositivo a IoT Hub, haga clic en nuevo en el nombre de dispositivo en el **dispositivos de Azure IoT Hub** sección la **Explorer** panel y haga clic en **iniciar supervisión Mensaje de D2C**.</span><span class="sxs-lookup"><span data-stu-id="39c37-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="39c37-406">Los mensajes enviados desde el dispositivo deben aparecer en el Terminal de VS.</span><span class="sxs-lookup"><span data-stu-id="39c37-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="39c37-407">Sea paciente, esta operación puede tardar algún tiempo.</span><span class="sxs-lookup"><span data-stu-id="39c37-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="39c37-408">Consulte el capítulo siguiente para la depuración y comprobación de si la implementación fue correcta.</span><span class="sxs-lookup"><span data-stu-id="39c37-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="39c37-409">Ahora creará una iteración de este módulo entre las imágenes en el **imágenes** carpeta y analizarlos, con cada iteración.</span><span class="sxs-lookup"><span data-stu-id="39c37-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="39c37-410">Esto es obviamente sólo una demostración de cómo obtener el modelo de aprendizaje automático básico para trabajar en un entorno de dispositivo IoT Edge.</span><span class="sxs-lookup"><span data-stu-id="39c37-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="39c37-411">Para expandir la funcionalidad de este ejemplo, podría proceder de varias maneras.</span><span class="sxs-lookup"><span data-stu-id="39c37-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="39c37-412">Una manera de estar podría incluir algo de código en el contenedor, que captura fotos desde una cámara Web que está conectado al dispositivo y guarda las imágenes en la carpeta imágenes.</span><span class="sxs-lookup"><span data-stu-id="39c37-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="39c37-413">Otra manera puede copiarse las imágenes desde el dispositivo de IoT en el contenedor.</span><span class="sxs-lookup"><span data-stu-id="39c37-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="39c37-414">Una forma práctica de hacerlo es ejecutar el comando siguiente en el dispositivo de IoT Terminal (quizás una pequeña aplicación podría hacer el trabajo, si se deseaba automatizar el proceso).</span><span class="sxs-lookup"><span data-stu-id="39c37-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="39c37-415">Para probar este comando, puede ejecutarlo manualmente desde la ubicación de la carpeta donde se almacenan los archivos:</span><span class="sxs-lookup"><span data-stu-id="39c37-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="39c37-416">Capítulo 10 - depuración el Runtime de IoT Edge</span><span class="sxs-lookup"><span data-stu-id="39c37-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="39c37-417">Los siguientes son una lista de líneas de comandos y sugerencias para ayudarle a supervisar y depurar la actividad de mensajería de la *en tiempo de ejecución de IoT Edge*, desde su **dispositivo Ubuntu ejecutando**.</span><span class="sxs-lookup"><span data-stu-id="39c37-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="39c37-418">Compruebe el *en tiempo de ejecución de IoT Edge* estado mediante la ejecución de la línea de comandos siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="39c37-419">Recuerde que debe presionar **Ctrl + C**, para finalizar la visualización del estado.</span><span class="sxs-lookup"><span data-stu-id="39c37-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="39c37-420">Enumerar los contenedores que están implementados actualmente.</span><span class="sxs-lookup"><span data-stu-id="39c37-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="39c37-421">Si el *servicio IoT Hub* ha implementado correctamente, los contenedores se mostrarán mediante la ejecución de la línea de comandos siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="39c37-422">O bien</span><span class="sxs-lookup"><span data-stu-id="39c37-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="39c37-423">El ejemplo anterior es una buena forma de comprobar si el módulo se ha implementado correctamente, tal y como aparecerá en la lista. en caso contrario, podrá **sólo** vea el *edgeHub* y *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="39c37-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="39c37-424">Para mostrar los registros de código de un contenedor, ejecute la siguiente línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="39c37-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="39c37-425">**Comandos útiles para administrar el tiempo de ejecución de IoT Edge:**</span><span class="sxs-lookup"><span data-stu-id="39c37-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="39c37-426">Para eliminar todos los contenedores en el host:</span><span class="sxs-lookup"><span data-stu-id="39c37-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="39c37-427">Para detener el *en tiempo de ejecución de IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="39c37-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="39c37-428">Capítulo 11: crear el servicio de tabla</span><span class="sxs-lookup"><span data-stu-id="39c37-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="39c37-429">Desplácese hasta el Portal de Azure, donde creará un servicio de tablas de Azure, mediante la creación de un recurso de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="39c37-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="39c37-430">Si no ha iniciado sesión, inicie sesión en el [Portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="39c37-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="39c37-431">Una vez iniciada la sesión, haga clic en **crear un recurso**, en la esquina superior izquierda esquina y busque **cuenta de almacenamiento**y presione la **ENTRAR** clave, para iniciar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="39c37-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="39c37-432">Una vez que ha aparecido, haga clic en **cuenta de almacenamiento: blob, archivo, tabla, cola** en la lista.</span><span class="sxs-lookup"><span data-stu-id="39c37-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Busque la cuenta de almacenamiento](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="39c37-434">La nueva página proporcionará una descripción de la **cuenta de almacenamiento** Service.</span><span class="sxs-lookup"><span data-stu-id="39c37-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="39c37-435">En la parte inferior izquierda de este símbolo del sistema, haga clic en el **crear** botón para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="39c37-437">Una vez que ha hecho clic **crear**, aparecerá un panel:</span><span class="sxs-lookup"><span data-stu-id="39c37-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="39c37-438">Insertar el elemento **nombre** para esta instancia de servicio (*debe estar en minúsculas*).</span><span class="sxs-lookup"><span data-stu-id="39c37-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="39c37-439">Para **modelo de implementación**, haga clic en **Administrador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="39c37-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="39c37-440">Para **tipo de cuenta**, mediante el menú desplegable, haga clic en **almacenamiento (uso general v1)** .</span><span class="sxs-lookup"><span data-stu-id="39c37-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="39c37-441">Haga clic en un adecuado **ubicación**.</span><span class="sxs-lookup"><span data-stu-id="39c37-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="39c37-442">Para el **replicación** menú desplegable, haga clic en **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="39c37-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="39c37-443">Para **rendimiento**, haga clic en **estándar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="39c37-444">Dentro de la **se requiere transferencia segura** sección, haga clic en **deshabilitado**.</span><span class="sxs-lookup"><span data-stu-id="39c37-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="39c37-445">Desde el **suscripción** menú desplegable, haga clic en una suscripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="39c37-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="39c37-446">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="39c37-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="39c37-447">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionamiento y administrar, de facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="39c37-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="39c37-448">Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="39c37-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="39c37-449">Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="39c37-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="39c37-450">Deje **redes virtuales** como **deshabilitado**, si se trata de una opción para usted.</span><span class="sxs-lookup"><span data-stu-id="39c37-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="39c37-451">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="39c37-451">Click **Create**.</span></span>

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="39c37-453">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="39c37-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="39c37-454">Una vez creada la instancia de servicio, aparecerá una notificación en el Portal.</span><span class="sxs-lookup"><span data-stu-id="39c37-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="39c37-455">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-455">Click on the notifications to explore your new Service instance.</span></span>

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="39c37-457">Haga clic en el **ir al recurso** botón en la notificación y se le dirigirá a la nueva página de información general de instancia de servicio de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="39c37-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![Ir al recurso](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="39c37-459">En la página de información general, en el lado derecho, haga clic en **tablas**.</span><span class="sxs-lookup"><span data-stu-id="39c37-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![Tablas](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="39c37-461">El panel de la derecha cambiará para mostrar el **Table Service** información, en la que deberá agregar una nueva tabla.</span><span class="sxs-lookup"><span data-stu-id="39c37-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="39c37-462">Haga clic en el **+ tabla** botón a la esquina superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="39c37-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![abrir tablas](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="39c37-464">Se mostrará una página nueva, en la que tiene que introducir un **nombre de la tabla**.</span><span class="sxs-lookup"><span data-stu-id="39c37-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="39c37-465">Este es el nombre que usará para hacer referencia a los datos en la aplicación en los capítulos posteriores (creación de Function App y Power BI).</span><span class="sxs-lookup"><span data-stu-id="39c37-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="39c37-466">Insertar **IoTMessages** como el nombre (solo puede elegir su propio, recuerde que cuando se usa más adelante en este documento) y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="39c37-467">Una vez creada la nueva tabla, podrá verlo en el **Table Service** página (en la parte inferior).</span><span class="sxs-lookup"><span data-stu-id="39c37-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="39c37-469">Ahora haga clic en **claves de acceso** y realice una copia de la **nombredecuentadealmacenamiento** y **clave** (mediante el Bloc de notas), se usará estos valores más adelante en este curso, al crear el **Aplicación de azure Function**.</span><span class="sxs-lookup"><span data-stu-id="39c37-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="39c37-471">Mediante el panel de la izquierda de nuevo, desplácese hasta la *Table Service* sección y haga clic en **tablas** (o **Examinar tablas**, en los portales más reciente) y realice una copia de la  **Dirección URL de la tabla** (mediante el Bloc de notas).</span><span class="sxs-lookup"><span data-stu-id="39c37-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="39c37-472">Usará este valor más adelante en este curso, al vincular la tabla a su **Power BI** aplicación.</span><span class="sxs-lookup"><span data-stu-id="39c37-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="39c37-474">Capítulo 12: finalización de la tabla de Azure</span><span class="sxs-lookup"><span data-stu-id="39c37-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="39c37-475">Ahora que su **Table Service** cuenta de almacenamiento ha sido el programa de instalación, es momento de agregar datos a él, que se usará para almacenar y recuperar información.</span><span class="sxs-lookup"><span data-stu-id="39c37-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="39c37-476">La edición de las tablas puede realizarse a través de **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="39c37-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="39c37-477">Abra **Visual Studio** (**no** código de Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="39c37-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="39c37-478">En el menú, haga clic en **vista** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="39c37-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Abra cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="39c37-480">El **Cloud Explorer** se abrirá como un elemento acoplado (tenga paciencia, como la carga puede tardar tiempo).</span><span class="sxs-lookup"><span data-stu-id="39c37-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="39c37-481">Si la suscripción que usó para crear su *cuentas de almacenamiento* no está visible, asegúrese de que tiene:</span><span class="sxs-lookup"><span data-stu-id="39c37-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="39c37-482">Iniciar sesión en la misma cuenta que usan para el Portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="39c37-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="39c37-483">Seleccionar la suscripción desde la página de administración de cuentas (es posible que deba aplicar un filtro de la configuración de su cuenta):</span><span class="sxs-lookup"><span data-stu-id="39c37-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![encuentra la suscripción](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="39c37-485">Se mostrarán los servicios de nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="39c37-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="39c37-486">Buscar **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de la que se va a expandir sus cuentas.</span><span class="sxs-lookup"><span data-stu-id="39c37-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Abra cuentas de almacenamiento](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="39c37-488">Una vez que se expande el recién creado **cuenta de almacenamiento** debe estar disponible.</span><span class="sxs-lookup"><span data-stu-id="39c37-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="39c37-489">Haga clic en la flecha situada a la izquierda de su almacenamiento y, a continuación, una vez que se expande, encontrar **tablas** y haga clic en la flecha situada junto a la que, para que se muestre el **tabla** que creó en el último capítulo.</span><span class="sxs-lookup"><span data-stu-id="39c37-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="39c37-490">Haga doble clic en su **tabla**.</span><span class="sxs-lookup"><span data-stu-id="39c37-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="39c37-491">La tabla se abrirá en el centro de la ventana de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39c37-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="39c37-492">Haga clic en el icono de tabla con el **+** (más) en él.</span><span class="sxs-lookup"><span data-stu-id="39c37-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Agregar nueva tabla](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="39c37-494">Se mostrará una ventana, se le pide para permitirle *Agregar entidad*.</span><span class="sxs-lookup"><span data-stu-id="39c37-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="39c37-495">Se creará una sola entidad, aunque tendrá tres propiedades.</span><span class="sxs-lookup"><span data-stu-id="39c37-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="39c37-496">Observará que *PartitionKey* y *RowKey* ya se proporcionan, ya que se usan para buscar los datos en la tabla.</span><span class="sxs-lookup"><span data-stu-id="39c37-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![clave de partición y fila](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="39c37-498">Actualice los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="39c37-498">Update the following values:</span></span>

    - <span data-ttu-id="39c37-499">Nombre: **PartitionKey**, valor: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="39c37-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="39c37-500">Nombre: **RowKey**, valor: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="39c37-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="39c37-501">A continuación, haga clic en **Agregar propiedad** (en la parte inferior izquierda de la *Agregar entidad* ventana) y agregue la siguiente propiedad:</span><span class="sxs-lookup"><span data-stu-id="39c37-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="39c37-502">**El elemento MessageContent**, como un *cadena*, deje el valor en blanco.</span><span class="sxs-lookup"><span data-stu-id="39c37-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="39c37-503">La tabla debe coincidir con el que aparece en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-503">Your table should match the one in the image below:</span></span>

    ![Agregue los valores correctos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="39c37-505">La razón por la entidad tiene el número 1 en la clave de fila, es porque puede ser conveniente agregar más de los mensajes que desee experimentar con este curso.</span><span class="sxs-lookup"><span data-stu-id="39c37-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="39c37-506">Haga clic en **Aceptar** cuando haya terminado.</span><span class="sxs-lookup"><span data-stu-id="39c37-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="39c37-507">La tabla ya está lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="39c37-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="39c37-508">Capítulo 13 - creación de una aplicación de función de Azure</span><span class="sxs-lookup"><span data-stu-id="39c37-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="39c37-509">Es el momento ahora para crear un *Azure Function App*, que será llamado por el *servicio IoT Hub* para almacenar el *IoT Edge* los mensajes de dispositivo en el **tabla** Servicio que creó en el capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="39c37-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="39c37-510">En primer lugar, deberá crear un archivo que permitirá que la función de Azure cargar las bibliotecas que necesarias.</span><span class="sxs-lookup"><span data-stu-id="39c37-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="39c37-511">Abra **el Bloc de notas** (presione el *Windows clave*y el tipo de *el Bloc de notas*).</span><span class="sxs-lookup"><span data-stu-id="39c37-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![Abra el Bloc de notas](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="39c37-513">Con el Bloc de notas abierto, inserte la siguiente estructura JSON en ella.</span><span class="sxs-lookup"><span data-stu-id="39c37-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="39c37-514">Una vez que lo haya hecho, guárdelo en el escritorio como **project.json**.</span><span class="sxs-lookup"><span data-stu-id="39c37-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="39c37-515">Este archivo define las bibliotecas que se va a usar la función.</span><span class="sxs-lookup"><span data-stu-id="39c37-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="39c37-516">Si ha usado NuGet, le resultarán familiares.</span><span class="sxs-lookup"><span data-stu-id="39c37-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="39c37-517">Es importante que la denominación es correcta. Asegúrese de que lo hace **no tienen un .txt** la extensión de archivo.</span><span class="sxs-lookup"><span data-stu-id="39c37-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="39c37-518">Consulte la referencia a continuación:</span><span class="sxs-lookup"><span data-stu-id="39c37-518">See below for reference:</span></span>
    >
    > ![Guardado de JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="39c37-520">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="39c37-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="39c37-521">Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda esquina y busque **Function App**y presione la **ENTRAR** clave para buscar.</span><span class="sxs-lookup"><span data-stu-id="39c37-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="39c37-522">Haga clic en *Function App* en los resultados, para abrir un nuevo panel.</span><span class="sxs-lookup"><span data-stu-id="39c37-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![Busque la aplicación de función](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="39c37-524">El nuevo panel ofrecerá una descripción de la **Function App** Service.</span><span class="sxs-lookup"><span data-stu-id="39c37-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="39c37-525">En la parte inferior izquierda de este panel, haga clic en el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![instancia de la aplicación de función](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="39c37-527">Una vez que ha hecho clic **crear**, rellene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="39c37-528">Para **nombre de la aplicación**, inserte el nombre deseado para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="39c37-529">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="39c37-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="39c37-530">Seleccione el plan de tarifa adecuado para usted, si ésta es la primera hora de creación de un **Function App Service**, un nivel gratuito debe estar disponible para usted.</span><span class="sxs-lookup"><span data-stu-id="39c37-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="39c37-531">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="39c37-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="39c37-532">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionamiento y administrar, de facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="39c37-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="39c37-533">Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="39c37-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="39c37-534">Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="39c37-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="39c37-535">Para **OS**, haga clic en Windows, ya que es la plataforma prevista.</span><span class="sxs-lookup"><span data-stu-id="39c37-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="39c37-536">Seleccione un **Plan de hospedaje** (este tutorial se usará un **Plan de consumo**.</span><span class="sxs-lookup"><span data-stu-id="39c37-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="39c37-537">Seleccione un **ubicación** (elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)</span><span class="sxs-lookup"><span data-stu-id="39c37-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="39c37-538">Para el **almacenamiento** sección **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.</span><span class="sxs-lookup"><span data-stu-id="39c37-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="39c37-539">No necesitará *Application Insights* en esta aplicación, por lo que no dude en dejarlo **desactivar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="39c37-540">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="39c37-540">Click **Create**.</span></span>

        ![Crear nueva instancia](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="39c37-542">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="39c37-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="39c37-543">Una vez creada la instancia de servicio, aparecerá una notificación en el Portal.</span><span class="sxs-lookup"><span data-stu-id="39c37-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![nueva notificación](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="39c37-545">Haga clic en la notificación, cuando la implementación sea correcta (finalizada).</span><span class="sxs-lookup"><span data-stu-id="39c37-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="39c37-546">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="39c37-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Ir al recurso](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="39c37-548">En el lado izquierdo del panel nuevo, haga clic en el **+** (más) situado junto a *funciones*, para crear una nueva función.</span><span class="sxs-lookup"><span data-stu-id="39c37-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Agregar nueva función](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="39c37-550">En el panel central, el **función** aparecerá la ventana de creación.</span><span class="sxs-lookup"><span data-stu-id="39c37-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="39c37-551">Desplácese más hacia abajo y haga clic en **función personalizada**.</span><span class="sxs-lookup"><span data-stu-id="39c37-551">Scroll down further, and click on **Custom function**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="39c37-553">Desplácese hacia abajo en la página siguiente, hasta que encuentre **IoT Hub (centro de eventos)** , a continuación, haga clic en él.</span><span class="sxs-lookup"><span data-stu-id="39c37-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="39c37-555">En el **IoT Hub (centro de eventos)** hoja, establezca el **lenguaje** a **C#** y, a continuación, haga clic en **nueva**.</span><span class="sxs-lookup"><span data-stu-id="39c37-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="39c37-557">En la ventana que aparece, asegúrese de que **IoT Hub** está seleccionada y el nombre de la *IoT Hub* campo se corresponde con el nombre de su *servicio IoT Hub* que tiene creado anteriormente ([en el paso 8 del capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="39c37-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="39c37-558">A continuación, haga clic en el **seleccione** botón.</span><span class="sxs-lookup"><span data-stu-id="39c37-558">Then click the **Select** button.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="39c37-560">En el **IoT Hub (centro de eventos)** hoja, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="39c37-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="39c37-562">Se le redirigirá al editor de función.</span><span class="sxs-lookup"><span data-stu-id="39c37-562">You will be redirected to the function editor.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="39c37-564">Elimine todo el código en él y reemplácelo con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c37-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="39c37-565">Cambie las siguientes variables, por lo que se correspondan con los valores adecuados (**tabla** y **almacenamiento** valores, de [paso 11 y 13, respectivamente, del capítulo 11](#chapter-11---create-table-service)), que encontrará en su **cuenta de almacenamiento**:</span><span class="sxs-lookup"><span data-stu-id="39c37-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="39c37-566">**tableName**, con el nombre de su **tabla** ubicado en su **cuenta de almacenamiento**.</span><span class="sxs-lookup"><span data-stu-id="39c37-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="39c37-567">**tableURL**, con la dirección URL de su **tabla** ubicado en su **cuenta de almacenamiento**.</span><span class="sxs-lookup"><span data-stu-id="39c37-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="39c37-568">**storageAccountName**, con el nombre del valor correspondiente con el nombre de su **cuenta de almacenamiento** nombre.</span><span class="sxs-lookup"><span data-stu-id="39c37-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="39c37-569">**storageAccountKey**, con la clave que obtuvo en el servicio de almacenamiento que ha creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="39c37-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="39c37-571">Con el código en su lugar, haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="39c37-572">A continuación, haga clic en el **\<** icono (flecha), en el lado derecho de la página.</span><span class="sxs-lookup"><span data-stu-id="39c37-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="39c37-574">Un panel se desliza en desde la derecha.</span><span class="sxs-lookup"><span data-stu-id="39c37-574">A panel will slide in from the right.</span></span> <span data-ttu-id="39c37-575">En el panel de control, haga clic en **cargar**y un *del explorador de archivos* aparecerá.</span><span class="sxs-lookup"><span data-stu-id="39c37-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="39c37-576">Vaya a y haga clic en, el **project.json** archivo que creó en **el Bloc de notas** anteriormente y, a continuación, haga clic en el **abierto** botón.</span><span class="sxs-lookup"><span data-stu-id="39c37-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="39c37-577">Este archivo define las bibliotecas que se va a usar la función.</span><span class="sxs-lookup"><span data-stu-id="39c37-577">This file defines the libraries that your function will use.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="39c37-579">Cuando se ha cargado el archivo, aparecerá en el panel de la derecha.</span><span class="sxs-lookup"><span data-stu-id="39c37-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="39c37-580">Haga clic en él se abrirá dentro la **función** editor.</span><span class="sxs-lookup"><span data-stu-id="39c37-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="39c37-581">Debe examinar **exactamente** igual que la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="39c37-581">It must look **exactly** the same as the next image.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="39c37-583">En este momento estaría muy bien probar la funcionalidad de la función para almacenar el mensaje en su *tabla*.</span><span class="sxs-lookup"><span data-stu-id="39c37-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="39c37-584">En la parte superior derecha de la ventana, haga clic en **prueba**.</span><span class="sxs-lookup"><span data-stu-id="39c37-584">On the top right side of the window, click on **Test**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="39c37-586">Insertar un mensaje en el **cuerpo de la solicitud**, como se muestra en la ilustración anterior y haga clic en **ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="39c37-587">La función se ejecutará, mostrar el estado de resultado (observará el verde **estado 202 aceptado**, más arriba la *salida* ventana, lo que significa que produjo una llamada correcta):</span><span class="sxs-lookup"><span data-stu-id="39c37-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![resultado de salida](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="39c37-589">Capítulo 14: ver los mensajes activos</span><span class="sxs-lookup"><span data-stu-id="39c37-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="39c37-590">Si ahora abre Visual Studio (**no** Visual Studio Code), puede visualizar el resultado de mensaje de prueba, tal como se almacenará en el *el elemento MessageContent* área de cadena.</span><span class="sxs-lookup"><span data-stu-id="39c37-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![función personalizada](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="39c37-592">Con el servicio de tabla y la aplicación de función en su lugar, los mensajes de dispositivo Ubuntu aparecerá en su *IoTMessages* tabla.</span><span class="sxs-lookup"><span data-stu-id="39c37-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="39c37-593">Si aún no se está ejecutando, inicie de nuevo el dispositivo y podrá ver los mensajes de resultados desde el dispositivo y el módulo, dentro de la tabla, a través mediante Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="39c37-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Visualizar datos](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="39c37-595">Capítulo 15: el programa de instalación de Power BI</span><span class="sxs-lookup"><span data-stu-id="39c37-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="39c37-596">Para visualizar los datos desde el dispositivo IOT que configurará **Power BI** (versión de escritorio), para recopilar los datos desde el *tabla* servicio, que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="39c37-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="39c37-597">El *HoloLens* versión de Power BI, a continuación, usará esos datos a visualizar el resultado.</span><span class="sxs-lookup"><span data-stu-id="39c37-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="39c37-598">Abrir la Microsoft Store en Windows 10 y buscar **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="39c37-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="39c37-600">Descargar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="39c37-600">Download the application.</span></span> <span data-ttu-id="39c37-601">Una vez que haya terminado de descargarse, ábralo.</span><span class="sxs-lookup"><span data-stu-id="39c37-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="39c37-602">Inicie sesión en *Power BI* con su **cuenta de Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="39c37-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="39c37-603">Que se le redirija a un explorador para registrarse.</span><span class="sxs-lookup"><span data-stu-id="39c37-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="39c37-604">Una vez que se registre, vuelva a la aplicación de Power BI y vuelva a iniciarla.</span><span class="sxs-lookup"><span data-stu-id="39c37-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="39c37-605">Haga clic en **obtener datos** y, a continuación, haga clic en **más...** .</span><span class="sxs-lookup"><span data-stu-id="39c37-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="39c37-607">Haga clic en **Azure**, **Azure Table Storage**, a continuación, haga clic en **Connect**.</span><span class="sxs-lookup"><span data-stu-id="39c37-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="39c37-609">Se le pedirá que inserte la **URL de la tabla** que recopiló anteriormente ([en el paso 13 del capítulo 11](#chapter-11---create-table-service)), al crear el servicio tabla.</span><span class="sxs-lookup"><span data-stu-id="39c37-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="39c37-610">Después de insertar la dirección URL, elimine la parte de la ruta de acceso que hace referencia a la tabla "subcarpeta" (que era IoTMessages, en este curso).</span><span class="sxs-lookup"><span data-stu-id="39c37-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="39c37-611">El resultado final debe ser como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="39c37-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="39c37-612">A continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="39c37-614">Se le pedirá que inserte la **clave de almacenamiento** que anotó ([en el paso 11 del capítulo 11](#chapter-11---create-table-service)) anteriores al crear el almacenamiento de tabla.</span><span class="sxs-lookup"><span data-stu-id="39c37-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="39c37-615">A continuación, haga clic en **Connect**.</span><span class="sxs-lookup"><span data-stu-id="39c37-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="39c37-617">Un **Panel navegador** se mostrará, marque la casilla situada junto a la tabla y haga clic en **carga**.</span><span class="sxs-lookup"><span data-stu-id="39c37-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="39c37-619">La tabla ya se ha cargado en Power BI, pero requiere una consulta para mostrar los valores en él.</span><span class="sxs-lookup"><span data-stu-id="39c37-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="39c37-620">Para ello, haga doble clic en el nombre de tabla que se encuentra en la **panel campos** en el lado derecho de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="39c37-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="39c37-621">A continuación, haga clic en **Editar consulta**.</span><span class="sxs-lookup"><span data-stu-id="39c37-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="39c37-623">Un **Editor de Power Query** abrirá una nueva ventana, se muestra la tabla.</span><span class="sxs-lookup"><span data-stu-id="39c37-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="39c37-624">Haga clic en la palabra **registro** dentro de la *contenido* columna de la tabla, para visualizar el contenido almacenado.</span><span class="sxs-lookup"><span data-stu-id="39c37-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="39c37-626">Haga clic en **en la tabla**, en la parte superior izquierda de la ventana.</span><span class="sxs-lookup"><span data-stu-id="39c37-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="39c37-628">Haga clic en **cerrar y aplicar**.</span><span class="sxs-lookup"><span data-stu-id="39c37-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="39c37-630">Una vez finalizada la carga dentro de la consulta, el **panel campos**, en el lado derecho de la pantalla, marque las casillas correspondientes a los parámetros **nombre** y **valor**a visualizar el **el elemento MessageContent** contenido de la columna.</span><span class="sxs-lookup"><span data-stu-id="39c37-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="39c37-632">Haga clic en el **icono de disco azul** en la parte superior izquierda de la ventana para guardar el trabajo en una carpeta de su elección.</span><span class="sxs-lookup"><span data-stu-id="39c37-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="39c37-634">Ahora puede hacer clic en el botón Publicar para cargar la tabla en el área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="39c37-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="39c37-635">Cuando se le solicite, haga clic en **mi área de trabajo** y haga clic en *seleccione*.</span><span class="sxs-lookup"><span data-stu-id="39c37-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="39c37-636">Espere a que se muestre el resultado del envío correcto.</span><span class="sxs-lookup"><span data-stu-id="39c37-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="39c37-639">El capítulo siguiente es específica de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="39c37-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="39c37-640">Power BI no está actualmente disponible como una aplicación envolvente, sin embargo, puede ejecutar la versión de escritorio en el Portal de realidad mixta de Windows (también conocido como Cliff House), a través de la aplicación de escritorio.</span><span class="sxs-lookup"><span data-stu-id="39c37-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="39c37-641">Capítulo 16: datos de visualización de Power BI en HoloLens</span><span class="sxs-lookup"><span data-stu-id="39c37-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="39c37-642">En su HoloLens, inicie sesión en el **Microsoft Store**, al pulsar el icono correspondiente en la lista de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="39c37-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="39c37-644">Busque y, a continuación, descargue el **Power BI** aplicación.</span><span class="sxs-lookup"><span data-stu-id="39c37-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="39c37-646">Iniciar **Power BI** desde la lista de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="39c37-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="39c37-647">**Power BI** podría pedirle que inicie sesión en su **cuenta de Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="39c37-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="39c37-648">Una vez dentro de la aplicación, el área de trabajo debe mostrar de forma predeterminada como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="39c37-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="39c37-649">Si no ocurre, simplemente haga clic en el icono del área de trabajo en el lado izquierdo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="39c37-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="39c37-651">Su terminado la aplicación de IoT Hub</span><span class="sxs-lookup"><span data-stu-id="39c37-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="39c37-652">Enhorabuena, ha creado correctamente un servicio IoT Hub, con un dispositivo simulado de borde de la máquina Virtual.</span><span class="sxs-lookup"><span data-stu-id="39c37-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="39c37-653">El dispositivo puede comunicarse los resultados de un modelo de machine learning a un servicio de tabla de Azure, que facilita una Azure Function App, que se leen en Power BI y se visualizan dentro de un Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="39c37-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="39c37-655">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="39c37-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="39c37-656">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="39c37-656">Exercise 1</span></span>

<span data-ttu-id="39c37-657">Expanda la estructura de mensajería que se almacena en la tabla y lo muestra como un gráfico.</span><span class="sxs-lookup"><span data-stu-id="39c37-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="39c37-658">Es posible que desee recopilar más datos y almacenarla en la misma tabla, que se mostrará más adelante.</span><span class="sxs-lookup"><span data-stu-id="39c37-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="39c37-659">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="39c37-659">Exercise 2</span></span>

<span data-ttu-id="39c37-660">Crear una más "captura de cámara" módulo va a implementar en el panel de IoT, por lo que pueden capturar imágenes a través de la cámara para analizarlos.</span><span class="sxs-lookup"><span data-stu-id="39c37-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
