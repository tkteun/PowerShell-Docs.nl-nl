---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: b5c09c9483250930f35eea5f480f2ca0a203445b
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "96777707"
---
# <span data-ttu-id="555dc-102">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="555dc-102">Start-ThreadJob</span></span>

## <span data-ttu-id="555dc-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="555dc-103">SYNOPSIS</span></span>
<span data-ttu-id="555dc-104">Maakt achtergrond taken die vergelijkbaar zijn met de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="555dc-104">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>

## <span data-ttu-id="555dc-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="555dc-105">SYNTAX</span></span>

### <span data-ttu-id="555dc-106">Script Block</span><span class="sxs-lookup"><span data-stu-id="555dc-106">ScriptBlock</span></span>

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### <span data-ttu-id="555dc-107">Bestandspad</span><span class="sxs-lookup"><span data-stu-id="555dc-107">FilePath</span></span>

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## <span data-ttu-id="555dc-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="555dc-108">DESCRIPTION</span></span>

<span data-ttu-id="555dc-109">`Start-ThreadJob` maakt achtergrond taken die vergelijkbaar zijn met de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="555dc-109">`Start-ThreadJob` creates background jobs similar to the `Start-Job` cmdlet.</span></span> <span data-ttu-id="555dc-110">Het belangrijkste verschil is dat de taken die worden gemaakt in afzonderlijke threads binnen het lokale proces worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="555dc-110">The main difference is that the jobs which are created run in separate threads within the local process.</span></span> <span data-ttu-id="555dc-111">De taken gebruiken standaard de huidige werkmap van de aanroeper die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="555dc-111">By default, the jobs use the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="555dc-112">De cmdlet biedt ook ondersteuning voor de para meter **ThrottleLimit** om het aantal taken dat tegelijk wordt uitgevoerd, te beperken.</span><span class="sxs-lookup"><span data-stu-id="555dc-112">The cmdlet also supports a **ThrottleLimit** parameter to limit the number of jobs running at one time.</span></span> <span data-ttu-id="555dc-113">Naarmate er meer taken worden gestart, worden deze in de wachtrij geplaatst en gewacht totdat het huidige aantal taken onder de vertragings limiet valt.</span><span class="sxs-lookup"><span data-stu-id="555dc-113">As more jobs are started, they are queued and wait until the current number of jobs drops below the throttle limit.</span></span>

## <span data-ttu-id="555dc-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="555dc-114">EXAMPLES</span></span>

### <span data-ttu-id="555dc-115">Voor beeld 1: Maak achtergrond taken met een thread limiet van 2</span><span class="sxs-lookup"><span data-stu-id="555dc-115">Example 1 - Create background jobs with a thread limit of 2</span></span>

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### <span data-ttu-id="555dc-116">Voor beeld 2: de prestaties van Start-Job en Start-ThreadJob vergelijken</span><span class="sxs-lookup"><span data-stu-id="555dc-116">Example 2 - Compare the performance of Start-Job and Start-ThreadJob</span></span>

<span data-ttu-id="555dc-117">In dit voor beeld ziet u het verschil tussen `Start-Job` en `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="555dc-117">This example shows the difference between `Start-Job` and `Start-ThreadJob`.</span></span> <span data-ttu-id="555dc-118">De taken voeren de `Start-Sleep` cmdlet uit voor 1 seconde.</span><span class="sxs-lookup"><span data-stu-id="555dc-118">The jobs run the `Start-Sleep` cmdlet for 1 second.</span></span> <span data-ttu-id="555dc-119">Omdat de taken parallel worden uitgevoerd, is de totale uitvoerings tijd ongeveer 1 seconde, plus de tijd die nodig is om de taken te maken.</span><span class="sxs-lookup"><span data-stu-id="555dc-119">Since the jobs run in parallel, the total execution time is about 1 second, plus any time required to create the jobs.</span></span>

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

<span data-ttu-id="555dc-120">Nadat 1 seconde voor uitvoerings tijd is afgetrokken, ziet u dat `Start-Job` ongeveer 4,8 seconden duren om vijf taken te maken.</span><span class="sxs-lookup"><span data-stu-id="555dc-120">After subtracting 1 second for execution time, you can see that `Start-Job` takes about 4.8 seconds to create five jobs.</span></span> <span data-ttu-id="555dc-121">`Start-ThreadJob` is 8 keer sneller, met ongeveer 0,6 seconden om vijf taken te maken.</span><span class="sxs-lookup"><span data-stu-id="555dc-121">`Start-ThreadJob` is 8 times faster, taking about 0.6 seconds to create five jobs.</span></span> <span data-ttu-id="555dc-122">De resultaten kunnen variëren in uw omgeving, maar de relatieve verbetering moet hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="555dc-122">The results may vary in your environment but the relative improvement should be the same.</span></span>

### <span data-ttu-id="555dc-123">Voor beeld 3: taken maken met input object</span><span class="sxs-lookup"><span data-stu-id="555dc-123">Example 3 - Create jobs using InputObject</span></span>

<span data-ttu-id="555dc-124">In dit voor beeld gebruikt het script blok de `$input` variabele om invoer te ontvangen van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="555dc-124">In this example, the script block uses the `$input` variable to receive input from the **InputObject** parameter.</span></span> <span data-ttu-id="555dc-125">Dit kan ook worden gedaan door pijpleiding objecten naar `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="555dc-125">This can also be done by piping objects to `Start-ThreadJob`.</span></span>

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### <span data-ttu-id="555dc-126">Voor beeld 4: taak uitvoer naar bovenliggende host streamen</span><span class="sxs-lookup"><span data-stu-id="555dc-126">Example 4 - Stream job output to parent host</span></span>

