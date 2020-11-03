---
description: Hierin worden de Opera tors beschreven voor het uitvoeren van berekeningen in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 96ca73a613c30e844fb19de29bf005480c5703d9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252637"
---
# <a name="about-arithmetic-operators"></a>Over reken kundige Opera tors

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de Opera tors beschreven voor het uitvoeren van berekeningen in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

Reken kundige Opera tors berekenen numerieke waarden. U kunt een of meer wiskundige opera toren gebruiken om waarden toe te voegen, af te trekken, te vermenigvuldigen en te delen en om de rest (modulus) van een delings bewerking te berekenen.

Daarnaast kunnen de operator voor optellen ( `+` ) en de operator voor vermenigvuldiging ( `*` ) ook worden gebruikt voor teken reeksen, matrices en hash-tabellen. De operator voor optellen voegt de invoer toe. De vermenigvuldigings operator retourneert meerdere exemplaren van de invoer. U kunt zelfs object typen in een reken kundige instructie combi neren. De methode die wordt gebruikt om de instructie te evalueren, wordt bepaald door het type van het meest linkse object in de expressie.

Vanaf Power Shell 2,0 werken alle reken kundige Opera tors met 64-bits getallen.

Vanaf Power Shell 3,0 worden de `-shr` (Shift-rechts) en `-shl` (Shift-links) toegevoegd ter ondersteuning van bitsgewijze berekeningen in Power shell.

Power shell ondersteunt de volgende reken kundige Opera tors:

|Operator|Beschrijving                       |Voorbeeld                      |
|--------|----------------------------------|-----------------------------|
| +      |Voegt gehele getallen toe; voegt       |`6 + 2`                      |
|        |Teken reeksen, matrices en hash-tabellen. |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |Trekt een waarde van een ander af  |`6 - 2`                      |
|        |waarde                             |                             |
| -      |Maakt een getal een negatief getal  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |Getallen vermenigvuldigen of teken reeksen kopiëren  |`6 * 2`                      |
|        |en arrays het opgegeven getal   |`@("!") * 4`                 |
|        |van de tijden.                         |`"!" * 3`                    |
| /      |Deelt twee waarden.               |`6 / 2`                      |
| %      |Modulus-retourneert het restant van|`7 % 2`                      |
|        |een delings bewerking.             |                             |
|-band   |Bitsgewijze AND                       |`5 -band 3`                  |
|-bniet   |Bitsgewijze NOT                       |`-bnot 5`                    |
|-Bof    |Bitsgewijze OR                        |`5 -bor 0x03`                |
|-bxor   |Bitsgewijze XOR                       |`5 -bxor 3`                  |
|-shl    |Hiermee worden bits naar links geschoven           |`102 -shl 2`                 |
|-SHR    |Hiermee worden de bits naar rechts verplaatst          |`102 -shr 2`                 |

De operator voor bitsgewijs werken alleen bij typen van gehele getallen.

## <a name="operator-precedence"></a>OPERATOR PRIORITEIT

Power shell verwerkt reken kundige Opera tors in de volgende volg orde:

|Prioriteit|Operator          |Beschrijving                            |
|----------|------------------|---------------------------------------|
|1         | `()`             |Haakjes                            |
|2         | `-`              |Voor een negatief getal of een unaire operator|
|3         | `*`, `/`, `%`    |Voor vermenigvuldiging en deling        |
|4         | `+`, `-`         |Voor optellen en aftrekken           |
|5         | `-band`, `-bnot` |Voor bitsgewijze bewerkingen                 |
|5         | `-bor`, `-bxor`  |Voor bitsgewijze bewerkingen                 |
|5         | `-shr`, `-shl`   |Voor bitsgewijze bewerkingen                 |

Power shell verwerkt de expressies van links naar rechts volgens de prioriteits regels. In de volgende voor beelden ziet u het effect van de prioriteits regels:

|Expression |Resultaat|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

De volg orde waarin in Power shell expressies worden geëvalueerd, kunnen afwijken van andere programmeer-en script talen die u hebt gebruikt. In het volgende voor beeld ziet u een gecompliceerde toewijzings instructie.

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

