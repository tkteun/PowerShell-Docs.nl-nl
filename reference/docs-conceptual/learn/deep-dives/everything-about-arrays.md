---
title: Alles wat u wilt weten over matrices
description: Matrices zijn een fundamentele taal functie van de meeste programmeer talen.
ms.date: 10/08/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: b26aa11aadbeea1984b2754cfcad061c7fa3ff1e
ms.sourcegitcommit: 3445a343e0683124652f64abef6fe911f9eb989f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/08/2020
ms.locfileid: "91852558"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a><span data-ttu-id="72312-103">Alles wat u wilt weten over matrices</span><span class="sxs-lookup"><span data-stu-id="72312-103">Everything you wanted to know about arrays</span></span>

<span data-ttu-id="72312-104">[Matrices][] zijn een fundamentele taal functie van de meeste programmeer talen.</span><span class="sxs-lookup"><span data-stu-id="72312-104">[Arrays][] are a fundamental language feature of most programming languages.</span></span> <span data-ttu-id="72312-105">Ze zijn een verzameling waarden of objecten die moeilijk te voor komen zijn.</span><span class="sxs-lookup"><span data-stu-id="72312-105">They're a collection of values or objects that are difficult to avoid.</span></span> <span data-ttu-id="72312-106">Laten we eens kijken naar matrices en alles wat ze te bieden hebben.</span><span class="sxs-lookup"><span data-stu-id="72312-106">Let's take a close look at arrays and everything they have to offer.</span></span>

> [!NOTE]
> <span data-ttu-id="72312-107">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="72312-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="72312-108">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="72312-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="72312-109">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="72312-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="72312-110">Wat is een matrix?</span><span class="sxs-lookup"><span data-stu-id="72312-110">What is an array?</span></span>

<span data-ttu-id="72312-111">Ik ga aan de slag met een eenvoudige technische beschrijving van de arrays en hoe deze worden gebruikt door de meeste programmeer talen voordat ik de andere manieren in Power shell gebruikt om deze te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="72312-111">I'm going to start with a basic technical description of what arrays are and how they are used by most programming languages before I shift into the other ways PowerShell makes use of them.</span></span>

<span data-ttu-id="72312-112">Een matrix is een gegevens structuur die fungeert als verzameling van meerdere items.</span><span class="sxs-lookup"><span data-stu-id="72312-112">An array is a data structure that serves as a collection of multiple items.</span></span> <span data-ttu-id="72312-113">U kunt de matrix herhalen of toegang krijgen tot afzonderlijke items met behulp van een index.</span><span class="sxs-lookup"><span data-stu-id="72312-113">You can iterate over the array or access individual items using an index.</span></span> <span data-ttu-id="72312-114">De matrix wordt gemaakt als opeenvolgend geheugen waarbij elke waarde direct naast het andere wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="72312-114">The array is created as a sequential chunk of memory where each value is stored right next to the other.</span></span>

<span data-ttu-id="72312-115">Ik raak aan elk van deze gegevens tijdens het bezoek.</span><span class="sxs-lookup"><span data-stu-id="72312-115">I'll touch on each of those details as we go.</span></span>

## <a name="basic-usage"></a><span data-ttu-id="72312-116">Basisgebruik</span><span class="sxs-lookup"><span data-stu-id="72312-116">Basic usage</span></span>

<span data-ttu-id="72312-117">Omdat matrices een van de basis functies van Power shell zijn, is er een eenvoudige syntaxis voor het werken met deze in Power shell.</span><span class="sxs-lookup"><span data-stu-id="72312-117">Because arrays are such a basic feature of PowerShell, there is a simple syntax for working with them in PowerShell.</span></span>

### <a name="create-an-array"></a><span data-ttu-id="72312-118">Een matrix maken</span><span class="sxs-lookup"><span data-stu-id="72312-118">Create an array</span></span>

<span data-ttu-id="72312-119">Een lege matrix kan worden gemaakt met behulp van `@()`</span><span class="sxs-lookup"><span data-stu-id="72312-119">An empty array can be created by using `@()`</span></span>

```powershell
PS> $data = @()
PS> $data.count
0
```

<span data-ttu-id="72312-120">We kunnen een matrix maken en deze met waarden seeden door ze te plaatsen in de `@()` haakjes.</span><span class="sxs-lookup"><span data-stu-id="72312-120">We can create an array and seed it with values just by placing them in the `@()` parentheses.</span></span>

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

<span data-ttu-id="72312-121">Deze matrix heeft 4 items.</span><span class="sxs-lookup"><span data-stu-id="72312-121">This array has 4 items.</span></span> <span data-ttu-id="72312-122">Wanneer we de variabele aanroepen `$data` , zien we de lijst met onze items.</span><span class="sxs-lookup"><span data-stu-id="72312-122">When we call the `$data` variable, we see the list of our items.</span></span> <span data-ttu-id="72312-123">Als het een matrix met teken reeksen is, krijgen we één regel per teken reeks.</span><span class="sxs-lookup"><span data-stu-id="72312-123">If it's an array of strings, then we get one line per string.</span></span>

<span data-ttu-id="72312-124">We kunnen een matrix op meerdere regels declareren.</span><span class="sxs-lookup"><span data-stu-id="72312-124">We can declare an array on multiple lines.</span></span> <span data-ttu-id="72312-125">In dit geval is de komma optioneel en links gelaten.</span><span class="sxs-lookup"><span data-stu-id="72312-125">The comma is optional in this case and generally left out.</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

<span data-ttu-id="72312-126">Ik wil graag mijn arrays declareren op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="72312-126">I prefer to declare my arrays on multiple lines like that.</span></span> <span data-ttu-id="72312-127">Het is niet alleen gemakkelijker te lezen wanneer u meerdere items hebt, maar maakt het gemakkelijker om te vergelijken met vorige versies wanneer u broncode beheer gebruikt.</span><span class="sxs-lookup"><span data-stu-id="72312-127">Not only does it get easier to read when you have multiple items, it also makes it easier to compare to previous versions when using source control.</span></span>

#### <a name="other-syntax"></a><span data-ttu-id="72312-128">Andere syntaxis</span><span class="sxs-lookup"><span data-stu-id="72312-128">Other syntax</span></span>

<span data-ttu-id="72312-129">Het `@()` is vaak de syntaxis voor het maken van een matrix, maar door komma's gescheiden lijsten werken het meeste tijd.</span><span class="sxs-lookup"><span data-stu-id="72312-129">It's commonly understood that `@()` is the syntax for creating an array, but comma-separated lists work most of the time.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a><span data-ttu-id="72312-130">Write-Output matrix maken</span><span class="sxs-lookup"><span data-stu-id="72312-130">Write-Output to create arrays</span></span>

<span data-ttu-id="72312-131">Eén leuke truc is dat u kunt gebruiken `Write-Output` om snel teken reeksen te maken in de-console.</span><span class="sxs-lookup"><span data-stu-id="72312-131">One cool little trick worth mentioning is that you can use `Write-Output` to quickly create strings at the console.</span></span>

```powershell
$data = Write-Output Zero One Two Three
```

<span data-ttu-id="72312-132">Dit is handig omdat u geen aanhalings tekens rond de teken reeksen hoeft te plaatsen wanneer de para meter teken reeksen accepteert.</span><span class="sxs-lookup"><span data-stu-id="72312-132">This is handy because you don't have to put quotes around the strings when the parameter accepts strings.</span></span> <span data-ttu-id="72312-133">Ik zou dit nooit doen in een script, maar het is wel een redelijk spel in de console.</span><span class="sxs-lookup"><span data-stu-id="72312-133">I would never do this in a script but it's fair game in the console.</span></span>

### <a name="accessing-items"></a><span data-ttu-id="72312-134">Toegang tot items</span><span class="sxs-lookup"><span data-stu-id="72312-134">Accessing items</span></span>

<span data-ttu-id="72312-135">Nu u een matrix met items hebt, wilt u deze items mogelijk openen en bijwerken.</span><span class="sxs-lookup"><span data-stu-id="72312-135">Now that you have an array with items in it, you may want to access and update those items.</span></span>

#### <a name="offset"></a><span data-ttu-id="72312-136">Offset</span><span class="sxs-lookup"><span data-stu-id="72312-136">Offset</span></span>

<span data-ttu-id="72312-137">Voor toegang tot afzonderlijke items gebruiken we de haakjes `[]` met een offset waarde die begint bij 0.</span><span class="sxs-lookup"><span data-stu-id="72312-137">To access individual items, we use the brackets `[]` with an offset value starting at 0.</span></span> <span data-ttu-id="72312-138">Zo wordt het eerste item in onze matrix opgehaald:</span><span class="sxs-lookup"><span data-stu-id="72312-138">This is how we get the first item in our array:</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

<span data-ttu-id="72312-139">De reden waarom we hier nul voor gebruiken, is omdat het eerste item zich aan het begin van de lijst bevindt, zodat we een offset van 0 items gebruiken om ernaar te gaan.</span><span class="sxs-lookup"><span data-stu-id="72312-139">The reason why we use zero here is because the first item is at the beginning of the list so we use an offset of 0 items to get to it.</span></span> <span data-ttu-id="72312-140">Als u naar het tweede item wilt gaan, moet u een offset van 1 gebruiken om het eerste item over te slaan.</span><span class="sxs-lookup"><span data-stu-id="72312-140">To get to the second item, we would need to use an offset of 1 to skip the first item.</span></span>

```powershell
PS> $data[1]
One
```

<span data-ttu-id="72312-141">Dit betekent dat het laatste item zich op offset 3 bevindt.</span><span class="sxs-lookup"><span data-stu-id="72312-141">This would mean that the last item is at offset 3.</span></span>

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a><span data-ttu-id="72312-142">Index</span><span class="sxs-lookup"><span data-stu-id="72312-142">Index</span></span>

