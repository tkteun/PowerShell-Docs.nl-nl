---
title: Wat is een Power shell-opdracht?
description: Met Power shell kunt u elke opdracht uitvoeren die beschikbaar is op uw systeem en een Power shell-specifieke opdracht die wordt aangeduid als cmdlets.
ms.date: 03/31/2021
ms.openlocfilehash: b6e54349ec15df3327c1f0525dce1a30ad35a6ac
ms.sourcegitcommit: eeedd4472b6cc6158494296c355579791e688baa
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106104070"
---
# <a name="powershell-commands"></a><span data-ttu-id="85855-103">PowerShell-opdrachten</span><span class="sxs-lookup"><span data-stu-id="85855-103">PowerShell commands</span></span>

<span data-ttu-id="85855-104">Met Power shell kunt u elke opdracht uitvoeren die beschikbaar is op uw systeem, met inbegrip van Power shell-opdrachten die worden aangeduid als cmdlets (uitgesp roken opdracht-staat).</span><span class="sxs-lookup"><span data-stu-id="85855-104">PowerShell allows you to run any command available on your system including PowerShell-specific commands known as cmdlets (pronounced command-lets).</span></span>

## <a name="what-is-a-cmdlet"></a><span data-ttu-id="85855-105">Wat is een cmdlet?</span><span class="sxs-lookup"><span data-stu-id="85855-105">What is a cmdlet?</span></span>

<span data-ttu-id="85855-106">Een cmdlet is één opdracht die deel uitmaakt van de pijp lijn semantiek van Power shell en retourneert meestal een .NET-object.</span><span class="sxs-lookup"><span data-stu-id="85855-106">A cmdlet is a single command that participates in the pipeline semantics of PowerShell and typically returns a .NET object.</span></span> <span data-ttu-id="85855-107">Cmdlets zijn systeem eigen Power shell-opdrachten, geen zelfstandige uitvoer bare bestanden.</span><span class="sxs-lookup"><span data-stu-id="85855-107">Cmdlets are native PowerShell commands, not stand-alone executables.</span></span> <span data-ttu-id="85855-108">Cmdlets worden verzameld in Power shell-modules die op aanvraag kunnen worden geladen.</span><span class="sxs-lookup"><span data-stu-id="85855-108">Cmdlets are collected into PowerShell modules that can be loaded on demand.</span></span> <span data-ttu-id="85855-109">Cmdlets kunnen worden geschreven in elke gecompileerde .NET-taal of in de Power shell-script taal zelf.</span><span class="sxs-lookup"><span data-stu-id="85855-109">Cmdlets can be written in any compiled .NET language or in the PowerShell scripting language itself.</span></span>

## <a name="cmdlet-names"></a><span data-ttu-id="85855-110">Namen van cmdlets</span><span class="sxs-lookup"><span data-stu-id="85855-110">Cmdlet names</span></span>

<span data-ttu-id="85855-111">Power shell gebruikt een combi natie van naam woorden en namen van _termen_ .</span><span class="sxs-lookup"><span data-stu-id="85855-111">PowerShell uses a _Verb-Noun_ name pair to name cmdlets.</span></span> <span data-ttu-id="85855-112">De `Get-Command` cmdlet die is opgenomen in Power shell wordt bijvoorbeeld gebruikt om alle cmdlets op te halen die zijn geregistreerd in de opdracht shell.</span><span class="sxs-lookup"><span data-stu-id="85855-112">For example, the `Get-Command` cmdlet included in PowerShell is used to get all the cmdlets that are registered in the command shell.</span></span> <span data-ttu-id="85855-113">De opdracht geeft de actie aan die door de cmdlet wordt uitgevoerd en het zelfstandig naam woord identificeert de resource waarop de cmdlet de actie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="85855-113">The verb identifies the action that the cmdlet performs, and the noun identifies the resource on which the cmdlet performs its action.</span></span>

## <a name="next-steps"></a><span data-ttu-id="85855-114">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="85855-114">Next steps</span></span>

<span data-ttu-id="85855-115">Meer informatie over Power shell en het vinden van andere cmdlets vindt u in de zelf studie Power shell-bits [Discover Power shell](learn/tutorials/01-discover-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="85855-115">To learn more about PowerShell and how to find other cmdlets, see the PowerShell Bits tutorial [Discover PowerShell](learn/tutorials/01-discover-powershell.md).</span></span>

<span data-ttu-id="85855-116">Raadpleeg de volgende bronnen voor meer informatie over het maken van uw eigen cmdlets:</span><span class="sxs-lookup"><span data-stu-id="85855-116">For more information about creating your own cmdlets, see the following resources:</span></span>

<span data-ttu-id="85855-117">Op scripts gebaseerde cmdlets</span><span class="sxs-lookup"><span data-stu-id="85855-117">Script-based cmdlets</span></span>

- [<span data-ttu-id="85855-118">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="85855-118">about_Functions_Advanced</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [<span data-ttu-id="85855-119">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="85855-119">about_Functions_CmdletBindingAttribute</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [<span data-ttu-id="85855-120">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="85855-120">about_Functions_Advanced_Methods</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

<span data-ttu-id="85855-121">Gecompileerde cmdlets (Power shell SDK docs)</span><span class="sxs-lookup"><span data-stu-id="85855-121">Compiled cmdlets (PowerShell SDK docs)</span></span>

- [<span data-ttu-id="85855-122">Overzicht van de cmdlet</span><span class="sxs-lookup"><span data-stu-id="85855-122">Cmdlet overview</span></span>](developer/cmdlet/cmdlet-overview.md)
