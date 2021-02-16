---
description: Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 54108eaafa645452f58b1962c3f103bcdd5c9e4a
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529988"
---
# <a name="about-wildcards"></a><span data-ttu-id="76a1b-103">Over joker tekens</span><span class="sxs-lookup"><span data-stu-id="76a1b-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="76a1b-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="76a1b-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="76a1b-105">Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="76a1b-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="76a1b-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="76a1b-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="76a1b-107">Joker tekens vertegenwoordigen een of meer tekens.</span><span class="sxs-lookup"><span data-stu-id="76a1b-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="76a1b-108">U kunt ze gebruiken om woord patronen te maken in opdrachten.</span><span class="sxs-lookup"><span data-stu-id="76a1b-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="76a1b-109">Joker teken expressies worden gebruikt met de `-like` operator of met een para meter die joker tekens accepteert.</span><span class="sxs-lookup"><span data-stu-id="76a1b-109">Wildcard expressions are used with the `-like` operator or with any parameter that accepts wildcards.</span></span>

<span data-ttu-id="76a1b-110">Als u bijvoorbeeld alle bestanden in de `C:\Techdocs` map met een `.ppt` bestands extensie wilt vergelijken, typt u:</span><span class="sxs-lookup"><span data-stu-id="76a1b-110">For example, to match all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="76a1b-111">In dit geval `*` vertegenwoordigt het Joker teken sterretje () alle tekens die voor de bestandsnaam extensie worden weer gegeven `.ppt` .</span><span class="sxs-lookup"><span data-stu-id="76a1b-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="76a1b-112">Joker teken expressies zijn eenvoudiger dan reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="76a1b-112">Wildcard expressions are simpler than regular expressions.</span></span> <span data-ttu-id="76a1b-113">Zie [about_Regular_Expressions](./about_Regular_Expressions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="76a1b-113">For more information, see [about_Regular_Expressions](./about_Regular_Expressions.md).</span></span>

<span data-ttu-id="76a1b-114">Power shell ondersteunt de volgende joker tekens:</span><span class="sxs-lookup"><span data-stu-id="76a1b-114">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="76a1b-115">Vervanging</span><span class="sxs-lookup"><span data-stu-id="76a1b-115">Wildcard</span></span>|<span data-ttu-id="76a1b-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="76a1b-116">Description</span></span>               |<span data-ttu-id="76a1b-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="76a1b-117">Example</span></span> |<span data-ttu-id="76a1b-118">Match</span><span class="sxs-lookup"><span data-stu-id="76a1b-118">Match</span></span>        |<span data-ttu-id="76a1b-119">Geen overeenkomst</span><span class="sxs-lookup"><span data-stu-id="76a1b-119">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="76a1b-120">Nul of meer tekens</span><span class="sxs-lookup"><span data-stu-id="76a1b-120">Match zero or more characters</span></span> | <span data-ttu-id="76a1b-121">één\*</span><span class="sxs-lookup"><span data-stu-id="76a1b-121">a\*</span></span>  | <span data-ttu-id="76a1b-122">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="76a1b-122">aA, ag, Apple</span></span> | <span data-ttu-id="76a1b-123">bananen</span><span class="sxs-lookup"><span data-stu-id="76a1b-123">banana</span></span> |
|<span data-ttu-id="76a1b-124">?</span><span class="sxs-lookup"><span data-stu-id="76a1b-124">?</span></span>       |<span data-ttu-id="76a1b-125">Komt overeen met één teken op die positie</span><span class="sxs-lookup"><span data-stu-id="76a1b-125">Match one character in that position</span></span> | <span data-ttu-id="76a1b-126">? n</span><span class="sxs-lookup"><span data-stu-id="76a1b-126">?n</span></span> | <span data-ttu-id="76a1b-127">een, in, op</span><span class="sxs-lookup"><span data-stu-id="76a1b-127">an, in, on</span></span> | <span data-ttu-id="76a1b-128">uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="76a1b-128">ran</span></span> |
|<span data-ttu-id="76a1b-129">\[ \]</span><span class="sxs-lookup"><span data-stu-id="76a1b-129">\[ \]</span></span>   |<span data-ttu-id="76a1b-130">Komt overeen met een reeks tekens</span><span class="sxs-lookup"><span data-stu-id="76a1b-130">Match a range of characters</span></span> | <span data-ttu-id="76a1b-131">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="76a1b-131">\[a-l\]ook</span></span> | <span data-ttu-id="76a1b-132">Book, Cook, zoeken</span><span class="sxs-lookup"><span data-stu-id="76a1b-132">book, cook, look</span></span> | <span data-ttu-id="76a1b-133">spoed</span><span class="sxs-lookup"><span data-stu-id="76a1b-133">took</span></span> |
|<span data-ttu-id="76a1b-134">\[ \]</span><span class="sxs-lookup"><span data-stu-id="76a1b-134">\[ \]</span></span>   |<span data-ttu-id="76a1b-135">Overeenkomen met specifieke tekens</span><span class="sxs-lookup"><span data-stu-id="76a1b-135">Match specific characters</span></span> | <span data-ttu-id="76a1b-136">\[BC \] ook</span><span class="sxs-lookup"><span data-stu-id="76a1b-136">\[bc\]ook</span></span> | <span data-ttu-id="76a1b-137">Book, Cook</span><span class="sxs-lookup"><span data-stu-id="76a1b-137">book, cook</span></span> | <span data-ttu-id="76a1b-138">accolade</span><span class="sxs-lookup"><span data-stu-id="76a1b-138">hook</span></span> |

<span data-ttu-id="76a1b-139">U kunt meerdere joker tekens in hetzelfde woord patroon toevoegen.</span><span class="sxs-lookup"><span data-stu-id="76a1b-139">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="76a1b-140">Als u bijvoorbeeld tekst bestanden zoekt met namen die beginnen met de letters **a** t/m **l**, typt u:</span><span class="sxs-lookup"><span data-stu-id="76a1b-140">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="76a1b-141">Veel cmdlets accepteren joker tekens in parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="76a1b-141">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="76a1b-142">In het Help-onderwerp voor elke cmdlet wordt beschreven welke para meters joker tekens accepteren.</span><span class="sxs-lookup"><span data-stu-id="76a1b-142">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="76a1b-143">Voor para meters die joker tekens accepteren, is het gebruik niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="76a1b-143">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="76a1b-144">U kunt joker tekens gebruiken in opdrachten en script blokken, zoals het maken van een Word-patroon dat eigenschaps waarden vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="76a1b-144">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="76a1b-145">Met de volgende opdracht worden bijvoorbeeld services opgehaald waarin de waarde van de eigenschap **service** type **interactief** is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="76a1b-145">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="76a1b-146">In het volgende voor beeld `If` bevat de instructie een voor waarde die joker tekens gebruikt om eigenschaps waarden te vinden.</span><span class="sxs-lookup"><span data-stu-id="76a1b-146">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="76a1b-147">Als de **Beschrijving** van het herstel punt **Power shell** bevat, voegt de opdracht de waarde van de eigenschap **CreationTime** van het herstel punt toe aan een logboek bestand.</span><span class="sxs-lookup"><span data-stu-id="76a1b-147">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="76a1b-148">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="76a1b-148">SEE ALSO</span></span>

[<span data-ttu-id="76a1b-149">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="76a1b-149">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="76a1b-150">about_If</span><span class="sxs-lookup"><span data-stu-id="76a1b-150">about_If</span></span>](about_If.md)

[<span data-ttu-id="76a1b-151">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="76a1b-151">about_Script_Blocks</span></span>](about_Script_Blocks.md)
