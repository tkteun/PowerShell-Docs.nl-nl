---
description: Beschrijft de operators die worden ondersteund door PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: fecf8808bb1b92a61359d327b5f87d045f913c09
ms.sourcegitcommit: 96efcc9613740449940b371b34c3baafb675b1ed
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107907359"
---
# <a name="about-operators"></a>Over operators

## <a name="short-description"></a>Korte beschrijving
Beschrijft de operators die worden ondersteund door PowerShell.

## <a name="long-description"></a>Lange beschrijving

Een operator is een taalelement dat u kunt gebruiken in een opdracht of expressie.
PowerShell ondersteunt verschillende typen operators om waarden te bewerken.

### <a name="arithmetic-operators"></a>Rekenkundige operators

Gebruik rekenkundige operators ( `+` , , , , , , ) om waarden in een opdracht of expressie te `-` `*` `/` `%` berekenen. Met deze operators kunt u waarden toevoegen, aftrekken, vermenigvuldigen of delen en de rest (modulus) van een delingsbewerking berekenen.

Met de optellingsoperator worden elementen samenvoegt. De vermenigvuldigingsoperator retourneert het opgegeven aantal kopieën van elk element. U kunt rekenkundige operators gebruiken voor elk .NET-type dat ze implementeert, zoals: `Int` , , , en `String` `DateTime` `Hashtable` Matrices.

Bitsgewijze operators ( `-band` , , , , , , , ) bewerken de `-bor` `-bxor` `-bnot` `-shl` `-shr` bitpatronen in waarden.

Zie voor meer informatie [about_Arithmetic_Operators.](about_Arithmetic_Operators.md)

### <a name="assignment-operators"></a>Toewijzingsoperators

Gebruik toewijzingsoperators ( , , , , , , ) om waarden toe te wijzen, te wijzigen of toe te wijzen `=` `+=` aan `-=` `*=` `/=` `%=` variabelen. U kunt rekenkundige operators combineren met toewijzing om het resultaat van de rekenkundige bewerking toe te wijzen aan een variabele.

Zie voor meer informatie [about_Assignment_Operators](about_Assignment_Operators.md).

### <a name="comparison-operators"></a>Vergelijkingsoperators

Gebruik vergelijkingsoperators ( `-eq` , , , , , , ) om waarden en `-ne` `-gt` `-lt` `-le` `-ge` testvoorwaarden te vergelijken. U kunt bijvoorbeeld twee tekenreekswaarden vergelijken om te bepalen of ze gelijk zijn.

De vergelijkingsoperators bevatten ook operators die patronen in tekst zoeken of vervangen. De operators ( `-match` , , ) gebruiken reguliere `-notmatch` `-replace` expressies en ( , ) `-like` gebruiken `-notlike` jokertekens. `*`

Vergelijkingsoperators voor insluitingen bepalen of een testwaarde wordt weergegeven in een referentieset ( `-in` `-notin` , , , `-contains` `-notcontains` ).

Typevergelijkingsoperators ( `-is` , ) bepalen of een object van een bepaald type `-isnot` is.

Zie voor meer informatie [about_Comparison_Operators](about_Comparison_Operators.md).

### <a name="logical-operators"></a>Logische operators

Gebruik logische operators ( , , , , , ) om voorwaardelijke instructies `-and` te verbinden met één complexe `-or` `-xor` `-not` `!` voorwaarde. U kunt bijvoorbeeld een logische operator gebruiken om een objectfilter met `-and` twee verschillende voorwaarden te maken.

Zie voor meer informatie [about_Logical_Operators](about_logical_operators.md).

### <a name="redirection-operators"></a>Omleidingsoperators

Gebruik omleidingsoperators ( , , , , en ) om de uitvoer van een opdracht of expressie naar `>` `>>` een `2>` `2>>` `2>&1` tekstbestand te verzenden. De omleidingsoperators werken als de cmdlet (zonder parameters), maar u kunt ook foutuitvoer `Out-File` omleiden naar opgegeven bestanden. U kunt ook de `Tee-Object` cmdlet gebruiken om de uitvoer om te leiden.

Zie voor meer informatie [about_Redirection](about_Redirection.md)

### <a name="split-and-join-operators"></a>Operators splitsen en lid worden

De `-split` operators en delen en combineren `-join` subtekenreeksen. De `-split` operator splitst een tekenreeks in subtekenreeksen. Met `-join` de operator worden meerdere tekenreeksen in één tekenreeks samenvoegd.

