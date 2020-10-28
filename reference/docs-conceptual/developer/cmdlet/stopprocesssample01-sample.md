---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld StopProcessSample01
description: Voorbeeld StopProcessSample01
ms.openlocfilehash: 9024f5c66330f3a1748c28b82e91b3915e956207
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660538"
---
# <a name="stopprocesssample01-sample"></a><span data-ttu-id="4fb3a-103">Voorbeeld StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="4fb3a-103">StopProcessSample01 Sample</span></span>

<span data-ttu-id="4fb3a-104">Dit voor beeld laat zien hoe u een cmdlet schrijft die feedback van de gebruiker vraagt voordat deze probeert een proces te stoppen, en hoe u een para meter implementeert die `PassThru` aangeeft dat de gebruiker de cmdlet een object wil laten retour neren.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-104">This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter indicating that the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="4fb3a-105">Deze cmdlet is vergelijkbaar met de `Stop-Process` cmdlet van Windows Power shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-105">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="4fb3a-106">Het voor beeld maken met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="4fb3a-107">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map StopProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-107">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample01 folder.</span></span> <span data-ttu-id="4fb3a-108">De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span></span>

2. <span data-ttu-id="4fb3a-109">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="4fb3a-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="4fb3a-110">Hiermee opent u het voorbeeld project in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="4fb3a-111">Selecteer in het menu **Build** de optie **Build Solution** .</span><span class="sxs-lookup"><span data-stu-id="4fb3a-111">In the **Build** menu, select **Build Solution** .</span></span>

    <span data-ttu-id="4fb3a-112">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="4fb3a-113">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="4fb3a-113">How to run the sample</span></span>

1. <span data-ttu-id="4fb3a-114">Maak de volgende module map:</span><span class="sxs-lookup"><span data-stu-id="4fb3a-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. <span data-ttu-id="4fb3a-115">Kopieer de voor beeld-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="4fb3a-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="4fb3a-117">Voer de volgende opdracht uit om de assembly in Windows Power shell te laden:</span><span class="sxs-lookup"><span data-stu-id="4fb3a-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample01`

5. <span data-ttu-id="4fb3a-118">Voer de volgende opdracht uit om de cmdlet uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="4fb3a-118">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="4fb3a-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4fb3a-119">Requirements</span></span>

<span data-ttu-id="4fb3a-120">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4fb3a-121">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="4fb3a-121">Demonstrates</span></span>

<span data-ttu-id="4fb3a-122">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="4fb3a-123">Declareer een cmdlet-klasse met behulp van het cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-123">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="4fb3a-124">Het declareren van een cmdlet-para meter met behulp van het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-124">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="4fb3a-125">De methode ShouldProcess wordt aangeroepen om een bevestiging aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-125">Calling the ShouldProcess method to request confirmation.</span></span>

- <span data-ttu-id="4fb3a-126">Implementatie van een `PassThru` para meter die aangeeft of de gebruiker wil dat de cmdlet een object retourneert.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-126">Implementing a `PassThru` parameter that indicates if the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="4fb3a-127">Deze cmdlet retourneert standaard geen object naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-127">By default, this cmdlet does not return an object to the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="4fb3a-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="4fb3a-128">Example</span></span>

<span data-ttu-id="4fb3a-129">Dit voor beeld laat zien hoe u een `PassThru` para meter implementeert die aangeeft dat de gebruiker wil dat de cmdlet een object retourneert en hoe gebruikers feedback kan aanvragen door aanroepen naar de `ShouldProcess` `ShouldContinue` methoden en.</span><span class="sxs-lookup"><span data-stu-id="4fb3a-129">This sample shows how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object, and how to request user feedback by calls to the `ShouldProcess` and `ShouldContinue` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;    // Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
           get { return processNames; }
           set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.
               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,"UnableToAccessProcessByName",
                       ErrorCategory.InvalidOperation, name));

                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                      WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                           ErrorCategory.ReadError, process));
                      continue;
                   }

                   // Confirm the operation with the user first.
                   // This is always false if the WhatIf parameter is set.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,"{0} ({1})", processName,
                               process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that could possibly stop the computer.
                   bool criticalProcess =
                       criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess &&!force)
                   {
                       string message = String.Format
                           (CultureInfo.CurrentCulture,
                                "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                    processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                               ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                          (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                           ErrorCategory.CloseError, process));
                           continue;
                       } // if ((e is...
                       else throw;
                   } // catch

                   // If the PassThru parameter is
                   // specified, return the terminated process.
                   if (passThru)
                   {
                       WriteObject(process);
                   }
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="4fb3a-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4fb3a-130">See Also</span></span>

[<span data-ttu-id="4fb3a-131">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="4fb3a-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
