---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 60b6d2e380685650a86f74056a992afb4051ddc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251365"
---
# <span data-ttu-id="22b16-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="22b16-103">Get-Command</span></span>

## <span data-ttu-id="22b16-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="22b16-104">SYNOPSIS</span></span>
<span data-ttu-id="22b16-105">Hiermee worden alle opdrachten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-105">Gets all commands.</span></span>

## <span data-ttu-id="22b16-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="22b16-106">SYNTAX</span></span>

### <span data-ttu-id="22b16-107">Cmdletset (standaard)</span><span class="sxs-lookup"><span data-stu-id="22b16-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="22b16-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="22b16-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="22b16-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="22b16-109">DESCRIPTION</span></span>

<span data-ttu-id="22b16-110">De `Get-Command` cmdlet haalt alle opdrachten op die zijn geïnstalleerd op de computer, zoals cmdlets, aliassen, functies, filters, scripts en toepassingen.</span><span class="sxs-lookup"><span data-stu-id="22b16-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="22b16-111">`Get-Command` Hiermee worden de opdrachten opgehaald van Power shell-modules en-opdrachten die zijn geïmporteerd uit andere sessies.</span><span class="sxs-lookup"><span data-stu-id="22b16-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="22b16-112">Als u alleen opdrachten wilt ophalen die in de huidige sessie zijn geïmporteerd, gebruikt u de para meter **ListImported** .</span><span class="sxs-lookup"><span data-stu-id="22b16-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="22b16-113">Zonder para meters worden `Get-Command` Alle cmdlets, functies en aliassen die op de computer zijn geïnstalleerd, opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="22b16-114">`Get-Command *` Hiermee worden alle typen opdrachten opgehaald, inclusief alle niet-Power Shell-bestanden in de Path-omgevings variabele ( `$env:Path` ), die wordt vermeld in het opdracht type van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="22b16-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="22b16-115">`Get-Command` met de exacte naam van de opdracht, zonder joker tekens, wordt automatisch de module met de opdracht geïmporteerd zodat u de opdracht direct kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="22b16-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="22b16-116">Als u het automatisch importeren van modules wilt in-en uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="22b16-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="22b16-117">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22b16-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="22b16-118">`Get-Command` de gegevens worden rechtstreeks opgehaald uit de opdracht code, in tegens telling tot `Get-Help` , waardoor de informatie wordt opgehaald uit de Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="22b16-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="22b16-119">Vanaf Windows Power shell 5,0 worden de resultaten van de `Get-Command` cmdlet standaard een **versie** kolom weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="22b16-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="22b16-120">Er is een nieuwe **versie** -eigenschap toegevoegd aan de klasse **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="22b16-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="22b16-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="22b16-121">EXAMPLES</span></span>

### <span data-ttu-id="22b16-122">Voor beeld 1: cmdlets, functies en aliassen ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="22b16-123">Met deze opdracht worden de Power shell-cmdlets, functies en aliassen opgehaald die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="22b16-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="22b16-124">Voor beeld 2: opdrachten in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="22b16-125">Met deze opdracht wordt de para meter **ListImported** gebruikt om alleen de opdrachten in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="22b16-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="22b16-126">Voor beeld 3: cmdlets ophalen en weer geven in volg orde</span><span class="sxs-lookup"><span data-stu-id="22b16-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="22b16-127">Met deze opdracht worden alle cmdlets opgehaald, alfabetisch gesorteerd op het zelfstandig naam woord in de cmdletnaam en worden deze vervolgens weer gegeven in groepen op basis van zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="22b16-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="22b16-128">Deze weer gave kan u helpen de cmdlets voor een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="22b16-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="22b16-129">Voor beeld 4: opdrachten in een module ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="22b16-130">Met deze opdracht wordt de para meter **module** gebruikt om de opdrachten in de modules micro soft. Power shell. Security en micro soft. Power shell. Utility op te halen.</span><span class="sxs-lookup"><span data-stu-id="22b16-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="22b16-131">Voor beeld 5: informatie over een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="22b16-132">Met deze opdracht wordt informatie over de `Get-AppLockerPolicy` cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="22b16-133">Ook wordt de **AppLocker** -module geïmporteerd, waarmee alle opdrachten in de **AppLocker** -module worden toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="22b16-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="22b16-134">Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de Import-Module-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22b16-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="22b16-135">De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="22b16-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="22b16-136">Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="22b16-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="22b16-137">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22b16-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="22b16-138">Voor beeld 6: de syntaxis van een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="22b16-139">Deze opdracht maakt gebruik van de para meters **argument List** en **syntax** om de syntaxis van de cmdlet op te halen `Get-ChildItem` wanneer deze wordt gebruikt in het certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="22b16-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="22b16-140">Het certificaat: station is een Power Shell-station dat door de certificaat provider aan de sessie wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="22b16-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="22b16-141">Wanneer u de syntaxis die wordt weer gegeven in de uitvoer vergelijkt met de syntaxis die wordt weer gegeven wanneer u de para meter **args** ( **argument List** ) weglaat, ziet u dat de **certificaat provider** een dynamische para meter, **CodeSigningCert** , toevoegt aan de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22b16-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** ( **ArgumentList** ) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert** , to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="22b16-142">Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie over de certificaat provider.</span><span class="sxs-lookup"><span data-stu-id="22b16-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="22b16-143">Voor beeld 7: dynamische para meters ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="22b16-144">De opdracht in het voor beeld gebruikt de `Get-DynamicParameters` functie om de dynamische para meters op te halen die de certificaat provider toevoegt aan de `Get-ChildItem` cmdlet wanneer deze wordt gebruikt in het certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="22b16-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

