---
title: Het maken van een beperkte runspace | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 3c70296cb22c325ace10dc04c8b1fd941742857b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851707"
---
# <a name="creating-a-constrained-runspace"></a>Een beperkte runspace maken

Voor prestaties of uit veiligheidsoverwegingen is het raadzaam om te beperken van de Windows PowerShell-opdrachten die beschikbaar zijn voor uw hosttoepassing. Om dit te doen die u maakt een lege [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) door het aanroepen van de [System.Management.Automation.Runspaces.Initialsessionstate.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) -methode en voeg vervolgens alleen de opdrachten die u beschikbaar wilt stellen.

 Met behulp van een runspace dat alleen de opdrachten die u opgeeft wordt geladen biedt aanzienlijk betere prestaties.

 U gebruikt de methoden van de [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) klasse voor het definiëren van de cmdlets voor de eerste sessiestatus.

 U kunt opdrachten ook privé maken. Persoonlijke opdrachten kunnen worden gebruikt door de host-toepassing, maar niet door gebruikers van de toepassing.

## <a name="adding-commands-to-an-empty-runspace"></a>Opdrachten toe te voegen aan een lege runspace

 Het volgende voorbeeld ziet u hoe u een lege InitialSessionState maken en opdrachten toegevoegd voor het.

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

## <a name="making-commands-private"></a>Opdrachten maken persoonlijk

 U kunt een opdracht privé, ook door de instelling voor het maken van [System.Management.Automation.Commandinfo.Visibility*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) eigenschap [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) . De host-toepassing en andere opdrachten die opdracht kunnen aanroepen, maar de gebruiker van de toepassing niet. In het volgende voorbeeld wordt de [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) opdracht is privé.
U kunt een opdracht privé, ook door de instelling voor het maken van [System.Management.Automation.Commandinfo.Visibility*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) eigenschap [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) . De host-toepassing en andere opdrachten die opdracht kunnen aanroepen, maar de gebruiker van de toepassing niet. In het volgende voorbeeld wordt de [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) opdracht is privé.

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>Zie ook

 [Het maken van een InitialSessionState](./creating-an-initialsessionstate.md)
