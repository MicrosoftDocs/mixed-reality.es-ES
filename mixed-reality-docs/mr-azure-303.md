---
title: El Sr. y Azure 303 - lenguaje Natural descripción (LUIS)
description: Realice este curso para obtener información sobre cómo implementar Azure Language Understanding Intelligence Service (LUIS) dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, servicio de lenguaje de descripción inteligencia, luis, vr envolventes, hololens,
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605321"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>El Sr. y Azure 303: Comprensión del lenguaje natural (LUIS)

En este curso, obtendrá información sobre cómo integrar la comprensión del lenguaje en una aplicación de realidad mixta con Azure Cognitive Services, con la API de lenguaje de descripción.

![Resultado de laboratorio](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* es un servicio de Microsoft Azure, que proporciona a las aplicaciones la capacidad para realizar el significado fuera de la entrada del usuario, como a través de extracción de lo que una persona es posible que desee en sus propias palabras. Esto se logra a través de machine learning, que comprende y aprende la información de entrada y, a continuación, puede responder con información detallada relevante. Para obtener más información, visite la [página Azure Language Understanding (LUIS)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Una vez completado este curso, tendrá una aplicación de envolventes auriculares de realidad mixta que podrá hacer lo siguiente:

1.  Captura de voz de entrada de usuario, con el micrófono conectado a los auriculares envolventes. 
2.  Enviar el dictado capturado la *Azure Language Understanding Intelligent Service* (*LUIS*). 
3.  Tienen extracción LUIS lo que significa que en la información de envío que se va a analizar e intenta determinar que la intención de la solicitud del usuario se realizará.

Desarrollo incluirá la creación de una aplicación donde el usuario podrá usar voz o que mirar para cambiar el tamaño y el color de los objetos de la escena. No se tratará el uso de los controladores de movimiento.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.

Prepárese para entrenar LUIS varias veces, lo que se trata en [capítulo 12](#chapter-12--improving-your-luis-service). Obtendrá mejores resultados más veces que se ha entrenado LUIS.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>El Sr. y Azure 303: Comprensión del lenguaje natural (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens. Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md)
- [El SDK más reciente de Windows 10](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Un conjunto de auriculares con micrófono integrado (si no tienen los auriculares altavoces y un micrófono integrado)
- Acceso a Internet para el programa de instalación de Azure y la recuperación de LUIS

## <a name="before-you-start"></a>Antes de empezar

1.  Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación). 
2.  Para permitir que la máquina para permitir dictado, vaya a **Windows Configuración > privacidad > voz de tinta & escribir** y pulse en el botón **activar servicios de voz y escritura sugerencias**.
3.  El código de este tutorial le permitirá grabar desde el **dispositivo de micrófono predeterminado** establecida en el equipo. Asegúrese de que el dispositivo de micrófono predeterminado se establece como el que desea usar para capturar la voz.
4.  Si los auriculares tienen un micrófono integrado, asegúrese de que la opción *"Cuando wear mi auriculares, vaya a auriculares con micrófono"* está activado en el *Portal de realidad mixta* configuración.

    ![Configuración de auriculares envolventes](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capítulo 1: configurar el Portal de Azure

Para usar el *Language Understanding* service en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.

1.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Language Understanding*y haga clic en **ENTRAR**. 

    ![Crear recurso de LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.
 
3.  La nueva página a la derecha proporcionará una descripción del servicio en la comprensión del lenguaje. En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una instancia de este servicio.

    ![Creación del servicio LUIS - aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  Una vez que ha hecho clic en crear:

    1. Insertar el elemento **nombre** para esta instancia de servicio.
    2. Seleccione un **suscripción**.
    3. Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *LUIS Service*, un nivel gratuito (denominado F0) debe estar disponible para usted. La asignación gratuita debe ser más que suficiente para este curso.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos cursos) en un grupo de recursos comunes). 

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    7. Selecciona **Crear**.

        ![Crear servicio LUIS - proporcionados por el usuario](images/AzureLabs-Lab3-03.png)
 
5.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.
6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal. 
 
    ![Nueva imagen de la notificación de Azure](images/AzureLabs-Lab3-04.png)

7.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![Notificación de creación de recurso correcta](images/AzureLabs-Lab3-05.png)
 
8.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia del servicio LUIS. 
 
    ![Acceso a las claves de LUIS](images/AzureLabs-Lab3-06.png)

9.  En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través del uso clave del servicio en la de suscripción.
10. Desde el *inicio rápido* página, de su *LUIS API* de servicio, navegue hasta el primer paso, *obtener las claves*y haga clic en **claves** (también puede lograr esto, haga clic en el hipervínculo azul claves, ubicado en el menú de navegación de servicios, indicado por el icono de llave). Esto revelará su servicio *claves*.
11. Realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto. 
12. En el *servicio* página, haga clic en *Portal de Language Understanding* se redirijan a la página Web que usará para crear su nuevo servicio en la App LUIS. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capítulo 2: Portal de Language Understanding

En esta sección obtendrá información sobre cómo hacer una App LUIS en el Portal de LUIS. 

> [!IMPORTANT]
> Tenga en cuenta que la configuración de la *entidades*, *intenciones*, y *grabaciones de voz* dentro de este capítulo es sólo el primer paso para crear el servicio LUIS: también deberá reciclar el servicio, varias veces, por lo que para que sea más precisa. Reciclaje del servicio se trata en el [último capítulo](#chapter-12--improving-your-luis-service) de este curso, así que asegúrese de que lo complete.

1.  Cuando se alcanza el *Portal de Language Understanding*, es posible que deba iniciar sesión, si no está ya, con las mismas credenciales que el portal de Azure. 

    ![Página de inicio de sesión de LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Si se trata de la primera vez que usa LUIS, deberá desplazarse hacia abajo hasta la parte inferior de la página de bienvenida, para buscar y haga clic en el **aplicación LUIS crear** botón.

    ![Crear página de aplicación de LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Una vez iniciada la sesión, haga clic en **mis aplicaciones** (si no estás en esa sección actualmente). A continuación, puede hacer clic en **crear nueva aplicación**.

    ![LUIS - mi imagen de aplicaciones](images/AzureLabs-Lab3-09.png)
 
4.  Asigne a la aplicación un *nombre*.
5.  Si se supone que la aplicación para entender un idioma distinto del inglés, debe cambiar la *referencia cultural* para el idioma adecuado.
6.  Aquí también puede agregar un *descripción* de la nueva aplicación de LUIS.

    ![LUIS - crear una nueva aplicación](images/AzureLabs-Lab3-10.png)

7.  Una vez que presione **realiza**, que va a escribir el *compilar* página de la nueva *LUIS* aplicación.
8.  Hay algunos conceptos importantes para comprender aquí:

    -   *Intención*, representa el método que se llama después de una consulta desde el usuario. Un *intención* puede tener uno o varios *entidades*.
    -   *Entidad*, es un componente de la consulta que describe la información relevante para el *intención*.
    -   *Grabaciones de voz*, son ejemplos de consultas proporcionado por el desarrollador, se usará ese LUIS para entrenar a sí mismo.

Si estos conceptos no son perfectamente borrar, no se preocupe, como este curso aclarar ellos aún más en este capítulo.

Comenzará creando la *entidades* necesarios para compilar este curso.

9.  En el lado izquierdo de la página, haga clic en *entidades*, a continuación, haga clic en **crear nueva entidad**.

    ![Crear nueva entidad](images/AzureLabs-Lab3-11.png)

10. Llame a la nueva entidad *color*, establezca su tipo en *Simple*, a continuación, presione **realiza**.

    ![Crear entidad simple - color](images/AzureLabs-Lab3-12.png)
 
11. Repita este proceso para crear tres (3) más Simple entidades denominadas:

    -   *upsize*
    -   *downsize*
    -   *target*

El resultado debería ser similar a la imagen siguiente:

![Resultado de la creación de la entidad](images/AzureLabs-Lab3-13.png)
 
En este momento puede comenzar a crear *intenciones*. 

> [!WARNING]
> No elimine el **ninguno** intención.

12. En el lado izquierdo de la página, haga clic en **intenciones**, a continuación, haga clic en **crear nuevo intento**.

    ![Crear nuevas plataformas intents](images/AzureLabs-Lab3-14.png)

13. Llame al nuevo *intención* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Esto *intención* nombre se usa dentro del código más adelante en este curso, así que para obtener mejores resultados, use este nombre tal y como se proporciona.

Una vez que confirme el nombre que se le dirigirá a la página de intenciones.

![LUIS - página de intenciones](images/AzureLabs-Lab3-15.png)

Observará que hay un cuadro de texto que le pide al tipo de 5 o más diferente *grabaciones de voz*.

> [!NOTE]
> LUIS convierte todas las grabaciones de voz a minúsculas.

14. Inserte el siguiente *Utterance* en el cuadro de texto superior (actualmente con el texto *tipo alrededor de 5 ejemplos...* ) y presione **ENTRAR**:

```
The color of the cylinder must be red
```

Observará que el nuevo *Utterance* aparecerán en una lista debajo.

Siguiendo el mismo proceso, inserte las siguientes declaraciones para seis (6):

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Para cada declaración que ha creado, debe identificar las palabras que se deben usar Luis como entidades. En este ejemplo necesita etiquetar todos los colores como un *color* entidad y todos los posibles referencia de un destino como un *destino* entidad.

15. Para ello, intente hacer clic en la palabra *cilindro* en el primer utterance (dictado) y seleccione *destino*.

    ![Identificar objetivos utterance (dictado)](images/AzureLabs-Lab3-16.png)
 
16. Ahora, haga clic en la palabra *rojo* en el primer utterance (dictado) y seleccione *color*.

    ![Identificación de las entidades utterance (dictado)](images/AzureLabs-Lab3-17.png)
 
17. Además, la siguiente línea de etiqueta donde *cubo* debe ser un *destino*, y *negro* debe ser un *color*. Observe también el uso de las palabras *'this'*, *'it'*, y *'este objeto'*, lo que ofrecemos, por lo que tener también tipos no específico de destino disponibles. 

18. Repita el proceso anterior hasta que todas las palabras pronunciadas tienen las entidades etiquetadas como. Vea la siguiente imagen, si necesita ayuda.

    > [!TIP]
    > Al seleccionar las palabras que desea etiquetarlos como entidades:
    > - Para las palabras individuales simplemente haga clic en ellos.
    > - Para un conjunto de dos o más palabras, haga clic al principio y, a continuación, al final del conjunto.

    > [!NOTE]
    > Puede usar el *Tokens vista* botón de alternancia para cambiar entre **entidades / Tokens View**!

19. Los resultados deben ser como se muestra en las imágenes, a continuación, que muestra la **entidades / Tokens View**:

    ![Las vistas de las entidades y los tokens](images/AzureLabs-Lab3-18.png)
  
20. En este momento se presione el **Train** situado en la parte superior derecha de la página y espere el pequeño indicador redondear en él para cambiar a verde. Esto indica que se ha entrenado LUIS correctamente para que reconozca esta intención.

    ![LUIS "Train"](images/AzureLabs-Lab3-19.png)
 
21. Como ejercicio para usted, cree un nuevo intento llamado **ChangeObjectSize**, con las entidades *destino*, *convertir*, y *reducir el tamaño de*.
22. Siguiendo el mismo proceso que la intención anterior, inserte las siguientes declaraciones para ocho (8) para *tamaño* cambiar:

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. El resultado debería ser como el de la imagen siguiente:

    ![Configurar los Tokens ChangeObjectSize / entidades](images/AzureLabs-Lab3-20.png) 

24. Una vez tanto intenciones **ChangeObjectColor** y **ChangeObjectSize**, se han creado y entrenado, haga clic en el **publicar** botón encima de la página.

    ![Publicar servicio LUIS](images/AzureLabs-Lab3-21.png)

25. En el *publicar* página se finalizar y publicar su App LUIS para que el código puede tener acceso a.

    1. Establecer la lista *Publish To* como **producción**.
    2. Establecer el *Timezone* a su zona horaria.
    3. Active la casilla de verificación **incluir todas las puntuaciones intención puede predecir**.
    4. Haga clic en **publicar en la ranura de producción**.

        ![Configuración de publicación](images/AzureLabs-Lab3-22.png)

26. En la sección *recursos y las claves*:

    1.  Seleccione la región que se configuró para la instancia de servicio en el Portal de Azure.
    2.  Observará un **Starter_Key** elemento a continuación, pasar por alto.
    3.  Haga clic en **Agregar clave** e inserte el *clave* que obtuvo en el Portal de Azure al crear la instancia del servicio. Si se registran los de Azure y el portal de LUIS en el mismo usuario, se le proporcionará los menús desplegables para *nombredeinquilino*, *nombre de la suscripción*y el *clave* que desea usar () tendrá el mismo nombre que proporcionó anteriormente en el Portal de Azure.

    > [!IMPORTANT] 
    > Debajo de la directiva *extremo*, realice una copia del punto de conexión correspondiente a la clave ha insertado, pronto podrá utilizarla en el código.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capítulo 3: configurar el proyecto de Unity

El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **New**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab3-24.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity, insertar **MR_LUIS**. Asegúrese de que el tipo de proyecto se establece en **3D**. Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz). A continuación, haga clic en **crear un proyecto**.

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a Editar > Preferencias y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab3-26.png)
 
4.  A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Vaya a **archivo > configuración de compilación** y asegúrese de que:

    1. **Dispositivo de destino** está establecido en **cualquier dispositivo**

        > Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.

    2. **Tipo de compilación** está establecido en **D3D**
    3. **SDK** está establecido en **instalada más reciente**
    4. **Versión de Visual Studio** está establecido en **instalada más reciente**
    5. **Compilar y ejecutar** está establecido en **máquina Local**
    6. Guarde la escena y agregarlo a la compilación.

        1. Hacer esto seleccionando **agregar escenas abierto**. Aparecerá el guardado de la ventana.
        
            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab3-28.png)

        2. Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab3-29.png)

        3. Abra el recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_LuisScene**, a continuación, presione **guardar**.

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab3-30.png)

    7. El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra. 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab3-31.png) 
 
7. En este panel, es necesario comprobar algunas opciones de configuración:

    1. En el **otra configuración** pestaña:

        1. **Versión en tiempo de ejecución de secuencias de comandos** debe ser **estable** (.NET 3.5 equivalente).
        2. **Scripting de back-end** debe ser **.NET**
        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab3-32.png)
      
    2. Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        1. **InternetClient**
        2. **Micrófono**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab3-33.png)

    3. Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab3-34.png)

