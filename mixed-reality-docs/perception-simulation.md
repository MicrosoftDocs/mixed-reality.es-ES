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
# <a name="perception-simulation"></a>Simulación de percepción

¿Desea crear una prueba automatizada de la aplicación? ¿Desea que las pruebas para ir más allá de las pruebas unitarias de nivel de componente y realmente ejercitar su aplicación-to-end? Simulación de percepción es lo está buscando. La biblioteca de simulación de percepción envía humana y mundo datos de entrada en la aplicación para que pueda automatizar las pruebas. Por ejemplo, puede simular la entrada de un humano busca una posición específica, repetible y, a continuación, realizar un gesto o con un controlador de movimiento.

Simulación de percepción puede enviar entrada simulado así a un HoloLens físico, el emulador de HoloLens (gen 1), el HoloLens 2 emulador o en un equipo con el Portal de realidad mixta instalado. Percepción simulación omite los sensores en directo en un dispositivo de realidad mixta y envía simula la entrada para aplicaciones que se ejecutan en el dispositivo. Las aplicaciones reciben estos eventos de entrada a través de las mismas API, use siempre y no se puede indicar la diferencia entre la ejecución con sensores reales frente a ejecutar con la simulación de percepción. Simulación de percepción es la misma tecnología que usa los emuladores de HoloLens para enviar la entrada simulado a la máquina Virtual de HoloLens.

Para empezar a usar la simulación en el código, empiece por crear un objeto IPerceptionSimulationManager. Desde ese objeto, puede emitir comandos para controlar las propiedades de un simulado "humano", incluida la posición principal, la posición de la mano y los gestos, y puede habilitar y manipular los controladores de movimiento.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configuración de un proyecto de Visual Studio para la simulación de percepción
1. [Instalar el emulador de HoloLens](install-the-tools.md) en el equipo de desarrollo. El emulador incluye las bibliotecas que se va a usar para la simulación de percepción.
2. Crear un nuevo Visual Studio C# proyecto de escritorio (un proyecto de consola funciona bien para empezar a trabajar).
3. Agregue los siguientes archivos binarios al proyecto como referencias (proyecto -> Agregar -> referencia...). Puede encontrarlos en % ProgramFiles (x86) %\Microsoft XDE\\(versión), como **% ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** para el emulador de HoloLens 2.  (Nota: aunque los archivos binarios forman parte del emulador de HoloLens 2, también funcionan en Windows Mixed Reality en el escritorio.) a. PerceptionSimulationManager.Interop.dll - Managed C# contenedor para la simulación de percepción.
    b. PerceptionSimulationRest.dll - Library para configurar un canal de comunicación de socket web al HoloLens o emulador.
    c. SimulationStream.Interop.dll - tipos compartidos para la simulación.
4. Agregue la implementación PerceptionSimulationManager.dll binarios al proyecto una. En primer lugar agregarlo al proyecto como un archivo binario (proyecto -> Agregar -> elemento existente...). Guárdelo como un vínculo para que no copiarlo a la carpeta de origen del proyecto. ![Agregar al proyecto como un vínculo PerceptionSimulationManager.dll](images/saveaslink.png) b. A continuación, asegúrese de que lo de la copia en la carpeta de salida en la compilación. Se trata en la hoja de propiedades para el archivo binario. ![Marcar PerceptionSimulationManager.dll para copiar en el directorio de salida](images/copyalways.png)
5. Establezca la plataforma de soluciones activas en x64.  (Use el Administrador de configuración para crear una entrada de la plataforma para x64 si aún no existe).

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Creación de un objeto de administrador IPerceptionSimulation

Para controlar la simulación, deberá emitir las actualizaciones a los objetos recuperados de un objeto IPerceptionSimulationManager. El primer paso es obtener ese objeto y conectarlo a su emulador o dispositivo de destino. Puede obtener la dirección IP de su emulador, haga clic en el botón de Portal de dispositivos en el [barra de herramientas](using-the-hololens-emulator.md)

