---
title: Het maken van een InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: c23640b69d1e71a343e2bef2c6b3f8ffe19826d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846590"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="8afcd-102">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="8afcd-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="8afcd-103">Windows PowerShell-opdrachten uitvoeren in een runspace.</span><span class="sxs-lookup"><span data-stu-id="8afcd-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="8afcd-104">Voor het hosten van Windows PowerShell in uw toepassing, moet u een [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span><span class="sxs-lookup"><span data-stu-id="8afcd-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="8afcd-105">Elke runspace heeft een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) die zijn gekoppeld aan dit object.</span><span class="sxs-lookup"><span data-stu-id="8afcd-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="8afcd-106">De [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) bepaalt de kenmerken van de runspace, zoals welke opdrachten, variabelen en -modules beschikbaar voor deze runspace zijn.</span><span class="sxs-lookup"><span data-stu-id="8afcd-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="8afcd-107">Een standaard InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="8afcd-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="8afcd-108">De [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)en [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methoden kunnen worden gebruikt maken [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objecten.</span><span class="sxs-lookup"><span data-stu-id="8afcd-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="8afcd-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) geladen, terwijl een InitialSessionState gemaakt met alle van de ingebouwde opdrachten [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) wordt geladen alleen de opdrachten die zijn vereist voor de host Windows PowerShell (de opdrachten in de module Microsoft.PowerShell.Core.</span><span class="sxs-lookup"><span data-stu-id="8afcd-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="8afcd-110">Als u wilt de opdrachten die beschikbaar zijn in uw hosttoepassing verder te beperken die u wilt maken van een beperkte runspace.</span><span class="sxs-lookup"><span data-stu-id="8afcd-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="8afcd-111">Zie voor informatie, het maken van een beperkte runspace.</span><span class="sxs-lookup"><span data-stu-id="8afcd-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="8afcd-112">De volgende code laat zien hoe een InitialSessionState maken, deze toewijzen aan een runspace, opdrachten toevoegen aan de pijplijn in deze runspace en aanroepen van de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="8afcd-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="8afcd-113">Zie voor meer informatie over het toevoegen en aanroepen van opdrachten, toevoegen en opdrachten aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="8afcd-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

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
      // Call the InitailSessionState.CreateDefault method to create
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

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
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

## <a name="see-also"></a><span data-ttu-id="8afcd-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8afcd-114">See Also</span></span>

 [<span data-ttu-id="8afcd-115">Het maken van een beperkte runspace</span><span class="sxs-lookup"><span data-stu-id="8afcd-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
