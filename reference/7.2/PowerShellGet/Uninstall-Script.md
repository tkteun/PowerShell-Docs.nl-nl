---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 2cd8b51e1d4ef11a0a5f9e3542ff89e094854d8c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705909"
---
# <span data-ttu-id="0ab55-102">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="0ab55-102">Uninstall-Script</span></span>

## <span data-ttu-id="0ab55-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0ab55-103">SYNOPSIS</span></span>
<span data-ttu-id="0ab55-104">Hiermee verwijdert u een script.</span><span class="sxs-lookup"><span data-stu-id="0ab55-104">Uninstalls a script.</span></span>

## <span data-ttu-id="0ab55-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0ab55-105">SYNTAX</span></span>

### <span data-ttu-id="0ab55-106">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="0ab55-106">NameParameterSet (Default)</span></span>

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0ab55-107">Input object</span><span class="sxs-lookup"><span data-stu-id="0ab55-107">InputObject</span></span>

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0ab55-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0ab55-108">DESCRIPTION</span></span>

<span data-ttu-id="0ab55-109">`Uninstall-Script`Met de cmdlet wordt een opgegeven script verwijderd van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0ab55-109">The `Uninstall-Script` cmdlet uninstalls a specified script from the local computer.</span></span>

## <span data-ttu-id="0ab55-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0ab55-110">EXAMPLES</span></span>

### <span data-ttu-id="0ab55-111">Voor beeld 1: een script verwijderen</span><span class="sxs-lookup"><span data-stu-id="0ab55-111">Example 1: Uninstall a script</span></span>

<span data-ttu-id="0ab55-112">In dit voor beeld wordt een script verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-112">This example uninstalls a script.</span></span>

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

<span data-ttu-id="0ab55-113">`Uninstall-Script` maakt gebruik van de para meter **name** om het script op te geven dat van de lokale computer moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-113">`Uninstall-Script` uses the **Name** parameter to specify the script to uninstall from the local computer.</span></span>

### <span data-ttu-id="0ab55-114">Voor beeld 2: de pijp lijn gebruiken om een script te verwijderen</span><span class="sxs-lookup"><span data-stu-id="0ab55-114">Example 2: Use the pipeline to uninstall a script</span></span>

<span data-ttu-id="0ab55-115">In dit voor beeld wordt de pijp lijn gebruikt voor het verwijderen van een script.</span><span class="sxs-lookup"><span data-stu-id="0ab55-115">In this example, the pipeline is used to uninstall a script.</span></span>

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

<span data-ttu-id="0ab55-116">`Get-InstalledScript` maakt gebruik van de para meter **name** om het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="0ab55-116">`Get-InstalledScript` uses the **Name** parameter to specify the script.</span></span> <span data-ttu-id="0ab55-117">Het object wordt naar de pijp lijn verzonden `Uninstall-Script` en het script wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-117">The object is sent down the pipeline to `Uninstall-Script` and the script is uninstalled.</span></span>

## <span data-ttu-id="0ab55-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ab55-118">PARAMETERS</span></span>

### <span data-ttu-id="0ab55-119">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0ab55-119">-AllowPrerelease</span></span>

<span data-ttu-id="0ab55-120">Hiermee kunt u een script dat is gemarkeerd als Prerelease, verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0ab55-120">Allows you to uninstall a script marked as a prerelease.</span></span>

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

### <span data-ttu-id="0ab55-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0ab55-121">-Confirm</span></span>

<span data-ttu-id="0ab55-122">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Uninstall-Script` .</span><span class="sxs-lookup"><span data-stu-id="0ab55-122">Prompts you for confirmation before running `Uninstall-Script`.</span></span>

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

### <span data-ttu-id="0ab55-123">-Force</span><span class="sxs-lookup"><span data-stu-id="0ab55-123">-Force</span></span>

<span data-ttu-id="0ab55-124">Er wordt geforceerd `Uninstall-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-124">Forces `Uninstall-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0ab55-125">-Input object</span><span class="sxs-lookup"><span data-stu-id="0ab55-125">-InputObject</span></span>

<span data-ttu-id="0ab55-126">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-126">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="0ab55-127">Bijvoorbeeld: uitvoer `Get-InstalledScript` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="0ab55-127">For example, output `Get-InstalledScript` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="0ab55-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0ab55-128">-MaximumVersion</span></span>

<span data-ttu-id="0ab55-129">Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-129">Specifies the maximum, or newest, version of the script to uninstall.</span></span> <span data-ttu-id="0ab55-130">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="0ab55-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0ab55-131">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0ab55-131">-MinimumVersion</span></span>

<span data-ttu-id="0ab55-132">Hiermee geeft u de minimum versie van het script dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-132">Specifies the minimum version of the script to uninstall.</span></span> <span data-ttu-id="0ab55-133">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="0ab55-133">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="0ab55-134">-Name</span><span class="sxs-lookup"><span data-stu-id="0ab55-134">-Name</span></span>

<span data-ttu-id="0ab55-135">Hiermee geeft u een matrix met script namen op die moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-135">Specifies an array of script names to uninstall.</span></span>

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

### <span data-ttu-id="0ab55-136">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0ab55-136">-RequiredVersion</span></span>

<span data-ttu-id="0ab55-137">Hiermee geeft u het exacte versie nummer van het script dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-137">Specifies the exact version number of the script to uninstall.</span></span>

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

### <span data-ttu-id="0ab55-138">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0ab55-138">-WhatIf</span></span>

<span data-ttu-id="0ab55-139">Hier wordt weer gegeven wat er gebeurt als er `Uninstall-Script` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-139">Shows what would happen if `Uninstall-Script` runs.</span></span> <span data-ttu-id="0ab55-140">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0ab55-140">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0ab55-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ab55-141">CommonParameters</span></span>

<span data-ttu-id="0ab55-142">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0ab55-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ab55-143">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0ab55-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0ab55-144">INVOER</span><span class="sxs-lookup"><span data-stu-id="0ab55-144">INPUTS</span></span>

### <span data-ttu-id="0ab55-145">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0ab55-145">System.String[]</span></span>

### <span data-ttu-id="0ab55-146">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="0ab55-146">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="0ab55-147">System. String</span><span class="sxs-lookup"><span data-stu-id="0ab55-147">System.String</span></span>

## <span data-ttu-id="0ab55-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0ab55-148">OUTPUTS</span></span>

### <span data-ttu-id="0ab55-149">System. object</span><span class="sxs-lookup"><span data-stu-id="0ab55-149">System.Object</span></span>

## <span data-ttu-id="0ab55-150">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0ab55-150">NOTES</span></span>

## <span data-ttu-id="0ab55-151">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0ab55-151">RELATED LINKS</span></span>

[<span data-ttu-id="0ab55-152">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="0ab55-152">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="0ab55-153">Install-script</span><span class="sxs-lookup"><span data-stu-id="0ab55-153">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="0ab55-154">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="0ab55-154">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="0ab55-155">Save-Script</span><span class="sxs-lookup"><span data-stu-id="0ab55-155">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="0ab55-156">Update-script</span><span class="sxs-lookup"><span data-stu-id="0ab55-156">Update-Script</span></span>](Update-Script.md)

