---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: d5008d5105b18b5a3d0423cab4282735e3d382d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250072"
---
# <span data-ttu-id="f1db3-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="f1db3-102">Enable-PSTrace</span></span>

## <span data-ttu-id="f1db3-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f1db3-103">SYNOPSIS</span></span>
<span data-ttu-id="f1db3-104">Hiermee schakelt u de logboeken van de gebeurtenis provider van micro soft Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="f1db3-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="f1db3-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f1db3-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="f1db3-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f1db3-106">DESCRIPTION</span></span>

<span data-ttu-id="f1db3-107">Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f1db3-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="f1db3-108">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="f1db3-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f1db3-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f1db3-109">EXAMPLES</span></span>

### <span data-ttu-id="f1db3-110">Voor beeld 1: het analytische gebeurtenis logboek inschakelen voor Power shell</span><span class="sxs-lookup"><span data-stu-id="f1db3-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="f1db3-111">In het volgende voor beeld wordt alleen het logboek van de analytische gebeurtenissen van de provider micro soft-Windows-Power shell ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f1db3-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="f1db3-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f1db3-112">PARAMETERS</span></span>

### <span data-ttu-id="f1db3-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="f1db3-113">-AnalyticOnly</span></span>

<span data-ttu-id="f1db3-114">Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="f1db3-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="f1db3-115">Het operationele gebeurtenis logboek is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f1db3-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="f1db3-116">-Force</span><span class="sxs-lookup"><span data-stu-id="f1db3-116">-Force</span></span>

<span data-ttu-id="f1db3-117">Wordt gebruikt om de wijziging te forceren zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="f1db3-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="f1db3-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f1db3-118">CommonParameters</span></span>
<span data-ttu-id="f1db3-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f1db3-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f1db3-120">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f1db3-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f1db3-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="f1db3-121">INPUTS</span></span>

### <span data-ttu-id="f1db3-122">Geen</span><span class="sxs-lookup"><span data-stu-id="f1db3-122">None</span></span>

## <span data-ttu-id="f1db3-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f1db3-123">OUTPUTS</span></span>

### <span data-ttu-id="f1db3-124">Geen</span><span class="sxs-lookup"><span data-stu-id="f1db3-124">None</span></span>

## <span data-ttu-id="f1db3-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f1db3-125">NOTES</span></span>

<span data-ttu-id="f1db3-126">Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f1db3-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="f1db3-127">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="f1db3-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f1db3-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f1db3-128">RELATED LINKS</span></span>

[<span data-ttu-id="f1db3-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f1db3-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="f1db3-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="f1db3-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="f1db3-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="f1db3-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
