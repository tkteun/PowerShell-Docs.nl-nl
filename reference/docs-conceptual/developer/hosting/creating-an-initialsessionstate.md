---
title: Een InitialSessionState maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271879"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="9f264-102">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="9f264-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="9f264-103">Power shell-opdrachten worden uitgevoerd in een runs Pace.</span><span class="sxs-lookup"><span data-stu-id="9f264-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="9f264-104">Als u Power shell in uw toepassing wilt hosten, moet u een [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -object maken.</span><span class="sxs-lookup"><span data-stu-id="9f264-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="9f264-105">Aan elke runs Pace is het object [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="9f264-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="9f264-106">De InitialSessionState geeft kenmerken van de runs Pace op, bijvoorbeeld welke opdrachten, variabelen en modules beschikbaar zijn voor die runs Pace.</span><span class="sxs-lookup"><span data-stu-id="9f264-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="9f264-107">Een standaard-InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="9f264-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="9f264-108">De methoden [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) en [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) van de klasse **InitialSessionState** kunnen worden gebruikt voor het maken van een **InitialSessionState** -object.</span><span class="sxs-lookup"><span data-stu-id="9f264-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="9f264-109">De methode **CreateDefault** maakt een **InitialSessionState** met alle ingebouwde opdrachten geladen, terwijl de methode **CreateDefault2** alleen de opdrachten laadt die vereist zijn voor het hosten van Power shell (de opdrachten van de module micro soft. Power shell. core).</span><span class="sxs-lookup"><span data-stu-id="9f264-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="9f264-110">Als u de opdrachten die beschikbaar zijn in uw host-toepassing verder wilt beperken, moet u een beperkte runs Pace maken.</span><span class="sxs-lookup"><span data-stu-id="9f264-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="9f264-111">Zie [een beperkte runs Pace maken](creating-a-constrained-runspace.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9f264-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="9f264-112">De volgende code laat zien hoe u een **InitialSessionState**kunt maken, deze kunt toewijzen aan een runs Pace, opdrachten kunt toevoegen aan de pijp lijn in die runs Pace en de opdrachten aanroept.</span><span class="sxs-lookup"><span data-stu-id="9f264-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="9f264-113">Zie [opdrachten toevoegen en aanroepen](adding-and-invoking-commands.md)voor meer informatie over het toevoegen en aanroepen van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="9f264-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9f264-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9f264-114">See Also</span></span>

[<span data-ttu-id="9f264-115">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="9f264-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="9f264-116">Opdrachten toevoegen en aanroepen</span><span class="sxs-lookup"><span data-stu-id="9f264-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
