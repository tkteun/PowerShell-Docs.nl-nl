---
title: Alles wat u wilt weten over de if-instructie
description: Net als bij veel andere talen bevat Power shell instructies voor het voorwaardelijk uitvoeren van code in uw scripts.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b6bafb99bfb8ecd0152bae841e5c58d4c27ccd3e
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469749"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a><span data-ttu-id="e5a2c-103">Alles wat u wilt weten over de `if` verklaring</span><span class="sxs-lookup"><span data-stu-id="e5a2c-103">Everything you wanted to know about the `if` statement</span></span>

<span data-ttu-id="e5a2c-104">Net als bij veel andere talen bevat Power shell instructies voor het voorwaardelijk uitvoeren van code in uw scripts.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-104">Like many other languages, PowerShell has statements for conditionally executing code in your scripts.</span></span> <span data-ttu-id="e5a2c-105">Een van deze instructies is de [if][] -instructie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-105">One of those statements is the [If][] statement.</span></span> <span data-ttu-id="e5a2c-106">Vandaag gaan we dieper in op een van de belangrijkste opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-106">Today we will take a deep dive into one of the most fundamental commands in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="e5a2c-107">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="e5a2c-108">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="e5a2c-109">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="e5a2c-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="conditional-execution"></a><span data-ttu-id="e5a2c-110">Voorwaardelijke uitvoering</span><span class="sxs-lookup"><span data-stu-id="e5a2c-110">Conditional execution</span></span>

<span data-ttu-id="e5a2c-111">Uw scripts moeten vaak beslissingen nemen en op basis van deze beslissingen andere logica uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-111">Your scripts often need to make decisions and perform different logic based on those decisions.</span></span>
<span data-ttu-id="e5a2c-112">Dit is wat ik wil zeggen door voorwaardelijke uitvoering.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-112">This is what I mean by conditional execution.</span></span> <span data-ttu-id="e5a2c-113">U hebt één instructie of waarde om te evalueren en vervolgens voert u een andere sectie met code uit op basis van die evaluatie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-113">You have one statement or value to evaluate, then execute a different section of code based on that evaluation.</span></span> <span data-ttu-id="e5a2c-114">Dit is precies wat de `if` instructie doet.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-114">This is exactly what the `if` statement does.</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="e5a2c-115">De `if` instructie</span><span class="sxs-lookup"><span data-stu-id="e5a2c-115">The `if` statement</span></span>

<span data-ttu-id="e5a2c-116">Hier volgt een basis voorbeeld van de- `if` instructie:</span><span class="sxs-lookup"><span data-stu-id="e5a2c-116">Here is a basic example of the `if` statement:</span></span>

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

<span data-ttu-id="e5a2c-117">Het eerste wat de `if` instructie doet, evalueert de expressie tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-117">The first thing the `if` statement does is evaluate the expression in parentheses.</span></span> <span data-ttu-id="e5a2c-118">Als deze wordt geëvalueerd `$true` , worden de `scriptblock` in de accolades uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-118">If it evaluates to `$true`, then it executes the `scriptblock` in the braces.</span></span> <span data-ttu-id="e5a2c-119">Als dit het geval is, wordt de waarde over `$false` die script Block overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-119">If the value was `$false`, then it would skip over that scriptblock.</span></span>

<span data-ttu-id="e5a2c-120">In het vorige voor beeld werd de- `if` instructie gewoon geëvalueerd `$condition` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-120">In the previous example, the `if` statement was just evaluating the `$condition` variable.</span></span> <span data-ttu-id="e5a2c-121">Het was `$true` en heeft de `Write-Output` opdracht in de script Block uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-121">It was `$true` and would have executed the `Write-Output` command inside the scriptblock.</span></span>

<span data-ttu-id="e5a2c-122">In sommige talen kunt u één regel code plaatsen na de `if` instructie en deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-122">In some languages, you can place a single line of code after the `if` statement and it gets executed.</span></span> <span data-ttu-id="e5a2c-123">Dat is niet het geval in Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-123">That isn't the case in PowerShell.</span></span> <span data-ttu-id="e5a2c-124">U moet een volledig `scriptblock` haakje met accolades opgeven om het correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-124">You must provide a full `scriptblock` with braces for it to work correctly.</span></span>

## <a name="comparison-operators"></a><span data-ttu-id="e5a2c-125">Vergelijkingsoperatoren</span><span class="sxs-lookup"><span data-stu-id="e5a2c-125">Comparison operators</span></span>

<span data-ttu-id="e5a2c-126">Het meest voorkomende gebruik van de `if` instructie voor is het vergelijken van twee items met elkaar.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-126">The most common use of the `if` statement for is comparing two items with each other.</span></span> <span data-ttu-id="e5a2c-127">Power Shell heeft speciale Opera tors voor verschillende vergelijkings scenario's.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-127">PowerShell has special operators for different comparison scenarios.</span></span> <span data-ttu-id="e5a2c-128">Wanneer u een vergelijkings operator gebruikt, wordt de waarde aan de linkerkant vergeleken met de waarde aan de rechter kant.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-128">When you use a comparison operator, the value on the left-hand side is compared to the value on the right-hand side.</span></span>

### <a name="-eq-for-equality"></a><span data-ttu-id="e5a2c-129">-EQ voor gelijkheid</span><span class="sxs-lookup"><span data-stu-id="e5a2c-129">-eq for equality</span></span>

<span data-ttu-id="e5a2c-130">De `-eq` voert een gelijkheids controle tussen twee waarden uit om ervoor te zorgen dat ze gelijk zijn aan elkaar.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-130">The `-eq` does an equality check between two values to make sure they're equal to each other.</span></span>

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

<span data-ttu-id="e5a2c-131">In dit voor beeld maken we een bekende waarde van `5` en vergelijken deze met mijn `$value` om te zien of ze overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-131">In this example, I'm taking a known value of `5` and comparing it to my `$value` to see if they match.</span></span>

<span data-ttu-id="e5a2c-132">Een mogelijke use-case is het controleren van de status van een waarde voordat u een actie onderneemt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-132">One possible use case is to check the status of a value before you take an action on it.</span></span> <span data-ttu-id="e5a2c-133">U kunt een service ophalen en controleren of de status werd uitgevoerd voordat u deze aanroept `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-133">You could get a service and check that the status was running before you called `Restart-Service` on it.</span></span>

<span data-ttu-id="e5a2c-134">Het is gebruikelijk in andere talen als C# om te gebruiken `==` voor gelijkheid (bijvoorbeeld: `5 == $value` ), maar dat werkt niet met Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-134">It's common in other languages like C# to use `==` for equality (ex: `5 == $value`) but that doesn't work with PowerShell.</span></span> <span data-ttu-id="e5a2c-135">Een andere veelvoorkomende fout die gebruikers doen, is het gelijkteken (bijvoorbeeld) te gebruiken `5 = $value` dat is gereserveerd voor het toewijzen van waarden aan variabelen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-135">Another common mistake that people make is to use the equals sign (ex: `5 = $value`) that is reserved for assigning values to variables.</span></span> <span data-ttu-id="e5a2c-136">Als u de bekende waarde aan de linkerkant plaatst, wordt deze fout meer vreemd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-136">By placing your known value on the left, it makes that mistake more awkward to make.</span></span>

<span data-ttu-id="e5a2c-137">Deze operator (en andere) heeft enkele variaties.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-137">This operator (and others) has a few variations.</span></span>

