---
title: Referencia de la API del portal de dispositivos
description: Referencia de API para el Windows Device Portal en HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694436"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="9ec0b-104">Referencia de la API del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-104">Device portal API reference</span></span>

<span data-ttu-id="9ec0b-105">Todo el contenido de la [Windows Device Portal](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para acceder a los datos y controlar el dispositivo mediante programación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="9ec0b-106">Implementación de aplicación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-106">App deloyment</span></span>

<span data-ttu-id="9ec0b-107">**/API/App/PackageManager/Package (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="9ec0b-108">Desinstala una aplicación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-108">Uninstalls an app</span></span>

<span data-ttu-id="9ec0b-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-109">Parameters</span></span>
* <span data-ttu-id="9ec0b-110">paquete: Nombre de archivo del paquete que se puede desinstalar.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="9ec0b-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="9ec0b-112">Instala una aplicación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-112">Installs an App</span></span>

<span data-ttu-id="9ec0b-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-113">Parameters</span></span>
* <span data-ttu-id="9ec0b-114">paquete: Nombre de archivo del paquete de instalación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="9ec0b-115">carga</span><span class="sxs-lookup"><span data-stu-id="9ec0b-115">Payload</span></span>
* <span data-ttu-id="9ec0b-116">cuerpo de http que cumplan varias partes</span><span class="sxs-lookup"><span data-stu-id="9ec0b-116">multi-part conforming http body</span></span>

<span data-ttu-id="9ec0b-117">**/API/App/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="9ec0b-118">Recupera la lista de las aplicaciones instaladas en el sistema, con detalles</span><span class="sxs-lookup"><span data-stu-id="9ec0b-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="9ec0b-119">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-119">Return data</span></span>
* <span data-ttu-id="9ec0b-120">Lista de paquetes instalados con detalles</span><span class="sxs-lookup"><span data-stu-id="9ec0b-120">List of installed packages with details</span></span>

<span data-ttu-id="9ec0b-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="9ec0b-122">Obtiene el estado de en la instalación de la aplicación de progreso</span><span class="sxs-lookup"><span data-stu-id="9ec0b-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="9ec0b-123">Colección de volcados de memoria</span><span class="sxs-lookup"><span data-stu-id="9ec0b-123">Dump collection</span></span>

<span data-ttu-id="9ec0b-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="9ec0b-125">Deshabilita el bloqueo recopilación del volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="9ec0b-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="9ec0b-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-126">Parameters</span></span>
* <span data-ttu-id="9ec0b-127">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="9ec0b-127">packageFullname : package name</span></span>

<span data-ttu-id="9ec0b-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="9ec0b-129">Obtiene colección de volcados de configuración de aplicaciones con instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="9ec0b-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="9ec0b-130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-130">Parameters</span></span>
* <span data-ttu-id="9ec0b-131">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="9ec0b-131">packageFullname : package name</span></span>

<span data-ttu-id="9ec0b-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="9ec0b-133">Habilita y establece la configuración de control de volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="9ec0b-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="9ec0b-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-134">Parameters</span></span>
* <span data-ttu-id="9ec0b-135">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="9ec0b-135">packageFullname : package name</span></span>

<span data-ttu-id="9ec0b-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="9ec0b-137">Elimina un volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="9ec0b-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="9ec0b-138">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-138">Parameters</span></span>
* <span data-ttu-id="9ec0b-139">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="9ec0b-139">packageFullname : package name</span></span>
* <span data-ttu-id="9ec0b-140">nombre de archivo: nombre de archivo de volcado de memoria</span><span class="sxs-lookup"><span data-stu-id="9ec0b-140">fileName : dump file name</span></span>

<span data-ttu-id="9ec0b-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="9ec0b-142">Recupera un volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="9ec0b-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="9ec0b-143">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-143">Parameters</span></span>
* <span data-ttu-id="9ec0b-144">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="9ec0b-144">packageFullname : package name</span></span>
* <span data-ttu-id="9ec0b-145">nombre de archivo: nombre de archivo de volcado de memoria</span><span class="sxs-lookup"><span data-stu-id="9ec0b-145">fileName : dump file name</span></span>

<span data-ttu-id="9ec0b-146">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-146">Return data</span></span>
* <span data-ttu-id="9ec0b-147">Archivo de volcado.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-147">Dump file.</span></span> <span data-ttu-id="9ec0b-148">Inspeccionar con WinDbg o en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9ec0b-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="9ec0b-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="9ec0b-150">Devuelve una lista de todos los volcados de memoria para las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="9ec0b-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="9ec0b-151">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-151">Return data</span></span>
* <span data-ttu-id="9ec0b-152">Vuelca la lista de bloqueo por aplicación cargada de lado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="9ec0b-153">ETW</span><span class="sxs-lookup"><span data-stu-id="9ec0b-153">ETW</span></span>

<span data-ttu-id="9ec0b-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="9ec0b-155">Enumera los proveedores registrados</span><span class="sxs-lookup"><span data-stu-id="9ec0b-155">Enumerates registered providers</span></span>

<span data-ttu-id="9ec0b-156">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-156">Return data</span></span>
* <span data-ttu-id="9ec0b-157">Lista de proveedores, el nombre descriptivo y el GUID</span><span class="sxs-lookup"><span data-stu-id="9ec0b-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="9ec0b-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="9ec0b-159">Crea una sesión ETW en tiempo real; se administran a través de un websocket.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="9ec0b-160">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-160">Return data</span></span>
* <span data-ttu-id="9ec0b-161">Eventos ETW de los proveedores habilitados</span><span class="sxs-lookup"><span data-stu-id="9ec0b-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="9ec0b-162">SO Holographic</span><span class="sxs-lookup"><span data-stu-id="9ec0b-162">Holographic OS</span></span>

<span data-ttu-id="9ec0b-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="9ec0b-164">Devuelve una lista de proveedores ETW específicos HoloLens que no están registrados con el sistema</span><span class="sxs-lookup"><span data-stu-id="9ec0b-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="9ec0b-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="9ec0b-166">Devuelve los Estados de todos los servicios en ejecución.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-166">Returns the states of all services running.</span></span>

<span data-ttu-id="9ec0b-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="9ec0b-168">Obtiene la IPD almacenada (distancia Interpupillary) en milímetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="9ec0b-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="9ec0b-170">Establece la IPD</span><span class="sxs-lookup"><span data-stu-id="9ec0b-170">Sets the IPD</span></span>

<span data-ttu-id="9ec0b-171">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-171">Parameters</span></span>
* <span data-ttu-id="9ec0b-172">IPD: Nuevo valor IPD debe establecerse en milímetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="9ec0b-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="9ec0b-174">Obtener los requisitos de HTTPS para Device Portal</span><span class="sxs-lookup"><span data-stu-id="9ec0b-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="9ec0b-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="9ec0b-176">Establece los requisitos de HTTPS para el Portal de dispositivo</span><span class="sxs-lookup"><span data-stu-id="9ec0b-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="9ec0b-177">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-177">Parameters</span></span>
* <span data-ttu-id="9ec0b-178">requerido: Sí, no o el valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="9ec0b-179">Percepción holográfica</span><span class="sxs-lookup"><span data-stu-id="9ec0b-179">Holographic Perception</span></span>

<span data-ttu-id="9ec0b-180">**/API/holographic/Perception/Client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="9ec0b-181">Acepta las actualizaciones de websocket y ejecuta a un cliente de la percepción que envía actualizaciones a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="9ec0b-182">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-182">Parameters</span></span>
* <span data-ttu-id="9ec0b-183">clientmode: "activo" modo de seguimiento visual de fuerza cuando no se puede establecer de forma pasiva</span><span class="sxs-lookup"><span data-stu-id="9ec0b-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="9ec0b-184">Térmico holográfica</span><span class="sxs-lookup"><span data-stu-id="9ec0b-184">Holographic Thermal</span></span>

<span data-ttu-id="9ec0b-185">**/API/holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="9ec0b-186">Obtener la fase térmica del dispositivo (normal 0, 1 en caliente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="9ec0b-187">Control de la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="9ec0b-187">Perception Simulation Control</span></span>

<span data-ttu-id="9ec0b-188">**/API/holographic/Simulation/control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="9ec0b-189">Obtener el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-189">Get the simulation mode</span></span>

<span data-ttu-id="9ec0b-190">**/API/holographic/Simulation/control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="9ec0b-191">Establecer el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-191">Set the simulation mode</span></span>

<span data-ttu-id="9ec0b-192">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-192">Parameters</span></span>
* <span data-ttu-id="9ec0b-193">modo: modo de simulación: de forma predeterminada, simulación, remoto, heredado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="9ec0b-194">**/API/holographic/Simulation/control/Stream (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="9ec0b-195">Eliminar un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-195">Delete a control stream.</span></span>

<span data-ttu-id="9ec0b-196">**/API/holographic/Simulation/control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="9ec0b-197">Abra una conexión de socket web para un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="9ec0b-198">**/API/holographic/Simulation/control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="9ec0b-199">Crear un flujo de control (prioridad es necesaria) o publicar datos en un flujo creado (streamId necesario).</span><span class="sxs-lookup"><span data-stu-id="9ec0b-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="9ec0b-200">Datos enviados debe ser de tipo "application/octet-stream".</span><span class="sxs-lookup"><span data-stu-id="9ec0b-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="9ec0b-201">Reproducción de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="9ec0b-201">Perception Simulation Playback</span></span>

<span data-ttu-id="9ec0b-202">**/API/holographic/Simulation/Playback/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="9ec0b-203">Eliminar una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-203">Delete a recording.</span></span>

<span data-ttu-id="9ec0b-204">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-204">Parameters</span></span>
* <span data-ttu-id="9ec0b-205">grabación: Nombre de la grabación para eliminar.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="9ec0b-206">**/API/holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="9ec0b-207">Cargue una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-207">Upload a recording.</span></span>

<span data-ttu-id="9ec0b-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="9ec0b-209">Obtener todas las grabaciones.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-209">Get all recordings.</span></span>

<span data-ttu-id="9ec0b-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="9ec0b-211">Obtener el estado actual de la reproducción de una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="9ec0b-212">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-212">Parameters</span></span>
* <span data-ttu-id="9ec0b-213">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-213">recording : Name of recording.</span></span>

<span data-ttu-id="9ec0b-214">**/API/holographic/Simulation/Playback/Session/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="9ec0b-215">Descargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-215">Unload a recording.</span></span>

<span data-ttu-id="9ec0b-216">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-216">Parameters</span></span>
* <span data-ttu-id="9ec0b-217">grabación: Nombre de la grabación para descargar.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="9ec0b-218">**/API/holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="9ec0b-219">Cargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-219">Load a recording.</span></span>

<span data-ttu-id="9ec0b-220">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-220">Parameters</span></span>
* <span data-ttu-id="9ec0b-221">grabación: Nombre de la grabación para cargar.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="9ec0b-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="9ec0b-223">Obtener grabaciones cargadas.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-223">Get all loaded recordings.</span></span>

<span data-ttu-id="9ec0b-224">**/API/holographic/Simulation/Playback/Session/Pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="9ec0b-225">Pausar una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-225">Pause a recording.</span></span>

<span data-ttu-id="9ec0b-226">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-226">Parameters</span></span>
* <span data-ttu-id="9ec0b-227">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-227">recording : Name of recording.</span></span>

<span data-ttu-id="9ec0b-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="9ec0b-229">Reproducir una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-229">Play a recording.</span></span>

<span data-ttu-id="9ec0b-230">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-230">Parameters</span></span>
* <span data-ttu-id="9ec0b-231">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-231">recording : Name of recording.</span></span>

<span data-ttu-id="9ec0b-232">**/API/holographic/Simulation/Playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="9ec0b-233">Detener la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-233">Stop a recording.</span></span>

<span data-ttu-id="9ec0b-234">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-234">Parameters</span></span>
* <span data-ttu-id="9ec0b-235">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-235">recording : Name of recording.</span></span>

<span data-ttu-id="9ec0b-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="9ec0b-237">Obtiene los tipos de datos en una grabación de carga.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="9ec0b-238">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-238">Parameters</span></span>
* <span data-ttu-id="9ec0b-239">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="9ec0b-240">Grabación de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="9ec0b-240">Perception Simulation Recording</span></span>

<span data-ttu-id="9ec0b-241">**/API/holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="9ec0b-242">Iniciar una grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-242">Start a recording.</span></span> <span data-ttu-id="9ec0b-243">Solo puede estar activa una grabación única a la vez.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="9ec0b-244">Debe establecerse un encabezado, manos, spatialMapping o entorno.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="9ec0b-245">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-245">Parameters</span></span>
* <span data-ttu-id="9ec0b-246">principal: Establezca en 1 para datos de registro principal.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="9ec0b-247">práctico: Se establece en 1 para registrar los datos disponibles.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="9ec0b-248">spatialMapping: Se establece en 1 para registrar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="9ec0b-249">entorno: Se establece en 1 para registrar datos de entorno.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="9ec0b-250">nombre: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-250">name : Name of the recording.</span></span>
* <span data-ttu-id="9ec0b-251">singleSpatialMappingFrame: Se establece en 1 para registrar solo un marco de asignación espacial único.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="9ec0b-252">**/API/holographic/Simulation/Recording/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="9ec0b-253">Obtener estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-253">Get recording state.</span></span>

<span data-ttu-id="9ec0b-254">**/API/holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="9ec0b-255">Detener la grabación actual.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-255">Stop the current recording.</span></span> <span data-ttu-id="9ec0b-256">Grabación se devolverá como un archivo.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="9ec0b-257">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="9ec0b-257">Mixed Reality Capture</span></span>

<span data-ttu-id="9ec0b-258">**/API/holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="9ec0b-259">Descarga un archivo de realidad mixta desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="9ec0b-260">Op uso = parámetro de consulta de stream para streaming.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="9ec0b-261">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-261">Parameters</span></span>
* <span data-ttu-id="9ec0b-262">nombre de archivo: El nombre, hex64 codificada del archivo de vídeo para obtener</span><span class="sxs-lookup"><span data-stu-id="9ec0b-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="9ec0b-263">op : stream</span><span class="sxs-lookup"><span data-stu-id="9ec0b-263">op : stream</span></span>

<span data-ttu-id="9ec0b-264">**/API/holographic/MRC/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="9ec0b-265">Elimina una grabación desde el dispositivo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="9ec0b-266">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-266">Parameters</span></span>
* <span data-ttu-id="9ec0b-267">nombre de archivo: El nombre, hex64 codificada del archivo para eliminar</span><span class="sxs-lookup"><span data-stu-id="9ec0b-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="9ec0b-268">**/API/holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="9ec0b-269">Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="9ec0b-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="9ec0b-270">**/API/holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="9ec0b-271">Toma una fotografía de realidad mixta y crea un archivo en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="9ec0b-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="9ec0b-272">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-272">Parameters</span></span>
* <span data-ttu-id="9ec0b-273">Holo: capturar hologramas: true o false (valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="9ec0b-274">PV: cámara captura PV: true o false (valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="9ec0b-275">RenderFromCamera: Render (sólo 2 HoloLens) desde la perspectiva de la cámara de vídeo y fotos: true o false (valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="9ec0b-276">**/API/holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="9ec0b-277">Obtiene el valor predeterminado la realidad mixta configuración de capture</span><span class="sxs-lookup"><span data-stu-id="9ec0b-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="9ec0b-278">**/API/holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="9ec0b-279">Establece el valor predeterminado la realidad mixta ajustes de captura.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="9ec0b-280">Algunas de estas opciones se aplican a la foto MRC y la captura de vídeo del sistema.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="9ec0b-281">**/API/holographic/MRC/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="9ec0b-282">Obtiene el estado de la realidad mixta registran (está ejecutando, detenido)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="9ec0b-283">**/API/holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="9ec0b-284">Obtiene la imagen en miniatura para el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="9ec0b-285">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-285">Parameters</span></span>
* <span data-ttu-id="9ec0b-286">filename: El nombre, hex64 codificada del archivo para el que se solicita la miniatura</span><span class="sxs-lookup"><span data-stu-id="9ec0b-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="9ec0b-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="9ec0b-288">Se inicia una grabación de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="9ec0b-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="9ec0b-289">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-289">Parameters</span></span>
* <span data-ttu-id="9ec0b-290">Holo: capturar hologramas: true o false (valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="9ec0b-291">PV: cámara captura PV: true o false (valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="9ec0b-292">MIC: captura de micrófono: true o false (valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="9ec0b-293">bucle invertido: capturar audio de la aplicación: true o false (valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="9ec0b-294">RenderFromCamera: Render (sólo 2 HoloLens) desde la perspectiva de la cámara de vídeo y fotos: true o false (valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="9ec0b-295">Vstab: Estabilización de vídeo (sólo en HoloLens 2) habilite: true o false (valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="9ec0b-296">vstabbuffer: Latencia de búfer de estabilización de vídeo (sólo 2 HoloLens): entre 0 y 30 fotogramas (valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="9ec0b-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="9ec0b-298">Se detiene la actual mixto grabación realidad</span><span class="sxs-lookup"><span data-stu-id="9ec0b-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="9ec0b-299">Realidad mixta de transmisión por secuencias</span><span class="sxs-lookup"><span data-stu-id="9ec0b-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="9ec0b-300">HoloLens es compatible con la vista previa activa de la realidad mixta mediante descarga fragmentada de un mp4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="9ec0b-301">Secuencias de realidad mixta comparten el mismo conjunto de parámetros para controlar lo que se captura:</span><span class="sxs-lookup"><span data-stu-id="9ec0b-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="9ec0b-302">Holo: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="9ec0b-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="9ec0b-303">PV: cámara captura PV: true o false</span><span class="sxs-lookup"><span data-stu-id="9ec0b-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="9ec0b-304">MIC: captura de micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="9ec0b-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="9ec0b-305">bucle invertido: capturar audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="9ec0b-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="9ec0b-306">Si no se especifica ninguno de ellos: se capturarán hologramas, la cámara de fotografías y vídeo y audio de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="9ec0b-307">Si se especifica alguna: false predeterminado será el parámetro no especificado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="9ec0b-308">Parámetros opcionales (sólo 2 HoloLens)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="9ec0b-309">RenderFromCamera: representar desde la perspectiva de la cámara de vídeo y fotos: true o false (valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="9ec0b-310">Vstab,: habilitar la estabilización de vídeo: true o false (valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="9ec0b-311">vstabbuffer: latencia de búfer de estabilización de vídeo: entre 0 y 30 fotogramas (valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="9ec0b-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="9ec0b-313">Una secuencia de 5Mbit 1280x720p 30fps.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="9ec0b-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="9ec0b-315">Una secuencia de 5Mbit 1280x720p 30fps.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="9ec0b-316">**/API/holographic/Stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="9ec0b-317">Una secuencia de 30fps 2.5Mbit 854x480p.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="9ec0b-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="9ec0b-319">Una secuencia de 15fps 0.6Mbit 428x240p.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="9ec0b-320">Funciones de red</span><span class="sxs-lookup"><span data-stu-id="9ec0b-320">Networking</span></span>

<span data-ttu-id="9ec0b-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="9ec0b-322">Obtiene la configuración de ip actual</span><span class="sxs-lookup"><span data-stu-id="9ec0b-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="9ec0b-323">Información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="9ec0b-323">OS Information</span></span>

<span data-ttu-id="9ec0b-324">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="9ec0b-325">Obtiene la información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="9ec0b-325">Gets operating system information</span></span>

<span data-ttu-id="9ec0b-326">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="9ec0b-327">Obtiene el nombre del equipo</span><span class="sxs-lookup"><span data-stu-id="9ec0b-327">Gets the machine name</span></span>

<span data-ttu-id="9ec0b-328">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="9ec0b-329">Establece el nombre del equipo</span><span class="sxs-lookup"><span data-stu-id="9ec0b-329">Sets the machine name</span></span>

<span data-ttu-id="9ec0b-330">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-330">Parameters</span></span>
* <span data-ttu-id="9ec0b-331">nombre: Nuevo nombre de la máquina, hex64 codificado para establecer en</span><span class="sxs-lookup"><span data-stu-id="9ec0b-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="9ec0b-332">Datos de rendimiento</span><span class="sxs-lookup"><span data-stu-id="9ec0b-332">Performance data</span></span>

<span data-ttu-id="9ec0b-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="9ec0b-334">Devuelve la lista de procesos en ejecución con detalles</span><span class="sxs-lookup"><span data-stu-id="9ec0b-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="9ec0b-335">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-335">Return data</span></span>
* <span data-ttu-id="9ec0b-336">JSON con la lista de procesos y los detalles de cada proceso</span><span class="sxs-lookup"><span data-stu-id="9ec0b-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="9ec0b-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="9ec0b-338">Devuelve estadísticas de rendimiento del sistema (lectura/escritura de E/S, estadísticas de memoria etcetera.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="9ec0b-339">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-339">Return data</span></span>
* <span data-ttu-id="9ec0b-340">JSON con información del sistema: CPU, GPU, memoria, E/S y red</span><span class="sxs-lookup"><span data-stu-id="9ec0b-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="9ec0b-341">Alimentación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-341">Power</span></span>

<span data-ttu-id="9ec0b-342">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="9ec0b-343">Obtiene el estado actual de la batería</span><span class="sxs-lookup"><span data-stu-id="9ec0b-343">Gets the current battery state</span></span>

<span data-ttu-id="9ec0b-344">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="9ec0b-345">Comprueba si el sistema está en un estado de bajo consumo de energía</span><span class="sxs-lookup"><span data-stu-id="9ec0b-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="9ec0b-346">Control remoto</span><span class="sxs-lookup"><span data-stu-id="9ec0b-346">Remote Control</span></span>

<span data-ttu-id="9ec0b-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="9ec0b-348">Reinicia el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="9ec0b-348">Restarts the target device</span></span>

<span data-ttu-id="9ec0b-349">**/API/control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="9ec0b-350">Apaga el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="9ec0b-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="9ec0b-351">Administrador de tareas</span><span class="sxs-lookup"><span data-stu-id="9ec0b-351">Task Manager</span></span>

<span data-ttu-id="9ec0b-352">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="9ec0b-353">Detiene una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="9ec0b-353">Stops a modern app</span></span>

<span data-ttu-id="9ec0b-354">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-354">Parameters</span></span>
* <span data-ttu-id="9ec0b-355">paquete: Nombre completo del paquete de aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="9ec0b-356">forzar detención: Forzar que detener todos los procesos (= yes)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="9ec0b-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="9ec0b-358">Se inicia una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="9ec0b-358">Starts a modern app</span></span>

<span data-ttu-id="9ec0b-359">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-359">Parameters</span></span>
* <span data-ttu-id="9ec0b-360">AppID: PRAID de aplicación para iniciar, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="9ec0b-361">paquete: Nombre completo del paquete de aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="9ec0b-362">Administración de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="9ec0b-362">WiFi Management</span></span>

<span data-ttu-id="9ec0b-363">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="9ec0b-364">Enumera las interfaces de red inalámbrica</span><span class="sxs-lookup"><span data-stu-id="9ec0b-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="9ec0b-365">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-365">Return data</span></span>
* <span data-ttu-id="9ec0b-366">Lista de interfaces inalámbricas con detalles (GUID), descripción, etcetera.)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="9ec0b-367">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="9ec0b-368">Elimina un perfil asociado a una red en una interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="9ec0b-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="9ec0b-369">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-369">Parameters</span></span>
* <span data-ttu-id="9ec0b-370">interfaz: guid de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="9ec0b-370">interface : network interface guid</span></span>
* <span data-ttu-id="9ec0b-371">perfil: nombre de perfil</span><span class="sxs-lookup"><span data-stu-id="9ec0b-371">profile : profile name</span></span>

<span data-ttu-id="9ec0b-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="9ec0b-373">Enumera las redes inalámbricas en la interfaz de red especificado</span><span class="sxs-lookup"><span data-stu-id="9ec0b-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="9ec0b-374">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-374">Parameters</span></span>
* <span data-ttu-id="9ec0b-375">interfaz: guid de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="9ec0b-375">interface : network interface guid</span></span>

<span data-ttu-id="9ec0b-376">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-376">Return data</span></span>
* <span data-ttu-id="9ec0b-377">Lista de redes inalámbricas que se encuentra en la interfaz de red con los detalles</span><span class="sxs-lookup"><span data-stu-id="9ec0b-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="9ec0b-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="9ec0b-379">Se conecta o desconecta a una red en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="9ec0b-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="9ec0b-380">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-380">Parameters</span></span>
* <span data-ttu-id="9ec0b-381">interfaz: guid de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="9ec0b-381">interface : network interface guid</span></span>
* <span data-ttu-id="9ec0b-382">SSID: ssid, hex64 codificado para conectarse a</span><span class="sxs-lookup"><span data-stu-id="9ec0b-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="9ec0b-383">OP: conectar o desconectar</span><span class="sxs-lookup"><span data-stu-id="9ec0b-383">op : connect or disconnect</span></span>
* <span data-ttu-id="9ec0b-384">CreateProfile: yes o no</span><span class="sxs-lookup"><span data-stu-id="9ec0b-384">createprofile : yes or no</span></span>
* <span data-ttu-id="9ec0b-385">clave: hex64 clave, compartidos con codificación</span><span class="sxs-lookup"><span data-stu-id="9ec0b-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="9ec0b-386">Grabadora de rendimiento de Windows</span><span class="sxs-lookup"><span data-stu-id="9ec0b-386">Windows Performance Recorder</span></span>

<span data-ttu-id="9ec0b-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="9ec0b-388">Carga un perfil WPR e inicia el seguimiento con el perfil cargado.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="9ec0b-389">carga</span><span class="sxs-lookup"><span data-stu-id="9ec0b-389">Payload</span></span>
* <span data-ttu-id="9ec0b-390">cuerpo de http que cumplan varias partes</span><span class="sxs-lookup"><span data-stu-id="9ec0b-390">multi-part conforming http body</span></span>

<span data-ttu-id="9ec0b-391">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-391">Return data</span></span>
* <span data-ttu-id="9ec0b-392">Devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-392">Returns the WPR session status.</span></span>

<span data-ttu-id="9ec0b-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="9ec0b-394">Recupera el estado de la sesión WPR</span><span class="sxs-lookup"><span data-stu-id="9ec0b-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="9ec0b-395">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-395">Return data</span></span>
* <span data-ttu-id="9ec0b-396">Estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-396">WPR session status.</span></span>

<span data-ttu-id="9ec0b-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="9ec0b-398">Detiene una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="9ec0b-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="9ec0b-399">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-399">Return data</span></span>
* <span data-ttu-id="9ec0b-400">Devuelve el archivo ETL de seguimiento</span><span class="sxs-lookup"><span data-stu-id="9ec0b-400">Returns the trace ETL file</span></span>

<span data-ttu-id="9ec0b-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="9ec0b-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="9ec0b-402">Se inicia un WPR (rendimiento), las sesiones de seguimiento</span><span class="sxs-lookup"><span data-stu-id="9ec0b-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="9ec0b-403">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9ec0b-403">Parameters</span></span>
* <span data-ttu-id="9ec0b-404">perfil: Nombre del perfil.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-404">profile : Profile name.</span></span> <span data-ttu-id="9ec0b-405">Perfiles disponibles se almacenan en perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="9ec0b-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="9ec0b-406">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="9ec0b-406">Return data</span></span>
* <span data-ttu-id="9ec0b-407">Durante el inicio, se devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="9ec0b-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ec0b-408">Vea también</span><span class="sxs-lookup"><span data-stu-id="9ec0b-408">See also</span></span>
* [<span data-ttu-id="9ec0b-409">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="9ec0b-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="9ec0b-410">Núcleo de Portal de dispositivo (UWP) de referencia de API</span><span class="sxs-lookup"><span data-stu-id="9ec0b-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
