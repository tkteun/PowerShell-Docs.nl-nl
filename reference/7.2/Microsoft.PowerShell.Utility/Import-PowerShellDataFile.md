---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: d7942abff2974064c52a8a9ac086a280959b3a63
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860852"
---
# <span data-ttu-id="aeb3e-102">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="aeb3e-102">Import-PowerShellDataFile</span></span>

## <span data-ttu-id="aeb3e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aeb3e-103">SYNOPSIS</span></span>
<span data-ttu-id="aeb3e-104">Hiermee worden waarden uit een `.PSD1` bestand geïmporteerd zonder dat de inhoud ervan wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-104">Imports values from a `.PSD1` file without invoking its contents.</span></span>

## <span data-ttu-id="aeb3e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aeb3e-105">SYNTAX</span></span>

### <span data-ttu-id="aeb3e-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="aeb3e-106">ByPath (Default)</span></span>

```
Import-PowerShellDataFile [-Path] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

### <span data-ttu-id="aeb3e-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="aeb3e-107">ByLiteralPath</span></span>

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [-SkipLimitCheck] [<CommonParameters>]
```

## <span data-ttu-id="aeb3e-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aeb3e-108">DESCRIPTION</span></span>

<span data-ttu-id="aeb3e-109">Met de `Import-PowerShellDataFile` cmdlet worden sleutel-waardeparen van hashtabellen die in een bestand zijn gedefinieerd, veilig geïmporteerd `.PSD1` .</span><span class="sxs-lookup"><span data-stu-id="aeb3e-109">The `Import-PowerShellDataFile` cmdlet safely imports key-value pairs from hashtables defined in a `.PSD1` file.</span></span> <span data-ttu-id="aeb3e-110">De waarden kunnen worden geïmporteerd `Invoke-Expression` op basis van de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-110">The values could be imported using `Invoke-Expression` on the contents of the file.</span></span>
<span data-ttu-id="aeb3e-111">Voert echter `Invoke-Expression` alle code in het bestand uit.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-111">However, `Invoke-Expression` runs any code contained in the file.</span></span> <span data-ttu-id="aeb3e-112">Dit kan ongewenste resultaten opleveren of onveilige code uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-112">This could produce unwanted results or execute unsafe code.</span></span> <span data-ttu-id="aeb3e-113">`Import-PowerShellDataFile` Hiermee importeert u de gegevens zonder de code aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-113">`Import-PowerShellDataFile` imports the data without invoking the code.</span></span> <span data-ttu-id="aeb3e-114">Er is standaard een 500-sleutel limiet, maar deze kan worden overgeslagen met de schakel optie **SkipLimitCheck** .</span><span class="sxs-lookup"><span data-stu-id="aeb3e-114">By default there is a 500 key limit but can be bypassed with the **SkipLimitCheck** switch.</span></span>

## <span data-ttu-id="aeb3e-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aeb3e-115">EXAMPLES</span></span>

### <span data-ttu-id="aeb3e-116">Voor beeld 1: waarden ophalen uit PSD1</span><span class="sxs-lookup"><span data-stu-id="aeb3e-116">Example 1: Retrieve values from PSD1</span></span>

<span data-ttu-id="aeb3e-117">In dit voor beeld worden de sleutel-waardeparen opgehaald die zijn opgeslagen in de hashtabel die in het bestand worden bewaard `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="aeb3e-117">This example retrieves the key-value pairs stored in the hashtable kept inside the `Configuration.psd1` file.</span></span> <span data-ttu-id="aeb3e-118">`Get-Content` wordt gebruikt om de inhoud van het bestand weer te geven `Configuration.psd1` .</span><span class="sxs-lookup"><span data-stu-id="aeb3e-118">`Get-Content` is used to show the contents of the `Configuration.psd1` file.</span></span>

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

## <span data-ttu-id="aeb3e-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aeb3e-119">PARAMETERS</span></span>

### <span data-ttu-id="aeb3e-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aeb3e-120">-LiteralPath</span></span>

<span data-ttu-id="aeb3e-121">Het pad naar het bestand dat wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-121">The path to the file being imported.</span></span> <span data-ttu-id="aeb3e-122">Alle tekens in het pad worden beschouwd als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-122">All characters in the path are treated as literal values.</span></span>
<span data-ttu-id="aeb3e-123">Joker tekens worden niet verwerkt.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-123">Wildcard characters are not processed.</span></span>

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

### <span data-ttu-id="aeb3e-124">-Path</span><span class="sxs-lookup"><span data-stu-id="aeb3e-124">-Path</span></span>

<span data-ttu-id="aeb3e-125">Het pad naar het bestand dat wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-125">The path to the file being imported.</span></span> <span data-ttu-id="aeb3e-126">Joker tekens zijn toegestaan, maar alleen het eerste overeenkomende bestand wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-126">Wildcards are allowed but only the first matching file is imported.</span></span>

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

### <span data-ttu-id="aeb3e-127">-SkipLimitCheck</span><span class="sxs-lookup"><span data-stu-id="aeb3e-127">-SkipLimitCheck</span></span>

<span data-ttu-id="aeb3e-128">Standaard `Import-PowerShellDataFile` worden slechts 500 sleutels uit een `.psd1` bestand geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-128">By default `Import-PowerShellDataFile` imports only 500 keys from a `.psd1` file.</span></span> <span data-ttu-id="aeb3e-129">Gebruik **SkipLimitCheck** om meer dan 500 sleutels te importeren.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-129">Use **SkipLimitCheck** to import more than 500 keys.</span></span>

```yaml
Type: Switch
Parameter Sets: All
Aliases:

Required: False
Position: 0
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aeb3e-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aeb3e-130">CommonParameters</span></span>

<span data-ttu-id="aeb3e-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aeb3e-132">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aeb3e-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="aeb3e-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="aeb3e-133">INPUTS</span></span>

## <span data-ttu-id="aeb3e-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aeb3e-134">OUTPUTS</span></span>

### <span data-ttu-id="aeb3e-135">System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="aeb3e-135">System.Collections.Hashtable</span></span>

## <span data-ttu-id="aeb3e-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aeb3e-136">NOTES</span></span>

## <span data-ttu-id="aeb3e-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aeb3e-137">RELATED LINKS</span></span>

[<span data-ttu-id="aeb3e-138">Invoke-expressie</span><span class="sxs-lookup"><span data-stu-id="aeb3e-138">Invoke-Expression</span></span>](Invoke-Expression.md)

[<span data-ttu-id="aeb3e-139">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="aeb3e-139">Import-LocalizedData</span></span>](Import-LocalizedData.md)
