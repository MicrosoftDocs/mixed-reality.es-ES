---
title: Referencia de la API del portal de dispositivos
description: Referencia de API para Windows Device portal en HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portal de dispositivos de Windows, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694436"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="b877e-104">Referencia de la API del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="b877e-104">Device portal API reference</span></span>

<span data-ttu-id="b877e-105">Todo lo que se encuentra en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para tener acceso a los datos y controlar el dispositivo mediante programación.</span><span class="sxs-lookup"><span data-stu-id="b877e-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="b877e-106">Implementación de aplicación</span><span class="sxs-lookup"><span data-stu-id="b877e-106">App deloyment</span></span>

<span data-ttu-id="b877e-107">**/API/App/packagemanager/Package (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="b877e-108">Desinstala una aplicación</span><span class="sxs-lookup"><span data-stu-id="b877e-108">Uninstalls an app</span></span>

<span data-ttu-id="b877e-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-109">Parameters</span></span>
* <span data-ttu-id="b877e-110">configura Nombre de archivo del paquete que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="b877e-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="b877e-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="b877e-112">Instala una aplicación</span><span class="sxs-lookup"><span data-stu-id="b877e-112">Installs an App</span></span>

<span data-ttu-id="b877e-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-113">Parameters</span></span>
* <span data-ttu-id="b877e-114">configura Nombre de archivo del paquete que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="b877e-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="b877e-115">Útiles</span><span class="sxs-lookup"><span data-stu-id="b877e-115">Payload</span></span>
* <span data-ttu-id="b877e-116">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="b877e-116">multi-part conforming http body</span></span>

<span data-ttu-id="b877e-117">**/API/App/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="b877e-118">Recupera la lista de aplicaciones instaladas en el sistema con detalles</span><span class="sxs-lookup"><span data-stu-id="b877e-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="b877e-119">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-119">Return data</span></span>
* <span data-ttu-id="b877e-120">Lista de paquetes instalados con detalles</span><span class="sxs-lookup"><span data-stu-id="b877e-120">List of installed packages with details</span></span>

<span data-ttu-id="b877e-121">**/API/App/packagemanager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="b877e-122">Obtiene el estado de la instalación de la aplicación en curso</span><span class="sxs-lookup"><span data-stu-id="b877e-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="b877e-123">Colección de volcados de memoria</span><span class="sxs-lookup"><span data-stu-id="b877e-123">Dump collection</span></span>

<span data-ttu-id="b877e-124">**/API/Debug/dump/usermode/CrashControl (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="b877e-125">Deshabilita la recopilación de volcados de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="b877e-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="b877e-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-126">Parameters</span></span>
* <span data-ttu-id="b877e-127">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="b877e-127">packageFullname : package name</span></span>

<span data-ttu-id="b877e-128">**/API/Debug/dump/usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="b877e-129">Obtiene la configuración de la colección de volcados de memoria de aplicaciones transferidas</span><span class="sxs-lookup"><span data-stu-id="b877e-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="b877e-130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-130">Parameters</span></span>
* <span data-ttu-id="b877e-131">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="b877e-131">packageFullname : package name</span></span>

<span data-ttu-id="b877e-132">**/API/Debug/dump/usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="b877e-133">Habilita y establece la configuración de control de volcado para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="b877e-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="b877e-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-134">Parameters</span></span>
* <span data-ttu-id="b877e-135">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="b877e-135">packageFullname : package name</span></span>

<span data-ttu-id="b877e-136">**/API/Debug/dump/usermode/crashdump (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="b877e-137">Elimina un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="b877e-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="b877e-138">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-138">Parameters</span></span>
* <span data-ttu-id="b877e-139">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="b877e-139">packageFullname : package name</span></span>
* <span data-ttu-id="b877e-140">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="b877e-140">fileName : dump file name</span></span>

<span data-ttu-id="b877e-141">**/API/Debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="b877e-142">Recupera un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="b877e-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="b877e-143">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-143">Parameters</span></span>
* <span data-ttu-id="b877e-144">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="b877e-144">packageFullname : package name</span></span>
* <span data-ttu-id="b877e-145">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="b877e-145">fileName : dump file name</span></span>

<span data-ttu-id="b877e-146">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-146">Return data</span></span>
* <span data-ttu-id="b877e-147">Archivo de volcado de memoria.</span><span class="sxs-lookup"><span data-stu-id="b877e-147">Dump file.</span></span> <span data-ttu-id="b877e-148">Inspeccionar con WinDbg o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b877e-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="b877e-149">**/API/Debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="b877e-150">Devuelve la lista de todos los volcados de memoria de las aplicaciones transferidas localmente</span><span class="sxs-lookup"><span data-stu-id="b877e-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="b877e-151">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-151">Return data</span></span>
* <span data-ttu-id="b877e-152">Lista de volcados de memoria por aplicación cargada</span><span class="sxs-lookup"><span data-stu-id="b877e-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="b877e-153">ETW</span><span class="sxs-lookup"><span data-stu-id="b877e-153">ETW</span></span>

<span data-ttu-id="b877e-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="b877e-155">Enumera los proveedores registrados</span><span class="sxs-lookup"><span data-stu-id="b877e-155">Enumerates registered providers</span></span>

<span data-ttu-id="b877e-156">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-156">Return data</span></span>
* <span data-ttu-id="b877e-157">Lista de proveedores, nombre descriptivo y GUID</span><span class="sxs-lookup"><span data-stu-id="b877e-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="b877e-158">**/API/ETW/Session/Realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b877e-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="b877e-159">Crea una sesión ETW en tiempo real; se administra a través de un WebSocket.</span><span class="sxs-lookup"><span data-stu-id="b877e-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="b877e-160">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-160">Return data</span></span>
* <span data-ttu-id="b877e-161">Eventos ETW de los proveedores habilitados</span><span class="sxs-lookup"><span data-stu-id="b877e-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="b877e-162">SO Holographic</span><span class="sxs-lookup"><span data-stu-id="b877e-162">Holographic OS</span></span>

<span data-ttu-id="b877e-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="b877e-164">Devuelve una lista de proveedores ETW específicos de HoloLens que no están registrados en el sistema.</span><span class="sxs-lookup"><span data-stu-id="b877e-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="b877e-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="b877e-166">Devuelve los Estados de todos los servicios que se están ejecutando.</span><span class="sxs-lookup"><span data-stu-id="b877e-166">Returns the states of all services running.</span></span>

<span data-ttu-id="b877e-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="b877e-168">Obtiene el IPD almacenado (distancia interpupillary) en milímetros.</span><span class="sxs-lookup"><span data-stu-id="b877e-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="b877e-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="b877e-170">Establece la configuración de IPD</span><span class="sxs-lookup"><span data-stu-id="b877e-170">Sets the IPD</span></span>

<span data-ttu-id="b877e-171">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-171">Parameters</span></span>
* <span data-ttu-id="b877e-172">IPD Nuevo valor de IPD que se establecerá en milímetros</span><span class="sxs-lookup"><span data-stu-id="b877e-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="b877e-173">**/API/Holographic/os/webmanagement/Settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="b877e-174">Obtener los requisitos de HTTPS para Device Portal</span><span class="sxs-lookup"><span data-stu-id="b877e-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="b877e-175">**/API/Holographic/os/webmanagement/Settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="b877e-176">Establece los requisitos de HTTPS para el portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="b877e-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="b877e-177">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-177">Parameters</span></span>
* <span data-ttu-id="b877e-178">requerido: sí, no o predeterminado</span><span class="sxs-lookup"><span data-stu-id="b877e-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="b877e-179">Percepción holográfica</span><span class="sxs-lookup"><span data-stu-id="b877e-179">Holographic Perception</span></span>

<span data-ttu-id="b877e-180">**/API/Holographic/Perception/Client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b877e-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="b877e-181">Acepta actualizaciones de WebSocket y ejecuta un cliente de percepción que envía actualizaciones a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="b877e-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="b877e-182">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-182">Parameters</span></span>
* <span data-ttu-id="b877e-183">clientmode: "Active" fuerza el modo de seguimiento visual cuando no se puede establecer de forma pasiva</span><span class="sxs-lookup"><span data-stu-id="b877e-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="b877e-184">Temperatura térmica holográfica</span><span class="sxs-lookup"><span data-stu-id="b877e-184">Holographic Thermal</span></span>

<span data-ttu-id="b877e-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="b877e-186">Obtener la fase térmica del dispositivo (0 normal, 1 cálido, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="b877e-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="b877e-187">Control de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="b877e-187">Perception Simulation Control</span></span>

<span data-ttu-id="b877e-188">**/API/Holographic/Simulation/control/MODE (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="b877e-189">Obtención del modo de simulación</span><span class="sxs-lookup"><span data-stu-id="b877e-189">Get the simulation mode</span></span>

<span data-ttu-id="b877e-190">**/API/Holographic/Simulation/control/MODE (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="b877e-191">Establecer el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="b877e-191">Set the simulation mode</span></span>

<span data-ttu-id="b877e-192">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-192">Parameters</span></span>
* <span data-ttu-id="b877e-193">modo de simulación: predeterminado, simulación, remoto, heredado</span><span class="sxs-lookup"><span data-stu-id="b877e-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="b877e-194">**/API/Holographic/Simulation/control/Stream (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="b877e-195">Elimine un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="b877e-195">Delete a control stream.</span></span>

<span data-ttu-id="b877e-196">**/API/Holographic/Simulation/control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b877e-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="b877e-197">Abra una conexión de socket web para un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="b877e-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="b877e-198">**/API/Holographic/Simulation/control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="b877e-199">Cree un flujo de control (se requiere prioridad) o publique los datos en un flujo creado (streamId obligatorio).</span><span class="sxs-lookup"><span data-stu-id="b877e-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="b877e-200">Se espera que los datos expuestos sean del tipo "application/octet-stream".</span><span class="sxs-lookup"><span data-stu-id="b877e-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="b877e-201">Reproducción de la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="b877e-201">Perception Simulation Playback</span></span>

<span data-ttu-id="b877e-202">**/API/Holographic/Simulation/Playback/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="b877e-203">Elimina una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-203">Delete a recording.</span></span>

<span data-ttu-id="b877e-204">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-204">Parameters</span></span>
* <span data-ttu-id="b877e-205">musicales Nombre de la grabación que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="b877e-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="b877e-206">**/API/Holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="b877e-207">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-207">Upload a recording.</span></span>

<span data-ttu-id="b877e-208">**/API/Holographic/Simulation/Playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="b877e-209">Obtener todas las grabaciones.</span><span class="sxs-lookup"><span data-stu-id="b877e-209">Get all recordings.</span></span>

<span data-ttu-id="b877e-210">**/API/Holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="b877e-211">Obtiene el estado de reproducción actual de una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="b877e-212">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-212">Parameters</span></span>
* <span data-ttu-id="b877e-213">musicales Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-213">recording : Name of recording.</span></span>

<span data-ttu-id="b877e-214">**/API/Holographic/Simulation/Playback/Session/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="b877e-215">Descargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-215">Unload a recording.</span></span>

<span data-ttu-id="b877e-216">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-216">Parameters</span></span>
* <span data-ttu-id="b877e-217">musicales Nombre de la grabación que se va a descargar.</span><span class="sxs-lookup"><span data-stu-id="b877e-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="b877e-218">**/API/Holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="b877e-219">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-219">Load a recording.</span></span>

<span data-ttu-id="b877e-220">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-220">Parameters</span></span>
* <span data-ttu-id="b877e-221">musicales Nombre de la grabación que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="b877e-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="b877e-222">**/API/Holographic/Simulation/Playback/Session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="b877e-223">Obtiene todas las grabaciones cargadas.</span><span class="sxs-lookup"><span data-stu-id="b877e-223">Get all loaded recordings.</span></span>

<span data-ttu-id="b877e-224">**/API/Holographic/Simulation/Playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="b877e-225">Pausar una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-225">Pause a recording.</span></span>

<span data-ttu-id="b877e-226">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-226">Parameters</span></span>
* <span data-ttu-id="b877e-227">musicales Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-227">recording : Name of recording.</span></span>

<span data-ttu-id="b877e-228">**/API/Holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="b877e-229">Reproducir una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-229">Play a recording.</span></span>

<span data-ttu-id="b877e-230">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-230">Parameters</span></span>
* <span data-ttu-id="b877e-231">musicales Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-231">recording : Name of recording.</span></span>

<span data-ttu-id="b877e-232">**/API/Holographic/Simulation/Playback/Session/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="b877e-233">Detener una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-233">Stop a recording.</span></span>

<span data-ttu-id="b877e-234">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-234">Parameters</span></span>
* <span data-ttu-id="b877e-235">musicales Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-235">recording : Name of recording.</span></span>

<span data-ttu-id="b877e-236">**/API/Holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="b877e-237">Obtiene los tipos de datos en una grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="b877e-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="b877e-238">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-238">Parameters</span></span>
* <span data-ttu-id="b877e-239">musicales Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="b877e-240">Grabación de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="b877e-240">Perception Simulation Recording</span></span>

<span data-ttu-id="b877e-241">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="b877e-242">Iniciar una grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-242">Start a recording.</span></span> <span data-ttu-id="b877e-243">Solo puede haber una grabación activa al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="b877e-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="b877e-244">Debe establecerse una de las clases Head, Hand, spatialMapping o Environment.</span><span class="sxs-lookup"><span data-stu-id="b877e-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="b877e-245">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-245">Parameters</span></span>
* <span data-ttu-id="b877e-246">Head Establézcalo en 1 para registrar los datos principales.</span><span class="sxs-lookup"><span data-stu-id="b877e-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="b877e-247">útiles Establézcalo en 1 para registrar los datos de la mano.</span><span class="sxs-lookup"><span data-stu-id="b877e-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="b877e-248">spatialMapping : Establézcalo en 1 para registrar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="b877e-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="b877e-249">entorno Establézcalo en 1 para registrar los datos del entorno.</span><span class="sxs-lookup"><span data-stu-id="b877e-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="b877e-250">Name Nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-250">name : Name of the recording.</span></span>
* <span data-ttu-id="b877e-251">singleSpatialMappingFrame : Establézcalo en 1 para registrar solo un marco de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="b877e-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="b877e-252">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="b877e-253">Obtiene el estado de grabación.</span><span class="sxs-lookup"><span data-stu-id="b877e-253">Get recording state.</span></span>

<span data-ttu-id="b877e-254">**/API/Holographic/Simulation/Recording/STOP (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="b877e-255">Detener la grabación actual.</span><span class="sxs-lookup"><span data-stu-id="b877e-255">Stop the current recording.</span></span> <span data-ttu-id="b877e-256">La grabación se devolverá como un archivo.</span><span class="sxs-lookup"><span data-stu-id="b877e-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="b877e-257">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b877e-257">Mixed Reality Capture</span></span>

<span data-ttu-id="b877e-258">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="b877e-259">Descarga un archivo de realidad mixta desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b877e-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="b877e-260">Use OP = parámetro de consulta de transmisión por secuencias.</span><span class="sxs-lookup"><span data-stu-id="b877e-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="b877e-261">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-261">Parameters</span></span>
* <span data-ttu-id="b877e-262">extensión Nombre, hex64 codificado, del archivo de vídeo que se va a obtener</span><span class="sxs-lookup"><span data-stu-id="b877e-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="b877e-263">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="b877e-263">op : stream</span></span>

<span data-ttu-id="b877e-264">**/API/Holographic/MRC/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="b877e-265">Elimina una grabación de realidad mixta del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b877e-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="b877e-266">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-266">Parameters</span></span>
* <span data-ttu-id="b877e-267">extensión Nombre, hex64 codificado, del archivo que se va a eliminar</span><span class="sxs-lookup"><span data-stu-id="b877e-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="b877e-268">**/API/Holographic/MRC/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="b877e-269">Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="b877e-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="b877e-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="b877e-271">Toma una fotografía de realidad mixta y crea un archivo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b877e-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="b877e-272">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-272">Parameters</span></span>
* <span data-ttu-id="b877e-273">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="b877e-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="b877e-274">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="b877e-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="b877e-275">RenderFromCamera : (Solo HoloLens 2) representar desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="b877e-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="b877e-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="b877e-277">Obtiene la configuración de captura de realidad mixta predeterminada</span><span class="sxs-lookup"><span data-stu-id="b877e-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="b877e-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="b877e-279">Establece la configuración de captura de realidad mixta predeterminada.</span><span class="sxs-lookup"><span data-stu-id="b877e-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="b877e-280">Algunos de estos valores se aplican a la captura de vídeo y fotos de MRC del sistema.</span><span class="sxs-lookup"><span data-stu-id="b877e-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="b877e-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="b877e-282">Obtiene el estado de la realidad mixta grabada (en ejecución, detenida)</span><span class="sxs-lookup"><span data-stu-id="b877e-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="b877e-283">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="b877e-284">Obtiene la imagen en miniatura del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="b877e-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="b877e-285">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-285">Parameters</span></span>
* <span data-ttu-id="b877e-286">extensión Nombre, hex64 codificado, del archivo para el que se solicita la miniatura</span><span class="sxs-lookup"><span data-stu-id="b877e-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="b877e-287">**/API/Holographic/MRC/video/control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="b877e-288">Inicia una grabación de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b877e-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="b877e-289">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-289">Parameters</span></span>
* <span data-ttu-id="b877e-290">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="b877e-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="b877e-291">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="b877e-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="b877e-292">MIC: Capture Microphone: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="b877e-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="b877e-293">bucle invertido: captura de audio de la aplicación: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="b877e-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="b877e-294">RenderFromCamera : (Solo HoloLens 2) representar desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="b877e-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="b877e-295">vstab : (Solo HoloLens 2) habilitar la estabilización de vídeo: true o false (el valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="b877e-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="b877e-296">vstabbuffer: (Solo HoloLens 2) latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="b877e-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="b877e-297">**/API/Holographic/MRC/video/control/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="b877e-298">Detiene la grabación de realidad mixta actual</span><span class="sxs-lookup"><span data-stu-id="b877e-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="b877e-299">Streaming de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b877e-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="b877e-300">HoloLens admite la vista previa dinámica de la realidad mixta a través de la descarga fragmentada de un MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="b877e-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="b877e-301">Los flujos de realidad mixta comparten el mismo conjunto de parámetros para controlar lo que se captura:</span><span class="sxs-lookup"><span data-stu-id="b877e-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="b877e-302">hololens: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="b877e-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="b877e-303">PV: capturar la cámara PV: true o false</span><span class="sxs-lookup"><span data-stu-id="b877e-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="b877e-304">MIC: capturar micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="b877e-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="b877e-305">bucle invertido: captura de audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="b877e-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="b877e-306">Si no se especifica ninguno de estos: los hologramas, la cámara de foto/vídeo y el audio de la aplicación se capturarán</span><span class="sxs-lookup"><span data-stu-id="b877e-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="b877e-307">Si se especifica any: los parámetros no especificados tendrán como valor predeterminado False.</span><span class="sxs-lookup"><span data-stu-id="b877e-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="b877e-308">Parámetros opcionales (solo HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="b877e-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="b877e-309">RenderFromCamera: representación de la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="b877e-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="b877e-310">Vstab: habilitar estabilización de vídeo: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="b877e-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="b877e-311">vstabbuffer: latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="b877e-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="b877e-312">**/API/Holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="b877e-313">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="b877e-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="b877e-314">**/API/Holographic/Stream/live_high.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="b877e-315">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="b877e-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="b877e-316">**/API/Holographic/Stream/live_med.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="b877e-317">Una secuencia de 854x480p 30 fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="b877e-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="b877e-318">**/API/Holographic/Stream/live_low.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="b877e-319">Una secuencia de 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="b877e-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="b877e-320">Redes</span><span class="sxs-lookup"><span data-stu-id="b877e-320">Networking</span></span>

<span data-ttu-id="b877e-321">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="b877e-322">Obtiene la configuración de IP actual.</span><span class="sxs-lookup"><span data-stu-id="b877e-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="b877e-323">Información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="b877e-323">OS Information</span></span>

<span data-ttu-id="b877e-324">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="b877e-325">Obtiene información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="b877e-325">Gets operating system information</span></span>

<span data-ttu-id="b877e-326">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="b877e-327">Obtiene el nombre de la máquina.</span><span class="sxs-lookup"><span data-stu-id="b877e-327">Gets the machine name</span></span>

<span data-ttu-id="b877e-328">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="b877e-329">Establece el nombre de la máquina</span><span class="sxs-lookup"><span data-stu-id="b877e-329">Sets the machine name</span></span>

<span data-ttu-id="b877e-330">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-330">Parameters</span></span>
* <span data-ttu-id="b877e-331">Name Nuevo nombre de equipo, hex64 codificado, para establecer en</span><span class="sxs-lookup"><span data-stu-id="b877e-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="b877e-332">Datos de rendimiento</span><span class="sxs-lookup"><span data-stu-id="b877e-332">Performance data</span></span>

<span data-ttu-id="b877e-333">**/API/ResourceManager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="b877e-334">Devuelve la lista de procesos en ejecución con detalles</span><span class="sxs-lookup"><span data-stu-id="b877e-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="b877e-335">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-335">Return data</span></span>
* <span data-ttu-id="b877e-336">JSON con la lista de procesos y detalles de cada proceso</span><span class="sxs-lookup"><span data-stu-id="b877e-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="b877e-337">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="b877e-338">Devuelve las estadísticas de rendimiento del sistema (e/s de lectura/escritura, estadísticas de memoria, etc.).</span><span class="sxs-lookup"><span data-stu-id="b877e-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="b877e-339">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-339">Return data</span></span>
* <span data-ttu-id="b877e-340">JSON con información del sistema: CPU, GPU, memoria, red, e/s</span><span class="sxs-lookup"><span data-stu-id="b877e-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="b877e-341">Alimentación</span><span class="sxs-lookup"><span data-stu-id="b877e-341">Power</span></span>

<span data-ttu-id="b877e-342">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="b877e-343">Obtiene el estado actual de la batería</span><span class="sxs-lookup"><span data-stu-id="b877e-343">Gets the current battery state</span></span>

<span data-ttu-id="b877e-344">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="b877e-345">Comprueba si el sistema está en un estado de baja energía.</span><span class="sxs-lookup"><span data-stu-id="b877e-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="b877e-346">Control remoto</span><span class="sxs-lookup"><span data-stu-id="b877e-346">Remote Control</span></span>

<span data-ttu-id="b877e-347">**/API/control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="b877e-348">Reinicia el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="b877e-348">Restarts the target device</span></span>

<span data-ttu-id="b877e-349">**/API/control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="b877e-350">Apaga el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="b877e-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="b877e-351">Administrador de tareas</span><span class="sxs-lookup"><span data-stu-id="b877e-351">Task Manager</span></span>

<span data-ttu-id="b877e-352">**/API/TaskManager/App (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="b877e-353">Detiene una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="b877e-353">Stops a modern app</span></span>

<span data-ttu-id="b877e-354">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-354">Parameters</span></span>
* <span data-ttu-id="b877e-355">configura Nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="b877e-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="b877e-356">forcestop : Forzar la detención de todos los procesos (= sí)</span><span class="sxs-lookup"><span data-stu-id="b877e-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="b877e-357">**/API/TaskManager/App (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="b877e-358">Inicia una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="b877e-358">Starts a modern app</span></span>

<span data-ttu-id="b877e-359">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-359">Parameters</span></span>
* <span data-ttu-id="b877e-360">AppID PRAID de la aplicación que se va a iniciar, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="b877e-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="b877e-361">configura Nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="b877e-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="b877e-362">Administración de WiFi</span><span class="sxs-lookup"><span data-stu-id="b877e-362">WiFi Management</span></span>

<span data-ttu-id="b877e-363">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="b877e-364">Enumera las interfaces de red inalámbrica</span><span class="sxs-lookup"><span data-stu-id="b877e-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="b877e-365">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-365">Return data</span></span>
* <span data-ttu-id="b877e-366">Lista de interfaces inalámbricas con detalles (GUID, descripción, etc.)</span><span class="sxs-lookup"><span data-stu-id="b877e-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="b877e-367">**/API/WiFi/Network (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="b877e-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="b877e-368">Elimina un perfil asociado a una red en una interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="b877e-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="b877e-369">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-369">Parameters</span></span>
* <span data-ttu-id="b877e-370">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="b877e-370">interface : network interface guid</span></span>
* <span data-ttu-id="b877e-371">Perfil: nombre del perfil</span><span class="sxs-lookup"><span data-stu-id="b877e-371">profile : profile name</span></span>

<span data-ttu-id="b877e-372">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="b877e-373">Enumera las redes inalámbricas de la interfaz de red especificada</span><span class="sxs-lookup"><span data-stu-id="b877e-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="b877e-374">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-374">Parameters</span></span>
* <span data-ttu-id="b877e-375">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="b877e-375">interface : network interface guid</span></span>

<span data-ttu-id="b877e-376">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-376">Return data</span></span>
* <span data-ttu-id="b877e-377">Lista de redes inalámbricas encontradas en la interfaz de red con detalles</span><span class="sxs-lookup"><span data-stu-id="b877e-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="b877e-378">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="b877e-379">Conecta o desconecta una red de la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="b877e-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="b877e-380">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-380">Parameters</span></span>
* <span data-ttu-id="b877e-381">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="b877e-381">interface : network interface guid</span></span>
* <span data-ttu-id="b877e-382">SSID: SSID, hex64 codificado, para conectarse</span><span class="sxs-lookup"><span data-stu-id="b877e-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="b877e-383">OP: conectar o desconectar</span><span class="sxs-lookup"><span data-stu-id="b877e-383">op : connect or disconnect</span></span>
* <span data-ttu-id="b877e-384">createprofile: sí o no</span><span class="sxs-lookup"><span data-stu-id="b877e-384">createprofile : yes or no</span></span>
* <span data-ttu-id="b877e-385">clave: clave compartida, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="b877e-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="b877e-386">Grabadora de rendimiento de Windows</span><span class="sxs-lookup"><span data-stu-id="b877e-386">Windows Performance Recorder</span></span>

<span data-ttu-id="b877e-387">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="b877e-388">Carga un perfil de WPR e inicia el seguimiento con el perfil cargado.</span><span class="sxs-lookup"><span data-stu-id="b877e-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="b877e-389">Útiles</span><span class="sxs-lookup"><span data-stu-id="b877e-389">Payload</span></span>
* <span data-ttu-id="b877e-390">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="b877e-390">multi-part conforming http body</span></span>

<span data-ttu-id="b877e-391">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-391">Return data</span></span>
* <span data-ttu-id="b877e-392">Devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="b877e-392">Returns the WPR session status.</span></span>

<span data-ttu-id="b877e-393">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="b877e-394">Recupera el estado de la sesión de WPR</span><span class="sxs-lookup"><span data-stu-id="b877e-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="b877e-395">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-395">Return data</span></span>
* <span data-ttu-id="b877e-396">Estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="b877e-396">WPR session status.</span></span>

<span data-ttu-id="b877e-397">**/API/WPR/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="b877e-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="b877e-398">Detiene una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="b877e-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="b877e-399">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-399">Return data</span></span>
* <span data-ttu-id="b877e-400">Devuelve el archivo ETL de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="b877e-400">Returns the trace ETL file</span></span>

<span data-ttu-id="b877e-401">**/API/WPR/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="b877e-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="b877e-402">Inicia una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="b877e-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="b877e-403">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b877e-403">Parameters</span></span>
* <span data-ttu-id="b877e-404">perfiles Nombre del perfil.</span><span class="sxs-lookup"><span data-stu-id="b877e-404">profile : Profile name.</span></span> <span data-ttu-id="b877e-405">Los perfiles disponibles se almacenan en perfprofiles/profiles. JSON.</span><span class="sxs-lookup"><span data-stu-id="b877e-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="b877e-406">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="b877e-406">Return data</span></span>
* <span data-ttu-id="b877e-407">Al iniciar, devuelve el estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="b877e-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="b877e-408">Vea también</span><span class="sxs-lookup"><span data-stu-id="b877e-408">See also</span></span>
* [<span data-ttu-id="b877e-409">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="b877e-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="b877e-410">Referencia de API principal del portal de dispositivos (UWP)</span><span class="sxs-lookup"><span data-stu-id="b877e-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
