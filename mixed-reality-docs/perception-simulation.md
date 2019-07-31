---
title: Simulación de percepción
description: Guía para el uso de la biblioteca de simulación de percepción para automatizar la entrada simulada para aplicaciones envolventes
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, simulación, pruebas
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414532"
---
# <a name="perception-simulation"></a><span data-ttu-id="0c532-104">Simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="0c532-104">Perception simulation</span></span>

<span data-ttu-id="0c532-105">¿Desea crear una prueba automatizada para la aplicación?</span><span class="sxs-lookup"><span data-stu-id="0c532-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="0c532-106">¿Desea que las pruebas vayan más allá de las pruebas unitarias de nivel de componente y realmente ejecute su aplicación de un extremo a otro?</span><span class="sxs-lookup"><span data-stu-id="0c532-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="0c532-107">La simulación de percepción es lo que está buscando.</span><span class="sxs-lookup"><span data-stu-id="0c532-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="0c532-108">La biblioteca de simulación de percepción envía datos de entrada humanos y del mundo a la aplicación para que pueda automatizar las pruebas.</span><span class="sxs-lookup"><span data-stu-id="0c532-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="0c532-109">Por ejemplo, puede simular la entrada de un usuario que busca una posición concreta y repetible y, a continuación, realizar un gesto o usar un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="0c532-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="0c532-110">La simulación de percepción puede enviar una entrada simulada como esta a una HoloLens física, el emulador de HoloLens (1ª generación), el emulador de HoloLens 2 o un equipo con el portal de realidad mixta instalado.</span><span class="sxs-lookup"><span data-stu-id="0c532-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="0c532-111">La simulación de percepción omite los sensores en directo en un dispositivo de realidad mixta y envía una entrada simulada a las aplicaciones que se ejecutan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0c532-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="0c532-112">Las aplicaciones reciben estos eventos de entrada a través de las mismas API que siempre usan y no indican la diferencia entre la ejecución con sensores reales y la ejecución con simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="0c532-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="0c532-113">La simulación de percepción es la misma tecnología que usan los emuladores de HoloLens para enviar datos simulados a la máquina virtual HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0c532-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="0c532-114">Para empezar a usar la simulación en el código, empiece por crear un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="0c532-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="0c532-115">Desde ese objeto, puede emitir comandos para controlar las propiedades de una "persona" simulada, incluida la posición del encabezado, la posición de la mano y los gestos, y puede habilitar y manipular los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="0c532-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="0c532-116">Configuración de un proyecto de Visual Studio para la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="0c532-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="0c532-117">[Instale el emulador de HoloLens](install-the-tools.md) en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="0c532-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="0c532-118">El emulador incluye las bibliotecas que se usarán para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="0c532-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="0c532-119">Cree un nuevo proyecto de C# Visual Studio Desktop (un proyecto de consola funciona bien para empezar a trabajar).</span><span class="sxs-lookup"><span data-stu-id="0c532-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="0c532-120">Agregue los siguientes archivos binarios al proyecto como referencias (proyecto-> referencia del complemento de >...). Puede encontrarlos en% ProgramFiles (x86)% \ Microsoft XDE\\(versión), como **% ProgramFiles (x86)% \ Microsoft XDE\\10.0.18362.0** para el emulador de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0c532-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="0c532-121">(Nota: aunque los archivos binarios forman parte del emulador de HoloLens 2, también funcionan para Windows Mixed Reality en el escritorio). un.</span><span class="sxs-lookup"><span data-stu-id="0c532-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="0c532-122">PerceptionSimulationManager. Interop. dll: contenedor C# administrado para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="0c532-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="0c532-123">b.</span><span class="sxs-lookup"><span data-stu-id="0c532-123">b.</span></span> <span data-ttu-id="0c532-124">PerceptionSimulationRest. dll-Library para configurar un canal de comunicación de socket web a HoloLens o emulador.</span><span class="sxs-lookup"><span data-stu-id="0c532-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="0c532-125">c.</span><span class="sxs-lookup"><span data-stu-id="0c532-125">c.</span></span> <span data-ttu-id="0c532-126">SimulationStream. Interop. dll: tipos compartidos para la simulación.</span><span class="sxs-lookup"><span data-stu-id="0c532-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="0c532-127">Agregue el archivo binario de implementación PerceptionSimulationManager. dll al proyecto a.</span><span class="sxs-lookup"><span data-stu-id="0c532-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="0c532-128">Agréguelo primero como un archivo binario al proyecto (proyecto-> Agregar > elemento existente...). Guárdelo como un vínculo para que no lo copie en la carpeta de origen del proyecto.</span><span class="sxs-lookup"><span data-stu-id="0c532-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="0c532-129">![Agregue PerceptionSimulationManager. dll al proyecto como un vínculo](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="0c532-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="0c532-130">Después, asegúrese de que se copia en la carpeta de salida en la compilación.</span><span class="sxs-lookup"><span data-stu-id="0c532-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="0c532-131">Está en la hoja de propiedades del archivo binario.</span><span class="sxs-lookup"><span data-stu-id="0c532-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="0c532-132">![Marque PerceptionSimulationManager. dll para copiarlo en el directorio de salida](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="0c532-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="0c532-133">Establezca la plataforma de soluciones activa en x64.</span><span class="sxs-lookup"><span data-stu-id="0c532-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="0c532-134">(Utilice la Configuration Manager para crear una entrada de plataforma para x64 si aún no existe ninguna).</span><span class="sxs-lookup"><span data-stu-id="0c532-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="0c532-135">Creación de un objeto de administrador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="0c532-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="0c532-136">Para controlar la simulación, emitirá actualizaciones de los objetos recuperados de un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="0c532-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="0c532-137">El primer paso es obtener ese objeto y conectarlo al dispositivo o emulador de destino.</span><span class="sxs-lookup"><span data-stu-id="0c532-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="0c532-138">Para obtener la dirección IP del emulador, haga clic en el botón portal de dispositivos en la [barra de herramientas](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="0c532-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="0c532-139">![Abra el icono](images/emulator-deviceportal.png) del portal de dispositivos **abrir portal de dispositivos**: abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.</span><span class="sxs-lookup"><span data-stu-id="0c532-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="0c532-140">En el caso de Windows Mixed Reality, puede recuperarse en la aplicación de configuración en "actualizar & seguridad" y luego en "para desarrolladores" en la sección "conectar usando:" en "habilitar el portal de dispositivos".</span><span class="sxs-lookup"><span data-stu-id="0c532-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="0c532-141">Asegúrese de anotar la dirección IP y el puerto.</span><span class="sxs-lookup"><span data-stu-id="0c532-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="0c532-142">En primer lugar, llame a RestSimulationStreamSink. Create para obtener un objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="0c532-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="0c532-143">Este es el dispositivo de destino o el emulador que controlará la conexión http.</span><span class="sxs-lookup"><span data-stu-id="0c532-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="0c532-144">Los comandos se pasarán y controlarán en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="0c532-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="0c532-145">Los cuatro parámetros que necesitará para crear un objeto son:</span><span class="sxs-lookup"><span data-stu-id="0c532-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="0c532-146">URI del URI: dirección IP del dispositivo de destino (por ejemplo,"http://123.123.123.123" o "http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="0c532-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="0c532-147">Credenciales de System .net. NetworkCredential: nombre de usuario/contraseña para conectarse al [portal de dispositivos de Windows](using-the-windows-device-portal.md) en el emulador o dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="0c532-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="0c532-148">Si se va a conectar al emulador a través de su dirección local (por ejemplo,*168.* . \*) en el mismo equipo, se aceptarán las credenciales.</span><span class="sxs-lookup"><span data-stu-id="0c532-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="0c532-149">bool normal: true para la prioridad normal; false para la prioridad baja.</span><span class="sxs-lookup"><span data-stu-id="0c532-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="0c532-150">Por lo general, desea establecer este valor en *true* para los escenarios de prueba, lo que permite que la prueba tome el control.</span><span class="sxs-lookup"><span data-stu-id="0c532-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="0c532-151">El emulador y la simulación de Windows Mixed Reality usan conexiones de baja prioridad.</span><span class="sxs-lookup"><span data-stu-id="0c532-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="0c532-152">Si la prueba también usa una conexión de prioridad baja, la conexión establecida más recientemente tendrá el control.</span><span class="sxs-lookup"><span data-stu-id="0c532-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="0c532-153">System. Threading. CancellationToken token-token para cancelar la operación asincrónica.</span><span class="sxs-lookup"><span data-stu-id="0c532-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="0c532-154">En segundo lugar, creará el IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="0c532-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="0c532-155">Este es el objeto que se usa para controlar la simulación.</span><span class="sxs-lookup"><span data-stu-id="0c532-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="0c532-156">Tenga en cuenta que esto también debe realizarse en un método asincrónico.</span><span class="sxs-lookup"><span data-stu-id="0c532-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="0c532-157">Controlar el usuario simulado</span><span class="sxs-lookup"><span data-stu-id="0c532-157">Control the simulated Human</span></span>

