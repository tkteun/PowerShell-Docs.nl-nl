---
title: Alles wat u wilt weten over $null
description: De Power shell-$null lijkt vaak eenvoudig te zijn, maar er zijn veel nuances. Laten we de $null sluiten, zodat u weet wat er gebeurt wanneer u onverwacht een null-waarde uitvoert.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/01/2020
ms.locfileid: "84149829"
---
# <a name="everything-you-wanted-to-know-about-null"></a>Alles wat u wilt weten over $null

De Power shell `$null` lijkt vaak eenvoudig te zijn, maar er zijn veel nuances. Laten we eens kijken `$null` hoe u weet wat er gebeurt wanneer u onverwacht een `$null` waarde uitvoert.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="what-is-null"></a>Wat is NULL?

U kunt NULL beschouwen als een onbekende of lege waarde. Een variabele is NULL totdat u er een waarde of een object aan toewijst. Dit kan belang rijk zijn omdat er enkele opdrachten zijn waarvoor een waarde is vereist en fouten worden gegenereerd als de waarde NULL is.

### <a name="powershell-null"></a>Power shell-$null

`$null` is een automatische variabele in Power shell die wordt gebruikt om NULL weer te geven. U kunt deze toewijzen aan variabelen, deze gebruiken in vergelijkingen en deze gebruiken als plaatsaanduiding voor NULL in een verzameling.

Power shell behandelt `$null` als een object met de waarde Null. Dit wijkt af van wat u kunt verwachten als u uit een andere taal komt.

## <a name="examples-of-null"></a>Voor beelden van $null

Telkens wanneer u een variabele wilt gebruiken die u niet hebt geïnitialiseerd, is de waarde `$null` . Dit is een van de meest voorkomende manieren waarop `$null` waarden in uw code worden alvast.

```powershell
PS> $null -eq $undefinedVariable
True
```

Als u een variabelenaam hebt getypt, ziet Power shell deze als een andere variabele en de waarde is `$null` .

De andere manier om `$null` waarden te vinden, is wanneer ze afkomstig zijn van andere opdrachten die geen resultaten opleveren.

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a>Gevolgen van $null

`$null` waarden beïnvloeden uw code anders, afhankelijk van waar ze worden weer gegeven.

### <a name="in-strings"></a>In teken reeksen

Als u `$null` in een teken reeks gebruikt, is het een lege waarde (of een lege teken reeks).

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

Dit is een van de redenen waarom ik in de logboek berichten een punt haken wil plaatsen rond variabelen. Het is nog belang rijker om de randen van de waarden van variabelen te identificeren wanneer de waarde aan het einde van de teken reeks is.

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

Dit maakt lege teken reeksen en `$null` waarden gemakkelijk te herkennen.

### <a name="in-numeric-equation"></a>In numerieke vergelijking

Wanneer een `$null` waarde wordt gebruikt in een numerieke vergelijking, zijn de resultaten ongeldig als ze geen fout geven. Soms `$null` wordt de evaluatie van `0` en andere tijden het hele resultaat `$null` .
Hier volgt een voor beeld met vermenigvuldiging met de waarde 0 of `$null` afhankelijk van de volg orde van de waarden.

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a>In plaats van een verzameling

Met een verzameling kunt u een index gebruiken om toegang te krijgen tot waarden. Als u probeert te indexeren in een verzameling die daad werkelijk wordt `null` weer geven, krijgt u deze fout: `Cannot index into a null array` .

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

Als u een verzameling hebt maar probeert toegang te krijgen tot een element dat zich niet in de verzameling bevindt, wordt er een resultaat weer geven `$null` .

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a>In plaats van een object

Als u probeert toegang te krijgen tot een eigenschap of sub-eigenschap van een object dat niet over de opgegeven eigenschap beschikt, krijgt u een `$null` waarde zoals u zou doen voor een niet-gedefinieerde variabele. Het maakt niet uit of de variabele `$null` of een werkelijk object in dit geval is.

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a>Methode voor een expressie met Null-waarden

Het aanroepen van een methode voor een `$null` object genereert een `RuntimeException` .

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

Wanneer ik de woord groep Zie, `You cannot call a method on a null-valued expression` wordt het eerste wat ik zoek, plaatsen waar ik een methode aanmeldt voor een variabele zonder deze eerst te controleren `$null` .

## <a name="checking-for-null"></a>Controleren op $null

U hebt wellicht al gemerkt dat ik aan de `$null` linkerkant altijd aan het controleren was wanneer ik `$null` in mijn voor beelden Controleer. Dit is opzettelijk en wordt geaccepteerd als Power shell-best practice. Er zijn enkele scenario's waarbij u deze aan de rechter kant niet het verwachte resultaat geeft.

Bekijk dit volgende voor beeld en probeer de resultaten te voors pellen:

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

