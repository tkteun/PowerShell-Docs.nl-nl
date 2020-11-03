---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/import-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Counter
ms.openlocfilehash: 837f6b4b3b2869c6f74b3b02904dd43b73f6bcd5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250119"
---
# Import-Counter

## SAMENVATTING
Importeert logboek bestanden voor prestatie meter items en maakt de objecten die elk item voorbeeld vertegenwoordigen in het logboek.

## SYNTAXIS

### GetCounterSet (standaard)

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### ListSetSet

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### Samenvattings

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **import-Counter** worden prestatie meter gegevens uit logboek bestanden voor prestatie meter items geïmporteerd en worden objecten gemaakt voor elk item voorbeeld in het bestand.
De **PerformanceCounterSampleSet** -objecten die worden gemaakt, zijn identiek aan de objecten die **Get-Counter** retourneert wanneer er prestatie meter gegevens worden verzameld.

U kunt gegevens importeren uit een bestand met door komma's gescheiden waarden (. CSV), een door tabs gescheiden waarde (. tsv) en logboek bestanden met de prestatie meter binary (. blg).
Als u. blg-bestanden gebruikt, kunt u Maxi maal 32 bestanden importeren in elke opdracht.
U kunt de para meters van **import teller** gebruiken om de geïmporteerde gegevens te filteren.

Met de Get-Counter-en Export-Counter-cmdlets kunt u met deze functie gegevens over prestatie meter items verzamelen, exporteren, importeren, combi neren, filteren, bewerken en opnieuw exporteren in Windows Power shell.

## VOORBEELDEN

### Voor beeld 1: alle item gegevens uit een bestand importeren

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

Met deze opdracht worden alle item gegevens uit het ProcessorData.csv-bestand in de $Data-variabele geïmporteerd.

### Voor beeld 2: specifieke item gegevens uit een bestand importeren

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

Met deze opdracht worden alleen de item gegevens **' processor (_Total) \ interrupts/sec '** uit het bestand ProcessorData. blg geïmporteerd in de $I-variabele.

### Voor beeld 3: gegevens selecteren uit een prestatie meter item en deze vervolgens exporteren naar een bestand

```
The first command uses **Import-Counter** to import all of the performance counter data from the ProcessorData.blg files. The command saves the data in the $Data variable.
PS C:\> $Data = Import-Counter .\ProcessorData.blg

The second command displays the counter paths in the $Data variable. To get the display shown in the command output, the example uses the Format-Table cmdlet to format as a table the counter paths of the first counter in the $Data variable.
PS C:\> $Data[0].CounterSamples | Format-Table -Property Path

Path
----
\\SERVER01\Processor(_Total)\DPC Rate
\\SERVER01\Processor(1)\DPC Rate
\\SERVER01\Processor(0)\DPC Rate
\\SERVER01\Processor(_Total)\% Idle Time
\\SERVER01\Processor(1)\% Idle Time
\\SERVER01\Processor(0)\% Idle Time
\\SERVER01\Processor(_Total)\% C3 Time
\\SERVER01\Processor(1)\% C3 Time

The third command gets the counter paths that end in "Interrupts/sec" and saves the paths in the $IntCtrs variable. It uses the Where-Object cmdlet to filter the counter paths and the ForEach-Object cmdlet to get only the value of the **Path** property of each selected path object.
PS C:\> $IntCtrs = $Data[0].Countersamples | Where-Object {$_.Path -like "*Interrupts/sec"} | ForEach-Object {$_.Path}

The fourth command displays the selected counter paths in the $IntCtrs variable.
PS C:\> $IntCtrs

\\SERVER01\Processor(_Total)\Interrupts/sec
\\SERVER01\Processor(1)\Interrupts/sec
\\SERVER01\Processor(0)\Interrupts/sec

The fifth command uses the **Import-Counter** cmdlet to import the data. It uses the $IntCtrs variable as the value of the *Counter* parameter to import only data for the counter paths in $IntCtrs.
PS C:\> $I = Import-Counter -Path .\ProcessorData.blg -Counter $intCtrs

The sixth command uses the Export-Counter cmdlet to export the data to the Interrupts.csv file.
PS C:\> $I | Export-Counter -Path .\Interrupts.csv -Format CSV
```