<span data-ttu-id="0c532-158">Un IPerceptionSimulationManager tiene una propiedad humana que devuelve un objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="0c532-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="0c532-159">Para controlar el humano simulado, realice operaciones en este objeto.</span><span class="sxs-lookup"><span data-stu-id="0c532-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="0c532-160">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="0c532-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="0c532-161">Aplicación de C# consola de ejemplo básica</span><span class="sxs-lookup"><span data-stu-id="0c532-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="0c532-162">Aplicación de C# consola de ejemplo extendida</span><span class="sxs-lookup"><span data-stu-id="0c532-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="0c532-163">Nota en los controladores de 6 DOF</span><span class="sxs-lookup"><span data-stu-id="0c532-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="0c532-164">Antes de llamar a cualquier propiedad de los métodos en un controlador simulado de 6 DOF, debe activar el controlador.</span><span class="sxs-lookup"><span data-stu-id="0c532-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="0c532-165">Si no lo hace, se producirá una excepción.</span><span class="sxs-lookup"><span data-stu-id="0c532-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="0c532-166">A partir de la actualización 2019 de Windows 10, se pueden instalar y activar controladores simulados de 6 DOF si se establece la propiedad Status en el objeto ISimulatedSixDofController en SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="0c532-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="0c532-167">En la actualización de Windows 10 de octubre de 2018 y versiones anteriores, debe instalar por separado un controlador simulado de 6 DOF en primer lugar mediante una llamada a la herramienta PerceptionSimulationDevice que se encuentra en la carpeta \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="0c532-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="0c532-168">El uso de esta herramienta es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="0c532-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="0c532-169">Por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="0c532-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="0c532-170">Las acciones admitidas son:</span><span class="sxs-lookup"><span data-stu-id="0c532-170">Supported actions are:</span></span>
* <span data-ttu-id="0c532-171">i = instalación</span><span class="sxs-lookup"><span data-stu-id="0c532-171">i = install</span></span>
* <span data-ttu-id="0c532-172">q = consulta</span><span class="sxs-lookup"><span data-stu-id="0c532-172">q = query</span></span>
* <span data-ttu-id="0c532-173">r = quitar</span><span class="sxs-lookup"><span data-stu-id="0c532-173">r = remove</span></span>

