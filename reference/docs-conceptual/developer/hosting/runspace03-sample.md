---
title: Runspace03-voor beeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: 980c75b07e1c35b293d00e6f2bca828499b3bd28
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561015"
---
# <a name="runspace03-sample"></a><span data-ttu-id="0b1c3-102">Voorbeeld Runspace03</span><span class="sxs-lookup"><span data-stu-id="0b1c3-102">Runspace03 Sample</span></span>

<span data-ttu-id="0b1c3-103">In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om een script synchroon uit te voeren en niet-afsluit fouten te verwerken.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="0b1c3-104">Het script ontvangt een lijst met proces namen en haalt deze processen vervolgens op.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-104">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="0b1c3-105">De resultaten van het script, met inbegrip van eventuele niet-afsluit fouten die zijn gegenereerd bij het uitvoeren van het script, worden weer gegeven in een console venster.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-105">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="0b1c3-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0b1c3-106">Requirements</span></span>

<span data-ttu-id="0b1c3-107">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0b1c3-108">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="0b1c3-108">Demonstrates</span></span>

<span data-ttu-id="0b1c3-109">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0b1c3-110">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken om een script uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a script.</span></span>

- <span data-ttu-id="0b1c3-111">Een script toevoegen aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="0b1c3-111">Adding a script to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="0b1c3-112">Invoer objecten worden door gegeven aan het script vanuit het aanroepende programma.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-112">Passing input objects to the script from the calling program.</span></span>

- <span data-ttu-id="0b1c3-113">Het script wordt synchroon uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-113">Running the script synchronously.</span></span>

- <span data-ttu-id="0b1c3-114">Gebruik [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objecten om eigenschappen uit te pakken en weer te geven van de objecten die door het script worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the script.</span></span>

- <span data-ttu-id="0b1c3-115">Fout records ophalen en weer geven die zijn gegenereerd tijdens het uitvoeren van het script.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-115">Retrieving and displaying error records that were generated when the script was run.</span></span>

## <a name="example"></a><span data-ttu-id="0b1c3-116">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0b1c3-116">Example</span></span>

<span data-ttu-id="0b1c3-117">In dit voor beeld wordt een script synchroon uitgevoerd in de standaard runs Pace van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-117">This sample runs a script synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="0b1c3-118">De uitvoer van het script en eventuele niet-afgesloten fouten die zijn gegenereerd, worden weer gegeven in een console venster.</span><span class="sxs-lookup"><span data-stu-id="0b1c3-118">The output of the script and any non-terminating errors that were generated are displayed in a console window.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="0b1c3-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0b1c3-119">See Also</span></span>

[<span data-ttu-id="0b1c3-120">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="0b1c3-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
