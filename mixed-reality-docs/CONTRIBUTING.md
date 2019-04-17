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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="db84d-103">Colaborar en la documentación para desarrolladores de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="db84d-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="db84d-104">Bienvenido a la [repositorio público de documentación para desarrolladores de Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="db84d-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="db84d-105">Los artículos se crean o editan en este repositorio **serán visibles para el público.**</span><span class="sxs-lookup"><span data-stu-id="db84d-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="db84d-106">Los documentos de Windows Mixed Reality ahora están en la plataforma de docs.microsoft.com, que usa el marcado característico de GitHub (con características Markdig).</span><span class="sxs-lookup"><span data-stu-id="db84d-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="db84d-107">En esencia, activar en páginas estilizadas y con formato que se muestran en el contenido que se edita en este repositorio https://docs.microsoft.com/windows/mixed-reality.</span><span class="sxs-lookup"><span data-stu-id="db84d-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="db84d-108">Esta página trata los pasos básicos y directrices para contribuir, así como vínculos a los conceptos básicos de Markdown.</span><span class="sxs-lookup"><span data-stu-id="db84d-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="db84d-109">Le agradecemos su contribución.</span><span class="sxs-lookup"><span data-stu-id="db84d-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="db84d-110">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="db84d-110">Before you start</span></span>

