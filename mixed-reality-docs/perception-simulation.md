---
title: Simulación de percepción
description: Guía para el uso de la biblioteca de simulación de percepción para automatizar la entrada simulada para aplicaciones envolventes
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, simulación, pruebas
ms.openlocfilehash: 701fd39490d87b70df9bd68cc99da6482d41b676
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228030"
---
# <a name="perception-simulation"></a><span data-ttu-id="af3d9-104">Simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="af3d9-104">Perception simulation</span></span>

<span data-ttu-id="af3d9-105">¿Desea crear una prueba automatizada para la aplicación?</span><span class="sxs-lookup"><span data-stu-id="af3d9-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="af3d9-106">¿Desea que las pruebas vayan más allá de las pruebas unitarias de nivel de componente y realmente ejecute su aplicación de un extremo a otro?</span><span class="sxs-lookup"><span data-stu-id="af3d9-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="af3d9-107">La simulación de percepción es lo que está buscando.</span><span class="sxs-lookup"><span data-stu-id="af3d9-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="af3d9-108">La biblioteca de simulación de percepción envía datos de entrada humanos y del mundo a la aplicación para que pueda automatizar las pruebas.</span><span class="sxs-lookup"><span data-stu-id="af3d9-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="af3d9-109">Por ejemplo, puede simular la entrada de un usuario que busca una posición concreta y repetible y, a continuación, realizar un gesto o usar un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="af3d9-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="af3d9-110">La simulación de percepción puede enviar una entrada simulada como esta a una HoloLens física, el emulador de HoloLens (1ª generación), el emulador de HoloLens 2 o un equipo con el portal de realidad mixta instalado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="af3d9-111">La simulación de percepción omite los sensores en directo en un dispositivo de realidad mixta y envía una entrada simulada a las aplicaciones que se ejecutan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="af3d9-112">Las aplicaciones reciben estos eventos de entrada a través de las mismas API que siempre usan y no indican la diferencia entre la ejecución con sensores reales y la ejecución con simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="af3d9-113">La simulación de percepción es la misma tecnología que usan los emuladores de HoloLens para enviar datos simulados a la máquina virtual HoloLens.</span><span class="sxs-lookup"><span data-stu-id="af3d9-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="af3d9-114">Para empezar a usar la simulación en el código, empiece por crear un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="af3d9-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="af3d9-115">Desde ese objeto, puede emitir comandos para controlar las propiedades de una "persona" simulada, incluida la posición del encabezado, la posición de la mano y los gestos, y puede habilitar y manipular los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="af3d9-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="af3d9-116">Configuración de un proyecto de Visual Studio para la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="af3d9-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="af3d9-117">[Instale el emulador de HoloLens](install-the-tools.md) en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="af3d9-118">El emulador incluye las bibliotecas que se usarán para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="af3d9-119">Cree un nuevo proyecto de escritorio de Visual Studio C# (un proyecto de consola funciona bien para empezar a trabajar).</span><span class="sxs-lookup"><span data-stu-id="af3d9-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="af3d9-120">Agregue los siguientes archivos binarios al proyecto como referencias (proyecto->referencia del complemento de >...). Puede encontrarlos en% ProgramFiles (x86)% \ Microsoft XDE \\ (versión), como **% ProgramFiles (x86)% \ Microsoft XDE \\ 10.0.18362.0** para el emulador de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="af3d9-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="af3d9-121">(Nota: aunque los archivos binarios forman parte del emulador de HoloLens 2, también funcionan para Windows Mixed Reality en el escritorio). un.</span><span class="sxs-lookup"><span data-stu-id="af3d9-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="af3d9-122">PerceptionSimulationManager. Interop. dll: contenedor de C# administrado para la simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="af3d9-123">b.</span><span class="sxs-lookup"><span data-stu-id="af3d9-123">b.</span></span> <span data-ttu-id="af3d9-124">PerceptionSimulationRest. dll-Library para configurar un canal de comunicación de socket web a HoloLens o emulador.</span><span class="sxs-lookup"><span data-stu-id="af3d9-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="af3d9-125">c.</span><span class="sxs-lookup"><span data-stu-id="af3d9-125">c.</span></span> <span data-ttu-id="af3d9-126">SimulationStream. Interop. dll: tipos compartidos para la simulación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="af3d9-127">Agregue el archivo binario de implementación PerceptionSimulationManager. dll al proyecto a.</span><span class="sxs-lookup"><span data-stu-id="af3d9-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="af3d9-128">Agréguelo primero como un archivo binario al proyecto (proyecto->agregar >elemento existente...). Guárdelo como un vínculo para que no lo copie en la carpeta de origen del proyecto.</span><span class="sxs-lookup"><span data-stu-id="af3d9-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="af3d9-129">![Agregue PerceptionSimulationManager. dll al proyecto como un vínculo ](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="af3d9-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="af3d9-130">Después, asegúrese de que se copia en la carpeta de salida en la compilación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="af3d9-131">Está en la hoja de propiedades del archivo binario.</span><span class="sxs-lookup"><span data-stu-id="af3d9-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="af3d9-132">![Marque PerceptionSimulationManager. dll para copiarlo en el directorio de salida](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="af3d9-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="af3d9-133">Establezca la plataforma de soluciones activa en x64.</span><span class="sxs-lookup"><span data-stu-id="af3d9-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="af3d9-134">(Utilice la Configuration Manager para crear una entrada de plataforma para x64 si aún no existe ninguna).</span><span class="sxs-lookup"><span data-stu-id="af3d9-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="af3d9-135">Creación de un objeto de administrador de IPerceptionSimulation</span><span class="sxs-lookup"><span data-stu-id="af3d9-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="af3d9-136">Para controlar la simulación, emitirá actualizaciones de los objetos recuperados de un objeto IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="af3d9-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="af3d9-137">El primer paso es obtener ese objeto y conectarlo al dispositivo o emulador de destino.</span><span class="sxs-lookup"><span data-stu-id="af3d9-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="af3d9-138">Para obtener la dirección IP del emulador, haga clic en el botón portal de dispositivos en la [barra de herramientas](using-the-hololens-emulator.md) .</span><span class="sxs-lookup"><span data-stu-id="af3d9-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="af3d9-139">![Abra el icono del portal de dispositivos ](images/emulator-deviceportal.png) **abrir portal**de dispositivos: Abra el portal de dispositivos de Windows para el sistema operativo HoloLens en el emulador.</span><span class="sxs-lookup"><span data-stu-id="af3d9-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="af3d9-140">En el caso de Windows Mixed Reality, puede recuperarse en la aplicación de configuración en "actualizar & seguridad" y luego en "para desarrolladores" en la sección "conectar usando:" en "habilitar el portal de dispositivos".</span><span class="sxs-lookup"><span data-stu-id="af3d9-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="af3d9-141">Asegúrese de anotar la dirección IP y el puerto.</span><span class="sxs-lookup"><span data-stu-id="af3d9-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="af3d9-142">En primer lugar, llame a RestSimulationStreamSink. Create para obtener un objeto RestSimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="af3d9-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="af3d9-143">Este es el dispositivo de destino o el emulador que controlará la conexión http.</span><span class="sxs-lookup"><span data-stu-id="af3d9-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="af3d9-144">Los comandos se pasarán y controlarán en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="af3d9-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="af3d9-145">Los cuatro parámetros que necesitará para crear un objeto son:</span><span class="sxs-lookup"><span data-stu-id="af3d9-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="af3d9-146">URI del URI: dirección IP del dispositivo de destino (por ejemplo, " https://123.123.123.123 " o " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="af3d9-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="af3d9-147">Credenciales de System .net. NetworkCredential: nombre de usuario/contraseña para conectarse al [portal de dispositivos de Windows](using-the-windows-device-portal.md) en el emulador o dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="af3d9-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="af3d9-148">Si se va a conectar al emulador a través de su dirección local (por ejemplo,*168...* \*) en el mismo equipo, se aceptarán las credenciales.</span><span class="sxs-lookup"><span data-stu-id="af3d9-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="af3d9-149">bool normal: true para la prioridad normal; false para la prioridad baja.</span><span class="sxs-lookup"><span data-stu-id="af3d9-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="af3d9-150">Por lo general, desea establecer este valor en *true* para los escenarios de prueba, lo que permite que la prueba tome el control.</span><span class="sxs-lookup"><span data-stu-id="af3d9-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="af3d9-151">El emulador y la simulación de Windows Mixed Reality usan conexiones de baja prioridad.</span><span class="sxs-lookup"><span data-stu-id="af3d9-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="af3d9-152">Si la prueba también usa una conexión de prioridad baja, la conexión establecida más recientemente tendrá el control.</span><span class="sxs-lookup"><span data-stu-id="af3d9-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="af3d9-153">System. Threading. CancellationToken token-token para cancelar la operación asincrónica.</span><span class="sxs-lookup"><span data-stu-id="af3d9-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="af3d9-154">En segundo lugar, creará el IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="af3d9-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="af3d9-155">Este es el objeto que se usa para controlar la simulación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="af3d9-156">Tenga en cuenta que esto también debe realizarse en un método asincrónico.</span><span class="sxs-lookup"><span data-stu-id="af3d9-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="af3d9-157">Controlar el usuario simulado</span><span class="sxs-lookup"><span data-stu-id="af3d9-157">Control the simulated Human</span></span>

