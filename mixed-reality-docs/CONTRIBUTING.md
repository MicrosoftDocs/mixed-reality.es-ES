---
title: Instrucciones de colaboración
description: Cómo contribuir a la documentación de Windows Mixed Reality.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516220"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="c3f4f-103">Contribución a la documentación para desarrolladores de realidad mixta de Windows</span><span class="sxs-lookup"><span data-stu-id="c3f4f-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="c3f4f-104">Este es el [repositorio público de la documentación para desarrolladores de Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="c3f4f-105">Los artículos que cree o edite en este repositorio **serán visibles para el público.**</span><span class="sxs-lookup"><span data-stu-id="c3f4f-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="c3f4f-106">Los documentos de Windows Mixed Reality se encuentran ahora en la plataforma docs.microsoft.com, que usa el Markdown con tipo GitHub (con características Markdig).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="c3f4f-107">En esencia, el contenido que se edita en este repositorio se convierte en páginas con formato y estilizadas que https://docs.microsoft.com/windows/mixed-reality se muestran en.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="c3f4f-108">En esta página se describen los pasos básicos y las instrucciones para contribuir, así como vínculos a los conceptos básicos de Markdown.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="c3f4f-109">Gracias por su contribución.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c3f4f-110">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="c3f4f-110">Before you start</span></span>

<span data-ttu-id="c3f4f-111">Si aún no tiene una, deberá [crear una cuenta de github](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="c3f4f-112">Si es un empleado de Microsoft, vincule su cuenta de GitHub a su alias de Microsoft en el [portal de código abierto de Microsoft](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="c3f4f-113">Únase a las organizaciones **"Microsoft"** y **"MicrosoftDocs"** ).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="c3f4f-114">Al configurar la cuenta de GitHub, también se recomiendan estas precauciones de seguridad:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="c3f4f-115">Cree una [contraseña segura para la cuenta de github](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="c3f4f-116">Habilitar [la autenticación en dos fases](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="c3f4f-117">Guarde los [códigos de recuperación](https://github.com/settings/auth/recovery-codes) en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="c3f4f-118">Actualice la [configuración del perfil público](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="c3f4f-119">Establezca su nombre y considere la posibilidad de establecer el *correo electrónico público* para *no mostrar la dirección de correo electrónico*.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="c3f4f-120">Se recomienda cargar una imagen de perfil, ya que se mostrará una miniatura en las páginas de docs a las que contribuya.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="c3f4f-121">Si planea usar un flujo de trabajo de línea de comandos, considere la posibilidad de configurar el [Administrador de credenciales de Git para Windows de](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) modo que no tenga que escribir la contraseña cada vez que realice una contribución.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="c3f4f-122">Realizar estos pasos es importante, ya que el sistema de publicación está asociado a GitHub y se mostrará como autor o colaborador en cada artículo mediante el alias de GitHub.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="c3f4f-123">Edición de un artículo existente</span><span class="sxs-lookup"><span data-stu-id="c3f4f-123">Editing an existing article</span></span>

<span data-ttu-id="c3f4f-124">Use el siguiente flujo de trabajo para efectuar actualizaciones en *un artículo existente* a través de github en un explorador Web:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="c3f4f-125">Navegue hasta el artículo que desea editar en la carpeta "Mixed Reality-docs".</span><span class="sxs-lookup"><span data-stu-id="c3f4f-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="c3f4f-126">Seleccione el botón Editar (icono de lápiz) en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="c3f4f-127">Se bifurcará automáticamente una rama descartable de la rama "principal".</span><span class="sxs-lookup"><span data-stu-id="c3f4f-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Edite un artículo.](images/editpage.png)
3. <span data-ttu-id="c3f4f-129">Edite el contenido del artículo (consulte ["conceptos básicos de Markdown"](#markdown-basics) a continuación para obtener instrucciones).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="c3f4f-130">Actualice los metadatos como corresponda en la parte superior de cada artículo:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="c3f4f-131">Titulo Este es el título de la página que aparece en la pestaña del explorador cuando se está viendo el artículo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="c3f4f-132">Como se usa para SEO e indexación, no debe cambiar el título a menos que sea necesario (aunque esto es menos crítico antes de que la documentación sea pública).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="c3f4f-133">description: Escriba una breve descripción del contenido del artículo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="c3f4f-134">Esto ayuda en la SEO y la detección.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="c3f4f-135">frente Si es el propietario principal de la página, agregue aquí su alias de GitHub.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="c3f4f-136">MS. Author: Si es el propietario principal de la página, agregue aquí su alias de Microsoft (no es necesario @microsoft.com, solo el alias).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="c3f4f-137">MS. Date: Actualice la fecha Si va a agregar contenido principal a la página, pero no para correcciones como aclaración, formato, gramática o ortografía.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="c3f4f-138">palabra Palabras clave: ayuda en SEO (optimización del motor de búsqueda).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="c3f4f-139">Agregue palabras clave, separadas por una coma y un espacio, específicas de su artículo (pero sin puntuación después de la última palabra clave de la lista); no es necesario agregar palabras clave globales que se apliquen a todos los artículos, ya que se administran en otro lugar.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="c3f4f-140">Cuando haya terminado de editar el artículo, desplácese hacia abajo y haga clic en el botón **proponer cambio de archivo** .</span><span class="sxs-lookup"><span data-stu-id="c3f4f-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="c3f4f-141">En la página siguiente, haga clic en **crear solicitud de incorporación** de cambios para fusionar mediante combinación la rama creada automáticamente en ' maestra '.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="c3f4f-142">Repita los pasos anteriores para el siguiente artículo que desee editar.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="c3f4f-143">Creación de un nuevo artículo</span><span class="sxs-lookup"><span data-stu-id="c3f4f-143">Creating a new article</span></span>

<span data-ttu-id="c3f4f-144">Use el siguiente flujo de trabajo para *crear nuevos artículos* en el repositorio de documentación a través de github en un explorador Web:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="c3f4f-145">Cree una bifurcación desconectada de la rama "principal" de MicrosoftDocs/Mixed  reality (con el botón bifurcar en la parte superior derecha).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Bifurcar la bifurcación principal.](images/forkbranch.png)
2. <span data-ttu-id="c3f4f-147">En la carpeta "Mixed Reality-docs", haga clic en el botón **crear nuevo archivo** en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="c3f4f-148">Crear un nombre de página para el artículo (usar guiones en lugar de espacios y no usar signos de puntuación ni apóstrofos) y anexar ". MD"</span><span class="sxs-lookup"><span data-stu-id="c3f4f-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Asigne un nombre a la nueva página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="c3f4f-150">Asegúrese de crear el nuevo artículo desde la carpeta "Mixed Reality-docs".</span><span class="sxs-lookup"><span data-stu-id="c3f4f-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="c3f4f-151">Puede confirmarlo comprobando "/Mixed-Reality-docs/" en la nueva línea de nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="c3f4f-152">En la parte superior de la página nueva, agregue el siguiente bloque de metadatos:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="c3f4f-153">Rellene los campos de metadatos pertinentes según las instrucciones de la [sección anterior](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="c3f4f-154">Escriba el contenido del artículo con los [conceptos básicos de Markdown](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="c3f4f-155">Agregue una `## See also` sección en la parte inferior del artículo con vínculos a otros artículos relevantes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="c3f4f-156">Cuando termine, haga clic en **confirmar nuevo archivo**.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="c3f4f-157">Haga clic en **nueva solicitud de incorporación** de cambios y mezcle la rama ' maestra ' de la bifurcación en MicrosoftDocs/mixed-reality ' maestra ' (Asegúrese de que la flecha señala la manera correcta).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Cree una solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="c3f4f-159">Aspectos básicos de Markdown</span><span class="sxs-lookup"><span data-stu-id="c3f4f-159">Markdown basics</span></span>

<span data-ttu-id="c3f4f-160">Los siguientes recursos le ayudarán a aprender a editar la documentación con el lenguaje Markdown:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="c3f4f-161">Aspectos básicos de Markdown</span><span class="sxs-lookup"><span data-stu-id="c3f4f-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="c3f4f-162">Póster de referencia de Markdown a un vistazo</span><span class="sxs-lookup"><span data-stu-id="c3f4f-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="c3f4f-163">Recursos adicionales para escribir Markdown para docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="c3f4f-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="c3f4f-164">Agregar tablas</span><span class="sxs-lookup"><span data-stu-id="c3f4f-164">Adding tables</span></span>

<span data-ttu-id="c3f4f-165">Debido a la forma en que docs.microsoft.com las tablas de estilos, no tendrán bordes ni estilos personalizados, aunque pruebe CSS en línea.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="c3f4f-166">Parecerá que funciona durante un breve período de tiempo, pero finalmente la plataforma eliminará el estilo de la tabla.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="c3f4f-167">Por tanto, planee con facilidad y mantenga las tablas sencillas.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="c3f4f-168">[Este es un sitio que facilita las tablas de Markdown](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="c3f4f-169">La [extensión docs Markdown para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) también facilita la generación de tablas si usa [Visual Studio Code (consulte a continuación)](#using-visual-studio-code) para editar la documentación.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="c3f4f-170">Agregar imágenes</span><span class="sxs-lookup"><span data-stu-id="c3f4f-170">Adding images</span></span>

<span data-ttu-id="c3f4f-171">Tendrá que cargar las imágenes en la carpeta "Mixed Reality-docs/Images" del repositorio y, a continuación, hacer referencia a ellas correctamente en el artículo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="c3f4f-172">Las imágenes se mostrarán automáticamente a tamaño completo, lo que significa que si la imagen es grande, rellenará el ancho completo del artículo.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="c3f4f-173">Por lo tanto, se recomienda ajustar el tamaño de las imágenes antes de cargarlas.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="c3f4f-174">El ancho recomendado es de entre 600 y 700 píxeles, aunque debe ajustarse verticalmente o reducirse si es una captura de pantalla densa o una fracción de una captura de pantalla, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c3f4f-175">Solo puede cargar imágenes en el repositorio bifurcado antes de la combinación.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="c3f4f-176">Por lo tanto, si planea agregar imágenes a un artículo, deberá [usar Visual Studio Code](#using-visual-studio-code) para agregar las imágenes a la carpeta "images" de la bifurcación en primer lugar o asegurarse de que ha realizado lo siguiente en un explorador Web:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="c3f4f-177">Se ha bifurcado el repositorio MicrosoftDocs/Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="c3f4f-178">Editó el artículo en la bifurcación.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="c3f4f-179">Cargó las imágenes a las que hace referencia en el artículo en la carpeta "Mixed Reality-docs/Images" de la bifurcación.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="c3f4f-180">Se creó una **solicitud de incorporación** de cambios para fusionar mediante combinación la bifurcación en la rama "principal" de MicrosoftDocs/Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="c3f4f-181">Para obtener información sobre cómo configurar su propio repositorio bifurcado, siga las instrucciones para [crear un nuevo artículo](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="c3f4f-182">Obtener una vista previa del trabajo</span><span class="sxs-lookup"><span data-stu-id="c3f4f-182">Previewing your work</span></span>

<span data-ttu-id="c3f4f-183">Mientras edita en GitHub a través de un explorador Web, puede hacer clic en la pestaña **vista previa** situada cerca de la parte superior de la página para obtener una vista previa del trabajo antes de confirmar.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="c3f4f-184">La vista previa de los cambios en review.docs.microsoft.com solo está disponible para los empleados de Microsoft</span><span class="sxs-lookup"><span data-stu-id="c3f4f-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="c3f4f-185">Empleados de Microsoft: una vez que las contribuciones se han combinado en la rama "principal", puede ver el aspecto que tendrá la documentación antes de https://review.docs.microsoft.com/windows/mixed-reality?branch=master que sea pública (busque el artículo mediante la tabla de contenido de la columna izquierda).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="c3f4f-186">Edición en el explorador frente a edición con un cliente de escritorio</span><span class="sxs-lookup"><span data-stu-id="c3f4f-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="c3f4f-187">La edición en el explorador es la forma más sencilla de realizar cambios rápidos; sin embargo, hay algunas desventajas:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="c3f4f-188">No obtiene la revisión ortográfica.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-188">You don't get spell-check.</span></span>
- <span data-ttu-id="c3f4f-189">No obtiene ninguna vinculación inteligente a otros artículos (tiene que escribir manualmente el nombre de archivo del artículo).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="c3f4f-190">Puede ser una molestia para cargar y hacer referencia a las imágenes.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="c3f4f-191">Si prefiere no tratar estos problemas, es posible que prefiera usar un cliente de escritorio como [Visual Studio Code](https://code.visualstudio.com/) con un par de [extensiones útiles](#useful-extensions) para contribuir a la documentación.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="c3f4f-192">Usar Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c3f4f-192">Using Visual Studio Code</span></span>

<span data-ttu-id="c3f4f-193">Por los motivos mencionados [anteriormente](#editing-in-the-browser-vs-editing-with-a-desktop-client), es posible que prefiera usar un cliente de escritorio para editar la documentación en lugar de un explorador Web.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="c3f4f-194">Se recomienda el uso de [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="c3f4f-195">Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="c3f4f-195">Setup</span></span>

<span data-ttu-id="c3f4f-196">Siga estos pasos para configurar Visual Studio Code para trabajar con este repositorio:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="c3f4f-197">En un explorador Web:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-197">In a web browser:</span></span>
    1. <span data-ttu-id="c3f4f-198">Instale [git para su PC](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="c3f4f-199">Instale [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="c3f4f-200">[Bifurcación MicrosoftDocs/Mixed-Reality](#creating-a-new-article) si todavía no lo ha hecho.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="c3f4f-201">En la bifurcación, haga clic en **clonar o descargar** y copiar la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="c3f4f-202">Cree un clon local de la bifurcación en Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="c3f4f-203">En el menú **Ver** , seleccione **paleta de comandos**.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="c3f4f-204">Escriba "git: Clone".</span><span class="sxs-lookup"><span data-stu-id="c3f4f-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="c3f4f-205">Pegue la dirección URL que acaba de copiar.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="c3f4f-206">Elija dónde desea guardar el clon en su PC.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="c3f4f-207">Haga clic en **abrir repositorio** en el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="c3f4f-208">Editar documentación</span><span class="sxs-lookup"><span data-stu-id="c3f4f-208">Editing documentation</span></span>

<span data-ttu-id="c3f4f-209">Use el siguiente flujo de trabajo para realizar cambios en la documentación con Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="c3f4f-210">Todas las instrucciones para [Editar](#editing-an-existing-article) y [crear](#creating-a-new-article) artículos, y los [aspectos básicos de la edición de Markdown](#markdown-basics), de lo anterior se aplican también cuando se usa Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="c3f4f-211">Asegúrese de que la bifurcación clonada esté actualizada con el repositorio oficial.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="c3f4f-212">En un explorador Web, cree una solicitud de incorporación de cambios para sincronizar los cambios recientes de otros colaboradores en MicrosoftDocs/mixed-reality ' maestra ' en la bifurcación (Asegúrese de que la flecha señala el modo correcto).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Sincronización de los cambios de MicrosoftDocs/Mixed-Reality en la bifurcación](images/sync_repos.PNG)
   2. <span data-ttu-id="c3f4f-214">En Visual Studio Code, haga clic en el botón sincronizar para sincronizar la bifurcación recién actualizada con el clon local.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Haga clic en el botón sincronizar](images/sync_clone.png)
2. <span data-ttu-id="c3f4f-216">Cree o edite artículos en el repositorio clonado mediante Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="c3f4f-217">Edite uno o varios artículos (agregue imágenes a la carpeta "images" si es necesario).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="c3f4f-218">**Guarde** los cambios en el **Explorador**.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-218">**Save** changes in **Explorer**.</span></span>
      
      ![Elija "guardar todo" en el explorador.](images/explorer_save.png)
   3. <span data-ttu-id="c3f4f-220">**Confirmar todos** los cambios en el **control de código fuente** (escribir mensaje de confirmación cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Elegir "confirmar todo" en el control de código fuente](images/source_control_commit.png)
   4. <span data-ttu-id="c3f4f-222">Haga clic  en el botón sincronizar para volver a sincronizar los cambios con el origen (la bifurcación en GitHub).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Haga clic en el botón sincronizar](images/sync_back.png)
3. <span data-ttu-id="c3f4f-224">En un explorador Web, cree una solicitud de incorporación de cambios para sincronizar nuevos cambios en la bifurcación de nuevo en MicrosoftDocs/mixed-reality ' maestra ' (Asegúrese de que la flecha señala la manera correcta).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Cree una solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="c3f4f-226">Extensiones útiles</span><span class="sxs-lookup"><span data-stu-id="c3f4f-226">Useful extensions</span></span>

<span data-ttu-id="c3f4f-227">Las siguientes extensiones de Visual Studio Code son muy útiles al editar la documentación:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="c3f4f-228">La [extensión de Markdown de docs para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : use **Alt + M** para abrir un menú de opciones de creación de docs como:</span><span class="sxs-lookup"><span data-stu-id="c3f4f-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="c3f4f-229">Imágenes de búsqueda y de referencia que ha cargado.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="c3f4f-230">Agregue formato como listas, tablas y llamadas específicas de documentos como `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="c3f4f-231">Buscar y hacer referencia a vínculos internos y marcadores (vínculos a secciones específicas de una página).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="c3f4f-232">Los errores de formato se resaltan (mantenga el mouse sobre el error para obtener más información).</span><span class="sxs-lookup"><span data-stu-id="c3f4f-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="c3f4f-233">[Corrector ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : las palabras mal escritas se subrayan; Haga clic con el botón derecho en una palabra mal escrita para cambiarla o guardarla en el diccionario.</span><span class="sxs-lookup"><span data-stu-id="c3f4f-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