<span data-ttu-id="0c532-174">Las instancias admitidas son:</span><span class="sxs-lookup"><span data-stu-id="0c532-174">Supported instances are:</span></span>
* <span data-ttu-id="0c532-175">1 = el controlador de 6 DOF izquierdo</span><span class="sxs-lookup"><span data-stu-id="0c532-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="0c532-176">2 = el controlador de 6 DOF adecuado</span><span class="sxs-lookup"><span data-stu-id="0c532-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="0c532-177">El código de salida del proceso indicará que la operación se ha realizado correctamente (un valor devuelto de cero) o un error (valor devuelto distinto de cero).</span><span class="sxs-lookup"><span data-stu-id="0c532-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="0c532-178">Al usar la acción ' q ' para consultar si está instalado un controlador, el valor devuelto será cero (0) si el controlador no está ya instalado o uno (1) si el controlador está instalado.</span><span class="sxs-lookup"><span data-stu-id="0c532-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="0c532-179">Al quitar un controlador en la actualización 2018 de octubre de Windows 10 o versiones anteriores, establezca su estado en desactivado a través de la API primero y, a continuación, llame a la herramienta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="0c532-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="0c532-180">Tenga en cuenta que esta herramienta debe ejecutarse como administrador.</span><span class="sxs-lookup"><span data-stu-id="0c532-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="0c532-181">Referencia de API</span><span class="sxs-lookup"><span data-stu-id="0c532-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="0c532-182">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="0c532-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="0c532-183">Describe un tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="0c532-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="0c532-184">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="0c532-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="0c532-185">Un dispositivo de referencia ficticio, el valor predeterminado para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="0c532-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="0c532-186">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="0c532-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="0c532-187">Describe un modo de seguimiento de encabezado</span><span class="sxs-lookup"><span data-stu-id="0c532-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="0c532-188">**Microsoft. PerceptionSimulation. HeadTrackerMode. default**</span><span class="sxs-lookup"><span data-stu-id="0c532-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="0c532-189">Seguimiento de encabezado predeterminado.</span><span class="sxs-lookup"><span data-stu-id="0c532-189">Default Head Tracking.</span></span> <span data-ttu-id="0c532-190">Esto significa que el sistema puede seleccionar el mejor modo de seguimiento de los encabezados según las condiciones del tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="0c532-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="0c532-191">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="0c532-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="0c532-192">Seguimiento de encabezado de solo orientación.</span><span class="sxs-lookup"><span data-stu-id="0c532-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="0c532-193">Esto significa que es posible que la posición de la que se realiza el seguimiento no sea confiable y que algunas funciones que dependen de la posición principal no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="0c532-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="0c532-194">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="0c532-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="0c532-195">Seguimiento de los cabezales posicionales.</span><span class="sxs-lookup"><span data-stu-id="0c532-195">Positional Head Tracking.</span></span> <span data-ttu-id="0c532-196">Esto significa que la posición y la orientación del encabezado controlados son confiables</span><span class="sxs-lookup"><span data-stu-id="0c532-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="0c532-197">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="0c532-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="0c532-198">Describe un gesto simulado</span><span class="sxs-lookup"><span data-stu-id="0c532-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="0c532-199">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="0c532-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="0c532-200">Un valor de centinela que se usa para indicar que no hay gestos.</span><span class="sxs-lookup"><span data-stu-id="0c532-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="0c532-201">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="0c532-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="0c532-202">Gesto de presionar un dedo.</span><span class="sxs-lookup"><span data-stu-id="0c532-202">A finger pressed gesture.</span></span>

<span data-ttu-id="0c532-203">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="0c532-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="0c532-204">Gesto de dedo liberado.</span><span class="sxs-lookup"><span data-stu-id="0c532-204">A finger released gesture.</span></span>

<span data-ttu-id="0c532-205">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="0c532-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="0c532-206">El gesto Home/System.</span><span class="sxs-lookup"><span data-stu-id="0c532-206">The home/system gesture.</span></span>

<span data-ttu-id="0c532-207">**Microsoft. PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="0c532-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="0c532-208">El gesto máximo válido.</span><span class="sxs-lookup"><span data-stu-id="0c532-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="0c532-209">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="0c532-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="0c532-210">Los posibles estados de un controlador simulado 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="0c532-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="0c532-211">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. OFF**</span><span class="sxs-lookup"><span data-stu-id="0c532-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="0c532-212">El controlador 6-DOF está desactivado.</span><span class="sxs-lookup"><span data-stu-id="0c532-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="0c532-213">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="0c532-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="0c532-214">El controlador 6-DOF está activado y controlado.</span><span class="sxs-lookup"><span data-stu-id="0c532-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="0c532-215">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="0c532-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="0c532-216">El controlador 6-DOF está activado, pero no se puede realizar su seguimiento.</span><span class="sxs-lookup"><span data-stu-id="0c532-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="0c532-217">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="0c532-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="0c532-218">Los botones admitidos en un controlador simulado 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="0c532-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="0c532-219">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="0c532-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="0c532-220">Un valor de centinela que se usa para indicar que no hay botones.</span><span class="sxs-lookup"><span data-stu-id="0c532-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="0c532-221">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="0c532-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="0c532-222">Se presiona el botón Inicio.</span><span class="sxs-lookup"><span data-stu-id="0c532-222">The Home button is pressed.</span></span>

<span data-ttu-id="0c532-223">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Menu**</span><span class="sxs-lookup"><span data-stu-id="0c532-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="0c532-224">Se presiona el botón de menú.</span><span class="sxs-lookup"><span data-stu-id="0c532-224">The Menu button is pressed.</span></span>

<span data-ttu-id="0c532-225">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. control**</span><span class="sxs-lookup"><span data-stu-id="0c532-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="0c532-226">Se presiona el botón de control.</span><span class="sxs-lookup"><span data-stu-id="0c532-226">The Grip button is pressed.</span></span>

<span data-ttu-id="0c532-227">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="0c532-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="0c532-228">El TouchPad está presionado.</span><span class="sxs-lookup"><span data-stu-id="0c532-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="0c532-229">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="0c532-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="0c532-230">Se presiona el botón seleccionar.</span><span class="sxs-lookup"><span data-stu-id="0c532-230">The Select button is pressed.</span></span>

<span data-ttu-id="0c532-231">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="0c532-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="0c532-232">El TouchPad se toca.</span><span class="sxs-lookup"><span data-stu-id="0c532-232">The TouchPad is touched.</span></span>

<span data-ttu-id="0c532-233">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Stick**</span><span class="sxs-lookup"><span data-stu-id="0c532-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="0c532-234">Se presiona el stick.</span><span class="sxs-lookup"><span data-stu-id="0c532-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="0c532-235">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="0c532-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="0c532-236">El botón válido máximo.</span><span class="sxs-lookup"><span data-stu-id="0c532-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="0c532-237">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="0c532-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="0c532-238">El estado de calibrado de los ojos simulados</span><span class="sxs-lookup"><span data-stu-id="0c532-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="0c532-239">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. no disponible**</span><span class="sxs-lookup"><span data-stu-id="0c532-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="0c532-240">La calibración de ojos no está disponible.</span><span class="sxs-lookup"><span data-stu-id="0c532-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="0c532-241">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="0c532-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="0c532-242">Los ojos se han calibrado.</span><span class="sxs-lookup"><span data-stu-id="0c532-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="0c532-243">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="0c532-243">This is the default value.</span></span>

