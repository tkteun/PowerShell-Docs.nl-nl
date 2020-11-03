---
external help file: ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 01/28/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: 9ac0570a5e26de47438a48817785836348de19cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250104"
---
# <span data-ttu-id="1bb14-102">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="1bb14-102">Start-ThreadJob</span></span>

## <span data-ttu-id="1bb14-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1bb14-103">SYNOPSIS</span></span>
<span data-ttu-id="1bb14-104">Maakt achtergrond taken die vergelijkbaar zijn met de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1bb14-104">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>

## <span data-ttu-id="1bb14-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1bb14-105">SYNTAX</span></span>

### <span data-ttu-id="1bb14-106">Script Block</span><span class="sxs-lookup"><span data-stu-id="1bb14-106">ScriptBlock</span></span>

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="1bb14-107">Bestandspad</span><span class="sxs-lookup"><span data-stu-id="1bb14-107">FilePath</span></span>

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="1bb14-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1bb14-108">DESCRIPTION</span></span>

<span data-ttu-id="1bb14-109">`Start-ThreadJob` maakt achtergrond taken die vergelijkbaar zijn met de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1bb14-109">`Start-ThreadJob` creates background jobs similar to the `Start-Job` cmdlet.</span></span> <span data-ttu-id="1bb14-110">Het belangrijkste verschil is dat de taken die worden gemaakt in afzonderlijke threads binnen het lokale proces worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bb14-110">The main difference is that the jobs which are created run in separate threads within the local process.</span></span> <span data-ttu-id="1bb14-111">De taken gebruiken standaard de huidige werkmap van de aanroeper die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="1bb14-111">By default, the jobs use the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="1bb14-112">De cmdlet biedt ook ondersteuning voor de para meter **ThrottleLimit** om het aantal taken dat tegelijk wordt uitgevoerd, te beperken.</span><span class="sxs-lookup"><span data-stu-id="1bb14-112">The cmdlet also supports a **ThrottleLimit** parameter to limit the number of jobs running at one time.</span></span> <span data-ttu-id="1bb14-113">Naarmate er meer taken worden gestart, worden deze in de wachtrij geplaatst en gewacht totdat het huidige aantal taken onder de vertragings limiet valt.</span><span class="sxs-lookup"><span data-stu-id="1bb14-113">As more jobs are started, they are queued and wait until the current number of jobs drops below the throttle limit.</span></span>

## <span data-ttu-id="1bb14-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1bb14-114">EXAMPLES</span></span>

### <span data-ttu-id="1bb14-115">Voor beeld 1: Maak achtergrond taken met een thread limiet van 2</span><span class="sxs-lookup"><span data-stu-id="1bb14-115">Example 1 - Create background jobs with a thread limit of 2</span></span>

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

### <span data-ttu-id="1bb14-116">Voor beeld 2: de prestaties van Start-Job en Start-ThreadJob vergelijken</span><span class="sxs-lookup"><span data-stu-id="1bb14-116">Example 2 - Compare the performance of Start-Job and Start-ThreadJob</span></span>

<span data-ttu-id="1bb14-117">In dit voor beeld ziet u het verschil tussen `Start-Job` en `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="1bb14-117">This example shows the difference between `Start-Job` and `Start-ThreadJob`.</span></span> <span data-ttu-id="1bb14-118">De taken voeren de `Start-Sleep` cmdlet uit voor 1 seconde.</span><span class="sxs-lookup"><span data-stu-id="1bb14-118">The jobs run the `Start-Sleep` cmdlet for 1 second.</span></span> <span data-ttu-id="1bb14-119">Omdat de taken parallel worden uitgevoerd, is de totale uitvoerings tijd ongeveer 1 seconde, plus de tijd die nodig is om de taken te maken.</span><span class="sxs-lookup"><span data-stu-id="1bb14-119">Since the jobs run in parallel, the total execution time is about 1 second, plus any time required to create the jobs.</span></span>

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

<span data-ttu-id="1bb14-120">Nadat 1 seconde voor uitvoerings tijd is afgetrokken, ziet u dat `Start-Job` ongeveer 4,8 seconden duren om vijf taken te maken.</span><span class="sxs-lookup"><span data-stu-id="1bb14-120">After subtracting 1 second for execution time, you can see that `Start-Job` takes about 4.8 seconds to create five jobs.</span></span> <span data-ttu-id="1bb14-121">`Start-ThreadJob` is 8 keer sneller, met ongeveer 0,6 seconden om vijf taken te maken.</span><span class="sxs-lookup"><span data-stu-id="1bb14-121">`Start-ThreadJob` is 8 times faster, taking about 0.6 seconds to create five jobs.</span></span> <span data-ttu-id="1bb14-122">De resultaten kunnen variëren in uw omgeving, maar de relatieve verbetering moet hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="1bb14-122">The results may vary in your environment but the relative improvement should be the same.</span></span>

### <span data-ttu-id="1bb14-123">Voor beeld 3: taken maken met input object</span><span class="sxs-lookup"><span data-stu-id="1bb14-123">Example 3 - Create jobs using InputObject</span></span>

<span data-ttu-id="1bb14-124">In dit voor beeld gebruikt het script blok de `$input` variabele om invoer te ontvangen van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="1bb14-124">In this example, the script block uses the `$input` variable to receive input from the **InputObject** parameter.</span></span> <span data-ttu-id="1bb14-125">Dit kan ook worden gedaan door pijpleiding objecten naar `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="1bb14-125">This can also be done by piping objects to `Start-ThreadJob`.</span></span>

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

