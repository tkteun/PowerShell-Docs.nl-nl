---
title: Opdrachten toevoegen en aanroepen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b51c4ae3fa5c5239e3c5c5e65bf7aa63c58c4da9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779791"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="f9a53-102">Opdrachten toevoegen en aanroepen</span><span class="sxs-lookup"><span data-stu-id="f9a53-102">Adding and invoking commands</span></span>

<span data-ttu-id="f9a53-103">Nadat u een runs Pace hebt gemaakt, kunt u Windows-PowerShellcommands en-scripts toevoegen aan een pijp lijn en vervolgens de pijp lijn synchroon of asynchroon aanroepen.</span><span class="sxs-lookup"><span data-stu-id="f9a53-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="f9a53-104">Een pijplijn maken</span><span class="sxs-lookup"><span data-stu-id="f9a53-104">Creating a pipeline</span></span>

 <span data-ttu-id="f9a53-105">De klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) biedt verschillende methoden om opdrachten, para meters en scripts toe te voegen aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f9a53-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="f9a53-106">U kunt de pijp lijn synchroon aanroepen door het aanroepen van een overbelasting van de methode [System. Management. Automation. Power shell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) of asynchroon door het aanroepen van een overbelasting van [System. Management. Automation. Power shell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) en vervolgens naar de methode [System. Management. Automation. Power shell. Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="f9a53-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="f9a53-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="f9a53-107">AddCommand</span></span>

1. <span data-ttu-id="f9a53-108">Maak een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.</span><span class="sxs-lookup"><span data-stu-id="f9a53-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="f9a53-109">Voeg de opdracht toe die u wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f9a53-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="f9a53-110">Roep de opdracht aan.</span><span class="sxs-lookup"><span data-stu-id="f9a53-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="f9a53-111">Als u de methode [System. Management. Automation. Power shell. Addcommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) meer dan eens aanroept voordat u de methode [System. Management. Automation. Power shell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) aanroept, wordt het resultaat van de eerste opdracht naar de tweede, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="f9a53-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="f9a53-112">Als u het resultaat van een vorige opdracht niet wilt door geven aan een opdracht, voegt u dit toe door het aanroepen van [System. Management. Automation. Power shell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="f9a53-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="f9a53-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="f9a53-113">AddParameter</span></span>

 <span data-ttu-id="f9a53-114">In het vorige voor beeld wordt één opdracht zonder para meters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f9a53-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="f9a53-115">U kunt para meters toevoegen aan de opdracht met behulp van de methode [System. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) . de volgende code haalt een lijst op met alle processen die worden `PowerShell` uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="f9a53-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="f9a53-116">U kunt aanvullende para meters toevoegen door [System. Management. Automation. Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) herhaaldelijk aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f9a53-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="f9a53-117">U kunt ook een woorden lijst met parameter namen en-waarden toevoegen door de methode [System. Management. Automation. Power shell. AddParameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f9a53-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="f9a53-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="f9a53-118">AddStatement</span></span>

 <span data-ttu-id="f9a53-119">U kunt batching simuleren met behulp van de methode [System. Management. Automation. Power shell. Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , waarmee een extra instructie aan het einde van de pijp lijn wordt toegevoegd met de volgende code wordt een lijst met actieve processen met de naam opgehaald `PowerShell` en wordt vervolgens de lijst met actieve services opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f9a53-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="f9a53-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="f9a53-120">AddScript</span></span>

 <span data-ttu-id="f9a53-121">U kunt een bestaand script uitvoeren door de methode [System. Management. Automation. Power shell. addScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f9a53-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="f9a53-122">In het volgende voor beeld wordt een script aan de pijp lijn toegevoegd en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f9a53-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="f9a53-123">In dit voor beeld wordt ervan uitgegaan dat er al een script `MyScript.ps1` met de naam in een map wordt genoemd `D:\PSScripts` .</span><span class="sxs-lookup"><span data-stu-id="f9a53-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="f9a53-124">Er is ook een versie van de methode [System. Management. Automation. Power shell. addScript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) die een Boole-para meter met de naam heeft `useLocalScope` .</span><span class="sxs-lookup"><span data-stu-id="f9a53-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="f9a53-125">Als deze para meter is ingesteld op `true` , wordt het script uitgevoerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="f9a53-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="f9a53-126">Met de volgende code wordt het script uitgevoerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="f9a53-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="f9a53-127">Een pijp lijn synchroon aanroepen</span><span class="sxs-lookup"><span data-stu-id="f9a53-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="f9a53-128">Nadat u elementen aan de pijp lijn hebt toegevoegd, kunt u deze aanroepen.</span><span class="sxs-lookup"><span data-stu-id="f9a53-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="f9a53-129">Als u de pijp lijn synchroon wilt aanroepen, roept u een overbelasting aan van de methode [System. Management. Automation. Power shell. Invoke \*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) .</span><span class="sxs-lookup"><span data-stu-id="f9a53-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="f9a53-130">In het volgende voor beeld ziet u hoe u een pijp lijn synchroon kunt aanroepen.</span><span class="sxs-lookup"><span data-stu-id="f9a53-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="f9a53-131">Een pijp lijn asynchroon aanroepen</span><span class="sxs-lookup"><span data-stu-id="f9a53-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="f9a53-132">U roept een pijp lijn asynchroon aan door een overbelasting van [System. Management. Automation. Power shell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) aan te roepen om een object [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) te maken en vervolgens de methode [System. Management. Automation. Power shell. Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f9a53-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="f9a53-133">In het volgende voor beeld ziet u hoe u een pijp lijn asynchroon aanroept.</span><span class="sxs-lookup"><span data-stu-id="f9a53-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f9a53-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f9a53-134">See Also</span></span>

 [<span data-ttu-id="f9a53-135">Een InitialSessionState maken</span><span class="sxs-lookup"><span data-stu-id="f9a53-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="f9a53-136">Een beperkte runspace maken</span><span class="sxs-lookup"><span data-stu-id="f9a53-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
