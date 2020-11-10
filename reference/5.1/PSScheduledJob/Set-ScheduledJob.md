---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387903"
---
# <span data-ttu-id="822f5-103">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="822f5-103">Set-ScheduledJob</span></span>

## <span data-ttu-id="822f5-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="822f5-104">SYNOPSIS</span></span>
<span data-ttu-id="822f5-105">Geplande taken worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="822f5-105">Changes scheduled jobs.</span></span>

## <span data-ttu-id="822f5-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="822f5-106">SYNTAX</span></span>

### <span data-ttu-id="822f5-107">Script Block (standaard)</span><span class="sxs-lookup"><span data-stu-id="822f5-107">ScriptBlock (Default)</span></span>

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="822f5-108">Bestandspad</span><span class="sxs-lookup"><span data-stu-id="822f5-108">FilePath</span></span>

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="822f5-109">Uitvoering</span><span class="sxs-lookup"><span data-stu-id="822f5-109">Execution</span></span>

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## <span data-ttu-id="822f5-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="822f5-110">DESCRIPTION</span></span>
<span data-ttu-id="822f5-111">Met de cmdlet **set-ScheduledJob** worden de eigenschappen van geplande taken gewijzigd, zoals de opdrachten die de taken uitvoeren of de referenties die nodig zijn om de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="822f5-111">The **Set-ScheduledJob** cmdlet changes the properties of scheduled jobs, such as the commands that the jobs run or the credentials required to run the job.</span></span>
<span data-ttu-id="822f5-112">U kunt dit ook gebruiken om de uitvoerings geschiedenis van de geplande taak te wissen.</span><span class="sxs-lookup"><span data-stu-id="822f5-112">You can also use it to clear the execution history of the scheduled job.</span></span>

<span data-ttu-id="822f5-113">Als u deze cmdlet wilt gebruiken, moet u beginnen met de cmdlet Get-ScheduledJob om de geplande taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="822f5-113">To use this cmdlet, begin by using the Get-ScheduledJob cmdlet to get the scheduled job.</span></span>
<span data-ttu-id="822f5-114">Pipet vervolgens de geplande taak om **ScheduledJob** in te stellen of de taak op te slaan in een variabele en de para meter *input object* te gebruiken om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="822f5-114">Then, pipe the scheduled job to **Set-ScheduledJob** or save the job in a variable and use the *InputObject* parameter to identify the job.</span></span>
<span data-ttu-id="822f5-115">Gebruik de resterende para meters van **set-ScheduledJob** om de taak eigenschappen te wijzigen of de uitvoerings geschiedenis te wissen.</span><span class="sxs-lookup"><span data-stu-id="822f5-115">Use the remaining parameters of **Set-ScheduledJob** to change the job properties or clear the execution history.</span></span>

<span data-ttu-id="822f5-116">Hoewel u **set-ScheduledJob** kunt gebruiken om de triggers en opties van een geplande taak te wijzigen, bieden de cmdlets Add-JobTrigger, set-JobTrigger en Set-ScheduledJobOption veel eenvoudiger manieren om deze taken uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="822f5-116">Although you can use **Set-ScheduledJob** to change the triggers and options of a scheduled job, the Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJobOption cmdlets provide much easier ways to accomplish those tasks.</span></span>
<span data-ttu-id="822f5-117">Als u een nieuwe geplande taak wilt maken, gebruikt u de cmdlet Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="822f5-117">To create a new scheduled job, use the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="822f5-118">De *trigger* parameter van **set-ScheduledJob** voegt een of meer taak triggers toe waarmee de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="822f5-118">The *Trigger* parameter of **Set-ScheduledJob** adds one or more job triggers that start the job.</span></span>
<span data-ttu-id="822f5-119">De *trigger* parameter is optioneel. u kunt triggers toevoegen wanneer u de geplande taak maakt, taak triggers later toevoegen, de para meter *RunNow* toevoegen om de taak onmiddellijk te starten. Gebruik de cmdlet Start-Job om de taak onmiddellijk te starten of sla de niet-geactiveerde geplande taak op als een sjabloon voor andere taken.</span><span class="sxs-lookup"><span data-stu-id="822f5-119">The *Trigger* parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the *RunNow* parameter to start the job immediately, use the Start-Job cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="822f5-120">**Set-ScheduledJob** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="822f5-120">**Set-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="822f5-121">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="822f5-121">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="822f5-122">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="822f5-122">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="822f5-123">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="822f5-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="822f5-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="822f5-124">EXAMPLES</span></span>

