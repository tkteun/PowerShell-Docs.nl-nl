---
description: Hierin worden matrices beschreven. Dit zijn gegevens structuren die zijn ontworpen om verzamelingen van items op te slaan.
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 15ab7bb28fc9dd9262ba71b5cc1347a609837d9c
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412977"
---
# <a name="about-arrays"></a>Over matrices

## <a name="short-description"></a>Korte beschrijving
Hierin worden matrices beschreven. Dit zijn gegevens structuren die zijn ontworpen om verzamelingen van items op te slaan.

## <a name="long-description"></a>Lange beschrijving

Een matrix is een gegevens structuur die is ontworpen voor het opslaan van een verzameling items.
De items kunnen van hetzelfde type of van verschillende typen zijn.

Vanaf Windows Power Shell 3,0 heeft een verzameling van nul of één object enkele eigenschappen van matrices.

## <a name="creating-and-initializing-an-array"></a>Een matrix maken en initialiseren

Als u een matrix wilt maken en initialiseren, moet u meerdere waarden toewijzen aan een variabele. De waarden die zijn opgeslagen in de matrix, worden gescheiden door een komma en gescheiden door de toewijzings operator () van de naam van de variabele `=` .

Als u bijvoorbeeld een matrix wilt maken `$A` met de naam die de zeven numerieke waarden (int) van 22, 5, 10, 8, 12, 9 en 80 bevat, typt u:

```powershell
$A = 22,5,10,8,12,9,80
```

De komma kan ook worden gebruikt voor het initialiseren van een enkele item matrix door de komma vóór het afzonderlijke item te plaatsen.

Als u bijvoorbeeld een enkele item matrix wilt maken met `$B` de naam met de waarde 7, typt u:

```powershell
$B = ,7
```

U kunt ook een matrix maken en initialiseren met behulp van de operator Range ( `..` ).
In het volgende voor beeld wordt een matrix gemaakt met de waarden 5 tot en met 8.

```powershell
$C = 5..8
```

Als gevolg hiervan `$C` bevat vier waarden: 5, 6, 7 en 8.

Als er geen gegevens type is opgegeven, maakt Power shell elke matrix als een object Matrix (**System. object []**). Gebruik de methode **gettype ()** om het gegevens type van een matrix te bepalen. Als u bijvoorbeeld het gegevens type van de matrix wilt bepalen `$A` , typt u:

```powershell
$A.GetType()
```

Als u een sterk getypeerde matrix wilt maken, dat wil zeggen een matrix die alleen waarden van een bepaald type kan bevatten, kunt u de variabele als een matrix type casten, zoals **String []**, **Long []** of **Int32 []**. Als u een matrix wilt casten, moet u vóór de naam van de variabele een matrix type opgeven tussen vier Kante haken. Als u bijvoorbeeld een matrix van 32-bits geheel getal met de naam `$ia` vier gehele getallen (1500, 2230, 3350 en 4000) wilt maken, typt u:

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

Als gevolg hiervan kan de `$ia` matrix alleen gehele getallen bevatten.

U kunt matrices maken die worden geconverteerd naar een ondersteund type in het Microsoft .NET Framework. De objecten die `Get-Process` worden opgehaald om processen te vertegenwoordigen, zijn bijvoorbeeld van het type **System. Diagnostics. process** . Als u een sterk getypeerde matrix met proces objecten wilt maken, voert u de volgende opdracht in:

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a>De subexpression-operator van de matrix

De operator subexpression van matrix maakt een matrix van de instructies hierin. Ongeacht het resultaat van de instructie in de operator, plaatst de operator deze in een matrix. Zelfs als er geen of een object is.

De syntaxis van de matrix operator is als volgt:

```syntax
@( ... )
```

U kunt de operator matrix gebruiken om een matrix van nul of één object te maken. Bijvoorbeeld:

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

De matrix operator is handig in scripts wanneer u objecten ophaalt, maar niet weet hoeveel objecten u krijgt. Bijvoorbeeld:

```powershell
$p = @(Get-Process Notepad)
```

Zie [about_Operators](about_Operators.md)voor meer informatie over de subexpression-operator van de matrix.

## <a name="accessing-and-using-array-elements"></a>Matrix elementen openen en gebruiken

### <a name="reading-an-array"></a>Een matrix lezen

