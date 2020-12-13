---
ms.date: 09/13/2016
ms.topic: reference
title: Achtergrondtaken
description: Achtergrondtaken
ms.openlocfilehash: 5478789a2ee1f2eabc71a46673e3a707643cdba8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648613"
---
# <a name="background-jobs"></a><span data-ttu-id="a2e48-103">Achtergrondtaken</span><span class="sxs-lookup"><span data-stu-id="a2e48-103">Background Jobs</span></span>

<span data-ttu-id="a2e48-104">Cmdlets kunnen hun actie intern of als Windows Power shell-*achtergrond taak* uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a2e48-104">Cmdlets can perform their action internally or as a Windows PowerShell *background job*.</span></span> <span data-ttu-id="a2e48-105">Wanneer een cmdlet wordt uitgevoerd als een achtergrond taak, wordt het werk asynchroon uitgevoerd in een eigen thread, gescheiden van de pijplijn thread die de cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a2e48-105">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="a2e48-106">Wanneer een cmdlet wordt uitgevoerd als achtergrond taak, retourneert de opdracht prompt onmiddellijk, zelfs als de taak een lange tijd lang duurt om te worden voltooid, en de gebruiker kan zonder onderbreking door gaan terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a2e48-106">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="a2e48-107">Achtergrond taken, onderliggende taken en de taak opslagplaats</span><span class="sxs-lookup"><span data-stu-id="a2e48-107">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="a2e48-108">Het taak object dat wordt geretourneerd door de cmdlets die ondersteuning bieden voor achtergrond taken, definieert de taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-108">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="a2e48-109">(De cmdlet [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) retourneert ook een taak object.) De naam van de taak, een id die wordt gebruikt om de taak op te geven, de status informatie en de onderliggende taken zijn opgenomen in deze definitie.</span><span class="sxs-lookup"><span data-stu-id="a2e48-109">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="a2e48-110">De taak voert geen werk uit.</span><span class="sxs-lookup"><span data-stu-id="a2e48-110">The job does not perform any of the work.</span></span> <span data-ttu-id="a2e48-111">Elke achtergrond taak heeft ten minste één onderliggende taak omdat de onderliggende taak het werkelijke werk uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a2e48-111">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="a2e48-112">Wanneer u een cmdlet uitvoert zodat het werk wordt uitgevoerd als een achtergrond taak, moet de cmdlet de taak en de onderliggende taken toevoegen aan een algemene opslag plaats, waarnaar wordt verwezen als de *taak opslagplaats*.</span><span class="sxs-lookup"><span data-stu-id="a2e48-112">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="a2e48-113">Zie het volgende voor meer informatie over de manier waarop achtergrond taken worden verwerkt op de opdracht regel:</span><span class="sxs-lookup"><span data-stu-id="a2e48-113">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="a2e48-114">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="a2e48-114">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="a2e48-115">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="a2e48-115">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="a2e48-116">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="a2e48-116">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="a2e48-117">Een cmdlet schrijven die als achtergrond taak wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="a2e48-117">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="a2e48-118">Als u een cmdlet wilt schrijven die als achtergrond taak kan worden uitgevoerd, moet u de volgende taken uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="a2e48-118">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="a2e48-119">Definieer een `asJob` Switch parameter zodat de gebruiker kan bepalen of de cmdlet moet worden uitgevoerd als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-119">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="a2e48-120">Maak een-object dat is afgeleid van de klasse [System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) .</span><span class="sxs-lookup"><span data-stu-id="a2e48-120">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="a2e48-121">Dit object kan een aangepast taak object zijn of een taak object dat wordt meegeleverd met Windows Power shell, zoals een [System. Management. Automation. Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) -object.</span><span class="sxs-lookup"><span data-stu-id="a2e48-121">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="a2e48-122">Voeg in een methode voor het verwerken van records een `if` instructie toe die detecteert of de cmdlet moet worden uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-122">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="a2e48-123">Implementeer voor aangepaste taak objecten de taak klasse.</span><span class="sxs-lookup"><span data-stu-id="a2e48-123">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="a2e48-124">De juiste objecten retour neren, afhankelijk van het feit of de cmdlet wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-124">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="a2e48-125">Zie [taken ondersteunen](./how-to-support-jobs.md)voor een code voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="a2e48-125">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="a2e48-126">Api's voor achtergrond Job-Related</span><span class="sxs-lookup"><span data-stu-id="a2e48-126">Background Job-Related APIs</span></span>

<span data-ttu-id="a2e48-127">De volgende Api's worden verzorgd door Windows Power shell voor het beheren van achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="a2e48-127">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="a2e48-128">Met [System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) worden aangepaste taak objecten afgeleid.</span><span class="sxs-lookup"><span data-stu-id="a2e48-128">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="a2e48-129">Dit is een abstracte klasse.</span><span class="sxs-lookup"><span data-stu-id="a2e48-129">This is an abstract class.</span></span>

<span data-ttu-id="a2e48-130">[System. Management. Automation. Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) beheert en bevat informatie over de huidige actieve achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="a2e48-130">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="a2e48-131">[System. Management. Automation. Jobstate](/dotnet/api/System.Management.Automation.JobState) definieert de status van de achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-131">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="a2e48-132">Statussen zijn gestart, actief en gestopt.</span><span class="sxs-lookup"><span data-stu-id="a2e48-132">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="a2e48-133">[System. Management. Automation. Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) biedt informatie over de status van een achtergrond taak en, als de laatste status wijziging is veroorzaakt door een fout, de reden waarom de taak de huidige status heeft opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a2e48-133">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="a2e48-134">[System. Management. Automation. Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) biedt de argumenten voor een gebeurtenis die optreedt wanneer de status van een achtergrond taak wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a2e48-134">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="a2e48-135">Windows Power shell-taak-cmdlets</span><span class="sxs-lookup"><span data-stu-id="a2e48-135">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="a2e48-136">De volgende cmdlets worden verzorgd door Windows Power shell voor het beheren van achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="a2e48-136">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="a2e48-137">Get-job</span><span class="sxs-lookup"><span data-stu-id="a2e48-137">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="a2e48-138">Hiermee worden Windows Power shell-achtergrond taken opgehaald die worden uitgevoerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a2e48-138">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="a2e48-139">Receive-job</span><span class="sxs-lookup"><span data-stu-id="a2e48-139">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="a2e48-140">Hiermee worden de resultaten van de Windows Power shell-achtergrond taken in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a2e48-140">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="a2e48-141">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="a2e48-141">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="a2e48-142">Hiermee verwijdert u een Windows Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-142">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="a2e48-143">Begin taak</span><span class="sxs-lookup"><span data-stu-id="a2e48-143">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="a2e48-144">Start een Windows Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-144">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="a2e48-145">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="a2e48-145">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="a2e48-146">Hiermee stopt u een Windows Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="a2e48-146">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="a2e48-147">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="a2e48-147">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="a2e48-148">Onderdrukt de opdracht prompt totdat een of alle Windows Power shell-achtergrond taken die in de sessie worden uitgevoerd, zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="a2e48-148">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2e48-149">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a2e48-149">See Also</span></span>

[<span data-ttu-id="a2e48-150">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="a2e48-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