### <span data-ttu-id="822f5-125">Voor beeld 1: het script wijzigen dat door een taak wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="822f5-125">Example 1: Change the script that a job runs</span></span>

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

<span data-ttu-id="822f5-126">In dit voor beeld ziet u hoe u het script wijzigt dat in een geplande taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="822f5-126">This example shows how to change the script that is run in a scheduled job.</span></span>

<span data-ttu-id="822f5-127">De eerste opdracht maakt gebruik van de cmdlet Get-ScheduledJob om de geplande voorraad taak te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="822f5-127">The first command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job.</span></span>
<span data-ttu-id="822f5-128">In de uitvoer ziet u dat de taak het Get-Inventory.ps1 script uitvoert.</span><span class="sxs-lookup"><span data-stu-id="822f5-128">The output shows that the job runs the Get-Inventory.ps1 script.</span></span>

<span data-ttu-id="822f5-129">Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de script wijziging weer te geven.</span><span class="sxs-lookup"><span data-stu-id="822f5-129">This command is not required; it is included only to show the effect of the script change.</span></span>

### <span data-ttu-id="822f5-130">Voor beeld 2: de uitvoerings geschiedenis van een geplande taak verwijderen</span><span class="sxs-lookup"><span data-stu-id="822f5-130">Example 2: Delete the execution history of a scheduled job</span></span>

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="822f5-131">Met deze opdracht worden de huidige uitvoerings geschiedenis en opgeslagen taak resultaten verwijderd voor de geplande taak BackupArchive.</span><span class="sxs-lookup"><span data-stu-id="822f5-131">This command deletes the current execution history and saved job results for the BackupArchive scheduled job.</span></span>

<span data-ttu-id="822f5-132">De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taak BackupArchive te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="822f5-132">The command uses the Get-ScheduledJob cmdlet to get the BackupArchive scheduled job.</span></span>
<span data-ttu-id="822f5-133">Een pijplijn operator (|) verzendt de taak naar de cmdlet **set-ScheduledJob** om deze te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="822f5-133">A pipeline operator (|) sends the job to the **Set-ScheduledJob** cmdlet to change it.</span></span>
<span data-ttu-id="822f5-134">De cmdlet **set-ScheduledJob** gebruikt de para meter *ClearExecutionHistory* om de uitvoerings geschiedenis te verwijderen en de resultaten op te slaan.</span><span class="sxs-lookup"><span data-stu-id="822f5-134">The **Set-ScheduledJob** cmdlet uses the *ClearExecutionHistory* parameter to delete the execution history and saved results.</span></span>

<span data-ttu-id="822f5-135">Zie about_Scheduled_Jobs voor meer informatie over de uitvoerings geschiedenis en de opgeslagen taak resultaten van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="822f5-135">For more information about the execution history and saved job results of scheduled jobs, see about_Scheduled_Jobs.</span></span>

### <span data-ttu-id="822f5-136">Voor beeld 3: geplande taken wijzigen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="822f5-136">Example 3: Change scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

<span data-ttu-id="822f5-137">Met deze opdracht wordt het initialisatie script gewijzigd in alle geplande taken op de Server01-en Server02-computers.</span><span class="sxs-lookup"><span data-stu-id="822f5-137">This command changes the initialization script in all scheduled jobs on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="822f5-138">De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de Server01-en Server02-computers.</span><span class="sxs-lookup"><span data-stu-id="822f5-138">The command uses the Invoke-Command cmdlet to run a command on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="822f5-139">De externe opdracht begint met een Get-ScheduledJob opdracht waarmee alle geplande taken op de computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="822f5-139">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="822f5-140">De geplande taken worden gepiped naar de cmdlet **set-ScheduledJob** , waarmee het initialisatie script wordt gewijzigd in SetForRun.ps1.</span><span class="sxs-lookup"><span data-stu-id="822f5-140">The scheduled jobs are piped to the **Set-ScheduledJob** cmdlet, which changes the initialization script to SetForRun.ps1.</span></span>

