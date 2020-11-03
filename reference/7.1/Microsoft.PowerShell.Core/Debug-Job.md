---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: 8ff583fbf0ebf453a5194deecbc1eb42a51242d4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251378"
---
# <span data-ttu-id="ac131-103">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="ac131-103">Debug-Job</span></span>

## <span data-ttu-id="ac131-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ac131-104">SYNOPSIS</span></span>
<span data-ttu-id="ac131-105">De uitvoering van een actieve achtergrond, externe of Power shell-werk stroom taak wordt ongebruikt.</span><span class="sxs-lookup"><span data-stu-id="ac131-105">Debugs a running background, remote, or PowerShell Workflow job.</span></span>

## <span data-ttu-id="ac131-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ac131-106">SYNTAX</span></span>

### <span data-ttu-id="ac131-107">JobParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="ac131-107">JobParameterSet (Default)</span></span>

```
Debug-Job [-Job] <Job> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ac131-108">JobNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="ac131-108">JobNameParameterSet</span></span>

```
Debug-Job [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ac131-109">JobIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="ac131-109">JobIdParameterSet</span></span>

```
Debug-Job [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ac131-110">JobInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="ac131-110">JobInstanceIdParameterSet</span></span>

```
Debug-Job [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ac131-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ac131-111">DESCRIPTION</span></span>
<span data-ttu-id="ac131-112">Met de cmdlet **debug-job** kunt u fouten opsporen in scripts die in taken worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac131-112">The **Debug-Job** cmdlet lets you debug scripts that are running within jobs.</span></span>
<span data-ttu-id="ac131-113">De cmdlet is ontworpen voor het opsporen van fouten in Power shell-werk stroom taken, achtergrond taken en taken die worden uitgevoerd in externe sessies.</span><span class="sxs-lookup"><span data-stu-id="ac131-113">The cmdlet is designed to debug PowerShell Workflow jobs, background jobs, and jobs running in remote sessions.</span></span>
<span data-ttu-id="ac131-114">**Debug: de taak** accepteert een actief taak object, naam, id of exemplaar-id als invoer, en start een foutopsporingssessie op het script dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac131-114">**Debug-Job** accepts a running job object, name, ID, or instance ID as input, and starts a debugging session on the script it is running.</span></span>
<span data-ttu-id="ac131-115">De opdracht debugger **Afsluiten** stopt de taak en voert script uit.</span><span class="sxs-lookup"><span data-stu-id="ac131-115">The debugger **quit** command stops the job and running script.</span></span>
<span data-ttu-id="ac131-116">Vanaf Windows Power shell 5,0 wordt met de opdracht **Exit** het fout opsporingsprogramma losgekoppeld en kan de taak worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac131-116">Starting in Windows PowerShell 5.0, the **exit** command detaches the debugger, and allows the job to continue to run.</span></span>

## <span data-ttu-id="ac131-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ac131-117">EXAMPLES</span></span>

### <span data-ttu-id="ac131-118">Voor beeld 1: fouten opsporen in een taak op taak-ID</span><span class="sxs-lookup"><span data-stu-id="ac131-118">Example 1: Debug a job by job ID</span></span>

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

<span data-ttu-id="ac131-119">Met deze opdracht wordt het einde van een taak met de ID 3 gekraakt.</span><span class="sxs-lookup"><span data-stu-id="ac131-119">This command breaks into a running job with an ID of 3.</span></span>

## <span data-ttu-id="ac131-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ac131-120">PARAMETERS</span></span>

### <span data-ttu-id="ac131-121">-Id</span><span class="sxs-lookup"><span data-stu-id="ac131-121">-Id</span></span>
<span data-ttu-id="ac131-122">Hiermee geeft u het ID-nummer van een actieve taak op.</span><span class="sxs-lookup"><span data-stu-id="ac131-122">Specifies the ID number of a running job.</span></span>
<span data-ttu-id="ac131-123">Als u het ID-nummer van een taak wilt ophalen, voert u de Get-Job-cmdlet uit.</span><span class="sxs-lookup"><span data-stu-id="ac131-123">To get the ID number of a job, run the Get-Job cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ac131-124">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="ac131-124">-InstanceId</span></span>
<span data-ttu-id="ac131-125">Hiermee geeft u de exemplaar-ID-GUID van een actieve taak op.</span><span class="sxs-lookup"><span data-stu-id="ac131-125">Specifies the instance ID GUID of a running job.</span></span>
<span data-ttu-id="ac131-126">Als u de *InstanceId* van een taak wilt ophalen, voert u de cmdlet **Get-job** uit, pijpleidingt u de resultaten in een **indeling-\*-** cmdlet, zoals weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ac131-126">To get the *InstanceId* of a job, run the **Get-Job** cmdlet, piping the results into a **Format-** \* cmdlet, as shown in the following example:</span></span>

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ac131-127">-Taak</span><span class="sxs-lookup"><span data-stu-id="ac131-127">-Job</span></span>
<span data-ttu-id="ac131-128">Hiermee wordt een actief taak object opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ac131-128">Specifies a running job object.</span></span>
<span data-ttu-id="ac131-129">De eenvoudigste manier om deze para meter te gebruiken is het opslaan van de resultaten van een **Get-job-** opdracht die de actieve taak retourneert die u wilt opsporen in een variabele, en vervolgens de variabele opgeven als de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="ac131-129">The simplest way to use this parameter is to save the results of a **Get-Job** command that returns the running job that you want to debug in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ac131-130">-Name</span><span class="sxs-lookup"><span data-stu-id="ac131-130">-Name</span></span>
<span data-ttu-id="ac131-131">Hiermee geeft u een taak op met de beschrijvende naam van de taak.</span><span class="sxs-lookup"><span data-stu-id="ac131-131">Specifies a job by the friendly name of the job.</span></span>
<span data-ttu-id="ac131-132">Wanneer u een taak start, kunt u een taak naam opgeven door de para meter *JobName* toe te voegen in cmdlets, zoals Invoke-Command en start taak.</span><span class="sxs-lookup"><span data-stu-id="ac131-132">When you start a job, you can specify a job name by adding the *JobName* parameter, in cmdlets such as Invoke-Command and Start-Job.</span></span>

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ac131-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ac131-133">-Confirm</span></span>
<span data-ttu-id="ac131-134">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ac131-134">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ac131-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ac131-135">-WhatIf</span></span>
<span data-ttu-id="ac131-136">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ac131-136">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ac131-137">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac131-137">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ac131-138">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="ac131-138">-BreakAll</span></span>

<span data-ttu-id="ac131-139">{{Opvulling BreakAll beschrijving}}</span><span class="sxs-lookup"><span data-stu-id="ac131-139">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="ac131-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ac131-140">CommonParameters</span></span>
<span data-ttu-id="ac131-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ac131-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ac131-142">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ac131-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ac131-143">INVOER</span><span class="sxs-lookup"><span data-stu-id="ac131-143">INPUTS</span></span>

### <span data-ttu-id="ac131-144">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="ac131-144">System.Management.Automation.RemotingJob</span></span>

## <span data-ttu-id="ac131-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ac131-145">OUTPUTS</span></span>

## <span data-ttu-id="ac131-146">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ac131-146">NOTES</span></span>

## <span data-ttu-id="ac131-147">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ac131-147">RELATED LINKS</span></span>

[<span data-ttu-id="ac131-148">Get-job</span><span class="sxs-lookup"><span data-stu-id="ac131-148">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="ac131-149">Receive-job</span><span class="sxs-lookup"><span data-stu-id="ac131-149">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="ac131-150">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="ac131-150">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="ac131-151">Begin taak</span><span class="sxs-lookup"><span data-stu-id="ac131-151">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="ac131-152">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="ac131-152">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="ac131-153">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="ac131-153">Wait-Job</span></span>](Wait-Job.md)

