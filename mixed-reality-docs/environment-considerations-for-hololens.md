---
title: Consideraciones sobre el entorno de HoloLens
description: Obtener la mejor experiencia posible con HoloLens al optimizar el dispositivo para su entorno y los ojos.
author: thetuvix
ms.author: msamples
ms.date: 02/24/2019
ms.topic: article
keywords: marco holográfica, campo de visión, fov, calibración, espacios, entorno, procedimientos
ms.openlocfilehash: d5433dc923aeb70e3ae82e75c9358d3a569e8f83
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601297"
---
# <a name="environment-considerations-for-hololens"></a>Consideraciones sobre el entorno de HoloLens

HoloLens combina holográfica con el mundo "real", colocar hologramas en su entorno. Una ventana de aplicación holográfica "bloquea" en la pared, una ballerina holográfica gira sobre el sobremesa, oídos conejo posicionarse por encima de la cabeza de su amigo involuntario. Cuando se usa una aplicación o juego envolvente, el mundo holográfico distribuirán para rellenar respecto a su entorno, pero aún podrá ver y moverse por el espacio.

El hologramas que coloca permanecerá donde ha colocado en él, incluso si desactiva el dispositivo. 

Estos son algunos aspectos a tener en cuenta para una mejor experiencia con todo el mundo holográfica. Tenga en cuenta que HoloLens está diseñado para usarse en el interior en un espacio seguro con ningún paso peligros. No se utiliza al automóvil o realice otras actividades que requieren su atención completa.

## <a name="spaces"></a>Espacios

HoloLens, aprende sobre tu espacio para que pueda recordar donde haya colocado hologramas. HoloLens pueden recordar varios espacios y está diseñado para cargar el espacio correcto cuando lo encienda.

### <a name="setting-up"></a>Configurar

HoloLens se pueden asignar y recordar los espacios de mejor si elige el entorno adecuado.
* Utilice una sala con luz adecuada y una gran cantidad de espacio. Evite los espacios oscuros y salas con mucha superficies oscuras, brillantes o translúcidas (por ejemplo, reflejos o finos cortinas).
* Si desea HoloLens para obtener información sobre un espacio, Admítalo directamente, desde aproximadamente un medidor.
* Evite los espacios con una gran cantidad de movimiento de objetos. Si un elemento se ha movido y desea HoloLens para obtener información sobre la nueva posición (por ejemplo, se mueve la mesa de café a una nueva zona), que mirar y para desplazarse por él.

### <a name="spatial-mapping"></a>Asignación espacial

Cuando escriba un nuevo espacio (o cargar uno ya existente), verá un gráfico de malla propagándose por el espacio. Esto significa que el dispositivo está [respecto a su entorno de asignación](spatial-mapping-design.md). Si tiene problemas para colocar hologramas, intente deambulan el espacio para que HoloLens pueden asignar más completa. Si su HoloLens no pueden asignar el espacio o está fuera de calibración, puede especificar el modo Limited. En el modo Limited, no podrá colocar hologramas en su entorno.

### <a name="managing-your-spaces"></a>Administrar los espacios

Se han contraído las secciones de mapa y los diferentes espacios en una única base de datos almacenado localmente en el dispositivo HoloLens.  La base de datos de asignación se almacena de forma segura, con acceso solo está disponible para el sistema interno y nunca a un usuario del dispositivo, incluso cuando conectado a un equipo o mediante la aplicación de explorador de archivos.  Cuando bitlocker está habilitado, también se cifran los datos del mapa almacenado.
Varios componentes de asignación existen cuando hologramas se colocan en diferentes ubicaciones sin una ruta de acceso de conexión entre las ubicaciones/hologramas.  Hologramas anclados dentro de la misma sección del mapa son considera "cercanos" en el espacio actual existe es una API para exportar un pequeño subconjunto del espacio"actual" para desarrolladores (una parte del componente de mapa que se reconoce actualmente) para habilitar escenarios holograma compartido.  Actualmente no hay ningún mecanismo para descargar la base de datos completa de todos los espacios que se han asignado.

