---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-aliassen
description: Cmdlet-aliassen
ms.openlocfilehash: 734553a9911aef256df563afa6abcdb23d7a62e6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660784"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="ba19f-103">Cmdlet-aliassen</span><span class="sxs-lookup"><span data-stu-id="ba19f-103">Cmdlet Aliases</span></span>

<span data-ttu-id="ba19f-104">U kunt cmdlet-aliassen gebruiken om de gebruikers ervaring van de cmdlet te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="ba19f-104">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="ba19f-105">U kunt aliassen toevoegen aan veelgebruikte cmdlets om het typen te verminderen en om het eenvoudiger te maken om taken snel uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ba19f-105">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="ba19f-106">U kunt ingebouwde aliassen in uw cmdlets toevoegen, of gebruikers kunnen hun eigen aangepaste aliassen definiëren.</span><span class="sxs-lookup"><span data-stu-id="ba19f-106">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="ba19f-107">De [Get-opdracht](/powershell/module/microsoft.powershell.core/get-command) cmdlet heeft bijvoorbeeld een ingebouwde `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="ba19f-107">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="ba19f-108">U kunt ook aliassen gebruiken om opdracht namen uit andere talen toe te voegen, zodat gebruikers geen nieuwe opdrachten hoeven te leren.</span><span class="sxs-lookup"><span data-stu-id="ba19f-108">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="ba19f-109">Richt lijnen voor alias</span><span class="sxs-lookup"><span data-stu-id="ba19f-109">Alias Guidelines</span></span>

<span data-ttu-id="ba19f-110">Volg deze richt lijnen wanneer u ingebouwde aliassen voor uw cmdlets maakt:</span><span class="sxs-lookup"><span data-stu-id="ba19f-110">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="ba19f-111">Voordat u aliassen toewijst, start u Windows Power shell en voert u de cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) uit om de aliassen weer te geven die al zijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ba19f-111">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="ba19f-112">Neem een voor voegsel van een alias op dat verwijst naar het werk woord van de naam van de cmdlet en een alias achtervoegsel dat verwijst naar het zelfstandig naam woord van de cmdletnaam.</span><span class="sxs-lookup"><span data-stu-id="ba19f-112">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="ba19f-113">De alias voor de `Import-Module` cmdlet is bijvoorbeeld ' ipmo '.</span><span class="sxs-lookup"><span data-stu-id="ba19f-113">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="ba19f-114">Zie [cmdlet-termen](./approved-verbs-for-windows-powershell-commands.md)voor een lijst met alle termen en de bijbehorende aliassen.</span><span class="sxs-lookup"><span data-stu-id="ba19f-114">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="ba19f-115">Voor cmdlets die dezelfde term hebben, neemt u hetzelfde alias voorvoegsel op.</span><span class="sxs-lookup"><span data-stu-id="ba19f-115">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="ba19f-116">Bijvoorbeeld: de aliassen voor alle Windows Power shell-cmdlets die de opdracht ' Get ' hebben in hun naam, gebruiken het voor voegsel ' g '.</span><span class="sxs-lookup"><span data-stu-id="ba19f-116">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="ba19f-117">Voor cmdlets die hetzelfde zelfstandig naam woord hebben, neemt u hetzelfde alias achtervoegsel op.</span><span class="sxs-lookup"><span data-stu-id="ba19f-117">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="ba19f-118">De aliassen voor alle Windows Power shell-cmdlets die het zelfstandig naam woord ' session ' hebben, gebruiken bijvoorbeeld het achtervoegsel ' SN '.</span><span class="sxs-lookup"><span data-stu-id="ba19f-118">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="ba19f-119">Voor cmdlets die gelijk zijn aan opdrachten in andere talen, gebruikt u de naam van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="ba19f-119">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="ba19f-120">In het algemeen maakt u aliassen zo kort mogelijk.</span><span class="sxs-lookup"><span data-stu-id="ba19f-120">In general, make aliases as short as possible.</span></span> <span data-ttu-id="ba19f-121">Zorg ervoor dat de alias ten minste één afzonderlijk teken voor de opdracht en één afzonderlijk teken voor het zelfstandige naam heeft.</span><span class="sxs-lookup"><span data-stu-id="ba19f-121">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="ba19f-122">Voeg indien nodig meer tekens toe om de alias uniek te maken.</span><span class="sxs-lookup"><span data-stu-id="ba19f-122">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba19f-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ba19f-123">See Also</span></span>

[<span data-ttu-id="ba19f-124">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="ba19f-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