## <span data-ttu-id="822f5-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="822f5-141">PARAMETERS</span></span>

### <span data-ttu-id="822f5-142">-Argument List</span><span class="sxs-lookup"><span data-stu-id="822f5-142">-ArgumentList</span></span>
<span data-ttu-id="822f5-143">Hiermee geeft u waarden op voor de para meters van het script dat is opgegeven met de para meter *filepath* of voor de opdracht die is opgegeven door de para meter *script Block* .</span><span class="sxs-lookup"><span data-stu-id="822f5-143">Specifies values for the parameters of the script that is specified by the *FilePath* parameter or for the command that is specified by the *ScriptBlock* parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-144">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="822f5-144">-Authentication</span></span>
<span data-ttu-id="822f5-145">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="822f5-145">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="822f5-146">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="822f5-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="822f5-147">Standaard</span><span class="sxs-lookup"><span data-stu-id="822f5-147">Default</span></span>
- <span data-ttu-id="822f5-148">Basic</span><span class="sxs-lookup"><span data-stu-id="822f5-148">Basic</span></span>
- <span data-ttu-id="822f5-149">CredSSP</span><span class="sxs-lookup"><span data-stu-id="822f5-149">Credssp</span></span>
- <span data-ttu-id="822f5-150">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="822f5-150">Digest</span></span>
- <span data-ttu-id="822f5-151">Kerberos</span><span class="sxs-lookup"><span data-stu-id="822f5-151">Kerberos</span></span>
- <span data-ttu-id="822f5-152">Negotiate</span><span class="sxs-lookup"><span data-stu-id="822f5-152">Negotiate</span></span>
- <span data-ttu-id="822f5-153">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="822f5-153">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="822f5-154">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="822f5-154">The default value is Default.</span></span> <span data-ttu-id="822f5-155">Zie [AuthenticationMechanism-inventarisatie](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) in de Power shell SDK voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="822f5-155">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) in the PowerShell SDK.</span></span>

<span data-ttu-id="822f5-156">Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="822f5-156">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="822f5-157">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="822f5-157">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="822f5-158">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="822f5-158">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-159">-ClearExecutionHistory</span><span class="sxs-lookup"><span data-stu-id="822f5-159">-ClearExecutionHistory</span></span>
<span data-ttu-id="822f5-160">Hiermee worden de huidige uitvoerings geschiedenis en de opgeslagen resultaten van de geplande taak verwijderd.</span><span class="sxs-lookup"><span data-stu-id="822f5-160">Deletes the current execution history and the saved results of the scheduled job.</span></span>

<span data-ttu-id="822f5-161">De geschiedenis van de taak uitvoering en taak resultaten worden opgeslagen met de geplande taak in de map $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs op de computer waarop de taak is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="822f5-161">The job execution history and job results are saved with the scheduled job in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the computer on which the job is created.</span></span>
<span data-ttu-id="822f5-162">Als u de uitvoerings geschiedenis wilt zien, gebruikt u de cmdlet Get-Job.</span><span class="sxs-lookup"><span data-stu-id="822f5-162">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="822f5-163">Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="822f5-163">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="822f5-164">Deze para meter heeft geen invloed op de gebeurtenissen die door Task Scheduler naar de gebeurtenis logboeken van Windows worden geschreven. de taak resultaten worden niet gestopt door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="822f5-164">This parameter does not affect the events that Task Scheduler writes to the Windows event logs and it does not stop Windows PowerShell from saving job results.</span></span>
<span data-ttu-id="822f5-165">Als u het aantal taak resultaten wilt beheren dat is opgeslagen, gebruikt u de para meter *MaxResultCount* .</span><span class="sxs-lookup"><span data-stu-id="822f5-165">To manage the number of job results that are saved, use the *MaxResultCount* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="822f5-166">-Credential</span></span>
<span data-ttu-id="822f5-167">Hiermee geeft u een gebruikers account op dat gemachtigd is om de geplande taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="822f5-167">Specifies a user account that has permission to run the scheduled job.</span></span>
<span data-ttu-id="822f5-168">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="822f5-168">The default is the current user.</span></span>

