---
title: Mirada y permanencia
description: Información general sobre el modelo de entrada de mirada y permanencia
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Diseñar la realidad, mirada, permanencia, interacción, mixta
ms.openlocfilehash: a50ae948a351f5152ebb98778da9be8c08090d72
ms.sourcegitcommit: 222cba2d622b47f75949bf8af80d5c62de4dceab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "64914611"
---
# <a name="gaze-and-dwell"></a>Mirada y permanencia

Cuando las manos están ocupadas con herramientas y los elementos, gestos pueden ser tedioso o imposible.  Comandos de voz, como movimiento, pueden resultar poco confiables, por ejemplo en condiciones excesivamente altos.  Además, el uso de voz a los equipos de control no es aún una interacción estándar, pero ciertamente está ganando vapor!  Mirada permanencia ofrece el mecanismo más familiar y fácil de patrón para sobreimpresa trabajo manos libres en HoloLens.  Además, mirada permanencia es 100% confiable independientemente de las restricciones de interferencias ni silencio de ruido en el entorno operativo.

## <a name="goals"></a>Objetivos

Proporcionan un mecanismo para interacciones completa manos libres, sin utilizar la voz.

## <a name="design-principles"></a>Principios de diseño

1. Mirada no es un arma
    
    Mirada requiere comentarios visuales para la interacción intuitiva, pero pueden provocar la ansiedad demasiada comentarios. Los comentarios deben ayudan a los usuarios saber lo tiene como destino, pero no selección automática en su intención. Leer texto requiere una consideración adicional para proporcionar un espacio de usuario para absorber la información antes de seleccionar.
    
2. Buscar la velocidad de Rubiales
    
    El relleno de permanencia puede tener temporizadores diferentes según el impacto de navegación: funciones utilizadas con más frecuencia generalmente se beneficiarán de tiempos más rápidos de relleno, mientras que las funciones más daños consecuenciales pueden beneficiarse de tiempos más largos de relleno. Las curvas de animación del color de relleno positivamente pueden influir en una sensación de tiempos más rápidos de relleno. Deben tener en cuenta consideraciones para habilitar la Decisión del usuario de fast/medium/lento invalidaciones de velocidad de relleno.
    
3. Diga definitivamente a efecto yo-yo

    El efecto de yo-yo (también conocido como "noche en the Roxbury") es un patrón incómodo que puede surgir de cierta selección de ubicación de contenido y los controles basados en la mirada. Por ejemplo, una barra de navegación de la lista con el botón de relleno en la parte inferior provoca un bucle de - vistazo hacia abajo para profundizaré, buscar en los resultados, busque hacia abajo para permanencia, etcetera. Este patrón resultante no resulta cómodo y debe evitarse mediante la colocación de controles de navegación en una ubicación centralizada que requiere menos atrás y adelante. Selección de ubicación de los botones de permanencia en relación con sus efectos se vuelve importante para su comodidad.

## <a name="ui-patterns"></a>Patrones de la interfaz de usuario

### <a name="high-frequency-buttons"></a>Botones de alta frecuencia
    
* Botones siguiente y atrás
  * Relleno de previo muy breve retraso (búfer del parpadeo paso elevado)
  * Los botones más grandes son más fáciles de posicionamiento con mirada
  * Bueno para no mantenerlos a la altura del ojo por lo tanto, ningún esfuerzo para interactuar en
  * Región de permanencia puede ser mayor que el icono inactivo que resulte más fácil de usar (atrás)

### <a name="low-frequency-buttons"></a>Botones de baja frecuencia
    
* Activar el menú de configuración
  * Retrasar ya relleno previo acuerdo (búfer del parpadeo paso elevado)
  * Intente mantener estos botones interfiera pathways cursor frecuentes

* Confirmaciones (es decir, flujo de análisis, los cuadros de diálogo)
  * Mostrar resaltado de la selección en el botón principal
  * Revelar permanencia destino al mismo tiempo que resalte de la selección
  * Use hincapié que rodea el icono para simplificar la interfaz de destino
  * Decisión importante, por lo que no activa el resaltado, revela permanencia destino para la revisión
        
### <a name="toggle-buttons"></a>Botones de alternancia

