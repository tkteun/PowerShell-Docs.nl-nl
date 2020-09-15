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
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a>Alles wat u wilt weten over de `if` verklaring

Net als bij veel andere talen bevat Power shell instructies voor het voorwaardelijk uitvoeren van code in uw scripts. Een van deze instructies is de [if][] -instructie. Vandaag gaan we dieper in op een van de belangrijkste opdrachten in Power shell.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="conditional-execution"></a>Voorwaardelijke uitvoering

Uw scripts moeten vaak beslissingen nemen en op basis van deze beslissingen andere logica uitvoeren.
Dit is wat ik wil zeggen door voorwaardelijke uitvoering. U hebt één instructie of waarde om te evalueren en vervolgens voert u een andere sectie met code uit op basis van die evaluatie. Dit is precies wat de `if` instructie doet.

## <a name="the-if-statement"></a>De `if` instructie

Hier volgt een basis voorbeeld van de- `if` instructie:

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

Het eerste wat de `if` instructie doet, evalueert de expressie tussen haakjes. Als deze wordt geëvalueerd `$true` , worden de `scriptblock` in de accolades uitgevoerd. Als dit het geval is, wordt de waarde over `$false` die script Block overgeslagen.

In het vorige voor beeld werd de- `if` instructie gewoon geëvalueerd `$condition` . Het was `$true` en heeft de `Write-Output` opdracht in de script Block uitgevoerd.

In sommige talen kunt u één regel code plaatsen na de `if` instructie en deze wordt uitgevoerd. Dat is niet het geval in Power shell. U moet een volledig `scriptblock` haakje met accolades opgeven om het correct te laten werken.

## <a name="comparison-operators"></a>Vergelijkingsoperatoren

Het meest voorkomende gebruik van de `if` instructie voor is het vergelijken van twee items met elkaar. Power Shell heeft speciale Opera tors voor verschillende vergelijkings scenario's. Wanneer u een vergelijkings operator gebruikt, wordt de waarde aan de linkerkant vergeleken met de waarde aan de rechter kant.

### <a name="-eq-for-equality"></a>-EQ voor gelijkheid

De `-eq` voert een gelijkheids controle tussen twee waarden uit om ervoor te zorgen dat ze gelijk zijn aan elkaar.

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

In dit voor beeld maken we een bekende waarde van `5` en vergelijken deze met mijn `$value` om te zien of ze overeenkomen.

Een mogelijke use-case is het controleren van de status van een waarde voordat u een actie onderneemt. U kunt een service ophalen en controleren of de status werd uitgevoerd voordat u deze aanroept `Restart-Service` .

Het is gebruikelijk in andere talen als C# om te gebruiken `==` voor gelijkheid (bijvoorbeeld: `5 == $value` ), maar dat werkt niet met Power shell. Een andere veelvoorkomende fout die gebruikers doen, is het gelijkteken (bijvoorbeeld) te gebruiken `5 = $value` dat is gereserveerd voor het toewijzen van waarden aan variabelen. Als u de bekende waarde aan de linkerkant plaatst, wordt deze fout meer vreemd.

Deze operator (en andere) heeft enkele variaties.

- `-eq` hoofdletter gevoelig gelijkheid
- `-ieq` hoofdletter gevoelig gelijkheid
- `-ceq` hoofdletter gevoelige gelijkheid

### <a name="-ne-not-equal"></a>-ne niet gelijk

Veel opera tors hebben een gerelateerde operator die het tegenovergestelde resultaat controleren. `-ne` verifieert of de waarden niet gelijk zijn aan elkaar.

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

Gebruik deze methode om ervoor te zorgen dat de actie alleen wordt uitgevoerd als de waarde niet is `5` . Een goed gebruik: gevallen waarin u kunt controleren of een service de status actief heeft voordat u deze probeert te starten.

**Verschillen**

- `-ne` niet hoofdletter gevoelig niet gelijk aan
- `-ine` niet hoofdletter gevoelig niet gelijk aan
- `-cne` hoofdletter gevoelig niet gelijk

Dit zijn inverse variaties van `-eq` . Ik Groepeer deze typen samen wanneer ik variaties voor andere opera tors vermeld.

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a>-gt-ge-lt-Le voor groter dan of kleiner dan