<span data-ttu-id="822f5-169">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals een van de Get-Credential-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="822f5-169">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the Get-Credential cmdlet.</span></span>
<span data-ttu-id="822f5-170">Als u alleen een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="822f5-170">If you enter only a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-171">-FilePath</span><span class="sxs-lookup"><span data-stu-id="822f5-171">-FilePath</span></span>
<span data-ttu-id="822f5-172">Hiermee geeft u een script op dat door de geplande taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="822f5-172">Specifies a script that the scheduled job runs.</span></span>
<span data-ttu-id="822f5-173">Geef het pad op naar een. ps1-bestand op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="822f5-173">Enter the path to a .ps1 file on the local computer.</span></span>
<span data-ttu-id="822f5-174">Als u standaard waarden voor de script parameters wilt opgeven, gebruikt u de para meter *argument List* .</span><span class="sxs-lookup"><span data-stu-id="822f5-174">To specify default values for the script parameters, use the *ArgumentList* parameter.</span></span>
<span data-ttu-id="822f5-175">Elke geplande taak moet een waarde van *script Block* of *filepath* hebben.</span><span class="sxs-lookup"><span data-stu-id="822f5-175">Every scheduled job must have either a *ScriptBlock* or *FilePath* value.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-176">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="822f5-176">-InitializationScript</span></span>
<span data-ttu-id="822f5-177">Hiermee geeft u het volledig gekwalificeerde pad naar een Windows Power shell-script (. ps1) op.</span><span class="sxs-lookup"><span data-stu-id="822f5-177">Specifies the fully qualified path to a Windows PowerShell script (.ps1).</span></span>
<span data-ttu-id="822f5-178">Het initialisatie script wordt uitgevoerd in de sessie die is gemaakt voor de achtergrond taak vóór de opdrachten die zijn opgegeven door de para meter *script Block* of het script dat is opgegeven door de para meter *filepath* .</span><span class="sxs-lookup"><span data-stu-id="822f5-178">The initialization script runs in the session that is created for the background job before the commands that are specified by the *ScriptBlock* parameter or the script that is specified by the *FilePath* parameter.</span></span>
<span data-ttu-id="822f5-179">U kunt het initialisatie script gebruiken om de sessie te configureren, zoals het toevoegen van bestanden, functies of aliassen, het maken van mappen of het controleren op vereisten.</span><span class="sxs-lookup"><span data-stu-id="822f5-179">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="822f5-180">Als u een script wilt opgeven dat de opdrachten van de primaire opdracht uitvoert, gebruikt u de *filepath* -para meter.</span><span class="sxs-lookup"><span data-stu-id="822f5-180">To specify a script that runs the primary job commands, use the *FilePath* parameter.</span></span>

<span data-ttu-id="822f5-181">Als het initialisatie script een fout genereert, inclusief een niet-afsluit fout, wordt het huidige exemplaar van de geplande taak niet uitgevoerd en is de status mislukt.</span><span class="sxs-lookup"><span data-stu-id="822f5-181">If the initialization script generates an error, including a non-terminating error, the current instance of the scheduled job does not run and its status is Failed.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-182">-Input object</span><span class="sxs-lookup"><span data-stu-id="822f5-182">-InputObject</span></span>
<span data-ttu-id="822f5-183">Hiermee geeft u de geplande taak moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="822f5-183">Specifies the scheduled job to be changed.</span></span>
<span data-ttu-id="822f5-184">Voer een variabele in die **ScheduledJobDefinition** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobDefinition** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.</span><span class="sxs-lookup"><span data-stu-id="822f5-184">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="822f5-185">U kunt ook een **ScheduledJobDefinition** -object pipeen naar **set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="822f5-185">You can also pipe a **ScheduledJobDefinition** object to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="822f5-186">Als u meerdere geplande taken opgeeft, worden met **set-ScheduledJob** dezelfde wijzigingen aangebracht aan alle taken.</span><span class="sxs-lookup"><span data-stu-id="822f5-186">If you specify multiple scheduled jobs, **Set-ScheduledJob** makes the same changes to all jobs.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-187">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="822f5-187">-MaxResultCount</span></span>
<span data-ttu-id="822f5-188">Hiermee geeft u op hoeveel items van de taak resultaat voor de geplande taak worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="822f5-188">Specifies how many job result entries are maintained for the scheduled job.</span></span>
<span data-ttu-id="822f5-189">De standaard waarde is 32.</span><span class="sxs-lookup"><span data-stu-id="822f5-189">The default value is 32.</span></span>