- <span data-ttu-id="e5a2c-138">`-eq` hoofdletter gevoelig gelijkheid</span><span class="sxs-lookup"><span data-stu-id="e5a2c-138">`-eq` case-insensitive equality</span></span>
- <span data-ttu-id="e5a2c-139">`-ieq` hoofdletter gevoelig gelijkheid</span><span class="sxs-lookup"><span data-stu-id="e5a2c-139">`-ieq` case-insensitive equality</span></span>
- <span data-ttu-id="e5a2c-140">`-ceq` hoofdletter gevoelige gelijkheid</span><span class="sxs-lookup"><span data-stu-id="e5a2c-140">`-ceq` case-sensitive equality</span></span>

### <a name="-ne-not-equal"></a><span data-ttu-id="e5a2c-141">-ne niet gelijk</span><span class="sxs-lookup"><span data-stu-id="e5a2c-141">-ne not equal</span></span>

<span data-ttu-id="e5a2c-142">Veel opera tors hebben een gerelateerde operator die het tegenovergestelde resultaat controleren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-142">Many operators have a related operator that is checking for the opposite result.</span></span> <span data-ttu-id="e5a2c-143">`-ne` verifieert of de waarden niet gelijk zijn aan elkaar.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-143">`-ne` verifies that the values don't equal each other.</span></span>

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

<span data-ttu-id="e5a2c-144">Gebruik deze methode om ervoor te zorgen dat de actie alleen wordt uitgevoerd als de waarde niet is `5` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-144">Use this to make sure that the action only executes if the value isn't `5`.</span></span> <span data-ttu-id="e5a2c-145">Een goed gebruik: gevallen waarin u kunt controleren of een service de status actief heeft voordat u deze probeert te starten.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-145">A good use-cases where would be to check if a service was in the running state before you try to start it.</span></span>

<span data-ttu-id="e5a2c-146">**Verschillen**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-146">**Variations:**</span></span>

- <span data-ttu-id="e5a2c-147">`-ne` niet hoofdletter gevoelig niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="e5a2c-147">`-ne` case-insensitive not equal</span></span>
- <span data-ttu-id="e5a2c-148">`-ine` niet hoofdletter gevoelig niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="e5a2c-148">`-ine` case-insensitive not equal</span></span>
- <span data-ttu-id="e5a2c-149">`-cne` hoofdletter gevoelig niet gelijk</span><span class="sxs-lookup"><span data-stu-id="e5a2c-149">`-cne` case-sensitive not equal</span></span>

<span data-ttu-id="e5a2c-150">Dit zijn inverse variaties van `-eq` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-150">These are inverse variations of `-eq`.</span></span> <span data-ttu-id="e5a2c-151">Ik Groepeer deze typen samen wanneer ik variaties voor andere opera tors vermeld.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-151">I'll group these types together when I list variations for other operators.</span></span>

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a><span data-ttu-id="e5a2c-152">-gt-ge-lt-Le voor groter dan of kleiner dan</span><span class="sxs-lookup"><span data-stu-id="e5a2c-152">-gt -ge -lt -le for greater than or less than</span></span>

<span data-ttu-id="e5a2c-153">Deze opera tors worden gebruikt bij het controleren of een waarde groter of kleiner dan een andere waarde is.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-153">These operators are used when checking to see if a value is larger or smaller than another value.</span></span>
<span data-ttu-id="e5a2c-154">De `-gt -ge -lt -le` standaard voor GreaterThan, GreaterThanOrEqual, LessThan en LessThanOrEqual.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-154">The `-gt -ge -lt -le` stand for GreaterThan, GreaterThanOrEqual, LessThan, and LessThanOrEqual.</span></span>

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

<span data-ttu-id="e5a2c-155">**Verschillen**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-155">**Variations:**</span></span>

- <span data-ttu-id="e5a2c-156">`-gt` groter dan</span><span class="sxs-lookup"><span data-stu-id="e5a2c-156">`-gt` greater than</span></span>
- <span data-ttu-id="e5a2c-157">`-igt` groter dan, niet hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-157">`-igt` greater than, case-insensitive</span></span>
- <span data-ttu-id="e5a2c-158">`-cgt` groter dan, hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-158">`-cgt` greater than, case-sensitive</span></span>
- <span data-ttu-id="e5a2c-159">`-ge` groter dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="e5a2c-159">`-ge` greater than or equal</span></span>
- <span data-ttu-id="e5a2c-160">`-ige` groter dan of gelijk aan, niet hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-160">`-ige` greater than or equal, case-insensitive</span></span>
- <span data-ttu-id="e5a2c-161">`-cge` groter dan of gelijk aan, hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-161">`-cge` greater than or equal, case-sensitive</span></span>
- <span data-ttu-id="e5a2c-162">`-lt` kleiner dan</span><span class="sxs-lookup"><span data-stu-id="e5a2c-162">`-lt` less than</span></span>
- <span data-ttu-id="e5a2c-163">`-ilt` kleiner dan, niet hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-163">`-ilt` less than, case-insensitive</span></span>
- <span data-ttu-id="e5a2c-164">`-clt` kleiner dan, hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-164">`-clt` less than, case-sensitive</span></span>
- <span data-ttu-id="e5a2c-165">`-le` kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="e5a2c-165">`-le` less than or equal</span></span>
- <span data-ttu-id="e5a2c-166">`-ile` kleiner dan of gelijk aan, niet hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-166">`-ile` less than or equal, case-insensitive</span></span>
- <span data-ttu-id="e5a2c-167">`-cle` kleiner dan of gelijk aan, hoofdletter gevoelig</span><span class="sxs-lookup"><span data-stu-id="e5a2c-167">`-cle` less than or equal, case-sensitive</span></span>

<span data-ttu-id="e5a2c-168">Ik weet niet waarom u hoofdletter gevoelige en ingevoelige opties zou gebruiken voor deze opera tors.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-168">I don't know why you would use case-sensitive and insensitive options for these operators.</span></span>

### <a name="-like-wildcard-matches"></a><span data-ttu-id="e5a2c-169">vergelijkbaar met Joker tekens</span><span class="sxs-lookup"><span data-stu-id="e5a2c-169">-like wildcard matches</span></span>

<span data-ttu-id="e5a2c-170">Power Shell heeft een eigen syntaxis op basis van joker tekens die overeenkomt en u kunt deze gebruiken met de `-like` operator.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-170">PowerShell has its own wildcard-based pattern matching syntax and you can use it with the `-like` operator.</span></span> <span data-ttu-id="e5a2c-171">Deze Joker teken patronen zijn redelijk eenvoudig.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-171">These wildcard patterns are fairly basic.</span></span>

- <span data-ttu-id="e5a2c-172">`?` komt overeen met één wille keurig teken</span><span class="sxs-lookup"><span data-stu-id="e5a2c-172">`?` matches any single character</span></span>
- <span data-ttu-id="e5a2c-173">`*` komt overeen met een wille keurig aantal tekens</span><span class="sxs-lookup"><span data-stu-id="e5a2c-173">`*` matches any number of characters</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

<span data-ttu-id="e5a2c-174">Het is belang rijk om te wijzen dat het patroon overeenkomt met de hele teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-174">It's important to point out that the pattern matches the whole string.</span></span> <span data-ttu-id="e5a2c-175">Als u iets in het midden van de teken reeks moet overeenkomen, moet u de `*` aan beide uiteinden van de teken reeks plaatsen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-175">If you need to match something in the middle of the string, you need to place the `*` on both ends of the string.</span></span>

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

<span data-ttu-id="e5a2c-176">**Verschillen**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-176">**Variations:**</span></span>

