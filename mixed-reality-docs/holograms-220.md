---
title: El Sr. espacial 220 - sonido espacial
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de sonido espaciales.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, sonido espacial
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599017"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR 220 espacial: Sonido espacial

[Sonido espacial](spatial-sound.md) breathes vida en hologramas y les da presencia en nuestro mundo. Hologramas se componen de luz y sonido, y si resulta que pasar por alto las hologramas, espacial sonido puede ayudarle a encontrarlas. Sonido espacial no es como el sonido típico que desea escuchar en el radio, es el sonido que se coloca en el espacio 3D. Con sonido espacial, puede realizar hologramas sonido que están detrás de usted, a su lado o incluso en la cabeza! En este curso, aprenderá a:

* Configurar el entorno de desarrollo para utilizar Microsoft Spatial Sound.
* Usar un sonido espacial para mejorar las interacciones.
* Usar un sonido espacial junto con la asignación espacial.
* Comprender el diseño del sonido y mezclando los procedimientos recomendados.
* Usar un sonido para mejorar los efectos especiales y conducir al usuario en el mundo de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>MR 220 espacial: Sonido espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).
* Básica C# capacidad de programación.
* Debe haber completado [MR Fundamentos 101](holograms-101.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Esta versión ya no esté actualizada.
  * Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Esta versión ya no esté actualizada.
  * Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Esta versión ya no esté actualizada.
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Erratas y notas

* "Habilitar Solo mi código" debe deshabilitarse (*unchecked*) en Visual Studio en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1: instalación de Unity

### <a name="objectives"></a>Objetivos

* Cambiar la configuración de sonido de Unity para usar Microsoft Spatial Sound.
* Agregar sonido 3D a un objeto en Unity.

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **abierto**.
* Vaya al escritorio y busque la carpeta se archivados previamente sin.
* Haga clic en el **Starting\Decibel** carpeta y, a continuación, presione el **Seleccionar carpeta** botón.
* Espere a que el proyecto se carga en Unity.
* En el **proyecto** panel abierto **Scenes\Decibel.unity**.
* En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **P0LY**.
* En el Inspector de, expanda **AudioSource** y tenga en cuenta que no hay ningún **Spatialize** casilla de verificación.

De forma predeterminada, Unity no carga un complemento espacial. Los pasos siguientes permitirán espacial sonido en el proyecto.

* En el menú superior de Unity, vaya a **Editar > configuración del proyecto > Audio**.
* Buscar el **espacial complemento** lista desplegable y seleccione **MS HRTF Spatializer**.
* En el **jerarquía** panel, seleccione **HologramCollection > P0LY**.
* En el **Inspector** panel, busque el **origen Audio** componente.
* Compruebe el **Spatialize** casilla de verificación.
* Arrastre el **Blend espacial** control deslizante hasta **3D**, o escriba **1** en el cuadro de edición.

Ahora cree el proyecto en Unity y configurar la solución en Visual Studio.

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Haga clic en **agregar escenas abierto** para agregar la escena.
3. Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.
4. Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**. En caso contrario, déjelo en **cualquier dispositivo**.
5. Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).
6. Haz clic en **Compilación**.
7. Crear un **nueva carpeta** denominada "Aplicación".
8. Solo haga clic en el **aplicación** carpeta.
9. Presione **Seleccionar carpeta**.

Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.

1. Abra el **aplicación** carpeta.
2. Abra el **solución de Visual Studio de decibelios**.

Si la implementación en HoloLens:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.
2. Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.
3. Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**. Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**. Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).

Si la implementación en un auricular envolvente:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.
2. Asegúrese de que el destino de implementación se establece en **máquina Local**.
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capítulo 2: sonido espacial e interacción

### <a name="objectives"></a>Objetivos

* Mejore el realismo holograma mediante sonido.
* Dirigir la mirada del usuario mediante sonido.
* Proporcionar comentarios de gesto mediante sonido.

### <a name="part-1---enhancing-realism"></a>Parte 1: si quiere mejorar

#### <a name="key-concepts"></a>Conceptos clave

* Spatialize sonidos holograma.
* Orígenes de sonido deben colocarse en una ubicación adecuada en el holograma.

La ubicación adecuada para el sonido va a depender del holograma. Por ejemplo, si el holograma es de una persona, el origen de sonido debe encontrarse cerca de la boca y no los pies.

#### <a name="instructions"></a>Instrucciones

