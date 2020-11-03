---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 5a0c197387f67dae1830b6d9ebd4145e96383b39
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253006"
---
# Write-Progress

## SAMENVATTING
Hiermee wordt een voortgangs balk binnen een Power shell-opdracht venster weer gegeven.

## SYNTAXIS

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de `Write-Progress` cmdlet wordt een voortgangs balk weer gegeven in een Power shell-opdracht venster met de status van een uitgevoerde opdracht of een script. U kunt de indica toren selecteren die de balk weergeeft en de tekst die boven en onder de voortgangs balk wordt weer gegeven.

## VOORBEELDEN

### Voor beeld 1: de voortgang van een lus for weer geven

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

Met deze opdracht wordt de voortgang weer gegeven van een for-lus die een aantal van 1 tot en met 100.

De `Write-Progress` cmdlet bevat een kop status balk `Activity` , een status regel en de variabele `$i` (de teller in de for-lus), die de relatieve volledigheid van de taak aangeeft.

### Voor beeld 2: de voortgang van geneste lussen weer geven

```powershell
for($I = 1; $I -lt 101; $I++ )
{
    Write-Progress -Activity Updating -Status 'Progress->' -PercentComplete $I -CurrentOperation OuterLoop
    for($j = 1; $j -lt 101; $j++ )
    {
        Write-Progress -Id 1 -Activity Updating -Status 'Progress' -PercentComplete $j -CurrentOperation InnerLoop
    }
}
```

```Output
Updating
Progress ->
 [ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo]
OuterLoop
Updating
Progress
 [oooooooooooooooooo                                                   ]
InnerLoop
```

In dit voor beeld wordt de voortgang weer gegeven van twee geneste lussen, die allemaal door een voortgangs balk worden weer gegeven.

De `Write-Progress` opdracht voor de tweede voortgangs balk bevat de **id-** para meter die het onderscheidt van de eerste voortgangs balk.

Zonder de **id-** para meter worden de voortgangs balken op elkaar toegepast in plaats van dat ze een onder de andere worden weer gegeven.

### Voor beeld 3: de voortgang weer geven tijdens het zoeken naar een teken reeks

```powershell
# Use Get-EventLog to get the events in the System log and store them in the $Events variable.
$Events = Get-EventLog -LogName system
# Pipe the events to the ForEach-Object cmdlet.
$Events | ForEach-Object -Begin {
    # In the Begin block, use Clear-Host to clear the screen.
    Clear-Host
    # Set the $i counter variable to zero.
    $i = 0
    # Set the $out variable to a empty string.
    $out = ""
} -Process {
    # In the Process script block search the message property of each incoming object for "bios".
    if($_.message -like "*bios*")
    {
        # Append the matching message to the out variable.
        $out=$out + $_.Message
    }
    # Increment the $i counter variable which is used to create the progress bar.
    $i = $i+1
    # Use Write-Progress to output a progress bar.
    # The Activity and Status parameters create the first and second lines of the progress bar heading, respectively.
    Write-Progress -Activity "Searching Events" -Status "Progress:" -PercentComplete ($i/$Events.count*100)
} -End {
    # Display the matching messages using the out variable.
    $out
}
```

Met deze opdracht wordt de voortgang van een opdracht weer gegeven om de teken reeks "BIOS" in het systeem gebeurtenis logboek te vinden.

De waarde van de para meter **percentagevoltooid** wordt berekend door het aantal gebeurtenissen te delen dat is verwerkt `$I` door het totale aantal opgehaalde gebeurtenissen `$Events.count` en vervolgens te vermenigvuldigen met 100.

### Voor beeld 4: voortgang weer geven voor elk niveau van een genest proces

```powershell
foreach ( $i in 1..10 ) {
  Write-Progress -Id 0 "Step $i"
  foreach ( $j in 1..10 ) {
    Write-Progress -Id 1 -ParentId 0 "Step $i - Substep $j"
    foreach ( $k in 1..10 ) {
      Write-Progress -Id 2  -ParentId 1 "Step $i - Substep $j - iteration $k"; start-sleep -m 150
    }
  }
}
```

```Output
Step 1
     Processing
    Step 1 - Substep 2
         Processing
        Step 1 - Substep 2 - Iteration 3
             Processing
```

In dit voor beeld kunt u de **ParentId** -para meter gebruiken om een Inge sprongen uitvoer te hebben om de bovenliggende/onderliggende relaties weer te geven in de voortgang van elke stap.

## PARAMETERS

### -Activiteit

Geeft de eerste regel tekst in de koptekst boven de status balk aan.
In deze tekst wordt de activiteit beschreven waarvan de voortgang wordt gerapporteerd.

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

### -Voltooid

Hiermee wordt aangegeven of de voortgangs balk wordt weer gegeven.
Als deze para meter wordt wegge laten, `Write-Progress` wordt de voortgangs gegevens weer gegeven.

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

### -CurrentOperation

Hiermee geeft u de tekst regel onder de voortgangs balk op.
Met deze tekst wordt de bewerking beschreven die momenteel wordt uitgevoerd.

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

### -Id

Hiermee geeft u een ID op waarmee elke voortgangs balk wordt onderscheiden van de andere. Gebruik deze para meter wanneer u meer dan één voortgangs balk in één opdracht maakt. Als de voortgangs balken geen andere Id's hebben, worden ze in plaats van weer gegeven in een reeks.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParentId

Hiermee geeft u de bovenliggende activiteit van de huidige activiteit.
Gebruik de waarde-1 als de huidige activiteit geen bovenliggende activiteit heeft.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Percentagevoltooid

Hiermee geeft u het percentage van de activiteit dat is voltooid.
Gebruik de waarde-1 als het percentage voltooid onbekend of niet van toepassing is.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondsRemaining

Hiermee geeft u het aantal resterende seconden op totdat de activiteit is voltooid.
Gebruik de waarde-1 als het aantal resterende seconden onbekend of niet van toepassing is.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceId

Hiermee geeft u de bron van de record op. U kunt deze gebruiken in plaats van **id** , maar kan niet worden gebruikt met andere para meters zoals **ParentId**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

Geeft de tweede regel tekst in de kop boven de status balk aan.
In deze tekst wordt de huidige status van de activiteit beschreven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen

`Write-Progress` Er wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Als de voortgangs balk niet wordt weer gegeven, controleert u de waarde van de `$ProgressPreference` variabele. Als de waarde is ingesteld op SilentlyContinue, wordt de voortgangs balk niet weer gegeven. Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie over Power shell-voor keuren.

De para meters van de cmdlet komen overeen met de eigenschappen van de klasse **System. Management. Automation. ProgressRecord** . Zie [ProgressRecord class](/dotnet/api/system.management.automation.progressrecord)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Schrijf fouten opsporen](Write-Debug.md)

[Schrijf fout](Write-Error.md)

[Write-host](Write-Host.md)

[Write-output](Write-Output.md)

[Schrijf voortgang](Write-Progress.md)

[Write-verbose](Write-Verbose.md)

[Waarschuwing voor schrijven](Write-Warning.md)
