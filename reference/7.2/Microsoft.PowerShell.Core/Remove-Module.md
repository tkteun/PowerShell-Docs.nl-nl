---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: 2954bbec68b837a73e5365ab6a1e8ecb501d4898
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706047"
---
# <span data-ttu-id="40b86-102">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="40b86-102">Remove-Module</span></span>

## <span data-ttu-id="40b86-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="40b86-103">SYNOPSIS</span></span>
<span data-ttu-id="40b86-104">Verwijdert modules uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="40b86-104">Removes modules from the current session.</span></span>

## <span data-ttu-id="40b86-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="40b86-105">SYNTAX</span></span>

### <span data-ttu-id="40b86-106">naam</span><span class="sxs-lookup"><span data-stu-id="40b86-106">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="40b86-107">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="40b86-107">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="40b86-108">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="40b86-108">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="40b86-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="40b86-109">DESCRIPTION</span></span>

<span data-ttu-id="40b86-110">Met de cmdlet **Remove-module** worden de leden van een module, zoals cmdlets en functions, verwijderd uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="40b86-110">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="40b86-111">Als de module een assembly (. dll) bevat, worden alle leden die door de assembly zijn geïmplementeerd, verwijderd, maar wordt de assembly niet uit het geheugen geladen.</span><span class="sxs-lookup"><span data-stu-id="40b86-111">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="40b86-112">Met deze cmdlet wordt de module niet verwijderd of verwijderd van de computer.</span><span class="sxs-lookup"><span data-stu-id="40b86-112">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="40b86-113">Dit is alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="40b86-113">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="40b86-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="40b86-114">EXAMPLES</span></span>

### <span data-ttu-id="40b86-115">Voor beeld 1: een module verwijderen</span><span class="sxs-lookup"><span data-stu-id="40b86-115">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="40b86-116">Met deze opdracht wordt de BitsTransfer-module verwijderd uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="40b86-116">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="40b86-117">Voor beeld 2: alle modules verwijderen</span><span class="sxs-lookup"><span data-stu-id="40b86-117">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="40b86-118">Met deze opdracht worden alle modules uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40b86-118">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="40b86-119">Voor beeld 3: modules verwijderen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="40b86-119">Example 3: Remove modules by using the pipeline</span></span>

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

<span data-ttu-id="40b86-120">Met deze opdracht verwijdert u de BitsTransfer-en PSDiagnostics-modules uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="40b86-120">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="40b86-121">De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de module namen naar **Remove-module**.</span><span class="sxs-lookup"><span data-stu-id="40b86-121">The command uses a pipeline operator (|) to send the module names to **Remove-Module**.</span></span>
<span data-ttu-id="40b86-122">De *uitgebreide* algemene para meter wordt gebruikt om gedetailleerde informatie over de verwijderde leden op te halen.</span><span class="sxs-lookup"><span data-stu-id="40b86-122">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="40b86-123">De *uitgebreide* berichten tonen de items die worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40b86-123">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="40b86-124">De berichten verschillen omdat de BitsTransfer-module een assembly bevat waarmee de cmdlets en een geneste module met een eigen assembly worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="40b86-124">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="40b86-125">De PSDiagnostics-module bevat een module script bestand (. psm1) dat functies exporteert.</span><span class="sxs-lookup"><span data-stu-id="40b86-125">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="40b86-126">Voor beeld 4: een module verwijderen met behulp van ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="40b86-126">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="40b86-127">Met deze opdracht wordt de *ModuleInfo* -para meter gebruikt om de BitsTransfer-module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="40b86-127">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="40b86-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="40b86-128">PARAMETERS</span></span>

### <span data-ttu-id="40b86-129">-Force</span><span class="sxs-lookup"><span data-stu-id="40b86-129">-Force</span></span>

<span data-ttu-id="40b86-130">Geeft aan dat met deze cmdlet alleen-lezen modules worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40b86-130">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="40b86-131">Standaard verwijdert **Remove-module** alleen de modules lezen/schrijven.</span><span class="sxs-lookup"><span data-stu-id="40b86-131">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="40b86-132">De **ReadOnly** -en **readwrite** -waarden worden opgeslagen in de eigenschap **AccessMode** van een module.</span><span class="sxs-lookup"><span data-stu-id="40b86-132">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="40b86-133">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="40b86-133">-FullyQualifiedName</span></span>

<span data-ttu-id="40b86-134">Hiermee geeft u de volledig gekwalificeerde namen van modules op die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40b86-134">Specifies the fully qualified names of modules to remove.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="40b86-135">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="40b86-135">-ModuleInfo</span></span>

