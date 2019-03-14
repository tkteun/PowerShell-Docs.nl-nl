---
title: Achtergrondtaken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794702"
---
# <a name="background-jobs"></a><span data-ttu-id="249ae-102">Achtergrondtaken</span><span class="sxs-lookup"><span data-stu-id="249ae-102">Background Jobs</span></span>

<span data-ttu-id="249ae-103">Cmdlets hun actie kunt uitvoeren, intern of als een Windows PowerShell*achtergrondtaak*.</span><span class="sxs-lookup"><span data-stu-id="249ae-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="249ae-104">Wanneer een cmdlet wordt uitgevoerd als achtergrondtaak, de bewerkingen worden asynchroon in een eigen thread gescheiden van de pijplijn-thread die door de cmdlet wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="249ae-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="249ae-105">Vanuit het gebruikersperspectief, wanneer een cmdlet wordt uitgevoerd als achtergrondtaak, retourneert de opdrachtprompt onmiddellijk, zelfs als de taak een uitgebreide hoeveelheid tijd in beslag neemt en de gebruikers zonder onderbreking houden toegang terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="249ae-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="249ae-106">Achtergrondtaken, onderliggende taken en de opslagplaats van de taak</span><span class="sxs-lookup"><span data-stu-id="249ae-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="249ae-107">Het taakobject dat wordt geretourneerd door de cmdlets die ondersteuning bieden voor achtergrondtaken definieert de taak.</span><span class="sxs-lookup"><span data-stu-id="249ae-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="249ae-108">(De [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet retourneert ook een taakobject.) De naam van de taak, een id die wordt gebruikt om op te geven van de taak, de informatie over de status en de onderliggende taken zijn opgenomen in deze definitie.</span><span class="sxs-lookup"><span data-stu-id="249ae-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="249ae-109">De taak uitvoeren niet een van de hoeveelheid werk.</span><span class="sxs-lookup"><span data-stu-id="249ae-109">The job does not perform any of the work.</span></span> <span data-ttu-id="249ae-110">Elke achtergrondtaak heeft ten minste één onderliggende taak, omdat de onderliggende taak het echte werk voert.</span><span class="sxs-lookup"><span data-stu-id="249ae-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="249ae-111">Wanneer u een cmdlet uitvoert, zodat het werk wordt uitgevoerd als achtergrondtaak, de cmdlet de taak en de onderliggende taken moet toevoegen aan een algemene opslagplaats, aangeduid als de *taak opslagplaats*.</span><span class="sxs-lookup"><span data-stu-id="249ae-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="249ae-112">Zie de volgende onderwerpen voor meer informatie over hoe achtergrondtaken worden verwerkt op de opdrachtregel:</span><span class="sxs-lookup"><span data-stu-id="249ae-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="249ae-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="249ae-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="249ae-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="249ae-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="249ae-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="249ae-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="249ae-116">Schrijven van een Cmdlet die wordt uitgevoerd als een achtergrondtaak</span><span class="sxs-lookup"><span data-stu-id="249ae-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="249ae-117">Voor het schrijven van een cmdlet die kan worden uitgevoerd als achtergrondtaak, moet u de volgende taken uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="249ae-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="249ae-118">Definieer een `asJob` overschakelen parameter zodat de gebruiker kunt vervolgens beslissen of de cmdlet uitvoeren als achtergrondtaak.</span><span class="sxs-lookup"><span data-stu-id="249ae-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="249ae-119">Maken van een object dat is afgeleid van de [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) klasse.</span><span class="sxs-lookup"><span data-stu-id="249ae-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="249ae-120">Dit object is een aangepaste taak of een taakobject dat is geleverd door Windows PowerShell, zoals een [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span><span class="sxs-lookup"><span data-stu-id="249ae-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="249ae-121">Een verwerkingsmethode voor de van de record, Voeg een `if` instructie waarmee wordt gedetecteerd of de cmdlet moet worden uitgevoerd als achtergrondtaak.</span><span class="sxs-lookup"><span data-stu-id="249ae-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="249ae-122">Voor taakobjecten van de aangepaste, de taakklasse te implementeren.</span><span class="sxs-lookup"><span data-stu-id="249ae-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="249ae-123">Retourneert de juiste objecten, afhankelijk van of de cmdlet wordt uitgevoerd als achtergrondtaak.</span><span class="sxs-lookup"><span data-stu-id="249ae-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="249ae-124">Zie voor een codevoorbeeld van [hoe ondersteuning taken](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="249ae-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="249ae-125">Achtergrond taakgerelateerde API 's</span><span class="sxs-lookup"><span data-stu-id="249ae-125">Background Job-Related APIs</span></span>

<span data-ttu-id="249ae-126">De volgende API's worden geleverd door Windows PowerShell voor het beheren van achtergrondtaken.</span><span class="sxs-lookup"><span data-stu-id="249ae-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="249ae-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) is afgeleid van aangepaste taakobjecten.</span><span class="sxs-lookup"><span data-stu-id="249ae-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="249ae-128">Dit is een abstracte klasse.</span><span class="sxs-lookup"><span data-stu-id="249ae-128">This is an abstract class.</span></span>

<span data-ttu-id="249ae-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Hiermee beheert u en bevat informatie over de huidige actieve achtergrondtaken.</span><span class="sxs-lookup"><span data-stu-id="249ae-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="249ae-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definieert de status van de achtergrondtaak.</span><span class="sxs-lookup"><span data-stu-id="249ae-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="249ae-131">Statussen zijn gestart, die wordt uitgevoerd en gestopt.</span><span class="sxs-lookup"><span data-stu-id="249ae-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="249ae-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) vindt u informatie over de status van een achtergrondtaak en, als de laatste status gewijzigd is veroorzaakt door een fout op de reden dat de taak hebt ingevoerd voor de huidige status.</span><span class="sxs-lookup"><span data-stu-id="249ae-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="249ae-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) biedt de argumenten voor een gebeurtenis die wordt gegenereerd wanneer de status van een achtergrondtaak wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="249ae-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="249ae-134">Windows PowerShell-taak-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="249ae-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="249ae-135">De volgende cmdlets worden geleverd door Windows PowerShell voor het beheren van achtergrondtaken.</span><span class="sxs-lookup"><span data-stu-id="249ae-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="249ae-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="249ae-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="249ae-137">Hiermee haalt u Windows PowerShell-achtergrondtaken die worden uitgevoerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="249ae-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="249ae-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="249ae-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="249ae-139">Hiermee haalt de resultaten van de Windows PowerShell-achtergrondtaken in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="249ae-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="249ae-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="249ae-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="249ae-141">Hiermee verwijdert u een achtergrondtaak van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="249ae-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="249ae-142">Taak starten</span><span class="sxs-lookup"><span data-stu-id="249ae-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="249ae-143">Start een achtergrondtaak van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="249ae-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="249ae-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="249ae-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="249ae-145">Hiermee stopt u een achtergrondtaak van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="249ae-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="249ae-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="249ae-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="249ae-147">Onderdrukt de opdrachtprompt totdat een of meer van de Windows PowerShell-achtergrondtaken die worden uitgevoerd in de sessie voltooid zijn.</span><span class="sxs-lookup"><span data-stu-id="249ae-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="249ae-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="249ae-148">See Also</span></span>

[<span data-ttu-id="249ae-149">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="249ae-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
