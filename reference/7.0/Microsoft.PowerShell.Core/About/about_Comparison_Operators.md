---
description: Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.
Locale: en-US
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: a89ab612a7f0fe518f97a4d037956df14546740d
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/21/2021
ms.locfileid: "98620112"
---
# <a name="about-comparison-operators"></a>Over vergelijkings operatoren

## <a name="short-description"></a>Korte beschrijving

Met de vergelijkings operatoren in Power shell kunt u twee waarden vergelijken of elementen van een verzameling filteren op basis van een invoer waarde.

## <a name="long-description"></a>Lange beschrijving

Vergelijkings operatoren bieden u de mogelijkheid waarden te vergelijken of waarden te vinden die overeenkomen met opgegeven patronen. Power shell bevat de volgende vergelijkings operatoren:

|    Type     |   Operator   |              Vergelijkings test              |
| ----------- | ------------ | ----------------------------------------- |
| Gelijkheid    | -eq          | is gelijk aan                                    |
|             | -ne          | niet gelijk aan                                |
|             | -gt          | groter dan                              |
|             | -ge          | groter dan of gelijk aan                     |
|             | -lt          | kleiner dan                                 |
|             | -Le          | kleiner dan of gelijk aan                        |
| Matching    | -like        | teken reeks komt overeen met Joker patroon           |
|             | -notlike     | teken reeks komt niet overeen met Joker patroon    |
|             | -match       | teken reeks komt overeen met regex-patroon              |
|             | -notmatch    | teken reeks komt niet overeen met regex-patroon       |
| Vervanging | -vervangen     | vervangt teken reeksen die overeenkomen met een regex-patroon |
| Containment | -contains    | verzameling bevat een waarde               |
|             | -notcontains | verzameling bevat geen waarde       |
|             | -in          | waarde bevindt zich in een verzameling                  |
|             | -notin       | waarde bevindt zich niet in een verzameling              |
| Type        | -is          | beide objecten zijn van hetzelfde type            |
|             | -isnot       | de objecten zijn niet van hetzelfde type         |

## <a name="common-features"></a>Algemene functies

Standaard zijn alle vergelijkings operatoren niet hoofdletter gevoelig. Als u een vergelijkings operator hoofdletter gevoelig wilt maken, moet u een `c` na de toevoegen `-` . `-ceq`Is bijvoorbeeld de hoofdletter gevoelige versie van `-eq` . Voeg een before toe om de hoofdletter gevoeligheid expliciet te maken `i` `-` . `-ieq`Is bijvoorbeeld de expliciete niet-hoofdletter gevoelige versie van `-eq` .

Wanneer de invoer van een operator een scalaire waarde is, retourneert de operator een **Boole** -waarde. Wanneer de invoer een verzameling is, retourneert de operator de elementen van de verzameling die overeenkomen met de rechter waarde van de expressie.
Als er geen overeenkomsten in de verzameling zijn, retour neren vergelijkings operatoren een lege matrix. Bijvoorbeeld:

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

Er zijn enkele uitzonde ringen:

- De containment-en type-Opera tors retour neren altijd een **Booleaanse** waarde
- De `-replace` operator retourneert het vervangings resultaat
- De `-match` `-notmatch` Opera tors en vullen ook de `$Matches` Automatische variabele

## <a name="equality-operators"></a>Gelijkheidsoperatoren

### <a name="-eq-and--ne"></a>-EQ en-ne

Wanneer de linkerkant scalair is, `-eq` retourneert **waar** als de rechter kant een exacte overeenkomst heeft, anders `-eq` wordt **False** geretourneerd. `-ne` doet het tegenovergestelde; Wanneer beide zijden overeenkomen, wordt **False** geretourneerd. anders `-ne` wordt waar geretourneerd.

Voorbeeld:

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

Wanneer de linkerkant een verzameling is, `-eq` retourneert de leden die aan de rechter kant overeenkomen, terwijl `-ne` deze worden gefilterd.

Voorbeeld:

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

Deze opera tors verwerken alle elementen van de verzameling. Voorbeeld:

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

De gelijkheids operatoren accepteren twee objecten, niet alleen een scalair of verzameling.
Maar het vergelijkings resultaat is niet gegarandeerd dat dit zinvol is voor de eind gebruiker.
In het volgende voor beeld wordt het probleem gedemonstreerd.

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

In dit voor beeld hebben we twee objecten met identieke eigenschappen gemaakt. Het resultaat van de gelijkheids test is dan **Onwaar** , omdat deze verschillende objecten zijn. Als u vergelijk bare klassen wilt maken, moet u [System. \<T> IEquatable][2] in uw klasse implementeren. In het volgende voor beeld ziet u de gedeeltelijke implementatie van een **MyFileInfoSet** -klasse die [System. \<T> IEquatable][2] implementeert en twee eigenschappen, **bestand** en **grootte** heeft. De `Equals()` methode retourneert True als de bestands-en grootte-eigenschappen van twee **MyFileInfoSet** -objecten hetzelfde zijn.

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

