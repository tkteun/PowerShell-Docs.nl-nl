---
title: Filter invoerparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845736"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="47c12-102">Filterparameters voor invoer</span><span class="sxs-lookup"><span data-stu-id="47c12-102">Input Filter Parameters</span></span>

<span data-ttu-id="47c12-103">Een cmdlet kunt definiëren `Filter`, `Include`, en `Exclude` parameters die de set invoer objecten die gevolgen heeft voor de cmdlet filteren.</span><span class="sxs-lookup"><span data-stu-id="47c12-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="47c12-104">Normaal gesproken de set invoer objecten wordt opgegeven door een `InputObject`, `Path`, of `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="47c12-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="47c12-105">Bijvoorbeeld, een cmdlet kunt hebben een `Path` parameter meerdere paden accepteert met jokertekens en elk pad verwijst naar een invoer-object.</span><span class="sxs-lookup"><span data-stu-id="47c12-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="47c12-106">Samen, gebruikt de `Filter`, `Include`, en `Exclude` verdere parameters in aanmerking komen de paden die de cmdlet werkt op telkens wanneer de toepassing wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="47c12-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="47c12-107">Opnemen en uitsluiten van Parameters</span><span class="sxs-lookup"><span data-stu-id="47c12-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="47c12-108">De `Include` en `Exclude` parameters identificeren de objecten die zijn opgenomen of uitgesloten van de set invoer objecten die zijn doorgegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="47c12-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="47c12-109">Deze parameters gebruiken wanneer u het filter kan worden uitgedrukt in de standard wildcard-taal.</span><span class="sxs-lookup"><span data-stu-id="47c12-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="47c12-110">(Zie voor meer informatie over jokertekens [ondersteunt jokertekens in de Cmdlet-Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) De `Include` parameter bevat alle objecten waarvan de namen overeenkomen met het filter opgenomen.</span><span class="sxs-lookup"><span data-stu-id="47c12-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="47c12-111">De `Exclude` parameter niet van toepassing op alle objecten waarvan de namen overeenkomen met het filter.</span><span class="sxs-lookup"><span data-stu-id="47c12-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="47c12-112">Filter Parameter</span><span class="sxs-lookup"><span data-stu-id="47c12-112">Filter Parameter</span></span>

<span data-ttu-id="47c12-113">De `Filter` parameter geeft u een filter op dat niet wordt uitgedrukt in de standard wildcard-taal.</span><span class="sxs-lookup"><span data-stu-id="47c12-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="47c12-114">Bijvoorbeeld, Active Directory Service Interfaces (ADSI) of SQL-filters kunnen worden doorgegeven aan de cmdlet via de `Filter` parameter.</span><span class="sxs-lookup"><span data-stu-id="47c12-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="47c12-115">Deze filters worden in de beschikbare Windows PowerShell cmdlets, opgegeven door de Windows PowerShell-providers die gebruikmaken van de cmdlet voor toegang tot een gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="47c12-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="47c12-116">Elke provider definieert doorgaans een eigen filter.</span><span class="sxs-lookup"><span data-stu-id="47c12-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="47c12-117">Als u geen Set invoer objecten opgeeft filteren</span><span class="sxs-lookup"><span data-stu-id="47c12-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="47c12-118">Als u geen set invoer objecten opgeeft, betekent dit doorgaans om te filteren op basis van alle objecten.</span><span class="sxs-lookup"><span data-stu-id="47c12-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="47c12-119">Zie voor meer informatie,[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="47c12-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="47c12-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="47c12-120">See Also</span></span>

[<span data-ttu-id="47c12-121">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="47c12-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)