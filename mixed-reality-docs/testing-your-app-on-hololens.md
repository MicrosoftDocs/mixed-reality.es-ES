---
title: Prueba de la aplicación en HoloLens
description: Instrucciones y sugerencias para probar la aplicación de HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, probar
ms.openlocfilehash: 9a189bf139c97fc13034d94f05aa8f5974cc19b9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437384"
---
# <a name="testing-your-app-on-hololens"></a>Prueba de la aplicación en HoloLens

Probar las aplicaciones de HoloLens es muy similar a probar aplicaciones Windows. Se deben tener en cuenta todas las áreas habituales (funcionalidad, interoperabilidad, rendimiento, seguridad, confiabilidad, etc.). Sin embargo, hay algunas áreas que requieren un tratamiento especial o prestar atención a los detalles que no suelen observarse en las aplicaciones de PC o de teléfono. Las aplicaciones holográficas deben ejecutarse sin problemas en un conjunto diverso de entornos. También necesitan mantener el rendimiento y la comodidad del usuario en todo momento. En este tema se detallan las instrucciones para probar estas áreas.

## <a name="performance"></a>Rendimiento

Las aplicaciones holográficas deben ejecutarse sin problemas en un conjunto diverso de entornos. También necesitan mantener el rendimiento y la comodidad del usuario en todo momento. El rendimiento es tan importante para la experiencia del usuario con una aplicación holográfica que tenemos un tema entero dedicado. Asegúrese de leer y seguir el [rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md) .

## <a name="testing-3d-in-3d"></a>Probar 3D en 3D
1. **Pruebe la aplicación en tantos espacios diferentes como sea posible.** Pruebe en grandes salones, pequeños salones, bathrooms, cocinas, dormitorios, oficinas, etc. También debe tener en cuenta los salones con características no estándar, como paredes no verticales, paredes curvas y límites no horizontales. ¿Funciona bien cuando se realiza la transición entre salas, suelos o escaleras?
2. **Pruebe la aplicación en condiciones de iluminación diferentes.** Responde correctamente a distintas condiciones del entorno, como la iluminación, las superficies negras, las superficies transparentes y reflectantes, como reflejos, paredes de vidrio, etc.
3. **Pruebe la aplicación en condiciones de movimiento diferentes.** Coloque en el dispositivo y pruebe sus escenarios en varios Estados de movimiento. ¿Responde correctamente a otro movimiento o estado estable?
4. **Probar el funcionamiento de la aplicación desde distintos ángulos.** Si tiene un holograma del mundo bloqueado, ¿qué ocurre si el usuario lo recorre? ¿Qué ocurre si hay algo entre el usuario y el holograma? ¿Qué ocurre si el usuario mira el holograma desde arriba o abajo?
5. **Usar indicaciones espaciales y de audio.** Asegúrese de que la aplicación los usa para evitar que se pierda el usuario.
6. **Pruebe la aplicación en distintos niveles de ruido ambiente.** Si ha implementado comandos de voz, intente invocarlos con distintos niveles de ruido ambiente.
7. **Pruebe la aplicación y su posición**. Asegúrese de probar desde el emplazamiento y las posiciones permanentes.
8. **Pruebe la aplicación desde distintas distancias**. ¿Los elementos de la interfaz de usuario pueden leerse e interactuar con ellos? ¿La aplicación reacciona a los usuarios que están demasiado cerca de sus hologramas?
9. **Pruebe la aplicación con las interacciones de la barra de aplicaciones comunes**. Todos los iconos de la aplicación y las aplicaciones universales en 2D tienen una barra de la [aplicación](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) que le permite controlar cómo se coloca la aplicación en el mundo mixto. Asegúrese de que al hacer clic en quitar se termina correctamente el proceso de la aplicación y que se admite el botón atrás en el contexto de la aplicación universal 2D. Pruebe a escalar y mover la aplicación en el [modo ajustar](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) mientras esté activa y mientras se encuentra en un icono de aplicación suspendida.

