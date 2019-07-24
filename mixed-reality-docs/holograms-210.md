---
title: Entrada MR 210-mirada
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de la mirada.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, mira fijamente
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993551"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

# <a name="mr-input-210-gaze"></a>Entrada MR 210: Mirada

[Mira](gaze.md) la primera forma de entrada y revela la intención y el reconocimiento del usuario. La entrada MR 210 (también conocido como Project Explorer) es un análisis profundo de los conceptos relacionados con la mirada para Windows Mixed Reality. Agregaremos reconocimiento contextual a nuestro cursor y a los hologramas, aprovechando al máximo lo que la aplicación conoce sobre la mirada del usuario.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Tenemos un Astronaut descriptivo aquí para ayudarle a conocer los conceptos de la mirada. En los [principios de MR 101](holograms-101.md), teníamos un cursor sencillo que acaba de hacer una mirada. Hoy vamos a mover un paso más allá del cursor simple:

* Estamos haciendo el cursor y nuestros hologramas con atención rápida: ambos cambiarán en función de dónde esté buscando el usuario o de dónde *no* esté buscando el usuario. Esto hace que sean compatibles con el contexto.
* Agregaremos comentarios a nuestro cursor y a los hologramas para proporcionar al usuario más contexto sobre lo que se va a dirigir. Estos comentarios pueden ser audio y objetos visuales.
* Le mostraremos las técnicas de destino para ayudar a los usuarios a alcanzar destinos más pequeños.
* Le mostraremos cómo atraer la atención del usuario a sus hologramas con un indicador direccional.
* Le enseñaremos técnicas para tomar sus hologramas con el usuario a medida que se desplaza por su mundo.

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta. Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Entrada MR 210: Mirada</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de comenzar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.
* Funcionalidad básica C# de programación.
* Debe haber completado los [principios básicos 101](holograms-101.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) requeridos por el proyecto. Requiere Unity 2017,2 o posterior.
* Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Erratas y notas

* En Visual Studio, "Solo mi código" debe estar deshabilitado (desactivado) en herramientas-> Opciones-> depuración para alcanzar puntos de interrupción en el código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1: configuración de Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Objetivos

* Optimizar Unity para el desarrollo de HoloLens.
* Importar recursos y configurar la escena.
* Vea el Astronaut en HoloLens.

### <a name="instructions"></a>Instrucciones

1. Inicia Unity.
2. Seleccione **nuevo proyecto**.
3. Asigne al proyecto el nombre **ModelExplorer**.
4. Escriba ubicación como la  carpeta de miras que ha eliminado previamente.
5. Asegúrate de que el proyecto esté establecido en **3D** (3D).
6. Haz clic en **Create Project** (Crear proyecto).

### <a name="unity-settings-for-hololens"></a>Configuración de Unity para HoloLens

Necesitamos que Unity sepa que la aplicación que se está intentando exportar debe crear una [vista envolvente](app-views.md) en lugar de una vista 2D. Lo hacemos agregando HoloLens como un dispositivo de realidad virtual.

1. Vaya a **editar > configuración del proyecto > Player**.
2. En el **panel Inspector** de configuración del reproductor, seleccione el icono de la **tienda Windows** .
3. Expanda el grupo de **configuración de XR** .
4. En la sección **representación** , active la casilla **compatibilidad con realidad virtual** para agregar una nueva lista de **SDK de realidad virtual** .
5. Compruebe que **Windows Mixed Reality** aparece en la lista. Si no es así, **+** Seleccione el botón situado en la parte inferior de la lista y elija **Windows Holographic**.

A continuación, es necesario establecer nuestro back-end de scripting en .NET.

1. Vaya a **editar > configuración del proyecto > Player** (es posible que todavía lo tenga en el paso anterior).
2. En el **panel Inspector** de configuración del reproductor, seleccione el icono de la **tienda Windows** .
3. En la sección configuración de **otros valores** , asegúrese de que el **back-end** de scripting está establecido en **.net.**

Por último, actualizaremos la configuración de calidad para lograr un rendimiento rápido en HoloLens.

