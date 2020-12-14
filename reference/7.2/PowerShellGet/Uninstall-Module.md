---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 0df911ad8b1f7b4516eef4a1c2b0180893013e3e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706143"
---
# <span data-ttu-id="1b85e-102">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="1b85e-102">Uninstall-Module</span></span>

## <span data-ttu-id="1b85e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1b85e-103">SYNOPSIS</span></span>
<span data-ttu-id="1b85e-104">Hiermee verwijdert u een module.</span><span class="sxs-lookup"><span data-stu-id="1b85e-104">Uninstalls a module.</span></span>

## <span data-ttu-id="1b85e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1b85e-105">SYNTAX</span></span>

### <span data-ttu-id="1b85e-106">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="1b85e-106">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1b85e-107">Input object</span><span class="sxs-lookup"><span data-stu-id="1b85e-107">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1b85e-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1b85e-108">DESCRIPTION</span></span>

<span data-ttu-id="1b85e-109">`Uninstall-Module`Met de cmdlet wordt een opgegeven module verwijderd van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1b85e-109">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="1b85e-110">U kunt een module niet verwijderen als deze andere modules als afhankelijkheden heeft.</span><span class="sxs-lookup"><span data-stu-id="1b85e-110">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="1b85e-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1b85e-111">EXAMPLES</span></span>

### <span data-ttu-id="1b85e-112">Voor beeld 1: een module verwijderen</span><span class="sxs-lookup"><span data-stu-id="1b85e-112">Example 1: Uninstall a module</span></span>

<span data-ttu-id="1b85e-113">In dit voor beeld wordt een module verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-113">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="1b85e-114">`Uninstall-Module` maakt gebruik van de para meter **name** om de module op te geven die u wilt verwijderen van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1b85e-114">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="1b85e-115">Voor beeld 2: de pijp lijn gebruiken om een module te verwijderen</span><span class="sxs-lookup"><span data-stu-id="1b85e-115">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="1b85e-116">In dit voor beeld wordt de pijp lijn gebruikt om een module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1b85e-116">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="1b85e-117">`Get-InstalledModule` maakt gebruik van de para meter **name** om de module op te geven.</span><span class="sxs-lookup"><span data-stu-id="1b85e-117">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="1b85e-118">Het object wordt naar de pijp lijn verzonden `Uninstall-Module` en wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-118">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="1b85e-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1b85e-119">PARAMETERS</span></span>

### <span data-ttu-id="1b85e-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="1b85e-120">-AllowPrerelease</span></span>

<span data-ttu-id="1b85e-121">Hiermee kunt u een module verwijderen die is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="1b85e-121">Allows you to uninstall a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="1b85e-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="1b85e-122">-AllVersions</span></span>

<span data-ttu-id="1b85e-123">Hiermee geeft u aan dat u alle beschik bare versies van een module wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="1b85e-123">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="1b85e-124">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion**, **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="1b85e-124">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="1b85e-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1b85e-125">-Confirm</span></span>

<span data-ttu-id="1b85e-126">Vraagt u om bevestiging voordat de wordt uitgevoerd `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="1b85e-126">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="1b85e-127">-Force</span><span class="sxs-lookup"><span data-stu-id="1b85e-127">-Force</span></span>

<span data-ttu-id="1b85e-128">Er wordt geforceerd `Uninstall-Module` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-128">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="1b85e-129">-Input object</span><span class="sxs-lookup"><span data-stu-id="1b85e-129">-InputObject</span></span>

<span data-ttu-id="1b85e-130">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-130">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="1b85e-131">Bijvoorbeeld: uitvoer `Get-InstalledModule` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="1b85e-131">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="1b85e-132">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1b85e-132">-MaximumVersion</span></span>

<span data-ttu-id="1b85e-133">Hiermee geeft u het maximum of nieuwste versie van de module moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-133">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="1b85e-134">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="1b85e-134">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="1b85e-135">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1b85e-135">-MinimumVersion</span></span>

<span data-ttu-id="1b85e-136">Hiermee geeft u de minimum versie op van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1b85e-136">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="1b85e-137">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="1b85e-137">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="1b85e-138">-Name</span><span class="sxs-lookup"><span data-stu-id="1b85e-138">-Name</span></span>

<span data-ttu-id="1b85e-139">Hiermee geeft u een matrix van module namen op die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-139">Specifies an array of module names to uninstall.</span></span>

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

### <span data-ttu-id="1b85e-140">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1b85e-140">-RequiredVersion</span></span>

<span data-ttu-id="1b85e-141">Hiermee geeft u het exacte versie nummer van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1b85e-141">Specifies the exact version number of the module to uninstall.</span></span>

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

### <span data-ttu-id="1b85e-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1b85e-142">-WhatIf</span></span>

<span data-ttu-id="1b85e-143">Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Module` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-143">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="1b85e-144">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1b85e-144">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="1b85e-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b85e-145">CommonParameters</span></span>

<span data-ttu-id="1b85e-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b85e-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b85e-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1b85e-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b85e-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="1b85e-148">INPUTS</span></span>

### <span data-ttu-id="1b85e-149">System.String[]</span><span class="sxs-lookup"><span data-stu-id="1b85e-149">System.String[]</span></span>

### <span data-ttu-id="1b85e-150">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="1b85e-150">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="1b85e-151">System. String</span><span class="sxs-lookup"><span data-stu-id="1b85e-151">System.String</span></span>

## <span data-ttu-id="1b85e-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1b85e-152">OUTPUTS</span></span>

### <span data-ttu-id="1b85e-153">System. object</span><span class="sxs-lookup"><span data-stu-id="1b85e-153">System.Object</span></span>

## <span data-ttu-id="1b85e-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1b85e-154">NOTES</span></span>

## <span data-ttu-id="1b85e-155">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1b85e-155">RELATED LINKS</span></span>

[<span data-ttu-id="1b85e-156">Find-Module</span><span class="sxs-lookup"><span data-stu-id="1b85e-156">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="1b85e-157">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="1b85e-157">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="1b85e-158">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="1b85e-158">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="1b85e-159">Save-Module</span><span class="sxs-lookup"><span data-stu-id="1b85e-159">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="1b85e-160">Update-Module</span><span class="sxs-lookup"><span data-stu-id="1b85e-160">Update-Module</span></span>](Update-Module.md)

