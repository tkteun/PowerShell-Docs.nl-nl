---
ms.date: 09/13/2016
ms.topic: reference
title: Opdrachten toevoegen en aanroepen
description: Opdrachten toevoegen en aanroepen
ms.openlocfilehash: c30cb15d473c344e40b96938c355d77c059fe2d5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96616026"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="c5064-103">Opdrachten toevoegen en aanroepen</span><span class="sxs-lookup"><span data-stu-id="c5064-103">Adding and invoking commands</span></span>

<span data-ttu-id="c5064-104">Nadat u een runs Pace hebt gemaakt, kunt u Windows-PowerShellcommands en-scripts toevoegen aan een pijp lijn en vervolgens de pijp lijn synchroon of asynchroon aanroepen.</span><span class="sxs-lookup"><span data-stu-id="c5064-104">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="c5064-105">Een pijplijn maken</span><span class="sxs-lookup"><span data-stu-id="c5064-105">Creating a pipeline</span></span>

<span data-ttu-id="c5064-106">De klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) biedt verschillende methoden om opdrachten, para meters en scripts toe te voegen aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c5064-106">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="c5064-107">U kunt de pijp lijn synchroon aanroepen door het aanroepen van een overbelasting van de methode [System. Management. Automation. Power shell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) of asynchroon door het aanroepen van een overbelasting van [System. Management. Automation. Power shell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) en vervolgens naar de methode [System. Management. Automation. Power shell. Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="c5064-107">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="c5064-108">AddCommand</span><span class="sxs-lookup"><span data-stu-id="c5064-108">AddCommand</span></span>

1. <span data-ttu-id="c5064-109">Maak een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.</span><span class="sxs-lookup"><span data-stu-id="c5064-109">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="c5064-110">Voeg de opdracht toe die u wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c5064-110">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="c5064-111">Roep de opdracht aan.</span><span class="sxs-lookup"><span data-stu-id="c5064-111">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="c5064-112">Als u de methode [System. Management. Automation. Power shell. Addcommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) meer dan eens aanroept voordat u de methode [System. Management. Automation. Power shell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) aanroept, wordt het resultaat van de eerste opdracht naar de tweede, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="c5064-112">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="c5064-113">Als u het resultaat van een vorige opdracht niet wilt door geven aan een opdracht, voegt u dit toe door het aanroepen van [System. Management. Automation. Power shell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="c5064-113">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="c5064-114">AddParameter</span><span class="sxs-lookup"><span data-stu-id="c5064-114">AddParameter</span></span>

 <span data-ttu-id="c5064-115">In het vorige voor beeld wordt één opdracht zonder para meters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c5064-115">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="c5064-116">U kunt para meters toevoegen aan de opdracht met behulp van de methode [System. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) . de volgende code haalt een lijst op met alle processen die worden `PowerShell` uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="c5064-116">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="c5064-117">U kunt aanvullende para meters toevoegen door [System. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) herhaaldelijk aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c5064-117">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Command")
                   .AddParameter("Name", "Get-VM")
                   .AddParameter("Module", "Hyper-V")
                   .Invoke();
```

<span data-ttu-id="c5064-118">U kunt ook een woorden lijst met parameter namen en-waarden toevoegen door de methode [System. Management. Automation. Power shell. AddParameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c5064-118">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "Get-VM");

parameters.Add("Module", "Hyper-V");
PowerShell.Create().AddCommand("Get-Command")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="c5064-119">AddStatement</span><span class="sxs-lookup"><span data-stu-id="c5064-119">AddStatement</span></span>

<span data-ttu-id="c5064-120">U kunt batching simuleren met behulp van de methode [System. Management. Automation. Power shell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , waarmee een extra instructie aan het einde van de pijp lijn wordt toegevoegd met de volgende code wordt een lijst met actieve processen met de naam opgehaald `PowerShell` en wordt vervolgens de lijst met actieve services opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5064-120">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="c5064-121">AddScript</span><span class="sxs-lookup"><span data-stu-id="c5064-121">AddScript</span></span>

<span data-ttu-id="c5064-122">U kunt een bestaand script uitvoeren door de methode [System. Management. Automation. Power shell. addScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c5064-122">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="c5064-123">In het volgende voor beeld wordt een script aan de pijp lijn toegevoegd en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c5064-123">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="c5064-124">In dit voor beeld wordt ervan uitgegaan dat er al een script `MyScript.ps1` met de naam in een map wordt genoemd `D:\PSScripts` .</span><span class="sxs-lookup"><span data-stu-id="c5064-124">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="c5064-125">Er is ook een versie van de methode [System. Management. Automation. Power shell. addScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) die een Boole-para meter met de naam heeft `useLocalScope` .</span><span class="sxs-lookup"><span data-stu-id="c5064-125">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="c5064-126">Als deze para meter is ingesteld op `true` , wordt het script uitgevoerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="c5064-126">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="c5064-127">Met de volgende code wordt het script uitgevoerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="c5064-127">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="c5064-128">Een pijp lijn synchroon aanroepen</span><span class="sxs-lookup"><span data-stu-id="c5064-128">Invoking a pipeline synchronously</span></span>

<span data-ttu-id="c5064-129">Nadat u elementen aan de pijp lijn hebt toegevoegd, kunt u deze aanroepen.</span><span class="sxs-lookup"><span data-stu-id="c5064-129">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="c5064-130">Als u de pijp lijn synchroon wilt aanroepen, roept u een overbelasting aan van de methode [System. Management. Automation. Power shell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) .</span><span class="sxs-lookup"><span data-stu-id="c5064-130">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="c5064-131">In het volgende voor beeld ziet u hoe u een pijp lijn synchroon kunt aanroepen.</span><span class="sxs-lookup"><span data-stu-id="c5064-131">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="c5064-132">Een pijp lijn asynchroon aanroepen</span><span class="sxs-lookup"><span data-stu-id="c5064-132">Invoking a pipeline asynchronously</span></span>

<span data-ttu-id="c5064-133">U roept een pijp lijn asynchroon aan door een overbelasting van [System. Management. Automation. Power shell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) aan te roepen om een object [IAsyncResult](/dotnet/api/system.iasyncresult) te maken en vervolgens de methode [System. Management. Automation. Power shell. Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c5064-133">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](/dotnet/api/system.iasyncresult) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="c5064-134">In het volgende voor beeld ziet u hoe u een pijp lijn asynchroon aanroept.</span><span class="sxs-lookup"><span data-stu-id="c5064-134">The following example shows how to invoke a pipeline asynchronously.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c5064-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c5064-135">See Also</span></span>

 [<span data-ttu-id="c5064-136">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="c5064-136">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="c5064-137">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="c5064-137">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