- <span data-ttu-id="e5a2c-177">`-like` hoofdletter gevoelig Joker teken</span><span class="sxs-lookup"><span data-stu-id="e5a2c-177">`-like` case-insensitive wildcard</span></span>
- <span data-ttu-id="e5a2c-178">`-ilike` hoofdletter gevoelig Joker teken</span><span class="sxs-lookup"><span data-stu-id="e5a2c-178">`-ilike` case-insensitive wildcard</span></span>
- <span data-ttu-id="e5a2c-179">`-clike` hoofdletter gevoelig Joker teken</span><span class="sxs-lookup"><span data-stu-id="e5a2c-179">`-clike` case-sensitive wildcard</span></span>
- <span data-ttu-id="e5a2c-180">`-notlike` hoofdletter gevoelig Joker teken niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-180">`-notlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="e5a2c-181">`-inotlike` hoofdletter gevoelig Joker teken niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-181">`-inotlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="e5a2c-182">`-cnotlike` hoofdletter gevoelige joker tekens komen niet overeen</span><span class="sxs-lookup"><span data-stu-id="e5a2c-182">`-cnotlike` case-sensitive wildcard not matched</span></span>

### <a name="-match-regular-expression"></a><span data-ttu-id="e5a2c-183">-overeenkomende reguliere expressie</span><span class="sxs-lookup"><span data-stu-id="e5a2c-183">-match regular expression</span></span>

<span data-ttu-id="e5a2c-184">`-match`Met de operator kunt u een teken reeks controleren op basis van een overeenkomst met een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-184">The `-match` operator allows you to check a string for a regular-expression-based match.</span></span> <span data-ttu-id="e5a2c-185">Gebruik deze wanneer de Joker teken patronen niet flexibel genoeg zijn voor u.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-185">Use this when the wildcard patterns aren't flexible enough for you.</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

<span data-ttu-id="e5a2c-186">Een regex-patroon komt standaard overeen met een wille keurige plaats in de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-186">A regex pattern matches anywhere in the string by default.</span></span> <span data-ttu-id="e5a2c-187">U kunt dus een subtekenreeks opgeven die overeenkomt met de volgende:</span><span class="sxs-lookup"><span data-stu-id="e5a2c-187">So you can specify a substring that you want matched like this:</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

<span data-ttu-id="e5a2c-188">Regex is een complexe taal van eigen talen en is aan het kijken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-188">Regex is a complex language of its own and worth looking into.</span></span> <span data-ttu-id="e5a2c-189">Ik spreek meer over `-match` en [de vele manieren om regex te gebruiken][] in een ander artikel.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-189">I talk more about `-match` and [the many ways to use regex][] in another article.</span></span>

<span data-ttu-id="e5a2c-190">**Verschillen**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-190">**Variations:**</span></span>

- <span data-ttu-id="e5a2c-191">`-match` hoofdletter gevoelige regex</span><span class="sxs-lookup"><span data-stu-id="e5a2c-191">`-match` case-insensitive regex</span></span>
- <span data-ttu-id="e5a2c-192">`-imatch` hoofdletter gevoelige regex</span><span class="sxs-lookup"><span data-stu-id="e5a2c-192">`-imatch` case-insensitive regex</span></span>
- <span data-ttu-id="e5a2c-193">`-cmatch` hoofdletter gevoelige regex</span><span class="sxs-lookup"><span data-stu-id="e5a2c-193">`-cmatch` case-sensitive regex</span></span>
- <span data-ttu-id="e5a2c-194">`-notmatch` hoofdletter gebruik: ongevoelige regex komt niet overeen</span><span class="sxs-lookup"><span data-stu-id="e5a2c-194">`-notmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="e5a2c-195">`-inotmatch` hoofdletter gebruik: ongevoelige regex komt niet overeen</span><span class="sxs-lookup"><span data-stu-id="e5a2c-195">`-inotmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="e5a2c-196">`-cnotmatch` hoofdletter gevoelige regex niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-196">`-cnotmatch` case-sensitive regex not matched</span></span>

### <a name="-is-of-type"></a><span data-ttu-id="e5a2c-197">-is van het type</span><span class="sxs-lookup"><span data-stu-id="e5a2c-197">-is of type</span></span>

<span data-ttu-id="e5a2c-198">U kunt het type van een waarde controleren met de `-is` operator.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-198">You can check a value's type with the `-is` operator.</span></span>

```powershell
if ( $value -is [string] )
{
    # do something
}
```

<span data-ttu-id="e5a2c-199">U kunt dit gebruiken als u met klassen werkt of verschillende objecten via de pijp lijn accepteert.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-199">You may use this if you're working with classes or accepting various objects over the pipeline.</span></span> <span data-ttu-id="e5a2c-200">U kunt een service-of service naam als invoer hebben.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-200">You could have either a service or a service name as your input.</span></span> <span data-ttu-id="e5a2c-201">Controleer vervolgens of u een service hebt en haal de service op als u alleen de naam hebt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-201">Then check to see if you have a service and fetch the service if you only have the name.</span></span>

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

<span data-ttu-id="e5a2c-202">**Verschillen**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-202">**Variations:**</span></span>

- <span data-ttu-id="e5a2c-203">`-is` van het type</span><span class="sxs-lookup"><span data-stu-id="e5a2c-203">`-is` of type</span></span>
- <span data-ttu-id="e5a2c-204">`-isnot` niet van het type</span><span class="sxs-lookup"><span data-stu-id="e5a2c-204">`-isnot` not of type</span></span>

## <a name="collection-operators"></a><span data-ttu-id="e5a2c-205">Verzamelings operators</span><span class="sxs-lookup"><span data-stu-id="e5a2c-205">Collection operators</span></span>

<span data-ttu-id="e5a2c-206">Wanneer u de vorige Opera tors met één waarde gebruikt, is dit het `$true` resultaat `$false` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-206">When you use the previous operators with a single value, the result is `$true` or `$false`.</span></span> <span data-ttu-id="e5a2c-207">Dit wordt iets anders behandeld bij het werken met een verzameling.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-207">This is handled slightly differently when working with a collection.</span></span> <span data-ttu-id="e5a2c-208">Elk item in de verzameling wordt geëvalueerd en de operator retourneert elke waarde die wordt geëvalueerd `$true` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-208">Each item in the collection gets evaluated and the operator returns every value that evaluates to `$true`.</span></span>

```powershell
PS> 1,2,3,4 -eq 3
3
```

<span data-ttu-id="e5a2c-209">Dit werkt nog steeds goed in een- `if` instructie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-209">This still works correctly in a `if` statement.</span></span> <span data-ttu-id="e5a2c-210">Daarom wordt er een waarde geretourneerd door uw operator, waarna de volledige instructie wordt weer gegeven `$true` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-210">So a value is returned by your operator, then the whole statement is `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

<span data-ttu-id="e5a2c-211">Er is een kleine trap die in de details wordt weer gegeven, die ik moet afwijzen. Wanneer u de `-ne` operator op deze manier gebruikt, is het eenvoudig om de logica achterwaarts te bekijken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-211">There's one small trap hiding in the details here that I need to point out. When using the `-ne` operator this way, it's easy to mistakenly look at the logic backwards.</span></span> <span data-ttu-id="e5a2c-212">Gebruiken `-ne` met een verzameling retourneert `$true` als een item in de verzameling niet overeenkomt met uw waarde.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-212">Using `-ne` with a collection returns `$true` if any item in the collection doesn't match your value.</span></span>

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

<span data-ttu-id="e5a2c-213">Dit ziet eruit als een slimme truc, maar we hebben Opera tors `-contains` en `-in` die dit efficiënter afhandelen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-213">This may look like a clever trick, but we have operators `-contains` and `-in` that handle this more efficiently.</span></span> <span data-ttu-id="e5a2c-214">En `-notcontains` wat u verwacht.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-214">And `-notcontains` does what you expect.</span></span>