<span data-ttu-id="22b16-145">Met de `Get-DynamicParameters` functie in dit voor beeld worden de dynamische para meters van een cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="22b16-146">Dit is een alternatief voor de methode die wordt gebruikt in het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="22b16-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="22b16-147">Dynamische para meter kan worden toegevoegd aan een cmdlet door een andere cmdlet of een provider.</span><span class="sxs-lookup"><span data-stu-id="22b16-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="22b16-148">Voor beeld 8: alle opdrachten van alle typen ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="22b16-149">Met deze opdracht worden alle opdrachten van alle typen op de lokale computer opgehaald, met inbegrip van uitvoer bare bestanden in de paden van de omgevings variabele **Path** ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="22b16-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="22b16-150">Er wordt een **ApplicationInfo** -object (System. Management. Automation. ApplicationInfo) geretourneerd voor elk bestand, niet een **file info** -object (System. io. file info).</span><span class="sxs-lookup"><span data-stu-id="22b16-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="22b16-151">Voor beeld 9: cmdlets ophalen met behulp van de naam en het type van de para meter</span><span class="sxs-lookup"><span data-stu-id="22b16-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="22b16-152">Met deze opdracht worden cmdlets opgehaald die een para meter hebben waarvan de naam auth bevat en waarvan het type **AuthenticationMechanism** is.</span><span class="sxs-lookup"><span data-stu-id="22b16-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism**.</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="22b16-153">U kunt een opdracht als deze gebruiken om cmdlets te vinden waarmee u de methode kunt opgeven die wordt gebruikt om de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="22b16-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="22b16-154">De para meter **parameter type** onderscheidt para meters die een **AuthenticationMechanism** -waarde overnemen van de para meter **authenticationLevel** , zelfs wanneer deze vergelijk bare namen hebben.</span><span class="sxs-lookup"><span data-stu-id="22b16-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="22b16-155">Voor beeld 10: een alias ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-155">Example 10: Get an alias</span></span>

<span data-ttu-id="22b16-156">In dit voor beeld ziet u hoe u de `Get-Command` cmdlet gebruikt met een alias.</span><span class="sxs-lookup"><span data-stu-id="22b16-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="22b16-157">Hoewel dit doorgaans wordt gebruikt voor cmdlets en functies, worden `Get-Command` ook scripts, functies, aliassen en uitvoer bare bestanden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="22b16-158">In de uitvoer van de opdracht wordt de speciale weer gave van de **naam** eigenschaps waarde voor aliassen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="22b16-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="22b16-159">In de weer gave worden de alias en de volledige opdracht naam weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="22b16-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="22b16-160">Voor beeld 11: de syntaxis van een alias ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-160">Example 11: Get Syntax from an alias</span></span>

