---
title: Alles wat u wilt weten over $null
description: De Power shell-$null lijkt vaak eenvoudig te zijn, maar er zijn veel nuances. Laten we de $null sluiten, zodat u weet wat er gebeurt wanneer u onverwacht een null-waarde uitvoert.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149829"
---
# <a name="everything-you-wanted-to-know-about-null"></a><span data-ttu-id="52ce2-104">Alles wat u wilt weten over $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-104">Everything you wanted to know about $null</span></span>

<span data-ttu-id="52ce2-105">De Power shell `$null` lijkt vaak eenvoudig te zijn, maar er zijn veel nuances.</span><span class="sxs-lookup"><span data-stu-id="52ce2-105">The PowerShell `$null` often appears to be simple but it has a lot of nuances.</span></span> <span data-ttu-id="52ce2-106">Laten we eens kijken `$null` hoe u weet wat er gebeurt wanneer u onverwacht een `$null` waarde uitvoert.</span><span class="sxs-lookup"><span data-stu-id="52ce2-106">Let's take a close look at `$null` so you know what happens when you unexpectedly run into a `$null` value.</span></span>

> [!NOTE]
> <span data-ttu-id="52ce2-107">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="52ce2-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="52ce2-108">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="52ce2-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="52ce2-109">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="52ce2-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-null"></a><span data-ttu-id="52ce2-110">Wat is NULL?</span><span class="sxs-lookup"><span data-stu-id="52ce2-110">What is NULL?</span></span>

<span data-ttu-id="52ce2-111">U kunt NULL beschouwen als een onbekende of lege waarde.</span><span class="sxs-lookup"><span data-stu-id="52ce2-111">You can think of NULL as an unknown or empty value.</span></span> <span data-ttu-id="52ce2-112">Een variabele is NULL totdat u er een waarde of een object aan toewijst.</span><span class="sxs-lookup"><span data-stu-id="52ce2-112">A variable is NULL until you assign a value or an object to it.</span></span> <span data-ttu-id="52ce2-113">Dit kan belang rijk zijn omdat er enkele opdrachten zijn waarvoor een waarde is vereist en fouten worden gegenereerd als de waarde NULL is.</span><span class="sxs-lookup"><span data-stu-id="52ce2-113">This can be important because there are some commands that require a value and generate errors if the value is NULL.</span></span>

### <a name="powershell-null"></a><span data-ttu-id="52ce2-114">Power shell-$null</span><span class="sxs-lookup"><span data-stu-id="52ce2-114">PowerShell $null</span></span>

<span data-ttu-id="52ce2-115">`$null`is een automatische variabele in Power shell die wordt gebruikt om NULL weer te geven.</span><span class="sxs-lookup"><span data-stu-id="52ce2-115">`$null` is an automatic variable in PowerShell used to represent NULL.</span></span> <span data-ttu-id="52ce2-116">U kunt deze toewijzen aan variabelen, deze gebruiken in vergelijkingen en deze gebruiken als plaatsaanduiding voor NULL in een verzameling.</span><span class="sxs-lookup"><span data-stu-id="52ce2-116">You can assign it to variables, use it in comparisons and use it as a place holder for NULL in a collection.</span></span>

<span data-ttu-id="52ce2-117">Power shell behandelt `$null` als een object met de waarde Null.</span><span class="sxs-lookup"><span data-stu-id="52ce2-117">PowerShell treats `$null` as an object with a value of NULL.</span></span> <span data-ttu-id="52ce2-118">Dit wijkt af van wat u kunt verwachten als u uit een andere taal komt.</span><span class="sxs-lookup"><span data-stu-id="52ce2-118">This is different than what you may expect if you come from another language.</span></span>

## <a name="examples-of-null"></a><span data-ttu-id="52ce2-119">Voor beelden van $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-119">Examples of $null</span></span>

<span data-ttu-id="52ce2-120">Telkens wanneer u een variabele wilt gebruiken die u niet hebt geïnitialiseerd, is de waarde `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-120">Anytime you try to use a variable that you have not initialized, the value is `$null`.</span></span> <span data-ttu-id="52ce2-121">Dit is een van de meest voorkomende manieren waarop `$null` waarden in uw code worden alvast.</span><span class="sxs-lookup"><span data-stu-id="52ce2-121">This is one of the most common ways that `$null` values sneak into your code.</span></span>

```powershell
PS> $null -eq $undefinedVariable
True
```

<span data-ttu-id="52ce2-122">Als u een variabelenaam hebt getypt, ziet Power shell deze als een andere variabele en de waarde is `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-122">If you happen to mistype a variable name then PowerShell sees it as a different variable and the value is `$null`.</span></span>

<span data-ttu-id="52ce2-123">De andere manier om `$null` waarden te vinden, is wanneer ze afkomstig zijn van andere opdrachten die geen resultaten opleveren.</span><span class="sxs-lookup"><span data-stu-id="52ce2-123">The other way you find `$null` values is when they come from other commands that don't give you any results.</span></span>

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a><span data-ttu-id="52ce2-124">Gevolgen van $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-124">Impact of $null</span></span>

<span data-ttu-id="52ce2-125">`$null`waarden beïnvloeden uw code anders, afhankelijk van waar ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="52ce2-125">`$null` values impact your code differently depending on where they show up.</span></span>

### <a name="in-strings"></a><span data-ttu-id="52ce2-126">In teken reeksen</span><span class="sxs-lookup"><span data-stu-id="52ce2-126">In strings</span></span>

<span data-ttu-id="52ce2-127">Als u `$null` in een teken reeks gebruikt, is het een lege waarde (of een lege teken reeks).</span><span class="sxs-lookup"><span data-stu-id="52ce2-127">If you use `$null` in a string, then it's a blank value (or empty string).</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

<span data-ttu-id="52ce2-128">Dit is een van de redenen waarom ik in de logboek berichten een punt haken wil plaatsen rond variabelen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-128">This is one of the reasons that I like to place brackets around variables when using them in log messages.</span></span> <span data-ttu-id="52ce2-129">Het is nog belang rijker om de randen van de waarden van variabelen te identificeren wanneer de waarde aan het einde van de teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="52ce2-129">It's even more important to identify the edges of your variable values when the value is at the end of the string.</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