![Icono de dispositivo Portal abierta](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.  Para Windows Mixed Reality, esto se puede recuperar en la aplicación de configuración en "Actualización y seguridad" y "para desarrolladores" en la "conectar mediante:" sección en "Habilitar Portal de dispositivo".  No olvide anotar la dirección IP y el puerto.

En primer lugar, llamaremos a RestSimulationStreamSink.Create para obtener un objeto RestSimulationStreamSink. Este es el dispositivo de destino o el emulador que se controlan a través de una conexión http. Se pasa a los comandos y controla el [Windows Device Portal](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador. Los cuatro parámetros que deberá crear un objeto son:
* Uri de URI: dirección IP del dispositivo de destino (por ejemplo, "http://123.123.123.123"o"http://123.123.123.123:50080")
* System.Net.NetworkCredential credenciales: nombre de usuario y contraseña para conectarse a la [Windows Device Portal](using-the-windows-device-portal.md) en el emulador o dispositivo de destino. Si se conecta con el emulador a través de su dirección local (p. ej., 168. *.* . *) en el mismo equipo, se aceptan las credenciales.
* normal: bool es True para una prioridad normal, false de prioridad baja. Por lo general desea establecerlo en *true* para escenarios de prueba, lo que permite la prueba para tomar el control.  El emulador y la simulación de Windows Mixed Reality usan conexiones de baja prioridad.  Si la prueba también utiliza una conexión de prioridad baja, el máximo establecido recientemente se cerrará en el control.
* Elemento System.Threading.CancellationToken token: Token para cancelar la operación asincrónica.

En segundo lugar, cree el IPerceptionSimulationManager. Este es el objeto que se usa para controlar la simulación. Tenga en cuenta que esto también se debe realizar en un método asincrónico.

## <a name="control-the-simulated-human"></a>Controlar a los humanos simulado

Un IPerceptionSimulationManager tiene una propiedad humana que devuelve un objeto ISimulatedHuman. Para controlar a los humanos simulado, realizar operaciones en este objeto. Por ejemplo:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Ejemplo básico C# aplicación de consola

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

## <a name="extended-sample-c-console-application"></a>Extended ejemplo C# aplicación de consola

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

## <a name="note-on-6-dof-controllers"></a>Tenga en cuenta en los controladores de 6 GDL

Antes de llamar a las propiedades en los métodos en un controlador de 6-GDL simulado, debe activar el controlador.  De no hacerlo, se producirá una excepción.  A partir de Windows 10 puede actualizar de 2019, se pueden instalar y activar estableciendo la propiedad Status del objeto ISimulatedSixDofController para SimulatedSixDofControllerStatus.Active controladores 6-GDL simulado.
En el 10 de octubre de 2018 de Windows Update y versiones anteriores, debe instalar por separado un controlador de 6-GDL simulado en primer lugar mediante una llamada a la herramienta PerceptionSimulationDevice ubicada en la carpeta \Windows\System32.  El uso de esta herramienta es como sigue:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Por ejemplo

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Acciones admitidas son:
* = install
* q = consulta
* r = quitar

Instancias admitidas son:
* 1 = el controlador de 6-GDL izquierdo
* 2 = el controlador derecho 6-GDL

El código de salida del proceso indicará (valor de retorno de un cero) de éxito o error (un valor devuelto distinto de cero).  Cuando se usa la acción 'q' para consultar si se instala un controlador, el valor devuelto será cero (0) si ya no está instalado el controlador o uno (1) si está instalado el controlador.

Al quitar un controlador de Windows 10 de octubre de 2018. actualice o anteriores, establece su estado desactivado a través de la API en primer lugar, a continuación, llamar a la herramienta PerceptionSimulationDevice.

Tenga en cuenta que esta herramienta se debe ejecutar como administrador.




## <a name="api-reference"></a>Referencia de API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Describe un tipo de dispositivo simulado

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Un dispositivo de referencia ficticia, el valor predeterminado para PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Describe el modo principal de la herramienta de seguimiento

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

De forma predeterminada Head de seguimiento. Esto significa que el sistema puede seleccionar el encabezado mejor según las condiciones de tiempo de ejecución del modo de seguimiento.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Orientación solo Head seguimiento. Esto significa que la posición de seguimiento puede no ser confiable y alguna funcionalidad depende de la posición principal no esté disponible.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Seguimiento de Head posicional. Esto significa que la posición principal sometidas a seguimiento y la orientación son confiables

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Describe un gesto simulado

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

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Un valor de centinela utilizado para no indicar ningún movimiento.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Un dedo presionado gesto.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Un gesto del dedo publicado.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

El gesto de inicio o de sistema.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

El gesto máximo válido.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

Los Estados posibles de un controlador de 6-GDL simulado.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

El controlador de 6 GDL está desactivado.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

El controlador de 6 GDL está encendido y realiza el seguimiento.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

El controlador de 6 GDL está activado pero no se puede realizar el seguimiento.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

Los botones admitidos en un controlador de 6-GDL simulado.

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

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

Un valor de centinela utilizado para no indicar ningún botón.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

Se presiona el botón de inicio.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

Se presiona el botón de menú.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

Se presiona el botón de control.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

El panel táctil está presionado.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

Se presiona el botón de selección.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

Se toca la pantalla táctil.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

Se presiona la tecla de navegación.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

El número máximo de botones válido.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

El estado de calibración de los ojos simulados

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

No está disponible la calibración de ojos.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

Han sido calibrados los ojos.  Este es el valor predeterminado.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

Se está calibran los ojos.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

Los ojos necesitan calibrarse.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

La precisión de seguimiento de una unión de la mano.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

No se realiza el seguimiento de la unión.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

La posición conjunta se infiere.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

La junta totalmente se realiza un seguimiento.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

La precisión de seguimiento de una unión de la mano.

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

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

Las uniones de la mano dedo se configuren para reflejar una postura cerrado.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

Las uniones de la mano dedo se configuren para reflejar una postura abierta.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

Las uniones de la mano dedo se configuren para reflejar una postura señalador.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

Las uniones de la mano dedo se configuren para reflejar una postura alejamiento.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

El máximo valor válido para SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Describe el estado de una reproducción.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

La grabación está actualmente detenido y listo para su reproducción.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

La grabación se está reproduciendo.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

Actualmente está en pausa la grabación.

**Microsoft.PerceptionSimulation.PlaybackState.End**

La grabación ha llegado al final.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Describe un vector de 3 componentes, que se puede describir un punto o un vector en el espacio 3D.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

Componente X del vector.

**Microsoft.PerceptionSimulation.Vector3.Y**

El componente Y del vector.

**Microsoft.PerceptionSimulation.Vector3.Z**

Componente Z del vector.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Construir un nuevo Vector3.

Parámetros
* x: el componente x del vector.
* y - el componente y del vector.
* z - el componente z del vector.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Describe un giro de 3 componentes.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

El componente de punto de rotación, abajo alrededor del eje X.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

El componente de rotación de la rotación, justo en el eje Y.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

El componente de rollo de rotación, justo en el eje Z.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Construir un nuevo Rotation3.

Parámetros
* pitch: el componente de tono de la rotación.
* guiñada: el componente de rotación de la rotación.
* Resumen: el componente de lanzamiento de la rotación.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

Describe la configuración de una unión en una mano simulada.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

La posición de la unión.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

La rotación de la unión.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

La precisión de seguimiento de la unión.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Describe un frustum de visualización, como suele ser utilizado por una cámara.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

La distancia mínima que se encuentra en el frustum.

**Microsoft.PerceptionSimulation.Frustum.Far**

La distancia máxima a la que se encuentra en el frustum.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Campo de visión horizontal de frustum, en radianes (menos de PI).

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

La proporción de campo de visión horizontal a vertical campo de visión.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Raíz para generar los paquetes utilizados para controlar un dispositivo.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Recuperar el objeto de dispositivo simulado que interpreta los humanos simulado y el mundo simulado.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Recuperar el objeto que controla a los humanos simulado.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

La simulación se restablece a su estado predeterminado.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Interfaz que describe el dispositivo que interpreta el mundo simulado y el usuario simulado

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Recuperar el Rastreador de Head del dispositivo simulado.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Recuperar el Rastreador de mano desde el dispositivo simulado.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Establecer las propiedades del dispositivo simulado para que coincida con el tipo de dispositivo proporcionado.

Parámetros
* tipo: el nuevo tipo de dispositivo simulado

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de la cabeza de los humanos simulado.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Recupera y establece el modo de seguimiento principal actual.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de las manos de los humanos simulado

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

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Recuperar la posición del nodo con respecto a la del mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Recuperar y establecer la posición de la herramienta de seguimiento de la mano simulado, en relación con el centro de la cabeza.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Recuperar y establecer el tono hacia abajo de la herramienta de seguimiento de la mano simulado.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Recuperar y establecer si se omite el frustum del Rastreador de mano simulado. Cuando se omite, dos manos siempre están visibles. Cuando no pasa por alto (predeterminado) manos solamente están visibles cuando estén dentro del frustum del Rastreador de mano.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Recuperar y establecer las propiedades de frustum utilizadas para determinar si son visibles para el seguimiento de la mano simulado manos.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Interfaz de nivel superior para controlar a los humanos simulado.

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

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

Recuperar y establecer la posición del nodo con respecto a la del mundo, en metros. La posición corresponde a un punto en el centro de metros del humanos.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

Recuperar y establecer las caras humanas simuladas de la dirección en el mundo. 0 radianes se enfrenta al eje Z negativo. Rotación radianes positivos sobre el eje Y.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

Recuperar y establecer el alto de los humanos simulado, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

Recuperar la parte izquierda de los humanos simulado.

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

Recuperar la parte derecha de los humanos simulado.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Recuperar el encabezado de los humanos simulado.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Mueva a los humanos simulado respecto a su posición actual, en metros.

Parámetros
* traducción: la traducción que se mueven en relación con la posición actual.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Girar a los humanos simulado con respecto a su dirección actual, las agujas del reloj sobre el eje Y

Parámetros
* radianes - la cantidad que se va a girar alrededor del eje Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

Propiedades adicionales están disponibles al convertir el ISimulatedHuman a ISimulatedHuman2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

Recuperar el controlador de 6-GDL izquierdo.

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

Recuperar el controlador derecho 6-GDL.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Interfaz que describe una mano de los humanos simulado

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

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Recuperar la posición del nodo con respecto a la del mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Recuperar y establecer la posición de la mano simulada con respecto a los humanos, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Recuperar y establecer si está activada actualmente la mano.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Recuperar datos si la mano está actualmente visible para el SimulatedDevice (es decir, si está en una posición para ser detectado por el HandTracker).

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Mover la mano de manera que es visible para el SimulatedDevice.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Mover la posición de la mano simulada respecto a su posición actual, en metros.

Parámetros
* traducción: la cantidad de traslación de la mano simulada.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Realizar un gesto de la mano simulada.  Solo se detectará el sistema si está habilitada la mano.

Parámetros
* gesto - gesto que se realice.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

Propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

Recuperar o establecer el giro de la mano simulado.  Radianes giran a la derecha al buscar en el eje positivo.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

Propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

Obtenga la configuración común para la unión especificada.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

Establezca la configuración común para la unión especificada.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

Establezca la mano para una postura conocido con una marca opcional que se va a animar.  Nota: la animación no origine articulaciones inmediatamente que refleja las configuraciones finales conjuntas.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Interfaz que describe el encabezado de los humanos simulado.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Recuperar la posición del nodo con respecto a la del mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Recuperar la rotación de la cabeza simulada. Radianes giran a la derecha al buscar en el eje positivo.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Recuperar el diámetro del encabezado simulado. Este valor se utiliza para determinar el centro del encabezado (punto de giro).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Girar la cabeza simulada con respecto a su rotación actual. Radianes giran a la derecha al buscar en el eje positivo.

Parámetros
* rotación: la cantidad que se va a girar.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

Propiedades adicionales están disponibles mediante la conversión de un ISimulatedHead a ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

Recuperar los ojos de los humanos simulado.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

Interfaz que describe un controlador de 6 GDL asociado con el usuario simulado.

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

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

Recuperar la posición del nodo con respecto a la del mundo, en metros.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

Recuperar o establecer el estado actual del controlador.  El estado del controlador debe establecerse en un valor distinto de desactivado antes de llamar a mover, girar o presione los botones se realizará correctamente.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

Recuperar o establecer la posición del controlador simulado con respecto a los humanos, en metros.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

Recuperar o establecer la orientación del controlador simulado.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

Mover la posición del controlador simulado respecto a su posición actual, en metros.

Parámetros
* traducción: la cantidad de traslación del controlador simulado.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

Presione un botón en el dispositivo simulado.  Solo se detectará el sistema si está habilitado el controlador.

Parámetros
* botón: presione el botón.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

Suelte un botón en el dispositivo simulado.  Solo se detectará el sistema si está habilitado el controlador.

Parámetros
* botón: el botón va a liberar.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**

Obtiene la posición de un dedo simulado en el panel táctil del dispositivo simulado.

Parámetros
* x: la posición horizontal del dedo.
* y - la posición vertical del dedo.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

Establezca la posición de un dedo simulado en el panel táctil del dispositivo simulado.

Parámetros
* x: la posición horizontal del dedo.
* y - la posición vertical del dedo.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

Métodos y propiedades adicionales están disponibles mediante la conversión de un ISimulatedSixDofController a ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**

Obtiene la posición de la tecla de navegación simulado en el controlador simulado.

Parámetros
* x: la posición horizontal de la tecla de navegación.
* y - la posición vertical de la tecla de navegación.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

Establezca la posición de la tecla de navegación simulado en el controlador simulado.

Parámetros
* x: la posición horizontal de la tecla de navegación.
* y - la posición vertical de la tecla de navegación.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

Recuperar o establecer el nivel de batería del controlador simulado.  El valor debe ser mayor que 0,0 y menor o igual que 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

Interfaz que describe los ojos de los humanos simulado.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

Recuperar la rotación de los ojos simulados. Radianes giran a la derecha al buscar en el eje positivo.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Gira los ojos simulados en relación con su rotación actual. Radianes giran a la derecha al buscar en el eje positivo.

Parámetros
* rotación: la cantidad que se va a girar.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

Recupera o establece el estado de calibración de los ojos simulados.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

Recuperar la posición del nodo con respecto a la del mundo, en metros.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Cargar la interfaz para interactuar con una grabación única para la reproducción.

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

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Recupera la lista de tipos de datos en la grabación.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Recupera el estado actual de la grabación.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Iniciar la reproducción. Si está en pausa la grabación, reproducción se reanudará desde la ubicación en pausa; Si se detiene, se iniciará la reproducción al principio. Si ya está reproduciendo, se omite esta llamada.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Pone en pausa la reproducción en su ubicación actual. Si se detiene la grabación, se omite la llamada.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Busca la grabación a la hora especificada (en intervalos de 100 nanosegundos desde el principio) y se detiene en esa ubicación. Si el tiempo es más allá del final de la grabación, está en pausa en el último fotograma.

Parámetros
* tics: el tiempo que se va a buscar.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Detiene la reproducción y restablece la posición al principio.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Interfaz para recibir los cambios de estado durante la reproducción.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Se llama cuando ha cambiado el estado de reproducción de un ISimulationRecording.

Parámetros
* newState - el nuevo estado de la grabación.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Objeto raíz para crear objetos de simulación de percepción.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Crear en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.

Parámetros
* Sink - el receptor que recibirá todos genera paquetes.

Valor devuelto

El administrador creado.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Crear un receptor que almacena los paquetes recibidos todo en un archivo en la ruta de acceso especificada.

Parámetros
* ruta de acceso: la ruta de acceso del archivo que se va a crear.

Valor devuelto

El receptor creado.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Cargar una grabación desde el archivo especificado.

Parámetros
* ruta de acceso: la ruta de acceso del archivo para cargar.
* Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario.

Valor devuelto

La grabación cargada.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Cargar una grabación desde el archivo especificado.

Parámetros
* ruta de acceso: la ruta de acceso del archivo para cargar.
* Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario.
* devolución de llamada - una devolución de llamada que recibe las actualizaciones reclasificación de estado de la grabación.

Valor devuelto

La grabación cargada.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Describe los diferentes tipos de datos de la secuencia.

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

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Un valor de centinela utilizado para no indicar ningún tipo de datos de la secuencia.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream de datos con respecto a la posición y la orientación de la cabeza.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Stream de datos con respecto a la posición y movimientos de manos.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Stream de datos con respecto a la asignación espacial del entorno.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Stream de datos con respecto a la calibración del dispositivo. Solo se aceptan los paquetes de calibración mediante un sistema en modo remoto.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Stream de datos relacionados con el entorno del dispositivo.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Un valor de centinela que se usa para indicar todos los tipos de datos registrados.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Un objeto que recibe los paquetes de datos de una secuencia de simulación.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

Recibe un solo paquete, que es internamente con tipo y con control de versiones.

Parámetros
* length: la longitud del paquete.
* paquete - los datos del paquete.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Objeto que crea ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Crea una instancia única de ISimulationStreamSink.

Valor devuelto

El receptor creado.
