---
title: Simulación de percepción
description: Una guía para utilizar la biblioteca de simulación de percepción para automatizar la entrada simulada para aplicaciones envolventes
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, simulación, las pruebas
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602207"
---
# <a name="perception-simulation"></a><span data-ttu-id="11fe7-104">Simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="11fe7-104">Perception simulation</span></span>

<span data-ttu-id="11fe7-105">¿Desea crear una prueba automatizada de la aplicación?</span><span class="sxs-lookup"><span data-stu-id="11fe7-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="11fe7-106">¿Desea que las pruebas para ir más allá de las pruebas unitarias de nivel de componente y realmente ejercitar su aplicación-to-end?</span><span class="sxs-lookup"><span data-stu-id="11fe7-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="11fe7-107">Simulación de percepción es lo está buscando.</span><span class="sxs-lookup"><span data-stu-id="11fe7-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="11fe7-108">La biblioteca de simulación de percepción envía humanos falsa y datos de entrada del mundo a la aplicación para que pueda automatizar las pruebas.</span><span class="sxs-lookup"><span data-stu-id="11fe7-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="11fe7-109">Por ejemplo, puede simular la entrada de un aspecto humano izquierda y derecha y, a continuación, realizar un gesto.</span><span class="sxs-lookup"><span data-stu-id="11fe7-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="11fe7-110">Simulación de percepción puede enviar entrada simulado así un HoloLens físico, el emulador de HoloLens o un equipo con el Portal de realidad mixta instalado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="11fe7-111">Percepción simulación omite los sensores en directo en un dispositivo de realidad mixta y envía simula la entrada para aplicaciones que se ejecutan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="11fe7-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="11fe7-112">Las aplicaciones reciben estos eventos de entrada falsos a través de las mismas API siempre usan y no se puede indicar la diferencia entre la ejecución con sensores reales frente a ejecutar con la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="11fe7-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="11fe7-113">Simulación de percepción es la misma tecnología que utiliza el emulador de HoloLens enviar la entrada simulado a la máquina Virtual de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="11fe7-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="11fe7-114">Simulación empieza por crear un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="11fe7-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="11fe7-115">Desde ese objeto, puede emitir comandos para controlar las propiedades de un simulado "humano", incluida la posición principal, la posición de la mano y los gestos.</span><span class="sxs-lookup"><span data-stu-id="11fe7-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="11fe7-116">Configuración de un proyecto de Visual Studio para la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="11fe7-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="11fe7-117">[Instalar el emulador de HoloLens](install-the-tools.md) en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="11fe7-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="11fe7-118">El emulador incluye las bibliotecas que se va a usar para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="11fe7-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="11fe7-119">Crear un nuevo Visual Studio C# proyecto de escritorio (un proyecto de consola funciona bien para empezar a trabajar).</span><span class="sxs-lookup"><span data-stu-id="11fe7-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="11fe7-120">Agregue los siguientes archivos binarios al proyecto como referencias (proyecto -> Agregar -> referencia...). Puede encontrarlos en **% ProgramFiles (x86) %\Microsoft XDE\10.0.11082.0** una.</span><span class="sxs-lookup"><span data-stu-id="11fe7-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="11fe7-121">PerceptionSimulationManager.Interop.dll - Managed C# contenedor para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="11fe7-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="11fe7-122">b.</span><span class="sxs-lookup"><span data-stu-id="11fe7-122">b.</span></span> <span data-ttu-id="11fe7-123">PerceptionSimulationRest.dll - Library para configurar un canal de comunicación de socket web al HoloLens o emulador.</span><span class="sxs-lookup"><span data-stu-id="11fe7-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="11fe7-124">c.</span><span class="sxs-lookup"><span data-stu-id="11fe7-124">c.</span></span> <span data-ttu-id="11fe7-125">SimulationStream.Interop.dll - tipos compartidos para la simulación.</span><span class="sxs-lookup"><span data-stu-id="11fe7-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="11fe7-126">Agregue la implementación PerceptionSimulationManager.dll binarios al proyecto una.</span><span class="sxs-lookup"><span data-stu-id="11fe7-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="11fe7-127">En primer lugar agregarlo al proyecto como un archivo binario (proyecto -> Agregar -> elemento existente...). Guárdelo como un vínculo para que no copiarlo a la carpeta de origen del proyecto.</span><span class="sxs-lookup"><span data-stu-id="11fe7-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="11fe7-128">![Agregar al proyecto como un vínculo PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="11fe7-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="11fe7-129">A continuación, asegúrese de que lo de la copia en la carpeta de salida en la compilación.</span><span class="sxs-lookup"><span data-stu-id="11fe7-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="11fe7-130">Se trata en la hoja de propiedades para el archivo binario.</span><span class="sxs-lookup"><span data-stu-id="11fe7-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="11fe7-131">![Marcar PerceptionSimulationManager.dll para copiar en el directorio de salida](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="11fe7-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="11fe7-132">Creación de un objeto de administrador IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="11fe7-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="11fe7-133">Para controlar la simulación, deberá emitir las actualizaciones a los objetos recuperados de un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="11fe7-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="11fe7-134">El primer paso es obtener ese objeto y conectarlo a su emulador o dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="11fe7-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="11fe7-135">Puede obtener la dirección IP de su emulador, haga clic en el botón de Portal de dispositivos en el [barra de herramientas](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="11fe7-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="11fe7-136">![Icono de dispositivo Portal abierta](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra el Windows Device Portal para el sistema operativo de HoloLens en el emulador.</span><span class="sxs-lookup"><span data-stu-id="11fe7-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="11fe7-137">En primer lugar, llamaremos a RestSimulationStreamSink.Create para obtener un objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="11fe7-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="11fe7-138">Este es el dispositivo de destino o el emulador que se controlan a través de una conexión http.</span><span class="sxs-lookup"><span data-stu-id="11fe7-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="11fe7-139">Se pasa a los comandos y controla el [Windows Device Portal](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="11fe7-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="11fe7-140">Los cuatro parámetros que deberá crear un objeto son:</span><span class="sxs-lookup"><span data-stu-id="11fe7-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="11fe7-141">Uri de URI: dirección IP del dispositivo de destino (por ejemplo, "http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="11fe7-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="11fe7-142">System.Net.NetworkCredential credenciales: nombre de usuario y contraseña para conectarse a la [Windows Device Portal](using-the-windows-device-portal.md) en el emulador o dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="11fe7-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="11fe7-143">Si va a conectar al emulador a través de su 168 local. *.* . \* dirección en el mismo equipo, se aceptan las credenciales.</span><span class="sxs-lookup"><span data-stu-id="11fe7-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="11fe7-144">normal: bool es True para una prioridad normal, false de prioridad baja.</span><span class="sxs-lookup"><span data-stu-id="11fe7-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="11fe7-145">Por lo general desea establecerlo en *true* para escenarios de prueba.</span><span class="sxs-lookup"><span data-stu-id="11fe7-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="11fe7-146">Elemento System.Threading.CancellationToken token: Token para cancelar la operación asincrónica.</span><span class="sxs-lookup"><span data-stu-id="11fe7-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="11fe7-147">En segundo lugar, cree el IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="11fe7-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="11fe7-148">Este es el objeto que se usa para controlar la simulación.</span><span class="sxs-lookup"><span data-stu-id="11fe7-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="11fe7-149">Tenga en cuenta que esto también se debe realizar en un método asincrónico.</span><span class="sxs-lookup"><span data-stu-id="11fe7-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="11fe7-150">Controlar a los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-150">Control the simulated Human</span></span>

<span data-ttu-id="11fe7-151">Un IPerceptionSimulationManager tiene una propiedad humana que devuelve un objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="11fe7-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="11fe7-152">Para controlar a los humanos simulado, realizar operaciones en este objeto.</span><span class="sxs-lookup"><span data-stu-id="11fe7-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="11fe7-153">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="11fe7-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="11fe7-154">Ejemplo básico C# aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="11fe7-154">Basic Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="11fe7-155">Extended ejemplo C# aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="11fe7-155">Extended Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

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
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="11fe7-156">Referencia de API</span><span class="sxs-lookup"><span data-stu-id="11fe7-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="11fe7-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="11fe7-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="11fe7-158">Describe un tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="11fe7-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="11fe7-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="11fe7-160">Un dispositivo de referencia ficticia, el valor predeterminado para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="11fe7-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="11fe7-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="11fe7-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="11fe7-162">Describe el modo principal de la herramienta de seguimiento</span><span class="sxs-lookup"><span data-stu-id="11fe7-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="11fe7-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="11fe7-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="11fe7-164">De forma predeterminada Head de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="11fe7-164">Default Head Tracking.</span></span> <span data-ttu-id="11fe7-165">Esto significa que el sistema puede seleccionar el encabezado mejor según las condiciones de tiempo de ejecución del modo de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="11fe7-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="11fe7-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="11fe7-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="11fe7-167">Orientación solo Head seguimiento.</span><span class="sxs-lookup"><span data-stu-id="11fe7-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="11fe7-168">Esto significa que la posición de seguimiento puede no ser confiable y alguna funcionalidad depende de la posición principal no esté disponible.</span><span class="sxs-lookup"><span data-stu-id="11fe7-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="11fe7-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="11fe7-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="11fe7-170">Seguimiento de Head posicional.</span><span class="sxs-lookup"><span data-stu-id="11fe7-170">Positional Head Tracking.</span></span> <span data-ttu-id="11fe7-171">Esto significa que la posición principal sometidas a seguimiento y la orientación son confiables</span><span class="sxs-lookup"><span data-stu-id="11fe7-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="11fe7-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="11fe7-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="11fe7-173">Describe un gesto simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-173">Describes a simulated gesture</span></span>

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

<span data-ttu-id="11fe7-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="11fe7-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="11fe7-175">Un valor de centinela utilizado para no indicar ningún gestos</span><span class="sxs-lookup"><span data-stu-id="11fe7-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="11fe7-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="11fe7-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="11fe7-177">Un dedo presionada gesto</span><span class="sxs-lookup"><span data-stu-id="11fe7-177">A finger pressed gesture</span></span>

<span data-ttu-id="11fe7-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="11fe7-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="11fe7-179">Un gesto del dedo publicado</span><span class="sxs-lookup"><span data-stu-id="11fe7-179">A finger released gesture</span></span>

<span data-ttu-id="11fe7-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="11fe7-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="11fe7-181">El gesto de inicio</span><span class="sxs-lookup"><span data-stu-id="11fe7-181">The home gesture</span></span>

<span data-ttu-id="11fe7-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="11fe7-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="11fe7-183">El movimiento válido máximo</span><span class="sxs-lookup"><span data-stu-id="11fe7-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="11fe7-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="11fe7-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="11fe7-185">Describe el estado de una reproducción</span><span class="sxs-lookup"><span data-stu-id="11fe7-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="11fe7-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="11fe7-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="11fe7-187">La grabación está actualmente detenido y listo para su reproducción</span><span class="sxs-lookup"><span data-stu-id="11fe7-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="11fe7-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="11fe7-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="11fe7-189">Ya se está reproduciendo la grabación</span><span class="sxs-lookup"><span data-stu-id="11fe7-189">The recording is currently playing</span></span>

<span data-ttu-id="11fe7-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="11fe7-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="11fe7-191">Actualmente está en pausa la grabación</span><span class="sxs-lookup"><span data-stu-id="11fe7-191">The recording is currently paused</span></span>

<span data-ttu-id="11fe7-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="11fe7-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="11fe7-193">La grabación ha llegado al final</span><span class="sxs-lookup"><span data-stu-id="11fe7-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="11fe7-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="11fe7-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="11fe7-195">Describe un vector de 3 componentes, que se puede describir un punto o un vector en el espacio 3D</span><span class="sxs-lookup"><span data-stu-id="11fe7-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="11fe7-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="11fe7-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="11fe7-197">El componente X del vector</span><span class="sxs-lookup"><span data-stu-id="11fe7-197">The X component of the vector</span></span>

<span data-ttu-id="11fe7-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="11fe7-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="11fe7-199">El componente Y del vector</span><span class="sxs-lookup"><span data-stu-id="11fe7-199">The Y component of the vector</span></span>

<span data-ttu-id="11fe7-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="11fe7-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="11fe7-201">Componente Z del vector</span><span class="sxs-lookup"><span data-stu-id="11fe7-201">The Z component of the vector</span></span>

<span data-ttu-id="11fe7-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="11fe7-203">Construir un nuevo Vector3</span><span class="sxs-lookup"><span data-stu-id="11fe7-203">Construct a new Vector3</span></span>

<span data-ttu-id="11fe7-204">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-204">Parameters</span></span>
* <span data-ttu-id="11fe7-205">x: el componente x del vector</span><span class="sxs-lookup"><span data-stu-id="11fe7-205">x - The x component of the vector</span></span>
* <span data-ttu-id="11fe7-206">y - el componente y del vector</span><span class="sxs-lookup"><span data-stu-id="11fe7-206">y - The y component of the vector</span></span>
* <span data-ttu-id="11fe7-207">z - el componente z del vector</span><span class="sxs-lookup"><span data-stu-id="11fe7-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="11fe7-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="11fe7-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="11fe7-209">Describe un giro de 3 componentes</span><span class="sxs-lookup"><span data-stu-id="11fe7-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="11fe7-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="11fe7-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="11fe7-211">El componente de punto de rotación, abajo alrededor del eje X</span><span class="sxs-lookup"><span data-stu-id="11fe7-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="11fe7-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="11fe7-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="11fe7-213">El componente de rotación de la rotación, justo en el eje Y</span><span class="sxs-lookup"><span data-stu-id="11fe7-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="11fe7-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="11fe7-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="11fe7-215">El componente de rollo de rotación, justo en el eje Z</span><span class="sxs-lookup"><span data-stu-id="11fe7-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="11fe7-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="11fe7-217">Construir un nuevo Rotation3</span><span class="sxs-lookup"><span data-stu-id="11fe7-217">Construct a new Rotation3</span></span>

<span data-ttu-id="11fe7-218">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-218">Parameters</span></span>
* <span data-ttu-id="11fe7-219">pitch: el componente de tono de la rotación</span><span class="sxs-lookup"><span data-stu-id="11fe7-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="11fe7-220">guiñada: el componente de rotación de la rotación</span><span class="sxs-lookup"><span data-stu-id="11fe7-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="11fe7-221">Resumen: el componente de lanzamiento de la rotación</span><span class="sxs-lookup"><span data-stu-id="11fe7-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="11fe7-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="11fe7-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="11fe7-223">Describe un frustum de visualización, como suele ser utilizado por una cámara</span><span class="sxs-lookup"><span data-stu-id="11fe7-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="11fe7-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="11fe7-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="11fe7-225">La distancia mínima que se encuentra en el frustum</span><span class="sxs-lookup"><span data-stu-id="11fe7-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="11fe7-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="11fe7-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="11fe7-227">La distancia máxima que se encuentra en el frustum</span><span class="sxs-lookup"><span data-stu-id="11fe7-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="11fe7-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="11fe7-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="11fe7-229">El campo de visión horizontal de frustum, en radianes (menos de PI)</span><span class="sxs-lookup"><span data-stu-id="11fe7-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="11fe7-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="11fe7-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="11fe7-231">La proporción del campo de visión horizontal a vertical campo de visión</span><span class="sxs-lookup"><span data-stu-id="11fe7-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="11fe7-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="11fe7-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="11fe7-233">Raíz para generar los paquetes utilizados para controlar un dispositivo</span><span class="sxs-lookup"><span data-stu-id="11fe7-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="11fe7-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="11fe7-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="11fe7-235">Recuperar el objeto de dispositivo simulado que interpreta los humanos simulado y el mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="11fe7-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="11fe7-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="11fe7-237">Recuperar el objeto que controla a los humanos simulado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="11fe7-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="11fe7-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="11fe7-239">La simulación se restablece a su estado predeterminado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="11fe7-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="11fe7-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="11fe7-241">Interfaz que describe el dispositivo que interpreta el mundo simulado y el usuario simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="11fe7-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="11fe7-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="11fe7-243">Recuperar el Rastreador de Head del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="11fe7-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="11fe7-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="11fe7-245">Recuperar el Rastreador de mano desde el dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="11fe7-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="11fe7-247">Establecer las propiedades del dispositivo simulado para que coincida con el tipo de dispositivo proporcionado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="11fe7-248">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-248">Parameters</span></span>
* <span data-ttu-id="11fe7-249">tipo: el nuevo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="11fe7-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="11fe7-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="11fe7-251">Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de la cabeza de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="11fe7-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="11fe7-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="11fe7-253">Recupera y establece el modo de seguimiento principal actual.</span><span class="sxs-lookup"><span data-stu-id="11fe7-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="11fe7-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="11fe7-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="11fe7-255">Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de las manos de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="11fe7-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="11fe7-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="11fe7-257">Recuperar la posición del nodo con respecto a la del mundo, en metros</span><span class="sxs-lookup"><span data-stu-id="11fe7-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="11fe7-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="11fe7-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="11fe7-259">Recuperar y establecer la posición de la herramienta de seguimiento de la mano simulado, en relación con el centro de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="11fe7-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="11fe7-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="11fe7-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="11fe7-261">Recuperar y establecer el tono hacia abajo de la herramienta de seguimiento de la mano simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="11fe7-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="11fe7-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="11fe7-263">Recuperar y establecer si se omite el frustum del Rastreador de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="11fe7-264">Cuando se omite, dos manos siempre están visibles.</span><span class="sxs-lookup"><span data-stu-id="11fe7-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="11fe7-265">Cuando no pasa por alto (predeterminado) manos solamente están visibles cuando estén dentro del frustum del Rastreador de mano.</span><span class="sxs-lookup"><span data-stu-id="11fe7-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="11fe7-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="11fe7-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="11fe7-267">Recuperar y establecer las propiedades de frustum utilizadas para determinar si son visibles para el seguimiento de la mano simulado manos.</span><span class="sxs-lookup"><span data-stu-id="11fe7-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="11fe7-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="11fe7-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="11fe7-269">Interfaz de nivel superior para controlar a los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-269">Top level interface for controlling the simulated human</span></span>

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

<span data-ttu-id="11fe7-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="11fe7-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="11fe7-271">Recuperar y establecer la posición del nodo con respecto a la del mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="11fe7-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="11fe7-272">La posición corresponde a un punto en el centro de metros del humanos.</span><span class="sxs-lookup"><span data-stu-id="11fe7-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="11fe7-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="11fe7-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="11fe7-274">Recuperar y establecer las caras humanas simuladas de la dirección en el mundo.</span><span class="sxs-lookup"><span data-stu-id="11fe7-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="11fe7-275">0 radianes se enfrenta al eje Z negativo.</span><span class="sxs-lookup"><span data-stu-id="11fe7-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="11fe7-276">Rotación radianes positivos sobre el eje Y.</span><span class="sxs-lookup"><span data-stu-id="11fe7-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="11fe7-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="11fe7-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="11fe7-278">Recuperar y establecer el alto de los humanos simulado, en metros</span><span class="sxs-lookup"><span data-stu-id="11fe7-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="11fe7-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="11fe7-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="11fe7-280">Recuperar la parte izquierda de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="11fe7-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="11fe7-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="11fe7-282">Recuperar la parte derecha de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="11fe7-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="11fe7-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="11fe7-284">Recuperar el encabezado de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="11fe7-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="11fe7-286">Mover a los humanos simulado respecto a su posición actual, en metros</span><span class="sxs-lookup"><span data-stu-id="11fe7-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="11fe7-287">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-287">Parameters</span></span>
* <span data-ttu-id="11fe7-288">traducción: la traducción que se mueven en relación con la posición actual</span><span class="sxs-lookup"><span data-stu-id="11fe7-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="11fe7-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="11fe7-290">Girar a los humanos simulado con respecto a su dirección actual, las agujas del reloj sobre el eje Y</span><span class="sxs-lookup"><span data-stu-id="11fe7-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="11fe7-291">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-291">Parameters</span></span>
* <span data-ttu-id="11fe7-292">radianes - la cantidad que se va a girar alrededor del eje Y</span><span class="sxs-lookup"><span data-stu-id="11fe7-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="11fe7-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="11fe7-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="11fe7-294">Interfaz que describe una mano de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-294">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="11fe7-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="11fe7-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="11fe7-296">Recuperar la posición del nodo con respecto a la del mundo, en metros</span><span class="sxs-lookup"><span data-stu-id="11fe7-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="11fe7-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="11fe7-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="11fe7-298">Recuperar y establecer la posición de la mano simulada con respecto a los humanos, en metros.</span><span class="sxs-lookup"><span data-stu-id="11fe7-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="11fe7-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="11fe7-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="11fe7-300">Recuperar y establecer si está activada actualmente la mano.</span><span class="sxs-lookup"><span data-stu-id="11fe7-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="11fe7-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="11fe7-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="11fe7-302">Recuperar datos si la mano está actualmente visible para el SimulatedDevice (es decir, si está en una posición para ser detectado por el HandTracker).</span><span class="sxs-lookup"><span data-stu-id="11fe7-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="11fe7-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="11fe7-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="11fe7-304">Mover la mano de manera que es visible para el SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="11fe7-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="11fe7-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="11fe7-306">Mover la posición de la mano simulada respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="11fe7-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="11fe7-307">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-307">Parameters</span></span>
* <span data-ttu-id="11fe7-308">traducción: la cantidad de traslación de la mano simulada</span><span class="sxs-lookup"><span data-stu-id="11fe7-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="11fe7-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="11fe7-310">Realizar un gesto de la mano simulada (solo se detectará el sistema si está habilitada la mano).</span><span class="sxs-lookup"><span data-stu-id="11fe7-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="11fe7-311">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-311">Parameters</span></span>
* <span data-ttu-id="11fe7-312">gesto - el gesto para realizar</span><span class="sxs-lookup"><span data-stu-id="11fe7-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="11fe7-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="11fe7-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="11fe7-314">Interfaz que describe el encabezado de los humanos simulado</span><span class="sxs-lookup"><span data-stu-id="11fe7-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="11fe7-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="11fe7-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="11fe7-316">Recuperar la posición del nodo con respecto a la del mundo, en metros</span><span class="sxs-lookup"><span data-stu-id="11fe7-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="11fe7-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="11fe7-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="11fe7-318">Recuperar la rotación de la cabeza simulada.</span><span class="sxs-lookup"><span data-stu-id="11fe7-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="11fe7-319">Radianes giran a la derecha al buscar en el eje positivo.</span><span class="sxs-lookup"><span data-stu-id="11fe7-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="11fe7-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="11fe7-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="11fe7-321">Recuperar el diámetro del encabezado simulado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="11fe7-322">Este valor se utiliza para determinar el centro del encabezado (punto de giro).</span><span class="sxs-lookup"><span data-stu-id="11fe7-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="11fe7-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="11fe7-324">Girar la cabeza simulada con respecto a su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="11fe7-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="11fe7-325">Radianes giran a la derecha al buscar en el eje positivo.</span><span class="sxs-lookup"><span data-stu-id="11fe7-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="11fe7-326">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-326">Parameters</span></span>
* <span data-ttu-id="11fe7-327">rotación: la cantidad que se va a girar</span><span class="sxs-lookup"><span data-stu-id="11fe7-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="11fe7-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="11fe7-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="11fe7-329">Cargar la interfaz para interactuar con una grabación única para la reproducción.</span><span class="sxs-lookup"><span data-stu-id="11fe7-329">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="11fe7-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="11fe7-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="11fe7-331">Recupera la lista de tipos de datos en la grabación.</span><span class="sxs-lookup"><span data-stu-id="11fe7-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="11fe7-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="11fe7-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="11fe7-333">Recupera el estado actual de la grabación.</span><span class="sxs-lookup"><span data-stu-id="11fe7-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="11fe7-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="11fe7-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="11fe7-335">Iniciar la reproducción.</span><span class="sxs-lookup"><span data-stu-id="11fe7-335">Start the playback.</span></span> <span data-ttu-id="11fe7-336">Si está en pausa la grabación, reproducción se reanudará desde la ubicación en pausa; Si se detiene, se iniciará la reproducción al principio.</span><span class="sxs-lookup"><span data-stu-id="11fe7-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="11fe7-337">Si ya está reproduciendo, se omite esta llamada.</span><span class="sxs-lookup"><span data-stu-id="11fe7-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="11fe7-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="11fe7-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="11fe7-339">Pone en pausa la reproducción en su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="11fe7-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="11fe7-340">Si se detiene la grabación, se omite la llamada.</span><span class="sxs-lookup"><span data-stu-id="11fe7-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="11fe7-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="11fe7-342">Busca la grabación a la hora especificada (en intervalos de 100 nanosegundos desde el principio) y se detiene en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="11fe7-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="11fe7-343">Si el tiempo es más allá del final de la grabación, está en pausa en el último fotograma.</span><span class="sxs-lookup"><span data-stu-id="11fe7-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="11fe7-344">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-344">Parameters</span></span>
* <span data-ttu-id="11fe7-345">tics: el tiempo que se va a buscar</span><span class="sxs-lookup"><span data-stu-id="11fe7-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="11fe7-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="11fe7-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="11fe7-347">Detiene la reproducción y restablece la posición al principio</span><span class="sxs-lookup"><span data-stu-id="11fe7-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="11fe7-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="11fe7-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="11fe7-349">Interfaz para recibir los cambios de estado durante la reproducción</span><span class="sxs-lookup"><span data-stu-id="11fe7-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="11fe7-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="11fe7-351">Se llama cuando ha cambiado el estado de reproducción de un ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="11fe7-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="11fe7-352">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-352">Parameters</span></span>
* <span data-ttu-id="11fe7-353">newState - el nuevo estado de la grabación</span><span class="sxs-lookup"><span data-stu-id="11fe7-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="11fe7-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="11fe7-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="11fe7-355">Objeto raíz para crear objetos de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="11fe7-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="11fe7-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="11fe7-357">Crear en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.</span><span class="sxs-lookup"><span data-stu-id="11fe7-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="11fe7-358">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-358">Parameters</span></span>
* <span data-ttu-id="11fe7-359">Sink - el receptor que recibirá todos genera paquetes</span><span class="sxs-lookup"><span data-stu-id="11fe7-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="11fe7-360">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="11fe7-360">Return value</span></span>

<span data-ttu-id="11fe7-361">El administrador creado</span><span class="sxs-lookup"><span data-stu-id="11fe7-361">The created Manager</span></span>

<span data-ttu-id="11fe7-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="11fe7-363">Crear un receptor que almacena los paquetes recibidos todo en un archivo en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="11fe7-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="11fe7-364">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-364">Parameters</span></span>
* <span data-ttu-id="11fe7-365">ruta de acceso: la ruta de acceso de archivo que se creará</span><span class="sxs-lookup"><span data-stu-id="11fe7-365">path - The path of the file to create</span></span>

<span data-ttu-id="11fe7-366">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="11fe7-366">Return value</span></span>

<span data-ttu-id="11fe7-367">El receptor creado</span><span class="sxs-lookup"><span data-stu-id="11fe7-367">The created sink</span></span>

<span data-ttu-id="11fe7-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="11fe7-369">Cargar una grabación desde el archivo especificado</span><span class="sxs-lookup"><span data-stu-id="11fe7-369">Load a recording from the specified file</span></span>

<span data-ttu-id="11fe7-370">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-370">Parameters</span></span>
* <span data-ttu-id="11fe7-371">ruta de acceso: la ruta de acceso del archivo para cargar</span><span class="sxs-lookup"><span data-stu-id="11fe7-371">path - The path of the file to load</span></span>
* <span data-ttu-id="11fe7-372">Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="11fe7-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="11fe7-373">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="11fe7-373">Return value</span></span>

<span data-ttu-id="11fe7-374">La grabación cargada</span><span class="sxs-lookup"><span data-stu-id="11fe7-374">The loaded recording</span></span>

<span data-ttu-id="11fe7-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="11fe7-376">Cargar una grabación desde el archivo especificado</span><span class="sxs-lookup"><span data-stu-id="11fe7-376">Load a recording from the specified file</span></span>

<span data-ttu-id="11fe7-377">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-377">Parameters</span></span>
* <span data-ttu-id="11fe7-378">ruta de acceso: la ruta de acceso del archivo para cargar</span><span class="sxs-lookup"><span data-stu-id="11fe7-378">path - The path of the file to load</span></span>
* <span data-ttu-id="11fe7-379">Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="11fe7-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="11fe7-380">Una devolución de llamada que recibe de devolución de llamada - actualiza reclasificación de estado de la grabación</span><span class="sxs-lookup"><span data-stu-id="11fe7-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="11fe7-381">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="11fe7-381">Return value</span></span>

<span data-ttu-id="11fe7-382">La grabación cargada</span><span class="sxs-lookup"><span data-stu-id="11fe7-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="11fe7-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="11fe7-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="11fe7-384">Describe los diferentes tipos de datos de secuencia</span><span class="sxs-lookup"><span data-stu-id="11fe7-384">Describes the different types of stream data</span></span>

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

<span data-ttu-id="11fe7-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="11fe7-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="11fe7-386">Un valor de centinela utilizado para no indicar ningún tipo de datos de secuencia</span><span class="sxs-lookup"><span data-stu-id="11fe7-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="11fe7-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="11fe7-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="11fe7-388">Stream de datos con respecto a la posición y la orientación de la cabeza</span><span class="sxs-lookup"><span data-stu-id="11fe7-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="11fe7-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="11fe7-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="11fe7-390">Stream de datos con respecto a la posición y movimientos de manos</span><span class="sxs-lookup"><span data-stu-id="11fe7-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="11fe7-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="11fe7-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="11fe7-392">Stream de datos con respecto a la asignación espacial del entorno</span><span class="sxs-lookup"><span data-stu-id="11fe7-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="11fe7-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="11fe7-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="11fe7-394">Stream de datos con respecto a la calibración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="11fe7-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="11fe7-395">Solo se aceptan los paquetes de calibración mediante un sistema en modo remoto.</span><span class="sxs-lookup"><span data-stu-id="11fe7-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="11fe7-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="11fe7-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="11fe7-397">Stream de datos relacionados con el entorno del dispositivo</span><span class="sxs-lookup"><span data-stu-id="11fe7-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="11fe7-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="11fe7-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="11fe7-399">Un valor de centinela utilizado para indicar todos los tipos de datos registrados</span><span class="sxs-lookup"><span data-stu-id="11fe7-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="11fe7-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="11fe7-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="11fe7-401">Un objeto que recibe los paquetes de datos de una secuencia de simulación</span><span class="sxs-lookup"><span data-stu-id="11fe7-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="11fe7-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="11fe7-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="11fe7-403">Recibe un paquete único, que es internamente con tipo y con control de versiones</span><span class="sxs-lookup"><span data-stu-id="11fe7-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="11fe7-404">Parámetros</span><span class="sxs-lookup"><span data-stu-id="11fe7-404">Parameters</span></span>
* <span data-ttu-id="11fe7-405">longitud: la longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="11fe7-405">length - The length of the packet</span></span>
* <span data-ttu-id="11fe7-406">paquete - los datos del paquete</span><span class="sxs-lookup"><span data-stu-id="11fe7-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="11fe7-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="11fe7-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="11fe7-408">Un objeto que crea ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="11fe7-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="11fe7-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="11fe7-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="11fe7-410">Crea una instancia única de ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="11fe7-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="11fe7-411">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="11fe7-411">Return value</span></span>

<span data-ttu-id="11fe7-412">El receptor creado</span><span class="sxs-lookup"><span data-stu-id="11fe7-412">The created sink</span></span>
