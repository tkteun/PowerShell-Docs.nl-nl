---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 3a11bdb27f3fe16b7b66e82821a3ffe8fa5f6cfa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706059"
---
# <span data-ttu-id="c9a25-102">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="c9a25-102">Receive-Job</span></span>

## <span data-ttu-id="c9a25-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c9a25-103">SYNOPSIS</span></span>
<span data-ttu-id="c9a25-104">Hiermee worden de resultaten van de Power shell-achtergrond taken in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9a25-104">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="c9a25-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c9a25-105">SYNTAX</span></span>

### <span data-ttu-id="c9a25-106">Locatie (standaard)</span><span class="sxs-lookup"><span data-stu-id="c9a25-106">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="c9a25-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c9a25-107">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="c9a25-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="c9a25-108">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="c9a25-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="c9a25-109">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c9a25-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="c9a25-110">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="c9a25-111">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="c9a25-111">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="c9a25-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c9a25-112">DESCRIPTION</span></span>

<span data-ttu-id="c9a25-113">Met de `Receive-Job` cmdlet worden de resultaten van Power shell-achtergrond taken opgehaald, zoals die zijn gestart met behulp `Start-Job` van de cmdlet of de **AsJob** -para meter van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9a25-113">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="c9a25-114">U kunt de resultaten van alle taken ophalen of taken identificeren met hun naam, ID, exemplaar-ID, computer naam, locatie of sessie of door een taak object in te dienen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-114">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="c9a25-115">Wanneer u een Power shell-achtergrond taak start, wordt de taak gestart, maar worden de resultaten niet onmiddellijk weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9a25-115">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="c9a25-116">In plaats daarvan wordt met de opdracht een object geretourneerd dat de achtergrond taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c9a25-116">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="c9a25-117">Het taak object bevat nuttige informatie over de taak, maar bevat niet de resultaten.</span><span class="sxs-lookup"><span data-stu-id="c9a25-117">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="c9a25-118">Met deze methode kunt u in de sessie blijven werken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c9a25-118">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="c9a25-119">Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over achtergrond taken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c9a25-119">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="c9a25-120">De `Receive-Job` cmdlet haalt de resultaten op die zijn gegenereerd op het moment dat de `Receive-Job` opdracht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="c9a25-120">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="c9a25-121">Als de resultaten nog niet zijn voltooid, kunt u aanvullende `Receive-Job` opdrachten uitvoeren om de resterende resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-121">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="c9a25-122">Standaard worden taak resultaten uit het systeem verwijderd wanneer u ze ontvangt, maar u kunt de para meter **bewaren** gebruiken om de resultaten op te slaan, zodat u ze opnieuw kunt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-122">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="c9a25-123">Als u de taak resultaten wilt verwijderen, voert u de `Receive-Job` opdracht opnieuw uit zonder de para meter **Keep** , sluit u de sessie of gebruikt `Remove-Job` u de cmdlet om de taak uit de sessie te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-123">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="c9a25-124">Met ingang van Windows Power Shell 3,0 worden `Receive-Job` ook de resultaten van aangepaste taak typen opgehaald, zoals werk stroom taken en exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="c9a25-124">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="c9a25-125">Als u `Receive-Job` wilt inschakelen om de resultaten van een aangepast taak type op te halen, importeert u de module die het aangepaste taak type in de sessie ondersteunt voordat een opdracht wordt uitgevoerd `Receive-Job` , met behulp van de `Import-Module` cmdlet of door een cmdlet in de module te gebruiken of op te halen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-125">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="c9a25-126">Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.</span><span class="sxs-lookup"><span data-stu-id="c9a25-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="c9a25-127">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c9a25-127">EXAMPLES</span></span>

