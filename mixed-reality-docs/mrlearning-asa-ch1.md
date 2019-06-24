---
title: Módulo de ASA de aprendizaje de MR Azure delimitador espaciales en HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326803"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>Introducción a Azure delimitadores espaciales en HoloLens 2

Bienvenido al segundo módulo del Tutorial 2 HoloLens. Antes de comenzar, asegúrese de que todos los de la [requisitos previos](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) se completan. Si no ha completado la primera, [módulo base](mrlearning-base.md) aún, se recomienda encarecidamente que completar primero. Si está comenzando desde un nuevo proyecto de unity, siga los pasos de creación del proyecto nuevo en el [módulo base](mrlearning-base.md). 

## <a name="objectives"></a>Objetivos

* Conozca los aspectos básicos del desarrollo con Azure anclajes espaciales con el 2 de HoloLens

* Crear, cargar y descargar delimitadores espaciales

  

## <a name="instructions"></a>Instrucciones

### <a name="downloading-and-importing-assets"></a>Descarga e importación de activos
Antes de empezar, debe descargar e importar los siguientes recursos:

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Módulo Base MR paquete de recursos](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[Paquete de recursos de módulo ASA](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> Nota: vea el paso 5 para obtener instrucciones específicas sobre cómo importar los delimitadores espacial de Azure, paso 6 para obtener instrucciones específicas sobre el módulo MR Base paquete de recursos y los pasos 3 y 4 para obtener instrucciones específicas sobre el Kit de herramientas de realidad mixta.

1. Cree una nueva escena en el proyecto. A la derecha, haga clic en la carpeta de la escena, haga clic en "crear", a continuación, la escena. Nombre de la nueva escena "ASALearningmodule."

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Haga doble clic en "ASALearningmodule" para ver algunos elementos predefinidos que aparecen junto con la nueva escena. 
3. Configure la escena para el desarrollo de realidad mixta. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Nota: Verá un ventana emergente que dice, "Elija un archivo para el Kit de herramientas de realidad mixta". Haga clic en "Aceptar" le llevará al paso 4.

4. Al elegir un archivo para el Kit de herramientas de realidad mixta, seleccionar, "DefaultMixedRealityToolkitConfigurationProfile".

   > Nota: Si tiene su propia configuración perfil si quiere, puede usarlo en su lugar.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Ahora la escena está configurada para realidad mixta. Asegúrese de guardar la escena (hacer esto con cualquier control / comando + S, o haga clic en archivo, a continuación, haga clic en guarda). 

5. Importar el [Azure delimitadores espaciales](https://github.com/azure/azure-spatial-anchors-samples/releases). Para poder usar delimitadores espaciales, debe importar este recurso. Por lo tanto, haga clic en el vínculo de arriba y haga clic con el botón derecho en "AzureSpatialAnchors.unitypackage". Haga clic en "Guardar destino como" y guárdela en el equipo. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   A continuación, se guarda después, volver a unity, haga clic en "activos", vaya a "Importar paquete", a continuación, haga clic en "paquete personalizado..." Se abrirán los archivos del equipo. Una vez, encontrar donde guardó el paquete Azure espacial delimitadores y selecciónelo. A continuación, haga clic en "Abrir".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   Ahora habrá un elemento emergente que proporciona una lista de herramientas y configuración, preguntando qué se va a importar. Seleccione ***todas*** de las opciones disponibles, a continuación, haga clic en "importar".

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > Nota: se tardará unos minutos en Importar, tenga paciencia. 

   6. Importación [módulo MR Base activo Pack](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) siguiente. Al igual que el paso 5, haga clic en el vínculo anterior, haga clic con el botón secundario del mouse en "BasemoduleAssetsV1 1.unitypackage" y haga clic en "Guardar destino como" y guárdela en el equipo.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > Sugerencia: Guarde todos estos recursos en la misma carpeta para que sean más fáciles de encontrar y tener acceso a. ¡Se conservará todo bien y organizada!

   Al igual que el paso 5, vaya en a unity, haga clic en "activos", mantenga el mouse sobre "Importar paquete", a continuación, haga clic en "paquete personalizado..." Por lo que los archivos del equipo deben aparecer de nuevo, vaya a donde guardó el paquete de recursos del módulo de Base y selecciónelo. A continuación, haga clic en "Abrir".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > Nota: puede haber más activos necesarios más adelante en este módulo. Siga estos pasos para importar los recursos mencionados a partir de ese momento. 

7. Importe el módulo ASA del módulo con el mismo enfoque que importar los paquetes anteriores.

### <a name="configuring-your-scene"></a>Configuración de la escena

En esta sección, agregaremos prefabricados y secuencias de comandos en la escena para crear una serie de botones que se muestran los aspectos básicos de cómo se comportan los delimitadores locales y Azure espacial anclajes en una aplicación.

7. En la pestaña "proyecto", debajo de la carpeta "activos", haga clic en "ASAmoduleAssets". Una vez seleccionado, verá 2 prefabricados, "ButtonParent" y "ParentAnchor."

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. Arrastre el prefabricados ambos en la escena. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. Haga doble clic en el delimitador de elemento primario para seleccionarlo. Es posible que deba ajustar la vista para ver toda la escena, así que ajuste su escena según sea necesario.

    Familiarícese con el recurso prefabricado ParentAnchor. Actualmente, el objeto de juego llamado "ParentAnchor" es un cubo de color, para fines de demostración. Finalmente, agregaremos ocultar el cubo y colocar el contenido como un elemento secundario de la ParentAnchor. Este recurso prefabricado incluye la secuencia de comandos AzureSpatialAnchorsDemoWrapper.cs (incluido con el SDK de ASA) y el script ASAmoduleScript.cs (incluido como parte de este módulo) para el objeto ParentAnchor. 

10. Configurar los botones. En el prefabricado verá ParentAnchor, verá varios botones con la etiqueta. Estos botones se crean desde prefabricados de PressableButton del MRTK. Más información sobre cómo crear botones Pressable desde el [módulo Base](mrlearning-base-ch2.md). Para cada botón, agregue un evento que se desencadena cuando el usuario presiona o selecciona el botón de acuerdo con la siguiente lista. 

- Para el botón denominado "StartAzureSession", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método StartAzureSession() del componente de ASAmoduleScript ParentAnchor del objeto.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Para el botón denominado "StopAzureSession", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método StopAzureSession() del componente de ASAmoduleScript ParentAnchor del objeto.

- Para el botón denominado "CreateAnchor", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método CreateAzureAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

- Para el botón de anclaje con nombre "Iniciar búsqueda para", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método FindAzureAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

- Para el botón denominado "DeleteAzureAnchor", cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método DeleteAzureAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

- Para el botón "Eliminar anclaje Local" con nombre, cree un nuevo evento en el desencadenador de eventos "Botón presionado", así como el desencadenador de eventos "En Click". Arrastre el objeto ParentAnchor en el campo vacío y asignar el método RemoveLocalAnchor() del componente de ASAmoduleScript ParentAnchor del objeto.

### <a name="build-and-demonstrate-base-application"></a>Compilar y demostrar la aplicación básica

Ahora que la escena está configurada para demostrar los conceptos básicos de Azure espacial delimitadores, compilará y demostrar el comportamiento básico de Azure espacial delimitadores. 

1. Si has cerrado la ventana Build Settings (Configuración de compilación) de las secciones anteriores, abre de nuevo la ventana de configuración de compilación en File>Build Settings (Archivo>Configuración de compilación).
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Comprueba que la escena que deseas probar está en la lista "Scenes in Build" (Escenas en compilación) haciendo clic en el botón "Add Open Scenes" (Agregar escenas abiertas).

3. Presiona el botón Build (Compilar) para comenzar el proceso de compilación.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se ha creado una carpeta con el nombre "App" (Aplicación) para contener la aplicación. Haz clic en "Select Folder" (Seleccionar carpeta) para empezar a compilar la carpeta recién creada. Una vez finalizada la compilación, puedes cerrar la ventana "Build Settings" (Configuración de compilación) en Unity. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > Nota: Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Si ves un error como "Error: CS0246 = "XX" no se encontró el nombre de tipo o espacio de nombres (¿falta un uso de directiva o una referencia de ensamblado?) ", a continuación, es posible que deba instalar [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haz doble clic en la solución "MixedRealityBase.sln" (o el nombre correspondiente, si has utilizado un nombre alternativo para el proyecto) para abrir el archivo de la solución en Visual Studio.

  > Nota: Asegúrate de abrir la carpeta recién creada [es decir, la carpeta "App" (Aplicaciones), si ha seguido las convenciones de nomenclatura de los pasos anteriores], ya que habrá un archivo .sln con el mismo nombre fuera de esa carpeta que no debes confundir con el archivo .sln dentro de la carpeta de compilación. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > Nota: Si visual studio le pide instalar nuevos componentes, dedique un momento para asegurarse de que todos los componentes de requisitos previos están instalados en lo más específico [la página "Instalar las herramientas"](install-the-tools.md) 

6. Conecta HoloLens 2 a tu equipo con el cable USB. Aunque estas instrucciones de la lección se suponen que va a implementar una prueba con un dispositivo HoloLens 2, también puede optar por implementar en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o elegir crear un [paquete de aplicación de instalación de prueba](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Antes de compilar en el dispositivo, comprueba que el dispositivo está en modo de desarrollador. Si es la primera vez que estás realizando una implementación en HoloLens 2, Visual Studio puede pedirte que emparejes HoloLens 2 con un PIN. Sigue [estas instrucciones](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) si tienes que habilitar el modo de desarrollador o emparejar con Visual Studio.

8. Configura Visual Studio para compilar HoloLens 2 seleccionando la configuración "Release" (Liberar) y la arquitectura "ARM".
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
    
9. El último paso es crear en el dispositivo seleccionando Depurar > Iniciar sin depurar. Al seleccionar "Iniciar sin depurar", la aplicación se iniciará de inmediato en el dispositivo tras una compilación correcta, pero sin que la información de depuración aparezca en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación. También puedes seleccionar Compilar>Implementar solución para realizar una implementación en el dispositivo sin necesidad de que se reinicie automáticamente la aplicación.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. Cuando la aplicación se está ejecutando en el dispositivo, siga la pantalla instrucciones. Presione los botones de escenas correspondientes a los pasos siguientes.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Inicie la sesión de Azure delimitadores espacial.
    
    2. Mueva el cubo a una ubicación diferente.
    
    3. Guarde los delimitadores Azure espaciales en la ubicación del cubo.
    
    4. Detener la sesión de Azure delimitadores espacial.
    
    5. Quite el delimitador en el cubo para permitir que el usuario mueva el cubo local.
    6. Mueva el cubo en otro lugar.
    
    7. Inicie sesión de Azure delimitadores espacial.
    
    8. Busque Azure delimitadores espaciales.
    (ahora cubo debe volver a su lugar original colocarlo cuando creó el delimitador).
    9. Eliminar Azure delimitador espacial.
    
    10. Detener sesión de Azure.

### <a name="anchoring-an-experience"></a>Delimitación de una experiencia

En las secciones anteriores, ha aprendido los aspectos básicos de Azure espacial delimitadores. Hemos usado para representar y visualizar el objeto primario del juego con el delimitador que se adjunta un cubo. En esta sección, wiill, obtenga información sobre cómo anclar una experiencia completa colocando como elemento secundario del objeto ParentAnchor. En este ejemplo, usaremos la aplicación de demostración de ensamblado de módulo Lunar que se creó durante [módulo básico lección 6](mrlearning-base-ch6.md).

1. Busque el módulo Lunar ensamblado completa prefabricado y arrástrelo a la jerarquía como un elemento secundario del gameobject AnchorParent, tal como se muestra en la imagen siguiente.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Coloque la experiencia de ensamblado de módulo de tal manera que todavía se expone el cubo, como se muestra en la imagen siguiente. En la aplicación, los usuarios pueden cambiar la posición de toda la experiencia moviendo el cubo. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > Nota: Hay una variedad de flujos de experiencia de usuario para cambiar la posición de experiencias, incluido el uso de un botón para alternar un cuadro de límite que rodea a la experiencia, el uso de un objeto colocaban (por ejemplo, el cubo que se usa en este paso) el uso de la posición y giro gizmos y mucho más.

## <a name="congratulations"></a>Enhorabuena
En esta lección, ha aprendido los aspectos básicos de Azure espacial delimitadores. Esta lección proporciona varios botones, lo que le permite explorar los pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar los anclajes de azure en un único dispositivo. En la siguiente lección, aprenderemos cómo guardar los identificadores de delimitador de Azure en el 2 de HoloLens para la recuperación, incluso después de que se reinicie la aplicación. Durante la serie, también aprenderá cómo transferir los identificadores de delimitador entre varios dispositivos para lograr la alineación espacial y, finalmente, obtenga información sobre varios usuarios compartida las sesiones (próximamente como parte del módulo de uso compartido).

[Siguiente lección: Lección 2 de ASA](mrlearning-asa-ch2.md)

