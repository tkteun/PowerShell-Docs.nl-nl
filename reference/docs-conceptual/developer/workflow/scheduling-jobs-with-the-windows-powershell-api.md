---
title: Taken plannen met de Windows Power shell-API | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64718f8e-de60-4fb7-894d-2975b5257ff6
caps.latest.revision: 4
ms.openlocfilehash: bdced961d91088dd75be347b7b74b22467c8c9be
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356635"
---
# <a name="scheduling-jobs-with-the-powershell-api"></a><span data-ttu-id="4a393-102">Taken plannen met de Power shell-API</span><span class="sxs-lookup"><span data-stu-id="4a393-102">Scheduling jobs with the PowerShell API</span></span>

<span data-ttu-id="4a393-103">U kunt de objecten die worden weer gegeven door de naam ruimte **micro soft. Power shell. ScheduledJob** gebruiken om het volgende te doen:</span><span class="sxs-lookup"><span data-stu-id="4a393-103">You can use the objects exposed by the **Microsoft.PowerShell.ScheduledJob** namespace to do the following:</span></span>

- <span data-ttu-id="4a393-104">Een geplande taak maken.</span><span class="sxs-lookup"><span data-stu-id="4a393-104">Create a scheduled job.</span></span>
- <span data-ttu-id="4a393-105">Definiëren wanneer de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4a393-105">Define when the job runs.</span></span>
- <span data-ttu-id="4a393-106">Resultaten van de voltooide taak ophalen.</span><span class="sxs-lookup"><span data-stu-id="4a393-106">Get results about the completed job.</span></span>

## <a name="triggering-the-job"></a><span data-ttu-id="4a393-107">De taak activeren</span><span class="sxs-lookup"><span data-stu-id="4a393-107">Triggering the job</span></span>

<span data-ttu-id="4a393-108">De eerste stap bij het maken van een geplande taak wordt opgegeven wanneer de taak moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4a393-108">The first step in creating a scheduled job is specifying when the job should run.</span></span> <span data-ttu-id="4a393-109">Doe dit door een **micro soft. Power shell. ScheduledJob. ScheduledJobTrigger** -object te maken en te configureren.</span><span class="sxs-lookup"><span data-stu-id="4a393-109">Do this by creating and configuring a **Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger** object.</span></span> <span data-ttu-id="4a393-110">Met de volgende code wordt een trigger gemaakt waarmee een taak wordt gepland om één keer 20 seconden in de toekomst uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4a393-110">The following code creates a trigger that schedules a job to run a single time 20 seconds in the future.</span></span>

```csharp
ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20), // Create trigger to start job in 20 seconds.
                    TimeSpan.Zero,               // No random delay
                    null,                        // No repetition interval time
                    null,                        // No repetition interval duration
                    1,                           // Trigger Id
                    true);                       // Create trigger enabled

```

## <a name="defining-the-job"></a><span data-ttu-id="4a393-111">De taak definiëren</span><span class="sxs-lookup"><span data-stu-id="4a393-111">Defining the job</span></span>

<span data-ttu-id="4a393-112">U definieert een Power shell-taak door een parameter woordenlijst te maken.</span><span class="sxs-lookup"><span data-stu-id="4a393-112">You define a PowerShell job by creating a parameter dictionary.</span></span> <span data-ttu-id="4a393-113">De volgende para meters worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="4a393-113">The following parameters are supported:</span></span>

|<span data-ttu-id="4a393-114">Parameternaam</span><span class="sxs-lookup"><span data-stu-id="4a393-114">Parameter Name</span></span>|<span data-ttu-id="4a393-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4a393-115">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="4a393-116">**Name**</span><span class="sxs-lookup"><span data-stu-id="4a393-116">**Name**</span></span>|<span data-ttu-id="4a393-117">De naam van de taak.</span><span class="sxs-lookup"><span data-stu-id="4a393-117">The name of the job.</span></span>|
|<span data-ttu-id="4a393-118">**ScriptBock**</span><span class="sxs-lookup"><span data-stu-id="4a393-118">**ScriptBock**</span></span>|<span data-ttu-id="4a393-119">Een Power shell-script blok dat aangeeft wat de taak doet.</span><span class="sxs-lookup"><span data-stu-id="4a393-119">A PowerShell script block that specifies what the job does.</span></span>|
|<span data-ttu-id="4a393-120">**Bestandspad**</span><span class="sxs-lookup"><span data-stu-id="4a393-120">**FilePath**</span></span>|<span data-ttu-id="4a393-121">Pad naar een bestand dat een Power shell-script blok bevat om op te geven wat de taak doet.</span><span class="sxs-lookup"><span data-stu-id="4a393-121">Path to a file that contains a PowerShell script block to specify what the job does.</span></span>|
|<span data-ttu-id="4a393-122">**InitializationScript**</span><span class="sxs-lookup"><span data-stu-id="4a393-122">**InitializationScript**</span></span>|<span data-ttu-id="4a393-123">Een Power shell-script blok dat de taak initialiseert.</span><span class="sxs-lookup"><span data-stu-id="4a393-123">A PowerShell script block that initializes the job.</span></span>|
|<span data-ttu-id="4a393-124">**Argument List**</span><span class="sxs-lookup"><span data-stu-id="4a393-124">**ArgumentList**</span></span>|<span data-ttu-id="4a393-125">Een matrix met objecten die argumenten opgeven die de taak in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="4a393-125">An array of objects that specify arguments that the job takes.</span></span>|
|<span data-ttu-id="4a393-126">**RunAs32**</span><span class="sxs-lookup"><span data-stu-id="4a393-126">**RunAs32**</span></span>|<span data-ttu-id="4a393-127">Een Booleaanse waarde die aangeeft of de taak moet worden uitgevoerd in een 32-bits proces.</span><span class="sxs-lookup"><span data-stu-id="4a393-127">A boolean value that specifies whether to run the job in a 32-bit process.</span></span>|