Zie voor meer informatie [about_Split](about_Split.md) en [about_Join](about_Join.md).

### <a name="type-operators"></a>Typeoperators

Gebruik de typeoperators ( , , ) om het type .NET Framework `-is` object te zoeken of te `-isnot` `-as` wijzigen.

Zie voor meer informatie [about_Type_Operators](about_Type_Operators.md).

### <a name="unary-operators"></a>Unaire operators

Gebruik de unaire operators en om waarden te verhogen `++` `--` of te degraderen en `-` voor negatie. Als u bijvoorbeeld de variabele wilt verhogen `$a` van `9` naar , `10` typt u `$a++` .

Zie voor meer informatie [about_Arithmetic_Operators.](about_Arithmetic_Operators.md)

### <a name="special-operators"></a>Speciale operators

Speciale operators hebben specifieke gebruiksgevallen die niet in een andere operatorgroep passen. Met speciale operators kunt u bijvoorbeeld opdrachten uitvoeren, het gegevenstype van een waarde wijzigen of elementen ophalen uit een matrix.

#### <a name="grouping-operator--"></a>Groeperingsoperator `( )`

Net als in andere talen dient `(...)` om de prioriteit van operatoren in expressies te overschrijven. Bijvoorbeeld: `(1 + 2) / 3`

In PowerShell zijn er echter aanvullende gedragingen.

- `(...)` met kunt u de uitvoer van een opdracht _laten_ deelnemen aan een expressie. Bijvoorbeeld:

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- Wanneer een opdracht of expressie tussen haakjes wordt gebruikt als het eerste segment van een pijplijn, leidt dat altijd tot een _enumeratie_ van het resultaat van de expressie. Als de haakjes een opdracht _verpakken,_ wordt deze uitgevoerd tot voltooiing met alle uitvoer die _in_ het geheugen is verzameld voordat de resultaten via de pijplijn worden verzonden.

> [!NOTE]
> Wanneer u een opdracht tussen haakjes verpakt, wordt de automatische variabele ingesteld op , zelfs wanneer de ingesloten `$?` opdracht zelf is ingesteld op `$true` `$?` `$false` .
> Onverwacht levert `(Get-Item /Nosuch); $?` bijvoorbeeld Waar **op.** Zie voor meer informatie `$?` [over about_Automatic_Variables](about_Automatic_Variables.md).

#### <a name="subexpression-operator--"></a>Subexpressieoperator `$( )`

Retourneert het resultaat van een of meer instructies. Retourneert een scalaire waarde voor één resultaat. Retourneert een matrix voor meerdere resultaten. Gebruik dit als u een expressie binnen een andere expressie wilt gebruiken. Als u bijvoorbeeld de resultaten van de opdracht wilt insluiten in een tekenreeksexpressie.

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a>Operator voor matrixsubexpressie `@( )`

Retourneert het resultaat van een of meer instructies als een matrix. Als er slechts één item is, heeft de matrix slechts één lid.

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a>Letterlijke syntaxis van hash-tabel `@{}`

Net als bij de matrixsubexpressie wordt deze syntaxis gebruikt om een hash-tabel te declaren.
Zie voor meer informatie [about_Hash_Tables](about_Hash_Tables.md).

#### <a name="call-operator-"></a>Operator voor aanroepen `&`

Voert een opdracht, script of scriptblok uit. Met de aanroepoperator, ook wel de aanroepoperator genoemd, kunt u opdrachten uitvoeren die zijn opgeslagen in variabelen en worden vertegenwoordigd door tekenreeksen of scriptblokken. De aanroepoperator wordt uitgevoerd in een onderliggend bereik. Zie voor meer informatie over [about_Scopes.](about_Scopes.md)

In dit voorbeeld slaat u een opdracht op in een tekenreeks en voert u deze uit met behulp van de aanroepoperator.

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

