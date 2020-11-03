---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: a1052c357f19fd8f06eb39a14f8e8eded0c881a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250148"
---
# <span data-ttu-id="f7604-103">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="f7604-103">Remove-Module</span></span>

## <span data-ttu-id="f7604-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f7604-104">SYNOPSIS</span></span>
<span data-ttu-id="f7604-105">Verwijdert modules uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f7604-105">Removes modules from the current session.</span></span>

## <span data-ttu-id="f7604-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f7604-106">SYNTAX</span></span>

### <span data-ttu-id="f7604-107">name</span><span class="sxs-lookup"><span data-stu-id="f7604-107">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f7604-108">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f7604-108">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f7604-109">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="f7604-109">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f7604-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f7604-110">DESCRIPTION</span></span>

<span data-ttu-id="f7604-111">Met de cmdlet **Remove-module** worden de leden van een module, zoals cmdlets en functions, verwijderd uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f7604-111">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="f7604-112">Als de module een assembly (. dll) bevat, worden alle leden die door de assembly zijn geïmplementeerd, verwijderd, maar wordt de assembly niet uit het geheugen geladen.</span><span class="sxs-lookup"><span data-stu-id="f7604-112">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="f7604-113">Met deze cmdlet wordt de module niet verwijderd of verwijderd van de computer.</span><span class="sxs-lookup"><span data-stu-id="f7604-113">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="f7604-114">Dit is alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="f7604-114">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="f7604-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f7604-115">EXAMPLES</span></span>

### <span data-ttu-id="f7604-116">Voor beeld 1: een module verwijderen</span><span class="sxs-lookup"><span data-stu-id="f7604-116">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="f7604-117">Met deze opdracht wordt de BitsTransfer-module verwijderd uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f7604-117">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="f7604-118">Voor beeld 2: alle modules verwijderen</span><span class="sxs-lookup"><span data-stu-id="f7604-118">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="f7604-119">Met deze opdracht worden alle modules uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f7604-119">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="f7604-120">Voor beeld 3: modules verwijderen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="f7604-120">Example 3: Remove modules by using the pipeline</span></span>

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

<span data-ttu-id="f7604-121">Met deze opdracht verwijdert u de BitsTransfer-en PSDiagnostics-modules uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f7604-121">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="f7604-122">De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de module namen naar **Remove-module**.</span><span class="sxs-lookup"><span data-stu-id="f7604-122">The command uses a pipeline operator (|) to send the module names to **Remove-Module**.</span></span>
<span data-ttu-id="f7604-123">De *uitgebreide* algemene para meter wordt gebruikt om gedetailleerde informatie over de verwijderde leden op te halen.</span><span class="sxs-lookup"><span data-stu-id="f7604-123">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="f7604-124">De *uitgebreide* berichten tonen de items die worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f7604-124">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="f7604-125">De berichten verschillen omdat de BitsTransfer-module een assembly bevat waarmee de cmdlets en een geneste module met een eigen assembly worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="f7604-125">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="f7604-126">De PSDiagnostics-module bevat een module script bestand (. psm1) dat functies exporteert.</span><span class="sxs-lookup"><span data-stu-id="f7604-126">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="f7604-127">Voor beeld 4: een module verwijderen met behulp van ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="f7604-127">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="f7604-128">Met deze opdracht wordt de *ModuleInfo* -para meter gebruikt om de BitsTransfer-module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f7604-128">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="f7604-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7604-129">PARAMETERS</span></span>

### <span data-ttu-id="f7604-130">-Force</span><span class="sxs-lookup"><span data-stu-id="f7604-130">-Force</span></span>

<span data-ttu-id="f7604-131">Geeft aan dat met deze cmdlet alleen-lezen modules worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f7604-131">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="f7604-132">Standaard verwijdert **Remove-module** alleen de modules lezen/schrijven.</span><span class="sxs-lookup"><span data-stu-id="f7604-132">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="f7604-133">De **ReadOnly** -en **readwrite** -waarden worden opgeslagen in de eigenschap **AccessMode** van een module.</span><span class="sxs-lookup"><span data-stu-id="f7604-133">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="f7604-134">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f7604-134">-FullyQualifiedName</span></span>

<span data-ttu-id="f7604-135">Hiermee geeft u de volledig gekwalificeerde namen van modules op die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f7604-135">Specifies the fully qualified names of modules to remove.</span></span>

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

### <span data-ttu-id="f7604-136">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="f7604-136">-ModuleInfo</span></span>

<span data-ttu-id="f7604-137">Hiermee geeft u de module objecten die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f7604-137">Specifies the module objects to remove.</span></span>
<span data-ttu-id="f7604-138">Voer een variabele in die een module object ( **PSModuleInfo** ) bevat of een opdracht waarmee een module object wordt opgehaald, zoals een Get-Module opdracht.</span><span class="sxs-lookup"><span data-stu-id="f7604-138">Enter a variable that contains a module object ( **PSModuleInfo** ) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="f7604-139">U kunt module-objecten ook pipeen om te **verwijderen-module**.</span><span class="sxs-lookup"><span data-stu-id="f7604-139">You can also pipe module objects to **Remove-Module**.</span></span>

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

### <span data-ttu-id="f7604-140">-Name</span><span class="sxs-lookup"><span data-stu-id="f7604-140">-Name</span></span>

<span data-ttu-id="f7604-141">Hiermee geeft u de namen van de modules die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f7604-141">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="f7604-142">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f7604-142">Wildcard characters are permitted.</span></span>
<span data-ttu-id="f7604-143">U kunt ook de naam van de teken reeksen van de **invoeg module verplaatsen**.</span><span class="sxs-lookup"><span data-stu-id="f7604-143">You can also pipe name strings to **Remove-Module**.</span></span>

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

### <span data-ttu-id="f7604-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f7604-144">-Confirm</span></span>

<span data-ttu-id="f7604-145">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f7604-145">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f7604-146">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f7604-146">-WhatIf</span></span>

<span data-ttu-id="f7604-147">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f7604-147">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f7604-148">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f7604-148">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f7604-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7604-149">CommonParameters</span></span>

<span data-ttu-id="f7604-150">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7604-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7604-151">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f7604-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7604-152">INVOER</span><span class="sxs-lookup"><span data-stu-id="f7604-152">INPUTS</span></span>

### <span data-ttu-id="f7604-153">System. String, System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="f7604-153">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="f7604-154">U kunt module namen en module-objecten in een pipe **neerzetten** om de module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f7604-154">You can pipe module names and module objects to **Remove-Module**.</span></span>

## <span data-ttu-id="f7604-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f7604-155">OUTPUTS</span></span>

### <span data-ttu-id="f7604-156">Geen</span><span class="sxs-lookup"><span data-stu-id="f7604-156">None</span></span>

<span data-ttu-id="f7604-157">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f7604-157">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f7604-158">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f7604-158">NOTES</span></span>

## <span data-ttu-id="f7604-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f7604-159">RELATED LINKS</span></span>

[<span data-ttu-id="f7604-160">Get-module</span><span class="sxs-lookup"><span data-stu-id="f7604-160">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="f7604-161">Import-module</span><span class="sxs-lookup"><span data-stu-id="f7604-161">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="f7604-162">about_Modules</span><span class="sxs-lookup"><span data-stu-id="f7604-162">about_Modules</span></span>](About/about_Modules.md)