<span data-ttu-id="555dc-127">Met de para meter **StreamingHost** kunt u een taak vertelt om alle host uitvoer naar een specifieke host te sturen.</span><span class="sxs-lookup"><span data-stu-id="555dc-127">Using the **StreamingHost** parameter you can tell a job to direct all host output to a specific host.</span></span> <span data-ttu-id="555dc-128">Zonder deze para meter wordt de uitvoer naar de gegevensstroom verzameling taak verplaatst en wordt deze niet weer gegeven in een host-console totdat u de uitvoer van de taak ontvangt.</span><span class="sxs-lookup"><span data-stu-id="555dc-128">Without this parameter the output goes to the job data stream collection and doesn't appear in a host console until you receive the output from the job.</span></span>

<span data-ttu-id="555dc-129">Voor dit voor beeld wordt de huidige host door gegeven aan `Start-ThreadJob` het gebruik van de `$Host` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="555dc-129">For this example, the current host is passed to `Start-ThreadJob` using the `$Host` automatic variable.</span></span>

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; …

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

<span data-ttu-id="555dc-130">U ziet dat de prompt van `Read-Host` wordt weer gegeven en u kunt invoer typen.</span><span class="sxs-lookup"><span data-stu-id="555dc-130">Notice that the prompt from `Read-Host` is displayed and you are able to type input.</span></span> <span data-ttu-id="555dc-131">Vervolgens wordt het bericht van `Write-Warning` weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="555dc-131">Then, the message from `Write-Warning` is displayed.</span></span> <span data-ttu-id="555dc-132">De `Receive-Job` cmdlet retourneert alle uitvoer van de taak.</span><span class="sxs-lookup"><span data-stu-id="555dc-132">The `Receive-Job` cmdlet returns all the output from the job.</span></span>

## <span data-ttu-id="555dc-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="555dc-133">PARAMETERS</span></span>

### <span data-ttu-id="555dc-134">-Argument List</span><span class="sxs-lookup"><span data-stu-id="555dc-134">-ArgumentList</span></span>

<span data-ttu-id="555dc-135">Hiermee geeft u een matrix met argumenten, of parameter waarden, op voor het script dat is opgegeven door de para meters **filepath** of **script Block** .</span><span class="sxs-lookup"><span data-stu-id="555dc-135">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** or **ScriptBlock** parameters.</span></span>

<span data-ttu-id="555dc-136">**Argument List** moet de laatste para meter zijn op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="555dc-136">**ArgumentList** must be the last parameter on the command line.</span></span> <span data-ttu-id="555dc-137">Alle waarden die de parameter naam volgen, worden geïnterpreteerd als waarden in de argumenten lijst.</span><span class="sxs-lookup"><span data-stu-id="555dc-137">All the values that follow the parameter name are interpreted values in the argument list.</span></span>

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

### <span data-ttu-id="555dc-138">-FilePath</span><span class="sxs-lookup"><span data-stu-id="555dc-138">-FilePath</span></span>

<span data-ttu-id="555dc-139">Hiermee geeft u een script bestand moet worden uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="555dc-139">Specifies a script file to run as a background job.</span></span> <span data-ttu-id="555dc-140">Voer het pad en de bestands naam van het script in.</span><span class="sxs-lookup"><span data-stu-id="555dc-140">Enter the path and filename of the script.</span></span> <span data-ttu-id="555dc-141">Het script moet zich op de lokale computer of in een map bevindt waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="555dc-141">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="555dc-142">Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd en wordt het script blok als achtergrond taak uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="555dc-142">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="555dc-143">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="555dc-143">-InitializationScript</span></span>

<span data-ttu-id="555dc-144">Geeft opdrachten die worden uitgevoerd voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="555dc-144">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="555dc-145">Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="555dc-145">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="555dc-146">Gebruik deze para meter om de sessie voor te bereiden waarin de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="555dc-146">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="555dc-147">U kunt dit bijvoorbeeld gebruiken om functies en modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="555dc-147">For example, you can use it to add functions and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="555dc-148">-Input object</span><span class="sxs-lookup"><span data-stu-id="555dc-148">-InputObject</span></span>

<span data-ttu-id="555dc-149">Hiermee geeft u de objecten die worden gebruikt als invoer voor het-script blok.</span><span class="sxs-lookup"><span data-stu-id="555dc-149">Specifies the objects used as input to the script block.</span></span> <span data-ttu-id="555dc-150">Het biedt ook ondersteuning voor pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="555dc-150">It also allows for pipeline input.</span></span> <span data-ttu-id="555dc-151">Gebruik de `$input` Automatische variabele in het script blok om toegang te krijgen tot de invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="555dc-151">Use the `$input` automatic variable in the script block to access the input objects.</span></span>

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

