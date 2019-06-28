---
title: Simulación de percepción
description: Una guía para utilizar la biblioteca de simulación de percepción para automatizar la entrada simulada para aplicaciones envolventes
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, simulación, las pruebas
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414532"
---
# <a name="perception-simulation"></a><span data-ttu-id="28f61-104">Simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="28f61-104">Perception simulation</span></span>

<span data-ttu-id="28f61-105">¿Desea crear una prueba automatizada de la aplicación?</span><span class="sxs-lookup"><span data-stu-id="28f61-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="28f61-106">¿Desea que las pruebas para ir más allá de las pruebas unitarias de nivel de componente y realmente ejercitar su aplicación-to-end?</span><span class="sxs-lookup"><span data-stu-id="28f61-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="28f61-107">Simulación de percepción es lo está buscando.</span><span class="sxs-lookup"><span data-stu-id="28f61-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="28f61-108">La biblioteca de simulación de percepción envía humana y mundo datos de entrada en la aplicación para que pueda automatizar las pruebas.</span><span class="sxs-lookup"><span data-stu-id="28f61-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="28f61-109">Por ejemplo, puede simular la entrada de un humano busca una posición específica, repetible y, a continuación, realizar un gesto o con un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="28f61-110">Simulación de percepción puede enviar entrada simulado así a un HoloLens físico, el emulador de HoloLens (gen 1), el HoloLens 2 emulador o en un equipo con el Portal de realidad mixta instalado.</span><span class="sxs-lookup"><span data-stu-id="28f61-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="28f61-111">Percepción simulación omite los sensores en directo en un dispositivo de realidad mixta y envía simula la entrada para aplicaciones que se ejecutan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="28f61-112">Las aplicaciones reciben estos eventos de entrada a través de las mismas API, use siempre y no se puede indicar la diferencia entre la ejecución con sensores reales frente a ejecutar con la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="28f61-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="28f61-113">Simulación de percepción es la misma tecnología que usa los emuladores de HoloLens para enviar la entrada simulado a la máquina Virtual de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="28f61-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="28f61-114">Para empezar a usar la simulación en el código, empiece por crear un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="28f61-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="28f61-115">Desde ese objeto, puede emitir comandos para controlar las propiedades de un simulado "humano", incluida la posición principal, la posición de la mano y los gestos, y puede habilitar y manipular los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="28f61-116">Configuración de un proyecto de Visual Studio para la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="28f61-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="28f61-117">[Instalar el emulador de HoloLens](install-the-tools.md) en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="28f61-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="28f61-118">El emulador incluye las bibliotecas que se va a usar para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="28f61-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="28f61-119">Crear un nuevo Visual Studio C# proyecto de escritorio (un proyecto de consola funciona bien para empezar a trabajar).</span><span class="sxs-lookup"><span data-stu-id="28f61-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="28f61-120">Agregue los siguientes archivos binarios al proyecto como referencias (proyecto -> Agregar -> referencia...). Puede encontrarlos en % ProgramFiles (x86) %\Microsoft XDE\\(versión), como **% ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** para el emulador de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="28f61-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="28f61-121">(Nota: aunque los archivos binarios forman parte del emulador de HoloLens 2, también funcionan en Windows Mixed Reality en el escritorio.) a.</span><span class="sxs-lookup"><span data-stu-id="28f61-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="28f61-122">PerceptionSimulationManager.Interop.dll - Managed C# contenedor para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="28f61-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="28f61-123">b.</span><span class="sxs-lookup"><span data-stu-id="28f61-123">b.</span></span> <span data-ttu-id="28f61-124">PerceptionSimulationRest.dll - Library para configurar un canal de comunicación de socket web al HoloLens o emulador.</span><span class="sxs-lookup"><span data-stu-id="28f61-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="28f61-125">c.</span><span class="sxs-lookup"><span data-stu-id="28f61-125">c.</span></span> <span data-ttu-id="28f61-126">SimulationStream.Interop.dll - tipos compartidos para la simulación.</span><span class="sxs-lookup"><span data-stu-id="28f61-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="28f61-127">Agregue la implementación PerceptionSimulationManager.dll binarios al proyecto una.</span><span class="sxs-lookup"><span data-stu-id="28f61-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="28f61-128">En primer lugar agregarlo al proyecto como un archivo binario (proyecto -> Agregar -> elemento existente...). Guárdelo como un vínculo para que no copiarlo a la carpeta de origen del proyecto.</span><span class="sxs-lookup"><span data-stu-id="28f61-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="28f61-129">![Agregar al proyecto como un vínculo PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="28f61-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="28f61-130">A continuación, asegúrese de que lo de la copia en la carpeta de salida en la compilación.</span><span class="sxs-lookup"><span data-stu-id="28f61-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="28f61-131">Se trata en la hoja de propiedades para el archivo binario.</span><span class="sxs-lookup"><span data-stu-id="28f61-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="28f61-132">![Marcar PerceptionSimulationManager.dll para copiar en el directorio de salida](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="28f61-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="28f61-133">Establezca la plataforma de soluciones activas en x64.</span><span class="sxs-lookup"><span data-stu-id="28f61-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="28f61-134">(Use el Administrador de configuración para crear una entrada de la plataforma para x64 si aún no existe).</span><span class="sxs-lookup"><span data-stu-id="28f61-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="28f61-135">Creación de un objeto de administrador IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="28f61-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="28f61-136">Para controlar la simulación, deberá emitir las actualizaciones a los objetos recuperados de un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="28f61-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="28f61-137">El primer paso es obtener ese objeto y conectarlo a su emulador o dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="28f61-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="28f61-138">Puede obtener la dirección IP de su emulador, haga clic en el botón de Portal de dispositivos en el [barra de herramientas](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="28f61-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="28f61-139">![Icono de dispositivo Portal abierta](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.</span><span class="sxs-lookup"><span data-stu-id="28f61-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="28f61-140">Para Windows Mixed Reality, esto se puede recuperar en la aplicación de configuración en "Actualización y seguridad" y "para desarrolladores" en la "conectar mediante:" sección en "Habilitar Portal de dispositivo".</span><span class="sxs-lookup"><span data-stu-id="28f61-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="28f61-141">No olvide anotar la dirección IP y el puerto.</span><span class="sxs-lookup"><span data-stu-id="28f61-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="28f61-142">En primer lugar, llamaremos a RestSimulationStreamSink.Create para obtener un objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="28f61-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="28f61-143">Este es el dispositivo de destino o el emulador que se controlan a través de una conexión http.</span><span class="sxs-lookup"><span data-stu-id="28f61-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="28f61-144">Se pasa a los comandos y controla el [Windows Device Portal](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="28f61-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="28f61-145">Los cuatro parámetros que deberá crear un objeto son:</span><span class="sxs-lookup"><span data-stu-id="28f61-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="28f61-146">Uri de URI: dirección IP del dispositivo de destino (por ejemplo, "http://123.123.123.123"o"http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="28f61-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="28f61-147">System.Net.NetworkCredential credenciales: nombre de usuario y contraseña para conectarse a la [Windows Device Portal](using-the-windows-device-portal.md) en el emulador o dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="28f61-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="28f61-148">Si se conecta con el emulador a través de su dirección local (p. ej., 168. *.* . \*) en el mismo equipo, se aceptan las credenciales.</span><span class="sxs-lookup"><span data-stu-id="28f61-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="28f61-149">normal: bool es True para una prioridad normal, false de prioridad baja.</span><span class="sxs-lookup"><span data-stu-id="28f61-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="28f61-150">Por lo general desea establecerlo en *true* para escenarios de prueba, lo que permite la prueba para tomar el control.</span><span class="sxs-lookup"><span data-stu-id="28f61-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="28f61-151">El emulador y la simulación de Windows Mixed Reality usan conexiones de baja prioridad.</span><span class="sxs-lookup"><span data-stu-id="28f61-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="28f61-152">Si la prueba también utiliza una conexión de prioridad baja, el máximo establecido recientemente se cerrará en el control.</span><span class="sxs-lookup"><span data-stu-id="28f61-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="28f61-153">Elemento System.Threading.CancellationToken token: Token para cancelar la operación asincrónica.</span><span class="sxs-lookup"><span data-stu-id="28f61-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="28f61-154">En segundo lugar, cree el IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="28f61-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="28f61-155">Este es el objeto que se usa para controlar la simulación.</span><span class="sxs-lookup"><span data-stu-id="28f61-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="28f61-156">Tenga en cuenta que esto también se debe realizar en un método asincrónico.</span><span class="sxs-lookup"><span data-stu-id="28f61-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="28f61-157">Controlar a los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="28f61-157">Control the simulated Human</span></span>

