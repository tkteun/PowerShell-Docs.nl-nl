---
description: Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: dbda5371224345a2e22dd281c17ae0d7c928aad6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090223"
---
# <a name="about-comparison-operators"></a>Over vergelijkings operatoren

## <a name="short-description"></a>Korte beschrijving
Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.

## <a name="long-description"></a>Lange beschrijving

Met vergelijkings operatoren kunt u voor waarden opgeven voor het vergelijken van waarden en waarden zoeken die overeenkomen met opgegeven patronen. Als u een vergelijkings operator wilt gebruiken, geeft u de waarden op die u wilt vergelijken samen met een operator die deze waarden scheidt.

Power shell bevat de volgende vergelijkings operatoren:

| Type        | Operators    | Description                                 |
| ----------- | ------------ | --------------------------------------------|
| Gelijkheid    | -eq          | is gelijk aan                                      |
|             | -ne          | niet gelijk aan                                  |
|             | -gt          | groter dan                                |
|             | -ge          | groter dan of gelijk aan                       |
|             | -lt          | kleiner dan                                   |
|             | -Le          | kleiner dan of gelijk aan                          |
|             |              |                                             |
| Matching    | -like        | Retourneert waar als teken reeks overeenkomt met Joker teken   |
|             |              | pattern                                     |
|             | -notlike     | Retourneert waar als de teken reeks niet overeenkomt     |
|             |              | Joker teken patroon                            |
|             | -match       | Retourneert True als teken reeks overeenkomt met regex      |
|             |              | pattern $matches bevat overeenkomende teken reeksen |
|             | -notmatch    | Retourneert waar als de teken reeks niet overeenkomt     |
|             |              | regex-patroon; $matches bevat overeenkomende   |
|             |              | tekenreeksen                                     |
|             |              |                                             |
| Containment | -contains    | Retourneert waar als de referentie waarde bevat |
|             |              | in een verzameling                             |
|             | -notcontains | Retourneert waar als de referentie waarde niet       |
|             |              | opgenomen in een verzameling                   |
|             | -in          | Retourneert waar als de test waarde in een |
|             |              | verzameling                                  |
|             | -notin       | Retourneert waar als de test waarde niet bevat  |
|             |              | in een verzameling                             |
|             |              |                                             |
| Vervanging | -vervangen     | Vervangt een teken reeks patroon                   |
|             |              |                                             |
| Type        | -is          | Retourneert waar als beide objecten hetzelfde zijn    |
|             |              | type                                        |
|             | -isnot       | Retourneert waar als de objecten niet hetzelfde zijn|
|             |              | type                                        |

Standaard zijn alle vergelijkings operatoren niet hoofdletter gevoelig. Als u een vergelijkings operator hoofdletter gevoelig wilt maken, moet u de naam van de operator vooraf vervangen door een `c` . De hoofdletter gevoelige versie van `-eq` is bijvoorbeeld `-ceq` . Als u de niet-hoofdletter gevoeligheid expliciet wilt maken, moet u voorafgaand aan de operator een `i` . De versie van is bijvoorbeeld expliciet niet hoofdletter gevoelig `-eq` `-ieq` .

Wanneer de invoer voor een operator een scalaire waarde is, retour neren vergelijkings operatoren een Booleaanse waarde. Wanneer de invoer een verzameling waarden is, retour neren de vergelijkings operatoren alle overeenkomende waarden. Als er geen overeenkomsten in een verzameling zijn, retour neren vergelijkings operatoren een lege matrix.

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

De uitzonde ringen zijn de containment-Opera Tors, de Opera tors in en de type operator, die altijd een **Booleaanse** waarde Retour neren.

> [!NOTE]
> Als u een waarde wilt vergelijken `$null` , moet u aan `$null` de linkerkant van de vergelijking zetten. Wanneer u vergelijkt `$null` met een **object []** , is het resultaat **False** omdat het vergelijkings object een matrix is. Wanneer u een matrix vergelijkt met `$null` , worden de `$null` waarden die in de matrix zijn opgeslagen, door de vergelijking gefilterd. Bijvoorbeeld:
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a>Gelijkheidsoperatoren

De gelijkheids operatoren ( `-eq` , `-ne` ) retour neren de waarde True of de overeenkomsten wanneer een of meer invoer waarden identiek zijn aan het opgegeven patroon. Het hele patroon moet overeenkomen met een volledige waarde.

Voorbeeld:

### <a name="-eq"></a>-eq

Beschrijving: gelijk aan. Bevat een identieke waarde.

Voorbeeld:

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

### <a name="-ne"></a>-ne

Beschrijving: niet gelijk aan. Bevat een andere waarde.

Voorbeeld:

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

### <a name="-gt"></a>-gt

Beschrijving: groter dan.

