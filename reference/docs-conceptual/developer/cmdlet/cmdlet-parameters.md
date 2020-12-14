---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-parameters
description: Cmdlet-parameters
ms.openlocfilehash: 1ab495cb674f6b2cd769c3f64d899aec67704216
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668266"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="a93c6-103">Cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="a93c6-103">Cmdlet Parameters</span></span>

<span data-ttu-id="a93c6-104">Cmdlet-para meters bieden het mechanisme waarmee een cmdlet invoer kan accepteren.</span><span class="sxs-lookup"><span data-stu-id="a93c6-104">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="a93c6-105">Para meters kunnen rechtstreeks invoer accepteren vanaf de opdracht regel of vanuit objecten die zijn door gegeven aan de cmdlet via de pijp lijn. de argumenten (ook wel aangeduid als *waarden*) van deze para meters kunnen de invoer opgeven die de cmdlet accepteert, hoe de cmdlet de acties moet uitvoeren en de gegevens die de cmdlet retourneert naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="a93c6-105">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a93c6-106">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="a93c6-106">In This Section</span></span>

<span data-ttu-id="a93c6-107">[Eigenschappen declareren als para meters](./declaring-properties-as-parameters.md) Geeft basis informatie die u moet begrijpen voordat u de para meters van een cmdlet declareert.</span><span class="sxs-lookup"><span data-stu-id="a93c6-107">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="a93c6-108">[Typen cmdlet-para meters](./types-of-cmdlet-parameters.md) Hierin worden de verschillende typen para meters beschreven die u in cmdlets kunt declareren.</span><span class="sxs-lookup"><span data-stu-id="a93c6-108">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="a93c6-109">[Richt lijnen voor cmdlet-para meters en-functies](./standard-cmdlet-parameter-names-and-types.md) Hierin worden de namen, het aanbevolen gegevens type en de functionaliteit van de standaard parameters beschreven.</span><span class="sxs-lookup"><span data-stu-id="a93c6-109">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discusses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="a93c6-110">[Parameter aliassen](./parameter-aliases.md) Hierin worden de aliassen beschreven die u kunt definiëren voor para meters.</span><span class="sxs-lookup"><span data-stu-id="a93c6-110">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="a93c6-111">[Algemene parameter namen](./common-parameter-names.md) In dit onderwerp worden de para meters beschreven die worden toegevoegd aan cmdlets in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="a93c6-111">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="a93c6-112">[Cmdlet-parameter sets](./cmdlet-parameter-sets.md) In dit artikel wordt beschreven hoe u met parameter sets een enkele cmdlet kunt schrijven die verschillende acties voor verschillende scenario's kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a93c6-112">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="a93c6-113">[Cmdlet dynamische para meters](./cmdlet-dynamic-parameters.md) Hierin worden para meters beschreven die voor de gebruiker beschikbaar zijn onder speciale voor waarden.</span><span class="sxs-lookup"><span data-stu-id="a93c6-113">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="a93c6-114">[Ondersteuning voor joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Hierin wordt beschreven hoe u ondersteuning biedt voor joker tekens wanneer u een cmdlet ontwerpt die wordt uitgevoerd voor een groep resources.</span><span class="sxs-lookup"><span data-stu-id="a93c6-114">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="a93c6-115">[Parameter invoer valideren](./validating-parameter-input.md) Hierin wordt beschreven hoe Windows Power shell de argumenten valideert die worden door gegeven aan cmdlet-para meters.</span><span class="sxs-lookup"><span data-stu-id="a93c6-115">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="a93c6-116">[Invoer filter parameters](./input-filter-parameters.md) Hierin worden de `Filter` `Include` `Exclude` para meters, en opgegeven voor het filteren van de set invoer objecten die door de cmdlet worden beïnvloed.</span><span class="sxs-lookup"><span data-stu-id="a93c6-116">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a93c6-117">Gerelateerde secties</span><span class="sxs-lookup"><span data-stu-id="a93c6-117">Related Sections</span></span>

[<span data-ttu-id="a93c6-118">Parameterinvoer valideren</span><span class="sxs-lookup"><span data-stu-id="a93c6-118">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="a93c6-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a93c6-119">See Also</span></span>

[<span data-ttu-id="a93c6-120">Declaratie van het kenmerk Parameter</span><span class="sxs-lookup"><span data-stu-id="a93c6-120">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="a93c6-121">Windows Power shell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="a93c6-121">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
