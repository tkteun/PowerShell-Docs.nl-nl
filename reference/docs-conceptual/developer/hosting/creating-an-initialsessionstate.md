---
ms.date: 09/13/2016
ms.topic: reference
title: Een InitialSessionState maken
description: Een InitialSessionState maken
ms.openlocfilehash: d58a32c2ae8a22132f3095d093e3cb322f65c486
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649424"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="b5827-103">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="b5827-103">Creating an InitialSessionState</span></span>

<span data-ttu-id="b5827-104">Power shell-opdrachten worden uitgevoerd in een runs Pace.</span><span class="sxs-lookup"><span data-stu-id="b5827-104">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="b5827-105">Als u Power shell in uw toepassing wilt hosten, moet u een [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -object maken.</span><span class="sxs-lookup"><span data-stu-id="b5827-105">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="b5827-106">Aan elke runs Pace is een [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="b5827-106">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="b5827-107">De InitialSessionState geeft kenmerken van de runs Pace op, bijvoorbeeld welke opdrachten, variabelen en modules beschikbaar zijn voor die runs Pace.</span><span class="sxs-lookup"><span data-stu-id="b5827-107">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="b5827-108">Een standaard-InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="b5827-108">Create a default InitialSessionState</span></span>

<span data-ttu-id="b5827-109">De methoden [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) en [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) van de klasse **InitialSessionState** kunnen worden gebruikt voor het maken van een **InitialSessionState** -object.</span><span class="sxs-lookup"><span data-stu-id="b5827-109">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="b5827-110">De methode **CreateDefault** maakt een **InitialSessionState** met alle ingebouwde opdrachten geladen, terwijl de methode **CreateDefault2** alleen de opdrachten laadt die vereist zijn voor het hosten van Power shell (de opdrachten van de module micro soft. Power shell. core).</span><span class="sxs-lookup"><span data-stu-id="b5827-110">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="b5827-111">Als u de opdrachten die beschikbaar zijn in uw host-toepassing verder wilt beperken, moet u een beperkte runs Pace maken.</span><span class="sxs-lookup"><span data-stu-id="b5827-111">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="b5827-112">Zie [een beperkte runs Pace maken](creating-a-constrained-runspace.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b5827-112">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="b5827-113">De volgende code laat zien hoe u een **InitialSessionState** kunt maken, deze kunt toewijzen aan een runs Pace, opdrachten kunt toevoegen aan de pijp lijn in die runs Pace en de opdrachten aanroept.</span><span class="sxs-lookup"><span data-stu-id="b5827-113">The following code shows how to create an **InitialSessionState** , assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="b5827-114">Zie [opdrachten toevoegen en aanroepen](adding-and-invoking-commands.md)voor meer informatie over het toevoegen en aanroepen van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b5827-114">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b5827-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b5827-115">See Also</span></span>

[<span data-ttu-id="b5827-116">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="b5827-116">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="b5827-117">Opdrachten toevoegen en aanroepen</span><span class="sxs-lookup"><span data-stu-id="b5827-117">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
