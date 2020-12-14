---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: d20a348f3f5ba193eb85e0f9d0e2cc11ad083b47
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705888"
---
# <span data-ttu-id="5a920-102">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="5a920-102">Remove-PSDrive</span></span>

## <span data-ttu-id="5a920-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5a920-103">SYNOPSIS</span></span>
<span data-ttu-id="5a920-104">Verwijdert tijdelijke Power Shell-stations en verbreekt de verbinding van toegewezen netwerk stations.</span><span class="sxs-lookup"><span data-stu-id="5a920-104">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="5a920-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5a920-105">SYNTAX</span></span>

### <span data-ttu-id="5a920-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="5a920-106">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5a920-107">Letterlijke waarde</span><span class="sxs-lookup"><span data-stu-id="5a920-107">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5a920-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5a920-108">DESCRIPTION</span></span>

<span data-ttu-id="5a920-109">De `Remove-PSDrive` cmdlet verwijdert tijdelijke Power Shell-stations die zijn gemaakt met behulp van de- `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a920-109">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="5a920-110">Met ingang van Windows Power Shell 3,0 `Remove-PSDrive` verbreekt ook de verbinding met toegewezen netwerk stations, inclusief, maar niet beperkt tot, stations die zijn gemaakt met behulp `Persist` van de para meter van `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="5a920-110">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="5a920-111">`Remove-PSDrive` kan fysieke of logische stations van Windows niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5a920-111">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="5a920-112">Vanaf Windows Power Shell 3,0, wanneer een extern station is verbonden met de computer, wordt door Power shell automatisch een PSDrive toegevoegd aan het bestands systeem dat het nieuwe station vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5a920-112">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="5a920-113">U hoeft Power shell niet opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="5a920-113">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="5a920-114">Op dezelfde manier verwijdert Power shell automatisch de PSDrive die de verwijderde schijf vertegenwoordigt wanneer een extern station wordt losgekoppeld van de computer.</span><span class="sxs-lookup"><span data-stu-id="5a920-114">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="5a920-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5a920-115">EXAMPLES</span></span>

### <span data-ttu-id="5a920-116">Voor beeld 1: een bestandssysteem station verwijderen</span><span class="sxs-lookup"><span data-stu-id="5a920-116">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="5a920-117">Met deze opdracht wordt een tijdelijk bestandssysteem station met de naam "smp" verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5a920-117">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="5a920-118">Voor beeld 2: toegewezen netwerk stations verwijderen</span><span class="sxs-lookup"><span data-stu-id="5a920-118">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="5a920-119">Met deze opdracht wordt gebruikt `Remove-PSDrive` om de verbinding met de X: en S: toegewezen netwerk stations te verbreken.</span><span class="sxs-lookup"><span data-stu-id="5a920-119">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="5a920-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a920-120">PARAMETERS</span></span>

### <span data-ttu-id="5a920-121">-Force</span><span class="sxs-lookup"><span data-stu-id="5a920-121">-Force</span></span>

<span data-ttu-id="5a920-122">Hiermee verwijdert u het huidige Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="5a920-122">Removes the current PowerShell drive.</span></span>

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

### <span data-ttu-id="5a920-123">-Literal-waarde</span><span class="sxs-lookup"><span data-stu-id="5a920-123">-LiteralName</span></span>

<span data-ttu-id="5a920-124">Hiermee geeft u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="5a920-124">Specifies the name of the drive.</span></span>

<span data-ttu-id="5a920-125">De waarde van **literal** wordt exact als getypt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a920-125">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="5a920-126">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="5a920-126">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="5a920-127">Als de naam escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens (').</span><span class="sxs-lookup"><span data-stu-id="5a920-127">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="5a920-128">Enkele aanhalings tekens geven Power shell opdracht instructies niet te interpreteren als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="5a920-128">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a920-129">-Name</span><span class="sxs-lookup"><span data-stu-id="5a920-129">-Name</span></span>

<span data-ttu-id="5a920-130">Hiermee geeft u de namen van de stations die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5a920-130">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="5a920-131">Typ geen dubbele punt (:) na de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="5a920-131">Do not type a colon (:) after the drive name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="5a920-132">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="5a920-132">-PSProvider</span></span>

<span data-ttu-id="5a920-133">Hiermee wordt een matrix met **PSProvider** -objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5a920-133">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="5a920-134">Met deze cmdlet worden alle stations die zijn gekoppeld aan de opgegeven Power shell-provider, verwijderd en verbroken.</span><span class="sxs-lookup"><span data-stu-id="5a920-134">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a920-135">-Bereik</span><span class="sxs-lookup"><span data-stu-id="5a920-135">-Scope</span></span>

<span data-ttu-id="5a920-136">Hiermee geeft u een bereik voor het station.</span><span class="sxs-lookup"><span data-stu-id="5a920-136">Specifies a scope for the drive.</span></span>
<span data-ttu-id="5a920-137">De acceptabele waarden voor deze para meter zijn: Global, local en script, of een getal dat relatief is ten opzichte van het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="5a920-137">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="5a920-138">Bereiken nummer 0 tot het aantal bereiken.</span><span class="sxs-lookup"><span data-stu-id="5a920-138">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="5a920-139">Het huidige bereik nummer is 0 en de bovenliggende waarde is 1.</span><span class="sxs-lookup"><span data-stu-id="5a920-139">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="5a920-140">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a920-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a920-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5a920-141">-Confirm</span></span>

<span data-ttu-id="5a920-142">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5a920-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5a920-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5a920-143">-WhatIf</span></span>

<span data-ttu-id="5a920-144">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5a920-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5a920-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5a920-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5a920-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a920-146">CommonParameters</span></span>

<span data-ttu-id="5a920-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a920-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a920-148">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a920-148">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5a920-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="5a920-149">INPUTS</span></span>

### <span data-ttu-id="5a920-150">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="5a920-150">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="5a920-151">U kunt een schijf object, zoals een, van de `Get-PSDrive` cmdlet, naar de cmdlet pipeen `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="5a920-151">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="5a920-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5a920-152">OUTPUTS</span></span>

### <span data-ttu-id="5a920-153">Geen</span><span class="sxs-lookup"><span data-stu-id="5a920-153">None</span></span>

<span data-ttu-id="5a920-154">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5a920-154">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="5a920-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5a920-155">NOTES</span></span>

- <span data-ttu-id="5a920-156">De `Remove-PSDrive` cmdlet is ontworpen om te werken met de gegevens die door elke Power shell-provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5a920-156">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="5a920-157">Gebruik de cmdlet om de providers in uw sessie weer te geven `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="5a920-157">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="5a920-158">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a920-158">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="5a920-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5a920-159">RELATED LINKS</span></span>

[<span data-ttu-id="5a920-160">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="5a920-160">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="5a920-161">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="5a920-161">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="5a920-162">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5a920-162">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