### <span data-ttu-id="c9a25-128">Voor beeld 1: resultaten voor een bepaalde taak ophalen</span><span class="sxs-lookup"><span data-stu-id="c9a25-128">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="c9a25-129">Deze opdrachten gebruiken de **taak** parameter van `Receive-Job` om de resultaten van een bepaalde taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-129">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="c9a25-130">Met de eerste opdracht wordt een taak gestart `Start-Job` en wordt het taak object in de `$job` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-130">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="c9a25-131">Met de tweede opdracht wordt de `Receive-Job` cmdlet gebruikt om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-131">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="c9a25-132">De **taak** parameter wordt gebruikt om de taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="c9a25-132">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="c9a25-133">Voor beeld 2: de para meter Keep gebruiken</span><span class="sxs-lookup"><span data-stu-id="c9a25-133">Example 2: Use the Keep parameter</span></span>

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

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="c9a25-134">In dit voor beeld wordt een taak opgeslagen in de `$job` variabele en wordt de taak door sluizen naar de `Receive-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9a25-134">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="c9a25-135">De `-Keep` para meter wordt ook gebruikt om toe te staan dat alle geaggregeerde stroom gegevens opnieuw worden opgehaald na de eerste weer gave.</span><span class="sxs-lookup"><span data-stu-id="c9a25-135">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="c9a25-136">Voor beeld 3: resultaten van verschillende achtergrond taken ophalen</span><span class="sxs-lookup"><span data-stu-id="c9a25-136">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="c9a25-137">Wanneer u de para meter **AsJob** van gebruikt `Invoke-Command` om een taak te starten, wordt het taak object gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="c9a25-137">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="c9a25-138">Als gevolg hiervan kunt u lokale opdrachten gebruiken om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="c9a25-138">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="c9a25-139">Wanneer u **AsJob** gebruikt, retourneert Power shell een taak object dat een onderliggende taak bevat voor elke taak die is gestart.</span><span class="sxs-lookup"><span data-stu-id="c9a25-139">Also, when you use **AsJob**, PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="c9a25-140">In dit geval bevat het taak object drie onderliggende taken, één voor elke taak op elke externe computer.</span><span class="sxs-lookup"><span data-stu-id="c9a25-140">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

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

### <span data-ttu-id="c9a25-141">Voor beeld 4: resultaten van achtergrond taken op meerdere externe computers ophalen</span><span class="sxs-lookup"><span data-stu-id="c9a25-141">Example 4: Get results of background jobs on multiple remote computers</span></span>

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

<span data-ttu-id="c9a25-142">In dit voor beeld ziet u hoe de resultaten van achtergrond taken worden uitgevoerd op drie externe computers.</span><span class="sxs-lookup"><span data-stu-id="c9a25-142">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="c9a25-143">In tegens telling tot het vorige voor beeld, gebruikt `Invoke-Command` om de opdracht uit te voeren, `Start-Job` drie onafhankelijke taken op elk van de drie computers.</span><span class="sxs-lookup"><span data-stu-id="c9a25-143">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="c9a25-144">Als gevolg hiervan heeft de opdracht drie taak objecten geretourneerd die drie taken vertegenwoordigen die lokaal worden uitgevoerd op drie verschillende computers.</span><span class="sxs-lookup"><span data-stu-id="c9a25-144">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="c9a25-145">In de laatste opdracht, omdat `$j` een lokale variabele is, gebruikt het script blok de aanpassings functie voor het **gebruik van** de scope om de variabele te identificeren `$j` .</span><span class="sxs-lookup"><span data-stu-id="c9a25-145">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="c9a25-146">Zie [about_Remote_Variables](./About/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.</span><span class="sxs-lookup"><span data-stu-id="c9a25-146">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="c9a25-147">Voor beeld 5: toegang tot onderliggende taken</span><span class="sxs-lookup"><span data-stu-id="c9a25-147">Example 5: Access child jobs</span></span>

<span data-ttu-id="c9a25-148">Met de `-Keep` para meter wordt de status van de geaggregeerde streams van een taak behouden, zodat deze weer kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9a25-148">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="c9a25-149">Zonder deze para meter worden alle samengevoegde stroom gegevens gewist wanneer de taak wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-149">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="c9a25-150">Zie [about_Job_Details](About/about_Job_Details.md#child-jobs) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9a25-150">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="c9a25-151">De geaggregeerde streams bevatten de streams van alle onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="c9a25-151">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="c9a25-152">U kunt nog steeds de afzonderlijke gegevens stromen bereiken via het taak object en onderliggende taak objecten.</span><span class="sxs-lookup"><span data-stu-id="c9a25-152">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
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

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="c9a25-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c9a25-153">PARAMETERS</span></span>

### <span data-ttu-id="c9a25-154">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="c9a25-154">-AutoRemoveJob</span></span>

<span data-ttu-id="c9a25-155">Geeft aan dat deze cmdlet de taak verwijdert nadat de taak resultaten zijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c9a25-155">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="c9a25-156">Als de taak meer resultaten heeft, wordt de taak nog steeds verwijderd, maar `Receive-Job` wordt een bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9a25-156">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="c9a25-157">Deze para meter werkt alleen voor aangepaste taak typen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-157">This parameter works only on custom job types.</span></span>
<span data-ttu-id="c9a25-158">Het is bedoeld voor exemplaren van taak typen die de taak of het type buiten de sessie opslaan, zoals exemplaren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="c9a25-158">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="c9a25-159">Deze para meter kan niet worden gebruikt zonder de para meter **wait** .</span><span class="sxs-lookup"><span data-stu-id="c9a25-159">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="c9a25-160">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c9a25-160">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c9a25-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c9a25-161">-ComputerName</span></span>

<span data-ttu-id="c9a25-162">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="c9a25-162">Specifies an array of names of computers.</span></span>

<span data-ttu-id="c9a25-163">Met deze para meter selecteert u onder de taak resultaten die zijn opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c9a25-163">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="c9a25-164">Er worden geen gegevens opgehaald voor taken die worden uitgevoerd op externe computers.</span><span class="sxs-lookup"><span data-stu-id="c9a25-164">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="c9a25-165">Als u taak resultaten wilt ophalen die zijn opgeslagen op externe computers, gebruikt u de `Invoke-Command` cmdlet om een `Receive-Job` opdracht op afstand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c9a25-165">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

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

### <span data-ttu-id="c9a25-166">-Force</span><span class="sxs-lookup"><span data-stu-id="c9a25-166">-Force</span></span>

<span data-ttu-id="c9a25-167">Geeft aan dat deze cmdlet blijft wachten als taken de status **onderbroken** of **losgekoppeld** hebben.</span><span class="sxs-lookup"><span data-stu-id="c9a25-167">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="c9a25-168">De **wait** -para meter van `Receive-Job` retourneert of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:</span><span class="sxs-lookup"><span data-stu-id="c9a25-168">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="c9a25-169">Voltooid</span><span class="sxs-lookup"><span data-stu-id="c9a25-169">Completed</span></span>
- <span data-ttu-id="c9a25-170">Mislukt</span><span class="sxs-lookup"><span data-stu-id="c9a25-170">Failed</span></span>
- <span data-ttu-id="c9a25-171">Gestopt</span><span class="sxs-lookup"><span data-stu-id="c9a25-171">Stopped</span></span>
- <span data-ttu-id="c9a25-172">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="c9a25-172">Suspended</span></span>
- <span data-ttu-id="c9a25-173">Verbroken.</span><span class="sxs-lookup"><span data-stu-id="c9a25-173">Disconnected.</span></span>

<span data-ttu-id="c9a25-174">De para meter **Force** is alleen geldig als de **wait** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c9a25-174">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="c9a25-175">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c9a25-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c9a25-176">-Id</span><span class="sxs-lookup"><span data-stu-id="c9a25-176">-Id</span></span>

<span data-ttu-id="c9a25-177">Hiermee geeft u een matrix met Id's op.</span><span class="sxs-lookup"><span data-stu-id="c9a25-177">Specifies an array of IDs.</span></span>
<span data-ttu-id="c9a25-178">Met deze cmdlet worden de resultaten van taken met de opgegeven Id's opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9a25-178">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="c9a25-179">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="c9a25-179">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="c9a25-180">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="c9a25-180">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="c9a25-181">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="c9a25-181">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="c9a25-182">Als u de ID van een taak wilt zoeken, gebruikt u `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="c9a25-182">To find the ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="c9a25-183">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="c9a25-183">-InstanceId</span></span>