<span data-ttu-id="0c532-244">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. configurando**</span><span class="sxs-lookup"><span data-stu-id="0c532-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="0c532-245">Los ojos se están calibrando.</span><span class="sxs-lookup"><span data-stu-id="0c532-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="0c532-246">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="0c532-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="0c532-247">Los ojos deben calibrarse.</span><span class="sxs-lookup"><span data-stu-id="0c532-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="0c532-248">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="0c532-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="0c532-249">La precisión del seguimiento de una Unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="0c532-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="0c532-250">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. no disponible**</span><span class="sxs-lookup"><span data-stu-id="0c532-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="0c532-251">No se realiza el seguimiento de la Unión.</span><span class="sxs-lookup"><span data-stu-id="0c532-251">The joint is not tracked.</span></span>

<span data-ttu-id="0c532-252">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**</span><span class="sxs-lookup"><span data-stu-id="0c532-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="0c532-253">Se deduce la posición de la Unión.</span><span class="sxs-lookup"><span data-stu-id="0c532-253">The joint position is inferred.</span></span>

<span data-ttu-id="0c532-254">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. visible**</span><span class="sxs-lookup"><span data-stu-id="0c532-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="0c532-255">Se realiza un seguimiento completo de la Unión.</span><span class="sxs-lookup"><span data-stu-id="0c532-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="0c532-256">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="0c532-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="0c532-257">La precisión del seguimiento de una Unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="0c532-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="0c532-258">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="0c532-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="0c532-259">Las uniones de dedos de la mano se configuran para reflejar una pose cerrada.</span><span class="sxs-lookup"><span data-stu-id="0c532-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="0c532-260">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="0c532-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="0c532-261">Las uniones de dedos de la mano se configuran para reflejar una pose abierta.</span><span class="sxs-lookup"><span data-stu-id="0c532-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="0c532-262">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="0c532-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="0c532-263">Las uniones de dedos de la mano se configuran para reflejar una postura señaladora.</span><span class="sxs-lookup"><span data-stu-id="0c532-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="0c532-264">**Microsoft. PerceptionSimulation. SimulatedHandPose. Pinch**</span><span class="sxs-lookup"><span data-stu-id="0c532-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="0c532-265">Las uniones de dedos de la mano se configuran para reflejar una pose de pinch.</span><span class="sxs-lookup"><span data-stu-id="0c532-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="0c532-266">**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="0c532-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="0c532-267">Valor máximo válido para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="0c532-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="0c532-268">Microsoft. PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="0c532-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="0c532-269">Describe el estado de una reproducción.</span><span class="sxs-lookup"><span data-stu-id="0c532-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="0c532-270">**Microsoft. PerceptionSimulation. PlaybackState. Stopped**</span><span class="sxs-lookup"><span data-stu-id="0c532-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="0c532-271">La grabación está actualmente detenida y lista para su reproducción.</span><span class="sxs-lookup"><span data-stu-id="0c532-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="0c532-272">**Microsoft. PerceptionSimulation. PlaybackState. Playing**</span><span class="sxs-lookup"><span data-stu-id="0c532-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="0c532-273">La grabación se está reproduciendo actualmente.</span><span class="sxs-lookup"><span data-stu-id="0c532-273">The recording is currently playing.</span></span>

<span data-ttu-id="0c532-274">**Microsoft. PerceptionSimulation. PlaybackState. pausado**</span><span class="sxs-lookup"><span data-stu-id="0c532-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="0c532-275">La grabación está en pausa actualmente.</span><span class="sxs-lookup"><span data-stu-id="0c532-275">The recording is currently paused.</span></span>

<span data-ttu-id="0c532-276">**Microsoft. PerceptionSimulation. PlaybackState. end**</span><span class="sxs-lookup"><span data-stu-id="0c532-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="0c532-277">La grabación ha alcanzado el final.</span><span class="sxs-lookup"><span data-stu-id="0c532-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="0c532-278">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="0c532-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="0c532-279">Describe un vector de 3 componentes, que puede describir un punto o un vector en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="0c532-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="0c532-280">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="0c532-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="0c532-281">Componente X del vector.</span><span class="sxs-lookup"><span data-stu-id="0c532-281">The X component of the vector.</span></span>

<span data-ttu-id="0c532-282">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="0c532-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="0c532-283">Componente Y del vector.</span><span class="sxs-lookup"><span data-stu-id="0c532-283">The Y component of the vector.</span></span>

<span data-ttu-id="0c532-284">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="0c532-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="0c532-285">Componente Z del vector.</span><span class="sxs-lookup"><span data-stu-id="0c532-285">The Z component of the vector.</span></span>

<span data-ttu-id="0c532-286">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="0c532-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="0c532-287">Construya un nuevo Vector3.</span><span class="sxs-lookup"><span data-stu-id="0c532-287">Construct a new Vector3.</span></span>

