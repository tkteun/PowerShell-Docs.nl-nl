---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 427f50a697186354c889e85bf080189f5ee4af9c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249795"
---
# <span data-ttu-id="0ed25-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="0ed25-103">Uninstall-Module</span></span>

## <span data-ttu-id="0ed25-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0ed25-104">SYNOPSIS</span></span>
<span data-ttu-id="0ed25-105">Hiermee verwijdert u een module.</span><span class="sxs-lookup"><span data-stu-id="0ed25-105">Uninstalls a module.</span></span>

## <span data-ttu-id="0ed25-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0ed25-106">SYNTAX</span></span>

### <span data-ttu-id="0ed25-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="0ed25-107">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="0ed25-108">Input object</span><span class="sxs-lookup"><span data-stu-id="0ed25-108">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0ed25-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0ed25-109">DESCRIPTION</span></span>

<span data-ttu-id="0ed25-110">`Uninstall-Module`Met de cmdlet wordt een opgegeven module verwijderd van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0ed25-110">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="0ed25-111">U kunt een module niet verwijderen als deze andere modules als afhankelijkheden heeft.</span><span class="sxs-lookup"><span data-stu-id="0ed25-111">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="0ed25-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0ed25-112">EXAMPLES</span></span>

### <span data-ttu-id="0ed25-113">Voor beeld 1: een module verwijderen</span><span class="sxs-lookup"><span data-stu-id="0ed25-113">Example 1: Uninstall a module</span></span>

<span data-ttu-id="0ed25-114">In dit voor beeld wordt een module verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-114">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="0ed25-115">`Uninstall-Module` maakt gebruik van de para meter **name** om de module op te geven die u wilt verwijderen van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0ed25-115">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="0ed25-116">Voor beeld 2: de pijp lijn gebruiken om een module te verwijderen</span><span class="sxs-lookup"><span data-stu-id="0ed25-116">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="0ed25-117">In dit voor beeld wordt de pijp lijn gebruikt om een module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0ed25-117">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="0ed25-118">`Get-InstalledModule` maakt gebruik van de para meter **name** om de module op te geven.</span><span class="sxs-lookup"><span data-stu-id="0ed25-118">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="0ed25-119">Het object wordt naar de pijp lijn verzonden `Uninstall-Module` en wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-119">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="0ed25-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ed25-120">PARAMETERS</span></span>

### <span data-ttu-id="0ed25-121">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0ed25-121">-AllowPrerelease</span></span>

<span data-ttu-id="0ed25-122">Hiermee kunt u een module verwijderen die is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="0ed25-122">Allows you to uninstall a module marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0ed25-123">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="0ed25-123">-AllVersions</span></span>

<span data-ttu-id="0ed25-124">Hiermee geeft u aan dat u alle beschik bare versies van een module wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="0ed25-124">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="0ed25-125">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="0ed25-125">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0ed25-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0ed25-126">-Confirm</span></span>

<span data-ttu-id="0ed25-127">Vraagt u om bevestiging voordat de wordt uitgevoerd `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="0ed25-127">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="0ed25-128">-Force</span><span class="sxs-lookup"><span data-stu-id="0ed25-128">-Force</span></span>

<span data-ttu-id="0ed25-129">Er wordt geforceerd `Uninstall-Module` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-129">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0ed25-130">-Input object</span><span class="sxs-lookup"><span data-stu-id="0ed25-130">-InputObject</span></span>

<span data-ttu-id="0ed25-131">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="0ed25-132">Bijvoorbeeld: uitvoer `Get-InstalledModule` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="0ed25-132">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0ed25-133">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0ed25-133">-MaximumVersion</span></span>

<span data-ttu-id="0ed25-134">Hiermee geeft u het maximum of nieuwste versie van de module moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-134">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="0ed25-135">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="0ed25-135">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0ed25-136">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0ed25-136">-MinimumVersion</span></span>

<span data-ttu-id="0ed25-137">Hiermee geeft u de minimum versie op van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0ed25-137">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="0ed25-138">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="0ed25-138">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0ed25-139">-Name</span><span class="sxs-lookup"><span data-stu-id="0ed25-139">-Name</span></span>

<span data-ttu-id="0ed25-140">Hiermee geeft u een matrix van module namen op die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-140">Specifies an array of module names to uninstall.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0ed25-141">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0ed25-141">-RequiredVersion</span></span>

<span data-ttu-id="0ed25-142">Hiermee geeft u het exacte versie nummer van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0ed25-142">Specifies the exact version number of the module to uninstall.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0ed25-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0ed25-143">-WhatIf</span></span>

<span data-ttu-id="0ed25-144">Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Module` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-144">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="0ed25-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0ed25-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0ed25-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ed25-146">CommonParameters</span></span>

<span data-ttu-id="0ed25-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0ed25-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ed25-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0ed25-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0ed25-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="0ed25-149">INPUTS</span></span>

### <span data-ttu-id="0ed25-150">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0ed25-150">System.String[]</span></span>

### <span data-ttu-id="0ed25-151">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="0ed25-151">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="0ed25-152">System. String</span><span class="sxs-lookup"><span data-stu-id="0ed25-152">System.String</span></span>

## <span data-ttu-id="0ed25-153">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0ed25-153">OUTPUTS</span></span>

### <span data-ttu-id="0ed25-154">System. object</span><span class="sxs-lookup"><span data-stu-id="0ed25-154">System.Object</span></span>

## <span data-ttu-id="0ed25-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0ed25-155">NOTES</span></span>

## <span data-ttu-id="0ed25-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0ed25-156">RELATED LINKS</span></span>

[<span data-ttu-id="0ed25-157">Find-Module</span><span class="sxs-lookup"><span data-stu-id="0ed25-157">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="0ed25-158">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="0ed25-158">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="0ed25-159">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="0ed25-159">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="0ed25-160">Save-Module</span><span class="sxs-lookup"><span data-stu-id="0ed25-160">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="0ed25-161">Update-Module</span><span class="sxs-lookup"><span data-stu-id="0ed25-161">Update-Module</span></span>](Update-Module.md)
