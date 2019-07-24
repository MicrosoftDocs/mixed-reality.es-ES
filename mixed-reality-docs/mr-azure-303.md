---
title: 'MR y Azure 303: comprensión del lenguaje natural (LUIS)'
description: Complete este curso para aprender a implementar Azure Language Understanding Intelligence Service (LUIS) en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, Language Understanding Intelligence Service, Luis, hololens, envolventes, VR
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63555153"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR y Azure 303: Comprensión del lenguaje natural (LUIS)

En este curso, aprenderá a integrar Language Understanding en una aplicación de realidad mixta con Azure Cognitive Services, con la Language Understanding API.

![Resultado de laboratorio](images/AzureLabs-Lab3-000.png)

*Language Understanding (Luis)* es un servicio de Microsoft Azure, que proporciona a las aplicaciones la capacidad de ser el significado de los datos proporcionados por el usuario, como por ejemplo, al extraer lo que una persona podría querer, en sus propias palabras. Esto se consigue a través del aprendizaje automático, que comprende y aprende la información de entrada y, a continuación, puede responder con información detallada, relevante. Para obtener más información, visite la [Página de Azure Language Understanding (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Una vez finalizado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta que podrá hacer lo siguiente:

1.  Capture la voz de entrada del usuario con el micrófono conectado al casco envolvente. 
2.  Envíe el dictado capturado a *Azure Language Understanding Intelligent Service* (*Luis*). 
3.  Tenga el significado de LUIS Extract de la información de envío, que se analizará y se realizará un intento de determinar la intención de la solicitud del usuario.

El desarrollo incluirá la creación de una aplicación en la que el usuario podrá usar la voz o la mirada para cambiar el tamaño y el color de los objetos de la escena. No se tratará el uso de controladores de movimiento.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.

Esté preparado para entrenar a LUIS varias veces, que se trata en el [capítulo 12](#chapter-12--improving-your-luis-service). Obtendrá mejores resultados cuanto más se haya entrenado a LUIS.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>MR y Azure 303: Comprensión del lenguaje natural (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens. Al usar HoloLens, puede observar algún Eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo). Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md)
- [El SDK de Windows 10 más reciente](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Un conjunto de auriculares con micrófono integrado (si el casco no tiene micrófonos y altavoces integrados)
- Acceso a Internet para la instalación de Azure y la recuperación de LUIS

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación). 
2.  Para permitir que el equipo habilite el dictado, vaya a **configuración de Windows > privacidad > voz, entrada manuscrita & escriba** y presione el botón **activar servicios de voz y sugerencias de escritura**.
3.  El código de este tutorial le permitirá grabar desde el dispositivo de **micrófono predeterminado** del equipo. Asegúrese de que el dispositivo de micrófono predeterminado esté establecido como el que desea usar para capturar la voz.
4.  Si el casco tiene un micrófono integrado, asegúrese de que la opción *"al gastar el casco, cambiar al micrófono de auriculares"* está activada en la configuración del *portal de realidad mixta* .

    ![Configuración de auriculares inmersivo](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Capítulo 1: configuración del portal de Azure

Para usar el servicio de *Language Understanding* en Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.

1.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *Language Understanding*y haga clic en **entrar**. 

    ![Crear recurso LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.
 
3.  La nueva página a la derecha proporcionará una descripción del servicio de Language Understanding. En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una instancia de este servicio.

    ![Creación del servicio LUIS: Aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  Una vez que haya hecho clic en crear:

    1. Inserte el **nombre** que desee para esta instancia de servicio.
    2. Seleccione una **suscripción**.
    3. Seleccione el **plan de tarifa** adecuado para usted; si es la primera vez que crea un *servicio Luis*, debe tener a su disposición un nivel gratis (denominado F0). La asignación gratuita debe ser más que suficiente para este curso.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común). 

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    6. También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.
    7. Seleccione **Crear**.

        ![Crear el servicio LUIS: entrada del usuario](images/AzureLabs-Lab3-03.png)
 
5.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.
6.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal. 
 
    ![Nueva imagen de notificación de Azure](images/AzureLabs-Lab3-04.png)

7.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![Notificación de creación de recursos correcta](images/AzureLabs-Lab3-05.png)
 
8.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. Se le dirigirá a la nueva instancia de servicio de LUIS. 
 
    ![Acceso a claves de LUIS](images/AzureLabs-Lab3-06.png)

9.  En este tutorial, la aplicación necesitará realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio.
10. En la página *Inicio rápido* , del servicio de *API de Luis* , navegue hasta el primer paso, grabe *sus claves*y haga clic en **claves** (también puede conseguirlo haciendo clic en las teclas de hipervínculo azul, que se encuentran en el menú de navegación servicios, indicado por icono de clave). Esto revelará las *claves*de servicio.
11. Realice una copia de una de las claves que se muestran, ya que la necesitará más adelante en el proyecto. 
12. En la página *servicio* , haga clic en *Language Understanding portal* para redirigirse a la página web que usará para crear el nuevo servicio, dentro de la aplicación Luis. 

## <a name="chapter-2--the-language-understanding-portal"></a>Capítulo 2: portal de Language Understanding

En esta sección, aprenderá a crear una aplicación de LUIS en el portal de LUIS. 

> [!IMPORTANT]
> Tenga en cuenta que la configuración de las *entidades*, las *intenciones*y *grabaciones* en este capítulo es solo el primer paso para crear el servicio de Luis: también tendrá que volver a entrenar el servicio, varias veces, para que sea más preciso. El reciclaje del servicio se trata en el [último capítulo](#chapter-12--improving-your-luis-service) de este curso, por lo que debe asegurarse de que lo completa.

1.  Al llegar al *portal de Language Understanding*, puede que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure portal. 

    ![Página de inicio de sesión de LUIS](images/AzureLabs-Lab3-07.png)
 
2.  Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la Página principal, para buscar y hacer clic en el botón **crear aplicación de Luis** .

    ![Página crear aplicación LUIS](images/AzureLabs-Lab3-08.png)
 
3.  Una vez que haya iniciado sesión, haga clic en **mis aplicaciones** (si no está en esa sección actualmente). Después, puede hacer clic en **crear nueva aplicación**.

    ![LUIS: imagen de mis aplicaciones](images/AzureLabs-Lab3-09.png)
 
4.  Asigne un *nombre*a la aplicación.
5.  Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la *referencia cultural* al idioma adecuado.
6.  Aquí también puede Agregar una *Descripción* de la nueva aplicación Luis.

    ![LUIS: creación de una nueva aplicación](images/AzureLabs-Lab3-10.png)

7.  Una vez que presione **listo**, escribirá la página *compilación* de la nueva aplicación *Luis* .
8.  Hay algunos conceptos importantes que debe comprender aquí:

    -   *Intención*, representa el método al que se llamará después de una consulta del usuario. Un *intento* puede tener una o más *entidades*.
    -   *Entidad*, es un componente de la consulta que describe la información relevante para la *intención*.
    -   *Grabaciones*, son ejemplos de consultas proporcionadas por el desarrollador que Luis usará para entrenarse.

Si estos conceptos no están perfectamente claros, no se preocupe, ya que este curso lo aclarará más adelante en este capítulo.

Comenzará creando las *entidades* necesarias para compilar este curso.

9.  En el lado izquierdo de la página, haga clic en *entidades*y, a continuación, haga clic en **crear nueva entidad**.

    ![Crear nueva entidad](images/AzureLabs-Lab3-11.png)

10. Llame al nuevo *color*de entidad, establezca su tipo en *simple*y, después, haga clic en **listo**.

    ![Crear un color de entidad simple](images/AzureLabs-Lab3-12.png)
 
11. Repita este proceso para crear tres (3) entidades más simples denominadas:

    -   *actualizar*
    -   *reducir*
    -   *dirigir*

El resultado debería ser similar a la imagen siguiente:

![Resultado de la creación de entidades](images/AzureLabs-Lab3-13.png)
 
Llegados a este punto, puede empezar a crear *intenciones*. 

> [!WARNING]
> No elimine **ningún** intento.

12. En el lado izquierdo de la página, haga clic en **intenciones y,** a continuación, haga clic en **crear nuevo intento**.

    ![Crear nuevas intenciones](images/AzureLabs-Lab3-14.png)

13. Llame al nuevo *intento* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Este nombre de *intención* se usa en el código más adelante en este curso, por lo que para obtener los mejores resultados, use este nombre exactamente como se indica.

Una vez que confirme el nombre, se le redirigirá a la página de intents.

![LUIS-página de intents](images/AzureLabs-Lab3-15.png)

Observará que hay un cuadro de texto que le pide que escriba 5 o más *grabaciones*diferentes.

> [!NOTE]
> LUIS convierte todos los grabaciones a minúsculas.

14. Inserte el siguiente *utterance* en el cuadro de texto superior (actualmente con el tipo de texto *sobre 5 ejemplos...* ) y presione **entrar**:

```
The color of the cylinder must be red
```

Observará que el nuevo *utterance* aparecerá en una lista debajo de.

Siguiendo el mismo proceso, inserte los seis (6) grabaciones siguientes:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Para cada utterance que haya creado, debe identificar qué palabras deben usar los LUIS como entidades. En este ejemplo, debe etiquetar todos los colores como una entidad de *color* y todas las referencias posibles a un destino como entidad de *destino* .

15. Para ello, intente hacer clic en la palabra *cilindro* en el primer utterance y seleccione *destino*.

    ![Identificación de los destinos de utterance](images/AzureLabs-Lab3-16.png)
 
16. Ahora, haga clic en la palabra *red* del primer utterance y seleccione *color*.

    ![Identificación de las entidades utterance](images/AzureLabs-Lab3-17.png)
 
17. Etiquete la siguiente línea también, donde *Cube* debe ser un *destino*y el *negro* debe ser un *color*. Observe también el uso de las palabras *' this '* , *' it '* y *' this Object '* , que ofrecemos, por lo que para tener también disponibles tipos de destino no específicos. 

18. Repita el proceso anterior hasta que todos los grabaciones tengan las entidades etiquetadas. Si necesita ayuda, consulte la siguiente imagen.

    > [!TIP]
    > Al seleccionar palabras para etiquetarlas como entidades:
    > - Solo tiene que hacer clic en las palabras individuales.
    > - Para un conjunto de dos o más palabras, haga clic en al principio y, a continuación, al final del conjunto.

    > [!NOTE]
    > Puede usar el botón de alternancia de la *vista tokens* para cambiar entre la **vista de entidades y tokens**.

19. Los resultados deben ser tal como se muestra en las imágenes siguientes, mostrando la **vista de entidades o tokens**:

    ![Tokens & vistas de entidades](images/AzureLabs-Lab3-18.png)
  
20. En este punto, presione el botón **entrenar** situado en la parte superior derecha de la página y espere a que el pequeño indicador redondo se convierta en verde. Esto indica que LUIS se ha entrenado correctamente para reconocer este intento.

    ![Entrenar a LUIS](images/AzureLabs-Lab3-19.png)
 
21. Como ejercicio, cree un nuevo intento llamado **ChangeObjectSize**con las entidades *target* *, up*y *reducir*.
22. Siguiendo el mismo proceso que la intención anterior, inserte los ocho (8) grabaciones siguientes para el cambio de *tamaño* :

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

    ![Configuración de las entidades o tokens de ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. Una vez que se han creado y entrenado las opciones intents, **ChangeObjectColor** y **ChangeObjectSize**, haga clic en el botón **publicar** de la parte superior de la página.

    ![Publicar el servicio LUIS](images/AzureLabs-Lab3-21.png)

25. En la página *publicar* , finalizará y publicará la aplicación Luis para que el código pueda acceder a ella.

    1. Establezca la lista desplegable *publicar en* como **producción**.
    2. Establezca la zona *horaria en la* zona horaria.
    3. Active la casilla **incluir todas las puntuaciones de intención**previstas.
    4. Haga clic en **publicar en ranura de producción**.

        ![Configuración de publicación](images/AzureLabs-Lab3-22.png)

26. En la sección *recursos y claves*:

    1.  Seleccione la región que estableció para instancia de servicio en Azure portal.
    2.  Observará un elemento **Starter_Key** a continuación, omítalo.
    3.  Haga clic en **Agregar clave** e inserte la *clave* que obtuvo en Azure portal al crear la instancia de servicio. Si el portal de Azure y LUIS están conectados al mismo usuario, se le proporcionarán menús desplegables para el *nombre del inquilino*, el nombre de la *suscripción*y la *clave* que quiere usar (tendrá el mismo nombre que proporcionó anteriormente en Azure portal).

    > [!IMPORTANT] 
    > Debajo de *punto de conexión*, realice una copia del punto de conexión correspondiente a la clave que ha insertado. lo usará pronto en el código.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Capítulo 3: configuración del proyecto de Unity

Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity* y haga clic en **nuevo**. 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab3-24.png)

2.  Ahora tendrá que proporcionar un nombre de proyecto de Unity, insertar **MR_LUIS**. Asegúrese de que el tipo de proyecto está establecido en **3D**. Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor). A continuación, haga clic en **crear proyecto**.

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab3-25.png)
 
3.  Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**. Vaya a Editar > Preferencias y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab3-26.png)
 
4.  A continuación, vaya a **archivo > configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab3-27.png)
 
5.  Vaya a **archivo > configuración de compilación** y asegúrese de que:

    1. El **dispositivo de destino** se establece en **cualquier dispositivo**

        > Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.

    2. El **tipo de compilación** se establece en **D3D**
    3. **SDK** está establecido en la **versión más reciente instalada**
    4. La **versión de Visual Studio** está establecida en la **más reciente instalada**
    5. **Compilar y ejecutar** está establecido en **equipo local**
    6. Guarde la escena y agréguela a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas**. Aparecerá una ventana de guardar.
        
            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab3-28.png)

        2. Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre Scenes.

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab3-29.png)

        3. Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **MR_LuisScene**y, a continuación, presione **Guardar**.

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab3-30.png)

    7. El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.