<span data-ttu-id="28f61-158">Un IPerceptionSimulationManager tiene una propiedad humana que devuelve un objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="28f61-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="28f61-159">Para controlar a los humanos simulado, realizar operaciones en este objeto.</span><span class="sxs-lookup"><span data-stu-id="28f61-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="28f61-160">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="28f61-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="28f61-161">Ejemplo básico C# aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="28f61-161">Basic Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="28f61-162">Extended ejemplo C# aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="28f61-162">Extended Sample C# console application</span></span>

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="28f61-163">Tenga en cuenta en los controladores de 6 GDL</span><span class="sxs-lookup"><span data-stu-id="28f61-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="28f61-164">Antes de llamar a las propiedades en los métodos en un controlador de 6-GDL simulado, debe activar el controlador.</span><span class="sxs-lookup"><span data-stu-id="28f61-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="28f61-165">De no hacerlo, se producirá una excepción.</span><span class="sxs-lookup"><span data-stu-id="28f61-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="28f61-166">A partir de Windows 10 puede actualizar de 2019, se pueden instalar y activar estableciendo la propiedad Status del objeto ISimulatedSixDofController para SimulatedSixDofControllerStatus.Active controladores 6-GDL simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="28f61-167">En el 10 de octubre de 2018 de Windows Update y versiones anteriores, debe instalar por separado un controlador de 6-GDL simulado en primer lugar mediante una llamada a la herramienta PerceptionSimulationDevice ubicada en la carpeta \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="28f61-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="28f61-168">El uso de esta herramienta es como sigue:</span><span class="sxs-lookup"><span data-stu-id="28f61-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="28f61-169">Por ejemplo</span><span class="sxs-lookup"><span data-stu-id="28f61-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="28f61-170">Acciones admitidas son:</span><span class="sxs-lookup"><span data-stu-id="28f61-170">Supported actions are:</span></span>
* <span data-ttu-id="28f61-171">= install</span><span class="sxs-lookup"><span data-stu-id="28f61-171">i = install</span></span>
* <span data-ttu-id="28f61-172">q = consulta</span><span class="sxs-lookup"><span data-stu-id="28f61-172">q = query</span></span>
* <span data-ttu-id="28f61-173">r = quitar</span><span class="sxs-lookup"><span data-stu-id="28f61-173">r = remove</span></span>

