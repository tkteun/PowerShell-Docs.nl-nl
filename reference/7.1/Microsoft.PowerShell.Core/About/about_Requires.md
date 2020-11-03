---
description: Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: 5c4eb4e272f214ffe906fd1a3f1c127824183d4a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252915"
---
# <a name="about-requires"></a><span data-ttu-id="ac20d-104">Over vereist</span><span class="sxs-lookup"><span data-stu-id="ac20d-104">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="ac20d-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="ac20d-105">Short description</span></span>
<span data-ttu-id="ac20d-106">Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.</span><span class="sxs-lookup"><span data-stu-id="ac20d-106">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="ac20d-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="ac20d-107">Long description</span></span>

<span data-ttu-id="ac20d-108">`#Requires`Met deze instructie wordt voor komen dat een script wordt uitgevoerd, tenzij aan de Power shell-versie, modules (en versie), modules (en versie) en aan de editie vereisten wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="ac20d-108">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="ac20d-109">Als niet aan de vereisten wordt voldaan, voert Power shell het script niet uit.</span><span class="sxs-lookup"><span data-stu-id="ac20d-109">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="ac20d-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac20d-110">Syntax</span></span>

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="ac20d-111">Zie [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)voor meer informatie over de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="ac20d-111">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="ac20d-112">Regels voor gebruik</span><span class="sxs-lookup"><span data-stu-id="ac20d-112">Rules for use</span></span>

<span data-ttu-id="ac20d-113">Een script kan meer dan één `#Requires` instructie bevatten.</span><span class="sxs-lookup"><span data-stu-id="ac20d-113">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="ac20d-114">De `#Requires` instructies kunnen op elke regel in een script worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ac20d-114">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="ac20d-115">Als u een `#Requires` instructie in een functie plaatst, wordt het bereik ervan niet beperkt.</span><span class="sxs-lookup"><span data-stu-id="ac20d-115">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="ac20d-116">Alle `#Requires` instructies worden altijd globaal toegepast en moeten worden voldaan voordat het script kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-116">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="ac20d-117">Hoewel een `#Requires` instructie op een regel in een script kan worden weer gegeven, heeft de positie in een script geen invloed op de volg orde van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="ac20d-117">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="ac20d-118">De algemene status `#Requires` van de instructie moet worden voldaan voordat de uitvoering van het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-118">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="ac20d-119">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-119">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="ac20d-120">U kunt denken dat de bovenstaande code niet moet worden uitgevoerd omdat de vereiste module vóór de `#Requires` instructie is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-120">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="ac20d-121">Er moest echter wel `#Requires` aan de status worden voldaan voordat het script zelfs kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-121">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="ac20d-122">De vereiste status is ongeldig voor de eerste regel van het script.</span><span class="sxs-lookup"><span data-stu-id="ac20d-122">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="ac20d-123">Parameters</span><span class="sxs-lookup"><span data-stu-id="ac20d-123">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="ac20d-124">-Assembly \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="ac20d-124">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

<span data-ttu-id="ac20d-125">Hiermee geeft u het pad naar het DLL-bestand van de assembly of een .NET-assembly-naam op.</span><span class="sxs-lookup"><span data-stu-id="ac20d-125">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="ac20d-126">De **Assembly** -para meter is geïntroduceerd in power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="ac20d-126">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="ac20d-127">Voor meer informatie over .NET-assembly's raadpleegt u [Assembly namen](/dotnet/standard/assembly/names).</span><span class="sxs-lookup"><span data-stu-id="ac20d-127">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="ac20d-128">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-128">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="ac20d-129">-Versie \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="ac20d-129">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="ac20d-130">Hiermee geeft u de mini maal vereiste versie van Power shell voor het script.</span><span class="sxs-lookup"><span data-stu-id="ac20d-130">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="ac20d-131">Voer een primair versie nummer en een optioneel secundair versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="ac20d-131">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="ac20d-132">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-132">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="ac20d-133">-PSSnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="ac20d-133">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="ac20d-134">Hiermee geeft u een Power shell-module op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="ac20d-134">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="ac20d-135">Voer de naam van de module en een optioneel versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="ac20d-135">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="ac20d-136">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-136">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="ac20d-137">-Modules \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="ac20d-137">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="ac20d-138">Hiermee geeft u Power shell-modules op die door het script worden vereist.</span><span class="sxs-lookup"><span data-stu-id="ac20d-138">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="ac20d-139">Voer de module naam en een optioneel versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="ac20d-139">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="ac20d-140">Als de vereiste modules zich niet in de huidige sessie bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-140">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="ac20d-141">Als de modules niet kunnen worden geïmporteerd, genereert Power shell een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="ac20d-141">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="ac20d-142">Voor elke module typt u de module naam ( \<String\> ) of een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="ac20d-142">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="ac20d-143">De waarde kan bestaan uit een combi natie van teken reeksen en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="ac20d-143">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="ac20d-144">De hash-tabel bevat de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="ac20d-144">The hash table has the following keys.</span></span>

