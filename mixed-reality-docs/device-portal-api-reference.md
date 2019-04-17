---
title: Referencia de la API del portal de dispositivos
description: Referencia de API para el Windows Device Portal en HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal, API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605372"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="472c2-104">Referencia de la API del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="472c2-104">Device portal API reference</span></span>

<span data-ttu-id="472c2-105">Todo el contenido de la [Windows Device Portal](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para acceder a los datos y controlar el dispositivo mediante programación.</span><span class="sxs-lookup"><span data-stu-id="472c2-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="472c2-106">Implementación de aplicación</span><span class="sxs-lookup"><span data-stu-id="472c2-106">App deloyment</span></span>

<span data-ttu-id="472c2-107">**/API/App/PackageManager/Package (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="472c2-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="472c2-108">Desinstala una aplicación</span><span class="sxs-lookup"><span data-stu-id="472c2-108">Uninstalls an app</span></span>

<span data-ttu-id="472c2-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-109">Parameters</span></span>
* <span data-ttu-id="472c2-110">paquete: Nombre de archivo del paquete que se puede desinstalar.</span><span class="sxs-lookup"><span data-stu-id="472c2-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="472c2-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="472c2-112">Instala una aplicación</span><span class="sxs-lookup"><span data-stu-id="472c2-112">Installs an App</span></span>

<span data-ttu-id="472c2-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-113">Parameters</span></span>
* <span data-ttu-id="472c2-114">paquete: Nombre de archivo del paquete de instalación.</span><span class="sxs-lookup"><span data-stu-id="472c2-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="472c2-115">carga</span><span class="sxs-lookup"><span data-stu-id="472c2-115">Payload</span></span>
* <span data-ttu-id="472c2-116">cuerpo de http que cumplan varias partes</span><span class="sxs-lookup"><span data-stu-id="472c2-116">multi-part conforming http body</span></span>

<span data-ttu-id="472c2-117">**/API/App/PackageManager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="472c2-118">Recupera la lista de las aplicaciones instaladas en el sistema, con detalles</span><span class="sxs-lookup"><span data-stu-id="472c2-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="472c2-119">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-119">Return data</span></span>
* <span data-ttu-id="472c2-120">Lista de paquetes instalados con detalles</span><span class="sxs-lookup"><span data-stu-id="472c2-120">List of installed packages with details</span></span>

<span data-ttu-id="472c2-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="472c2-122">Obtiene el estado de en la instalación de la aplicación de progreso</span><span class="sxs-lookup"><span data-stu-id="472c2-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="472c2-123">Colección de volcados de memoria</span><span class="sxs-lookup"><span data-stu-id="472c2-123">Dump collection</span></span>

<span data-ttu-id="472c2-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="472c2-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="472c2-125">Deshabilita el bloqueo recopilación del volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="472c2-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="472c2-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-126">Parameters</span></span>
* <span data-ttu-id="472c2-127">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="472c2-127">packageFullname : package name</span></span>

<span data-ttu-id="472c2-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="472c2-129">Obtiene colección de volcados de configuración de aplicaciones con instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="472c2-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="472c2-130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-130">Parameters</span></span>
* <span data-ttu-id="472c2-131">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="472c2-131">packageFullname : package name</span></span>

<span data-ttu-id="472c2-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="472c2-133">Habilita y establece la configuración de control de volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="472c2-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="472c2-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-134">Parameters</span></span>
* <span data-ttu-id="472c2-135">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="472c2-135">packageFullname : package name</span></span>

<span data-ttu-id="472c2-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="472c2-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="472c2-137">Elimina un volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="472c2-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="472c2-138">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-138">Parameters</span></span>
* <span data-ttu-id="472c2-139">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="472c2-139">packageFullname : package name</span></span>
* <span data-ttu-id="472c2-140">nombre de archivo: nombre de archivo de volcado de memoria</span><span class="sxs-lookup"><span data-stu-id="472c2-140">fileName : dump file name</span></span>

<span data-ttu-id="472c2-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="472c2-142">Recupera un volcado de memoria para una aplicación de instalación de prueba</span><span class="sxs-lookup"><span data-stu-id="472c2-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="472c2-143">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-143">Parameters</span></span>
* <span data-ttu-id="472c2-144">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="472c2-144">packageFullname : package name</span></span>
* <span data-ttu-id="472c2-145">nombre de archivo: nombre de archivo de volcado de memoria</span><span class="sxs-lookup"><span data-stu-id="472c2-145">fileName : dump file name</span></span>

<span data-ttu-id="472c2-146">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-146">Return data</span></span>
* <span data-ttu-id="472c2-147">Archivo de volcado.</span><span class="sxs-lookup"><span data-stu-id="472c2-147">Dump file.</span></span> <span data-ttu-id="472c2-148">Inspeccionar con WinDbg o en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="472c2-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="472c2-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="472c2-150">Devuelve una lista de todos los volcados de memoria para las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="472c2-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="472c2-151">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-151">Return data</span></span>
* <span data-ttu-id="472c2-152">Vuelca la lista de bloqueo por aplicación cargada de lado</span><span class="sxs-lookup"><span data-stu-id="472c2-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="472c2-153">ETW</span><span class="sxs-lookup"><span data-stu-id="472c2-153">ETW</span></span>

<span data-ttu-id="472c2-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="472c2-155">Enumera los proveedores registrados</span><span class="sxs-lookup"><span data-stu-id="472c2-155">Enumerates registered providers</span></span>

<span data-ttu-id="472c2-156">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-156">Return data</span></span>
* <span data-ttu-id="472c2-157">Lista de proveedores, el nombre descriptivo y el GUID</span><span class="sxs-lookup"><span data-stu-id="472c2-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="472c2-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="472c2-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="472c2-159">Crea una sesión ETW en tiempo real; se administran a través de un websocket.</span><span class="sxs-lookup"><span data-stu-id="472c2-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="472c2-160">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-160">Return data</span></span>
* <span data-ttu-id="472c2-161">Eventos ETW de los proveedores habilitados</span><span class="sxs-lookup"><span data-stu-id="472c2-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="472c2-162">SO Holographic</span><span class="sxs-lookup"><span data-stu-id="472c2-162">Holographic OS</span></span>

<span data-ttu-id="472c2-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="472c2-164">Devuelve una lista de proveedores ETW específicos HoloLens que no están registrados con el sistema</span><span class="sxs-lookup"><span data-stu-id="472c2-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="472c2-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="472c2-166">Devuelve los Estados de todos los servicios en ejecución.</span><span class="sxs-lookup"><span data-stu-id="472c2-166">Returns the states of all services running.</span></span>

<span data-ttu-id="472c2-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="472c2-168">Obtiene la IPD almacenada (distancia Interpupillary) en milímetros</span><span class="sxs-lookup"><span data-stu-id="472c2-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="472c2-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="472c2-170">Establece la IPD</span><span class="sxs-lookup"><span data-stu-id="472c2-170">Sets the IPD</span></span>

<span data-ttu-id="472c2-171">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-171">Parameters</span></span>
* <span data-ttu-id="472c2-172">IPD: Nuevo valor IPD debe establecerse en milímetros</span><span class="sxs-lookup"><span data-stu-id="472c2-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="472c2-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="472c2-174">Obtener los requisitos de HTTPS para Device Portal</span><span class="sxs-lookup"><span data-stu-id="472c2-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="472c2-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="472c2-176">Establece los requisitos de HTTPS para el Portal de dispositivo</span><span class="sxs-lookup"><span data-stu-id="472c2-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="472c2-177">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-177">Parameters</span></span>
* <span data-ttu-id="472c2-178">requerido: Sí, no o el valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="472c2-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="472c2-179">Percepción holográfica</span><span class="sxs-lookup"><span data-stu-id="472c2-179">Holographic Perception</span></span>

<span data-ttu-id="472c2-180">**/API/holographic/Perception/Client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="472c2-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="472c2-181">Acepta las actualizaciones de websocket y ejecuta a un cliente de la percepción que envía actualizaciones a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="472c2-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="472c2-182">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-182">Parameters</span></span>
* <span data-ttu-id="472c2-183">clientmode: "activo" modo de seguimiento visual de fuerza cuando no se puede establecer de forma pasiva</span><span class="sxs-lookup"><span data-stu-id="472c2-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="472c2-184">Térmico holográfica</span><span class="sxs-lookup"><span data-stu-id="472c2-184">Holographic Thermal</span></span>

<span data-ttu-id="472c2-185">**/API/holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="472c2-186">Obtener la fase térmica del dispositivo (normal 0, 1 en caliente, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="472c2-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="472c2-187">Control de la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="472c2-187">Perception Simulation Control</span></span>

<span data-ttu-id="472c2-188">**/API/holographic/Simulation/control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="472c2-189">Obtener el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="472c2-189">Get the simulation mode</span></span>

<span data-ttu-id="472c2-190">**/API/holographic/Simulation/control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="472c2-191">Establecer el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="472c2-191">Set the simulation mode</span></span>

<span data-ttu-id="472c2-192">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-192">Parameters</span></span>
* <span data-ttu-id="472c2-193">modo: modo de simulación: de forma predeterminada, simulación, remoto, heredado</span><span class="sxs-lookup"><span data-stu-id="472c2-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="472c2-194">**/API/holographic/Simulation/control/Stream (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="472c2-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="472c2-195">Eliminar un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="472c2-195">Delete a control stream.</span></span>

<span data-ttu-id="472c2-196">**/API/holographic/Simulation/control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="472c2-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="472c2-197">Abra una conexión de socket web para un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="472c2-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="472c2-198">**/API/holographic/Simulation/control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="472c2-199">Crear un flujo de control (prioridad es necesaria) o publicar datos en un flujo creado (streamId necesario).</span><span class="sxs-lookup"><span data-stu-id="472c2-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="472c2-200">Datos enviados debe ser de tipo "application/octet-stream".</span><span class="sxs-lookup"><span data-stu-id="472c2-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="472c2-201">Reproducción de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="472c2-201">Perception Simulation Playback</span></span>

<span data-ttu-id="472c2-202">**/API/holographic/Simulation/Playback/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="472c2-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="472c2-203">Eliminar una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-203">Delete a recording.</span></span>

<span data-ttu-id="472c2-204">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-204">Parameters</span></span>
* <span data-ttu-id="472c2-205">grabación: Nombre de la grabación para eliminar.</span><span class="sxs-lookup"><span data-stu-id="472c2-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="472c2-206">**/API/holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="472c2-207">Cargue una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-207">Upload a recording.</span></span>

<span data-ttu-id="472c2-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="472c2-209">Obtener todas las grabaciones.</span><span class="sxs-lookup"><span data-stu-id="472c2-209">Get all recordings.</span></span>

<span data-ttu-id="472c2-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="472c2-211">Obtener el estado actual de la reproducción de una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="472c2-212">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-212">Parameters</span></span>
* <span data-ttu-id="472c2-213">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-213">recording : Name of recording.</span></span>

<span data-ttu-id="472c2-214">**/API/holographic/Simulation/Playback/Session/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="472c2-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="472c2-215">Descargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-215">Unload a recording.</span></span>

<span data-ttu-id="472c2-216">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-216">Parameters</span></span>
* <span data-ttu-id="472c2-217">grabación: Nombre de la grabación para descargar.</span><span class="sxs-lookup"><span data-stu-id="472c2-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="472c2-218">**/API/holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="472c2-219">Cargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-219">Load a recording.</span></span>

<span data-ttu-id="472c2-220">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-220">Parameters</span></span>
* <span data-ttu-id="472c2-221">grabación: Nombre de la grabación para cargar.</span><span class="sxs-lookup"><span data-stu-id="472c2-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="472c2-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="472c2-223">Obtener grabaciones cargadas.</span><span class="sxs-lookup"><span data-stu-id="472c2-223">Get all loaded recordings.</span></span>

<span data-ttu-id="472c2-224">**/API/holographic/Simulation/Playback/Session/Pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="472c2-225">Pausar una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-225">Pause a recording.</span></span>

<span data-ttu-id="472c2-226">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-226">Parameters</span></span>
* <span data-ttu-id="472c2-227">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-227">recording : Name of recording.</span></span>

<span data-ttu-id="472c2-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="472c2-229">Reproducir una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-229">Play a recording.</span></span>

<span data-ttu-id="472c2-230">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-230">Parameters</span></span>
* <span data-ttu-id="472c2-231">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-231">recording : Name of recording.</span></span>

<span data-ttu-id="472c2-232">**/API/holographic/Simulation/Playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="472c2-233">Detener la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-233">Stop a recording.</span></span>

<span data-ttu-id="472c2-234">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-234">Parameters</span></span>
* <span data-ttu-id="472c2-235">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-235">recording : Name of recording.</span></span>

<span data-ttu-id="472c2-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="472c2-237">Obtiene los tipos de datos en una grabación de carga.</span><span class="sxs-lookup"><span data-stu-id="472c2-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="472c2-238">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-238">Parameters</span></span>
* <span data-ttu-id="472c2-239">grabación: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="472c2-240">Grabación de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="472c2-240">Perception Simulation Recording</span></span>

<span data-ttu-id="472c2-241">**/API/holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="472c2-242">Iniciar una grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-242">Start a recording.</span></span> <span data-ttu-id="472c2-243">Solo puede estar activa una grabación única a la vez.</span><span class="sxs-lookup"><span data-stu-id="472c2-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="472c2-244">Debe establecerse un encabezado, manos, spatialMapping o entorno.</span><span class="sxs-lookup"><span data-stu-id="472c2-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="472c2-245">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-245">Parameters</span></span>
* <span data-ttu-id="472c2-246">principal: Establezca en 1 para datos de registro principal.</span><span class="sxs-lookup"><span data-stu-id="472c2-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="472c2-247">práctico: Se establece en 1 para registrar los datos disponibles.</span><span class="sxs-lookup"><span data-stu-id="472c2-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="472c2-248">spatialMapping: Se establece en 1 para registrar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="472c2-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="472c2-249">entorno: Se establece en 1 para registrar datos de entorno.</span><span class="sxs-lookup"><span data-stu-id="472c2-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="472c2-250">nombre: Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-250">name : Name of the recording.</span></span>
* <span data-ttu-id="472c2-251">singleSpatialMappingFrame: Se establece en 1 para registrar solo un marco de asignación espacial único.</span><span class="sxs-lookup"><span data-stu-id="472c2-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="472c2-252">**/API/holographic/Simulation/Recording/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="472c2-253">Obtener estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="472c2-253">Get recording state.</span></span>

<span data-ttu-id="472c2-254">**/API/holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="472c2-255">Detener la grabación actual.</span><span class="sxs-lookup"><span data-stu-id="472c2-255">Stop the current recording.</span></span> <span data-ttu-id="472c2-256">Grabación se devolverá como un archivo.</span><span class="sxs-lookup"><span data-stu-id="472c2-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="472c2-257">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="472c2-257">Mixed Reality Capture</span></span>

<span data-ttu-id="472c2-258">**/API/holographic/MRC/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="472c2-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="472c2-259">Elimina una grabación desde el dispositivo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="472c2-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="472c2-260">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-260">Parameters</span></span>
* <span data-ttu-id="472c2-261">nombre de archivo: El nombre, hex64 codificada del archivo para eliminar</span><span class="sxs-lookup"><span data-stu-id="472c2-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="472c2-262">**/API/holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="472c2-263">Obtiene el valor predeterminado la realidad mixta configuración de capture</span><span class="sxs-lookup"><span data-stu-id="472c2-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="472c2-264">**/API/holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="472c2-265">Descarga un archivo de realidad mixta desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="472c2-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="472c2-266">Op uso = parámetro de consulta de stream para streaming.</span><span class="sxs-lookup"><span data-stu-id="472c2-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="472c2-267">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-267">Parameters</span></span>
* <span data-ttu-id="472c2-268">nombre de archivo: El nombre, hex64 codificada del archivo de vídeo para obtener</span><span class="sxs-lookup"><span data-stu-id="472c2-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="472c2-269">op : stream</span><span class="sxs-lookup"><span data-stu-id="472c2-269">op : stream</span></span>

<span data-ttu-id="472c2-270">**/API/holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="472c2-271">Obtiene la imagen en miniatura para el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="472c2-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="472c2-272">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-272">Parameters</span></span>
* <span data-ttu-id="472c2-273">filename: El nombre, hex64 codificada del archivo para el que se solicita la miniatura</span><span class="sxs-lookup"><span data-stu-id="472c2-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="472c2-274">**/API/holographic/MRC/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="472c2-275">Obtiene el estado de la realidad mixta registran (está ejecutando, detenido)</span><span class="sxs-lookup"><span data-stu-id="472c2-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="472c2-276">**/API/holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="472c2-277">Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="472c2-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="472c2-278">**/API/holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="472c2-279">Establece el valor predeterminado la realidad mixta configuración de capture</span><span class="sxs-lookup"><span data-stu-id="472c2-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="472c2-280">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="472c2-281">Se inicia una grabación de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="472c2-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="472c2-282">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-282">Parameters</span></span>
* <span data-ttu-id="472c2-283">Holo: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="472c2-284">PV: cámara captura PV: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="472c2-285">MIC: captura de micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="472c2-286">bucle invertido: capturar audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="472c2-287">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="472c2-288">Se detiene la actual mixto grabación realidad</span><span class="sxs-lookup"><span data-stu-id="472c2-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="472c2-289">**/API/holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="472c2-290">Toma una fotografía de realidad mixta y crea un archivo en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="472c2-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="472c2-291">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-291">Parameters</span></span>
* <span data-ttu-id="472c2-292">Holo: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="472c2-293">PV: cámara captura PV: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="472c2-294">Realidad mixta de transmisión por secuencias</span><span class="sxs-lookup"><span data-stu-id="472c2-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="472c2-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="472c2-296">Inicia una descarga fragmentada de un archivo mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="472c2-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="472c2-297">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-297">Parameters</span></span>
* <span data-ttu-id="472c2-298">Holo: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="472c2-299">PV: cámara captura PV: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="472c2-300">MIC: captura de micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="472c2-301">bucle invertido: capturar audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="472c2-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="472c2-303">Inicia una descarga fragmentada de un archivo mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="472c2-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="472c2-304">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-304">Parameters</span></span>
* <span data-ttu-id="472c2-305">Holo: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="472c2-306">PV: cámara captura PV: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="472c2-307">MIC: captura de micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="472c2-308">bucle invertido: capturar audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="472c2-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="472c2-310">Inicia una descarga fragmentada de un archivo mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="472c2-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="472c2-311">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-311">Parameters</span></span>
* <span data-ttu-id="472c2-312">Holo: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="472c2-313">PV: cámara captura PV: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="472c2-314">MIC: captura de micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="472c2-315">bucle invertido: capturar audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="472c2-316">**/API/holographic/Stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="472c2-317">Inicia una descarga fragmentada de un archivo mp4 fragmentado</span><span class="sxs-lookup"><span data-stu-id="472c2-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="472c2-318">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-318">Parameters</span></span>
* <span data-ttu-id="472c2-319">Holo: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="472c2-320">PV: cámara captura PV: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="472c2-321">MIC: captura de micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="472c2-322">bucle invertido: capturar audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="472c2-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="472c2-323">Funciones de red</span><span class="sxs-lookup"><span data-stu-id="472c2-323">Networking</span></span>

<span data-ttu-id="472c2-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="472c2-325">Obtiene la configuración de ip actual</span><span class="sxs-lookup"><span data-stu-id="472c2-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="472c2-326">Información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="472c2-326">OS Information</span></span>

<span data-ttu-id="472c2-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="472c2-328">Obtiene la información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="472c2-328">Gets operating system information</span></span>

<span data-ttu-id="472c2-329">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="472c2-330">Obtiene el nombre del equipo</span><span class="sxs-lookup"><span data-stu-id="472c2-330">Gets the machine name</span></span>

<span data-ttu-id="472c2-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="472c2-332">Establece el nombre del equipo</span><span class="sxs-lookup"><span data-stu-id="472c2-332">Sets the machine name</span></span>

<span data-ttu-id="472c2-333">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-333">Parameters</span></span>
* <span data-ttu-id="472c2-334">nombre: Nuevo nombre de la máquina, hex64 codificado para establecer en</span><span class="sxs-lookup"><span data-stu-id="472c2-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="472c2-335">Datos de rendimiento</span><span class="sxs-lookup"><span data-stu-id="472c2-335">Performance data</span></span>

<span data-ttu-id="472c2-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="472c2-337">Devuelve la lista de procesos en ejecución con detalles</span><span class="sxs-lookup"><span data-stu-id="472c2-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="472c2-338">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-338">Return data</span></span>
* <span data-ttu-id="472c2-339">JSON con la lista de procesos y los detalles de cada proceso</span><span class="sxs-lookup"><span data-stu-id="472c2-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="472c2-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="472c2-341">Devuelve estadísticas de rendimiento del sistema (lectura/escritura de E/S, estadísticas de memoria etcetera.</span><span class="sxs-lookup"><span data-stu-id="472c2-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="472c2-342">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-342">Return data</span></span>
* <span data-ttu-id="472c2-343">JSON con información del sistema: CPU, GPU, memoria, E/S y red</span><span class="sxs-lookup"><span data-stu-id="472c2-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="472c2-344">Alimentación</span><span class="sxs-lookup"><span data-stu-id="472c2-344">Power</span></span>

<span data-ttu-id="472c2-345">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="472c2-346">Obtiene el estado actual de la batería</span><span class="sxs-lookup"><span data-stu-id="472c2-346">Gets the current battery state</span></span>

<span data-ttu-id="472c2-347">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="472c2-348">Comprueba si el sistema está en un estado de bajo consumo de energía</span><span class="sxs-lookup"><span data-stu-id="472c2-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="472c2-349">Control remoto</span><span class="sxs-lookup"><span data-stu-id="472c2-349">Remote Control</span></span>

<span data-ttu-id="472c2-350">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="472c2-351">Reinicia el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="472c2-351">Restarts the target device</span></span>

<span data-ttu-id="472c2-352">**/API/control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="472c2-353">Apaga el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="472c2-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="472c2-354">Administrador de tareas</span><span class="sxs-lookup"><span data-stu-id="472c2-354">Task Manager</span></span>

<span data-ttu-id="472c2-355">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="472c2-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="472c2-356">Detiene una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="472c2-356">Stops a modern app</span></span>

<span data-ttu-id="472c2-357">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-357">Parameters</span></span>
* <span data-ttu-id="472c2-358">paquete: Nombre completo del paquete de aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="472c2-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="472c2-359">forzar detención: Forzar que detener todos los procesos (= yes)</span><span class="sxs-lookup"><span data-stu-id="472c2-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="472c2-360">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="472c2-361">Se inicia una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="472c2-361">Starts a modern app</span></span>

<span data-ttu-id="472c2-362">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-362">Parameters</span></span>
* <span data-ttu-id="472c2-363">AppID: PRAID de aplicación para iniciar, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="472c2-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="472c2-364">paquete: Nombre completo del paquete de aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="472c2-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="472c2-365">Administración de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="472c2-365">WiFi Management</span></span>

<span data-ttu-id="472c2-366">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="472c2-367">Enumera las interfaces de red inalámbrica</span><span class="sxs-lookup"><span data-stu-id="472c2-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="472c2-368">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-368">Return data</span></span>
* <span data-ttu-id="472c2-369">Lista de interfaces inalámbricas con detalles (GUID), descripción, etcetera.)</span><span class="sxs-lookup"><span data-stu-id="472c2-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="472c2-370">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="472c2-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="472c2-371">Elimina un perfil asociado a una red en una interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="472c2-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="472c2-372">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-372">Parameters</span></span>
* <span data-ttu-id="472c2-373">interfaz: guid de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="472c2-373">interface : network interface guid</span></span>
* <span data-ttu-id="472c2-374">perfil: nombre de perfil</span><span class="sxs-lookup"><span data-stu-id="472c2-374">profile : profile name</span></span>

<span data-ttu-id="472c2-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="472c2-376">Enumera las redes inalámbricas en la interfaz de red especificado</span><span class="sxs-lookup"><span data-stu-id="472c2-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="472c2-377">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-377">Parameters</span></span>
* <span data-ttu-id="472c2-378">interfaz: guid de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="472c2-378">interface : network interface guid</span></span>

<span data-ttu-id="472c2-379">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-379">Return data</span></span>
* <span data-ttu-id="472c2-380">Lista de redes inalámbricas que se encuentra en la interfaz de red con los detalles</span><span class="sxs-lookup"><span data-stu-id="472c2-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="472c2-381">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="472c2-382">Se conecta o desconecta a una red en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="472c2-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="472c2-383">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-383">Parameters</span></span>
* <span data-ttu-id="472c2-384">interfaz: guid de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="472c2-384">interface : network interface guid</span></span>
* <span data-ttu-id="472c2-385">SSID: ssid, hex64 codificado para conectarse a</span><span class="sxs-lookup"><span data-stu-id="472c2-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="472c2-386">OP: conectar o desconectar</span><span class="sxs-lookup"><span data-stu-id="472c2-386">op : connect or disconnect</span></span>
* <span data-ttu-id="472c2-387">CreateProfile: yes o no</span><span class="sxs-lookup"><span data-stu-id="472c2-387">createprofile : yes or no</span></span>
* <span data-ttu-id="472c2-388">clave: hex64 clave, compartidos con codificación</span><span class="sxs-lookup"><span data-stu-id="472c2-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="472c2-389">Grabadora de rendimiento de Windows</span><span class="sxs-lookup"><span data-stu-id="472c2-389">Windows Performance Recorder</span></span>

<span data-ttu-id="472c2-390">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="472c2-391">Carga un perfil WPR e inicia el seguimiento con el perfil cargado.</span><span class="sxs-lookup"><span data-stu-id="472c2-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="472c2-392">carga</span><span class="sxs-lookup"><span data-stu-id="472c2-392">Payload</span></span>
* <span data-ttu-id="472c2-393">cuerpo de http que cumplan varias partes</span><span class="sxs-lookup"><span data-stu-id="472c2-393">multi-part conforming http body</span></span>

<span data-ttu-id="472c2-394">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-394">Return data</span></span>
* <span data-ttu-id="472c2-395">Devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="472c2-395">Returns the WPR session status.</span></span>

<span data-ttu-id="472c2-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="472c2-397">Recupera el estado de la sesión WPR</span><span class="sxs-lookup"><span data-stu-id="472c2-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="472c2-398">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-398">Return data</span></span>
* <span data-ttu-id="472c2-399">Estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="472c2-399">WPR session status.</span></span>

<span data-ttu-id="472c2-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="472c2-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="472c2-401">Detiene una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="472c2-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="472c2-402">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-402">Return data</span></span>
* <span data-ttu-id="472c2-403">Devuelve el archivo ETL de seguimiento</span><span class="sxs-lookup"><span data-stu-id="472c2-403">Returns the trace ETL file</span></span>

<span data-ttu-id="472c2-404">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="472c2-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="472c2-405">Se inicia un WPR (rendimiento), las sesiones de seguimiento</span><span class="sxs-lookup"><span data-stu-id="472c2-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="472c2-406">Parámetros</span><span class="sxs-lookup"><span data-stu-id="472c2-406">Parameters</span></span>
* <span data-ttu-id="472c2-407">perfil: Nombre del perfil.</span><span class="sxs-lookup"><span data-stu-id="472c2-407">profile : Profile name.</span></span> <span data-ttu-id="472c2-408">Perfiles disponibles se almacenan en perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="472c2-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="472c2-409">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="472c2-409">Return data</span></span>
* <span data-ttu-id="472c2-410">Durante el inicio, se devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="472c2-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="472c2-411">Vea también</span><span class="sxs-lookup"><span data-stu-id="472c2-411">See also</span></span>
* [<span data-ttu-id="472c2-412">Uso de la Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="472c2-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="472c2-413">Núcleo de Portal de dispositivo (UWP) de referencia de API</span><span class="sxs-lookup"><span data-stu-id="472c2-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
