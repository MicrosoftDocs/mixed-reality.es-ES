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
# <a name="perception-simulation"></a>Simulación de percepción

¿Desea crear una prueba automatizada para la aplicación? ¿Desea que las pruebas vayan más allá de las pruebas unitarias de nivel de componente y realmente ejecute su aplicación de un extremo a otro? La simulación de percepción es lo que está buscando. La biblioteca de simulación de percepción envía datos de entrada humanos y del mundo a la aplicación para que pueda automatizar las pruebas. Por ejemplo, puede simular la entrada de un usuario que busca una posición concreta y repetible y, a continuación, realizar un gesto o usar un controlador de movimiento.

La simulación de percepción puede enviar una entrada simulada como esta a una HoloLens física, el emulador de HoloLens (1ª generación), el emulador de HoloLens 2 o un equipo con el portal de realidad mixta instalado. La simulación de percepción omite los sensores en directo en un dispositivo de realidad mixta y envía una entrada simulada a las aplicaciones que se ejecutan en el dispositivo. Las aplicaciones reciben estos eventos de entrada a través de las mismas API que siempre usan y no indican la diferencia entre la ejecución con sensores reales y la ejecución con simulación de percepción. La simulación de percepción es la misma tecnología que usan los emuladores de HoloLens para enviar datos simulados a la máquina virtual HoloLens.

Para empezar a usar la simulación en el código, empiece por crear un objeto IPerceptionSimulationManager. Desde ese objeto, puede emitir comandos para controlar las propiedades de una "persona" simulada, incluida la posición del encabezado, la posición de la mano y los gestos, y puede habilitar y manipular los controladores de movimiento.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configuración de un proyecto de Visual Studio para la simulación de percepción
1. [Instale el emulador de HoloLens](install-the-tools.md) en el equipo de desarrollo. El emulador incluye las bibliotecas que se usarán para la simulación de percepción.
2. Cree un nuevo proyecto de C# Visual Studio Desktop (un proyecto de consola funciona bien para empezar a trabajar).
3. Agregue los siguientes archivos binarios al proyecto como referencias (proyecto-> referencia del complemento de >...). Puede encontrarlos en% ProgramFiles (x86)% \ Microsoft XDE\\(versión), como **% ProgramFiles (x86)% \ Microsoft XDE\\10.0.18362.0** para el emulador de HoloLens 2.  (Nota: aunque los archivos binarios forman parte del emulador de HoloLens 2, también funcionan para Windows Mixed Reality en el escritorio). un. PerceptionSimulationManager. Interop. dll: contenedor C# administrado para la simulación de percepción.
    b. PerceptionSimulationRest. dll-Library para configurar un canal de comunicación de socket web a HoloLens o emulador.
    c. SimulationStream. Interop. dll: tipos compartidos para la simulación.
4. Agregue el archivo binario de implementación PerceptionSimulationManager. dll al proyecto a. Agréguelo primero como un archivo binario al proyecto (proyecto-> Agregar > elemento existente...). Guárdelo como un vínculo para que no lo copie en la carpeta de origen del proyecto. ![Agregue PerceptionSimulationManager. dll al proyecto como un vínculo](images/saveaslink.png) b. Después, asegúrese de que se copia en la carpeta de salida en la compilación. Está en la hoja de propiedades del archivo binario. ![Marque PerceptionSimulationManager. dll para copiarlo en el directorio de salida](images/copyalways.png)
5. Establezca la plataforma de soluciones activa en x64.  (Utilice la Configuration Manager para crear una entrada de plataforma para x64 si aún no existe ninguna).

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Creación de un objeto de administrador de IPerceptionSimulation

Para controlar la simulación, emitirá actualizaciones de los objetos recuperados de un objeto IPerceptionSimulationManager. El primer paso es obtener ese objeto y conectarlo al dispositivo o emulador de destino. Para obtener la dirección IP del emulador, haga clic en el botón portal de dispositivos en la [barra de herramientas](using-the-hololens-emulator.md) .

![Abra el icono](images/emulator-deviceportal.png) del portal de dispositivos **abrir portal de dispositivos**: abre el Portal de dispositivos Windows correspondiente al sistema operativo de HoloLens en el emulador.  En el caso de Windows Mixed Reality, puede recuperarse en la aplicación de configuración en "actualizar & seguridad" y luego en "para desarrolladores" en la sección "conectar usando:" en "habilitar el portal de dispositivos".  Asegúrese de anotar la dirección IP y el puerto.

