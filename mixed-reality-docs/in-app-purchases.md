---
title: Compras desde la aplicación
description: Las compras desde la aplicación se admiten en aplicaciones de realidad mixta, pero hay algún trabajo para configurarlas.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: compras desde la aplicación, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515292"
---
# <a name="in-app-purchases"></a><span data-ttu-id="7b269-104">Compras desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="7b269-104">In-app purchases</span></span>

<span data-ttu-id="7b269-105">Las compras desde la aplicación se admiten en HoloLens, pero hay algún trabajo para configurarlas.</span><span class="sxs-lookup"><span data-stu-id="7b269-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="7b269-106">Para aprovechar la funcionalidad de compra de la aplicación, debe:</span><span class="sxs-lookup"><span data-stu-id="7b269-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="7b269-107">Crear una [vista 2D](app-views.md) de XAML para que aparezca como una pizarra</span><span class="sxs-lookup"><span data-stu-id="7b269-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="7b269-108">Cambiar a él para activar la selección de ubicación, que deja la vista envolvente</span><span class="sxs-lookup"><span data-stu-id="7b269-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="7b269-109">Llame a la API: Await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="7b269-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="7b269-110">Esta API abrirá el menú contextual de sistema operativo Windows que muestra el nombre, la descripción y el precio de la compra desde la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7b269-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="7b269-111">El usuario puede elegir opciones de compra.</span><span class="sxs-lookup"><span data-stu-id="7b269-111">The user can then choose purchase options.</span></span> <span data-ttu-id="7b269-112">Una vez completada la acción, la aplicación necesitará presentar una interfaz de usuario que permita al usuario cambiar a su [vista envolvente](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="7b269-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="7b269-113">En el caso de las aplicaciones destinadas a auriculares con Windows Mixed Reality en el escritorio, no es necesario cambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="7b269-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
