---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250515"
---
# <span data-ttu-id="e84c1-103">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="e84c1-103">Get-OperationValidation</span></span>

## <span data-ttu-id="e84c1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e84c1-104">SYNOPSIS</span></span>
<span data-ttu-id="e84c1-105">Hiermee worden tests voor het validatie raamwerk voor bewerkingen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e84c1-105">Gets Operation Validation Framework tests.</span></span>

## <span data-ttu-id="e84c1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e84c1-106">SYNTAX</span></span>

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e84c1-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e84c1-107">DESCRIPTION</span></span>
<span data-ttu-id="e84c1-108">Met de cmdlet **Get-OperationValidation** worden bewerkings validatie raamwerk tests voor geïnstalleerde modules opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e84c1-108">The **Get-OperationValidation** cmdlet gets Operation Validation Framework tests for installed modules.</span></span>

<span data-ttu-id="e84c1-109">Modules die een map met diagnostische gegevens bevatten, worden gecontroleerd op Ziekteloze tests in de submap Simple of complete, of beide.</span><span class="sxs-lookup"><span data-stu-id="e84c1-109">Modules that include a Diagnostics folder are inspected for Pester tests in the Simple or Comprehensive subfolder, or both.</span></span>

## <span data-ttu-id="e84c1-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e84c1-110">EXAMPLES</span></span>

### <span data-ttu-id="e84c1-111">Voor beeld 1: validatie tests voor bewerkingen ophalen</span><span class="sxs-lookup"><span data-stu-id="e84c1-111">Example 1: Get Operation Validation tests</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

<span data-ttu-id="e84c1-112">Met deze opdracht worden validatie tests uitgevoerd vanuit de module met de naam AddNumbers in de map C:\temp\modules.</span><span class="sxs-lookup"><span data-stu-id="e84c1-112">This command gets validation tests from the module named AddNumbers in the C:\temp\modules folder.</span></span>

## <span data-ttu-id="e84c1-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e84c1-113">PARAMETERS</span></span>

### <span data-ttu-id="e84c1-114">-Module naam</span><span class="sxs-lookup"><span data-stu-id="e84c1-114">-ModuleName</span></span>
<span data-ttu-id="e84c1-115">Hiermee geeft u een matrix met namen van modules op.</span><span class="sxs-lookup"><span data-stu-id="e84c1-115">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e84c1-116">-TestType</span><span class="sxs-lookup"><span data-stu-id="e84c1-116">-TestType</span></span>
<span data-ttu-id="e84c1-117">Hiermee geeft u een matrix met test typen op.</span><span class="sxs-lookup"><span data-stu-id="e84c1-117">Specifies an array of test types.</span></span>
<span data-ttu-id="e84c1-118">Geldige waarden zijn eenvoudig, uitgebreid of beide.</span><span class="sxs-lookup"><span data-stu-id="e84c1-118">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="e84c1-119">De standaard instelling is eenvoudig, uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="e84c1-119">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e84c1-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e84c1-120">CommonParameters</span></span>
<span data-ttu-id="e84c1-121">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e84c1-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e84c1-122">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e84c1-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e84c1-123">INVOER</span><span class="sxs-lookup"><span data-stu-id="e84c1-123">INPUTS</span></span>

### <span data-ttu-id="e84c1-124">Geen</span><span class="sxs-lookup"><span data-stu-id="e84c1-124">None</span></span>
<span data-ttu-id="e84c1-125">U kunt geen invoer naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="e84c1-125">You cannot pipe any input to this cmdlet.</span></span>

## <span data-ttu-id="e84c1-126">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e84c1-126">OUTPUTS</span></span>

### <span data-ttu-id="e84c1-127">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="e84c1-127">PSCustomObject</span></span>
<span data-ttu-id="e84c1-128">De **PSCustomObject** beschrijft de validatie.</span><span class="sxs-lookup"><span data-stu-id="e84c1-128">The **PSCustomObject** describes the validation.</span></span>

## <span data-ttu-id="e84c1-129">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e84c1-129">NOTES</span></span>

## <span data-ttu-id="e84c1-130">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e84c1-130">RELATED LINKS</span></span>

[<span data-ttu-id="e84c1-131">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="e84c1-131">Invoke-OperationValidation</span></span>](Invoke-OperationValidation.md)
