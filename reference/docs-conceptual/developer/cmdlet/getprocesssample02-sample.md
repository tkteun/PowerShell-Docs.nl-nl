---
title: GetProcessSample02-voor beeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355620"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="2d4b5-102">Voorbeeld GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="2d4b5-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="2d4b5-103">In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="2d4b5-104">Het bevat een `Name`-para meter die kan worden gebruikt om de processen op te geven die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="2d4b5-105">Deze cmdlet is een vereenvoudigde versie van de `Get-Process`-cmdlet van Windows Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="2d4b5-106">Het voor beeld maken met Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="2d4b5-107">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="2d4b5-108">De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="2d4b5-109">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="2d4b5-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="2d4b5-110">Hiermee opent u het voorbeeld project in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="2d4b5-111">Selecteer in het menu **Build** de optie **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="2d4b5-112">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="2d4b5-113">Het voor beeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="2d4b5-113">How to run the sample</span></span>

1. <span data-ttu-id="2d4b5-114">Maak de volgende module map:</span><span class="sxs-lookup"><span data-stu-id="2d4b5-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="2d4b5-115">Kopieer de voor beeld-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="2d4b5-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="2d4b5-117">Voer de volgende opdracht uit om de assembly in Windows Power shell te laden:</span><span class="sxs-lookup"><span data-stu-id="2d4b5-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="2d4b5-118">Voer de volgende opdracht uit om de cmdlet uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="2d4b5-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="2d4b5-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2d4b5-119">Requirements</span></span>

<span data-ttu-id="2d4b5-120">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2d4b5-121">Laat zien</span><span class="sxs-lookup"><span data-stu-id="2d4b5-121">Demonstrates</span></span>

<span data-ttu-id="2d4b5-122">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="2d4b5-123">Het declareren van een cmdlet-klasse met het cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="2d4b5-124">Declareer een cmdlet-para meter met het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="2d4b5-125">De positie van de para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="2d4b5-126">Het declareren van een validatie kenmerk voor de parameter invoer.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="2d4b5-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2d4b5-127">Example</span></span>

<span data-ttu-id="2d4b5-128">In dit voor beeld ziet u een implementatie van de cmdlet Get-proc die een `Name`-para meter bevat.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="2d4b5-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2d4b5-129">See Also</span></span>

[<span data-ttu-id="2d4b5-130">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="2d4b5-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
