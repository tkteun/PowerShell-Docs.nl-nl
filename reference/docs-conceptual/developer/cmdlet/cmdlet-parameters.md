---
title: Cmdlet-para meters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356572"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="1a39f-102">Cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="1a39f-102">Cmdlet Parameters</span></span>

<span data-ttu-id="1a39f-103">Cmdlet-para meters bieden het mechanisme waarmee een cmdlet invoer kan accepteren.</span><span class="sxs-lookup"><span data-stu-id="1a39f-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="1a39f-104">Para meters kunnen rechtstreeks invoer accepteren vanaf de opdracht regel of vanuit objecten die zijn door gegeven aan de cmdlet via de pijp lijn. de argumenten (ook wel aangeduid als *waarden*) van deze para meters kunnen de invoer opgeven die de cmdlet accepteert, hoe de cmdlet de acties en de gegevens die de cmdlet retourneert naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="1a39f-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1a39f-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="1a39f-105">In This Section</span></span>

<span data-ttu-id="1a39f-106">[Eigenschappen declareren als para meters](./declaring-properties-as-parameters.md) Geeft basis informatie die u moet begrijpen voordat u de para meters van een cmdlet declareert.</span><span class="sxs-lookup"><span data-stu-id="1a39f-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="1a39f-107">[Typen cmdlet-para meters](./types-of-cmdlet-parameters.md) Hierin worden de verschillende typen para meters beschreven die u in cmdlets kunt declareren.</span><span class="sxs-lookup"><span data-stu-id="1a39f-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="1a39f-108">[Richt lijnen voor cmdlet-para meters en-functies](./standard-cmdlet-parameter-names-and-types.md) Discuses de namen, het aanbevolen gegevens type en de functionaliteit van de standaard parameters.</span><span class="sxs-lookup"><span data-stu-id="1a39f-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="1a39f-109">[Parameter aliassen](./parameter-aliases.md) Hierin worden de aliassen beschreven die u kunt definiëren voor para meters.</span><span class="sxs-lookup"><span data-stu-id="1a39f-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="1a39f-110">[Algemene parameter namen](./common-parameter-names.md) In dit onderwerp worden de para meters beschreven die worden toegevoegd aan cmdlets in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="1a39f-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="1a39f-111">[Cmdlet-parameter sets](./cmdlet-parameter-sets.md) In dit artikel wordt beschreven hoe u met parameter sets een enkele cmdlet kunt schrijven die verschillende acties voor verschillende scenario's kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="1a39f-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="1a39f-112">[Cmdlet dynamische para meters](./cmdlet-dynamic-parameters.md) Hierin worden para meters beschreven die voor de gebruiker beschikbaar zijn onder speciale voor waarden.</span><span class="sxs-lookup"><span data-stu-id="1a39f-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="1a39f-113">[Ondersteuning voor joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Hierin wordt beschreven hoe u ondersteuning biedt voor joker tekens wanneer u een cmdlet ontwerpt die wordt uitgevoerd voor een groep resources.</span><span class="sxs-lookup"><span data-stu-id="1a39f-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="1a39f-114">[Parameter invoer valideren](./validating-parameter-input.md) Hierin wordt beschreven hoe Windows Power shell de argumenten valideert die worden door gegeven aan cmdlet-para meters.</span><span class="sxs-lookup"><span data-stu-id="1a39f-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="1a39f-115">[Invoer filter parameters](./input-filter-parameters.md) Hierin worden de para meters voor `Filter`, `Include` en `Exclude` beschreven waarmee de set invoer objecten wordt gefilterd die door de cmdlet worden beïnvloed.</span><span class="sxs-lookup"><span data-stu-id="1a39f-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1a39f-116">Gerelateerde secties</span><span class="sxs-lookup"><span data-stu-id="1a39f-116">Related Sections</span></span>

[<span data-ttu-id="1a39f-117">Parameter invoer valideren</span><span class="sxs-lookup"><span data-stu-id="1a39f-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="1a39f-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1a39f-118">See Also</span></span>

[<span data-ttu-id="1a39f-119">Parameter kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="1a39f-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="1a39f-120">Windows Power shell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="1a39f-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
