---
title: GetProcessSample03-voor beeld | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 09df93792ab611e167279bc35755d8d6c28e7cf3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784211"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="0597c-102">Voorbeeld GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="0597c-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="0597c-103">In dit voor beeld ziet u hoe u een cmdlet implementeert waarmee de processen op de lokale computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0597c-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="0597c-104">Het bevat een `Name` para meter die een object van de pijp lijn kan accepteren of een waarde van een eigenschap van een object waarvan de naam van de eigenschap gelijk is aan de naam van de para meter.</span><span class="sxs-lookup"><span data-stu-id="0597c-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="0597c-105">Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet die wordt meegeleverd met Windows Power shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="0597c-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="0597c-106">Het voor beeld maken met Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0597c-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="0597c-107">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="0597c-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="0597c-108">De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="0597c-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="0597c-109">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="0597c-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="0597c-110">Hiermee opent u het voorbeeld project in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0597c-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="0597c-111">Selecteer in het menu **Build** de optie **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="0597c-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="0597c-112">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="0597c-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="0597c-113">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="0597c-113">How to run the sample</span></span>

1. <span data-ttu-id="0597c-114">Maak de volgende module map:</span><span class="sxs-lookup"><span data-stu-id="0597c-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="0597c-115">Kopieer de voor beeld-assembly naar de module map.</span><span class="sxs-lookup"><span data-stu-id="0597c-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="0597c-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0597c-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="0597c-117">Voer de volgende opdracht uit om de assembly in Windows Power shell te laden:</span><span class="sxs-lookup"><span data-stu-id="0597c-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="0597c-118">Voer de volgende opdracht uit om de cmdlet uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="0597c-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="0597c-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0597c-119">Requirements</span></span>

<span data-ttu-id="0597c-120">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="0597c-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0597c-121">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="0597c-121">Demonstrates</span></span>

<span data-ttu-id="0597c-122">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="0597c-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0597c-123">Het declareren van een cmdlet-klasse met het cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="0597c-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="0597c-124">Declareer een cmdlet-para meter met het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="0597c-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="0597c-125">De positie van de para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="0597c-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="0597c-126">Opgeven dat de para meter invoer van de pijp lijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0597c-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="0597c-127">De invoer kan worden gemaakt op basis van een object of een waarde van een eigenschap van een object waarvan de naam van de eigenschap gelijk is aan de naam van de para meter.</span><span class="sxs-lookup"><span data-stu-id="0597c-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="0597c-128">Het declareren van een validatie kenmerk voor de parameter invoer.</span><span class="sxs-lookup"><span data-stu-id="0597c-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="0597c-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0597c-129">Example</span></span>

<span data-ttu-id="0597c-130">Dit voor beeld toont een implementatie van de cmdlet Get-proc die een `Name` para meter bevat die invoer van de pijp lijn accepteert.</span><span class="sxs-lookup"><span data-stu-id="0597c-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0597c-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0597c-131">See Also</span></span>

[<span data-ttu-id="0597c-132">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="0597c-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