### <span data-ttu-id="555dc-152">-Name</span><span class="sxs-lookup"><span data-stu-id="555dc-152">-Name</span></span>

<span data-ttu-id="555dc-153">Hiermee geeft u een beschrijvende naam op voor de nieuwe taak.</span><span class="sxs-lookup"><span data-stu-id="555dc-153">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="555dc-154">U kunt de naam gebruiken om de taak te identificeren in andere taak-cmdlets, zoals de- `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="555dc-154">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="555dc-155">De standaard beschrijvende naam is ' job # ', waarbij ' # ' een rang nummer is dat voor elke taak wordt verhoogd.</span><span class="sxs-lookup"><span data-stu-id="555dc-155">The default friendly name is "Job#", where "#" is an ordinal number that is incremented for each job.</span></span>

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

### <span data-ttu-id="555dc-156">-Script Block</span><span class="sxs-lookup"><span data-stu-id="555dc-156">-ScriptBlock</span></span>

<span data-ttu-id="555dc-157">Hiermee geeft u de opdrachten op die in de achtergrond taak moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="555dc-157">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="555dc-158">Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="555dc-158">Enclose the commands in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="555dc-159">Gebruik de `$Input` Automatische variabele om toegang te krijgen tot de waarde van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="555dc-159">Use the `$Input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="555dc-160">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="555dc-160">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="555dc-161">-StreamingHost</span><span class="sxs-lookup"><span data-stu-id="555dc-161">-StreamingHost</span></span>

<span data-ttu-id="555dc-162">Deze para meter biedt een veilige manier om `Write-Host` de uitvoer van een thread direct naar het door gegeven **PSHost** -object te laten gaan.</span><span class="sxs-lookup"><span data-stu-id="555dc-162">This parameter provides a thread safe way to allow `Write-Host` output to go directly to the passed in **PSHost** object.</span></span> <span data-ttu-id="555dc-163">Zonder IT `Write-Host` gaat uitvoer naar de gegevensstroom verzameling taak gegevens en pas weer in een host-console nadat de uitvoering van de taken is voltooid.</span><span class="sxs-lookup"><span data-stu-id="555dc-163">Without it, `Write-Host` output goes to the job information data stream collection and doesn't appear in a host console until after the jobs finish running.</span></span>

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="555dc-164">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="555dc-164">-ThrottleLimit</span></span>

<span data-ttu-id="555dc-165">Deze para meter beperkt het aantal taken dat tegelijk wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="555dc-165">This parameter limits the number of jobs running at one time.</span></span> <span data-ttu-id="555dc-166">Wanneer taken worden gestart, worden deze in de wachtrij geplaatst en gewacht totdat een thread beschikbaar is in de thread groep om de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="555dc-166">As jobs are started, they are queued and wait until a thread is available in the thread pool to run the job.</span></span> <span data-ttu-id="555dc-167">De standaard limiet is 5 threads.</span><span class="sxs-lookup"><span data-stu-id="555dc-167">The default limit is 5 threads.</span></span>

<span data-ttu-id="555dc-168">De grootte van de thread groep is globaal voor de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="555dc-168">The thread pool size is global to the PowerShell session.</span></span> <span data-ttu-id="555dc-169">Als u een **ThrottleLimit** in één aanroep opgeeft, wordt de limiet voor de volgende aanroepen in dezelfde sessie ingesteld.</span><span class="sxs-lookup"><span data-stu-id="555dc-169">Specifying a **ThrottleLimit** in one call sets the limit for subsequent calls in the same session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="555dc-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="555dc-170">CommonParameters</span></span>

<span data-ttu-id="555dc-171">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="555dc-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="555dc-172">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="555dc-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="555dc-173">INVOER</span><span class="sxs-lookup"><span data-stu-id="555dc-173">INPUTS</span></span>

### <span data-ttu-id="555dc-174">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="555dc-174">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="555dc-175">UITVOER</span><span class="sxs-lookup"><span data-stu-id="555dc-175">OUTPUTS</span></span>

### <span data-ttu-id="555dc-176">ThreadJob.ThreadJob</span><span class="sxs-lookup"><span data-stu-id="555dc-176">ThreadJob.ThreadJob</span></span>

## <span data-ttu-id="555dc-177">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="555dc-177">NOTES</span></span>

## <span data-ttu-id="555dc-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="555dc-178">RELATED LINKS</span></span>

[<span data-ttu-id="555dc-179">Begin taak</span><span class="sxs-lookup"><span data-stu-id="555dc-179">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="555dc-180">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="555dc-180">Stop-Job</span></span>](../Microsoft.PowerShell.Core/Stop-Job.md)

[<span data-ttu-id="555dc-181">Receive-job</span><span class="sxs-lookup"><span data-stu-id="555dc-181">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)
