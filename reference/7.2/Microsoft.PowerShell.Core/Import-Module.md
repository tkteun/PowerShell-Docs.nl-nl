---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 1b8164be05f011e13945323a6288426bd2d41183
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564490"
---
# <span data-ttu-id="b0fbe-102">Import-Module</span><span class="sxs-lookup"><span data-stu-id="b0fbe-102">Import-Module</span></span>

## <span data-ttu-id="b0fbe-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b0fbe-103">SYNOPSIS</span></span>
<span data-ttu-id="b0fbe-104">Hiermee voegt u modules toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-104">Adds modules to the current session.</span></span>

## <span data-ttu-id="b0fbe-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b0fbe-105">SYNTAX</span></span>

### <span data-ttu-id="b0fbe-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="b0fbe-106">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-107">PSSession</span><span class="sxs-lookup"><span data-stu-id="b0fbe-107">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-108">CimSession</span><span class="sxs-lookup"><span data-stu-id="b0fbe-108">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-109">UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="b0fbe-109">UseWindowsPowerShell</span></span>

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-110">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b0fbe-110">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-111">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="b0fbe-111">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-112">FullyQualifiedNameAndUseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="b0fbe-112">FullyQualifiedNameAndUseWindowsPowerShell</span></span>

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-113">Assembly</span><span class="sxs-lookup"><span data-stu-id="b0fbe-113">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="b0fbe-114">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="b0fbe-114">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="b0fbe-115">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b0fbe-115">DESCRIPTION</span></span>