<span data-ttu-id="72312-143">Nu kunt u zien waarom ik de waarden voor dit voor beeld heb gekozen.</span><span class="sxs-lookup"><span data-stu-id="72312-143">Now you can see why I picked the values that I did for this example.</span></span> <span data-ttu-id="72312-144">Ik heb dit als een offset geïntroduceerd, omdat dat echt is, maar deze offset wordt vaak aangeduid als een index.</span><span class="sxs-lookup"><span data-stu-id="72312-144">I introduced this as an offset because that is what it really is, but this offset is more commonly referred to as an index.</span></span> <span data-ttu-id="72312-145">Een index die begint bij `0` .</span><span class="sxs-lookup"><span data-stu-id="72312-145">An index that starts at `0`.</span></span> <span data-ttu-id="72312-146">In de rest van dit artikel noemen we de offset een index.</span><span class="sxs-lookup"><span data-stu-id="72312-146">For the rest of this article I will call the offset an index.</span></span>

#### <a name="special-index-tricks"></a><span data-ttu-id="72312-147">Speciale index slagen</span><span class="sxs-lookup"><span data-stu-id="72312-147">Special index tricks</span></span>

<span data-ttu-id="72312-148">In de meeste talen kunt u slechts één getal opgeven als de index en krijgt u één item terug.</span><span class="sxs-lookup"><span data-stu-id="72312-148">In most languages, you can only specify a single number as the index and you get a single item back.</span></span>
<span data-ttu-id="72312-149">Power shell is veel flexibeler.</span><span class="sxs-lookup"><span data-stu-id="72312-149">PowerShell is much more flexible.</span></span> <span data-ttu-id="72312-150">U kunt meerdere indexen tegelijk gebruiken.</span><span class="sxs-lookup"><span data-stu-id="72312-150">You can use multiple indexes at once.</span></span> <span data-ttu-id="72312-151">Als u een lijst met indexen opgeeft, kunnen we verschillende items selecteren.</span><span class="sxs-lookup"><span data-stu-id="72312-151">By providing a list of indexes, we can select several items.</span></span>

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

<span data-ttu-id="72312-152">De items worden geretourneerd op basis van de volg orde van de opgegeven indexen.</span><span class="sxs-lookup"><span data-stu-id="72312-152">The items are returned based on the order of the indexes provided.</span></span> <span data-ttu-id="72312-153">Als u een index dupliceert, krijgt u dat item beide keren.</span><span class="sxs-lookup"><span data-stu-id="72312-153">If you duplicate an index, you get that item both times.</span></span>

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

<span data-ttu-id="72312-154">We kunnen een reeks getallen met de ingebouwde `..` operator opgeven.</span><span class="sxs-lookup"><span data-stu-id="72312-154">We can specify a sequence of numbers with the built-in `..` operator.</span></span>

```powershell
PS> $data[1..3]
One
Two
Three
```

<span data-ttu-id="72312-155">Dit werkt ook in omgekeerde volg orde.</span><span class="sxs-lookup"><span data-stu-id="72312-155">This works in reverse too.</span></span>

```powershell
PS> $data[3..1]
Three
Two
One
```

<span data-ttu-id="72312-156">U kunt negatieve index waarden gebruiken om vanaf het einde te verschuiven.</span><span class="sxs-lookup"><span data-stu-id="72312-156">You can use negative index values to offset from the end.</span></span> <span data-ttu-id="72312-157">Dus als u het laatste item in de lijst nodig hebt, kunt u gebruiken `-1` .</span><span class="sxs-lookup"><span data-stu-id="72312-157">So if you need the last item in the list, you can use `-1`.</span></span>

```powershell
PS> $data[-1]
Three
```

<span data-ttu-id="72312-158">Dit is een woord van voorzichtig met de `..` operator.</span><span class="sxs-lookup"><span data-stu-id="72312-158">One word of caution here with the `..` operator.</span></span> <span data-ttu-id="72312-159">De volg orde `0..-1` en `-1..0` evalueren van de waarden `0,-1` en `-1,0` .</span><span class="sxs-lookup"><span data-stu-id="72312-159">The sequence `0..-1` and `-1..0` evaluate to the values `0,-1` and `-1,0`.</span></span> <span data-ttu-id="72312-160">Het is eenvoudig om te zien en te controleren `$data[0..-1]` of alle items zouden worden opgesomd als u deze details vergeet.</span><span class="sxs-lookup"><span data-stu-id="72312-160">It's easy to see `$data[0..-1]` and think it would enumerate all items if you forget this detail.</span></span> <span data-ttu-id="72312-161">`$data[0..-1]` geeft u dezelfde waarde als `$data[0,-1]` door u het eerste en laatste item in de matrix te geven (en geen van de andere waarden).</span><span class="sxs-lookup"><span data-stu-id="72312-161">`$data[0..-1]` gives you the same value as `$data[0,-1]` by giving you the first and last item in the array (and none of the other values).</span></span>

#### <a name="out-of-bounds"></a><span data-ttu-id="72312-162">Buiten het bereik</span><span class="sxs-lookup"><span data-stu-id="72312-162">Out of bounds</span></span>

<span data-ttu-id="72312-163">Als u in de meeste talen probeert toegang te krijgen tot een index van een item dat zich aan het einde van de matrix bevindt, krijgt u een fout melding of een uitzonde ring.</span><span class="sxs-lookup"><span data-stu-id="72312-163">In most languages, if you try to access an index of an item that is past the end of the array, you would get some type of error or an exception.</span></span> <span data-ttu-id="72312-164">Power shell retourneert niets op de achtergrond.</span><span class="sxs-lookup"><span data-stu-id="72312-164">PowerShell silently returns nothing.</span></span>

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a><span data-ttu-id="72312-165">Kan niet indexeren naar een null-matrix</span><span class="sxs-lookup"><span data-stu-id="72312-165">Cannot index into a null array</span></span>

<span data-ttu-id="72312-166">Als uw variabele is `$null` en u probeert deze te indexeren als een matrix, krijgt u een `System.Management.Automation.RuntimeException` uitzonde ring met het bericht `Cannot index into a null array` .</span><span class="sxs-lookup"><span data-stu-id="72312-166">If your variable is `$null` and you try to index it like an array, you get a `System.Management.Automation.RuntimeException` exception with the message `Cannot index into a null array`.</span></span>

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

<span data-ttu-id="72312-167">Zorg er dus voor dat uw matrices niet `$null` voordat u probeert toegang te krijgen tot elementen erin.</span><span class="sxs-lookup"><span data-stu-id="72312-167">So make sure your arrays are not `$null` before you try to access elements inside them.</span></span>

#### <a name="count"></a><span data-ttu-id="72312-168">Aantal</span><span class="sxs-lookup"><span data-stu-id="72312-168">Count</span></span>

<span data-ttu-id="72312-169">Matrices en andere verzamelingen hebben een eigenschap Count waarmee wordt aangegeven hoeveel items zich in de matrix bevinden.</span><span class="sxs-lookup"><span data-stu-id="72312-169">Arrays and other collections have a count property that tells you how many items are in the array.</span></span>

```powershell
PS> $data.count
4
```

<span data-ttu-id="72312-170">Power Shell 3,0 heeft een eigenschap Count aan de meeste objecten toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="72312-170">PowerShell 3.0 added a count property to most objects.</span></span> <span data-ttu-id="72312-171">u kunt één object hebben en dit moet een aantal van bevatten `1` .</span><span class="sxs-lookup"><span data-stu-id="72312-171">you can have a single object and it should give you a count of `1`.</span></span>

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

<span data-ttu-id="72312-172">`$null`Heeft zelfs een eigenschap Count, behalve het resultaat `0` .</span><span class="sxs-lookup"><span data-stu-id="72312-172">Even `$null` has a count property except it returns `0`.</span></span>

```powershell
PS> $null.count
0
```

<span data-ttu-id="72312-173">Er zijn een aantal traps die hier worden weer gegeven wanneer ik `$null` in dit artikel een controle voor of lege matrices ondervindt.</span><span class="sxs-lookup"><span data-stu-id="72312-173">There are some traps here that I will revisit when I cover checking for `$null` or empty arrays later on in this article.</span></span>

#### <a name="off-by-one-errors"></a><span data-ttu-id="72312-174">Niet-voor-één-fouten</span><span class="sxs-lookup"><span data-stu-id="72312-174">Off-by-one errors</span></span>

<span data-ttu-id="72312-175">Er wordt een veelvoorkomende programmeer fout gemaakt, omdat matrices beginnen bij index 0.</span><span class="sxs-lookup"><span data-stu-id="72312-175">A common programming error is created because arrays start at index 0.</span></span> <span data-ttu-id="72312-176">Er kunnen op twee manieren geen fouten worden geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="72312-176">Off-by-one errors can be introduced in two ways.</span></span>

<span data-ttu-id="72312-177">De eerste is namelijk door denken dat u het tweede item en de index van `2` en echt het derde item wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="72312-177">The first is by mentally thinking you want the second item and using an index of `2` and really getting the third item.</span></span> <span data-ttu-id="72312-178">Of u hebt vier items en u wilt het laatste item gebruiken, dus u gebruikt de telling voor toegang tot het laatste item.</span><span class="sxs-lookup"><span data-stu-id="72312-178">Or by thinking that you have four items and you want last item, so you use the count to access the last item.</span></span>

```powershell
$data[ $data.count ]
```

<span data-ttu-id="72312-179">Power shell is zo blij dat u dit kunt doen en precies aangeven welk item er op index 4 is `$null` .</span><span class="sxs-lookup"><span data-stu-id="72312-179">PowerShell is perfectly happy to let you do that and give you exactly what item exists at index 4: `$null`.</span></span> <span data-ttu-id="72312-180">U moet gebruikmaken `$data.count - 1` van of de `-1` die we hiervoor hebben geleerd.</span><span class="sxs-lookup"><span data-stu-id="72312-180">You should be using `$data.count - 1` or the `-1` that we learned about above.</span></span>

```powershell
PS> $data[ $data.count - 1 ]
Three
```

<span data-ttu-id="72312-181">Hier kunt u de `-1` index gebruiken om het laatste element op te halen.</span><span class="sxs-lookup"><span data-stu-id="72312-181">This is where you can use the `-1` index to get the last element.</span></span>

