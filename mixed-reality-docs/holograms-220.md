---
title: MR espacial 220-sonido espacial
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de sonido espacial.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, sonido espacial
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434724"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR espacial 220: sonido espacial

El [sonido espacial](spatial-sound.md) respire la vida en los hologramas y les da presencia en nuestro mundo. Los hologramas se componen de luz y sonido, y si se pierde la visión de los hologramas, el sonido espacial puede ayudarle a encontrarlos. El sonido espacial no es como el sonido típico que se oíría en la radio, sino que se encuentra en el espacio 3D. Con el sonido espacial, puede hacer que los hologramas suenen como si estuvieran detrás, junto a usted o incluso en su cabeza. En este curso, hará lo siguiente:

* Configure el entorno de desarrollo para usar el sonido espacial de Microsoft.
* Use el sonido espacial para mejorar las interacciones.
* Use el sonido espacial junto con la [asignación espacial](spatial-mapping.md).
* Comprenda las prácticas recomendadas de diseño y mezcla.
* Use el sonido para mejorar los efectos especiales y poner al usuario en el mundo de la realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>MR espacial 220: sonido espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).
* Funcionalidad básica C# de programación.
* Debe haber completado los [principios básicos 101](holograms-101.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) requeridos por el proyecto. Requiere Unity 2017,2 o posterior.
  * Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Es posible que esta versión ya no esté actualizada.
  * Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Es posible que esta versión ya no esté actualizada.
  * Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Es posible que esta versión ya no esté actualizada.
* Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Erratas y notas

* "Habilitar Solo mi código" debe estar deshabilitado *(desactivado*) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1: configuración de Unity

### <a name="objectives"></a>Objetivos

* Cambie la configuración de sonido de Unity para usar el sonido espacial de Microsoft.
* Agregue un sonido 3D a un objeto en Unity.

### <a name="instructions"></a>Instrucciones

* Inicia Unity.
* Seleccione **abrir**.
* Navegue hasta el escritorio y busque la carpeta que ha eliminado previamente.
* Haga clic en la carpeta **Starting\Decibel** y, a continuación, presione el botón **Seleccionar carpeta** .
* Espere a que el proyecto se cargue en Unity.
* En el panel **proyecto** , Abra **Scenes\Decibel.Unity**.
* En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.
* En el inspector, expanda **AudioSource** y observe que no hay ninguna casilla **Spatial** .

De forma predeterminada, Unity no carga un complemento de spatializer. En los pasos siguientes se habilitará el sonido espacial en el proyecto.

* En el menú superior de Unity, vaya a **editar > configuración del proyecto > audio**.
* Busque la lista desplegable **complemento de Spatializer** y seleccione **MS HRTF Spatializer**.
* En el panel **jerarquía** , seleccione **HologramCollection > P0LY**.
* En el panel **Inspector** , busque el componente de **origen de audio** .
* Active la casilla **Spatial** .
* Arrastre el control deslizante de **combinación espacial** hasta el modo **3D**o escriba **1** en el cuadro de edición.

Ahora se compilará el proyecto en Unity y se configurará la solución en Visual Studio.

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Haga clic en **Agregar escenas abiertas** para agregar la escena.
3. Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.
4. Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**. De lo contrario, déjelo en **cualquier dispositivo**.
5. Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).
6. Haz clic en **Compilación**.
7. Cree una **nueva carpeta** denominada "app".
8. Haga clic en la carpeta de la **aplicación** .
9. Presione **Seleccionar carpeta**.

Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.

1. Abra la carpeta de la **aplicación** .
2. Abra la **solución de Visual Studio de decibelios**.

Si se implementa en HoloLens:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.
2. Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.
3. Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** . Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.
4. En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**. Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device).

Si se implementa en un auricular envolvente:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.
2. Asegúrese de que el destino de implementación está establecido en **equipo local**.
3. En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capítulo 2: sonido espacial e interacción

### <a name="objectives"></a>Objetivos

* Mejore el realismo del holograma mediante el sonido.
* Dirija la mirada del usuario con el sonido.
* Proporcione comentarios de gestos mediante sonido.

### <a name="part-1---enhancing-realism"></a>Parte 1: mejora del realismo

#### <a name="key-concepts"></a>Conceptos clave

* Spatial los sonidos del holograma.
* Los orígenes de sonido se deben colocar en una ubicación adecuada en el holograma.

La ubicación adecuada para el sonido dependerá del holograma. Por ejemplo, si el holograma es humano, el origen de sonido debe estar situado cerca de la boca y no de los pies.