En primer lugar, llame a RestSimulationStreamSink. Create para obtener un objeto RestSimulationStreamSink. Este es el dispositivo de destino o el emulador que controlará la conexión http. Los comandos se pasarán y controlarán en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador. Los cuatro parámetros que necesitará para crear un objeto son:
* URI del URI: dirección IP del dispositivo de destino (por ejemplo,"http://123.123.123.123" o "http://123.123.123.123:50080")
* Credenciales de System .net. NetworkCredential: nombre de usuario/contraseña para conectarse al [portal de dispositivos de Windows](using-the-windows-device-portal.md) en el emulador o dispositivo de destino. Si se va a conectar al emulador a través de su dirección local (por ejemplo,*168.* . *) en el mismo equipo, se aceptarán las credenciales.
* bool normal: true para la prioridad normal; false para la prioridad baja. Por lo general, desea establecer este valor en *true* para los escenarios de prueba, lo que permite que la prueba tome el control.  El emulador y la simulación de Windows Mixed Reality usan conexiones de baja prioridad.  Si la prueba también usa una conexión de prioridad baja, la conexión establecida más recientemente tendrá el control.
* System. Threading. CancellationToken token-token para cancelar la operación asincrónica.

En segundo lugar, creará el IPerceptionSimulationManager. Este es el objeto que se usa para controlar la simulación. Tenga en cuenta que esto también debe realizarse en un método asincrónico.

## <a name="control-the-simulated-human"></a>Controlar el usuario simulado

Un IPerceptionSimulationManager tiene una propiedad humana que devuelve un objeto ISimulatedHuman. Para controlar el humano simulado, realice operaciones en este objeto. Por ejemplo:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Aplicación de C# consola de ejemplo básica

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

## <a name="extended-sample-c-console-application"></a>Aplicación de C# consola de ejemplo extendida

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

## <a name="note-on-6-dof-controllers"></a>Nota en los controladores de 6 DOF

Antes de llamar a cualquier propiedad de los métodos en un controlador simulado de 6 DOF, debe activar el controlador.  Si no lo hace, se producirá una excepción.  A partir de la actualización 2019 de Windows 10, se pueden instalar y activar controladores simulados de 6 DOF si se establece la propiedad Status en el objeto ISimulatedSixDofController en SimulatedSixDofControllerStatus. Active.
En la actualización de Windows 10 de octubre de 2018 y versiones anteriores, debe instalar por separado un controlador simulado de 6 DOF en primer lugar mediante una llamada a la herramienta PerceptionSimulationDevice que se encuentra en la carpeta \Windows\System32.  El uso de esta herramienta es el siguiente:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Por ejemplo,

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Las acciones admitidas son:
* i = instalación
* q = consulta
* r = quitar

Las instancias admitidas son:
* 1 = el controlador de 6 DOF izquierdo
* 2 = el controlador de 6 DOF adecuado

El código de salida del proceso indicará que la operación se ha realizado correctamente (un valor devuelto de cero) o un error (valor devuelto distinto de cero).  Al usar la acción ' q ' para consultar si está instalado un controlador, el valor devuelto será cero (0) si el controlador no está ya instalado o uno (1) si el controlador está instalado.

Al quitar un controlador en la actualización 2018 de octubre de Windows 10 o versiones anteriores, establezca su estado en desactivado a través de la API primero y, a continuación, llame a la herramienta PerceptionSimulationDevice.

Tenga en cuenta que esta herramienta debe ejecutarse como administrador.




## <a name="api-reference"></a>Referencia de API

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft. PerceptionSimulation. SimulatedDeviceType

Describe un tipo de dispositivo simulado

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft. PerceptionSimulation. SimulatedDeviceType. Reference**

Un dispositivo de referencia ficticio, el valor predeterminado para PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft. PerceptionSimulation. HeadTrackerMode

Describe un modo de seguimiento de encabezado

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft. PerceptionSimulation. HeadTrackerMode. default**

Seguimiento de encabezado predeterminado. Esto significa que el sistema puede seleccionar el mejor modo de seguimiento de los encabezados según las condiciones del tiempo de ejecución.

**Microsoft. PerceptionSimulation. HeadTrackerMode. Orientation**