8.  En *configuración de compilación* _Unity C#_  proyectos ya no está atenuada; Marque la casilla situada junto a esto. 
9.  Cierre la ventana de configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).

## <a name="chapter-4--create-the-scene"></a>Capítulo 4: crear la escena

> [!IMPORTANT]
> Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importarlo en el proyecto como un [paquete personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5--create-the-microphonemanager-class). 

1.  Haga clic en un área vacía de la *jerarquía Panel*, en **objeto 3D**, agregue un **plano**.

    ![Crear un plano.](images/AzureLabs-Lab3-35.png)

2.  Tenga en cuenta que cuando haga doble clic en el *jerarquía* nuevo para crear más objetos, si sigue teniendo el último objeto seleccionado, el objeto seleccionado será el elemento primario del objeto nuevo. Evitar esto, hace clic en un espacio vacío dentro de la jerarquía y, a continuación, haciendo clic en.

3.  Repita el procedimiento anterior para agregar los siguientes objetos:

    1. *Sphere*
    2. *Cilindro*
    3. *Cubo*
    4. *Texto 3D*

4.  La escena resultante *jerarquía* debe ser como el de la imagen siguiente:

    ![Configuración de la jerarquía escena.](images/AzureLabs-Lab3-36.png)
 
5.  Haga clic en el **cámara principal** para seleccionarlo, examine el *Panel Inspector* , verá el objeto de cámara con todos los sus componentes.
6.  Haga clic en el **Agregar componente** situado en la parte inferior de la *Panel Inspector*.

    ![Agregar origen de Audio](images/AzureLabs-Lab3-37.png)
 
