---
title: Alles wat u moet weten over de instructie switch
description: De instructie switch in Power shell biedt functies die niet in andere talen zijn gevonden.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 685a5691599408a0d54ca99bf383bcd7702322a6
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469715"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a>Alles wat u moet weten over de instructie switch

Net als bij veel andere talen heeft Power shell opdrachten voor het beheren van de stroom van uitvoering binnen uw scripts. Een van deze instructies is de instructie [Switch][] en in Power shell en biedt functies die niet in andere talen worden gevonden. Vandaag gaan we een grondige kennis van het werken met de Power shell `switch` .

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="the-if-statement"></a>De `if` instructie

Een van de eerste instructies die u leert, is de `if` instructie. U kunt hiermee een script blok uitvoeren als een instructie is `$true` .

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

U kunt veel gecompliceerdere logica hebben door gebruik `elseif` te maken van en- `else` instructies. Hier volgt een voor beeld waarin ik een numerieke waarde voor de dag van de week heb en de naam als teken reeks wil ophalen.

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

Hiermee wordt aangegeven dat dit een gemeen schappelijk patroon is en er verschillende manieren zijn om dit te verwerken. Een van deze is met een `switch` .

## <a name="switch-statement"></a>Switch-instructie

Met de- `switch` instructie kunt u een variabele en een lijst met mogelijke waarden opgeven. Als de waarde overeenkomt met de variabele, wordt de script Block uitgevoerd.

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

Voor dit voor beeld is de waarde van `$day` overeenkomt met een van de numerieke waarden. vervolgens wordt de juiste naam toegewezen aan `$result` . In dit voor beeld maken we alleen een variabele-toewijzing, maar Power shell kan in die script blokken worden uitgevoerd.

### <a name="assign-to-a-variable"></a>Toewijzen aan een variabele

We kunnen dat laatste voor beeld op een andere manier schrijven.

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

We plaatsen de waarde op de Power shell-pijp lijn en wijzen deze toe aan de `$result` . U kunt dit hetzelfde doen met de `if` instructies and `foreach` .

### <a name="default"></a>Standaard

We kunnen het `default` sleutel woord gebruiken om aan te geven wat er moet gebeuren als er geen overeenkomst is.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

Hier retour neren we de waarde `Unknown` in de standaard situatie.

### <a name="strings"></a>Tekenreeksen

Ik vond getallen in de laatste voor beelden, maar u kunt ook teken reeksen overeenkomen.

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

Ik heb besloten om het niet `Component` in te pakken `Role` en `Location` komt hier overeen met aanhalings tekens om te markeren dat ze optioneel zijn. `switch`In de meeste gevallen worden deze behandeld als een teken reeks.

## <a name="arrays"></a>Matrices

Een van de coole functies van Power shell `switch` is de manier waarop de arrays worden verwerkt. Als u een `switch` matrix geeft, wordt elk element in die verzameling verwerkt.

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

Als u items in uw matrix hebt herhaald, worden deze meerdere keren met de juiste sectie overeenkomen.

### <a name="psitem"></a>PSItem

U kunt de `$PSItem` of gebruiken `$_` om te verwijzen naar het huidige item dat is verwerkt. Wanneer we een eenvoudige overeenkomst volgen, `$PSItem` is de waarde die we overeenkomen. Ik voer enkele geavanceerde overeenkomsten uit in de volgende sectie waar deze variabele wordt gebruikt.

## <a name="parameters"></a>Parameters

Een unieke functie van de Power shell `switch` is dat deze een aantal [para meters][] heeft die wijzigen hoe deze wordt uitgevoerd.

### <a name="-casesensitive"></a>-CaseSensitive

De overeenkomsten zijn standaard niet hoofdletter gevoelig. Als u hoofdletter gevoelig moet zijn, kunt u gebruiken `-CaseSensitive` . Dit kan worden gebruikt in combi natie met de andere para meters voor switches.

### <a name="-wildcard"></a>-Joker teken

U kunt ondersteuning voor joker tekens inschakelen met de `-wildcard` Switch. Dit maakt gebruik van dezelfde Joker teken-Logic als de `-like` operator voor elke overeenkomst.

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

Hier verwerken we een bericht en voeren we het uit op verschillende stromen op basis van de inhoud.

### <a name="-regex"></a>-Regex

De instructie switch ondersteunt regex-overeenkomsten op dezelfde manier als joker tekens.

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

Ik heb meer voor beelden van het gebruik van regex in een ander artikel dat ik heb geschreven: [de vele manieren om regex te gebruiken][].

