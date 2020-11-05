---
title: Alles wat u moet weten over de instructie switch
description: De instructie switch in Power shell biedt functies die niet in andere talen zijn gevonden.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: c2e77aa5fb36d04fec1bc86f751291205120c729
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355116"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a><span data-ttu-id="ceaca-103">Alles wat u moet weten over de instructie switch</span><span class="sxs-lookup"><span data-stu-id="ceaca-103">Everything you ever wanted to know about the switch statement</span></span>

<span data-ttu-id="ceaca-104">Net als bij veel andere talen heeft Power shell opdrachten voor het beheren van de stroom van uitvoering binnen uw scripts.</span><span class="sxs-lookup"><span data-stu-id="ceaca-104">Like many other languages, PowerShell has commands for controlling the flow of execution within your scripts.</span></span> <span data-ttu-id="ceaca-105">Een van deze instructies is de instructie [Switch][] en in Power shell en biedt functies die niet in andere talen worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="ceaca-105">One of those statements is the [switch][] statement and in PowerShell, it offers features that aren't found in other languages.</span></span> <span data-ttu-id="ceaca-106">Vandaag gaan we een grondige kennis van het werken met de Power shell `switch` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-106">Today, we take a deep dive into working with the PowerShell `switch`.</span></span>

> [!NOTE]
> <span data-ttu-id="ceaca-107">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="ceaca-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="ceaca-108">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="ceaca-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="ceaca-109">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="ceaca-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="ceaca-110">De `if` instructie</span><span class="sxs-lookup"><span data-stu-id="ceaca-110">The `if` statement</span></span>

<span data-ttu-id="ceaca-111">Een van de eerste instructies die u leert, is de `if` instructie.</span><span class="sxs-lookup"><span data-stu-id="ceaca-111">One of the first statements that you learn is the `if` statement.</span></span> <span data-ttu-id="ceaca-112">U kunt hiermee een script blok uitvoeren als een instructie is `$true` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-112">It lets you execute a script block if a statement is `$true`.</span></span>

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

<span data-ttu-id="ceaca-113">U kunt veel gecompliceerdere logica hebben door gebruik `elseif` te maken van en- `else` instructies.</span><span class="sxs-lookup"><span data-stu-id="ceaca-113">You can have much more complicated logic by using `elseif` and `else` statements.</span></span> <span data-ttu-id="ceaca-114">Hier volgt een voor beeld waarin ik een numerieke waarde voor de dag van de week heb en de naam als teken reeks wil ophalen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-114">Here is an example where I have a numeric value for day of the week and I want to get the name as a string.</span></span>

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

<span data-ttu-id="ceaca-115">Hiermee wordt aangegeven dat dit een gemeen schappelijk patroon is en er verschillende manieren zijn om dit te verwerken.</span><span class="sxs-lookup"><span data-stu-id="ceaca-115">It turns out that this is a common pattern and there are many ways to deal with this.</span></span> <span data-ttu-id="ceaca-116">Een van deze is met een `switch` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-116">One of them is with a `switch`.</span></span>

## <a name="switch-statement"></a><span data-ttu-id="ceaca-117">Switch-instructie</span><span class="sxs-lookup"><span data-stu-id="ceaca-117">Switch statement</span></span>

<span data-ttu-id="ceaca-118">Met de- `switch` instructie kunt u een variabele en een lijst met mogelijke waarden opgeven.</span><span class="sxs-lookup"><span data-stu-id="ceaca-118">The `switch` statement allows you to provide a variable and a list of possible values.</span></span> <span data-ttu-id="ceaca-119">Als de waarde overeenkomt met de variabele, wordt de script Block uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ceaca-119">If the value matches the variable, then its scriptblock is executed.</span></span>

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

<span data-ttu-id="ceaca-120">Voor dit voor beeld is de waarde van `$day` overeenkomt met een van de numerieke waarden. vervolgens wordt de juiste naam toegewezen aan `$result` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-120">For this example, the value of `$day` matches one of the numeric values, then the correct name is assigned to `$result`.</span></span> <span data-ttu-id="ceaca-121">In dit voor beeld maken we alleen een variabele-toewijzing, maar Power shell kan in die script blokken worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ceaca-121">We are only doing a variable assignment in this example, but any PowerShell can be executed in those script blocks.</span></span>

