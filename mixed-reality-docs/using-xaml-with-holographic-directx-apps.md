---
title: Uso de XAML con aplicaciones de DirectX holográficas
description: Explica el impacto de cambiar entre las vistas XAML 2D y las vistas de envolvente en la aplicación DirectX y cómo hacer un uso eficaz de una vista XAML y una vista envolvente.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, UWP, administración de vistas de aplicaciones, XAML, teclado, tutorial, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548700"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso de XAML con aplicaciones de DirectX holográficas

En este tema se explica el impacto del cambio entre las [vistas XAML 2D y las vistas de envolvente](app-views.md) en la aplicación DirectX y cómo hacer un uso eficaz de una vista XAML y una vista envolvente.

## <a name="xaml-view-switching-overview"></a>Información general sobre el cambio de vista XAML

En HoloLens, una aplicación en general que puede mostrar más adelante una vista XAML 2D debe inicializar esa vista XAML primero y cambiar inmediatamente a una vista envolvente desde allí. Esto significa que XAML se cargará antes de que la aplicación pueda hacer nada. Como resultado, habrá un pequeño aumento en el tiempo de inicio y XAML continuará ocupando espacio de memoria en el proceso de la aplicación mientras se encuentra en segundo plano. la cantidad de retraso de inicio y el uso de memoria depende de lo que hace la aplicación con XAML antes de cambiar a la vista nativa. Si no hace nada en su código XAML, inicie el código al principio, excepto iniciar la vista envolvente, el impacto debe ser menor. Además, dado que la representación holográfica se realiza directamente en la vista envolvente, se evitarán las restricciones relacionadas con XAML en esa representación.

Tenga en cuenta que los recuentos de uso de memoria para CPU y GPU. Direct3D 11 es capaz de intercambiar memoria de gráficos virtuales, pero es posible que no pueda intercambiar algunos o todos los recursos de GPU de XAML, y puede haber un impacto apreciable en el rendimiento. En cualquier caso, si no se cargan las características de XAML que no necesite, dejará más espacio para la aplicación y proporcionará una mejor experiencia.

## <a name="xaml-view-switching-workflow"></a>Flujo de trabajo de cambio de vista XAML

El flujo de trabajo de una aplicación que va directamente desde XAML al modo inmersivo es como el siguiente:
* La aplicación se inicia en la vista XAML 2D.
* La secuencia de inicio de XAML de la aplicación detecta si el sistema actual admite la representación holográfica:
* Si es así, la aplicación crea la vista envolvente y la pone en primer plano de forma inmediata. La carga de XAML se omite para cualquier elemento que no sea necesario en dispositivos de Windows Mixed Reality, incluidas las clases de representación y la carga de recursos en la vista XAML. Si la aplicación usa XAML para la entrada de teclado, la página de entrada se debe crear.
* Si no es así, la vista XAML puede continuar con la empresa como de costumbre.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Sugerencia para representar gráficos en ambas vistas

Si la aplicación necesita implementar una cantidad de representación en DirectX para la vista XAML en Windows Mixed Reality, la mejor opción es crear un representador que pueda funcionar con ambas vistas. El representador debe ser una instancia a la que se pueda tener acceso desde ambas vistas y debe poder cambiar entre la representación 2D y holográfica. De esta forma, los recursos de GPU solo se cargan una vez: Esto reduce los tiempos de carga, el impacto en la memoria y la cantidad de recursos que se van a intercambiar al cambiar de vista.
