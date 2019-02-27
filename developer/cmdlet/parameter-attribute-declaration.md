---
title: Kenmerk parameterdeclaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/07/2019
ms.locfileid: "56852141"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="e44f4-102">Declaratie van het kenmerk Parameter</span><span class="sxs-lookup"><span data-stu-id="e44f4-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="e44f4-103">De Parameter-kenmerk geeft aan dat een openbare eigenschap van de cmdlet-klasse cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="e44f4-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="e44f4-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e44f4-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="e44f4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e44f4-105">Parameters</span></span>

<span data-ttu-id="e44f4-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="e44f4-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="e44f4-107">`True` Geeft aan dat de cmdlet-parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="e44f4-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="e44f4-108">Als een vereiste parameter niet is opgegeven wanneer de cmdlet wordt aangeroepen, wordt de gebruiker voor een parameterwaarde gevraagd in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e44f4-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="e44f4-109">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="e44f4-109">The default is `false`.</span></span>

<span data-ttu-id="e44f4-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="e44f4-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="e44f4-111">Hiermee geeft u dat de parameter ingesteld dat deze cmdlet-parameter deel uitmaakt.</span><span class="sxs-lookup"><span data-stu-id="e44f4-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="e44f4-112">Als er geen parameterset is opgegeven, wordt de parameter hoort bij alle parametersets.</span><span class="sxs-lookup"><span data-stu-id="e44f4-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="e44f4-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="e44f4-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional named parameter.</span></span> <span data-ttu-id="e44f4-114">Hiermee geeft u de positie van de parameter in een Windows PowerShell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="e44f4-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="e44f4-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="e44f4-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="e44f4-116">`True` Geeft aan dat de cmdlet-parameter de waarde van een pijplijn-object heeft.</span><span class="sxs-lookup"><span data-stu-id="e44f4-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="e44f4-117">Dit trefwoord opgeven als de cmdlet toegang heeft tot de volledige-object is niet alleen een eigenschap van het object.</span><span class="sxs-lookup"><span data-stu-id="e44f4-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="e44f4-118">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="e44f4-118">The default is `false`.</span></span>

<span data-ttu-id="e44f4-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="e44f4-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="e44f4-120">`True` Geeft aan dat de cmdlet-parameter heeft de waarde van een eigenschap van een pijplijn-object met dezelfde naam of de dezelfde alias als deze parameter.</span><span class="sxs-lookup"><span data-stu-id="e44f4-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="e44f4-121">Bijvoorbeeld, als de cmdlet heeft een `Name` parameter en de pijplijn-object heeft ook een `Name` eigenschap, de waarde van de `Name` eigenschap is toegewezen aan de `Name` parameter van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e44f4-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="e44f4-122">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="e44f4-122">The default is `false`.</span></span>

<span data-ttu-id="e44f4-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel.</span><span class="sxs-lookup"><span data-stu-id="e44f4-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="e44f4-124">`True` Geeft aan dat de parameter van de cmdlet alle resterende argumenten die zijn doorgegeven aan de cmdlet accepteert.</span><span class="sxs-lookup"><span data-stu-id="e44f4-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="e44f4-125">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="e44f4-125">The default is `false`.</span></span>

<span data-ttu-id="e44f4-126">`HelpMessage` De optionele parameter met de naam.</span><span class="sxs-lookup"><span data-stu-id="e44f4-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="e44f4-127">Hiermee geeft u een korte beschrijving van de parameter.</span><span class="sxs-lookup"><span data-stu-id="e44f4-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="e44f4-128">Windows PowerShell wordt deze weergegeven als een cmdlet wordt uitgevoerd en een verplichte parameter is niet opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e44f4-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="e44f4-129">`HelpMessageBaseName` De optionele parameter met de naam. Hiermee geeft u de locatie waar de resource-id's zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="e44f4-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="e44f4-130">Deze parameter kan bijvoorbeeld opgeven dat een resource-assembly met Help-berichten die u wilt om te lokaliseren.</span><span class="sxs-lookup"><span data-stu-id="e44f4-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="e44f4-131">`HelpMessageResourceId` De optionele parameter met de naam. Hiermee geeft u de resource-id voor een Help-bericht.</span><span class="sxs-lookup"><span data-stu-id="e44f4-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="e44f4-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e44f4-132">Remarks</span></span>

- <span data-ttu-id="e44f4-133">Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e44f4-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="e44f4-134">Een cmdlet kan een onbeperkt aantal parameters hebben.</span><span class="sxs-lookup"><span data-stu-id="e44f4-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="e44f4-135">Echter voor een betere ervaring voor eindgebruikers, beperkt u het aantal parameters.</span><span class="sxs-lookup"><span data-stu-id="e44f4-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="e44f4-136">Parameters moeten worden gedeclareerd voor het openbare niet-statische velden of properties.</span><span class="sxs-lookup"><span data-stu-id="e44f4-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="e44f4-137">Parameters moeten worden gedeclareerd voor eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="e44f4-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="e44f4-138">De eigenschap een openbare set-accessor moet hebben en als de `ValueFromPipeline` of `ValueFromPipelineByPropertyName` sleutelwoord is opgegeven, moet de eigenschap een openbare get-accessor heeft hebben.</span><span class="sxs-lookup"><span data-stu-id="e44f4-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="e44f4-139">Wanneer u positionele parameters opgeeft, moet u het aantal positionele parameters in een parameter is ingesteld op minder dan vijf beperken.</span><span class="sxs-lookup"><span data-stu-id="e44f4-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="e44f4-140">En positionele parameters hoeft niet aaneengesloten te zijn.</span><span class="sxs-lookup"><span data-stu-id="e44f4-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="e44f4-141">Posities 5, 100 en 250 werken op dezelfde manier als posities 0, 1 en 2.</span><span class="sxs-lookup"><span data-stu-id="e44f4-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="e44f4-142">Wanneer de `Position` sleutelwoord niet is opgegeven, wordt de cmdlet-parameter moet worden verwezen door de naam ervan.</span><span class="sxs-lookup"><span data-stu-id="e44f4-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="e44f4-143">Wanneer u parametersets gebruikt, Let op het volgende:</span><span class="sxs-lookup"><span data-stu-id="e44f4-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="e44f4-144">Elke parameter is ingesteld, moet ten minste één unieke parameter hebben.</span><span class="sxs-lookup"><span data-stu-id="e44f4-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="e44f4-145">Goede cmdlet ontwerp geeft aan dat deze unieke parameter moet ook zijn verplicht, indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="e44f4-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="e44f4-146">Als de cmdlet is ontworpen om te worden uitgevoerd zonder parameters, is de unieke parameter kan niet verplicht.</span><span class="sxs-lookup"><span data-stu-id="e44f4-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="e44f4-147">Er is geen parameter ingesteld moet meer dan één positionele parameter met dezelfde positie bevatten.</span><span class="sxs-lookup"><span data-stu-id="e44f4-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="e44f4-148">Slechts één parameter in een parameterset moet declareren `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="e44f4-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="e44f4-149">Meerdere parameters kunnen definiëren `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="e44f4-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="e44f4-150">Meerdere parameters kunnen definiëren `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="e44f4-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="e44f4-151">Zie voor meer informatie over de richtlijnen voor de namen van parameters [namen van de Cmdlet-parameters](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="e44f4-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="e44f4-152">De parameterkenmerk wordt gedefinieerd door de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="e44f4-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e44f4-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e44f4-153">See Also</span></span>

[<span data-ttu-id="e44f4-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="e44f4-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="e44f4-155">Namen van de cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="e44f4-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="e44f4-156">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e44f4-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
