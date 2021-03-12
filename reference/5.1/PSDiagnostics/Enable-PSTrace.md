---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 2ec01393a46de84b59f06995473bdff6bd5b2b4f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195028"
---
# <span data-ttu-id="0ab69-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="0ab69-102">Enable-PSTrace</span></span>

## <span data-ttu-id="0ab69-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0ab69-103">SYNOPSIS</span></span>
<span data-ttu-id="0ab69-104">Hiermee schakelt u de logboeken van de gebeurtenis provider van micro soft Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="0ab69-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="0ab69-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0ab69-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## <span data-ttu-id="0ab69-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0ab69-106">DESCRIPTION</span></span>

<span data-ttu-id="0ab69-107">Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="0ab69-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="0ab69-108">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="0ab69-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="0ab69-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0ab69-109">EXAMPLES</span></span>

### <span data-ttu-id="0ab69-110">Voor beeld 1: het analytische gebeurtenis logboek inschakelen voor Power shell</span><span class="sxs-lookup"><span data-stu-id="0ab69-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="0ab69-111">In het volgende voor beeld wordt alleen het logboek van de analytische gebeurtenissen van de provider micro soft-Windows-Power shell ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="0ab69-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="0ab69-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ab69-112">PARAMETERS</span></span>

### <span data-ttu-id="0ab69-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="0ab69-113">-AnalyticOnly</span></span>

<span data-ttu-id="0ab69-114">Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="0ab69-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="0ab69-115">Het operationele gebeurtenis logboek is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="0ab69-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="0ab69-116">-Force</span><span class="sxs-lookup"><span data-stu-id="0ab69-116">-Force</span></span>

<span data-ttu-id="0ab69-117">Wordt gebruikt om de wijziging te forceren zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="0ab69-117">Used to force the change without prompting.</span></span>

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

## <span data-ttu-id="0ab69-118">INVOER</span><span class="sxs-lookup"><span data-stu-id="0ab69-118">INPUTS</span></span>

### <span data-ttu-id="0ab69-119">Geen</span><span class="sxs-lookup"><span data-stu-id="0ab69-119">None</span></span>

## <span data-ttu-id="0ab69-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0ab69-120">OUTPUTS</span></span>

### <span data-ttu-id="0ab69-121">System. object</span><span class="sxs-lookup"><span data-stu-id="0ab69-121">System.Object</span></span>

## <span data-ttu-id="0ab69-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0ab69-122">NOTES</span></span>

<span data-ttu-id="0ab69-123">Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0ab69-123">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="0ab69-124">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="0ab69-124">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="0ab69-125">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0ab69-125">RELATED LINKS</span></span>

[<span data-ttu-id="0ab69-126">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="0ab69-126">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="0ab69-127">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="0ab69-127">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="0ab69-128">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="0ab69-128">Disable-PSTrace</span></span>](Disable-PSTrace.md)
