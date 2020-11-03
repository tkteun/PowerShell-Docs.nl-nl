---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/invoke-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-OperationValidation
ms.openlocfilehash: 6c9d4001392de48032a0fe1ba3667db90ea614fc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250514"
---
# <span data-ttu-id="cbd15-103">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="cbd15-103">Invoke-OperationValidation</span></span>

## <span data-ttu-id="cbd15-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cbd15-104">SYNOPSIS</span></span>

<span data-ttu-id="cbd15-105">Hiermee worden tests voor het valideren van de bewerkings raamwerk aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="cbd15-105">Invokes Operation Validation Framework tests.</span></span>

## <span data-ttu-id="cbd15-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cbd15-106">SYNTAX</span></span>

### <span data-ttu-id="cbd15-107">FileAndTest (standaard)</span><span class="sxs-lookup"><span data-stu-id="cbd15-107">FileAndTest (Default)</span></span>

```
Invoke-OperationValidation [-TestInfo <PSObject[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cbd15-108">Pad</span><span class="sxs-lookup"><span data-stu-id="cbd15-108">Path</span></span>

```
Invoke-OperationValidation [-testFilePath <String[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="cbd15-109">UseGetOperationTest</span><span class="sxs-lookup"><span data-stu-id="cbd15-109">UseGetOperationTest</span></span>

```
Invoke-OperationValidation [-ModuleName <String[]>] [-TestType <String[]>] [-IncludePesterOutput] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cbd15-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cbd15-110">DESCRIPTION</span></span>

<span data-ttu-id="cbd15-111">Met de cmdlet **invoke-OperationValidation** worden bewerkings validatie raamwerk tests aangeroepen voor een opgegeven module.</span><span class="sxs-lookup"><span data-stu-id="cbd15-111">The **Invoke-OperationValidation** cmdlet invokes Operation Validation Framework tests for a specified module.</span></span>

## <span data-ttu-id="cbd15-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cbd15-112">EXAMPLES</span></span>

### <span data-ttu-id="cbd15-113">Voor beeld 1: een validatie test voor bewerkingen aanroepen</span><span class="sxs-lookup"><span data-stu-id="cbd15-113">Example 1: Invoke an Operation Validation test</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "OperationValidation" | Invoke-OperationValidation -IncludePesterOutput
Describing Simple Test Suite
 [+] first Operational test 20ms
 [+] second Operational test 19ms
 [+] third Operational test 9ms
Tests completed in 48ms
Passed: 3 Failed: 0 Skipped: 0 Pending: 0
Describing Scenario targeted tests
   Context The RemoteAccess service
    [+] The service is running 37ms
   Context The Firewall Rules
    [+] A rule for TCP port 3389 is enabled 1.19s
    [+] A rule for UDP port 3389 is enabled 11ms
Tests completed in 1.24s
Passed: 3 Failed: 0 Skipped: 0 Pending: 0




   Module: OperationValidation




Result  Name
------- --------
Passed  Simple Test Suite::first Operational test
Passed  Simple Test Suite::second Operational test
Passed  Simple Test Suite::third Operational test
Passed  Scenario targeted tests:The RemoteAccess service:The service is running
Passed  Scenario targeted tests:The Firewall Rules:A rule for TCP port 3389 is enabled
Passed  Scenario targeted tests:The Firewall Rules:A rule for UDP port 3389 is enabled
```

<span data-ttu-id="cbd15-114">Met deze opdracht wordt de module met de naam OperationValidation opgehaald en wordt de pijplijn operator gebruikt om deze door te geven aan de cmdlet **invoke-OperationValidation** , waarmee de test wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cbd15-114">This command gets the module named OperationValidation, and uses the pipeline operator to pass it to the **Invoke-OperationValidation** cmdlet, which runs the test.</span></span>

## <span data-ttu-id="cbd15-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbd15-115">PARAMETERS</span></span>

### <span data-ttu-id="cbd15-116">-IncludePesterOutput</span><span class="sxs-lookup"><span data-stu-id="cbd15-116">-IncludePesterOutput</span></span>

<span data-ttu-id="cbd15-117">Inclusief ongewenste test uitvoer.</span><span class="sxs-lookup"><span data-stu-id="cbd15-117">Includes Pester test output.</span></span>
<span data-ttu-id="cbd15-118">De standaard waarde is $False.</span><span class="sxs-lookup"><span data-stu-id="cbd15-118">The default is $False.</span></span>

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

### <span data-ttu-id="cbd15-119">-Module naam</span><span class="sxs-lookup"><span data-stu-id="cbd15-119">-ModuleName</span></span>

<span data-ttu-id="cbd15-120">Hiermee geeft u een matrix met namen van modules op.</span><span class="sxs-lookup"><span data-stu-id="cbd15-120">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbd15-121">-testFilePath</span><span class="sxs-lookup"><span data-stu-id="cbd15-121">-testFilePath</span></span>

<span data-ttu-id="cbd15-122">Hiermee geeft u het pad van een test bestand voor bewerkings validatie Framework.</span><span class="sxs-lookup"><span data-stu-id="cbd15-122">Specifies the path of an Operation Validation Framework test file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd15-123">-TestInfo</span><span class="sxs-lookup"><span data-stu-id="cbd15-123">-TestInfo</span></span>

<span data-ttu-id="cbd15-124">Hiermee geeft u een aangepast object op waarmee het pad naar het bestand en de naam van de test moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cbd15-124">Specifies a custom object that specifies the path to the file and the name of the test to run.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: FileAndTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd15-125">-TestType</span><span class="sxs-lookup"><span data-stu-id="cbd15-125">-TestType</span></span>

<span data-ttu-id="cbd15-126">Hiermee geeft u een matrix met test typen op.</span><span class="sxs-lookup"><span data-stu-id="cbd15-126">Specifies an array of test types.</span></span>
<span data-ttu-id="cbd15-127">Geldige waarden zijn eenvoudig, uitgebreid of beide.</span><span class="sxs-lookup"><span data-stu-id="cbd15-127">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="cbd15-128">De standaard instelling is eenvoudig, uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="cbd15-128">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbd15-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cbd15-129">-Confirm</span></span>

<span data-ttu-id="cbd15-130">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cbd15-130">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbd15-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cbd15-131">-WhatIf</span></span>

<span data-ttu-id="cbd15-132">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cbd15-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cbd15-133">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cbd15-133">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbd15-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbd15-134">CommonParameters</span></span>
<span data-ttu-id="cbd15-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cbd15-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbd15-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cbd15-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cbd15-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="cbd15-137">INPUTS</span></span>

### <span data-ttu-id="cbd15-138">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="cbd15-138">PSCustomObject</span></span>

<span data-ttu-id="cbd15-139">U kunt de uitvoer van **Get-OperationValidation** naar deze cmdlet door geven.</span><span class="sxs-lookup"><span data-stu-id="cbd15-139">You can pipe the output of **Get-OperationValidation** to this cmdlet.</span></span>

## <span data-ttu-id="cbd15-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cbd15-140">OUTPUTS</span></span>

### <span data-ttu-id="cbd15-141">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="cbd15-141">PSCustomObject</span></span>

<span data-ttu-id="cbd15-142">De **PSCustomObject** beschrijft of de validatie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="cbd15-142">The **PSCustomObject** describes whether the validation was successful.</span></span>

## <span data-ttu-id="cbd15-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cbd15-143">NOTES</span></span>

## <span data-ttu-id="cbd15-144">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cbd15-144">RELATED LINKS</span></span>

[<span data-ttu-id="cbd15-145">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="cbd15-145">Get-OperationValidation</span></span>](Get-OperationValidation.md)
