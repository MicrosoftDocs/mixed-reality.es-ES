---
title: Mediante el emulador de HoloLens
description: El emulador de HoloLens le permite probar aplicaciones de realidad mixta en su PC sin un HoloLens físico.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, emulador
ms.openlocfilehash: 0dfca73e6c8e1809e1bea3df6ca344b3de0698d5
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730917"
---
# <a name="using-the-hololens-emulator"></a>Mediante el emulador de HoloLens

El emulador de HoloLens permite probar aplicaciones holográficas en su PC sin un HoloLens físico y viene con el conjunto de herramientas de desarrollo de HoloLens. El emulador usa una máquina virtual de Hyper-V. Las entradas de usuarios y del entorno que normalmente se lean los sensores en el HoloLens en su lugar se simulan mediante el teclado, un mouse o un mando de Xbox. Las aplicaciones no es necesario modificar para ejecutarse en el emulador y no sabe que no se está ejecutando en un HoloLens real.

Si desea para desarrollar aplicaciones de Windows Mixed Reality envolventes (VR) auriculares o juegos para PC de escritorio, consulte el [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), que le permite simular auriculares de escritorio en su lugar.


## <a name="installing-the-hololens-emulator"></a>Instalar el emulador de HoloLens
Descargue el emulador de HoloLens y plantillas de proyecto holográfica.

