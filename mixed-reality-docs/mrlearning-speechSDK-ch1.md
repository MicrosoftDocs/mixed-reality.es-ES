---
title: 'Tutoriales de Azure Speech Services: 1. Integración y uso del reconocimiento de voz y la transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: defa33e56cfe4450a8d42855bd11dc23973dc401
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913447"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. integración y uso del reconocimiento de voz y la transcripción

En este tutorial se crea una aplicación de realidad mixta que explora el uso de Azure Cognitive Services Speech SDK con HoloLens 2. Una vez finalizada esta serie de tutoriales, podrá usar el micrófono del dispositivo para transcribir voz en texto en tiempo real, traducir su voz en otros idiomas y aprovechar la característica de intención del SDK de Speech para comprender los comandos de voz con inteligencia artificial.

## <a name="objectives"></a>Objetivos

- Obtenga información sobre cómo integrar el SDK de voz de Azure en una aplicación de HoloLens 2.
- Obtener información sobre cómo usar comandos de voz
- Aprenda a usar las funcionalidades de voz a texto

## <a name="instructions"></a>Instrucciones

### <a name="getting-started"></a>Tareas iniciales

1. Inicie Unity y cree un nuevo proyecto. Escriba el nombre del proyecto de Speech SDK Learning Module. Elija una ubicación donde guardar el proyecto. A continuación, haga clic en crear proyecto.

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >Asegúrese de que la plantilla está establecida en 3D, tal como se muestra en la imagen anterior.

2. Descargue el paquete de la [versión 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) del [Kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) y guárdelo en una carpeta de su equipo. Importe el paquete en el proyecto de Unity. Para obtener instrucciones detalladas sobre cómo hacerlo, consulte los [tutoriales de introducción de la lección 2. Inicializar el proyecto y la primera aplicación](mrlearning-base-ch1.md).