<span data-ttu-id="22b16-161">In dit voor beeld ziet u hoe u de syntaxis krijgt, samen met de standaard naam van een alias.</span><span class="sxs-lookup"><span data-stu-id="22b16-161">This example shows how to get the syntax along with the standard name of an alias.</span></span>

<span data-ttu-id="22b16-162">De uitvoer van de opdracht toont de alias met het label met de standaard naam, gevolgd door de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="22b16-162">The output of the command shows the labeled alias with the standard name, followed by the syntax.</span></span>

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="22b16-163">Voor beeld 12: alle exemplaren van de opdracht Notepad ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-163">Example 12: Get all instances of the Notepad command</span></span>

<span data-ttu-id="22b16-164">In dit voor beeld wordt de para meter **all** van de `Get-Command` cmdlet gebruikt om alle exemplaren van de `Notepad` opdracht op de lokale computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="22b16-164">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="22b16-165">De para meter **all** is handig wanneer er meer dan één opdracht is met dezelfde naam in de sessie.</span><span class="sxs-lookup"><span data-stu-id="22b16-165">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="22b16-166">Vanaf Windows Power Shell 3,0 wordt standaard, wanneer de sessie meerdere opdrachten met dezelfde naam bevat, `Get-Command` alleen de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="22b16-166">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="22b16-167">Met de **alle** para meters worden `Get-Command` alle opdrachten met de opgegeven naam opgehaald en worden deze in volg orde van uitvoerings volgorde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="22b16-167">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="22b16-168">Als u een andere opdracht dan de eerste uit de lijst wilt uitvoeren, typt u het volledig gekwalificeerde pad naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="22b16-168">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="22b16-169">Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de rang orde van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="22b16-169">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="22b16-170">Voor beeld 13: de naam van een module met een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-170">Example 13: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="22b16-171">Met deze opdracht wordt de naam opgehaald van de module waarin de `Get-Date` cmdlet afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="22b16-171">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="22b16-172">De opdracht maakt gebruik van **de eigenschap PropertyName** van alle opdrachten.</span><span class="sxs-lookup"><span data-stu-id="22b16-172">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="22b16-173">Deze opdracht indeling werkt op opdrachten in Power shell-modules, zelfs als deze niet in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="22b16-173">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="22b16-174">Voor beeld 14: cmdlets en functies met een uitvoer type ophalen</span><span class="sxs-lookup"><span data-stu-id="22b16-174">Example 14: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="22b16-175">Met deze opdracht worden de cmdlets en functies opgehaald die een uitvoer type hebben en het type objecten dat ze retour neren.</span><span class="sxs-lookup"><span data-stu-id="22b16-175">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="22b16-176">Het eerste deel van de opdracht haalt alle cmdlets op.</span><span class="sxs-lookup"><span data-stu-id="22b16-176">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="22b16-177">Een pijplijn operator ( `|` ) verzendt de-cmdlets naar de `Where-Object` cmdlet, waarmee alleen de waarden worden geselecteerd waarin de eigenschap **output** type wordt ingevuld.</span><span class="sxs-lookup"><span data-stu-id="22b16-177">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="22b16-178">Een andere pijplijn operator verzendt de geselecteerde cmdlet-objecten naar de `Format-List` cmdlet, waarin de naam en het uitvoer type van elke cmdlet in een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="22b16-178">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="22b16-179">De eigenschap **output** type van een **CommandInfo** -object heeft alleen een waarde die niet null is wanneer de cmdlet code het kenmerk **output** type voor de cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="22b16-179">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="22b16-180">Voor beeld 15: cmdlets ophalen die een specifiek object type als invoer hebben</span><span class="sxs-lookup"><span data-stu-id="22b16-180">Example 15: Get cmdlets that take a specific object type as input</span></span>

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

