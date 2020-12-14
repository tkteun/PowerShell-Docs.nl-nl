---
description: Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: efae9689a1abc96b04a7d8d5ac524c61b73152ca
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705646"
---
# <a name="about-requires"></a><span data-ttu-id="f6f49-103">Over vereist</span><span class="sxs-lookup"><span data-stu-id="f6f49-103">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="f6f49-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="f6f49-104">Short description</span></span>
<span data-ttu-id="f6f49-105">Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.</span><span class="sxs-lookup"><span data-stu-id="f6f49-105">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="f6f49-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="f6f49-106">Long description</span></span>

<span data-ttu-id="f6f49-107">`#Requires`Met deze instructie wordt voor komen dat een script wordt uitgevoerd, tenzij aan de Power shell-versie, modules (en versie), modules (en versie) en aan de editie vereisten wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="f6f49-107">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="f6f49-108">Als niet aan de vereisten wordt voldaan, voert Power shell het script niet uit.</span><span class="sxs-lookup"><span data-stu-id="f6f49-108">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="f6f49-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6f49-109">Syntax</span></span>

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="f6f49-110">Zie [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)voor meer informatie over de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="f6f49-110">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="f6f49-111">Regels voor gebruik</span><span class="sxs-lookup"><span data-stu-id="f6f49-111">Rules for use</span></span>

<span data-ttu-id="f6f49-112">Een script kan meer dan één `#Requires` instructie bevatten.</span><span class="sxs-lookup"><span data-stu-id="f6f49-112">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="f6f49-113">De `#Requires` instructies kunnen op elke regel in een script worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f6f49-113">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="f6f49-114">Als u een `#Requires` instructie in een functie plaatst, wordt het bereik ervan niet beperkt.</span><span class="sxs-lookup"><span data-stu-id="f6f49-114">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="f6f49-115">Alle `#Requires` instructies worden altijd globaal toegepast en moeten worden voldaan voordat het script kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-115">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="f6f49-116">Hoewel een `#Requires` instructie op een regel in een script kan worden weer gegeven, heeft de positie in een script geen invloed op de volg orde van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="f6f49-116">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="f6f49-117">De algemene status `#Requires` van de instructie moet worden voldaan voordat de uitvoering van het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-117">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="f6f49-118">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-118">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="f6f49-119">U kunt denken dat de bovenstaande code niet moet worden uitgevoerd omdat de vereiste module vóór de `#Requires` instructie is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-119">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="f6f49-120">Er moest echter wel `#Requires` aan de status worden voldaan voordat het script zelfs kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-120">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="f6f49-121">De vereiste status is ongeldig voor de eerste regel van het script.</span><span class="sxs-lookup"><span data-stu-id="f6f49-121">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6f49-122">Parameters</span><span class="sxs-lookup"><span data-stu-id="f6f49-122">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="f6f49-123">-Assembly \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="f6f49-123">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

<span data-ttu-id="f6f49-124">Hiermee geeft u het pad naar het DLL-bestand van de assembly of een .NET-assembly-naam op.</span><span class="sxs-lookup"><span data-stu-id="f6f49-124">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="f6f49-125">De **Assembly** -para meter is geïntroduceerd in power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="f6f49-125">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="f6f49-126">Voor meer informatie over .NET-assembly's raadpleegt u [Assembly namen](/dotnet/standard/assembly/names).</span><span class="sxs-lookup"><span data-stu-id="f6f49-126">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="f6f49-127">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-127">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="f6f49-128">-Versie \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="f6f49-128">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="f6f49-129">Hiermee geeft u de mini maal vereiste versie van Power shell voor het script.</span><span class="sxs-lookup"><span data-stu-id="f6f49-129">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="f6f49-130">Voer een primair versie nummer en een optioneel secundair versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="f6f49-130">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="f6f49-131">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-131">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="f6f49-132">-PSSnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="f6f49-132">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="f6f49-133">Hiermee geeft u een Power shell-module op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="f6f49-133">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="f6f49-134">Voer de naam van de module en een optioneel versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="f6f49-134">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="f6f49-135">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-135">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="f6f49-136">-Modules \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="f6f49-136">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="f6f49-137">Hiermee geeft u Power shell-modules op die door het script worden vereist.</span><span class="sxs-lookup"><span data-stu-id="f6f49-137">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="f6f49-138">Voer de module naam en een optioneel versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="f6f49-138">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="f6f49-139">Als de vereiste modules zich niet in de huidige sessie bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-139">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="f6f49-140">Als de modules niet kunnen worden geïmporteerd, genereert Power shell een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="f6f49-140">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="f6f49-141">Voor elke module typt u de module naam ( \<String\> ) of een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="f6f49-141">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="f6f49-142">De waarde kan bestaan uit een combi natie van teken reeksen en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="f6f49-142">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="f6f49-143">De hash-tabel bevat de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="f6f49-143">The hash table has the following keys.</span></span>

