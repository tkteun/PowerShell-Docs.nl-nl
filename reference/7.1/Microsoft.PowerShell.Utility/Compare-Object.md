---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: f7decea60b92dc3613eecc1726855c100a245524
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "93253231"
---
# Compare-Object

## Samen vatting
Vergelijkt twee sets met objecten.

## Syntax

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## Beschrijving

De `Compare-Object` cmdlet vergelijkt twee sets met objecten. Een set van objecten is de **verwijzing** en de andere set met objecten is het **verschil**.

`Compare-Object` Hiermee wordt gecontroleerd op beschik bare methoden voor het vergelijken van een geheel object. Als er geen geschikte methode kan worden gevonden, worden de **toString ()** -methoden van de invoer objecten aangeroepen en worden de teken reeks resultaten vergeleken. U kunt een of meer eigenschappen opgeven die moeten worden gebruikt voor de vergelijking. Wanneer eigenschappen worden gegeven, vergelijkt de cmdlet alleen de waarden van die eigenschappen.

Het resultaat van de vergelijking geeft aan of een eigenschaps waarde alleen voor komt in het **verwijzings** object ( `<=` ) of alleen in het object **diff** ( `=>` ). Als de para meter **IncludeEqual** wordt gebruikt, ( `==` ) geeft aan dat de waarde in beide objecten is.

Als de **verwijzings** -of de **verschillen** objecten Null ( `$null` ) zijn, wordt `Compare-Object` een afsluit fout gegenereerd.

Enkele voor beelden gebruiken splatting om de regel lengte van de code voorbeelden te reduceren. Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.

## Voorbeelden

### Voor beeld 1: de inhoud van twee tekst bestanden vergelijken

In dit voor beeld wordt de inhoud van twee tekst bestanden vergeleken. In het voor beeld worden de volgende twee tekst bestanden gebruikt, met elke waarde op een afzonderlijke regel.

- `Testfile1.txt` bevat de waarden: hond, Squirrel en vogel.
- `Testfile2.txt` bevat de waarden: kat, vogel en racoon.

In de uitvoer worden alleen de lijnen weer gegeven die verschillen tussen de bestanden. `Testfile1.txt` is het **referentie** object ( `<=` ) en `Testfile2.txt` is het object **diff** ( `=>` ). Regels met inhoud die worden weer gegeven in beide bestanden, worden niet weer gegeven.

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### Voor beeld 2: elke regel met inhoud vergelijken en de verschillen uitsluiten

In dit voor beeld wordt de para meter **ExcludeDifferent** gebruikt voor het vergelijken van elke regel met inhoud in twee tekst bestanden.

Vanaf Power shell 7,1, wanneer u de para meter **ExcludeDifferent** gebruikt, wordt **IncludeEqual** afgeleid en de uitvoer bevat alleen regels die in beide bestanden staan, zoals wordt weer gegeven door de **SideIndicator** ( `==` ).

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### Voor beeld 3: het verschil weer geven bij gebruik van de para meter PassThru

Normaal gesp roken `Compare-Object` retourneert een **PSCustomObject** -type met de volgende eigenschappen:

- De **input object** die wordt vergeleken
- De eigenschap **SideIndicator** geeft aan met welk invoer object de uitvoer hoort

Wanneer u de para meter **PassThru** gebruikt, wordt het **type** van het object niet gewijzigd, maar het exemplaar van het geretourneerde object heeft een toegevoegd **NoteProperty** met de naam **SideIndicator**. **SideIndicator** laat zien met welk invoer object de uitvoer behoort.

In de volgende voor beelden ziet u de verschillende uitvoer typen.

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

Wanneer u **PassThru** gebruikt, wordt het oorspronkelijke object type ( **System. Boolean** ) geretourneerd. U ziet hoe de uitvoer die wordt weer gegeven door de standaard indeling voor **System. Boolean** -objecten, de eigenschap **SideIndicator** niet weergeeft. Het geretourneerde **System. Boolean** -object heeft echter het toegevoegde **NoteProperty**.

### Voor beeld 4: twee eenvoudige objecten vergelijken met eigenschappen

In dit voor beeld vergelijken we twee verschillende teken reeksen die dezelfde lengte hebben.

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### Voor beeld 5: complexe objecten vergelijken met eigenschappen