<span data-ttu-id="22b16-181">Met deze opdracht vindt u cmdlets die net-adapter objecten als invoer hebben.</span><span class="sxs-lookup"><span data-stu-id="22b16-181">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="22b16-182">U kunt deze opdracht indeling gebruiken om de cmdlets te vinden die het type objecten accepteren dat door een opdracht wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="22b16-182">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="22b16-183">De opdracht maakt gebruik van de intrinsieke eigenschap **PSTypeNames** van alle objecten, waarmee de typen worden opgehaald die het object beschrijven.</span><span class="sxs-lookup"><span data-stu-id="22b16-183">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="22b16-184">Als u de eigenschap **PSTypeNames** van een netwerk adapter wilt ophalen en niet de eigenschap **PSTypeNames** van een verzameling netwerk adapters, gebruikt de opdracht matrix notatie om de eerste netadapter op te halen die door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="22b16-184">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="22b16-185">Voor beeld 16: opdrachten ophalen met behulp van een benadering van het Zoek resultaat</span><span class="sxs-lookup"><span data-stu-id="22b16-185">Example 16: Get commands using a fuzzy match</span></span>

<span data-ttu-id="22b16-186">In dit voor beeld heeft de naam van de opdracht opzettelijk een type ' Get-commnd '.</span><span class="sxs-lookup"><span data-stu-id="22b16-186">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="22b16-187">Met behulp van de `-UseFuzzyMatching` Switch heeft de cmdlet bepaald dat het beste resultaat werd `Get-Command` gevolgd door andere systeem eigen opdrachten op het systeem die een vergelijk bare overeenkomst hebben.</span><span class="sxs-lookup"><span data-stu-id="22b16-187">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## <span data-ttu-id="22b16-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="22b16-188">PARAMETERS</span></span>

### <span data-ttu-id="22b16-189">-Alle</span><span class="sxs-lookup"><span data-stu-id="22b16-189">-All</span></span>