### <a name="-file"></a>-Bestand

Een kleine bekende functie van de instructie switch is dat een bestand met de para meter kan worden verwerkt `-File` . U gebruikt `-file` met een pad naar een bestand in plaats van het een variabele-expressie op te geven.

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

Het werkt net zoals bij het verwerken van een matrix. In dit voor beeld moet ik deze combi neren met Joker tekens die overeenkomen en het gebruik van gebruiken `$PSItem` . Hiermee wordt een logboek bestand verwerkt en omgezet in waarschuwings-en fout berichten, afhankelijk van de regex-overeenkomsten.

## <a name="advanced-details"></a>Gedetailleerde Details

Nu u op de hoogte bent van al deze gedocumenteerde functies, kunnen we deze gebruiken in de context van geavanceerdere verwerking.

### <a name="expressions"></a>Expressies

De `switch` kan zich in een expressie bevindt in plaats van een variabele.

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

Ongeacht de expressie wordt geëvalueerd naar de waarde die wordt gebruikt voor de overeenkomst.

### <a name="multiple-matches"></a>Meerdere overeenkomsten

U hebt deze mogelijk al verzameld, maar een `switch` kan overeenkomen met meerdere voor waarden. Dit geldt met name bij het gebruik van `-wildcard` of `-regex` overeenkomsten. U kunt dezelfde voor waarde meerdere keren toevoegen en deze allemaal worden geactiveerd.

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

Alle drie de instructies worden gestart. Dit betekent dat elke voor waarde is ingeschakeld (op volg orde). Dit geldt voor verwerkings matrices waarbij elk item elke voor waarde controleert.

### <a name="continue"></a>Doorgaan

Normaal gesp roken is dit waar ik de instructie zou introducen `break` , maar het is beter om eerst te leren hoe we het moeten gebruiken `continue` . Net als bij een `foreach` lus `continue` gaat u verder met het volgende item in de verzameling of sluit u het `switch` als er geen items meer zijn. We kunnen dat laatste voor beeld met continue instructies herschrijven, zodat er slechts één instructie wordt uitgevoerd.

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

In plaats van alle drie de items te vergelijken, wordt de eerste overeenkomst vergeleken en gaat de switch verder met de volgende waarde. Omdat er nog geen waarden meer zijn om te verwerken, wordt de switch afgesloten. In dit volgende voor beeld wordt weer gegeven hoe een Joker teken kan overeenkomen met meerdere items.

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

Omdat een regel in het invoer bestand het woord zou kunnen bevatten `Error` en `Warning` , willen we alleen dat het eerst wordt uitgevoerd en vervolgens door gaan met het verwerken van het bestand.

### <a name="break"></a>Breken

Een `break` instructie sluit de switch af. Dit is hetzelfde gedrag dat `continue` voor één waarde wordt weer gegeven. Het verschil wordt weer gegeven bij het verwerken van een matrix. `break` stopt alle verwerking van de switch en `continue` gaat naar het volgende item.

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

Als we in dit geval regels hebben bezocht die beginnen met, `Error` krijgen we een fout melding en wordt de switch gestopt.
Dit is wat de `break` instructie voor ons doet. Als we `Error` in de teken reeks zoeken en niet alleen aan het begin, schrijven we deze als een waarschuwing. We doen hetzelfde voor `Warning` . Het is mogelijk dat een regel zowel het woord als heeft `Error` `Warning` , maar er is slechts één nodig om te verwerken. Dit is de `continue` instructie voor ons.

### <a name="break-labels"></a>Labels opdelen

De `switch` instructie ondersteunt `break/continue` labels op dezelfde manier als `foreach` .

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

Ik ben niet tevreden over het gebruik van labels voor het kraken, maar ik wilde er wel eens mee weten dat ze verwarrend zijn als u ze nog nooit eerder hebt gezien. Wanneer u meerdere `switch` of `foreach` geneste instructies hebt, wilt u mogelijk meer dan het binnenste item opdelen. U kunt een label plaatsen op een adres `switch` dat het doel van uw kan zijn `break` .

### <a name="enum"></a>Enum

Power shell 5,0 heeft de Enum-teksten geleverd en we kunnen deze gebruiken in een switch.

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

Als u alles wilt opslaan als een sterk getypeerde opsommings punt, kunt u ze tussen haakjes plaatsen.

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

De haakjes zijn hier nodig, zodat de switch de waarde niet `[Context]::Location` als een letterlijke teken reeks behandelt.

### <a name="scriptblock"></a>Script Block