Als ik niet Definieer `$value` , wordt het eerste geëvalueerd `$true` en het bericht is `The array is $null` . Deze trap is het mogelijk om een te maken `$value` waarmee beide kunnen worden `$false`

```powershell
$value = @( $null )
```

In dit geval is de een `$value` matrix met een `$null` . `-eq`Hiermee wordt elke waarde in de matrix gecontroleerd en wordt `$null` er een overeenkomst geretourneerd. Dit resulteert in `$false` . Het `-ne` retourneert alles dat niet overeenkomt `$null` , en in dit geval zijn er geen resultaten (deze worden ook geëvalueerd naar `$false` ). Geen van beide kan worden weer gegeven `$true` , maar het lijkt erop dat er een van de twee is.

U kunt niet alleen een waarde maken waardoor beide worden geëvalueerd `$false` . het is mogelijk om een waarde te maken waarbij deze beide worden geëvalueerd `$true` . Mathias Jessen ( @IISResetMe ) heeft een [goede post][] die Dives in dat scenario.

### <a name="psscriptanalyzer-and-vscode"></a>PSScriptAnalyzer en VSCode

De [PSScriptAnalyzer][] -module heeft een regel waarmee wordt gecontroleerd of dit probleem is aangeroepen `PSPossibleIncorrectComparisonWithNull` .

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

Omdat VS code ook de PSScriptAnalyser-regels gebruikt, wordt dit door de service gemarkeerd of geïdentificeerd als een probleem in het script.

### <a name="simple-if-check"></a>Eenvoudig als controleren

Een gemeen schappelijke manier die gebruikers controleren op een niet-$nulle waarde, is het gebruik van een eenvoudige `if()` instructie zonder de vergelijking.

```powershell
if ( $value )
{
    Do-Something
}
```

Als de waarde is `$null` , wordt deze geëvalueerd als `$false` . Dit is eenvoudig te lezen, maar wees voorzichtig met het zoeken naar precies wat u verwacht. Ik heb deze regel code gelezen als:

> Als `$value` heeft een waarde.

Maar dat is niet het hele verhaal. Deze regel heeft de volgende melding:

> Als `$value` is niet `$null` of `0` of of `$false` een `empty string`

Hier volgt een meer uitgebreid voor beeld van deze instructie.

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

Het is heel goed om een basis controle te gebruiken `if` , zolang u weet dat de andere waarden tellen als `$false` en niet alleen dat een variabele een waarde heeft.

Ik heb dit probleem ondertreden bij het refactoreren van een paar dagen geleden. Dit is een basis eigenschap die er ongeveer als volgt uitziet.

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

Ik wilde een waarde alleen toewijzen aan de object eigenschap als deze aanwezig is. In de meeste gevallen heeft het oorspronkelijke object een waarde die `$true` in de instructie zou kunnen evalueren `if` . Maar er is een probleem opgetreden waarbij de waarde af en toe niet is ingesteld. Er is een fout opgetreden in de code en er is vastgesteld dat het object de eigenschap had, maar dit is een lege teken reeks waarde. Dit voor komt dat het ooit is bijgewerkt met de vorige logica. Dus ik heb een goede `$null` controle en alles gewerkt.

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

Het is weinig bugs, zoals deze die moeilijk te herkennen zijn, en u kunt de waarden controleren voor `$null` .

## <a name="nullcount"></a>$null. Aantal

Als u een eigenschap van een waarde probeert te openen `$null` , is dat ook de eigenschap `$null` . De `count` eigenschap is de uitzonde ring op deze regel.

```powershell
PS> $value = $null
PS> $value.count
0
```

Wanneer u een `$null` waarde hebt, is dat `count` `0` . Deze speciale eigenschap wordt toegevoegd door Power shell.

### <a name="pscustomobject-count"></a>PSCustomObject Aantal

Bijna alle objecten in Power Shell hebben die eigenschap Count. Een belang rijke uitzonde ring is de `[PSCustomObject]` in Windows Power shell 5,1 (dit is opgelost in Power shell 6,0). Het heeft geen eigenschap Count, dus u krijgt een `$null` waarde als u deze probeert te gebruiken. Dit noemen we hier zodat je niet kunt gebruiken `.Count` in plaats van een `$null` cheque.

Als u dit voor beeld uitvoert op Windows Power shell 5,1 en Power shell 6,0, hebt u verschillende resultaten.

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a>Lege Null

Er is een speciaal type van `$null` dat anders is dan de andere. Ik bel het, maar het is wel `$null` echt een [System. Management. Automation. internal. AutomationNull][]. Dit `$null` is een leeg item dat u krijgt als resultaat van een functie of script blok dat Nothing retourneert (een ongeldig resultaat).

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