<span data-ttu-id="52ce2-130">Dit maakt lege teken reeksen en `$null` waarden gemakkelijk te herkennen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-130">This makes empty strings and `$null` values easy to spot.</span></span>

### <a name="in-numeric-equation"></a><span data-ttu-id="52ce2-131">In numerieke vergelijking</span><span class="sxs-lookup"><span data-stu-id="52ce2-131">In numeric equation</span></span>

<span data-ttu-id="52ce2-132">Wanneer een `$null` waarde wordt gebruikt in een numerieke vergelijking, zijn de resultaten ongeldig als ze geen fout geven.</span><span class="sxs-lookup"><span data-stu-id="52ce2-132">When a `$null` value is used in a numeric equation then your results are invalid if they don't give an error.</span></span> <span data-ttu-id="52ce2-133">Soms `$null` wordt de evaluatie van `0` en andere tijden het hele resultaat `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-133">Sometimes the `$null` evaluates to `0` and other times it makes the whole result `$null`.</span></span>
<span data-ttu-id="52ce2-134">Hier volgt een voor beeld met vermenigvuldiging met de waarde 0 of `$null` afhankelijk van de volg orde van de waarden.</span><span class="sxs-lookup"><span data-stu-id="52ce2-134">Here is an example with multiplication that gives 0 or `$null` depending on the order of the values.</span></span>

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a><span data-ttu-id="52ce2-135">In plaats van een verzameling</span><span class="sxs-lookup"><span data-stu-id="52ce2-135">In place of a collection</span></span>

<span data-ttu-id="52ce2-136">Met een verzameling kunt u een index gebruiken om toegang te krijgen tot waarden.</span><span class="sxs-lookup"><span data-stu-id="52ce2-136">A collection allow you use an index to access values.</span></span> <span data-ttu-id="52ce2-137">Als u probeert te indexeren in een verzameling die daad werkelijk wordt `null` weer geven, krijgt u deze fout: `Cannot index into a null array` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-137">If you try to index into a collection that is actually `null`, you get this error: `Cannot index into a null array`.</span></span>

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

<span data-ttu-id="52ce2-138">Als u een verzameling hebt maar probeert toegang te krijgen tot een element dat zich niet in de verzameling bevindt, wordt er een resultaat weer geven `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-138">If you have a collection but try to access an element that is not in the collection, you get a `$null` result.</span></span>

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a><span data-ttu-id="52ce2-139">In plaats van een object</span><span class="sxs-lookup"><span data-stu-id="52ce2-139">In place of an object</span></span>

<span data-ttu-id="52ce2-140">Als u probeert toegang te krijgen tot een eigenschap of sub-eigenschap van een object dat niet over de opgegeven eigenschap beschikt, krijgt u een `$null` waarde zoals u zou doen voor een niet-gedefinieerde variabele.</span><span class="sxs-lookup"><span data-stu-id="52ce2-140">If you try to access a property or sub property of an object that doesn't have the specified property, you get a `$null` value like you would for an undefined variable.</span></span> <span data-ttu-id="52ce2-141">Het maakt niet uit of de variabele `$null` of een werkelijk object in dit geval is.</span><span class="sxs-lookup"><span data-stu-id="52ce2-141">It doesn't matter if the variable is `$null` or an actual object in this case.</span></span>

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a><span data-ttu-id="52ce2-142">Methode voor een expressie met Null-waarden</span><span class="sxs-lookup"><span data-stu-id="52ce2-142">Method on a null-valued expression</span></span>

<span data-ttu-id="52ce2-143">Het aanroepen van een methode voor een `$null` object genereert een `RuntimeException` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-143">Calling a method on a `$null` object throws a `RuntimeException`.</span></span>

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

<span data-ttu-id="52ce2-144">Wanneer ik de woord groep Zie, `You cannot call a method on a null-valued expression` wordt het eerste wat ik zoek, plaatsen waar ik een methode aanmeldt voor een variabele zonder deze eerst te controleren `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-144">Whenever I see the phrase `You cannot call a method on a null-valued expression` then the first thing I look for are places where I am calling a method on a variable without first checking it for `$null`.</span></span>

## <a name="checking-for-null"></a><span data-ttu-id="52ce2-145">Controleren op $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-145">Checking for $null</span></span>

<span data-ttu-id="52ce2-146">U hebt wellicht al gemerkt dat ik aan de `$null` linkerkant altijd aan het controleren was wanneer ik `$null` in mijn voor beelden Controleer.</span><span class="sxs-lookup"><span data-stu-id="52ce2-146">You may have noticed that I always place the `$null` on the left when checking for `$null` in my examples.</span></span> <span data-ttu-id="52ce2-147">Dit is opzettelijk en wordt geaccepteerd als Power shell-best practice.</span><span class="sxs-lookup"><span data-stu-id="52ce2-147">This is intentional and accepted as a PowerShell best practice.</span></span> <span data-ttu-id="52ce2-148">Er zijn enkele scenario's waarbij u deze aan de rechter kant niet het verwachte resultaat geeft.</span><span class="sxs-lookup"><span data-stu-id="52ce2-148">There are some scenarios where placing it on the right doesn't give you the expected result.</span></span>

<span data-ttu-id="52ce2-149">Bekijk dit volgende voor beeld en probeer de resultaten te voors pellen:</span><span class="sxs-lookup"><span data-stu-id="52ce2-149">Look at this next example and try to predict the results:</span></span>

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