Deze opera tors worden gebruikt bij het controleren of een waarde groter of kleiner dan een andere waarde is.
De `-gt -ge -lt -le` standaard voor GreaterThan, GreaterThanOrEqual, LessThan en LessThanOrEqual.

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

**Verschillen**

- `-gt` groter dan
- `-igt` groter dan, niet hoofdletter gevoelig
- `-cgt` groter dan, hoofdletter gevoelig
- `-ge` groter dan of gelijk aan
- `-ige` groter dan of gelijk aan, niet hoofdletter gevoelig
- `-cge` groter dan of gelijk aan, hoofdletter gevoelig
- `-lt` kleiner dan
- `-ilt` kleiner dan, niet hoofdletter gevoelig
- `-clt` kleiner dan, hoofdletter gevoelig
- `-le` kleiner dan of gelijk aan
- `-ile` kleiner dan of gelijk aan, niet hoofdletter gevoelig
- `-cle` kleiner dan of gelijk aan, hoofdletter gevoelig

Ik weet niet waarom u hoofdletter gevoelige en ingevoelige opties zou gebruiken voor deze opera tors.

### <a name="-like-wildcard-matches"></a>vergelijkbaar met Joker tekens

Power Shell heeft een eigen syntaxis op basis van joker tekens die overeenkomt en u kunt deze gebruiken met de `-like` operator. Deze Joker teken patronen zijn redelijk eenvoudig.

- `?` komt overeen met één wille keurig teken
- `*` komt overeen met een wille keurig aantal tekens

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

Het is belang rijk om te wijzen dat het patroon overeenkomt met de hele teken reeks. Als u iets in het midden van de teken reeks moet overeenkomen, moet u de `*` aan beide uiteinden van de teken reeks plaatsen.

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

**Verschillen**

- `-like` hoofdletter gevoelig Joker teken
- `-ilike` hoofdletter gevoelig Joker teken
- `-clike` hoofdletter gevoelig Joker teken
- `-notlike` hoofdletter gevoelig Joker teken niet gevonden
- `-inotlike` hoofdletter gevoelig Joker teken niet gevonden
- `-cnotlike` hoofdletter gevoelige joker tekens komen niet overeen

### <a name="-match-regular-expression"></a>-overeenkomende reguliere expressie

`-match`Met de operator kunt u een teken reeks controleren op basis van een overeenkomst met een reguliere expressie. Gebruik deze wanneer de Joker teken patronen niet flexibel genoeg zijn voor u.

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

Een regex-patroon komt standaard overeen met een wille keurige plaats in de teken reeks. U kunt dus een subtekenreeks opgeven die overeenkomt met de volgende:

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

Regex is een complexe taal van eigen talen en is aan het kijken. Ik spreek meer over `-match` en [de vele manieren om regex te gebruiken][] in een ander artikel.

**Verschillen**

- `-match` hoofdletter gevoelige regex
- `-imatch` hoofdletter gevoelige regex
- `-cmatch` hoofdletter gevoelige regex
- `-notmatch` hoofdletter gebruik: ongevoelige regex komt niet overeen
- `-inotmatch` hoofdletter gebruik: ongevoelige regex komt niet overeen
- `-cnotmatch` hoofdletter gevoelige regex niet gevonden

### <a name="-is-of-type"></a>-is van het type

U kunt het type van een waarde controleren met de `-is` operator.

```powershell
if ( $value -is [string] )
{
    # do something
}
```

U kunt dit gebruiken als u met klassen werkt of verschillende objecten via de pijp lijn accepteert. U kunt een service-of service naam als invoer hebben. Controleer vervolgens of u een service hebt en haal de service op als u alleen de naam hebt.

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

**Verschillen**

- `-is` van het type
- `-isnot` niet van het type

## <a name="collection-operators"></a>Verzamelings operators

Wanneer u de vorige Opera tors met één waarde gebruikt, is dit het `$true` resultaat `$false` . Dit wordt iets anders behandeld bij het werken met een verzameling. Elk item in de verzameling wordt geëvalueerd en de operator retourneert elke waarde die wordt geëvalueerd `$true` .

```powershell
PS> 1,2,3,4 -eq 3
3
```