```powershell
PS> $data[ -1 ]
Three
```

<span data-ttu-id="72312-182">Lee Dailey wijst ook naar me dat we kunnen gebruiken `$data.GetUpperBound(0)` om het maximum aantal indexen te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="72312-182">Lee Dailey also pointed out to me that we can use `$data.GetUpperBound(0)` to get the max index number.</span></span>

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

<span data-ttu-id="72312-183">De tweede meest voorkomende manier is om de lijst te herhalen en niet op het juiste moment te stoppen.</span><span class="sxs-lookup"><span data-stu-id="72312-183">The second most common way is when iterating the list and not stopping at the right time.</span></span> <span data-ttu-id="72312-184">Ik ga hier door met het gebruik van de `for` lus.</span><span class="sxs-lookup"><span data-stu-id="72312-184">I'll revisit this when we talk about using the `for` loop.</span></span>

### <a name="updating-items"></a><span data-ttu-id="72312-185">Items bijwerken</span><span class="sxs-lookup"><span data-stu-id="72312-185">Updating items</span></span>

<span data-ttu-id="72312-186">We kunnen dezelfde index gebruiken om bestaande items in de matrix bij te werken.</span><span class="sxs-lookup"><span data-stu-id="72312-186">We can use the same index to update existing items in the array.</span></span> <span data-ttu-id="72312-187">Dit biedt directe toegang tot het bijwerken van afzonderlijke items.</span><span class="sxs-lookup"><span data-stu-id="72312-187">This gives us direct access to update individual items.</span></span>

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

<span data-ttu-id="72312-188">Als we proberen een item bij te werken dat zich in het laatste element bevindt, wordt er een `Index was outside the bounds of the array.` fout bericht weer geven.</span><span class="sxs-lookup"><span data-stu-id="72312-188">If we try to update an item that is past the last element, then we get an `Index was outside the bounds of the array.` error.</span></span>

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

<span data-ttu-id="72312-189">Ik ga deze later opnieuw door als ik praat over hoe u een matrix groter kunt maken.</span><span class="sxs-lookup"><span data-stu-id="72312-189">I'll revisit this later when I talk about how to make an array larger.</span></span>

### <a name="iteration"></a><span data-ttu-id="72312-190">Iteratie</span><span class="sxs-lookup"><span data-stu-id="72312-190">Iteration</span></span>

<span data-ttu-id="72312-191">Op een bepaald moment moet u mogelijk de hele lijst door lopen of herhalen en een aantal acties uitvoeren voor elk item in de matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-191">At some point, you might need to walk or iterate the entire list and perform some action for each item in the array.</span></span>

#### <a name="pipeline"></a><span data-ttu-id="72312-192">Pijplijn</span><span class="sxs-lookup"><span data-stu-id="72312-192">Pipeline</span></span>

<span data-ttu-id="72312-193">Matrices en de Power shell-pijp lijn zijn bedoeld voor elkaar.</span><span class="sxs-lookup"><span data-stu-id="72312-193">Arrays and the PowerShell pipeline are meant for each other.</span></span> <span data-ttu-id="72312-194">Dit is een van de eenvoudigste manieren om deze waarden te verwerken.</span><span class="sxs-lookup"><span data-stu-id="72312-194">This is one of the simplest ways to process over those values.</span></span> <span data-ttu-id="72312-195">Wanneer u een matrix doorgeeft aan een pijp lijn, wordt elk item in de matrix afzonderlijk verwerkt.</span><span class="sxs-lookup"><span data-stu-id="72312-195">When you pass an array to a pipeline, each item inside the array is processed individually.</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

<span data-ttu-id="72312-196">Als u nog niet eerder hebt gezien `$PSItem` , weet u zeker dat het hetzelfde is als `$_` .</span><span class="sxs-lookup"><span data-stu-id="72312-196">If you have not seen `$PSItem` before, just know that it's the same thing as `$_`.</span></span> <span data-ttu-id="72312-197">U kunt een van beide gebruiken omdat beide het huidige object in de pijp lijn vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="72312-197">You can use either one because they both represent the current object in the pipeline.</span></span>

#### <a name="foreach-loop"></a><span data-ttu-id="72312-198">ForEach-lus</span><span class="sxs-lookup"><span data-stu-id="72312-198">ForEach loop</span></span>

<span data-ttu-id="72312-199">De `ForEach` lus werkt goed met verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="72312-199">The `ForEach` loop works well with collections.</span></span> <span data-ttu-id="72312-200">Met de syntaxis: `foreach ( <variable> in <collection> )`</span><span class="sxs-lookup"><span data-stu-id="72312-200">Using the syntax: `foreach ( <variable> in <collection> )`</span></span>

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a><span data-ttu-id="72312-201">ForEach-methode</span><span class="sxs-lookup"><span data-stu-id="72312-201">ForEach method</span></span>

<span data-ttu-id="72312-202">Ik vergeet dit maar over dit abonnement, maar het werkt goed voor eenvoudige bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="72312-202">I tend to forget about this one but it works well for simple operations.</span></span> <span data-ttu-id="72312-203">Met Power shell kunt u aanroepen `.ForEach()` voor een verzameling.</span><span class="sxs-lookup"><span data-stu-id="72312-203">PowerShell allows you to call `.ForEach()` on a collection.</span></span>

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

<span data-ttu-id="72312-204">`.foreach()`Er wordt een para meter met een script blok gebruikt.</span><span class="sxs-lookup"><span data-stu-id="72312-204">The `.foreach()` takes a parameter that is a script block.</span></span> <span data-ttu-id="72312-205">U kunt de haakjes verwijderen en alleen het script blok opgeven.</span><span class="sxs-lookup"><span data-stu-id="72312-205">You can drop the parentheses and just provide the script block.</span></span>

```powershell
$data.foreach{"Item [$PSItem]"}
```

<span data-ttu-id="72312-206">Dit is een minder bekende syntaxis, maar werkt precies hetzelfde.</span><span class="sxs-lookup"><span data-stu-id="72312-206">This is a lesser known syntax but it works just the same.</span></span> <span data-ttu-id="72312-207">Deze `foreach` methode is toegevoegd in Power shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="72312-207">This `foreach` method was added in PowerShell 4.0.</span></span>

#### <a name="for-loop"></a><span data-ttu-id="72312-208">For-lus</span><span class="sxs-lookup"><span data-stu-id="72312-208">For loop</span></span>

<span data-ttu-id="72312-209">De `for` lus wordt sterk in de meeste andere talen gebruikt, maar u ziet deze niet veel in Power shell.</span><span class="sxs-lookup"><span data-stu-id="72312-209">The `for` loop is used heavily in most other languages but you don't see it much in PowerShell.</span></span> <span data-ttu-id="72312-210">Wanneer u dit ziet, is dit vaak in de context van een matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-210">When you do see it, it's often in the context of walking an array.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="72312-211">Het eerste wat we doen, initialiseren van een `$index` naar `0` .</span><span class="sxs-lookup"><span data-stu-id="72312-211">The first thing we do is initialize an `$index` to `0`.</span></span> <span data-ttu-id="72312-212">Vervolgens voegen we de voor waarde toe die `$index` kleiner moet zijn dan `$data.count` .</span><span class="sxs-lookup"><span data-stu-id="72312-212">Then we add the condition that `$index` must be less than `$data.count`.</span></span> <span data-ttu-id="72312-213">Ten slotte geven we op dat elke keer dat ik de index moet verg Roten `1` .</span><span class="sxs-lookup"><span data-stu-id="72312-213">Finally, we specify that every time we loop that me must increase the index by `1`.</span></span> <span data-ttu-id="72312-214">In dit geval `$index++` is de enige korte voor `$index = $index + 1` .</span><span class="sxs-lookup"><span data-stu-id="72312-214">In this case `$index++` is short for `$index = $index + 1`.</span></span>

<span data-ttu-id="72312-215">Wanneer u een lus gebruikt `for` , moet u speciale aandacht schenken aan de voor waarde.</span><span class="sxs-lookup"><span data-stu-id="72312-215">Whenever you're using a `for` loop, pay special attention to the condition.</span></span> <span data-ttu-id="72312-216">Hier gebruikt u `$index -lt $data.count` .</span><span class="sxs-lookup"><span data-stu-id="72312-216">I used `$index -lt $data.count` here.</span></span> <span data-ttu-id="72312-217">Het is eenvoudig om de voor waarde iets verkeerd te krijgen om een fout in uw logica op te halen.</span><span class="sxs-lookup"><span data-stu-id="72312-217">It's easy to get the condition slightly wrong to get an off-by-one error in your logic.</span></span> <span data-ttu-id="72312-218">Het gebruik `$index -le $data.count` of `$index -lt ($data.count - 1)` ooit is iets verkeerd.</span><span class="sxs-lookup"><span data-stu-id="72312-218">Using `$index -le $data.count` or `$index -lt ($data.count - 1)` are ever so slightly wrong.</span></span> <span data-ttu-id="72312-219">Dit kan ertoe leiden dat er te veel of te weinig items worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="72312-219">That would cause your result to process too many or too few items.</span></span> <span data-ttu-id="72312-220">Dit is een onklassieke fout.</span><span class="sxs-lookup"><span data-stu-id="72312-220">This is the classic off-by-one error.</span></span>

#### <a name="switch-loop"></a><span data-ttu-id="72312-221">Switch herhalen</span><span class="sxs-lookup"><span data-stu-id="72312-221">Switch loop</span></span>

<span data-ttu-id="72312-222">Dit is een gemakkelijk te herspeld abonnement.</span><span class="sxs-lookup"><span data-stu-id="72312-222">This is one that is easy to overlook.</span></span> <span data-ttu-id="72312-223">Als u een matrix voor een [Switch-instructie][]opgeeft, wordt elk item in de matrix gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="72312-223">If you provide an array to a [switch statement][], it checks each item in the array.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