In dit voor beeld wordt de expressie `$a++` eerder geëvalueerd `$b[$a]` .
`$a++`Als u een evaluatie wijzigt, wordt de waarde van `$a` nadat deze is gebruikt in de instructie, `$c[$a++]` maar voordat deze wordt gebruikt in `$b[$a]` . De variabele `$a` `$b[$a]` is gelijk aan `1` , niet `0` ; daarom wijst de instructie een waarde toe aan `$b[1]` , niet `$b[0]` .

De bovenstaande code is gelijk aan:

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a>DELEN EN AFRONDEN

Wanneer het quotiënt van een delings bewerking een geheel getal is, wordt de waarde door Power shell afgerond op het dichtstbijzijnde gehele getal. Wanneer de waarde is `.5` , wordt deze afgerond op het dichtstbijzijnde even gehele getal.

In het volgende voor beeld ziet u het effect van het afronden op het dichtstbijzijnde even gehele getal.

|Expression      |Resultaat|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

U ziet hoe **_5/2_ = 2,5** wordt afgerond op **2**. Maar **_7/2_ = 3,5** wordt afgerond op **4**.

U kunt de `[Math]` klasse gebruiken om verschillende Afrondings gedrag te verkrijgen.

|                          Expression                          | Resultaat |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

Zie de methode [Math. Round](/dotnet/api/system.math.round) (Engelstalig) voor meer informatie.

## <a name="adding-and-multiplying-non-numeric-types"></a>NIET-NUMERIEKE TYPEN TOEVOEGEN EN VERMENIGVULDIGEN

U kunt cijfers, teken reeksen, matrices en hash-tabellen toevoegen. En u kunt getallen, teken reeksen en matrices vermenigvuldigen. U kunt hash-tabellen echter niet vermenigvuldigen.

Wanneer u teken reeksen, matrices of hash-tabellen toevoegt, worden de elementen samengevoegd. Wanneer u verzamelingen samenvoegt, zoals matrices of hash-tabellen, wordt er een nieuw object gemaakt met daarin de objecten uit beide verzamelingen. Als u hash-tabellen met dezelfde sleutel probeert samen te voegen, mislukt de bewerking.

Met de volgende opdrachten worden bijvoorbeeld twee matrices gemaakt en vervolgens toegevoegd:

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

U kunt ook reken kundige bewerkingen uitvoeren op objecten van verschillende typen.
De bewerking die Power shell uitvoert, wordt bepaald door het Microsoft .NET Framework-type van het meest linkse object in de bewerking. Power shell probeert alle objecten in de bewerking te converteren naar het .NET Framework type van het eerste object. Als de objecten zijn geconverteerd, wordt de bewerking uitgevoerd die geschikt is voor het .NET Framework type van het eerste object. Als een van de objecten niet kan worden geconverteerd, mislukt de bewerking.

In de volgende voor beelden wordt het gebruik van de Opera tors voor toevoegen en vermenigvuldigen gedemonstreerd. in bewerkingen die verschillende object typen bevatten. Aannemen `$array = 1,2,3` :

|Expression       |Resultaat                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |`1`,`2`,`3`,`16`       |
|`$array + "file"`|`1`,`2`,`3`,`file`     |
|`$array * 2`     |`1`,`2`,`3`,`1`,`2`,`3`|
|`"file" * 3`     |`filefilefile`         |

Omdat de methode die wordt gebruikt om-instructies te evalueren, wordt bepaald door het meest linkse object, is toevoeging en vermenigvuldiging in Power shell niet strikt Commutative. Is bijvoorbeeld `(a + b)` niet altijd gelijk aan `(b + a)` en is `(ab)` niet altijd gelijk aan `(ba)` .

In de volgende voor beelden ziet u dit principe:

|Expression   |Resultaat                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |+ 16 + "bestand" "                                       |

Hash-tabellen zijn iets anders. U kunt hash-tabellen toevoegen aan een andere hash-tabel, op voor waarde dat de toegevoegde hash-tabellen geen dubbele sleutels hebben.

In het volgende voor beeld ziet u hoe u hash-tabellen aan elkaar kunt toevoegen.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

