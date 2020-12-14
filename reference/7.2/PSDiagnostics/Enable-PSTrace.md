---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 231c2e3d2e28463be35ff1c9d5dab5a5d958f430
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705669"
---
# <span data-ttu-id="164c2-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="164c2-102">Enable-PSTrace</span></span>

## <span data-ttu-id="164c2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="164c2-103">SYNOPSIS</span></span>
<span data-ttu-id="164c2-104">Hiermee schakelt u de logboeken van de gebeurtenis provider van micro soft Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="164c2-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="164c2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="164c2-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="164c2-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="164c2-106">DESCRIPTION</span></span>

<span data-ttu-id="164c2-107">Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="164c2-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="164c2-108">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="164c2-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="164c2-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="164c2-109">EXAMPLES</span></span>

### <span data-ttu-id="164c2-110">Voor beeld 1: het analytische gebeurtenis logboek inschakelen voor Power shell</span><span class="sxs-lookup"><span data-stu-id="164c2-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="164c2-111">In het volgende voor beeld wordt alleen het logboek van de analytische gebeurtenissen van de provider micro soft-Windows-Power shell ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="164c2-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="164c2-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="164c2-112">PARAMETERS</span></span>

### <span data-ttu-id="164c2-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="164c2-113">-AnalyticOnly</span></span>

<span data-ttu-id="164c2-114">Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="164c2-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="164c2-115">Het operationele gebeurtenis logboek is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="164c2-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="164c2-116">-Force</span><span class="sxs-lookup"><span data-stu-id="164c2-116">-Force</span></span>

<span data-ttu-id="164c2-117">Wordt gebruikt om de wijziging te forceren zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="164c2-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="164c2-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="164c2-118">CommonParameters</span></span>
<span data-ttu-id="164c2-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="164c2-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="164c2-120">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="164c2-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="164c2-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="164c2-121">INPUTS</span></span>

### <span data-ttu-id="164c2-122">Geen</span><span class="sxs-lookup"><span data-stu-id="164c2-122">None</span></span>

## <span data-ttu-id="164c2-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="164c2-123">OUTPUTS</span></span>

### <span data-ttu-id="164c2-124">Geen</span><span class="sxs-lookup"><span data-stu-id="164c2-124">None</span></span>

## <span data-ttu-id="164c2-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="164c2-125">NOTES</span></span>

<span data-ttu-id="164c2-126">Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="164c2-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="164c2-127">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="164c2-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="164c2-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="164c2-128">RELATED LINKS</span></span>

[<span data-ttu-id="164c2-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="164c2-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="164c2-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="164c2-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="164c2-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="164c2-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)