* Anclar
  * Estado visual clara activas e inactivas
  * Relleno radial ayuda al usuario centrarse y proporciona un curso natural 

* Opciones de configuración individuales
  * Estados desactive activas e inactivas
  * Profundizaré destinos todos en el icono circundante izquierda
  * Permanencia tiene como destino solo aparecen cuando resaltada de la selección activa
  * "Hincapié en el control deslizante" en el lado derecho para activar/desactivar configuración

### <a name="list-views"></a>Vistas de lista

* Vista de lista exploración: archivos de la guía para abrir
  * Información destacada de cursor de fila desde cualquier parte en la fila, pero no comienza permanencia
  * Cuando se resalte la fila cursor, el destino de permanencia aparece a la izquierda
  * Profundizaré siempre un círculo en el lado izquierdo del texto en todas las vistas de lista de destino
  * No se muestran que todos profundizaré destinos al mismo tiempo para evitar la interfaz de usuario repetitivo
  * Volver a usar el mismo patrón para establecer la familiaridad de la experiencia del usuario
        
* Exploración de la vista de lista - jerarquía de tareas y pasos de una guía
  * Profundizaré siempre un círculo en el lado izquierdo del texto de destino
  * Contraer o expandir la prestación de permanencia
        
* Vista de lista exploración: selección del modo
  * Siga patrones establecidas anteriormente

### <a name="contextual-buttons"></a>Botones contextuales

* Mostrar u ocultar 3D - muestra copia en 3D a lo largo de anclaje cerca hologramas 
  * Estado visual clara activas e inactivas

### <a name="pivots"></a>Tablas dinámicas

* Lista de recientes/All guías
  * Rellenar la prestación de la interfaz de usuario que queda para indicar qué pestaña está activa
  * Para los ejes corto de una sola palabra, decidimos omitan el patrón de destino de permanencia
  * Se prefiere la interfaz simplificada destinos de otro círculo 2 y una interfaz de usuario más amplia
  * En nuestro caso, son lo suficientemente cortos para que un retraso proporciona suficiente confort antes de rellenar las palabras


## <a name="ux-guidelines-and-best-practices"></a>Directrices de experiencia de usuario y procedimientos recomendados

### <a name="target-sizes"></a>Tamaños de los destinos

  * Tamaño mínimo del icono de PIN: 6cm en el espacio global en Unity, 30 MRU (30cm @ 2m)
  * ¿Son los destinos "magnetizar" o "permanente" en absoluto? (es decir, que mirar suavizado del cursor)

### <a name="animation"></a>Animación

  * Retraso antes de permanencia desencadenadores visual .5sec
  * Duración del objeto visual de permanencia 1,2 s
  * ¿Animación de curva?

### <a name="visual-feedback"></a>Información visual

  * Relleno radial de ubicación de inicio del cursor de mirada
  * Relleno radial siempre desde el centro del botón. Una respuesta coherente es menos confusa que todas las direcciones diferentes en los botones diferentes. 
    * Esta regla puede interrumpirse aunque interacciones direccionales (p. ej., nav arriba/abajo/izquierda/derecha, etcetera.). Por ejemplo, a la derecha hace que las guías una excepción en la siguiente y atrás ha dejado rellenos.
    * Considere la posibilidad de invertir radial relleno desde fuera (si alternancia desactivado). Inversa sensación de pulsar un botón es un práctico patrón visual para mantener. 

### <a name="progressive-disclosure"></a>Revelación progresiva

 * Revelación progresiva significa que el destino de permanencia se revela en resaltado (por ejemplo, en un control de lista)
 * Revela información destacada de la barra de texto con spotlight en mirada en cualquier parte de texto
 * Destino de relleno mirada siempre aparece en la izquierda, pero solo para el elemento de lista que aparece resaltado
 * Evite tener todos los destinos de permanencia en todo momento debido a la apariencia repetitiva de círculos apiladas
 
 ## <a name="see-also"></a>Vea también
* [Manipulación directa](direct-manipulation.md)
* [Punto y confirmación](point-and-commit.md)
* [Conceptos básicos de la interacción](interaction-fundamentals.md)
* [Mirada de encabezado y confirmación](gaze-and-commit.md)
* [Mirada y voz](voice-design.md)