6. En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* . 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab3-31.png) 
 
7. En este panel, deben comprobarse algunas opciones de configuración:

    1. En la pestaña **otros valores** :

        1. La **versión de scripting en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).
        2. El **back-end** de scripting debe ser **.net**
        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab3-32.png)
      
    2. En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        1. **InternetClient**
        2. **Micrófono**

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab3-33.png)

    3. Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .

        ![Actualice la configuración de X R.](images/AzureLabs-Lab3-34.png)

8.  De nuevo en la *configuración de compilación* , los proyectos de _Unity C#_  ya no están atenuados; Marque la casilla situada junto a este. 
9.  Cierre la ventana Configuración de compilación.
10. Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).

## <a name="chapter-4--create-the-scene"></a>Capítulo 4: creación de la escena

> [!IMPORTANT]
> Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), impórtelo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo 5](#chapter-5--create-the-microphonemanager-class). 

1.  Haga clic con el botón secundario en un área vacía del *Panel*de jerarquías, en **objeto 3D**, agregar un **plano**.

    ![Cree un plano.](images/AzureLabs-Lab3-35.png)

2.  Tenga en cuenta que al hacer clic con el botón secundario en la *jerarquía* de nuevo para crear más objetos, si todavía tiene el último objeto seleccionado, el objeto seleccionado será el elemento primario del nuevo objeto. Evite este clic con el botón secundario en un espacio vacío dentro de la jerarquía y, a continuación, haga clic con el botón derecho en.

3.  Repita el procedimiento anterior para agregar los objetos siguientes:

    1. *Compartimiento*
    2. *Cerradura*
    3. *BD*
    4. *Texto 3D*

4.  La *jerarquía* de escenas resultante debe ser similar a la de la imagen siguiente:

    ![Configuración de la jerarquía de escenas.](images/AzureLabs-Lab3-36.png)
 
5.  Haga clic con el botón izquierdo en la **cámara principal** para seleccionarla y, en el *Panel de inspector* , verá el objeto de cámara con todos sus componentes.
6.  Haga clic en el botón **Agregar componente** situado en la parte inferior del *panel Inspector*.

    ![Agregar origen de audio](images/AzureLabs-Lab3-37.png)
 
7.  Busque el componente denominado *origen de audio*, como se mostró anteriormente.
8.  Asegúrese también de que el componente de *transformación* de la cámara principal esté establecido en (0,0). para ello, presione el icono de **engranaje** situado junto al componente de *transformación* de la cámara y seleccione **restablecer**. El componente de *transformación* debería tener el siguiente aspecto:

    1.  La *posición* se establece en **0, 0,0**.
    2.  La *rotación* se establece en **0,** 0,0.

    > [!NOTE] 
    > En el caso de Microsoft HoloLens, también deberá cambiar lo siguiente, que forman parte del componente de **cámara** , que se encuentra en la **cámara principal**:
    > - **Borrar marcas:** Color sólido.
    > - **Información general** ' Black, Alpha 0 ' – color Hex: #00000000.

9.  Haga clic con el botón izquierdo en el **plano** para seleccionarlo. En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:

    |       | Transformación: *posición* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **SÍ**                  | **Z** |
    | 0     | -1                     | 0     |


10. Haga clic con el botón izquierdo en la **esfera** para seleccionarlo. En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:

    |       | Transformación: *posición* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **SÍ**                  | **Z** |
    | 2     | 1                      | 2     |

11. Haga clic con el botón izquierdo en el **cilindro** para seleccionarlo. En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:

    |       | Transformación: *posición* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **SÍ**                  | **Z** |
    | -2    | 1                      | 2     |

12. Haga clic con el botón izquierdo en el **cubo** para seleccionarlo. En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:

    |        | Transformación: *posición* |       |  \| |       | Transformación- *giro* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **SÍ**                   | **Z** |  \| | **X** | **SÍ**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Haga clic con el botón izquierdo en el nuevo objeto de **texto** para seleccionarlo. En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:

    |       | Transformación: *posición* |       |  \| |       | Transformación de *escala* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **SÍ**                  | **Z** |  \| | **X** | **SÍ**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0,1   | 0,1                 | 0,1   | 

14. Cambie el **tamaño de fuente** en el componente de malla de **texto** a **50**.
15. Cambie el *nombre* del objeto de **malla de texto** a texto de **dictado**.

    ![Crear objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. La estructura del panel de jerarquías debería tener ahora el siguiente aspecto:

    ![malla de texto en la vista de escenas](images/AzureLabs-Lab3-38b.png)


17. La escena final debe ser similar a la imagen siguiente:

    ![Vista de la escena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Capítulo 5: crear la clase MicrophoneManager

El primer script que va a crear es la clase *MicrophoneManager* . Después, creará el *LuisManager*, la clase de *comportamientos* y, por último, la clase  de miras (no dude en crearlos ahora, aunque se cubrirá cuando llegue a cada capítulo).

La clase *MicrophoneManager* es responsable de:

-   Detección del dispositivo de grabación conectado a los auriculares o al equipo (lo que sea el predeterminado).
-   Capture el audio (voz) y use el dictado para almacenarlo como una cadena.
-   Una vez que se haya pausado la voz, envíe el dictado a la clase *LuisManager* . 

Para crear esta clase: 

1.  Haga clic con el botón derecho en el *panel Proyecto*, **cree > carpeta**. Llame a los **scripts**de la carpeta. 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab3-40.png)
 
2.  Con la  carpeta scripts creada, haga doble clic en ella para abrirla. A continuación, en esa carpeta, haga clic con el botón secundario en **crear > C# script**. Asigne al script el nombre *MicrophoneManager*. 

3.  Haga doble clic en *MicrophoneManager* para abrirlo con *Visual Studio*.
4.  Agregue los siguientes espacios de nombres al principio del archivo:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  A continuación, agregue las siguientes variables dentro de la clase *MicrophoneManager* :

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* . Se llamará cuando se inicialice la clase:

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
 
7.  Ahora necesita el método que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la clase *LuisManager* , que creará pronto. 

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

8.  Agregue un *controlador* de dictado que se invocará cuando la voz se ponga en pausa. Este método pasará el texto de dictado a la clase *LuisManager* .

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
    > Elimine el método *Update ()* , ya que esta clase no lo usará.

9.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

    > [!NOTE]
    > En este punto, observará que aparece un error en el *Panel*de la consola del editor de Unity. Esto se debe a que el código hace referencia a la clase *LuisManager* que creará en el siguiente capítulo.

## <a name="chapter-6--create-the-luismanager-class"></a>Capítulo 6: crear la clase LUISManager

Es el momento de crear la clase *LuisManager* , que realizará la llamada al servicio de Luis de Azure. 

El propósito de esta clase es recibir el texto de dictado de la clase *MicrophoneManager* y enviarlo al *Language Understanding API de Azure* que se va a analizar.

Esta clase deserializará la respuesta *JSON* y llamará a los métodos adecuados de la clase de *comportamientos* para desencadenar una acción.

Para crear esta clase: 

1.  Haga doble clic en  la carpeta scripts para abrirla. 
2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**. Asigne al script el nombre *LuisManager*. 
3.  Haga doble clic en el script para abrirlo con Visual Studio.
4.  Agregue los siguientes espacios de nombres al principio del archivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Comenzará creando tres clases **dentro** de la clase *LuisManager* (dentro del mismo archivo de script, encima del método *Start ()* ) que representará la respuesta JSON deserializada de Azure.

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

6.  A continuación, agregue las siguientes variables dentro de la clase *LuisManager* :
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Asegúrese de colocar el punto de conexión de LUIS en este momento (que tendrá del portal de LUIS).

8.  Ahora es necesario agregar el código para el método *activo ()* . Se llamará a este método cuando se inicialice la clase:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Ahora necesita los métodos que esta aplicación usa para enviar el dictado recibido de la clase *MicrophoneManager* a *Luis*y, a continuación, recibir y deserializar la respuesta. 
10. Una vez que se ha determinado el valor de la intención y las entidades asociadas, se pasan a la instancia de la clase de *comportamientos* para desencadenar la acción deseada.

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
 
11. Cree un nuevo método llamado *AnalyseResponseElements ()* que leerá el *AnalysedQuery* resultante y determine las entidades. Una vez que se determinen esas entidades, se pasarán a la instancia de la clase de *comportamientos* que se va a usar en las acciones.

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
    > Elimine los métodos *Start ()* y *Update ()* , ya que esta clase no los usará.

12. Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

> [!NOTE]
> En este punto, observará que aparecen varios errores en el *Panel*de la consola del editor de Unity. Esto se debe a que el código hace referencia a la clase de *comportamientos* que creará en el siguiente capítulo.

## <a name="chapter-7--create-the-behaviours-class"></a>Capítulo 7: creación de la clase de comportamientos

La clase de *comportamientos* desencadenará las acciones mediante las entidades proporcionadas por la clase *LuisManager* .

Para crear esta clase: 

1.  Haga doble clic en  la carpeta scripts para abrirla. 
2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**. Asigne un nombre a los *comportamientos*del script. 
3.  Haga doble clic en el script para abrirlo con *Visual Studio*.
4.  A continuación, agregue las siguientes variables dentro de la clase de *comportamientos* :

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Agregue el código del método *activo ()* . Se llamará a este método cuando se inicialice la clase:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  La clase *LuisManager* (que ha creado anteriormente) llama a los métodos siguientes para determinar qué objeto es el destino de la consulta y, a continuación, desencadenar la acción adecuada.

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
 
7.  Agregue el método *FindTarget ()* para determinar cuál de *GameObjects* es el destino de la intención actual. Este método usa de forma predeterminada el destino en el *GameObject* que se "mira" si no se define ningún destino explícito en las entidades.

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
    > Elimine los métodos *Start ()* y *Update ()* , ya que esta clase no los usará.

8.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Capítulo 8: crear la clase fijamente

La última clase que necesitará para completar esta aplicación es la clase *fijamente* . Esta clase actualiza la referencia a *GameObject* actualmente en el foco visual del usuario.

Para crear esta clase: 

1.  Haga doble clic en  la carpeta scripts para abrirla. 
2.  Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**. Asigne un nombre *al script.* 
3.  Haga doble clic en el script para abrirlo con *Visual Studio*.
4.  Inserte el código siguiente para esta clase:

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

## <a name="chapter-9--completing-the-scene-setup"></a>Capítulo 9: completar la configuración de la escena

1.  Para completar la instalación de la escena, arrastre cada script que ha creado desde la carpeta scripts hasta el objeto **cámara principal** del *Panel jerarquía*.
2.  Seleccione la **cámara principal** y mire en el *panel del inspector*, podrá ver cada script que ha adjuntado y observará que hay parámetros en cada script que todavía se deben establecer.

    ![Establecer los destinos de referencia de la cámara.](images/AzureLabs-Lab3-41.png)

3.  Para establecer estos parámetros correctamente, siga estas instrucciones:

    1. *MicrophoneManager*:

        - En el *Panel jerarquía*, arrastre el objeto de **texto dictado** al cuadro valor del parámetro de **texto** de dictado.

    2. *Comportamientos*, en el *Panel jerarquía*:

        - Arrastre el objeto **Sphere** al cuadro destino de referencia *Sphere* .
        - Arrastre el **cilindro** al cuadro destino de referencia del *cilindro* .
        - Arrastre el **cubo** al cuadro destino de referencia del *cubo* .

    3. *Mira fijamente*:

        - Establezca la *distancia máxima* de miración en **300** (si aún no lo está). 

4.  El resultado debería ser similar a la imagen siguiente:

    ![Que muestra los destinos de referencia de la cámara, ahora establecido.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Capítulo 10: prueba en el editor de Unity

Compruebe que la configuración de la escena está implementada correctamente.

Asegúrate de lo siguiente:

-   Todos los scripts se adjuntan al objeto de **cámara principal** . 
-   Todos los campos del *panel Inspector de cámara principal* están asignados correctamente.

1.  Presione el botón **reproducir** en el *Editor de Unity*. La aplicación debe ejecutarse dentro de los auriculares inmersivo agregados.

2.  Pruebe unos cuantos grabaciones, como:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Si ve un error en la consola de Unity sobre el cambio del dispositivo de audio predeterminado, es posible que la escena no funcione según lo previsto. Esto se debe a la forma en que el portal de realidad mixta trata los micrófonos integrados para los auriculares que los tienen. Si ve este error, simplemente detenga la escena e iníciela de nuevo y las cosas deberían funcionar según lo previsto.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Capítulo 11: compilar y transferir localmente la solución de UWP

Una vez que se ha asegurado de que la aplicación funciona en el editor de Unity, está listo para compilar e implementar.

Para compilar:

1.  Guarde la escena actual haciendo clic en **archivo > guardar**.
2.  Vaya a **archivo > configuración de compilación**.
3.  Marque el cuadro denominado **proyectos C# de Unity** (útil para ver y depurar el código una vez creado el proyecto de UWP.
4.  Haga clic en **Agregar escenas abiertas**y luego haga clic en compilar.

    ![Ventana Configuración de compilación](images/AzureLabs-Lab3-43.png)

4.  Se le pedirá que seleccione la carpeta en la que desea compilar la solución. 

5.  Cree una  carpeta Compilaciones y, dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección. 
6.  Haga clic en **Seleccionar carpeta** para iniciar la compilación en esa ubicación.
 
    ![Crear carpeta](images/AzureLabs-Lab3-44.png)
    ![de compilaciones Seleccionar carpeta de compilaciones](images/AzureLabs-Lab3-45.png)
 
7.  Una vez que Unity termine de compilar (puede tardar algún tiempo), debe abrir una ventana del **Explorador de archivos** en la ubicación de la compilación.

Para implementar en la máquina local:

1.  En *Visual Studio*, abra el archivo de solución que se creó en el [capítulo anterior](#chapter-10--test-in-the-unity-editor).
2.  En la **plataforma**de la solución, seleccione **x86**, **equipo local**.
3.  En la **configuración de soluciones** , seleccione Depurar.

    > En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP** de HoloLens, que puede encontrarse en la *configuración > red & Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar. 
    > - Asegurarse de que el **modo de desarrollador** está **activado**; se encuentra en *configuración > actualizar & > de seguridad para desarrolladores*.

    ![Implementar aplicación](images/AzureLabs-Lab3-46.png)
 
4.  Vaya al **menú** compilar y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.
5.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para su lanzamiento.
6.  Una vez iniciado, la aplicación le pedirá que autorice el acceso al _micrófono_. Use los *controladores de movimiento*, la *entrada de voz*o el *teclado* para presionar el botón **sí** . 

## <a name="chapter-12--improving-your-luis-service"></a>Capítulo 12: mejorar el servicio de LUIS

>[!IMPORTANT] 
> Este capítulo es increíblemente importante, por lo que es posible que tenga que interated varias veces, ya que le ayudará a mejorar la precisión del servicio LUIS: Asegúrese de que lo completa.

Para mejorar el nivel de comprensión proporcionado por LUIS, debe capturar nuevos grabaciones y usarlos para volver a entrenar su aplicación de LUIS.

Por ejemplo, es posible que haya entrenado a LUIS para comprender "aumento" y "tamaño", pero no desea que la aplicación también entienda palabras como "agrandar"?

Una vez que haya usado la aplicación varias veces, se recopilará todo lo que haya dicho en LUIS y estará disponible en el PORTAL de LUIS.

1.  Vaya a la aplicación de portal que sigue a este [vínculo](https://www.luis.ai/home)e inicie sesión.
2.  Una vez que haya iniciado sesión con sus credenciales de MS, haga clic en el nombre de la *aplicación*.
3.  Haga clic en el botón **revisar extremo grabaciones** situado a la izquierda de la página.

    ![Revisar grabaciones](images/AzureLabs-Lab3-47.png)
 
4.  Se le mostrará una lista de los grabaciones enviados a LUIS por la aplicación de realidad mixta.

    ![Lista de grabaciones](images/AzureLabs-Lab3-48.png)
 
Observará algunas *entidades*resaltadas. 

Al mantener el mouse sobre cada palabra resaltada, puede revisar cada utterance y determinar qué entidad se reconoció correctamente, qué entidades son erróneas y qué entidades se han perdido.

En el ejemplo anterior, se encontró que la palabra "Spear" se resaltó como destino, por lo que era necesario corregir el error, lo que se realiza al mantener el mouse sobre la palabra con el mouse y hacer clic en **quitar etiqueta**.

![Comprobar grabaciones](images/AzureLabs-Lab3-49.png)
![quitar etiqueta de imagen](images/AzureLabs-Lab3-50.png)
 
5.  Si encuentra grabaciones que son completamente incorrectas, puede eliminarlos mediante el botón **eliminar** situado en el lado derecho de la pantalla.

    ![Eliminar grabaciones erróneo](images/AzureLabs-Lab3-51.png)

6.  O bien, si cree que LUIS ha interpretado el utterance correctamente, puede validar su comprensión mediante el botón **Agregar a intento alineado** .

    ![Agregar a intención alineada](images/AzureLabs-Lab3-52.png)

7.  Una vez que haya ordenado todo el grabaciones que se muestra, intente volver a cargar la página para ver si hay más disponibles.
8.  Es muy importante repetir este proceso tantas veces como sea posible para mejorar la comprensión de la aplicación. 

**¡Que te diviertas!**

## <a name="your-finished-luis-integrated-application"></a>Su aplicación integrada de LUIS finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio de inteligencia de Language Understanding de Azure para comprender lo que un usuario dice y actuar sobre esa información.

![Resultado de laboratorio](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

Al usar esta aplicación, es posible que observe que si mira el objeto Floor y pide cambiar su color, lo hará. ¿Puede averiguar cómo evitar que la aplicación cambie el color del piso?

### <a name="exercise-2"></a>Ejercicio 2

Intente ampliar las funcionalidades de LUIS y App, agregando funcionalidad adicional a los objetos de la escena. por ejemplo, cree nuevos objetos en el punto de Miración de la mirada, en función de lo que indique el usuario y, a continuación, podrá usar esos objetos junto con los objetos de la escena actual con los comandos existentes. 
