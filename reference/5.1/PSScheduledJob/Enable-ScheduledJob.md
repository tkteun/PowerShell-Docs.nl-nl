---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250309"
---
# <span data-ttu-id="23f70-103">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="23f70-103">Enable-ScheduledJob</span></span>

## <span data-ttu-id="23f70-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="23f70-104">SYNOPSIS</span></span>
<span data-ttu-id="23f70-105">Hiermee wordt een geplande taak ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="23f70-105">Enables a scheduled job.</span></span>

## <span data-ttu-id="23f70-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="23f70-106">SYNTAX</span></span>

### <span data-ttu-id="23f70-107">Definitie (standaard)</span><span class="sxs-lookup"><span data-stu-id="23f70-107">Definition (Default)</span></span>

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="23f70-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="23f70-108">DefinitionId</span></span>

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="23f70-109">Definitie</span><span class="sxs-lookup"><span data-stu-id="23f70-109">DefinitionName</span></span>

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="23f70-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="23f70-110">DESCRIPTION</span></span>
<span data-ttu-id="23f70-111">Met de cmdlet **Enable-ScheduledJob** worden geplande taken die zijn uitgeschakeld, ingeschakeld, zoals die zijn uitgeschakeld met behulp van de cmdlet Disable-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="23f70-111">The **Enable-ScheduledJob** cmdlet re-enables scheduled jobs that are disabled, such as those that are disabled by using the Disable-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="23f70-112">Ingeschakelde taken worden automatisch uitgevoerd wanneer deze wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="23f70-112">Enabled jobs run automatically when triggered.</span></span>

<span data-ttu-id="23f70-113">Als u een geplande taak wilt inschakelen, stelt de cmdlet **Enable-ScheduledJob** de eigenschap Enabled van de geplande taak in op $True.</span><span class="sxs-lookup"><span data-stu-id="23f70-113">To enable a scheduled job, the **Enable-ScheduledJob** cmdlet sets the Enabled property of the scheduled job to $True.</span></span>

<span data-ttu-id="23f70-114">**Ingeschakeld: ScheduledJob** is een van een verzameling cmdlets voor taak planning in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="23f70-114">**Enabled-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="23f70-115">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="23f70-115">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="23f70-116">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="23f70-116">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="23f70-117">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23f70-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="23f70-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="23f70-118">EXAMPLES</span></span>

### <span data-ttu-id="23f70-119">Voor beeld 1: een geplande taak inschakelen</span><span class="sxs-lookup"><span data-stu-id="23f70-119">Example 1: Enable a scheduled job</span></span>

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

<span data-ttu-id="23f70-120">Met deze opdracht wordt de geplande taak met ID 2 ingeschakeld op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="23f70-120">This command enables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="23f70-121">In de uitvoer ziet u het effect van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="23f70-121">The output shows the effect of the command.</span></span>

### <span data-ttu-id="23f70-122">Voor beeld 2: alle geplande taken inschakelen</span><span class="sxs-lookup"><span data-stu-id="23f70-122">Example 2: Enable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

<span data-ttu-id="23f70-123">Met deze opdracht worden alle geplande taken op de lokale computer ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="23f70-123">This command enables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="23f70-124">De cmdlet Get-ScheduledJob wordt gebruikt voor het ophalen van alle geplande taken en de cmdlet **Enable-ScheduledJob** om deze in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="23f70-124">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Enable-ScheduledJob** cmdlet to enable them.</span></span>

<span data-ttu-id="23f70-125">**Enable-ScheduledJob** genereert geen waarschuwingen of fouten als u een geplande taak inschakelt die al is ingeschakeld, zodat u alle geplande taken zonder voor waarden kunt inschakelen.</span><span class="sxs-lookup"><span data-stu-id="23f70-125">**Enable-ScheduledJob** does not generate warnings or errors if you enable a scheduled job that is already enabled, so you can enable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="23f70-126">Voor beeld 3: geselecteerde geplande taken inschakelen</span><span class="sxs-lookup"><span data-stu-id="23f70-126">Example 3: Enable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