<span data-ttu-id="0c532-288">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-288">Parameters</span></span>
* <span data-ttu-id="0c532-289">x: el componente x del vector.</span><span class="sxs-lookup"><span data-stu-id="0c532-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="0c532-290">y: el componente y del vector.</span><span class="sxs-lookup"><span data-stu-id="0c532-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="0c532-291">z: el componente z del vector.</span><span class="sxs-lookup"><span data-stu-id="0c532-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="0c532-292">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="0c532-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="0c532-293">Describe un giro de 3 componentes.</span><span class="sxs-lookup"><span data-stu-id="0c532-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="0c532-294">**Microsoft. PerceptionSimulation. Rotation3. Brea**</span><span class="sxs-lookup"><span data-stu-id="0c532-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="0c532-295">El componente de tono de la rotación, en torno al eje X.</span><span class="sxs-lookup"><span data-stu-id="0c532-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="0c532-296">**Microsoft. PerceptionSimulation. Rotation3. guiñada**</span><span class="sxs-lookup"><span data-stu-id="0c532-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="0c532-297">Componente de guiñada de la rotación, justo alrededor del eje Y.</span><span class="sxs-lookup"><span data-stu-id="0c532-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="0c532-298">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="0c532-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="0c532-299">Componente de rollo de la rotación, justo alrededor del eje Z.</span><span class="sxs-lookup"><span data-stu-id="0c532-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="0c532-300">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="0c532-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="0c532-301">Construya un nuevo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="0c532-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="0c532-302">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-302">Parameters</span></span>
* <span data-ttu-id="0c532-303">paso: el componente de paso de la rotación.</span><span class="sxs-lookup"><span data-stu-id="0c532-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="0c532-304">guiñada: el componente de guiñada de la rotación.</span><span class="sxs-lookup"><span data-stu-id="0c532-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="0c532-305">rollo: componente de rollo de la rotación.</span><span class="sxs-lookup"><span data-stu-id="0c532-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="0c532-306">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="0c532-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="0c532-307">Describe la configuración de una Unión en una mano simulada.</span><span class="sxs-lookup"><span data-stu-id="0c532-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="0c532-308">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="0c532-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="0c532-309">La posición de la Unión.</span><span class="sxs-lookup"><span data-stu-id="0c532-309">The position of the joint.</span></span>

<span data-ttu-id="0c532-310">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="0c532-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="0c532-311">Rotación de la Unión.</span><span class="sxs-lookup"><span data-stu-id="0c532-311">The rotation of the joint.</span></span>

