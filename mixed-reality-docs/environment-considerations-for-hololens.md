---
title: Consideraciones de entorno para HoloLens
description: Obtenga la mejor experiencia posible mediante HoloLens al optimizar el dispositivo para los ojos y el entorno. Muchos factores ambientales diferentes se combinan para permitir el seguimiento, pero como desarrollador de realidad mixta, hay varios factores que puede tener en cuenta para optimizar un espacio para mejores hologramas.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: trama holográfica, campo de vista, campo de visualización, calibración, espacios, entorno, procedimientos
ms.openlocfilehash: 0070455792e09cd59741362b201ca6b7b9af0aec
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670179"
---
# <a name="environment-considerations-for-hololens"></a>Consideraciones de entorno para HoloLens

HoloLens combina el Holographic con el mundo "real", colocando hologramas en el entorno. Una ventana de la aplicación holográfica se "cuelga" en la pared, una ballerina holográfica gira en el Bunny de sobremesa y los oídos en la parte superior de la cabeza del amigo de involuntario. Cuando use un juego o una aplicación envolventes, el mundo holográfica se redistribuirá para rellenar su entorno, pero podrá ver y desplazarse por el espacio.

Los hologramas que coloque permanecerán donde se colocan, incluso si apaga el dispositivo. 

## <a name="setting-up-an-environment"></a>Configuración de un entorno

Los dispositivos HoloLens saben cómo colocar hologramas estables y precisos mediante el *seguimiento* de los usuarios en un espacio. Sin un seguimiento adecuado, el dispositivo no entiende el entorno o el usuario que contiene, por lo que los hologramas pueden aparecer en lugares equivocados, no aparecer en el mismo lugar cada vez o no aparecen en absoluto.

El seguimiento del rendimiento se ve afectado en gran medida por el entorno en el que se encuentra el usuario, y el ajuste de un entorno para inducir un seguimiento estable y coherente es un arte en lugar de una ciencia. Muchos factores ambientales diferentes se combinan para permitir el seguimiento, pero como desarrollador de realidad mixta, hay varios factores que puede tener en cuenta para optimizar un espacio para un mejor seguimiento.
 
### <a name="lighting"></a>Iluminación
Windows Mixed Reality usa visual Light para realizar un seguimiento de la ubicación del usuario. Cuando un entorno es demasiado brillante, las cámaras pueden saturarse y no se verá nada. Si el entorno es demasiado oscuro, las cámaras no podrán recoger suficiente información y no se verá nada. La iluminación debe ser uniforme y suficientemente brillante que un usuario pueda ver sin esfuerzo, pero no tan brillante que la luz sea doloroso.

Las áreas en las que hay puntos de luz brillante en un área de cotas generales también son problemáticas, ya que la cámara tiene que ajustarse al moverse dentro y fuera de los espacios brillantes. Esto puede hacer que el dispositivo "se pierda" y pensar que el cambio en la luz equivale a un cambio en la ubicación. Los niveles de luz estable en un área darán lugar a un mejor seguimiento.

Cualquier iluminación exterior también puede provocar inestabilidad en el seguimiento, ya que el sol puede variar considerablemente con el tiempo. Por ejemplo, el seguimiento en el mismo espacio en el verano frente a invierno puede producir resultados drásticamente diferentes, ya que la luz Secondhand fuera de puede ser más alta en distintos momentos del año.

Si tiene un Luxmeter, un 500-1000 Lux estable es un buen punto de partida. 

#### <a name="types-of-lighting"></a>Tipos de iluminación
Los distintos tipos de luz en un espacio también pueden influir en el seguimiento. Bombillas con la electricidad de CA que se ejecuta a través de ella: Si la frecuencia de la CA es de 50 Hz, la luz se pulsa en 50 Hz. Para un usuario, este pulso no se observa. Sin embargo, la cámara 30 fps de HoloLens ve estos cambios: algunos fotogramas estarán bien iluminados, algunos quedarán mal iluminados y otros se expondrán a medida que la cámara intente compensar los impulsos ligeros.

En Estados Unidos, el estándar de frecuencia de electricidad es de 60 Hz, por lo que los impulsores de bombilla se comparan con los impulsos de velocidad de bits de HoloLens con la alineación de 30 FPS de Hololens. Sin embargo, muchos países tienen un estándar de frecuencia de AC de 50 Hz, lo que significa que se realizarán algunos fotogramas de Hololens durante los impulsos, y otros no. En concreto, se sabe que la iluminación fluorescente en Europa causa problemas. 

