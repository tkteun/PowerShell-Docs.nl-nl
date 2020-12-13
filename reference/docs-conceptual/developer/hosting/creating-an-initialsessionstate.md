---
ms.date: 09/13/2016
ms.topic: reference
title: Een InitialSessionState maken
description: Een InitialSessionState maken
ms.openlocfilehash: d58a32c2ae8a22132f3095d093e3cb322f65c486
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649424"
---
# <a name="creating-an-initialsessionstate"></a>Een InitialSessionState maken

Power shell-opdrachten worden uitgevoerd in een runs Pace.
Als u Power shell in uw toepassing wilt hosten, moet u een [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -object maken.
Aan elke runs Pace is een [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object gekoppeld.
De InitialSessionState geeft kenmerken van de runs Pace op, bijvoorbeeld welke opdrachten, variabelen en modules beschikbaar zijn voor die runs Pace.

## <a name="create-a-default-initialsessionstate"></a>Een standaard-InitialSessionState maken

De methoden [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) en [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) van de klasse **InitialSessionState** kunnen worden gebruikt voor het maken van een **InitialSessionState** -object.
De methode **CreateDefault** maakt een **InitialSessionState** met alle ingebouwde opdrachten geladen, terwijl de methode **CreateDefault2** alleen de opdrachten laadt die vereist zijn voor het hosten van Power shell (de opdrachten van de module micro soft. Power shell. core).

Als u de opdrachten die beschikbaar zijn in uw host-toepassing verder wilt beperken, moet u een beperkte runs Pace maken.
Zie [een beperkte runs Pace maken](creating-a-constrained-runspace.md)voor meer informatie.

De volgende code laat zien hoe u een **InitialSessionState** kunt maken, deze kunt toewijzen aan een runs Pace, opdrachten kunt toevoegen aan de pijp lijn in die runs Pace en de opdrachten aanroept.
Zie [opdrachten toevoegen en aanroepen](adding-and-invoking-commands.md)voor meer informatie over het toevoegen en aanroepen van opdrachten.

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>Zie ook

[Een beperkte runspace maken](creating-a-constrained-runspace.md)

[Opdrachten toevoegen en aanroepen](adding-and-invoking-commands.md)