### <a name="assign-to-a-variable"></a><span data-ttu-id="ceaca-122">Toewijzen aan een variabele</span><span class="sxs-lookup"><span data-stu-id="ceaca-122">Assign to a variable</span></span>

<span data-ttu-id="ceaca-123">We kunnen dat laatste voor beeld op een andere manier schrijven.</span><span class="sxs-lookup"><span data-stu-id="ceaca-123">We can write that last example in another way.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

<span data-ttu-id="ceaca-124">We plaatsen de waarde op de Power shell-pijp lijn en wijzen deze toe aan de `$result` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-124">We are placing the value on the PowerShell pipeline and assigning it to the `$result`.</span></span> <span data-ttu-id="ceaca-125">U kunt dit hetzelfde doen met de `if` instructies and `foreach` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-125">You can do this same thing with the `if` and `foreach` statements.</span></span>

### <a name="default"></a><span data-ttu-id="ceaca-126">Standaard</span><span class="sxs-lookup"><span data-stu-id="ceaca-126">Default</span></span>

<span data-ttu-id="ceaca-127">We kunnen het `default` sleutel woord gebruiken om aan te geven wat er moet gebeuren als er geen overeenkomst is.</span><span class="sxs-lookup"><span data-stu-id="ceaca-127">We can use the `default` keyword to identify the what should happen if there is no match.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

<span data-ttu-id="ceaca-128">Hier retour neren we de waarde `Unknown` in de standaard situatie.</span><span class="sxs-lookup"><span data-stu-id="ceaca-128">Here we return the value `Unknown` in the default case.</span></span>

### <a name="strings"></a><span data-ttu-id="ceaca-129">Tekenreeksen</span><span class="sxs-lookup"><span data-stu-id="ceaca-129">Strings</span></span>

<span data-ttu-id="ceaca-130">Ik vond getallen in de laatste voor beelden, maar u kunt ook teken reeksen overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-130">I was matching numbers in those last examples, but you can also match strings.</span></span>

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="ceaca-131">Ik heb besloten om het niet `Component` in te pakken `Role` en `Location` komt hier overeen met aanhalings tekens om te markeren dat ze optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="ceaca-131">I decided not to wrap the `Component`,`Role` and `Location` matches in quotes here to highlight that they're optional.</span></span> <span data-ttu-id="ceaca-132">`switch`In de meeste gevallen worden deze behandeld als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="ceaca-132">The `switch` treats those as a string in most cases.</span></span>

## <a name="arrays"></a><span data-ttu-id="ceaca-133">Matrices</span><span class="sxs-lookup"><span data-stu-id="ceaca-133">Arrays</span></span>

<span data-ttu-id="ceaca-134">Een van de coole functies van Power shell `switch` is de manier waarop de arrays worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-134">One of the cool features of the PowerShell `switch` is the way it handles arrays.</span></span> <span data-ttu-id="ceaca-135">Als u een `switch` matrix geeft, wordt elk element in die verzameling verwerkt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-135">If you give a `switch` an array, it processes each element in that collection.</span></span>

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

<span data-ttu-id="ceaca-136">Als u items in uw matrix hebt herhaald, worden deze meerdere keren met de juiste sectie overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-136">If you have repeated items in your array, then they're matched multiple times by the appropriate section.</span></span>

### <a name="psitem"></a><span data-ttu-id="ceaca-137">PSItem</span><span class="sxs-lookup"><span data-stu-id="ceaca-137">PSItem</span></span>

<span data-ttu-id="ceaca-138">U kunt de `$PSItem` of gebruiken `$_` om te verwijzen naar het huidige item dat is verwerkt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-138">You can use the `$PSItem` or `$_` to reference the current item that was processed.</span></span> <span data-ttu-id="ceaca-139">Wanneer we een eenvoudige overeenkomst volgen, `$PSItem` is de waarde die we overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-139">When we do a simple match, `$PSItem` is the value that we are matching.</span></span> <span data-ttu-id="ceaca-140">Ik voer enkele geavanceerde overeenkomsten uit in de volgende sectie waar deze variabele wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-140">I'll be performing some advanced matches in the next section where this variable is used.</span></span>