Seguimiento de encabezado de solo orientación. Esto significa que es posible que la posición de la que se realiza el seguimiento no sea confiable y que algunas funciones que dependen de la posición principal no estén disponibles.

**Microsoft. PerceptionSimulation. HeadTrackerMode. Position**

Seguimiento de los cabezales posicionales. Esto significa que la posición y la orientación del encabezado controlados son confiables

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft. PerceptionSimulation. SimulatedGesture

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

**Microsoft. PerceptionSimulation. SimulatedGesture. None**

Un valor de centinela que se usa para indicar que no hay gestos.

**Microsoft. PerceptionSimulation. SimulatedGesture. FingerPressed**

Gesto de presionar un dedo.

**Microsoft. PerceptionSimulation. SimulatedGesture. FingerReleased**

Gesto de dedo liberado.

**Microsoft. PerceptionSimulation. SimulatedGesture. Home**

El gesto Home/System.

**Microsoft. PerceptionSimulation. SimulatedGesture. Max**

El gesto máximo válido.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus

Los posibles estados de un controlador simulado 6-DOF.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. OFF**

El controlador 6-DOF está desactivado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. Active**

El controlador 6-DOF está activado y controlado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerStatus. TrackingLost**

El controlador 6-DOF está activado, pero no se puede realizar su seguimiento.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton

Los botones admitidos en un controlador simulado 6-DOF.

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

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. None**

Un valor de centinela que se usa para indicar que no hay botones.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Home**

Se presiona el botón Inicio.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Menu**

Se presiona el botón de menú.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. control**

Se presiona el botón de control.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

El TouchPad está presionado.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Select**

Se presiona el botón seleccionar.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

El TouchPad se toca.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Stick**

Se presiona el stick.

**Microsoft. PerceptionSimulation. SimulatedSixDofControllerButton. Max**

El botón válido máximo.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState

El estado de calibrado de los ojos simulados

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. no disponible**

La calibración de ojos no está disponible.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. Ready**

Los ojos se han calibrado.  Este es el valor predeterminado.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. configurando**

Los ojos se están calibrando.

**Microsoft. PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

Los ojos deben calibrarse.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy

La precisión del seguimiento de una Unión de la mano.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. no disponible**

No se realiza el seguimiento de la Unión.

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. aproximado**

Se deduce la posición de la Unión.

**Microsoft. PerceptionSimulation. SimulatedHandJointTrackingAccuracy. visible**

Se realiza un seguimiento completo de la Unión.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft. PerceptionSimulation. SimulatedHandPose

La precisión del seguimiento de una Unión de la mano.

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

**Microsoft. PerceptionSimulation. SimulatedHandPose. Closed**

Las uniones de dedos de la mano se configuran para reflejar una pose cerrada.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Open**

Las uniones de dedos de la mano se configuran para reflejar una pose abierta.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Point**

Las uniones de dedos de la mano se configuran para reflejar una postura señaladora.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Pinch**

Las uniones de dedos de la mano se configuran para reflejar una pose de pinch.

**Microsoft. PerceptionSimulation. SimulatedHandPose. Max**

Valor máximo válido para SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft. PerceptionSimulation. PlaybackState

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

**Microsoft. PerceptionSimulation. PlaybackState. Stopped**

La grabación está actualmente detenida y lista para su reproducción.

**Microsoft. PerceptionSimulation. PlaybackState. Playing**

La grabación se está reproduciendo actualmente.

**Microsoft. PerceptionSimulation. PlaybackState. pausado**

La grabación está en pausa actualmente.

**Microsoft. PerceptionSimulation. PlaybackState. end**

La grabación ha alcanzado el final.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft. PerceptionSimulation. Vector3

Describe un vector de 3 componentes, que puede describir un punto o un vector en el espacio 3D.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft. PerceptionSimulation. Vector3. X**

Componente X del vector.

**Microsoft. PerceptionSimulation. Vector3. Y**

Componente Y del vector.

**Microsoft. PerceptionSimulation. Vector3. Z**

Componente Z del vector.

**Microsoft. PerceptionSimulation. Vector3. #ctor (System. single, System. single, System. Single)**

Construya un nuevo Vector3.

Parámetros
* x: el componente x del vector.
* y: el componente y del vector.
* z: el componente z del vector.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft. PerceptionSimulation. Rotation3

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

