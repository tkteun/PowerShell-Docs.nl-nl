---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: 646d186b34e31aa2572aeefa12cc73d941076a13
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249515"
---
# Start-Trace

## SAMENVATTING
Start een logboek registratie sessie voor gebeurtenis tracering.

## SYNTAXIS

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## BESCHRIJVING
Met deze cmdlet wordt een Windows-sessie voor logboek registratie van gebeurtenissen gestart.

Deze cmdlet wordt gebruikt door de volgende cmdlets:

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: een sessie met WSMan-traceer logboek registratie starten

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## PARAMETERS

### -BufferSizeInKB
Buffer grootte voor de gebeurtenis tracerings sessie in kilo bytes (KB).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -ETS
Opdrachten zonder opslaan of plannen rechtstreeks naar Gebeurtenissessies Trace kunnen verzenden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Indeling
Hiermee geeft u de indeling voor de gegevensverzamelaar. Voor SQL database indeling moet u de optie **OutputFilePath** in de opdracht regel gebruiken met de `dsn!log` waarde. De standaard waarde is binary (bin). De mogelijke waarden zijn:

- bin-binary
- bincirc-binary met circulaire logboek registratie
- CSV-door Komma's gescheiden waarden
- TSV-door tabs gescheiden waarden
- SQL-SQL database

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxBuffers
Hiermee stelt u het maximum aantal buffers voor gebeurtenis tracerings sessies.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxLogFileSizeInMB
Hiermee stelt u de maximale grootte van het logboek bestand in mega bytes (MB) of het aantal records voor SQL-logboeken.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinBuffers
Hiermee stelt u het minimum aantal buffers voor gebeurtenis tracerings sessies.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputFilePath
Pad van het uitvoer logboek bestand of de naam van de DSN en logboekset in een SQL database. Het standaardpad is `$env:systemdrive\PerfLogs\Admin` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderFilePath
Bestand waarin meerdere gebeurtenistraceerproviders worden weer gegeven om in te scha kelen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie naam
De naam van de gebeurtenistraceersessie. Als u een tracerings sessie wilt stoppen, moet u de sessie naam weten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### Geen

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Gebeurtenis tracering](/windows/desktop/ETW/event-tracing-portal)

[Stoppen-traceren](stop-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)

[Enable-PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)

[Enable-WSManTrace](Enable-WSManTrace.md)