<span data-ttu-id="af3d9-158">Un IPerceptionSimulationManager tiene una propiedad humana que devuelve un objeto ISimulatedHuman.</span><span class="sxs-lookup"><span data-stu-id="af3d9-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="af3d9-159">Para controlar el humano simulado, realice operaciones en este objeto.</span><span class="sxs-lookup"><span data-stu-id="af3d9-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="af3d9-160">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="af3d9-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="af3d9-161">Aplicación de consola C# de ejemplo básica</span><span class="sxs-lookup"><span data-stu-id="af3d9-161">Basic Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="af3d9-162">Aplicación de consola de C# de ejemplo extendida</span><span class="sxs-lookup"><span data-stu-id="af3d9-162">Extended Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="af3d9-163">Nota en los controladores de 6 DOF</span><span class="sxs-lookup"><span data-stu-id="af3d9-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="af3d9-164">Antes de llamar a cualquier propiedad de los métodos en un controlador simulado de 6 DOF, debe activar el controlador.</span><span class="sxs-lookup"><span data-stu-id="af3d9-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="af3d9-165">Si no lo hace, se producirá una excepción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="af3d9-166">A partir de la actualización 2019 de Windows 10, se pueden instalar y activar controladores simulados de 6 DOF si se establece la propiedad Status en el objeto ISimulatedSixDofController en SimulatedSixDofControllerStatus. Active.</span><span class="sxs-lookup"><span data-stu-id="af3d9-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="af3d9-167">En la actualización de Windows 10 de octubre de 2018 y versiones anteriores, debe instalar por separado un controlador simulado de 6 DOF en primer lugar mediante una llamada a la herramienta PerceptionSimulationDevice que se encuentra en la carpeta \Windows\System32..</span><span class="sxs-lookup"><span data-stu-id="af3d9-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="af3d9-168">El uso de esta herramienta es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="af3d9-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="af3d9-169">Por ejemplo</span><span class="sxs-lookup"><span data-stu-id="af3d9-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="af3d9-170">Las acciones admitidas son:</span><span class="sxs-lookup"><span data-stu-id="af3d9-170">Supported actions are:</span></span>
* <span data-ttu-id="af3d9-171">i = instalación</span><span class="sxs-lookup"><span data-stu-id="af3d9-171">i = install</span></span>
* <span data-ttu-id="af3d9-172">q = consulta</span><span class="sxs-lookup"><span data-stu-id="af3d9-172">q = query</span></span>
* <span data-ttu-id="af3d9-173">r = quitar</span><span class="sxs-lookup"><span data-stu-id="af3d9-173">r = remove</span></span>

<span data-ttu-id="af3d9-174">Las instancias admitidas son:</span><span class="sxs-lookup"><span data-stu-id="af3d9-174">Supported instances are:</span></span>
* <span data-ttu-id="af3d9-175">1 = el controlador de 6 DOF izquierdo</span><span class="sxs-lookup"><span data-stu-id="af3d9-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="af3d9-176">2 = el controlador de 6 DOF adecuado</span><span class="sxs-lookup"><span data-stu-id="af3d9-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="af3d9-177">El código de salida del proceso indicará que la operación se ha realizado correctamente (un valor devuelto de cero) o un error (valor devuelto distinto de cero).</span><span class="sxs-lookup"><span data-stu-id="af3d9-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="af3d9-178">Al usar la acción ' q ' para consultar si está instalado un controlador, el valor devuelto será cero (0) si el controlador no está ya instalado o uno (1) si el controlador está instalado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="af3d9-179">Al quitar un controlador en la actualización 2018 de octubre de Windows 10 o versiones anteriores, establezca su estado en desactivado a través de la API primero y, a continuación, llame a la herramienta PerceptionSimulationDevice.</span><span class="sxs-lookup"><span data-stu-id="af3d9-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="af3d9-180">Tenga en cuenta que esta herramienta debe ejecutarse como administrador.</span><span class="sxs-lookup"><span data-stu-id="af3d9-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="af3d9-181">Referencia de API</span><span class="sxs-lookup"><span data-stu-id="af3d9-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="af3d9-182">Microsoft. PerceptionSimulation. SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="af3d9-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="af3d9-183">Describe un tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="af3d9-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="af3d9-184">**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**</span><span class="sxs-lookup"><span data-stu-id="af3d9-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="af3d9-185">Un dispositivo de referencia ficticio, el valor predeterminado para PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="af3d9-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="af3d9-186">Microsoft. PerceptionSimulation. HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="af3d9-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="af3d9-187">Describe un modo de seguimiento de encabezado</span><span class="sxs-lookup"><span data-stu-id="af3d9-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="af3d9-188">**Microsoft. PerceptionSimulation. HeadTrackerMode. default**</span><span class="sxs-lookup"><span data-stu-id="af3d9-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="af3d9-189">Seguimiento de encabezado predeterminado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-189">Default Head Tracking.</span></span> <span data-ttu-id="af3d9-190">Esto significa que el sistema puede seleccionar el mejor modo de seguimiento de los encabezados según las condiciones del tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="af3d9-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="af3d9-191">**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="af3d9-192">Seguimiento de encabezado de solo orientación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="af3d9-193">Esto significa que es posible que la posición de la que se realiza el seguimiento no sea confiable y que algunas funciones que dependen de la posición principal no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="af3d9-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="af3d9-194">**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**</span><span class="sxs-lookup"><span data-stu-id="af3d9-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="af3d9-195">Seguimiento de los cabezales posicionales.</span><span class="sxs-lookup"><span data-stu-id="af3d9-195">Positional Head Tracking.</span></span> <span data-ttu-id="af3d9-196">Esto significa que la posición y la orientación del encabezado controlados son confiables</span><span class="sxs-lookup"><span data-stu-id="af3d9-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="af3d9-197">Microsoft. PerceptionSimulation. SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="af3d9-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="af3d9-198">Describe un gesto simulado</span><span class="sxs-lookup"><span data-stu-id="af3d9-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="af3d9-199">**Microsoft. PerceptionSimulation. SimulatedGesture. None**</span><span class="sxs-lookup"><span data-stu-id="af3d9-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="af3d9-200">Un valor de centinela que se usa para indicar que no hay gestos.</span><span class="sxs-lookup"><span data-stu-id="af3d9-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="af3d9-201">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="af3d9-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="af3d9-202">Gesto de presionar un dedo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-202">A finger pressed gesture.</span></span>