<span data-ttu-id="72312-224">Er zijn veel leuke dingen die u kunt doen met de switch-instructie.</span><span class="sxs-lookup"><span data-stu-id="72312-224">There are a lot of cool things that we can do with the switch statement.</span></span> <span data-ttu-id="72312-225">Ik heb een ander artikel dat hieraan is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="72312-225">I have another article dedicated to this.</span></span>

- <span data-ttu-id="72312-226">[Alles wat u zou weten over de][instructie] switch-instructie switch</span><span class="sxs-lookup"><span data-stu-id="72312-226">[Everything you ever wanted to know about the switch statement][switch statement]</span></span>

#### <a name="updating-values"></a><span data-ttu-id="72312-227">Waarden worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="72312-227">Updating values</span></span>

<span data-ttu-id="72312-228">Als uw matrix een verzameling teken reeksen of gehele getallen (waardetypen) is, wilt u misschien de waarden in de matrix bijwerken tijdens de lus.</span><span class="sxs-lookup"><span data-stu-id="72312-228">When your array is a collection of string or integers (value types), sometimes you may want to update the values in the array as you loop over them.</span></span> <span data-ttu-id="72312-229">De meeste lussen hierboven gebruiken een variabele in de lus die een kopie van de waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="72312-229">Most of the loops above use a variable in the loop that holds a copy of the value.</span></span> <span data-ttu-id="72312-230">Als u die variabele bijwerkt, wordt de oorspronkelijke waarde in de matrix niet bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="72312-230">If you update that variable, the original value in the array is not updated.</span></span>

<span data-ttu-id="72312-231">De uitzonde ring op die instructie is de `for` lus.</span><span class="sxs-lookup"><span data-stu-id="72312-231">The exception to that statement is the `for` loop.</span></span> <span data-ttu-id="72312-232">Als u een matrix wilt bekijken en waarden hierin wilt bijwerken, `for` is de lus wat u zoekt.</span><span class="sxs-lookup"><span data-stu-id="72312-232">If you want to walk an array and update values inside it, then the `for` loop is what you're looking for.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="72312-233">In dit voor beeld wordt een waarde gesorteerd op index, worden enkele wijzigingen aangebracht en wordt dezelfde index vervolgens gebruikt om deze weer toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="72312-233">This example takes a value by index, makes a few changes, and then uses that same index to assign it back.</span></span>

## <a name="arrays-of-objects"></a><span data-ttu-id="72312-234">Matrices van objecten</span><span class="sxs-lookup"><span data-stu-id="72312-234">Arrays of Objects</span></span>

<span data-ttu-id="72312-235">Tot nu toe is het enige wat we in een matrix hebben geplaatst, een Waardetype, maar matrices kunnen ook objecten bevatten.</span><span class="sxs-lookup"><span data-stu-id="72312-235">So far, the only thing we've placed in an array is a value type, but arrays can also contain objects.</span></span>

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

<span data-ttu-id="72312-236">Veel cmdlets retour neren verzamelingen objecten als matrices wanneer u deze toewijst aan een variabele.</span><span class="sxs-lookup"><span data-stu-id="72312-236">Many cmdlets return collections of objects as arrays when you assign them to a variable.</span></span>

```powershell
$processList = Get-Process
```

<span data-ttu-id="72312-237">Alle basis functies die al eerder zijn besproken, zijn nog steeds van toepassing op arrays van objecten met enkele details die u moet aanwijzen.</span><span class="sxs-lookup"><span data-stu-id="72312-237">All of the basic features we already talked about still apply to arrays of objects with a few details worth pointing out.</span></span>

### <a name="accessing-properties"></a><span data-ttu-id="72312-238">Eigenschappen openen</span><span class="sxs-lookup"><span data-stu-id="72312-238">Accessing properties</span></span>

<span data-ttu-id="72312-239">We kunnen een index gebruiken om toegang te krijgen tot een afzonderlijk item in een verzameling, net als bij waardetypen.</span><span class="sxs-lookup"><span data-stu-id="72312-239">We can use an index to access an individual item in a collection just like with value types.</span></span>

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="72312-240">We kunnen eigenschappen rechtstreeks openen en bijwerken.</span><span class="sxs-lookup"><span data-stu-id="72312-240">We can access and update properties directly.</span></span>

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a><span data-ttu-id="72312-241">Matrix eigenschappen</span><span class="sxs-lookup"><span data-stu-id="72312-241">Array properties</span></span>

<span data-ttu-id="72312-242">Normaal gesp roken moet u de hele lijst als zodanig opsommen voor toegang tot alle eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="72312-242">Normally you would have to enumerate the whole list like this to access all the properties:</span></span>

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

<span data-ttu-id="72312-243">Of met behulp van de- `Select-Object -ExpandProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72312-243">Or by using the `Select-Object -ExpandProperty` cmdlet.</span></span>

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

<span data-ttu-id="72312-244">Maar Power shell biedt ons de mogelijkheid om rechtstreeks aan te vragen `LastName` .</span><span class="sxs-lookup"><span data-stu-id="72312-244">But PowerShell offers us the ability to request `LastName` directly.</span></span> <span data-ttu-id="72312-245">In Power shell worden alle bestanden voor ons opgesomd en wordt een schone lijst weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="72312-245">PowerShell enumerates them all for us and returns a clean list.</span></span>

```powershell
PS> $data.LastName