<span data-ttu-id="b0fbe-116">De `Import-Module` cmdlet voegt een of meer modules toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-116">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="b0fbe-117">Vanaf Power Shell 3,0 worden geïnstalleerde modules automatisch geïmporteerd in de sessie wanneer u opdrachten of providers in de module gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-117">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="b0fbe-118">U kunt echter nog steeds de `Import-Module` opdracht gebruiken om een module te importeren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-118">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="b0fbe-119">U kunt het automatisch importeren van modules uitschakelen met behulp van de `$PSModuleAutoloadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-119">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="b0fbe-120">Zie about_Preference_Variables voor meer informatie over de `$PSModuleAutoloadingPreference` variabele [](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b0fbe-120">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="b0fbe-121">Een module is een pakket dat leden bevat die kunnen worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-121">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="b0fbe-122">Leden zijn onder andere cmdlets, providers, scripts, functies, variabelen en andere hulpprogram ma's en bestanden.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-122">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="b0fbe-123">Nadat een module is geïmporteerd, kunt u de module leden in uw sessie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-123">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="b0fbe-124">Zie [about_Modules](About/about_Modules.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-124">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="b0fbe-125">Standaard worden `Import-Module` alle leden geïmporteerd die de module exporteert, maar u kunt de para meters **alias**, **Function**, **cmdlet** en **Variable** gebruiken om te beperken welke leden worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-125">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias**, **Function**, **Cmdlet**, and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="b0fbe-126">Met de para meter **NoClobber** wordt voor komen dat `Import-Module` leden met dezelfde namen als leden in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-126">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="b0fbe-127">`Import-Module` Hiermee wordt een module alleen in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-127">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="b0fbe-128">Als u de module wilt importeren in elke nieuwe sessie, voegt `Import-Module` u een opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-128">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="b0fbe-129">Zie [about_Profiles](About/about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-129">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="b0fbe-130">U kunt externe Windows-computers waarvoor Power shell Remoting is ingeschakeld, beheren door een **PSSession** te maken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-130">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="b0fbe-131">Gebruik vervolgens de para meter **PSSession** van `Import-Module` om de modules te importeren die zijn geïnstalleerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-131">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="b0fbe-132">Wanneer u de geïmporteerde opdrachten in de huidige sessie gebruikt, worden de opdrachten impliciet uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-132">When you use the imported commands in the current session the commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="b0fbe-133">Vanuit Windows Power Shell 3,0 kunt u gebruiken `Import-Module` om Common Information Model-modules (CIM) te importeren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-133">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="b0fbe-134">Met CIM-modules worden cmdlets in CDXML-bestanden (cmdlet definition XML) gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-134">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="b0fbe-135">Met deze functie kunt u cmdlets gebruiken die zijn geïmplementeerd in niet-beheerde code-assembly's, zoals die zijn geschreven in C++.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-135">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="b0fbe-136">Voor externe computers waarvoor geen externe communicatie van Power shell is ingeschakeld, met inbegrip van computers waarop het Windows-besturings systeem niet wordt uitgevoerd, kunt u de para meter **CIMSession** van gebruiken `Import-Module` voor het importeren van CIM-modules van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-136">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="b0fbe-137">De geïmporteerde opdrachten worden impliciet uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-137">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="b0fbe-138">Een **CIMSession** is een verbinding met Windows Management INSTRUMENTATION (WMI) op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-138">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="b0fbe-139">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b0fbe-139">EXAMPLES</span></span>

### <span data-ttu-id="b0fbe-140">Voor beeld 1: de leden van een module importeren in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="b0fbe-140">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="b0fbe-141">In dit voor beeld worden de leden van de module **PSDiagnostics** in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-141">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="b0fbe-142">Voor beeld 2: alle modules importeren die zijn opgegeven in het pad naar de module</span><span class="sxs-lookup"><span data-stu-id="b0fbe-142">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="b0fbe-143">In dit voor beeld worden alle beschik bare modules in het pad dat door de `$env:PSModulePath` omgevings variabele is opgegeven, in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-143">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="b0fbe-144">Voor beeld 3: de leden van verschillende modules importeren in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="b0fbe-144">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="b0fbe-145">In dit voor beeld worden de leden van de **PSDiagnostics** -en **DISM** -modules in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-145">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="b0fbe-146">De `Get-Module` cmdlet haalt de **PSDiagnostics** -en **DISM** -modules op en slaat de objecten op in de `$m` variabele.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-146">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="b0fbe-147">De para meter **ListAvailable** is vereist als u modules gaat ophalen die nog niet in de sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-147">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="b0fbe-148">De para meter **ModuleInfo** van `Import-Module` wordt gebruikt voor het importeren van de modules in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-148">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="b0fbe-149">Voor beeld 4: alle modules importeren die zijn opgegeven met een pad</span><span class="sxs-lookup"><span data-stu-id="b0fbe-149">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="b0fbe-150">In dit voor beeld wordt een expliciet pad gebruikt om te bepalen welke module moet worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-150">This example uses an explicit path to identify the module to import.</span></span>

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

<span data-ttu-id="b0fbe-151">Het gebruik van de **uitgebreide** para meter zorgt ervoor dat `Import-Module` de voortgang wordt gerapporteerd bij het laden van de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-151">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="b0fbe-152">Zonder de para meter **uitgebreid**, **PassThru** of **AsCustomObject** wordt geen `Import-Module` uitvoer gegenereerd wanneer een module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-152">Without the **Verbose**, **PassThru**, or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="b0fbe-153">Voor beeld 5: module leden beperken die in een sessie zijn geïmporteerd</span><span class="sxs-lookup"><span data-stu-id="b0fbe-153">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="b0fbe-154">In dit voor beeld ziet u hoe u kunt beperken welke module leden in de sessie worden geïmporteerd en wat het effect van deze opdracht voor de sessie is.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-154">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="b0fbe-155">De **functie** parameter beperkt de leden die worden geïmporteerd uit de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-155">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="b0fbe-156">U kunt ook de para meters **alias**, **variabele** en **cmdlet** gebruiken om andere leden te beperken die door de module worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-156">You can also use the **Alias**, **Variable**, and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="b0fbe-157">De `Get-Module` cmdlet haalt het object op dat de module **PSDiagnostics** vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-157">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="b0fbe-158">De eigenschap **ExportedCmdlets** geeft een lijst van alle cmdlets die de module exporteert, ook al zijn ze niet allemaal geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-158">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

<span data-ttu-id="b0fbe-159">Met de **module** para meter van de `Get-Command` cmdlet worden de opdrachten weer gegeven die zijn geïmporteerd uit de **PSDiagnostics** -module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-159">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="b0fbe-160">De resultaten bevestigen dat alleen de `Disable-PSTrace` `Enable-PSTrace` cmdlets en zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-160">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="b0fbe-161">Voor beeld 6: de leden van een module importeren en een voor voegsel toevoegen</span><span class="sxs-lookup"><span data-stu-id="b0fbe-161">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="b0fbe-162">In dit voor beeld wordt de module **PSDiagnostics** in de huidige sessie geïmporteerd, wordt een voor voegsel toegevoegd aan de lidnamen en worden vervolgens de namen van de voor voegsels weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-162">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="b0fbe-163">De **voor voegsel** -para meter van `Import-Module` voegt het **x** -voor voegsel toe aan alle leden die worden geïmporteerd uit de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-163">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="b0fbe-164">Het voor voegsel is alleen van toepassing op de leden van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-164">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="b0fbe-165">De module wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-165">It does not change the module.</span></span> <span data-ttu-id="b0fbe-166">De para meter **PassThru** retourneert een module-object dat de geïmporteerde module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-166">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

<span data-ttu-id="b0fbe-167">`Get-Command` Hiermee worden de leden opgehaald die zijn geïmporteerd uit de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-167">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="b0fbe-168">In de uitvoer ziet u dat de module leden correct zijn voor speld.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-168">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="b0fbe-169">Voor beeld 7: een aangepast object ophalen en gebruiken</span><span class="sxs-lookup"><span data-stu-id="b0fbe-169">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="b0fbe-170">In dit voor beeld ziet u hoe u het aangepaste object dat wordt geretourneerd door kunt ophalen en gebruiken `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-170">This example demonstrates how to get and use the custom object returned by `Import-Module`.</span></span>

<span data-ttu-id="b0fbe-171">Aangepaste objecten bevatten synthetische leden die elk van de geïmporteerde module leden vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-171">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="b0fbe-172">De cmdlets en functies in een module worden bijvoorbeeld geconverteerd naar script methoden van het aangepaste object.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-172">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="b0fbe-173">Aangepaste objecten zijn handig voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-173">Custom objects are useful in scripting.</span></span> <span data-ttu-id="b0fbe-174">Ze zijn ook handig wanneer verschillende geïmporteerde objecten dezelfde namen hebben.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-174">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="b0fbe-175">Het gebruik van de script methode van een object is gelijk aan het opgeven van de volledig gekwalificeerde naam van een geïmporteerd lid, inclusief de module naam.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-175">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="b0fbe-176">De para meter **AsCustomObject** kan alleen worden gebruikt bij het importeren van een script module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-176">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="b0fbe-177">Gebruiken `Get-Module` om te bepalen welke van de beschik bare modules een script module is.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-177">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

<span data-ttu-id="b0fbe-178">De `Show-Calendar` script module wordt geïmporteerd met de para meter **AsCustomObject** voor het aanvragen van een aangepast object en de para meter **PassThru** om het object te retour neren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-178">The `Show-Calendar` script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="b0fbe-179">Het resulterende aangepaste object wordt opgeslagen in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-179">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="b0fbe-180">De `$a` variabele wordt naar de cmdlet gepiped `Get-Member` om de eigenschappen en methoden van het opgeslagen object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-180">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="b0fbe-181">In de uitvoer ziet u een `Show-Calendar` script methode.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-181">The output shows a `Show-Calendar` script method.</span></span>

<span data-ttu-id="b0fbe-182">De `Show-Calendar` methode naam moet tussen aanhalings tekens worden geplaatst, omdat de naam een afbreek streepje bevat om de script methode aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-182">To call the `Show-Calendar` script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="b0fbe-183">Voor beeld 8: een module opnieuw importeren in dezelfde sessie</span><span class="sxs-lookup"><span data-stu-id="b0fbe-183">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="b0fbe-184">In dit voor beeld ziet u hoe u de **Force** -para meter van gebruikt `Import-Module` Wanneer u een module opnieuw importeert in dezelfde sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-184">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="b0fbe-185">Met de para meter **Force** wordt de geladen module verwijderd en vervolgens opnieuw geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-185">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="b0fbe-186">Met de eerste opdracht wordt de **PSDiagnostics** -module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-186">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="b0fbe-187">Met de tweede opdracht wordt de module opnieuw geïmporteerd. deze keer gebruikt u de para meter **prefix** .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-187">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="b0fbe-188">Zonder de para meter **Force** bevat de sessie twee exemplaren van elke **PSDiagnostics** -cmdlet, een met de standaard naam en één met de naam van de voor voegsel.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-188">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="b0fbe-189">Voor beeld 9: opdrachten uitvoeren die zijn verborgen door geïmporteerde opdrachten</span><span class="sxs-lookup"><span data-stu-id="b0fbe-189">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="b0fbe-190">In dit voor beeld ziet u hoe u opdrachten kunt uitvoeren die zijn verborgen door geïmporteerde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-190">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="b0fbe-191">De **TestModule** -module bevat een functie `Get-Date` met de naam die het jaar en de dag van het jaar retourneert.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-191">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

<span data-ttu-id="b0fbe-192">De eerste `Get-Date` cmdlet retourneert een **DateTime** -object met de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-192">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="b0fbe-193">Na het importeren van de **TestModule** -module `Get-Date` retourneert het jaar en de dag van het jaar.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-193">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="b0fbe-194">De para meter **all** gebruiken om `Get-Command` alle `Get-Date` opdrachten in de sessie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-194">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="b0fbe-195">In de resultaten ziet u dat er twee `Get-Date` opdrachten in de sessie zijn, een functie uit de **TestModule** -module en een cmdlet uit de module **micro soft. Power shell. Utility** .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-195">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="b0fbe-196">Omdat functies voor rang hebben boven cmdlets, `Get-Date` wordt de functie van de **TestModule** -module uitgevoerd in plaats van de `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-196">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="b0fbe-197">Als u de oorspronkelijke versie van wilt uitvoeren `Get-Date` , moet u de naam van de opdracht kwalificeren met de module naam.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-197">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="b0fbe-198">Zie [about_Command_Precedence](about/about_Command_Precedence.md)voor meer informatie over de prioriteit van opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-198">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="b0fbe-199">Voor beeld 10: een minimum versie van een module importeren</span><span class="sxs-lookup"><span data-stu-id="b0fbe-199">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="b0fbe-200">In dit voor beeld wordt de module **PowerShellGet** geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-200">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="b0fbe-201">Hierbij wordt de para meter **MinimumVersion** van gebruikt `Import-Module` voor het importeren van alleen versie 2.0.0 of hoger van de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-201">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="b0fbe-202">U kunt ook de para meter **RequiredVersion** gebruiken om een bepaalde versie van een module te importeren, of gebruik de **module** -en **versie** parameters van het `#Requires` tref woord om een bepaalde versie van een module in een script te vereisen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-202">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="b0fbe-203">Voor beeld 11: importeren met een volledig gekwalificeerde naam</span><span class="sxs-lookup"><span data-stu-id="b0fbe-203">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="b0fbe-204">In dit voor beeld wordt een specifieke versie van een module geïmporteerd met behulp van de FullyQualifiedName.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-204">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### <span data-ttu-id="b0fbe-205">Voor beeld 12: importeren met een volledig gekwalificeerd pad</span><span class="sxs-lookup"><span data-stu-id="b0fbe-205">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="b0fbe-206">In dit voor beeld wordt een specifieke versie van een module met het volledig gekwalificeerde pad geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-206">This example imports a specific version of a module using the fully qualified path.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### <span data-ttu-id="b0fbe-207">Voor beeld 13: een module van een externe computer importeren</span><span class="sxs-lookup"><span data-stu-id="b0fbe-207">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="b0fbe-208">In dit voor beeld ziet u hoe u de- `Import-Module` cmdlet gebruikt om een module te importeren vanaf een externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-208">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="b0fbe-209">Met deze opdracht wordt de impliciete externe functie van Power shell gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-209">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="b0fbe-210">Wanneer u modules uit een andere sessie importeert, kunt u de cmdlets in de huidige sessie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-210">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="b0fbe-211">Opdrachten die gebruikmaken van de cmdlets worden echter uitgevoerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-211">However, commands that use the cmdlets run in the remote session.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

<span data-ttu-id="b0fbe-212">`New-PSSession` Hiermee maakt u een externe sessie (**PSSession**) op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-212">`New-PSSession` creates a remote session (**PSSession**) to the Server01 computer.</span></span> <span data-ttu-id="b0fbe-213">De **PSSession** wordt opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-213">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="b0fbe-214">Met `Get-Module` de para meter **PSSession** wordt aangegeven dat de module **netsecurity** is geïnstalleerd en beschikbaar is op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-214">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="b0fbe-215">Deze opdracht is gelijk aan het gebruik `Invoke-Command` van de cmdlet om de `Get-Module` opdracht uit te voeren in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-215">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="b0fbe-216">Bijvoorbeeld: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="b0fbe-216">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="b0fbe-217">Met `Import-Module` de para meter **PSSession** wordt de module **netsecurity** van de externe computer in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-217">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="b0fbe-218">De `Get-Command` cmdlet wordt gebruikt om opdrachten op te halen die beginnen met de **firewall** **Get** en include in de module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-218">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="b0fbe-219">De uitvoer bevestigt dat de module en de bijbehorende cmdlets zijn geïmporteerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-219">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="b0fbe-220">Vervolgens haalt de `Get-NetFirewallRule` cmdlet Windows Remote Management firewall-regels op de Server01-computer op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-220">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="b0fbe-221">Dit komt overeen met het gebruik `Invoke-Command` van de cmdlet om uit te voeren `Get-NetFirewallRule` op de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-221">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="b0fbe-222">Voor beeld 14: opslag beheren op een externe computer zonder het Windows-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="b0fbe-222">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="b0fbe-223">In dit voor beeld heeft de beheerder van de computer de WMI-provider voor module detectie geïnstalleerd, waarmee u CIM-opdrachten kunt gebruiken die zijn ontworpen voor de provider.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-223">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="b0fbe-224">`New-CimSession`Met de cmdlet wordt een sessie gemaakt op de externe computer met de naam RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-224">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="b0fbe-225">De sessie maakt verbinding met de WMI-service op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-225">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="b0fbe-226">De CIM-sessie wordt opgeslagen in de `$cs` variabele.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-226">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="b0fbe-227">`Import-Module` maakt gebruik van de **CimSession** in `$cs` om de CIM- **opslag** module te importeren van de RSDGF03-computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-227">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="b0fbe-228">De `Get-Command` cmdlet toont de `Get-Disk` opdracht in de module **opslag** .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-228">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="b0fbe-229">Wanneer u een CIM-module in de lokale sessie importeert, zet Power shell de CDXML-bestanden voor elke opdracht om in Power shell-scripts, die als functies in de lokale sessie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-229">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="b0fbe-230">Hoewel `Get-Disk` in de lokale sessie wordt getypt, wordt de cmdlet impliciet uitgevoerd op de externe computer van waaruit deze is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-230">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="b0fbe-231">De opdracht retourneert objecten van de externe computer naar de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-231">The command returns objects from the remote computer to the local session.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## <span data-ttu-id="b0fbe-232">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0fbe-232">PARAMETERS</span></span>

### <span data-ttu-id="b0fbe-233">-Alias</span><span class="sxs-lookup"><span data-stu-id="b0fbe-233">-Alias</span></span>

<span data-ttu-id="b0fbe-234">Hiermee geeft u de aliassen op die met deze cmdlet worden geïmporteerd van de module in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-234">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="b0fbe-235">Voer een door komma's gescheiden lijst met aliassen in.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-235">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="b0fbe-236">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-236">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b0fbe-237">Sommige modules exporteren automatisch geselecteerde aliassen in uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-237">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="b0fbe-238">Met deze para meter kunt u uit de geëxporteerde aliassen selecteren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-238">This parameter lets you select from among the exported aliases.</span></span>

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

### <span data-ttu-id="b0fbe-239">-Argument List</span><span class="sxs-lookup"><span data-stu-id="b0fbe-239">-ArgumentList</span></span>

<span data-ttu-id="b0fbe-240">Hiermee wordt een matrix met argumenten, of parameter waarden, opgegeven die worden door gegeven aan een script module tijdens de `Import-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-240">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="b0fbe-241">Deze para meter is alleen geldig wanneer u een script module importeert.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-241">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="b0fbe-242">U kunt ook naar de para meter **argument List** verwijzen met behulp van de alias, **args**.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-242">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="b0fbe-243">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-243">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-244">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="b0fbe-244">-AsCustomObject</span></span>

<span data-ttu-id="b0fbe-245">Hiermee wordt aangegeven dat met deze cmdlet een aangepast object wordt geretourneerd met leden die de geïmporteerde module leden vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-245">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="b0fbe-246">Deze para meter is alleen geldig voor script modules.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-246">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="b0fbe-247">Wanneer u de para meter **AsCustomObject** gebruikt, worden `Import-Module` de module leden in de sessie geïmporteerd en wordt vervolgens een **PSCustomObject** -object geretourneerd in plaats van een **PSModuleInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-247">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="b0fbe-248">U kunt het aangepaste object opslaan in een variabele en de punt notatie gebruiken om de leden aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-248">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-249">-Assembly</span><span class="sxs-lookup"><span data-stu-id="b0fbe-249">-Assembly</span></span>

<span data-ttu-id="b0fbe-250">Hiermee wordt een matrix van assembly-objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-250">Specifies an array of assembly objects.</span></span> <span data-ttu-id="b0fbe-251">Met deze cmdlet worden de cmdlets en providers geïmporteerd die in de opgegeven assembly-objecten zijn geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-251">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="b0fbe-252">Voer een variabele in die assembly-objecten of een opdracht voor het maken van assembly-objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-252">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="b0fbe-253">U kunt ook een assembly-object pipeen naar `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-253">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="b0fbe-254">Wanneer u deze para meter gebruikt, worden alleen de cmdlets en providers geïmporteerd die door de opgegeven assembly's worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-254">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="b0fbe-255">Als de module andere bestanden bevat, worden deze niet geïmporteerd en ontbreken er mogelijk belang rijke leden van de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-255">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="b0fbe-256">Gebruik deze para meter voor het opsporen van fouten en het testen van de module, of wanneer u wordt gevraagd deze te gebruiken door de module auteur.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-256">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-257">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="b0fbe-257">-CimNamespace</span></span>

<span data-ttu-id="b0fbe-258">Hiermee geeft u de naam ruimte van een alternatieve CIM-provider die CIM-modules beschikbaar stelt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-258">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="b0fbe-259">De standaard waarde is de naam ruimte van de WMI-provider van de module detectie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-259">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="b0fbe-260">Gebruik deze para meter om CIM-modules te importeren van computers en apparaten waarop geen Windows-besturings systeem wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-260">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="b0fbe-261">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-262">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="b0fbe-262">-CimResourceUri</span></span>

<span data-ttu-id="b0fbe-263">Hiermee geeft u een alternatieve locatie voor CIM-modules op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-263">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="b0fbe-264">De standaard waarde is de resource-URI van de module detectie WMI-provider op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-264">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="b0fbe-265">Gebruik deze para meter om CIM-modules te importeren van computers en apparaten waarop geen Windows-besturings systeem wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-265">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="b0fbe-266">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-267">-CimSession</span><span class="sxs-lookup"><span data-stu-id="b0fbe-267">-CimSession</span></span>

<span data-ttu-id="b0fbe-268">Hiermee geeft u een CIM-sessie op de externe computer op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-268">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="b0fbe-269">Voer een variabele in die de CIM-sessie bevat of een opdracht waarmee de CIM-sessie wordt opgehaald, zoals een [Get-CimSession-](../CimCmdlets/Get-CimSession.md) opdracht.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-269">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="b0fbe-270">`Import-Module` maakt gebruik van de verbinding met de CIM-sessie om modules van de externe computer te importeren in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-270">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="b0fbe-271">Wanneer u de opdrachten van de geïmporteerde module in de huidige sessie gebruikt, worden de opdrachten uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-271">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="b0fbe-272">U kunt deze para meter gebruiken om modules te importeren van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd, en Windows-computers met Power shell, maar waarvoor geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-272">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="b0fbe-273">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-273">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-274">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b0fbe-274">-Cmdlet</span></span>

<span data-ttu-id="b0fbe-275">Hiermee geeft u een matrix met cmdlets op die met deze cmdlet van de module in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-275">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="b0fbe-276">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b0fbe-277">Sommige modules exporteren geselecteerde cmdlets automatisch naar uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-277">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="b0fbe-278">Met deze para meter kunt u uit de geëxporteerde cmdlets selecteren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-278">This parameter lets you select from among the exported cmdlets.</span></span>

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

### <span data-ttu-id="b0fbe-279">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="b0fbe-279">-DisableNameChecking</span></span>

<span data-ttu-id="b0fbe-280">Geeft aan dat deze cmdlet het bericht onderdrukt dat u waarschuwt wanneer u een cmdlet of functie importeert waarvan de naam een niet-goedgekeurde term of een verboden teken bevat.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-280">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="b0fbe-281">Als een module die u importeert, cmdlets of functies met een niet-goedgekeurde term in hun namen exporteert, wordt standaard het volgende waarschuwings bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="b0fbe-281">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="b0fbe-282">Waarschuwing: Sommige geïmporteerde opdracht namen bevatten niet-goedgekeurde werk woorden, waardoor ze minder kunnen worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-282">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="b0fbe-283">Gebruik de para meter uitgebreid voor meer details of typ Get-Verb om de lijst met goedgekeurde werk woorden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-283">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="b0fbe-284">Dit bericht wordt alleen een waarschuwing gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-284">This message is only a warning.</span></span> <span data-ttu-id="b0fbe-285">De volledige module is nog steeds geïmporteerd, met inbegrip van de niet-conforme opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-285">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="b0fbe-286">Hoewel het bericht wordt weer gegeven voor module gebruikers, moet het naam probleem worden opgelost door de module auteur.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-286">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-287">-Force</span><span class="sxs-lookup"><span data-stu-id="b0fbe-287">-Force</span></span>

<span data-ttu-id="b0fbe-288">Deze para meter zorgt ervoor dat een module wordt geladen, of opnieuw geladen, boven op de huidige.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-288">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-289">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b0fbe-289">-FullyQualifiedName</span></span>

<span data-ttu-id="b0fbe-290">Hiermee geeft u de volledig gekwalificeerde naam van de module op als een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-290">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="b0fbe-291">De waarde kan bestaan uit een combi natie van teken reeksen en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-291">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="b0fbe-292">De hash-tabel bevat de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-292">The hash table has the following keys.</span></span>

- <span data-ttu-id="b0fbe-293">`ModuleName` - **Vereist** Hiermee geeft u de module naam op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-293">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="b0fbe-294">`GUID` - **Optioneel** Hiermee geeft u de GUID van de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-294">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="b0fbe-295">Het is ook **vereist** om een van de drie onderstaande sleutels op te geven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-295">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="b0fbe-296">Deze sleutels kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-296">These keys can't be used together.</span></span>
  - <span data-ttu-id="b0fbe-297">`ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-297">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="b0fbe-298">`RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-298">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="b0fbe-299">`MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-299">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-300">-Functie</span><span class="sxs-lookup"><span data-stu-id="b0fbe-300">-Function</span></span>

<span data-ttu-id="b0fbe-301">Hiermee geeft u een matrix op met functies die met deze cmdlet worden geïmporteerd van de module in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-301">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="b0fbe-302">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-302">Wildcard characters are permitted.</span></span> <span data-ttu-id="b0fbe-303">In sommige modules worden geselecteerde functies automatisch geëxporteerd naar uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-303">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="b0fbe-304">Met deze para meter kunt u kiezen uit de geëxporteerde functies.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-304">This parameter lets you select from among the exported functions.</span></span>

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

### <span data-ttu-id="b0fbe-305">-Wereld wijd</span><span class="sxs-lookup"><span data-stu-id="b0fbe-305">-Global</span></span>

<span data-ttu-id="b0fbe-306">Geeft aan dat met deze cmdlet modules worden geïmporteerd in de algemene sessie status, zodat deze beschikbaar zijn voor alle opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-306">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="b0fbe-307">Wanneer `Import-Module` cmdlet wordt aangeroepen vanuit de opdracht prompt, script bestand of script Block, worden standaard alle opdrachten geïmporteerd in de status van de globale sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-307">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="b0fbe-308">Wanneer de cmdlet vanuit een andere module wordt aangeroepen, worden `Import-Module` de opdrachten in een module, inclusief opdrachten van geneste modules, in de sessie status van de aanroepende module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-308">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="b0fbe-309">U moet aanroepen `Import-Module` vanuit een module vermijden.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-309">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="b0fbe-310">Declareer in plaats daarvan de doel module als een geneste module in het manifest van de bovenliggende module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-310">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="b0fbe-311">Het declareren van geneste modules verbetert de detectie van afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-311">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="b0fbe-312">De **algemene** para meter is gelijk aan de **bereik** parameter met de waarde **Global**.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-312">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="b0fbe-313">Als u de opdrachten die een module exporteert, wilt beperken, gebruikt u een `Export-ModuleMember` opdracht in de script module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-313">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-314">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b0fbe-314">-MaximumVersion</span></span>

<span data-ttu-id="b0fbe-315">Hiermee geeft u een maximum versie op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-315">Specifies a maximum version.</span></span> <span data-ttu-id="b0fbe-316">Met deze cmdlet wordt alleen een versie van de module geïmporteerd die kleiner is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-316">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="b0fbe-317">Als er geen versie in aanmerking komt, `Import-Module` wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-317">If no version qualifies, `Import-Module` returns an error.</span></span>

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-318">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b0fbe-318">-MinimumVersion</span></span>

<span data-ttu-id="b0fbe-319">Hiermee geeft u een minimum versie op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-319">Specifies a minimum version.</span></span> <span data-ttu-id="b0fbe-320">Met deze cmdlet wordt alleen een versie van de module geïmporteerd die groter is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-320">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="b0fbe-321">Gebruik de naam van de **MinimumVersion** -para meter of de alias, **versie**.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-321">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="b0fbe-322">Als er geen versie in aanmerking komt, wordt `Import-Module` een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-322">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="b0fbe-323">Als u een exacte versie wilt opgeven, gebruikt u de para meter **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-323">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="b0fbe-324">U kunt ook de **module** en de **versie** parameters van het sleutel woord **#Requires** gebruiken om een specifieke versie van een module in een script te vereisen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-324">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="b0fbe-325">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-326">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="b0fbe-326">-ModuleInfo</span></span>

<span data-ttu-id="b0fbe-327">Hiermee geeft u een matrix op met module objecten die moeten worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-327">Specifies an array of module objects to import.</span></span> <span data-ttu-id="b0fbe-328">Voer een variabele in die de module objecten bevat, of een opdracht die de module objecten ophaalt, bijvoorbeeld de volgende opdracht: `Get-Module -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-328">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="b0fbe-329">U kunt ook module-objecten pipet naar `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-329">You can also pipe module objects to `Import-Module`.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-330">-Name</span><span class="sxs-lookup"><span data-stu-id="b0fbe-330">-Name</span></span>

<span data-ttu-id="b0fbe-331">Hiermee geeft u de namen op van de modules die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-331">Specifies the names of the modules to import.</span></span> <span data-ttu-id="b0fbe-332">Voer de naam van de module of de naam van een bestand in de module in, zoals een `.psd1` , `.psm1` , `.dll` of `.ps1` bestand.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-332">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="b0fbe-333">Bestands paden zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-333">File paths are optional.</span></span> <span data-ttu-id="b0fbe-334">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-334">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="b0fbe-335">U kunt ook de naam van de module en de bestands namen in de pipes `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-335">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="b0fbe-336">Als u een pad weglaat, `Import-Module` zoekt naar de module in de paden die zijn opgeslagen in de `$env:PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-336">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="b0fbe-337">Geef waar mogelijk alleen de module naam op.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-337">Specify only the module name whenever possible.</span></span> <span data-ttu-id="b0fbe-338">Wanneer u een bestands naam opgeeft, worden alleen de leden geïmporteerd die in dat bestand zijn geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-338">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="b0fbe-339">Als de module andere bestanden bevat, worden deze niet geïmporteerd en ontbreken er mogelijk belang rijke leden van de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-339">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="b0fbe-340">Hoewel het mogelijk is om een script bestand ( `.ps1` ) te importeren als een module, zijn script bestanden meestal niet gestructureerd als script modules file ( `.psm1` )-bestand.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-340">While it is possible to import a script (`.ps1`) file as a module, script files are usually not structured like script modules file (`.psm1`) file.</span></span> <span data-ttu-id="b0fbe-341">Het importeren van een script bestand garandeert niet dat het kan worden gebruikt als een module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-341">Importing a script file does not guarantee that it is usable as a module.</span></span> <span data-ttu-id="b0fbe-342">Zie [about_Modules](about/about_Modules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-342">For more information, see [about_Modules](about/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b0fbe-343">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="b0fbe-343">-NoClobber</span></span>

<span data-ttu-id="b0fbe-344">Hiermee wordt voor komen dat opdrachten die dezelfde naam hebben als bestaande opdrachten in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-344">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="b0fbe-345">Standaard worden `Import-Module` alle geëxporteerde module opdrachten geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-345">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="b0fbe-346">Opdrachten met dezelfde naam kunnen opdrachten in de sessie verbergen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-346">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="b0fbe-347">Gebruik de **voor voegsel** -of **NoClobber** -para meter om conflicten met de naam van een sessie te voor komen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-347">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="b0fbe-348">Zie ' modules en naam conflicten ' in [about_Modules](about/about_Modules.md) en [about_Command_Precedence](about/about_Command_Precedence.md)voor meer informatie over naam conflicten en de prioriteit van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-348">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="b0fbe-349">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-349">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-350">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b0fbe-350">-PassThru</span></span>

<span data-ttu-id="b0fbe-351">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-351">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="b0fbe-352">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-352">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-353">-Voor voegsel</span><span class="sxs-lookup"><span data-stu-id="b0fbe-353">-Prefix</span></span>

<span data-ttu-id="b0fbe-354">Hiermee geeft u een voor voegsel op dat met deze cmdlet wordt toegevoegd aan de naam woorden in de namen van geïmporteerde module leden.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-354">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="b0fbe-355">Gebruik deze para meter om naam conflicten te voor komen die zich kunnen voordoen wanneer verschillende leden in de sessie dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-355">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="b0fbe-356">Met deze para meter wordt de module niet gewijzigd en heeft dit geen invloed op bestanden die door de module worden geïmporteerd voor eigen gebruik.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-356">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="b0fbe-357">Deze worden geneste modules genoemd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-357">These are known as nested modules.</span></span> <span data-ttu-id="b0fbe-358">Deze cmdlet is alleen van invloed op de namen van leden in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-358">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="b0fbe-359">Als u bijvoorbeeld het voor voegsel UTC opgeeft en vervolgens een cmdlet importeert `Get-Date` , wordt de cmdlet bekend in de sessie als `Get-UTCDate` en wordt deze niet verward met de oorspronkelijke `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-359">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="b0fbe-360">De waarde van deze para meter heeft voor rang op de eigenschap **DefaultCommandPrefix** van de module, waarmee het standaard voorvoegsel wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-360">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-361">-PSSession</span><span class="sxs-lookup"><span data-stu-id="b0fbe-361">-PSSession</span></span>

<span data-ttu-id="b0fbe-362">Hiermee geeft u een door Power shell door de gebruiker beheerde sessie (**PSSession**) op waarvan de cmdlet modules in de huidige sessie importeert.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-362">Specifies a PowerShell user-managed session (**PSSession**) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="b0fbe-363">Voer een variabele in die een **PSSession** of een opdracht bevat waarmee een **PSSession** wordt opgehaald, zoals een `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-363">Enter a variable that contains a **PSSession** or a command that gets a **PSSession**, such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="b0fbe-364">Wanneer u een module vanuit een andere sessie in de huidige sessie importeert, kunt u de cmdlets uit de module in de huidige sessie gebruiken, net zoals u cmdlets van een lokale module zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-364">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="b0fbe-365">Opdrachten die gebruikmaken van de externe cmdlets worden uitgevoerd in de externe sessie, maar de externe gegevens worden op de achtergrond beheerd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-365">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="b0fbe-366">Deze para meter maakt gebruik van de impliciete functie voor externe communicatie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-366">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="b0fbe-367">Het is gelijk aan het gebruik `Import-PSSession` van de cmdlet om bepaalde modules vanuit een sessie te importeren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-367">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="b0fbe-368">`Import-Module` kan geen Power shell core-modules importeren uit een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-368">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="b0fbe-369">De Power shell-kern modules hebben namen die beginnen met micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-369">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="b0fbe-370">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-370">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-371">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b0fbe-371">-RequiredVersion</span></span>

<span data-ttu-id="b0fbe-372">Hiermee geeft u een versie van de module op die met deze cmdlet wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-372">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="b0fbe-373">Als de versie niet is geïnstalleerd, wordt er `Import-Module` een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-373">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="b0fbe-374">Standaard wordt `Import-Module` de module geïmporteerd zonder het versie nummer te controleren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-374">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="b0fbe-375">Als u een minimum versie wilt opgeven, gebruikt u de para meter **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="b0fbe-375">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="b0fbe-376">U kunt ook de **module** en de **versie** parameters van het sleutel woord **#Requires** gebruiken om een specifieke versie van een module in een script te vereisen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-376">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="b0fbe-377">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-377">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="b0fbe-378">Scripts die gebruikmaken van **RequiredVersion** om modules te importeren die zijn opgenomen in bestaande releases van het Windows-besturings systeem, worden niet automatisch uitgevoerd in toekomstige releases van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-378">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="b0fbe-379">Dit komt doordat de versie nummers van de Power shell-module in toekomstige releases van het Windows-besturings systeem hoger zijn dan de module versie nummers in bestaande releases van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-379">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-380">-Bereik</span><span class="sxs-lookup"><span data-stu-id="b0fbe-380">-Scope</span></span>

<span data-ttu-id="b0fbe-381">Hiermee geeft u een bereik op waarin met deze cmdlet de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-381">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="b0fbe-382">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b0fbe-382">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b0fbe-383">**Global**.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-383">**Global**.</span></span> <span data-ttu-id="b0fbe-384">Beschikbaar voor alle opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-384">Available to all commands in the session.</span></span> <span data-ttu-id="b0fbe-385">Komt overeen met de **algemene** para meter.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-385">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="b0fbe-386">**Lokaal**.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-386">**Local**.</span></span> <span data-ttu-id="b0fbe-387">Alleen beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-387">Available only in the current scope.</span></span>

<span data-ttu-id="b0fbe-388">Wanneer `Import-Module` cmdlet wordt aangeroepen vanuit de opdracht prompt, script bestand of script Block, worden standaard alle opdrachten geïmporteerd in de status van de globale sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-388">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="b0fbe-389">U kunt de `-Scope Local` para meter gebruiken voor het importeren van module-inhoud in het script-of script Block-bereik.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-389">You can use the `-Scope Local` parameter to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="b0fbe-390">Wanneer de cmdlet vanuit een andere module wordt aangeroepen, worden `Import-Module` de opdrachten in een module, inclusief opdrachten van geneste modules, in de sessie status van de oproepende functie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-390">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="b0fbe-391">Opgeven `-Scope Global` of `-Global` aangeven dat met deze cmdlet modules worden geïmporteerd in de algemene sessie status, zodat deze beschikbaar zijn voor alle opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-391">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="b0fbe-392">De **algemene** para meter is gelijk aan de **bereik** parameter met de waarde **Global**.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-392">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="b0fbe-393">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-393">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-394">-Variabele</span><span class="sxs-lookup"><span data-stu-id="b0fbe-394">-Variable</span></span>

<span data-ttu-id="b0fbe-395">Hiermee geeft u een matrix van variabelen op die met deze cmdlet worden geïmporteerd uit de module in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-395">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="b0fbe-396">Voer een lijst met variabelen in.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-396">Enter a list of variables.</span></span> <span data-ttu-id="b0fbe-397">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-397">Wildcard characters are permitted.</span></span>

<span data-ttu-id="b0fbe-398">Sommige modules exporteren geselecteerde variabelen automatisch naar uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-398">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="b0fbe-399">Met deze para meter kunt u uit de geëxporteerde variabelen selecteren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-399">This parameter lets you select from among the exported variables.</span></span>

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

### <span data-ttu-id="b0fbe-400">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="b0fbe-400">-SkipEditionCheck</span></span>

<span data-ttu-id="b0fbe-401">Hiermee wordt de selectie van het `CompatiblePSEditions` veld overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-401">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="b0fbe-402">Hiermee kunt u een module laden vanuit de `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory in Power shell Core wanneer die module niet `Core` in het `CompatiblePSEditions` manifest veld is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-402">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="b0fbe-403">Bij het importeren van een module vanuit een ander pad heeft deze switch niets omdat de controle niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-403">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="b0fbe-404">In Linux en macOS heeft deze switch niets.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-404">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="b0fbe-405">Zie [about_PowerShell_Editions](About/about_PowerShell_Editions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-405">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="b0fbe-406">`Import-Module -SkipEditionCheck` is het waarschijnlijk dat een module niet kan worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-406">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="b0fbe-407">Zelfs als de functie slaagt, kan het aanroepen van een opdracht uit de module later mislukken wanneer er een incompatibele API wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-407">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedName, FullyQualifiedNameAndPSSession, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-408">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="b0fbe-408">-UseWindowsPowerShell</span></span>

<span data-ttu-id="b0fbe-409">Laadt een module met Windows Power shell-compatibiliteits functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-409">Loads module using Windows PowerShell Compatibility functionality.</span></span> <span data-ttu-id="b0fbe-410">Zie [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-410">See [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0fbe-411">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0fbe-411">CommonParameters</span></span>

<span data-ttu-id="b0fbe-412">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-412">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0fbe-413">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-413">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0fbe-414">INVOER</span><span class="sxs-lookup"><span data-stu-id="b0fbe-414">INPUTS</span></span>

### <span data-ttu-id="b0fbe-415">System. String, System. Management. Automation. PSModuleInfo, System. reflectie. assembly</span><span class="sxs-lookup"><span data-stu-id="b0fbe-415">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="b0fbe-416">U kunt een module naam, module object of Assembly-object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-416">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="b0fbe-417">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b0fbe-417">OUTPUTS</span></span>

### <span data-ttu-id="b0fbe-418">Geen, System. Management. Automation. PSModuleInfo of System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="b0fbe-418">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="b0fbe-419">`Import-Module`Er wordt standaard geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-419">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="b0fbe-420">Als u de para meter **PassThru** opgeeft, genereert de cmdlet een **System. Management. Automation. PSModuleInfo** -object dat de module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-420">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="b0fbe-421">Als u de para meter **AsCustomObject** opgeeft, wordt er een **PSCustomObject** -object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-421">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="b0fbe-422">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b0fbe-422">NOTES</span></span>

- <span data-ttu-id="b0fbe-423">Voordat u een module kunt importeren, moet de module op de lokale computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-423">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="b0fbe-424">Dat wil zeggen dat de module directory moet worden gekopieerd naar een map die toegankelijk is voor uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-424">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="b0fbe-425">Zie [about_Modules](About/about_Modules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-425">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="b0fbe-426">U kunt ook de para meters **PSSession** en **CIMSession** gebruiken voor het importeren van modules die op externe computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-426">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="b0fbe-427">Opdrachten die gebruikmaken van de cmdlets in deze modules, worden echter uitgevoerd in de externe sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-427">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="b0fbe-428">Als u leden met dezelfde naam en hetzelfde type in uw sessie importeert, gebruikt Power Shell standaard het laatst geïmporteerde lid.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-428">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="b0fbe-429">Variabelen en aliassen worden vervangen en de oorspronkelijke waarden zijn niet toegankelijk.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-429">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="b0fbe-430">Functies, cmdlets en providers worden alleen geschaduwd door de nieuwe leden.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-430">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="b0fbe-431">Ze zijn toegankelijk door in aanmerking te komen voor de naam van de opdracht met de naam van de module, module of functie pad.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-431">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="b0fbe-432">Als u de opmaak gegevens wilt bijwerken voor opdrachten die zijn geïmporteerd uit een module, gebruikt u de `Update-FormatData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-432">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="b0fbe-433">`Update-FormatData` werkt ook de opmaak gegevens bij voor opdrachten in de sessie die uit modules zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-433">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="b0fbe-434">Als het opmaak bestand voor een module wordt gewijzigd, kunt u een `Update-FormatData` opdracht uitvoeren om de opmaak gegevens voor geïmporteerde opdrachten bij te werken.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-434">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="b0fbe-435">U hoeft de module niet opnieuw te importeren.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-435">You don't need to import the module again.</span></span>

- <span data-ttu-id="b0fbe-436">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn geïnstalleerd met Power shell, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-436">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="b0fbe-437">In Windows Power Shell 2,0, en in hostgroepen die oudere sessies maken in latere versies van Power shell, worden de kern opdrachten verpakt in modules (**PSSnapins**).</span><span class="sxs-lookup"><span data-stu-id="b0fbe-437">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="b0fbe-438">De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-438">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="b0fbe-439">Externe sessies, zoals computers die zijn gestart door de `New-PSSession` cmdlet, zijn ook oudere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-439">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="b0fbe-440">Zie de [methode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)voor informatie over de **CreateDefault2** -methode waarmee nieuwe-stijl sessies met kern modules worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-440">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="b0fbe-441">In Windows Power Shell 2,0 zijn sommige eigenschaps waarden van het module object, zoals de waarden van de eigenschappen **ExportedCmdlets** en **NestedModules** , niet ingevuld tot de module werd geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-441">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported.</span></span>

- <span data-ttu-id="b0fbe-442">Als u probeert een module te importeren die gemengde assembly's bevat die niet compatibel zijn met Windows Power Shell 3.0 +, `Import-Module` wordt een fout bericht van de volgende strekking weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-442">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0+, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="b0fbe-443">Import-Module: de assembly met gemengde modus is gebouwd op basis van versie ' v 2.0.50727 ' van de runtime en kan niet worden geladen in de 4,0-runtime zonder aanvullende configuratie-informatie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-443">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="b0fbe-444">Deze fout treedt op wanneer een module die is ontworpen voor Windows Power Shell 2,0 ten minste één assembly met gemengde modules bevat.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-444">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly.</span></span> <span data-ttu-id="b0fbe-445">Een assembly met gemengde modules die zowel beheerde als niet-beheerde code bevat, zoals C++ en C#.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-445">A mixed-module assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="b0fbe-446">Als u een module wilt importeren die gebruikmaakt van assembly's met gemengde modus, start u Windows Power Shell 2,0 met de volgende opdracht en probeert u het `Import-Module` opnieuw.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-446">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="b0fbe-447">Als u de functie CIM-sessie wilt gebruiken, moet de externe computer beschikken over WS-Management remoting en Windows Management Instrumentation (WMI), de micro soft-implementatie van de Common Information Model (CIM)-standaard.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-447">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="b0fbe-448">De computer moet ook de WMI-provider voor module detectie hebben of een alternatieve CIM-provider die dezelfde basis functies heeft.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-448">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="b0fbe-449">U kunt de functie CIM-sessie gebruiken op computers waarop geen Windows-besturings systeem wordt uitgevoerd en op Windows-computers met Power shell, maar geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-449">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="b0fbe-450">U kunt ook de CIM-para meters gebruiken om CIM-modules op te halen van computers waarop externe communicatie van Power shell is ingeschakeld, met inbegrip van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-450">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="b0fbe-451">Wanneer u een CIM-sessie op de lokale computer maakt, gebruikt Power shell DCOM in plaats van WMI om de sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-451">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="b0fbe-452">Standaard `Import-Module` importeert de modules in het globale bereik, zelfs wanneer deze worden aangeroepen vanuit een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-452">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="b0fbe-453">Het bereik op het hoogste niveau en alle onderliggende bereiken hebben toegang tot de geëxporteerde elementen van de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-453">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="b0fbe-454">In een onderliggend bereik `-Scope Local` beperkt het importeren tot dat bereik en alle onderliggende bereiken.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-454">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="b0fbe-455">Bovenliggende bereiken zien de geïmporteerde leden vervolgens niet.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-455">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b0fbe-456">`Get-Module` geeft alle modules weer die in de huidige sessie zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-456">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="b0fbe-457">Dit omvat modules die lokaal zijn geladen in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-457">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="b0fbe-458">Gebruiken `Get-Command -Module modulename` om te zien welke leden in het huidige bereik zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-458">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="b0fbe-459">`Import-Module` laadt geen klassen-en inventaris definities in de module.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-459">`Import-Module` does not load class and enum definitions in the module.</span></span> <span data-ttu-id="b0fbe-460">Gebruik de `using module` instructie aan het begin van uw script.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-460">Use the `using module` statement at the beginning of your script.</span></span> <span data-ttu-id="b0fbe-461">Hiermee wordt de module geïmporteerd, met inbegrip van de klassen-en inventaris definities.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-461">This imports the module, including the class and enum definitions.</span></span> <span data-ttu-id="b0fbe-462">Zie [about_Using](About/about_Using.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0fbe-462">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="b0fbe-463">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b0fbe-463">RELATED LINKS</span></span>

[<span data-ttu-id="b0fbe-464">about_Modules</span><span class="sxs-lookup"><span data-stu-id="b0fbe-464">about_Modules</span></span>](about/about_Modules.md)

[<span data-ttu-id="b0fbe-465">Exporteren-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="b0fbe-465">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="b0fbe-466">Get-module</span><span class="sxs-lookup"><span data-stu-id="b0fbe-466">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="b0fbe-467">New-module</span><span class="sxs-lookup"><span data-stu-id="b0fbe-467">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="b0fbe-468">Remove-module</span><span class="sxs-lookup"><span data-stu-id="b0fbe-468">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="b0fbe-469">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="b0fbe-469">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