Hay algunas cosas que puede intentar para resolver problemas de parpadeo. La temperatura, la edad de la lámpara y los ciclos de preparación son causas comunes del parpadeo de fluorescentes y la sustitución de bombillas puede resultar de ayuda. Apretar las bombillas y asegurarse de que los dibujos actuales son constantes también pueden ayudar. 

### <a name="items-in-a-space"></a>Elementos de un espacio
HoloLens usa puntos de referencia de entorno únicos, también conocidos como *características*, para buscarse en un espacio. 

Un dispositivo casi nunca realiza un seguimiento en un área de característica deficiente, ya que el dispositivo no tiene forma de saber dónde se encuentra en el espacio. Agregar características a las paredes de un espacio es normalmente una buena forma de mejorar el seguimiento. Los pósteres, los símbolos que se adquieren a una pared, plantas, objetos únicos u otros elementos similares sirven de ayuda. Un escritorio desordenado es un buen ejemplo de un entorno que conduce a un buen seguimiento: hay muchas características diferentes en una sola área. 

Además, use características únicas en el mismo espacio. El mismo póster se repite varias veces a lo largo de una pared, por ejemplo, causará confusión en el dispositivo, ya que HoloLens no sabrá cuál de los pósteres repetitivos está examinando. Una forma común de agregar características únicas es usar líneas de cinta de enmascaramiento para crear patrones únicos y nonrepetitves en las paredes y el piso de un espacio. 

Una buena pregunta que debe plantearse es: si vio solo una pequeña cantidad de la escena, ¿podría encontrarse de forma exclusiva en el espacio? Si no es así, es probable que el dispositivo también tenga problemas de seguimiento.

#### <a name="wormholes"></a>Túneles espaciales
Si tiene dos áreas o regiones que tienen el mismo aspecto, el rastreador puede pensar que son iguales. Esto da lugar a que el dispositivo se confunda en el caso de que sea algo más. Llamamos a estos tipos de áreas repetitivas, *túneles espaciales*. 

Para evitar los túneles espaciales, intente evitar áreas idénticas en el mismo espacio. A veces, las áreas idénticas pueden incluir estaciones de fábrica, ventanas en un edificio, bastidores de servidor o estaciones de trabajo. Las áreas de etiquetado o la adición de características únicas a cada una de las áreas de aspecto similar pueden ayudar a mitigar los túneles espaciales.
 
### <a name="temporal-stability-of-a-space"></a>Estabilidad temporal de un espacio
Si el entorno está cambiando y cambiando constantemente, el dispositivo no tiene características estables para localizar. 

Cuanto más se muevan los objetos que se encuentren en un espacio, incluidas las personas, más fácil será perder el seguimiento. Se sabe que todos los puntos de las correas transportadoras, los elementos en diferentes Estados de construcción y muchas personas de un espacio causan problemas de seguimiento.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Proximidad del usuario a los elementos del espacio
De forma similar al modo en que los usuarios no pueden centrarse bien en objetos cercanos a los ojos, HoloLens lucha cuando los objetos están cerca de sus cámaras. Si un objeto está demasiado cerca de verlo con ambas cámaras, o si un objeto está bloqueando una cámara, el dispositivo tendrá muchos más problemas con el seguimiento del objeto. 

Las cámaras no pueden ver más cerca de 15cm de un objeto.
 
### <a name="surfaces-in-a-space"></a>Superficies en un espacio
Las superficies muy reflectantes probablemente tendrán un aspecto diferente en función del ángulo, que afecta al seguimiento. Piense en un automóvil nuevo: cuando se desplaza por él, la luz se refleja y se ven objetos diferentes en la superficie a medida que se mueve. En el seguimiento, los distintos objetos que se reflejan en la superficie representan un entorno cambiante y el dispositivo pierde el seguimiento.

No es más fácil realizar un seguimiento de los objetos menos brillantes.

### <a name="wifi-fingerprint-considerations"></a>Consideraciones sobre las huellas digitales WiFi
Mientras WiFi esté habilitado, los datos del mapa se correlacionarán con una huella digital WiFi, incluso cuando no estén conectados a una red o enrutador Wi-Fi real. Sin la información de Wi-Fi, el espacio y los hologramas pueden ser ligeramente más lentos de reconocer. Si las señales de WiFi cambian significativamente, el dispositivo puede pensar que está en un espacio diferente.

La identificación de red (es decir, el SSID, la dirección MAC) no se envía a Microsoft y todas las referencias WiFi se mantienen en el equipo local en HoloLens.

