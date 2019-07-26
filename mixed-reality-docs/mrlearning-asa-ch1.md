---
title: MR Learning ASA Module Azure Spatial delimitador de HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 391e797ad9cc8933b057366ab47a3f453c68723e
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485773"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introducción a los delimitadores espaciales de Azure

Este es el segundo módulo de los tutoriales de HoloLens 2. Antes de empezar, asegúrese de que se hayan completado todos los [requisitos previos](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) . Si aún no ha completado el primer [módulo base](mrlearning-base.md) , se recomienda que complete primero ese módulo. Si va a comenzar desde un nuevo proyecto de Unity, siga los pasos de creación del nuevo proyecto en el [módulo base](mrlearning-base.md). 

## <a name="objectives"></a>Objetivos

* Conozca los aspectos básicos del desarrollo con los anclajes espaciales de Azure con HoloLens 2

* Crear, cargar y descargar anclajes espaciales

## <a name="instructions"></a>Instrucciones

### <a name="downloading-and-importing-assets"></a>Descarga e importación de recursos
Antes de comenzar, descargue e importe los siguientes recursos:

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Paquete de recursos del módulo base MR](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)

[Módulo de recursos del módulo ASA](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)

[Kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)

> Nota: Consulte el paso 5 para obtener instrucciones específicas sobre cómo importar los anclajes espaciales de Azure, el paso 6 para obtener instrucciones específicas sobre el módulo de recursos del módulo base MR y los pasos del 3 al 4 para obtener instrucciones específicas sobre el kit de herramientas de la realidad mixta (MRKT).

1. Cree una nueva escena en el proyecto. Haga clic con el botón derecho en la carpeta de la escena, haga clic en crear y luego en escena. Asigne a la nueva escena el nombre ASALearningmodule.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Haga doble clic en ASALearningmodule para ver que aparecen algunos elementos predefinidos junto con la nueva escena. 
3. Configure la escena para el desarrollo de realidad mixta. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: Verá un mensaje emergente que indica que debe elegir un archivo para el kit de herramientas de realidad mixta. Al hacer clic en aceptar, aparecerá el paso 4.

4. Al elegir un archivo para MRTK, seleccione, DefaultMixedRealityToolkitConfigurationProfile.

> Nota: Si tiene su propio perfil de configuración, no dude en usarlo en su lugar.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Ahora la escena está configurada para la realidad mixta. Asegúrese de guardar la escena (haga esto con control/comando + S o haga clic en archivo y, a continuación, haga clic en guardar). 

5. Importe los delimitadores espaciales de [Azure](https://github.com/azure/azure-spatial-anchors-samples/releases). Para usar delimitadores espaciales, debe importar este recurso. Haga clic en el vínculo anterior y haga clic con el botón derecho en AzureSpatialAnchors. unitypackage Tools. Haga clic en Guardar destino como y guárdelo en el equipo. 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

Una vez que se haya guardado, vuelva a Unity, haga clic en activos y luego en importar paquete. A continuación, haga clic en paquete personalizado... Se abrirán los archivos del equipo. Cuando lo haga, busque el lugar en el que guardó el paquete de anclajes espaciales de Azure y selecciónelo. A continuación, haga clic en abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Aparece una ventana emergente, providingg una lista de herramientas y valores de configuración, y preguntándole qué desea importar. Seleccione ***todas*** las opciones disponibles y, a continuación, haga clic en importar.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Nota: Sea paciente, tardará unos minutos en realizar la importación. 

6. Importe [Mr paquete de recursos del módulo https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) base] siguiente. Al igual que el paso 5, haga clic en el vínculo anterior. A continuación, haga clic con el botón secundario en BasemoduleAssetsV1 1. unitypackag y haga clic en Guardar destino como y guárdelo en el equipo.

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> Sugerencia: Guarde todos estos recursos en la misma carpeta para que sean más fáciles de encontrar y de tener acceso a. Mantiene todo bien y organizado.

Al igual que el paso 5, vuelva a Unity, haga clic en activos y mantenga el mouse sobre el paquete de importación. Haga clic en paquete personalizado... Los archivos del equipo volverán a aparecer. Vaya a la ubicación en la que almacenó el módulo de recursos del módulo base. y selecciónelo. Haga clic en Abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Nota: Es posible que se necesiten más recursos más adelante en este módulo. Siga estos pasos para importar los recursos mencionados a partir de este punto. 

