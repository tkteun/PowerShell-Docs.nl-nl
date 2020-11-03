---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: e4cc40e7a9a5fdcd12b6a787607e4979ddbb3273
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250917"
---
# ConvertTo-Csv

## SAMENVATTING
Hiermee converteert u .NET-objecten naar een reeks teken reeksen met tekens gescheiden waarden (CSV).

## SYNTAXIS

### Scheidingsteken

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### UseCulture

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## BESCHRIJVING

De `ConvertTo-CSV` cmdlet retourneert een reeks teken reeksen met door komma's gescheiden waarden (CSV) die de objecten vertegenwoordigen die u verzendt. U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Csv` om objecten opnieuw te maken op basis van de CSV-teken reeksen. De objecten die zijn geconverteerd van CSV zijn teken reeks waarden van de oorspronkelijke objecten die eigenschaps waarden en geen methoden bevatten.

U kunt de `Export-Csv` cmdlet gebruiken om objecten te converteren naar CSV-teken reeksen. `Export-CSV` is vergelijkbaar met `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.

De `ConvertTo-CSV` cmdlet bevat para meters om een ander scheidings teken dan een komma op te geven of gebruik de huidige cultuur als scheidings teken.

## VOORBEELDEN

### Voor beeld 1: een object converteren naar CSV

In dit voor beeld wordt een **proces** object geconverteerd naar een CSV-teken reeks.

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

De `Get-Process` cmdlet haalt het **proces** object op en gebruikt de para meter **name** om het Power Shell-proces op te geven. Het proces object wordt via de pijp lijn naar de `ConvertTo-CSV` cmdlet verzonden. De `ConvertTo-CSV` cmdlet converteert het object naar CSV-teken reeksen. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.

### Voor beeld 2: een DateTime-object converteren naar CSV

In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

De `Get-Date` cmdlet haalt het **DateTime** -object op en slaat het op in de `$Date` variabele. `ConvertTo-Csv`Met de cmdlet wordt het **DateTime** -object geconverteerd naar teken reeksen. De para meter **input object** maakt gebruik van het **DateTime** -object dat is opgeslagen in de `$Date` variabele. De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.

### Voor beeld 3: het Power shell-gebeurtenis logboek converteren naar CSV

In dit voor beeld wordt het Windows-gebeurtenis logboek voor Power shell geconverteerd naar een reeks CSV-teken reeksen.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer. De `Get-WinEvent` cmdlet haalt de gebeurtenis logboek objecten op en gebruikt de para meter **LogName** om de naam van het logboek bestand op te geven. De gebeurtenis logboek objecten worden naar de-cmdlet verzonden via de pijp lijn `ConvertTo-Csv` . `ConvertTo-Csv`Met de cmdlet worden gebeurtenis logboek objecten geconverteerd naar een reeks CSV-teken reeksen. De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer en is niet vereist in Power shell 6.

### Voor beeld 4: converteren naar CSV met aanhalings tekens rond twee kolommen

In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### Voor beeld 4: Converteer naar CSV met alleen aanhalings tekens als dat nodig is

In dit voor beeld wordt een **DateTime** -object geconverteerd naar een CSV-teken reeks.

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## PARAMETERS

### -Scheidings teken

Hiermee geeft u het scheidings teken voor het scheiden van de eigenschaps waarden in CSV-teken reeksen. De standaard waarde is een komma ( `,` ). Voer een teken in, bijvoorbeeld een dubbele punt ( `:` ). Als u een punt komma () wilt opgeven, `;` plaatst u deze tussen enkele aanhalings tekens.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeTypeInformation

Als deze para meter wordt gebruikt, bevat de eerste regel van de uitvoer **#TYPE** gevolgd door de volledig gekwalificeerde naam van het object type. Bijvoorbeeld **#TYPE System. Diagnostics. process**.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de objecten die worden geconverteerd naar CSV-teken reeksen. Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald. U kunt ook objecten pipeen naar `ConvertTo-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

Hiermee verwijdert u de **#TYPE** informatie uit de uitvoer. Deze para meter werd de standaard waarde in Power shell 6,0 en is opgenomen voor achterwaartse compatibiliteit.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken. Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QuoteFields

Hiermee geeft u de namen van de kolommen die moeten worden genoteerd. Als deze para meter wordt gebruikt, worden alleen de opgegeven kolommen genoteerd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseQuotes

Hiermee geeft u op wanneer aanhalings tekens worden gebruikt in de CSV-bestanden. Mogelijke waarden zijn:

- Nooit: niets citeren
- Altijd: alle citaten (standaard gedrag)
- Alleen-AsNeeded die een scheidings teken bevatten

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object dat een adapter met een Extended type systeem (ETS) bevat, aan `ConvertTo-CSV` .

## UITVOER

### System. String

De CSV-uitvoer wordt geretourneerd als een verzameling teken reeksen.

## OPMERKINGEN

In CSV-indeling wordt elk object vertegenwoordigd door een door komma's gescheiden lijst van de eigenschaps waarde. De eigenschaps waarden worden geconverteerd naar teken reeksen met de methode **toString ()** van het object. De teken reeksen worden vertegenwoordigd door de naam van de eigenschaps waarde. `ConvertTo-CSV` exporteert de methoden van het object niet.

De CSV-teken reeksen worden als volgt uitgevoerd:

- Als **IncludeTypeInformation** wordt gebruikt, bestaat de eerste teken reeks uit **#TYPE** gevolgd door de volledig gekwalificeerde naam van het object type. Bijvoorbeeld **#TYPE System. Diagnostics. process**.
- Als **IncludeTypeInformation** niet wordt gebruikt, bevat de eerste teken reeks de kolom koppen. De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.
- De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.

Vanaf Power shell 6,0 is het standaard gedrag van de `ConvertTo-CSV` **#TYPE** informatie in het CSV-bestand en **NoTypeInformation** wordt geïmpliceerd. **IncludeTypeInformation** kan worden gebruikt om de **#TYPE** informatie op te neemt en het standaard gedrag van `ConvertTo-CSV` vóór Power shell 6,0 te emuleren.

Wanneer u meerdere objecten verzendt naar `ConvertTo-CSV` , worden `ConvertTo-CSV` de teken reeksen door gesorteerd op basis van de eigenschappen van het eerste object dat u verzendt. Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's. Als de resterende objecten extra eigenschappen hebben, worden die eigenschaps waarden genegeerd.

## GERELATEERDE KOPPELINGEN

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[Exporteren-CSV](Export-Csv.md)

[Import-Csv](Import-Csv.md)