## <a name="parameters"></a><span data-ttu-id="ceaca-141">Parameters</span><span class="sxs-lookup"><span data-stu-id="ceaca-141">Parameters</span></span>

<span data-ttu-id="ceaca-142">Een unieke functie van de Power shell `switch` is dat deze een aantal [para meters][] heeft die wijzigen hoe deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ceaca-142">A unique feature of the PowerShell `switch` is that it has a number of [switch parameters][] that change how it performs.</span></span>

### <a name="-casesensitive"></a><span data-ttu-id="ceaca-143">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="ceaca-143">-CaseSensitive</span></span>

<span data-ttu-id="ceaca-144">De overeenkomsten zijn standaard niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="ceaca-144">The matches aren't case-sensitive by default.</span></span> <span data-ttu-id="ceaca-145">Als u hoofdletter gevoelig moet zijn, kunt u gebruiken `-CaseSensitive` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-145">If you need to be case-sensitive, you can use `-CaseSensitive`.</span></span> <span data-ttu-id="ceaca-146">Dit kan worden gebruikt in combi natie met de andere para meters voor switches.</span><span class="sxs-lookup"><span data-stu-id="ceaca-146">This can be used in combination with the other switch parameters.</span></span>

### <a name="-wildcard"></a><span data-ttu-id="ceaca-147">-Joker teken</span><span class="sxs-lookup"><span data-stu-id="ceaca-147">-Wildcard</span></span>

<span data-ttu-id="ceaca-148">U kunt ondersteuning voor joker tekens inschakelen met de `-wildcard` Switch.</span><span class="sxs-lookup"><span data-stu-id="ceaca-148">We can enable wildcard support with the `-wildcard` switch.</span></span> <span data-ttu-id="ceaca-149">Dit maakt gebruik van dezelfde Joker teken-Logic als de `-like` operator voor elke overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="ceaca-149">This uses the same wildcard logic as the `-like` operator to do each match.</span></span>

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

<span data-ttu-id="ceaca-150">Hier verwerken we een bericht en voeren we het uit op verschillende stromen op basis van de inhoud.</span><span class="sxs-lookup"><span data-stu-id="ceaca-150">Here we are processing a message and then outputting it on different streams based on the contents.</span></span>

### <a name="-regex"></a><span data-ttu-id="ceaca-151">-Regex</span><span class="sxs-lookup"><span data-stu-id="ceaca-151">-Regex</span></span>

<span data-ttu-id="ceaca-152">De instructie switch ondersteunt regex-overeenkomsten op dezelfde manier als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="ceaca-152">The switch statement supports regex matches just like it does wildcards.</span></span>

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

<span data-ttu-id="ceaca-153">Ik heb meer voor beelden van het gebruik van regex in een ander artikel dat ik heb geschreven: [de vele manieren om regex te gebruiken][].</span><span class="sxs-lookup"><span data-stu-id="ceaca-153">I have more examples of using regex in another article I wrote: [The many ways to use regex][].</span></span>

### <a name="-file"></a><span data-ttu-id="ceaca-154">-Bestand</span><span class="sxs-lookup"><span data-stu-id="ceaca-154">-File</span></span>

