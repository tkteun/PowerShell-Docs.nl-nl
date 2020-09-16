---
title: Voortgang weer geven tijdens meerdere threads
description: Het gebruik van schrijf voortgang over meerdere threads met foreach-object-parallel
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: 640646992955116def23d16dd12c221857d37b68
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2020
ms.locfileid: "89410839"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a><span data-ttu-id="f4ad3-103">Voortgang van het schrijven over meerdere threads met foreach parallel</span><span class="sxs-lookup"><span data-stu-id="f4ad3-103">Writing Progress across multiple threads with Foreach Parallel</span></span>

<span data-ttu-id="f4ad3-104">Vanaf Power shell 7,0 is de mogelijkheid om in meerdere threads tegelijk te werken mogelijk te maken met behulp van de **parallelle** para meter in de [foreach-object-](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-104">Starting in PowerShell 7.0, the ability to work in multiple threads simultaneously is possible using the **Parallel** parameter in the [Foreach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdlet.</span></span> <span data-ttu-id="f4ad3-105">Het bewaken van de voortgang van deze threads kan echter een uitdaging zijn.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-105">Monitoring the progress of these threads can be a challenge though.</span></span> <span data-ttu-id="f4ad3-106">Normaal gesp roken kunt u de voortgang van een proces bewaken met behulp van [schrijven](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).</span><span class="sxs-lookup"><span data-stu-id="f4ad3-106">Normally, you can monitor the progress of a process using [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).</span></span>
<span data-ttu-id="f4ad3-107">Omdat Power shell echter gebruikmaakt van een afzonderlijke runs Pace voor elke thread wanneer **parallelle**verbinding wordt gebruikt, is het rapporteren van de voortgang aan de host niet zo meteen als normaal gebruik van `Write-Progress` .</span><span class="sxs-lookup"><span data-stu-id="f4ad3-107">However, since PowerShell uses a separate runspace for each thread when using **Parallel**, reporting the progress back to the host isn't as straight forward as normal use of `Write-Progress`.</span></span>

## <a name="using-a-synced-hashtable-to-track-progress"></a><span data-ttu-id="f4ad3-108">Een gesynchroniseerde hashtabel gebruiken om de voortgang bij te houden</span><span class="sxs-lookup"><span data-stu-id="f4ad3-108">Using a synced hashtable to track progress</span></span>

<span data-ttu-id="f4ad3-109">Wanneer u de voortgang van meerdere threads schrijft, wordt het bijhouden lastig omdat bij het uitvoeren van parallelle processen in Power shell elk proces een eigen runs Pace heeft.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-109">When writing the progress from multiple threads, tracking becomes difficult because when running parallel processes in PowerShell, each process has it's own runspace.</span></span> <span data-ttu-id="f4ad3-110">U kunt dit doen door een [gesynchroniseerde hashtabel](/dotnet/api/system.collections.hashtable.synchronized)te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-110">To get around this, you can use a [synchronized hashtable](/dotnet/api/system.collections.hashtable.synchronized).</span></span> <span data-ttu-id="f4ad3-111">Een gesynchroniseerde hashtabel is een veilige gegevens structuur die door meerdere threads tegelijk kan worden gewijzigd zonder dat er een fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-111">A synced hashtable is a thread safe data structure that can be modified by multiple threads simultaneously without throwing an error.</span></span>

### <a name="set-up"></a><span data-ttu-id="f4ad3-112">Instellen</span><span class="sxs-lookup"><span data-stu-id="f4ad3-112">Set up</span></span>

<span data-ttu-id="f4ad3-113">Een van de verzekeringen van deze benadering is dat er een, even complexe set wordt gebruikt om ervoor te zorgen dat alles zonder fouten wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-113">One of the downsides to this approach is it takes a, somewhat, complex set up to ensure everything runs without error.</span></span>

```powershell
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)
```

<span data-ttu-id="f4ad3-114">In deze sectie worden drie verschillende gegevens structuren gemaakt, voor drie verschillende doel einden.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-114">This section creates three different data structures, for three different purposes.</span></span>

<span data-ttu-id="f4ad3-115">De `$dataSet` variabele bevat een matrix met hashtabellen die wordt gebruikt voor het coördineren van de volgende stappen zonder dat het risico wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-115">The `$dataSet` variable stores an array of hashtables that is used to coordinate the next steps without the risk of being modified.</span></span> <span data-ttu-id="f4ad3-116">Als een object verzameling wordt gewijzigd tijdens het sequentieel door de verzameling, genereert Power shell een fout.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-116">If an object collection is modified while iterating through the collection, PowerShell throws an error.</span></span> <span data-ttu-id="f4ad3-117">U moet de object verzameling in de lus gescheiden houden van de objecten die worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-117">You must keep the object collection in the loop separate from the objects being modified.</span></span> <span data-ttu-id="f4ad3-118">De `Id` sleutel in elke hashtabel is de id voor een model proces.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-118">The `Id` key in each hashtable is the identifier for a mock process.</span></span> <span data-ttu-id="f4ad3-119">De `Wait` sleutel simuleert de werk belasting van elk getraceerd proces.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-119">The `Wait` key simulates the workload of each mock process being tracked.</span></span>

<span data-ttu-id="f4ad3-120">`$origin`Met de variabele wordt een geneste hashtabel opgeslagen waarbij elke sleutel een van de proces-id van de model is.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-120">The `$origin` variable stores a nested hashtable with each key being one of the mock process id's.</span></span>
<span data-ttu-id="f4ad3-121">Vervolgens wordt deze gebruikt om de gesynchroniseerde hashtabel te laten ontdubbelt die is opgeslagen in de `$sync` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-121">Then, it is used to hydrate the synchronized hashtable stored in the `$sync` variable.</span></span> <span data-ttu-id="f4ad3-122">De `$sync` variabele is verantwoordelijk voor het rapporteren van de voortgang terug naar de bovenliggende runs Pace, waarin de voortgang wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-122">The `$sync` variable is responsible for reporting the progress back to the parent runspace, which displays the progress.</span></span>

### <a name="running-the-processes"></a><span data-ttu-id="f4ad3-123">De processen uitvoeren</span><span class="sxs-lookup"><span data-stu-id="f4ad3-123">Running the processes</span></span>

<span data-ttu-id="f4ad3-124">In deze sectie worden de processen met meerdere threads uitgevoerd en wordt een deel van de uitvoer gemaakt die wordt gebruikt om de voortgang weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-124">This section runs the multi-threaded processes and creates some of the output used to display progress.</span></span>

```powershell
$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}
```

<span data-ttu-id="f4ad3-125">De model processen worden verzonden naar `Foreach-Object` en gestart als taken.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-125">The mock processes are sent to `Foreach-Object` and started as jobs.</span></span> <span data-ttu-id="f4ad3-126">De **ThrottleLimit** is ingesteld op **3** om het uitvoeren van meerdere processen in een wachtrij te markeren.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-126">The **ThrottleLimit** is set to **3** to highlight running multiple processes in a queue.</span></span> <span data-ttu-id="f4ad3-127">De taken worden opgeslagen in de `$job` variabele en kunnen ons laten weten wanneer alle processen later zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-127">The jobs are stored in the `$job` variable and allows us to know when all the processes have finished later on.</span></span>

<span data-ttu-id="f4ad3-128">Wanneer u de- `using:` instructie gebruikt om te verwijzen naar een bovenliggende bereik variabele in Power shell, kunt u geen expressies gebruiken om deze dynamisch te maken.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-128">When using the `using:` statement to reference a parent scope variable in PowerShell, you can't use expressions to make it dynamic.</span></span> <span data-ttu-id="f4ad3-129">Als u bijvoorbeeld probeert de `$process` variabele als volgt te maken, wordt er `$process = $using:sync.$($PSItem.id)` een fout melding weer gegeven waarin u geen expressies kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-129">For example, if you tried to create the `$process` variable like this, `$process = $using:sync.$($PSItem.id)`, you would get an error stating you can't use expressions there.</span></span> <span data-ttu-id="f4ad3-130">Daarom maken we de `$syncCopy` variabele om de variabele te kunnen verwijzen en te wijzigen, `$sync` zonder het risico dat er een fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-130">So, we create the `$syncCopy` variable to be able to reference and modify the `$sync` variable without the risk of it failing.</span></span>

<span data-ttu-id="f4ad3-131">Vervolgens bouwen we een hashtabel op om de voortgang van het proces dat zich momenteel in de lus begeeft aan te geven met behulp `$process` van de variabele door te verwijzen naar de gesynchroniseerde hash-sleutels.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-131">Next, we build out a hashtable to represent the progress of the process currently in the loop using the `$process` variable by referencing the synchronized hashtable keys.</span></span> <span data-ttu-id="f4ad3-132">De **activiteit** en de **status** sleutels worden gebruikt als parameter waarden voor `Write-Progress` om de status van een bepaald model proces weer te geven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-132">The **Activity** and the **Status** keys are used as parameter values for `Write-Progress` to display the status of a given mock process in the next section.</span></span>

<span data-ttu-id="f4ad3-133">De `foreach` lus is een manier om te simuleren dat het proces werkt en dat wille keurig wordt gemaakt op basis van het `$dataSet` **wacht** kenmerk dat wordt ingesteld `Start-Sleep` met behulp van milliseconden.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-133">The `foreach` loop is just a way to simulate the process working and is randomized based on the `$dataSet` **Wait** attribute to set `Start-Sleep` using milliseconds.</span></span> <span data-ttu-id="f4ad3-134">Hoe u de voortgang van uw proces berekent, kan variëren.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-134">How you calculate the progress of your process may vary.</span></span>

### <a name="displaying-the-progress-of-multiple-processes"></a><span data-ttu-id="f4ad3-135">De voortgang van meerdere processen weer geven</span><span class="sxs-lookup"><span data-stu-id="f4ad3-135">Displaying the progress of multiple processes</span></span>

<span data-ttu-id="f4ad3-136">Nu de Modeler-processen worden uitgevoerd als taken, kunnen we de voortgang van processen in het Power shell-venster gaan schrijven.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-136">Now that the mock processes are running as jobs, we can start to write the processes progress to the PowerShell window.</span></span>

```powershell
while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

<span data-ttu-id="f4ad3-137">De `$job` variabele bevat de bovenliggende **taak** en heeft een onderliggende **taak** voor elk van de model processen.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-137">The `$job` variable contains the parent **job** and has a child **job** for each of the mock processes.</span></span> <span data-ttu-id="f4ad3-138">Terwijl een van de onderliggende taken nog steeds wordt uitgevoerd, blijft de **status** van de bovenliggende taak actief.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-138">While any of the child jobs are still running, the parent job **State** will remain "Running".</span></span> <span data-ttu-id="f4ad3-139">Hierdoor kunnen we de lus gebruiken `while` om de voortgang van elk proces continu bij te werken totdat alle processen zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-139">This allows us to use the `while` loop to continually update the progress of every process until all processes are finished.</span></span>

<span data-ttu-id="f4ad3-140">In de lus while worden alle sleutels in de variabele door lopen `$sync` .</span><span class="sxs-lookup"><span data-stu-id="f4ad3-140">Within the while loop, we loop through each of the keys in the `$sync` variable.</span></span> <span data-ttu-id="f4ad3-141">Aangezien dit een gesynchroniseerde hashtabel is, wordt deze voortdurend bijgewerkt, maar kan deze nog steeds worden gebruikt zonder dat er fouten optreden.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-141">Since this is a synchronized hashtable, it is constantly updated but can still be accessed without throwing any errors.</span></span>

<span data-ttu-id="f4ad3-142">Er wordt gecontroleerd of het proces dat wordt gerapporteerd, daad werkelijk wordt uitgevoerd met behulp van de- `IsNullOrEmpty()` methode.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-142">There is a check to ensure that the process being reported is actually running using the `IsNullOrEmpty()` method.</span></span> <span data-ttu-id="f4ad3-143">Als het proces niet is gestart, wordt de lus niet op de lijst gerapporteerd en gaat u verder met de volgende stap totdat het proces wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="f4ad3-143">If the process hasn't been started, the loop won't report on it and move on to the next until it gets to a process that has been started.</span></span> <span data-ttu-id="f4ad3-144">Als het proces wordt gestart, wordt de hashtabel van de huidige sleutel gebruikt voor het splat van de para meters voor `Write-Progress` .</span><span class="sxs-lookup"><span data-stu-id="f4ad3-144">If the process is started, the hashtable from the current key is used to splat the parameters to `Write-Progress`.</span></span>

### <a name="full-example"></a><span data-ttu-id="f4ad3-145">Volledig voor beeld</span><span class="sxs-lookup"><span data-stu-id="f4ad3-145">Full example</span></span>

```powershell
# Example workload
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)

$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}

while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

## <a name="related-links"></a><span data-ttu-id="f4ad3-146">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="f4ad3-146">Related Links</span></span>

- [<span data-ttu-id="f4ad3-147">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f4ad3-147">about_Jobs</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [<span data-ttu-id="f4ad3-148">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f4ad3-148">about_Scopes</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [<span data-ttu-id="f4ad3-149">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="f4ad3-149">about_Splatting</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