7. Importe el [paquete de módulo de asa](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) con el mismo enfoque que la importación de los paquetes anteriores.

### <a name="configuring-your-scene"></a>Configuración de la escena

En esta sección, agregaremos Prefabs y scripts a la escena para crear una serie de botones que muestran los aspectos básicos de cómo se comportan los delimitadores locales y los delimitadores espaciales de Azure en una aplicación.

8. En la pestaña proyecto, debajo de la carpeta activos, haga clic en ASAmoduleAssets. Una vez seleccionado, verá dos Prefabs: ButtonParent y ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Arrastre ambos Prefabs a la escena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. Haga doble clic en el delimitador primario para seleccionarlo. Es posible que necesite ajustar la vista para ver toda la escena. Ajuste la escena según sea necesario.

Familiarícese con el recurso prefabricado de ParentAnchor. Actualmente, el objeto de juego denominado, ParentAnchor, es un cubo de color con fines de demostración. Finalmente, se oculta el cubo y se coloca el contenido como un elemento secundario de ParentAnchor. Este recurso prefabricado incluye el script AzureSpatialAnchorsDemoWrapper.cs (incluido con el SDK de ASA) y el script ASAmoduleScript.cs, incluido como parte de este módulo en el objeto ParentAnchor. 

11. Configurar botones. En ButtonParent recurso prefabricado, observe varios botones con etiqueta. Estos botones se crean a partir del Prefabs de PressableButton de MRTK. Obtenga más información sobre cómo crear botones que se pueda presionar desde el [módulo base](mrlearning-base-ch2.md). Para cada botón, agregue un evento que se desencadenará cuando el usuario presione o seleccione el botón según la lista siguiente. 

- En el caso del botón denominado, StartAzureSession, cree un nuevo evento bajo el desencadenador de eventos presionado de botón, así como el desencadenador de evento on click. Arrastre el objeto ParentAnchor al campo vacío y asigne el método StartAzureSession () desde el componente ASAmoduleScript del objeto ParentAnchor.

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- En el nombre del botón, StopAzureSession, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método StopAzureSession () desde el componente ASAmoduleScript del objeto ParentAnchor.

- En el caso del botón denominado, CreateAnchor, cree un nuevo evento bajo el desencadenador de eventos presionado de botón, así como el desencadenador de evento on click. Arrastre el objeto ParentAnchor al campo vacío y asigne el método CreateAzureAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.

- En el caso del botón denominado, empiece a buscar delimitadores, cree un nuevo evento en el desencadenador de evento Button Presse, así como el desencadenador de evento on click. Arrastre el objeto ParentAnchor al campo vacío y asigne el método FindAzureAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.

- En el caso del botón denominado, DeleteAzureAnchor, cree un nuevo evento bajo el desencadenador de eventos presionado de botón, así como el desencadenador de evento on click. Arrastre el objeto ParentAnchor al campo vacío y asigne el método DeleteAzureAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.

- En el caso del botón denominado, elimine el delimitador local, cree un nuevo evento en el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método RemoveLocalAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.

### <a name="build-and-demonstrate-base-application"></a>Compilar y demostrar la aplicación base

Ahora que la escena está configurada para mostrar los aspectos básicos de los anclajes espaciales de Azure, crearemos y mostraremos el comportamiento básico de los delimitadores espaciales de Azure. 

