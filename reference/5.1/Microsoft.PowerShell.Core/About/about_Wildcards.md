---
description: Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 4656266107a29e4f57c5e273788d382a477a2428
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252723"
---
# <a name="about-wildcards"></a><span data-ttu-id="b604d-104">Over joker tekens</span><span class="sxs-lookup"><span data-stu-id="b604d-104">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="b604d-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b604d-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b604d-106">Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b604d-106">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b604d-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b604d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b604d-108">Joker tekens vertegenwoordigen een of meer tekens.</span><span class="sxs-lookup"><span data-stu-id="b604d-108">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="b604d-109">U kunt ze gebruiken om woord patronen te maken in opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b604d-109">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="b604d-110">Als u bijvoorbeeld alle bestanden in de `C:\Techdocs` map met een `.ppt` bestands extensie wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="b604d-110">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="b604d-111">In dit geval `*` vertegenwoordigt het Joker teken sterretje () alle tekens die voor de bestandsnaam extensie worden weer gegeven `.ppt` .</span><span class="sxs-lookup"><span data-stu-id="b604d-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="b604d-112">Power shell ondersteunt de volgende joker tekens:</span><span class="sxs-lookup"><span data-stu-id="b604d-112">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="b604d-113">Vervanging</span><span class="sxs-lookup"><span data-stu-id="b604d-113">Wildcard</span></span>|<span data-ttu-id="b604d-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b604d-114">Description</span></span>               |<span data-ttu-id="b604d-115">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b604d-115">Example</span></span> |<span data-ttu-id="b604d-116">Match</span><span class="sxs-lookup"><span data-stu-id="b604d-116">Match</span></span>        |<span data-ttu-id="b604d-117">Geen overeenkomst</span><span class="sxs-lookup"><span data-stu-id="b604d-117">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="b604d-118">Nul of meer tekens</span><span class="sxs-lookup"><span data-stu-id="b604d-118">Match zero or more characters</span></span> | <span data-ttu-id="b604d-119">één\*</span><span class="sxs-lookup"><span data-stu-id="b604d-119">a\*</span></span>  | <span data-ttu-id="b604d-120">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="b604d-120">aA, ag, Apple</span></span> | <span data-ttu-id="b604d-121">bananen</span><span class="sxs-lookup"><span data-stu-id="b604d-121">banana</span></span> |
|<span data-ttu-id="b604d-122">?</span><span class="sxs-lookup"><span data-stu-id="b604d-122">?</span></span>       |<span data-ttu-id="b604d-123">Komt overeen met één teken op die positie</span><span class="sxs-lookup"><span data-stu-id="b604d-123">Match one character in that position</span></span> | <span data-ttu-id="b604d-124">? n</span><span class="sxs-lookup"><span data-stu-id="b604d-124">?n</span></span> | <span data-ttu-id="b604d-125">een, in, op</span><span class="sxs-lookup"><span data-stu-id="b604d-125">an, in, on</span></span> | <span data-ttu-id="b604d-126">uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="b604d-126">ran</span></span> |
|<span data-ttu-id="b604d-127">\[ \]</span><span class="sxs-lookup"><span data-stu-id="b604d-127">\[ \]</span></span>   |<span data-ttu-id="b604d-128">Komt overeen met een reeks tekens</span><span class="sxs-lookup"><span data-stu-id="b604d-128">Match a range of characters</span></span> | <span data-ttu-id="b604d-129">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="b604d-129">\[a-l\]ook</span></span> | <span data-ttu-id="b604d-130">Book, Cook, zoeken</span><span class="sxs-lookup"><span data-stu-id="b604d-130">book, cook, look</span></span> | <span data-ttu-id="b604d-131">spoed</span><span class="sxs-lookup"><span data-stu-id="b604d-131">took</span></span> |
|<span data-ttu-id="b604d-132">\[ \]</span><span class="sxs-lookup"><span data-stu-id="b604d-132">\[ \]</span></span>   |<span data-ttu-id="b604d-133">Overeenkomen met specifieke tekens</span><span class="sxs-lookup"><span data-stu-id="b604d-133">Match specific characters</span></span> | <span data-ttu-id="b604d-134">\[BC \] ook</span><span class="sxs-lookup"><span data-stu-id="b604d-134">\[bc\]ook</span></span> | <span data-ttu-id="b604d-135">Book, Cook</span><span class="sxs-lookup"><span data-stu-id="b604d-135">book, cook</span></span> | <span data-ttu-id="b604d-136">accolade</span><span class="sxs-lookup"><span data-stu-id="b604d-136">hook</span></span> |

<span data-ttu-id="b604d-137">U kunt meerdere joker tekens in hetzelfde woord patroon toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b604d-137">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="b604d-138">Als u bijvoorbeeld tekst bestanden zoekt met namen die beginnen met de letters **a** t/m **l** , typt u:</span><span class="sxs-lookup"><span data-stu-id="b604d-138">For example, to find text files with names that begin with the letters **a** through **l** , type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="b604d-139">Veel cmdlets accepteren joker tekens in parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="b604d-139">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="b604d-140">In het Help-onderwerp voor elke cmdlet wordt beschreven welke para meters joker tekens accepteren.</span><span class="sxs-lookup"><span data-stu-id="b604d-140">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="b604d-141">Voor para meters die joker tekens accepteren, is het gebruik niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="b604d-141">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="b604d-142">U kunt joker tekens gebruiken in opdrachten en script blokken, zoals het maken van een Word-patroon dat eigenschaps waarden vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b604d-142">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="b604d-143">Met de volgende opdracht worden bijvoorbeeld services opgehaald waarin de waarde van de eigenschap **service** type **interactief** is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="b604d-143">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="b604d-144">In het volgende voor beeld `If` bevat de instructie een voor waarde die joker tekens gebruikt om eigenschaps waarden te vinden.</span><span class="sxs-lookup"><span data-stu-id="b604d-144">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="b604d-145">Als de **Beschrijving** van het herstel punt **Power shell** bevat, voegt de opdracht de waarde van de eigenschap **CreationTime** van het herstel punt toe aan een logboek bestand.</span><span class="sxs-lookup"><span data-stu-id="b604d-145">If the restore point's **Description** includes **PowerShell** , the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="b604d-146">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="b604d-146">SEE ALSO</span></span>

[<span data-ttu-id="b604d-147">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="b604d-147">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="b604d-148">about_If</span><span class="sxs-lookup"><span data-stu-id="b604d-148">about_If</span></span>](about_If.md)

[<span data-ttu-id="b604d-149">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="b604d-149">about_Script_Blocks</span></span>](about_Script_Blocks.md)