<span data-ttu-id="af3d9-203">**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="af3d9-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="af3d9-204">Gesto de dedo liberado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-204">A finger released gesture.</span></span>

<span data-ttu-id="af3d9-205">**Microsoft. PerceptionSimulation. SimulatedGesture. Home**</span><span class="sxs-lookup"><span data-stu-id="af3d9-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="af3d9-206">El gesto Home/System.</span><span class="sxs-lookup"><span data-stu-id="af3d9-206">The home/system gesture.</span></span>

<span data-ttu-id="af3d9-207">**Microsoft. PerceptionSimulation. SimulatedGesture. Max**</span><span class="sxs-lookup"><span data-stu-id="af3d9-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="af3d9-208">El gesto máximo válido.</span><span class="sxs-lookup"><span data-stu-id="af3d9-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="af3d9-209">Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="af3d9-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="af3d9-210">Los posibles estados de un controlador simulado 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="af3d9-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="af3d9-211">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. OFF**</span><span class="sxs-lookup"><span data-stu-id="af3d9-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="af3d9-212">El controlador 6-DOF está desactivado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="af3d9-213">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. Active**</span><span class="sxs-lookup"><span data-stu-id="af3d9-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="af3d9-214">El controlador 6-DOF está activado y controlado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="af3d9-215">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="af3d9-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="af3d9-216">El controlador 6-DOF está activado, pero no se puede realizar su seguimiento.</span><span class="sxs-lookup"><span data-stu-id="af3d9-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="af3d9-217">Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="af3d9-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="af3d9-218">Los botones admitidos en un controlador simulado 6-DOF.</span><span class="sxs-lookup"><span data-stu-id="af3d9-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="af3d9-219">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**</span><span class="sxs-lookup"><span data-stu-id="af3d9-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="af3d9-220">Un valor de centinela que se usa para indicar que no hay botones.</span><span class="sxs-lookup"><span data-stu-id="af3d9-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="af3d9-221">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**</span><span class="sxs-lookup"><span data-stu-id="af3d9-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="af3d9-222">Se presiona el botón Inicio.</span><span class="sxs-lookup"><span data-stu-id="af3d9-222">The Home button is pressed.</span></span>

<span data-ttu-id="af3d9-223">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Menu**</span><span class="sxs-lookup"><span data-stu-id="af3d9-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="af3d9-224">Se presiona el botón de menú.</span><span class="sxs-lookup"><span data-stu-id="af3d9-224">The Menu button is pressed.</span></span>

<span data-ttu-id="af3d9-225">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. control**</span><span class="sxs-lookup"><span data-stu-id="af3d9-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="af3d9-226">Se presiona el botón de control.</span><span class="sxs-lookup"><span data-stu-id="af3d9-226">The Grip button is pressed.</span></span>

<span data-ttu-id="af3d9-227">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="af3d9-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="af3d9-228">El TouchPad está presionado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="af3d9-229">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**</span><span class="sxs-lookup"><span data-stu-id="af3d9-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="af3d9-230">Se presiona el botón seleccionar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-230">The Select button is pressed.</span></span>

<span data-ttu-id="af3d9-231">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="af3d9-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="af3d9-232">El TouchPad se toca.</span><span class="sxs-lookup"><span data-stu-id="af3d9-232">The TouchPad is touched.</span></span>

<span data-ttu-id="af3d9-233">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Stick**</span><span class="sxs-lookup"><span data-stu-id="af3d9-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="af3d9-234">Se presiona el stick.</span><span class="sxs-lookup"><span data-stu-id="af3d9-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="af3d9-235">**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**</span><span class="sxs-lookup"><span data-stu-id="af3d9-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="af3d9-236">El botón válido máximo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="af3d9-237">Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="af3d9-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="af3d9-238">El estado de calibrado de los ojos simulados</span><span class="sxs-lookup"><span data-stu-id="af3d9-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="af3d9-239">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. no disponible**</span><span class="sxs-lookup"><span data-stu-id="af3d9-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="af3d9-240">La calibración de ojos no está disponible.</span><span class="sxs-lookup"><span data-stu-id="af3d9-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="af3d9-241">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**</span><span class="sxs-lookup"><span data-stu-id="af3d9-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="af3d9-242">Los ojos se han calibrado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="af3d9-243">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-243">This is the default value.</span></span>

<span data-ttu-id="af3d9-244">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. configurando**</span><span class="sxs-lookup"><span data-stu-id="af3d9-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="af3d9-245">Los ojos se están calibrando.</span><span class="sxs-lookup"><span data-stu-id="af3d9-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="af3d9-246">**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="af3d9-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="af3d9-247">Los ojos deben calibrarse.</span><span class="sxs-lookup"><span data-stu-id="af3d9-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="af3d9-248">Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="af3d9-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="af3d9-249">La precisión del seguimiento de una Unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="af3d9-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="af3d9-250">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. no disponible**</span><span class="sxs-lookup"><span data-stu-id="af3d9-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="af3d9-251">No se realiza el seguimiento de la Unión.</span><span class="sxs-lookup"><span data-stu-id="af3d9-251">The joint is not tracked.</span></span>