<span data-ttu-id="52ce2-150">Als ik niet Definieer `$value` , wordt het eerste geëvalueerd `$true` en het bericht is `The array is $null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-150">If I do not define `$value`, the first one evaluates to `$true` and our message is `The array is $null`.</span></span> <span data-ttu-id="52ce2-151">Deze trap is het mogelijk om een te maken `$value` waarmee beide kunnen worden`$false`</span><span class="sxs-lookup"><span data-stu-id="52ce2-151">The trap here is that it's possible to create a `$value` that allows both of them to be `$false`</span></span>

```powershell
$value = @( $null )
```

<span data-ttu-id="52ce2-152">In dit geval is de een `$value` matrix met een `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-152">In this case, the `$value` is an array that contains a `$null`.</span></span> <span data-ttu-id="52ce2-153">`-eq`Hiermee wordt elke waarde in de matrix gecontroleerd en wordt `$null` er een overeenkomst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="52ce2-153">The `-eq` checks every value in the array and returns the `$null` that is matched.</span></span> <span data-ttu-id="52ce2-154">Dit resulteert in `$false` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-154">This evaluates to `$false`.</span></span> <span data-ttu-id="52ce2-155">Het `-ne` retourneert alles dat niet overeenkomt `$null` , en in dit geval zijn er geen resultaten (deze worden ook geëvalueerd naar `$false` ).</span><span class="sxs-lookup"><span data-stu-id="52ce2-155">The `-ne` returns everything that doesn't match `$null` and in this case there are no results (This also evaluates to `$false`).</span></span> <span data-ttu-id="52ce2-156">Geen van beide kan worden weer gegeven `$true` , maar het lijkt erop dat er een van de twee is.</span><span class="sxs-lookup"><span data-stu-id="52ce2-156">Neither one is `$true` even though it looks like one of them should be.</span></span>

<span data-ttu-id="52ce2-157">U kunt niet alleen een waarde maken waardoor beide worden geëvalueerd `$false` . het is mogelijk om een waarde te maken waarbij deze beide worden geëvalueerd `$true` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-157">Not only can we create a value that makes both of them evaluate to `$false`, it's possible to create a value where they both evaluate to `$true`.</span></span> <span data-ttu-id="52ce2-158">Mathias Jessen ( @IISResetMe ) heeft een [goede post][] die Dives in dat scenario.</span><span class="sxs-lookup"><span data-stu-id="52ce2-158">Mathias Jessen (@IISResetMe) has a [good post][] that dives into that scenario.</span></span>

### <a name="psscriptanalyzer-and-vscode"></a><span data-ttu-id="52ce2-159">PSScriptAnalyzer en VSCode</span><span class="sxs-lookup"><span data-stu-id="52ce2-159">PSScriptAnalyzer and VSCode</span></span>

<span data-ttu-id="52ce2-160">De [PSScriptAnalyzer][] -module heeft een regel waarmee wordt gecontroleerd of dit probleem is aangeroepen `PSPossibleIncorrectComparisonWithNull` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-160">The [PSScriptAnalyzer][] module has a rule that checks for this issue called `PSPossibleIncorrectComparisonWithNull`.</span></span>

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

<span data-ttu-id="52ce2-161">Omdat VS code ook de PSScriptAnalyser-regels gebruikt, wordt dit door de service gemarkeerd of geïdentificeerd als een probleem in het script.</span><span class="sxs-lookup"><span data-stu-id="52ce2-161">Because VS Code uses the PSScriptAnalyser rules too, it also highlights or identifies this as a problem in your script.</span></span>

### <a name="simple-if-check"></a><span data-ttu-id="52ce2-162">Eenvoudig als controleren</span><span class="sxs-lookup"><span data-stu-id="52ce2-162">Simple if check</span></span>

<span data-ttu-id="52ce2-163">Een gemeen schappelijke manier die gebruikers controleren op een niet-$nulle waarde, is het gebruik van een eenvoudige `if()` instructie zonder de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="52ce2-163">A common way that people check for a non-$null value is to use a simple `if()` statement without the comparison.</span></span>

```powershell
if ( $value )
{
    Do-Something
}
```

<span data-ttu-id="52ce2-164">Als de waarde is `$null` , wordt deze geëvalueerd als `$false` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-164">If the value is `$null`, this evaluates to `$false`.</span></span> <span data-ttu-id="52ce2-165">Dit is eenvoudig te lezen, maar wees voorzichtig met het zoeken naar precies wat u verwacht.</span><span class="sxs-lookup"><span data-stu-id="52ce2-165">This is easy to read, but be careful that it's looking for exactly what you're expecting it to look for.</span></span> <span data-ttu-id="52ce2-166">Ik heb deze regel code gelezen als:</span><span class="sxs-lookup"><span data-stu-id="52ce2-166">I read that line of code as:</span></span>

> <span data-ttu-id="52ce2-167">Als `$value` heeft een waarde.</span><span class="sxs-lookup"><span data-stu-id="52ce2-167">If `$value` has a value.</span></span>

<span data-ttu-id="52ce2-168">Maar dat is niet het hele verhaal.</span><span class="sxs-lookup"><span data-stu-id="52ce2-168">But that's not the whole story.</span></span> <span data-ttu-id="52ce2-169">Deze regel heeft de volgende melding:</span><span class="sxs-lookup"><span data-stu-id="52ce2-169">That line is actually saying:</span></span>

> <span data-ttu-id="52ce2-170">Als `$value` is niet `$null` of `0` of of `$false` een`empty string`</span><span class="sxs-lookup"><span data-stu-id="52ce2-170">If `$value` is not `$null` or `0` or `$false` or an `empty string`</span></span>

<span data-ttu-id="52ce2-171">Hier volgt een meer uitgebreid voor beeld van deze instructie.</span><span class="sxs-lookup"><span data-stu-id="52ce2-171">Here is a more complete sample of that statement.</span></span>

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

<span data-ttu-id="52ce2-172">Het is heel goed om een basis controle te gebruiken `if` , zolang u weet dat de andere waarden tellen als `$false` en niet alleen dat een variabele een waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="52ce2-172">It's perfectly OK to use a basic `if` check as long as you remember those other values count as `$false` and not just that a variable has a value.</span></span>

