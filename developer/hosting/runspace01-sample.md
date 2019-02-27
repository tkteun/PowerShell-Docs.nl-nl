---
title: Voorbeeld van Runspace01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: c33044fde4456513b5b07b998cc8db389b318e8e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846611"
---
# <a name="runspace01-sample"></a>Voorbeeld Runspace01

In dit voorbeeld laat zien hoe u de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse om uit te voeren de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon. De [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retourneert [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objecten voor elk proces dat wordt uitgevoerd op de lokale computer. De waarden van de [System.Diagnostics.Process.Processname*](/dotnet/api/System.Diagnostics.Process.ProcessName) en [System.Diagnostics.Process.Handlecount*](/dotnet/api/System.Diagnostics.Process.Handlecount) eigenschappen vervolgens worden geëxtraheerd uit de geretourneerde objecten en weergegeven in de console het venster.

## <a name="requirements"></a>Vereisten

 In dit voorbeeld is Windows PowerShell 2.0 vereist.

## <a name="demonstrates"></a>Hier ziet u

- Het maken van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object een opdracht uit te voeren.

- Een opdracht toe te voegen aan de pijplijn van de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

- De opdracht synchroon wordt uitgevoerd.

- Met behulp van [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objecten eigenschappen ophalen uit de objecten die zijn geretourneerd door de opdracht.

## <a name="example"></a>Voorbeeld

 In dit voorbeeld wordt uitgevoerd de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon in de standaard-runspace geleverd door Windows PowerShell.

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
