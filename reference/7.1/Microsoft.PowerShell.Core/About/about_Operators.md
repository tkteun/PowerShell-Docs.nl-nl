---
description: Beschrijft de operators die worden ondersteund door PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: 416a0a5abfaa354b0fe960ac4ac8784d5247585c
ms.sourcegitcommit: 96efcc9613740449940b371b34c3baafb675b1ed
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107907391"
---
# <a name="about-operators"></a>Over operators

## <a name="short-description"></a>Korte beschrijving
Beschrijft de operators die worden ondersteund door PowerShell.

## <a name="long-description"></a>Lange beschrijving

Een operator is een taalelement dat u kunt gebruiken in een opdracht of expressie.
PowerShell ondersteunt verschillende typen operators om waarden te bewerken.

### <a name="arithmetic-operators"></a>Rekenkundige operators

Gebruik rekenkundige operators ( , , , , , ) om waarden in een opdracht of expressie `+` `-` te `*` `/` `%` berekenen. Met deze operators kunt u waarden toevoegen, aftrekken, vermenigvuldigen of delen en de rest (modulus) van een delingsbewerking berekenen.

Met de optellingsoperator worden elementen samenvoegt. De vermenigvuldigingsoperator retourneert het opgegeven aantal kopieën van elk element. U kunt rekenkundige operators gebruiken voor elk .NET-type dat ze implementeert, zoals: `Int` , , , en `String` `DateTime` `Hashtable` Matrices.

Bitsgewijze operators ( `-band` , , , , , , ) bewerken de `-bor` `-bxor` `-bnot` `-shl` `-shr` bitpatronen in waarden.

Zie voor meer informatie [about_Arithmetic_Operators](about_Arithmetic_Operators.md).

### <a name="assignment-operators"></a>Toewijzingsoperators

Gebruik toewijzingsoperators ( , , , , , , ) om waarden toe te wijzen, te wijzigen of toe te wijzen `=` `+=` aan `-=` `*=` `/=` `%=` variabelen. U kunt rekenkundige operators combineren met toewijzing om het resultaat van de rekenkundige bewerking toe te wijzen aan een variabele.

Zie voor meer informatie [about_Assignment_Operators](about_Assignment_Operators.md).

### <a name="comparison-operators"></a>Vergelijkingsoperators

Gebruik vergelijkingsoperators ( `-eq` , , , , , , ) om waarden en `-ne` `-gt` `-lt` `-le` `-ge` testvoorwaarden te vergelijken. U kunt bijvoorbeeld twee tekenreekswaarden vergelijken om te bepalen of ze gelijk zijn.

De vergelijkingsoperators bevatten ook operators die patronen in tekst zoeken of vervangen. De operators ( `-match` , , ) gebruiken reguliere `-notmatch` `-replace` expressies en ( , ) `-like` gebruiken `-notlike` jokertekens. `*`

Vergelijkingsoperators voor insluiting bepalen of een testwaarde wordt weergegeven in een referentieset ( `-in` , , , , `-notin` `-contains` `-notcontains` ).

Typevergelijkingsoperators ( `-is` , ) bepalen of een object van een bepaald type `-isnot` is.

Zie voor meer informatie [about_Comparison_Operators](about_Comparison_Operators.md).

### <a name="logical-operators"></a>Logische operators

Gebruik logische operators ( , , , , , ) om voorwaardelijke instructies `-and` te verbinden met één complexe `-or` `-xor` `-not` `!` voorwaarde. U kunt bijvoorbeeld een logische operator gebruiken om een objectfilter met `-and` twee verschillende voorwaarden te maken.

Zie voor meer informatie [about_Logical_Operators.](about_logical_operators.md)

### <a name="redirection-operators"></a>Omleidingsoperators

Gebruik omleidingsoperators ( , , , , en ) om de uitvoer van een opdracht of expressie naar `>` `>>` een `2>` `2>>` `2>&1` tekstbestand te verzenden. De omleidingsoperators werken als de cmdlet (zonder parameters), maar u kunt ook `Out-File` foutuitvoer omleiden naar opgegeven bestanden. U kunt ook de `Tee-Object` cmdlet gebruiken om uitvoer om te leiden.

Zie voor meer informatie [about_Redirection](about_Redirection.md)

### <a name="split-and-join-operators"></a>Operators splitsen en lid worden

De `-split` operators en delen en combineren `-join` subtekenreeksen. De `-split` operator splitst een tekenreeks in subtekenreeksen. Met `-join` de operator worden meerdere tekenreeksen in één tekenreeks samenvoegd.

Zie voor meer informatie [about_Split](about_Split.md) en [about_Join.](about_Join.md)

### <a name="type-operators"></a>Typeoperators