<span data-ttu-id="28f61-174">Instancias admitidas son:</span><span class="sxs-lookup"><span data-stu-id="28f61-174">Supported instances are:</span></span>
* <span data-ttu-id="28f61-175">1 = el controlador de 6-GDL izquierdo</span><span class="sxs-lookup"><span data-stu-id="28f61-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="28f61-176">2 = el controlador derecho 6-GDL</span><span class="sxs-lookup"><span data-stu-id="28f61-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="28f61-177">El código de salida del proceso indicará (valor de retorno de un cero) de éxito o error (un valor devuelto distinto de cero).</span><span class="sxs-lookup"><span data-stu-id="28f61-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="28f61-178">Cuando se usa la acción 'q' para consultar si se instala un controlador, el valor devuelto será cero (0) si ya no está instalado el controlador o uno (1) si está instalado el controlador.</span><span class="sxs-lookup"><span data-stu-id="28f61-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="28f61-179">Al quitar un controlador de Windows 10 de octubre de 2018. actualice o anteriores, establece su estado desactivado a través de la API en primer lugar, a continuación, llamar a la herramienta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="28f61-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="28f61-180">Tenga en cuenta que esta herramienta se debe ejecutar como administrador.</span><span class="sxs-lookup"><span data-stu-id="28f61-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="28f61-181">Referencia de API</span><span class="sxs-lookup"><span data-stu-id="28f61-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="28f61-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="28f61-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="28f61-183">Describe un tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="28f61-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="28f61-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="28f61-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="28f61-185">Un dispositivo de referencia ficticia, el valor predeterminado para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="28f61-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="28f61-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="28f61-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="28f61-187">Describe el modo principal de la herramienta de seguimiento</span><span class="sxs-lookup"><span data-stu-id="28f61-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="28f61-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="28f61-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="28f61-189">De forma predeterminada Head de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-189">Default Head Tracking.</span></span> <span data-ttu-id="28f61-190">Esto significa que el sistema puede seleccionar el encabezado mejor según las condiciones de tiempo de ejecución del modo de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="28f61-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="28f61-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="28f61-192">Orientación solo Head seguimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="28f61-193">Esto significa que la posición de seguimiento puede no ser confiable y alguna funcionalidad depende de la posición principal no esté disponible.</span><span class="sxs-lookup"><span data-stu-id="28f61-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="28f61-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="28f61-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="28f61-195">Seguimiento de Head posicional.</span><span class="sxs-lookup"><span data-stu-id="28f61-195">Positional Head Tracking.</span></span> <span data-ttu-id="28f61-196">Esto significa que la posición principal sometidas a seguimiento y la orientación son confiables</span><span class="sxs-lookup"><span data-stu-id="28f61-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="28f61-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="28f61-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="28f61-198">Describe un gesto simulado</span><span class="sxs-lookup"><span data-stu-id="28f61-198">Describes a simulated gesture</span></span>

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

<span data-ttu-id="28f61-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="28f61-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="28f61-200">Un valor de centinela utilizado para no indicar ningún movimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="28f61-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="28f61-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="28f61-202">Un dedo presionado gesto.</span><span class="sxs-lookup"><span data-stu-id="28f61-202">A finger pressed gesture.</span></span>

<span data-ttu-id="28f61-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="28f61-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="28f61-204">Un gesto del dedo publicado.</span><span class="sxs-lookup"><span data-stu-id="28f61-204">A finger released gesture.</span></span>

<span data-ttu-id="28f61-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="28f61-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="28f61-206">El gesto de inicio o de sistema.</span><span class="sxs-lookup"><span data-stu-id="28f61-206">The home/system gesture.</span></span>

<span data-ttu-id="28f61-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="28f61-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="28f61-208">El gesto máximo válido.</span><span class="sxs-lookup"><span data-stu-id="28f61-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="28f61-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="28f61-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="28f61-210">Los Estados posibles de un controlador de 6-GDL simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="28f61-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="28f61-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="28f61-212">El controlador de 6 GDL está desactivado.</span><span class="sxs-lookup"><span data-stu-id="28f61-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="28f61-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="28f61-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="28f61-214">El controlador de 6 GDL está encendido y realiza el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="28f61-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="28f61-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="28f61-216">El controlador de 6 GDL está activado pero no se puede realizar el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="28f61-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="28f61-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="28f61-218">Los botones admitidos en un controlador de 6-GDL simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-218">The supported buttons on a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

<span data-ttu-id="28f61-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="28f61-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="28f61-220">Un valor de centinela utilizado para no indicar ningún botón.</span><span class="sxs-lookup"><span data-stu-id="28f61-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="28f61-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="28f61-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="28f61-222">Se presiona el botón de inicio.</span><span class="sxs-lookup"><span data-stu-id="28f61-222">The Home button is pressed.</span></span>

<span data-ttu-id="28f61-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="28f61-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="28f61-224">Se presiona el botón de menú.</span><span class="sxs-lookup"><span data-stu-id="28f61-224">The Menu button is pressed.</span></span>

<span data-ttu-id="28f61-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="28f61-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="28f61-226">Se presiona el botón de control.</span><span class="sxs-lookup"><span data-stu-id="28f61-226">The Grip button is pressed.</span></span>

<span data-ttu-id="28f61-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="28f61-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="28f61-228">El panel táctil está presionado.</span><span class="sxs-lookup"><span data-stu-id="28f61-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="28f61-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="28f61-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="28f61-230">Se presiona el botón de selección.</span><span class="sxs-lookup"><span data-stu-id="28f61-230">The Select button is pressed.</span></span>

<span data-ttu-id="28f61-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="28f61-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="28f61-232">Se toca la pantalla táctil.</span><span class="sxs-lookup"><span data-stu-id="28f61-232">The TouchPad is touched.</span></span>