Als u het vergelijkt met `$null` , krijgt u een `$null` waarde. Bij gebruik in een evaluatie waarbij een waarde is vereist, is de waarde altijd `$null` . Maar als u dit binnen een matrix plaatst, wordt het beschouwd als een lege matrix.

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

U kunt een matrix hebben die één `$null` waarde bevat `count` `1` . Maar als u een leeg resultaat binnen een matrix plaatst, wordt dit niet als een item beschouwd. Het aantal is `0` .

Als u het lege item als `$null` een verzameling behandelt, is het leeg.

### <a name="pipeline"></a>Pijplijn

De primaire locatie die u ziet, is het verschil wanneer u de pijp lijn gebruikt. U kunt een waarde sluis teken, `$null` maar niet een lege `$null` waarde.

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

Afhankelijk van uw code moet u rekening `$null` met de in uw logica.

Controleer eerst op `$null`

- Null filteren op de pijp lijn ( `... | Where {$null -ne $_} | ...` )
- Afhandelen in de pijplijn functie

## <a name="foreach"></a>foreach

Een van mijn favoriete functies van `foreach` is dat deze niet wordt geïnventariseerd over een `$null` verzameling.

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

Zo hoeft u niet te `$null` controleren of de verzameling moet worden gecontroleerd voordat deze wordt geïnventariseerd. Als u een verzameling waarden hebt `$null` , kan de waarde `$node` nog steeds zijn `$null` .

De foreach-bewerking is op deze manier gestart met Power Shell 3,0. Als u een oudere versie hebt, is dit niet het geval. Dit is een van de belang rijke wijzigingen waar u rekening mee moet houden bij het maken van back-poort code voor 2,0-compatibiliteit.

## <a name="value-types"></a>Waardetypen

Technisch gezien kunnen alleen verwijzings typen zijn `$null` . Power shell is echter zeer ruime en Hiermee kunnen variabelen elk type zijn. Als u besluit een type waarde te typen, kan dat niet `$null` .
Power shell converteert `$null` naar een standaard waarde voor veel typen.

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

Er zijn een aantal typen die geen geldige conversie van hebben `$null` . Deze typen genereren een `Cannot convert null to type` fout.

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a>Functie parameters

Het gebruik van een sterk getypeerde waarde in functie parameters is zeer gebruikelijk. Het is raadzaam om de typen van de para meters te definiëren, zelfs als we de typen van andere variabelen in onze scripts niet definiëren. Mogelijk hebt u al een aantal sterk getypeerde variabelen in uw functies en kunt u deze zelfs niet realiseren.

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

Zodra u het type van de para meter instelt als een `string` , mag de waarde nooit zijn `$null` . Het is gebruikelijk om te controleren of een waarde is `$null` om te zien of de gebruiker een waarde heeft gegeven of niet.

```powershell
if ( $null -ne $Value ){...}
```

`$Value` is een lege teken reeks `''` als er geen waarde is opgegeven. Gebruik `$PSBoundParameters.Value` in plaats daarvan de automatische variabele.

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

`$PSBoundParameters` bevat alleen de para meters die zijn opgegeven bij het aanroepen van de functie.
U kunt ook de `ContainsKey` methode gebruiken om te controleren op de eigenschap.

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a>IsNotNullOrEmpty

Als de waarde een teken reeks is, kunt u een statische teken reeks functie gebruiken om te controleren of de waarde `$null` of een lege teken reeks tegelijk is.

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

Ik vind mijzelf vaak als ik weet dat het waardetype een teken reeks moet zijn.

## <a name="when-i-null-check"></a>Wanneer ik $null controleren

Ik ben een verdedigings scripter. Wanneer ik een functie oproep en deze aan een variabele toewijs, controleer ik deze voor `$null` .

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

Ik wil veel voor keur gebruiken `if` of `foreach` gebruiken `try/catch` . Krijg ik niet mis, ik gebruik nog steeds `try/catch` een hoop. Maar als ik op een fout voorwaarde of een lege set resultaten kan testen, kan ik mijn uitzonderings afhandeling toestaan voor echte uitzonde ringen.

Er wordt ook in de praktijk gecontroleerd `$null` of er een waarde is voor een-object of om methoden aan te roepen. Deze twee acties mislukken voor een `$null` object, zodat het belang rijk is om het eerst te valideren. Ik heb deze scenario's al eerder in dit bericht behandeld.

### <a name="no-results-scenario"></a>Scenario met geen resultaten

Het is belang rijk om te weten dat verschillende functies en opdrachten het scenario voor geen resultaten anders afhandelen. Veel Power shell-opdrachten retour neren de lege `$null` en een fout in de fout stroom. Maar andere veroorzaken uitzonde ringen of bieden u een status object. Het is nog steeds aan u om te weten hoe de opdrachten die u gebruikt, geen resultaten en fout scenario's opleveren.