3. Descargue e importe el [SDK de voz](https://aka.ms/csspeech/unitypackage) de Azure para el paquete de activos de Unity. Importe el paquete del SDK de Speech; para ello, haga clic en recursos, seleccione Importar paquete y, a continuación, seleccione paquete personalizado. Busque el paquete del SDK de Speech descargado anteriormente y ábralo para comenzar el proceso de importación.

    ![mrlearning-Speech-CH1-1-step3a. png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-Speech-CH1-1-step3b. png](images/mrlearning-speech-ch1-1-step3b.png)

4. En la siguiente ventana emergente, haga clic en importar para iniciar la importación del paquete del SDK de Speech. Asegúrese de que todos los elementos se comprueban como se muestra en la imagen siguiente.

    ![mrlearning-Speech-CH1-1-Step4. png](images/mrlearning-speech-ch1-1-step4.png)

5. Descargue el paquete de activos del módulo Speech SDK, también conocido como paquete Lunarcom haciendo clic en [este vínculo](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2). El paquete de recursos Lunarcom es una colección de recursos y scripts desarrollados para esta serie de lecciones con el fin de presentar un uso práctico del SDK de voz de Azure. Es un terminal de comandos de voz que, en última instancia, se conectará a la experiencia de ensamblado del módulo lunar desarrollada en los [tutoriales de introducción: lección 7. Crear una aplicación de ejemplo de módulo lunar](mrlearning-base-ch6.md).

6. Importe el paquete de recursos Lunarcom en el proyecto de Unity siguiendo unos pasos similares que se han llevado a cabo para importar el kit de herramientas de realidad mixta y el SDK de Speech.

7. Configure el kit de herramientas de realidad mixta (MRTK).

    Para ello, haga clic en el panel del kit de herramientas de realidad mixta en la parte superior de la ventana y, a continuación, seleccione Agregar a escena y configurar.

    ![mrlearning-Speech-CH1-1-step7a. png](images/mrlearning-speech-ch1-1-step7a.png)

    En el menú emergente que aparece, seleccione DefaultHoloLens2ConfigurationProfile para convertirlo en el perfil activo para el kit de herramientas de realidad mixta.

    ![mrlearning-Speech-CH1-1-step7b. png](images/mrlearning-speech-ch1-1-step7b.png)

8. La escena ahora tiene varios elementos nuevos en ella desde MRTK. Guarde la escena en un nombre diferente; para ello, haga clic en "archivo", "guardar como" y asigne el nombre SpeechScene a la escena.

    >[!NOTE]
    >Si presiona reproducir en la escena después de agregar el MRTK al proyecto y no entra en el modo de reproducción, es posible que tenga que reiniciar Unity.

9. Con el objeto MixedRealityToolkit seleccionado en la jerarquía de la escena, haga clic en copiar & personalizar en el panel Inspector para abrir el menú emergente del perfil de clonación. En el menú emergente clonar perfil, escriba un nombre adecuado para su perfil personalizado, por ejemplo, HoloLens2ConfigurationProfile personalizado y haga clic en clonar para crear el perfil de configuración personalizado y establézcalo como el perfil activo.

    ![mrlearning-Speech-CH1-1-step9. png](images/mrlearning-speech-ch1-1-step9.png)

10. También en el panel Inspector (con el objeto MixedRealityToolkit seleccionado en la jerarquía), deshabilite el sistema de diagnósticos desactivando la casilla situada a la derecha de habilitar el sistema de diagnósticos.

    ![mrlearning-Speech-CH1-1-step10. png](images/mrlearning-speech-ch1-1-step10.png)

11. En este tutorial, vamos a usar los comandos de voz de entrada para el reconocimiento de voz y la transcripción. Permite clonar el perfil de entrada para realizar cambios en la configuración de voz.

    Con el objeto MixedRealityToolkit todavía seleccionado en la jerarquía de la escena, haga clic en el botón pequeño clon del panel Inspector para abrir el menú emergente del perfil de clonación. En el menú emergente clonar perfil, escriba un nombre adecuado para su perfil personalizado, por ejemplo, HoloLens2InputSystemProfile personalizado y, a continuación, haga clic en clonar para crear el perfil de sistema de entrada personalizado y establézcalo como el perfil activo.

    ![mrlearning-Speech-CH1-1-step11. png](images/mrlearning-speech-ch1-1-step11.png)

12. Una vez clonado el perfil de entrada, expanda la sección voz y siga el mismo proceso que en el paso anterior para clonar el perfil comandos de voz.

    ![mrlearning-Speech-CH1-1-step12. png](images/mrlearning-speech-ch1-1-step12.png)

13. Ahora, en la sección voz, vaya a configuración general y cambie el comportamiento de inicio a Inicio manual.

    ![mrlearning-Speech-CH1-1-step13. png](images/mrlearning-speech-ch1-1-step13.png)

14. En el panel Proyecto, expanda la carpeta Lunarcom y arrastre el Lunarcom_Base recurso prefabricado a la jerarquía de la escena.

    ![mrlearning-Speech-CH1-1-step14. png](images/mrlearning-speech-ch1-1-step14.png)

15. Seleccione el objeto de Lunarcom_Base de la jerarquía y asegúrese de que la posición está establecida en x = 0, y = 0 y z = 0, así como en la rotación establecida en x = 0, y = 0 y z = 0. Establezca la escala en Read x = 0.008, y = 0.008 y z = 0,01.

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. Haga clic en Agregar componente y busque y seleccione controlador de Lunarcom. Este script se incluye en el módulo de recursos Lunarcom que importó en el paso 6.

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. Para conectar la aplicación a Azure Cognitive Services, debe especificar una clave de suscripción (también conocida como clave de API) para el servicio de voz. Siga las instrucciones que se indican [aquí](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) para obtener una clave de suscripción gratuita. Una vez que obtenga la clave de suscripción, escríbala en el campo clave de la API del servicio de voz del componente LunarcomController en el panel Inspector, tal como se muestra en la imagen siguiente.

18. Escriba la región que eligió al suscribirse a la clave de suscripción en el campo región del servicio de voz del componente LunarcomController del panel Inspector. Por ejemplo, para la región oeste de EE. UU., escriba "westus".

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. En la jerarquía, expanda el objeto Lunarcom_Base haciendo clic en la flecha situada a su izquierda. A continuación, haga lo mismo para su objeto secundario, "terminal, tal como se muestra en la imagen siguiente.

20. Mientras Lunarcom_Base está seleccionado, haga clic en el texto Lunarcom y arrástrelo desde la jerarquía hasta la ranura del texto de salida en el componente LunarcomController del panel Inspector, tal como se muestra en la imagen siguiente.

21. Haga lo mismo con el objeto terminal en la ranura de terminal y el objeto de luz de conexión con la ranura del controlador de luz de conexión.

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. Haga clic en la flecha situada junto a la sección botones de Lunarcom del script LunarcomController en el panel Inspector y cambie el tamaño a 3. Presione entrar o entrar. Esto hace que aparezcan tres nuevos campos de elemento.

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. Para expandir los botones de Lunarcom, haga clic en la flecha situada junto a él en la jerarquía y, con el mismo proceso anterior, arrastre los GameObjects MIC, Satellite y Rocket a las referencias del elemento 0, 1 y 2, respectivamente, en el componente LunarcomController de la Panel Inspector.

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. Seleccione el objeto Lunarcom_Base "en la jerarquía. Haga clic en Agregar componente en el panel Inspector y busque y seleccione Lunarcom Speech Recognizer. Repita los mismos pasos para agregar reconocedor de Lunarcom Wake Word.

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. En la ranura de reactivación de la palabra, escriba activar terminal. En la casilla descartar palabra, escriba descartar terminal.

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>Compilación de la aplicación para el dispositivo

1. Vuelva a abrir la ventana de configuración de compilación. para ello, vaya a archivo > configuración de compilación.

    ![images/mrlearning-Speech-CH1-2-paso 1](images/mrlearning-speach-ch1-2-step1.jpg)

2. Comprueba que la escena que deseas probar está en la lista "Scenes in Build" (Escenas en compilación) haciendo clic en el botón "Add Open Scenes" (Agregar escenas abiertas).

3. Presione el botón Configuración del reproductor y vaya a configuración de publicación. En capacidades, habilite: Internet, servidor cliente de Internet, servidor cliente de red privada, micrófono y percepción espacial.

4. En la misma configuración del reproductor, vaya a la configuración de XR y seleccione la realidad virtual admitida en activado.

5. Presiona el botón Build (Compilar) para comenzar el proceso de compilación.

    ![mrlearning-Speech-CH1-2-paso5](images/mrlearning-speach-ch1-2-step5.jpg)

6. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se ha creado una carpeta con el nombre "App" (Aplicación) para contener la aplicación. Haz clic en "Select Folder" (Seleccionar carpeta) para empezar a compilar la carpeta recién creada. Una vez finalizada la compilación, puedes cerrar la ventana "Build Settings" (Configuración de compilación) en Unity.

    ![mrlearning-Speech-CH1-2-Paso6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Si ve un error como "error: CS0246 = no se encontró el tipo o el nombre de espacio de nombres" XX "(¿falta una directiva using o una referencia de ensamblado?)", es posible que deba instalar el [SDK de Windows 10 (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)

7. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haga doble clic en el archivo de solución ". sln" para abrir el archivo de solución en Visual Studio.

    >[!NOTE]
    >Asegúrate de abrir la carpeta recién creada [es decir, la carpeta "App" (Aplicaciones), si ha seguido las convenciones de nomenclatura de los pasos anteriores], ya que habrá un archivo .sln con el mismo nombre fuera de esa carpeta que no debes confundir con el archivo .sln dentro de la carpeta de compilación. 

    ![mrlearning-Speech-CH1-2-STEP7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >Si Visual Studio te pide que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de requisitos previos estén instalados, tal como se especifica en la [página "Instalación de las herramientas"](install-the-tools.md).

8. Conecta HoloLens 2 a tu equipo con el cable USB. Aunque en estas instrucciones de la lección se supone que vas a implementar una prueba con un dispositivo HoloLens 2, también puedes optar por realizar la implementación en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o decidir crear un [paquete de la aplicación para una transferencia local](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

9. Antes de compilar en el dispositivo, comprueba que el dispositivo está en modo de desarrollador. Si es la primera vez que estás realizando una implementación en HoloLens 2, Visual Studio puede pedirte que emparejes HoloLens 2 con un PIN. Sigue [estas instrucciones](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) si tienes que habilitar el modo de desarrollador o emparejar con Visual Studio.

10. Configura Visual Studio para compilar HoloLens 2 seleccionando la configuración "Release" (Liberar) y la arquitectura "ARM".

    ![mrlearning-Speech-CH1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. El último paso es compilar en el dispositivo seleccionando Depurar>Iniciar sin depurar. Al seleccionar "Iniciar sin depurar", la aplicación se iniciará de inmediato en el dispositivo tras una compilación correcta, pero sin que la información de depuración aparezca en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación. También puedes seleccionar Compilar>Implementar solución para realizar una implementación en el dispositivo sin necesidad de que se reinicie automáticamente la aplicación.

    ![mrlearning-Speech-CH1-2-step11. JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>Enhorabuena

Ha configurado el reconocimiento de voz en la aplicación, con la tecnología de Azure. Ejecute la aplicación para asegurarse de que todas las funciones y características funcionan correctamente. Empiece por decir la palabra de reactivación que escribió en el paso 22, activar terminal. Seleccione el botón micrófono para iniciar el reconocimiento de voz. Empiece a hablar. Verá las palabras transformadas en el terminal mientras habla. Presione el botón micrófono una segunda vez para detener el reconocimiento de voz. Por ejemplo, descartar terminal para ocultar el terminal Lunarcom. En la lección siguiente, veremos cómo cambiar dinámicamente al uso del reconocimiento de voz basado en dispositivos en situaciones en las que el SDK de voz de Azure no está disponible debido a que HoloLens 2 está sin conexión.

[Siguiente tutorial: 2. agregar un modo sin conexión para la traducción de voz a texto local](mrlearning-speechSDK-ch2.md)
