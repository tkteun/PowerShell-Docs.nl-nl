---
title: Quick Start van Windows PowerShell-Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855105"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="53801-102">Snelstartgids voor Windows PowerShell-hosts</span><span class="sxs-lookup"><span data-stu-id="53801-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="53801-103">Voor het hosten van Windows PowerShell in uw toepassing, gebruikt u de [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasse.</span><span class="sxs-lookup"><span data-stu-id="53801-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="53801-104">Deze klasse biedt methoden voor het maken van een pijplijn van opdrachten en vervolgens deze opdrachten uitvoeren in een runspace.</span><span class="sxs-lookup"><span data-stu-id="53801-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="53801-105">De eenvoudigste manier om een hosttoepassing te maken is met de standaard-runspace.</span><span class="sxs-lookup"><span data-stu-id="53801-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="53801-106">De standaard-runspace bevat alle van de belangrijkste Windows PowerShell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="53801-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="53801-107">Als u wilt dat uw toepassing om slechts een subset van de Windows PowerShell-opdrachten zichtbaar te maken, moet u een aangepaste runspace maken.</span><span class="sxs-lookup"><span data-stu-id="53801-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="53801-108">Met behulp van de standaard-runspace</span><span class="sxs-lookup"><span data-stu-id="53801-108">Using the default runspace</span></span>

<span data-ttu-id="53801-109">Als u wilt starten, we gebruiken de standaard-runspace en gebruikt u de methoden van de [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klasse opdrachten, parameters, instructies en -scripts toevoegen aan een pijplijn.</span><span class="sxs-lookup"><span data-stu-id="53801-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="53801-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="53801-110">AddCommand</span></span>

<span data-ttu-id="53801-111">U gebruikt de [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) methode opdrachten toe te voegen aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="53801-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="53801-112">Stel bijvoorbeeld dat u wilt ophalen van de lijst met actieve processen op de machine.</span><span class="sxs-lookup"><span data-stu-id="53801-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="53801-113">De manier om uit te voeren met deze opdracht is als volgt.</span><span class="sxs-lookup"><span data-stu-id="53801-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="53801-114">Maak een [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span><span class="sxs-lookup"><span data-stu-id="53801-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="53801-115">Voeg de opdracht die u wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="53801-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="53801-116">De opdracht aanroepen.</span><span class="sxs-lookup"><span data-stu-id="53801-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="53801-117">Als u de methode AddCommand meer dan één keer aanroepen voordat u contact opneemt met de [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) methode, het resultaat van de eerste opdracht wordt doorgegeven naar de tweede, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="53801-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="53801-118">Als u niet doorgeven van het resultaat van een vorige opdracht op een opdracht wilt, toevoegen door het aanroepen van de [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="53801-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="53801-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="53801-119">AddParameter</span></span>

<span data-ttu-id="53801-120">Het vorige voorbeeld wordt een enkele opdracht zonder parameters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="53801-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="53801-121">U kunt parameters toevoegen aan de opdracht met behulp van de [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) methode.</span><span class="sxs-lookup"><span data-stu-id="53801-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="53801-122">Bijvoorbeeld de volgende code verkrijgt u een lijst met alle van de processen die zijn benoemde `PowerShell` uitgevoerd op de machine.</span><span class="sxs-lookup"><span data-stu-id="53801-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="53801-123">U kunt extra parameters toevoegen door de methode AddParameter herhaaldelijk aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="53801-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="53801-124">U kunt ook een woordenlijst met de namen van parameters en waarden toevoegen door het aanroepen van de [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) methode.</span><span class="sxs-lookup"><span data-stu-id="53801-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="53801-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="53801-125">AddStatement</span></span>

<span data-ttu-id="53801-126">U kunt simuleren via batchverwerking uitvoeren met behulp van de [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) methode, die een aanvullende instructie toegevoegd aan het einde van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="53801-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="53801-127">De volgende code verkrijgt u een lijst met actieve processen met de naam van de `PowerShell`, en vervolgens wordt de lijst met services.</span><span class="sxs-lookup"><span data-stu-id="53801-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="53801-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="53801-128">AddScript</span></span>

<span data-ttu-id="53801-129">U kunt een bestaand script uitvoeren door het aanroepen van de [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) methode.</span><span class="sxs-lookup"><span data-stu-id="53801-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="53801-130">Het volgende voorbeeld wordt een script toegevoegd aan de pijplijn en wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="53801-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="53801-131">In dit voorbeeld wordt ervan uitgegaan dat er is al een script met de naam `MyScript.ps1` in een map met de naam `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="53801-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="53801-132">Er is ook een versie van de methode voor toevoegen script waarmee een Boole-parameter met de naam `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="53801-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="53801-133">Als deze parameter is ingesteld op `true`, en vervolgens het script wordt uitgevoerd in de lokale scope.</span><span class="sxs-lookup"><span data-stu-id="53801-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="53801-134">De volgende code wordt het script uitgevoerd in de lokale scope.</span><span class="sxs-lookup"><span data-stu-id="53801-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="53801-135">Het maken van een aangepaste runspace</span><span class="sxs-lookup"><span data-stu-id="53801-135">Creating a custom runspace</span></span>

<span data-ttu-id="53801-136">Terwijl de standaard-runspace gebruikt in de vorige voorbeelden wordt geladen van de belangrijkste Windows PowerShell-opdrachten, kunt u een aangepaste runspace die alleen een subverzameling van alle opdrachten laadt.</span><span class="sxs-lookup"><span data-stu-id="53801-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="53801-137">U kunt dit wilt doen voor betere prestaties (het laden van een groter aantal opdrachten is een treffer prestaties), of om te beperken van de mogelijkheid van de gebruiker bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="53801-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="53801-138">Een runspace dat slechts een beperkt aantal opdrachten wordt een beperkte runspace genoemd.</span><span class="sxs-lookup"><span data-stu-id="53801-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="53801-139">Voor het maken van een beperkte runspace die u gebruikt de [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) en [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) klassen.</span><span class="sxs-lookup"><span data-stu-id="53801-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="53801-140">Het maken van een object InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="53801-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="53801-141">Voor het maken van een aangepaste runspace, moet u eerst maken een [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span><span class="sxs-lookup"><span data-stu-id="53801-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="53801-142">In het volgende voorbeeld gebruiken we de [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) te maken van een runspace na het maken van een standaard InitialSessionState-object.</span><span class="sxs-lookup"><span data-stu-id="53801-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="53801-143">Beperken van de runspace</span><span class="sxs-lookup"><span data-stu-id="53801-143">Constraining the runspace</span></span>

<span data-ttu-id="53801-144">In het vorige voorbeeld, er een standaard gemaakt [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object dat alle van de ingebouwde Windows PowerShell-kern geladen.</span><span class="sxs-lookup"><span data-stu-id="53801-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="53801-145">Er kan ook zijn met de naam de [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methode voor het maken van een InitialSessionState-object dat alleen de opdrachten in de Microsoft.PowerShell.Core zou laden de module.</span><span class="sxs-lookup"><span data-stu-id="53801-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="53801-146">Voor het maken van een meer beperkte runspace, moet u een lege InitialSessionState-object maken door het aanroepen van de [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) methode, en voeg deze opdrachten de InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="53801-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="53801-147">Met behulp van een runspace dat alleen de opdrachten die u opgeeft wordt geladen biedt aanzienlijk betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="53801-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="53801-148">U gebruikt de methoden van de [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) klasse voor het definiëren van de cmdlets voor de eerste sessiestatus.</span><span class="sxs-lookup"><span data-stu-id="53801-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="53801-149">In het volgende voorbeeld maakt u een lege initiële sessiestatus, vervolgens definieert en voegt de `Get-Command` en `Import-Module` opdrachten naar de sessiestatus van de eerste.</span><span class="sxs-lookup"><span data-stu-id="53801-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="53801-150">We maken een runspace beperkt door die staat voor de eerste sessie, en voert u de opdrachten in deze runspace.</span><span class="sxs-lookup"><span data-stu-id="53801-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="53801-151">Status van de eerste sessie maken.</span><span class="sxs-lookup"><span data-stu-id="53801-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="53801-152">Definieer en opdrachten toegevoegd voor de eerste sessiestatus.</span><span class="sxs-lookup"><span data-stu-id="53801-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="53801-153">Maak en open de runspace.</span><span class="sxs-lookup"><span data-stu-id="53801-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="53801-154">Een opdracht uitvoeren en het resultaat weergegeven.</span><span class="sxs-lookup"><span data-stu-id="53801-154">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="53801-155">Wanneer uitvoert, ziet de uitvoer van deze code als volgt.</span><span class="sxs-lookup"><span data-stu-id="53801-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
