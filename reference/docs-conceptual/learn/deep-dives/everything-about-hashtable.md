---
title: Alles wat u wilt weten over hashtabellen
description: Hashtabellen zijn heel belang rijk in Power shell, zodat het goed is om een duidelijker beeld te krijgen.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: a471c0fe2c48820d6c1d152e2850b1e431d28f23
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101686063"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a>Alles wat u wilt weten over hashtabellen

Ik wil een stap terugnemen en praten over [hashtabellen][]. Ik gebruik deze nu altijd. Ik ben van de afgelopen avond een studie over de gebruikers groep, en ik heb een andere uitverwar ring gehad over hen. Hashtabellen zijn heel belang rijk in Power shell, zodat het goed is om een duidelijker beeld te krijgen.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="hashtable-as-a-collection-of-things"></a>Hashtabel als een verzameling dingen

Ik wil dat u eerst een **hashtabel** als een verzameling in de traditionele definitie van een hashtabel ziet. Deze definitie biedt u een basis kennis van hoe ze werken wanneer ze later worden gebruikt voor meer geavanceerde dingen. Het overs laan van deze inzichten is vaak een bron van Verwar ring.

## <a name="what-is-an-array"></a>Wat is een matrix?

Voordat ik naar wat een **hashtabel** gaat, moet ik eerst de [matrixen][] vermelden. Voor het doel van deze discussie is een matrix een lijst of verzameling waarden of objecten.

```powershell
$array = @(1,2,3,5,7,11)
```

Zodra u uw items in een matrix hebt, kunt u gebruiken `foreach` om de lijst te herhalen of een index te gebruiken voor toegang tot afzonderlijke elementen in de matrix.

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

Op dezelfde manier kunt u ook waarden bijwerken met behulp van een index.

```powershell
$array[2] = 13
```

Ik heb gewoon het Opper vlak op matrices kwijt, maar dat zou ze in de juiste context moeten zetten terwijl ik op hashtabellen ga.

## <a name="what-is-a-hashtable"></a>Wat is een hashtabel?

Ik ga aan de slag met een eenvoudige technische beschrijving van wat hashtabellen in het algemeen zinvol zijn, voordat ik de andere manieren in Power shell gebruik.

Een hashtabel is een gegevens structuur die vergelijkbaar is met een matrix, behalve dat u elke waarde (object) opslaat met behulp van een sleutel. Het is een basis sleutel/waarde-archief. Eerst maken we een lege hashtabel.

```powershell
$ageList = @{}
```

U ziet dat accolades in plaats van haakjes worden gebruikt voor het definiëren van een hashtabel. Vervolgens voegen we een item toe met behulp van een sleutel als volgt:

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

De naam van de persoon is de sleutel en de leeftijd is de waarde die ik wil opslaan.

## <a name="using-the-brackets-for-access"></a>De vier Kante haken gebruiken voor toegang

Zodra u uw waarden aan de hashtabel hebt toegevoegd, kunt u ze weer gebruiken met dezelfde sleutel (in plaats van een numerieke index zoals u voor een matrix zou gebruiken).

```powershell
$ageList['Kevin']
$ageList['Alex']
```

Wanneer ik de leeftijd van Kevin wil, gebruik ik dan de naam ervan om deze te openen. U kunt deze methode gebruiken om ook waarden toe te voegen of bij te werken in de hashtabel. Dit is net als het gebruik van de `add()` bovenstaande functie.

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

Er is een andere syntaxis die u kunt gebruiken voor toegang tot en het bijwerken van waarden die ik in een latere sectie bevindt. Als u vanuit een andere taal naar Power shell gaat, moeten deze voor beelden passen in met de manier waarop u hashtabellen al eerder hebt gebruikt.

### <a name="creating-hashtables-with-values"></a>Hashtabellen maken met waarden

Tot nu toe heb ik een lege hashtabel gemaakt voor deze voor beelden. U kunt de sleutels en waarden vooraf invullen wanneer u ze maakt.

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a>Als opzoek tabel

