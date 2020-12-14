---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 2e2bd5474198745d72ad2b87c3c305695a198f22
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705686"
---
# <span data-ttu-id="973a9-102">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="973a9-102">Write-Progress</span></span>

## <span data-ttu-id="973a9-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="973a9-103">SYNOPSIS</span></span>
<span data-ttu-id="973a9-104">Hiermee wordt een voortgangs balk binnen een Power shell-opdracht venster weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="973a9-104">Displays a progress bar within a PowerShell command window.</span></span>

## <span data-ttu-id="973a9-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="973a9-105">SYNTAX</span></span>

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="973a9-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="973a9-106">DESCRIPTION</span></span>

<span data-ttu-id="973a9-107">Met de `Write-Progress` cmdlet wordt een voortgangs balk weer gegeven in een Power shell-opdracht venster met de status van een uitgevoerde opdracht of een script.</span><span class="sxs-lookup"><span data-stu-id="973a9-107">The `Write-Progress` cmdlet displays a progress bar in a PowerShell command window that depicts the status of a running command or script.</span></span> <span data-ttu-id="973a9-108">U kunt de indica toren selecteren die de balk weergeeft en de tekst die boven en onder de voortgangs balk wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="973a9-108">You can select the indicators that the bar reflects and the text that appears above and below the progress bar.</span></span>

## <span data-ttu-id="973a9-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="973a9-109">EXAMPLES</span></span>

### <span data-ttu-id="973a9-110">Voor beeld 1: de voortgang van een lus for weer geven</span><span class="sxs-lookup"><span data-stu-id="973a9-110">Example 1: Display the progress of a For loop</span></span>

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

<span data-ttu-id="973a9-111">Met deze opdracht wordt de voortgang weer gegeven van een for-lus die een aantal van 1 tot en met 100.</span><span class="sxs-lookup"><span data-stu-id="973a9-111">This command displays the progress of a For loop that counts from 1 to 100.</span></span>

<span data-ttu-id="973a9-112">De `Write-Progress` cmdlet bevat een kop status balk `Activity` , een status regel en de variabele `$i` (de teller in de for-lus), die de relatieve volledigheid van de taak aangeeft.</span><span class="sxs-lookup"><span data-stu-id="973a9-112">The `Write-Progress` cmdlet includes a status bar heading `Activity`, a status line, and the variable `$i` (the counter in the For loop), which indicates the relative completeness of the task.</span></span>

### <span data-ttu-id="973a9-113">Voor beeld 2: de voortgang van geneste lussen weer geven</span><span class="sxs-lookup"><span data-stu-id="973a9-113">Example 2: Display the progress of nested For loops</span></span>

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

<span data-ttu-id="973a9-114">In dit voor beeld wordt de voortgang weer gegeven van twee geneste lussen, die allemaal door een voortgangs balk worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="973a9-114">This example displays the progress of two nested For loops, each of which is represented by a progress bar.</span></span>

<span data-ttu-id="973a9-115">De `Write-Progress` opdracht voor de tweede voortgangs balk bevat de **id-** para meter die het onderscheidt van de eerste voortgangs balk.</span><span class="sxs-lookup"><span data-stu-id="973a9-115">The `Write-Progress` command for the second progress bar includes the **Id** parameter that distinguishes it from the first progress bar.</span></span>

<span data-ttu-id="973a9-116">Zonder de **id-** para meter worden de voortgangs balken op elkaar toegepast in plaats van dat ze een onder de andere worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="973a9-116">Without the **Id** parameter, the progress bars would be superimposed on each other instead of being displayed one below the other.</span></span>

### <span data-ttu-id="973a9-117">Voor beeld 3: de voortgang weer geven tijdens het zoeken naar een teken reeks</span><span class="sxs-lookup"><span data-stu-id="973a9-117">Example 3: Display the progress while searching for a string</span></span>

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

<span data-ttu-id="973a9-118">Met deze opdracht wordt de voortgang van een opdracht weer gegeven om de teken reeks "BIOS" in het systeem gebeurtenis logboek te vinden.</span><span class="sxs-lookup"><span data-stu-id="973a9-118">This command displays the progress of a command to find the string "bios" in the System event log.</span></span>

<span data-ttu-id="973a9-119">De waarde van de para meter **percentagevoltooid** wordt berekend door het aantal gebeurtenissen te delen dat is verwerkt `$I` door het totale aantal opgehaalde gebeurtenissen `$Events.count` en vervolgens te vermenigvuldigen met 100.</span><span class="sxs-lookup"><span data-stu-id="973a9-119">The **PercentComplete** parameter value is calculated by dividing the number of events that have been processed `$I` by the total number of events retrieved `$Events.count` and then multiplying that result by 100.</span></span>