<span data-ttu-id="52ce2-173">Ik heb dit probleem ondertreden bij het refactoreren van een paar dagen geleden.</span><span class="sxs-lookup"><span data-stu-id="52ce2-173">I ran into this issue when refactoring some code a few days ago.</span></span> <span data-ttu-id="52ce2-174">Dit is een basis eigenschap die er ongeveer als volgt uitziet.</span><span class="sxs-lookup"><span data-stu-id="52ce2-174">It had a basic property check like this.</span></span>

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="52ce2-175">Ik wilde een waarde alleen toewijzen aan de object eigenschap als deze aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="52ce2-175">I wanted to assign a value to the object property only if it existed.</span></span> <span data-ttu-id="52ce2-176">In de meeste gevallen heeft het oorspronkelijke object een waarde die `$true` in de instructie zou kunnen evalueren `if` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-176">In most cases, the original object had a value that would evaluate to `$true` in the `if` statement.</span></span> <span data-ttu-id="52ce2-177">Maar er is een probleem opgetreden waarbij de waarde af en toe niet is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="52ce2-177">But I ran into an issue where the value was occasionally not getting set.</span></span> <span data-ttu-id="52ce2-178">Er is een fout opgetreden in de code en er is vastgesteld dat het object de eigenschap had, maar dit is een lege teken reeks waarde.</span><span class="sxs-lookup"><span data-stu-id="52ce2-178">I debugged the code and found that the object had the property but it was a blank string value.</span></span> <span data-ttu-id="52ce2-179">Dit voor komt dat het ooit is bijgewerkt met de vorige logica.</span><span class="sxs-lookup"><span data-stu-id="52ce2-179">This prevented it from ever getting updated with the previous logic.</span></span> <span data-ttu-id="52ce2-180">Dus ik heb een goede `$null` controle en alles gewerkt.</span><span class="sxs-lookup"><span data-stu-id="52ce2-180">So I added a proper `$null` check and everything worked.</span></span>

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="52ce2-181">Het is weinig bugs, zoals deze die moeilijk te herkennen zijn, en u kunt de waarden controleren voor `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-181">It's little bugs like these that are hard to spot and make me aggressively check values for `$null`.</span></span>

## <a name="nullcount"></a><span data-ttu-id="52ce2-182">$null. Aantal</span><span class="sxs-lookup"><span data-stu-id="52ce2-182">$null.Count</span></span>

<span data-ttu-id="52ce2-183">Als u een eigenschap van een waarde probeert te openen `$null` , is dat ook de eigenschap `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-183">If you try to access a property on a `$null` value, that the property is also `$null`.</span></span> <span data-ttu-id="52ce2-184">De `count` eigenschap is de uitzonde ring op deze regel.</span><span class="sxs-lookup"><span data-stu-id="52ce2-184">The `count` property is the exception to this rule.</span></span>

```powershell
PS> $value = $null
PS> $value.count
0
```

<span data-ttu-id="52ce2-185">Wanneer u een `$null` waarde hebt, is dat `count` `0` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-185">When you have a `$null` value, then the `count` is `0`.</span></span> <span data-ttu-id="52ce2-186">Deze speciale eigenschap wordt toegevoegd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="52ce2-186">This special property is added by PowerShell.</span></span>

### <a name="pscustomobject-count"></a><span data-ttu-id="52ce2-187">PSCustomObject Aantal</span><span class="sxs-lookup"><span data-stu-id="52ce2-187">[PSCustomObject] Count</span></span>

<span data-ttu-id="52ce2-188">Bijna alle objecten in Power Shell hebben die eigenschap Count.</span><span class="sxs-lookup"><span data-stu-id="52ce2-188">Almost all objects in PowerShell have that count property.</span></span> <span data-ttu-id="52ce2-189">Een belang rijke uitzonde ring is de `[PSCustomObject]` in Windows Power shell 5,1 (dit is opgelost in Power shell 6,0).</span><span class="sxs-lookup"><span data-stu-id="52ce2-189">One important exception is the `[PSCustomObject]` in Windows PowerShell 5.1 (This is fixed in PowerShell 6.0).</span></span> <span data-ttu-id="52ce2-190">Het heeft geen eigenschap Count, dus u krijgt een `$null` waarde als u deze probeert te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="52ce2-190">It doesn't have a count property so you get a `$null` value if you try to use it.</span></span> <span data-ttu-id="52ce2-191">Dit noemen we hier zodat je niet kunt gebruiken `.Count` in plaats van een `$null` cheque.</span><span class="sxs-lookup"><span data-stu-id="52ce2-191">I call this out here so that you don't try to use `.Count` instead of a `$null` check.</span></span>

<span data-ttu-id="52ce2-192">Als u dit voor beeld uitvoert op Windows Power shell 5,1 en Power shell 6,0, hebt u verschillende resultaten.</span><span class="sxs-lookup"><span data-stu-id="52ce2-192">Running this example on Windows PowerShell 5.1 and PowerShell 6.0 gives you different results.</span></span>

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a><span data-ttu-id="52ce2-193">Lege Null</span><span class="sxs-lookup"><span data-stu-id="52ce2-193">Empty null</span></span>

<span data-ttu-id="52ce2-194">Er is een speciaal type van `$null` dat anders is dan de andere.</span><span class="sxs-lookup"><span data-stu-id="52ce2-194">There is one special type of `$null` that acts differently than the others.</span></span> <span data-ttu-id="52ce2-195">Ik bel het, maar het is wel `$null` echt een [System. Management. Automation. internal. AutomationNull][].</span><span class="sxs-lookup"><span data-stu-id="52ce2-195">I am going to call it the empty `$null` but it's really a [System.Management.Automation.Internal.AutomationNull][].</span></span> <span data-ttu-id="52ce2-196">Dit `$null` is een leeg item dat u krijgt als resultaat van een functie of script blok dat Nothing retourneert (een ongeldig resultaat).</span><span class="sxs-lookup"><span data-stu-id="52ce2-196">This empty `$null` is the one you get as the result of a function or script block that returns nothing (a void result).</span></span>

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

