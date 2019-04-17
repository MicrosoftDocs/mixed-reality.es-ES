---
title: Paquetes MRTK
description: En este artículo describe los paquetes que componen el Toollkit de realidad mixta de Microsoft.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality, MRTK, componente, paquete
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605692"
---
# <a name="mrtk-packages"></a><span data-ttu-id="6fa5d-104">Paquetes MRTK</span><span class="sxs-lookup"><span data-stu-id="6fa5d-104">MRTK packages</span></span>

<span data-ttu-id="6fa5d-105">El Kit de herramientas de realidad mixta (MRTK) es una colección de paquetes que permiten el desarrollo de aplicaciones de realidad mixta multiplataforma al proporcionar soporte para el hardware de realidad mixta y plataformas de manera formada por componentes.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="6fa5d-106">Hay tres categorías de paquetes MRTK:</span><span class="sxs-lookup"><span data-stu-id="6fa5d-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="6fa5d-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="6fa5d-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="6fa5d-108">Extensión</span><span class="sxs-lookup"><span data-stu-id="6fa5d-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="6fa5d-109">Experimental</span><span class="sxs-lookup"><span data-stu-id="6fa5d-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="6fa5d-110">Paquetes de Windows Foundation</span><span class="sxs-lookup"><span data-stu-id="6fa5d-110">Foundation Packages</span></span>

<span data-ttu-id="6fa5d-111">La base de Kit de herramientas de realidad mixta es el conjunto de paquetes que se habilite la aplicación para aprovechar la funcionalidad común entre plataformas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="6fa5d-112">Estos paquetes se libera y compatible con Microsoft desde el código fuente en el [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) bifurcación en GitHub.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![MRTK Foundation paquetes](images/mrtk-foundation.jpg)

<span data-ttu-id="6fa5d-114">*Paquetes de Foundation del Kit de herramientas de realidad mixtos*</span><span class="sxs-lookup"><span data-stu-id="6fa5d-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="6fa5d-115">La base de MRTK consta de:</span><span class="sxs-lookup"><span data-stu-id="6fa5d-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="6fa5d-116">Core Package</span><span class="sxs-lookup"><span data-stu-id="6fa5d-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="6fa5d-117">Proveedores de plataformas</span><span class="sxs-lookup"><span data-stu-id="6fa5d-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="6fa5d-118">Servicios del sistema</span><span class="sxs-lookup"><span data-stu-id="6fa5d-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="6fa5d-119">Característica activos</span><span class="sxs-lookup"><span data-stu-id="6fa5d-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="6fa5d-120">Las siguientes secciones describen los tipos de paquetes en cada categoría.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="6fa5d-121">Paquete de Core</span><span class="sxs-lookup"><span data-stu-id="6fa5d-121">Core Package</span></span>

<span data-ttu-id="6fa5d-122">El paquete principal es un _requiere_ componente y se toma como una dependencia por todos los paquetes MRTK foundation.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="6fa5d-123">El paquete MRTK Core incluye:</span><span class="sxs-lookup"><span data-stu-id="6fa5d-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="6fa5d-124">Tipos comunes de las interfaces, clases y datos</span><span class="sxs-lookup"><span data-stu-id="6fa5d-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="6fa5d-125">Componente de escena MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="6fa5d-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="6fa5d-126">Sombreador MRTK estándar</span><span class="sxs-lookup"><span data-stu-id="6fa5d-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="6fa5d-127">Proveedor de entrada de Unity</span><span class="sxs-lookup"><span data-stu-id="6fa5d-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="6fa5d-128">Administración de paquetes</span><span class="sxs-lookup"><span data-stu-id="6fa5d-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="6fa5d-129">Tipos comunes de las interfaces, clases y datos</span><span class="sxs-lookup"><span data-stu-id="6fa5d-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="6fa5d-130">El paquete principal de Kit de herramientas de realidad mixta contiene las definiciones para todas las interfaces comunes, las clases y tipos de datos que se usan por todos los demás componentes.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="6fa5d-131">Se recomienda encarecidamente que las aplicaciones tener acceso a componentes MRTK exclusivamente a través de las interfaces definidas para permitir el máximo nivel de compatibilidad entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="6fa5d-132">Componente de escena MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="6fa5d-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="6fa5d-133">El componente de la escena MixedRealityToolkit es el Administrador de recursos único y centralizado para el Kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6fa5d-134">Este componente carga y administra la duración de los módulos de plataforma y el servicio y proporciona recursos para los sistemas tener acceso a sus valores de configuración.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="6fa5d-135">Sombreador MRTK estándar</span><span class="sxs-lookup"><span data-stu-id="6fa5d-135">MRTK Standard Shader</span></span>

