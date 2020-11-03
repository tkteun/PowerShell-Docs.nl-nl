---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 26e32cc3d7330026bd77d33ba6574818559d1c6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250105"
---
# <span data-ttu-id="2d5b9-103">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="2d5b9-103">Uninstall-Script</span></span>

## <span data-ttu-id="2d5b9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2d5b9-104">SYNOPSIS</span></span>
<span data-ttu-id="2d5b9-105">Hiermee verwijdert u een script.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-105">Uninstalls a script.</span></span>

## <span data-ttu-id="2d5b9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2d5b9-106">SYNTAX</span></span>

### <span data-ttu-id="2d5b9-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="2d5b9-107">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2d5b9-108">Input object</span><span class="sxs-lookup"><span data-stu-id="2d5b9-108">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2d5b9-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2d5b9-109">DESCRIPTION</span></span>

<span data-ttu-id="2d5b9-110">`Uninstall-Script`Met de cmdlet wordt een opgegeven script verwijderd van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-110">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="2d5b9-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2d5b9-111">EXAMPLES</span></span>

### <span data-ttu-id="2d5b9-112">Voor beeld 1: een script verwijderen</span><span class="sxs-lookup"><span data-stu-id="2d5b9-112">Example 1: Uninstall a script</span></span>

<span data-ttu-id="2d5b9-113">In dit voor beeld wordt een script verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-113">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="2d5b9-114">`Uninstall-Script` maakt gebruik van de para meter **name** om het script op te geven dat van de lokale computer moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-114">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="2d5b9-115">Voor beeld 2: de pijp lijn gebruiken om een script te verwijderen</span><span class="sxs-lookup"><span data-stu-id="2d5b9-115">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="2d5b9-116">In dit voor beeld wordt de pijp lijn gebruikt voor het verwijderen van een script.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-116">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="2d5b9-117">`Get-InstalledScript` maakt gebruik van de para meter **name** om het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-117">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="2d5b9-118">Het object wordt naar de pijp lijn verzonden `Uninstall-Script` en het script wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-118">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="2d5b9-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d5b9-119">PARAMETERS</span></span>

### <span data-ttu-id="2d5b9-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="2d5b9-120">-AllowPrerelease</span></span>

<span data-ttu-id="2d5b9-121">Hiermee kunt u een script dat is gemarkeerd als Prerelease, verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-121">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="2d5b9-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2d5b9-122">-Confirm</span></span>

<span data-ttu-id="2d5b9-123">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="2d5b9-123">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="2d5b9-124">-Force</span><span class="sxs-lookup"><span data-stu-id="2d5b9-124">-Force</span></span>

<span data-ttu-id="2d5b9-125">Er wordt geforceerd `Uninstall-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-125">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2d5b9-126">-Input object</span><span class="sxs-lookup"><span data-stu-id="2d5b9-126">-InputObject</span></span>

<span data-ttu-id="2d5b9-127">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-127">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="2d5b9-128">Bijvoorbeeld: uitvoer `Get-InstalledScript` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="2d5b9-128">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="2d5b9-129">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2d5b9-129">-MaximumVersion</span></span>

<span data-ttu-id="2d5b9-130">Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-130">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="2d5b9-131">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-131">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="2d5b9-132">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2d5b9-132">-MinimumVersion</span></span>

<span data-ttu-id="2d5b9-133">Hiermee geeft u de minimum versie van het script dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-133">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="2d5b9-134">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-134">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="2d5b9-135">-Name</span><span class="sxs-lookup"><span data-stu-id="2d5b9-135">-Name</span></span>

<span data-ttu-id="2d5b9-136">Hiermee geeft u een matrix met script namen op die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-136">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="2d5b9-137">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2d5b9-137">-RequiredVersion</span></span>

<span data-ttu-id="2d5b9-138">Hiermee geeft u het exacte versie nummer van het script dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-138">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="2d5b9-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2d5b9-139">-WhatIf</span></span>

<span data-ttu-id="2d5b9-140">Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Script` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-140">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="2d5b9-141">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-141">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2d5b9-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d5b9-142">CommonParameters</span></span>

<span data-ttu-id="2d5b9-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d5b9-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2d5b9-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d5b9-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="2d5b9-145">INPUTS</span></span>

### <span data-ttu-id="2d5b9-146">System.String[]</span><span class="sxs-lookup"><span data-stu-id="2d5b9-146">System.String[]</span></span>

### <span data-ttu-id="2d5b9-147">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="2d5b9-147">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="2d5b9-148">System. String</span><span class="sxs-lookup"><span data-stu-id="2d5b9-148">System.String</span></span>

## <span data-ttu-id="2d5b9-149">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2d5b9-149">OUTPUTS</span></span>

### <span data-ttu-id="2d5b9-150">System. object</span><span class="sxs-lookup"><span data-stu-id="2d5b9-150">System.Object</span></span>

## <span data-ttu-id="2d5b9-151">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2d5b9-151">NOTES</span></span>

## <span data-ttu-id="2d5b9-152">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2d5b9-152">RELATED LINKS</span></span>

[<span data-ttu-id="2d5b9-153">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="2d5b9-153">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="2d5b9-154">Install-script</span><span class="sxs-lookup"><span data-stu-id="2d5b9-154">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="2d5b9-155">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="2d5b9-155">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="2d5b9-156">Save-Script</span><span class="sxs-lookup"><span data-stu-id="2d5b9-156">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="2d5b9-157">Update-script</span><span class="sxs-lookup"><span data-stu-id="2d5b9-157">Update-Script</span></span>](Update-Script.md)