<span data-ttu-id="28f61-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="28f61-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="28f61-234">Se presiona la tecla de navegación.</span><span class="sxs-lookup"><span data-stu-id="28f61-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="28f61-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="28f61-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="28f61-236">El número máximo de botones válido.</span><span class="sxs-lookup"><span data-stu-id="28f61-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="28f61-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="28f61-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="28f61-238">El estado de calibración de los ojos simulados</span><span class="sxs-lookup"><span data-stu-id="28f61-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="28f61-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="28f61-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="28f61-240">No está disponible la calibración de ojos.</span><span class="sxs-lookup"><span data-stu-id="28f61-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="28f61-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="28f61-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="28f61-242">Han sido calibrados los ojos.</span><span class="sxs-lookup"><span data-stu-id="28f61-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="28f61-243">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="28f61-243">This is the default value.</span></span>

<span data-ttu-id="28f61-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="28f61-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="28f61-245">Se está calibran los ojos.</span><span class="sxs-lookup"><span data-stu-id="28f61-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="28f61-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="28f61-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="28f61-247">Los ojos necesitan calibrarse.</span><span class="sxs-lookup"><span data-stu-id="28f61-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="28f61-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="28f61-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="28f61-249">La precisión de seguimiento de una unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="28f61-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="28f61-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="28f61-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="28f61-251">No se realiza el seguimiento de la unión.</span><span class="sxs-lookup"><span data-stu-id="28f61-251">The joint is not tracked.</span></span>

<span data-ttu-id="28f61-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="28f61-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="28f61-253">La posición conjunta se infiere.</span><span class="sxs-lookup"><span data-stu-id="28f61-253">The joint position is inferred.</span></span>

<span data-ttu-id="28f61-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="28f61-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="28f61-255">La junta totalmente se realiza un seguimiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="28f61-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="28f61-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="28f61-257">La precisión de seguimiento de una unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="28f61-257">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

<span data-ttu-id="28f61-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="28f61-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="28f61-259">Las uniones de la mano dedo se configuren para reflejar una postura cerrado.</span><span class="sxs-lookup"><span data-stu-id="28f61-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="28f61-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="28f61-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="28f61-261">Las uniones de la mano dedo se configuren para reflejar una postura abierta.</span><span class="sxs-lookup"><span data-stu-id="28f61-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="28f61-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="28f61-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="28f61-263">Las uniones de la mano dedo se configuren para reflejar una postura señalador.</span><span class="sxs-lookup"><span data-stu-id="28f61-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="28f61-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="28f61-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="28f61-265">Las uniones de la mano dedo se configuren para reflejar una postura alejamiento.</span><span class="sxs-lookup"><span data-stu-id="28f61-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="28f61-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="28f61-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="28f61-267">El máximo valor válido para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="28f61-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="28f61-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="28f61-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="28f61-269">Describe el estado de una reproducción.</span><span class="sxs-lookup"><span data-stu-id="28f61-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="28f61-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="28f61-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="28f61-271">La grabación está actualmente detenido y listo para su reproducción.</span><span class="sxs-lookup"><span data-stu-id="28f61-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="28f61-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="28f61-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="28f61-273">La grabación se está reproduciendo.</span><span class="sxs-lookup"><span data-stu-id="28f61-273">The recording is currently playing.</span></span>

<span data-ttu-id="28f61-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="28f61-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="28f61-275">Actualmente está en pausa la grabación.</span><span class="sxs-lookup"><span data-stu-id="28f61-275">The recording is currently paused.</span></span>

<span data-ttu-id="28f61-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="28f61-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="28f61-277">La grabación ha llegado al final.</span><span class="sxs-lookup"><span data-stu-id="28f61-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="28f61-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="28f61-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="28f61-279">Describe un vector de 3 componentes, que se puede describir un punto o un vector en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="28f61-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="28f61-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="28f61-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="28f61-281">Componente X del vector.</span><span class="sxs-lookup"><span data-stu-id="28f61-281">The X component of the vector.</span></span>

<span data-ttu-id="28f61-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="28f61-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="28f61-283">El componente Y del vector.</span><span class="sxs-lookup"><span data-stu-id="28f61-283">The Y component of the vector.</span></span>

<span data-ttu-id="28f61-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="28f61-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="28f61-285">Componente Z del vector.</span><span class="sxs-lookup"><span data-stu-id="28f61-285">The Z component of the vector.</span></span>

<span data-ttu-id="28f61-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="28f61-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="28f61-287">Construir un nuevo Vector3.</span><span class="sxs-lookup"><span data-stu-id="28f61-287">Construct a new Vector3.</span></span>

<span data-ttu-id="28f61-288">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-288">Parameters</span></span>
* <span data-ttu-id="28f61-289">x: el componente x del vector.</span><span class="sxs-lookup"><span data-stu-id="28f61-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="28f61-290">y - el componente y del vector.</span><span class="sxs-lookup"><span data-stu-id="28f61-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="28f61-291">z - el componente z del vector.</span><span class="sxs-lookup"><span data-stu-id="28f61-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="28f61-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="28f61-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="28f61-293">Describe un giro de 3 componentes.</span><span class="sxs-lookup"><span data-stu-id="28f61-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="28f61-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="28f61-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="28f61-295">El componente de punto de rotación, abajo alrededor del eje X.</span><span class="sxs-lookup"><span data-stu-id="28f61-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="28f61-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="28f61-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="28f61-297">El componente de rotación de la rotación, justo en el eje Y.</span><span class="sxs-lookup"><span data-stu-id="28f61-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="28f61-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="28f61-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="28f61-299">El componente de rollo de rotación, justo en el eje Z.</span><span class="sxs-lookup"><span data-stu-id="28f61-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="28f61-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="28f61-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="28f61-301">Construir un nuevo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="28f61-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="28f61-302">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-302">Parameters</span></span>
* <span data-ttu-id="28f61-303">pitch: el componente de tono de la rotación.</span><span class="sxs-lookup"><span data-stu-id="28f61-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="28f61-304">guiñada: el componente de rotación de la rotación.</span><span class="sxs-lookup"><span data-stu-id="28f61-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="28f61-305">Resumen: el componente de lanzamiento de la rotación.</span><span class="sxs-lookup"><span data-stu-id="28f61-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="28f61-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="28f61-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="28f61-307">Describe la configuración de una unión en una mano simulada.</span><span class="sxs-lookup"><span data-stu-id="28f61-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="28f61-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="28f61-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="28f61-309">La posición de la unión.</span><span class="sxs-lookup"><span data-stu-id="28f61-309">The position of the joint.</span></span>

