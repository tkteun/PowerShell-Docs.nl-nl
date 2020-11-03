---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: e9b9e63815e1eb312a30eca11c691107ea3d070f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250812"
---
# <span data-ttu-id="c8dfb-103">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="c8dfb-103">Get-ComputerInfo</span></span>

## <span data-ttu-id="c8dfb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c8dfb-104">SYNOPSIS</span></span>
<span data-ttu-id="c8dfb-105">Hiermee haalt u een geconsolideerd object op met de eigenschappen van het systeem en het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-105">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="c8dfb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c8dfb-106">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c8dfb-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c8dfb-107">DESCRIPTION</span></span>

<span data-ttu-id="c8dfb-108">De `Get-ComputerInfo` cmdlet haalt een geconsolideerd object op van de eigenschappen van het systeem en het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-108">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="c8dfb-109">Deze cmdlet is geïntroduceerd in Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-109">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="c8dfb-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c8dfb-110">EXAMPLES</span></span>

### <span data-ttu-id="c8dfb-111">Voor beeld 1: alle computer Eigenschappen ophalen</span><span class="sxs-lookup"><span data-stu-id="c8dfb-111">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="c8dfb-112">Met deze opdracht worden alle eigenschappen van het systeem en het besturings systeem van de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-112">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="c8dfb-113">Voor beeld 2: alle eigenschappen van het besturings systeem van de computer ophalen</span><span class="sxs-lookup"><span data-stu-id="c8dfb-113">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="c8dfb-114">Met deze opdracht worden alle eigenschappen van het besturings systeem van de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-114">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="c8dfb-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c8dfb-115">PARAMETERS</span></span>

### <span data-ttu-id="c8dfb-116">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="c8dfb-116">-Property</span></span>

<span data-ttu-id="c8dfb-117">Hiermee geeft u als een teken reeks matrix de computer eigenschappen op waarin deze cmdlet wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-117">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

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

### <span data-ttu-id="c8dfb-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8dfb-118">CommonParameters</span></span>

<span data-ttu-id="c8dfb-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8dfb-120">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c8dfb-120">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c8dfb-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="c8dfb-121">INPUTS</span></span>

### <span data-ttu-id="c8dfb-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="c8dfb-122">System.String[]</span></span>

## <span data-ttu-id="c8dfb-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c8dfb-123">OUTPUTS</span></span>

### <span data-ttu-id="c8dfb-124">Micro soft. Power shell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="c8dfb-124">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="c8dfb-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c8dfb-125">NOTES</span></span>

## <span data-ttu-id="c8dfb-126">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c8dfb-126">RELATED LINKS</span></span>
