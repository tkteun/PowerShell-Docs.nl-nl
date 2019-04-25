---
title: Voorbeeld van GetProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068042"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="aaa95-102">Voorbeeld GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="aaa95-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="aaa95-103">Dit voorbeeld laat zien hoe u voor het implementeren van een cmdlet die worden opgehaald van de processen die op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="aaa95-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="aaa95-104">Het biedt een `Name` parameter een object van de pijplijn of een waarde van een eigenschap van een object waarvan de de eigenschapsnaam hetzelfde als de parameternaam is kan accepteren.</span><span class="sxs-lookup"><span data-stu-id="aaa95-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="aaa95-105">Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet geleverd door Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="aaa95-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="aaa95-106">Over het bouwen van het voorbeeld met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aaa95-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="aaa95-107">Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="aaa95-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="aaa95-108">De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="aaa95-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="aaa95-109">Dubbelklik op het pictogram voor het oplossingsbestand (.sln).</span><span class="sxs-lookup"><span data-stu-id="aaa95-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="aaa95-110">Hiermee opent u het voorbeeldproject in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aaa95-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="aaa95-111">In de **bouwen** in het menu **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="aaa95-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="aaa95-112">De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.</span><span class="sxs-lookup"><span data-stu-id="aaa95-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="aaa95-113">Hoe u het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="aaa95-113">How to run the sample</span></span>

1. <span data-ttu-id="aaa95-114">Maak de volgende modulemap:</span><span class="sxs-lookup"><span data-stu-id="aaa95-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="aaa95-115">Kopieer de voorbeeld-assembly naar de modulemap.</span><span class="sxs-lookup"><span data-stu-id="aaa95-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="aaa95-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aaa95-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="aaa95-117">Voer de volgende opdracht om het laden van de assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="aaa95-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="aaa95-118">Voer de volgende opdracht om uit te voeren van de cmdlet:</span><span class="sxs-lookup"><span data-stu-id="aaa95-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="aaa95-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="aaa95-119">Requirements</span></span>

<span data-ttu-id="aaa95-120">In dit voorbeeld is Windows PowerShell 2.0 vereist.</span><span class="sxs-lookup"><span data-stu-id="aaa95-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="aaa95-121">Ziet u</span><span class="sxs-lookup"><span data-stu-id="aaa95-121">Demonstrates</span></span>

<span data-ttu-id="aaa95-122">In dit voorbeeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="aaa95-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="aaa95-123">Het declareren van een cmdlet-klasse met behulp van de Cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="aaa95-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="aaa95-124">Cmdlet-parameter met behulp van de Parameter-kenmerk declareren.</span><span class="sxs-lookup"><span data-stu-id="aaa95-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="aaa95-125">De positie van de parameter aangeeft.</span><span class="sxs-lookup"><span data-stu-id="aaa95-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="aaa95-126">Op te geven dat de parameter wordt de invoer van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="aaa95-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="aaa95-127">De invoer kan worden uitgevoerd van een object of een waarde van een eigenschap van een object waarvan de de eigenschapsnaam hetzelfde als de naam van de parameter is.</span><span class="sxs-lookup"><span data-stu-id="aaa95-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="aaa95-128">Een kenmerk validatie voor de parameter invoer declareren.</span><span class="sxs-lookup"><span data-stu-id="aaa95-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="aaa95-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="aaa95-129">Example</span></span>

<span data-ttu-id="aaa95-130">In dit voorbeeld toont een implementatie van de cmdlet Get-Proc met een `Name` parameter dat invoer van de pijplijn accepteert.</span><span class="sxs-lookup"><span data-stu-id="aaa95-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
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
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="aaa95-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="aaa95-131">See Also</span></span>

[<span data-ttu-id="aaa95-132">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="aaa95-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
