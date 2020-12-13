---
ms.date: 09/13/2016
ms.topic: reference
title: Modules en snap-ins
description: Modules en snap-ins
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658686"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="827b3-103">Modules en snap-ins</span><span class="sxs-lookup"><span data-stu-id="827b3-103">Modules and Snap-ins</span></span>

<span data-ttu-id="827b3-104">Cmdlets kunnen worden toegevoegd aan een sessie met behulp van modules (geïntroduceerd door Windows Power Shell 2,0) of modules. Zodra de cmdlet is toegevoegd aan de sessie, kan de toepassing programmatisch worden uitgevoerd door een hosttoepassing of interactief op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="827b3-104">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="827b3-105">U wordt aangeraden modules te gebruiken als de leverings methode voor het toevoegen van cmdlets aan een sessie om de volgende redenen:</span><span class="sxs-lookup"><span data-stu-id="827b3-105">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="827b3-106">Met modules kunt u cmdlets toevoegen door de assembly te laden waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="827b3-106">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="827b3-107">U hoeft geen module te implementeren.</span><span class="sxs-lookup"><span data-stu-id="827b3-107">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="827b3-108">Met modules kunt u andere resources toevoegen, zoals variabelen, functies, scripts, typen en indelings bestanden, en meer.</span><span class="sxs-lookup"><span data-stu-id="827b3-108">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="827b3-109">Modules kunnen alleen worden gebruikt om cmdlets en providers toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="827b3-109">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="827b3-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="827b3-110">See Also</span></span>

[<span data-ttu-id="827b3-111">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="827b3-111">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="827b3-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="827b3-112">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