1. Vaya a **editar > configuración del proyecto > calidad**.
2. Haga clic en la flecha hacia abajo de la fila **predeterminada** bajo el icono de la tienda Windows.
3. Seleccione **muy bajo** para **aplicaciones de la tienda Windows**.

### <a name="import-project-assets"></a>Importar recursos del proyecto

1. Haga clic con el botón secundario en la carpeta **activos** del panel **proyecto** .
2. Haga clic en **importar paquete > paquete personalizado**.
3. Navegue hasta los archivos de proyecto que descargó y haga clic en **ModelExplorer. unitypackage Tools**.
4. Haga clic en **Abrir**.
5. Una vez cargado el paquete, haga clic en el botón **importar** .

### <a name="setup-the-scene"></a>Configuración de la escena

1. En la jerarquía, elimine la **cámara principal**.
2. En la carpeta **HoloToolkit** , abra la carpeta **Input** y, a continuación, abra la carpeta **Prefabs** .
3. Arrastre y coloque el recurso prefabricado de **MixedRealityCameraParent** de la carpeta **Prefabs** en la **jerarquía**.
4. Haga clic con el botón derecho en la **luz direccional** de la jerarquía y seleccione **eliminar**.
5. En la  carpeta hologramas, arrastre y coloque los recursos siguientes en la raíz de la **jerarquía**:
    * **AstroMan**
    * **Circular**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Inicie el **modo de reproducción** ▶ para ver el Astronaut.
7. Vuelva a hacer clic en **modo de reproducción** ▶ para detenerse.
8. En la  carpeta hologramas, busque el recurso **Fitbox** y arrástrelo hasta la raíz de la **jerarquía**.
9. Seleccione **Fitbox** en el panel **jerarquía** .
10. Arrastre la colección **AstroMan** desde la **jerarquía** a la propiedad de **colección holograma** de Fitbox en el panel **Inspector** .

### <a name="save-the-project"></a>Guardar el proyecto

1. Guarde la nueva escena: **Archivo > guardar la escena como**.
2. Haga clic en **nueva carpeta** y asigne un nombre a la carpeta Scenes.
3. Asigne al archivo el nombre "**ModelExplorer**" y guárdelo en  la carpeta Scenes.

### <a name="build-the-project"></a>Compilación del proyecto

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Haga clic en **Agregar escenas abiertas** para agregar la escena.
3. Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.
4. Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**. De lo contrario, déjelo en **cualquier dispositivo**.
5. Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).
6. Haz clic en **Compilación**.
7. Cree una **nueva carpeta** denominada "app".
8. Haga clic en la carpeta de la **aplicación** .
9. Presione **Seleccionar carpeta**.

Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.

1. Abra la carpeta de la **aplicación** .
2. Abra la **solución ModelExplorer de Visual Studio**.

Si se implementa en HoloLens:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.
2. Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.
3. Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** . Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.
4. En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**. Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.

Si se implementa en un auricular envolvente:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.
2. Asegúrese de que el destino de implementación está establecido en **equipo local**.
3. En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.
4. Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capítulo 2: comentarios de cursores y de destino

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Objetivos

* Comportamiento y diseño visual de los cursores.
* Comentarios del cursor basados en la mirada.
* Comentarios sobre hologramas basados en la mirada.

Vamos a basar nuestro trabajo en algunos principios de diseño de cursores, es decir:

* El cursor siempre está presente.
* No deje que el cursor sea demasiado pequeño o grande.
* Evite obstruir el contenido.

### <a name="instructions"></a>Instrucciones

1. En la carpeta **HoloToolkit\Input\Prefabs** , busque el recurso **InputManager** .
2. Arrastre y coloque el **InputManager** en la **jerarquía**.
3. En la carpeta **HoloToolkit\Input\Prefabs** , busque el recurso **cursor** .
4. Arrastre y coloque el **cursor** en la **jerarquía**.
5. Seleccione el objeto **InputManager** en la **jerarquía**.
6. Arrastre el objeto **cursor** desde la **jerarquía** al campo **cursor** de la **SimpleSinglePointerSelector**de InputManager, en la parte inferior del **Inspector**.