7.  Busque el componente denominado *origen Audio*, como se indicó anteriormente.
8.  Además, asegúrese de que el *transformar* componente de la cámara principal se establece en (0,0,0), esto puede hacerse presionando el **engranaje** icono situado junto a la cámara *transformar* componente y seleccione **restablecer**. El *transformar* componente debería entonces el aspecto siguiente:

    1.  *Posición* está establecido en **0, 0, 0**.
    2.  *Rotación* está establecido en **0, 0, 0**.

    > [!NOTE] 
    > Para el Microsoft HoloLens, deberá cambiar también los siguientes valores, que forman parte de la **cámara** componente, que se encuentra en su **cámara principal**:
    > - **Borrar las marcas de:** Color sólido.
    > - **En segundo plano** ' negro, alfa 0': código de color hexadecimal: #00000000.

9.  Haga clic en el **plano** para seleccionarlo. En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:

    |       | Transformar - *posición* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. Haga clic en el **esfera** para seleccionarlo. En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:

    |       | Transformar - *posición* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. Haga clic en el **cilindro** para seleccionarlo. En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:

    |       | Transformar - *posición* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. Haga clic en el **cubo** para seleccionarlo. En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:

    |        | Transformar - *posición* |       |  \| |       | Transformar - *rotación* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Haga clic en el **nuevo texto** objeto para seleccionarlo. En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:

    |       | Transformar - *posición* |       |  \| |       | Transformar - *escala* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. Cambio **Font Size** en el **texto de la malla** al **50**.