<span data-ttu-id="22b16-190">Geeft aan dat met deze cmdlet alle opdrachten worden opgehaald, met inbegrip van opdrachten van hetzelfde type die dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="22b16-190">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="22b16-191">Standaard worden `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="22b16-191">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="22b16-192">Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de methode die door Power shell wordt gebruikt voor het selecteren van de opdracht die moet worden uitgevoerd wanneer meerdere opdrachten dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="22b16-192">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="22b16-193">Zie [about_Modules](About/about_Modules.md)voor meer informatie over opdracht namen in de module en het uitvoeren van opdrachten die niet standaard worden uitgevoerd vanwege een naam conflict.</span><span class="sxs-lookup"><span data-stu-id="22b16-193">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="22b16-194">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="22b16-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="22b16-195">In Windows Power Shell 2,0 worden `Get-Command` alle opdrachten standaard opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-195">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

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

### <span data-ttu-id="22b16-196">-Argument List</span><span class="sxs-lookup"><span data-stu-id="22b16-196">-ArgumentList</span></span>

<span data-ttu-id="22b16-197">Hiermee wordt een matrix met argumenten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="22b16-197">Specifies an array of arguments.</span></span> <span data-ttu-id="22b16-198">Met deze cmdlet wordt informatie opgehaald over een cmdlet of functie wanneer deze wordt gebruikt met de opgegeven para meters ("argumenten").</span><span class="sxs-lookup"><span data-stu-id="22b16-198">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="22b16-199">De alias voor **argument List** is **args**.</span><span class="sxs-lookup"><span data-stu-id="22b16-199">The alias for **ArgumentList** is **Args**.</span></span>

<span data-ttu-id="22b16-200">Als u dynamische para meters wilt detecteren die alleen beschikbaar zijn wanneer bepaalde andere para meters worden gebruikt, stelt u de waarde van **argument List** in op de para meters die de dynamische para meters activeren.</span><span class="sxs-lookup"><span data-stu-id="22b16-200">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="22b16-201">Als u de dynamische para meters wilt detecteren die een provider aan een cmdlet toevoegt, stelt u de waarde van de para meter **argument List** in op een pad in het provider station, zoals WSMan:, HKLM: of CERT:.</span><span class="sxs-lookup"><span data-stu-id="22b16-201">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="22b16-202">Wanneer de opdracht een Power shell-provider-cmdlet is, voert u slechts één pad in elke opdracht in.</span><span class="sxs-lookup"><span data-stu-id="22b16-202">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="22b16-203">De provider-cmdlets retour neren alleen de dynamische para meters voor het eerste pad de waarde van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="22b16-203">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList**.</span></span> <span data-ttu-id="22b16-204">Zie [about_Providers](About/about_Providers.md)voor meer informatie over de provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="22b16-204">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

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

### <span data-ttu-id="22b16-205">-CommandType</span><span class="sxs-lookup"><span data-stu-id="22b16-205">-CommandType</span></span>

<span data-ttu-id="22b16-206">Hiermee geeft u de typen opdrachten op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-206">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="22b16-207">Voer een of meer opdracht typen in.</span><span class="sxs-lookup"><span data-stu-id="22b16-207">Enter one or more command types.</span></span> <span data-ttu-id="22b16-208">Gebruik **CommandType** of de alias, **Typ**.</span><span class="sxs-lookup"><span data-stu-id="22b16-208">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="22b16-209">Hiermee worden standaard `Get-Command` Alle cmdlets, functies en aliassen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-209">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="22b16-210">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="22b16-210">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="22b16-211">Toe.</span><span class="sxs-lookup"><span data-stu-id="22b16-211">Alias.</span></span> <span data-ttu-id="22b16-212">Hiermee worden de aliassen opgehaald van alle Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="22b16-212">Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="22b16-213">Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22b16-213">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="22b16-214">Hele.</span><span class="sxs-lookup"><span data-stu-id="22b16-214">All.</span></span> <span data-ttu-id="22b16-215">Hiermee worden alle opdracht typen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-215">Gets all command types.</span></span> <span data-ttu-id="22b16-216">Deze parameter waarde is gelijk aan `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="22b16-216">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="22b16-217">Modules.</span><span class="sxs-lookup"><span data-stu-id="22b16-217">Application.</span></span> <span data-ttu-id="22b16-218">Hiermee worden niet-Power Shell-bestanden opgehaald in paden die worden vermeld in de omgevings variabele **Path** ($env:p AD), inclusief txt-, exe-en dll-bestanden.</span><span class="sxs-lookup"><span data-stu-id="22b16-218">Gets non-PowerShell files in paths listed in the **Path** environment variable ($env:path), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="22b16-219">Zie about_Environment_Variables voor meer informatie over de omgevings variabele **Path** .</span><span class="sxs-lookup"><span data-stu-id="22b16-219">For more information about the **Path** environment variable, see about_Environment_Variables.</span></span>
- <span data-ttu-id="22b16-220">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22b16-220">Cmdlet.</span></span> <span data-ttu-id="22b16-221">Hiermee worden alle cmdlets opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-221">Gets all cmdlets.</span></span>
- <span data-ttu-id="22b16-222">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="22b16-222">ExternalScript.</span></span> <span data-ttu-id="22b16-223">Hiermee worden alle. ps1-bestanden opgehaald uit de paden die worden vermeld in de **Path** -omgevings variabele ($env:p AD).</span><span class="sxs-lookup"><span data-stu-id="22b16-223">Gets all .ps1 files in the paths listed in the **Path** environment variable ($env:path).</span></span>
- <span data-ttu-id="22b16-224">Filter en functie.</span><span class="sxs-lookup"><span data-stu-id="22b16-224">Filter and Function.</span></span> <span data-ttu-id="22b16-225">Hiermee worden alle geavanceerde en eenvoudige Power shell-functies en-filters opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-225">Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="22b16-226">Schriften.</span><span class="sxs-lookup"><span data-stu-id="22b16-226">Script.</span></span> <span data-ttu-id="22b16-227">Hiermee worden alle script blokken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-227">Gets all script blocks.</span></span> <span data-ttu-id="22b16-228">Als u Power shell-scripts (. ps1-bestanden) wilt ophalen, gebruikt u de ExternalScript-waarde.</span><span class="sxs-lookup"><span data-stu-id="22b16-228">To get PowerShell scripts (.ps1 files), use the ExternalScript value.</span></span>

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

### <span data-ttu-id="22b16-229">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="22b16-229">-FullyQualifiedModule</span></span>

