---
title: 'Tutoriales de anclaje espacial de Azure: 1. Introducción a los delimitadores espaciales de Azure'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b615f1135f5d2947f8f718e080ef45a3c1fcc576
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830850"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introducción a los anclajes espaciales de Azure

Este es el segundo módulo de los tutoriales de HoloLens 2. Antes de empezar, asegúrese de que se hayan completado todos los [requisitos previos](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) . Si aún no ha completado el primer [módulo base](mrlearning-base.md) , se recomienda que complete primero ese módulo. Si va a comenzar desde un nuevo proyecto de Unity, siga los pasos de creación del nuevo proyecto en el [módulo base](mrlearning-base.md). 

## <a name="objectives"></a>Objetivos

* Conozca los aspectos básicos del desarrollo con los anclajes espaciales de Azure con HoloLens 2

* Crear, cargar y descargar anclajes espaciales

## <a name="instructions"></a>Instrucciones

### <a name="downloading-and-importing-assets"></a>Descarga e importación de recursos
Antes de comenzar, descargue e importe los siguientes recursos:

[Anclajes espaciales de Azure v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[Unity. HoloLens2. GettingStarted. tutoriales. Asset. 2.1.0.0. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[Unity. HoloLens2. AzureSpatialAnchor. tutoriales. Asset. 2.1.0.0. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[Paquete para el kit de herramientas de realidad mixta 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. Cree una nueva escena en el proyecto. Haga clic con el botón derecho en la carpeta de la escena, haga clic en crear y luego en escena. Asigne a la nueva escena el nombre "ASALearningModule".

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Haga doble clic en "ASALearningmodule" para ver algunos elementos predefinidos que aparecerán junto con la nueva escena. 
3. Configure la escena para el desarrollo de realidad mixta. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: es posible que vea un cuadro de diálogo emergente para seleccionar un [perfil para el kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Elija el perfil denominado *DefaultHoloLens2ConfigurationProfile* haciendo doble clic en él.

4. Al elegir un archivo para MRTK, seleccione DefaultMixedRealityToolkitConfigurationProfile.

> Nota: Si tiene su propio perfil de configuración, no dude en usarlo en su lugar.
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

La escena ya está configurada para la realidad mixta. Asegúrese de guardar la escena (haga esto con control/comando + S o haga clic en archivo, seguido de guardar). 

5. Importe el paquete de [anclaje espacial de Azure v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) Unity que descargó en el paso 1. Para ello, haga clic en activos, desplácese hasta importar paquete y, a continuación, haga clic en paquete personalizado... Se abrirán los archivos del equipo. Cuando lo haga, busque el lugar en el que guardó el paquete de anclajes espaciales de Azure y selecciónelo. A continuación, haga clic en abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Aparece una ventana emergente que proporciona una lista de herramientas y valores de configuración que le piden qué importar. Seleccione ***todas*** las opciones disponibles y, a continuación, haga clic en importar.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Nota: sea paciente, tardará unos minutos en realizar la importación. 

6. Importe [Unity. HoloLens2. gettingstarted. tutorials. Asset. 2.1.0.0. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) Next. Al igual que el paso 5, vuelva a Unity, haga clic en activos y mantenga el mouse sobre el paquete de importación. Haga clic en paquete personalizado... Los archivos del equipo volverán a aparecer. Vaya a la ubicación en la que almacenó el módulo de recursos del módulo base. y selecciónelo. Haga clic en Abrir.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Nota: es posible que se necesiten más recursos más adelante en este módulo. Siga estos pasos para importar los recursos mencionados a partir de este punto. 

7. Importe el [módulo asa Module 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage), siguiendo los mismos pasos que para importar los paquetes anteriores.

### <a name="configuring-your-scene"></a>Configuración de la escena

En esta sección, agregaremos Prefabs y scripts a la escena para crear una serie de botones que muestran los aspectos básicos de cómo se comportan los delimitadores locales y los delimitadores espaciales de Azure en una aplicación.

8. En la pestaña proyecto, debajo de la carpeta activos, haga clic en ASAmoduleAssets. Una vez seleccionado, verá dos Prefabs: ButtonParent y ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Arrastre ambos Prefabs a la escena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

Nota: después de agregar ButtonParent a la escena, aparecerá una ventana emergente en la que se le pedirá que importe los recursos de TMP. Importe "TMP Essentials". Después, si ve un texto de fuente grande en la escena, elimine el objeto ButtonParent y agréguelo de nuevo desde la carpeta ASAmoduleAssets.

Nota: Si desea comprobar los registros de depuración en HoloLens, puede arrastrar y colocar la DebugWindow recurso prefabricado de la carpeta ASAModuleAssets en la escena. Adjunte el script DebugWindowMessaging en el panel Inspector de DebugWindow y habilite la opción de la ventana Depurar habilitada. Después, arrastre y coloque DebugWindow recurso prefabricado en el campo DebugText Empty. También puede ajustar la posición de DebugWindow cuando sea apropiado.

10. Para acercar la escena, haga doble clic en el anclaje primario en la jerarquía y ajuste la vista para ver toda la escena según sea necesario. Actualmente, ParentAnchor es un cubo coloreado que se usa solo con fines de demostración. Finalmente, se ocultará el cubo y se colocará el contenido como un elemento secundario de ParentAnchor. 

11. Ahora vamos a configurar los botones para el funcionamiento de la escena. Para ello, expanda ButtonParent recurso prefabricado y verá varios botones con etiqueta, que se crean a partir de la Prefabs PressableButton de MRTK. Obtenga más información sobre cómo crear PressableButton desde el [módulo base](mrlearning-base-ch2.md). Para que estos botones funcionen, debe agregar un evento que se desencadenará cuando el usuario presione o seleccione los botones individuales. 

- En el caso del botón denominado StartAzureSession, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método StartAzureSession () desde el componente ASAmoduleScript del objeto ParentAnchor, tal como se muestra en la captura de pantalla siguiente.
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- En el caso del botón denominado StopAzureSession, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método StopAzureSession () desde el componente ASAmoduleScript del objeto ParentAnchor.

- En el caso del botón denominado CreateAnchor, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método CreateAzureAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.  **Después, arrastre ParentAnchor de nuevo al siguiente campo vacío "objeto de juego".**

- En el caso del botón denominado start buscar delimitador, cree un nuevo evento en el botón Pulse "desencadenador de eventos, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método FindAzureAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.

- En el caso del botón denominado DeleteAzureAnchor, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método DeleteAzureAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor.  

- En el caso del botón denominado eliminar delimitador local, cree un nuevo evento bajo el desencadenador de eventos presionado del botón, así como el desencadenador de evento al hacer clic. Arrastre el objeto ParentAnchor al campo vacío y asigne el método RemoveLocalAnchor () desde el componente ASAmoduleScript del objeto ParentAnchor. **Después, arrastre el objeto ParentAnchor de nuevo al siguiente campo vacío "objeto de juego".**

12. Para configurar los anclajes espaciales de Azure, vaya a la carpeta AzureSpatialAnchorsPlugin en la carpeta assets y navegue hasta examples-> Resources-> archivo AzureSpatialAnchorsDemoConfig. En el panel Inspector, agregue el identificador de cuenta y la clave de cuenta de Azure que creó anteriormente. Si no los ha creado o no los tiene, siga los [requisitos previos](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens). 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a>Compilar y demostrar la aplicación base

Ahora que la escena está configurada para mostrar los aspectos básicos de los anclajes espaciales de Azure, crearemos y mostraremos el comportamiento básico de los delimitadores espaciales de Azure. 

1. Vuelva a abrir la ventana de configuración de compilación. para ello, vaya a archivo > configuración de compilación.
    ![mrlearning-asa-CH1-3-paso 1](images/mrlearning-asa-ch1-3-step1.jpg)
2. Asegúrese de que la escena que desea probar está en segundo plano en la lista de compilación; para ello, haga clic en el botón Agregar escenas abiertas.
3. Compruebe que la plataforma esté establecida en el Plataforma universal de Windows. Si no es así, establézcalo en el mismo.
4. Presione el botón Configuración del reproductor y vaya a configuración de publicación. En capacidades, habilite: Internet, servidor cliente de Internet, servidor cliente de red privada, almacenamiento extraíble, cámara web, micrófono e percepción espacial.
5. En la misma configuración del reproductor, vaya a la configuración de XR y seleccione la realidad virtual admitida en activado.
6. Presiona el botón Build (Compilar) para comenzar el proceso de compilación.
   ![mrlearning-asa-CH1-3-Paso6](images/mrlearning-asa-ch1-3-step6.jpg)
7. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se creó una carpeta con el nombre app que contiene la aplicación. Haga clic en Seleccionar carpeta para empezar a compilar en la carpeta que acaba de crear. Una vez completada la compilación, puede cerrar la ventana de configuración de compilación en Unity.

    ![mrlearning-asa-CH1-3-STEP7](images/mrlearning-asa-ch1-3-step7.jpg)

    > Nota: si se produce un error en la compilación, intente compilar de nuevo o reiniciar Unity y compilar de nuevo. Si ve un error como "error: CS0246 = no se encontró el tipo o el nombre de espacio de nombres" XX "(¿falta una directiva using o una referencia de ensamblado?), es posible que deba instalar el [SDK de Windows 10 (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) 


8. Incluso después de una compilación correcta, podría obtener algunos errores, como se muestra a continuación, pero si la compilación se realiza correctamente, puede omitirlos y continuar con los pasos siguientes.

    ![mrlearning-asa-CH1-3-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haga doble clic en la solución "MixedRealityBase. sln" o en el nombre correspondiente, si ha usado un nombre alternativo para el proyecto con el fin de abrir el archivo de solución en Visual Studio.

    > Nota: Asegúrese de abrir la carpeta recién creada (es decir, la carpeta de la aplicación, si sigue las convenciones de nomenclatura de los pasos anteriores, ya que habrá un archivo. sln con el nombre similar fuera de esa carpeta que no se debe confundir con el archivo. sln dentro de la carpeta de compilación.

    ![mrlearning-asa-CH1-3-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > Nota: Si Visual Studio le pide que instale nuevos componentes, asegúrese de que todos los componentes necesarios se instalan como específicos en [la página "instalar las herramientas"](install-the-tools.md) .


9. Conecta HoloLens 2 a tu equipo con el cable USB. Aunque estas instrucciones de la lección suponen que va a implementar una prueba con un dispositivo HoloLens 2, también puede optar por implementarla en el [emulador de hololens 2](using-the-hololens-emulator.md) o elegir crear un [paquete de aplicación para la instalación de prueba](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) .

10. Antes de compilar en el dispositivo, asegúrese de que está en modo de desarrollador. Si esta es la primera vez que se implementa en HoloLens 2, Visual Studio puede pedirle que empareje su HoloLens 2 con un PIN. Siga [estas instrucciones](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) si necesita habilitar el modo de desarrollador o emparejar con Visual Studio.

11. Configure Visual Studio para compilar en HoloLens 2, seleccionando la configuración de lanzamiento y la arquitectura ARM.

    ![mrlearning-asa-CH1-3-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. El último paso es compilar en el dispositivo seleccionando Depurar>Iniciar sin depurar. Al seleccionar iniciar sin depurar, la aplicación se inicia inmediatamente en el dispositivo tras una compilación correcta sin la información de depuración que aparece en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación. También puede seleccionar compilar > implementar solución para implementar en el dispositivo sin que la aplicación se inicie automáticamente.

    ![mrlearning-asa-CH1-3-step12](images/mrlearning-asa-ch1-3-step12.jpg)

>Nota: los delimitadores espaciales de Azure usan Internet para guardar y cargar los datos de delimitador, por lo que debe asegurarse de que el dispositivo está conectado a Internet antes de probar la aplicación ASA.

13. Sigue las instrucciones. 
    Cuando la aplicación se esté ejecutando en el dispositivo, siga las instrucciones que aparecen en pantalla. Presione los botones de la escena correspondientes a los pasos siguientes. Si ha agregado la ventana depuración tal como se mencionó en los pasos anteriores, puede ver los comentarios de la pulsación de botones individual y el progreso de las operaciones individuales relacionadas con los anclajes espaciales de Azure.

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

1. Busque "Rocket Launcher Complete" recurso prefabricado y arrástrelo a la jerarquía como un elemento secundario del objeto (vea la imagen siguiente).

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Coloque la experiencia del ensamblado del módulo para que el cubo siga expuesto, tal como se muestra en la imagen siguiente. En la aplicación, los usuarios pueden cambiar la posición de toda la experiencia moviendo el cubo. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Nota: hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un botón para alternar un cuadro de límite que rodea la experiencia, el uso de un objeto de cambio de posición (como el cubo que se usa en este paso), el uso de la posición y la rotación Gizmos y mucho más.

## <a name="congratulations"></a>Enhorabuena
En este tutorial, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure. En esta lección se proporcionan varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar delimitadores de Azure en un único dispositivo. En la lección siguiente, aprenderá a guardar los identificadores de delimitador de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación. Durante la serie, también aprenderá a transferir los ID. de delimitador entre varios dispositivos para lograr la alineación espacial y obtener información sobre las sesiones compartidas de varios usuarios, próximamente como parte del tutorial de uso compartido.

[Lección siguiente: 2. guardar, recuperar y compartir anclajes espaciales de Azure](mrlearning-asa-ch2.md)