<span data-ttu-id="ceaca-155">Een kleine bekende functie van de instructie switch is dat een bestand met de para meter kan worden verwerkt `-File` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-155">A little known feature of the switch statement is that it can process a file with the `-File` parameter.</span></span> <span data-ttu-id="ceaca-156">U gebruikt `-file` met een pad naar een bestand in plaats van het een variabele-expressie op te geven.</span><span class="sxs-lookup"><span data-stu-id="ceaca-156">You use `-file` with a path to a file instead of giving it a variable expression.</span></span>

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="ceaca-157">Het werkt net zoals bij het verwerken van een matrix.</span><span class="sxs-lookup"><span data-stu-id="ceaca-157">It works just like processing an array.</span></span> <span data-ttu-id="ceaca-158">In dit voor beeld moet ik deze combi neren met Joker tekens die overeenkomen en het gebruik van gebruiken `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-158">In this example, I combine it with wildcard matching and make use of the `$PSItem`.</span></span> <span data-ttu-id="ceaca-159">Hiermee wordt een logboek bestand verwerkt en omgezet in waarschuwings-en fout berichten, afhankelijk van de regex-overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="ceaca-159">This would process a log file and convert it to warning and error messages depending on the regex matches.</span></span>

## <a name="advanced-details"></a><span data-ttu-id="ceaca-160">Gedetailleerde Details</span><span class="sxs-lookup"><span data-stu-id="ceaca-160">Advanced details</span></span>

<span data-ttu-id="ceaca-161">Nu u op de hoogte bent van al deze gedocumenteerde functies, kunnen we deze gebruiken in de context van geavanceerdere verwerking.</span><span class="sxs-lookup"><span data-stu-id="ceaca-161">Now that you're aware of all these documented features, we can use them in the context of more advanced processing.</span></span>

### <a name="expressions"></a><span data-ttu-id="ceaca-162">Expressies</span><span class="sxs-lookup"><span data-stu-id="ceaca-162">Expressions</span></span>

<span data-ttu-id="ceaca-163">De `switch` kan zich in een expressie bevindt in plaats van een variabele.</span><span class="sxs-lookup"><span data-stu-id="ceaca-163">The `switch` can be on an expression instead of a variable.</span></span>

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

<span data-ttu-id="ceaca-164">Ongeacht de expressie wordt geëvalueerd naar de waarde die wordt gebruikt voor de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="ceaca-164">Whatever the expression evaluates to is the value used for the match.</span></span>

### <a name="multiple-matches"></a><span data-ttu-id="ceaca-165">Meerdere overeenkomsten</span><span class="sxs-lookup"><span data-stu-id="ceaca-165">Multiple matches</span></span>

<span data-ttu-id="ceaca-166">U hebt deze mogelijk al verzameld, maar een `switch` kan overeenkomen met meerdere voor waarden.</span><span class="sxs-lookup"><span data-stu-id="ceaca-166">You may have already picked up on this, but a `switch` can match to multiple conditions.</span></span> <span data-ttu-id="ceaca-167">Dit geldt met name bij het gebruik van `-wildcard` of `-regex` overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="ceaca-167">This is especially true when using `-wildcard` or `-regex` matches.</span></span> <span data-ttu-id="ceaca-168">U kunt dezelfde voor waarde meerdere keren toevoegen en deze allemaal worden geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ceaca-168">You can add the same condition multiple times and all of them are triggered.</span></span>

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

<span data-ttu-id="ceaca-169">Alle drie de instructies worden gestart.</span><span class="sxs-lookup"><span data-stu-id="ceaca-169">All three of these statements are fired.</span></span> <span data-ttu-id="ceaca-170">Dit betekent dat elke voor waarde is ingeschakeld (op volg orde).</span><span class="sxs-lookup"><span data-stu-id="ceaca-170">This shows that every condition is checked (in order).</span></span> <span data-ttu-id="ceaca-171">Dit geldt voor verwerkings matrices waarbij elk item elke voor waarde controleert.</span><span class="sxs-lookup"><span data-stu-id="ceaca-171">This holds true for processing arrays where each item checks each condition.</span></span>

### <a name="continue"></a><span data-ttu-id="ceaca-172">Doorgaan</span><span class="sxs-lookup"><span data-stu-id="ceaca-172">Continue</span></span>

<span data-ttu-id="ceaca-173">Normaal gesp roken is dit waar ik de instructie zou introducen `break` , maar het is beter om eerst te leren hoe we het moeten gebruiken `continue` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-173">Normally, this is where I would introduce the `break` statement, but it's better that we learn how to use `continue` first.</span></span> <span data-ttu-id="ceaca-174">Net als bij een `foreach` lus `continue` gaat u verder met het volgende item in de verzameling of sluit u het `switch` als er geen items meer zijn.</span><span class="sxs-lookup"><span data-stu-id="ceaca-174">Just like with a `foreach` loop, `continue` continues onto the next item in the collection or exits the `switch` if there are no more items.</span></span> <span data-ttu-id="ceaca-175">We kunnen dat laatste voor beeld met continue instructies herschrijven, zodat er slechts één instructie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ceaca-175">We can rewrite that last example with continue statements so that only one statement executes.</span></span>

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

<span data-ttu-id="ceaca-176">In plaats van alle drie de items te vergelijken, wordt de eerste overeenkomst vergeleken en gaat de switch verder met de volgende waarde.</span><span class="sxs-lookup"><span data-stu-id="ceaca-176">Instead of matching all three items, the first one is matched and the switch continues to the next value.</span></span> <span data-ttu-id="ceaca-177">Omdat er nog geen waarden meer zijn om te verwerken, wordt de switch afgesloten.</span><span class="sxs-lookup"><span data-stu-id="ceaca-177">Because there are no values left to process, the switch exits.</span></span> <span data-ttu-id="ceaca-178">In dit volgende voor beeld wordt weer gegeven hoe een Joker teken kan overeenkomen met meerdere items.</span><span class="sxs-lookup"><span data-stu-id="ceaca-178">This next example is showing how a wildcard could match multiple items.</span></span>

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="ceaca-179">Omdat een regel in het invoer bestand het woord zou kunnen bevatten `Error` en `Warning` , willen we alleen dat het eerst wordt uitgevoerd en vervolgens door gaan met het verwerken van het bestand.</span><span class="sxs-lookup"><span data-stu-id="ceaca-179">Because a line in the input file could contain both the word `Error` and `Warning`, we only want the first one to execute and then continue processing the file.</span></span>

### <a name="break"></a><span data-ttu-id="ceaca-180">Breken</span><span class="sxs-lookup"><span data-stu-id="ceaca-180">Break</span></span>

<span data-ttu-id="ceaca-181">Een `break` instructie sluit de switch af.</span><span class="sxs-lookup"><span data-stu-id="ceaca-181">A `break` statement exits the switch.</span></span> <span data-ttu-id="ceaca-182">Dit is hetzelfde gedrag dat `continue` voor één waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ceaca-182">This is the same behavior that `continue` presents for single values.</span></span> <span data-ttu-id="ceaca-183">Het verschil wordt weer gegeven bij het verwerken van een matrix.</span><span class="sxs-lookup"><span data-stu-id="ceaca-183">The difference is shown when processing an array.</span></span> <span data-ttu-id="ceaca-184">`break` stopt alle verwerking van de switch en `continue` gaat naar het volgende item.</span><span class="sxs-lookup"><span data-stu-id="ceaca-184">`break` stops all processing in the switch and `continue` moves onto the next item.</span></span>

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

<span data-ttu-id="ceaca-185">Als we in dit geval regels hebben bezocht die beginnen met, `Error` krijgen we een fout melding en wordt de switch gestopt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-185">In this case, if we hit any lines that start with `Error` then we get an error and the switch stops.</span></span>
<span data-ttu-id="ceaca-186">Dit is wat de `break` instructie voor ons doet.</span><span class="sxs-lookup"><span data-stu-id="ceaca-186">This is what that `break` statement is doing for us.</span></span> <span data-ttu-id="ceaca-187">Als we `Error` in de teken reeks zoeken en niet alleen aan het begin, schrijven we deze als een waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="ceaca-187">If we find `Error` inside the string and not just at the beginning, we write it as a warning.</span></span> <span data-ttu-id="ceaca-188">We doen hetzelfde voor `Warning` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-188">We do the same thing for `Warning`.</span></span> <span data-ttu-id="ceaca-189">Het is mogelijk dat een regel zowel het woord als heeft `Error` `Warning` , maar er is slechts één nodig om te verwerken.</span><span class="sxs-lookup"><span data-stu-id="ceaca-189">It's possible that a line could have both the word `Error` and `Warning`, but we only need one to process.</span></span> <span data-ttu-id="ceaca-190">Dit is de `continue` instructie voor ons.</span><span class="sxs-lookup"><span data-stu-id="ceaca-190">This is what the `continue` statement is doing for us.</span></span>

### <a name="break-labels"></a><span data-ttu-id="ceaca-191">Labels opdelen</span><span class="sxs-lookup"><span data-stu-id="ceaca-191">Break labels</span></span>

<span data-ttu-id="ceaca-192">De `switch` instructie ondersteunt `break/continue` labels op dezelfde manier als `foreach` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-192">The `switch` statement supports `break/continue` labels just like `foreach`.</span></span>

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

<span data-ttu-id="ceaca-193">Ik ben niet tevreden over het gebruik van labels voor het kraken, maar ik wilde er wel eens mee weten dat ze verwarrend zijn als u ze nog nooit eerder hebt gezien.</span><span class="sxs-lookup"><span data-stu-id="ceaca-193">I personally don't like the use of break labels but I wanted to point them out because they're confusing if you've never seen them before.</span></span> <span data-ttu-id="ceaca-194">Wanneer u meerdere `switch` of `foreach` geneste instructies hebt, wilt u mogelijk meer dan het binnenste item opdelen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-194">When you have multiple `switch` or `foreach` statements that are nested, you may want to break out of more than the inner most item.</span></span> <span data-ttu-id="ceaca-195">U kunt een label plaatsen op een adres `switch` dat het doel van uw kan zijn `break` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-195">You can place a label on a `switch` that can be the target of your `break`.</span></span>

### <a name="enum"></a><span data-ttu-id="ceaca-196">Enum</span><span class="sxs-lookup"><span data-stu-id="ceaca-196">Enum</span></span>

<span data-ttu-id="ceaca-197">Power shell 5,0 heeft de Enum-teksten geleverd en we kunnen deze gebruiken in een switch.</span><span class="sxs-lookup"><span data-stu-id="ceaca-197">PowerShell 5.0 gave us enums and we can use them in a switch.</span></span>

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="ceaca-198">Als u alles wilt opslaan als een sterk getypeerde opsommings punt, kunt u ze tussen haakjes plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-198">If you want to keep everything as strongly typed enums, then you can place them in parentheses.</span></span>

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

<span data-ttu-id="ceaca-199">De haakjes zijn hier nodig, zodat de switch de waarde niet `[Context]::Location` als een letterlijke teken reeks behandelt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-199">The parentheses are needed here so that the switch doesn't treat the value `[Context]::Location` as a literal string.</span></span>

### <a name="scriptblock"></a><span data-ttu-id="ceaca-200">Script Block</span><span class="sxs-lookup"><span data-stu-id="ceaca-200">ScriptBlock</span></span>

<span data-ttu-id="ceaca-201">We kunnen een script Block gebruiken om de evaluatie uit te voeren voor een overeenkomst, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="ceaca-201">We can use a scriptblock to perform the evaluation for a match if needed.</span></span>

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

<span data-ttu-id="ceaca-202">Dit voegt complexiteit toe en maakt het mogelijk `switch` om uw moeilijk te lezen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-202">This adds complexity and can make your `switch` hard to read.</span></span> <span data-ttu-id="ceaca-203">In de meeste gevallen is het beter om het gebruik en de instructies te gebruiken `if` `elseif` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-203">In most cases where you would use something like this it would be better to use `if` and `elseif` statements.</span></span> <span data-ttu-id="ceaca-204">Ik zou dit ook gebruiken als ik al een grote switch heb en ik heb twee items nodig om hetzelfde evaluatie blok te bereiken.</span><span class="sxs-lookup"><span data-stu-id="ceaca-204">I would consider using this if I already had a large switch in place and I needed two items to hit the same evaluation block.</span></span>

<span data-ttu-id="ceaca-205">Een ding die ik denk aan de Lees baarheid, is om de script Block tussen haakjes te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-205">One thing that I think helps with legibility is to place the scriptblock in parentheses.</span></span>

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

<span data-ttu-id="ceaca-206">Het wordt nog steeds op dezelfde manier uitgevoerd en biedt een betere visuele afbreek tijd wanneer u deze snel bekijkt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-206">It still executes the same way and gives a better visual break when quickly looking at it.</span></span>

### <a name="regex-matches"></a><span data-ttu-id="ceaca-207">Regex $matches</span><span class="sxs-lookup"><span data-stu-id="ceaca-207">Regex $matches</span></span>

<span data-ttu-id="ceaca-208">We moeten de regex opnieuw bezoeken om iets te raken dat niet direct zichtbaar is.</span><span class="sxs-lookup"><span data-stu-id="ceaca-208">We need to revisit regex to touch on something that isn't immediately obvious.</span></span> <span data-ttu-id="ceaca-209">Het gebruik van regex vult de `$matches` variabele.</span><span class="sxs-lookup"><span data-stu-id="ceaca-209">The use of regex populates the `$matches` variable.</span></span> <span data-ttu-id="ceaca-210">Ik ga naar het gebruik van `$matches` meer wanneer ik [op de vele manieren met regex][]gepraat.</span><span class="sxs-lookup"><span data-stu-id="ceaca-210">I do go into the use of `$matches` more when I talk about [The many ways to use regex][].</span></span> <span data-ttu-id="ceaca-211">Hier volgt een kort voor beeld om het weer te geven in actie met benoemde overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="ceaca-211">Here is a quick sample to show it in action with named matches.</span></span>

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a><span data-ttu-id="ceaca-212">$null</span><span class="sxs-lookup"><span data-stu-id="ceaca-212">$null</span></span>

<span data-ttu-id="ceaca-213">U kunt een `$null` waarde die niet standaard is, vergelijken.</span><span class="sxs-lookup"><span data-stu-id="ceaca-213">You can match a `$null` value that doesn't have to be the default.</span></span>

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

<span data-ttu-id="ceaca-214">Hetzelfde geldt voor een lege teken reeks.</span><span class="sxs-lookup"><span data-stu-id="ceaca-214">Same goes for an empty string.</span></span>

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a><span data-ttu-id="ceaca-215">Constante-expressie</span><span class="sxs-lookup"><span data-stu-id="ceaca-215">Constant expression</span></span>

<span data-ttu-id="ceaca-216">Lee Dailey verwijst dat we een constante-expressie kunnen gebruiken `$true` om `[bool]` items te evalueren.</span><span class="sxs-lookup"><span data-stu-id="ceaca-216">Lee Dailey pointed out that we can use a constant `$true` expression to evaluate `[bool]` items.</span></span>
<span data-ttu-id="ceaca-217">Stel dat er verschillende Booleaanse controles moeten plaatsvinden.</span><span class="sxs-lookup"><span data-stu-id="ceaca-217">Imagine if we have several boolean checks that need to happen.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

<span data-ttu-id="ceaca-218">Dit is een schone manier om de status van verschillende Boole-velden te evalueren en actie te ondernemen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-218">This is a clean way to evaluate and take action on the status of several boolean fields.</span></span> <span data-ttu-id="ceaca-219">Het leuke hiervan is dat u met één overeenkomst de status van een waarde die nog niet is geëvalueerd, kunt spie gelen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-219">The cool thing about this is that you can have one match flip the status of a value that hasn't been evaluated yet.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

<span data-ttu-id="ceaca-220">`$isEnabled` `$true` In dit voor beeld zorgt u ervoor dat `$isVisible` ook is ingesteld op `$true` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-220">Setting `$isEnabled` to `$true` in this example makes sure that `$isVisible` is also set to `$true`.</span></span> <span data-ttu-id="ceaca-221">Vervolgens `$isVisible` wordt de script Block geactiveerd wanneer deze wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ceaca-221">Then when `$isVisible` gets evaluated, its scriptblock is invoked.</span></span> <span data-ttu-id="ceaca-222">Dit is een beetje intuïtieve teller, maar is een slimme toepassing van de mechanismen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-222">This is a bit counter-intuitive but is a clever use of the mechanics.</span></span>

### <a name="switch-automatic-variable"></a><span data-ttu-id="ceaca-223">Automatische variabele $switch</span><span class="sxs-lookup"><span data-stu-id="ceaca-223">$switch automatic variable</span></span>

<span data-ttu-id="ceaca-224">Wanneer de `switch` waarden worden verwerkt, wordt een enumerator gemaakt en aangeroepen `$switch` .</span><span class="sxs-lookup"><span data-stu-id="ceaca-224">When the `switch` is processing its values, it creates an enumerator and calls it `$switch`.</span></span> <span data-ttu-id="ceaca-225">Dit is een automatische variabele die door Power shell wordt gemaakt en u kunt deze rechtstreeks bewerken.</span><span class="sxs-lookup"><span data-stu-id="ceaca-225">This is an automatic variable created by PowerShell and you can manipulate it directly.</span></span>

```powershell
$a = 1, 2, 3, 4

