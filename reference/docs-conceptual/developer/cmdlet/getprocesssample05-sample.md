---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld GetProcessSample05
description: Voorbeeld GetProcessSample05
ms.openlocfilehash: d4bfaf52b00bb68cf11d8bbebf72487472d73f6e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646509"
---
# <a name="getprocesssample05-sample"></a><span data-ttu-id="3db1b-103">Voorbeeld GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="3db1b-103">GetProcessSample05 Sample</span></span>

<span data-ttu-id="3db1b-104">In dit voor beeld ziet u een volledige versie van de cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="3db1b-104">This sample shows a complete version of the Get-Proc cmdlet.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="3db1b-105">Het voor beeld maken met Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3db1b-105">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="3db1b-106">Open Windows Verkenner en navigeer naar de map GetProcessSample05 in de map Samples.</span><span class="sxs-lookup"><span data-stu-id="3db1b-106">Open Windows Explorer and navigate to the GetProcessSample05 directory under the Samples directory.</span></span>

   <span data-ttu-id="3db1b-107">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="3db1b-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample05 folder.</span></span> <span data-ttu-id="3db1b-108">De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span><span class="sxs-lookup"><span data-stu-id="3db1b-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample05.</span></span>

2. <span data-ttu-id="3db1b-109">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="3db1b-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="3db1b-110">Hiermee opent u het voorbeeld project in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3db1b-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="3db1b-111">Selecteer in het menu **Build** de optie **Build Solution** .</span><span class="sxs-lookup"><span data-stu-id="3db1b-111">In the **Build** menu, select **Build Solution** .</span></span>

   <span data-ttu-id="3db1b-112">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin en \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="3db1b-112">The library for the sample will be built in the default \bin or \bin\debug directories.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="3db1b-113">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="3db1b-113">How to run the sample</span></span>

1. <span data-ttu-id="3db1b-114">Maak de volgende module map:</span><span class="sxs-lookup"><span data-stu-id="3db1b-114">Create the following module folder:</span></span>

   `[user]/documents/windowspowershell/modules/GetProcessSample05`

2. <span data-ttu-id="3db1b-115">Kopieer de voor beeld-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="3db1b-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="3db1b-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3db1b-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="3db1b-117">Voer de volgende opdracht uit om de assembly in Windows Power shell te laden:</span><span class="sxs-lookup"><span data-stu-id="3db1b-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

   `Import-module getprossessample05`

5. <span data-ttu-id="3db1b-118">Voer de volgende opdracht uit om de cmdlet uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="3db1b-118">Run the following command to run the cmdlet:</span></span>

   `get-proc`

## <a name="requirements"></a><span data-ttu-id="3db1b-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3db1b-119">Requirements</span></span>

<span data-ttu-id="3db1b-120">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="3db1b-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3db1b-121">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="3db1b-121">Demonstrates</span></span>

<span data-ttu-id="3db1b-122">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="3db1b-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3db1b-123">Het declareren van een cmdlet-klasse met het cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="3db1b-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="3db1b-124">Declareer een cmdlet-para meter met het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="3db1b-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="3db1b-125">Posities opgeven voor para meters.</span><span class="sxs-lookup"><span data-stu-id="3db1b-125">Specifying positions for parameters.</span></span>

- <span data-ttu-id="3db1b-126">Opgeven dat para meters invoer van de pijp lijn kan overnemen.</span><span class="sxs-lookup"><span data-stu-id="3db1b-126">Specifying that parameters can take input from the pipeline.</span></span> <span data-ttu-id="3db1b-127">De invoer kan worden gemaakt op basis van een object of een waarde van een eigenschap van een object waarvan de naam van de eigenschap gelijk is aan de naam van de para meter.</span><span class="sxs-lookup"><span data-stu-id="3db1b-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="3db1b-128">Het declareren van een validatie kenmerk voor de parameter invoer.</span><span class="sxs-lookup"><span data-stu-id="3db1b-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="3db1b-129">Het afhandelen van fouten en uitzonde ringen.</span><span class="sxs-lookup"><span data-stu-id="3db1b-129">Handling errors and exceptions.</span></span>

- <span data-ttu-id="3db1b-130">Fout bij het schrijven van berichten.</span><span class="sxs-lookup"><span data-stu-id="3db1b-130">Writing debug messages.</span></span>

## <a name="example"></a><span data-ttu-id="3db1b-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3db1b-131">Example</span></span>