### <a name="-contains"></a><span data-ttu-id="e5a2c-215">-contains</span><span class="sxs-lookup"><span data-stu-id="e5a2c-215">-contains</span></span>

<span data-ttu-id="e5a2c-216">De `-contains` operator controleert de verzameling op uw waarde.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-216">The `-contains` operator checks the collection for your value.</span></span> <span data-ttu-id="e5a2c-217">Zodra er een overeenkomst wordt gevonden, wordt deze geretourneerd `$true` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-217">As soon as it finds a match, it returns `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

<span data-ttu-id="e5a2c-218">Dit is de aanbevolen manier om te zien of een verzameling uw waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-218">This is the preferred way to see if a collection contains your value.</span></span> <span data-ttu-id="e5a2c-219">Met `Where-Object` (of `-eq` ) wordt de volledige lijst elke keer door lopen en is deze aanzienlijk langzamer.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-219">Using `Where-Object` (or `-eq`) walks the entire list every time and is significantly slower.</span></span>

<span data-ttu-id="e5a2c-220">**Verschillen**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-220">**Variations:**</span></span>

- <span data-ttu-id="e5a2c-221">`-contains` hoofdletter gevoelig overeenkomst</span><span class="sxs-lookup"><span data-stu-id="e5a2c-221">`-contains` case-insensitive match</span></span>
- <span data-ttu-id="e5a2c-222">`-icontains` hoofdletter gevoelig overeenkomst</span><span class="sxs-lookup"><span data-stu-id="e5a2c-222">`-icontains` case-insensitive match</span></span>
- <span data-ttu-id="e5a2c-223">`-ccontains` hoofdletter gevoelige overeenkomst</span><span class="sxs-lookup"><span data-stu-id="e5a2c-223">`-ccontains` case-sensitive match</span></span>
- <span data-ttu-id="e5a2c-224">`-notcontains` niet hoofdletter gevoelig niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-224">`-notcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="e5a2c-225">`-inotcontains` niet hoofdletter gevoelig niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-225">`-inotcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="e5a2c-226">`-cnotcontains` hoofdletter gevoelig niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-226">`-cnotcontains` case-sensitive not matched</span></span>

### <a name="-in"></a><span data-ttu-id="e5a2c-227">-in</span><span class="sxs-lookup"><span data-stu-id="e5a2c-227">-in</span></span>

<span data-ttu-id="e5a2c-228">De operator bevindt `-in` zich net als de `-contains` operator, behalve dat de verzameling zich aan de rechter kant bevindt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-228">The `-in` operator is just like the `-contains` operator except the collection is on the right-hand side.</span></span>

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

<span data-ttu-id="e5a2c-229">**Verschillen**</span><span class="sxs-lookup"><span data-stu-id="e5a2c-229">**Variations:**</span></span>

- <span data-ttu-id="e5a2c-230">`-in` hoofdletter gevoelig overeenkomst</span><span class="sxs-lookup"><span data-stu-id="e5a2c-230">`-in` case-insensitive match</span></span>
- <span data-ttu-id="e5a2c-231">`-iin` hoofdletter gevoelig overeenkomst</span><span class="sxs-lookup"><span data-stu-id="e5a2c-231">`-iin` case-insensitive match</span></span>
- <span data-ttu-id="e5a2c-232">`-cin` hoofdletter gevoelige overeenkomst</span><span class="sxs-lookup"><span data-stu-id="e5a2c-232">`-cin` case-sensitive match</span></span>
- <span data-ttu-id="e5a2c-233">`-notin` niet hoofdletter gevoelig niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-233">`-notin` case-insensitive not matched</span></span>
- <span data-ttu-id="e5a2c-234">`-inotin` niet hoofdletter gevoelig niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-234">`-inotin` case-insensitive not matched</span></span>
- <span data-ttu-id="e5a2c-235">`-cnotin` hoofdletter gevoelig niet gevonden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-235">`-cnotin` case-sensitive not matched</span></span>

## <a name="logical-operators"></a><span data-ttu-id="e5a2c-236">Logische operators</span><span class="sxs-lookup"><span data-stu-id="e5a2c-236">Logical operators</span></span>

<span data-ttu-id="e5a2c-237">Logische Opera tors worden gebruikt om andere expressies om te draaien of te combi neren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-237">Logical operators are used to invert or combine other expressions.</span></span>

### <a name="-not"></a><span data-ttu-id="e5a2c-238">-niet</span><span class="sxs-lookup"><span data-stu-id="e5a2c-238">-not</span></span>

<span data-ttu-id="e5a2c-239">De `-not` operator spiegelt een expressie van `$false` naar `$true` of van `$true` naar `$false` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-239">The `-not` operator flips an expression from `$false` to `$true` or from `$true` to `$false`.</span></span> <span data-ttu-id="e5a2c-240">Hier volgt een voor beeld waarin we een actie willen uitvoeren wanneer dat het geval `Test-Path` is `$false` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-240">Here is an example where we want to perform an action when `Test-Path` is `$false`.</span></span>

```powershell
if ( -not ( Test-Path -Path $path ) )
```

<span data-ttu-id="e5a2c-241">De meeste Opera tors die ons hebben besproken hebben een variant waarin u de operator niet hoeft te gebruiken `-not` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-241">Most of the operators we talked about do have a variation where you do not need to use the `-not` operator.</span></span> <span data-ttu-id="e5a2c-242">Het is echter nog steeds handig.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-242">But there are still times it is useful.</span></span>

### <a name="-operator"></a><span data-ttu-id="e5a2c-243">!</span><span class="sxs-lookup"><span data-stu-id="e5a2c-243">!</span></span> <span data-ttu-id="e5a2c-244">operator</span><span class="sxs-lookup"><span data-stu-id="e5a2c-244">operator</span></span>

<span data-ttu-id="e5a2c-245">U kunt gebruiken `!` als een alias voor `-not` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-245">You can use `!` as an alias for `-not`.</span></span>

```powershell
if ( -not $value ){}
if ( !$value ){}
```

<span data-ttu-id="e5a2c-246">U ziet mogelijk `!` meer voor mensen die afkomstig zijn uit andere talen, zoals C#.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-246">You may see `!` used more by people that come from another languages like C#.</span></span> <span data-ttu-id="e5a2c-247">Ik wil het beste typen, omdat ik het moeilijk kan zien wanneer ik snel naar mijn scripts zoek.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-247">I prefer to type it out because I find it hard to see when quickly looking at my scripts.</span></span>

### <a name="-and"></a><span data-ttu-id="e5a2c-248">-en</span><span class="sxs-lookup"><span data-stu-id="e5a2c-248">-and</span></span>

<span data-ttu-id="e5a2c-249">U kunt expressies combi neren met de `-and` operator.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-249">You can combine expressions with the `-and` operator.</span></span> <span data-ttu-id="e5a2c-250">Wanneer u dat doet, moeten beide zijden `$true` van de hele expressie zijn `$true` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-250">When you do that, both sides need to be `$true` for the whole expression to be `$true`.</span></span>

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

<span data-ttu-id="e5a2c-251">In dit voor beeld `$age` moet de linkerkant 13 of ouder zijn en kleiner dan 55 voor de rechter kant.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-251">In that example, `$age` must be 13 or older for the left side and less than 55 for the right side.</span></span> <span data-ttu-id="e5a2c-252">Ik heb extra haakjes toegevoegd om het voor beeld duidelijker te maken, maar ze zijn optioneel, zolang de expressie eenvoudig is.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-252">I added extra parentheses to make it clearer in that example but they're optional as long as the expression is simple.</span></span> <span data-ttu-id="e5a2c-253">Hier volgt hetzelfde voor beeld zonder deze.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-253">Here is the same example without them.</span></span>

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

