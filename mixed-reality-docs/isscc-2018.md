---
title: 'Notas del producto de la cámara de profundidad: ISSCC 2018'
description: Notas del producto técnicas en las que se describe la cámara de profundidad que se va a utilizar en el control Kinect de Project para Azure y la próxima versión de HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: Event, ISCC, Computer Vision, Research, Kinect, hololens, Depth, TOF
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516897"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="aa4d6-104">Notas del producto de la cámara de profundidad: ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="aa4d6-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="aa4d6-105">**Titulo** 1Mpixel 65nm BSI 320MHz desmodulado TOF de imagen con píxeles de obturador global 3,5 μm y discretización analógica</span><span class="sxs-lookup"><span data-stu-id="aa4d6-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="aa4d6-106">**Colaboradores** Cyrus S Bamji, Swati Mehta, Barry Thompson, Farag Elkhatib, Stefan Wurster, ONUR Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Sundanés nieve, Rich McCauley, Mustansir Mukadam, Iskender AGI, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, VEI-has Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="aa4d6-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="aa4d6-107">**Presentado en ISSCC 2018 y publicado en ISSCC Gradle. Técnicos. Papers, 2018 de febrero.**</span><span class="sxs-lookup"><span data-stu-id="aa4d6-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="aa4d6-108">C.</span><span class="sxs-lookup"><span data-stu-id="aa4d6-108">C.</span></span> <span data-ttu-id="aa4d6-109">Bamji et al., "1Mpixel 65nm BSI 320MHz demodulado TOF image sensor con 3,5 μm píxeles de obturación global y discretización analógicos," ISSCC Grad.</span><span class="sxs-lookup"><span data-stu-id="aa4d6-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="aa4d6-110">Técnicos.</span><span class="sxs-lookup"><span data-stu-id="aa4d6-110">Tech.</span></span> <span data-ttu-id="aa4d6-111">Papers, PP. 94-95, febrero de 2018.</span><span class="sxs-lookup"><span data-stu-id="aa4d6-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="aa4d6-112">Vínculo IEEE Explore: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="aa4d6-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="aa4d6-113">© IEEE 2018.</span><span class="sxs-lookup"><span data-stu-id="aa4d6-113">© 2018 IEEE.</span></span> <span data-ttu-id="aa4d6-114">Se permite el uso personal de este material.</span><span class="sxs-lookup"><span data-stu-id="aa4d6-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="aa4d6-115">El permiso de IEEE debe obtenerse para todos los demás usos, en cualquier medio actual o en el futuro, lo que incluye la reimpresión/republicación de este material con fines publicitarios o publicitarios, la creación de nuevas obras colectivas, la reventa o redistribución a servidores o listas, o la reutilización de cualquier componente con copyright de este trabajo en otros trabajos.</span><span class="sxs-lookup"><span data-stu-id="aa4d6-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="aa4d6-116">**Notas del producto**</span><span class="sxs-lookup"><span data-stu-id="aa4d6-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="aa4d6-117">![Vista previa de notas del producto](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="aa4d6-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="aa4d6-118">Notas del producto de download Depth Camera</span><span class="sxs-lookup"><span data-stu-id="aa4d6-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