<span data-ttu-id="c9a25-184">Hiermee geeft u een matrix met exemplaar-Id's op.</span><span class="sxs-lookup"><span data-stu-id="c9a25-184">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="c9a25-185">Met deze cmdlet worden de resultaten van taken met de opgegeven exemplaar-Id's opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9a25-185">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="c9a25-186">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="c9a25-186">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="c9a25-187">Gebruik de cmdlet om de exemplaar-ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="c9a25-187">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

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

### <span data-ttu-id="c9a25-188">-Taak</span><span class="sxs-lookup"><span data-stu-id="c9a25-188">-Job</span></span>

<span data-ttu-id="c9a25-189">Hiermee geeft u de taak op waarvoor de resultaten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9a25-189">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="c9a25-190">Voer een variabele in die de taak of een opdracht bevat die de taak ontvangt.</span><span class="sxs-lookup"><span data-stu-id="c9a25-190">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="c9a25-191">U kunt ook een taak object door sluizen naar `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="c9a25-191">You can also pipe a job object to `Receive-Job`.</span></span>

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

### <span data-ttu-id="c9a25-192">-Keep</span><span class="sxs-lookup"><span data-stu-id="c9a25-192">-Keep</span></span>

<span data-ttu-id="c9a25-193">Geeft aan dat deze cmdlet de geaggregeerde stream-gegevens in het systeem opslaat, zelfs nadat u ze hebt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-193">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="c9a25-194">Samengevoegde stroom gegevens worden standaard gewist na weer gave met `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="c9a25-194">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="c9a25-195">Als u de sessie sluit of als u de taak met de cmdlet verwijdert, `Remove-Job` worden ook geaggregeerde stroom gegevens verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c9a25-195">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

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

