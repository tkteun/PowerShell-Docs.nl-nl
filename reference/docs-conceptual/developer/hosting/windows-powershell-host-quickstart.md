---
title: Snelstartgids voor Windows Power shell-host | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: fea6bd5ae49ecf552c583271ee9d869b1ccebae8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779400"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="6a6c6-102">Snelstartgids voor Windows PowerShell-hosts</span><span class="sxs-lookup"><span data-stu-id="6a6c6-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="6a6c6-103">Als u Windows Power shell in uw toepassing wilt hosten, gebruikt u de klasse [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell) .</span><span class="sxs-lookup"><span data-stu-id="6a6c6-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="6a6c6-104">Deze klasse biedt methoden die een pijp lijn van opdrachten maken en die opdrachten vervolgens uitvoeren in een runs Pace.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="6a6c6-105">De eenvoudigste manier om een hosttoepassing te maken, is door de standaard runs Pace te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="6a6c6-106">De standaard runs Pace bevat alle kern opdrachten van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="6a6c6-107">Als u wilt dat uw toepassing slechts een subset van de Windows Power shell-opdrachten weergeeft, moet u een aangepaste runs Pace maken.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="6a6c6-108">De standaard runs Pace gebruiken</span><span class="sxs-lookup"><span data-stu-id="6a6c6-108">Using the default runspace</span></span>

<span data-ttu-id="6a6c6-109">We gebruiken de standaard runs Pace en gebruiken de methoden van de klasse [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell) om opdrachten, para meters, instructies en scripts toe te voegen aan een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="6a6c6-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="6a6c6-110">AddCommand</span></span>

