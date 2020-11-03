---
description: Hierin worden de Opera tors beschreven die met Microsoft .NET typen werken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 6ea2ef2f61636d67a8bacf69ff577f477712a165
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253007"
---
# <a name="about-type-operators"></a>Over type operators

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de Opera tors beschreven die met Microsoft .NET typen werken.

## <a name="long-description"></a>LANGE BESCHRIJVING

De Boole-operator ( `-is` en `-isNot` ) geven aan of een object een exemplaar van een opgegeven .net-type is. De `-is` operator retourneert de waarde **True** als het type overeenkomt met en de waarde **False** . De `-isNot` operator retourneert de waarde **False** als het type overeenkomt met en de waarde **True** .

De `-as` operator probeert het invoer object te converteren naar het opgegeven .net-type. Als dit lukt, wordt het geconverteerde object geretourneerd. Als dit mislukt, wordt geretourneerd `$null` . Er wordt geen fout geretourneerd.

De volgende tabel bevat de type operators in Power shell.

|Operator|Beschrijving                |Voorbeeld                          |
|--------|---------------------------|---------------------------------|
|`-is`   |Retourneert waar wanneer de invoer|`(get-date) -is [DateTime]`      |
|        |is een exemplaar van de      |`True`                           |
|        |opgegeven .NET-type.       |                                 |
|`-isNot`|Retourneert waar wanneer de invoer|`(get-date) -isNot [DateTime]`   |
|        |geen exemplaar van de     |`False`                          |
|        |type specified.NET.        |                                 |
|`-as`   |Hiermee wordt de invoer geconverteerd naar de  |`"5/7/07" -as [DateTime]`        |
|        |opgegeven .NET-type.       |`Monday, May 7, 2007 12:00:00 AM`|

De syntaxis van de type operators is als volgt:

```powershell
<input> <operator> [.NET type]
```

U kunt ook de volgende syntaxis gebruiken:

```powershell
<input> <operator> ".NET type"
```

Het .NET-type kan worden geschreven als een type naam tussen vier Kante haken of een teken reeks, zoals `[DateTime]` of `"DateTime"` voor **System. datetime**. Als het type zich niet in de hoofdmap van de naam ruimte van het systeem bevindt, geeft u de volledige naam van het object type op. U kunt ' System. ' weglaten. U kunt bijvoorbeeld **System. Diagnostics. process** opgeven, invoeren `[System.Diagnostics.Process]` , `[Diagnostics.Process]` of `"Diagnostics.Process"` .

De type operators worden altijd als geheel op het invoer object toegepast. Dat wil zeggen, als het invoer object een verzameling is, het het type _verzameling_ dat wordt getest, niet de typen van de _elementen_ van de verzameling.

### <a name="-isisnot-operators"></a>-is/isNot Opera tors

De **Boole** -operator ( `-is` en `-isNot` ) retour neren altijd een **Booleaanse** waarde, zelfs als de invoer een verzameling van objecten is.

Als `<input>` is een type dat gelijk is aan of is _afgeleid_ van het .net-type, `-is` retourneert de operator `$True` .

Het type **DirectoryInfo** wordt bijvoorbeeld afgeleid van het type **FileSystemInfo** . Beide voor beelden geven daarom de **waarde True**.

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

De `-is` operator kan ook interfaces overeenkomen als de `<input>` interface in de vergelijking wordt geïmplementeerd. In dit voor beeld is de invoer een matrix. Matrices implementeren de interface **System. Collections. IList** .

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a>-as-operator

De `-as` operator probeert het invoer object te converteren naar het opgegeven .net-type. Als dit lukt, wordt het geconverteerde object geretourneerd. Als dit mislukt, wordt geretourneerd `$null` . Er wordt geen fout geretourneerd.

Als het `<input>` is een type dat is _afgeleid_ van het .net-type door gegeven, `-as` _passes through_ wordt het ingevoerde invoer object ongewijzigd. Het type **DirectoryInfo** wordt bijvoorbeeld afgeleid van het type **FileSystemInfo** . Daarom is het object type ongewijzigd in het volgende voor beeld:

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a>Conversie van het type DateTime is cultuur gevoelig

Conversie naar `[DateTime]` type met behulp `-as` van de operator werkt alleen met teken reeksen die zijn opgemaakt op basis van de regels van de huidige cultuur, in tegens telling tot type cast.

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

Als u het .NET-type van een object wilt zoeken, gebruikt u de `Get-Member` cmdlet. Of gebruik de **gettype** -methode van alle objecten in combi natie met de eigenschap **FullName** van deze methode. De volgende instructie haalt bijvoorbeeld het type van de retour waarde van een opdracht op `Get-Culture` :

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a>VOORBEELDEN

In de volgende voor beelden ziet u enkele gebruik van de type operators:

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

In het volgende voor beeld ziet u dat wanneer de invoer een verzameling objecten is, het overeenkomende type het .NET-type van de verzameling is, niet het type van de afzonderlijke objecten in de verzameling.

In dit voor beeld, hoewel zowel `Get-Culture` de `Get-UICulture` cmdlets als **System. Globalization. Culture info** -objecten retour neren, is een verzameling van deze objecten een System. object-matrix.

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

In de volgende voor beelden ziet u hoe u de `-as` operator gebruikt.

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

In het volgende voor beeld ziet u dat wanneer de `-as` operator het invoer object niet kan converteren naar het .net-type, het wordt geretourneerd `$null` .

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a>ZIE OOK

[about_Operators](about_Operators.md)
