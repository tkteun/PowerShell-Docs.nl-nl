---
description: Hierin worden de Opera tors beschreven die worden ondersteund door Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: 88369b1ccf3157e56dd5266784d8ca16e55b1f8f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892518"
---
# <a name="about-operators"></a>Opera tors

## <a name="short-description"></a>Korte beschrijving
Hierin worden de Opera tors beschreven die worden ondersteund door Power shell.

## <a name="long-description"></a>Lange beschrijving

Een operator is een taal element dat u kunt gebruiken in een opdracht of expressie.
Power shell ondersteunt diverse typen Opera tors die u helpen bij het manipuleren van waarden.

### <a name="arithmetic-operators"></a>Rekenkundige operators

Reken kundige Opera tors ( `+` ,, `-` `*` , `/` ) gebruiken `%` om waarden in een opdracht of expressie te berekenen. Met deze opera tors kunt u waarden toevoegen, aftrekken, vermenigvuldigen of delen, en de rest (modulus) van een delings bewerking berekenen.

De operator voor optellen voegt elementen samen. De operator voor vermenigvuldigen retourneert het opgegeven aantal exemplaren van elk element. U kunt reken kundige Opera tors gebruiken voor elk .net-type dat deze implementeert, zoals: `Int` ,, `String` `DateTime` , `Hashtable` en arrays.

Bitsgewijze Opera tors ( `-band` , `-bor` ,,, `-bxor` `-bnot` `-shl` , `-shr` ) bewerken de bits patronen in waarden.

Zie [about_Arithmetic_Operators](about_Arithmetic_Operators.md)voor meer informatie.

### <a name="assignment-operators"></a>Toewijzings operatoren

Gebruik toewijzings operatoren (,,,, `=` `+=` `-=` `*=` `/=` , `%=` ) om waarden toe te wijzen, te wijzigen of toe te voegen aan variabelen. U kunt reken kundige Opera tors combi neren met toewijzing om het resultaat van de reken kundige bewerking aan een variabele toe te wijzen.

Zie [about_Assignment_Operators](about_Assignment_Operators.md)voor meer informatie.

### <a name="comparison-operators"></a>Vergelijkingsoperators

Gebruik vergelijkings operatoren ( `-eq` ,, `-ne` `-gt` , `-lt` , `-le` , `-ge` ) om waarden en test voorwaarden te vergelijken. U kunt bijvoorbeeld twee teken reeks waarden vergelijken om te bepalen of ze gelijk zijn.

De vergelijkings operators omvatten ook Opera tors waarmee patronen in tekst worden gezocht of vervangen. De `-match` `-notmatch` Opera tors (,, `-replace` ) gebruiken reguliere expressies en `-like` `-notlike` gebruiken joker tekens `*` .

Containment-vergelijkings operatoren bepalen of een test waarde wordt weer gegeven in een referentieset ( `-in` ,, `-notin` `-contains` , `-notcontains` ).

Type vergelijkings operatoren ( `-is` , `-isnot` ) bepalen of een object van een bepaald type is.

Zie [about_Comparison_Operators](about_Comparison_Operators.md)voor meer informatie.

### <a name="logical-operators"></a>Logische operators

Gebruik logische Opera tors (,,, `-and` `-or` `-xor` `-not` , `!` ) om voorwaardelijke instructies te verbinden met één complexe voorwaardelijke waarde. U kunt bijvoorbeeld een logische `-and` operator gebruiken om een object filter te maken met twee verschillende voor waarden.

Zie [about_Logical_Operators](about_logical_operators.md)voor meer informatie.

### <a name="redirection-operators"></a>Omleidings operatoren

Gebruik de omleidings operatoren ( `>` ,, `>>` `2>` , `2>>` en `2>&1` ) om de uitvoer van een opdracht of expressie naar een tekst bestand te verzenden. De omleidings operatoren werken zoals de `Out-File` cmdlet (zonder para meters), maar u kunt ook de fout uitvoer omleiden naar opgegeven bestanden. U kunt ook de- `Tee-Object` cmdlet gebruiken om uitvoer om te leiden.

Zie [about_Redirection](about_Redirection.md) voor meer informatie.