<span data-ttu-id="822f5-190">Windows Power shell slaat de uitvoerings geschiedenis en resultaten van elk geactiveerd exemplaar van de geplande taak op schijf op.</span><span class="sxs-lookup"><span data-stu-id="822f5-190">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span>
<span data-ttu-id="822f5-191">De waarde van deze para meter bepaalt het aantal taak exemplaar resultaten dat voor deze geplande taak wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="822f5-191">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span>
<span data-ttu-id="822f5-192">Wanneer het aantal taak exemplaren deze waarde overschrijdt, worden de resultaten van het oudste taak exemplaar door Windows Power shell verwijderd om ruimte te maken voor de resultaten van het nieuwste taak exemplaar.</span><span class="sxs-lookup"><span data-stu-id="822f5-192">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="822f5-193">De geschiedenis van de taak uitvoering en taak resultaten worden opgeslagen in de \Output-directory's van $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs \\ \<JobName\> \\ \<Timestamp\> op de computer waarop de taak is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="822f5-193">The job execution history and job results are saved in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\\\<JobName\>\Output\\\<Timestamp\> directories on the computer on which the job is created.</span></span>
<span data-ttu-id="822f5-194">Als u de uitvoerings geschiedenis wilt zien, gebruikt u de cmdlet Get-Job.</span><span class="sxs-lookup"><span data-stu-id="822f5-194">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="822f5-195">Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="822f5-195">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="822f5-196">Met de para meter *MaxResultCount* wordt de waarde van de eigenschap ExecutionHistoryLength van de geplande taak ingesteld.</span><span class="sxs-lookup"><span data-stu-id="822f5-196">The *MaxResultCount* parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="822f5-197">Als u de huidige uitvoerings geschiedenis en taak resultaten wilt verwijderen, gebruikt u de para meter *ClearExecutionHistory* .</span><span class="sxs-lookup"><span data-stu-id="822f5-197">To delete the current execution history and job results, use the *ClearExecutionHistory* parameter.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-198">-Name</span><span class="sxs-lookup"><span data-stu-id="822f5-198">-Name</span></span>
<span data-ttu-id="822f5-199">Hiermee geeft u een nieuwe naam op voor de geplande taak en exemplaren van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="822f5-199">Specifies a new name for the scheduled job and instances of the scheduled job.</span></span>
<span data-ttu-id="822f5-200">De naam moet uniek zijn op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="822f5-200">The name must be unique on the local computer.</span></span>

<span data-ttu-id="822f5-201">Als u wilt weten welke geplande taak moet worden gewijzigd, gebruikt u de para meter *input object* of pipet u een geplande taak van Get-ScheduledJob naar **set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="822f5-201">To identify the scheduled job to be changed, use the *InputObject* parameter or pipe a scheduled job from Get-ScheduledJob to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="822f5-202">Met deze para meter worden de namen van taak exemplaren op de schijf niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="822f5-202">This parameter does not change the names of job instances on disk.</span></span>
<span data-ttu-id="822f5-203">Dit is alleen van invloed op taak exemplaren die worden gestart nadat deze opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="822f5-203">It affects only job instances that are started after this command completes.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-204">-PassThru</span><span class="sxs-lookup"><span data-stu-id="822f5-204">-PassThru</span></span>
<span data-ttu-id="822f5-205">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="822f5-205">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="822f5-206">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="822f5-206">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="822f5-207">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="822f5-207">-RunAs32</span></span>
<span data-ttu-id="822f5-208">De geplande taak wordt uitgevoerd in een 32-bits proces.</span><span class="sxs-lookup"><span data-stu-id="822f5-208">Runs the scheduled job in a 32-bit process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-209">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="822f5-209">-RunEvery</span></span>

