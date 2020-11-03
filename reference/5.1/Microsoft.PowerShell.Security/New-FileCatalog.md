---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 139ebf10cd0097d55eac521cd81016f8f168d2bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250498"
---
# <span data-ttu-id="21d21-103">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="21d21-103">New-FileCatalog</span></span>

## <span data-ttu-id="21d21-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="21d21-104">SYNOPSIS</span></span>

<span data-ttu-id="21d21-105">`New-FileCatalog` Hiermee maakt u een catalogus bestand met bestands-hashes dat kan worden gebruikt om de authenticiteit van een bestand te valideren.</span><span class="sxs-lookup"><span data-stu-id="21d21-105">`New-FileCatalog` creates a catalog file of file hashes that can be used to validate the authenticity of a file.</span></span>

## <span data-ttu-id="21d21-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="21d21-106">SYNTAX</span></span>

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="21d21-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="21d21-107">DESCRIPTION</span></span>

<span data-ttu-id="21d21-108">`New-FileCatalog` Hiermee maakt u een [Windows-catalogus bestand](/windows-hardware/drivers/install/catalog-files) voor een set mappen en bestanden.</span><span class="sxs-lookup"><span data-stu-id="21d21-108">`New-FileCatalog` creates a [Windows catalog file](/windows-hardware/drivers/install/catalog-files) for a set of folders and files.</span></span>
<span data-ttu-id="21d21-109">Dit catalogus bestand bevat hashes voor alle bestanden in de gegeven paden.</span><span class="sxs-lookup"><span data-stu-id="21d21-109">This catalog file contains hashes for all files in the provided paths.</span></span>
<span data-ttu-id="21d21-110">Gebruikers kunnen de catalogus vervolgens distribueren met hun bestanden, zodat gebruikers kunnen valideren of er wijzigingen zijn aangebracht in de mappen sinds de aanmaak tijd van de catalogus.</span><span class="sxs-lookup"><span data-stu-id="21d21-110">Users can then distribute the catalog with their files so that users can validate whether any changes have been made to the folders since catalog creation time.</span></span>

<span data-ttu-id="21d21-111">Catalogus versies 1 en 2 worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="21d21-111">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="21d21-112">Versie 1 maakt gebruik van het (afgeschafte) SHA1 hash-algoritme om bestands-hashes te maken en versie 2 maakt gebruik van SHA256.</span><span class="sxs-lookup"><span data-stu-id="21d21-112">Version 1 uses the (deprecated) SHA1 hashing algorithm to create file hashes, and version 2 uses SHA256.</span></span>
<span data-ttu-id="21d21-113">Catalogus versie 2 wordt niet ondersteund in Windows Server 2008 R2 of Windows 7.</span><span class="sxs-lookup"><span data-stu-id="21d21-113">Catalog version 2 is not supported on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="21d21-114">U moet Catalog versie 2 gebruiken voor Windows 8, Windows Server 2012 en latere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="21d21-114">You should use catalog version 2 on Windows 8, Windows Server 2012, and later operating systems.</span></span>

## <span data-ttu-id="21d21-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="21d21-115">EXAMPLES</span></span>

### <span data-ttu-id="21d21-116">Voor beeld 1: een bestands catalogus maken voor `Microsoft.PowerShell.Utility`</span><span class="sxs-lookup"><span data-stu-id="21d21-116">Example 1: Create a file catalog for `Microsoft.PowerShell.Utility`</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## <span data-ttu-id="21d21-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21d21-117">PARAMETERS</span></span>

### <span data-ttu-id="21d21-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="21d21-118">-CatalogFilePath</span></span>

<span data-ttu-id="21d21-119">Een pad naar een bestand of map waar het catalogus bestand (. cat) moet worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="21d21-119">A path to a file or folder where the catalog file (.cat) should be placed.</span></span>
<span data-ttu-id="21d21-120">Als er een mappad is opgegeven, wordt de standaard bestandsnaam `catalog.cat` gebruikt.</span><span class="sxs-lookup"><span data-stu-id="21d21-120">If a folder path is specified, the default filename `catalog.cat` will be used.</span></span>

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

### <span data-ttu-id="21d21-121">-CatalogVersion</span><span class="sxs-lookup"><span data-stu-id="21d21-121">-CatalogVersion</span></span>

<span data-ttu-id="21d21-122">Accepteert `1.0` of `2.0` als mogelijke waarden voor het opgeven van de catalogus versie.</span><span class="sxs-lookup"><span data-stu-id="21d21-122">Accepts `1.0` or `2.0` as possible values for specifying the catalog version.</span></span>
<span data-ttu-id="21d21-123">`1.0` moet zoveel mogelijk worden gebruikt, aangezien het het onveilige SHA-1-hash-algoritme gebruikt, terwijl `2.0` het beveiligde SHA-256-algoritme wordt gebruikt `1.0` . Dit is echter het enige ondersteunde algoritme voor Windows 7 en Server 2008R2.</span><span class="sxs-lookup"><span data-stu-id="21d21-123">`1.0` should be used avoided whenever possible, as it uses the insecure SHA-1 hash algorithm, while `2.0` uses the secure SHA-256 algorithm However, `1.0` is the only supported algorithm on Windows 7 and Server 2008R2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21d21-124">-Path</span><span class="sxs-lookup"><span data-stu-id="21d21-124">-Path</span></span>

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

### <span data-ttu-id="21d21-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="21d21-125">-Confirm</span></span>

<span data-ttu-id="21d21-126">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="21d21-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="21d21-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="21d21-127">-WhatIf</span></span>

<span data-ttu-id="21d21-128">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="21d21-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="21d21-129">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="21d21-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="21d21-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21d21-130">CommonParameters</span></span>
<span data-ttu-id="21d21-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21d21-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21d21-132">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="21d21-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="21d21-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="21d21-133">INPUTS</span></span>

### <span data-ttu-id="21d21-134">System. String</span><span class="sxs-lookup"><span data-stu-id="21d21-134">System.String</span></span>

<span data-ttu-id="21d21-135">De pijp lijn neemt een teken reeks die wordt gebruikt als de naam van de catalogus.</span><span class="sxs-lookup"><span data-stu-id="21d21-135">The pipeline takes a string that is used as the catalog filename.</span></span>

## <span data-ttu-id="21d21-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="21d21-136">OUTPUTS</span></span>

### <span data-ttu-id="21d21-137">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="21d21-137">System.IO.FileInfo</span></span>

## <span data-ttu-id="21d21-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="21d21-138">NOTES</span></span>

## <span data-ttu-id="21d21-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="21d21-139">RELATED LINKS</span></span>

[<span data-ttu-id="21d21-140">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="21d21-140">Test-FileCatalog</span></span>](Test-FileCatalog.md)

[<span data-ttu-id="21d21-141">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="21d21-141">PowerShellGet</span></span>](/powerShell/module/powershellget)
