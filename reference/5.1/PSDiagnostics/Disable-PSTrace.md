---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: fc58e0bcfdd0b4ee7c7ee383b44f7d7f428c34c0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250338"
---
# <span data-ttu-id="f4720-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="f4720-102">Disable-PSTrace</span></span>

## <span data-ttu-id="f4720-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f4720-103">SYNOPSIS</span></span>
<span data-ttu-id="f4720-104">Hiermee schakelt u de logboeken van de micro soft-Windows-Power shell-gebeurtenis provider uit.</span><span class="sxs-lookup"><span data-stu-id="f4720-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="f4720-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f4720-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="f4720-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f4720-106">DESCRIPTION</span></span>

<span data-ttu-id="f4720-107">Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f4720-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="f4720-108">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="f4720-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f4720-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f4720-109">EXAMPLES</span></span>

### <span data-ttu-id="f4720-110">Voor beeld 1: het analytische gebeurtenis logboek uitschakelen voor Power shell</span><span class="sxs-lookup"><span data-stu-id="f4720-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="f4720-111">In het volgende voor beeld wordt alleen het analytische gebeurtenis logboek van de provider micro soft-Windows-Power shell uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f4720-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="f4720-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4720-112">PARAMETERS</span></span>

### <span data-ttu-id="f4720-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="f4720-113">-AnalyticOnly</span></span>

<span data-ttu-id="f4720-114">Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell uit.</span><span class="sxs-lookup"><span data-stu-id="f4720-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="f4720-115">Het operationele gebeurtenis logboek is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f4720-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="f4720-116">INVOER</span><span class="sxs-lookup"><span data-stu-id="f4720-116">INPUTS</span></span>

### <span data-ttu-id="f4720-117">Geen</span><span class="sxs-lookup"><span data-stu-id="f4720-117">None</span></span>

## <span data-ttu-id="f4720-118">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f4720-118">OUTPUTS</span></span>

### <span data-ttu-id="f4720-119">System. object</span><span class="sxs-lookup"><span data-stu-id="f4720-119">System.Object</span></span>

## <span data-ttu-id="f4720-120">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f4720-120">NOTES</span></span>

<span data-ttu-id="f4720-121">Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f4720-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="f4720-122">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="f4720-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f4720-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f4720-123">RELATED LINKS</span></span>

[<span data-ttu-id="f4720-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f4720-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="f4720-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f4720-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="f4720-126">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="f4720-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)
