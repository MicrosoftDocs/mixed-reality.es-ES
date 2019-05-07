---
title: Seguimiento de los ojos
description: Seguimiento de los ojos
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
keywords: Seguimiento de los ojos, mixto en realidad, Input, ojo mirada
ms.openlocfilehash: 75cbba9048b620e4b00492ad3f71315fabf86677
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581055"
---
# <a name="eye-tracking-on-hololens-2"></a>Ojo de seguimiento en 2 HoloLens
Permite un nivel completamente nuevo de contexto y la descripción humana dentro de la Holographic HoloLens 2 experiencia proporcionando a los desarrolladores la capacidad de uso de información sobre lo que están mirando los usuarios increíble. Esta página proporciona información general sobre cómo los desarrolladores pueden beneficiarse de seguimiento de ojo para varios casos de uso y lo que debe tener en cuenta cuando el diseño de interfaces de usuario basada en la mirada de ojos. 

## <a name="use-cases"></a>Casos de uso
Seguimiento de los ojos permiten que las aplicaciones realizar un seguimiento de dónde mira el usuario en tiempo real. Esta sección describen algunos de los posibles casos de uso y las interacciones novedosas que son posibles con los ojos de seguimiento en la realidad mixta.
Antes de comenzar, a continuación se mencionará el [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) varias veces, ya que proporciona varios ejemplos interesantes y eficaces para usar el seguimiento de ojo como destino admitidos por el ojo rápido y sin esfuerzo las selecciones y desplazarse automáticamente a través de texto en función de donde se examina el usuario. 

