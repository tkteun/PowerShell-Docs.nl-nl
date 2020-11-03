---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252123"
---
# Export-Counter

## SAMENVATTING
Exporteert gegevens van prestatie meter items naar logboek bestanden.

## SYNTAXIS

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## BESCHRIJVING

De `Export-Counter` cmdlet exporteert gegevens over prestatie meter items (PerformanceCounterSampleSet-objecten) naar logboek bestanden in een binair prestatie logboek (. blg), door komma's gescheiden waarden (. CSV) of door tabs gescheiden waarden (. tsv). Met deze cmdlet kunt u gegevens van prestatie meter items registreren.

De `Export-Counter` cmdlet is ontworpen voor het exporteren van gegevens die worden geretourneerd door de- `Get-Counter` en- `Import-Counter` cmdlets.

Deze cmdlet kan alleen worden uitgevoerd op Windows 7, Windows Server 2008 R2 en latere versies van Windows.

## VOORBEELDEN

### VOOR beeld 1: item gegevens exporteren naar een bestand

In dit voor beeld worden item gegevens geëxporteerd naar een BLG-bestand.

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

De opdracht gebruikt de `Get-Counter` cmdlet voor het verzamelen van processor tijd gegevens. Er wordt gebruikgemaakt van een pijplijn operator (|) voor het verzenden van de gegevens naar de `Export-Counter` cmdlet. De `Export-Counter` opdracht gebruikt de **padvariabele** om het uitvoer bestand op te geven.

Omdat de gegevensset mogelijk erg groot is, verzendt dit voor beeld de gegevens naar `Export-Counter` via de pijp lijn. Als de gegevens zijn opgeslagen in een variabele, kunt u een onevenredige hoeveelheid geheugen gebruiken.

### Voor beeld 2: een bestand naar een bestands indeling voor een teller exporteren

In dit voor beeld wordt een CSV-bestand geconverteerd naar een teller data BLG-indeling.

`Import-Counter`Met de cmdlet worden prestatie meter gegevens uit het `Threads.csv` bestand geïmporteerd. In het voor beeld wordt ervan uitgegaan dat dit bestand eerder is geëxporteerd met behulp van de- `Export-Counter` cmdlet. Een pijplijn operator ( `|` ) verzendt de geïmporteerde gegevens naar de `Export-Counter` cmdlet. De opdracht gebruikt de para meter **Path** om de locatie van het uitvoer bestand op te geven. De para meters **circulair** en **MaxSize** worden gebruikt om de `Export-Counter` cmdlet te sturen om een circulair logboek te maken dat op 1 GB loopt. De **MaxSize** para meter wordt uitgedrukt in mega bytes.

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### Voor beeld 3: item gegevens ophalen van een externe computer en de gegevens opslaan in een bestand

In dit voor beeld ziet u hoe gegevens van een prestatie meter item worden opgehaald van een externe computer en dat de gegevens worden opgeslagen in een bestand op de externe computer.

Met de eerste opdracht wordt de `Get-Counter` cmdlet gebruikt voor het verzamelen van gegevens over de werkset van Server01, een externe computer. Met de opdracht worden de gegevens in de `$C` variabele opgeslagen.

De tweede opdracht maakt gebruik van een pijplijn operator ( `|` ) om de gegevens `$C` te verzenden naar de `Export-Counter` cmdlet. deze wordt opgeslagen in het `Workingset.blg` bestand in het gedeelte prestaties van de computer Server01.

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### Voor beeld 4: bestaande gegevens opnieuw registreren

In dit voor beeld ziet u hoe u de- `Import-Counter` en `Export-Counter` -cmdlets kunt gebruiken om bestaande gegevens opnieuw te registreren.

Met de eerste opdracht wordt de `Import-Counter` cmdlet gebruikt voor het importeren van gegevens uit het prestatie meter item uit het logboek DiskSpace. blg. De gegevens worden opgeslagen in de `$All` variabele. Dit bestand bevat voor beelden van het \% meter item ' beschik bare ruimte op de logische schijf ' op meer dan 200 externe computers in de onderneming.

De tweede opdracht gebruikt de `Where-Object` cmdlet om objecten te selecteren met **CookedValue** van minder dan 15 (procent). Met de opdracht worden de resultaten opgeslagen in de `$LowSpace` variabele.

De derde opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van de gegevens in de `$LowSpace` variabele naar de `Export-Counter` cmdlet. De opdracht gebruikt de para meter **Path** om aan te geven dat de geselecteerde gegevens moeten worden geregistreerd in het bestand LowDiskSpace. blg.

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## PARAMETERS

### -Circulair

Geeft aan dat het uitvoer bestand een circulaire logboek met FIFO-indeling (First in, first out) is.
Wanneer u deze para meter opneemt, is de para meter **MaxSize** vereist.

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

### -File Format

Hiermee geeft u de uitvoer indeling van het uitvoer logboek bestand.

De aanvaardbare waarden voor deze parameter zijn:

- CSV
- TSV
- BLG

De standaard waarde is BLG.

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

### -Force

Overschrijft en vervangt een bestaand bestand als er een bestaat op de locatie die is opgegeven door de para meter **Path** .

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

### -Input object

Geeft als een matrix de item gegevens aan die moeten worden geëxporteerd. Voer een variabele in die de gegevens bevat of een opdracht die de gegevens ophaalt, zoals de `Get-Counter` of- `Import-Counter` cmdlet.

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaxSize

Hiermee geeft u de maximale grootte van het uitvoer bestand in mega bytes (MB).

Als de **circulaire** para meter is opgegeven, wordt de oudste vermeldingen verwijderd wanneer het logboek bestand de opgegeven maximum grootte heeft bereikt. Als de **kring** veld niet is opgegeven, wordt er geen nieuwe gegevens toegevoegd en wordt er een niet-afsluit fout gegenereerd wanneer het logboek bestand de opgegeven maximum grootte heeft bereikt.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad en de bestands naam van het uitvoer bestand. Voer een relatief of absoluut pad op de lokale computer of een UNC-pad (Uniform Naming Convention) naar een externe computer, zoals `\\Computer\Share\file.blg` . Deze parameter is vereist.

De bestands indeling wordt bepaald door de waarde van de para meter **File Format** , niet door de bestandsnaam extensie in het pad.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet

U kunt prestatie meter gegevens van `Get-Counter` of `Import-Counter` naar deze cmdlet sluizen.

## UITVOER

### Geen

## OPMERKINGEN

De generator van het logboek bestand verwacht dat alle invoer objecten hetzelfde itempad hebben en dat de objecten in oplopende volg orde zijn gerangschikt.

Het item type en pad van het eerste invoer object bepalen welke eigenschappen in het logboek bestand worden vastgelegd. Als andere invoer objecten geen waarde voor een vastgelegde eigenschap hebben, is het veld van de eigenschap leeg. Als de objecten eigenschaps waarden hebben die niet zijn vastgelegd, worden de extra eigenschaps waarden genegeerd.

De prestatie meter kan mogelijk niet alle logboeken lezen die worden `Export-Counter` gegenereerd. Prestatie meter vereist bijvoorbeeld dat alle objecten hetzelfde pad hebben en dat alle objecten worden gescheiden door hetzelfde tijds interval.

De `Import-Counter` cmdlet heeft geen **ComputerName** -para meter. Als de computer echter is geconfigureerd voor externe Windows Power shell Windows Power shell, kunt u de `Invoke-Command` cmdlet gebruiken om een opdracht uit te voeren `Import-Counter` op een externe computer.

## GERELATEERDE KOPPELINGEN

[Get-teller](Get-Counter.md)

[Import teller](Import-Counter.md)