## <span data-ttu-id="1bb14-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1bb14-126">PARAMETERS</span></span>

### <span data-ttu-id="1bb14-127">-Argument List</span><span class="sxs-lookup"><span data-stu-id="1bb14-127">-ArgumentList</span></span>

<span data-ttu-id="1bb14-128">Hiermee geeft u een matrix met argumenten, of parameter waarden, op voor het script dat is opgegeven door de para meters **filepath** of **script Block** .</span><span class="sxs-lookup"><span data-stu-id="1bb14-128">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** or **ScriptBlock** parameters.</span></span>

<span data-ttu-id="1bb14-129">**Argument List** moet de laatste para meter zijn op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="1bb14-129">**ArgumentList** must be the last parameter on the command line.</span></span> <span data-ttu-id="1bb14-130">Alle waarden die de parameter naam volgen, worden geïnterpreteerd als waarden in de argumenten lijst.</span><span class="sxs-lookup"><span data-stu-id="1bb14-130">All the values that follow the parameter name are interpreted values in the argument list.</span></span>

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

### <span data-ttu-id="1bb14-131">-FilePath</span><span class="sxs-lookup"><span data-stu-id="1bb14-131">-FilePath</span></span>

<span data-ttu-id="1bb14-132">Hiermee geeft u een script bestand moet worden uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="1bb14-132">Specifies a script file to run as a background job.</span></span> <span data-ttu-id="1bb14-133">Voer het pad en de bestands naam van het script in.</span><span class="sxs-lookup"><span data-stu-id="1bb14-133">Enter the path and filename of the script.</span></span> <span data-ttu-id="1bb14-134">Het script moet zich op de lokale computer of in een map bevindt waartoe de lokale computer toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="1bb14-134">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="1bb14-135">Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd en wordt het script blok als achtergrond taak uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bb14-135">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="1bb14-136">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="1bb14-136">-InitializationScript</span></span>

<span data-ttu-id="1bb14-137">Geeft opdrachten die worden uitgevoerd voordat de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="1bb14-137">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="1bb14-138">Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="1bb14-138">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="1bb14-139">Gebruik deze para meter om de sessie voor te bereiden waarin de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bb14-139">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="1bb14-140">U kunt dit bijvoorbeeld gebruiken om functies en modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="1bb14-140">For example, you can use it to add functions and modules to the session.</span></span>

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

### <span data-ttu-id="1bb14-141">-Input object</span><span class="sxs-lookup"><span data-stu-id="1bb14-141">-InputObject</span></span>

<span data-ttu-id="1bb14-142">Hiermee geeft u de objecten die worden gebruikt als invoer voor het-script blok.</span><span class="sxs-lookup"><span data-stu-id="1bb14-142">Specifies the objects used as input to the script block.</span></span> <span data-ttu-id="1bb14-143">Het biedt ook ondersteuning voor pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="1bb14-143">It also allows for pipeline input.</span></span> <span data-ttu-id="1bb14-144">Gebruik de `$input` Automatische variabele in het script blok om toegang te krijgen tot de invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="1bb14-144">Use the `$input` automatic variable in the script block to access the input objects.</span></span>

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

### <span data-ttu-id="1bb14-145">-Name</span><span class="sxs-lookup"><span data-stu-id="1bb14-145">-Name</span></span>

