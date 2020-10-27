---
ms.date: 09/13/2016
ms.topic: reference
title: Een beperkte runspace maken
description: Een beperkte runspace maken
ms.openlocfilehash: 53fee3cc7d8625425bc6a73196aee9eee7f17ed6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651164"
---
# <a name="creating-a-constrained-runspace"></a>Een beperkte runspace maken

Uit veiligheids overwegingen kunt u het beste de Windows Power shell-opdrachten beperken die beschikbaar zijn voor uw hosttoepassing. Als u dit wilt doen, maakt u een lege [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) door deSystem.Management.Automation.Runspaces.Initialsessionstate aan te roepen [ . Maak](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) de methode * en voeg vervolgens alleen de opdrachten toe die u wilt weer beschikbaar.

 Het gebruik van een runs Pace waarmee alleen de door u opgegeven opdrachten worden geladen, levert aanzienlijk betere prestaties.

 U gebruikt de methoden van de klasse [System. Management. Automation. Runspaces. Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) om cmdlets te definiëren voor de oorspronkelijke sessie status.

 U kunt ook persoonlijke opdrachten maken. Persoonlijke opdrachten kunnen worden gebruikt door de hosttoepassing, maar niet door gebruikers van de toepassing.

## <a name="adding-commands-to-an-empty-runspace"></a>Opdrachten toevoegen aan een lege runs Pace

 In het volgende voor beeld ziet u hoe u een lege InitialSessionState maakt en er opdrachten aan toevoegt.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a>Opdrachten privé maken

 U kunt ook een persoonlijke opdracht maken door de eigenschap [System. Management. Automation. Commandinfo. visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) in te stellen op [System. Management. Automation. SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private** . De hosttoepassing en andere opdrachten kunnen deze opdracht aanroepen, maar de gebruiker van de toepassing kan niet. In het volgende voor beeld is de opdracht [Get-Child item](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) privé.

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>Zie ook

 [Een InitialSessionState maken](./creating-an-initialsessionstate.md)
