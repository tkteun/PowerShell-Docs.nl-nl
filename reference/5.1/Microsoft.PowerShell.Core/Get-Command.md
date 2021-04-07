---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 7cb2b6af886e8175ab035cfe599641fa1afa02ff
ms.sourcegitcommit: d95a7255f6775b2973aa9473611185a5583881ff
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106555148"
---
# <span data-ttu-id="8c772-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="8c772-103">Get-Command</span></span>

## <span data-ttu-id="8c772-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="8c772-104">Synopsis</span></span>
<span data-ttu-id="8c772-105">Hiermee worden alle opdrachten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-105">Gets all commands.</span></span>

## <span data-ttu-id="8c772-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8c772-106">Syntax</span></span>

### <span data-ttu-id="8c772-107">Cmdletset (standaard)</span><span class="sxs-lookup"><span data-stu-id="8c772-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="8c772-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="8c772-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-CommandType <CommandTypes>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>]
 [-All] [-ListImported] [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

## <span data-ttu-id="8c772-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8c772-109">Description</span></span>

<span data-ttu-id="8c772-110">De `Get-Command` cmdlet haalt alle opdrachten op die zijn geïnstalleerd op de computer, zoals cmdlets, aliassen, functies, filters, scripts en toepassingen.</span><span class="sxs-lookup"><span data-stu-id="8c772-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="8c772-111">`Get-Command` Hiermee worden de opdrachten opgehaald van Power shell-modules en-opdrachten die zijn geïmporteerd uit andere sessies.</span><span class="sxs-lookup"><span data-stu-id="8c772-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="8c772-112">Als u alleen opdrachten wilt ophalen die in de huidige sessie zijn geïmporteerd, gebruikt u de para meter **ListImported** .</span><span class="sxs-lookup"><span data-stu-id="8c772-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="8c772-113">Zonder para meters worden `Get-Command` Alle cmdlets, functies en aliassen die op de computer zijn geïnstalleerd, opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="8c772-114">`Get-Command *` Hiermee worden alle typen opdrachten opgehaald, inclusief alle niet-Power Shell-bestanden in de Path-omgevings variabele ( `$env:Path` ), die wordt vermeld in het opdracht type van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="8c772-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="8c772-115">`Get-Command` met de exacte naam van de opdracht, zonder joker tekens, wordt automatisch de module met de opdracht geïmporteerd zodat u de opdracht direct kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8c772-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="8c772-116">Als u het automatisch importeren van modules wilt in-en uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="8c772-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="8c772-117">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c772-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="8c772-118">`Get-Command` de gegevens worden rechtstreeks opgehaald uit de opdracht code, in tegens telling tot `Get-Help` , waardoor de informatie wordt opgehaald uit de Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="8c772-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="8c772-119">Vanaf Windows Power shell 5,0 worden de resultaten van de `Get-Command` cmdlet standaard een **versie** kolom weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c772-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="8c772-120">Er is een nieuwe **versie** -eigenschap toegevoegd aan de klasse **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="8c772-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="8c772-121">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="8c772-121">Examples</span></span>

### <span data-ttu-id="8c772-122">Voor beeld 1: cmdlets, functies en aliassen ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="8c772-123">Met deze opdracht worden de Power shell-cmdlets, functies en aliassen opgehaald die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8c772-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="8c772-124">Voor beeld 2: opdrachten in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="8c772-125">Met deze opdracht wordt de para meter **ListImported** gebruikt om alleen de opdrachten in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="8c772-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="8c772-126">Voor beeld 3: cmdlets ophalen en weer geven in volg orde</span><span class="sxs-lookup"><span data-stu-id="8c772-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="8c772-127">Met deze opdracht worden alle cmdlets opgehaald, alfabetisch gesorteerd op het zelfstandig naam woord in de cmdletnaam en worden deze vervolgens weer gegeven in groepen op basis van zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="8c772-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="8c772-128">Deze weer gave kan u helpen de cmdlets voor een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="8c772-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="8c772-129">Voor beeld 4: opdrachten in een module ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="8c772-130">Met deze opdracht wordt de para meter **module** gebruikt om de opdrachten in de modules micro soft. Power shell. Security en micro soft. Power shell. Utility op te halen.</span><span class="sxs-lookup"><span data-stu-id="8c772-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="8c772-131">Voor beeld 5: informatie over een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="8c772-132">Met deze opdracht wordt informatie over de `Get-AppLockerPolicy` cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="8c772-133">Ook wordt de **AppLocker** -module geïmporteerd, waarmee alle opdrachten in de **AppLocker** -module worden toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="8c772-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="8c772-134">Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de Import-Module-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c772-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="8c772-135">De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="8c772-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="8c772-136">Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="8c772-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="8c772-137">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c772-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="8c772-138">Voor beeld 6: de syntaxis van een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="8c772-139">Deze opdracht maakt gebruik van de para meters **argument List** en **syntax** om de syntaxis van de cmdlet op te halen `Get-ChildItem` wanneer deze wordt gebruikt in het certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="8c772-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="8c772-140">Het certificaat: station is een Power Shell-station dat door de certificaat provider aan de sessie wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="8c772-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="8c772-141">Wanneer u de syntaxis die wordt weer gegeven in de uitvoer vergelijkt met de syntaxis die wordt weer gegeven wanneer u de para meter **args** (**argument List**) weglaat, ziet u dat de **certificaat provider** een dynamische para meter, **CodeSigningCert**, toevoegt aan de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c772-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** (**ArgumentList**) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert**, to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="8c772-142">Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie over de certificaat provider.</span><span class="sxs-lookup"><span data-stu-id="8c772-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="8c772-143">Voor beeld 7: dynamische para meters ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="8c772-144">De opdracht in het voor beeld gebruikt de `Get-DynamicParameters` functie om de dynamische para meters op te halen die de certificaat provider toevoegt aan de `Get-ChildItem` cmdlet wanneer deze wordt gebruikt in het certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="8c772-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | 
      ForEach-Object {$_.Parameters} | 
        Where-Object { $_.IsDynamic } | 
          Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="8c772-145">Met de `Get-DynamicParameters` functie in dit voor beeld worden de dynamische para meters van een cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="8c772-146">Dit is een alternatief voor de methode die wordt gebruikt in het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="8c772-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="8c772-147">Dynamische para meter kan worden toegevoegd aan een cmdlet door een andere cmdlet of een provider.</span><span class="sxs-lookup"><span data-stu-id="8c772-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="8c772-148">Voor beeld 8: alle opdrachten van alle typen ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="8c772-149">Met deze opdracht worden alle opdrachten van alle typen op de lokale computer opgehaald, met inbegrip van uitvoer bare bestanden in de paden van de omgevings variabele **Path** ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="8c772-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="8c772-150">Er wordt een **ApplicationInfo** -object (System. Management. Automation. ApplicationInfo) geretourneerd voor elk bestand, niet een **file info** -object (System. io. file info).</span><span class="sxs-lookup"><span data-stu-id="8c772-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="8c772-151">Voor beeld 9: cmdlets ophalen met behulp van de naam en het type van de para meter</span><span class="sxs-lookup"><span data-stu-id="8c772-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="8c772-152">Met deze opdracht worden cmdlets opgehaald die een para meter hebben waarvan de naam auth bevat en waarvan het type **AuthenticationMechanism** is.</span><span class="sxs-lookup"><span data-stu-id="8c772-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism**.</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="8c772-153">U kunt een opdracht als deze gebruiken om cmdlets te vinden waarmee u de methode kunt opgeven die wordt gebruikt om de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="8c772-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="8c772-154">De para meter **parameter type** onderscheidt para meters die een **AuthenticationMechanism** -waarde overnemen van de para meter **authenticationLevel** , zelfs wanneer deze vergelijk bare namen hebben.</span><span class="sxs-lookup"><span data-stu-id="8c772-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="8c772-155">Voor beeld 10: een alias ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-155">Example 10: Get an alias</span></span>

<span data-ttu-id="8c772-156">In dit voor beeld ziet u hoe u de `Get-Command` cmdlet gebruikt met een alias.</span><span class="sxs-lookup"><span data-stu-id="8c772-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command -Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="8c772-157">Hoewel dit doorgaans wordt gebruikt voor cmdlets en functies, worden `Get-Command` ook scripts, functies, aliassen en uitvoer bare bestanden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="8c772-158">In de uitvoer van de opdracht wordt de speciale weer gave van de **naam** eigenschaps waarde voor aliassen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c772-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="8c772-159">In de weer gave worden de alias en de volledige opdracht naam weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c772-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="8c772-160">Voor beeld 11: alle exemplaren van de opdracht Notepad ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-160">Example 11: Get all instances of the Notepad command</span></span>

<span data-ttu-id="8c772-161">In dit voor beeld wordt de para meter **all** van de `Get-Command` cmdlet gebruikt om alle exemplaren van de `Notepad` opdracht op de lokale computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8c772-161">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="8c772-162">De para meter **all** is handig wanneer er meer dan één opdracht is met dezelfde naam in de sessie.</span><span class="sxs-lookup"><span data-stu-id="8c772-162">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="8c772-163">Vanaf Windows Power Shell 3,0 wordt standaard, wanneer de sessie meerdere opdrachten met dezelfde naam bevat, `Get-Command` alleen de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="8c772-163">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="8c772-164">Met de **alle** para meters worden `Get-Command` alle opdrachten met de opgegeven naam opgehaald en worden deze in volg orde van uitvoerings volgorde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8c772-164">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="8c772-165">Als u een andere opdracht dan de eerste uit de lijst wilt uitvoeren, typt u het volledig gekwalificeerde pad naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8c772-165">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="8c772-166">Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de rang orde van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8c772-166">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="8c772-167">Voor beeld 12: de naam van een module met een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-167">Example 12: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="8c772-168">Met deze opdracht wordt de naam opgehaald van de module waarin de `Get-Date` cmdlet afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="8c772-168">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="8c772-169">De opdracht maakt gebruik van **de eigenschap PropertyName** van alle opdrachten.</span><span class="sxs-lookup"><span data-stu-id="8c772-169">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="8c772-170">Deze opdracht indeling werkt op opdrachten in Power shell-modules, zelfs als deze niet in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="8c772-170">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="8c772-171">Voor beeld 13: cmdlets en functies met een uitvoer type ophalen</span><span class="sxs-lookup"><span data-stu-id="8c772-171">Example 13: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="8c772-172">Met deze opdracht worden de cmdlets en functies opgehaald die een uitvoer type hebben en het type objecten dat ze retour neren.</span><span class="sxs-lookup"><span data-stu-id="8c772-172">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="8c772-173">Het eerste deel van de opdracht haalt alle cmdlets op.</span><span class="sxs-lookup"><span data-stu-id="8c772-173">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="8c772-174">Een pijplijn operator ( `|` ) verzendt de-cmdlets naar de `Where-Object` cmdlet, waarmee alleen de waarden worden geselecteerd waarin de eigenschap **output** type wordt ingevuld.</span><span class="sxs-lookup"><span data-stu-id="8c772-174">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="8c772-175">Een andere pijplijn operator verzendt de geselecteerde cmdlet-objecten naar de `Format-List` cmdlet, waarin de naam en het uitvoer type van elke cmdlet in een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c772-175">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="8c772-176">De eigenschap **output** type van een **CommandInfo** -object heeft alleen een waarde die niet null is wanneer de cmdlet code het kenmerk **output** type voor de cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="8c772-176">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="8c772-177">Voor beeld 14: cmdlets ophalen die een specifiek object type als invoer hebben</span><span class="sxs-lookup"><span data-stu-id="8c772-177">Example 14: Get cmdlets that take a specific object type as input</span></span>

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

<span data-ttu-id="8c772-178">Met deze opdracht vindt u cmdlets die net-adapter objecten als invoer hebben.</span><span class="sxs-lookup"><span data-stu-id="8c772-178">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="8c772-179">U kunt deze opdracht indeling gebruiken om de cmdlets te vinden die het type objecten accepteren dat door een opdracht wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8c772-179">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="8c772-180">De opdracht maakt gebruik van de intrinsieke eigenschap **PSTypeNames** van alle objecten, waarmee de typen worden opgehaald die het object beschrijven.</span><span class="sxs-lookup"><span data-stu-id="8c772-180">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="8c772-181">Als u de eigenschap **PSTypeNames** van een netwerk adapter wilt ophalen en niet de eigenschap **PSTypeNames** van een verzameling netwerk adapters, gebruikt de opdracht matrix notatie om de eerste netadapter op te halen die door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8c772-181">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span> <span data-ttu-id="8c772-182">Als u de eigenschap **PSTypeNames** van een netwerk adapter wilt ophalen en niet de eigenschap **PSTypeNames** van een verzameling netwerk adapters, gebruikt de opdracht matrix notatie om de eerste netadapter op te halen die door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8c772-182">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

## <span data-ttu-id="8c772-183">Parameters</span><span class="sxs-lookup"><span data-stu-id="8c772-183">Parameters</span></span>

### <span data-ttu-id="8c772-184">-Alle</span><span class="sxs-lookup"><span data-stu-id="8c772-184">-All</span></span>

<span data-ttu-id="8c772-185">Geeft aan dat met deze cmdlet alle opdrachten worden opgehaald, met inbegrip van opdrachten van hetzelfde type die dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="8c772-185">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="8c772-186">Standaard worden `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="8c772-186">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="8c772-187">Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de methode die door Power shell wordt gebruikt voor het selecteren van de opdracht die moet worden uitgevoerd wanneer meerdere opdrachten dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="8c772-187">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="8c772-188">Zie [about_Modules](About/about_Modules.md)voor meer informatie over opdracht namen in de module en het uitvoeren van opdrachten die niet standaard worden uitgevoerd vanwege een naam conflict.</span><span class="sxs-lookup"><span data-stu-id="8c772-188">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="8c772-189">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c772-189">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="8c772-190">In Windows Power Shell 2,0 worden `Get-Command` alle opdrachten standaard opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-190">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-191">-Argument List</span><span class="sxs-lookup"><span data-stu-id="8c772-191">-ArgumentList</span></span>

<span data-ttu-id="8c772-192">Hiermee wordt een matrix met argumenten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8c772-192">Specifies an array of arguments.</span></span> <span data-ttu-id="8c772-193">Met deze cmdlet wordt informatie opgehaald over een cmdlet of functie wanneer deze wordt gebruikt met de opgegeven para meters ("argumenten").</span><span class="sxs-lookup"><span data-stu-id="8c772-193">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="8c772-194">De alias voor **argument List** is **args**.</span><span class="sxs-lookup"><span data-stu-id="8c772-194">The alias for **ArgumentList** is **Args**.</span></span>

<span data-ttu-id="8c772-195">Als u dynamische para meters wilt detecteren die alleen beschikbaar zijn wanneer bepaalde andere para meters worden gebruikt, stelt u de waarde van **argument List** in op de para meters die de dynamische para meters activeren.</span><span class="sxs-lookup"><span data-stu-id="8c772-195">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="8c772-196">Als u de dynamische para meters wilt detecteren die een provider aan een cmdlet toevoegt, stelt u de waarde van de para meter **argument List** in op een pad in het provider station, zoals WSMan:, HKLM: of CERT:.</span><span class="sxs-lookup"><span data-stu-id="8c772-196">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="8c772-197">Wanneer de opdracht een Power shell-provider-cmdlet is, voert u slechts één pad in elke opdracht in.</span><span class="sxs-lookup"><span data-stu-id="8c772-197">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="8c772-198">De provider-cmdlets retour neren alleen de dynamische para meters voor het eerste pad de waarde van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="8c772-198">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList**.</span></span> <span data-ttu-id="8c772-199">Zie [about_Providers](About/about_Providers.md)voor meer informatie over de provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8c772-199">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-200">-CommandType</span><span class="sxs-lookup"><span data-stu-id="8c772-200">-CommandType</span></span>

<span data-ttu-id="8c772-201">Hiermee geeft u de typen opdrachten op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-201">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="8c772-202">Voer een of meer opdracht typen in.</span><span class="sxs-lookup"><span data-stu-id="8c772-202">Enter one or more command types.</span></span> <span data-ttu-id="8c772-203">Gebruik **CommandType** of de alias, **Typ**.</span><span class="sxs-lookup"><span data-stu-id="8c772-203">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="8c772-204">Hiermee worden standaard `Get-Command` Alle cmdlets, functies en aliassen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-204">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="8c772-205">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="8c772-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8c772-206">`Alias`: Hiermee worden de aliassen van alle Power shell-opdrachten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-206">`Alias`: Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="8c772-207">Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c772-207">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="8c772-208">`All`: Hiermee worden alle opdracht typen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-208">`All`: Gets all command types.</span></span> <span data-ttu-id="8c772-209">Deze parameter waarde is gelijk aan `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="8c772-209">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="8c772-210">`Application`: Hiermee worden niet-Power Shell-bestanden in paden weer gegeven in de omgevings variabele **Path** ( `$env:path` ), inclusief. txt,. exe en. dll-bestanden.</span><span class="sxs-lookup"><span data-stu-id="8c772-210">`Application`: Gets non-PowerShell files in paths listed in the **Path** environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="8c772-211">Zie [about_Environment_Variables](About/about_Environment_Variables.md)voor meer informatie over de omgevings variabele **Path** .</span><span class="sxs-lookup"><span data-stu-id="8c772-211">For more information about the **Path** environment variable, see [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>
- <span data-ttu-id="8c772-212">`Cmdlet`: Hiermee worden alle cmdlets opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-212">`Cmdlet`: Gets all cmdlets.</span></span>
- <span data-ttu-id="8c772-213">`ExternalScript`: Hiermee worden alle. ps1-bestanden opgehaald uit de paden die worden weer gegeven in de **Path** -omgevings variabele ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="8c772-213">`ExternalScript`: Gets all .ps1 files in the paths listed in the **Path** environment variable (`$env:path`).</span></span>
- <span data-ttu-id="8c772-214">`Filter` en `Function` : haalt alle geavanceerde en eenvoudige Power shell-functies en-filters op.</span><span class="sxs-lookup"><span data-stu-id="8c772-214">`Filter` and `Function`: Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="8c772-215">`Script`: Hiermee worden alle script blokken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-215">`Script`: Gets all script blocks.</span></span> <span data-ttu-id="8c772-216">Als u Power shell-scripts (. ps1-bestanden) wilt ophalen, gebruikt u de `ExternalScript` waarde.</span><span class="sxs-lookup"><span data-stu-id="8c772-216">To get PowerShell scripts (.ps1 files), use the `ExternalScript` value.</span></span>
- <span data-ttu-id="8c772-217">`Workflow`: Hiermee worden alle werk stromen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-217">`Workflow`: Gets all workflows.</span></span> <span data-ttu-id="8c772-218">Zie Inleiding tot de Windows Power shell-werk stroom voor meer informatie over werk stromen.</span><span class="sxs-lookup"><span data-stu-id="8c772-218">For more information about workflows, see Introducing Windows PowerShell Workflow.</span></span>

<span data-ttu-id="8c772-219">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="8c772-219">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="8c772-220">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="8c772-220">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="8c772-221">De waarden kunnen worden door gegeven aan de **CommandType** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="8c772-221">The values can be passed to the **CommandType** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="8c772-222">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="8c772-222">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="8c772-223">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="8c772-223">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-224">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="8c772-224">-FullyQualifiedModule</span></span>

<span data-ttu-id="8c772-225">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten, zoals beschreven in de sectie **opmerkingen** van [ModuleSpecification constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="8c772-225">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="8c772-226">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="8c772-226">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="8c772-227">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="8c772-227">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="8c772-228">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="8c772-228">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="8c772-229">De twee para meters sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="8c772-229">The two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-230">-ListImported</span><span class="sxs-lookup"><span data-stu-id="8c772-230">-ListImported</span></span>

<span data-ttu-id="8c772-231">Geeft aan dat met deze cmdlet alleen opdrachten in de huidige sessie worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-231">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="8c772-232">Vanaf Power Shell 3,0 worden standaard `Get-Command` alle geïnstalleerde opdrachten opgehaald, inclusief, maar niet beperkt tot, de opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="8c772-232">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="8c772-233">In Power Shell 2,0 worden alleen opdrachten in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-233">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="8c772-234">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c772-234">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-235">-Module</span><span class="sxs-lookup"><span data-stu-id="8c772-235">-Module</span></span>

<span data-ttu-id="8c772-236">Hiermee geeft u een matrix met modules op.</span><span class="sxs-lookup"><span data-stu-id="8c772-236">Specifies an array of modules.</span></span> <span data-ttu-id="8c772-237">Met deze cmdlet worden de opdrachten opgehaald die afkomstig zijn van de opgegeven modules of modules. Voer de namen in van modules of modules.</span><span class="sxs-lookup"><span data-stu-id="8c772-237">This cmdlet gets the commands that came from the specified modules or snap-ins. Enter the names of modules or snap-ins.</span></span>

<span data-ttu-id="8c772-238">Deze para meter neemt teken reeks waarden, maar de waarde van deze para meter kan ook een **PSModuleInfo** -of **PSSnapinInfo** -object zijn, zoals de objecten die de `Get-Module` , `Get-PSSnapin` , en `Import-PSSession` cmdlets retour neren.</span><span class="sxs-lookup"><span data-stu-id="8c772-238">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** or **PSSnapinInfo** object, such as the objects that the `Get-Module`, `Get-PSSnapin`, and `Import-PSSession` cmdlets return.</span></span>

<span data-ttu-id="8c772-239">U kunt deze para meter naar de naam, **module** of de alias **PSSnapin**.</span><span class="sxs-lookup"><span data-stu-id="8c772-239">You can refer to this parameter by its name, **Module**, or by its alias, **PSSnapin**.</span></span> <span data-ttu-id="8c772-240">De parameter naam die u kiest, heeft geen effect op de uitvoer van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8c772-240">The parameter name that you choose has no effect on the command output.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8c772-241">-Name</span><span class="sxs-lookup"><span data-stu-id="8c772-241">-Name</span></span>

<span data-ttu-id="8c772-242">Hiermee geeft u een matrix met namen op.</span><span class="sxs-lookup"><span data-stu-id="8c772-242">Specifies an array of names.</span></span> <span data-ttu-id="8c772-243">Met deze cmdlet worden alleen opdrachten met de opgegeven naam opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-243">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="8c772-244">Voer een naam of naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="8c772-244">Enter a name or name pattern.</span></span> <span data-ttu-id="8c772-245">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c772-245">Wildcard characters are permitted.</span></span>

<span data-ttu-id="8c772-246">Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** .</span><span class="sxs-lookup"><span data-stu-id="8c772-246">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="8c772-247">Wanneer twee opdrachten dezelfde naam hebben, `Get-Command` wordt standaard de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="8c772-247">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="8c772-248">-Zelfstandig naam woord</span><span class="sxs-lookup"><span data-stu-id="8c772-248">-Noun</span></span>

<span data-ttu-id="8c772-249">Hiermee geeft u een matrix met de naam van de opdracht op.</span><span class="sxs-lookup"><span data-stu-id="8c772-249">Specifies an array of command nouns.</span></span> <span data-ttu-id="8c772-250">Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die het opgegeven zelfstandig naam woord bevatten.</span><span class="sxs-lookup"><span data-stu-id="8c772-250">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="8c772-251">Voer een of meer zelfstandige naam woorden of een zelfstandige naam op.</span><span class="sxs-lookup"><span data-stu-id="8c772-251">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="8c772-252">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c772-252">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8c772-253">-Para meternaam</span><span class="sxs-lookup"><span data-stu-id="8c772-253">-ParameterName</span></span>

<span data-ttu-id="8c772-254">Hiermee geeft u een matrix met parameter namen op.</span><span class="sxs-lookup"><span data-stu-id="8c772-254">Specifies an array of parameter names.</span></span> <span data-ttu-id="8c772-255">Met deze cmdlet worden opdrachten in de sessie met de opgegeven para meters opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-255">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="8c772-256">Voer parameter namen of parameter aliassen in.</span><span class="sxs-lookup"><span data-stu-id="8c772-256">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="8c772-257">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="8c772-257">Wildcard characters are supported.</span></span>

<span data-ttu-id="8c772-258">Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.</span><span class="sxs-lookup"><span data-stu-id="8c772-258">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="8c772-259">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c772-259">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8c772-260">-Parameter type</span><span class="sxs-lookup"><span data-stu-id="8c772-260">-ParameterType</span></span>

<span data-ttu-id="8c772-261">Hiermee geeft u een matrix met parameter namen op.</span><span class="sxs-lookup"><span data-stu-id="8c772-261">Specifies an array of parameter names.</span></span> <span data-ttu-id="8c772-262">Deze cmdlet haalt opdrachten op in de sessie die para meters van het opgegeven type hebben.</span><span class="sxs-lookup"><span data-stu-id="8c772-262">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="8c772-263">Voer de volledige naam of gedeeltelijke naam van een parameter type in.</span><span class="sxs-lookup"><span data-stu-id="8c772-263">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="8c772-264">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="8c772-264">Wildcard characters are supported.</span></span>

<span data-ttu-id="8c772-265">Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.</span><span class="sxs-lookup"><span data-stu-id="8c772-265">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="8c772-266">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c772-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8c772-267">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="8c772-267">-ShowCommandInfo</span></span>

<span data-ttu-id="8c772-268">Geeft aan dat met deze cmdlet opdracht gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8c772-268">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="8c772-269">Deze para meter is geïntroduceerd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="8c772-269">This parameter was introduced in Windows PowerShell 5.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-270">-Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8c772-270">-Syntax</span></span>

<span data-ttu-id="8c772-271">Geeft aan dat met deze cmdlet alleen de volgende opgegeven gegevens over de opdracht worden opgehaald:</span><span class="sxs-lookup"><span data-stu-id="8c772-271">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="8c772-272">Aliassen krijgt de standaard naam.</span><span class="sxs-lookup"><span data-stu-id="8c772-272">Aliases Gets the standard name.</span></span>
- <span data-ttu-id="8c772-273">Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8c772-273">Cmdlets.</span></span> <span data-ttu-id="8c772-274">Hiermee wordt de syntaxis opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-274">Gets the syntax.</span></span>
- <span data-ttu-id="8c772-275">Functies en filters.</span><span class="sxs-lookup"><span data-stu-id="8c772-275">Functions and filters.</span></span> <span data-ttu-id="8c772-276">Hiermee wordt de functie definitie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-276">Gets the function definition.</span></span>
- <span data-ttu-id="8c772-277">Scripts en toepassingen of bestanden.</span><span class="sxs-lookup"><span data-stu-id="8c772-277">Scripts and applications or files.</span></span> <span data-ttu-id="8c772-278">Hiermee haalt u het pad en de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="8c772-278">Gets the path and filename.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-279">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="8c772-279">-TotalCount</span></span>

<span data-ttu-id="8c772-280">Hiermee geeft u het aantal opdrachten op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-280">Specifies the number of commands to get.</span></span> <span data-ttu-id="8c772-281">U kunt deze para meter gebruiken om de uitvoer van een opdracht te beperken.</span><span class="sxs-lookup"><span data-stu-id="8c772-281">You can use this parameter to limit the output of a command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8c772-282">-Verb</span><span class="sxs-lookup"><span data-stu-id="8c772-282">-Verb</span></span>

<span data-ttu-id="8c772-283">Hiermee geeft u een matrix met opdracht woorden op.</span><span class="sxs-lookup"><span data-stu-id="8c772-283">Specifies an array of command verbs.</span></span> <span data-ttu-id="8c772-284">Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die de opgegeven term bevatten.</span><span class="sxs-lookup"><span data-stu-id="8c772-284">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="8c772-285">Voer een of meer woorden of woord patronen in.</span><span class="sxs-lookup"><span data-stu-id="8c772-285">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="8c772-286">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8c772-286">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8c772-287">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c772-287">CommonParameters</span></span>

<span data-ttu-id="8c772-288">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c772-288">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c772-289">Zie [about_CommonParameters](About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c772-289">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="8c772-290">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="8c772-290">Inputs</span></span>

### <span data-ttu-id="8c772-291">System. String</span><span class="sxs-lookup"><span data-stu-id="8c772-291">System.String</span></span>

<span data-ttu-id="8c772-292">U kunt opdracht namen door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c772-292">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="8c772-293">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="8c772-293">Outputs</span></span>

### <span data-ttu-id="8c772-294">System. Management. Automation. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="8c772-294">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="8c772-295">Deze cmdlet retourneert objecten die zijn afgeleid van de **CommandInfo** -klasse.</span><span class="sxs-lookup"><span data-stu-id="8c772-295">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="8c772-296">Het type van het object dat wordt geretourneerd, is afhankelijk van het type opdracht dat `Get-Command` wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8c772-296">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="8c772-297">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="8c772-297">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="8c772-298">Vertegenwoordigt aliassen.</span><span class="sxs-lookup"><span data-stu-id="8c772-298">Represents aliases.</span></span>

### <span data-ttu-id="8c772-299">System. Management. Automation. ApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="8c772-299">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="8c772-300">Hiermee worden toepassingen en bestanden aangeduid.</span><span class="sxs-lookup"><span data-stu-id="8c772-300">Represents applications and files.</span></span>

### <span data-ttu-id="8c772-301">System. Management. Automation. CmdletInfo</span><span class="sxs-lookup"><span data-stu-id="8c772-301">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="8c772-302">Vertegenwoordigt cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8c772-302">Represents cmdlets.</span></span>

### <span data-ttu-id="8c772-303">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="8c772-303">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="8c772-304">Hiermee worden functies en filters aangeduid.</span><span class="sxs-lookup"><span data-stu-id="8c772-304">Represents functions and filters.</span></span>

### <span data-ttu-id="8c772-305">System. Management. Automation. WorkflowInfo</span><span class="sxs-lookup"><span data-stu-id="8c772-305">System.Management.Automation.WorkflowInfo</span></span>

<span data-ttu-id="8c772-306">Vertegenwoordigt werk stromen.</span><span class="sxs-lookup"><span data-stu-id="8c772-306">Represents workflows.</span></span>

## <span data-ttu-id="8c772-307">Notities</span><span class="sxs-lookup"><span data-stu-id="8c772-307">Notes</span></span>

- <span data-ttu-id="8c772-308">Wanneer er meer dan één opdracht met dezelfde naam beschikbaar is voor de sessie, `Get-Command` wordt de opdracht weer gegeven die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="8c772-308">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="8c772-309">Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** in volg orde uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="8c772-309">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="8c772-310">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c772-310">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="8c772-311">Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c772-311">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="8c772-312">De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="8c772-312">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="8c772-313">Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="8c772-313">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="8c772-314">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c772-314">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="8c772-315">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="8c772-315">Related Links</span></span>

[<span data-ttu-id="8c772-316">Exporteren-PSSession</span><span class="sxs-lookup"><span data-stu-id="8c772-316">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="8c772-317">Get-Help</span><span class="sxs-lookup"><span data-stu-id="8c772-317">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="8c772-318">Get-member</span><span class="sxs-lookup"><span data-stu-id="8c772-318">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="8c772-319">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="8c772-319">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="8c772-320">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="8c772-320">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="8c772-321">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="8c772-321">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)