Voorbeeld:

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> Dit mag niet worden verward met `>` , de operator groter dan in veel andere programmeer talen. In Power shell `>` wordt gebruikt voor omleiding. Zie [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)voor meer informatie.

### <a name="-ge"></a>-ge

Beschrijving: groter dan of gelijk aan.

Voorbeeld:

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a>-lt

Beschrijving: kleiner dan.

Voorbeeld:

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a>-Le

Beschrijving: kleiner dan of gelijk aan.

Voorbeeld:

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a>Overeenkomende Opera tors

De like-Opera tors ( `-like` en `-notlike` ) vinden elementen die overeenkomen met of die niet overeenkomen met een opgegeven patroon met Joker teken expressies.

De syntaxis is:

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

De overeenkomende Opera tors ( `-match` en `-notmatch` ) vinden elementen die overeenkomen met of die niet overeenkomen met een opgegeven patroon met reguliere expressies.

De operators matchen vullen de `$Matches` Automatische variabele in wanneer de invoer (het argument aan de linkerkant) naar de operator is één scalair object. Wanneer de invoer scalair is, `-match` `-notmatch` retour neren de Opera tors en wordt de waarde van de `$Matches` Automatische variabele ingesteld op de overeenkomende onderdelen van het argument.

De syntaxis is:

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a>-like

Beschrijving: komt overeen met het Joker teken ( \* ).

Voorbeeld:

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a>-notlike

Beschrijving: komt niet overeen met het Joker teken ( \* ).

Voorbeeld:

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a>-match

Beschrijving: komt overeen met een teken reeks met reguliere expressies. Wanneer de invoer scalair is, wordt de `$Matches` Automatische variabele gevuld.

Als de invoer een verzameling is, `-match` `-notmatch` retour neren de Opera tors en de overeenkomende leden van die verzameling, maar de operator vult de `$Matches` variabele niet in.

Met de volgende opdracht wordt bijvoorbeeld een verzameling teken reeksen naar de operator verzonden `-match` . De `-match` operator retourneert de items in de verzameling die overeenkomen. De automatische variabele wordt niet gevuld `$Matches` .

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

Met de volgende opdracht wordt daarentegen één teken reeks naar de `-match` operator verzonden. De `-match` operator retourneert een Booleaanse waarde en vult de `$Matches` Automatische variabele. De `$Matches` Automatische variabele is een **hashtabel**. Als er geen groepering of opname wordt gebruikt, wordt er slechts één sleutel ingevuld.
De `0` sleutel vertegenwoordigt alle tekst die overeenkomt. Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie over het groeperen en vastleggen met behulp van reguliere expressies.

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