<span data-ttu-id="28f61-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="28f61-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="28f61-311">La rotación de la unión.</span><span class="sxs-lookup"><span data-stu-id="28f61-311">The rotation of the joint.</span></span>

<span data-ttu-id="28f61-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="28f61-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="28f61-313">La precisión de seguimiento de la unión.</span><span class="sxs-lookup"><span data-stu-id="28f61-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="28f61-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="28f61-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="28f61-315">Describe un frustum de visualización, como suele ser utilizado por una cámara.</span><span class="sxs-lookup"><span data-stu-id="28f61-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="28f61-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="28f61-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="28f61-317">La distancia mínima que se encuentra en el frustum.</span><span class="sxs-lookup"><span data-stu-id="28f61-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="28f61-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="28f61-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="28f61-319">La distancia máxima a la que se encuentra en el frustum.</span><span class="sxs-lookup"><span data-stu-id="28f61-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="28f61-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="28f61-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="28f61-321">Campo de visión horizontal de frustum, en radianes (menos de PI).</span><span class="sxs-lookup"><span data-stu-id="28f61-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="28f61-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="28f61-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="28f61-323">La proporción de campo de visión horizontal a vertical campo de visión.</span><span class="sxs-lookup"><span data-stu-id="28f61-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="28f61-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="28f61-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="28f61-325">Raíz para generar los paquetes utilizados para controlar un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="28f61-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="28f61-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="28f61-327">Recuperar el objeto de dispositivo simulado que interpreta los humanos simulado y el mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="28f61-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="28f61-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="28f61-329">Recuperar el objeto que controla a los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="28f61-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="28f61-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="28f61-331">La simulación se restablece a su estado predeterminado.</span><span class="sxs-lookup"><span data-stu-id="28f61-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="28f61-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="28f61-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="28f61-333">Interfaz que describe el dispositivo que interpreta el mundo simulado y el usuario simulado</span><span class="sxs-lookup"><span data-stu-id="28f61-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="28f61-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="28f61-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="28f61-335">Recuperar el Rastreador de Head del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="28f61-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="28f61-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="28f61-337">Recuperar el Rastreador de mano desde el dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="28f61-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="28f61-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="28f61-339">Establecer las propiedades del dispositivo simulado para que coincida con el tipo de dispositivo proporcionado.</span><span class="sxs-lookup"><span data-stu-id="28f61-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="28f61-340">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-340">Parameters</span></span>
* <span data-ttu-id="28f61-341">tipo: el nuevo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="28f61-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="28f61-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="28f61-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="28f61-343">Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de la cabeza de los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="28f61-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="28f61-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="28f61-345">Recupera y establece el modo de seguimiento principal actual.</span><span class="sxs-lookup"><span data-stu-id="28f61-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="28f61-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="28f61-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="28f61-347">Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de las manos de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="28f61-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

<span data-ttu-id="28f61-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="28f61-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="28f61-349">Recuperar la posición del nodo con respecto a la del mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="28f61-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="28f61-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="28f61-351">Recuperar y establecer la posición de la herramienta de seguimiento de la mano simulado, en relación con el centro de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="28f61-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="28f61-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="28f61-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="28f61-353">Recuperar y establecer el tono hacia abajo de la herramienta de seguimiento de la mano simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="28f61-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="28f61-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="28f61-355">Recuperar y establecer si se omite el frustum del Rastreador de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="28f61-356">Cuando se omite, dos manos siempre están visibles.</span><span class="sxs-lookup"><span data-stu-id="28f61-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="28f61-357">Cuando no pasa por alto (predeterminado) manos solamente están visibles cuando estén dentro del frustum del Rastreador de mano.</span><span class="sxs-lookup"><span data-stu-id="28f61-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="28f61-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="28f61-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="28f61-359">Recuperar y establecer las propiedades de frustum utilizadas para determinar si son visibles para el seguimiento de la mano simulado manos.</span><span class="sxs-lookup"><span data-stu-id="28f61-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="28f61-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="28f61-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="28f61-361">Interfaz de nivel superior para controlar a los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-361">Top level interface for controlling the simulated human.</span></span>

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