## <a name="mapping-new-spaces"></a>Asignar nuevos espacios
Al escribir un nuevo espacio (o cargar uno existente), verá un gráfico de malla que se propaga por el espacio. Esto significa que el dispositivo está [asignando su entorno](spatial-mapping-design.md). 

Si tiene problemas para colocar hologramas, intente desplazarse por el espacio para que HoloLens pueda asignarlo más completo. 

Si HoloLens no puede asignar espacio o está fuera de la calibración, puede entrar en modo limitado. En el modo limitado, no podrá colocar hologramas en su entorno.

## <a name="environment-management"></a>Administración de entornos
Hay dos opciones de configuración que permiten a los usuarios "limpiar" los hologramas y hacer que HoloLens "olvide" un espacio.  Existen en "hologramas and Environments" en la aplicación de configuración, donde la segunda opción también aparece en "privacidad" en la aplicación de configuración.

1.  Eliminar hologramas cercanos: al seleccionar esta opción, HoloLens borrará todos los hologramas delimitados y todos los datos del mapa almacenados para el "espacio actual" en el que se encuentra el dispositivo.  Se creará una nueva sección de mapa y se almacenará en la base de datos para esa ubicación una vez que se vuelvan a colocar los hologramas en el mismo espacio.

2.  Eliminar todos los hologramas: al seleccionar esta opción, HoloLens borrará todos los datos de mapa y los hologramas delimitados en las bases de datos completas de espacios.  No se volverá a detectar ningún holograma y los hologramas deberán colocarse de nuevo para almacenar las secciones de mapa en la base de datos.

### <a name="managing-your-spaces"></a>Administrar los espacios

Las secciones de mapa y los distintos espacios se han contraído en una sola base de datos, almacenadas localmente en el dispositivo HoloLens. La base de datos de mapa se almacena de forma segura, con acceso solo disponible para el sistema interno y nunca a un usuario del dispositivo, incluso cuando está conectado a un equipo o a través de la aplicación del explorador de archivos. Cuando BitLocker está habilitado, los datos del mapa almacenado también se cifran.

Existen varios componentes de mapa cuando los hologramas se colocan en ubicaciones diferentes sin una ruta de acceso de conexión entre las ubicaciones y los hologramas.  Los hologramas delimitados dentro de la misma sección de mapa se consideran "cercanos" en el espacio actual.

Hay una API de desarrollador para exportar un pequeño subconjunto del "espacio actual" (una parte del componente de mapa reconocido actualmente) para habilitar escenarios de hologramas compartidos.  Actualmente no hay ningún mecanismo para descargar toda la base de datos de todos los espacios que se han asignado.


## <a name="hologram-quality"></a>Calidad de hologramas

Los hologramas se pueden colocar en todo el entorno (alta, baja y todo el suyo), pero los verá a través de un [marco holográfica](holographic-frame.md) que se encuentra delante de los ojos. Para obtener la mejor vista, asegúrese de ajustar el dispositivo para que pueda ver todo el marco. Y no dude en recorrer su entorno y explorarlo.

Para que los [hologramas](hologram.md) parezcan nítidos, claros y estables, HoloLens debe calibrarse solo para usted. La primera vez que configure su HoloLens, se le guiará a través de este proceso. Más adelante, si los hologramas no parecen correctos o está viendo muchos errores, puede realizar ajustes.

### <a name="calibration"></a>Curva

Si los hologramas parecen vibrar o desplazarse, o si tiene problemas para colocar hologramas, lo primero que debe probar es la [aplicación de calibración](calibration.md). Esta aplicación también puede ser de ayuda si tiene la molestia de usar HoloLens.

Para ir a la aplicación de calibración, vaya a Configuración > > Utilidades del sistema. Seleccione abrir calibración y siga las instrucciones.

Si ejecuta la aplicación de calibración y sigue teniendo problemas con la calidad de los hologramas, o si ve un mensaje de "pérdida de seguimiento" frecuente, pruebe la aplicación de optimización del sensor. Vaya a Configuración > > Utilidades del sistema, seleccione Abrir el ajuste del sensor y siga las instrucciones.

Si otra persona va a usar HoloLens, debe ejecutar la aplicación de calibración en primer lugar para que el dispositivo esté configurado correctamente.

## <a name="see-also"></a>Vea también
* [Diseño de asignaciones espaciales](spatial-mapping-design.md)
* [Hologramas](hologram.md)
* [Calibración](calibration.md)