<span data-ttu-id="22b16-230">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten, zoals beschreven in de sectie **opmerkingen** van [ModuleSpecification constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="22b16-230">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="22b16-231">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="22b16-231">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="22b16-232">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="22b16-232">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="22b16-233">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="22b16-233">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="22b16-234">De twee para meters sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="22b16-234">The two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="22b16-235">-ListImported</span><span class="sxs-lookup"><span data-stu-id="22b16-235">-ListImported</span></span>

<span data-ttu-id="22b16-236">Geeft aan dat met deze cmdlet alleen opdrachten in de huidige sessie worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-236">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="22b16-237">Vanaf Power Shell 3,0 worden standaard `Get-Command` alle geïnstalleerde opdrachten opgehaald, inclusief, maar niet beperkt tot, de opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="22b16-237">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="22b16-238">In Power Shell 2,0 worden alleen opdrachten in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-238">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="22b16-239">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="22b16-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="22b16-240">-Module</span><span class="sxs-lookup"><span data-stu-id="22b16-240">-Module</span></span>

<span data-ttu-id="22b16-241">Hiermee geeft u een matrix met modules op.</span><span class="sxs-lookup"><span data-stu-id="22b16-241">Specifies an array of modules.</span></span> <span data-ttu-id="22b16-242">Met deze cmdlet worden de opdrachten opgehaald die afkomstig zijn van de opgegeven modules.</span><span class="sxs-lookup"><span data-stu-id="22b16-242">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="22b16-243">Voer de namen in van modules of module-objecten.</span><span class="sxs-lookup"><span data-stu-id="22b16-243">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="22b16-244">Deze para meter neemt teken reeks waarden, maar de waarde van deze para meter kan ook een **PSModuleInfo** -object zijn, zoals de objecten die de `Get-Module` en `Import-PSSession` cmdlets retour neren.</span><span class="sxs-lookup"><span data-stu-id="22b16-244">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

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

### <span data-ttu-id="22b16-245">-Name</span><span class="sxs-lookup"><span data-stu-id="22b16-245">-Name</span></span>

<span data-ttu-id="22b16-246">Hiermee geeft u een matrix met namen op.</span><span class="sxs-lookup"><span data-stu-id="22b16-246">Specifies an array of names.</span></span> <span data-ttu-id="22b16-247">Met deze cmdlet worden alleen opdrachten met de opgegeven naam opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-247">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="22b16-248">Voer een naam of naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="22b16-248">Enter a name or name pattern.</span></span> <span data-ttu-id="22b16-249">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="22b16-249">Wildcard characters are permitted.</span></span>

<span data-ttu-id="22b16-250">Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** .</span><span class="sxs-lookup"><span data-stu-id="22b16-250">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="22b16-251">Wanneer twee opdrachten dezelfde naam hebben, `Get-Command` wordt standaard de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="22b16-251">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

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

### <span data-ttu-id="22b16-252">-Zelfstandig naam woord</span><span class="sxs-lookup"><span data-stu-id="22b16-252">-Noun</span></span>

<span data-ttu-id="22b16-253">Hiermee geeft u een matrix met de naam van de opdracht op.</span><span class="sxs-lookup"><span data-stu-id="22b16-253">Specifies an array of command nouns.</span></span> <span data-ttu-id="22b16-254">Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die het opgegeven zelfstandig naam woord bevatten.</span><span class="sxs-lookup"><span data-stu-id="22b16-254">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="22b16-255">Voer een of meer zelfstandige naam woorden of een zelfstandige naam op.</span><span class="sxs-lookup"><span data-stu-id="22b16-255">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="22b16-256">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="22b16-256">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="22b16-257">-Para meternaam</span><span class="sxs-lookup"><span data-stu-id="22b16-257">-ParameterName</span></span>

<span data-ttu-id="22b16-258">Hiermee geeft u een matrix met parameter namen op.</span><span class="sxs-lookup"><span data-stu-id="22b16-258">Specifies an array of parameter names.</span></span> <span data-ttu-id="22b16-259">Met deze cmdlet worden opdrachten in de sessie met de opgegeven para meters opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-259">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="22b16-260">Voer parameter namen of parameter aliassen in.</span><span class="sxs-lookup"><span data-stu-id="22b16-260">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="22b16-261">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="22b16-261">Wildcard characters are supported.</span></span>

<span data-ttu-id="22b16-262">Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.</span><span class="sxs-lookup"><span data-stu-id="22b16-262">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="22b16-263">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="22b16-263">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="22b16-264">-Parameter type</span><span class="sxs-lookup"><span data-stu-id="22b16-264">-ParameterType</span></span>

<span data-ttu-id="22b16-265">Hiermee geeft u een matrix met parameter namen op.</span><span class="sxs-lookup"><span data-stu-id="22b16-265">Specifies an array of parameter names.</span></span> <span data-ttu-id="22b16-266">Deze cmdlet haalt opdrachten op in de sessie die para meters van het opgegeven type hebben.</span><span class="sxs-lookup"><span data-stu-id="22b16-266">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="22b16-267">Voer de volledige naam of gedeeltelijke naam van een parameter type in.</span><span class="sxs-lookup"><span data-stu-id="22b16-267">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="22b16-268">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="22b16-268">Wildcard characters are supported.</span></span>

<span data-ttu-id="22b16-269">Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.</span><span class="sxs-lookup"><span data-stu-id="22b16-269">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="22b16-270">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="22b16-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="22b16-271">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="22b16-271">-ShowCommandInfo</span></span>

<span data-ttu-id="22b16-272">Geeft aan dat met deze cmdlet opdracht gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="22b16-272">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="22b16-273">Deze para meter is geïntroduceerd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="22b16-273">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="22b16-274">-Syntaxis</span><span class="sxs-lookup"><span data-stu-id="22b16-274">-Syntax</span></span>

<span data-ttu-id="22b16-275">Geeft aan dat met deze cmdlet alleen de volgende opgegeven gegevens over de opdracht worden opgehaald:</span><span class="sxs-lookup"><span data-stu-id="22b16-275">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="22b16-276">Aliassen.</span><span class="sxs-lookup"><span data-stu-id="22b16-276">Aliases.</span></span> <span data-ttu-id="22b16-277">Hiermee haalt u de standaard naam en syntaxis op.</span><span class="sxs-lookup"><span data-stu-id="22b16-277">Gets the standard name and syntax.</span></span>
- <span data-ttu-id="22b16-278">Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="22b16-278">Cmdlets.</span></span> <span data-ttu-id="22b16-279">Hiermee wordt de syntaxis opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-279">Gets the syntax.</span></span>
- <span data-ttu-id="22b16-280">Functies en filters.</span><span class="sxs-lookup"><span data-stu-id="22b16-280">Functions and filters.</span></span> <span data-ttu-id="22b16-281">Hiermee wordt de functie definitie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-281">Gets the function definition.</span></span>
- <span data-ttu-id="22b16-282">Scripts en toepassingen of bestanden.</span><span class="sxs-lookup"><span data-stu-id="22b16-282">Scripts and applications or files.</span></span> <span data-ttu-id="22b16-283">Hiermee haalt u het pad en de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="22b16-283">Gets the path and filename.</span></span>

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

### <span data-ttu-id="22b16-284">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="22b16-284">-TotalCount</span></span>

<span data-ttu-id="22b16-285">Hiermee geeft u het aantal opdrachten op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-285">Specifies the number of commands to get.</span></span> <span data-ttu-id="22b16-286">U kunt deze para meter gebruiken om de uitvoer van een opdracht te beperken.</span><span class="sxs-lookup"><span data-stu-id="22b16-286">You can use this parameter to limit the output of a command.</span></span>

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

### <span data-ttu-id="22b16-287">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="22b16-287">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="22b16-288">Hiermee wordt aangegeven dat overeenkomende tekens in de opdracht wordt gebruikt om te zoeken naar hoofd letters in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="22b16-288">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="22b16-289">Bijvoorbeeld, `i-psdf` komt overeen met `Import-PowerShellDataFile` de zoek tekens die overeenkomen met een hoofd letter in het resultaat.</span><span class="sxs-lookup"><span data-stu-id="22b16-289">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="22b16-290">Wanneer dit type overeenkomst wordt gebruikt, hebben joker tekens geen overeenkomstige resultaten.</span><span class="sxs-lookup"><span data-stu-id="22b16-290">When using this type of match, any wildcards will result in no matches.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="22b16-291">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="22b16-291">-UseFuzzyMatching</span></span>

<span data-ttu-id="22b16-292">Geeft aan dat er een matching-algoritme wordt gebruikt bij het zoeken van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="22b16-292">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="22b16-293">De volg orde van de uitvoer is van het meest overeenkomende resultaat dat overeenkomt met de minst waarschijnlijke overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="22b16-293">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="22b16-294">Joker tekens mogen niet worden gebruikt met fuzzy match, omdat er wordt geprobeerd opdrachten te vinden die deze Joker tekens kunnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="22b16-294">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22b16-295">-Verb</span><span class="sxs-lookup"><span data-stu-id="22b16-295">-Verb</span></span>

<span data-ttu-id="22b16-296">Hiermee geeft u een matrix met opdracht woorden op.</span><span class="sxs-lookup"><span data-stu-id="22b16-296">Specifies an array of command verbs.</span></span> <span data-ttu-id="22b16-297">Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die de opgegeven term bevatten.</span><span class="sxs-lookup"><span data-stu-id="22b16-297">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="22b16-298">Voer een of meer woorden of woord patronen in.</span><span class="sxs-lookup"><span data-stu-id="22b16-298">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="22b16-299">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="22b16-299">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="22b16-300">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="22b16-300">CommonParameters</span></span>

<span data-ttu-id="22b16-301">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="22b16-301">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="22b16-302">Zie [about_CommonParameters](About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22b16-302">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="22b16-303">INVOER</span><span class="sxs-lookup"><span data-stu-id="22b16-303">INPUTS</span></span>

### <span data-ttu-id="22b16-304">System. String</span><span class="sxs-lookup"><span data-stu-id="22b16-304">System.String</span></span>

<span data-ttu-id="22b16-305">U kunt opdracht namen door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22b16-305">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="22b16-306">UITVOER</span><span class="sxs-lookup"><span data-stu-id="22b16-306">OUTPUTS</span></span>

### <span data-ttu-id="22b16-307">System. Management. Automation. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="22b16-307">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="22b16-308">Deze cmdlet retourneert objecten die zijn afgeleid van de **CommandInfo** -klasse.</span><span class="sxs-lookup"><span data-stu-id="22b16-308">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="22b16-309">Het type van het object dat wordt geretourneerd, is afhankelijk van het type opdracht dat `Get-Command` wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22b16-309">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="22b16-310">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="22b16-310">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="22b16-311">Vertegenwoordigt aliassen.</span><span class="sxs-lookup"><span data-stu-id="22b16-311">Represents aliases.</span></span>

### <span data-ttu-id="22b16-312">System. Management. Automation. ApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="22b16-312">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="22b16-313">Hiermee worden toepassingen en bestanden aangeduid.</span><span class="sxs-lookup"><span data-stu-id="22b16-313">Represents applications and files.</span></span>

### <span data-ttu-id="22b16-314">System. Management. Automation. CmdletInfo</span><span class="sxs-lookup"><span data-stu-id="22b16-314">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="22b16-315">Vertegenwoordigt cmdlets.</span><span class="sxs-lookup"><span data-stu-id="22b16-315">Represents cmdlets.</span></span>

### <span data-ttu-id="22b16-316">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="22b16-316">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="22b16-317">Hiermee worden functies en filters aangeduid.</span><span class="sxs-lookup"><span data-stu-id="22b16-317">Represents functions and filters.</span></span>

## <span data-ttu-id="22b16-318">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="22b16-318">NOTES</span></span>

* <span data-ttu-id="22b16-319">Wanneer er meer dan één opdracht met dezelfde naam beschikbaar is voor de sessie, `Get-Command` wordt de opdracht weer gegeven die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="22b16-319">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="22b16-320">Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** in volg orde uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="22b16-320">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="22b16-321">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22b16-321">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
* <span data-ttu-id="22b16-322">Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22b16-322">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="22b16-323">De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="22b16-323">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="22b16-324">Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="22b16-324">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="22b16-325">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="22b16-325">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="22b16-326">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="22b16-326">RELATED LINKS</span></span>

[<span data-ttu-id="22b16-327">Exporteren-PSSession</span><span class="sxs-lookup"><span data-stu-id="22b16-327">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="22b16-328">Get-Help</span><span class="sxs-lookup"><span data-stu-id="22b16-328">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="22b16-329">Get-member</span><span class="sxs-lookup"><span data-stu-id="22b16-329">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="22b16-330">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="22b16-330">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="22b16-331">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="22b16-331">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="22b16-332">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="22b16-332">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)

