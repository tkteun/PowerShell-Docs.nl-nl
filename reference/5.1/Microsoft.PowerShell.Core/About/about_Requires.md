---
description: Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: f8ff922fcf8deb710008bbd9bab619f137d6c831
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490700"
---
# <a name="about-requires"></a><span data-ttu-id="9035a-103">Over vereist</span><span class="sxs-lookup"><span data-stu-id="9035a-103">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="9035a-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="9035a-104">Short description</span></span>
<span data-ttu-id="9035a-105">Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.</span><span class="sxs-lookup"><span data-stu-id="9035a-105">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="9035a-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="9035a-106">Long description</span></span>

<span data-ttu-id="9035a-107">`#Requires`Met deze instructie wordt voor komen dat een script wordt uitgevoerd, tenzij aan de Power shell-versie, modules (en versie), modules (en versie) en aan de editie vereisten wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="9035a-107">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="9035a-108">Als niet aan de vereisten wordt voldaan, voert Power shell het script niet uit.</span><span class="sxs-lookup"><span data-stu-id="9035a-108">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="9035a-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="9035a-109">Syntax</span></span>

```
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="9035a-110">Zie [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)voor meer informatie over de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="9035a-110">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="9035a-111">Regels voor gebruik</span><span class="sxs-lookup"><span data-stu-id="9035a-111">Rules for use</span></span>

<span data-ttu-id="9035a-112">Een script kan meer dan één `#Requires` instructie bevatten.</span><span class="sxs-lookup"><span data-stu-id="9035a-112">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="9035a-113">De `#Requires` instructies kunnen op elke regel in een script worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9035a-113">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="9035a-114">Als u een `#Requires` instructie in een functie plaatst, wordt het bereik ervan niet beperkt.</span><span class="sxs-lookup"><span data-stu-id="9035a-114">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="9035a-115">Alle `#Requires` instructies worden altijd globaal toegepast en moeten worden voldaan voordat het script kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-115">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="9035a-116">Hoewel een `#Requires` instructie op een regel in een script kan worden weer gegeven, heeft de positie in een script geen invloed op de volg orde van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="9035a-116">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="9035a-117">De algemene status `#Requires` van de instructie moet worden voldaan voordat de uitvoering van het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-117">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="9035a-118">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-118">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="9035a-119">U kunt denken dat de bovenstaande code niet moet worden uitgevoerd omdat de vereiste module vóór de `#Requires` instructie is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9035a-119">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="9035a-120">Er moest echter wel `#Requires` aan de status worden voldaan voordat het script zelfs kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-120">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="9035a-121">De vereiste status is ongeldig voor de eerste regel van het script.</span><span class="sxs-lookup"><span data-stu-id="9035a-121">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="9035a-122">Parameters</span><span class="sxs-lookup"><span data-stu-id="9035a-122">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="9035a-123">-Assembly \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="9035a-123">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

> [!IMPORTANT]
> <span data-ttu-id="9035a-124">De `-Assembly` syntaxis is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="9035a-124">The `-Assembly` syntax is deprecated.</span></span> <span data-ttu-id="9035a-125">Deze functie is niet van toepassing.</span><span class="sxs-lookup"><span data-stu-id="9035a-125">It serves no function.</span></span> <span data-ttu-id="9035a-126">De syntaxis is toegevoegd aan Power shell 5,1, maar de ondersteunende code werd nooit geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-126">The syntax was added in PowerShell 5.1 but the supporting code was never implemented.</span></span> <span data-ttu-id="9035a-127">De syntaxis wordt nog steeds geaccepteerd voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="9035a-127">The syntax is still accepted for backward compatibility.</span></span>

<span data-ttu-id="9035a-128">Hiermee geeft u het pad naar het DLL-bestand van de assembly of een .NET-assembly-naam op.</span><span class="sxs-lookup"><span data-stu-id="9035a-128">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="9035a-129">De **Assembly** -para meter is geïntroduceerd in power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="9035a-129">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="9035a-130">Voor meer informatie over .NET-assembly's raadpleegt u [Assembly namen](/dotnet/standard/assembly/names).</span><span class="sxs-lookup"><span data-stu-id="9035a-130">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="9035a-131">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-131">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="9035a-132">-Versie \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="9035a-132">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="9035a-133">Hiermee geeft u de mini maal vereiste versie van Power shell voor het script.</span><span class="sxs-lookup"><span data-stu-id="9035a-133">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="9035a-134">Voer een primair versie nummer en een optioneel secundair versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="9035a-134">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="9035a-135">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-135">For example:</span></span>

```powershell
#Requires -Version 5.1
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="9035a-136">-PSSnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="9035a-136">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="9035a-137">Hiermee geeft u een Power shell-module op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="9035a-137">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="9035a-138">Voer de naam van de module en een optioneel versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="9035a-138">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="9035a-139">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-139">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="9035a-140">-Modules \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="9035a-140">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="9035a-141">Hiermee geeft u Power shell-modules op die door het script worden vereist.</span><span class="sxs-lookup"><span data-stu-id="9035a-141">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="9035a-142">Voer de module naam en een optioneel versie nummer in.</span><span class="sxs-lookup"><span data-stu-id="9035a-142">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="9035a-143">Als de vereiste modules zich niet in de huidige sessie bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-143">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="9035a-144">Als de modules niet kunnen worden geïmporteerd, genereert Power shell een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="9035a-144">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="9035a-145">Voor elke module typt u de module naam ( \<String\> ) of een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="9035a-145">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="9035a-146">De waarde kan bestaan uit een combi natie van teken reeksen en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="9035a-146">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="9035a-147">De hash-tabel bevat de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="9035a-147">The hash table has the following keys.</span></span>

- <span data-ttu-id="9035a-148">`ModuleName` - **Vereist** Hiermee geeft u de module naam op.</span><span class="sxs-lookup"><span data-stu-id="9035a-148">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="9035a-149">`GUID` - **Optioneel** Hiermee geeft u de GUID van de module.</span><span class="sxs-lookup"><span data-stu-id="9035a-149">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="9035a-150">Het is ook **vereist** om een van de drie onderstaande sleutels op te geven.</span><span class="sxs-lookup"><span data-stu-id="9035a-150">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="9035a-151">Deze sleutels kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9035a-151">These keys can't be used together.</span></span>
  - <span data-ttu-id="9035a-152">`ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="9035a-152">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="9035a-153">`RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="9035a-153">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="9035a-154">`MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.</span><span class="sxs-lookup"><span data-stu-id="9035a-154">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="9035a-155">`RequiredVersion` is toegevoegd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="9035a-155">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="9035a-156">`MaximumVersion` is toegevoegd in Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="9035a-156">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="9035a-157">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-157">For example:</span></span>

