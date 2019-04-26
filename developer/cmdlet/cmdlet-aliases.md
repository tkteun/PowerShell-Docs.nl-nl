---
title: Cmdlet aliassen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068711"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="d5322-102">Cmdlet-aliassen</span><span class="sxs-lookup"><span data-stu-id="d5322-102">Cmdlet Aliases</span></span>

<span data-ttu-id="d5322-103">U kunt cmdlet-aliassen gebruiken voor het verbeteren van de gebruikerservaring van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5322-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="d5322-104">U kunt aliassen voor veelgebruikte-cmdlets te verminderen te typen en eenvoudiger taken uitvoeren snel toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d5322-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="d5322-105">U kunt ingebouwde aliassen opnemen in uw cmdlets, of gebruikers kunnen hun eigen aangepaste aliassen definiëren.</span><span class="sxs-lookup"><span data-stu-id="d5322-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="d5322-106">Bijvoorbeeld, de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet heeft een ingebouwde `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="d5322-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="d5322-107">U kunt ook aliassen gebruiken om toe te voegen opdrachtnamen van andere talen zodat gebruikers geen nieuwe opdrachten te leren.</span><span class="sxs-lookup"><span data-stu-id="d5322-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="d5322-108">Alias-richtlijnen</span><span class="sxs-lookup"><span data-stu-id="d5322-108">Alias Guidelines</span></span>

<span data-ttu-id="d5322-109">Volg deze richtlijnen wanneer u ingebouwde aliassen voor uw cmdlets maakt:</span><span class="sxs-lookup"><span data-stu-id="d5322-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="d5322-110">Voordat u alias toewijst, start u Windows PowerShell en voer vervolgens de [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet om te controleren van de aliassen die al worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d5322-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="d5322-111">Een alias-voorvoegsel dat verwijst naar de bewerking van de cmdlet-naam en een alias-achtervoegsel die verwijst naar het zelfstandig naamwoord van de cmdlet-naam bevatten.</span><span class="sxs-lookup"><span data-stu-id="d5322-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="d5322-112">Bijvoorbeeld: de alias voor de `Import-Module` cmdlet is 'ipmo'.</span><span class="sxs-lookup"><span data-stu-id="d5322-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="d5322-113">Zie voor een lijst van alle bewerkingen en hun aliassen, [werkwoorden](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="d5322-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="d5322-114">Cmdlets die de dezelfde opdracht hebben, zijn hetzelfde voorvoegsel alias.</span><span class="sxs-lookup"><span data-stu-id="d5322-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="d5322-115">Bijvoorbeeld de aliassen voor alle Windows PowerShell-cmdlets die de term 'Get' in hun naam hebben het voorvoegsel "g" gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d5322-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="d5322-116">De cmdlets die de dezelfde zelfstandig naamwoord, het achtervoegsel van dezelfde alias opgenomen.</span><span class="sxs-lookup"><span data-stu-id="d5322-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="d5322-117">Bijvoorbeeld, gebruik de aliassen voor alle Windows PowerShell-cmdlets die de "Sessie" zelfstandig naamwoord in hun naam hebben het achtervoegsel 'sn'.</span><span class="sxs-lookup"><span data-stu-id="d5322-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="d5322-118">De cmdlets die gelijk aan de opdrachten in andere talen zijn, de naam van de opdracht te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d5322-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="d5322-119">In het algemeen moet u aliassen zo kort mogelijk.</span><span class="sxs-lookup"><span data-stu-id="d5322-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="d5322-120">Zorg ervoor dat de alias is ten minste één afzonderlijke voor het werkwoord en een afzonderlijke teken voor het zelfstandig naamwoord.</span><span class="sxs-lookup"><span data-stu-id="d5322-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="d5322-121">Voeg meer tekens zo nodig de alias uniek te maken.</span><span class="sxs-lookup"><span data-stu-id="d5322-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5322-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d5322-122">See Also</span></span>

[<span data-ttu-id="d5322-123">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d5322-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
