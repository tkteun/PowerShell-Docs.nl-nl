---
ms.date: 09/13/2016
ms.topic: reference
title: Taken ondersteunen
description: Taken ondersteunen
ms.openlocfilehash: d755093e941aa660032f8d283cb43ba5eeec8c4b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666974"
---
# <a name="how-to-support-jobs"></a><span data-ttu-id="beda9-103">Taken ondersteunen</span><span class="sxs-lookup"><span data-stu-id="beda9-103">How to Support Jobs</span></span>

<span data-ttu-id="beda9-104">In dit voor beeld ziet u hoe u taken kunt ondersteunen wanneer u cmdlets schrijft.</span><span class="sxs-lookup"><span data-stu-id="beda9-104">This example shows how to support jobs when you write cmdlets.</span></span> <span data-ttu-id="beda9-105">Als u wilt dat gebruikers uw cmdlet als een achtergrond taak uitvoeren, moet u de code die in de volgende procedure wordt beschreven, toevoegen.</span><span class="sxs-lookup"><span data-stu-id="beda9-105">If you want users to run your cmdlet as a background job, you must include the code described in the following procedure.</span></span> <span data-ttu-id="beda9-106">Zie [achtergrond taken](./background-jobs.md)voor meer informatie over achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="beda9-106">For more information about background jobs, see [Background Jobs](./background-jobs.md).</span></span>

## <a name="to-support-jobs"></a><span data-ttu-id="beda9-107">Om taken te ondersteunen</span><span class="sxs-lookup"><span data-stu-id="beda9-107">To support jobs</span></span>

