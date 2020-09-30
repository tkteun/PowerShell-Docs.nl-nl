---
title: Alles wat u wilt weten over matrices
description: Matrices zijn een fundamentele taal functie van de meeste programmeer talen.
ms.date: 07/07/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 307189bf27d383159d34181eca4dac1f77792e51
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91543369"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a>Alles wat u wilt weten over matrices

[Matrices][] zijn een fundamentele taal functie van de meeste programmeer talen. Ze zijn een verzameling waarden of objecten die moeilijk te voor komen zijn. Laten we eens kijken naar matrices en alles wat ze te bieden hebben.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="what-is-an-array"></a>Wat is een matrix?

Ik ga aan de slag met een eenvoudige technische beschrijving van de arrays en hoe deze worden gebruikt door de meeste programmeer talen voordat ik de andere manieren in Power shell gebruikt om deze te gebruiken.

Een matrix is een gegevens structuur die fungeert als verzameling van meerdere items. U kunt de matrix herhalen of toegang krijgen tot afzonderlijke items met behulp van een index. De matrix wordt gemaakt als opeenvolgend geheugen waarbij elke waarde direct naast het andere wordt opgeslagen.

Ik raak aan elk van deze gegevens tijdens het bezoek.

## <a name="basic-usage"></a>Basisgebruik

Omdat matrices een van de basis functies van Power shell zijn, is er een eenvoudige syntaxis voor het werken met deze in Power shell.

### <a name="create-an-array"></a>Een matrix maken

Een lege matrix kan worden gemaakt met behulp van `@()`

```powershell
PS> $data = @()
PS> $data.count
0
```

We kunnen een matrix maken en deze met waarden seeden door ze te plaatsen in de `@()` haakjes.

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

Deze matrix heeft 4 items. Wanneer we de variabele aanroepen `$data` , zien we de lijst met onze items. Als het een matrix met teken reeksen is, krijgen we één regel per teken reeks.

We kunnen een matrix op meerdere regels declareren. In dit geval is de komma optioneel en links gelaten.

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

Ik wil graag mijn arrays declareren op meerdere regels. Het is niet alleen gemakkelijker te lezen wanneer u meerdere items hebt, maar maakt het gemakkelijker om te vergelijken met vorige versies wanneer u broncode beheer gebruikt.

#### <a name="other-syntax"></a>Andere syntaxis

Het `@()` is vaak de syntaxis voor het maken van een matrix, maar door komma's gescheiden lijsten werken het meeste tijd.

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a>Write-output voor het maken van matrices

Eén leuke truc is dat u kunt gebruiken `Write-Output` om snel teken reeksen te maken in de-console.

```powershell
$data = Write-Output Zero One Two Three
```

Dit is handig omdat u geen aanhalings tekens rond de teken reeksen hoeft te plaatsen wanneer de para meter teken reeksen accepteert. Ik zou dit nooit doen in een script, maar het is wel een redelijk spel in de console.

### <a name="accessing-items"></a>Toegang tot items

Nu u een matrix met items hebt, wilt u deze items mogelijk openen en bijwerken.

#### <a name="offset"></a>Offset

Voor toegang tot afzonderlijke items gebruiken we de haakjes `[]` met een offset waarde die begint bij 0. Zo wordt het eerste item in onze matrix opgehaald:

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

De reden waarom we hier nul voor gebruiken, is omdat het eerste item zich aan het begin van de lijst bevindt, zodat we een offset van 0 items gebruiken om ernaar te gaan. Als u naar het tweede item wilt gaan, moet u een offset van 1 gebruiken om het eerste item over te slaan.

```powershell
PS> $data[1]
One
```

Dit betekent dat het laatste item zich op offset 3 bevindt.

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a>Index

Nu kunt u zien waarom ik de waarden voor dit voor beeld heb gekozen. Ik heb dit als een offset geïntroduceerd, omdat dat echt is, maar deze offset wordt vaak aangeduid als een index. Een index die begint bij `0` . In de rest van dit artikel noemen we de offset een index.

#### <a name="special-index-tricks"></a>Speciale index slagen

In de meeste talen kunt u slechts één getal opgeven als de index en krijgt u één item terug.
Power shell is veel flexibeler. U kunt meerdere indexen tegelijk gebruiken. Als u een lijst met indexen opgeeft, kunnen we verschillende items selecteren.

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

