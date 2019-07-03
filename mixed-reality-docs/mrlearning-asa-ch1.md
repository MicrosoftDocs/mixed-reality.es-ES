---
title: Módulo de ASA de aprendizaje de MR Azure delimitador espaciales en HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: fcca828fa228894e0e60986c6c7fd0053b210357
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523236"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Introducción a Azure espacial delimitadores

Le damos la bienvenida al módulo de segundo de los tutoriales de HoloLens 2. Antes de comenzar, asegúrese de que todos los de la [requisitos previos](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) se completan. Si no ha completado la primera, [módulo Base](mrlearning-base.md) aún, se recomienda que complete primero ese módulo. Si está comenzando desde un nuevo proyecto de Unity, siga los pasos de creación del proyecto nuevo en el [módulo Base](mrlearning-base.md). 

## <a name="objectives"></a>Objetivos

* Conozca los aspectos básicos del desarrollo con Azure anclajes espaciales con HoloLens 2

* Crear, cargar y descargar los anclajes espaciales

  

## <a name="instructions"></a>Instrucciones

### <a name="downloading-and-importing-assets"></a>Descarga e importación de activos
Antes de comenzar, descargue e importe los siguientes recursos:

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Módulo Base MR paquete de recursos](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[Paquete de recursos de módulo ASA](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> Nota: Vea el paso 5 para obtener instrucciones específicas sobre cómo importar delimitadores espacial de Azure, paso 6 para obtener instrucciones específicas sobre el módulo MR Base paquete de recursos y los pasos 3 a 4 para obtener instrucciones específicas en el Kit de herramientas de realidad mixta (MRKT).

1. Cree una nueva escena en el proyecto. A la derecha, haga clic en la carpeta de la escena, haga clic en crear y, después, en escena. Nombre de la nueva escena ASALearningmodule.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Haga doble clic en ASALearningmodule para ver algunos elementos predefinidos aparecen junto con la nueva escena. 
3. Configure la escena para el desarrollo de realidad mixta. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: Verá un mensaje emergente que dice, debe elegir un archivo para el Kit de herramientas de realidad mixta. Al hacer clic en Aceptar, se accede al paso 4.

4. Al elegir un archivo para el MRTK, seleccione DefaultMixedRealityToolkitConfigurationProfile.

   > Nota: Si tiene su propio perfil de configuración, no dude usarlo en su lugar.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Ahora la escena está configurada para realidad mixta. Asegúrese de guardar la escena (hacer esto con uno de los controles o comando + S o haga clic en el archivo, a continuación, haga clic en Guardar en). 

5. Importar el [Azure delimitadores espaciales](https://github.com/azure/azure-spatial-anchors-samples/releases). Para poder usar delimitadores espaciales, debe importar este recurso. Haga clic en el vínculo anterior y haga clic con el botón derecho en AzureSpatialAnchors.unitypackage. Haga clic en Guardar destino como y guárdelo en su equipo. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   Después de guardarla, vaya a Unity, haga clic en los activos, dejan de funcionar al paquete de importación. A continuación, haga clic en el paquete personalizado... Se abrirán los archivos del equipo. Cuando realice, encontrar donde guardó el paquete Azure espacial delimitadores y selecciónelo. A continuación, haga clic en Abrir.

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   Un elemento emergente aparece providingg una lista de herramientas y la configuración que le pide que lo que se debe importar. Seleccione ***todas*** de las opciones disponibles, a continuación, haga clic en Importar.

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > Nota: Tenga paciencia, tardará unos minutos en Importar. 

   6. Importación [módulo MR Base activo Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) siguiente. Mucho al igual que el paso 5, haga clic en el vínculo anterior. A continuación, haga clic con el botón secundario del mouse en BasemoduleAssetsV1 1.unitypackag y haga clic en Guardar destino como y guardarlo en el equipo.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > Sugerencia: Guarde todos estos recursos en la misma carpeta para que sean más fáciles de encontrar y tener acceso a. Mantiene todo bien y organizada.

   Igual que el paso 5, volver atrás a Unity, haga clic en los recursos y mantenga el mouse sobre el paquete de importación. Haga clic en el paquete personalizado... Los archivos del equipo volverá a aparecer. Vaya a donde guardó el paquete de recursos del módulo de Base. y selecciónelo. Haga clic en Abrir.

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > Nota: Puede haber más activos necesarios más adelante en este módulo. Siga estos pasos para importar los recursos mencionados a partir de ese momento. 
                                                                                                                                                                                                                    
7. Importar la confirmación del módulo ASA mediante el mismo enfoque que importar los paquetes anteriores.

### <a name="configuring-your-scene"></a>Configuración de la escena

En esta sección, agregaremos prefabricados y secuencias de comandos en la escena para crear una serie de botones que se muestran los aspectos básicos de cómo se comportan los delimitadores locales y Azure espacial anclajes en una aplicación.

7. En la ficha de proyecto, debajo de la carpeta de recursos, haga clic en ASAmoduleAssets. Una vez seleccionado, verá dos prefabricados: ButtonParent y ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. Arrastre ambos prefabricados a la escena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. Haga doble clic en el delimitador de elemento primario para seleccionarlo. Es posible que deba ajustar la vista para ver toda la escena. Ajuste la escena según sea necesario.

    Familiarícese con el recurso prefabricado ParentAnchor. Actualmente, el objeto de juego con nombre, ParentAnchor, es un cubo de color para fines de demostración. Finalmente, hemos ', ll ocultar el cubo y coloque el contenido como un elemento secundario de la ParentAnchor. Este recurso prefabricado incluye la secuencia de comandos AzureSpatialAnchorsDemoWrapper.cs (incluido con el SDK de ASA) y el script ASAmoduleScript.cs, incluido como parte de este módulo para el objeto ParentAnchor. 

10. Configurar los botones. En el prefabricado verá ParentAnchor, tenga en cuenta varios botones con la etiqueta. Estos botones se crean desde prefabricados de PressableButton del MRTK. Más información sobre cómo crear botones Pressable desde el [módulo Base](mrlearning-base-ch2.md). Para cada botón, agregue un evento que se desencadena cuando el usuario presiona o selecciona el botón de acuerdo con la siguiente lista. 

- Para el botón denominado StartAzureSession, cree un nuevo evento en el desencadenador de eventos de botón presionado, así como el desencadenador de eventos en haga clic en. Arrastre el objeto ParentAnchor en el campo vacío y asignar el método StartAzureSession() del componente de ASAmoduleScript ParentAnchor del objeto.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Para el nombre del botón, StopAzureSession, cree un nuevo evento en el desencadenador de eventos de botón presionado, así como el desencadenador de eventos en haga clic en. Arrastre el objeto ParentAnchor en el campo vacío y asignar el método StopAzureSession() del componente de ASAmoduleScript ParentAnchor del objeto.

- Para el botón denominado CreateAnchor, cree un nuevo evento en el desencadenador de eventos de botón presionado, así como el desencadenador de eventos en haga clic en. Arrastre el objeto ParentAnchor en el campo vacío y asignar el método CreateAzureAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

- Desencadenador de eventos para el botón denominado inicio busca para delimitador, crear un nuevo evento en el botón de presionar", así como el desencadenador de eventos en haga clic en. Arrastre el objeto ParentAnchor en el campo vacío y asignar el método FindAzureAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

- Para el botón denominado DeleteAzureAnchor, cree un nuevo evento en el desencadenador de eventos de botón presionado, así como el desencadenador de eventos en haga clic en. Arrastre el objeto ParentAnchor en el campo vacío y asignar el método DeleteAzureAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

- Para el botón de anclaje con nombre, eliminar Local, cree un nuevo evento en el desencadenador de eventos de botón presionado, así como el desencadenador de eventos en haga clic en. Arrastre el objeto ParentAnchor en el campo vacío y asignar el método RemoveLocalAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

### <a name="build-and-demonstrate-base-application"></a>Generar y mostrar la aplicación de Base

Ahora que la escena está configurada para demostrar los conceptos básicos de Azure espacial delimitadores, compilará y demostrar el comportamiento básico de Azure espacial delimitadores. 

1. Si has cerrado la ventana Build Settings (Configuración de compilación) de las secciones anteriores, abre de nuevo la ventana de configuración de compilación en File>Build Settings (Archivo>Configuración de compilación).
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Asegúrese de la escena que desea probar está en segundo plano en la lista de compilación haciendo clic en el botón Agregar escenas abierto.

3. Presiona el botón Build (Compilar) para comenzar el proceso de compilación.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se creó una carpeta con el nombre de la aplicación para que contenga la aplicación. Haga clic en seleccionar la carpeta para empezar a crear la carpeta recién creada. Una vez finalizada la compilación, puede cerrar la configuración de compilación"ventana de Unity. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > Nota: Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Si ves un error como "Error: Error CS0246 = "XX" no se encontró el nombre de espacio de nombres o tipo (¿falta un uso de la directiva o una referencia de ensamblado?). Es posible que deba instalar [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haga doble clic en la solución de the"MixedRealityBase.sln o el nombre correspondiente. Si usa un nombre alternativo para el proyecto para abrir el archivo de solución en Visual Studio.

  > Nota: Asegúrese de abrir la carpeta recién creada (es decir, la carpeta aplicación, si sigue las convenciones de nomenclatura de los pasos anteriores porque habrá un archivo .sln con el mismo nombre fuera de esa carpeta que no debe confundirse con el archivo .sln dentro de la carpeta de compilación. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > Nota: Si Visual Studio le pide que instale los nuevos componentes, dedique un momento para asegurarse de que todos los componentes de requisitos previos están instalados en lo más específico [la página "Instalar las herramientas"](install-the-tools.md) 

6. Conecta HoloLens 2 a tu equipo con el cable USB. Aunque estas instrucciones de la lección se suponen que va a implementar una prueba con un dispositivo HoloLens 2, también puede optar por implementar en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o elegir crear un [paquete de aplicación de instalación de prueba](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Antes de compilar en el dispositivo, comprueba que el dispositivo está en modo de desarrollador. Si es la primera vez que estás realizando una implementación en HoloLens 2, Visual Studio puede pedirte que emparejes HoloLens 2 con un PIN. Siga [estas instrucciones](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) si tiene que habilitar el modo de programador o emparejarse con Visual Studio.

8. Configurar Visual Studio para compilar el 2 de HoloLens seleccionando la configuración de lanzamiento, así como la arquitectura de Resource Manager.
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. El último paso es crear en el dispositivo seleccionando Depurar > Iniciar sin depurar. Seleccione Iniciar sin depurar, hace que la aplicación iniciar inmediatamente en el dispositivo en una información de depuración de compilación correcta ithout que aparecen en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación. También puede seleccionar compilación > implementar la solución para implementar en el dispositivo sin necesidad de la aplicación se inicie automáticamente.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. siga las instrucciones. Cuando la aplicación se está ejecutando en el dispositivo, siga la pantalla instrucciones. Presione los botones de escenas correspondientes a los pasos siguientes.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Inicie la sesión de delimitadores espacial.
    
    2. Mueva el cubo a una ubicación diferente.
    
    3. Guarde los delimitadores Azure espaciales en la ubicación del cubo.
    
    4. Detener la sesión de Azure delimitadores espacial.
    
    5. Quite el delimitador en el cubo para permitir que el usuario mueva el cubo local.
    6. Mueva el cubo en otro lugar.
    
    7. Inicie sesión de Azure delimitadores espacial.
    
    8. Busque Azure delimitadores espaciales. 
    
    e debe volver a la ubicación original, colóquelo al crear el delimitador.
    9. Eliminar Azure delimitador espacial.
    
    10. Detener sesión de Azure.

### <a name="anchoring-an-experience"></a>Delimitación de una experiencia

En las secciones anteriores, ha aprendido los aspectos básicos de Azure espacial delimitadores. Hemos usado para representar y visualizar el objeto primario del juego con el delimitador que se adjunta un cubo. En esta sección, obtendrá información sobre cómo anclar una experiencia completa colocando como elemento secundario del objeto ParentAnchor. En este ejemplo, usamos el módulo lunar aplicación de demostración de ensamblado que se creó durante la [módulo básico lección 6](mrlearning-base-ch6.md).

1. Busque el módulo Lunar ensamblado completa prefabricado y arrástrelo a la jerarquía como un elemento secundario de la gameobject AnchorParent tal como se muestra en la imagen siguiente.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Experiencia de posición el ensamblado de módulo para que el cubo aún se expone como se muestra en la imagen siguiente. En la aplicación, los usuarios pueden cambiar la posición de toda la experiencia moviendo el cubo. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > Nota: Hay una variedad de flujos de experiencia de usuario para cambiar la posición de experiencias, incluido el uso de un botón para alternar un cuadro de límite que rodea a la experiencia, el uso de un objeto colocaban (por ejemplo, el cubo que se usa en este paso) el uso de la posición y giro gizmos y mucho más.

## <a name="congratulations"></a>Enhorabuena
En este tutorial, ha aprendido los aspectos básicos de Azure espacial delimitadores. Este esson proporciona varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar los anclajes de azure en un único dispositivo. En la siguiente lección, aprenderemos cómo guardar los identificadores de delimitador de Azure en el 2 de HoloLens para la recuperación, incluso después de que se reinicie la aplicación. Durante la serie, también aprenderá cómo transferir los identificadores de delimitador entre varios dispositivos para lograr la alineación espacial y obtenga información acerca de varios usuarios compartida las sesiones, próximamente como parte del tutorial de uso compartido.

[Siguiente lección: Lección 2 de ASA](mrlearning-asa-ch2.md)