Dit werkt nog steeds goed in een- `if` instructie. Daarom wordt er een waarde geretourneerd door uw operator, waarna de volledige instructie wordt weer gegeven `$true` .

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

Er is een kleine trap die in de details wordt weer gegeven, die ik moet afwijzen. Wanneer u de `-ne` operator op deze manier gebruikt, is het eenvoudig om de logica achterwaarts te bekijken. Gebruiken `-ne` met een verzameling retourneert `$true` als een item in de verzameling niet overeenkomt met uw waarde.

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

Dit ziet eruit als een slimme truc, maar we hebben Opera tors `-contains` en `-in` die dit efficiënter afhandelen. En `-notcontains` wat u verwacht.

### <a name="-contains"></a>-contains

De `-contains` operator controleert de verzameling op uw waarde. Zodra er een overeenkomst wordt gevonden, wordt deze geretourneerd `$true` .

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

Dit is de aanbevolen manier om te zien of een verzameling uw waarde bevat. Met `Where-Object` (of `-eq` ) wordt de volledige lijst elke keer door lopen en is deze aanzienlijk langzamer.

**Verschillen**

- `-contains` hoofdletter gevoelig overeenkomst
- `-icontains` hoofdletter gevoelig overeenkomst
- `-ccontains` hoofdletter gevoelige overeenkomst
- `-notcontains` niet hoofdletter gevoelig niet gevonden
- `-inotcontains` niet hoofdletter gevoelig niet gevonden
- `-cnotcontains` hoofdletter gevoelig niet gevonden

### <a name="-in"></a>-in

De operator bevindt `-in` zich net als de `-contains` operator, behalve dat de verzameling zich aan de rechter kant bevindt.

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

**Verschillen**

- `-in` hoofdletter gevoelig overeenkomst
- `-iin` hoofdletter gevoelig overeenkomst
- `-cin` hoofdletter gevoelige overeenkomst
- `-notin` niet hoofdletter gevoelig niet gevonden
- `-inotin` niet hoofdletter gevoelig niet gevonden
- `-cnotin` hoofdletter gevoelig niet gevonden

## <a name="logical-operators"></a>Logische operators

Logische Opera tors worden gebruikt om andere expressies om te draaien of te combi neren.

### <a name="-not"></a>-niet

De `-not` operator spiegelt een expressie van `$false` naar `$true` of van `$true` naar `$false` . Hier volgt een voor beeld waarin we een actie willen uitvoeren wanneer dat het geval `Test-Path` is `$false` .

```powershell
if ( -not ( Test-Path -Path $path ) )
```

De meeste Opera tors die ons hebben besproken hebben een variant waarin u de operator niet hoeft te gebruiken `-not` . Het is echter nog steeds handig.

### <a name="-operator"></a>! operator

U kunt gebruiken `!` als een alias voor `-not` .

```powershell
if ( -not $value ){}
if ( !$value ){}
```

U ziet mogelijk `!` meer voor mensen die afkomstig zijn uit andere talen, zoals C#. Ik wil het beste typen, omdat ik het moeilijk kan zien wanneer ik snel naar mijn scripts zoek.

### <a name="-and"></a>-en

U kunt expressies combi neren met de `-and` operator. Wanneer u dat doet, moeten beide zijden `$true` van de hele expressie zijn `$true` .

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

In dit voor beeld `$age` moet de linkerkant 13 of ouder zijn en kleiner dan 55 voor de rechter kant. Ik heb extra haakjes toegevoegd om het voor beeld duidelijker te maken, maar ze zijn optioneel, zolang de expressie eenvoudig is. Hier volgt hetzelfde voor beeld zonder deze.

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

De evaluatie vindt plaats van links naar rechts. Als het eerste item wordt geëvalueerd naar `$false` , wordt het vroegtijdig afgesloten en wordt de juiste vergelijking niet uitgevoerd. Dit is handig wanneer u er zeker van wilt zijn dat er een waarde bestaat voordat u deze gebruikt. `Test-Path`Als u bijvoorbeeld een pad geeft, treedt er een fout op `$null` .

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a>-of

`-or`Op die manier kunt u twee expressies opgeven en wordt geretourneerd `$true` als er een van beide wordt weer gegeven `$true` .

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

