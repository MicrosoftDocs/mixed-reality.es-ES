---
title: Probar una aplicación en HoloLens
description: Orientación y sugerencias para probar la aplicación de HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, las pruebas
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599977"
---
# <a name="testing-your-app-on-hololens"></a>Probar una aplicación en HoloLens

Probar las aplicaciones de HoloLens son muy similares a las pruebas de aplicaciones de Windows. Todas las áreas habituales deben considerarse (funcionalidad, interoperabilidad, rendimiento, seguridad, confiabilidad, etcetera). Sin embargo, hay algunas áreas que requieren un tratamiento especial o atención a los detalles que no se observan normalmente en aplicaciones de PC o teléfono. Aplicaciones holográficas deben ejecutar sin problemas en una amplia variedad de entornos. También debe mantener el rendimiento y comodidad en todo momento. En este tema se detallan las instrucciones para probar estas áreas.

## <a name="performance"></a>Rendimiento

Aplicaciones holográficas deben ejecutar sin problemas en una amplia variedad de entornos. También debe mantener el rendimiento y comodidad en todo momento. Rendimiento es tan importante para la experiencia del usuario con una aplicación holográfica que tenemos un tema completo dedicado a él. Asegúrese de leer y seguir el [análisis de rendimiento para Mixed Reality](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Las pruebas 3D en 3D
1. **Pruebe su aplicación en diferentes espacios tantos como sea posible.** Pruebe en salas big, salas de pequeñas, baños, cocinas, dormitorios, oficinas, etcetera. También tiene en salas de cuenta con características no estándar como paredes no verticales, curvas paredes, techos no horizontal. ¿Funciona bien al realizar la transición entre las habitaciones, suelos, pasar por los vestíbulos o escaleras?
2. **Pruebe su aplicación en diferentes condiciones de iluminación.** Responde correctamente a distintas condiciones ambientales como iluminación, negras superficies, superficies transparente reflectantes como reflejos, paredes de vidrio, etcetera.
3. **Pruebe su aplicación en condiciones diferentes de movimiento.** Colocar en el dispositivo y probar los escenarios en distintos Estados de movimiento. ¿Responde correctamente al movimiento diferentes o en estado estable?
4. **Probar el funcionamiento de la aplicación desde distintos ángulos.** Si tiene un holograma mundo bloqueado, ¿qué ocurre si el usuario se describe detrás de él? ¿Qué ocurre si se trata de algo entre el usuario y el holograma? ¿Qué ocurre si el usuario examina el holograma de encima o debajo de?
5. **Utilice las pistas de audio y espaciales.** Asegúrese de que la aplicación usa para evitar que el usuario perderse.
6. **Pruebe la aplicación en diferentes niveles de ruido ambiental.** Si ha implementado los comandos de voz, intente invocar a ellos con diferentes niveles de ruido ambiental.
7. **Probar su aplicación sentado y permanentes**. Asegúrese de probar de asientos y posiciones permanente.
8. **Probar la aplicación desde diferentes distancias**. ¿Elementos de interfaz de usuario se pueden leer e interactuar con ellos desde muy lejos? ¿Hace la aplicación de react para los usuarios reciban demasiado a sus hologramas?
9. **Probar la aplicación con las interacciones de la barra de aplicación habituales**. Todos los iconos de aplicación y las aplicaciones universales de 2D tienen un [barra de la aplicación](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) que le permite controlar cómo la aplicación se sitúa en el mundo mixto. Asegúrese de que al hacer clic en Quitar finaliza correctamente el proceso de aplicación y que el botón Atrás se admite en el contexto de la aplicación universal 2D. Pruebe a escalar y cómo migrar una aplicación [ajustar modo](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) cuando está activo y si bien es un icono de aplicación suspendida.

### <a name="environmental-test-matrix"></a>Matriz de prueba del entorno

![Matriz de pruebas del entorno de desarrollo de aplicaciones de HoloLens](images/environment-matrix-600px.png)

## <a name="comfort"></a>Comodidad
1. **Planos de recorte.** Estar atento al lugar donde [se representan hologramas](hologram-stability.md#hologram-render-distances).
2. **Evitar movimiento virtual incoherente con el movimiento real.** Evitar mover la cámara de forma que no sea representativo del movimiento real del usuario. Si la aplicación requiere mover al usuario a través de una escena, que el movimiento predecible, minimizar la aceleración y permiten al usuario controlar el movimiento.
3. **Siga las instrucciones de calidad holograma.** Las aplicaciones de alto rendimiento que implementan la [Guía de calidad holograma](hologram-stability.md) tienen menos probabilidades de provocar malestar de usuario.
4. **Distribuir hologramas horizontalmente en lugar de verticalmente.** Obligar al usuario a gastar largos períodos de tiempo buscando o hacia abajo puede dar lugar a fatiga en el cuello.

## <a name="input"></a>Entrada

### <a name="gaze-and-gestures"></a>Mirada y gestos

[Observación](gaze.md) es un formulario básico de entrada en HoloLens que permiten a los usuarios están destinadas a hologramas y el entorno. Visualmente puede ver dónde está destinado su mirada basándose en la posición del cursor. Es habitual para asociar el cursor mirada a un cursor del mouse.

[Los gestos](gestures.md) indican cómo se interactúa con hologramas, como un clic del mouse. La mayoría del tiempo los comportamientos de mouse y toque son los mismos, pero es importante comprender y validar cuando se diferencian.

**Validar cuando la aplicación tiene un comportamiento diferente con el mouse y toque.** Esto identificará las incoherencias y ayudar a tomar decisiones de diseño para facilitar la experiencia más natural a los usuarios. Por ejemplo, puede desencadenar una acción basada en mantener el mouse.

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

### <a name="custom-voice-commands"></a>Comandos de voz personalizado

[Entrada de voz](voice-input.md) es una forma natural de interacción. Puede ser la experiencia del usuario mágica o confuso según la elección de los comandos y cómo exponer. Como regla general, no se deben usar comandos de voz del sistema como "Select" o "Hola Cortana" como comandos personalizados. Estos son algunos puntos a tener en cuenta:
1. **Evite usar los comandos que suenan de forma similares.** Potencialmente, esto puede desencadenar el comando incorrecto.
2. **Elija fonéticamente enriquecidas palabras cuando sea posible.** Esto se minimizar o evitar las activaciones falsas.

### <a name="peripherals"></a>Periféricos

Los usuarios pueden interactuar con la aplicación a través de [periféricos](hardware-accessories.md). Las aplicaciones no es necesario hacer nada especial para aprovechar las ventajas de esa funcionalidad, sin embargo, hay un par de cosas que vale la pena comprobar.
1. **Validar interacciones personalizadas.** Cosas como métodos abreviados de teclado para la aplicación.
2. **Validar el cambio de tipos de entrada.** Al intentar usar varios métodos de entrada para completar una tarea, como voz, gestos, mouse y teclado en el mismo escenario.

## <a name="system-integration"></a>Integración de sistemas

### <a name="battery"></a>Batería

Probar la aplicación sin una fuente de alimentación conectada para entender rápidamente cómo agota la batería. El estado de la batería uno puede comprender fácilmente echando un vistazo a las lecturas de LED de alimentación. ![Estados de LED que indican la batería](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a>Transiciones de estado de energía

Validar escenarios clave trabajo según lo esperado al realizar la transición entre Estados de energía. Por ejemplo, ¿la aplicación permanece en su posición original? ¿Conserva su estado correctamente? ¿Sigue funcionando según lo previsto?
1. **Modo de espera y reanudar.** Para entrar en suspensión, uno puede presione y suelte el botón de encendido inmediatamente. El dispositivo también entrará en suspensión automáticamente después de 3 minutos de inactividad. Para reanudar el modo de espera, uno puede presione y suelte el botón de encendido inmediatamente. El dispositivo también se reanudará si conectar o desconectar de una fuente de alimentación.
2. **Apagar o reiniciar.** Para apagar, presione y mantenga el botón de encendido continuamente durante 6 segundos. Para reiniciar, presione el botón de encendido.

### <a name="multi-app-scenarios"></a>Escenarios con varias aplicaciones

Validar la funcionalidad de aplicación principal al cambiar entre las aplicaciones, especialmente si se ha implementado una tarea en segundo plano. Copiar y pegar y la integración de Cortana son también vale la pena comprobar si procede.

## <a name="telemetry"></a>Telemetría

Uso de telemetría y análisis como guía. Integración de análisis en la aplicación le ayudará a obtener información acerca de la aplicación de los evaluadores de Beta y a los usuarios finales. Estos datos se pueden utilizar para ayudar a optimizar la aplicación antes de su envío a la Store y las actualizaciones futuras. Hay muchas opciones de análisis. Si no está seguro de dónde empezar, consulte [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Preguntas que debe considerar:
1. ¿Cómo los usuarios usan el espacio?
2. ¿Cómo es la aplicación de colocar los objetos del mundo, puede detectar problemas?
3. ¿Cuánto tiempo dedican en distintas fases de la aplicación?
4. ¿Cuánto tiempo dedican en la aplicación?
5. ¿Cuáles son las rutas de acceso de uso más comunes a los usuarios intentan?
6. ¿Los usuarios alcanzan estados inesperados y errores?

## <a name="emulator-and-simulated-input"></a>Emulador y entrada simulado

El [emulador de HoloLens](using-the-hololens-emulator.md) es una excelente manera de probar de forma eficaz la aplicación holográfica con una variedad de características de los usuarios simulados y espacios. Estas son algunas sugerencias para usar eficazmente el emulador para probar la aplicación:
1. **Use salas virtuales del emulador para expandir sus pruebas.** El emulador incluye un conjunto de salas virtuales que puede usar para probar la aplicación en entornos aún más.
2. **Usar el emulador para ver la aplicación desde todos los ángulos.** Las teclas RE PÁG/PageDn hará que el usuario simulado sean más alto o más corto.
3. **Probar la aplicación con un HoloLens real.** El emulador de HoloLens es una excelente herramienta para ayudarle rápidamente iterar en una aplicación y detectar errores nuevos, pero asegúrese de probar también en un HoloLens físico antes de enviarlo a la Store Windows. Esto es importante para asegurarse de que el rendimiento y la experiencia son excelentes en hardware real.

## <a name="automated-testing-with-perception-simulation"></a>Pruebas automatizadas con la percepción de simulación

Algunos desarrolladores de aplicaciones es posible que desee automatizar pruebas de sus aplicaciones. Más allá de las pruebas unitarias simple, puede usar el [simulación percepción](perception-simulation.md) pila en HoloLens para automatizar la entrada humana y mundial a su aplicación. La API de simulación de percepción puede enviar entrada simulado para el emulador de HoloLens o un HoloLens físico.

## <a name="windows-app-certification-kit"></a>Kit para la certificación de aplicaciones en Windows

Para proporcionar la mejor oportunidad de que se va a la aplicación [publicados en el Store Windows](submitting-an-app-to-the-microsoft-store.md), validar y probar localmente antes de enviarla para su certificación. Si la aplicación tiene como destino la familia de dispositivos Windows.Holographic, el [Windows App Certification Kit](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) sólo ejecutará las pruebas de análisis estático local en su PC. No hay ninguna prueba se ejecutará en su HoloLens.

## <a name="see-also"></a>Vea también
* [Envío de una aplicación para el Store de Windows](submitting-an-app-to-the-microsoft-store.md)