1. Si has cerrado la ventana Build Settings (Configuración de compilación) de las secciones anteriores, abre de nuevo la ventana de configuración de compilación en File>Build Settings (Archivo>Configuración de compilación).
![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Asegúrese de que la escena que desea probar está en la lista de escenas de la compilación haciendo clic en el botón Agregar escenas abiertas.

3. Presiona el botón Build (Compilar) para comenzar el proceso de compilación.
![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se creó una carpeta con el nombre app que contiene la aplicación. Haga clic en Seleccionar carpeta para empezar a compilar en la carpeta que acaba de crear. Una vez completada la compilación, puede cerrar la ventana de configuración de compilación en Unity. 
![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > Nota: Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Si ves un error como "Error: CS0246 = no se encontró el escriba o el nombre de espacio de nombres "XX" (¿falta una directiva using o una referencia de ensamblado?). Es posible que tenga que instalar el [SDK de Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haga doble clic en la solución "MixedRealityBase. sln" o en el nombre correspondiente. Si ha usado un nombre alternativo para el proyecto para abrir el archivo de solución en Visual Studio.

  > Nota: Asegúrese de abrir la carpeta recién creada (es decir, la carpeta de la aplicación, si sigue las convenciones de nomenclatura de los pasos anteriores porque habrá un archivo. sln con el mismo nombre fuera de esa carpeta que no debe confundirse con el archivo. sln dentro de la carpeta de compilación. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> Nota: Si Visual Studio le pide que instale nuevos componentes, dedique un momento a asegurarse de que todos los componentes necesarios se instalan como específicos en [la página "instalar las herramientas"](install-the-tools.md) . 

6. Conecta HoloLens 2 a tu equipo con el cable USB. Aunque estas instrucciones de la lección suponen que va a implementar una prueba con un dispositivo HoloLens 2, también puede optar por implementarla en el emulador de [hololens 2](using-the-hololens-emulator.md) o elegir crear un [paquete de aplicación para la instalación de prueba](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) .

7. Antes de compilar en el dispositivo, comprueba que el dispositivo está en modo de desarrollador. Si es la primera vez que estás realizando una implementación en HoloLens 2, Visual Studio puede pedirte que emparejes HoloLens 2 con un PIN. Siga [estas instrucciones](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) si necesita habilitar el modo de desarrollador o emparejar con Visual Studio.

8. Configure Visual Studio para compilar en HoloLens 2 seleccionando la configuración de lanzamiento y la arquitectura de RM.
![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. El paso final consiste en compilar en el dispositivo seleccionando Depurar > iniciar sin depurar. Al seleccionar iniciar sin depurar, la aplicación se inicia inmediatamente en el dispositivo tras una compilación correcta ithout información de depuración que aparece en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación. También puede seleccionar compilar > implementar solución para implementar en el dispositivo sin que la aplicación se inicie automáticamente.
![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
   
10. Sigue las instrucciones. Cuando la aplicación se esté ejecutando en el dispositivo, siga las instrucciones que aparecen en pantalla. Presione los botones de la escena correspondientes a los pasos siguientes.

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Inicie la sesión de delimitadores espaciales.
    
    2. Mueva el cubo a una ubicación diferente.
    
    3. Guarde los anclajes espaciales de Azure en la ubicación del cubo.
    
    4. Detenga la sesión de anclajes espaciales de Azure.
    
    5. Quite el delimitador local del cubo para permitir que el usuario mueva el cubo.
    
    6. Mueva el cubo en otro lugar.
    
    7. Inicie la sesión de anclajes espaciales de Azure.
    
    8. Busque los anclajes espaciales de Azure. 
    Debe volver al lugar original donde lo colocó al crear el delimitador.
    
    9. Elimine el delimitador espacial de Azure.
    
    10. Detenga la sesión de Azure.

### <a name="anchoring-an-experience"></a>Delimitar una experiencia

En las secciones anteriores, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure. Hemos usado un cubo para representar y visualizar el objeto de juego primario con el delimitador adjunto. En esta sección, aprenderá a anclar una experiencia completa colocándolo como un elemento secundario del objeto ParentAnchor. En este ejemplo, usamos la aplicación de demostración del ensamblado del módulo lunar que se creó durante la [Lección 6 del módulo base](mrlearning-base-ch6.md).

1. Busque el ensamblado del módulo lunar completo recurso prefabricado y arrástrelo a la jerarquía como elemento secundario de AnchorParent GameObject, tal como se muestra en la imagen siguiente.

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Coloque la experiencia del ensamblado del módulo para que el cubo siga expuesto como se muestra en la imagen siguiente. En la aplicación, los usuarios pueden cambiar la posición de toda la experiencia moviendo el cubo. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Nota: Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un botón para alternar un cuadro de límite que rodea la experiencia, el uso de un objeto de cambio de posición (como el cubo que se usa en este paso), el uso de la posición y la rotación Gizmos y mucho más.

## <a name="congratulations"></a>Enhorabuena
En este tutorial, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure. Esta Esso le proporcionó varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure, y crear, cargar y descargar los delimitadores de Azure en un único dispositivo. En la lección siguiente, aprenderá a guardar los identificadores de delimitador de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación. Durante la serie, también aprenderá a transferir los ID. de delimitador entre varios dispositivos para lograr la alineación espacial y a obtener información sobre las sesiones compartidas de varios usuarios, próximamente como parte del tutorial de uso compartido.

[Siguiente lección: 2. Guardado, recuperación y uso compartido de Azure Spatial Anchors](mrlearning-asa-ch2.md)

