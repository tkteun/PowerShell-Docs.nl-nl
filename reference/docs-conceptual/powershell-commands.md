---
title: Wat is een PowerShell-opdracht?
description: Opdrachten voor PowerShell worden cmdlets genoemd (uitgesproken als command-lets)
ms.date: 03/31/2021
ms.openlocfilehash: 3980ed53f0e0c6f86a5ebab7b6ca64aeee6b173e
ms.sourcegitcommit: d63769de0e59d117d90171799bda6544bf2f2f0b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107855563"
---
# <a name="what-is-a-powershell-command-cmdlet"></a><span data-ttu-id="f4ecb-103">Wat is een PowerShell-opdracht (cmdlet)?</span><span class="sxs-lookup"><span data-stu-id="f4ecb-103">What is a PowerShell command (cmdlet)?</span></span>

<span data-ttu-id="f4ecb-104">Opdrachten voor PowerShell worden cmdlets genoemd (uitgesproken als command-lets).</span><span class="sxs-lookup"><span data-stu-id="f4ecb-104">Commands for PowerShell are known as cmdlets (pronounced command-lets).</span></span> <span data-ttu-id="f4ecb-105">Naast cmdlets kunt u met PowerShell elke opdracht uitvoeren die beschikbaar is op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-105">In addition to cmdlets, PowerShell allows you to run any command available on your system.</span></span>

## <a name="what-is-a-cmdlet"></a><span data-ttu-id="f4ecb-106">Wat is een cmdlet?</span><span class="sxs-lookup"><span data-stu-id="f4ecb-106">What is a cmdlet?</span></span>

<span data-ttu-id="f4ecb-107">Cmdlets zijn native PowerShell-opdrachten, geen stand-alone uitvoerbare bestanden.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-107">Cmdlets are native PowerShell commands, not stand-alone executables.</span></span> <span data-ttu-id="f4ecb-108">Cmdlets worden verzameld in PowerShell-modules die op aanvraag kunnen worden geladen.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-108">Cmdlets are collected into PowerShell modules that can be loaded on demand.</span></span> <span data-ttu-id="f4ecb-109">Cmdlets kunnen worden geschreven in elke gecompileerde .NET-taal of in de PowerShell-scripttaal zelf.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-109">Cmdlets can be written in any compiled .NET language or in the PowerShell scripting language itself.</span></span>

## <a name="cmdlet-names"></a><span data-ttu-id="f4ecb-110">Cmdlet-namen</span><span class="sxs-lookup"><span data-stu-id="f4ecb-110">Cmdlet names</span></span>

<span data-ttu-id="f4ecb-111">PowerShell maakt gebruik van een _werkwoord-zelfstandig naampaar_ om cmdlets te noemen.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-111">PowerShell uses a _Verb-Noun_ name pair to name cmdlets.</span></span> <span data-ttu-id="f4ecb-112">De cmdlet die is opgenomen in PowerShell wordt bijvoorbeeld gebruikt om alle cmdlets op te halen `Get-Command` die zijn geregistreerd in de opdrachtshell.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-112">For example, the `Get-Command` cmdlet included in PowerShell is used to get all the cmdlets that are registered in the command shell.</span></span> <span data-ttu-id="f4ecb-113">De werkwoord identificeert de actie die de cmdlet uitvoert en het zelfstandig naamwoord identificeert de resource waarop de cmdlet de actie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-113">The verb identifies the action that the cmdlet performs, and the noun identifies the resource on which the cmdlet performs its action.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f4ecb-114">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="f4ecb-114">Next steps</span></span>

<span data-ttu-id="f4ecb-115">Zie de PowerShell Bits-zelfstudie PowerShell ontdekken voor meer [](learn/tutorials/01-discover-powershell.md)informatie over PowerShell en het vinden van andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f4ecb-115">To learn more about PowerShell and how to find other cmdlets, see the PowerShell Bits tutorial [Discover PowerShell](learn/tutorials/01-discover-powershell.md).</span></span>

<span data-ttu-id="f4ecb-116">Zie de volgende bronnen voor meer informatie over het maken van uw eigen cmdlets:</span><span class="sxs-lookup"><span data-stu-id="f4ecb-116">For more information about creating your own cmdlets, see the following resources:</span></span>

<span data-ttu-id="f4ecb-117">Cmdlets op basis van scripts</span><span class="sxs-lookup"><span data-stu-id="f4ecb-117">Script-based cmdlets</span></span>

- [<span data-ttu-id="f4ecb-118">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="f4ecb-118">about_Functions_Advanced</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [<span data-ttu-id="f4ecb-119">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="f4ecb-119">about_Functions_CmdletBindingAttribute</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [<span data-ttu-id="f4ecb-120">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="f4ecb-120">about_Functions_Advanced_Methods</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

<span data-ttu-id="f4ecb-121">Gecompileerde cmdlets (PowerShell SDK-documenten)</span><span class="sxs-lookup"><span data-stu-id="f4ecb-121">Compiled cmdlets (PowerShell SDK docs)</span></span>

- [<span data-ttu-id="f4ecb-122">Overzicht van cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4ecb-122">Cmdlet overview</span></span>](developer/cmdlet/cmdlet-overview.md)