U kunt naar een matrix verwijzen met behulp van de naam van de variabele. Als u alle elementen in de matrix wilt weer geven, typt u de naam van de matrix. `$a`Als er bijvoorbeeld een matrix is met gehele getallen 0, 1, 2, tot 9; typt u:

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

U kunt naar de elementen in een matrix verwijzen met behulp van een index, te beginnen bij positie 0. Plaats het index nummer tussen haakjes. Als u bijvoorbeeld het eerste element in de matrix wilt weer geven `$a` , typt u:

```powershell
$a[0]
```

```Output
0
```

Als u het derde element wilt weer geven in de `$a` matrix, typt u:

```powershell
$a[2]
```

```Output
2
```

U kunt een deel van de matrix ophalen met behulp van een bereik operator voor de index. Als u bijvoorbeeld de tweede tot vijfde elementen van de matrix wilt ophalen, typt u:

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

Het aantal negatieve getallen vanaf het einde van de matrix. Bijvoorbeeld: '-1 ' verwijst naar het laatste element van de matrix. Als u de laatste drie elementen van de matrix wilt weer geven, typt u in oplopende volg orde index:

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

Als u negatieve indexen in aflopende volg orde typt, verandert de uitvoer.

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

Wees echter voorzichtig bij het gebruik van deze notatie. De notatie loopt van de eind grens naar het begin van de matrix.

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

Daarnaast moet u er ook `$a[0..-2]` voor kiezen om te verwijzen naar alle elementen van de matrix, met uitzonde ring van de laatste. Deze verwijst naar de elementen First, last en Second naar laatste in de matrix.

U kunt de plus operator ( `+` ) gebruiken om een bereik te combi neren met een lijst met elementen in een matrix. Als u bijvoorbeeld de elementen op index posities 0, 2 en 4 tot en met 6 wilt weer geven, typt u:

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

Als u meerdere bereiken en afzonderlijke elementen wilt weer geven, kunt u ook de operator plus gebruiken. Als u bijvoorbeeld elementen wilt weer geven van nul tot twee, vier tot zes en het element met het achtste positie type:

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a>Herhalingen over matrix elementen

U kunt ook herhalings constructies, zoals ForEach, voor en tijdens lussen, gebruiken om te verwijzen naar de elementen in een matrix. Als u bijvoorbeeld een ForEach-lus wilt gebruiken om de elementen in de matrix weer te geven `$a` , typt u:

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

De foreach-lus doorloopt de matrix en retourneert elke waarde in de matrix totdat het einde van de matrix wordt bereikt.

De for-lus is handig wanneer u prestatie meter items verhoogt tijdens het onderzoeken van de elementen in een matrix. Als u bijvoorbeeld een for-lus wilt gebruiken om elke andere waarde in een matrix te retour neren, typt u:

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

U kunt een while-lus gebruiken om de elementen in een matrix weer te geven totdat een gedefinieerde voor waarde niet meer waar is. Als u bijvoorbeeld de elementen in de matrix wilt weer geven `$a` terwijl de index van de matrix kleiner is dan 4, typt u:

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a>Eigenschappen van matrices

### <a name="count-or-length-or-longlength"></a>Aantal of lengte of LongLength

Gebruik de `Length` eigenschap of de alias om te bepalen hoeveel items zich in een matrix bevinden `Count` . `Longlength` is handig als de matrix meer dan 2.147.483.647 elementen bevat.

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a>Positie

Retourneert het aantal dimensies in de matrix. De meeste matrices in Power Shell hebben één dimensie. Zelfs wanneer u denkt dat u een multidimensionale matrix bouwt zoals in het volgende voor beeld:

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

