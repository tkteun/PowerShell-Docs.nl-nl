---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 7b872c2a28943ee3d2b9ab27459ddb87722cc954
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250161"
---
# <span data-ttu-id="2220a-103">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="2220a-103">Receive-Job</span></span>

## <span data-ttu-id="2220a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2220a-104">SYNOPSIS</span></span>
<span data-ttu-id="2220a-105">Hiermee worden de resultaten van de Power shell-achtergrond taken in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2220a-105">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="2220a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2220a-106">SYNTAX</span></span>

### <span data-ttu-id="2220a-107">Locatie (standaard)</span><span class="sxs-lookup"><span data-stu-id="2220a-107">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="2220a-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="2220a-108">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="2220a-109">ComputerName</span><span class="sxs-lookup"><span data-stu-id="2220a-109">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="2220a-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="2220a-110">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="2220a-111">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2220a-111">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="2220a-112">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="2220a-112">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="2220a-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2220a-113">DESCRIPTION</span></span>

<span data-ttu-id="2220a-114">Met de `Receive-Job` cmdlet worden de resultaten van Power shell-achtergrond taken opgehaald, zoals die zijn gestart met behulp `Start-Job` van de cmdlet of de **AsJob** -para meter van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2220a-114">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="2220a-115">U kunt de resultaten van alle taken ophalen of taken identificeren met hun naam, ID, exemplaar-ID, computer naam, locatie of sessie of door een taak object in te dienen.</span><span class="sxs-lookup"><span data-stu-id="2220a-115">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="2220a-116">Wanneer u een Power shell-achtergrond taak start, wordt de taak gestart, maar worden de resultaten niet onmiddellijk weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2220a-116">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="2220a-117">In plaats daarvan wordt met de opdracht een object geretourneerd dat de achtergrond taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2220a-117">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="2220a-118">Het taak object bevat nuttige informatie over de taak, maar bevat niet de resultaten.</span><span class="sxs-lookup"><span data-stu-id="2220a-118">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="2220a-119">Met deze methode kunt u in de sessie blijven werken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2220a-119">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="2220a-120">Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over achtergrond taken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2220a-120">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="2220a-121">De `Receive-Job` cmdlet haalt de resultaten op die zijn gegenereerd op het moment dat de `Receive-Job` opdracht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="2220a-121">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="2220a-122">Als de resultaten nog niet zijn voltooid, kunt u aanvullende `Receive-Job` opdrachten uitvoeren om de resterende resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="2220a-122">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="2220a-123">Standaard worden taak resultaten uit het systeem verwijderd wanneer u ze ontvangt, maar u kunt de para meter **bewaren** gebruiken om de resultaten op te slaan, zodat u ze opnieuw kunt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="2220a-123">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="2220a-124">Als u de taak resultaten wilt verwijderen, voert u de `Receive-Job` opdracht opnieuw uit zonder de para meter **Keep** , sluit u de sessie of gebruikt `Remove-Job` u de cmdlet om de taak uit de sessie te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2220a-124">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="2220a-125">Met ingang van Windows Power Shell 3,0 worden `Receive-Job` ook de resultaten van aangepaste taak typen opgehaald, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="2220a-125">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="2220a-126">Als u `Receive-Job` wilt inschakelen om de resultaten van een aangepast taak type op te halen, importeert u de module die het aangepaste taak type in de sessie ondersteunt voordat een opdracht wordt uitgevoerd `Receive-Job` , met behulp van de `Import-Module` cmdlet of door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="2220a-126">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="2220a-127">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="2220a-127">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="2220a-128">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2220a-128">EXAMPLES</span></span>

