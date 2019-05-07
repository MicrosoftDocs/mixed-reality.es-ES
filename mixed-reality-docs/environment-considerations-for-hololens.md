---
title: Consideraciones sobre el entorno de HoloLens
description: Obtener la mejor experiencia posible con HoloLens al optimizar el dispositivo para su entorno y los ojos. Muchos factores diferentes se fusionan conjuntamente para habilitar el seguimiento, pero como desarrolladora de realidad mixta, hay varios factores que puede tener en cuenta al optimizar un espacio para una mejor hologramas.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: marco holográfica, campo de visión, fov, calibración, espacios, entorno, procedimientos
ms.openlocfilehash: 0070455792e09cd59741362b201ca6b7b9af0aec
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670179"
---
# <a name="environment-considerations-for-hololens"></a>Consideraciones sobre el entorno de HoloLens

HoloLens combina holográfica con el mundo "real", colocar hologramas en su entorno. Una ventana de aplicación holográfica "bloquea" en la pared, una ballerina holográfica gira sobre el sobremesa, oídos conejo posicionarse por encima de la cabeza de su amigo involuntario. Cuando se usa una aplicación o juego envolvente, el mundo holográfico distribuirán para rellenar respecto a su entorno, pero aún podrá ver y moverse por el espacio.

El hologramas que coloca permanecerá donde ha colocado en él, incluso si desactiva el dispositivo. 

## <a name="setting-up-an-environment"></a>Configurar un entorno

Los dispositivos HoloLens saben cómo colocar hologramas estables y precisas por *seguimiento* a los usuarios en un espacio. Sin seguimiento adecuado, el dispositivo no entiende el entorno o el usuario dentro de él - para que hologramas pueden aparecer en los lugares incorrectos, no aparecen en la misma posición cada vez o no aparecen en absoluto.

Seguimiento del rendimiento se ve influenciado por el usuario está en el entorno de y ajuste de un entorno para inducir a seguimiento estable y coherente es un arte en lugar de una ciencia. Muchos factores diferentes se fusionan conjuntamente para habilitar el seguimiento, pero como desarrolladora de realidad mixta, hay varios factores que puede tener en cuenta al optimizar un espacio para un mejor seguimiento.
 
### <a name="lighting"></a>Iluminación
Windows Mixed Reality usa luz visual para realizar un seguimiento de la ubicación del usuario. Cuando un entorno es demasiado intensa, pueden obtener saturadas las cámaras y se ve nada. Si el entorno es demasiado oscuro, las cámaras no se pueden recoger información suficiente y se ve nada. La iluminación debe ser incluso y lo suficientemente claro que una persona puede ver sin esfuerzo, pero no tan brillantes que es difícil mirar la luz.

Las áreas donde hay puntos de luz brillante en un área general dim también son problemáticos, ya que la cámara tiene que ajustar al mover de entrada y salida de espacios brillantes. Esto puede causar que el dispositivo "perderse" y piensan que el cambio de luz equivale a un cambio en la ubicación. Los niveles de luz estables en un área dará lugar a un mejor seguimiento.

Cualquier iluminación al aire libre también puede provocar inestabilidad en la herramienta de seguimiento, como el sol puede variar considerablemente con el tiempo. Por ejemplo, el seguimiento en el mismo espacio en el verano frente a invierno puede producir resultados muy diferentes, como la luz secondhand fuera puede ser más alto en distintos momentos del año.

Si tiene un luxmeter, una constante lux 500-1000 es un buen lugar para comenzar. 

#### <a name="types-of-lighting"></a>Tipos de iluminación
También pueden afectar a diferentes tipos de luz en un espacio de seguimiento. Bombillas pulso con la electricidad AC practicando - si la frecuencia de CA es 50Hz, a continuación, la luz impulsos a 50Hz. Para que las personas, no se observa este pulso. Sin embargo, cámara de 30fps de HoloLens ve estos cambios: estarán bien iluminados algunos marcos, iluminados mal algunas y algunas se exceso expondrá tal y como se trata de la cámara compensar la luz pulsos.

En Estados Unidos, frecuencia de electricidad estándar es 60Hz, por lo que la bombilla pulsos se armonización con velocidad de fotogramas de HoloLens: 60Hz pulsos se alinean con la velocidad de fotogramas de Hololens 30 FPS. Sin embargo, muchos países tienen un estándar de la frecuencia de CA de 50Hz, lo que significa que algunos marcos de Hololens se tomarán durante pulsos, y otras no. En concreto, se sabe fluorescentes en Europa que cause problemas. 