<span data-ttu-id="0c532-312">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="0c532-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="0c532-313">La precisión del seguimiento de la Unión.</span><span class="sxs-lookup"><span data-stu-id="0c532-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="0c532-314">Microsoft. PerceptionSimulation. frustum</span><span class="sxs-lookup"><span data-stu-id="0c532-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="0c532-315">Describe un frustum de vista, tal y como lo usa normalmente una cámara.</span><span class="sxs-lookup"><span data-stu-id="0c532-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="0c532-316">**Microsoft. PerceptionSimulation. frustum. Near**</span><span class="sxs-lookup"><span data-stu-id="0c532-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="0c532-317">Distancia mínima contenida en el frustum.</span><span class="sxs-lookup"><span data-stu-id="0c532-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="0c532-318">**Microsoft. PerceptionSimulation. frustum. Far**</span><span class="sxs-lookup"><span data-stu-id="0c532-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="0c532-319">La distancia máxima contenida en el frustum.</span><span class="sxs-lookup"><span data-stu-id="0c532-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="0c532-320">**Microsoft. PerceptionSimulation. frustum. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="0c532-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="0c532-321">Campo horizontal de la vista del frustum, en radianes (menor que PI).</span><span class="sxs-lookup"><span data-stu-id="0c532-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="0c532-322">**Microsoft. PerceptionSimulation. frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="0c532-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="0c532-323">La proporción del campo horizontal de la vista en el campo vertical de la vista.</span><span class="sxs-lookup"><span data-stu-id="0c532-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="0c532-324">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="0c532-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="0c532-325">Raíz para generar los paquetes usados para controlar un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0c532-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="0c532-326">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="0c532-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="0c532-327">Recupere el objeto de dispositivo simulado que interpreta el usuario simulado y el mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="0c532-328">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="0c532-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="0c532-329">Recupera el objeto que controla el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="0c532-330">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="0c532-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="0c532-331">Restablece el estado predeterminado de la simulación.</span><span class="sxs-lookup"><span data-stu-id="0c532-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="0c532-332">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="0c532-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="0c532-333">Interfaz que describe el dispositivo que interpreta el mundo simulado y el usuario simulado</span><span class="sxs-lookup"><span data-stu-id="0c532-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="0c532-334">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="0c532-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="0c532-335">Recupere el rastreador principal del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="0c532-336">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="0c532-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="0c532-337">Recupere el seguimiento de manos del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="0c532-338">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="0c532-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="0c532-339">Establezca las propiedades del dispositivo simulado para que coincida con el tipo de dispositivo proporcionado.</span><span class="sxs-lookup"><span data-stu-id="0c532-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="0c532-340">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-340">Parameters</span></span>
* <span data-ttu-id="0c532-341">tipo: el nuevo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="0c532-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="0c532-342">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="0c532-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="0c532-343">Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento del encabezado del usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="0c532-344">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="0c532-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="0c532-345">Recupera y establece el modo de seguimiento de encabezado actual.</span><span class="sxs-lookup"><span data-stu-id="0c532-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="0c532-346">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="0c532-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="0c532-347">Interfaz que describe la parte del dispositivo simulado que hace un seguimiento de las manos del usuario simulado</span><span class="sxs-lookup"><span data-stu-id="0c532-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="0c532-348">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0c532-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="0c532-349">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0c532-350">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="0c532-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="0c532-351">Recupera y establece la posición del seguimiento de mano simulado, en relación con el centro del encabezado.</span><span class="sxs-lookup"><span data-stu-id="0c532-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="0c532-352">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Brea**</span><span class="sxs-lookup"><span data-stu-id="0c532-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="0c532-353">Recupere y establezca el tono hacia abajo del seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="0c532-354">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="0c532-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="0c532-355">Recupera y establece si se omite el frustum del seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="0c532-356">Cuando se omite, ambas manecillas siempre están visibles.</span><span class="sxs-lookup"><span data-stu-id="0c532-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="0c532-357">Cuando no se omite (el valor predeterminado), las manecillas solo están visibles cuando se encuentran dentro del frustum del seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="0c532-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="0c532-358">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**</span><span class="sxs-lookup"><span data-stu-id="0c532-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="0c532-359">Recupere y establezca las propiedades de frustum utilizadas para determinar si las manecillas están visibles para el seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="0c532-360">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="0c532-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="0c532-361">Interfaz de nivel superior para controlar el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="0c532-362">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0c532-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="0c532-363">Recuperar y establecer la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="0c532-364">La posición corresponde a un punto en el centro de los pies del hombre.</span><span class="sxs-lookup"><span data-stu-id="0c532-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="0c532-365">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="0c532-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="0c532-366">Recupere y establezca la dirección de las caras humanas simuladas del mundo.</span><span class="sxs-lookup"><span data-stu-id="0c532-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="0c532-367">0 radianes se orientan hacia abajo en el eje Z negativo.</span><span class="sxs-lookup"><span data-stu-id="0c532-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="0c532-368">Los radianes positivos giran en el sentido de las agujas del reloj sobre el eje Y.</span><span class="sxs-lookup"><span data-stu-id="0c532-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="0c532-369">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="0c532-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="0c532-370">Recupere y establezca el alto del hombre simulado, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="0c532-371">**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="0c532-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="0c532-372">Recupere el lado izquierdo del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="0c532-373">**Microsoft. PerceptionSimulation. ISimulatedHuman. derecho**</span><span class="sxs-lookup"><span data-stu-id="0c532-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="0c532-374">Recupere la mano derecha del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="0c532-375">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="0c532-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="0c532-376">Recupera el encabezado del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="0c532-377">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0c532-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0c532-378">Mover el humano simulado con respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="0c532-379">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-379">Parameters</span></span>
* <span data-ttu-id="0c532-380">Translation: la traducción que se va a mover, relativa a la posición actual.</span><span class="sxs-lookup"><span data-stu-id="0c532-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="0c532-381">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="0c532-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="0c532-382">Girar el hombre simulado con respecto a su dirección actual, en el sentido de las agujas del reloj sobre el eje Y</span><span class="sxs-lookup"><span data-stu-id="0c532-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="0c532-383">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-383">Parameters</span></span>
* <span data-ttu-id="0c532-384">radianes: la cantidad que se va a girar alrededor del eje Y.</span><span class="sxs-lookup"><span data-stu-id="0c532-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="0c532-385">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="0c532-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="0c532-386">Las propiedades adicionales están disponibles al convertir ISimulatedHuman en ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="0c532-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="0c532-387">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="0c532-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="0c532-388">Recupere el controlador de 6-DOF izquierdo.</span><span class="sxs-lookup"><span data-stu-id="0c532-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="0c532-389">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="0c532-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="0c532-390">Recupere el controlador de 6-DOF adecuado.</span><span class="sxs-lookup"><span data-stu-id="0c532-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="0c532-391">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="0c532-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="0c532-392">Interfaz que describe una mano del usuario simulado</span><span class="sxs-lookup"><span data-stu-id="0c532-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="0c532-393">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0c532-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="0c532-394">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0c532-395">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="0c532-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="0c532-396">Recupera y establece la posición de la mano simulada en relación con el hombre, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="0c532-397">**Microsoft. PerceptionSimulation. ISimulatedHand. activado**</span><span class="sxs-lookup"><span data-stu-id="0c532-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="0c532-398">Recupera y establece si la mano está activada actualmente.</span><span class="sxs-lookup"><span data-stu-id="0c532-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="0c532-399">**Microsoft. PerceptionSimulation. ISimulatedHand. visible**</span><span class="sxs-lookup"><span data-stu-id="0c532-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="0c532-400">Recupera si la mano es visible actualmente para SimulatedDevice (es decir, si se encuentra en una posición que HandTracker).</span><span class="sxs-lookup"><span data-stu-id="0c532-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="0c532-401">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="0c532-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="0c532-402">Mueva la mano para que sea visible para el SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="0c532-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="0c532-403">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0c532-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0c532-404">Mover la posición de la mano simulada en relación con su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="0c532-405">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-405">Parameters</span></span>
* <span data-ttu-id="0c532-406">Translation: la cantidad que se va a trasladar a la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="0c532-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="0c532-407">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="0c532-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="0c532-408">Realizar un gesto mediante la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="0c532-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="0c532-409">Solo lo detectará el sistema si está habilitada la mano.</span><span class="sxs-lookup"><span data-stu-id="0c532-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="0c532-410">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-410">Parameters</span></span>
* <span data-ttu-id="0c532-411">gesto: el gesto que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="0c532-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="0c532-412">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="0c532-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="0c532-413">Las propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="0c532-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="0c532-414">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="0c532-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="0c532-415">Recupera o establece la rotación de la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="0c532-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="0c532-416">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="0c532-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="0c532-417">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="0c532-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="0c532-418">Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="0c532-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="0c532-419">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="0c532-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="0c532-420">Obtiene la configuración conjunta de la Unión especificada.</span><span class="sxs-lookup"><span data-stu-id="0c532-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="0c532-421">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="0c532-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="0c532-422">Establezca la configuración conjunta de la Unión especificada.</span><span class="sxs-lookup"><span data-stu-id="0c532-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="0c532-423">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="0c532-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="0c532-424">Establezca la mano en una pose conocida con una marca opcional que se va a animar.</span><span class="sxs-lookup"><span data-stu-id="0c532-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="0c532-425">Nota: la animación no provocará que las uniones reflejen inmediatamente sus configuraciones de conjuntos finales.</span><span class="sxs-lookup"><span data-stu-id="0c532-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="0c532-426">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="0c532-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="0c532-427">Interfaz que describe el encabezado del usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="0c532-428">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0c532-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="0c532-429">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0c532-430">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="0c532-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="0c532-431">Recupera el giro del encabezado simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="0c532-432">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="0c532-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0c532-433">**Microsoft. PerceptionSimulation. ISimulatedHead. diameter**</span><span class="sxs-lookup"><span data-stu-id="0c532-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="0c532-434">Recuperar el diámetro del cabezal simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="0c532-435">Este valor se usa para determinar el centro del encabezado (punto de giro).</span><span class="sxs-lookup"><span data-stu-id="0c532-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="0c532-436">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="0c532-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="0c532-437">Gira el encabezado simulado con respecto a su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="0c532-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="0c532-438">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="0c532-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0c532-439">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-439">Parameters</span></span>
* <span data-ttu-id="0c532-440">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="0c532-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="0c532-441">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="0c532-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="0c532-442">Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHead a ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="0c532-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="0c532-443">**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="0c532-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="0c532-444">Recupere los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="0c532-445">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="0c532-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="0c532-446">Interfaz que describe un controlador de 6 DOF asociado con el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="0c532-447">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0c532-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="0c532-448">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="0c532-449">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="0c532-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="0c532-450">Recupera o establece el estado actual del controlador.</span><span class="sxs-lookup"><span data-stu-id="0c532-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="0c532-451">El estado del controlador debe establecerse en un valor distinto de OFF antes de que las llamadas a Move, gire o presione botones se realicen correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c532-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="0c532-452">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="0c532-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="0c532-453">Recupera o establece la posición del controlador simulado con respecto al hombre, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="0c532-454">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="0c532-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="0c532-455">Recupera o establece la orientación del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="0c532-456">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="0c532-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="0c532-457">Mover la posición del controlador simulado con respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="0c532-458">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-458">Parameters</span></span>
* <span data-ttu-id="0c532-459">Translation: la cantidad para traducir el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="0c532-460">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="0c532-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="0c532-461">Presione un botón en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="0c532-462">Solo lo detectará el sistema si el controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="0c532-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="0c532-463">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-463">Parameters</span></span>
* <span data-ttu-id="0c532-464">Button: botón que se va a presionar.</span><span class="sxs-lookup"><span data-stu-id="0c532-464">button - The button to press.</span></span>