<span data-ttu-id="23f70-127">Met deze opdracht worden geplande taken ingeschakeld waarvoor geen netwerk verbinding nodig is.</span><span class="sxs-lookup"><span data-stu-id="23f70-127">This command enables scheduled jobs that do not require a network connection.</span></span>

<span data-ttu-id="23f70-128">De opdracht gebruikt de cmdlet Get-ScheduledJob om alle geplande taken op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="23f70-128">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="23f70-129">Een pijplijn operator verzendt de geplande taken naar de cmdlet Get-ScheduledJobOption, waarmee de taak opties van elke geplande taak worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="23f70-129">A pipeline operator sends the scheduled jobs to the Get-ScheduledJobOption cmdlet, which gets the job options of each scheduled job.</span></span>
<span data-ttu-id="23f70-130">Elk taak opties object heeft een eigenschap taak definitie die de bijbehorende geplande taak bevat.</span><span class="sxs-lookup"><span data-stu-id="23f70-130">Each job options object has a JobDefinition property that contains the associated scheduled job.</span></span>
<span data-ttu-id="23f70-131">De eigenschap taak definitie wordt gebruikt om de opdracht te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="23f70-131">The JobDefinition property is used to complete the command.</span></span>

<span data-ttu-id="23f70-132">De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de taak opties naar de cmdlet Where-Object, waarmee optie objecten van geplande taken worden geselecteerd waarin de eigenschap **RunWithoutNetwork** de waarde True ($true) heeft.</span><span class="sxs-lookup"><span data-stu-id="23f70-132">The command uses a pipeline operator (|) to send the job options to the Where-Object cmdlet, which selects scheduled job option objects in which the **RunWithoutNetwork** property has a value of True ($true).</span></span>
<span data-ttu-id="23f70-133">Een andere pijplijn operator verzendt de geselecteerde geplande opdracht Opties objecten naar de ForEach-Object-cmdlet waarmee de opdracht **Enable-ScheduledJob** wordt uitgevoerd voor de geplande taak in de waarde van de eigenschap taak definitie van elk object voor taak opties.</span><span class="sxs-lookup"><span data-stu-id="23f70-133">Another pipeline operator sends the selected scheduled job options objects to the ForEach-Object cmdlet which runs an **Enable-ScheduledJob** command on the scheduled job in the value of the JobDefinition property of each job options object.</span></span>

### <span data-ttu-id="23f70-134">Voor beeld 4: geplande taken inschakelen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="23f70-134">Example 4: Enable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

<span data-ttu-id="23f70-135">Met deze opdracht kunt u geplande taken met ' test ' in hun namen op twee externe computers, Srv01 en Srv10.</span><span class="sxs-lookup"><span data-stu-id="23f70-135">This command enables scheduled jobs that have "test" in their names on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="23f70-136">De opdracht gebruikt de cmdlet Invoke-Command om een opdracht **Enable-ScheduledJob** uit te voeren op de computers Srv01 en Srv10.</span><span class="sxs-lookup"><span data-stu-id="23f70-136">The command uses the Invoke-Command cmdlet to run an **Enable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="23f70-137">De opdracht maakt gebruik van de para meter *name* van **Enable-ScheduledJob** om de geplande inventaris op elke computer in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="23f70-137">The command uses the *Name* parameter of **Enable-ScheduledJob** to enable the Inventory scheduled job on each computer.</span></span>

## <span data-ttu-id="23f70-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23f70-138">PARAMETERS</span></span>