Versiones: 
* [Emulador de HoloLens 2 y plantillas de proyecto holográfica](https://go.microsoft.com/fwlink/?linkid=2087187).
* [Emulador de HoloLens (Gen 1) y las plantillas de proyecto holográfica](https://go.microsoft.com/fwlink/?linkid=2065980).

Puede encontrar las compilaciones anteriores del emulador de HoloLens en la [archive de emulador de HoloLens](hololens-emulator-archive.md) página.

### <a name="hololens-emulator-system-requirements"></a>Requisitos de sistema del emulador de HoloLens

El emulador de HoloLens usa Hyper-V con RemoteFx (emulador de Gen 1) o GPU-PV (emulador de HoloLens 2) para el hardware de gráficos acelerados. Para usar el emulador, asegúrese de que su PC cumple estos requisitos de hardware:
* 64-bit Windows 10 Pro, Enterprise o la educación 
    >[!NOTE]
    >Windows 10 Home edition no es compatible con Hyper-V o en el emulador de HoloLens.  
    >El emulador de HoloLens 2 requiere Windows 10 de octubre de 2018 update o posterior.
* CPU de 64 bits
* Uso de CPU con 4 núcleos (o varias CPU con un total de 4 núcleos)
* 8 GB de RAM o más
* En el BIOS, las características siguientes deben estar [admitir y tener habilitado](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Virtualización asistida por hardware
   * Traducción de direcciones de segundo nivel (SLAT)
   * Prevención de ejecución de datos basada en hardware (DEP)
* Requisitos de la GPU
   * DirectX 11.0 o versiones posterior
   * Controlador de gráficos WDDM 1.2 o posterior (gen. 1)
   * Controlador de gráficos WDDM 2.5 (emulador de HoloLens 2)
   * El emulador podría funcionar con una GPU no compatible, pero será notablemente más lento

Si su sistema cumple los requisitos anteriores, **, asegúrese de que se ha habilitado la característica "Hyper-V" en el sistema** a través del Panel de Control -> Programas -> programas y características -> Activar las características de Windows o desactivar -> Asegúrese de que está seleccionado "Hyper-V" para que la instalación del emulador se realice correctamente.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Implementación de aplicaciones en el emulador de HoloLens

1. Cargue la solución de aplicación en Visual Studio.
    >[!NOTE]
    >Al usar Unity, compile el proyecto de Unity y, a continuación, cargue la solución generada en Visual Studio como de costumbre.
2. Para el emulador de HoloLens (Gen 1), asegúrese de que la plataforma se establece en **x86**. Para el emulador de HoloLens 2 asegurarse de la plataforma se establece en **x86** o **x64**.
3. Seleccione el elemento **emulador de HoloLens** versión como dispositivo de destino para la depuración.
4. Vaya a **Depurar > Iniciar depuración** o presione **F5** para iniciar el emulador e implementar la aplicación para la depuración.

El emulador puede tardar un minuto o más para que arranque cuando se inicia por primera vez. Se recomienda que mantenga el emulador abierto durante la sesión de depuración para poder implementar rápidamente las aplicaciones en el emulador en ejecución.

## <a name="basic-emulator-input"></a>Entrada básico del emulador

Control del emulador es muy similar a muchos juegos de vídeo 3D comunes. Hay opciones de entrada mediante el teclado, mouse o mando de Xbox. Controlar el emulador dirigiendo las acciones de un usuario simulado wearing un HoloLens. Las acciones de mover que usuario simulado alrededor y aplicaciones que se ejecutan en el emulador de responden como lo harían en un dispositivo real.

El cursor en HoloLens (Gen 1) sigue el movimiento y la rotación.  En el emulador de HoloLens 2, el cursor sigue el movimiento y la orientación.

* **Recorrer hacia delante, izquierda y derecha** -usar el W, A, S y D teclas del teclado o el stick izquierdo en un controlador de Xbox.
* **Buscar hacia arriba, abajo, izquierda y a la derecha** -hacer clic y arrastrar el mouse, utilice las teclas de flecha del teclado o el stick derecho en un controlador de Xbox.
* **Gesto de pulsar en el aire** : haga clic en el mouse, presione la tecla ENTRAR del teclado o usar el botón en un controlador de Xbox.
* **Gesto de Bloom/sistema** : presione la tecla de Windows o la tecla F2 del teclado, o presione el botón B en un controlador de Xbox.
* **Entregar el movimiento de desplazamiento** : mantenga presionada la tecla Alt, mantenga presionado el botón secundario del mouse y arrastre el mouse arriba / abajo, o en un controlador Xbox presionada el desencadenador correcto y un botón y Subir o bajar el stick derecho.
* **Entregar el movimiento y la orientación** (sólo 2 HoloLens emulador) - mantenga presionada la tecla Alt y arrastre el mouse arriba, abajo, izquierdo y derecho mover la mano o usar las teclas de dirección y Q / E de giro e inclinación de la mano.  Para un controlador Xbox, mantenga lo paragolpes izquierdo o derecho y utilice la tecla de navegación izquierda para mover la mano izquierda, derecha, hacia delante y atrás, la tecla de navegación derecha para girarlo y activo / inactivo en Dpad para subir o bajar la mano.

## <a name="anatomy-of-the-hololens-2-emulator"></a>Anatomía del emulador de HoloLens 2 

### <a name="main-window"></a>Ventana principal

![Ventana principal del emulador de HoloLens 2](images/emulator2-900px.png)

### <a name="toolbar"></a>Barra de herramientas

A la derecha de la ventana principal, verá la barra de herramientas del emulador. La barra de herramientas contiene los siguientes botones:
* ![Icono Cerrar](images/emulator-close.png) **cerrar**: Cierra el emulador.
* ![Icono minimizar](images/emulator-minimize.png) **minimizar**: Minimiza la ventana del emulador.
* ![Simulation_icon](images/emulator-simulation-panel.png) **Panel de Control de simulación**: Mostrar u ocultar el [panel de Control de simulación](#simulation-control-panel) para configurar y controlar [como entrada para el emulador](#basic-emulator-input).
* ![Ajustar al icono de pantalla](images/emulator-fit.png) **ajustar a la pantalla**: Ajusta el emulador de la pantalla.
* ![Icono de zoom](images/emulator-zoom.png) **Zoom**: Acelerar el emulador grandes y pequeños.
* ![Icono de Ayuda](images/emulator-help.png) **ayuda**: Abra la Ayuda del emulador.
* ![Icono de portal de dispositivo abierto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra el Windows Device Portal para el sistema operativo de HoloLens en el emulador.
* ![Icono herramientas](images/emulator-tools.png) **herramientas**: Abra el **herramientas adicionales** panel.

### <a name="simulation-control-panel"></a>Panel de Control de simulación

El Panel de Control de la simulación permite ver la posición actual y la orientación de los dispositivos simulados de entrada humanos y simulados.  También permite configurar ambos entrada simulado, como se muestra u oculta uno o dos manos y los dispositivos usados para controlar la entrada simulado, como el teclado, mouse y controlador para juegos de su PC.

![Panel de control de simulación](images/emulator-simulation-control-panel.png)

* Para mostrar u ocultar el panel de simulación, presione F7 en el teclado o haga clic en el botón de barra de herramientas.
* Mantenga el mouse sobre un control o campo para mostrar información sobre herramientas que contiene los controles del teclado, mouse y controlador de juegos para él.
* Para mostrar u ocultar una mano, activar o desactivar el modificador adecuado en la parte izquierda o derecha.
* Para controlar la mano, utilice las teclas Alt izquierdas o derecha en el teclado o lo paragolpes izquierdo o derecho en el controlador para juegos.
* Para indicar todas las entradas a manos de uno o ambos, haga clic en el botón de alfiler en el conmutador de alternancia.  Esto es el equivalente de manteniendo presionada la tecla Alt para la mano.
* Para controlar la dirección de mirada ojos, haga clic en el PIN en la sección "Ojos".  Esto es el equivalente de manteniendo presionada la tecla 'Y' en el teclado.
* Para cargar una sala de grabación, haga clic en el botón "Cargar" en la sección "Grabación".  Consulte [simulated salas](#simulated-rooms) para obtener más información.
* Para ajustar la velocidad que los dispositivos simulados de entrada humanos o simulados mover o girar en respuesta al teclado, mouse o controlador para juegos de entrada, haga clic en el icono de engranaje junto a "Configuración de entrada" y ajustar los controles deslizantes.
* De forma predeterminada, entrada de teclado controla la entrada humana y simulada simulada.  Para que la entrada de teclado de su PC enviada a través a la HoloLens, desactive la opción "Utilizar el teclado para la simulación".  F4 es la tecla de método abreviado para esta configuración.
* Si ya está visible el panel de simulación, presione F8 se moverá el foco de teclado a él.
* Para desacoplar el panel de simulación desde la ventana del emulador, presione F9 en el teclado o haga clic en el botón situado en la parte inferior del panel.  Cierra la ventana o si vuelve a presionar F9 devolverá la ventana en el emulador.
* Se puede iniciar el panel de control de simulación como una aplicación independiente, lo que le permite conectarse y controlar el emulador de HoloLens 2, un dispositivo HoloLens 2 o simulación Windows Mixed Reality ejecutando PerceptionSimulationInput.exe desde % ProgramFiles(x86) % \ Windows Kits\10\Microsoft XDE\10.0.18362.0\.

### <a name="account-tab"></a>ficha Cuenta

La pestaña cuenta le permite configurar el emulador para iniciar sesión con una Account de Microsoft. Esto es útil para probar las API que requieren que el usuario que inició sesión con una cuenta.  Si activa o desactiva esta opción será necesario completamente cerrar y reiniciar el emulador de HoloLens para la configuración surta efecto.  Si esta opción está habilitada, lanzamientos subsiguientes del emulador le pedirá que inicie sesión, al igual que un usuario sería la primera vez que se inicia el HoloLens.  Para escribir rápidamente las credenciales con el teclado de su PC, desactive la opción "Utilizar el teclado para la simulación" en el Panel de Control de simulación o presione F4 en su teclado para activar o desactivar la configuración de teclado.

### <a name="optional-settings-tab"></a>Ficha Configuración opcional

La ficha Configuración opcional mostrará un control para habilitar o deshabilitar gráficos acelerados de hardware.  Gráficos acelerados de hardware se usará de forma predeterminada, si es compatible con el controlador de adaptador de gráficos de su PC.  Si el controlador de su adaptador de gráficos no es compatible con GPU PV, esta opción no estará visible.

### <a name="diagnostics-tab"></a>Ficha diagnóstico

La ficha diagnóstico muestra la dirección IP del emulador en forma de un vínculo a Windows Device Portal junto con el estado de la GPU virtual.


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>Anatomía de la HoloLens (Gen 1) emulador

### <a name="main-window"></a>Ventana principal

Cuando se inicia el emulador, verá una ventana que muestra el sistema operativo de HoloLens.

![Ventana principal del emulador de HoloLens](images/emulator-890px.png)

### <a name="toolbar"></a>Barra de herramientas

A la derecha de la ventana principal, verá la barra de herramientas del emulador. La barra de herramientas contiene los siguientes botones:
* ![Icono Cerrar](images/emulator-close.png) **cerrar**: Cierra el emulador.
* ![Icono minimizar](images/emulator-minimize.png) **minimizar**: Minimiza la ventana del emulador.
* ![Icono de entrada humana](images/emulator-control.png) **entrada humana**: Mouse y teclado se utilizan para simular humano [como entrada para el emulador](#basic-emulator-input).
* ![Icono de entrada de teclado y mouse](images/emulator-input.png) **teclado y Mouse entrada**: Teclado y mouse de entrada se pasan directamente al sistema operativo HoloLens como eventos de teclado y mouse que si se conectara un mouse y teclado con Bluetooth.
* ![Ajustar al icono de pantalla](images/emulator-fit.png) **ajustar a la pantalla**: Ajusta el emulador de la pantalla.
* ![Icono de zoom](images/emulator-zoom.png) **Zoom**: Acelerar el emulador grandes y pequeños.
* ![Icono de Ayuda](images/emulator-help.png) **ayuda**: Abra la Ayuda del emulador.
* ![Icono de portal de dispositivo abierto](images/emulator-deviceportal.png) **abrir Portal de dispositivo**: Abra el Windows Device Portal para el sistema operativo de HoloLens en el emulador.
* ![Icono herramientas](images/emulator-tools.png) **herramientas**: Abra el **herramientas adicionales** panel.

### <a name="simulation-tab"></a>Pestaña de simulación

La pestaña predeterminada dentro de la **herramientas adicionales** panel es el **simulación** ficha.

![Panel de "Herramientas adicionales" emulador de HoloLens](images/emulator-simulation-500px.png)

La pestaña de simulación muestra el estado actual de los sensores simulados que se usa para controlar el sistema operativo de HoloLens en el emulador. Al mantener el mouse sobre cualquier valor en la pestaña de simulación le proporcionará una información sobre herramientas que describe cómo controlar ese valor.

### <a name="room-tab"></a>Sala

El emulador simula la entrada del mundo en el formulario de la malla de asignación espacial desde simulados "habitaciones". Esta pestaña le permite elegir qué espacio para cargar en lugar de la sala de forma predeterminada.

![Pestaña 'Locales' de emulador de HoloLens](images/emulator-room-500px.png)

Consulte [simulated salas](#simulated-rooms) para obtener más información.

### <a name="account-tab"></a>ficha Cuenta

La pestaña cuenta le permite configurar el emulador para iniciar sesión con una Account de Microsoft. Esto es útil para probar la API que requieran que el usuario no ha iniciado sesión con una cuenta. Después de activar la casilla de esta página, lanzamientos subsiguientes del emulador le preguntará al inicio de sesión, tal como haría con un usuario de la primera vez que se inicia el HoloLens.

## <a name="simulated-rooms"></a>Salas simuladas

Salas simuladas son útiles para probar la aplicación en varios entornos. Existen varias habitaciones se suministran con el emulador y una vez que instale la emulación, encontrará en % ProgramFiles (x86) %\Windows Kits\10\Microsoft XDE\\\Plugins\Rooms (versión). Todas estas salas se capturaron en entornos reales mediante un HoloLens:
* **DefaultRoom.xef** -una pequeña sala de estar con un Televisor, mesa de café y dos sofás. Carga de forma predeterminada cuando se inicia el emulador.
* **Bedroom1.xef** -un dormitorio pequeño con un departamento de soporte técnico.
* **Bedroom2.xef** -un dormitorio cuenta con una cama de tamaño de la Reina, Aparador, nightstands y sin cita armario.
* **GreatRoom.xef** -una sala excelente gran espacio abierto con sala de estar, comedor y cocina.
* **LivingRoom.xef** : un salón con un hogar, el sofá, armchairs y una tabla de café con un jarrón.

También puede grabar sus propios salas para usar en el emulador con la página de simulación de la [Windows Device Portal](using-the-windows-device-portal.md) en su HoloLens (Gen 1).

En el emulador, solo verán hologramas que representa y no verá la sala detrás del hologramas simulada. Esto es en contraste con el HoloLens real, donde puede ver tanto fusionado. Si desea ver la sala simulada en el emulador de HoloLens, deberá actualizar la aplicación para representar la malla de asignación espacial en la escena.

## <a name="troubleshooting"></a>Solución de problemas

Puede ver un error al instalar el emulador que necesite *"Visual Studio 2015 Update 1 y UWP tools versión 1.2"*. Existen tres posibles causas de este error:
* No tiene una versión suficientemente reciente de Visual Studio (2019 de Visual Studio, Visual Studio 2017 o Visual Studio 2015 Update 1 o posterior). Para corregir este problema, instale la versión más reciente de Visual Studio.
* Tiene una versión suficientemente reciente de Visual Studio, pero no tiene instaladas las herramientas de plataforma Universal de Windows (UWP). Se trata de una característica opcional de Visual Studio.

También puede ver un error al instalar el emulador en una no-Pro, Enterprise y Education SKU de Windows o si no tiene características de Hyper-V habilitado.
* Lea la [requisitos del sistema](#hololens-emulator-system-requirements) sección anterior para un conjunto completo de requisitos.
* También asegúrese de que se ha habilitado la característica Hyper-V en el sistema.

Si la instalación se completa correctamente, pero no ve el emulador de HoloLens como una opción para la implementación y depuración, compruebe lo siguiente:
* La configuración del proyecto de Visual Studio se establece en x86 (Gen 1 º de HoloLens) o x86 o x64 (emulador de HoloLens 2).
* Si usa Visual Studio de 2019, el conjunto de herramientas de plataforma en la configuración del proyecto se establece en v142.

Si la instalación se completa correctamente, pero Visual Studio muestra un error al intentar iniciar el emulador de HoloLens, pruebe lo siguiente:
* Ejecute Visual Studio como administrador
* Si solo tiene Visual Studio de 2019 instalado, compruebe que el valor del registro "KitsRoot10" en HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed raíces apunta a la carpeta de archivos de programa de 32 bits (por ejemplo, "C:\Program Files (x86) \Windows Kits \10 ").  Si no es así, desinstale el emulador de HoloLens, cambie el valor del registro a la carpeta de archivos de programa de 32 bits y vuelva a instalar el emulador de HoloLens.  Este problema se soluciona en Visual Studio 2019 16.0.3.

Si el emulador muestra un cuadro de diálogo de error de "Codificación de bytes no válida" en el inicio:
* Eliminar todos los archivos de %localappdata%\Microsoft\XDE\HCS e inténtelo de nuevo.

Si está vacía la lista de destino de depuración en Visual Studio (por ejemplo, "Start" es la única opción) y ha seguido todos los pasos de solución de problemas anteriores:
* Elimine la carpeta 'ConfigurationCache' en %localappdata%\Microsoft\VisualStudio\\<*Id. de instalación*> \CoreCon e inténtelo de nuevo.

Si el sistema se bloquea cuando se inicia el emulador, deshabilite la aceleración de hardware para gráficos del emulador.
* Cree un valor DWORD del registro denominado "DisableGPU" en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 y establezca su valor en 1.

## <a name="see-also"></a>Vea también
* [Introducción de datos avanzada en el emulador de HoloLens y el simulador de realidad mixta](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Historial de software de emulador de HoloLens](hololens-emulator-archive.md)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
