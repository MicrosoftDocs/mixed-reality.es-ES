---
title: Uso de XAML con aplicaciones de DirectX holográficas
description: Explica el impacto del cambio entre 2D vistas XAML y envolventes en la aplicación de DirectX y cómo hacer un uso eficaz de una vista XAML y la vista envolvente.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: aplicación de realidad mixta, UWP, Windows Vista administración, xaml, teclado, tutorial, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598687"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Uso de XAML con aplicaciones de DirectX holográficas

En este tema se explica el impacto del cambio entre [2D vistas XAML y envolventes](app-views.md) en la aplicación de DirectX y cómo hacer un uso eficaz de una vista XAML y la vista envolvente.

## <a name="xaml-view-switching-overview"></a>Información general de cambio de la vista XAML

En HoloLens, una aplicación generalmente envolvente que posteriormente se puede mostrar una vista XAML 2D debe inicializar primero esa vista XAML y pasar inmediatamente a una vista envolvente a partir de ahí. Esto significa que XAML se cargará antes de la aplicación puede hacer cualquier cosa. Como resultado, habrá un pequeño incremento en el tiempo de inicio y XAML seguirán ocupando espacio de memoria en el proceso de aplicación mientras se encuentra en segundo plano; la cantidad de retraso de inicio y uso depende de lo que hace la aplicación con XAML antes de cambiar a la vista nativa de memoria. Si no hace nada en el código al principio, salvo que iniciar la vista envolvente de inicio XAML, el impacto debería ser menor. Además, dado que se realiza la representación holográfica directamente a la vista envolvente, evitará las restricciones relacionadas con el XAML en esa representación.

Tenga en cuenta que cuenta el uso de memoria de CPU y GPU. Direct3D 11 es capaz de intercambiar la memoria de gráficos virtuales, pero es posible que no pueda intercambiar algunos o todos los recursos XAML GPU y es posible que haya una disminución del rendimiento notable. En cualquier caso, no carga las características XAML que no necesita se deja más espacio para la aplicación y ofrecer una mejor experiencia.

## <a name="xaml-view-switching-workflow"></a>Cambio de flujo de trabajo de la vista XAML

El flujo de trabajo para una aplicación que se va directamente desde XAML a modo envolvente es así:
* La aplicación se inicia en la vista XAML 2D.
* Secuencia de inicio de la aplicación XAML detecta si el sistema actual admite la representación holográfica:
* Si es así, la aplicación crea la vista envolvente y pone inmediatamente al primer plano. Carga de XAML se omite para cualquier elemento que no sea necesario en los dispositivos de Windows Mixed Reality, incluidas las clases de representación y activos que se carga en la vista XAML. Si la aplicación usa XAML para la entrada de teclado, esa página de entrada debe crearse.
* Si no es así, la vista XAML puede continuar con la empresa como de costumbre.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Sugerencia para la representación de gráficos en ambas vistas

Si la aplicación necesita para implementar cierta cantidad de representación en DirectX para la vista XAML en Windows Mixed Reality, la mejor opción es crear a un representador que funcione con ambas vistas. El representador debe ser una instancia que se puede acceder desde ambas vistas, y debe ser capaz de cambiar entre la representación 2D y holográfica. De este modo los activos GPU solo se cargan una vez; esto reduce los tiempos de carga, repercusión en la memoria y la cantidad de recursos deben intercambiar al cambiar de vista.
