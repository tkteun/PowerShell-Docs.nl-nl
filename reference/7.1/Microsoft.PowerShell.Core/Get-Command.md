---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 676ea490cbdc941ec8f7d03726a428970b0235a4
ms.sourcegitcommit: d95a7255f6775b2973aa9473611185a5583881ff
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106555488"
---
# <span data-ttu-id="30006-103">Get-Command</span><span class="sxs-lookup"><span data-stu-id="30006-103">Get-Command</span></span>

## <span data-ttu-id="30006-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="30006-104">Synopsis</span></span>
<span data-ttu-id="30006-105">Hiermee worden alle opdrachten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-105">Gets all commands.</span></span>

## <span data-ttu-id="30006-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="30006-106">Syntax</span></span>

### <span data-ttu-id="30006-107">Cmdletset (standaard)</span><span class="sxs-lookup"><span data-stu-id="30006-107">CmdletSet (Default)</span></span>

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### <span data-ttu-id="30006-108">AllCommandSet</span><span class="sxs-lookup"><span data-stu-id="30006-108">AllCommandSet</span></span>

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## <span data-ttu-id="30006-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="30006-109">Description</span></span>

<span data-ttu-id="30006-110">De `Get-Command` cmdlet haalt alle opdrachten op die zijn geïnstalleerd op de computer, zoals cmdlets, aliassen, functies, filters, scripts en toepassingen.</span><span class="sxs-lookup"><span data-stu-id="30006-110">The `Get-Command` cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications.</span></span> <span data-ttu-id="30006-111">`Get-Command` Hiermee worden de opdrachten opgehaald van Power shell-modules en-opdrachten die zijn geïmporteerd uit andere sessies.</span><span class="sxs-lookup"><span data-stu-id="30006-111">`Get-Command` gets the commands from PowerShell modules and commands that were imported from other sessions.</span></span> <span data-ttu-id="30006-112">Als u alleen opdrachten wilt ophalen die in de huidige sessie zijn geïmporteerd, gebruikt u de para meter **ListImported** .</span><span class="sxs-lookup"><span data-stu-id="30006-112">To get only commands that have been imported into the current session, use the **ListImported** parameter.</span></span>

<span data-ttu-id="30006-113">Zonder para meters worden `Get-Command` Alle cmdlets, functies en aliassen die op de computer zijn geïnstalleerd, opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-113">Without parameters, `Get-Command` gets all of the cmdlets, functions, and aliases installed on the computer.</span></span> <span data-ttu-id="30006-114">`Get-Command *` Hiermee worden alle typen opdrachten opgehaald, inclusief alle niet-Power Shell-bestanden in de Path-omgevings variabele ( `$env:Path` ), die wordt vermeld in het opdracht type van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="30006-114">`Get-Command *` gets all types of commands, including all of the non-PowerShell files in the Path environment variable (`$env:Path`), which it lists in the Application command type.</span></span>

<span data-ttu-id="30006-115">`Get-Command` met de exacte naam van de opdracht, zonder joker tekens, wordt automatisch de module met de opdracht geïmporteerd zodat u de opdracht direct kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="30006-115">`Get-Command` that uses the exact name of the command, without wildcard characters, automatically imports the module that contains the command so that you can use the command immediately.</span></span> <span data-ttu-id="30006-116">Als u het automatisch importeren van modules wilt in-en uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="30006-116">To enable, disable, and configure automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="30006-117">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30006-117">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="30006-118">`Get-Command` de gegevens worden rechtstreeks opgehaald uit de opdracht code, in tegens telling tot `Get-Help` , waardoor de informatie wordt opgehaald uit de Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="30006-118">`Get-Command` gets its data directly from the command code, unlike `Get-Help`, which gets its information from help topics.</span></span>

<span data-ttu-id="30006-119">Vanaf Windows Power shell 5,0 worden de resultaten van de `Get-Command` cmdlet standaard een **versie** kolom weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="30006-119">Starting in Windows PowerShell 5.0, results of the `Get-Command` cmdlet display a **Version** column by default.</span></span> <span data-ttu-id="30006-120">Er is een nieuwe **versie** -eigenschap toegevoegd aan de klasse **CommandInfo** .</span><span class="sxs-lookup"><span data-stu-id="30006-120">A new **Version** property has been added to the **CommandInfo** class.</span></span>

## <span data-ttu-id="30006-121">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="30006-121">Examples</span></span>

### <span data-ttu-id="30006-122">Voor beeld 1: cmdlets, functies en aliassen ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-122">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="30006-123">Met deze opdracht worden de Power shell-cmdlets, functies en aliassen opgehaald die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="30006-123">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <span data-ttu-id="30006-124">Voor beeld 2: opdrachten in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-124">Example 2: Get commands in the current session</span></span>

<span data-ttu-id="30006-125">Met deze opdracht wordt de para meter **ListImported** gebruikt om alleen de opdrachten in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="30006-125">This command uses the **ListImported** parameter to get only the commands in the current session.</span></span>

```powershell
Get-Command -ListImported
```

### <span data-ttu-id="30006-126">Voor beeld 3: cmdlets ophalen en weer geven in volg orde</span><span class="sxs-lookup"><span data-stu-id="30006-126">Example 3: Get cmdlets and display them in order</span></span>

<span data-ttu-id="30006-127">Met deze opdracht worden alle cmdlets opgehaald, alfabetisch gesorteerd op het zelfstandig naam woord in de cmdletnaam en worden deze vervolgens weer gegeven in groepen op basis van zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="30006-127">This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups.</span></span> <span data-ttu-id="30006-128">Deze weer gave kan u helpen de cmdlets voor een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="30006-128">This display can help you find the cmdlets for a task.</span></span>

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### <span data-ttu-id="30006-129">Voor beeld 4: opdrachten in een module ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-129">Example 4: Get commands in a module</span></span>

