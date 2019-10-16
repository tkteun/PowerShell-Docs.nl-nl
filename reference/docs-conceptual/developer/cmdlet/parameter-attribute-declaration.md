---
title: Parameter kenmerk declaratie | Microsoft Docs
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
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356173"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="cfbcd-102">Declaratie van het kenmerk Parameter</span><span class="sxs-lookup"><span data-stu-id="cfbcd-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="cfbcd-103">Het parameter kenmerk identificeert een open bare eigenschap van de cmdlet-klasse als een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="cfbcd-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cfbcd-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="cfbcd-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="cfbcd-105">Parameters</span></span>

<span data-ttu-id="cfbcd-106">`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="cfbcd-107">`True` geeft aan dat de cmdlet-para meter is vereist.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="cfbcd-108">Als een vereiste para meter niet wordt opgegeven wanneer de cmdlet wordt aangeroepen, vraagt Windows Power shell de gebruiker om een parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="cfbcd-109">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-109">The default is `false`.</span></span>

<span data-ttu-id="cfbcd-110">`ParameterSetName` ([System. String](/dotnet/api/System.String)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="cfbcd-111">Hiermee geeft u de para meter instellen waarvan deze cmdlet-para meter deel uitmaakt.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="cfbcd-112">Als er geen parameterset is opgegeven, hoort de para meter bij alle parameter sets.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="cfbcd-113">`Position` ([System. Int32](/dotnet/api/System.Int32)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="cfbcd-114">Hiermee geeft u de positie van de para meter in een Windows Power shell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="cfbcd-115">`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="cfbcd-116">`True` geeft aan dat de cmdlet-para meter de waarde ervan uit een pijplijn object haalt.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="cfbcd-117">Geef dit tref woord op als de cmdlet toegang heeft tot het volledige object, niet alleen een eigenschap van het object.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="cfbcd-118">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-118">The default is `false`.</span></span>

<span data-ttu-id="cfbcd-119">`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="cfbcd-120">`True` geeft aan dat de cmdlet-para meter de waarde van een eigenschap van een pijplijn object met dezelfde naam of dezelfde alias als deze para meter heeft.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="cfbcd-121">Als de cmdlet bijvoorbeeld een `Name`-para meter heeft en het pijplijn object ook een eigenschap `Name` heeft, wordt de waarde van de eigenschap `Name` toegewezen aan de para meter `Name` van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="cfbcd-122">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-122">The default is `false`.</span></span>

<span data-ttu-id="cfbcd-123">`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="cfbcd-124">`True` geeft aan dat de cmdlet-para meter alle resterende argumenten accepteert die worden door gegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="cfbcd-125">De standaardwaarde is `false`.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-125">The default is `false`.</span></span>

<span data-ttu-id="cfbcd-126">`HelpMessage` optionele benoemde para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="cfbcd-127">Hiermee geeft u een korte beschrijving van de para meter.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="cfbcd-128">In Windows Power shell wordt dit bericht weer gegeven wanneer een cmdlet wordt uitgevoerd en er geen verplichte para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="cfbcd-129">`HelpMessageBaseName` optionele benoemde para meter. Hiermee geeft u de locatie op waar resource-id's zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="cfbcd-130">Met deze para meter kan bijvoorbeeld een bron-assembly worden opgegeven die Help-berichten bevat die u wilt lokaliseren.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="cfbcd-131">`HelpMessageResourceId` optionele benoemde para meter. Hiermee wordt de resource-id voor een Help-bericht opgegeven.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="cfbcd-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cfbcd-132">Remarks</span></span>

- <span data-ttu-id="cfbcd-133">Zie voor meer informatie over het declareren van dit kenmerk [cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="cfbcd-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="cfbcd-134">Een cmdlet kan een wille keurig aantal para meters hebben.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="cfbcd-135">Voor een betere gebruikers ervaring beperkt u echter het aantal para meters.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="cfbcd-136">Para meters moeten worden gedeclareerd voor open bare niet-statische velden of eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="cfbcd-137">Para meters moeten worden gedeclareerd voor eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="cfbcd-138">De eigenschap moet een accessor voor een open bare set hebben en als het sleutel woord `ValueFromPipeline` of `ValueFromPipelineByPropertyName` is opgegeven, moet de eigenschap een open bare Get-accessor hebben.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="cfbcd-139">Wanneer u positionele para meters opgeeft, beperkt u het aantal positionele para meters in een para meter ingesteld op minder dan vijf.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="cfbcd-140">En positionele para meters hoeven niet aaneengesloten te zijn.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="cfbcd-141">De posities 5, 100 en 250 werken hetzelfde als de posities 0, 1 en 2.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="cfbcd-142">Wanneer het sleutel woord `Position` niet is opgegeven, moet er naar de cmdlet-para meter worden verwezen met de naam.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="cfbcd-143">Let op het volgende wanneer u parameter sets gebruikt:</span><span class="sxs-lookup"><span data-stu-id="cfbcd-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="cfbcd-144">Elke parameterset moet ten minste één unieke para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="cfbcd-145">Goede cmdlet-ontwerp geeft aan dat deze unieke para meter ook verplicht moet zijn, indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="cfbcd-146">Als uw cmdlet is ontworpen om zonder para meters te worden uitgevoerd, kan de unieke para meter niet verplicht zijn.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="cfbcd-147">Geen enkele parameterset mag meer dan één positionele para meter met dezelfde positie bevatten.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="cfbcd-148">Er mag slechts één para meter in een parameterset `ValueFromPipeline = true` declareren.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="cfbcd-149">Meerdere para meters kunnen `ValueFromPipelineByPropertyName = true` definiëren.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="cfbcd-150">Meerdere para meters kunnen `ValueFromPipelineByPropertyName = true` definiëren.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="cfbcd-151">Zie [cmdlet para meter names](standard-cmdlet-parameter-names-and-types.md)(Engelstalig) voor meer informatie over de richt lijnen voor parameter namen.</span><span class="sxs-lookup"><span data-stu-id="cfbcd-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="cfbcd-152">Het parameter kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="cfbcd-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfbcd-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cfbcd-153">See Also</span></span>

[<span data-ttu-id="cfbcd-154">System. Management. Automation. Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="cfbcd-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="cfbcd-155">Cmdlet-parameter namen</span><span class="sxs-lookup"><span data-stu-id="cfbcd-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="cfbcd-156">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="cfbcd-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