<span data-ttu-id="52ce2-197">Als u het vergelijkt met `$null` , krijgt u een `$null` waarde.</span><span class="sxs-lookup"><span data-stu-id="52ce2-197">If you compare it with `$null`, you get a `$null` value.</span></span> <span data-ttu-id="52ce2-198">Bij gebruik in een evaluatie waarbij een waarde is vereist, is de waarde altijd `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-198">When used in an evaluation where a value is required, the value is always `$null`.</span></span> <span data-ttu-id="52ce2-199">Maar als u dit binnen een matrix plaatst, wordt het beschouwd als een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="52ce2-199">But if you place it inside an array, it's treated the same as an empty array.</span></span>

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

<span data-ttu-id="52ce2-200">U kunt een matrix hebben die één `$null` waarde bevat `count` `1` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-200">You can have an array that contains one `$null` value and its `count` is `1`.</span></span> <span data-ttu-id="52ce2-201">Maar als u een leeg resultaat binnen een matrix plaatst, wordt dit niet als een item beschouwd.</span><span class="sxs-lookup"><span data-stu-id="52ce2-201">But if you place an empty result inside an array then it's not counted as an item.</span></span> <span data-ttu-id="52ce2-202">Het aantal is `0` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-202">The count is `0`.</span></span>

<span data-ttu-id="52ce2-203">Als u het lege item als `$null` een verzameling behandelt, is het leeg.</span><span class="sxs-lookup"><span data-stu-id="52ce2-203">If you treat the empty `$null` like a collection, then it's empty.</span></span>

### <a name="pipeline"></a><span data-ttu-id="52ce2-204">Pijplijn</span><span class="sxs-lookup"><span data-stu-id="52ce2-204">Pipeline</span></span>

<span data-ttu-id="52ce2-205">De primaire locatie die u ziet, is het verschil wanneer u de pijp lijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="52ce2-205">The primary place you see the difference is when using the pipeline.</span></span> <span data-ttu-id="52ce2-206">U kunt een waarde sluis teken, `$null` maar niet een lege `$null` waarde.</span><span class="sxs-lookup"><span data-stu-id="52ce2-206">You can pipe a `$null` value but not an empty `$null` value.</span></span>

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

<span data-ttu-id="52ce2-207">Afhankelijk van uw code moet u rekening `$null` met de in uw logica.</span><span class="sxs-lookup"><span data-stu-id="52ce2-207">Depending on your code, you should account for the `$null` in your logic.</span></span>

<span data-ttu-id="52ce2-208">Controleer eerst op `$null`</span><span class="sxs-lookup"><span data-stu-id="52ce2-208">Either check for `$null` first</span></span>

- <span data-ttu-id="52ce2-209">Null filteren op de pijp lijn ( `... | Where {$null -ne $_} | ...` )</span><span class="sxs-lookup"><span data-stu-id="52ce2-209">Filter out null on the pipeline (`... | Where {$null -ne $_} | ...`)</span></span>
- <span data-ttu-id="52ce2-210">Afhandelen in de pijplijn functie</span><span class="sxs-lookup"><span data-stu-id="52ce2-210">Handle it in the pipeline function</span></span>

## <a name="foreach"></a><span data-ttu-id="52ce2-211">foreach</span><span class="sxs-lookup"><span data-stu-id="52ce2-211">foreach</span></span>

<span data-ttu-id="52ce2-212">Een van mijn favoriete functies van `foreach` is dat deze niet wordt geïnventariseerd over een `$null` verzameling.</span><span class="sxs-lookup"><span data-stu-id="52ce2-212">One of my favorite features of `foreach` is that it doesn't enumerate over a `$null` collection.</span></span>

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

<span data-ttu-id="52ce2-213">Zo hoeft u niet te `$null` controleren of de verzameling moet worden gecontroleerd voordat deze wordt geïnventariseerd.</span><span class="sxs-lookup"><span data-stu-id="52ce2-213">This saves me from having to `$null` check the collection before I enumerate it.</span></span> <span data-ttu-id="52ce2-214">Als u een verzameling waarden hebt `$null` , kan de waarde `$node` nog steeds zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-214">If you have a collection of `$null` values, the `$node` can still be `$null`.</span></span>

<span data-ttu-id="52ce2-215">De foreach-bewerking is op deze manier gestart met Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="52ce2-215">The foreach started working this way with PowerShell 3.0.</span></span> <span data-ttu-id="52ce2-216">Als u een oudere versie hebt, is dit niet het geval.</span><span class="sxs-lookup"><span data-stu-id="52ce2-216">If you happen to be on an older version, then this is not the case.</span></span> <span data-ttu-id="52ce2-217">Dit is een van de belang rijke wijzigingen waar u rekening mee moet houden bij het maken van back-poort code voor 2,0-compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="52ce2-217">This is one of the important changes to be aware of when back-porting code for 2.0 compatibility.</span></span>

## <a name="value-types"></a><span data-ttu-id="52ce2-218">Waardetypen</span><span class="sxs-lookup"><span data-stu-id="52ce2-218">Value types</span></span>

<span data-ttu-id="52ce2-219">Technisch gezien kunnen alleen verwijzings typen zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-219">Technically, only reference types can be `$null`.</span></span> <span data-ttu-id="52ce2-220">Power shell is echter zeer ruime en Hiermee kunnen variabelen elk type zijn.</span><span class="sxs-lookup"><span data-stu-id="52ce2-220">But PowerShell is very generous and allows for variables to be any type.</span></span> <span data-ttu-id="52ce2-221">Als u besluit een type waarde te typen, kan dat niet `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-221">If you decide to strongly type a value type, it cannot be `$null`.</span></span>
<span data-ttu-id="52ce2-222">Power shell converteert `$null` naar een standaard waarde voor veel typen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-222">PowerShell converts `$null` to a default value for many types.</span></span>

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

