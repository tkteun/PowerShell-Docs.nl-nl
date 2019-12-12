---
title: GetProcessSample04-voor beeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356418"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="c2ef7-102">Voorbeeld GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="c2ef7-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="c2ef7-103">In dit voor beeld ziet u hoe u een cmdlet implementeert waarmee de processen op de lokale computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="c2ef7-104">Er wordt een niet-afsluit fout gegenereerd als er een fout optreedt tijdens het ophalen van een proces.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="c2ef7-105">Deze cmdlet is een vereenvoudigde versie van de `Get-Process`-cmdlet van Windows Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="c2ef7-106">Het voor beeld maken met Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="c2ef7-107">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="c2ef7-108">De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="c2ef7-109">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="c2ef7-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="c2ef7-110">Hiermee opent u het voorbeeld project in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="c2ef7-111">Selecteer in het menu **Build** de optie **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="c2ef7-112">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="c2ef7-113">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="c2ef7-113">How to run the sample</span></span>

1. <span data-ttu-id="c2ef7-114">Maak de volgende module map:</span><span class="sxs-lookup"><span data-stu-id="c2ef7-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="c2ef7-115">Kopieer de voor beeld-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="c2ef7-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="c2ef7-117">Voer de volgende opdracht uit om de assembly in Windows Power shell te laden:</span><span class="sxs-lookup"><span data-stu-id="c2ef7-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="c2ef7-118">Voer de volgende opdracht uit om de cmdlet uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="c2ef7-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="c2ef7-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c2ef7-119">Requirements</span></span>

<span data-ttu-id="c2ef7-120">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c2ef7-121">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="c2ef7-121">Demonstrates</span></span>

<span data-ttu-id="c2ef7-122">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="c2ef7-123">Het declareren van een cmdlet-klasse met het cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="c2ef7-124">Declareer een cmdlet-para meter met het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="c2ef7-125">De positie van de para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="c2ef7-126">Opgeven dat de para meter invoer van de pijp lijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="c2ef7-127">De invoer kan worden gemaakt op basis van een object of een waarde van een eigenschap van een object waarvan de naam van de eigenschap gelijk is aan de naam van de para meter.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="c2ef7-128">Het declareren van een validatie kenmerk voor de parameter invoer.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="c2ef7-129">Er wordt een niet-afsluit fout overgevuld en er wordt een fout bericht naar de fout stroom geschreven.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="c2ef7-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c2ef7-130">Example</span></span>

<span data-ttu-id="c2ef7-131">In dit voor beeld ziet u hoe u een cmdlet maakt waarmee niet-afsluit fouten worden verwerkt en fout berichten naar de fout stroom worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="c2ef7-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c2ef7-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c2ef7-132">See Also</span></span>

[<span data-ttu-id="c2ef7-133">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="c2ef7-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