### <span data-ttu-id="c9a25-196">-Locatie</span><span class="sxs-lookup"><span data-stu-id="c9a25-196">-Location</span></span>

<span data-ttu-id="c9a25-197">Hiermee geeft u een matrix met locaties op.</span><span class="sxs-lookup"><span data-stu-id="c9a25-197">Specifies an array of locations.</span></span>
<span data-ttu-id="c9a25-198">Met deze cmdlet worden alleen de resultaten van taken op de opgegeven locaties opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9a25-198">This cmdlet gets only the results of jobs in the specified locations.</span></span>

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

### <span data-ttu-id="c9a25-199">-Name</span><span class="sxs-lookup"><span data-stu-id="c9a25-199">-Name</span></span>

<span data-ttu-id="c9a25-200">Hiermee geeft u een matrix met beschrijvende namen op.</span><span class="sxs-lookup"><span data-stu-id="c9a25-200">Specifies an array of friendly names.</span></span>
<span data-ttu-id="c9a25-201">Met deze cmdlet worden de resultaten opgehaald van taken met de opgegeven namen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-201">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="c9a25-202">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c9a25-202">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="c9a25-203">-Niet-terugkerend</span><span class="sxs-lookup"><span data-stu-id="c9a25-203">-NoRecurse</span></span>

<span data-ttu-id="c9a25-204">Geeft aan dat deze cmdlet alleen resultaten ophaalt van de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="c9a25-204">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="c9a25-205">`Receive-Job`De resultaten van alle onderliggende taken van de opgegeven taak worden standaard ook opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9a25-205">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

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

### <span data-ttu-id="c9a25-206">-Sessie</span><span class="sxs-lookup"><span data-stu-id="c9a25-206">-Session</span></span>

