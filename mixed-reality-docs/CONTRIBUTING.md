---
title: Instrucciones de colaboración
description: Cómo contribuir a la documentación de Windows Mixed Reality.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: 934171f26571b3219bbe390aff44349fb6908f74
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437127"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Contribución a la documentación para desarrolladores de realidad mixta de Windows

Este es el [repositorio público de la documentación para desarrolladores de Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs). Los artículos que cree o edite en este repositorio **serán visibles para el público.** 

Los documentos de Windows Mixed Reality se encuentran ahora en la plataforma docs.microsoft.com, que usa el Markdown con tipo GitHub (con características Markdig). En esencia, el contenido que se edita en este repositorio se convierte en páginas con formato y estilizadas que se muestran en https://docs.microsoft.com/windows/mixed-reality. 

En esta página se describen los pasos básicos y las instrucciones para contribuir, así como vínculos a los conceptos básicos de Markdown. Gracias por su contribución.

## <a name="before-you-start"></a>Antes de empezar

Si aún no tiene una, deberá [crear una cuenta de github](https://github.com/join).

>[!NOTE]
>Si es un empleado de Microsoft, vincule su cuenta de GitHub a su alias de Microsoft en el [portal de código abierto de Microsoft](https://repos.opensource.microsoft.com/). Únase a las organizaciones **"Microsoft"** y **"MicrosoftDocs"** ).

Al configurar la cuenta de GitHub, también se recomiendan estas precauciones de seguridad:
- Cree una [contraseña segura para la cuenta de github](https://github.com/settings/admin).
- Habilitar [la autenticación en dos fases](https://github.com/settings/two_factor_authentication/configure).
- Guarde los [códigos de recuperación](https://github.com/settings/auth/recovery-codes) en un lugar seguro.
- Actualice la [configuración del perfil público](https://github.com/settings/profile).
   - Establezca su nombre y considere la posibilidad de establecer el *correo electrónico público* para *no mostrar la dirección de correo electrónico*.
   - Se recomienda cargar una imagen de perfil, ya que se mostrará una miniatura en las páginas de docs a las que contribuya.
- Si planea usar un flujo de trabajo de línea de comandos, considere la posibilidad de configurar el [Administrador de credenciales de Git para Windows de](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) modo que no tenga que escribir la contraseña cada vez que realice una contribución.

Realizar estos pasos es importante, ya que el sistema de publicación está asociado a GitHub y se mostrará como autor o colaborador en cada artículo mediante el alias de GitHub.

## <a name="editing-an-existing-article"></a>Edición de un artículo existente

Use el siguiente flujo de trabajo para efectuar actualizaciones en *un artículo existente* a través de github en un explorador Web:

1. Navegue hasta el artículo que desea editar en la carpeta "Mixed Reality-docs".
2. Seleccione el botón Editar (icono de lápiz) en la parte superior derecha. Se bifurcará automáticamente una rama descartable de la rama "principal".

   ![Edite un artículo.](images/editpage.png)
3. Edite el contenido del artículo (consulte ["conceptos básicos de Markdown"](#markdown-basics) a continuación para obtener instrucciones).
4. Actualice los metadatos como corresponda en la parte superior de cada artículo:
   * Título: este es el título de la página que aparece en la pestaña del explorador cuando se está viendo el artículo. Como se usa para SEO e indexación, no debe cambiar el título a menos que sea necesario (aunque esto es menos crítico antes de que la documentación sea pública).
   * Descripción: escriba una breve descripción del contenido del artículo. Esto ayuda en la SEO y la detección.
   * Autor: si es el propietario principal de la página, agregue aquí su alias de GitHub.
   * MS. Author: si es el propietario principal de la página, agregue aquí su alias de Microsoft (no necesita @microsoft.com, solo el alias).
   * MS. Date: actualice la fecha Si va a agregar contenido principal a la página, pero no para correcciones como aclaración, formato, gramática o ortografía.
   * Palabras clave: ayuda de palabras clave en SEO (optimización del motor de búsqueda). Agregue palabras clave, separadas por una coma y un espacio, específicas de su artículo (pero sin puntuación después de la última palabra clave de la lista); no es necesario agregar palabras clave globales que se apliquen a todos los artículos, ya que se administran en otro lugar. 
5. Cuando haya terminado de editar el artículo, desplácese hacia abajo y haga clic en el botón **proponer cambio de archivo** .
6. En la página siguiente, haga clic en **crear solicitud de incorporación** de cambios para fusionar mediante combinación la rama creada automáticamente en ' maestra '.
7. Repita los pasos anteriores para el siguiente artículo que desee editar.

## <a name="renaming-or-deleting-an-existing-article"></a>Cambiar el nombre o eliminar un artículo existente

Si el cambio cambiará el nombre o eliminará un artículo existente, asegúrese de agregar una redirección. De este modo, todos los usuarios con un vínculo al artículo existente seguirán en el lugar correcto. Las redirecciones se administran mediante el archivo. openpublishing. Redirection. JSON en la raíz del repositorio.

Para agregar una redirección a. openpublishing. Redirection. JSON, agregue una entrada a la matriz de `redirections`:

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- La `source_path` es la ruta de acceso relativa del repositorio al artículo anterior que se va a quitar. Asegúrese de que la ruta de acceso comienza con `mixed-reality-docs` y termina con `.md`.
- El `redirect_url` es la dirección URL pública relativa del artículo anterior al nuevo artículo. Asegúrese de que esta dirección **URL no contenga `mixed-reality-docs`** o `.md`, ya que hace referencia a la dirección URL pública y no a la ruta de acceso del repositorio. Se permite la vinculación a una sección del nuevo artículo mediante `#section`. También puede usar una ruta de acceso absoluta a otro sitio, si es necesario.
- `redirect_document_id` indica si desea conservar el identificador de documento del archivo anterior. El valor predeterminado es `false`. Use `true` si desea conservar el valor de atributo de `ms.documentid` del artículo redirigido. Si conserva el identificador de documento, los datos, como las vistas de página y las clasificaciones, se transferirán al artículo de destino. Haga esto si el redireccionamiento es principalmente un cambio de nombre y no un puntero a un artículo diferente que solo trata parte del mismo contenido.

Si agrega un redireccionamiento, asegúrese de eliminar también el archivo antiguo.

## <a name="creating-a-new-article"></a>Creación de un nuevo artículo

Use el siguiente flujo de trabajo para *crear nuevos artículos* en el repositorio de documentación a través de github en un explorador Web:

1. Cree una bifurcación desconectada de la rama "principal" de MicrosoftDocs/Mixed Reality (con el botón **bifurcar** en la parte superior derecha).

   ![Bifurcar la bifurcación principal.](images/forkbranch.png)
2. En la carpeta "Mixed Reality-docs", haga clic en el botón **crear nuevo archivo** en la parte superior derecha.
3. Crear un nombre de página para el artículo (usar guiones en lugar de espacios y no usar signos de puntuación ni apóstrofos) y anexar ". MD"

   ![Asigne un nombre a la nueva página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Asegúrese de crear el nuevo artículo desde la carpeta "Mixed Reality-docs". Puede confirmarlo comprobando "/Mixed-Reality-docs/" en la nueva línea de nombre de archivo.

4. En la parte superior de la página nueva, agregue el siguiente bloque de metadatos:

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

5. Rellene los campos de metadatos pertinentes según las instrucciones de la [sección anterior](#editing-an-existing-article).
6. Escriba el contenido del artículo con los [conceptos básicos de Markdown](#markdown-basics).
7. Agregue una sección `## See also` en la parte inferior del artículo con vínculos a otros artículos relevantes.
8. Cuando termine, haga clic en **confirmar nuevo archivo**.
9. Haga clic en **nueva solicitud de incorporación** de cambios y mezcle la rama ' maestra ' de la bifurcación en MicrosoftDocs/mixed-reality ' maestra ' (Asegúrese de que la flecha señala la manera correcta).

   ![Cree una solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Aspectos básicos de Markdown

Los siguientes recursos le ayudarán a aprender a editar la documentación con el lenguaje Markdown:

- [Aspectos básicos de Markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Póster de referencia de Markdown a un vistazo](images/MarkdownPoster.pdf)
- [Recursos adicionales para escribir Markdown para docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Agregar tablas

Debido a la forma en que docs.microsoft.com las tablas de estilos, no tendrán bordes ni estilos personalizados, aunque pruebe CSS en línea. Parecerá que funciona durante un breve período de tiempo, pero finalmente la plataforma eliminará el estilo de la tabla. Por tanto, planee con facilidad y mantenga las tablas sencillas. [Este es un sitio que facilita las tablas de Markdown](https://www.tablesgenerator.com/markdown_tables).

La [extensión docs Markdown para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) también facilita la generación de tablas si usa [Visual Studio Code (consulte a continuación)](#using-visual-studio-code) para editar la documentación.

### <a name="adding-images"></a>Agregar imágenes

Tendrá que cargar las imágenes en la carpeta "Mixed Reality-docs/Images" del repositorio y, a continuación, hacer referencia a ellas correctamente en el artículo. Las imágenes se mostrarán automáticamente a tamaño completo, lo que significa que si la imagen es grande, rellenará el ancho completo del artículo. Por lo tanto, se recomienda ajustar el tamaño de las imágenes antes de cargarlas. El ancho recomendado es de entre 600 y 700 píxeles, aunque debe ajustarse verticalmente o reducirse si es una captura de pantalla densa o una fracción de una captura de pantalla, respectivamente.

>[!IMPORTANT]
>Solo puede cargar imágenes en el repositorio bifurcado antes de la combinación. Por lo tanto, si planea agregar imágenes a un artículo, deberá [usar Visual Studio Code](#using-visual-studio-code) para agregar las imágenes a la carpeta "images" de la bifurcación en primer lugar o asegurarse de que ha realizado lo siguiente en un explorador Web:
>
>1. Se ha bifurcado el repositorio MicrosoftDocs/Mixed Reality.
>2. Editó el artículo en la bifurcación.
>3. Cargó las imágenes a las que hace referencia en el artículo en la carpeta "Mixed Reality-docs/Images" de la bifurcación.
>4. Se creó una **solicitud de incorporación** de cambios para fusionar mediante combinación la bifurcación en la rama "principal" de MicrosoftDocs/Mixed Reality.
>
>Para obtener información sobre cómo configurar su propio repositorio bifurcado, siga las instrucciones para [crear un nuevo artículo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Obtener una vista previa del trabajo

Mientras edita en GitHub a través de un explorador Web, puede hacer clic en la pestaña **vista previa** situada cerca de la parte superior de la página para obtener una vista previa del trabajo antes de confirmar. 

>[!NOTE]
>La vista previa de los cambios en review.docs.microsoft.com solo está disponible para los empleados de Microsoft

Empleados de Microsoft: una vez que las contribuciones se han combinado en la rama "principal", puede ver el aspecto que tendrá la documentación antes de que sea pública en https://review.docs.microsoft.com/windows/mixed-reality?branch=master (busque el artículo con la tabla de contenido de la columna izquierda).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Edición en el explorador frente a edición con un cliente de escritorio

La edición en el explorador es la forma más sencilla de realizar cambios rápidos; sin embargo, hay algunas desventajas:

- No obtiene la revisión ortográfica.
- No obtiene ninguna vinculación inteligente a otros artículos (tiene que escribir manualmente el nombre de archivo del artículo).
- Puede ser una molestia para cargar y hacer referencia a las imágenes.

Si prefiere no tratar estos problemas, es posible que prefiera usar un cliente de escritorio como [Visual Studio Code](https://code.visualstudio.com/) con un par de [extensiones útiles](#useful-extensions) para contribuir a la documentación.

## <a name="using-visual-studio-code"></a>Usar Visual Studio Code

Por los motivos mencionados [anteriormente](#editing-in-the-browser-vs-editing-with-a-desktop-client), es posible que prefiera usar un cliente de escritorio para editar la documentación en lugar de un explorador Web. Se recomienda el uso de [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configuración

Siga estos pasos para configurar Visual Studio Code para trabajar con este repositorio:

1. En un explorador Web:
    1. Instale [git para su PC](https://git-scm.com/downloads).
    2. Instale [Visual Studio Code](https://code.visualstudio.com/).
    3. [Bifurcación MicrosoftDocs/Mixed-Reality](#creating-a-new-article) si todavía no lo ha hecho.
    4. En la bifurcación, haga clic en **clonar o descargar** y copiar la dirección URL.
2. Cree un clon local de la bifurcación en Visual Studio Code:
    1. En el menú **Ver** , seleccione **paleta de comandos**.
    2. Escriba "git: Clone".
    3. Pegue la dirección URL que acaba de copiar.
    4. Elija dónde desea guardar el clon en su PC.
    5. Haga clic en **abrir repositorio** en el menú emergente.

### <a name="editing-documentation"></a>Editar documentación

Use el siguiente flujo de trabajo para realizar cambios en la documentación con Visual Studio Code:

>[!NOTE]
>Todas las instrucciones para [Editar](#editing-an-existing-article) y [crear](#creating-a-new-article) artículos, y los [aspectos básicos de la edición de Markdown](#markdown-basics), de lo anterior se aplican también cuando se usa Visual Studio Code.

1. Asegúrese de que la bifurcación clonada esté actualizada con el repositorio oficial.
   1. En un explorador Web, cree una solicitud de incorporación de cambios para sincronizar los cambios recientes de otros colaboradores en MicrosoftDocs/mixed-reality ' maestra ' en la bifurcación (Asegúrese de que la flecha señala el modo correcto).
      
      ![Sincronización de los cambios de MicrosoftDocs/Mixed-Reality en la bifurcación](images/sync_repos.PNG)
   2. En Visual Studio Code, haga clic en el botón sincronizar para sincronizar la bifurcación recién actualizada con el clon local.
      
      ![Haga clic en el botón sincronizar](images/sync_clone.png)
2. Cree o edite artículos en el repositorio clonado mediante Visual Studio Code.
   1. Edite uno o varios artículos (agregue imágenes a la carpeta "images" si es necesario).
   2. **Guarde** los cambios en el **Explorador**.
      
      ![Elija "guardar todo" en el explorador.](images/explorer_save.png)
   3. **Confirmar todos** los cambios en el **control de código fuente** (escribir mensaje de confirmación cuando se le solicite).
      
      ![Elegir "confirmar todo" en el control de código fuente](images/source_control_commit.png)
   4. Haga clic en el botón **sincronizar** para volver a sincronizar los cambios con el origen (la bifurcación en GitHub).
      
      ![Haga clic en el botón sincronizar](images/sync_back.png)
3. En un explorador Web, cree una solicitud de incorporación de cambios para sincronizar nuevos cambios en la bifurcación de nuevo en MicrosoftDocs/mixed-reality ' maestra ' (Asegúrese de que la flecha señala la manera correcta).

   ![Cree una solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensiones útiles

Las siguientes extensiones de Visual Studio Code son muy útiles al editar la documentación:

- La [extensión de Markdown de docs para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : use **Alt + M** para abrir un menú de opciones de creación de docs como:
   - Imágenes de búsqueda y de referencia que ha cargado.
   - Agregue formato como listas, tablas y llamadas específicas de docs como `>[!NOTE]`.
   - Buscar y hacer referencia a vínculos internos y marcadores (vínculos a secciones específicas de una página).
   - Los errores de formato se resaltan (mantenga el mouse sobre el error para obtener más información).
- [Corrector ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : las palabras mal escritas se subrayan; Haga clic con el botón derecho en una palabra mal escrita para cambiarla o guardarla en el diccionario.
