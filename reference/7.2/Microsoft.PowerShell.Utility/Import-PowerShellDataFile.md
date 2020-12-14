---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: 2853c5757b12e75e50948192e5a9e29889553b8e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705428"
---
# <span data-ttu-id="0797b-102">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="0797b-102">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="0797b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0797b-103">SYNOPSIS</span></span>
<span data-ttu-id="0797b-104">Hiermee worden waarden uit een `.PSD1` bestand geïmporteerd zonder dat de inhoud ervan wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="0797b-104">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="0797b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0797b-105">SYNTAX</span></span>

### <span data-ttu-id="0797b-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="0797b-106">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="0797b-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="0797b-107">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="0797b-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0797b-108">DESCRIPTION</span></span>

<span data-ttu-id="0797b-109">Met de `Import-PowerShellDataFile` cmdlet worden sleutel-waardeparen van hashtabellen die in een bestand zijn gedefinieerd, veilig geïmporteerd `.PSD1` .</span><span class="sxs-lookup"><span data-stu-id="0797b-109">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="0797b-110">De waarden kunnen worden geïmporteerd `Invoke-Expression` op basis van de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="0797b-110">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="0797b-111">Voert echter `Invoke-Expression` alle code in het bestand uit.</span><span class="sxs-lookup"><span data-stu-id="0797b-111">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="0797b-112">Dit kan ongewenste resultaten opleveren of onveilige code uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0797b-112">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="0797b-113">`Import-PowerShellDataFile` Hiermee importeert u de gegevens zonder de code aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="0797b-113">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span>

## <span data-ttu-id="0797b-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0797b-114">EXAMPLES</span></span>

### <span data-ttu-id="0797b-115">Voor beeld 1: waarden ophalen uit PSD1</span><span class="sxs-lookup"><span data-stu-id="0797b-115">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="0797b-116">In dit voor beeld worden de sleutel-waardeparen opgehaald die zijn opgeslagen in de hashtabel die in het bestand worden bewaard `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="0797b-116">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="0797b-117">`Get-Content` wordt gebruikt om de inhoud van het bestand weer te geven `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="0797b-117">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

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

## <span data-ttu-id="0797b-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0797b-118">PARAMETERS</span></span>

### <span data-ttu-id="0797b-119">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0797b-119">-LiteralPath</span></span>

<span data-ttu-id="0797b-120">Het pad naar het bestand dat wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="0797b-120">The path to the file being imported.</span></span> <span data-ttu-id="0797b-121">Alle tekens in het pad worden beschouwd als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="0797b-121">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="0797b-122">Joker tekens worden niet verwerkt.</span><span class="sxs-lookup"><span data-stu-id="0797b-122">Wildcard characters are not processed.</span></span>

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

### <span data-ttu-id="0797b-123">-Path</span><span class="sxs-lookup"><span data-stu-id="0797b-123">-Path</span></span>

<span data-ttu-id="0797b-124">Het pad naar het bestand dat wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="0797b-124">The path to the file being imported.</span></span> <span data-ttu-id="0797b-125">Joker tekens zijn toegestaan, maar alleen het eerste overeenkomende bestand wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="0797b-125">Wildcards are allowed but only the first matching file is imported.</span></span>

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

### <span data-ttu-id="0797b-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0797b-126">CommonParameters</span></span>

<span data-ttu-id="0797b-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0797b-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0797b-128">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0797b-128">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0797b-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="0797b-129">INPUTS</span></span>

## <span data-ttu-id="0797b-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0797b-130">OUTPUTS</span></span>

### <span data-ttu-id="0797b-131">System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="0797b-131">System.Collections.Hashtable</span></span>

## <span data-ttu-id="0797b-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0797b-132">NOTES</span></span>

## <span data-ttu-id="0797b-133">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0797b-133">RELATED LINKS</span></span>

[<span data-ttu-id="0797b-134">Invoke-expressie</span><span class="sxs-lookup"><span data-stu-id="0797b-134">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="0797b-135">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="0797b-135">Import-LocalizedData</span></span>](Import-LocalizedData.md)