Een prominent voor beeld van het vergelijken van wille keurige objecten is om erachter te komen of ze null zijn. Maar als u wilt bepalen of een variabele is `$null` , moet u `$null` aan de linkerkant van de gelijkheids operator. Als u deze aan de rechter kant gebruikt, heeft dat niet de verwachte.

U kunt bijvoorbeeld `$a` een matrix met null-elementen maken:

```powershell
$a = 1, 2, $null, 4, $null, 6
```

De volgende tests die `$a` niet null zijn.

```powershell
$null -ne $a
```

```output
False
```

De volgende bestanden zijn echter alle null-elementen van `$a` :

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a>-gt,-ge,-lt en-Le

`-gt`, `-ge` , `-lt` en `-le` gedragen zich op dezelfde manier. Wanneer beide zijden scalair zijn, retour neren ze **waar** of **Onwaar** , afhankelijk van de mate waarin de twee zijden elkaar vergelijken:

| Operator | Retourneert waar als...                   |
| -------- | -------------------------------------- |
| -gt      | De linkerkant is groter          |
| -ge      | De linkerkant is groter of gelijk aan |
| -lt      | De linkerkant is kleiner          |
| -Le      | De linkerkant is kleiner of gelijk aan |

In de volgende voor beelden retour neren alle instructies waar.

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> In de meeste programmeer talen is de operator groter dan `>` . In Power shell wordt dit teken gebruikt voor omleiding. Zie [about_Redirection][3]voor meer informatie.

Wanneer de linkerkant een verzameling is, vergelijken deze opera tors elk lid van de verzameling met de rechter kant. Afhankelijk van hun logica, kunnen ze het lid blijven of negeren.

Voorbeeld:

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

Deze opera tors werken met elke klasse die [System. IComparable][1]implementeert.

Voorbeelden:

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

In het volgende voor beeld ziet u dat er geen symbool is op een American QWERTY-toetsen bord dat na ' a ' wordt gesorteerd. Er wordt een set met al deze symbolen aan de `-gt` operator gevoed om ze te vergelijken met ' a '. De uitvoer is een lege matrix.

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

Als de twee zijden van de Opera tors niet redelijk vergelijkbaar zijn, verhogen deze opera tors een fout die niet wordt beëindigd.

## <a name="matching-operators"></a>Overeenkomende Opera tors

De overeenkomende Opera tors ( `-like` ,, `-notlike` `-match` en `-notmatch` ) vinden elementen die overeenkomen of niet overeenkomen met een opgegeven patroon. Het patroon voor `-like` en `-notlike` is een Joker teken expressie (die `*` , `?` en `[ ]` ) en `-match` `-notmatch` een reguliere expressie (regex) accepteert.

De syntaxis is:

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

Wanneer de invoer van deze opera tors een scalaire waarde is, retour neren ze een **Booleaanse** waarde. Wanneer de invoer een verzameling waarden is, retour neren de Opera tors overeenkomende leden. Als er geen overeenkomsten in een verzameling zijn, retour neren de Opera tors een lege matrix.

### <a name="-like-and--notlike"></a>-like en-notlike

`-like` en `-notlike` gedragen zich op dezelfde manier als `-eq` en `-ne` , maar de rechter kant kan een teken reeks met [joker tekens](about_Wildcards.md)zijn.

Voorbeeld:

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a>-Match and-notmatch

`-match` en `-notmatch` gebruik reguliere expressies om te zoeken naar een patroon in de waarden aan de linkerkant. Reguliere expressies kunnen overeenkomen met complexe patronen zoals e-mail adressen, UNC-paden of geformatteerde telefoon nummers. De teken reeks aan de rechter kant moet voldoen aan de regels voor [reguliere expressies](about_Regular_Expressions.md) .

Scalaire voor beelden:

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

Als de invoer een verzameling is, retour neren de Opera tors de overeenkomende leden van die verzameling.

Voor beelden van verzamelingen:

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

`-match` en `-notmatch` ondersteunen regex Capture-groepen. Telkens wanneer ze worden uitgevoerd, wordt de `$Matches` Automatische variabele overschreven. Wanneer `<input>` is een verzameling de `$Matches` variabele `$null` . `$Matches` is een **hashtabel** die altijd een sleutel met de naam ' 0 ' heeft, waarin de volledige overeenkomst wordt opgeslagen. Als de reguliere expressie opname groepen bevat, `$Matches` bevat de extra sleutels voor elke groep.

Voorbeeld:

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie.

## <a name="replacement-operator"></a>Vervangings operator

### <a name="replacement-with-regular-expressions"></a>Vervangen door reguliere expressies

Net als `-match` : de `-replace` operator gebruikt reguliere expressies om het opgegeven patroon te vinden. Maar in tegens telling tot `-match` , worden de overeenkomsten vervangen door een andere opgegeven waarde.

Syntaxis:

```
<input> -replace <regular-expression>, <substitute>
```

