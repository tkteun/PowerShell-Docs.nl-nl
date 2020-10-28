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
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="b2f00-103">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="b2f00-103">Creating a constrained runspace</span></span>

<span data-ttu-id="b2f00-104">Uit veiligheids overwegingen kunt u het beste de Windows Power shell-opdrachten beperken die beschikbaar zijn voor uw hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="b2f00-104">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="b2f00-105">Als u dit wilt doen, maakt u een lege [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) door deSystem.Management.Automation.Runspaces.Initialsessionstate aan te roepen [ . Maak](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) de methode \* en voeg vervolgens alleen de opdrachten toe die u wilt weer beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="b2f00-105">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="b2f00-106">Het gebruik van een runs Pace waarmee alleen de door u opgegeven opdrachten worden geladen, levert aanzienlijk betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="b2f00-106">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="b2f00-107">U gebruikt de methoden van de klasse [System. Management. Automation. Runspaces. Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) om cmdlets te definiëren voor de oorspronkelijke sessie status.</span><span class="sxs-lookup"><span data-stu-id="b2f00-107">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="b2f00-108">U kunt ook persoonlijke opdrachten maken.</span><span class="sxs-lookup"><span data-stu-id="b2f00-108">You can also make commands private.</span></span> <span data-ttu-id="b2f00-109">Persoonlijke opdrachten kunnen worden gebruikt door de hosttoepassing, maar niet door gebruikers van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="b2f00-109">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="b2f00-110">Opdrachten toevoegen aan een lege runs Pace</span><span class="sxs-lookup"><span data-stu-id="b2f00-110">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="b2f00-111">In het volgende voor beeld ziet u hoe u een lege InitialSessionState maakt en er opdrachten aan toevoegt.</span><span class="sxs-lookup"><span data-stu-id="b2f00-111">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

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

## <a name="making-commands-private"></a><span data-ttu-id="b2f00-112">Opdrachten privé maken</span><span class="sxs-lookup"><span data-stu-id="b2f00-112">Making commands private</span></span>

 <span data-ttu-id="b2f00-113">U kunt ook een persoonlijke opdracht maken door de eigenschap [System. Management. Automation. Commandinfo. visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) in te stellen op [System. Management. Automation. SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private** .</span><span class="sxs-lookup"><span data-stu-id="b2f00-113">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private** .</span></span> <span data-ttu-id="b2f00-114">De hosttoepassing en andere opdrachten kunnen deze opdracht aanroepen, maar de gebruiker van de toepassing kan niet.</span><span class="sxs-lookup"><span data-stu-id="b2f00-114">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="b2f00-115">In het volgende voor beeld is de opdracht [Get-Child item](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) privé.</span><span class="sxs-lookup"><span data-stu-id="b2f00-115">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="b2f00-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b2f00-116">See Also</span></span>

 [<span data-ttu-id="b2f00-117">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="b2f00-117">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
