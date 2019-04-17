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
# <a name="in-app-purchases"></a>Compras desde la aplicación

Adquisición de la aplicación se admite en HoloLens, pero hay algún trabajo para configurarlas.

Para poder beneficiarse de la compra de aplicación en funcionalidad, debe:
* Crear un XAML [vista 2D](app-views.md) aparezca como una pizarra
* Cambiar a él para activar la selección de ubicación, lo que deja la vista envolvente
* Llamar a la API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Esta API se abrirá la ventana emergente del sistema operativo de Windows estándar que se muestra el nombre de la compra en la aplicación, descripción y precio. El usuario, a continuación, puede elegir las opciones de compra. Una vez completada la acción, la aplicación necesitará presentar la interfaz de usuario que permite al usuario volver a su [vista envolvente](app-views.md).

Para aplicaciones orientadas a en el escritorio Windows Mixed Reality inmersivos, no es necesario intercambiar manualmente a una vista XAML antes de llamar a la API RequestProductPurchaseAsync.
