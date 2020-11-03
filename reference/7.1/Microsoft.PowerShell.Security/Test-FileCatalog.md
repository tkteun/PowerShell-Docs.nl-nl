---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 7e2102963df66988d4d7bc2d67ac054d8b7414b8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250633"
---
# <span data-ttu-id="dfcce-103">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="dfcce-103">Test-FileCatalog</span></span>

## <span data-ttu-id="dfcce-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="dfcce-104">SYNOPSIS</span></span>
<span data-ttu-id="dfcce-105">`Test-FileCatalog` Hiermee wordt gecontroleerd of de hashes in een catalogus bestand (. cat) overeenkomen met de hashes van de daad werkelijke bestanden om de echtheid te valideren.</span><span class="sxs-lookup"><span data-stu-id="dfcce-105">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="dfcce-106">Deze cmdlet wordt alleen ondersteund in Windows.</span><span class="sxs-lookup"><span data-stu-id="dfcce-106">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="dfcce-107">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="dfcce-107">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dfcce-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="dfcce-108">DESCRIPTION</span></span>

<span data-ttu-id="dfcce-109">`Test-FileCatalog` valideert de echtheid van bestanden door de bestands-hashes van een catalogus bestand (. cat) te vergelijken met de hashes van de daad werkelijke bestanden op schijf.</span><span class="sxs-lookup"><span data-stu-id="dfcce-109">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span>
<span data-ttu-id="dfcce-110">Als er niet-overeenkomende items worden gedetecteerd, wordt de status als ValidationFailed geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dfcce-110">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="dfcce-111">Gebruikers kunnen al deze gegevens ophalen met behulp van de-gedetailleerde para meter.</span><span class="sxs-lookup"><span data-stu-id="dfcce-111">Users can retrieve all this information by using the -Detailed parameter.</span></span>
<span data-ttu-id="dfcce-112">Ook wordt de handtekening status van de catalogus in de handtekening eigenschap weer gegeven, wat gelijk is aan de aanroep- `Get-AuthenticodeSignature` cmdlet op het catalogus bestand.</span><span class="sxs-lookup"><span data-stu-id="dfcce-112">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span>
<span data-ttu-id="dfcce-113">Gebruikers kunnen ook bestanden overs Laan tijdens de validatie met behulp van de para meter-FilesToSkip.</span><span class="sxs-lookup"><span data-stu-id="dfcce-113">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="dfcce-114">Deze cmdlet wordt alleen ondersteund in Windows.</span><span class="sxs-lookup"><span data-stu-id="dfcce-114">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="dfcce-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="dfcce-115">EXAMPLES</span></span>

### <span data-ttu-id="dfcce-116">Voor beeld 1: een bestands catalogus maken en valideren</span><span class="sxs-lookup"><span data-stu-id="dfcce-116">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="dfcce-117">Voor beeld 2: een bestands catalogus valideren met gedetailleerde uitvoer</span><span class="sxs-lookup"><span data-stu-id="dfcce-117">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## <span data-ttu-id="dfcce-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dfcce-118">PARAMETERS</span></span>

### <span data-ttu-id="dfcce-119">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="dfcce-119">-CatalogFilePath</span></span>

<span data-ttu-id="dfcce-120">Een pad naar een catalogus bestand (. cat) dat de hashes bevat die voor validatie moeten worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dfcce-120">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dfcce-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dfcce-121">-Confirm</span></span>

<span data-ttu-id="dfcce-122">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="dfcce-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dfcce-123">-Gedetailleerd</span><span class="sxs-lookup"><span data-stu-id="dfcce-123">-Detailed</span></span>

<span data-ttu-id="dfcce-124">Retourneert meer informatie over een meer gedetailleerd `CatalogInformation` object dat de geteste bestanden bevat, de verwachte/werkelijke hashes en een Authenticode-hand tekening van het catalogus bestand als het is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="dfcce-124">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="dfcce-125">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="dfcce-125">-FilesToSkip</span></span>

<span data-ttu-id="dfcce-126">Een matrix met paden die niet moeten worden getest als onderdeel van de validatie.</span><span class="sxs-lookup"><span data-stu-id="dfcce-126">An array of paths that should not be tested as part of the validation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dfcce-127">-Path</span><span class="sxs-lookup"><span data-stu-id="dfcce-127">-Path</span></span>

<span data-ttu-id="dfcce-128">Een map of een reeks bestanden die moet worden gevalideerd op basis van het catalogus bestand.</span><span class="sxs-lookup"><span data-stu-id="dfcce-128">A folder or array of files that should be validated against the catalog file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dfcce-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dfcce-129">-WhatIf</span></span>

<span data-ttu-id="dfcce-130">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="dfcce-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dfcce-131">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="dfcce-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dfcce-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dfcce-132">CommonParameters</span></span>

<span data-ttu-id="dfcce-133">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="dfcce-133">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="dfcce-134">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dfcce-134">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dfcce-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="dfcce-135">INPUTS</span></span>

### <span data-ttu-id="dfcce-136">System. IO. DirectoryInfo [], System. string []</span><span class="sxs-lookup"><span data-stu-id="dfcce-136">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="dfcce-137">De pijp lijn accepteert een matrix met teken reeksen of `DirectoryInfo` objecten die paden vertegenwoordigen naar de bestanden die moeten worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="dfcce-137">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="dfcce-138">UITVOER</span><span class="sxs-lookup"><span data-stu-id="dfcce-138">OUTPUTS</span></span>

### <span data-ttu-id="dfcce-139">System. Management. Automation. CatalogValidationStatus</span><span class="sxs-lookup"><span data-stu-id="dfcce-139">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="dfcce-140">Het standaard retour type met een waarde van ofwel `Valid` of `ValidationFailed` .</span><span class="sxs-lookup"><span data-stu-id="dfcce-140">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="dfcce-141">System. Management. Automation. CatalogInformation</span><span class="sxs-lookup"><span data-stu-id="dfcce-141">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="dfcce-142">Een meer gedetailleerd object dat wordt gebruikt `-Detailed` voor het analyseren van specifieke bestanden die mogelijk wel of niet zijn gevalideerd, welke hashes werden verwacht versus gevonden en de algoritme die in de catalogus wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dfcce-142">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="dfcce-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="dfcce-143">NOTES</span></span>

## <span data-ttu-id="dfcce-144">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="dfcce-144">RELATED LINKS</span></span>

[<span data-ttu-id="dfcce-145">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="dfcce-145">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="dfcce-146">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="dfcce-146">PowerShellGet</span></span>](/powershell/module/PowerShellGet)