**Microsoft. PerceptionSimulation. Rotation3. Brea**

El componente de tono de la rotación, en torno al eje X.

**Microsoft. PerceptionSimulation. Rotation3. guiñada**

Componente de guiñada de la rotación, justo alrededor del eje Y.

**Microsoft. PerceptionSimulation. Rotation3. roll**

Componente de rollo de la rotación, justo alrededor del eje Z.

**Microsoft. PerceptionSimulation. Rotation3. #ctor (System. single, System. single, System. Single)**

Construya un nuevo Rotation3.

Parámetros
* paso: el componente de paso de la rotación.
* guiñada: el componente de guiñada de la rotación.
* rollo: componente de rollo de la rotación.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration

Describe la configuración de una Unión en una mano simulada.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Position**

La posición de la Unión.

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. Rotation**

Rotación de la Unión.

**Microsoft. PerceptionSimulation. SimulatedHandJointConfiguration. TrackingAccuracy**

La precisión del seguimiento de la Unión.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft. PerceptionSimulation. frustum

Describe un frustum de vista, tal y como lo usa normalmente una cámara.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft. PerceptionSimulation. frustum. Near**

Distancia mínima contenida en el frustum.

**Microsoft. PerceptionSimulation. frustum. Far**

La distancia máxima contenida en el frustum.

**Microsoft. PerceptionSimulation. frustum. FieldOfView**

Campo horizontal de la vista del frustum, en radianes (menor que PI).

**Microsoft. PerceptionSimulation. frustum. AspectRatio**

La proporción del campo horizontal de la vista en el campo vertical de la vista.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft. PerceptionSimulation. IPerceptionSimulationManager

Raíz para generar los paquetes usados para controlar un dispositivo.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Device**

Recupere el objeto de dispositivo simulado que interpreta el usuario simulado y el mundo simulado.

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Human**

Recupera el objeto que controla el usuario simulado.

**Microsoft. PerceptionSimulation. IPerceptionSimulationManager. Reset**

Restablece el estado predeterminado de la simulación.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft. PerceptionSimulation. ISimulatedDevice

Interfaz que describe el dispositivo que interpreta el mundo simulado y el usuario simulado

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft. PerceptionSimulation. ISimulatedDevice. HeadTracker**

Recupere el rastreador principal del dispositivo simulado.

**Microsoft. PerceptionSimulation. ISimulatedDevice. HandTracker**

Recupere el seguimiento de manos del dispositivo simulado.

**Microsoft. PerceptionSimulation. ISimulatedDevice. SetSimulatedDeviceType (Microsoft. PerceptionSimulation. SimulatedDeviceType)**

Establezca las propiedades del dispositivo simulado para que coincida con el tipo de dispositivo proporcionado.

Parámetros
* tipo: el nuevo tipo de dispositivo simulado

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft. PerceptionSimulation. ISimulatedHeadTracker

Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento del encabezado del usuario simulado.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft. PerceptionSimulation. ISimulatedHeadTracker. HeadTrackerMode**

Recupera y establece el modo de seguimiento de encabezado actual.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft. PerceptionSimulation. ISimulatedHandTracker

Interfaz que describe la parte del dispositivo simulado que hace un seguimiento de las manos del usuario simulado

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

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. WorldPosition**

Recupere la posición del nodo con relación al mundo, en metros.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Position**

Recupera y establece la posición del seguimiento de mano simulado, en relación con el centro del encabezado.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. Brea**

Recupere y establezca el tono hacia abajo del seguimiento de mano simulado.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**

Recupera y establece si se omite el frustum del seguimiento de mano simulado. Cuando se omite, ambas manecillas siempre están visibles. Cuando no se omite (el valor predeterminado), las manecillas solo están visibles cuando se encuentran dentro del frustum del seguimiento de la mano.

**Microsoft. PerceptionSimulation. ISimulatedHandTracker. frustum**

Recupere y establezca las propiedades de frustum utilizadas para determinar si las manecillas están visibles para el seguimiento de mano simulado.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft. PerceptionSimulation. ISimulatedHuman

Interfaz de nivel superior para controlar el usuario simulado.

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

**Microsoft. PerceptionSimulation. ISimulatedHuman. WorldPosition**

Recuperar y establecer la posición del nodo con relación al mundo, en metros. La posición corresponde a un punto en el centro de los pies del hombre.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Direction**