Marquette
Doe
```

<span data-ttu-id="72312-246">De inventarisatie wordt nog steeds uitgevoerd, maar de complexiteit ligt daar niet meer te zien.</span><span class="sxs-lookup"><span data-stu-id="72312-246">The enumeration still happens but we don't see the complexity behind it.</span></span>

### <a name="where-object-filtering"></a><span data-ttu-id="72312-247">Where-Object filteren</span><span class="sxs-lookup"><span data-stu-id="72312-247">Where-Object filtering</span></span>

<span data-ttu-id="72312-248">Hier kan worden `Where-Object` gefilterd en geselecteerd wat we uit de matrix willen zien op basis van de eigenschappen van het object.</span><span class="sxs-lookup"><span data-stu-id="72312-248">This is where `Where-Object` comes in so we can filter and select what we want out of the array based on the properties of the object.</span></span>

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="72312-249">We kunnen dezelfde query schrijven om de `FirstName` Zoek resultaten te vinden.</span><span class="sxs-lookup"><span data-stu-id="72312-249">We can write that same query to get the `FirstName` we are looking for.</span></span>

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a><span data-ttu-id="72312-250">WHERE ()</span><span class="sxs-lookup"><span data-stu-id="72312-250">Where()</span></span>

<span data-ttu-id="72312-251">Matrices hebben een `Where()` methode waarmee u een `scriptblock` voor het filter kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="72312-251">Arrays have a `Where()` method on them that allows you to specify a `scriptblock` for the filter.</span></span>

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

<span data-ttu-id="72312-252">Deze functie is toegevoegd aan Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="72312-252">This feature was added in PowerShell 4.0.</span></span>

### <a name="updating-objects-in-loops"></a><span data-ttu-id="72312-253">Objecten in lussen bijwerken</span><span class="sxs-lookup"><span data-stu-id="72312-253">Updating objects in loops</span></span>

<span data-ttu-id="72312-254">Met waardetypen kan de matrix alleen worden bijgewerkt met behulp van een for-lus, omdat de index moet worden gebruikt om de waarde te vervangen.</span><span class="sxs-lookup"><span data-stu-id="72312-254">With value types, the only way to update the array is to use a for loop because we need to know the index to replace the value.</span></span> <span data-ttu-id="72312-255">We hebben meer opties met objecten omdat ze verwijzen naar typen.</span><span class="sxs-lookup"><span data-stu-id="72312-255">We have more options with objects because they are reference types.</span></span> <span data-ttu-id="72312-256">Hier volgt een kort voor beeld:</span><span class="sxs-lookup"><span data-stu-id="72312-256">Here is a quick example:</span></span>

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

<span data-ttu-id="72312-257">Deze lus doorloopt elk object in de `$data` matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-257">This loop is walking every object in the `$data` array.</span></span> <span data-ttu-id="72312-258">Omdat objecten verwijzen naar typen, `$person` verwijst de variabele naar exact hetzelfde object dat zich in de matrix bevindt.</span><span class="sxs-lookup"><span data-stu-id="72312-258">Because objects are reference types, the `$person` variable references the exact same object that is in the array.</span></span> <span data-ttu-id="72312-259">Als er updates worden uitgevoerd op de eigenschappen, wordt het origineel bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="72312-259">So updates to its properties do update the original.</span></span>

<span data-ttu-id="72312-260">U kunt het hele object niet op deze manier vervangen.</span><span class="sxs-lookup"><span data-stu-id="72312-260">You still can't replace the whole object this way.</span></span> <span data-ttu-id="72312-261">Als u een nieuw object aan de variabele probeert toe te wijzen `$person` , werkt u de verwijzing naar de variabele bij naar iets anders dat niet langer naar het oorspronkelijke object in de matrix verwijst.</span><span class="sxs-lookup"><span data-stu-id="72312-261">If you try to assign a new object to the `$person` variable, you're updating the variable reference to something else that no longer points to the original object in the array.</span></span> <span data-ttu-id="72312-262">Dit werkt niet zoals verwacht:</span><span class="sxs-lookup"><span data-stu-id="72312-262">This doesn't work like you would expect:</span></span>

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a><span data-ttu-id="72312-263">Operators</span><span class="sxs-lookup"><span data-stu-id="72312-263">Operators</span></span>

<span data-ttu-id="72312-264">De Opera tors in Power shell werken ook aan matrices.</span><span class="sxs-lookup"><span data-stu-id="72312-264">The operators in PowerShell also work on arrays.</span></span> <span data-ttu-id="72312-265">Sommige van deze werken iets anders.</span><span class="sxs-lookup"><span data-stu-id="72312-265">Some of them work slightly differently.</span></span>

### <a name="-join"></a><span data-ttu-id="72312-266">-lid worden</span><span class="sxs-lookup"><span data-stu-id="72312-266">-join</span></span>

<span data-ttu-id="72312-267">De `-join` operator is het meest duidelijkst, dus we bekijken deze eerst.</span><span class="sxs-lookup"><span data-stu-id="72312-267">The `-join` operator is the most obvious one so let's look at it first.</span></span> <span data-ttu-id="72312-268">Ik vind de `-join` operator leuk en gebruik deze regel matig.</span><span class="sxs-lookup"><span data-stu-id="72312-268">I like the `-join` operator and use it often.</span></span> <span data-ttu-id="72312-269">Hiermee worden alle elementen in de matrix samengevoegd met het teken of de teken reeks die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="72312-269">It joins all elements in the array with the character or string that you specify.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

<span data-ttu-id="72312-270">Een van de functies die ik op de `-join` operator bevindt, is dat deze afzonderlijke items verwerkt.</span><span class="sxs-lookup"><span data-stu-id="72312-270">One of the features that I like about the `-join` operator is that it handles single items.</span></span>

```powershell
PS> 1 -join '-'
1
```

<span data-ttu-id="72312-271">Ik gebruik dit in logboek registratie en uitgebreide berichten.</span><span class="sxs-lookup"><span data-stu-id="72312-271">I use this inside logging and verbose messages.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a><span data-ttu-id="72312-272">-$array toevoegen</span><span class="sxs-lookup"><span data-stu-id="72312-272">-join $array</span></span>

<span data-ttu-id="72312-273">Hier volgt een slimme truc die Lee Dailey naar mij wijst.</span><span class="sxs-lookup"><span data-stu-id="72312-273">Here is a clever trick that Lee Dailey pointed out to me.</span></span> <span data-ttu-id="72312-274">Als u alles zonder scheidings teken wilt gebruiken, in plaats van dit te doen:</span><span class="sxs-lookup"><span data-stu-id="72312-274">If you ever want to join everything without a delimiter, instead of doing this:</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

<span data-ttu-id="72312-275">U kunt `-join` met de matrix gebruiken als de para meter zonder voor voegsel.</span><span class="sxs-lookup"><span data-stu-id="72312-275">You can use `-join` with the array as the parameter with no prefix.</span></span> <span data-ttu-id="72312-276">Bekijk dit voor beeld om te zien dat ik over het praten ben.</span><span class="sxs-lookup"><span data-stu-id="72312-276">Take a look at this example to see that I'm talking about.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a><span data-ttu-id="72312-277">-vervangen en-splitsen</span><span class="sxs-lookup"><span data-stu-id="72312-277">-replace and -split</span></span>

<span data-ttu-id="72312-278">De andere opera tors zoals `-replace` en worden `-split` uitgevoerd op elk item in de matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-278">The other operators like `-replace` and `-split` execute on each item in the array.</span></span> <span data-ttu-id="72312-279">Ik zeg dat ik ooit deze manier heb gebruikt, maar dit is een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="72312-279">I can't say that I have ever used them this way but here is an example.</span></span>

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a><span data-ttu-id="72312-280">-contains</span><span class="sxs-lookup"><span data-stu-id="72312-280">-contains</span></span>

<span data-ttu-id="72312-281">Met de `-contains` operator kunt u een matrix met waarden controleren om te zien of deze een opgegeven waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="72312-281">The `-contains` operator allows you to check an array of values to see if it contains a specified value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a><span data-ttu-id="72312-282">-in</span><span class="sxs-lookup"><span data-stu-id="72312-282">-in</span></span>

<span data-ttu-id="72312-283">Wanneer u één waarde hebt die u wilt verifiëren, kunt u een van de volgende waarden gebruiken `-in` .</span><span class="sxs-lookup"><span data-stu-id="72312-283">When you have a single value that you would like to verify matches one of several values, you can use the `-in` operator.</span></span> <span data-ttu-id="72312-284">De waarde is links en de matrix aan de rechter kant van de operator.</span><span class="sxs-lookup"><span data-stu-id="72312-284">The value would be on the left and the array on the right-hand side of the operator.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

<span data-ttu-id="72312-285">Dit kan duur krijgen als de lijst groot is.</span><span class="sxs-lookup"><span data-stu-id="72312-285">This can get expensive if the list is large.</span></span> <span data-ttu-id="72312-286">Ik gebruik vaak een regex-patroon als ik meer dan een paar waarden Controleer.</span><span class="sxs-lookup"><span data-stu-id="72312-286">I often use a regex pattern if I'm checking more than a few values.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a><span data-ttu-id="72312-287">-EQ en-ne</span><span class="sxs-lookup"><span data-stu-id="72312-287">-eq and -ne</span></span>

<span data-ttu-id="72312-288">Gelijkheid en matrices kunnen gecompliceerd zijn.</span><span class="sxs-lookup"><span data-stu-id="72312-288">Equality and arrays can get complicated.</span></span> <span data-ttu-id="72312-289">Wanneer de matrix aan de linkerkant wordt geplaatst, wordt elk item vergeleken.</span><span class="sxs-lookup"><span data-stu-id="72312-289">When the array is on the left side, every item gets compared.</span></span> <span data-ttu-id="72312-290">In plaats van `True` te retour neren, wordt het object geretourneerd dat overeenkomt.</span><span class="sxs-lookup"><span data-stu-id="72312-290">Instead of returning `True`, it returns the object that matches.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

<span data-ttu-id="72312-291">Wanneer u de `-ne` operator gebruikt, worden alle waarden opgehaald die niet gelijk zijn aan onze waarde.</span><span class="sxs-lookup"><span data-stu-id="72312-291">When you use the `-ne` operator, we get all the values that are not equal to our value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

<span data-ttu-id="72312-292">Wanneer u dit gebruikt in een `if()` -instructie, is een waarde die wordt geretourneerd een `True` waarde.</span><span class="sxs-lookup"><span data-stu-id="72312-292">When you use this in an `if()` statement, a value that is returned is a `True` value.</span></span> <span data-ttu-id="72312-293">Als er geen waarde wordt geretourneerd, is dit een `False` waarde.</span><span class="sxs-lookup"><span data-stu-id="72312-293">If no value is returned, then it's a `False` value.</span></span> <span data-ttu-id="72312-294">Beide volgende instructies evalueren naar `True` .</span><span class="sxs-lookup"><span data-stu-id="72312-294">Both of these next statements evaluate to `True`.</span></span>

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

<span data-ttu-id="72312-295">Ik ga dit op een moment opnieuw door met het bespreken van testen `$null` .</span><span class="sxs-lookup"><span data-stu-id="72312-295">I'll revisit this in a moment when we talk about testing for `$null`.</span></span>

### <a name="-match"></a><span data-ttu-id="72312-296">-match</span><span class="sxs-lookup"><span data-stu-id="72312-296">-match</span></span>

<span data-ttu-id="72312-297">De `-match` operator probeert elk item in de verzameling te koppelen.</span><span class="sxs-lookup"><span data-stu-id="72312-297">The `-match` operator tries to match each item in the collection.</span></span>

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

<span data-ttu-id="72312-298">Wanneer u `-match` met één waarde gebruikt, wordt een speciale variabele `$Matches` gevuld met overeenkomende gegevens.</span><span class="sxs-lookup"><span data-stu-id="72312-298">When you use `-match` with a single value, a special variable `$Matches` gets populated with match info.</span></span> <span data-ttu-id="72312-299">Dit is niet het geval wanneer een matrix op deze manier wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="72312-299">This isn't the case when an array is processed this way.</span></span>

<span data-ttu-id="72312-300">We kunnen dezelfde benadering uitvoeren met `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="72312-300">We can take the same approach with `Select-String`.</span></span>

```powershell
$servers | Select-String SQL
```

<span data-ttu-id="72312-301">Ik kijk eens naar `Select-String` `-match` en de `$matches` variabele in een ander bericht heet [de vele manieren om regex te gebruiken][].</span><span class="sxs-lookup"><span data-stu-id="72312-301">I take a closer look at `Select-String`,`-match` and the `$matches` variable in another post called [The many ways to use regex][].</span></span>

### <a name="null-or-empty"></a><span data-ttu-id="72312-302">$null of leeg</span><span class="sxs-lookup"><span data-stu-id="72312-302">$null or empty</span></span>

<span data-ttu-id="72312-303">Testen van `$null` of lege matrices kunnen lastig zijn.</span><span class="sxs-lookup"><span data-stu-id="72312-303">Testing for `$null` or empty arrays can be tricky.</span></span> <span data-ttu-id="72312-304">Dit zijn de algemene traps met matrices.</span><span class="sxs-lookup"><span data-stu-id="72312-304">Here are the common traps with arrays.</span></span>

<span data-ttu-id="72312-305">In een oogopslag lijkt het alsof deze instructie werkt.</span><span class="sxs-lookup"><span data-stu-id="72312-305">At a glance, this statement looks like it should work.</span></span>

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

<span data-ttu-id="72312-306">Maar ik heb zojuist overgegaan hoe `-eq` elk item in de matrix wordt gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="72312-306">But I just went over how `-eq` checks each item in the array.</span></span> <span data-ttu-id="72312-307">We kunnen dus een matrix van verschillende items hebben met één $null waarde en deze evalueren `$true`</span><span class="sxs-lookup"><span data-stu-id="72312-307">So we can have an array of several items with a single $null value and it would evaluate to `$true`</span></span>

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

<span data-ttu-id="72312-308">Daarom is het een best practice om de `$null` aan de linkerkant van de operator te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="72312-308">This is why it's a best practice to place the `$null` on the left side of the operator.</span></span> <span data-ttu-id="72312-309">Dit scenario maakt dan een niet-probleem.</span><span class="sxs-lookup"><span data-stu-id="72312-309">This makes this scenario a non-issue.</span></span>

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

<span data-ttu-id="72312-310">Een `$null` matrix is niet hetzelfde als een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-310">A `$null` array isn't the same thing as an empty array.</span></span> <span data-ttu-id="72312-311">Als u weet dat u een matrix hebt, controleert u het aantal objecten hierin.</span><span class="sxs-lookup"><span data-stu-id="72312-311">If you know you have an array, check the count of objects in it.</span></span> <span data-ttu-id="72312-312">Als de matrix is `$null` , is het aantal `0` .</span><span class="sxs-lookup"><span data-stu-id="72312-312">If the array is `$null`, the count is `0`.</span></span>

