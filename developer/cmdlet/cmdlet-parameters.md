---
title: Cmdlet-Parameters | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845302"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="d7580-102">Cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="d7580-102">Cmdlet Parameters</span></span>

<span data-ttu-id="d7580-103">Cmdlet-parameters bieden het mechanisme waarmee een cmdlet voor het accepteren van invoer.</span><span class="sxs-lookup"><span data-stu-id="d7580-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="d7580-104">Parameters kunnen accepteren invoer rechtstreeks vanaf de opdrachtregel of vanuit de pipeline, de argumenten doorgegeven aan de cmdlet-objecten (ook wel bekend als *waarden*) van deze parameters de gegevensinvoer die door de cmdlet accepteert, kunt opgeven hoe de cmdlet moet de acties en de gegevens die de cmdlet retourneert aan de pijplijn worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d7580-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d7580-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="d7580-105">In This Section</span></span>

<span data-ttu-id="d7580-106">[Eigenschappen als Parameters declareren](./declaring-properties-as-parameters.md) bevat algemene informatie die u begrijpen moet voordat u de parameters van een cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="d7580-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="d7580-107">[Typen van de Cmdlet-Parameters](./types-of-cmdlet-parameters.md) beschrijft de verschillende soorten parameters die u in de cmdlets aangeven kunt.</span><span class="sxs-lookup"><span data-stu-id="d7580-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="d7580-108">[Naam van de cmdlet-Parameter en richtlijnen voor functionaliteit](./standard-cmdlet-parameter-names-and-types.md) discussen de namen van de gegevens van het type en de functionaliteit van standard parameters aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="d7580-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="d7580-109">[Aliassen](./parameter-aliases.md) bespreekt de aliassen die u voor parameters definiëren kunt.</span><span class="sxs-lookup"><span data-stu-id="d7580-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="d7580-110">[Namen van algemene parameters](./common-parameter-names.md) in dit onderwerp beschrijft de parameters die door Windows PowerShell-cmdlets worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d7580-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="d7580-111">[De cmdlet-Parameter ingesteld](./cmdlet-parameter-sets.md) wordt besproken hoe parametersets inschakelen u één cmdlet die u verschillende acties voor verschillende scenario's uitvoeren kunt te schrijven.</span><span class="sxs-lookup"><span data-stu-id="d7580-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="d7580-112">[Dynamische Parameters van de cmdlet](./cmdlet-dynamic-parameters.md) parameters die beschikbaar voor de gebruiker speciale voorwaarden zijn worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="d7580-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="d7580-113">[Ondersteuning van jokertekens in de Cmdlet-Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) wordt beschreven hoe u bieden ondersteuning voor jokertekens bij het ontwerpen van een cmdlet die wordt uitgevoerd op basis van een groep resources.</span><span class="sxs-lookup"><span data-stu-id="d7580-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="d7580-114">[Valideren van de invoer van de Parameter](./validating-parameter-input.md) wordt beschreven hoe de argumenten doorgegeven aan de cmdlet-parameters in Windows PowerShell wordt gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="d7580-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="d7580-115">[Filter invoerparameters](./input-filter-parameters.md) Discusses de `Filter`, `Include`, en `Exclude` parameters die de set invoer objecten die gevolgen heeft voor de cmdlet filteren.</span><span class="sxs-lookup"><span data-stu-id="d7580-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d7580-116">Gerelateerde secties</span><span class="sxs-lookup"><span data-stu-id="d7580-116">Related Sections</span></span>

[<span data-ttu-id="d7580-117">Het valideren van de Parameter-invoer</span><span class="sxs-lookup"><span data-stu-id="d7580-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="d7580-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d7580-118">See Also</span></span>

[<span data-ttu-id="d7580-119">Kenmerk parameterdeclaratie</span><span class="sxs-lookup"><span data-stu-id="d7580-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="d7580-120">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="d7580-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
