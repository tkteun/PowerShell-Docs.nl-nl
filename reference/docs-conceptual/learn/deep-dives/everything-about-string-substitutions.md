---
title: Alles wat u wilt weten over variabele vervanging in teken reeksen
description: Er zijn veel manieren om variabelen in teken reeksen te gebruiken om opgemaakte tekst te maken.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1e65e90ffa09b34f62bc49ad64b062d429483c33
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149822"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a>Alles wat u wilt weten over variabele vervanging in teken reeksen

Er zijn veel manieren om variabelen in teken reeksen te gebruiken. Ik roep deze vervanging van variabelen aan, maar ik Raadpleeg een wille keurig tijdstip waarop u een teken reeks wilt opmaken om waarden van variabelen op te nemen. Dit is iets wat ik vaak Zoek in nieuwe scripts.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="concatenation"></a>Samenvoeging

De eerste klasse van methoden kan worden aangeduid als samen voeging. Het is in wezen meerdere teken reeksen te maken en samen te voegen. Er is een lange geschiedenis van het gebruik van samen voeging om opgemaakte teken reeksen te maken.

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

Samen voegen werkt op OK wanneer er slechts enkele waarden kunnen worden toegevoegd. Maar dit kan ingewikkeld zijn.

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

Dit eenvoudige voor beeld is al moeilijker te lezen.

## <a name="variable-substitution"></a>Vervanging van variabelen

Power Shell heeft nog een andere optie die eenvoudiger is. U kunt de variabelen rechtstreeks in de teken reeksen opgeven.

```powershell
$message = "Hello, $first $last."
```

Het type aanhalings tekens dat u voor de teken reeks gebruikt, maakt een verschil. Een teken reeks met dubbele aanhalings tekens kan worden vervangen, maar een enkele aanhalings teken reeks niet. Het kan zijn dat u een of meer opties wilt maken.

## <a name="command-substitution"></a>Opdracht vervanging

Het kan even duren wanneer u begint met het ophalen van de waarden van eigenschappen in een teken reeks. Hier worden veel nieuwe personen in de weg staan. Eerst laten we u zien wat ze denken te werk (en bij gezichts waarde lijkt het alsof het zou).

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

U wordt verwacht om aan de slag te gaan `CreationTime` `$directory` , maar u krijgt dit in plaats daarvan `Time: c:\windows.CreationTime` als uw waarde. De reden is dat dit type vervanging alleen de basis variabele ziet. De periode wordt beschouwd als onderdeel van de teken reeks, zodat de waarde niet meer kan worden opgelost.

Dit betekent dat dit object een teken reeks als standaard waarde geeft wanneer deze in een teken reeks wordt geplaatst.
Sommige objecten geven u de type naam in plaats van een `System.Collections.Hashtable` . Iets om te kijken naar.

Met Power shell kunt u opdrachten uitvoeren binnen de teken reeks met een speciale syntaxis. Hierdoor kunnen we de eigenschappen van deze objecten ophalen en een andere opdracht uitvoeren om een waarde op te halen.

```powershell
$message = "Time: $($directory.CreationTime)"
```

Dit werkt prima voor bepaalde situaties, maar het kan net zo gekke zijn als samen voegen als u slechts een paar variabelen hebt.

### <a name="command-execution"></a>Opdracht uitvoering

U kunt opdrachten binnen een teken reeks uitvoeren. Hoewel ik deze optie heb, vind ik deze niet mooi. Het wordt snel en moeilijk geruimed om fouten op te sporen. Ik voer de opdracht uit en sla deze op in een variabele of gebruik een opmaak teken reeks.

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a>Teken reeks voor opmaak

.NET heeft een manier om teken reeksen te Format teren die ik redelijk eenvoudig kan gebruiken. Eerst laten we u de statische methode voor deze weer geven voordat u de Power shell-snelkoppeling weergeeft om hetzelfde te doen.

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

Hier vindt u de teken reeks die wordt geparseerd voor de tokens `{0}` en `{1}` vervolgens gebruikt u dat nummer om te kiezen uit de waarden die worden weer gegeven. Als u één waarde op een plek in de teken reeks wilt herhalen, kunt u het aantal waarden opnieuw gebruiken.

Hoe complexer de teken reeks, hoe meer u uit deze benadering haalt.

### <a name="format-values-as-arrays"></a>Waarden opmaken als matrices

Als uw opmaak regel te lang wordt, kunt u de waarden eerst in een matrix plaatsen.

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

Dit is niet splatting omdat de gehele matrix wordt door gegeven in, maar het idee lijkt op.

## <a name="advanced-formatting"></a>Geavanceerde opmaak

Ik noem dit opzettelijk van .NET, omdat er al een groot aantal opmaak opties is [gedocumenteerd][] . Er zijn ingebouwde manieren om verschillende gegevens typen op te maken.

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

Ik ga er niet mee aan de slag, maar ik wil graag weten dat dit een zeer krachtige indelings engine is als u dat nodig hebt.

## <a name="joining-strings"></a>Teken reeksen samen voegen

Soms wilt u eigenlijk een lijst met waarden samen voegen. Er is een `-join` operator die u voor u kan doen. U kunt zelfs een teken opgeven om tussen de teken reeksen te koppelen.

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