Net als bij de `-and` operator is de evaluatie van links naar rechts. Behalve dat als het eerste deel is `$true` , is het hele overzicht `$true` en wordt de rest van de expressie niet verwerkt.

Houd er ook rekening mee dat de syntaxis voor deze opera tors werkt. U hebt twee afzonderlijke expressies nodig. Ik heb gezien dat gebruikers iets anders proberen te doen, `$value -eq 5 -or 6` zonder hun fout te realiseren.

### <a name="-xor-exclusive-or"></a>-XOR exclusieve of

Dit is een beetje ongebruikelijk. `-xor` Hiermee kan slechts één expressie worden geëvalueerd `$true` . Dus als beide items `$false` of beide items zijn `$true` , is de hele expressie `$false` . Een andere manier om dit te bekijken is de expressie alleen `$true` wanneer de resultaten van de expressie verschillend zijn.

Het komt zelden voor dat iedereen deze logische operator zou gebruiken en ik niet op de juiste manier kan zien waarom ik deze ooit zou gebruiken.

## <a name="bitwise-operators"></a>Bitsgewijze operatoren

Bitsgewijze Opera tors voeren berekeningen uit op de bits binnen de waarden en produceren een nieuwe waarde als resultaat. Leer [bitsgewijze Opera tors][] vallen buiten het bereik van dit artikel, maar dit is de lijst.

- `-band` binaire en
- `-bor` binair of
- `-bxor` binaire exclusieve of
- `-bnot` binair niet
- `-shl` Shift-links
- `-shr` naar rechts verplaatsen

## <a name="powershell-expressions"></a>Power shell-expressies

U kunt normaal Power shell gebruiken in de voor waarde-instructie.

```powershell
if ( Test-Path -Path $Path )
```

`Test-Path` retourneert `$true` of `$false` wanneer deze wordt uitgevoerd. Dit geldt ook voor opdrachten die andere waarden retour neren.

```powershell
if ( Get-Process Notepad* )
```

`$true`Als er een proces wordt geretourneerd, wordt het geëvalueerd als `$false` there'sn'thing. Het is volledig geldig om pijplijn expressies of andere Power shell-instructies te gebruiken:

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

Deze expressies kunnen met elkaar worden gecombineerd met de `-and` `-or` Opera tors en, maar u kunt ook haakjes gebruiken om ze in subexpressies te splitsen.

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a>Controleren op $null

`$null`Als er `$false` in de instructie geen resultaat of een waarde wordt geëvalueerd `if` . Bij het controleren van `$null` de specifiek voor is het een best practice om de `$null` aan de linkerkant te plaatsen.

```powershell
if ( $null -eq $value )
```

Er zijn zeer enkele nuances voor het omgaan met `$null` waarden in Power shell. Als u geïnteresseerd bent in een diep gaande, heb ik een artikel over [Alles wat je van $Null zou weten te][]komen.

### <a name="variable-assignment"></a>Variabele toewijzing

Ik ben bijna klaar om deze toe te voegen tot [Prasoon Karunan V][] eraan herinneren.

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

Normaal gesp roken wanneer u een waarde aan een variabele toewijst, wordt de waarde niet door gegeven aan de pijp lijn of de console. Wanneer u een variabele toewijzing in een sub-expressie doet, wordt deze door gegeven aan de pijp lijn.

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

Zie hoe de `$first` toewijzing geen uitvoer heeft en de `$second` toewijzing? Wanneer een toewijzing wordt uitgevoerd in een `if` instructie, wordt deze uitgevoerd op dezelfde manier als de `$second` bovenstaande toewijzing. Hier volgt een voor beeld van hoe u het kunt gebruiken:

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

Als `$process` wordt toegewezen aan een waarde, wordt de instructie `$true` beëindigd en wordt `$process` deze gestopt.

Zorg ervoor dat u dit niet verwart met `-eq` omdat dit geen gelijkheids controle is. Dit is een meer bedekkende functie die de meeste mensen niet op deze manier kunnen gebruiken.

## <a name="alternate-execution-path"></a>Alternatief pad voor uitvoering