switch($a) {
    1 { [void]$switch.MoveNext(); $switch.Current }
    3 { [void]$switch.MoveNext(); $switch.Current }
}
```

<span data-ttu-id="ceaca-226">Dit geeft u de resultaten van:</span><span class="sxs-lookup"><span data-stu-id="ceaca-226">This gives you the results of:</span></span>

```Output
2
4
```

<span data-ttu-id="ceaca-227">Door de enumerator vooruit te verplaatsen, wordt het volgende item niet verwerkt door de `switch` maar hebt u rechtstreeks toegang tot deze waarde.</span><span class="sxs-lookup"><span data-stu-id="ceaca-227">By moving the enumerator forward, the next item doesn't get processed by the `switch` but you can access that value directly.</span></span> <span data-ttu-id="ceaca-228">Ik zou dit ook aanroepen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-228">I would call it madness.</span></span>

## <a name="other-patterns"></a><span data-ttu-id="ceaca-229">Andere patronen</span><span class="sxs-lookup"><span data-stu-id="ceaca-229">Other patterns</span></span>

### <a name="hashtables"></a><span data-ttu-id="ceaca-230">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="ceaca-230">Hashtables</span></span>

<span data-ttu-id="ceaca-231">Een van mijn populairste berichten is de versie van [hashtabellen][].</span><span class="sxs-lookup"><span data-stu-id="ceaca-231">One of my most popular posts is the one I did on [hashtables][].</span></span> <span data-ttu-id="ceaca-232">Een van de use-cases voor a moet `hashtable` een opzoek tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="ceaca-232">One of the use cases for a `hashtable` is to be a lookup table.</span></span> <span data-ttu-id="ceaca-233">Dit is een alternatieve benadering van een gemeen schappelijk patroon dat een `switch` instructie vaak adressert.</span><span class="sxs-lookup"><span data-stu-id="ceaca-233">That is an alternate approach to a common pattern that a `switch` statement is often addressing.</span></span>

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

<span data-ttu-id="ceaca-234">Als ik alleen een `switch` als lookup gebruik, gebruik ik vaak een `hashtable` in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="ceaca-234">If I'm only using a `switch` as a lookup, I often use a `hashtable` instead.</span></span>

### <a name="enum"></a><span data-ttu-id="ceaca-235">Enum</span><span class="sxs-lookup"><span data-stu-id="ceaca-235">Enum</span></span>

<span data-ttu-id="ceaca-236">Power shell 5,0 `Enum` is geïntroduceerd in en is ook een optie in dit geval.</span><span class="sxs-lookup"><span data-stu-id="ceaca-236">PowerShell 5.0 introduced the `Enum` and it's also an option in this case.</span></span>

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

<span data-ttu-id="ceaca-237">We kunnen de hele dag op verschillende manieren bezoeken om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="ceaca-237">We could go all day looking at different ways to solve this problem.</span></span> <span data-ttu-id="ceaca-238">Ik wil er zeker van zijn dat u wist dat u nog geen opties hebt.</span><span class="sxs-lookup"><span data-stu-id="ceaca-238">I just wanted to make sure you knew you had options.</span></span>

## <a name="final-words"></a><span data-ttu-id="ceaca-239">Laatste woorden</span><span class="sxs-lookup"><span data-stu-id="ceaca-239">Final words</span></span>

<span data-ttu-id="ceaca-240">De instructie switch is eenvoudig op het Opper vlak, maar biedt een aantal geavanceerde functies die de meeste mensen niet realiseren.</span><span class="sxs-lookup"><span data-stu-id="ceaca-240">The switch statement is simple on the surface but it offers some advanced features that most people don't realize are available.</span></span> <span data-ttu-id="ceaca-241">Door deze functies samen te stellen, is dit een krachtig onderdeel.</span><span class="sxs-lookup"><span data-stu-id="ceaca-241">Stringing those features together makes this a powerful feature.</span></span> <span data-ttu-id="ceaca-242">Ik hoop dat u iets hebt geleerd dat u nog niet eerder hebt gerealiseerd.</span><span class="sxs-lookup"><span data-stu-id="ceaca-242">I hope you learned something that you had not realized before.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[original version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[/tijdnotatie]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch parameters]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[De vele manieren om regex te gebruiken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[hashtabellen]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
