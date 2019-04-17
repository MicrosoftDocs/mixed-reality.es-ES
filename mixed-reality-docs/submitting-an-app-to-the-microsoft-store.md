---
title: Envío de una aplicación a la Microsoft Store
description: Este artículo ofrecen sugerencias sobre el envío de las aplicaciones de realidad mixta en la Microsoft Store, incluida la forma de paquete y probar la aplicación y sugerencias para conseguir la certificación y a mantener la detectabilidad de la aplicación en el Store.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: aplicación de uwp, enviar, envío, filtros, los metadatos, los requisitos del sistema, las palabras clave, wack, certificación, paquete, appx, comercialización
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600867"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Envío de una aplicación a la Microsoft Store

Ambos [HoloLens](hololens-hardware-details.md) y el equipo con Windows 10 potenciar su [auriculares envolventes](immersive-headset-hardware-details.md) ejecutar aplicaciones de la plataforma Universal de Windows. Si va a enviar una aplicación que admite HoloLens o PC (o ambos), deberá enviar la aplicación a la Microsoft Store a través de [centro de partners](https://partner.microsoft.com/dashboard).

Si no dispone de una cuenta de desarrollador de centro de partners, puede [Regístrese hoy](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Empaquetar una aplicación de realidad mixta

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparar los activos de imagen que se incluye en el appx

Hay varios activos de imagen requeridos la creación de herramientas de appx para compilar la aplicación en un paquete appx para enviar a la Store. Puede obtener más información acerca de [directrices para los recursos de icono y el icono](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) en MSDN.

| Activos necesarios | Escala recomendada | Formato de imagen | ¿Donde se muestra? | 
|----------|----------|----------|------------------|
| Logotipo cuadrado de 71 x 71 | Cualquiera |  PNG | N/D | 
| Logotipo cuadrado de 150 x 150 | 150 x 150 (escala al 100%) o 225 x 225 (150% escala) | PNG | PIN y todas las aplicaciones de inicio (si no se proporciona de 310 x 310), las sugerencias de búsqueda de Store, la página de listado de Store, Store examinar, búsqueda de Store | 
|  Ancho de 310 x 150 Logo |  Cualquiera  |  PNG  |  N/D | 
|  Logotipo de Store |  75 x 75 (150% escala)  |  PNG  |  Centro de partners, aplicación de informes, escribir una opinión, mi biblioteca | 
|  Pantalla de presentación |  450 930 (150% escala)  |  PNG  |  Iniciador de aplicaciones 2D (Pizarra) | 

También hay algunos recursos recomendados que HoloLens pueden aprovechar.

| Recursos recomendados | Escala recomendada | ¿Donde se muestra? | 
|----------|----------|----------|
|  Logotipo cuadrado de 310 x 310 |  310 x 310 (150% escala) |  Los PIN de inicio y todas las aplicaciones | 

### <a name="live-tile-requirements"></a>Requisitos del icono de Live

El menú Inicio en HoloLens usará la imagen de icono cuadrado incluye más grande.

Puede ver que algunas aplicaciones publicadas por Microsoft tienen un selector de 3D para su aplicación. Los desarrolladores pueden agregar un selector de 3D en su aplicación mediante [estas instrucciones](implementing-3d-app-launchers.md).

### <a name="specifying-target-and-minimum-version-of-windows"></a>Especifica la versión mínima de Windows y de destino

Si la aplicación de realidad mixta incluye características que son específicas de una determinada versión de Windows, es importante especificar el destino y las versiones mínimas de la plataforma que admitirá la aplicación Windows Universal.

**Esto es especialmente cierto para aplicaciones orientadas a [inmersivos Windows Mixed Reality](immersive-headset-hardware-details.md), que requiere al menos el Windows 10 Fall Creators Update (10.0; Compilación 16299) para funcionar correctamente.**

Se le pedirá para establecer la versión mínima de Windows y de destino cuando se crea un nuevo proyecto Universal de Windows en Visual Studio. También puede cambiar esta configuración para un proyecto existente en el menú "Proyecto", a continuación, "propiedades del < nombre de la aplicación >" en la parte inferior del menú desplegable.

![Establecer la duración mínima y tienen como destino versiones de plataforma en Visual Studio 2017](images/visual-studio-min-version-500px.png)<br>
Establecer la duración mínima y tienen como destino versiones de plataforma en Visual Studio

### <a name="specifying-target-device-families"></a>Especifica las familias de dispositivos de destino

Las aplicaciones de Windows Mixed Reality (tanto para [HoloLens](hololens-hardware-details.md) y [inmersivos](immersive-headset-hardware-details.md)) forman parte de la plataforma Universal de Windows, por lo que cualquier paquete de aplicación con un [lafamiliadedispositivosdedestino](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)de "Windows.Universal" es capaz de ejecutarse en HoloLens o equipos con Windows 10 con inmersivos. Dicho esto, si no especifica una familia de dispositivos de destino en el manifiesto de aplicación se puede abrir accidentalmente la aplicación para dispositivos Windows 10 no deseados. Siga los pasos siguientes para especificar la familia de dispositivos Windows 10 prevista y, a continuación, [vuelva a comprobar que se seleccionen las familias de dispositivos correcto al cargar el paquete de aplicación en el centro de partners para enviar a la Store.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Para establecer este campo en Visual Studio, haga clic con el botón derecho en Package.appxmanifest y seleccione "Ver código", a continuación, busque el campo de nombre TargetDeviceFamily. De forma predeterminada, podría parecerse a lo siguiente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Si la aplicación se crea para **HoloLens**, a continuación, puede asegurarse de que solo se instale en HoloLens especificando una familia de dispositivos de destino de "Windows.Holographic". 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Si la aplicación se crea para **inmersivos Windows Mixed Reality**, a continuación, puede asegurarse de que sólo está instalado en equipos con Windows 10 con el de Windows 10 Fall Creators Update (es necesario para Windows Mixed Reality) mediante la especificación de un destino familia de dispositivos de "Windows.Desktop" y MinVersion de "10.0.16299.0".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Por último, si la aplicación está diseñada para ejecutarse en ambos **HoloLens y Windows Mixed Reality inmersivos**, puede asegurarse de la aplicación sólo estará disponible para esas familias de dos dispositivos y garantizar al mismo tiempo cada una tiene como destino el valor correcto versión mínima de Windows mediante la inclusión de una línea para cada familia de dispositivos de destino con su respectivo MinVersion.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Puede aprender más sobre cómo destinar las familias de dispositivos, lea el [documentación TargetDeviceFamily UWP](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>Asociar aplicación con el Store

En el menú de proyecto en la solución de Visual Studio, elija "Store > asociar aplicación con el Store". Si lo hace, puede probar escenarios de adquisición y notificación en la aplicación. Al asociar la aplicación con el Store, estos valores se descargan en el archivo de manifiesto de aplicación para el proyecto actual en el equipo local:
* Nombre para mostrar del paquete
* Nombre del paquete
* Id. de publicador
* Nombre para mostrar del publicador
* Versión

Si invalida el archivo predeterminado.appxmanifest creando un archivo .xml personalizado para el manifiesto, no se puede asociar la aplicación con el Store. Si intenta asociar el Store en un archivo de manifiesto personalizado, verá un mensaje de error.

### <a name="creating-an-upload-package"></a>Creación de un paquete de carga

Siga las instrucciones en [Windows Universal de empaquetado de aplicaciones para Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

El último paso de creación de un paquete de carga está validando el paquete mediante el [Windows App Certification Kit](#windows-app-certification-kit).

Si va a agregar un paquete específicamente para HoloLens a un producto existente que está disponible en otras familias de dispositivos Windows 10, también deseará conocer [cómo los números de versión pueden afectar a los paquetes que se entregan a clientes específicos ](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx), y [cómo se distribuyen los paquetes a distintos sistemas operativos](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

La regla general es que el paquete de número de versión más alto que se aplica a un dispositivo será distribuido por el Store.

Si hay un paquete de Windows.Universal y un paquete Windows.Holographic y el paquete de Windows.Universal tiene un mayor número de versión, un usuario de HoloLens descargará el paquete de Windows.Universal número de versión superior en lugar de la Windows.Holographic paquete. Existen varias soluciones para este problema:
1. Asegúrese de los paquetes específicos de plataforma como Windows.Holographic siempre tienen un número de versión mayor que los paquetes independientes de plataforma como Windows.Universal
2. No empaquetar aplicaciones como Windows.Universal si también tiene paquetes específicos de plataforma - paquete en su lugar para las plataformas específicas que desea que esté disponible en el paquete de Windows.Universal

>[!NOTE]
> Puede declarar un único paquete que se aplique a varias familias de dispositivos de destino

3. Crear un paquete de Windows.Universal único que funciona en todas las plataformas. Ahora mismo soporte técnico para esto no es excelente para que las soluciones anteriores se recomiendan.

## <a name="testing-your-app"></a>Probar la aplicación

### <a name="windows-app-certification-kit"></a>Kit para la certificación de aplicaciones en Windows

Cuando se crean paquetes de aplicación para enviar al centro de partners a través de Visual Studio, el Asistente para crear paquetes de aplicaciones le solicitará que ejecutará los paquetes que se crean en el Kit de certificación de aplicaciones de Windows. Para tener un proceso de envío sin problemas a la Store, es mejor comprobar que la [Kit de certificación de aplicaciones de Windows comprueba](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) pasar en la aplicación en el equipo local antes de enviarlas a la Store. No se admite actualmente la ejecución el Kit de certificación de aplicaciones de Windows en un HoloLens remoto.

### <a name="run-on-all-targeted-device-families"></a>Ejecutar en todas las familias de dispositivos de destino

La plataforma Universal de Windows permite crear una única aplicación que se ejecuta en todas las familias de dispositivos Windows 10. Sin embargo, no garantiza que las aplicaciones de Windows Universal solo funcionará en todas las familias de dispositivos. Antes de elegir para su aplicación esté disponible en HoloLens o cualquier otra familia de dispositivos de destino de Windows 10, es importante que usted [probar la aplicación](testing-your-app-on-hololens.md) en cada una de las familias de dispositivos para garantizar una buena experiencia.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Enviar la aplicación de realidad mixta en el Store

Si va a enviar una aplicación de realidad mixta que se basa en un proyecto de Unity, consulte este [vídeo](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) primero.

En general, enviando un Windows Mixed Reality aplicación que funcione en HoloLens o inmersivos es igual que el envío de cualquier aplicación UWP a la Microsoft Store. Una vez que haya [creó su aplicación mediante su nombre de reserva](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), debe seguir el [lista de comprobación de envío de UWP](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

Una de las primeras cosas que haremos es [seleccione una categoría y subcategoría](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) para su experiencia de realidad mixta. Es importante que usted **elija la categoría más precisa para la aplicación** para que podamos comercialícela en la aplicación en las categorías de Store adecuadas y asegurarse de se muestra mediante consultas de búsqueda pertinentes. **Mostrar el título de la realidad virtual como un juego no darán como resultado una mejor exposición de la aplicación,** y puede impedir que aparezcan en las categorías que se ajuste más y menos saturado.

Sin embargo, hay cuatro áreas clave en el proceso de envío donde quiera realizar selecciones de específicos de realidad mixtas:
1. En el **[declaraciones de producto](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** sección [propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. En el **[requisitos del sistema](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** sección [propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. En el **[disponibilidad familia de dispositivos](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** sección [paquetes](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. En algunos de los **[página de listado de Store](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** campos.

### <a name="mixed-reality-product-declarations"></a>Declaraciones de producto de realidad mixta

En el **[propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** página de proceso de envío, encontrará varias opciones relacionadas con la realidad mixta en el **[declaraciones de producto](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** sección.

![Declaraciones de producto de realidad mixta](images/product-declarations-900px.png)<br>
Declaraciones de producto de realidad mixta

En primer lugar, conviene identificar los tipos de dispositivo para el que la aplicación ofrece una experiencia de realidad mixta. Esto garantiza que la aplicación se incluye en las colecciones de realidad mixta de Windows en el Store y que aparece para los usuarios que examinen el Store después de conectar un auricular envolvente (o al examinar el Store en HoloLens).

Junto a "esta experiencia se ha diseñado para Windows Mixed Reality en:"
* Compruebe el **PC** cuadro solo si la aplicación ofrece una experiencia de realidad virtual cuando se conecta un auricular envolvente para el equipo del usuario. Se debe activar esta casilla si la aplicación está diseñada exclusivamente para ejecutar en un auricular envolvente o si se trata de una PC juego o aplicación estándar que ofrece un contenido extra o modo de realidad mixta cuando está conectado auriculares.
* Compruebe el **HoloLens** cuadro solo si la aplicación ofrece una experiencia holográfica cuando se ejecuta en HoloLens.
* Comprobar **ambos** cuadros si la aplicación ofrece una realidad mixta de la experiencia en ambos tipos de dispositivo, como el [Academy de realidad mixta "Isla de proyecto" aplicación](mixed-reality-250.md) de Build 2017.

Si ha seleccionado "PC" anterior, conviene establecer la configuración de la realidad mixta"" (nivel de actividad). Esto solo se aplica a las experiencias de realidad mixta que se ejecutan en los equipos conectados a inmersivos, como aplicaciones de realidad mixta en HoloLens se escala mundial y el usuario no define un límite durante la instalación.
* Elija **su asiento + permanente** si la aplicación se ha diseñado con la intención de que el usuario sigue abierta en una posición (un ejemplo sería un juego donde está sentado en una cabina de un avión).
* Elija **todas las experiencias** si la aplicación está diseñada con la intención de que el usuario se describe en torno a dentro del límite que se define durante la instalación (un ejemplo podría ser un juego where lado paso y duck dodge ataques).

### <a name="mixed-reality-system-requirements"></a>Requisitos del sistema de realidad mixta

En el **[propiedades](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** página de proceso de envío, encontrará varias opciones relacionadas con la realidad mixta en el **[requisitos del sistema](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** sección.

![Requisitos del sistema](images/system-reqs-800px.png)<br>
Requisitos del sistema

En esta sección, podrá identificar mínimos de hardware (obligatorio) y recomendada hardware (opcional) para la aplicación de realidad mixta.

**Entrada de hardware:**

Use las casillas para indicar a los clientes potenciales si la aplicación admite **micrófono** (para [entrada de voz](voice-input.md)), **[Xbox controlador o gamepad](hardware-accessories.md#bluetooth-gamepads)**, o  **[los controladores de Windows Mixed Reality movimiento](motion-controllers.md)**. Esta información se producirá en la página de detalles del producto de la aplicación en el Store y le ayudará a la aplicación se incluyen en las colecciones de la aplicación o juego adecuado (por ejemplo, puede existir una colección de todos los juegos que admiten controladores de movimiento).

Estar bien meditada acerca de cómo seleccionar las casillas de verificación "mínimos de hardware" o "hardware recomendado" para tipos de entrada. 

Por ejemplo: 
* Si su juego requiere controladores de movimiento, pero acepta la entrada de voz a través de micrófono, active la casilla de verificación "mínimos de hardware" junto a "Controladores de Windows Mixed Reality movimiento", pero la casilla de verificación "hardware recomendado" junto a "Micrófono". 
* Si su juego se puede reproducir con cualquier una Xbox controlador/gamepad o movimiento controladores, es posible que la casilla "mínimos de hardware" junto a "mando de Xbox o gamepad" y Active la casilla "hardware recomendado" junto a "movimiento Windows Mixed Reality controladores"como controladores de movimiento es probable que proporcionará una edición superior en la experiencia desde el controlador para juegos.

**Auriculares envolventes de Windows Mixed Reality:**

Que indica si un auricular envolvente se requiere para usar la aplicación, o es opcional, es fundamental para la educación y satisfacción del cliente.

Si la aplicación puede *sólo* usarse a través de un auricular envolvente, active la casilla "mínimos de hardware" junto a "Auriculares envolventes de Windows Mixed Reality." Esto se expone en la página de detalles del producto de la aplicación en Store como una advertencia sobre el botón de compra por lo que los clientes no se piensan que están comprando una aplicación que funcionará en su PC como una aplicación de escritorio tradicionales.

Si la aplicación se ejecuta en el escritorio, como una aplicación tradicional de PC, pero ofrece una experiencia de realidad virtual cuando se conecta un auricular envolvente (si el contenido completo de la aplicación está disponible, o sólo una parte), active la casilla "hardware recomendado" junto a "Windows Mixed Reality auriculares envolventes." Ninguna advertencia aparecerán encima del botón de compra en la página de detalles del producto de la aplicación si las funciones de aplicación como una aplicación de escritorio tradicional sin un auricular envolvente conectado.

**Especificaciones de PC:**

Si desea que la aplicación para llegar a tantos usuarios envolventes auriculares de realidad mixta de Windows como sea posible, deseará [destino](understanding-performance-for-mixed-reality.md) las especificaciones de PC de [equipos con Windows Mixed Reality con gráficos integrados](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Si la aplicación de realidad mixta tiene como destino los requisitos mínimos de PC con Windows Mixed Reality, o requiere una configuración específica del equipo (al igual que la GPU dedicada de un [PC con Windows Mixed Reality Ultra](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), debe indicar que con la correspondiente Especificaciones de PC en la columna "mínimos de hardware".

Si la aplicación de realidad mixta está diseñada para un mejor rendimiento, o para ofrecer mayor resolución gráficos, en una determinada configuración de PC o una tarjeta gráfica, debe indicar las especificaciones relevantes de PC en la columna "hardware recomendado".

Esto solo se aplica si su aplicación de realidad mixta usa un auricular envolvente conectado a un equipo. Si la aplicación de realidad mixta solo se ejecuta en HoloLens, no tendrá que indicar las especificaciones de PC como HoloLens tiene solo una configuración de hardware.

### <a name="device-family-availability"></a>Disponibilidad de familias de dispositivos

Si ha [empaqueta la aplicación correctamente](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) en Visual Studio, cargarlo en la página de los paquetes del proceso de envío debe generar una tabla que identifica qué familias de dispositivos que estará disponible para su aplicación.

![Tabla de disponibilidad de la familia de dispositivos](images/device-family-table-900px.png)<br>
Tabla de disponibilidad de la familia de dispositivos

Si la aplicación de realidad mixta funciona en inmersivos y luego en menos "Windows 10 Desktop" debería estar seleccionado en la tabla. Si la aplicación de realidad mixta funciona en HoloLens y luego en menos "Windows 10 Holographic" se debe seleccionar. Si la aplicación se ejecuta en ambos tipos de auriculares de realidad mixta de Windows, como el [Academy de realidad mixta "Isla de proyecto" aplicación](mixed-reality-250.md), "Windows 10 escritorio" y "Windows 10 Holographic" se deben seleccionar.

>[!TIP]
>Muchos desarrolladores experimenta errores al cargar el paquete de la aplicación relacionados con discrepancias entre el manifiesto del paquete y la información de su cuenta de publicador de la aplicación o en el centro de partners. A menudo se pueden evitar estos errores, inicie sesión en Visual Studio con la misma cuenta asociada con su cuenta de desarrollador de Windows (lo que se usa para iniciar sesión en el centro de partners). Si usa la misma cuenta, podrá asociar la aplicación con su identidad en la Microsoft Store antes de empaquetarla.

![Asociar la aplicación a la Microsoft Store](images/associate-your-app-700px.png)<br>
Asociar la aplicación a la Microsoft Store en Visual Studio

### <a name="store-listing-page"></a>Página de listado de Store

En el [lista Store](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) procesar la página de la presentación de la aplicación, hay varios lugares, puede agregar información útil sobre la aplicación de realidad mixta.

>[!IMPORTANT]
>Para asegurarse de la aplicación está correctamente clasificada por el Store y reconocible para los clientes de Windows Mixed Reality, debe agregar **"Windows Mixed Reality"** como uno de los "términos de búsqueda" para la aplicación (puede encontrar los términos de búsqueda expandiendo la "Compartida campos" sección).

![Agregar Windows Mixed Reality para los términos de búsqueda](images/search-terms-800px.png)<br>
Agregar "Windows Mixed Reality" términos de búsqueda

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Ofrece una evaluación gratuita para su juego o aplicación

Muchos consumidores habrá limitado o ninguna experiencia con la realidad virtual antes de comprar un auricular envolvente de Windows Mixed Reality. Que es posible que no sepan qué pueden esperar de juegos y quizás no estén familiarizados con su propio umbral comodidad en experiencias envolventes. Muchos clientes también pueden intentar un auricular envolvente de Windows Mixed Reality en los equipos que no están identificados como parte de como [equipos con Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Por estos motivos, se recomienda encarecidamente que considere la posibilidad de oferta un [gratuita](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) para su aplicación de realidad mixta pago o el juego.

## <a name="see-also"></a>Vea también
* [Realidad mixta](mixed-reality.md)
* [Información general sobre desarrollo](development-overview.md)
* [Vistas de aplicación](app-views.md)
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Probar una aplicación en HoloLens](testing-your-app-on-hololens.md)
* [Directrices para compatibilidad de hardware mínimas PC de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
