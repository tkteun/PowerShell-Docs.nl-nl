---
title: Voorbeeld van GetProcessSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068025"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="43f3b-102">Voorbeeld GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="43f3b-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="43f3b-103">Dit voorbeeld laat zien hoe u voor het implementeren van een cmdlet die worden opgehaald van de processen die op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="43f3b-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="43f3b-104">Er wordt een nonterminating fout gegenereerd als er een fout optreedt tijdens het ophalen van een proces.</span><span class="sxs-lookup"><span data-stu-id="43f3b-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="43f3b-105">Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet geleverd door Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="43f3b-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="43f3b-106">Over het bouwen van het voorbeeld met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43f3b-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="43f3b-107">Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="43f3b-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="43f3b-108">De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="43f3b-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="43f3b-109">Dubbelklik op het pictogram voor het oplossingsbestand (.sln).</span><span class="sxs-lookup"><span data-stu-id="43f3b-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="43f3b-110">Hiermee opent u het voorbeeldproject in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43f3b-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="43f3b-111">In de **bouwen** in het menu **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="43f3b-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="43f3b-112">De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.</span><span class="sxs-lookup"><span data-stu-id="43f3b-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="43f3b-113">Hoe u het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="43f3b-113">How to run the sample</span></span>

1. <span data-ttu-id="43f3b-114">Maak de volgende modulemap:</span><span class="sxs-lookup"><span data-stu-id="43f3b-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="43f3b-115">Kopieer de voorbeeld-assembly naar de modulemap.</span><span class="sxs-lookup"><span data-stu-id="43f3b-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="43f3b-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43f3b-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="43f3b-117">Voer de volgende opdracht om het laden van de assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="43f3b-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="43f3b-118">Voer de volgende opdracht om uit te voeren van de cmdlet:</span><span class="sxs-lookup"><span data-stu-id="43f3b-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="43f3b-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="43f3b-119">Requirements</span></span>

<span data-ttu-id="43f3b-120">In dit voorbeeld is Windows PowerShell 2.0 vereist.</span><span class="sxs-lookup"><span data-stu-id="43f3b-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="43f3b-121">Ziet u</span><span class="sxs-lookup"><span data-stu-id="43f3b-121">Demonstrates</span></span>

<span data-ttu-id="43f3b-122">In dit voorbeeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="43f3b-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="43f3b-123">Het declareren van een cmdlet-klasse met behulp van de Cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="43f3b-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="43f3b-124">Cmdlet-parameter met behulp van de Parameter-kenmerk declareren.</span><span class="sxs-lookup"><span data-stu-id="43f3b-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="43f3b-125">De positie van de parameter aangeeft.</span><span class="sxs-lookup"><span data-stu-id="43f3b-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="43f3b-126">Op te geven dat de parameter wordt de invoer van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="43f3b-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="43f3b-127">De invoer kan worden uitgevoerd van een object of een waarde van een eigenschap van een object waarvan de de eigenschapsnaam hetzelfde als de naam van de parameter is.</span><span class="sxs-lookup"><span data-stu-id="43f3b-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="43f3b-128">Een kenmerk validatie voor de parameter invoer declareren.</span><span class="sxs-lookup"><span data-stu-id="43f3b-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="43f3b-129">Een nonterminating fout overlapping van en schrijven van een foutbericht naar de foutstroom.</span><span class="sxs-lookup"><span data-stu-id="43f3b-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="43f3b-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="43f3b-130">Example</span></span>

<span data-ttu-id="43f3b-131">Dit voorbeeld laat zien hoe u een cmdlet die afsluitfouten worden verwerkt en foutberichten schrijft naar de foutstroom maakt.</span><span class="sxs-lookup"><span data-stu-id="43f3b-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="43f3b-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="43f3b-132">See Also</span></span>

[<span data-ttu-id="43f3b-133">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="43f3b-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