"`$a rank: $($a.Rank)"
"`$a length: $($a.Length)"
"`$a length: $($a.Length)"
"Process `$a[2][1]: $($a[2][1].ProcessName)"
```

In dit voor beeld maakt u een eendimensionale matrix die andere matrices bevat. Dit wordt ook wel een _gekartelde matrix_ genoemd. De eigenschap **Rank** heeft aangetoond dat dit eendimensionale is. Voor toegang tot items in een gekartelde matrix moeten de indexen tussen vier Kante haken ( `[]` ) staan.

```Output
$a rank: 1
$a length: 3
$a[2] length: 348
Process $a[2][1]: AcroRd32
```

Multidimensionale matrices worden opgeslagen in de [volg orde row-major](https://wikipedia.org/wiki/Row-_and_column-major_order). In het volgende voor beeld ziet u hoe u een echte multidimensionale matrix maakt.

```powershell
[string[,]]$rank2 = [string[,]]::New(3,2)
$rank2.rank
$rank2.Length
$rank2[0,0] = 'a'
$rank2[0,1] = 'b'
$rank2[1,0] = 'c'
$rank2[1,1] = 'd'
$rank2[2,0] = 'e'
$rank2[2,1] = 'f'
$rank2[1,1]
```

```Output
2
6
d
```

Als u toegang wilt krijgen tot items in een multidimensionale matrix, scheidt u de indexen met een komma ( `,` ) binnen één set haken ( `[]` ).

Bij sommige bewerkingen op een multidimensionale matrix, zoals replicatie en samen voegen, moet de matrix worden afgevlakt. Met afvlakking wordt de matrix omgezet in een eendimensionale matrix van het type unperked. De resulterende matrix neemt alle elementen in de volg orde van de rij-groot op. Kijk eens naar het volgende voorbeeld:

```powershell
$a = "red",$true
$b = (New-Object 'int[,]' 2,2)
$b[0,0] = 10
$b[0,1] = 20
$b[1,0] = 30
$b[1,1] = 40
$c = $a + $b
$a.GetType().Name
$b.GetType().Name
$c.GetType().Name
$c
```

In de uitvoer ziet u `$c` een eendimensionale matrix met daarin de items van `$a` en in de `$b` volg orde van de rij-Major.

```output
Object[]
Int32[,]
Object[]
red
True
10
20
30
40
```

## <a name="methods-of-arrays"></a>Methoden van matrices

### <a name="clear"></a>Veilig

Hiermee stelt u alle element waarden in op de _standaard waarde_ van het element type van de matrix.
De methode Clear () stelt de grootte van de matrix niet opnieuw in.

In het volgende voor beeld `$a` is een matrix met objecten.

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

In dit voor beeld `$intA` wordt expliciet getypt om gehele getallen te bevatten.

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a>ForEach

Hiermee kunt u alle elementen in de matrix herhalen en een bepaalde bewerking uitvoeren voor elk element van de matrix.

De ForEach-methode heeft verschillende Overloads die verschillende bewerkingen uitvoeren.

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a>ForEach (script Block-expressie)

#### <a name="foreachscriptblock-expression-object-arguments"></a>ForEach (script Block-expressie, object [] argumenten)

Deze methode is toegevoegd in Power shell v4.

> [!NOTE]
> De syntaxis vereist het gebruik van een script blok. Haakjes zijn optioneel als de script Block de enige para meter is. Er mag ook geen spatie tussen de methode en het haakje openen of de accolade worden geplaatst.

In het volgende voor beeld ziet u hoe u de methode foreach gebruikt. In dit geval is de bedoeling de vier Kante waarde van de elementen in de matrix te genereren.

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

Net als de `-ArgumentList` para meter van `ForEach-Object` `arguments` kan de para meter een matrix met argumenten door geven aan een script blok dat is geconfigureerd om deze te accepteren.

Zie [about_Splatting](about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

#### <a name="foreachtype-converttotype"></a>ForEach (type convertToType)

De `ForEach` methode kan worden gebruikt om de elementen snel te casten naar een ander type. in het volgende voor beeld ziet u hoe u een lijst met teken reeks datums converteert naar een `[DateTime]` type.

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a>ForEach (String PropertyName)

#### <a name="foreachstring-propertyname-object-newvalue"></a>ForEach (String PropertyName, object [] newValue)

De `ForEach` methode kan ook worden gebruikt om snel eigenschaps waarden op te halen of in te stellen voor elk item in de verzameling.

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a>ForEach (String methode)

#### <a name="foreachstring-methodname-object-arguments"></a>ForEach (String Method methode, object [] argumenten)

Ten slotte `ForEach` kunnen methoden worden gebruikt om een methode uit te voeren voor elk item in de verzameling.

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

Net als de `-ArgumentList` para meter van `ForEach-Object` `arguments` kan de para meter een matrix met argumenten door geven aan een script blok dat is geconfigureerd om deze te accepteren.

> [!NOTE]
> Starten in Windows Power Shell 3,0 het ophalen van eigenschappen en het uitvoeren van methoden voor elk item in een verzameling kan ook worden uitgevoerd met behulp van methoden van scalaire objecten en verzamelingen. hier vindt u meer informatie over deze [about_methods](about_methods.md).

### <a name="where"></a>Waar

Hiermee kunt u de elementen van de matrix filteren of selecteren. Het script moet resulteren in iets anders dan: nul (0), lege teken reeks `$false` of `$null` voor het element dat moet worden weer gegeven na de `Where`

Er is één definitie voor de `Where` methode.

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> De syntaxis vereist het gebruik van een script blok. Haakjes zijn optioneel als de script Block de enige para meter is. Er mag ook geen spatie tussen de methode en het haakje openen of de accolade worden geplaatst.

De `Expression` script Block is vereist voor het filteren, het `mode` optionele argument biedt aanvullende selectie mogelijkheden en `numberToReturn` met het optionele argument kunt u het aantal items dat door het filter wordt geretourneerd, beperken.

De acceptabele waarden voor `mode` zijn:

- Standaard (0)-alle items retour neren
- Eerste (1)-retourneert het eerste item
- Last (2)-het laatste item retour neren
- SkipUntil (3)-items overs Laan tot voor waarde is ingesteld op ' True ', de resterende items retour neren
- Tot (4): alle items retour neren totdat de voor waarde waar is
- Splitsen (5)-een matrix van twee elementen retour neren
  - Het eerste element bevat overeenkomende items
  - Het tweede element bevat de resterende items

In het volgende voor beeld ziet u hoe u alle oneven getallen uit de matrix selecteert.

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

In dit voor beeld ziet u hoe u de teken reeksen selecteert die niet leeg zijn.

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a>Standaard

`Default`In de modus worden items gefilterd met behulp van de `Expression` script Block.

Als er een `numberToReturn` is opgegeven, wordt hiermee het maximum aantal items opgegeven dat moet worden geretourneerd.

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> Zowel de `Default` modus als de `First` modus retour neren de eerste ( `numberToReturn` ) items en kunnen door elkaar worden gebruikt.

#### <a name="last"></a>Laatste

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a>SkipUntil

`SkipUntil`In de modus worden alle objecten in een verzameling overgeslagen totdat een object het filter voor script blok expressies door gegeven. Vervolgens worden **alle** resterende verzamelings items geretourneerd zonder ze te testen. _Er wordt slechts één door gegeven item getest_.

Dit betekent dat de geretourneerde verzameling zowel _door gegeven_ als _niet-door gegeven_ items bevat die niet zijn getest.

Het aantal geretourneerde items kan worden beperkt door een waarde door te geven aan het `numberToReturn` argument.

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a>Totdat

De modus `Until` keert de `SkipUntil` modus om.  **Alle** items in een verzameling worden geretourneerd totdat een item de script blok expressie door gegeven. Zodra een item de script Block-expressie heeft _door gegeven_ , stopt de methode met het `Where` verwerken van items.

Dit betekent dat u de eerste set van _niet-door gegeven_ items van de `Where` methode ontvangt. _Nadat_ één item is door gegeven, wordt de rest niet getest of geretourneerd.

Het aantal geretourneerde items kan worden beperkt door een waarde door te geven aan het `numberToReturn` argument.

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> `Until`Met en `SkipUntil` zonder een batch met items te testen.
>
> `Until` retourneert de items **vóór** de eerste _fase_.
>
> `SkipUntil` retourneert alle items **na** de eerste _fase_, inclusief het eerste door gegeven item.

#### <a name="split"></a>Splitsen

De `Split` modus splitst of groepeert items in twee afzonderlijke verzamelingen. Gebruikers die de script Block-expressie door geven, en de expressies die dat niet doen.

Als er een `numberToReturn` is opgegeven, bevat de eerste verzameling de _door gegeven_ items, niet om de opgegeven waarde te overschrijden.

De resterende objecten, zelfs degene die het expressie filter **door geven** , worden geretourneerd in de tweede verzameling.

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a>De leden van een matrix ophalen

Gebruik de para meter **input object** van de cmdlet om de eigenschappen en methoden van een matrix op te halen, zoals de eigenschap length en de methode **WaardeInstellen** `Get-Member` .

Wanneer u een matrix naar verplaatst `Get-Member` , verzendt Power shell de items per keer en `Get-Member` retourneert het type van elk item in de matrix (dubbele waarden worden genegeerd).

Wanneer u de para meter **input object** gebruikt, `Get-Member` retourneert de leden van de matrix.

Met de volgende opdracht worden bijvoorbeeld de leden van de `$a` matrix variabele opgehaald.

```powershell
Get-Member -InputObject $a
```

U kunt ook de leden van een matrix ophalen door een komma (,) te typen vóór de waarde die is gesluisd met de `Get-Member` cmdlet. De komma maakt de matrix het tweede item in een matrix met matrices. Power shell Pipet de matrix per keer en `Get-Member` retourneert de leden van de matrix. Net als de volgende twee voor beelden.

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a>Een matrix bewerken

U kunt de elementen in een matrix wijzigen, een element aan een matrix toevoegen en de waarden van twee matrices combi neren in een derde matrix.

Als u de waarde van een bepaald element in een matrix wilt wijzigen, geeft u de naam van de matrix en de index op van het element dat u wilt wijzigen, en gebruikt u vervolgens de toewijzings operator ( `=` ) om een nieuwe waarde voor het element op te geven. Als u bijvoorbeeld de waarde van het tweede item in de `$a` matrix (index positie 1) op 10 wilt wijzigen, typt u:

```powershell
$a[1] = 10
```

U kunt ook de **WaardeInstellen** -methode van een matrix gebruiken om een waarde te wijzigen. In het volgende voor beeld wordt de tweede waarde (index positie 1) van de `$a` matrix gewijzigd in 500:

```powershell
$a.SetValue(500,1)
```

U kunt de `+=` operator gebruiken om een element aan een matrix toe te voegen. In het volgende voor beeld ziet u hoe u een element aan de matrix kunt toevoegen `$a` .

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> Wanneer u de `+=` operator gebruikt, maakt Power shell in feite een nieuwe matrix met de waarden van de oorspronkelijke matrix en de toegevoegde waarde. Dit kan leiden tot prestatie problemen als de bewerking meerdere keren wordt herhaald of de grootte van de matrix te groot is.

Het is niet eenvoudig om elementen uit een matrix te verwijderen, maar u kunt wel een nieuwe matrix maken die alleen geselecteerde elementen van een bestaande matrix bevat. Als u bijvoorbeeld de `$t` matrix met alle elementen in de matrix wilt maken, met `$a` uitzonde ring van de waarde op index positie 2, typt u:

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

Als u twee matrices wilt combi neren tot één matrix, gebruikt u de plus operator ( `+` ). In het volgende voor beeld worden twee matrices gemaakt, gecombineerd en wordt de resulterende gecombineerde matrix weer gegeven.

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

Als gevolg hiervan bevat de `$z` matrix 1, 3, 5 en 9.

Als u een matrix wilt verwijderen, wijst u een waarde `$null` toe aan de matrix. Met de volgende opdracht wordt de matrix in de `$a` variabele verwijderd.

`$a = $null`

U kunt de cmdlet ook gebruiken `Remove-Item` , maar een waarde van `$null` is sneller, vooral voor grote matrices.

## <a name="arrays-of-zero-or-one"></a>Matrices van nul of één

Vanaf Windows Power Shell 3,0 heeft een verzameling van nul of één object de eigenschap Count en length. U kunt ook indexeren naar een matrix van één object. Deze functie helpt u bij het voor komen van script fouten die optreden wanneer een opdracht die een verzameling verwacht minder dan twee items ontvangt.

In de volgende voor beelden wordt deze functie gedemonstreerd.

### <a name="zero-objects"></a>Nul objecten

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a>Eén object

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a>Ondersteuning voor het indexeren van System. tuple-objecten

Power shell 6,1 heeft de ondersteuning toegevoegd voor geïndexeerde toegang van **tuple** -objecten, vergelijkbaar met matrices.
Bijvoorbeeld:

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

In tegens telling tot matrices en andere verzamelings objecten worden **tuple** -objecten beschouwd als één enkel object wanneer ze worden door gegeven via de pijp lijn of door para meters die matrices van objecten ondersteunen.

Zie [System. tuple](/dotnet/api/system.tuple)voor meer informatie.

## <a name="see-also"></a>Zie ook

- [about_Assignment_Operators](about_Assignment_Operators.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Operators](about_Operators.md)
- [about_For](about_For.md)
- [about_Foreach](about_Foreach.md)
- [about_While](about_While.md)

