---
description: Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: b5f13fdbfbc24e19e5ad0b1cd6ecc1b99f68914f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705781"
---
# <a name="about-wildcards"></a><span data-ttu-id="d7485-103">Over joker tekens</span><span class="sxs-lookup"><span data-stu-id="d7485-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="d7485-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d7485-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d7485-105">Hierin wordt beschreven hoe u Joker tekens gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="d7485-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d7485-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d7485-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="d7485-107">Joker tekens vertegenwoordigen een of meer tekens.</span><span class="sxs-lookup"><span data-stu-id="d7485-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="d7485-108">U kunt ze gebruiken om woord patronen te maken in opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d7485-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="d7485-109">Als u bijvoorbeeld alle bestanden in de `C:\Techdocs` map met een `.ppt` bestands extensie wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="d7485-109">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="d7485-110">In dit geval `*` vertegenwoordigt het Joker teken sterretje () alle tekens die voor de bestandsnaam extensie worden weer gegeven `.ppt` .</span><span class="sxs-lookup"><span data-stu-id="d7485-110">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="d7485-111">Power shell ondersteunt de volgende joker tekens:</span><span class="sxs-lookup"><span data-stu-id="d7485-111">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="d7485-112">Vervanging</span><span class="sxs-lookup"><span data-stu-id="d7485-112">Wildcard</span></span>|<span data-ttu-id="d7485-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d7485-113">Description</span></span>               |<span data-ttu-id="d7485-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d7485-114">Example</span></span> |<span data-ttu-id="d7485-115">Match</span><span class="sxs-lookup"><span data-stu-id="d7485-115">Match</span></span>        |<span data-ttu-id="d7485-116">Geen overeenkomst</span><span class="sxs-lookup"><span data-stu-id="d7485-116">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="d7485-117">Nul of meer tekens</span><span class="sxs-lookup"><span data-stu-id="d7485-117">Match zero or more characters</span></span> | <span data-ttu-id="d7485-118">één\*</span><span class="sxs-lookup"><span data-stu-id="d7485-118">a\*</span></span>  | <span data-ttu-id="d7485-119">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="d7485-119">aA, ag, Apple</span></span> | <span data-ttu-id="d7485-120">bananen</span><span class="sxs-lookup"><span data-stu-id="d7485-120">banana</span></span> |
|<span data-ttu-id="d7485-121">?</span><span class="sxs-lookup"><span data-stu-id="d7485-121">?</span></span>       |<span data-ttu-id="d7485-122">Komt overeen met één teken op die positie</span><span class="sxs-lookup"><span data-stu-id="d7485-122">Match one character in that position</span></span> | <span data-ttu-id="d7485-123">? n</span><span class="sxs-lookup"><span data-stu-id="d7485-123">?n</span></span> | <span data-ttu-id="d7485-124">een, in, op</span><span class="sxs-lookup"><span data-stu-id="d7485-124">an, in, on</span></span> | <span data-ttu-id="d7485-125">uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="d7485-125">ran</span></span> |
|<span data-ttu-id="d7485-126">\[ \]</span><span class="sxs-lookup"><span data-stu-id="d7485-126">\[ \]</span></span>   |<span data-ttu-id="d7485-127">Komt overeen met een reeks tekens</span><span class="sxs-lookup"><span data-stu-id="d7485-127">Match a range of characters</span></span> | <span data-ttu-id="d7485-128">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="d7485-128">\[a-l\]ook</span></span> | <span data-ttu-id="d7485-129">Book, Cook, zoeken</span><span class="sxs-lookup"><span data-stu-id="d7485-129">book, cook, look</span></span> | <span data-ttu-id="d7485-130">spoed</span><span class="sxs-lookup"><span data-stu-id="d7485-130">took</span></span> |
|<span data-ttu-id="d7485-131">\[ \]</span><span class="sxs-lookup"><span data-stu-id="d7485-131">\[ \]</span></span>   |<span data-ttu-id="d7485-132">Overeenkomen met specifieke tekens</span><span class="sxs-lookup"><span data-stu-id="d7485-132">Match specific characters</span></span> | <span data-ttu-id="d7485-133">\[BC \] ook</span><span class="sxs-lookup"><span data-stu-id="d7485-133">\[bc\]ook</span></span> | <span data-ttu-id="d7485-134">Book, Cook</span><span class="sxs-lookup"><span data-stu-id="d7485-134">book, cook</span></span> | <span data-ttu-id="d7485-135">accolade</span><span class="sxs-lookup"><span data-stu-id="d7485-135">hook</span></span> |

<span data-ttu-id="d7485-136">U kunt meerdere joker tekens in hetzelfde woord patroon toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d7485-136">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="d7485-137">Als u bijvoorbeeld tekst bestanden zoekt met namen die beginnen met de letters **a** t/m **l**, typt u:</span><span class="sxs-lookup"><span data-stu-id="d7485-137">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="d7485-138">Veel cmdlets accepteren joker tekens in parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="d7485-138">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="d7485-139">In het Help-onderwerp voor elke cmdlet wordt beschreven welke para meters joker tekens accepteren.</span><span class="sxs-lookup"><span data-stu-id="d7485-139">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="d7485-140">Voor para meters die joker tekens accepteren, is het gebruik niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="d7485-140">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="d7485-141">U kunt joker tekens gebruiken in opdrachten en script blokken, zoals het maken van een Word-patroon dat eigenschaps waarden vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="d7485-141">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="d7485-142">Met de volgende opdracht worden bijvoorbeeld services opgehaald waarin de waarde van de eigenschap **service** type **interactief** is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="d7485-142">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="d7485-143">In het volgende voor beeld `If` bevat de instructie een voor waarde die joker tekens gebruikt om eigenschaps waarden te vinden.</span><span class="sxs-lookup"><span data-stu-id="d7485-143">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="d7485-144">Als de **Beschrijving** van het herstel punt **Power shell** bevat, voegt de opdracht de waarde van de eigenschap **CreationTime** van het herstel punt toe aan een logboek bestand.</span><span class="sxs-lookup"><span data-stu-id="d7485-144">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d7485-145">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="d7485-145">SEE ALSO</span></span>

[<span data-ttu-id="d7485-146">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d7485-146">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="d7485-147">about_If</span><span class="sxs-lookup"><span data-stu-id="d7485-147">about_If</span></span>](about_If.md)

[<span data-ttu-id="d7485-148">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="d7485-148">about_Script_Blocks</span></span>](about_Script_Blocks.md)

