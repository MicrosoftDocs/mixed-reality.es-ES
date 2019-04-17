---
title: Mediante el emulador de HoloLens
description: El emulador de HoloLens le permite probar aplicaciones de realidad mixta en su PC sin un HoloLens físico.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, emulador
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605578"
---
# <a name="using-the-hololens-emulator"></a>Mediante el emulador de HoloLens

El emulador de HoloLens permite probar aplicaciones holográficas en su PC sin un HoloLens físico y viene con el conjunto de herramientas de desarrollo de HoloLens. El emulador usa una máquina virtual de Hyper-V. Las entradas de usuarios y del entorno que normalmente se lean los sensores en el HoloLens en su lugar se simulan mediante el teclado, un mouse o un mando de Xbox. Las aplicaciones no es necesario modificar para ejecutarse en el emulador y no sabe que no se está ejecutando en un HoloLens real.

Si desea para desarrollar aplicaciones de Windows Mixed Reality envolventes (VR) auriculares o juegos para PC de escritorio, consulte el [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md), que le permite simular auriculares de escritorio en su lugar.

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="installing-the-hololens-emulator"></a>Instalar el emulador de HoloLens

Descargue el [HoloLens (gen 1) emulador y plantillas de proyecto holográfica](https://go.microsoft.com/fwlink/?linkid=2065980).

Puede encontrar las compilaciones anteriores del emulador de HoloLens en la [archive de emulador de HoloLens](hololens-emulator-archive.md) página.

### <a name="hololens-emulator-system-requirements"></a>Requisitos de sistema del emulador de HoloLens

El emulador de HoloLens se basa en Hyper-V y utiliza RemoteFx para gráficos acelerados de hardware. Para usar el emulador, asegúrese de que su PC cumple estos requisitos de hardware:
* 64-bit Windows 10 Pro, Enterprise o la educación 
    >[!NOTE]
    >Windows 10 Home edition no es compatible con Hyper-V o en el emulador de HoloLens
* CPU de 64 bits
* Uso de CPU con 4 núcleos (o varias CPU con un total de 4 núcleos)
* 8 GB de RAM o más
* En el BIOS, las características siguientes deben estar [admitir y tener habilitado](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * Virtualización asistida por hardware
   * Traducción de direcciones de segundo nivel (SLAT)
   * Prevención de ejecución de datos basada en hardware (DEP)
* Requisitos de la GPU (el emulador podría funcionar con una GPU no compatible, pero será notablemente más lenta)
   * DirectX 11.0 o versiones posterior
   * Controlador WDDM 1.2 o posterior

Si su sistema cumple los requisitos anteriores, **, asegúrese de que se ha habilitado la característica "Hyper-V" en el sistema** a través del Panel de Control -> Programas -> programas y características -> Activar las características de Windows o desactivar -> Asegúrese de que está seleccionado "Hyper-V" para que la instalación del emulador se realice correctamente.

### <a name="installation-troubleshooting"></a>Solución de problemas de instalación

Puede ver un error al instalar el emulador que necesite *"Visual Studio 2015 Update 1 y UWP tools versión 1.2"*. Existen tres posibles causas de este error:
* No tiene una versión suficientemente reciente de Visual Studio (Visual Studio 2017 o Visual Studio 2015 Update 1 o posterior). Para corregir este problema, instale la versión más reciente de Visual Studio.
* Tiene una versión suficientemente reciente de Visual Studio, pero no tiene instaladas las herramientas de plataforma Universal de Windows (UWP). Se trata de una característica opcional de Visual Studio.

También puede ver un error al instalar el emulador en una no-PRO, Enterprise y Education SKU de Windows o si no tiene características de Hyper-V habilitado.
* Lea la [requisitos del sistema](#hololens-emulator-system-requirements) sección anterior para un conjunto completo de requisitos.
* También asegúrese de que se ha habilitado la característica Hyper-V en el sistema.

## <a name="deploying-apps-to-the-hololens-emulator"></a>Implementación de aplicaciones en el emulador de HoloLens

1. Cargue la solución de aplicación en Visual Studio 2015.
    >[!NOTE]
    >Al usar Unity, compile el proyecto de Unity y, a continuación, cargue la solución generada en Visual Studio como de costumbre.
2. Asegúrese de que la plataforma se establece en **x86**.
3. Seleccione el **emulador de HoloLens** como dispositivo de destino para la depuración.
4. Vaya a **Depurar > Iniciar depuración** o presione **F5** para iniciar el emulador e implementar la aplicación para la depuración.

El emulador puede tardar un minuto o más para que arranque cuando se inicia por primera vez. Se recomienda que mantenga el emulador abierto durante la sesión de depuración para poder implementar rápidamente las aplicaciones en el emulador en ejecución.

## <a name="basic-emulator-input"></a>Entrada básico del emulador

Control del emulador es muy similar a muchos juegos de vídeo 3D comunes. Hay opciones de entrada mediante el teclado, mouse o mando de Xbox. Controlar el emulador dirigiendo las acciones de un usuario simulado wearing un HoloLens. Las acciones de mover que usuario simulado alrededor y aplicaciones que se ejecutan en el emulador de responden como lo harían en un dispositivo real.
* **Recorrer hacia delante, izquierda y derecha** -usar el W, A, S y D teclas del teclado o el stick izquierdo en un controlador de Xbox.
* **Buscar hacia arriba, abajo, izquierda y a la derecha** -hacer clic y arrastrar el mouse, utilice las teclas de flecha del teclado o el stick derecho en un controlador de Xbox.
* **Gesto de pulsar en el aire** : haga clic en el mouse, presione la tecla ENTRAR del teclado o usar el botón en un controlador de Xbox.
* **Gesto de floración** : presione la tecla de Windows o la tecla F2 del teclado, o presione el botón B en un controlador de Xbox.
* **Entregar el movimiento de desplazamiento** : mantenga presionada la tecla Alt, mantenga presionado el botón secundario del mouse y arrastre el mouse arriba / abajo, o en un controlador Xbox presionada el desencadenador correcto y un botón y Subir o bajar el stick derecho.

## <a name="anatomy-of-the-hololens-emulator"></a>Anatomía del emulador de HoloLens

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

![Ficha de "Salas" emulador de HoloLens](images/emulator-room-500px.png)

Salas simuladas son útiles para probar la aplicación en varios entornos. Existen varias habitaciones se suministran con el emulador y una vez que instale la emulación, encontrará en % ProgramFiles(x86) %\Program archivos (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms. Todas estas salas se capturaron en entornos reales mediante un HoloLens:
* **DefaultRoom.xef** -una pequeña sala de estar con un Televisor, mesa de café y dos sofás. Carga de forma predeterminada cuando se inicia el emulador.
* **Bedroom1.xef** -un dormitorio pequeño con un departamento de soporte técnico.
* **Bedroom2.xef** -un dormitorio cuenta con una cama de tamaño de la Reina, Aparador, nightstands y sin cita armario.
* **GreatRoom.xef** -una sala excelente gran espacio abierto con sala de estar, comedor y cocina.
* **LivingRoom.xef** : un salón con un hogar, el sofá, armchairs y una tabla de café con un jarrón.

También puede grabar sus propios salas para usar en el emulador con la página de simulación de la [Windows Device Portal](using-the-windows-device-portal.md) en su HoloLens.

En el emulador, solo verán hologramas que representa y no verá la sala detrás del hologramas simulada. Esto es en contraste con el HoloLens real, donde puede ver tanto fusionado. Si desea ver la sala simulada en el emulador de HoloLens, deberá actualizar la aplicación para representar la malla de asignación espacial en la escena.

### <a name="account-tab"></a>ficha Cuenta

La pestaña cuenta le permite configurar el emulador para iniciar sesión con una Account de Microsoft. Esto es útil para probar la API que requieran que el usuario no ha iniciado sesión con una cuenta. Después de activar la casilla de esta página, lanzamientos subsiguientes del emulador le preguntará al inicio de sesión, tal como haría con un usuario de la primera vez que se inicia el HoloLens.

## <a name="see-also"></a>Vea también
* [Entrada de emulador de HoloLens y el simulador de realidad mixta avanzados](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Historial de software del emulador de HoloLens](hololens-emulator-archive.md)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