In het volgende voor beeld wordt een fout gegenereerd omdat een van de sleutels in beide hash-tabellen is gedupliceerd.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

U kunt ook een hash-tabel aan een matrix toevoegen. en de gehele hash-tabel wordt een item in de matrix.

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

U kunt echter geen ander type toevoegen aan een hash-tabel.

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

Hoewel de optellings operatoren erg nuttig zijn, gebruikt u de toewijzings operatoren om elementen toe te voegen aan hash-tabellen en-matrices. Zie [about_assignment_operators](about_Assignment_Operators.md)voor meer informatie. De volgende voor beelden gebruiken de `+=` toewijzings operator om items toe te voegen aan een matrix:

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a>TYPE CONVERSIE OM RESULTAAT TE BIEDEN

Power shell selecteert automatisch het .NET Framework numerieke type dat het resultaat het beste oplevert zonder dat de precisie verloren gaat. Bijvoorbeeld:

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

Als het resultaat van een bewerking te groot is voor het type, wordt het type van het resultaat uitgebreid met het resultaat, zoals in het volgende voor beeld:

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

Het type van het resultaat is niet noodzakelijkerwijs hetzelfde als een van de operanden. In het volgende voor beeld kan de negatieve waarde niet worden geconverteerd naar een niet-ondertekend geheel getal en is het niet-ondertekende gehele getal te groot om te worden geconverteerd naar `Int32` :

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

In dit voor beeld `Int64` kan dit elk type bevatten.

Het `System.Decimal` type is een uitzonde ring. Als een van beide operanden het decimale type heeft, is het resultaat van het decimale type. Als het resultaat te groot is voor het decimale type, wordt dit niet geconverteerd naar double. In plaats daarvan treedt er een fout op.

|Expression               |Resultaat                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a>WISKUNDIGE OPERA TORS EN VARIABELEN

U kunt ook reken kundige Opera tors met variabelen gebruiken. De Opera tors handelen op de waarden van de variabelen. In de volgende voor beelden wordt het gebruik van reken kundige Opera tors met variabelen gedemonstreerd:

| Expression                                    |Resultaat      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a>WISKUNDIGE OPERA TORS EN OPDRACHTEN

Normaal gesp roken gebruikt u de reken kundige Opera tors in expressies met getallen, teken reeksen en matrices. U kunt echter ook reken kundige Opera tors gebruiken met de objecten die door opdrachten worden geretourneerd en met de eigenschappen van deze objecten.

In de volgende voor beelden ziet u hoe u wiskundige Opera tors gebruikt in expressies met Power shell-opdrachten:

```powershell
(get-date) + (new-timespan -day 1)
```

De operator voor haakjes afdwingt de evaluatie van de `get-date` cmdlet en de evaluatie van de `new-timespan -day 1` cmdlet-expressie, in die volg orde. Beide resultaten worden vervolgens toegevoegd met behulp van de `+` operator.

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

In de bovenstaande expressie wordt elk proces werk ruimte ( `$_.ws` ) vermenigvuldigd met `2` ; en wordt het resultaat vergeleken met `50mb` om te zien of het groter is dan dat.

## <a name="bitwise-operators"></a>Bitsgewijze Opera tors

Power shell ondersteunt de standaard bitsgewijze Opera Tors, waaronder bitsgewijze-en ( `-bAnd` ), de inclusieve en exclusieve BITSGEWIJZE or-Opera tors ( `-bOr` en `-bXor` ) en bitsgewijze-not ( `-bNot` ).

Vanaf Power Shell 2,0 werken alle bitsgewijze Opera tors met 64-bits geheel getal.

Vanaf Power Shell 3,0 worden de `-shr` (Shift-rechts) en `-shl` (Shift-links) geïntroduceerd voor de ondersteuning van bitsgewijze berekeningen in Power shell.

Power shell ondersteunt de volgende bitsgewijze Opera tors.

| Operator | Beschrijving            | Expression   | Resultaat |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | Bitsgewijze AND            | `10 -band 3` | 2      |
| `-bor`   | Bitsgewijze OR (inclusief) | `10 -bor 3`  | 11     |
| `-bxor`  | Bitsgewijze OR (exclusief) | `10 -bxor 3` | 9      |
| `-bnot`  | Bitsgewijze NOT            | `-bNot 10`   | -11    |
| `-shl`   | Shift-links             | `102 -shl 2` | 408    |
| `-shr`   | Shift-rechts            | `102 -shr 1` | 51     |