- <span data-ttu-id="ac20d-145">`ModuleName` - **Vereist** Hiermee geeft u de module naam op.</span><span class="sxs-lookup"><span data-stu-id="ac20d-145">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="ac20d-146">`GUID` - **Optioneel** Hiermee geeft u de GUID van de module.</span><span class="sxs-lookup"><span data-stu-id="ac20d-146">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="ac20d-147">Het is ook **vereist** om een van de drie onderstaande sleutels op te geven.</span><span class="sxs-lookup"><span data-stu-id="ac20d-147">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="ac20d-148">Deze sleutels kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ac20d-148">These keys can't be used together.</span></span>
  - <span data-ttu-id="ac20d-149">`ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="ac20d-149">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="ac20d-150">`RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="ac20d-150">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="ac20d-151">`MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="ac20d-151">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="ac20d-152">`RequiredVersion` is toegevoegd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="ac20d-152">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="ac20d-153">`MaximumVersion` is toegevoegd in Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="ac20d-153">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="ac20d-154">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-154">For example:</span></span>

<span data-ttu-id="ac20d-155">Vereisen dat `AzureRM.Netcore` (versie `0.12.0` of hoger) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-155">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="ac20d-156">Vereisen dat `AzureRM.Netcore` ( **alleen** versie `0.12.0` ) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-156">Require that `AzureRM.Netcore` ( **only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="ac20d-157">Vereist dat `AzureRM.Netcore` (versie `0.12.0` of lager) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-157">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="ac20d-158">Vereisen dat elke versie van `AzureRM.Netcore` en `PowerShellGet` is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-158">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="ac20d-159">Wanneer u de `RequiredVersion` sleutel gebruikt, moet u ervoor zorgen dat uw versie teken reeks precies overeenkomt met de versie teken reeks die u nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="ac20d-159">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="ac20d-160">Het volgende voor beeld mislukt omdat **0,12** niet exact overeenkomt met **0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="ac20d-160">The following example fails because **0.12** doesn't exactly match **0.12.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="ac20d-161">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="ac20d-161">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="ac20d-162">Hiermee geeft u een Power shell-editie op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="ac20d-162">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="ac20d-163">Geldige waarden zijn **kern geheugen** voor Power shell core en **Desktop** voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="ac20d-163">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="ac20d-164">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-164">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="ac20d-165">-ShellId</span><span class="sxs-lookup"><span data-stu-id="ac20d-165">-ShellId</span></span>

<span data-ttu-id="ac20d-166">Hiermee geeft u de shell op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="ac20d-166">Specifies the shell that the script requires.</span></span> <span data-ttu-id="ac20d-167">Voer de shell-ID in.</span><span class="sxs-lookup"><span data-stu-id="ac20d-167">Enter the shell ID.</span></span> <span data-ttu-id="ac20d-168">Als u de para meter **ShellId** gebruikt, moet u ook de para meter **PSSnapin** toevoegen.</span><span class="sxs-lookup"><span data-stu-id="ac20d-168">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="ac20d-169">U kunt de huidige **ShellId** vinden door de `$ShellId` Automatische variabele te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="ac20d-169">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="ac20d-170">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-170">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="ac20d-171">Deze para meter is bedoeld voor gebruik in Mini shells, die zijn afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="ac20d-171">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="ac20d-172">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="ac20d-172">-RunAsAdministrator</span></span>

<span data-ttu-id="ac20d-173">Wanneer deze switch parameter wordt toegevoegd aan uw `#Requires` -instructie, wordt opgegeven dat de Power shell-sessie waarin u het script uitvoert, moet worden gestart met verhoogde gebruikers rechten.</span><span class="sxs-lookup"><span data-stu-id="ac20d-173">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="ac20d-174">De para meter **RunAsAdministrator** wordt genegeerd op een niet-Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="ac20d-174">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="ac20d-175">De para meter **RunAsAdministrator** is geïntroduceerd in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="ac20d-175">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="ac20d-176">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ac20d-176">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="ac20d-177">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="ac20d-177">Examples</span></span>

<span data-ttu-id="ac20d-178">Het volgende script heeft twee `#Requires` instructies.</span><span class="sxs-lookup"><span data-stu-id="ac20d-178">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="ac20d-179">Als de vereisten die zijn opgegeven in beide instructies niet worden voldaan, wordt het script niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac20d-179">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="ac20d-180">Elke `#Requires` instructie moet het eerste item op een regel zijn:</span><span class="sxs-lookup"><span data-stu-id="ac20d-180">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="ac20d-181">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ac20d-181">See also</span></span>

[<span data-ttu-id="ac20d-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="ac20d-182">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="ac20d-183">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="ac20d-183">about_Language_Keywords</span></span>](about_Language_Keywords.md)