<span data-ttu-id="52ce2-223">Er zijn een aantal typen die geen geldige conversie van hebben `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-223">There are some types that do not have a valid conversion from `$null`.</span></span> <span data-ttu-id="52ce2-224">Deze typen genereren een `Cannot convert null to type` fout.</span><span class="sxs-lookup"><span data-stu-id="52ce2-224">These types generate a `Cannot convert null to type` error.</span></span>

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a><span data-ttu-id="52ce2-225">Functie parameters</span><span class="sxs-lookup"><span data-stu-id="52ce2-225">Function parameters</span></span>

<span data-ttu-id="52ce2-226">Het gebruik van een sterk getypeerde waarde in functie parameters is zeer gebruikelijk.</span><span class="sxs-lookup"><span data-stu-id="52ce2-226">Using a strongly typed values in function parameters is very common.</span></span> <span data-ttu-id="52ce2-227">Het is raadzaam om de typen van de para meters te definiëren, zelfs als we de typen van andere variabelen in onze scripts niet definiëren.</span><span class="sxs-lookup"><span data-stu-id="52ce2-227">We generally learn to define the types of our parameters even if we tend not to define the types of other variables in our scripts.</span></span> <span data-ttu-id="52ce2-228">Mogelijk hebt u al een aantal sterk getypeerde variabelen in uw functies en kunt u deze zelfs niet realiseren.</span><span class="sxs-lookup"><span data-stu-id="52ce2-228">You may already have some strongly typed variables in your functions and not even realize it.</span></span>

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

<span data-ttu-id="52ce2-229">Zodra u het type van de para meter instelt als een `string` , mag de waarde nooit zijn `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-229">As soon as you set the type of the parameter as a `string`, the value can never be `$null`.</span></span> <span data-ttu-id="52ce2-230">Het is gebruikelijk om te controleren of een waarde is `$null` om te zien of de gebruiker een waarde heeft gegeven of niet.</span><span class="sxs-lookup"><span data-stu-id="52ce2-230">It's common to check if a value is `$null` to see if the user provided a value or not.</span></span>

```powershell
if ( $null -ne $Value ){...}
```

<span data-ttu-id="52ce2-231">`$Value`is een lege teken reeks `''` als er geen waarde is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="52ce2-231">`$Value` is an empty string `''` when no value is provided.</span></span> <span data-ttu-id="52ce2-232">Gebruik `$PSBoundParameters.Value` in plaats daarvan de automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="52ce2-232">Use the automatic variable `$PSBoundParameters.Value` instead.</span></span>

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

<span data-ttu-id="52ce2-233">`$PSBoundParameters`bevat alleen de para meters die zijn opgegeven bij het aanroepen van de functie.</span><span class="sxs-lookup"><span data-stu-id="52ce2-233">`$PSBoundParameters` only contains the parameters that were specified when the function was called.</span></span>
<span data-ttu-id="52ce2-234">U kunt ook de `ContainsKey` methode gebruiken om te controleren op de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="52ce2-234">You can also use the `ContainsKey` method to check for the property.</span></span>

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a><span data-ttu-id="52ce2-235">IsNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="52ce2-235">IsNotNullOrEmpty</span></span>

<span data-ttu-id="52ce2-236">Als de waarde een teken reeks is, kunt u een statische teken reeks functie gebruiken om te controleren of de waarde `$null` of een lege teken reeks tegelijk is.</span><span class="sxs-lookup"><span data-stu-id="52ce2-236">If the value is a string, you can use a static string function to check if the value is `$null` or an empty string at the same time.</span></span>

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

<span data-ttu-id="52ce2-237">Ik vind mijzelf vaak als ik weet dat het waardetype een teken reeks moet zijn.</span><span class="sxs-lookup"><span data-stu-id="52ce2-237">I find myself using this often when I know the value type should be a string.</span></span>

## <a name="when-i-null-check"></a><span data-ttu-id="52ce2-238">Wanneer ik $null controleren</span><span class="sxs-lookup"><span data-stu-id="52ce2-238">When I $null check</span></span>