<span data-ttu-id="30006-130">Met deze opdracht wordt de para meter **module** gebruikt om de opdrachten in de modules micro soft. Power shell. Security en micro soft. Power shell. Utility op te halen.</span><span class="sxs-lookup"><span data-stu-id="30006-130">This command uses the **Module** parameter to get the commands in the Microsoft.PowerShell.Security and Microsoft.PowerShell.Utility modules.</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### <span data-ttu-id="30006-131">Voor beeld 5: informatie over een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-131">Example 5: Get information about a cmdlet</span></span>

<span data-ttu-id="30006-132">Met deze opdracht wordt informatie over de `Get-AppLockerPolicy` cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-132">This command gets information about the `Get-AppLockerPolicy` cmdlet.</span></span> <span data-ttu-id="30006-133">Ook wordt de **AppLocker** -module geïmporteerd, waarmee alle opdrachten in de **AppLocker** -module worden toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="30006-133">It also imports the **AppLocker** module, which adds all of the commands in the **AppLocker** module to the current session.</span></span>

```powershell
Get-Command Get-AppLockerPolicy
```

<span data-ttu-id="30006-134">Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de Import-Module-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30006-134">When a module is imported automatically, the effect is the same as using the Import-Module cmdlet.</span></span>
<span data-ttu-id="30006-135">De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="30006-135">The module can add commands, types and formatting files, and run scripts in the session.</span></span> <span data-ttu-id="30006-136">Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="30006-136">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="30006-137">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30006-137">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="30006-138">Voor beeld 6: de syntaxis van een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-138">Example 6: Get the syntax of a cmdlet</span></span>

<span data-ttu-id="30006-139">Deze opdracht maakt gebruik van de para meters **argument List** en **syntax** om de syntaxis van de cmdlet op te halen `Get-ChildItem` wanneer deze wordt gebruikt in het certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="30006-139">This command uses the **ArgumentList** and **Syntax** parameters to get the syntax of the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span> <span data-ttu-id="30006-140">Het certificaat: station is een Power Shell-station dat door de certificaat provider aan de sessie wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="30006-140">The Cert: drive is a PowerShell drive that the Certificate Provider adds to the session.</span></span>

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

<span data-ttu-id="30006-141">Wanneer u de syntaxis die wordt weer gegeven in de uitvoer vergelijkt met de syntaxis die wordt weer gegeven wanneer u de para meter **args** (**argument List**) weglaat, ziet u dat de **certificaat provider** een dynamische para meter, **CodeSigningCert**, toevoegt aan de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30006-141">When you compare the syntax displayed in the output with the syntax that is displayed when you omit the **Args** (**ArgumentList**) parameter, you'll see that the **Certificate provider** adds a dynamic parameter, **CodeSigningCert**, to the `Get-ChildItem` cmdlet.</span></span>

<span data-ttu-id="30006-142">Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie over de certificaat provider.</span><span class="sxs-lookup"><span data-stu-id="30006-142">For more information about the Certificate provider, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="30006-143">Voor beeld 7: dynamische para meters ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-143">Example 7: Get dynamic parameters</span></span>

<span data-ttu-id="30006-144">De opdracht in het voor beeld gebruikt de `Get-DynamicParameters` functie om de dynamische para meters op te halen die de certificaat provider toevoegt aan de `Get-ChildItem` cmdlet wanneer deze wordt gebruikt in het certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="30006-144">The command in the example uses the `Get-DynamicParameters` function to get the dynamic parameters that the Certificate provider adds to the `Get-ChildItem` cmdlet when it is used in the Cert: drive.</span></span>

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

<span data-ttu-id="30006-145">Met de `Get-DynamicParameters` functie in dit voor beeld worden de dynamische para meters van een cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-145">The `Get-DynamicParameters` function in this example gets the dynamic parameters of a cmdlet.</span></span> <span data-ttu-id="30006-146">Dit is een alternatief voor de methode die wordt gebruikt in het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="30006-146">This is an alternative to the method used in the previous example.</span></span> <span data-ttu-id="30006-147">Dynamische para meter kan worden toegevoegd aan een cmdlet door een andere cmdlet of een provider.</span><span class="sxs-lookup"><span data-stu-id="30006-147">Dynamic parameter can be added to a cmdlet by another cmdlet or a provider.</span></span>

### <span data-ttu-id="30006-148">Voor beeld 8: alle opdrachten van alle typen ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-148">Example 8: Get all commands of all types</span></span>

<span data-ttu-id="30006-149">Met deze opdracht worden alle opdrachten van alle typen op de lokale computer opgehaald, met inbegrip van uitvoer bare bestanden in de paden van de omgevings variabele **Path** ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="30006-149">This command gets all commands of all types on the local computer, including executable files in the paths of the **Path** environment variable (`$env:path`).</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="30006-150">Er wordt een **ApplicationInfo** -object (System. Management. Automation. ApplicationInfo) geretourneerd voor elk bestand, niet een **file info** -object (System. io. file info).</span><span class="sxs-lookup"><span data-stu-id="30006-150">It returns an **ApplicationInfo** object (System.Management.Automation.ApplicationInfo) for each file, not a **FileInfo** object (System.IO.FileInfo).</span></span>

### <span data-ttu-id="30006-151">Voor beeld 9: cmdlets ophalen met behulp van de naam en het type van de para meter</span><span class="sxs-lookup"><span data-stu-id="30006-151">Example 9: Get cmdlets by using a parameter name and type</span></span>

<span data-ttu-id="30006-152">Met deze opdracht worden cmdlets opgehaald die een para meter hebben waarvan de naam auth bevat en waarvan het type **AuthenticationMechanism** is.</span><span class="sxs-lookup"><span data-stu-id="30006-152">This command gets cmdlets that have a parameter whose name includes Auth and whose type is **AuthenticationMechanism**.</span></span>

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