<span data-ttu-id="28f61-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="28f61-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="28f61-363">Recuperar y establecer la posición del nodo con respecto a la del mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="28f61-364">La posición corresponde a un punto en el centro de metros del humanos.</span><span class="sxs-lookup"><span data-stu-id="28f61-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="28f61-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="28f61-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="28f61-366">Recuperar y establecer las caras humanas simuladas de la dirección en el mundo.</span><span class="sxs-lookup"><span data-stu-id="28f61-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="28f61-367">0 radianes se enfrenta al eje Z negativo.</span><span class="sxs-lookup"><span data-stu-id="28f61-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="28f61-368">Rotación radianes positivos sobre el eje Y.</span><span class="sxs-lookup"><span data-stu-id="28f61-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="28f61-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="28f61-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="28f61-370">Recuperar y establecer el alto de los humanos simulado, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="28f61-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="28f61-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="28f61-372">Recuperar la parte izquierda de los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="28f61-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="28f61-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="28f61-374">Recuperar la parte derecha de los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="28f61-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="28f61-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="28f61-376">Recuperar el encabezado de los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="28f61-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="28f61-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="28f61-378">Mueva a los humanos simulado respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="28f61-379">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-379">Parameters</span></span>
* <span data-ttu-id="28f61-380">traducción: la traducción que se mueven en relación con la posición actual.</span><span class="sxs-lookup"><span data-stu-id="28f61-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="28f61-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="28f61-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="28f61-382">Girar a los humanos simulado con respecto a su dirección actual, las agujas del reloj sobre el eje Y</span><span class="sxs-lookup"><span data-stu-id="28f61-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="28f61-383">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-383">Parameters</span></span>
* <span data-ttu-id="28f61-384">radianes - la cantidad que se va a girar alrededor del eje Y.</span><span class="sxs-lookup"><span data-stu-id="28f61-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="28f61-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="28f61-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="28f61-386">Propiedades adicionales están disponibles al convertir el ISimulatedHuman a ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="28f61-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="28f61-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="28f61-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="28f61-388">Recuperar el controlador de 6-GDL izquierdo.</span><span class="sxs-lookup"><span data-stu-id="28f61-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="28f61-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="28f61-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="28f61-390">Recuperar el controlador derecho 6-GDL.</span><span class="sxs-lookup"><span data-stu-id="28f61-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="28f61-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="28f61-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="28f61-392">Interfaz que describe una mano de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="28f61-392">Interface describing a hand of the simulated human</span></span>

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

<span data-ttu-id="28f61-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="28f61-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="28f61-394">Recuperar la posición del nodo con respecto a la del mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="28f61-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="28f61-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="28f61-396">Recuperar y establecer la posición de la mano simulada con respecto a los humanos, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="28f61-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="28f61-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="28f61-398">Recuperar y establecer si está activada actualmente la mano.</span><span class="sxs-lookup"><span data-stu-id="28f61-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="28f61-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="28f61-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="28f61-400">Recuperar datos si la mano está actualmente visible para el SimulatedDevice (es decir, si está en una posición para ser detectado por el HandTracker).</span><span class="sxs-lookup"><span data-stu-id="28f61-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="28f61-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="28f61-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="28f61-402">Mover la mano de manera que es visible para el SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="28f61-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="28f61-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="28f61-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="28f61-404">Mover la posición de la mano simulada respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="28f61-405">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-405">Parameters</span></span>
* <span data-ttu-id="28f61-406">traducción: la cantidad de traslación de la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="28f61-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="28f61-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="28f61-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="28f61-408">Realizar un gesto de la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="28f61-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="28f61-409">Solo se detectará el sistema si está habilitada la mano.</span><span class="sxs-lookup"><span data-stu-id="28f61-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="28f61-410">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-410">Parameters</span></span>
* <span data-ttu-id="28f61-411">gesto - gesto que se realice.</span><span class="sxs-lookup"><span data-stu-id="28f61-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="28f61-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="28f61-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="28f61-413">Propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="28f61-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="28f61-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="28f61-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="28f61-415">Recuperar o establecer el giro de la mano simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="28f61-416">Radianes giran a la derecha al buscar en el eje positivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="28f61-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="28f61-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="28f61-418">Propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="28f61-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="28f61-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="28f61-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="28f61-420">Obtenga la configuración común para la unión especificada.</span><span class="sxs-lookup"><span data-stu-id="28f61-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="28f61-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="28f61-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="28f61-422">Establezca la configuración común para la unión especificada.</span><span class="sxs-lookup"><span data-stu-id="28f61-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="28f61-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="28f61-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="28f61-424">Establezca la mano para una postura conocido con una marca opcional que se va a animar.</span><span class="sxs-lookup"><span data-stu-id="28f61-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="28f61-425">Nota: la animación no origine articulaciones inmediatamente que refleja las configuraciones finales conjuntas.</span><span class="sxs-lookup"><span data-stu-id="28f61-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="28f61-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="28f61-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="28f61-427">Interfaz que describe el encabezado de los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="28f61-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="28f61-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="28f61-429">Recuperar la posición del nodo con respecto a la del mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="28f61-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="28f61-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="28f61-431">Recuperar la rotación de la cabeza simulada.</span><span class="sxs-lookup"><span data-stu-id="28f61-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="28f61-432">Radianes giran a la derecha al buscar en el eje positivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="28f61-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="28f61-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="28f61-434">Recuperar el diámetro del encabezado simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="28f61-435">Este valor se utiliza para determinar el centro del encabezado (punto de giro).</span><span class="sxs-lookup"><span data-stu-id="28f61-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="28f61-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="28f61-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="28f61-437">Girar la cabeza simulada con respecto a su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="28f61-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="28f61-438">Radianes giran a la derecha al buscar en el eje positivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="28f61-439">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-439">Parameters</span></span>
* <span data-ttu-id="28f61-440">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="28f61-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="28f61-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="28f61-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="28f61-442">Propiedades adicionales están disponibles mediante la conversión de un ISimulatedHead a ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="28f61-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="28f61-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="28f61-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="28f61-444">Recuperar los ojos de los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="28f61-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="28f61-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="28f61-446">Interfaz que describe un controlador de 6 GDL asociado con el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

