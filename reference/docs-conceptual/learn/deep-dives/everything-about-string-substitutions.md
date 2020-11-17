---
title: Alles wat u wilt weten over variabele vervanging in teken reeksen
description: Er zijn veel manieren om variabelen in teken reeksen te gebruiken om opgemaakte tekst te maken.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 786526fb98dbf1b3ec7c5c6c985ac95b85a96259
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301315"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a><span data-ttu-id="2d670-103">Alles wat u wilt weten over variabele vervanging in teken reeksen</span><span class="sxs-lookup"><span data-stu-id="2d670-103">Everything you wanted to know about variable substitution in strings</span></span>

<span data-ttu-id="2d670-104">Er zijn veel manieren om variabelen in teken reeksen te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2d670-104">There are many ways to use variables in strings.</span></span> <span data-ttu-id="2d670-105">Ik roep deze vervanging van variabelen aan, maar ik Raadpleeg een wille keurig tijdstip waarop u een teken reeks wilt opmaken om waarden van variabelen op te nemen.</span><span class="sxs-lookup"><span data-stu-id="2d670-105">I'm calling this variable substitution but I'm referring to any time you want to format a string to include values from variables.</span></span> <span data-ttu-id="2d670-106">Dit is iets wat ik vaak Zoek in nieuwe scripts.</span><span class="sxs-lookup"><span data-stu-id="2d670-106">This is something that I often find myself explaining to new scripters.</span></span>

> [!NOTE]
> <span data-ttu-id="2d670-107">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="2d670-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="2d670-108">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="2d670-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="2d670-109">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="2d670-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="concatenation"></a><span data-ttu-id="2d670-110">Samenvoeging</span><span class="sxs-lookup"><span data-stu-id="2d670-110">Concatenation</span></span>

<span data-ttu-id="2d670-111">De eerste klasse van methoden kan worden aangeduid als samen voeging.</span><span class="sxs-lookup"><span data-stu-id="2d670-111">The first class of methods can be referred to as concatenation.</span></span> <span data-ttu-id="2d670-112">Het is in wezen meerdere teken reeksen te maken en samen te voegen.</span><span class="sxs-lookup"><span data-stu-id="2d670-112">It's basically taking several strings and joining them together.</span></span> <span data-ttu-id="2d670-113">Er is een lange geschiedenis van het gebruik van samen voeging om opgemaakte teken reeksen te maken.</span><span class="sxs-lookup"><span data-stu-id="2d670-113">There's a long history of using concatenation to build formatted strings.</span></span>

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

<span data-ttu-id="2d670-114">Samen voegen werkt op OK wanneer er slechts enkele waarden kunnen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2d670-114">Concatenation works out OK when there are only a few values to add.</span></span> <span data-ttu-id="2d670-115">Maar dit kan ingewikkeld zijn.</span><span class="sxs-lookup"><span data-stu-id="2d670-115">But this can get complicated quickly.</span></span>

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

<span data-ttu-id="2d670-116">Dit eenvoudige voor beeld is al moeilijker te lezen.</span><span class="sxs-lookup"><span data-stu-id="2d670-116">This simple example is already getting harder to read.</span></span>

## <a name="variable-substitution"></a><span data-ttu-id="2d670-117">Vervanging van variabelen</span><span class="sxs-lookup"><span data-stu-id="2d670-117">Variable substitution</span></span>

<span data-ttu-id="2d670-118">Power Shell heeft nog een andere optie die eenvoudiger is.</span><span class="sxs-lookup"><span data-stu-id="2d670-118">PowerShell has another option that is easier.</span></span> <span data-ttu-id="2d670-119">U kunt de variabelen rechtstreeks in de teken reeksen opgeven.</span><span class="sxs-lookup"><span data-stu-id="2d670-119">You can specify your variables directly in the strings.</span></span>

```powershell
$message = "Hello, $first $last."
```