<span data-ttu-id="30006-153">U kunt een opdracht als deze gebruiken om cmdlets te vinden waarmee u de methode kunt opgeven die wordt gebruikt om de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="30006-153">You can use a command like this one to find cmdlets that let you specify the method that is used to authenticate the user.</span></span>

<span data-ttu-id="30006-154">De para meter **parameter type** onderscheidt para meters die een **AuthenticationMechanism** -waarde overnemen van de para meter **authenticationLevel** , zelfs wanneer deze vergelijk bare namen hebben.</span><span class="sxs-lookup"><span data-stu-id="30006-154">The **ParameterType** parameter distinguishes parameters that take an **AuthenticationMechanism** value from those that take an **AuthenticationLevel** parameter, even when they have similar names.</span></span>

### <span data-ttu-id="30006-155">Voor beeld 10: een alias ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-155">Example 10: Get an alias</span></span>

<span data-ttu-id="30006-156">In dit voor beeld ziet u hoe u de `Get-Command` cmdlet gebruikt met een alias.</span><span class="sxs-lookup"><span data-stu-id="30006-156">This example shows how to use the `Get-Command` cmdlet with an alias.</span></span>

```powershell
Get-Command -Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

<span data-ttu-id="30006-157">Hoewel dit doorgaans wordt gebruikt voor cmdlets en functies, worden `Get-Command` ook scripts, functies, aliassen en uitvoer bare bestanden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-157">Although it is typically used on cmdlets and functions, `Get-Command` also gets scripts, functions, aliases, and executable files.</span></span>

<span data-ttu-id="30006-158">In de uitvoer van de opdracht wordt de speciale weer gave van de **naam** eigenschaps waarde voor aliassen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="30006-158">The output of the command shows the special view of the **Name** property value for aliases.</span></span> <span data-ttu-id="30006-159">In de weer gave worden de alias en de volledige opdracht naam weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="30006-159">The view shows the alias and the full command name.</span></span>

### <span data-ttu-id="30006-160">Voor beeld 11: de syntaxis van een alias ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-160">Example 11: Get Syntax from an alias</span></span>

<span data-ttu-id="30006-161">In dit voor beeld ziet u hoe u de syntaxis krijgt, samen met de standaard naam van een alias.</span><span class="sxs-lookup"><span data-stu-id="30006-161">This example shows how to get the syntax along with the standard name of an alias.</span></span>

<span data-ttu-id="30006-162">De uitvoer van de opdracht toont de alias met het label met de standaard naam, gevolgd door de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="30006-162">The output of the command shows the labeled alias with the standard name, followed by the syntax.</span></span>

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="30006-163">Voor beeld 12: alle exemplaren van de opdracht Notepad ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-163">Example 12: Get all instances of the Notepad command</span></span>

<span data-ttu-id="30006-164">In dit voor beeld wordt de para meter **all** van de `Get-Command` cmdlet gebruikt om alle exemplaren van de `Notepad` opdracht op de lokale computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="30006-164">This example uses the **All** parameter of the `Get-Command` cmdlet to show all instances of the `Notepad` command on the local computer.</span></span>

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

<span data-ttu-id="30006-165">De para meter **all** is handig wanneer er meer dan één opdracht is met dezelfde naam in de sessie.</span><span class="sxs-lookup"><span data-stu-id="30006-165">The **All** parameter is useful when there is more than one command with the same name in the session.</span></span>

<span data-ttu-id="30006-166">Vanaf Windows Power Shell 3,0 wordt standaard, wanneer de sessie meerdere opdrachten met dezelfde naam bevat, `Get-Command` alleen de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="30006-166">Beginning in Windows PowerShell 3.0, by default, when the session includes multiple commands with the same name, `Get-Command` gets only the command that runs when you type the command name.</span></span> <span data-ttu-id="30006-167">Met de **alle** para meters worden `Get-Command` alle opdrachten met de opgegeven naam opgehaald en worden deze in volg orde van uitvoerings volgorde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="30006-167">With the **All** parameter, `Get-Command` gets all commands with the specified name and returns them in execution precedence order.</span></span> <span data-ttu-id="30006-168">Als u een andere opdracht dan de eerste uit de lijst wilt uitvoeren, typt u het volledig gekwalificeerde pad naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="30006-168">To run a command other than the first one in the list, type the fully qualified path to the command.</span></span>

<span data-ttu-id="30006-169">Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de rang orde van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="30006-169">For more information about command precedence, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="30006-170">Voor beeld 13: de naam van een module met een cmdlet ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-170">Example 13: Get the name of a module that contains a cmdlet</span></span>

<span data-ttu-id="30006-171">Met deze opdracht wordt de naam opgehaald van de module waarin de `Get-Date` cmdlet afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="30006-171">This command gets the name of the module in which the `Get-Date` cmdlet originated.</span></span>
<span data-ttu-id="30006-172">De opdracht maakt gebruik van **de eigenschap PropertyName** van alle opdrachten.</span><span class="sxs-lookup"><span data-stu-id="30006-172">The command uses the **ModuleName** property of all commands.</span></span>

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

<span data-ttu-id="30006-173">Deze opdracht indeling werkt op opdrachten in Power shell-modules, zelfs als deze niet in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="30006-173">This command format works on commands in PowerShell modules, even if they are not imported into the session.</span></span>

### <span data-ttu-id="30006-174">Voor beeld 14: cmdlets en functies met een uitvoer type ophalen</span><span class="sxs-lookup"><span data-stu-id="30006-174">Example 14: Get cmdlets and functions that have an output type</span></span>

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

<span data-ttu-id="30006-175">Met deze opdracht worden de cmdlets en functies opgehaald die een uitvoer type hebben en het type objecten dat ze retour neren.</span><span class="sxs-lookup"><span data-stu-id="30006-175">This command gets the cmdlets and functions that have an output type and the type of objects that they return.</span></span>

<span data-ttu-id="30006-176">Het eerste deel van de opdracht haalt alle cmdlets op.</span><span class="sxs-lookup"><span data-stu-id="30006-176">The first part of the command gets all cmdlets.</span></span> <span data-ttu-id="30006-177">Een pijplijn operator ( `|` ) verzendt de-cmdlets naar de `Where-Object` cmdlet, waarmee alleen de waarden worden geselecteerd waarin de eigenschap **output** type wordt ingevuld.</span><span class="sxs-lookup"><span data-stu-id="30006-177">A pipeline operator (`|`) sends the cmdlets to the `Where-Object` cmdlet, which selects only the ones in which the **OutputType** property is populated.</span></span> <span data-ttu-id="30006-178">Een andere pijplijn operator verzendt de geselecteerde cmdlet-objecten naar de `Format-List` cmdlet, waarin de naam en het uitvoer type van elke cmdlet in een lijst worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="30006-178">Another pipeline operator sends the selected cmdlet objects to the `Format-List` cmdlet, which displays the name and output type of each cmdlet in a list.</span></span>

<span data-ttu-id="30006-179">De eigenschap **output** type van een **CommandInfo** -object heeft alleen een waarde die niet null is wanneer de cmdlet code het kenmerk **output** type voor de cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="30006-179">The **OutputType** property of a **CommandInfo** object has a non-null value only when the cmdlet code defines the **OutputType** attribute for the cmdlet.</span></span>

### <span data-ttu-id="30006-180">Voor beeld 15: cmdlets ophalen die een specifiek object type als invoer hebben</span><span class="sxs-lookup"><span data-stu-id="30006-180">Example 15: Get cmdlets that take a specific object type as input</span></span>

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

<span data-ttu-id="30006-181">Met deze opdracht vindt u cmdlets die net-adapter objecten als invoer hebben.</span><span class="sxs-lookup"><span data-stu-id="30006-181">This command finds cmdlets that take net adapter objects as input.</span></span> <span data-ttu-id="30006-182">U kunt deze opdracht indeling gebruiken om de cmdlets te vinden die het type objecten accepteren dat door een opdracht wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="30006-182">You can use this command format to find the cmdlets that accept the type of objects that any command returns.</span></span>

<span data-ttu-id="30006-183">De opdracht maakt gebruik van de intrinsieke eigenschap **PSTypeNames** van alle objecten, waarmee de typen worden opgehaald die het object beschrijven.</span><span class="sxs-lookup"><span data-stu-id="30006-183">The command uses the **PSTypeNames** intrinsic property of all objects, which gets the types that describe the object.</span></span> <span data-ttu-id="30006-184">Als u de eigenschap **PSTypeNames** van een netwerk adapter wilt ophalen en niet de eigenschap **PSTypeNames** van een verzameling netwerk adapters, gebruikt de opdracht matrix notatie om de eerste netadapter op te halen die door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="30006-184">To get the **PSTypeNames** property of a net adapter, and not the **PSTypeNames** property of a collection of net adapters, the command uses array notation to get the first net adapter that the cmdlet returns.</span></span>

### <span data-ttu-id="30006-185">Voor beeld 16: opdrachten ophalen met behulp van een benadering van het Zoek resultaat</span><span class="sxs-lookup"><span data-stu-id="30006-185">Example 16: Get commands using a fuzzy match</span></span>

<span data-ttu-id="30006-186">In dit voor beeld heeft de naam van de opdracht opzettelijk een type ' Get-commnd '.</span><span class="sxs-lookup"><span data-stu-id="30006-186">In this example, the name of the command deliberately has a typo as 'get-commnd'.</span></span>
<span data-ttu-id="30006-187">Met behulp van de `-UseFuzzyMatching` Switch heeft de cmdlet bepaald dat het beste resultaat werd `Get-Command` gevolgd door andere systeem eigen opdrachten op het systeem die een vergelijk bare overeenkomst hebben.</span><span class="sxs-lookup"><span data-stu-id="30006-187">Using the `-UseFuzzyMatching` switch, the cmdlet determined that the best match was `Get-Command` followed by other native commands on the system that were a similar match.</span></span>

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

## <span data-ttu-id="30006-188">Parameters</span><span class="sxs-lookup"><span data-stu-id="30006-188">Parameters</span></span>

### <span data-ttu-id="30006-189">-Alle</span><span class="sxs-lookup"><span data-stu-id="30006-189">-All</span></span>

<span data-ttu-id="30006-190">Geeft aan dat met deze cmdlet alle opdrachten worden opgehaald, met inbegrip van opdrachten van hetzelfde type die dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="30006-190">Indicates that this cmdlet gets all commands, including commands of the same type that have the same name.</span></span> <span data-ttu-id="30006-191">Standaard worden `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="30006-191">By default, `Get-Command` gets only the commands that run when you type the command name.</span></span>