<span data-ttu-id="28f61-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="28f61-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="28f61-448">Recuperar la posición del nodo con respecto a la del mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="28f61-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="28f61-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="28f61-450">Recuperar o establecer el estado actual del controlador.</span><span class="sxs-lookup"><span data-stu-id="28f61-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="28f61-451">El estado del controlador debe establecerse en un valor distinto de desactivado antes de llamar a mover, girar o presione los botones se realizará correctamente.</span><span class="sxs-lookup"><span data-stu-id="28f61-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="28f61-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="28f61-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="28f61-453">Recuperar o establecer la posición del controlador simulado con respecto a los humanos, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="28f61-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="28f61-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="28f61-455">Recuperar o establecer la orientación del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="28f61-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="28f61-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="28f61-457">Mover la posición del controlador simulado respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="28f61-458">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-458">Parameters</span></span>
* <span data-ttu-id="28f61-459">traducción: la cantidad de traslación del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="28f61-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="28f61-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="28f61-461">Presione un botón en el dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="28f61-462">Solo se detectará el sistema si está habilitado el controlador.</span><span class="sxs-lookup"><span data-stu-id="28f61-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="28f61-463">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-463">Parameters</span></span>
* <span data-ttu-id="28f61-464">botón: presione el botón.</span><span class="sxs-lookup"><span data-stu-id="28f61-464">button - The button to press.</span></span>

<span data-ttu-id="28f61-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="28f61-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="28f61-466">Suelte un botón en el dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="28f61-467">Solo se detectará el sistema si está habilitado el controlador.</span><span class="sxs-lookup"><span data-stu-id="28f61-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="28f61-468">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-468">Parameters</span></span>
* <span data-ttu-id="28f61-469">botón: el botón va a liberar.</span><span class="sxs-lookup"><span data-stu-id="28f61-469">button - The button to release.</span></span>

<span data-ttu-id="28f61-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="28f61-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="28f61-471">Obtiene la posición de un dedo simulado en el panel táctil del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="28f61-472">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-472">Parameters</span></span>
* <span data-ttu-id="28f61-473">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="28f61-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="28f61-474">y - la posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="28f61-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="28f61-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="28f61-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="28f61-476">Establezca la posición de un dedo simulado en el panel táctil del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="28f61-477">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-477">Parameters</span></span>
* <span data-ttu-id="28f61-478">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="28f61-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="28f61-479">y - la posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="28f61-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="28f61-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="28f61-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="28f61-481">Métodos y propiedades adicionales están disponibles mediante la conversión de un ISimulatedSixDofController a ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="28f61-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="28f61-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="28f61-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="28f61-483">Obtiene la posición de la tecla de navegación simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="28f61-484">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-484">Parameters</span></span>
* <span data-ttu-id="28f61-485">x: la posición horizontal de la tecla de navegación.</span><span class="sxs-lookup"><span data-stu-id="28f61-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="28f61-486">y - la posición vertical de la tecla de navegación.</span><span class="sxs-lookup"><span data-stu-id="28f61-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="28f61-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="28f61-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="28f61-488">Establezca la posición de la tecla de navegación simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="28f61-489">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-489">Parameters</span></span>
* <span data-ttu-id="28f61-490">x: la posición horizontal de la tecla de navegación.</span><span class="sxs-lookup"><span data-stu-id="28f61-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="28f61-491">y - la posición vertical de la tecla de navegación.</span><span class="sxs-lookup"><span data-stu-id="28f61-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="28f61-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="28f61-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="28f61-493">Recuperar o establecer el nivel de batería del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="28f61-494">El valor debe ser mayor que 0,0 y menor o igual que 100,0.</span><span class="sxs-lookup"><span data-stu-id="28f61-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="28f61-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="28f61-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="28f61-496">Interfaz que describe los ojos de los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="28f61-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="28f61-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="28f61-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="28f61-498">Recuperar la rotación de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="28f61-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="28f61-499">Radianes giran a la derecha al buscar en el eje positivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="28f61-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="28f61-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="28f61-501">Gira los ojos simulados en relación con su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="28f61-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="28f61-502">Radianes giran a la derecha al buscar en el eje positivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="28f61-503">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-503">Parameters</span></span>
* <span data-ttu-id="28f61-504">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="28f61-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="28f61-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="28f61-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="28f61-506">Recupera o establece el estado de calibración de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="28f61-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="28f61-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="28f61-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="28f61-508">Recuperar la posición del nodo con respecto a la del mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="28f61-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="28f61-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="28f61-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="28f61-510">Cargar la interfaz para interactuar con una grabación única para la reproducción.</span><span class="sxs-lookup"><span data-stu-id="28f61-510">Interface for interacting with a single recording loaded for playback.</span></span>

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

<span data-ttu-id="28f61-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="28f61-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="28f61-512">Recupera la lista de tipos de datos en la grabación.</span><span class="sxs-lookup"><span data-stu-id="28f61-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="28f61-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="28f61-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="28f61-514">Recupera el estado actual de la grabación.</span><span class="sxs-lookup"><span data-stu-id="28f61-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="28f61-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="28f61-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="28f61-516">Iniciar la reproducción.</span><span class="sxs-lookup"><span data-stu-id="28f61-516">Start the playback.</span></span> <span data-ttu-id="28f61-517">Si está en pausa la grabación, reproducción se reanudará desde la ubicación en pausa; Si se detiene, se iniciará la reproducción al principio.</span><span class="sxs-lookup"><span data-stu-id="28f61-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="28f61-518">Si ya está reproduciendo, se omite esta llamada.</span><span class="sxs-lookup"><span data-stu-id="28f61-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="28f61-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="28f61-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="28f61-520">Pone en pausa la reproducción en su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="28f61-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="28f61-521">Si se detiene la grabación, se omite la llamada.</span><span class="sxs-lookup"><span data-stu-id="28f61-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="28f61-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="28f61-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="28f61-523">Busca la grabación a la hora especificada (en intervalos de 100 nanosegundos desde el principio) y se detiene en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="28f61-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="28f61-524">Si el tiempo es más allá del final de la grabación, está en pausa en el último fotograma.</span><span class="sxs-lookup"><span data-stu-id="28f61-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="28f61-525">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-525">Parameters</span></span>
* <span data-ttu-id="28f61-526">tics: el tiempo que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="28f61-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="28f61-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="28f61-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="28f61-528">Detiene la reproducción y restablece la posición al principio.</span><span class="sxs-lookup"><span data-stu-id="28f61-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="28f61-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="28f61-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="28f61-530">Interfaz para recibir los cambios de estado durante la reproducción.</span><span class="sxs-lookup"><span data-stu-id="28f61-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="28f61-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="28f61-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="28f61-532">Se llama cuando ha cambiado el estado de reproducción de un ISimulationRecording.</span><span class="sxs-lookup"><span data-stu-id="28f61-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="28f61-533">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-533">Parameters</span></span>
* <span data-ttu-id="28f61-534">newState - el nuevo estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="28f61-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="28f61-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="28f61-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="28f61-536">Objeto raíz para crear objetos de simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="28f61-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="28f61-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="28f61-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="28f61-538">Crear en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.</span><span class="sxs-lookup"><span data-stu-id="28f61-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="28f61-539">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-539">Parameters</span></span>
* <span data-ttu-id="28f61-540">Sink - el receptor que recibirá todos genera paquetes.</span><span class="sxs-lookup"><span data-stu-id="28f61-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="28f61-541">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="28f61-541">Return value</span></span>