<span data-ttu-id="822f5-210">Wordt gebruikt om op te geven hoe vaak de taak moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="822f5-210">Used to specify how often to run the job.</span></span> <span data-ttu-id="822f5-211">Gebruik deze optie bijvoorbeeld om elke 15 minuten een taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="822f5-211">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-212">-RunNow</span><span class="sxs-lookup"><span data-stu-id="822f5-212">-RunNow</span></span>
<span data-ttu-id="822f5-213">Start een taak onmiddellijk zodra de cmdlet **set-ScheduledJob** wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="822f5-213">Starts a job immediately, as soon as the **Set-ScheduledJob** cmdlet is run.</span></span>
<span data-ttu-id="822f5-214">Met deze para meter is het niet nodig om taak planner te activeren om een Windows Power shell-script uit te voeren direct na de registratie, en hoeven gebruikers geen trigger te maken die een begin datum en-tijd opgeeft.</span><span class="sxs-lookup"><span data-stu-id="822f5-214">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and does not require users to create a trigger that specifies a starting date and time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-215">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="822f5-215">-ScheduledJobOption</span></span>
<span data-ttu-id="822f5-216">Opties instellen voor de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="822f5-216">Sets options for the scheduled job.</span></span>
<span data-ttu-id="822f5-217">Voer een **ScheduledJobOptions** -object in, zoals een, dat u maakt met behulp van de cmdlet New-ScheduledJobOption, of een hash-tabel waarde.</span><span class="sxs-lookup"><span data-stu-id="822f5-217">Enter a **ScheduledJobOptions** object, such as one that you create by using the New-ScheduledJobOption cmdlet, or a hash table value.</span></span>

<span data-ttu-id="822f5-218">U kunt opties voor een geplande taak instellen wanneer u de geplande taak registreert of de Set-ScheduledJobOption-of **set-ScheduledJob-** cmdlets gebruikt om opties in te stellen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="822f5-218">You can set options for a scheduled job when you register the scheduled job or use the Set-ScheduledJobOption or **Set-ScheduledJob** cmdlets to set or change options.</span></span>

<span data-ttu-id="822f5-219">Veel van de opties en hun standaard waarden bepalen of en wanneer een geplande taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="822f5-219">Many of the options and their default values determine whether and when a scheduled job runs.</span></span>
<span data-ttu-id="822f5-220">Controleer deze opties voordat u een taak plant.</span><span class="sxs-lookup"><span data-stu-id="822f5-220">Be sure to review these options before scheduling a job.</span></span>
<span data-ttu-id="822f5-221">Zie New-ScheduledJobOption voor een beschrijving van de opties voor geplande taken, met inbegrip van de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="822f5-221">For a description of the scheduled job options, including the default values, see New-ScheduledJobOption.</span></span>

<span data-ttu-id="822f5-222">Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="822f5-222">To submit a hash table, use the following keys.</span></span>
<span data-ttu-id="822f5-223">In de volgende hash-tabel worden de sleutels weer gegeven met de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="822f5-223">In the following hash table, the keys are shown with their default values.</span></span>

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-224">-Script Block</span><span class="sxs-lookup"><span data-stu-id="822f5-224">-ScriptBlock</span></span>
<span data-ttu-id="822f5-225">Hiermee geeft u de opdrachten op die door de geplande taak worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="822f5-225">Specifies the commands that the scheduled job runs.</span></span>
<span data-ttu-id="822f5-226">Plaats de opdrachten tussen accolades ({}) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="822f5-226">Enclose the commands in braces ( { } ) to create a script block.</span></span>
<span data-ttu-id="822f5-227">Als u standaard waarden voor opdracht parameters wilt opgeven, gebruikt u de para meter *argument List* .</span><span class="sxs-lookup"><span data-stu-id="822f5-227">To specify default values for command parameters, use the *ArgumentList* parameter.</span></span>

<span data-ttu-id="822f5-228">Elke Register-ScheduledJob-opdracht moet de para meters *script Block* of *filepath* gebruiken.</span><span class="sxs-lookup"><span data-stu-id="822f5-228">Every Register-ScheduledJob command must use either the *ScriptBlock* or *FilePath* parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-229">-Trigger</span><span class="sxs-lookup"><span data-stu-id="822f5-229">-Trigger</span></span>
<span data-ttu-id="822f5-230">Hiermee geeft u de triggers voor de geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="822f5-230">Specifies the triggers for the scheduled job.</span></span>
<span data-ttu-id="822f5-231">Voer een of meer **ScheduledJobTrigger** -objecten in, zoals de objecten die de New-JobTrigger cmdlet retourneert of een hash-tabel met sleutels en waarden van de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="822f5-231">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the New-JobTrigger cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="822f5-232">Met een taak trigger wordt automatisch een geplande taak gestart op een eenmalige of terugkerende geplande of wanneer er een gebeurtenis optreedt.</span><span class="sxs-lookup"><span data-stu-id="822f5-232">A job trigger starts a scheduled job automatically on a one-time or recurring scheduled or when an event occurs.</span></span>