15. Cambiar el *nombre* de la **texto de la malla** objeto **texto dictado**.

    ![Crear objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. La estructura del Panel de la jerarquía debe ser ahora similar al siguiente:

    ![texto de la malla en la vista de escena](images/AzureLabs-Lab3-38b.png)


17. La escena final debe parecerse a la imagen siguiente:

    ![La vista de escena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capítulo 5: crear la clase MicrophoneManager

Es el primer Script que se va a crear el *MicrophoneManager* clase. De este modo, creará el *LuisManager*, el *comportamientos* (clase), por último, el *que mirar* clase (si quiere, puede crear todos estos ahora, aunque se tratarán como llegar a cada capítulo).

El *MicrophoneManager* clase es responsable de:

-   Detectar el dispositivo de grabación conectado al equipo (lo que sea el valor predeterminado) o auriculares.
-   Captura de audio (voces) y use el dictado para almacenarla como una cadena.
-   Una vez que se ha pausado la voz, enviar el dictado a la *LuisManager* clase. 

Para crear esta clase: 

1.  Haga clic en el *Panel del proyecto*, **crear > carpeta**. Llame a la carpeta **Scripts**. 

    ![Crear carpeta de Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Con el **Scripts** carpeta creada, haga doble clic en él para abrirlo. A continuación, dentro de esa carpeta, con el botón secundario, **crear > C# Script**. Nombre de la secuencia de comandos *MicrophoneManager*. 

3.  Haga doble clic en *MicrophoneManager* para abrirlo con *Visual Studio*.
4.  Agregue los siguientes espacios de nombres en la parte superior del archivo:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *MicrophoneManager* clase:

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  El código para *Awake()* y *Start()* métodos ahora debe agregarse. Estos se llamará cuando se inicializa la clase:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  Ahora tiene el método que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la *LuisManager* (clase), que se compila en breve. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Agregar un *controlador dictado* que se invocará cuando se detiene la voz. Este método pasará el texto dictado a la *LuisManager* clase.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Eliminar el *Update()* método puesto que esta clase no lo usará.

9.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

    > [!NOTE]
    > En este momento aparece un error que aparecen en la *Panel de consola del Editor de Unity*. Esto es porque el código hace referencia a la *LuisManager* clase que se creará en el próximo capítulo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capítulo 6: crear la clase LUISManager

Es el momento de crear el *LuisManager* (clase), lo que hará que la llamada al servicio Azure LUIS. 

El propósito de esta clase se va a recibir el texto dictado el *MicrophoneManager* clase y enviarlo a la *Azure Language Understanding API* para analizarlos.

Esta clase se deserializará la *JSON* respuesta y llamar a los métodos adecuados de la *comportamientos* clase para desencadenar una acción.

Para crear esta clase: 

1.  Haga doble clic en el **Scripts** carpeta para abrirla. 
2.  Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos *LuisManager*. 
3.  Haga doble clic en el script para abrirlo con Visual Studio.
4.  Agregue los siguientes espacios de nombres en la parte superior del archivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Se iniciará mediante la creación de tres clases **dentro de** el *LuisManager* clase (dentro del mismo archivo de script, por encima del *Start()* método) que representará deserializado Respuesta JSON de Azure.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  A continuación, agregue las siguientes variables dentro de la *LuisManager* clase:
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Asegúrese de que va a colocar el punto de conexión de LUIS en ahora (que tendrá desde el portal de LUIS).

8.  El código para el *Awake()* método ahora debe agregarse. Este método se llamará cuando se inicializa la clase:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Ahora tiene los métodos de esta aplicación se usa para enviar el dictado recibido desde el *MicrophoneManager* clase *LUIS*y, a continuación, recibir y deserializar la respuesta. 
10. Una vez determinado el valor de la intención y las entidades asociadas, se pasan a la instancia de la *comportamientos* clase para desencadenar la acción deseada.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Crear un nuevo método denominado *AnalyseResponseElements()* que leerá resultante *AnalysedQuery* y determinar las entidades. Una vez que se determinan las entidades, se pasará a la instancia de la *comportamientos* clase que se utiliza en las acciones.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Eliminar el *Start()* y *Update()* métodos, ya que esta clase no los utilizará.

12. Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

> [!NOTE]
> En este punto se dará cuenta de varios errores que aparecen en la *Panel de consola del Editor de Unity*. Esto es porque el código hace referencia a la *comportamientos* clase que se creará en el próximo capítulo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capítulo 7: crear la clase de comportamientos

El *comportamientos* clase desencadenará las acciones con las entidades proporcionadas por el *LuisManager* clase.

Para crear esta clase: 

1.  Haga doble clic en el **Scripts** carpeta para abrirla. 
2.  Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos *comportamientos*. 
3.  Haga doble clic en el script para abrirlo con *Visual Studio*.
4.  A continuación, agregue las siguientes variables dentro de la *comportamientos* clase:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Agregar el *Awake()* código del método. Este método se llamará cuando se inicializa la clase:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  Los siguientes métodos son invocados por la *LuisManager* clase (que ha creado anteriormente) para determinar qué objeto es el destino de la consulta y, a continuación, desencadenar la acción apropiada.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Agregar el *FindTarget()* método para determinar cuál de los *GameObjects* es el destino de la intención de actual. Este método el valor predeterminado es el destino de la *GameObject* que se va a "gazed" Si no se define ningún destino explícita en las entidades.

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Eliminar el *Start()* y *Update()* métodos, ya que esta clase no los utilizará.

8.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Capítulo 8: crear la clase de mirada

La clase último que necesitará para completar esta aplicación es el *que mirar* clase. Esta clase actualiza la referencia a la *GameObject* actualmente en foco visuales del usuario.

Para crear esta clase: 

1.  Haga doble clic en el **Scripts** carpeta para abrirla. 
2.  Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**. Nombre de la secuencia de comandos *que mirar*. 
3.  Haga doble clic en el script para abrirlo con *Visual Studio*.
4.  Inserte el siguiente código para esta clase:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-9--completing-the-scene-setup"></a>Capítulo 9: finalización de la configuración de la escena

1.  Para completar la instalación de la escena, arrastre cada script que ha creado desde la carpeta Scripts para la **cámara principal** objeto en el *jerarquía Panel*.
2.  Seleccione el **cámara principal** y examine el *Panel Inspector*, podrá ver cada script que se ha conectado y observará que hay parámetros en cada secuencia de comandos que todavía han de establecerse.

    ![Establecer los destinos de referencia de la cámara.](images/AzureLabs-Lab3-41.png)

3.  Para establecer estos parámetros correctamente, siga estas instrucciones:

    1. *MicrophoneManager*:

        - Desde el *jerarquía Panel*, arrastre el **texto dictado** objeto en el **texto dictado** cuadro del valor de parámetro.

    2. *Comportamientos*, desde el *jerarquía Panel*:

        - Arrastre el **esfera** objeto en el *esfera* cuadro del destino de referencia.
        - Arrastre el **cilindro** en el *cilindro* cuadro del destino de referencia.
        - Arrastre el **cubo** en el *cubo* cuadro del destino de referencia.

    3. *Gaze*:

        - Establecer el *que mirar Max distancia* a **300** (si aún no está). 

4.  El resultado debería ser similar a la imagen siguiente:

    ![Ahora que muestra los destinos de referencia de la cámara, establecer.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capítulo 10: prueba en el Editor de Unity

Prueba que se ha implementado correctamente la configuración de la escena.

Asegúrate de lo siguiente:

-   Todos los scripts están conectados a la **cámara principal** objeto. 
-   Todos los campos de la *Panel de Inspector de cámara principal* se asignan correctamente.

1.  Presione el **reproducir** situado en la *Editor de Unity*. La aplicación debe estar ejecutándose dentro de los auriculares envolventes adjunto.

2.  Pruebe algunas declaraciones, como:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Si ve un error en la consola de Unity sobre el dispositivo de audio predeterminado cambia, la escena podría no funcionar según lo previsto. Esto es debido al modo en que el portal de realidad mixta se ocupa de los micrófonos integrados para auriculares que disponen de ella. Si ve este error, basta con detener la escena y vuelva a iniciarlo y todo debería funcionar como se esperaba.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capítulo 11: generar y transferir localmente la solución de UWP

Una vez que se ha asegurado de que la aplicación funciona en el Editor de Unity, está listo para compilar e implementar.

Para compilar:

1.  Guarde la escena actual haciendo clic en **archivo > Guardar**.
2.  Vaya a **archivo > configuración de compilación**.
3.  Marque la casilla llamada **Unity C# proyectos** (útil para ver y depurar el código una vez creado el proyecto de UWP.
4.  Haga clic en **agregar escenas abierto**, a continuación, haga clic en **compilar**.

    ![Ventana de configuración de la compilación](images/AzureLabs-Lab3-43.png)

4.  Se le pedirá que seleccione la carpeta donde desea compilar la solución. 

5.  Crear un *compilaciones* carpeta y dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección. 
6.  Haga clic en **Seleccionar carpeta** para iniciar la compilación en esa ubicación.
 
    ![Crear carpeta compilaciones](images/AzureLabs-Lab3-44.png)
    ![Seleccionar carpeta de compilaciones](images/AzureLabs-Lab3-45.png)
 
7.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), debería abrir un **Explorador de archivos** ventana en la ubicación de la compilación.

Para implementar en el equipo Local:

1.  En *Visual Studio*, abra el archivo de solución que se ha creado en el [capítulo anterior](#chapter-10--test-in-the-unity-editor).
2.  En el **plataforma de solución**, seleccione **x86**, **máquina Local**.
3.  En el **configuración de la solución** seleccione **depurar**.

    > Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo. Sin embargo, necesitará también hacer lo siguiente:
    > - Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la *configuración > red e Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar. 
    > - Asegúrese de **modo de programador** es **en**; se encuentra en *configuración > actualización y seguridad > para los desarrolladores*.

    ![Implementación de aplicación](images/AzureLabs-Lab3-46.png)
 
4.  Vaya a la **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.
5.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.
6.  Una vez iniciado, la aplicación le pedirá que autorice el acceso a la _micrófono_. Use la *controladores de movimiento*, o *entrada de voz*, o el *teclado* presionar el **Sí** botón. 

## <a name="chapter-12--improving-your-luis-service"></a>Capítulo 12: mejorar el servicio LUIS

>[!IMPORTANT] 
> Este capítulo es muy importante y es posible que deba realizar una tras varias veces, le ayudará a mejorar la precisión del servicio LUIS: asegúrese de completar esta.

Para mejorar el grado de conocimiento proporciona LUIS deberá capturar grabaciones de voz nueva y usarlos para volver a entrenar su App LUIS.

Por ejemplo, es posible que haya entrenado LUIS a comprender "Aumentar" y "Convertir", pero no quiere que su aplicación para poder comprender también palabras como "Ampliar"?

Una vez que ha usado la aplicación varias veces, todo lo que dicen será recopilados Luis y está disponible en el PORTAL de LUIS.

1.  Vaya a la aplicación de portal siguiente esto [vínculo](https://www.luis.ai/home)y en el registro.
2.  Una vez haya iniciado sesión con sus Credentials MS, haga clic en su *nombre de la aplicación*.
3.  Haga clic en el **revisar grabaciones de voz de punto de conexión** botón a la izquierda de la página.

    ![Revisar grabaciones de voz](images/AzureLabs-Lab3-47.png)
 
4.  Se mostrará una lista de las palabras pronunciadas que se han enviado a LUIS por su aplicación de realidad mixta.

    ![Lista de declaraciones](images/AzureLabs-Lab3-48.png)
 
Observará algunos resaltado *entidades*. 

Mantenga el puntero sobre cada palabra resaltada, puede revisar las declaraciones y determinar qué entidad ha sido reconocida correctamente, lo que las entidades son erróneas y cuáles se pierden las entidades.

En el ejemplo anterior, se encontró que la palabra "spear" tenía ha resaltado como destino, por lo tanto, es necesario corregir el error, que se realiza mediante el mouse sobre la palabra con el mouse y haga clic en **Quitar etiqueta**.

![Compruebe las grabaciones de voz](images/AzureLabs-Lab3-49.png)
![Quitar etiqueta de imagen](images/AzureLabs-Lab3-50.png)
 
5.  Si encuentra declaraciones que están completamente equivocados, puede eliminarlos mediante la **eliminar** situado a la derecha de la pantalla.

    ![Eliminar grabaciones de voz incorrectos](images/AzureLabs-Lab3-51.png)

6.  O si se siente que LUIS interpreta correctamente la declaración, puede validar su descripción mediante el **agregar a la intención alineado** botón.

    ![Agregar a la intención alineada](images/AzureLabs-Lab3-52.png)

7.  Una vez que haya ordenado todas las palabras pronunciadas mostradas, pruebe y vuelva a cargar la página para ver si hay disponibles más.
8.  Es muy importante que repetir este proceso tantas veces como sea posible mejorar la comprensión de la aplicación. 

**¡Que te diviertas!**

## <a name="your-finished-luis-integrated-application"></a>La aplicación LUIS integrado finalizada

Enhorabuena, compila una aplicación de realidad mixta que aprovecha Azure Language Understanding Intelligence Service, para entender lo que dice un usuario y actuar en esa información.

![Resultado de laboratorio](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

Al usar esta aplicación, puede que observe que si mire el objeto Floor y pida que cambie su color, lo hará. ¿Puede averiguar cómo detener la aplicación si cambia el color de suelo?

### <a name="exercise-2"></a>Ejercicio 2

Intentar extender las capacidades de LUIS y aplicación, agregar funcionalidad adicional para los objetos en la escena; Por ejemplo, crear nuevos objetos en la mirada punto de posicionamiento, dependiendo de cuál es el usuario dice y, a continuación, podrá usar esos objetos junto con los objetos de escena actual, con los comandos existentes. 