Hay algunas cosas que puede intentar resolver los problemas que parpadean. Temperatura, la antigüedad de bombilla y ciclos de preparación son las causas comunes de parpadeo fluorescentes y reemplazando las bombillas puede ayudar. También pueden ayudar apriete bombillas y asegurándose de que dibuja actual es constante. 

### <a name="items-in-a-space"></a>Elementos de un espacio
HoloLens usa puntos de referencia del entorno únicos, también conocido como *características*, para buscar el propio en un espacio. 

Un dispositivo no puede realizar un seguimiento casi nunca en un área de característica deficiente, como el dispositivo no tiene ninguna manera de saber que en el espacio se trata. Agregar características a los planos laterales de un espacio suele ser una buena forma de mejorar el seguimiento. Pósteres, los símbolos pegado en una pared, plantas, objetos únicos u otros elementos similares toda la Ayuda. Un departamento de soporte técnico desorganizado es un buen ejemplo de un entorno que conduce a seguimiento buena, pero hay muchas características diferentes en una única área. 

Además, puede usar características únicas en el mismo espacio. El mismo póster repetida varias veces en una pared, por ejemplo, hará que confusión de dispositivo como el HoloLens no sabrá cuál de los pósteres repetitivos que está viendo. Una forma habitual de agregar características únicas es usar las líneas de la cinta de enmascaramiento para crear un único, nonrepetitve patrones a lo largo de las paredes y el límite inferior de un espacio. 

¿Es una buena pregunta preguntarse - si ve solo una pequeña cantidad de la escena, forma exclusiva encontró usted mismo en el espacio? De lo contrario, es probable que el dispositivo tiene problemas para así de seguimiento.

#### <a name="wormholes"></a>Túneles espaciales
Si tiene dos áreas o las regiones que tenga el mismo aspecto, puede considerar la herramienta de seguimiento son iguales. Este se produce en el dispositivo propio engañar creyendo que está en otro lugar. Llamamos a estos tipos de áreas repetitivas *túneles espaciales*. 

Para evitar túneles espaciales, intente evitar áreas idénticas en el mismo espacio. Áreas idénticas en ocasiones pueden incluir las estaciones de fábrica, windows en un edificio, soportes de servidores o estaciones de trabajo. Áreas de etiquetado o agregar características únicas para cada áreas parecidas puede ayudar a mitigar túneles espaciales.
 
### <a name="temporal-stability-of-a-space"></a>Estabilidad temporal de un espacio
Si su entorno cambiante y cambiando constantemente, el dispositivo no tiene ninguna característica estable para buscar en. 

Los objetos más móviles que están en un espacio, incluidas las personas, más fácil es a perder el seguimiento. Mover cintas transportadoras, los elementos en distintos Estados de construcción y una gran cantidad de personas en un espacio de todos se sabe que causar problemas de seguimiento.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Proximidad del usuario a los elementos en el espacio
De forma similar a cómo los seres humanos no centran así en objetos cerca de los ojos, HoloLens batalla cuando los objetos estén cerca de su cámaras. Si un objeto es demasiado cerca de verse con dos cámaras, o si un objeto está bloqueando una cámara, el dispositivo tendrá mucho más problemas con el seguimiento en el objeto. 

Ver las cámaras no menos de 15cm desde un objeto.
 
### <a name="surfaces-in-a-space"></a>Superficies de un espacio
Las superficies reflectantes fuertemente probablemente será diferentes según el ángulo, lo que afecta al seguimiento. Piense en un automóvil nuevo - cuando se mueve alrededor de ella, la luz refleja y verá diferentes objetos en la superficie de medida que se desplaza. En la herramienta de seguimiento, los distintos objetos que reflejan en la superficie representan un entorno cambiante y pierde el dispositivo el seguimiento.

Son más fáciles de hacer un seguimiento con menos objetos brillantes.

### <a name="wifi-fingerprint-considerations"></a>Consideraciones de huellas digitales de Wi-Fi
Siempre y cuando se habilita la Wi-Fi, datos del mapa se correlacionan con una huella digital de Wi-Fi, incluso cuando no está conectado a un red Wi-Fi real o enrutador. Sin información de Wi-Fi, pueden ser ligeramente más lentas para que reconozca el espacio y hologramas. Si se cambian significativamente las señales Wi-Fi, puede considerar el dispositivo está en un espacio diferente por completo.