<span data-ttu-id="9035a-158">Vereisen dat `Hyper-V` (versie `1.1` of hoger) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-158">Require that `Hyper-V` (version `1.1` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; ModuleVersion="1.1" }
```

<span data-ttu-id="9035a-159">Vereist dat `Hyper-V` (**alleen** versie `1.1` ) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-159">Requires that `Hyper-V` (**only** version `1.1`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="1.1" }
```

<span data-ttu-id="9035a-160">Vereist dat `Hyper-V` (versie `1.1` of lager) is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-160">Requires that `Hyper-V` (version `1.1` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; MaximumVersion="1.1" }
```

<span data-ttu-id="9035a-161">Vereist dat elke versie van `PSScheduledJob` en `PSWorkflow` is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-161">Requires that any version of `PSScheduledJob` and `PSWorkflow`, is installed.</span></span>

```powershell
#Requires -Modules PSWorkflow, PSScheduledJob
```

<span data-ttu-id="9035a-162">Wanneer u de `RequiredVersion` sleutel gebruikt, moet u ervoor zorgen dat uw versie teken reeks precies overeenkomt met de versie teken reeks die u wilt vereisen.</span><span class="sxs-lookup"><span data-stu-id="9035a-162">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you wish to require.</span></span>

```powershell
Get-Module Hyper-V
```

```Output
ModuleType Version    Name     ExportedCommands
---------- -------    ----     ------------------
Binary     2.0.0.0    hyper-v  {Add-VMAssignableDevice, ...}
```

<span data-ttu-id="9035a-163">Het volgende voor beeld mislukt omdat **2.0.0** niet exact overeenkomt met **2.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="9035a-163">The following example fails because **2.0.0** doesn't exactly match **2.0.0.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="2.0.0" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="9035a-164">-PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="9035a-164">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="9035a-165">Hiermee geeft u een Power shell-editie op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="9035a-165">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="9035a-166">Geldige waarden zijn **kern geheugen** voor Power shell core en **Desktop** voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9035a-166">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="9035a-167">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-167">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="9035a-168">-ShellId</span><span class="sxs-lookup"><span data-stu-id="9035a-168">-ShellId</span></span>

<span data-ttu-id="9035a-169">Hiermee geeft u de shell op die door het script wordt vereist.</span><span class="sxs-lookup"><span data-stu-id="9035a-169">Specifies the shell that the script requires.</span></span> <span data-ttu-id="9035a-170">Voer de shell-ID in.</span><span class="sxs-lookup"><span data-stu-id="9035a-170">Enter the shell ID.</span></span> <span data-ttu-id="9035a-171">Als u de para meter **ShellId** gebruikt, moet u ook de para meter **PSSnapin** toevoegen.</span><span class="sxs-lookup"><span data-stu-id="9035a-171">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="9035a-172">U kunt de huidige **ShellId** vinden door de `$ShellId` Automatische variabele te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="9035a-172">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="9035a-173">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-173">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="9035a-174">Deze para meter is bedoeld voor gebruik in Mini shells, die zijn afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="9035a-174">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="9035a-175">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="9035a-175">-RunAsAdministrator</span></span>

<span data-ttu-id="9035a-176">Wanneer deze switch parameter wordt toegevoegd aan uw `#Requires` -instructie, wordt opgegeven dat de Power shell-sessie waarin u het script uitvoert, moet worden gestart met verhoogde gebruikers rechten.</span><span class="sxs-lookup"><span data-stu-id="9035a-176">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="9035a-177">De para meter **RunAsAdministrator** wordt genegeerd op een niet-Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="9035a-177">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="9035a-178">De para meter **RunAsAdministrator** is geïntroduceerd in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="9035a-178">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="9035a-179">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9035a-179">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="9035a-180">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="9035a-180">Examples</span></span>

<span data-ttu-id="9035a-181">Het volgende script heeft twee `#Requires` instructies.</span><span class="sxs-lookup"><span data-stu-id="9035a-181">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="9035a-182">Als de vereisten die zijn opgegeven in beide instructies niet worden voldaan, wordt het script niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9035a-182">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="9035a-183">Elke `#Requires` instructie moet het eerste item op een regel zijn:</span><span class="sxs-lookup"><span data-stu-id="9035a-183">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules PSWorkflow
#Requires -Version 3
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="9035a-184">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9035a-184">See also</span></span>

[<span data-ttu-id="9035a-185">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="9035a-185">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="9035a-186">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="9035a-186">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="9035a-187">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="9035a-187">about_PSSnapins</span></span>](about_PSSnapins.md)

[<span data-ttu-id="9035a-188">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="9035a-188">Get-PSSnapin</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSnapin)