Gebruik de typeoperators ( , , ) om het type .NET Framework `-is` object te zoeken of te `-isnot` `-as` wijzigen.

Zie voor meer informatie [about_Type_Operators](about_Type_Operators.md).

### <a name="unary-operators"></a>Unaire operators

Gebruik de unaire `++`  operators en om waarden te verhogen of te `--` degraderen en `-` voor negatie. Als u bijvoorbeeld de variabele wilt verhogen `$a` van `9` naar , `10` typt u `$a++` .

Zie voor meer informatie [about_Arithmetic_Operators](about_Arithmetic_Operators.md).

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

- Wanneer een opdracht of expressie tussen haakjes wordt gebruikt als het  eerste segment van een pijplijn, wordt het resultaat van de expressie altijd opsnoemd. Als de haakjes een opdracht _verpakken,_ wordt deze uitgevoerd tot voltooiing met alle uitvoer die _in_ het geheugen is verzameld voordat de resultaten via de pijplijn worden verzonden.

#### <a name="subexpression-operator--"></a>Subexpressieoperator `$( )`

Retourneert het resultaat van een of meer instructies. Retourneert een scalaire waarde voor één resultaat. Retourneert een matrix voor meerdere resultaten. Gebruik dit als u een expressie binnen een andere expressie wilt gebruiken. Als u bijvoorbeeld de resultaten van de opdracht wilt insluiten in een tekenreeksexpressie.

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a>Matrixsubexpressieoperator `@( )`

Retourneert het resultaat van een of meer instructies als een matrix. Als er slechts één item is, heeft de matrix slechts één lid.

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a>Letterlijke syntaxis van hash-tabel `@{}`

Net als bij de subexpressie van de matrix wordt deze syntaxis gebruikt om een hash-tabel te declaren.
Zie voor meer informatie [about_Hash_Tables](about_Hash_Tables.md).

#### <a name="call-operator-"></a>Operator voor aanroepen `&`

