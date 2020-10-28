---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Runspace10
description: Voorbeeld Runspace10
ms.openlocfilehash: fd58cea553e6b830a56df7edfa7901d39f46a06c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657576"
---
# <a name="runspace10-sample"></a>Voorbeeld Runspace10

Dit voor beeld laat zien hoe u een standaard begin sessie status kunt maken, hoe u een cmdlet kunt toevoegen aan de [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), hoe u een runs Pace maakt die de oorspronkelijke sessie status gebruikt en hoe u de opdracht uitvoert met behulp van een object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .

## <a name="requirements"></a>Vereisten

Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Demonstreert

In dit voor beeld ziet u het volgende.

- Een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object maken.

- Het toevoegen van een cmdlet (gedefinieerd door de hosttoepassing) aan hetSystem.Management.Automation.Runspaces.Ini-object [ tialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

- Een object [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) maken dat gebruikmaakt van het-object.

- Maken van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object dat gebruikmaakt van het object [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .

- De opdracht wordt toegevoegd aan de pijp lijn van het object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .

- Eigenschappen uit de objecten [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) worden opgehaald die door de opdracht zijn geretourneerd.

## <a name="example"></a>Voorbeeld

In dit voor beeld wordt een runs Pace gemaakt die gebruikmaakt van een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object om de elementen te definiëren die beschikbaar zijn wanneer de runs Pace wordt geopend. In dit voor beeld wordt de cmdlet Get-Proc (gedefinieerd door de hosttoepassing) toegevoegd aan de eerste sessie status en wordt de cmdlet synchroon uitgevoerd met behulp van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// Class that implements the GetProcCommand.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Cmdlet Overrides

    /// <summary>
    /// For each of the requested process names, retrieve and write
    /// the associated processes.
    /// </summary>
    protected override void ProcessRecord()
    {
      // Get the current processes.
      Process[] processes = Process.GetProcesses();

      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument (true) tells the
      // system to enumerate the array, and send one process object
      // at a time to the pipeline.
      WriteObject(processes, true);
    }

    #endregion Overrides
  } // End GetProcCommand class.

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace10
  {
    /// <summary>
    /// This sample shows how to create a default initial session state, how to add
    /// add a cmdlet to the InitialSessionState object, and then how to create
    /// a Runspace object.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// This sample demonstrates:
    /// 1. Creating an InitialSessionState object.
    /// 2. Adding a cmdlet to the InitialSessionState object.
    /// 3. Creating a runspace that uses the InitialSessionState object.
    /// 4. Creating a PowerShell object that uses the Runspace object.
    /// 5. Running the added command synchronously.
    /// 6. Working with PSObject objects to extract properties
    ///    from the objects returned by the pipeline.
    private static void Main(string[] args)
    {
      // Create a default InitialSessionState object. The default
      // InitialSessionState object contains all the elements provided
      // by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the InitialSessionState object.
      SessionStateCmdletEntry ssce = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(ssce);

      // Create a Runspace object that uses the InitialSessionState object.
      // Notice that no PSHost object is specified, so the default host is used.
      // See the Hosting samples for information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Add the get-proc cmdlet to the pipeline of the PowerShell object.
          powershell.AddCommand("get-proc");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the output of the pipeline.
          foreach (PSObject result in results)
          {
             Console.WriteLine(
                               "{0,-20} {1}",
                               result.Members["ProcessName"].Value,
                               result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-hosttoepassing schrijven](./writing-a-windows-powershell-host-application.md)