<span data-ttu-id="af3d9-252">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**</span><span class="sxs-lookup"><span data-stu-id="af3d9-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="af3d9-253">Se deduce la posición de la Unión.</span><span class="sxs-lookup"><span data-stu-id="af3d9-253">The joint position is inferred.</span></span>

<span data-ttu-id="af3d9-254">**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. visible**</span><span class="sxs-lookup"><span data-stu-id="af3d9-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="af3d9-255">Se realiza un seguimiento completo de la Unión.</span><span class="sxs-lookup"><span data-stu-id="af3d9-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="af3d9-256">Microsoft. PerceptionSimulation. SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="af3d9-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="af3d9-257">La precisión del seguimiento de una Unión de la mano.</span><span class="sxs-lookup"><span data-stu-id="af3d9-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="af3d9-258">**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**</span><span class="sxs-lookup"><span data-stu-id="af3d9-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="af3d9-259">Las uniones de dedos de la mano se configuran para reflejar una pose cerrada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="af3d9-260">**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**</span><span class="sxs-lookup"><span data-stu-id="af3d9-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="af3d9-261">Las uniones de dedos de la mano se configuran para reflejar una pose abierta.</span><span class="sxs-lookup"><span data-stu-id="af3d9-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="af3d9-262">**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**</span><span class="sxs-lookup"><span data-stu-id="af3d9-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="af3d9-263">Las uniones de dedos de la mano se configuran para reflejar una postura señaladora.</span><span class="sxs-lookup"><span data-stu-id="af3d9-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="af3d9-264">**Microsoft. PerceptionSimulation. SimulatedHandPose. Pinch**</span><span class="sxs-lookup"><span data-stu-id="af3d9-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="af3d9-265">Las uniones de dedos de la mano se configuran para reflejar una pose de pinch.</span><span class="sxs-lookup"><span data-stu-id="af3d9-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="af3d9-266">**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**</span><span class="sxs-lookup"><span data-stu-id="af3d9-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="af3d9-267">Valor máximo válido para SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="af3d9-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="af3d9-268">Microsoft. PerceptionSimulation. PlaybackState</span><span class="sxs-lookup"><span data-stu-id="af3d9-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="af3d9-269">Describe el estado de una reproducción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="af3d9-270">**Microsoft. PerceptionSimulation. PlaybackState. Stopped**</span><span class="sxs-lookup"><span data-stu-id="af3d9-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="af3d9-271">La grabación está actualmente detenida y lista para su reproducción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="af3d9-272">**Microsoft. PerceptionSimulation. PlaybackState. Playing**</span><span class="sxs-lookup"><span data-stu-id="af3d9-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="af3d9-273">La grabación se está reproduciendo actualmente.</span><span class="sxs-lookup"><span data-stu-id="af3d9-273">The recording is currently playing.</span></span>

<span data-ttu-id="af3d9-274">**Microsoft. PerceptionSimulation. PlaybackState. pausado**</span><span class="sxs-lookup"><span data-stu-id="af3d9-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="af3d9-275">La grabación está en pausa actualmente.</span><span class="sxs-lookup"><span data-stu-id="af3d9-275">The recording is currently paused.</span></span>

<span data-ttu-id="af3d9-276">**Microsoft. PerceptionSimulation. PlaybackState. end**</span><span class="sxs-lookup"><span data-stu-id="af3d9-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="af3d9-277">La grabación ha alcanzado el final.</span><span class="sxs-lookup"><span data-stu-id="af3d9-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="af3d9-278">Microsoft. PerceptionSimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="af3d9-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="af3d9-279">Describe un vector de 3 componentes, que puede describir un punto o un vector en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="af3d9-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="af3d9-280">**Microsoft. PerceptionSimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="af3d9-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="af3d9-281">Componente X del vector.</span><span class="sxs-lookup"><span data-stu-id="af3d9-281">The X component of the vector.</span></span>

<span data-ttu-id="af3d9-282">**Microsoft. PerceptionSimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="af3d9-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="af3d9-283">Componente Y del vector.</span><span class="sxs-lookup"><span data-stu-id="af3d9-283">The Y component of the vector.</span></span>

<span data-ttu-id="af3d9-284">**Microsoft. PerceptionSimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="af3d9-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="af3d9-285">Componente Z del vector.</span><span class="sxs-lookup"><span data-stu-id="af3d9-285">The Z component of the vector.</span></span>

<span data-ttu-id="af3d9-286">**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="af3d9-287">Construya un nuevo Vector3.</span><span class="sxs-lookup"><span data-stu-id="af3d9-287">Construct a new Vector3.</span></span>

<span data-ttu-id="af3d9-288">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-288">Parameters</span></span>
* <span data-ttu-id="af3d9-289">x: el componente x del vector.</span><span class="sxs-lookup"><span data-stu-id="af3d9-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="af3d9-290">y: el componente y del vector.</span><span class="sxs-lookup"><span data-stu-id="af3d9-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="af3d9-291">z: el componente z del vector.</span><span class="sxs-lookup"><span data-stu-id="af3d9-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="af3d9-292">Microsoft. PerceptionSimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="af3d9-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="af3d9-293">Describe un giro de 3 componentes.</span><span class="sxs-lookup"><span data-stu-id="af3d9-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="af3d9-294">**Microsoft. PerceptionSimulation. Rotation3. Brea**</span><span class="sxs-lookup"><span data-stu-id="af3d9-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="af3d9-295">El componente de tono de la rotación, en torno al eje X.</span><span class="sxs-lookup"><span data-stu-id="af3d9-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="af3d9-296">**Microsoft. PerceptionSimulation. Rotation3. guiñada**</span><span class="sxs-lookup"><span data-stu-id="af3d9-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="af3d9-297">Componente de guiñada de la rotación, justo alrededor del eje Y.</span><span class="sxs-lookup"><span data-stu-id="af3d9-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="af3d9-298">**Microsoft. PerceptionSimulation. Rotation3. roll**</span><span class="sxs-lookup"><span data-stu-id="af3d9-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="af3d9-299">Componente de rollo de la rotación, justo alrededor del eje Z.</span><span class="sxs-lookup"><span data-stu-id="af3d9-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="af3d9-300">**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="af3d9-301">Construya un nuevo Rotation3.</span><span class="sxs-lookup"><span data-stu-id="af3d9-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="af3d9-302">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-302">Parameters</span></span>
* <span data-ttu-id="af3d9-303">paso: el componente de paso de la rotación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="af3d9-304">guiñada: el componente de guiñada de la rotación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="af3d9-305">rollo: componente de rollo de la rotación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="af3d9-306">Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="af3d9-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="af3d9-307">Describe la configuración de una Unión en una mano simulada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="af3d9-308">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="af3d9-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="af3d9-309">La posición de la Unión.</span><span class="sxs-lookup"><span data-stu-id="af3d9-309">The position of the joint.</span></span>

<span data-ttu-id="af3d9-310">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="af3d9-311">Rotación de la Unión.</span><span class="sxs-lookup"><span data-stu-id="af3d9-311">The rotation of the joint.</span></span>