<span data-ttu-id="40b86-136">Hiermee geeft u de module objecten die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40b86-136">Specifies the module objects to remove.</span></span>
<span data-ttu-id="40b86-137">Voer een variabele in die een module object (**PSModuleInfo**) bevat of een opdracht waarmee een module object wordt opgehaald, zoals een Get-Module opdracht.</span><span class="sxs-lookup"><span data-stu-id="40b86-137">Enter a variable that contains a module object (**PSModuleInfo**) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="40b86-138">U kunt module-objecten ook pipeen om te **verwijderen-module**.</span><span class="sxs-lookup"><span data-stu-id="40b86-138">You can also pipe module objects to **Remove-Module**.</span></span>

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

### <span data-ttu-id="40b86-139">-Name</span><span class="sxs-lookup"><span data-stu-id="40b86-139">-Name</span></span>

<span data-ttu-id="40b86-140">Hiermee geeft u de namen van de modules die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="40b86-140">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="40b86-141">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="40b86-141">Wildcard characters are permitted.</span></span>
<span data-ttu-id="40b86-142">U kunt ook de naam van de teken reeksen van de **invoeg module verplaatsen**.</span><span class="sxs-lookup"><span data-stu-id="40b86-142">You can also pipe name strings to **Remove-Module**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="40b86-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="40b86-143">-Confirm</span></span>

<span data-ttu-id="40b86-144">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="40b86-144">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40b86-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="40b86-145">-WhatIf</span></span>

<span data-ttu-id="40b86-146">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="40b86-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="40b86-147">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="40b86-147">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40b86-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40b86-148">CommonParameters</span></span>

<span data-ttu-id="40b86-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="40b86-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40b86-150">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40b86-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="40b86-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="40b86-151">INPUTS</span></span>

### <span data-ttu-id="40b86-152">System. String, System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="40b86-152">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="40b86-153">U kunt module namen en module-objecten in een pipe **neerzetten** om de module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="40b86-153">You can pipe module names and module objects to **Remove-Module**.</span></span>

## <span data-ttu-id="40b86-154">UITVOER</span><span class="sxs-lookup"><span data-stu-id="40b86-154">OUTPUTS</span></span>

### <span data-ttu-id="40b86-155">Geen</span><span class="sxs-lookup"><span data-stu-id="40b86-155">None</span></span>

<span data-ttu-id="40b86-156">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="40b86-156">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="40b86-157">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="40b86-157">NOTES</span></span>

<span data-ttu-id="40b86-158">Wanneer u een module verwijdert, is er een gebeurtenis in de module die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="40b86-158">When removing a module, there is an event on the module that will execute.</span></span>
<span data-ttu-id="40b86-159">Met deze gebeurtenis kan een module reageren op het verwijderen en enige opschoning uitvoeren, zoals het vrijmaken van resources.</span><span class="sxs-lookup"><span data-stu-id="40b86-159">This event allows a module to react to being removed and perform some cleanup such as freeing up resources.</span></span> <span data-ttu-id="40b86-160">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="40b86-160">Example:</span></span>

<span data-ttu-id="40b86-161">$OnRemoveScript = {</span><span class="sxs-lookup"><span data-stu-id="40b86-161">$OnRemoveScript = {</span></span>

  <span data-ttu-id="40b86-162">\# opschonen uitvoeren</span><span class="sxs-lookup"><span data-stu-id="40b86-162">\# perform cleanup</span></span>

  <span data-ttu-id="40b86-163">$cachedSessions | Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="40b86-163">$cachedSessions | Remove-PSSession</span></span>

<span data-ttu-id="40b86-164">}</span><span class="sxs-lookup"><span data-stu-id="40b86-164">}</span></span>

<span data-ttu-id="40b86-165">$ExecutionContext. SessionState. module. OnRemove + = $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="40b86-165">$ExecutionContext.SessionState.Module.OnRemove += $OnRemoveScript</span></span>

<span data-ttu-id="40b86-166">Voor volledige consistentie is het wellicht ook handig om te reageren op het sluiten van het Power Shell-proces:</span><span class="sxs-lookup"><span data-stu-id="40b86-166">For full consistency, it might be also useful to react to the closing of the PowerShell process:</span></span>

<span data-ttu-id="40b86-167">Register-EngineEvent-SourceIdentifier ([System. Management. Automation. PsEngineEvent]:: Exit)-actie $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="40b86-167">Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Action $OnRemoveScript</span></span>

## <span data-ttu-id="40b86-168">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="40b86-168">RELATED LINKS</span></span>

[<span data-ttu-id="40b86-169">Get-module</span><span class="sxs-lookup"><span data-stu-id="40b86-169">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="40b86-170">Import-module</span><span class="sxs-lookup"><span data-stu-id="40b86-170">Import-Module</span></span>](Import-Module.md)