<span data-ttu-id="e5a2c-254">De evaluatie vindt plaats van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-254">Evaluation happens from left to right.</span></span> <span data-ttu-id="e5a2c-255">Als het eerste item wordt geëvalueerd naar `$false` , wordt het vroegtijdig afgesloten en wordt de juiste vergelijking niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-255">If the first item evaluates to `$false`, it exits early and doesn't perform the right comparison.</span></span> <span data-ttu-id="e5a2c-256">Dit is handig wanneer u er zeker van wilt zijn dat er een waarde bestaat voordat u deze gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-256">This is handy when you need to make sure a value exists before you use it.</span></span> <span data-ttu-id="e5a2c-257">`Test-Path`Als u bijvoorbeeld een pad geeft, treedt er een fout op `$null` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-257">For example, `Test-Path` throws an error if you give it a `$null` path.</span></span>

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a><span data-ttu-id="e5a2c-258">-of</span><span class="sxs-lookup"><span data-stu-id="e5a2c-258">-or</span></span>

<span data-ttu-id="e5a2c-259">`-or`Op die manier kunt u twee expressies opgeven en wordt geretourneerd `$true` als er een van beide wordt weer gegeven `$true` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-259">The `-or` allows for you to specify two expressions and returns `$true` if either one of them is `$true`.</span></span>

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

<span data-ttu-id="e5a2c-260">Net als bij de `-and` operator is de evaluatie van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-260">Just like with the `-and` operator, the evaluation happens from left to right.</span></span> <span data-ttu-id="e5a2c-261">Behalve dat als het eerste deel is `$true` , is het hele overzicht `$true` en wordt de rest van de expressie niet verwerkt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-261">Except that if the first part is `$true`, then the whole statement is `$true` and it doesn't process the rest of the expression.</span></span>

<span data-ttu-id="e5a2c-262">Houd er ook rekening mee dat de syntaxis voor deze opera tors werkt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-262">Also make note of how the syntax works for these operators.</span></span> <span data-ttu-id="e5a2c-263">U hebt twee afzonderlijke expressies nodig.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-263">You need two separate expressions.</span></span> <span data-ttu-id="e5a2c-264">Ik heb gezien dat gebruikers iets anders proberen te doen, `$value -eq 5 -or 6` zonder hun fout te realiseren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-264">I have seen users try to do something like this `$value -eq 5 -or 6` without realizing their mistake.</span></span>

### <a name="-xor-exclusive-or"></a><span data-ttu-id="e5a2c-265">-XOR exclusieve of</span><span class="sxs-lookup"><span data-stu-id="e5a2c-265">-xor exclusive or</span></span>

<span data-ttu-id="e5a2c-266">Dit is een beetje ongebruikelijk.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-266">This one is a little unusual.</span></span> <span data-ttu-id="e5a2c-267">`-xor` Hiermee kan slechts één expressie worden geëvalueerd `$true` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-267">`-xor` allows only one expression to evaluate to `$true`.</span></span> <span data-ttu-id="e5a2c-268">Dus als beide items `$false` of beide items zijn `$true` , is de hele expressie `$false` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-268">So if both items are `$false` or both items are `$true`, then the whole expression is `$false`.</span></span> <span data-ttu-id="e5a2c-269">Een andere manier om dit te bekijken is de expressie alleen `$true` wanneer de resultaten van de expressie verschillend zijn.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-269">Another way to look at this is the expression is only `$true` when the results of the expression are different.</span></span>

<span data-ttu-id="e5a2c-270">Het komt zelden voor dat iedereen deze logische operator zou gebruiken en ik niet op de juiste manier kan zien waarom ik deze ooit zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-270">It's rare that anyone would ever use this logical operator and I can't think up a good example as to why I would ever use it.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="e5a2c-271">Bitsgewijze operatoren</span><span class="sxs-lookup"><span data-stu-id="e5a2c-271">Bitwise operators</span></span>

<span data-ttu-id="e5a2c-272">Bitsgewijze Opera tors voeren berekeningen uit op de bits binnen de waarden en produceren een nieuwe waarde als resultaat.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-272">Bitwise operators perform calculations on the bits within the values and produce a new value as the result.</span></span> <span data-ttu-id="e5a2c-273">Leer [bitsgewijze Opera tors][] vallen buiten het bereik van dit artikel, maar dit is de lijst.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-273">Teaching [bitwise operators][] is beyond the scope of this article, but here is the list the them.</span></span>

- <span data-ttu-id="e5a2c-274">`-band` binaire en</span><span class="sxs-lookup"><span data-stu-id="e5a2c-274">`-band` binary AND</span></span>
- <span data-ttu-id="e5a2c-275">`-bor` binair of</span><span class="sxs-lookup"><span data-stu-id="e5a2c-275">`-bor` binary OR</span></span>
- <span data-ttu-id="e5a2c-276">`-bxor` binaire exclusieve of</span><span class="sxs-lookup"><span data-stu-id="e5a2c-276">`-bxor` binary exclusive OR</span></span>
- <span data-ttu-id="e5a2c-277">`-bnot` binair niet</span><span class="sxs-lookup"><span data-stu-id="e5a2c-277">`-bnot` binary NOT</span></span>
- <span data-ttu-id="e5a2c-278">`-shl` Shift-links</span><span class="sxs-lookup"><span data-stu-id="e5a2c-278">`-shl` shift left</span></span>
- <span data-ttu-id="e5a2c-279">`-shr` naar rechts verplaatsen</span><span class="sxs-lookup"><span data-stu-id="e5a2c-279">`-shr` shift right</span></span>

## <a name="powershell-expressions"></a><span data-ttu-id="e5a2c-280">Power shell-expressies</span><span class="sxs-lookup"><span data-stu-id="e5a2c-280">PowerShell expressions</span></span>

<span data-ttu-id="e5a2c-281">U kunt normaal Power shell gebruiken in de voor waarde-instructie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-281">We can use normal PowerShell inside the condition statement.</span></span>

```powershell
if ( Test-Path -Path $Path )
```

<span data-ttu-id="e5a2c-282">`Test-Path` retourneert `$true` of `$false` wanneer deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-282">`Test-Path` returns `$true` or `$false` when it executes.</span></span> <span data-ttu-id="e5a2c-283">Dit geldt ook voor opdrachten die andere waarden retour neren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-283">This also applies to commands that return other values.</span></span>

```powershell
if ( Get-Process Notepad* )
```

<span data-ttu-id="e5a2c-284">`$true`Als er een proces wordt geretourneerd, wordt het geëvalueerd als `$false` there'sn'thing.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-284">It evaluates to `$true` if there's a returned process and `$false` if there'sn'thing.</span></span> <span data-ttu-id="e5a2c-285">Het is volledig geldig om pijplijn expressies of andere Power shell-instructies te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="e5a2c-285">It's perfectly valid to use pipeline expressions or other PowerShell statements like this:</span></span>

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

<span data-ttu-id="e5a2c-286">Deze expressies kunnen met elkaar worden gecombineerd met de `-and` `-or` Opera tors en, maar u kunt ook haakjes gebruiken om ze in subexpressies te splitsen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-286">These expressions can be combined with each other with the `-and` and `-or` operators, but you may have to use parenthesis to break them into subexpressions.</span></span>

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a><span data-ttu-id="e5a2c-287">Controleren op $null</span><span class="sxs-lookup"><span data-stu-id="e5a2c-287">Checking for $null</span></span>