<span data-ttu-id="af3d9-312">**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="af3d9-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="af3d9-313">La precisión del seguimiento de la Unión.</span><span class="sxs-lookup"><span data-stu-id="af3d9-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="af3d9-314">Microsoft. PerceptionSimulation. frustum</span><span class="sxs-lookup"><span data-stu-id="af3d9-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="af3d9-315">Describe un frustum de vista, tal y como lo usa normalmente una cámara.</span><span class="sxs-lookup"><span data-stu-id="af3d9-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="af3d9-316">**Microsoft. PerceptionSimulation. frustum. Near**</span><span class="sxs-lookup"><span data-stu-id="af3d9-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="af3d9-317">Distancia mínima contenida en el frustum.</span><span class="sxs-lookup"><span data-stu-id="af3d9-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="af3d9-318">**Microsoft. PerceptionSimulation. frustum. Far**</span><span class="sxs-lookup"><span data-stu-id="af3d9-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="af3d9-319">La distancia máxima contenida en el frustum.</span><span class="sxs-lookup"><span data-stu-id="af3d9-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="af3d9-320">**Microsoft. PerceptionSimulation. frustum. FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="af3d9-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="af3d9-321">Campo horizontal de la vista del frustum, en radianes (menor que PI).</span><span class="sxs-lookup"><span data-stu-id="af3d9-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="af3d9-322">**Microsoft. PerceptionSimulation. frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="af3d9-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="af3d9-323">La proporción del campo horizontal de la vista en el campo vertical de la vista.</span><span class="sxs-lookup"><span data-stu-id="af3d9-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="af3d9-324">Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration</span><span class="sxs-lookup"><span data-stu-id="af3d9-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="af3d9-325">Describe la configuración de la pantalla del casco simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-325">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="af3d9-326">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyePosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="af3d9-327">La transformación desde el centro de la cabeza hacia la izquierda para fines de representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="af3d9-328">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. LeftEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="af3d9-329">Rotación del ojo izquierdo de la representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="af3d9-330">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyePosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="af3d9-331">La transformación desde el centro del cabezal hasta el ojo adecuado para fines de representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="af3d9-332">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. RightEyeRotation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="af3d9-333">La rotación del ojo adecuado para fines de representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="af3d9-334">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. IPD**</span><span class="sxs-lookup"><span data-stu-id="af3d9-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="af3d9-335">El valor de IPD indicado por el sistema para la representación de estéreo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="af3d9-336">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyEyeTransforms**</span><span class="sxs-lookup"><span data-stu-id="af3d9-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="af3d9-337">El hecho de que los valores proporcionados para las transformaciones de ojo izquierdo y derecho se consideren válidos y se apliquen al sistema en ejecución.</span><span class="sxs-lookup"><span data-stu-id="af3d9-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="af3d9-338">**Microsoft. PerceptionSimulation. SimulatedDisplayConfiguration. ApplyIpd**</span><span class="sxs-lookup"><span data-stu-id="af3d9-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="af3d9-339">Si el valor proporcionado para IPD se debe considerar válido y se puede aplicar al sistema en ejecución.</span><span class="sxs-lookup"><span data-stu-id="af3d9-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="af3d9-340">Microsoft. PerceptionSimulation. IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="af3d9-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="af3d9-341">Raíz para generar los paquetes usados para controlar un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="af3d9-342">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**</span><span class="sxs-lookup"><span data-stu-id="af3d9-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="af3d9-343">Recupere el objeto de dispositivo simulado que interpreta el usuario simulado y el mundo simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="af3d9-344">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**</span><span class="sxs-lookup"><span data-stu-id="af3d9-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="af3d9-345">Recupera el objeto que controla el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="af3d9-346">**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**</span><span class="sxs-lookup"><span data-stu-id="af3d9-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="af3d9-347">Restablece el estado predeterminado de la simulación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="af3d9-348">Microsoft. PerceptionSimulation. ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="af3d9-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="af3d9-349">Interfaz que describe el dispositivo que interpreta el mundo simulado y el usuario simulado</span><span class="sxs-lookup"><span data-stu-id="af3d9-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="af3d9-350">**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="af3d9-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="af3d9-351">Recupere el rastreador principal del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="af3d9-352">**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**</span><span class="sxs-lookup"><span data-stu-id="af3d9-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="af3d9-353">Recupere el seguimiento de manos del dispositivo simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="af3d9-354">**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="af3d9-355">Establezca las propiedades del dispositivo simulado para que coincida con el tipo de dispositivo proporcionado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="af3d9-356">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-356">Parameters</span></span>
* <span data-ttu-id="af3d9-357">tipo: el nuevo tipo de dispositivo simulado</span><span class="sxs-lookup"><span data-stu-id="af3d9-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="af3d9-358">Microsoft. PerceptionSimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="af3d9-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="af3d9-359">Las propiedades adicionales están disponibles al convertir ISimulatedDevice en ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="af3d9-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="af3d9-360">**Microsoft. PerceptionSimulation. ISimulatedDevice2. IsUserPresent**</span><span class="sxs-lookup"><span data-stu-id="af3d9-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="af3d9-361">Recupera o establece si el usuario simulado está usando activamente el casco.</span><span class="sxs-lookup"><span data-stu-id="af3d9-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="af3d9-362">**Microsoft. PerceptionSimulation. ISimulatedDevice2. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="af3d9-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="af3d9-363">Recupera o establece las propiedades de la pantalla simulada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="af3d9-364">Microsoft. PerceptionSimulation. ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="af3d9-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="af3d9-365">Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento del encabezado del usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="af3d9-366">**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="af3d9-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="af3d9-367">Recupera y establece el modo de seguimiento de encabezado actual.</span><span class="sxs-lookup"><span data-stu-id="af3d9-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="af3d9-368">Microsoft. PerceptionSimulation. ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="af3d9-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="af3d9-369">Interfaz que describe la parte del dispositivo simulado que hace un seguimiento de las manos del usuario simulado</span><span class="sxs-lookup"><span data-stu-id="af3d9-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="af3d9-370">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="af3d9-371">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="af3d9-372">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**</span><span class="sxs-lookup"><span data-stu-id="af3d9-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="af3d9-373">Recupera y establece la posición del seguimiento de mano simulado, en relación con el centro del encabezado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="af3d9-374">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Brea**</span><span class="sxs-lookup"><span data-stu-id="af3d9-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="af3d9-375">Recupere y establezca el tono hacia abajo del seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="af3d9-376">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="af3d9-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="af3d9-377">Recupera y establece si se omite el frustum del seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="af3d9-378">Cuando se omite, ambas manecillas siempre están visibles.</span><span class="sxs-lookup"><span data-stu-id="af3d9-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="af3d9-379">Cuando no se omite (el valor predeterminado), las manecillas solo están visibles cuando se encuentran dentro del frustum del seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="af3d9-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="af3d9-380">**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**</span><span class="sxs-lookup"><span data-stu-id="af3d9-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="af3d9-381">Recupere y establezca las propiedades de frustum utilizadas para determinar si las manecillas están visibles para el seguimiento de mano simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="af3d9-382">Microsoft. PerceptionSimulation. ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="af3d9-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="af3d9-383">Interfaz de nivel superior para controlar el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="af3d9-384">**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="af3d9-385">Recuperar y establecer la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="af3d9-386">La posición corresponde a un punto en el centro de los pies del hombre.</span><span class="sxs-lookup"><span data-stu-id="af3d9-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="af3d9-387">**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="af3d9-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="af3d9-388">Recupere y establezca la dirección de las caras humanas simuladas del mundo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="af3d9-389">0 radianes se orientan hacia abajo en el eje Z negativo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="af3d9-390">Los radianes positivos giran en el sentido de las agujas del reloj sobre el eje Y.</span><span class="sxs-lookup"><span data-stu-id="af3d9-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="af3d9-391">**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**</span><span class="sxs-lookup"><span data-stu-id="af3d9-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="af3d9-392">Recupere y establezca el alto del hombre simulado, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="af3d9-393">**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**</span><span class="sxs-lookup"><span data-stu-id="af3d9-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="af3d9-394">Recupere el lado izquierdo del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="af3d9-395">**Microsoft. PerceptionSimulation. ISimulatedHuman. derecho**</span><span class="sxs-lookup"><span data-stu-id="af3d9-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="af3d9-396">Recupere la mano derecha del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="af3d9-397">**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**</span><span class="sxs-lookup"><span data-stu-id="af3d9-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="af3d9-398">Recupera el encabezado del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="af3d9-399">**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="af3d9-400">Mover el humano simulado con respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="af3d9-401">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-401">Parameters</span></span>
* <span data-ttu-id="af3d9-402">Translation: la traducción que se va a mover, relativa a la posición actual.</span><span class="sxs-lookup"><span data-stu-id="af3d9-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="af3d9-403">**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="af3d9-404">Girar el hombre simulado con respecto a su dirección actual, en el sentido de las agujas del reloj sobre el eje Y</span><span class="sxs-lookup"><span data-stu-id="af3d9-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="af3d9-405">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-405">Parameters</span></span>
* <span data-ttu-id="af3d9-406">radianes: la cantidad que se va a girar alrededor del eje Y.</span><span class="sxs-lookup"><span data-stu-id="af3d9-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="af3d9-407">Microsoft. PerceptionSimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="af3d9-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="af3d9-408">Las propiedades adicionales están disponibles al convertir ISimulatedHuman en ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="af3d9-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="af3d9-409">**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**</span><span class="sxs-lookup"><span data-stu-id="af3d9-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="af3d9-410">Recupere el controlador de 6-DOF izquierdo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="af3d9-411">**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**</span><span class="sxs-lookup"><span data-stu-id="af3d9-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="af3d9-412">Recupere el controlador de 6-DOF adecuado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="af3d9-413">Microsoft. PerceptionSimulation. ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="af3d9-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="af3d9-414">Interfaz que describe una mano del usuario simulado</span><span class="sxs-lookup"><span data-stu-id="af3d9-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="af3d9-415">**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="af3d9-416">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="af3d9-417">**Microsoft. PerceptionSimulation. ISimulatedHand. Position**</span><span class="sxs-lookup"><span data-stu-id="af3d9-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="af3d9-418">Recupera y establece la posición de la mano simulada en relación con el hombre, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="af3d9-419">**Microsoft. PerceptionSimulation. ISimulatedHand. activado**</span><span class="sxs-lookup"><span data-stu-id="af3d9-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="af3d9-420">Recupera y establece si la mano está activada actualmente.</span><span class="sxs-lookup"><span data-stu-id="af3d9-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="af3d9-421">**Microsoft. PerceptionSimulation. ISimulatedHand. visible**</span><span class="sxs-lookup"><span data-stu-id="af3d9-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="af3d9-422">Recupera si la mano es visible actualmente para SimulatedDevice (es decir, si se encuentra en una posición que HandTracker).</span><span class="sxs-lookup"><span data-stu-id="af3d9-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="af3d9-423">**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="af3d9-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="af3d9-424">Mueva la mano para que sea visible para el SimulatedDevice.</span><span class="sxs-lookup"><span data-stu-id="af3d9-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="af3d9-425">**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="af3d9-426">Mover la posición de la mano simulada en relación con su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="af3d9-427">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-427">Parameters</span></span>
* <span data-ttu-id="af3d9-428">Translation: la cantidad que se va a trasladar a la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="af3d9-429">**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="af3d9-430">Realizar un gesto mediante la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="af3d9-431">Solo lo detectará el sistema si está habilitada la mano.</span><span class="sxs-lookup"><span data-stu-id="af3d9-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="af3d9-432">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-432">Parameters</span></span>
* <span data-ttu-id="af3d9-433">gesto: el gesto que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="af3d9-434">Microsoft. PerceptionSimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="af3d9-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="af3d9-435">Las propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand2.</span><span class="sxs-lookup"><span data-stu-id="af3d9-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="af3d9-436">**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="af3d9-437">Recupera o establece la rotación de la mano simulada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="af3d9-438">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="af3d9-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="af3d9-439">Microsoft. PerceptionSimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="af3d9-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="af3d9-440">Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="af3d9-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="af3d9-441">**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="af3d9-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="af3d9-442">Obtiene la configuración conjunta de la Unión especificada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="af3d9-443">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="af3d9-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="af3d9-444">Establezca la configuración conjunta de la Unión especificada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="af3d9-445">**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="af3d9-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="af3d9-446">Establezca la mano en una pose conocida con una marca opcional que se va a animar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="af3d9-447">Nota: la animación no provocará que las uniones reflejen inmediatamente sus configuraciones de conjuntos finales.</span><span class="sxs-lookup"><span data-stu-id="af3d9-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="af3d9-448">Microsoft. PerceptionSimulation. ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="af3d9-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="af3d9-449">Interfaz que describe el encabezado del usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="af3d9-450">**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="af3d9-451">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="af3d9-452">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="af3d9-453">Recupera el giro del encabezado simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="af3d9-454">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="af3d9-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="af3d9-455">**Microsoft. PerceptionSimulation. ISimulatedHead. diameter**</span><span class="sxs-lookup"><span data-stu-id="af3d9-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="af3d9-456">Recuperar el diámetro del cabezal simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="af3d9-457">Este valor se usa para determinar el centro del encabezado (punto de giro).</span><span class="sxs-lookup"><span data-stu-id="af3d9-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="af3d9-458">**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="af3d9-459">Gira el encabezado simulado con respecto a su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="af3d9-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="af3d9-460">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="af3d9-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="af3d9-461">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-461">Parameters</span></span>
* <span data-ttu-id="af3d9-462">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="af3d9-463">Microsoft. PerceptionSimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="af3d9-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="af3d9-464">Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHead a ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="af3d9-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="af3d9-465">**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="af3d9-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="af3d9-466">Recupere los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="af3d9-467">Microsoft. PerceptionSimulation. ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="af3d9-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="af3d9-468">Interfaz que describe un controlador de 6 DOF asociado con el usuario simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="af3d9-469">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="af3d9-470">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="af3d9-471">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**</span><span class="sxs-lookup"><span data-stu-id="af3d9-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="af3d9-472">Recupera o establece el estado actual del controlador.</span><span class="sxs-lookup"><span data-stu-id="af3d9-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="af3d9-473">El estado del controlador debe establecerse en un valor distinto de OFF antes de que las llamadas a Move, gire o presione botones se realicen correctamente.</span><span class="sxs-lookup"><span data-stu-id="af3d9-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="af3d9-474">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**</span><span class="sxs-lookup"><span data-stu-id="af3d9-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="af3d9-475">Recupera o establece la posición del controlador simulado con respecto al hombre, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="af3d9-476">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="af3d9-477">Recupera o establece la orientación del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="af3d9-478">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="af3d9-479">Mover la posición del controlador simulado con respecto a su posición actual, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="af3d9-480">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-480">Parameters</span></span>
* <span data-ttu-id="af3d9-481">Translation: la cantidad para traducir el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="af3d9-482">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="af3d9-483">Presione un botón en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="af3d9-484">Solo lo detectará el sistema si el controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="af3d9-485">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-485">Parameters</span></span>
* <span data-ttu-id="af3d9-486">Button: botón que se va a presionar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-486">button - The button to press.</span></span>