Recupere y establezca la dirección de las caras humanas simuladas del mundo. 0 radianes se orientan hacia abajo en el eje Z negativo. Los radianes positivos giran en el sentido de las agujas del reloj sobre el eje Y.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Height**

Recupere y establezca el alto del hombre simulado, en metros.

**Microsoft. PerceptionSimulation. ISimulatedHuman. LeftHand**

Recupere el lado izquierdo del hombre simulado.

**Microsoft. PerceptionSimulation. ISimulatedHuman. derecho**

Recupere la mano derecha del hombre simulado.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Head**

Recupera el encabezado del hombre simulado.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Move (Microsoft. PerceptionSimulation. Vector3)**

Mover el humano simulado con respecto a su posición actual, en metros.

Parámetros
* Translation: la traducción que se va a mover, relativa a la posición actual.

**Microsoft. PerceptionSimulation. ISimulatedHuman. Rotate (System. Single)**

Girar el hombre simulado con respecto a su dirección actual, en el sentido de las agujas del reloj sobre el eje Y

Parámetros
* radianes: la cantidad que se va a girar alrededor del eje Y.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft. PerceptionSimulation. ISimulatedHuman2

Las propiedades adicionales están disponibles al convertir ISimulatedHuman en ISimulatedHuman2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHuman2. LeftController**

Recupere el controlador de 6-DOF izquierdo.

**Microsoft. PerceptionSimulation. ISimulatedHuman2. RightController**

Recupere el controlador de 6-DOF adecuado.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft. PerceptionSimulation. ISimulatedHand

Interfaz que describe una mano del usuario simulado

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

**Microsoft. PerceptionSimulation. ISimulatedHand. WorldPosition**

Recupere la posición del nodo con relación al mundo, en metros.

**Microsoft. PerceptionSimulation. ISimulatedHand. Position**

Recupera y establece la posición de la mano simulada en relación con el hombre, en metros.

**Microsoft. PerceptionSimulation. ISimulatedHand. activado**

Recupera y establece si la mano está activada actualmente.

**Microsoft. PerceptionSimulation. ISimulatedHand. visible**

Recupera si la mano es visible actualmente para SimulatedDevice (es decir, si se encuentra en una posición que HandTracker).

**Microsoft. PerceptionSimulation. ISimulatedHand. EnsureVisible**

Mueva la mano para que sea visible para el SimulatedDevice.

**Microsoft. PerceptionSimulation. ISimulatedHand. Move (Microsoft. PerceptionSimulation. Vector3)**

Mover la posición de la mano simulada en relación con su posición actual, en metros.

Parámetros
* Translation: la cantidad que se va a trasladar a la mano simulada.

**Microsoft. PerceptionSimulation. ISimulatedHand. PerformGesture (Microsoft. PerceptionSimulation. SimulatedGesture)**

Realizar un gesto mediante la mano simulada.  Solo lo detectará el sistema si está habilitada la mano.

Parámetros
* gesto: el gesto que se va a realizar.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft. PerceptionSimulation. ISimulatedHand2

Las propiedades adicionales están disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand2.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHand2. Orientation**

Recupera o establece la rotación de la mano simulada.  Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft. PerceptionSimulation. ISimulatedHand3

Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHand a ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft. PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**

Obtiene la configuración conjunta de la Unión especificada.

**Microsoft. PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**

Establezca la configuración conjunta de la Unión especificada.

**Microsoft. PerceptionSimulation. ISimulatedHand3. SetHandPose**

Establezca la mano en una pose conocida con una marca opcional que se va a animar.  Nota: la animación no provocará que las uniones reflejen inmediatamente sus configuraciones de conjuntos finales.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft. PerceptionSimulation. ISimulatedHead

Interfaz que describe el encabezado del usuario simulado.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft. PerceptionSimulation. ISimulatedHead. WorldPosition**

Recupere la posición del nodo con relación al mundo, en metros.

**Microsoft. PerceptionSimulation. ISimulatedHead. Rotation**

Recupera el giro del encabezado simulado. Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.

**Microsoft. PerceptionSimulation. ISimulatedHead. diameter**

Recuperar el diámetro del cabezal simulado. Este valor se usa para determinar el centro del encabezado (punto de giro).

**Microsoft. PerceptionSimulation. ISimulatedHead. Rotate (Microsoft. PerceptionSimulation. Rotation3)**