Als u een `-join` aantal teken reeksen zonder scheidings teken wilt, moet u een lege teken reeks opgeven `''` .
Maar als dat niet het geval is, is er een snellere optie.

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

Het is ook een goed idee dat u ook `-split` teken reeksen kunt.

## <a name="join-path"></a>Pad voor samen voegen

Dit wordt vaak gezien als een fantastische cmdlet voor het maken van een bestandspad.

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

Het fantastisch is dat de backslashes correct worden uitgevoerd wanneer de waarden samen worden geplaatst. Dit is vooral belang rijk als u waarden opneemt van gebruikers of configuratie bestanden.

Dit gaat ook goed met `Split-Path` en `Test-Path` . Ik vind deze ook in mijn post over het [lezen en opslaan van bestanden][].

## <a name="strings-are-arrays"></a>Teken reeksen zijn matrices

Ik moet hier teken reeksen toevoegen voordat ik ga aan. Houd er rekening mee dat een teken reeks alleen uit een matrix met tekens bestaat. Wanneer u meerdere teken reeksen samen voegen, wordt elke keer een nieuwe matrix gemaakt.

Bekijk dit voor beeld:

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

Het lijkt zeer eenvoudig, maar wat u niet ziet, is dat telkens wanneer een teken reeks wordt toegevoegd aan `$message` dat er een hele nieuwe teken reeks wordt gemaakt. Er wordt geheugen toegewezen, gegevens worden gekopieerd en de oude wordt verwijderd.
Geen grote deal wanneer deze slechts een paar keer wordt gedaan, maar een lus zoals dit zou het probleem werkelijk weer geven.

### <a name="stringbuilder"></a>String

String Builder is ook populair bij het bouwen van grote teken reeksen uit veel kleinere teken reeksen. De reden hiervoor is dat alle teken reeksen die u toevoegt alleen worden verzameld en aan het einde worden samengevoegd wanneer u de waarde ophaalt.

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

Nu is dit iets wat ik aan .NET heb voor. Ik gebruik het niet vaak meer, maar het is wel goed om te weten dat het daar is.

## <a name="delineation-with-braces"></a>Conto uren met accolades

Dit wordt gebruikt voor het samen voegen van achtervoegsels in de teken reeks. Soms heeft uw variabele geen schone woord grens.

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

Hartelijk dank dat u [real_parbold][] voor dat abonnement.

Dit is een alternatief voor deze methode:

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

Ik gebruik deze teken reeks voor Format teren, maar dit is handig om te weten wat het geval is in de vrije vorm.

## <a name="find-and-replace-tokens"></a>Tokens zoeken en vervangen

Hoewel de meeste van deze functies uw eigen oplossing niet meer nodig hebben, zijn er situaties waarin u mogelijk grote sjabloon bestanden hebt waar u teken reeksen in wilt vervangen.

We gaan ervan uit dat u een sjabloon hebt opgehaald uit een bestand met veel tekst.

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

Het kan zijn dat u veel tokens kunt vervangen. De truc is het gebruik van een zeer uniek token dat gemakkelijk te vinden is en te vervangen. Ik gebruik aan beide uiteinden een speciaal teken om het te onderscheiden.

Ik heb onlangs een nieuwe manier gevonden om dit te benaderen. Ik heb besloten deze sectie hier te laten staan, omdat dit een patroon is dat vaak wordt gebruikt.

### <a name="replace-multiple-tokens"></a>Meerdere tokens vervangen

Wanneer ik een lijst met tokens heb die ik moet vervangen, doe ik een meer algemene benadering. Ik plaats deze in een hashtabel en herhaal deze om de vervangen uit te voeren.

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

Deze tokens kunnen, indien nodig, worden geladen vanuit JSON of CSV.

### <a name="executioncontext-expandstring"></a>ExecutionContext ExpandString

Er is een slimme manier om een vervangings teken reeks te definiëren met enkele aanhalings tekens en de variabelen later te verg Roten. Bekijk dit voor beeld:

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

De aanroep `.InvokeCommand.ExpandString` van op de huidige uitvoerings context maakt gebruik van de variabelen in het huidige bereik voor vervanging. De belangrijkste dingen zijn dat de `$message` kan worden gedefinieerd in een vroeg stadium voordat de variabelen nog bestaan.

Als we deze alleen maar een beetje uitvouwen, kunnen we deze vervanging uitvoeren op wih verschillende waarden.

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

Om aan dit idee te blijven. u kunt dit doen door een grote e-mail sjabloon te importeren uit een tekst bestand. Ik ben Kraus voor deze [suggestie][]te [markeren][] .

## <a name="whatever-works-the-best-for-you"></a>Wat voor u het beste werkt

Ik ben een ventilator van de notatie teken reeks. Ik wil dit niet doen met de complexere teken reeksen of als er meerdere variabelen zijn. Op een zeer korte wijze kan ik elk van deze gebruiken.

## <a name="anything-else"></a>Nog iets?

Ik heb veel op dit terrein gedekt. We hopen dat u nog iets nieuws leert.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Kraus markeren]: https://get-powershellblog.blogspot.com/
[voorstel]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[bestanden lezen en opslaan]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[Noteer]: /dotnet/api/system.string.format#overloads