<span data-ttu-id="30006-192">Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de methode die door Power shell wordt gebruikt voor het selecteren van de opdracht die moet worden uitgevoerd wanneer meerdere opdrachten dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="30006-192">For more information about the method that PowerShell uses to select the command to run when multiple commands have the same name, see [about_Command_Precedence](About/about_Command_Precedence.md).</span></span>
<span data-ttu-id="30006-193">Zie [about_Modules](About/about_Modules.md)voor meer informatie over opdracht namen in de module en het uitvoeren van opdrachten die niet standaard worden uitgevoerd vanwege een naam conflict.</span><span class="sxs-lookup"><span data-stu-id="30006-193">For information about module-qualified command names and running commands that do not run by default because of a name conflict, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="30006-194">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="30006-194">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="30006-195">In Windows Power Shell 2,0 worden `Get-Command` alle opdrachten standaard opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-195">In Windows PowerShell 2.0, `Get-Command` gets all commands by default.</span></span>

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

### <span data-ttu-id="30006-196">-Argument List</span><span class="sxs-lookup"><span data-stu-id="30006-196">-ArgumentList</span></span>

<span data-ttu-id="30006-197">Hiermee wordt een matrix met argumenten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="30006-197">Specifies an array of arguments.</span></span> <span data-ttu-id="30006-198">Met deze cmdlet wordt informatie opgehaald over een cmdlet of functie wanneer deze wordt gebruikt met de opgegeven para meters ("argumenten").</span><span class="sxs-lookup"><span data-stu-id="30006-198">This cmdlet gets information about a cmdlet or function when it is used with the specified parameters ("arguments").</span></span> <span data-ttu-id="30006-199">De alias voor **argument List** is **args**.</span><span class="sxs-lookup"><span data-stu-id="30006-199">The alias for **ArgumentList** is **Args**.</span></span>

