---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: be590368539f396f0aac694e9565674393543f2c
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913199"
---
# ConvertTo-Csv

## SAMENVATTING
Converteert .NET-objecten naar een reeks teken reeksen met door komma's gescheiden waarden (CSV).

## SYNTAXIS

### Scheidings teken (standaard)

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### UseCulture

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## BESCHRIJVING

De `ConvertTo-CSV` cmdlet retourneert een reeks teken reeksen met door komma's gescheiden waarden (CSV) die de objecten vertegenwoordigen die u verzendt. U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Csv` om objecten opnieuw te maken op basis van de CSV-teken reeksen. De objecten die zijn geconverteerd van CSV zijn teken reeks waarden van de oorspronkelijke objecten die eigenschaps waarden en geen methoden bevatten.

U kunt de `Export-Csv` cmdlet gebruiken om objecten te converteren naar CSV-teken reeksen. `Export-CSV` is vergelijkbaar met `ConvertTo-CSV` , behalve dat de CSV-teken reeksen worden opgeslagen in een bestand.

De `ConvertTo-CSV` cmdlet bevat para meters om een ander scheidings teken dan een komma op te geven of gebruik de huidige cultuur als scheidings teken.

## VOORBEELDEN

### Voor beeld 1: een object converteren naar CSV

In dit voor beeld wordt een **proces** object geconverteerd naar een CSV-teken reeks.

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

De `Get-Process` cmdlet haalt het **proces** object op en gebruikt de para meter **name** om het Power Shell-proces op te geven. Het proces object wordt via de pijp lijn naar de `ConvertTo-CSV` cmdlet verzonden. De `ConvertTo-CSV` cmdlet converteert het object naar CSV-teken reeksen. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer.

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

De `Get-Date` cmdlet haalt het **DateTime** -object op en slaat het op in de `$Date` variabele. `ConvertTo-Csv`Met de cmdlet wordt het **DateTime** -object geconverteerd naar teken reeksen. De para meter **input object** maakt gebruik van het **DateTime** -object dat is opgeslagen in de `$Date` variabele. De **scheidings** parameter geeft een punt komma om de teken reeks waarden te scheiden. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer.

### Voor beeld 3: het Power shell-gebeurtenis logboek converteren naar CSV

In dit voor beeld wordt het Windows-gebeurtenis logboek voor Power shell geconverteerd naar een reeks CSV-teken reeksen.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

De `Get-Culture` cmdlet maakt gebruik van de geneste eigenschappen **Eigenschappen** en **ListSeparator** en geeft het standaard lijst scheidings teken van de huidige cultuur weer. De `Get-WinEvent` cmdlet haalt de gebeurtenis logboek objecten op en gebruikt de para meter **LogName** om de naam van het logboek bestand op te geven. De gebeurtenis logboek objecten worden naar de-cmdlet verzonden via de pijp lijn `ConvertTo-Csv` . `ConvertTo-Csv`Met de cmdlet worden gebeurtenis logboek objecten geconverteerd naar een reeks CSV-teken reeksen. De para meter **UseCulture** gebruikt het standaard lijst scheidings teken van de huidige cultuur als scheidings teken. De para meter **NoTypeInformation** verwijdert de **#TYPE** informatie uit de CSV-uitvoer.

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

- De eerste teken reeks bevat standaard de **#TYPE** informatie header, gevolgd door de volledig gekwalificeerde naam van het object type. Bijvoorbeeld **#TYPE System. Diagnostics. process**.
- Als **NoTypeInformation** wordt gebruikt, bevat de eerste teken reeks de kolom koppen. De headers bevatten de eigenschaps namen van het eerste object als een door komma's gescheiden lijst.
- De resterende teken reeksen bevatten door komma's gescheiden lijsten van de eigenschaps waarden van elk object.

Wanneer u meerdere objecten verzendt naar `ConvertTo-CSV` , worden `ConvertTo-CSV` de teken reeksen door gesorteerd op basis van de eigenschappen van het eerste object dat u verzendt. Als de resterende objecten niet beschikken over een van de opgegeven eigenschappen, is de eigenschaps waarde van dat object null, zoals wordt weer gegeven in twee opeenvolgende komma's. Als de resterende objecten extra eigenschappen hebben, worden die eigenschaps waarden genegeerd.

## GERELATEERDE KOPPELINGEN

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[Exporteren-CSV](Export-Csv.md)

[Import-Csv](Import-Csv.md)