<span data-ttu-id="e5a2c-288">`$null`Als er `$false` in de instructie geen resultaat of een waarde wordt geëvalueerd `if` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-288">Having a no result or a `$null` value evaluates to `$false` in the `if` statement.</span></span> <span data-ttu-id="e5a2c-289">Bij het controleren van `$null` de specifiek voor is het een best practice om de `$null` aan de linkerkant te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-289">When checking specifically for `$null`, it's a best practice to place the `$null` on the left-hand side.</span></span>

```powershell
if ( $null -eq $value )
```

<span data-ttu-id="e5a2c-290">Er zijn zeer enkele nuances voor het omgaan met `$null` waarden in Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-290">There are quite a few nuances when dealing with `$null` values in PowerShell.</span></span> <span data-ttu-id="e5a2c-291">Als u geïnteresseerd bent in een diep gaande, heb ik een artikel over [Alles wat je van $Null zou weten te][]komen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-291">If you're interested in diving deeper, I have an article about [everything you wanted to know about $null][].</span></span>

### <a name="variable-assignment"></a><span data-ttu-id="e5a2c-292">Variabele toewijzing</span><span class="sxs-lookup"><span data-stu-id="e5a2c-292">Variable assignment</span></span>

<span data-ttu-id="e5a2c-293">Ik ben bijna klaar om deze toe te voegen tot [Prasoon Karunan V][] eraan herinneren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-293">I almost forgot to add this one until [Prasoon Karunan V][] reminded me of it.</span></span>

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

<span data-ttu-id="e5a2c-294">Normaal gesp roken wanneer u een waarde aan een variabele toewijst, wordt de waarde niet door gegeven aan de pijp lijn of de console.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-294">Normally when you assign a value to a variable, the value isn't passed onto the pipeline or console.</span></span> <span data-ttu-id="e5a2c-295">Wanneer u een variabele toewijzing in een sub-expressie doet, wordt deze door gegeven aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-295">When you do a variable assignment in a sub expression, it does get passed on to the pipeline.</span></span>

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

<span data-ttu-id="e5a2c-296">Zie hoe de `$first` toewijzing geen uitvoer heeft en de `$second` toewijzing?</span><span class="sxs-lookup"><span data-stu-id="e5a2c-296">See how the `$first` assignment has no output and the `$second` assignment does?</span></span> <span data-ttu-id="e5a2c-297">Wanneer een toewijzing wordt uitgevoerd in een `if` instructie, wordt deze uitgevoerd op dezelfde manier als de `$second` bovenstaande toewijzing.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-297">When an assignment is done in an `if` statement, it executes just like the `$second` assignment above.</span></span> <span data-ttu-id="e5a2c-298">Hier volgt een voor beeld van hoe u het kunt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="e5a2c-298">Here is a clean example on how you could use it:</span></span>

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

<span data-ttu-id="e5a2c-299">Als `$process` wordt toegewezen aan een waarde, wordt de instructie `$true` beëindigd en wordt `$process` deze gestopt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-299">If `$process` gets assigned a value, then the statement is `$true` and `$process` gets stopped.</span></span>

<span data-ttu-id="e5a2c-300">Zorg ervoor dat u dit niet verwart met `-eq` omdat dit geen gelijkheids controle is.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-300">Make sure you don't confuse this with `-eq` because this isn't an equality check.</span></span> <span data-ttu-id="e5a2c-301">Dit is een meer bedekkende functie die de meeste mensen niet op deze manier kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-301">This is a more obscure feature that most people don't realize works this way.</span></span>

## <a name="alternate-execution-path"></a><span data-ttu-id="e5a2c-302">Alternatief pad voor uitvoering</span><span class="sxs-lookup"><span data-stu-id="e5a2c-302">Alternate execution path</span></span>

<span data-ttu-id="e5a2c-303">Met de- `if` instructie kunt u een actie voor niet alleen opgeven als de instructie `$true` , maar ook voor wanneer deze is `$false` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-303">The `if` statement allows you to specify an action for not only when the statement is `$true`, but also for when it's `$false`.</span></span> <span data-ttu-id="e5a2c-304">Hier `else` komt de instructie af.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-304">This is where the `else` statement comes into play.</span></span>

### <a name="else"></a><span data-ttu-id="e5a2c-305">else</span><span class="sxs-lookup"><span data-stu-id="e5a2c-305">else</span></span>

<span data-ttu-id="e5a2c-306">De `else` instructie is altijd het laatste deel van de `if` instructie wanneer deze wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-306">The `else` statement is always the last part of the `if` statement when used.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

<span data-ttu-id="e5a2c-307">In dit voor beeld controleren we de `$path` om er zeker van te zijn dat het een bestand is.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-307">In this example, we check the `$path` to make sure it's a file.</span></span> <span data-ttu-id="e5a2c-308">Als we het bestand vinden, verplaatsen we het.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-308">If we find the file, we move it.</span></span> <span data-ttu-id="e5a2c-309">Als dat niet het geval is, wordt er een waarschuwing geschreven.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-309">If not, we write a warning.</span></span> <span data-ttu-id="e5a2c-310">Dit type vertakkings logica is zeer gebruikelijk.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-310">This type of branching logic is very common.</span></span>

### <a name="nested-if"></a><span data-ttu-id="e5a2c-311">Genest als</span><span class="sxs-lookup"><span data-stu-id="e5a2c-311">Nested if</span></span>

<span data-ttu-id="e5a2c-312">De `if` `else` instructies and maken een script blok, zodat we een Power shell-opdracht in de and kunnen plaatsen, met inbegrip van een andere `if` instructie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-312">The `if` and `else` statements take a script block, so we can place any PowerShell command inside them, including another `if` statement.</span></span> <span data-ttu-id="e5a2c-313">Zo kunt u veel gecompliceerdere logica gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-313">This allows you to make use of much more complicated logic.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

<span data-ttu-id="e5a2c-314">In dit voor beeld testen we het pad blij eerst en vervolgens onderneemt u actie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-314">In this example, we test the happy path first and then take action on it.</span></span> <span data-ttu-id="e5a2c-315">Als dat niet lukt, voert u een andere controle uit en geeft u meer gedetailleerde informatie aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-315">If that fails, we do another check and to provide more detailed information to the user.</span></span>

### <a name="elseif"></a><span data-ttu-id="e5a2c-316">elseif</span><span class="sxs-lookup"><span data-stu-id="e5a2c-316">elseif</span></span>

<span data-ttu-id="e5a2c-317">We zijn niet beperkt tot slechts één voorwaardelijke controle.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-317">We aren't limited to just a single conditional check.</span></span> <span data-ttu-id="e5a2c-318">We kunnen `if` `else` de instructies en overzichten samen voegen in plaats van ze te nesten met behulp van de- `elseif` instructie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-318">We can chain `if` and `else` statements together instead of nesting them by using the `elseif` statement.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

<span data-ttu-id="e5a2c-319">De uitvoering vindt plaats van boven naar beneden.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-319">The execution happens from the top to the bottom.</span></span> <span data-ttu-id="e5a2c-320">De `if` instructie top wordt eerst geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-320">The top `if` statement is evaluated first.</span></span> <span data-ttu-id="e5a2c-321">Als dat zo is `$false` , wordt het naar het volgende `elseif` of `else` in de lijst verplaatst.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-321">If that is `$false`, then it moves down to the next `elseif` or `else` in the list.</span></span> <span data-ttu-id="e5a2c-322">Dat laatste `else` is de standaard actie die moet worden uitgevoerd als geen van de andere gebruikers retour neren `$true` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-322">That last `else` is the default action to take if none of the others return `$true`.</span></span>

### <a name="switch"></a><span data-ttu-id="e5a2c-323">schakelen</span><span class="sxs-lookup"><span data-stu-id="e5a2c-323">switch</span></span>

