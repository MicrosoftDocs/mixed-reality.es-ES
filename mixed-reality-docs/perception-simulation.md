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
# <a name="perception-simulation"></a>Simulación de percepción

¿Desea crear una prueba automatizada de la aplicación? ¿Desea que las pruebas para ir más allá de las pruebas unitarias de nivel de componente y realmente ejercitar su aplicación-to-end? Simulación de percepción es lo está buscando. La biblioteca de simulación de percepción envía humanos falsa y datos de entrada del mundo a la aplicación para que pueda automatizar las pruebas. Por ejemplo, puede simular la entrada de un aspecto humano izquierda y derecha y, a continuación, realizar un gesto.

Simulación de percepción puede enviar entrada simulado así un HoloLens físico, el emulador de HoloLens o un equipo con el Portal de realidad mixta instalado. Percepción simulación omite los sensores en directo en un dispositivo de realidad mixta y envía simula la entrada para aplicaciones que se ejecutan en el dispositivo. Las aplicaciones reciben estos eventos de entrada falsos a través de las mismas API siempre usan y no se puede indicar la diferencia entre la ejecución con sensores reales frente a ejecutar con la simulación de percepción. Simulación de percepción es la misma tecnología que utiliza el emulador de HoloLens enviar la entrada simulado a la máquina Virtual de HoloLens.

Simulación empieza por crear un objeto IPerceptionSimulationManager. Desde ese objeto, puede emitir comandos para controlar las propiedades de un simulado "humano", incluida la posición principal, la posición de la mano y los gestos.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Configuración de un proyecto de Visual Studio para la simulación de percepción
1. [Instalar el emulador de HoloLens](install-the-tools.md) en el equipo de desarrollo. El emulador incluye las bibliotecas que se va a usar para la simulación de percepción.
2. Crear un nuevo Visual Studio C# proyecto de escritorio (un proyecto de consola funciona bien para empezar a trabajar).
3. Agregue los siguientes archivos binarios al proyecto como referencias (proyecto -> Agregar -> referencia...). Puede encontrarlos en **% ProgramFiles (x86) %\Microsoft XDE\10.0.11082.0** una. PerceptionSimulationManager.Interop.dll - Managed C# contenedor para la simulación de percepción.
    b. PerceptionSimulationRest.dll - Library para configurar un canal de comunicación de socket web al HoloLens o emulador.
    c. SimulationStream.Interop.dll - tipos compartidos para la simulación.
4. Agregue la implementación PerceptionSimulationManager.dll binarios al proyecto una. En primer lugar agregarlo al proyecto como un archivo binario (proyecto -> Agregar -> elemento existente...). Guárdelo como un vínculo para que no copiarlo a la carpeta de origen del proyecto. ![Agregar al proyecto como un vínculo PerceptionSimulationManager.dll](images/saveaslink.png) b. A continuación, asegúrese de que lo de la copia en la carpeta de salida en la compilación. Se trata en la hoja de propiedades para el archivo binario. ![Marcar PerceptionSimulationManager.dll para copiar en el directorio de salida](images/copyalways.png)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Creación de un objeto de administrador IPerceptionSimulation

Para controlar la simulación, deberá emitir las actualizaciones a los objetos recuperados de un objeto IPerceptionSimulationManager. El primer paso es obtener ese objeto y conectarlo a su emulador o dispositivo de destino. Puede obtener la dirección IP de su emulador, haga clic en el botón de Portal de dispositivos en el [barra de herramientas](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)

