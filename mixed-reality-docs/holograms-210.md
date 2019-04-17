---
title: Entrada MR 210 - mirada
description: Siga este tutorial con Unity, Visual Studio y HoloLens para conocer los detalles de mirada conceptos de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, mirada tutorial, academy,
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599377"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

# <a name="mr-input-210-gaze"></a>Entrada MR 210: Mirada

[Observación](gaze.md) es el primer formulario de entrada y revela el reconocimiento y la intención del usuario. El Sr. entrada 210 (también conocido como el Explorador de proyectos) es una profundización en los conceptos relacionados con la mirada para Windows Mixed Reality. Iremos agregando reconocimiento contextual a nuestro cursor y hologramas, si quiere aprovechar lo que la aplicación conoce mirada del usuario.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Tenemos un astronautas descriptivo que le ayudarán a aprender los conceptos de mirada. En [MR Fundamentos 101](holograms-101.md), tuvimos un cursor sencillo que simplemente seguir su mirada. Hoy nos estamos trasladando un paso más allá de los cursores simples:

* Estamos haciendo el cursor y nuestro hologramas basadas en la mirada: ambos cambiará en función de donde el usuario examina - o cuando el usuario es *no* buscando. Esto hace que sean compatibles con el contexto.
* Comentarios, agregaremos a nuestro cursor y hologramas para proporcionar al usuario obtener más contexto sobre lo que está usando como objetivo. Estos comentarios pueden audio y visuales.
* Le mostraremos destinatarios técnicas para ayudar a los usuarios a destinos más pequeños de posicionamiento.
* Le mostraremos cómo atraer la atención del usuario a sus hologramas con un indicador de dirección.
* Podrá mostrarle las técnicas para aprovechar sus hologramas con el usuario mientras se desplaza en torno a su mundo.

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los siguientes capítulos se guardó usando una versión anterior de Unity y el Kit de herramientas de realidad mixta. Aunque las instrucciones paso a paso son actuales y precisas, puede ver las secuencias de comandos y los objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para la posterioridad y porque se tratan los conceptos se siguen aplican.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>Entrada MR 210: Mirada</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).
* Básica C# capacidad de programación.
* Debe haber completado [MR Fundamentos 101](holograms-101.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Erratas y notas

* En Visual Studio, debe ser "Solo mi código" deshabilitado (desactivado) en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1: instalación de Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Objetivos

* Optimizar el desarrollo de HoloLens Unity.
* Importar recursos y configuración de la escena.
* Ver a los astronautas en el HoloLens.

### <a name="instructions"></a>Instrucciones

1. Inicie Unity.
2. Seleccione **nuevo proyecto**.
3. Denomine el proyecto **ModelExplorer**.
4. Escriba la ubicación que el **que mirar** carpeta que anteriormente no archivados.
5. Asegúrese de que el proyecto está establecido en **3D**.
6. Haga clic en **crear proyecto**.

### <a name="unity-settings-for-hololens"></a>Configuración de Unity para HoloLens

Es necesario informar a Unity que se debe crear la aplicación que estamos intentando exportar una [vista envolvente](app-views.md) en lugar de una vista 2D. Para hacerlo mediante la adición de HoloLens como un dispositivo de realidad virtual.

1. Vaya a **Editar > configuración del proyecto > Reproductor**.
2. En el **Panel Inspector** para la configuración del Reproductor, seleccione la **Windows Store** icono.
3. Expanda el **configuración XR** grupo.
4. En el **representación** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar un nuevo **SDK de realidad Virtual** lista.
5. Compruebe que **Windows Mixed Reality** aparece en la lista. Si no, seleccione el **+** situado en la parte inferior de la lista y elija **Windows Holographic**.

A continuación, se debe establecer nuestro back-end de scripting a. NET.

1. Vaya a **Editar > configuración del proyecto > Reproductor** (todavía puede tener esta en el paso anterior).
2. En el **Panel Inspector** para la configuración del Reproductor, seleccione la **Windows Store** icono.
3. En el **otra configuración** configuración sección, asegúrese de que **back-end de Scripting** está establecido en **.NET**

Por último, actualizaremos nuestra configuración de calidad para lograr un rendimiento rápido en HoloLens.

1. Vaya a **Editar > configuración del proyecto > calidad**.
2. Haga clic en la flecha hacia abajo en la **predeterminado** fila bajo el icono de Windows Store.
3. Seleccione **más rápido** para **Windows Store Apps**.

### <a name="import-project-assets"></a>Importar los recursos del proyecto

1. Haga clic en el **activos** carpeta en el **proyecto** panel.
2. Haga clic en **Importar paquete > paquete personalizado**.
3. Vaya a los archivos del proyecto descargado y haga clic en **ModelExplorer.unitypackage**.
4. Haga clic en **Abrir**.
5. Después de carga el paquete, haga clic en el **importación** botón.

### <a name="setup-the-scene"></a>Programa de instalación de la escena

1. En la jerarquía, elimine el **cámara principal**.
2. En el **HoloToolkit** carpeta, abra el **entrada** carpeta, a continuación, abra el **prefabricados** carpeta.
3. Arrastre y coloque el **MixedRealityCameraParent** prefabricado desde el **prefabricados** carpeta en el **jerarquía**.
4. Haga clic en el **luz direccional** en la jerarquía y seleccione **eliminar**.
5. En el **hologramas** carpeta, arrastre y coloque los recursos siguientes en la raíz de la **jerarquía**:
    * **AstroMan**
    * **luces**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Iniciar **reproducir modo** ▶ para ver los astronautas.
7. Haga clic en **reproducir modo** ▶ nuevamente a **detener**.
8. En el **hologramas** carpeta, busque el **Fitbox** activo y arrástrelo a la raíz de la **jerarquía**.
9. Seleccione el **Fitbox** en el **jerarquía** panel.
10. Arrastre el **AstroMan** colección desde la **jerarquía** a la **holograma colección** propiedad de la Fitbox en el **Inspector** panel.

### <a name="save-the-project"></a>Guarde el proyecto

1. Guarde la nueva escena: **Archivo > Guardar escena como**.
2. Haga clic en **nueva carpeta** y el nombre de la carpeta **escenas**.
3. Nombre del archivo "**ModelExplorer**" y guárdela en el **escenas** carpeta.

### <a name="build-the-project"></a>Compilar el proyecto

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Haga clic en **agregar escenas abierto** para agregar la escena.
3. Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.
4. Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**. En caso contrario, déjelo en **cualquier dispositivo**.
5. Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).
6. Haz clic en **Compilación**.
7. Crear un **nueva carpeta** denominada "Aplicación".
8. Solo haga clic en el **aplicación** carpeta.
9. Presione **Seleccionar carpeta**.

Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.