![Configuración sencilla del selector de puntero único](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilación e implementación

1. Vuelva a compilar la aplicación desde el **archivo > la configuración de compilación**.
2. Abra la **carpeta**de la aplicación.
3. Abra la **solución ModelExplorer de Visual Studio**.
4. Haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.
5. Observe cómo se dibuja el cursor y cómo cambia la apariencia si toca un holograma.

### <a name="instructions"></a>Instrucciones

1. En el panel **jerarquía** , expanda el objeto **AstroMan**->**GEO_G**->**Back_Center** .
2. Haga doble clic en **Interactible.CS** para abrirlo en Visual Studio.
3. Quite las marcas de comentario de las líneas de las devoluciones de llamada **IFocusable. OnFocusEnter ()** y **IFocusable. OnFocusExit ()** en **Interactible.CS**. Las llama el InputManager del kit de herramientas de realidad mixta cuando el foco (ya sea por miras o por controlador) entra y sale del Colisionador de GameObject específico.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>`EnableKeyword` Usamos y `DisableKeyword` versiones posteriores. Con el fin de usarlos en su propia aplicación con el sombreador estándar del kit de herramientas, debe seguir las [directrices de Unity para acceder a los materiales a través del script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). En este caso, ya hemos incluido las [tres variantes de material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) resaltado necesarios en la carpeta de recursos (busque los tres materiales con resaltado en el nombre).

### <a name="build-and-deploy"></a>Compilación e implementación

1. Como antes, compile el proyecto e impleméntelo en HoloLens.
2. Observe lo que sucede cuando la mirada está dirigida a un objeto y cuando no lo está.

## <a name="chapter-3---targeting-techniques"></a>Capítulo 3: técnicas de destino

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Objetivos

* Facilitar el destino de los hologramas.
* Estabilice los movimientos de los cabezales naturales.

### <a name="instructions"></a>Instrucciones

1. En el panel **jerarquía** , seleccione el objeto **InputManager** .
2. En el panel **Inspector** , busque el script del estabilizador de **miras** . Haga clic en él para abrirlo en Visual Studio, si desea echar un vistazo.
    * Este script recorre en iteración muestras de datos de Raycast y ayuda a estabilizar la mirada del usuario para el destino de precisión.
3. En el **Inspector**, puede editar el valor de los **ejemplos de estabilidad almacenados** . Este valor representa el número de muestras que el estabilizador recorre en iteración para calcular el valor estabilizado.

## <a name="chapter-4---directional-indicator"></a>Capítulo 4: indicador direccional

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Objetivos

* Agregue un indicador direccional en el cursor para buscar hologramas.

### <a name="instructions"></a>Instrucciones

Vamos a usar el archivo **DirectionIndicator.CS** , que:

1. Muestra el indicador direccional si el usuario no se Gazing en los hologramas.
2. Oculte el indicador direccional si el usuario es Gazing en los hologramas.
3. Actualice el indicador direccional para que apunte a los hologramas.

Empecemos.

1. Haga clic en el objeto **AstroMan** en el panel **jerarquía** y **haga clic en la flecha** para expandirlo.
2. En el panel **jerarquía** , seleccione el objeto **DirectionalIndicator** en **AstroMan**.
3. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
4. En el menú, escriba en el indicador de **Dirección**del cuadro de búsqueda. Seleccione el resultado de la búsqueda.
5. En el panel **jerarquía** , arrastre y coloque el objeto **cursor** en la propiedad **cursor** del **Inspector**.
6. En el **panel Proyecto** , en la **carpeta hologramas** , arrastre y coloque el recurso **DirectionalIndicator** en la propiedad **indicador direccional** del **Inspector**.
7. Compile e implemente la aplicación.
8. Vea cómo el objeto indicador direccional le ayuda a encontrar el Astronaut.

## <a name="chapter-5---billboarding"></a>Capítulo 5: cartelera

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Objetivos

* Use la cartelera para que los hologramas siempre se encuentren en su caso.

Vamos a usar el archivo **Billboard.CS** para mantener una orientación GameObject de forma que se enfrente al usuario en todo momento.

1. En el panel **jerarquía** , seleccione el objeto **AstroMan** .
2. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
3. En el menú, escriba en el cuadro de búsqueda de la **cartelera**. Seleccione el resultado de la búsqueda.
4. En el **Inspector** , establezca el **eje dinámico** en **Y**.
5. Pruébalo. Compile e implemente la aplicación como antes.
6. Vea cómo se enfrenta el objeto de la cartelera independientemente de cómo cambie el punto de vista.
7. Elimine el script de **AstroMan** por ahora.

## <a name="chapter-6---tag-along"></a>Capítulo 6: Etiquetas:

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Objetivos

* Use la etiqueta para que nuestros hologramas nos vayan alrededor de la habitación.

A medida que trabajamos en este problema, se le guiará por las siguientes restricciones de diseño:

* El contenido siempre debe ser un vistazo.
* El contenido no debe estar en el camino.
* No se siente el contenido del bloqueo de encabezado.

La solución que se usa aquí es usar un enfoque "etiqueta a lo largo".

Un objeto de etiqueta no deja completamente la vista del usuario. Puede pensar en una etiqueta, como un objeto asociado al encabezado del usuario por las bandas de goma. A medida que el usuario se mueve, el contenido permanecerá dentro de un sencillo vistazo mediante la deslizamiento hacia el borde de la vista sin salir completamente. Cuando el usuario mira hacia el objeto de etiqueta, resulta más completo ver.

Vamos a usar el archivo **SimpleTagalong.CS** , que:

1. Determine si el objeto de etiqueta se encuentra dentro de los límites de la cámara.
2. Si no se encuentra dentro del frustum de vista, coloque la etiqueta junto a parcialmente dentro del frustum de la vista.
3. De lo contrario, coloque la etiqueta junto a una distancia predeterminada del usuario.

Para ello, primero debemos cambiar el script **Interactible.CS** para llamar a **TagalongAction**.

1. Edite **Interactible.CS** completando la codificación del ejercicio 6. a (Quite los comentarios de las líneas 84 a 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

El script **InteractibleAction.CS** , emparejado con **Interactible.CS** , realiza acciones personalizadas cuando se pulsa en los hologramas. En este caso, usaremos un específicamente para etiquetar.

* En la  carpeta scripts, haga clic en el recurso **TagalongAction.CS** para abrirlo en Visual Studio.
* Complete el ejercicio de codificación o cámbielo por este:
  * En la parte superior de la **jerarquía**, en la barra de búsqueda, escriba **ChestButton_Center** y seleccione el resultado.
  * En el panel **Inspector** , haga clic en el botón **Agregar componente** .
  * En el menú, escriba en la **acción tagalong**del cuadro de búsqueda. Seleccione el resultado de la búsqueda.
  * En  la carpeta hologramas, busque el recurso **tagalong** .
  * Seleccione el objeto **ChestButton_Center** en la **jerarquía**. Arrastre y coloque el objeto **TagAlong** del panel **proyecto** en el **Inspector** en el **objeto en** la propiedad TagAlong.
  * Arrastre el objeto de **acción tagalong** desde el **Inspector** al campo **Acción** interactiva del script **interactuable** .
* Haga doble clic en el script **TagalongAction** para abrirlo en Visual Studio.

![Instalación interactiva](images/holograms210-interactible.png)

Necesitamos agregar lo siguiente:

* Agregue funcionalidad a la función PerformAction en el script TagalongAction (se hereda de InteractibleAction).
* Agregue la cartelera al objeto mirados y establezca el eje dinámico en XY.
* A continuación, agregue la etiqueta simple junto al objeto.

Esta es nuestra solución, desde **TagalongAction.CS**:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* Pruébalo. Compile e implemente la aplicación.
* Vea cómo el contenido sigue el centro del punto de miración, pero no continuamente y sin bloquearlo.
