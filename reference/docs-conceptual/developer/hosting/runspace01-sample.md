---
title: Runspace01-voor beeld | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ac286512f3cb3b97a6b3179c9dd45f1fefe1ecf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772192"
---
# <a name="runspace01-sample"></a><span data-ttu-id="d6c84-102">Voorbeeld Runspace01</span><span class="sxs-lookup"><span data-stu-id="d6c84-102">Runspace01 Sample</span></span>

<span data-ttu-id="d6c84-103">In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de [Get-process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d6c84-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="d6c84-104">De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten voor elk proces dat wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d6c84-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="d6c84-105">De waarden van de [systeem. Diagnostics. process. procesnaam \*](/dotnet/api/System.Diagnostics.Process.ProcessName) en [System. Diagnostics. process. Handlecount \*](/dotnet/api/System.Diagnostics.Process.Handlecount) -eigenschappen worden vervolgens geëxtraheerd uit de geretourneerde objecten en weer gegeven in een console venster.</span><span class="sxs-lookup"><span data-stu-id="d6c84-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6c84-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d6c84-106">Requirements</span></span>

 <span data-ttu-id="d6c84-107">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="d6c84-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d6c84-108">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="d6c84-108">Demonstrates</span></span>

- <span data-ttu-id="d6c84-109">Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken om een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d6c84-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="d6c84-110">Een opdracht toevoegen aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="d6c84-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="d6c84-111">De opdracht synchroon uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d6c84-111">Running the command synchronously.</span></span>

- <span data-ttu-id="d6c84-112">Met [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) objecten worden eigenschappen geëxtraheerd uit de objecten die zijn geretourneerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d6c84-112">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="d6c84-113">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d6c84-113">Example</span></span>

 <span data-ttu-id="d6c84-114">In dit voor beeld wordt de [Get-process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon uitgevoerd in de standaard runs Pace van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="d6c84-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d6c84-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d6c84-115">See Also</span></span>
