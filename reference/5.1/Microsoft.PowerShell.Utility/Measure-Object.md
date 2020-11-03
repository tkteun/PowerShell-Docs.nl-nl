---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 5d4a27f1a1949056ca63b9b6a2340bf1226592e0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251737"
---
# Measure-Object

## SAMENVATTING
Hiermee worden de numerieke eigenschappen van objecten en de tekens, woorden en regels in teken reeks objecten, zoals tekst bestanden, berekend.

## SYNTAXIS

### GenericMeasure (standaard)

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Sum] [-Average] [-Maximum] [-Minimum]
 [<CommonParameters>]
```

### TextMeasure

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Line] [-Word] [-Character]
 [-IgnoreWhiteSpace] [<CommonParameters>]
```

## BESCHRIJVING

`Measure-Object`Met de cmdlet worden de eigenschapwaarden van bepaalde typen objecten berekend.
`Measure-Object` voert drie soorten metingen uit, afhankelijk van de para meters in de opdracht.

De `Measure-Object` cmdlet voert berekeningen uit op de eigenschaps waarden van objecten. U kunt gebruiken `Measure-Object` om objecten te tellen of objecten te tellen met een opgegeven **eigenschap**. U kunt ook gebruiken `Measure-Object` om het **minimum** , **maximum** , **Sum** , **StandardDeviation** en het **gemiddelde** van numerieke waarden te berekenen. Voor **teken reeks** objecten kunt u ook gebruiken `Measure-Object` om het aantal regels, woorden en tekens te tellen.

## VOORBEELDEN

### Voor beeld 1: het aantal bestanden en mappen in een map tellen

Met deze opdracht worden de bestanden en mappen in de huidige map geteld.

```powershell
Get-ChildItem | Measure-Object
```

### Voor beeld 2: de bestanden in een map meten

Met deze opdracht worden het **minimum** , **maximum** en de **som** van de grootte van alle bestanden in de huidige map en de gemiddelde grootte van een bestand in de map weer gegeven.

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### Voor beeld 3: tekst in een tekst bestand meten

Met deze opdracht wordt het aantal tekens, woorden en regels in het Text.txt bestand weer gegeven.
Zonder de **onbewerkte** para meter `Get-Content` voert het bestand uit als een matrix met regels.

De eerste opdracht wordt gebruikt `Set-Content` om een standaard tekst toe te voegen aan een bestand.

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### Voor beeld 4: objecten met een opgegeven eigenschap meten

In dit voor beeld wordt het aantal objecten met een eigenschap **DisplayName** geteld. Met de eerste twee opdrachten worden alle services en processen op de lokale computer opgehaald. Met de derde opdracht wordt het gecombineerde aantal services en processen geteld. Met de laatste opdracht worden de twee verzamelingen gecombineerd en wordt het resultaat door sluizen naar `Measure-Object` .

Het object **System. Diagnostics. process** heeft geen eigenschap **DisplayName** en wordt wegge laten uit het laatste aantal.

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### Voor beeld 5: de inhoud van een CSV-bestand meten

Met deze opdracht wordt het gemiddelde aantal jaren van de service van de werk nemers van een bedrijf berekend.

Het `ServiceYrs.csv` bestand is een CSV-bestand dat het werknemers nummer en de dienst jaren van elke werk nemer bevat. De eerste rij in de tabel is een veldnamenrij van **EmpNo** , **jaar**.

Wanneer u gebruikt `Import-Csv` om het bestand te importeren, is het resultaat een **PSCustomObject** met notitie-eigenschappen van **EmpNo** en **jaren**.
U kunt gebruiken `Measure-Object` voor het berekenen van de waarden van deze eigenschappen, net als elke andere eigenschap van een object.

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### Voor beeld 6: Boole-waarden meten

In dit voor beeld wordt gedemonstreerd hoe `Measure-Object` Booleaanse waarden kunnen worden gemeten.
In dit geval wordt de **PSIsContainer** **Boolean** -eigenschap gebruikt om het incidenten van mappen (versus bestanden) in de huidige map te meten.

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### Voor beeld 7: teken reeksen meten

In het volgende voor beeld wordt het aantal regels, eerste één teken reeks, in meerdere teken reeksen gemeten. Het teken voor een nieuwe regel <code>`n</code> scheidt reeksen in meerdere regels.

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

## PARAMETERS

### -Gemiddeld

Geeft aan dat de cmdlet de gemiddelde waarde van de opgegeven eigenschappen weergeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Teken

Geeft aan dat de cmdlet het aantal tekens in de invoer objecten telt.

> [!NOTE]
> Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten. Zie voor beeld 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWhiteSpace

Geeft aan dat de cmdlet witruimte in het aantal tekens negeert.
Standaard wordt witruimte niet genegeerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Geeft aan welke objecten moeten worden gemeten.
Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

Wanneer u de para meter **input object** gebruikt in `Measure-Object` plaats van de resultaten van de pijpleiding opdracht, `Measure-Object` wordt de waarde van **input object** behandeld als een enkel object.

Het is raadzaam `Measure-Object` om in de pijp lijn te gebruiken als u een verzameling objecten wilt meten op basis van het feit of de objecten specifieke waarden in gedefinieerde eigenschappen hebben.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Regel

Geeft aan dat de cmdlet het aantal regels in de invoer objecten telt.

> [!NOTE]
> Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten. Zie voor beeld 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Maximum

Geeft aan dat de cmdlet de maximum waarde van de opgegeven eigenschappen weergeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

Geeft aan dat de cmdlet de minimale waarde van de opgegeven eigenschappen weergeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u een of meer eigenschappen op die moeten worden gemeten. Als u geen andere maat regelen opgeeft, `Measure-Object` telt het aantal objecten dat de door u opgegeven eigenschappen bevat.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Sum

Geeft aan dat de cmdlet de som van de waarden van de opgegeven eigenschappen weergeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Word

Geeft aan dat de cmdlet het aantal woorden in de invoer objecten telt.

> [!NOTE]
> Het **woord** , **char** en **regel** switches tellen *in* elk invoer object, evenals *over* invoer objecten. Zie voor beeld 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt objecten door sluizen naar `Measure-Object` .

## UITVOER

### Micro soft. Power shell. commands. GenericMeasureInfo

### Micro soft. Power shell. commands. TextMeasureInfo

Als u de para meter **Word** gebruikt, `Measure-Object` wordt een **TextMeasureInfo** -object geretourneerd.
Anders wordt een **GenericMeasureInfo** -object geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Compare-object](Compare-Object.md)

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Groep-object](Group-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sorteer object](Sort-Object.md)

[T-object](Tee-Object.md)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)