<span data-ttu-id="af3d9-487">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="af3d9-488">Suelte un botón en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="af3d9-489">Solo lo detectará el sistema si el controlador está habilitado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="af3d9-490">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-490">Parameters</span></span>
* <span data-ttu-id="af3d9-491">Button: el botón que se va a liberar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-491">button - The button to release.</span></span>

<span data-ttu-id="af3d9-492">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out Float, out float)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="af3d9-493">Obtiene la posición de un dedo simulado en el Touchpad del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="af3d9-494">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-494">Parameters</span></span>
* <span data-ttu-id="af3d9-495">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="af3d9-496">y: posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="af3d9-497">**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="af3d9-498">Establece la posición de un dedo simulado en el Touchpad del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="af3d9-499">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-499">Parameters</span></span>
* <span data-ttu-id="af3d9-500">x: la posición horizontal del dedo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="af3d9-501">y: posición vertical del dedo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="af3d9-502">Microsoft. PerceptionSimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="af3d9-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="af3d9-503">Los métodos y propiedades adicionales están disponibles mediante la conversión de un ISimulatedSixDofController a ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="af3d9-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="af3d9-504">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out Float, out float)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="af3d9-505">Obtiene la posición del stick analógico simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="af3d9-506">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-506">Parameters</span></span>
* <span data-ttu-id="af3d9-507">x: la posición horizontal del Stick.</span><span class="sxs-lookup"><span data-stu-id="af3d9-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="af3d9-508">y: la posición vertical del Stick.</span><span class="sxs-lookup"><span data-stu-id="af3d9-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="af3d9-509">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="af3d9-510">Establece la posición del stick analógico simulado en el controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="af3d9-511">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-511">Parameters</span></span>
* <span data-ttu-id="af3d9-512">x: la posición horizontal del Stick.</span><span class="sxs-lookup"><span data-stu-id="af3d9-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="af3d9-513">y: la posición vertical del Stick.</span><span class="sxs-lookup"><span data-stu-id="af3d9-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="af3d9-514">**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="af3d9-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="af3d9-515">Recupera o establece el nivel de batería del controlador simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="af3d9-516">El valor debe ser mayor que 0,0 y menor o igual que 100,0.</span><span class="sxs-lookup"><span data-stu-id="af3d9-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="af3d9-517">Microsoft. PerceptionSimulation. ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="af3d9-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="af3d9-518">Interfaz que describe los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="af3d9-519">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="af3d9-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="af3d9-520">Recupera el giro de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="af3d9-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="af3d9-521">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="af3d9-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="af3d9-522">**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="af3d9-523">Gira los ojos simulados en relación con su rotación actual.</span><span class="sxs-lookup"><span data-stu-id="af3d9-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="af3d9-524">Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.</span><span class="sxs-lookup"><span data-stu-id="af3d9-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="af3d9-525">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-525">Parameters</span></span>
* <span data-ttu-id="af3d9-526">rotación: la cantidad que se va a girar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="af3d9-527">**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="af3d9-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="af3d9-528">Recupera o establece el estado de calibrado de los ojos simulados.</span><span class="sxs-lookup"><span data-stu-id="af3d9-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="af3d9-529">**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="af3d9-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="af3d9-530">Recupere la posición del nodo con relación al mundo, en metros.</span><span class="sxs-lookup"><span data-stu-id="af3d9-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="af3d9-531">Microsoft. PerceptionSimulation. ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="af3d9-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="af3d9-532">Interfaz para interactuar con un solo registro cargado para la reproducción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="af3d9-533">**Microsoft. PerceptionSimulation. ISimulationRecording. Datatypes**</span><span class="sxs-lookup"><span data-stu-id="af3d9-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="af3d9-534">Recupera la lista de tipos de datos de la grabación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="af3d9-535">**Microsoft. PerceptionSimulation. ISimulationRecording. State**</span><span class="sxs-lookup"><span data-stu-id="af3d9-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="af3d9-536">Recupera el estado actual de la grabación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="af3d9-537">**Microsoft. PerceptionSimulation. ISimulationRecording. Play**</span><span class="sxs-lookup"><span data-stu-id="af3d9-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="af3d9-538">Inicie la reproducción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-538">Start the playback.</span></span> <span data-ttu-id="af3d9-539">Si se pausa la grabación, la reproducción se reanudará desde la ubicación en pausa; Si se detiene, la reproducción se iniciará al principio.</span><span class="sxs-lookup"><span data-stu-id="af3d9-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="af3d9-540">Si ya se está reproduciendo, se omitirá esta llamada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="af3d9-541">**Microsoft. PerceptionSimulation. ISimulationRecording. PAUSE**</span><span class="sxs-lookup"><span data-stu-id="af3d9-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="af3d9-542">Pausa la reproducción en su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="af3d9-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="af3d9-543">Si se detiene la grabación, se omite la llamada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="af3d9-544">**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="af3d9-545">Busca la grabación en el tiempo especificado (en intervalos de 100 nanosegundos desde el principio) y se pausa en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="af3d9-546">Si el tiempo está más allá del final de la grabación, se pausa en el último fotograma.</span><span class="sxs-lookup"><span data-stu-id="af3d9-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="af3d9-547">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-547">Parameters</span></span>
* <span data-ttu-id="af3d9-548">TICs: la hora a la que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="af3d9-549">**Microsoft. PerceptionSimulation. ISimulationRecording. STOP**</span><span class="sxs-lookup"><span data-stu-id="af3d9-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="af3d9-550">Detiene la reproducción y restablece la posición al principio.</span><span class="sxs-lookup"><span data-stu-id="af3d9-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="af3d9-551">Microsoft. PerceptionSimulation. ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="af3d9-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="af3d9-552">Interfaz para recibir cambios de estado durante la reproducción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="af3d9-553">**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="af3d9-554">Se llama cuando el estado de reproducción de un ISimulationRecording ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="af3d9-555">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-555">Parameters</span></span>
* <span data-ttu-id="af3d9-556">newState: el nuevo estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="af3d9-557">Microsoft. PerceptionSimulation. PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="af3d9-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="af3d9-558">Objeto raíz para crear objetos de simulación de percepción.</span><span class="sxs-lookup"><span data-stu-id="af3d9-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="af3d9-559">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="af3d9-560">Cree en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="af3d9-561">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-561">Parameters</span></span>
* <span data-ttu-id="af3d9-562">receptor: el receptor que recibirá todos los paquetes generados.</span><span class="sxs-lookup"><span data-stu-id="af3d9-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="af3d9-563">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="af3d9-563">Return value</span></span>