```powershell
if ( $array.count -gt 0 )
{
    "Array isn't empty"
}
```

<span data-ttu-id="72312-313">Er is nog een trap die u hier kunt bekijken.</span><span class="sxs-lookup"><span data-stu-id="72312-313">There is one more trap to watch out for here.</span></span> <span data-ttu-id="72312-314">U kunt ook gebruiken `count` Als u één object hebt, tenzij dat object een is `PSCustomObject` .</span><span class="sxs-lookup"><span data-stu-id="72312-314">You can use the `count` even if you have a single object, unless that object is a `PSCustomObject`.</span></span> <span data-ttu-id="72312-315">Dit is een fout die wordt opgelost in Power shell 6,1.</span><span class="sxs-lookup"><span data-stu-id="72312-315">This is a bug that is fixed in PowerShell 6.1.</span></span>
<span data-ttu-id="72312-316">Dat is goed nieuws, maar een groot aantal mensen bevindt zich nog steeds op 5,1 en moet erop letten.</span><span class="sxs-lookup"><span data-stu-id="72312-316">That's good news, but a lot of people are still on 5.1 and need to watch out for it.</span></span>

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

<span data-ttu-id="72312-317">Als u nog steeds in Power shell 5,1 bent, kunt u het object in een matrix inpakken voordat u het aantal controleert om een nauw keurig aantal te bepalen.</span><span class="sxs-lookup"><span data-stu-id="72312-317">If you're still on PowerShell 5.1, you can wrap the object in an array before checking the count to get an accurate count.</span></span>

```powershell
if ( @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

<span data-ttu-id="72312-318">Als u het veilig wilt afspelen, controleert u op `$null` en controleert u de telling.</span><span class="sxs-lookup"><span data-stu-id="72312-318">To fully play it safe, check for `$null`, then check the count.</span></span>

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    "Array isn't empty"
}
```

### <a name="all--eq"></a><span data-ttu-id="72312-319">All-EQ</span><span class="sxs-lookup"><span data-stu-id="72312-319">All -eq</span></span>

<span data-ttu-id="72312-320">Ik zag onlangs dat iemand [een vraag stelt om te controleren of elke waarde in een matrix overeenkomt met een bepaalde waarde][].</span><span class="sxs-lookup"><span data-stu-id="72312-320">I recently saw someone ask [how to verify that every value in an array matches a given value][].</span></span>
<span data-ttu-id="72312-321">Reddit User **/u/bis** had deze slimme [oplossing][] die op onjuiste waarden controleert en vervolgens het resultaat spiegelt.</span><span class="sxs-lookup"><span data-stu-id="72312-321">Reddit user **/u/bis** had this clever [solution][] that checks for any incorrect values and then flips the result.</span></span>

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a><span data-ttu-id="72312-322">Toevoegen aan matrices</span><span class="sxs-lookup"><span data-stu-id="72312-322">Adding to arrays</span></span>

<span data-ttu-id="72312-323">Op dit moment begint u met het toevoegen van items aan een matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-323">At this point, you're starting to wonder how to add items to an array.</span></span> <span data-ttu-id="72312-324">Het snelle antwoord is dat u dat niet kunt.</span><span class="sxs-lookup"><span data-stu-id="72312-324">The quick answer is that you can't.</span></span> <span data-ttu-id="72312-325">Een matrix is een vaste grootte in het geheugen.</span><span class="sxs-lookup"><span data-stu-id="72312-325">An array is a fixed size in memory.</span></span> <span data-ttu-id="72312-326">Als u het item wilt verg Roten of er één aan wilt toevoegen, moet u een nieuwe matrix maken en alle waarden van de oude matrix kopiëren.</span><span class="sxs-lookup"><span data-stu-id="72312-326">If you need to grow it or add a single item to it, then you need to create a new array and copy all the values over from the old array.</span></span> <span data-ttu-id="72312-327">Dit klinkt als veel werk, maar in Power shell wordt de complexiteit van het maken van de nieuwe matrix echter verborgen.</span><span class="sxs-lookup"><span data-stu-id="72312-327">This sounds like a lot of work, however, PowerShell hides the complexity of creating the new array.</span></span> <span data-ttu-id="72312-328">Power shell implementeert de operator voor optellen ( `+` ) voor matrices.</span><span class="sxs-lookup"><span data-stu-id="72312-328">PowerShell implements the addition operator (`+`) for arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="72312-329">Power shell implementeert geen aftrekkings bewerking.</span><span class="sxs-lookup"><span data-stu-id="72312-329">PowerShell does not implement a subtraction operation.</span></span> <span data-ttu-id="72312-330">Als u een flexibel alternatief voor een matrix wilt, moet u een [Gene riek `List` ](#generic-list) object gebruiken.</span><span class="sxs-lookup"><span data-stu-id="72312-330">If you want a flexible alternative to an array, you need to use a [generic `List`](#generic-list) object.</span></span>

### <a name="array-addition"></a><span data-ttu-id="72312-331">Matrix toevoegen</span><span class="sxs-lookup"><span data-stu-id="72312-331">Array addition</span></span>

<span data-ttu-id="72312-332">We kunnen de operator voor toevoeging met matrices gebruiken om een nieuwe matrix te maken.</span><span class="sxs-lookup"><span data-stu-id="72312-332">We can use the addition operator with arrays to create a new array.</span></span> <span data-ttu-id="72312-333">Deze twee matrices hebben daarom de volgende:</span><span class="sxs-lookup"><span data-stu-id="72312-333">So given these two arrays:</span></span>

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

<span data-ttu-id="72312-334">We kunnen ze samen toevoegen om een nieuwe matrix te krijgen.</span><span class="sxs-lookup"><span data-stu-id="72312-334">We can add them together to get a new array.</span></span>

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a><span data-ttu-id="72312-335">Plus teken is gelijk aan + =</span><span class="sxs-lookup"><span data-stu-id="72312-335">Plus equals +=</span></span>

<span data-ttu-id="72312-336">We kunnen een nieuwe matrix maken en daar een item aan toevoegen:</span><span class="sxs-lookup"><span data-stu-id="72312-336">We can create a new array in place and add an item to it like this:</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

<span data-ttu-id="72312-337">Houd er rekening mee dat elke keer `+=` dat u het dupliceert en een nieuwe matrix maakt.</span><span class="sxs-lookup"><span data-stu-id="72312-337">Just remember that every time you use `+=` that you're duplicating and creating a new array.</span></span> <span data-ttu-id="72312-338">Dit is geen probleem voor kleine gegevens sets, maar het wordt zeer slecht geschaald.</span><span class="sxs-lookup"><span data-stu-id="72312-338">This is a not an issue for small datasets but it scales extremely poorly.</span></span>

### <a name="pipeline-assignment"></a><span data-ttu-id="72312-339">Pijplijn toewijzing</span><span class="sxs-lookup"><span data-stu-id="72312-339">Pipeline assignment</span></span>

<span data-ttu-id="72312-340">U kunt de resultaten van een pijp lijn toewijzen aan een variabele.</span><span class="sxs-lookup"><span data-stu-id="72312-340">You can assign the results of any pipeline into a variable.</span></span> <span data-ttu-id="72312-341">Het is een matrix als deze meerdere items bevat.</span><span class="sxs-lookup"><span data-stu-id="72312-341">It's an array if it contains multiple items.</span></span>

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

<span data-ttu-id="72312-342">Normaal gesp roken is het gebruik van de pijp lijn van de typische Power shell-One-Lines.</span><span class="sxs-lookup"><span data-stu-id="72312-342">Normally when we think of using the pipeline, we think of the typical PowerShell one-liners.</span></span> <span data-ttu-id="72312-343">We kunnen gebruikmaken van de pijp lijn met `foreach()` instructies en andere lussen.</span><span class="sxs-lookup"><span data-stu-id="72312-343">We can leverage the pipeline with `foreach()` statements and other loops.</span></span> <span data-ttu-id="72312-344">In plaats van items aan een matrix toe te voegen, kunnen we items naar de pijp lijn verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="72312-344">So instead of adding items to an array in a loop, we can drop items onto the pipeline.</span></span>

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a><span data-ttu-id="72312-345">Matrix typen</span><span class="sxs-lookup"><span data-stu-id="72312-345">Array Types</span></span>

<span data-ttu-id="72312-346">Standaard wordt een matrix in Power shell gemaakt als een `[PSObject[]]` type.</span><span class="sxs-lookup"><span data-stu-id="72312-346">By default, an array in PowerShell is created as a `[PSObject[]]` type.</span></span> <span data-ttu-id="72312-347">Dit kan een wille keurig type object of waarde bevatten.</span><span class="sxs-lookup"><span data-stu-id="72312-347">This allows it to contain any type of object or value.</span></span> <span data-ttu-id="72312-348">Dit werkt omdat alles wordt overgenomen van het `PSObject` type.</span><span class="sxs-lookup"><span data-stu-id="72312-348">This works because everything is inherited from the `PSObject` type.</span></span>

### <a name="strongly-typed-arrays"></a><span data-ttu-id="72312-349">Sterk getypeerde matrices</span><span class="sxs-lookup"><span data-stu-id="72312-349">Strongly typed arrays</span></span>

<span data-ttu-id="72312-350">U kunt een matrix van elk type maken met een vergelijk bare syntaxis.</span><span class="sxs-lookup"><span data-stu-id="72312-350">You can create an array of any type using a similar syntax.</span></span> <span data-ttu-id="72312-351">Wanneer u een sterk getypeerde matrix maakt, kan deze alleen waarden of objecten van het opgegeven type bevatten.</span><span class="sxs-lookup"><span data-stu-id="72312-351">When you create a strongly typed array, it can only contain values or objects the specified type.</span></span>

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a><span data-ttu-id="72312-352">List</span><span class="sxs-lookup"><span data-stu-id="72312-352">ArrayList</span></span>

