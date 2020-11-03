---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: fea84d9ae83eae88f9a665e8a49aaf2e6743127d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249797"
---
# <span data-ttu-id="9c2ae-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="9c2ae-102">Enable-PSTrace</span></span>

## <span data-ttu-id="9c2ae-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9c2ae-103">SYNOPSIS</span></span>
<span data-ttu-id="9c2ae-104">Hiermee schakelt u de logboeken van de gebeurtenis provider van micro soft Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="9c2ae-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9c2ae-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="9c2ae-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9c2ae-106">DESCRIPTION</span></span>

<span data-ttu-id="9c2ae-107">Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="9c2ae-108">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="9c2ae-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9c2ae-109">EXAMPLES</span></span>

### <span data-ttu-id="9c2ae-110">Voor beeld 1: het analytische gebeurtenis logboek inschakelen voor Power shell</span><span class="sxs-lookup"><span data-stu-id="9c2ae-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="9c2ae-111">In het volgende voor beeld wordt alleen het logboek van de analytische gebeurtenissen van de provider micro soft-Windows-Power shell ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="9c2ae-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c2ae-112">PARAMETERS</span></span>

### <span data-ttu-id="9c2ae-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="9c2ae-113">-AnalyticOnly</span></span>

<span data-ttu-id="9c2ae-114">Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell in.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="9c2ae-115">Het operationele gebeurtenis logboek is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="9c2ae-116">-Force</span><span class="sxs-lookup"><span data-stu-id="9c2ae-116">-Force</span></span>

<span data-ttu-id="9c2ae-117">Wordt gebruikt om de wijziging te forceren zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="9c2ae-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c2ae-118">CommonParameters</span></span>
<span data-ttu-id="9c2ae-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c2ae-120">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c2ae-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="9c2ae-121">INPUTS</span></span>

### <span data-ttu-id="9c2ae-122">Geen</span><span class="sxs-lookup"><span data-stu-id="9c2ae-122">None</span></span>

## <span data-ttu-id="9c2ae-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9c2ae-123">OUTPUTS</span></span>

### <span data-ttu-id="9c2ae-124">Geen</span><span class="sxs-lookup"><span data-stu-id="9c2ae-124">None</span></span>

## <span data-ttu-id="9c2ae-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9c2ae-125">NOTES</span></span>

<span data-ttu-id="9c2ae-126">Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="9c2ae-127">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="9c2ae-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="9c2ae-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9c2ae-128">RELATED LINKS</span></span>

[<span data-ttu-id="9c2ae-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="9c2ae-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="9c2ae-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="9c2ae-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="9c2ae-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="9c2ae-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
