---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: d0bf17b4bdc169661cf4cde878739287d8be668b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343980"
---
# <span data-ttu-id="65189-103">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="65189-103">Get-ComputerInfo</span></span>

## <span data-ttu-id="65189-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="65189-104">SYNOPSIS</span></span>
<span data-ttu-id="65189-105">Hiermee haalt u een geconsolideerd object op met de eigenschappen van het systeem en het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="65189-105">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="65189-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="65189-106">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="65189-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="65189-107">DESCRIPTION</span></span>

<span data-ttu-id="65189-108">De `Get-ComputerInfo` cmdlet haalt een geconsolideerd object op van de eigenschappen van het systeem en het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="65189-108">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="65189-109">Deze cmdlet is geïntroduceerd in Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="65189-109">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="65189-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="65189-110">EXAMPLES</span></span>

### <span data-ttu-id="65189-111">Voor beeld 1: alle computer Eigenschappen ophalen</span><span class="sxs-lookup"><span data-stu-id="65189-111">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="65189-112">Met deze opdracht worden alle eigenschappen van het systeem en het besturings systeem van de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="65189-112">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="65189-113">Voor beeld 2: alle eigenschappen van het besturings systeem van de computer ophalen</span><span class="sxs-lookup"><span data-stu-id="65189-113">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="65189-114">Met deze opdracht worden alle eigenschappen van het besturings systeem van de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="65189-114">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="65189-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="65189-115">PARAMETERS</span></span>

### <span data-ttu-id="65189-116">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="65189-116">-Property</span></span>

<span data-ttu-id="65189-117">Hiermee geeft u als een teken reeks matrix de computer eigenschappen op waarin deze cmdlet wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="65189-117">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="65189-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65189-118">CommonParameters</span></span>

<span data-ttu-id="65189-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="65189-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65189-120">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="65189-120">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="65189-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="65189-121">INPUTS</span></span>

### <span data-ttu-id="65189-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="65189-122">System.String[]</span></span>

## <span data-ttu-id="65189-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="65189-123">OUTPUTS</span></span>

### <span data-ttu-id="65189-124">Micro soft. Power shell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="65189-124">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="65189-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="65189-125">NOTES</span></span>

<span data-ttu-id="65189-126">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="65189-126">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="65189-127">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="65189-127">RELATED LINKS</span></span>
