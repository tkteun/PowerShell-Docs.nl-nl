---
title: Toe te voegen en aan te roepen opdrachten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057651"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="54098-102">Opdrachten toevoegen en aanroepen</span><span class="sxs-lookup"><span data-stu-id="54098-102">Adding and invoking commands</span></span>

<span data-ttu-id="54098-103">Na het maken van een runspace, kunt u Windows PowerShellcommands en scripts toevoegen aan een pijplijn en vervolgens de pijplijn aanroepen synchroon of asynchroon.</span><span class="sxs-lookup"><span data-stu-id="54098-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="54098-104">Het maken van een pijplijn</span><span class="sxs-lookup"><span data-stu-id="54098-104">Creating a pipeline</span></span>

 <span data-ttu-id="54098-105">De [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse biedt verschillende methoden voor het toevoegen van opdrachten, parameters en scripts aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="54098-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="54098-106">U kunt de pijplijn synchroon aanroepen door het aanroepen van een overbelasting van de [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode, of asynchroon door het aanroepen van een overbelasting van de [ System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) en vervolgens de [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) methode.</span><span class="sxs-lookup"><span data-stu-id="54098-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="54098-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="54098-107">AddCommand</span></span>

1. <span data-ttu-id="54098-108">Maak een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span><span class="sxs-lookup"><span data-stu-id="54098-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="54098-109">Voeg de opdracht die u wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="54098-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="54098-110">De opdracht aanroepen.</span><span class="sxs-lookup"><span data-stu-id="54098-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="54098-111">Als u de [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) methode meer dan één keer voordat u contact opneemt met de [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode, het resultaat van de eerste opdracht wordt doorgegeven naar de tweede, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="54098-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="54098-112">Als u niet doorgeven van het resultaat van een vorige opdracht op een opdracht wilt, toevoegen door het aanroepen van de [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="54098-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="54098-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="54098-113">AddParameter</span></span>

 <span data-ttu-id="54098-114">Het vorige voorbeeld wordt een enkele opdracht zonder parameters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="54098-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="54098-115">U kunt parameters toevoegen aan de opdracht met behulp van de [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) methode bijvoorbeeld de volgende code verkrijgt u een lijst met alle van de processen die zijn met de naam `PowerShell` die worden uitgevoerd op de machine.</span><span class="sxs-lookup"><span data-stu-id="54098-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="54098-116">U kunt extra parameters toevoegen door het aanroepen van [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) herhaaldelijk.</span><span class="sxs-lookup"><span data-stu-id="54098-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="54098-117">U kunt ook een woordenlijst met de namen van parameters en waarden toevoegen door het aanroepen van de [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) methode.</span><span class="sxs-lookup"><span data-stu-id="54098-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="54098-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="54098-118">AddStatement</span></span>

 <span data-ttu-id="54098-119">U kunt simuleren via batchverwerking uitvoeren met behulp van de [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) methode, die een aanvullende instructie toegevoegd aan het einde van de pijplijn die de volgende code verkrijgt u een lijst met actieve processen met de naam `PowerShell`, en vervolgens wordt de lijst met services.</span><span class="sxs-lookup"><span data-stu-id="54098-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="54098-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="54098-120">AddScript</span></span>

 <span data-ttu-id="54098-121">U kunt een bestaand script uitvoeren door het aanroepen van de [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) methode.</span><span class="sxs-lookup"><span data-stu-id="54098-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="54098-122">Het volgende voorbeeld wordt een script toegevoegd aan de pijplijn en wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="54098-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="54098-123">In dit voorbeeld wordt ervan uitgegaan dat er is al een script met de naam `MyScript.ps1` in een map met de naam `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="54098-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="54098-124">Er is ook een versie van de [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) methode die een Boole-parameter met de naam `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="54098-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="54098-125">Als deze parameter is ingesteld op `true`, en vervolgens het script wordt uitgevoerd in de lokale scope.</span><span class="sxs-lookup"><span data-stu-id="54098-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="54098-126">De volgende code wordt het script uitgevoerd in de lokale scope.</span><span class="sxs-lookup"><span data-stu-id="54098-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="54098-127">Een pijplijn aanroepen synchroon</span><span class="sxs-lookup"><span data-stu-id="54098-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="54098-128">Nadat u elementen aan de pijplijn toevoegen, Roep deze.</span><span class="sxs-lookup"><span data-stu-id="54098-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="54098-129">Voor het aanroepen van de pijplijn synchroon, die u aanroept een overbelasting van de [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode.</span><span class="sxs-lookup"><span data-stu-id="54098-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="54098-130">Het volgende voorbeeld ziet hoe u een pijplijn synchroon kunt aanroepen.</span><span class="sxs-lookup"><span data-stu-id="54098-130">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="54098-131">Een pijplijn aanroepen asynchroon</span><span class="sxs-lookup"><span data-stu-id="54098-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="54098-132">U asynchroon een pijplijn aanroepen door het aanroepen van een overbelasting van de [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) maken een [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) -object en klikt u vervolgens aanroepen van de [ System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) methode.</span><span class="sxs-lookup"><span data-stu-id="54098-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="54098-133">Het volgende voorbeeld ziet hoe u een pijplijn asynchroon aanroepen.</span><span class="sxs-lookup"><span data-stu-id="54098-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="54098-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="54098-134">See Also</span></span>

 [<span data-ttu-id="54098-135">Het maken van een InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="54098-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="54098-136">Het maken van een beperkte runspace</span><span class="sxs-lookup"><span data-stu-id="54098-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
