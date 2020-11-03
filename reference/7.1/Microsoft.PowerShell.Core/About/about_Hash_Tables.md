---
description: Hierin wordt beschreven hoe u hash-tabellen maakt, gebruikt en sorteert in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: 0c4c54ea0ac017f0238ea5766c3489a1918d8fdd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252153"
---
# <a name="about-hash-tables"></a>Hash-tabellen

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u hash-tabellen maakt, gebruikt en sorteert in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

Een hash-tabel, ook wel een woorden lijst of associatieve matrix genoemd, is een compacte gegevens structuur waarin een of meer sleutel-waardeparen worden opgeslagen. Een hash-tabel kan bijvoorbeeld een reeks IP-adressen en computer namen bevatten, waarbij de IP-adressen de sleutels zijn en de computer namen de waarden zijn, of andersom.

Elke hash-tabel in Power shell is een hashtabel-object (System. Collections. hashtabel). U kunt de eigenschappen en methoden van hashtabel-objecten in Power shell gebruiken.

Vanaf Power Shell 3,0 kunt u het kenmerk [gelastd] gebruiken om een geordende woorden lijst (System. Collections. specialist. OrderedDictionary) in Power shell te maken.

Geordende woorden boeken verschillen van hash-tabellen in dat de sleutels altijd worden weer gegeven in de volg orde waarin u ze opvermeldt. De volg orde van de sleutels in een hash-tabel is niet bepaald.

De sleutels en waarde in hash-tabellen zijn ook .NET-objecten. Ze zijn meestal teken reeksen of gehele getallen, maar ze kunnen elk object type hebben. U kunt ook geneste hash-tabellen maken, waarbij de waarde van een sleutel een andere hash-tabel is.

Hash-tabellen worden vaak gebruikt, omdat ze zeer efficiënt zijn voor het zoeken en ophalen van gegevens. U kunt hash-tabellen gebruiken om lijsten op te slaan en berekende eigenschappen in Power shell te maken. En Power Shell heeft een cmdlet, ConvertFrom-StringData, waarmee teken reeksen naar een hash-tabel worden geconverteerd.

### <a name="syntax"></a>Syntax

De syntaxis van een hash-tabel is als volgt:

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

De syntaxis van een geordende woorden lijst is als volgt:

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

Het kenmerk [gelastd] is geïntroduceerd in Power Shell 3,0.

### <a name="creating-hash-tables"></a>Hash-tabellen maken

Als u een hash-tabel wilt maken, volgt u deze richt lijnen:

- Begin de hash-tabel met een apen staartje (@).
- Plaats de hash-tabel tussen accolades ( {} ).
- Voer een of meer sleutel-waardeparen in voor de inhoud van de hash-tabel.
- Gebruik een gelijkteken (=) als scheidings teken voor elke sleutel van de waarde.
- Gebruik een punt komma (;) of een regel-afbreek punt om de sleutel/waarde-paren van elkaar te scheiden.
- De sleutel die spaties bevat moet tussen aanhalings tekens worden geplaatst. De waarden moeten geldige Power shell-expressies zijn. Teken reeksen moeten tussen aanhalings tekens worden weer gegeven, zelfs als ze geen spaties bevatten.
- Als u de hash-tabel wilt beheren, slaat u deze op in een variabele.
- Wanneer u een geordende hash-tabel aan een variabele toewijst, plaatst u het kenmerk [gelastd] vóór het @-teken. Als u deze voor de naam van de variabele plaatst, mislukt de opdracht.

Als u een lege hash-tabel wilt maken in de waarde van $hash, typt u:

```powershell
$hash = @{}
```

U kunt ook sleutels en waarden aan een hash-tabel toevoegen wanneer u deze maakt. Met de volgende instructie maakt u bijvoorbeeld een hash-tabel met drie sleutels.

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a>Geordende woorden lijsten maken

U kunt een geordende woorden lijst maken door een object van het type OrderedDictionary toe te voegen, maar de eenvoudigste manier om een geordende woorden lijst te maken, is het kenmerk [besteld] te gebruiken.

Het kenmerk [gelastd] is geïntroduceerd in Power Shell 3,0.

Plaats het kenmerk direct voor het @-teken.

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

U kunt geordende woorden lijsten op dezelfde manier gebruiken als voor het gebruik van hash-tabellen.
Een van beide typen kan worden gebruikt als de waarde van para meters die een hash-tabel of-woorden lijst (iDictionary) maken.