### <span data-ttu-id="2220a-129">Voor beeld 1: resultaten voor een bepaalde taak ophalen</span><span class="sxs-lookup"><span data-stu-id="2220a-129">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="2220a-130">Deze opdrachten gebruiken de **taak** parameter van `Receive-Job` om de resultaten van een bepaalde taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="2220a-130">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="2220a-131">Met de eerste opdracht wordt een taak gestart `Start-Job` en wordt het taak object in de `$job` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2220a-131">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="2220a-132">Met de tweede opdracht wordt de `Receive-Job` cmdlet gebruikt om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="2220a-132">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="2220a-133">De **taak** parameter wordt gebruikt om de taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="2220a-133">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="2220a-134">Voor beeld 2: de para meter Keep gebruiken</span><span class="sxs-lookup"><span data-stu-id="2220a-134">Example 2: Use the Keep parameter</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="2220a-135">In dit voor beeld wordt een taak opgeslagen in de `$job` variabele en wordt de taak door sluizen naar de `Receive-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2220a-135">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="2220a-136">De `-Keep` para meter wordt ook gebruikt om toe te staan dat alle geaggregeerde stroom gegevens opnieuw worden opgehaald na de eerste weer gave.</span><span class="sxs-lookup"><span data-stu-id="2220a-136">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="2220a-137">Voor beeld 3: resultaten van verschillende achtergrond taken ophalen</span><span class="sxs-lookup"><span data-stu-id="2220a-137">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="2220a-138">Wanneer u de para meter **AsJob** van gebruikt `Invoke-Command` om een taak te starten, wordt het taak object gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="2220a-138">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="2220a-139">Als gevolg hiervan kunt u lokale opdrachten gebruiken om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="2220a-139">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="2220a-140">Wanneer u **AsJob** gebruikt, retourneert Power shell een taak object dat een onderliggende taak bevat voor elke taak die is gestart.</span><span class="sxs-lookup"><span data-stu-id="2220a-140">Also, when you use **AsJob** , PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="2220a-141">In dit geval bevat het taak object drie onderliggende taken, één voor elke taak op elke externe computer.</span><span class="sxs-lookup"><span data-stu-id="2220a-141">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### <span data-ttu-id="2220a-142">Voor beeld 4: resultaten van achtergrond taken op meerdere externe computers ophalen</span><span class="sxs-lookup"><span data-stu-id="2220a-142">Example 4: Get results of background jobs on multiple remote computers</span></span>

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