Gira el encabezado simulado con respecto a su rotación actual. Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.

Parámetros
* rotación: la cantidad que se va a girar.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft. PerceptionSimulation. ISimulatedHead2

Hay propiedades adicionales disponibles mediante la conversión de un ISimulatedHead a ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedHead2. Eyes**

Recupere los ojos del hombre simulado.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft. PerceptionSimulation. ISimulatedSixDofController

Interfaz que describe un controlador de 6 DOF asociado con el usuario simulado.

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

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. WorldPosition**

Recupere la posición del nodo con relación al mundo, en metros.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. status**

Recupera o establece el estado actual del controlador.  El estado del controlador debe establecerse en un valor distinto de OFF antes de que las llamadas a Move, gire o presione botones se realicen correctamente.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Position**

Recupera o establece la posición del controlador simulado con respecto al hombre, en metros.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Orientation**

Recupera o establece la orientación del controlador simulado.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. Move (Microsoft. PerceptionSimulation. Vector3)**

Mover la posición del controlador simulado con respecto a su posición actual, en metros.

Parámetros
* Translation: la cantidad para traducir el controlador simulado.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. PressButton (SimulatedSixDofControllerButton)**

Presione un botón en el controlador simulado.  Solo lo detectará el sistema si el controlador está habilitado.

Parámetros
* Button: botón que se va a presionar.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. ReleaseButton (SimulatedSixDofControllerButton)**

Suelte un botón en el controlador simulado.  Solo lo detectará el sistema si el controlador está habilitado.

Parámetros
* Button: el botón que se va a liberar.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. GetTouchpadPosition (out Float, out float)**

Obtiene la posición de un dedo simulado en el Touchpad del controlador simulado.

Parámetros
* x: la posición horizontal del dedo.
* y: posición vertical del dedo.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController. SetTouchpadPosition (float, float)**

Establece la posición de un dedo simulado en el Touchpad del controlador simulado.

Parámetros
* x: la posición horizontal del dedo.
* y: posición vertical del dedo.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft. PerceptionSimulation. ISimulatedSixDofController2

Los métodos y propiedades adicionales están disponibles mediante la conversión de un ISimulatedSixDofController a ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. GetThumbstickPosition (out Float, out float)**

Obtiene la posición del stick analógico simulado en el controlador simulado.

Parámetros
* x: la posición horizontal del Stick.
* y: la posición vertical del Stick.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. SetThumbstickPosition (float, float)**

Establece la posición del stick analógico simulado en el controlador simulado.

Parámetros
* x: la posición horizontal del Stick.
* y: la posición vertical del Stick.

**Microsoft. PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**

Recupera o establece el nivel de batería del controlador simulado.  El valor debe ser mayor que 0,0 y menor o igual que 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft. PerceptionSimulation. ISimulatedEyes

Interfaz que describe los ojos del hombre simulado.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotation**

Recupera el giro de los ojos simulados. Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.

**Microsoft. PerceptionSimulation. ISimulatedEyes. Rotate (Microsoft. PerceptionSimulation. Rotation3)**

Gira los ojos simulados en relación con su rotación actual. Los radianes positivos giran en el sentido de las agujas del reloj al mirar por el eje.

Parámetros
* rotación: la cantidad que se va a girar.

**Microsoft. PerceptionSimulation. ISimulatedEyes. CalibrationState**

Recupera o establece el estado de calibrado de los ojos simulados.

**Microsoft. PerceptionSimulation. ISimulatedEyes. WorldPosition**

Recupere la posición del nodo con relación al mundo, en metros.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft. PerceptionSimulation. ISimulationRecording

Interfaz para interactuar con un solo registro cargado para la reproducción.

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

**Microsoft. PerceptionSimulation. ISimulationRecording. Datatypes**

Recupera la lista de tipos de datos de la grabación.

**Microsoft. PerceptionSimulation. ISimulationRecording. State**

Recupera el estado actual de la grabación.

**Microsoft. PerceptionSimulation. ISimulationRecording. Play**

Inicie la reproducción. Si se pausa la grabación, la reproducción se reanudará desde la ubicación en pausa; Si se detiene, la reproducción se iniciará al principio. Si ya se está reproduciendo, se omitirá esta llamada.

**Microsoft. PerceptionSimulation. ISimulationRecording. PAUSE**