<span data-ttu-id="28f61-542">El administrador creado.</span><span class="sxs-lookup"><span data-stu-id="28f61-542">The created Manager.</span></span>

<span data-ttu-id="28f61-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="28f61-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="28f61-544">Crear un receptor que almacena los paquetes recibidos todo en un archivo en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="28f61-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="28f61-545">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-545">Parameters</span></span>
* <span data-ttu-id="28f61-546">ruta de acceso: la ruta de acceso del archivo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="28f61-546">path - The path of the file to create.</span></span>

<span data-ttu-id="28f61-547">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="28f61-547">Return value</span></span>

<span data-ttu-id="28f61-548">El receptor creado.</span><span class="sxs-lookup"><span data-stu-id="28f61-548">The created sink.</span></span>

<span data-ttu-id="28f61-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="28f61-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="28f61-550">Cargar una grabación desde el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="28f61-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="28f61-551">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-551">Parameters</span></span>
* <span data-ttu-id="28f61-552">ruta de acceso: la ruta de acceso del archivo para cargar.</span><span class="sxs-lookup"><span data-stu-id="28f61-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="28f61-553">Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="28f61-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="28f61-554">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="28f61-554">Return value</span></span>

<span data-ttu-id="28f61-555">La grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="28f61-555">The loaded recording.</span></span>

<span data-ttu-id="28f61-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="28f61-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="28f61-557">Cargar una grabación desde el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="28f61-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="28f61-558">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-558">Parameters</span></span>
* <span data-ttu-id="28f61-559">ruta de acceso: la ruta de acceso del archivo para cargar.</span><span class="sxs-lookup"><span data-stu-id="28f61-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="28f61-560">Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="28f61-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="28f61-561">devolución de llamada - una devolución de llamada que recibe las actualizaciones reclasificación de estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="28f61-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="28f61-562">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="28f61-562">Return value</span></span>

<span data-ttu-id="28f61-563">La grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="28f61-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="28f61-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="28f61-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="28f61-565">Describe los diferentes tipos de datos de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="28f61-565">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

<span data-ttu-id="28f61-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="28f61-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="28f61-567">Un valor de centinela utilizado para no indicar ningún tipo de datos de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="28f61-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="28f61-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="28f61-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="28f61-569">Stream de datos con respecto a la posición y la orientación de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="28f61-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="28f61-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="28f61-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="28f61-571">Stream de datos con respecto a la posición y movimientos de manos.</span><span class="sxs-lookup"><span data-stu-id="28f61-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="28f61-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="28f61-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="28f61-573">Stream de datos con respecto a la asignación espacial del entorno.</span><span class="sxs-lookup"><span data-stu-id="28f61-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="28f61-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="28f61-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="28f61-575">Stream de datos con respecto a la calibración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="28f61-576">Solo se aceptan los paquetes de calibración mediante un sistema en modo remoto.</span><span class="sxs-lookup"><span data-stu-id="28f61-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="28f61-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="28f61-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="28f61-578">Stream de datos relacionados con el entorno del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="28f61-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="28f61-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="28f61-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="28f61-580">Un valor de centinela que se usa para indicar todos los tipos de datos registrados.</span><span class="sxs-lookup"><span data-stu-id="28f61-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="28f61-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="28f61-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="28f61-582">Un objeto que recibe los paquetes de datos de una secuencia de simulación.</span><span class="sxs-lookup"><span data-stu-id="28f61-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="28f61-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="28f61-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="28f61-584">Recibe un solo paquete, que es internamente con tipo y con control de versiones.</span><span class="sxs-lookup"><span data-stu-id="28f61-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="28f61-585">Parámetros</span><span class="sxs-lookup"><span data-stu-id="28f61-585">Parameters</span></span>
* <span data-ttu-id="28f61-586">length: la longitud del paquete.</span><span class="sxs-lookup"><span data-stu-id="28f61-586">length - The length of the packet.</span></span>
* <span data-ttu-id="28f61-587">paquete - los datos del paquete.</span><span class="sxs-lookup"><span data-stu-id="28f61-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="28f61-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="28f61-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="28f61-589">Objeto que crea ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="28f61-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="28f61-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="28f61-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="28f61-591">Crea una instancia única de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="28f61-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="28f61-592">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="28f61-592">Return value</span></span>

<span data-ttu-id="28f61-593">El receptor creado.</span><span class="sxs-lookup"><span data-stu-id="28f61-593">The created sink.</span></span>
