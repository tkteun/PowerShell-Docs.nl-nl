---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: c3ae9fa2189b3c8b41f092b1f2ac2dfca54aebc6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250685"
---
# <span data-ttu-id="21fed-103">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="21fed-103">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="21fed-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="21fed-104">SYNOPSIS</span></span>
<span data-ttu-id="21fed-105">Hiermee worden waarden uit een `.PSD1` bestand geïmporteerd zonder dat de inhoud ervan wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="21fed-105">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="21fed-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="21fed-106">SYNTAX</span></span>

### <span data-ttu-id="21fed-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="21fed-107">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="21fed-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="21fed-108">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="21fed-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="21fed-109">DESCRIPTION</span></span>

<span data-ttu-id="21fed-110">Met de `Import-PowerShellDataFile` cmdlet worden sleutel-waardeparen van hashtabellen die in een bestand zijn gedefinieerd, veilig geïmporteerd `.PSD1` .</span><span class="sxs-lookup"><span data-stu-id="21fed-110">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="21fed-111">De waarden kunnen worden geïmporteerd `Invoke-Expression` op basis van de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="21fed-111">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="21fed-112">Voert echter `Invoke-Expression` alle code in het bestand uit.</span><span class="sxs-lookup"><span data-stu-id="21fed-112">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="21fed-113">Dit kan ongewenste resultaten opleveren of onveilige code uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="21fed-113">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="21fed-114">`Import-PowerShellDataFile` Hiermee importeert u de gegevens zonder de code aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="21fed-114">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="21fed-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="21fed-115">EXAMPLES</span></span>

### <span data-ttu-id="21fed-116">Voor beeld 1: waarden ophalen uit PSD1</span><span class="sxs-lookup"><span data-stu-id="21fed-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="21fed-117">In dit voor beeld worden de sleutel-waardeparen opgehaald die zijn opgeslagen in de hashtabel die in het bestand worden bewaard `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="21fed-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="21fed-118">`Get-Content` wordt gebruikt om de inhoud van het bestand weer te geven `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="21fed-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## <span data-ttu-id="21fed-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21fed-119">PARAMETERS</span></span>

### <span data-ttu-id="21fed-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="21fed-120">-LiteralPath</span></span>

<span data-ttu-id="21fed-121">Het pad naar het bestand dat wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="21fed-121">The path to the file being imported.</span></span> <span data-ttu-id="21fed-122">Alle tekens in het pad worden beschouwd als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="21fed-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="21fed-123">Joker tekens worden niet verwerkt.</span><span class="sxs-lookup"><span data-stu-id="21fed-123">Wildcard characters are not processed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21fed-124">-Path</span><span class="sxs-lookup"><span data-stu-id="21fed-124">-Path</span></span>

<span data-ttu-id="21fed-125">Het pad naar het bestand dat wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="21fed-125">The path to the file being imported.</span></span> <span data-ttu-id="21fed-126">Joker tekens zijn toegestaan, maar alleen het eerste overeenkomende bestand wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="21fed-126">Wildcards are allowed but only the first matching file is imported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="21fed-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21fed-127">CommonParameters</span></span>

<span data-ttu-id="21fed-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21fed-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21fed-129">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="21fed-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="21fed-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="21fed-130">INPUTS</span></span>

## <span data-ttu-id="21fed-131">UITVOER</span><span class="sxs-lookup"><span data-stu-id="21fed-131">OUTPUTS</span></span>

### <span data-ttu-id="21fed-132">System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="21fed-132">System.Collections.Hashtable</span></span>

## <span data-ttu-id="21fed-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="21fed-133">NOTES</span></span>

## <span data-ttu-id="21fed-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="21fed-134">RELATED LINKS</span></span>

[<span data-ttu-id="21fed-135">Invoke-expressie</span><span class="sxs-lookup"><span data-stu-id="21fed-135">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="21fed-136">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="21fed-136">Import-LocalizedData</span></span>](Import-LocalizedData.md)
