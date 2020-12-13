---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Runspace01
description: Voorbeeld Runspace01
ms.openlocfilehash: f47f79dd507db258119016353dc5a72d110d9252
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657910"
---
# <a name="runspace01-sample"></a><span data-ttu-id="3cab0-103">Voorbeeld Runspace01</span><span class="sxs-lookup"><span data-stu-id="3cab0-103">Runspace01 Sample</span></span>

<span data-ttu-id="3cab0-104">In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de [Get-process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3cab0-104">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="3cab0-105">De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten voor elk proces dat wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3cab0-105">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="3cab0-106">De waarden van de [systeem. Diagnostics. process. procesnaam \*](/dotnet/api/System.Diagnostics.Process.ProcessName) en [System. Diagnostics. process. Handlecount \*](/dotnet/api/System.Diagnostics.Process.Handlecount) -eigenschappen worden vervolgens geëxtraheerd uit de geretourneerde objecten en weer gegeven in een console venster.</span><span class="sxs-lookup"><span data-stu-id="3cab0-106">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cab0-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3cab0-107">Requirements</span></span>

 <span data-ttu-id="3cab0-108">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="3cab0-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3cab0-109">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="3cab0-109">Demonstrates</span></span>

- <span data-ttu-id="3cab0-110">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3cab0-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="3cab0-111">Een opdracht toevoegen aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="3cab0-111">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="3cab0-112">De opdracht synchroon uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="3cab0-112">Running the command synchronously.</span></span>

- <span data-ttu-id="3cab0-113">Met [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) objecten worden eigenschappen geëxtraheerd uit de objecten die zijn geretourneerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3cab0-113">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="3cab0-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3cab0-114">Example</span></span>

 <span data-ttu-id="3cab0-115">In dit voor beeld wordt de [Get-process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon uitgevoerd in de standaard runs Pace van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="3cab0-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="3cab0-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3cab0-116">See Also</span></span>