<span data-ttu-id="e5a2c-324">Op dit moment moet ik de `switch` instructie vermelden.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-324">At this point, I need to mention the `switch` statement.</span></span> <span data-ttu-id="e5a2c-325">Het bevat een alternatieve syntaxis voor het uitvoeren van meerdere vergelijkingen met een waarde.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-325">It provides an alternate syntax for doing multiple comparisons with a value.</span></span> <span data-ttu-id="e5a2c-326">Met de `switch` kunt u een expressie opgeven en wordt het resultaat vergeleken met verschillende waarden.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-326">With the `switch`, you specify an expression and that result gets compared with several different values.</span></span> <span data-ttu-id="e5a2c-327">Als een van deze waarden overeenkomt, wordt het overeenkomende code blok uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-327">If one of those values match, the matching code block is executed.</span></span> <span data-ttu-id="e5a2c-328">Bekijk dit voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e5a2c-328">Take a look at this example:</span></span>

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

<span data-ttu-id="e5a2c-329">Er zijn drie mogelijke waarden die kunnen overeenkomen met `$itemType` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-329">There three possible values that can match the `$itemType`.</span></span> <span data-ttu-id="e5a2c-330">In dit geval komt het overeen met `Role` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-330">In this case, it matches with `Role`.</span></span> <span data-ttu-id="e5a2c-331">Ik heb een eenvoudig voor beeld gebruikt om u een deel van de `switch` operator te geven.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-331">I used a simple example just to give you some exposure to the `switch` operator.</span></span> <span data-ttu-id="e5a2c-332">Ik vind meer informatie over [Alles wat je ooit zou weten over de instructie switch][] in een ander artikel.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-332">I talk more about [everything you ever wanted to know about the switch statement][] in another article.</span></span>

## <a name="pipeline"></a><span data-ttu-id="e5a2c-333">Pijplijn</span><span class="sxs-lookup"><span data-stu-id="e5a2c-333">Pipeline</span></span>

<span data-ttu-id="e5a2c-334">De pijp lijn is een unieke en belang rijke functie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-334">The pipeline is a unique and important feature of PowerShell.</span></span> <span data-ttu-id="e5a2c-335">Elke waarde die niet wordt onderdrukt of toegewezen aan een variabele, wordt in de pijp lijn geplaatst.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-335">Any value that isn't suppressed or assigned to a variable gets placed in the pipeline.</span></span> <span data-ttu-id="e5a2c-336">Het `if` biedt ons een manier om te profiteren van de pijp lijn op een manier die niet altijd duidelijk is.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-336">The `if` provides us a way to take advantage of the pipeline in a way that isn't always obvious.</span></span>

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

<span data-ttu-id="e5a2c-337">Elk script blok plaatst de resultaten van de opdrachten of de waarde in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-337">Each script block is placing the results the commands or the value into the pipeline.</span></span> <span data-ttu-id="e5a2c-338">Vervolgens wijzen we het resultaat van de `if` instructie toe aan de `$discount` variabele.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-338">Then we assign the result of the `if` statement to the `$discount` variable.</span></span> <span data-ttu-id="e5a2c-339">Dit voor beeld kan net zo eenvoudig worden toegewezen aan de `$discount` variabele rechtstreeks in elke script Block.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-339">That example could have just as easily assigned those values to the `$discount` variable directly in each scriptblock.</span></span> <span data-ttu-id="e5a2c-340">Ik kan dit niet zeggen dat ik dit met de `if` instructie regel matig gebruik, maar ik heb er wel een voor beeld van.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-340">I can't say that I use this with the `if` statement often, but I do have an example where I used this recently.</span></span>

### <a name="array-inline"></a><span data-ttu-id="e5a2c-341">Matrix inline</span><span class="sxs-lookup"><span data-stu-id="e5a2c-341">Array inline</span></span>

<span data-ttu-id="e5a2c-342">Ik heb een functie met de naam [invoke-SnowSql][] waarmee een uitvoerbaar bestand met verschillende opdracht regel argumenten wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-342">I have a function called [Invoke-SnowSql][] that launches an executable with several command-line arguments.</span></span> <span data-ttu-id="e5a2c-343">Hier volgt een clip van deze functie, waarbij de matrix met argumenten wordt opgebouwd.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-343">Here is a clip from that function where I build the array of arguments.</span></span>

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

<span data-ttu-id="e5a2c-344">De `$Debug` `$Path` variabelen en zijn para meters voor de functie die door de eind gebruiker wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-344">The `$Debug` and `$Path` variables are parameters on the function that are provided by the end user.</span></span>
<span data-ttu-id="e5a2c-345">Ik Beoordeel deze inline binnen de initialisatie van mijn matrix.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-345">I evaluate them inline inside the initialization of my array.</span></span> <span data-ttu-id="e5a2c-346">Als `$Debug` is ingesteld op True, worden deze waarden `$snowSqlParam` in de juiste plaats gezet.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-346">If `$Debug` is true, then those values fall into the `$snowSqlParam` in the correct place.</span></span> <span data-ttu-id="e5a2c-347">Hetzelfde geldt voor de `$Path` variabele.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-347">Same holds true for the `$Path` variable.</span></span>

## <a name="simplify-complex-operations"></a><span data-ttu-id="e5a2c-348">Vereenvoudig complexe bewerkingen</span><span class="sxs-lookup"><span data-stu-id="e5a2c-348">Simplify complex operations</span></span>

<span data-ttu-id="e5a2c-349">Het is onvermijdelijk dat u een situatie ondervindt die te veel vergelijkingen heeft om te controleren en uw `If` instructie schuift in de rechter kant van het scherm.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-349">It's inevitable that you run into a situation that has way too many comparisons to check and your `If` statement scrolls way off the right side of the screen.</span></span>

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

<span data-ttu-id="e5a2c-350">Ze kunnen moeilijk te lezen zijn en waardoor u meer gevoelig maakt voor fouten.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-350">They can be hard to read and that make you more prone to make mistakes.</span></span> <span data-ttu-id="e5a2c-351">Er zijn enkele dingen die we hiervoor kunnen doen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-351">There are a few things we can do about that.</span></span>

### <a name="line-continuation"></a><span data-ttu-id="e5a2c-352">Regel voortzetting</span><span class="sxs-lookup"><span data-stu-id="e5a2c-352">Line continuation</span></span>

<span data-ttu-id="e5a2c-353">Er zijn enkele opera tors in Power shell waarmee u naar de volgende regel kunt teruglopen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-353">There some operators in PowerShell that let you wrap you command to the next line.</span></span> <span data-ttu-id="e5a2c-354">De logische Opera tors `-and` en `-or` zijn goede Opera tors die u kunt gebruiken als u uw expressie wilt opsplitsen in meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-354">The logical operators `-and` and `-or` are good operators to use if you want to break your expression into multiple lines.</span></span>

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

<span data-ttu-id="e5a2c-355">Er is nog steeds veel aan de slag, maar elk stuk op een aparte regel maakt een groot verschil.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-355">There's still a lot going on there, but placing each piece on its own line makes a big difference.</span></span>
<span data-ttu-id="e5a2c-356">Dit wordt in het algemeen gebruikt wanneer ik meer dan twee vergelijkingen krijg of als ik naar rechts moet schuiven om een van de logica te lezen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-356">I generally use this when I get more than two comparisons or if I have to scroll to the right to read any of the logic.</span></span>

### <a name="pre-calculating-results"></a><span data-ttu-id="e5a2c-357">Resultaten vooraf berekenen</span><span class="sxs-lookup"><span data-stu-id="e5a2c-357">Pre-calculating results</span></span>