De items worden geretourneerd op basis van de volg orde van de opgegeven indexen. Als u een index dupliceert, krijgt u dat item beide keren.

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

We kunnen een reeks getallen met de ingebouwde `..` operator opgeven.

```powershell
PS> $data[1..3]
One
Two
Three
```

Dit werkt ook in omgekeerde volg orde.

```powershell
PS> $data[3..1]
Three
Two
One
```

U kunt negatieve index waarden gebruiken om vanaf het einde te verschuiven. Dus als u het laatste item in de lijst nodig hebt, kunt u gebruiken `-1` .

```powershell
PS> $data[-1]
Three
```

Dit is een woord van voorzichtig met de `..` operator. De volg orde `0..-1` en `-1..0` evalueren van de waarden `0,-1` en `-1,0` . Het is eenvoudig om te zien en te controleren `$data[0..-1]` of alle items zouden worden opgesomd als u deze details vergeet. `$data[0..-1]` geeft u dezelfde waarde als `$data[0,-1]` door u het eerste en laatste item in de matrix te geven (en geen van de andere waarden).

#### <a name="out-of-bounds"></a>Buiten het bereik

Als u in de meeste talen probeert toegang te krijgen tot een index van een item dat zich aan het einde van de matrix bevindt, krijgt u een fout melding of een uitzonde ring. Power shell retourneert niets op de achtergrond.

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a>Kan niet indexeren naar een null-matrix

Als uw variabele is `$null` en u probeert deze te indexeren als een matrix, krijgt u een `System.Management.Automation.RuntimeException` uitzonde ring met het bericht `Cannot index into a null array` .

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

Zorg er dus voor dat uw matrices niet `$null` voordat u probeert toegang te krijgen tot elementen erin.

#### <a name="count"></a>Aantal

Matrices en andere verzamelingen hebben een eigenschap Count waarmee wordt aangegeven hoeveel items zich in de matrix bevinden.

```powershell
PS> $data.count
4
```

Power Shell 3,0 heeft een eigenschap Count aan de meeste objecten toegevoegd. u kunt één object hebben en dit moet een aantal van bevatten `1` .

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

`$null`Heeft zelfs een eigenschap Count, behalve het resultaat `0` .

```powershell
PS> $null.count
0
```

Er zijn een aantal traps die hier worden weer gegeven wanneer ik `$null` in dit artikel een controle voor of lege matrices ondervindt.

#### <a name="off-by-one-errors"></a>Niet-voor-één-fouten

Er wordt een veelvoorkomende programmeer fout gemaakt, omdat matrices beginnen bij index 0. Er kunnen op twee manieren geen fouten worden geïntroduceerd.

De eerste is namelijk door denken dat u het tweede item en de index van `2` en echt het derde item wilt gebruiken. Of u hebt vier items en u wilt het laatste item gebruiken, dus u gebruikt de telling voor toegang tot het laatste item.

```powershell
$data[ $data.count ]
```

Power shell is zo blij dat u dit kunt doen en precies aangeven welk item er op index 4 is `$null` . U moet gebruikmaken `$data.count - 1` van of de `-1` die we hiervoor hebben geleerd.

```powershell
PS> $data[ $data.count - 1 ]
Three
```

Hier kunt u de `-1` index gebruiken om het laatste element op te halen.

```powershell
PS> $data[ -1 ]
Three
```

Lee Dailey wijst ook naar me dat we kunnen gebruiken `$data.GetUpperBound(0)` om het maximum aantal indexen te verkrijgen.

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

De tweede meest voorkomende manier is om de lijst te herhalen en niet op het juiste moment te stoppen. Ik ga hier door met het gebruik van de `for` lus.

### <a name="updating-items"></a>Items bijwerken

We kunnen dezelfde index gebruiken om bestaande items in de matrix bij te werken. Dit biedt directe toegang tot het bijwerken van afzonderlijke items.

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

Als we proberen een item bij te werken dat zich in het laatste element bevindt, wordt er een `Index was outside the bounds of the array.` fout bericht weer geven.

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

Ik ga deze later opnieuw door als ik praat over hoe u een matrix groter kunt maken.

### <a name="iteration"></a>Iteratie

Op een bepaald moment moet u mogelijk de hele lijst door lopen of herhalen en een aantal acties uitvoeren voor elk item in de matrix.

