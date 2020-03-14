---
title: Enviar una aplicación a la Microsoft Store
description: En este artículo se ofrecen sugerencias sobre el envío de aplicaciones de realidad mixta al Microsoft Store, incluido cómo empaquetar y probar la aplicación y sugerencias para pasar la certificación y ayudar a detectar la aplicación en la tienda.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: aplicación, UWP, envío, envío, filtros, metadatos, requisitos del sistema, palabras clave, Wack, certificación, paquete, appx, comercialización
ms.openlocfilehash: f2eb4093a2bea51d8c39b94d23777e426810981e
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375812"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Enviar una aplicación a la Microsoft Store

Tanto [HoloLens](hololens-hardware-details.md) como el equipo con Windows 10 que encienden el [casco envolvente](immersive-headset-hardware-details.md) se ejecutan plataforma universal de Windows aplicaciones. Tanto si va a enviar una aplicación que admite HoloLens como equipo (o ambos), enviará la aplicación al Microsoft Store a través del [centro de Partners](https://partner.microsoft.com/dashboard).

Si aún no tiene una cuenta de desarrollador de centro de Partners, puede [registrarse hoy mismo](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Empaquetado de una aplicación de realidad mixta

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparar los recursos de imagen incluidos en el appx

Las herramientas de compilación de appx requieren varios recursos de imagen para compilar la aplicación en un paquete appx para enviarla a la tienda. Puede obtener más información acerca [de las directrices para los recursos de iconos e iconos](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) en MSDN.

| Recurso necesario | Escala recomendada | Formato de imágenes | ¿Dónde se muestra? | 
|----------|----------|----------|------------------|
| Logotipo cuadrado de 71 x 71 | Cualquiera |  PNG | N/D | 
| Logotipo cuadrado de 150 x 150 | 150 x 150 (escala del 100%) o 225x225 (150% de escala) | PNG | PIN de inicio y todas las aplicaciones (si no se proporciona 310 x 310), sugerencias de búsqueda en el almacén, página de lista de tiendas, exploración de tiendas, búsqueda de la tienda | 
|  Logotipo de ancho de 310 |  Cualquiera  |  PNG  |  N/D | 
|  Logotipo de la Tienda |  75x75 (escala del 150%)  |  PNG  |  Centro de Partners, aplicación de informes, escribir una revisión, mi biblioteca | 
|  Pantalla de presentación |  930x450 (escala del 150%)  |  PNG  |  iniciador de aplicaciones 2D (pizarra) | 

También hay algunos activos recomendados que HoloLens puede aprovechar.

| Activos recomendados | Escala recomendada | ¿Dónde se muestra? | 
|----------|----------|----------|
|  Logotipo cuadrado de 310 x 310 |  310 x 310 (escala del 150%) |  PIN de inicio y todas las aplicaciones | 

### <a name="live-tile-requirements"></a>Requisitos de iconos dinámicos

El menú Inicio de HoloLens usará la imagen de icono cuadrado más grande incluida.

Puede ver que algunas aplicaciones publicadas por Microsoft tienen un selector 3D para su aplicación. Los desarrolladores pueden agregar un selector 3D para su aplicación mediante [estas instrucciones](implementing-3d-app-launchers.md).

### <a name="specifying-target-and-minimum-version-of-windows"></a>Especificar el destino y la versión mínima de Windows

Si la aplicación de realidad mixta incluye características que son específicas de una determinada versión de Windows, es importante especificar las versiones de plataforma de destino y mínima que admitirá la aplicación universal de Windows.

**Esto es especialmente cierto en el caso de las aplicaciones destinadas a los auriculares con una [realidad mixta de Windows](immersive-headset-hardware-details.md), que requieren al menos Windows 10 Fall Creators Update (10,0; Compilación 16299) para que funcione correctamente.**

Cuando cree un nuevo proyecto universal de Windows en Visual Studio, se le pedirá que establezca el destino y la versión mínima de Windows. También puede cambiar esta configuración para un proyecto existente en el menú "proyecto" y, a continuación, "< las propiedades > del nombre de la aplicación" en la parte inferior del menú desplegable.

![establecer las versiones de plataforma mínima y de destino en Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
Establecimiento de versiones de plataforma mínima y de destino en Visual Studio

### <a name="specifying-target-device-families"></a>Especificación de las familias de dispositivos de destino

Las aplicaciones de realidad mixta de Windows (tanto para [HoloLens](hololens-hardware-details.md) como para [auriculares envolvente](immersive-headset-hardware-details.md)) forman parte de la plataforma universal de Windows, por lo que cualquier paquete de aplicación con una [familia de dispositivos de destino](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) de "Windows. universal" es capaz de ejecutarse en equipos HoloLens o Windows 10 con auriculares envolventes. Dicho esto, si no especifica una familia de dispositivos de destino en el manifiesto de la aplicación, puede abrir la aplicación involuntariamente en dispositivos Windows 10 imprevistos. Siga los pasos que se indican a continuación para especificar la familia de dispositivos Windows 10 deseada y, a continuación, [Compruebe que se han seleccionado las familias de dispositivos correctas al cargar el paquete de aplicación en el centro de partners para enviarlo a la tienda.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Para establecer este campo en Visual Studio, haga clic con el botón derecho en package. appxmanifest y seleccione "ver código" y, a continuación, busque el campo Nombre de TargetDeviceFamily. De forma predeterminada, podría ser similar al siguiente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Si la aplicación se crea para **hololens**, puede asegurarse de que solo se instala en hololens especificando una familia de dispositivos de destino de "Windows. Holographic". 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Si su aplicación requiere la funcionalidad de **HoloLens 2** específicamente, como seguimiento de ojo o seguimiento de mano, puede asegurarse de que está destinada a las versiones de Windows 18362 o superior especificando una familia de dispositivos de destino de "Windows. Holographic" y MinVersion 10.0.18362.0. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

Si la aplicación se crea para **auriculares con Windows Mixed Reality**, puede asegurarse de que solo está instalado en equipos con Windows 10 con Windows 10 Fall Creators Update (necesario para Windows Mixed Reality) mediante la especificación de una familia de dispositivos de destino de "Windows. Desktop" y MinVersion de "10.0.16299.0".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Por último, si la aplicación está pensada para ejecutarse en **HoloLens y en auriculares mixto de Windows Mixed Reality**, puede asegurarse de que la aplicación solo esté disponible para esas dos familias de dispositivos y asegurarse de que cada uno tiene la versión mínima de Windows correcta incluyendo una línea para cada familia de dispositivos de destino con su MinVersion correspondiente.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Puede obtener más información sobre cómo establecer el destino de las familias de dispositivos leyendo la [documentación de TARGETDEVICEFAMILY UWP](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Asociar aplicación con la tienda

En el menú proyecto de la solución de Visual Studio, elija "almacenar > asociar la aplicación con la tienda". Si lo hace, puede probar escenarios de compra y de notificación en la aplicación. Al asociar la aplicación a la tienda, estos valores se descargan en el archivo de manifiesto de la aplicación para el proyecto actual en el equipo local:
* Nombre para mostrar del paquete
* Nombre del paquete
* Id. de publicador
* Nombre para mostrar del publicador
* Versión

Si invalida el archivo predeterminado .appxmanifest creando un archivo .xml personalizado para el manifiesto, no podrá asociar la aplicación a la Tienda. Si intenta asociar un archivo de manifiesto personalizado a la Tienda, recibirá un mensaje de error.

### <a name="creating-an-upload-package"></a>Crear un paquete de carga

Siga las instrucciones que se indican en [empaquetar aplicaciones universales de Windows para Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

El paso final de la creación de un paquete de carga es la validación del paquete con el [Kit de certificación de aplicaciones de Windows](#windows-app-certification-kit).

Si va a agregar un paquete específicamente para HoloLens a un producto existente que está disponible en otras familias de dispositivos de Windows 10, también querrá saber [cómo los números de versión pueden afectar a los paquetes que se entregan a clientes específicos](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx)y [cómo se distribuyen los paquetes a diferentes sistemas operativos](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

La guía general es que el paquete de número de versión más alto que se aplica a un dispositivo será el distribuido por el almacén.

Si hay un paquete de Windows. universal y un paquete de Windows. Holographic y el paquete de Windows. universal tiene un número de versión superior, un usuario de HoloLens descargará el paquete Windows. universal con el número de versión más alto en lugar de Windows. Holographic configura. Existen varias soluciones para este problema:
1. Asegúrese de que los paquetes específicos de la plataforma como Windows. Holographic siempre tienen un número de versión mayor que los paquetes independientes de la plataforma, como Windows. universal.
2. No empaquete aplicaciones como Windows. universal si también tiene paquetes específicos de la plataforma. en su lugar, empaquete el paquete Windows. universal para las plataformas específicas en las que desea que esté disponible.

>[!NOTE]
> Para admitir la aplicación en HoloLens (1º gen) y HoloLen 2, deberá cargar dos paquetes de aplicaciones. uno que contiene x86 para HoloLens (1º gen) y otro que contiene ARM o ARM64 para HoloLens 2. 
> 
> Si incluye ARM y ARM64 en el paquete, se usará la versión de ARM64 en HoloLens 2. 

>[!NOTE]
> Puede declarar un único paquete para que sea aplicable a varias familias de dispositivos de destino.

3. Cree un único paquete Windows. universal que funcione en todas las plataformas. La compatibilidad con esto no es excelente ahora, por lo que se recomiendan las soluciones anteriores.

## <a name="testing-your-app"></a>Prueba de una aplicación

### <a name="windows-app-certification-kit"></a>Kit para la certificación de aplicaciones en Windows

Al crear paquetes de aplicaciones para enviarlos al centro de partners a través de Visual Studio, el Asistente para crear paquetes de aplicaciones le pedirá que ejecute el kit de certificación de aplicaciones de Windows con los paquetes que se crean. Para poder realizar un proceso de envío sin problemas a la tienda, es mejor comprobar que las [pruebas del kit de certificación de aplicaciones de Windows](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) se superen en la aplicación en el equipo local antes de enviarlas al almacén. Actualmente no se admite la ejecución del kit de certificación de aplicaciones de Windows en un HoloLens remoto.

### <a name="run-on-all-targeted-device-families"></a>Ejecutar en todas las familias de dispositivos de destino

La plataforma universal de Windows permite crear una única aplicación que se ejecuta en todas las familias de dispositivos de Windows 10. Sin embargo, no garantiza que las aplicaciones universales de Windows funcionen en todas las familias de dispositivos. Antes de decidir que la aplicación esté disponible en HoloLens o en cualquier otra familia de dispositivos de destino de Windows 10, es importante que [pruebe la aplicación](testing-your-app-on-hololens.md) en cada una de esas familias de dispositivos para garantizar una buena experiencia.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Envío de la aplicación de realidad mixta a la tienda

Si va a enviar una aplicación de realidad mixta que se basa en un proyecto de Unity, consulte primero este [vídeo](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) .

En general, el envío de una aplicación de Windows Mixed Reality que funcione en HoloLens y/o auriculares envolvente es igual que enviar cualquier aplicación de UWP al Microsoft Store. Una vez que haya [creado la aplicación reservando su nombre](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), debe seguir la [lista de comprobación de envío de UWP](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

Una de las primeras cosas que debe hacer es [seleccionar una categoría y una subcategoría](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) para la experiencia de realidad mixta. Es importante que **Elija la categoría más precisa de la aplicación** para que podamos aplicar la mercancía a la aplicación en las categorías de tienda adecuadas y asegurarse de que se muestra mediante consultas de búsqueda pertinentes. **Mostrar el título de VR como un juego no dará como resultado una mejor exposición a la aplicación** y puede impedir que se muestre en categorías con más montaje y menos abarrotado.

Sin embargo, hay cuatro áreas clave en el proceso de envío en las que querrá hacer selecciones específicas de realidad mixta:
1. En la sección **[declaraciones de producto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** , en [propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. En la sección **[requisitos del sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** , en [propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. En la sección disponibilidad de la **[familia de dispositivos](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** , en [paquetes](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. En algunos de los campos de la **[Página de lista de tiendas](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Declaraciones de productos de realidad mixta

En la página **[propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** del proceso de envío de la aplicación, encontrará varias opciones relacionadas con la realidad mixta en la sección **[declaraciones del producto](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** .

![declaraciones de productos de realidad mixta](images/product-declarations-900px.png)<br>
Declaraciones de productos de realidad mixta

En primer lugar, querrá identificar los tipos de dispositivo para los que la aplicación ofrece una experiencia de realidad mixta. Esto garantiza que la aplicación se incluya en las colecciones de Windows Mixed Reality en el almacén y que se muestre a los usuarios que exploren la tienda después de conectarse a un casco envolvente (o al examinar la tienda en HoloLens).

Junto a "esta experiencia está diseñada para Windows Mixed Reality en:"
* Active la casilla **PC** solo si la aplicación ofrece una experiencia de VR cuando se conecta un auricular envolvente al equipo del usuario. Debes activar esta casilla si tu aplicación está diseñada exclusivamente para ejecutarse en un casco inmersivo o si se trata de un juego o aplicación estándar que ofrece un modo de realidad mixta y/o contenido adicional cuando se conecta un auricular.
* Active la casilla **HoloLens** solo si la aplicación ofrece una experiencia holográfica cuando se ejecuta en HoloLens.
* Active **ambas** casillas si la aplicación ofrece una experiencia de realidad mixta en ambos tipos de dispositivo, como la [aplicación "isla de proyecto" de la realidad mixta](mixed-reality-250.md) de la compilación 2017.

Si seleccionó "PC" arriba, querrá establecer la "configuración de realidad mixta" (nivel de actividad). Esto solo se aplica a las experiencias de realidad mixta que se ejecutan en equipos conectados a auriculares envolventes, ya que las aplicaciones de realidad mixta en HoloLens son de escala mundial y el usuario no define ningún límite durante la instalación.
* Elija **sentado +** en espera si la aplicación está diseñada con la intención de que el usuario permanezca en una posición (un ejemplo sería un juego en el que está sentado en una cabina de un avión).
* Elija **todas las experiencias** si su aplicación está diseñada con la intención de que el usuario se desplazará dentro del límite que ha definido durante la instalación (un ejemplo podría ser un juego en el que se encuentra el paso lateral y el pato para aclarar los ataques).

### <a name="mixed-reality-system-requirements"></a>Requisitos del sistema de realidad mixta

En la página **[propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** del proceso de envío de la aplicación, encontrará varias opciones relacionadas con la realidad mixta en la sección **[requisitos del sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** .

![Requisitos del sistema](images/system-reqs-800px.png)<br>
Requisitos del sistema

En esta sección, identificará el hardware mínimo (necesario) y el hardware recomendado (opcional) para la aplicación de realidad mixta.

**Hardware de entrada:**

Use las casillas para indicar a los clientes potenciales si la aplicación admite **micrófono** (para la [entrada de voz](voice-input.md)), **[controlador de Xbox o](hardware-accessories.md#bluetooth-gamepads)** controlador para juegos, o **[controladores de movimiento de Windows Mixed Reality](motion-controllers.md)** . Esta información se mostrará en la página de detalles del producto de la aplicación en la tienda y ayudará a la aplicación a incluirse en las colecciones de aplicaciones y juegos correspondientes (por ejemplo, puede existir una colección para todos los juegos que admiten controladores de movimiento).

Tenga cuidado al seleccionar casillas de verificación para "hardware mínimo" o "Hardware recomendado" para los tipos de entrada. 

Por ejemplo: 
* Si el juego requiere controladores de movimiento, pero acepta la entrada de voz a través del micrófono, active la casilla "hardware mínimo" junto a "controladores de movimiento de Windows Mixed Reality", pero la casilla "Hardware recomendado" junto a "micrófono". 
* Si el juego puede reproducirse con un controlador de Xbox o un controlador de vídeo o controladores de movimiento, puede activar la casilla "hardware mínimo" junto a "controlador de Xbox o controlador de juegos" y activar la casilla "Hardware recomendado" junto a "controladores de movimiento de realidad mixta de Windows", ya que los controladores de movimiento probablemente ofrecerán un paso en la experiencia del controlador de juegos

**Auriculares envolventes de Windows Mixed Reality:**

Que indica si se requiere un casco envolvente para usar la aplicación, o si es opcional, es fundamental para la satisfacción del cliente y la educación.

Si la aplicación *solo* se puede usar a través de un auricular envolvente, active la casilla "hardware mínimo" junto a "auriculares con pausa de Windows Mixed Reality". Esto se mostrará en la página de detalles del producto de la aplicación en la tienda como una advertencia sobre el botón comprar para que los clientes no creen que compren una aplicación que funcionará en su equipo como una aplicación de escritorio tradicional.

Si la aplicación se ejecuta en el escritorio como una aplicación de equipo tradicional, pero ofrece una experiencia de VR cuando se conecta un auricular envolvente (tanto si el contenido completo de la aplicación está disponible como si solo una parte), active la casilla "Hardware recomendado" junto a "Windows Mixed Reality. auriculares envolventes ". No se mostrará ninguna advertencia sobre el botón comprar en la página de detalles del producto de la aplicación si la aplicación funciona como una aplicación de escritorio tradicional sin un casco envolvente conectado.

**Especificaciones de PC:**

Si desea que la aplicación llegue a la mayoría de los auriculares de la realidad mixta de Windows, es posible que quiera [dirigirse](understanding-performance-for-mixed-reality.md) a las especificaciones de PC para [equipos de realidad mixta de Windows con gráficos integrados](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Tanto si la aplicación de realidad mixta tiene como destino los requisitos mínimos de equipo de Windows Mixed Reality, o requiere una configuración de equipo específica (como la GPU dedicada de un [ultra PC con Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)), debe indicar que con las especificaciones de PC correspondientes en la columna de "hardware mínimo".

Si la aplicación de realidad mixta se ha diseñado para que funcione mejor, o si ofrece gráficos de mayor resolución, en una tarjeta de gráficos o una configuración de PC concreta, debe indicar que con las especificaciones de PC correspondientes en la columna "Hardware recomendado".

Esto solo se aplica si la aplicación de realidad mixta usa un casco envolvente conectado a un equipo. Si la aplicación de realidad mixta solo se ejecuta en HoloLens, no tendrá que indicar las especificaciones de equipo, ya que HoloLens solo tiene una configuración de hardware.

### <a name="device-family-availability"></a>Disponibilidad de familias de dispositivos

Si ha [empaquetado la aplicación correctamente](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) en Visual Studio, la carga en la página paquetes del proceso de envío de la aplicación debe generar una tabla que identifique en qué familias de dispositivos estará disponible su aplicación.

![tabla de disponibilidad de la familia de dispositivos](images/device-family-table-900px.png)<br>
Tabla de disponibilidad de la familia de dispositivos

Si la aplicación de realidad mixta funciona en auriculares envolventes, se debe seleccionar al menos "Windows 10 Desktop" en la tabla. Si la aplicación de realidad mixta funciona en HoloLens, se debe seleccionar al menos "Windows 10 Holographic". Si la aplicación se ejecuta en los dos tipos de auriculares de la realidad mixta de Windows, como la [aplicación "isla de proyecto](mixed-reality-250.md)" de la realidad mixta, debe seleccionarse "Windows 10 Desktop" y "Windows 10 Holographic".

>[!TIP]
>Muchos desarrolladores experimentan errores al cargar el paquete de la aplicación relacionado con las discrepancias entre el manifiesto del paquete y la información de la cuenta de aplicación/publicador en el centro de Partners. Estos errores suelen evitarse iniciando sesión en Visual Studio con la misma cuenta asociada con su cuenta de desarrollador de Windows (la que se usa para iniciar sesión en el centro de Partners). Si usa la misma cuenta, podrá asociar la aplicación con su identidad en el Microsoft Store antes de empaquetarla.

![asociar la aplicación a la Microsoft Store](images/associate-your-app-700px.png)<br>
Asociar la aplicación a la Microsoft Store en Visual Studio

### <a name="store-listing-page"></a>Página de lista de tiendas

En la página Descripción de la [tienda](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) del proceso de envío de la aplicación, hay varios lugares en los que puede agregar información útil acerca de la aplicación de realidad mixta.

>[!IMPORTANT]
>Para asegurarse de que la aplicación esté clasificada correctamente por el almacén y que sea reconocible para los clientes de la realidad mixta de Windows, debe agregar **"Windows Mixed Reality"** como uno de los "términos de búsqueda" de la aplicación (puede buscar términos de búsqueda expandiendo la sección "campos compartidos").

![agregar Windows Mixed Reality a los términos de búsqueda](images/search-terms-800px.png)<br>
Agregar "Windows Mixed Reality" a los términos de búsqueda

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Ofrecer una evaluación gratuita para su juego o aplicación

Muchos consumidores se habrán limitado a no tener experiencia con la realidad virtual antes de comprar un casco de realidad más envolvente de Windows Mixed Reality. Es posible que no sepan qué esperan de juegos intensivos y que no estén familiarizados con su propio umbral de confort en experiencias envolventes. Muchos clientes también pueden probar con un casco con Windows Mixed Reality en equipos que no están identificados como [equipos con Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Debido a estas consideraciones, le recomendamos encarecidamente que considere la posibilidad de ofrecer una [evaluación gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) para su aplicación o juego de realidad mixta.

## <a name="see-also"></a>Vea también
* [Realidad mixta](mixed-reality.md)
* [Introducción al desarrollo](development.md)
* [Vistas de aplicación](app-views.md)
* [Descripción del rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Prueba de una aplicación en HoloLens](testing-your-app-on-hololens.md)
* [Instrucciones de compatibilidad de hardware de equipo mínima de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