Met de- `if` instructie kunt u een actie voor niet alleen opgeven als de instructie `$true` , maar ook voor wanneer deze is `$false` . Hier `else` komt de instructie af.

### <a name="else"></a>else

De `else` instructie is altijd het laatste deel van de `if` instructie wanneer deze wordt gebruikt.

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

In dit voor beeld controleren we de `$path` om er zeker van te zijn dat het een bestand is. Als we het bestand vinden, verplaatsen we het. Als dat niet het geval is, wordt er een waarschuwing geschreven. Dit type vertakkings logica is zeer gebruikelijk.

### <a name="nested-if"></a>Genest als

De `if` `else` instructies and maken een script blok, zodat we een Power shell-opdracht in de and kunnen plaatsen, met inbegrip van een andere `if` instructie. Zo kunt u veel gecompliceerdere logica gebruiken.

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

In dit voor beeld testen we het pad blij eerst en vervolgens onderneemt u actie. Als dat niet lukt, voert u een andere controle uit en geeft u meer gedetailleerde informatie aan de gebruiker.

### <a name="elseif"></a>elseif

We zijn niet beperkt tot slechts één voorwaardelijke controle. We kunnen `if` `else` de instructies en overzichten samen voegen in plaats van ze te nesten met behulp van de- `elseif` instructie.

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

De uitvoering vindt plaats van boven naar beneden. De `if` instructie top wordt eerst geëvalueerd. Als dat zo is `$false` , wordt het naar het volgende `elseif` of `else` in de lijst verplaatst. Dat laatste `else` is de standaard actie die moet worden uitgevoerd als geen van de andere gebruikers retour neren `$true` .

### <a name="switch"></a>schakelen

Op dit moment moet ik de `switch` instructie vermelden. Het bevat een alternatieve syntaxis voor het uitvoeren van meerdere vergelijkingen met een waarde. Met de `switch` kunt u een expressie opgeven en wordt het resultaat vergeleken met verschillende waarden. Als een van deze waarden overeenkomt, wordt het overeenkomende code blok uitgevoerd. Bekijk dit voorbeeld:

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

Er zijn drie mogelijke waarden die kunnen overeenkomen met `$itemType` . In dit geval komt het overeen met `Role` . Ik heb een eenvoudig voor beeld gebruikt om u een deel van de `switch` operator te geven. Ik vind meer informatie over [Alles wat je ooit zou weten over de instructie switch][] in een ander artikel.

## <a name="pipeline"></a>Pijplijn

De pijp lijn is een unieke en belang rijke functie van Power shell. Elke waarde die niet wordt onderdrukt of toegewezen aan een variabele, wordt in de pijp lijn geplaatst. Het `if` biedt ons een manier om te profiteren van de pijp lijn op een manier die niet altijd duidelijk is.

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

Elk script blok plaatst de resultaten van de opdrachten of de waarde in de pijp lijn. Vervolgens wijzen we het resultaat van de `if` instructie toe aan de `$discount` variabele. Dit voor beeld kan net zo eenvoudig worden toegewezen aan de `$discount` variabele rechtstreeks in elke script Block. Ik kan dit niet zeggen dat ik dit met de `if` instructie regel matig gebruik, maar ik heb er wel een voor beeld van.

### <a name="array-inline"></a>Matrix inline

Ik heb een functie met de naam [invoke-SnowSql][] waarmee een uitvoerbaar bestand met verschillende opdracht regel argumenten wordt gestart. Hier volgt een clip van deze functie, waarbij de matrix met argumenten wordt opgebouwd.

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

De `$Debug` `$Path` variabelen en zijn para meters voor de functie die door de eind gebruiker wordt opgegeven.
Ik Beoordeel deze inline binnen de initialisatie van mijn matrix. Als `$Debug` is ingesteld op True, worden deze waarden `$snowSqlParam` in de juiste plaats gezet. Hetzelfde geldt voor de `$Path` variabele.

## <a name="simplify-complex-operations"></a>Vereenvoudig complexe bewerkingen

Het is onvermijdelijk dat u een situatie ondervindt die te veel vergelijkingen heeft om te controleren en uw `If` instructie schuift in de rechter kant van het scherm.

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

