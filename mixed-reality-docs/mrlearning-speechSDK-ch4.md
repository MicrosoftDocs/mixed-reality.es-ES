---
title: 'Tutoriales de Azure Speech Services: 4. Configuración del propósito y la comprensión del lenguaje natural'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e712fc2fd66b1add5b16b7dd8e6c37551aefe43a
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003214"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. configuración del propósito y comprensión del lenguaje natural

En esta lección, explorará la característica de intención del servicio de voz de Azure. La característica de intención le permite equipar nuestra aplicación con comandos de voz con tecnología de inteligencia artificial, donde los usuarios pueden indicar comandos de voz no específicos y seguir teniendo la intención entendida por el sistema. En esta lección, se configurará nuestro portal de LUIS de Azure, se configurará nuestra intención/entidades/grabaciones, se publicará nuestro recurso de intención, se conectará la aplicación de Unity a nuestro recurso de intención y se realizará nuestra primera llamada de API de intención.

## <a name="objectives"></a>目標

- Obtenga información sobre cómo configurar la intención y el lenguaje natural en nuestra aplicación.
- Aprenda a configurar el portal de LUIS de Azure
- Aprenda a configurar la intención, las entidades y los grabaciones en Azure

## <a name="instructions"></a>指示

1. Permita que el equipo habilite el dictado. Para ello, vaya a configuración de Windows, seleccione "privacidad", "voz", seguido de "entrada manuscrita & escribiendo" y active los servicios de voz y sugerencias de escritura.

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. 登入 [Azure 入口網站](https://portal.azure.com/)。 Una vez que haya iniciado sesión, haga clic en crear un recurso, busque "Language Understanding" y haga clic en entrar.

    ![mrlearning-Speech-CH4-1-Step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. Haga clic en el botón **crear** para crear una instancia de este servicio.

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    Asigne un **nombre**al recurso, por ejemplo, *Speech-SDK-Learning-Module*. En **suscripción**, seleccione *pago por* uso o *pista gratuita* si tiene una cuenta de prueba. A continuación, cree un nuevo **grupo de recursos** . para ello, haga clic en el vínculo **crear nuevo** , escriba un nombre, por ejemplo, *HoloLens-2-tutoriales-Resource-Group*y haga clic en el botón **Aceptar** .

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. Seleccione la **Ubicación de creación** y la **ubicación en tiempo de ejecución**. Para este tutorial, use *(EE. UU.) oeste de EE. UU.* y luego elija *F0 (5 llamadas por segundo, 10 000 llamadas al mes)* para el plan de tarifa de **creación** y el plan de tarifa **en tiempo de ejecución**. Por último, haga clic en el botón **crear** para crear el recurso, así como el nuevo grupo de recursos.

    ![mrlearning-Speech-CH4-1-Step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >Después de hacer clic en el botón crear, tendrá que esperar a que se cree el servicio, lo que puede tardar unos minutos.

5. Una vez completado el proceso de creación de recursos, verá el mensaje **se ha completado la implementación**.

    ![mrlearning-Speech-CH4-1-Step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. Con la misma cuenta de usuario, inicie sesión en el portal de [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) , seleccione su país y acepte los términos de uso.

    >[!NOTE]
    >Al llegar al portal de Language Understanding, es posible que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure Portal. Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la página de bienvenida para buscar y hacer clic en el botón "crear LUIS" de la aplicación.

7. Una vez que haya iniciado sesión, haga clic en mis aplicaciones (si no está actualmente en esa sección). Después, puede hacer clic en crear nueva aplicación. Asigne a la nueva aplicación el nombre "módulo de aprendizaje de SDK de Speech". Agregue "Speech SDK Learning Module" al campo Descripción. A continuación, haga clic en "listo".

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la "referencia cultural" al idioma adecuado.

8. Haga clic en "compilar" en la parte superior derecha.

9. En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en "crear nuevo intento" y asígnele el nombre "PressButton".

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >Es importante usar los nombres de los intentos y las entidades que se usan en este tutorial, ya que la aplicación Lunarcom hará referencia a ellos por su nombre.

    >[!NOTE]
    >Ahora debería tener 2 intenciones: "PressButton" y "none".

10. En activos de la aplicación de la izquierda, seleccione "entidades", haga clic en "crear nueva entidad", asígnele el nombre "acción" y mantenga el tipo de entidad como "simple".

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. Vuelva a hacer clic en "crear nueva entidad" y asígnele el nombre "destino". CONSERVE también el tipo de entidad como "simple".

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en el intento de "PressButton" que creó en el paso 10.

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar valores de entidad".

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    Haga clic en la "Escriba un ejemplo..." . A continuación, escriba el siguiente grabaciones:

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar nombres de entidad".

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. Asegúrese de que cada uno de los 10 grabaciones tenga las siguientes etiquetas de entidad en los lugares siguientes en 1). al hacer clic en palabras que no están etiquetadas y, en el menú emergente, seleccionando "quitar etiqueta" y 2). al hacer clic en las palabras que deben etiquetarse y, en el menú emergente, seleccione la etiqueta adecuada.

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. Ahora, para publicar el modelo, haga clic en "entrenar" en la parte superior derecha. Después, una vez finalizado el procesamiento, haga clic en "probar" en la parte superior derecha.

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. Escriba en "seleccionar el botón de inicio" en el cuadro de texto.

    >[!NOTE]
    >No hemos agregado "Select" como acción en ninguno de nuestros grabaciones, pero si hace clic en "inspeccionar", el modelo reconoció "Select" como entidad de acción.
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. Haga clic en "publicar" en la parte superior derecha. Asegúrese de que la lista desplegable indica "producción" y haga clic en "publicar" en el menú emergente.

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. Una vez publicada, aparecerá una barra verde en la parte superior de la página. Haga clic en la barra verde para ver la página "administrar".

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. Haga clic en "claves y puntos de conexión" en "configuración de la aplicación" a la izquierda. A continuación, establezca la lista desplegable "publicar en" como "producción". Establezca la zona horaria para que coincida con la suya y active la casilla para incluir todas las puntuaciones de intención previstas. Por último, haga clic en "asignar recurso".

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. Seleccione inquilino en la primera lista desplegable y seleccione "pago por uso" en la lista desplegable nombre de suscripción. En el nombre del recurso LUIS, elija el recurso que se creó anteriormente en los pasos 1-5. A continuación, haga clic en "asignar recurso".

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >Asegúrese de copiar y guardar la dirección URL del punto de conexión asociada con el recurso que acaba de asignar para que sea fácilmente accesible para la sección siguiente.

    >[!NOTE]
    >En el nombre del inquilino, coloque su corporación o el perfil que creó para esta aplicación.

22. Ahora, abra la nueva aplicación en Unity y seleccione el objeto de Lunarcom_Base de la jerarquía. Haga clic en "Agregar componente" en el panel Inspector y busque y seleccione "LunarcomIntentRecognizer".

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. En el campo punto de conexión Luis de "LunarcomIntentRecognizer" en el panel Inspector, escriba la dirección URL del punto de conexión que guardó en el paso 22.

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >En el componente "LunarcomOfflineRecognizer" del panel Inspector, asegúrese de que está seleccionado "Deshabilitar" para "SimulateOfflineMode"; de lo contrario, no funcionará la prueba del programa.

24. Presione el botón reproducir en el editor de Unity y haga clic en el botón Rocket para iniciar el reconocimiento de intenciones. En la frase, haga clic en el botón iniciar Rocket.

    >[!NOTE]
    >La aplicación reconoció la función deseada y activó el botón Rocket.
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>恭喜！

En esta lección ha aprendido a agregar comandos de voz con tecnología de AI. Ahora el programa puede reconocer la intención de los usuarios, incluso si no son comandos de voz precisos.