### <a name="split-and-join-operators"></a>Opera tors voor splitsen en samen voegen

De `-split` `-join` Opera tors en delen subtekenreeksen en combi neren deze. De `-split` operator splitst een teken reeks in subtekenreeksen. De `-join` operator voegt meerdere teken reeksen samen tot één teken reeks.

Zie [about_Split](about_Split.md) en [about_Join](about_Join.md)voor meer informatie.

### <a name="type-operators"></a>Type operators

Gebruik de type operators ( `-is` , `-isnot` , `-as` ) om het .NET Framework type van een object te zoeken of te wijzigen.

Zie [about_Type_Operators](about_Type_Operators.md)voor meer informatie.

### <a name="unary-operators"></a>Unaire Opera tors

Gebruik unaire Opera tors om variabelen of object eigenschappen te verhogen of verlagen en om integers in te stellen op positieve of negatieve getallen. Als u bijvoorbeeld de variabele wilt verhogen `$a` van `9` naar `10` , typt u `$a++` .

### <a name="special-operators"></a>Speciale Opera tors

Speciale Opera tors hebben specifieke use-cases die niet in een andere operator groep passen. Speciale Opera tors maken het bijvoorbeeld mogelijk om opdrachten uit te voeren, het gegevens type van een waarde te wijzigen of elementen uit een matrix op te halen.

#### <a name="grouping-operator--"></a>Operator voor groeperen `( )`

Net als in andere talen `(...)` moet de operator prioriteit in expressies worden overschreven. Bijvoorbeeld: `(1 + 2) / 3`

Er zijn echter extra problemen in Power shell.

- `(...)` met kunt u de uitvoer van een _opdracht_ laten deel uitmaken van een expressie. Bijvoorbeeld:

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- Wanneer u gebruikt als het eerste segment van een pijp lijn, verpakt u een opdracht of expressie tussen haakjes invariably resulteert in de _opsomming_ van het resultaat van de expressie. Als de haakjes een _opdracht_ teruglopen, wordt deze uitgevoerd om te volt ooien met alle uitvoer die _in het geheugen is verzameld_ voordat de resultaten via de pijp lijn worden verzonden.

#### <a name="subexpression-operator--"></a>Operator voor subexpressie `$( )`

Retourneert het resultaat van een of meer instructies. Voor één resultaat retourneert een scalaire waarde. Voor meerdere resultaten wordt een matrix geretourneerd. Gebruik deze als u een expressie binnen een andere expressie wilt gebruiken. Bijvoorbeeld, om de resultaten van de opdracht in een teken reeks expressie in te sluiten.

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a>Operator voor subexpressie van matrix `@( )`

Retourneert het resultaat van een of meer instructies als een matrix. Als er slechts één item is, heeft de matrix slechts één lid.

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="hash-table-literal-syntax-"></a>Hash-tabel letterlijke syntaxis `@{}`

Net als bij de subexpressie van de matrix wordt deze syntaxis gebruikt voor het declareren van een hash-tabel.
Zie [about_Hash_Tables](about_Hash_Tables.md)voor meer informatie.

#### <a name="call-operator-"></a>Aanroep operator `&`

Voert een opdracht, script of script blok uit. Met de oproep operator, ook wel bekend als aanroep operator, kunt u opdrachten uitvoeren die zijn opgeslagen in variabelen en vertegenwoordigd door teken reeksen of script blokken. De aanroep operator wordt uitgevoerd in een onderliggend bereik. Zie [about_Scopes](about_Scopes.md)voor meer informatie over bereiken.

In dit voor beeld wordt een opdracht in een teken reeks opgeslagen en uitgevoerd met de aanroep operator.

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

De aanroep operator parseert geen teken reeksen. Dit betekent dat u geen opdracht parameters binnen een teken reeks kunt gebruiken wanneer u de aanroep operator gebruikt.

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