In dit voor beeld ziet u hoe u gegevens selecteert uit een logboek bestand voor prestatie meter items (. blg) en hoe u de geselecteerde gegevens vervolgens exporteert naar een CSV-bestand.
Met de eerste vier opdrachten worden de item paden opgehaald uit het bestand en opgeslagen in de variabele met de naam $Data.
De laatste twee opdrachten importeren geselecteerde gegevens en exporteren alleen de geselecteerde gegevens.

### Voor beeld 4: alle item paden weer geven in een groep met geïmporteerde item sets

```
The first command uses the *ListSet* parameter of the **Import-Counter** cmdlet to get all of the counter sets that are represented in a counter data file.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet *

CounterSetName     : Processor
MachineName        : \\SERVER01
CounterSetType     : MultiInstance
Description        :
Paths              : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}
PathsWithInstances : {\\SERVER01\Processor(_Total)\DPC Rate, \\SERVER01\Processor(1)\DPC Rate, \\SERVER01
\Processor(0)\DPC Rate, \\SERVER01\Processor(_Total)\% Idle Time...}
Counter            : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}

The second command gets all of the counter paths from the list set.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet * | ForEach-Object {$_.Paths}

\\SERVER01\Processor(*)\DPC Rate
\\SERVER01\Processor(*)\% Idle Time
\\SERVER01\Processor(*)\% C3 Time
\\SERVER01\Processor(*)\% Interrupt Time
\\SERVER01\Processor(*)\% C2 Time
\\SERVER01\Processor(*)\% User Time
\\SERVER01\Processor(*)\% C1 Time
\\SERVER01\Processor(*)\% Processor Time
\\SERVER01\Processor(*)\C1 Transitions/sec
\\SERVER01\Processor(*)\% DPC Time
\\SERVER01\Processor(*)\C2 Transitions/sec
\\SERVER01\Processor(*)\% Privileged Time
\\SERVER01\Processor(*)\C3 Transitions/sec
\\SERVER01\Processor(*)\DPCs Queued/sec
\\SERVER01\Processor(*)\Interrupts/sec
```

In dit voor beeld ziet u hoe alle item paden worden weer gegeven in een groep met geïmporteerde item sets.

### Voor beeld 5: item gegevens importeren uit een bereik van tijds tempels

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

In dit voor beeld worden alleen de prestatie meter items geïmporteerd die een tijds tempel hebben tussen het begin van een eindigend bereik dat is opgegeven in de opdracht.

### Voor beeld 6: een opgegeven aantal oudste voor beelden importeren uit een logboek bestand voor prestatie meter items

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

In dit voor beeld ziet u hoe u de vijf oudste en vijf meest recente steek proeven importeert uit een logboek bestand voor prestatie meter items.

### Voor beeld 7: een samen vatting van item gegevens uit een bestand ophalen

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

Met deze opdracht wordt de *samenvattings* parameter van de cmdlet **import-Counter** gebruikt om een samen vatting van de item gegevens in het bestand Memory. blg weer te geven.

### Voor beeld 8: een logboek bestand voor prestatie meter items bijwerken

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

In dit voor beeld wordt een logboek bestand voor prestatie meter items bijgewerkt.

### Voor beeld 9: prestatie logboek gegevens importeren uit meerdere bestanden en deze vervolgens opslaan

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

Met deze opdracht worden prestatie logboek gegevens uit twee logboeken geïmporteerd en worden de gegevens opgeslagen in de variabele $Counters.
De opdracht maakt gebruik van een pijplijn operator voor het verzenden van de prestatie logboek paden naar import teller, waarmee de gegevens uit de opgegeven paden worden geïmporteerd.

U ziet dat elk pad tussen aanhalings tekens staat en dat de paden van elkaar worden gescheiden door een komma.

## PARAMETERS

### -Teller