De werkelijke waarde van dit type van een hashtabel is dat u ze als opzoek tabel kunt gebruiken. Hier volgt een eenvoudig voor beeld.

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

In dit voor beeld geeft u een omgeving voor de `$env` variabele op en wordt de juiste server gekozen. U kunt een `switch($env){...}` voor een selectie zoals deze gebruiken, maar een hashtabel is een mooie optie.

Dit wordt nog beter wanneer u de opzoek tabel dynamisch bouwt om deze later te gebruiken. Denk dus na over het gebruik van deze aanpak wanneer u naar iets moet verwijzen. Ik denk dat dit zelfs meer zou worden weer gegeven als Power shell niet zo goed kan worden gefilterd op de pipe met `Where-Object` . Als u ooit een situatie hebt waarbij de prestaties van belang zijn, moet u rekening houden met deze aanpak.

Ik zeg niet dat het sneller is, maar wel in het geval van [prestatie][]problemen.

#### <a name="multiselection"></a>Multiselectie

Over het algemeen kunt u een hashtabel beschouwen als een sleutel/waarde-paar, waarbij u één sleutel opgeeft en één waarde ophaalt. Met Power shell kunt u een matrix met sleutels opgeven om meerdere waarden te verkrijgen.

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

In dit voor beeld gebruiken we dezelfde overeenkomende hashtabel en bieden ze drie verschillende matrix stijlen om de overeenkomsten op te halen. Dit is een verborgen edelsteen in Power shell waarmee de meeste mensen niet op de hoogte zijn.

## <a name="iterating-hashtables"></a>Hashtabellen herhalen

Omdat een hashtabel bestaat uit een verzameling sleutel-waardeparen, voert u een andere sequentie in dan die voor een matrix of een normale lijst met items.

Het eerste dat u moet nadoen, is dat als u de hashtabel bewaart, de pipe als één object beschouwt.

```powershell
PS> $ageList | Measure-Object
count : 1
```

Hoewel de `.count` eigenschap vertelt u hoeveel waarden deze bevat.

```powershell
PS> $ageList.count
2
```

U kunt dit probleem omzeilen door de `.values` eigenschap te gebruiken als u alleen de waarden hoeft op te geven.

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

Het is vaak handiger om de sleutels te inventariseren en gebruiken om toegang te krijgen tot de waarden.

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

Hier volgt een voor beeld met een `foreach(){...}` lus.

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

Elke sleutel in de hashtabel wordt door lopen en vervolgens gebruikt om toegang te krijgen tot de waarde. Dit is een algemeen patroon wanneer u met hashtabellen werkt als een verzameling.

### <a name="getenumerator"></a>GetEnumerator ()

Dit zorgt ervoor dat we de `GetEnumerator()` hashtabel kunnen herhalen.

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