<span data-ttu-id="db84d-111">Si aún no tiene uno, deberá [crear una cuenta de GitHub](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="db84d-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="db84d-112">Si es empleado de Microsoft, vincular su cuenta de GitHub para el alias de Microsoft en la [portal de código abierto de Microsoft](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="db84d-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="db84d-113">Únase a la **"Microsoft"** y **"MicrosoftDocs"** organizaciones).</span><span class="sxs-lookup"><span data-stu-id="db84d-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="db84d-114">Al configurar la cuenta de GitHub, también se recomienda que estas precauciones de seguridad:</span><span class="sxs-lookup"><span data-stu-id="db84d-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="db84d-115">Crear un [contraseña segura para la cuenta de Github](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="db84d-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="db84d-116">Habilitar [autenticación en dos fases](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="db84d-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="db84d-117">Guarde su [códigos de recuperación](https://github.com/settings/auth/recovery-codes) en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="db84d-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="db84d-118">Actualización de su [configuración del perfil público](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="db84d-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="db84d-119">Configure su nombre y considere la posibilidad de su *correo electrónico público* a *no mostrar mi dirección de correo electrónico*.</span><span class="sxs-lookup"><span data-stu-id="db84d-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="db84d-120">Se recomienda cargar una imagen de perfil, tal como se mostrará una miniatura en páginas de docs a las que contribuya.</span><span class="sxs-lookup"><span data-stu-id="db84d-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="db84d-121">Si tiene previsto usar un flujo de trabajo de línea de comandos, considere la posibilidad de configurar [Git Credential Manager para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) para que no tengan que escribir la contraseña cada vez que realizar una contribución.</span><span class="sxs-lookup"><span data-stu-id="db84d-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="db84d-122">Si realiza estos pasos es importante, como el sistema de publicación está asociado a GitHub y se mostrarán como autor o colaborador en cada artículo mediante su alias de GitHub.</span><span class="sxs-lookup"><span data-stu-id="db84d-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="db84d-123">Edición de un artículo existente</span><span class="sxs-lookup"><span data-stu-id="db84d-123">Editing an existing article</span></span>

<span data-ttu-id="db84d-124">Use el siguiente flujo de trabajo para realizar actualizaciones para *un artículo existente* a través de GitHub en un explorador web:</span><span class="sxs-lookup"><span data-stu-id="db84d-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="db84d-125">Vaya al artículo que desea editar en la carpeta "mixto de realidad-docs".</span><span class="sxs-lookup"><span data-stu-id="db84d-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="db84d-126">En la esquina superior derecha, seleccione el botón Editar (icono de lápiz).</span><span class="sxs-lookup"><span data-stu-id="db84d-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="db84d-127">Esto automáticamente bifurcará descartable bifurcación de la rama "principal".</span><span class="sxs-lookup"><span data-stu-id="db84d-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Editar un artículo.](images/editpage.png)
3. <span data-ttu-id="db84d-129">Editar el contenido del artículo (consulte ["Aspectos básicos de Markdown"](#markdown-basics) a continuación para obtener instrucciones).</span><span class="sxs-lookup"><span data-stu-id="db84d-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="db84d-130">Actualizar los metadatos como importante en la parte superior de cada artículo:</span><span class="sxs-lookup"><span data-stu-id="db84d-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="db84d-131">title: Este es el título de página que aparece en la pestaña del explorador cuando se está viendo el artículo.</span><span class="sxs-lookup"><span data-stu-id="db84d-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="db84d-132">Puesto que se usa para la indexación y la SEO, no debería cambiar el título a menos que es necesario (aunque esto es menos crítica antes de que quede pública documentación).</span><span class="sxs-lookup"><span data-stu-id="db84d-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="db84d-133">description: Escriba una breve descripción del contenido del artículo.</span><span class="sxs-lookup"><span data-stu-id="db84d-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="db84d-134">Esto ayuda a SEO y detección.</span><span class="sxs-lookup"><span data-stu-id="db84d-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="db84d-135">Autor: Si es el propietario de la página principal, agregue aquí su alias de GitHub.</span><span class="sxs-lookup"><span data-stu-id="db84d-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="db84d-136">ms.author: Si es el propietario de la página principal, agregue su alias aquí de Microsoft (no es necesario @microsoft.com, sólo con el alias).</span><span class="sxs-lookup"><span data-stu-id="db84d-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="db84d-137">ms.date: Si va a agregar contenido importante a la página, pero no para las revisiones como aclaración, formato, gramática, o de ortografía, actualice la fecha.</span><span class="sxs-lookup"><span data-stu-id="db84d-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="db84d-138">palabras clave: Palabras clave ayudan a SEO (optimización de motor de búsqueda).</span><span class="sxs-lookup"><span data-stu-id="db84d-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="db84d-139">Agregar palabras clave, separadas por una coma y un espacio, que son específicas de su artículo (pero sin puntuación después de la última palabra clave en la lista); no es necesario agregar las palabras clave globales que se aplican a todos los artículos, como los que se administran en otro lugar.</span><span class="sxs-lookup"><span data-stu-id="db84d-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="db84d-140">Cuando haya completado las modificaciones del artículo, desplácese hacia abajo y haga clic en el **proponer cambio de archivo** botón.</span><span class="sxs-lookup"><span data-stu-id="db84d-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="db84d-141">En la siguiente página, haga clic en **crear solicitud de incorporación de cambios** para combinar la rama creada automáticamente en 'master'.</span><span class="sxs-lookup"><span data-stu-id="db84d-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="db84d-142">Repita los pasos anteriores para el siguiente artículo que desea editar.</span><span class="sxs-lookup"><span data-stu-id="db84d-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="db84d-143">Crear un nuevo artículo</span><span class="sxs-lookup"><span data-stu-id="db84d-143">Creating a new article</span></span>

<span data-ttu-id="db84d-144">Use el siguiente flujo de trabajo *crear nuevos artículos* en el repositorio de documentación a través de GitHub en un explorador web:</span><span class="sxs-lookup"><span data-stu-id="db84d-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="db84d-145">Crear una bifurcación de la rama "principal" MicrosoftDocs/realidad mixta (mediante el **bifurcación** botón en la esquina superior derecha).</span><span class="sxs-lookup"><span data-stu-id="db84d-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Bifurcación de la rama maestra.](images/forkbranch.png)
2. <span data-ttu-id="db84d-147">En la carpeta "mixto de realidad-docs", haga clic en el **crear nuevo archivo** botón en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="db84d-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="db84d-148">Crear un nombre de página para el artículo (utilice guiones en lugar de espacios y no use signos de puntuación o apóstrofos) y anexar "MD"</span><span class="sxs-lookup"><span data-stu-id="db84d-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Nombre de la nueva página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="db84d-150">Asegúrese de que crear el nuevo artículo desde dentro de la carpeta "mixto de realidad-docs".</span><span class="sxs-lookup"><span data-stu-id="db84d-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="db84d-151">Puede confirmarlo comprobando "/ docs de realidad mixta /" en la línea de nombre de archivo nuevo.</span><span class="sxs-lookup"><span data-stu-id="db84d-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="db84d-152">En la parte superior de la nueva página, agregue el siguiente bloque de metadatos:</span><span class="sxs-lookup"><span data-stu-id="db84d-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="db84d-153">Rellene los campos de metadatos relevantes por las instrucciones de la [sección anterior](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="db84d-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="db84d-154">Artículo de escritura contenido mediante [conceptos básicos de Markdown](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="db84d-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="db84d-155">Agregar un `## See also` en la parte inferior del artículo con vínculos a artículos relevantes.</span><span class="sxs-lookup"><span data-stu-id="db84d-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="db84d-156">Cuando termine, haga clic en **confirmación nuevo archivo**.</span><span class="sxs-lookup"><span data-stu-id="db84d-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="db84d-157">Haga clic en **nueva solicitud de incorporación de cambios** y combinar rama "principal" de la bifurcación en MicrosoftDocs/realidad mixta 'master' (asegúrese de que la flecha señala la manera correcta).</span><span class="sxs-lookup"><span data-stu-id="db84d-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Crear solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/realidad mixta](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="db84d-159">Conceptos básicos de markdown</span><span class="sxs-lookup"><span data-stu-id="db84d-159">Markdown basics</span></span>

<span data-ttu-id="db84d-160">Los siguientes recursos le ayudarán a obtener información sobre cómo editar la documentación mediante el lenguaje de Markdown:</span><span class="sxs-lookup"><span data-stu-id="db84d-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="db84d-161">Conceptos básicos de markdown</span><span class="sxs-lookup"><span data-stu-id="db84d-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="db84d-162">Póster de referencia de markdown de instantánea</span><span class="sxs-lookup"><span data-stu-id="db84d-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="db84d-163">Recursos adicionales para la escritura de Markdown para docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="db84d-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="db84d-164">Agregar tablas</span><span class="sxs-lookup"><span data-stu-id="db84d-164">Adding tables</span></span>

<span data-ttu-id="db84d-165">Debido a las tablas de los estilos de docs.microsoft.com de forma, no tienen bordes o estilos personalizados, incluso si se trata de CSS en línea.</span><span class="sxs-lookup"><span data-stu-id="db84d-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="db84d-166">Parece que funcionan durante un breve período de tiempo, pero finalmente la plataforma eliminará el estilo fuera de la tabla.</span><span class="sxs-lookup"><span data-stu-id="db84d-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="db84d-167">Por lo tanto, planee con antelación y simplificar las tablas.</span><span class="sxs-lookup"><span data-stu-id="db84d-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="db84d-168">[Este es un sitio que facilita las tablas de Markdown](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="db84d-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="db84d-169">El [extensión Docs Markdown para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) también hace que la tabla generación fácil si usa [Visual Studio Code (ver abajo)](#using-visual-studio-code) para editar la documentación.</span><span class="sxs-lookup"><span data-stu-id="db84d-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="db84d-170">Adición de imágenes</span><span class="sxs-lookup"><span data-stu-id="db84d-170">Adding images</span></span>

<span data-ttu-id="db84d-171">Deberá cargar sus imágenes a la carpeta "mixto-realidad-docs/images" en el repositorio y, a continuación, hacer referencia a ellos correctamente en el artículo.</span><span class="sxs-lookup"><span data-stu-id="db84d-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="db84d-172">Las imágenes se mostrarán automáticamente en tamaño completo, lo que significa que si la imagen es grande, rellenará todo el ancho del artículo.</span><span class="sxs-lookup"><span data-stu-id="db84d-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="db84d-173">Por lo tanto, se recomienda ajustar previamente el tamaño de las imágenes antes de cargarlos.</span><span class="sxs-lookup"><span data-stu-id="db84d-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="db84d-174">El ancho recomendado es de 600 a 700 píxeles, aunque debe dimensionar o reducir verticalmente si es una captura de pantalla con gran densidad o una fracción de una captura de pantalla, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="db84d-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="db84d-175">Solo puede cargar imágenes en el repositorio bifurcado antes de la mezcla.</span><span class="sxs-lookup"><span data-stu-id="db84d-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="db84d-176">Por lo tanto, si tiene previsto agregar imágenes a un artículo, deberá [usar Visual Studio Code](#using-visual-studio-code) para agregar las imágenes a la carpeta "images" de la bifurcación primero o asegúrese de que ha hecho lo siguiente en un explorador web:</span><span class="sxs-lookup"><span data-stu-id="db84d-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="db84d-177">Bifurcado el repositorio MicrosoftDocs/realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="db84d-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="db84d-178">Puede editar el artículo en la bifurcación.</span><span class="sxs-lookup"><span data-stu-id="db84d-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="db84d-179">Cargar las imágenes que se hace referencia en el artículo a la carpeta "mixto-realidad-docs/images" en la bifurcación.</span><span class="sxs-lookup"><span data-stu-id="db84d-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="db84d-180">Crea un **solicitud de extracción** para combinar la bifurcación en la rama "principal" MicrosoftDocs/realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="db84d-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="db84d-181">Para obtener información sobre cómo configurar su propio repositorio bifurcado, siga las instrucciones para [crear un nuevo artículo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="db84d-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="db84d-182">Vista previa de su trabajo</span><span class="sxs-lookup"><span data-stu-id="db84d-182">Previewing your work</span></span>

<span data-ttu-id="db84d-183">Mientras se edita en GitHub a través de un explorador web, puede hacer clic en el **Preview** ficha cerca de la parte superior de la página para obtener una vista previa de su trabajo antes de confirmar.</span><span class="sxs-lookup"><span data-stu-id="db84d-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="db84d-184">Vista previa de los cambios en review.docs.microsoft.com solo está disponible para los empleados de Microsoft</span><span class="sxs-lookup"><span data-stu-id="db84d-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="db84d-185">Los empleados de Microsoft: una vez que se han combinado las contribuciones en la rama "principal", puede ver el aspecto de la documentación antes de enviarlos pública en https://review.docs.microsoft.com/windows/mixed-reality?branch=master (encontrar su artículo con la tabla de contenido de la columna izquierda).</span><span class="sxs-lookup"><span data-stu-id="db84d-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="db84d-186">Edición en el explorador frente a edición con un cliente de escritorio</span><span class="sxs-lookup"><span data-stu-id="db84d-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="db84d-187">La edición en el explorador es la manera más fácil realizar cambios rápidos, sin embargo, hay algunas desventajas:</span><span class="sxs-lookup"><span data-stu-id="db84d-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="db84d-188">No obtendrá el corrector ortográfico.</span><span class="sxs-lookup"><span data-stu-id="db84d-188">You don't get spell-check.</span></span>
- <span data-ttu-id="db84d-189">No obtendrá ninguna vinculación inteligente a otros artículos (tendrá que escribir manualmente el nombre de archivo del artículo).</span><span class="sxs-lookup"><span data-stu-id="db84d-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="db84d-190">Puede ser una molestia para cargar y hacer referencia a las imágenes.</span><span class="sxs-lookup"><span data-stu-id="db84d-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="db84d-191">Si en su lugar podría no tratar con estos problemas, es preferible usar un cliente de escritorio como [Visual Studio Code](https://code.visualstudio.com/) con un par [extensiones útiles](#useful-extensions) para contribuir a la documentación.</span><span class="sxs-lookup"><span data-stu-id="db84d-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="db84d-192">Con Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="db84d-192">Using Visual Studio Code</span></span>

<span data-ttu-id="db84d-193">Por motivos de la lista [anteriormente](#editing-in-the-browser-vs-editing-with-a-desktop-client), quizás prefiera usar un cliente de escritorio para editar la documentación en lugar de un explorador web.</span><span class="sxs-lookup"><span data-stu-id="db84d-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="db84d-194">Se recomienda usar [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="db84d-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="db84d-195">Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="db84d-195">Setup</span></span>

<span data-ttu-id="db84d-196">Siga estos pasos para configurar el código de Visual Studio para trabajar con este repositorio:</span><span class="sxs-lookup"><span data-stu-id="db84d-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="db84d-197">En un explorador web:</span><span class="sxs-lookup"><span data-stu-id="db84d-197">In a web browser:</span></span>
    1. <span data-ttu-id="db84d-198">Instalar [Git para su PC](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="db84d-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="db84d-199">Instalar [código de Visual Studio](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="db84d-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="db84d-200">[Bifurcar MicrosoftDocs/realidad mixta](#creating-a-new-article) si no lo ha hecho ya.</span><span class="sxs-lookup"><span data-stu-id="db84d-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="db84d-201">En la bifurcación, haga clic en **clonar o descargar** y copie la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="db84d-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="db84d-202">Crear un clon local de la bifurcación en Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="db84d-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="db84d-203">Desde el **vista** menú, seleccione **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="db84d-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="db84d-204">Tipo "Git:Clone".</span><span class="sxs-lookup"><span data-stu-id="db84d-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="db84d-205">Pegue la dirección URL que acaba de copiar.</span><span class="sxs-lookup"><span data-stu-id="db84d-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="db84d-206">Elija dónde desea guardar el clon en su PC.</span><span class="sxs-lookup"><span data-stu-id="db84d-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="db84d-207">Haga clic en **repositorio abierto** en el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="db84d-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="db84d-208">Edición de la documentación</span><span class="sxs-lookup"><span data-stu-id="db84d-208">Editing documentation</span></span>

<span data-ttu-id="db84d-209">Use el siguiente flujo de trabajo para realizar cambios en la documentación de Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="db84d-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="db84d-210">Todas las instrucciones para [edición](#editing-an-existing-article) y [crear](#creating-a-new-article) artículos y el [aspectos básicos de la edición de Markdown](#markdown-basics), desde arriba se aplica cuando se usa Visual Studio Code también.</span><span class="sxs-lookup"><span data-stu-id="db84d-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="db84d-211">Asegúrese de que la bifurcación clonada está actualizada con el repositorio oficial.</span><span class="sxs-lookup"><span data-stu-id="db84d-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="db84d-212">En un explorador web, cree una solicitud de incorporación de cambios para sincronizar los cambios recientes de otros colaboradores en MicrosoftDocs/realidad mixta 'master' en la bifurcación (asegúrese de que la flecha señala la manera correcta).</span><span class="sxs-lookup"><span data-stu-id="db84d-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Sincronizar los cambios de MicrosoftDocs/realidad mixta en la bifurcación](images/sync_repos.PNG)
   2. <span data-ttu-id="db84d-214">En Visual Studio Code, haga clic en el botón de sincronización para sincronizar la bifurcación recién actualizada al clon local.</span><span class="sxs-lookup"><span data-stu-id="db84d-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Haga clic en el botón Sincronizar](images/sync_clone.png)
2. <span data-ttu-id="db84d-216">Cree o edite artículos en el repositorio clonado mediante Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="db84d-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="db84d-217">Editar uno o más artículos (agregar imágenes a la carpeta "images" si es necesario).</span><span class="sxs-lookup"><span data-stu-id="db84d-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="db84d-218">**Guardar** cambia en **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="db84d-218">**Save** changes in **Explorer**.</span></span>
      
      ![Elija "Guardar todo" en el explorador](images/explorer_save.png)
   3. <span data-ttu-id="db84d-220">**Confirmar todo** cambia en **Control de código fuente** (Escribir mensaje de confirmación cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="db84d-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Elija "Confirmar todo" en el Control de código fuente](images/source_control_commit.png)
   4. <span data-ttu-id="db84d-222">Haga clic en el **sincronización** botón para sincronizar los cambios de nuevo al origen (la bifurcación en GitHub).</span><span class="sxs-lookup"><span data-stu-id="db84d-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Haga clic en el botón Sincronizar](images/sync_back.png)
3. <span data-ttu-id="db84d-224">En un explorador web, cree una solicitud de incorporación de cambios para sincronizar los cambios nuevo en la bifurcación a MicrosoftDocs/realidad mixta 'master' (asegúrese de que la flecha señala la manera correcta).</span><span class="sxs-lookup"><span data-stu-id="db84d-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Crear solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/realidad mixta](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="db84d-226">Extensiones útiles</span><span class="sxs-lookup"><span data-stu-id="db84d-226">Useful extensions</span></span>

<span data-ttu-id="db84d-227">Las siguientes extensiones de Visual Studio Code son muy útiles cuando se edita la documentación:</span><span class="sxs-lookup"><span data-stu-id="db84d-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="db84d-228">[Extensión docs Markdown para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -uso **Alt + M** para que aparezca un menú de opciones, como de creación de docs:</span><span class="sxs-lookup"><span data-stu-id="db84d-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="db84d-229">Búsqueda y referencia de imágenes que ha cargado.</span><span class="sxs-lookup"><span data-stu-id="db84d-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="db84d-230">Agregar formato, como listas, tablas y leyendas específico de documentos como `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="db84d-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="db84d-231">Buscar y hacer referencia a vínculos internos y los marcadores (vínculos a secciones específicas dentro de una página).</span><span class="sxs-lookup"><span data-stu-id="db84d-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="db84d-232">Se resaltan los errores de formato (mantenga el mouse sobre el error para obtener más información).</span><span class="sxs-lookup"><span data-stu-id="db84d-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="db84d-233">[Corrector ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -aparecerá subrayadas; haga doble clic en una palabra mal escrita para cambiarla o guardarlo en el diccionario de palabras mal escritas.</span><span class="sxs-lookup"><span data-stu-id="db84d-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