1. <span data-ttu-id="beda9-108">Definieer een `AsJob` Switch parameter zodat de gebruiker kan bepalen of de cmdlet moet worden uitgevoerd als een taak.</span><span class="sxs-lookup"><span data-stu-id="beda9-108">Define an `AsJob` switch parameter so that the user can decide whether to run the cmdlet as a job.</span></span>

    <span data-ttu-id="beda9-109">In het volgende voor beeld wordt een AsJob-parameter declaratie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="beda9-109">The following example shows an AsJob parameter declaration.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06AsJobParam](msh_samplesGetProc06#GetProc06AsJobParam)]  -->

2. <span data-ttu-id="beda9-110">Maak een-object dat is afgeleid van de klasse [System. Management. Automation. Job](/dotnet/api/System.Management.Automation.Job) .</span><span class="sxs-lookup"><span data-stu-id="beda9-110">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="beda9-111">Dit object kan een aangepast taak object zijn of een van de taak objecten van Windows Power shell, zoals een [System. Management. Automation. Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) -object.</span><span class="sxs-lookup"><span data-stu-id="beda9-111">This object can be a custom job object or one of the job objects provided by Windows PowerShell, such a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

    <span data-ttu-id="beda9-112">In het volgende voor beeld ziet u een aangepast taak object.</span><span class="sxs-lookup"><span data-stu-id="beda9-112">The following example shows a custom job object.</span></span>

    ```csharp
    private SampleJob job = new SampleJob("Get-ProcAsJob");
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobObject](msh_samplesGetProc06#GetProc06JobObject)]  -->

3. <span data-ttu-id="beda9-113">Voeg in een methode voor het verwerken van records een `if` instructie toe om te detecteren of de cmdlet moet worden uitgevoerd als een taak.</span><span class="sxs-lookup"><span data-stu-id="beda9-113">In a record processing method, add an `if` statement to detect whether the cmdlet should run as a job.</span></span> <span data-ttu-id="beda9-114">De volgende code maakt gebruik van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="beda9-114">The following code uses the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

    ```csharp
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06ProcessRecord](msh_samplesGetProc06#GetProc06ProcessRecord)]  -->

4. <span data-ttu-id="beda9-115">Implementeer voor aangepaste taak objecten de taak klasse.</span><span class="sxs-lookup"><span data-stu-id="beda9-115">For custom job objects, implement the job class.</span></span>

    ```csharp
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06JobClass](msh_samplesGetProc06#GetProc06JobClass)]  -->

5. <span data-ttu-id="beda9-116">Als de cmdlet het werk uitvoert, roept u de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) aan om een proces object naar de pijp lijn te retour neren.</span><span class="sxs-lookup"><span data-stu-id="beda9-116">If the cmdlet performs the work, call the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method to return a process object to the pipeline.</span></span> <span data-ttu-id="beda9-117">Als het werk wordt uitgevoerd als een taak, voegt u een onderliggende taak toe aan de taak.</span><span class="sxs-lookup"><span data-stu-id="beda9-117">If the work is performed as a job, add child job to the job.</span></span>

    ```csharp
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
    ```

    <!-- TODO!!!: review snippet reference      [!CODE [msh_samplesGetProc06#GetProc06Output](msh_samplesGetProc06#GetProc06Output)]  -->

## <a name="example"></a><span data-ttu-id="beda9-118">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="beda9-118">Example</span></span>

<span data-ttu-id="beda9-119">De volgende voorbeeld code toont de code voor een **Get-proc-** cmdlet waarmee processen intern of met behulp van een achtergrond taak kunnen worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="beda9-119">The following sample code shows the code for a **Get-Proc** cmdlet that can retrieve processes internally or by using a background job.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;  // Windows PowerShell namespace.
using System.Threading;              // Thread pool namespace for posting work.
using System.Diagnostics;            // Diagnostics namespace for retrieving
                                     // process objects.

// This sample shows a cmdlet whose work can be done by the cmdlet or by using
// a background job. Background jobs are executed in their own thread,
// independent of the pipeline thread in which the cmdlet is executed.
//
// To load this cmdlet, create a module folder and copy the GetProcessSample06.dll
// assembly into the module folder. Make sure that the path to the module folder
// is added to the $PSModulePath environment variable.
// Module folder path:
//    user/documents/WindowsPowerShell/modules/GetProcessSample06
//
// To import the module, run the following command: Import-Module GetProcessSample06.
// To test the cmdlet, run the following command: Get-Proc -name <process name>
//

//
namespace Microsoft.Samples.PowerShell.Commands
{
  /// <summary>
  ///  This cmdlet retrieves process internally or returns
  ///  a job that retrieves the processes.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public sealed class GetProcCommand : PSCmdlet
  {

    #region Parameters
    /// <summary>
    /// Specify the Name parameter. This parameter accepts
    /// process names from the command line.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    /// <summary>
    /// Specify the AsJob parameter. This parameter indicates
    /// whether the cmdlet should retrieve the processes internally
    /// or return a Job object that retrieves the processes.
    [Parameter()]
    public SwitchParameter AsJob
    {
      get { return asjob; }
      set { asjob = value; }
    }
    private bool asjob;

    #endregion Parameters

    #region Cmdlet Overrides

    // Create a custom job object.
    private SampleJob job = new SampleJob("Get-ProcAsJob");

    /// <summary>
    /// Determines if the processes should be retrieved
    /// internally or if a Job object should be returned.
    /// </summary>
    protected override void ProcessRecord()
    {
      if (asjob)
      {
        // Add the job definition to the job repository,
        // return the job object, and then create the thread
        // used to run the job.
        JobRepository.Add(job);
        WriteObject(job);
        ThreadPool.QueueUserWorkItem(WorkItem);
      }
      else
      {
        job.ProcessJob();
        foreach (PSObject p in job.Output)
        {
          WriteObject(p);
        }
      }
    }
    #endregion Overrides

    // Implement a custom job that derives
    // from the System.Management.Automation.Job class.
    private class SampleJob : Job
    {
      internal SampleJob(string command)
          : base(command)
      {
        SetJobState(JobState.NotStarted);
      }
      public override string StatusMessage
      {
        get { throw new NotImplementedException(); }
      }

      public override bool HasMoreData
      {
        get
        {
          return hasMoreData;
        }
      }
      private bool hasMoreData = true;

      public override string Location
      {
        get { throw new NotImplementedException(); }
      }

      public override void StopJob()
      {
        throw new NotImplementedException();
      }

      internal void ProcessJob()
      {
        SetJobState(JobState.Running);
        DoProcessLogic();
        SetJobState(JobState.Completed);
      }

      // Retrieve the processes of the local computer.
      void DoProcessLogic()
      {
        Process[] p = Process.GetProcesses();

        foreach (Process pl in p)
        {
          Output.Add(PSObject.AsPSObject(pl));
        }
        Output.Complete();
      } // End DoProcessLogic.
    } // End SampleJob class.

    void WorkItem(object dummy)
    {
       job.ProcessJob();
    }

    // Display the results of the work. If not a job,
    // process objects are returned. If a job, the
    // output is added to the job as a child job.
    void DoProcessLogic(bool asJob)
    {
      Process[] p = Process.GetProcesses();

      foreach (Process pl in p)
      {
        if (!asjob)
        {
          WriteObject(pl);
        }
        else
        {
          job.ChildJobs[0].Output.Add(new PSObject(pl));
        }
      }
    } // End DoProcessLogic.
  } //End GetProcCommand
}
```

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesGetProc06#GetProc06All](msh_samplesGetProc06#GetProc06All)]  -->