<span data-ttu-id="0c532-465">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="0c532-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="0c532-466">Suelte un botón en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="0c532-467">Solo lo detectará el sistema si el controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="0c532-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="0c532-468">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-468">Parameters</span></span>
* <span data-ttu-id="0c532-469">Button: el botón que se va a liberar.</span><span class="sxs-lookup"><span data-stu-id="0c532-469">button - The button to release.</span></span>

<span data-ttu-id="0c532-470">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out Float, out float)**</span><span class="sxs-lookup"><span data-stu-id="0c532-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="0c532-471">Obtiene la posición de un dedo simulado en el Touchpad del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="0c532-472">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-472">Parameters</span></span>
* <span data-ttu-id="0c532-473">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="0c532-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="0c532-474">y: posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="0c532-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="0c532-475">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="0c532-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="0c532-476">Establece la posición de un dedo simulado en el Touchpad del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="0c532-477">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-477">Parameters</span></span>
* <span data-ttu-id="0c532-478">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="0c532-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="0c532-479">y: posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="0c532-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="0c532-480">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="0c532-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="0c532-481">Los métodos y propiedades adicionales están disponibles mediante la conversión de un ISimulatedSixDofController a ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="0c532-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="0c532-482">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out Float, out float)**</span><span class="sxs-lookup"><span data-stu-id="0c532-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="0c532-483">Obtiene la posición del stick analógico simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="0c532-484">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-484">Parameters</span></span>
* <span data-ttu-id="0c532-485">x: la posición horizontal del Stick.</span><span class="sxs-lookup"><span data-stu-id="0c532-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="0c532-486">y: la posición vertical del Stick.</span><span class="sxs-lookup"><span data-stu-id="0c532-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="0c532-487">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="0c532-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="0c532-488">Establece la posición del stick analógico simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="0c532-489">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-489">Parameters</span></span>
* <span data-ttu-id="0c532-490">x: la posición horizontal del Stick.</span><span class="sxs-lookup"><span data-stu-id="0c532-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="0c532-491">y: la posición vertical del Stick.</span><span class="sxs-lookup"><span data-stu-id="0c532-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="0c532-492">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="0c532-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="0c532-493">Recupera o establece el nivel de batería del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="0c532-494">El valor debe ser mayor que 0,0 y menor o igual que 100,0.</span><span class="sxs-lookup"><span data-stu-id="0c532-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="0c532-495">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="0c532-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="0c532-496">Interfaz que describe los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="0c532-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="0c532-497">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="0c532-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="0c532-498">Recupera el giro de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="0c532-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="0c532-499">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="0c532-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0c532-500">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="0c532-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="0c532-501">Gira los ojos simulados en relación con su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="0c532-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="0c532-502">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="0c532-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="0c532-503">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-503">Parameters</span></span>
* <span data-ttu-id="0c532-504">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="0c532-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="0c532-505">**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="0c532-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="0c532-506">Recupera o establece el estado de calibrado de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="0c532-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="0c532-507">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="0c532-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="0c532-508">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="0c532-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="0c532-509">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="0c532-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="0c532-510">Interfaz para interactuar con un solo registro cargado para la reproducción.</span><span class="sxs-lookup"><span data-stu-id="0c532-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="0c532-511">**Microsoft. PerceptionSimulation. ISimulationRecording. Datatypes**</span><span class="sxs-lookup"><span data-stu-id="0c532-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="0c532-512">Recupera la lista de tipos de datos de la grabación.</span><span class="sxs-lookup"><span data-stu-id="0c532-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="0c532-513">**Microsoft. PerceptionSimulation. ISimulationRecording. State**</span><span class="sxs-lookup"><span data-stu-id="0c532-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="0c532-514">Recupera el estado actual de la grabación.</span><span class="sxs-lookup"><span data-stu-id="0c532-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="0c532-515">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="0c532-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="0c532-516">Inicie la reproducción.</span><span class="sxs-lookup"><span data-stu-id="0c532-516">Start the playback.</span></span> <span data-ttu-id="0c532-517">Si se pausa la grabación, la reproducción se reanudará desde la ubicación en pausa; Si se detiene, la reproducción se iniciará al principio.</span><span class="sxs-lookup"><span data-stu-id="0c532-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="0c532-518">Si ya se está reproduciendo, se omitirá esta llamada.</span><span class="sxs-lookup"><span data-stu-id="0c532-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="0c532-519">**Microsoft. PerceptionSimulation. ISimulationRecording. PAUSE**</span><span class="sxs-lookup"><span data-stu-id="0c532-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="0c532-520">Pausa la reproducción en su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="0c532-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="0c532-521">Si se detiene la grabación, se omite la llamada.</span><span class="sxs-lookup"><span data-stu-id="0c532-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="0c532-522">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="0c532-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="0c532-523">Busca la grabación en el tiempo especificado (en intervalos de 100 nanosegundos desde el principio) y se pausa en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="0c532-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="0c532-524">Si el tiempo está más allá del final de la grabación, se pausa en el último fotograma.</span><span class="sxs-lookup"><span data-stu-id="0c532-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="0c532-525">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-525">Parameters</span></span>
* <span data-ttu-id="0c532-526">TICs: la hora a la que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="0c532-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="0c532-527">**Microsoft. PerceptionSimulation. ISimulationRecording. STOP**</span><span class="sxs-lookup"><span data-stu-id="0c532-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="0c532-528">Detiene la reproducción y restablece la posición al principio.</span><span class="sxs-lookup"><span data-stu-id="0c532-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="0c532-529">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="0c532-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="0c532-530">Interfaz para recibir cambios de estado durante la reproducción.</span><span class="sxs-lookup"><span data-stu-id="0c532-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="0c532-531">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="0c532-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="0c532-532">Se llama cuando el estado de reproducción de un ISimulationRecording ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="0c532-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="0c532-533">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-533">Parameters</span></span>
* <span data-ttu-id="0c532-534">newState: el nuevo estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="0c532-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="0c532-535">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="0c532-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="0c532-536">Objeto raíz para crear objetos de simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="0c532-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="0c532-537">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="0c532-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="0c532-538">Cree en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.</span><span class="sxs-lookup"><span data-stu-id="0c532-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="0c532-539">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-539">Parameters</span></span>
* <span data-ttu-id="0c532-540">receptor: el receptor que recibirá todos los paquetes generados.</span><span class="sxs-lookup"><span data-stu-id="0c532-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="0c532-541">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0c532-541">Return value</span></span>