<span data-ttu-id="2220a-143">In dit voor beeld ziet u hoe de resultaten van achtergrond taken worden uitgevoerd op drie externe computers.</span><span class="sxs-lookup"><span data-stu-id="2220a-143">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="2220a-144">In tegens telling tot het vorige voor beeld, gebruikt `Invoke-Command` om de opdracht uit te voeren, `Start-Job` drie onafhankelijke taken op elk van de drie computers.</span><span class="sxs-lookup"><span data-stu-id="2220a-144">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="2220a-145">Als gevolg hiervan heeft de opdracht drie taak objecten geretourneerd die drie taken vertegenwoordigen die lokaal worden uitgevoerd op drie verschillende computers.</span><span class="sxs-lookup"><span data-stu-id="2220a-145">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="2220a-146">In de laatste opdracht, omdat `$j` een lokale variabele is, gebruikt het script blok de aanpassings functie voor het **gebruik van** de scope om de variabele te identificeren `$j` .</span><span class="sxs-lookup"><span data-stu-id="2220a-146">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="2220a-147">Zie [about_Remote_Variables](./About/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.</span><span class="sxs-lookup"><span data-stu-id="2220a-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="2220a-148">Voor beeld 5: toegang tot onderliggende taken</span><span class="sxs-lookup"><span data-stu-id="2220a-148">Example 5: Access child jobs</span></span>

<span data-ttu-id="2220a-149">Met de `-Keep` para meter wordt de status van de geaggregeerde streams van een taak behouden, zodat deze weer kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2220a-149">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="2220a-150">Zonder deze para meter worden alle samengevoegde stroom gegevens gewist wanneer de taak wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="2220a-150">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="2220a-151">Zie [about_Job_Details](About/about_Job_Details.md#child-jobs) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2220a-151">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="2220a-152">De geaggregeerde streams bevatten de streams van alle onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="2220a-152">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="2220a-153">U kunt nog steeds de afzonderlijke gegevens stromen bereiken via het taak object en onderliggende taak objecten.</span><span class="sxs-lookup"><span data-stu-id="2220a-153">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="2220a-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2220a-154">PARAMETERS</span></span>

### <span data-ttu-id="2220a-155">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="2220a-155">-AutoRemoveJob</span></span>

<span data-ttu-id="2220a-156">Geeft aan dat deze cmdlet de taak verwijdert nadat de taak resultaten zijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2220a-156">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="2220a-157">Als de taak meer resultaten heeft, wordt de taak nog steeds verwijderd, maar `Receive-Job` wordt een bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2220a-157">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="2220a-158">Deze para meter werkt alleen voor aangepaste taak typen.</span><span class="sxs-lookup"><span data-stu-id="2220a-158">This parameter works only on custom job types.</span></span>
<span data-ttu-id="2220a-159">Het is bedoeld voor exemplaren van taak typen die de taak of het type buiten de sessie opslaan, zoals exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="2220a-159">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="2220a-160">Deze para meter kan niet worden gebruikt zonder de para meter **wait** .</span><span class="sxs-lookup"><span data-stu-id="2220a-160">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="2220a-161">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2220a-161">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="2220a-162">-ComputerName</span></span>

<span data-ttu-id="2220a-163">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="2220a-163">Specifies an array of names of computers.</span></span>

<span data-ttu-id="2220a-164">Met deze para meter selecteert u onder de taak resultaten die zijn opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2220a-164">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="2220a-165">Er worden geen gegevens opgehaald voor taken die worden uitgevoerd op externe computers.</span><span class="sxs-lookup"><span data-stu-id="2220a-165">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="2220a-166">Als u taak resultaten wilt ophalen die zijn opgeslagen op externe computers, gebruikt u de `Invoke-Command` cmdlet om een `Receive-Job` opdracht op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2220a-166">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2220a-167">-Force</span><span class="sxs-lookup"><span data-stu-id="2220a-167">-Force</span></span>

<span data-ttu-id="2220a-168">Geeft aan dat deze cmdlet blijft wachten als taken de status **onderbroken** of **losgekoppeld** hebben.</span><span class="sxs-lookup"><span data-stu-id="2220a-168">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="2220a-169">De **wait** -para meter van `Receive-Job` retourneert of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="2220a-169">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="2220a-170">Voltooid</span><span class="sxs-lookup"><span data-stu-id="2220a-170">Completed</span></span>
- <span data-ttu-id="2220a-171">Mislukt</span><span class="sxs-lookup"><span data-stu-id="2220a-171">Failed</span></span>
- <span data-ttu-id="2220a-172">Gestopt</span><span class="sxs-lookup"><span data-stu-id="2220a-172">Stopped</span></span>
- <span data-ttu-id="2220a-173">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="2220a-173">Suspended</span></span>
- <span data-ttu-id="2220a-174">Verbroken.</span><span class="sxs-lookup"><span data-stu-id="2220a-174">Disconnected.</span></span>

<span data-ttu-id="2220a-175">De para meter **Force** is alleen geldig als de **wait** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2220a-175">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="2220a-176">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2220a-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-177">-Id</span><span class="sxs-lookup"><span data-stu-id="2220a-177">-Id</span></span>

<span data-ttu-id="2220a-178">Hiermee geeft u een matrix met Id's op.</span><span class="sxs-lookup"><span data-stu-id="2220a-178">Specifies an array of IDs.</span></span>
<span data-ttu-id="2220a-179">Met deze cmdlet worden de resultaten van taken met de opgegeven Id's opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2220a-179">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="2220a-180">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2220a-180">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="2220a-181">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2220a-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="2220a-182">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="2220a-182">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="2220a-183">Als u de ID van een taak wilt zoeken, gebruikt u `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="2220a-183">To find the ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="2220a-184">-InstanceId</span></span>

<span data-ttu-id="2220a-185">Hiermee geeft u een matrix met exemplaar-Id's op.</span><span class="sxs-lookup"><span data-stu-id="2220a-185">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="2220a-186">Met deze cmdlet worden de resultaten van taken met de opgegeven exemplaar-Id's opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2220a-186">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="2220a-187">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="2220a-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="2220a-188">Gebruik de cmdlet om de exemplaar-ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="2220a-188">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-189">-Taak</span><span class="sxs-lookup"><span data-stu-id="2220a-189">-Job</span></span>

<span data-ttu-id="2220a-190">Hiermee geeft u de taak op waarvoor de resultaten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2220a-190">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="2220a-191">Voer een variabele in die de taak of een opdracht bevat die de taak ontvangt.</span><span class="sxs-lookup"><span data-stu-id="2220a-191">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="2220a-192">U kunt ook een taak object door sluizen naar `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="2220a-192">You can also pipe a job object to `Receive-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-193">-Keep</span><span class="sxs-lookup"><span data-stu-id="2220a-193">-Keep</span></span>

<span data-ttu-id="2220a-194">Geeft aan dat deze cmdlet de geaggregeerde stream-gegevens in het systeem opslaat, zelfs nadat u ze hebt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="2220a-194">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="2220a-195">Samengevoegde stroom gegevens worden standaard gewist na weer gave met `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="2220a-195">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="2220a-196">Als u de sessie sluit of als u de taak met de cmdlet verwijdert, `Remove-Job` worden ook geaggregeerde stroom gegevens verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2220a-196">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-197">-Locatie</span><span class="sxs-lookup"><span data-stu-id="2220a-197">-Location</span></span>

<span data-ttu-id="2220a-198">Hiermee geeft u een matrix met locaties op.</span><span class="sxs-lookup"><span data-stu-id="2220a-198">Specifies an array of locations.</span></span>
<span data-ttu-id="2220a-199">Met deze cmdlet worden alleen de resultaten van taken op de opgegeven locaties opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2220a-199">This cmdlet gets only the results of jobs in the specified locations.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-200">-Name</span><span class="sxs-lookup"><span data-stu-id="2220a-200">-Name</span></span>

<span data-ttu-id="2220a-201">Hiermee geeft u een matrix met beschrijvende namen op.</span><span class="sxs-lookup"><span data-stu-id="2220a-201">Specifies an array of friendly names.</span></span>
<span data-ttu-id="2220a-202">Met deze cmdlet worden de resultaten opgehaald van taken met de opgegeven namen.</span><span class="sxs-lookup"><span data-stu-id="2220a-202">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="2220a-203">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="2220a-203">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2220a-204">-Niet-terugkerend</span><span class="sxs-lookup"><span data-stu-id="2220a-204">-NoRecurse</span></span>

<span data-ttu-id="2220a-205">Geeft aan dat deze cmdlet alleen resultaten ophaalt van de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="2220a-205">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="2220a-206">`Receive-Job`De resultaten van alle onderliggende taken van de opgegeven taak worden standaard ook opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2220a-206">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-207">-Sessie</span><span class="sxs-lookup"><span data-stu-id="2220a-207">-Session</span></span>

<span data-ttu-id="2220a-208">Hiermee geeft u een matrix met sessies op.</span><span class="sxs-lookup"><span data-stu-id="2220a-208">Specifies an array of sessions.</span></span>
<span data-ttu-id="2220a-209">Met deze cmdlet worden de resultaten opgehaald van taken die zijn uitgevoerd in de opgegeven Power shell-sessie ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="2220a-209">This cmdlet gets the results of jobs that were run in the specified PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="2220a-210">Voer een variabele in die de **PSSession** bevat of een opdracht die de **PSSession** , zoals een opdracht, ophalen `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="2220a-210">Enter a variable that contains the **PSSession** or a command that gets the **PSSession** , such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-211">-Wachten</span><span class="sxs-lookup"><span data-stu-id="2220a-211">-Wait</span></span>

<span data-ttu-id="2220a-212">Geeft aan dat deze cmdlet de opdracht prompt onderdrukt totdat alle taak resultaten zijn ontvangen.</span><span class="sxs-lookup"><span data-stu-id="2220a-212">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="2220a-213">Standaard `Receive-Job` retourneert onmiddellijk de beschik bare resultaten.</span><span class="sxs-lookup"><span data-stu-id="2220a-213">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="2220a-214">Standaard wacht de **wait** -para meter totdat de taak een van de volgende statussen heeft:</span><span class="sxs-lookup"><span data-stu-id="2220a-214">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="2220a-215">Voltooid</span><span class="sxs-lookup"><span data-stu-id="2220a-215">Completed</span></span>
- <span data-ttu-id="2220a-216">Mislukt</span><span class="sxs-lookup"><span data-stu-id="2220a-216">Failed</span></span>
- <span data-ttu-id="2220a-217">Gestopt</span><span class="sxs-lookup"><span data-stu-id="2220a-217">Stopped</span></span>
- <span data-ttu-id="2220a-218">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="2220a-218">Suspended</span></span>
- <span data-ttu-id="2220a-219">Verbroken.</span><span class="sxs-lookup"><span data-stu-id="2220a-219">Disconnected.</span></span>

<span data-ttu-id="2220a-220">Als u de **wait** -para meter wilt blijven wachten als de taak status onderbroken of losgekoppeld is, gebruikt u de para meter **Force** in combi natie met de para meter **wait** .</span><span class="sxs-lookup"><span data-stu-id="2220a-220">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="2220a-221">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2220a-221">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="2220a-222">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="2220a-222">-WriteEvents</span></span>

<span data-ttu-id="2220a-223">Geeft aan dat deze cmdlet wijzigingen in de taak status rapporteert terwijl de taak kan worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="2220a-223">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="2220a-224">Deze para meter is alleen geldig als de **wait** -para meter wordt gebruikt in de opdracht en de **Keep** -para meter wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="2220a-224">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="2220a-225">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2220a-225">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-226">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="2220a-226">-WriteJobInResults</span></span>

<span data-ttu-id="2220a-227">Geeft aan dat deze cmdlet het taak object retourneert, gevolgd door de resultaten.</span><span class="sxs-lookup"><span data-stu-id="2220a-227">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="2220a-228">Deze para meter is alleen geldig als de **wait** -para meter wordt gebruikt in de opdracht en de **Keep** -para meter wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="2220a-228">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="2220a-229">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2220a-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2220a-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2220a-230">CommonParameters</span></span>

<span data-ttu-id="2220a-231">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2220a-231">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2220a-232">Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2220a-232">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2220a-233">INVOER</span><span class="sxs-lookup"><span data-stu-id="2220a-233">INPUTS</span></span>

### <span data-ttu-id="2220a-234">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="2220a-234">System.Management.Automation.Job</span></span>

<span data-ttu-id="2220a-235">U kunt taak objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2220a-235">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="2220a-236">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2220a-236">OUTPUTS</span></span>

### <span data-ttu-id="2220a-237">PSObject</span><span class="sxs-lookup"><span data-stu-id="2220a-237">PSObject</span></span>

<span data-ttu-id="2220a-238">Met deze cmdlet worden de resultaten van de opdrachten in de taak geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2220a-238">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="2220a-239">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2220a-239">NOTES</span></span>

## <span data-ttu-id="2220a-240">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2220a-240">RELATED LINKS</span></span>

[<span data-ttu-id="2220a-241">Get-job</span><span class="sxs-lookup"><span data-stu-id="2220a-241">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="2220a-242">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="2220a-242">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="2220a-243">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="2220a-243">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="2220a-244">Resume-job</span><span class="sxs-lookup"><span data-stu-id="2220a-244">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="2220a-245">Begin taak</span><span class="sxs-lookup"><span data-stu-id="2220a-245">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="2220a-246">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="2220a-246">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="2220a-247">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="2220a-247">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="2220a-248">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="2220a-248">Wait-Job</span></span>](Wait-Job.md)
