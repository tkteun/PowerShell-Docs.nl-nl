---
ms.date: 09/13/2016
ms.topic: reference
title: Modules en snap-ins
description: Modules en snap-ins
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658686"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="11edb-103">Modules en snap-ins</span><span class="sxs-lookup"><span data-stu-id="11edb-103">Modules and Snap-ins</span></span>

<span data-ttu-id="11edb-104">Cmdlets kunnen worden toegevoegd aan een sessie met behulp van modules (geïntroduceerd door Windows Power Shell 2,0) of modules. Zodra de cmdlet is toegevoegd aan de sessie, kan de toepassing programmatisch worden uitgevoerd door een hosttoepassing of interactief op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="11edb-104">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="11edb-105">U wordt aangeraden modules te gebruiken als de leverings methode voor het toevoegen van cmdlets aan een sessie om de volgende redenen:</span><span class="sxs-lookup"><span data-stu-id="11edb-105">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="11edb-106">Met modules kunt u cmdlets toevoegen door de assembly te laden waarin de cmdlet is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="11edb-106">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="11edb-107">U hoeft geen module te implementeren.</span><span class="sxs-lookup"><span data-stu-id="11edb-107">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="11edb-108">Met modules kunt u andere resources toevoegen, zoals variabelen, functies, scripts, typen en indelings bestanden, en meer.</span><span class="sxs-lookup"><span data-stu-id="11edb-108">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="11edb-109">Modules kunnen alleen worden gebruikt om cmdlets en providers toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="11edb-109">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="11edb-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11edb-110">See Also</span></span>

[<span data-ttu-id="11edb-111">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="11edb-111">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="11edb-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="11edb-112">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