<span data-ttu-id="2d670-120">Het type aanhalings tekens dat u voor de teken reeks gebruikt, maakt een verschil.</span><span class="sxs-lookup"><span data-stu-id="2d670-120">The type of quotes you use around the string makes a difference.</span></span> <span data-ttu-id="2d670-121">Een teken reeks met dubbele aanhalings tekens kan worden vervangen, maar een enkele aanhalings teken reeks niet.</span><span class="sxs-lookup"><span data-stu-id="2d670-121">A double quoted string allows the substitution but a single quoted string doesn't.</span></span> <span data-ttu-id="2d670-122">Het kan zijn dat u een of meer opties wilt maken.</span><span class="sxs-lookup"><span data-stu-id="2d670-122">There are times you want one or the other so you have an option.</span></span>

## <a name="command-substitution"></a><span data-ttu-id="2d670-123">Opdracht vervanging</span><span class="sxs-lookup"><span data-stu-id="2d670-123">Command substitution</span></span>

<span data-ttu-id="2d670-124">Het kan even duren wanneer u begint met het ophalen van de waarden van eigenschappen in een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2d670-124">Things get a little tricky when you start trying to get the values of properties into a string.</span></span> <span data-ttu-id="2d670-125">Hier worden veel nieuwe personen in de weg staan.</span><span class="sxs-lookup"><span data-stu-id="2d670-125">This is where many new people get tripped up.</span></span> <span data-ttu-id="2d670-126">Eerst laten we u zien wat ze denken te werk (en bij gezichts waarde lijkt het alsof het zou).</span><span class="sxs-lookup"><span data-stu-id="2d670-126">First let me show you what they think should work (and at face value almost looks like it should).</span></span>

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

<span data-ttu-id="2d670-127">U wordt verwacht om aan de slag te gaan `CreationTime` `$directory` , maar u krijgt dit in plaats daarvan `Time: c:\windows.CreationTime` als uw waarde.</span><span class="sxs-lookup"><span data-stu-id="2d670-127">You would be expecting to get the `CreationTime` off of the `$directory`, but instead you get this `Time: c:\windows.CreationTime` as your value.</span></span> <span data-ttu-id="2d670-128">De reden is dat dit type vervanging alleen de basis variabele ziet.</span><span class="sxs-lookup"><span data-stu-id="2d670-128">The reason is that this type of substitution only sees the base variable.</span></span> <span data-ttu-id="2d670-129">De periode wordt beschouwd als onderdeel van de teken reeks, zodat de waarde niet meer kan worden opgelost.</span><span class="sxs-lookup"><span data-stu-id="2d670-129">It considers the period as part of the string so it stops resolving the value any deeper.</span></span>