#### <a name="instructions"></a>Instrucciones

Las instrucciones siguientes conectarán un sonido espacial a un holograma.

* En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.
* En el panel **Inspector** , en el **AudioSource**, haga clic en el círculo situado junto a **AudioClip** y seleccione el **subdesplazamiento** en el elemento emergente.
* Haga clic en el círculo situado junto a **salida** y seleccione **SoundEffects** en el elemento emergente.

El proyecto de decibelios usa un componente **AudioMixer** de Unity para habilitar el ajuste de los niveles de sonido para grupos de sonidos. Al agrupar los sonidos de esta manera, se puede ajustar el volumen global mientras se mantiene el volumen relativo de cada sonido.

* En **AudioSource**, expanda **configuración de sonido 3D**.
* Establezca el **nivel de Doppler** en **0**.

Si se establece el nivel de Doppler en cero, se deshabilitan los cambios de tono causados por el movimiento (el holograma o el usuario). Un ejemplo clásico de Doppler es un coche con movimiento rápido. A medida que el coche se aproxima a un agente de escucha estacionario, aumenta el tono del motor. Cuando pasa el agente de escucha, el paso disminuye con la distancia.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2: dirigir la mirada del usuario

#### <a name="key-concepts"></a>Conceptos clave

* Use el sonido para llamar la atención a los hologramas importantes.
* Los oídos le ayudarán a tener el aspecto de los ojos.
* El cerebro tiene algunas expectativas conocidas.

Un ejemplo de expectativas aprendidas es que las aves suelen estar por encima de los cabezales de los seres humanos. Si un usuario oye un sonido de pájaro, su reacción inicial es buscar. Colocar un pájaro debajo del usuario puede conducir a que se dirija a la dirección correcta del sonido, pero no puede encontrar el holograma en función de la expectativa de necesidad de buscar.

#### <a name="instructions"></a>Instrucciones

Las instrucciones siguientes permiten que P0LY se oculte por detrás, de modo que pueda usar el sonido para buscar el holograma.

* En el panel **jerarquía** , seleccione **administradores**.
* En el panel **Inspector** , busque **controlador de entrada de voz**.
* En **controlador de entrada de voz**, expanda **ocultar**.
* **No cambie ninguna función** a **poliactions. GoHide**.