<span data-ttu-id="3db1b-132">In dit voor beeld ziet u hoe u een cmdlet maakt waarmee een lijst met opgegeven processen wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3db1b-132">This sample shows how to create a cmdlet that displays a list of specified processes.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Collections.Generic;
    using System.Diagnostics;
    using System.Management.Automation;    // Windows PowerShell namespace.
    using System.Security.Permissions;
    using Win32Exception = System.ComponentModel.Win32Exception;
    #region GetProcCommand

    /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc",
      DefaultParameterSetName = "ProcessName")]
   public class GetProcCommand : PSCmdlet
   {
       #region Fields
       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

       /// <summary>
       /// The identifiers of the processes to act on.
       /// </summary>
       private int[] processIds;

       /// <summary>
       /// The process objects to act on.
       /// </summary>
       private Process[] inputObjects;

       #endregion Fields

       #region Parameters

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ParameterSetName = "ProcessName",
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      /// <summary>
      /// Gets or sets the list of process identifiers on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         ParameterSetName = "Id",
         Mandatory = true,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true,
         HelpMessage = "The unique id of the process to get.")]
      public int[] Id
      {
         get { return this.processIds; }
         set { this.processIds = value; }
      }

      /// <summary>
      /// Gets or sets Process objects directly. If the input is a
      /// stream of [collection of] Process objects, the cmdlet bypasses the
      /// ProcessName and Id parameters and reads the Process objects
      /// directly.  This allows the cmdlet to deal with processes that have
      /// wildcard characters in their name.
      /// <value>Process objects</value>
      /// </summary>
      [Parameter(
         ParameterSetName = "InputObject",
         Mandatory = true,
         ValueFromPipeline = true)]
      public Process[] Input
      {
         get { return this.inputObjects; }
         set { this.inputObjects = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes. Then, the WriteObject
      /// method writes the associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         List<Process> matchingProcesses;

         WriteDebug("Obtaining the list of matching process objects.");

         switch (ParameterSetName)
         {
            case "Id":
               matchingProcesses = this.GetMatchingProcessesById();
               break;
            case "ProcessName":
               matchingProcesses = this.GetMatchingProcessesByName();
               break;
            case "InputObject":
               matchingProcesses = this.GetProcessesByInput();
               break;
            default:
               ThrowTerminatingError(
                   new ErrorRecord(
                       new ArgumentException("Bad ParameterSetName"),
                       "UnableToAccessProcessList",
                       ErrorCategory.InvalidOperation,
                       null));
               return;
         } // switch (ParameterSetName)

         WriteDebug("Outputting the matching process objects.");

         matchingProcesses.Sort(ProcessComparison);

         foreach (Process process in matchingProcesses)
         {
            WriteObject(process);
         }
      } // ProcessRecord

      #endregion Overrides

      #region protected Methods and Data

      /// <summary>
      /// Retrieves the list of all processes matching the ProcessName
      /// parameter and generates a nonterminating error for each
      /// specified process name which is not found even though the name
      /// contains no wildcards.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesByName()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> allProcesses =
            new List<Process>(Process.GetProcesses());

         // The keys dictionary is used for rapid lookup of
         // processes that are already in the matchingProcesses list.
         Dictionary<int, byte> keys = new Dictionary<int, byte>();

         List<Process> matchingProcesses = new List<Process>();

         if (null == this.processNames)
         {
             matchingProcesses.AddRange(allProcesses);
         }
         else
         {
             foreach (string pattern in this.processNames)
             {
                 WriteVerbose("Finding matches for process name \""
                    + pattern + "\".");

                 // WildCard search on the available processes
                 WildcardPattern wildcard =
                    new WildcardPattern(
                        pattern,
                        WildcardOptions.IgnoreCase);

                 bool found = false;

                 foreach (Process process in allProcesses)
                 {
                     if (!keys.ContainsKey(process.Id))
                     {
                         string processName = SafeGetProcessName(process);

                         // Remove the process from the allProcesses list
                         // so that it is not tested again.
                         if (processName.Length == 0)
                         {
                             allProcesses.Remove(process);
                         }

                         // Perform a wildcard search on this particular
                         // process name and check whether it matches the
                         // pattern specified.
                         if (!wildcard.IsMatch(processName))
                         {
                             continue;
                         }

                         WriteDebug("Found matching process id "
                            + process.Id + ".");

                         // A match is found.
                         found = true;

                         // Store the process identifier so that the same process
                         // is not added twice.
                         keys.Add(process.Id, 0);

                         // Add the process to the processes list.
                         matchingProcesses.Add(process);
                     }
                 } // foreach (Process...

                 if (!found &&
                   !WildcardPattern.ContainsWildcardCharacters(pattern))
                 {
                     WriteError(new ErrorRecord(
                        new ArgumentException("Cannot find process name "
                           + "\"" + pattern + "\"."),
                        "ProcessNameNotFound",
                        ErrorCategory.ObjectNotFound,
                        pattern));
                 }
             } // foreach (string...
         } // if (null...

         return matchingProcesses;
      } // GetMatchingProcessesByName

      /// <summary>
      /// Returns the name of a process.  If an error occurs, a blank
      /// string is returned.
      /// </summary>
      /// <param name="process">The process whose name is
      /// returned.</param>
      /// <returns>The name of the process.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand, Unrestricted = true)]
      protected static string SafeGetProcessName(Process process)
      {
         new EnvironmentPermission(PermissionState.Unrestricted).Assert();
         string name = String.Empty;

         if (process != null)
         {
            try
            {
                return process.ProcessName;
            }
            catch (Win32Exception)
            {
            }
            catch (InvalidOperationException)
            {
            }
         }

         return name;
     } // SafeGetProcessName

      #endregion Cmdlet Overrides

      #region Private Methods

      /// <summary>
      /// Function to sort by process name first, and then by
      /// the process identifier.
      /// </summary>
      /// <param name="x">First process object.</param>
      /// <param name="y">Second process object.</param>
      /// <returns>
      /// Returns less than zero if x is less than y,
      /// greater than 0 if x is greater than y, and 0 if x == y.
      /// </returns>
      private static int ProcessComparison(Process x, Process y)
      {
         int diff = String.Compare(
            SafeGetProcessName(x),
            SafeGetProcessName(y),
            StringComparison.CurrentCultureIgnoreCase);

         if (0 != diff)
         {
             return diff;
         }
         else
         {
             return x.Id.CompareTo(y.Id);
         }
      }

      /// <summary>
      /// Retrieves the list of all processes matching the Id
      /// parameter and generates a nonterminating error for
      /// each specified process identifier which is not found.
      /// </summary>
      /// <returns>
      /// An array of processes that match the given identifier.
      /// </returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetMatchingProcessesById()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.processIds)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (int processId in this.processIds)
            {
               WriteVerbose("Finding match for process id "
                  + processId + ".");

               if (!keys.ContainsKey(processId))
               {
                  Process process;
                  try
                  {
                      process = Process.GetProcessById(processId);
                  }
                  catch (ArgumentException ex)
                  {
                     WriteError(new ErrorRecord(
                        ex,
                        "ProcessIdNotFound",
                        ErrorCategory.ObjectNotFound,
                        processId));
                     continue;
                  }

                  WriteDebug("Found matching process.");

                  matchingProcesses.Add(process);
                  keys.Add(processId, 0);
               }
            }
         }

         return matchingProcesses;
      } // GetMatchingProcessesById

      /// <summary>
      /// Retrieves the list of all processes matching the InputObject
      /// parameter.
      /// </summary>
      /// <returns>The matching processes.</returns>
      [EnvironmentPermissionAttribute(
         SecurityAction.LinkDemand,
         Unrestricted = true)]
      private List<Process> GetProcessesByInput()
      {
         new EnvironmentPermission(
            PermissionState.Unrestricted).Assert();

         List<Process> matchingProcesses = new List<Process>();

         if (null != this.Input)
         {
            // The keys dictionary is used for rapid lookup of the
            // processes already in the matchingProcesses list.
            Dictionary<int, byte> keys = new Dictionary<int, byte>();

            foreach (Process process in this.Input)
            {
               WriteVerbose("Refreshing process object.");

               if (!keys.ContainsKey(process.Id))
               {
                  try
                  {
                      process.Refresh();
                  }
                  catch (Win32Exception)
                  {
                  }
                  catch (InvalidOperationException)
                  {
                  }

                  matchingProcesses.Add(process);
               }
            }
         }

         return matchingProcesses;
      } // GetProcessesByInput
      #endregion Private Methods
    } // End GetProcCommand class.

    #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="3db1b-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3db1b-133">See Also</span></span>

[<span data-ttu-id="3db1b-134">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="3db1b-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