Pausa la reproducción en su ubicación actual. Si se detiene la grabación, se omite la llamada.

**Microsoft. PerceptionSimulation. ISimulationRecording. Seek (System. UInt64)**

Busca la grabación en el tiempo especificado (en intervalos de 100 nanosegundos desde el principio) y se pausa en esa ubicación. Si el tiempo está más allá del final de la grabación, se pausa en el último fotograma.

Parámetros
* TICs: la hora a la que se va a buscar.

**Microsoft. PerceptionSimulation. ISimulationRecording. STOP**

Detiene la reproducción y restablece la posición al principio.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft. PerceptionSimulation. ISimulationRecordingCallback

Interfaz para recibir cambios de estado durante la reproducción.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft. PerceptionSimulation. ISimulationRecordingCallback. PlaybackStateChanged (Microsoft. PerceptionSimulation. PlaybackState)**

Se llama cuando el estado de reproducción de un ISimulationRecording ha cambiado.

Parámetros
* newState: el nuevo estado de la grabación.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft. PerceptionSimulation. PerceptionSimulationManager

Objeto raíz para crear objetos de simulación de percepción.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationManager (Microsoft. PerceptionSimulation. ISimulationStreamSink)**

Cree en el objeto para generar paquetes simulados y entregarlos al receptor proporcionado.

Parámetros
* receptor: el receptor que recibirá todos los paquetes generados.

Valor devuelto

Administrador creado.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. CreatePerceptionSimulationRecording (System. String)**

Cree un receptor que almacene todos los paquetes recibidos en un archivo en la ruta de acceso especificada.

Parámetros
* Ruta de acceso: la ruta de acceso del archivo que se va a crear.

Valor devuelto

Receptor creado.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory)**

Cargar una grabación del archivo especificado.

Parámetros
* Ruta de acceso: la ruta de acceso del archivo que se va a cargar.
* Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.

Valor devuelto

Grabación cargada.

**Microsoft. PerceptionSimulation. PerceptionSimulationManager. LoadPerceptionSimulationRecording (System. String, Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory, Microsoft. PerceptionSimulation. ISimulationRecordingCallback)**

Cargar una grabación del archivo especificado.

Parámetros
* Ruta de acceso: la ruta de acceso del archivo que se va a cargar.
* Factory: un generador que utiliza la grabación para crear un ISimulationStreamSink cuando sea necesario.
* callback: devolución de llamada que recibe actualizaciones que retrasan el estado de la grabación.

Valor devuelto

Grabación cargada.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft. PerceptionSimulation. StreamDataTypes

Describe los diferentes tipos de datos de secuencia.

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

**Microsoft. PerceptionSimulation. StreamDataTypes. None**

Un valor de centinela que se usa para indicar que no hay tipos de datos de flujo.

**Microsoft. PerceptionSimulation. StreamDataTypes. Head**

Secuencia de datos con respecto a la posición y orientación del encabezado.

**Microsoft. PerceptionSimulation. StreamDataTypes. handles**

Flujo de datos con respecto a la posición y los gestos de las manos.

**Microsoft. PerceptionSimulation. StreamDataTypes. SpatialMapping**

Flujo de datos con respecto a la asignación espacial del entorno.

**Microsoft. PerceptionSimulation. StreamDataTypes. Calibration**

Flujo de datos con respecto a la calibración del dispositivo. Los paquetes de calibración solo los acepta un sistema en modo remoto.

**Microsoft. PerceptionSimulation. StreamDataTypes. Environment**

Flujo de datos sobre el entorno del dispositivo.

**Microsoft. PerceptionSimulation. StreamDataTypes. All**

Un valor de centinela que se usa para indicar todos los tipos de datos grabados.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft. PerceptionSimulation. ISimulationStreamSink

Objeto que recibe paquetes de datos de una secuencia de simulación.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft. PerceptionSimulation. ISimulationStreamSink. OnPacketReceived (uint longitud, Byte [], paquete)**

Recibe un único paquete, que está escrito internamente y con control de versiones.

Parámetros
* longitud: la longitud del paquete.
* paquete: los datos del paquete.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory

Objeto que crea ISimulationStreamSink.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft. PerceptionSimulation. ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**

Crea una única instancia de ISimulationStreamSink.

Valor devuelto

Receptor creado.
