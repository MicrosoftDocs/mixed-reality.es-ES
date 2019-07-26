---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485785"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Configuración del propósito y la comprensión del lenguaje natural

En esta lección, exploraremos la característica de intención del servicio de voz de Azure. La característica de intención nos permite equipar nuestra aplicación con comandos de voz con tecnología de AI, donde los usuarios pueden indicar comandos de voz no específicos y seguir teniendo la intención entendida por el sistema. En esta lección, se configurará nuestro portal de LUIS de Azure, se configurará nuestra intención/entidades/grabaciones, se publicará nuestro recurso de intención, se conectará la aplicación de Unity a nuestro recurso de intención y se realizará nuestra primera llamada de API de intención.

## <a name="objectives"></a>Objetivos

- Obtenga información sobre cómo configurar la intención y el lenguaje natural en nuestra aplicación.
- Aprenda a configurar el portal de LUIS de Azure
- Aprenda a configurar la intención, las entidades y los grabaciones en Azure

## <a name="instructions"></a>Instrucciones
1. Permitir que la máquina habilite el dictado para ello, vaya a configuración de Windows, seleccione "privacidad", "voz" y, finalmente, "entrada manuscrita & escribir" y Active servicios de voz y sugerencias de escritura.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. Inicie sesión en el [portal de Azure](https://portal.azure.com/). Una vez que haya iniciado sesión, haga clic en crear un recurso y busque "Language Understanding" y haga clic en entrar.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Seleccione el botón crear para crear una instancia de este servicio. Asigne al proyecto el nombre "Speech_SDK_Learning_Module" y seleccione "pago por uso".

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Seleccione su región.  Para este tutorial, seleccione "(EE. UU.) oeste de EE. UU.". A continuación, elija "F0" para el plan de tarifa. Ahora haga clic en "crear" (que se encuentra en la esquina inferior izquierda) para crear el recurso.

>  Nota: una vez que haya hecho clic en "crear", tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

5. Una vez que se crea el recurso, aparecerá una notificación en el portal. Haga clic en esta notificación y seleccione "ir a recurso".

6. En la página "Inicio rápido" del servicio "LUIS API", navegue hasta el primer paso, tome las "teclas" y haga clic en "claves" (también puede conseguirlo haciendo clic en el hipervínculo azul "Keys", que se muestra en la imagen siguiente). Esto revelará el servicio, "claves". Guarde una copia de una de las claves para poder usarla más adelante en la aplicación.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. De nuevo en la página "Inicio rápido" de la sección 2b, haga clic en "portal de Language Understanding" (que se muestra en la imagen anterior) para redirigirse a la página web que usará para crear el nuevo servicio, dentro de la aplicación LUIS.

> Nota: Al llegar al "portal de Language Understanding", es posible que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure Portal. Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la Página principal, para buscar y hacer clic en el botón "crear LUIS" de la aplicación.

8. Una vez que haya iniciado sesión, haga clic en mis aplicaciones (si no está en esa sección actualmente). Después, puede hacer clic en crear nueva aplicación. Asigne a la nueva aplicación el nombre "módulo de aprendizaje de SDK de Speech". Agregue "Speech SDK Learning Module" al campo Descripción. A continuación, haga clic en "listo".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Tenga en cuenta Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la "referencia cultural" al idioma adecuado.

9. Haga clic en "compilar" en la parte superior derecha.

10. En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en "crear nuevo intento" y asígnele el nombre "PressButton". 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Nota: Es importante usar los nombres de los intentos y las entidades que se usan en este tutorial, ya que la aplicación Lunarcom hará referencia a ellos por su nombre. 
>
> Nota: ahora debe tener 2 intenciones: "PressButton" y "none".

11. En activos de la aplicación de la izquierda, seleccione "entidades", haga clic en "crear nueva entidad" y asígnele el nombre "acción" y mantenga el tipo de entidad como "simple".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Vuelva a hacer clic en "crear nueva entidad" y asígnele el nombre "destino" y conserve también el tipo de entidad como "simple".

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en el intento de "PressButton" que creó en el paso 10.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar valores de entidad". 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Haga clic en el "Escriba un ejemplo..." mytextbox. A continuación, escriba el siguiente grabaciones: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar nombres de entidad".

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Asegúrese de que cada uno de los 10 grabaciones tenga las siguientes etiquetas de entidad en los lugares siguientes en 1). al hacer clic en palabras que no están etiquetadas y, en el menú emergente, seleccionando "quitar etiqueta" y 2). al hacer clic en las palabras que deben etiquetarse y, en el menú emergente, seleccione la etiqueta adecuada.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. Ahora, para publicar el modelo, haga clic en "entrenar" en la parte superior derecha. Después, una vez finalizado el procesamiento, haga clic en "probar" en la parte superior derecha.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Escriba en "seleccionar el botón de inicio" en el cuadro de texto.

> Nota: no hemos agregado "Select" como acción en ninguno de nuestros grabaciones, pero si hace clic en "inspeccionar", el modelo reconoció "Select" como entidad de acción.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. Ahora, haga clic en "publicar" en la parte superior derecha. Asegúrese de que la lista desplegable indica "producción" y haga clic en "publicar" también en la ventana emergente. 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Una vez publicada, aparecerá una barra verde en la parte superior de la página.  Haga clic en la barra verde para ir a la página "administrar". 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Haga clic en "claves y puntos de conexión" en "configuración de la aplicación" a la izquierda. A continuación, establezca la lista desplegable "publicar en" como "producción". Establezca la zona horaria para que coincida con la suya y active la casilla para incluir todas las puntuaciones de intención previstas. Por último, haga clic en "asignar recurso".

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Seleccione inquilino en la primera lista desplegable y seleccione "pago por uso" en el menú desplegable nombre de la suscripción. En el nombre del recurso LUIS, elija el recurso que se creó anteriormente en los pasos 1-5. A continuación, haga clic en "asignar recurso". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Nota: Asegúrese de copiar y guardar la dirección URL del punto de conexión asociada con el recurso que acaba de asignar para que sea fácilmente accesible para la sección siguiente.
>
> Nota: En el nombre del inquilino, coloque su corporación o el perfil que creó para esta aplicación.

23. Ahora, abra la nueva aplicación en Unity y seleccione el objeto Lunarcom_Base en la jerarquía. Haga clic en "Agregar componente" en el panel Inspector y busque y seleccione "LunarcomIntentRecognizer".

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. En el campo punto de conexión Luis de "LunarcomIntentRecognizer" en el panel Inspector, escriba la dirección URL del punto de conexión que guardó en el paso 22. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Nota: En el componente "LunarcomOfflineRecognizer" del panel Inspector, asegúrese de que está seleccionado "Deshabilitar" para "SimulateOfflineMode"; de lo contrario, no funcionará la prueba del programa. 

25. Presione el botón reproducir en el editor de Unity y haga clic en el botón Rocket para iniciar el reconocimiento de intenciones. En la frase, haga clic en el botón iniciar Rocket.

>  Nota: La aplicación reconoció la función deseada y activó el botón Rocket.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Enhorabuena

En esta lección, hemos aprendido a agregar comandos de voz con tecnología de AI. Ahora el programa puede reconocer la intención de los usuarios, incluso si no son comandos de voz precisos.