### <span data-ttu-id="23f70-139">-Id</span><span class="sxs-lookup"><span data-stu-id="23f70-139">-Id</span></span>
<span data-ttu-id="23f70-140">Hiermee wordt de geplande taak met het opgegeven id-nummer (ID) ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="23f70-140">Enables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="23f70-141">Voer de ID van een geplande taak in.</span><span class="sxs-lookup"><span data-stu-id="23f70-141">Enter the ID of a scheduled job.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23f70-142">-Input object</span><span class="sxs-lookup"><span data-stu-id="23f70-142">-InputObject</span></span>
<span data-ttu-id="23f70-143">Hiermee geeft u de geplande taak moet worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="23f70-143">Specifies the scheduled job to enable.</span></span>
<span data-ttu-id="23f70-144">Voer een variabele in die **ScheduledJobDefinition** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobDefinition** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="23f70-144">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="23f70-145">U kunt ook een **ScheduledJobDefinition** -object pipeen om **-ScheduledJob in te scha kelen**.</span><span class="sxs-lookup"><span data-stu-id="23f70-145">You can also pipe a **ScheduledJobDefinition** object to **Enable-ScheduledJob**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="23f70-146">-Name</span><span class="sxs-lookup"><span data-stu-id="23f70-146">-Name</span></span>
<span data-ttu-id="23f70-147">Hiermee worden de geplande taken met de opgegeven namen ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="23f70-147">Enables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="23f70-148">Voer de naam van een geplande taak in.</span><span class="sxs-lookup"><span data-stu-id="23f70-148">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="23f70-149">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="23f70-149">Wildcards are supported.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23f70-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="23f70-150">-PassThru</span></span>
<span data-ttu-id="23f70-151">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="23f70-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="23f70-152">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="23f70-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="23f70-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="23f70-153">-Confirm</span></span>
<span data-ttu-id="23f70-154">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="23f70-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="23f70-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="23f70-155">-WhatIf</span></span>
<span data-ttu-id="23f70-156">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="23f70-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="23f70-157">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23f70-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="23f70-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23f70-158">CommonParameters</span></span>
<span data-ttu-id="23f70-159">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23f70-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23f70-160">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23f70-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23f70-161">INVOER</span><span class="sxs-lookup"><span data-stu-id="23f70-161">INPUTS</span></span>

### <span data-ttu-id="23f70-162">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="23f70-162">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="23f70-163">U kunt een geplande taak pipeen om **-ScheduledJob in te scha kelen**.</span><span class="sxs-lookup"><span data-stu-id="23f70-163">You can pipe a scheduled job to **Enable-ScheduledJob**.</span></span>

## <span data-ttu-id="23f70-164">UITVOER</span><span class="sxs-lookup"><span data-stu-id="23f70-164">OUTPUTS</span></span>

### <span data-ttu-id="23f70-165">Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="23f70-165">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="23f70-166">Als u de para meter **PassThru** gebruikt, wordt de geplande taak die is ingeschakeld, door **Enable-ScheduledJob** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="23f70-166">If you use the **Passthru** parameter, **Enable-ScheduledJob** returns the scheduled job that was enabled.</span></span>
<span data-ttu-id="23f70-167">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="23f70-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="23f70-168">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="23f70-168">NOTES</span></span>

* <span data-ttu-id="23f70-169">**Enable-ScheduledJob** genereert geen waarschuwingen of fouten als u deze gebruikt om een geplande taak in te scha kelen die al is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="23f70-169">**Enable-ScheduledJob** does not generate warnings or errors if you use it to enable a scheduled job that is already enabled.</span></span>

## <span data-ttu-id="23f70-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="23f70-170">RELATED LINKS</span></span>

[<span data-ttu-id="23f70-171">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="23f70-171">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="23f70-172">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="23f70-172">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="23f70-173">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="23f70-173">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="23f70-174">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="23f70-174">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="23f70-175">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="23f70-175">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="23f70-176">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="23f70-176">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="23f70-177">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="23f70-177">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="23f70-178">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="23f70-178">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="23f70-179">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="23f70-179">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="23f70-180">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="23f70-180">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="23f70-181">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="23f70-181">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="23f70-182">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="23f70-182">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="23f70-183">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="23f70-183">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="23f70-184">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="23f70-184">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="23f70-185">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="23f70-185">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="23f70-186">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="23f70-186">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