#### <a name="pipeline"></a>Pijplijn

Matrices en de Power shell-pijp lijn zijn bedoeld voor elkaar. Dit is een van de eenvoudigste manieren om deze waarden te verwerken. Wanneer u een matrix doorgeeft aan een pijp lijn, wordt elk item in de matrix afzonderlijk verwerkt.

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

Als u nog niet eerder hebt gezien `$PSItem` , weet u zeker dat het hetzelfde is als `$_` . U kunt een van beide gebruiken omdat beide het huidige object in de pijp lijn vertegenwoordigen.

#### <a name="foreach-loop"></a>ForEach-lus

De `ForEach` lus werkt goed met verzamelingen. Met de syntaxis: `foreach ( <variable> in <collection> )`

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a>ForEach-methode

Ik vergeet dit maar over dit abonnement, maar het werkt goed voor eenvoudige bewerkingen. Met Power shell kunt u aanroepen `.ForEach()` voor een verzameling.

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

`.foreach()`Er wordt een para meter met een script blok gebruikt. U kunt de haakjes verwijderen en alleen het script blok opgeven.

```powershell
$data.foreach{"Item [$PSItem]"}
```

Dit is een minder bekende syntaxis, maar werkt precies hetzelfde. Deze `foreach` methode is toegevoegd in Power shell 4,0.

#### <a name="for-loop"></a>For-lus

De `for` lus wordt sterk in de meeste andere talen gebruikt, maar u ziet deze niet veel in Power shell. Wanneer u dit ziet, is dit vaak in de context van een matrix.

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

Het eerste wat we doen, initialiseren van een `$index` naar `0` . Vervolgens voegen we de voor waarde toe die `$index` kleiner moet zijn dan `$data.count` . Ten slotte geven we op dat elke keer dat ik de index moet verg Roten `1` . In dit geval `$index++` is de enige korte voor `$index = $index + 1` .

Wanneer u een lus gebruikt `for` , moet u speciale aandacht schenken aan de voor waarde. Hier gebruikt u `$index -lt $data.count` . Het is eenvoudig om de voor waarde iets verkeerd te krijgen om een fout in uw logica op te halen. Het gebruik `$index -le $data.count` of `$index -lt ($data.count - 1)` ooit is iets verkeerd. Dit kan ertoe leiden dat er te veel of te weinig items worden verwerkt. Dit is een onklassieke fout.

#### <a name="switch-loop"></a>Switch herhalen

Dit is een gemakkelijk te herspeld abonnement. Als u een matrix voor een [Switch-instructie][]opgeeft, wordt elk item in de matrix gecontroleerd.

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

Er zijn veel leuke dingen die u kunt doen met de switch-instructie. Ik heb een ander artikel dat hieraan is gekoppeld.

- [Alles wat u zou weten over de][instructie] switch-instructie switch

#### <a name="updating-values"></a>Waarden worden bijgewerkt

Als uw matrix een verzameling teken reeksen of gehele getallen (waardetypen) is, wilt u misschien de waarden in de matrix bijwerken tijdens de lus. De meeste lussen hierboven gebruiken een variabele in de lus die een kopie van de waarde bevat. Als u die variabele bijwerkt, wordt de oorspronkelijke waarde in de matrix niet bijgewerkt.

De uitzonde ring op die instructie is de `for` lus. Als u een matrix wilt bekijken en waarden hierin wilt bijwerken, `for` is de lus wat u zoekt.

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

In dit voor beeld wordt een waarde gesorteerd op index, worden enkele wijzigingen aangebracht en wordt dezelfde index vervolgens gebruikt om deze weer toe te wijzen.

## <a name="arrays-of-objects"></a>Matrices van objecten

Tot nu toe is het enige wat we in een matrix hebben geplaatst, een Waardetype, maar matrices kunnen ook objecten bevatten.

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

Veel cmdlets retour neren verzamelingen objecten als matrices wanneer u deze toewijst aan een variabele.

```powershell
$processList = Get-Process
```

Alle basis functies die al eerder zijn besproken, zijn nog steeds van toepassing op arrays van objecten met enkele details die u moet aanwijzen.

### <a name="accessing-properties"></a>Eigenschappen openen

We kunnen een index gebruiken om toegang te krijgen tot een afzonderlijk item in een verzameling, net als bij waardetypen.

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