<span data-ttu-id="6fa5d-136">El sombreador estándar MRTK proporciona la base para prácticamente todos los materiales proporcionados por el MRTK.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="6fa5d-137">Este sombreador es extremadamente flexible y optimizado para la variedad de plataformas que admiten MRTK.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="6fa5d-138">Es _altamente_ recomienda materiales de la aplicación que utilice el sombreador MRTK estándar para un rendimiento óptimo.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="6fa5d-139">Proveedor de entrada de Unity</span><span class="sxs-lookup"><span data-stu-id="6fa5d-139">Unity Input Provider</span></span>

<span data-ttu-id="6fa5d-140">El proveedor de entrada de Unity proporciona acceso a los dispositivos de entrada común como dispositivos de juego, pantallas táctiles y un mouse espacial en 3D.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="6fa5d-141">Administración del paquete</span><span class="sxs-lookup"><span data-stu-id="6fa5d-141">Package Management</span></span>

<span data-ttu-id="6fa5d-142">_Próximamente_</span><span class="sxs-lookup"><span data-stu-id="6fa5d-142">_Coming soon_</span></span>

<span data-ttu-id="6fa5d-143">El paquete principal de Kit de herramientas de realidad mixta proporciona compatibilidad para detectar y administrar la foundation opcional, extensión y paquetes MRTK experimentales.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="6fa5d-144">Proveedores de plataformas</span><span class="sxs-lookup"><span data-stu-id="6fa5d-144">Platform Providers</span></span>

<span data-ttu-id="6fa5d-145">Los paquetes de proveedor de la plataforma MRTK son los componentes que habilitan la funcionalidad de plataforma y el Kit de herramientas de realidad mixta para hardware de realidad mixta de destino.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="6fa5d-146">Plataformas compatibles incluyen:</span><span class="sxs-lookup"><span data-stu-id="6fa5d-146">Supported platforms include:</span></span>

