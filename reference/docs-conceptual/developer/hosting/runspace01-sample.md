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
# <a name="runspace01-sample"></a>Voorbeeld Runspace01

In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de [Get-process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon uit te voeren. De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objecten voor elk proces dat wordt uitgevoerd op de lokale computer. De waarden van de [systeem. Diagnostics. process. procesnaam *](/dotnet/api/System.Diagnostics.Process.ProcessName) en [System. Diagnostics. process. Handlecount *](/dotnet/api/System.Diagnostics.Process.Handlecount) -eigenschappen worden vervolgens geëxtraheerd uit de geretourneerde objecten en weer gegeven in een console venster.

## <a name="requirements"></a>Vereisten

 Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Demonstreert

- Een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object maken om een opdracht uit te voeren.

- Een opdracht toevoegen aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .

- De opdracht synchroon uitvoeren.

- Met [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) objecten worden eigenschappen geëxtraheerd uit de objecten die zijn geretourneerd door de opdracht.

## <a name="example"></a>Voorbeeld

 In dit voor beeld wordt de [Get-process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon uitgevoerd in de standaard runs Pace van Windows Power shell.

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

## <a name="see-also"></a>Zie ook