<span data-ttu-id="4a393-128">Met de volgende code wordt een parameter woordenboek object gemaakt en worden de **naam** -en **script Block** -para meters ingesteld.</span><span class="sxs-lookup"><span data-stu-id="4a393-128">The following code creates a parameter dictionary object and sets the **Name** and **ScriptBlock** parameters.</span></span>

```csharp
string schedJobDefName = "MySampleSchedJob";
  Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
  jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

  ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
  jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath
                                                    // is required.

```

## <a name="creating-the-invocation-and-job-definition-objects"></a><span data-ttu-id="4a393-129">De aanroep-en taak definitie objecten maken</span><span class="sxs-lookup"><span data-stu-id="4a393-129">Creating the invocation and job definition objects</span></span>

<span data-ttu-id="4a393-130">Vervolgens maakt u `ScheduledJobInvocationInfo` en `ScheduledJobDefinition` objecten om de taak uit te voeren, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="4a393-130">You then create `ScheduledJobInvocationInfo` and `ScheduledJobDefinition` objects to run the job as shown in the following example:</span></span>

```csharp
ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
    jobDefParameters);

    schedJobDefinition = new ScheduledJobDefinition(
    jobInvocationInfo,                          // Defines the PowerShell job to run.
    new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the PowerShell job.
    null,                                       // No custom options. We accept default.
    null);                                      // No credentials. PowerShell job is run
                                                // in default Task Scheduler process, account.

```

## <a name="registering-the-job-with-the-task-scheduler"></a><span data-ttu-id="4a393-131">De taak registreren bij de taak planner</span><span class="sxs-lookup"><span data-stu-id="4a393-131">Registering the job with the task scheduler</span></span>