1. Abra el **aplicación** carpeta.
2. Abra el **ModelExplorer Visual Studio solución**.

Si la implementación en HoloLens:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.
2. Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.
3. Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**. Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**. Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Cuando haya implementado la aplicación, descartar los **Fitbox** con un **seleccione gesto**.

Si la implementación en un auricular envolvente:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.
2. Asegúrese de que el destino de implementación se establece en **máquina Local**.
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
4. Cuando haya implementado la aplicación, descartar los **Fitbox** extrayendo el desencadenador en un controlador de movimiento.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capítulo 2: comentarios del Cursor y de destino

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Objetivos

* Diseño visual del cursor y el comportamiento.
* Comentarios del cursor basado en la mirada.
* Comentarios en función de mirada holograma.

Vamos a basar nuestra labor en algunos principios de diseño de cursor, a saber:

* El cursor siempre está presente.
* No permita que el cursor obtener demasiado pequeña o grande.
* Evite obstrucción de contenido.

### <a name="instructions"></a>Instrucciones

1. En el **HoloToolkit\Input\Prefabs** carpeta, busque la **InputManager** activo.
2. Arrastre y coloque el **InputManager** hasta la **jerarquía**.
3. En el **HoloToolkit\Input\Prefabs** carpeta, busque la **Cursor** activo.
4. Arrastre y coloque el **Cursor** hasta la **jerarquía**.
5. Seleccione el **InputManager** objeto en el **jerarquía**.
6. Arrastre el **Cursor** objeto desde el **jerarquía** en el InputManager **SimpleSinglePointerSelector**del **Cursor** campo, en el parte inferior de la **Inspector**.