## <a name="initializing-to-null"></a>Initialiseren naar $null

Eén gewoonte die ik heb gekozen, initialiseert al mijn variabelen voordat ik ze gebruik. U moet dit doen in andere talen. Aan de bovenkant van mijn functie of als ik een foreach-lus Voer, definieer ik alle waarden die ik gebruik.

Hier volgt een scenario waarin u een close-out wilt maken. Dit is een voor beeld van een bug die ik eerder moest opsporen.

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

De verwachting is dat `Get-Something` ofwel een resultaat of een lege waarde `$null` . Als er een fout optreedt, wordt het geregistreerd. Vervolgens controleren we of we een geldig resultaat hebben ontvangen voordat we het verwerken.

De fout bij het verbergen van deze code is wanneer `Get-Something` een uitzonde ring wordt gegenereerd en er geen waarde aan wordt toegewezen `$result` . Dit mislukt vóór de toewijzing, dus we gaan niet zelfs `$null` toe aan de `$result` variabele. `$result` bevat nog steeds de voor gaande geldige `$result` van andere herhalingen.
`Update-Something` meerdere keren uitvoeren op hetzelfde object in dit voor beeld.

Ik ben ingesteld `$result` op `$null` rechts in de foreach-lus voordat ik deze gebruik om dit probleem te verhelpen.

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a>Scope problemen

Dit helpt ook bij het beperken van problemen met scopes. In dit voor beeld wijzen we waarden toe aan `$result` boven en boven in een lus. Maar omdat in Power shell variabele waarden van buiten de functie kunnen worden verkleind tot het bereik van de huidige functie, worden de fouten die op die manier kunnen worden geïnitialiseerd, in de functie opgelost.

Een niet-geïnitialiseerde variabele in de functie is niet `$null` als deze is ingesteld op een waarde in een bovenliggend bereik.
Het bovenliggende bereik kan een andere functie zijn die de functie aanroept en dezelfde variabele namen gebruikt.

Als ik hetzelfde `Do-something` voor beeld doe en de lus Verwijder, zou ik uiteindelijk iets zien dat er ongeveer zo uitziet als in dit voor beeld:

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

Als de aanroep `Get-Something` een uitzonde ring genereert, zoekt mijn `$null` controle de `$result` van `Invoke-Something` . Het initialiseren van de waarde in de functie vermindert dit probleem.

Naamgevings variabelen zijn moeilijk en het is gebruikelijk dat een auteur dezelfde namen van variabelen in meerdere functies gebruikt. Ik weet dat ik `$node` , `$result` ,, `$data` altijd. Het is dus heel eenvoudig om waarden uit verschillende bereiken weer te geven op plaatsen waar ze niet mogen zijn.

## <a name="redirect-output-to-null"></a>Uitvoer omleiden naar $null

Ik heb op de hoogte `$null` van de waarden voor dit hele artikel, maar het onderwerp is niet voltooid als er geen omleidings uitvoer naar wordt vermeld `$null` . Er zijn momenten waarop u opdrachten kunt uitvoeren die gegevens of objecten bevatten die u wilt onderdrukken. Uitvoer omleiden naar `$null` is dat.

### <a name="out-null"></a>Out-Null

De out-null-opdracht is de ingebouwde manier om pijplijn gegevens om te leiden naar `$null` .

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a>Toewijzen aan $null

U kunt de resultaten van een opdracht toewijzen aan `$null` voor hetzelfde effect als met `Out-Null` .

```powershell
$null = New-Item -Type Directory -Path $path
```

Omdat `$null` een constante waarde is, kunt u deze nooit overschrijven. Ik vind het niet mooi dat deze in mijn code wordt weer gegeven, maar dit wordt vaak sneller uitgevoerd dan `Out-Null` .

### <a name="redirect-to-null"></a>Omleiden naar $null

U kunt ook de omleidings operator gebruiken om uitvoer naar te verzenden `$null` .

```powershell
New-Item -Type Directory -Path $path > $null
```

Als u werkt met opdracht regel uitvoer bare bestanden die worden uitgevoerd op de verschillende stromen. U kunt alle uitvoer stromen als volgt omleiden `$null` :

```powershell
git status *> $null
```

## <a name="summary"></a>Samenvatting

Ik heb veel aan de slag op deze ene en ik weet dat dit artikel meer is gefragmenteerd dan het meeste van mijn diepe Dives. Dat komt doordat `$null` waarden in een groot aantal verschillende locaties in Power shell kunnen worden pop-ups en alle nuances zijn specifiek voor de locatie waar u deze kunt vinden. Ik hoop dat u dit niet kunt doen met een beter inzicht in en een duidelijk beeld van `$null` de meer onduidelijke scenario's die u kunt uitvoeren in.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[goede post]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System. Management. Automation. internal. AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