De enumerator geeft u elk sleutel/waarde-paar op één na andere. Het is specifiek ontworpen voor deze use-case. Hartelijk dank dat u [Kraus markeert](https://get-PowerShellblog.blogspot.com) om dit te onthouden.

### <a name="badenumeration"></a>BadEnumeration

Een van de belang rijke details is dat u een hashtabel niet kunt wijzigen tijdens het inventariseren. Als we beginnen met het basis `$environments` voorbeeld:

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

En het instellen van elke sleutel op dezelfde server waarde mislukt.

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

Dit kan ook gebeuren, zelfs als het lijkt alsof het ook goed is:

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

De truc van deze situatie is het klonen van de sleutels voordat u de inventarisatie uitvoert.

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a>Hashtabel als een verzameling eigenschappen

Tot nu toe was het type van de objecten die we in onze hashtabel hebben geplaatst, allemaal hetzelfde type object. Ik heb in al deze voor beelden leeftijden gebruikt en de sleutel is de naam van de persoon. Dit is een uitstekende manier om ernaar te kijken wanneer uw verzameling objecten elk een naam heeft. Een andere gang bare manier om hashtabellen te gebruiken in Power shell is een verzameling eigenschappen te bewaren waarbij de sleutel de naam van de eigenschap is. Ik Step Into dat idee in dit volgende voor beeld.

### <a name="property-based-access"></a>Toegang op basis van eigenschappen

Het gebruik van op eigenschappen gebaseerde toegang wijzigt de dynamiek van hashtabellen en hoe u deze kunt gebruiken in Power shell. Hieronder ziet u een voor beeld van de bovenstaande sleutels als eigenschappen.

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

Net als in de bovenstaande voor beelden voegt u in dit voor beeld deze sleutels toe als ze al in de hashtabel aanwezig zijn. Afhankelijk van hoe u uw sleutels hebt gedefinieerd en wat uw waarden zijn, is dit een beetje vreemde of een perfecte keuze. Het voor beeld van de leeftijds lijst is tot dit punt goed gewerkt. We hebben een nieuw voor beeld nodig om aan de slag te gaan.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

En we kunnen op deze manier kenmerken toevoegen en er toegang toe krijgen `$person` .

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

Het enige wat een plotselinge hash van deze hashtabel is, lijkt een object te zijn. Er is nog steeds een verzameling dingen, dus alle bovenstaande voor beelden zijn nog steeds van toepassing. We benadert dit gewoon vanuit een ander weergave punt.

### <a name="checking-for-keys-and-values"></a>Controleren op sleutels en waarden

In de meeste gevallen kunt u gewoon testen op de waarde, wat er ongeveer als volgt uitziet:

```powershell
if( $person.age ){...}
```

Het is eenvoudig, maar is de bron van veel fouten voor mij, omdat er een belang rijke details in mijn logica worden weer gegeven. Ik ben begonnen met het gebruik ervan om te testen of er een sleutel aanwezig was. Als de waarde is `$false` of nul, zou deze instructie `$false` onverwacht worden geretourneerd.

```powershell
if( $person.age -ne $null ){...}
```

Dit werkt rond het probleem voor nulwaarden, maar niet $null versus niet-bestaande sleutels. In de meeste gevallen hoeft u dit onderscheid niet te maken, maar er zijn functies voor wanneer u dat doet.

```powershell
if( $person.ContainsKey('age') ){...}
```

We hebben ook een `ContainsValue()` voor de situatie waarin u moet testen op een waarde zonder de sleutel te weten of de hele verzameling te herhalen.

### <a name="removing-and-clearing-keys"></a>Sleutels verwijderen en wissen

U kunt sleutels verwijderen met de `.Remove()` functie.

```powershell
$person.remove('age')
```

Als u een waarde toewijst, `$null` hoeft u alleen een sleutel met een waarde op te geven `$null` .

Een gemeen schappelijke manier om een hashtabel te wissen, is om deze eenvoudigweg te initialiseren naar een lege hashtabel.

```powershell
$person = @{}
```

Probeer `clear()` in plaats daarvan de functie te gebruiken.

```powershell
$person.clear()
```

Dit is een van deze gevallen waarbij het gebruik van de functie zelf-document code maakt en de bedoelingen van de code zeer helder maakt.

## <a name="all-the-fun-stuff"></a>Alle leuke dingen

### <a name="ordered-hashtables"></a>Besteld hashtabellen

Hashtabellen zijn standaard niet gerangschikt (of gesorteerd). In de traditionele context is de volg orde niet belang rijk wanneer u altijd een sleutel gebruikt om toegang te krijgen tot waarden. Mogelijk wilt u dat de eigenschappen in de volg orde blijven staan waarin u ze definieert. Gelukkig, er is een manier om dat te doen met het `ordered` sleutel woord.

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

Wanneer u de sleutels en waarden nu opsomt, blijven ze in die volg orde.

### <a name="inline-hashtables"></a>Inline-hashtabellen

Wanneer u een hashtabel op één regel definieert, kunt u de sleutel-waardeparen scheiden met een punt komma.

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

Dit kan handig zijn als u ze op de pipe maakt.

### <a name="custom-expressions-in-common-pipeline-commands"></a>Aangepaste expressies in algemene pijplijn opdrachten

Er zijn enkele cmdlets die ondersteuning bieden voor het gebruik van hashtabellen om aangepaste of berekende eigenschappen te maken. U ziet dit meestal met `Select-Object` en `Format-Table` . De hashtabellen hebben een speciale syntaxis die er als volgt uitziet wanneer deze volledig is uitgevouwen.

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

De `name` is wat de cmdlet zou labelen. Het `expression` is een script blok dat wordt uitgevoerd, waarbij `$_` de waarde van het object op de pipe is. Dit is het script in actie:

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Property name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

Ik heb dat in een variabele geplaatst, maar dit kan gemakkelijk inline worden gedefinieerd, en u kunt de kortings functie voor u verkorten `name` `n` `expression` `e` .

```powershell
$drives | Select-Object -property name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

Ik weet niet hoe lang het duurt om opdrachten uit te geven. het bevordert vaak een slecht gedrag dat daar niet aan is. Ik wil waarschijnlijk een nieuwe hashtabel maken of `pscustomobject` met alle velden en eigenschappen die ik wil gebruiken in plaats van deze benadering in scripts. Maar er is wel een groot aantal Program meren waarmee u op de hoogte zou zijn. Ik vind iets over het maken `pscustomobject` van een latere versie.

### <a name="custom-sort-expression"></a>Aangepaste Sorteer expressie

Het is eenvoudig om een verzameling te sorteren als de objecten de gegevens bevatten waarop u wilt sorteren. U kunt de gegevens toevoegen aan het object voordat u het sorteert of een aangepaste expressie maakt voor `Sort-Object` .

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

In dit voor beeld maken we een lijst met gebruikers en gebruiken we een aangepaste cmdlet om meer informatie te krijgen voor de sorteer bewerking.

#### <a name="sort-a-list-of-hashtables"></a>Een lijst met hashtabellen sorteren

Als u een lijst met hashtabellen hebt die u wilt sorteren, zult u zien dat de `Sort-Object` sleutels niet worden behandeld als eigenschappen. We kunnen een afronding krijgen met behulp van een aangepaste Sorteer expressie.

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a>Splatting hashtabellen bij cmdlets

Dit is een van mijn favoriete dingen over hashtabellen die veel mensen niet vroeg ontdekken.
Het idee is dat u in plaats van alle eigenschappen een cmdlet op één regel moet opgeven, maar u kunt ze eerst in een hashtabel inpakken. U kunt de hashtabel vervolgens op een speciale manier aan de functie toewijzen.
Hier volgt een voor beeld van het maken van een DHCP-scope op de normale manier.

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

Als [splatting][]niet wordt gebruikt, moeten al deze dingen op één regel worden gedefinieerd. Er wordt een schuif balk van het scherm weer gegeven of er wordt gewikkeld waar ooit het lijkt. Vergelijk nu met een opdracht die gebruikmaakt van splatting.

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

Het gebruik van het `@` teken in plaats van de `$` is het aanroepen van de splat-bewerking.

Neem even de tijd om te weten hoe eenvoudig het voor beeld is te lezen. Ze zijn exact dezelfde opdracht met dezelfde waarden. De tweede is gemakkelijker te begrijpen en verder te onderhouden.

Ik gebruik splatting altijd wanneer de opdracht te lang wordt. Er wordt te lang gedefinieerd, waardoor mijn venster naar rechts schuift. Als ik drie eigenschappen voor een functie raak, zijn conflicteert dat ik deze herschrijft met behulp van een splatted hashtabel.

### <a name="splatting-for-optional-parameters"></a>Splatting voor optionele para meters

Een van de meest voorkomende manieren om splatting te gebruiken, is door te omgaan met optionele para meters die afkomstig zijn van andere plaatsen in mijn script. Stel dat ik een functie heb waarmee een `Get-CIMInstance` aanroep met een optioneel argument wordt ingepakt `$Credential` .

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

U begint met het maken van mijn hashtabel met algemene para meters. Vervolgens voeg ik de toe `$Credential` als deze bestaat.
Omdat ik splatting hier gebruik, hoeft ik alleen maar `Get-CIMInstance` één keer naar mijn code te bellen. Dit ontwerp patroon is zeer helder en kan veel optionele para meters eenvoudig verwerken.

Als u eerlijk wilt zijn, kunt u uw opdrachten schrijven om `$null` waarden voor para meters toe te staan. U hebt gewoon niet altijd de controle over de andere opdrachten die u aanroept.

### <a name="multiple-splats"></a>Meerdere splats

U kunt meerdere hashtabellen naar dezelfde cmdlet splat. Als we ons oorspronkelijke splatting-voor beeld bekijken:

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

Ik gebruik deze methode wanneer ik een gemeen schappelijke set para meters heb die ik aan een groot aantal opdrachten kan door geven.

### <a name="splatting-for-clean-code"></a>Splatting voor schone code

Er is niets mis met het splatting van een enkele para meter als u code kunt opschonen.

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a>Splatting uitvoer bare bestanden

Splatting werkt ook voor sommige uitvoer bare bestanden die gebruikmaken van een `/param:value` syntaxis. `Robocopy.exe`heeft bijvoorbeeld een aantal para meters zoals deze.

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

Ik weet niet dat dit nuttig is, maar ik heb het interessant vond.

## <a name="adding-hashtables"></a>Hashtabellen toevoegen

Hashtabellen ondersteunen de operator voor optellen om twee hashtabellen te combi neren.

```powershell
$person += @{Zip = '78701'}
```

Dit werkt alleen als de twee hashtabellen geen sleutel delen.

## <a name="nested-hashtables"></a>Geneste hashtabellen

We kunnen hashtabellen gebruiken als waarden binnen een hashtabel.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

Ik heb een basis-hashtabel met twee sleutels gestart. Ik heb een sleutel `location` met de naam met een lege hashtabel toegevoegd. Vervolgens zijn de laatste twee items toegevoegd aan die `location` hashtabel. We kunnen dit ook doen.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

Hiermee maakt u dezelfde hashtabel die we hierboven hebben gezien en toegang hebben tot de eigenschappen op dezelfde manier.

```powershell
$person.location.city
Austin
```

Er zijn veel manieren om de structuur van uw objecten te benaderen. Hier volgt een tweede manier om een geneste hashtabel te bekijken.

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

Dit is een combi Naties van het concept van het gebruik van hashtabellen als een verzameling objecten en een verzameling eigenschappen. De waarden zijn nog steeds eenvoudig te benaderen, zelfs wanneer ze zijn genest met een wille keurige benadering.

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

Ik gebruik de punt eigenschap vaak wanneer ik deze wil behandelen als een eigenschap. Dit zijn doorgaans de dingen die ik statisch heb gedefinieerd in mijn code en ik weet dat ze zich op de bovenkant van mijn hoofd bevinden. Als ik de lijst wil door lopen of op een programmatische manier toegang wil krijgen tot de toetsen, gebruik ik de vier Kante haken om de naam van de sleutel op te geven.

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

Met de mogelijkheid om hashtabellen te nesten, hebt u veel flexibiliteit en opties.

### <a name="looking-at-nested-hashtables"></a>Geneste hashtabellen bekijken

Zodra u begint met het nesten van hashtabellen, hebt u een eenvoudige manier nodig om ze te bekijken vanuit de-console. Als ik deze laatste hashtabel, krijg ik een uitvoer die er als volgt uitziet en zo dieper gaat:

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

Mijn ga naar opdracht voor het bekijken van deze dingen is `ConvertTo-JSON` omdat deze zeer schoon is en dat ik regel matig JSON op andere zaken zou gebruiken.

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

Zelfs als u geen JSON kent, kunt u zien wat u zoekt. Er is een `Format-Custom` opdracht voor gestructureerde gegevens, zoals deze, maar de JSON-weer gave is beter.

## <a name="creating-objects"></a>Objecten maken

Soms hoeft u alleen maar een object te hebben en een hashtabel te gebruiken om eigenschappen te bewaren, maar wordt de taak niet uitgevoerd. Doorgaans wilt u de sleutels zien als kolom namen. Een `pscustomobject` maakt dat eenvoudig.

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

Zelfs als u deze niet `pscustomobject` in eerste instantie maakt, kunt u deze altijd later opnieuw casten wanneer dat nodig is.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

Ik heb al een gedetailleerde write-up voor [pscustomobject][] die je na deze versie moet lezen. Het is gebaseerd op een groot aantal dingen die hier worden geleerd.

## <a name="reading-and-writing-hashtables-to-file"></a>Hashtabellen lezen en schrijven naar bestand

### <a name="saving-to-csv"></a>Opslaan in CSV

Lastig met het ophalen van een hashtabel om op te slaan in een CSV, is een van de problemen waarnaar wordt verwezen. Converteer uw hashtabel naar een `pscustomobject` en wordt op de juiste manier opgeslagen in CSV. Zo kunt u beginnen met een `pscustomobject` zodat de volg orde van de kolommen behouden blijft. Maar u kunt deze `pscustomobject` indien nodig naar een inline casten.

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

Ga opnieuw naar mijn write-up met behulp van een [pscustomobject][].

### <a name="saving-a-nested-hashtable-to-file"></a>Een geneste hashtabel opslaan in een bestand

Als ik een geneste hashtabel moet opslaan in een bestand en deze vervolgens weer kan lezen, moet ik de JSON-cmdlets gebruiken om het te doen.

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

Er zijn twee belang rijke punten over deze methode. Ten eerste is de JSON wegge schreven, zodat ik de optie moet gebruiken `-Raw` om deze weer in één teken reeks te lezen. Ten tweede is het geïmporteerde object niet meer een `[hashtable]` . Het is nu a `[pscustomobject]` en dat kan problemen veroorzaken als u deze niet verwacht.

Kijk voor een diep geneste hashtabellen. Wanneer u deze converteert naar JSON, worden de verwachte resultaten mogelijk niet weer geven.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

Gebruik de para meter **Depth** om ervoor te zorgen dat u alle geneste hashtabellen hebt uitgebreid.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

Als u wilt dat deze bij het `[hashtable]` importeren moet worden, moet u de `Export-CliXml` opdrachten en gebruiken `Import-CliXml` .

### <a name="converting-json-to-hashtable"></a>JSON converteren naar hashtabel

Als u JSON naar a moet converteren `[hashtable]` , is er een manier waarop u deze kunt doen met de [JavaScriptSerializer][] in .net.

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

Vanaf Power shell V6 maakt JSON-ondersteuning gebruik van de Newton Soft-JSON.NET en voegt hashtabel-ondersteuning toe.

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

Power shell 6,2 heeft de **Depth** -para meter toegevoegd aan `ConvertFrom-Json` . De standaard **diepte** is 1024.

### <a name="reading-directly-from-a-file"></a>Rechtstreeks vanuit een bestand lezen

Als u een bestand hebt dat een hashtabel met een Power shell-syntaxis bevat, is het een manier om deze rechtstreeks te importeren.

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

De inhoud van het bestand wordt geïmporteerd in een `scriptblock` , waarna wordt gecontroleerd of er geen andere Power shell-opdrachten aanwezig zijn voordat deze wordt uitgevoerd.

Wist u dat een module manifest (het psd1-bestand) alleen een hashtabel is?

## <a name="keys-can-be-any-object"></a>Sleutels kunnen elk wille keurig object zijn

De meeste tijd zijn de sleutels alleen uit teken reeksen. Daarom kunnen we aanhalings tekens maken en deze een eigen sleutel geven.

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

U kunt oneven dingen doen die u mogelijk niet hebt gerealiseerd.

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

Maar omdat u iets kunt doen, betekent dit niet dat u moet. Het laatste lijkt erop dat er een fout is opgetreden die in de wacht staat en dat de code eenvoudig te begrijpen is.

Technisch uw sleutel hoeft geen teken reeks te zijn, maar ze zijn gemakkelijker te zien als u alleen teken reeksen gebruikt. Indexering werkt echter niet goed met de complexe sleutels.

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

Het is niet altijd mogelijk om een waarde in de hashtabel te openen met de bijbehorende sleutel. Bijvoorbeeld:

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

Wanneer de sleutel een matrix is, moet u de `$key` variabele in een subexpressie laten teruglopen zodat deze kan worden gebruikt met de notatie member Access ( `.` ). U kunt ook de notatie matrix index ( `[]` ) gebruiken.

## <a name="use-in-automatic-variables"></a>Gebruiken in automatische variabelen

### <a name="psboundparameters"></a>$PSBoundParameters

[$PSBoundParameters] [] is een automatische variabele die alleen in de context van een functie bestaat.
Het bevat alle para meters waarmee de functie is aangeroepen. Dit is niet precies een hashtabel, maar bijna genoeg zodat u deze kunt behandelen als één.

Dit omvat het verwijderen van sleutels en het splatting aan andere functies. Als u een proxy functie hebt gevonden, kunt u deze beter bekijken.

Zie [about_Automatic_Variables][] voor meer informatie.

### <a name="psboundparameters-gotcha"></a>PSBoundParameters gotcha

Een belang rijke ding die u moet onthouden is dat dit alleen de waarden bevat die worden door gegeven als para meters. Als u ook para meters met standaard waarden hebt, maar deze niet worden door gegeven door de aanroeper, `$PSBoundParameters` bevatten deze waarden niet. Dit wordt meestal gezien.

### <a name="psdefaultparametervalues"></a>$PSDefaultParameterValues

Met deze automatische variabele kunt u standaard waarden toewijzen aan elke cmdlet zonder de cmdlet te wijzigen.
Bekijk dit voor beeld.

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

Hiermee voegt u een vermelding toe aan de `$PSDefaultParameterValues` hashtabel die wordt ingesteld `UTF8` als de standaard waarde voor de `Out-File -Encoding` para meter. Dit is een specifieke sessie, zodat u deze in uw kunt plaatsen `$profile` .

Ik gebruik dit regel matig om waarden vooraf toe te wijzen die ik regel matig Typ.

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

Er worden ook joker tekens geaccepteerd zodat u waarden in bulk kunt instellen. Hier volgen enkele manieren waarop u deze kunt gebruiken:

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

Zie dit fantastische artikel over [automatische standaard instellingen][] door [Michael Sorens][]voor een uitgebreidere uitsplitsing.

## <a name="regex-matches"></a>Regex $Matches

Wanneer u de `-match` operator gebruikt, wordt een automatische variabele `$matches` met de naam gemaakt met de resultaten van de overeenkomst. Als u sub-expressies in uw regex hebt, worden deze subtreffers ook weer gegeven.

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a>Benoemde overeenkomsten

Dit is een van mijn favoriete functies die de meeste mensen niet kennen. Als u een benoemde regex match gebruikt, hebt u toegang tot die overeenkomst op naam op basis van de overeenkomsten.

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

In het bovenstaande voor beeld `(?<Name>.*)` is de een benoemde subexpression. Deze waarde wordt vervolgens in de `$Matches.Name` eigenschap geplaatst.

## <a name="group-object--ashashtable"></a>Group-Object-AsHashtable

Een weinig bekende functie van `Group-Object` is dat deze gegevens sets kan omzetten in een hashtabel voor u.

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

Hiermee wordt elke rij toegevoegd aan een hashtabel en wordt de opgegeven eigenschap gebruikt als de sleutel voor toegang tot de tabel.

## <a name="copying-hashtables"></a>Hashtabellen kopiëren

Een belang rijke ding die u moet weten, is dat hashtabellen objecten zijn. En elke variabele is alleen een verwijzing naar een object. Dit betekent dat het meer werk nodig heeft om een geldige kopie van een hashtabel te maken.

### <a name="assigning-reference-types"></a>Verwijzings typen toewijzen

Wanneer u één hashtabel hebt en deze toewijst aan een tweede variabele, wijzen beide variabelen naar dezelfde hashtabel.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

Dit markeert dat ze hetzelfde zijn omdat het wijzigen van de waarden in een ook de waarden in de andere wijzigt. Dit geldt ook voor het door geven van hashtabellen in andere functies. Als deze functies wijzigingen aanbrengen in de hashtabel, wordt het origineel ook gewijzigd.

### <a name="shallow-copies-single-level"></a>Recente kopieën, één niveau

Als we een eenvoudige hashtabel hebben, zoals in het bovenstaande voor beeld, kunnen we gebruiken om een inkomend `.Clone()` exemplaar te maken.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

Hierdoor kunnen we enkele eenvoudige wijzigingen aanbrengen die niet van invloed zijn op de andere.

### <a name="shallow-copies-nested"></a>Recente kopieën, genest

De reden waarom het een begrootte kopie wordt genoemd, is dat alleen de eigenschappen van het basis niveau worden gekopieerd. Als een van deze eigenschappen een verwijzings type is (zoals een andere hashtabel), zullen die geneste objecten nog steeds naar elkaar wijzen.

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

Zo kunt u zien dat hoewel de hashtabel is gekloond, de verwijzing naar niet is `person` gekloond. We moeten een diepe kopie maken om echt een tweede hashtabel te hebben die niet is gekoppeld aan de eerste.

### <a name="deep-copies"></a>Uitgebreide kopieën

Er zijn een aantal manieren om een diepe kopie van een hashtabel te maken (en deze als hash-tabel te gebruiken). Hier volgt een functie voor het recursief maken van een diepe kopie met behulp van Power shell:

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

Er worden geen andere verwijzings typen of-matrices verwerkt, maar dit is een goed uitgangs punt.

Een andere manier is om .net te gebruiken om deze te deserialiseren met **CliXml** zoals in deze functie:

```powershell
function Get-DeepClone
{
    param(
        $InputObject
    )
    $TempCliXmlString = [System.Management.Automation.PSSerializer]::Serialize($obj, [int32]::MaxValue)
    return [System.Management.Automation.PSSerializer]::Deserialize($TempCliXmlString)
}
```

Voor extreem grote hashtabellen is de deserialisatie functie sneller wanneer deze wordt geschaald. Er zijn echter enkele zaken waarmee u rekening moet houden wanneer u deze methode gebruikt. Aangezien **CliXml** wordt gebruikt, is het geheugen intensief en als u grote hashtabellen klont, kan dit een probleem zijn. Een andere beperking van de **CliXml** is een diepte limiet van 48. Als u een hashtabel met 48 lagen van geneste hashtabellen hebt, mislukt het klonen en wordt er helemaal geen hash-uitvoer uitgevoerd.

## <a name="anything-else"></a>Nog iets?

Ik heb veel moeite gedekt. Ik hoop dat u er geen zorgen meer meer over hebt, of dat u deze beter kunt zien wanneer u dit leest. Omdat ik het volledige spectrum van deze functie heb gezien, zijn er aspecten die alleen op u nu mogelijk niet van toepassing zijn. Dat is heel goed en de verwachte soort is afhankelijk van hoeveel u met Power shell werkt.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[hashtabellen]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[matrices]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Als u prestatie problemen hebt, test u deze]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Automatische standaard waarden]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
