---
title: MR y Azure 313-IoT Hub servicio
description: Complete este curso para aprender a implementar Azure IoT Hub servicio en una máquina virtual que ejecuta Ubuntu 16,4 y, a continuación, visualice los datos de los mensajes mediante Microsoft HoloLens o un casco envolvente (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, realidad mixta, Academia, Edge, IOT Edge, tutorial, API, notificación, funciones, tablas, hololens, inmersivo, VR, IOT, máquina virtual, Ubuntu, Python
ms.openlocfilehash: bfb1518869892ed4899019d7b9c504a960e7db3f
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926835"
---
>[!NOTE]
><span data-ttu-id="9f5ca-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9f5ca-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9f5ca-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9f5ca-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9f5ca-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9f5ca-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="9f5ca-110">MR y Azure 313: servicio de IoT Hub</span><span class="sxs-lookup"><span data-stu-id="9f5ca-110">MR and Azure 313: IoT Hub Service</span></span>

![resultado del curso](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="9f5ca-112">En este curso, aprenderá a implementar un servicio de **Azure IOT Hub** en una máquina virtual que ejecuta el sistema operativo Ubuntu 16,4.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="9f5ca-113">A continuación, se usará una **function App de Azure** para recibir mensajes de la máquina virtual de Ubuntu y almacenar el resultado en un **servicio tabla de Azure**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="9f5ca-114">A continuación, podrá ver estos datos con **Power BI** en el casco de Microsoft HoloLens o envolvente (VR).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="9f5ca-115">El contenido de este curso *es aplicable* a los dispositivos IOT Edge, aunque para este curso, el foco estará en un entorno de máquina virtual, de modo que el acceso a un dispositivo perimetral físico no sea necesario.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="9f5ca-116">Al completar este curso, aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="9f5ca-117">Implemente un **módulo de IOT Edge** en una máquina virtual (sistema operativo Ubuntu 16), que representará el dispositivo de IOT.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="9f5ca-118">Agregue un **modelo Tensorflow de Azure Custom Vision** al módulo Edge, con código que analizará las imágenes almacenadas en el contenedor.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="9f5ca-119">Configure el módulo para enviar el mensaje de resultado del análisis de vuelta a su **servicio de IOT Hub**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="9f5ca-120">Use una **function App de Azure** para almacenar el mensaje en una **tabla de Azure**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="9f5ca-121">Configure **Power BI** para recopilar el mensaje almacenado y crear un informe.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="9f5ca-122">Visualice los datos de los mensajes de IoT en **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="9f5ca-123">Los servicios que usará incluyen:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-123">The Services you will use include:</span></span>

- <span data-ttu-id="9f5ca-124">**Azure IOT Hub** es un servicio de Microsoft Azure que permite a los desarrolladores conectarse, supervisar y administrar recursos de IOT.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="9f5ca-125">Para obtener más información, visite la [página **servicio de Azure IOT Hub** ](https://azure.microsoft.com/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/services/iot-hub/).</span></span>

- <span data-ttu-id="9f5ca-126">**Azure Container Registry** es un servicio de Microsoft Azure que permite a los desarrolladores almacenar imágenes de contenedor para varios tipos de contenedores.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="9f5ca-127">Para obtener más información, visite la [página **servicio de Azure Container Registry** ](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/services/container-registry/).</span></span>

- <span data-ttu-id="9f5ca-128">**Azure function App** es un servicio Microsoft Azure, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="9f5ca-129">Esto proporciona una manera de delegar el trabajo en la nube, en lugar de la aplicación local, que puede tener muchas ventajas.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="9f5ca-130">**Azure Functions** admite varios lenguajes de desarrollo, como C\#, F\#, node. js, Java y php.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="9f5ca-131">Para obtener más información, visite la [página **Azure Functions** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="9f5ca-132">**Azure Storage: tables** es un servicio de Microsoft Azure, que permite a los desarrolladores almacenar datos estructurados que no son de SQL en la nube, lo que hace que sea fácilmente accesible en cualquier lugar.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="9f5ca-133">El servicio ofrece un diseño sin esquemas, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="9f5ca-134">Para obtener más información, visite la [página **tablas de Azure** .](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="9f5ca-135">Este curso le enseñará cómo configurar y usar el servicio de IoT Hub y, a continuación, visualizar una respuesta proporcionada por un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="9f5ca-136">Dependerá de que aplique estos conceptos a una configuración personalizada del servicio de IoT Hub, que podría estar compilando.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="9f5ca-137">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="9f5ca-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9f5ca-138">Recurso</span><span class="sxs-lookup"><span data-stu-id="9f5ca-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9f5ca-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9f5ca-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9f5ca-140"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="9f5ca-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="9f5ca-141">MR y Azure 313: servicio de IoT Hub</span><span class="sxs-lookup"><span data-stu-id="9f5ca-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="9f5ca-142">✔️</span><span class="sxs-lookup"><span data-stu-id="9f5ca-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9f5ca-143">✔️</span><span class="sxs-lookup"><span data-stu-id="9f5ca-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="9f5ca-144">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="9f5ca-144">Prerequisites</span></span>

<span data-ttu-id="9f5ca-145">Para obtener los requisitos previos más actualizados para el desarrollo con la realidad mixta, incluido con Microsoft HoloLens, visite el artículo [instalar las herramientas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="9f5ca-146">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Python.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="9f5ca-147">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="9f5ca-148">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="9f5ca-149">Se requiere el siguiente hardware y software:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="9f5ca-150">Windows 10 Fall Creators Update (o posterior), **modo de desarrollador habilitado**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="9f5ca-151">No se puede ejecutar una máquina virtual con Hyper-V en Windows 10 Home Edition.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="9f5ca-152">SDK de Windows 10 (versión más reciente)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="9f5ca-153">HoloLens, **modo de desarrollador habilitado**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="9f5ca-154">Visual Studio 2017.15.4 (solo se usa para acceder a Azure Cloud Explorer)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="9f5ca-155">Acceso a Internet para Azure y para el servicio de IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="9f5ca-156">Para obtener más información, siga este [vínculo a IOT Hub página de servicio](https://azure.microsoft.com/services/iot-hub/) .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/services/iot-hub/)</span></span>
- <span data-ttu-id="9f5ca-157">Un modelo de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-157">A machine learning model.</span></span> <span data-ttu-id="9f5ca-158">Si no tiene su propio modelo listo para usar, [puede usar el modelo que se proporciona con este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="9f5ca-159">Software de **Hyper-V** habilitado en la máquina de desarrollo de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="9f5ca-160">Una máquina virtual que ejecuta Ubuntu (16,4 o 18,4), que se ejecuta en el equipo de desarrollo o, como alternativa, puede usar un equipo independiente que ejecute Linux (Ubuntu 16,4 o 18,4).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="9f5ca-161">Puede encontrar más información sobre cómo crear una máquina virtual en Windows con Hyper-V en el [capítulo "antes de empezar"](#before-you-start). (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="9f5ca-162">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="9f5ca-162">Before you start</span></span>

1. <span data-ttu-id="9f5ca-163">Configure y pruebe su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="9f5ca-164">Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="9f5ca-165">Es una buena idea realizar la **calibración** y el **ajuste del sensor** al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="9f5ca-166">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="9f5ca-167">Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="9f5ca-168">Configure la **máquina virtual de Ubuntu** con **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="9f5ca-169">Los siguientes recursos le ayudarán en el proceso.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="9f5ca-170">En primer lugar, siga este vínculo para [descargar el ISO de Ubuntu 16.04.4 lts (Xenial Xerus)](https://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="9f5ca-171">Seleccione la **imagen de escritorio de PC de 64 bits (amd64)** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="9f5ca-172">Asegúrese de que **Hyper-V** está habilitado en el equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="9f5ca-173">Puede seguir este vínculo para obtener instrucciones sobre la [instalación y habilitación de Hyper-V en Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="9f5ca-174">Inicie Hyper-V y cree una nueva máquina virtual de Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="9f5ca-175">Puede seguir este vínculo para obtener una [Guía paso a paso sobre cómo crear una máquina virtual con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="9f5ca-176">Cuando se le solicite **"instalar un sistema operativo desde un archivo de imagen de arranque"** , seleccione el **ISO de Ubuntu** que ha descargado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9f5ca-177">No se sugiere el uso de **creación rápida de Hyper-V** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="9f5ca-178">Capítulo 1: recuperar el modelo de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="9f5ca-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="9f5ca-179">Con este curso, tendrá acceso a un [modelo de Custom Vision](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) predefinido que detecta teclados y ratones de las imágenes.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="9f5ca-180">Si usa esto, continúe con el [capítulo 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="9f5ca-181">Sin embargo, puede seguir estos pasos si desea usar su propio modelo de Custom Vision:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="9f5ca-182">En el **proyecto de Custom Vision** , vaya a la pestaña **rendimiento** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="9f5ca-183">El modelo debe usar un dominio *compacto* para exportar el modelo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="9f5ca-184">Puede cambiar el dominio de modelos en la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-184">You can change your models domain in the settings for your project.</span></span>

    ![pestaña rendimiento](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="9f5ca-186">Seleccione la **iteración** que desea exportar y haga clic en **exportar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="9f5ca-187">Aparecerá una hoja.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-187">A blade will appear.</span></span>

    ![exportar hoja](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="9f5ca-189">En la hoja, haga clic en **archivo de Docker**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-189">In the blade click **Docker File**.</span></span>

    ![seleccionar Docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="9f5ca-191">Haga clic en **Linux** en el menú desplegable y, a continuación, haga clic en **Descargar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Haga clic en descargar](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="9f5ca-193">Descomprima el contenido.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-193">Unzip the content.</span></span> <span data-ttu-id="9f5ca-194">La usará más adelante en este curso.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="9f5ca-195">Capítulo 2: servicio de Container Registry</span><span class="sxs-lookup"><span data-stu-id="9f5ca-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="9f5ca-196">El **servicio Container Registry** es el repositorio que se usa para hospedar los contenedores.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="9f5ca-197">El **servicio IOT Hub** que se va a compilar y usar en este curso hace referencia a **Container Registry servicio** para obtener los contenedores que se van a implementar en el dispositivo perimetral.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="9f5ca-198">En primer lugar, siga este [vínculo a Azure portal](https://portal.azure.com/)e inicie sesión con sus credenciales.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="9f5ca-199">Vaya a **crear un recurso** y busque **Container Registry**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![registro de contenedor](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="9f5ca-201">Haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="9f5ca-202">Establezca los parámetros de instalación del servicio:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="9f5ca-203">Inserte un nombre para el proyecto, en este ejemplo, llamado **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="9f5ca-204">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="9f5ca-205">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="9f5ca-206">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="9f5ca-207">Establezca la ubicación del servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="9f5ca-208">Establezca el **usuario administrador** en **Habilitar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="9f5ca-209">Establezca **SKU** en **básico**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="9f5ca-210">Haga clic en **crear** y espere a que se creen los servicios.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="9f5ca-211">Cuando aparezca la notificación que le informa de la creación correcta de la *Container Registry*, haga clic en **ir al recurso** para redirigirlo a la página del servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="9f5ca-212">En la página servicio de *Container Registry* , haga clic en **claves de acceso**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="9f5ca-213">Tome nota (puede utilizar el Bloc de notas) de los siguientes parámetros:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="9f5ca-214">**Servidor de inicio de sesión**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-214">**Login Server**</span></span>
    2. <span data-ttu-id="9f5ca-215">**Nombre**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-215">**Username**</span></span>
    3. <span data-ttu-id="9f5ca-216">**Contraseña**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="9f5ca-217">Capítulo 3: servicio de IoT Hub</span><span class="sxs-lookup"><span data-stu-id="9f5ca-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="9f5ca-218">Ahora comenzará la creación y configuración del servicio de **IOT Hub**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="9f5ca-219">Si aún no ha iniciado sesión, inicie sesión en [Azure portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="9f5ca-220">Una vez iniciada la sesión, haga clic en **crear un recurso** en la esquina superior izquierda y busque **IOT Hub**y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![búsqueda de la cuenta de almacenamiento](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="9f5ca-222">La nueva página proporcionará una descripción del servicio de la **cuenta de almacenamiento** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="9f5ca-223">En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="9f5ca-225">Una vez que haya hecho clic en **crear**, aparecerá un panel:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="9f5ca-226">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="9f5ca-227">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="9f5ca-228">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="9f5ca-229">Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="9f5ca-230">Seleccione una **Ubicación** adecuada (use la misma ubicación en todos los servicios que cree en este curso).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="9f5ca-231">Inserte el **nombre** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="9f5ca-232">En la parte inferior de la página, haga clic en **siguiente: tamaño y escala**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="9f5ca-234">En esta página, seleccione el **nivel de precios y de escala** (si se trata de la primera instancia de servicio de IOT Hub, debe estar disponible un nivel gratis).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="9f5ca-235">Haga clic en **revisar y crear**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-235">Click on **Review + Create**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="9f5ca-237">Revise la configuración y haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-237">Review your settings and click on **Create**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="9f5ca-239">Cuando aparezca la notificación que le informa de la creación correcta del servicio de *IOT Hub* , haga clic en **ir al recurso** para redirigirlo a la página del servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="9f5ca-241">Desplácese por el panel lateral de la izquierda hasta que vea *Administración automática de dispositivos*, haga clic en **IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="9f5ca-243">En la ventana que aparece a la derecha, haga clic en **agregar IOT Edge dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="9f5ca-244">Aparecerá una hoja a la derecha.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="9f5ca-245">En la hoja, proporcione a su nuevo dispositivo un **identificador de dispositivo** (el nombre que prefiera).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="9f5ca-246">A continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-246">Then, click **Save**.</span></span> <span data-ttu-id="9f5ca-247">Las claves *principal* y *secundaria* se generarán automáticamente, si se ha **generado automáticamente** una marca.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="9f5ca-249">Volverá a la sección *dispositivos IOT Edge* , donde se mostrará el nuevo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="9f5ca-250">Haga clic en el nuevo dispositivo (descrito en rojo en la siguiente imagen).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="9f5ca-252">En la página *detalles del dispositivo* que aparece, realice una copia de la cadena de **conexión** (clave principal).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="9f5ca-254">Vuelva al panel de la izquierda y haga clic en *directivas de acceso compartido*para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="9f5ca-255">En la página que aparece, haga clic en **iothubowner**y aparecerá una hoja a la derecha de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="9f5ca-256">Tome nota (en el Bloc de notas) de la **cadena de conexión** (clave principal), para usarla más adelante al establecer la *cadena de conexión* en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="9f5ca-258">Capítulo 4: configurar el entorno de desarrollo</span><span class="sxs-lookup"><span data-stu-id="9f5ca-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="9f5ca-259">Para crear e implementar módulos para *IOT Hub Edge*, necesitará los siguientes componentes instalados en el equipo de desarrollo que ejecuta Windows 10:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="9f5ca-260">[Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), le pedirá que cree una cuenta para poder descargar.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="9f5ca-261">[![descargar Docker para Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9f5ca-262">Docker requiere *Windows 10 Pro*, *Enterprise 14393*o *Windows Server 2016 RTM*para ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="9f5ca-263">Si está ejecutando otras versiones de Windows 10, puede intentar instalar Docker con el cuadro de [herramientas de Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="9f5ca-264">[Python 3,6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="9f5ca-265">[![descargar Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="9f5ca-266">[Visual Studio Code (también conocido como vs Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="9f5ca-267">[![descargar VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="9f5ca-268">Después de instalar el software mencionado anteriormente, deberá reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="9f5ca-269">Capítulo 5: configuración del entorno de Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9f5ca-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="9f5ca-270">Ahora puede continuar con la configuración del dispositivo **que ejecuta el sistema operativo Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="9f5ca-271">Siga los pasos que se indican a continuación para instalar el software necesario para implementar los contenedores en el panel:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f5ca-272">Siempre debe preceder los comandos de terminal con **sudo** para que se ejecute como usuario administrador.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="9f5ca-273">es decir,</span><span class="sxs-lookup"><span data-stu-id="9f5ca-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="9f5ca-274">Abra el **terminal Ubuntu**y use el siguiente comando para instalar **PIP**:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! SUGERENCIA]<span data-ttu-id="9f5ca-275"> puede abrir *terminal* fácilmente mediante el método abreviado de teclado: **Ctrl + Alt + T**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="9f5ca-276">En este capítulo, es posible que el *terminal*le solicite permiso para usar el almacenamiento del dispositivo y que escriba y **/n** (sí o no), escriba **' y '** y, a continuación, presione la tecla **entrar** para aceptar.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="9f5ca-277">Una vez que se haya completado el comando, use el siguiente comando para instalar **rizo**:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="9f5ca-278">Una vez instalados **PIP** y **doblez** , use el siguiente comando para instalar el **IOT Edge en tiempo de ejecución**, que es necesario para implementar y controlar los módulos en el panel:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="9f5ca-279">En este momento se le pedirá que abra el archivo de *configuración en tiempo de ejecución*para insertar **la cadena de conexión del dispositivo**que anotó (en el Bloc de notas), al crear el servicio de **IOT Hub** ([en el paso 14, del capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="9f5ca-280">Ejecute la siguiente línea en el terminal para abrir el archivo:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="9f5ca-281">El archivo **config. yaml** se mostrará, listo para su edición:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="9f5ca-282">Cuando se abre este archivo, puede ser algo confuso.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="9f5ca-283">Modificará el texto de este archivo, dentro del propio *terminal* .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="9f5ca-284">Use las teclas de flecha del teclado para desplazarse hacia abajo (tendrá que desplazarse hacia abajo) para llegar a la línea que contiene ":</span><span class="sxs-lookup"><span data-stu-id="9f5ca-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="9f5ca-285">" **\<agregar la cadena de conexión del dispositivo aquí >** ".</span><span class="sxs-lookup"><span data-stu-id="9f5ca-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="9f5ca-286">Línea de sustitución, **incluidos los corchetes**, con la **cadena de conexión del dispositivo** que anotó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="9f5ca-287">Con la cadena de conexión en su lugar, en el teclado, presione las teclas **Ctrl + X** para guardar el archivo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="9f5ca-288">Le pedirá que confirme si escribe **Y**. A continuación, presione la tecla **entrar** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="9f5ca-289">Regresará al *terminal*normal.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="9f5ca-290">Una vez que estos comandos se ejecuten correctamente, habrá instalado el **tiempo de ejecución de IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="9f5ca-291">Una vez inicializado, el tiempo de ejecución se iniciará por sí mismo cada vez que se encienda el dispositivo y permanecerá en segundo plano, esperando a que los módulos se implementen desde el **servicio de IOT Hub**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="9f5ca-292">Ejecute la siguiente línea de comandos para inicializar el *tiempo de ejecución de IOT Edge*:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="9f5ca-293">Si realiza cambios en el archivo. yaml o en la configuración anterior, deberá volver a ejecutar la línea de reinicio anterior en *terminal*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="9f5ca-294">Para comprobar el estado del *tiempo de ejecución de IOT Edge* , ejecute la siguiente línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="9f5ca-295">El tiempo de ejecución debe aparecer con el estado **activo (en ejecución)** en texto verde.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="9f5ca-296">Presione las teclas **Ctrl + C** para salir de la página Estado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="9f5ca-297">Para comprobar que el *tiempo de ejecución de IOT Edge* está extrayendo los contenedores, escriba el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="9f5ca-298">Debe aparecer una lista con dos (2) contenedores.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="9f5ca-299">Estos son los módulos predeterminados que crea automáticamente el servicio IoT Hub (edgeAgent y edgeHub).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="9f5ca-300">Una vez que cree e implemente sus propios módulos, aparecerán en esta lista, debajo de los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="9f5ca-301">Capítulo 6: instalación de las extensiones</span><span class="sxs-lookup"><span data-stu-id="9f5ca-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f5ca-302">Los siguientes capítulos (6-9) se realizarán en el equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="9f5ca-303">Abra **vs Code**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="9f5ca-304">Haga clic en el botón **extensiones** (cuadrado) de la barra izquierda de vs code para abrir el **Panel extensiones**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="9f5ca-305">Busque e instale las extensiones siguientes (como se muestra en la imagen siguiente):</span><span class="sxs-lookup"><span data-stu-id="9f5ca-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="9f5ca-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="9f5ca-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="9f5ca-307">Kit de herramientas de IoT de Azure</span><span class="sxs-lookup"><span data-stu-id="9f5ca-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="9f5ca-308">Docker</span><span class="sxs-lookup"><span data-stu-id="9f5ca-308">Docker</span></span>   

    ![Creación de un contenedor](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="9f5ca-310">Una vez instaladas las extensiones, cierre y vuelva a abrir VS Code.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="9f5ca-311">Con VS Code abierto una vez más, vaya a **ver** > **terminal integrado**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="9f5ca-312">Ahora va a instalar **Cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="9f5ca-313">En el terminal, ejecute el siguiente comando de Bash:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! SUGERENCIA]<span data-ttu-id="9f5ca-314"> Si tiene problemas con este comando:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="9f5ca-315">Reinicie VS Code y/o el equipo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="9f5ca-316">Puede que sea necesario cambiar el **terminal de vs Code** por el que ha estado usando para instalar Python, es decir, **PowerShell** (especialmente en caso de que el entorno de Python ya esté instalado en el equipo).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="9f5ca-317">Con el terminal abierto, encontrará el menú desplegable en el lado derecho del terminal.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="9f5ca-318">![crear el contenedor](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="9f5ca-319">Asegúrese de que la ruta de instalación de **Python** se agrega como **variable de entorno** en la máquina.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="9f5ca-320">Cookiecutter debe formar parte de la misma ruta de acceso de ubicación.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="9f5ca-321">Siga este [vínculo para obtener más información sobre las variables de entorno](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="9f5ca-322">Una vez que **Cookiecutter** haya finalizado la instalación, debe reiniciar el equipo para que **Cookiecutter** se reconozca como un comando, dentro del entorno del sistema.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="9f5ca-323">Capítulo 7: creación de la solución de contenedor</span><span class="sxs-lookup"><span data-stu-id="9f5ca-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="9f5ca-324">En este punto, debe crear el contenedor, con el módulo, que se va a insertar en el *Container Registry*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="9f5ca-325">Una vez que haya insertado el contenedor, usará el servicio *IOT Hub Edge* para implementarlo en el dispositivo, que ejecuta el *tiempo de ejecución de IOT Edge*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="9f5ca-326">En VS Code, haga clic en **ver** > **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="9f5ca-327">En la paleta, busque y ejecute **Azure IOT Edge: nueva solución de IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="9f5ca-328">Vaya a la ubicación en la que desea crear la solución.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="9f5ca-329">Presione la tecla **entrar** para aceptar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="9f5ca-330">Asigne un nombre a la solución.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-330">Give a name to your solution.</span></span> <span data-ttu-id="9f5ca-331">Presione la tecla **entrar** para confirmar el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="9f5ca-332">Ahora se le pedirá que elija el marco de trabajo de la plantilla de la solución.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="9f5ca-333">Haga clic en **módulo de Python**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-333">Click **Python Module**.</span></span> <span data-ttu-id="9f5ca-334">Presione la tecla **entrar** para confirmar esta opción.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="9f5ca-335">Asigne un nombre al módulo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-335">Give a name to your module.</span></span> <span data-ttu-id="9f5ca-336">Presione la tecla **entrar** para confirmar el nombre del módulo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="9f5ca-337">Asegúrese de tomar nota (con el Bloc de notas) del nombre del módulo, tal y como se usa más adelante.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="9f5ca-338">Observará que aparecerá una dirección de *repositorio de imagen de Docker* pregenerada en la paleta.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="9f5ca-339">Tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-339">It will look like:</span></span>

    <span data-ttu-id="9f5ca-340">**localhost: 5000/-el nombre del módulo:** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="9f5ca-341">Elimine **localhost: 5000**y, en su lugar, inserte la *Container Registry* dirección del **servidor de inicio de sesión** , que anotó al crear el **servicio Container Registry** ([en el paso 8 del capítulo 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="9f5ca-342">Presione la tecla **entrar** para confirmar la dirección.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="9f5ca-343">En este momento, se creará la solución que contiene la plantilla para el módulo de Python y su estructura se mostrará en la **pestaña explorar**, de vs Code, en el lado izquierdo de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="9f5ca-344">Si la **pestaña explorar** no está abierta, puede abrirla haciendo clic en el botón de nivel superior, en la barra de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Creación de un contenedor](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="9f5ca-346">El último paso de este capítulo es hacer clic y abrir el **archivo. env**, desde la **pestaña explorar**, y agregar el **nombre de usuario** y la **contraseña**de *Container Registry* .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="9f5ca-347">Git omite este archivo, pero al compilar el contenedor, establecerá las credenciales para tener acceso al **servicio Container Registry**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Creación de un contenedor](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="9f5ca-349">Capítulo 8: edición de la solución de contenedor</span><span class="sxs-lookup"><span data-stu-id="9f5ca-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="9f5ca-350">Ahora completará la solución de contenedor mediante la actualización de los siguientes archivos:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="9f5ca-351">script de Python *<span></span>Main. py* .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="9f5ca-352">*requirements. txt*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-352">*requirements.txt*.</span></span>
- <span data-ttu-id="9f5ca-353">*Deployment. template. JSON*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="9f5ca-354">*Dockerfile. AMD64*</span><span class="sxs-lookup"><span data-stu-id="9f5ca-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="9f5ca-355">A continuación, creará la carpeta *images* , usada por el script de Python para comprobar que las imágenes coinciden con el *modelo de Custom Vision*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="9f5ca-356">Por último, agregará el archivo *Labels. txt* , que le ayudará a leer el modelo y el archivo *Model. PB* , que es el modelo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="9f5ca-357">Con VS Code abierto, vaya a la carpeta del módulo y busque el script denominado **<span></span>Main. py**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="9f5ca-358">Haga doble clic para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-358">Double-click to open it.</span></span>

2. <span data-ttu-id="9f5ca-359">Elimine el contenido del archivo e inserte el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="9f5ca-360">Abra el archivo denominado **requirements. txt**y sustituya su contenido por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="9f5ca-361">Abra el archivo denominado **Deployment. template. JSON**y sustituya su contenido por la siguiente directriz:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="9f5ca-362">Dado que tendrá su propia estructura JSON, única, tendrá que editarla manualmente (en lugar de copiar un ejemplo).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="9f5ca-363">Para facilitar esta tarea, use la imagen siguiente como guía.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="9f5ca-364">Las áreas que tendrán un aspecto distinto al suyo, pero que **no debe cambiar, se resaltan en amarillo**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="9f5ca-365">**Las secciones que debe eliminar se resaltan en rojo.**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="9f5ca-366">Tenga cuidado de eliminar los corchetes correctos y, además, quite las comas.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Creación de un contenedor](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="9f5ca-368">El JSON completado debe parecerse a la imagen siguiente (sin embargo, con las diferencias únicas: *nombre de usuario/contraseña/nombre de módulo/referencias de módulo*):</span><span class="sxs-lookup"><span data-stu-id="9f5ca-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Creación de un contenedor](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="9f5ca-370">Abra el archivo denominado **Dockerfile. AMD64**y sustituya su contenido por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="9f5ca-371">Haga clic con el botón secundario en la carpeta situada debajo de **módulos** (tendrá el nombre que proporcionó anteriormente; en el ejemplo más abajo, se denomina *pythonmodule*) y haga clic en **nueva carpeta**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="9f5ca-372">Asigne a la carpeta el nombre **images**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="9f5ca-373">Dentro de la carpeta, agregue algunas imágenes que contengan el mouse o el teclado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="9f5ca-374">Serán las imágenes que se van a analizar con el modelo Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="9f5ca-375">Si usa su propio modelo, tendrá que cambiarlo para reflejar sus propios datos de modelos.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="9f5ca-376">Ahora deberá recuperar los archivos **Labels. txt** y **Model. PB** de la carpeta del modelo, que antes descargó (o creó a partir de su propio **Custom Vision Service**), en el [capítulo 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="9f5ca-377">Una vez que tenga los archivos, colóquelos dentro de la solución, junto con los demás archivos.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="9f5ca-378">El resultado final debe ser similar a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-378">The final result should look like the image below:</span></span>

    ![Creación de un contenedor](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="9f5ca-380">Capítulo 9: empaquetar la solución como un contenedor</span><span class="sxs-lookup"><span data-stu-id="9f5ca-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="9f5ca-381">Ahora está listo para "empaquetar" los archivos como un contenedor e insertarlos en el **Azure Container Registry**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="9f5ca-382">En VS Code, abra el *terminal integrado* (**Ver** > **terminal integrado** o **Ctrl**+ **\`** ) y use la siguiente línea para iniciar sesión en **Docker** (sustituya los valores del comando por las credenciales de la **Azure Container Registry (ACR)** ):</span><span class="sxs-lookup"><span data-stu-id="9f5ca-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="9f5ca-383">Haga clic con el botón derecho en el archivo **Deployment. template. JSON**y haga clic en **compilar IOT Edge solución**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="9f5ca-384">Este proceso de compilación tarda bastante tiempo (dependiendo del dispositivo), por lo que debe estar preparado para esperar.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="9f5ca-385">Una vez finalizado el proceso de compilación, se creará un archivo **Deployment. JSON** en una nueva carpeta denominada **config**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![crear implementación](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="9f5ca-387">Vuelva a abrir la **paleta de comandos** y busque **Azure: Sign in**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="9f5ca-388">Siga las indicaciones con las credenciales de su cuenta de Azure. VS Code le proporcionará una opción para *copiar y abrir*, que copiará el código del dispositivo que necesitará pronto y abrirá el explorador Web predeterminado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="9f5ca-389">Cuando se le solicite, pegue el código del dispositivo para autenticar el equipo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![copiar y abrir](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="9f5ca-391">Una vez que haya iniciado sesión, observará que, en la parte inferior del panel de *exploración* , se trata de una nueva sección denominada **Azure IOT Hub dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="9f5ca-392">Haga clic en esta sección para expandirla.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-392">Click this section to expand it.</span></span>

    ![dispositivo perimetral](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="9f5ca-394">Si el dispositivo no está aquí, tendrá que hacer clic con el botón derecho en *Azure IOT Hub dispositivos*y, a continuación, hacer clic en **establecer cadena de conexión de IOT Hub**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="9f5ca-395">Después verá que la paleta de **comandos** (en la parte superior de vs Code) le pedirá que escriba la *cadena de conexión*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="9f5ca-396">Esta es la *cadena de conexión* que anotó al final del [capítulo 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="9f5ca-397">Presione la tecla **entrar** cuando haya copiado la cadena en.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="9f5ca-398">El dispositivo debe cargarse y aparecer.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-398">Your device should load, and appear.</span></span> <span data-ttu-id="9f5ca-399">Haga clic con el botón derecho en el nombre del dispositivo y, a continuación, haga clic en **crear implementación para un único dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![crear implementación](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="9f5ca-401">Obtendrá un mensaje del *Explorador de archivos* , donde puede ir a la carpeta **config** y, a continuación, seleccionar el archivo **Deployment. JSON** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="9f5ca-402">Con ese archivo seleccionado, haga clic en el botón **seleccionar manifiesto de implementación perimetral** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![crear implementación](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="9f5ca-404">Llegados a este punto, ha proporcionado su **servicio de IOT Hub** con el manifiesto para que implemente el contenedor, como un módulo, desde su **Azure Container Registry**, y lo implemente de forma eficaz en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="9f5ca-405">Para ver los mensajes enviados desde el dispositivo a la IoT Hub, vuelva a hacer clic con el botón derecho en el nombre del dispositivo en la sección **dispositivos Azure IOT Hub** , en el panel **Explorador** y haga clic en **iniciar supervisión del mensaje de D2C**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="9f5ca-406">Los mensajes enviados desde el dispositivo deben aparecer en el terminal de VS.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="9f5ca-407">Sea paciente, ya que esto puede tardar algún tiempo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="9f5ca-408">Vea el capítulo siguiente para la depuración y comprobar si la implementación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="9f5ca-409">Este módulo iterará ahora entre las imágenes de la carpeta **images** y las analizará con cada iteración.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="9f5ca-410">Obviamente, esto es solo una demostración de cómo obtener el modelo de aprendizaje automático básico para trabajar en un entorno de dispositivo IoT Edge.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="9f5ca-411">Para expandir la funcionalidad de este ejemplo, puede continuar de varias maneras.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="9f5ca-412">Una manera podría incluir código en el contenedor, que capture fotografías de una cámara web conectada al dispositivo y las guarde en la carpeta images.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="9f5ca-413">Otra manera podría ser copiar las imágenes del dispositivo IoT en el contenedor.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="9f5ca-414">Una manera práctica de hacerlo es ejecutar el siguiente comando en el terminal del dispositivo IoT (quizás una aplicación pequeña podría hacer el trabajo, si desea automatizar el proceso).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="9f5ca-415">Puede probar este comando si lo ejecuta manualmente desde la ubicación de la carpeta donde se almacenan los archivos:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="9f5ca-416">Capítulo 10: depurar el tiempo de ejecución de IoT Edge</span><span class="sxs-lookup"><span data-stu-id="9f5ca-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="9f5ca-417">A continuación se muestra una lista de líneas de comandos y sugerencias que le ayudarán a supervisar y depurar la actividad de mensajería del *tiempo de ejecución de IOT Edge*desde el **dispositivo Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="9f5ca-418">Para comprobar el estado del *tiempo de ejecución de IOT Edge* , ejecute la siguiente línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="9f5ca-419">Recuerde presionar **Ctrl + C**para terminar de ver el estado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="9f5ca-420">Enumerar los contenedores que están implementados actualmente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="9f5ca-421">Si el *servicio IOT Hub* ha implementado los contenedores correctamente, se mostrarán ejecutando la siguiente línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="9f5ca-422">O bien</span><span class="sxs-lookup"><span data-stu-id="9f5ca-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="9f5ca-423">Lo anterior es una buena manera de comprobar si el módulo se ha implementado correctamente, tal y como aparecerá en la lista. de lo contrario, **solo** verá *edgeHub* y *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="9f5ca-424">Para mostrar los registros de código de un contenedor, ejecute la siguiente línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="9f5ca-425">**Comandos útiles para administrar el tiempo de ejecución de IoT Edge:**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="9f5ca-426">Para eliminar todos los contenedores del host:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="9f5ca-427">Para detener el *tiempo de ejecución de IOT Edge*:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="9f5ca-428">Capítulo 11: creación de un servicio tabla</span><span class="sxs-lookup"><span data-stu-id="9f5ca-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="9f5ca-429">Vuelva a Azure portal, donde creará un servicio de tablas de Azure, mediante la creación de un recurso de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="9f5ca-430">Si aún no ha iniciado sesión, inicie sesión en [Azure portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="9f5ca-431">Una vez que haya iniciado sesión, haga clic en **crear un recurso**, en la esquina superior izquierda, busque la **cuenta de almacenamiento**y presione la tecla **entrar** para iniciar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="9f5ca-432">Una vez que haya aparecido, haga clic en **cuenta de almacenamiento: BLOB, archivo, tabla, cola** en la lista.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![búsqueda de la cuenta de almacenamiento](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="9f5ca-434">La nueva página proporcionará una descripción del servicio de la **cuenta de almacenamiento** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="9f5ca-435">En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="9f5ca-437">Una vez que haya hecho clic en **crear**, aparecerá un panel:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="9f5ca-438">Inserte el **nombre** que desee para esta instancia de servicio (*debe estar todo en minúsculas*).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="9f5ca-439">En **modelo de implementación**, haga clic en **Administrador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="9f5ca-440">En **tipo de cuenta**, en el menú desplegable, haga clic en **almacenamiento (uso general V1)** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="9f5ca-441">Haga clic en una **Ubicación**adecuada.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="9f5ca-442">En el menú desplegable **replicación** , haga clic en **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="9f5ca-443">En **rendimiento**, haga clic en **estándar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="9f5ca-444">Dentro de la sección **transferencia segura requerida** , haga clic en **deshabilitado**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="9f5ca-445">En el menú desplegable **suscripción** , haga clic en una suscripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="9f5ca-446">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="9f5ca-447">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="9f5ca-448">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="9f5ca-449">Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="9f5ca-450">Deje **redes virtuales** como **deshabilitadas**si se trata de una opción.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="9f5ca-451">Haz clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-451">Click **Create**.</span></span>

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="9f5ca-453">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="9f5ca-454">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="9f5ca-455">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-455">Click on the notifications to explore your new Service instance.</span></span>

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="9f5ca-457">Haga clic en el botón **ir a recurso** de la notificación y se le dirigirá a la página de información general de la nueva instancia del servicio de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![ir al recurso](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="9f5ca-459">En la página información general, en la parte derecha, haga clic en **tablas**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![tablas](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="9f5ca-461">El panel de la derecha cambiará para mostrar la información del **servicio tabla** , en la que es necesario agregar una nueva tabla.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="9f5ca-462">Para ello, haga clic en el botón **+ tabla** en la esquina superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![abrir tablas](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="9f5ca-464">Se mostrará una nueva página, en la que es necesario escribir un **nombre de tabla**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="9f5ca-465">Este es el nombre que usará para hacer referencia a los datos de la aplicación en capítulos posteriores (creación de Function App y Power BI).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="9f5ca-466">Inserte **IoTMessages** como nombre (puede elegir el suyo propio, simplemente Recuerde que cuando se usa más adelante en este documento) y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="9f5ca-467">Una vez creada la nueva tabla, podrá verla en la página **Table Service** (en la parte inferior).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="9f5ca-469">Ahora, haga clic en **claves de acceso** y tome una copia del nombre y la **clave** de la **cuenta de almacenamiento** (con el Bloc de notas). estos valores se usarán más adelante en este curso, al crear el function App de **Azure**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="9f5ca-471">Vuelva a usar el panel de la izquierda, desplácese hasta la sección *Table Service* y haga clic en **tables** ( **examinar tablas**, en portales más recientes) y realice una copia de la **dirección URL** de la tabla (con el Bloc de notas).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="9f5ca-472">Usará este valor más adelante en este curso, al vincular la tabla a la aplicación **Power BI** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="9f5ca-474">Capítulo 12: completar la tabla de Azure</span><span class="sxs-lookup"><span data-stu-id="9f5ca-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="9f5ca-475">Ahora que se ha configurado la cuenta de almacenamiento de **Table Service** , es el momento de agregar datos a ella, que se usará para almacenar y recuperar información.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="9f5ca-476">La edición de las tablas se puede realizar a través de **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="9f5ca-477">Abra **Visual Studio** (**no** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="9f5ca-478">En el menú, haga clic en **ver** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Abra Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="9f5ca-480">El **Cloud Explorer** se abrirá como un elemento acoplado (sea paciente, ya que la carga puede tardar tiempo).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="9f5ca-481">Si la suscripción que usó para crear las *cuentas de almacenamiento* no es visible, asegúrese de que tiene:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="9f5ca-482">Ha iniciado sesión en la misma cuenta que la que usó para Azure portal.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="9f5ca-483">Seleccionó su suscripción desde la página de administración de cuentas (puede que tenga que aplicar un filtro de la configuración de la cuenta):</span><span class="sxs-lookup"><span data-stu-id="9f5ca-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![buscar suscripción](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="9f5ca-485">Se mostrarán los servicios en la nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="9f5ca-486">Busque **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de ella para expandir sus cuentas.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![abrir cuentas de almacenamiento](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="9f5ca-488">Una vez expandida, la **cuenta de almacenamiento** recién creada debe estar disponible.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="9f5ca-489">Haga clic en la flecha situada a la izquierda de su almacenamiento y, después, una vez expandida, busque **tablas** y haga clic en la flecha situada junto a ella para mostrar la **tabla** que ha creado en el último capítulo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="9f5ca-490">Haga doble clic en la **tabla**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="9f5ca-491">La tabla se abrirá en el centro de la ventana de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="9f5ca-492">Haga clic en el icono de la tabla con la **+** (más).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Agregar nueva tabla](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="9f5ca-494">Aparecerá una ventana que le solicitará que *agregue la entidad*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="9f5ca-495">Solo creará una entidad, aunque tendrá tres propiedades.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="9f5ca-496">Observará que *PartitionKey* y *RowKey* ya se han proporcionado, ya que se usan en la tabla para buscar los datos.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![partición y clave de fila](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="9f5ca-498">Actualice los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-498">Update the following values:</span></span>

    - <span data-ttu-id="9f5ca-499">Nombre: **PartitionKey**, valor: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="9f5ca-500">Nombre: **RowKey**, valor: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="9f5ca-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="9f5ca-501">A continuación, haga clic en **Agregar propiedad** (en la esquina inferior izquierda de la ventana *Agregar entidad* ) y agregue la siguiente propiedad:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="9f5ca-502">**MessageContent**, como una *cadena*, deje el valor vacío.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="9f5ca-503">La tabla debe coincidir con la de la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-503">Your table should match the one in the image below:</span></span>

    ![agregar valores correctos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="9f5ca-505">La razón por la que la entidad tiene el número 1 en la clave de fila, es que es posible que desee agregar más mensajes, en caso de que desee experimentar con este curso.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="9f5ca-506">Cuando haya terminado, haga clic en **Aceptar** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="9f5ca-507">La tabla ya está lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="9f5ca-508">Capítulo 13: creación de una Function App de Azure</span><span class="sxs-lookup"><span data-stu-id="9f5ca-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="9f5ca-509">Ahora es el momento de crear una *function App de Azure*, a la que llamará *el servicio IOT Hub* para almacenar los mensajes de dispositivo *IOT Edge* en el servicio **tabla** , que creó en el capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="9f5ca-510">En primer lugar, debe crear un archivo que permita que la función de Azure cargue las bibliotecas que necesita.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="9f5ca-511">Abra el **Bloc de notas** (Presione la *tecla Windows*y escriba *Notepad*).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![abrir el Bloc de notas](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="9f5ca-513">Con el Bloc de notas abierto, inserte la siguiente estructura JSON en él.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="9f5ca-514">Una vez hecho esto, guárdelo en el escritorio como **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="9f5ca-515">Este archivo define las bibliotecas que utilizará la función.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="9f5ca-516">Si ha usado NuGet, le resultará familiar.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="9f5ca-517">Es importante que la nomenclatura sea correcta; Asegúrese de que **no tiene una extensión de archivo. txt** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="9f5ca-518">Vea la siguiente referencia:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-518">See below for reference:</span></span>
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

3.  <span data-ttu-id="9f5ca-520">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="9f5ca-521">Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda y busque **function App**y presione la tecla **entrar** para buscar.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="9f5ca-522">Haga clic en *function App* de los resultados para abrir un nuevo panel.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![búsqueda de function App](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="9f5ca-524">El nuevo panel proporcionará una descripción del servicio **function App** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="9f5ca-525">En la parte inferior izquierda de este panel, haga clic en el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![instancia de la aplicación de función](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="9f5ca-527">Una vez que haya hecho clic en **crear**, rellene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="9f5ca-528">En **nombre**de la aplicación, inserte el nombre que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="9f5ca-529">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="9f5ca-530">Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea un **servicio de function App**, debe estar disponible un nivel gratis.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="9f5ca-531">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="9f5ca-532">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="9f5ca-533">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="9f5ca-534">Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="9f5ca-535">En el caso de **sistemas operativos**, haga clic en Windows, ya que es la plataforma prevista.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="9f5ca-536">Seleccione un **plan de hospedaje** (este tutorial usa un **plan de consumo**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="9f5ca-537">Seleccione una **Ubicación** (elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)</span><span class="sxs-lookup"><span data-stu-id="9f5ca-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="9f5ca-538">En la sección **almacenamiento** , **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="9f5ca-539">No necesitará *Application Insights* en esta aplicación, así que no dude en dejarlo **fuera**de servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="9f5ca-540">Haz clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-540">Click **Create**.</span></span>

        ![crear nueva instancia](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="9f5ca-542">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="9f5ca-543">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![nueva notificación](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="9f5ca-545">Haga clic en la notificación, una vez que la implementación sea correcta (ha finalizado).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="9f5ca-546">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![ir al recurso](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="9f5ca-548">En el lado izquierdo del nuevo panel, haga clic en el icono de **+** (más) situado junto a *funciones*para crear una nueva función.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Agregar nueva función](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="9f5ca-550">En el panel central, aparecerá la ventana de creación de la **función** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="9f5ca-551">Desplácese hacia abajo y haga clic en **función personalizada**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-551">Scroll down further, and click on **Custom function**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="9f5ca-553">Desplácese hacia abajo en la página siguiente hasta que encuentre **IOT Hub (centro de eventos)** y haga clic en él.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="9f5ca-555">En la hoja **IOT Hub (centro de eventos)** , establezca el **idioma** en **C#** y, a continuación, haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="9f5ca-557">En la ventana que aparecerá, asegúrese de que está seleccionado **IOT Hub** y de que el nombre del campo de *IOT Hub* corresponde al nombre del *servicio de IOT Hub* que ha creado anteriormente (en el[paso 8, del capítulo 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="9f5ca-558">A continuación, haga clic en el botón **seleccionar** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-558">Then click the **Select** button.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="9f5ca-560">De nuevo en la hoja **IOT Hub (centro de eventos)** , haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="9f5ca-562">Se le redirigirá al editor de funciones.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-562">You will be redirected to the function editor.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="9f5ca-564">Elimine todo el código que contiene y reemplácelo por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="9f5ca-565">Cambie las siguientes variables para que se correspondan con los valores adecuados (valores de**tabla** y **almacenamiento** , del [paso 11 y 13, respectivamente, del capítulo 11](#chapter-11---create-table-service)), que encontrará en la **cuenta de almacenamiento**:</span><span class="sxs-lookup"><span data-stu-id="9f5ca-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="9f5ca-566">**TableName**, con el nombre de la **tabla** que se encuentra en la **cuenta de almacenamiento**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="9f5ca-567">**tableURL**, con la dirección URL de la **tabla** que se encuentra en la **cuenta de almacenamiento**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="9f5ca-568">**storageAccountName**, con el nombre del valor que corresponde al nombre de su **cuenta de almacenamiento** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="9f5ca-569">**storageAccountKey**, con la clave que ha obtenido en el servicio de almacenamiento que ha creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="9f5ca-571">Con el código en su lugar, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="9f5ca-572">A continuación, haga clic en el icono de **\<** (flecha) situado en el lado derecho de la página.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="9f5ca-574">Un panel se deslizará hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-574">A panel will slide in from the right.</span></span> <span data-ttu-id="9f5ca-575">En ese panel, haga clic en **cargar**y aparecerá un *Explorador de archivos* .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="9f5ca-576">Vaya a y haga clic en el archivo **Project. JSON** , que ha creado anteriormente en el **Bloc de notas** y, a continuación, haga clic en el botón **abrir** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="9f5ca-577">Este archivo define las bibliotecas que utilizará la función.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-577">This file defines the libraries that your function will use.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="9f5ca-579">Cuando se haya cargado el archivo, aparecerá en el panel de la derecha.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="9f5ca-580">Al hacer clic en él se abrirá en el editor de **funciones** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="9f5ca-581">Debe tener **exactamente** el mismo aspecto que la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-581">It must look **exactly** the same as the next image.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="9f5ca-583">En este momento, sería conveniente probar la funcionalidad de la función para almacenar el mensaje en la *tabla*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="9f5ca-584">En el lado superior derecho de la ventana, haga clic en **prueba**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-584">On the top right side of the window, click on **Test**.</span></span>

    ![función personalizada](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="9f5ca-586">Inserte un mensaje en el **cuerpo**de la solicitud, tal como se muestra en la imagen anterior, y haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="9f5ca-587">La función se ejecutará y mostrará el estado del resultado (verá el **estado verde 202 aceptado**, encima de la ventana de *salida* , lo que significa que se trata de una llamada correcta):</span><span class="sxs-lookup"><span data-stu-id="9f5ca-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![resultado de salida](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="9f5ca-589">Capítulo 14: ver los mensajes activos</span><span class="sxs-lookup"><span data-stu-id="9f5ca-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="9f5ca-590">Si ahora abre Visual Studio (**no** Visual Studio Code), puede visualizar el resultado del mensaje de prueba, ya que se almacenará en el área de la cadena *MessageContent* .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![función personalizada](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="9f5ca-592">Con el servicio tabla y Function App en su lugar, los mensajes del dispositivo Ubuntu aparecerán en la tabla *IoTMessages* .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="9f5ca-593">Si aún no se está ejecutando, vuelva a iniciar el dispositivo y podrá ver los mensajes de resultado desde el dispositivo, y el módulo, dentro de la tabla, mediante el uso de Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![visualizar datos](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="9f5ca-595">Capítulo 15: configuración de Power BI</span><span class="sxs-lookup"><span data-stu-id="9f5ca-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="9f5ca-596">Para visualizar los datos del dispositivo IOT, configurará **Power BI** (versión de escritorio) para recopilar los datos del servicio *tabla* , que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="9f5ca-597">La versión de *HoloLens* de Power BI usará los datos para visualizar el resultado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="9f5ca-598">Abra el Microsoft Store en Windows 10 y busque **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="9f5ca-600">Descargue la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-600">Download the application.</span></span> <span data-ttu-id="9f5ca-601">Una vez finalizada la descarga, ábrala.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="9f5ca-602">Inicie sesión en *Power BI* con su **cuenta de Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="9f5ca-603">Puede que se le redirija a un explorador para suscribirse.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="9f5ca-604">Una vez que se haya registrado, vuelva a la aplicación Power BI e inicie sesión de nuevo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="9f5ca-605">Haga clic en **obtener datos** y, a continuación, haga clic en **más..** ..</span><span class="sxs-lookup"><span data-stu-id="9f5ca-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="9f5ca-607">Haga clic en **Azure**, **Azure Table Storage**y, a continuación, haga clic en **conectar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="9f5ca-609">Se le pedirá que inserte la **dirección URL** de la tabla que recopiló anteriormente ([en el paso 13 del capítulo 11](#chapter-11---create-table-service)) al crear el servicio tabla.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="9f5ca-610">Después de insertar la dirección URL, elimine la parte de la ruta de acceso que hace referencia a la tabla "subcarpeta" (que se IoTMessages en este curso).</span><span class="sxs-lookup"><span data-stu-id="9f5ca-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="9f5ca-611">El resultado final debe ser como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="9f5ca-612">A continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="9f5ca-614">Se le pedirá que inserte la **clave de almacenamiento** que anotó (en el[paso 11 del capítulo 11](#chapter-11---create-table-service)) antes de crear el Table Storage.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="9f5ca-615">A continuación, haga clic en **conectar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="9f5ca-617">Se mostrará un **Panel de navegación** , marque el cuadro situado junto a la tabla y haga clic en **cargar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="9f5ca-619">La tabla ya se ha cargado en Power BI, pero requiere una consulta para mostrar los valores en ella.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="9f5ca-620">Para ello, haga clic con el botón secundario en el nombre de la tabla que se encuentra en el **Panel campos** , en el lado derecho de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="9f5ca-621">A continuación, haga clic en **Editar consulta**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="9f5ca-623">Se abrirá un **Editor de Power Query** como una nueva ventana que muestra la tabla.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="9f5ca-624">Haga clic en el **registro** de palabra dentro de la columna *contenido* de la tabla para visualizar el contenido almacenado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="9f5ca-626">Haga clic en en la **tabla**, en la parte superior izquierda de la ventana.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="9f5ca-628">Haga clic en **cerrar & aplicar**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="9f5ca-630">Una vez que haya finalizado la carga de la consulta, en el **Panel campos**, en el lado derecho de la pantalla, marque las casillas correspondientes al **nombre** y el **valor**de los parámetros para visualizar el contenido de la columna **MessageContent** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="9f5ca-632">Haga clic en el **icono de disco azul** situado en la parte superior izquierda de la ventana para guardar el trabajo en una carpeta de su elección.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="9f5ca-634">Ahora puede hacer clic en el botón publicar para cargar la tabla en el área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="9f5ca-635">Cuando se le solicite, haga clic en **mi área de trabajo** y haga clic en *seleccionar*.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="9f5ca-636">Espere a que se muestre el resultado correcto del envío.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="9f5ca-639">El siguiente capítulo es específico de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="9f5ca-640">Power BI no está disponible actualmente como aplicación envolvente, pero puede ejecutar la versión de escritorio en el portal de Windows Mixed Reality (también conocido como acantilado House) a través de la aplicación de escritorio.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-640">Power BI is not currently available as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="9f5ca-641">Capítulo 16: visualización de datos de Power BI en HoloLens</span><span class="sxs-lookup"><span data-stu-id="9f5ca-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="9f5ca-642">En HoloLens, inicie sesión en el **Microsoft Store**; para ello, puntee en su icono en la lista de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="9f5ca-644">Busque y, a continuación, descargue la aplicación **Power BI** .</span><span class="sxs-lookup"><span data-stu-id="9f5ca-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="9f5ca-646">Inicie **Power BI** desde la lista de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="9f5ca-647">**Power BI** podría pedirle que inicie sesión en su **cuenta de Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="9f5ca-648">Una vez dentro de la aplicación, el área de trabajo se debe mostrar de forma predeterminada, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="9f5ca-649">Si esto no ocurre, simplemente haga clic en el icono del área de trabajo en el lado izquierdo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="9f5ca-651">Su aplicación IoT Hub finalizada</span><span class="sxs-lookup"><span data-stu-id="9f5ca-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="9f5ca-652">Enhorabuena, ha creado correctamente un servicio IoT Hub con un dispositivo perimetral de máquina virtual simulado.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="9f5ca-653">El dispositivo puede comunicar los resultados de un modelo de machine learning a un servicio tabla de Azure, facilitado por una Function App de Azure, que se lee en Power BI y se visualiza en una de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="9f5ca-655">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="9f5ca-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="9f5ca-656">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="9f5ca-656">Exercise 1</span></span>

<span data-ttu-id="9f5ca-657">Expanda la estructura de mensajería almacenada en la tabla y mostrarla como un gráfico.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="9f5ca-658">Es posible que desee recopilar más datos y almacenarlos en la misma tabla para que se muestren más adelante.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="9f5ca-659">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="9f5ca-659">Exercise 2</span></span>

<span data-ttu-id="9f5ca-660">Cree un módulo de "captura de cámara" adicional para implementarlo en el panel de IoT, de modo que pueda capturar imágenes a través de la cámara para su análisis.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