<span data-ttu-id="af3d9-564">Administrador creado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-564">The created Manager.</span></span>

<span data-ttu-id="af3d9-565">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="af3d9-566">Cree un receptor que almacene todos los paquetes recibidos en un archivo en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="af3d9-567">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-567">Parameters</span></span>
* <span data-ttu-id="af3d9-568">Ruta de acceso: la ruta de acceso del archivo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="af3d9-568">path - The path of the file to create.</span></span>

<span data-ttu-id="af3d9-569">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="af3d9-569">Return value</span></span>

<span data-ttu-id="af3d9-570">Receptor creado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-570">The created sink.</span></span>

<span data-ttu-id="af3d9-571">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="af3d9-572">Cargar una grabación del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="af3d9-573">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-573">Parameters</span></span>
* <span data-ttu-id="af3d9-574">Ruta de acceso: la ruta de acceso del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="af3d9-575">Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="af3d9-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="af3d9-576">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="af3d9-576">Return value</span></span>

<span data-ttu-id="af3d9-577">Grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-577">The loaded recording.</span></span>

<span data-ttu-id="af3d9-578">**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="af3d9-579">Cargar una grabación del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="af3d9-580">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-580">Parameters</span></span>
* <span data-ttu-id="af3d9-581">Ruta de acceso: la ruta de acceso del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="af3d9-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="af3d9-582">Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="af3d9-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="af3d9-583">callback: devolución de llamada que recibe actualizaciones que retrasan el estado de la grabación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="af3d9-584">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="af3d9-584">Return value</span></span>