Hiermee geeft u als een teken reeks matrix de prestatie meter items op.
**Import-Counter** importeert standaard alle gegevens uit alle items in de invoer bestanden.
Voer een of meer teller paden in.
Joker tekens zijn toegestaan in het gedeelte exemplaar van het pad.

Elk itempad heeft de volgende indeling.
De waarde ComputerName is vereist in het pad.
Bijvoorbeeld:

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

Bijvoorbeeld:

- `\\Server01\Processor(2)\% User Time`
- `\\Server01\Processor(*)\% Processor Time`

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: All counter
Accept pipeline input: False
Accept wildcard characters: True
```

### -EndTime

Hiermee geeft u een eind datum en-tijd op die met deze cmdlet item gegevens worden geïmporteerd tussen de *StartTime* en de tijds tempel van deze para meter.
Voer een **DateTime** -object in, zoals een dat is gemaakt door de cmdlet Get-Date.
**Import-Counter** importeert standaard alle item gegevens in de bestanden die zijn opgegeven met de para meter *Path* .

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No end time
Accept pipeline input: False
Accept wildcard characters: False
```

### -Lijstset

Hiermee geeft u de prestatie meter sets op die in de geëxporteerde bestanden worden weer gegeven.
Met de opdrachten met deze para meter worden geen gegevens geïmporteerd.

Voer een of meer namen van tellers sets in.
Joker tekens zijn toegestaan.
Als u alle item sets in het bestand wilt ophalen, typt u `Import-Counter -ListSet *` .

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -MaxSamples

Hiermee geeft u het maximum aantal steek proeven op voor elk item dat u wilt importeren.
Standaard worden met **Get-Counter** alle gegevens geïmporteerd uit de bestanden die zijn opgegeven met de para meter *Path* .

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No maximum
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u de bestands paden op van de bestanden die moeten worden geïmporteerd.
Deze parameter is vereist.

Voer het pad en de bestands naam in van een, CSV,,. TSV-of. blg-bestand dat u hebt geëxporteerd met de cmdlet **export-Counter** .
U kunt slechts één CSV-of TSV-bestand opgeven, maar u kunt meerdere. blg-bestanden (Maxi maal 32) in elke opdracht opgeven.
U kunt ook teken reeksen van het bestandspad (tussen aanhalings tekens) naar **import teller**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StartTime

Hiermee geeft u de begin datum en-tijd op waarop deze cmdlet item gegevens ophaalt.
Voer een **DateTime** -object in, zoals een, gemaakt door de cmdlet **Get-date** .
**Import-Counter** importeert standaard alle item gegevens in de bestanden die zijn opgegeven met de para meter *Path* .

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No start time
Accept pipeline input: False
Accept wildcard characters: False
```

### -Samen vatting

Hiermee wordt aangegeven dat met deze cmdlet een samen vatting van de geïmporteerde gegevens wordt opgehaald, in plaats van afzonderlijke meter gegevens voor beelden te verkrijgen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SummarySet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt de logboek paden voor prestatie meter items door sluizen naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. GetCounter. PerformanceCounterSampleSet, micro soft. Power shell. commands. GetCounter. Counterset, micro soft. Power shell. commands. GetCounter. CounterFileInfo

Met deze cmdlet wordt een **Microsoft. Power shell. commands. GetCounter. PerformanceCounterSampleSet** geretourneerd.
Als u de *listset* -para meter gebruikt, retourneert deze cmdlet een **micro soft. Power shell. commands. GetCounter. counterset** -object.
Als u de para meter *Summary* gebruikt, retourneert deze cmdlet een object **micro soft. Power shell. commands. GetCounter. CounterFileInfo** .

## OPMERKINGEN

* Deze cmdlet heeft geen *ComputerName* -para meter. Als de computer echter is geconfigureerd voor externe communicatie met Windows Power shell, kunt u de cmdlet Invoke-Command gebruiken om een opdracht voor het **importeren van items** uit te voeren op een externe computer.

## GERELATEERDE KOPPELINGEN

[Exporteren-teller](Export-Counter.md)

[Get-teller](Get-Counter.md)