We kunnen eigenschappen rechtstreeks openen en bijwerken.

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a>Matrix eigenschappen

Normaal gesp roken moet u de hele lijst als zodanig opsommen voor toegang tot alle eigenschappen:

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

Of met behulp van de- `Select-Object -ExpandProperty` cmdlet.

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

Maar Power shell biedt ons de mogelijkheid om rechtstreeks aan te vragen `LastName` . In Power shell worden alle bestanden voor ons opgesomd en wordt een schone lijst weer gegeven.

```powershell
PS> $data.LastName

Marquette
Doe
```

De inventarisatie wordt nog steeds uitgevoerd, maar de complexiteit ligt daar niet meer te zien.

### <a name="where-object-filtering"></a>Where-object filtering

Hier kan worden `Where-Object` gefilterd en geselecteerd wat we uit de matrix willen zien op basis van de eigenschappen van het object.

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

We kunnen dezelfde query schrijven om de `FirstName` Zoek resultaten te vinden.

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a>WHERE ()

Matrices hebben een `Where()` methode waarmee u een `scriptblock` voor het filter kunt opgeven.

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

Deze functie is toegevoegd aan Power Shell 4,0.

### <a name="updating-objects-in-loops"></a>Objecten in lussen bijwerken

Met waardetypen kan de matrix alleen worden bijgewerkt met behulp van een for-lus, omdat de index moet worden gebruikt om de waarde te vervangen. We hebben meer opties met objecten omdat ze verwijzen naar typen. Hier volgt een kort voor beeld:

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

Deze lus doorloopt elk object in de `$data` matrix. Omdat objecten verwijzen naar typen, `$person` verwijst de variabele naar exact hetzelfde object dat zich in de matrix bevindt. Als er updates worden uitgevoerd op de eigenschappen, wordt het origineel bijgewerkt.

U kunt het hele object niet op deze manier vervangen. Als u een nieuw object aan de variabele probeert toe te wijzen `$person` , werkt u de verwijzing naar de variabele bij naar iets anders dat niet langer naar het oorspronkelijke object in de matrix verwijst. Dit werkt niet zoals verwacht:

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a>Operators

De Opera tors in Power shell werken ook aan matrices. Sommige van deze werken iets anders.

### <a name="-join"></a>-lid worden

De `-join` operator is het meest duidelijkst, dus we bekijken deze eerst. Ik vind de `-join` operator leuk en gebruik deze regel matig. Hiermee worden alle elementen in de matrix samengevoegd met het teken of de teken reeks die u opgeeft.

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

Een van de functies die ik op de `-join` operator bevindt, is dat deze afzonderlijke items verwerkt.

```powershell
PS> 1 -join '-'
1
```

Ik gebruik dit in logboek registratie en uitgebreide berichten.

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a>-$array toevoegen

Hier volgt een slimme truc die Lee Dailey naar mij wijst. Als u alles zonder scheidings teken wilt gebruiken, in plaats van dit te doen:

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

U kunt `-join` met de matrix gebruiken als de para meter zonder voor voegsel. Bekijk dit voor beeld om te zien dat ik over het praten ben.

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a>-vervangen en-splitsen

De andere opera tors zoals `-replace` en worden `-split` uitgevoerd op elk item in de matrix. Ik zeg dat ik ooit deze manier heb gebruikt, maar dit is een voor beeld.

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a>-contains

Met de `-contains` operator kunt u een matrix met waarden controleren om te zien of deze een opgegeven waarde bevat.

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a>-in

Wanneer u één waarde hebt die u wilt verifiëren, kunt u een van de volgende waarden gebruiken `-in` . De waarde is links en de matrix aan de rechter kant van de operator.

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

Dit kan duur krijgen als de lijst groot is. Ik gebruik vaak een regex-patroon als ik meer dan een paar waarden Controleer.

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a>-EQ en-ne

Gelijkheid en matrices kunnen gecompliceerd zijn. Wanneer de matrix aan de linkerkant wordt geplaatst, wordt elk item vergeleken. In plaats van `True` te retour neren, wordt het object geretourneerd dat overeenkomt.

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

Wanneer u de `-ne` operator gebruikt, worden alle waarden opgehaald die niet gelijk zijn aan onze waarde.

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

