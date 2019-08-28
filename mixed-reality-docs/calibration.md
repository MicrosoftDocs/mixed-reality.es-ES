---
title: Curva
description: La calibración de IPD (Interpupillary Distance) puede mejorar la calidad de los objetos visuales. Tanto HoloLens como Windows Mixed Reality con micrófonos que se incluyen en la realidad ofrecen maneras de personalizar IPD.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: calibración, confort, objetos visuales, calidad, IPD
ms.openlocfilehash: 1fc3904f4b3e441a967616f20e4287dbc7f08835
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047051"
---
# <a name="improve-visual-quality-and-comfort"></a>Mejore la calidad visual y la comodidad
Los auriculares de alta calidad de HoloLens, HoloLens y Windows Mixed Reality ofrecen diferentes maneras de mejorar la calidad de la experiencia visual. 

## <a name="hololens-2"></a>Hololens 2

### <a name="calibration"></a>Curva

Hololens 2 está diseñado para proporcionar el mayor nivel de imagen y comodidad para nuestros clientes. La tecnología de seguimiento ocular se usa para mejorar la experiencia del usuario de ver e interactuar con el entorno virtual.  
En HoloLens 2, se le pedirá que calibre los objetos visuales durante la configuración del dispositivo. Se pide a los usuarios que examinen el conjunto de destinos de fijación. Esto permite que el dispositivo ajuste la representación de hologramas para el usuario con el fin de garantizar un holograma colocado con precisión, una experiencia de visualización 3D y una calidad de presentación mejorada. Todos los ajustes se producen sobre la marcha sin necesidad de una optimización manual. Mediante el uso de los ojos como puntos de referencia, el dispositivo se ajusta para cada usuario y los objetos visuales se ajustan cuando el casco se desplaza ligeramente en el uso. El sistema utiliza internamente el seguimiento de la posición del ojo y los desarrolladores no tienen que hacer nada para aprovechar esta funcionalidad. Esta información no está disponible para los desarrolladores. En Hololens 2, realizar una calibración también garantiza un seguimiento preciso de la mirada para cada usuario. El seguimiento de los ojos permite a las aplicaciones realizar un seguimiento de dónde mira el usuario en tiempo real. Esta es la principal capacidad que los desarrolladores pueden aprovechar para habilitar un nuevo nivel completo de contexto, comprensión humana e interacciones dentro de la experiencia holográfica.  
La calibración se almacena localmente en el dispositivo y no está asociada a ninguna información de la cuenta. No hay ningún registro de quién ha usado el dispositivo sin calibración. Esto significa que se les pedirá a los nuevos usuarios que calibren los objetos visuales cuando usen el dispositivo por primera vez, así como los usuarios que hayan optado por la calibración previamente o si la calibración no se ha realizado correctamente. La calibración siempre se puede eliminar del dispositivo en **configuración** > de la**vista**de**privacidad** > . 

### <a name="calibration-failures"></a>Errores de calibración

La calibración debe funcionar para la mayoría de los usuarios, pero hay casos en los que es posible que el usuario no pueda calibrarse correctamente.  
Algunos ejemplos de errores de calibración se deben a:
- El usuario se distrae y no sigue los objetivos de calibración durante la experiencia de calibración
- El visor del dispositivo sucio o desarañado o el visor del dispositivo no se colocaron correctamente 
- Vasos sucios o con arañazos
- Determinados tipos de lentes y anteojos de contacto (lentes de contacto en color, algunos lentes de contacto de toric, gafas de bloqueo de INFRARROJOs, algunos vasos de receta elevados, cristal de la luna, etc.)
- Composición más pronunciada, algunas extensiones de eyelash
- Oclusións de ojo y/o visor del dispositivo (pelo, algunos fotogramas de gafas gruesos)
- Physiology ocular, ciertas condiciones oculares o cirugía ocular (algunos ojos estrechos, eyelashes largos, amblyopia, nystagmus, algunos casos de LASIK u otros surgeries ocular, etc.)

Si la calibración no se realiza correctamente, pruebe una de estas correcciones: 
- Limpiar el visor del dispositivo
- Limpie sus gafas
- Inserte el visor del dispositivo en todo el proceso.
- Asegúrese de que no haya ninguna obstrucción de los sensores o de los ojos (por ejemplo, pelo) 
- Asegúrese de que hay suficiente luz en su habitación y que no está bajo la luz solar directa
- Asegúrese de seguir cuidadosamente los destinos durante la calibración

