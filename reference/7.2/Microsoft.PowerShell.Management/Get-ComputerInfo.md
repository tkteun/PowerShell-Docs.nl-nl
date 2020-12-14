---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: abc820bd6f8f5c8cd8c6301aacee268c82161d7e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706044"
---
# <span data-ttu-id="262b2-102">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="262b2-102">Get-ComputerInfo</span></span>

## <span data-ttu-id="262b2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="262b2-103">SYNOPSIS</span></span>
<span data-ttu-id="262b2-104">Hiermee haalt u een geconsolideerd object op met de eigenschappen van het systeem en het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="262b2-104">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="262b2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="262b2-105">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="262b2-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="262b2-106">DESCRIPTION</span></span>

<span data-ttu-id="262b2-107">De `Get-ComputerInfo` cmdlet haalt een geconsolideerd object op van de eigenschappen van het systeem en het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="262b2-107">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="262b2-108">Deze cmdlet is geïntroduceerd in Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="262b2-108">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="262b2-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="262b2-109">EXAMPLES</span></span>

### <span data-ttu-id="262b2-110">Voor beeld 1: alle computer Eigenschappen ophalen</span><span class="sxs-lookup"><span data-stu-id="262b2-110">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="262b2-111">Met deze opdracht worden alle eigenschappen van het systeem en het besturings systeem van de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="262b2-111">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="262b2-112">Voor beeld 2: alle eigenschappen van het besturings systeem van de computer ophalen</span><span class="sxs-lookup"><span data-stu-id="262b2-112">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="262b2-113">Met deze opdracht worden alle eigenschappen van het besturings systeem van de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="262b2-113">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="262b2-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="262b2-114">PARAMETERS</span></span>

### <span data-ttu-id="262b2-115">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="262b2-115">-Property</span></span>

<span data-ttu-id="262b2-116">Hiermee geeft u als een teken reeks matrix de computer eigenschappen op waarin deze cmdlet wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="262b2-116">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

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

### <span data-ttu-id="262b2-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="262b2-117">CommonParameters</span></span>

<span data-ttu-id="262b2-118">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="262b2-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="262b2-119">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="262b2-119">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="262b2-120">INVOER</span><span class="sxs-lookup"><span data-stu-id="262b2-120">INPUTS</span></span>

### <span data-ttu-id="262b2-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="262b2-121">System.String[]</span></span>

## <span data-ttu-id="262b2-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="262b2-122">OUTPUTS</span></span>

### <span data-ttu-id="262b2-123">Micro soft. Power shell. Management. ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="262b2-123">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="262b2-124">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="262b2-124">NOTES</span></span>

<span data-ttu-id="262b2-125">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="262b2-125">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="262b2-126">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="262b2-126">RELATED LINKS</span></span>
