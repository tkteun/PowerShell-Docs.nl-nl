---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 6085585a50f8d3ac8adb34d4d9e3e376a1bc17cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251270"
---
# <span data-ttu-id="e85ff-103">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="e85ff-103">New-DscChecksum</span></span>

## <span data-ttu-id="e85ff-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e85ff-104">SYNOPSIS</span></span>
<span data-ttu-id="e85ff-105">Hiermee maakt u controlesom bestanden voor DSC-documenten en DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="e85ff-105">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="e85ff-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e85ff-106">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e85ff-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e85ff-107">DESCRIPTION</span></span>

<span data-ttu-id="e85ff-108">De cmdlet **New-DSCCheckSum** genereert controlesom bestanden voor de Power shell-documenten voor desired state Configuration (DSC) en gecomprimeerde DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="e85ff-108">The **New-DSCCheckSum** cmdlet generates checksum files for PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="e85ff-109">Met deze cmdlet wordt een controlesom bestand gegenereerd voor elke configuratie en resource die in de pull-modus moeten worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e85ff-109">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="e85ff-110">De DSC-service gebruikt de controle sommen om ervoor te zorgen dat de juiste configuratie en resources bestaan op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="e85ff-110">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="e85ff-111">Plaats de controle sommen samen met de bijbehorende DSC-documenten en gecomprimeerde DSC-resources in de DSC-service opslag.</span><span class="sxs-lookup"><span data-stu-id="e85ff-111">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="e85ff-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e85ff-112">EXAMPLES</span></span>

### <span data-ttu-id="e85ff-113">Voor beeld 1: controlesom bestanden maken voor alle configuraties in een specifiek pad</span><span class="sxs-lookup"><span data-stu-id="e85ff-113">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="e85ff-114">Met deze opdracht worden controlesom bestanden gemaakt voor alle configuraties in het pad C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="e85ff-114">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="e85ff-115">Eventuele controlesom bestanden die al bestaan, worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e85ff-115">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="e85ff-116">Voor beeld 2: controlesom bestanden maken voor alle configuraties in een specifiek pad en de bestaande controlesom bestanden overschrijven</span><span class="sxs-lookup"><span data-stu-id="e85ff-116">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="e85ff-117">Met deze opdracht worden nieuwe controlesom bestanden gemaakt voor alle configuraties in het pad C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="e85ff-117">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="e85ff-118">Het opgeven van de para meter *Force* zorgt ervoor dat de opdracht eventuele controlesom bestanden overschrijft die al bestaan.</span><span class="sxs-lookup"><span data-stu-id="e85ff-118">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="e85ff-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e85ff-119">PARAMETERS</span></span>

### <span data-ttu-id="e85ff-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e85ff-120">-Confirm</span></span>

<span data-ttu-id="e85ff-121">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e85ff-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e85ff-122">-Force</span><span class="sxs-lookup"><span data-stu-id="e85ff-122">-Force</span></span>

<span data-ttu-id="e85ff-123">Geeft aan dat de cmdlet het opgegeven uitvoer bestand overschrijft als dit al bestaat.</span><span class="sxs-lookup"><span data-stu-id="e85ff-123">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="e85ff-124">-Outpath</span><span class="sxs-lookup"><span data-stu-id="e85ff-124">-OutPath</span></span>

<span data-ttu-id="e85ff-125">Hiermee geeft u het pad en de bestands naam van het bestand met de uitvoer controlesom op.</span><span class="sxs-lookup"><span data-stu-id="e85ff-125">Specifies the path and file name of the output checksum file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e85ff-126">-Path</span><span class="sxs-lookup"><span data-stu-id="e85ff-126">-Path</span></span>

<span data-ttu-id="e85ff-127">Hiermee geeft u het pad van het invoer bestand.</span><span class="sxs-lookup"><span data-stu-id="e85ff-127">Specifies the path of the input file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e85ff-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e85ff-128">-WhatIf</span></span>

<span data-ttu-id="e85ff-129">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e85ff-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e85ff-130">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e85ff-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e85ff-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e85ff-131">CommonParameters</span></span>

<span data-ttu-id="e85ff-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e85ff-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e85ff-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e85ff-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e85ff-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="e85ff-134">INPUTS</span></span>

### <span data-ttu-id="e85ff-135">Geen</span><span class="sxs-lookup"><span data-stu-id="e85ff-135">None</span></span>

## <span data-ttu-id="e85ff-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e85ff-136">OUTPUTS</span></span>

### <span data-ttu-id="e85ff-137">System. object</span><span class="sxs-lookup"><span data-stu-id="e85ff-137">System.Object</span></span>

## <span data-ttu-id="e85ff-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e85ff-138">NOTES</span></span>

## <span data-ttu-id="e85ff-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e85ff-139">RELATED LINKS</span></span>

[<span data-ttu-id="e85ff-140">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="e85ff-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

