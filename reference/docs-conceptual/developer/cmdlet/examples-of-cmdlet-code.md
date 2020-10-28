---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeelden van cmdlet-code
description: Voorbeelden van cmdlet-code
ms.openlocfilehash: 91dd2019300504697ad9a7a0c155a04600d09c58
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652915"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="aa6f4-103">Voorbeelden van cmdlet-code</span><span class="sxs-lookup"><span data-stu-id="aa6f4-103">Examples of Cmdlet Code</span></span>

<span data-ttu-id="aa6f4-104">Deze sectie bevat voor beelden van cmdlet-code die u kunt gebruiken om uw eigen cmdlets te schrijven.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-104">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa6f4-105">Zie [zelf studies voor het schrijven](./tutorials-for-writing-cmdlets.md)van cmdlets als u stapsgewijze instructies wilt voor het schrijven van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-105">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="aa6f4-106">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="aa6f4-106">In This Section</span></span>

<span data-ttu-id="aa6f4-107">[Een eenvoudige cmdlet schrijven](./how-to-write-a-simple-cmdlet.md) In dit voor beeld wordt de basis structuur van de cmdlet-code weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-107">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="aa6f4-108">[Cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md) In dit voor beeld ziet u hoe u de verschillende typen para meters declareert.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-108">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="aa6f4-109">[Parameter sets declareren](./how-to-declare-parameter-sets.md) In dit voor beeld ziet u hoe u sets para meters declareert waarmee de actie die een cmdlet uitvoert, kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-109">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="aa6f4-110">[Parameter invoer valideren](./how-to-validate-parameter-input.md) In deze voor beelden ziet u hoe u parameter invoer kunt valideren.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-110">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="aa6f4-111">[Dynamische para meters declareren](./how-to-declare-dynamic-parameters.md) In dit voor beeld ziet u hoe u een para meter declareert die tijdens runtime is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-111">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="aa6f4-112">[Scripts aanroepen binnen een cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) In dit voor beeld ziet u hoe u een script aanroept dat wordt geleverd aan een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-112">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="aa6f4-113">[Invoer verwerkings methoden onderdrukken](./how-to-override-input-processing-methods.md) In deze voor beelden ziet u de basis structuur die wordt gebruikt om de BeginProcessing-, ProcessRecord-en EndProcessing-methoden te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-113">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="aa6f4-114">[ShouldProcess-aanroepen ondersteunen](./how-to-request-confirmations.md) In dit voor beeld ziet u hoe de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) moeten worden aangeroepen vanuit een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-114">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="aa6f4-115">[Trans acties ondersteunen](./how-to-support-transactions.md) In dit voor beeld ziet u hoe u kunt aangeven dat de cmdlet trans acties ondersteunt en hoe u de actie implementeert die moet worden uitgevoerd wanneer de cmdlet wordt gebruikt binnen een trans actie.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-115">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="aa6f4-116">[Taken ondersteunen](./how-to-support-jobs.md) In dit voor beeld ziet u hoe u taken kunt ondersteunen wanneer u cmdlets schrijft.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-116">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="aa6f4-117">[Een cmdlet aanroepen vanuit een cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) In dit voor beeld ziet u hoe u een cmdlet aanroept vanuit een andere cmdlet, waarmee u de functionaliteit van de aangeroepen cmdlet kunt toevoegen aan de cmdlet die u ontwikkelt.</span><span class="sxs-lookup"><span data-stu-id="aa6f4-117">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa6f4-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="aa6f4-118">See Also</span></span>

[<span data-ttu-id="aa6f4-119">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="aa6f4-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
