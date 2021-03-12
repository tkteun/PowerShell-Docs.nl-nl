---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: 1d202b7bbda359f859838475eb9f37730506bd1f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194365"
---
# <span data-ttu-id="cd874-103">Export-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="cd874-103">Export-BinaryMiLog</span></span>

## <span data-ttu-id="cd874-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cd874-104">SYNOPSIS</span></span>
<span data-ttu-id="cd874-105">Hiermee maakt u een binaire, gecodeerde weer gave van een object of objecten en slaat u deze op in een bestand.</span><span class="sxs-lookup"><span data-stu-id="cd874-105">Creates a binary encoded representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="cd874-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cd874-106">SYNTAX</span></span>

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="cd874-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cd874-107">DESCRIPTION</span></span>

<span data-ttu-id="cd874-108">`Export-BinaryMILog`Met de cmdlet wordt een op binaire wijze weer gave van een object of objecten gemaakt en opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="cd874-108">The `Export-BinaryMILog` cmdlet creates a binary-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="cd874-109">U kunt de cmdlet vervolgens gebruiken `Import-BinaryMiLog` om het opgeslagen object opnieuw te maken op basis van de inhoud van het bestand.</span><span class="sxs-lookup"><span data-stu-id="cd874-109">You can then use the `Import-BinaryMiLog` cmdlet to re-create the saved object based on the contents of that file.</span></span>

<span data-ttu-id="cd874-110">Deze cmdlet is vergelijkbaar met `Import-Clixml` , behalve dat `Export-BinaryMILog` het resulterende object wordt opgeslagen in een bestand met binaire code ring.</span><span class="sxs-lookup"><span data-stu-id="cd874-110">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="cd874-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cd874-111">EXAMPLES</span></span>

### <span data-ttu-id="cd874-112">Voor beeld 1: een binaire weer gave van CimInstances maken</span><span class="sxs-lookup"><span data-stu-id="cd874-112">Example 1 - Create a binary representation of CimInstances</span></span>

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

<span data-ttu-id="cd874-113">Met deze opdracht wordt **CimInstances** geëxporteerd naar een binair mi-logboek bestand dat is opgegeven door de para meter Path.</span><span class="sxs-lookup"><span data-stu-id="cd874-113">This command exports **CimInstances** to a binary MI log file specified by the Path parameter.</span></span> <span data-ttu-id="cd874-114">Zie het voor beeld voor Import-BinaryMiLog om te zien hoe u de **CimInstances** opnieuw kunt maken door dit bestand te importeren.</span><span class="sxs-lookup"><span data-stu-id="cd874-114">See the example for Import-BinaryMiLog to see how to recreate the **CimInstances** by importing this file.</span></span>

## <span data-ttu-id="cd874-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd874-115">PARAMETERS</span></span>

### <span data-ttu-id="cd874-116">-Input object</span><span class="sxs-lookup"><span data-stu-id="cd874-116">-InputObject</span></span>

<span data-ttu-id="cd874-117">Hiermee geeft u de invoer voor deze cmdlet op.</span><span class="sxs-lookup"><span data-stu-id="cd874-117">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="cd874-118">U kunt deze para meter gebruiken, of u kunt de invoer door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd874-118">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cd874-119">-Path</span><span class="sxs-lookup"><span data-stu-id="cd874-119">-Path</span></span>

<span data-ttu-id="cd874-120">Hiermee geeft u het pad van het bestand waarin de binaire weer gave van het object moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="cd874-120">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="cd874-121">De para meter **Path** ondersteunt joker tekens en relatieve paden.</span><span class="sxs-lookup"><span data-stu-id="cd874-121">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="cd874-122">Met deze cmdlet wordt een fout gegenereerd als het pad wordt omgezet in meer dan een bestand.</span><span class="sxs-lookup"><span data-stu-id="cd874-122">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="cd874-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd874-123">CommonParameters</span></span>

<span data-ttu-id="cd874-124">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cd874-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd874-125">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cd874-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cd874-126">INVOER</span><span class="sxs-lookup"><span data-stu-id="cd874-126">INPUTS</span></span>

### <span data-ttu-id="cd874-127">Micro soft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="cd874-127">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="cd874-128">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cd874-128">OUTPUTS</span></span>

### <span data-ttu-id="cd874-129">System. object</span><span class="sxs-lookup"><span data-stu-id="cd874-129">System.Object</span></span>

## <span data-ttu-id="cd874-130">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cd874-130">NOTES</span></span>

## <span data-ttu-id="cd874-131">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cd874-131">RELATED LINKS</span></span>

[<span data-ttu-id="cd874-132">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="cd874-132">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="cd874-133">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="cd874-133">Import-BinaryMiLog</span></span>](import-binarymilog.md)

[<span data-ttu-id="cd874-134">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="cd874-134">Import-Clixml</span></span>](../microsoft.powershell.utility/import-clixml.md)