### <span data-ttu-id="973a9-120">Voor beeld 4: voortgang weer geven voor elk niveau van een genest proces</span><span class="sxs-lookup"><span data-stu-id="973a9-120">Example 4: Display progress for each level of a nested process</span></span>

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

<span data-ttu-id="973a9-121">In dit voor beeld kunt u de **ParentId** -para meter gebruiken om een Inge sprongen uitvoer te hebben om de bovenliggende/onderliggende relaties weer te geven in de voortgang van elke stap.</span><span class="sxs-lookup"><span data-stu-id="973a9-121">In this example you can use the **ParentId** parameter to have indented output to show parent/child relationships in the progress of each step.</span></span>

## <span data-ttu-id="973a9-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="973a9-122">PARAMETERS</span></span>

### <span data-ttu-id="973a9-123">-Activiteit</span><span class="sxs-lookup"><span data-stu-id="973a9-123">-Activity</span></span>

<span data-ttu-id="973a9-124">Geeft de eerste regel tekst in de koptekst boven de status balk aan.</span><span class="sxs-lookup"><span data-stu-id="973a9-124">Specifies the first line of text in the heading above the status bar.</span></span>
<span data-ttu-id="973a9-125">In deze tekst wordt de activiteit beschreven waarvan de voortgang wordt gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="973a9-125">This text describes the activity whose progress is being reported.</span></span>

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

### <span data-ttu-id="973a9-126">-Voltooid</span><span class="sxs-lookup"><span data-stu-id="973a9-126">-Completed</span></span>

<span data-ttu-id="973a9-127">Hiermee wordt aangegeven of de voortgangs balk wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="973a9-127">Indicates whether the progress bar is visible.</span></span>
<span data-ttu-id="973a9-128">Als deze para meter wordt wegge laten, `Write-Progress` wordt de voortgangs gegevens weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="973a9-128">If this parameter is omitted, `Write-Progress` displays progress information.</span></span>

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

### <span data-ttu-id="973a9-129">-CurrentOperation</span><span class="sxs-lookup"><span data-stu-id="973a9-129">-CurrentOperation</span></span>

<span data-ttu-id="973a9-130">Hiermee geeft u de tekst regel onder de voortgangs balk op.</span><span class="sxs-lookup"><span data-stu-id="973a9-130">Specifies the line of text below the progress bar.</span></span>
<span data-ttu-id="973a9-131">Met deze tekst wordt de bewerking beschreven die momenteel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="973a9-131">This text describes the operation that is currently taking place.</span></span>

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

### <span data-ttu-id="973a9-132">-Id</span><span class="sxs-lookup"><span data-stu-id="973a9-132">-Id</span></span>

<span data-ttu-id="973a9-133">Hiermee geeft u een ID op waarmee elke voortgangs balk wordt onderscheiden van de andere.</span><span class="sxs-lookup"><span data-stu-id="973a9-133">Specifies an ID that distinguishes each progress bar from the others.</span></span> <span data-ttu-id="973a9-134">Gebruik deze para meter wanneer u meer dan één voortgangs balk in één opdracht maakt.</span><span class="sxs-lookup"><span data-stu-id="973a9-134">Use this parameter when you are creating more than one progress bar in a single command.</span></span> <span data-ttu-id="973a9-135">Als de voortgangs balken geen andere Id's hebben, worden ze in plaats van weer gegeven in een reeks.</span><span class="sxs-lookup"><span data-stu-id="973a9-135">If the progress bars do not have different IDs, they are superimposed instead of being displayed in a series.</span></span>

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

### <span data-ttu-id="973a9-136">-ParentId</span><span class="sxs-lookup"><span data-stu-id="973a9-136">-ParentId</span></span>

<span data-ttu-id="973a9-137">Hiermee geeft u de bovenliggende activiteit van de huidige activiteit.</span><span class="sxs-lookup"><span data-stu-id="973a9-137">Specifies the parent activity of the current activity.</span></span>
<span data-ttu-id="973a9-138">Gebruik de waarde-1 als de huidige activiteit geen bovenliggende activiteit heeft.</span><span class="sxs-lookup"><span data-stu-id="973a9-138">Use the value -1 if the current activity has no parent activity.</span></span>

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

### <span data-ttu-id="973a9-139">-Percentagevoltooid</span><span class="sxs-lookup"><span data-stu-id="973a9-139">-PercentComplete</span></span>

<span data-ttu-id="973a9-140">Hiermee geeft u het percentage van de activiteit dat is voltooid.</span><span class="sxs-lookup"><span data-stu-id="973a9-140">Specifies the percentage of the activity that is completed.</span></span>
<span data-ttu-id="973a9-141">Gebruik de waarde-1 als het percentage voltooid onbekend of niet van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="973a9-141">Use the value -1 if the percentage complete is unknown or not applicable.</span></span>

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