Wanneer u dit gebruikt in een `if()` -instructie, is een waarde die wordt geretourneerd een `True` waarde. Als er geen waarde wordt geretourneerd, is dit een `False` waarde. Beide volgende instructies evalueren naar `True` .

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

Ik ga dit op een moment opnieuw door met het bespreken van testen `$null` .

### <a name="-match"></a>-match

De `-match` operator probeert elk item in de verzameling te koppelen.

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

Wanneer u `-match` met één waarde gebruikt, wordt een speciale variabele `$Matches` gevuld met overeenkomende gegevens. Dit is niet het geval wanneer een matrix op deze manier wordt verwerkt.

We kunnen dezelfde benadering uitvoeren met `Select-String` .

```powershell
$servers | Select-String SQL
```

Ik kijk eens naar `Select-String` `-match` en de `$matches` variabele in een ander bericht heet [de vele manieren om regex te gebruiken][].

### <a name="null-or-empty"></a>$null of leeg

Testen van `$null` of lege matrices kunnen lastig zijn. Dit zijn de algemene traps met matrices.

In een oogopslag lijkt het alsof deze instructie werkt.

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

Maar ik heb zojuist overgegaan hoe `-eq` elk item in de matrix wordt gecontroleerd. We kunnen dus een matrix van verschillende items hebben met één $null waarde en deze evalueren `$true`

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

Daarom is het een best practice om de `$null` aan de linkerkant van de operator te plaatsen. Dit scenario maakt dan een niet-probleem.

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

Een `$null` matrix is niet hetzelfde als een lege matrix. Als u weet dat u een matrix hebt, controleert u het aantal objecten hierin. Als de matrix is `$null` , is het aantal `0` .

```powershell
if ( $array.count -gt 0 )
{
    'Array isn't empty'
}
```

Er is nog een trap die u hier kunt bekijken. U kunt ook gebruiken `count` Als u één object hebt, tenzij dat object een is `PSCustomObject` . Dit is een fout die wordt opgelost in Power shell 6,1.
Dat is goed nieuws, maar een groot aantal mensen bevindt zich nog steeds op 5,1 en moet erop letten.

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

Als u nog steeds in Power shell 5,1 bent, kunt u het object in een matrix inpakken voordat u het aantal controleert om een nauw keurig aantal te bepalen.