<span data-ttu-id="1bb14-146">Hiermee geeft u een beschrijvende naam op voor de nieuwe taak.</span><span class="sxs-lookup"><span data-stu-id="1bb14-146">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="1bb14-147">U kunt de naam gebruiken om de taak te identificeren in andere taak-cmdlets, zoals de- `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1bb14-147">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="1bb14-148">De standaard beschrijvende naam is ' job # ', waarbij ' # ' een rang nummer is dat voor elke taak wordt verhoogd.</span><span class="sxs-lookup"><span data-stu-id="1bb14-148">The default friendly name is "Job#", where "#" is an ordinal number that is incremented for each job.</span></span>

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

### <span data-ttu-id="1bb14-149">-Script Block</span><span class="sxs-lookup"><span data-stu-id="1bb14-149">-ScriptBlock</span></span>

<span data-ttu-id="1bb14-150">Hiermee geeft u de opdrachten op die in de achtergrond taak moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bb14-150">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="1bb14-151">Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="1bb14-151">Enclose the commands in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="1bb14-152">Gebruik de `$Input` Automatische variabele om toegang te krijgen tot de waarde van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="1bb14-152">Use the `$Input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="1bb14-153">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="1bb14-153">This parameter is required.</span></span>

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

### <span data-ttu-id="1bb14-154">-StreamingHost</span><span class="sxs-lookup"><span data-stu-id="1bb14-154">-StreamingHost</span></span>

<span data-ttu-id="1bb14-155">Deze para meter biedt een veilige manier om `Write-Host` de uitvoer van een thread direct naar het door gegeven **PSHost** -object te laten gaan.</span><span class="sxs-lookup"><span data-stu-id="1bb14-155">This parameter provides a thread safe way to allow `Write-Host` output to go directly to the passed in **PSHost** object.</span></span> <span data-ttu-id="1bb14-156">Zonder IT `Write-Host` gaat uitvoer naar de gegevensstroom verzameling taak gegevens en pas weer in een host-console nadat de uitvoering van de taken is voltooid.</span><span class="sxs-lookup"><span data-stu-id="1bb14-156">Without it, `Write-Host` output goes to the job information data stream collection and doesn't appear in a host console until after the jobs finish running.</span></span>

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

### <span data-ttu-id="1bb14-157">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="1bb14-157">-ThrottleLimit</span></span>

<span data-ttu-id="1bb14-158">Deze para meter beperkt het aantal taken dat tegelijk wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bb14-158">This parameter limits the number of jobs running at one time.</span></span> <span data-ttu-id="1bb14-159">Wanneer taken worden gestart, worden deze in de wachtrij geplaatst en gewacht totdat een thread beschikbaar is in de thread groep om de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1bb14-159">As jobs are started, they are queued and wait until a thread is available in the thread pool to run the job.</span></span> <span data-ttu-id="1bb14-160">De standaard limiet is 5 threads.</span><span class="sxs-lookup"><span data-stu-id="1bb14-160">The default limit is 5 threads.</span></span>

<span data-ttu-id="1bb14-161">De grootte van de thread groep is globaal voor de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="1bb14-161">The thread pool size is global to the PowerShell session.</span></span> <span data-ttu-id="1bb14-162">Als u een **ThrottleLimit** in één aanroep opgeeft, wordt de limiet voor de volgende aanroepen in dezelfde sessie ingesteld.</span><span class="sxs-lookup"><span data-stu-id="1bb14-162">Specifying a **ThrottleLimit** in one call sets the limit for subsequent calls in the same session.</span></span>

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

### <span data-ttu-id="1bb14-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1bb14-163">CommonParameters</span></span>

<span data-ttu-id="1bb14-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1bb14-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1bb14-165">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1bb14-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1bb14-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="1bb14-166">INPUTS</span></span>

### <span data-ttu-id="1bb14-167">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="1bb14-167">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="1bb14-168">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1bb14-168">OUTPUTS</span></span>

### <span data-ttu-id="1bb14-169">ThreadJob.ThreadJob</span><span class="sxs-lookup"><span data-stu-id="1bb14-169">ThreadJob.ThreadJob</span></span>

## <span data-ttu-id="1bb14-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1bb14-170">NOTES</span></span>

## <span data-ttu-id="1bb14-171">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1bb14-171">RELATED LINKS</span></span>

[<span data-ttu-id="1bb14-172">Begin taak</span><span class="sxs-lookup"><span data-stu-id="1bb14-172">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="1bb14-173">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="1bb14-173">Stop-Job</span></span>](../Microsoft.PowerShell.Core/Stop-Job.md)

[<span data-ttu-id="1bb14-174">Receive-job</span><span class="sxs-lookup"><span data-stu-id="1bb14-174">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)

