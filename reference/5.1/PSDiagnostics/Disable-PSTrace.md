---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50d4118c5805a59d291d8dd17f467e7b47d34b46
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194508"
---
# <span data-ttu-id="b9b58-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="b9b58-102">Disable-PSTrace</span></span>

## <span data-ttu-id="b9b58-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b9b58-103">SYNOPSIS</span></span>
<span data-ttu-id="b9b58-104">Hiermee schakelt u de logboeken van de micro soft-Windows-Power shell-gebeurtenis provider uit.</span><span class="sxs-lookup"><span data-stu-id="b9b58-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="b9b58-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b9b58-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="b9b58-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b9b58-106">DESCRIPTION</span></span>

<span data-ttu-id="b9b58-107">Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b9b58-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="b9b58-108">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="b9b58-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b9b58-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b9b58-109">EXAMPLES</span></span>

### <span data-ttu-id="b9b58-110">Voor beeld 1: het analytische gebeurtenis logboek uitschakelen voor Power shell</span><span class="sxs-lookup"><span data-stu-id="b9b58-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="b9b58-111">In het volgende voor beeld wordt alleen het analytische gebeurtenis logboek van de provider micro soft-Windows-Power shell uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b9b58-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="b9b58-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b9b58-112">PARAMETERS</span></span>

### <span data-ttu-id="b9b58-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="b9b58-113">-AnalyticOnly</span></span>

<span data-ttu-id="b9b58-114">Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell uit.</span><span class="sxs-lookup"><span data-stu-id="b9b58-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="b9b58-115">Het operationele gebeurtenis logboek is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b9b58-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="b9b58-116">INVOER</span><span class="sxs-lookup"><span data-stu-id="b9b58-116">INPUTS</span></span>

### <span data-ttu-id="b9b58-117">Geen</span><span class="sxs-lookup"><span data-stu-id="b9b58-117">None</span></span>

## <span data-ttu-id="b9b58-118">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b9b58-118">OUTPUTS</span></span>

### <span data-ttu-id="b9b58-119">System. object</span><span class="sxs-lookup"><span data-stu-id="b9b58-119">System.Object</span></span>

## <span data-ttu-id="b9b58-120">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b9b58-120">NOTES</span></span>

<span data-ttu-id="b9b58-121">Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b9b58-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="b9b58-122">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="b9b58-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b9b58-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b9b58-123">RELATED LINKS</span></span>

[<span data-ttu-id="b9b58-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="b9b58-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="b9b58-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="b9b58-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="b9b58-126">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="b9b58-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)