Identificación de red (es decir, el SSID, dirección MAC) no se envía a Microsoft y WiFi todas las referencias se mantienen de forma locales en el HoloLens.

## <a name="mapping-new-spaces"></a>Nuevos espacios de asignación
Cuando escriba un nuevo espacio (o cargar uno ya existente), verá un gráfico de malla propagándose por el espacio. Esto significa que el dispositivo está [respecto a su entorno de asignación](spatial-mapping-design.md). 

Si tiene problemas para colocar hologramas, intente deambulan el espacio para que HoloLens pueden asignar más completa. 

Si su HoloLens no pueden asignar el espacio o está fuera de calibración, puede especificar el modo Limited. En el modo Limited, no podrá colocar hologramas en su entorno.

## <a name="environment-management"></a>Administración del entorno
Hay dos opciones que permiten a los usuarios para "limpiar" hologramas y causa HoloLens "olvidar" un espacio.  Existen en "Hologramas y entornos" en la aplicación de configuración, con la segunda opción también aparecen en "Privacidad" en la aplicación de configuración.

1.  Eliminar cercanas hologramas: al seleccionar esta opción, borrarán HoloLens hologramas todo anclados y todos los datos del mapa almacenado para el "espacio actual" donde se encuentra el dispositivo.  Crea una nueva sección de asignación y almacenada en la base de datos para esa ubicación una vez hologramas nuevo se colocan en el mismo espacio.

2.  Eliminar hologramas todas: al seleccionar esta opción, borrarán todos los datos del mapa HoloLens y anclados hologramas en las bases de datos completas de espacios.  No hay hologramas se se detecten y cualquier hologramas deben ubicarse recién para volver a almacenar las secciones de mapa en la base de datos.

### <a name="managing-your-spaces"></a>Administrar los espacios

Se han contraído las secciones de mapa y los diferentes espacios en una única base de datos almacenado localmente en el dispositivo HoloLens. La base de datos de asignación se almacena de forma segura, con acceso solo está disponible para el sistema interno y nunca a un usuario del dispositivo, incluso cuando conectado a un equipo o mediante la aplicación de explorador de archivos. Cuando bitlocker está habilitado, también se cifran los datos del mapa almacenado.

Varios componentes de asignación existen cuando hologramas se colocan en diferentes ubicaciones sin una ruta de acceso de conexión entre las ubicaciones/hologramas.  Se consideran hologramas anclados dentro de la misma sección del mapa "cercanos" en el espacio actual.

Hay una API para exportar un pequeño subconjunto del espacio"actual" para desarrolladores (una parte del componente de mapa que se reconoce actualmente) para habilitar escenarios holograma compartido.  Actualmente no hay ningún mecanismo para descargar la base de datos completa de todos los espacios que se han asignado.


## <a name="hologram-quality"></a>Calidad holograma

Hologramas pueden colocarse a lo largo de su entorno: alta, baja y en todo, pero verá a través de un [marco holográfica](holographic-frame.md) que se coloca delante de sus ojos. Para obtener la vista más eficaz, asegúrese de ajustar el dispositivo para que pueda ver todo el marco. Y no dude en caminar alrededor de su entorno y explorar.

Para su [hologramas](hologram.md) para buscar estable, claras y nítidas, su HoloLens necesita calibrarse solo para usted. Cuando se configura por primera vez su HoloLens, se le guiará a través de este proceso. Más adelante si no se ven bien hologramas o si ve muchos errores, puede realizar ajustes.

### <a name="calibration"></a>Calibración

Si sus hologramas busque tiemble o inestable, o si tiene problemas para colocar hologramas, lo primero que se intente el [aplicación calibración](calibration.md). Esta aplicación también puede ayudar si tiene cualquier malestar mientras usa su HoloLens.

Para llegar a la aplicación de calibración, vaya a Configuración > sistema > Utilidades. Seleccione la calibración abierto y siga las instrucciones.

Si ejecutar la aplicación de calibración y sigue teniendo problemas con calidad holograma, o si ve un mensaje de "seguimiento pierde" frecuentes, pruebe la aplicación de optimización Sensor. Vaya a Configuración > sistema > Utilidades, seleccione la optimización Sensor abierto y siga las instrucciones.

Si otra persona va a usar su HoloLens, debe ejecutar la aplicación de calibración primero por lo que el dispositivo esté configurado correctamente para ellos.

## <a name="see-also"></a>Vea también
* [Diseño de asignaciones espaciales](spatial-mapping-design.md)
* [Hologramas](hologram.md)
* [Calibración](calibration.md)