<span data-ttu-id="c9a25-207">Hiermee geeft u een matrix met sessies op.</span><span class="sxs-lookup"><span data-stu-id="c9a25-207">Specifies an array of sessions.</span></span>
<span data-ttu-id="c9a25-208">Met deze cmdlet worden de resultaten opgehaald van taken die zijn uitgevoerd in de opgegeven Power shell-sessie (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="c9a25-208">This cmdlet gets the results of jobs that were run in the specified PowerShell session (**PSSession**).</span></span>
<span data-ttu-id="c9a25-209">Voer een variabele in die de **PSSession** bevat of een opdracht die de **PSSession**, zoals een opdracht, ophalen `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c9a25-209">Enter a variable that contains the **PSSession** or a command that gets the **PSSession**, such as a `Get-PSSession` command.</span></span>

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

### <span data-ttu-id="c9a25-210">-Wachten</span><span class="sxs-lookup"><span data-stu-id="c9a25-210">-Wait</span></span>

<span data-ttu-id="c9a25-211">Geeft aan dat deze cmdlet de opdracht prompt onderdrukt totdat alle taak resultaten zijn ontvangen.</span><span class="sxs-lookup"><span data-stu-id="c9a25-211">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="c9a25-212">Standaard `Receive-Job` retourneert onmiddellijk de beschik bare resultaten.</span><span class="sxs-lookup"><span data-stu-id="c9a25-212">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="c9a25-213">Standaard wacht de **wait** -para meter totdat de taak een van de volgende statussen heeft:</span><span class="sxs-lookup"><span data-stu-id="c9a25-213">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="c9a25-214">Voltooid</span><span class="sxs-lookup"><span data-stu-id="c9a25-214">Completed</span></span>
- <span data-ttu-id="c9a25-215">Mislukt</span><span class="sxs-lookup"><span data-stu-id="c9a25-215">Failed</span></span>
- <span data-ttu-id="c9a25-216">Gestopt</span><span class="sxs-lookup"><span data-stu-id="c9a25-216">Stopped</span></span>
- <span data-ttu-id="c9a25-217">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="c9a25-217">Suspended</span></span>
- <span data-ttu-id="c9a25-218">Verbroken.</span><span class="sxs-lookup"><span data-stu-id="c9a25-218">Disconnected.</span></span>

<span data-ttu-id="c9a25-219">Als u de **wait** -para meter wilt blijven wachten als de taak status onderbroken of losgekoppeld is, gebruikt u de para meter **Force** in combi natie met de para meter **wait** .</span><span class="sxs-lookup"><span data-stu-id="c9a25-219">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="c9a25-220">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c9a25-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c9a25-221">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="c9a25-221">-WriteEvents</span></span>

<span data-ttu-id="c9a25-222">Geeft aan dat deze cmdlet wijzigingen in de taak status rapporteert terwijl de taak kan worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="c9a25-222">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="c9a25-223">Deze para meter is alleen geldig als de **wait** -para meter wordt gebruikt in de opdracht en de **Keep** -para meter wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="c9a25-223">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="c9a25-224">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c9a25-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c9a25-225">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="c9a25-225">-WriteJobInResults</span></span>

<span data-ttu-id="c9a25-226">Geeft aan dat deze cmdlet het taak object retourneert, gevolgd door de resultaten.</span><span class="sxs-lookup"><span data-stu-id="c9a25-226">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="c9a25-227">Deze para meter is alleen geldig als de **wait** -para meter wordt gebruikt in de opdracht en de **Keep** -para meter wordt wegge laten.</span><span class="sxs-lookup"><span data-stu-id="c9a25-227">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="c9a25-228">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c9a25-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c9a25-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c9a25-229">CommonParameters</span></span>

<span data-ttu-id="c9a25-230">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c9a25-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c9a25-231">Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9a25-231">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c9a25-232">INVOER</span><span class="sxs-lookup"><span data-stu-id="c9a25-232">INPUTS</span></span>

### <span data-ttu-id="c9a25-233">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="c9a25-233">System.Management.Automation.Job</span></span>

<span data-ttu-id="c9a25-234">U kunt taak objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9a25-234">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="c9a25-235">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c9a25-235">OUTPUTS</span></span>

### <span data-ttu-id="c9a25-236">PSObject</span><span class="sxs-lookup"><span data-stu-id="c9a25-236">PSObject</span></span>

<span data-ttu-id="c9a25-237">Met deze cmdlet worden de resultaten van de opdrachten in de taak geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c9a25-237">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="c9a25-238">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c9a25-238">NOTES</span></span>

## <span data-ttu-id="c9a25-239">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c9a25-239">RELATED LINKS</span></span>

[<span data-ttu-id="c9a25-240">Get-job</span><span class="sxs-lookup"><span data-stu-id="c9a25-240">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="c9a25-241">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="c9a25-241">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="c9a25-242">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="c9a25-242">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="c9a25-243">Begin taak</span><span class="sxs-lookup"><span data-stu-id="c9a25-243">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="c9a25-244">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="c9a25-244">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="c9a25-245">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="c9a25-245">Wait-Job</span></span>](Wait-Job.md)