Voert een opdracht- of scriptblok uit. Met de aanroepoperator, ook wel de aanroepoperator genoemd, kunt u opdrachten uitvoeren die zijn opgeslagen in variabelen en worden vertegenwoordigd door tekenreeksen of scriptblokken. De aanroepoperator wordt uitgevoerd in een onderliggend bereik. Zie voor meer informatie over [about_Scopes.](about_Scopes.md)

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
```

De [cmdlet Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan code uitvoeren die parseringsfouten veroorzaakt bij het gebruik van de aanroepoperator.

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

Zie voor meer informatie over scriptblokken [about_Script_Blocks](about_Script_Blocks.md).

#### <a name="background-operator-"></a>Achtergrondoperator `&`

Voert de pijplijn vóór deze op de achtergrond uit in een PowerShell-taak. Deze operator werkt op dezelfde manier als de UNIX-besturingsoperator ampersand ( ), waarmee de opdracht vóór deze asynchroon in subshell als een taak `&` wordt uitgevoerd.

Deze operator is functioneel equivalent aan `Start-Job` . De achtergrondoperator start de taken standaard in de huidige werkmap van de aanroeper die de parallelle taken heeft gestart. In het volgende voorbeeld wordt het basisgebruik van de operator voor achtergrondfuncties gedemonstreerd.

```powershell
Get-Process -Name pwsh &
```

Deze opdracht is functioneel equivalent aan het volgende gebruik van `Start-Job` :

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

Net als `Start-Job` retourneert `&` de achtergrondoperator een `Job` -object. Dit object kan worden gebruikt met `Receive-Job` en , net zoals u hebt gebruikt om de taak te `Remove-Job` `Start-Job` starten.

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

De `&` achtergrondoperator is ook een instructie-eindafding, net als de UNIX-besturingsoperator ampersand ( `&` ). Hiermee kunt u aanvullende opdrachten aanroepen na de `&` achtergrondoperator. In het volgende voorbeeld wordt het aanroepen van aanvullende opdrachten na de `&` achtergrondoperator gedemonstreerd.

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

Dit is gelijk aan het volgende script:

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

Als u meerdere opdrachten wilt uitvoeren, elk in hun eigen achtergrondproces, maar allemaal op één regel, plaats dan tussen en `&` na elk van de opdrachten.

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

Zie Voor meer informatie over PowerShell-taken [about_Jobs](about_Jobs.md).

#### <a name="cast-operator--"></a>Cast-operator `[ ]`

Converteert of beperkt objecten tot het opgegeven type. Als de objecten niet kunnen worden geconverteerd, genereert PowerShell een fout.

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
> In het volgende voorbeeld wordt het Sample.ps1 in de huidige map uitgevoerd in het huidige bereik.
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a>Opmaakoperator `-f`

Maakt tekenreeksen op met behulp van de indelingsmethode van tekenreeksobjecten. Voer de notatiereeks in aan de linkerkant van de operator en de objecten die aan de rechterkant van de operator moeten worden opgemaakt.

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

Zie de methode [String.Format](/dotnet/api/system.string.format) en Samengestelde opmaak [voor meer informatie.](/dotnet/standard/base-types/composite-formatting)

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

Verzendt ("pipes") de uitvoer van de opdracht die voorafgaat aan de opdracht die volgt. Wanneer de uitvoer meer dan één object (een 'verzameling') bevat, verzendt de pijplijnoperator de objecten één voor één.

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a>Pijplijnketenoperators `&&` en `||`

Voer de pijplijn aan de rechterkant voorwaardelijk uit op basis van het succes van de pijplijn aan de linkerkant.

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

Zie voor meer informatie [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md).

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

Vanaf PowerShell 6 werkt de bereikoperator met **tekens** en **gehele getallen.**

Als u een bereik van tekens wilt maken, sluit u de grenstekens tussen aanhalingstekens.

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a>Operator voor lidtoegang `.`

Heeft toegang tot de eigenschappen en methoden van een object. De lidnaam kan een expressie zijn.

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a>Statische lidoperator `::`

Roept de statische eigenschappen en methoden van een .NET Framework aan. Gebruik de statische parameter van de cmdlet om de statische eigenschappen en methoden van een object `Get-Member` te vinden.  De naam van het lid kan een expressie zijn.

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a>Ternaire operator `? <if-true> : <if-false>`

U kunt de ternaire operator gebruiken als vervanging voor de `if-else` instructie in eenvoudige voorwaardelijke gevallen.

Zie voor meer informatie [about_If](about_If.md).

#### <a name="null-coalescing-operator-"></a>Operator voor null-sameneten `??`

De operator null-coalescing retourneert de waarde van de linkerope `??` operand als deze niet null is. Anders wordt de rechterope operand geëvalueerd en wordt het resultaat ervan retourneert. De `??` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

In het volgende voorbeeld wordt de rechteropeen niet geëvalueerd.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a>Toewijzingsoperator null-samen te sluiten `??=`

De toewijzingsoperator null-coalescing wijst de waarde van de rechteropend alleen toe aan de linkerope operand als de operand aan de linkerkant als null wordt `??=` geëvalueerd. De `??=` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

In het volgende voorbeeld wordt de rechteropeen niet geëvalueerd.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a>Null-voorwaardelijke operators `?.` en `?[]`

> [!NOTE]
> Deze functie is verplaatst van experimenteel naar standaard in PowerShell 7.1.

Een null-voorwaardelijke operator past een bewerking voor lidtoegang, , of elementtoegang, alleen toe op de operand als die operand als niet-null wordt geëvalueerd; anders wordt `?.` `?[]` null geretourneerd.

Omdat PowerShell deel mag uitmaken van de naam van de variabele, is een formele specificatie van de naam van de variabele `?` vereist voor het gebruik van deze operators. Het is dus vereist om te gebruiken `{}` rond de namen van variabelen, zoals of wanneer deel uitmaakt van de `${a}` `?` variabelenaam `${a?}` .

In het volgende voorbeeld wordt de waarde **van PropName** geretourneerd.

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

In het volgende voorbeeld wordt null geretourneerd, zonder toegang te krijgen tot de **lidnaam PropName.**

```powershell
$a = $null
${a}?.PropName
```

Op dezelfde manier wordt de waarde van het element geretourneerd.

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

En wanneer de operand null is, wordt het element niet toegankelijk en wordt null geretourneerd.

```PowerShell
$a = $null
${a}?[0]
```

> [!NOTE]
> Omdat PowerShell deel mag uitmaken van de naam van de variabele, is een formele specificatie van de naam van de variabele `?` vereist voor het gebruik van deze operators. Het is dus vereist om te gebruiken rond de namen van variabelen, zoals `{}` of wanneer deel uitmaakt van de `${a}` `?` variabelenaam `${a?}` .
>
> De syntaxis van de `${<name>}` variabelenaam mag niet worden verward met de `$()` operator subexpressie. Zie voor meer informatie de sectie Variabelenaam van [about_Variables](about_Variables.md#variable-names-that-include-special-characters).

## <a name="see-also"></a>Zie ook

[about_Arithmetic_Operators](about_Arithmetic_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Logical_Operators](about_logical_operators.md)

[about_Operator_Precedence](about_operator_precedence.md)

[about_Type_Operators](about_Type_Operators.md)

[about_Pipeline_Chain_Operators](about_Pipeline_Chain_Operators.md)

[about_Split](about_Split.md)

[about_Join](about_Join.md)

[about_Redirection](about_Redirection.md)