Las siguientes instrucciones asociará un sonido spatialized un holograma.

* En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **P0LY**.
* En el **Inspector** panel el **AudioSource**, haga clic en el círculo junto a **AudioClip** y seleccione **PolyHover** desde el menú emergente.
* Haga clic en el círculo junto a **salida** y seleccione **efectos de sonido** desde el menú emergente.

Proyecto decibelios usa un Unity **AudioMixer** componente para habilitar el ajuste de los niveles de sonido para grupos de sonidos. Por agrupación sonidos de este modo, se puede ajustar el volumen global al tiempo que mantiene el volumen relativo de cada sonido.

* En el **AudioSource**, expanda **configuración sonido 3D**.
* Establecer **Doppler nivel** a **0**.

Establecer nivel Doppler a cero los deshabilita cambios de timbre causados por el movimiento (ya sea el holograma o del usuario). Un ejemplo clásico de Doppler es un automóvil de avance rápido. Como el vehículo aproxima a un agente de escucha inmóvil, aumenta el tono del motor. Cuando pasa el agente de escucha, el tono disminuye con la distancia.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2: dirigir la mirada del usuario

#### <a name="key-concepts"></a>Conceptos clave

* Usar un sonido para llamar la atención sobre hologramas importante.
* Las orejas ayudarán a dirigir donde deben buscar los ojos.
* El cerebro tiene ciertas expectativas aprendidos.

Un ejemplo de expectativas aprendidos es que generalmente son pájaros por encima de los cabezales de los seres humanos. Si un usuario oye un sonido de pájaro, su reacción inicial es buscar. Colocación de una vista de pájaro a continuación el usuario puede dar lugar a ellos orientado a la dirección correcta de sonido, pero no puede encontrar el holograma según la expectativa de que se necesitan buscar.

#### <a name="instructions"></a>Instrucciones

Las instrucciones siguientes permiten P0LY ocultar detrás, para que pueda usar sonido para localizar el holograma.

* En el **jerarquía** panel, seleccione **administradores**.
* En el **Inspector** panel, busque **controlador de entrada de voz**.
* En **controlador de entrada de voz**, expanda **vaya ocultar**.
* Cambio **ninguna función** a **PolyActions.GoHide**.