Met de cmdlet [invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan code worden uitgevoerd die fouten tijdens het parseren van de aanroep operator veroorzaakt.

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

U kunt de aanroep operator gebruiken om scripts uit te voeren met hun bestands namen. In het onderstaande voor beeld ziet u een script bestandsnaam die spaties bevat. Wanneer u het script probeert uit te voeren, geeft Power shell in plaats daarvan de inhoud weer van de teken reeks met de bestands naam. Met de aanroep operator kunt u de inhoud van de teken reeks met de bestands naam uitvoeren.

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

Zie [about_Script_Blocks](about_Script_Blocks.md)voor meer informatie over script blokken.

#### <a name="background-operator-"></a>Operator voor achtergrond `&`

Voert de pijp lijn voordat deze op de achtergrond wordt uitgevoerd in een Power shell-taak. Deze operator werkt op dezelfde manier als de UNIX-besturings operator en-teken ( `&` ), waarbij de opdracht wordt uitgevoerd vóór asynchroon in subshell als een taak.

Deze operator is functioneel gelijk aan `Start-Job` . Standaard start de operator achtergrond de taken in de huidige werkmap van de aanroeper die de parallelle taken heeft gestart. In het volgende voor beeld wordt het basis gebruik van de taak operator achtergrond gedemonstreerd.

```powershell
Get-Process -Name pwsh &
```

Deze opdracht is functioneel gelijk aan het volgende gebruik van `Start-Job` :

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

Net als `Start-Job` : de `&` operator background retourneert een- `Job` object. Dit object kan worden gebruikt met `Receive-Job` en `Remove-Job` , net alsof u hebt gebruikt `Start-Job` om de taak te starten.

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

De `&` operator voor de achtergrond is ook een instructie-eind punt, net als bij de UNIX-besturings operator en-teken ( `&` ). Hierdoor kunt u aanvullende opdrachten aanroepen na de `&` operator achtergrond. In het volgende voor beeld ziet u de aanroep van extra opdrachten na de `&` operator achtergrond.

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

Dit komt overeen met het volgende script:

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

Als u meerdere opdrachten wilt uitvoeren, elk in een eigen achtergrond proces, maar op één regel, plaatst u gewoon `&` tussen en na elk van de opdrachten.

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

Zie [about_Jobs](about_Jobs.md)voor meer informatie over Power shell-taken.

#### <a name="cast-operator--"></a>Conversie operator `[ ]`

Hiermee worden objecten geconverteerd of beperkt tot het opgegeven type. Als de objecten niet kunnen worden geconverteerd, wordt er door Power shell een fout gegenereerd.

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

Een cast kan ook worden uitgevoerd wanneer een variabele is toegewezen aan met behulp van de [cast-notatie](about_Variables.md).

#### <a name="comma-operator-"></a>Komma operator `,`

Als binaire operator maakt de komma een matrix of voegt deze toe aan de matrix die wordt gemaakt. In de expressie modus, als een unaire operator, maakt de komma een matrix met slechts één lid. Plaats de komma vóór het lid.

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

Omdat `Write-Object` een argument wordt verwacht, moet u de expressie tussen haakjes plaatsen.

#### <a name="dot-sourcing-operator-"></a>Operator voor punt sourcing `.`

Voert een script uit in het huidige bereik, zodat alle functies, aliassen en variabelen die het script maakt, worden toegevoegd aan het huidige bereik en bestaande worden overschreven. De door het script gedeclareerde para meters worden variabelen. Para meters waarvoor geen waarde is opgegeven, worden variabelen zonder waarde. De automatische variabele blijft echter `$args` behouden.

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> De operator stip sourcing wordt gevolgd door een spatie. Gebruik de ruimte om het punt te onderscheiden van het punt ( `.` ) dat staat voor de huidige map.
>
> In het volgende voor beeld wordt het Sample.ps1 script in de huidige map uitgevoerd in het huidige bereik.
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a>Indelings operator `-f`

Teken reeksen met de indelings methode van teken reeks objecten. Voer de notatie teken reeks links van de operator in en de objecten die aan de rechter kant van de operator moeten worden opgemaakt.

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

Als u de accolades ( `{}` ) in de opgemaakte teken reeks moet blijven staan, kunt u ze weglaten door de accolades te verdubbelen.

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

Zie de methode [String. Format](/dotnet/api/system.string.format) en [samengestelde opmaak](/dotnet/standard/base-types/composite-formatting)voor meer informatie.

#### <a name="index-operator--"></a>Index operator `[ ]`

Selecteert objecten uit geïndexeerde verzamelingen, zoals matrices en hash-tabellen. Matrix indexen zijn gebaseerd op nul, dus het eerste object wordt geïndexeerd als `[0]` . Voor matrices (alleen) kunt u ook negatieve indexen gebruiken om de laatste waarden op te halen. Hash-tabellen worden geïndexeerd op basis van de sleutel waarde.

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

#### <a name="pipeline-operator-"></a>Pijplijn operator `|`

Verzendt ("sluizen") de uitvoer van de opdracht die voorafgaat aan de opdracht die erop volgt. Wanneer de uitvoer meer dan één object (een ' verzameling ') bevat, verzendt de pijplijn operator een voor een per keer de objecten.

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a>Pijplijn keten operators `&&` en `||`

Voer voorwaardelijk de rechter pijplijn uit op basis van het succes van de pijp lijn aan de linkerkant.

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

Zie [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md)voor meer informatie.

#### <a name="range-operator-"></a>De operator Range `..`

Vertegenwoordigt de sequentiële gehele getallen in een matrix met gehele getallen, op basis van een bovenste en onderste grens.

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

U kunt ook bereiken maken in omgekeerde volg orde.

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

Vanaf Power shell 6 werkt de bereik operator met **tekens** en **gehele getallen**.

Als u een reeks tekens wilt maken, plaatst u de grens tekens in aanhalings teken.

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

#### <a name="member-access-operator-"></a>Operator voor leden toegang `.`

Toegang tot de eigenschappen en methoden van een object. De lidnaam mag een expressie zijn.

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a>Statische lid-operator `::`

Hiermee worden de statische eigenschappen en methoden van een .NET Framework klasse aangeroepen. Als u de statische eigenschappen en methoden van een object wilt zoeken, gebruikt u de statische para meter van de `Get-Member` cmdlet.  De lidnaam mag een expressie zijn.

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a>Ternaire operator `? <if-true> : <if-false>`

U kunt de ternaire operator als vervanging voor de instructie gebruiken `if-else` in eenvoudige voorwaardelijke cases.

Zie [about_If](about_If.md)voor meer informatie.

#### <a name="null-coalescing-operator-"></a>Null-samenvoegings operator `??`

De operator null-samenvoeging `??` retourneert de waarde van de linkeroperand als deze niet null is. Anders wordt de rechter operand geëvalueerd en wordt het resultaat geretourneerd. De `??` operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

In het volgende voor beeld wordt de rechter operand niet geëvalueerd.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a>De toewijzings operator null-samen voegen `??=`

De operator voor het samen voegen van Null-samen voegen `??=` wijst de waarde van de rechter operand alleen aan de linkeroperand toe als de linkeroperand wordt geëvalueerd als null. De `??=` operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

In het volgende voor beeld wordt de rechter operand niet geëvalueerd.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a>Null-voorwaardelijke Opera tors `?.` en `?[]`

> [!NOTE]
> Dit is een experimentele functie. Zie [about_Experimental_Features](about_Experimental_Features.md)voor meer informatie.

Een null-voorwaardelijke operator past een leden toegang, `?.` , of element toegang, `?[]` alleen aan de operand toe als die operand resulteert in niet-null; anders wordt Null geretourneerd.

In het volgende voor beeld wordt de waarde van **propnaam** geretourneerd.

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

In het volgende voor beeld wordt Null geretourneerd zonder dat u toegang probeert te krijgen tot **de naam van de lidnaam.**

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

En als de operand null is, wordt het element niet geopend en wordt Null geretourneerd.

```PowerShell
$a = $null
${a}?[0]
```

> [!NOTE]
> Aangezien Power shell `?` een deel van de naam van de variabele toestaat, is formele specificatie van de naam van de variabele vereist voor het gebruik van deze opera tors. Het is dus nood zakelijk om `{}` de namen van variabelen te gebruiken, zoals `${a}` of wanneer `?` het een deel van de naam van de variabele is `${a?}` .
>
> De variabele naam syntaxis van `${<name>}` mag niet worden verward met de `$()` operator voor subexpressie. Zie de sectie variabele name van [about_Variables](about_Variables.md#variable-names-that-include-special-characters)voor meer informatie.

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