<span data-ttu-id="52ce2-239">Ik ben een verdedigings scripter.</span><span class="sxs-lookup"><span data-stu-id="52ce2-239">I am a defensive scripter.</span></span> <span data-ttu-id="52ce2-240">Wanneer ik een functie oproep en deze aan een variabele toewijs, controleer ik deze voor `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-240">Anytime I call a function and assign it to a variable, I check it for `$null`.</span></span>

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

<span data-ttu-id="52ce2-241">Ik wil veel voor keur gebruiken `if` of `foreach` gebruiken `try/catch` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-241">I much prefer using `if` or `foreach` over using `try/catch`.</span></span> <span data-ttu-id="52ce2-242">Krijg ik niet mis, ik gebruik nog steeds `try/catch` een hoop.</span><span class="sxs-lookup"><span data-stu-id="52ce2-242">Don't get me wrong, I still use `try/catch` a lot.</span></span> <span data-ttu-id="52ce2-243">Maar als ik op een fout voorwaarde of een lege set resultaten kan testen, kan ik mijn uitzonderings afhandeling toestaan voor echte uitzonde ringen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-243">But if I can test for an error condition or an empty set of results, I can allow my exception handling be for true exceptions.</span></span>

<span data-ttu-id="52ce2-244">Er wordt ook in de praktijk gecontroleerd `$null` of er een waarde is voor een-object of om methoden aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-244">I also tend to check for `$null` before I index into a value or call methods on an object.</span></span> <span data-ttu-id="52ce2-245">Deze twee acties mislukken voor een `$null` object, zodat het belang rijk is om het eerst te valideren.</span><span class="sxs-lookup"><span data-stu-id="52ce2-245">These two actions fail for a `$null` object so I find it important to validate them first.</span></span> <span data-ttu-id="52ce2-246">Ik heb deze scenario's al eerder in dit bericht behandeld.</span><span class="sxs-lookup"><span data-stu-id="52ce2-246">I already covered those scenarios earlier in this post.</span></span>

### <a name="no-results-scenario"></a><span data-ttu-id="52ce2-247">Scenario met geen resultaten</span><span class="sxs-lookup"><span data-stu-id="52ce2-247">No results scenario</span></span>

<span data-ttu-id="52ce2-248">Het is belang rijk om te weten dat verschillende functies en opdrachten het scenario voor geen resultaten anders afhandelen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-248">It's important to know that different functions and commands handle the no results scenario differently.</span></span> <span data-ttu-id="52ce2-249">Veel Power shell-opdrachten retour neren de lege `$null` en een fout in de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="52ce2-249">Many PowerShell commands return the empty `$null` and an error in the error stream.</span></span> <span data-ttu-id="52ce2-250">Maar andere veroorzaken uitzonde ringen of bieden u een status object.</span><span class="sxs-lookup"><span data-stu-id="52ce2-250">But others throw exceptions or give you a status object.</span></span> <span data-ttu-id="52ce2-251">Het is nog steeds aan u om te weten hoe de opdrachten die u gebruikt, geen resultaten en fout scenario's opleveren.</span><span class="sxs-lookup"><span data-stu-id="52ce2-251">It's still up to you to know how the commands you use deal with the no results and error scenarios.</span></span>

## <a name="initializing-to-null"></a><span data-ttu-id="52ce2-252">Initialiseren naar $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-252">Initializing to $null</span></span>

<span data-ttu-id="52ce2-253">Eén gewoonte die ik heb gekozen, initialiseert al mijn variabelen voordat ik ze gebruik.</span><span class="sxs-lookup"><span data-stu-id="52ce2-253">One habit that I have picked up is initializing all my variables before I use them.</span></span> <span data-ttu-id="52ce2-254">U moet dit doen in andere talen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-254">You are required to do this in other languages.</span></span> <span data-ttu-id="52ce2-255">Aan de bovenkant van mijn functie of als ik een foreach-lus Voer, definieer ik alle waarden die ik gebruik.</span><span class="sxs-lookup"><span data-stu-id="52ce2-255">At the top of my function or as I enter a foreach loop, I define all the values that I'm using.</span></span>

<span data-ttu-id="52ce2-256">Hier volgt een scenario waarin u een close-out wilt maken.</span><span class="sxs-lookup"><span data-stu-id="52ce2-256">Here is a scenario that I want you to take a close look at.</span></span> <span data-ttu-id="52ce2-257">Dit is een voor beeld van een bug die ik eerder moest opsporen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-257">It's an example of a bug I had to chase down before.</span></span>

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

<span data-ttu-id="52ce2-258">De verwachting is dat `Get-Something` ofwel een resultaat of een lege waarde `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-258">The expectation here is that `Get-Something` returns either a result or an empty `$null`.</span></span> <span data-ttu-id="52ce2-259">Als er een fout optreedt, wordt het geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="52ce2-259">If there is an error, we log it.</span></span> <span data-ttu-id="52ce2-260">Vervolgens controleren we of we een geldig resultaat hebben ontvangen voordat we het verwerken.</span><span class="sxs-lookup"><span data-stu-id="52ce2-260">Then we check to make sure we got a valid result before processing it.</span></span>

<span data-ttu-id="52ce2-261">De fout bij het verbergen van deze code is wanneer `Get-Something` een uitzonde ring wordt gegenereerd en er geen waarde aan wordt toegewezen `$result` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-261">The bug hiding in this code is when `Get-Something` throws an exception and doesn't assign a value to `$result`.</span></span> <span data-ttu-id="52ce2-262">Dit mislukt vóór de toewijzing, dus we gaan niet zelfs `$null` toe aan de `$result` variabele.</span><span class="sxs-lookup"><span data-stu-id="52ce2-262">It fails before the assignment so we don't even assign `$null` to the `$result` variable.</span></span> <span data-ttu-id="52ce2-263">`$result`bevat nog steeds de voor gaande geldige `$result` van andere herhalingen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-263">`$result` still contains the previous valid `$result` from other iterations.</span></span>
<span data-ttu-id="52ce2-264">`Update-Something`meerdere keren uitvoeren op hetzelfde object in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="52ce2-264">`Update-Something` to execute multiple times on the same object in this example.</span></span>

<span data-ttu-id="52ce2-265">Ik ben ingesteld `$result` op `$null` rechts in de foreach-lus voordat ik deze gebruik om dit probleem te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-265">I set `$result` to `$null` right inside the foreach loop before I use it to mitigate this issue.</span></span>

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a><span data-ttu-id="52ce2-266">Scope problemen</span><span class="sxs-lookup"><span data-stu-id="52ce2-266">Scope issues</span></span>

<span data-ttu-id="52ce2-267">Dit helpt ook bij het beperken van problemen met scopes.</span><span class="sxs-lookup"><span data-stu-id="52ce2-267">This also helps mitigate scoping issues.</span></span> <span data-ttu-id="52ce2-268">In dit voor beeld wijzen we waarden toe aan `$result` boven en boven in een lus.</span><span class="sxs-lookup"><span data-stu-id="52ce2-268">In that example, we assign values to `$result` over and over in a loop.</span></span> <span data-ttu-id="52ce2-269">Maar omdat in Power shell variabele waarden van buiten de functie kunnen worden verkleind tot het bereik van de huidige functie, worden de fouten die op die manier kunnen worden geïnitialiseerd, in de functie opgelost.</span><span class="sxs-lookup"><span data-stu-id="52ce2-269">But because PowerShell allows variable values from outside the function to bleed into the scope of the current function, initializing them inside your function mitigates bugs that can be introduced that way.</span></span>

<span data-ttu-id="52ce2-270">Een niet-geïnitialiseerde variabele in de functie is niet `$null` als deze is ingesteld op een waarde in een bovenliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="52ce2-270">An uninitialized variable in your function is not `$null` if it's set to a value in a parent scope.</span></span>
<span data-ttu-id="52ce2-271">Het bovenliggende bereik kan een andere functie zijn die de functie aanroept en dezelfde variabele namen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="52ce2-271">The parent scope could be another function that calls your function and uses the same variable names.</span></span>

<span data-ttu-id="52ce2-272">Als ik hetzelfde `Do-something` voor beeld doe en de lus Verwijder, zou ik uiteindelijk iets zien dat er ongeveer zo uitziet als in dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="52ce2-272">If I take that same `Do-something` example and remove the loop, I would end up with something that looks like this example:</span></span>

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