#### <a name="wifi"></a>Wi-Fi
Vs conectados. No – siempre y cuando se habilita la Wi-Fi, datos del mapa se correlacionan con una huella digital de Wi-Fi, incluso cuando no está conectado a un red Wi-Fi real o enrutador.  Esto es porque la MAC dirección y la señal de fuerza (es decir, huella digital de Wi-Fi) de un enrutador está disponible sin necesidad de conectarse a él.  Identificación de red (es decir, el SSID, dirección MAC) no se envía a Microsoft y WiFi todas las referencias se mantienen de forma locales en el HoloLens.

Vs habilitadas. Deshabilitado: HoloLens se detectan y recuerde que incluso cuando está deshabilitado de Wi-Fi, forma de almacenar los datos del sensor de forma segura cuando se colocan hologramas espacios.  Sin la información de Wi-Fi, el espacio y hologramas pueden ser ligeramente más lentos reconocer en un momento posterior, como el HoloLens necesita comparar análisis activa para todos los delimitadores de holograma y secciones de mapa almacenadas en el dispositivo con el fin de "relocalize" a la parte derecha de la asignación.

#### <a name="environment-management"></a>Administración del entorno
Hay 2 opciones que permiten a los usuarios para "limpiar" hologramas y causa HoloLens "olvidar un espacio".  Existen en "Hologramas y entornos" en la aplicación de configuración, con la segunda opción también aparecen en "Privacidad" en la aplicación de configuración.
1.  Eliminar cercanas hologramas: al seleccionar esta opción, borrarán HoloLens hologramas todo anclados y todos los datos del mapa almacenado para el "espacio actual" donde se encuentra el dispositivo.  Crea una nueva sección de asignación y almacenada en la base de datos para esa ubicación una vez hologramas nuevo se colocan en el mismo espacio.
2.  Eliminar hologramas todas: al seleccionar esta opción, borrarán todos los datos del mapa HoloLens y anclados hologramas en las bases de datos completas de espacios.  No hay hologramas se se detecten y cualquier hologramas deben ubicarse recién para volver a almacenar las secciones de mapa en la base de datos.


## <a name="hologram-quality"></a>Calidad holograma

Hologramas pueden colocarse a lo largo de su entorno: alta, baja y en todo, pero verá a través de un [marco holográfica](holographic-frame.md) que se coloca delante de sus ojos. Para obtener la vista más eficaz, asegúrese de ajustar el dispositivo para que pueda ver todo el marco. Y no dude en caminar alrededor de su entorno y explorar.

Para su [hologramas](hologram.md) para buscar estable, claras y nítidas, su HoloLens necesita calibrarse solo para usted. Cuando se configura por primera vez su HoloLens, se le guiará a través de este proceso. Más adelante si no se ven bien hologramas o si ve muchos errores, puede realizar ajustes.

### <a name="calibration"></a>Calibración

Si sus hologramas busque tiemble o inestable, o si tiene problemas para colocar hologramas, lo primero que se intente el [aplicación calibración](calibration.md). Esta aplicación también puede ayudar si tiene cualquier malestar mientras usa su HoloLens.

Para llegar a la aplicación de calibración, vaya a Configuración > sistema > Utilidades. Seleccione la calibración abierto y siga las instrucciones.

Si ejecutar la aplicación de calibración y sigue teniendo problemas con calidad holograma, o si ve un mensaje de "seguimiento pierde" frecuentes, pruebe la aplicación de optimización Sensor. Vaya a Configuración > sistema > Utilidades, seleccione la optimización Sensor abierto y siga las instrucciones.

Si otra persona va a usar su HoloLens, debe ejecutar la aplicación de calibración primero por lo que el dispositivo esté configurado correctamente para ellos.

## <a name="see-also"></a>Vea también
* [Diseño de la asignación espacial](spatial-mapping-design.md)
* [Hologramas](hologram.md)
* [Calibración](calibration.md)
