---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 72cdbd26a909e4be33fa32f67019e4c1f02ce3de
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250735"
---
# <span data-ttu-id="3242b-103">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="3242b-103">Uninstall-Module</span></span>

## <span data-ttu-id="3242b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3242b-104">SYNOPSIS</span></span>
<span data-ttu-id="3242b-105">Hiermee verwijdert u een module.</span><span class="sxs-lookup"><span data-stu-id="3242b-105">Uninstalls a module.</span></span>

## <span data-ttu-id="3242b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3242b-106">SYNTAX</span></span>

### <span data-ttu-id="3242b-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="3242b-107">NameParameterSet (Default)</span></span>

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3242b-108">Input object</span><span class="sxs-lookup"><span data-stu-id="3242b-108">InputObject</span></span>

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3242b-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3242b-109">DESCRIPTION</span></span>

<span data-ttu-id="3242b-110">`Uninstall-Module`Met de cmdlet wordt een opgegeven module verwijderd van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3242b-110">The `Uninstall-Module` cmdlet uninstalls a specified module from the local computer.</span></span> <span data-ttu-id="3242b-111">U kunt een module niet verwijderen als deze andere modules als afhankelijkheden heeft.</span><span class="sxs-lookup"><span data-stu-id="3242b-111">You can't uninstall a module if it has other modules as dependencies.</span></span>

## <span data-ttu-id="3242b-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3242b-112">EXAMPLES</span></span>

### <span data-ttu-id="3242b-113">Voor beeld 1: een module verwijderen</span><span class="sxs-lookup"><span data-stu-id="3242b-113">Example 1: Uninstall a module</span></span>

<span data-ttu-id="3242b-114">In dit voor beeld wordt een module verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3242b-114">This example uninstalls a module.</span></span>

```powershell
Uninstall-Module -Name SpeculationControl
```

<span data-ttu-id="3242b-115">`Uninstall-Module` maakt gebruik van de para meter **name** om de module op te geven die u wilt verwijderen van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3242b-115">`Uninstall-Module` uses the **Name** parameter to specify the module to uninstall from the local computer.</span></span>

### <span data-ttu-id="3242b-116">Voor beeld 2: de pijp lijn gebruiken om een module te verwijderen</span><span class="sxs-lookup"><span data-stu-id="3242b-116">Example 2: Use the pipeline to uninstall a module</span></span>

<span data-ttu-id="3242b-117">In dit voor beeld wordt de pijp lijn gebruikt om een module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3242b-117">In this example, the pipeline is used to uninstall a module.</span></span>

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

<span data-ttu-id="3242b-118">`Get-InstalledModule` maakt gebruik van de para meter **name** om de module op te geven.</span><span class="sxs-lookup"><span data-stu-id="3242b-118">`Get-InstalledModule` uses the **Name** parameter to specify the module.</span></span> <span data-ttu-id="3242b-119">Het object wordt naar de pijp lijn verzonden `Uninstall-Module` en wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3242b-119">The object is sent down the pipeline to `Uninstall-Module` and is uninstalled.</span></span>

## <span data-ttu-id="3242b-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3242b-120">PARAMETERS</span></span>

### <span data-ttu-id="3242b-121">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="3242b-121">-AllowPrerelease</span></span>

<span data-ttu-id="3242b-122">Hiermee kunt u een module verwijderen die is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="3242b-122">Allows you to uninstall a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="3242b-123">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="3242b-123">-AllVersions</span></span>

<span data-ttu-id="3242b-124">Hiermee geeft u aan dat u alle beschik bare versies van een module wilt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3242b-124">Specifies that you want to include all available versions of a module.</span></span> <span data-ttu-id="3242b-125">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="3242b-125">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="3242b-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3242b-126">-Confirm</span></span>

<span data-ttu-id="3242b-127">Vraagt u om bevestiging voordat de wordt uitgevoerd `Uninstall-Module` .</span><span class="sxs-lookup"><span data-stu-id="3242b-127">Prompts you for confirmation before running the `Uninstall-Module`.</span></span>

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

### <span data-ttu-id="3242b-128">-Force</span><span class="sxs-lookup"><span data-stu-id="3242b-128">-Force</span></span>

<span data-ttu-id="3242b-129">Er wordt geforceerd `Uninstall-Module` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="3242b-129">Forces `Uninstall-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="3242b-130">-Input object</span><span class="sxs-lookup"><span data-stu-id="3242b-130">-InputObject</span></span>

<span data-ttu-id="3242b-131">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3242b-131">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="3242b-132">Bijvoorbeeld: uitvoer `Get-InstalledModule` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="3242b-132">For example, output `Get-InstalledModule` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="3242b-133">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3242b-133">-MaximumVersion</span></span>

<span data-ttu-id="3242b-134">Hiermee geeft u het maximum of nieuwste versie van de module moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3242b-134">Specifies the maximum, or newest, version of the module to uninstall.</span></span> <span data-ttu-id="3242b-135">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="3242b-135">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="3242b-136">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3242b-136">-MinimumVersion</span></span>

<span data-ttu-id="3242b-137">Hiermee geeft u de minimum versie op van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3242b-137">Specifies the minimum version of the module to uninstall.</span></span> <span data-ttu-id="3242b-138">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="3242b-138">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="3242b-139">-Name</span><span class="sxs-lookup"><span data-stu-id="3242b-139">-Name</span></span>

<span data-ttu-id="3242b-140">Hiermee geeft u een matrix van module namen op die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3242b-140">Specifies an array of module names to uninstall.</span></span>

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

### <span data-ttu-id="3242b-141">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3242b-141">-RequiredVersion</span></span>

<span data-ttu-id="3242b-142">Hiermee geeft u het exacte versie nummer van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3242b-142">Specifies the exact version number of the module to uninstall.</span></span>

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

### <span data-ttu-id="3242b-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3242b-143">-WhatIf</span></span>

<span data-ttu-id="3242b-144">Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Module` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3242b-144">Shows what would happen if `Uninstall-Module` runs.</span></span> <span data-ttu-id="3242b-145">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3242b-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="3242b-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3242b-146">CommonParameters</span></span>

<span data-ttu-id="3242b-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3242b-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3242b-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3242b-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3242b-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="3242b-149">INPUTS</span></span>

### <span data-ttu-id="3242b-150">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="3242b-150">PSRepositoryItemInfo</span></span>

<span data-ttu-id="3242b-151">`Uninstall-Module` Hiermee worden **PSRepositoryItemInfo** -objecten geaccepteerd vanuit de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="3242b-151">`Uninstall-Module` accepts **PSRepositoryItemInfo** objects from the pipeline.</span></span>

## <span data-ttu-id="3242b-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3242b-152">OUTPUTS</span></span>

## <span data-ttu-id="3242b-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3242b-153">NOTES</span></span>

## <span data-ttu-id="3242b-154">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3242b-154">RELATED LINKS</span></span>

[<span data-ttu-id="3242b-155">Find-Module</span><span class="sxs-lookup"><span data-stu-id="3242b-155">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="3242b-156">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="3242b-156">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="3242b-157">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="3242b-157">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="3242b-158">Save-Module</span><span class="sxs-lookup"><span data-stu-id="3242b-158">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="3242b-159">Update-Module</span><span class="sxs-lookup"><span data-stu-id="3242b-159">Update-Module</span></span>](Update-Module.md)