* [<span data-ttu-id="6fa5d-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6fa5d-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="6fa5d-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="6fa5d-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="6fa5d-149">Voz de Windows</span><span class="sxs-lookup"><span data-stu-id="6fa5d-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="6fa5d-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="6fa5d-150">Windows Mixed Reality</span></span>

<span data-ttu-id="6fa5d-151">El paquete de Windows Mixed Reality proporciona compatibilidad para dispositivos de Microsoft HoloLens y Windows Mixed Reality envolventes.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="6fa5d-152">El paquete contiene compatibilidad de plataforma completa, incluidos:</span><span class="sxs-lookup"><span data-stu-id="6fa5d-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="6fa5d-153">Mirada destinadas a</span><span class="sxs-lookup"><span data-stu-id="6fa5d-153">Gaze targeting</span></span>
* <span data-ttu-id="6fa5d-154">Gestos</span><span class="sxs-lookup"><span data-stu-id="6fa5d-154">Gestures</span></span>
* <span data-ttu-id="6fa5d-155">Controladores de movimiento de realidad mixta de Windows</span><span class="sxs-lookup"><span data-stu-id="6fa5d-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="6fa5d-156">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="6fa5d-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="6fa5d-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="6fa5d-157">OpenVR</span></span>

<span data-ttu-id="6fa5d-158">El paquete OpenVR proporciona compatibilidad con hardware y plataforma para dispositivos con la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="6fa5d-159">Voz de Windows</span><span class="sxs-lookup"><span data-stu-id="6fa5d-159">Windows Voice</span></span>

<span data-ttu-id="6fa5d-160">El paquete de voz de Windows proporciona compatibilidad para la funcionalidad de reconocimiento y el dictado de palabra clave en los dispositivos de Microsoft Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="6fa5d-161">Servicios del sistema</span><span class="sxs-lookup"><span data-stu-id="6fa5d-161">System Services</span></span>

<span data-ttu-id="6fa5d-162">Servicios de plataforma principales se muestran en los paquetes de servicio de sistema.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="6fa5d-163">Estos paquetes contienen las implementaciones predeterminadas de Mixed Reality del Kit de herramientas de las interfaces de servicio de sistema, definidas en el [core](#core-package) paquete.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="6fa5d-164">La base MRTK incluye los siguientes servicios del sistema:</span><span class="sxs-lookup"><span data-stu-id="6fa5d-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="6fa5d-165">Sistema de límite</span><span class="sxs-lookup"><span data-stu-id="6fa5d-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="6fa5d-166">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="6fa5d-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="6fa5d-167">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="6fa5d-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="6fa5d-168">Sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="6fa5d-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="6fa5d-169">Sistema Teleport</span><span class="sxs-lookup"><span data-stu-id="6fa5d-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="6fa5d-170">Sistema de límite</span><span class="sxs-lookup"><span data-stu-id="6fa5d-170">Boundary System</span></span>

<span data-ttu-id="6fa5d-171">El sistema de límite MRTK proporciona datos sobre la realidad virtual a playspace.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="6fa5d-172">En los sistemas para el que el usuario ha configurado el límite, el sistema puede proporcionar un plano floor, playspace rectangular, área sometidas a seguimiento y mucho más.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="6fa5d-173">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="6fa5d-173">Diagnostic System</span></span>

<span data-ttu-id="6fa5d-174">El sistema de diagnóstico MRTK proporciona datos de rendimiento en tiempo real dentro de su experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="6fa5d-175">En una vista, podrá ver la velocidad de fotogramas, tiempo de procesador y otras métricas de rendimiento clave que usa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="6fa5d-176">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="6fa5d-176">Input System</span></span>

<span data-ttu-id="6fa5d-177">Los sistemas de entrada MRTK permite que las aplicaciones tener acceso a la entrada de una manera multiplataforma especificando las acciones del usuario y asignar esas acciones a los botones más adecuados y ejes en los controladores de destino.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="6fa5d-178">Sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="6fa5d-178">Spatial Awareness System</span></span>

<span data-ttu-id="6fa5d-179">El sistema de reconocimiento MRTK espacial permite el acceso a datos del entorno del mundo real desde dispositivos, como el Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="6fa5d-180">Sistema Teleport</span><span class="sxs-lookup"><span data-stu-id="6fa5d-180">Teleport System</span></span>

<span data-ttu-id="6fa5d-181">El sistema de Teleport MRTK proporciona compatibilidad de desplazamiento de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="6fa5d-182">Característica activos</span><span class="sxs-lookup"><span data-stu-id="6fa5d-182">Feature Assets</span></span>

<span data-ttu-id="6fa5d-183">Característica activos son colecciones de funcionalidad relacionada que se entregan como secuencias de comandos y activos de Unity.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="6fa5d-184">Algunas de estas características incluyen:</span><span class="sxs-lookup"><span data-stu-id="6fa5d-184">Some of these features include:</span></span>

* <span data-ttu-id="6fa5d-185">Controles de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="6fa5d-185">User Interface Controls</span></span>
* <span data-ttu-id="6fa5d-186">Recursos estándar</span><span class="sxs-lookup"><span data-stu-id="6fa5d-186">Standard Assets</span></span>
* <span data-ttu-id="6fa5d-187">more</span><span class="sxs-lookup"><span data-stu-id="6fa5d-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="6fa5d-188">Paquetes de extensión</span><span class="sxs-lookup"><span data-stu-id="6fa5d-188">Extension Packages</span></span>

<span data-ttu-id="6fa5d-189">Los paquetes de extensión MRTK son una colección de paquetes por Microsoft y la Comunidad que amplían y mejoran la funcionalidad del Kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6fa5d-190">Los autores de extensiones se las dependencias necesarias de estado, marcar el paquete como compatible con el Kit de herramientas de realidad mixta y proporcionar las licencias y admite las instrucciones.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="6fa5d-191">Los paquetes de extensión pueden proporcionar las nuevas características y compatibilidad con la plataforma nueva.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="6fa5d-192">Con el tiempo, las extensiones, con la Ayuda y la aprobación de los autores, se pueden migrar a la base de MRTK en qué momento se libera y compatible con Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![Paquete de extensión MRTK](images/mrtk-extensions.jpg)

<span data-ttu-id="6fa5d-194">*Paquetes de extensión del Kit de herramientas de realidad mixtos*</span><span class="sxs-lookup"><span data-stu-id="6fa5d-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="6fa5d-195">Paquetes experimentales</span><span class="sxs-lookup"><span data-stu-id="6fa5d-195">Experimental Packages</span></span>

<span data-ttu-id="6fa5d-196">Paquetes experimentales proporcionan la capacidad de las características de prototipo de vuelo, versiones preliminares y emocionantes nuevas ideas.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="6fa5d-197">El objetivo de los paquetes más experimentales es probar algo nuevo y para medir el interés del cliente.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="6fa5d-198">Muchos, aunque no todos los paquetes experimentales estarán vuelto a publicar como extensiones una vez completada la creación de prototipos y la fase de pruebas.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![Paquetes Experimental MRTK](images/mrtk-experimental.jpg)

<span data-ttu-id="6fa5d-200">*Paquetes Experimental del Kit de herramientas de realidad mixtos*</span><span class="sxs-lookup"><span data-stu-id="6fa5d-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="6fa5d-201">Conclusión</span><span class="sxs-lookup"><span data-stu-id="6fa5d-201">Conclusion</span></span>

<span data-ttu-id="6fa5d-202">Los paquetes de Kit de herramientas de realidad mixta y el sistema de administración de paquetes están diseñados para habilitar un método simple y limpio para que pueda crear aditivamente características en sus experiencias sin necesidad de componentes innecesarios que se incluirán en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="6fa5d-203">Con el tiempo, se agregará compatibilidad con administración de paquetes y mejorado en el Kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6fa5d-204">Si tiene comentarios o desea participar, visite la [proyecto del Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity) en GitHub.</span><span class="sxs-lookup"><span data-stu-id="6fa5d-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="6fa5d-205">Vea también</span><span class="sxs-lookup"><span data-stu-id="6fa5d-205">See also</span></span>

* [<span data-ttu-id="6fa5d-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="6fa5d-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

