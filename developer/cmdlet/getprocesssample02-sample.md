---
title: Voorbeeld van GetProcessSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849509"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="88b89-102">Voorbeeld GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="88b89-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="88b89-103">Dit voorbeeld laat zien hoe u een cmdlet die worden opgehaald van de processen die op de lokale computer schrijft.</span><span class="sxs-lookup"><span data-stu-id="88b89-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="88b89-104">Het biedt een `Name` parameter die kan worden gebruikt om op te geven van de processen worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="88b89-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="88b89-105">Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet geleverd door Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="88b89-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="88b89-106">Over het bouwen van het voorbeeld met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88b89-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="88b89-107">Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="88b89-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="88b89-108">De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="88b89-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="88b89-109">Dubbelklik op het pictogram voor het oplossingsbestand (.sln).</span><span class="sxs-lookup"><span data-stu-id="88b89-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="88b89-110">Hiermee opent u het voorbeeldproject in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88b89-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="88b89-111">In de **bouwen** in het menu **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="88b89-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="88b89-112">De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.</span><span class="sxs-lookup"><span data-stu-id="88b89-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="88b89-113">Hoe u het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="88b89-113">How to run the sample</span></span>

1. <span data-ttu-id="88b89-114">Maak de volgende modulemap:</span><span class="sxs-lookup"><span data-stu-id="88b89-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="88b89-115">Kopieer de voorbeeld-assembly naar de modulemap.</span><span class="sxs-lookup"><span data-stu-id="88b89-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="88b89-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88b89-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="88b89-117">Voer de volgende opdracht om het laden van de assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="88b89-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="88b89-118">Voer de volgende opdracht om uit te voeren van de cmdlet:</span><span class="sxs-lookup"><span data-stu-id="88b89-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="88b89-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="88b89-119">Requirements</span></span>

<span data-ttu-id="88b89-120">In dit voorbeeld is Windows PowerShell 2.0 vereist.</span><span class="sxs-lookup"><span data-stu-id="88b89-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="88b89-121">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="88b89-121">Demonstrates</span></span>

<span data-ttu-id="88b89-122">In dit voorbeeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="88b89-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="88b89-123">Het declareren van een cmdlet-klasse met behulp van de Cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="88b89-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="88b89-124">Cmdlet-parameter met behulp van de Parameter-kenmerk declareren.</span><span class="sxs-lookup"><span data-stu-id="88b89-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="88b89-125">De positie van de parameter aangeeft.</span><span class="sxs-lookup"><span data-stu-id="88b89-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="88b89-126">Een kenmerk validatie voor de parameter invoer declareren.</span><span class="sxs-lookup"><span data-stu-id="88b89-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="88b89-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="88b89-127">Example</span></span>

<span data-ttu-id="88b89-128">In dit voorbeeld toont een implementatie van de cmdlet Get-Proc met een `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="88b89-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="88b89-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="88b89-129">See Also</span></span>

[<span data-ttu-id="88b89-130">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="88b89-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