<span data-ttu-id="0c532-542">Administrador creado.</span><span class="sxs-lookup"><span data-stu-id="0c532-542">The created Manager.</span></span>

<span data-ttu-id="0c532-543">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="0c532-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="0c532-544">Cree un receptor que almacene todos los paquetes recibidos en un archivo en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="0c532-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="0c532-545">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-545">Parameters</span></span>
* <span data-ttu-id="0c532-546">Ruta de acceso: la ruta de acceso del archivo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="0c532-546">path - The path of the file to create.</span></span>

<span data-ttu-id="0c532-547">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0c532-547">Return value</span></span>

<span data-ttu-id="0c532-548">Receptor creado.</span><span class="sxs-lookup"><span data-stu-id="0c532-548">The created sink.</span></span>

<span data-ttu-id="0c532-549">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="0c532-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="0c532-550">Cargar una grabación del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="0c532-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="0c532-551">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-551">Parameters</span></span>
* <span data-ttu-id="0c532-552">Ruta de acceso: la ruta de acceso del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="0c532-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="0c532-553">Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="0c532-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="0c532-554">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0c532-554">Return value</span></span>

<span data-ttu-id="0c532-555">Grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="0c532-555">The loaded recording.</span></span>

<span data-ttu-id="0c532-556">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="0c532-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="0c532-557">Cargar una grabación del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="0c532-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="0c532-558">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-558">Parameters</span></span>
* <span data-ttu-id="0c532-559">Ruta de acceso: la ruta de acceso del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="0c532-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="0c532-560">Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="0c532-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="0c532-561">callback: devolución de llamada que recibe actualizaciones que retrasan el estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="0c532-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="0c532-562">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0c532-562">Return value</span></span>

<span data-ttu-id="0c532-563">Grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="0c532-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="0c532-564">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="0c532-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="0c532-565">Describe los diferentes tipos de datos de secuencia.</span><span class="sxs-lookup"><span data-stu-id="0c532-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="0c532-566">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="0c532-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="0c532-567">Un valor de centinela que se usa para indicar que no hay tipos de datos de flujo.</span><span class="sxs-lookup"><span data-stu-id="0c532-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="0c532-568">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="0c532-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="0c532-569">Secuencia de datos con respecto a la posición y orientación del encabezado.</span><span class="sxs-lookup"><span data-stu-id="0c532-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="0c532-570">**Microsoft. PerceptionSimulation. StreamDataTypes. handles**</span><span class="sxs-lookup"><span data-stu-id="0c532-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="0c532-571">Flujo de datos con respecto a la posición y los gestos de las manos.</span><span class="sxs-lookup"><span data-stu-id="0c532-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="0c532-572">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="0c532-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="0c532-573">Flujo de datos con respecto a la asignación espacial del entorno.</span><span class="sxs-lookup"><span data-stu-id="0c532-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="0c532-574">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="0c532-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="0c532-575">Flujo de datos con respecto a la calibración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0c532-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="0c532-576">Los paquetes de calibración solo los acepta un sistema en modo remoto.</span><span class="sxs-lookup"><span data-stu-id="0c532-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="0c532-577">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="0c532-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="0c532-578">Flujo de datos sobre el entorno del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0c532-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="0c532-579">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="0c532-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="0c532-580">Un valor de centinela que se usa para indicar todos los tipos de datos grabados.</span><span class="sxs-lookup"><span data-stu-id="0c532-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="0c532-581">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="0c532-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="0c532-582">Objeto que recibe paquetes de datos de una secuencia de simulación.</span><span class="sxs-lookup"><span data-stu-id="0c532-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="0c532-583">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint longitud, Byte [], paquete)**</span><span class="sxs-lookup"><span data-stu-id="0c532-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="0c532-584">Recibe un único paquete, que está escrito internamente y con control de versiones.</span><span class="sxs-lookup"><span data-stu-id="0c532-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="0c532-585">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0c532-585">Parameters</span></span>
* <span data-ttu-id="0c532-586">longitud: la longitud del paquete.</span><span class="sxs-lookup"><span data-stu-id="0c532-586">length - The length of the packet.</span></span>
* <span data-ttu-id="0c532-587">paquete: los datos del paquete.</span><span class="sxs-lookup"><span data-stu-id="0c532-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="0c532-588">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="0c532-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="0c532-589">Objeto que crea ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="0c532-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="0c532-590">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="0c532-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="0c532-591">Crea una única instancia de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="0c532-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="0c532-592">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0c532-592">Return value</span></span>

<span data-ttu-id="0c532-593">Receptor creado.</span><span class="sxs-lookup"><span data-stu-id="0c532-593">The created sink.</span></span>