<span data-ttu-id="72312-353">Het toevoegen van items aan een matrix is een van de grootste beperkingen, maar er zijn een aantal andere verzamelingen die we kunnen omzetten om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="72312-353">Adding items to an array is one of its biggest limitations, but there are a few other collections that we can turn to that solve this problem.</span></span>

<span data-ttu-id="72312-354">De `ArrayList` is doorgaans een van de eerste dingen die we denken wanneer we een matrix nodig hebben die sneller werkt met.</span><span class="sxs-lookup"><span data-stu-id="72312-354">The `ArrayList` is commonly one of the first things that we think of when we need an array that is faster to work with.</span></span> <span data-ttu-id="72312-355">Het fungeert als een object matrix op elke locatie waar we deze nodig hebben, maar Hiermee wordt het snel toevoegen van items.</span><span class="sxs-lookup"><span data-stu-id="72312-355">It acts like an object array every place that we need it, but it handles adding items quickly.</span></span>

<span data-ttu-id="72312-356">Hier wordt uitgelegd hoe we een `ArrayList` items maken en hieraan toevoegen.</span><span class="sxs-lookup"><span data-stu-id="72312-356">Here is how we create an `ArrayList` and add items to it.</span></span>

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

<span data-ttu-id="72312-357">Er wordt naar .NET gebeld om dit type op te halen.</span><span class="sxs-lookup"><span data-stu-id="72312-357">We are calling into .NET to get this type.</span></span> <span data-ttu-id="72312-358">In dit geval gebruiken we de standaard-constructor om deze te maken.</span><span class="sxs-lookup"><span data-stu-id="72312-358">In this case, we are using the default constructor to create it.</span></span> <span data-ttu-id="72312-359">Vervolgens roept de `Add` methode aan om een item toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="72312-359">Then we call the `Add` method to add an item to it.</span></span>

<span data-ttu-id="72312-360">De reden `[void]` dat ik aan het begin van de regel bevindt, is om de retour code te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="72312-360">The reason I'm using `[void]` at the beginning of the line is to suppress the return code.</span></span> <span data-ttu-id="72312-361">In sommige .NET-aanroepen wordt dit gedaan en kan onverwachte uitvoer worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="72312-361">Some .NET calls do this and can create unexpected output.</span></span>

<span data-ttu-id="72312-362">Als de enige gegevens die u in uw matrix hebt, teken reeksen zijn, bekijkt u ook de gebruik van [String Builder][].</span><span class="sxs-lookup"><span data-stu-id="72312-362">If the only data that you have in your array is strings, then also take a look at using [StringBuilder][].</span></span> <span data-ttu-id="72312-363">Het is bijna hetzelfde, maar heeft een aantal methoden die alleen worden behandeld met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="72312-363">It's almost the same thing but has some methods that are just for dealing with strings.</span></span> <span data-ttu-id="72312-364">De `StringBuilder` is speciaal ontworpen voor prestaties.</span><span class="sxs-lookup"><span data-stu-id="72312-364">The `StringBuilder` is specially designed for performance.</span></span>

<span data-ttu-id="72312-365">Het is gebruikelijk om te zien hoe mensen `ArrayList` van matrices worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="72312-365">It's common to see people move to `ArrayList` from arrays.</span></span> <span data-ttu-id="72312-366">Maar het is afkomstig van een keer dat C# geen algemene ondersteuning heeft.</span><span class="sxs-lookup"><span data-stu-id="72312-366">But it comes from a time where C# didn't have generic support.</span></span> <span data-ttu-id="72312-367">De `ArrayList` is afgeschaft in ondersteuning voor de algemene `List[]`</span><span class="sxs-lookup"><span data-stu-id="72312-367">The `ArrayList` is deprecated in support for the generic `List[]`</span></span>

### <a name="generic-list"></a><span data-ttu-id="72312-368">Algemene lijst</span><span class="sxs-lookup"><span data-stu-id="72312-368">Generic List</span></span>

<span data-ttu-id="72312-369">Een Gene riek type is een speciaal type in C# dat een gegeneraliseerde klasse definieert en de gebruiker specificeert de gegevens typen die worden gebruikt wanneer ze worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="72312-369">A generic type is a special type in C# that defines a generalized class and the user specifies the data types it uses when created.</span></span> <span data-ttu-id="72312-370">Als u dus een lijst met getallen of teken reeksen wilt, definieert u dat u een lijst `int` of `string` typen wilt.</span><span class="sxs-lookup"><span data-stu-id="72312-370">So if you want a list of numbers or strings, you would define that you want list of `int` or `string` types.</span></span>

<span data-ttu-id="72312-371">Hier kunt u een lijst maken voor teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="72312-371">Here is how you create a List for strings.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

<span data-ttu-id="72312-372">Of een lijst met getallen.</span><span class="sxs-lookup"><span data-stu-id="72312-372">Or a list for numbers.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

<span data-ttu-id="72312-373">We kunnen een bestaande matrix Converteren naar een lijst zoals deze zonder eerst het object te maken:</span><span class="sxs-lookup"><span data-stu-id="72312-373">We can cast an existing array to a list like this without creating the object first:</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

<span data-ttu-id="72312-374">We kunnen de syntaxis verkorten met de `using namespace` instructie in Power shell 5 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="72312-374">We can shorten the syntax with the `using namespace` statement in PowerShell 5 and newer.</span></span> <span data-ttu-id="72312-375">De `using` instructie moet de eerste regel van het script zijn.</span><span class="sxs-lookup"><span data-stu-id="72312-375">The `using` statement needs to be the first line of your script.</span></span> <span data-ttu-id="72312-376">Als u een naam ruimte declareert, kunt u met Power shell de gegevens typen uitschakelen wanneer u ernaar verwijst.</span><span class="sxs-lookup"><span data-stu-id="72312-376">By declaring a namespace, PowerShell lets you leave it off of the data types when you reference them.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

<span data-ttu-id="72312-377">Dit maakt het `List` veel handiger.</span><span class="sxs-lookup"><span data-stu-id="72312-377">This makes the `List` much more usable.</span></span>

<span data-ttu-id="72312-378">U hebt een vergelijk bare `Add` methode voor u.</span><span class="sxs-lookup"><span data-stu-id="72312-378">You have a similar `Add` method available to you.</span></span> <span data-ttu-id="72312-379">In tegens telling tot de array List is er geen retour waarde voor de `Add` methode `void` .</span><span class="sxs-lookup"><span data-stu-id="72312-379">Unlike the ArrayList, there is no return value on the `Add` method so we don't have to `void` it.</span></span>

```powershell
$myList.Add(10)
```

<span data-ttu-id="72312-380">En we hebben nog steeds toegang tot de elementen zoals andere matrices.</span><span class="sxs-lookup"><span data-stu-id="72312-380">And we can still access the elements like other arrays.</span></span>

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a><span data-ttu-id="72312-381">Lijst [PSObject]</span><span class="sxs-lookup"><span data-stu-id="72312-381">List[PSObject]</span></span>

<span data-ttu-id="72312-382">U kunt een lijst van elk type hebben, maar wanneer u het type objecten niet weet, kunt u deze gebruiken `[List[PSObject]]` om ze te bevatten.</span><span class="sxs-lookup"><span data-stu-id="72312-382">You can have a list of any type, but when you don't know the type of objects, you can use `[List[PSObject]]` to contain them.</span></span>

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a><span data-ttu-id="72312-383">Remove()</span><span class="sxs-lookup"><span data-stu-id="72312-383">Remove()</span></span>

<span data-ttu-id="72312-384">De `ArrayList` en de algemene `List[]` ondersteuning voor het verwijderen van items uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="72312-384">The `ArrayList` and the generic `List[]` both support removing items from the collection.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

<span data-ttu-id="72312-385">Bij het werken met waardetypen wordt het eerste item uit de lijst verwijderd.</span><span class="sxs-lookup"><span data-stu-id="72312-385">When working with value types, it removes the first one from the list.</span></span> <span data-ttu-id="72312-386">U kunt deze opnieuw aanroepen om deze waarde te blijven verwijderen.</span><span class="sxs-lookup"><span data-stu-id="72312-386">You can call it over and over again to keep removing that value.</span></span> <span data-ttu-id="72312-387">Als u referentie typen hebt, moet u het object opgeven dat u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="72312-387">If you have reference types, you have to provide the object that you want removed.</span></span>

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

<span data-ttu-id="72312-388">De methode Remove wordt geretourneerd `true` als het item in de verzameling kan worden gevonden en verwijderd.</span><span class="sxs-lookup"><span data-stu-id="72312-388">The remove method returns `true` if it was able to find and remove the item from the collection.</span></span>

### <a name="more-collections"></a><span data-ttu-id="72312-389">Meer verzamelingen</span><span class="sxs-lookup"><span data-stu-id="72312-389">More collections</span></span>

<span data-ttu-id="72312-390">Er zijn veel andere verzamelingen die kunnen worden gebruikt, maar dit zijn de goede algemene matrix vervangingen.</span><span class="sxs-lookup"><span data-stu-id="72312-390">There are many other collections that can be used but these are the good generic array replacements.</span></span>
<span data-ttu-id="72312-391">Als u meer wilt weten [over deze opties](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) , gaat u naar deze lessen die [Kraus markeren](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) .</span><span class="sxs-lookup"><span data-stu-id="72312-391">If you're interested in learning about more of these options, take a look at this [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) that [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) put together.</span></span>

## <a name="other-nuances"></a><span data-ttu-id="72312-392">Andere nuances</span><span class="sxs-lookup"><span data-stu-id="72312-392">Other nuances</span></span>

<span data-ttu-id="72312-393">Nu u alle belang rijke functies hebt behandeld, zijn er nog enkele dingen die ik wilde vermelden voordat ik dit inpakt.</span><span class="sxs-lookup"><span data-stu-id="72312-393">Now that I have covered all the major functionality, here are a few more things that I wanted to mention before I wrap this up.</span></span>

### <a name="pre-sized-arrays"></a><span data-ttu-id="72312-394">Pregrote matrices</span><span class="sxs-lookup"><span data-stu-id="72312-394">Pre-sized arrays</span></span>