<span data-ttu-id="2d670-130">Dit betekent dat dit object een teken reeks als standaard waarde geeft wanneer deze in een teken reeks wordt geplaatst.</span><span class="sxs-lookup"><span data-stu-id="2d670-130">It just so happens that this object gives a string as a default value when placed into a string.</span></span>
<span data-ttu-id="2d670-131">Sommige objecten geven u de type naam in plaats van een `System.Collections.Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="2d670-131">Some objects give you the type name instead like `System.Collections.Hashtable`.</span></span> <span data-ttu-id="2d670-132">Iets om te kijken naar.</span><span class="sxs-lookup"><span data-stu-id="2d670-132">Just something to watch for.</span></span>

<span data-ttu-id="2d670-133">Met Power shell kunt u opdrachten uitvoeren binnen de teken reeks met een speciale syntaxis.</span><span class="sxs-lookup"><span data-stu-id="2d670-133">PowerShell allows you to do command execution inside the string with a special syntax.</span></span> <span data-ttu-id="2d670-134">Hierdoor kunnen we de eigenschappen van deze objecten ophalen en een andere opdracht uitvoeren om een waarde op te halen.</span><span class="sxs-lookup"><span data-stu-id="2d670-134">This allows us to get the properties of these objects and run any other command to get a value.</span></span>

```powershell
$message = "Time: $($directory.CreationTime)"
```

<span data-ttu-id="2d670-135">Dit werkt prima voor bepaalde situaties, maar het kan net zo gekke zijn als samen voegen als u slechts een paar variabelen hebt.</span><span class="sxs-lookup"><span data-stu-id="2d670-135">This works great for some situations but it can get just as crazy as concatenation if you have just a few variables.</span></span>

### <a name="command-execution"></a><span data-ttu-id="2d670-136">Opdrachtuitvoering</span><span class="sxs-lookup"><span data-stu-id="2d670-136">Command execution</span></span>

<span data-ttu-id="2d670-137">U kunt opdrachten binnen een teken reeks uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="2d670-137">You can run commands inside a string.</span></span> <span data-ttu-id="2d670-138">Hoewel ik deze optie heb, vind ik deze niet mooi.</span><span class="sxs-lookup"><span data-stu-id="2d670-138">Even though I have this option, I don't like it.</span></span> <span data-ttu-id="2d670-139">Het wordt snel en moeilijk geruimed om fouten op te sporen.</span><span class="sxs-lookup"><span data-stu-id="2d670-139">It gets cluttered quickly and hard to debug.</span></span> <span data-ttu-id="2d670-140">Ik voer de opdracht uit en sla deze op in een variabele of gebruik een opmaak teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2d670-140">I either run the command and save to a variable or use a format string.</span></span>

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a><span data-ttu-id="2d670-141">Notatietekenreeks</span><span class="sxs-lookup"><span data-stu-id="2d670-141">Format string</span></span>

<span data-ttu-id="2d670-142">.NET heeft een manier om teken reeksen te Format teren die ik redelijk eenvoudig kan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2d670-142">.NET has a way to format strings that I find fairly easy to work with.</span></span> <span data-ttu-id="2d670-143">Eerst laten we u de statische methode voor deze weer geven voordat u de Power shell-snelkoppeling weergeeft om hetzelfde te doen.</span><span class="sxs-lookup"><span data-stu-id="2d670-143">First let me show you the static method for it before I show you the PowerShell shortcut to do the same thing.</span></span>

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

<span data-ttu-id="2d670-144">Hier vindt u de teken reeks die wordt geparseerd voor de tokens `{0}` en `{1}` vervolgens gebruikt u dat nummer om te kiezen uit de waarden die worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2d670-144">What is happening here is that the string is parsed for the tokens `{0}` and `{1}`, then it uses that number to pick from the values provided.</span></span> <span data-ttu-id="2d670-145">Als u één waarde op een plek in de teken reeks wilt herhalen, kunt u het aantal waarden opnieuw gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2d670-145">If you want to repeat one value some place in the string, you can reuse that values number.</span></span>

<span data-ttu-id="2d670-146">Hoe complexer de teken reeks, hoe meer u uit deze benadering haalt.</span><span class="sxs-lookup"><span data-stu-id="2d670-146">The more complicated the string gets, the more value you get out of this approach.</span></span>

### <a name="format-values-as-arrays"></a><span data-ttu-id="2d670-147">Waarden opmaken als matrices</span><span class="sxs-lookup"><span data-stu-id="2d670-147">Format values as arrays</span></span>

<span data-ttu-id="2d670-148">Als uw opmaak regel te lang wordt, kunt u de waarden eerst in een matrix plaatsen.</span><span class="sxs-lookup"><span data-stu-id="2d670-148">If your format line gets too long, you can place your values into an array first.</span></span>

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

<span data-ttu-id="2d670-149">Dit is niet splatting omdat de gehele matrix wordt door gegeven in, maar het idee lijkt op.</span><span class="sxs-lookup"><span data-stu-id="2d670-149">This is not splatting because I'm passing the whole array in, but the idea is similar.</span></span>

## <a name="advanced-formatting"></a><span data-ttu-id="2d670-150">Geavanceerde opmaak</span><span class="sxs-lookup"><span data-stu-id="2d670-150">Advanced formatting</span></span>

<span data-ttu-id="2d670-151">Ik noem dit opzettelijk van .NET, omdat er al een groot aantal opmaak opties is [gedocumenteerd][] .</span><span class="sxs-lookup"><span data-stu-id="2d670-151">I intentionally called these out as coming from .NET because there are lots of formatting options already well [documented][] on it.</span></span> <span data-ttu-id="2d670-152">Er zijn ingebouwde manieren om verschillende gegevens typen op te maken.</span><span class="sxs-lookup"><span data-stu-id="2d670-152">There are built in ways to format various data types.</span></span>

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

<span data-ttu-id="2d670-153">Ik ga er niet mee aan de slag, maar ik wil graag weten dat dit een zeer krachtige indelings engine is als u dat nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="2d670-153">I'm not going to go into them but I just wanted to let you know that this is a very powerful formatting engine if you need it.</span></span>

## <a name="joining-strings"></a><span data-ttu-id="2d670-154">Teken reeksen samen voegen</span><span class="sxs-lookup"><span data-stu-id="2d670-154">Joining strings</span></span>

<span data-ttu-id="2d670-155">Soms wilt u eigenlijk een lijst met waarden samen voegen.</span><span class="sxs-lookup"><span data-stu-id="2d670-155">Sometimes you actually do want to concatenate a list of values together.</span></span> <span data-ttu-id="2d670-156">Er is een `-join` operator die u voor u kan doen.</span><span class="sxs-lookup"><span data-stu-id="2d670-156">There's a `-join` operator that can do that for you.</span></span> <span data-ttu-id="2d670-157">U kunt zelfs een teken opgeven om tussen de teken reeksen te koppelen.</span><span class="sxs-lookup"><span data-stu-id="2d670-157">It even lets you specify a character to join between the strings.</span></span>

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

<span data-ttu-id="2d670-158">Als u een `-join` aantal teken reeksen zonder scheidings teken wilt, moet u een lege teken reeks opgeven `''` .</span><span class="sxs-lookup"><span data-stu-id="2d670-158">If you want to `-join` some strings without a separator, you need to specify an empty string `''`.</span></span>
<span data-ttu-id="2d670-159">Maar als dat niet het geval is, is er een snellere optie.</span><span class="sxs-lookup"><span data-stu-id="2d670-159">But if that is all you need, there's a faster option.</span></span>

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

<span data-ttu-id="2d670-160">Het is ook een goed idee dat u ook `-split` teken reeksen kunt.</span><span class="sxs-lookup"><span data-stu-id="2d670-160">It's also worth pointing out that you can also `-split` strings too.</span></span>

## <a name="join-path"></a><span data-ttu-id="2d670-161">Join-Path</span><span class="sxs-lookup"><span data-stu-id="2d670-161">Join-Path</span></span>

<span data-ttu-id="2d670-162">Dit wordt vaak gezien als een fantastische cmdlet voor het maken van een bestandspad.</span><span class="sxs-lookup"><span data-stu-id="2d670-162">This is often overlooked but a great cmdlet for building a file path.</span></span>

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

<span data-ttu-id="2d670-163">Het fantastisch is dat de backslashes correct worden uitgevoerd wanneer de waarden samen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="2d670-163">The great thing about this is it works out the backslashes correctly when it puts the values together.</span></span> <span data-ttu-id="2d670-164">Dit is vooral belang rijk als u waarden opneemt van gebruikers of configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="2d670-164">This is especially important if you are taking values from users or config files.</span></span>

<span data-ttu-id="2d670-165">Dit gaat ook goed met `Split-Path` en `Test-Path` .</span><span class="sxs-lookup"><span data-stu-id="2d670-165">This also goes well with `Split-Path` and `Test-Path`.</span></span> <span data-ttu-id="2d670-166">Ik vind deze ook in mijn post over het [lezen en opslaan van bestanden][].</span><span class="sxs-lookup"><span data-stu-id="2d670-166">I also cover these in my post about [reading and saving to files][].</span></span>

## <a name="strings-are-arrays"></a><span data-ttu-id="2d670-167">Teken reeksen zijn matrices</span><span class="sxs-lookup"><span data-stu-id="2d670-167">Strings are arrays</span></span>

<span data-ttu-id="2d670-168">Ik moet hier teken reeksen toevoegen voordat ik ga aan.</span><span class="sxs-lookup"><span data-stu-id="2d670-168">I do need to mention adding strings here before I go on.</span></span> <span data-ttu-id="2d670-169">Houd er rekening mee dat een teken reeks alleen uit een matrix met tekens bestaat.</span><span class="sxs-lookup"><span data-stu-id="2d670-169">Remember that a string is just an array of characters.</span></span> <span data-ttu-id="2d670-170">Wanneer u meerdere teken reeksen samen voegen, wordt elke keer een nieuwe matrix gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2d670-170">When you add multiple strings together, a new array is created each time.</span></span>

<span data-ttu-id="2d670-171">Bekijk dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="2d670-171">Look at this example:</span></span>

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

<span data-ttu-id="2d670-172">Het lijkt zeer eenvoudig, maar wat u niet ziet, is dat telkens wanneer een teken reeks wordt toegevoegd aan `$message` dat er een hele nieuwe teken reeks wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2d670-172">It looks very basic but what you don't see is that each time a string is added to `$message` that a whole new string is created.</span></span> <span data-ttu-id="2d670-173">Er wordt geheugen toegewezen, gegevens worden gekopieerd en de oude wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d670-173">Memory gets allocated, data gets copied and the old one is discarded.</span></span>
<span data-ttu-id="2d670-174">Geen grote deal wanneer deze slechts een paar keer wordt gedaan, maar een lus zoals dit zou het probleem werkelijk weer geven.</span><span class="sxs-lookup"><span data-stu-id="2d670-174">Not a big deal when it's only done a few times, but a loop like this would really expose the issue.</span></span>

### <a name="stringbuilder"></a><span data-ttu-id="2d670-175">String</span><span class="sxs-lookup"><span data-stu-id="2d670-175">StringBuilder</span></span>

<span data-ttu-id="2d670-176">String Builder is ook populair bij het bouwen van grote teken reeksen uit veel kleinere teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="2d670-176">StringBuilder is also very popular for building large strings from lots of smaller strings.</span></span> <span data-ttu-id="2d670-177">De reden hiervoor is dat alle teken reeksen die u toevoegt alleen worden verzameld en aan het einde worden samengevoegd wanneer u de waarde ophaalt.</span><span class="sxs-lookup"><span data-stu-id="2d670-177">The reason why is because it just collects all the strings you add to it and only concatenates all of them at the end when you retrieve the value.</span></span>

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

<span data-ttu-id="2d670-178">Nu is dit iets wat ik aan .NET heb voor.</span><span class="sxs-lookup"><span data-stu-id="2d670-178">Again, this is something that I'm reaching out to .NET for.</span></span> <span data-ttu-id="2d670-179">Ik gebruik het niet vaak meer, maar het is wel goed om te weten dat het daar is.</span><span class="sxs-lookup"><span data-stu-id="2d670-179">I don't use it often anymore but it's good to know it's there.</span></span>

## <a name="delineation-with-braces"></a><span data-ttu-id="2d670-180">Conto uren met accolades</span><span class="sxs-lookup"><span data-stu-id="2d670-180">Delineation with braces</span></span>

<span data-ttu-id="2d670-181">Dit wordt gebruikt voor het samen voegen van achtervoegsels in de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2d670-181">This is used for suffix concatenation within the string.</span></span> <span data-ttu-id="2d670-182">Soms heeft uw variabele geen schone woord grens.</span><span class="sxs-lookup"><span data-stu-id="2d670-182">Sometimes your variable doesn't have a clean word boundary.</span></span>

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

<span data-ttu-id="2d670-183">Hartelijk dank dat u [real_parbold][] voor dat abonnement.</span><span class="sxs-lookup"><span data-stu-id="2d670-183">Thank you [/u/real_parbold][] for that one.</span></span>

<span data-ttu-id="2d670-184">Dit is een alternatief voor deze methode:</span><span class="sxs-lookup"><span data-stu-id="2d670-184">Here is an alternate to this approach:</span></span>

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

<span data-ttu-id="2d670-185">Ik gebruik deze teken reeks voor Format teren, maar dit is handig om te weten wat het geval is in de vrije vorm.</span><span class="sxs-lookup"><span data-stu-id="2d670-185">I personally use format string for this, but this is good to know incase you see it in the wild.</span></span>

## <a name="find-and-replace-tokens"></a><span data-ttu-id="2d670-186">Tokens zoeken en vervangen</span><span class="sxs-lookup"><span data-stu-id="2d670-186">Find and replace tokens</span></span>

<span data-ttu-id="2d670-187">Hoewel de meeste van deze functies uw eigen oplossing niet meer nodig hebben, zijn er situaties waarin u mogelijk grote sjabloon bestanden hebt waar u teken reeksen in wilt vervangen.</span><span class="sxs-lookup"><span data-stu-id="2d670-187">While most of these features limit your need to roll your own solution, there are times where you may have large template files where you want to replace strings inside.</span></span>

<span data-ttu-id="2d670-188">We gaan ervan uit dat u een sjabloon hebt opgehaald uit een bestand met veel tekst.</span><span class="sxs-lookup"><span data-stu-id="2d670-188">Let us assume you pulled in a template from a file that has a lot of text.</span></span>

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

<span data-ttu-id="2d670-189">Het kan zijn dat u veel tokens kunt vervangen.</span><span class="sxs-lookup"><span data-stu-id="2d670-189">You may have lots of tokens to replace.</span></span> <span data-ttu-id="2d670-190">De truc is het gebruik van een zeer uniek token dat gemakkelijk te vinden is en te vervangen.</span><span class="sxs-lookup"><span data-stu-id="2d670-190">The trick is to use a very distinct token that is easy to find and replace.</span></span> <span data-ttu-id="2d670-191">Ik gebruik aan beide uiteinden een speciaal teken om het te onderscheiden.</span><span class="sxs-lookup"><span data-stu-id="2d670-191">I tend to use a special character at both ends to help distinguish it.</span></span>

<span data-ttu-id="2d670-192">Ik heb onlangs een nieuwe manier gevonden om dit te benaderen.</span><span class="sxs-lookup"><span data-stu-id="2d670-192">I recently found a new way to approach this.</span></span> <span data-ttu-id="2d670-193">Ik heb besloten deze sectie hier te laten staan, omdat dit een patroon is dat vaak wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2d670-193">I decided to leave this section in here because this is a pattern that is commonly used.</span></span>

### <a name="replace-multiple-tokens"></a><span data-ttu-id="2d670-194">Meerdere tokens vervangen</span><span class="sxs-lookup"><span data-stu-id="2d670-194">Replace multiple tokens</span></span>

<span data-ttu-id="2d670-195">Wanneer ik een lijst met tokens heb die ik moet vervangen, doe ik een meer algemene benadering.</span><span class="sxs-lookup"><span data-stu-id="2d670-195">When I have a list of tokens that I need to replace, I take a more generic approach.</span></span> <span data-ttu-id="2d670-196">Ik plaats deze in een hashtabel en herhaal deze om de vervangen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2d670-196">I would place them in a hashtable and iterate over them to do the replace.</span></span>

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

<span data-ttu-id="2d670-197">Deze tokens kunnen, indien nodig, worden geladen vanuit JSON of CSV.</span><span class="sxs-lookup"><span data-stu-id="2d670-197">Those tokens could be loaded from JSON or CSV if needed.</span></span>

### <a name="executioncontext-expandstring"></a><span data-ttu-id="2d670-198">ExecutionContext ExpandString</span><span class="sxs-lookup"><span data-stu-id="2d670-198">ExecutionContext ExpandString</span></span>

<span data-ttu-id="2d670-199">Er is een slimme manier om een vervangings teken reeks te definiëren met enkele aanhalings tekens en de variabelen later te verg Roten.</span><span class="sxs-lookup"><span data-stu-id="2d670-199">There's a clever way to define a substitution string with single quotes and expand the variables later.</span></span> <span data-ttu-id="2d670-200">Bekijk dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="2d670-200">Look at this example:</span></span>

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

<span data-ttu-id="2d670-201">De aanroep `.InvokeCommand.ExpandString` van op de huidige uitvoerings context maakt gebruik van de variabelen in het huidige bereik voor vervanging.</span><span class="sxs-lookup"><span data-stu-id="2d670-201">The call to `.InvokeCommand.ExpandString` on the current execution context uses the variables in the current scope for substitution.</span></span> <span data-ttu-id="2d670-202">De belangrijkste dingen zijn dat de `$message` kan worden gedefinieerd in een vroeg stadium voordat de variabelen nog bestaan.</span><span class="sxs-lookup"><span data-stu-id="2d670-202">The key thing here is that the `$message` can be defined very early before the variables even exist.</span></span>

<span data-ttu-id="2d670-203">Als we deze alleen maar een beetje uitvouwen, kunnen we deze vervanging uitvoeren op wih verschillende waarden.</span><span class="sxs-lookup"><span data-stu-id="2d670-203">If we expand on that just a little bit, we can perform this substitution over and over wih different values.</span></span>

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

<span data-ttu-id="2d670-204">Om aan dit idee te blijven. u kunt dit doen door een grote e-mail sjabloon te importeren uit een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="2d670-204">To keep going on this idea; you could be importing a large email template from a text file to do this.</span></span> <span data-ttu-id="2d670-205">Ik ben Kraus voor deze [suggestie][]te [markeren][] .</span><span class="sxs-lookup"><span data-stu-id="2d670-205">I have to thank [Mark Kraus][] for this [suggestion][].</span></span>

## <a name="whatever-works-the-best-for-you"></a><span data-ttu-id="2d670-206">Wat voor u het beste werkt</span><span class="sxs-lookup"><span data-stu-id="2d670-206">Whatever works the best for you</span></span>

<span data-ttu-id="2d670-207">Ik ben een ventilator van de notatie teken reeks.</span><span class="sxs-lookup"><span data-stu-id="2d670-207">I'm a fan of the format string approach.</span></span> <span data-ttu-id="2d670-208">Ik wil dit niet doen met de complexere teken reeksen of als er meerdere variabelen zijn.</span><span class="sxs-lookup"><span data-stu-id="2d670-208">I definitely do this with the more complicated strings or if there are multiple variables.</span></span> <span data-ttu-id="2d670-209">Op een zeer korte wijze kan ik elk van deze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2d670-209">On anything that is very short, I may use any one of these.</span></span>

## <a name="anything-else"></a><span data-ttu-id="2d670-210">Nog iets?</span><span class="sxs-lookup"><span data-stu-id="2d670-210">Anything else?</span></span>

<span data-ttu-id="2d670-211">Ik heb veel op dit terrein gedekt.</span><span class="sxs-lookup"><span data-stu-id="2d670-211">I covered a lot of ground on this one.</span></span> <span data-ttu-id="2d670-212">We hopen dat u nog iets nieuws leert.</span><span class="sxs-lookup"><span data-stu-id="2d670-212">My hope is that you walk away learning something new.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[original version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Kraus markeren]: https://get-powershellblog.blogspot.com/
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[voorstel]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[suggestion]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[bestanden lezen en opslaan]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[reading and saving to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[Noteer]: /dotnet/api/system.string.format#overloads
[documented]: /dotnet/api/system.string.format#overloads