<span data-ttu-id="30006-200">Als u dynamische para meters wilt detecteren die alleen beschikbaar zijn wanneer bepaalde andere para meters worden gebruikt, stelt u de waarde van **argument List** in op de para meters die de dynamische para meters activeren.</span><span class="sxs-lookup"><span data-stu-id="30006-200">To detect dynamic parameters that are available only when certain other parameters are used, set the value of **ArgumentList** to the parameters that trigger the dynamic parameters.</span></span>

<span data-ttu-id="30006-201">Als u de dynamische para meters wilt detecteren die een provider aan een cmdlet toevoegt, stelt u de waarde van de para meter **argument List** in op een pad in het provider station, zoals WSMan:, HKLM: of CERT:.</span><span class="sxs-lookup"><span data-stu-id="30006-201">To detect the dynamic parameters that a provider adds to a cmdlet, set the value of the **ArgumentList** parameter to a path in the provider drive, such as WSMan:, HKLM:, or Cert:.</span></span> <span data-ttu-id="30006-202">Wanneer de opdracht een Power shell-provider-cmdlet is, voert u slechts één pad in elke opdracht in.</span><span class="sxs-lookup"><span data-stu-id="30006-202">When the command is a PowerShell provider cmdlet, enter only one path in each command.</span></span> <span data-ttu-id="30006-203">De provider-cmdlets retour neren alleen de dynamische para meters voor het eerste pad de waarde van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="30006-203">The provider cmdlets return only the dynamic parameters for the first path the value of **ArgumentList**.</span></span> <span data-ttu-id="30006-204">Zie [about_Providers](About/about_Providers.md)voor meer informatie over de provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="30006-204">For information about the provider cmdlets, see [about_Providers](About/about_Providers.md).</span></span>

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

### <span data-ttu-id="30006-205">-CommandType</span><span class="sxs-lookup"><span data-stu-id="30006-205">-CommandType</span></span>

<span data-ttu-id="30006-206">Hiermee geeft u de typen opdrachten op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-206">Specifies the types of commands that this cmdlet gets.</span></span> <span data-ttu-id="30006-207">Voer een of meer opdracht typen in.</span><span class="sxs-lookup"><span data-stu-id="30006-207">Enter one or more command types.</span></span> <span data-ttu-id="30006-208">Gebruik **CommandType** of de alias, **Typ**.</span><span class="sxs-lookup"><span data-stu-id="30006-208">Use **CommandType** or its alias, **Type**.</span></span> <span data-ttu-id="30006-209">Hiermee worden standaard `Get-Command` Alle cmdlets, functies en aliassen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-209">By default, `Get-Command` gets all cmdlets, functions, and aliases.</span></span>

