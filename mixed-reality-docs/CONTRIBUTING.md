---
title: Instrucciones de contribución
description: Cómo contribuir a la documentación de Windows Mixed Reality.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605694"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Colaborar en la documentación para desarrolladores de Windows Mixed Reality

Bienvenido a la [repositorio público de documentación para desarrolladores de Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! Los artículos se crean o editan en este repositorio **serán visibles para el público.** 

Los documentos de Windows Mixed Reality ahora están en la plataforma de docs.microsoft.com, que usa el marcado característico de GitHub (con características Markdig). En esencia, activar en páginas estilizadas y con formato que se muestran en el contenido que se edita en este repositorio https://docs.microsoft.com/windows/mixed-reality. 

Esta página trata los pasos básicos y directrices para contribuir, así como vínculos a los conceptos básicos de Markdown. Le agradecemos su contribución.

## <a name="before-you-start"></a>Antes de empezar

Si aún no tiene uno, deberá [crear una cuenta de GitHub](https://github.com/join).

>[!NOTE]
>Si es empleado de Microsoft, vincular su cuenta de GitHub para el alias de Microsoft en la [portal de código abierto de Microsoft](https://repos.opensource.microsoft.com/). Únase a la **"Microsoft"** y **"MicrosoftDocs"** organizaciones).

Al configurar la cuenta de GitHub, también se recomienda que estas precauciones de seguridad:
- Crear un [contraseña segura para la cuenta de Github](https://github.com/settings/admin).
- Habilitar [autenticación en dos fases](https://github.com/settings/two_factor_authentication/configure).
- Guarde su [códigos de recuperación](https://github.com/settings/auth/recovery-codes) en un lugar seguro.
- Actualización de su [configuración del perfil público](https://github.com/settings/profile).
   - Configure su nombre y considere la posibilidad de su *correo electrónico público* a *no mostrar mi dirección de correo electrónico*.
   - Se recomienda cargar una imagen de perfil, tal como se mostrará una miniatura en páginas de docs a las que contribuya.
- Si tiene previsto usar un flujo de trabajo de línea de comandos, considere la posibilidad de configurar [Git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) para que no tengan que escribir la contraseña cada vez que realizar una contribución.

Si realiza estos pasos es importante, como el sistema de publicación está asociado a GitHub y se mostrarán como autor o colaborador en cada artículo mediante su alias de GitHub.

## <a name="editing-an-existing-article"></a>Edición de un artículo existente

Use el siguiente flujo de trabajo para realizar actualizaciones para *un artículo existente* a través de GitHub en un explorador web:

1. Vaya al artículo que desea editar en la carpeta "mixto de realidad-docs".
2. En la esquina superior derecha, seleccione el botón Editar (icono de lápiz). Esto automáticamente bifurcará descartable bifurcación de la rama "principal".

   ![Editar un artículo.](images/editpage.png)
3. Editar el contenido del artículo (consulte ["Aspectos básicos de Markdown"](#markdown-basics) a continuación para obtener instrucciones).
4. Actualizar los metadatos como importante en la parte superior de cada artículo:
   * title: Este es el título de página que aparece en la pestaña del explorador cuando se está viendo el artículo. Puesto que se usa para la indexación y la SEO, no debería cambiar el título a menos que es necesario (aunque esto es menos crítica antes de que quede pública documentación).
   * description: Escriba una breve descripción del contenido del artículo. Esto ayuda a SEO y detección.
   * Autor: Si es el propietario de la página principal, agregue aquí su alias de GitHub.
   * ms.author: Si es el propietario de la página principal, agregue su alias aquí de Microsoft (no es necesario @microsoft.com, sólo con el alias).
   * ms.date: Si va a agregar contenido importante a la página, pero no para las revisiones como aclaración, formato, gramática, o de ortografía, actualice la fecha.
   * palabras clave: Palabras clave ayudan a SEO (optimización de motor de búsqueda). Agregar palabras clave, separadas por una coma y un espacio, que son específicas de su artículo (pero sin puntuación después de la última palabra clave en la lista); no es necesario agregar las palabras clave globales que se aplican a todos los artículos, como los que se administran en otro lugar. 
5. Cuando haya completado las modificaciones del artículo, desplácese hacia abajo y haga clic en el **proponer cambio de archivo** botón.
6. En la siguiente página, haga clic en **crear solicitud de incorporación de cambios** para combinar la rama creada automáticamente en 'master'.
7. Repita los pasos anteriores para el siguiente artículo que desea editar.

## <a name="creating-a-new-article"></a>Crear un nuevo artículo

Use el siguiente flujo de trabajo *crear nuevos artículos* en el repositorio de documentación a través de GitHub en un explorador web:

1. Crear una bifurcación de la rama "principal" MicrosoftDocs/realidad mixta (mediante el **bifurcación** botón en la esquina superior derecha).

   ![Bifurcación de la rama maestra.](images/forkbranch.png)
2. En la carpeta "mixto de realidad-docs", haga clic en el **crear nuevo archivo** botón en la esquina superior derecha.
3. Crear un nombre de página para el artículo (utilice guiones en lugar de espacios y no use signos de puntuación o apóstrofos) y anexar "MD"

   ![Nombre de la nueva página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Asegúrese de que crear el nuevo artículo desde dentro de la carpeta "mixto de realidad-docs". Puede confirmarlo comprobando "/ docs de realidad mixta /" en la línea de nombre de archivo nuevo.

4. En la parte superior de la nueva página, agregue el siguiente bloque de metadatos:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Rellene los campos de metadatos relevantes por las instrucciones de la [sección anterior](#editing-an-existing-article).
6. Artículo de escritura contenido mediante [conceptos básicos de Markdown](#markdown-basics).
7. Agregar un `## See also` en la parte inferior del artículo con vínculos a artículos relevantes.
8. Cuando termine, haga clic en **confirmación nuevo archivo**.
9. Haga clic en **nueva solicitud de incorporación de cambios** y combinar rama "principal" de la bifurcación en MicrosoftDocs/realidad mixta 'master' (asegúrese de que la flecha señala la manera correcta).

   ![Crear solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/realidad mixta](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Conceptos básicos de markdown

Los siguientes recursos le ayudarán a obtener información sobre cómo editar la documentación mediante el lenguaje de Markdown:

- [Conceptos básicos de markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Póster de referencia de markdown de instantánea](images/MarkdownPoster.pdf)
- [Recursos adicionales para la escritura de Markdown para docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Agregar tablas

Debido a las tablas de los estilos de docs.microsoft.com de forma, no tienen bordes o estilos personalizados, incluso si se trata de CSS en línea. Parece que funcionan durante un breve período de tiempo, pero finalmente la plataforma eliminará el estilo fuera de la tabla. Por lo tanto, planee con antelación y simplificar las tablas. [Este es un sitio que facilita las tablas de Markdown](http://www.tablesgenerator.com/markdown_tables).

El [extensión Docs Markdown para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) también hace que la tabla generación fácil si usa [Visual Studio Code (ver abajo)](#using-visual-studio-code) para editar la documentación.

### <a name="adding-images"></a>Adición de imágenes

Deberá cargar sus imágenes a la carpeta "mixto-realidad-docs/images" en el repositorio y, a continuación, hacer referencia a ellos correctamente en el artículo. Las imágenes se mostrarán automáticamente en tamaño completo, lo que significa que si la imagen es grande, rellenará todo el ancho del artículo. Por lo tanto, se recomienda ajustar previamente el tamaño de las imágenes antes de cargarlos. El ancho recomendado es de 600 a 700 píxeles, aunque debe dimensionar o reducir verticalmente si es una captura de pantalla con gran densidad o una fracción de una captura de pantalla, respectivamente.

>[!IMPORTANT]
>Solo puede cargar imágenes en el repositorio bifurcado antes de la mezcla. Por lo tanto, si tiene previsto agregar imágenes a un artículo, deberá [usar Visual Studio Code](#using-visual-studio-code) para agregar las imágenes a la carpeta "images" de la bifurcación primero o asegúrese de que ha hecho lo siguiente en un explorador web:
>
>1. Bifurcado el repositorio MicrosoftDocs/realidad mixta.
>2. Puede editar el artículo en la bifurcación.
>3. Cargar las imágenes que se hace referencia en el artículo a la carpeta "mixto-realidad-docs/images" en la bifurcación.
>4. Crea un **solicitud de extracción** para combinar la bifurcación en la rama "principal" MicrosoftDocs/realidad mixta.
>
>Para obtener información sobre cómo configurar su propio repositorio bifurcado, siga las instrucciones para [crear un nuevo artículo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Vista previa de su trabajo

Mientras se edita en GitHub a través de un explorador web, puede hacer clic en el **Preview** ficha cerca de la parte superior de la página para obtener una vista previa de su trabajo antes de confirmar. 

>[!NOTE]
>Vista previa de los cambios en review.docs.microsoft.com solo está disponible para los empleados de Microsoft

Los empleados de Microsoft: una vez que se han combinado las contribuciones en la rama "principal", puede ver el aspecto de la documentación antes de enviarlos pública en https://review.docs.microsoft.com/windows/mixed-reality?branch=master (encontrar su artículo con la tabla de contenido de la columna izquierda).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Edición en el explorador frente a edición con un cliente de escritorio

La edición en el explorador es la manera más fácil realizar cambios rápidos, sin embargo, hay algunas desventajas:

- No obtendrá el corrector ortográfico.
- No obtendrá ninguna vinculación inteligente a otros artículos (tendrá que escribir manualmente el nombre de archivo del artículo).
- Puede ser una molestia para cargar y hacer referencia a las imágenes.

Si en su lugar podría no tratar con estos problemas, es preferible usar un cliente de escritorio como [Visual Studio Code](https://code.visualstudio.com/) con un par [extensiones útiles](#useful-extensions) para contribuir a la documentación.

## <a name="using-visual-studio-code"></a>Con Visual Studio Code

Por motivos de la lista [anteriormente](#editing-in-the-browser-vs-editing-with-a-desktop-client), quizás prefiera usar un cliente de escritorio para editar la documentación en lugar de un explorador web. Se recomienda usar [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Programa de instalación

Siga estos pasos para configurar el código de Visual Studio para trabajar con este repositorio:

1. En un explorador web:
    1. Instalar [Git para su PC](https://git-scm.com/downloads).
    2. Instalar [código de Visual Studio](https://code.visualstudio.com/).
    3. [Bifurcar MicrosoftDocs/realidad mixta](#creating-a-new-article) si no lo ha hecho ya.
    4. En la bifurcación, haga clic en **clonar o descargar** y copie la dirección URL.
2. Crear un clon local de la bifurcación en Visual Studio Code:
    1. Desde el **vista** menú, seleccione **paleta de comandos**.
    2. Tipo "Git:Clone".
    3. Pegue la dirección URL que acaba de copiar.
    4. Elija dónde desea guardar el clon en su PC.
    5. Haga clic en **repositorio abierto** en el menú emergente.

### <a name="editing-documentation"></a>Edición de la documentación

Use el siguiente flujo de trabajo para realizar cambios en la documentación de Visual Studio Code:

>[!NOTE]
>Todas las instrucciones para [edición](#editing-an-existing-article) y [crear](#creating-a-new-article) artículos y el [aspectos básicos de la edición de Markdown](#markdown-basics), desde arriba se aplica cuando se usa Visual Studio Code también.

1. Asegúrese de que la bifurcación clonada está actualizada con el repositorio oficial.
   1. En un explorador web, cree una solicitud de incorporación de cambios para sincronizar los cambios recientes de otros colaboradores en MicrosoftDocs/realidad mixta 'master' en la bifurcación (asegúrese de que la flecha señala la manera correcta).
      
      ![Sincronizar los cambios de MicrosoftDocs/realidad mixta en la bifurcación](images/sync_repos.PNG)
   2. En Visual Studio Code, haga clic en el botón de sincronización para sincronizar la bifurcación recién actualizada al clon local.
      
      ![Haga clic en el botón Sincronizar](images/sync_clone.png)
2. Cree o edite artículos en el repositorio clonado mediante Visual Studio Code.
   1. Editar uno o más artículos (agregar imágenes a la carpeta "images" si es necesario).
   2. **Guardar** cambia en **Explorer**.
      
      ![Elija "Guardar todo" en el explorador](images/explorer_save.png)
   3. **Confirmar todo** cambia en **Control de código fuente** (Escribir mensaje de confirmación cuando se le solicite).
      
      ![Elija "Confirmar todo" en el Control de código fuente](images/source_control_commit.png)
   4. Haga clic en el **sincronización** botón para sincronizar los cambios de nuevo al origen (la bifurcación en GitHub).
      
      ![Haga clic en el botón Sincronizar](images/sync_back.png)
3. En un explorador web, cree una solicitud de incorporación de cambios para sincronizar los cambios nuevo en la bifurcación a MicrosoftDocs/realidad mixta 'master' (asegúrese de que la flecha señala la manera correcta).

   ![Crear solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/realidad mixta](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensiones útiles

Las siguientes extensiones de Visual Studio Code son muy útiles cuando se edita la documentación:

- [Extensión docs Markdown para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -uso **Alt + M** para que aparezca un menú de opciones, como de creación de docs:
   - Búsqueda y referencia de imágenes que ha cargado.
   - Agregar formato, como listas, tablas y leyendas específico de documentos como `>[!NOTE]`.
   - Buscar y hacer referencia a vínculos internos y los marcadores (vínculos a secciones específicas dentro de una página).
   - Se resaltan los errores de formato (mantenga el mouse sobre el error para obtener más información).
- [Corrector ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -aparecerá subrayadas; haga doble clic en una palabra mal escrita para cambiarla o guardarlo en el diccionario de palabras mal escritas.
