---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 0a990b1c0c46cda06c5239a4c8fde55b29296376
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490875"
---
# <span data-ttu-id="1a6be-102">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="1a6be-102">Test-FileCatalog</span></span>

## <span data-ttu-id="1a6be-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1a6be-103">SYNOPSIS</span></span>
<span data-ttu-id="1a6be-104">`Test-FileCatalog` Hiermee wordt gecontroleerd of de hashes in een catalogus bestand (. cat) overeenkomen met de hashes van de daad werkelijke bestanden om de echtheid te valideren.</span><span class="sxs-lookup"><span data-stu-id="1a6be-104">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="1a6be-105">Deze cmdlet wordt alleen ondersteund in Windows.</span><span class="sxs-lookup"><span data-stu-id="1a6be-105">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="1a6be-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1a6be-106">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1a6be-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1a6be-107">DESCRIPTION</span></span>

<span data-ttu-id="1a6be-108">`Test-FileCatalog` valideert de echtheid van bestanden door de bestands-hashes van een catalogus bestand (. cat) te vergelijken met de hashes van de daad werkelijke bestanden op schijf.</span><span class="sxs-lookup"><span data-stu-id="1a6be-108">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="1a6be-109">Als er niet-overeenkomende items worden gedetecteerd, wordt de status als ValidationFailed geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1a6be-109">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="1a6be-110">Gebruikers kunnen al deze gegevens ophalen met behulp van de-gedetailleerde para meter.</span><span class="sxs-lookup"><span data-stu-id="1a6be-110">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="1a6be-111">Ook wordt de handtekening status van de catalogus in de handtekening eigenschap weer gegeven, wat gelijk is aan de aanroep- `Get-AuthenticodeSignature` cmdlet op het catalogus bestand.</span><span class="sxs-lookup"><span data-stu-id="1a6be-111">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="1a6be-112">Gebruikers kunnen ook bestanden overs Laan tijdens de validatie met behulp van de para meter-FilesToSkip.</span><span class="sxs-lookup"><span data-stu-id="1a6be-112">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="1a6be-113">Deze cmdlet wordt alleen ondersteund in Windows.</span><span class="sxs-lookup"><span data-stu-id="1a6be-113">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="1a6be-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1a6be-114">EXAMPLES</span></span>

### <span data-ttu-id="1a6be-115">Voor beeld 1: een bestands catalogus maken en valideren</span><span class="sxs-lookup"><span data-stu-id="1a6be-115">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="1a6be-116">Voor beeld 2: een bestands catalogus valideren met gedetailleerde uitvoer</span><span class="sxs-lookup"><span data-stu-id="1a6be-116">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -Detailed -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
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

## <span data-ttu-id="1a6be-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a6be-117">PARAMETERS</span></span>

### <span data-ttu-id="1a6be-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="1a6be-118">-CatalogFilePath</span></span>

<span data-ttu-id="1a6be-119">Een pad naar een catalogus bestand (. cat) dat de hashes bevat die voor validatie moeten worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1a6be-119">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

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

### <span data-ttu-id="1a6be-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1a6be-120">-Confirm</span></span>

<span data-ttu-id="1a6be-121">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1a6be-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1a6be-122">-Gedetailleerd</span><span class="sxs-lookup"><span data-stu-id="1a6be-122">-Detailed</span></span>

<span data-ttu-id="1a6be-123">Retourneert meer informatie over een meer gedetailleerd `CatalogInformation` object dat de geteste bestanden bevat, de verwachte/werkelijke hashes en een Authenticode-hand tekening van het catalogus bestand als het is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="1a6be-123">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="1a6be-124">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="1a6be-124">-FilesToSkip</span></span>

<span data-ttu-id="1a6be-125">Een matrix met paden die niet moeten worden getest als onderdeel van de validatie.</span><span class="sxs-lookup"><span data-stu-id="1a6be-125">An array of paths that should not be tested as part of the validation.</span></span>

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

### <span data-ttu-id="1a6be-126">-Path</span><span class="sxs-lookup"><span data-stu-id="1a6be-126">-Path</span></span>

<span data-ttu-id="1a6be-127">Een map of een reeks bestanden die moet worden gevalideerd op basis van het catalogus bestand.</span><span class="sxs-lookup"><span data-stu-id="1a6be-127">A folder or array of files that should be validated against the catalog file.</span></span>

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

### <span data-ttu-id="1a6be-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1a6be-128">-WhatIf</span></span>

<span data-ttu-id="1a6be-129">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1a6be-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1a6be-130">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1a6be-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1a6be-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a6be-131">CommonParameters</span></span>

<span data-ttu-id="1a6be-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a6be-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a6be-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1a6be-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a6be-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="1a6be-134">INPUTS</span></span>

### <span data-ttu-id="1a6be-135">System. IO. DirectoryInfo [], System. string []</span><span class="sxs-lookup"><span data-stu-id="1a6be-135">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="1a6be-136">De pijp lijn accepteert een matrix met teken reeksen of `DirectoryInfo` objecten die paden vertegenwoordigen naar de bestanden die moeten worden gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="1a6be-136">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="1a6be-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1a6be-137">OUTPUTS</span></span>

### <span data-ttu-id="1a6be-138">System. Management. Automation. CatalogValidationStatus</span><span class="sxs-lookup"><span data-stu-id="1a6be-138">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="1a6be-139">Het standaard retour type met een waarde van ofwel `Valid` of `ValidationFailed` .</span><span class="sxs-lookup"><span data-stu-id="1a6be-139">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="1a6be-140">System. Management. Automation. CatalogInformation</span><span class="sxs-lookup"><span data-stu-id="1a6be-140">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="1a6be-141">Een meer gedetailleerd object dat wordt gebruikt `-Detailed` voor het analyseren van specifieke bestanden die mogelijk wel of niet zijn gevalideerd, welke hashes werden verwacht versus gevonden en de algoritme die in de catalogus wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1a6be-141">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="1a6be-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1a6be-142">NOTES</span></span>

<span data-ttu-id="1a6be-143">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="1a6be-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="1a6be-144">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1a6be-144">RELATED LINKS</span></span>

[<span data-ttu-id="1a6be-145">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="1a6be-145">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="1a6be-146">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1a6be-146">PowerShellGet</span></span>](/powershell/module/PowerShellGet)
