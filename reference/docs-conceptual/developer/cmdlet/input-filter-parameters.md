---
title: Invoer filter parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355494"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="7aeca-102">Filterparameters voor invoer</span><span class="sxs-lookup"><span data-stu-id="7aeca-102">Input Filter Parameters</span></span>

<span data-ttu-id="7aeca-103">Een cmdlet kan `Filter`, `Include`-en `Exclude` para meters definiëren waarmee de set invoer objecten wordt gefilterd waarop de cmdlet van invloed is.</span><span class="sxs-lookup"><span data-stu-id="7aeca-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="7aeca-104">Normaal gesp roken wordt de set invoer objecten opgegeven met een `InputObject`, `Path` of de para meter `Name`.</span><span class="sxs-lookup"><span data-stu-id="7aeca-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="7aeca-105">Een cmdlet kan bijvoorbeeld een para meter `Path` hebben die meerdere paden accepteert met behulp van joker tekens, en elk pad wijst naar een invoer object.</span><span class="sxs-lookup"><span data-stu-id="7aeca-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="7aeca-106">In combi natie met de para meters `Filter`, `Include` en `Exclude` worden de paden die de cmdlet op elke keer dat deze wordt aangeroepen, verder gekwalificeerd.</span><span class="sxs-lookup"><span data-stu-id="7aeca-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="7aeca-107">Para meters opnemen en uitsluiten</span><span class="sxs-lookup"><span data-stu-id="7aeca-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="7aeca-108">De para meters `Include` en `Exclude` identificeren de objecten die worden opgenomen in of uitgesloten van de set invoer objecten die worden door gegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7aeca-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="7aeca-109">Gebruik deze para meters wanneer het filter kan worden weer gegeven in de standaard taal joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7aeca-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="7aeca-110">(Zie het [ondersteunings joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md)voor meer informatie over joker tekens.) De para meter `Include` bevat alle objecten waarvan de namen overeenkomen met het insluitings filter.</span><span class="sxs-lookup"><span data-stu-id="7aeca-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="7aeca-111">Met de para meter `Exclude` worden alle objecten uitgesloten waarvan de namen overeenkomen met het filter.</span><span class="sxs-lookup"><span data-stu-id="7aeca-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="7aeca-112">Filter parameter</span><span class="sxs-lookup"><span data-stu-id="7aeca-112">Filter Parameter</span></span>

<span data-ttu-id="7aeca-113">De para meter `Filter` geeft een filter op dat niet wordt weer gegeven in de standaard taal voor joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7aeca-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="7aeca-114">Active Directory Service interfaces (ADSI) of SQL-filters kunnen bijvoorbeeld worden door gegeven aan de cmdlet via de para meter `Filter`.</span><span class="sxs-lookup"><span data-stu-id="7aeca-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="7aeca-115">In de cmdlets van Windows Power shell worden deze filters opgegeven door de Windows Power shell-providers die de cmdlet gebruiken om toegang te krijgen tot een gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="7aeca-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="7aeca-116">Elke provider definieert meestal een eigen filter.</span><span class="sxs-lookup"><span data-stu-id="7aeca-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="7aeca-117">Filteren als er geen set invoer objecten is opgegeven</span><span class="sxs-lookup"><span data-stu-id="7aeca-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="7aeca-118">Als er geen set invoer objecten is opgegeven, betekent dit meestal dat u wilt filteren op alle objecten.</span><span class="sxs-lookup"><span data-stu-id="7aeca-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="7aeca-119">Zie[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7aeca-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="7aeca-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7aeca-120">See Also</span></span>

[<span data-ttu-id="7aeca-121">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="7aeca-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)