### <span data-ttu-id="973a9-142">-SecondsRemaining</span><span class="sxs-lookup"><span data-stu-id="973a9-142">-SecondsRemaining</span></span>

<span data-ttu-id="973a9-143">Hiermee geeft u het aantal resterende seconden op totdat de activiteit is voltooid.</span><span class="sxs-lookup"><span data-stu-id="973a9-143">Specifies the projected number of seconds remaining until the activity is completed.</span></span>
<span data-ttu-id="973a9-144">Gebruik de waarde-1 als het aantal resterende seconden onbekend of niet van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="973a9-144">Use the value -1 if the number of seconds remaining is unknown or not applicable.</span></span>

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

### <span data-ttu-id="973a9-145">-SourceId</span><span class="sxs-lookup"><span data-stu-id="973a9-145">-SourceId</span></span>

<span data-ttu-id="973a9-146">Hiermee geeft u de bron van de record op.</span><span class="sxs-lookup"><span data-stu-id="973a9-146">Specifies the source of the record.</span></span> <span data-ttu-id="973a9-147">U kunt deze gebruiken in plaats van **id** , maar kan niet worden gebruikt met andere para meters zoals **ParentId**.</span><span class="sxs-lookup"><span data-stu-id="973a9-147">You can use this in place of **Id** but cannot be used with other parameters like **ParentId**.</span></span>

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

### <span data-ttu-id="973a9-148">-Status</span><span class="sxs-lookup"><span data-stu-id="973a9-148">-Status</span></span>

<span data-ttu-id="973a9-149">Geeft de tweede regel tekst in de kop boven de status balk aan.</span><span class="sxs-lookup"><span data-stu-id="973a9-149">Specifies the second line of text in the heading above the status bar.</span></span>
<span data-ttu-id="973a9-150">In deze tekst wordt de huidige status van de activiteit beschreven.</span><span class="sxs-lookup"><span data-stu-id="973a9-150">This text describes current state of the activity.</span></span>

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

### <span data-ttu-id="973a9-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="973a9-151">CommonParameters</span></span>

<span data-ttu-id="973a9-152">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="973a9-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="973a9-153">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="973a9-153">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="973a9-154">INVOER</span><span class="sxs-lookup"><span data-stu-id="973a9-154">INPUTS</span></span>

### <span data-ttu-id="973a9-155">Geen</span><span class="sxs-lookup"><span data-stu-id="973a9-155">None</span></span>

<span data-ttu-id="973a9-156">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="973a9-156">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="973a9-157">UITVOER</span><span class="sxs-lookup"><span data-stu-id="973a9-157">OUTPUTS</span></span>

### <span data-ttu-id="973a9-158">Geen</span><span class="sxs-lookup"><span data-stu-id="973a9-158">None</span></span>

<span data-ttu-id="973a9-159">`Write-Progress` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="973a9-159">`Write-Progress` does not generate any output.</span></span>

## <span data-ttu-id="973a9-160">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="973a9-160">NOTES</span></span>

<span data-ttu-id="973a9-161">Als de voortgangs balk niet wordt weer gegeven, controleert u de waarde van de `$ProgressPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="973a9-161">If the progress bar does not appear, check the value of the `$ProgressPreference` variable.</span></span> <span data-ttu-id="973a9-162">Als de waarde is ingesteld op SilentlyContinue, wordt de voortgangs balk niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="973a9-162">If the value is set to SilentlyContinue, the progress bar is not displayed.</span></span> <span data-ttu-id="973a9-163">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie over Power shell-voor keuren.</span><span class="sxs-lookup"><span data-stu-id="973a9-163">For more information about PowerShell preferences, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="973a9-164">De para meters van de cmdlet komen overeen met de eigenschappen van de klasse **System. Management. Automation. ProgressRecord** .</span><span class="sxs-lookup"><span data-stu-id="973a9-164">The parameters of the cmdlet correspond to the properties of the **System.Management.Automation.ProgressRecord** class.</span></span> <span data-ttu-id="973a9-165">Zie [ProgressRecord class](/dotnet/api/system.management.automation.progressrecord)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="973a9-165">For more information, see [ProgressRecord Class](/dotnet/api/system.management.automation.progressrecord).</span></span>

## <span data-ttu-id="973a9-166">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="973a9-166">RELATED LINKS</span></span>

[<span data-ttu-id="973a9-167">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="973a9-167">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="973a9-168">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="973a9-168">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="973a9-169">Write-host</span><span class="sxs-lookup"><span data-stu-id="973a9-169">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="973a9-170">Write-output</span><span class="sxs-lookup"><span data-stu-id="973a9-170">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="973a9-171">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="973a9-171">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="973a9-172">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="973a9-172">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="973a9-173">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="973a9-173">Write-Warning</span></span>](Write-Warning.md)