De operator vervangt alle of een deel van een waarde met de opgegeven waarde met reguliere expressies. U kunt de operator gebruiken voor veel beheer taken, zoals het wijzigen van de naam van bestanden. Met de volgende opdracht worden bijvoorbeeld de bestandsnaam extensies van alle bestanden gewijzigd `.txt` in `.log` :

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

Standaard `-replace` is de operator niet hoofdletter gevoelig. Gebruik om het hoofdletter gevoelig te maken `-creplace` . Gebruik om het expliciet niet hoofdletter gevoelig te maken `-ireplace` .

Voorbeelden:

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a>Vervangingen van reguliere expressies

Het is ook mogelijk om reguliere expressies te gebruiken om tekst dynamisch te vervangen met opname groepen en vervangingen. Er kan in de teken reeks naar vastleg groepen worden verwezen `<substitute>` met het `$` teken voor het dollar teken () voor de groeps-id.

In het volgende voor beeld `-replace` accepteert de operator een gebruikers naam in de vorm van `DomainName\Username` en wordt geconverteerd naar de `Username@DomainName` indeling:

```powershell
$SearchExp = '^(?<Username>[\w-.]+)\\(?<DomainName>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> Het `$` teken heeft syntatic-rollen in Power shell en reguliere expressies:
>
> - Tussen dubbele aanhalings tekens in Power shell worden variabelen aangeduid en fungeert als een operator voor subexpressie.
> - In regex-Zoek reeksen geeft het einde van de regel aan
> - In regex-vervangings teken reeksen worden vastgelegde groepen als zodanig aangeduid, moet u ervoor zorgen dat u de reguliere expressies tussen enkele aanhalings tekens plaatst of een apostroffen- `` ` `` teken () voor de tekst plaatst.

Bijvoorbeeld:

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

`$$` in regex duidt een letterlijke teken reeks aan `$` . Dit wordt `$$` in de vervangings teken reeks toegevoegd aan een letterlijke waarde `$` in de resulterende vervanging. Bijvoorbeeld:

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

Zie [about_Regular_Expressions](about_Regular_Expressions.md) en [vervangingen in reguliere expressies][4]voor meer informatie.

### <a name="substituting-in-a-collection"></a>Vervangen in een verzameling

Wanneer de `<input>` naar de `-replace` operator een verzameling is, past Power shell de vervanging toe op elke waarde in de verzameling. Bijvoorbeeld:

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a>Vervanging met een script blok

In Power shell 6 en hoger `-replace` accepteert de operator ook een script blok dat de vervanging uitvoert. Het script blok wordt één keer voor elke overeenkomst uitgevoerd.

Syntaxis:

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

Gebruik in het-script blok de `$_` Automatische variabele voor toegang tot de invoer tekst die wordt vervangen en andere nuttige informatie. Het klassen type van deze variabele is [System. Text. RegularExpressions. match][2].

In het volgende voor beeld wordt elke reeks van drie cijfers vervangen door de teken equivalenten. Het script blok wordt uitgevoerd voor elke set met drie cijfers die moeten worden vervangen.

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a>Containment-Opera tors

De containment-Opera tors ( `-contains` ,, `-notcontains` `-in` en `-notin` ) zijn vergelijkbaar met de gelijkheids operatoren, behalve dat ze altijd een **Booleaanse** waarde Retour neren, zelfs wanneer de invoer een verzameling is. Deze opera tors worden niet meer vergeleken wanneer ze de eerste overeenkomst detecteren, terwijl de gelijkheids operatoren alle invoer leden evalueren. In een zeer grote verzameling retour neren deze opera tors sneller dan de gelijkheids operators.

Syntaxis:

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a>-bevat en-notcontains

Deze opera tors geven aan of een set een bepaald element bevat. `-contains` Retourneert waar wanneer de rechter kant (test object) overeenkomt met een van de elementen in de set. `-notcontains` in plaats daarvan wordt false geretourneerd. Wanneer het test object een verzameling is, gebruiken deze opera tors referentie gelijkheid, dat wil zeggen dat ze controleren of een van de set-elementen hetzelfde exemplaar van het test object is.

Voorbeelden:

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

Complexere voor beelden:

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a>-in en-notin

De `-in` `notin` Opera tors en zijn geïntroduceerd in Power Shell 3 als de syntaxis van de `contains` `-notcontain` Opera tors van en. `-in` retourneert **waar** wanneer de linkerkant `<test-object>` overeenkomt met een van de elementen in de set. `-notin` in plaats daarvan wordt **False** geretourneerd. Wanneer het test object een set is, gebruiken deze opera tors referentie gelijkheid om te controleren of een van de set-elementen hetzelfde exemplaar van het test object is.

De volgende voor beelden doen hetzelfde als de voor beelden voor `-contain` en `-notcontain` doen, maar ze zijn wel geschreven met `-in` en `-notin` in plaats daarvan.

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

Complexere voor beelden:

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a>Type vergelijking

De type vergelijkings operators ( `-is` en `-isnot` ) worden gebruikt om te bepalen of een object een specifiek type is.

Syntaxis:

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

Voorbeeld:

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a>ZIE OOK

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [Foreach-object](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-object](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