<span data-ttu-id="6a6c6-111">U gebruikt de methode [System. Management. Automation. Power shell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) om opdrachten toe te voegen aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="6a6c6-112">Stel bijvoorbeeld dat u de lijst met actieve processen op de computer wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="6a6c6-113">De manier om deze opdracht uit te voeren, is als volgt.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="6a6c6-114">Maak een [System. Management. Automation. Power shell](/dotnet/api/System.Management.Automation.PowerShell) -object.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="6a6c6-115">Voeg de opdracht toe die u wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="6a6c6-116">Roep de opdracht aan.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="6a6c6-117">Als u de AddCommand-methode meer dan één keer aanroept voordat u de methode [System. Management. Automation. Power shell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) aanroept, wordt het resultaat van de eerste opdracht naar het tweede gepiped, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="6a6c6-118">Als u niet wilt dat het resultaat van een vorige opdracht naar een opdracht wordt geleid, voegt u dit toe door het aanroepen van [System. Management. Automation. Power shell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="6a6c6-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="6a6c6-119">AddParameter</span></span>

<span data-ttu-id="6a6c6-120">In het vorige voor beeld wordt één opdracht zonder para meters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="6a6c6-121">U kunt para meters toevoegen aan de opdracht met behulp van de methode [System. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .</span><span class="sxs-lookup"><span data-stu-id="6a6c6-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="6a6c6-122">Met de volgende code wordt bijvoorbeeld een lijst opgehaald van alle processen die worden `PowerShell` uitgevoerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="6a6c6-123">U kunt aanvullende para meters toevoegen door de methode AddParameter herhaaldelijk aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="6a6c6-124">U kunt ook een woorden lijst met parameter namen en-waarden toevoegen door de methode [System. Management. Automation. Power shell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="6a6c6-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="6a6c6-125">AddStatement</span></span>

<span data-ttu-id="6a6c6-126">U kunt batching simuleren met behulp van de methode [System. Management. Automation. Power shell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , waarmee een extra instructie wordt toegevoegd aan het einde van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="6a6c6-127">Met de volgende code wordt een lijst met actieve processen met de naam opgehaald `PowerShell` en wordt vervolgens de lijst met actieve services opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="6a6c6-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="6a6c6-128">AddScript</span></span>

<span data-ttu-id="6a6c6-129">U kunt een bestaand script uitvoeren door de methode [System. Management. Automation. Power shell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="6a6c6-130">In het volgende voor beeld wordt een script aan de pijp lijn toegevoegd en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="6a6c6-131">In dit voor beeld wordt ervan uitgegaan dat er al een script `MyScript.ps1` met de naam in een map wordt genoemd `D:\PSScripts` .</span><span class="sxs-lookup"><span data-stu-id="6a6c6-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="6a6c6-132">Er is ook een versie van de methode AddScript die een Boole-para meter met de naam heeft `useLocalScope` .</span><span class="sxs-lookup"><span data-stu-id="6a6c6-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="6a6c6-133">Als deze para meter is ingesteld op `true` , wordt het script uitgevoerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="6a6c6-134">Met de volgende code wordt het script uitgevoerd in het lokale bereik.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="6a6c6-135">Een aangepaste runs Pace maken</span><span class="sxs-lookup"><span data-stu-id="6a6c6-135">Creating a custom runspace</span></span>

<span data-ttu-id="6a6c6-136">Hoewel de standaard runs Pace die in de vorige voor beelden wordt gebruikt, alle kern opdrachten van Windows Power shell laden, kunt u een aangepaste runs Pace maken waarmee alleen een opgegeven subset van alle opdrachten wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="6a6c6-137">U kunt dit doen om de prestaties te verbeteren (het laden van een groter aantal opdrachten is een prestatie treffer), of om de functionaliteit van de gebruiker te beperken om bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="6a6c6-138">Een runs Pace waarmee slechts een beperkt aantal opdrachten wordt weer gegeven, wordt een beperkte runs Pace genoemd.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="6a6c6-139">Als u een beperkte runs Pace wilt maken, gebruikt u de klassen [System. Management. Automation. Runspaces. runs Pace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) en [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="6a6c6-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="6a6c6-140">Een InitialSessionState-object maken</span><span class="sxs-lookup"><span data-stu-id="6a6c6-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="6a6c6-141">Als u een aangepaste runs Pace wilt maken, moet u eerst een [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object maken.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="6a6c6-142">In het volgende voor beeld gebruiken we [System. Management. Automation. Runspaces. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) om een runs Pace te maken na het maken van een standaard InitialSessionState-object.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="6a6c6-143">De runs Pace beperken</span><span class="sxs-lookup"><span data-stu-id="6a6c6-143">Constraining the runspace</span></span>

<span data-ttu-id="6a6c6-144">In het vorige voor beeld is een standaard [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object gemaakt waarmee alle ingebouwde kernen van Windows Power shell worden geladen.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="6a6c6-145">We hebben ook de [System.Management.Automation.Runspaces.InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) -methode aangeroepen om een InitialSessionState-object te maken dat alleen de opdrachten in de module micro soft. Power shell. Core zou laden.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="6a6c6-146">Als u een meer beperkte runs Pace wilt maken, moet u een leeg InitialSessionState-object maken door de [System.Management.Automation.Runspaces.InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) -methode aan te roepen en vervolgens opdrachten toe te voegen aan de InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="6a6c6-147">Het gebruik van een runs Pace waarmee alleen de door u opgegeven opdrachten worden geladen, levert aanzienlijk betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="6a6c6-148">U gebruikt de methoden van de klasse [System. Management. Automation. Runspaces. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) om cmdlets te definiëren voor de oorspronkelijke sessie status.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="6a6c6-149">In het volgende voor beeld wordt een lege begin sessie status gemaakt `Get-Command` . vervolgens worden de opdrachten en toegevoegd `Import-Module` aan de eerste sessie status.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="6a6c6-150">Vervolgens maken we een runs Pace die is beperkt door de eerste sessie status en voert u de opdrachten in die runs Pace uit.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="6a6c6-151">Maak de eerste sessie status.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="6a6c6-152">Definieer en voeg opdrachten toe aan de eerste sessie status.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="6a6c6-153">Maak de runs Pace en open deze.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="6a6c6-154">Een opdracht uitvoeren en het resultaat weer geven.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="6a6c6-155">Wanneer u deze uitvoert, ziet de uitvoer van deze code er als volgt uit.</span><span class="sxs-lookup"><span data-stu-id="6a6c6-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