U kunt het kenmerk [gelastd] niet gebruiken om een hash-tabel te converteren of te casten. Als u het kenmerk besteld vóór de naam van de variabele plaatst, mislukt de opdracht met het volgende fout bericht.

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

Verplaats het kenmerk [gelastd] om de expressie te corrigeren.

```powershell
PS C:\> $hash = [ordered]@{}
```

U kunt een geordende woorden lijst converteren naar een hash-tabel, maar u kunt het bestelde kenmerk niet herstellen, zelfs niet als u de variabele wist en nieuwe waarden opgeeft. Als u de volg orde wilt herstellen, moet u de variabele verwijderen en opnieuw maken.

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a>Hash-tabellen weer geven

Als u een hash-tabel wilt weer geven die is opgeslagen in een variabele, typt u de naam van de variabele.
Standaard worden hash-tabellen weer gegeven als een tabel met één kolom voor sleutels en één voor waarden.

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

Hash-tabellen hebben eigenschappen van sleutels en waarden. Gebruik de punt notatie om alle sleutels of alle waarden weer te geven.

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

Elke sleutel naam is ook een eigenschap van de hash-tabel en de waarde ervan is de waarde van de eigenschap key-name. Gebruik de volgende indeling om de eigenschaps waarden weer te geven.

```powershell
$hashtable.<key>
<value>
```

Bijvoorbeeld:

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

Als de naam van de sleutel conflicteert met een van de eigenschaps namen van het type hash-tabel, kunt u gebruiken `PSBase` om toegang te krijgen tot die eigenschappen. Als de naam van de sleutel bijvoorbeeld is `keys` en u de verzameling sleutels wilt retour neren, gebruikt u de volgende syntaxis:

```powershell
$hashtable.PSBase.Keys
```

Hash-tabellen hebben een eigenschap Count die het aantal sleutel-waardeparen in de hash-tabel aangeeft.

```powershell
C:\PS> $hash.count
3
```

Hash-tabel tabellen zijn geen matrices. Daarom kunt u geen geheel getal als een index in de hashtabel gebruiken, maar wel een sleutel naam gebruiken om in de hashtabel te indexeren.
Als de sleutel een teken reeks waarde is, plaatst u de sleutel naam tussen aanhalings tekens.

Bijvoorbeeld:

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a>Sleutels en waarden toevoegen en verwijderen

Als u sleutels en waarden wilt toevoegen aan een hash-tabel, gebruikt u de volgende opdracht indeling.

```powershell
$hash["<key>"] = "<value>"
```

Als u bijvoorbeeld een ' tijd sleutel ' met de waarde ' Now ' wilt toevoegen aan de hash-tabel, gebruikt u de volgende instructie indeling.

```powershell
$hash["Time"] = "Now"
```

U kunt ook sleutels en waarden toevoegen aan een hash-tabel met behulp van de methode Add van het object System. Collections. hashtabel. De methode Add heeft de volgende syntaxis:

```powershell
Add(Key, Value)
```

Als u bijvoorbeeld een ' tijd sleutel ' met de waarde ' Now ' wilt toevoegen aan de hash-tabel, gebruikt u de volgende instructie indeling.

```powershell
$hash.Add("Time", "Now")
```

En u kunt sleutels en waarden toevoegen aan een hash-tabel met behulp van de operator voor optellen (+) om een hash-tabel toe te voegen aan een bestaande hash-tabel. De volgende instructie voegt bijvoorbeeld een ' time '-sleutel met de waarde ' Now ' toe aan de hash-tabel in de variabele $hash.

```powershell
$hash = $hash + @{Time="Now"}
```

U kunt ook waarden toevoegen die zijn opgeslagen in variabelen.

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

U kunt een operator voor aftrekken niet gebruiken om een sleutel/waarde-paar uit een hashtabel te verwijderen, maar met de methode Remove van het object hash-tabel. De methode Remove neemt de sleutel als waarde.

De methode Remove heeft de volgende syntaxis:

```
Remove(Key)
```

Als u bijvoorbeeld de tijd = nu sleutel/waarde-paar uit de hash-tabel wilt verwijderen in de waarde van de variabele $hash, typt u:

```powershell
$hash.Remove("Time")
```

