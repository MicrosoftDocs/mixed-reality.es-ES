---
title: Compras desde la aplicación
description: Adquisición de la aplicación se admite en aplicaciones de realidad mixta, pero hay algún trabajo para configurarlas.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: adquisición de la aplicación, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602878"
---
# <a name="in-app-purchases"></a><span data-ttu-id="9179a-104">Compras desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="9179a-104">In-app purchases</span></span>

<span data-ttu-id="9179a-105">Adquisición de la aplicación se admite en HoloLens, pero hay algún trabajo para configurarlas.</span><span class="sxs-lookup"><span data-stu-id="9179a-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="9179a-106">Para poder beneficiarse de la compra de aplicación en funcionalidad, debe:</span><span class="sxs-lookup"><span data-stu-id="9179a-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="9179a-107">Crear un XAML [vista 2D](app-views.md) aparezca como una pizarra</span><span class="sxs-lookup"><span data-stu-id="9179a-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="9179a-108">Cambiar a él para activar la selección de ubicación, lo que deja la vista envolvente</span><span class="sxs-lookup"><span data-stu-id="9179a-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="9179a-109">Llamar a la API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="9179a-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="9179a-110">Esta API se abrirá la ventana emergente del sistema operativo de Windows estándar que se muestra el nombre de la compra en la aplicación, descripción y precio.</span><span class="sxs-lookup"><span data-stu-id="9179a-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="9179a-111">El usuario, a continuación, puede elegir las opciones de compra.</span><span class="sxs-lookup"><span data-stu-id="9179a-111">The user can then choose purchase options.</span></span> <span data-ttu-id="9179a-112">Una vez completada la acción, la aplicación necesitará presentar la interfaz de usuario que permite al usuario volver a su [vista envolvente](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="9179a-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="9179a-113">Para aplicaciones orientadas a en el escritorio Windows Mixed Reality inmersivos, no es necesario intercambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.</span><span class="sxs-lookup"><span data-stu-id="9179a-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