![Configuración de Selector de puntero único simple](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilación e implementación

1. Vuelva a compilar la aplicación de **archivo > configuración de compilación**.
2. Abra el **carpeta aplicación**.
3. Abra el **ModelExplorer Visual Studio solución**.
4. Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
5. Observe cómo se dibuja el cursor, y cómo cambia de apariencia si toca un holograma.

### <a name="instructions"></a>Instrucciones

1. En el **jerarquía** del panel, expanda el **AstroMan**->**GEO_G**->**Back_Center** objeto.
2. Haga doble clic en **Interactible.cs** para abrirlo en Visual Studio.
3. Comentarios de las líneas en el **IFocusable.OnFocusEnter()** y **IFocusable.OnFocusExit()** devoluciones de llamada en **Interactible.cs**. Se denominan por InputManager Mixed Reality del Kit de herramientas cuando el foco (ya sea mediante la mirada o controlador señalando) entra y sale colisionador del GameObject específico.

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
>Usamos `EnableKeyword` y `DisableKeyword` anteriormente. Para hacer que el uso de estas opciones en su propia aplicación con el sombreador de este Kit de herramientas estándar, deberá seguir el [directrices de Unity para tener acceso a materiales a través de la secuencia de comandos](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). En este caso, ya hemos incluido la [tres variantes de material resaltado](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) necesarios en la carpeta de recursos (busque los materiales con resaltado en el nombre de tres).

### <a name="build-and-deploy"></a>Compilación e implementación

1. Como antes, compile el proyecto e implemente en el HoloLens.
2. Observe lo que sucede cuando la mirada está destinado a un objeto y cuando no lo es.

## <a name="chapter-3---targeting-techniques"></a>Capítulo 3: técnicas de destinatarios

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Objetivos

* Facilitar hologramas de destino.
* Estabilizar movimientos principales naturales.

### <a name="instructions"></a>Instrucciones

1. En el **jerarquía** panel, seleccione el **InputManager** objeto.
2. En el **Inspector** panel, busque el **que mirar estabilizador** secuencia de comandos. Haga clic en él para abrirlo en Visual Studio, si desea echar un vistazo.
    * Este script recorre en iteración las muestras de datos Raycast y ayuda a estabilizar la mirada del usuario para dirigirse a la precisión.
3. En el **Inspector**, puede editar el **almacenados estabilidad ejemplos** valor. Este valor representa el número de muestras que el estabilizador itera a calcular el valor estabilizado.

## <a name="chapter-4---directional-indicator"></a>Capítulo 4: indicador de dirección

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Objetivos

* Agregar un indicador de dirección en el cursor para ayudar a encontrar hologramas.

### <a name="instructions"></a>Instrucciones

Vamos a usar el **DirectionIndicator.cs** archivo, que:

1. Mostrar el indicador de dirección si el usuario no es gazing en el hologramas.
2. Si el usuario es gazing en el hologramas, ocultar el indicador de dirección.
3. Actualice el indicador de dirección para que apunte a la hologramas.

Empecemos.

1. Haga clic en el **AstroMan** objeto en el **jerarquía** panel y **haga clic en la flecha** para expandirlo.
2. En el **jerarquía** panel, seleccione el **DirectionalIndicator** objeto bajo **AstroMan**.
3. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
4. En el menú, escriba en el cuadro de búsqueda **indicador de dirección**. Seleccione el resultado de búsqueda.
5. En el **jerarquía** panel, arrastre y coloque el **Cursor** objeto en el **Cursor** propiedad en el **Inspector**.
6. En el **proyecto** panel el **hologramas** carpeta, arrastre y coloque el **DirectionalIndicator** activo hasta la **indicadores direccionales**propiedad en el **Inspector**.
7. Compile e implemente la aplicación.
8. Vea cómo el objeto de indicadores direccionales le ayuda a encontrar a los astronautas.

## <a name="chapter-5---billboarding"></a>Capítulo 5: vallas publicitarias

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Objetivos

* Usar vallas publicitarias para hologramas hacia TI se enfrentan a siempre.

Vamos a usar el **Billboard.cs** archivo para mantener un GameObject orientada a servicios, que es accesible desde el usuario en todo momento.

1. En el **jerarquía** panel, seleccione el **AstroMan** objeto.
2. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
3. En el menú, escriba en el cuadro de búsqueda **cartelera**. Seleccione el resultado de búsqueda.
4. En el **Inspector** establecer el **Pivot eje** a **Y**.
5. Pruébalo. Compile e implemente la aplicación como antes.
6. Vea Cómo enfrenta el objeto cartelera independientemente de cómo se puede cambiar el punto de vista.
7. Elimine el script desde el **AstroMan** por ahora.

## <a name="chapter-6---tag-along"></a>Capítulo 6: Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Objetivos

* Usar Tag-Along para que nuestro hologramas Síganos en torno a la sala de reuniones.

Mientras se trabaja en este problema, se le guiará por las restricciones de diseño siguientes:

* Contenido siempre debe ser un solo vistazo ausente.
* No debe ser el contenido de la forma.
* Contenido principal de bloqueo es incómodo.

La solución que se usa aquí es usar un enfoque de "tag-along".

Un objeto tag-along totalmente nunca deja la vista del usuario. Se puede considerar el un tag-along como un objeto asociado al encabezado del usuario bandas de goma. Cuando el usuario se mueve, se mantendrá el contenido dentro de un solo vistazo fácil desplazando hacia el borde de la vista sin salir completamente. Cuando el usuario gazes hacia el objeto tag-along, resulta más completa en la vista.

Vamos a usar el **SimpleTagalong.cs** archivo, que:

1. Determine si el objeto Tag-Along dentro de los límites de la cámara.
2. Si no es así en frustum de visualización, colocar el Tag-Along a parcialmente dentro del frustum de vista.
3. En caso contrario, coloque el Tag-Along a una distancia predeterminada del usuario.

Para ello, primero debemos cambiar el **Interactible.cs** script para llamar a la **TagalongAction**.

1. Editar **Interactible.cs** completando codificación ejercicio 6.a (84 a 87 quitando los comentarios de líneas).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

El **InteractibleAction.cs** secuencia de comandos, emparejada con **Interactible.cs** realiza acciones personalizadas cuando pulse en hologramas. En este caso, vamos a usar otro específicamente para tag-along.

* En el **Scripts** carpeta, haga clic en **TagalongAction.cs** activos para abrir en Visual Studio.
* Completar el ejercicio de codificación o cámbielo a esto:
  * En la parte superior de la **jerarquía**, en el tipo de barra de búsqueda **ChestButton_Center** y seleccione el resultado.
  * En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
  * En el menú, escriba en el cuadro de búsqueda **acción sean**. Seleccione el resultado de búsqueda.
  * En **hologramas** Buscar carpeta la **sean** activo.
  * Seleccione el **ChestButton_Center** objeto en el **jerarquía**. Arrastrar y colocar la **sean** objeto desde el **proyecto** panel en el **Inspector** en el **objeto a sean** propiedad.
  * Arrastre el **acción sean** objeto desde el **Inspector** en el **acción Interactible** campo el **Interactible** script.
* Haga doble clic en el **TagalongAction** script para abrirlo en Visual Studio.

![Instalación interactible](images/holograms210-interactible.png)

Se debe agregar lo siguiente:

* Agregar funcionalidad a la función PerformAction en el script TagalongAction (heredado de InteractibleAction).
* Agregue vallas publicitarias para el objeto gazed tras y establezca el eje pivot en XY.
* A continuación, agregue Tag-Along simple al objeto.

Aquí está nuestra solución, de **TagalongAction.cs**:

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
* Vea cómo el contenido sigue el centro del punto de mirada, pero no continuamente y sin bloquearla.