Het is belang rijk te weten dat de `$Matches` hashtabel alleen het eerste exemplaar van een overeenkomend patroon moet bevatten.

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> De `0` sleutel is een **geheel getal**. U kunt elke **hash** -methode gebruiken om toegang te krijgen tot de opgeslagen waarde.
>
> ```powershell
> PS> "Good Dog" -match "Dog"
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

De `-notmatch` operator vult de `$Matches` Automatische variabele in wanneer de invoer scalair is en het resultaat ONWAAR is, wanneer er een overeenkomst wordt gedetecteerd.

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

### <a name="-notmatch"></a>-notmatch

Beschrijving: komt niet overeen met een teken reeks. Maakt gebruik van reguliere expressies. Wanneer de invoer scalair is, wordt de `$Matches` Automatische variabele gevuld.

Voorbeeld:

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

## <a name="containment-operators"></a>Containment-Opera tors

De containment-Opera tors ( `-contains` en `-notcontains` ) zijn vergelijkbaar met de gelijkheids operatoren. De containment-Opera tors retour neren echter altijd een Booleaanse waarde, zelfs wanneer de invoer een verzameling is.

Ook, in tegens telling tot de gelijkheids operatoren, retour neren de container-Opera tors een waarde zodra ze de eerste overeenkomst detecteren. De gelijkheids operatoren evalueren alle invoer en retour neren vervolgens alle overeenkomende items in de verzameling.

### <a name="-contains"></a>-contains

Beschrijving: containment-operator. Hiermee wordt aangegeven of een verzameling verwijzings waarden één test waarde bevat. Retourneert altijd een Boole-waarde. Retourneert alleen waar als de test waarde exact overeenkomt met ten minste een van de referentie waarden.

Wanneer de test waarde een verzameling is, gebruikt de contains-operator referentie gelijkheid. Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.

In een zeer grote verzameling retourneert de `-contains` operator resultaten sneller dan de operator equal to.

Syntaxis:

`<Reference-values> -contains <Test-value>`

Voorbeelden:

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

### <a name="-notcontains"></a>-notcontains

Beschrijving: containment-operator. Hiermee wordt aangegeven of een verzameling verwijzings waarden één test waarde bevat. Retourneert altijd een Boole-waarde. Retourneert waar als de test waarde geen exacte overeenkomsten voor ten minste een van de verwijzings waarden is.

Wanneer de test waarde een verzameling is, gebruikt de NotContains-operator referentie gelijkheid.

Syntaxis:

`<Reference-values> -notcontains <Test-value>`

Voorbeelden:

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

### <a name="-in"></a>-in

Beschrijving: in operator. Hiermee wordt aangegeven of een test waarde wordt weer gegeven in een verzameling referentie waarden. Altijd retour neren als Booleaanse waarde. Retourneert alleen waar als de test waarde exact overeenkomt met ten minste een van de referentie waarden.

Wanneer de test waarde een verzameling is, gebruikt de in-operator referentie gelijkheid.
Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.

De `-in` operator is geïntroduceerd in Power shell 3,0.

Syntaxis:

`<Test-value> -in <Reference-values>`

Voorbeelden:

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

### <a name="-notin"></a>-notin

Beschrijving: Hiermee wordt aangegeven of een test waarde wordt weer gegeven in een verzameling referentie waarden. Retourneert altijd een Boole-waarde. Retourneert waar als de test waarde niet exact overeenkomt voor ten minste een van de referentie waarden.

Wanneer de test waarde een verzameling is, gebruikt de in-operator referentie gelijkheid.
Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.

De `-notin` operator is geïntroduceerd in Power shell 3,0.

Syntaxis:

`<Test-value> -notin <Reference-values>`

Voorbeelden:

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

## <a name="replacement-operator"></a>Vervangings operator

De `-replace` operator heeft de volgende syntaxis:

`<input> -replace <original>, <substitute>`

De `<original>` tijdelijke aanduiding is een reguliere expressie die overeenkomt met de tekens die moeten worden vervangen. De `<substitute>` tijdelijke aanduiding is een letterlijke teken reeks waarmee ze worden vervangen.

De operator vervangt alle of een deel van een waarde met de opgegeven waarde met reguliere expressies. U kunt de operator gebruiken voor veel beheer taken, zoals het wijzigen van de naam van bestanden. Met de volgende opdracht worden bijvoorbeeld de bestandsnaam extensies van alle bestanden gewijzigd `.txt` in `.log` :

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a>Hoofdletter gevoelige overeenkomsten

Standaard `-replace` is de operator niet hoofdletter gevoelig. Gebruik om het hoofdletter gevoelig te maken `-creplace` . Gebruik om het expliciet niet hoofdletter gevoelig te maken `-ireplace` .

Bekijk de volgende voorbeelden:

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a>Vervangingen in reguliere expressies

Het is ook mogelijk om reguliere expressies te gebruiken om tekst dynamisch te vervangen met opname groepen en vervangingen. Er kan in de teken reeks naar vastleg groepen worden verwezen `<substitute>` met het `$` teken voor het dollar teken () voor de groeps-id.

Naar vastleg groepen kan worden verwezen met een **getal** of **naam**

- Op **nummer** : het vastleggen van groepen wordt van links naar rechts genummerd.

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- Op **naam** : voor het vastleggen van groepen kan ook naar een naam worden verwezen.

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> Omdat het `$` teken wordt gebruikt in teken reeks uitbreiding, moet u letterlijke teken reeksen gebruiken of het teken escapeen `$` .
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> Omdat het `$` teken in substitutie wordt gebruikt, moet u ook alle exemplaren in de teken reeks verescapenen.
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

Zie [about_Regular_Expressions](about_Regular_Expressions.md) en [vervangingen in reguliere expressies](/dotnet/standard/base-types/substitutions-in-regular-expressions) voor meer informatie.

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

### <a name="scriptblock-substitutions"></a>Script Block vervangingen

Vanaf Power shell 6 kunt u een **script Block** -argument gebruiken voor de _vervangings_ tekst. De **script Block** wordt uitgevoerd voor elke overeenkomst die in de _invoer_ teken reeks is gevonden.

Gebruik in de **script Block** de `$_` Automatische variabele om te verwijzen naar het huidige **System. Text. RegularExpressions. match** -object. Met het object **match** krijgt u toegang tot de huidige invoer tekst die wordt vervangen, evenals andere nuttige informatie.

In dit voor beeld wordt elke reeks van drie decimalen vervangen door het teken equivalent. De **script Block** wordt uitgevoerd voor elke set van drie decimalen die moeten worden vervangen.

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

## <a name="type-comparison"></a>Type vergelijking

De type vergelijkings operators ( `-is` en `-isnot` ) worden gebruikt om te bepalen of een object een specifiek type is.

### <a name="-is"></a>-is

Syntaxis:

`<object> -is <type reference>`

Voorbeeld:

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a>-isnot

Syntaxis:

`<object> -isnot <type reference>`

Voorbeeld:

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a>Zie ook

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [Foreach-object](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-object](xref:Microsoft.PowerShell.Core.Where-Object)