- <span data-ttu-id="f6f49-144">`ModuleName` - **Vereist** Hiermee geeft u de module naam op.</span><span class="sxs-lookup"><span data-stu-id="f6f49-144">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="f6f49-145">`GUID` - **Optioneel** Hiermee geeft u de GUID van de module.</span><span class="sxs-lookup"><span data-stu-id="f6f49-145">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="f6f49-146">Het is ook **vereist** om een van de drie onderstaande sleutels op te geven.</span><span class="sxs-lookup"><span data-stu-id="f6f49-146">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="f6f49-147">Deze sleutels kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f6f49-147">These keys can't be used together.</span></span>
  - <span data-ttu-id="f6f49-148">`ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="f6f49-148">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="f6f49-149">`RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="f6f49-149">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="f6f49-150">`MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="f6f49-150">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="f6f49-151">`RequiredVersion` is toegevoegd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="f6f49-151">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="f6f49-152">`MaximumVersion` is toegevoegd in Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="f6f49-152">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="f6f49-153">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-153">For example:</span></span>

<span data-ttu-id="f6f49-154">Vereisen dat `AzureRM.Netcore` (versie `0.12.0` of hoger) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-154">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="f6f49-155">Vereisen dat `AzureRM.Netcore` (**alleen** versie `0.12.0` ) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-155">Require that `AzureRM.Netcore` (**only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="f6f49-156">Vereist dat `AzureRM.Netcore` (versie `0.12.0` of lager) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-156">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="f6f49-157">Vereisen dat elke versie van `AzureRM.Netcore` en `PowerShellGet` is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-157">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="f6f49-158">Wanneer u de `RequiredVersion` sleutel gebruikt, moet u ervoor zorgen dat uw versie teken reeks precies overeenkomt met de versie teken reeks die u nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="f6f49-158">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="f6f49-159">Het volgende voor beeld mislukt omdat **0,12** niet exact overeenkomt met **0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="f6f49-159">The following example fails because **0.12** doesn't exactly match **0.12.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="f6f49-160">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="f6f49-160">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="f6f49-161">Hiermee geeft u een Power shell-editie op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="f6f49-161">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="f6f49-162">Geldige waarden zijn **kern geheugen** voor Power shell core en **Desktop** voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="f6f49-162">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="f6f49-163">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-163">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="f6f49-164">-ShellId</span><span class="sxs-lookup"><span data-stu-id="f6f49-164">-ShellId</span></span>

<span data-ttu-id="f6f49-165">Hiermee geeft u de shell op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="f6f49-165">Specifies the shell that the script requires.</span></span> <span data-ttu-id="f6f49-166">Voer de shell-ID in.</span><span class="sxs-lookup"><span data-stu-id="f6f49-166">Enter the shell ID.</span></span> <span data-ttu-id="f6f49-167">Als u de para meter **ShellId** gebruikt, moet u ook de para meter **PSSnapin** toevoegen.</span><span class="sxs-lookup"><span data-stu-id="f6f49-167">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="f6f49-168">U kunt de huidige **ShellId** vinden door de `$ShellId` Automatische variabele te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="f6f49-168">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="f6f49-169">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-169">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="f6f49-170">Deze para meter is bedoeld voor gebruik in Mini shells, die zijn afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="f6f49-170">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="f6f49-171">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="f6f49-171">-RunAsAdministrator</span></span>

<span data-ttu-id="f6f49-172">Wanneer deze switch parameter wordt toegevoegd aan uw `#Requires` -instructie, wordt opgegeven dat de Power shell-sessie waarin u het script uitvoert, moet worden gestart met verhoogde gebruikers rechten.</span><span class="sxs-lookup"><span data-stu-id="f6f49-172">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="f6f49-173">De para meter **RunAsAdministrator** wordt genegeerd op een niet-Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="f6f49-173">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="f6f49-174">De para meter **RunAsAdministrator** is geïntroduceerd in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="f6f49-174">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="f6f49-175">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6f49-175">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="f6f49-176">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f6f49-176">Examples</span></span>

<span data-ttu-id="f6f49-177">Het volgende script heeft twee `#Requires` instructies.</span><span class="sxs-lookup"><span data-stu-id="f6f49-177">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="f6f49-178">Als de vereisten die zijn opgegeven in beide instructies niet worden voldaan, wordt het script niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f6f49-178">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="f6f49-179">Elke `#Requires` instructie moet het eerste item op een regel zijn:</span><span class="sxs-lookup"><span data-stu-id="f6f49-179">Each `#Requires` statement must be the first item on a line:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f6f49-180">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6f49-180">See also</span></span>

[<span data-ttu-id="f6f49-181">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="f6f49-181">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="f6f49-182">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="f6f49-182">about_Language_Keywords</span></span>](about_Language_Keywords.md)