<span data-ttu-id="30006-210">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="30006-210">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="30006-211">`Alias`: Hiermee worden de aliassen van alle Power shell-opdrachten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-211">`Alias`: Gets the aliases of all PowerShell commands.</span></span> <span data-ttu-id="30006-212">Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30006-212">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>
- <span data-ttu-id="30006-213">`All`: Hiermee worden alle opdracht typen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-213">`All`: Gets all command types.</span></span> <span data-ttu-id="30006-214">Deze parameter waarde is gelijk aan `Get-Command *` .</span><span class="sxs-lookup"><span data-stu-id="30006-214">This parameter value is the equivalent of `Get-Command *`.</span></span>
- <span data-ttu-id="30006-215">`Application`: Hiermee worden niet-Power Shell-bestanden in paden weer gegeven in de omgevings variabele **Path** ( `$env:path` ), inclusief. txt,. exe en. dll-bestanden.</span><span class="sxs-lookup"><span data-stu-id="30006-215">`Application`: Gets non-PowerShell files in paths listed in the **Path** environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span> <span data-ttu-id="30006-216">Zie [about_Environment_Variables](About/about_Environment_Variables.md)voor meer informatie over de omgevings variabele **Path** .</span><span class="sxs-lookup"><span data-stu-id="30006-216">For more information about the **Path** environment variable, see [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>
- <span data-ttu-id="30006-217">`Cmdlet`: Hiermee worden alle cmdlets opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-217">`Cmdlet`: Gets all cmdlets.</span></span>
- <span data-ttu-id="30006-218">`ExternalScript`: Hiermee worden alle. ps1-bestanden opgehaald uit de paden die worden weer gegeven in de **Path** -omgevings variabele ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="30006-218">`ExternalScript`: Gets all .ps1 files in the paths listed in the **Path** environment variable (`$env:path`).</span></span>
- <span data-ttu-id="30006-219">`Filter` en `Function` : haalt alle geavanceerde en eenvoudige Power shell-functies en-filters op.</span><span class="sxs-lookup"><span data-stu-id="30006-219">`Filter` and `Function`: Gets all PowerShell advanced and simple functions and filters.</span></span>
- <span data-ttu-id="30006-220">`Script`: Hiermee worden alle script blokken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-220">`Script`: Gets all script blocks.</span></span> <span data-ttu-id="30006-221">Als u Power shell-scripts (. ps1-bestanden) wilt ophalen, gebruikt u de `ExternalScript` waarde.</span><span class="sxs-lookup"><span data-stu-id="30006-221">To get PowerShell scripts (.ps1 files), use the `ExternalScript` value.</span></span>

<span data-ttu-id="30006-222">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="30006-222">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="30006-223">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="30006-223">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="30006-224">De waarden kunnen worden door gegeven aan de **CommandType** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="30006-224">The values can be passed to the **CommandType** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="30006-225">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="30006-225">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="30006-226">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="30006-226">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

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

### <span data-ttu-id="30006-227">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="30006-227">-FullyQualifiedModule</span></span>

<span data-ttu-id="30006-228">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten, zoals beschreven in de sectie **opmerkingen** van [ModuleSpecification constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="30006-228">Specifies modules with names that are specified in the form of **ModuleSpecification** objects, described in the **Remarks** section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="30006-229">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="30006-229">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in one of the following formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="30006-230">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="30006-230">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="30006-231">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="30006-231">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="30006-232">De twee para meters sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="30006-232">The two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="30006-233">-ListImported</span><span class="sxs-lookup"><span data-stu-id="30006-233">-ListImported</span></span>

<span data-ttu-id="30006-234">Geeft aan dat met deze cmdlet alleen opdrachten in de huidige sessie worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-234">Indicates that this cmdlet gets only commands in the current session.</span></span>

<span data-ttu-id="30006-235">Vanaf Power Shell 3,0 worden standaard `Get-Command` alle geïnstalleerde opdrachten opgehaald, inclusief, maar niet beperkt tot, de opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="30006-235">Starting in PowerShell 3.0, by default, `Get-Command` gets all installed commands, including, but not limited to, the commands in the current session.</span></span> <span data-ttu-id="30006-236">In Power Shell 2,0 worden alleen opdrachten in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-236">In PowerShell 2.0, it gets only commands in the current session.</span></span>

<span data-ttu-id="30006-237">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="30006-237">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="30006-238">-Module</span><span class="sxs-lookup"><span data-stu-id="30006-238">-Module</span></span>

<span data-ttu-id="30006-239">Hiermee geeft u een matrix met modules op.</span><span class="sxs-lookup"><span data-stu-id="30006-239">Specifies an array of modules.</span></span> <span data-ttu-id="30006-240">Met deze cmdlet worden de opdrachten opgehaald die afkomstig zijn van de opgegeven modules.</span><span class="sxs-lookup"><span data-stu-id="30006-240">This cmdlet gets the commands that came from the specified modules.</span></span>
<span data-ttu-id="30006-241">Voer de namen in van modules of module-objecten.</span><span class="sxs-lookup"><span data-stu-id="30006-241">Enter the names of modules or module objects.</span></span>

<span data-ttu-id="30006-242">Deze para meter neemt teken reeks waarden, maar de waarde van deze para meter kan ook een **PSModuleInfo** -object zijn, zoals de objecten die de `Get-Module` en `Import-PSSession` cmdlets retour neren.</span><span class="sxs-lookup"><span data-stu-id="30006-242">This parameter takes string values, but the value of this parameter can also be a **PSModuleInfo** object, such as the objects that the `Get-Module` and `Import-PSSession` cmdlets return.</span></span>

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

### <span data-ttu-id="30006-243">-Name</span><span class="sxs-lookup"><span data-stu-id="30006-243">-Name</span></span>

<span data-ttu-id="30006-244">Hiermee geeft u een matrix met namen op.</span><span class="sxs-lookup"><span data-stu-id="30006-244">Specifies an array of names.</span></span> <span data-ttu-id="30006-245">Met deze cmdlet worden alleen opdrachten met de opgegeven naam opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-245">This cmdlet gets only commands that have the specified name.</span></span> <span data-ttu-id="30006-246">Voer een naam of naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="30006-246">Enter a name or name pattern.</span></span> <span data-ttu-id="30006-247">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="30006-247">Wildcard characters are permitted.</span></span>

<span data-ttu-id="30006-248">Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** .</span><span class="sxs-lookup"><span data-stu-id="30006-248">To get commands that have the same name, use the **All** parameter.</span></span> <span data-ttu-id="30006-249">Wanneer twee opdrachten dezelfde naam hebben, `Get-Command` wordt standaard de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="30006-249">When two commands have the same name, by default, `Get-Command` gets the command that runs when you type the command name.</span></span>

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

### <span data-ttu-id="30006-250">-Zelfstandig naam woord</span><span class="sxs-lookup"><span data-stu-id="30006-250">-Noun</span></span>

<span data-ttu-id="30006-251">Hiermee geeft u een matrix met de naam van de opdracht op.</span><span class="sxs-lookup"><span data-stu-id="30006-251">Specifies an array of command nouns.</span></span> <span data-ttu-id="30006-252">Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die het opgegeven zelfstandig naam woord bevatten.</span><span class="sxs-lookup"><span data-stu-id="30006-252">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified noun.</span></span> <span data-ttu-id="30006-253">Voer een of meer zelfstandige naam woorden of een zelfstandige naam op.</span><span class="sxs-lookup"><span data-stu-id="30006-253">Enter one or more nouns or noun patterns.</span></span> <span data-ttu-id="30006-254">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="30006-254">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="30006-255">-Para meternaam</span><span class="sxs-lookup"><span data-stu-id="30006-255">-ParameterName</span></span>

<span data-ttu-id="30006-256">Hiermee geeft u een matrix met parameter namen op.</span><span class="sxs-lookup"><span data-stu-id="30006-256">Specifies an array of parameter names.</span></span> <span data-ttu-id="30006-257">Met deze cmdlet worden opdrachten in de sessie met de opgegeven para meters opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-257">This cmdlet gets commands in the session that have the specified parameters.</span></span> <span data-ttu-id="30006-258">Voer parameter namen of parameter aliassen in.</span><span class="sxs-lookup"><span data-stu-id="30006-258">Enter parameter names or parameter aliases.</span></span> <span data-ttu-id="30006-259">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="30006-259">Wildcard characters are supported.</span></span>

<span data-ttu-id="30006-260">Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.</span><span class="sxs-lookup"><span data-stu-id="30006-260">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="30006-261">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="30006-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="30006-262">-Parameter type</span><span class="sxs-lookup"><span data-stu-id="30006-262">-ParameterType</span></span>

<span data-ttu-id="30006-263">Hiermee geeft u een matrix met parameter namen op.</span><span class="sxs-lookup"><span data-stu-id="30006-263">Specifies an array of parameter names.</span></span> <span data-ttu-id="30006-264">Deze cmdlet haalt opdrachten op in de sessie die para meters van het opgegeven type hebben.</span><span class="sxs-lookup"><span data-stu-id="30006-264">This cmdlet gets commands in the session that have parameters of the specified type.</span></span> <span data-ttu-id="30006-265">Voer de volledige naam of gedeeltelijke naam van een parameter type in.</span><span class="sxs-lookup"><span data-stu-id="30006-265">Enter the full name or partial name of a parameter type.</span></span> <span data-ttu-id="30006-266">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="30006-266">Wildcard characters are supported.</span></span>

<span data-ttu-id="30006-267">Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.</span><span class="sxs-lookup"><span data-stu-id="30006-267">The **ParameterName** and **ParameterType** parameters search only commands in the current session.</span></span>

<span data-ttu-id="30006-268">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="30006-268">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="30006-269">-ShowCommandInfo</span><span class="sxs-lookup"><span data-stu-id="30006-269">-ShowCommandInfo</span></span>

<span data-ttu-id="30006-270">Geeft aan dat met deze cmdlet opdracht gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="30006-270">Indicates that this cmdlet displays command information.</span></span>

<span data-ttu-id="30006-271">Deze para meter is geïntroduceerd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="30006-271">This parameter was introduced in Windows PowerShell 5.0.</span></span>

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

### <span data-ttu-id="30006-272">-Syntaxis</span><span class="sxs-lookup"><span data-stu-id="30006-272">-Syntax</span></span>

<span data-ttu-id="30006-273">Geeft aan dat met deze cmdlet alleen de volgende opgegeven gegevens over de opdracht worden opgehaald:</span><span class="sxs-lookup"><span data-stu-id="30006-273">Indicates that this cmdlet gets only the following specified data about the command:</span></span>

- <span data-ttu-id="30006-274">Aliassen.</span><span class="sxs-lookup"><span data-stu-id="30006-274">Aliases.</span></span> <span data-ttu-id="30006-275">Hiermee haalt u de standaard naam en syntaxis op.</span><span class="sxs-lookup"><span data-stu-id="30006-275">Gets the standard name and syntax.</span></span>
- <span data-ttu-id="30006-276">Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="30006-276">Cmdlets.</span></span> <span data-ttu-id="30006-277">Hiermee wordt de syntaxis opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-277">Gets the syntax.</span></span>
- <span data-ttu-id="30006-278">Functies en filters.</span><span class="sxs-lookup"><span data-stu-id="30006-278">Functions and filters.</span></span> <span data-ttu-id="30006-279">Hiermee wordt de functie definitie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-279">Gets the function definition.</span></span>
- <span data-ttu-id="30006-280">Scripts en toepassingen of bestanden.</span><span class="sxs-lookup"><span data-stu-id="30006-280">Scripts and applications or files.</span></span> <span data-ttu-id="30006-281">Hiermee haalt u het pad en de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="30006-281">Gets the path and filename.</span></span>

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

### <span data-ttu-id="30006-282">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="30006-282">-TotalCount</span></span>

<span data-ttu-id="30006-283">Hiermee geeft u het aantal opdrachten op dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-283">Specifies the number of commands to get.</span></span> <span data-ttu-id="30006-284">U kunt deze para meter gebruiken om de uitvoer van een opdracht te beperken.</span><span class="sxs-lookup"><span data-stu-id="30006-284">You can use this parameter to limit the output of a command.</span></span>

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

### <span data-ttu-id="30006-285">-UseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="30006-285">-UseAbbreviationExpansion</span></span>

<span data-ttu-id="30006-286">Hiermee wordt aangegeven dat overeenkomende tekens in de opdracht wordt gebruikt om te zoeken naar hoofd letters in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="30006-286">Indicates using matching of the characters in the command to find with uppercase characters in a command.</span></span> <span data-ttu-id="30006-287">Bijvoorbeeld, `i-psdf` komt overeen met `Import-PowerShellDataFile` de zoek tekens die overeenkomen met een hoofd letter in het resultaat.</span><span class="sxs-lookup"><span data-stu-id="30006-287">For example, `i-psdf` would match `Import-PowerShellDataFile` as each of the characters to find matches an uppercase character in the result.</span></span> <span data-ttu-id="30006-288">Wanneer dit type overeenkomst wordt gebruikt, hebben joker tekens geen overeenkomstige resultaten.</span><span class="sxs-lookup"><span data-stu-id="30006-288">When using this type of match, any wildcards will result in no matches.</span></span>

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

### <span data-ttu-id="30006-289">-UseFuzzyMatching</span><span class="sxs-lookup"><span data-stu-id="30006-289">-UseFuzzyMatching</span></span>

<span data-ttu-id="30006-290">Geeft aan dat er een matching-algoritme wordt gebruikt bij het zoeken van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="30006-290">Indicates using a fuzzy matching algorithm when finding commands.</span></span> <span data-ttu-id="30006-291">De volg orde van de uitvoer is van het meest overeenkomende resultaat dat overeenkomt met de minst waarschijnlijke overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="30006-291">The order of the output is from closest match to least likely match.</span></span> <span data-ttu-id="30006-292">Joker tekens mogen niet worden gebruikt met fuzzy match, omdat er wordt geprobeerd opdrachten te vinden die deze Joker tekens kunnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="30006-292">Wildcards should not be used with fuzzy matching as it will attempt to match commands that may contain those wildcard characters.</span></span>

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

### <span data-ttu-id="30006-293">-Verb</span><span class="sxs-lookup"><span data-stu-id="30006-293">-Verb</span></span>

<span data-ttu-id="30006-294">Hiermee geeft u een matrix met opdracht woorden op.</span><span class="sxs-lookup"><span data-stu-id="30006-294">Specifies an array of command verbs.</span></span> <span data-ttu-id="30006-295">Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die de opgegeven term bevatten.</span><span class="sxs-lookup"><span data-stu-id="30006-295">This cmdlet gets commands, which include cmdlets, functions, and aliases, that have names that include the specified verb.</span></span> <span data-ttu-id="30006-296">Voer een of meer woorden of woord patronen in.</span><span class="sxs-lookup"><span data-stu-id="30006-296">Enter one or more verbs or verb patterns.</span></span> <span data-ttu-id="30006-297">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="30006-297">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="30006-298">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30006-298">CommonParameters</span></span>

<span data-ttu-id="30006-299">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30006-299">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30006-300">Zie [about_CommonParameters](About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30006-300">For more information, see [about_CommonParameters](About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="30006-301">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="30006-301">Inputs</span></span>

### <span data-ttu-id="30006-302">System. String</span><span class="sxs-lookup"><span data-stu-id="30006-302">System.String</span></span>

<span data-ttu-id="30006-303">U kunt opdracht namen door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30006-303">You can pipe command names to this cmdlet.</span></span>

## <span data-ttu-id="30006-304">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="30006-304">Outputs</span></span>

### <span data-ttu-id="30006-305">System. Management. Automation. CommandInfo</span><span class="sxs-lookup"><span data-stu-id="30006-305">System.Management.Automation.CommandInfo</span></span>

<span data-ttu-id="30006-306">Deze cmdlet retourneert objecten die zijn afgeleid van de **CommandInfo** -klasse.</span><span class="sxs-lookup"><span data-stu-id="30006-306">This cmdlet returns objects derived from the **CommandInfo** class.</span></span> <span data-ttu-id="30006-307">Het type van het object dat wordt geretourneerd, is afhankelijk van het type opdracht dat `Get-Command` wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="30006-307">The type of object that is returned depends on the type of command that `Get-Command` gets.</span></span>

### <span data-ttu-id="30006-308">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="30006-308">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="30006-309">Vertegenwoordigt aliassen.</span><span class="sxs-lookup"><span data-stu-id="30006-309">Represents aliases.</span></span>

### <span data-ttu-id="30006-310">System. Management. Automation. ApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="30006-310">System.Management.Automation.ApplicationInfo</span></span>

<span data-ttu-id="30006-311">Hiermee worden toepassingen en bestanden aangeduid.</span><span class="sxs-lookup"><span data-stu-id="30006-311">Represents applications and files.</span></span>

### <span data-ttu-id="30006-312">System. Management. Automation. CmdletInfo</span><span class="sxs-lookup"><span data-stu-id="30006-312">System.Management.Automation.CmdletInfo</span></span>

<span data-ttu-id="30006-313">Vertegenwoordigt cmdlets.</span><span class="sxs-lookup"><span data-stu-id="30006-313">Represents cmdlets.</span></span>

### <span data-ttu-id="30006-314">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="30006-314">System.Management.Automation.FunctionInfo</span></span>

<span data-ttu-id="30006-315">Hiermee worden functies en filters aangeduid.</span><span class="sxs-lookup"><span data-stu-id="30006-315">Represents functions and filters.</span></span>

## <span data-ttu-id="30006-316">Notities</span><span class="sxs-lookup"><span data-stu-id="30006-316">Notes</span></span>

- <span data-ttu-id="30006-317">Wanneer er meer dan één opdracht met dezelfde naam beschikbaar is voor de sessie, `Get-Command` wordt de opdracht weer gegeven die wordt uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="30006-317">When more than one command that has the same name is available to the session, `Get-Command` returns the command that runs when you type the command name.</span></span> <span data-ttu-id="30006-318">Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** in volg orde uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="30006-318">To get commands that have the same name, listed in run order, use the **All** parameter.</span></span> <span data-ttu-id="30006-319">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30006-319">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>
- <span data-ttu-id="30006-320">Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30006-320">When a module is imported automatically, the effect is the same as using the `Import-Module` cmdlet.</span></span> <span data-ttu-id="30006-321">De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="30006-321">The module can add commands, types and formatting files, and run scripts in the session.</span></span>
  <span data-ttu-id="30006-322">Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="30006-322">To enable, disable, and configuration automatic importing of modules, use the `$PSModuleAutoLoadingPreference` preference variable.</span></span> <span data-ttu-id="30006-323">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="30006-323">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="30006-324">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="30006-324">Related Links</span></span>

[<span data-ttu-id="30006-325">Exporteren-PSSession</span><span class="sxs-lookup"><span data-stu-id="30006-325">Export-PSSession</span></span>](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[<span data-ttu-id="30006-326">Get-Help</span><span class="sxs-lookup"><span data-stu-id="30006-326">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="30006-327">Get-member</span><span class="sxs-lookup"><span data-stu-id="30006-327">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="30006-328">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="30006-328">Get-PSDrive</span></span>](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[<span data-ttu-id="30006-329">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="30006-329">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="30006-330">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="30006-330">about_Command_Precedence</span></span>](About/about_Command_Precedence.md)