In dit voor beeld ziet u het gedrag bij het vergelijken van complexe objecten. In dit voor beeld slaan we twee verschillende proces objecten op voor verschillende instanties van Power shell. Beide variabelen bevatten proces objecten met dezelfde naam. Wanneer de objecten worden vergeleken zonder de para meter **Property** op te geven, beschouwt de cmdlet dat de objecten gelijk zijn. U ziet dat de waarde van **input object** gelijk is aan het resultaat van de methode **toString ()** . Omdat de klasse **System. Diagnostics. process** niet de interface **IComparable** heeft, converteert de cmdlet de objecten naar teken reeksen en vergelijkt de resultaten.

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

Wanneer u de eigenschappen opgeeft die moeten worden vergeleken, worden de verschillen in de cmdlet weer gegeven.

### Voor beeld 6: complexe objecten vergelijken die IComparable implementeren

Als het object **icomparable** implementeert, zoekt de cmdlet naar manieren om de objecten te vergelijken. Als de objecten verschillend zijn, wordt het object **verschil** geconverteerd naar het type van de **ReferenceObject** en vervolgens vergeleken.

In dit voor beeld vergelijkt u een teken reeks naar een **time span** -object. In het eerste geval wordt de teken reeks geconverteerd naar een **time span** zodat de objecten gelijk zijn.

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

In het tweede geval wordt de **time span** geconverteerd naar een teken reeks zodat het object verschillend is.

## Parameters

### -CaseSensitive

Geeft aan dat vergelijkingen hoofdletter gevoelig moeten zijn.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cultuur

Hiermee geeft u de cultuur op die moet worden gebruikt voor vergelijkingen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DifferenceObject

Hiermee geeft u de objecten die worden vergeleken met de **referentie** objecten.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ExcludeDifferent

Geeft aan dat met deze cmdlet alleen de kenmerken van vergeleken objecten worden weer gegeven die gelijk zijn. De verschillen tussen de objecten worden verwijderd.

Gebruik **ExcludeDifferent** met **IncludeEqual** om alleen de lijnen weer te geven die overeenkomen met de objecten **Reference** en **diff** .

Als **ExcludeDifferent** is opgegeven zonder **IncludeEqual** , is er geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeEqual

**IncludeEqual** geeft de overeenkomsten tussen de objecten **verwijzing** en **verschil** weer.

De uitvoer bevat standaard ook de verschillen tussen de objecten **verwijzing** en **verschil** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Wanneer u de para meter **PassThru** gebruikt, `Compare-Object` wordt de **PSCustomObject** -wrapper rond de vergeleken objecten wegge laten en worden de verschillende objecten ongewijzigd geretourneerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u een matrix met eigenschappen van de objecten **Reference** en **diff** op die u wilt vergelijken.

De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Expressie- `<string>` of `<script block>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceObject

Hiermee wordt een matrix met objecten opgegeven die worden gebruikt als verwijzing voor de vergelijking.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SyncWindow

Hiermee geeft u het aantal aangrenzende objecten op dat `Compare-Object` inspecteert terwijl er wordt gezocht naar een overeenkomst in een verzameling objecten. `Compare-Object` Hiermee worden aangrenzende objecten onderzocht wanneer het object niet op dezelfde positie in een verzameling wordt gevonden. De standaard waarde is `[Int32]::MaxValue` , wat betekent dat `Compare-Object` de volledige object verzameling onderzoekt.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. Management. Automation. PSObject

U kunt een object naar de **DifferenceObject** -para meter verzenden via de pijp lijn.

## Uitvoer

### Geen

Als het **referentie** object en het **verschil** object hetzelfde zijn, is er geen uitvoer, tenzij u de para meter **IncludeEqual** gebruikt.

### System. Management. Automation. PSCustomObject

Als de objecten verschillend zijn, worden `Compare-Object` de objecten in een `PSCustomObject` wrapper vervangen door de **SideIndicator** -eigenschap om te verwijzen naar de verschillen.

Wanneer u de para meter **PassThru** gebruikt, wordt het **type** van het object niet gewijzigd, maar het exemplaar van het geretourneerde object heeft een toegevoegd **NoteProperty** met de naam **SideIndicator**. **SideIndicator** laat zien met welk invoer object de uitvoer behoort.

## Opmerkingen

Wanneer u de para meter **PassThru** gebruikt, bevat de uitvoer die in de-console wordt weer gegeven, mogelijk niet de eigenschap **SideIndicator** . De standaard indelings weergave van de voor het object type uitvoer met `Compare-Object` bevat niet de eigenschap **SideIndicator** . Zie [voor beeld 3](#ex3) in dit artikel voor meer informatie.

## Verwante koppelingen

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Groep-object](Group-Object.md)

[Meting object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sorteer object](Sort-Object.md)

[T-object](Tee-Object.md)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