<span data-ttu-id="72312-395">Ik heb genoteerd dat u de grootte van een matrix niet kunt wijzigen nadat deze is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="72312-395">I mentioned that you can't change the size of an array once it's created.</span></span> <span data-ttu-id="72312-396">We kunnen een matrix maken van een vooraf bepaalde grootte door deze aan te roepen met de `new($size)` constructor.</span><span class="sxs-lookup"><span data-stu-id="72312-396">We can create an array of a pre-determined size by calling it with the `new($size)` constructor.</span></span>

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a><span data-ttu-id="72312-397">Matrices vermenigvuldigen</span><span class="sxs-lookup"><span data-stu-id="72312-397">Multiplying arrays</span></span>

<span data-ttu-id="72312-398">Een interessante truc is dat u een matrix kunt vermenigvuldigen met een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="72312-398">An interesting little trick is that you can multiply an array by an integer.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a><span data-ttu-id="72312-399">Initialiseren met 0</span><span class="sxs-lookup"><span data-stu-id="72312-399">Initialize with 0</span></span>

<span data-ttu-id="72312-400">Een veelvoorkomend scenario is dat u een matrix met alle nullen wilt maken.</span><span class="sxs-lookup"><span data-stu-id="72312-400">A common scenario is that you want to create an array with all zeros.</span></span> <span data-ttu-id="72312-401">Als u alleen gehele getallen wilt hebben, wordt een sterk getypeerde matrix van gehele getallen standaard ingesteld op nullen.</span><span class="sxs-lookup"><span data-stu-id="72312-401">If you're only going to have integers, a strongly typed array of integers defaults to all zeros.</span></span>

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

<span data-ttu-id="72312-402">We kunnen de verwerkings truc ook gebruiken om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="72312-402">We can use the multiplying trick to do this too.</span></span>

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

<span data-ttu-id="72312-403">Het mooie van de vermenigvuldigings truc is dat u een wille keurige waarde kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="72312-403">The nice thing about the multiplying trick is that you can use any value.</span></span> <span data-ttu-id="72312-404">Als u `255` de standaard waarde liever hebt, is dit een goede manier om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="72312-404">So if you would rather have `255` as your default value, this would be a good way to do it.</span></span>

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a><span data-ttu-id="72312-405">Geneste matrices</span><span class="sxs-lookup"><span data-stu-id="72312-405">Nested arrays</span></span>

<span data-ttu-id="72312-406">Een matrix binnen een matrix wordt een geneste matrix genoemd.</span><span class="sxs-lookup"><span data-stu-id="72312-406">An array inside an array is called a nested array.</span></span> <span data-ttu-id="72312-407">Ik gebruik deze niet veel in Power shell, maar ik heb ze meer in andere talen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="72312-407">I don't use these much in PowerShell but I have used them more in other languages.</span></span> <span data-ttu-id="72312-408">U kunt een matrix met matrices gebruiken als uw gegevens in een raster overeenkomen met het patroon.</span><span class="sxs-lookup"><span data-stu-id="72312-408">Consider using an array of arrays when your data fits in a grid like pattern.</span></span>

<span data-ttu-id="72312-409">Hier volgen twee manieren waarop we een tweedimensionale matrix kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="72312-409">Here are two ways we can create a two-dimensional array.</span></span>

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

<span data-ttu-id="72312-410">De komma is zeer belang rijk in die voor beelden.</span><span class="sxs-lookup"><span data-stu-id="72312-410">The comma is very important in those examples.</span></span> <span data-ttu-id="72312-411">Ik heb een eerder voor beeld van een normale matrix op meerdere regels genoteerd, waar de komma optioneel was.</span><span class="sxs-lookup"><span data-stu-id="72312-411">I gave an earlier example of a normal array on multiple lines where the comma was optional.</span></span> <span data-ttu-id="72312-412">Dat is niet het geval met een multi-dimensionale matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-412">That isn't the case with a multi-dimensional array.</span></span>

<span data-ttu-id="72312-413">De manier waarop we de index notatie gebruiken, verandert nu iets dat we een geneste matrix hebben.</span><span class="sxs-lookup"><span data-stu-id="72312-413">The way we use the index notation changes slightly now that we've a nested array.</span></span> <span data-ttu-id="72312-414">Op basis van het `$data` bovenstaande is dit hoe we de waarde 3 benaderen.</span><span class="sxs-lookup"><span data-stu-id="72312-414">Using the `$data` above, this is how we would access the value 3.</span></span>

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

<span data-ttu-id="72312-415">Voeg een set met haakjes toe voor elk niveau van matrix Nesting.</span><span class="sxs-lookup"><span data-stu-id="72312-415">Add a set of bracket for each level of array nesting.</span></span> <span data-ttu-id="72312-416">De eerste set met haken is voor de buitenste matrix en vervolgens werkt u vanuit deze werk wijze.</span><span class="sxs-lookup"><span data-stu-id="72312-416">The first set of brackets is for the outer most array and then you work your way in from there.</span></span>

### <a name="write-output--noenumerate"></a><span data-ttu-id="72312-417">Write-Output-opsomming</span><span class="sxs-lookup"><span data-stu-id="72312-417">Write-Output -NoEnumerate</span></span>

<span data-ttu-id="72312-418">Power shell kan de terugloop of het opsommen van matrices opvangen.</span><span class="sxs-lookup"><span data-stu-id="72312-418">PowerShell likes to unwrap or enumerate arrays.</span></span> <span data-ttu-id="72312-419">Dit is een kern aspect van de manier waarop Power shell de pijp lijn gebruikt, maar er zijn tijden die u niet wilt dat.</span><span class="sxs-lookup"><span data-stu-id="72312-419">This is a core aspect of the way PowerShell uses the pipeline but there are times that you don't want that to happen.</span></span>

<span data-ttu-id="72312-420">Ik pipet objecten vaak om `Get-Member` meer te weten te komen over hen.</span><span class="sxs-lookup"><span data-stu-id="72312-420">I commonly pipe objects to `Get-Member` to learn more about them.</span></span> <span data-ttu-id="72312-421">Wanneer ik een matrix naar het object Pipet, wordt deze teruggeleid en Get-Member ziet de leden van de matrix en niet de daad werkelijke matrix.</span><span class="sxs-lookup"><span data-stu-id="72312-421">When I pipe an array to it, it gets unwrapped and Get-Member sees the members of the array and not the actual array.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

<span data-ttu-id="72312-422">U kunt gebruiken om te voor komen dat de matrix op te slaan `Write-Object -NoEnumerate` .</span><span class="sxs-lookup"><span data-stu-id="72312-422">To prevent that unwrap of the array, you can use `Write-Object -NoEnumerate`.</span></span>

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

<span data-ttu-id="72312-423">Ik heb een tweede manier om meer van een hack (en probeer Hacks zoals dit te voor komen).</span><span class="sxs-lookup"><span data-stu-id="72312-423">I have a second way that's more of a hack (and I try to avoid hacks like this).</span></span> <span data-ttu-id="72312-424">U kunt een komma vóór de matrix plaatsen voordat u deze pipet.</span><span class="sxs-lookup"><span data-stu-id="72312-424">You can place a comma in front of the array before you pipe it.</span></span>

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a><span data-ttu-id="72312-425">Een matrix retour neren</span><span class="sxs-lookup"><span data-stu-id="72312-425">Return an array</span></span>

<span data-ttu-id="72312-426">Dit ontpakken van matrices gebeurt ook wanneer u waarden uit een functie uitvoert of retourneert.</span><span class="sxs-lookup"><span data-stu-id="72312-426">This unwrapping of arrays also happens when you output or return values from a function.</span></span> <span data-ttu-id="72312-427">U kunt nog steeds een matrix ophalen als u de uitvoer toewijst aan een variabele, zodat dit niet vaak een probleem is.</span><span class="sxs-lookup"><span data-stu-id="72312-427">You can still get an array if you assign the output to a variable so this isn't commonly an issue.</span></span>

<span data-ttu-id="72312-428">De catch is dat u een nieuwe matrix hebt.</span><span class="sxs-lookup"><span data-stu-id="72312-428">The catch is that you have a new array.</span></span> <span data-ttu-id="72312-429">Als het probleem zich ooit voordoet, kunt u `Write-Output -NoEnumerate $array` het gebruiken of omzeilen `return ,$array` .</span><span class="sxs-lookup"><span data-stu-id="72312-429">If that is ever a problem, you can use `Write-Output -NoEnumerate $array` or `return ,$array` to work around it.</span></span>

## <a name="anything-else"></a><span data-ttu-id="72312-430">Nog iets?</span><span class="sxs-lookup"><span data-stu-id="72312-430">Anything else?</span></span>

<span data-ttu-id="72312-431">Ik weet dat dit allemaal veel tijd in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="72312-431">I know this is all a lot to take in.</span></span> <span data-ttu-id="72312-432">We hopen dat u een deel van dit artikel leert elke keer dat u het leest en dat het gedurende lange tijd een goede referentie voor u is.</span><span class="sxs-lookup"><span data-stu-id="72312-432">My hope is that you learn something from this article every time you read it and that it turns out to be a good reference for you for a long time to come.</span></span> <span data-ttu-id="72312-433">Als u ontdekt dat dit nuttig is, kunt u het delen met anderen waarvan u denkt dat ze de waarde van de app kunnen halen.</span><span class="sxs-lookup"><span data-stu-id="72312-433">If you found this to be helpful, please share it with others you think may get value out of it.</span></span>

<span data-ttu-id="72312-434">Hier raden we u aan een vergelijk bare post te bekijken die ik heb geschreven over [hashtabellen][].</span><span class="sxs-lookup"><span data-stu-id="72312-434">From here, I would recommend you check out a similar post that I wrote about [hashtables][].</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Matrices]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch-instructie]: everything-about-switch.md
[switch statement]: everything-about-switch.md
[hashtabellen]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
[De vele manieren om regex te gebruiken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[controleren of elke waarde in een matrix overeenkomt met een bepaalde waarde]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[how to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[oplossen]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[String]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