Bitsgewijze Opera tors handelen op de binaire indeling van een waarde. De bits-structuur voor het nummer 10 is bijvoorbeeld 00001010 (op basis van 1 byte) en de bit-structuur voor het nummer 3 is 00000011. Wanneer u een bitsgewijze operator gebruikt om 10 tot 3 te vergelijken, worden de afzonderlijke bits in elke byte vergeleken.

In een bitsgewijze AND-bewerking wordt de resulterende bit ingesteld op 1 alleen wanneer beide invoer bits 1 zijn.

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

In een bitsgewijze of (inclusief) bewerking wordt de resulterende bit ingesteld op 1 wanneer een van beide of beide invoer bits 1 zijn. De resulterende bit wordt alleen ingesteld op 0 als beide invoer bits zijn ingesteld op 0.

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

In een bitsgewijze of (exclusieve) bewerking wordt de resulterende bit ingesteld op 1 alleen als één invoer bit 1 is.

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

De operator Bitsgewijze NOT is een unaire operator die de binaire complement waarde produceert. Een bit van 1 is ingesteld op 0 en een bit van 0 is ingesteld op 1.

Bijvoorbeeld, de binaire complement van 0 is-1, het Maxi maal niet-ondertekende gehele getal (0xFFFFFFFF) en het binaire complement van-1 is 0.

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

In een bitsgewijze bewerking met een bitsgewijs verplaatsen, worden alle bits ' n ' naar links verplaatst, waarbij ' n ' de waarde van de rechter operand is. Er wordt een nul ingevoegd op de locatie.

Wanneer de linkeroperand een geheel getal (32-bits) is, bepaalt de onderste 5 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.

Wanneer de linkeroperand een lange (64-bits) waarde heeft, bepaalt de onderste 6 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.

|Expression |Resultaat|Binair resultaat|
|-----------|------|-------------|
|`21 -shl 0`|21    |0001 0101    |
|`21 -shl 1`|42    |0010 1010    |
|`21 -shl 2`|84    |0101 0100    |

In een bitsgewijs-rechts bewerking worden alle bits ' n ' naar rechts verplaatst, waarbij ' n ' wordt opgegeven door de rechter operand. Met de operator Shift-Right (-SHR) wordt een nul ingevoegd op de meest linkse positie wanneer een positieve of niet-ondertekende waarde naar rechts wordt geschoven.

Wanneer de linkeroperand een geheel getal (32-bits) is, bepaalt de onderste 5 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.

Wanneer de linkeroperand een lange (64-bits) waarde heeft, bepaalt de onderste 6 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.

|Expression              |Resultaat      |Binair     |Bovenaanzicht         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | 21         | 0001 0101 | 0x15       |
|`21 -shr 1`             | 10         | 0000 1010 | 0x0A       |
|`21 -shr 2`             | 5          | 0000 0101 | 0x05       |
|`21 -shr 31`            | 0          | 0000 0000 | 0x00       |
|`21 -shr 32`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 64`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 65`            | 10         | 0000 1010 | 0x0A       |
|`21 -shr 66`            | 5          | 0000 0101 | 0x05       |
|`[int]::MaxValue -shr 1`| 1073741823 |           | 0x3FFFFFFF |
|`[int]::MinValue -shr 1`| -1073741824|           | 0xC0000000 |
|`-1 -shr 1`             | -1         |           | 0xFFFFFFFF |

## <a name="see-also"></a>ZIE OOK

- [about_arrays](about_Arrays.md)
- [about_assignment_operators](about_Assignment_Operators.md)
- [about_comparison_operators](about_Comparison_Operators.md)
- [about_hash_tables](about_Hash_Tables.md)
- [about_operators](about_Operators.md)
- [about_variables](about_Variables.md)
- [Ophalen datum](xref:Microsoft.PowerShell.Utility.Get-Date)
- [Nieuw-time span](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
