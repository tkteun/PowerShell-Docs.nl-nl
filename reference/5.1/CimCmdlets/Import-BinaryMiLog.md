---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: b31d12f06a8d2e8e226908db9663446baf09a124
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194263"
---
# <span data-ttu-id="85332-102">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="85332-102">Import-BinaryMiLog</span></span>

## <span data-ttu-id="85332-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="85332-103">SYNOPSIS</span></span>
<span data-ttu-id="85332-104">Wordt gebruikt om de opgeslagen objecten opnieuw te maken op basis van de inhoud van een export bestand.</span><span class="sxs-lookup"><span data-stu-id="85332-104">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="85332-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="85332-105">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="85332-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="85332-106">DESCRIPTION</span></span>

<span data-ttu-id="85332-107">Gebruik deze cmdlet om opgeslagen objecten opnieuw te maken op basis van de inhoud van een export bestand dat is gemaakt door `Export-BinaryMILog` .</span><span class="sxs-lookup"><span data-stu-id="85332-107">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="85332-108">Deze cmdlet is vergelijkbaar met `Import-Clixml` , behalve dat `Export-BinaryMILog` het resulterende object wordt opgeslagen in een bestand met binaire code ring.</span><span class="sxs-lookup"><span data-stu-id="85332-108">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="85332-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="85332-109">EXAMPLES</span></span>

### <span data-ttu-id="85332-110">Voor beeld 1: objecten herstellen die zijn geëxporteerd naar een bestand</span><span class="sxs-lookup"><span data-stu-id="85332-110">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="85332-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="85332-111">PARAMETERS</span></span>

### <span data-ttu-id="85332-112">-Path</span><span class="sxs-lookup"><span data-stu-id="85332-112">-Path</span></span>

<span data-ttu-id="85332-113">Hiermee geeft u het pad van het bestand waarin de binaire weer gave van het object moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="85332-113">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="85332-114">De para meter **Path** ondersteunt joker tekens en relatieve paden.</span><span class="sxs-lookup"><span data-stu-id="85332-114">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="85332-115">Met deze cmdlet wordt een fout gegenereerd als het pad wordt omgezet in meer dan een bestand.</span><span class="sxs-lookup"><span data-stu-id="85332-115">This cmdlet generates an error if the path resolves to more than one file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="85332-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="85332-116">CommonParameters</span></span>
<span data-ttu-id="85332-117">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="85332-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="85332-118">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85332-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="85332-119">INVOER</span><span class="sxs-lookup"><span data-stu-id="85332-119">INPUTS</span></span>

### <span data-ttu-id="85332-120">Geen</span><span class="sxs-lookup"><span data-stu-id="85332-120">None</span></span>

## <span data-ttu-id="85332-121">UITVOER</span><span class="sxs-lookup"><span data-stu-id="85332-121">OUTPUTS</span></span>

### <span data-ttu-id="85332-122">System. object</span><span class="sxs-lookup"><span data-stu-id="85332-122">System.Object</span></span>

## <span data-ttu-id="85332-123">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="85332-123">NOTES</span></span>

## <span data-ttu-id="85332-124">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="85332-124">RELATED LINKS</span></span>
