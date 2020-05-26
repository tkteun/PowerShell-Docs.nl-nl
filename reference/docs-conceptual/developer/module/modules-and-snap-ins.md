---
title: Modules en modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811161"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="33e5d-102">Modules en snap-ins</span><span class="sxs-lookup"><span data-stu-id="33e5d-102">Modules and Snap-ins</span></span>

<span data-ttu-id="33e5d-103">Cmdlets kunnen worden toegevoegd aan een sessie met behulp van modules (geïntroduceerd door Windows Power Shell 2,0) of modules. Zodra de cmdlet is toegevoegd aan de sessie, kan de toepassing programmatisch worden uitgevoerd door een hosttoepassing of interactief op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="33e5d-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="33e5d-104">U wordt aangeraden modules te gebruiken als de leverings methode voor het toevoegen van cmdlets aan een sessie om de volgende redenen:</span><span class="sxs-lookup"><span data-stu-id="33e5d-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="33e5d-105">Met modules kunt u cmdlets toevoegen door de assembly te laden waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="33e5d-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="33e5d-106">U hoeft geen module te implementeren.</span><span class="sxs-lookup"><span data-stu-id="33e5d-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="33e5d-107">Met modules kunt u andere resources toevoegen, zoals variabelen, functies, scripts, typen en indelings bestanden, en meer.</span><span class="sxs-lookup"><span data-stu-id="33e5d-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="33e5d-108">Modules kunnen alleen worden gebruikt om cmdlets en providers toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="33e5d-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="33e5d-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="33e5d-109">See Also</span></span>

[<span data-ttu-id="33e5d-110">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="33e5d-110">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="33e5d-111">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="33e5d-111">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