![Palabra clave: ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3: comentarios de gestos

#### <a name="key-concepts"></a>Conceptos clave

* Proporcionar al usuario la confirmación de gestos positivos mediante el sonido
* No sobrecargar el exceso de sonido del usuario en el camino
* Los sonidos sutiles funcionan mejor: no hagan la experiencia

#### <a name="instructions"></a>Instrucciones

* En el panel **jerarquía** , expanda **HologramCollection**.
* Expanda **EnergyHub** y seleccione **base**.
* En el panel **Inspector** , haga clic en **Agregar componente** y agregue el **controlador de sonido de gesto**.
* En el **controlador de sonido de gestos**, haga clic en el círculo situado junto a **navegación Inicio clip** y **navegación actualizado clip** y seleccione **RotateClick** en el elemento emergente para ambos.
* Haga doble clic en "GestureSoundHandler" para cargar en Visual Studio.

El controlador de sonido de gestos realiza las siguientes tareas:

* Cree y configure un **AudioSource**.
* Coloque **AudioSource** en la ubicación de la **GameObject**adecuada.
* Reproduce el **AudioClip** asociado con el gesto.

#### <a name="build-and-deploy"></a>Compilación e implementación

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Haz clic en **Compilación**.
3. Haga clic en la carpeta de la **aplicación** .
4. Presione **Seleccionar carpeta**.

Compruebe que la barra de herramientas indica "release", "x86" o "x64" y "dispositivo remoto". Si no es así, se trata de la instancia de codificación de Visual Studio. Es posible que tenga que volver a abrir la solución desde la carpeta de la aplicación.

* Si se le solicita, vuelva a cargar los archivos de proyecto.
* Como antes, implemente desde Visual Studio.

Una vez implementada la aplicación:

* Observe cómo cambia el sonido a medida que se desplaza por P0LY.
* Di *"ir a ocultar"* para que P0LY se mueva a una ubicación detrás. Lo encuentra en el sonido.
* Mira la base de la central de energía. Puntee y arrastre hacia la izquierda o hacia la derecha para girar el holograma y observe cómo el sonido que hace clic confirma el gesto.

Nota: hay un panel de texto que se etiquetará junto con usted. Esto contendrá los comandos de voz disponibles que puede usar en este curso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capítulo 3: mapa espacial y de sonido espacial

### <a name="objectives"></a>Objetivos

* Confirme la interacción entre los hologramas y el mundo real mediante el sonido.
* Tapaba sonido con el mundo físico.

### <a name="part-1---physical-world-interaction"></a>Parte 1: interacción del mundo físico

#### <a name="key-concepts"></a>Conceptos clave

* Normalmente, los objetos físicos realizan un sonido al encontrar una superficie u otro objeto.
* Los sonidos deben ser el contexto adecuado dentro de la experiencia.

Por ejemplo, el establecimiento de una copa en una tabla debe hacer un sonido más silencioso que colocar un Boulder en una pieza de metal.

#### <a name="instructions"></a>Instrucciones

* En el panel **jerarquía** , expanda **HologramCollection**.
* Expanda **EnergyHub**y seleccione **base**.
* En el panel **Inspector** , haga clic en **Agregar componente** y agregue **puntear para colocar con el sonido y la acción**.
* En **puntear para colocar con el sonido y la acción**:
  * Active **colocar primario al pulsar**.
  * Establezca el sonido de **selección de ubicación** .
  * Establezca **sonido de recogida** en **recogida**.
  * Presione + en la parte inferior derecha, en la acción **de recogida** y **en la acción de selección de ubicación**. Arrastre EnergyHub desde la escena hasta los campos **ninguno (objeto)** .
    * En **acción de recogida**, haga clic en **ninguna función** -> **EnergyHubBase** -> **ResetAnimation**.
    * En **acción de selección de ubicación**, haga clic en **ninguna función** -> **EnergyHubBase** -> **alseleccionar**.

![Puntee para colocar con el sonido y la acción](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2: oclusión de sonido

#### <a name="key-concepts"></a>Conceptos clave

* El sonido, como Light, puede ser ocluidos.

Un ejemplo clásico es un salón de concierto. Cuando un agente de escucha está fuera del salón y la puerta está cerrada, la música suena silenciada. Normalmente, también hay una reducción del volumen. Cuando se abre la puerta, se oye todo el espectro del sonido en el volumen real. Los sonidos de alta frecuencia suelen absorber más que las bajas frecuencias.

#### <a name="instructions"></a>Instrucciones

* En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.
* En el panel **Inspector** , haga clic en **Agregar componente** y agregue **emisor de audio**.

La clase emisora de audio proporciona las siguientes características:

* Restaura cualquier cambio realizado en el volumen de **AudioSource**.
* Realiza una conexión **física. RaycastNonAlloc** desde la posición del usuario en la dirección del **GameObject** al que se adjunta el **AudioEmitter** .

El método RaycastNonAlloc se usa como optimización del rendimiento para limitar las asignaciones y el número de resultados devueltos.

* Para cada **IAudioInfluencer** encontrada, llama al método **ApplyEffect** .
* Para cada **IAudioInfluencer** anterior que ya no se encuentre, llame al método **RemoveEffect** .

Tenga en cuenta que AudioEmitter se actualiza en las escalas de tiempo humano, en lugar de en cada fotograma. Esto se hace porque los seres humanos generalmente no se mueven lo suficientemente rápido como para que el efecto tenga que actualizarse con más frecuencia que cada trimestre o mitad de segundo. Los hologramas que se destransportan rápidamente de una ubicación a otra pueden interrumpir el efecto.

* En el panel **jerarquía** , expanda **HologramCollection**.
* Expanda **EnergyHub** y seleccione **BlobOutside**.
* En el panel **Inspector** , haga clic en **Agregar componente** y agregue **audio Occluder**.
* En **audio Occluder**, establezca la **frecuencia límite** en **1500**.

Esta configuración limita las frecuencias AudioSource a 1500 Hz y por debajo.

* Establezca el **paso de volumen** en **0,9**.

Esta configuración reduce el volumen de AudioSource al 90% del nivel actual.

Audio Occluder implementa IAudioInfluencer para:

* Aplicar un efecto de oclusión mediante un **AudioLowPassFilter** que se adjunta a la **AudioSource** administrada compre el **AudioEmitter**.
* Aplica la atenuación del volumen a AudioSource.
* Deshabilita el efecto estableciendo una frecuencia de límite neutro y deshabilitando el filtro.

La frecuencia usada como neutra es de 22 kHz (22000 Hz). Esta frecuencia se eligió debido a que está por encima de la frecuencia máxima nominal que puede ser oída por el oído humano, lo que no hace ningún impacto más perceptible en el sonido.

* En el panel **jerarquía** , seleccione **SpatialMapping**.
* En el panel **Inspector** , haga clic en **Agregar componente** y agregue **audio Occluder**.
* En **audio Occluder**, establezca la **frecuencia límite** en **750**.

Cuando hay varios occluders en la ruta de acceso entre el usuario y el **AudioEmitter**, se aplica la frecuencia más baja al filtro.

* Establezca el **paso de volumen** en **0,75**.

Cuando hay varios occluders en la ruta de acceso entre el usuario y el **AudioEmitter**, el paso del volumen a través se aplica de forma aditiva.

* En el panel **jerarquía** , seleccione **administradores**.
* En el panel **Inspector** , expanda **controlador de entrada de voz**.
* En **controlador de entrada de voz**, expanda **gastos de avance**.
* **No cambie ninguna función** a **poliactions. GoCharge**.

![Palabra clave: gastos de avance](images/gocharge.png)

* Amplíe **aquí**.
* **No cambie ninguna función** a **poliactions. Comeback**.

![Palabra clave: viene aquí](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilación e implementación

* Como antes, compile el proyecto en Unity e impleméntelo en Visual Studio.

Una vez implementada la aplicación:

* Por ejemplo, *"go CHARGE"* para que P0LY escriba el centro de energía.

Observe el cambio en el sonido. Debe sonar silenciado y un poco más silencioso. Si puede colocarse con una pared u otro objeto entre usted y el centro de energía, debe observar un mayor silenciamiento del sonido debido a la oclusión del mundo real.

* Supongamos que *"viene aquí"* para que P0LY deje la central de energía y se coloque por delante.

Tenga en cuenta que la oclusión de sonido se quita una vez que P0LY sale del centro de energía. Si todavía está escuchando oclusión, P0LY puede ser ocluidos en el mundo real. Intente cambiar para asegurarse de que tiene una línea de visión clara a P0LY.

### <a name="part-3---room-models"></a>Parte 3: modelos Room

#### <a name="key-concepts"></a>Conceptos clave

* El tamaño del espacio proporciona colas de subliminal que contribuyen a la localización de sonido.
* Los modelos de sala se establecen por**AudioSource**.
* [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona código para establecer el modelo de habitación.
* En el caso de experiencias de realidad mixta, seleccione el modelo de salón que mejor se adapte al espacio real del mundo.

Si va a crear un escenario de realidad virtual, seleccione el modelo de salón que mejor se adapte al entorno virtual.

## <a name="chapter-4---sound-design"></a>Capítulo 4: diseño de sonido

### <a name="objectives"></a>Objetivos

* Comprender las consideraciones para un diseño de sonido eficaz.
* Obtenga información sobre las técnicas y las directrices de combinación.

### <a name="part-1---sound-and-experience-design"></a>Parte 1: diseño de la experiencia y el sonido

En esta sección se describen las consideraciones y directrices de diseño de la experiencia y el sonido clave.

#### <a name="normalize-all-sounds"></a>Normalizar todos los sonidos

Esto evita la necesidad de que el código de caso especial ajuste los niveles de volumen por sonido, lo que puede llevar mucho tiempo y limita la capacidad de actualizar fácilmente los archivos de sonido.

#### <a name="design-for-an-untethered-experience"></a>Diseño para una experiencia de untethered

HoloLens es un equipo untethered Holographic totalmente contenido. Los usuarios pueden usar sus experiencias mientras se mueven. Asegúrese de probar la combinación de audio.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emitir sonido desde ubicaciones lógicas en los hologramas

En el mundo real, un perro no se corteza de su cola y la voz de un hombre no proviene de sus pies. Evite que los sonidos se emitan desde partes inesperadas de los hologramas.

En el caso de los hologramas pequeños, es razonable tener una emisión de sonido desde el centro de la geometría.

#### <a name="familiar-sounds-are-most-localizable"></a>Los sonidos conocidos son más localizables

La voz humana y la música son muy fáciles de localizar. Si alguien llama a su nombre, puede determinar con precisión desde qué dirección se ha recibido la voz y desde dónde está. Los sonidos cortos y desconocidos son más difíciles de localizar.

#### <a name="be-cognizant-of-user-expectations"></a>Cognizant de las expectativas de los usuarios

La experiencia de vida juega una parte en nuestra capacidad de identificar la ubicación de un sonido. Esta es una de las razones por las que la voz humana es especialmente fácil de localizar. Es importante tener en cuenta las expectativas aprendidas del usuario al colocar los sonidos.

Por ejemplo, cuando alguien oye una canción de pájaro, se suele buscar, ya que las aves tienden a estar por encima de la línea de visión (vuelo o en un árbol). No es raro que un usuario Active la dirección correcta de un sonido, sino que mire en la dirección vertical equivocada y se confunda o frustraría cuando no pueda encontrar el holograma.

#### <a name="avoid-hidden-emitters"></a>Evitar emisores ocultos

En el mundo real, si escuchamos un sonido, generalmente podemos identificar el objeto que emite el sonido. También debe tener el valor true en sus experiencias. Puede ser muy difícil para los usuarios oír un sonido, saber desde dónde se origina el sonido y no puede ver un objeto.

Existen algunas excepciones a esta directriz. Por ejemplo, los sonidos ambientales como Crickets en un campo no deben ser visibles. La experiencia de vida nos permite familiarizarse con el origen de estos sonidos sin necesidad de verlo.

### <a name="part-2---sound-mixing"></a>Parte 2: combinación de sonidos

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Destine su combinación para el volumen del 70% en HoloLens

Las experiencias de realidad mixta permiten que los hologramas se vean en el mundo real. También deben permitir escuchar sonidos reales. Un destino de volumen del 70% permite al usuario oír todo el mundo junto con el sonido de su experiencia.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens en 100% de volumen debe estar ahogado a los sonidos externos

Un nivel de volumen del 100% es similar a una experiencia de realidad virtual. Visualmente, el usuario se transporta a un mundo diferente. Lo mismo debe ser un verdadero audible.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Usar el AudioMixer de Unity para ajustar categorías de sonidos

Al diseñar la combinación, a menudo resulta útil crear categorías de sonido y tener la capacidad de aumentar o disminuir el volumen como una unidad. De este modo, se conservan los niveles relativos de cada sonido a la vez que se habilitan los cambios rápidos y sencillos en la combinación global. Entre las categorías comunes se incluyen: efectos sonoros, ambiente, voz y música de fondo.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Mezcle los sonidos en función de la mirada del usuario

A menudo, puede resultar útil cambiar la combinación de sonidos de su experiencia en función de la ubicación de un usuario (o no). Un uso común de esta técnica consiste en reducir el nivel de volumen de los hologramas que están fuera del marco holográfica para que el usuario pueda centrarse más fácilmente en la información que se encuentra delante de ellos. Otro uso es aumentar el volumen de un sonido para atraer la atención del usuario a un evento importante.

#### <a name="building-your-mix"></a>Crear la combinación

Al compilar la combinación, se recomienda empezar con el audio de fondo de la experiencia y agregar capas basadas en importancia. A menudo, esto da lugar a que cada capa sea más fuerte que la anterior.

Al imaginarse la combinación como un embudo invertido, con el menos importante (y los sonidos generalmente más silencioso) en la parte inferior, se recomienda estructurar la combinación similar al siguiente diagrama.

![Estructura de combinación de sonidos](images/soundlevels.png)

La voz es un escenario interesante. En función de la experiencia que cree, puede que desee tener un sonido estéreo (no localizado) o crear un espacial de la voz. Dos experiencias publicadas de Microsoft muestran excelentes ejemplos de cada escenario.

[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voz de estéreo. Cuando el narrador describe la ubicación que se está viendo, el sonido es coherente y no varía en función de la posición del usuario. Esto permite al narrador describir la escena sin tener que alejarse de los sonidos espaciales del entorno.

[Fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) emplea una voz espacial en forma de un detective. La voz del detective se usa para ayudar a la atención del usuario a una pista importante como si hubiera un hombre real en el salón. Esto permite una mayor sensación de inmersión en la experiencia de resolución del misterio.

### <a name="part-3--performance"></a>Parte 3: rendimiento

#### <a name="cpu-usage"></a>Uso de CPU

Cuando se usa el sonido espacial, 10-12 emisores consumirán aproximadamente el 12% de la CPU.

#### <a name="stream-long-audio-files"></a>Transmitir archivos de audio largos

Los datos de audio pueden ser grandes, sobre todo en las tarifas de ejemplo comunes (44,1 y 48 kHz). Una regla general es que los archivos de audio de más de 5-10 segundos se deben transmitir para reducir el uso de memoria de la aplicación.

En Unity, puede marcar un archivo de audio para el streaming en la configuración de importación del archivo.

![Configuración de importación de audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capítulo 5: efectos especiales

### <a name="objectives"></a>Objetivos

* Agregue profundidad a "Magic Windows".
* Traslade al usuario al mundo virtual.

### <a name="magic-windows"></a>Ventanas mágicas

#### <a name="key-concepts"></a>Conceptos clave

* La creación de vistas en un mundo oculto es visualmente atractiva.
* Mejore el realismo agregando efectos de audio cuando un holograma o el usuario están cerca del mundo oculto.

#### <a name="instructions"></a>Instrucciones

* En el panel **jerarquía** , expanda **HologramCollection** y seleccione el **submundo**.
* Expanda el **submundo** y seleccione **VoiceSource**.
* En el panel **Inspector** , haga clic en **Agregar componente** y agregar **efecto de voz de usuario**.

Se agregará un componente **AudioSource** a **VoiceSource**.

* En **AudioSource**, establezca **salida** en **UserVoice (Mixer)** .
* Active la casilla **Spatial** .
* Arrastre el control deslizante de **combinación espacial** hasta el modo **3D**o escriba **1** en el cuadro de edición.
* Expanda **configuración de sonido 3D**.
* Establezca el **nivel de Doppler** en **0**.
* En **efecto de voz de usuario**, establezca **objeto primario** en el **mundo** de la escena.
* Establezca la **distancia máxima** en **1**.

El establecimiento de la **distancia máxima** indica al **usuario el efecto** de la forma en que el usuario debe estar al objeto primario antes de que se habilite el efecto.

* En **efecto de voz de usuario**, expanda **los parámetros de coro**.
* Establezca **profundidad** en **0,1**.
* Establezca **TAP 1 Volume**, **Pulse 2 Volume** y **Pulse 3 Volume** hasta **0,8**.
* Establezca el **volumen de sonido original** en **0,5**.

La configuración anterior configura los parámetros del **AudioChorusFilter** de Unity que se usa para agregar riqueza a la voz del usuario.

* En **efecto de voz de usuario**, expanda **parámetros de eco**.
* Establecer **retraso** en **300**
* Establezca la **relación de decadencia** en **0,2**.
* Establezca el **volumen de sonido original** en **0**.

La configuración anterior configura los parámetros del **AudioEchoFilter** de Unity que se usa para hacer que la voz del usuario se repita.

El script de efecto de la voz de usuario es responsable de:

* Medir la distancia entre el usuario y el **GameObject** al que se adjunta el script.
* Determinar si el usuario está orientado o no al **GameObject**.

El usuario debe estar orientado a GameObject, independientemente de la distancia, para que el efecto se habilite.

* Aplicar y configurar **AudioChorusFilter** y **AudioEchoFilter** en **AudioSource**.
* Deshabilitar el efecto deshabilitando los filtros.

Efecto de voz de usuario usa el componente selector de flujo de MIC, de [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), para seleccionar el flujo de voz de alta calidad y enrutarlo al sistema de audio de Unity.

* En el panel **jerarquía** , seleccione **administradores**.
* En el panel **Inspector** , expanda **controlador de entrada de voz**.
* En **controlador de entrada de voz**, expanda **Mostrar el submundo**.
* No cambie la **función** a **UnderworldBase. alhabilitar**.

![Palabra clave: mostrar el submundo](images/showunderworld.png)

* Expanda **ocultar submundo**.
* No cambie la **función** a **UnderworldBase. deshabilito**.

![Palabra clave: ocultar el submundo](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilación e implementación

* Como antes, compile el proyecto en Unity e impleméntelo en Visual Studio.

Una vez implementada la aplicación:

* Cara a una superficie (pared, piso, tabla) y decir *"Mostrar el mundo"* .

Se mostrará el submundo y se ocultarán todos los demás hologramas. Si no ve el mundo, asegúrese de que se enfrenta a una superficie real.

* Enfoque dentro de 1 medidor del holograma de submundo y empiece a hablar.

Ahora hay efectos de audio aplicados a la voz.

* Desactive el mundo y observe cómo ya no se aplica el efecto.
* *"Oculte el mundo"* para ocultar el mundo.

El mundo se ocultará y los hologramas previamente ocultos volverán a aparecer.

## <a name="the-end"></a>Fin

Enhorabuena. Ahora ha completado el **Mr espacial 220: sonido espacial**.

Escuche el mundo y llévese sus experiencias con sonido.
