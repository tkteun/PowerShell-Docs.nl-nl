---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 4be0e64f05f841f3cf3dfdd8b5f91fdcaa158965
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251053"
---
# <span data-ttu-id="f4a6a-103">Import-Module</span><span class="sxs-lookup"><span data-stu-id="f4a6a-103">Import-Module</span></span>

## <span data-ttu-id="f4a6a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f4a6a-104">SYNOPSIS</span></span>
<span data-ttu-id="f4a6a-105">Hiermee voegt u modules toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-105">Adds modules to the current session.</span></span>

## <span data-ttu-id="f4a6a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f4a6a-106">SYNTAX</span></span>

### <span data-ttu-id="f4a6a-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="f4a6a-107">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="f4a6a-108">PSSession</span><span class="sxs-lookup"><span data-stu-id="f4a6a-108">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="f4a6a-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="f4a6a-109">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="f4a6a-110">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f4a6a-110">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="f4a6a-111">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="f4a6a-111">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="f4a6a-112">Assembly</span><span class="sxs-lookup"><span data-stu-id="f4a6a-112">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="f4a6a-113">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="f4a6a-113">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="f4a6a-114">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f4a6a-114">DESCRIPTION</span></span>

<span data-ttu-id="f4a6a-115">De `Import-Module` cmdlet voegt een of meer modules toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-115">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="f4a6a-116">Vanaf Power Shell 3,0 worden geïnstalleerde modules automatisch geïmporteerd in de sessie wanneer u opdrachten of providers in de module gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-116">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="f4a6a-117">U kunt echter nog steeds de `Import-Module` opdracht gebruiken om een module te importeren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-117">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="f4a6a-118">U kunt het automatisch importeren van modules uitschakelen met behulp van de `$PSModuleAutoloadingPreference` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-118">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="f4a6a-119">Zie about_Preference_Variables voor meer informatie over de `$PSModuleAutoloadingPreference` variabele [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f4a6a-119">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="f4a6a-120">Een module is een pakket dat leden bevat die kunnen worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-120">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="f4a6a-121">Leden zijn onder andere cmdlets, providers, scripts, functies, variabelen en andere hulpprogram ma's en bestanden.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-121">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="f4a6a-122">Nadat een module is geïmporteerd, kunt u de module leden in uw sessie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-122">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="f4a6a-123">Zie [about_Modules](About/about_Modules.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-123">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="f4a6a-124">Standaard worden `Import-Module` alle leden geïmporteerd die de module exporteert, maar u kunt de para meters **alias** , **Function** , **cmdlet** en **Variable** gebruiken om te beperken welke leden worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-124">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias** , **Function** , **Cmdlet** , and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="f4a6a-125">Met de para meter **NoClobber** wordt voor komen dat `Import-Module` leden met dezelfde namen als leden in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-125">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="f4a6a-126">`Import-Module` Hiermee wordt een module alleen in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-126">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="f4a6a-127">Als u de module wilt importeren in elke nieuwe sessie, voegt `Import-Module` u een opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-127">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="f4a6a-128">Zie [about_Profiles](About/about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-128">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="f4a6a-129">U kunt externe Windows-computers waarvoor Power shell Remoting is ingeschakeld, beheren door een **PSSession** te maken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-129">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="f4a6a-130">Gebruik vervolgens de para meter **PSSession** van `Import-Module` om de modules te importeren die zijn geïnstalleerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-130">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="f4a6a-131">U kunt nu de geïmporteerde opdrachten in de huidige sessie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-131">You can now use the imported commands in the current session.</span></span> <span data-ttu-id="f4a6a-132">De opdrachten worden impliciet uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-132">The commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="f4a6a-133">Vanaf Windows Power Shell 3,0 kunt u gebruiken `Import-Module` om Common Information Model-modules (CIM) te importeren waarin de cmdlets worden gedefinieerd in de cmdlet definition XML-bestanden (CDXML).</span><span class="sxs-lookup"><span data-stu-id="f4a6a-133">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="f4a6a-134">Met deze functie kunt u cmdlets gebruiken die zijn geïmplementeerd in niet-beheerde code-assembly's, zoals die zijn geschreven in C++.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-134">This feature allows you to use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="f4a6a-135">Voor externe computers waarvoor geen externe communicatie van Power shell is ingeschakeld, met inbegrip van computers waarop het Windows-besturings systeem niet wordt uitgevoerd, kunt u de para meter **CIMSession** van gebruiken `Import-Module` voor het importeren van CIM-modules van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-135">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="f4a6a-136">De geïmporteerde opdrachten worden impliciet uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-136">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="f4a6a-137">Een **CIMSession** is een verbinding met Windows Management INSTRUMENTATION (WMI) op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-137">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="f4a6a-138">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f4a6a-138">EXAMPLES</span></span>

### <span data-ttu-id="f4a6a-139">Voor beeld 1: de leden van een module importeren in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="f4a6a-139">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="f4a6a-140">In dit voor beeld worden de leden van de module **PSDiagnostics** in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-140">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="f4a6a-141">Voor beeld 2: alle modules importeren die zijn opgegeven in het pad naar de module</span><span class="sxs-lookup"><span data-stu-id="f4a6a-141">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="f4a6a-142">In dit voor beeld worden alle beschik bare modules in het pad dat door de `$env:PSModulePath` omgevings variabele is opgegeven, in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-142">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="f4a6a-143">Voor beeld 3: de leden van verschillende modules importeren in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="f4a6a-143">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="f4a6a-144">In dit voor beeld worden de leden van de **PSDiagnostics** -en **DISM** -modules in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-144">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="f4a6a-145">De `Get-Module` cmdlet haalt de **PSDiagnostics** -en **DISM** -modules op en slaat de objecten op in de `$m` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-145">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="f4a6a-146">De para meter **ListAvailable** is vereist als u modules gaat ophalen die nog niet in de sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-146">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="f4a6a-147">De para meter **ModuleInfo** van `Import-Module` wordt gebruikt voor het importeren van de modules in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-147">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="f4a6a-148">Voor beeld 4: alle modules importeren die zijn opgegeven met een pad</span><span class="sxs-lookup"><span data-stu-id="f4a6a-148">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="f4a6a-149">In dit voor beeld wordt een expliciet pad gebruikt om te bepalen welke module moet worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-149">This example uses an explicit path to identify the module to import.</span></span>

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

<span data-ttu-id="f4a6a-150">Het gebruik van de **uitgebreide** para meter zorgt ervoor dat `Import-Module` de voortgang wordt gerapporteerd bij het laden van de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-150">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="f4a6a-151">Zonder de para meter **uitgebreid** , **PassThru** of **AsCustomObject** wordt geen `Import-Module` uitvoer gegenereerd wanneer een module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-151">Without the **Verbose** , **PassThru** , or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="f4a6a-152">Voor beeld 5: module leden beperken die in een sessie zijn geïmporteerd</span><span class="sxs-lookup"><span data-stu-id="f4a6a-152">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="f4a6a-153">In dit voor beeld ziet u hoe u kunt beperken welke module leden in de sessie worden geïmporteerd en wat het effect van deze opdracht voor de sessie is.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-153">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="f4a6a-154">De **functie** parameter beperkt de leden die worden geïmporteerd uit de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-154">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="f4a6a-155">U kunt ook de para meters **alias** , **variabele** en **cmdlet** gebruiken om andere leden te beperken die door de module worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-155">You can also use the **Alias** , **Variable** , and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="f4a6a-156">De `Get-Module` cmdlet haalt het object op dat de module **PSDiagnostics** vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-156">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="f4a6a-157">De eigenschap **ExportedCmdlets** geeft een lijst van alle cmdlets die de module exporteert, ook al zijn ze niet allemaal geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-157">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

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

<span data-ttu-id="f4a6a-158">Met de **module** para meter van de `Get-Command` cmdlet worden de opdrachten weer gegeven die zijn geïmporteerd uit de **PSDiagnostics** -module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-158">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="f4a6a-159">De resultaten bevestigen dat alleen de `Disable-PSTrace` `Enable-PSTrace` cmdlets en zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-159">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="f4a6a-160">Voor beeld 6: de leden van een module importeren en een voor voegsel toevoegen</span><span class="sxs-lookup"><span data-stu-id="f4a6a-160">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="f4a6a-161">In dit voor beeld wordt de module **PSDiagnostics** in de huidige sessie geïmporteerd, wordt een voor voegsel toegevoegd aan de lidnamen en worden vervolgens de namen van de voor voegsels weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-161">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="f4a6a-162">De **voor voegsel** -para meter van `Import-Module` voegt het **x** -voor voegsel toe aan alle leden die worden geïmporteerd uit de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-162">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="f4a6a-163">Het voor voegsel is alleen van toepassing op de leden van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-163">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="f4a6a-164">De module wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-164">It does not change the module.</span></span> <span data-ttu-id="f4a6a-165">De para meter **PassThru** retourneert een module-object dat de geïmporteerde module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-165">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

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

<span data-ttu-id="f4a6a-166">`Get-Command` Hiermee worden de leden opgehaald die zijn geïmporteerd uit de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-166">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="f4a6a-167">In de uitvoer ziet u dat de module leden correct zijn voor speld.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-167">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="f4a6a-168">Voor beeld 7: een aangepast object ophalen en gebruiken</span><span class="sxs-lookup"><span data-stu-id="f4a6a-168">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="f4a6a-169">In dit voor beeld ziet u hoe u het aangepaste object dat wordt geretourneerd door **import-module** kunt ophalen en gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-169">This example demonstrates how to get and use the custom object returned by **Import-Module**.</span></span>

<span data-ttu-id="f4a6a-170">Aangepaste objecten bevatten synthetische leden die elk van de geïmporteerde module leden vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-170">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="f4a6a-171">De cmdlets en functies in een module worden bijvoorbeeld geconverteerd naar script methoden van het aangepaste object.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-171">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="f4a6a-172">Aangepaste objecten zijn handig voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-172">Custom objects are useful in scripting.</span></span> <span data-ttu-id="f4a6a-173">Ze zijn ook handig wanneer verschillende geïmporteerde objecten dezelfde namen hebben.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-173">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="f4a6a-174">Het gebruik van de script methode van een object is gelijk aan het opgeven van de volledig gekwalificeerde naam van een geïmporteerd lid, inclusief de module naam.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-174">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="f4a6a-175">De para meter **AsCustomObject** kan alleen worden gebruikt bij het importeren van een script module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-175">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="f4a6a-176">Gebruiken `Get-Module` om te bepalen welke van de beschik bare modules een script module is.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-176">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

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

<span data-ttu-id="f4a6a-177">De script module **show-calendar** wordt geïmporteerd met de para meter **AsCustomObject** voor het aanvragen van een aangepast object en de para meter **PassThru** om het object te retour neren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-177">The **Show-Calendar** script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="f4a6a-178">Het resulterende aangepaste object wordt opgeslagen in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-178">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="f4a6a-179">De `$a` variabele wordt naar de cmdlet gepiped `Get-Member` om de eigenschappen en methoden van het opgeslagen object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-179">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="f4a6a-180">In de uitvoer ziet u een script methode voor het **weer geven** van een agenda.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-180">The output shows a **Show-Calendar** script method.</span></span>

<span data-ttu-id="f4a6a-181">Als u de script methode voor het **weer geven** van de agenda wilt aanroepen, moet de naam van de methode tussen aanhalings tekens worden geplaatst, omdat de naam een koppel teken bevat.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-181">To call the **Show-Calendar** script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="f4a6a-182">Voor beeld 8: een module opnieuw importeren in dezelfde sessie</span><span class="sxs-lookup"><span data-stu-id="f4a6a-182">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="f4a6a-183">In dit voor beeld ziet u hoe u de **Force** -para meter van gebruikt `Import-Module` Wanneer u een module opnieuw importeert in dezelfde sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-183">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="f4a6a-184">Met de para meter **Force** wordt de geladen module verwijderd en vervolgens opnieuw geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-184">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="f4a6a-185">Met de eerste opdracht wordt de **PSDiagnostics** -module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-185">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="f4a6a-186">Met de tweede opdracht wordt de module opnieuw geïmporteerd. deze keer gebruikt u de para meter **prefix** .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-186">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="f4a6a-187">Zonder de para meter **Force** bevat de sessie twee exemplaren van elke **PSDiagnostics** -cmdlet, een met de standaard naam en één met de naam van de voor voegsel.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-187">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="f4a6a-188">Voor beeld 9: opdrachten uitvoeren die zijn verborgen door geïmporteerde opdrachten</span><span class="sxs-lookup"><span data-stu-id="f4a6a-188">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="f4a6a-189">In dit voor beeld ziet u hoe u opdrachten kunt uitvoeren die zijn verborgen door geïmporteerde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-189">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="f4a6a-190">De **TestModule** -module bevat een functie `Get-Date` met de naam die het jaar en de dag van het jaar retourneert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-190">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

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

<span data-ttu-id="f4a6a-191">De eerste `Get-Date` cmdlet retourneert een **DateTime** -object met de huidige datum.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-191">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="f4a6a-192">Na het importeren van de **TestModule** -module `Get-Date` retourneert het jaar en de dag van het jaar.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-192">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="f4a6a-193">De para meter **all** gebruiken om `Get-Command` alle `Get-Date` opdrachten in de sessie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-193">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="f4a6a-194">In de resultaten ziet u dat er twee `Get-Date` opdrachten in de sessie zijn, een functie uit de **TestModule** -module en een cmdlet uit de module **micro soft. Power shell. Utility** .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-194">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="f4a6a-195">Omdat functies voor rang hebben boven cmdlets, `Get-Date` wordt de functie van de **TestModule** -module uitgevoerd in plaats van de `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-195">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="f4a6a-196">Als u de oorspronkelijke versie van wilt uitvoeren `Get-Date` , moet u de naam van de opdracht kwalificeren met de module naam.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-196">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="f4a6a-197">Zie [about_Command_Precedence](about/about_Command_Precedence.md)voor meer informatie over de prioriteit van opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-197">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="f4a6a-198">Voor beeld 10: een minimum versie van een module importeren</span><span class="sxs-lookup"><span data-stu-id="f4a6a-198">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="f4a6a-199">In dit voor beeld wordt de module **PowerShellGet** geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-199">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="f4a6a-200">Hierbij wordt de para meter **MinimumVersion** van gebruikt `Import-Module` voor het importeren van alleen versie 2.0.0 of hoger van de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-200">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="f4a6a-201">U kunt ook de para meter **RequiredVersion** gebruiken om een bepaalde versie van een module te importeren, of gebruik de **module** -en **versie** parameters van het `#Requires` tref woord om een bepaalde versie van een module in een script te vereisen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-201">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="f4a6a-202">Voor beeld 11: importeren met een volledig gekwalificeerde naam</span><span class="sxs-lookup"><span data-stu-id="f4a6a-202">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="f4a6a-203">In dit voor beeld wordt een specifieke versie van een module geïmporteerd met behulp van de FullyQualifiedName.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-203">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

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

### <span data-ttu-id="f4a6a-204">Voor beeld 12: importeren met een volledig gekwalificeerd pad</span><span class="sxs-lookup"><span data-stu-id="f4a6a-204">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="f4a6a-205">In dit voor beeld wordt een specifieke versie van een module met het volledig gekwalificeerde pad geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-205">This example imports a specific version of a module using the fully qualified path.</span></span>

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

### <span data-ttu-id="f4a6a-206">Voor beeld 13: een module van een externe computer importeren</span><span class="sxs-lookup"><span data-stu-id="f4a6a-206">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="f4a6a-207">In dit voor beeld ziet u hoe u de- `Import-Module` cmdlet gebruikt om een module te importeren vanaf een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-207">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="f4a6a-208">Met deze opdracht wordt de impliciete externe functie van Power shell gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-208">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="f4a6a-209">Wanneer u modules uit een andere sessie importeert, kunt u de cmdlets in de huidige sessie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-209">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="f4a6a-210">Opdrachten die gebruikmaken van de cmdlets worden echter uitgevoerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-210">However, commands that use the cmdlets run in the remote session.</span></span>

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

<span data-ttu-id="f4a6a-211">`New-PSSession` Hiermee maakt u een externe sessie ( **PSSession** ) op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-211">`New-PSSession` creates a remote session ( **PSSession** ) to the Server01 computer.</span></span> <span data-ttu-id="f4a6a-212">De **PSSession** wordt opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-212">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="f4a6a-213">Met `Get-Module` de para meter **PSSession** wordt aangegeven dat de module **netsecurity** is geïnstalleerd en beschikbaar is op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-213">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="f4a6a-214">Deze opdracht is gelijk aan het gebruik `Invoke-Command` van de cmdlet om de `Get-Module` opdracht uit te voeren in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-214">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="f4a6a-215">Bijvoorbeeld: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="f4a6a-215">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="f4a6a-216">Met `Import-Module` de para meter **PSSession** wordt de module **netsecurity** van de externe computer in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-216">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="f4a6a-217">De `Get-Command` cmdlet wordt gebruikt om opdrachten op te halen die beginnen met de **firewall** **Get** en include in de module **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-217">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="f4a6a-218">De uitvoer bevestigt dat de module en de bijbehorende cmdlets zijn geïmporteerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-218">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="f4a6a-219">Vervolgens haalt de `Get-NetFirewallRule` cmdlet Windows Remote Management firewall-regels op de Server01-computer op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-219">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="f4a6a-220">Dit komt overeen met het gebruik `Invoke-Command` van de cmdlet om uit te voeren `Get-NetFirewallRule` op de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-220">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="f4a6a-221">Voor beeld 14: opslag beheren op een externe computer zonder het Windows-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="f4a6a-221">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="f4a6a-222">In dit voor beeld heeft de beheerder van de computer de WMI-provider voor module detectie geïnstalleerd, waarmee u CIM-opdrachten kunt gebruiken die zijn ontworpen voor de provider.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-222">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="f4a6a-223">`New-CimSession`Met de cmdlet wordt een sessie gemaakt op de externe computer met de naam RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-223">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="f4a6a-224">De sessie maakt verbinding met de WMI-service op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-224">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="f4a6a-225">De CIM-sessie wordt opgeslagen in de `$cs` variabele.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-225">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="f4a6a-226">`Import-Module` maakt gebruik van de **CimSession** in `$cs` om de CIM- **opslag** module te importeren van de RSDGF03-computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-226">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="f4a6a-227">De `Get-Command` cmdlet toont de `Get-Disk` opdracht in de module **opslag** .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-227">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="f4a6a-228">Wanneer u een CIM-module in de lokale sessie importeert, zet Power shell de CDXML-bestanden voor elke opdracht om in Power shell-scripts, die als functies in de lokale sessie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-228">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="f4a6a-229">Hoewel `Get-Disk` in de lokale sessie wordt getypt, wordt de cmdlet impliciet uitgevoerd op de externe computer van waaruit deze is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-229">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="f4a6a-230">De opdracht retourneert objecten van de externe computer naar de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-230">The command returns objects from the remote computer to the local session.</span></span>

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

## <span data-ttu-id="f4a6a-231">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4a6a-231">PARAMETERS</span></span>

### <span data-ttu-id="f4a6a-232">-Alias</span><span class="sxs-lookup"><span data-stu-id="f4a6a-232">-Alias</span></span>

<span data-ttu-id="f4a6a-233">Hiermee geeft u de aliassen op die met deze cmdlet worden geïmporteerd van de module in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-233">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="f4a6a-234">Voer een door komma's gescheiden lijst met aliassen in.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-234">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="f4a6a-235">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-235">Wildcard characters are permitted.</span></span>

<span data-ttu-id="f4a6a-236">Sommige modules exporteren automatisch geselecteerde aliassen in uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-236">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="f4a6a-237">Met deze para meter kunt u uit de geëxporteerde aliassen selecteren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-237">This parameter lets you select from among the exported aliases.</span></span>

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

### <span data-ttu-id="f4a6a-238">-Argument List</span><span class="sxs-lookup"><span data-stu-id="f4a6a-238">-ArgumentList</span></span>

<span data-ttu-id="f4a6a-239">Hiermee wordt een matrix met argumenten, of parameter waarden, opgegeven die worden door gegeven aan een script module tijdens de `Import-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-239">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="f4a6a-240">Deze para meter is alleen geldig wanneer u een script module importeert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-240">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="f4a6a-241">U kunt ook naar de para meter **argument List** verwijzen met behulp van de alias, **args**.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-241">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="f4a6a-242">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-242">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="f4a6a-243">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="f4a6a-243">-AsCustomObject</span></span>

<span data-ttu-id="f4a6a-244">Hiermee wordt aangegeven dat met deze cmdlet een aangepast object wordt geretourneerd met leden die de geïmporteerde module leden vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-244">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="f4a6a-245">Deze para meter is alleen geldig voor script modules.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-245">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="f4a6a-246">Wanneer u de para meter **AsCustomObject** gebruikt, worden `Import-Module` de module leden in de sessie geïmporteerd en wordt vervolgens een **PSCustomObject** -object geretourneerd in plaats van een **PSModuleInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-246">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="f4a6a-247">U kunt het aangepaste object opslaan in een variabele en de punt notatie gebruiken om de leden aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-247">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

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

### <span data-ttu-id="f4a6a-248">-Assembly</span><span class="sxs-lookup"><span data-stu-id="f4a6a-248">-Assembly</span></span>

<span data-ttu-id="f4a6a-249">Hiermee wordt een matrix van assembly-objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-249">Specifies an array of assembly objects.</span></span> <span data-ttu-id="f4a6a-250">Met deze cmdlet worden de cmdlets en providers geïmporteerd die in de opgegeven assembly-objecten zijn geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-250">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="f4a6a-251">Voer een variabele in die assembly-objecten of een opdracht voor het maken van assembly-objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-251">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="f4a6a-252">U kunt ook een assembly-object pipeen naar `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-252">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="f4a6a-253">Wanneer u deze para meter gebruikt, worden alleen de cmdlets en providers geïmporteerd die door de opgegeven assembly's worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-253">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="f4a6a-254">Als de module andere bestanden bevat, worden deze niet geïmporteerd en ontbreken er mogelijk belang rijke leden van de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-254">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="f4a6a-255">Gebruik deze para meter voor het opsporen van fouten en het testen van de module, of wanneer u wordt gevraagd deze te gebruiken door de module auteur.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-255">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

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

### <span data-ttu-id="f4a6a-256">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="f4a6a-256">-CimNamespace</span></span>

<span data-ttu-id="f4a6a-257">Hiermee geeft u de naam ruimte van een alternatieve CIM-provider die CIM-modules beschikbaar stelt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-257">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="f4a6a-258">De standaard waarde is de naam ruimte van de WMI-provider van de module detectie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-258">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="f4a6a-259">Gebruik deze para meter om CIM-modules te importeren van computers en apparaten waarop geen Windows-besturings systeem wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-259">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="f4a6a-260">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f4a6a-261">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="f4a6a-261">-CimResourceUri</span></span>

<span data-ttu-id="f4a6a-262">Hiermee geeft u een alternatieve locatie voor CIM-modules op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-262">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="f4a6a-263">De standaard waarde is de resource-URI van de module detectie WMI-provider op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-263">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="f4a6a-264">Gebruik deze para meter om CIM-modules te importeren van computers en apparaten waarop geen Windows-besturings systeem wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-264">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="f4a6a-265">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-265">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f4a6a-266">-CimSession</span><span class="sxs-lookup"><span data-stu-id="f4a6a-266">-CimSession</span></span>

<span data-ttu-id="f4a6a-267">Hiermee geeft u een CIM-sessie op de externe computer op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-267">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="f4a6a-268">Voer een variabele in die de CIM-sessie bevat of een opdracht waarmee de CIM-sessie wordt opgehaald, zoals een [Get-CimSession-](../CimCmdlets/Get-CimSession.md) opdracht.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-268">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="f4a6a-269">`Import-Module` maakt gebruik van de verbinding met de CIM-sessie om modules van de externe computer te importeren in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-269">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="f4a6a-270">Wanneer u de opdrachten van de geïmporteerde module in de huidige sessie gebruikt, worden de opdrachten uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-270">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="f4a6a-271">U kunt deze para meter gebruiken om modules te importeren van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd, en Windows-computers met Power shell, maar waarvoor geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-271">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="f4a6a-272">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f4a6a-273">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4a6a-273">-Cmdlet</span></span>

<span data-ttu-id="f4a6a-274">Hiermee geeft u een matrix met cmdlets op die met deze cmdlet van de module in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-274">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="f4a6a-275">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="f4a6a-276">Sommige modules exporteren geselecteerde cmdlets automatisch naar uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-276">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="f4a6a-277">Met deze para meter kunt u uit de geëxporteerde cmdlets selecteren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-277">This parameter lets you select from among the exported cmdlets.</span></span>

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

### <span data-ttu-id="f4a6a-278">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="f4a6a-278">-DisableNameChecking</span></span>

<span data-ttu-id="f4a6a-279">Geeft aan dat deze cmdlet het bericht onderdrukt dat u waarschuwt wanneer u een cmdlet of functie importeert waarvan de naam een niet-goedgekeurde term of een verboden teken bevat.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-279">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="f4a6a-280">Als een module die u importeert, cmdlets of functies met een niet-goedgekeurde term in hun namen exporteert, wordt standaard het volgende waarschuwings bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="f4a6a-280">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="f4a6a-281">Waarschuwing: Sommige geïmporteerde opdracht namen bevatten niet-goedgekeurde werk woorden, waardoor ze minder kunnen worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-281">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="f4a6a-282">Gebruik de para meter uitgebreid voor meer details of typ Get-Verb om de lijst met goedgekeurde werk woorden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-282">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="f4a6a-283">Dit bericht wordt alleen een waarschuwing gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-283">This message is only a warning.</span></span> <span data-ttu-id="f4a6a-284">De volledige module is nog steeds geïmporteerd, met inbegrip van de niet-conforme opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-284">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="f4a6a-285">Hoewel het bericht wordt weer gegeven voor module gebruikers, moet het naam probleem worden opgelost door de module auteur.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-285">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="f4a6a-286">-Force</span><span class="sxs-lookup"><span data-stu-id="f4a6a-286">-Force</span></span>

<span data-ttu-id="f4a6a-287">Deze para meter zorgt ervoor dat een module wordt geladen, of opnieuw geladen, boven op de huidige.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-287">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

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

### <span data-ttu-id="f4a6a-288">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f4a6a-288">-FullyQualifiedName</span></span>

<span data-ttu-id="f4a6a-289">Hiermee geeft u de volledig gekwalificeerde naam van de module op als een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-289">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="f4a6a-290">De waarde kan bestaan uit een combi natie van teken reeksen en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-290">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="f4a6a-291">De hash-tabel bevat de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-291">The hash table has the following keys.</span></span>

- <span data-ttu-id="f4a6a-292">`ModuleName` - **Vereist** Hiermee geeft u de module naam op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-292">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="f4a6a-293">`GUID` - **Optioneel** Hiermee geeft u de GUID van de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-293">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="f4a6a-294">Het is ook **vereist** om een van de drie onderstaande sleutels op te geven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-294">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="f4a6a-295">Deze sleutels kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-295">These keys can't be used together.</span></span>
  - <span data-ttu-id="f4a6a-296">`ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-296">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="f4a6a-297">`RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-297">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="f4a6a-298">`MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-298">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f4a6a-299">-Functie</span><span class="sxs-lookup"><span data-stu-id="f4a6a-299">-Function</span></span>

<span data-ttu-id="f4a6a-300">Hiermee geeft u een matrix op met functies die met deze cmdlet worden geïmporteerd van de module in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-300">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="f4a6a-301">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-301">Wildcard characters are permitted.</span></span> <span data-ttu-id="f4a6a-302">In sommige modules worden geselecteerde functies automatisch geëxporteerd naar uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-302">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="f4a6a-303">Met deze para meter kunt u kiezen uit de geëxporteerde functies.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-303">This parameter lets you select from among the exported functions.</span></span>

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

### <span data-ttu-id="f4a6a-304">-Wereld wijd</span><span class="sxs-lookup"><span data-stu-id="f4a6a-304">-Global</span></span>

<span data-ttu-id="f4a6a-305">Geeft aan dat met deze cmdlet modules worden geïmporteerd in de algemene sessie status, zodat deze beschikbaar zijn voor alle opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-305">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="f4a6a-306">Wanneer `Import-Module` cmdlet wordt aangeroepen vanuit de opdracht prompt, script bestand of script Block, worden standaard alle opdrachten geïmporteerd in de status van de globale sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-306">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="f4a6a-307">Wanneer de cmdlet vanuit een andere module wordt aangeroepen, worden `Import-Module` de opdrachten in een module, inclusief opdrachten van geneste modules, in de sessie status van de aanroepende module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-307">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="f4a6a-308">U moet aanroepen `Import-Module` vanuit een module vermijden.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-308">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="f4a6a-309">Declareer in plaats daarvan de doel module als een geneste module in het manifest van de bovenliggende module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-309">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="f4a6a-310">Het declareren van geneste modules verbetert de detectie van afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-310">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="f4a6a-311">De **algemene** para meter is gelijk aan de **bereik** parameter met de waarde **Global**.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-311">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="f4a6a-312">Als u de opdrachten die een module exporteert, wilt beperken, gebruikt u een `Export-ModuleMember` opdracht in de script module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-312">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

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

### <span data-ttu-id="f4a6a-313">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f4a6a-313">-MaximumVersion</span></span>

<span data-ttu-id="f4a6a-314">Hiermee geeft u een maximum versie op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-314">Specifies a maximum version.</span></span> <span data-ttu-id="f4a6a-315">Met deze cmdlet wordt alleen een versie van de module geïmporteerd die kleiner is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-315">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="f4a6a-316">Als er geen versie in aanmerking komt, `Import-Module` wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-316">If no version qualifies, `Import-Module` returns an error.</span></span>

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

### <span data-ttu-id="f4a6a-317">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f4a6a-317">-MinimumVersion</span></span>

<span data-ttu-id="f4a6a-318">Hiermee geeft u een minimum versie op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-318">Specifies a minimum version.</span></span> <span data-ttu-id="f4a6a-319">Met deze cmdlet wordt alleen een versie van de module geïmporteerd die groter is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-319">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="f4a6a-320">Gebruik de naam van de **MinimumVersion** -para meter of de alias, **versie**.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-320">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="f4a6a-321">Als er geen versie in aanmerking komt, wordt `Import-Module` een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-321">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="f4a6a-322">Als u een exacte versie wilt opgeven, gebruikt u de para meter **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-322">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="f4a6a-323">U kunt ook de **module** en de **versie** parameters van het sleutel woord **#Requires** gebruiken om een specifieke versie van een module in een script te vereisen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-323">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="f4a6a-324">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-324">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f4a6a-325">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="f4a6a-325">-ModuleInfo</span></span>

<span data-ttu-id="f4a6a-326">Hiermee geeft u een matrix op met module objecten die moeten worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-326">Specifies an array of module objects to import.</span></span> <span data-ttu-id="f4a6a-327">Voer een variabele in die de module objecten bevat, of een opdracht die de module objecten ophaalt, bijvoorbeeld de volgende opdracht: `Get-Module -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-327">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="f4a6a-328">U kunt ook module-objecten pipet naar `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-328">You can also pipe module objects to `Import-Module`.</span></span>

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

### <span data-ttu-id="f4a6a-329">-Name</span><span class="sxs-lookup"><span data-stu-id="f4a6a-329">-Name</span></span>

<span data-ttu-id="f4a6a-330">Hiermee geeft u de namen op van de modules die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-330">Specifies the names of the modules to import.</span></span> <span data-ttu-id="f4a6a-331">Voer de naam van de module of de naam van een bestand in de module in, zoals een `.psd1` , `.psm1` , `.dll` of `.ps1` bestand.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-331">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="f4a6a-332">Bestands paden zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-332">File paths are optional.</span></span> <span data-ttu-id="f4a6a-333">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-333">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="f4a6a-334">U kunt ook de naam van de module en de bestands namen in de pipes `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-334">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="f4a6a-335">Als u een pad weglaat, `Import-Module` zoekt naar de module in de paden die zijn opgeslagen in de `$env:PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-335">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="f4a6a-336">Geef waar mogelijk alleen de module naam op.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-336">Specify only the module name whenever possible.</span></span> <span data-ttu-id="f4a6a-337">Wanneer u een bestands naam opgeeft, worden alleen de leden geïmporteerd die in dat bestand zijn geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-337">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="f4a6a-338">Als de module andere bestanden bevat, worden deze niet geïmporteerd en ontbreken er mogelijk belang rijke leden van de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-338">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

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

### <span data-ttu-id="f4a6a-339">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="f4a6a-339">-NoClobber</span></span>

<span data-ttu-id="f4a6a-340">Hiermee wordt voor komen dat opdrachten die dezelfde naam hebben als bestaande opdrachten in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-340">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="f4a6a-341">Standaard worden `Import-Module` alle geëxporteerde module opdrachten geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-341">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="f4a6a-342">Opdrachten met dezelfde naam kunnen opdrachten in de sessie verbergen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-342">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="f4a6a-343">Gebruik de **voor voegsel** -of **NoClobber** -para meter om conflicten met de naam van een sessie te voor komen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-343">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="f4a6a-344">Zie ' modules en naam conflicten ' in [about_Modules](about/about_Modules.md) en [about_Command_Precedence](about/about_Command_Precedence.md)voor meer informatie over naam conflicten en de prioriteit van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-344">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="f4a6a-345">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-345">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f4a6a-346">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f4a6a-346">-PassThru</span></span>

<span data-ttu-id="f4a6a-347">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-347">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="f4a6a-348">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-348">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f4a6a-349">-Voor voegsel</span><span class="sxs-lookup"><span data-stu-id="f4a6a-349">-Prefix</span></span>

<span data-ttu-id="f4a6a-350">Hiermee geeft u een voor voegsel op dat met deze cmdlet wordt toegevoegd aan de naam woorden in de namen van geïmporteerde module leden.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-350">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="f4a6a-351">Gebruik deze para meter om naam conflicten te voor komen die zich kunnen voordoen wanneer verschillende leden in de sessie dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-351">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="f4a6a-352">Met deze para meter wordt de module niet gewijzigd en heeft dit geen invloed op bestanden die door de module worden geïmporteerd voor eigen gebruik.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-352">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="f4a6a-353">Deze worden geneste modules genoemd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-353">These are known as nested modules.</span></span> <span data-ttu-id="f4a6a-354">Deze cmdlet is alleen van invloed op de namen van leden in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-354">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="f4a6a-355">Als u bijvoorbeeld het voor voegsel UTC opgeeft en vervolgens een cmdlet importeert `Get-Date` , wordt de cmdlet bekend in de sessie als `Get-UTCDate` en wordt deze niet verward met de oorspronkelijke `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-355">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="f4a6a-356">De waarde van deze para meter heeft voor rang op de eigenschap **DefaultCommandPrefix** van de module, waarmee het standaard voorvoegsel wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-356">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

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

### <span data-ttu-id="f4a6a-357">-PSSession</span><span class="sxs-lookup"><span data-stu-id="f4a6a-357">-PSSession</span></span>

<span data-ttu-id="f4a6a-358">Hiermee geeft u een door Power shell door de gebruiker beheerde sessie ( **PSSession** ) op waarvan de cmdlet modules in de huidige sessie importeert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-358">Specifies a PowerShell user-managed session ( **PSSession** ) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="f4a6a-359">Voer een variabele in die een **PSSession** of een opdracht bevat waarmee een **PSSession** wordt opgehaald, zoals een `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-359">Enter a variable that contains a **PSSession** or a command that gets a **PSSession** , such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="f4a6a-360">Wanneer u een module vanuit een andere sessie in de huidige sessie importeert, kunt u de cmdlets uit de module in de huidige sessie gebruiken, net zoals u cmdlets van een lokale module zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-360">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="f4a6a-361">Opdrachten die gebruikmaken van de externe cmdlets worden uitgevoerd in de externe sessie, maar de externe gegevens worden op de achtergrond beheerd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-361">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="f4a6a-362">Deze para meter maakt gebruik van de impliciete functie voor externe communicatie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-362">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="f4a6a-363">Het is gelijk aan het gebruik `Import-PSSession` van de cmdlet om bepaalde modules vanuit een sessie te importeren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-363">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="f4a6a-364">`Import-Module` kan geen Power shell core-modules importeren uit een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-364">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="f4a6a-365">De Power shell-kern modules hebben namen die beginnen met micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-365">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="f4a6a-366">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-366">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f4a6a-367">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f4a6a-367">-RequiredVersion</span></span>

<span data-ttu-id="f4a6a-368">Hiermee geeft u een versie van de module op die met deze cmdlet wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-368">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="f4a6a-369">Als de versie niet is geïnstalleerd, wordt er `Import-Module` een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-369">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="f4a6a-370">Standaard wordt `Import-Module` de module geïmporteerd zonder het versie nummer te controleren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-370">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="f4a6a-371">Als u een minimum versie wilt opgeven, gebruikt u de para meter **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-371">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="f4a6a-372">U kunt ook de **module** en de **versie** parameters van het sleutel woord **#Requires** gebruiken om een specifieke versie van een module in een script te vereisen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-372">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="f4a6a-373">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-373">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f4a6a-374">Scripts die gebruikmaken van **RequiredVersion** om modules te importeren die zijn opgenomen in bestaande releases van het Windows-besturings systeem, worden niet automatisch uitgevoerd in toekomstige releases van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-374">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="f4a6a-375">Dit komt doordat de versie nummers van de Power shell-module in toekomstige releases van het Windows-besturings systeem hoger zijn dan de module versie nummers in bestaande releases van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-375">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

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

### <span data-ttu-id="f4a6a-376">-Bereik</span><span class="sxs-lookup"><span data-stu-id="f4a6a-376">-Scope</span></span>

<span data-ttu-id="f4a6a-377">Hiermee geeft u een bereik op waarin met deze cmdlet de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-377">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="f4a6a-378">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f4a6a-378">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f4a6a-379">**Global**.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-379">**Global**.</span></span> <span data-ttu-id="f4a6a-380">Beschikbaar voor alle opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-380">Available to all commands in the session.</span></span> <span data-ttu-id="f4a6a-381">Komt overeen met de **algemene** para meter.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-381">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="f4a6a-382">**Lokaal**.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-382">**Local**.</span></span> <span data-ttu-id="f4a6a-383">Alleen beschikbaar in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-383">Available only in the current scope.</span></span>

<span data-ttu-id="f4a6a-384">Wanneer `Import-Module` cmdlet wordt aangeroepen vanuit de opdracht prompt, script bestand of script Block, worden standaard alle opdrachten geïmporteerd in de status van de globale sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-384">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="f4a6a-385">U kunt de para meter **-Scope** gebruiken met de waarde **lokaal** om module-inhoud te importeren in het script-of script Block-bereik.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-385">You can use the **-Scope** parameter with the value of **Local** to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="f4a6a-386">Wanneer de cmdlet vanuit een andere module wordt aangeroepen, worden `Import-Module` de opdrachten in een module, inclusief opdrachten van geneste modules, in de sessie status van de oproepende functie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-386">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="f4a6a-387">Opgeven `-Scope Global` of `-Global` aangeven dat met deze cmdlet modules worden geïmporteerd in de algemene sessie status, zodat deze beschikbaar zijn voor alle opdrachten in de sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-387">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="f4a6a-388">De **algemene** para meter is gelijk aan de **bereik** parameter met de waarde Global.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-388">The **Global** parameter is equivalent to the **Scope** parameter with a value of Global.</span></span>

<span data-ttu-id="f4a6a-389">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-389">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f4a6a-390">-Variabele</span><span class="sxs-lookup"><span data-stu-id="f4a6a-390">-Variable</span></span>

<span data-ttu-id="f4a6a-391">Hiermee geeft u een matrix van variabelen op die met deze cmdlet worden geïmporteerd uit de module in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-391">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="f4a6a-392">Voer een lijst met variabelen in.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-392">Enter a list of variables.</span></span> <span data-ttu-id="f4a6a-393">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-393">Wildcard characters are permitted.</span></span>

<span data-ttu-id="f4a6a-394">Sommige modules exporteren geselecteerde variabelen automatisch naar uw sessie wanneer u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-394">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="f4a6a-395">Met deze para meter kunt u uit de geëxporteerde variabelen selecteren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-395">This parameter lets you select from among the exported variables.</span></span>

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

### <span data-ttu-id="f4a6a-396">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="f4a6a-396">-SkipEditionCheck</span></span>

<span data-ttu-id="f4a6a-397">Hiermee wordt de selectie van het `CompatiblePSEditions` veld overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-397">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="f4a6a-398">Hiermee kunt u een module laden vanuit de `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory in Power shell Core wanneer die module niet `Core` in het `CompatiblePSEditions` manifest veld is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-398">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="f4a6a-399">Bij het importeren van een module vanuit een ander pad heeft deze switch niets omdat de controle niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-399">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="f4a6a-400">In Linux en macOS heeft deze switch niets.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-400">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="f4a6a-401">Zie [about_PowerShell_Editions](About/about_PowerShell_Editions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-401">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="f4a6a-402">`Import-Module -SkipEditionCheck` is het waarschijnlijk dat een module niet kan worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-402">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="f4a6a-403">Zelfs als de functie slaagt, kan het aanroepen van een opdracht uit de module later mislukken wanneer er een incompatibele API wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-403">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

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

### <span data-ttu-id="f4a6a-404">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4a6a-404">CommonParameters</span></span>

<span data-ttu-id="f4a6a-405">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-405">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4a6a-406">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-406">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4a6a-407">INVOER</span><span class="sxs-lookup"><span data-stu-id="f4a6a-407">INPUTS</span></span>

### <span data-ttu-id="f4a6a-408">System. String, System. Management. Automation. PSModuleInfo, System. reflectie. assembly</span><span class="sxs-lookup"><span data-stu-id="f4a6a-408">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="f4a6a-409">U kunt een module naam, module object of Assembly-object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-409">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="f4a6a-410">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f4a6a-410">OUTPUTS</span></span>

### <span data-ttu-id="f4a6a-411">Geen, System. Management. Automation. PSModuleInfo of System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f4a6a-411">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="f4a6a-412">`Import-Module`Er wordt standaard geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-412">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="f4a6a-413">Als u de para meter **PassThru** opgeeft, genereert de cmdlet een **System. Management. Automation. PSModuleInfo** -object dat de module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-413">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="f4a6a-414">Als u de para meter **AsCustomObject** opgeeft, wordt er een **PSCustomObject** -object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-414">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="f4a6a-415">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f4a6a-415">NOTES</span></span>

- <span data-ttu-id="f4a6a-416">Voordat u een module kunt importeren, moet de module op de lokale computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-416">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="f4a6a-417">Dat wil zeggen dat de module directory moet worden gekopieerd naar een map die toegankelijk is voor uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-417">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="f4a6a-418">Zie [about_Modules](About/about_Modules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-418">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="f4a6a-419">U kunt ook de para meters **PSSession** en **CIMSession** gebruiken voor het importeren van modules die op externe computers zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-419">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="f4a6a-420">Opdrachten die gebruikmaken van de cmdlets in deze modules, worden echter uitgevoerd in de externe sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-420">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="f4a6a-421">Als u leden met dezelfde naam en hetzelfde type in uw sessie importeert, gebruikt Power Shell standaard het laatst geïmporteerde lid.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-421">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="f4a6a-422">Variabelen en aliassen worden vervangen en de oorspronkelijke waarden zijn niet toegankelijk.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-422">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="f4a6a-423">Functies, cmdlets en providers worden alleen geschaduwd door de nieuwe leden.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-423">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="f4a6a-424">Ze zijn toegankelijk door in aanmerking te komen voor de naam van de opdracht met de naam van de module, module of functie pad.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-424">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="f4a6a-425">Als u de opmaak gegevens wilt bijwerken voor opdrachten die zijn geïmporteerd uit een module, gebruikt u de `Update-FormatData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-425">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="f4a6a-426">`Update-FormatData` werkt ook de opmaak gegevens bij voor opdrachten in de sessie die uit modules zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-426">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="f4a6a-427">Als het opmaak bestand voor een module wordt gewijzigd, kunt u een `Update-FormatData` opdracht uitvoeren om de opmaak gegevens voor geïmporteerde opdrachten bij te werken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-427">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="f4a6a-428">U hoeft de module niet opnieuw te importeren.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-428">You don't need to import the module again.</span></span>

- <span data-ttu-id="f4a6a-429">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn geïnstalleerd met Power shell, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-429">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="f4a6a-430">In Windows Power Shell 2,0, en in hostgroepen die oudere sessies maken in latere versies van Power shell, worden de kern opdrachten verpakt in modules ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="f4a6a-430">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="f4a6a-431">De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-431">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="f4a6a-432">Externe sessies, zoals computers die zijn gestart door de `New-PSSession` cmdlet, zijn ook oudere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-432">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="f4a6a-433">Zie de [methode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)voor informatie over de **CreateDefault2** -methode waarmee nieuwe-stijl sessies met kern modules worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-433">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="f4a6a-434">`Import-Module` kan geen Power shell core-modules importeren uit een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-434">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="f4a6a-435">De Power shell-kern modules hebben namen die beginnen met `Microsoft.PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="f4a6a-435">The PowerShell Core modules have names that begin with `Microsoft.PowerShell`.</span></span>

- <span data-ttu-id="f4a6a-436">In Windows Power Shell 2,0 zijn sommige eigenschaps waarden van het module-object, zoals de waarden van de eigenschappen **ExportedCmdlets** en **NestedModules** , pas ingevuld wanneer de module werd geïmporteerd en niet beschikbaar was op het module object dat de para meter **PassThru** retourneert.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-436">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported and were not available on the module object that the **PassThru** parameter returns.</span></span> <span data-ttu-id="f4a6a-437">In Windows Power Shell 3,0 worden alle waarden van de module-eigenschap ingevuld.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-437">In Windows PowerShell 3.0, all module property values are populated.</span></span>

- <span data-ttu-id="f4a6a-438">Als u probeert een module te importeren die gemengde assembly's bevat die niet compatibel zijn met Windows Power Shell 3,0, `Import-Module` wordt een fout bericht als het volgende weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-438">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="f4a6a-439">Import-Module: de assembly met gemengde modus is gebouwd op basis van versie ' v 2.0.50727 ' van de runtime en kan niet worden geladen in de 4,0-runtime zonder aanvullende configuratie-informatie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-439">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="f4a6a-440">Deze fout treedt op wanneer een module die is ontworpen voor Windows Power Shell 2,0 ten minste één assembly met een gemengde module bevat, dat wil zeggen een assembly die zowel beheerde als niet-beheerde code bevat, zoals C++ en C#.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-440">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly, that is, an assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="f4a6a-441">Als u een module wilt importeren die gebruikmaakt van assembly's met gemengde modus, start u Windows Power Shell 2,0 met de volgende opdracht en probeert u het `Import-Module` opnieuw.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-441">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="f4a6a-442">Als u de functie CIM-sessie wilt gebruiken, moet de externe computer beschikken over WS-Management remoting en Windows Management Instrumentation (WMI), de micro soft-implementatie van de Common Information Model (CIM)-standaard.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-442">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="f4a6a-443">De computer moet ook de WMI-provider voor module detectie hebben of een alternatieve CIM-provider die dezelfde basis functies heeft.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-443">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="f4a6a-444">U kunt de functie CIM-sessie gebruiken op computers waarop geen Windows-besturings systeem wordt uitgevoerd en op Windows-computers met Power shell, maar geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-444">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="f4a6a-445">U kunt ook de CIM-para meters gebruiken om CIM-modules op te halen van computers waarop externe communicatie van Power shell is ingeschakeld, met inbegrip van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-445">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="f4a6a-446">Wanneer u een CIM-sessie op de lokale computer maakt, gebruikt Power shell DCOM in plaats van WMI om de sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-446">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="f4a6a-447">Standaard `Import-Module` importeert de modules in het globale bereik, zelfs wanneer deze worden aangeroepen vanuit een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-447">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="f4a6a-448">Het bereik op het hoogste niveau en alle onderliggende bereiken hebben toegang tot de geëxporteerde elementen van de module.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-448">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="f4a6a-449">In een onderliggend bereik `-Scope Local` beperkt het importeren tot dat bereik en alle onderliggende bereiken.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-449">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="f4a6a-450">Bovenliggende bereiken zien de geïmporteerde leden vervolgens niet.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-450">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f4a6a-451">`Get-Module` geeft alle modules weer die in de huidige sessie zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-451">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="f4a6a-452">Dit omvat modules die lokaal zijn geladen in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-452">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="f4a6a-453">Gebruiken `Get-Command -Module modulename` om te zien welke leden in het huidige bereik zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-453">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="f4a6a-454">Als de module klassen-en inventaris definities bevat, gebruikt u `using module` aan het begin van het script.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-454">If the module includes class and enum definitions, use `using module` at the beginning of your script.</span></span> <span data-ttu-id="f4a6a-455">De scripts worden geïmporteerd, met inbegrip van de klassen-en inventaris definities.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-455">This import the scripts, including the class and enum definitions.</span></span> <span data-ttu-id="f4a6a-456">Zie [about_Using](About/about_Using.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4a6a-456">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="f4a6a-457">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f4a6a-457">RELATED LINKS</span></span>

[<span data-ttu-id="f4a6a-458">Exporteren-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="f4a6a-458">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="f4a6a-459">Get-module</span><span class="sxs-lookup"><span data-stu-id="f4a6a-459">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="f4a6a-460">New-module</span><span class="sxs-lookup"><span data-stu-id="f4a6a-460">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="f4a6a-461">Remove-module</span><span class="sxs-lookup"><span data-stu-id="f4a6a-461">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="f4a6a-462">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="f4a6a-462">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