<span data-ttu-id="af3d9-585">Grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="af3d9-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="af3d9-586">Microsoft. PerceptionSimulation. StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="af3d9-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="af3d9-587">Describe los diferentes tipos de datos de secuencia.</span><span class="sxs-lookup"><span data-stu-id="af3d9-587">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="af3d9-588">**Microsoft. PerceptionSimulation. StreamDataTypes. None**</span><span class="sxs-lookup"><span data-stu-id="af3d9-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="af3d9-589">Un valor de centinela que se usa para indicar que no hay tipos de datos de flujo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="af3d9-590">**Microsoft. PerceptionSimulation. StreamDataTypes. Head**</span><span class="sxs-lookup"><span data-stu-id="af3d9-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="af3d9-591">Secuencia de datos con respecto a la posición y orientación del encabezado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="af3d9-592">**Microsoft. PerceptionSimulation. StreamDataTypes. handles**</span><span class="sxs-lookup"><span data-stu-id="af3d9-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="af3d9-593">Flujo de datos con respecto a la posición y los gestos de las manos.</span><span class="sxs-lookup"><span data-stu-id="af3d9-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="af3d9-594">**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="af3d9-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="af3d9-595">Flujo de datos con respecto a la asignación espacial del entorno.</span><span class="sxs-lookup"><span data-stu-id="af3d9-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="af3d9-596">**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**</span><span class="sxs-lookup"><span data-stu-id="af3d9-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="af3d9-597">Flujo de datos con respecto a la calibración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="af3d9-598">Los paquetes de calibración solo los acepta un sistema en modo remoto.</span><span class="sxs-lookup"><span data-stu-id="af3d9-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="af3d9-599">**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="af3d9-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="af3d9-600">Flujo de datos sobre el entorno del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="af3d9-601">**Microsoft. PerceptionSimulation. StreamDataTypes. SixDofControllers**</span><span class="sxs-lookup"><span data-stu-id="af3d9-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="af3d9-602">Flujo de datos con respecto a los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="af3d9-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="af3d9-603">**Microsoft. PerceptionSimulation. StreamDataTypes. Eyes**</span><span class="sxs-lookup"><span data-stu-id="af3d9-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="af3d9-604">Flujo de datos sobre los ojos del hombre simulado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="af3d9-605">**Microsoft. PerceptionSimulation. StreamDataTypes. DisplayConfiguration**</span><span class="sxs-lookup"><span data-stu-id="af3d9-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="af3d9-606">Flujo de datos con respecto a la configuración de pantalla del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="af3d9-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="af3d9-607">**Microsoft. PerceptionSimulation. StreamDataTypes. All**</span><span class="sxs-lookup"><span data-stu-id="af3d9-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="af3d9-608">Un valor de centinela que se usa para indicar todos los tipos de datos grabados.</span><span class="sxs-lookup"><span data-stu-id="af3d9-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="af3d9-609">Microsoft. PerceptionSimulation. ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="af3d9-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="af3d9-610">Objeto que recibe paquetes de datos de una secuencia de simulación.</span><span class="sxs-lookup"><span data-stu-id="af3d9-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="af3d9-611">**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint longitud, Byte [], paquete)**</span><span class="sxs-lookup"><span data-stu-id="af3d9-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="af3d9-612">Recibe un único paquete, que está escrito internamente y con control de versiones.</span><span class="sxs-lookup"><span data-stu-id="af3d9-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="af3d9-613">Parámetros</span><span class="sxs-lookup"><span data-stu-id="af3d9-613">Parameters</span></span>
* <span data-ttu-id="af3d9-614">longitud: la longitud del paquete.</span><span class="sxs-lookup"><span data-stu-id="af3d9-614">length - The length of the packet.</span></span>
* <span data-ttu-id="af3d9-615">paquete: los datos del paquete.</span><span class="sxs-lookup"><span data-stu-id="af3d9-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="af3d9-616">Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="af3d9-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="af3d9-617">Objeto que crea ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="af3d9-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="af3d9-618">**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**</span><span class="sxs-lookup"><span data-stu-id="af3d9-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="af3d9-619">Crea una única instancia de ISimulationStreamSink.</span><span class="sxs-lookup"><span data-stu-id="af3d9-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="af3d9-620">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="af3d9-620">Return value</span></span>

<span data-ttu-id="af3d9-621">Receptor creado.</span><span class="sxs-lookup"><span data-stu-id="af3d9-621">The created sink.</span></span>