U kunt alle eigenschappen en methoden van hashtabel-objecten in Power shell gebruiken, inclusief contains, Clear, clone en CopyTo. Zie ' System. Collections. hashtabel ' op MSDN voor meer informatie over Hashtable-objecten.

### <a name="object-types-in-hashtables"></a>Object typen in hashtabellen

De sleutels en waarden in een hash-tabel kunnen elk .NET-object type hebben en een enkele hash-tabel kan sleutels en waarden van meerdere typen hebben.

Met de volgende instructie maakt u een hash-tabel met proces naam reeksen en proces object waarden en slaat u deze op in de \$ variabele p.

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

U kunt de hash-tabel weer geven in \$ p en de eigenschappen van de sleutel naam gebruiken om de waarden weer te geven.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

De sleutels in een hash-tabel kunnen ook elk .NET-type zijn. De volgende instructie voegt een sleutel/waarde-paar toe aan de hash-tabel in de \$ variabele p. De sleutel is een service object dat de WinRM-service vertegenwoordigt en de waarde is de huidige status van de service.

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

U kunt het nieuwe sleutel/waardepaar weer geven en openen met behulp van dezelfde methoden die u voor andere paren in de hash-tabel gebruikt.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

De sleutels en waarden in een hash-tabel kunnen ook hash-objecten zijn. De volgende instructie voegt een sleutel/waarde-paar toe aan de hash-tabel in de \$ p-variabele waarin de sleutel een teken reeks, Hash2 en de waarde is een hash-tabel met drie sleutel-waardeparen.

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

U kunt de nieuwe waarden weer geven en openen met behulp van dezelfde methoden.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a>Sleutels en waarden sorteren

De items in een hash-tabel zijn niet in de juiste volg orde. De sleutel-waardeparen kunnen elke keer dat u ze weer geven in een andere volg orde worden weer gegeven.

Hoewel u een hashtabel kunt niet sorteren, kunt u de GetEnumerator-methode van hash-tabellen gebruiken om de sleutels en waarden op te sommen en vervolgens de cmdlet Sort-Object gebruiken om de opgesomde waarden voor weer gave te sorteren.

Met de volgende opdrachten worden bijvoorbeeld de sleutels en waarden in de hash-tabel in de \$ variabele p opgesomd en vervolgens de sleutels in alfabetische volg orde gesorteerd.

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

De volgende opdracht maakt gebruik van dezelfde procedure om de hash-waarden in aflopende volg orde te sorteren.

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a>Objecten maken op basis van hash-tabellen

Vanaf Power Shell 3,0 kunt u een object maken op basis van een hash-tabel met eigenschappen en eigenschaps waarden.

De syntaxis is als volgt:

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

Deze methode werkt alleen voor klassen die een null-constructor hebben, dat wil zeggen een constructor zonder para meters. De object eigenschappen moeten openbaar en instelbaar zijn.

Zie [about_Object_Creation](about_Object_Creation.md)voor meer informatie.

### <a name="convertfrom-stringdata"></a>ConvertFrom-StringData

`ConvertFrom-StringData`Met de cmdlet wordt een teken reeks of hier een teken reeks van sleutel-waardeparen geconverteerd naar een hash-tabel. U kunt de `ConvertFrom-StringData` cmdlet veilig gebruiken in het gedeelte gegevens van een script en u kunt deze met de cmdlet gebruiken `Import-LocalizedData` om gebruikers berichten weer te geven in de gebruikers interface cultuur (UI) van de huidige gebruiker.

Hier-teken reeksen zijn vooral handig wanneer de waarden in de hash-tabel aanhalings tekens bevatten. Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.

In het volgende voor beeld ziet u hoe u een hier-reeks maakt van de gebruikers berichten in het vorige voor beeld en hoe u deze kunt gebruiken `ConvertFrom-StringData` om ze te converteren van een teken reeks naar een hash-tabel.

Met de volgende opdracht maakt u een teken reeks van de sleutel-waardeparen en slaat u deze op in de \$ teken reeks variabele.

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

Met deze opdracht wordt gebruikgemaakt van de cmdlet ConvertFrom-StringData om de hier-teken reeks te converteren naar een hash-tabel.

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.

## <a name="see-also"></a>ZIE OOK

[about_Arrays](about_Arrays.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[System. Collections. hashtabel](/dotnet/api/system.collections.hashtable)