Si ha seguido las instrucciones y se sigue produciendo un error en la calibración, puede deshabilitar la petición de calibración en **configuración** > **calibración** **del sistema** > . ' Cuando una persona nueva usa este Hololens, preguntar automáticamente para ejecutar la calibración de ojo ' debe estar optimizada. Tenga en cuentan que esto podría dar lugar a una calidad de representación de hologramas peor y a la molestia.

### <a name="launching-the-calibration-app-from-settings"></a>Inicio de la aplicación de calibración desde la configuración
1. Use el gesto de inicio para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione **todas las aplicaciones** para ver todas las aplicaciones si la **configuración** no está anclada para iniciarse.
3. **Configuración**de inicio.
4. Desplácese > a calibración**ocular** **del sistema** > y seleccione **Ejecutar calibración de ojo**.

### <a name="calibration-when-sharing-a-devicesession"></a>Calibración al compartir un dispositivo/sesión

Hololens 2 puede compartirse entre personas, sin necesidad de que cada persona pase a través de la configuración del dispositivo. Hololens 2 le pedirá al usuario que calibre los objetos visuales cuando el dispositivo se coloque en el cabezal si el usuario es nuevo en el dispositivo. Si el usuario ha calibrado previamente objetos visuales en el dispositivo, la pantalla se ajustará sin problemas para la calidad y una experiencia de visualización cómoda cuando el usuario coloque el dispositivo en el cabezal. 


## <a name="hololens-v1"></a>Hololens (V1)

La calibración de IPD (Interpupillary Distance) puede mejorar la calidad de los objetos visuales.

### <a name="during-setup"></a>Durante la instalación

![Pantalla de alineación con el dedo de IPD en el segundo paso](images/ipd-finger-alignment-300px.jpg)<br>

*Pantalla de alineación con el dedo de IPD en el segundo paso*

En HoloLens, se le pedirá que calibre los objetos visuales durante la instalación. Esto permite que el dispositivo ajuste la presentación del holograma según la [distancia de Interpupillary](https://en.wikipedia.org/wiki/Interpupillary_distance) del usuario (IPD). Con un IPD incorrecto, los hologramas pueden aparecer inestables o en una distancia incorrecta.

Una vez que Cortana se introduce a sí mismo, el primer paso de configuración es la calibración. Se recomienda completar el paso de calibración durante esta fase de configuración, pero se puede omitir esperando a que Cortana le pida que indique "SKIP" para continuar.

A los usuarios se les pide que alineen su dedo con una serie de seis destinos por ojo. A través de este proceso, HoloLens establece el IPD correcto para el usuario. Si la calibración debe actualizarse o ajustarse para un nuevo usuario, se puede ejecutar fuera de la instalación mediante la aplicación de calibración.

### <a name="calibration-app"></a>Aplicación de calibración

La calibración puede realizarse en cualquier momento a través de la aplicación de calibración. La aplicación de calibración se instala de manera predeterminada y se puede acceder a ella desde el menú Inicio o a través de la aplicación de configuración. Se recomienda la calibración si desea mejorar la calidad de los objetos visuales o para calibrar los objetos visuales para un nuevo usuario.

**Iniciar la aplicación desde el inicio**
1. Use la [floración](gestures.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione **+** esta información para ver todas las aplicaciones.
3. **Calibración**de inicio.

![Acceso a la aplicación de calibración desde el shell](images/calibration-shell.png)

![La aplicación de calibración que se muestra como un cubo activo después de iniciarse](images/calibration-livecube-200px.png)

**Inicio de la aplicación desde la configuración**
1. Use la [floración](gestures.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione **+** esta opción para ver todas las aplicaciones si la **configuración** no está anclada para iniciarse.
3. **Configuración**de inicio.
4. Vaya a**utilidades** **del sistema** > y seleccione **abrir calibración**.

![Inicio de la aplicación de calibración desde la aplicación de configuración](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a>Cascos envolventes

Para cambiar IPD dentro de los auriculares, abra la aplicación de configuración y vaya a la**pantalla de casco** de **realidad** > mixta y mueva el control deslizante. Verá los cambios en tiempo real en el casco. Si conoce el IPD, quizás desde una visita a Optometrist, puede escribirlo directamente.

También puede ajustar esta configuración; para ello, vaya a **configuración** > de la**pantalla de casco** de**realidad** > mixta en su PC.

Si el casco no admite la personalización de IPD, se deshabilitará esta configuración.

## <a name="see-also"></a>Vea también
* [Consideraciones acerca del entorno en HoloLens](environment-considerations-for-hololens.md)
