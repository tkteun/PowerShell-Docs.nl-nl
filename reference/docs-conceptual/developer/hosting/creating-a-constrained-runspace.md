---
title: Een beperkte runs Pace maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 20ac1e2af8e047b8b572d86a55439676aa8df25c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357762"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="28e03-102">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="28e03-102">Creating a constrained runspace</span></span>

<span data-ttu-id="28e03-103">Uit veiligheids overwegingen kunt u het beste de Windows Power shell-opdrachten beperken die beschikbaar zijn voor uw hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="28e03-103">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="28e03-104">Als u dit wilt doen, maakt u een leeg [System. Management. Automation. Runspaces. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) door de methode [System. Management. Automation. Runspaces. Initialsessionstate. Create \*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) aan te roepen en vervolgens alleen de gewenste opdrachten toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="28e03-104">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="28e03-105">Het gebruik van een runs Pace waarmee alleen de door u opgegeven opdrachten worden geladen, levert aanzienlijk betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="28e03-105">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="28e03-106">U gebruikt de methoden van de klasse [System. Management. Automation. Runspaces. Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) om cmdlets te definiëren voor de oorspronkelijke sessie status.</span><span class="sxs-lookup"><span data-stu-id="28e03-106">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="28e03-107">U kunt ook persoonlijke opdrachten maken.</span><span class="sxs-lookup"><span data-stu-id="28e03-107">You can also make commands private.</span></span> <span data-ttu-id="28e03-108">Persoonlijke opdrachten kunnen worden gebruikt door de hosttoepassing, maar niet door gebruikers van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="28e03-108">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="28e03-109">Opdrachten toevoegen aan een lege runs Pace</span><span class="sxs-lookup"><span data-stu-id="28e03-109">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="28e03-110">In het volgende voor beeld ziet u hoe u een lege InitialSessionState maakt en er opdrachten aan toevoegt.</span><span class="sxs-lookup"><span data-stu-id="28e03-110">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

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

## <a name="making-commands-private"></a><span data-ttu-id="28e03-111">Opdrachten privé maken</span><span class="sxs-lookup"><span data-stu-id="28e03-111">Making commands private</span></span>

 <span data-ttu-id="28e03-112">U kunt ook een persoonlijke opdracht maken door de eigenschap [System. Management. Automation. Commandinfo. visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) in te stellen op [System. Management. Automation. SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**.</span><span class="sxs-lookup"><span data-stu-id="28e03-112">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**.</span></span> <span data-ttu-id="28e03-113">De hosttoepassing en andere opdrachten kunnen deze opdracht aanroepen, maar de gebruiker van de toepassing kan niet.</span><span class="sxs-lookup"><span data-stu-id="28e03-113">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="28e03-114">In het volgende voor beeld is de opdracht [Get-Child item](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) privé.</span><span class="sxs-lookup"><span data-stu-id="28e03-114">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="28e03-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="28e03-115">See Also</span></span>

 [<span data-ttu-id="28e03-116">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="28e03-116">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
