---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: e285391bdfd68211883827babbc7075e4727f06d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250734"
---
# <span data-ttu-id="9e29d-103">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="9e29d-103">Uninstall-Script</span></span>

## <span data-ttu-id="9e29d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9e29d-104">SYNOPSIS</span></span>
<span data-ttu-id="9e29d-105">Hiermee verwijdert u een script.</span><span class="sxs-lookup"><span data-stu-id="9e29d-105">Uninstalls a script.</span></span>

## <span data-ttu-id="9e29d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9e29d-106">SYNTAX</span></span>

### <span data-ttu-id="9e29d-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="9e29d-107">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9e29d-108">Input object</span><span class="sxs-lookup"><span data-stu-id="9e29d-108">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9e29d-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9e29d-109">DESCRIPTION</span></span>

<span data-ttu-id="9e29d-110">`Uninstall-Script`Met de cmdlet wordt een opgegeven script verwijderd van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e29d-110">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="9e29d-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9e29d-111">EXAMPLES</span></span>

### <span data-ttu-id="9e29d-112">Voor beeld 1: een script verwijderen</span><span class="sxs-lookup"><span data-stu-id="9e29d-112">Example 1: Uninstall a script</span></span>

<span data-ttu-id="9e29d-113">In dit voor beeld wordt een script verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-113">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="9e29d-114">`Uninstall-Script` maakt gebruik van de para meter **name** om het script op te geven dat van de lokale computer moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-114">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="9e29d-115">Voor beeld 2: de pijp lijn gebruiken om een script te verwijderen</span><span class="sxs-lookup"><span data-stu-id="9e29d-115">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="9e29d-116">In dit voor beeld wordt de pijp lijn gebruikt voor het verwijderen van een script.</span><span class="sxs-lookup"><span data-stu-id="9e29d-116">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="9e29d-117">`Get-InstalledScript` maakt gebruik van de para meter **name** om het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="9e29d-117">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="9e29d-118">Het object wordt naar de pijp lijn verzonden `Uninstall-Script` en het script wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-118">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="9e29d-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e29d-119">PARAMETERS</span></span>

### <span data-ttu-id="9e29d-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9e29d-120">-AllowPrerelease</span></span>

<span data-ttu-id="9e29d-121">Hiermee kunt u een script dat is gemarkeerd als Prerelease, verwijderen.</span><span class="sxs-lookup"><span data-stu-id="9e29d-121">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="9e29d-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9e29d-122">-Confirm</span></span>

<span data-ttu-id="9e29d-123">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="9e29d-123">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="9e29d-124">-Force</span><span class="sxs-lookup"><span data-stu-id="9e29d-124">-Force</span></span>

<span data-ttu-id="9e29d-125">Er wordt geforceerd `Uninstall-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-125">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9e29d-126">-Input object</span><span class="sxs-lookup"><span data-stu-id="9e29d-126">-InputObject</span></span>

<span data-ttu-id="9e29d-127">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-127">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="9e29d-128">Bijvoorbeeld: uitvoer `Get-InstalledScript` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="9e29d-128">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="9e29d-129">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9e29d-129">-MaximumVersion</span></span>

<span data-ttu-id="9e29d-130">Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-130">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="9e29d-131">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="9e29d-131">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="9e29d-132">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9e29d-132">-MinimumVersion</span></span>

<span data-ttu-id="9e29d-133">Hiermee geeft u de minimum versie van het script dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-133">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="9e29d-134">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="9e29d-134">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="9e29d-135">-Name</span><span class="sxs-lookup"><span data-stu-id="9e29d-135">-Name</span></span>

<span data-ttu-id="9e29d-136">Hiermee geeft u een matrix met script namen op die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-136">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="9e29d-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9e29d-137">-RequiredVersion</span></span>

<span data-ttu-id="9e29d-138">Hiermee geeft u het exacte versie nummer van het script dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-138">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="9e29d-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9e29d-139">-WhatIf</span></span>

<span data-ttu-id="9e29d-140">Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Script` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-140">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="9e29d-141">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e29d-141">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9e29d-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e29d-142">CommonParameters</span></span>

<span data-ttu-id="9e29d-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e29d-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e29d-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9e29d-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e29d-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="9e29d-145">INPUTS</span></span>

### <span data-ttu-id="9e29d-146">System.String[]</span><span class="sxs-lookup"><span data-stu-id="9e29d-146">System.String[]</span></span>

### <span data-ttu-id="9e29d-147">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="9e29d-147">System.Management.Automation.PSObject[]</span></span>

<span data-ttu-id="9e29d-148">`Uninstall-Script` Hiermee worden **PSRepositoryItemInfo** -objecten geaccepteerd vanuit de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="9e29d-148">`Uninstall-Script` accepts **PSRepositoryItemInfo** objects from the pipeline.</span></span>

### <span data-ttu-id="9e29d-149">System. String</span><span class="sxs-lookup"><span data-stu-id="9e29d-149">System.String</span></span>

## <span data-ttu-id="9e29d-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9e29d-150">OUTPUTS</span></span>

### <span data-ttu-id="9e29d-151">System. object</span><span class="sxs-lookup"><span data-stu-id="9e29d-151">System.Object</span></span>

## <span data-ttu-id="9e29d-152">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9e29d-152">NOTES</span></span>

## <span data-ttu-id="9e29d-153">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9e29d-153">RELATED LINKS</span></span>

[<span data-ttu-id="9e29d-154">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="9e29d-154">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="9e29d-155">Install-script</span><span class="sxs-lookup"><span data-stu-id="9e29d-155">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="9e29d-156">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="9e29d-156">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="9e29d-157">Save-Script</span><span class="sxs-lookup"><span data-stu-id="9e29d-157">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="9e29d-158">Update-script</span><span class="sxs-lookup"><span data-stu-id="9e29d-158">Update-Script</span></span>](Update-Script.md)