```powershell
if ( @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

Als u het veilig wilt afspelen, controleert u op `$null` en controleert u de telling.

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

### <a name="all--eq"></a>All-EQ

Ik zag onlangs dat iemand [een vraag stelt om te controleren of elke waarde in een matrix overeenkomt met een bepaalde waarde][].
Reddit User **/u/bis** had deze slimme [oplossing][] die op onjuiste waarden controleert en vervolgens het resultaat spiegelt.

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a>Toevoegen aan matrices

Op dit moment begint u met het toevoegen van items aan een matrix. Het snelle antwoord is dat u dat niet kunt. Een matrix is een vaste grootte in het geheugen. Als u het item wilt verg Roten of er één aan wilt toevoegen, moet u een nieuwe matrix maken en alle waarden van de oude matrix kopiëren. Dit klinkt als veel werk, maar in Power shell wordt de complexiteit van het maken van de nieuwe matrix echter verborgen. Power shell implementeert de operator voor optellen ( `+` ) voor matrices.

> [!NOTE]
> Power shell implementeert geen aftrekkings bewerking. Als u een flexibel alternatief voor een matrix wilt, moet u een [Gene riek `List` ](#generic-list) object gebruiken.

### <a name="array-addition"></a>Matrix toevoegen

We kunnen de operator voor toevoeging met matrices gebruiken om een nieuwe matrix te maken. Deze twee matrices hebben daarom de volgende:

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

We kunnen ze samen toevoegen om een nieuwe matrix te krijgen.

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a>Plus teken is gelijk aan + =

We kunnen een nieuwe matrix maken en daar een item aan toevoegen:

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

Houd er rekening mee dat elke keer `+=` dat u het dupliceert en een nieuwe matrix maakt. Dit is geen probleem voor kleine gegevens sets, maar het wordt zeer slecht geschaald.

### <a name="pipeline-assignment"></a>Pijplijn toewijzing

U kunt de resultaten van een pijp lijn toewijzen aan een variabele. Het is een matrix als deze meerdere items bevat.

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

Normaal gesp roken is het gebruik van de pijp lijn van de typische Power shell-One-Lines. We kunnen gebruikmaken van de pijp lijn met `foreach()` instructies en andere lussen. In plaats van items aan een matrix toe te voegen, kunnen we items naar de pijp lijn verplaatsen.

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a>Matrix typen

Standaard wordt een matrix in Power shell gemaakt als een `[PSObject[]]` type. Dit kan een wille keurig type object of waarde bevatten. Dit werkt omdat alles wordt overgenomen van het `PSObject` type.

### <a name="strongly-typed-arrays"></a>Sterk getypeerde matrices

U kunt een matrix van elk type maken met een vergelijk bare syntaxis. Wanneer u een sterk getypeerde matrix maakt, kan deze alleen waarden of objecten van het opgegeven type bevatten.

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a>List

Het toevoegen van items aan een matrix is een van de grootste beperkingen, maar er zijn een aantal andere verzamelingen die we kunnen omzetten om dit probleem op te lossen.

De `ArrayList` is doorgaans een van de eerste dingen die we denken wanneer we een matrix nodig hebben die sneller werkt met. Het fungeert als een object matrix op elke locatie waar we deze nodig hebben, maar Hiermee wordt het snel toevoegen van items.

Hier wordt uitgelegd hoe we een `ArrayList` items maken en hieraan toevoegen.

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

Er wordt naar .NET gebeld om dit type op te halen. In dit geval gebruiken we de standaard-constructor om deze te maken. Vervolgens roept de `Add` methode aan om een item toe te voegen.

De reden `[void]` dat ik aan het begin van de regel bevindt, is om de retour code te onderdrukken. In sommige .NET-aanroepen wordt dit gedaan en kan onverwachte uitvoer worden gemaakt.

Als de enige gegevens die u in uw matrix hebt, teken reeksen zijn, bekijkt u ook de gebruik van [String Builder][]. Het is bijna hetzelfde, maar heeft een aantal methoden die alleen worden behandeld met teken reeksen. De `StringBuilder` is speciaal ontworpen voor prestaties.

Het is gebruikelijk om te zien hoe mensen `ArrayList` van matrices worden verplaatst. Maar het is afkomstig van een keer dat C# geen algemene ondersteuning heeft. De `ArrayList` is afgeschaft in ondersteuning voor de algemene `List[]`

### <a name="generic-list"></a>Algemene lijst

Een Gene riek type is een speciaal type in C# dat een gegeneraliseerde klasse definieert en de gebruiker specificeert de gegevens typen die worden gebruikt wanneer ze worden gemaakt. Als u dus een lijst met getallen of teken reeksen wilt, definieert u dat u een lijst `int` of `string` typen wilt.

Hier kunt u een lijst maken voor teken reeksen.

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

Of een lijst met getallen.

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

We kunnen een bestaande matrix Converteren naar een lijst zoals deze zonder eerst het object te maken:

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

We kunnen de syntaxis verkorten met de `using namespace` instructie in Power shell 5 en nieuwer. De `using` instructie moet de eerste regel van het script zijn. Als u een naam ruimte declareert, kunt u met Power shell de gegevens typen uitschakelen wanneer u ernaar verwijst.

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

Dit maakt het `List` veel handiger.

U hebt een vergelijk bare `Add` methode voor u. In tegens telling tot de array List is er geen retour waarde voor de `Add` methode `void` .

```powershell
$myList.Add(10)
```

En we hebben nog steeds toegang tot de elementen zoals andere matrices.

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a>Lijst [PSObject]

U kunt een lijst van elk type hebben, maar wanneer u het type objecten niet weet, kunt u deze gebruiken `[List[PSObject]]` om ze te bevatten.

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a>Remove()

De `ArrayList` en de algemene `List[]` ondersteuning voor het verwijderen van items uit de verzameling.

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

Bij het werken met waardetypen wordt het eerste item uit de lijst verwijderd. U kunt deze opnieuw aanroepen om deze waarde te blijven verwijderen. Als u referentie typen hebt, moet u het object opgeven dat u wilt verwijderen.

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

De methode Remove wordt geretourneerd `true` als het item in de verzameling kan worden gevonden en verwijderd.

### <a name="more-collections"></a>Meer verzamelingen

Er zijn veel andere verzamelingen die kunnen worden gebruikt, maar dit zijn de goede algemene matrix vervangingen.
Als u meer wilt weten [over deze opties](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) , gaat u naar deze lessen die [Kraus markeren](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) .

## <a name="other-nuances"></a>Andere nuances

Nu u alle belang rijke functies hebt behandeld, zijn er nog enkele dingen die ik wilde vermelden voordat ik dit inpakt.

### <a name="pre-sized-arrays"></a>Pregrote matrices

Ik heb genoteerd dat u de grootte van een matrix niet kunt wijzigen nadat deze is gemaakt. We kunnen een matrix maken van een vooraf bepaalde grootte door deze aan te roepen met de `new($size)` constructor.

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a>Matrices vermenigvuldigen

Een interessante truc is dat u een matrix kunt vermenigvuldigen met een geheel getal.

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

### <a name="initialize-with-0"></a>Initialiseren met 0

Een veelvoorkomend scenario is dat u een matrix met alle nullen wilt maken. Als u alleen gehele getallen wilt hebben, wordt een sterk getypeerde matrix van gehele getallen standaard ingesteld op nullen.

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

We kunnen de verwerkings truc ook gebruiken om dit te doen.

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

Het mooie van de vermenigvuldigings truc is dat u een wille keurige waarde kunt gebruiken. Als u `255` de standaard waarde liever hebt, is dit een goede manier om dit te doen.

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a>Geneste matrices

Een matrix binnen een matrix wordt een geneste matrix genoemd. Ik gebruik deze niet veel in Power shell, maar ik heb ze meer in andere talen gebruikt. U kunt een matrix met matrices gebruiken als uw gegevens in een raster overeenkomen met het patroon.

Hier volgen twee manieren waarop we een tweedimensionale matrix kunnen maken.

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

De komma is zeer belang rijk in die voor beelden. Ik heb een eerder voor beeld van een normale matrix op meerdere regels genoteerd, waar de komma optioneel was. Dat is niet het geval met een multi-dimensionale matrix.

De manier waarop we de index notatie gebruiken, verandert nu iets dat we een geneste matrix hebben. Op basis van het `$data` bovenstaande is dit hoe we de waarde 3 benaderen.

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

Voeg een set met haakjes toe voor elk niveau van matrix Nesting. De eerste set met haken is voor de buitenste matrix en vervolgens werkt u vanuit deze werk wijze.

### <a name="write-output--noenumerate"></a>Write-output-opsomming

Power shell kan de terugloop of het opsommen van matrices opvangen. Dit is een kern aspect van de manier waarop Power shell de pijp lijn gebruikt, maar er zijn tijden die u niet wilt dat.

Ik pipet objecten vaak om `Get-Member` meer te weten te komen over hen. Wanneer ik een matrix naar het object Pipet, wordt deze teruggestuurd en wordt Get-member de leden van de matrix en niet de daad werkelijke matrix weer gegeven.

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

U kunt gebruiken om te voor komen dat de matrix op te slaan `Write-Object -NoEnumerate` .

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

Ik heb een tweede manier om meer van een hack (en probeer Hacks zoals dit te voor komen). U kunt een komma vóór de matrix plaatsen voordat u deze pipet.

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a>Een matrix retour neren

Dit ontpakken van matrices gebeurt ook wanneer u waarden uit een functie uitvoert of retourneert. U kunt nog steeds een matrix ophalen als u de uitvoer toewijst aan een variabele, zodat dit niet vaak een probleem is.

De catch is dat u een nieuwe matrix hebt. Als het probleem zich ooit voordoet, kunt u `Write-Output -NoEnumerate $array` het gebruiken of omzeilen `return ,$array` .

## <a name="anything-else"></a>Nog iets?

Ik weet dat dit allemaal veel tijd in beslag neemt. We hopen dat u een deel van dit artikel leert elke keer dat u het leest en dat het gedurende lange tijd een goede referentie voor u is. Als u ontdekt dat dit nuttig is, kunt u het delen met anderen waarvan u denkt dat ze de waarde van de app kunnen halen.

Hier raden we u aan een vergelijk bare post te bekijken die ik heb geschreven over [hashtabellen][].

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Matrices]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch-instructie]: everything-about-switch.md
[hashtabellen]: everything-about-hashtable.md
[De vele manieren om regex te gebruiken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[controleren of elke waarde in een matrix overeenkomt met een bepaalde waarde]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[oplossen]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[String]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