De aanroepoperator parseert geen tekenreeksen. Dit betekent dat u geen opdrachtparameters binnen een tekenreeks kunt gebruiken wanneer u de aanroepoperator gebruikt.

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
At line:1 char:2
+ & $c
+  ~~
    + CategoryInfo          : ObjectNotFound: (Get-Service -Name Spooler:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

De [invoke-expression-cmdlet](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan code uitvoeren die parseringsfouten veroorzaakt bij het gebruik van de aanroepoperator.

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

U kunt de aanroepoperator gebruiken om scripts uit te voeren met hun bestandsnamen. In het onderstaande voorbeeld ziet u een scriptbestandsnaam die spaties bevat. Wanneer u het script probeert uit te voeren, geeft PowerShell in plaats daarvan de inhoud weer van de tekenreeks met de bestandsnaam. Met de aanroepoperator kunt u de inhoud van de tekenreeks met de bestandsnaam uitvoeren.

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

Zie voor meer informatie over scriptblokken [about_Script_Blocks.](about_Script_Blocks.md)

#### <a name="cast-operator--"></a>Cast-operator `[ ]`

Converteert of beperkt objecten naar het opgegeven type. Als de objecten niet kunnen worden geconverteerd, genereert PowerShell een fout.

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

Een cast-cast kan ook worden uitgevoerd wanneer een variabele wordt toegewezen aan met behulp van [cast-notatie](about_Variables.md).

#### <a name="comma-operator-"></a>Kommaoperator `,`

Als binaire operator maakt de komma een matrix of wordt deze aan de matrix die wordt gemaakt, aan de matrix die wordt gemaakt. In de expressiemodus maakt de komma als unaire operator een matrix met slechts één lid. Plaats de komma vóór het lid.

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

Omdat `Write-Object` een argument verwacht, moet u de expressie tussen haakjes zetten.

#### <a name="dot-sourcing-operator-"></a>Operator voor puntsourcing `.`

Voert een script uit in het huidige bereik, zodat alle functies, aliassen en variabelen die door het script worden gemaakt, worden toegevoegd aan het huidige bereik, waardoor bestaande functies, aliassen en variabelen worden overschrijven. Parameters die door het script zijn gedeclareerd, worden variabelen. Parameters waarvoor geen waarde is gegeven, worden variabelen zonder waarde. De automatische variabele `$args` blijft echter behouden.

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> De operator voor puntsourcing wordt gevolgd door een spatie. Gebruik de spatie om de punt te onderscheiden van het punt ( `.` ) symbool dat de huidige map vertegenwoordigt.
>
> In het volgende voorbeeld wordt het Sample.ps1 script in de huidige map uitgevoerd in het huidige bereik.
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a>Opmaakoperator `-f`

Maakt tekenreeksen op met behulp van de indelingsmethode van tekenreeksobjecten. Voer de notatiereeks aan de linkerkant van de operator en de objecten in die aan de rechterkant van de operator moeten worden opgemaakt.

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

Als u de accolades ( ) in de opgemaakte tekenreeks wilt houden, kunt u deze escapen door de `{}` accolades te verdubbelen.

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

Zie de methode [String.Format en](/dotnet/api/system.string.format) Samengestelde opmaak [voor meer informatie.](/dotnet/standard/base-types/composite-formatting)

#### <a name="index-operator--"></a>Indexoperator `[ ]`

Selecteert objecten uit geïndexeerde verzamelingen, zoals matrices en hashtabellen. Matrixindexen zijn op nul gebaseerd, dus het eerste object wordt geïndexeerd als `[0]` . Voor matrices (alleen) kunt u ook negatieve indexen gebruiken om de laatste waarden op te halen. Hashtabellen worden geïndexeerd op sleutelwaarde.

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a>Pijplijnoperator `|`

Verzendt ("pipes") de uitvoer van de opdracht die voorafgaat aan de opdracht die volgt. Wanneer de uitvoer meer dan één object (een verzameling) bevat, verzendt de pijplijnoperator de objecten één voor één.

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a>Bereikoperator `..`

Vertegenwoordigt de sequentiële gehele getallen in een matrix met gehele getallen op een boven- en ondergrens.

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

U kunt ook in omgekeerde volgorde reeksen maken.

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

#### <a name="member-access-operator-"></a>Operator voor lidtoegang `.`

Heeft toegang tot de eigenschappen en methoden van een object. De lidnaam kan een expressie zijn.

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a>Statische lidoperator `::`

Roept de statische eigenschappen en methoden van een .NET Framework klasse aan. Als u de statische eigenschappen en methoden van een object wilt vinden, gebruikt u de parameter Statisch van de `Get-Member` cmdlet .  De naam van het lid kan een expressie zijn.

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a>Zie ook

[about_Arithmetic_Operators](about_Arithmetic_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Logical_Operators](about_logical_operators.md)

[about_Operator_Precedence](about_operator_precedence.md)

[about_Type_Operators](about_Type_Operators.md)

[about_Split](about_Split.md)

[about_Join](about_Join.md)

[about_Redirection](about_Redirection.md)