### <a name="environmental-test-matrix"></a>Matriz de pruebas de entorno

![Matriz de pruebas de entorno para el desarrollo de aplicaciones de HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a>Comodidad
1. **Planos de recortes.** Debe ser Attentive donde [se representan los hologramas](hologram-stability.md#hologram-render-distances).
2. **Evite el movimiento virtual incoherente con el movimiento de cabeza real.** Evite mover la cámara de forma que no sea representativa del movimiento real del usuario. Si su aplicación requiere mover el usuario a través de una escena, haga que el movimiento sea predecible, minimice la aceleración y deje que el usuario controle el movimiento.
3. **Siga las instrucciones de calidad de los hologramas.** Es menos probable que las aplicaciones de rendimiento que implementan la guía de calidad de los [hologramas](hologram-stability.md) resulten descomodidades del usuario.
4. **Distribuya los hologramas horizontalmente en lugar de verticalmente.** Forzar al usuario a dedicar períodos prolongados de tiempo buscando o baja puede provocar una fatiga en el cuello.


## <a name="input"></a>Entrada

### <a name="interaction-models"></a>Modelos de interacción

Asegúrese de que las interacciones de los hologramas funcionan con el [modelo de interacción](interaction-fundamentals.md)elegido.
También es una buena idea validar con accesorios diferentes, como el mouse y el teclado, si se necesitan estos accesorios para admitir la accesibilidad.

**Valide cuando la aplicación tenga un comportamiento diferente con Mouse y toque.** Esto identificará las incoherencias y ayuda a tomar decisiones de diseño para que la experiencia sea más natural para los usuarios. Por ejemplo, desencadenar una acción basada en el desplazamiento.


### <a name="custom-voice-commands"></a>Comandos de voz personalizados

La [entrada de voz](voice-input.md) es una forma natural de interacción. La experiencia del usuario puede ser mágica o confusa en función de los comandos elegidos y de cómo se exponen. Como norma general, no debe usar comandos de voz del sistema como "Select" o "Hola Cortana" como comandos personalizados. Estos son algunos puntos a tener en cuenta:
1. **Evite el uso de comandos que suenen de forma similar.** Esto puede desencadenar potencialmente el comando incorrecto.
2. **Elija palabras enriquecidas fonéticamente cuando sea posible.** Esto minimizará o evitará las activaciones falsas.

### <a name="peripherals"></a>Periféricos

Los usuarios pueden interactuar con la aplicación a través de [periféricos](hardware-accessories.md). Las aplicaciones no necesitan hacer nada especial para aprovechar esa capacidad, pero hay un par de cosas que merece la pena comprobar.
1. **Valida las interacciones personalizadas.** Cosas como métodos abreviados de teclado personalizados para la aplicación.
2. **Validar los tipos de entrada de conmutación.** Intentando usar varios métodos de entrada para completar una tarea, como voz, movimiento, mouse y teclado en el mismo escenario.

## <a name="system-integration"></a>Integración del sistema

### <a name="battery"></a>Batería

Pruebe la aplicación sin una fuente de alimentación conectada para comprender la rapidez con la que se agota la batería. Uno puede comprender fácilmente el estado de la batería mirando las lecturas del LED de alimentación. 

![Estados de LED que indican la energía de la batería](images/batterypowerledindication-500px.png)<br>

*Estados de LED que indican la energía de la batería*

### <a name="power-state-transitions"></a>Transiciones de estado de energía

La validación de escenarios clave funciona según lo previsto al realizar la transición entre los Estados de energía. Por ejemplo, ¿la aplicación permanece en su posición original? ¿Conserva correctamente su estado? ¿Continúa funcionando según lo previsto?
1. **Suspender/reanudar.** Para entrar en modo de espera, puede presionar y soltar el botón de encendido inmediatamente. El dispositivo también introducirá el modo de espera automáticamente después de 3 minutos de inactividad. Para reanudar desde el modo de espera, puede presionar y soltar el botón de encendido inmediatamente. El dispositivo también se reanudará si se conecta o se desconecta de una fuente de alimentación.
2. **Cierre o reinicio.** Para apagar, mantenga presionado el botón de encendido continuamente durante 6 segundos. Para reiniciarlo, presione el botón de encendido.

### <a name="multi-app-scenarios"></a>Escenarios de varias aplicaciones

Validar la funcionalidad de la aplicación principal al cambiar entre aplicaciones, especialmente si se ha implementado una tarea en segundo plano. La integración de copiar y pegar y Cortana también merece la pena comprobar si es aplicable.

## <a name="telemetry"></a>Telemetría

Use la telemetría y el análisis como guía. La integración de Analytics en la aplicación le ayudará a obtener información sobre la aplicación a los evaluadores de la versión beta y a los usuarios finales. Estos datos se pueden usar para ayudar a optimizar la aplicación antes de enviarla a la tienda y para futuras actualizaciones. Existen muchas opciones de análisis. Si no está seguro de por dónde empezar, consulte [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Preguntas a tener en cuenta:
1. ¿Cómo usan los usuarios el espacio?
2. ¿Cómo la aplicación coloca objetos en el mundo? ¿puede detectar problemas?
3. ¿Cuánto tiempo gastan en diferentes fases de la aplicación?
4. ¿Cuánto tiempo pasan en la aplicación?
5. ¿Cuáles son las rutas de acceso de uso más comunes que los usuarios están probando?
6. ¿Los usuarios visitan Estados o errores inesperados?

## <a name="emulator-and-simulated-input"></a>Emulador y entrada simulada

El [emulador de HoloLens](using-the-hololens-emulator.md) es una excelente manera de probar eficazmente la aplicación holográfica con una variedad de características y espacios de usuario simulados. Estas son algunas sugerencias para usar el emulador de forma eficaz para probar la aplicación:
1. **Use las salas virtuales del emulador para expandir las pruebas.** El emulador incluye un conjunto de salones virtuales que puede usar para probar la aplicación en incluso más entornos.
2. **Use el emulador para ver la aplicación en todos los ángulos.** Las teclas RePág/PageDn harán que el usuario simulado sea más alto o más corto.
3. **Pruebe la aplicación con una HoloLens real.** El emulador de HoloLens es una excelente herramienta para ayudarle a iterar rápidamente en una aplicación y detectar nuevos errores, pero asegúrese de probar también en una HoloLens física antes de enviarla a la tienda Windows. Esto es importante para asegurarse de que el rendimiento y la experiencia son excelentes en el hardware real.

## <a name="automated-testing-with-perception-simulation"></a>Pruebas automatizadas con simulación de percepción

Algunos desarrolladores de aplicaciones pueden querer automatizar las pruebas de sus aplicaciones. Además de las pruebas unitarias simples, puede usar la pila de [simulación de percepción](perception-simulation.md) de HoloLens para automatizar la entrada humana y internacional a su aplicación. La API de simulación de percepción puede enviar entradas simuladas al emulador de HoloLens o a HoloLens físico.

## <a name="windows-app-certification-kit"></a>Kit para la certificación de aplicaciones en Windows

Para proporcionar a la aplicación la mejor posibilidad de [publicarla en la tienda Windows](submitting-an-app-to-the-microsoft-store.md), valide y pruébelo localmente antes de enviarla para su certificación. Si la aplicación está destinada a la familia de dispositivos Windows. Holographic, el kit para la [certificación de aplicaciones de Windows](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) solo ejecutará pruebas de análisis estático local en su equipo. No se ejecutará ninguna prueba en HoloLens.

## <a name="see-also"></a>Consulta también
* [Envío de una aplicación a la tienda Windows](submitting-an-app-to-the-microsoft-store.md)