![Icono de dispositivo Portal abierta](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra el Windows Device Portal para el sistema operativo de HoloLens en el emulador.

En primer lugar, llamaremos a RestSimulationStreamSink.Create para obtener un objeto RestSimulationStreamSink. Este es el dispositivo de destino o el emulador que se controlan a través de una conexión http. Se pasa a los comandos y controla el [Windows Device Portal](using-the-windows-device-portal.md) que se ejecuta en el dispositivo o emulador. Los cuatro parámetros que deberá crear un objeto son:
* Uri de URI: dirección IP del dispositivo de destino (por ejemplo, "http://123.123.123.123")
* System.Net.NetworkCredential credenciales: nombre de usuario y contraseña para conectarse a la [Windows Device Portal](using-the-windows-device-portal.md) en el emulador o dispositivo de destino. Si va a conectar al emulador a través de su 168 local. *.* . * dirección en el mismo equipo, se aceptan las credenciales.
* normal: bool es True para una prioridad normal, false de prioridad baja. Por lo general desea establecerlo en *true* para escenarios de prueba.
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

Un valor de centinela utilizado para no indicar ningún gestos

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Un dedo presionada gesto

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Un gesto del dedo publicado

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

El gesto de inicio

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

El movimiento válido máximo

### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Describe el estado de una reproducción

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

La grabación está actualmente detenido y listo para su reproducción

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

Ya se está reproduciendo la grabación

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

Actualmente está en pausa la grabación

**Microsoft.PerceptionSimulation.PlaybackState.End**

La grabación ha llegado al final

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Describe un vector de 3 componentes, que se puede describir un punto o un vector en el espacio 3D

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

El componente X del vector

**Microsoft.PerceptionSimulation.Vector3.Y**

El componente Y del vector

**Microsoft.PerceptionSimulation.Vector3.Z**

Componente Z del vector

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Construir un nuevo Vector3

Parámetros
* x: el componente x del vector
* y - el componente y del vector
* z - el componente z del vector

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Describe un giro de 3 componentes

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

El componente de punto de rotación, abajo alrededor del eje X

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

El componente de rotación de la rotación, justo en el eje Y

**Microsoft.PerceptionSimulation.Rotation3.Roll**

El componente de rollo de rotación, justo en el eje Z

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Construir un nuevo Rotation3

Parámetros
* pitch: el componente de tono de la rotación
* guiñada: el componente de rotación de la rotación
* Resumen: el componente de lanzamiento de la rotación

### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Describe un frustum de visualización, como suele ser utilizado por una cámara

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

La distancia mínima que se encuentra en el frustum

**Microsoft.PerceptionSimulation.Frustum.Far**

La distancia máxima que se encuentra en el frustum

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

El campo de visión horizontal de frustum, en radianes (menos de PI)

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

La proporción del campo de visión horizontal a vertical campo de visión

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Raíz para generar los paquetes utilizados para controlar un dispositivo

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

Interfaz que describe la parte del dispositivo simulado que realiza el seguimiento de la cabeza de los humanos simulado

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

Recuperar la posición del nodo con respecto a la del mundo, en metros

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Recuperar y establecer la posición de la herramienta de seguimiento de la mano simulado, en relación con el centro de la cabeza.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Recuperar y establecer el tono hacia abajo de la herramienta de seguimiento de la mano simulado

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Recuperar y establecer si se omite el frustum del Rastreador de mano simulado. Cuando se omite, dos manos siempre están visibles. Cuando no pasa por alto (predeterminado) manos solamente están visibles cuando estén dentro del frustum del Rastreador de mano.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Recuperar y establecer las propiedades de frustum utilizadas para determinar si son visibles para el seguimiento de la mano simulado manos.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Interfaz de nivel superior para controlar a los humanos simulado

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

Recuperar y establecer el alto de los humanos simulado, en metros

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

Recuperar la parte izquierda de los humanos simulado

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

Recuperar la parte derecha de los humanos simulado

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Recuperar el encabezado de los humanos simulado

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Mover a los humanos simulado respecto a su posición actual, en metros

Parámetros
* traducción: la traducción que se mueven en relación con la posición actual

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Girar a los humanos simulado con respecto a su dirección actual, las agujas del reloj sobre el eje Y

Parámetros
* radianes - la cantidad que se va a girar alrededor del eje Y

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

Recuperar la posición del nodo con respecto a la del mundo, en metros

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
* traducción: la cantidad de traslación de la mano simulada

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Realizar un gesto de la mano simulada (solo se detectará el sistema si está habilitada la mano).

Parámetros
* gesto - el gesto para realizar

### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Interfaz que describe el encabezado de los humanos simulado

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

Recuperar la posición del nodo con respecto a la del mundo, en metros

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Recuperar la rotación de la cabeza simulada. Radianes giran a la derecha al buscar en el eje positivo.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Recuperar el diámetro del encabezado simulado. Este valor se utiliza para determinar el centro del encabezado (punto de giro).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Girar la cabeza simulada con respecto a su rotación actual. Radianes giran a la derecha al buscar en el eje positivo.

Parámetros
* rotación: la cantidad que se va a girar

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
* tics: el tiempo que se va a buscar

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Detiene la reproducción y restablece la posición al principio

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Interfaz para recibir los cambios de estado durante la reproducción

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Se llama cuando ha cambiado el estado de reproducción de un ISimulationRecording

Parámetros
* newState - el nuevo estado de la grabación

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Objeto raíz para crear objetos de simulación de percepción

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
* Sink - el receptor que recibirá todos genera paquetes

Valor devuelto

El administrador creado

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Crear un receptor que almacena los paquetes recibidos todo en un archivo en la ruta de acceso especificada.

Parámetros
* ruta de acceso: la ruta de acceso de archivo que se creará

Valor devuelto

El receptor creado

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Cargar una grabación desde el archivo especificado

Parámetros
* ruta de acceso: la ruta de acceso del archivo para cargar
* Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario

Valor devuelto

La grabación cargada

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Cargar una grabación desde el archivo especificado

Parámetros
* ruta de acceso: la ruta de acceso del archivo para cargar
* Factory - un generador utilizado por la grabación para crear un ISimulationStreamSink cuando sea necesario
* Una devolución de llamada que recibe de devolución de llamada - actualiza reclasificación de estado de la grabación

Valor devuelto

La grabación cargada

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Describe los diferentes tipos de datos de secuencia

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

Un valor de centinela utilizado para no indicar ningún tipo de datos de secuencia

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream de datos con respecto a la posición y la orientación de la cabeza

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Stream de datos con respecto a la posición y movimientos de manos

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Stream de datos con respecto a la asignación espacial del entorno

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Stream de datos con respecto a la calibración del dispositivo. Solo se aceptan los paquetes de calibración mediante un sistema en modo remoto.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Stream de datos relacionados con el entorno del dispositivo

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Un valor de centinela utilizado para indicar todos los tipos de datos registrados

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Un objeto que recibe los paquetes de datos de una secuencia de simulación

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

Recibe un paquete único, que es internamente con tipo y con control de versiones

Parámetros
* longitud: la longitud del paquete
* paquete - los datos del paquete

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Un objeto que crea ISimulationStreamSink

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Crea una instancia única de ISimulationStreamSink

Valor devuelto

El receptor creado
