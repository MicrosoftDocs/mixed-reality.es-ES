---
title: Referencia de la API del Portal de dispositivos
description: Referencia de API para Windows Device portal en HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, portal de dispositivos de Windows, API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451330"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="bc82a-104">Referencia de la API del Portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="bc82a-104">Device portal API reference</span></span>

<span data-ttu-id="bc82a-105">Todo lo que se encuentra en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para tener acceso a los datos y controlar el dispositivo mediante programación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="bc82a-106">Implementación de aplicación</span><span class="sxs-lookup"><span data-stu-id="bc82a-106">App deloyment</span></span>

<span data-ttu-id="bc82a-107">**/API/App/packagemanager/Package (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="bc82a-108">Desinstala una aplicación</span><span class="sxs-lookup"><span data-stu-id="bc82a-108">Uninstalls an app</span></span>

<span data-ttu-id="bc82a-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-109">Parameters</span></span>
* <span data-ttu-id="bc82a-110">paquete: nombre de archivo del paquete que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="bc82a-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="bc82a-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="bc82a-112">Instala una aplicación</span><span class="sxs-lookup"><span data-stu-id="bc82a-112">Installs an App</span></span>

<span data-ttu-id="bc82a-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-113">Parameters</span></span>
* <span data-ttu-id="bc82a-114">paquete: nombre de archivo del paquete que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="bc82a-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="bc82a-115">Carga</span><span class="sxs-lookup"><span data-stu-id="bc82a-115">Payload</span></span>
* <span data-ttu-id="bc82a-116">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="bc82a-116">multi-part conforming http body</span></span>

<span data-ttu-id="bc82a-117">**/API/App/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="bc82a-118">Recupera la lista de aplicaciones instaladas en el sistema con detalles</span><span class="sxs-lookup"><span data-stu-id="bc82a-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="bc82a-119">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-119">Return data</span></span>
* <span data-ttu-id="bc82a-120">Lista de paquetes instalados con detalles</span><span class="sxs-lookup"><span data-stu-id="bc82a-120">List of installed packages with details</span></span>

<span data-ttu-id="bc82a-121">**/API/App/packagemanager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="bc82a-122">Obtiene el estado de la instalación de la aplicación en curso</span><span class="sxs-lookup"><span data-stu-id="bc82a-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="bc82a-123">Colección de volcados de memoria</span><span class="sxs-lookup"><span data-stu-id="bc82a-123">Dump collection</span></span>

<span data-ttu-id="bc82a-124">**/API/Debug/dump/usermode/CrashControl (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="bc82a-125">Deshabilita la recopilación de volcados de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="bc82a-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="bc82a-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-126">Parameters</span></span>
* <span data-ttu-id="bc82a-127">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="bc82a-127">packageFullname : package name</span></span>

<span data-ttu-id="bc82a-128">**/API/Debug/dump/usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="bc82a-129">Obtiene la configuración de la colección de volcados de memoria de aplicaciones transferidas</span><span class="sxs-lookup"><span data-stu-id="bc82a-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="bc82a-130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-130">Parameters</span></span>
* <span data-ttu-id="bc82a-131">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="bc82a-131">packageFullname : package name</span></span>

<span data-ttu-id="bc82a-132">**/API/Debug/dump/usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="bc82a-133">Habilita y establece la configuración de control de volcado para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="bc82a-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="bc82a-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-134">Parameters</span></span>
* <span data-ttu-id="bc82a-135">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="bc82a-135">packageFullname : package name</span></span>

<span data-ttu-id="bc82a-136">**/API/Debug/dump/usermode/crashdump (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="bc82a-137">Elimina un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="bc82a-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="bc82a-138">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-138">Parameters</span></span>
* <span data-ttu-id="bc82a-139">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="bc82a-139">packageFullname : package name</span></span>
* <span data-ttu-id="bc82a-140">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="bc82a-140">fileName : dump file name</span></span>

<span data-ttu-id="bc82a-141">**/API/Debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="bc82a-142">Recupera un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="bc82a-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="bc82a-143">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-143">Parameters</span></span>
* <span data-ttu-id="bc82a-144">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="bc82a-144">packageFullname : package name</span></span>
* <span data-ttu-id="bc82a-145">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="bc82a-145">fileName : dump file name</span></span>

<span data-ttu-id="bc82a-146">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-146">Return data</span></span>
* <span data-ttu-id="bc82a-147">Archivo de volcado de memoria.</span><span class="sxs-lookup"><span data-stu-id="bc82a-147">Dump file.</span></span> <span data-ttu-id="bc82a-148">Inspeccionar con WinDbg o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bc82a-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="bc82a-149">**/API/Debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="bc82a-150">Devuelve la lista de todos los volcados de memoria de las aplicaciones transferidas localmente</span><span class="sxs-lookup"><span data-stu-id="bc82a-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="bc82a-151">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-151">Return data</span></span>
* <span data-ttu-id="bc82a-152">Lista de volcados de memoria por aplicación cargada</span><span class="sxs-lookup"><span data-stu-id="bc82a-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="bc82a-153">ETW</span><span class="sxs-lookup"><span data-stu-id="bc82a-153">ETW</span></span>

<span data-ttu-id="bc82a-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="bc82a-155">Enumera los proveedores registrados</span><span class="sxs-lookup"><span data-stu-id="bc82a-155">Enumerates registered providers</span></span>

<span data-ttu-id="bc82a-156">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-156">Return data</span></span>
* <span data-ttu-id="bc82a-157">Lista de proveedores, nombre descriptivo y GUID</span><span class="sxs-lookup"><span data-stu-id="bc82a-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="bc82a-158">**/API/ETW/Session/Realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="bc82a-159">Crea una sesión ETW en tiempo real; se administra a través de un WebSocket.</span><span class="sxs-lookup"><span data-stu-id="bc82a-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="bc82a-160">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-160">Return data</span></span>
* <span data-ttu-id="bc82a-161">Eventos ETW de los proveedores habilitados</span><span class="sxs-lookup"><span data-stu-id="bc82a-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="bc82a-162">SO Holographic</span><span class="sxs-lookup"><span data-stu-id="bc82a-162">Holographic OS</span></span>

<span data-ttu-id="bc82a-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="bc82a-164">Devuelve una lista de proveedores ETW específicos de HoloLens que no están registrados en el sistema.</span><span class="sxs-lookup"><span data-stu-id="bc82a-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="bc82a-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="bc82a-166">Devuelve los Estados de todos los servicios que se están ejecutando.</span><span class="sxs-lookup"><span data-stu-id="bc82a-166">Returns the states of all services running.</span></span>

<span data-ttu-id="bc82a-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="bc82a-168">Obtiene el IPD almacenado (distancia interpupillary) en milímetros.</span><span class="sxs-lookup"><span data-stu-id="bc82a-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="bc82a-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="bc82a-170">Establece la configuración de IPD</span><span class="sxs-lookup"><span data-stu-id="bc82a-170">Sets the IPD</span></span>

<span data-ttu-id="bc82a-171">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-171">Parameters</span></span>
* <span data-ttu-id="bc82a-172">IPD: nuevo valor de IPD que se establecerá en milímetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="bc82a-173">**/API/Holographic/os/webmanagement/Settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="bc82a-174">Obtener los requisitos de HTTPS para Device Portal</span><span class="sxs-lookup"><span data-stu-id="bc82a-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="bc82a-175">**/API/Holographic/os/webmanagement/Settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="bc82a-176">Establece los requisitos de HTTPS para el portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="bc82a-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="bc82a-177">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-177">Parameters</span></span>
* <span data-ttu-id="bc82a-178">requerido: sí, no o predeterminado</span><span class="sxs-lookup"><span data-stu-id="bc82a-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="bc82a-179">Percepción holográfica</span><span class="sxs-lookup"><span data-stu-id="bc82a-179">Holographic Perception</span></span>

<span data-ttu-id="bc82a-180">**/API/Holographic/Perception/Client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="bc82a-181">Acepta actualizaciones de WebSocket y ejecuta un cliente de percepción que envía actualizaciones a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="bc82a-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="bc82a-182">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-182">Parameters</span></span>
* <span data-ttu-id="bc82a-183">clientmode: "Active" fuerza el modo de seguimiento visual cuando no se puede establecer de forma pasiva</span><span class="sxs-lookup"><span data-stu-id="bc82a-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="bc82a-184">Temperatura térmica holográfica</span><span class="sxs-lookup"><span data-stu-id="bc82a-184">Holographic Thermal</span></span>

<span data-ttu-id="bc82a-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="bc82a-186">Obtener la fase térmica del dispositivo (0 normal, 1 cálido, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="bc82a-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="bc82a-187">Control de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="bc82a-187">Perception Simulation Control</span></span>

<span data-ttu-id="bc82a-188">**/API/Holographic/Simulation/control/MODE (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="bc82a-189">Obtención del modo de simulación</span><span class="sxs-lookup"><span data-stu-id="bc82a-189">Get the simulation mode</span></span>

<span data-ttu-id="bc82a-190">**/API/Holographic/Simulation/control/MODE (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="bc82a-191">Establecer el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="bc82a-191">Set the simulation mode</span></span>

<span data-ttu-id="bc82a-192">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-192">Parameters</span></span>
* <span data-ttu-id="bc82a-193">modo de simulación: predeterminado, simulación, remoto, heredado</span><span class="sxs-lookup"><span data-stu-id="bc82a-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="bc82a-194">**/API/Holographic/Simulation/control/Stream (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="bc82a-195">Elimine un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="bc82a-195">Delete a control stream.</span></span>

<span data-ttu-id="bc82a-196">**/API/Holographic/Simulation/control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="bc82a-197">Abra una conexión de socket web para un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="bc82a-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="bc82a-198">**/API/Holographic/Simulation/control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="bc82a-199">Cree un flujo de control (se requiere prioridad) o publique los datos en un flujo creado (streamId obligatorio).</span><span class="sxs-lookup"><span data-stu-id="bc82a-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="bc82a-200">Se espera que los datos expuestos sean del tipo "application/octet-stream".</span><span class="sxs-lookup"><span data-stu-id="bc82a-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="bc82a-201">**/API/Holographic/Simulation/display/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="bc82a-202">Solicitar una secuencia de vídeo de simulación que contenga el contenido representado en la pantalla del sistema cuando esté en modo de ' simulación '.</span><span class="sxs-lookup"><span data-stu-id="bc82a-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="bc82a-203">Inicialmente, se enviará un encabezado de descriptor de formato simple, seguido de las texturas codificadas en H. 264, cada una precedida por un encabezado que indica el índice ocular y el tamaño de la textura.</span><span class="sxs-lookup"><span data-stu-id="bc82a-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="bc82a-204">Reproducción de la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="bc82a-204">Perception Simulation Playback</span></span>

<span data-ttu-id="bc82a-205">**/API/Holographic/Simulation/Playback/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="bc82a-206">Elimina una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-206">Delete a recording.</span></span>

<span data-ttu-id="bc82a-207">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-207">Parameters</span></span>
* <span data-ttu-id="bc82a-208">grabación: nombre de la grabación que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="bc82a-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="bc82a-209">**/API/Holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="bc82a-210">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-210">Upload a recording.</span></span>

<span data-ttu-id="bc82a-211">**/API/Holographic/Simulation/Playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="bc82a-212">Obtener todas las grabaciones.</span><span class="sxs-lookup"><span data-stu-id="bc82a-212">Get all recordings.</span></span>

<span data-ttu-id="bc82a-213">**/API/Holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="bc82a-214">Obtiene el estado de reproducción actual de una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="bc82a-215">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-215">Parameters</span></span>
* <span data-ttu-id="bc82a-216">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-216">recording : Name of recording.</span></span>

<span data-ttu-id="bc82a-217">**/API/Holographic/Simulation/Playback/Session/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="bc82a-218">Descargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-218">Unload a recording.</span></span>

<span data-ttu-id="bc82a-219">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-219">Parameters</span></span>
* <span data-ttu-id="bc82a-220">grabación: nombre de la grabación que se va a descargar.</span><span class="sxs-lookup"><span data-stu-id="bc82a-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="bc82a-221">**/API/Holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="bc82a-222">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-222">Load a recording.</span></span>

<span data-ttu-id="bc82a-223">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-223">Parameters</span></span>
* <span data-ttu-id="bc82a-224">grabación: nombre de la grabación que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="bc82a-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="bc82a-225">**/API/Holographic/Simulation/Playback/Session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="bc82a-226">Obtiene todas las grabaciones cargadas.</span><span class="sxs-lookup"><span data-stu-id="bc82a-226">Get all loaded recordings.</span></span>

<span data-ttu-id="bc82a-227">**/API/Holographic/Simulation/Playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="bc82a-228">Pausar una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-228">Pause a recording.</span></span>

<span data-ttu-id="bc82a-229">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-229">Parameters</span></span>
* <span data-ttu-id="bc82a-230">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-230">recording : Name of recording.</span></span>

<span data-ttu-id="bc82a-231">**/API/Holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="bc82a-232">Reproducir una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-232">Play a recording.</span></span>

<span data-ttu-id="bc82a-233">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-233">Parameters</span></span>
* <span data-ttu-id="bc82a-234">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-234">recording : Name of recording.</span></span>

<span data-ttu-id="bc82a-235">**/API/Holographic/Simulation/Playback/Session/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="bc82a-236">Detener una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-236">Stop a recording.</span></span>

<span data-ttu-id="bc82a-237">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-237">Parameters</span></span>
* <span data-ttu-id="bc82a-238">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-238">recording : Name of recording.</span></span>

<span data-ttu-id="bc82a-239">**/API/Holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="bc82a-240">Obtiene los tipos de datos en una grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="bc82a-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="bc82a-241">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-241">Parameters</span></span>
* <span data-ttu-id="bc82a-242">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="bc82a-243">Grabación de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="bc82a-243">Perception Simulation Recording</span></span>

<span data-ttu-id="bc82a-244">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="bc82a-245">Iniciar una grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-245">Start a recording.</span></span> <span data-ttu-id="bc82a-246">Solo puede haber una grabación activa al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="bc82a-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="bc82a-247">Debe establecerse una de las clases Head, Hand, spatialMapping o Environment.</span><span class="sxs-lookup"><span data-stu-id="bc82a-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="bc82a-248">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-248">Parameters</span></span>
* <span data-ttu-id="bc82a-249">Head: establézcalo en 1 para registrar los datos principales.</span><span class="sxs-lookup"><span data-stu-id="bc82a-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="bc82a-250">manos: establézcalo en 1 para registrar los datos de la mano.</span><span class="sxs-lookup"><span data-stu-id="bc82a-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="bc82a-251">spatialMapping: establézcalo en 1 para registrar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="bc82a-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="bc82a-252">entorno: establézcalo en 1 para registrar los datos del entorno.</span><span class="sxs-lookup"><span data-stu-id="bc82a-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="bc82a-253">Nombre: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-253">name : Name of the recording.</span></span>
* <span data-ttu-id="bc82a-254">singleSpatialMappingFrame: establézcalo en 1 para registrar solo un marco de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="bc82a-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="bc82a-255">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="bc82a-256">Obtiene el estado de grabación.</span><span class="sxs-lookup"><span data-stu-id="bc82a-256">Get recording state.</span></span>

<span data-ttu-id="bc82a-257">**/API/Holographic/Simulation/Recording/STOP (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="bc82a-258">Detener la grabación actual.</span><span class="sxs-lookup"><span data-stu-id="bc82a-258">Stop the current recording.</span></span> <span data-ttu-id="bc82a-259">La grabación se devolverá como un archivo.</span><span class="sxs-lookup"><span data-stu-id="bc82a-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="bc82a-260">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="bc82a-260">Mixed Reality Capture</span></span>

<span data-ttu-id="bc82a-261">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="bc82a-262">Descarga un archivo de realidad mixta desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bc82a-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="bc82a-263">Use OP = parámetro de consulta de transmisión por secuencias.</span><span class="sxs-lookup"><span data-stu-id="bc82a-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="bc82a-264">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-264">Parameters</span></span>
* <span data-ttu-id="bc82a-265">Filename: nombre, hex64 codificado, del archivo de vídeo que se va a obtener</span><span class="sxs-lookup"><span data-stu-id="bc82a-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="bc82a-266">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="bc82a-266">op : stream</span></span>

<span data-ttu-id="bc82a-267">**/API/Holographic/MRC/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="bc82a-268">Elimina una grabación de realidad mixta del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bc82a-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="bc82a-269">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-269">Parameters</span></span>
* <span data-ttu-id="bc82a-270">Filename: nombre, hex64 codificado, del archivo que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="bc82a-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="bc82a-271">**/API/Holographic/MRC/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="bc82a-272">Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="bc82a-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="bc82a-273">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="bc82a-274">Toma una fotografía de realidad mixta y crea un archivo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bc82a-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="bc82a-275">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-275">Parameters</span></span>
* <span data-ttu-id="bc82a-276">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="bc82a-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="bc82a-277">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="bc82a-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="bc82a-278">RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="bc82a-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="bc82a-279">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="bc82a-280">Obtiene la configuración de captura de realidad mixta predeterminada</span><span class="sxs-lookup"><span data-stu-id="bc82a-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="bc82a-281">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="bc82a-282">Establece la configuración de captura de realidad mixta predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bc82a-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="bc82a-283">Algunos de estos valores se aplican a la captura de vídeo y fotos de MRC del sistema.</span><span class="sxs-lookup"><span data-stu-id="bc82a-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="bc82a-284">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="bc82a-285">Obtiene el estado de la captura de realidad mixta en el portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="bc82a-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="bc82a-286">***Respuesta***</span><span class="sxs-lookup"><span data-stu-id="bc82a-286">***Response***</span></span>

<span data-ttu-id="bc82a-287">La respuesta contiene una propiedad JSON que indica si el portal de dispositivos de Windows está grabando vídeo o no.</span><span class="sxs-lookup"><span data-stu-id="bc82a-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="bc82a-288">**/API/Holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="bc82a-289">Obtiene la imagen en miniatura del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="bc82a-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="bc82a-290">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-290">Parameters</span></span>
* <span data-ttu-id="bc82a-291">Filename: nombre, hex64 codificado, del archivo para el que se solicita la miniatura</span><span class="sxs-lookup"><span data-stu-id="bc82a-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="bc82a-292">**/API/Holographic/MRC/video/control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="bc82a-293">Inicia una grabación de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="bc82a-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="bc82a-294">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-294">Parameters</span></span>
* <span data-ttu-id="bc82a-295">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="bc82a-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="bc82a-296">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="bc82a-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="bc82a-297">MIC: Capture Microphone: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="bc82a-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="bc82a-298">bucle invertido: captura de audio de la aplicación: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="bc82a-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="bc82a-299">RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="bc82a-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="bc82a-300">Vstab: (solo HoloLens 2) habilitar estabilización de vídeo: true o false (el valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="bc82a-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="bc82a-301">vstabbuffer: (solo HoloLens 2) latencia de búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="bc82a-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="bc82a-302">**/API/Holographic/MRC/video/control/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="bc82a-303">Detiene la grabación de realidad mixta actual</span><span class="sxs-lookup"><span data-stu-id="bc82a-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="bc82a-304">Streaming de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="bc82a-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="bc82a-305">HoloLens admite la vista previa dinámica de la realidad mixta a través de la descarga fragmentada de un MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="bc82a-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="bc82a-306">Los flujos de realidad mixta comparten el mismo conjunto de parámetros para controlar lo que se captura:</span><span class="sxs-lookup"><span data-stu-id="bc82a-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="bc82a-307">hololens: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="bc82a-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="bc82a-308">PV: capturar la cámara PV: true o false</span><span class="sxs-lookup"><span data-stu-id="bc82a-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="bc82a-309">MIC: capturar micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="bc82a-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="bc82a-310">bucle invertido: captura de audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="bc82a-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="bc82a-311">Si no se especifica ninguno de estos: los hologramas, la cámara de foto/vídeo y el audio de la aplicación se capturarán</span><span class="sxs-lookup"><span data-stu-id="bc82a-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="bc82a-312">Si se especifica any: los parámetros no especificados tendrán como valor predeterminado False.</span><span class="sxs-lookup"><span data-stu-id="bc82a-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="bc82a-313">Parámetros opcionales (solo HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="bc82a-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="bc82a-314">RenderFromCamera: representación de la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="bc82a-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="bc82a-315">Vstab: habilitar estabilización de vídeo: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="bc82a-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="bc82a-316">vstabbuffer: latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="bc82a-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="bc82a-317">**/API/Holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="bc82a-318">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="bc82a-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="bc82a-319">**/API/Holographic/Stream/live_high. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="bc82a-320">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="bc82a-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="bc82a-321">**/API/Holographic/Stream/live_med. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="bc82a-322">Una secuencia de 854x480p 30 fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="bc82a-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="bc82a-323">**/API/Holographic/Stream/live_low. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="bc82a-324">Una secuencia de 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="bc82a-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="bc82a-325">Redes</span><span class="sxs-lookup"><span data-stu-id="bc82a-325">Networking</span></span>

<span data-ttu-id="bc82a-326">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="bc82a-327">Obtiene la configuración de IP actual.</span><span class="sxs-lookup"><span data-stu-id="bc82a-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="bc82a-328">Información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="bc82a-328">OS Information</span></span>

<span data-ttu-id="bc82a-329">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="bc82a-330">Obtiene información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="bc82a-330">Gets operating system information</span></span>

<span data-ttu-id="bc82a-331">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="bc82a-332">Obtiene el nombre de la máquina.</span><span class="sxs-lookup"><span data-stu-id="bc82a-332">Gets the machine name</span></span>

<span data-ttu-id="bc82a-333">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="bc82a-334">Establece el nombre de la máquina</span><span class="sxs-lookup"><span data-stu-id="bc82a-334">Sets the machine name</span></span>

<span data-ttu-id="bc82a-335">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-335">Parameters</span></span>
* <span data-ttu-id="bc82a-336">Nombre: nuevo nombre del equipo, hex64 codificado, para establecer en</span><span class="sxs-lookup"><span data-stu-id="bc82a-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="bc82a-337">Datos de rendimiento</span><span class="sxs-lookup"><span data-stu-id="bc82a-337">Performance data</span></span>

<span data-ttu-id="bc82a-338">**/API/ResourceManager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="bc82a-339">Devuelve la lista de procesos en ejecución con detalles</span><span class="sxs-lookup"><span data-stu-id="bc82a-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="bc82a-340">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-340">Return data</span></span>
* <span data-ttu-id="bc82a-341">JSON con la lista de procesos y detalles de cada proceso</span><span class="sxs-lookup"><span data-stu-id="bc82a-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="bc82a-342">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="bc82a-343">Devuelve las estadísticas de rendimiento del sistema (e/s de lectura/escritura, estadísticas de memoria, etc.).</span><span class="sxs-lookup"><span data-stu-id="bc82a-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="bc82a-344">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-344">Return data</span></span>
* <span data-ttu-id="bc82a-345">JSON con información del sistema: CPU, GPU, memoria, red, e/s</span><span class="sxs-lookup"><span data-stu-id="bc82a-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="bc82a-346">Potencia</span><span class="sxs-lookup"><span data-stu-id="bc82a-346">Power</span></span>

<span data-ttu-id="bc82a-347">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="bc82a-348">Obtiene el estado actual de la batería</span><span class="sxs-lookup"><span data-stu-id="bc82a-348">Gets the current battery state</span></span>

<span data-ttu-id="bc82a-349">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="bc82a-350">Comprueba si el sistema está en un estado de baja energía.</span><span class="sxs-lookup"><span data-stu-id="bc82a-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="bc82a-351">Control remoto</span><span class="sxs-lookup"><span data-stu-id="bc82a-351">Remote Control</span></span>

<span data-ttu-id="bc82a-352">**/API/control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="bc82a-353">Reinicia el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="bc82a-353">Restarts the target device</span></span>

<span data-ttu-id="bc82a-354">**/API/control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="bc82a-355">Apaga el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="bc82a-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="bc82a-356">Administrador de tareas</span><span class="sxs-lookup"><span data-stu-id="bc82a-356">Task Manager</span></span>

<span data-ttu-id="bc82a-357">**/API/TaskManager/App (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="bc82a-358">Detiene una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="bc82a-358">Stops a modern app</span></span>

<span data-ttu-id="bc82a-359">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-359">Parameters</span></span>
* <span data-ttu-id="bc82a-360">paquete: nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="bc82a-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="bc82a-361">forcestop: forzar la detención de todos los procesos (= sí)</span><span class="sxs-lookup"><span data-stu-id="bc82a-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="bc82a-362">**/API/TaskManager/App (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="bc82a-363">Inicia una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="bc82a-363">Starts a modern app</span></span>

<span data-ttu-id="bc82a-364">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-364">Parameters</span></span>
* <span data-ttu-id="bc82a-365">AppID: PRAID de la aplicación que se va a iniciar, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="bc82a-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="bc82a-366">paquete: nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="bc82a-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="bc82a-367">Administración de WiFi</span><span class="sxs-lookup"><span data-stu-id="bc82a-367">WiFi Management</span></span>

<span data-ttu-id="bc82a-368">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="bc82a-369">Enumera las interfaces de red inalámbrica</span><span class="sxs-lookup"><span data-stu-id="bc82a-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="bc82a-370">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-370">Return data</span></span>
* <span data-ttu-id="bc82a-371">Lista de interfaces inalámbricas con detalles (GUID, descripción, etc.)</span><span class="sxs-lookup"><span data-stu-id="bc82a-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="bc82a-372">**/API/WiFi/Network (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="bc82a-373">Elimina un perfil asociado a una red en una interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="bc82a-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="bc82a-374">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-374">Parameters</span></span>
* <span data-ttu-id="bc82a-375">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="bc82a-375">interface : network interface guid</span></span>
* <span data-ttu-id="bc82a-376">Perfil: nombre del perfil</span><span class="sxs-lookup"><span data-stu-id="bc82a-376">profile : profile name</span></span>

<span data-ttu-id="bc82a-377">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="bc82a-378">Enumera las redes inalámbricas de la interfaz de red especificada</span><span class="sxs-lookup"><span data-stu-id="bc82a-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="bc82a-379">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-379">Parameters</span></span>
* <span data-ttu-id="bc82a-380">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="bc82a-380">interface : network interface guid</span></span>

<span data-ttu-id="bc82a-381">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-381">Return data</span></span>
* <span data-ttu-id="bc82a-382">Lista de redes inalámbricas encontradas en la interfaz de red con detalles</span><span class="sxs-lookup"><span data-stu-id="bc82a-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="bc82a-383">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="bc82a-384">Conecta o desconecta una red de la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="bc82a-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="bc82a-385">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-385">Parameters</span></span>
* <span data-ttu-id="bc82a-386">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="bc82a-386">interface : network interface guid</span></span>
* <span data-ttu-id="bc82a-387">SSID: SSID, hex64 codificado, para conectarse</span><span class="sxs-lookup"><span data-stu-id="bc82a-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="bc82a-388">OP: conectar o desconectar</span><span class="sxs-lookup"><span data-stu-id="bc82a-388">op : connect or disconnect</span></span>
* <span data-ttu-id="bc82a-389">createprofile: sí o no</span><span class="sxs-lookup"><span data-stu-id="bc82a-389">createprofile : yes or no</span></span>
* <span data-ttu-id="bc82a-390">clave: clave compartida, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="bc82a-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="bc82a-391">Grabadora de rendimiento de Windows</span><span class="sxs-lookup"><span data-stu-id="bc82a-391">Windows Performance Recorder</span></span>

<span data-ttu-id="bc82a-392">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="bc82a-393">Carga un perfil de WPR e inicia el seguimiento con el perfil cargado.</span><span class="sxs-lookup"><span data-stu-id="bc82a-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="bc82a-394">Carga</span><span class="sxs-lookup"><span data-stu-id="bc82a-394">Payload</span></span>
* <span data-ttu-id="bc82a-395">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="bc82a-395">multi-part conforming http body</span></span>

<span data-ttu-id="bc82a-396">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-396">Return data</span></span>
* <span data-ttu-id="bc82a-397">Devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="bc82a-397">Returns the WPR session status.</span></span>

<span data-ttu-id="bc82a-398">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="bc82a-399">Recupera el estado de la sesión de WPR</span><span class="sxs-lookup"><span data-stu-id="bc82a-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="bc82a-400">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-400">Return data</span></span>
* <span data-ttu-id="bc82a-401">Estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="bc82a-401">WPR session status.</span></span>

<span data-ttu-id="bc82a-402">**/API/WPR/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="bc82a-403">Detiene una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="bc82a-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="bc82a-404">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-404">Return data</span></span>
* <span data-ttu-id="bc82a-405">Devuelve el archivo ETL de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="bc82a-405">Returns the trace ETL file</span></span>

<span data-ttu-id="bc82a-406">**/API/WPR/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="bc82a-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="bc82a-407">Inicia una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="bc82a-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="bc82a-408">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc82a-408">Parameters</span></span>
* <span data-ttu-id="bc82a-409">Perfil: nombre del perfil.</span><span class="sxs-lookup"><span data-stu-id="bc82a-409">profile : Profile name.</span></span> <span data-ttu-id="bc82a-410">Los perfiles disponibles se almacenan en perfprofiles/profiles. JSON.</span><span class="sxs-lookup"><span data-stu-id="bc82a-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="bc82a-411">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="bc82a-411">Return data</span></span>
* <span data-ttu-id="bc82a-412">Al iniciar, devuelve el estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="bc82a-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc82a-413">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bc82a-413">See also</span></span>
* [<span data-ttu-id="bc82a-414">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="bc82a-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="bc82a-415">Referencia de API principal del portal de dispositivos (UWP)</span><span class="sxs-lookup"><span data-stu-id="bc82a-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
