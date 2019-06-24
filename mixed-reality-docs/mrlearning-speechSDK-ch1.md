# <a name="speech-sdk-learning-module"></a>Módulo de aprendizaje de Speech SDK

En este tutorial creará una aplicación de realidad mixta que explora el uso de Azure Cognitive Services Speech SDK con el 2 de HoloLens. Cuando haya terminado con esta serie de tutoriales, podrá usar el micrófono del dispositivo transcribir voz a texto en tiempo real, traducir su voz a otros idiomas y aprovechar la característica de intención de Speech SDK para entender el uso de los comandos de voz inteligencia artificial.

Objetivos:

- Obtenga información sobre cómo integrar Azure Speech SDK en una aplicación de HoloLens 2
- Aprenda a usar los comandos de voz
- Aprenda a usar las capacidades de voz a texto

## <a name="instructions"></a>Instrucciones

### <a name="getting-started"></a>Introducción

1. Inicie Unity y cree un nuevo proyecto. Escriba el nombre del proyecto "Módulo de aprendizaje de Speech SDK". Elija una ubicación para guardar el proyecto. A continuación, haga clic en "Crear un proyecto".

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> Nota: Asegúrese de que la plantilla está establecida en "3D", tal como se muestra en la imagen anterior.

2. Descargue el [Kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity del paquete y guárdelo en una carpeta en su PC. Importar el paquete en el proyecto de Unity. Para obtener instrucciones detalladas sobre cómo hacerlo, consulte [lección base módulo 1](mrlearning-base-ch1.md). 

3. Descargue e importe Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) para paquete de activos de Unity. Importar el paquete del SDK de voz, haga clic en "activos", seleccione "Importar paquete,", a continuación, seleccione "paquete personalizado". Busque el paquete del SDK de voz descargado anteriormente y ábralo para comenzar el proceso de importación. 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. En la siguiente ventana emergente, haga clic en "Importar" para comenzar a importar el paquete del SDK de voz. Asegúrese de se comprueban todos los elementos, como se muestra en la imagen siguiente.

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. Descargue el [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) paquete activo. El paquete de recurso Lunarcom es una colección de recursos y los scripts desarrollados para esta serie de lección para presentar un uso práctico de voz del SDK de Azure. Es un terminal de comandos de voz que finalmente se comunicará con la experiencia de ensamblado de módulo lunar desarrollada en el [Tutorial de Base de módulo.](mrlearning-base-ch6.md)
6. Importar el paquete de recurso Lunarcom en el proyecto de Unity siguiendo los mismos pasos que llevados a cabo para importar el Kit de herramientas de realidad mixta y Speech SDK.
7. Configurar el Kit de herramientas de realidad mixta (MRTK). Para ello, haga clic en el panel "Kit de herramientas de realidad mixta" en la parte superior de la ventana y, a continuación, seleccione "Agregar a la escena y configurar".

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. La escena ahora tendrá varios elementos nuevos en ella desde el MRTK. Guarde la escena con un nombre diferente, haga clic en "file", a continuación, "Guardar como" y nombre "SpeechScene" de la escena. 

   > Nota: Si presiona el botón Reproducir en la escena después de agregar el MRTK al proyecto y no el modo "reproducir", es posible que deba reiniciar Unity. 

9. Con el objeto "MixedRealityToolkit" seleccionado en la jerarquía, haga clic en "copiar y personalizar" en el panel del inspector.

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. También en el panel del inspector (con el objeto "MixedRealityToolkit" seleccionado en la jerarquía), deshabilite el sistema de diagnóstico para ello, desactive la casilla a la derecha de "Habilitar sistema de diagnóstico".

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. En el panel de proyecto, expanda la carpeta "Lunarcom" y arrastre el recurso prefabricado "Lunarcom_Base" en la jerarquía.

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. Seleccione el objeto de "Lunarcom_Base" en la jerarquía y asegúrese de que la posición está establecida en x = 0, y = 0 y, z = 0, así como la rotación establecida en x = 0, y = 0 y, z = 0. Establezca la escala para leer x = 0.008, y = 0.008 y, z = 0,01.

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. Haga clic en "agregar el componente" y busque y seleccione "LunarcomController." Este script se incluye en el paquete de recursos Lunarcom que ha importado en el paso 6.

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. Para conectar la aplicación a Azure Cognitive Services, debe escribir una clave de"suscripción" también se denomina una "clave de API" para el servicio de voz. Siga las instrucciones de [este vínculo](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) para obtener una clave de suscripción gratuita. Una vez que obtenga la clave de suscripción, escríbalo en el campo "Clave de API del servicio de voz" del componente "LunarcomController" en el panel del inspector, tal como se muestra en la imagen siguiente.

15. Especifique la región que eligió al suscribirse para la clave de suscripción en el campo "Speech Service Region" del componente "LunarcomController" en el panel del inspector.

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. En la jerarquía, expanda el objeto "Lunarcom_Base", haga clic en la flecha situada a la izquierda de la misma, y lo mismo para su objeto secundario, "Terminal" como se muestra en la imagen siguiente.

17. Mientras está seleccionado "Lunarcom_Base", haga clic y arrastre "Lunarcom Text" de la jerarquía a la ranura de "Texto de salida" en el componente "LunarcomController" en el panel del inspector, tal como se muestra en la imagen siguiente.
18. Ahora puede hacer lo mismo con el objeto "Terminal" en la ranura "terminal" y el objeto "Conexión Light" en la ranura de "Conexión luz Controller".

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. Haga clic en la flecha situada junto a la sección "Lunarcom botones" de la secuencia de comandos "LunarcomController" en el panel de inspector y cambiar el tamaño a 3 y presione la tecla ENTRAR o retorno en el teclado. Esto hará que los tres nuevos campos "Element" en aparecer.

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. Expanda "Lunarcom botones" haciendo clic en la flecha situada junto a él en la jerarquía y, con el mismo proceso que anterior, arrastre el Mic, satélite y Rocket gameobjects a las referencias del elemento 0, 1 y 2 respectivamente en el componente "LunarcomController" en el panel del inspector. 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. Seleccione el objeto "Lunarcom_Base" en la jerarquía. Haga clic en "Agregar componente" en el panel de inspector y busque y seleccione "LunarcomWakeWordRecognizer."

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. En la ranura "Wake Word", escriba "Activate Terminal". Además, en la ranura "Descartar la palabra", escriba "Terminal de descartar".

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>Enhorabuena

¡Ha configurado el reconocimiento de voz en la aplicación, con tecnología de Azure! Ejecute la aplicación para asegurarse de que todas las funciones están funcionando correctamente. Comience con la apuros wake escrito en el paso 22, "Activate Terminal". A continuación, seleccione el botón de micrófono para iniciar el reconocimiento de voz y empiece a hablar. Verá las palabras de transcripción en el terminal mientras habla. Presione el botón de micrófono una segunda vez para detener el reconocimiento de voz. Diga "Descartar Terminal" para ocultar el terminal Lunarcom. En la lección siguiente, se obtendrá información sobre cómo cambiar dinámicamente a utilizando el reconocimiento de voz con tecnología de dispositivo para las situaciones donde la voz del Azure SDK no está disponible debido a las 2 de HoloLens sin conexión.

[Siguiente lección: Speech SDK lección 2](mrlearning-speechSDK-ch2.md)