Ze kunnen moeilijk te lezen zijn en waardoor u meer gevoelig maakt voor fouten. Er zijn enkele dingen die we hiervoor kunnen doen.

### <a name="line-continuation"></a>Regel voortzetting

Er zijn enkele opera tors in Power shell waarmee u naar de volgende regel kunt teruglopen. De logische Opera tors `-and` en `-or` zijn goede Opera tors die u kunt gebruiken als u uw expressie wilt opsplitsen in meerdere regels.

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

Er is nog steeds veel aan de slag, maar elk stuk op een aparte regel maakt een groot verschil.
Dit wordt in het algemeen gebruikt wanneer ik meer dan twee vergelijkingen krijg of als ik naar rechts moet schuiven om een van de logica te lezen.

### <a name="pre-calculating-results"></a>Resultaten vooraf berekenen

We kunnen deze instructie uit de verklaring halen `if` en alleen het resultaat controleren.

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

Dit is net zo veel duidelijker dan het vorige voor beeld. U krijgt ook de mogelijkheid om een naam van een variabele te gebruiken waarin wordt uitgelegd wat het is dat u werkelijk controleert. Dit is ook een voor beeld van zelf-document code waarmee overbodige opmerkingen worden opgeslagen.

### <a name="multiple-if-statements"></a>Meerdere if-instructies

We kunnen dit in meerdere instructies opsplitsen en er één tegelijk op controleren. In dit geval gebruiken we een vlag of een tracerings variabele om de resultaten te combi neren.

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

Ik had de logica moeten inverteren om ervoor te zorgen dat de vlag logica goed werkt. Elke evaluatie is een afzonderlijke `if` instructie. Het voor deel hiervan is dat wanneer u fouten wilt opsporen, u precies weet wat de logica doet. Ik kon op hetzelfde moment veel betere uitgebreider toevoegen.

Het voor de hand liggende nadeel is dat er veel meer code moet worden geschreven. De code is complexer om te kijken naar dezelfde regel logica en explodeert deze in 25 of meer regels.

### <a name="using-functions"></a>Functies gebruiken

We kunnen ook alle validatie logica naar een functie verplaatsen. Bekijk hoe schoon dit in één oogopslag eruitziet.

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

U moet de functie nog steeds maken om de validatie uit te voeren, maar dit maakt het veel eenvoudiger om met deze code te werken. Dit maakt deze code gemakkelijker te testen. In uw tests kunt u de aanroep naar vertrekt `Test-ADDriveConfiguration` en hebt u slechts twee tests nodig voor deze functie. Een locatie waar deze wordt geretourneerd `$true` en een waar deze wordt geretourneerd `$false` . Het testen van de andere functie is eenvoudiger omdat deze zo klein is.

De hoofd tekst van de functie kan nog steeds zijn dat er één regel is gestart met of de uitgelichte logica die we in de laatste sectie hebben gebruikt. Dit werkt goed voor beide scenario's en stelt u in staat om die implementatie later eenvoudig te wijzigen.

## <a name="error-handling"></a>Foutafhandeling

Een belang rijk gebruik van de- `if` instructie is het controleren op fouten voordat u fouten ondervindt. Een goed voor beeld is om te controleren of er al een map bestaat voordat u deze probeert te maken.

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

Als u een uitzonde ring verwacht, is dit niet echt een uitzonde ring. Controleer uw waarden dus en Valideer uw voor waarden waar u dit kunt doen.

Als u nog iets meer wilt weten over uitzonde ringen, kunt u een artikel over [Alles wat u graag op het punt staat dat u op de hoogte zou zijn van uitzonde ringen][].

## <a name="final-words"></a>Laatste woorden

De `if` instructie is een eenvoudige instructie, maar is een fundamenteel onderdeel van Power shell. U kunt deze meermaals gebruiken in bijna elk script dat u schrijft. Ik hoop dat u een beter inzicht hebt dan voorheen.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2019-08-11-Powershell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[If]: /powershell/module/microsoft.powershell.core/about/about_if
[bitsgewijze Opera tors]: /powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[de vele manieren om regex te gebruiken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[alles wat u moet weten over uitzonde ringen]: everything-about-exceptions.md
[alles wat u wilt weten over $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[alles wat u moet weten over de instructie switch]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