We kunnen een script Block gebruiken om de evaluatie uit te voeren voor een overeenkomst, indien nodig.

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

Dit voegt complexiteit toe en maakt het mogelijk `switch` om uw moeilijk te lezen. In de meeste gevallen is het beter om het gebruik en de instructies te gebruiken `if` `elseif` . Ik zou dit ook gebruiken als ik al een grote switch heb en ik heb twee items nodig om hetzelfde evaluatie blok te bereiken.

Een ding die ik denk aan de Lees baarheid, is om de script Block tussen haakjes te plaatsen.

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

Het wordt nog steeds op dezelfde manier uitgevoerd en biedt een betere visuele afbreek tijd wanneer u deze snel bekijkt.

### <a name="regex-matches"></a>Regex $matches

We moeten de regex opnieuw bezoeken om iets te raken dat niet direct zichtbaar is. Het gebruik van regex vult de `$matches` variabele. Ik ga naar het gebruik van `$matches` meer wanneer ik [op de vele manieren met regex][]gepraat. Hier volgt een kort voor beeld om het weer te geven in actie met benoemde overeenkomsten.

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

### <a name="null"></a>$null

U kunt een `$null` waarde die niet standaard is, vergelijken.

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

Hetzelfde geldt voor een lege teken reeks.

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

### <a name="constant-expression"></a>Constante-expressie

Lee Dailey verwijst dat we een constante-expressie kunnen gebruiken `$true` om `[bool]` items te evalueren.
Stel dat er verschillende Booleaanse controles moeten plaatsvinden.

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

Dit is een schone manier om de status van verschillende Boole-velden te evalueren en actie te ondernemen. Het leuke hiervan is dat u met één overeenkomst de status van een waarde die nog niet is geëvalueerd, kunt spie gelen.

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

`$isEnabled` `$true` In dit voor beeld zorgt u ervoor dat `$isVisible` ook is ingesteld op `$true` . Vervolgens `$isVisible` wordt de script Block geactiveerd wanneer deze wordt geëvalueerd. Dit is een beetje intuïtieve teller, maar is een slimme toepassing van de mechanismen.

### <a name="switch-automatic-variable"></a>Automatische variabele $switch

Wanneer de `switch` waarden worden verwerkt, wordt een enumerator gemaakt en aangeroepen `$switch` . Dit is een automatische variabele die door Power shell wordt gemaakt en u kunt deze rechtstreeks bewerken.

Dit is naar mij gewijsd door [/u/frmadsen](https://www.reddit.com/user/frmadsen)

<div class="reddit-embed" data-embed-media="www.redditmedia.com" data-embed-parent="false" data-embed-live="false" data-embed-uuid="8f6edbf1-abc6-4513-971e-ccd1d202889d" data-embed-created="2018-12-25T22:05:33.986Z"><a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">Commentaar</a> bij de discussie <a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">Wat moet ik doen (IT student) meer informatie over de hoofd-Power shell?</a>.</div><script async src="https://www.redditstatic.com/comment-embed.js"></script>

Dit geeft u de resultaten van:

```Output
2
4
```

Door de enumerator vooruit te verplaatsen, wordt het volgende item niet verwerkt door de `switch` maar hebt u rechtstreeks toegang tot deze waarde. Ik zou dit ook aanroepen.

## <a name="other-patterns"></a>Andere patronen

### <a name="hashtables"></a>Hashtabellen

Een van mijn populairste berichten is de versie van [hashtabellen][]. Een van de use-cases voor a moet `hashtable` een opzoek tabel zijn. Dit is een alternatieve benadering van een gemeen schappelijk patroon dat een `switch` instructie vaak adressert.

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

Als ik alleen een `switch` als lookup gebruik, gebruik ik vaak een `hashtable` in plaats daarvan.

### <a name="enum"></a>Enum

Power shell 5,0 `Enum` is geïntroduceerd in en is ook een optie in dit geval.

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

We kunnen de hele dag op verschillende manieren bezoeken om dit probleem op te lossen. Ik wil er zeker van zijn dat u wist dat u nog geen opties hebt.

## <a name="final-words"></a>Laatste woorden

De instructie switch is eenvoudig op het Opper vlak, maar biedt een aantal geavanceerde functies die de meeste mensen niet realiseren. Door deze functies samen te stellen, is dit een krachtig onderdeel. Ik hoop dat u iets hebt geleerd dat u nog niet eerder hebt gerealiseerd.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[/tijdnotatie]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch parameters]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[De vele manieren om regex te gebruiken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[hashtabellen]: everything-about-hashtable.md