![palabra clave: Ocultar vaya](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3: comentarios de gestos

#### <a name="key-concepts"></a>Conceptos clave

* Proporcione al usuario confirmación positivo gesto con sonido
* No se sobrecargará el usuario - get sonidos demasiado altos de la manera
* Sonidos sutiles funcionan mejor - no hagan la experiencia

#### <a name="instructions"></a>Instrucciones

* En el **jerarquía** del panel, expanda **HologramCollection**.
* Expanda **EnergyHub** y seleccione **Base**.
* En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **controlador de gestos sonido**.
* En **controlador de gestos sonido**, haga clic en el círculo junto a **navegación iniciado Clip** y **navegación actualizado Clip** y seleccione **RotateClick**desde la ventana emergente para ambos.
* Haga doble clic en "GestureSoundHandler" para cargar en Visual Studio.

Controlador de gestos sonido realiza las siguientes tareas:

* Crear y configurar un **AudioSource**.
* Colocar el **AudioSource** en la ubicación de la correspondiente **GameObject**.
* Reproduce el **AudioClip** relacionadas con el gesto.

#### <a name="build-and-deploy"></a>Compilación e implementación

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Haz clic en **Compilación**.
3. Solo haga clic en el **aplicación** carpeta.
4. Presione **Seleccionar carpeta**.

Compruebe que la barra de herramientas dice "Release", "x 86" o "x64" y "Dispositivo remoto". Si no es así, se trata de la instancia de codificación de Visual Studio. Es posible que deba volver a abrir la solución desde la carpeta de la aplicación.

* Si se le solicite, vuelva a cargar los archivos del proyecto.
* Como antes, la implementación desde Visual Studio.

Una vez implementada la aplicación:

* Observe cómo el sonido cambia al desplazarse por P0LY.
* Por ejemplo *"Ocultar vaya"* realizar P0LY mover a una ubicación que tiene detrás. Encontrarlo si el sonido.
* Mire la base del concentrador de energía. Pulse y arrastre izquierda o derecha para girar el holograma y observe cómo el sonido de clic confirma el gesto.

Nota: Hay un panel de texto que se va a tag-along con usted. Contiene los comandos de voz disponibles que puede usar a lo largo de este curso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capítulo 3: asignación espacial de sonido y espacial

### <a name="objectives"></a>Objetivos

* Confirme la interacción entre hologramas y el mundo real mediante sonido.
* Occlude sonido con el mundo físico.

### <a name="part-1---physical-world-interaction"></a>Parte 1: interacción del mundo físico

#### <a name="key-concepts"></a>Conceptos clave

* Los objetos físicos generalmente emita un sonido al encontrar una superficie u otro objeto.
* Sonidos deben ser el contexto adecuado dentro de la experiencia.

Por ejemplo, al definir una taza de una tabla, debe realizar un sonido y más suave que quitar un boulder en una parte del sistema operativo.

#### <a name="instructions"></a>Instrucciones

* En el **jerarquía** del panel, expanda **HologramCollection**.
* Expanda **EnergyHub**, seleccione **Base**.
* En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **acción y puntee en lugar de a con sonido**.
* En **pulse al lugar con la acción y sonido**:
  * Comprobar **colocar primario al pulsar**.
  * Establecer **colocación sonido** a **lugar**.
  * Establecer **Pickup sonido** a **Pickup**.
  * Presione el signo + de la parte inferior derecha bajo **Pickup acción** y **en acción de selección de ubicación**. Arrastre EnergyHub desde la escena en el **None (objeto)** campos.
    * En **Pickup acción**, haga clic en **sin función** -> **EnergyHubBase** -> **ResetAnimation**.
    * En **en acción de selección de ubicación**, haga clic en **sin función** -> **EnergyHubBase** -> **OnSelect**.

![Pulse en lugar de con la acción y sonido](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2: oclusión de sonido

#### <a name="key-concepts"></a>Conceptos clave

* Sonido, al igual que la luz, puede ser ocluido.

Un ejemplo clásico es una sala de conciertos. Cuando un agente de escucha es permanente fuera del pasillo y la puerta se cierra, los sonidos de música atenuarse. Normalmente, también es una reducción del volumen. Cuando se abre la puerta, todo el espectro de sonido se escucha en el volumen real. Sonidos de alta frecuencia generalmente absorbe más de las frecuencias bajas.

#### <a name="instructions"></a>Instrucciones

* En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **P0LY**.
* En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **Audio emisor**.

La clase emisora Audio proporciona las siguientes características:

* Restaura los cambios en el volumen de la **AudioSource**.
* Realiza una **Physics.RaycastNonAlloc** desde la posición del usuario en la dirección de la **GameObject** a la que el **AudioEmitter** está conectado.

El método RaycastNonAlloc se utiliza como una optimización del rendimiento para limitar las asignaciones, así como el número de resultados devueltos.

* Para cada **IAudioInfluencer** encontrado, llama a la **ApplyEffect** método.
* Para cada uno anterior **IAudioInfluencer** es decir, ya no se ha encontrado, llamada la **RemoveEffect** método.

Tenga en cuenta que AudioEmitter se actualiza en escalas de tiempo humano, en contraposición a en un fotograma a fotograma. Esto se hace porque los seres humanos generalmente no se mueven lo suficientemente rápido para que el efecto a deben actualizarse con más frecuencia que cada trimestre o medio segundo. Hologramas ese teleport rápidamente desde una ubicación a otra puede interrumpir la ilusión.

* En el **jerarquía** del panel, expanda **HologramCollection**.
* Expanda **EnergyHub** y seleccione **BlobOutside**.
* En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **Occluder Audio**.
* En **Audio Occluder**, establezca **límite de frecuencia** a **1500**.

Esta configuración limita las frecuencias AudioSource a 1500 Hz y anteriores.

* Establecer **volumen pasar** a **0.9**.

Esta configuración reduce el volumen de la AudioSource al 90% de su nivel actual.

Audio Occluder implementa IAudioInfluencer para:

* Aplicar un efecto de oclusión utilizando un **AudioLowPassFilter** que se asocia a la **AudioSource** administrado comprar el **AudioEmitter**.
* Aplica la atenuación de volumen a la AudioSource.
* Deshabilita el efecto de establecer una frecuencia de corte neutra y deshabilitando el filtro.

La frecuencia usada como neutro es 22 kHz (22000 Hz). Se ha elegido esta frecuencia debido a que está por encima de la frecuencia máxima nominal que pueda ser escuchada por el oído humano, no realizar ningún impacto perceptible en el sonido.

* En el **jerarquía** panel, seleccione **SpatialMapping**.
* En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **Occluder Audio**.
* En **Audio Occluder**, establezca **límite de frecuencia** a **750**.

Cuando varios occluders se encuentran en la ruta de acceso entre el usuario y la **AudioEmitter**, la frecuencia mínima se aplica el filtro.

* Establecer **volumen pasar** a **0,75**.

Cuando varios occluders se encuentran en la ruta de acceso entre el usuario y la **AudioEmitter**, se aplica el paso de volumen a través de aditivamente.

* En el **jerarquía** panel, seleccione **administradores**.
* En el **Inspector** del panel, expanda **controlador de entrada de voz**.
* En **controlador de entrada de voz**, expanda **cargo vaya**.
* Cambio **ninguna función** a **PolyActions.GoCharge**.

![palabra clave: Vaya a cargo](images/gocharge.png)

* Expanda **aquí**.
* Cambio **ninguna función** a **PolyActions.ComeBack**.

![palabra clave: Ven aca](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilación e implementación

* Como antes, compile el proyecto de Unity e implemente en Visual Studio.

Una vez implementada la aplicación:

* Por ejemplo *"Cargo por ir"* para que P0LY entrar en el centro de energía.

Tenga en cuenta el cambio en el sonido. Debe parecer un poco más silencioso y estropeados. Si es posible colocar manualmente con una pared u otro objeto entre usted y el centro de energía, debe observar un muffling adicional del sonido debido a la ocultación de todo el mundo real.

* Por ejemplo *"Proceden aquí"* tener P0LY deje el concentrador de energía y colocarse delante de usted.

Tenga en cuenta que se ha quitado la ocultación de sonido cuando P0LY se cierra el concentrador de energía. Si sigues siendo oclusión de audición, P0LY es posible que se ocluyeron en el mundo real. Intente mover para asegurarse de que tiene un claro ejemplo de línea de visión a P0LY.

### <a name="part-3---room-models"></a>Parte 3: modelos de sala

#### <a name="key-concepts"></a>Conceptos clave

* El tamaño del espacio proporciona colas subliminales que contribuyen a la localización de sonido.
* Los modelos de la sala se establecen por-**AudioSource**.
* El [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona código para establecer el modelo de espacio.
* Para la experiencia de realidad mixta, seleccione el modelo de espacio que mejor se ajusta el espacio del mundo real.

Si va a crear un escenario de realidad Virtual, seleccione el modelo de espacio que se adapte el entorno virtual.

## <a name="chapter-4---sound-design"></a>Capítulo 4: diseño de sonido

### <a name="objectives"></a>Objetivos

* Conocer las consideraciones de diseño eficaz de sonido.
* Obtenga información sobre las directrices y técnicas de mezcla.

### <a name="part-1---sound-and-experience-design"></a>Parte 1: diseño de la experiencia y sonido

Esta sección describe directrices y consideraciones de diseño de experiencia y sonido clave de.

#### <a name="normalize-all-sounds"></a>Normalizar todos los sonidos

Esto evita la necesidad de código de casos especial ajustar los niveles de volumen por sonido, que puede llevar mucho tiempo y limita la capacidad para actualizar fácilmente los archivos de sonido.

#### <a name="design-for-an-untethered-experience"></a>Diseño para una experiencia sin restricción

HoloLens es un equipo completamente independiente, sin restricción holográfico. Los usuarios pueden y usará sus experiencias al mover. No olvide probar la mezcla de audio recorriendo alrededor.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emitir sonidos desde ubicaciones lógicas en sus hologramas

En el mundo real, un perro no corteza de su cola y voz de una persona no proceden de sus pies. Evitar la que emisión de los sonidos de inesperado partes de sus hologramas.

Para hologramas pequeño, es razonable tener sonido emitir desde el centro de la geometría.

#### <a name="familiar-sounds-are-most-localizable"></a>Suena familiar es más localizable

La voz humana y la música son muy fáciles de localizar. Si alguien llama a su nombre, es capaz de manera muy precisa determinar de qué dirección proviene de la voz y de cómo lejos. Sonidos cortos y desconocidas son más difíciles de localizar.

#### <a name="be-cognizant-of-user-expectations"></a>Estar al corriente de las expectativas del usuario

Experiencia de vida juega un papel en nuestra capacidad para identificar la ubicación de un sonido. Se trata de uno de los motivos por qué la voz humana es especialmente fácil de localizar. Es importante tener en cuenta las expectativas de los usuarios aprendidos al colocar los sonidos.

Por ejemplo, cuando alguien oye una canción de la vista de pájaro generalmente parecen, como pájaros tienden a estar por encima de la línea de visión (volando o en un árbol). No es raro que un usuario activar en la dirección correcta de un sonido, pero buscar en la dirección equivocada vertical y dejarán de estar confundirse o frustrados cuando se ha podido encontrar el holograma.

#### <a name="avoid-hidden-emitters"></a>Evite los emisores ocultos

En el mundo real, si recibimos un sonido, podemos identificar por lo general el objeto que emite el sonido. Esto también debe contener true en sus experiencias. Puede ser muy desconcertar a los usuarios para oír un sonido, sabe de dónde se origina el sonido y podrá ver un objeto.

Existen algunas excepciones a esta directriz. Por ejemplo, los sonidos ambientales como Bates de cricket en un campo no debe visibles. Experiencia de vida nos da la familiaridad con el origen de estos sonidos sin necesidad de verlo.

### <a name="part-2---sound-mixing"></a>Parte 2: mezcla de sonido

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Destino de la combinación adecuada para el volumen de un 70% en el HoloLens

Experiencias de realidad mixtas permiten hologramas para verse en el mundo real. También deben permitir sonidos del mundo real se oye hablar mucho. Un destino de un 70% del volumen permite al usuario escuchar el mundo en torno a ellas, junto con el sonido de su experiencia.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens en 100% del volumen deben ahogar los sonidos externos

Un nivel de volumen del 100% es semejante a una experiencia de realidad Virtual. Visualmente, el usuario se transporta a un mundo diferente. La misma debe cumplirse audible.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Utilice el AudioMixer Unity para ajustar las categorías de sonidos

Al diseñar la combinación, a menudo resulta útil crear categorías de sonido y tiene la posibilidad de aumentar o reducir su volumen como una unidad. Esto conserva los niveles relativos de cada sonido y se permiten cambios rápidos y sencillo a la combinación global. Incluyen categorías comunes; efectos de sonido de ambiente, voz superpuesta y música de fondo.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Combinación de sonidos según la mirada del usuario

A menudo puede ser útil cambiar la combinación de sonidos en su experiencia en función de dónde un usuario es (o no) busca. Un uso común de esta técnica son reducir el nivel de volumen para hologramas que se encuentran fuera del marco holográfica para que sea más fácil para el usuario para centrarse en la información frente a ellas. Otro uso es aumentar el volumen de un sonido para atraer la atención del usuario a un evento importante.

#### <a name="building-your-mix"></a>Creación de la combinación

Al compilar la combinación, se recomienda comenzar con audio de fondo de su experiencia y agregar capas basadas en importancia. A menudo, esto da como resultado de cada capa que se va a aumentar el volumen que el anterior.

Uno se imagina la combinación como un embudo invertido, con menos importante (y por lo general los sonidos) en la parte inferior, se recomienda para estructurar la combinación similar al siguiente diagrama.

![Estructura de la combinación de sonido](images/soundlevels.png)

Voz superpuesta es un escenario interesante. Basándose en la experiencia que se va a crear es posible que desee tener un sonido estéreo (no localizado) o spatialize su voz superpuesta. Publicado por Microsoft dos experiencias de ilustrar excelente ejemplos de cada escenario.

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voz estéreo a través. Cuando el Narrador que describe la ubicación que se va a ver, el sonido es coherente y no varían en función de la posición del usuario. Esto permite que el Narrador describir la escena sin toma de los sonidos spatialized del entorno.

[Fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utiliza una voz spatialized sobre en forma de un detective. Voz del detective se usa para ayudar a que la atención del usuario a una importante pista como si fuera un humanos real en la sala. Esto permite una mayor sensación de inmersión en la experiencia para resolver el misterio.

### <a name="part-3--performance"></a>Parte 3: rendimiento

#### <a name="cpu-usage"></a>Uso de CPU

Al usar sonido espacial, 10-12 emisores consumirá aproximadamente un 12% de la CPU.

#### <a name="stream-long-audio-files"></a>Archivos de sonido de larga duración Stream

Datos de audio pueden ser grandes, especialmente a velocidades de muestreo comunes (48 y 44,1 kHz). Por regla general es que se deben transmitir archivos de audio más de 5 a 10 segundos para reducir el uso de memoria de la aplicación.

En Unity, puede marcar un archivo de audio para el streaming en importar la configuración del archivo.

![Configuración de importación de audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capítulo 5: efectos especiales

### <a name="objectives"></a>Objetivos

* Agregar profundidad a "Magic Windows".
* Poner el usuario en el mundo virtual.

### <a name="magic-windows"></a>Windows mágica

#### <a name="key-concepts"></a>Conceptos clave

* Creación de vistas en un mundo oculto, es visualmente atractiva.
* Mejore el realismo mediante la adición de efectos de audio cuando el usuario o un holograma es casi del mundo oculto.

#### <a name="instructions"></a>Instrucciones

* En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **Underword**.
* Expanda **Underword** y seleccione **VoiceSource**.
* En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **efecto de voz del usuario**.

Un **AudioSource** componente se agregará a **VoiceSource**.

* En **AudioSource**, establezca **salida** a **UserVoice (Mixer)**.
* Compruebe el **Spatialize** casilla de verificación.
* Arrastre el **Blend espacial** control deslizante hasta **3D**, o escriba **1** en el cuadro de edición.
* Expanda **configuración de sonido 3D**.
* Establecer **Doppler nivel** a **0**.
* En **efecto de voz del usuario**, establezca **objeto primario** a la **Underword** desde la escena.
* Establecer **distancia máxima** a **1**.

Establecer **distancia máxima** indica **efecto de voz del usuario** cómo cerrar el usuario debe ser para el objeto primario antes de que el efecto está habilitado.

* En **efecto de voz del usuario**, expanda **coro parámetros**.
* Establecer **profundidad** a **0,1**.
* Establecer **pulse 1 volumen**, **pulse 2 volumen** y **pulse volumen 3** a **0.8**.
* Establecer **volumen del sonido Original** a **0,5**.

La configuración anterior configura los parámetros de la unidad **AudioChorusFilter** usa para agregar la riqueza a la voz del usuario.

* En **efecto de voz del usuario**, expanda **Echo parámetros**.
* Establecer **retraso** a **300**
* Establecer **decaer proporción** a **0.2**.
* Establecer **volumen del sonido Original** a **0**.

La configuración anterior configura los parámetros de la unidad **AudioEchoFilter** usa para hacer que la voz del usuario se van a reflejar.

La secuencia de comandos de efecto de voz del usuario es responsable de:

* Medir la distancia entre el usuario y la **GameObject** al que está adjunta la secuencia de comandos.
* Determinar si el usuario es accesible desde el **GameObject**.

El usuario debe ser accesible desde GameObject, independientemente de la distancia del efecto que se habilite.

* Aplicar y configurar un **AudioChorusFilter** y un **AudioEchoFilter** a la **AudioSource**.
* Deshabilitar el efecto de deshabilitar los filtros.

Efecto de voz del usuario utiliza el componente de Mic Stream Selector, desde el [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)para seleccionar la secuencia de voz de alta calidad y enrutarlo en el sistema de audio de Unity.

* En el **jerarquía** panel, seleccione **administradores**.
* En el **Inspector** del panel, expanda **controlador de entrada de voz**.
* En **controlador de entrada de voz**, expanda **Underword mostrar**.
* Cambio **ninguna función** a **UnderworldBase.OnEnable**.

![palabra clave: Mostrar Underword](images/showunderworld.png)

* Expanda **ocultar Underword**.
* Cambio **ninguna función** a **UnderworldBase.OnDisable**.

![palabra clave: Ocultar Underword](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilación e implementación

* Como antes, compile el proyecto de Unity e implemente en Visual Studio.

Una vez implementada la aplicación:

* Se enfrentan a una superficie (pared, floor, tabla) y say *"Mostrar Underword"*.

Se mostrará el Underword y todos los demás hologramas estará oculto. Si no ve el Underword, asegúrese de que se enfrentan a una superficie del mundo real.

* Enfoque de menos de 1 metro del holograma Underword y comience a hablar.

Ahora hay efectos de audio aplicados a su voz.

* Aleje el Underword y observe cómo ya no se aplica el efecto.
* Por ejemplo *"Ocultar Underword"* para ocultar el Underword.

Se ocultará el Underword y volverá a aparecer la hologramas estaban ocultos anteriormente.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ahora ha completado **220 espacial MR: Sonido espacial**.

Escuchar a todo el mundo y traiga sus experiencias cobren vida con sonido.