<span data-ttu-id="822f5-233">Taak triggers zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="822f5-233">Job triggers are optional.</span></span>
<span data-ttu-id="822f5-234">U kunt een trigger toevoegen tijdens het maken van de geplande taak. Gebruik de cmdlets Add-JobTrigger of **set-ScheduledJob** om later triggers toe te voegen of gebruik de Start-Job cmdlet om de geplande taak onmiddellijk te starten.</span><span class="sxs-lookup"><span data-stu-id="822f5-234">You can add a trigger when you create the scheduled job, use the Add-JobTrigger or **Set-ScheduledJob** cmdlets to add triggers later, or use the Start-Job cmdlet to start the scheduled job immediately.</span></span>
<span data-ttu-id="822f5-235">U kunt ook een geplande taak maken en onderhouden die geen taak triggers heeft.</span><span class="sxs-lookup"><span data-stu-id="822f5-235">You can also create and maintain a scheduled job that has no job triggers.</span></span>

<span data-ttu-id="822f5-236">Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="822f5-236">To submit a hash table, use the following keys.</span></span>

<span data-ttu-id="822f5-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (of een wille keurige geldige tijd reeks); `DaysOfWeek="Monday", "Wednesday"` (of een combi natie van namen van dagen); `Interval=2` (of een geldig frequentie-interval); `RandomDelay="30minutes"` (of een wille keurige geldige time span-teken reeks); `User="Domain1\User01"` (of een geldige gebruiker; wordt alleen gebruikt met de frequentie waarde AtLogon)</span><span class="sxs-lookup"><span data-stu-id="822f5-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01"` (or any valid user; used only with the AtLogon frequency value)</span></span>

<span data-ttu-id="822f5-238">}</span><span class="sxs-lookup"><span data-stu-id="822f5-238">}</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="822f5-239">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="822f5-239">CommonParameters</span></span>
<span data-ttu-id="822f5-240">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="822f5-240">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="822f5-241">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="822f5-241">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="822f5-242">INVOER</span><span class="sxs-lookup"><span data-stu-id="822f5-242">INPUTS</span></span>

### <span data-ttu-id="822f5-243">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="822f5-243">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="822f5-244">U kunt geplande taken door sluizen naar **set-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="822f5-244">You can pipe scheduled jobs to **Set-ScheduledJob**.</span></span>

## <span data-ttu-id="822f5-245">UITVOER</span><span class="sxs-lookup"><span data-stu-id="822f5-245">OUTPUTS</span></span>

### <span data-ttu-id="822f5-246">Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="822f5-246">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="822f5-247">Als u de para meter *PassThru* gebruikt, wordt door **set-ScheduledJob** de geplande taak geretourneerd die is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="822f5-247">If you use the *Passthru* parameter, **Set-ScheduledJob** returns the scheduled job that was changed.</span></span>
<span data-ttu-id="822f5-248">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="822f5-248">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="822f5-249">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="822f5-249">NOTES</span></span>

## <span data-ttu-id="822f5-250">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="822f5-250">RELATED LINKS</span></span>

[<span data-ttu-id="822f5-251">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="822f5-251">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="822f5-252">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="822f5-252">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="822f5-253">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="822f5-253">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="822f5-254">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="822f5-254">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="822f5-255">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="822f5-255">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="822f5-256">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="822f5-256">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="822f5-257">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="822f5-257">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="822f5-258">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="822f5-258">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="822f5-259">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="822f5-259">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="822f5-260">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="822f5-260">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="822f5-261">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="822f5-261">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="822f5-262">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="822f5-262">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="822f5-263">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="822f5-263">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="822f5-264">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="822f5-264">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="822f5-265">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="822f5-265">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="822f5-266">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="822f5-266">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