### <a name="user-intent"></a>Intención del usuario    
Información acerca de dónde se examina un usuario proporciona una potente **contexto para otras entradas**, como voz, manos y controladores.
Esto puede usarse para varias tareas.
Por ejemplo, esto puede oscilar entre rápidamente y sin esfuerzo **destinadas a** a través de la escena con solo mirar un holograma y que dice "select" (consulte también [mirada de encabezado y confirmación](gaze-and-commit.md)) o diciendo "poner esto...", a continuación, consultando hasta donde desee colocar el holograma y decir "... There". Ejemplos para esto pueden encontrarse en [Kit de herramientas de realidad mixta - selección de destino compatible con el efecto de ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) y [Kit de herramientas realidad mixta - posicionamiento de destino compatible con el efecto de ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Puede incluir un ejemplo adicional de la intención del usuario con la información sobre lo que examine los usuarios para mejorar la interacción con los agentes virtuales embodied y hologramas interactivos. Por ejemplo, los agentes virtuales pueden adaptar las opciones disponibles y su comportamiento según actualmente ve contenido. 

### <a name="implicit-actions"></a>Acciones implícitas
La categoría de acciones implícitas está estrechamente relacionado con intención del usuario.
La idea es que hologramas o elementos de la interfaz de usuario reaccionan de manera un poco instinctual que puede no incluso sentir interactúa con el sistema en absoluto, sino más bien que el sistema y el usuario están sincronizadas. Por ejemplo, es un ejemplo inmensamente correcto **desplazamiento automático basados en ojo-mirada**. La idea es tan sencillo: El usuario lee un texto y solo puede dejen de leer. El texto se mueve hacia arriba gradualmente mantener a los usuarios en su flujo de lectura. Un aspecto clave es que la velocidad de desplazamiento se adapta a la velocidad de lectura del usuario.
Otro ejemplo es **compatible con la vista de zoom y panorámica** para que el usuario puede parecer un profundizar exactamente hacia lo que se centra en. Activando el zoom y controlar la velocidad de zoom pueden controlarse a través de voz o pasar la entrada que es importante acerca de cómo proporcionar la sensación de control y evitar sobrecargar el usuario (hablaremos acerca de estas instrucciones de diseño con más detalle a continuación). Una vez que el zoom activo, el usuario puede, a continuación, suavemente seguir, por ejemplo, el curso de una calle para explorar su vecindario simplemente con su mirada ojos.
Ejemplos de demostración para estos tipos de interacciones que pueden encontrarse en el [Kit de herramientas de realidad mixta - compatible con el efecto de ojos navegación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) ejemplo.

Usos adicionales para _acciones implícitas_ pueden incluir:
- **Notificaciones inteligentes:** ¿Alguna vez obtener le molesta notificaciones emergentes derecha donde que se centraban? Teniendo en cuenta que un usuario actualmente está prestando atención a, puede que sea mejor! Mostrar notificaciones de desplazamiento desde donde el usuario está observando actualmente para limitar las distracciones y descartarlas automáticamente una vez terminado de leer. 
- **El lector atento hologramas:** Hologramas que reaccionan sutilmente cuando está examinando. Esto puede oscilar entre elementos de interfaz de usuario ligeramente resplandecientes, una flor floración lentamente a una mascota virtual inicial tener en cuenta o intenta evitar su mirada ojo después un observe fijamente prolongado. Esto puede proporcionar una idea interesante de la conectividad y la satisfacción del cliente en la aplicación.

### <a name="attention-tracking"></a>Atención de seguimiento   
Información acerca de dónde mirar a los usuarios es una herramienta increíblemente eficaz para evaluar la facilidad de uso de diseños y a identificar los problemas de flujos de trabajo eficaces. En este momento, seguimiento de análisis y visualización de los ojos ya son una práctica común en varias áreas de la aplicación. Con el 2 de HoloLens, proporcionamos una nueva dimensión a este conocimiento como hologramas 3D pueden colocarse en contextos del mundo real y evalúa junto con. El [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) se proporcionan ejemplos básicos para el registro y cargar datos de seguimiento de los ojos y cómo visualizarlos.

Otras aplicaciones en esta área pueden incluir: 
-   **Visualización de mirada ojo remoto:** Visualizar lo que los colaboradores remotos están mirando, por ejemplo, asegúrese de si las instrucciones se entiende y seguidas correctamente.
-   **Estudios de investigación de usuario:** Atención de seguimiento puede usarse para explorar la manera Inexperto frente a los usuarios expertos visualmente analizar contenido o su coordinación de ojo de mano para tareas complejas (por ejemplo, para el análisis de datos médicos o al usar máquinas).
-   **Supervisión del rendimiento y simulaciones de formación:** Practique y optimizar la ejecución de tareas mediante la identificación de cuellos de botella más eficazmente en el flujo de ejecución.
-   **Diseñar las evaluaciones, anuncio y la investigación de mercado:** Seguimiento de los ojos es una herramienta común para la investigación de mercado evaluar los diseños de producto y el sitio Web.

### <a name="additional-use-cases"></a>Casos de uso adicionales
- **Juegos:** ¿Quisiera tienen superpoderes? ¡Esta es su oportunidad! Levitate hologramas por que comience en ellos. Solucionar láser vigas de sus ojos. ¡Convierta los enemigos en piedra o inmovilizó! Use su visión de rayos x para explorar los edificios. Su imaginación es el límite.  

- **Avatares expresivos:** Efecto de ojos SIDA en avatares 3D más expresivos de seguimiento utilizando la fecha de seguimiento de los ojos en vivo para animar los ojos de avatar para indicar lo que el usuario está viendo en este momento. También se agrega más expresividad agregando guiños y parpadea. 

- **Entrada de texto:** Seguimiento de los ojos pueden utilizarse como una alternativa interesante para la entrada de texto de bajo esfuerzo especialmente cuando las manos o voz no son convenientes para usar. 


## <a name="eye-tracking-api"></a>API de seguimiento de ojo
Antes de entrar en detalles sobre las directrices de diseño específicas para la interacción de mirada, que queremos brevemente las funcionalidades que ofrece el Rastreador de ojo de HoloLens 2. El [API de seguimiento de ojo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) es accesible a través: `Windows.Perception.People.EyesPose`. Proporciona un rayo de mirada única ojo (origen de mirada y dirección) a los desarrolladores.
El Rastreador de ojo proporciona los datos en sobre _30 FPS_.
La mirada de ojo de predicción se encuentra dentro de la entidad emisora de certificados. 1.0-1,5 grados en ángulo visual en torno a los datos reales visto destino. Como se esperan que las imprecisiones ligeras, debe planear un margen alrededor de este valor de límite inferior. Trataremos esto más a continuación. Para el seguimiento para que funcione con precisión de los ojos, cada usuario es necesario recorrer en iteración un ojo calibración de usuario de seguimiento. 

![Tamaño de destino óptimo a distancia de medidor 2](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de destino óptimo a distancia de medidor 2*


## <a name="eye-gaze-design-guidelines"></a>Instrucciones de diseño de ojo mirada
Creación de una interacción que aprovecha las ventajas de rápido movimiento ojo como destino puede ser complicado. En esta sección, se resumen las principales ventajas y desafíos a tener en cuenta al diseñar la aplicación. 

### <a name="benefits-of-eye-gaze-input"></a>Ventajas de la entrada de mirada ojo
- **Sugerir de alta velocidad.** Músculo es el músculo reaccionando más rápido en nuestro cuerpo. 

- **Esfuerzo bajo.** Prácticamente ningún movimientos físicos son necesarios. 

- **Implícito.** Información acerca de los movimientos de ojo de un usuario a menudo se describen los usuarios como "cuenta de lectura", permite que el sistema sepa qué destino utilizar los planes de usuario para ponerse en contacto con. 

- **Canal de entrada alternativo.** Mirada ojo puede proporcionar una entrada auxiliar eficaz para la mano y voz entrada creación en años de experiencia de los usuarios según su coordinación de ojo de mano.

- **Atención Visual.** Otra ventaja importante es la posibilidad de deducir qué un usuario está prestando atención a. Esto puede ayudar a en varias áreas de la aplicación que abarcan desde más evaluar eficazmente diseños diferentes para ayudar en las Interfaces de usuario más inteligentes y mejorado sociales indicaciones para la comunicación remota.

En pocas palabras, mediante mirada ojo como entrada potencialmente ofrece una señal contextual rápida y sin esfuerzo - esto es especialmente eficaz en combinación con otras entradas como *voz* y *manual* como entrada para Confirme que la intención del usuario.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafíos del ojo que mirar como entrada
Una gran cantidad de energía, conlleva una gran cantidad de responsabilidad: Aunque mirada ojo se puede usar para crear experiencias de usuario mágica sentir como un héroe, también es importante saber lo que no es bueno para la cuenta para este adecuadamente. En la siguiente tabla, se describen algunos *desafíos* a tener en cuenta y cómo abordarlos cuando se trabaja con la entrada de mirada ojos: 

- **Su mirada ojo está "siempre activado"** el momento de abrir tapas de sus ojos, los ojos iniciar fixating cosas en su entorno. Reacción a cada aspecto marca y emitir accidentalmente potencialmente acciones porque se ve algo para resultaría demasiado tiempo en una experiencia terrible!
Es por esta razón se recomienda combinar el efecto de ojos mirada con un *comandos de voz*, *entregar gesto*, *clic de botón* o extendido permanencia para desencadenar la selección de un destino.
Esta solución también admite un modo en que el usuario puede buscar libremente en torno a sin la sensación de desencadenar involuntariamente algo abrumador. Este problema también debe tenerse en cuenta al diseñar los comentarios visuales y auditivos cuando simplemente mirar un destino.
No sobrecargar el usuario con los efectos inmediatos de emergente o mantenga el mouse sonidos. Matiz es clave. Trataremos algunas prácticas recomendadas para esto aún más, a continuación al hablar sobre recomendaciones de diseño.

- **Observación frente a control** suponga que desea alinear una fotografía en su muro de forma precisa. Examine sus bordes y sus alrededores para ver si también alinea. Ahora imagine cómo podría hacerlo cuando desee utilizar su mirada ojo como entrada para mover la imagen al mismo tiempo. Difícil, ¿no? Esto describe el rol de doble de mirada ojo cuando sea necesario tanto para la entrada y el control. 

- **Deje esta opción antes de hacer clic:** Selecciones de destino rápido, investigaciones han demostrado que mirada de ojo de un usuario puede pasar antes de concluir un clic manual (por ejemplo, un airtap). Por lo tanto, se debe prestar especial atención a la sincronización de la señal de ojo rápida mirada con entrada de control más lenta (por ejemplo, voz, manos, controlador).

- **Destinos pequeños:** ¿Sabe lo que se siente al intentar leer el texto que simplemente es un poco demasiado pequeño para leer cómodamente? ¿Esta sensación agotar sus ojos que hacerle sentir cansados y gastados out porque intenta reajustar los ojos centrarse mejor?
Se trata de una sensación que puede invocar en los usuarios cuando se le obliga a seleccionar destinos demasiado pequeños en la aplicación con los ojos destinatarios.
Para el diseño, para crear una experiencia agradable y cómoda para los usuarios, se recomienda que los destinos deben ser al menos 2° en ángulo visual, preferiblemente mayor.

- **Desiguales movimientos de ojo mirada** los ojos realizan movimientos rápidos de fijación a fijación. Si observa las rutas de acceso de análisis de movimientos de ojo grabado, puede ver que parecen desiguales. Los ojos mover rápidamente y en saltos espontáneos en comparación con *mirada principal* o *entregar movimientos*.  

- **Seguimiento de la confiabilidad:** Seguimiento de la precisión de los ojos pueden degradar un poco en cambiar la luz como sus ojos ajustar a las nuevas condiciones.
Aunque esto no debería necesariamente afectar al diseño de su aplicación, como la precisión debe estar dentro de la limitación de 2° mencionada anteriormente. Puede significar que el usuario tiene que ejecutar otro calibración. 


### <a name="design-recommendations"></a>Recomendaciones de diseño
En la siguiente tabla, se enumeran las recomendaciones de diseño específicas en función de las ventajas que se describe y desafíos para el ojo que mirar entrada:

1. **Mirada ojo! = mirada Head:**
    - **Tenga en cuenta si rápidas ojo desiguales movimientos ajustan su tarea de entrada:** Aunque nuestro movimientos rápidos e irregulares de ojos son excelentes seleccionar rápidamente los destinos a través de nuestro campo de visión, es menos aplicable para las tareas que requieren smooth trayectorias de entrada (por ejemplo, para dibujar o redes de cerco anotaciones). En este caso, debe preferirse mano o head apunta.
  
    - **Evite asociar algo directamente a la mirada de ojo del usuario (por ejemplo, un control deslizante o cursor).**
En el caso de un cursor, esto puede producir el efecto "eluden cursor" debido a la ligeros desplazamientos de la señal de mirada ojo proyectado. En el caso de un control deslizante, entra en conflicto con el rol de doble de controlar el control deslizante con los ojos también desean comprobar si el objeto está en la ubicación correcta. En pocas palabras, los usuarios pueden rápidamente sentirse abrumado y distrae, especialmente si la señal es imprecisa para ese usuario. 
  
2. **Combinar mirada ojo con otras entradas:** La integración de ojo de seguimiento con otras entradas, como los gestos de mano, los comandos de voz o presionar el botón, tiene varias ventajas:
    - **Permitir la observación de forma gratuita:** Dado que el rol principal de los ojos es observar nuestro entorno, es importante para permitir que los usuarios buscar sin activar cualquiera (visuales, auditivas,...) comentarios o acciones. 
    La combinación de ET con otro control de entrada permite para la transición sin problemas entre los modos de control de entrada y observación ET.
  
    - **Proveedor de contexto eficaces:** Utilizando la información acerca de que el usuario está viendo durante la puesta en circulación un comando de voz o permite realizar un gesto de mano sin esfuerzo canalizar la entrada en el campo de visión. Algunos ejemplos son: "De manera no existe" rápidamente con fluidez y seleccione simplemente mirar un destino y un destino para colocar un holograma a través de la escena. 

    - **Es necesario para la sincronización de las entradas multimodales (problema de "dejar antes de hacer clic"):** Combinación rápida ojo movimientos más complejos entradas adicionales (por ejemplo, los comandos de voz larga o gestos de mano) soporta el riesgo de continuar con su mirada ojo antes de finalizar el comando de entrada adicional. Por lo tanto, si crea sus propios controles de entrada (por ejemplo, gestos de mano personalizado), asegúrese de que inicien sesión desde el principio de esta duración de entrada o aproximado para correlacionarlos con lo que un usuario tenía centra en acertar en el pasado.
    
3. **Comentarios sutiles para entrada de seguimiento de los ojos:** Es útil proporcionar comentarios si un destino es examinado (para indicar que el sistema funciona según lo previsto) pero debe mantenerse sutil. Esto puede incluir la lentitud de fusión de entrada/salida información destacada de visual o realizar otros comportamientos sutiles de destino, como movimientos lentos (por ejemplo, incrementando el destino ligeramente) para indicar que el sistema detectó correctamente que el usuario está viendo un destino, sin embargo, innecesariamente interrumpir el flujo de trabajo del usuario actual. 

4. **Evitar aplicar movimientos ojo no naturales como entrada:** No fuerce a los usuarios realizar movimientos de ojo específico (gestos mirada) para desencadenar acciones en la aplicación.

5. **Cuenta las imprecisiones:** Podemos distinguir dos tipos de las imprecisiones que son visibles para los usuarios: Desplazamiento y vibración. La manera más fácil a los desplazamientos de la dirección es proporcionar destinos lo suficientemente grandes para interactuar con (> 2° en ángulo visual – como referencia: la vista en miniatura es aproximadamente 2° en ángulo visual cuando estire el brazo (1)). Esto conduce a la siguiente orientación:
    - No fuerce a los usuarios seleccionar destinos diminutos: Investigación ha demostrado que si los destinos son lo suficientemente grandes (y el sistema está diseñado también), los usuarios describir la interacción como mágica y sin esfuerzo. Si los destinos se vuelven demasiado pequeños, los usuarios describen la experiencia como cansado y frustrante.
    
# <a name="eye-gaze-design-guidelines-placeholder"></a>Instrucciones de diseño de ojo mirada (marcador de posición)

Con el 2 de HoloLens, tenemos la gran oportunidad para realizar mirada & confirmación más rápido y más cómodo con efecto de ojos mirada en lugar de mirada principal. Sin embargo, la mirada ojo se comporta de forma muy distinta a principal mirada en ciertos aspectos y, por tanto, incluye una serie de desafíos únicos. En instrucciones de diseño que mirar ojos, se resumen las ventajas y desafíos a tener en cuenta al usar el seguimiento de ojo como un medio de entrada en la aplicación holográfica. En esta sección, nos centramos en las consideraciones de diseño específicas para mirada ojo & confirmación. En primer lugar, los ojos mover increíblemente rápido y, por tanto, son una excelentes destino rápidamente en la vista. Esto hace que ojo que mirar ideal para una mirada rápida y confirmar acciones, especialmente cuando se combina con confirmaciones rápidas como un botón o pulsar en el aire press.

No mostrar un cursor: Aunque es casi imposible interactuar sin un cursor cuando se usa el encabezado que mirar, el cursor se vuelve rápidamente que distraen y molestos cuando se usa la mirada de ojos. En lugar de depender de un cursor para informar al usuario detecta la actualmente buscar si rastreo ocular funciona y tiene correctamente en el destino, use sutiles visual resalta (más detalles a continuación).

Se esfuerzan por lograr comentarios sutiles activable combinada: Lo que parece excelentes comentarios visuales para mirada principal puede dar lugar a experiencias terribles abrumadores mediante mirada ojos. Recuerde que los ojos son extremadamente rápidos, darting rápidamente entre los puntos en el campo de la vista. Cambios de resaltado repentino rápido (activar/desactivar) pueden dar lugar flickery comentarios cuando echando un vistazo. Por lo tanto, al proporcionar comentarios al mantener el mouse, se recomienda usar un área resaltada de mezcla sin problemas (y blended horizontal comparada ausente). Esto significa que al principio apenas observaría los comentarios en un destino. En el transcurso de 500-1000 ms el resaltado aumentaría en intensidad. Mientras que los usuarios inexpertos podrían seguir buscando en el destino para asegurarse de que el sistema ha determinado correctamente el destino centrado, usuarios expertos rápidamente podrían observación & se confirman sin esperar a que los comentarios son en su máxima intensidad. Además, también se recomienda usar una mezcla de salida cuando se atenúa, los comentarios al mantener el mouse. Investigación ha demostrado que los cambios rápidos de movimiento y el contraste son muy notables en su visión periférico (por lo tanto, el área de campo visual donde no desea). El fundido de salida no tiene que ser tan lenta como en blend. Esto solo es importante cuando disponga de contraste alto o cambios de color para el resaltado. Si los comentarios al mantener el mouse eran bastante sutil para empezar, probablemente no notará ninguna diferencia.

Busque señales mirada y confirmar la sincronización: La sincronización de señales de entrada puede ser menor de un desafío para simple mirada & confirmación, por lo tanto, no se preocupe! Es algo a tener en cuenta en caso de que desea usar acciones de confirmación más complicadas aunque puede implicar a los comandos de voz larga o gestos de mano complicada. Imagine que mire diana y emitido un comando de voz largo. Tenga en cuenta el tiempo que necesita para hablar y el momento en que el sistema necesita para detectar lo que dicho, su mirada ojo normalmente larga cambió a algún nuevo destino de la escena. Por lo tanto, puede hacer que los usuarios tener en cuenta que es posible que deba seguir buscando en un destino hasta que se le ha reconocido el comando o controlar la entrada en una forma de determinar desde el principio del comando y lo que el usuario había estado viendo entonces.

## <a name="see-also"></a>Vea también
* [Mirada y confirmación](gaze-and-commit.md)
* [Mirada HEAD destinadas a](gaze-targeting.md)
* [Gestos](gestures.md)
* [Diseño de la voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
* [Comodidad](comfort.md)