<span data-ttu-id="52ce2-273">Als de aanroep `Get-Something` een uitzonde ring genereert, zoekt mijn `$null` controle de `$result` van `Invoke-Something` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-273">If the call to `Get-Something` throws an exception, then my `$null` check finds the `$result` from `Invoke-Something`.</span></span> <span data-ttu-id="52ce2-274">Het initialiseren van de waarde in de functie vermindert dit probleem.</span><span class="sxs-lookup"><span data-stu-id="52ce2-274">Initializing the value inside your function mitigates this issue.</span></span>

<span data-ttu-id="52ce2-275">Naamgevings variabelen zijn moeilijk en het is gebruikelijk dat een auteur dezelfde namen van variabelen in meerdere functies gebruikt.</span><span class="sxs-lookup"><span data-stu-id="52ce2-275">Naming variables is hard and it's common for an author to use the same variable names in multiple functions.</span></span> <span data-ttu-id="52ce2-276">Ik weet dat ik `$node` , `$result` ,, `$data` altijd.</span><span class="sxs-lookup"><span data-stu-id="52ce2-276">I know I use `$node`,`$result`,`$data` all the time.</span></span> <span data-ttu-id="52ce2-277">Het is dus heel eenvoudig om waarden uit verschillende bereiken weer te geven op plaatsen waar ze niet mogen zijn.</span><span class="sxs-lookup"><span data-stu-id="52ce2-277">So it would be very easy for values from different scopes to show up in places where they should not be.</span></span>

## <a name="redirect-output-to-null"></a><span data-ttu-id="52ce2-278">Uitvoer omleiden naar $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-278">Redirect output to $null</span></span>

<span data-ttu-id="52ce2-279">Ik heb op de hoogte `$null` van de waarden voor dit hele artikel, maar het onderwerp is niet voltooid als er geen omleidings uitvoer naar wordt vermeld `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-279">I have been talking about `$null` values for this entire article but the topic is not complete if I didn't mention redirecting output to `$null`.</span></span> <span data-ttu-id="52ce2-280">Er zijn momenten waarop u opdrachten kunt uitvoeren die gegevens of objecten bevatten die u wilt onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="52ce2-280">There are times when you have commands that output information or objects that you want to suppress.</span></span> <span data-ttu-id="52ce2-281">Uitvoer omleiden naar `$null` is dat.</span><span class="sxs-lookup"><span data-stu-id="52ce2-281">Redirecting output to `$null` does that.</span></span>

### <a name="out-null"></a><span data-ttu-id="52ce2-282">Out-Null</span><span class="sxs-lookup"><span data-stu-id="52ce2-282">Out-Null</span></span>

<span data-ttu-id="52ce2-283">De out-null-opdracht is de ingebouwde manier om pijplijn gegevens om te leiden naar `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-283">The Out-Null command is the built-in way to redirect pipeline data to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a><span data-ttu-id="52ce2-284">Toewijzen aan $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-284">Assign to $null</span></span>

<span data-ttu-id="52ce2-285">U kunt de resultaten van een opdracht toewijzen aan `$null` voor hetzelfde effect als met `Out-Null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-285">You can assign the results of a command to `$null` for the same effect as using `Out-Null`.</span></span>

```powershell
$null = New-Item -Type Directory -Path $path
```

<span data-ttu-id="52ce2-286">Omdat `$null` een constante waarde is, kunt u deze nooit overschrijven.</span><span class="sxs-lookup"><span data-stu-id="52ce2-286">Because `$null` is a constant value, you can never overwrite it.</span></span> <span data-ttu-id="52ce2-287">Ik vind het niet mooi dat deze in mijn code wordt weer gegeven, maar dit wordt vaak sneller uitgevoerd dan `Out-Null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-287">I don't like the way it looks in my code but it often performs faster than `Out-Null`.</span></span>

### <a name="redirect-to-null"></a><span data-ttu-id="52ce2-288">Omleiden naar $null</span><span class="sxs-lookup"><span data-stu-id="52ce2-288">Redirect to $null</span></span>

<span data-ttu-id="52ce2-289">U kunt ook de omleidings operator gebruiken om uitvoer naar te verzenden `$null` .</span><span class="sxs-lookup"><span data-stu-id="52ce2-289">You can also use the redirection operator to send output to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path > $null
```

<span data-ttu-id="52ce2-290">Als u werkt met opdracht regel uitvoer bare bestanden die worden uitgevoerd op de verschillende stromen.</span><span class="sxs-lookup"><span data-stu-id="52ce2-290">If you're dealing with command-line executables that output on the different streams.</span></span> <span data-ttu-id="52ce2-291">U kunt alle uitvoer stromen als volgt omleiden `$null` :</span><span class="sxs-lookup"><span data-stu-id="52ce2-291">You can redirect all output streams to `$null` like this:</span></span>

```powershell
git status *> $null
```

## <a name="summary"></a><span data-ttu-id="52ce2-292">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="52ce2-292">Summary</span></span>

<span data-ttu-id="52ce2-293">Ik heb veel aan de slag op deze ene en ik weet dat dit artikel meer is gefragmenteerd dan het meeste van mijn diepe Dives.</span><span class="sxs-lookup"><span data-stu-id="52ce2-293">I covered a lot of ground on this one and I know this article is more fragmented than most of my deep dives.</span></span> <span data-ttu-id="52ce2-294">Dat komt doordat `$null` waarden in een groot aantal verschillende locaties in Power shell kunnen worden pop-ups en alle nuances zijn specifiek voor de locatie waar u deze kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="52ce2-294">That is because `$null` values can pop up in many different places in PowerShell and all the nuances are specific to where you find it.</span></span> <span data-ttu-id="52ce2-295">Ik hoop dat u dit niet kunt doen met een beter inzicht in en een duidelijk beeld van `$null` de meer onduidelijke scenario's die u kunt uitvoeren in.</span><span class="sxs-lookup"><span data-stu-id="52ce2-295">I hope you walk away from this with a better understanding of `$null` and an awareness of the more obscure scenarios you may run into.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[goede post]: https://blog.iisreset.me/schrodingers-argumentlist
[good post]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System. Management. Automation. internal. AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
