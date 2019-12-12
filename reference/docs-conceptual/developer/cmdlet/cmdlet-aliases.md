---
title: Cmdlet-aliassen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359458"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="11682-102">Cmdlet-aliassen</span><span class="sxs-lookup"><span data-stu-id="11682-102">Cmdlet Aliases</span></span>

<span data-ttu-id="11682-103">U kunt cmdlet-aliassen gebruiken om de gebruikers ervaring van de cmdlet te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="11682-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="11682-104">U kunt aliassen toevoegen aan veelgebruikte cmdlets om het typen te verminderen en om het eenvoudiger te maken om taken snel uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="11682-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="11682-105">U kunt ingebouwde aliassen in uw cmdlets toevoegen, of gebruikers kunnen hun eigen aangepaste aliassen definiëren.</span><span class="sxs-lookup"><span data-stu-id="11682-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="11682-106">De [Get-opdracht](/powershell/module/microsoft.powershell.core/get-command) cmdlet heeft bijvoorbeeld een ingebouwde `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="11682-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="11682-107">U kunt ook aliassen gebruiken om opdracht namen uit andere talen toe te voegen, zodat gebruikers geen nieuwe opdrachten hoeven te leren.</span><span class="sxs-lookup"><span data-stu-id="11682-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="11682-108">Richt lijnen voor alias</span><span class="sxs-lookup"><span data-stu-id="11682-108">Alias Guidelines</span></span>

<span data-ttu-id="11682-109">Volg deze richt lijnen wanneer u ingebouwde aliassen voor uw cmdlets maakt:</span><span class="sxs-lookup"><span data-stu-id="11682-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="11682-110">Voordat u aliassen toewijst, start u Windows Power shell en voert u de cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) uit om de aliassen weer te geven die al zijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11682-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="11682-111">Neem een voor voegsel van een alias op dat verwijst naar het werk woord van de naam van de cmdlet en een alias achtervoegsel dat verwijst naar het zelfstandig naam woord van de cmdletnaam.</span><span class="sxs-lookup"><span data-stu-id="11682-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="11682-112">De alias voor de `Import-Module`-cmdlet is bijvoorbeeld ' ipmo '.</span><span class="sxs-lookup"><span data-stu-id="11682-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="11682-113">Zie [cmdlet-termen](./approved-verbs-for-windows-powershell-commands.md)voor een lijst met alle termen en de bijbehorende aliassen.</span><span class="sxs-lookup"><span data-stu-id="11682-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="11682-114">Voor cmdlets die dezelfde term hebben, neemt u hetzelfde alias voorvoegsel op.</span><span class="sxs-lookup"><span data-stu-id="11682-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="11682-115">Bijvoorbeeld: de aliassen voor alle Windows Power shell-cmdlets die de opdracht ' Get ' hebben in hun naam, gebruiken het voor voegsel ' g '.</span><span class="sxs-lookup"><span data-stu-id="11682-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="11682-116">Voor cmdlets die hetzelfde zelfstandig naam woord hebben, neemt u hetzelfde alias achtervoegsel op.</span><span class="sxs-lookup"><span data-stu-id="11682-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="11682-117">De aliassen voor alle Windows Power shell-cmdlets die het zelfstandig naam woord ' session ' hebben, gebruiken bijvoorbeeld het achtervoegsel ' SN '.</span><span class="sxs-lookup"><span data-stu-id="11682-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="11682-118">Voor cmdlets die gelijk zijn aan opdrachten in andere talen, gebruikt u de naam van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="11682-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="11682-119">In het algemeen maakt u aliassen zo kort mogelijk.</span><span class="sxs-lookup"><span data-stu-id="11682-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="11682-120">Zorg ervoor dat de alias ten minste één afzonderlijk teken voor de opdracht en één afzonderlijk teken voor het zelfstandige naam heeft.</span><span class="sxs-lookup"><span data-stu-id="11682-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="11682-121">Voeg indien nodig meer tekens toe om de alias uniek te maken.</span><span class="sxs-lookup"><span data-stu-id="11682-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="11682-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11682-122">See Also</span></span>

[<span data-ttu-id="11682-123">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="11682-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