<span data-ttu-id="e5a2c-358">We kunnen deze instructie uit de verklaring halen `if` en alleen het resultaat controleren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-358">We can take that statement out of the `if` statement and only check the result.</span></span>

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

<span data-ttu-id="e5a2c-359">Dit is net zo veel duidelijker dan het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-359">This just feels much cleaner than the previous example.</span></span> <span data-ttu-id="e5a2c-360">U krijgt ook de mogelijkheid om een naam van een variabele te gebruiken waarin wordt uitgelegd wat het is dat u werkelijk controleert.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-360">You also are given an opportunity to use a variable name that explains what it's that you're really checking.</span></span> <span data-ttu-id="e5a2c-361">Dit is ook een voor beeld van zelf-document code waarmee overbodige opmerkingen worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-361">This is also and example of self-documenting code that saves unnecessary comments.</span></span>

### <a name="multiple-if-statements"></a><span data-ttu-id="e5a2c-362">Meerdere if-instructies</span><span class="sxs-lookup"><span data-stu-id="e5a2c-362">Multiple if statements</span></span>

<span data-ttu-id="e5a2c-363">We kunnen dit in meerdere instructies opsplitsen en er één tegelijk op controleren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-363">We can break this up into multiple statements and check them one at a time.</span></span> <span data-ttu-id="e5a2c-364">In dit geval gebruiken we een vlag of een tracerings variabele om de resultaten te combi neren.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-364">In this case, we use a flag or a tracking variable to combine the results.</span></span>

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

<span data-ttu-id="e5a2c-365">Ik had de logica moeten inverteren om ervoor te zorgen dat de vlag logica goed werkt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-365">I did have to invert the logic to make the flag logic work correctly.</span></span> <span data-ttu-id="e5a2c-366">Elke evaluatie is een afzonderlijke `if` instructie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-366">Each evaluation is an individual `if` statement.</span></span> <span data-ttu-id="e5a2c-367">Het voor deel hiervan is dat wanneer u fouten wilt opsporen, u precies weet wat de logica doet.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-367">The advantage of this is that when you're debugging, you can tell exactly what the logic is doing.</span></span> <span data-ttu-id="e5a2c-368">Ik kon op hetzelfde moment veel betere uitgebreider toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-368">I was able to add much better verbosity at the same time.</span></span>

<span data-ttu-id="e5a2c-369">Het voor de hand liggende nadeel is dat er veel meer code moet worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-369">The obvious downside is that it's so much more code to write.</span></span> <span data-ttu-id="e5a2c-370">De code is complexer om te kijken naar dezelfde regel logica en explodeert deze in 25 of meer regels.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-370">The code is more complex to look at as it takes a single line of logic and explodes it into 25 or more lines.</span></span>

### <a name="using-functions"></a><span data-ttu-id="e5a2c-371">Functies gebruiken</span><span class="sxs-lookup"><span data-stu-id="e5a2c-371">Using functions</span></span>

<span data-ttu-id="e5a2c-372">We kunnen ook alle validatie logica naar een functie verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-372">We can also move all that validation logic into a function.</span></span> <span data-ttu-id="e5a2c-373">Bekijk hoe schoon dit in één oogopslag eruitziet.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-373">Look at how clean this looks at a glance.</span></span>

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

<span data-ttu-id="e5a2c-374">U moet de functie nog steeds maken om de validatie uit te voeren, maar dit maakt het veel eenvoudiger om met deze code te werken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-374">You still have to create the function to do the validation, but it makes this code much easier to work with.</span></span> <span data-ttu-id="e5a2c-375">Dit maakt deze code gemakkelijker te testen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-375">It makes this code easier to test.</span></span> <span data-ttu-id="e5a2c-376">In uw tests kunt u de aanroep naar vertrekt `Test-ADDriveConfiguration` en hebt u slechts twee tests nodig voor deze functie.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-376">In your tests, you can mock the call to `Test-ADDriveConfiguration` and you only need two tests for this function.</span></span> <span data-ttu-id="e5a2c-377">Een locatie waar deze wordt geretourneerd `$true` en een waar deze wordt geretourneerd `$false` .</span><span class="sxs-lookup"><span data-stu-id="e5a2c-377">One where it returns `$true` and one where it returns `$false`.</span></span> <span data-ttu-id="e5a2c-378">Het testen van de andere functie is eenvoudiger omdat deze zo klein is.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-378">Testing the other function is simpler because it's so small.</span></span>

<span data-ttu-id="e5a2c-379">De hoofd tekst van de functie kan nog steeds zijn dat er één regel is gestart met of de uitgelichte logica die we in de laatste sectie hebben gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-379">The body of that function could still be that one-liner we started with or the exploded logic that we used in the last section.</span></span> <span data-ttu-id="e5a2c-380">Dit werkt goed voor beide scenario's en stelt u in staat om die implementatie later eenvoudig te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-380">This works well for both scenarios and allows you to easily change that implementation later.</span></span>

## <a name="error-handling"></a><span data-ttu-id="e5a2c-381">Foutafhandeling</span><span class="sxs-lookup"><span data-stu-id="e5a2c-381">Error handling</span></span>

<span data-ttu-id="e5a2c-382">Een belang rijk gebruik van de- `if` instructie is het controleren op fouten voordat u fouten ondervindt.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-382">One important use of the `if` statement is to check for error conditions before you run into errors.</span></span> <span data-ttu-id="e5a2c-383">Een goed voor beeld is om te controleren of er al een map bestaat voordat u deze probeert te maken.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-383">A good example is to check if a folder already exists before you try to create it.</span></span>

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

<span data-ttu-id="e5a2c-384">Als u een uitzonde ring verwacht, is dit niet echt een uitzonde ring.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-384">I like to say that if you expect an exception to happen, then it's not really an exception.</span></span> <span data-ttu-id="e5a2c-385">Controleer uw waarden dus en Valideer uw voor waarden waar u dit kunt doen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-385">So check your values and validate your conditions where you can.</span></span>

<span data-ttu-id="e5a2c-386">Als u nog iets meer wilt weten over uitzonde ringen, kunt u een artikel over [Alles wat u graag op het punt staat dat u op de hoogte zou zijn van uitzonde ringen][].</span><span class="sxs-lookup"><span data-stu-id="e5a2c-386">If you want to dive a little more into actual exception handling, I have an article on [everything you ever wanted to know about exceptions][].</span></span>

## <a name="final-words"></a><span data-ttu-id="e5a2c-387">Laatste woorden</span><span class="sxs-lookup"><span data-stu-id="e5a2c-387">Final words</span></span>

<span data-ttu-id="e5a2c-388">De `if` instructie is een eenvoudige instructie, maar is een fundamenteel onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-388">The `if` statement is such a simple statement but is a fundamental piece of PowerShell.</span></span> <span data-ttu-id="e5a2c-389">U kunt deze meermaals gebruiken in bijna elk script dat u schrijft.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-389">You will find yourself using this multiple times in almost every script you write.</span></span> <span data-ttu-id="e5a2c-390">Ik hoop dat u een beter inzicht hebt dan voorheen.</span><span class="sxs-lookup"><span data-stu-id="e5a2c-390">I hope you have a better understanding than you had before.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[original version]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[If]: /powershell/module/microsoft.powershell.core/about/about_if
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[bitsgewijze Opera tors]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[bitwise operators]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[de vele manieren om regex te gebruiken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[the many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[alles wat u moet weten over uitzonde ringen]: everything-about-exceptions.md
[everything you ever wanted to know about exceptions]: everything-about-exceptions.md
[alles wat u wilt weten over $null]: everything-about-null.md
[everything you wanted to know about $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[alles wat u moet weten over de instructie switch]: everything-about-switch.md
[everything you ever wanted to know about the switch statement]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
