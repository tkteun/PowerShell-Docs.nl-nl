---
external help file: PSDesiredStateConfiguration-help.xml
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 8b8d0c545cdb36b6184a0670a52a5a30aa33a465
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705680"
---
# <span data-ttu-id="8c9d9-102">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="8c9d9-102">New-DscChecksum</span></span>

## <span data-ttu-id="8c9d9-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8c9d9-103">SYNOPSIS</span></span>
<span data-ttu-id="8c9d9-104">Hiermee maakt u controlesom bestanden voor DSC-documenten en DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-104">Creates checksum files for DSC documents and DSC resources.</span></span>

## <span data-ttu-id="8c9d9-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8c9d9-105">SYNTAX</span></span>

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8c9d9-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8c9d9-106">DESCRIPTION</span></span>

<span data-ttu-id="8c9d9-107">De cmdlet **New-DSCCheckSum** genereert controlesom bestanden voor de Power shell-documenten voor desired state Configuration (DSC) en gecomprimeerde DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-107">The **New-DSCCheckSum** cmdlet generates checksum files for PowerShell Desired State Configuration (DSC) documents and compressed DSC resources.</span></span>
<span data-ttu-id="8c9d9-108">Met deze cmdlet wordt een controlesom bestand gegenereerd voor elke configuratie en resource die in de pull-modus moeten worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-108">This cmdlet generates a checksum file for each configuration and resource to be used in pull mode.</span></span>
<span data-ttu-id="8c9d9-109">De DSC-service gebruikt de controle sommen om ervoor te zorgen dat de juiste configuratie en resources bestaan op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-109">The DSC service uses the checksums to make sure that the correct configuration and resources exist on the target node.</span></span>
<span data-ttu-id="8c9d9-110">Plaats de controle sommen samen met de bijbehorende DSC-documenten en gecomprimeerde DSC-resources in de DSC-service opslag.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-110">Place the checksums together with the associated DSC documents and compressed DSC resources in the DSC service store.</span></span>

## <span data-ttu-id="8c9d9-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8c9d9-111">EXAMPLES</span></span>

### <span data-ttu-id="8c9d9-112">Voor beeld 1: controlesom bestanden maken voor alle configuraties in een specifiek pad</span><span class="sxs-lookup"><span data-stu-id="8c9d9-112">Example 1: Create checksum files for all configurations in a specific path</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="8c9d9-113">Met deze opdracht worden controlesom bestanden gemaakt voor alle configuraties in het pad C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-113">This command creates checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="8c9d9-114">Eventuele controlesom bestanden die al bestaan, worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-114">Any checksum files that already exist are skipped.</span></span>

### <span data-ttu-id="8c9d9-115">Voor beeld 2: controlesom bestanden maken voor alle configuraties in een specifiek pad en de bestaande controlesom bestanden overschrijven</span><span class="sxs-lookup"><span data-stu-id="8c9d9-115">Example 2: Create checksum files for all configurations in a specific path and overwrite the existing checksum files</span></span>

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

<span data-ttu-id="8c9d9-116">Met deze opdracht worden nieuwe controlesom bestanden gemaakt voor alle configuraties in het pad C:\DSC\Configurations.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-116">This command creates new checksum files for all configurations in the path C:\DSC\Configurations.</span></span>
<span data-ttu-id="8c9d9-117">Het opgeven van de para meter *Force* zorgt ervoor dat de opdracht eventuele controlesom bestanden overschrijft die al bestaan.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-117">Specifying the *Force* parameter causes the command to overwrite any checksum files that already exist.</span></span>

## <span data-ttu-id="8c9d9-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c9d9-118">PARAMETERS</span></span>

### <span data-ttu-id="8c9d9-119">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8c9d9-119">-Confirm</span></span>

<span data-ttu-id="8c9d9-120">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-120">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8c9d9-121">-Force</span><span class="sxs-lookup"><span data-stu-id="8c9d9-121">-Force</span></span>

<span data-ttu-id="8c9d9-122">Geeft aan dat de cmdlet het opgegeven uitvoer bestand overschrijft als dit al bestaat.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-122">Indicates that the cmdlet overwrites the specified output file if it already exists.</span></span>

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

### <span data-ttu-id="8c9d9-123">-Outpath</span><span class="sxs-lookup"><span data-stu-id="8c9d9-123">-OutPath</span></span>

<span data-ttu-id="8c9d9-124">Hiermee geeft u het pad en de bestands naam van het bestand met de uitvoer controlesom op.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-124">Specifies the path and file name of the output checksum file.</span></span>

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

### <span data-ttu-id="8c9d9-125">-Path</span><span class="sxs-lookup"><span data-stu-id="8c9d9-125">-Path</span></span>

<span data-ttu-id="8c9d9-126">Hiermee geeft u het pad van het invoer bestand.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-126">Specifies the path of the input file.</span></span>

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

### <span data-ttu-id="8c9d9-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8c9d9-127">-WhatIf</span></span>

<span data-ttu-id="8c9d9-128">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8c9d9-129">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8c9d9-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c9d9-130">CommonParameters</span></span>

<span data-ttu-id="8c9d9-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c9d9-132">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c9d9-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c9d9-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="8c9d9-133">INPUTS</span></span>

### <span data-ttu-id="8c9d9-134">Geen</span><span class="sxs-lookup"><span data-stu-id="8c9d9-134">None</span></span>

## <span data-ttu-id="8c9d9-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8c9d9-135">OUTPUTS</span></span>

### <span data-ttu-id="8c9d9-136">System. object</span><span class="sxs-lookup"><span data-stu-id="8c9d9-136">System.Object</span></span>

## <span data-ttu-id="8c9d9-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8c9d9-137">NOTES</span></span>

## <span data-ttu-id="8c9d9-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8c9d9-138">RELATED LINKS</span></span>

[<span data-ttu-id="8c9d9-139">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="8c9d9-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