<span data-ttu-id="4a393-132">Met de volgende code wordt de taak geregistreerd bij de [Windows-taak planner](https://go.microsoft.com/fwlink/?LinkId=251817).</span><span class="sxs-lookup"><span data-stu-id="4a393-132">The following code registers the job with the [Windows Task Scheduler](https://go.microsoft.com/fwlink/?LinkId=251817).</span></span>

```csharp
schedJobDefinition.Register();
    registrationSucceeded = true;
    Console.WriteLine("Scheduled job is registered. Waiting 30 seconds for it to run.");

```

## <a name="complete-code-example"></a><span data-ttu-id="4a393-133">Volledig code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="4a393-133">Complete code Example</span></span>

<span data-ttu-id="4a393-134">Hieronder ziet u het volledige code voorbeeld van waaruit de vorige fragmenten zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4a393-134">The following is the complete code example from which the previous snippets were taken.</span></span>

```csharp
using System;
using System.Threading;
using System.Collections.Generic;
using System.Management.Automation;             // PowerShell namespace.
using Microsoft.PowerShell.ScheduledJob;        // PowerShell ScheduledJob namespace.

namespace Microsoft.Samples.PowerShell.ScheduledJob
{
    /// <summary>
    /// This class contains the Main entry point for the application.
    /// </summary>
    public class ScheduledJobSample
    {
        /// <summary>
        /// This sample shows how to use the PowerShell ScheduledJob API to create
        /// a simple PowerShell scheduled job, register it with a trigger object
        /// that defines when the job will run and retrieve job run results from
        /// the job file store.
        /// </summary>
        /// <param name="args"></param>
        public static void Main(string[] args)
        {
            // ScheduledJobDefinition contains all elements of a PowerShell scheduled
            // job including the PowerShell job script or script file path, scheduling
            // triggers, and scheduling options.
            ScheduledJobDefinition schedJobDefinition = null;
            bool registrationSucceeded = false;

            try
            {
                // First create a scheduled job trigger object.  This object will
                // define when the PowerShell job is scheduled to run.  For this
                // example we will create a trigger to run the job just one time
                // 20 seconds after the trigger object is created.
                // Note: If you are stepping through this code in a debugger you
                // may want to increase the 20 seconds value so that the trigger time
                // remains in the future once you register the scheduled job.
                ScheduledJobTrigger jobTrigger = ScheduledJobTrigger.CreateOnceTrigger(
                    DateTime.Now.AddSeconds(20),      // Create trigger to start job in 20 seconds.
                    TimeSpan.Zero,                    // No random delay
                    null,                             // No repetition interval time
                    null,                             // No repetition interval duration
                    1,                                // Trigger Id
                    true);                            // Create trigger enabled

                // Create a parameter dictionary that defines the PowerShell job.
                // For this example we will create a simple script that runs for
                // 5 seconds generating output.
                // Here are the parameters supported to define the PowerShell job.
                // Name                 - Job name string.
                // ScriptBlock          - PowerShell ScriptBlock type.
                // FilePath             - PowerShell script file path string.
                // InitializationScript - PowerShell Scriptblock type.
                // ArgumentList         - object[] type.
                // RunAs32              - Switch (boolean type).
                string schedJobDefName = "MySampleSchedJob";
                Dictionary<string, object> jobDefParameters = new Dictionary<string, object>();
                jobDefParameters.Add("Name", schedJobDefName);      // Unique name is required.

                ScriptBlock scriptBlock = ScriptBlock.Create(@"1..5 | foreach {sleep 1; ""SchedJobOutput $_""}");
                jobDefParameters.Add("ScriptBlock", scriptBlock);  // A scriptblock or script FilePath is required.

                // Now create a JobInvocation object that contains all information about the PowerShell job to run.
                ScheduledJobInvocationInfo jobInvocationInfo = new ScheduledJobInvocationInfo(
                    new JobDefinition(typeof(ScheduledJobSourceAdapter), scriptBlock.ToString(), schedJobDefName),
                    jobDefParameters);

                // Finally create the scheduled job definition object that pulls all
                // of this information together.
                schedJobDefinition = new ScheduledJobDefinition(
                   jobInvocationInfo,                          // Defines the PowerShell job to run.
                   new ScheduledJobTrigger[1] { jobTrigger },  // Defines when to run the job.
                   null,                                       // No custom options. Accept default.
                   null);                                      // No credentials. PowerShell job is
                                                               // run in default Task Scheduler
                                                               // process, account.

                // Next we register this scheduled job object with Windows Task Scheduler.
                // The Task Scheduler runs the PowerShell script based on the provided job trigger.
                schedJobDefinition.Register();
                registrationSucceeded = true;
                Console.WriteLine("Scheduled job is registered. Waiting 30 seconds for it to run.");

                // You can see this PowerShell job task registered in the Task Scheduler UI.
                // Look under path:
                // Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs

                // Wait for Task Scheduler to run the PowerShell job.
                // This should happen in 20 seconds and then the job takes about 5 seconds to run.
                // If PowerShell job task doesn't run try increasing the trigger time in the
                // ScheduledJobTrigger object.
                // You can run this task manually from the Task Scheduler UI.
                for (int count = 1; count < 31; ++count)
                {
                    Thread.Sleep(1000);
                    Console.WriteLine(count + " seconds elapsed");
                }

                Console.WriteLine();
                Console.WriteLine("Job run results.");
                Console.WriteLine();

                // Since the PowerShell job runs in a non-interactive Task Scheduler
                // process the job status and output data is written to a file based
                // job store and the directory location is the current user local app
                // data ($env:LOCALAPPDATA).
                // This job store can be accessed through the ScheduledJobSourceAdapter class.
                ScheduledJobSourceAdapter schedJobSourceAdapter = new ScheduledJobSourceAdapter();
                IList<Job2> jobRuns = schedJobSourceAdapter.GetJobs();
                foreach (var jobRun in jobRuns)
                {
                    // Check for jobs in finished state.
                    // Note that job data is not written to the job store until the job
                    // has reached a finished state.
                    JobState jobState = jobRun.JobStateInfo.State;
                    if (jobState == JobState.Completed ||
                        jobState == JobState.Stopped ||
                        jobState == JobState.Failed)
                    {
                        // Write job run finished state.
                        Console.WriteLine("Job Status: " + jobRun.JobStateInfo.State);
                        Console.WriteLine();
                        Console.WriteLine("Job Data");

                        // Write output data.
                        foreach (var item in jobRun.Output)
                        {
                            Console.WriteLine(item.ToString());
                        }

                        // Write any errors.
                        foreach (var item in jobRun.Error)
                        {
                            Console.WriteLine(item.ToString());
                        }
                    }
                }

                Console.WriteLine();
                Console.WriteLine("Press any key to continue...");
                Console.ReadKey();
            }
            catch (ScheduledJobException e)
            {
                Console.WriteLine("Error: " + e.Message);
            }
            finally
            {
                // Unregister this scheduled job or an error will be thrown when
                // running this sample code again (scheduled job already exists.)
                // because all registered scheduled jobs must have a unique name.
                if (registrationSucceeded)
                {
                    schedJobDefinition.Remove(true);
                }
            }
        }
    }
}

```
